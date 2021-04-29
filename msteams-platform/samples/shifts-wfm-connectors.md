---
title: Conectores de Turnos prontos para produção
description: Conectores de turnos de gerenciamento de força de trabalho para o Teams
ms.topic: reference
author: laujan
ms.date: 03/09/2020
localization_priority: Normal
keywords: Kronos dos conectores do Microsoft Teams
ms.author: lajanuar
ms.openlocfilehash: 459797dd3f8425223c0dcbedc335955bf106ae37
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075735"
---
# <a name="production-ready-shifts-connectors"></a><span data-ttu-id="b221f-104">Conectores de Turnos prontos para produção</span><span class="sxs-lookup"><span data-stu-id="b221f-104">Production-ready Shifts Connectors</span></span>  

<span data-ttu-id="b221f-105">Os conectores de gerenciamento de força de trabalho do Teams Shifts (WFM) são integrações prontas para produção, de código aberto e orientadas pela comunidade, úteis para os funcionários de primeira linha.</span><span class="sxs-lookup"><span data-stu-id="b221f-105">Teams Shifts Workforce management (WFM) connectors are production-ready, open-source, and community-driven integrations, useful for firstline workers.</span></span> <span data-ttu-id="b221f-106">Eles oferecem uma experiência perfeita e um processo rápido para a transformação digital de funcionários de primeira linha com Turnos do Teams.</span><span class="sxs-lookup"><span data-stu-id="b221f-106">They offer a seamless experience and quick process for the digital transformation of firstline workers with Teams Shifts.</span></span> 

<span data-ttu-id="b221f-107">Cada conector fornece orientações detalhadas para implantação e integração à sua organização.</span><span class="sxs-lookup"><span data-stu-id="b221f-107">Each connector provides detailed guidance for deployment and integration to your organization.</span></span> <span data-ttu-id="b221f-108">O código-fonte completo está disponível no repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="b221f-108">The complete source code is available in GitHub repository.</span></span> <span data-ttu-id="b221f-109">Você pode explorar em detalhes ou bifurcação e personalizar para atender às suas necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="b221f-109">You can explore in detail or fork, and customize to meet your specific needs.</span></span>   

<span data-ttu-id="b221f-110">Este documento fornece uma visão geral dos principais benefícios dos conectores WFM do Teams Shifts, do conector de Turnos do Kronos para o Teams e do conector de turnos JDA-para-Teams.</span><span class="sxs-lookup"><span data-stu-id="b221f-110">This document gives an overview of key benefits of Teams Shifts WFM connectors, Kronos-to-Teams Shifts connector, and JDA-to-Teams Shifts connector.</span></span>

## <a name="key-benefits-of-teams-shifts-wfm-connectors"></a><span data-ttu-id="b221f-111">Principais benefícios dos conectores WFM do Teams Shifts</span><span class="sxs-lookup"><span data-stu-id="b221f-111">Key benefits of Teams Shifts WFM connectors</span></span>

<span data-ttu-id="b221f-112">A seguir estão os principais benefícios dos conectores WFM do Teams Shifts:</span><span class="sxs-lookup"><span data-stu-id="b221f-112">Following are the key benefits of Teams Shifts WFM connectors:</span></span>

* <span data-ttu-id="b221f-113">**Experiência de plug and play:** Todos os conectores WFM shifts incluem ARM scripts de implantação do Azure que permitem hospedar todos os serviços necessários no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="b221f-113">**Plug and play experience:** All Shifts WFM connectors include ARM Azure deployment scripts that allow you to host all necessary services in Microsoft Azure.</span></span> <span data-ttu-id="b221f-114">Nenhuma codificação é necessária para implantar os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b221f-114">No coding is required to deploy the apps.</span></span>

* <span data-ttu-id="b221f-115">**Código pronto para produção:** Todos os conectores shifts estão em conformidade com as práticas recomendadas de segurança e infraestrutura e todas as alterações enviadas à comunidade são revisadas para garantir a conformidade contínua.</span><span class="sxs-lookup"><span data-stu-id="b221f-115">**Production-ready code:** All  Shifts connectors conform to the recommended security and infrastructure best practices and all community-submitted changes are reviewed to ensure continued conformance.</span></span>

* <span data-ttu-id="b221f-116">**Personalizável e extensível:**   Enquanto todos os conectores WFM shifts estão prontos para implantação para uso imediato, com toda a base de códigos e scripts de implantação prontamente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b221f-116">**Customizable and extensible:**  While all Shifts WFM connectors are ready to deploy for immediate use, with the entire code base and deployment scripts readily available.</span></span> <span data-ttu-id="b221f-117">Você pode personalizá-los ou estendá-los facilmente para se ajustar às suas necessidades exclusivas.</span><span class="sxs-lookup"><span data-stu-id="b221f-117">You can easily customize or extend them to fit your unique needs.</span></span>

* <span data-ttu-id="b221f-118">**Documentação detalhada & suporte:**   Todos os conectores WFM shifts são acompanhados por documentação de ponta a ponta para as etapas de arquitetura, implantação e configuração da solução.</span><span class="sxs-lookup"><span data-stu-id="b221f-118">**Detailed documentation & support:**  All Shifts WFM connectors are accompanied by end-to-end documentation for solution architecture, deployment, and configuration steps.</span></span> <span data-ttu-id="b221f-119">Os repositórios do conector são monitorados, para que você possa relatar quaisquer problemas, desafios ou dificuldades encontrados por meio do rastreador de Problemas do GitHub do repositório.</span><span class="sxs-lookup"><span data-stu-id="b221f-119">The connector repositories are monitored, so that you can report any issues, challenges or difficulties you encounter through the repo's GitHub Issues tracker.</span></span>

* <span data-ttu-id="b221f-120">**Integração perfeita:** A integração entre soluções WFM e Turnos do Teams permite que os funcionários de primeira linha usem o aplicativo Turnos do Teams para exibir ou gerenciar seus horários de turno e agendamento e usar todos os outros recursos avançados de colaboração fornecidos no Teams desde seu dispositivo móvel ou área de trabalho sem precisar alternar o contexto para outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b221f-120">**Seamless integration:** The integration between WFM solutions and Teams Shifts allows firstline workers to use the Teams Shifts app to view or manage their schedules and shift times, and use all the other rich collaboration features provided in Teams right from their mobile device or desktop without having to switch context to another app.</span></span>  

<span data-ttu-id="b221f-121">**Exibição de turnos abertos no Teams**</span><span class="sxs-lookup"><span data-stu-id="b221f-121">**Open shifts view in Teams**</span></span> 

<span data-ttu-id="b221f-122">A exibição de turnos no Teams é mostrada na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="b221f-122">The shifts view in Teams is shown in the following image:</span></span> 

![Abrir turnos no Teams](../assets/images/teams-open-shifts-view.png)

## <a name="kronos-to-teams-shifts-connector"></a><span data-ttu-id="b221f-124">Conector de turnos de Kronos para Teams</span><span class="sxs-lookup"><span data-stu-id="b221f-124">Kronos-to-Teams Shifts connector</span></span>

<span data-ttu-id="b221f-125">Com código de código aberto, você pode integrar a Central de Força de Trabalho kronos versão 8.1 e acima, com turnos do Teams, como, aplicativo do Teams desktop ou móvel para os seguintes cenários de funcionários e gerentes de linha de base:</span><span class="sxs-lookup"><span data-stu-id="b221f-125">With open-source code, you can integrate Kronos Workforce Central Version 8.1 and above, with Teams Shifts such as, desktop or mobile Teams app for the following firstline worker and manager scenarios:</span></span>

* <span data-ttu-id="b221f-126">Exibir agendamento.</span><span class="sxs-lookup"><span data-stu-id="b221f-126">View schedule.</span></span>

* <span data-ttu-id="b221f-127">Publicar e solicitar turnos abertos.</span><span class="sxs-lookup"><span data-stu-id="b221f-127">Publish and request open shifts.</span></span>

* <span data-ttu-id="b221f-128">Troca de turnos.</span><span class="sxs-lookup"><span data-stu-id="b221f-128">Swap shifts.</span></span>

* <span data-ttu-id="b221f-129">Solicitar tempo de folga.</span><span class="sxs-lookup"><span data-stu-id="b221f-129">Request time off.</span></span>

* <span data-ttu-id="b221f-130">Ofereça turnos.</span><span class="sxs-lookup"><span data-stu-id="b221f-130">Offer shifts.</span></span>

<span data-ttu-id="b221f-131">Para obter mais informações sobre a implantação do conector de turnos do Kronos-to-Teams, consulte [Get it on GitHub](https://aka.ms/KronosShiftsConnector).</span><span class="sxs-lookup"><span data-stu-id="b221f-131">For more information on deployment of Kronos-to-Teams Shifts connector, see [Get it on GitHub](https://aka.ms/KronosShiftsConnector).</span></span>

## <a name="jda-to-teams-shifts-connector"></a><span data-ttu-id="b221f-132">Conector de turnos JDA para Teams</span><span class="sxs-lookup"><span data-stu-id="b221f-132">JDA-to-Teams Shifts connector</span></span>

<span data-ttu-id="b221f-133">Com código de código aberto, você pode integrar o JDA, como BlueYonder Versão 17.2 e acima, com Turnos do Teams, como aplicativo do Teams para área de trabalho ou móvel do Teams, para os seguintes cenários de gerente e trabalho de primeira linha:</span><span class="sxs-lookup"><span data-stu-id="b221f-133">With open-source code, you can integrate JDA, such as BlueYonder Version 17.2 and above, with Teams Shifts  such as, desktop or mobile Teams app for the following firstline worker and manager scenarios:</span></span>

* <span data-ttu-id="b221f-134">Publicar turnos e agendar grupos no JDA e exibi-los no Teams.</span><span class="sxs-lookup"><span data-stu-id="b221f-134">Publish shifts and schedule groups in JDA and view them in Teams.</span></span>

* <span data-ttu-id="b221f-135">Habilita cenários de agendamento ricos, incluindo solicitação de trocas de turno e tempo de folga.</span><span class="sxs-lookup"><span data-stu-id="b221f-135">Enable rich scheduling scenarios, including requesting shift swaps and time off.</span></span>

* <span data-ttu-id="b221f-136">Definir a disponibilidade do usuário usando a [API do Microsoft Graph para Turnos.](/graph/api/resources/shift?view=graph-rest-beta&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="b221f-136">Set user availability using the [Microsoft Graph API for Shifts](/graph/api/resources/shift?view=graph-rest-beta&preserve-view=true).</span></span>

<span data-ttu-id="b221f-137">Para obter mais informações sobre contribuição e sugestão, consulte [Get it on GitHub](https://aka.ms/JDAShiftsConnector).</span><span class="sxs-lookup"><span data-stu-id="b221f-137">For more information on contribution and suggestion, see [Get it on GitHub](https://aka.ms/JDAShiftsConnector).</span></span></br></br>

## <a name="see-also"></a><span data-ttu-id="b221f-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="b221f-138">See also</span></span>

[<span data-ttu-id="b221f-139">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="b221f-139">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
