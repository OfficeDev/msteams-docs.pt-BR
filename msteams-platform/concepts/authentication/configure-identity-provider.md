---
title: Configurando provedores de identidade OAuth 2,0
description: Descreve como configurar provedores de identidade com foco no Azure AD
keywords: provedor de identidade OAuth do AAD de autenticação do Microsoft Teams
ms.openlocfilehash: 799b0c20cda64456a4610acbdbedf758989bee55
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672834"
---
# <a name="configuring-identity-providers"></a>Configurando provedores de identidade

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a>Configurando um aplicativo para usar o Azure Active Directory como um provedor de identidade

Os provedores de identidade que dão suporte ao OAuth 2,0 não autenticarão solicitações de aplicativos desconhecidos; os aplicativos devem ser registrados antes do tempo. Para fazer isso com o Azure AD, siga estas etapas:

1. Abra o [portal de registro do aplicativo](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Selecione seu aplicativo para exibir suas propriedades ou clique no botão "novo registro". Encontre a seção **Redirecionar URI** para o aplicativo.

3. No menu suspenso, verifique se a **Web** está selecionada. Atualize a URL para o ponto de extremidade de autenticação. Para os aplicativos de amostra do TypeScript/node. js e C# no GitHub, as URLs de redirecionamento serão semelhantes a esta:

    Redirecionar URLs:`https://<hostname>/bot-auth/simple-start`

Substitua `<hostname>` pelo host real. Este pode ser um site de hospedagem dedicado, como o Azure, falha ou um túnel ngrok para localhost no seu computador de desenvolvimento `abcd1234.ngrok.io`, como. Talvez você ainda não tenha essas informações se não tiver concluído ou hospedado seu aplicativo (ou o aplicativo de exemplo mencionado acima), mas você sempre poderá retornar a essa página quando essa informação for conhecida.

## <a name="other-authentication-providers"></a>Outros provedores de autenticação

* **LinkedIn** Siga as instruções em [configurando seu aplicativo do LinkedIn](https://developer.linkedin.com/docs/oauth2)

* **Google** Obter credenciais de cliente do OAuth 2,0 do [console do Google API](https://console.developers.google.com/)
