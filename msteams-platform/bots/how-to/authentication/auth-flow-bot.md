---
title: Fluxo de autenticação do Microsoft Teams para bots
description: Habilite a autenticação para o aplicativo de bot do Microsoft Teams com o provedor OAuth de terceiros usando exemplos de código.
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: 67668f11fafcc8eff878d82913f002ed8c2f96bc
ms.sourcegitcommit: 82c585d287d61924ce3a3bba3e9caeff35c9a27a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67587012"
---
# <a name="authentication-flow-for-bots-in-microsoft-teams"></a>Fluxo de autenticação para bots no Microsoft Teams

OAuth 2.0 é um padrão aberto para autenticação e autorização usado pelo Azure Active Directory e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams; [aqui está uma boa visão geral](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal](https://oauth.net/2/). O fluxo de autenticação para guias e bots é um pouco diferente — as guias são semelhantes aos sites para que possam usar o OAuth 2.0 diretamente, enquanto os bots não são e devem fazer algumas coisas de forma diferente, mas os conceitos principais são idênticos.

Consulte o repositório do GitHub [Exemplo de Autenticação do Microsoft Teams](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) para obter um exemplo que demonstra o fluxo de autenticação para bots usando o Node.js e o [tipo de concessão de código de autorização do OAuth 2.0](https://oauth.net/2/grant-types/authorization-code/).

![Diagrama da sequência de autenticação do bot](../../../assets/images/authentication/bot_auth_sequence_diagram.png)

1. O usuário envia uma mensagem para o bot.
2. O bot determina se o usuário precisa entrar.
   Neste exemplo, o bot armazena o token de acesso no seu armazenamento de dados do usuário. Ele solicita ao usuário que entre se ele não tiver um token validado para o provedor de identidade selecionado. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. O bot constrói o URL para a página inicial do fluxo de autenticação e envia um cartão para o usuário com uma ação `signin`. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))</br>
    Como outros fluxos de autenticação de aplicativos no Teams, a página inicial deve estar em um domínio que esteja na sua lista `validDomains` e no mesmo domínio que a página de redirecionamento pós-logon.
    > [!IMPORTANT]
    > O fluxo de concessão do código de autorização do OAuth 2.0 exige um parâmetro `state` na solicitação de autenticação, que contém um token de sessão exclusivo para impedir um [ataque de falsificação de solicitação entre sites](https://en.wikipedia.org/wiki/Cross-site_request_forgery). O exemplo utiliza um GUID gerado aleatoriamente.
4. Quando o usuário seleciona o botão *entrar*, o Teams abre uma janela pop-up e navega até a página inicial.
   > [!NOTE]
   > O tamanho da janela pop-up pode ser controlado através de parâmetros da cadeia de caracteres de consulta de largura e altura no URL. Por exemplo, se você adicionar largura=600 e altura=600, o tamanho da janela pop-up será de 600x600 pixels. O tamanho real da janela pop-up é limitado proporcionalmente ao tamanho da janela principal do Teams. Se a janela do Teams for pequena, a janela pop-up será menor que as dimensões especificadas.

5. A página inicial redireciona o usuário para o ponto de extremidade `authorize` do provedor de identidade. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. No site do provedor, o usuário entra e concede acesso ao bot.
7. O provedor leva o usuário à página de redirecionamento do OAuth do bot com um código de autorização.
8. O bot resgata o código de autorização para um token de acesso e associa **provisoriamente** o token ao usuário que iniciou o fluxo de entrada. Abaixo, chamamos isso de *token provisório*.
    * No exemplo, o bot associa o valor do parâmetro `state` à ID do usuário que iniciou o processo de entrada para que ele possa posteriormente corresponder com o valor `state` retornado pelo provedor de identidade. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
      > [!IMPORTANT]
      > O bot armazena o token que recebe do provedor de identidade e o associa a um usuário específico, mas é marcado como "validação pendente".
    * O token provisório não pode ser utilizado sem validação adicional.
      1. **Validar o que foi recebido do provedor de identidade.** O valor do parâmetro `state` deve ser confirmado em relação ao que foi salvo anteriormente.
      1. **Validar o que foi recebido do Teams.** Uma validação de [autenticação em duas etapas](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) é executada para garantir que o usuário que autorizou o bot com o provedor de identidade seja o mesmo usuário que está conversando com o bot. Isto protege contra os ataques [man-in-the-middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) e [phishing](https://en.wikipedia.org/wiki/Phishing). O bot gera um código de verificação e o armazena, associado com o usuário. O código de verificação é enviado automaticamente pelo Teams, conforme descrito abaixo. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. O retorno de chamada do OAuth renderiza uma página que chama `notifySuccess("<verification code>")`. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. O Teams fecha a janela pop-up e envia o `<verification code>` enviado para `notifySuccess()` de volta ao bot. O bot recebe uma mensagem [invocar](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) com `name = signin/verifyState`.
11. O bot verifica o código de verificação de entrada em relação ao código de verificação armazenado com o token provisório do usuário. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Se forem iguais, o bot marcará o token como validado e pronto para uso. Caso contrário, o fluxo de autenticação falhará e o bot excluirá o token provisório.

    > [!NOTE]
    > Se você tiver problemas com a autenticação em dispositivos móveis, certifique-se de que seu SDK JavaScript esteja atualizado para a versão 1.4.1 ou posterior.

## <a name="code-sample"></a>Exemplo de código

Exemplo de código mostrando o processo de autenticação do bot:

| **Nome de exemplo** | **Descrição** | **Node.js** | **.NET** | **Python** |
|-----------------|----------------|--------------|----------|-----------|
| Autenticação do Teams | Este exemplo demonstra a autenticação em aplicativos do Microsoft Teams. | [View](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) | | |
| Autenticação do bot | Este exemplo demonstra como usar a autenticação de um bot em execução no Microsoft Teams | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/46.teams-auth) | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth)

## <a name="see-also"></a>Confira também

[Adicionar autenticação ao seu bot do Teams](add-authentication.md)
