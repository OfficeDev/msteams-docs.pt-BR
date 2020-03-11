---
title: Publicar publicação
description: O que fazer após a publicação do aplicativo
keywords: publicar o Microsoft Teams postar certificado de atualização
ms.openlocfilehash: 54d0615c262e45729a36f556c3eda3b810d2a097
ms.sourcegitcommit: 2a84a3c8b10771e37ce51bf603a967633947a3e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "42582857"
---
# <a name="maintain-and-support-your-published-app"></a><span data-ttu-id="2f1ea-104">Manter e dar suporte ao aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="2f1ea-104">Maintain and support your published app</span></span> 

<span data-ttu-id="2f1ea-105">Depois que o aplicativo é aprovado e listado no catálogo de aplicativos públicos, você pode aumentar seu alcance obtendo a certificação do aplicativo ou adicionando um botão de download ao seu site.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-105">After your app is approved and listed in the public app catalog, you can increase your reach by achieving app certification, or adding a download button your website.</span></span>

## <a name="application-certificate"></a><span data-ttu-id="2f1ea-106">Certificado de aplicativo</span><span class="sxs-lookup"><span data-stu-id="2f1ea-106">Application Certificate</span></span>

<span data-ttu-id="2f1ea-107">A Microsoft fornece um [programa de certificação de aplicativo](./application-certification.md) que compila suas informações de aplicativo e as apresenta na página de [conformidade e segurança do aplicativo do Microsoft Teams](https://aka.ms/AppCertification).</span><span class="sxs-lookup"><span data-stu-id="2f1ea-107">Microsoft provides a [Application Certification program](./application-certification.md) that compiles your app information and presents it on [Microsoft Teams App Security and Compliance Page](https://aka.ms/AppCertification).</span></span> <span data-ttu-id="2f1ea-108">Essas informações destinam-se a ajudar os administradores a escolher aplicativos seguros para suas organizações.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-108">This information is intended to help admins to choose apps that are safe for their organizations.</span></span>

## <a name="add-a-download-button-to-your-product-site"></a><span data-ttu-id="2f1ea-109">Adicionar um botão de download ao seu site do produto</span><span class="sxs-lookup"><span data-stu-id="2f1ea-109">Add a download button to your product site</span></span>

<span data-ttu-id="2f1ea-110">Se seu aplicativo estiver no Microsoft Teams Store, você poderá gerar um link para o seu site que inicia o Teams e mostra uma caixa de diálogo de consentimento e instalação para que os usuários adicionem o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-110">If your app is in the Microsoft Teams store, you can generate a link for your website that launches Teams and shows a consent and installation dialog for users to add the app.</span></span>
<span data-ttu-id="2f1ea-111">O formato é: `https://teams.microsoft.com/l/app/<appId>` onde AppID é o GUID que eles declaram no manifesto enviado.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-111">The format is:  `https://teams.microsoft.com/l/app/<appId>` where appID is the GUID they declare in the submitted manifest.</span></span>
<span data-ttu-id="2f1ea-112">Exemplo: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` é o link para instalar o Trello.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-112">Example: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` is the link to install Trello.</span></span>

## <a name="updating-your-existing-teams-app"></a><span data-ttu-id="2f1ea-113">Atualizando seu aplicativo do teams existente</span><span class="sxs-lookup"><span data-stu-id="2f1ea-113">Updating your existing Teams app</span></span>

* <span data-ttu-id="2f1ea-114">Não use o botão *Adicionar um novo aplicativo* para reenviar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-114">Do not use the *Add a new app* button to resubmit your app.</span></span> <span data-ttu-id="2f1ea-115">Em vez disso, use o bloco para seu aplicativo na guia Visão geral.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-115">Use the tile for your app on the Overview tab instead.</span></span>
* <span data-ttu-id="2f1ea-116">O appId no manifesto atualizado deve ser igual ao do manifesto atual, com um número de versão incrementado.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-116">The appId in the updated manifest should be the same as in the current manifest, with an incremented version number.</span></span>
* <span data-ttu-id="2f1ea-117">Aumente o número da versão no manifesto se você fizer alterações de manifesto no seu envio.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-117">Increment your version number in the manifest if you make any manifest changes to your submission.</span></span>
* <span data-ttu-id="2f1ea-118">Envios atualizados são necessários para passar por um novo processo de revisão e validação.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-118">Updated submissions are required to undergo a new review and validation process.</span></span>


### <a name="when-does-updating-your-app-trigger-the-user-consent-flow"></a><span data-ttu-id="2f1ea-119">Quando a atualização do aplicativo dispara o fluxo de consentimento do usuário?</span><span class="sxs-lookup"><span data-stu-id="2f1ea-119">When does updating your app trigger the user consent flow?</span></span>

<span data-ttu-id="2f1ea-120">Quando um usuário instala o aplicativo uma das primeiras coisas que eles fazem é o consentimento para dar permissão ao aplicativo para acessar os serviços e informações de que o aplicativo precisa para realizar o trabalho.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-120">When a user installs your application one of the first things they do is consent to give the app permission to access the services and information that the app needs to do its job.</span></span> <span data-ttu-id="2f1ea-121">Ao atualizar seu aplicativo, isso pode disparar novamente esse comportamento de consentimento, especialmente se você tiver feito uma ou mais das seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="2f1ea-121">When you update your app, that can re-trigger this consent behavior, particularly if you have made one or more of the following changes:</span></span>

* <span data-ttu-id="2f1ea-122">Adição de um novo recurso a um aplicativo, como a adição de um bot a um aplicativo somente de tabulação.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-122">Adding a new capability to an app such as adding a bot to an tab only app.</span></span>
* <span data-ttu-id="2f1ea-123">Alterar a matriz de permissões no manifesto.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-123">Changing the permissions array in the manifest.</span></span>
* <span data-ttu-id="2f1ea-124">Incrementando o número de versão do aplicativo em seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="2f1ea-124">Incrementing your app version number in your manifest.</span></span>
