---
title: Microsoft Teams Fluxo de autenticação para bots
description: Descreve fluxo de autenticação Microsoft Teams em bots
keywords: robôs de fluxo de autenticação de equipes
localization_priority: Normal
ms.topic: overview
ms.openlocfilehash: f3bf73c105dc38e1cea515bfa7bb7d5324b02ce4
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565897"
---
# <a name="authentication-flow-for-bots-in-microsoft-teams"></a>Fluxo de autenticação para bots em Microsoft Teams

O OAuth 2.0 é um padrão aberto para autenticação e autorização usadas pelo Azure Active Directory (Azure AD) e muitos outros provedores de identidade. Um entendimento básico do OAuth 2.0 é um pré-requisito para trabalhar com autenticação em Teams; [aqui está uma boa visão geral](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal](https://oauth.net/2/). O fluxo de autenticação para guias e bots é um pouco diferente — as guias são muito semelhantes aos sites para que eles possam usar o OAuth 2.0 diretamente, enquanto os bots não são e devem fazer algumas coisas de forma diferente — mas os conceitos principais são idênticos.

Consulte a amostra de [autenticação Microsoft Teams](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) GitHub repo para um exemplo que demonstra o fluxo de autenticação para bots que usam Node.js e o [tipo de concessão de código de autorização OAuth 2.0](https://oauth.net/2/grant-types/authorization-code/).

![Diagrama da sequência de autenticação de bot](../../../assets/images/authentication/bot_auth_sequence_diagram.png)

1. O usuário envia uma mensagem para o bot.
2. O bot determina se o usuário precisa fazer login.
   Neste exemplo, o bot armazena o token de acesso em sua loja de dados de usuário. Ele pede ao usuário para fazer login se ele não tiver um token validado para o provedor de identidade selecionado. (Ver[código)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76)
3. O bot constrói a URL para a página inicial do fluxo de autenticação e envia um cartão para o usuário com uma `signin` ação. (Ver[código)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190)</br>
    Como outros fluxos de auth de aplicativos em Teams, a página inicial deve estar em um domínio que está em sua `validDomains` lista e no mesmo domínio da página de redirecionamento pós-login.
    > [!IMPORTANT] 
    > O fluxo de concessão de código de autorização OAuth 2.0 exige um `state` parâmetro na solicitação de autenticação que contém um token de sessão exclusivo para evitar um ataque de [falsificação de solicitação entre sites](https://en.wikipedia.org/wiki/Cross-site_request_forgery). O exemplo usa um GUID gerado aleatoriamente.
4. Quando o usuário seleciona o botão *de sinalização,* Teams abre uma janela pop-up e navega até a página inicial.
   > [!NOTE]
   > O tamanho da janela pop-up pode ser controlado através de parâmetros de sequência de espartidão de largura e altura na URL. Por exemplo, se você adicionar largura=500 e altura=500, o tamanho da janela pop-up é de 500x500 pixels. Teams exibe a janela pop-up com o tamanho dado do pixel, até um máximo que é uma porcentagem do tamanho da janela principal.

5. A página inicial redireciona o usuário para o ponto final do provedor de `authorize` identidade. (Ver[código)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56)
6. No site do provedor, o usuário faz a assinatura e concede acesso ao bot.
7. O provedor leva o usuário para a página de redirecionamento OAuth do bot com um código de autorização.
8. O bot resgata o código de autorização para um token de acesso e associa **provisoriamente** o token ao usuário que iniciou o fluxo de login. Abaixo, chamamos isso de *um token provisório.*
    * No exemplo, o bot associa o valor do `state` parâmetro com o ID do usuário que iniciou o processo de login para que ele possa depois igualá-lo com o valor devolvido pelo provedor de `state` identidade. (Ver[código)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99)
      > [!IMPORTANT] 
      > O bot armazena o token que recebe do provedor de identidade e o associa a um usuário específico, mas é marcado como "validação pendente". 
    * O token provisório não pode ser usado sem maiores validações.
      1. **Validar o que é recebido do provedor de identidade.** O valor do `state` parâmetro deve ser confirmado em relação ao que foi salvo anteriormente. 
      1. **Valide o que é recebido de Teams.** Uma [validação de autenticação em duas etapas](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) é realizada para garantir que o usuário que autorizou o bot com o provedor de identidade seja o mesmo usuário que está conversando com o bot. Este guarda contra [ataques de homem no meio](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) e [phishing.](https://en.wikipedia.org/wiki/Phishing) O bot gera um código de verificação e o armazena, associado ao usuário. O código de verificação é enviado automaticamente por Teams conforme descrito abaixo. (Ver[código)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113)
9. O retorno de chamada do OAuth renderiza uma página que chama `notifySuccess("<verification code>")` . (Ver[código)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs)
10. Teams fecha a janela pop-up e envia o `<verification code>` enviado de volta para o `notifySuccess()` bot. O bot recebe uma mensagem [de invocação](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) com `name = signin/verifyState` .
11. O bot verifica o código de verificação recebido em relação ao código de verificação armazenado com o token provisório do usuário. (Ver[código)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140)
12. Se eles corresponderem, o bot marca o token como validado e pronto para uso. Caso contrário, o fluxo de auth falha e o bot exclui o token provisório.

    > [!NOTE]
    > Se você tiver problemas com autenticação no celular, certifique-se de que seu JavaScript SDK seja atualizado para a versão 1.4.1 ou posterior.

## <a name="code-sample"></a>Exemplo de código

Código de amostra mostrando o processo de autenticação do bot:

| **Nome da amostra** | **Descrição** | **Node.js** | **.NET** | **Python** |
|-----------------|----------------|--------------|----------|-----------|
| autenticação Teams | Esta amostra demonstra autenticação em aplicativos Microsoft Teams. | [View](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) | | |
| Autenticação de bot | Esta amostra demoniza como usar autenticação para um runnning de bot em Microsoft Teams | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth)

## <a name="see-also"></a>Confira também

[Adicione autenticação ao seu bot Teams](add-authentication.md)
