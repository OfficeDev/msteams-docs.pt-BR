---
title: Criar uma página de conteúdo
author: laujan
description: como criar uma página de conteúdo
keywords: teams tabs group channel configurble static
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: c33f58197e8b49ac7122178e154724cc5186bcb1
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034695"
---
# <a name="create-a-content-page-for-your-tab"></a><span data-ttu-id="a71ce-104">Criar uma página de conteúdo para sua guia</span><span class="sxs-lookup"><span data-stu-id="a71ce-104">Create a content page for your tab</span></span>

<span data-ttu-id="a71ce-105">Uma página de conteúdo é uma página da Web renderizada dentro do cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="a71ce-105">A content page is a webpage that is rendered within the Teams client.</span></span> <span data-ttu-id="a71ce-106">Normalmente, eles fazem parte de:</span><span class="sxs-lookup"><span data-stu-id="a71ce-106">Typically these are part of:</span></span>

* <span data-ttu-id="a71ce-107">Uma guia personalizada com escopo pessoal - Nesta instância, a página de conteúdo é a primeira página que o usuário encontra.</span><span class="sxs-lookup"><span data-stu-id="a71ce-107">A personal-scoped custom tab - In this instance the content page is the first page the user encounters.</span></span>
* <span data-ttu-id="a71ce-108">Uma guia personalizada de canal/grupo - Após o usuário fixar e configurar a guia no contexto apropriado, a página de conteúdo será exibida.</span><span class="sxs-lookup"><span data-stu-id="a71ce-108">A channel/group custom tab - After the user pins and configures the tab in the appropriate context, the content page is displayed.</span></span>
* <span data-ttu-id="a71ce-109">Um [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md) - Você pode criar uma página de conteúdo e in-locar como um webview dentro de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="a71ce-109">A [task module](~/task-modules-and-cards/what-are-task-modules.md) - You can create a content page and embed it as a webview inside a task module.</span></span> <span data-ttu-id="a71ce-110">A página será renderizada dentro do pop-up modal.</span><span class="sxs-lookup"><span data-stu-id="a71ce-110">The page will be rendered inside the modal popup.</span></span>

<span data-ttu-id="a71ce-111">Este artigo é específico para usar páginas de conteúdo como guias; no entanto, a maioria das diretrizes aqui se aplicaria independentemente de como a página de conteúdo é apresentada ao usuário final.</span><span class="sxs-lookup"><span data-stu-id="a71ce-111">This article is specific to using content pages as tabs; however the majority of the guidance here would apply regardless of how the content page is presented to the end-user.</span></span>

## <a name="tab-content-and-style-guidelines"></a><span data-ttu-id="a71ce-112">Diretrizes de estilo e conteúdo de tabulação</span><span class="sxs-lookup"><span data-stu-id="a71ce-112">Tab content and style guidelines</span></span>

<span data-ttu-id="a71ce-113">O objetivo geral da guia deve ser fornecer acesso a conteúdo significativo e envolvente que tenha um valor prático e uma finalidade evidente.</span><span class="sxs-lookup"><span data-stu-id="a71ce-113">Your tab's overall objective should be to provide access to meaningful and engaging content that has a practical value and an evident purpose.</span></span> <span data-ttu-id="a71ce-114">Isso não significa que você deve deixar um estilo agradável, mas você deve se concentrar em minimizar a desordem, tornando seu design de tabulação limpo, intuitivo de navegação e imersivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a71ce-114">That does not mean that you should forego a pleasing style, but you should focus on minimizing clutter by making your tab design clean, navigation intuitive, and content immersive.</span></span> <span data-ttu-id="a71ce-115">Consulte [Conteúdo e conversas, tudo de uma vez usando guias](~/tabs/design/tabs.md) e [orientações do processo](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) de aprovação de aplicativos do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a71ce-115">See [Content and conversations, all at once using tabs](~/tabs/design/tabs.md) and [Microsoft Teams app approval process guidance](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span></span>

## <a name="integrate-your-code-with-teams"></a><span data-ttu-id="a71ce-116">Integrar seu código com o Teams</span><span class="sxs-lookup"><span data-stu-id="a71ce-116">Integrate your code with Teams</span></span>

<span data-ttu-id="a71ce-117">Para que sua página seja exibida no Teams, você deve incluir o [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript do Microsoft Teams e incluir uma chamada para depois que sua `microsoftTeams.initialize()` página for carregada.</span><span class="sxs-lookup"><span data-stu-id="a71ce-117">For your page to display in Teams, you must include the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="a71ce-118">É assim que sua página e o cliente do Teams se comunicam:</span><span class="sxs-lookup"><span data-stu-id="a71ce-118">That is how your page and the Teams client communicate:</span></span>

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

## <a name="accessing-additional-content"></a><span data-ttu-id="a71ce-119">Acessando conteúdo adicional</span><span class="sxs-lookup"><span data-stu-id="a71ce-119">Accessing additional content</span></span>

### <a name="using-the-sdk-to-interact-with-teams"></a><span data-ttu-id="a71ce-120">Usando o SDK para interagir com o Teams</span><span class="sxs-lookup"><span data-stu-id="a71ce-120">Using the SDK to interact with Teams</span></span>

<span data-ttu-id="a71ce-121">O [SDK JavaScript do cliente](~/tabs/how-to/using-teams-client-sdk.md) do Teams fornece muitas funções adicionais que podem ser úteis durante o desenvolvimento de sua página de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a71ce-121">The [Teams client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) provides many additional functions you may find useful while developing your content page.</span></span>

### <a name="deep-links"></a><span data-ttu-id="a71ce-122">Links profundos</span><span class="sxs-lookup"><span data-stu-id="a71ce-122">Deep links</span></span>

<span data-ttu-id="a71ce-123">Você pode criar links profundos para entidades no Teams.</span><span class="sxs-lookup"><span data-stu-id="a71ce-123">You can create deep links to entities in Teams.</span></span> <span data-ttu-id="a71ce-124">Normalmente, eles são usados para criar links que navegam para conteúdo e informações em sua guia. Consulte [Criar links profundos para conteúdo e recursos no Microsoft Teams.](~/concepts/build-and-test/deep-links.md)</span><span class="sxs-lookup"><span data-stu-id="a71ce-124">Typically, these are used to create links that navigate to content and information within your tab. See [Create deep links to content and features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span></span>

### <a name="task-modules"></a><span data-ttu-id="a71ce-125">Módulos de Tarefa</span><span class="sxs-lookup"><span data-stu-id="a71ce-125">Task Modules</span></span>

<span data-ttu-id="a71ce-126">Um módulo de tarefa é uma experiência pop-up modal que você pode disparar da guia. Normalmente, em uma página de conteúdo, você não deseja navegar pelo usuário por várias páginas.</span><span class="sxs-lookup"><span data-stu-id="a71ce-126">A task module is a modal popup-like experience that you can trigger from your tab. Typically in a content page you do not want to navigate your user through multiple pages.</span></span> <span data-ttu-id="a71ce-127">Em vez disso, você usará módulos de tarefa para apresentar formulários para coletar informações adicionais, exibindo os detalhes de um item em uma lista ou qualquer outra vez que precisar apresentar ao usuário informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="a71ce-127">Instead, you will use task modules to present forms for gathering additional information, displaying the details of an item in a list, or any other time you need to present the user with additional information.</span></span> <span data-ttu-id="a71ce-128">Os próprios módulos de tarefa podem ser páginas de conteúdo adicionais ou criados completamente usando Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="a71ce-128">The task modules themselves can be additional content pages, or created completely using Adaptive Cards.</span></span> <span data-ttu-id="a71ce-129">Consulte [Usando módulos de tarefa em guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md) para obter informações completas.</span><span class="sxs-lookup"><span data-stu-id="a71ce-129">See [Using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md) for complete information.</span></span>

### <a name="valid-domains"></a><span data-ttu-id="a71ce-130">Domínios válidos</span><span class="sxs-lookup"><span data-stu-id="a71ce-130">Valid Domains</span></span>

<span data-ttu-id="a71ce-131">Verifique se todos os domínios de URL usados em suas guias estão incluídos na `validDomains` matriz em seu [manifesto](~/concepts/build-and-test/apps-package.md).</span><span class="sxs-lookup"><span data-stu-id="a71ce-131">Ensure that the all URL domains used in your tabs are included in the `validDomains` array in your [manifest](~/concepts/build-and-test/apps-package.md).</span></span> <span data-ttu-id="a71ce-132">Para obter mais informações, [consulte validDomains](~/resources/schema/manifest-schema.md#validdomains) na referência de esquema de manifesto.</span><span class="sxs-lookup"><span data-stu-id="a71ce-132">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema reference.</span></span> <span data-ttu-id="a71ce-133">No entanto, não se esqueça de que a funcionalidade principal da sua guia existe no Teams e não fora do Teams.</span><span class="sxs-lookup"><span data-stu-id="a71ce-133">However, be mindful that the core functionality of your tab exists within Teams and not outside of Teams.</span></span>

## <a name="reorder-static-personal-tabs"></a><span data-ttu-id="a71ce-134">Reordenar guias pessoais estáticas</span><span class="sxs-lookup"><span data-stu-id="a71ce-134">Reorder static personal tabs</span></span>

<span data-ttu-id="a71ce-135">A partir da versão 1.7 do manifesto, os desenvolvedores podem reorganizar todas as guias em seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="a71ce-135">Starting with manifest version 1.7, developers can rearrange all tabs in their personal app.</span></span> <span data-ttu-id="a71ce-136">Em particular, um desenvolvedor pode mover a guia de *chat* bot, que sempre é padrão para a primeira posição, em qualquer lugar no header da guia do aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="a71ce-136">In particular, a developer can move the *bot chat* tab, which always defaults to the first position, anywhere in the personal app tab header.</span></span> <span data-ttu-id="a71ce-137">Declaramos duas guias reservadas entityId palavras-chave, *conversas* e *sobre*.</span><span class="sxs-lookup"><span data-stu-id="a71ce-137">We’ve declared two reserved tab entityId keywords, *conversations* and *about*.</span></span>

<span data-ttu-id="a71ce-138">Se você criar um bot com *um escopo* pessoal, ele será a primeira posição de tabulação em um aplicativo pessoal por padrão.</span><span class="sxs-lookup"><span data-stu-id="a71ce-138">If you create a bot with a *personal* scope, it will show up in the first tab position in a personal app by default.</span></span> <span data-ttu-id="a71ce-139">Se quiser movê-lo para outra posição, adicione um objeto de guia estático ao manifesto com a palavra-chave reservada, *conversas*.</span><span class="sxs-lookup"><span data-stu-id="a71ce-139">If you wish to move it to another position, you must add a static tab object to your manifest with the reserved keyword, *conversations*.</span></span> <span data-ttu-id="a71ce-140">A *guia* conversa é exibida na Web ou na área de trabalho com base em onde você adiciona a guia *de* conversa na `staticTabs` matriz.</span><span class="sxs-lookup"><span data-stu-id="a71ce-140">The *conversation* tab appears on web or desktop based on where you add the *conversation* tab in the `staticTabs` array.</span></span> 

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```

## <a name="show-a-native-loading-indicator"></a><span data-ttu-id="a71ce-141">Mostrar um indicador de carregamento nativo</span><span class="sxs-lookup"><span data-stu-id="a71ce-141">Show a native loading indicator</span></span>

<span data-ttu-id="a71ce-142">A partir do esquema de manifesto [v1.7](../../../resources/schema/manifest-schema.md), você pode fornecer um indicador de carregamento nativo onde quer que o conteúdo da Web seja carregado no Teams, por [exemplo,](#integrate-your-code-with-teams)página de conteúdo de tabulação, [](configuration-page.md)página de configuração, [](removal-page.md) página de remoção e [módulos](../../../task-modules-and-cards/task-modules/task-modules-tabs.md)de tarefa nas guias . [](../../../resources/schema/manifest-schema.md#showloadingindicator)</span><span class="sxs-lookup"><span data-stu-id="a71ce-142">Starting with [manifest schema v1.7](../../../resources/schema/manifest-schema.md), you can provide a [native loading indicator](../../../resources/schema/manifest-schema.md#showloadingindicator) wherever your web content is loaded in Teams, e.g., [tab content page](#integrate-your-code-with-teams), [configuration page](configuration-page.md), [removal page](removal-page.md) and [task modules in tabs](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span></span>

> [!NOTE]
> 1. <span data-ttu-id="a71ce-143">O comportamento em clientes móveis não é configurável por meio dessa propriedade de manifesto.</span><span class="sxs-lookup"><span data-stu-id="a71ce-143">The behavior on mobile clients is not configurable through this manifest property.</span></span> <span data-ttu-id="a71ce-144">Os clientes móveis mostram um indicador de carregamento nativo por padrão em páginas de conteúdo e módulos de tarefa baseados em iframe.</span><span class="sxs-lookup"><span data-stu-id="a71ce-144">Mobile clients show a native loading indicator by default across content pages and iframe-based task modules.</span></span> <span data-ttu-id="a71ce-145">Esse indicador no celular é mostrado quando uma solicitação é feita para buscar conteúdo e é descartada assim que a solicitação é concluída.</span><span class="sxs-lookup"><span data-stu-id="a71ce-145">This indicator on mobile is shown when a request is made to fetch content and gets dismissed as soon as the request gets completed.</span></span>
> 2. <span data-ttu-id="a71ce-146">Se você indicar no manifesto do aplicativo, todas as páginas de configuração, conteúdo e remoção de guias e todos os módulos de tarefa baseados em iframe devem seguir o protocolo obrigatório  `"showLoadingIndicator : true`  abaixo:</span><span class="sxs-lookup"><span data-stu-id="a71ce-146">If you indicate  `"showLoadingIndicator : true`  in your app manifest, then all tab configuration, content, and removal pages and all iframe-based task modules must follow the mandatory protocol, below:</span></span>


1. <span data-ttu-id="a71ce-147">Para mostrar o indicador de carregamento, adicione `"showLoadingIndicator": true` ao manifesto.</span><span class="sxs-lookup"><span data-stu-id="a71ce-147">To show the loading indicator, add `"showLoadingIndicator": true` to your manifest.</span></span> 
2. <span data-ttu-id="a71ce-148">Lembre-se de chamar `microsoftTeams.initialize();` .</span><span class="sxs-lookup"><span data-stu-id="a71ce-148">Remember to call `microsoftTeams.initialize();`.</span></span>
3. <span data-ttu-id="a71ce-149">**Opcional**.</span><span class="sxs-lookup"><span data-stu-id="a71ce-149">**Optional**.</span></span> <span data-ttu-id="a71ce-150">Se você estiver pronto para imprimir na tela e desejar carregar o restante do conteúdo do aplicativo, poderá ocultar manualmente o indicador de carregamento chamando `microsoftTeams.appInitialization.notifyAppLoaded();`</span><span class="sxs-lookup"><span data-stu-id="a71ce-150">If you're ready to print to the screen and wish to lazy load the rest of your application's content, you can manually hide the loading indicator by calling `microsoftTeams.appInitialization.notifyAppLoaded();`</span></span>
4. <span data-ttu-id="a71ce-151">**Obrigatório**.</span><span class="sxs-lookup"><span data-stu-id="a71ce-151">**Mandatory**.</span></span> <span data-ttu-id="a71ce-152">Por fim, `microsoftTeams.appInitialization.notifySuccess()` chame para notificar o Teams de que seu aplicativo carregou com êxito.</span><span class="sxs-lookup"><span data-stu-id="a71ce-152">Finally, call `microsoftTeams.appInitialization.notifySuccess()` to notify Teams that your app has successfully loaded.</span></span> <span data-ttu-id="a71ce-153">Em seguida, o Teams ocultará o indicador de carregamento, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="a71ce-153">Teams will then hide the loading indicator if applicable.</span></span> <span data-ttu-id="a71ce-154">Se  `notifySuccess`  não for chamado dentro de 30 segundos, será assumido que o tempo decorria do aplicativo e uma tela de erro com uma opção de nova tentativa aparecerá.</span><span class="sxs-lookup"><span data-stu-id="a71ce-154">If  `notifySuccess`  is not called within 30 seconds, it will be assumed that your app timed out and an error screen with a retry option will appear.</span></span>
5. <span data-ttu-id="a71ce-155">Se o aplicativo não for carregado, você poderá chamar para `microsoftTeams.appInitialization.notifyFailure(reason);` que o Teams saiba que houve um erro.</span><span class="sxs-lookup"><span data-stu-id="a71ce-155">If your application fails to load, you can call `microsoftTeams.appInitialization.notifyFailure(reason);` to let Teams know there was an error.</span></span> <span data-ttu-id="a71ce-156">Em seguida, uma tela de erro será mostrada ao usuário:</span><span class="sxs-lookup"><span data-stu-id="a71ce-156">An error screen will then be shown to the user:</span></span>

```typescript
``
/* List of failure reasons */
export const enum FailedReason {
    AuthFailed = "AuthFailed",
    Timeout = "Timeout",
    Other = "Other"
}
```
>
