---
title: Configurar provedores de identidade OAuth 2.0
description: Descreve como configurar provedores de identidade com foco no Microsoft Azure Active Directory (Azure AD)
ms.topic: how-to
ms.localizationpriority: medium
keywords: autenticação do teams O provedor de identidade oauth do Azure AD
ms.openlocfilehash: b35f28f2cb306a6dfc3ae3151616925da1525069
ms.sourcegitcommit: b9af51e24c9befcf46945400789e750c34723e56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62821350"
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
