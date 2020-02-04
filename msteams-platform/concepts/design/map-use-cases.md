---
title: Mapear seus casos de uso para os recursos do aplicativo
author: clearab
description: Decidir como distribuir seu aplicativo
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 5ebfa73df9b4f2c83533a33fbc6366c2c0ccffb4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672779"
---
# <a name="map-your-use-cases-to-teams-app-capabilities"></a><span data-ttu-id="82c78-103">Mapear seus casos de uso para recursos de aplicativos do teams</span><span class="sxs-lookup"><span data-stu-id="82c78-103">Map your use cases to teams app capabilities</span></span>

<span data-ttu-id="82c78-104">Se você ainda não tiver feito isso, certifique-se [de que os casos de uso foram considerados](~/concepts/design/map-use-cases.md) com cuidado.</span><span class="sxs-lookup"><span data-stu-id="82c78-104">If you haven't already, make sure you've [considered your use cases](~/concepts/design/map-use-cases.md) carefully.</span></span> <span data-ttu-id="82c78-105">Você também deve ter uma boa compreensão dos [pontos de extensibilidade e dos elementos da interface do usuário](~/concepts/extensibility-points.md) disponíveis para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="82c78-105">You should also have a good understanding of the [extensibility points and UI elements](~/concepts/extensibility-points.md) available for your app.</span></span> <span data-ttu-id="82c78-106">Depois de descobrir *o que* você está tentando resolver e *quem* você está resolvendo, é hora de começar a pensar sobre *como*.</span><span class="sxs-lookup"><span data-stu-id="82c78-106">Once you've figured out *what* your trying to solve, and *who* you're solving it for, it is time to start thinking about *how*.</span></span>

<span data-ttu-id="82c78-107">Abaixo você encontrará alguns cenários comuns e uma seleção de pontos de extensibilidade e elementos de interface do usuário que funcionam bem com eles.</span><span class="sxs-lookup"><span data-stu-id="82c78-107">Below you'll find some common scenarios, and a selection of extensibility points and UI elements that work well with them.</span></span> <span data-ttu-id="82c78-108">Não se trata de uma lista exaustiva, apenas para ajudá-lo a pensar em algumas das possibilidades disponíveis para você e a plataforma do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="82c78-108">It isn't intended to be an exhaustive list, just to help you think through some of the possibilities available to you and the Teams platform.</span></span>

## <a name="create-share-and-collaborate-on-items-in-an-external-system"></a><span data-ttu-id="82c78-109">Criar, compartilhar e colaborar em itens em um sistema externo</span><span class="sxs-lookup"><span data-stu-id="82c78-109">Create, share and collaborate on items in an external system</span></span>

<span data-ttu-id="82c78-110">O aplicativo para o Microsoft Teams é uma ótima maneira de interagir com seus dados, e há uma variedade de pontos de integração para escolher.</span><span class="sxs-lookup"><span data-stu-id="82c78-110">App for Microsoft Teams are a great way to interact with your data, and there are a variety of integration points to choose from.</span></span>

* <span data-ttu-id="82c78-111">Extensões de mensagens com comandos de pesquisa – pesquise sistemas externos e compartilhe os resultados como um cartão interativo.</span><span class="sxs-lookup"><span data-stu-id="82c78-111">Messaging extensions with search commands - Search external systems and share the results as an interactive card.</span></span>

* <span data-ttu-id="82c78-112">Extensões de mensagens com comandos de ação-coletar informações para inserir em um repositório de dados ou executar pesquisas avançadas.</span><span class="sxs-lookup"><span data-stu-id="82c78-112">Messaging extensions with action commands - Collect information to insert into a data store or perform advanced searches.</span></span>

* <span data-ttu-id="82c78-113">Guias: criar experiências da Web incorporadas para exibir, trabalhar e compartilhar dados.</span><span class="sxs-lookup"><span data-stu-id="82c78-113">Tabs - Create embedded web experiences to view, work with, and share data.</span></span>

* <span data-ttu-id="82c78-114">Conectores e WebHooks-uma maneira simples de enviar dados para e enviar dados do cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="82c78-114">Connectors and webhooks - A simple way to push data into, and send data out of the Teams client.</span></span>

* <span data-ttu-id="82c78-115">Módulos de tarefas-formulários modais interativos de onde você precisar coletar ou exibir informações.</span><span class="sxs-lookup"><span data-stu-id="82c78-115">Task modules - Interactive modal forms from wherever you need them to collect or display information.</span></span>

## <a name="initiate-workflows-and-processes"></a><span data-ttu-id="82c78-116">Iniciar fluxos de trabalho e processos</span><span class="sxs-lookup"><span data-stu-id="82c78-116">Initiate workflows and processes</span></span>

<span data-ttu-id="82c78-117">Às vezes, você precisa apenas de uma maneira rápida de iniciar um processo ou fluxo de trabalho em um sistema externo.</span><span class="sxs-lookup"><span data-stu-id="82c78-117">Sometimes you just need a quick way to start a process or workflow in an external system.</span></span>

* <span data-ttu-id="82c78-118">Comandos de ação de extensões de mensagens-disparar de mensagens, permitindo que os usuários enviem rapidamente o conteúdo de uma mensagem para seus serviços Web.</span><span class="sxs-lookup"><span data-stu-id="82c78-118">Messaging extensions action commands - Trigger from messages, allowing your users to quickly send the contents of a message to your web services.</span></span>

* <span data-ttu-id="82c78-119">Módulos de tarefas: Abra-os a partir de uma guia, de um bot ou de uma extensão de mensagens para coletar informações antes de iniciar um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="82c78-119">Task modules - Open them from a tab, a bot, or a messaging extension to collect information before initiating a workflow.</span></span>

* <span data-ttu-id="82c78-120">Bots de conversa-interaja com seus usuários por meio de texto e cartões ricos.</span><span class="sxs-lookup"><span data-stu-id="82c78-120">Conversational bots - Interact with your users through text and rich cards.</span></span>

* <span data-ttu-id="82c78-121">WebHooks de saída-uma boa opção para uma simples interação de frente e para trás quando você não precisa criar um bot de conversa inteiro.</span><span class="sxs-lookup"><span data-stu-id="82c78-121">Outgoing webhooks - A good choice for a simple back-and-forth interaction when you don't need to build an entire conversational bot.</span></span>

## <a name="send-notifications-and-alerts"></a><span data-ttu-id="82c78-122">Enviar notificações e alertas</span><span class="sxs-lookup"><span data-stu-id="82c78-122">Send notifications and alerts</span></span>

<span data-ttu-id="82c78-123">Envie notificações e alertas assíncronos para seus usuários no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="82c78-123">Send asynchronous notifications and alerts to your users in Teams.</span></span> <span data-ttu-id="82c78-124">Use cartões interativos para fornecer acesso rápido a ações comumente usadas e links para informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="82c78-124">Use interactive cards to provide quick access to commonly used actions and links to additional information.</span></span>

* <span data-ttu-id="82c78-125">Bots de conversa-envie mensagens pró-ativas para grupos, canais ou usuários individuais.</span><span class="sxs-lookup"><span data-stu-id="82c78-125">Conversational bots - Send proactive messages to groups, channels, or individual users.</span></span>

* <span data-ttu-id="82c78-126">Conectores & WebHooks de entrada: permitir que um canal assine receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="82c78-126">Connectors & incoming webhooks - Allow a channel to subscribe to receive messages.</span></span> <span data-ttu-id="82c78-127">Com um conector permite que os usuários personalizem a assinatura com uma página de configuração.</span><span class="sxs-lookup"><span data-stu-id="82c78-127">With a connector let users tailor the subscription with a configuration page.</span></span>

## <a name="ask-questions-and-get-answers"></a><span data-ttu-id="82c78-128">Fazer perguntas e obter respostas</span><span class="sxs-lookup"><span data-stu-id="82c78-128">Ask questions and get answers</span></span>

<span data-ttu-id="82c78-129">Pessoas têm dúvidas.</span><span class="sxs-lookup"><span data-stu-id="82c78-129">People have questions.</span></span> <span data-ttu-id="82c78-130">Você provavelmente tem muitas das respostas armazenadas em algum lugar.</span><span class="sxs-lookup"><span data-stu-id="82c78-130">You've probably got a lot of the answers stored away somewhere.</span></span> <span data-ttu-id="82c78-131">Infelizmente, o que costuma ser muito difícil de conectar os dois juntos.</span><span class="sxs-lookup"><span data-stu-id="82c78-131">Unfortunately, its often quite difficult to connect the two together.</span></span>

* <span data-ttu-id="82c78-132">Bots de conversa-processamento de linguagem natural, AI, aprendizado de máquina, todos os buzzwords.</span><span class="sxs-lookup"><span data-stu-id="82c78-132">Conversational bots - Natural language processing, AI, machine learning, all the buzzwords.</span></span> <span data-ttu-id="82c78-133">Use um bot alimentado pela nuvem inteligente para conectar seus usuários às respostas de que precisam.</span><span class="sxs-lookup"><span data-stu-id="82c78-133">Use a bot powered by the intelligent cloud to connect your users to the answers they need.</span></span>

* <span data-ttu-id="82c78-134">Guias-incorpore o portal da Web existente no Microsoft Teams ou crie uma versão específica do teams para funcionalidade adicional.</span><span class="sxs-lookup"><span data-stu-id="82c78-134">Tabs - Embed your existing web portal in Teams, or create a Teams-specific version for added functionality.</span></span>

## <a name="get-social"></a><span data-ttu-id="82c78-135">Obter social</span><span class="sxs-lookup"><span data-stu-id="82c78-135">Get social</span></span>

<span data-ttu-id="82c78-136">Uma plataforma de colaboração é inerentemente uma plataforma social.</span><span class="sxs-lookup"><span data-stu-id="82c78-136">A collaboration platform is inherently a social platform.</span></span> <span data-ttu-id="82c78-137">Deixe que seu lado criativo fique livre e adicione uma diversão ao seu ambiente de trabalho.</span><span class="sxs-lookup"><span data-stu-id="82c78-137">Let your creative side be free, and add some fun into your workplace.</span></span>

* <span data-ttu-id="82c78-138">Todos eles-enviam piadas, dão Parabéns, obtêm alguns memess, emitem alguns emojis ou qualquer outra coisa que tenha sido elaborado.</span><span class="sxs-lookup"><span data-stu-id="82c78-138">All of them - Send jokes, give kudos, get some memes, toss out some emoji's or whatever else strikes your fancy.</span></span>

## <a name="anything-you-can-do-in-a-single-page-app-spa"></a><span data-ttu-id="82c78-139">Tudo o que você pode fazer em um aplicativo de página única (SPA)</span><span class="sxs-lookup"><span data-stu-id="82c78-139">Anything you can do in a Single Page App (SPA)</span></span>

<span data-ttu-id="82c78-140">As guias são páginas da Web incorporadas.</span><span class="sxs-lookup"><span data-stu-id="82c78-140">Tabs are embedded web pages.</span></span> <span data-ttu-id="82c78-141">Praticamente tudo o que você pode fazer em um SPA, você pode fazer em uma guia no Teams.</span><span class="sxs-lookup"><span data-stu-id="82c78-141">Pretty much anything you can do in a SPA, you can do in a tab in Teams.</span></span> <span data-ttu-id="82c78-142">Só não se esqueça de prestar atenção às guias de grupo e canal de escopo para experiências compartilhadas, guias pessoais são para... experiências pessoais.</span><span class="sxs-lookup"><span data-stu-id="82c78-142">Just be sure to pay attention to scope - group and channel tabs are for shared experiences, personal tabs are for ... personal experiences.</span></span> <span data-ttu-id="82c78-143">A lista de itens da equipe fica na guia canal, a lista de suas coisas é exibida na guia pessoal.</span><span class="sxs-lookup"><span data-stu-id="82c78-143">The team's list of stuff goes on the channel tab, the list of your stuff goes in the personal tab.</span></span>

## <a name="start-small"></a><span data-ttu-id="82c78-144">Iniciar pequeno</span><span class="sxs-lookup"><span data-stu-id="82c78-144">Start small</span></span>

<span data-ttu-id="82c78-145">Não sabe por onde começar?</span><span class="sxs-lookup"><span data-stu-id="82c78-145">Not sure where to start?</span></span> <span data-ttu-id="82c78-146">Você se sente um pouco sobrecarregado com a variedade de opções incríveis disponíveis?</span><span class="sxs-lookup"><span data-stu-id="82c78-146">Feeling a bit overwhelmed with the awesome variety of options available to you?</span></span> <span data-ttu-id="82c78-147">Não fret, escolha um recurso principal do seu aplicativo e inicie lá.</span><span class="sxs-lookup"><span data-stu-id="82c78-147">Don't fret, choose a core feature of your app and start there.</span></span> <span data-ttu-id="82c78-148">Depois que você se sentir para o fluxo de informações através dos vários contextos no Teams, será muito mais simples fazer uma interação mais complexa.</span><span class="sxs-lookup"><span data-stu-id="82c78-148">Once you get a feel for the flow of information through the various contexts in Teams, it will be a lot simpler to picture a more complex interaction.</span></span>

## <a name="putting-it-all-together"></a><span data-ttu-id="82c78-149">Colocando tudo em um só lugar</span><span class="sxs-lookup"><span data-stu-id="82c78-149">Putting it all together</span></span>

<span data-ttu-id="82c78-150">Dito isso, os melhores aplicativos geralmente combinam vários recursos, criando um aplicativo que contrata usuários no contexto certo com a funcionalidade correta no momento certo.</span><span class="sxs-lookup"><span data-stu-id="82c78-150">That being said, the best apps usually combine multiple features, creating an app that engages users in the right context with the right functionality at the right time.</span></span> <span data-ttu-id="82c78-151">Não tente forçar a funcionalidade em um local que não pertença-apenas porque você tem um bom bot de conversa um-para-um não significa que você deve apenas adicioná-lo a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="82c78-151">Don't try to force functionality into a place it doesn't belong - just because you've got a good one-to-one conversational bot doesn't mean you should just add it to a team.</span></span> <span data-ttu-id="82c78-152">Pontos de extensibilidade diferentes são bons para coisas diferentes; Jogue até seus pontos fortes e seu aplicativo brilhará.</span><span class="sxs-lookup"><span data-stu-id="82c78-152">Different extensibility points are good for different things; play to their strengths and your app will shine.</span></span>
