---
title: Upload seu aplicativo personalizado
description: Aprenda a carregar seu aplicativo de lado em Microsoft Teams. O sideloading é comum ao testar e depurar um aplicativo durante o desenvolvimento.
ms.topic: how-to
author: KirtiPereira
ms.author: surbhigupta
ms.openlocfilehash: 39e94317ceb615ecd7d5481276ffafed5afe5cde
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565190"
---
# <a name="upload-your-app-in-microsoft-teams"></a><span data-ttu-id="7b07d-104">Upload seu aplicativo em Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7b07d-104">Upload your app in Microsoft Teams</span></span>

<span data-ttu-id="7b07d-105">Você pode carregar Microsoft Teams aplicativos sem ter que publicar na sua organização ou na loja Teams.</span><span class="sxs-lookup"><span data-stu-id="7b07d-105">You can sideload Microsoft Teams apps without having to publish to your organization or the Teams store.</span></span> <span data-ttu-id="7b07d-106">Isso faz sentido nos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="7b07d-106">This makes sense in the following scenarios:</span></span>

* <span data-ttu-id="7b07d-107">Você quer testar e depurar um aplicativo localmente você mesmo ou com outros desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="7b07d-107">You want to test and debug an app locally yourself or with other developers.</span></span>
* <span data-ttu-id="7b07d-108">Você construiu um aplicativo só para você.</span><span class="sxs-lookup"><span data-stu-id="7b07d-108">You built an app just for yourself.</span></span> <span data-ttu-id="7b07d-109">Por exemplo, para automatizar um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7b07d-109">For example, to automate a workflow.</span></span>
* <span data-ttu-id="7b07d-110">Você construiu um aplicativo para um pequeno conjunto de usuários, como, como, seu grupo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7b07d-110">You built an app for a small set of users, such as, your work group.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7b07d-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7b07d-111">Prerequisites</span></span>

* <span data-ttu-id="7b07d-112">Crie seu [pacote de aplicativos](~/concepts/build-and-test/apps-package.md) e [valide-o](https://dev.teams.microsoft.com/appvalidation.html) para erros.</span><span class="sxs-lookup"><span data-stu-id="7b07d-112">Create your [app package](~/concepts/build-and-test/apps-package.md) and [validate it](https://dev.teams.microsoft.com/appvalidation.html) for errors.</span></span>
* <span data-ttu-id="7b07d-113">[Habilite o upload personalizado de aplicativos](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) em Teams.</span><span class="sxs-lookup"><span data-stu-id="7b07d-113">[Enable custom app uploading](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) in Teams.</span></span>
* <span data-ttu-id="7b07d-114">Certifique-se de que seu aplicativo está em execução e acessível via HTTPs.</span><span class="sxs-lookup"><span data-stu-id="7b07d-114">Make sure that your app is running and accessible via HTTPs.</span></span>

## <a name="upload-your-app"></a><span data-ttu-id="7b07d-115">Carregar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7b07d-115">Upload your app</span></span>

<span data-ttu-id="7b07d-116">Você pode carregar seu aplicativo de lado para uma equipe, bate-papo, reunião ou para uso pessoal, dependendo de como você configurou o escopo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b07d-116">You can sideload your app to a team, chat, meeting, or for personal use depending on how you configured your app's scope.</span></span>

1. <span data-ttu-id="7b07d-117">Faça login no Teams cliente com sua [conta de desenvolvimento Microsoft 365](~/build-your-first-app/build-and-run.md#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="7b07d-117">Log in to the Teams client with your [Microsoft 365 development account](~/build-your-first-app/build-and-run.md#prerequisites).</span></span>
1. <span data-ttu-id="7b07d-118">Selecione **Aplicativos** e escolha **Upload um aplicativo personalizado**.</span><span class="sxs-lookup"><span data-stu-id="7b07d-118">Select **Apps** and choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="7b07d-119">Selecione seu pacote de aplicativo .zip arquivo.</span><span class="sxs-lookup"><span data-stu-id="7b07d-119">Select your app package .zip file.</span></span> <span data-ttu-id="7b07d-120">Uma instalação de monitores de diálogo.</span><span class="sxs-lookup"><span data-stu-id="7b07d-120">An install dialog displays.</span></span>
:::image type="content" source="~/assets/images/build-your-first-app/add-teams-app.png" alt-text="Captura de tela mostrando um exemplo de Teams aplicativo instalar a caixa de diálogo.":::
1. <span data-ttu-id="7b07d-122">Adicione seu aplicativo a Teams.</span><span class="sxs-lookup"><span data-stu-id="7b07d-122">Add your app to Teams.</span></span>

## <a name="troubleshoot-upload-issues"></a><span data-ttu-id="7b07d-123">Solução de problemas de carregamento</span><span class="sxs-lookup"><span data-stu-id="7b07d-123">Troubleshoot upload issues</span></span>

<span data-ttu-id="7b07d-124">Se o aplicativo não conseguir fazer a carga lateral, faça o seguinte até que o problema seja resolvido:</span><span class="sxs-lookup"><span data-stu-id="7b07d-124">If your app fails to sideload, do the following until the issue resolves:</span></span>

1. <span data-ttu-id="7b07d-125">Volte as instruções para [criar seu pacote de aplicativos](../../concepts/build-and-test/apps-package.md).</span><span class="sxs-lookup"><span data-stu-id="7b07d-125">Go back through the instructions for [creating your app package](../../concepts/build-and-test/apps-package.md).</span></span>
1. <span data-ttu-id="7b07d-126">[Valide seu pacote de aplicativos](https://dev.teams.microsoft.com/appvalidation.html) novamente.</span><span class="sxs-lookup"><span data-stu-id="7b07d-126">[Validate your app package](https://dev.teams.microsoft.com/appvalidation.html) again.</span></span>
1. <span data-ttu-id="7b07d-127">Certifique-se de que o manifesto do aplicativo corresponda ao [esquema](../../resources/schema/manifest-schema.md)mais recente .</span><span class="sxs-lookup"><span data-stu-id="7b07d-127">Make sure your app manifest matches the latest [schema](../../resources/schema/manifest-schema.md).</span></span>

## <a name="access-your-app"></a><span data-ttu-id="7b07d-128">Acesse seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7b07d-128">Access your app</span></span>

<span data-ttu-id="7b07d-129">Teams fornece várias maneiras de abrir aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7b07d-129">Teams provides several ways to open apps.</span></span> <span data-ttu-id="7b07d-130">Para obter mais informações, consulte [acessar seus aplicativos em Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).</span><span class="sxs-lookup"><span data-stu-id="7b07d-130">For more information, see [access your apps in Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).</span></span>

## <a name="update-your-app"></a><span data-ttu-id="7b07d-131">Atualize seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7b07d-131">Update your app</span></span>

<span data-ttu-id="7b07d-132">Você não precisa carregar seu aplicativo novamente se fizer alterações de código (estas são refletidas em Teams em tempo real).</span><span class="sxs-lookup"><span data-stu-id="7b07d-132">You don't have to sideload your app again if you make code changes (these are reflected in Teams in real-time).</span></span> <span data-ttu-id="7b07d-133">No entanto, você deve reinstalar se alterar qualquer configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b07d-133">However, you must reinstall if you change any app configurations.</span></span>

## <a name="remove-your-app"></a><span data-ttu-id="7b07d-134">Remova seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7b07d-134">Remove your app</span></span>

<span data-ttu-id="7b07d-135">Para remover seu aplicativo, clique com o botão direito do mouse no ícone do aplicativo em Teams e selecione **Desinstalar**.</span><span class="sxs-lookup"><span data-stu-id="7b07d-135">To remove your app, right click the app icon in Teams and select **Uninstall**.</span></span>

> [!NOTE]
> <span data-ttu-id="7b07d-136">Você não pode remover totalmente a atividade do bot pessoal.</span><span class="sxs-lookup"><span data-stu-id="7b07d-136">You can't remove personal bot activity entirely.</span></span> <span data-ttu-id="7b07d-137">Se você remover o aplicativo e adicioná-lo novamente, uma nova comunicação com o bot anexa à conversa anterior com ele.</span><span class="sxs-lookup"><span data-stu-id="7b07d-137">If you remove the app and add it again, new communication with the bot appends to the previous conversation with it.</span></span>

## <a name="next-step"></a><span data-ttu-id="7b07d-138">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="7b07d-138">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7b07d-139">Use seu aplicativo de Teams</span><span class="sxs-lookup"><span data-stu-id="7b07d-139">Use your Teams app</span></span>](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us)
