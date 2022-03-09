---
title: Configurar provedores de identidade OAuth 2.0
description: Descreve como configurar provedores de identidade com foco no Microsoft Azure Active Directory (Azure AD)
ms.topic: how-to
ms.localizationpriority: medium
keywords: autenticação do teams O provedor de identidade oauth do Azure AD
ms.openlocfilehash: 36e81839b1837fca8a124b60701c3d5f95608851
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63356410"
---
# <a name="configure-identity-providers"></a>Configurar provedores de identidade

## <a name="configuring-an-application-to-use-azure-ad-as-an-identity-provider"></a>Configurando um aplicativo para usar o Azure AD como um provedor de identidade

Os provedores de identidade que suportam o OAuth 2.0 não autenticam solicitações de aplicativos desconhecidos; os aplicativos devem ser registrados com antecedência. Para fazer isso com o Azure AD, siga estas etapas:

1. Abra o [Portal de Registro de Aplicativos](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Selecione seu aplicativo para exibir suas propriedades ou selecione o botão "Novo Registro". Encontre a **seção Redirecionar URI** para o aplicativo.

3. Selecione **Web** no menu suspenso. Atualize a URL para o ponto de extremidade de autenticação. Para os aplicativos de exemplo TypeScript/Node.js e C# no GitHub, as URLs de redirecionamento serão semelhantes às seguintes:

    URLs de redirecionamento: `https://<hostname>/bot-auth/simple-start`

Substitua `<hostname>` pelo host real, que pode ser um site de hospedagem dedicado, como o Azure, o Glitch ou um túnel de ngrok para o host local `abcd1234.ngrok.io`em sua máquina de desenvolvimento, como . Você pode não ter essas informações se ainda não tiver concluído ou hospedado seu aplicativo (ou o aplicativo de exemplo mencionado acima), mas sempre poderá retornar a essa página quando essas informações são conhecidas.

## <a name="other-authentication-providers"></a>Outros provedores de autenticação

* **LinkedIn:** Siga as instruções em [Configurando seu aplicativo LinkedIn](/linkedin/talent/apply-with-linkedin)

* **Google:** Obter credenciais de cliente OAuth 2.0 do [Console da API do Google](https://console.developers.google.com/)

* **Provedores OAuth externos de guias:** Para obter mais informações, [consulte Usar provedores OAuth externos](../../tabs/how-to/authentication/auth-oauth-provider.md)

## <a name="see-also"></a>Confira também 

* [Autenticar um usuário em um Microsoft Teams bot](../../resources/bot-v3/bot-authentication/auth-bot-AAD.md)
* [Suporte ao SSO (logon único) para guias](../../tabs/how-to/authentication/auth-aad-sso.md)
* [Autenticar um usuário em uma Microsoft Teams guia](../../tabs/how-to/authentication/auth-tab-aad.md)