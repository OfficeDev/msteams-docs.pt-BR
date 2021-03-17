---
title: Removendo margens de tabulação no Microsoft Teams
author: laujan
description: Descreve como a remoção das margens de tabulação melhorará a experiência do desenvolvedor.
keywords: guia removendo preenchimento de margens
ms.topic: reference
ms.author: lomeybur
ms.openlocfilehash: f26701b2c432ba35ce6f069eabd3b401aae8e369
ms.sourcegitcommit: 1ce74ed167bb81bf09f7f6f8d518093efafb549e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2021
ms.locfileid: "50827925"
---
# <a name="tab-margin-changes"></a><span data-ttu-id="7c554-104">Mudanças na margem da guia</span><span class="sxs-lookup"><span data-stu-id="7c554-104">Tab margin changes</span></span>

<span data-ttu-id="7c554-105">Este documento descreve como a remoção de margens em torno de todas as guias no Microsoft Teams melhorará a experiência do desenvolvedor ao criar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7c554-105">This document describes how the removal of margins around all tabs in Microsoft Teams will enhance the developer's experience when building apps.</span></span> <span data-ttu-id="7c554-106">Este é um aprimoramento introduzido no Microsoft Teams em 2021.</span><span class="sxs-lookup"><span data-stu-id="7c554-106">This is an enhancement introduced in Microsoft Teams in 2021.</span></span>
<span data-ttu-id="7c554-107">Remover as margens ao redor de todas as guias permitirá que os desenvolvedores criem aplicativos que pareçam mais nativos para o Teams.</span><span class="sxs-lookup"><span data-stu-id="7c554-107">Removing the margins around all tabs will allow developers to build apps that look more native to Teams.</span></span> <span data-ttu-id="7c554-108">Isso também se alinhará com nossos designs [de kit de interface do usuário.](~/tabs/design/tabs.md)</span><span class="sxs-lookup"><span data-stu-id="7c554-108">This will also align with our [UI kit designs](~/tabs/design/tabs.md).</span></span> <span data-ttu-id="7c554-109">A maioria dos aplicativos já fica melhor sem as margens ao redor de suas experiências.</span><span class="sxs-lookup"><span data-stu-id="7c554-109">Most apps already look better without the margins surrounding their experiences.</span></span> <span data-ttu-id="7c554-110">No entanto, algumas guias são afetadas visualmente por essa alteração, e os desenvolvedores devem fazer as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="7c554-110">However, some tabs are visually affected by this change, and developers must make the necessary changes.</span></span>

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Inteligência de tabulação e sem margens" border="false":::

## <a name="timelines"></a><span data-ttu-id="7c554-112">Linhas do tempo</span><span class="sxs-lookup"><span data-stu-id="7c554-112">Timelines</span></span>

* <span data-ttu-id="7c554-113">5 de março de 2021 - Margens removidas na [Visualização do Desenvolvedor Público.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="7c554-113">March 5, 2021 - Margins removed in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
* <span data-ttu-id="7c554-114">15 de junho de 2021 - As margens serão removidas em produção.</span><span class="sxs-lookup"><span data-stu-id="7c554-114">June 15, 2021 - Margins will be removed in production.</span></span>

## <a name="guidelines"></a><span data-ttu-id="7c554-115">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="7c554-115">Guidelines</span></span>

<span data-ttu-id="7c554-116">Os aplicativos do Microsoft Teams que usam guias serão afetados por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="7c554-116">Microsoft Teams apps that use tabs will be affected by this change.</span></span> <span data-ttu-id="7c554-117">Os desenvolvedores devem alternar para [Visualização](~/resources/dev-preview/developer-preview-intro.md) de Desenvolvedor Público para determinar como suas guias são afetadas e fazer as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="7c554-117">Developers must switch to [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) in order to determine how their tabs are affected and make the necessary changes.</span></span>

<span data-ttu-id="7c554-118">Os desenvolvedores de guias não devem confiar no Teams para fornecer margens ao redor de suas guias.</span><span class="sxs-lookup"><span data-stu-id="7c554-118">Tab developers must not rely on Teams to provide margins surrounding their tabs.</span></span> <span data-ttu-id="7c554-119">Os desenvolvedores são incentivados a adicionar margens ao redor de seus designs de tabulação onde é necessário.</span><span class="sxs-lookup"><span data-stu-id="7c554-119">Developers are encouraged to add margins around their tab designs where it is required.</span></span> <span data-ttu-id="7c554-120">Designs de aplicativos em produção podem parecer que há preenchimento extra, ou seja, margens fornecidas pelo Teams e margens fornecidas pela guia. No entanto, o preenchimento extra é apenas temporário e desaparecerá em algumas semanas, deixando apenas o preenchimento fornecido pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c554-120">App designs in production can look like there is extra padding, that is, margins provided by Teams and margins provided by the tab. However, the extra padding is only temporary and will go away in a few weeks, leaving only the app's provided padding.</span></span>

## <a name="faq"></a><span data-ttu-id="7c554-121">Perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="7c554-121">FAQ</span></span>

<span data-ttu-id="7c554-122">**Tudo bem para o aplicativo cromado, como barra de header ou barra de tarefas, tocar nas bordas de nossos designs?**</span><span class="sxs-lookup"><span data-stu-id="7c554-122">**Is it OK for app chrome, such as header bar or taskbar, to touch the edges of our designs?**</span></span>

<span data-ttu-id="7c554-123">Sim, isso é bom e incentivado.</span><span class="sxs-lookup"><span data-stu-id="7c554-123">Yes, this is fine and encouraged.</span></span> <span data-ttu-id="7c554-124">Isso ajuda o aplicativo a se sentir nativo.</span><span class="sxs-lookup"><span data-stu-id="7c554-124">This helps the app feel native.</span></span>

<span data-ttu-id="7c554-125">**Tudo bem para conteúdo do aplicativo, como texto, logotipos e imagens, tocar as bordas esquerda e direita de nossos designs?**</span><span class="sxs-lookup"><span data-stu-id="7c554-125">**Is it OK for app content, such as text, logos, and images, to touch the left and right edges of our designs?**</span></span>

<span data-ttu-id="7c554-126">Não, você deve fornecer seu próprio preenchimento ou margens à esquerda e à direita de todo o conteúdo do aplicativo para garantir que ele não toque nas bordas da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7c554-126">No, you must provide your own padding or margins to the left and right of all app content to ensure it does not touch the edges of your UI.</span></span> <span data-ttu-id="7c554-127">Você também pode adicionar margens na parte superior da guia, se necessário.</span><span class="sxs-lookup"><span data-stu-id="7c554-127">You can also add margins at the top of your tab, if required.</span></span>

<span data-ttu-id="7c554-128">**Qual é o tamanho das margens que o Teams aplicou anteriormente?**</span><span class="sxs-lookup"><span data-stu-id="7c554-128">**What's the size of the margins Teams previously applied?**</span></span>

* <span data-ttu-id="7c554-129">Esquerda e direita: 20px</span><span class="sxs-lookup"><span data-stu-id="7c554-129">Left and right: 20px</span></span>
* <span data-ttu-id="7c554-130">Top: 16px</span><span class="sxs-lookup"><span data-stu-id="7c554-130">Top: 16px</span></span>
* <span data-ttu-id="7c554-131">Inferior: 0px</span><span class="sxs-lookup"><span data-stu-id="7c554-131">Bottom: 0px</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="7c554-132">Todas as guias têm suas margens removidas: guias pessoais, guias de chat (grupo), guias de reunião e guias de canal.</span><span class="sxs-lookup"><span data-stu-id="7c554-132">All tabs have their margins removed: personal tabs, (group) chat tabs, meeting tabs, and channel tabs.</span></span>
> * <span data-ttu-id="7c554-133">Não há como optar ou não por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="7c554-133">There is no way to opt-in or opt-out of this change.</span></span> <span data-ttu-id="7c554-134">Ela se aplicará a todas as guias.</span><span class="sxs-lookup"><span data-stu-id="7c554-134">It will apply to all tabs.</span></span>
> * <span data-ttu-id="7c554-135">Essa alteração pode afetar guias que dependem do Microsoft Teams para fornecer margens em torno de sua interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7c554-135">This change can affect tabs that rely on Microsoft Teams to provide margins surrounding their UI.</span></span>
