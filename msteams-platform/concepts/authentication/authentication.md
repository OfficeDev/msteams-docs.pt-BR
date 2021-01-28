---
title: Autenticando usuários do aplicativo
description: Descreve a autenticação no Teams e como usá-la em seus aplicativos
ms.topic: conceptual
keywords: autenticação de equipes OAuth SSO AAD
ms.openlocfilehash: 6ddcd8a9e847d9216b7e2dcc12733a6cd413b48e
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014289"
---
# <a name="authenticating-users-in-microsoft-teams"></a>Autenticando usuários no Microsoft Teams

> [!Note]
> A autenticação baseada na Web em clientes móveis requer a versão 1.4.1 ou posterior do SDK JavaScript do Teams.

Para que seu aplicativo acesse as informações do usuário protegidas pelo Azure Active Directory, bem como acessar dados de outros serviços, como o Facebook e o Twitter, seu aplicativo terá que estabelecer uma conexão confiável com esses provedores. Se seu aplicativo precisar usar APIs do Microsoft Graph no escopo do usuário, você também precisará autenticar o usuário para recuperar os tokens de autenticação apropriados.

No Microsoft Teams, há dois fluxos de autenticação diferentes para seu aplicativo aproveitar. Você pode executar um fluxo de [](~/tabs/how-to/create-tab-pages/content-page.md) autenticação baseado na Web tradicional em uma página de conteúdo inserida em uma guia, uma página de configuração ou um módulo de tarefa. Se seu aplicativo contiver um bot de conversa, você poderá usar o fluxo do OAuthPrompt (e, opcionalmente, o serviço de token do Azure Bot Framework) para autenticar um usuário como parte de uma conversa.

## <a name="web-based-authentication-flow"></a>Fluxo de autenticação baseada na Web

Você precisará usar o fluxo de autenticação baseado na Web para guias e pode optar por usá-lo com [bots](~/bots/what-are-bots.md) de conversa ou extensões [de mensagens.](~/messaging-extensions/what-are-messaging-extensions.md) [](~/tabs/what-are-tabs.md) Você usará o [SDK](/javascript/api/overview/msteams-client) do cliente JavaScript do Microsoft Teams em uma página de conteúdo da Web para habilitar a autenticação e inserir essa página de conteúdo em uma guia, uma página de configuração ou um módulo de tarefa. Se você quiser usar o fluxo de autenticação baseada na Web com um bot de conversa, precisará usar um módulo de tarefa [com um bot.](~/task-modules-and-cards/task-modules/task-modules-bots.md)

* [O fluxo de autenticação nas guias](~/tabs/how-to/authentication/auth-flow-tab.md) descreve como a autenticação de guia funciona no Teams. Isso mostra um típico fluxo de autenticação baseado na Web usado para guias.
* [A autenticação do Azure AD](~/tabs/how-to/authentication/auth-tab-AAD.md) nas guias descreve como se conectar ao Azure Active Directory de dentro de uma guia em seu aplicativo no Teams.
* [A autenticação silenciosa (Azure AD)](~/tabs/how-to/authentication/auth-silent-AAD.md) descreve como reduzir os prompts de login/consentimento em seu aplicativo usando o Azure Active Directory.
* Autenticação baseada na Web [em dotnet/C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) ou [JavaScript/Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>O fluxo OAuthPrompt para bots de conversa

O OAuthPrompt da Estrutura de Bot do Azure facilita a autenticação para aplicativos que usam bots de conversa. Você também pode aproveitar o serviço de token do Azure Bot Framework para ajudar no cache de tokens.

Para obter mais informações sobre como usar o OAuthPrompt, consulte:

* [A visão geral do fluxo de autenticação](~/bots/how-to/authentication/auth-flow-bot.md) de bot descreve como a autenticação funciona em um bot em seu aplicativo no Teams. Isso mostra um fluxo de autenticação não baseado na Web usado para bots em todas as versões do Teams (web, aplicativo da área de trabalho e aplicativos móveis)
* [Autenticação de bot](~/bots/how-to/authentication/add-authentication.md)
* Exemplo de autenticação de bot (SDK v3) [em dotnet/C#](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) ou [JavaScript/Node.js](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth)

## <a name="configure-your-identity-provider"></a>Configurar seu provedor de identidade

Independentemente do fluxo de autenticação que seu aplicativo está usando (você pode até mesmo estar usando ambos), você precisará configurar seu provedor de identidade para se comunicar com seu aplicativo do Teams. A maioria dos exemplos e passo a passo que você encontrará aqui lidará principalmente com o uso do Azure Active Directory como seu provedor de identidade. No entanto, os conceitos se aplicam independentemente de qual provedor de identidade você usará.

Para obter mais informações, [consulte a configuração de um provedor de identidade](~/concepts/authentication/configure-identity-provider.md)
