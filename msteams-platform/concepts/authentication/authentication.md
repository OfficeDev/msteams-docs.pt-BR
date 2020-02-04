---
title: Autenticar um usuário no Teams
description: Descreve a autenticação no Microsoft Teams e como usá-la em seus aplicativos
keywords: AAD SSO OAuth de autenticação de equipes
ms.openlocfilehash: d3ae57d9937c6794fb743b44ca8210a5afd181bf
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672571"
---
# <a name="authentication-in-teams"></a>Autenticação no Teams

> [!Note]
> A autenticação baseada na Web em clientes móveis requer a versão 1.4.1 ou posterior do SDK do Microsoft Teams.

Para que seu aplicativo acesse as informações do usuário protegidas pelo Azure Active Directory, além de acessar dados de outros serviços, como o Facebook e o Twitter, seu aplicativo terá que estabelecer uma conexão confiável com esses provedores. Se seu aplicativo precisar usar as APIs do Microsoft Graph no escopo do usuário, você também precisará autenticar o usuário para recuperar os tokens de autenticação apropriados.

No Microsoft Teams há dois fluxos de autenticação diferentes para que seu aplicativo aproveite. Você pode executar um fluxo de autenticação tradicional baseado na Web em uma [página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md) incorporada em uma guia, em uma página de configuração ou em um módulo de tarefa. Se seu aplicativo contiver um bot de conversa, você poderá usar o fluxo do OAuthPrompt (e, opcionalmente, o serviço de token da estrutura de bot do Azure) para autenticar um usuário como parte de uma conversa.

## <a name="web-based-authentication-flow"></a>Fluxo de autenticação baseado na Web

Você precisará usar o fluxo de autenticação baseado na Web para [guias](~/tabs/what-are-tabs.md)e poderá optar por usá-lo com [bots](~/bots/what-are-bots.md) ou extensões de [mensagens](~/messaging-extensions/what-are-messaging-extensions.md)de conversa. Você usará o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) em uma página de conteúdo da Web para habilitar a autenticação e, em seguida, incorporar essa página de conteúdo em uma guia, uma página de configuração ou um módulo de tarefa. Se quiser usar o fluxo de autenticação baseado na Web com um bot de conversa, você precisará [usar um módulo de tarefa com um bot](~/task-modules-and-cards/task-modules/task-modules-bots.md).

* [Fluxo de autenticação em guias](~/tabs/how-to/authentication/auth-flow-tab.md) descreve como a autenticação de guia funciona no Microsoft Teams. Isso mostra um fluxo de autenticação baseado na Web típico usado para guias.
* [Autenticação do Azure AD em guias](~/tabs/how-to/authentication/auth-tab-AAD.md) descreve como se conectar ao Azure Active Directory de dentro de uma guia em seu aplicativo no Microsoft Teams.
* [Autenticação silenciosa (Azure AD)](~/tabs/how-to/authentication/auth-silent-AAD.md) descreve como reduzir as solicitações de entrada/consentimento no aplicativo usando o Azure Active Directory.
* Autenticação baseada na Web em [dotnet/C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) ou [JavaScript/node. js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>O fluxo de OAuthPrompt para bots de conversa

O OAuthPrompt da estrutura de bot do Azure torna a autenticação mais fácil para aplicativos que usam bots de conversa. Você pode aproveitar o serviço de token da estrutura de bot do Azure para ajudar com o cache de token também.

Para obter mais informações sobre como usar o OAuthPrompt, confira:

* [Visão geral do fluxo de autenticação do bot](~/bots/how-to/authentication/auth-flow-bot.md) descreve como a autenticação funciona dentro de um bot em seu aplicativo no Microsoft Teams. Isso mostra um fluxo de autenticação não baseado na Web usado para bots em todas as versões do Teams (Web, aplicativo de área de trabalho e aplicativos móveis)
* [Autenticação de bot](~/bots/how-to/authentication/add-authentication.md)
* Exemplo de autenticação de bot (SDK do v3) em [dotnet/C#](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) ou [JavaScript/node. js](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth)

## <a name="configure-your-identity-provider"></a>Configurar seu provedor de identidade

Independentemente do fluxo de autenticação que seu aplicativo está usando (você pode até mesmo usar ambos), precisará configurar seu provedor de identidade para se comunicar com o aplicativo do Microsoft Teams. A maioria dos exemplos e orientações explicativas que você encontrará aqui lidará principalmente com o uso do Azure Active Directory como provedor de identidade. Os conceitos, no entanto, se aplicam independentemente do provedor de identidade que você usará.

Para obter mais informações, consulte [Configuring a Identity Provider](~/concepts/authentication/configure-identity-provider.md)
