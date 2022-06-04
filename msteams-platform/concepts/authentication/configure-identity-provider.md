---
title: Configurar provedores de identidade OAuth 2.0
description: Descreve como configurar provedores de identidade com foco no Microsoft Azure Active Directory (Azure AD)
ms.topic: how-to
ms.localizationpriority: medium
keywords: autenticação do teams provedor de identidade oauth do Azure AD
ms.openlocfilehash: 6fb17041e9169b4d5e74295cbb62ea97c8befd0f
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65887566"
---
# <a name="configure-identity-providers"></a>Configurar provedores de identidade

## <a name="configuring-an-application-to-use-azure-ad-as-an-identity-provider"></a>Configurando um aplicativo para usar o Azure AD como um provedor de identidade

Os provedores de identidade que dão suporte ao OAuth 2.0 não autenticam solicitações de aplicativos desconhecidos; os aplicativos devem ser registrados antecipadamente. Para fazer isso com o Azure AD, siga estas etapas:

1. Abra o [Portal de Registro do Aplicativo](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Selecione seu aplicativo para exibir suas propriedades ou selecione o botão "Novo Registro". Localize a seção **URI de direcionamento** para o aplicativo.

3. Selecione **Web** no menu suspenso. Atualize a URL para o ponto de extremidade de autenticação. Para os aplicativos de exemplo TypeScript/Node.js e C# no GitHub, as URLs de redirecionamento serão semelhantes ao seguinte:

    URLs de redirecionamento: `https://<hostname>/bot-auth/simple-start`

Substitua `<hostname>` pelo host real, que pode ser um site de hospedagem dedicado, como Azure, Glitch ou um túnel ngrok para o localhost em seu computador de desenvolvimento, como `abcd1234.ngrok.io`. Talvez você não tenha essas informações se não tiver concluído ou hospedado seu aplicativo (ou o aplicativo de exemplo mencionado acima), mas sempre poderá retornar a esta página quando essas informações forem conhecidas.

## <a name="other-authentication-providers"></a>Outros fornecedores de autenticação

* **LinkedIn:** Siga as instruções em [Configurando seu aplicativo LinkedIn](/linkedin/talent/apply-with-linkedin)

* **Google:** Obtenha credenciais de cliente OAuth 2.0 do [Console de API do Google](https://console.developers.google.com/)

* **Provedores OAuth externos de guias:** Para obter mais informações, consulte [Use provedores OAuth externos](../../tabs/how-to/authentication/auth-oauth-provider.md)

## <a name="see-also"></a>Confira também

* [Autenticar um usuário em um bot do Microsoft Teams](../../resources/bot-v3/bot-authentication/auth-bot-AAD.md)
* [Suporte ao SSO (logon único) para guias](../../tabs/how-to/authentication/tab-sso-overview.md)
* [Autenticar um usuário em uma guia do Microsoft Teams](../../tabs/how-to/authentication/auth-tab-aad.md)
