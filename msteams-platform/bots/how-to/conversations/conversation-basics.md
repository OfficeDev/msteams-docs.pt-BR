---
title: Noções básicas sobre conversas
description: descreve maneiras de ter uma conversa com um bot do Microsoft Teams
ms.topic: overview
ms.author: anclear
keyword: conversations basics receive message send message picture message channel data adaptive cards
ms.openlocfilehash: 3cf11b5b96a1504ddb3fb8c9fc5814c5131d072f
ms.sourcegitcommit: e78c9f51c4538212c53bb6c6a45a09d994896f09
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2021
ms.locfileid: "51585852"
---
# <a name="conversation-basics"></a><span data-ttu-id="5810a-103">Noções básicas sobre conversas</span><span class="sxs-lookup"><span data-stu-id="5810a-103">Conversation basics</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="5810a-104">Uma conversa é uma série de mensagens enviadas entre o bot do Microsoft Teams e um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="5810a-104">A conversation is a series of messages sent between your Microsoft Teams bot and one or more users.</span></span> <span data-ttu-id="5810a-105">Há três tipos de conversas, também chamados de escopos no Teams:</span><span class="sxs-lookup"><span data-stu-id="5810a-105">There are three types of conversations, also called scopes in Teams:</span></span>

| <span data-ttu-id="5810a-106">Tipo de conversa</span><span class="sxs-lookup"><span data-stu-id="5810a-106">Conversation type</span></span> | <span data-ttu-id="5810a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5810a-107">Description</span></span> |
| ------- | ----------- |
| `channel` | <span data-ttu-id="5810a-108">Esse tipo de conversa é visível para todos os membros do canal.</span><span class="sxs-lookup"><span data-stu-id="5810a-108">This conversation type is visible to all members of the channel.</span></span> |
| `personal` | <span data-ttu-id="5810a-109">Esse tipo de conversa inclui conversas entre bots e um único usuário.</span><span class="sxs-lookup"><span data-stu-id="5810a-109">This conversation type includes conversations between bots and a single user.</span></span> |
| `groupChat` | <span data-ttu-id="5810a-110">Esse tipo de conversa inclui chat entre um bot e dois ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="5810a-110">This conversation type includes chat between a bot and two or more users.</span></span> <span data-ttu-id="5810a-111">Ele também habilita seu bot em chats de reunião.</span><span class="sxs-lookup"><span data-stu-id="5810a-111">It also enables your bot in meeting chats.</span></span> |

<span data-ttu-id="5810a-112">Um bot se comporta de forma diferente, dependendo da conversa em que ele está envolvido:</span><span class="sxs-lookup"><span data-stu-id="5810a-112">A bot behaves differently depending on the conversation it is involved in:</span></span>

* <span data-ttu-id="5810a-113">Bots em conversas de chat de canal e grupo exigem que o usuário @ mencione o bot para invocá-lo em um canal.</span><span class="sxs-lookup"><span data-stu-id="5810a-113">Bots in channel and group chat conversations require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="5810a-114">Bots em uma conversa um para um não exigem uma menção @.</span><span class="sxs-lookup"><span data-stu-id="5810a-114">Bots in a one-to-one conversation do not require an @ mention.</span></span> <span data-ttu-id="5810a-115">Todas as mensagens enviadas pelo usuário são encaminhadas para seu bot.</span><span class="sxs-lookup"><span data-stu-id="5810a-115">All messages sent by the user routes to your bot.</span></span>

<span data-ttu-id="5810a-116">Para que o bot funcione em uma determinada conversa ou escopo, adicione suporte a esse escopo no manifesto [do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="5810a-116">For the bot to work in a particular conversation or scope, add support to that scope in the [app manifest](~/resources/schema/manifest-schema.md).</span></span>

## <a name="messages-in-bot-conversations"></a><span data-ttu-id="5810a-117">Mensagens em conversas de bot</span><span class="sxs-lookup"><span data-stu-id="5810a-117">Messages in bot conversations</span></span>

<span data-ttu-id="5810a-118">Cada mensagem em uma conversa é um `Activity` objeto do tipo `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="5810a-118">Each message in a conversation is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="5810a-119">Quando um usuário envia uma mensagem, o Teams posta a mensagem no bot.</span><span class="sxs-lookup"><span data-stu-id="5810a-119">When a user sends a message, Teams posts the message to your bot.</span></span> <span data-ttu-id="5810a-120">O Teams envia um objeto JSON para o ponto de extremidade de mensagens do bot.</span><span class="sxs-lookup"><span data-stu-id="5810a-120">Teams sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="5810a-121">Seu bot examina a mensagem para determinar seu tipo e responde de acordo.</span><span class="sxs-lookup"><span data-stu-id="5810a-121">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="5810a-122">As conversas básicas são manipuladas por meio do conector da Estrutura do Bot, uma única API REST.</span><span class="sxs-lookup"><span data-stu-id="5810a-122">Basic conversations are handled through the Bot Framework connector, a single REST API.</span></span> <span data-ttu-id="5810a-123">Essa API permite que seu bot se comunique com o Teams e outros canais.</span><span class="sxs-lookup"><span data-stu-id="5810a-123">This API enables your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="5810a-124">O SDK do Construtor de Bots fornece o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5810a-124">The Bot Builder SDK provides the following:</span></span>

* <span data-ttu-id="5810a-125">Acesso fácil ao conector da Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="5810a-125">Easy access to the Bot Framework connector.</span></span>
* <span data-ttu-id="5810a-126">Funcionalidade adicional para gerenciar o fluxo e o estado da conversa.</span><span class="sxs-lookup"><span data-stu-id="5810a-126">Additional functionality to manage conversation flow and state.</span></span>
* <span data-ttu-id="5810a-127">Maneiras simples de incorporar serviços cognitivos, como o Processamento de Linguagem Natural (NLP).</span><span class="sxs-lookup"><span data-stu-id="5810a-127">Simple ways to incorporate cognitive services such as Natural Language Processing (NLP).</span></span>

<span data-ttu-id="5810a-128">Seu bot recebe mensagens do Teams usando a propriedade e envia respostas de mensagem única ou `Text` múltipla aos usuários.</span><span class="sxs-lookup"><span data-stu-id="5810a-128">Your bot receives messages from Teams using the `Text` property and it sends single or multiple message responses to the users.</span></span>

## <a name="receive-a-message"></a><span data-ttu-id="5810a-129">Receber uma mensagem</span><span class="sxs-lookup"><span data-stu-id="5810a-129">Receive a message</span></span>

<span data-ttu-id="5810a-130">Para receber uma mensagem de texto, use a propriedade `Text` do objeto `Activity`.</span><span class="sxs-lookup"><span data-stu-id="5810a-130">To receive a text message, use the `Text` property of the `Activity` object.</span></span> <span data-ttu-id="5810a-131">No manipulador de atividades do bot, alterne o contexto do objeto `Activity` para ler uma única solicitação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5810a-131">In the bot's activity handler, use the turn context object's `Activity` to read a single message request.</span></span>

<span data-ttu-id="5810a-132">O código a seguir mostra um exemplo de recebimento de uma mensagem:</span><span class="sxs-lookup"><span data-stu-id="5810a-132">The following code shows an example of receiving a message:</span></span>

# <a name="c"></a>[<span data-ttu-id="5810a-133">C#</span><span class="sxs-lookup"><span data-stu-id="5810a-133">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescript"></a>[<span data-ttu-id="5810a-134">TypeScript</span><span class="sxs-lookup"><span data-stu-id="5810a-134">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="5810a-135">Python</span><span class="sxs-lookup"><span data-stu-id="5810a-135">Python</span></span>](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="json"></a>[<span data-ttu-id="5810a-136">JSON</span><span class="sxs-lookup"><span data-stu-id="5810a-136">JSON</span></span>](#tab/json)

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

## <a name="send-a-message"></a><span data-ttu-id="5810a-137">Enviar uma mensagem</span><span class="sxs-lookup"><span data-stu-id="5810a-137">Send a message</span></span>

<span data-ttu-id="5810a-138">Para enviar uma mensagem de texto, especifique a cadeia de caracteres que você deseja enviar como a atividade.</span><span class="sxs-lookup"><span data-stu-id="5810a-138">To send a text message, specify the string you want to send as the activity.</span></span> <span data-ttu-id="5810a-139">No manipulador de atividades do bot, use o método do objeto turn context `SendActivityAsync` para enviar uma única resposta de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5810a-139">In the bot's activity handler, use the turn context object's `SendActivityAsync` method to send a single message response.</span></span> <span data-ttu-id="5810a-140">Use o método do `SendActivitiesAsync` objeto para enviar várias respostas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="5810a-140">Use the object's `SendActivitiesAsync` method to send multiple responses at once.</span></span> <span data-ttu-id="5810a-141">O código a seguir mostra um exemplo de envio de uma mensagem quando um usuário é adicionado a uma conversa:</span><span class="sxs-lookup"><span data-stu-id="5810a-141">The following code shows an example of sending a message when a user is added to a conversation:</span></span>

<span data-ttu-id="5810a-142">O código a seguir mostra um exemplo de envio de uma mensagem:</span><span class="sxs-lookup"><span data-stu-id="5810a-142">The following code shows an example of sending a message:</span></span>

# <a name="c"></a>[<span data-ttu-id="5810a-143">C#</span><span class="sxs-lookup"><span data-stu-id="5810a-143">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescript"></a>[<span data-ttu-id="5810a-144">TypeScript</span><span class="sxs-lookup"><span data-stu-id="5810a-144">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="5810a-145">Python</span><span class="sxs-lookup"><span data-stu-id="5810a-145">Python</span></span>](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="json"></a>[<span data-ttu-id="5810a-146">JSON</span><span class="sxs-lookup"><span data-stu-id="5810a-146">JSON</span></span>](#tab/json)

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
> <span data-ttu-id="5810a-147">A divisão de mensagens ocorre quando uma mensagem de texto e um anexo são enviados na mesma carga de atividade.</span><span class="sxs-lookup"><span data-stu-id="5810a-147">Message splitting occurs when a text message and an attachment are sent in the same activity payload.</span></span> <span data-ttu-id="5810a-148">Essa atividade é dividida em atividades separadas pelo Microsoft Teams, uma com apenas uma mensagem de texto e outra com um anexo.</span><span class="sxs-lookup"><span data-stu-id="5810a-148">This activity is split into separate activities by Microsoft Teams, one with just a text message and the other with an attachment.</span></span> <span data-ttu-id="5810a-149">À medida que a atividade é dividida, você não recebe a ID da mensagem em resposta, que é usada para atualizar [ou excluir](~/bots/how-to/update-and-delete-bot-messages.md) a mensagem proativamente.</span><span class="sxs-lookup"><span data-stu-id="5810a-149">As the activity is split, you do not receive the message ID in response, which is used to [update or delete](~/bots/how-to/update-and-delete-bot-messages.md) the message proactively.</span></span> <span data-ttu-id="5810a-150">É recomendável enviar atividades separadas em vez de depender da divisão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5810a-150">It is recommended to send separate activities instead of depending on message splitting.</span></span>

<span data-ttu-id="5810a-151">As mensagens enviadas entre usuários e bots incluem dados de canal interno dentro da mensagem.</span><span class="sxs-lookup"><span data-stu-id="5810a-151">Messages sent between users and bots include internal channel data within the message.</span></span> <span data-ttu-id="5810a-152">Esses dados permitem que o bot se comunique corretamente nesse canal.</span><span class="sxs-lookup"><span data-stu-id="5810a-152">This data allows the bot to communicate properly on that channel.</span></span> <span data-ttu-id="5810a-153">O SDK do Construtor de Bots permite modificar a estrutura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5810a-153">The Bot Builder SDK allows you to modify the message structure.</span></span>

## <a name="teams-channel-data"></a><span data-ttu-id="5810a-154">Dados do canal do Teams</span><span class="sxs-lookup"><span data-stu-id="5810a-154">Teams channel data</span></span>

<span data-ttu-id="5810a-155">O `channelData` objeto contém informações específicas do Teams e é uma fonte definitiva para IDs de equipe e canal.</span><span class="sxs-lookup"><span data-stu-id="5810a-155">The `channelData` object contains Teams-specific information and is a definitive source for team and channel IDs.</span></span> <span data-ttu-id="5810a-156">Opcionalmente, você pode armazenar em cache e usar essas IDs como chaves para armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="5810a-156">Optionally, you can cache and use these IDs as keys for local storage.</span></span> <span data-ttu-id="5810a-157">O no SDK normalmente retira informações importantes do objeto para `TeamsActivityHandler` `channelData` torná-lo facilmente acessível.</span><span class="sxs-lookup"><span data-stu-id="5810a-157">The `TeamsActivityHandler` in the SDK typically pulls out important information from the `channelData` object to make it easily accessible.</span></span> <span data-ttu-id="5810a-158">No entanto, você sempre pode acessar os dados originais do `turnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="5810a-158">However, you can always access the original data from the `turnContext` object.</span></span>

<span data-ttu-id="5810a-159">O `channelData` objeto não está incluído em mensagens em conversas pessoais, pois elas ocorrem fora de um canal.</span><span class="sxs-lookup"><span data-stu-id="5810a-159">The `channelData` object is not included in messages in personal conversations, as these take place outside of a channel.</span></span>

<span data-ttu-id="5810a-160">Um objeto `channelData` típico em uma atividade enviada ao bot contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="5810a-160">A typical `channelData` object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="5810a-161">`eventType`: Tipo de evento do Teams passado somente em casos de [eventos de modificação de canal.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="5810a-161">`eventType`: Teams event type passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="5810a-162">`tenant.id`: ID de locatário do Azure Active Directory passada em todos os contextos.</span><span class="sxs-lookup"><span data-stu-id="5810a-162">`tenant.id`: Azure Active Directory tenant ID passed in all contexts.</span></span>
* <span data-ttu-id="5810a-163">`team`: Passado somente em contextos de canal, não em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="5810a-163">`team`: Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="5810a-164">`id`: GUID para o canal.</span><span class="sxs-lookup"><span data-stu-id="5810a-164">`id`: GUID for the channel.</span></span>
  * <span data-ttu-id="5810a-165">`name`: Nome da equipe passada somente em casos de [eventos de renomear a equipe.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="5810a-165">`name`: Name of the team passed only in cases of [team rename events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="5810a-166">`channel`: Passado somente em contextos de canal quando o bot é mencionado ou para eventos em canais em equipes onde o bot foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="5810a-166">`channel`: Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added.</span></span>
  * <span data-ttu-id="5810a-167">`id`: GUID para o canal.</span><span class="sxs-lookup"><span data-stu-id="5810a-167">`id`: GUID for the channel.</span></span>
  * <span data-ttu-id="5810a-168">`name`: Nome do canal passado somente em casos de eventos [de modificação de canal.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="5810a-168">`name`: Channel name passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="5810a-169">`channelData.teamsTeamId`: Preterido.</span><span class="sxs-lookup"><span data-stu-id="5810a-169">`channelData.teamsTeamId`: Deprecated.</span></span> <span data-ttu-id="5810a-170">Essa propriedade só é incluída para compatibilidade com compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="5810a-170">This property is only included for backward compatibility.</span></span>
* <span data-ttu-id="5810a-171">`channelData.teamsChannelId`: Preterido.</span><span class="sxs-lookup"><span data-stu-id="5810a-171">`channelData.teamsChannelId`: Deprecated.</span></span> <span data-ttu-id="5810a-172">Essa propriedade só é incluída para compatibilidade com compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="5810a-172">This property is only included for backward compatibility.</span></span>

### <a name="example-channeldata-object-channelcreated-event"></a><span data-ttu-id="5810a-173">Objeto channelData de exemplo (evento channelCreated)</span><span class="sxs-lookup"><span data-stu-id="5810a-173">Example channelData object (channelCreated event)</span></span>

<span data-ttu-id="5810a-174">O código a seguir mostra um exemplo do objeto channelData:</span><span class="sxs-lookup"><span data-stu-id="5810a-174">The following code shows an example of channelData object:</span></span>

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

<span data-ttu-id="5810a-175">As mensagens recebidas ou enviadas ao bot podem incluir diferentes tipos de conteúdo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5810a-175">Messages received from or sent to your bot can include different types of message content.</span></span>

## <a name="message-content"></a><span data-ttu-id="5810a-176">Conteúdo da mensagem</span><span class="sxs-lookup"><span data-stu-id="5810a-176">Message content</span></span>

<span data-ttu-id="5810a-177">Seu bot pode enviar rich text, pictures e cards.</span><span class="sxs-lookup"><span data-stu-id="5810a-177">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="5810a-178">Os usuários podem enviar texto e imagens rich para seu bot.</span><span class="sxs-lookup"><span data-stu-id="5810a-178">Users can send rich text and pictures to your bot.</span></span>

| <span data-ttu-id="5810a-179">Formatar</span><span class="sxs-lookup"><span data-stu-id="5810a-179">Format</span></span>    | <span data-ttu-id="5810a-180">De usuário para bot</span><span class="sxs-lookup"><span data-stu-id="5810a-180">From user to bot</span></span> | <span data-ttu-id="5810a-181">De bot para usuário</span><span class="sxs-lookup"><span data-stu-id="5810a-181">From bot to user</span></span> | <span data-ttu-id="5810a-182">Observações</span><span class="sxs-lookup"><span data-stu-id="5810a-182">Notes</span></span>                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| <span data-ttu-id="5810a-183">Rich text </span><span class="sxs-lookup"><span data-stu-id="5810a-183">Rich text</span></span> | <span data-ttu-id="5810a-184">✔</span><span class="sxs-lookup"><span data-stu-id="5810a-184">✔</span></span>                | <span data-ttu-id="5810a-185">✔</span><span class="sxs-lookup"><span data-stu-id="5810a-185">✔</span></span>                |                                                                                         |
| <span data-ttu-id="5810a-186">Imagens</span><span class="sxs-lookup"><span data-stu-id="5810a-186">Pictures</span></span>  | <span data-ttu-id="5810a-187">✔</span><span class="sxs-lookup"><span data-stu-id="5810a-187">✔</span></span>                | <span data-ttu-id="5810a-188">✔</span><span class="sxs-lookup"><span data-stu-id="5810a-188">✔</span></span>                | <span data-ttu-id="5810a-189">Máximo de 1024×1024 e 1 MB no formato PNG, JPEG ou GIF.</span><span class="sxs-lookup"><span data-stu-id="5810a-189">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="5810a-190">Gif animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="5810a-190">Animated GIF is not supported.</span></span>  |
| <span data-ttu-id="5810a-191">Cartões</span><span class="sxs-lookup"><span data-stu-id="5810a-191">Cards</span></span>     | <span data-ttu-id="5810a-192">✖</span><span class="sxs-lookup"><span data-stu-id="5810a-192">✖</span></span>                | <span data-ttu-id="5810a-193">✔</span><span class="sxs-lookup"><span data-stu-id="5810a-193">✔</span></span>                | <span data-ttu-id="5810a-194">Consulte a [referência de cartão do Teams](~/task-modules-and-cards/cards/cards-reference.md) para cartões com suporte.</span><span class="sxs-lookup"><span data-stu-id="5810a-194">See the [Teams card reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards.</span></span> |
| <span data-ttu-id="5810a-195">Emojis</span><span class="sxs-lookup"><span data-stu-id="5810a-195">Emojis</span></span>    | <span data-ttu-id="5810a-196">✖</span><span class="sxs-lookup"><span data-stu-id="5810a-196">✖</span></span>                | <span data-ttu-id="5810a-197">✔</span><span class="sxs-lookup"><span data-stu-id="5810a-197">✔</span></span>                | <span data-ttu-id="5810a-198">Atualmente, o Teams dá suporte a emojis por meio do UTF-16, como U+1F600 para face de riso.</span><span class="sxs-lookup"><span data-stu-id="5810a-198">Teams currently supports emojis through UTF-16, such as U+1F600 for grinning face.</span></span> |

<span data-ttu-id="5810a-199">Você também pode adicionar notificações à sua mensagem usando a `Notification.Alert` propriedade.</span><span class="sxs-lookup"><span data-stu-id="5810a-199">You can also add notifications to your message using the `Notification.Alert` property.</span></span>

## <a name="notifications-to-your-message"></a><span data-ttu-id="5810a-200">Notificações à sua mensagem</span><span class="sxs-lookup"><span data-stu-id="5810a-200">Notifications to your message</span></span>

<span data-ttu-id="5810a-201">As notificações alertam os usuários sobre novas tarefas, menções e comentários.</span><span class="sxs-lookup"><span data-stu-id="5810a-201">Notifications alert users about new tasks, mentions, and comments.</span></span> <span data-ttu-id="5810a-202">Esses alertas estão relacionados ao que os usuários estão trabalhando ou ao que devem observar inserindo um aviso no feed de atividades.</span><span class="sxs-lookup"><span data-stu-id="5810a-202">These alerts are related to what users are working on or what they must look at by inserting a notice into their activity feed.</span></span> <span data-ttu-id="5810a-203">Para que as notificações acionem de sua mensagem bot, de definir a propriedade `TeamsChannelData` `Notification.Alert` objects como true.</span><span class="sxs-lookup"><span data-stu-id="5810a-203">For notifications to trigger from your bot message, set the `TeamsChannelData` objects `Notification.Alert` property to true.</span></span> <span data-ttu-id="5810a-204">A ativação ou não de uma notificação depende das configurações do Teams do usuário individual e você não pode substituir essas configurações.</span><span class="sxs-lookup"><span data-stu-id="5810a-204">Whether or not a notification is raised depends on the individual user's Teams settings and you cannot override these settings.</span></span> <span data-ttu-id="5810a-205">O tipo de notificação é um banner ou um banner e um email.</span><span class="sxs-lookup"><span data-stu-id="5810a-205">The notification type is either a banner or both a banner and an email.</span></span>

<span data-ttu-id="5810a-206">O código a seguir mostra um exemplo de adição de notificações à sua mensagem:</span><span class="sxs-lookup"><span data-stu-id="5810a-206">The following code shows an example of adding notifications to your message:</span></span>

# <a name="c"></a>[<span data-ttu-id="5810a-207">C#</span><span class="sxs-lookup"><span data-stu-id="5810a-207">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescript"></a>[<span data-ttu-id="5810a-208">TypeScript</span><span class="sxs-lookup"><span data-stu-id="5810a-208">TypeScript</span></span>](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="python"></a>[<span data-ttu-id="5810a-209">Python</span><span class="sxs-lookup"><span data-stu-id="5810a-209">Python</span></span>](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="json"></a>[<span data-ttu-id="5810a-210">JSON</span><span class="sxs-lookup"><span data-stu-id="5810a-210">JSON</span></span>](#tab/json)

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

<span data-ttu-id="5810a-211">Para aprimorar sua mensagem, você pode incluir imagens como anexos a essa mensagem.</span><span class="sxs-lookup"><span data-stu-id="5810a-211">To enhance your message, you can include pictures as attachments to that message.</span></span>

## <a name="picture-messages"></a><span data-ttu-id="5810a-212">Mensagens de imagem</span><span class="sxs-lookup"><span data-stu-id="5810a-212">Picture messages</span></span>

<span data-ttu-id="5810a-213">As imagens são enviadas adicionando anexos a uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="5810a-213">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="5810a-214">Para obter mais informações sobre anexos, consulte [Documentação da Estrutura de Bots.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments)</span><span class="sxs-lookup"><span data-stu-id="5810a-214">For more information on attachments, see [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).</span></span>

<span data-ttu-id="5810a-215">As imagens podem ter no máximo 1024×1024 e 1 MB no formato PNG, JPEG ou GIF.</span><span class="sxs-lookup"><span data-stu-id="5810a-215">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="5810a-216">Gif animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="5810a-216">Animated GIF is not supported.</span></span>

<span data-ttu-id="5810a-217">Especifique a altura e a largura de cada imagem usando XML.</span><span class="sxs-lookup"><span data-stu-id="5810a-217">Specify the height and width of each image by using XML.</span></span> <span data-ttu-id="5810a-218">Na marcação, o tamanho da imagem é padrão para 256×256.</span><span class="sxs-lookup"><span data-stu-id="5810a-218">In markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="5810a-219">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5810a-219">For example:</span></span>

* <span data-ttu-id="5810a-220">Use: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` .</span><span class="sxs-lookup"><span data-stu-id="5810a-220">Use: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`.</span></span>
* <span data-ttu-id="5810a-221">Não use: `![Duck on a rock](http://aka.ms/Fo983c)` .</span><span class="sxs-lookup"><span data-stu-id="5810a-221">Do not use: `![Duck on a rock](http://aka.ms/Fo983c)`.</span></span>

<span data-ttu-id="5810a-222">Um bot de conversa pode incluir cartões adaptáveis que simplificam fluxos de trabalho de negócios.</span><span class="sxs-lookup"><span data-stu-id="5810a-222">A conversational bot can include adaptive cards that simplify business workflows.</span></span> <span data-ttu-id="5810a-223">Os cartões adaptáveis oferecem texto, fala, imagens, botões e campos de entrada personalizáveis.</span><span class="sxs-lookup"><span data-stu-id="5810a-223">Adaptive cards offer rich customizable text, speech, images, buttons, and input fields.</span></span>

## <a name="adaptive-cards"></a><span data-ttu-id="5810a-224">Cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="5810a-224">Adaptive cards</span></span>

<span data-ttu-id="5810a-225">Cartões adaptáveis podem ser de autoria em um bot e mostrados em vários aplicativos, como o Teams, seu site e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="5810a-225">Adaptive cards can be authored in a bot and shown in multiple apps such as Teams, your website, and so on.</span></span> <span data-ttu-id="5810a-226">Para obter mais informações, consulte [cartões adaptáveis](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span><span class="sxs-lookup"><span data-stu-id="5810a-226">For more information, see [adaptive cards](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>

<span data-ttu-id="5810a-227">O código a seguir mostra um exemplo de envio de um cartão adaptável simples:</span><span class="sxs-lookup"><span data-stu-id="5810a-227">The following code shows an example of sending a simple adaptive card:</span></span>

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

<span data-ttu-id="5810a-228">Para saber mais sobre cartões e cartões em bots, consulte [documentação de cartões.](~/task-modules-and-cards/what-are-cards.md)</span><span class="sxs-lookup"><span data-stu-id="5810a-228">To know more about cards and cards in bots, see [cards documentation](~/task-modules-and-cards/what-are-cards.md).</span></span>

<span data-ttu-id="5810a-229">A próxima seção fornece respostas de código de status para erros gerados a partir de APIs bot.</span><span class="sxs-lookup"><span data-stu-id="5810a-229">The next section provides status code responses for errors generated from Bot APIs.</span></span>

## <a name="status-code-responses"></a><span data-ttu-id="5810a-230">Respostas de código de status</span><span class="sxs-lookup"><span data-stu-id="5810a-230">Status code responses</span></span>

<span data-ttu-id="5810a-231">A seguir estão os códigos de status e seus valores de código de erro e mensagem:</span><span class="sxs-lookup"><span data-stu-id="5810a-231">Following are the status codes and their error code and message values:</span></span>

| <span data-ttu-id="5810a-232">Código de status</span><span class="sxs-lookup"><span data-stu-id="5810a-232">Status code</span></span> | <span data-ttu-id="5810a-233">Valores de código de erro e mensagem</span><span class="sxs-lookup"><span data-stu-id="5810a-233">Error code and message values</span></span> | <span data-ttu-id="5810a-234">Descrição</span><span class="sxs-lookup"><span data-stu-id="5810a-234">Description</span></span> |
|----------------|-----------------|-----------------|
| <span data-ttu-id="5810a-235">403</span><span class="sxs-lookup"><span data-stu-id="5810a-235">403</span></span> | <span data-ttu-id="5810a-236">**Código**: `ConversationBlockedByUser`</span><span class="sxs-lookup"><span data-stu-id="5810a-236">**Code**: `ConversationBlockedByUser`</span></span> <br/> <span data-ttu-id="5810a-237">**Mensagem**: "O usuário bloqueou a conversa com o bot".</span><span class="sxs-lookup"><span data-stu-id="5810a-237">**Message**: "User blocked the conversation with the bot."</span></span> | <span data-ttu-id="5810a-238">O usuário bloqueou o bot no chat 1:1 ou em um canal por meio de configurações de moderação.</span><span class="sxs-lookup"><span data-stu-id="5810a-238">User blocked the bot in 1:1 chat or a channel through moderation settings.</span></span> |
| <span data-ttu-id="5810a-239">403</span><span class="sxs-lookup"><span data-stu-id="5810a-239">403</span></span> | <span data-ttu-id="5810a-240">**Código**: `BotNotInConversationRoster`</span><span class="sxs-lookup"><span data-stu-id="5810a-240">**Code**: `BotNotInConversationRoster`</span></span> <br/> <span data-ttu-id="5810a-241">**Mensagem**: "O bot não faz parte da lista de conversas".</span><span class="sxs-lookup"><span data-stu-id="5810a-241">**Message**: "The bot is not part of the conversation roster."</span></span> | <span data-ttu-id="5810a-242">O bot não faz parte da conversa.</span><span class="sxs-lookup"><span data-stu-id="5810a-242">The bot is not part of the conversation.</span></span> |
| <span data-ttu-id="5810a-243">403</span><span class="sxs-lookup"><span data-stu-id="5810a-243">403</span></span> | <span data-ttu-id="5810a-244">**Código**: `BotDisabledByAdmin`</span><span class="sxs-lookup"><span data-stu-id="5810a-244">**Code**: `BotDisabledByAdmin`</span></span> <br/> <span data-ttu-id="5810a-245">**Mensagem**: "O administrador do locatário desabilitou esse bot".</span><span class="sxs-lookup"><span data-stu-id="5810a-245">**Message**: "The tenant admin disabled this bot."</span></span> | <span data-ttu-id="5810a-246">O locatário bloqueou o bot.</span><span class="sxs-lookup"><span data-stu-id="5810a-246">Tenant blocked the bot.</span></span> |
| <span data-ttu-id="5810a-247">401</span><span class="sxs-lookup"><span data-stu-id="5810a-247">401</span></span> | <span data-ttu-id="5810a-248">**Código**: `BotNotRegistered`</span><span class="sxs-lookup"><span data-stu-id="5810a-248">**Code**: `BotNotRegistered`</span></span> <br/> <span data-ttu-id="5810a-249">**Mensagem**: "Nenhum registro encontrado para esse bot".</span><span class="sxs-lookup"><span data-stu-id="5810a-249">**Message**: “No registration found for this bot.”</span></span> | <span data-ttu-id="5810a-250">O registro desse bot não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="5810a-250">The registration for this bot was not found.</span></span> |
| <span data-ttu-id="5810a-251">412</span><span class="sxs-lookup"><span data-stu-id="5810a-251">412</span></span> | <span data-ttu-id="5810a-252">**Código**: `PreconditionFailed`</span><span class="sxs-lookup"><span data-stu-id="5810a-252">**Code**: `PreconditionFailed`</span></span> <br/> <span data-ttu-id="5810a-253">**Mensagem**: "Falha na pré-condição, tente novamente".</span><span class="sxs-lookup"><span data-stu-id="5810a-253">**Message**: “Precondition failed, please try again.”</span></span> | <span data-ttu-id="5810a-254">Uma pré-condição falhou em uma de nossas dependências devido a várias operações simultâneas na mesma conversa.</span><span class="sxs-lookup"><span data-stu-id="5810a-254">A precondition failed on one of our dependencies due to multiple concurrent operations on the same conversation.</span></span> |
| <span data-ttu-id="5810a-255">404</span><span class="sxs-lookup"><span data-stu-id="5810a-255">404</span></span> | <span data-ttu-id="5810a-256">**Código**: `ConversationNotFound`</span><span class="sxs-lookup"><span data-stu-id="5810a-256">**Code**: `ConversationNotFound`</span></span> <br/> <span data-ttu-id="5810a-257">**Mensagem**: "Conversa não encontrada".</span><span class="sxs-lookup"><span data-stu-id="5810a-257">**Message**: “Conversation not found.”</span></span> | <span data-ttu-id="5810a-258">A conversa não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="5810a-258">The conversation was not found.</span></span> |
| <span data-ttu-id="5810a-259">413</span><span class="sxs-lookup"><span data-stu-id="5810a-259">413</span></span> | <span data-ttu-id="5810a-260">**Código**: `MessageSizeTooBig`</span><span class="sxs-lookup"><span data-stu-id="5810a-260">**Code**: `MessageSizeTooBig`</span></span> <br/> <span data-ttu-id="5810a-261">**Mensagem**: "Tamanho da mensagem muito grande".</span><span class="sxs-lookup"><span data-stu-id="5810a-261">**Message**: “Message size too large.”</span></span> | <span data-ttu-id="5810a-262">O tamanho da solicitação de entrada era muito grande.</span><span class="sxs-lookup"><span data-stu-id="5810a-262">The size on the incoming request was too large.</span></span> |
| <span data-ttu-id="5810a-263">429</span><span class="sxs-lookup"><span data-stu-id="5810a-263">429</span></span> | <span data-ttu-id="5810a-264">**Código**: `Throttled`</span><span class="sxs-lookup"><span data-stu-id="5810a-264">**Code**: `Throttled`</span></span> <br/> <span data-ttu-id="5810a-265">**Mensagem**: "Muitas solicitações".</span><span class="sxs-lookup"><span data-stu-id="5810a-265">**Message**: “Too many requests.”</span></span> <span data-ttu-id="5810a-266">Também retorna quando repetir depois.</span><span class="sxs-lookup"><span data-stu-id="5810a-266">Also returns when to retry after.</span></span> | <span data-ttu-id="5810a-267">Muitas solicitações foram enviadas pelo bot.</span><span class="sxs-lookup"><span data-stu-id="5810a-267">Too many requests were sent by the bot.</span></span> <span data-ttu-id="5810a-268">Para obter mais informações, consulte [limite de taxa](~/bots/how-to/rate-limit.md).</span><span class="sxs-lookup"><span data-stu-id="5810a-268">For more information, see [rate limit](~/bots/how-to/rate-limit.md).</span></span> |

<span data-ttu-id="5810a-269">A próxima seção ilustra um exemplo de código simples que incorpora o fluxo de conversa básica em um aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="5810a-269">The next section illustrates a simple code sample that incorporates basic conversational flow into a Teams application.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5810a-270">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5810a-270">Code sample</span></span>

<span data-ttu-id="5810a-271">A seguir estão os exemplos de código para o bot de conversa do Teams:</span><span class="sxs-lookup"><span data-stu-id="5810a-271">Following are the code samples for Teams conversation bot:</span></span>

|<span data-ttu-id="5810a-272">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="5810a-272">Sample name</span></span> | <span data-ttu-id="5810a-273">Descrição</span><span class="sxs-lookup"><span data-stu-id="5810a-273">Description</span></span> | <span data-ttu-id="5810a-274">. NETCore</span><span class="sxs-lookup"><span data-stu-id="5810a-274">.NETCore</span></span> | <span data-ttu-id="5810a-275">Node.js</span><span class="sxs-lookup"><span data-stu-id="5810a-275">Node.js</span></span> | <span data-ttu-id="5810a-276">Python</span><span class="sxs-lookup"><span data-stu-id="5810a-276">Python</span></span> |
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="5810a-277">Bot de conversas do Teams</span><span class="sxs-lookup"><span data-stu-id="5810a-277">Teams conversation bot</span></span> | <span data-ttu-id="5810a-278">Manipulação de eventos de mensagens e conversas.</span><span class="sxs-lookup"><span data-stu-id="5810a-278">Messaging and conversation event handling.</span></span> |[<span data-ttu-id="5810a-279">View</span><span class="sxs-lookup"><span data-stu-id="5810a-279">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="5810a-280">View</span><span class="sxs-lookup"><span data-stu-id="5810a-280">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [<span data-ttu-id="5810a-281">View</span><span class="sxs-lookup"><span data-stu-id="5810a-281">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="see-also"></a><span data-ttu-id="5810a-282">Confira também</span><span class="sxs-lookup"><span data-stu-id="5810a-282">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5810a-283">Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="5810a-283">Send proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="5810a-284">Inscreva-se em eventos de conversa</span><span class="sxs-lookup"><span data-stu-id="5810a-284">Subscribe to conversation events</span></span>](~/bots/how-to/conversations/subscribe-to-conversation-events.md)

## <a name="next-step"></a><span data-ttu-id="5810a-285">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="5810a-285">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5810a-286">Menus de comando bot</span><span class="sxs-lookup"><span data-stu-id="5810a-286">Bot command menus</span></span>](~/bots/how-to/create-a-bot-commands-menu.md)
