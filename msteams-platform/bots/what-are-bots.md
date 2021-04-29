---
title: Bots no Microsoft Teams
author: clearab
description: Uma visão geral dos bots no Microsoft Teams.
ms.topic: overview
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: e91211d7237384b1d39f877cf217dcddfc66cc1e
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075658"
---
# <a name="bots-in-microsoft-teams"></a><span data-ttu-id="9712d-103">Bots no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9712d-103">Bots in Microsoft Teams</span></span>

<span data-ttu-id="9712d-104">Um bot também conhecido como chatbot ou bot de conversa é um aplicativo que executa tarefas automatizadas simples e repetitivas executadas pelos usuários, como atendimento ao cliente ou equipe de suporte.</span><span class="sxs-lookup"><span data-stu-id="9712d-104">A bot also referred to as a chatbot or conversational bot is an app that runs simple and repetitive automated tasks performed by the users, such as customer service or support staff.</span></span> <span data-ttu-id="9712d-105">Exemplos de bots no uso diário incluem bots que fornecem informações sobre o clima, fazem reservas de jantar ou fornecem informações de viagem.</span><span class="sxs-lookup"><span data-stu-id="9712d-105">Examples of bots in everyday use include, bots that provide information about the weather, make dinner reservations, or provide travel information.</span></span> <span data-ttu-id="9712d-106">A interação com um bot pode ser uma resposta e uma pergunta rápida, ou pode ser uma conversa complexa que fornece acesso aos serviços.</span><span class="sxs-lookup"><span data-stu-id="9712d-106">A bot interaction can be a quick question and answer, or it can be a complex conversation that provides access to services.</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/zSIysk0yL0Q]

<span data-ttu-id="9712d-107">Os bots de conversa permitem aos usuários interagir com o serviço Web por meio de texto, cartões interativos e módulos de tarefas.</span><span class="sxs-lookup"><span data-stu-id="9712d-107">Conversational bots allow users to interact with your web service through text, interactive cards, and task modules.</span></span>

![Invocar bot usando texto](~/assets/images/invokebotwithtext.png)

![Invocar bot usando cartão](~/assets/images/invokebotwithcard.png)

<img src="~/assets/images/task-module-example.png" alt="Invoke bot using task module" width="400"/>

<span data-ttu-id="9712d-110">Os bots de conversa são extremamente flexíveis e podem ser escopos para lidar com alguns comandos simples ou tarefas complexas, com inteligência artificial e processamento de linguagem natural.</span><span class="sxs-lookup"><span data-stu-id="9712d-110">Conversational bots are incredibly flexible and can be scoped to handle a few simple commands, or complex, artificial-intelligence-powered, and natural-language-processing tasks.</span></span> <span data-ttu-id="9712d-111">Eles podem ser um aspecto de um aplicativo maior ou ser completamente autônomo.</span><span class="sxs-lookup"><span data-stu-id="9712d-111">They can be one aspect of a larger application, or be completely stand-alone.</span></span>

<span data-ttu-id="9712d-112">Encontrar a combinação correta de cartões, texto e módulos de tarefa são fundamentais para criar um bot útil.</span><span class="sxs-lookup"><span data-stu-id="9712d-112">Finding the right mix of cards, text, and task modules are key to create a useful bot.</span></span> <span data-ttu-id="9712d-113">A imagem a seguir mostra um usuário conversando com um bot em um chat um para um usando cartões interativos e de texto:</span><span class="sxs-lookup"><span data-stu-id="9712d-113">The following image shows a user conversing with a bot in a one-to-one chat using both, text and interactive cards:</span></span>

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Exemplo de bot de perguntas frequentes" border="true":::

<span data-ttu-id="9712d-115">Cada interação entre o usuário e o bot é representada como uma atividade.</span><span class="sxs-lookup"><span data-stu-id="9712d-115">Every interaction between the user and the bot is represented as an activity.</span></span> <span data-ttu-id="9712d-116">Quando um bot recebe uma atividade, ele a passa para seus manipuladores de atividades.</span><span class="sxs-lookup"><span data-stu-id="9712d-116">When a bot receives an activity, it passes it on to its activity handlers.</span></span> <span data-ttu-id="9712d-117">Para obter mais informações, consulte [manipuladores de atividade de bot.](~/bots/bot-basics.md)</span><span class="sxs-lookup"><span data-stu-id="9712d-117">For more information, see [bot activity handlers](~/bots/bot-basics.md).</span></span> 

<span data-ttu-id="9712d-118">Além disso, os bots são aplicativos que têm uma interface de conversa.</span><span class="sxs-lookup"><span data-stu-id="9712d-118">In addition, bots are apps that have a conversational interface.</span></span> <span data-ttu-id="9712d-119">Você pode interagir com um bot usando texto, cartões interativos e fala.</span><span class="sxs-lookup"><span data-stu-id="9712d-119">You can interact with a bot using text, interactive cards, and speech.</span></span> <span data-ttu-id="9712d-120">Um bot se comporta de forma diferente, dependendo se a conversa é um canal ou conversa de chat de grupo, ou é uma conversa um para um.</span><span class="sxs-lookup"><span data-stu-id="9712d-120">A bot behaves differently depending on whether the conversation is a channel or group chat conversation, or it is a one-to-one conversation.</span></span> <span data-ttu-id="9712d-121">As conversas são manipuladas por meio do conector da Estrutura do Bot.</span><span class="sxs-lookup"><span data-stu-id="9712d-121">Conversations are handled through the Bot Framework connector.</span></span> <span data-ttu-id="9712d-122">Para obter mais informações, consulte [noções básicas de conversa.](~/bots/how-to/conversations/conversation-basics.md)</span><span class="sxs-lookup"><span data-stu-id="9712d-122">For more information, see [conversation basics](~/bots/how-to/conversations/conversation-basics.md).</span></span>

<span data-ttu-id="9712d-123">Seu bot exige informações contextuais, como detalhes do perfil do usuário para acessar conteúdo relevante e aprimorar a experiência do bot.</span><span class="sxs-lookup"><span data-stu-id="9712d-123">Your bot requires contextual information, such as user profile details to access relevant content and enhance the bot experience.</span></span> <span data-ttu-id="9712d-124">Para obter mais informações, consulte [get Teams context](~/bots/how-to/get-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="9712d-124">For more information, see [get Teams context](~/bots/how-to/get-teams-context.md).</span></span> 

<span data-ttu-id="9712d-125">Você também pode enviar e receber arquivos por meio do bot usando APIs do Graph ou APIs de bot do Teams.</span><span class="sxs-lookup"><span data-stu-id="9712d-125">You can also send and receive files through the bot using Graph APIs or Teams bot APIs.</span></span> <span data-ttu-id="9712d-126">Para obter mais informações, [consulte enviar e receber arquivos por meio do bot](~/bots/how-to/bots-filesv4.md).</span><span class="sxs-lookup"><span data-stu-id="9712d-126">For more information, see [send and receive files through the bot](~/bots/how-to/bots-filesv4.md).</span></span>

<span data-ttu-id="9712d-127">Além disso, o limite de taxas é usado para otimizar bots usados para seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="9712d-127">In addition, rate limiting is used to optimize bots used for your Teams application.</span></span> <span data-ttu-id="9712d-128">Para proteger o Microsoft Teams e seus usuários, as APIs de bot fornecem um limite de taxa para solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="9712d-128">To protect Microsoft Teams and its users, the bot APIs provide a rate limit for incoming requests.</span></span> <span data-ttu-id="9712d-129">Para obter mais informações, consulte [optimize your bot with rate limiting in Teams](~/bots/how-to/rate-limit.md).</span><span class="sxs-lookup"><span data-stu-id="9712d-129">For more information, see [optimize your bot with rate limiting in Teams](~/bots/how-to/rate-limit.md).</span></span>

<span data-ttu-id="9712d-130">Com APIs do Microsoft Graph para chamadas e reuniões online, os aplicativos do Microsoft Teams agora podem interagir com os usuários usando voz e vídeo.</span><span class="sxs-lookup"><span data-stu-id="9712d-130">With Microsoft Graph APIs for calls and online meetings, Microsoft Teams apps can now interact with users using voice and video.</span></span> <span data-ttu-id="9712d-131">Para obter mais informações, consulte [chamadas e reuniões bots](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9712d-131">For more information, see [calls and meetings bots](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span> 

<span data-ttu-id="9712d-132">Você pode usar as APIs de bot do Teams para obter informações para um ou mais membros de um chat ou equipe.</span><span class="sxs-lookup"><span data-stu-id="9712d-132">You can use the Teams bot APIs to get information for one or more members of a chat or team.</span></span> <span data-ttu-id="9712d-133">Para obter mais informações, consulte [changes to Teams bot APIs for fetching team or chat members](~/resources/team-chat-member-api-changes.md).</span><span class="sxs-lookup"><span data-stu-id="9712d-133">For more information, see [changes to Teams bot APIs for fetching team or chat members](~/resources/team-chat-member-api-changes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9712d-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="9712d-134">See also</span></span>

[<span data-ttu-id="9712d-135">Criar um bot para o Teams</span><span class="sxs-lookup"><span data-stu-id="9712d-135">Create a bot for Teams</span></span>](~/bots/how-to/create-a-bot-for-teams.md)

## <a name="next-step"></a><span data-ttu-id="9712d-136">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="9712d-136">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9712d-137">Bots e SDKs</span><span class="sxs-lookup"><span data-stu-id="9712d-137">Bots and SDKs</span></span>](~/bots/bot-features.md)
