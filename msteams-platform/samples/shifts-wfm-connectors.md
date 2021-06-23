---
title: Conectores de Turnos prontos para produção
description: Conectores de turnos de gerenciamento de força de trabalho para Teams
ms.topic: reference
author: surbhigupta
ms.date: 03/09/2020
localization_priority: Normal
keywords: Microsoft Teams conectores kronos
ms.author: lajanuar
ms.openlocfilehash: 088c049342c36b4f126b4a9d2f788601378b7db4
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069142"
---
# <a name="production-ready-shifts-connectors"></a><span data-ttu-id="3fcd3-104">Conectores de Turnos prontos para produção</span><span class="sxs-lookup"><span data-stu-id="3fcd3-104">Production-ready Shifts Connectors</span></span>  

<span data-ttu-id="3fcd3-105">Teams Os conectores de gerenciamento de força de trabalho (WFM) são integrações prontas para produção, de código aberto e orientadas pela comunidade, úteis para os funcionários de primeira linha.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-105">Teams Shifts Workforce management (WFM) connectors are production-ready, open-source, and community-driven integrations, useful for firstline workers.</span></span> <span data-ttu-id="3fcd3-106">Eles oferecem uma experiência perfeita e um processo rápido para a transformação digital de trabalhadores de primeira linha com Teams Turnos.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-106">They offer a seamless experience and quick process for the digital transformation of firstline workers with Teams Shifts.</span></span> 

<span data-ttu-id="3fcd3-107">Cada conector fornece orientações detalhadas para implantação e integração à sua organização.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-107">Each connector provides detailed guidance for deployment and integration to your organization.</span></span> <span data-ttu-id="3fcd3-108">O código-fonte completo está disponível GitHub repositório.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-108">The complete source code is available in GitHub repository.</span></span> <span data-ttu-id="3fcd3-109">Você pode explorar em detalhes ou bifurcação e personalizar para atender às suas necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-109">You can explore in detail or fork, and customize to meet your specific needs.</span></span>   

<span data-ttu-id="3fcd3-110">Este documento fornece uma visão geral dos principais benefícios dos conectores WFM do Teams Shifts, do conector De Turnos de Kronos para Teams e do conector de Turnos do JDA para Teams Shifts.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-110">This document gives an overview of key benefits of Teams Shifts WFM connectors, Kronos-to-Teams Shifts connector, and JDA-to-Teams Shifts connector.</span></span>

## <a name="key-benefits-of-teams-shifts-wfm-connectors"></a><span data-ttu-id="3fcd3-111">Principais benefícios dos conectores WFM Teams Shifts</span><span class="sxs-lookup"><span data-stu-id="3fcd3-111">Key benefits of Teams Shifts WFM connectors</span></span>

<span data-ttu-id="3fcd3-112">A seguir estão os principais benefícios Teams conectores WFM shifts:</span><span class="sxs-lookup"><span data-stu-id="3fcd3-112">Following are the key benefits of Teams Shifts WFM connectors:</span></span>

* <span data-ttu-id="3fcd3-113">**Experiência de plug and play:** Todos os conectores WFM shifts incluem ARM scripts de implantação do Azure que permitem hospedar todos os serviços necessários no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-113">**Plug and play experience:** All Shifts WFM connectors include ARM Azure deployment scripts that allow you to host all necessary services in Microsoft Azure.</span></span> <span data-ttu-id="3fcd3-114">Nenhuma codificação é necessária para implantar os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-114">No coding is required to deploy the apps.</span></span>

* <span data-ttu-id="3fcd3-115">**Código pronto para produção:** Todos os conectores shifts estão em conformidade com as práticas recomendadas de segurança e infraestrutura e todas as alterações enviadas à comunidade são revisadas para garantir a conformidade contínua.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-115">**Production-ready code:** All  Shifts connectors conform to the recommended security and infrastructure best practices and all community-submitted changes are reviewed to ensure continued conformance.</span></span>

* <span data-ttu-id="3fcd3-116">**Personalizável e extensível:**   Enquanto todos os conectores WFM shifts estão prontos para implantação para uso imediato, com toda a base de códigos e scripts de implantação prontamente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-116">**Customizable and extensible:**  While all Shifts WFM connectors are ready to deploy for immediate use, with the entire code base and deployment scripts readily available.</span></span> <span data-ttu-id="3fcd3-117">Você pode personalizá-los ou estendá-los facilmente para se ajustar às suas necessidades exclusivas.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-117">You can easily customize or extend them to fit your unique needs.</span></span>

* <span data-ttu-id="3fcd3-118">**Documentação detalhada & suporte:**   Todos os conectores WFM shifts são acompanhados por documentação de ponta a ponta para as etapas de arquitetura, implantação e configuração da solução.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-118">**Detailed documentation & support:**  All Shifts WFM connectors are accompanied by end-to-end documentation for solution architecture, deployment, and configuration steps.</span></span> <span data-ttu-id="3fcd3-119">Os repositórios do conector são monitorados, para que você possa relatar quaisquer problemas, desafios ou dificuldades encontrados por meio do rastreador de GitHub Problemas do repositório.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-119">The connector repositories are monitored, so that you can report any issues, challenges or difficulties you encounter through the repo's GitHub Issues tracker.</span></span>

* <span data-ttu-id="3fcd3-120">**Integração perfeita:** A integração entre soluções WFM e turnos Teams permite que os funcionários de primeira linha usem o aplicativo shifts do Teams para exibir ou gerenciar seus horários e horários de turno e usar todos os outros recursos avançados de colaboração fornecidos no Teams desde seu dispositivo móvel ou desktop sem precisar alternar o contexto para outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-120">**Seamless integration:** The integration between WFM solutions and Teams Shifts allows firstline workers to use the Teams Shifts app to view or manage their schedules and shift times, and use all the other rich collaboration features provided in Teams right from their mobile device or desktop without having to switch context to another app.</span></span>  

<span data-ttu-id="3fcd3-121">**Exibição de turnos abertos Teams**</span><span class="sxs-lookup"><span data-stu-id="3fcd3-121">**Open shifts view in Teams**</span></span> 

<span data-ttu-id="3fcd3-122">A exibição de turnos no Teams é mostrada na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="3fcd3-122">The shifts view in Teams is shown in the following image:</span></span> 

![Abrir turnos em Teams](../assets/images/teams-open-shifts-view.png)

## <a name="kronos-to-teams-shifts-connector"></a><span data-ttu-id="3fcd3-124">Conector kronos-to-Teams shifts</span><span class="sxs-lookup"><span data-stu-id="3fcd3-124">Kronos-to-Teams Shifts connector</span></span>

<span data-ttu-id="3fcd3-125">Com código de código aberto, você pode integrar a Central de Força de Trabalho kronos versão 8.1 e acima, com turnos do Teams, como, aplicativo de Teams desktop ou móvel para os seguintes cenários de gerente e trabalho de primeira linha:</span><span class="sxs-lookup"><span data-stu-id="3fcd3-125">With open-source code, you can integrate Kronos Workforce Central Version 8.1 and above, with Teams Shifts such as, desktop or mobile Teams app for the following firstline worker and manager scenarios:</span></span>

* <span data-ttu-id="3fcd3-126">Exibir agendamento.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-126">View schedule.</span></span>

* <span data-ttu-id="3fcd3-127">Publicar e solicitar turnos abertos.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-127">Publish and request open shifts.</span></span>

* <span data-ttu-id="3fcd3-128">Troca de turnos.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-128">Swap shifts.</span></span>

* <span data-ttu-id="3fcd3-129">Solicitar tempo de folga.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-129">Request time off.</span></span>

* <span data-ttu-id="3fcd3-130">Ofereça turnos.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-130">Offer shifts.</span></span>

<span data-ttu-id="3fcd3-131">Para obter mais informações sobre a implantação do conector De turnos Teams Kronos-to-Teams, consulte [Get it on GitHub](https://aka.ms/KronosShiftsConnector).</span><span class="sxs-lookup"><span data-stu-id="3fcd3-131">For more information on deployment of Kronos-to-Teams Shifts connector, see [Get it on GitHub](https://aka.ms/KronosShiftsConnector).</span></span>

## <a name="jda-to-teams-shifts-connector"></a><span data-ttu-id="3fcd3-132">Conector de turnos do JDA para Teams de turnos</span><span class="sxs-lookup"><span data-stu-id="3fcd3-132">JDA-to-Teams Shifts connector</span></span>

<span data-ttu-id="3fcd3-133">Com código de código aberto, você pode integrar o JDA, como BlueYonder Versão 17.2 e acima, com turnos do Teams, como, aplicativo de Teams desktop ou móvel para os seguintes cenários de gerente e trabalho de primeira linha:</span><span class="sxs-lookup"><span data-stu-id="3fcd3-133">With open-source code, you can integrate JDA, such as BlueYonder Version 17.2 and above, with Teams Shifts  such as, desktop or mobile Teams app for the following firstline worker and manager scenarios:</span></span>

* <span data-ttu-id="3fcd3-134">Publicar turnos e agendar grupos no JDA e exibi-los Teams.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-134">Publish shifts and schedule groups in JDA and view them in Teams.</span></span>

* <span data-ttu-id="3fcd3-135">Habilita cenários de agendamento ricos, incluindo solicitação de trocas de turno e tempo de folga.</span><span class="sxs-lookup"><span data-stu-id="3fcd3-135">Enable rich scheduling scenarios, including requesting shift swaps and time off.</span></span>

* <span data-ttu-id="3fcd3-136">Definir a disponibilidade do usuário usando a [API Graph Microsoft para Turnos.](/graph/api/resources/shift?view=graph-rest-beta&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="3fcd3-136">Set user availability using the [Microsoft Graph API for Shifts](/graph/api/resources/shift?view=graph-rest-beta&preserve-view=true).</span></span>

<span data-ttu-id="3fcd3-137">Para obter mais informações sobre contribuição e sugestão, consulte [Get it on GitHub](https://aka.ms/JDAShiftsConnector).</span><span class="sxs-lookup"><span data-stu-id="3fcd3-137">For more information on contribution and suggestion, see [Get it on GitHub](https://aka.ms/JDAShiftsConnector).</span></span></br></br>

## <a name="see-also"></a><span data-ttu-id="3fcd3-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="3fcd3-138">See also</span></span>

[<span data-ttu-id="3fcd3-139">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="3fcd3-139">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
