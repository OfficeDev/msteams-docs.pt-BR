---
title: Microsoft Teams Fluxo de autenticação para bots
description: Descreve Microsoft Teams fluxo de autenticação em bots
keywords: bots de fluxo de autenticação do teams
localization_priority: Normal
ms.topic: overview
ms.openlocfilehash: 0eb4808cc162b293404530f7da7ac9d63b9f98cb86a0d864866fd31e388ecb89
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57708313"
---
# <a name="authentication-flow-for-bots-in-microsoft-teams"></a>Fluxo de autenticação para bots Microsoft Teams

O OAuth 2.0 é um padrão aberto para autenticação e autorização usadas pelo Azure Active Directory (Azure AD) e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams; [aqui está uma boa visão geral](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal](https://oauth.net/2/). O fluxo de autenticação para guias e bots é um pouco diferente — as guias são muito semelhantes aos sites, para que eles possam usar o OAuth 2.0 diretamente, enquanto os bots não são e devem fazer algumas coisas de forma diferente — mas os conceitos principais são idênticos.

Consulte o GitHub de Microsoft Teams [de](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) autenticação para um exemplo que demonstra o fluxo de autenticação para bots usando o Node.js e o tipo de concessão de código de autorização [OAuth 2.0](https://oauth.net/2/grant-types/authorization-code/).

![Diagrama de sequência de autenticação bot](../../../assets/images/authentication/bot_auth_sequence_diagram.png)

1. O usuário envia uma mensagem para o bot.
2. O bot determina se o usuário precisa entrar.
   Neste exemplo, o bot armazena o token de acesso em seu armazenamento de dados do usuário. Ele solicita que o usuário entre se não tiver um token validado para o provedor de identidade selecionado. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. O bot constrói a URL para a página inicial do fluxo de autenticação e envia um cartão para o usuário com uma `signin` ação. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))</br>
    Como outros fluxos de auth de aplicativos no Teams, a página inicial deve estar em um domínio que está em sua lista e no mesmo domínio que a página de redirecionamento `validDomains` pós-logon.
    > [!IMPORTANT] 
    > O código de autorização OAuth 2.0 concede chamadas de fluxo para um parâmetro na solicitação de autenticação que contém um token de sessão exclusivo para evitar um ataque de falsificação de solicitação entre `state` [sites.](https://en.wikipedia.org/wiki/Cross-site_request_forgery) O exemplo usa um GUID gerado aleatoriamente.
4. Quando o usuário seleciona o botão *de* Teams abre uma janela pop-up e navega até a página inicial.
   > [!NOTE]
   > O tamanho da janela pop-up pode ser controlado por meio de parâmetros de cadeia de caracteres de consulta de largura e altura na URL. Por exemplo, se você adicionar width=600 e height=600, o tamanho da janela pop-up será 600x600 pixels. O tamanho real da janela pop-up é limitado como uma porcentagem do tamanho da janela Teams principal. Se a Teams for pequena, a janela pop-up será menor do que as dimensões especificadas.

5. A página inicial redireciona o usuário para o ponto de extremidade do provedor `authorize` de identidade. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. No site do provedor, o usuário faz o acesso e concede acesso ao bot.
7. O provedor leva o usuário para a página de redirecionamento OAuth do bot com um código de autorização.
8. O bot resgata o código de autorização de um token de acesso e associa provisoriamente o token ao usuário que iniciou o fluxo de entrada.  Abaixo, chamamos isso de *token provisório*.
    * No exemplo, o bot associa o valor do parâmetro com a ID do usuário que iniciou o processo de login para que ele possa, posteriormente, corresponder a ele com o valor retornado pelo provedor de `state` `state` identidade. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
      > [!IMPORTANT] 
      > O bot armazena o token que recebe do provedor de identidade e o associa a um usuário específico, mas é marcado como "validação pendente". 
    * O token provisório não pode ser usado sem validação posterior.
      1. **Valide o que é recebido do provedor de identidade.** O valor do `state` parâmetro deve ser confirmado em relação ao que foi salvo anteriormente. 
      1. **Valide o que é recebido do Teams.** Uma [validação de autenticação](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) em duas etapas é realizada para garantir que o usuário que autorizou o bot com o provedor de identidade seja o mesmo usuário que está conversando com o bot. Isso protege contra ataques de [phishing e](https://en.wikipedia.org/wiki/Phishing) [man-in-the-middle.](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) O bot gera um código de verificação e o armazena, associado ao usuário. O código de verificação é enviado automaticamente Teams conforme descrito abaixo. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. O retorno de chamada OAuth renderiza uma página que chama `notifySuccess("<verification code>")` . ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. Teams fecha a janela pop-up e envia `<verification code>` o enviado de volta para o `notifySuccess()` bot. O bot recebe uma [mensagem de invocação](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) com `name = signin/verifyState` .
11. O bot verifica o código de verificação de entrada em relação ao código de verificação armazenado com o token provisório do usuário. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Se eles corresponderem, o bot marcará o token como validado e pronto para uso. Caso contrário, o fluxo de auth falhará e o bot excluirá o token provisório.

    > [!NOTE]
    > Se você tiver problemas com a autenticação no celular, verifique se o SDK JavaScript está atualizado para a versão 1.4.1 ou posterior.

## <a name="code-sample"></a>Exemplo de código

Código de exemplo mostrando o processo de autenticação de bot:

| **Nome do exemplo** | **Descrição** | **Node.js** | **.NET** | **Python** |
|-----------------|----------------|--------------|----------|-----------|
| Teams autenticação | Este exemplo demonstra autenticação em Microsoft Teams aplicativos. | [Exibir](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) | | |
| Autenticação bot | Este exemplo demonstra como usar a autenticação para um bot em execução no Microsoft Teams | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/46.teams-auth) | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/46.teams-auth) | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth)

## <a name="see-also"></a>Confira também

[Adicionar autenticação ao seu Teams bot](add-authentication.md)
