---
title: Enviar mensagens proativas
author: clearab
description: Como enviar mensagens pró-ativas com o bot do Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2dfb8e18243079ca38d505f4b80deb7abf2de32f
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874846"
---
# <a name="send-proactive-messages"></a><span data-ttu-id="f6f26-103">Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="f6f26-103">Send proactive messages</span></span>

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="f6f26-104">Uma mensagem proativa é qualquer mensagem enviada por um bot que não está em resposta direta a uma solicitação de um usuário.</span><span class="sxs-lookup"><span data-stu-id="f6f26-104">A proactive message is any message sent by a bot that is not in direct response to a request from a user.</span></span> <span data-ttu-id="f6f26-105">Isso pode incluir mensagens como:</span><span class="sxs-lookup"><span data-stu-id="f6f26-105">This can include messages like:</span></span>

* <span data-ttu-id="f6f26-106">Mensagens de boas-vindas</span><span class="sxs-lookup"><span data-stu-id="f6f26-106">Welcome messages</span></span>
* <span data-ttu-id="f6f26-107">Notificações</span><span class="sxs-lookup"><span data-stu-id="f6f26-107">Notifications</span></span>
* <span data-ttu-id="f6f26-108">Mensagens agendadas</span><span class="sxs-lookup"><span data-stu-id="f6f26-108">Scheduled messages</span></span>

<span data-ttu-id="f6f26-109">Para que o bot envie uma mensagem pró-ativa, ele deve ter acesso ao usuário, ao chat de grupo ou à equipe para a qual você deseja enviar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f6f26-109">In order for your bot to send a proactive message, it must have access to the user, group chat, or team that you wish to send the message to.</span></span> <span data-ttu-id="f6f26-110">Para um chat de grupo ou equipe, isso significa que o aplicativo que contém o bot deve primeiro ser instalado nesse local.</span><span class="sxs-lookup"><span data-stu-id="f6f26-110">For a group chat or team, this means the app that contains your bot must first be installed to that location.</span></span> <span data-ttu-id="f6f26-111">Você pode [instalar proativamente seu aplicativo usando o Graph](#proactively-install-your-app-using-graph) em uma equipe, se necessário, ou usar uma [política de aplicativo](/microsoftteams/teams-custom-app-policies-and-settings) para enviar aplicativos para o Microsoft Teams e usuários em seu locatário.</span><span class="sxs-lookup"><span data-stu-id="f6f26-111">You can [proactively install your app using Graph](#proactively-install-your-app-using-graph) in a team if necessary, or use an [app policy](/microsoftteams/teams-custom-app-policies-and-settings) to push apps out to teams and users in your tenant.</span></span> <span data-ttu-id="f6f26-112">Para os usuários, seu aplicativo precisa ser instalado para esse usuário, ou o usuário precisa fazer parte de uma equipe onde seu aplicativo está instalado.</span><span class="sxs-lookup"><span data-stu-id="f6f26-112">For users, your app either needs to be installed for that user, or your user needs to be part of a team where your app is installed.</span></span>

<span data-ttu-id="f6f26-113">O envio de uma mensagem pró-ativa é diferente do envio de uma mensagem regular, pois você não terá um ativo `turnContext` para ser usado para uma resposta.</span><span class="sxs-lookup"><span data-stu-id="f6f26-113">Sending a proactive message is different than sending a regular message in that you won't have an active `turnContext` to use for a reply.</span></span> <span data-ttu-id="f6f26-114">Você também pode precisar criar a conversa (por exemplo, um novo chat de um-para-um ou um novo thread de conversa em um canal) antes de enviar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f6f26-114">You may also need to create the conversation (for example a new one-to-one chat, or a new conversation thread in a channel) before sending the message.</span></span> <span data-ttu-id="f6f26-115">Você não pode criar um novo chat de grupo ou um novo canal em uma equipe com mensagens proativas.</span><span class="sxs-lookup"><span data-stu-id="f6f26-115">You cannot create a new group chat or a new channel in a team with proactive messaging.</span></span>

<span data-ttu-id="f6f26-116">Em um nível alto, as etapas que você precisa concluir para enviar uma mensagem pró-ativa são:</span><span class="sxs-lookup"><span data-stu-id="f6f26-116">At a high level the steps you'll need to complete to send a proactive message are:</span></span>

1. <span data-ttu-id="f6f26-117">[Obtenha a ID de usuário ou ID de canal/equipe](#get-the-user-id-or-teamchannel-id) (se necessário).</span><span class="sxs-lookup"><span data-stu-id="f6f26-117">[Get the user ID or team/channel ID](#get-the-user-id-or-teamchannel-id) (if needed).</span></span>
1. <span data-ttu-id="f6f26-118">[Crie a conversa ou thread de conversa](#create-the-conversation) (se necessário).</span><span class="sxs-lookup"><span data-stu-id="f6f26-118">[Create the conversation or conversation thread](#create-the-conversation) (if needed).</span></span>
1. <span data-ttu-id="f6f26-119">[Obtenha a ID da conversa](#get-the-conversation-id).</span><span class="sxs-lookup"><span data-stu-id="f6f26-119">[Get the conversation ID](#get-the-conversation-id).</span></span>
1. <span data-ttu-id="f6f26-120">[Envie a mensagem](#send-the-message).</span><span class="sxs-lookup"><span data-stu-id="f6f26-120">[Send the message](#send-the-message).</span></span>

<span data-ttu-id="f6f26-121">Os trechos de código na seção de [exemplos](#examples) abaixo são para a criação de uma conversa de um-para-um, consulte a seção de [referências](#references) para obter links de exemplos de trabalho completos para conversas de uma única vez e grupo/canais.</span><span class="sxs-lookup"><span data-stu-id="f6f26-121">The code snippets in the [examples](#examples) section below are for creating a one-to-one conversation, see the [references](#references) section for links to complete working samples for both one-to-once conversations and group/channels.</span></span>

## <a name="get-the-user-id-or-teamchannel-id"></a><span data-ttu-id="f6f26-122">Obter a ID do usuário ou a ID do canal/equipe</span><span class="sxs-lookup"><span data-stu-id="f6f26-122">Get the user ID or team/channel ID</span></span>

<span data-ttu-id="f6f26-123">Se você precisar criar uma nova conversa ou thread de conversa em um canal, precisará primeiro da ID correta para criar a conversa.</span><span class="sxs-lookup"><span data-stu-id="f6f26-123">If you need to create a new conversation or conversation thread in a channel you'll first need the right ID to create the conversation.</span></span> <span data-ttu-id="f6f26-124">Você pode receber/recuperar essa ID de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="f6f26-124">You can receive/retrieve this ID in multiple ways:</span></span>

1. <span data-ttu-id="f6f26-125">Quando seu aplicativo for instalado em qualquer contexto específico, você receberá uma [ `onMembersAdded` atividade](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="f6f26-125">When your app is installed in any particular context, you'll receive a [`onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
1. <span data-ttu-id="f6f26-126">Quando um novo usuário é adicionado a um contexto em que seu aplicativo está instalado, você receberá uma [ `onMembersAdded` atividade](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="f6f26-126">When a new user is added to a context where your app is installed, you'll receive a [`onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
1. <span data-ttu-id="f6f26-127">Você pode recuperar a [lista de canais](~/bots/how-to/get-teams-context.md) em uma equipe que seu aplicativo está instalado.</span><span class="sxs-lookup"><span data-stu-id="f6f26-127">You can retrieve the [list of channels](~/bots/how-to/get-teams-context.md) in a team your app is installed.</span></span>
1. <span data-ttu-id="f6f26-128">Você pode recuperar a [lista de membros](~/bots/how-to/get-teams-context.md) de uma equipe que seu aplicativo está instalado.</span><span class="sxs-lookup"><span data-stu-id="f6f26-128">You can retrieve the [list of members](~/bots/how-to/get-teams-context.md) of a team your app is installed.</span></span>
1. <span data-ttu-id="f6f26-129">Toda atividade que seu bot recebe conterá as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="f6f26-129">Every Activity your bot receives will contain the necessary information.</span></span>

<span data-ttu-id="f6f26-130">Independentemente de como você obtém as informações, você precisará armazenar o `tenantId` e o `userId` ou `channelId` para criar uma nova conversa.</span><span class="sxs-lookup"><span data-stu-id="f6f26-130">Regardless of how you gain the information, you'll need to store the `tenantId` and either the `userId` or `channelId` in order to create a new conversation.</span></span> <span data-ttu-id="f6f26-131">Você também pode usar o `teamId` para criar um novo thread de conversa no canal geral/padrão de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="f6f26-131">You can also use the `teamId` to create a new conversation thread in the general/default channel of a team.</span></span>

<span data-ttu-id="f6f26-132">O `userId` é exclusivo do seu ID de bot e de um usuário específico, não é possível usá-los novamente entre bots.</span><span class="sxs-lookup"><span data-stu-id="f6f26-132">The `userId` is unique to your bot Id and a particular user, you cannot re-use them between bots.</span></span> <span data-ttu-id="f6f26-133">O `channelId` é global, mas seu bot _deve_ ser instalado na equipe antes que você possa enviar uma mensagem proativa para um canal.</span><span class="sxs-lookup"><span data-stu-id="f6f26-133">The `channelId` is global, however your bot _must_ be installed in the team before you can send a proactive message to a channel.</span></span>

## <a name="create-the-conversation"></a><span data-ttu-id="f6f26-134">Criar a conversa</span><span class="sxs-lookup"><span data-stu-id="f6f26-134">Create the conversation</span></span>

<span data-ttu-id="f6f26-135">Depois de ter as informações de usuário/canal, você precisará criar a conversa se ela ainda não existir (ou se você não souber o `conversationId` ).</span><span class="sxs-lookup"><span data-stu-id="f6f26-135">Once you have the user/channel information, you'll need to create the conversation if it doesn't already exist (or you don't know the `conversationId`).</span></span> <span data-ttu-id="f6f26-136">Você só deve criar a conversa uma vez; Certifique-se de armazenar o `conversationId` valor ou o `conversationReference` objeto a ser usado no futuro.</span><span class="sxs-lookup"><span data-stu-id="f6f26-136">You should only create the conversation once; make sure you store the `conversationId` value or `conversationReference` object to use in the future.</span></span>

## <a name="get-the-conversation-id"></a><span data-ttu-id="f6f26-137">Obter a ID da conversa</span><span class="sxs-lookup"><span data-stu-id="f6f26-137">Get the conversation ID</span></span>

<span data-ttu-id="f6f26-138">Após a criação da conversa, você usará o `conversationReference` objeto ou o `conversationId` e o `tenantId` para enviar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f6f26-138">Once the conversation has been created, you will use either the `conversationReference` object or the `conversationId` and the `tenantId` to send the message.</span></span> <span data-ttu-id="f6f26-139">Você pode obter essa ID criando a conversa ou armazenando-a de qualquer atividade enviada por esse contexto.</span><span class="sxs-lookup"><span data-stu-id="f6f26-139">You can get this Id by either creating the conversation, or storing it from any Activity sent to you from that context.</span></span> <span data-ttu-id="f6f26-140">Certifique-se de que armazenou essa ID.</span><span class="sxs-lookup"><span data-stu-id="f6f26-140">Make certain that you store this Id.</span></span>

## <a name="send-the-message"></a><span data-ttu-id="f6f26-141">Enviar a mensagem</span><span class="sxs-lookup"><span data-stu-id="f6f26-141">Send the message</span></span>

<span data-ttu-id="f6f26-142">Agora que você tem as informações de endereço corretas, você pode enviar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f6f26-142">Now that you have the right address information, you can send your message.</span></span> <span data-ttu-id="f6f26-143">Se você estiver usando o SDK, fará isso usando o método e `continueConversation` o `conversationId` e `tenantId` para fazer uma chamada de API direta.</span><span class="sxs-lookup"><span data-stu-id="f6f26-143">If you're using the SDK, you'll do so using the `continueConversation` method,and the `conversationId` and `tenantId` to make a direct API call.</span></span>  <span data-ttu-id="f6f26-144">Você precisará definir `conversationParameters` corretamente para enviar sua mensagem com êxito, consulte os [exemplos](#examples) abaixo ou use um dos exemplos listados na seção [referências](#references) .</span><span class="sxs-lookup"><span data-stu-id="f6f26-144">You'll need to set the `conversationParameters` correctly to successfully send your message - see the [examples](#examples) below or use one of the samples listed in the [references](#references) section.</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="f6f26-145">Práticas recomendadas para mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="f6f26-145">Best practices for proactive messaging</span></span>

<span data-ttu-id="f6f26-146">Enviar mensagens pró-ativas para os usuários pode ser uma maneira muito eficaz de se comunicar com seus usuários.</span><span class="sxs-lookup"><span data-stu-id="f6f26-146">Sending proactive messages to users can be a very effective way to communicate with your users.</span></span> <span data-ttu-id="f6f26-147">No entanto, de sua perspectiva esta mensagem pode aparecer completamente sem confirmação e, no caso de mensagens de boas-vindas, será a primeira vez que interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6f26-147">However, from their perspective this message can appear completely unprompted and, in the case of welcome messages, it will be the first time they've interacted with your app.</span></span> <span data-ttu-id="f6f26-148">Assim, é muito importante usar essa funcionalidade com moderação (não enviar spam aos usuários) e fornecer informações suficientes para permitir que os usuários entendam por que estão sendo messaged.</span><span class="sxs-lookup"><span data-stu-id="f6f26-148">As such, it is very important to use this functionality sparingly (don't spam your users) and to provide enough information to let users understand why they are being messaged.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="f6f26-149">Mensagens de boas-vindas</span><span class="sxs-lookup"><span data-stu-id="f6f26-149">Welcome messages</span></span>

<span data-ttu-id="f6f26-150">Ao usar o sistema de mensagens proativas para enviar uma mensagem de boas-vindas a um usuário, você deve ter em mente que, para a maioria das pessoas receber a mensagem, não haverá nenhum contexto para o recebimento.</span><span class="sxs-lookup"><span data-stu-id="f6f26-150">When using proactive messaging to send a welcome message to a user you must keep in mind that, for most people receiving the message, there will be no context for why they are receiving it.</span></span> <span data-ttu-id="f6f26-151">Essa é também a primeira vez que terá interagindo com o aplicativo; é sua oportunidade de criar uma boa impressão em bom lugar.</span><span class="sxs-lookup"><span data-stu-id="f6f26-151">This is also the first time they will have interacted with your app; it is your opportunity to create a good first impression.</span></span> <span data-ttu-id="f6f26-152">As melhores mensagens de boas-vindas incluirão:</span><span class="sxs-lookup"><span data-stu-id="f6f26-152">The best welcome messages will include:</span></span>

* <span data-ttu-id="f6f26-153">**Por que um usuário recebe a mensagem.**</span><span class="sxs-lookup"><span data-stu-id="f6f26-153">**Why a user is receiving the message.**</span></span> <span data-ttu-id="f6f26-154">Deve estar muito claro para o usuário por que eles estão recebendo a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f6f26-154">It should be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="f6f26-155">Se o seu bot foi instalado em um canal e você enviou uma mensagem de boas-vindas para todos os usuários, informe-o sobre o canal em que ele foi instalado e possivelmente quem o instalou.</span><span class="sxs-lookup"><span data-stu-id="f6f26-155">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and potentially who installed it.</span></span>
* <span data-ttu-id="f6f26-156">**O que você oferece.**</span><span class="sxs-lookup"><span data-stu-id="f6f26-156">**What do you offer.**</span></span> <span data-ttu-id="f6f26-157">O que eles podem fazer com o seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="f6f26-157">What can they do with your app?</span></span> <span data-ttu-id="f6f26-158">Que valor você pode trazer para eles?</span><span class="sxs-lookup"><span data-stu-id="f6f26-158">What value can you bring to them?</span></span>
* <span data-ttu-id="f6f26-159">**O que deve ser feito em seguida.**</span><span class="sxs-lookup"><span data-stu-id="f6f26-159">**What should they do next.**</span></span> <span data-ttu-id="f6f26-160">Convide-os a experimentar um comando ou interagir com o aplicativo de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="f6f26-160">Invite them to try out a command, or interact with your app in some way.</span></span>

<span data-ttu-id="f6f26-161">Lembre-se: as mensagens de boas-vindas podem levar a usuários que estão bloqueando o bot</span><span class="sxs-lookup"><span data-stu-id="f6f26-161">Remember, poor welcome messages can lead to users blocking your bot.</span></span> <span data-ttu-id="f6f26-162">Você deve gastar bastante tempo para criar suas mensagens de boas-vindas e iterar neles se elas não estiverem tendo o efeito desejado.</span><span class="sxs-lookup"><span data-stu-id="f6f26-162">You should spend plenty of time crafting your welcome messages, and iterate on them if they are not having the desired effect.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="f6f26-163">Mensagens de notificação</span><span class="sxs-lookup"><span data-stu-id="f6f26-163">Notification messages</span></span>

<span data-ttu-id="f6f26-164">Ao usar mensagens proativas para enviar notificações, você precisa certificar-se de que seus usuários tenham um caminho claro para tomar ações comuns com base em sua notificação e uma compreensão clara de por que a notificação ocorreu.</span><span class="sxs-lookup"><span data-stu-id="f6f26-164">When using proactive messaging to send notifications you need to make sure your users have a clear path to take common actions based on your notification and a clear understanding of why the notification occurred.</span></span> <span data-ttu-id="f6f26-165">Geralmente, as boas mensagens de notificação incluirão:</span><span class="sxs-lookup"><span data-stu-id="f6f26-165">Good notification messages will generally include:</span></span>

* <span data-ttu-id="f6f26-166">**O que aconteceu.**</span><span class="sxs-lookup"><span data-stu-id="f6f26-166">**What happened.**</span></span> <span data-ttu-id="f6f26-167">Uma indicação clara do que aconteceu com a notificação.</span><span class="sxs-lookup"><span data-stu-id="f6f26-167">A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="f6f26-168">**Qual era o resultado.**</span><span class="sxs-lookup"><span data-stu-id="f6f26-168">**What was the result.**</span></span> <span data-ttu-id="f6f26-169">Deve estar claro qual item/coisa foi atualizado para causar a notificação.</span><span class="sxs-lookup"><span data-stu-id="f6f26-169">It should be clear what item/thing was updated to cause the notification.</span></span>
* <span data-ttu-id="f6f26-170">**Quem/o disparou.**</span><span class="sxs-lookup"><span data-stu-id="f6f26-170">**Who/what triggered it.**</span></span> <span data-ttu-id="f6f26-171">Quem ou o que executou a ação que provocou a envio da notificação.</span><span class="sxs-lookup"><span data-stu-id="f6f26-171">Who or what took action that caused the notification to be sent.</span></span>
* <span data-ttu-id="f6f26-172">**O que os usuários podem fazer em resposta.**</span><span class="sxs-lookup"><span data-stu-id="f6f26-172">**What can users do in response.**</span></span> <span data-ttu-id="f6f26-173">Facilite que os usuários executem ações com base em suas notificações.</span><span class="sxs-lookup"><span data-stu-id="f6f26-173">Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="f6f26-174">**Como os usuários podem recusar.** Você precisa fornecer um caminho para que os usuários recusem notificações adicionais.</span><span class="sxs-lookup"><span data-stu-id="f6f26-174">**How can users opt out.** You need to provide a path for users to opt out of additional notifications.</span></span>

## <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="f6f26-175">Instalar o aplicativo proativamente usando o Graph</span><span class="sxs-lookup"><span data-stu-id="f6f26-175">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="f6f26-176">A instalação proativa de aplicativos usando o Microsoft Graph está atualmente em versão beta.</span><span class="sxs-lookup"><span data-stu-id="f6f26-176">Proactively installing apps using the Microsoft Graph is currently in beta.</span></span>

<span data-ttu-id="f6f26-177">Ocasionalmente, pode ser necessário que usuários de mensagens de forma proativa não tenham sido instalados ou interagindo com o aplicativo anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f6f26-177">Occasionally it may be necessary to proactively message users that have not installed or interacted with your app previously.</span></span> <span data-ttu-id="f6f26-178">Por exemplo, você deseja usar o [Communicator da empresa](~/samples/app-templates.md#company-communicator) para enviar mensagens para toda a sua organização.</span><span class="sxs-lookup"><span data-stu-id="f6f26-178">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="f6f26-179">Para este cenário, você pode usar a API do Graph para instalar proativamente seu aplicativo para seus usuários e, em seguida, armazenar em cache os valores necessários do `conversationUpdate` evento que seu aplicativo receberá na instalação.</span><span class="sxs-lookup"><span data-stu-id="f6f26-179">For this scenario you can use the Graph API to proactively install your app for your users, then cache the necessary values from the `conversationUpdate` event your app will receive upon install.</span></span>

<span data-ttu-id="f6f26-180">Você só pode instalar aplicativos que estão no catálogo de aplicativos organizacionais ou na loja de aplicativos do teams.</span><span class="sxs-lookup"><span data-stu-id="f6f26-180">You can only install apps that are in your organizational app catalogue, or the Teams app store.</span></span>

<span data-ttu-id="f6f26-181">Confira [instalar aplicativos para usuários](/graph/teams-proactive-messaging) na documentação de gráfico e [instalação e mensagens de bot proativas no Teams com o Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span><span class="sxs-lookup"><span data-stu-id="f6f26-181">See [Install apps for users](/graph/teams-proactive-messaging) in the Graph documentation and [Proactive bot installation and messaging in Teams with Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span></span> <span data-ttu-id="f6f26-182">Há também um [exemplo do Microsoft .NET Framework](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176)  na plataforma github.</span><span class="sxs-lookup"><span data-stu-id="f6f26-182">There is also a [Microsoft .NET framework sample](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176)  on the GitHub platform.</span></span>

## <a name="examples"></a><span data-ttu-id="f6f26-183">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f6f26-183">Examples</span></span>

# <a name="cnet"></a>[<span data-ttu-id="f6f26-184">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="f6f26-184">C#/.NET</span></span>](#tab/dotnet)

```csharp
private async Task MessageAllMembersAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var teamsChannelId = turnContext.Activity.TeamsGetChannelId();
    var serviceUrl = turnContext.Activity.ServiceUrl;
    var credentials = new MicrosoftAppCredentials(_appId, _appPassword);
    ConversationReference conversationReference = null;

    //Get the set of member IDs to send the message to
    var members = await GetPagedMembers(turnContext, cancellationToken);

    foreach (var teamMember in members)
    {
        var proactiveMessage = MessageFactory.Text($"Hello {teamMember.GivenName} {teamMember.Surname}. I'm a Teams conversation bot.");

        var conversationParameters = new ConversationParameters
        {
            IsGroup = false,
            Bot = turnContext.Activity.Recipient,
            Members = new ChannelAccount[] { teamMember },
            TenantId = turnContext.Activity.Conversation.TenantId,
        };
        //create the new one-to-one conversations
        await ((BotFrameworkAdapter)turnContext.Adapter).CreateConversationAsync(
            teamsChannelId,
            serviceUrl,
            credentials,
            conversationParameters,
            async (t1, c1) =>
            {
                //Get the conversationReference
                conversationReference = t1.Activity.GetConversationReference();
                //Send the proactive message
                await ((BotFrameworkAdapter)turnContext.Adapter).ContinueConversationAsync(
                    _appId,
                    conversationReference,
                    async (t2, c2) =>
                    {
                        await t2.SendActivityAsync(proactiveMessage, c2);
                    },
                    cancellationToken);
            },
            cancellationToken);
    }

    await turnContext.SendActivityAsync(MessageFactory.Text("All messages have been sent."), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="f6f26-185">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="f6f26-185">TypeScript/Node.js</span></span>](#tab/typescript)

```javascript

async messageAllMembersAsync(context) {
    const members = await this.getPagedMembers(context);

    members.forEach(async (teamMember) => {
        const message = MessageFactory.text('Hello ${ teamMember.givenName } ${ teamMember.surname }. I\'m a Teams conversation bot.');

        var ref = TurnContext.getConversationReference(context.activity);
        ref.user = teamMember;

        await context.adapter.createConversation(ref,
            async (t1) => {
                const ref2 = TurnContext.getConversationReference(t1.activity);
                await t1.adapter.continueConversation(ref2, async (t2) => {
                    await t2.sendActivity(message);
                });
            });
    });

    await context.sendActivity(MessageFactory.text('All messages have been sent.'));
}
```

# <a name="python"></a>[<span data-ttu-id="f6f26-186">Python</span><span class="sxs-lookup"><span data-stu-id="f6f26-186">Python</span></span>](#tab/python)

```python
async def _message_all_members(self, turn_context: TurnContext):
    team_members = await self._get_paged_members(turn_context)

    for member in team_members:
        conversation_reference = TurnContext.get_conversation_reference(
            turn_context.activity
        )

        conversation_parameters = ConversationParameters(
            is_group=False,
            bot=turn_context.activity.recipient,
            members=[member],
            tenant_id=turn_context.activity.conversation.tenant_id,
        )

        async def get_ref(tc1):
            conversation_reference_inner = TurnContext.get_conversation_reference(
                tc1.activity
            )
            return await tc1.adapter.continue_conversation(
                conversation_reference_inner, send_message, self._app_id
            )

        async def send_message(tc2: TurnContext):
            return await tc2.send_activity(
                f"Hello {member.name}. I'm a Teams conversation bot."
            )

        await turn_context.adapter.create_conversation(
            conversation_reference, get_ref, conversation_parameters
        )

    await turn_context.send_activity(
        MessageFactory.text("All messages have been sent")
    )

```

# <a name="json"></a>[<span data-ttu-id="f6f26-187">JSON</span><span class="sxs-lookup"><span data-stu-id="f6f26-187">JSON</span></span>](#tab/json)

```json
POST /v3/conversations
{
  "bot": {
    "id": "28:10j12ou0d812-2o1098-c1mjojzldxcj-1098028n ",
    "name": "The Bot"
  },
  "members": [
    {
      "id": "29:012d20j1cjo20211"
    }
  ],
  "channelData": {
    "tenant": {
      "id": "197231joe-1209j01821-012kdjoj"
    }
  }
}
```

<span data-ttu-id="f6f26-188">Você deve fornecer a ID de usuário e a ID do locatário.</span><span class="sxs-lookup"><span data-stu-id="f6f26-188">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="f6f26-189">Se a chamada for bem-sucedida, a API retornará com o seguinte objeto Response.</span><span class="sxs-lookup"><span data-stu-id="f6f26-189">If the call succeeds, the API returns with the following response object.</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="references"></a><span data-ttu-id="f6f26-190">Referências</span><span class="sxs-lookup"><span data-stu-id="f6f26-190">References</span></span>

<span data-ttu-id="f6f26-191">As amostras de mensagens pró-ativas oficiais estão listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="f6f26-191">The official proactive messaging samples are listed below.</span></span>

|  <span data-ttu-id="f6f26-192">Não.</span><span class="sxs-lookup"><span data-stu-id="f6f26-192">No.</span></span>  | <span data-ttu-id="f6f26-193">Nome da amostra</span><span class="sxs-lookup"><span data-stu-id="f6f26-193">Sample Name</span></span>           | <span data-ttu-id="f6f26-194">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6f26-194">Description</span></span>                                                                      | <span data-ttu-id="f6f26-195">.NET</span><span class="sxs-lookup"><span data-stu-id="f6f26-195">.NET</span></span>    | <span data-ttu-id="f6f26-196">JavaScript</span><span class="sxs-lookup"><span data-stu-id="f6f26-196">JavaScript</span></span>   | <span data-ttu-id="f6f26-197">Python</span><span class="sxs-lookup"><span data-stu-id="f6f26-197">Python</span></span>  |
|:--:|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|<span data-ttu-id="f6f26-198">57</span><span class="sxs-lookup"><span data-stu-id="f6f26-198">57</span></span>|<span data-ttu-id="f6f26-199">Noções básicas da conversa do teams</span><span class="sxs-lookup"><span data-stu-id="f6f26-199">Teams Conversation Basics</span></span>  | <span data-ttu-id="f6f26-200">Demonstra noções básicas de conversas no Teams, incluindo o envio de mensagens pró-ativas de um para um.</span><span class="sxs-lookup"><span data-stu-id="f6f26-200">Demonstrates basics of conversations in Teams, including sending one-to-one proactive messages.</span></span>|[<span data-ttu-id="f6f26-201">&nbsp;Núcleo .net</span><span class="sxs-lookup"><span data-stu-id="f6f26-201">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="f6f26-202">JavaScript</span><span class="sxs-lookup"><span data-stu-id="f6f26-202">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="f6f26-203">Python</span><span class="sxs-lookup"><span data-stu-id="f6f26-203">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|<span data-ttu-id="f6f26-204">58</span><span class="sxs-lookup"><span data-stu-id="f6f26-204">58</span></span>|<span data-ttu-id="f6f26-205">Iniciar novo thread em um canal</span><span class="sxs-lookup"><span data-stu-id="f6f26-205">Start new thread in a channel</span></span>     | <span data-ttu-id="f6f26-206">Demonstra como criar um novo thread em um canal.</span><span class="sxs-lookup"><span data-stu-id="f6f26-206">Demonstrates creating a new thread in a channel.</span></span> |[<span data-ttu-id="f6f26-207">&nbsp;Núcleo .net</span><span class="sxs-lookup"><span data-stu-id="f6f26-207">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[<span data-ttu-id="f6f26-208">JavaScript</span><span class="sxs-lookup"><span data-stu-id="f6f26-208">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[<span data-ttu-id="f6f26-209">Python</span><span class="sxs-lookup"><span data-stu-id="f6f26-209">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

<span data-ttu-id="f6f26-210">O exemplo a seguir demonstra a quantidade mínima de informações necessárias para enviar uma mensagem proativa (sem usar um `conversationReference` objeto).</span><span class="sxs-lookup"><span data-stu-id="f6f26-210">The sample below demonstrates the minimal amount of information needed to send a proactive message (without using a `conversationReference` object).</span></span> <span data-ttu-id="f6f26-211">Este exemplo pode ser útil se você estiver usando chamadas de API REST diretamente ou não armazenou `conversationReference` objetos completos.</span><span class="sxs-lookup"><span data-stu-id="f6f26-211">This sample can be useful if you're using REST API calls directly, or haven't been storing full `conversationReference` objects.</span></span>

* [<span data-ttu-id="f6f26-212">Mensagens proativas do teams</span><span class="sxs-lookup"><span data-stu-id="f6f26-212">Teams Proactive Messaging</span></span>](https://github.com/clearab/teamsProactiveMessaging)

## <a name="view-additional-code"></a><span data-ttu-id="f6f26-213">Exibir código adicional</span><span class="sxs-lookup"><span data-stu-id="f6f26-213">View additional code</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f6f26-214">**Amostras de código de mensagens proativas do teams**</span><span class="sxs-lookup"><span data-stu-id="f6f26-214">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>