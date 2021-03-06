---
title: Configurar provedores de identidade OAuth 2.0
description: Descreve como configurar provedores de identidade com foco no Azure AD
ms.topic: how-to
localization_priority: Normal
keywords: autenticação do teams Provedor de identidade Oauth do AAD
ms.openlocfilehash: ffcf376ea6c4f1a94d797413af22af867dbd5b53
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020853"
---
# <a name="configure-identity-providers"></a>Configurar provedores de identidade

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a>Configurando um aplicativo para usar Azure Active Directory como um provedor de identidade

Os provedores de identidade que suportam o OAuth 2.0 não autenticam solicitações de aplicativos desconhecidos; os aplicativos devem ser registrados com antecedência. Para fazer isso com o Azure AD, siga estas etapas:

1. Abra o [Portal de Registro de Aplicativos](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Selecione seu aplicativo para exibir suas propriedades ou clique no botão "Novo Registro". Encontre a **seção Redirecionar URI** para o aplicativo.

3. No menu suspenso, certifique-se **de que a Web** está selecionada. Atualize a URL para o ponto de extremidade de autenticação. Para os aplicativos de exemplo TypeScript/Node.js e C# no GitHub, as URLs de redirecionamento serão semelhantes a esta:

    URLs de redirecionamento: `https://<hostname>/bot-auth/simple-start`

Substitua `<hostname>` pelo host real. Pode ser um site de hospedagem dedicado, como o Azure, o Glitch ou um túnel ngrok para o localhost em sua máquina de desenvolvimento, como `abcd1234.ngrok.io` . Você pode não ter essas informações ainda se não tiver concluído ou hospedado seu aplicativo (ou o aplicativo de exemplo mencionado acima), mas sempre poderá retornar a essa página quando essas informações são conhecidas.

## <a name="other-authentication-providers"></a>Outros provedores de autenticação

* **LinkedIn** Siga as instruções em [Configurando seu aplicativo LinkedIn](/linkedin/talent/apply-with-linkedin)

* **Google** Obter credenciais de cliente OAuth 2.0 do [Console da API do Google](https://console.developers.google.com/)
