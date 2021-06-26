---
title: Criar uma página de conteúdo
author: surbhigupta
description: como criar uma página de conteúdo
keywords: teams tabs group channel configurble static
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: d1ec2c0381ba371393a03cda69ffc44a5f49924e
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140198"
---
# <a name="create-a-content-page-for-your-tab"></a><span data-ttu-id="ac165-104">Criar uma página de conteúdo para sua guia</span><span class="sxs-lookup"><span data-stu-id="ac165-104">Create a content page for your tab</span></span>

<span data-ttu-id="ac165-105">Uma página de conteúdo é uma página da Web renderizada no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="ac165-105">A content page is a webpage that is rendered within the Teams client.</span></span> <span data-ttu-id="ac165-106">Elas fazem parte de:</span><span class="sxs-lookup"><span data-stu-id="ac165-106">These are part of:</span></span>

* <span data-ttu-id="ac165-107">Uma guia personalizada com escopo pessoal: nesse caso, a página de conteúdo é a primeira página que o usuário encontra.</span><span class="sxs-lookup"><span data-stu-id="ac165-107">A personal-scoped custom tab: In this case, the content page is the first page the user encounters.</span></span>
* <span data-ttu-id="ac165-108">Uma guia personalizada de canal ou grupo: a página de conteúdo é exibida após o usuário fixar e configurar a guia no contexto apropriado.</span><span class="sxs-lookup"><span data-stu-id="ac165-108">A channel or group custom tab: The content page is displayed after the user pins and configures the tab in the appropriate context.</span></span>
* <span data-ttu-id="ac165-109">Um [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md): você pode criar uma página de conteúdo e in-locar como um webview dentro de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="ac165-109">A [task module](~/task-modules-and-cards/what-are-task-modules.md): You can create a content page and embed it as a webview inside a task module.</span></span> <span data-ttu-id="ac165-110">A página é renderizada dentro do pop-up modal.</span><span class="sxs-lookup"><span data-stu-id="ac165-110">The page is rendered inside the modal pop-up.</span></span>

<span data-ttu-id="ac165-111">Este artigo é específico para usar páginas de conteúdo como guias; no entanto, a maioria das diretrizes aqui se aplica independentemente de como a página de conteúdo é apresentada ao usuário.</span><span class="sxs-lookup"><span data-stu-id="ac165-111">This article is specific to using content pages as tabs; however the majority of the guidance here applies regardless of how the content page is presented to the user.</span></span>

## <a name="tab-content-and-design-guidelines"></a><span data-ttu-id="ac165-112">Diretrizes de design e conteúdo de tabulação</span><span class="sxs-lookup"><span data-stu-id="ac165-112">Tab content and design guidelines</span></span>

<span data-ttu-id="ac165-113">O objetivo geral da guia é fornecer acesso a conteúdo significativo e envolvente que tenha valor prático e uma finalidade evidente.</span><span class="sxs-lookup"><span data-stu-id="ac165-113">Your tab's overall objective is to provide access to meaningful and engaging content that has practical value and an evident purpose.</span></span> <span data-ttu-id="ac165-114">Você deve se concentrar em tornar seu design de tabulação limpo, intuitivo e imersivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ac165-114">You must focus on making your tab design clean, navigation intuitive, and content immersive.</span></span>

<span data-ttu-id="ac165-115">Para obter mais informações, consulte [diretrizes de design de guias](~/tabs/design/tabs.md) e Microsoft Teams de [validação do armazenamento.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)</span><span class="sxs-lookup"><span data-stu-id="ac165-115">For more information, see [tab design guidelines](~/tabs/design/tabs.md) and [Microsoft Teams store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).</span></span>

## <a name="integrate-your-code-with-teams"></a><span data-ttu-id="ac165-116">Integrar seu código com Teams</span><span class="sxs-lookup"><span data-stu-id="ac165-116">Integrate your code with Teams</span></span>

<span data-ttu-id="ac165-117">Para que sua página seja exibida Teams, você deve incluir o [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript Microsoft Teams e incluir uma chamada depois que a página `microsoftTeams.initialize()` for carregada.</span><span class="sxs-lookup"><span data-stu-id="ac165-117">For your page to display in Teams, you must include the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> 

<span data-ttu-id="ac165-118">O código a seguir fornece um exemplo de como sua página e o Teams cliente se comunicam:</span><span class="sxs-lookup"><span data-stu-id="ac165-118">The following code provides an example of how your page and the Teams client communicate:</span></span>

```html
<!DOCTYPE html>
<html>
<head>
...
    <script src= 'https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js'></script>
...
</head>

<body>
...
    <script>
    microsoftTeams.initialize();
    </script>
...
</body>
```

## <a name="access-additional-content"></a><span data-ttu-id="ac165-119">Acessar conteúdo adicional</span><span class="sxs-lookup"><span data-stu-id="ac165-119">Access additional content</span></span>

<span data-ttu-id="ac165-120">Você pode acessar conteúdo adicional usando o SDK para interagir com o Teams, criar links profundos, usar módulos de tarefa e verificar se os domínios de URL estão incluídos na `validDomains` matriz.</span><span class="sxs-lookup"><span data-stu-id="ac165-120">You can access additional content by using the SDK to interact with Teams, creating deep links, using task modules, and verifying if URL domains are included in the `validDomains` array.</span></span>

### <a name="use-the-sdk-to-interact-with-teams"></a><span data-ttu-id="ac165-121">Use o SDK para interagir com Teams</span><span class="sxs-lookup"><span data-stu-id="ac165-121">Use the SDK to interact with Teams</span></span>

<span data-ttu-id="ac165-122">O [Teams cliente JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) fornece muitas funções adicionais que você pode encontrar úteis durante o desenvolvimento de sua página de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ac165-122">The [Teams client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) provides many additional functions that you can find useful while developing your content page.</span></span>

### <a name="deep-links"></a><span data-ttu-id="ac165-123">Links profundos</span><span class="sxs-lookup"><span data-stu-id="ac165-123">Deep links</span></span>

<span data-ttu-id="ac165-124">Você pode criar links profundos para entidades Teams.</span><span class="sxs-lookup"><span data-stu-id="ac165-124">You can create deep links to entities in Teams.</span></span> <span data-ttu-id="ac165-125">Eles são usados para criar links que navegam até conteúdo e informações em sua guia. Para obter mais informações, [consulte create deep links to content and features in Teams](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="ac165-125">These are used to create links that navigate to content and information within your tab. For more information, see [create deep links to content and features in Teams](~/concepts/build-and-test/deep-links.md).</span></span>

### <a name="task-modules"></a><span data-ttu-id="ac165-126">Módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="ac165-126">Task modules</span></span>

<span data-ttu-id="ac165-127">Um módulo de tarefa é uma experiência pop-up modal que você pode disparar da guia. Em uma página de conteúdo, você pode usar módulos de tarefa para apresentar formulários para coletar informações adicionais, exibir os detalhes de um item em uma lista ou apresentar o usuário com informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="ac165-127">A task module is a modal pop-up experience that you can trigger from your tab. In a content page, you can use task modules to present forms for gathering additional information, displaying the details of an item in a list, or presenting the user with additional information.</span></span> <span data-ttu-id="ac165-128">Os próprios módulos de tarefa podem ser páginas de conteúdo adicionais ou criados completamente usando Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="ac165-128">The task modules themselves can be additional content pages, or created completely using Adaptive Cards.</span></span> <span data-ttu-id="ac165-129">Para obter mais informações, [consulte using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md).</span><span class="sxs-lookup"><span data-stu-id="ac165-129">For more information, see [using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md).</span></span>

### <a name="valid-domains"></a><span data-ttu-id="ac165-130">Domínios válidos</span><span class="sxs-lookup"><span data-stu-id="ac165-130">Valid domains</span></span>

<span data-ttu-id="ac165-131">Verifique se todos os domínios de URL usados em suas guias estão incluídos na `validDomains` matriz em seu [manifesto](~/concepts/build-and-test/apps-package.md).</span><span class="sxs-lookup"><span data-stu-id="ac165-131">Ensure that all URL domains used in your tabs are included in the `validDomains` array in your [manifest](~/concepts/build-and-test/apps-package.md).</span></span> <span data-ttu-id="ac165-132">Para obter mais informações, [consulte validDomains](~/resources/schema/manifest-schema.md#validdomains) na referência de esquema de manifesto.</span><span class="sxs-lookup"><span data-stu-id="ac165-132">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema reference.</span></span>

> [!NOTE]
> <span data-ttu-id="ac165-133">A funcionalidade principal da guia existe dentro Teams e não fora do Teams.</span><span class="sxs-lookup"><span data-stu-id="ac165-133">The core functionality of your tab exists within Teams and not outside of Teams.</span></span>

## <a name="show-a-native-loading-indicator"></a><span data-ttu-id="ac165-134">Mostrar um indicador de carregamento nativo</span><span class="sxs-lookup"><span data-stu-id="ac165-134">Show a native loading indicator</span></span>

<span data-ttu-id="ac165-135">A partir [do esquema de manifesto v1.7](../../../resources/schema/manifest-schema.md), você pode fornecer um indicador de carregamento [nativo.](../../../resources/schema/manifest-schema.md#showloadingindicator)</span><span class="sxs-lookup"><span data-stu-id="ac165-135">Starting with [manifest schema v1.7](../../../resources/schema/manifest-schema.md), you can provide a [native loading indicator](../../../resources/schema/manifest-schema.md#showloadingindicator).</span></span> <span data-ttu-id="ac165-136">Por exemplo, página [de conteúdo de tabulação,](#integrate-your-code-with-teams) [página](removal-page.md) [de configuração,](configuration-page.md)página de remoção e [módulos de tarefa nas guias](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span><span class="sxs-lookup"><span data-stu-id="ac165-136">For example, [tab content page](#integrate-your-code-with-teams), [configuration page](configuration-page.md), [removal page](removal-page.md), and [task modules in tabs](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span></span>

> [!NOTE]
> * <span data-ttu-id="ac165-137">O comportamento em clientes móveis não é configurável por meio da propriedade indicador de carregamento nativo.</span><span class="sxs-lookup"><span data-stu-id="ac165-137">The behavior on mobile clients is not configurable through the native loading indicator property.</span></span> <span data-ttu-id="ac165-138">Os clientes móveis mostram esse indicador por padrão em páginas de conteúdo e módulos de tarefa baseados em iframe.</span><span class="sxs-lookup"><span data-stu-id="ac165-138">Mobile clients show this indicator by default across content pages and iframe-based task modules.</span></span> <span data-ttu-id="ac165-139">Esse indicador no celular é mostrado quando uma solicitação é feita para buscar conteúdo e é descartada assim que a solicitação é concluída.</span><span class="sxs-lookup"><span data-stu-id="ac165-139">This indicator on mobile is shown when a request is made to fetch content and gets dismissed as soon as the request gets completed.</span></span>

<span data-ttu-id="ac165-140">Se você indicar no manifesto do aplicativo, todas as páginas de configuração, conteúdo e remoção de guias e todos os módulos de tarefa baseados em iframe devem `showLoadingIndicator : true`  seguir estas etapas:</span><span class="sxs-lookup"><span data-stu-id="ac165-140">If you indicate `showLoadingIndicator : true`  in your app manifest, then all tab configuration, content, and removal pages and all iframe-based task modules must follow these steps:</span></span>

<span data-ttu-id="ac165-141">**Para mostrar o indicador de carregamento**</span><span class="sxs-lookup"><span data-stu-id="ac165-141">**To show the loading indicator**</span></span>

1. <span data-ttu-id="ac165-142">Adicione `"showLoadingIndicator": true` ao manifesto.</span><span class="sxs-lookup"><span data-stu-id="ac165-142">Add `"showLoadingIndicator": true` to your manifest.</span></span>
1. <span data-ttu-id="ac165-143">Chamar `microsoftTeams.initialize();`.</span><span class="sxs-lookup"><span data-stu-id="ac165-143">Call `microsoftTeams.initialize();`.</span></span>
1. <span data-ttu-id="ac165-144">Como etapa **obrigatória,** chame para `microsoftTeams.appInitialization.notifySuccess()` notificar Teams que seu aplicativo carregou com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac165-144">As a **mandatory** step, call `microsoftTeams.appInitialization.notifySuccess()` to notify Teams that your app has successfully loaded.</span></span> <span data-ttu-id="ac165-145">Teams, em seguida, oculta o indicador de carregamento, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="ac165-145">Teams then hides the loading indicator, if applicable.</span></span> <span data-ttu-id="ac165-146">Se `notifySuccess`  não for chamado dentro de 30 segundos, presume-se que o aplicativo esteja com o tempo decoro e uma tela de erro com uma opção de nova tentativa será exibida.</span><span class="sxs-lookup"><span data-stu-id="ac165-146">If `notifySuccess`  is not called within 30 seconds, it is assumed that your app timed out and an error screen with a retry option appears.</span></span>
1. <span data-ttu-id="ac165-147">**Opcionalmente**, se você estiver pronto para imprimir na tela e desejar carregar o restante do conteúdo do aplicativo, poderá ocultar manualmente o indicador de carregamento chamando `microsoftTeams.appInitialization.notifyAppLoaded();` .</span><span class="sxs-lookup"><span data-stu-id="ac165-147">**Optionally**, if you are ready to print to the screen and wish to lazy load the rest of your application's content, you can manually hide the loading indicator by calling `microsoftTeams.appInitialization.notifyAppLoaded();`.</span></span>
1. <span data-ttu-id="ac165-148">Se o aplicativo não for carregado, você poderá chamar para `microsoftTeams.appInitialization.notifyFailure(reason);` Teams que houve um erro.</span><span class="sxs-lookup"><span data-stu-id="ac165-148">If your application fails to load, you can call `microsoftTeams.appInitialization.notifyFailure(reason);` to let Teams know there was an error.</span></span> <span data-ttu-id="ac165-149">Uma tela de erro é mostrada ao usuário.</span><span class="sxs-lookup"><span data-stu-id="ac165-149">An error screen is shown to the user.</span></span> <span data-ttu-id="ac165-150">O código a seguir fornece um exemplo de motivos de falha do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ac165-150">The following code provides an example of application failure reasons:</span></span>

    ```typescript
    /* List of failure reasons */
    export const enum FailedReason {
        AuthFailed = "AuthFailed",
        Timeout = "Timeout",
        Other = "Other"
    }
    ```

## <a name="see-also"></a><span data-ttu-id="ac165-151">Também consulte</span><span class="sxs-lookup"><span data-stu-id="ac165-151">See also</span></span>

* [<span data-ttu-id="ac165-152">Teams guias</span><span class="sxs-lookup"><span data-stu-id="ac165-152">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="ac165-153">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ac165-153">Prerequisites</span></span>](~/tabs/how-to/tab-requirements.md)
* [<span data-ttu-id="ac165-154">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="ac165-154">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="ac165-155">Criar um canal ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="ac165-155">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="ac165-156">Criar uma página de conteúdo</span><span class="sxs-lookup"><span data-stu-id="ac165-156">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
* [<span data-ttu-id="ac165-157">Criar uma página de remoção para sua guia</span><span class="sxs-lookup"><span data-stu-id="ac165-157">Create a removal page for your tab</span></span>](~/tabs/how-to/create-tab-pages/removal-page.md)
* [<span data-ttu-id="ac165-158">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="ac165-158">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="ac165-159">Obtenha contexto para sua guia</span><span class="sxs-lookup"><span data-stu-id="ac165-159">Get context for your tab</span></span>](~/tabs/how-to/access-teams-context.md)
* [<span data-ttu-id="ac165-160">Criar guias com Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="ac165-160">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)
* [<span data-ttu-id="ac165-161">Link de guias desdobradas e Exibição de Estágio</span><span class="sxs-lookup"><span data-stu-id="ac165-161">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)
* [<span data-ttu-id="ac165-162">Criar abas para conversação</span><span class="sxs-lookup"><span data-stu-id="ac165-162">Create conversational tabs</span></span>](~/tabs/how-to/conversational-tabs.md)
* [<span data-ttu-id="ac165-163">Alterações na margem da guia</span><span class="sxs-lookup"><span data-stu-id="ac165-163">Tab margin changes</span></span>](~/resources/removing-tab-margins.md)

## <a name="next-step"></a><span data-ttu-id="ac165-164">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ac165-164">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ac165-165">Criar uma página de configuração</span><span class="sxs-lookup"><span data-stu-id="ac165-165">Create a configuration page</span></span>](~/tabs/how-to/create-tab-pages/configuration-page.md)
