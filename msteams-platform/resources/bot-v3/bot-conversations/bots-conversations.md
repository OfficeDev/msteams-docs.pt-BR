---
title: Enviar e receber mensagens com um bot
description: Descreve como enviar e receber mensagens com bots no Microsoft Teams
ms.topic: overview
keywords: mensagens de bots do Teams
ms.date: 05/20/2019
ms.openlocfilehash: 20c285a0cd06ac929d628edbc059b2a00b937eec
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014114"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a><span data-ttu-id="126a5-104">Conversar com um bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="126a5-104">Have a conversation with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="126a5-105">Uma conversa é uma série de mensagens enviadas entre seu bot e um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="126a5-105">A conversation is a series of messages sent between your bot and one or more users.</span></span> <span data-ttu-id="126a5-106">Há três tipos de conversas (também chamadas de escopos) no Teams:</span><span class="sxs-lookup"><span data-stu-id="126a5-106">There are three kinds of conversations (also called scopes) in Teams:</span></span>

* <span data-ttu-id="126a5-107">`teams` Também chamadas de conversas do canal, visíveis para todos os membros do canal.</span><span class="sxs-lookup"><span data-stu-id="126a5-107">`teams` Also called channel conversations, visible to all members of the channel.</span></span>
* <span data-ttu-id="126a5-108">`personal` Conversas entre bots e um único usuário.</span><span class="sxs-lookup"><span data-stu-id="126a5-108">`personal` Conversations between bots and a single user.</span></span>
* <span data-ttu-id="126a5-109">`groupChat` Chat entre um bot e dois ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="126a5-109">`groupChat` Chat between a bot and two or more users.</span></span>

<span data-ttu-id="126a5-110">Um bot se comporta de forma ligeiramente diferente, dependendo do tipo de conversa em que ele está envolvido:</span><span class="sxs-lookup"><span data-stu-id="126a5-110">A bot behaves slightly differently depending on what kind of conversation it is involved in:</span></span>

* <span data-ttu-id="126a5-111">[Bots em conversas de chat](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) em grupo e canal exigem que o usuário @ mencione o bot para invocá-lo em um canal.</span><span class="sxs-lookup"><span data-stu-id="126a5-111">[Bots in channel and group chat conversations](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="126a5-112">[Bots in single user conversations](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) do not require an @ mention - the user can just type.</span><span class="sxs-lookup"><span data-stu-id="126a5-112">[Bots in single user conversations](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) do not require an @ mention -  the user can just type.</span></span>

<span data-ttu-id="126a5-113">Para que o bot funcione em um escopo específico, ele deve estar listado como suporte a esse escopo no manifesto.</span><span class="sxs-lookup"><span data-stu-id="126a5-113">In order for the bot to work in a particular scope it should be listed as supporting that scope in the manifest.</span></span> <span data-ttu-id="126a5-114">Os escopos são definidos e discutidos ainda mais na Referência [de Manifesto.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="126a5-114">Scopes are defined and discussed further in the [Manifest Reference](~/resources/schema/manifest-schema.md).</span></span>

## <a name="proactive-messages"></a><span data-ttu-id="126a5-115">Mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="126a5-115">Proactive messages</span></span>

<span data-ttu-id="126a5-116">Os bots podem participar de uma conversa ou iniciar uma.</span><span class="sxs-lookup"><span data-stu-id="126a5-116">Bots can participate in a conversation or initiate one.</span></span> <span data-ttu-id="126a5-117">A maioria das comunicações é em resposta a outra mensagem.</span><span class="sxs-lookup"><span data-stu-id="126a5-117">Most communication is in response to another message.</span></span> <span data-ttu-id="126a5-118">Se um bot iniciar uma conversa, ele será chamado de *mensagem proativa.*</span><span class="sxs-lookup"><span data-stu-id="126a5-118">If a bot initiates a conversation it is called a *proactive message*.</span></span> <span data-ttu-id="126a5-119">Os exemplos incluem:</span><span class="sxs-lookup"><span data-stu-id="126a5-119">Examples include:</span></span>

* <span data-ttu-id="126a5-120">Mensagens de boas-vindas</span><span class="sxs-lookup"><span data-stu-id="126a5-120">Welcome messages</span></span>
* <span data-ttu-id="126a5-121">Notificações de evento</span><span class="sxs-lookup"><span data-stu-id="126a5-121">Event notifications</span></span>
* <span data-ttu-id="126a5-122">Sondagem de mensagens</span><span class="sxs-lookup"><span data-stu-id="126a5-122">Polling messages</span></span>

## <a name="conversation-basics"></a><span data-ttu-id="126a5-123">Noções básicas sobre conversas</span><span class="sxs-lookup"><span data-stu-id="126a5-123">Conversation basics</span></span>

<span data-ttu-id="126a5-124">Cada mensagem é um `Activity` objeto do tipo `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="126a5-124">Each message is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="126a5-125">Quando um usuário envia uma mensagem, o Teams envia a mensagem para seu bot; especificamente, ele envia um objeto JSON para o ponto de extremidade de mensagens do bot.</span><span class="sxs-lookup"><span data-stu-id="126a5-125">When a user sends a message, Teams posts the message to your bot; specifically, it sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="126a5-126">Seu bot examina a mensagem para determinar seu tipo e responde de acordo.</span><span class="sxs-lookup"><span data-stu-id="126a5-126">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="126a5-127">Os bots também suportam mensagens de estilo de evento.</span><span class="sxs-lookup"><span data-stu-id="126a5-127">Bots also support event-style messages.</span></span> <span data-ttu-id="126a5-128">Confira [Manipular eventos de bot no Microsoft Teams](~/resources/bot-v3/bots-notifications.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="126a5-128">See [Handle bot events in Microsoft Teams](~/resources/bot-v3/bots-notifications.md) for more details.</span></span> <span data-ttu-id="126a5-129">Não há suporte para fala no momento.</span><span class="sxs-lookup"><span data-stu-id="126a5-129">Speech is currently not supported.</span></span>

<span data-ttu-id="126a5-130">As mensagens são, em grande parte, as mesmas em todos os escopos, mas há diferenças em como o bot é acessado na interface do usuário e diferenças nos bastidores que você precisará saber.</span><span class="sxs-lookup"><span data-stu-id="126a5-130">Messages are for the most part the same in across all scopes, but there are differences in how the bot is accessed in the UI and differences behind the scenes which you will need to know about.</span></span>

<span data-ttu-id="126a5-131">A conversa básica é manipulada por meio do Bot Framework Connector, uma única API REST para permitir que seu bot se comunique com o Teams e outros canais.</span><span class="sxs-lookup"><span data-stu-id="126a5-131">Basic conversation is handled through the Bot Framework Connector, a single REST API to enable your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="126a5-132">O SDK do Construtor de Bots fornece acesso fácil a essa API, funcionalidade adicional para gerenciar o fluxo e o estado da conversa e maneiras simples de incorporar serviços cognitivas, como processamento de linguagem natural (NLP).</span><span class="sxs-lookup"><span data-stu-id="126a5-132">The Bot Builder SDK provides easy access to this API, additional functionality to manage conversation flow and state, and simple ways to incorporate cognitive services such as natural language processing (NLP).</span></span>

## <a name="message-content"></a><span data-ttu-id="126a5-133">Conteúdo da mensagem</span><span class="sxs-lookup"><span data-stu-id="126a5-133">Message content</span></span>

<span data-ttu-id="126a5-134">Seu bot pode enviar rich text, imagens e cartões.</span><span class="sxs-lookup"><span data-stu-id="126a5-134">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="126a5-135">Os usuários podem enviar rich text e imagens para seu bot.</span><span class="sxs-lookup"><span data-stu-id="126a5-135">Users can send rich text and pictures to your bot.</span></span> <span data-ttu-id="126a5-136">Você pode especificar o tipo de conteúdo que seu bot pode manipular na página de configurações do Microsoft Teams para seu bot.</span><span class="sxs-lookup"><span data-stu-id="126a5-136">You can specify the type of content your bot can handle in the Microsoft Teams settings page for your bot.</span></span>

| <span data-ttu-id="126a5-137">Formatar</span><span class="sxs-lookup"><span data-stu-id="126a5-137">Format</span></span> | <span data-ttu-id="126a5-138">De usuário para bot</span><span class="sxs-lookup"><span data-stu-id="126a5-138">From user to bot</span></span>  | <span data-ttu-id="126a5-139">De bot para usuário</span><span class="sxs-lookup"><span data-stu-id="126a5-139">From bot to user</span></span> |  <span data-ttu-id="126a5-140">Observações</span><span class="sxs-lookup"><span data-stu-id="126a5-140">Notes</span></span> |
| --- | :---: | :---: | --- |
| <span data-ttu-id="126a5-141">Rich text </span><span class="sxs-lookup"><span data-stu-id="126a5-141">Rich text</span></span> | <span data-ttu-id="126a5-142">✔</span><span class="sxs-lookup"><span data-stu-id="126a5-142">✔</span></span> | <span data-ttu-id="126a5-143">✔</span><span class="sxs-lookup"><span data-stu-id="126a5-143">✔</span></span> |  |
| <span data-ttu-id="126a5-144">Imagens</span><span class="sxs-lookup"><span data-stu-id="126a5-144">Pictures</span></span> | <span data-ttu-id="126a5-145">✔</span><span class="sxs-lookup"><span data-stu-id="126a5-145">✔</span></span> | <span data-ttu-id="126a5-146">✔</span><span class="sxs-lookup"><span data-stu-id="126a5-146">✔</span></span> | <span data-ttu-id="126a5-147">Máximo de 1024×1024 e 1 MB em formato PNG, JPEG ou GIF; NÃO há suporte para GIF animado</span><span class="sxs-lookup"><span data-stu-id="126a5-147">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF are not supported</span></span> |
| <span data-ttu-id="126a5-148">Cartões</span><span class="sxs-lookup"><span data-stu-id="126a5-148">Cards</span></span> | <span data-ttu-id="126a5-149">✖</span><span class="sxs-lookup"><span data-stu-id="126a5-149">✖</span></span> | <span data-ttu-id="126a5-150">✔</span><span class="sxs-lookup"><span data-stu-id="126a5-150">✔</span></span> | <span data-ttu-id="126a5-151">Confira a Referência [de Cartão do Teams](~/task-modules-and-cards/cards/cards-reference.md) para cartões com suporte</span><span class="sxs-lookup"><span data-stu-id="126a5-151">See the [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards</span></span> |
| <span data-ttu-id="126a5-152">Emojis</span><span class="sxs-lookup"><span data-stu-id="126a5-152">Emojis</span></span> | <span data-ttu-id="126a5-153">✖</span><span class="sxs-lookup"><span data-stu-id="126a5-153">✖</span></span> | <span data-ttu-id="126a5-154">✔</span><span class="sxs-lookup"><span data-stu-id="126a5-154">✔</span></span> | <span data-ttu-id="126a5-155">No momento, o Teams dá suporte a emojis via UTF-16 (como U+1F600 para face de operação)</span><span class="sxs-lookup"><span data-stu-id="126a5-155">Teams currently supports emojis via UTF-16 (such as U+1F600 for grinning face)</span></span> |
|

<span data-ttu-id="126a5-156">Para obter mais informações sobre os tipos de interação de bot com suporte na Estrutura de [](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0) Bot (em que os bots nas equipes se baseiam), consulte a documentação do Bot Framework sobre o fluxo de conversas e os conceitos relacionados na documentação do [SDK](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0) do Construtor de Bots para .NET e do [SDK ](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0)do Bot Builder para Node.js.</span><span class="sxs-lookup"><span data-stu-id="126a5-156">For more information on the types of bot interaction supported by the Bot Framework (which bots in teams are based on), see the Bot Framework documentation on [conversation flow](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0) and related concepts in the documentation for [the Bot Builder SDK for .NET](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0) and [the Bot Builder SDK for Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0).</span></span>

## <a name="message-formatting"></a><span data-ttu-id="126a5-157">Formatação de mensagem</span><span class="sxs-lookup"><span data-stu-id="126a5-157">Message formatting</span></span>

<span data-ttu-id="126a5-158">Você pode definir a propriedade [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) opcional de um para controlar como o conteúdo de texto da mensagem é `message` renderizado.</span><span class="sxs-lookup"><span data-stu-id="126a5-158">You can set the optional [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) property of a `message` to control how your message's text content is rendered.</span></span> <span data-ttu-id="126a5-159">Consulte [Formatação de mensagem](~/resources/bot-v3/bots-message-format.md) para uma descrição detalhada da formatação com suporte em mensagens de bot.</span><span class="sxs-lookup"><span data-stu-id="126a5-159">See [Message formatting](~/resources/bot-v3/bots-message-format.md) for a detailed description of supported formatting in bot messages.</span></span>
<span data-ttu-id="126a5-160">Você pode definir a propriedade [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) opcional para controlar como o conteúdo de texto da mensagem é renderizado.</span><span class="sxs-lookup"><span data-stu-id="126a5-160">You can set the optional [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) property to control how your message's text content is rendered.</span></span>

<span data-ttu-id="126a5-161">Para obter informações detalhadas sobre como o Teams dá suporte à formatação de texto em equipes, consulte [Formatação de texto em mensagens de bot.](~/resources/bot-v3/bots-text-formats.md)</span><span class="sxs-lookup"><span data-stu-id="126a5-161">For detailed information on how Teams supports text formatting in teams see [Text formatting in bot messages](~/resources/bot-v3/bots-text-formats.md).</span></span>

<span data-ttu-id="126a5-162">Para obter informações sobre a formatação de cartões em mensagens, consulte [Formatação de cartão.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="126a5-162">For information on formatting cards in messages, see [Card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

## <a name="picture-messages"></a><span data-ttu-id="126a5-163">Mensagens de imagem</span><span class="sxs-lookup"><span data-stu-id="126a5-163">Picture messages</span></span>

<span data-ttu-id="126a5-164">Imagens são enviadas adicionando anexos a uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="126a5-164">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="126a5-165">Você pode encontrar mais informações sobre anexos na documentação [do Bot Framework.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0)</span><span class="sxs-lookup"><span data-stu-id="126a5-165">You can find more information on attachments in the [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0).</span></span>

<span data-ttu-id="126a5-166">As imagens podem ter no máximo 1024×1024 e 1 MB em formato PNG, JPEG ou GIF; NÃO há suporte para GIF animado.</span><span class="sxs-lookup"><span data-stu-id="126a5-166">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF is not supported.</span></span>

<span data-ttu-id="126a5-167">Recomendamos que você especifique a altura e a largura de cada imagem usando XML.</span><span class="sxs-lookup"><span data-stu-id="126a5-167">We recommend that you specify the height and width of each image by using XML.</span></span> <span data-ttu-id="126a5-168">Se você usar Markdown, o tamanho da imagem será padrão 256×256.</span><span class="sxs-lookup"><span data-stu-id="126a5-168">If you use Markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="126a5-169">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="126a5-169">For example:</span></span>

* <span data-ttu-id="126a5-170">Usar o `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span><span class="sxs-lookup"><span data-stu-id="126a5-170">Use `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span></span>
* <span data-ttu-id="126a5-171">Não usar `![Duck on a rock](http://aka.ms/Fo983c)`</span><span class="sxs-lookup"><span data-stu-id="126a5-171">Don't use `![Duck on a rock](http://aka.ms/Fo983c)`</span></span>

## <a name="receiving-messages"></a><span data-ttu-id="126a5-172">Receber mensagens</span><span class="sxs-lookup"><span data-stu-id="126a5-172">Receiving messages</span></span>

<span data-ttu-id="126a5-173">Dependendo de quais escopos são declarados, seu bot pode receber mensagens nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="126a5-173">Depending on which scopes are declared, your bot can receive messages in the following contexts:</span></span>

* <span data-ttu-id="126a5-174">**personal chat** Os usuários podem interagir em uma conversa privada com um bot simplesmente selecionando o bot adicionado no histórico de chat ou digitando seu nome ou ID do aplicativo na caixa Para: em um novo chat.</span><span class="sxs-lookup"><span data-stu-id="126a5-174">**personal chat** Users can interact in a private conversation with a bot by simply selecting the added bot in the chat history, or typing its name or app ID in the To: box on a new chat.</span></span>
* <span data-ttu-id="126a5-175">**Canais** Um bot pode ser mencionado ("@_botname_") em um canal se ele tiver sido adicionado à equipe.</span><span class="sxs-lookup"><span data-stu-id="126a5-175">**Channels** A bot can be mentioned ("@_botname_") in a channel if it has been added to the team.</span></span> <span data-ttu-id="126a5-176">Observe que respostas adicionais a um bot em um canal exigem a menção do bot.</span><span class="sxs-lookup"><span data-stu-id="126a5-176">Note that additional replies to a bot in a channel require mentioning the bot.</span></span> <span data-ttu-id="126a5-177">Ele não responderá às respostas onde não for mencionado.</span><span class="sxs-lookup"><span data-stu-id="126a5-177">It will not respond to replies where it is not mentioned.</span></span>

<span data-ttu-id="126a5-178">Para mensagens de entrada, seu bot recebe um [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0) objeto do tipo `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="126a5-178">For incoming messages, your bot receives an [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0) object of type `messageType: message`.</span></span> <span data-ttu-id="126a5-179">Embora o objeto possa conter outros tipos de informações, como atualizações de canal enviadas para seu bot, o tipo representa a comunicação `Activity` entre o bot e o [](~/resources/bot-v3/bots-notifications.md#channel-updates) `message` usuário.</span><span class="sxs-lookup"><span data-stu-id="126a5-179">Although the `Activity` object can contain other types of information, like [channel updates](~/resources/bot-v3/bots-notifications.md#channel-updates) sent to your bot, the `message` type represents communication between bot and user.</span></span>

<span data-ttu-id="126a5-180">Seu bot recebe uma carga que contém a mensagem do usuário, bem como outras informações sobre o usuário, a origem da mensagem e `Text` informações do Teams.</span><span class="sxs-lookup"><span data-stu-id="126a5-180">Your bot receives a payload that contains the user message `Text` as well as other information about the user, the source of the message, and Teams information.</span></span> <span data-ttu-id="126a5-181">Observação:</span><span class="sxs-lookup"><span data-stu-id="126a5-181">Of note:</span></span>

* <span data-ttu-id="126a5-182">`timestamp` A data e a hora da mensagem em UTC (Tempo Universal Coordenado)</span><span class="sxs-lookup"><span data-stu-id="126a5-182">`timestamp` The date and time of the message in Coordinated Universal Time (UTC)</span></span>
* <span data-ttu-id="126a5-183">`localTimestamp` A data e a hora da mensagem no fuso horário do remetente</span><span class="sxs-lookup"><span data-stu-id="126a5-183">`localTimestamp` The date and time of the message in the time zone of the sender</span></span>
* <span data-ttu-id="126a5-184">`channelId` Sempre "msteams".</span><span class="sxs-lookup"><span data-stu-id="126a5-184">`channelId` Always "msteams".</span></span> <span data-ttu-id="126a5-185">Isso se refere a um canal de estrutura de bot, não a um canal do Teams.</span><span class="sxs-lookup"><span data-stu-id="126a5-185">This refers to a bot framework channel, not a teams channel.</span></span>
* <span data-ttu-id="126a5-186">`from.id` Uma ID exclusiva e criptografada para esse usuário para seu bot; adequado como uma chave se seu aplicativo precisar armazenar dados do usuário.</span><span class="sxs-lookup"><span data-stu-id="126a5-186">`from.id` A unique and encrypted ID for that user for your bot; suitable as a key if your app needs to store user data.</span></span> <span data-ttu-id="126a5-187">Ele é exclusivo para seu bot e não pode ser usado diretamente fora da instância do bot de maneira significativa para identificar esse usuário</span><span class="sxs-lookup"><span data-stu-id="126a5-187">It is unique for your bot and cannot be directly used outside your bot instance in any meaningful way to identify that user</span></span>
* <span data-ttu-id="126a5-188">`channelData.tenant.id` A ID de locatário do usuário.</span><span class="sxs-lookup"><span data-stu-id="126a5-188">`channelData.tenant.id` The tenant ID for the user.</span></span>

> [!NOTE]
> <span data-ttu-id="126a5-189">`from.id` é exclusivo para seu bot e não pode ser usado diretamente fora da instância do bot de maneira significativa para identificar esse usuário.</span><span class="sxs-lookup"><span data-stu-id="126a5-189">`from.id` is unique for your bot and cannot be directly used outside your bot instance in any meaningful way to identify that user.</span></span>

## <a name="combining-channel-and-private-interactions-with-your-bot"></a><span data-ttu-id="126a5-190">Combinando canal e interações privadas com seu bot</span><span class="sxs-lookup"><span data-stu-id="126a5-190">Combining channel and private interactions with your bot</span></span>

<span data-ttu-id="126a5-191">Ao interagir em um canal, seu bot deve ser inteligente em tirar determinadas conversas offline com um usuário.</span><span class="sxs-lookup"><span data-stu-id="126a5-191">When interacting in a channel, your bot should be smart about taking certain conversations offline with a user.</span></span> <span data-ttu-id="126a5-192">Por exemplo, suponha que um usuário está tentando coordenar uma tarefa complexa, como o agendamento com um conjunto de membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="126a5-192">For instance, suppose a user is trying to coordinate a complex task, such as scheduling with a set of team members.</span></span> <span data-ttu-id="126a5-193">Em vez de ter toda a sequência de interações visíveis para o canal, considere enviar uma mensagem de chat pessoal para o usuário.</span><span class="sxs-lookup"><span data-stu-id="126a5-193">Rather than have the entire sequence of interactions visible to the channel, consider sending a personal chat message to the user.</span></span> <span data-ttu-id="126a5-194">Seu bot deve ser capaz de fazer a transição fácil do usuário entre conversas pessoais e de canal sem perder o estado.</span><span class="sxs-lookup"><span data-stu-id="126a5-194">Your bot should be able to easily transition the user between personal and channel conversations without losing state.</span></span>

> [!NOTE]
><span data-ttu-id="126a5-195">Não se esqueça de atualizar o canal quando a interação for concluída para notificar os outros membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="126a5-195">Don’t forget to update the channel when the interaction is complete to notify the other team members.</span></span>

## <a name="full-inbound-schema-example"></a><span data-ttu-id="126a5-196">Exemplo de esquema de entrada completo</span><span class="sxs-lookup"><span data-stu-id="126a5-196">Full inbound schema example</span></span>

```json
{
    "type": "message",
    "id": "1485983408511",
    "timestamp": "2017-02-01T21:10:07.437Z",
    "localTimestamp": "2017-02-01T14:10:07.437-07:00",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "channelId": "msteams",
    "from": {
        "id": "29:1XJKJMvc5GBtc2JwZq0oj8tHZmzrQgFmB39ATiQWA85gQtHieVkKilBZ9XHoq9j7Zaqt7CZ-NJWi7me2kHTL3Bw",
        "name": "Megan Bowen",
        "aadObjectId": "7faf8ab2-3d56-4244-b585-20c8a42ed2b8"
    },
    "conversation": {
        "conversationType": "personal",
        "id": "a:17I0kl9EkpE1O9PH5TWrzrLNwnWWcfrU7QZjKR0WSfOpzbfcAg2IaydGElSo10tVr4C7Fc6GtieTJX663WuJCc1uA83n4CSrHSgGBj5XNYLcVlJAs2ZX8DbYBPck201w-"
    },
    "recipient": {
        "id": "28:c9e8c047-2a74-40a2-b28a-b162d5f5327c",
        "name": "Teams TestBot"
    },
    "textFormat": "plain",
    "text": "Hello Teams TestBot",
    "entities": [
      { 
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "America/Los_Angeles",
        "type": "clientInfo"
      }
    ],
    "channelData": {
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "locale": "en-US"
}
```

> [!NOTE]
> <span data-ttu-id="126a5-197">Às vezes, o campo de texto para mensagens de entrada contém menções.</span><span class="sxs-lookup"><span data-stu-id="126a5-197">The text field for inbound messages sometimes contains mentions.</span></span> <span data-ttu-id="126a5-198">Certifique-se de verificar e retirar corretamente.</span><span class="sxs-lookup"><span data-stu-id="126a5-198">Be sure to properly check and strip those.</span></span> <span data-ttu-id="126a5-199">Para obter mais informações, consulte [Menções.](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions)</span><span class="sxs-lookup"><span data-stu-id="126a5-199">For more information, see [Mentions](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).</span></span>

## <a name="teams-channel-data"></a><span data-ttu-id="126a5-200">Dados de canal do Teams</span><span class="sxs-lookup"><span data-stu-id="126a5-200">Teams channel data</span></span>

<span data-ttu-id="126a5-201">O `channelData` objeto contém informações específicas do Teams e é a fonte definitiva para IDs de equipe e canal.</span><span class="sxs-lookup"><span data-stu-id="126a5-201">The `channelData` object contains Teams-specific information and is the definitive source for team and channel IDs.</span></span> <span data-ttu-id="126a5-202">Você deve armazenar em cache e usar essas IDs como chaves para armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="126a5-202">You should cache and use these ids as keys for local storage.</span></span>

<span data-ttu-id="126a5-203">O `channelData` objeto não está incluído em mensagens em conversas pessoais, pois elas ocorrem fora de qualquer canal.</span><span class="sxs-lookup"><span data-stu-id="126a5-203">The `channelData` object is not included in messages in personal conversations since these take place outside of any channel.</span></span>

<span data-ttu-id="126a5-204">Um objeto channelData típico em uma atividade enviada ao seu bot contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="126a5-204">A typical channelData object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="126a5-205">`eventType` Tipo de evento do Teams; passado somente em casos de eventos [de modificação de canal](~/resources/bot-v3/bots-notifications.md#channel-updates)</span><span class="sxs-lookup"><span data-stu-id="126a5-205">`eventType` Teams event type; passed only in cases of [channel modification events](~/resources/bot-v3/bots-notifications.md#channel-updates)</span></span>
* <span data-ttu-id="126a5-206">`tenant.id` ID de locatário do Azure Active Directory; passado em todos os contextos</span><span class="sxs-lookup"><span data-stu-id="126a5-206">`tenant.id` Azure Active Directory tenant ID; passed in all contexts</span></span>
* <span data-ttu-id="126a5-207">`team` Passado somente em contextos de canal, não em bate-papo pessoal.</span><span class="sxs-lookup"><span data-stu-id="126a5-207">`team` Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="126a5-208">`id` GUID do canal</span><span class="sxs-lookup"><span data-stu-id="126a5-208">`id` GUID for the channel</span></span>
  * <span data-ttu-id="126a5-209">`name` Nome da equipe; passado somente em casos de [eventos de renomear equipe](~/resources/bot-v3/bots-notifications.md#team-name-updates)</span><span class="sxs-lookup"><span data-stu-id="126a5-209">`name` Name of the team; passed only in cases of [team rename events](~/resources/bot-v3/bots-notifications.md#team-name-updates)</span></span>
* <span data-ttu-id="126a5-210">`channel` Passado somente em contextos de canal quando o bot é mencionado ou para eventos em canais em equipes onde o bot foi adicionado</span><span class="sxs-lookup"><span data-stu-id="126a5-210">`channel` Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added</span></span>
  * <span data-ttu-id="126a5-211">`id` GUID do canal</span><span class="sxs-lookup"><span data-stu-id="126a5-211">`id` GUID for the channel</span></span>
  * <span data-ttu-id="126a5-212">`name`Nome do canal; passado somente em casos de eventos [de modificação de canal.](~/resources/bot-v3/bots-notifications.md#channel-updates)</span><span class="sxs-lookup"><span data-stu-id="126a5-212">`name` Channel name; passed only in cases of [channel modification events](~/resources/bot-v3/bots-notifications.md#channel-updates).</span></span>
* <span data-ttu-id="126a5-213">`channelData.teamsTeamId` Preterido.</span><span class="sxs-lookup"><span data-stu-id="126a5-213">`channelData.teamsTeamId` Deprecated.</span></span> <span data-ttu-id="126a5-214">Essa propriedade é incluída somente para compatibilidade com compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="126a5-214">This property is included only for backwards compatibility.</span></span>
* <span data-ttu-id="126a5-215">`channelData.teamsChannelId` Preterido.</span><span class="sxs-lookup"><span data-stu-id="126a5-215">`channelData.teamsChannelId` Deprecated.</span></span> <span data-ttu-id="126a5-216">Essa propriedade é incluída somente para compatibilidade com compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="126a5-216">This property is included only for backwards compatibility.</span></span>

### <a name="example-channeldata-object-channelcreated-event"></a><span data-ttu-id="126a5-217">Objeto channelData de exemplo (evento channelCreated)</span><span class="sxs-lookup"><span data-stu-id="126a5-217">Example channelData object (channelCreated event)</span></span>

```json
"channelData": {
    "eventType": "channelCreated",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    },
    "channel": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype",
        "name": "My New Channel"
    },
    "team": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype"
    }
}
```

### <a name="net-example"></a><span data-ttu-id="126a5-218">Exemplo de .NET</span><span class="sxs-lookup"><span data-stu-id="126a5-218">.NET example</span></span>

<span data-ttu-id="126a5-219">O [pacote NuGet Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) fornece um objeto especializado, que expõe propriedades para acessar informações `TeamsChannelData` específicas do Teams.</span><span class="sxs-lookup"><span data-stu-id="126a5-219">The [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package provides a specialized `TeamsChannelData` object, which exposes properties to access Teams-specific information.</span></span>

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a><span data-ttu-id="126a5-220">Enviar respostas a mensagens</span><span class="sxs-lookup"><span data-stu-id="126a5-220">Sending replies to messages</span></span>

<span data-ttu-id="126a5-221">Para responder a uma mensagem existente, chame [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_) no .NET ou [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities) no Node.js.</span><span class="sxs-lookup"><span data-stu-id="126a5-221">To reply to an existing message, call [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_) in .NET or [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities) in Node.js.</span></span> <span data-ttu-id="126a5-222">O SDK do Construtor de Bots lida com todos os detalhes.</span><span class="sxs-lookup"><span data-stu-id="126a5-222">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="126a5-223">Se você optar por usar a API REST, também poderá chamar o [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0) ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="126a5-223">If you choose to use the REST API, you can also call the [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0) endpoint.</span></span>

<span data-ttu-id="126a5-224">O conteúdo da mensagem em si pode conter texto simples ou algumas das ações de cartão e cartões fornecidas pelo Bot [Framework.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="126a5-224">The message content itself can contain simple text or some of the Bot Framework supplied [cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

<span data-ttu-id="126a5-225">Observe que, em seu esquema de saída, você sempre deve usar o mesmo `serviceUrl` que o que recebeu.</span><span class="sxs-lookup"><span data-stu-id="126a5-225">Please note that in your outbound schema you should always use the same `serviceUrl` as the one you received.</span></span> <span data-ttu-id="126a5-226">Esteja ciente de que o valor `serviceUrl` tende a ser estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="126a5-226">Be aware that the value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="126a5-227">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado de `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="126a5-227">When a new message arrives, your bot should verify its stored value of `serviceUrl`.</span></span>

## <a name="updating-messages"></a><span data-ttu-id="126a5-228">Atualizando mensagens</span><span class="sxs-lookup"><span data-stu-id="126a5-228">Updating messages</span></span>

<span data-ttu-id="126a5-229">Em vez de suas mensagens serem instantâneos estáticos de dados, seu bot pode atualizar dinamicamente as mensagens em linha depois de enviá-las.</span><span class="sxs-lookup"><span data-stu-id="126a5-229">Rather than have your messages be static snapshots of data, your bot can dynamically update messages inline after sending them.</span></span> <span data-ttu-id="126a5-230">Você pode usar atualizações dinâmicas de mensagens para cenários como atualizações de votação, modificação de ações disponíveis após um pressionamento de botão ou qualquer outra alteração de estado assíncrona.</span><span class="sxs-lookup"><span data-stu-id="126a5-230">You can use dynamic message updates for scenarios such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="126a5-231">A nova mensagem não precisa corresponder ao tipo original.</span><span class="sxs-lookup"><span data-stu-id="126a5-231">The new message need not match the original in type.</span></span> <span data-ttu-id="126a5-232">Por exemplo, se a mensagem original continha um anexo, a nova mensagem pode ser uma mensagem de texto simples.</span><span class="sxs-lookup"><span data-stu-id="126a5-232">For instance, if the original message contained an attachment, the new message can be a simple text message.</span></span>

> [!NOTE]
> <span data-ttu-id="126a5-233">Você pode atualizar somente o conteúdo enviado em mensagens de anexo único e layouts de carrossel.</span><span class="sxs-lookup"><span data-stu-id="126a5-233">You can update only content sent in single-attachment messages and carousel layouts.</span></span> <span data-ttu-id="126a5-234">Não há suporte para postagem de atualizações em mensagens com vários anexos no layout de lista.</span><span class="sxs-lookup"><span data-stu-id="126a5-234">Posting updates to messages with multiple attachments in list layout is not supported.</span></span>

### <a name="rest-api"></a><span data-ttu-id="126a5-235">API REST</span><span class="sxs-lookup"><span data-stu-id="126a5-235">REST API</span></span>

<span data-ttu-id="126a5-236">Para emitir uma atualização de mensagem, basta executar uma solicitação PUT contra o ponto de extremidade `/v3/conversations/<conversationId>/activities/<activityId>/` usando uma determinada ID de atividade.</span><span class="sxs-lookup"><span data-stu-id="126a5-236">To issue a message update, simply perform a PUT request against the `/v3/conversations/<conversationId>/activities/<activityId>/` endpoint using a given activity ID.</span></span> <span data-ttu-id="126a5-237">Para concluir esse cenário, você deve armazenar em cache a ID de atividade retornada pela chamada POST original.</span><span class="sxs-lookup"><span data-stu-id="126a5-237">To complete this scenario, you should cache the activity ID returned by the original POST call.</span></span>

```json
PUT /v3/conversations/19%3Aja0cu120i1jod12j%40skype.net/activities/012ujdo0128
{
    "type": "message",
    "text": "This message has been updated"
}
```

### <a name="net-example"></a><span data-ttu-id="126a5-238">Exemplo de .NET</span><span class="sxs-lookup"><span data-stu-id="126a5-238">.NET example</span></span>

<span data-ttu-id="126a5-239">Você pode usar `UpdateActivityAsync` o método no SDK do Construtor de Bots para atualizar uma mensagem existente.</span><span class="sxs-lookup"><span data-stu-id="126a5-239">You can use the `UpdateActivityAsync` method in the Bot Builder SDK to update an existing message.</span></span>

```csharp
public async Task<HttpResponseMessage> Post([FromBody]Activity activity)
{
  if (activity.Type == ActivityTypes.Message)
  {
    ConnectorClient connector = new ConnectorClient(new Uri(activity.ServiceUrl));
    Activity reply = activity.CreateReply($"You sent {activity.Text} which was {activity.Text.Length} characters");
    var msgToUpdate = await connector.Conversations.ReplyToActivityAsync(reply);
    Activity updatedReply = activity.CreateReply($"This is an updated message");
    await connector.Conversations.UpdateActivityAsync(reply.Conversation.Id, msgToUpdate.Id, updatedReply);
  }
}
```

### <a name="nodejs-example"></a><span data-ttu-id="126a5-240">Node.js exemplo</span><span class="sxs-lookup"><span data-stu-id="126a5-240">Node.js example</span></span>

<span data-ttu-id="126a5-241">Você pode usar o `session.connector.update` método no SDK do Construtor de Bots para atualizar uma mensagem existente.</span><span class="sxs-lookup"><span data-stu-id="126a5-241">You can use the `session.connector.update` method in the Bot Builder SDK to update an existing message.</span></span>

```javascript
function sendCardUpdate(bot, session, originalMessage, address) {

  var origAttachment = originalMessage.data.attachments[0];
  origAttachment.content.subtitle = 'Assigned to Larry Jin';

  var updatedMsg = new builder.Message()
    .address(address)
    .textFormat(builder.TextFormat.markdown)
    .addAttachment(origAttachment)
    .toMessage();

  session.connector.update(updatedMsg, function(err, addresses) {
    if (err) {
      console.log(`Could not update the message`);
    }
  });
}
```

## <a name="starting-a-conversation-proactive-messaging"></a><span data-ttu-id="126a5-242">Iniciando uma conversa (mensagens proativas)</span><span class="sxs-lookup"><span data-stu-id="126a5-242">Starting a conversation (proactive messaging)</span></span>

<span data-ttu-id="126a5-243">Você pode criar uma conversa pessoal com um usuário ou iniciar uma nova cadeia de resposta em um canal para seu bot de equipe.</span><span class="sxs-lookup"><span data-stu-id="126a5-243">You can create a personal conversation with a user or start a new reply chain in a channel for your team bot.</span></span> <span data-ttu-id="126a5-244">Isso permite que você mensagem seu usuário ou usuários sem que eles iniciem primeiro contato com seu bot.</span><span class="sxs-lookup"><span data-stu-id="126a5-244">This lets you to message your user or users without having them first initiate contact with your bot.</span></span> <span data-ttu-id="126a5-245">Para mais informações, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="126a5-245">For more information, see the following topics:</span></span>

<span data-ttu-id="126a5-246">Consulte [Mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para obter mais informações gerais sobre conversas iniciadas por bots.</span><span class="sxs-lookup"><span data-stu-id="126a5-246">See [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) for more general information on conversations started by bots.</span></span>

## <a name="deleting-messages"></a><span data-ttu-id="126a5-247">Excluir mensagens</span><span class="sxs-lookup"><span data-stu-id="126a5-247">Deleting messages</span></span>

<span data-ttu-id="126a5-248">As mensagens podem ser excluídas usando o método [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) de conectores no [SDK do BotBuilder.](/bot-framework/bot-builder-overview-getstarted)</span><span class="sxs-lookup"><span data-stu-id="126a5-248">Messages can be deleted using the connectors [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) method in the [BotBuilder SDK](/bot-framework/bot-builder-overview-getstarted).</span></span>

```typescript
bot.dialog('BotDeleteMessage', function (session: builder.Session) {
  var msg = new teams.TeamsMessage(session).text("Bot will delete this message in 5 sec.")
  bot.send(msg, function (err, response) {
    if (err) {
      console.log(err);
      session.endDialog();
    }

    console.log('Proactive message response:');
    console.log(response);
    console.log('---------------------------------------------------')
    setTimeout(function () {
      var activityId: string = null;
      var messageAddress: builder.IChatConnectorAddress = null;
      if (response[0]){
        messageAddress = response[0];
        activityId = messageAddress.id;
      }

      if (activityId == null)
      {
        console.log('Message failed to send.');
        session.endDialog();
        return;
      }

      // Bot delete message
      let address: builder.IChatConnectorAddress  = {
        channelId: 'msteams',
        user: messageAddress.user,
        bot: messageAddress.bot,
        id : activityId,
        serviceUrl : (<builder.IChatConnectorAddress>session.message.address).serviceUrl,
        conversation: {
          id: session.message.address.conversation.id
        }
      };

      connector.delete(address, function (err) {
        if (err)
        {
          console.log(err);
        }
        else
        {
          console.log("Message: " + activityId + " deleted successfully.");
        }

        // Try editing deleted message would fail
        var newMsg = new builder.Message().address(address).text("To edit message.");
        connector.update(newMsg.toMessage(), function (err, address) {
          if (err)
          {
            console.log(err);
            console.log('Deleted message can not be edited.');
          }
          else
          {
            console.log("There is something wrong. Message: " + activityId + " edited successfully.");
            console.log(address);
          }

          session.endDialog();
        });
      });
    }, 5000);
  });
})
```
