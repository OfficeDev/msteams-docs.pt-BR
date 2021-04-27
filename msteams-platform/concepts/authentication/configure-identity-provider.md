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
# <a name="configure-identity-providers"></a><span data-ttu-id="d02eb-104">Configurar provedores de identidade</span><span class="sxs-lookup"><span data-stu-id="d02eb-104">Configure identity providers</span></span>

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a><span data-ttu-id="d02eb-105">Configurando um aplicativo para usar o Azure Active Directory como um provedor de identidade</span><span class="sxs-lookup"><span data-stu-id="d02eb-105">Configuring an application to use Azure Active Directory as an identity provider</span></span>

<span data-ttu-id="d02eb-106">Os provedores de identidade que suportam o OAuth 2.0 não autenticam solicitações de aplicativos desconhecidos; os aplicativos devem ser registrados com antecedência.</span><span class="sxs-lookup"><span data-stu-id="d02eb-106">Identity providers supporting OAuth 2.0 will not authenticate requests from unknown applications; applications must be registered ahead of time.</span></span> <span data-ttu-id="d02eb-107">Para fazer isso com o Azure AD, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d02eb-107">To do this with Azure AD, follow these steps:</span></span>

1. <span data-ttu-id="d02eb-108">Abra o [Portal de Registro de Aplicativos](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).</span><span class="sxs-lookup"><span data-stu-id="d02eb-108">Open the [Application Registration Portal](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).</span></span>

2. <span data-ttu-id="d02eb-109">Selecione seu aplicativo para exibir suas propriedades ou clique no botão "Novo Registro".</span><span class="sxs-lookup"><span data-stu-id="d02eb-109">Select your app to view its properties, or click the "New Registration" button.</span></span> <span data-ttu-id="d02eb-110">Encontre a **seção Redirecionar URI** para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d02eb-110">Find the **Redirect URI** section for the app.</span></span>

3. <span data-ttu-id="d02eb-111">No menu suspenso, certifique-se **de que a Web** está selecionada.</span><span class="sxs-lookup"><span data-stu-id="d02eb-111">In the dropdown menu, make sure **Web** is selected.</span></span> <span data-ttu-id="d02eb-112">Atualize a URL para o ponto de extremidade de autenticação.</span><span class="sxs-lookup"><span data-stu-id="d02eb-112">Update the URL to your authentication endpoint.</span></span> <span data-ttu-id="d02eb-113">Para os aplicativos de exemplo TypeScript/Node.js e C# no GitHub, as URLs de redirecionamento serão semelhantes a esta:</span><span class="sxs-lookup"><span data-stu-id="d02eb-113">For the TypeScript/Node.js and C# sample apps on GitHub, the redirect URLs will be similar to this:</span></span>

    <span data-ttu-id="d02eb-114">URLs de redirecionamento: `https://<hostname>/bot-auth/simple-start`</span><span class="sxs-lookup"><span data-stu-id="d02eb-114">Redirect URLs: `https://<hostname>/bot-auth/simple-start`</span></span>

<span data-ttu-id="d02eb-115">Substitua `<hostname>` pelo host real.</span><span class="sxs-lookup"><span data-stu-id="d02eb-115">Replace `<hostname>` with your actual host.</span></span> <span data-ttu-id="d02eb-116">Pode ser um site de hospedagem dedicado, como o Azure, o Glitch ou um túnel ngrok para o localhost em sua máquina de desenvolvimento, como `abcd1234.ngrok.io` .</span><span class="sxs-lookup"><span data-stu-id="d02eb-116">This might be a dedicated hosting site such as Azure, Glitch, or an ngrok tunnel to localhost on your development machine such as `abcd1234.ngrok.io`.</span></span> <span data-ttu-id="d02eb-117">Você pode não ter essas informações ainda se não tiver concluído ou hospedado seu aplicativo (ou o aplicativo de exemplo mencionado acima), mas sempre poderá retornar a essa página quando essas informações são conhecidas.</span><span class="sxs-lookup"><span data-stu-id="d02eb-117">You may not have this information yet if you have not completed or hosted your app (or the sample app mentioned above), but you can always return to this page when that information is known.</span></span>

## <a name="other-authentication-providers"></a><span data-ttu-id="d02eb-118">Outros provedores de autenticação</span><span class="sxs-lookup"><span data-stu-id="d02eb-118">Other authentication providers</span></span>

* <span data-ttu-id="d02eb-119">**LinkedIn** Siga as instruções em [Configurando seu aplicativo LinkedIn](/linkedin/talent/apply-with-linkedin)</span><span class="sxs-lookup"><span data-stu-id="d02eb-119">**LinkedIn** Follow the instructions in [Configuring your LinkedIn application](/linkedin/talent/apply-with-linkedin)</span></span>

* <span data-ttu-id="d02eb-120">**Google** Obter credenciais de cliente OAuth 2.0 do [Console da API do Google](https://console.developers.google.com/)</span><span class="sxs-lookup"><span data-stu-id="d02eb-120">**Google** Obtain OAuth 2.0 client credentials from the [Google API Console](https://console.developers.google.com/)</span></span>
