---
title: Mensagens em conversas de bot
description: Descreve maneiras de ter uma conversa com um bot do Microsoft Teams
ms.topic: overview
ms.author: anclear
localization_priority: Normal
keyword: receive message send message picture message channel data adaptive cards
ms.openlocfilehash: 5944cc299a8ad4bebdaf034d803919a54868e41f
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020923"
---
# <a name="messages-in-bot-conversations"></a><span data-ttu-id="805ce-103">Mensagens em conversas de bot</span><span class="sxs-lookup"><span data-stu-id="805ce-103">Messages in bot conversations</span></span>

<span data-ttu-id="805ce-104">Cada mensagem em uma conversa é um `Activity` objeto do tipo `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="805ce-104">Each message in a conversation is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="805ce-105">Quando um usuário envia uma mensagem, o Teams posta a mensagem no bot.</span><span class="sxs-lookup"><span data-stu-id="805ce-105">When a user sends a message, Teams posts the message to your bot.</span></span> <span data-ttu-id="805ce-106">O Teams envia um objeto JSON para o ponto de extremidade de mensagens do bot.</span><span class="sxs-lookup"><span data-stu-id="805ce-106">Teams sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="805ce-107">Seu bot examina a mensagem para determinar seu tipo e responde de acordo.</span><span class="sxs-lookup"><span data-stu-id="805ce-107">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="805ce-108">As conversas básicas são manipuladas por meio do conector da Estrutura do Bot, uma única API REST.</span><span class="sxs-lookup"><span data-stu-id="805ce-108">Basic conversations are handled through the Bot Framework connector, a single REST API.</span></span> <span data-ttu-id="805ce-109">Essa API permite que seu bot se comunique com o Teams e outros canais.</span><span class="sxs-lookup"><span data-stu-id="805ce-109">This API enables your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="805ce-110">O SDK do Construtor de Bots fornece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="805ce-110">The Bot Builder SDK provides the following features:</span></span>

* <span data-ttu-id="805ce-111">Acesso fácil ao conector da Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="805ce-111">Easy access to the Bot Framework connector.</span></span>
* <span data-ttu-id="805ce-112">Funcionalidade adicional para gerenciar o fluxo e o estado da conversa.</span><span class="sxs-lookup"><span data-stu-id="805ce-112">Additional functionality to manage conversation flow and state.</span></span>
* <span data-ttu-id="805ce-113">Maneiras simples de incorporar serviços cognitivos, como o processamento de linguagem natural (NLP).</span><span class="sxs-lookup"><span data-stu-id="805ce-113">Simple ways to incorporate cognitive services, such as natural language processing (NLP).</span></span>

<span data-ttu-id="805ce-114">Seu bot recebe mensagens do Teams usando a propriedade e envia respostas de mensagem única ou `Text` múltipla aos usuários.</span><span class="sxs-lookup"><span data-stu-id="805ce-114">Your bot receives messages from Teams using the `Text` property and it sends single or multiple message responses to the users.</span></span>

## <a name="receive-a-message"></a><span data-ttu-id="805ce-115">Receber uma mensagem</span><span class="sxs-lookup"><span data-stu-id="805ce-115">Receive a message</span></span>

<span data-ttu-id="805ce-116">Para receber uma mensagem de texto, use a propriedade `Text` do objeto `Activity`.</span><span class="sxs-lookup"><span data-stu-id="805ce-116">To receive a text message, use the `Text` property of the `Activity` object.</span></span> <span data-ttu-id="805ce-117">No manipulador de atividades do bot, alterne o contexto do objeto `Activity` para ler uma única solicitação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="805ce-117">In the bot's activity handler, use the turn context object's `Activity` to read a single message request.</span></span>

<span data-ttu-id="805ce-118">O código a seguir mostra um exemplo de recebimento de uma mensagem:</span><span class="sxs-lookup"><span data-stu-id="805ce-118">The following code shows an example of receiving a message:</span></span>

# <a name="c"></a>[<span data-ttu-id="805ce-119">C#</span><span class="sxs-lookup"><span data-stu-id="805ce-119">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescript"></a>[<span data-ttu-id="805ce-120">TypeScript</span><span class="sxs-lookup"><span data-stu-id="805ce-120">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="805ce-121">Python</span><span class="sxs-lookup"><span data-stu-id="805ce-121">Python</span></span>](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="json"></a>[<span data-ttu-id="805ce-122">JSON</span><span class="sxs-lookup"><span data-stu-id="805ce-122">JSON</span></span>](#tab/json)

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

## <a name="send-a-message"></a><span data-ttu-id="805ce-123">Enviar uma mensagem</span><span class="sxs-lookup"><span data-stu-id="805ce-123">Send a message</span></span>

<span data-ttu-id="805ce-124">Para enviar uma mensagem de texto, especifique a cadeia de caracteres que você deseja enviar como a atividade.</span><span class="sxs-lookup"><span data-stu-id="805ce-124">To send a text message, specify the string you want to send as the activity.</span></span> <span data-ttu-id="805ce-125">No manipulador de atividades do bot, use o método do objeto turn context `SendActivityAsync` para enviar uma única resposta de mensagem.</span><span class="sxs-lookup"><span data-stu-id="805ce-125">In the bot's activity handler, use the turn context object's `SendActivityAsync` method to send a single message response.</span></span> <span data-ttu-id="805ce-126">Use o método do `SendActivitiesAsync` objeto para enviar várias respostas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="805ce-126">Use the object's `SendActivitiesAsync` method to send multiple responses at once.</span></span>

<span data-ttu-id="805ce-127">O código a seguir mostra um exemplo de envio de uma mensagem quando um usuário é adicionado a uma conversa:</span><span class="sxs-lookup"><span data-stu-id="805ce-127">The following code shows an example of sending a message when a user is added to a conversation:</span></span>

# <a name="c"></a>[<span data-ttu-id="805ce-128">C#</span><span class="sxs-lookup"><span data-stu-id="805ce-128">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescript"></a>[<span data-ttu-id="805ce-129">TypeScript</span><span class="sxs-lookup"><span data-stu-id="805ce-129">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="805ce-130">Python</span><span class="sxs-lookup"><span data-stu-id="805ce-130">Python</span></span>](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="json"></a>[<span data-ttu-id="805ce-131">JSON</span><span class="sxs-lookup"><span data-stu-id="805ce-131">JSON</span></span>](#tab/json)

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
> <span data-ttu-id="805ce-132">A divisão de mensagens ocorre quando uma mensagem de texto e um anexo são enviados na mesma carga de atividade.</span><span class="sxs-lookup"><span data-stu-id="805ce-132">Message splitting occurs when a text message and an attachment are sent in the same activity payload.</span></span> <span data-ttu-id="805ce-133">Essa atividade é dividida em atividades separadas pelo Microsoft Teams, uma com apenas uma mensagem de texto e outra com um anexo.</span><span class="sxs-lookup"><span data-stu-id="805ce-133">This activity is split into separate activities by Microsoft Teams, one with just a text message and the other with an attachment.</span></span> <span data-ttu-id="805ce-134">À medida que a atividade é dividida, você não recebe a ID da mensagem em resposta, que é usada para atualizar [ou excluir](~/bots/how-to/update-and-delete-bot-messages.md) a mensagem proativamente.</span><span class="sxs-lookup"><span data-stu-id="805ce-134">As the activity is split, you do not receive the message ID in response, which is used to [update or delete](~/bots/how-to/update-and-delete-bot-messages.md) the message proactively.</span></span> <span data-ttu-id="805ce-135">É recomendável enviar atividades separadas em vez de depender da divisão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="805ce-135">It is recommended to send separate activities instead of depending on message splitting.</span></span>

<span data-ttu-id="805ce-136">As mensagens enviadas entre usuários e bots incluem dados de canal interno dentro da mensagem.</span><span class="sxs-lookup"><span data-stu-id="805ce-136">Messages sent between users and bots include internal channel data within the message.</span></span> <span data-ttu-id="805ce-137">Esses dados permitem que o bot se comunique corretamente nesse canal.</span><span class="sxs-lookup"><span data-stu-id="805ce-137">This data allows the bot to communicate properly on that channel.</span></span> <span data-ttu-id="805ce-138">O SDK do Construtor de Bots permite modificar a estrutura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="805ce-138">The Bot Builder SDK allows you to modify the message structure.</span></span>

## <a name="teams-channel-data"></a><span data-ttu-id="805ce-139">Dados do canal do Teams</span><span class="sxs-lookup"><span data-stu-id="805ce-139">Teams channel data</span></span>

<span data-ttu-id="805ce-140">O `channelData` objeto contém informações específicas do Teams e é uma fonte definitiva para IDs de equipe e canal.</span><span class="sxs-lookup"><span data-stu-id="805ce-140">The `channelData` object contains Teams-specific information and is a definitive source for team and channel IDs.</span></span> <span data-ttu-id="805ce-141">Opcionalmente, você pode armazenar em cache e usar essas IDs como chaves para armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="805ce-141">Optionally, you can cache and use these IDs as keys for local storage.</span></span> <span data-ttu-id="805ce-142">O no SDK retira informações importantes do objeto para `TeamsActivityHandler` `channelData` torná-lo facilmente acessível.</span><span class="sxs-lookup"><span data-stu-id="805ce-142">The `TeamsActivityHandler` in the SDK pulls out important information from the `channelData` object to make it easily accessible.</span></span> <span data-ttu-id="805ce-143">No entanto, você sempre pode acessar os dados originais do `turnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="805ce-143">However, you can always access the original data from the `turnContext` object.</span></span>

<span data-ttu-id="805ce-144">O `channelData` objeto não está incluído em mensagens em conversas pessoais, pois elas ocorrem fora de um canal.</span><span class="sxs-lookup"><span data-stu-id="805ce-144">The `channelData` object is not included in messages in personal conversations, as these take place outside of a channel.</span></span>

<span data-ttu-id="805ce-145">Um objeto `channelData` típico em uma atividade enviada ao bot contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="805ce-145">A typical `channelData` object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="805ce-146">`eventType`: Tipo de evento do Teams passado somente em casos de [eventos de modificação de canal.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="805ce-146">`eventType`: Teams event type passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="805ce-147">`tenant.id`: ID de locatário do Azure Active Directory passada em todos os contextos.</span><span class="sxs-lookup"><span data-stu-id="805ce-147">`tenant.id`: Azure Active Directory tenant ID passed in all contexts.</span></span>
* <span data-ttu-id="805ce-148">`team`: Passado somente em contextos de canal, não em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="805ce-148">`team`: Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="805ce-149">`id`: GUID para o canal.</span><span class="sxs-lookup"><span data-stu-id="805ce-149">`id`: GUID for the channel.</span></span>
  * <span data-ttu-id="805ce-150">`name`: Nome da equipe passada somente em casos de [eventos de renomear a equipe.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="805ce-150">`name`: Name of the team passed only in cases of [team rename events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="805ce-151">`channel`: Passado somente em contextos de canal quando o bot é mencionado ou para eventos em canais em equipes onde o bot foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="805ce-151">`channel`: Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added.</span></span>
  * <span data-ttu-id="805ce-152">`id`: GUID para o canal.</span><span class="sxs-lookup"><span data-stu-id="805ce-152">`id`: GUID for the channel.</span></span>
  * <span data-ttu-id="805ce-153">`name`: Nome do canal passado somente em casos de eventos [de modificação de canal.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="805ce-153">`name`: Channel name passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="805ce-154">`channelData.teamsTeamId`: Preterido.</span><span class="sxs-lookup"><span data-stu-id="805ce-154">`channelData.teamsTeamId`: Deprecated.</span></span> <span data-ttu-id="805ce-155">Essa propriedade só é incluída para compatibilidade com compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="805ce-155">This property is only included for backward compatibility.</span></span>
* <span data-ttu-id="805ce-156">`channelData.teamsChannelId`: Preterido.</span><span class="sxs-lookup"><span data-stu-id="805ce-156">`channelData.teamsChannelId`: Deprecated.</span></span> <span data-ttu-id="805ce-157">Essa propriedade só é incluída para compatibilidade com compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="805ce-157">This property is only included for backward compatibility.</span></span>

### <a name="example-channeldata-object-or-channelcreated-event"></a><span data-ttu-id="805ce-158">Exemplo de objeto channelData ou evento channelCreated</span><span class="sxs-lookup"><span data-stu-id="805ce-158">Example channelData object or channelCreated event</span></span>

<span data-ttu-id="805ce-159">O código a seguir mostra um exemplo do objeto channelData:</span><span class="sxs-lookup"><span data-stu-id="805ce-159">The following code shows an example of channelData object:</span></span>

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

<span data-ttu-id="805ce-160">As mensagens recebidas ou enviadas ao bot podem incluir diferentes tipos de conteúdo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="805ce-160">Messages received from or sent to your bot can include different types of message content.</span></span>

## <a name="message-content"></a><span data-ttu-id="805ce-161">Conteúdo da mensagem</span><span class="sxs-lookup"><span data-stu-id="805ce-161">Message content</span></span>

| <span data-ttu-id="805ce-162">Formatar</span><span class="sxs-lookup"><span data-stu-id="805ce-162">Format</span></span>    | <span data-ttu-id="805ce-163">De usuário para bot</span><span class="sxs-lookup"><span data-stu-id="805ce-163">From user to bot</span></span> | <span data-ttu-id="805ce-164">De bot para usuário</span><span class="sxs-lookup"><span data-stu-id="805ce-164">From bot to user</span></span> | <span data-ttu-id="805ce-165">Observações</span><span class="sxs-lookup"><span data-stu-id="805ce-165">Notes</span></span>                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| <span data-ttu-id="805ce-166">Rich text </span><span class="sxs-lookup"><span data-stu-id="805ce-166">Rich text</span></span> | <span data-ttu-id="805ce-167">✔</span><span class="sxs-lookup"><span data-stu-id="805ce-167">✔</span></span>                | <span data-ttu-id="805ce-168">✔</span><span class="sxs-lookup"><span data-stu-id="805ce-168">✔</span></span>                | <span data-ttu-id="805ce-169">Seu bot pode enviar rich text, pictures e cards.</span><span class="sxs-lookup"><span data-stu-id="805ce-169">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="805ce-170">Os usuários podem enviar texto e imagens rich para seu bot.</span><span class="sxs-lookup"><span data-stu-id="805ce-170">Users can send rich text and pictures to your bot.</span></span>                                                                                        |
| <span data-ttu-id="805ce-171">Imagens</span><span class="sxs-lookup"><span data-stu-id="805ce-171">Pictures</span></span>  | <span data-ttu-id="805ce-172">✔</span><span class="sxs-lookup"><span data-stu-id="805ce-172">✔</span></span>                | <span data-ttu-id="805ce-173">✔</span><span class="sxs-lookup"><span data-stu-id="805ce-173">✔</span></span>                | <span data-ttu-id="805ce-174">Máximo de 1024×1024 e 1 MB no formato PNG, JPEG ou GIF.</span><span class="sxs-lookup"><span data-stu-id="805ce-174">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="805ce-175">Gif animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="805ce-175">Animated GIF is not supported.</span></span>  |
| <span data-ttu-id="805ce-176">Cartões</span><span class="sxs-lookup"><span data-stu-id="805ce-176">Cards</span></span>     | <span data-ttu-id="805ce-177">✖</span><span class="sxs-lookup"><span data-stu-id="805ce-177">✖</span></span>                | <span data-ttu-id="805ce-178">✔</span><span class="sxs-lookup"><span data-stu-id="805ce-178">✔</span></span>                | <span data-ttu-id="805ce-179">Consulte a [referência de cartão do Teams](~/task-modules-and-cards/cards/cards-reference.md) para cartões com suporte.</span><span class="sxs-lookup"><span data-stu-id="805ce-179">See the [Teams card reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards.</span></span> |
| <span data-ttu-id="805ce-180">Emojis</span><span class="sxs-lookup"><span data-stu-id="805ce-180">Emojis</span></span>    | <span data-ttu-id="805ce-181">✖</span><span class="sxs-lookup"><span data-stu-id="805ce-181">✖</span></span>                | <span data-ttu-id="805ce-182">✔</span><span class="sxs-lookup"><span data-stu-id="805ce-182">✔</span></span>                | <span data-ttu-id="805ce-183">Atualmente, o Teams dá suporte a emojis por meio do UTF-16, como U+1F600 para face de riso.</span><span class="sxs-lookup"><span data-stu-id="805ce-183">Teams currently supports emojis through UTF-16, such as U+1F600 for grinning face.</span></span> |

<span data-ttu-id="805ce-184">Você também pode adicionar notificações à sua mensagem usando a `Notification.Alert` propriedade.</span><span class="sxs-lookup"><span data-stu-id="805ce-184">You can also add notifications to your message using the `Notification.Alert` property.</span></span>

## <a name="notifications-to-your-message"></a><span data-ttu-id="805ce-185">Notificações à sua mensagem</span><span class="sxs-lookup"><span data-stu-id="805ce-185">Notifications to your message</span></span>

<span data-ttu-id="805ce-186">As notificações alertam os usuários sobre novas tarefas, menções e comentários.</span><span class="sxs-lookup"><span data-stu-id="805ce-186">Notifications alert users about new tasks, mentions, and comments.</span></span> <span data-ttu-id="805ce-187">Esses alertas estão relacionados ao que os usuários estão trabalhando ou ao que devem observar inserindo um aviso no feed de atividades.</span><span class="sxs-lookup"><span data-stu-id="805ce-187">These alerts are related to what users are working on or what they must look at by inserting a notice into their activity feed.</span></span> <span data-ttu-id="805ce-188">Para que as notificações acionem de sua mensagem bot, de definir a propriedade `TeamsChannelData` objects `Notification.Alert` como *true*.</span><span class="sxs-lookup"><span data-stu-id="805ce-188">For notifications to trigger from your bot message, set the `TeamsChannelData` objects `Notification.Alert` property to *true*.</span></span> <span data-ttu-id="805ce-189">A ativação ou não de uma notificação depende das configurações do Teams do usuário individual e você não pode substituir essas configurações.</span><span class="sxs-lookup"><span data-stu-id="805ce-189">Whether or not a notification is raised depends on the individual user's Teams settings and you cannot override these settings.</span></span> <span data-ttu-id="805ce-190">O tipo de notificação é um banner ou um banner e um email.</span><span class="sxs-lookup"><span data-stu-id="805ce-190">The notification type is either a banner, or both a banner and an email.</span></span>

> [!NOTE]
> <span data-ttu-id="805ce-191">O **campo** Resumo exibe qualquer texto do usuário como uma mensagem de notificação no feed.</span><span class="sxs-lookup"><span data-stu-id="805ce-191">The **Summary** field displays any text from the user as a notification message in the feed.</span></span>

<span data-ttu-id="805ce-192">O código a seguir mostra um exemplo de adição de notificações à sua mensagem:</span><span class="sxs-lookup"><span data-stu-id="805ce-192">The following code shows an example of adding notifications to your message:</span></span>

# <a name="c"></a>[<span data-ttu-id="805ce-193">C#</span><span class="sxs-lookup"><span data-stu-id="805ce-193">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescript"></a>[<span data-ttu-id="805ce-194">TypeScript</span><span class="sxs-lookup"><span data-stu-id="805ce-194">TypeScript</span></span>](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="python"></a>[<span data-ttu-id="805ce-195">Python</span><span class="sxs-lookup"><span data-stu-id="805ce-195">Python</span></span>](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="json"></a>[<span data-ttu-id="805ce-196">JSON</span><span class="sxs-lookup"><span data-stu-id="805ce-196">JSON</span></span>](#tab/json)

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

<span data-ttu-id="805ce-197">Para aprimorar sua mensagem, você pode incluir imagens como anexos a essa mensagem.</span><span class="sxs-lookup"><span data-stu-id="805ce-197">To enhance your message, you can include pictures as attachments to that message.</span></span>

## <a name="picture-messages"></a><span data-ttu-id="805ce-198">Mensagens de imagem</span><span class="sxs-lookup"><span data-stu-id="805ce-198">Picture messages</span></span>

<span data-ttu-id="805ce-199">As imagens são enviadas adicionando anexos a uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="805ce-199">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="805ce-200">Para obter mais informações sobre anexos, consulte [Documentação da Estrutura de Bots.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments)</span><span class="sxs-lookup"><span data-stu-id="805ce-200">For more information on attachments, see [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).</span></span>

<span data-ttu-id="805ce-201">As imagens podem ter no máximo 1024×1024 e 1 MB no formato PNG, JPEG ou GIF.</span><span class="sxs-lookup"><span data-stu-id="805ce-201">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="805ce-202">Gif animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="805ce-202">Animated GIF is not supported.</span></span>

<span data-ttu-id="805ce-203">Especifique a altura e a largura de cada imagem usando XML.</span><span class="sxs-lookup"><span data-stu-id="805ce-203">Specify the height and width of each image by using XML.</span></span> <span data-ttu-id="805ce-204">Na marcação, o tamanho da imagem é padrão para 256×256.</span><span class="sxs-lookup"><span data-stu-id="805ce-204">In markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="805ce-205">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="805ce-205">For example:</span></span>

* <span data-ttu-id="805ce-206">Use: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` .</span><span class="sxs-lookup"><span data-stu-id="805ce-206">Use: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`.</span></span>
* <span data-ttu-id="805ce-207">Não use: `![Duck on a rock](http://aka.ms/Fo983c)` .</span><span class="sxs-lookup"><span data-stu-id="805ce-207">Do not use: `![Duck on a rock](http://aka.ms/Fo983c)`.</span></span>

<span data-ttu-id="805ce-208">Um bot de conversa pode incluir Cartões Adaptáveis que simplificam fluxos de trabalho de negócios.</span><span class="sxs-lookup"><span data-stu-id="805ce-208">A conversational bot can include Adaptive Cards that simplify business workflows.</span></span> <span data-ttu-id="805ce-209">Os Cartões Adaptáveis oferecem texto, fala, imagens, botões e campos de entrada personalizáveis.</span><span class="sxs-lookup"><span data-stu-id="805ce-209">Adaptive Cards offer rich customizable text, speech, images, buttons, and input fields.</span></span>

## <a name="adaptive-cards"></a><span data-ttu-id="805ce-210">Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="805ce-210">Adaptive Cards</span></span>

<span data-ttu-id="805ce-211">Cartões adaptáveis podem ser autorados em um bot e mostrados em vários aplicativos, como o Teams, seu site e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="805ce-211">Adaptive Cards can be authored in a bot and shown in multiple apps such as Teams, your website, and so on.</span></span> <span data-ttu-id="805ce-212">Para obter mais informações, consulte [Adaptive Cards](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span><span class="sxs-lookup"><span data-stu-id="805ce-212">For more information, see [Adaptive Cards](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>

<span data-ttu-id="805ce-213">O código a seguir mostra um exemplo de envio de um cartão adaptável simples:</span><span class="sxs-lookup"><span data-stu-id="805ce-213">The following code shows an example of sending a simple Adaptive Card:</span></span>

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

<span data-ttu-id="805ce-214">Para saber mais sobre cartões e cartões em bots, consulte [documentação de cartões.](~/task-modules-and-cards/what-are-cards.md)</span><span class="sxs-lookup"><span data-stu-id="805ce-214">To know more about cards and cards in bots, see [cards documentation](~/task-modules-and-cards/what-are-cards.md).</span></span>

## <a name="status-code-responses"></a><span data-ttu-id="805ce-215">Respostas de código de status</span><span class="sxs-lookup"><span data-stu-id="805ce-215">Status code responses</span></span>

<span data-ttu-id="805ce-216">A seguir estão os códigos de status e seus valores de código de erro e mensagem:</span><span class="sxs-lookup"><span data-stu-id="805ce-216">Following are the status codes and their error code and message values:</span></span>

| <span data-ttu-id="805ce-217">Código de status</span><span class="sxs-lookup"><span data-stu-id="805ce-217">Status code</span></span> | <span data-ttu-id="805ce-218">Valores de código de erro e mensagem</span><span class="sxs-lookup"><span data-stu-id="805ce-218">Error code and message values</span></span> | <span data-ttu-id="805ce-219">Descrição</span><span class="sxs-lookup"><span data-stu-id="805ce-219">Description</span></span> |
|----------------|-----------------|-----------------|
| <span data-ttu-id="805ce-220">403</span><span class="sxs-lookup"><span data-stu-id="805ce-220">403</span></span> | <span data-ttu-id="805ce-221">**Código**: `ConversationBlockedByUser`</span><span class="sxs-lookup"><span data-stu-id="805ce-221">**Code**: `ConversationBlockedByUser`</span></span> <br/> <span data-ttu-id="805ce-222">**Mensagem**: o usuário bloqueou a conversa com o bot.</span><span class="sxs-lookup"><span data-stu-id="805ce-222">**Message**: User blocked the conversation with the bot.</span></span> | <span data-ttu-id="805ce-223">O usuário bloqueou o bot no chat 1:1 ou em um canal por meio de configurações de moderação.</span><span class="sxs-lookup"><span data-stu-id="805ce-223">User blocked the bot in 1:1 chat or a channel through moderation settings.</span></span> |
| <span data-ttu-id="805ce-224">403</span><span class="sxs-lookup"><span data-stu-id="805ce-224">403</span></span> | <span data-ttu-id="805ce-225">**Código**: `BotNotInConversationRoster`</span><span class="sxs-lookup"><span data-stu-id="805ce-225">**Code**: `BotNotInConversationRoster`</span></span> <br/> <span data-ttu-id="805ce-226">**Mensagem**: o bot não faz parte da lista de conversas.</span><span class="sxs-lookup"><span data-stu-id="805ce-226">**Message**: The bot is not part of the conversation roster.</span></span> | <span data-ttu-id="805ce-227">O bot não faz parte da conversa.</span><span class="sxs-lookup"><span data-stu-id="805ce-227">The bot is not part of the conversation.</span></span> |
| <span data-ttu-id="805ce-228">403</span><span class="sxs-lookup"><span data-stu-id="805ce-228">403</span></span> | <span data-ttu-id="805ce-229">**Código**: `BotDisabledByAdmin`</span><span class="sxs-lookup"><span data-stu-id="805ce-229">**Code**: `BotDisabledByAdmin`</span></span> <br/> <span data-ttu-id="805ce-230">**Mensagem**: o administrador do locatário desabilitou esse bot.</span><span class="sxs-lookup"><span data-stu-id="805ce-230">**Message**: The tenant admin disabled this bot.</span></span> | <span data-ttu-id="805ce-231">O locatário bloqueou o bot.</span><span class="sxs-lookup"><span data-stu-id="805ce-231">Tenant blocked the bot.</span></span> |
| <span data-ttu-id="805ce-232">401</span><span class="sxs-lookup"><span data-stu-id="805ce-232">401</span></span> | <span data-ttu-id="805ce-233">**Código**: `BotNotRegistered`</span><span class="sxs-lookup"><span data-stu-id="805ce-233">**Code**: `BotNotRegistered`</span></span> <br/> <span data-ttu-id="805ce-234">**Mensagem**: nenhum registro encontrado para este bot.</span><span class="sxs-lookup"><span data-stu-id="805ce-234">**Message**: No registration found for this bot.</span></span> | <span data-ttu-id="805ce-235">O registro desse bot não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="805ce-235">The registration for this bot was not found.</span></span> |
| <span data-ttu-id="805ce-236">412</span><span class="sxs-lookup"><span data-stu-id="805ce-236">412</span></span> | <span data-ttu-id="805ce-237">**Código**: `PreconditionFailed`</span><span class="sxs-lookup"><span data-stu-id="805ce-237">**Code**: `PreconditionFailed`</span></span> <br/> <span data-ttu-id="805ce-238">**Mensagem**: Falha na pré-condição, tente novamente.</span><span class="sxs-lookup"><span data-stu-id="805ce-238">**Message**: Precondition failed, please try again.</span></span> | <span data-ttu-id="805ce-239">Uma pré-condição falhou em uma de nossas dependências devido a várias operações simultâneas na mesma conversa.</span><span class="sxs-lookup"><span data-stu-id="805ce-239">A precondition failed on one of our dependencies due to multiple concurrent operations on the same conversation.</span></span> |
| <span data-ttu-id="805ce-240">404</span><span class="sxs-lookup"><span data-stu-id="805ce-240">404</span></span> | <span data-ttu-id="805ce-241">**Código**: `ConversationNotFound`</span><span class="sxs-lookup"><span data-stu-id="805ce-241">**Code**: `ConversationNotFound`</span></span> <br/> <span data-ttu-id="805ce-242">**Mensagem**: Conversa não encontrada.</span><span class="sxs-lookup"><span data-stu-id="805ce-242">**Message**: Conversation not found.</span></span> | <span data-ttu-id="805ce-243">A conversa não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="805ce-243">The conversation was not found.</span></span> |
| <span data-ttu-id="805ce-244">413</span><span class="sxs-lookup"><span data-stu-id="805ce-244">413</span></span> | <span data-ttu-id="805ce-245">**Código**: `MessageSizeTooBig`</span><span class="sxs-lookup"><span data-stu-id="805ce-245">**Code**: `MessageSizeTooBig`</span></span> <br/> <span data-ttu-id="805ce-246">**Mensagem**: tamanho da mensagem muito grande.</span><span class="sxs-lookup"><span data-stu-id="805ce-246">**Message**: Message size too large.</span></span> | <span data-ttu-id="805ce-247">O tamanho da solicitação de entrada era muito grande.</span><span class="sxs-lookup"><span data-stu-id="805ce-247">The size on the incoming request was too large.</span></span> |
| <span data-ttu-id="805ce-248">429</span><span class="sxs-lookup"><span data-stu-id="805ce-248">429</span></span> | <span data-ttu-id="805ce-249">**Código**: `Throttled`</span><span class="sxs-lookup"><span data-stu-id="805ce-249">**Code**: `Throttled`</span></span> <br/> <span data-ttu-id="805ce-250">**Mensagem**: solicitações demais.</span><span class="sxs-lookup"><span data-stu-id="805ce-250">**Message**: Too many requests.</span></span> <span data-ttu-id="805ce-251">Também retorna quando repetir depois.</span><span class="sxs-lookup"><span data-stu-id="805ce-251">Also returns when to retry after.</span></span> | <span data-ttu-id="805ce-252">Muitas solicitações foram enviadas pelo bot.</span><span class="sxs-lookup"><span data-stu-id="805ce-252">Too many requests were sent by the bot.</span></span> <span data-ttu-id="805ce-253">Para obter mais informações, consulte [limite de taxa](~/bots/how-to/rate-limit.md).</span><span class="sxs-lookup"><span data-stu-id="805ce-253">For more information, see [rate limit](~/bots/how-to/rate-limit.md).</span></span> |

## <a name="code-sample"></a><span data-ttu-id="805ce-254">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="805ce-254">Code sample</span></span>

|<span data-ttu-id="805ce-255">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="805ce-255">Sample name</span></span> | <span data-ttu-id="805ce-256">Descrição</span><span class="sxs-lookup"><span data-stu-id="805ce-256">Description</span></span> | <span data-ttu-id="805ce-257">. NETCore</span><span class="sxs-lookup"><span data-stu-id="805ce-257">.NETCore</span></span> | <span data-ttu-id="805ce-258">Node.js</span><span class="sxs-lookup"><span data-stu-id="805ce-258">Node.js</span></span> | <span data-ttu-id="805ce-259">Python</span><span class="sxs-lookup"><span data-stu-id="805ce-259">Python</span></span> |
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="805ce-260">Bot de conversas do Teams</span><span class="sxs-lookup"><span data-stu-id="805ce-260">Teams conversation bot</span></span> | <span data-ttu-id="805ce-261">Manipulação de eventos de mensagens e conversas.</span><span class="sxs-lookup"><span data-stu-id="805ce-261">Messaging and conversation event handling.</span></span> |[<span data-ttu-id="805ce-262">View</span><span class="sxs-lookup"><span data-stu-id="805ce-262">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="805ce-263">View</span><span class="sxs-lookup"><span data-stu-id="805ce-263">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [<span data-ttu-id="805ce-264">View</span><span class="sxs-lookup"><span data-stu-id="805ce-264">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="see-also"></a><span data-ttu-id="805ce-265">Confira também</span><span class="sxs-lookup"><span data-stu-id="805ce-265">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="805ce-266">Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="805ce-266">Send proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="805ce-267">Inscreva-se em eventos de conversa</span><span class="sxs-lookup"><span data-stu-id="805ce-267">Subscribe to conversation events</span></span>](~/bots/how-to/conversations/subscribe-to-conversation-events.md)

## <a name="next-step"></a><span data-ttu-id="805ce-268">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="805ce-268">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="805ce-269">Menus de comando bot</span><span class="sxs-lookup"><span data-stu-id="805ce-269">Bot command menus</span></span>](~/bots/how-to/create-a-bot-commands-menu.md)
