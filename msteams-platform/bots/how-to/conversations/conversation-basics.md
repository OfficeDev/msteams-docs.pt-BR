---
title: Noções básicas sobre conversas
description: descreve maneiras de ter uma conversa com um bot do Microsoft Teams
ms.topic: overview
ms.author: anclear
keyword: conversations basics receive message send message picture message channel data adaptive cards
ms.openlocfilehash: 193a93dbf775389383e0385207fa4112440bffe5
ms.sourcegitcommit: 82bda0599ba2676ab9348c2f4284f73c7dad0838
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596671"
---
# <a name="conversation-basics"></a><span data-ttu-id="f1323-103">Noções básicas sobre conversas</span><span class="sxs-lookup"><span data-stu-id="f1323-103">Conversation basics</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="f1323-104">Uma conversa é uma série de mensagens enviadas entre o bot do Microsoft Teams e um ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="f1323-104">A conversation is a series of messages sent between your Microsoft Teams bot and one or more users.</span></span> <span data-ttu-id="f1323-105">Há três tipos de conversas, também chamados de escopos no Teams:</span><span class="sxs-lookup"><span data-stu-id="f1323-105">There are three types of conversations, also called scopes in Teams:</span></span>

| <span data-ttu-id="f1323-106">Tipo de conversa</span><span class="sxs-lookup"><span data-stu-id="f1323-106">Conversation type</span></span> | <span data-ttu-id="f1323-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1323-107">Description</span></span> |
| ------- | ----------- |
| `channel` | <span data-ttu-id="f1323-108">Esse tipo de conversa é visível para todos os membros do canal.</span><span class="sxs-lookup"><span data-stu-id="f1323-108">This conversation type is visible to all members of the channel.</span></span> |
| `personal` | <span data-ttu-id="f1323-109">Esse tipo de conversa inclui conversas entre bots e um único usuário.</span><span class="sxs-lookup"><span data-stu-id="f1323-109">This conversation type includes conversations between bots and a single user.</span></span> |
| `groupChat` | <span data-ttu-id="f1323-110">Esse tipo de conversa inclui chat entre um bot e dois ou mais usuários.</span><span class="sxs-lookup"><span data-stu-id="f1323-110">This conversation type includes chat between a bot and two or more users.</span></span> <span data-ttu-id="f1323-111">Ele também habilita seu bot em chats de reunião.</span><span class="sxs-lookup"><span data-stu-id="f1323-111">It also enables your bot in meeting chats.</span></span> |

<span data-ttu-id="f1323-112">Um bot se comporta de forma diferente, dependendo da conversa em que ele está envolvido:</span><span class="sxs-lookup"><span data-stu-id="f1323-112">A bot behaves differently depending on the conversation it is involved in:</span></span>

* <span data-ttu-id="f1323-113">Bots em conversas de chat de canal e grupo exigem que o usuário @ mencione o bot para invocá-lo em um canal.</span><span class="sxs-lookup"><span data-stu-id="f1323-113">Bots in channel and group chat conversations require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="f1323-114">Bots em uma conversa um para um não exigem uma menção @.</span><span class="sxs-lookup"><span data-stu-id="f1323-114">Bots in a one-to-one conversation do not require an @ mention.</span></span> <span data-ttu-id="f1323-115">Todas as mensagens enviadas pelo usuário são encaminhadas para seu bot.</span><span class="sxs-lookup"><span data-stu-id="f1323-115">All messages sent by the user routes to your bot.</span></span>

<span data-ttu-id="f1323-116">Para que o bot funcione em uma determinada conversa ou escopo, adicione suporte a esse escopo no manifesto [do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="f1323-116">For the bot to work in a particular conversation or scope, add support to that scope in the [app manifest](~/resources/schema/manifest-schema.md).</span></span>

## <a name="messages-in-bot-conversations"></a><span data-ttu-id="f1323-117">Mensagens em conversas de bot</span><span class="sxs-lookup"><span data-stu-id="f1323-117">Messages in bot conversations</span></span>

<span data-ttu-id="f1323-118">Cada mensagem em uma conversa é um `Activity` objeto do tipo `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="f1323-118">Each message in a conversation is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="f1323-119">Quando um usuário envia uma mensagem, o Teams posta a mensagem no bot.</span><span class="sxs-lookup"><span data-stu-id="f1323-119">When a user sends a message, Teams posts the message to your bot.</span></span> <span data-ttu-id="f1323-120">O Teams envia um objeto JSON para o ponto de extremidade de mensagens do bot.</span><span class="sxs-lookup"><span data-stu-id="f1323-120">Teams sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="f1323-121">Seu bot examina a mensagem para determinar seu tipo e responde de acordo.</span><span class="sxs-lookup"><span data-stu-id="f1323-121">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="f1323-122">As conversas básicas são manipuladas por meio do conector da Estrutura do Bot, uma única API REST.</span><span class="sxs-lookup"><span data-stu-id="f1323-122">Basic conversations are handled through the Bot Framework connector, a single REST API.</span></span> <span data-ttu-id="f1323-123">Essa API permite que seu bot se comunique com o Teams e outros canais.</span><span class="sxs-lookup"><span data-stu-id="f1323-123">This API enables your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="f1323-124">O SDK do Construtor de Bots fornece o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f1323-124">The Bot Builder SDK provides the following:</span></span>

* <span data-ttu-id="f1323-125">Acesso fácil ao conector da Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="f1323-125">Easy access to the Bot Framework connector.</span></span>
* <span data-ttu-id="f1323-126">Funcionalidade adicional para gerenciar o fluxo e o estado da conversa.</span><span class="sxs-lookup"><span data-stu-id="f1323-126">Additional functionality to manage conversation flow and state.</span></span>
* <span data-ttu-id="f1323-127">Maneiras simples de incorporar serviços cognitivos, como o Processamento de Linguagem Natural (NLP).</span><span class="sxs-lookup"><span data-stu-id="f1323-127">Simple ways to incorporate cognitive services such as Natural Language Processing (NLP).</span></span>

<span data-ttu-id="f1323-128">Seu bot recebe mensagens do Teams usando a propriedade e envia respostas de mensagem única ou `Text` múltipla aos usuários.</span><span class="sxs-lookup"><span data-stu-id="f1323-128">Your bot receives messages from Teams using the `Text` property and it sends single or multiple message responses to the users.</span></span>

## <a name="receive-a-message"></a><span data-ttu-id="f1323-129">Receber uma mensagem</span><span class="sxs-lookup"><span data-stu-id="f1323-129">Receive a message</span></span>

<span data-ttu-id="f1323-130">Para receber uma mensagem de texto, use a propriedade `Text` do objeto `Activity`.</span><span class="sxs-lookup"><span data-stu-id="f1323-130">To receive a text message, use the `Text` property of the `Activity` object.</span></span> <span data-ttu-id="f1323-131">No manipulador de atividades do bot, alterne o contexto do objeto `Activity` para ler uma única solicitação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f1323-131">In the bot's activity handler, use the turn context object's `Activity` to read a single message request.</span></span>

<span data-ttu-id="f1323-132">O código a seguir mostra um exemplo de recebimento de uma mensagem:</span><span class="sxs-lookup"><span data-stu-id="f1323-132">The following code shows an example of receiving a message:</span></span>

# <a name="c"></a>[<span data-ttu-id="f1323-133">C#</span><span class="sxs-lookup"><span data-stu-id="f1323-133">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescript"></a>[<span data-ttu-id="f1323-134">TypeScript</span><span class="sxs-lookup"><span data-stu-id="f1323-134">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="f1323-135">Python</span><span class="sxs-lookup"><span data-stu-id="f1323-135">Python</span></span>](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="json"></a>[<span data-ttu-id="f1323-136">JSON</span><span class="sxs-lookup"><span data-stu-id="f1323-136">JSON</span></span>](#tab/json)

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

## <a name="send-a-message"></a><span data-ttu-id="f1323-137">Enviar uma mensagem</span><span class="sxs-lookup"><span data-stu-id="f1323-137">Send a message</span></span>

<span data-ttu-id="f1323-138">Para enviar uma mensagem de texto, especifique a cadeia de caracteres que você deseja enviar como a atividade.</span><span class="sxs-lookup"><span data-stu-id="f1323-138">To send a text message, specify the string you want to send as the activity.</span></span> <span data-ttu-id="f1323-139">No manipulador de atividades do bot, use o método do objeto turn context `SendActivityAsync` para enviar uma única resposta de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f1323-139">In the bot's activity handler, use the turn context object's `SendActivityAsync` method to send a single message response.</span></span> <span data-ttu-id="f1323-140">Use o método do `SendActivitiesAsync` objeto para enviar várias respostas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="f1323-140">Use the object's `SendActivitiesAsync` method to send multiple responses at once.</span></span> <span data-ttu-id="f1323-141">O código a seguir mostra um exemplo de envio de uma mensagem quando um usuário é adicionado a uma conversa:</span><span class="sxs-lookup"><span data-stu-id="f1323-141">The following code shows an example of sending a message when a user is added to a conversation:</span></span>

<span data-ttu-id="f1323-142">O código a seguir mostra um exemplo de envio de uma mensagem:</span><span class="sxs-lookup"><span data-stu-id="f1323-142">The following code shows an example of sending a message:</span></span>

# <a name="c"></a>[<span data-ttu-id="f1323-143">C#</span><span class="sxs-lookup"><span data-stu-id="f1323-143">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescript"></a>[<span data-ttu-id="f1323-144">TypeScript</span><span class="sxs-lookup"><span data-stu-id="f1323-144">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="f1323-145">Python</span><span class="sxs-lookup"><span data-stu-id="f1323-145">Python</span></span>](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="json"></a>[<span data-ttu-id="f1323-146">JSON</span><span class="sxs-lookup"><span data-stu-id="f1323-146">JSON</span></span>](#tab/json)

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
> <span data-ttu-id="f1323-147">A divisão de mensagens ocorre quando uma mensagem de texto e um anexo são enviados na mesma carga de atividade.</span><span class="sxs-lookup"><span data-stu-id="f1323-147">Message splitting occurs when a text message and an attachment are sent in the same activity payload.</span></span> <span data-ttu-id="f1323-148">Essa atividade é dividida em atividades separadas pelo Microsoft Teams, uma com apenas uma mensagem de texto e outra com um anexo.</span><span class="sxs-lookup"><span data-stu-id="f1323-148">This activity is split into separate activities by Microsoft Teams, one with just a text message and the other with an attachment.</span></span> <span data-ttu-id="f1323-149">À medida que a atividade é dividida, você não recebe a ID da mensagem em resposta, que é usada para atualizar [ou excluir](~/bots/how-to/update-and-delete-bot-messages.md) a mensagem proativamente.</span><span class="sxs-lookup"><span data-stu-id="f1323-149">As the activity is split, you do not receive the message ID in response, which is used to [update or delete](~/bots/how-to/update-and-delete-bot-messages.md) the message proactively.</span></span> <span data-ttu-id="f1323-150">É recomendável enviar atividades separadas em vez de depender da divisão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f1323-150">It is recommended to send separate activities instead of depending on message splitting.</span></span>

<span data-ttu-id="f1323-151">As mensagens enviadas entre usuários e bots incluem dados de canal interno dentro da mensagem.</span><span class="sxs-lookup"><span data-stu-id="f1323-151">Messages sent between users and bots include internal channel data within the message.</span></span> <span data-ttu-id="f1323-152">Esses dados permitem que o bot se comunique corretamente nesse canal.</span><span class="sxs-lookup"><span data-stu-id="f1323-152">This data allows the bot to communicate properly on that channel.</span></span> <span data-ttu-id="f1323-153">O SDK do Construtor de Bots permite modificar a estrutura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f1323-153">The Bot Builder SDK allows you to modify the message structure.</span></span>

## <a name="teams-channel-data"></a><span data-ttu-id="f1323-154">Dados do canal do Teams</span><span class="sxs-lookup"><span data-stu-id="f1323-154">Teams channel data</span></span>

<span data-ttu-id="f1323-155">O `channelData` objeto contém informações específicas do Teams e é uma fonte definitiva para IDs de equipe e canal.</span><span class="sxs-lookup"><span data-stu-id="f1323-155">The `channelData` object contains Teams-specific information and is a definitive source for team and channel IDs.</span></span> <span data-ttu-id="f1323-156">Opcionalmente, você pode armazenar em cache e usar essas IDs como chaves para armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="f1323-156">Optionally, you can cache and use these IDs as keys for local storage.</span></span> <span data-ttu-id="f1323-157">O no SDK normalmente retira informações importantes do objeto para `TeamsActivityHandler` `channelData` torná-lo facilmente acessível.</span><span class="sxs-lookup"><span data-stu-id="f1323-157">The `TeamsActivityHandler` in the SDK typically pulls out important information from the `channelData` object to make it easily accessible.</span></span> <span data-ttu-id="f1323-158">No entanto, você sempre pode acessar os dados originais do `turnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="f1323-158">However, you can always access the original data from the `turnContext` object.</span></span>

<span data-ttu-id="f1323-159">O `channelData` objeto não está incluído em mensagens em conversas pessoais, pois elas ocorrem fora de um canal.</span><span class="sxs-lookup"><span data-stu-id="f1323-159">The `channelData` object is not included in messages in personal conversations, as these take place outside of a channel.</span></span>

<span data-ttu-id="f1323-160">Um objeto `channelData` típico em uma atividade enviada ao bot contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="f1323-160">A typical `channelData` object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="f1323-161">`eventType`: Tipo de evento do Teams passado somente em casos de [eventos de modificação de canal.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="f1323-161">`eventType`: Teams event type passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="f1323-162">`tenant.id`: ID de locatário do Azure Active Directory passada em todos os contextos.</span><span class="sxs-lookup"><span data-stu-id="f1323-162">`tenant.id`: Azure Active Directory tenant ID passed in all contexts.</span></span>
* <span data-ttu-id="f1323-163">`team`: Passado somente em contextos de canal, não em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="f1323-163">`team`: Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="f1323-164">`id`: GUID para o canal.</span><span class="sxs-lookup"><span data-stu-id="f1323-164">`id`: GUID for the channel.</span></span>
  * <span data-ttu-id="f1323-165">`name`: Nome da equipe passada somente em casos de [eventos de renomear a equipe.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="f1323-165">`name`: Name of the team passed only in cases of [team rename events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="f1323-166">`channel`: Passado somente em contextos de canal quando o bot é mencionado ou para eventos em canais em equipes onde o bot foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="f1323-166">`channel`: Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added.</span></span>
  * <span data-ttu-id="f1323-167">`id`: GUID para o canal.</span><span class="sxs-lookup"><span data-stu-id="f1323-167">`id`: GUID for the channel.</span></span>
  * <span data-ttu-id="f1323-168">`name`: Nome do canal passado somente em casos de eventos [de modificação de canal.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="f1323-168">`name`: Channel name passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="f1323-169">`channelData.teamsTeamId`: Preterido.</span><span class="sxs-lookup"><span data-stu-id="f1323-169">`channelData.teamsTeamId`: Deprecated.</span></span> <span data-ttu-id="f1323-170">Essa propriedade só é incluída para compatibilidade com compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="f1323-170">This property is only included for backward compatibility.</span></span>
* <span data-ttu-id="f1323-171">`channelData.teamsChannelId`: Preterido.</span><span class="sxs-lookup"><span data-stu-id="f1323-171">`channelData.teamsChannelId`: Deprecated.</span></span> <span data-ttu-id="f1323-172">Essa propriedade só é incluída para compatibilidade com compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="f1323-172">This property is only included for backward compatibility.</span></span>

### <a name="example-channeldata-object-channelcreated-event"></a><span data-ttu-id="f1323-173">Objeto channelData de exemplo (evento channelCreated)</span><span class="sxs-lookup"><span data-stu-id="f1323-173">Example channelData object (channelCreated event)</span></span>

<span data-ttu-id="f1323-174">O código a seguir mostra um exemplo do objeto channelData:</span><span class="sxs-lookup"><span data-stu-id="f1323-174">The following code shows an example of channelData object:</span></span>

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

<span data-ttu-id="f1323-175">As mensagens recebidas ou enviadas ao bot podem incluir diferentes tipos de conteúdo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f1323-175">Messages received from or sent to your bot can include different types of message content.</span></span>

## <a name="message-content"></a><span data-ttu-id="f1323-176">Conteúdo da mensagem</span><span class="sxs-lookup"><span data-stu-id="f1323-176">Message content</span></span>

<span data-ttu-id="f1323-177">Seu bot pode enviar rich text, pictures e cards.</span><span class="sxs-lookup"><span data-stu-id="f1323-177">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="f1323-178">Os usuários podem enviar texto e imagens rich para seu bot.</span><span class="sxs-lookup"><span data-stu-id="f1323-178">Users can send rich text and pictures to your bot.</span></span>

| <span data-ttu-id="f1323-179">Formatar</span><span class="sxs-lookup"><span data-stu-id="f1323-179">Format</span></span>    | <span data-ttu-id="f1323-180">De usuário para bot</span><span class="sxs-lookup"><span data-stu-id="f1323-180">From user to bot</span></span> | <span data-ttu-id="f1323-181">De bot para usuário</span><span class="sxs-lookup"><span data-stu-id="f1323-181">From bot to user</span></span> | <span data-ttu-id="f1323-182">Observações</span><span class="sxs-lookup"><span data-stu-id="f1323-182">Notes</span></span>                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| <span data-ttu-id="f1323-183">Rich text </span><span class="sxs-lookup"><span data-stu-id="f1323-183">Rich text</span></span> | <span data-ttu-id="f1323-184">✔</span><span class="sxs-lookup"><span data-stu-id="f1323-184">✔</span></span>                | <span data-ttu-id="f1323-185">✔</span><span class="sxs-lookup"><span data-stu-id="f1323-185">✔</span></span>                |                                                                                         |
| <span data-ttu-id="f1323-186">Imagens</span><span class="sxs-lookup"><span data-stu-id="f1323-186">Pictures</span></span>  | <span data-ttu-id="f1323-187">✔</span><span class="sxs-lookup"><span data-stu-id="f1323-187">✔</span></span>                | <span data-ttu-id="f1323-188">✔</span><span class="sxs-lookup"><span data-stu-id="f1323-188">✔</span></span>                | <span data-ttu-id="f1323-189">Máximo de 1024×1024 e 1 MB no formato PNG, JPEG ou GIF.</span><span class="sxs-lookup"><span data-stu-id="f1323-189">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="f1323-190">Gif animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="f1323-190">Animated GIF is not supported.</span></span>  |
| <span data-ttu-id="f1323-191">Cartões</span><span class="sxs-lookup"><span data-stu-id="f1323-191">Cards</span></span>     | <span data-ttu-id="f1323-192">✖</span><span class="sxs-lookup"><span data-stu-id="f1323-192">✖</span></span>                | <span data-ttu-id="f1323-193">✔</span><span class="sxs-lookup"><span data-stu-id="f1323-193">✔</span></span>                | <span data-ttu-id="f1323-194">Consulte a [referência de cartão do Teams](~/task-modules-and-cards/cards/cards-reference.md) para cartões com suporte.</span><span class="sxs-lookup"><span data-stu-id="f1323-194">See the [Teams card reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards.</span></span> |
| <span data-ttu-id="f1323-195">Emojis</span><span class="sxs-lookup"><span data-stu-id="f1323-195">Emojis</span></span>    | <span data-ttu-id="f1323-196">✖</span><span class="sxs-lookup"><span data-stu-id="f1323-196">✖</span></span>                | <span data-ttu-id="f1323-197">✔</span><span class="sxs-lookup"><span data-stu-id="f1323-197">✔</span></span>                | <span data-ttu-id="f1323-198">Atualmente, o Teams dá suporte a emojis por meio do UTF-16, como U+1F600 para face de riso.</span><span class="sxs-lookup"><span data-stu-id="f1323-198">Teams currently supports emojis through UTF-16, such as U+1F600 for grinning face.</span></span> |

<span data-ttu-id="f1323-199">Você também pode adicionar notificações à sua mensagem usando a `Notification.Alert` propriedade.</span><span class="sxs-lookup"><span data-stu-id="f1323-199">You can also add notifications to your message using the `Notification.Alert` property.</span></span>

## <a name="notifications-to-your-message"></a><span data-ttu-id="f1323-200">Notificações à sua mensagem</span><span class="sxs-lookup"><span data-stu-id="f1323-200">Notifications to your message</span></span>

<span data-ttu-id="f1323-201">As notificações alertam os usuários sobre novas tarefas, menções e comentários.</span><span class="sxs-lookup"><span data-stu-id="f1323-201">Notifications alert users about new tasks, mentions, and comments.</span></span> <span data-ttu-id="f1323-202">Esses alertas estão relacionados ao que os usuários estão trabalhando ou ao que devem observar inserindo um aviso no feed de atividades.</span><span class="sxs-lookup"><span data-stu-id="f1323-202">These alerts are related to what users are working on or what they must look at by inserting a notice into their activity feed.</span></span> <span data-ttu-id="f1323-203">Para que as notificações acionem de sua mensagem bot, de definir a propriedade `TeamsChannelData` `Notification.Alert` objects como true.</span><span class="sxs-lookup"><span data-stu-id="f1323-203">For notifications to trigger from your bot message, set the `TeamsChannelData` objects `Notification.Alert` property to true.</span></span> <span data-ttu-id="f1323-204">A ativação ou não de uma notificação depende das configurações do Teams do usuário individual e você não pode substituir essas configurações.</span><span class="sxs-lookup"><span data-stu-id="f1323-204">Whether or not a notification is raised depends on the individual user's Teams settings and you cannot override these settings.</span></span> <span data-ttu-id="f1323-205">O tipo de notificação é um banner ou um banner e um email.</span><span class="sxs-lookup"><span data-stu-id="f1323-205">The notification type is either a banner or both a banner and an email.</span></span>

> [!NOTE]
> <span data-ttu-id="f1323-206">O **campo** Resumo exibe qualquer texto do usuário como uma mensagem de notificação no feed.</span><span class="sxs-lookup"><span data-stu-id="f1323-206">The **Summary** field displays any text from the user as a notification message in the feed.</span></span>

<span data-ttu-id="f1323-207">O código a seguir mostra um exemplo de adição de notificações à sua mensagem:</span><span class="sxs-lookup"><span data-stu-id="f1323-207">The following code shows an example of adding notifications to your message:</span></span>

# <a name="c"></a>[<span data-ttu-id="f1323-208">C#</span><span class="sxs-lookup"><span data-stu-id="f1323-208">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescript"></a>[<span data-ttu-id="f1323-209">TypeScript</span><span class="sxs-lookup"><span data-stu-id="f1323-209">TypeScript</span></span>](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="python"></a>[<span data-ttu-id="f1323-210">Python</span><span class="sxs-lookup"><span data-stu-id="f1323-210">Python</span></span>](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="json"></a>[<span data-ttu-id="f1323-211">JSON</span><span class="sxs-lookup"><span data-stu-id="f1323-211">JSON</span></span>](#tab/json)

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

<span data-ttu-id="f1323-212">Para aprimorar sua mensagem, você pode incluir imagens como anexos a essa mensagem.</span><span class="sxs-lookup"><span data-stu-id="f1323-212">To enhance your message, you can include pictures as attachments to that message.</span></span>

## <a name="picture-messages"></a><span data-ttu-id="f1323-213">Mensagens de imagem</span><span class="sxs-lookup"><span data-stu-id="f1323-213">Picture messages</span></span>

<span data-ttu-id="f1323-214">As imagens são enviadas adicionando anexos a uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="f1323-214">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="f1323-215">Para obter mais informações sobre anexos, consulte [Documentação da Estrutura de Bots.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments)</span><span class="sxs-lookup"><span data-stu-id="f1323-215">For more information on attachments, see [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).</span></span>

<span data-ttu-id="f1323-216">As imagens podem ter no máximo 1024×1024 e 1 MB no formato PNG, JPEG ou GIF.</span><span class="sxs-lookup"><span data-stu-id="f1323-216">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="f1323-217">Gif animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="f1323-217">Animated GIF is not supported.</span></span>

<span data-ttu-id="f1323-218">Especifique a altura e a largura de cada imagem usando XML.</span><span class="sxs-lookup"><span data-stu-id="f1323-218">Specify the height and width of each image by using XML.</span></span> <span data-ttu-id="f1323-219">Na marcação, o tamanho da imagem é padrão para 256×256.</span><span class="sxs-lookup"><span data-stu-id="f1323-219">In markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="f1323-220">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f1323-220">For example:</span></span>

* <span data-ttu-id="f1323-221">Use: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` .</span><span class="sxs-lookup"><span data-stu-id="f1323-221">Use: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`.</span></span>
* <span data-ttu-id="f1323-222">Não use: `![Duck on a rock](http://aka.ms/Fo983c)` .</span><span class="sxs-lookup"><span data-stu-id="f1323-222">Do not use: `![Duck on a rock](http://aka.ms/Fo983c)`.</span></span>

<span data-ttu-id="f1323-223">Um bot de conversa pode incluir cartões adaptáveis que simplificam fluxos de trabalho de negócios.</span><span class="sxs-lookup"><span data-stu-id="f1323-223">A conversational bot can include adaptive cards that simplify business workflows.</span></span> <span data-ttu-id="f1323-224">Os cartões adaptáveis oferecem texto, fala, imagens, botões e campos de entrada personalizáveis.</span><span class="sxs-lookup"><span data-stu-id="f1323-224">Adaptive cards offer rich customizable text, speech, images, buttons, and input fields.</span></span>

## <a name="adaptive-cards"></a><span data-ttu-id="f1323-225">Cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="f1323-225">Adaptive cards</span></span>

<span data-ttu-id="f1323-226">Cartões adaptáveis podem ser de autoria em um bot e mostrados em vários aplicativos, como o Teams, seu site e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f1323-226">Adaptive cards can be authored in a bot and shown in multiple apps such as Teams, your website, and so on.</span></span> <span data-ttu-id="f1323-227">Para obter mais informações, consulte [cartões adaptáveis](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span><span class="sxs-lookup"><span data-stu-id="f1323-227">For more information, see [adaptive cards](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>

<span data-ttu-id="f1323-228">O código a seguir mostra um exemplo de envio de um cartão adaptável simples:</span><span class="sxs-lookup"><span data-stu-id="f1323-228">The following code shows an example of sending a simple adaptive card:</span></span>

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

<span data-ttu-id="f1323-229">Para saber mais sobre cartões e cartões em bots, consulte [documentação de cartões.](~/task-modules-and-cards/what-are-cards.md)</span><span class="sxs-lookup"><span data-stu-id="f1323-229">To know more about cards and cards in bots, see [cards documentation](~/task-modules-and-cards/what-are-cards.md).</span></span>

<span data-ttu-id="f1323-230">A próxima seção fornece respostas de código de status para erros gerados a partir de APIs bot.</span><span class="sxs-lookup"><span data-stu-id="f1323-230">The next section provides status code responses for errors generated from Bot APIs.</span></span>

## <a name="status-code-responses"></a><span data-ttu-id="f1323-231">Respostas de código de status</span><span class="sxs-lookup"><span data-stu-id="f1323-231">Status code responses</span></span>

<span data-ttu-id="f1323-232">A seguir estão os códigos de status e seus valores de código de erro e mensagem:</span><span class="sxs-lookup"><span data-stu-id="f1323-232">Following are the status codes and their error code and message values:</span></span>

| <span data-ttu-id="f1323-233">Código de status</span><span class="sxs-lookup"><span data-stu-id="f1323-233">Status code</span></span> | <span data-ttu-id="f1323-234">Valores de código de erro e mensagem</span><span class="sxs-lookup"><span data-stu-id="f1323-234">Error code and message values</span></span> | <span data-ttu-id="f1323-235">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1323-235">Description</span></span> |
|----------------|-----------------|-----------------|
| <span data-ttu-id="f1323-236">403</span><span class="sxs-lookup"><span data-stu-id="f1323-236">403</span></span> | <span data-ttu-id="f1323-237">**Código**: `ConversationBlockedByUser`</span><span class="sxs-lookup"><span data-stu-id="f1323-237">**Code**: `ConversationBlockedByUser`</span></span> <br/> <span data-ttu-id="f1323-238">**Mensagem**: "O usuário bloqueou a conversa com o bot".</span><span class="sxs-lookup"><span data-stu-id="f1323-238">**Message**: "User blocked the conversation with the bot."</span></span> | <span data-ttu-id="f1323-239">O usuário bloqueou o bot no chat 1:1 ou em um canal por meio de configurações de moderação.</span><span class="sxs-lookup"><span data-stu-id="f1323-239">User blocked the bot in 1:1 chat or a channel through moderation settings.</span></span> |
| <span data-ttu-id="f1323-240">403</span><span class="sxs-lookup"><span data-stu-id="f1323-240">403</span></span> | <span data-ttu-id="f1323-241">**Código**: `BotNotInConversationRoster`</span><span class="sxs-lookup"><span data-stu-id="f1323-241">**Code**: `BotNotInConversationRoster`</span></span> <br/> <span data-ttu-id="f1323-242">**Mensagem**: "O bot não faz parte da lista de conversas".</span><span class="sxs-lookup"><span data-stu-id="f1323-242">**Message**: "The bot is not part of the conversation roster."</span></span> | <span data-ttu-id="f1323-243">O bot não faz parte da conversa.</span><span class="sxs-lookup"><span data-stu-id="f1323-243">The bot is not part of the conversation.</span></span> |
| <span data-ttu-id="f1323-244">403</span><span class="sxs-lookup"><span data-stu-id="f1323-244">403</span></span> | <span data-ttu-id="f1323-245">**Código**: `BotDisabledByAdmin`</span><span class="sxs-lookup"><span data-stu-id="f1323-245">**Code**: `BotDisabledByAdmin`</span></span> <br/> <span data-ttu-id="f1323-246">**Mensagem**: "O administrador do locatário desabilitou esse bot".</span><span class="sxs-lookup"><span data-stu-id="f1323-246">**Message**: "The tenant admin disabled this bot."</span></span> | <span data-ttu-id="f1323-247">O locatário bloqueou o bot.</span><span class="sxs-lookup"><span data-stu-id="f1323-247">Tenant blocked the bot.</span></span> |
| <span data-ttu-id="f1323-248">401</span><span class="sxs-lookup"><span data-stu-id="f1323-248">401</span></span> | <span data-ttu-id="f1323-249">**Código**: `BotNotRegistered`</span><span class="sxs-lookup"><span data-stu-id="f1323-249">**Code**: `BotNotRegistered`</span></span> <br/> <span data-ttu-id="f1323-250">**Mensagem**: "Nenhum registro encontrado para esse bot".</span><span class="sxs-lookup"><span data-stu-id="f1323-250">**Message**: “No registration found for this bot.”</span></span> | <span data-ttu-id="f1323-251">O registro desse bot não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="f1323-251">The registration for this bot was not found.</span></span> |
| <span data-ttu-id="f1323-252">412</span><span class="sxs-lookup"><span data-stu-id="f1323-252">412</span></span> | <span data-ttu-id="f1323-253">**Código**: `PreconditionFailed`</span><span class="sxs-lookup"><span data-stu-id="f1323-253">**Code**: `PreconditionFailed`</span></span> <br/> <span data-ttu-id="f1323-254">**Mensagem**: "Falha na pré-condição, tente novamente".</span><span class="sxs-lookup"><span data-stu-id="f1323-254">**Message**: “Precondition failed, please try again.”</span></span> | <span data-ttu-id="f1323-255">Uma pré-condição falhou em uma de nossas dependências devido a várias operações simultâneas na mesma conversa.</span><span class="sxs-lookup"><span data-stu-id="f1323-255">A precondition failed on one of our dependencies due to multiple concurrent operations on the same conversation.</span></span> |
| <span data-ttu-id="f1323-256">404</span><span class="sxs-lookup"><span data-stu-id="f1323-256">404</span></span> | <span data-ttu-id="f1323-257">**Código**: `ConversationNotFound`</span><span class="sxs-lookup"><span data-stu-id="f1323-257">**Code**: `ConversationNotFound`</span></span> <br/> <span data-ttu-id="f1323-258">**Mensagem**: "Conversa não encontrada".</span><span class="sxs-lookup"><span data-stu-id="f1323-258">**Message**: “Conversation not found.”</span></span> | <span data-ttu-id="f1323-259">A conversa não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="f1323-259">The conversation was not found.</span></span> |
| <span data-ttu-id="f1323-260">413</span><span class="sxs-lookup"><span data-stu-id="f1323-260">413</span></span> | <span data-ttu-id="f1323-261">**Código**: `MessageSizeTooBig`</span><span class="sxs-lookup"><span data-stu-id="f1323-261">**Code**: `MessageSizeTooBig`</span></span> <br/> <span data-ttu-id="f1323-262">**Mensagem**: "Tamanho da mensagem muito grande".</span><span class="sxs-lookup"><span data-stu-id="f1323-262">**Message**: “Message size too large.”</span></span> | <span data-ttu-id="f1323-263">O tamanho da solicitação de entrada era muito grande.</span><span class="sxs-lookup"><span data-stu-id="f1323-263">The size on the incoming request was too large.</span></span> |
| <span data-ttu-id="f1323-264">429</span><span class="sxs-lookup"><span data-stu-id="f1323-264">429</span></span> | <span data-ttu-id="f1323-265">**Código**: `Throttled`</span><span class="sxs-lookup"><span data-stu-id="f1323-265">**Code**: `Throttled`</span></span> <br/> <span data-ttu-id="f1323-266">**Mensagem**: "Muitas solicitações".</span><span class="sxs-lookup"><span data-stu-id="f1323-266">**Message**: “Too many requests.”</span></span> <span data-ttu-id="f1323-267">Também retorna quando repetir depois.</span><span class="sxs-lookup"><span data-stu-id="f1323-267">Also returns when to retry after.</span></span> | <span data-ttu-id="f1323-268">Muitas solicitações foram enviadas pelo bot.</span><span class="sxs-lookup"><span data-stu-id="f1323-268">Too many requests were sent by the bot.</span></span> <span data-ttu-id="f1323-269">Para obter mais informações, consulte [limite de taxa](~/bots/how-to/rate-limit.md).</span><span class="sxs-lookup"><span data-stu-id="f1323-269">For more information, see [rate limit](~/bots/how-to/rate-limit.md).</span></span> |

<span data-ttu-id="f1323-270">A próxima seção ilustra um exemplo de código simples que incorpora o fluxo de conversa básica em um aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="f1323-270">The next section illustrates a simple code sample that incorporates basic conversational flow into a Teams application.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f1323-271">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f1323-271">Code sample</span></span>

<span data-ttu-id="f1323-272">A seguir estão os exemplos de código para o bot de conversa do Teams:</span><span class="sxs-lookup"><span data-stu-id="f1323-272">Following are the code samples for Teams conversation bot:</span></span>

|<span data-ttu-id="f1323-273">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="f1323-273">Sample name</span></span> | <span data-ttu-id="f1323-274">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1323-274">Description</span></span> | <span data-ttu-id="f1323-275">. NETCore</span><span class="sxs-lookup"><span data-stu-id="f1323-275">.NETCore</span></span> | <span data-ttu-id="f1323-276">Node.js</span><span class="sxs-lookup"><span data-stu-id="f1323-276">Node.js</span></span> | <span data-ttu-id="f1323-277">Python</span><span class="sxs-lookup"><span data-stu-id="f1323-277">Python</span></span> |
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="f1323-278">Bot de conversas do Teams</span><span class="sxs-lookup"><span data-stu-id="f1323-278">Teams conversation bot</span></span> | <span data-ttu-id="f1323-279">Manipulação de eventos de mensagens e conversas.</span><span class="sxs-lookup"><span data-stu-id="f1323-279">Messaging and conversation event handling.</span></span> |[<span data-ttu-id="f1323-280">View</span><span class="sxs-lookup"><span data-stu-id="f1323-280">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="f1323-281">View</span><span class="sxs-lookup"><span data-stu-id="f1323-281">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [<span data-ttu-id="f1323-282">View</span><span class="sxs-lookup"><span data-stu-id="f1323-282">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="see-also"></a><span data-ttu-id="f1323-283">Confira também</span><span class="sxs-lookup"><span data-stu-id="f1323-283">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1323-284">Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="f1323-284">Send proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="f1323-285">Inscreva-se em eventos de conversa</span><span class="sxs-lookup"><span data-stu-id="f1323-285">Subscribe to conversation events</span></span>](~/bots/how-to/conversations/subscribe-to-conversation-events.md)

## <a name="next-step"></a><span data-ttu-id="f1323-286">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="f1323-286">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1323-287">Menus de comando bot</span><span class="sxs-lookup"><span data-stu-id="f1323-287">Bot command menus</span></span>](~/bots/how-to/create-a-bot-commands-menu.md)
