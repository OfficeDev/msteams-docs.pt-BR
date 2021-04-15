---
title: Fluxo de autenticação para bots
description: Descreve o fluxo de autenticação em bots
keywords: bots de fluxo de autenticação do teams
ms.topic: conceptual
ms.date: 03/01/2018
ms.openlocfilehash: 317e0d8310c0e040eccc7bd1cc343e7a1fa9a16d
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696196"
---
# <a name="microsoft-teams-authentication-flow-for-bots"></a>Fluxo de autenticação do Microsoft Teams para bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

OAuth 2.0 é um padrão aberto para autenticação e autorização usada pelo Azure AD e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams; [aqui está uma boa visão geral](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal](https://oauth.net/2/). O fluxo de autenticação para guias e bots é um pouco diferente porque as guias são muito semelhantes aos sites para que possam usar o OAuth 2.0 diretamente, e os bots não são e devem fazer algumas coisas diferentes, mas os conceitos principais são idênticos.

Consulte o Exemplo de Autenticação do Microsoft Teams do [GitHub](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) para um exemplo que demonstra o fluxo de autenticação para bots usando Node usando o tipo de concessão de código de autorização [OAuth 2.0](https://oauth.net/2/grant-types/authorization-code/).

![Diagrama de sequência de autenticação bot](~/assets/images/authentication/bot_auth_sequence_diagram.png)

1. O usuário envia uma mensagem para o bot.
2. O bot determina se o usuário precisa entrar.
    * Neste exemplo, o bot armazena o token de acesso em seu armazenamento de dados do usuário. Ele solicita que o usuário faça logoff se ele não tiver um token validado para o provedor de identidade selecionado. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. O bot constrói a URL para a página inicial do fluxo de autenticação e envia um cartão para o usuário com uma `signin` ação. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))
    * Como outros fluxos de auth de aplicativos no Teams, a página inicial deve estar em um domínio que está em sua lista e no mesmo domínio que a página de redirecionamento `validDomains` pós-logon.
    * **IMPORTANTE**: O código de autorização OAuth 2.0 concede chamadas de fluxo para um parâmetro na solicitação de autenticação que contém um token de sessão exclusivo para evitar um ataque de falsificação de solicitação entre `state` sites. [](https://en.wikipedia.org/wiki/Cross-site_request_forgery) O exemplo usa um GUID gerado aleatoriamente.
4. Quando o usuário clica no botão *de* login, o Teams abre uma janela pop-up e navega até a página inicial.
5. A página inicial redireciona o usuário para o ponto de extremidade do provedor `authorize` de identidade. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. No site do provedor, o usuário faz o acesso e concede acesso ao bot.
7. O provedor leva o usuário para a página de redirecionamento OAuth do bot, com um código de autorização.
8. O bot resgata o código de autorização de um token de acesso e associa provisoriamente o token ao usuário que iniciou o fluxo de entrada.  Abaixo, chamamos isso de *token provisório*.
    * No exemplo, o bot associa o valor do parâmetro com a id do usuário que iniciou o processo de login para que ele possa corresponder posteriormente com o valor retornado pelo provedor `state` `state` de identidade. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
    * **IMPORTANTE**: o bot armazena o token que recebe do provedor de identidade e o associa a um usuário específico, mas é marcado como "validação pendente". O token provisório ainda não pode ser usado: ele deve ser ainda mais validado: 
      1. **Valide o que é recebido do provedor de identidade.** O valor do `state` parâmetro deve ser confirmado em relação ao que foi salvo anteriormente. 
      1. **Valide o que é recebido do Teams.** Uma [validação de autenticação](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) em duas etapas é realizada para garantir que o usuário que autorizou o bot com o provedor de identidade seja o mesmo usuário que está conversando com o bot. Isso protege contra ataques de [phishing e](https://en.wikipedia.org/wiki/Phishing) [man-in-the-middle.](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) O bot gera um código de verificação e o armazena, associado ao usuário. O código de verificação é enviado automaticamente pelo Teams, conforme descrito abaixo nas etapas 9 e 10. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. O retorno de chamada OAuth renderiza uma página que chama `notifySuccess("<verification code>")` . ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. O Teams fecha o pop-up e envia `<verification code>` o enviado para voltar ao `notifySuccess()` bot. O bot recebe uma [mensagem de invocação](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) com `name = signin/verifyState` .
11. O bot verifica o código de verificação de entrada em relação ao código de verificação armazenado com o token provisório do usuário. ([Código de exibição](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Se eles corresponderem, o bot marcará o token como validado e pronto para uso. Caso contrário, o fluxo de auth falhará e o bot excluirá o token provisório.

> [!Note]
> Se você tiver problemas com a autenticação no celular, verifique se o SDK Javascript está atualizado para a versão 1.4.1 ou posterior.

## <a name="samples"></a>Exemplos

Para um código de exemplo que mostra o processo de autenticação do bot, consulte:

* [Exemplo de autenticação de bot do Microsoft Teams (Nó)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)

## <a name="more-details"></a>Mais detalhes

Para ver os passo a passo detalhados da implementação para autenticação de bot voltada para o Azure Active Directory, consulte:

* [Autenticar um usuário em um bot do Microsoft Teams](~/resources/bot-v3/bot-authentication/auth-bot-AAD.md)
