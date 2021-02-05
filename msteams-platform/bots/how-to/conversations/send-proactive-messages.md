---
title: enviar mensagens proativas
description: descreve como enviar mensagens proativas com seu bot do Microsoft Teams.
ms.topic: overview
ms.author: anclear
Keywords: enviar uma mensagem obter a ID de conversa do canal de ID do usuário
ms.openlocfilehash: 2d7ff10469a181bb06fda5029c8f6b2725b0402d
ms.sourcegitcommit: 7db6eabe3ef128ac7f14b32d07e9e86c995d187f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2021
ms.locfileid: "50103602"
---
# <a name="send-proactive-messages"></a><span data-ttu-id="6aa28-104">Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="6aa28-104">Send proactive messages</span></span>

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="6aa28-105">Uma mensagem proativa é qualquer mensagem enviada por um bot que não está em resposta direta a uma solicitação de um usuário.</span><span class="sxs-lookup"><span data-stu-id="6aa28-105">A proactive message is any message sent by a bot that is not in direct response to a request from a user.</span></span> <span data-ttu-id="6aa28-106">Isso pode incluir mensagens como:</span><span class="sxs-lookup"><span data-stu-id="6aa28-106">This can include messages like:</span></span>

* <span data-ttu-id="6aa28-107">Mensagens de boas-vindas</span><span class="sxs-lookup"><span data-stu-id="6aa28-107">Welcome messages</span></span>
* <span data-ttu-id="6aa28-108">Notificações</span><span class="sxs-lookup"><span data-stu-id="6aa28-108">Notifications</span></span>
* <span data-ttu-id="6aa28-109">Mensagens agendadas</span><span class="sxs-lookup"><span data-stu-id="6aa28-109">Scheduled messages</span></span>

<span data-ttu-id="6aa28-110">Para que seu bot envie uma mensagem proativa, ele deve ter acesso ao usuário, chat em grupo ou equipe para a quem você deseja enviar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="6aa28-110">For your bot to send a proactive message, it must have access to the user, group chat, or team that you want to send the message to.</span></span> <span data-ttu-id="6aa28-111">Para um chat ou uma equipe de grupo, isso significa que o aplicativo que contém seu bot deve ser instalado nesse local primeiro.</span><span class="sxs-lookup"><span data-stu-id="6aa28-111">For a group chat or team, this means the app that contains your bot must be installed to that location first.</span></span> <span data-ttu-id="6aa28-112">Você pode [instalar proativamente](#proactively-install-your-app-using-graph) seu aplicativo usando o Graph [](/microsoftteams/teams-custom-app-policies-and-settings) em uma equipe, se necessário, ou usar uma política de aplicativo para por push de aplicativos para equipes e usuários em seu locatário.</span><span class="sxs-lookup"><span data-stu-id="6aa28-112">You can [proactively install your app using Graph](#proactively-install-your-app-using-graph) in a team, if required or use an [app policy](/microsoftteams/teams-custom-app-policies-and-settings) to push apps out to teams and users in your tenant.</span></span> <span data-ttu-id="6aa28-113">Para os usuários, seu aplicativo deve ser instalado para o usuário ou o usuário deve fazer parte de uma equipe em que seu aplicativo está instalado.</span><span class="sxs-lookup"><span data-stu-id="6aa28-113">For users, your app either must be installed for the user or your user must be part of a team where your app is installed.</span></span>

<span data-ttu-id="6aa28-114">Enviar uma mensagem proativa é diferente de enviar uma mensagem normal.</span><span class="sxs-lookup"><span data-stu-id="6aa28-114">Sending a proactive message is different than sending a regular message.</span></span> <span data-ttu-id="6aa28-115">In that, there is no active `turnContext` to use for a reply.</span><span class="sxs-lookup"><span data-stu-id="6aa28-115">In that, there is no active `turnContext` to use for a reply.</span></span> <span data-ttu-id="6aa28-116">Talvez também seja necessário criar a conversa antes de enviar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="6aa28-116">You may also need to create the conversation before sending the message.</span></span> <span data-ttu-id="6aa28-117">Por exemplo, um novo chat um-para-um ou um novo thread de conversa em um canal.</span><span class="sxs-lookup"><span data-stu-id="6aa28-117">For example, a new one-to-one chat or a new conversation thread in a channel.</span></span> <span data-ttu-id="6aa28-118">Você não pode criar um novo chat em grupo ou um novo canal em uma equipe com mensagens proativas.</span><span class="sxs-lookup"><span data-stu-id="6aa28-118">You cannot create a new group chat or a new channel in a team with proactive messaging.</span></span>

<span data-ttu-id="6aa28-119">Em um nível alto, as etapas que você precisará concluir para enviar uma mensagem proativa são:</span><span class="sxs-lookup"><span data-stu-id="6aa28-119">At a high level the steps you'll need to complete to send a proactive message are:</span></span>

1. <span data-ttu-id="6aa28-120">[Obter a ID de usuário ou a ID de equipe/canal](#get-the-user-id-or-teamchannel-id) (se necessário).</span><span class="sxs-lookup"><span data-stu-id="6aa28-120">[Get the user ID or team/channel ID](#get-the-user-id-or-teamchannel-id) (if needed).</span></span>
1. <span data-ttu-id="6aa28-121">[Crie o thread de conversa ou conversa](#create-the-conversation) (se necessário).</span><span class="sxs-lookup"><span data-stu-id="6aa28-121">[Create the conversation or conversation thread](#create-the-conversation) (if needed).</span></span>
1. <span data-ttu-id="6aa28-122">[Obter a ID da conversa.](#get-the-conversation-id)</span><span class="sxs-lookup"><span data-stu-id="6aa28-122">[Get the conversation ID](#get-the-conversation-id).</span></span>
1. <span data-ttu-id="6aa28-123">[Envie a mensagem.](#send-the-message)</span><span class="sxs-lookup"><span data-stu-id="6aa28-123">[Send the message](#send-the-message).</span></span>

<span data-ttu-id="6aa28-124">Os trechos de código na seção [de exemplos](#examples) são para criar uma conversa um-para-um.</span><span class="sxs-lookup"><span data-stu-id="6aa28-124">The code snippets in the [examples](#examples) section are for creating a one-to-one conversation.</span></span> <span data-ttu-id="6aa28-125">Para links para concluir amostras de trabalho para conversas de um para um e grupo ou canais, consulte [exemplos de código.](#code-samples)</span><span class="sxs-lookup"><span data-stu-id="6aa28-125">For links to complete working samples for both one-to-one conversations and group or channels , see [code samples](#code-samples).</span></span>

## <a name="get-the-user-id-or-teamchannel-id"></a><span data-ttu-id="6aa28-126">Obter a ID de usuário ou a ID de equipe/canal</span><span class="sxs-lookup"><span data-stu-id="6aa28-126">Get the user ID or team/channel ID</span></span>

<span data-ttu-id="6aa28-127">Para criar um novo thread de conversa ou conversa em um canal, você precisa da ID correta.</span><span class="sxs-lookup"><span data-stu-id="6aa28-127">To create a new conversation or conversation thread in a channel, you need the correct ID.</span></span> <span data-ttu-id="6aa28-128">Você pode receber ou recuperar essa ID de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="6aa28-128">You can receive or retrieve this ID in multiple ways:</span></span>

1. <span data-ttu-id="6aa28-129">Quando seu aplicativo for instalado em qualquer contexto específico, você receberá uma [ `onMembersAdded` Atividade.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="6aa28-129">When your app is installed in any particular context, you'll receive a [`onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
1. <span data-ttu-id="6aa28-130">Quando um novo usuário é adicionado a um contexto em que seu aplicativo está instalado, você receberá uma [ `onMembersAdded` Atividade.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="6aa28-130">When a new user is added to a context where your app is installed, you'll receive a [`onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
1. <span data-ttu-id="6aa28-131">Você pode recuperar a [lista de canais](~/bots/how-to/get-teams-context.md) em uma equipe em que seu aplicativo está instalado.</span><span class="sxs-lookup"><span data-stu-id="6aa28-131">You can retrieve the [list of channels](~/bots/how-to/get-teams-context.md) in a team your app is installed.</span></span>
1. <span data-ttu-id="6aa28-132">Você pode recuperar a [lista de membros](~/bots/how-to/get-teams-context.md) de uma equipe em que seu aplicativo está instalado.</span><span class="sxs-lookup"><span data-stu-id="6aa28-132">You can retrieve the [list of members](~/bots/how-to/get-teams-context.md) of a team your app is installed.</span></span>
1. <span data-ttu-id="6aa28-133">Todas as atividades que seu bot recebe devem conter as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="6aa28-133">Every Activity your bot receives must contain the required information.</span></span>

<span data-ttu-id="6aa28-134">Independentemente de como você obtenha as informações, será necessário armazenar o ou criar `tenantId` `userId` uma nova `channelId` conversa.</span><span class="sxs-lookup"><span data-stu-id="6aa28-134">Regardless of how you gain the information, you'll need to store the `tenantId` and either the `userId` or `channelId` to create a new conversation.</span></span> <span data-ttu-id="6aa28-135">Você também pode usar o `teamId` para criar um novo thread de conversa no canal geral ou padrão de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="6aa28-135">You can also use the `teamId` to create a new conversation thread in the general or default channel of a team.</span></span>

<span data-ttu-id="6aa28-136">Ela `userId` é exclusiva para sua ID de bot e um usuário específico, você não pode re usá-los entre bots.</span><span class="sxs-lookup"><span data-stu-id="6aa28-136">The `userId` is unique to your bot Id and a particular user, you cannot re-use them between bots.</span></span> <span data-ttu-id="6aa28-137">No entanto, é global, seu bot deve ser instalado na equipe antes que você possa enviar uma mensagem `channelId` proativa para um canal.</span><span class="sxs-lookup"><span data-stu-id="6aa28-137">The `channelId` is global, however, your bot must be installed in the team before you can send a proactive message to a channel.</span></span>

## <a name="create-the-conversation"></a><span data-ttu-id="6aa28-138">Criar a conversa</span><span class="sxs-lookup"><span data-stu-id="6aa28-138">Create the conversation</span></span>

<span data-ttu-id="6aa28-139">Depois de ter as informações do usuário ou do canal, você precisará criar a conversa se ela ainda não existir ou você não sabe o `conversationId` .</span><span class="sxs-lookup"><span data-stu-id="6aa28-139">After you have the user or channel information, you need to create the conversation if it doesn't already exist or you don't know the `conversationId`.</span></span> <span data-ttu-id="6aa28-140">Você só deve criar a conversa uma vez e certificar-se de armazenar o `conversationId` valor ou objeto a ser usado no `conversationReference` futuro.</span><span class="sxs-lookup"><span data-stu-id="6aa28-140">You must only create the conversation once and make sure you store the `conversationId` value or `conversationReference` object to use in the future.</span></span>

## <a name="get-the-conversation-id"></a><span data-ttu-id="6aa28-141">Obter a ID da conversa</span><span class="sxs-lookup"><span data-stu-id="6aa28-141">Get the conversation ID</span></span>

<span data-ttu-id="6aa28-142">Depois que a conversa for criada, use o `conversationReference` objeto ou e envie a `conversationId` `tenantId` mensagem.</span><span class="sxs-lookup"><span data-stu-id="6aa28-142">After the conversation is created, use either the `conversationReference` object or `conversationId` and `tenantId` to send the message.</span></span> <span data-ttu-id="6aa28-143">Você pode obter essa ID criando a conversa ou armazenar a partir de qualquer Atividade enviada a você a partir desse contexto.</span><span class="sxs-lookup"><span data-stu-id="6aa28-143">You can get this ID by either creating the conversation or storing it from any Activity sent to you from that context.</span></span> <span data-ttu-id="6aa28-144">Certifique-se de armazenar essa ID.</span><span class="sxs-lookup"><span data-stu-id="6aa28-144">Make certain that you store this ID.</span></span>

## <a name="send-the-message"></a><span data-ttu-id="6aa28-145">Enviar a mensagem</span><span class="sxs-lookup"><span data-stu-id="6aa28-145">Send the message</span></span>

<span data-ttu-id="6aa28-146">Agora que você tem as informações de endereço corretas, pode enviar sua mensagem.</span><span class="sxs-lookup"><span data-stu-id="6aa28-146">Now that you have the right address information, you can send your message.</span></span> <span data-ttu-id="6aa28-147">Se você estiver usando o SDK, você fará isso usando o método e o e para `continueConversation` fazer uma chamada direta à `conversationId` `tenantId` API.</span><span class="sxs-lookup"><span data-stu-id="6aa28-147">If you're using the SDK, you'll do so using the `continueConversation` method, and the `conversationId` and `tenantId` to make a direct API call.</span></span> <span data-ttu-id="6aa28-148">Você deve definir o `conversationParameters` corretamente para enviar sua mensagem com êxito.</span><span class="sxs-lookup"><span data-stu-id="6aa28-148">You must set the `conversationParameters` correctly to successfully send your message.</span></span> <span data-ttu-id="6aa28-149">Consulte a [seção de exemplos](#examples) ou use um dos exemplos listados na seção [de exemplos de](#code-samples) código.</span><span class="sxs-lookup"><span data-stu-id="6aa28-149">See the [examples](#examples) section or use one of the samples listed in the [code samples](#code-samples) section.</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="6aa28-150">Práticas recomendadas para mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="6aa28-150">Best practices for proactive messaging</span></span>

<span data-ttu-id="6aa28-151">Enviar mensagens proativas aos usuários é uma maneira muito eficaz de se comunicar com seus usuários.</span><span class="sxs-lookup"><span data-stu-id="6aa28-151">Sending proactive messages to users is a very effective way to communicate with your users.</span></span> <span data-ttu-id="6aa28-152">No entanto, de acordo com a perspectiva, essa mensagem pode parecer completamente nãompida e, no caso de mensagens de boas-vindas, é a primeira vez que elas interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6aa28-152">However, from their perspective, this message can appear completely unprompted, and in the case of welcome messages, it is the first time they have interacted with your app.</span></span> <span data-ttu-id="6aa28-153">Portanto, é muito importante usar essa funcionalidade com moderação, não enviar spam para os usuários e fornecer informações suficientes para permitir que os usuários entendam por que estão sendo mensagens.</span><span class="sxs-lookup"><span data-stu-id="6aa28-153">Therefore, it is very important to use this functionality sparingly, don't spam your users, and to provide enough information to let users understand why they are being messaged.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="6aa28-154">Mensagens de boas-vindas</span><span class="sxs-lookup"><span data-stu-id="6aa28-154">Welcome messages</span></span>

<span data-ttu-id="6aa28-155">Ao usar mensagens proativas para enviar uma mensagem de boas-vindas a um usuário, você deve ter em mente que, para a maioria das pessoas que recebem a mensagem, não há contexto para o motivo pelo qual elas a estão recebendo.</span><span class="sxs-lookup"><span data-stu-id="6aa28-155">When using proactive messaging to send a welcome message to a user you must keep in mind that, for most people receiving the message, there is no context for why they are receiving it.</span></span> <span data-ttu-id="6aa28-156">Essa também é a primeira vez que eles interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6aa28-156">This is also the first time they have interacted with your app.</span></span> <span data-ttu-id="6aa28-157">É sua oportunidade de criar uma boa primeira impressão.</span><span class="sxs-lookup"><span data-stu-id="6aa28-157">It is your opportunity to create a good first impression.</span></span> <span data-ttu-id="6aa28-158">As melhores mensagens de boas-vindas devem incluir:</span><span class="sxs-lookup"><span data-stu-id="6aa28-158">The best welcome messages must include:</span></span>

* <span data-ttu-id="6aa28-159">**Por que um usuário está recebendo a mensagem.**</span><span class="sxs-lookup"><span data-stu-id="6aa28-159">**Why a user is receiving the message.**</span></span> <span data-ttu-id="6aa28-160">Deve ser muito claro para o usuário por que ele está recebendo a mensagem.</span><span class="sxs-lookup"><span data-stu-id="6aa28-160">It must be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="6aa28-161">Se o bot foi instalado em um canal e você enviou uma mensagem de boas-vindas a todos os usuários, avise em qual canal ele foi instalado e, potencialmente, quem o instalou.</span><span class="sxs-lookup"><span data-stu-id="6aa28-161">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and potentially who installed it.</span></span>
* <span data-ttu-id="6aa28-162">**O que você oferece.**</span><span class="sxs-lookup"><span data-stu-id="6aa28-162">**What do you offer.**</span></span> <span data-ttu-id="6aa28-163">O que eles podem fazer com seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="6aa28-163">What can they do with your app?</span></span> <span data-ttu-id="6aa28-164">Qual valor você pode trazer para eles?</span><span class="sxs-lookup"><span data-stu-id="6aa28-164">What value can you bring to them?</span></span>
* <span data-ttu-id="6aa28-165">**O que eles devem fazer em seguida.**</span><span class="sxs-lookup"><span data-stu-id="6aa28-165">**What should they do next.**</span></span> <span data-ttu-id="6aa28-166">Convide-os para experimentar um comando ou interagir com seu aplicativo de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="6aa28-166">Invite them to try out a command, or interact with your app in some way.</span></span>

<span data-ttu-id="6aa28-167">Lembre-se de que mensagens de boas-vindas ruins podem fazer com que os usuários bloqueem seu bot.</span><span class="sxs-lookup"><span data-stu-id="6aa28-167">Remember, poor welcome messages can lead to users blocking your bot.</span></span> <span data-ttu-id="6aa28-168">Passe muito tempo preparando suas mensagens de boas-vindas e itere neles se elas não estão tendo o efeito desejado.</span><span class="sxs-lookup"><span data-stu-id="6aa28-168">Spend plenty of time crafting your welcome messages, and iterate on them if they are not having the desired effect.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="6aa28-169">Mensagens de notificação</span><span class="sxs-lookup"><span data-stu-id="6aa28-169">Notification messages</span></span>

<span data-ttu-id="6aa28-170">Ao usar mensagens proativas para enviar notificações, você deve garantir que seus usuários tenham um caminho claro para tomar ações comuns com base em sua notificação e um entendimento claro do motivo pelo qual a notificação ocorreu.</span><span class="sxs-lookup"><span data-stu-id="6aa28-170">When using proactive messaging to send notifications you must ensure your users have a clear path to take common actions based on your notification and a clear understanding of why the notification occurred.</span></span> <span data-ttu-id="6aa28-171">As mensagens de notificação boas geralmente incluem:</span><span class="sxs-lookup"><span data-stu-id="6aa28-171">Good notification messages generally include:</span></span>

* <span data-ttu-id="6aa28-172">**O que aconteceu.**</span><span class="sxs-lookup"><span data-stu-id="6aa28-172">**What happened.**</span></span> <span data-ttu-id="6aa28-173">Uma indicação clara do que causou a notificação.</span><span class="sxs-lookup"><span data-stu-id="6aa28-173">A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="6aa28-174">**Qual foi o resultado.**</span><span class="sxs-lookup"><span data-stu-id="6aa28-174">**What was the result.**</span></span> <span data-ttu-id="6aa28-175">Deve ser claro qual item ou coisa foi atualizado para causar a notificação.</span><span class="sxs-lookup"><span data-stu-id="6aa28-175">It must be clear what item or thing was updated to cause the notification.</span></span>
* <span data-ttu-id="6aa28-176">**Quem/o que a disparou.**</span><span class="sxs-lookup"><span data-stu-id="6aa28-176">**Who/what triggered it.**</span></span> <span data-ttu-id="6aa28-177">Quem ou o que fez com que a notificação fosse enviada.</span><span class="sxs-lookup"><span data-stu-id="6aa28-177">Who or what took action that caused the notification to be sent.</span></span>
* <span data-ttu-id="6aa28-178">**O que os usuários podem fazer em resposta.**</span><span class="sxs-lookup"><span data-stu-id="6aa28-178">**What can users do in response.**</span></span> <span data-ttu-id="6aa28-179">Facilmente para os usuários tomarem ações com base em suas notificações.</span><span class="sxs-lookup"><span data-stu-id="6aa28-179">Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="6aa28-180">**Como os usuários podem optar por não fazer isso.** Você deve fornecer um caminho para que os usuários retivem notificações adicionais.</span><span class="sxs-lookup"><span data-stu-id="6aa28-180">**How can users opt out.** You must provide a path for users to opt out of additional notifications.</span></span>

## <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="6aa28-181">Instalar seu aplicativo proativamente usando o Graph</span><span class="sxs-lookup"><span data-stu-id="6aa28-181">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="6aa28-182">A instalação proativa de aplicativos usando o Microsoft Graph está atualmente na versão beta.</span><span class="sxs-lookup"><span data-stu-id="6aa28-182">Proactively installing apps using the Microsoft Graph is currently in beta.</span></span>

<span data-ttu-id="6aa28-183">Ocasionalmente, pode ser necessário mensagens proativas de usuários que não tenham instalado ou interagido com seu aplicativo anteriormente.</span><span class="sxs-lookup"><span data-stu-id="6aa28-183">Occasionally it may be necessary to proactively message users that have not installed or interacted with your app previously.</span></span> <span data-ttu-id="6aa28-184">Por exemplo, você deseja usar o [comunicador da empresa](~/samples/app-templates.md#company-communicator) para enviar mensagens para toda a organização.</span><span class="sxs-lookup"><span data-stu-id="6aa28-184">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="6aa28-185">Para esse cenário, você pode usar a API do Graph para instalar seu aplicativo proativamente para seus usuários e, em seguida, armazenar em cache os valores necessários do evento que seu aplicativo recebe `conversationUpdate` na instalação.</span><span class="sxs-lookup"><span data-stu-id="6aa28-185">For this scenario you can use the Graph API to proactively install your app for your users, then cache the necessary values from the `conversationUpdate` event your app receives upon installation.</span></span>

<span data-ttu-id="6aa28-186">Você só pode instalar aplicativos que estão no catálogo de aplicativos organizacionais ou na loja de aplicativos do Teams.</span><span class="sxs-lookup"><span data-stu-id="6aa28-186">You can only install apps that are in your organizational app catalog or the Teams app store.</span></span>

<span data-ttu-id="6aa28-187">Consulte [Instalar aplicativos para usuários na](/graph/api/userteamwork-post-installedapps) documentação do Graph e instalação de bot proativo e mensagens no Teams com o Microsoft [Graph.](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md)</span><span class="sxs-lookup"><span data-stu-id="6aa28-187">See [Install apps for users](/graph/api/userteamwork-post-installedapps) in the Graph documentation and [Proactive bot installation and messaging in Teams with Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span></span> <span data-ttu-id="6aa28-188">Há também um [exemplo do Microsoft .NET Framework](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) na plataforma GitHub.</span><span class="sxs-lookup"><span data-stu-id="6aa28-188">There is also a [Microsoft .NET framework sample](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) on the GitHub platform.</span></span>

## <a name="examples"></a><span data-ttu-id="6aa28-189">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6aa28-189">Examples</span></span>

# <a name="cnet"></a>[<span data-ttu-id="6aa28-190">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="6aa28-190">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="6aa28-191">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="6aa28-191">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="6aa28-192">Python</span><span class="sxs-lookup"><span data-stu-id="6aa28-192">Python</span></span>](#tab/python)

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

# <a name="json"></a>[<span data-ttu-id="6aa28-193">JSON</span><span class="sxs-lookup"><span data-stu-id="6aa28-193">JSON</span></span>](#tab/json)

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

<span data-ttu-id="6aa28-194">Você deve fornecer a ID de usuário e a ID do locatário.</span><span class="sxs-lookup"><span data-stu-id="6aa28-194">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="6aa28-195">Se a chamada for bem-sucedida, a API retornará com o seguinte objeto de resposta.</span><span class="sxs-lookup"><span data-stu-id="6aa28-195">If the call succeeds, the API returns with the following response object.</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-samples"></a><span data-ttu-id="6aa28-196">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="6aa28-196">Code samples</span></span>

<span data-ttu-id="6aa28-197">Os exemplos oficiais de mensagens proativas são os seguinte:</span><span class="sxs-lookup"><span data-stu-id="6aa28-197">The official proactive messaging samples are as follows:</span></span>

| <span data-ttu-id="6aa28-198">Nome do exemplo</span><span class="sxs-lookup"><span data-stu-id="6aa28-198">Sample Name</span></span>           | <span data-ttu-id="6aa28-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="6aa28-199">Description</span></span>                                                                      | <span data-ttu-id="6aa28-200">.NET</span><span class="sxs-lookup"><span data-stu-id="6aa28-200">.NET</span></span>    | <span data-ttu-id="6aa28-201">JavaScript</span><span class="sxs-lookup"><span data-stu-id="6aa28-201">JavaScript</span></span>   | <span data-ttu-id="6aa28-202">Python</span><span class="sxs-lookup"><span data-stu-id="6aa28-202">Python</span></span>  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|<span data-ttu-id="6aa28-203">Noções básicas de conversa do Teams</span><span class="sxs-lookup"><span data-stu-id="6aa28-203">Teams Conversation Basics</span></span>  | <span data-ttu-id="6aa28-204">Demonstra noções básicas de conversas no Teams, incluindo o envio de mensagens proativas um-para-um.</span><span class="sxs-lookup"><span data-stu-id="6aa28-204">Demonstrates basics of conversations in Teams, including sending one-to-one proactive messages.</span></span>|[<span data-ttu-id="6aa28-205">.NET &nbsp; Core</span><span class="sxs-lookup"><span data-stu-id="6aa28-205">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="6aa28-206">JavaScript</span><span class="sxs-lookup"><span data-stu-id="6aa28-206">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="6aa28-207">Python</span><span class="sxs-lookup"><span data-stu-id="6aa28-207">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|<span data-ttu-id="6aa28-208">Iniciar novo thread em um canal</span><span class="sxs-lookup"><span data-stu-id="6aa28-208">Start new thread in a channel</span></span>     | <span data-ttu-id="6aa28-209">Demonstra a criação de um novo thread em um canal.</span><span class="sxs-lookup"><span data-stu-id="6aa28-209">Demonstrates creating a new thread in a channel.</span></span> |[<span data-ttu-id="6aa28-210">.NET &nbsp; Core</span><span class="sxs-lookup"><span data-stu-id="6aa28-210">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[<span data-ttu-id="6aa28-211">JavaScript</span><span class="sxs-lookup"><span data-stu-id="6aa28-211">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[<span data-ttu-id="6aa28-212">Python</span><span class="sxs-lookup"><span data-stu-id="6aa28-212">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

## <a name="view-additional-code-samples"></a><span data-ttu-id="6aa28-213">Exibir exemplos de código adicionais</span><span class="sxs-lookup"><span data-stu-id="6aa28-213">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="6aa28-214">**Exemplos proativos de código de mensagens do Teams**</span><span class="sxs-lookup"><span data-stu-id="6aa28-214">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
