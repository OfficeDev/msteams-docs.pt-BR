---
title: Autenticando usuários de aplicativos
description: Descreve a autenticação no Teams e como usá-la nos aplicativos
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Autenticação do teams OAuth SSO AAD
ms.openlocfilehash: 40d5659251b1faff087c6ee6458800ede2a5c840
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155392"
---
# <a name="authenticate-users-in-microsoft-teams"></a>Autenticar usuários no Microsoft Teams

> [!Note]
> A autenticação baseada na Web em clientes móveis requer a versão 1.4.1 ou posterior do SDK do cliente JavaScript do Teams JavaScript.

Para acessar informações do usuário protegidas pelo Azure Active Directory (AAD) e para acessar dados de serviços como Facebook e Twitter, o aplicativo estabelece uma conexão confiável com esses provedores. Se o aplicativo usa APIs Graph Microsoft no escopo do usuário, autenture o usuário para recuperar os tokens de autenticação apropriados.

No Teams, há dois fluxos de autenticação diferentes para o aplicativo. Execute um fluxo de autenticação baseado na Web tradicional em uma página [de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md) inserida em uma guia, uma página de configuração ou um módulo de tarefa. Se o aplicativo contiver um bot de conversação, use o fluxo OAuthPrompt e, opcionalmente, o serviço de token do Bot Framework do Azure para autenticar um usuário como parte de uma conversa.

## <a name="web-based-authentication-flow"></a>Fluxo de autenticação baseado na Web

Use o fluxo de autenticação baseado na Web para [guias](~/tabs/what-are-tabs.md) e escolha usá-lo com [bots](~/bots/what-are-bots.md) de conversa ou extensões [de mensagens.](~/messaging-extensions/what-are-messaging-extensions.md) Use o [Microsoft Teams SDK do cliente JavaScript](/javascript/api/overview/msteams-client) em uma página de conteúdo da Web para habilitar a autenticação. Depois de habilitar a autenticação, insira a página de conteúdo em uma guia, uma página de configuração ou um módulo de tarefa. Para obter mais informações sobre o fluxo de autenticação baseado na Web, consulte:

* [Adicionar autenticação ao bot Teams](~/bots/how-to/authentication/add-authentication.md) descreve como usar o fluxo de autenticação baseado na Web com um bot de conversa.
* [O fluxo de autenticação nas guias](~/tabs/how-to/authentication/auth-flow-tab.md) descreve como a autenticação de tabulação funciona Teams. Isso mostra um fluxo de autenticação baseado na Web típico usado para guias.
* [A autenticação AAD em guias](~/tabs/how-to/authentication/auth-tab-AAD.md) descreve como se conectar ao AAD de dentro de uma guia no aplicativo em Teams.
* [Autenticação silenciosa O AAD](~/tabs/how-to/authentication/auth-silent-AAD.md) descreve como reduzir os prompts de login ou consentimento no aplicativo usando o AAD.
* [O .Net ou C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) ou [JavaScript ou Node.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) fornece exemplos para autenticação baseada na Web.

## <a name="the-oauthprompt-flow-for-conversational-bots"></a>O fluxo OAuthPrompt para bots de conversa

O OAuthPrompt do Bot Framework Azure facilita a autenticação para aplicativos que usam bots de conversa. Use o serviço Bot Framework token do Azure para auxiliar no cache de tokens.

Para obter mais informações sobre como usar o OAuthPrompt, consulte:

* [Visão geral do fluxo de autenticação bot](~/bots/how-to/authentication/auth-flow-bot.md) descreve como a autenticação funciona em um bot no aplicativo em Teams. Isso mostra um fluxo de autenticação não baseado na Web usado para bots em Teams web, aplicativo de área de trabalho e aplicativos móveis.
* [A autenticação](~/bots/how-to/authentication/add-authentication.md) bot descreve como adicionar autenticação OAuth ao Teams bot.

## <a name="code-sample"></a>Exemplo de código

fornece exemplo de SDK de autenticação de bot v3.

| **Nome do exemplo** | **Descrição** | **.NET** | **Node.js** | **Python** |
|---------------|------------|------------|-------------|---------------|
| Autenticação bot | Este exemplo mostra como começar a usar a autenticação em um bot para Microsoft Teams. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth) |
| Guia, Bot e Extensão de Mensagens (ME) SSO | Este exemplo mostra SSO para Tab, Bot e ME - pesquisa, ação, linkunfurl. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) | Não disponível |


## <a name="configure-the-identity-provider"></a>Configurar o provedor de identidade

Independentemente do fluxo de autenticação do aplicativo, configure o provedor de identidade para se comunicar com o Teams aplicativo. A maioria dos exemplos e passo a passo lida principalmente com o uso do AAD como provedor de identidade. No entanto, os conceitos se aplicam independentemente do provedor de identidade.

Para obter mais informações, consulte [configuring an identity provider](~/concepts/authentication/configure-identity-provider.md).
