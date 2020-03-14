---
title: O que são bots de conversa?
author: clearab
description: Uma visão geral dos bots de conversa no Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: e10275cba97f835cd59e572b48d2db7cb902d096
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "42635302"
---
# <a name="what-are-conversational-bots"></a><span data-ttu-id="c49cf-103">O que são bots de conversa?</span><span class="sxs-lookup"><span data-stu-id="c49cf-103">What are conversational bots?</span></span>

<span data-ttu-id="c49cf-104">Os bots de conversa permitem que os usuários interajam com o serviço Web por meio de texto, cartões interativos e módulos de tarefa.</span><span class="sxs-lookup"><span data-stu-id="c49cf-104">Conversational bots allow users to interact with your web service through text, interactive cards, and task modules.</span></span> <span data-ttu-id="c49cf-105">Eles são incrivelmente flexíveis — os bots de conversação podem ser delimitados para lidar com alguns comandos simples ou assistentes virtuais de processamento de idioma natural, com inteligência artificial e de alta capacidade de comunicação.</span><span class="sxs-lookup"><span data-stu-id="c49cf-105">They're incredibly flexible — conversational bots can be scoped to handling a few simple commands or complex, artificial-intelligence-powered and natural-language-processing virtual assistants.</span></span> <span data-ttu-id="c49cf-106">Eles podem ser um aspecto de um aplicativo maior ou totalmente autônomo.</span><span class="sxs-lookup"><span data-stu-id="c49cf-106">They can be one aspect of a larger application, or completely stand-alone.</span></span>

<span data-ttu-id="c49cf-107">O GIF abaixo mostra um usuário que está se invertendo com um bot em um chat de um-para-um usando os cartões de texto e interativos.</span><span class="sxs-lookup"><span data-stu-id="c49cf-107">The GIF below shows a user conversing with a bot in a one-to-one chat using both text and interactive cards.</span></span> <span data-ttu-id="c49cf-108">Encontrar a combinação certa de cartões, texto e módulos de tarefas é fundamental para criar um bot útil.</span><span class="sxs-lookup"><span data-stu-id="c49cf-108">Finding the right mix of cards, text, and task modules is key to creating a useful bot.</span></span> <span data-ttu-id="c49cf-109">Não se esqueça, os bots são muito mais do que apenas texto!</span><span class="sxs-lookup"><span data-stu-id="c49cf-109">Don't forget, bots are much more than just text!</span></span>

![Perguntas frequentes mais sobre gif](~/assets/images/FAQPlusEndUser.gif)

## <a name="how-bots-work"></a><span data-ttu-id="c49cf-111">Como funcionam os bots</span><span class="sxs-lookup"><span data-stu-id="c49cf-111">How bots work</span></span>

<span data-ttu-id="c49cf-112">O bot da equipe consiste em três elementos:</span><span class="sxs-lookup"><span data-stu-id="c49cf-112">Your Teams bot consists of three elements:</span></span>

* <span data-ttu-id="c49cf-113">Um serviço Web publicamente acessível que você hospeda.</span><span class="sxs-lookup"><span data-stu-id="c49cf-113">A publicly accessible web service that you host.</span></span>
* <span data-ttu-id="c49cf-114">O registro do bot com a estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="c49cf-114">Your bot registration with the Bot Framework.</span></span>
* <span data-ttu-id="c49cf-115">Seu pacote de aplicativos do Microsoft Teams com o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c49cf-115">Your Teams app package with your app manifest.</span></span> <span data-ttu-id="c49cf-116">Isso é o que os usuários instalarão e conectarão o cliente do teams ao seu serviço Web, roteado através do serviço bot.</span><span class="sxs-lookup"><span data-stu-id="c49cf-116">This is what your users will install and connects the Teams client to your web service, routed through the Bot Service.</span></span>

<span data-ttu-id="c49cf-117">Os bots do Microsoft Teams são criados na [Microsoft bot Framework](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="c49cf-117">Bots for Microsoft Teams are built on the [Microsoft Bot Framework](https://dev.botframework.com/).</span></span> <span data-ttu-id="c49cf-118">Se você já tiver um bot baseado na estrutura de bot, poderá adaptá-lo facilmente para trabalhar no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="c49cf-118">If you already have a bot that's based on the Bot Framework, you can easily adapt it to work in Microsoft Teams.</span></span> <span data-ttu-id="c49cf-119">Recomendamos que você use C# ou node. js para aproveitar os benefícios de nossos [SDKs](/microsoftteams/platform/#pivot=sdk-tools).</span><span class="sxs-lookup"><span data-stu-id="c49cf-119">We recommend you use either C# or Node.js to take advantage of our [SDKs](/microsoftteams/platform/#pivot=sdk-tools).</span></span> <span data-ttu-id="c49cf-120">Esses pacotes estendem as classes e os métodos do SDK do gerador de bot básico da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c49cf-120">These packages extend the basic Bot Builder SDK classes and methods as follows:</span></span>

* <span data-ttu-id="c49cf-121">Use tipos de cartões especializados como o cartão de conexão do Office 365.</span><span class="sxs-lookup"><span data-stu-id="c49cf-121">Use specialized card types like the Office 365 Connector card.</span></span>
* <span data-ttu-id="c49cf-122">Consumir e definir dados de canal específicos de equipes em atividades.</span><span class="sxs-lookup"><span data-stu-id="c49cf-122">Consume and set Teams-specific channel data on activities.</span></span>
* <span data-ttu-id="c49cf-123">Processar solicitações de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c49cf-123">Process messaging extension requests.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c49cf-124">Você pode desenvolver aplicativos do teams em qualquer tecnologia de programação Web e chamar as [APIs REST da estrutura de bot](/bot-framework/rest-api/bot-framework-rest-overview) diretamente, mas você deve executar todo o tratamento de tokens por conta própria.</span><span class="sxs-lookup"><span data-stu-id="c49cf-124">You can develop Teams apps in any web-programming technology and call the [Bot Framework REST APIs](/bot-framework/rest-api/bot-framework-rest-overview) directly, but you must perform all token handling yourself.</span></span>

> [!TIP]
> <span data-ttu-id="c49cf-125">O Teams app Studio \* ajuda você a criar e configurar o manifesto do aplicativo e pode registrar seu serviço Web como um bot na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="c49cf-125">Teams App Studio\* helps you create and configure your app manifest, and can register your web service as a bot on the Bot Framework.</span></span> <span data-ttu-id="c49cf-126">Ele também contém uma biblioteca de controle de reagir e um construtor de cartões interativos.</span><span class="sxs-lookup"><span data-stu-id="c49cf-126">It also contains a React control library and an interactive card builder.</span></span> <span data-ttu-id="c49cf-127">*Confira* [introdução ao Teams app Studio](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c49cf-127">*See* [Getting started with Teams App Studio](~/concepts/build-and-test/app-studio-overview.md).</span></span>

## <a name="webhooks-and-connectors"></a><span data-ttu-id="c49cf-128">WebHooks e conectores</span><span class="sxs-lookup"><span data-stu-id="c49cf-128">Webhooks and connectors</span></span>

<span data-ttu-id="c49cf-129">WebHooks e conectores permitem que você crie um bot simples para interação básica, como iniciando de um fluxo de trabalho ou outros comandos simples.</span><span class="sxs-lookup"><span data-stu-id="c49cf-129">Webhooks and connectors allow you to create a simple bot for basic interaction, like kicking off a workflow or other simple commands.</span></span> <span data-ttu-id="c49cf-130">Eles residem apenas na equipe em que você os cria e se destinam a processos simples específicos do fluxo de trabalho de sua empresa.</span><span class="sxs-lookup"><span data-stu-id="c49cf-130">They live only in the team in which you create them and are intended for simple processes specific to your company's workflow.</span></span> <span data-ttu-id="c49cf-131">*Confira* [o que são WebHooks e conectores?](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c49cf-131">*See* [What are webhooks and connectors?](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) for more information.</span></span>

## <a name="where-bots-work-best"></a><span data-ttu-id="c49cf-132">Onde os bots funcionam melhor</span><span class="sxs-lookup"><span data-stu-id="c49cf-132">Where bots work best</span></span>

<span data-ttu-id="c49cf-133">Os bots no Microsoft Teams podem fazer parte de uma conversa de um-para-um, um chat de grupo ou um canal de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="c49cf-133">Bots in Microsoft Teams can be part of a one-to-one conversation, a group chat, or a channel in a Team.</span></span> <span data-ttu-id="c49cf-134">Cada escopo fornecerá oportunidades e desafios exclusivos para o bot da conversa.</span><span class="sxs-lookup"><span data-stu-id="c49cf-134">Each scope will provide unique opportunities, and challenges, for your conversational bot.</span></span>

### <a name="in-a-channel"></a><span data-ttu-id="c49cf-135">Em um canal</span><span class="sxs-lookup"><span data-stu-id="c49cf-135">In a channel</span></span>

<span data-ttu-id="c49cf-136">Os canais contêm conversas encadeadas entre várias pessoas, potencialmente muitas pessoas (atualmente, até 2000).</span><span class="sxs-lookup"><span data-stu-id="c49cf-136">Channels contain threaded conversations between multiple people — potentially lots of people (currently, up to two thousand).</span></span> <span data-ttu-id="c49cf-137">Isso pode causar o alcance maciço de bot, mas as interações individuais precisam ser concisas.</span><span class="sxs-lookup"><span data-stu-id="c49cf-137">This potentially gives your bot massive reach, but individual interactions need to be concise.</span></span> <span data-ttu-id="c49cf-138">Interações de múltipla volta tradicional provavelmente não funcionarão bem.</span><span class="sxs-lookup"><span data-stu-id="c49cf-138">Traditional multi-turn interactions probably won't work well.</span></span> <span data-ttu-id="c49cf-139">Em vez disso, procure usar cartões interativos ou módulos de tarefas ou mova a conversa para uma conversa de um para um se precisar coletar muitas informações.</span><span class="sxs-lookup"><span data-stu-id="c49cf-139">Instead, look to use interactive cards or task modules, or potentially move the conversation to a one-to-one conversation if you need to collect lots of information.</span></span> <span data-ttu-id="c49cf-140">O bot também terá acesso apenas às mensagens em que for `@mentioned` diretamente, não será possível recuperar mensagens adicionais da conversa usando o Microsoft Graph e permissões elevadas de nível de organização.</span><span class="sxs-lookup"><span data-stu-id="c49cf-140">Your bot will also only have access to messages where it's `@mentioned` directly, you cannot retrieve additional messages from the conversation using Microsoft Graph and elevated organization-level permissions.</span></span>

<span data-ttu-id="c49cf-141">Alguns cenários em que os bots Excel em um canal incluem:</span><span class="sxs-lookup"><span data-stu-id="c49cf-141">Some scenarios where bots excel in a channel include:</span></span>

* <span data-ttu-id="c49cf-142">**Notificações**, especialmente se você fornecer um cartão interativo para que os usuários tenham mais informações.</span><span class="sxs-lookup"><span data-stu-id="c49cf-142">**Notifications**, particularly if you provide an interactive card for users to take additional information.</span></span>
* <span data-ttu-id="c49cf-143">**Cenários de comentários** como pesquisas e pesquisas.</span><span class="sxs-lookup"><span data-stu-id="c49cf-143">**Feedback scenarios** like polls and surveys.</span></span>
* <span data-ttu-id="c49cf-144">Interações que podem ser resolvidas em um **único ciclo de solicitação/resposta**, onde os resultados são úteis para vários membros da conversa.</span><span class="sxs-lookup"><span data-stu-id="c49cf-144">Interactions that can be resolved in a **single request/response cycle**, where the results are useful for multiple members of the conversation.</span></span>
* <span data-ttu-id="c49cf-145">**Bots sociais/divertidos** — obtenha uma imagem de gato incrível, escolha aleatoriamente um vencedor, etc.</span><span class="sxs-lookup"><span data-stu-id="c49cf-145">**Social/fun bots** — get an awesome cat image, randomly pick a winner, etc.</span></span>

### <a name="in-a-group-chat"></a><span data-ttu-id="c49cf-146">Em um chat de grupo</span><span class="sxs-lookup"><span data-stu-id="c49cf-146">In a group chat</span></span>

<span data-ttu-id="c49cf-147">Os chats de grupo são conversas não encadeadas entre três ou mais pessoas.</span><span class="sxs-lookup"><span data-stu-id="c49cf-147">Group chats are non-threaded conversations between three or more people.</span></span> <span data-ttu-id="c49cf-148">Eles tendem a ter menos membros do que um canal e são mais transitórios.</span><span class="sxs-lookup"><span data-stu-id="c49cf-148">They tend to have fewer members than a channel, and are more transient.</span></span> <span data-ttu-id="c49cf-149">Semelhante a um canal, seu bot só terá acesso a mensagens em que for `@mentioned` diretamente.</span><span class="sxs-lookup"><span data-stu-id="c49cf-149">Similar to a channel, your bot will only have access to messages where it's `@mentioned` directly.</span></span>

<span data-ttu-id="c49cf-150">Cenários que funcionam bem em um canal normalmente funcionarão tão bem em um chat de grupo.</span><span class="sxs-lookup"><span data-stu-id="c49cf-150">Scenarios that work well in a channel will usually work just as well in a group chat.</span></span>

### <a name="in-a-one-to-one-chat"></a><span data-ttu-id="c49cf-151">Em um chat de um-para-um</span><span class="sxs-lookup"><span data-stu-id="c49cf-151">In a one-to-one chat</span></span>

<span data-ttu-id="c49cf-152">Essa é a maneira tradicional de um bot de conversação interagir com um usuário.</span><span class="sxs-lookup"><span data-stu-id="c49cf-152">This is the traditional way for a conversational bot to interact with a user.</span></span> <span data-ttu-id="c49cf-153">Eles podem habilitar cargas de trabalho incrivelmente diversificadas.</span><span class="sxs-lookup"><span data-stu-id="c49cf-153">They can enable incredibly diverse workloads.</span></span> <span data-ttu-id="c49cf-154">P&um bots, bots que iniciam fluxos de trabalho em outros sistemas, bots que dizem piadas e bots que fazem anotações são apenas alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="c49cf-154">Q&A bots, bots that initiate workflows in other systems, bots that tell jokes, and bots that take notes are just a few examples.</span></span> <span data-ttu-id="c49cf-155">Lembre-se apenas de considerar se uma interface baseada em conversa é a melhor maneira de apresentar sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="c49cf-155">Just remember to consider whether a conversation-based interface is the best way to present your functionality.</span></span>

## <a name="bot-fails"></a><span data-ttu-id="c49cf-156">Falha no bot</span><span class="sxs-lookup"><span data-stu-id="c49cf-156">Bot fails</span></span>

### <a name="having-multi-turn-experiences-in-chat"></a><span data-ttu-id="c49cf-157">Ter experiências de vários voltagens no chat</span><span class="sxs-lookup"><span data-stu-id="c49cf-157">Having multi-turn experiences in chat</span></span>

<span data-ttu-id="c49cf-158">Uma caixa de diálogo abrangente entre o bot e o usuário é uma maneira lenta e muito complexa de obter uma tarefa concluída e também exige que o desenvolvedor Mantenha o estado.</span><span class="sxs-lookup"><span data-stu-id="c49cf-158">An extensive dialog between your bot and the user is a slow and overly complex way to get a task completed and it also requires the developer to maintain state.</span></span> <span data-ttu-id="c49cf-159">Para sair desse Estado, um usuário deve se esgotar ou digitar "*Cancelar*".</span><span class="sxs-lookup"><span data-stu-id="c49cf-159">To exit this state a user must either time-out or type “*Cancel*”.</span></span> <span data-ttu-id="c49cf-160">Acima de tudo, o processo é desnecessariamente entediante:</span><span class="sxs-lookup"><span data-stu-id="c49cf-160">Above all, the process is unnecessarily tedious:</span></span>

<span data-ttu-id="c49cf-161">USUÁRIO: agendar uma reunião com o Megan.</span><span class="sxs-lookup"><span data-stu-id="c49cf-161">USER: Schedule a meeting with Megan.</span></span>

<span data-ttu-id="c49cf-162">BOT: Eu encontrei 200 resultados, inclua um nome e sobrenome.</span><span class="sxs-lookup"><span data-stu-id="c49cf-162">BOT: I’ve found 200 results, please include a first and last name.</span></span>

<span data-ttu-id="c49cf-163">USUÁRIO: agendar uma reunião com o Megan Bowen.</span><span class="sxs-lookup"><span data-stu-id="c49cf-163">USER: Schedule a meeting with Megan Bowen.</span></span>

<span data-ttu-id="c49cf-164">BOT: OK, que horário você gostaria de reunir com o Megan Bowen?</span><span class="sxs-lookup"><span data-stu-id="c49cf-164">BOT: OK, what time would you like to meet with Megan Bowen?</span></span>

<span data-ttu-id="c49cf-165">USUÁRIO: 1:00 PM.</span><span class="sxs-lookup"><span data-stu-id="c49cf-165">USER: 1:00 pm.</span></span>

<span data-ttu-id="c49cf-166">BOT: em que dia?</span><span class="sxs-lookup"><span data-stu-id="c49cf-166">BOT: On which day?</span></span>

### <a name="supporting-too-many-commands"></a><span data-ttu-id="c49cf-167">Suporte a muitos comandos</span><span class="sxs-lookup"><span data-stu-id="c49cf-167">Supporting too many commands</span></span>

<span data-ttu-id="c49cf-168">Um bot que dá suporte a comandos excessivos, especialmente uma ampla variedade de comandos, não será bem-sucedido ou exibido positivamente pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="c49cf-168">A bot that supports excessive commands, especially a broad range of commands, will not be successful or viewed positively by users.</span></span> <span data-ttu-id="c49cf-169">Como há apenas 6 comandos visíveis no menu do bot atual, qualquer outra coisa provavelmente será usada com qualquer frequência.</span><span class="sxs-lookup"><span data-stu-id="c49cf-169">Since there are only 6 visible commands in the current bot menu, anything more is unlikely to be used with any frequency.</span></span> <span data-ttu-id="c49cf-170">Os bots que se aprofundam em uma área específica em vez de tentar ser um assistente amplo funcionará e se comportarão melhor.</span><span class="sxs-lookup"><span data-stu-id="c49cf-170">Bots that go deep into a specific area rather than trying to be a broad assistant will work and fare better.</span></span>

### <a name="maintaining-a-large-retrieval-knowledge-base-with-unranked-responses"></a><span data-ttu-id="c49cf-171">Mantendo uma grande base de conhecimento de recuperação com respostas não classificadas</span><span class="sxs-lookup"><span data-stu-id="c49cf-171">Maintaining a large retrieval knowledge base with unranked responses</span></span>

<span data-ttu-id="c49cf-172">Os bots são mais adequados para interações curtas e rápidas, não pesquisando por meio de listas longas procurando por uma resposta.</span><span class="sxs-lookup"><span data-stu-id="c49cf-172">Bots are best suited for short, quick interactions, not sifting though long lists looking for an answer.</span></span>

## <a name="get-started"></a><span data-ttu-id="c49cf-173">Introdução</span><span class="sxs-lookup"><span data-stu-id="c49cf-173">Get started</span></span>

* [<span data-ttu-id="c49cf-174">Bot de conversa do teams em C#/dotnet</span><span class="sxs-lookup"><span data-stu-id="c49cf-174">Teams conversation bot in C#/dotnet</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)
* [<span data-ttu-id="c49cf-175">Bot de conversa do teams em JavaScript</span><span class="sxs-lookup"><span data-stu-id="c49cf-175">Teams conversation bot in JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)

## <a name="learn-more"></a><span data-ttu-id="c49cf-176">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="c49cf-176">Learn more</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c49cf-177">Noções básicas de bots no Teams</span><span class="sxs-lookup"><span data-stu-id="c49cf-177">The basics of bots in Teams</span></span>](~/bots/bot-basics.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="c49cf-178">Criar um bot para o Teams</span><span class="sxs-lookup"><span data-stu-id="c49cf-178">Create a bot for Teams</span></span>](~/bots/how-to/create-a-bot-for-teams.md)
