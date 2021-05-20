---
title: Criar uma página de conteúdo
author: laujan
description: como criar uma página de conteúdo
keywords: equipes guias canal de grupo estática configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 136160cb9154d62be40d8e29075ac1fc86135a6b
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566674"
---
# <a name="create-a-content-page-for-your-tab"></a><span data-ttu-id="c2d9b-104">Crie uma página de conteúdo para sua guia</span><span class="sxs-lookup"><span data-stu-id="c2d9b-104">Create a content page for your tab</span></span>

<span data-ttu-id="c2d9b-105">Uma página de conteúdo é uma página da Web que é renderizada dentro do Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-105">A content page is a webpage that is rendered within the Teams client.</span></span> <span data-ttu-id="c2d9b-106">Normalmente, estes fazem parte de:</span><span class="sxs-lookup"><span data-stu-id="c2d9b-106">Typically these are part of:</span></span>

* <span data-ttu-id="c2d9b-107">Uma guia personalizada com escopo pessoal: Neste caso, a página de conteúdo é a primeira página que o usuário encontra.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-107">A personal-scoped custom tab: In this instance the content page is the first page the user encounters.</span></span>
* <span data-ttu-id="c2d9b-108">Uma guia personalizada de canal/grupo: Depois que o usuário fixa e configura a guia no contexto apropriado, a página de conteúdo é exibida.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-108">A channel/group custom tab: After the user pins and configures the tab in the appropriate context, the content page is displayed.</span></span>
* <span data-ttu-id="c2d9b-109">Um [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md): Você pode criar uma página de conteúdo e incorporá-la como uma webview dentro de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-109">A [task module](~/task-modules-and-cards/what-are-task-modules.md): You can create a content page and embed it as a webview inside a task module.</span></span> <span data-ttu-id="c2d9b-110">A página será renderizada dentro do popup modal.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-110">The page will be rendered inside the modal popup.</span></span>

<span data-ttu-id="c2d9b-111">Este artigo é específico para usar páginas de conteúdo como guias; no entanto, a maioria das orientações aqui se aplicaria independentemente de como a página de conteúdo é apresentada ao usuário final.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-111">This article is specific to using content pages as tabs; however the majority of the guidance here would apply regardless of how the content page is presented to the end-user.</span></span>

## <a name="tab-content-and-design-guidelines"></a><span data-ttu-id="c2d9b-112">Guiar o conteúdo e as diretrizes de design</span><span class="sxs-lookup"><span data-stu-id="c2d9b-112">Tab content and design guidelines</span></span>

<span data-ttu-id="c2d9b-113">O objetivo geral da sua guia deve ser fornecer acesso a conteúdo significativo e envolvente que tenha um valor prático e um propósito evidente.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-113">Your tab's overall objective should be to provide access to meaningful and engaging content that has a practical value and an evident purpose.</span></span> <span data-ttu-id="c2d9b-114">Isso não significa que você deve renunciar a um estilo agradável, mas você deve se concentrar em minimizar a desordem, tornando seu design de guia limpo, intuitivo de navegação e conteúdo imersivo.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-114">That does not mean that you should forego a pleasing style, but you should focus on minimizing clutter by making your tab design clean, navigation intuitive, and content immersive.</span></span>

<span data-ttu-id="c2d9b-115">Para obter mais informações, consulte as [diretrizes de design](~/tabs/design/tabs.md) de guias e [as diretrizes de validação da loja Microsoft Teams](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)</span><span class="sxs-lookup"><span data-stu-id="c2d9b-115">For more information, see the [tab design guidelines](~/tabs/design/tabs.md) and [Microsoft Teams store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)</span></span>

## <a name="integrate-your-code-with-teams"></a><span data-ttu-id="c2d9b-116">Integre seu código com Teams</span><span class="sxs-lookup"><span data-stu-id="c2d9b-116">Integrate your code with Teams</span></span>

<span data-ttu-id="c2d9b-117">Para que sua página seja exibida em Teams, você deve incluir o [Microsoft Teams Cliente JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) e incluir uma chamada para `microsoftTeams.initialize()` depois que sua página for carregada.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-117">For your page to display in Teams, you must include the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="c2d9b-118">É assim que sua página e o Teams cliente se comunicam:</span><span class="sxs-lookup"><span data-stu-id="c2d9b-118">That is how your page and the Teams client communicate:</span></span>

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

## <a name="accessing-additional-content"></a><span data-ttu-id="c2d9b-119">Acessando conteúdo adicional</span><span class="sxs-lookup"><span data-stu-id="c2d9b-119">Accessing additional content</span></span>

### <a name="using-the-sdk-to-interact-with-teams"></a><span data-ttu-id="c2d9b-120">Usando o SDK para interagir com Teams</span><span class="sxs-lookup"><span data-stu-id="c2d9b-120">Using the SDK to interact with Teams</span></span>

<span data-ttu-id="c2d9b-121">O [Teams cliente JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) fornece muitas funções adicionais que você pode achar úteis ao desenvolver sua página de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-121">The [Teams client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) provides many additional functions you may find useful while developing your content page.</span></span>

### <a name="deep-links"></a><span data-ttu-id="c2d9b-122">Links profundos</span><span class="sxs-lookup"><span data-stu-id="c2d9b-122">Deep links</span></span>

<span data-ttu-id="c2d9b-123">Você pode criar links profundos para entidades em Teams.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-123">You can create deep links to entities in Teams.</span></span> <span data-ttu-id="c2d9b-124">Normalmente, estes são usados para criar links que navegam para conteúdo e informações dentro de sua guia. Para obter mais informações, consulte [Criar links profundos para conteúdo e recursos em Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="c2d9b-124">Typically, these are used to create links that navigate to content and information within your tab. For more information, see [Create deep links to content and features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span></span>

### <a name="task-modules"></a><span data-ttu-id="c2d9b-125">Módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="c2d9b-125">Task Modules</span></span>

<span data-ttu-id="c2d9b-126">Um módulo de tarefa é uma experiência modal semelhante ao pop-up que você pode acionar a partir de sua guia. Normalmente em uma página de conteúdo você não quer navegar pelo usuário através de várias páginas.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-126">A task module is a modal popup-like experience that you can trigger from your tab. Typically in a content page you do not want to navigate your user through multiple pages.</span></span> <span data-ttu-id="c2d9b-127">Em vez disso, você usará módulos de tarefa para apresentar formulários para coletar informações adicionais, exibindo os detalhes de um item em uma lista ou qualquer outra hora que você precisar apresentar ao usuário informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-127">Instead, you will use task modules to present forms for gathering additional information, displaying the details of an item in a list, or any other time you need to present the user with additional information.</span></span> <span data-ttu-id="c2d9b-128">Os módulos de tarefa em si podem ser páginas de conteúdo adicionais ou criadas completamente usando cartões adaptativos.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-128">The task modules themselves can be additional content pages, or created completely using Adaptive Cards.</span></span> <span data-ttu-id="c2d9b-129">Consulte [Usando módulos de tarefas em guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md) para obter informações completas.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-129">See [Using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md) for complete information.</span></span>

### <a name="valid-domains"></a><span data-ttu-id="c2d9b-130">Domínios válidos</span><span class="sxs-lookup"><span data-stu-id="c2d9b-130">Valid Domains</span></span>

<span data-ttu-id="c2d9b-131">Certifique-se de que todos os domínios de URL usados em suas guias estejam incluídos no `validDomains` array em seu [manifesto](~/concepts/build-and-test/apps-package.md).</span><span class="sxs-lookup"><span data-stu-id="c2d9b-131">Ensure that the all URL domains used in your tabs are included in the `validDomains` array in your [manifest](~/concepts/build-and-test/apps-package.md).</span></span> <span data-ttu-id="c2d9b-132">Para obter mais informações, consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) na referência manifesto esquema.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-132">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema reference.</span></span> <span data-ttu-id="c2d9b-133">No entanto, esteja ciente de que a funcionalidade central da sua guia existe dentro de Teams e não fora de Teams.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-133">However, be mindful that the core functionality of your tab exists within Teams and not outside of Teams.</span></span>

## <a name="reorder-static-personal-tabs"></a><span data-ttu-id="c2d9b-134">Reordenar guias pessoais estáticas</span><span class="sxs-lookup"><span data-stu-id="c2d9b-134">Reorder static personal tabs</span></span>

<span data-ttu-id="c2d9b-135">Começando com a versão manifesto 1.7, os desenvolvedores podem reorganizar todas as guias em seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-135">Starting with manifest version 1.7, developers can rearrange all tabs in their personal app.</span></span> <span data-ttu-id="c2d9b-136">Em particular, um desenvolvedor pode mover a guia *de bate-papo do bot,* que sempre é padrão para a primeira posição, em qualquer lugar no cabeçalho da guia do aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-136">In particular, a developer can move the *bot chat* tab, which always defaults to the first position, anywhere in the personal app tab header.</span></span> <span data-ttu-id="c2d9b-137">Declaramos duas palavras-chave reservadas da tab EntityId, *conversas* e *sobre*.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-137">We’ve declared two reserved tab entityId keywords, *conversations* and *about*.</span></span>

<span data-ttu-id="c2d9b-138">Se você criar um bot com um escopo *pessoal,* ele aparecerá na primeira posição da guia em um aplicativo pessoal por padrão.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-138">If you create a bot with a *personal* scope, it will show up in the first tab position in a personal app by default.</span></span> <span data-ttu-id="c2d9b-139">Se você deseja movê-lo para outra posição, você deve adicionar um objeto de guia estática ao seu manifesto com a palavra-chave reservada, *conversas*.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-139">If you wish to move it to another position, you must add a static tab object to your manifest with the reserved keyword, *conversations*.</span></span> <span data-ttu-id="c2d9b-140">A guia *de conversação* é exibida na Web ou na área de trabalho com base em onde você adiciona a guia *de conversação* no `staticTabs` array.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-140">The *conversation* tab appears on web or desktop based on where you add the *conversation* tab in the `staticTabs` array.</span></span> 

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

## <a name="show-a-native-loading-indicator"></a><span data-ttu-id="c2d9b-141">Mostre um indicador de carregamento nativo</span><span class="sxs-lookup"><span data-stu-id="c2d9b-141">Show a native loading indicator</span></span>

<span data-ttu-id="c2d9b-142">Começando com [o esquema manifesto v1.7](../../../resources/schema/manifest-schema.md), você pode fornecer um [indicador de carregamento nativo](../../../resources/schema/manifest-schema.md#showloadingindicator) onde quer que seu conteúdo da Web esteja carregado em Teams.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-142">Starting with [manifest schema v1.7](../../../resources/schema/manifest-schema.md), you can provide a [native loading indicator](../../../resources/schema/manifest-schema.md#showloadingindicator) wherever your web content is loaded in Teams.</span></span> <span data-ttu-id="c2d9b-143">Por exemplo, [página de conteúdo de guia,](#integrate-your-code-with-teams)página de [configuração,](configuration-page.md) [página de remoção](removal-page.md)e [módulos de tarefa em guias](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span><span class="sxs-lookup"><span data-stu-id="c2d9b-143">For example, [tab content page](#integrate-your-code-with-teams), [configuration page](configuration-page.md), [removal page](removal-page.md), and [task modules in tabs](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span></span>

> [!NOTE]
> * <span data-ttu-id="c2d9b-144">O comportamento dos clientes móveis não é configurável através desta propriedade manifesto.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-144">The behavior on mobile clients is not configurable through this manifest property.</span></span> <span data-ttu-id="c2d9b-145">Os clientes móveis mostram um indicador de carregamento nativo por padrão em páginas de conteúdo e módulos de tarefa baseados em iframe.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-145">Mobile clients show a native loading indicator by default across content pages and iframe-based task modules.</span></span> <span data-ttu-id="c2d9b-146">Este indicador no celular é mostrado quando uma solicitação é feita para buscar conteúdo e é rejeitada assim que a solicitação é concluída.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-146">This indicator on mobile is shown when a request is made to fetch content and gets dismissed as soon as the request gets completed.</span></span>
> * <span data-ttu-id="c2d9b-147">Se você indicar  `"showLoadingIndicator : true`  no manifesto do aplicativo, todas as páginas de configuração, conteúdo e remoção da guia e todos os módulos de tarefa baseados em iframe devem seguir o protocolo obrigatório, abaixo:</span><span class="sxs-lookup"><span data-stu-id="c2d9b-147">If you indicate  `"showLoadingIndicator : true`  in your app manifest, then all tab configuration, content, and removal pages and all iframe-based task modules must follow the mandatory protocol, below:</span></span>

<span data-ttu-id="c2d9b-148">**Para mostrar o indicador de carregamento**</span><span class="sxs-lookup"><span data-stu-id="c2d9b-148">**To show the loading indicator**</span></span>

* <span data-ttu-id="c2d9b-149">Adicione `"showLoadingIndicator": true` ao seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-149">Add `"showLoadingIndicator": true` to your manifest.</span></span> 
* <span data-ttu-id="c2d9b-150">Lembre-se de `microsoftTeams.initialize();` ligar.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-150">Remember to call `microsoftTeams.initialize();`.</span></span>
* <span data-ttu-id="c2d9b-151">**Opcional**: Se você estiver pronto para imprimir na tela e desejar carregar o resto do conteúdo do aplicativo, você pode ocultar manualmente o indicador de carregamento ligando para `microsoftTeams.appInitialization.notifyAppLoaded();`</span><span class="sxs-lookup"><span data-stu-id="c2d9b-151">**Optional**: If you're ready to print to the screen and wish to lazy load the rest of your application's content, you can manually hide the loading indicator by calling `microsoftTeams.appInitialization.notifyAppLoaded();`</span></span>
* <span data-ttu-id="c2d9b-152">**Obrigatório**: Por fim, ligue `microsoftTeams.appInitialization.notifySuccess()` para notificar Teams que seu aplicativo carregou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-152">**Mandatory**: Finally, call `microsoftTeams.appInitialization.notifySuccess()` to notify Teams that your app has successfully loaded.</span></span> <span data-ttu-id="c2d9b-153">Teams, em seguida, ocultará o indicador de carregamento, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-153">Teams will then hide the loading indicator if applicable.</span></span> <span data-ttu-id="c2d9b-154">Se  `notifySuccess`  não for chamado dentro de 30 segundos, presume-se que seu aplicativo foi cronometrado e uma tela de erro com uma opção de repetição será exibida.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-154">If  `notifySuccess`  is not called within 30 seconds, it will be assumed that your app timed out and an error screen with a retry option will appear.</span></span>
* <span data-ttu-id="c2d9b-155">Se o aplicativo não for carregado, você pode ligar `microsoftTeams.appInitialization.notifyFailure(reason);` para avisar Teams que houve um erro.</span><span class="sxs-lookup"><span data-stu-id="c2d9b-155">If your application fails to load, you can call `microsoftTeams.appInitialization.notifyFailure(reason);` to let Teams know there was an error.</span></span> <span data-ttu-id="c2d9b-156">Em seguida, uma tela de erro será mostrada ao usuário:</span><span class="sxs-lookup"><span data-stu-id="c2d9b-156">An error screen will then be shown to the user:</span></span>

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
