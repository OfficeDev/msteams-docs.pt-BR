---
title: Autenticando usuários de aplicativos
description: Descreve a autenticação no Teams e como usá-la nos aplicativos
ms.topic: conceptual
ms.localizationpriority: medium
keywords: teams authentication OAuth SSO Microsoft Azure Active Directory (Azure AD)
ms.openlocfilehash: 811b8917297ad8fe1420f4887983b93f43cd73b3
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103955"
---
# <a name="authenticate-users-in-microsoft-teams"></a>Autenticar usuários no Microsoft Teams

> [!Note]
> A autenticação baseada na Web em clientes móveis requer a versão 1.4.1 ou posterior do SDK do Teams cliente JavaScript.

Para acessar informações do usuário protegidas pelo Azure AD e acessar dados de serviços como Facebook e Twitter, o aplicativo estabelece uma conexão confiável com esses provedores. Se o aplicativo usar apIs do Microsoft Graph no escopo do usuário, autentique o usuário para recuperar os tokens de autenticação apropriados.

No Teams, há dois fluxos de autenticação diferentes para o aplicativo. Execute um fluxo de autenticação tradicional baseado na Web em uma página [de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md) inserida em uma guia, uma página de configuração ou um módulo de tarefa. Se o aplicativo contiver um bot de conversação, use o fluxo OAuthPrompt e, opcionalmente, o serviço de token do Bot Framework do Azure para autenticar um usuário como parte de uma conversa.

## <a name="web-based-authentication-flow"></a>Fluxo de autenticação baseado na Web

Use o fluxo de autenticação baseado na Web para [guias](~/tabs/what-are-tabs.md) e opte por usá-lo com [bots](~/bots/what-are-bots.md) de conversação ou [extensões de mensagem](~/messaging-extensions/what-are-messaging-extensions.md). Use o [Microsoft Teams SDK do cliente JavaScript](/javascript/api/overview/msteams-client) em uma página de conteúdo da Web para habilitar a autenticação. Depois de habilitar a autenticação, insira a página de conteúdo em uma guia, uma página de configuração ou um módulo de tarefa. Para obter mais informações sobre o fluxo de autenticação baseado na Web, consulte:

* [Adicionar autenticação ao Teams bot](~/bots/how-to/authentication/add-authentication.md) descreve como usar o fluxo de autenticação baseado na Web com um bot de conversa.
* [O fluxo de autenticação em guias](~/tabs/how-to/authentication/auth-flow-tab.md) descreve como a autenticação de guia funciona Teams. Isso mostra um fluxo de autenticação baseado na Web típico usado para guias.
* [A autenticação do Azure AD](~/tabs/how-to/authentication/auth-tab-AAD.md) em guias descreve como se conectar ao Azure AD de dentro de uma guia no aplicativo no Teams.
* [Autenticação silenciosa O Azure AD](~/tabs/how-to/authentication/auth-silent-AAD.md) descreve como reduzir os prompts de entrada ou consentimento no aplicativo usando o Azure AD.
* [.Net, C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) ou [JavaScript ou Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) fornece exemplos para autenticação baseada na Web.

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>O fluxo OAuthPrompt para bots conversacionais

O OAuthPrompt do Bot Framework Azure facilita a autenticação para aplicativos que usam bots de conversa. Use o serviço Bot Framework token do Azure para auxiliar no cache de tokens.

Para obter mais informações sobre como usar o OAuthPrompt, consulte:

* [A visão geral do fluxo de](~/bots/how-to/authentication/auth-flow-bot.md) autenticação de bot descreve como a autenticação funciona em um bot no aplicativo Teams. Isso mostra um fluxo de autenticação não baseado na Web usado para bots Teams web, aplicativo da área de trabalho e aplicativos móveis.
* [A autenticação de bot](~/bots/how-to/authentication/add-authentication.md) descreve como adicionar a autenticação OAuth ao Teams bot.

## <a name="code-sample"></a>Exemplo de código

fornece exemplo de SDK de autenticação de bot v3.

| **Nome de exemplo** | **Descrição** | **.NET** | **Node.js** | **Python** |
|---------------|------------|------------|-------------|---------------|
| Autenticação de bot | Este exemplo mostra como começar a usar a autenticação em um bot para Microsoft Teams. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth) |
| SSO de Tab, Bot e Extensão de Mensagem (ME) | Este exemplo mostra o SSO para Tab, Bot e ME – pesquisa, ação, linkunfurl. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) | Não disponível |

## <a name="configure-the-identity-provider"></a>Configurar o provedor de identidade

Independentemente do fluxo de autenticação do aplicativo, configure o provedor de identidade para se comunicar com o Teams aplicativo. A maioria dos exemplos e explicações passo a passo lida principalmente com o uso do Azure AD como o provedor de identidade. No entanto, os conceitos se aplicam independentemente do provedor de identidade.

Para obter mais informações, [consulte configurar um provedor de identidade](~/concepts/authentication/configure-identity-provider.md).

## <a name="third-party-cookies-on-ios"></a>Cookies de terceiros no iOS

Após a atualização do iOS 14, a Apple bloqueou o acesso a [cookies](https://webkit.org/blog/10218/full-third-party-cookie-blocking-and-more/) de terceiros para todos os aplicativos por padrão. Portanto, os aplicativos que aproveitam cookies de terceiros para autenticação em suas guias canal ou chat e aplicativos pessoais não poderão concluir seus fluxos de trabalho de autenticação em clientes Teams iOS. Para estar em conformidade com os requisitos de Privacidade e Segurança, você deve migrar para um sistema baseado em token ou usar cookies de terceiros para os fluxos de trabalho de autenticação do usuário.

## <a name="see-also"></a>Confira também

* [Fluxo de autenticação do Microsoft Teams para guias](~/tabs/how-to/authentication/auth-flow-tab.md)
* [Suporte de logon único para bots](~/bots/how-to/authentication/auth-aad-sso-bots.md)
* [Adicionar autenticação à extensão de mensagem](~/messaging-extensions/how-to/add-authentication.md)
