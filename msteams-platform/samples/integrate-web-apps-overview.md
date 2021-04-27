---
title: Integrar aplicativos Web
author: Rajeshwari-v
description: Uma visão geral da integração de aplicativos Web e recursos de dispositivo com o aplicativo Microsoft Teams.
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 6493f493b2bfc67a23aebfb5142aff60cf0afe93
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020236"
---
# <a name="integrate-web-apps"></a><span data-ttu-id="34a86-103">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="34a86-103">Integrate web apps</span></span>

<span data-ttu-id="34a86-104">Você pode fornecer uma experiência de usuário enriquecida integrando os recursos de um aplicativo Web existente na plataforma do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-104">You can provide an enriched user experience by integrating the features of an existing web application into Microsoft Teams platform.</span></span> <span data-ttu-id="34a86-105">Certifique-se de [seguir as diretrizes de design do Teams](~/concepts/design/understand-use-cases.md) para tornar seu aplicativo nativo ao Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-105">Ensure to follow [Teams design guidelines](~/concepts/design/understand-use-cases.md) to make your app native to Teams.</span></span>
<span data-ttu-id="34a86-106">Este documento fornece uma visão geral dos pré-requisitos para integrar aplicativos Web com o Teams, plataforma Power para criar aplicativos do Power, Agentes Virtuais do Power, Assistente Virtual, modelos de aplicativo, conectores de turno, LMS Moodle, criação de um botão Share-to-Teams para seu site, a adição de uma guia do Microsoft Teams no SharePoint, a criação de links profundos e a integração de recursos do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="34a86-106">This document gives an overview of prerequisites to integrate web applications with Teams, Power platform to create Power apps, Power Virtual Agents, Virtual Assistant, app templates, Shift connectors, Moodle LMS, creating a Share-to-Teams button for your website, adding a Microsoft Teams tab in SharePoint, creating deep links, and integrating device capabilities.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="34a86-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="34a86-107">Prerequisites</span></span>   

<span data-ttu-id="34a86-108">Para uma integração eficaz, certifique-se de ter uma melhor compreensão dos seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="34a86-108">For effective integration, ensure to have a better understanding of the following prerequisites:</span></span>
* <span data-ttu-id="34a86-109">Recursos do Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-109">Teams capabilities.</span></span> 
* <span data-ttu-id="34a86-110">Requisitos do SharePoint para armazenamento de arquivos e dados.</span><span class="sxs-lookup"><span data-stu-id="34a86-110">SharePoint requirements for file and data storage.</span></span>
* <span data-ttu-id="34a86-111">Requisitos de API.</span><span class="sxs-lookup"><span data-stu-id="34a86-111">API requirements.</span></span>
* <span data-ttu-id="34a86-112">Autenticação.</span><span class="sxs-lookup"><span data-stu-id="34a86-112">Authentication.</span></span>
* <span data-ttu-id="34a86-113">Vinculação profunda do seu aplicativo com o Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-113">Deep linking of your app with Teams.</span></span>
* <span data-ttu-id="34a86-114">Mapeie os casos de uso do aplicativo para os recursos da plataforma teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-114">Map your app's use cases to Teams platform capabilities.</span></span>
* <span data-ttu-id="34a86-115">Determine os pontos de entrada do aplicativo, como uso pessoal, colaboração ou ambos.</span><span class="sxs-lookup"><span data-stu-id="34a86-115">Determine your app's entry points, such as personal use, collaboration, or both.</span></span>

## <a name="low-code-platforms"></a><span data-ttu-id="34a86-116">Plataformas de código baixo</span><span class="sxs-lookup"><span data-stu-id="34a86-116">Low code platforms</span></span>

<span data-ttu-id="34a86-117">As plataformas de código baixo fornecem uma abordagem intuitiva para o desenvolvimento de software e exigem pouca ou nenhuma codificação para criar aplicativos e processos.</span><span class="sxs-lookup"><span data-stu-id="34a86-117">Low code platforms provide an intuitive approach to software development and require little or no coding to build applications and processes.</span></span> <span data-ttu-id="34a86-118">Você pode criar aplicativos personalizados facilmente com plataformas de código baixo.</span><span class="sxs-lookup"><span data-stu-id="34a86-118">You can create custom apps easily with low code platforms.</span></span> <span data-ttu-id="34a86-119">Essas plataformas consistem em uma interface visual, conectores para serviços back-end e um sistema de gerenciamento de ciclo de vida de aplicativos integrado para criar, depurar, implantar e manter aplicativos.</span><span class="sxs-lookup"><span data-stu-id="34a86-119">These platforms consist of a visual interface, connectors to back end services, and a built-in app lifecycle management system to build, debug, deploy, and maintain applications.</span></span> <span data-ttu-id="34a86-120">A Microsoft fornece os seguintes gateways inovadores para criar rapidamente aplicativos compatíveis com o Teams usando atributos de código baixos:</span><span class="sxs-lookup"><span data-stu-id="34a86-120">Microsoft provides the following innovative gateways to rapidly build Teams-compatible apps using low code attributes:</span></span>
* <span data-ttu-id="34a86-121">Plataforma Microsoft Power</span><span class="sxs-lookup"><span data-stu-id="34a86-121">Microsoft Power platform</span></span>
* <span data-ttu-id="34a86-122">Modelos de aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="34a86-122">Microsoft Teams app templates</span></span>

## <a name="microsoft-power-platform"></a><span data-ttu-id="34a86-123">Plataforma Microsoft Power</span><span class="sxs-lookup"><span data-stu-id="34a86-123">Microsoft Power platform</span></span>

<span data-ttu-id="34a86-124">A plataforma Microsoft Power combina quatro tecnologias robustas da Microsoft, como Power BI, Power Apps, Power Automate e Agentes Virtuais do Power em uma plataforma de aplicativo poderosa.</span><span class="sxs-lookup"><span data-stu-id="34a86-124">Microsoft Power platform combines four robust Microsoft technologies, such as Power BI, Power Apps, Power Automate, and Power Virtual Agents in one powerful application platform.</span></span> <span data-ttu-id="34a86-125">Essas tecnologias capacitam você a criar soluções, automatizar processos, analisar dados e criar agentes virtuais em um ambiente unificado e integrado.</span><span class="sxs-lookup"><span data-stu-id="34a86-125">These technologies empower you to build solutions, automate processes, analyze data, and create virtual agents within a unified and integrated environment.</span></span>

### <a name="power-apps"></a><span data-ttu-id="34a86-126">Power Apps</span><span class="sxs-lookup"><span data-stu-id="34a86-126">Power Apps</span></span>

<span data-ttu-id="34a86-127">Com o Power Apps, você pode criar aplicativos de negócios que se conectam aos dados da sua empresa e são adaptados às necessidades da sua organização.</span><span class="sxs-lookup"><span data-stu-id="34a86-127">With Power Apps, you can build business apps that connect to your business data and are tailored to your organization's needs.</span></span> <span data-ttu-id="34a86-128">Os Aplicativos Do Power permitem uma ampla variedade de cenários de aplicativos para resolver desafios de negócios por meio de aplicativos de tela.</span><span class="sxs-lookup"><span data-stu-id="34a86-128">Power Apps enable a wide range of app scenarios to solve business challenges through canvas apps.</span></span> <span data-ttu-id="34a86-129">Depois de criar o aplicativo, você pode exportá-lo do portal do criador do Power Apps e incorporar no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-129">After building the app, you can export it from the Power Apps maker portal and embed in Microsoft Teams.</span></span>

### <a name="power-virtual-agents"></a><span data-ttu-id="34a86-130">Agentes virtuais do Power</span><span class="sxs-lookup"><span data-stu-id="34a86-130">Power Virtual Agents</span></span>

<span data-ttu-id="34a86-131">O Power Virtual Agent é uma solução de interface gráfica sem código e guiada.</span><span class="sxs-lookup"><span data-stu-id="34a86-131">Power Virtual Agent is a no code, guided graphical interface solution.</span></span> <span data-ttu-id="34a86-132">Ele é criado na Plataforma do Microsoft Power e na Estrutura de Bots.</span><span class="sxs-lookup"><span data-stu-id="34a86-132">It is built on the Microsoft Power Platform and the Bot Framework.</span></span> <span data-ttu-id="34a86-133">Ele capacita todos os membros da sua equipe a criar e manter chatbots de conversação ricos que se integram facilmente à plataforma do Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-133">It empowers every member of your team to create and maintain rich conversational chatbots that easily integrate with the Teams platform.</span></span> <span data-ttu-id="34a86-134">Você pode projetar, desenvolver e publicar agentes virtuais inteligentes para o Teams sem precisar configurar um ambiente de desenvolvimento, criar um serviço Web ou se registrar diretamente com a Estrutura de Bots.</span><span class="sxs-lookup"><span data-stu-id="34a86-134">You can design, develop, and publish intelligent virtual agents for Teams without having to setup a development environment, create a web service, or directly register with the Bot Framework.</span></span>

### <a name="create-virtual-assistant"></a><span data-ttu-id="34a86-135">Criar Assistente Virtual</span><span class="sxs-lookup"><span data-stu-id="34a86-135">Create Virtual Assistant</span></span>

<span data-ttu-id="34a86-136">O Assistente Virtual é um modelo de código aberto da Microsoft que permite que você crie uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da identidade visual organizacional e dos dados necessários.</span><span class="sxs-lookup"><span data-stu-id="34a86-136">Virtual Assistant is a Microsoft open-source template that enables you to create a robust conversational solution while maintaining full control of user experience, organizational branding, and necessary data.</span></span> 

## <a name="app-templates"></a><span data-ttu-id="34a86-137">Modelos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="34a86-137">App templates</span></span>

<span data-ttu-id="34a86-138">Você pode usar o modelo de aplicativo para criar aplicativos personalizados feitos para atender às suas necessidades organizacionais.</span><span class="sxs-lookup"><span data-stu-id="34a86-138">You can use app template to create custom made apps to suit your organizational needs.</span></span> <span data-ttu-id="34a86-139">Esses são aplicativos prontos para produção para o Microsoft Teams que são orientados pela comunidade, de código aberto e disponíveis no GitHub.</span><span class="sxs-lookup"><span data-stu-id="34a86-139">These are production-ready apps for Microsoft Teams that are community driven, open-source, and available on GitHub.</span></span> <span data-ttu-id="34a86-140">Cada modelo contém instruções detalhadas para implantar e instalar o aplicativo para sua organização.</span><span class="sxs-lookup"><span data-stu-id="34a86-140">Each template contains detailed instructions to deploy and install the app for your organization.</span></span> <span data-ttu-id="34a86-141">Ele fornece um aplicativo pronto para uso que você pode instalar e começar a usar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="34a86-141">It provides a ready-to-use application that you can install and start using immediately.</span></span> 

## <a name="teams-shifts-work-force-management-connectors"></a><span data-ttu-id="34a86-142">Teams Shifts Work Force Management connectors</span><span class="sxs-lookup"><span data-stu-id="34a86-142">Teams Shifts Work Force Management connectors</span></span>

<span data-ttu-id="34a86-143">Os conectores de Gerenciamento de Força de Trabalho de Turnos do Teams são integrações prontas para produção, de código aberto e orientadas pela comunidade.</span><span class="sxs-lookup"><span data-stu-id="34a86-143">Teams Shifts Work Force Management connectors are production-ready, open-source, and community-driven integrations.</span></span> <span data-ttu-id="34a86-144">Eles oferecem uma experiência perfeita e um processo rápido para a transformação digital de funcionários de primeira linha com Turnos do Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-144">They offer a seamless experience and quick process for the digital transformation of firstline workers with Teams Shifts.</span></span>

## <a name="install-moodle-lms"></a><span data-ttu-id="34a86-145">Instalar o Moodle LMS</span><span class="sxs-lookup"><span data-stu-id="34a86-145">Install Moodle LMS</span></span>

<span data-ttu-id="34a86-146">Moodle é um LMS (Sistema de Gerenciamento de Aprendizagem) de código aberto popular.</span><span class="sxs-lookup"><span data-stu-id="34a86-146">Moodle is a popular open-source Learning Management System (LMS).</span></span> <span data-ttu-id="34a86-147">Agora, ele está integrado ao Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-147">It is now integrated with Microsoft Teams.</span></span> <span data-ttu-id="34a86-148">Essa integração ajuda educadores e professores a colaborarem em torno de cursos de miojo, fazer perguntas sobre notas e atribuições e manter-se atualizados com notificações diretamente no Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-148">This integration helps educators and teachers to collaborate around Moodle courses, ask questions about grades and assignments, and stay updated with notifications directly within Teams.</span></span>

## <a name="create-a-share-to-teams-button-for-your-website"></a><span data-ttu-id="34a86-149">Criar um botão Compartilhar no Teams para o seu site</span><span class="sxs-lookup"><span data-stu-id="34a86-149">Create a Share-to-Teams button for your website</span></span>

<span data-ttu-id="34a86-150">Sites de terceiros podem usar o script do launcher para incorporar os botões Compartilhar ao Teams em suas páginas da Web.</span><span class="sxs-lookup"><span data-stu-id="34a86-150">Third-party websites can use the launcher script to embed Share to Teams buttons on their webpages.</span></span> <span data-ttu-id="34a86-151">Quando você seleciona o botão, ele inicia a experiência Compartilhar para o Teams em uma janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="34a86-151">When you select the button, it launches the Share to Teams experience in a pop-up window.</span></span> <span data-ttu-id="34a86-152">Isso permite compartilhar um link diretamente com qualquer pessoa ou canal do Microsoft Teams sem alternar o contexto.</span><span class="sxs-lookup"><span data-stu-id="34a86-152">This allows you to share a link directly to any person or Microsoft Teams channel without switching context.</span></span>

## <a name="add-a-microsoft-teams-tab-in-sharepoint"></a><span data-ttu-id="34a86-153">Adicionar uma guia do Microsoft Teams no SharePoint</span><span class="sxs-lookup"><span data-stu-id="34a86-153">Add a Microsoft Teams tab in SharePoint</span></span>

<span data-ttu-id="34a86-154">Você pode obter uma experiência de integração rica entre o Microsoft Teams e o SharePoint adicionando uma guia do Microsoft Teams no SharePoint como uma Web Part SPFx.</span><span class="sxs-lookup"><span data-stu-id="34a86-154">You can get a rich integration experience between Microsoft Teams and SharePoint by adding a Microsoft Teams tab in SharePoint as an SPFx web part.</span></span> 

## <a name="create-deep-link"></a><span data-ttu-id="34a86-155">Criar link profundo</span><span class="sxs-lookup"><span data-stu-id="34a86-155">Create deep link</span></span>

<span data-ttu-id="34a86-156">Você pode criar links profundos para as entidades no Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-156">You can create deep links to the entities in Teams.</span></span> <span data-ttu-id="34a86-157">Você pode criar links para informações e recursos no Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-157">You can create links to information and features within Teams.</span></span> <span data-ttu-id="34a86-158">Esses links profundos navegam para conteúdo e informações em sua guia. Você pode usar links profundos para vincular seu aplicativo com o Teams à medida que eles vinculam várias partes de um aplicativo para uma experiência do Teams mais nativa.</span><span class="sxs-lookup"><span data-stu-id="34a86-158">These deep links navigate to content and information within your tab. You can use deep links to link your app with Teams as they tie together multiple pieces of an app for a more native Teams experience.</span></span>

## <a name="integrate-device-capabilities"></a><span data-ttu-id="34a86-159">Integrar recursos de dispositivo</span><span class="sxs-lookup"><span data-stu-id="34a86-159">Integrate device capabilities</span></span>

<span data-ttu-id="34a86-160">A plataforma do Microsoft Teams está aprimorando continuamente os recursos de desenvolvedor alinhando com experiências de primeira parte.</span><span class="sxs-lookup"><span data-stu-id="34a86-160">Microsoft Teams platform is continuously enhancing developer capabilities aligning with built-in first-party experiences.</span></span> <span data-ttu-id="34a86-161">A plataforma do Teams aprimorada permite que os parceiros acessem e integrem os recursos de dispositivo nativo, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e local usando APIs dedicadas disponíveis no SDK do cliente JavaScript do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="34a86-161">The enhanced Teams platform allows partners to access and integrate the native device capabilities, such as camera, QR or barcode scanner, photo gallery, microphone, and location using dedicated APIs available in Microsoft Teams JavaScript client SDK.</span></span> 

## <a name="see-also"></a><span data-ttu-id="34a86-162">Confira também</span><span class="sxs-lookup"><span data-stu-id="34a86-162">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-163">Mapear os casos de uso do aplicativo para os recursos da plataforma Teams</span><span class="sxs-lookup"><span data-stu-id="34a86-163">Map your app's use cases to Teams platform capabilities</span></span>](~/concepts/design/map-use-cases.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-164">Determinar os pontos de entrada do aplicativo</span><span class="sxs-lookup"><span data-stu-id="34a86-164">Determine your app's entry points</span></span>](~/concepts/extensibility-points.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-165">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="34a86-165">Integrate web apps</span></span>](~/samples/integrating-web-apps.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-166">Criar aplicativos personalizados de baixo código para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="34a86-166">Create low-code custom apps for Microsoft Teams</span></span>](~/samples/teams-low-code-solutions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-167">Adicionar um chatbot de agentes virtuais de energia</span><span class="sxs-lookup"><span data-stu-id="34a86-167">Add a Power Virtual Agents chatbot</span></span>](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-168">Criar assistente virtual</span><span class="sxs-lookup"><span data-stu-id="34a86-168">Create virtual assistant</span></span>](~/samples/virtual-assistant.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-169">Modelos de aplicativos para o Teams</span><span class="sxs-lookup"><span data-stu-id="34a86-169">App templates for Microsoft Teams</span></span>](~/samples/app-templates.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-170">Conectores de Turno prontos para produção</span><span class="sxs-lookup"><span data-stu-id="34a86-170">Production-ready Shift Connectors</span></span>](~/samples/shifts-wfm-connectors.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-171">Instalar o Moodle LMS</span><span class="sxs-lookup"><span data-stu-id="34a86-171">Install Moodle LMS</span></span>](~/resources/moodleinstructions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-172">Criar um botão compartilhar para o Teams</span><span class="sxs-lookup"><span data-stu-id="34a86-172">Create a Share-to-Teams button</span></span>](~/concepts/build-and-test/share-to-teams.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-173">Adicionar uma guia do Teams ao SharePoint</span><span class="sxs-lookup"><span data-stu-id="34a86-173">Add a Teams tab to SharePoint</span></span>](~/tabs/how-to/tabs-in-sharepoint.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-174">Criar links detalhados</span><span class="sxs-lookup"><span data-stu-id="34a86-174">Create deep links</span></span>](~/concepts/build-and-test/deep-links.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a86-175">Funcionalidades de dispositivo</span><span class="sxs-lookup"><span data-stu-id="34a86-175">Device capabilities</span></span>](~/concepts/device-capabilities/device-capabilities-overview.md)
