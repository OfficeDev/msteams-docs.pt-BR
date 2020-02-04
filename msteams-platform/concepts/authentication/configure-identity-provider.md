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
# <a name="configuring-identity-providers"></a><span data-ttu-id="05cc5-104">Configurando provedores de identidade</span><span class="sxs-lookup"><span data-stu-id="05cc5-104">Configuring identity providers</span></span>

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a><span data-ttu-id="05cc5-105">Configurando um aplicativo para usar o Azure Active Directory como um provedor de identidade</span><span class="sxs-lookup"><span data-stu-id="05cc5-105">Configuring an application to use Azure Active Directory as an identity provider</span></span>

<span data-ttu-id="05cc5-106">Os provedores de identidade que dão suporte ao OAuth 2,0 não autenticarão solicitações de aplicativos desconhecidos; os aplicativos devem ser registrados antes do tempo.</span><span class="sxs-lookup"><span data-stu-id="05cc5-106">Identity providers supporting OAuth 2.0 will not authenticate requests from unknown applications; applications must be registered ahead of time.</span></span> <span data-ttu-id="05cc5-107">Para fazer isso com o Azure AD, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="05cc5-107">To do this with Azure AD, follow these steps:</span></span>

1. <span data-ttu-id="05cc5-108">Abra o [portal de registro do aplicativo](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).</span><span class="sxs-lookup"><span data-stu-id="05cc5-108">Open the [Application Registration Portal](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).</span></span>

2. <span data-ttu-id="05cc5-109">Selecione seu aplicativo para exibir suas propriedades ou clique no botão "novo registro".</span><span class="sxs-lookup"><span data-stu-id="05cc5-109">Select your app to view its properties, or click the "New Registration" button.</span></span> <span data-ttu-id="05cc5-110">Encontre a seção **Redirecionar URI** para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="05cc5-110">Find the **Redirect URI** section for the app.</span></span>

3. <span data-ttu-id="05cc5-111">No menu suspenso, verifique se a **Web** está selecionada.</span><span class="sxs-lookup"><span data-stu-id="05cc5-111">In the dropdown menu, make sure **Web** is selected.</span></span> <span data-ttu-id="05cc5-112">Atualize a URL para o ponto de extremidade de autenticação.</span><span class="sxs-lookup"><span data-stu-id="05cc5-112">Update the URL to your authentication endpoint.</span></span> <span data-ttu-id="05cc5-113">Para os aplicativos de amostra do TypeScript/node. js e C# no GitHub, as URLs de redirecionamento serão semelhantes a esta:</span><span class="sxs-lookup"><span data-stu-id="05cc5-113">For the TypeScript/Node.js and C# sample apps on GitHub, the redirect URLs will be similar to this:</span></span>

    <span data-ttu-id="05cc5-114">Redirecionar URLs:`https://<hostname>/bot-auth/simple-start`</span><span class="sxs-lookup"><span data-stu-id="05cc5-114">Redirect URLs: `https://<hostname>/bot-auth/simple-start`</span></span>

<span data-ttu-id="05cc5-115">Substitua `<hostname>` pelo host real.</span><span class="sxs-lookup"><span data-stu-id="05cc5-115">Replace `<hostname>` with your actual host.</span></span> <span data-ttu-id="05cc5-116">Este pode ser um site de hospedagem dedicado, como o Azure, falha ou um túnel ngrok para localhost no seu computador de desenvolvimento `abcd1234.ngrok.io`, como.</span><span class="sxs-lookup"><span data-stu-id="05cc5-116">This might be a dedicated hosting site such as Azure, Glitch, or an ngrok tunnel to localhost on your development machine such as `abcd1234.ngrok.io`.</span></span> <span data-ttu-id="05cc5-117">Talvez você ainda não tenha essas informações se não tiver concluído ou hospedado seu aplicativo (ou o aplicativo de exemplo mencionado acima), mas você sempre poderá retornar a essa página quando essa informação for conhecida.</span><span class="sxs-lookup"><span data-stu-id="05cc5-117">You may not have this information yet if you have not completed or hosted your app (or the sample app mentioned above), but you can always return to this page when that information is known.</span></span>

## <a name="other-authentication-providers"></a><span data-ttu-id="05cc5-118">Outros provedores de autenticação</span><span class="sxs-lookup"><span data-stu-id="05cc5-118">Other authentication providers</span></span>

* <span data-ttu-id="05cc5-119">**LinkedIn** Siga as instruções em [configurando seu aplicativo do LinkedIn](https://developer.linkedin.com/docs/oauth2)</span><span class="sxs-lookup"><span data-stu-id="05cc5-119">**LinkedIn** Follow the instructions in [Configuring your LinkedIn application](https://developer.linkedin.com/docs/oauth2)</span></span>

* <span data-ttu-id="05cc5-120">**Google** Obter credenciais de cliente do OAuth 2,0 do [console do Google API](https://console.developers.google.com/)</span><span class="sxs-lookup"><span data-stu-id="05cc5-120">**Google** Obtain OAuth 2.0 client credentials from the [Google API Console](https://console.developers.google.com/)</span></span>
