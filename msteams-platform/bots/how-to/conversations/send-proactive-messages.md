---
title: Enviar mensagens proativas
description: Descreve como enviar mensagens proativas com seu bot do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
localization_priority: Normal
Keywords: enviar uma mensagem obter iD de conversa de canal de ID do usuário
ms.openlocfilehash: 56411fe381a05318d0e12d6876cf26138baba42c
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994214"
---
# <a name="send-proactive-messages"></a><span data-ttu-id="24e10-104">Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="24e10-104">Send proactive messages</span></span>

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="24e10-105">Uma mensagem proativa é qualquer mensagem enviada por um bot que não responde a uma solicitação de um usuário.</span><span class="sxs-lookup"><span data-stu-id="24e10-105">A proactive message is any message sent by a bot that is not in response to a request from a user.</span></span> <span data-ttu-id="24e10-106">Isso pode incluir mensagens, como:</span><span class="sxs-lookup"><span data-stu-id="24e10-106">This can include messages, such as:</span></span>

* <span data-ttu-id="24e10-107">Mensagem de boas-vindas</span><span class="sxs-lookup"><span data-stu-id="24e10-107">Welcome messages</span></span>
* <span data-ttu-id="24e10-108">Notificações</span><span class="sxs-lookup"><span data-stu-id="24e10-108">Notifications</span></span>
* <span data-ttu-id="24e10-109">Mensagens agendadas</span><span class="sxs-lookup"><span data-stu-id="24e10-109">Scheduled messages</span></span>

<span data-ttu-id="24e10-110">Para que o bot envie uma mensagem proativa para um usuário, chat em grupo ou equipe, ele deve ter acesso para enviar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="24e10-110">For your bot to send a proactive message to a user, group chat, or team, it must have access to send the message.</span></span> <span data-ttu-id="24e10-111">Para um chat em grupo ou equipe, o aplicativo que contém seu bot deve ser instalado primeiro nesse local.</span><span class="sxs-lookup"><span data-stu-id="24e10-111">For a group chat or team, the app that contains your bot must be first installed in that location.</span></span> <span data-ttu-id="24e10-112">Você pode [instalar proativamente](#proactively-install-your-app-using-graph) seu aplicativo usando o Microsoft Graph [](/microsoftteams/teams-custom-app-policies-and-settings) em uma equipe, se necessário, ou usar uma política de aplicativo para empurrar aplicativos para equipes e usuários em seu locatário.</span><span class="sxs-lookup"><span data-stu-id="24e10-112">You can [proactively install your app using Microsoft Graph](#proactively-install-your-app-using-graph) in a team, if required, or use an [app policy](/microsoftteams/teams-custom-app-policies-and-settings) to push apps out to teams and users in your tenant.</span></span> <span data-ttu-id="24e10-113">Para os usuários, seu aplicativo deve ser instalado para o usuário ou seu usuário deve fazer parte de uma equipe em que seu aplicativo está instalado.</span><span class="sxs-lookup"><span data-stu-id="24e10-113">For users, your app either must be installed for the user or your user must be part of a team where your app is installed.</span></span>

<span data-ttu-id="24e10-114">Enviar uma mensagem proativa é diferente de enviar uma mensagem regular.</span><span class="sxs-lookup"><span data-stu-id="24e10-114">Sending a proactive message is different from sending a regular message.</span></span> <span data-ttu-id="24e10-115">Não há nenhum ativo `turnContext` a ser usado para uma resposta.</span><span class="sxs-lookup"><span data-stu-id="24e10-115">There is no active `turnContext` to use for a reply.</span></span> <span data-ttu-id="24e10-116">Você deve criar a conversa antes de enviar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="24e10-116">You must create the conversation before sending the message.</span></span> <span data-ttu-id="24e10-117">Por exemplo, um novo chat um para um ou um novo thread de conversa em um canal.</span><span class="sxs-lookup"><span data-stu-id="24e10-117">For example, a new one-to-one chat or a new conversation thread in a channel.</span></span> <span data-ttu-id="24e10-118">Não é possível criar um novo chat em grupo ou um novo canal em uma equipe com mensagens proativas.</span><span class="sxs-lookup"><span data-stu-id="24e10-118">You cannot create a new group chat or a new channel in a team with proactive messaging.</span></span>

<span data-ttu-id="24e10-119">**Para enviar uma mensagem proativa**</span><span class="sxs-lookup"><span data-stu-id="24e10-119">**To send a proactive message**</span></span>

1. <span data-ttu-id="24e10-120">[Obter a ID do usuário, a ID da equipe ou a ID do](#get-the-user-id-team-id-or-channel-id)canal, se necessário.</span><span class="sxs-lookup"><span data-stu-id="24e10-120">[Get the user ID, team ID, or channel ID](#get-the-user-id-team-id-or-channel-id), if required.</span></span>
1. <span data-ttu-id="24e10-121">[Crie a conversa](#create-the-conversation), se necessário.</span><span class="sxs-lookup"><span data-stu-id="24e10-121">[Create the conversation](#create-the-conversation), if required.</span></span>
1. <span data-ttu-id="24e10-122">[Obter a ID da conversa](#get-the-conversation-id).</span><span class="sxs-lookup"><span data-stu-id="24e10-122">[Get the conversation ID](#get-the-conversation-id).</span></span>
1. <span data-ttu-id="24e10-123">[Envie a mensagem](#send-the-message).</span><span class="sxs-lookup"><span data-stu-id="24e10-123">[Send the message](#send-the-message).</span></span>

<span data-ttu-id="24e10-124">Os trechos de código na seção [exemplos](#samples) são para criar uma conversa um para um.</span><span class="sxs-lookup"><span data-stu-id="24e10-124">The code snippets in the [samples](#samples) section are for creating a one-to-one conversation.</span></span> <span data-ttu-id="24e10-125">Para links para concluir exemplos de trabalho para conversas um-para-um e grupos ou canais , consulte [exemplo de código](#code-sample).</span><span class="sxs-lookup"><span data-stu-id="24e10-125">For links to complete working samples for both one-to-one conversations and group or channels , see [code sample](#code-sample).</span></span>

<span data-ttu-id="24e10-126">Para usar mensagens proativas efetivamente, consulte [práticas recomendadas para mensagens proativas.](#best-practices-for-proactive-messaging)</span><span class="sxs-lookup"><span data-stu-id="24e10-126">For using proactive messages effectively, see [best practices for proactive messaging](#best-practices-for-proactive-messaging).</span></span> <span data-ttu-id="24e10-127">Para determinados cenários, você deve [instalar proativamente seu aplicativo usando Graph](#proactively-install-your-app-using-graph).</span><span class="sxs-lookup"><span data-stu-id="24e10-127">For certain scenarios, you must [proactively install your app using Graph](#proactively-install-your-app-using-graph).</span></span> <span data-ttu-id="24e10-128">Os trechos de código na seção [exemplos](#samples) são para criar uma conversa um para um.</span><span class="sxs-lookup"><span data-stu-id="24e10-128">The code snippets in the [samples](#samples) section are for creating a one-to-one conversation.</span></span> <span data-ttu-id="24e10-129">Para amostras completas de trabalho para conversas e grupos ou canais de um para um, consulte [amostra de código](#code-sample).</span><span class="sxs-lookup"><span data-stu-id="24e10-129">For complete working samples for both one-to-one conversations and groups or channels, see [code sample](#code-sample).</span></span>

## <a name="get-the-user-id-team-id-or-channel-id"></a><span data-ttu-id="24e10-130">Obter a ID do usuário, a ID da equipe ou a ID do canal</span><span class="sxs-lookup"><span data-stu-id="24e10-130">Get the user ID, team ID or channel ID</span></span>

<span data-ttu-id="24e10-131">Para criar um novo thread de conversa ou conversa em um canal, você deve ter a ID correta.</span><span class="sxs-lookup"><span data-stu-id="24e10-131">To create a new conversation or conversation thread in a channel, you must have the correct ID.</span></span> <span data-ttu-id="24e10-132">Você pode receber ou recuperar essa ID usando qualquer um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="24e10-132">You can receive or retrieve this ID using any of the following:</span></span>

* <span data-ttu-id="24e10-133">Quando seu aplicativo é instalado em qualquer contexto específico, você recebe uma [ `onMembersAdded` atividade](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="24e10-133">When your app is installed in any particular context, you receive an [`onMembersAdded` activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="24e10-134">Quando um novo usuário é adicionado a um contexto em que seu aplicativo está instalado, você recebe uma [ `onMembersAdded` atividade](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="24e10-134">When a new user is added to a context where your app is installed, you receive an [`onMembersAdded` activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="24e10-135">Você pode recuperar a [lista de canais](~/bots/how-to/get-teams-context.md) em uma equipe onde seu aplicativo está instalado.</span><span class="sxs-lookup"><span data-stu-id="24e10-135">You can retrieve the [list of channels](~/bots/how-to/get-teams-context.md) in a team where your app is installed.</span></span>
* <span data-ttu-id="24e10-136">Você pode recuperar a [lista de membros](~/bots/how-to/get-teams-context.md) de uma equipe onde seu aplicativo está instalado.</span><span class="sxs-lookup"><span data-stu-id="24e10-136">You can retrieve the [list of members](~/bots/how-to/get-teams-context.md) of a team where your app is installed.</span></span>
* <span data-ttu-id="24e10-137">Todas as atividades que seu bot recebe devem conter as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="24e10-137">Every activity your bot receives must contain the required information.</span></span>

<span data-ttu-id="24e10-138">Independentemente de como você obter as informações, você deve armazenar e `tenantId` ou criar uma nova `userId` `channelId` conversa.</span><span class="sxs-lookup"><span data-stu-id="24e10-138">Regardless of how you get the information, you must store the `tenantId` and either the `userId` or `channelId` to create a new conversation.</span></span> <span data-ttu-id="24e10-139">Você também pode usar o para criar um novo thread de conversa no canal geral ou `teamId` padrão de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="24e10-139">You can also use the `teamId` to create a new conversation thread in the general or default channel of a team.</span></span>

<span data-ttu-id="24e10-140">O `userId` é exclusivo da ID do bot e de um usuário específico.</span><span class="sxs-lookup"><span data-stu-id="24e10-140">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="24e10-141">Não é possível reutilizar os `userId` bots entre.</span><span class="sxs-lookup"><span data-stu-id="24e10-141">You cannot reuse the `userId` between bots.</span></span> <span data-ttu-id="24e10-142">O `channelId` é global.</span><span class="sxs-lookup"><span data-stu-id="24e10-142">The `channelId` is global.</span></span> <span data-ttu-id="24e10-143">No entanto, seu bot deve ser instalado na equipe antes de poder enviar uma mensagem proativa para um canal.</span><span class="sxs-lookup"><span data-stu-id="24e10-143">However, your bot must be installed in the team before you can send a proactive message to a channel.</span></span>

<span data-ttu-id="24e10-144">Depois de ter as informações do usuário ou do canal, você deve criar a conversa.</span><span class="sxs-lookup"><span data-stu-id="24e10-144">After you have the user or channel information, you must create the conversation.</span></span>

## <a name="create-the-conversation"></a><span data-ttu-id="24e10-145">Criar a conversa</span><span class="sxs-lookup"><span data-stu-id="24e10-145">Create the conversation</span></span>

<span data-ttu-id="24e10-146">Você deve criar a conversa se ela não existir ou não conhecer `conversationId` o .</span><span class="sxs-lookup"><span data-stu-id="24e10-146">You must create the conversation if it does not exist or you do not know the `conversationId`.</span></span> <span data-ttu-id="24e10-147">Você só deve criar a conversa uma vez e armazenar `conversationId` o valor ou `conversationReference` objeto.</span><span class="sxs-lookup"><span data-stu-id="24e10-147">You must only create the conversation once and store the `conversationId` value or `conversationReference` object.</span></span>

<span data-ttu-id="24e10-148">Após a criação da conversa, você deve obter a ID da conversa.</span><span class="sxs-lookup"><span data-stu-id="24e10-148">After the conversation is created, you must get the conversation ID.</span></span>

## <a name="get-the-conversation-id"></a><span data-ttu-id="24e10-149">Obter a ID da conversa</span><span class="sxs-lookup"><span data-stu-id="24e10-149">Get the conversation ID</span></span>

<span data-ttu-id="24e10-150">Use o `conversationReference` objeto ou e envie a `conversationId` `tenantId` mensagem.</span><span class="sxs-lookup"><span data-stu-id="24e10-150">Use either the `conversationReference` object or `conversationId` and `tenantId` to send the message.</span></span> <span data-ttu-id="24e10-151">Você pode obter essa ID criando a conversa ou o armazenamento de qualquer atividade enviada a você a partir desse contexto.</span><span class="sxs-lookup"><span data-stu-id="24e10-151">You can get this ID by either creating the conversation or storing it from any activity sent to you from that context.</span></span> <span data-ttu-id="24e10-152">Armazene essa ID para referência.</span><span class="sxs-lookup"><span data-stu-id="24e10-152">Store this ID for reference.</span></span>

<span data-ttu-id="24e10-153">Depois de obter as informações de endereço apropriadas, você pode enviar sua mensagem.</span><span class="sxs-lookup"><span data-stu-id="24e10-153">After you get the appropriate address information, you can send your message.</span></span>

## <a name="send-the-message"></a><span data-ttu-id="24e10-154">Enviar a mensagem</span><span class="sxs-lookup"><span data-stu-id="24e10-154">Send the message</span></span>

<span data-ttu-id="24e10-155">Agora que você tem as informações de endereço corretas, você pode enviar sua mensagem.</span><span class="sxs-lookup"><span data-stu-id="24e10-155">Now that you have the right address information, you can send your message.</span></span> <span data-ttu-id="24e10-156">Se você estiver usando o SDK, deverá usar o método e e `continueConversation` fazer uma chamada de API `conversationId` `tenantId` direta.</span><span class="sxs-lookup"><span data-stu-id="24e10-156">If you are using the SDK, you must use the `continueConversation` method, and the `conversationId` and `tenantId` to make a direct API call.</span></span> <span data-ttu-id="24e10-157">Você deve definir `conversationParameters` corretamente para enviar sua mensagem com êxito.</span><span class="sxs-lookup"><span data-stu-id="24e10-157">You must set the `conversationParameters` correctly to successfully send your message.</span></span> <span data-ttu-id="24e10-158">Consulte a [seção exemplos](#samples) ou use um dos exemplos listados na seção de exemplo [de](#code-sample) código.</span><span class="sxs-lookup"><span data-stu-id="24e10-158">See the [samples](#samples) section or use one of the samples listed in the [code sample](#code-sample) section.</span></span>

<span data-ttu-id="24e10-159">Agora que você enviou a mensagem proativa, você deve seguir essas práticas recomendadas ao enviar mensagens proativas para melhor troca de informações entre usuários e o bot.</span><span class="sxs-lookup"><span data-stu-id="24e10-159">Now that you have sent the proactive message, you must follow these best practices while sending proactive messages for better information exchange between users and the bot.</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="24e10-160">Práticas recomendadas para mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="24e10-160">Best practices for proactive messaging</span></span>

<span data-ttu-id="24e10-161">Enviar mensagens proativas aos usuários é uma maneira muito eficaz de se comunicar com seus usuários.</span><span class="sxs-lookup"><span data-stu-id="24e10-161">Sending proactive messages to users is a very effective way to communicate with your users.</span></span> <span data-ttu-id="24e10-162">No entanto, da perspectiva deles, essa mensagem pode parecer completamente não prompada e, no caso de mensagens de boas-vindas, é a primeira vez que elas interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24e10-162">However, from their perspective, this message can appear completely unprompted, and in the case of welcome messages, it is the first time they have interacted with your app.</span></span> <span data-ttu-id="24e10-163">Portanto, é muito importante usar mensagens proativas com moderação, não spam de seus usuários e fornecer informações suficientes para permitir que os usuários entendam por que estão recebendo as mensagens.</span><span class="sxs-lookup"><span data-stu-id="24e10-163">Therefore, it is very important to use proactive messaging sparingly, not spam your users, and provide enough information to let users understand why they are receiving the messages.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="24e10-164">Mensagem de boas-vindas</span><span class="sxs-lookup"><span data-stu-id="24e10-164">Welcome messages</span></span>

<span data-ttu-id="24e10-165">Quando as mensagens proativas são usadas para enviar uma mensagem de boas-vindas a um usuário, não há contexto para o motivo pelo qual os usuários recebem a mensagem.</span><span class="sxs-lookup"><span data-stu-id="24e10-165">When proactive messaging is used to send a welcome message to a user, there is no context for why the users receive the message.</span></span> <span data-ttu-id="24e10-166">Essa também é a primeira vez que os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24e10-166">This is also the first time users interact with your app.</span></span> <span data-ttu-id="24e10-167">É uma oportunidade de criar uma boa primeira impressão.</span><span class="sxs-lookup"><span data-stu-id="24e10-167">It is an opportunity to create a good first impression.</span></span> <span data-ttu-id="24e10-168">As melhores mensagens de boas-vindas devem incluir:</span><span class="sxs-lookup"><span data-stu-id="24e10-168">The best welcome messages must include:</span></span>

* <span data-ttu-id="24e10-169">Por que um usuário está recebendo a mensagem: deve ser muito claro para o usuário o motivo pelo qual ele está recebendo a mensagem.</span><span class="sxs-lookup"><span data-stu-id="24e10-169">Why a user is receiving the message: It must be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="24e10-170">Se o bot foi instalado em um canal e você enviou uma mensagem de boas-vindas a todos os usuários, deixe-os saber em qual canal ele foi instalado e quem o instalou.</span><span class="sxs-lookup"><span data-stu-id="24e10-170">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and who installed it.</span></span>
* <span data-ttu-id="24e10-171">O que você oferece: os usuários devem ser capazes de identificar o que podem fazer com seu aplicativo e qual valor você pode trazer para eles.</span><span class="sxs-lookup"><span data-stu-id="24e10-171">What do you offer: Users must be able to identify what they can do with your app and what value can you bring to them.</span></span>
* <span data-ttu-id="24e10-172">O que eles devem fazer a seguir: convidar os usuários para experimentar um comando ou interagir com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24e10-172">What should they do next: Invite users to try out a command, or interact with your app.</span></span>

<span data-ttu-id="24e10-173">Mensagens de boas-vindas ruins podem levar os usuários a bloquear seu bot.</span><span class="sxs-lookup"><span data-stu-id="24e10-173">Poor welcome messages can lead to users blocking your bot.</span></span> <span data-ttu-id="24e10-174">Escreva até o ponto e limpe as mensagens de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="24e10-174">Write to the point and clear welcome messages.</span></span> <span data-ttu-id="24e10-175">Iterar nas mensagens de boas-vindas se elas não estão tendo o efeito desejado.</span><span class="sxs-lookup"><span data-stu-id="24e10-175">Iterate on the welcome messages if they are not having the desired effect.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="24e10-176">Mensagens de notificação</span><span class="sxs-lookup"><span data-stu-id="24e10-176">Notification messages</span></span>

<span data-ttu-id="24e10-177">Para enviar notificações usando mensagens proativas, certifique-se de que seus usuários tenham um caminho claro para tomar ações comuns com base em sua notificação.</span><span class="sxs-lookup"><span data-stu-id="24e10-177">To send notifications using proactive messaging, ensure your users have a clear path to take common actions based on your notification.</span></span> <span data-ttu-id="24e10-178">Verifique se os usuários têm uma compreensão clara do motivo pelo qual receberam uma notificação.</span><span class="sxs-lookup"><span data-stu-id="24e10-178">Ensure users have a clear understanding of why they have received a notification.</span></span> <span data-ttu-id="24e10-179">As boas mensagens de notificação geralmente incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="24e10-179">Good notification messages generally include the following:</span></span>

* <span data-ttu-id="24e10-180">O que aconteceu: uma indicação clara do que aconteceu para causar a notificação.</span><span class="sxs-lookup"><span data-stu-id="24e10-180">What happened: A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="24e10-181">Qual foi o resultado: deve ser claro qual item foi atualizado para causar a notificação.</span><span class="sxs-lookup"><span data-stu-id="24e10-181">What was the result: It must be clear what item was updated to cause the notification.</span></span>
* <span data-ttu-id="24e10-182">Quem ou o que a acionou: Quem ou o que fez com que a notificação fosse enviada.</span><span class="sxs-lookup"><span data-stu-id="24e10-182">Who or what triggered it: Who or what took action that caused the notification to be sent.</span></span>
* <span data-ttu-id="24e10-183">O que os usuários podem fazer em resposta: facilitar a ação dos usuários com base em suas notificações.</span><span class="sxs-lookup"><span data-stu-id="24e10-183">What can users do in response: Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="24e10-184">Como os usuários podem optar por não fazer isso: você deve fornecer um caminho para que os usuários optem por não receber notificações adicionais.</span><span class="sxs-lookup"><span data-stu-id="24e10-184">How can users opt-out: You must provide a path for users to opt-out of additional notifications.</span></span>

<span data-ttu-id="24e10-185">Para enviar mensagens para um grande grupo de usuários, por exemplo, para sua organização, instale proativamente seu aplicativo usando o Graph.</span><span class="sxs-lookup"><span data-stu-id="24e10-185">To send messages to a large group of users, for example to your organization, proactively install your app using Graph.</span></span>

### <a name="scheduled-messages"></a><span data-ttu-id="24e10-186">Mensagens agendadas</span><span class="sxs-lookup"><span data-stu-id="24e10-186">Scheduled messages</span></span>

<span data-ttu-id="24e10-187">Ao usar mensagens proativas para enviar mensagens agendadas aos usuários, verifique se o fuso horário está atualizado para o fuso horário.</span><span class="sxs-lookup"><span data-stu-id="24e10-187">When using proactive messaging to send scheduled messages to users, verify that your time zone is updated to their time zone.</span></span> <span data-ttu-id="24e10-188">Isso garante que as mensagens sejam entregues aos usuários no momento relevante.</span><span class="sxs-lookup"><span data-stu-id="24e10-188">This ensures that the messages are delivered to the users at the relevant time.</span></span> <span data-ttu-id="24e10-189">As mensagens de agenda geralmente incluem:</span><span class="sxs-lookup"><span data-stu-id="24e10-189">Schedule messages generally include:</span></span>

* <span data-ttu-id="24e10-190">Por que o usuário está recebendo a mensagem: facilmente para os usuários entenderem o motivo pelo qual estão recebendo a mensagem.</span><span class="sxs-lookup"><span data-stu-id="24e10-190">Why is the user receiving the message: Make it easy for your users to understand the reason for which they are receiving the message.</span></span>
* <span data-ttu-id="24e10-191">O que o usuário pode fazer a seguir: os usuários podem tomar a ação necessária com base no conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="24e10-191">What can user do next: Users can take the required action based on the message content.</span></span>

## <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="24e10-192">Instalar proativamente seu aplicativo usando o Graph</span><span class="sxs-lookup"><span data-stu-id="24e10-192">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="24e10-193">A instalação proativa de aplicativos usando o Graph está atualmente na versão beta.</span><span class="sxs-lookup"><span data-stu-id="24e10-193">Proactively installing apps using Graph is currently in beta.</span></span>

<span data-ttu-id="24e10-194">Mensagens proativas de usuários que anteriormente não instalaram ou interagiram com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24e10-194">Proactively message users that have previously not installed or interacted with your app.</span></span> <span data-ttu-id="24e10-195">Por exemplo, você deseja usar o [comunicador da](~/samples/app-templates.md#company-communicator) empresa para enviar mensagens para toda a sua organização.</span><span class="sxs-lookup"><span data-stu-id="24e10-195">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="24e10-196">Nesse caso, você pode usar a API do Graph para instalar proativamente seu aplicativo para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="24e10-196">In this case, you can use the Graph API to proactively install your app for your users.</span></span> <span data-ttu-id="24e10-197">Armazenar em cache os valores necessários `conversationUpdate` do evento que seu aplicativo recebe durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="24e10-197">Cache the necessary values from the `conversationUpdate` event your app receives upon installation.</span></span>

<span data-ttu-id="24e10-198">Você só pode instalar aplicativos que estão no catálogo de aplicativos organizacionais ou na Loja de Aplicativos do Teams.</span><span class="sxs-lookup"><span data-stu-id="24e10-198">You can only install apps that are in your organizational app catalog or the Teams App Store.</span></span>

<span data-ttu-id="24e10-199">Consulte [instalar aplicativos para usuários na](/graph/api/userteamwork-post-installedapps) documentação do Graph e instalação proativa de bots e mensagens no Teams com [Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span><span class="sxs-lookup"><span data-stu-id="24e10-199">See [install apps for users](/graph/api/userteamwork-post-installedapps) in the Graph documentation and [proactive bot installation and messaging in Teams with Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span></span> <span data-ttu-id="24e10-200">Também há um exemplo [de estrutura do Microsoft .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) na plataforma GitHub.</span><span class="sxs-lookup"><span data-stu-id="24e10-200">There is also a [Microsoft .NET framework sample](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) on the GitHub platform.</span></span>

## <a name="samples"></a><span data-ttu-id="24e10-201">Exemplos</span><span class="sxs-lookup"><span data-stu-id="24e10-201">Samples</span></span>

<span data-ttu-id="24e10-202">O código a seguir mostra um exemplo de código simples que instala proativamente seu aplicativo usando Graph:</span><span class="sxs-lookup"><span data-stu-id="24e10-202">The following code shows a simple code sample that proactively installs your app using Graph:</span></span>

# <a name="c"></a>[<span data-ttu-id="24e10-203">C#</span><span class="sxs-lookup"><span data-stu-id="24e10-203">C#</span></span>](#tab/dotnet)

```csharp
[Route("api/notify")]
[ApiController]
public class NotifyController : ControllerBase
{
    private readonly IBotFrameworkHttpAdapter _adapter;
    private readonly string _appId;
    private readonly ConcurrentDictionary<string, ConversationReference> _conversationReferences;

    public NotifyController(IBotFrameworkHttpAdapter adapter, IConfiguration configuration, ConcurrentDictionary<string, ConversationReference> conversationReferences)
    {
        _adapter = adapter;
        _conversationReferences = conversationReferences;
        _appId = configuration["MicrosoftAppId"] ?? string.Empty;
    }

    public async Task<IActionResult> Get()
    {
        foreach (var conversationReference in _conversationReferences.Values)
        {
            await ((BotAdapter)_adapter).ContinueConversationAsync(_appId, conversationReference, BotCallback, default(CancellationToken));
        }
        
        // Let the caller know proactive messages have been sent
        return new ContentResult()
        {
            Content = "<html><body><h1>Proactive messages have been sent.</h1></body></html>",
            ContentType = "text/html",
            StatusCode = (int)HttpStatusCode.OK,
        };
    }

    private async Task BotCallback(ITurnContext turnContext, CancellationToken cancellationToken)
    {
        // If you encounter permission-related errors when sending this message, see
        // https://aka.ms/BotTrustServiceUrl
        await turnContext.SendActivityAsync("proactive hello");
    }
}
```

# <a name="typescript"></a>[<span data-ttu-id="24e10-204">TypeScript</span><span class="sxs-lookup"><span data-stu-id="24e10-204">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="24e10-205">Python</span><span class="sxs-lookup"><span data-stu-id="24e10-205">Python</span></span>](#tab/python)

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

# <a name="json"></a>[<span data-ttu-id="24e10-206">JSON</span><span class="sxs-lookup"><span data-stu-id="24e10-206">JSON</span></span>](#tab/json)

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

<span data-ttu-id="24e10-207">Você deve fornecer a ID do usuário e a ID do locatário.</span><span class="sxs-lookup"><span data-stu-id="24e10-207">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="24e10-208">Se a chamada for bem-sucedida, a API retornará o seguinte objeto de resposta:</span><span class="sxs-lookup"><span data-stu-id="24e10-208">If the call succeeds, the API returns the following response object:</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

> [!NOTE]
> <span data-ttu-id="24e10-209">Atualmente, os bots não podem criar um chat de grupo por meio de APIs de bot ou Graph.</span><span class="sxs-lookup"><span data-stu-id="24e10-209">Currently bots cannot create a group chat through bot APIs or Graph.</span></span> <span data-ttu-id="24e10-210">`createConversation` está disponível apenas para chats 1:1.</span><span class="sxs-lookup"><span data-stu-id="24e10-210">`createConversation` is available only for 1:1 chats.</span></span>

## <a name="code-sample"></a><span data-ttu-id="24e10-211">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="24e10-211">Code sample</span></span>

<span data-ttu-id="24e10-212">A tabela a seguir fornece um exemplo de código simples que incorpora o fluxo básico de conversa em um aplicativo Teams e como criar um novo thread de conversa em um canal em Teams:</span><span class="sxs-lookup"><span data-stu-id="24e10-212">The following table provides a simple code sample that incorporate basic conversation flow into a Teams application and how to create a new conversation thread in a channel in Teams:</span></span>

| <span data-ttu-id="24e10-213">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="24e10-213">**Sample Name**</span></span> | <span data-ttu-id="24e10-214">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="24e10-214">**Description**</span></span> | <span data-ttu-id="24e10-215">**.NET**</span><span class="sxs-lookup"><span data-stu-id="24e10-215">**.NET**</span></span> | <span data-ttu-id="24e10-216">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="24e10-216">**Node.js**</span></span> | <span data-ttu-id="24e10-217">**Python**</span><span class="sxs-lookup"><span data-stu-id="24e10-217">**Python**</span></span> |
|---------------|--------------|--------|-------------|--------|
| <span data-ttu-id="24e10-218">Teams Noções básicas de conversa</span><span class="sxs-lookup"><span data-stu-id="24e10-218">Teams Conversation Basics</span></span>  | <span data-ttu-id="24e10-219">Demonstra noções básicas de conversas Teams, incluindo o envio de mensagens proativas um para um.</span><span class="sxs-lookup"><span data-stu-id="24e10-219">Demonstrates basics of conversations in Teams, including sending one-to-one proactive messages.</span></span>| [<span data-ttu-id="24e10-220">View</span><span class="sxs-lookup"><span data-stu-id="24e10-220">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot) | [<span data-ttu-id="24e10-221">View</span><span class="sxs-lookup"><span data-stu-id="24e10-221">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="24e10-222">View</span><span class="sxs-lookup"><span data-stu-id="24e10-222">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot) |
| <span data-ttu-id="24e10-223">Iniciar novo thread em um canal</span><span class="sxs-lookup"><span data-stu-id="24e10-223">Start new thread in a channel</span></span> | <span data-ttu-id="24e10-224">Demonstra a criação de um novo thread em um canal.</span><span class="sxs-lookup"><span data-stu-id="24e10-224">Demonstrates creating a new thread in a channel.</span></span> | [<span data-ttu-id="24e10-225">View</span><span class="sxs-lookup"><span data-stu-id="24e10-225">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel) | [<span data-ttu-id="24e10-226">View</span><span class="sxs-lookup"><span data-stu-id="24e10-226">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel) | [<span data-ttu-id="24e10-227">View</span><span class="sxs-lookup"><span data-stu-id="24e10-227">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

### <a name="additional-code-sample"></a><span data-ttu-id="24e10-228">Exemplo de código adicional</span><span class="sxs-lookup"><span data-stu-id="24e10-228">Additional code sample</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="24e10-229">Teams exemplos proativos de código de mensagens</span><span class="sxs-lookup"><span data-stu-id="24e10-229">Teams proactive messaging code samples</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)

## <a name="see-also"></a><span data-ttu-id="24e10-230">Confira também</span><span class="sxs-lookup"><span data-stu-id="24e10-230">See also</span></span>

[<span data-ttu-id="24e10-231">**Teams exemplos proativos de código de mensagens**</span><span class="sxs-lookup"><span data-stu-id="24e10-231">**Teams proactive messaging code samples**</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)

## <a name="next-step"></a><span data-ttu-id="24e10-232">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="24e10-232">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="24e10-233">Formatar suas mensagens de bot</span><span class="sxs-lookup"><span data-stu-id="24e10-233">Format your bot messages</span></span>](~/bots/how-to/format-your-bot-messages.md)
