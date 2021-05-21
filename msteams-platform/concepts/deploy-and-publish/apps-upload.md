---
title: Upload seu aplicativo personalizado
description: Saiba como fazer sideload do aplicativo Microsoft Teams. O sideload é comum ao testar e depurar um aplicativo durante o desenvolvimento.
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
# <a name="upload-your-app-in-microsoft-teams"></a><span data-ttu-id="ff1ad-104">Upload seu aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ff1ad-104">Upload your app in Microsoft Teams</span></span>

<span data-ttu-id="ff1ad-105">Você pode fazer sideload Microsoft Teams aplicativos sem precisar publicar na sua organização ou no Teams store.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-105">You can sideload Microsoft Teams apps without having to publish to your organization or the Teams store.</span></span> <span data-ttu-id="ff1ad-106">Isso faz sentido nos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="ff1ad-106">This makes sense in the following scenarios:</span></span>

* <span data-ttu-id="ff1ad-107">Você deseja testar e depurar um aplicativo localmente ou com outros desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-107">You want to test and debug an app locally yourself or with other developers.</span></span>
* <span data-ttu-id="ff1ad-108">Você criou um aplicativo apenas para si mesmo.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-108">You built an app just for yourself.</span></span> <span data-ttu-id="ff1ad-109">Por exemplo, para automatizar um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-109">For example, to automate a workflow.</span></span>
* <span data-ttu-id="ff1ad-110">Você criou um aplicativo para um pequeno conjunto de usuários, como seu grupo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-110">You built an app for a small set of users, such as, your work group.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ff1ad-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ff1ad-111">Prerequisites</span></span>

* <span data-ttu-id="ff1ad-112">Crie seu [pacote de aplicativos](~/concepts/build-and-test/apps-package.md) [e valide-o](https://dev.teams.microsoft.com/appvalidation.html) para erros.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-112">Create your [app package](~/concepts/build-and-test/apps-package.md) and [validate it](https://dev.teams.microsoft.com/appvalidation.html) for errors.</span></span>
* <span data-ttu-id="ff1ad-113">[Habilitar o carregamento personalizado de aplicativos](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) Teams.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-113">[Enable custom app uploading](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) in Teams.</span></span>
* <span data-ttu-id="ff1ad-114">Certifique-se de que seu aplicativo está em execução e acessível por meio de HTTPs.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-114">Make sure that your app is running and accessible via HTTPs.</span></span>

## <a name="upload-your-app"></a><span data-ttu-id="ff1ad-115">Carregar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff1ad-115">Upload your app</span></span>

<span data-ttu-id="ff1ad-116">Você pode fazer sideload do aplicativo em uma equipe, chat, reunião ou para uso pessoal, dependendo de como você configurou o escopo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-116">You can sideload your app to a team, chat, meeting, or for personal use depending on how you configured your app's scope.</span></span>

1. <span data-ttu-id="ff1ad-117">Faça logoff no cliente Teams com sua [conta Microsoft 365 de desenvolvimento.](~/build-your-first-app/build-and-run.md#prerequisites)</span><span class="sxs-lookup"><span data-stu-id="ff1ad-117">Log in to the Teams client with your [Microsoft 365 development account](~/build-your-first-app/build-and-run.md#prerequisites).</span></span>
1. <span data-ttu-id="ff1ad-118">Selecione **Aplicativos** e escolha **Upload um aplicativo personalizado.**</span><span class="sxs-lookup"><span data-stu-id="ff1ad-118">Select **Apps** and choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="ff1ad-119">Selecione o arquivo .zip pacote do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-119">Select your app package .zip file.</span></span> <span data-ttu-id="ff1ad-120">Uma caixa de diálogo de instalação é exibida.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-120">An install dialog displays.</span></span>
:::image type="content" source="~/assets/images/build-your-first-app/add-teams-app.png" alt-text="Captura de tela mostrando um exemplo de uma caixa de diálogo Teams instalação do aplicativo.":::
1. <span data-ttu-id="ff1ad-122">Adicione seu aplicativo ao Teams.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-122">Add your app to Teams.</span></span>

## <a name="troubleshoot-upload-issues"></a><span data-ttu-id="ff1ad-123">Solução de problemas de carregamento</span><span class="sxs-lookup"><span data-stu-id="ff1ad-123">Troubleshoot upload issues</span></span>

<span data-ttu-id="ff1ad-124">Se o aplicativo não fizer sideload, faça o seguinte até que o problema seja resolvido:</span><span class="sxs-lookup"><span data-stu-id="ff1ad-124">If your app fails to sideload, do the following until the issue resolves:</span></span>

1. <span data-ttu-id="ff1ad-125">Volte pelas instruções para criar [seu pacote de aplicativos.](../../concepts/build-and-test/apps-package.md)</span><span class="sxs-lookup"><span data-stu-id="ff1ad-125">Go back through the instructions for [creating your app package](../../concepts/build-and-test/apps-package.md).</span></span>
1. <span data-ttu-id="ff1ad-126">[Valide seu pacote de aplicativo novamente.](https://dev.teams.microsoft.com/appvalidation.html)</span><span class="sxs-lookup"><span data-stu-id="ff1ad-126">[Validate your app package](https://dev.teams.microsoft.com/appvalidation.html) again.</span></span>
1. <span data-ttu-id="ff1ad-127">Certifique-se de que o manifesto do aplicativo corresponde ao [esquema mais recente.](../../resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="ff1ad-127">Make sure your app manifest matches the latest [schema](../../resources/schema/manifest-schema.md).</span></span>

## <a name="access-your-app"></a><span data-ttu-id="ff1ad-128">Acessar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff1ad-128">Access your app</span></span>

<span data-ttu-id="ff1ad-129">Teams fornece várias maneiras de abrir aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-129">Teams provides several ways to open apps.</span></span> <span data-ttu-id="ff1ad-130">Para obter mais informações, [consulte access your apps in Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).</span><span class="sxs-lookup"><span data-stu-id="ff1ad-130">For more information, see [access your apps in Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).</span></span>

## <a name="update-your-app"></a><span data-ttu-id="ff1ad-131">Atualizar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff1ad-131">Update your app</span></span>

<span data-ttu-id="ff1ad-132">Você não precisa fazer sideload do aplicativo novamente se fizer alterações de código (elas são refletidas em Teams em tempo real).</span><span class="sxs-lookup"><span data-stu-id="ff1ad-132">You don't have to sideload your app again if you make code changes (these are reflected in Teams in real-time).</span></span> <span data-ttu-id="ff1ad-133">No entanto, você deve reinstalar se alterar qualquer configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-133">However, you must reinstall if you change any app configurations.</span></span>

## <a name="remove-your-app"></a><span data-ttu-id="ff1ad-134">Remover seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff1ad-134">Remove your app</span></span>

<span data-ttu-id="ff1ad-135">Para remover seu aplicativo, clique com o botão direito do mouse no ícone do aplicativo no Teams e selecione **Desinstalar**.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-135">To remove your app, right click the app icon in Teams and select **Uninstall**.</span></span>

> [!NOTE]
> <span data-ttu-id="ff1ad-136">Não é possível remover totalmente a atividade de bot pessoal.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-136">You can't remove personal bot activity entirely.</span></span> <span data-ttu-id="ff1ad-137">Se você remover o aplicativo e adicioná-lo novamente, a nova comunicação com o bot acrescenta à conversa anterior com ele.</span><span class="sxs-lookup"><span data-stu-id="ff1ad-137">If you remove the app and add it again, new communication with the bot appends to the previous conversation with it.</span></span>

## <a name="next-step"></a><span data-ttu-id="ff1ad-138">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ff1ad-138">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ff1ad-139">Usar seu Teams aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff1ad-139">Use your Teams app</span></span>](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us)
