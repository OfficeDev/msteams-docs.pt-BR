---
title: Guias em dispositivos móveis
description: Descreve considerações do desenvolvedor para implementar guias em Microsoft Teams celular.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 41ba96b64bd31f3b226aeba72969bc44c1ae8955
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630653"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="a8222-103">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="a8222-103">Tabs on mobile</span></span>

<span data-ttu-id="a8222-104">Ao criar um aplicativo Microsoft Teams que inclui uma guia, você deve considerar (e testar) como sua guia funcionará nos clientes android e iOS Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a8222-104">When you're building a Microsoft Teams app that includes a tab, you must consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="a8222-105">As seções abaixo delineam alguns dos principais cenários que você precisa considerar.</span><span class="sxs-lookup"><span data-stu-id="a8222-105">The sections below outline some of the key scenarios you need to consider.</span></span>

## <a name="authentication"></a><span data-ttu-id="a8222-106">Autenticação</span><span class="sxs-lookup"><span data-stu-id="a8222-106">Authentication</span></span>

<span data-ttu-id="a8222-107">Para que a autenticação funcione em clientes móveis, você deve atualizar Teams SDK JavaScript para pelo menos a versão 1.4.1.</span><span class="sxs-lookup"><span data-stu-id="a8222-107">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

## <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="a8222-108">Baixa largura de banda e conexões intermitentes</span><span class="sxs-lookup"><span data-stu-id="a8222-108">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="a8222-109">Clientes móveis regularmente precisam funcionar com baixa largura de banda e conexões intermitentes.</span><span class="sxs-lookup"><span data-stu-id="a8222-109">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="a8222-110">Seu aplicativo deve lidar com quaisquer tempos de tempo apropriados fornecendo uma mensagem contextual ao usuário.</span><span class="sxs-lookup"><span data-stu-id="a8222-110">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="a8222-111">Você também deve ter indicadores de progresso do usuário para fornecer comentários aos usuários sobre processos de longa duração.</span><span class="sxs-lookup"><span data-stu-id="a8222-111">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

## <a name="testing-on-mobile-clients"></a><span data-ttu-id="a8222-112">Testes em clientes móveis</span><span class="sxs-lookup"><span data-stu-id="a8222-112">Testing on mobile clients</span></span>

<span data-ttu-id="a8222-113">Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades.</span><span class="sxs-lookup"><span data-stu-id="a8222-113">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="a8222-114">Para dispositivos Android, você pode usar [o DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="a8222-114">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="a8222-115">Recomendamos que você teste em dispositivos de alto e baixo desempenho, incluindo um tablet.</span><span class="sxs-lookup"><span data-stu-id="a8222-115">We recommend that you test on both high- and low-performance devices, including a tablet.</span></span>

## <a name="distribution"></a><span data-ttu-id="a8222-116">Distribuição</span><span class="sxs-lookup"><span data-stu-id="a8222-116">Distribution</span></span>

<span data-ttu-id="a8222-117">Os aplicativos listados no Teams devem ser aprovados para uso móvel para funcionar corretamente no cliente Teams celular.</span><span class="sxs-lookup"><span data-stu-id="a8222-117">Apps listed on the Teams store must be approved for mobile use to function properly in the Teams mobile client.</span></span> <span data-ttu-id="a8222-118">A disponibilidade e o comportamento de tabulação dependem da aprovação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8222-118">Tab availability and behavior depends on whether your app is approved.</span></span>

### <a name="apps-on-teams-store-approved-for-mobile"></a><span data-ttu-id="a8222-119">Aplicativos no Teams store aprovados para dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="a8222-119">Apps on Teams store approved for mobile</span></span>

<span data-ttu-id="a8222-120">A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo é listado no Teams e aprovado para uso móvel:</span><span class="sxs-lookup"><span data-stu-id="a8222-120">The following table describes tab availability and behavior when the app is listed on the Teams store and approved for mobile use:</span></span>

|<span data-ttu-id="a8222-121">Recursos</span><span class="sxs-lookup"><span data-stu-id="a8222-121">Capability</span></span>   |<span data-ttu-id="a8222-122">Disponibilidade móvel?</span><span class="sxs-lookup"><span data-stu-id="a8222-122">Mobile availability?</span></span>   |<span data-ttu-id="a8222-123">Comportamento móvel</span><span class="sxs-lookup"><span data-stu-id="a8222-123">Mobile behavior</span></span>|
|----------|-----------|------------|
|<span data-ttu-id="a8222-124">Canal</span><span class="sxs-lookup"><span data-stu-id="a8222-124">Channel</span></span> <br /> <span data-ttu-id="a8222-125">e guia grupo</span><span class="sxs-lookup"><span data-stu-id="a8222-125">and group tab</span></span>|<span data-ttu-id="a8222-126">Sim</span><span class="sxs-lookup"><span data-stu-id="a8222-126">Yes</span></span>|<span data-ttu-id="a8222-127">A guia é aberta Teams cliente móvel usando a configuração do `contentUrl` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8222-127">Tab opens in the Teams mobile client using your app's `contentUrl` configuration.</span></span>|
|<span data-ttu-id="a8222-128">Aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="a8222-128">Personal app</span></span>|<span data-ttu-id="a8222-129">Sim</span><span class="sxs-lookup"><span data-stu-id="a8222-129">Yes</span></span>|<span data-ttu-id="a8222-130">Cada guia na guia aplicativo pessoal é aberta no cliente Teams móvel usando sua respectiva `contentUrl` configuração.</span><span class="sxs-lookup"><span data-stu-id="a8222-130">Each tab in the personal app tab opens in the Teams mobile client using its respective `contentUrl` configuration.</span></span>|

### <a name="apps-on-teams-store-not-approved-for-mobile"></a><span data-ttu-id="a8222-131">Aplicativos na Teams não aprovados para dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="a8222-131">Apps on Teams store not approved for mobile</span></span>

<span data-ttu-id="a8222-132">A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo está listado no Teams, mas não aprovado para uso móvel:</span><span class="sxs-lookup"><span data-stu-id="a8222-132">The following table describes tab availability and behavior when the app is listed on the Teams store but not approved for mobile use:</span></span>

| <span data-ttu-id="a8222-133">Recursos</span><span class="sxs-lookup"><span data-stu-id="a8222-133">Capability</span></span> | <span data-ttu-id="a8222-134">Disponibilidade móvel?</span><span class="sxs-lookup"><span data-stu-id="a8222-134">Mobile availability?</span></span> | <span data-ttu-id="a8222-135">Comportamento móvel</span><span class="sxs-lookup"><span data-stu-id="a8222-135">Mobile behavior</span></span> |
|----------|-----------|------------|
|<span data-ttu-id="a8222-136">Guia Canal e grupo</span><span class="sxs-lookup"><span data-stu-id="a8222-136">Channel and group tab</span></span>|<span data-ttu-id="a8222-137">Sim</span><span class="sxs-lookup"><span data-stu-id="a8222-137">Yes</span></span>|<span data-ttu-id="a8222-138">A guia é aberta no navegador padrão do dispositivo, em vez do cliente Teams móvel usando a configuração do aplicativo, que também deve ser incluído na função do `websiteUrl` `setSettings()` [código-fonte.](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a8222-138">Tab opens in the device's default browser instead of the Teams mobile client using your app's `websiteUrl` configuration, which also must be included in your source code's `setSettings()` [function](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true).</span></span> <span data-ttu-id="a8222-139">No entanto, os usuários ainda podem exibir a guia no cliente Teams móvel selecionando **Mais** ao lado do aplicativo e escolhendo **Abrir**, o que dispara a configuração do `contentUrl` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8222-139">However, users can still view the tab in the Teams mobile client by selecting **More** next to the app and choosing **Open**, which triggers your app’s `contentUrl` configuration.</span></span>|
|<span data-ttu-id="a8222-140">Aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="a8222-140">Personal app</span></span>|<span data-ttu-id="a8222-141">Não</span><span class="sxs-lookup"><span data-stu-id="a8222-141">No</span></span>|<span data-ttu-id="a8222-142">Não aplicável</span><span class="sxs-lookup"><span data-stu-id="a8222-142">Not applicable</span></span>|

### <a name="apps-not-on-teams-store"></a><span data-ttu-id="a8222-143">Aplicativos que não Teams loja</span><span class="sxs-lookup"><span data-stu-id="a8222-143">Apps not on Teams store</span></span>

<span data-ttu-id="a8222-144">Se você estiver fazendo sideload do seu aplicativo ou publicação no catálogo de aplicativos de uma organização, o comportamento da guia será o mesmo Teams aplicativos da loja aprovados pela Microsoft para dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="a8222-144">If you're sideloading your app or publishing to an org's app catalog, tab behavior will be the same as Teams store apps approved by Microsoft for mobile.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8222-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8222-145">See also</span></span>

* [<span data-ttu-id="a8222-146">Diretrizes de design de tabulação</span><span class="sxs-lookup"><span data-stu-id="a8222-146">Tab design guidelines</span></span>](~/tabs/design/tabs.md)
