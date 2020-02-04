---
title: Criar uma página de conteúdo
author: laujan
description: ''
keywords: guias do teams com o canal de grupo configurado como estático
ms.topic: conceptual
ms.author: v-laujan
ms.openlocfilehash: ac85e000c9bdaebf28cb33143a7c82a348d3771e
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672703"
---
# <a name="create-a-content-page-for-your-tab"></a><span data-ttu-id="169cd-103">Criar uma página de conteúdo para sua guia</span><span class="sxs-lookup"><span data-stu-id="169cd-103">Create a content page for your tab</span></span>

<span data-ttu-id="169cd-104">Uma página de conteúdo é uma página da Web que é renderizada no cliente Teams.</span><span class="sxs-lookup"><span data-stu-id="169cd-104">A content page is a webpage that is rendered within the Teams client.</span></span> <span data-ttu-id="169cd-105">Normalmente, são parte de:</span><span class="sxs-lookup"><span data-stu-id="169cd-105">Typically these are part of:</span></span>

* <span data-ttu-id="169cd-106">Uma guia personalizada de escopo pessoal-nesta instância, a página de conteúdo é a primeira página que o usuário encontra.</span><span class="sxs-lookup"><span data-stu-id="169cd-106">A personal-scoped custom tab - In this instance the content page is the first page the user encounters.</span></span>
* <span data-ttu-id="169cd-107">Uma guia personalizada de canal/grupo, depois que o usuário fixa e configura a guia no contexto apropriado, a página de conteúdo é exibida.</span><span class="sxs-lookup"><span data-stu-id="169cd-107">A channel/group custom tab - After the user pins and configures the tab in the appropriate context, the content page is displayed.</span></span>
* <span data-ttu-id="169cd-108">Um [módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md) -você pode criar uma página de conteúdo e incorporá-la como uma WebView dentro de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="169cd-108">A [task module](~/task-modules-and-cards/what-are-task-modules.md) - You can create a content page and embed it as a webview inside a task module.</span></span> <span data-ttu-id="169cd-109">A página será renderizada dentro do popup modal.</span><span class="sxs-lookup"><span data-stu-id="169cd-109">The page will be rendered inside the modal popup.</span></span>

<span data-ttu-id="169cd-110">Este artigo é específico para usar páginas de conteúdo como guias; no entanto, a maioria das orientações aqui aplica-se independentemente de como a página de conteúdo é apresentada ao usuário final.</span><span class="sxs-lookup"><span data-stu-id="169cd-110">This article is specific to using content pages as tabs; however the majority of the guidance here would apply regardless of how the content page is presented to the end-user.</span></span>

## <a name="tab-content-and-style-guidelines"></a><span data-ttu-id="169cd-111">Diretrizes de conteúdo e estilo da guia</span><span class="sxs-lookup"><span data-stu-id="169cd-111">Tab content and style guidelines</span></span>

<span data-ttu-id="169cd-112">O objetivo geral da guia é fornecer acesso a conteúdo significativo e envolvente que tenha um valor prático e uma finalidade evidente.</span><span class="sxs-lookup"><span data-stu-id="169cd-112">Your tab's overall objective should be to provide access to meaningful and engaging content that has a practical value and an evident purpose.</span></span> <span data-ttu-id="169cd-113">Isso não significa que você tenha um estilo agradável, mas você deve se concentrar em minimizar a desordem, tornando seu design de guia limpo, intuitivo e de aparência de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="169cd-113">That does not mean that you should forego a pleasing style, but you should focus on minimizing clutter by making your tab design clean, navigation intuitive, and content immersive.</span></span> <span data-ttu-id="169cd-114">Veja [conteúdo e conversas, tudo de uma vez usando guias](~/tabs/design/tabs.md) e a [orientação do processo de aprovação do Microsoft Teams app](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span><span class="sxs-lookup"><span data-stu-id="169cd-114">See [Content and conversations, all at once using tabs](~/tabs/design/tabs.md) and [Microsoft Teams app approval process guidance](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span></span>

## <a name="integrate-your-code-with-teams"></a><span data-ttu-id="169cd-115">Integrar seu código com o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="169cd-115">Integrate your code with Teams</span></span>

<span data-ttu-id="169cd-116">Para que sua página seja exibida no Teams, você deve incluir o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) e incluir uma chamada para depois que `microsoftTeams.initialize()` a página for carregada.</span><span class="sxs-lookup"><span data-stu-id="169cd-116">For your page to display in Teams, you must include the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="169cd-117">É assim que sua página e o cliente Teams se comunicam:</span><span class="sxs-lookup"><span data-stu-id="169cd-117">That is how your page and the Teams client communicate:</span></span>

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

## <a name="accessing-additional-content"></a><span data-ttu-id="169cd-118">Acessar conteúdo adicional</span><span class="sxs-lookup"><span data-stu-id="169cd-118">Accessing additional content</span></span>

### <a name="using-the-sdk-to-interact-with-teams"></a><span data-ttu-id="169cd-119">Usando o SDK para interagir com o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="169cd-119">Using the SDK to interact with Teams</span></span>

<span data-ttu-id="169cd-120">O [SDK JavaScript do teams Client](~/tabs/how-to/using-teams-client-sdk.md) fornece várias funções adicionais que podem ser úteis ao desenvolver sua página de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="169cd-120">The [Teams client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) provides many additional functions you may find useful while developer your content page.</span></span>

### <a name="deep-links"></a><span data-ttu-id="169cd-121">Deep links</span><span class="sxs-lookup"><span data-stu-id="169cd-121">Deep links</span></span>

<span data-ttu-id="169cd-122">Você pode criar links de profunda para entidades no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="169cd-122">You can create deep links to entities in Teams.</span></span> <span data-ttu-id="169cd-123">Normalmente, são usados para criar links que navegam para conteúdo e informações dentro de sua guia. Consulte [criar links de profundas para conteúdo e recursos no Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="169cd-123">Typically, these are used to create links that navigate to content and information within your tab. See [Create deep links to content and features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span></span>

### <a name="task-modules"></a><span data-ttu-id="169cd-124">Módulos de tarefa</span><span class="sxs-lookup"><span data-stu-id="169cd-124">Task Modules</span></span>

<span data-ttu-id="169cd-125">Um módulo de tarefa é uma experiência de pop-up modal que você pode disparar na sua guia. normalmente, em uma página de conteúdo, você não deseja navegar pelo usuário por várias páginas.</span><span class="sxs-lookup"><span data-stu-id="169cd-125">A task module is a modal popup-like experience that you can trigger from your tab. Typically in a content page you do not want to navigate your user through multiple pages.</span></span> <span data-ttu-id="169cd-126">Em vez disso, você usará os módulos de tarefas para apresentar formulários de coleta de informações adicionais, exibindo os detalhes de um item em uma lista ou qualquer outro momento necessário para apresentar informações adicionais ao usuário.</span><span class="sxs-lookup"><span data-stu-id="169cd-126">Instead, you will use task modules to present forms for gathering additional information, displaying the details of an item in a list, or any other time you need to present the user with additional information.</span></span> <span data-ttu-id="169cd-127">Os próprios módulos de tarefas podem ser páginas de conteúdo adicionais ou criados completamente usando cartões adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="169cd-127">The task modules themselves can be additional content pages, or created completely using Adaptive Cards.</span></span> <span data-ttu-id="169cd-128">Consulte [usando módulos de tarefas em guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md) para obter informações completas.</span><span class="sxs-lookup"><span data-stu-id="169cd-128">See [Using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md) for complete information.</span></span>

### <a name="valid-domains"></a><span data-ttu-id="169cd-129">Domínios válidos</span><span class="sxs-lookup"><span data-stu-id="169cd-129">Valid Domains</span></span>

<span data-ttu-id="169cd-130">Certifique-se de que todos os domínios de URL usados nas suas guias `validDomains` estão incluídos na matriz em seu [manifesto](~/concepts/build-and-test/apps-package.md).</span><span class="sxs-lookup"><span data-stu-id="169cd-130">Ensure that the all URL domains used in your tabs are included in the `validDomains` array in your [manifest](~/concepts/build-and-test/apps-package.md).</span></span> <span data-ttu-id="169cd-131">Para obter mais informações, consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) na referência de esquema de manifesto.</span><span class="sxs-lookup"><span data-stu-id="169cd-131">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema reference.</span></span> <span data-ttu-id="169cd-132">No entanto, lembre-se de que a funcionalidade principal da sua guia existe no Microsoft Teams e não fora do teams.</span><span class="sxs-lookup"><span data-stu-id="169cd-132">However, be mindful that the core functionality of your tab exists within Teams and not outside of Teams.</span></span>
