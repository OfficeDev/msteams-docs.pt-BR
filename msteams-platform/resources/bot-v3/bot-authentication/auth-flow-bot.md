---
title: Fluxo de autenticação para bots
description: Descreve o fluxo de autenticação em bots
keywords: bots do fluxo de autenticação do teams
localization_priority: Normal
ms.topic: conceptual
ms.date: 03/01/2018
ms.openlocfilehash: e3bc5395a6a95272901076ec8bf51dc2ad57dfd2
ms.sourcegitcommit: 1cda2fd3498a76c09e31ed7fd88175414ad428f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2022
ms.locfileid: "67035328"
---
# <a name="microsoft-teams-authentication-flow-for-bots"></a>Fluxo de autenticação do Microsoft Teams para bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

O OAuth 2.0 é um padrão aberto para autenticação e autorização usada pelo Azure AD e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams; [aqui está uma boa visão geral](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal](https://oauth.net/2/). O fluxo de autenticação para guias e bots é diferente. As guias são semelhantes aos sites para que possam usar o OAuth 2.0 diretamente, e os bots não são e devem fazer algumas coisas de forma diferente, mas os conceitos principais são idênticos.

Consulte o exemplo de autenticação do [Microsoft Teams](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) do repositório GitHub para obter um exemplo que demonstra o fluxo de autenticação para bots que usam o Node usando o tipo de concessão de código de autorização [OAuth 2.0](https://oauth.net/2/grant-types/authorization-code/).

![Diagrama da sequência de autenticação do bot](~/assets/images/authentication/bot_auth_sequence_diagram.png)

1. O usuário envia uma mensagem para o bot.
2. O bot determina se o usuário precisa entrar.
    * Neste exemplo, o bot armazena o token de acesso no seu armazenamento de dados do usuário. Ele solicita que o usuário faça logon se ele não tiver um token validado para o provedor de identidade selecionado. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. O bot constrói o URL para a página inicial do fluxo de autenticação e envia um cartão para o usuário com uma ação `signin`. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))
    * Assim como outros fluxos de autenticação de aplicativo no Teams, a página inicial deve estar em um domínio que esteja em sua lista e no mesmo domínio que a `validDomains` página de redirecionamento pós-logon.
    * **IMPORTANTE**: o fluxo de concessão de código de autorização do OAuth 2.0 `state` chama um parâmetro na solicitação de autenticação que contém um token de sessão exclusivo para evitar um ataque de solicitação entre sites [forjada](https://en.wikipedia.org/wiki/Cross-site_request_forgery). O exemplo usa um GUID gerado aleatoriamente.
4. Quando o usuário seleciona o botão *de* entrada, o Teams abre uma janela pop-up e a navega até a página inicial.
5. A página inicial redireciona o usuário para o ponto de extremidade `authorize` do provedor de identidade. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. No site do provedor, o usuário entra e concede acesso ao bot.
7. O provedor leva o usuário para a página de redirecionamento OAuth do bot, com um código de autorização.
8. O bot resgata o código de autorização para um token de acesso e associa **provisoriamente** o token ao usuário que iniciou o fluxo de entrada. Abaixo, chamamos isso de *token provisório*.
    * No exemplo, o bot associa o valor do parâmetro `state` à ID do usuário que iniciou o processo de entrada para que ele possa posteriormente corresponder com o valor `state` retornado pelo provedor de identidade. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
    * **IMPORTANTE**: o bot armazena o token que recebe do provedor de identidade e o associa a um usuário específico, mas é marcado como "validação pendente". O token provisório ainda não pode ser usado: ele deve ser validado ainda mais:
      1. **Validar o que foi recebido do provedor de identidade.** O valor do parâmetro `state` deve ser confirmado em relação ao que foi salvo anteriormente.
      1. **Validar o que foi recebido do Teams.** Uma validação de [autenticação em duas etapas](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) é executada para garantir que o usuário que autorizou o bot com o provedor de identidade seja o mesmo usuário que está conversando com o bot. Essa validação protege contra [ataques man-in-the-middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) e [phishing](https://en.wikipedia.org/wiki/Phishing) . O bot gera um código de verificação e o armazena, associado com o usuário. O código de verificação é enviado automaticamente pelo Teams, conforme descrito abaixo nas etapas 9 e 10. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. O retorno de chamada do OAuth renderiza uma página que chama `notifySuccess("<verification code>")`. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. O Teams fecha o pop-up e envia o `<verification code>` enviado para `notifySuccess()` o bot. O bot recebe uma mensagem [invocar](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) com `name = signin/verifyState`.
11. O bot verifica o código de verificação de entrada em relação ao código de verificação armazenado com o token provisório do usuário. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Se forem iguais, o bot marcará o token como validado e pronto para uso. Caso contrário, o fluxo de autenticação falhará e o bot excluirá o token provisório.

> [!Note]
> Se você tiver problemas com a autenticação em dispositivos móveis, verifique se o SDK do JavaScript está atualizado para a versão 1.4.1 ou posterior.

## <a name="samples"></a>Exemplos

Para obter o código de exemplo mostrando o processo de autenticação de bot, consulte:

* [Exemplo de autenticação de bot do Microsoft Teams (Node)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)

## <a name="more-details"></a>Mais detalhes

Para obter instruções passo a passo de implementação detalhadas para autenticação de bot direcionada ao Azure Active Directory, consulte:

* [Autenticar um usuário em um bot do Microsoft Teams](~/resources/bot-v3/bot-authentication/auth-bot-AAD.md)
