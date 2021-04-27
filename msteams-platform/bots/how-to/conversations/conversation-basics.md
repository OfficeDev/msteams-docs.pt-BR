---
title: Noções básicas sobre conversas
description: Introdução às conversas
ms.topic: overview
ms.author: anclear
localization_priority: Normal
keyword: conversations basics messages
ms.openlocfilehash: c06f8765ae17f28f3abb1dff67d77aad4e76958c
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020032"
---
# <a name="conversation-basics"></a><span data-ttu-id="1ee54-103">Noções básicas sobre conversas</span><span class="sxs-lookup"><span data-stu-id="1ee54-103">Conversation basics</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="1ee54-104">Uma conversa é uma série de mensagens enviadas entre o bot do Microsoft Teams e um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="1ee54-104">A conversation is a series of messages sent between your Microsoft Teams bot and one or more users.</span></span> <span data-ttu-id="1ee54-105">A tabela a seguir fornece os três tipos de conversas, também chamados de escopos no Teams:</span><span class="sxs-lookup"><span data-stu-id="1ee54-105">The following table provides the three types of conversations, also called scopes in Teams:</span></span>

| <span data-ttu-id="1ee54-106">Tipo de conversa</span><span class="sxs-lookup"><span data-stu-id="1ee54-106">Conversation type</span></span> | <span data-ttu-id="1ee54-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ee54-107">Description</span></span> |
| ------- | ----------- |
| `channel` | <span data-ttu-id="1ee54-108">Esse tipo de conversa é visível para todos os membros do canal.</span><span class="sxs-lookup"><span data-stu-id="1ee54-108">This conversation type is visible to all members of the channel.</span></span> |
| `personal` | <span data-ttu-id="1ee54-109">Esse tipo de conversa inclui conversas entre bots e um único usuário.</span><span class="sxs-lookup"><span data-stu-id="1ee54-109">This conversation type includes conversations between bots and a single user.</span></span> |
| `groupChat` | <span data-ttu-id="1ee54-110">Esse tipo de conversa inclui chat entre um bot e dois ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="1ee54-110">This conversation type includes chat between a bot and two or more users.</span></span> <span data-ttu-id="1ee54-111">Ele também habilita seu bot em chats de reunião.</span><span class="sxs-lookup"><span data-stu-id="1ee54-111">It also enables your bot in meeting chats.</span></span> |

<span data-ttu-id="1ee54-112">Um bot se comporta de forma diferente, dependendo da conversa em que ele está envolvido:</span><span class="sxs-lookup"><span data-stu-id="1ee54-112">A bot behaves differently depending on the conversation it is involved in:</span></span>

* <span data-ttu-id="1ee54-113">Bots em conversas de chat de canal e grupo exigem que o usuário @ mencione o bot para invocá-lo em um canal.</span><span class="sxs-lookup"><span data-stu-id="1ee54-113">Bots in channel and group chat conversations require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="1ee54-114">Bots em uma conversa um para um não exigem uma menção @.</span><span class="sxs-lookup"><span data-stu-id="1ee54-114">Bots in a one-to-one conversation do not require an @ mention.</span></span> <span data-ttu-id="1ee54-115">Todas as mensagens enviadas pelo usuário são encaminhadas para seu bot.</span><span class="sxs-lookup"><span data-stu-id="1ee54-115">All messages sent by the user routes to your bot.</span></span>

<span data-ttu-id="1ee54-116">Para que o bot funcione em uma determinada conversa ou escopo, adicione suporte a esse escopo no manifesto [do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="1ee54-116">For the bot to work in a particular conversation or scope, add support to that scope in the [app manifest](~/resources/schema/manifest-schema.md).</span></span>

<span data-ttu-id="1ee54-117">Cada mensagem em uma conversa bot é `Activity` um objeto do tipo `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="1ee54-117">Each message in a bot conversation is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="1ee54-118">Quando um usuário envia uma mensagem, o Teams posta a mensagem no bot e o bot lida com a mensagem.</span><span class="sxs-lookup"><span data-stu-id="1ee54-118">When a user sends a message, Teams posts the message to your bot and the bot handles the message.</span></span> <span data-ttu-id="1ee54-119">Além disso, para definir os comandos principais aos quais o bot responde, você pode adicionar um menu de comando com uma lista lista de comandos suspensos para seu bot.</span><span class="sxs-lookup"><span data-stu-id="1ee54-119">In addition, to define core commands that your bot responds to, you can add a command menu with a drop-down list of commands for your bot.</span></span> <span data-ttu-id="1ee54-120">Os bots em um grupo ou canal só recebem mensagens quando são mencionados @botname.</span><span class="sxs-lookup"><span data-stu-id="1ee54-120">Bots in a group or channel only receive messages when they are mentioned @botname.</span></span> <span data-ttu-id="1ee54-121">O Teams envia notificações ao bot para eventos de conversa que ocorrem em escopos onde o bot está ativo.</span><span class="sxs-lookup"><span data-stu-id="1ee54-121">Teams sends notifications to your bot for conversation events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="1ee54-122">Você pode capturar esses eventos em seu código e tomar medidas sobre eles.</span><span class="sxs-lookup"><span data-stu-id="1ee54-122">You can capture these events in your code and take action on them.</span></span> 

<span data-ttu-id="1ee54-123">Um bot também pode enviar mensagens proativas aos usuários.</span><span class="sxs-lookup"><span data-stu-id="1ee54-123">A bot can also send proactive messages to users.</span></span> <span data-ttu-id="1ee54-124">Uma mensagem proativa é qualquer mensagem enviada por um bot que não responde a uma solicitação de um usuário.</span><span class="sxs-lookup"><span data-stu-id="1ee54-124">A proactive message is any message sent by a bot that is not in response to a request from a user.</span></span> <span data-ttu-id="1ee54-125">Você pode formatar suas mensagens bot para incluir cartões rich que incluem elementos interativos, como botões, texto, imagens, áudio, vídeo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="1ee54-125">You can format your bot messages to include rich cards that include interactive elements, such as buttons, text, images, audio, video, and so on.</span></span> <span data-ttu-id="1ee54-126">O Bot pode atualizar dinamicamente as mensagens depois de enviá-las, em vez de ter suas mensagens como instantâneos estáticos de dados.</span><span class="sxs-lookup"><span data-stu-id="1ee54-126">Bot can dynamically update messages after sending them, instead of having your messages as static snapshots of data.</span></span> <span data-ttu-id="1ee54-127">As mensagens também podem ser excluídas usando o método da Estrutura de `DeleteActivity` Bot.</span><span class="sxs-lookup"><span data-stu-id="1ee54-127">Messages can also be deleted using the Bot Framework's `DeleteActivity` method.</span></span>

## <a name="next-step"></a><span data-ttu-id="1ee54-128">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="1ee54-128">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1ee54-129">Mensagens em conversas de bot</span><span class="sxs-lookup"><span data-stu-id="1ee54-129">Messages in bot conversations</span></span>](~/bots/how-to/conversations/conversation-messages.md)
