---
title: Comece - Construa sua primeira visão geral do aplicativo e pré-requisitos
author: girliemac
description: Aprenda a começar com Microsoft Teams desenvolvimento de aplicativos e configure seu ambiente.
ms.author: timura
ms.date: 03/18/2021
ms.topic: quickstart
ms.openlocfilehash: dae942be9383ef1e0a931d238e6148651f334ef5
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565876"
---
# <a name="get-started-with-microsoft-teams-app-development"></a><span data-ttu-id="8b311-103">Comece com o desenvolvimento de aplicativos Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8b311-103">Get started with Microsoft Teams app development</span></span>

<span data-ttu-id="8b311-104">Construa um aplicativo simples para aprender o básico do desenvolvimento de aplicativos Teams.</span><span class="sxs-lookup"><span data-stu-id="8b311-104">Build a simple app to learn the basics of Teams app development.</span></span> <span data-ttu-id="8b311-105">Uma vez que você vê "Olá, Mundo!", experimente qualquer um dos outros artigos para obter mais informações sobre ferramentas comuns, conceitos fundamentais e recursos avançados.</span><span class="sxs-lookup"><span data-stu-id="8b311-105">Once you see "Hello, World!", try any of the other get started articles for more information on common tools, fundamental concepts, and advanced features.</span></span>



## <a name="what-youll-learn"></a><span data-ttu-id="8b311-106">O que você vai aprender</span><span class="sxs-lookup"><span data-stu-id="8b311-106">What you'll learn</span></span>

* <span data-ttu-id="8b311-107">Levante-se e concorram rapidamente com o Teams Toolkit, uma extensão Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8b311-107">Get up and running quickly with the Teams Toolkit, a Visual Studio Code extension.</span></span> 
* <span data-ttu-id="8b311-108">Configure seu aplicativo com App Studio.</span><span class="sxs-lookup"><span data-stu-id="8b311-108">Configure your app with App Studio.</span></span>
* <span data-ttu-id="8b311-109">Conheça Teams ferramentas de desenvolvedores e SDKs.</span><span class="sxs-lookup"><span data-stu-id="8b311-109">Get familiar with Teams developer tools and SDKs.</span></span>
* <span data-ttu-id="8b311-110">Considere conceitos importantes de aplicativos Teams, como autenticação e design de práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="8b311-110">Consider important Teams app concepts, such as authentication and design best practices.</span></span>

<span data-ttu-id="8b311-111">Você pode criar um aplicativo Teams usando qualquer tecnologia de sua escolha, por exemplo, interface de linha de comando (CLI).</span><span class="sxs-lookup"><span data-stu-id="8b311-111">You can build a Teams app using any technology of your choice, for example, command-line interface (CLI).</span></span> <span data-ttu-id="8b311-112">Mas, esses artigos ajudam você a começar com as seguintes ferramentas e tecnologias recomendadas:</span><span class="sxs-lookup"><span data-stu-id="8b311-112">But, these articles help you get started with the following recommended tools and technologies:</span></span>

* <span data-ttu-id="8b311-113">Teams Toolkit, uma extensão Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8b311-113">Teams Toolkit, a Visual Studio Code extension</span></span>
* <span data-ttu-id="8b311-114">React.js para guias</span><span class="sxs-lookup"><span data-stu-id="8b311-114">React.js for tabs</span></span>
* <span data-ttu-id="8b311-115">Node.js para bots e extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8b311-115">Node.js for bots and messaging extensions</span></span>


## <a name="teams-app-fundamentals"></a><span data-ttu-id="8b311-116">Teams fundamentos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="8b311-116">Teams app fundamentals</span></span>

<span data-ttu-id="8b311-117">Você pode criar aplicativos personalizados Teams para você, pessoas em sua organização ou pessoas em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="8b311-117">You can build custom Teams apps for yourself, people in your org, or people all over the world.</span></span> <span data-ttu-id="8b311-118">Antes de começar, você deve entender os seguintes conceitos fundamentais sobre Teams desenvolvimento de aplicativos:</span><span class="sxs-lookup"><span data-stu-id="8b311-118">Before you begin, you should understand the following fundamental concepts about Teams app development:</span></span>

### <a name="common-app-use-cases"></a><span data-ttu-id="8b311-119">Casos comuns de uso de aplicativos</span><span class="sxs-lookup"><span data-stu-id="8b311-119">Common app use cases</span></span>

<span data-ttu-id="8b311-120">Alguns cenários típicos que um aplicativo de Teams personalizado pode ajudar são:</span><span class="sxs-lookup"><span data-stu-id="8b311-120">Some typical scenarios that a custom Teams app can help with are:</span></span>

* <span data-ttu-id="8b311-121">Incorpore conteúdo baseado na Web, como um aplicativo web ou parte de um site, no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="8b311-121">Embed web-based content, such as a web app or part of a website, in the Teams client.</span></span>
* <span data-ttu-id="8b311-122">Procure informações rapidamente em outro sistema e adicione-as a uma conversa Teams.</span><span class="sxs-lookup"><span data-stu-id="8b311-122">Look up information quickly in another system and adding it to a Teams conversation.</span></span>
* <span data-ttu-id="8b311-123">Acione fluxos de trabalho e processos diretamente do que é dito em uma conversa.</span><span class="sxs-lookup"><span data-stu-id="8b311-123">Trigger workflows and processes directly from what's said in a conversation.</span></span>

### <a name="app-capabilities-and-tools"></a><span data-ttu-id="8b311-124">Recursos e ferramentas do aplicativo</span><span class="sxs-lookup"><span data-stu-id="8b311-124">App capabilities and tools</span></span>

<span data-ttu-id="8b311-125">Um aplicativo é composto por um ou mais Teams recursos e pontos de interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="8b311-125">An app is made up of one or more Teams capabilities and user interaction points.</span></span> <span data-ttu-id="8b311-126">Seu lado de ferramentas de desenvolvimento vai variar dependendo dos recursos que você deseja.</span><span class="sxs-lookup"><span data-stu-id="8b311-126">Your development toolset will vary depending on the capabilities you want.</span></span>

| <span data-ttu-id="8b311-127">**Recursos do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="8b311-127">**App capabilities**</span></span>| <span data-ttu-id="8b311-128">**Pontos de interação**</span><span class="sxs-lookup"><span data-stu-id="8b311-128">**Interaction points**</span></span> | <span data-ttu-id="8b311-129">**Ferramentas recomendadas**</span><span class="sxs-lookup"><span data-stu-id="8b311-129">**Recommended tools**</span></span> | <span data-ttu-id="8b311-130">**SDKs**</span><span class="sxs-lookup"><span data-stu-id="8b311-130">**SDKs**</span></span> | <span data-ttu-id="8b311-131">**Pilhas de tecnologia**</span><span class="sxs-lookup"><span data-stu-id="8b311-131">**Technology stacks**</span></span> |
|--------|--------|--------|--------|--------|
| <span data-ttu-id="8b311-132">Guias</span><span class="sxs-lookup"><span data-stu-id="8b311-132">Tabs</span></span> | <span data-ttu-id="8b311-133">Espaços onde os usuários podem interagir com conteúdo da Web incorporado em contextos pessoais e compartilhados.</span><span class="sxs-lookup"><span data-stu-id="8b311-133">Spaces where users can interact with embedded web content in personal and shared contexts.</span></span> | <span data-ttu-id="8b311-134">VS Code com extensão Teams Toolkit ou Gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="8b311-134">VS Code with Teams Toolkit extension or Yeoman Generator</span></span> | <span data-ttu-id="8b311-135">SDK do cliente JavaScript do Teams</span><span class="sxs-lookup"><span data-stu-id="8b311-135">Teams JavaScript client SDK</span></span> | <span data-ttu-id="8b311-136">Tecnologias web gerais (HTML, CSS e JavaScript) ou React.js</span><span class="sxs-lookup"><span data-stu-id="8b311-136">General web technologies (HTML, CSS, and JavaScript) or React.js</span></span> |
| <span data-ttu-id="8b311-137">Bots</span><span class="sxs-lookup"><span data-stu-id="8b311-137">Bots</span></span> | <span data-ttu-id="8b311-138">Chatbots que interagem com os usuários em contextos pessoais e compartilhados.</span><span class="sxs-lookup"><span data-stu-id="8b311-138">Chatbots that interact with users in personal and shared contexts.</span></span> | <span data-ttu-id="8b311-139">VS Code com extensão Teams Toolkit ou Gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="8b311-139">VS Code with Teams Toolkit extension or Yeoman Generator</span></span> | <span data-ttu-id="8b311-140">Quadro de bot SDK</span><span class="sxs-lookup"><span data-stu-id="8b311-140">Bot Framework SDK</span></span> | <span data-ttu-id="8b311-141">Node.js, C#ou Python</span><span class="sxs-lookup"><span data-stu-id="8b311-141">Node.js, C#, or Python</span></span> | 
| <span data-ttu-id="8b311-142">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8b311-142">Messaging extensions</span></span> | <span data-ttu-id="8b311-143">Atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem navegar longe da conversa.</span><span class="sxs-lookup"><span data-stu-id="8b311-143">Shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span> | <span data-ttu-id="8b311-144">VS Code com extensão Teams Toolkit ou Gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="8b311-144">VS Code with Teams Toolkit extension or Yeoman Generator</span></span> | <span data-ttu-id="8b311-145">Quadro de bot SDK</span><span class="sxs-lookup"><span data-stu-id="8b311-145">Bot Framework SDK</span></span> | <span data-ttu-id="8b311-146">Node.js, C#ou Python</span><span class="sxs-lookup"><span data-stu-id="8b311-146">Node.js, C#, or Python</span></span> |

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="8b311-147">Teams não hospeda seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="8b311-147">Teams doesn't host your app</span></span>

<span data-ttu-id="8b311-148">Quando um usuário instala seu aplicativo em Teams, ele só instala um pacote de aplicativo que contém um arquivo de configuração (também conhecido como manifesto de aplicativo) e os ícones do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b311-148">When a user installs your app in Teams, they only install an app package that contains a configuration file (also known as an app manifest) and your app’s icons.</span></span> <span data-ttu-id="8b311-149">A lógica e o armazenamento de dados do seu aplicativo estão hospedados em outros lugares, como o Azure Web Services ou o localhost durante o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8b311-149">Your app’s logic and data storage are hosted elsewhere, such as Azure Web Services or localhost during development.</span></span> <span data-ttu-id="8b311-150">Teams acessa esses recursos via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8b311-150">Teams accesses these resources via HTTPS.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-in-cloud.png" alt-text="Ilustração mostrando seu aplicativo em Teams está apontando para a lógica do aplicativo no servidor em nuvem.":::

## <a name="next-step"></a><span data-ttu-id="8b311-152">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="8b311-152">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8b311-153">Construa e execute seu primeiro aplicativo de Teams</span><span class="sxs-lookup"><span data-stu-id="8b311-153">Build and run your first Teams app</span></span>](../build-your-first-app/build-and-run.md)
