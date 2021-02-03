---
title: Autenticando usuários do aplicativo
description: Descreve a autenticação no Teams e como usá-la nos aplicativos
ms.topic: conceptual
keywords: autenticação de equipes OAuth SSO AAD
ms.openlocfilehash: 88b2098b7d45444cf47bebdfccc22fae772b7c22
ms.sourcegitcommit: 843da1730443ff8474a05295f60a6b376ed140da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2021
ms.locfileid: "50073100"
---
# <a name="authenticate-users-in-microsoft-teams"></a>Autenticar usuários no Microsoft Teams

> [!NOTE]
> A autenticação baseada na Web em clientes móveis requer a versão 1.4.1 ou posterior do SDK javaScript do Microsoft Teams.

Para acessar informações do usuário protegidas pelo Azure Active Directory (AAD) e acessar dados de serviços como o Facebook e o Twitter, o aplicativo estabelece uma conexão confiável com esses provedores. Se o aplicativo usar APIs do Microsoft Graph no escopo do usuário, autenti-o para recuperar os tokens de autenticação apropriados.

No Teams, há dois fluxos de autenticação diferentes para o aplicativo. Execute um fluxo de autenticação baseado na Web tradicional em uma página [de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md) inserida em uma guia, uma página de configuração ou um módulo de tarefa. Se o aplicativo contiver um bot de conversa, use o fluxo do OAuthPrompt e, opcionalmente, o serviço de token do Azure Bot Framework para autenticar um usuário como parte de uma conversa.

## <a name="web-based-authentication-flow"></a>Fluxo de autenticação baseada na Web

Use o fluxo de autenticação baseada na Web para [guias](~/tabs/what-are-tabs.md) e opte por usá-lo com [bots](~/bots/what-are-bots.md) de conversa ou extensões [de mensagens.](~/messaging-extensions/what-are-messaging-extensions.md) Use o [SDK do](/javascript/api/overview/msteams-client) cliente JavaScript do Microsoft Teams em uma página de conteúdo da Web para habilitar a autenticação. Depois de habilite a autenticação, incorporar a página de conteúdo em uma guia, uma página de configuração ou um módulo de tarefa. Para obter mais informações sobre o fluxo de autenticação baseada na Web, consulte:

* [Adicionar autenticação ao bot do Teams](~/bots/how-to/authentication/add-authentication.md) descreve como usar o fluxo de autenticação baseada na Web com um bot de conversa.
* [O fluxo de autenticação nas guias](~/tabs/how-to/authentication/auth-flow-tab.md) descreve como a autenticação de guia funciona no Teams. Isso mostra um típico fluxo de autenticação baseado na Web usado para guias.
* [A autenticação AAD em guias](~/tabs/how-to/authentication/auth-tab-AAD.md) descreve como se conectar ao AAD de dentro de uma guia no aplicativo no Teams.
* [A autenticação silenciosa do AAD](~/tabs/how-to/authentication/auth-silent-AAD.md) descreve como reduzir as solicitações de login ou consentimento no aplicativo usando o AAD.
* [.Net, C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) ou [JavaScript ou Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) fornece exemplos de autenticação baseada na Web.

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>O fluxo OAuthPrompt para bots de conversa

O OAuthPrompt da Estrutura de Bot do Azure facilita a autenticação para aplicativos que usam bots de conversa. Use o serviço de token do Azure Bot Framework para ajudar no cache de tokens.

Para obter mais informações sobre como usar o OAuthPrompt, consulte:

* [A visão geral do fluxo de autenticação](~/bots/how-to/authentication/auth-flow-bot.md) de bot descreve como a autenticação funciona em um bot no aplicativo no Teams. Isso mostra um fluxo de autenticação não baseado na Web usado para bots na Web, aplicativos da área de trabalho e aplicativos móveis do Teams.
* [A autenticação](~/bots/how-to/authentication/add-authentication.md) bot descreve como adicionar a autenticação OAuth ao bot do Teams.
* [.Net, C#](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) ou [JavaScript ou Node.js](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) fornece um exemplo de SDK de autenticação de Bot v3.

## <a name="configure-the-identity-provider"></a>Configurar o provedor de identidade

Independentemente do fluxo de autenticação do aplicativo, configure o provedor de identidade para se comunicar com o aplicativo teams. A maioria dos exemplos e passo a passo lida principalmente com o uso do AAD como provedor de identidade. No entanto, os conceitos se aplicam independentemente do provedor de identidade.

Para obter mais informações, [consulte a configuração de um provedor de identidade.](~/concepts/authentication/configure-identity-provider.md)
