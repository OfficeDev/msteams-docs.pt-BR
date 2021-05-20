---
title: Mensagens proativas
description: Descreve que bots podem iniciar uma conversa em Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: cenários de equipes proativo troca de mensagens bot
ms.openlocfilehash: baf148d0f4d0a669de582dfca70ed5d5bed0274c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566786"
---
# <a name="proactive-messaging-for-bots"></a><span data-ttu-id="05d0f-104">Mensagens proativas para bots</span><span class="sxs-lookup"><span data-stu-id="05d0f-104">Proactive messaging for bots</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="05d0f-105">Uma mensagem proativa é uma mensagem enviada por um bot para iniciar uma conversa.</span><span class="sxs-lookup"><span data-stu-id="05d0f-105">A proactive message is a message that is sent by a bot to start a conversation.</span></span> <span data-ttu-id="05d0f-106">Talvez você queira que seu bot inicie uma conversa por vários motivos, incluindo:</span><span class="sxs-lookup"><span data-stu-id="05d0f-106">You may want your bot to start a conversation for a number of reasons, including:</span></span>

* <span data-ttu-id="05d0f-107">Mensagens de boas-vindas para conversas pessoais de bots.</span><span class="sxs-lookup"><span data-stu-id="05d0f-107">Welcome messages for personal bot conversations.</span></span>
* <span data-ttu-id="05d0f-108">Respostas nas pesquisas.</span><span class="sxs-lookup"><span data-stu-id="05d0f-108">Poll responses.</span></span>
* <span data-ttu-id="05d0f-109">Notificações externas de eventos.</span><span class="sxs-lookup"><span data-stu-id="05d0f-109">External event notifications.</span></span>

<span data-ttu-id="05d0f-110">Enviar uma mensagem para iniciar um novo segmento de conversação é diferente de enviar uma mensagem em resposta a uma conversa existente: quando seu bot inicia uma nova conversa, não há conversa pré-existente para postar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="05d0f-110">Sending a message to start a new conversation thread is different than sending a message in response to an existing conversation: when your bot starts a new a conversation, there is no pre-existing conversation to post the message to.</span></span> <span data-ttu-id="05d0f-111">Para enviar uma mensagem proativa, você precisa:</span><span class="sxs-lookup"><span data-stu-id="05d0f-111">In order to send a proactive message you need to:</span></span>

1. [<span data-ttu-id="05d0f-112">Decida o que você vai dizer</span><span class="sxs-lookup"><span data-stu-id="05d0f-112">Decide what you're going to say</span></span>](#best-practices-for-proactive-messaging)
1. [<span data-ttu-id="05d0f-113">Obtenha a identificação única do usuário e o ID do inquilino</span><span class="sxs-lookup"><span data-stu-id="05d0f-113">Obtain the user's unique Id and tenant Id</span></span>](#obtain-necessary-user-information)
1. [<span data-ttu-id="05d0f-114">Enviar a mensagem</span><span class="sxs-lookup"><span data-stu-id="05d0f-114">Send the message</span></span>](#examples)

<span data-ttu-id="05d0f-115">Ao criar mensagens proativas, você **deve** ligar `MicrosoftAppCredentials.TrustServiceUrl` e passar na URL do serviço antes de criar a que você usará para enviar `ConnectorClient` a mensagem.</span><span class="sxs-lookup"><span data-stu-id="05d0f-115">When creating proactive messages you **must** call `MicrosoftAppCredentials.TrustServiceUrl`, and pass in the service URL before creating the `ConnectorClient` you will use to send the message.</span></span> <span data-ttu-id="05d0f-116">Se você não fizer isso, seu aplicativo receberá uma `401: Unauthorized` resposta.</span><span class="sxs-lookup"><span data-stu-id="05d0f-116">If you do not, your app will receive a `401: Unauthorized` response.</span></span> <span data-ttu-id="05d0f-117">Para obter mais informações, consulte [as amostras abaixo](#net-example-from-this-sample).</span><span class="sxs-lookup"><span data-stu-id="05d0f-117">For more information, see [the samples below](#net-example-from-this-sample).</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="05d0f-118">Melhores práticas para mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="05d0f-118">Best practices for proactive messaging</span></span>

<span data-ttu-id="05d0f-119">Enviar mensagens proativas aos usuários pode ser uma maneira muito eficaz de se comunicar com seus usuários.</span><span class="sxs-lookup"><span data-stu-id="05d0f-119">Sending proactive messages to users can be a very effective way to communicate with your users.</span></span> <span data-ttu-id="05d0f-120">No entanto, do ponto de vista deles, essa mensagem pode parecer chegar a eles completamente sem ser provocada, e no caso de mensagens de boas-vindas será a primeira vez que eles interagiram com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="05d0f-120">However, from their perspective this message can appear to come to them completely unprompted, and in the case of welcome messages will be the first time they've interacted with your app.</span></span> <span data-ttu-id="05d0f-121">Como tal, é muito importante usar essa funcionalidade com moderação (não spam seus usuários), e fornecer-lhes informações suficientes para deixá-los entender por que eles estão sendo mensagens.</span><span class="sxs-lookup"><span data-stu-id="05d0f-121">As such, it is very important to use this functionality sparingly (don't spam your users), and to provide them with enough information to let them understand why they are being messaged.</span></span>

<span data-ttu-id="05d0f-122">As mensagens proativas geralmente se enquadram em uma das duas categorias: mensagens de boas-vindas ou notificações.</span><span class="sxs-lookup"><span data-stu-id="05d0f-122">Proactive messages generally fall into one of two categories, welcome messages or notifications.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="05d0f-123">Mensagem de boas-vindas</span><span class="sxs-lookup"><span data-stu-id="05d0f-123">Welcome messages</span></span>

<span data-ttu-id="05d0f-124">Ao usar mensagens proativas para enviar uma mensagem de boas-vindas a um usuário, você deve ter em mente que para a maioria das pessoas que recebem a mensagem eles não terão contexto para o porquê de eles estarem recebendo.</span><span class="sxs-lookup"><span data-stu-id="05d0f-124">When using proactive messaging to send a welcome message to a user you must keep in mind that for most people receiving the message they will have no context for why they are receiving it.</span></span> <span data-ttu-id="05d0f-125">Esta também é a primeira vez que eles terão interagido com o seu aplicativo; é sua oportunidade de criar uma boa primeira impressão.</span><span class="sxs-lookup"><span data-stu-id="05d0f-125">This is also the first time they will have interacted with your app; it is your opportunity to create a good first impression.</span></span> <span data-ttu-id="05d0f-126">As melhores mensagens de boas-vindas incluirão:</span><span class="sxs-lookup"><span data-stu-id="05d0f-126">The best welcome messages will include:</span></span>

* <span data-ttu-id="05d0f-127">**Por que eles estão recebendo esta mensagem.**</span><span class="sxs-lookup"><span data-stu-id="05d0f-127">**Why are they receiving this message.**</span></span> <span data-ttu-id="05d0f-128">Deve ser muito claro para o usuário por que eles estão recebendo a mensagem.</span><span class="sxs-lookup"><span data-stu-id="05d0f-128">It should be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="05d0f-129">Se o seu bot foi instalado em um canal e você enviou uma mensagem de boas-vindas a todos os usuários, avise-os em que canal foi instalado e potencialmente quem o instalou.</span><span class="sxs-lookup"><span data-stu-id="05d0f-129">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and potentially who installed it.</span></span>
* <span data-ttu-id="05d0f-130">**O que você oferece.**</span><span class="sxs-lookup"><span data-stu-id="05d0f-130">**What do you offer.**</span></span> <span data-ttu-id="05d0f-131">O que eles podem fazer com o seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="05d0f-131">What can they do with your app?</span></span> <span data-ttu-id="05d0f-132">Que valor você pode trazer para eles?</span><span class="sxs-lookup"><span data-stu-id="05d0f-132">What value can you bring to them?</span></span>
* <span data-ttu-id="05d0f-133">**O que eles devem fazer a seguir.**</span><span class="sxs-lookup"><span data-stu-id="05d0f-133">**What should they do next.**</span></span> <span data-ttu-id="05d0f-134">Convide-os a experimentar um comando ou interagir com seu aplicativo de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="05d0f-134">Invite them to try out a command, or interact with your app in some way.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="05d0f-135">Mensagens de notificação</span><span class="sxs-lookup"><span data-stu-id="05d0f-135">Notification messages</span></span>

<span data-ttu-id="05d0f-136">Ao usar mensagens proativas para enviar notificações, você precisa garantir que seus usuários tenham um caminho claro para tomar ações comuns com base em sua notificação e uma compreensão clara do porquê da notificação ter ocorrido.</span><span class="sxs-lookup"><span data-stu-id="05d0f-136">When using proactive messaging to send notifications you need to make sure your users have a clear path to take common actions based on your notification, and a clear understanding of why the notification occurred.</span></span> <span data-ttu-id="05d0f-137">Boas mensagens de notificação geralmente incluem:</span><span class="sxs-lookup"><span data-stu-id="05d0f-137">Good notification messages will generally include:</span></span>

* <span data-ttu-id="05d0f-138">**O que aconteceu.**</span><span class="sxs-lookup"><span data-stu-id="05d0f-138">**What happened.**</span></span> <span data-ttu-id="05d0f-139">Uma clara indicação do que aconteceu para causar a notificação.</span><span class="sxs-lookup"><span data-stu-id="05d0f-139">A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="05d0f-140">**O que aconteceu com.**</span><span class="sxs-lookup"><span data-stu-id="05d0f-140">**What it happened to.**</span></span> <span data-ttu-id="05d0f-141">Deve ficar claro qual item/coisa foi atualizado para causar a notificação.</span><span class="sxs-lookup"><span data-stu-id="05d0f-141">It should be clear what item/thing was updated to cause the notification.</span></span>
* <span data-ttu-id="05d0f-142">**Who fiz isso.**</span><span class="sxs-lookup"><span data-stu-id="05d0f-142">**Who did it.**</span></span> <span data-ttu-id="05d0f-143">Who tomou a ação que fez com que a notificação fosse enviada.</span><span class="sxs-lookup"><span data-stu-id="05d0f-143">Who took the action that caused the notification to be sent.</span></span>
* <span data-ttu-id="05d0f-144">**O que eles podem fazer sobre isso.**</span><span class="sxs-lookup"><span data-stu-id="05d0f-144">**What they can do about it.**</span></span> <span data-ttu-id="05d0f-145">Facilite a tomada de ações dos seus usuários com base em suas notificações.</span><span class="sxs-lookup"><span data-stu-id="05d0f-145">Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="05d0f-146">**Como eles podem optar por sair.** Você precisa fornecer um caminho para que os usuários optem por não receber notificações adicionais.</span><span class="sxs-lookup"><span data-stu-id="05d0f-146">**How they can opt out.** You need to provide a path for users to opt out of additional notifications.</span></span>

## <a name="obtain-necessary-user-information"></a><span data-ttu-id="05d0f-147">Obtenha informações necessárias do usuário</span><span class="sxs-lookup"><span data-stu-id="05d0f-147">Obtain necessary user information</span></span>

<span data-ttu-id="05d0f-148">Os bots podem criar novas conversas com um usuário Microsoft Teams individual obtendo o *ID exclusivo* do usuário e o *ID do inquilino.*</span><span class="sxs-lookup"><span data-stu-id="05d0f-148">Bots can create new conversations with an individual Microsoft Teams user by obtaining the user's *unique ID* and *tenant ID.*</span></span> <span data-ttu-id="05d0f-149">Você pode obter esses valores usando um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="05d0f-149">You can obtain these values using one of the following methods:</span></span>

* <span data-ttu-id="05d0f-150">[Ao buscar a lista](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) da equipe a partir de um canal em que seu aplicativo está instalado.</span><span class="sxs-lookup"><span data-stu-id="05d0f-150">By [fetching the team roster](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) from a channel your app is installed in.</span></span>
* <span data-ttu-id="05d0f-151">Ao caching-los quando um usuário [interage com seu bot em um canal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md).</span><span class="sxs-lookup"><span data-stu-id="05d0f-151">By caching them when a user [interacts with your bot in a channel](~/resources/bot-v3/bot-conversations/bots-conv-channel.md).</span></span>
* <span data-ttu-id="05d0f-152">Quando um usuário é @mentioned em uma conversa de [canal,](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) o bot faz parte.</span><span class="sxs-lookup"><span data-stu-id="05d0f-152">When a users is [@mentioned in a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) the bot is a part of.</span></span>
* <span data-ttu-id="05d0f-153">Ao caching-los quando você [recebe o `conversationUpdate` ](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) evento quando seu aplicativo é instalado em um escopo pessoal, ou novos membros são adicionados a um canal ou bate-papo em grupo que.</span><span class="sxs-lookup"><span data-stu-id="05d0f-153">By caching them when you [receive the `conversationUpdate`](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) event when your app is installed in a personal scope, or new members are added to a channel or group chat that.</span></span>

### <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="05d0f-154">Instale proativamente seu aplicativo usando Graph</span><span class="sxs-lookup"><span data-stu-id="05d0f-154">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="05d0f-155">A instalação proativa de aplicativos usando gráficos está atualmente em beta.</span><span class="sxs-lookup"><span data-stu-id="05d0f-155">Proactively installing apps using graph is currently in beta.</span></span>

<span data-ttu-id="05d0f-156">Ocasionalmente, pode ser necessário enviar mensagens proativas aos usuários que não instalaram ou interagiram com seu aplicativo anteriormente.</span><span class="sxs-lookup"><span data-stu-id="05d0f-156">Occasionally it may be necessary to proactively message users that have not installed or interacted with your app previously.</span></span> <span data-ttu-id="05d0f-157">Por exemplo, você deseja usar o [comunicador](~/samples/app-templates.md#company-communicator) da empresa para enviar mensagens para toda a sua organização.</span><span class="sxs-lookup"><span data-stu-id="05d0f-157">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="05d0f-158">Para este cenário, você pode usar a API Graph para instalar proativamente seu aplicativo para seus usuários e, em seguida, em cache os valores necessários do evento que `conversationUpdate` seu aplicativo receberá no momento da instalação.</span><span class="sxs-lookup"><span data-stu-id="05d0f-158">For this scenario you can use the Graph API to proactively install your app for your users, then cache the necessary values from the `conversationUpdate` event your app will receive upon install.</span></span>

<span data-ttu-id="05d0f-159">Você só pode instalar aplicativos que estão no seu catálogo de aplicativos organizacionais ou na loja de aplicativos Teams.</span><span class="sxs-lookup"><span data-stu-id="05d0f-159">You can only install apps that are in your organizational app catalogue, or the Teams app store.</span></span>

<span data-ttu-id="05d0f-160">Consulte [Instalar aplicativos para usuários](/graph/teams-proactive-messaging) na documentação Graph para obter detalhes completos.</span><span class="sxs-lookup"><span data-stu-id="05d0f-160">See [Install apps for users](/graph/teams-proactive-messaging) in the Graph documentation for complete details.</span></span> <span data-ttu-id="05d0f-161">Há também uma [amostra em .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).</span><span class="sxs-lookup"><span data-stu-id="05d0f-161">There is also a [sample in .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).</span></span>

## <a name="examples"></a><span data-ttu-id="05d0f-162">Exemplos</span><span class="sxs-lookup"><span data-stu-id="05d0f-162">Examples</span></span>

<span data-ttu-id="05d0f-163">Certifique-se de autenticar e ter um token portador antes de criar uma nova conversa usando a API REST.</span><span class="sxs-lookup"><span data-stu-id="05d0f-163">Be sure that you authenticate and have a bearer token before creating a new conversation using the REST API.</span></span>

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

<span data-ttu-id="05d0f-164">Você deve fornecer o ID do usuário e o ID do inquilino.</span><span class="sxs-lookup"><span data-stu-id="05d0f-164">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="05d0f-165">Se a chamada for bem sucedida, a API retorna com o seguinte objeto de resposta.</span><span class="sxs-lookup"><span data-stu-id="05d0f-165">If the call succeeds, the API returns with the following response object.</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

<span data-ttu-id="05d0f-166">Esta ID é a id de conversa única do chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="05d0f-166">This ID is the personal chat's unique conversation ID.</span></span> <span data-ttu-id="05d0f-167">Por favor, armazene esse valor e reutilize-o para futuras interações com o usuário.</span><span class="sxs-lookup"><span data-stu-id="05d0f-167">Please store this value and reuse it for future interactions with the user.</span></span>

### <a name="using-net"></a><span data-ttu-id="05d0f-168">Usando .NET</span><span class="sxs-lookup"><span data-stu-id="05d0f-168">Using .NET</span></span>

<span data-ttu-id="05d0f-169">Este exemplo usa o pacote [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet.</span><span class="sxs-lookup"><span data-stu-id="05d0f-169">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

```csharp
// Create or get existing chat conversation with user
var response = client.Conversations.CreateOrGetDirectConversation(activity.Recipient, activity.From, activity.GetTenantId());

// Construct the message to post to conversation
Activity newActivity = new Activity()
{
    Text = "Hello",
    Type = ActivityTypes.Message,
    Conversation = new ConversationAccount
    {
        Id = response.Id
    },
};

// Post the message to chat conversation with user
await client.Conversations.SendToConversationAsync(newActivity, response.Id);
```

### <a name="using-nodejs"></a><span data-ttu-id="05d0f-170">Usando Node.js</span><span class="sxs-lookup"><span data-stu-id="05d0f-170">Using Node.js</span></span>

```javascript
var address =
{
    channelId: 'msteams',
    user: { id: userId },
    channelData: {
        tenant: {
            id: tenantId
        }
    },
    bot:
    {
        id: appId,
        name: appName
    },
    serviceUrl: session.message.address.serviceUrl,
    useAuth: true
}

var msg = new builder.Message().address(address);
msg.text('Hello, this is a notification');
bot.send(msg);
```

## <a name="creating-a-channel-conversation"></a><span data-ttu-id="05d0f-171">Criar uma conversa de canal</span><span class="sxs-lookup"><span data-stu-id="05d0f-171">Creating a channel conversation</span></span>

<span data-ttu-id="05d0f-172">Seu bot adicionado pela equipe pode postar em um canal para criar uma nova cadeia de respostas.</span><span class="sxs-lookup"><span data-stu-id="05d0f-172">Your team-added bot can post into a channel to create a new reply chain.</span></span> <span data-ttu-id="05d0f-173">Se você estiver usando o Node.js Teams SDK, use `startReplyChain()` o que lhe dá um endereço totalmente preenchido com o id de atividade correto e o id de conversação. Se você estiver usando C#, veja o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="05d0f-173">If you're using the Node.js Teams SDK, use `startReplyChain()` which gives you a fully-populated address with the correct activity id and conversation id. If you are using C#, see the example below.</span></span>

<span data-ttu-id="05d0f-174">Alternativamente, você pode usar a API REST e emitir uma solicitação POST para [`/conversations`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) o recurso.</span><span class="sxs-lookup"><span data-stu-id="05d0f-174">Alternatively, you can use the REST API and issue a POST request to [`/conversations`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) resource.</span></span>

### <a name="net-example-from-this-sample"></a><span data-ttu-id="05d0f-175">Exemplo .NET [(desta amostra](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))</span><span class="sxs-lookup"><span data-stu-id="05d0f-175">.NET example (from [this sample](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))</span></span>

```csharp
using Microsoft.Bot.Builder.Dialogs;
using Microsoft.Bot.Connector;
using Microsoft.Bot.Connector.Teams.Models;
using Microsoft.Teams.TemplateBotCSharp.Properties;
using System;
using System.Threading.Tasks;

namespace Microsoft.Teams.TemplateBotCSharp.Dialogs
{
    [Serializable]
    public class ProactiveMsgTo1to1Dialog : IDialog<object>
    {
        public async Task StartAsync(IDialogContext context)
        {
            if (context == null)
            {
                throw new ArgumentNullException(nameof(context));
            }

            var channelData = context.Activity.GetChannelData<TeamsChannelData>();
            var message = Activity.CreateMessageActivity();
            message.Text = "Hello World";

            var conversationParameters = new ConversationParameters
            {
                  IsGroup = true,
                  ChannelData = new TeamsChannelData
                  {
                      Channel = new ChannelInfo(channelData.Channel.Id),
                  },
                  Activity = (Activity) message
            };

            MicrosoftAppCredentials.TrustServiceUrl(serviceUrl, DateTime.MaxValue);
            var connectorClient = new ConnectorClient(new Uri(activity.ServiceUrl));
            var response = await connectorClient.Conversations.CreateConversationAsync(conversationParameters);

            context.Done<object>(null);
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="05d0f-176">Confira também</span><span class="sxs-lookup"><span data-stu-id="05d0f-176">See also</span></span>

[<span data-ttu-id="05d0f-177">Amostras do Bot Framework</span><span class="sxs-lookup"><span data-stu-id="05d0f-177">Bot Framework samples</span></span>](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)