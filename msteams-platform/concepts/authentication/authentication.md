---
title: Autenticação de usuários de aplicativos
description: Descreve a autenticação no Teams e como usá-la nos aplicativos
ms.topic: conceptual
ms.localizationpriority: high
keywords: autenticação de equipes OAuth SSO Microsoft Azure Active Directory (Azure AD)
ms.openlocfilehash: f5aecf2791d03795229d3b37c5fc8784de992326
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111399"
---
# <a name="authenticate-users-in-microsoft-teams"></a>Autenticar usuários no Microsoft Teams

> [!Note]
> A autenticação baseada na Web em clientes móveis requer a versão 1.4.1 ou posterior do SDK do cliente JavaScript do Teams.

Para acessar as informações do usuário protegidas pelo Azure Active Directory e acessar dados de serviços como Facebook e Twitter, o aplicativo estabelece uma conexão confiável com esses provedores. Se o aplicativo usar APIs do Microsoft Graph no escopo do usuário, autentique o usuário para recuperar os tokens de autenticação apropriados.

No Teams, há dois fluxos de autenticação diferentes para o aplicativo. Execute um fluxo de autenticação tradicional baseado na web em uma [página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md) incorporada em uma guia, página de configuração ou módulo de tarefa. Se o aplicativo contiver um bot de conversação, use o fluxo OAuthPrompt e, opcionalmente, o serviço de token do Bot Framework do Azure para autenticar um usuário como parte de uma conversa.

## <a name="web-based-authentication-flow"></a>Fluxo de autenticação baseado na Web

Use o fluxo de autenticação baseado na web para [guias](~/tabs/what-are-tabs.md) e opte por usá-lo com [bots de conversação](~/bots/what-are-bots.md) ou [extensões de mensagem](~/messaging-extensions/what-are-messaging-extensions.md). Use o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) em uma página de conteúdo da web para ativar a autenticação. Depois de habilitar a autenticação, insira a página de conteúdo em uma guia, uma página de configuração ou um módulo de tarefa. Para obter mais informações sobre o fluxo de autenticação baseado na Web, consulte:

* [Adicionar autenticação ao bot do Teams](~/bots/how-to/authentication/add-authentication.md) descreve como usar o fluxo de autenticação baseado na Web com um bot conversacional.
* [Fluxo de autenticação em guias](~/tabs/how-to/authentication/auth-flow-tab.md) descreve como a autenticação de guia funciona no Teams. Isso mostra um fluxo de autenticação baseado na Web típico usado para guias.
* [Autenticação do Azure Active Directory em guias](~/tabs/how-to/authentication/auth-tab-AAD.md) descreve como se conectar ao Azure Active Directory de dentro de uma guia no aplicativo no Teams.
* [Autenticação silenciosa Azure Active Directory](~/tabs/how-to/authentication/auth-silent-AAD.md) descreve como reduzir os prompts de entrada ou consentimento no aplicativo usando o Azure Active Directory.
* [.Net ou C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) ou [JavaScript ou Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) fornece exemplos de autenticação baseada na web.

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>O fluxo OAuthPrompt para bots de conversação

O OAuthPrompt do Bot Framework Azure facilita a autenticação para aplicativos que usam bots de conversa. Use o serviço Bot Framework token do Azure para auxiliar no cache de tokens.

Para obter mais informações sobre como usar o OAuthPrompt, consulte:

* [Visão geral do fluxo de autenticação de bot](~/bots/how-to/authentication/auth-flow-bot.md) descreve como a autenticação funciona em um bot no aplicativo no Teams. Isso mostra um fluxo de autenticação não baseado na Web usado para bots na Web do Teams, no aplicativo de desktop e nos aplicativos móveis.
* [Autenticação de bot](~/bots/how-to/authentication/add-authentication.md) descreve como adicionar autenticação OAuth ao bot do Teams.

## <a name="code-sample"></a>Exemplo de código

fornece amostra de SDK de autenticação de bot v3.

| **Nome de exemplo** | **Descrição** | **.NET** | **Node.js** | **Python** |
|---------------|------------|------------|-------------|---------------|
| Autenticação de bot | Esta amostra mostra como começar com a autenticação em um bot para o Microsoft Teams. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth) |
| SSO de guia, bot e extensão de mensagem (ME) | Este exemplo mostra o SSO para Tab, Bot e ME – pesquisa, ação, linkunfurl. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) | Não disponível |

## <a name="configure-the-identity-provider"></a>Configurar o provedor de identidade

Independentemente do fluxo de autenticação do aplicativo, configure o provedor de identidade para se comunicar com o aplicativo Teams. A maioria das amostras e orientações lidam principalmente com o uso do Azure Active Directory como provedor de identidade. Os conceitos, no entanto, se aplicam independentemente do provedor de identidade.

Para obter mais informações, consulte [como configurar um provedor de identidade](~/concepts/authentication/configure-identity-provider.md).

## <a name="third-party-cookies-on-ios"></a>Cookies de terceiros no iOS

Após a atualização do iOS 14, a Apple bloqueou o acesso de [cookies de terceiros](https://webkit.org/blog/10218/full-third-party-cookie-blocking-and-more/) para todos os aplicativos por padrão. Portanto, os aplicativos que utilizam cookies de terceiros para autenticação em suas guias de canal ou bate-papo e aplicativos pessoais não poderão concluir seus fluxos de trabalho de autenticação em clientes do Teams iOS. Para estar em conformidade com os requisitos de privacidade e segurança, você deve migrar para um sistema baseado em token ou usar cookies primários para os fluxos de trabalho de autenticação do usuário.

## <a name="see-also"></a>Confira também

* [Fluxo de autenticação do Microsoft Teams para guias](~/tabs/how-to/authentication/auth-flow-tab.md)
* [Suporte de logon único para bots](~/bots/how-to/authentication/auth-aad-sso-bots.md)
* [Adicionar autenticação à sua extensão de mensagens](~/messaging-extensions/how-to/add-authentication.md)
