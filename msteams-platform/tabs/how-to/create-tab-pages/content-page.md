---
title: Criar uma página de conteúdo
author: laujan
description: como criar uma página de conteúdo
keywords: guias do teams com o canal de grupo configurado como estático
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 91a7d643d3a631610989e31eae14265cd725dbd0
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "47818903"
---
# <a name="create-a-content-page-for-your-tab"></a><span data-ttu-id="bb495-104">Criar uma página de conteúdo para sua guia</span><span class="sxs-lookup"><span data-stu-id="bb495-104">Create a content page for your tab</span></span>

<span data-ttu-id="bb495-105">Uma página de conteúdo é uma página da Web que é renderizada no cliente Teams.</span><span class="sxs-lookup"><span data-stu-id="bb495-105">A content page is a webpage that is rendered within the Teams client.</span></span> <span data-ttu-id="bb495-106">Normalmente, são parte de:</span><span class="sxs-lookup"><span data-stu-id="bb495-106">Typically these are part of:</span></span>

* <span data-ttu-id="bb495-107">Uma guia personalizada de escopo pessoal-nesta instância, a página de conteúdo é a primeira página que o usuário encontra.</span><span class="sxs-lookup"><span data-stu-id="bb495-107">A personal-scoped custom tab - In this instance the content page is the first page the user encounters.</span></span>
* <span data-ttu-id="bb495-108">Uma guia personalizada de canal/grupo, depois que o usuário fixa e configura a guia no contexto apropriado, a página de conteúdo é exibida.</span><span class="sxs-lookup"><span data-stu-id="bb495-108">A channel/group custom tab - After the user pins and configures the tab in the appropriate context, the content page is displayed.</span></span>
* <span data-ttu-id="bb495-109">Um [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md) -você pode criar uma página de conteúdo e incorporá-la como uma WebView dentro de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="bb495-109">A [task module](~/task-modules-and-cards/what-are-task-modules.md) - You can create a content page and embed it as a webview inside a task module.</span></span> <span data-ttu-id="bb495-110">A página será renderizada dentro do popup modal.</span><span class="sxs-lookup"><span data-stu-id="bb495-110">The page will be rendered inside the modal popup.</span></span>

<span data-ttu-id="bb495-111">Este artigo é específico para usar páginas de conteúdo como guias; no entanto, a maioria das orientações aqui aplica-se independentemente de como a página de conteúdo é apresentada ao usuário final.</span><span class="sxs-lookup"><span data-stu-id="bb495-111">This article is specific to using content pages as tabs; however the majority of the guidance here would apply regardless of how the content page is presented to the end-user.</span></span>

## <a name="tab-content-and-style-guidelines"></a><span data-ttu-id="bb495-112">Diretrizes de conteúdo e estilo da guia</span><span class="sxs-lookup"><span data-stu-id="bb495-112">Tab content and style guidelines</span></span>

<span data-ttu-id="bb495-113">O objetivo geral da guia é fornecer acesso a conteúdo significativo e envolvente que tenha um valor prático e uma finalidade evidente.</span><span class="sxs-lookup"><span data-stu-id="bb495-113">Your tab's overall objective should be to provide access to meaningful and engaging content that has a practical value and an evident purpose.</span></span> <span data-ttu-id="bb495-114">Isso não significa que você tenha um estilo agradável, mas você deve se concentrar em minimizar a desordem, tornando seu design de guia limpo, intuitivo e de aparência de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bb495-114">That does not mean that you should forego a pleasing style, but you should focus on minimizing clutter by making your tab design clean, navigation intuitive, and content immersive.</span></span> <span data-ttu-id="bb495-115">Veja [conteúdo e conversas, tudo de uma vez usando guias](~/tabs/design/tabs.md) e a [orientação do processo de aprovação do Microsoft Teams app](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span><span class="sxs-lookup"><span data-stu-id="bb495-115">See [Content and conversations, all at once using tabs](~/tabs/design/tabs.md) and [Microsoft Teams app approval process guidance](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span></span>

## <a name="integrate-your-code-with-teams"></a><span data-ttu-id="bb495-116">Integrar seu código com o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bb495-116">Integrate your code with Teams</span></span>

<span data-ttu-id="bb495-117">Para que sua página seja exibida no Teams, você deve incluir o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) e incluir uma chamada para `microsoftTeams.initialize()` depois que a página for carregada.</span><span class="sxs-lookup"><span data-stu-id="bb495-117">For your page to display in Teams, you must include the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="bb495-118">É assim que sua página e o cliente Teams se comunicam:</span><span class="sxs-lookup"><span data-stu-id="bb495-118">That is how your page and the Teams client communicate:</span></span>

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

## <a name="accessing-additional-content"></a><span data-ttu-id="bb495-119">Acessar conteúdo adicional</span><span class="sxs-lookup"><span data-stu-id="bb495-119">Accessing additional content</span></span>

### <a name="using-the-sdk-to-interact-with-teams"></a><span data-ttu-id="bb495-120">Usando o SDK para interagir com o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bb495-120">Using the SDK to interact with Teams</span></span>

<span data-ttu-id="bb495-121">O [SDK JavaScript do teams Client](~/tabs/how-to/using-teams-client-sdk.md) fornece várias funções adicionais que podem ser úteis ao desenvolver sua página de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bb495-121">The [Teams client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) provides many additional functions you may find useful while developer your content page.</span></span>

### <a name="deep-links"></a><span data-ttu-id="bb495-122">Deep links</span><span class="sxs-lookup"><span data-stu-id="bb495-122">Deep links</span></span>

<span data-ttu-id="bb495-123">Você pode criar links de profunda para entidades no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="bb495-123">You can create deep links to entities in Teams.</span></span> <span data-ttu-id="bb495-124">Normalmente, são usados para criar links que navegam para conteúdo e informações dentro de sua guia. Consulte [criar links de profundas para conteúdo e recursos no Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="bb495-124">Typically, these are used to create links that navigate to content and information within your tab. See [Create deep links to content and features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span></span>

### <a name="task-modules"></a><span data-ttu-id="bb495-125">Módulos de tarefa</span><span class="sxs-lookup"><span data-stu-id="bb495-125">Task Modules</span></span>

<span data-ttu-id="bb495-126">Um módulo de tarefa é uma experiência do tipo pop-up modal que você pode disparar na sua guia. Normalmente, em uma página de conteúdo, você não deseja navegar pelo usuário por várias páginas.</span><span class="sxs-lookup"><span data-stu-id="bb495-126">A task module is a modal popup-like experience that you can trigger from your tab. Typically in a content page you do not want to navigate your user through multiple pages.</span></span> <span data-ttu-id="bb495-127">Em vez disso, você usará os módulos de tarefas para apresentar formulários de coleta de informações adicionais, exibindo os detalhes de um item em uma lista ou qualquer outro momento necessário para apresentar informações adicionais ao usuário.</span><span class="sxs-lookup"><span data-stu-id="bb495-127">Instead, you will use task modules to present forms for gathering additional information, displaying the details of an item in a list, or any other time you need to present the user with additional information.</span></span> <span data-ttu-id="bb495-128">Os próprios módulos de tarefas podem ser páginas de conteúdo adicionais ou criados completamente usando cartões adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="bb495-128">The task modules themselves can be additional content pages, or created completely using Adaptive Cards.</span></span> <span data-ttu-id="bb495-129">Consulte [usando módulos de tarefas em guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md) para obter informações completas.</span><span class="sxs-lookup"><span data-stu-id="bb495-129">See [Using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md) for complete information.</span></span>

### <a name="valid-domains"></a><span data-ttu-id="bb495-130">Domínios válidos</span><span class="sxs-lookup"><span data-stu-id="bb495-130">Valid Domains</span></span>

<span data-ttu-id="bb495-131">Certifique-se de que todos os domínios de URL usados nas suas guias estão incluídos na `validDomains` matriz em seu [manifesto](~/concepts/build-and-test/apps-package.md).</span><span class="sxs-lookup"><span data-stu-id="bb495-131">Ensure that the all URL domains used in your tabs are included in the `validDomains` array in your [manifest](~/concepts/build-and-test/apps-package.md).</span></span> <span data-ttu-id="bb495-132">Para obter mais informações, consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) na referência de esquema de manifesto.</span><span class="sxs-lookup"><span data-stu-id="bb495-132">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema reference.</span></span> <span data-ttu-id="bb495-133">No entanto, lembre-se de que a funcionalidade principal da sua guia existe no Microsoft Teams e não fora do teams.</span><span class="sxs-lookup"><span data-stu-id="bb495-133">However, be mindful that the core functionality of your tab exists within Teams and not outside of Teams.</span></span>

## <a name="show-a-native-loading-indicator"></a><span data-ttu-id="bb495-134">Mostrar um indicador de carregamento nativo</span><span class="sxs-lookup"><span data-stu-id="bb495-134">Show a native loading indicator</span></span>

<span data-ttu-id="bb495-135">A partir [do esquema de manifesto v 1.7](../../../resources/schema/manifest-schema.md), você pode fornecer um [indicador de carregamento nativo](../../../resources/schema/manifest-schema.md#showloadingindicator) sempre que o conteúdo da Web é carregado no Teams, por exemplo, [página de conteúdo da guia](#integrate-your-code-with-teams), página de [configuração](configuration-page.md), [página de remoção](removal-page.md) e [módulos de tarefa em guias](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span><span class="sxs-lookup"><span data-stu-id="bb495-135">Starting with [manifest schema v1.7](../../../resources/schema/manifest-schema.md), you can provide a [native loading indicator](../../../resources/schema/manifest-schema.md#showloadingindicator) wherever your web content is loaded in Teams, e.g., [tab content page](#integrate-your-code-with-teams), [configuration page](configuration-page.md), [removal page](removal-page.md) and [task modules in tabs](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span></span>

> [!NOTE]
> <span data-ttu-id="bb495-136">Se você indicar  `"showLoadingIndicator : true`  no manifesto do aplicativo, todas as páginas configuração de guia, conteúdo e remoção e todos os módulos de tarefa com base em iframe devem seguir o protocolo obrigatório, abaixo:</span><span class="sxs-lookup"><span data-stu-id="bb495-136">If you indicate  `"showLoadingIndicator : true`  in your app manifest, then all tab configuration, content, and removal pages and all iframe-based task modules must follow the mandatory protocol, below:</span></span>

1. <span data-ttu-id="bb495-137">Para mostrar o indicador de carregamento, adicione-o `"showLoadingIndicator": true` ao seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="bb495-137">To show the loading indicator, add `"showLoadingIndicator": true` to your manifest.</span></span> 
2. <span data-ttu-id="bb495-138">Lembre-se de chamar `microsoftTeams.initialize();` .</span><span class="sxs-lookup"><span data-stu-id="bb495-138">Remember to call `microsoftTeams.initialize();`.</span></span>
3. <span data-ttu-id="bb495-139">**Opcional**.</span><span class="sxs-lookup"><span data-stu-id="bb495-139">**Optional**.</span></span> <span data-ttu-id="bb495-140">Se você estiver pronto para imprimir na tela e quiser carregar o restante do conteúdo do aplicativo, você pode ocultar manualmente o indicador de carregamento chamando `microsoftTeams.appInitialization.notifyAppLoaded();`</span><span class="sxs-lookup"><span data-stu-id="bb495-140">If you're ready to print to the screen and wish to lazy load the rest of your application's content, you can manually hide the loading indicator by calling `microsoftTeams.appInitialization.notifyAppLoaded();`</span></span>
4. <span data-ttu-id="bb495-141">**Obrigatório**.</span><span class="sxs-lookup"><span data-stu-id="bb495-141">**Mandatory**.</span></span> <span data-ttu-id="bb495-142">Por fim, chame `microsoftTeams.appInitialization.notifySuccess()` para notificar as equipes de que seu aplicativo carregou com êxito.</span><span class="sxs-lookup"><span data-stu-id="bb495-142">Finally, call `microsoftTeams.appInitialization.notifySuccess()` to notify Teams that your app has successfully loaded.</span></span> <span data-ttu-id="bb495-143">O Microsoft Teams ocultará o indicador de carregamento, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="bb495-143">Teams will then hide the loading indicator if applicable.</span></span> <span data-ttu-id="bb495-144">Se  `notifySuccess`  não for chamado dentro de 30 segundos, será considerado que seu aplicativo esgotou o tempo limite e uma tela de erro com uma opção de repetição será exibida.</span><span class="sxs-lookup"><span data-stu-id="bb495-144">If  `notifySuccess`  is not called within 30 seconds, it will be assumed that your app timed out and an error screen with a retry option will appear.</span></span>
5. <span data-ttu-id="bb495-145">Se o aplicativo não puder ser carregado, você poderá chamá-lo `microsoftTeams.appInitialization.notifyFailure(reason);` para permitir que as equipes saibam que houve um erro.</span><span class="sxs-lookup"><span data-stu-id="bb495-145">If your application fails to load, you can call `microsoftTeams.appInitialization.notifyFailure(reason);` to let Teams know there was an error.</span></span> <span data-ttu-id="bb495-146">Uma tela de erro será exibida para o usuário:</span><span class="sxs-lookup"><span data-stu-id="bb495-146">An error screen will then be shown to the user:</span></span>

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
