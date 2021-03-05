---
title: Noções básicas sobre conversas
description: descreve maneiras de ter uma conversa com um bot do Microsoft Teams
ms.topic: overview
ms.author: anclear
keyword: conversations basics receive message send message picture message channel data adaptive cards
ms.openlocfilehash: 4eba22e9b29f5378dc03480ba5f6ba421f816eb3
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449504"
---
# <a name="conversation-basics"></a><span data-ttu-id="ed418-103">Noções básicas sobre conversas</span><span class="sxs-lookup"><span data-stu-id="ed418-103">Conversation basics</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="ed418-104">Uma conversa é uma série de mensagens enviadas entre seu bot e um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="ed418-104">A conversation is a series of messages sent between your bot and one or more users.</span></span> <span data-ttu-id="ed418-105">Há três tipos de conversas, também chamados de escopos no Teams:</span><span class="sxs-lookup"><span data-stu-id="ed418-105">There are three types of conversations, also called scopes in Teams:</span></span>

| <span data-ttu-id="ed418-106">Tipo de conversa</span><span class="sxs-lookup"><span data-stu-id="ed418-106">Conversation type</span></span> | <span data-ttu-id="ed418-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed418-107">Description</span></span> |
| ------- | ----------- |
|  `teams` | <span data-ttu-id="ed418-108">Também chamadas de conversas de canal, visíveis para todos os membros do canal.</span><span class="sxs-lookup"><span data-stu-id="ed418-108">Also called channel conversations, visible to all members of the channel.</span></span> |
| `personal` | <span data-ttu-id="ed418-109">Conversas entre bots e um único usuário.</span><span class="sxs-lookup"><span data-stu-id="ed418-109">Conversations between bots and a single user.</span></span> |
| `groupChat` | <span data-ttu-id="ed418-110">Chat entre um bot e dois ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="ed418-110">Chat between a bot and two or more users.</span></span> <span data-ttu-id="ed418-111">Também habilita seu bot em chats de reunião.</span><span class="sxs-lookup"><span data-stu-id="ed418-111">Also enables your bot in meeting chats.</span></span> |

<span data-ttu-id="ed418-112">Um bot se comporta um pouco diferente dependendo do tipo de conversa em que ele está envolvido:</span><span class="sxs-lookup"><span data-stu-id="ed418-112">A bot behaves slightly differently depending on what kind of conversation it is involved in:</span></span>

* <span data-ttu-id="ed418-113">Bots em conversas de chat de canal e grupo exigem que o usuário @ mencione o bot para invocá-lo em um canal.</span><span class="sxs-lookup"><span data-stu-id="ed418-113">Bots in channel and group chat conversations require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="ed418-114">Bots em uma conversa um para um não exigem uma menção @.</span><span class="sxs-lookup"><span data-stu-id="ed418-114">Bots in a one-to-one conversation do not require an @ mention.</span></span> <span data-ttu-id="ed418-115">Todas as mensagens enviadas pelo usuário são encaminhadas para seu bot.</span><span class="sxs-lookup"><span data-stu-id="ed418-115">All messages sent by the user routes to your bot.</span></span>

<span data-ttu-id="ed418-116">Para habilitar seu bot em um escopo específico, adicione esse escopo ao manifesto [do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="ed418-116">To enable your bot in a particular scope, add that scope to your [app manifest](~/resources/schema/manifest-schema.md).</span></span>

## <a name="activities"></a><span data-ttu-id="ed418-117">Atividades</span><span class="sxs-lookup"><span data-stu-id="ed418-117">Activities</span></span>

<span data-ttu-id="ed418-118">Cada mensagem é um `Activity` objeto do tipo `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="ed418-118">Each message is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="ed418-119">Quando um usuário envia uma mensagem, o Teams posta a mensagem em seu bot; especificamente, ele envia um objeto JSON para o ponto de extremidade de mensagens do bot.</span><span class="sxs-lookup"><span data-stu-id="ed418-119">When a user sends a message, Teams posts the message to your bot; specifically, it sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="ed418-120">Seu bot examina a mensagem para determinar seu tipo e responde de acordo.</span><span class="sxs-lookup"><span data-stu-id="ed418-120">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="ed418-121">As conversas básicas são manipuladas por meio do Bot Framework Connector, uma única API REST.</span><span class="sxs-lookup"><span data-stu-id="ed418-121">Basic conversations are handled through the Bot Framework Connector, a single REST API.</span></span> <span data-ttu-id="ed418-122">Essa API permite que seu bot se comunique com o Teams e outros canais.</span><span class="sxs-lookup"><span data-stu-id="ed418-122">This API enables your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="ed418-123">O SDK do Construtor de Bots fornece fácil acesso a essa API, funcionalidade adicional para gerenciar o fluxo e o estado da conversa e maneiras simples de incorporar serviços cognitivos, como o Processamento de Linguagem Natural (NLP).</span><span class="sxs-lookup"><span data-stu-id="ed418-123">The Bot Builder SDK provides easy access to this API, additional functionality to manage conversation flow and state, and simple ways to incorporate cognitive services such as Natural Language Processing (NLP).</span></span>

## <a name="receive-a-message"></a><span data-ttu-id="ed418-124">Receber uma mensagem</span><span class="sxs-lookup"><span data-stu-id="ed418-124">Receive a message</span></span>

<span data-ttu-id="ed418-125">Para receber uma mensagem de texto, use `Text` a propriedade do `Activity` objeto.</span><span class="sxs-lookup"><span data-stu-id="ed418-125">To receive a text message, use the `Text` property of the `Activity` object.</span></span> <span data-ttu-id="ed418-126">No manipulador de atividades do bot, use o objeto turn context's `Activity` para ler uma única solicitação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="ed418-126">In the bot's activity handler, use the turn context object's `Activity` to read a single message request.</span></span>

<span data-ttu-id="ed418-127">O código a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="ed418-127">The following code shows an example.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ed418-128">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ed418-128">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ed418-129">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ed418-129">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            await context.sendActivity(`Echo: '${context.activity.text}'`);
            await next();
        });
    }
}

```

# <a name="python"></a>[<span data-ttu-id="ed418-130">Python</span><span class="sxs-lookup"><span data-stu-id="ed418-130">Python</span></span>](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="json"></a>[<span data-ttu-id="ed418-131">JSON</span><span class="sxs-lookup"><span data-stu-id="ed418-131">JSON</span></span>](#tab/json)

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

---

## <a name="send-a-message"></a><span data-ttu-id="ed418-132">Enviar uma mensagem</span><span class="sxs-lookup"><span data-stu-id="ed418-132">Send a message</span></span>

<span data-ttu-id="ed418-133">Para enviar uma mensagem de texto, especifique a cadeia de caracteres que você deseja enviar como a atividade.</span><span class="sxs-lookup"><span data-stu-id="ed418-133">To send a text message, specify the string you want to send as the activity.</span></span> <span data-ttu-id="ed418-134">No manipulador de atividades do bot, use o método do objeto turn context `SendActivityAsync` para enviar uma única resposta de mensagem.</span><span class="sxs-lookup"><span data-stu-id="ed418-134">In the bot's activity handler, use the turn context object's `SendActivityAsync` method to send a single message response.</span></span> <span data-ttu-id="ed418-135">Use o método do `SendActivitiesAsync` objeto para enviar várias respostas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="ed418-135">Use the object's `SendActivitiesAsync` method to send multiple responses at once.</span></span> <span data-ttu-id="ed418-136">O código a seguir mostra um exemplo de envio de uma mensagem quando alguém é adicionado a uma conversa.</span><span class="sxs-lookup"><span data-stu-id="ed418-136">The following code shows an example of sending a message when someone is added to a conversation.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ed418-137">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ed418-137">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ed418-138">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ed418-138">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            await context.sendActivity('Hello and welcome!');
            await next();
        });
    }
}
```

# <a name="python"></a>[<span data-ttu-id="ed418-139">Python</span><span class="sxs-lookup"><span data-stu-id="ed418-139">Python</span></span>](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="json"></a>[<span data-ttu-id="ed418-140">JSON</span><span class="sxs-lookup"><span data-stu-id="ed418-140">JSON</span></span>](#tab/json)

```json
{
    "text": "hi",
    "textFormat": "plain",
    "type": "message",
    "timestamp": "2019-10-31T20:57:27.2347285Z",
    "localTimestamp": "2019-10-31T13:57:27.2347285-07:00",
    "id": "1572555447214",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "from": {
        "id": "29:1Xv-kvy4dKirR0rZfSF_kAVUzotoT1SXuEzkC9XGkuZng8YBw8qyu5uh4128fQRjlGgvEiRLx-0XP4KYMwcgdZw",
        "name": "Jane Doe",
        "aadObjectId": "df486eae-88fd-42a5-b45e-c581588186db"
    },
    "conversation": {
        "conversationType": "personal",
        "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
        "id": "a:1oAmWTVBBe9E0JrpGxauqNyx4CCE_iQf2ZuWon9D42722Fon3wYIpbhgbRChE3wgVS1Gwl9zS1pZy4FSu6-x1vGEq5KBQK-EbBgyPyeP_C-lbLBY3vxnGk9m9D_282jbg"
    },
    "recipient": {
        "id": "28:5baea8d1-d4ea-43a1-b101-882f4c8d9cb4",
        "name": "Imported Bot"
    },
    "entities": [
        {
            "locale": "en-US",
            "country": "US",
            "platform": "Windows",
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

---

> [!NOTE]
> <span data-ttu-id="ed418-141">A divisão de mensagens ocorre quando uma mensagem de texto e um anexo são enviados na mesma carga de atividade.</span><span class="sxs-lookup"><span data-stu-id="ed418-141">Message splitting occurs when a text message and an attachment are sent in the same activity payload.</span></span> <span data-ttu-id="ed418-142">Essa atividade é dividida em atividades separadas pelo Microsoft Teams, uma atividade com apenas uma mensagem de texto e outra com um anexo.</span><span class="sxs-lookup"><span data-stu-id="ed418-142">This activity is split into separate activities by Microsoft Teams, one activity with just a text message and the other with an attachment.</span></span> <span data-ttu-id="ed418-143">À medida que a atividade é dividida, você não recebe a ID da mensagem em resposta, que é usada para atualizar [ou excluir](~/bots/how-to/update-and-delete-bot-messages.md) a mensagem proativamente.</span><span class="sxs-lookup"><span data-stu-id="ed418-143">As the activity is split, you do not receive the message ID in response, which is used to [update or delete](~/bots/how-to/update-and-delete-bot-messages.md) the message proactively.</span></span> <span data-ttu-id="ed418-144">É recomendável enviar atividades separadas em vez de depender da divisão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ed418-144">It is recommended to send separate activities instead of depending on message splitting.</span></span>

## <a name="teams-channel-data"></a><span data-ttu-id="ed418-145">Dados do canal do Teams</span><span class="sxs-lookup"><span data-stu-id="ed418-145">Teams channel data</span></span>

<span data-ttu-id="ed418-146">O `channelData` objeto contém informações específicas do Teams e é uma fonte definitiva para IDs de equipe e canal.</span><span class="sxs-lookup"><span data-stu-id="ed418-146">The `channelData` object contains Teams-specific information and is a definitive source for team and channel IDs.</span></span> <span data-ttu-id="ed418-147">Talvez seja necessário armazenar em cache e usar essas IDs como chaves para armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="ed418-147">You may need to cache and use these IDs as keys for local storage.</span></span> <span data-ttu-id="ed418-148">O no SDK normalmente retira informações importantes do objeto para `TeamsActivityHandler` `channelData` torná-lo facilmente acessível.</span><span class="sxs-lookup"><span data-stu-id="ed418-148">The `TeamsActivityHandler` in the SDK, typically pulls out important information from the `channelData` object to make it easily accessible.</span></span> <span data-ttu-id="ed418-149">No entanto, você sempre pode acessar os dados originais do `turnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="ed418-149">However, you can always access the original data from the `turnContext` object.</span></span>

<span data-ttu-id="ed418-150">O `channelData` objeto não está incluído em mensagens em conversas pessoais, pois elas ocorrem fora de qualquer canal.</span><span class="sxs-lookup"><span data-stu-id="ed418-150">The `channelData` object is not included in messages in personal conversations, as these take place outside of any channel.</span></span>

<span data-ttu-id="ed418-151">Um objeto channelData típico em uma atividade enviada ao bot contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="ed418-151">A typical channelData object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="ed418-152">`eventType` Tipo de evento do Teams; passada somente em casos de eventos [de modificação de canal](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="ed418-152">`eventType` Teams event type; passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="ed418-153">`tenant.id` ID do locatário do Azure Active Directory, passada em todos os contextos.</span><span class="sxs-lookup"><span data-stu-id="ed418-153">`tenant.id` Azure Active Directory tenant ID, passed in all contexts.</span></span>
* <span data-ttu-id="ed418-154">`team` Passado somente em contextos de canal, não em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="ed418-154">`team` Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="ed418-155">`id` GUID para o canal.</span><span class="sxs-lookup"><span data-stu-id="ed418-155">`id` GUID for the channel.</span></span>
  * <span data-ttu-id="ed418-156">`name`Nome da equipe; passada somente em casos de [eventos de renomear equipe.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="ed418-156">`name` Name of the team; passed only in cases of [team rename events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="ed418-157">`channel` Passado somente em contextos de canal quando o bot é mencionado ou para eventos em canais em equipes onde o bot foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="ed418-157">`channel` Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added.</span></span>
  * <span data-ttu-id="ed418-158">`id` GUID para o canal.</span><span class="sxs-lookup"><span data-stu-id="ed418-158">`id` GUID for the channel.</span></span>
  * <span data-ttu-id="ed418-159">`name` Nome do canal; passada somente em casos de eventos [de modificação de canal](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="ed418-159">`name` Channel name; passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="ed418-160">`channelData.teamsTeamId` Preterido.</span><span class="sxs-lookup"><span data-stu-id="ed418-160">`channelData.teamsTeamId` Deprecated.</span></span> <span data-ttu-id="ed418-161">Essa propriedade é incluída apenas para compatibilidade com compatibilidade com compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="ed418-161">This property is included only for backwards compatibility.</span></span>
* <span data-ttu-id="ed418-162">`channelData.teamsChannelId` Preterido.</span><span class="sxs-lookup"><span data-stu-id="ed418-162">`channelData.teamsChannelId` Deprecated.</span></span> <span data-ttu-id="ed418-163">Essa propriedade é incluída apenas para compatibilidade com compatibilidade com compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="ed418-163">This property is included only for backwards compatibility.</span></span>

### <a name="example-channeldata-object-channelcreated-event"></a><span data-ttu-id="ed418-164">Objeto channelData de exemplo (evento channelCreated)</span><span class="sxs-lookup"><span data-stu-id="ed418-164">Example channelData object (channelCreated event)</span></span>

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

## <a name="message-content"></a><span data-ttu-id="ed418-165">Conteúdo da mensagem</span><span class="sxs-lookup"><span data-stu-id="ed418-165">Message content</span></span>

<span data-ttu-id="ed418-166">Seu bot pode enviar rich text, pictures e cards.</span><span class="sxs-lookup"><span data-stu-id="ed418-166">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="ed418-167">Os usuários podem enviar texto e imagens rich para seu bot.</span><span class="sxs-lookup"><span data-stu-id="ed418-167">Users can send rich text and pictures to your bot.</span></span>

| <span data-ttu-id="ed418-168">Formatar</span><span class="sxs-lookup"><span data-stu-id="ed418-168">Format</span></span>    | <span data-ttu-id="ed418-169">De usuário para bot</span><span class="sxs-lookup"><span data-stu-id="ed418-169">From user to bot</span></span> | <span data-ttu-id="ed418-170">De bot para usuário</span><span class="sxs-lookup"><span data-stu-id="ed418-170">From bot to user</span></span> | <span data-ttu-id="ed418-171">Observações</span><span class="sxs-lookup"><span data-stu-id="ed418-171">Notes</span></span>                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| <span data-ttu-id="ed418-172">Rich text </span><span class="sxs-lookup"><span data-stu-id="ed418-172">Rich text</span></span> | <span data-ttu-id="ed418-173">✔</span><span class="sxs-lookup"><span data-stu-id="ed418-173">✔</span></span>                | <span data-ttu-id="ed418-174">✔</span><span class="sxs-lookup"><span data-stu-id="ed418-174">✔</span></span>                |                                                                                         |
| <span data-ttu-id="ed418-175">Imagens</span><span class="sxs-lookup"><span data-stu-id="ed418-175">Pictures</span></span>  | <span data-ttu-id="ed418-176">✔</span><span class="sxs-lookup"><span data-stu-id="ed418-176">✔</span></span>                | <span data-ttu-id="ed418-177">✔</span><span class="sxs-lookup"><span data-stu-id="ed418-177">✔</span></span>                | <span data-ttu-id="ed418-178">Máximo de 1024×1024 e 1 MB no formato PNG, JPEG ou GIF; GIF animado não são suportados</span><span class="sxs-lookup"><span data-stu-id="ed418-178">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF are not supported</span></span>  |
| <span data-ttu-id="ed418-179">Cartões</span><span class="sxs-lookup"><span data-stu-id="ed418-179">Cards</span></span>     | <span data-ttu-id="ed418-180">✖</span><span class="sxs-lookup"><span data-stu-id="ed418-180">✖</span></span>                | <span data-ttu-id="ed418-181">✔</span><span class="sxs-lookup"><span data-stu-id="ed418-181">✔</span></span>                | <span data-ttu-id="ed418-182">Consulte a [Referência de Cartão do Teams](~/task-modules-and-cards/cards/cards-reference.md) para cartões com suporte</span><span class="sxs-lookup"><span data-stu-id="ed418-182">See the [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards</span></span> |
| <span data-ttu-id="ed418-183">Emojis</span><span class="sxs-lookup"><span data-stu-id="ed418-183">Emojis</span></span>    | <span data-ttu-id="ed418-184">✖</span><span class="sxs-lookup"><span data-stu-id="ed418-184">✖</span></span>                | <span data-ttu-id="ed418-185">✔</span><span class="sxs-lookup"><span data-stu-id="ed418-185">✔</span></span>                | <span data-ttu-id="ed418-186">No momento, o Teams dá suporte a emojis por meio do UTF-16 (como U+1F600 para rosto de curtição)</span><span class="sxs-lookup"><span data-stu-id="ed418-186">Teams currently supports emojis through UTF-16 (such as U+1F600 for grinning face)</span></span>          |

## <a name="adding-notifications-to-your-message"></a><span data-ttu-id="ed418-187">Adicionando notificações à sua mensagem</span><span class="sxs-lookup"><span data-stu-id="ed418-187">Adding notifications to your message</span></span>

<span data-ttu-id="ed418-188">As notificações alertam os usuários sobre novas tarefas, menções e comentários relacionados ao que estão trabalhando ou precisam observar inserindo um aviso no feed de atividades.</span><span class="sxs-lookup"><span data-stu-id="ed418-188">Notifications alert users about new tasks, mentions, and comments related to what they are working on or need to look at by inserting a notice into their activity feed.</span></span> <span data-ttu-id="ed418-189">Você pode definir notificações para disparar de sua mensagem bot definindo a `TeamsChannelData` propriedade `Notification.Alert` objects como true.</span><span class="sxs-lookup"><span data-stu-id="ed418-189">You can set notifications to trigger from your bot-message by setting the `TeamsChannelData` objects `Notification.Alert` property to true.</span></span> <span data-ttu-id="ed418-190">A ativação ou não de uma notificação depende das configurações do Teams do usuário individual e você não pode substituir programaticamente essas configurações.</span><span class="sxs-lookup"><span data-stu-id="ed418-190">Whether or not a notification is raised ultimately depends on the individual user's Teams settings and you cannot programmatically override these settings.</span></span> <span data-ttu-id="ed418-191">O tipo de notificação é um banner ou um banner e um email.</span><span class="sxs-lookup"><span data-stu-id="ed418-191">The type of notification is either a banner or both a banner and an email.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ed418-192">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ed418-192">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ed418-193">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ed418-193">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="python"></a>[<span data-ttu-id="ed418-194">Python</span><span class="sxs-lookup"><span data-stu-id="ed418-194">Python</span></span>](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="json"></a>[<span data-ttu-id="ed418-195">JSON</span><span class="sxs-lookup"><span data-stu-id="ed418-195">JSON</span></span>](#tab/json)

```json
{
  "type": "message",
  "timestamp": "2017-04-24T21:46:00.9663655Z",
  "localTimestamp": "2017-04-24T14:46:00.9663655-07:00",
  "serviceUrl": "https://callback.com",
  "channelId": "msteams",
  "from": {
    "id": "28:e4fda94a-4b80-40eb-9bf0-6314491bc793",
    "name": "The bot"
  },
  "conversation": {
    "id": "a:1pL6i0oY3C0K8oAj8"
  },
  "recipient": {
    "id": "29:1rsVJmSSFMScF0YFyCXpvNWlo",
    "name": "User"
  },
  "text": "John Phillips assigned you a weekly todo",
  "summary": "Don't forget to meet with Marketing next week",
  "channelData": {
    "notification": {
      "alert": true
    }
  },
  "replyToId": "1493070356924"
}
```

---

## <a name="picture-messages"></a><span data-ttu-id="ed418-196">Mensagens de imagem</span><span class="sxs-lookup"><span data-stu-id="ed418-196">Picture messages</span></span>

<span data-ttu-id="ed418-197">As imagens são enviadas adicionando anexos a uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="ed418-197">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="ed418-198">Você pode encontrar mais informações sobre anexos na documentação [da Estrutura de Bots.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments)</span><span class="sxs-lookup"><span data-stu-id="ed418-198">You can find more information on attachments in the [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).</span></span>

<span data-ttu-id="ed418-199">As imagens podem ter no máximo 1024×1024 e 1 MB no formato PNG, JPEG ou GIF.</span><span class="sxs-lookup"><span data-stu-id="ed418-199">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="ed418-200">Gif animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="ed418-200">Animated GIF is not supported.</span></span>

<span data-ttu-id="ed418-201">Sempre especifique a altura e a largura de cada imagem usando XML.</span><span class="sxs-lookup"><span data-stu-id="ed418-201">Always specify the height and width of each image by using XML.</span></span> <span data-ttu-id="ed418-202">Em Markdown, o tamanho da imagem é padrão para 256×256.</span><span class="sxs-lookup"><span data-stu-id="ed418-202">In Markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="ed418-203">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ed418-203">For example:</span></span>

* <span data-ttu-id="ed418-204">Usar - `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span><span class="sxs-lookup"><span data-stu-id="ed418-204">Use - `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span></span>
* <span data-ttu-id="ed418-205">Não use - `![Duck on a rock](http://aka.ms/Fo983c)`</span><span class="sxs-lookup"><span data-stu-id="ed418-205">Don't use - `![Duck on a rock](http://aka.ms/Fo983c)`</span></span>

## <a name="adaptive-cards"></a><span data-ttu-id="ed418-206">Cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="ed418-206">Adaptive cards</span></span>

<span data-ttu-id="ed418-207">Use o seguinte código para enviar um cartão adaptável simples:</span><span class="sxs-lookup"><span data-stu-id="ed418-207">Use the following code to send a simple adaptive card:</span></span>

```json
{
    "type": "AdaptiveCard",
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.5",
    "body": [
    {
        "items": [
        {
            "size": "large",
            "text": " Simple Adaptivecard Example with a Textbox",
            "type": "TextBlock",
            "weight": "bolder",
            "wrap": true
        },
        ],
        "spacing": "extraLarge",
        "type": "Container",
        "verticalContentAlignment": "center"
    }
    ]
}
```

<span data-ttu-id="ed418-208">Para saber mais sobre cartões e cartões em bots, consulte [documentação de cartões.](~/task-modules-and-cards/what-are-cards.md)</span><span class="sxs-lookup"><span data-stu-id="ed418-208">To know more about cards and cards in bots, see [cards documentation](~/task-modules-and-cards/what-are-cards.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="ed418-209">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="ed418-209">Code sample</span></span>

|<span data-ttu-id="ed418-210">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="ed418-210">**Sample name**</span></span> | <span data-ttu-id="ed418-211">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ed418-211">**Description**</span></span> | <span data-ttu-id="ed418-212">**. NETCore**</span><span class="sxs-lookup"><span data-stu-id="ed418-212">**.NETCore**</span></span> | <span data-ttu-id="ed418-213">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="ed418-213">**JavaScript**</span></span> | <span data-ttu-id="ed418-214">**Python**</span><span class="sxs-lookup"><span data-stu-id="ed418-214">**Python**</span></span>|
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="ed418-215">Bot de Conversa do Teams</span><span class="sxs-lookup"><span data-stu-id="ed418-215">Teams Conversation Bot</span></span> | <span data-ttu-id="ed418-216">Manipulação de eventos de mensagens e conversas.</span><span class="sxs-lookup"><span data-stu-id="ed418-216">Messaging and conversation event handling.</span></span> |[<span data-ttu-id="ed418-217">View</span><span class="sxs-lookup"><span data-stu-id="ed418-217">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="ed418-218">View</span><span class="sxs-lookup"><span data-stu-id="ed418-218">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [<span data-ttu-id="ed418-219">View</span><span class="sxs-lookup"><span data-stu-id="ed418-219">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-steps"></a><span data-ttu-id="ed418-220">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ed418-220">Next steps</span></span>

* [<span data-ttu-id="ed418-221">Enviando mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="ed418-221">Sending proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
* [<span data-ttu-id="ed418-222">Inscreva-se em eventos de conversa</span><span class="sxs-lookup"><span data-stu-id="ed418-222">Subscribe to conversation events</span></span>](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
