---
title: Criando seu primeiro aplicativo de equipe
author: heath-hamilton
description: Tutorial para criar um aplicativo do Microsoft Teams real
ms.openlocfilehash: 4915dde4ef5a852f4fc5d1e4c83e3349db2eaf6b
ms.sourcegitcommit: 80bf79a952bb14cbc38c0bd1e3cf8a346158e28e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2020
ms.locfileid: "46655671"
---
# <a name="learn-how-to-build-your-first-teams-app"></a><span data-ttu-id="61bbe-103">Saiba como criar seu primeiro aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="61bbe-103">Learn how to build your first Teams app</span></span>

<span data-ttu-id="61bbe-104">Em **compilar seu primeiro aplicativo**, você aprende como criar um aplicativo Basic Teams por meio de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="61bbe-104">In **Build your first app**, you learn how to create a basic Teams app through tutorials.</span></span> <span data-ttu-id="61bbe-105">As lições são criadas umas sobre as outras, orientando cada etapa de criação de um aplicativo simples e real de equipes do mundo.</span><span class="sxs-lookup"><span data-stu-id="61bbe-105">The lessons build on each other, walking you through each step of creating a simple, real-world Teams app.</span></span> <span data-ttu-id="61bbe-106">Apresentamos a você ferramentas comuns, conceitos fundamentais e links úteis ao longo do caminho.</span><span class="sxs-lookup"><span data-stu-id="61bbe-106">We introduce you to common tools, fundamental concepts, and useful links along the way.</span></span>

<span data-ttu-id="61bbe-107">Você começará a criar e executar um "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="61bbe-107">You'll start with creating and running a "Hello, World!"</span></span> <span data-ttu-id="61bbe-108">aplicativo de guia.</span><span class="sxs-lookup"><span data-stu-id="61bbe-108">tab app.</span></span> <span data-ttu-id="61bbe-109">Em seguida, você criará uma interface do usuário simples e aprenderá a obter um contexto útil com o SDK do JavaScript do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="61bbe-109">You'll then create some simple UI and learn how to get useful context with the Microsoft Teams Javascript SDK.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="61bbe-110">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="61bbe-110">What you'll learn</span></span>

> [!div class="checklist"]
  >
  > - <span data-ttu-id="61bbe-111">**Comece a trabalhar rapidamente com o Teams Toolkit**: o Microsoft Teams Toolkit para Visual Studio Code cuida da criação do seu projeto de aplicativo e do scaffolding, para que você possa ter um aplicativo em execução em minutos.</span><span class="sxs-lookup"><span data-stu-id="61bbe-111">**Get up and running quickly with the Teams Toolkit**: The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.</span></span>
  > - <span data-ttu-id="61bbe-112">**Defina seu aplicativo com o manifesto**: o manifesto é um plano gráfico onde você especifica os recursos e serviços que seu aplicativo Teams usa.</span><span class="sxs-lookup"><span data-stu-id="61bbe-112">**Define your app with the manifest**: The manifest is a blueprint where you specify the capabilities and services your Teams app uses.</span></span>
  > - <span data-ttu-id="61bbe-113">**Escopo da sua audiência**: você pode criar um aplicativo do teams para uso pessoal ou colaboração.</span><span class="sxs-lookup"><span data-stu-id="61bbe-113">**Scope your audience**: You can build a Teams app for personal use or collaboration.</span></span> <span data-ttu-id="61bbe-114">Nos tutoriais, você aprenderá como criar uma guia para usuários individuais ou um grupo de pessoas em um canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="61bbe-114">In the tutorials, you'll learn how build a tab for individual users or a group of people in a channel or chat.</span></span>
  > - <span data-ttu-id="61bbe-115">Use o **SDK do teams para obter o contexto**: saiba como usar o SDK do Microsoft Teams JavaScript para executar a mudança de tema ou configurar a experiência de configuração</span><span class="sxs-lookup"><span data-stu-id="61bbe-115">**Utilize Teams SDK to get context**: Learn how to use the Microsoft Teams JavaScript SDK to perform theme change or set up configuration experience</span></span>  
  > - <span data-ttu-id="61bbe-116">**Expanda em seu aplicativo**: em todos os tutoriais, nos links para tópicos relacionados que você provavelmente tem interesse (alguns dos quais incluem diretrizes de autenticação e Design).</span><span class="sxs-lookup"><span data-stu-id="61bbe-116">**Expand on your app**: Throughout the tutorials, we link to related topics you're probably interested in (some of which include authentication and design guidelines).</span></span>

## <a name="teams-app-fundamentals"></a><span data-ttu-id="61bbe-117">Conceitos básicos do aplicativo Teams</span><span class="sxs-lookup"><span data-stu-id="61bbe-117">Teams app fundamentals</span></span>

<span data-ttu-id="61bbe-118">Antes de começar os tutoriais, você deve saber o seguinte sobre a criação de aplicativos para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="61bbe-118">Before you begin the tutorials, you should know the following about building apps for Teams.</span></span>

### <a name="apps-can-have-multiple-capabilities"></a><span data-ttu-id="61bbe-119">Os aplicativos podem ter vários recursos</span><span class="sxs-lookup"><span data-stu-id="61bbe-119">Apps can have multiple capabilities</span></span>

<span data-ttu-id="61bbe-120">Os aplicativos do teams são compostos por um ou mais [recursos de plataforma](../capabilities-overview.md), incluindo [guias](../doc-links/what-are-tabs.md), [bots](../doc-links/what-are-bots.md ), [extensões de mensagens](../doc-links/what-are-messaging-extensions.md)e [conectores e WebHooks](../doc-links/what-are-webhooks-and-connectors.md).</span><span class="sxs-lookup"><span data-stu-id="61bbe-120">Teams apps are made up of one or more [platform capabilities](../capabilities-overview.md), including [tabs](../doc-links/what-are-tabs.md), [bots](../doc-links/what-are-bots.md ), [messaging extensions](../doc-links/what-are-messaging-extensions.md), and [webhooks and connectors](../doc-links/what-are-webhooks-and-connectors.md).</span></span> <span data-ttu-id="61bbe-121">Os aplicativos do teams também têm muitas [convenções e elementos de interface do usuário](../doc-links/teams-ui-conventions.md), como cartões, módulos de tarefas e vinculação profunda, que você pode usar para criar a melhor experiência de usuário possível.</span><span class="sxs-lookup"><span data-stu-id="61bbe-121">Teams apps also have many [UI conventions and elements](../doc-links/teams-ui-conventions.md), such as cards, task modules, and deep linking, you can use to build the best possible user experience.</span></span>

<span data-ttu-id="61bbe-122">Para esses tutoriais, você criará apenas guias, mas poderá adicionar um bot ou outro recurso ao seu aplicativo como desejar.</span><span class="sxs-lookup"><span data-stu-id="61bbe-122">For these tutorials, you'll build only tabs but can add a bot or other capability to your app as you like.</span></span>

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="61bbe-123">O Microsoft Teams não hospeda seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="61bbe-123">Teams doesn't host your app</span></span>  

<span data-ttu-id="61bbe-124">Um aplicativo do teams consiste em três partes principais:</span><span class="sxs-lookup"><span data-stu-id="61bbe-124">A Teams app consists of three major pieces:</span></span>

1. <span data-ttu-id="61bbe-125">O cliente Microsoft Teams (Web, desktop ou celular) onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61bbe-125">The Microsoft Teams client (web, desktop, or mobile) where users interact with your app.</span></span>
1. <span data-ttu-id="61bbe-126">Seu aplicativo, serviço, fluxo de trabalho ou site que executa a lógica necessária, o armazenamento de dados e as chamadas de API para alimentar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61bbe-126">Your app, service, workflow, or website that performs the necessary logic, data storage, and API calls to power your app.</span></span>
1. <span data-ttu-id="61bbe-127">Seu pacote de aplicativos, que você usa para instalar o aplicativo no Teams.</span><span class="sxs-lookup"><span data-stu-id="61bbe-127">Your app package, which you use to install the app in Teams.</span></span> <span data-ttu-id="61bbe-128">Ele contém metadados de aplicativo (nome, ícones, etc.) e aponta para seus serviços.</span><span class="sxs-lookup"><span data-stu-id="61bbe-128">It contains app metadata (name, icons, etc.) and pointers to your services.</span></span>

## <a name="next-step"></a><span data-ttu-id="61bbe-129">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="61bbe-129">Next step</span></span>

<span data-ttu-id="61bbe-130">Isso é tudo por enquanto, vamos começar!</span><span class="sxs-lookup"><span data-stu-id="61bbe-130">That's all for now, let's get started!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="61bbe-131">Criar e executar seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="61bbe-131">Build and run your first app</span></span>](build-and-run-with-toolkit.md)
