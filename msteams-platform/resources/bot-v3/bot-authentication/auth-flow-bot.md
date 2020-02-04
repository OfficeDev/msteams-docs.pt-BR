---
title: Fluxo de autenticação para bots
description: Descreve o fluxo de autenticação em bots
keywords: bots de fluxo de autenticação de equipes
ms.date: 03/01/2018
ms.openlocfilehash: 5230a94b23f9042d9d7753b52467fba5b2fec89e
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672947"
---
# <a name="microsoft-teams-authentication-flow-for-bots"></a>Fluxo de autenticação do Microsoft Teams para bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

O OAuth 2,0 é um padrão aberto para autenticação e autorização usados pelo Azure AD e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2,0 é um pré-requisito para trabalhar com autenticação no Microsoft Teams; [Veja aqui uma boa visão geral](https://aaronparecki.com/oauth-2-simplified/) que é mais fácil de seguir do que a [especificação formal](https://oauth.net/2/). O fluxo de autenticação para guias e bots é um pouco diferente porque guias são muito semelhantes aos sites para que eles possam usar o OAuth 2,0 diretamente, e os bots não são e devem fazer algumas coisas de forma diferente, mas os conceitos principais são idênticos.

Confira o [exemplo de autenticação do Microsoft Teams](https://github.com/OfficeDev/microsoft-teams-sample-auth-node) do GitHub para obter um exemplo que demonstre o fluxo de autenticação para bots usando o nó usando o [tipo de concessão de código de autorização OAuth 2,0](https://oauth.net/2/grant-types/authorization-code/).

![Diagrama de sequência de autenticação de bot](~/assets/images/authentication/bot_auth_sequence_diagram.png)

1. O usuário envia uma mensagem para o bot.
2. O bot determina se o usuário precisa entrar.
    * Neste exemplo, o bot armazena o token de acesso no armazenamento de dados do usuário. Ele solicita que o usuário faça logon se não tiver um token validado para o provedor de identidade selecionado. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/utils/AuthenticationUtils.ts#L58-L76))
3. O bot cria a URL para a página inicial do fluxo de autenticação e envia um cartão para o usuário com uma `signin` ação. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L160-L190))
    * Como outros fluxos de autenticação de aplicativos no Microsoft Teams, a página inicial deve estar em um domínio `validDomains` que esteja na sua lista e no mesmo domínio que a página de redirecionamento pós-logon.
    * **Importante**: o fluxo de concessão do código de autorização OAuth 2,0 `state` chama um parâmetro na solicitação de autenticação que contém um token de sessão exclusivo para evitar um [ataque de falsificação de solicitação entre sites](https://en.wikipedia.org/wiki/Cross-site_request_forgery). O exemplo usa um GUID gerado aleatoriamente.
4. Quando o usuário clica no botão de *entrada* , o Microsoft Teams abre uma janela pop-up e a navega para a página inicial.
5. A página inicial redireciona o usuário para o ponto de extremidade do `authorize` provedor de identidade. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/public/html/auth-start.html#L51-L56))
6. No site do provedor, o usuário entra e concede acesso ao bot.
7. O provedor leva o usuário para a página de redirecionamento OAuth do bot, com um código de autorização.
8. O bot reconsidera o código de autorização para um token de acesso e **associa o** token ao usuário que iniciou o fluxo de entrada. A seguir, chamamos isso de um *token provisório*.
    * No exemplo, o bot associa o valor do `state` parâmetro com a ID do usuário que iniciou o processo de entrada para que ele possa correspondê-lo mais tarde com o `state` valor retornado pelo provedor de identidade. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L70-L99))
    * **Importante**: o bot armazena o token que recebe do provedor de identidade e o associa a um usuário específico, mas está marcado como "validação pendente". O token provisório ainda não pode ser usado: ele deve ser validado novamente: 
      1. **Validar o que é recebido do provedor de identidade.** O valor do `state` parâmetro deve ser confirmado em relação ao que foi salvo anteriormente. 
      1. **Validar o que é recebido do teams.** Uma validação de [autenticação de duas etapas](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) é executada para garantir que o usuário que autorizou o bot com o provedor de identidade seja o mesmo usuário que está batendo papo com o bot. Isso protege contra ataques [Man-in-the-Middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) e [phishing](https://en.wikipedia.org/wiki/Phishing) . O bot gera um código de verificação e o armazena, associado ao usuário. O código de verificação é enviado automaticamente pelo Teams, conforme descrito abaixo nas etapas 9 e 10. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/AuthBot.ts#L100-L113))
9. O retorno de chamada OAuth renderiza uma página que `notifySuccess("<verification code>")`chama. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/master/src/views/oauth-callback-success.hbs))
10. O Microsoft Teams fecha o pop `<verification code>` -up `notifySuccess()` e envia o enviado para de volta para o bot. O bot recebe uma mensagem [Invoke](/bot-framework/dotnet/bot-builder-dotnet-activities#invoke) com `name = signin/verifyState`.
11. O bot verifica o código de verificação de entrada em relação ao código de verificação armazenado com o token provisório do usuário. ([Exibir código](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/469952a26d618dbf884a3be53c7d921cc580b1e2/src/dialogs/BaseIdentityDialog.ts#L127-L140))
12. Se houver correspondência, o bot marca o token como validado e pronto para uso. Caso contrário, o fluxo de autenticação falhará e o bot excluirá o token provisionado.

> [!Note]
> Se você tiver problemas com a autenticação em dispositivos móveis, verifique se o SDK do JavaScript está atualizado para a versão 1.4.1 ou posterior.

## <a name="samples"></a>Exemplos

Para ver o código de exemplo que mostra o processo de autenticação do bot, confira:

* [Exemplo de autenticação de bot do Microsoft Teams (nó)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)

## <a name="more-details"></a>Mais detalhes

Para obter instruções detalhadas de implementação para a autenticação de bot direcionada ao Azure Active Directory, confira:

* [Autenticar um usuário em um bot do Microsoft Teams](~/resources/bot-v3/bot-authentication/auth-bot-AAD.md)
