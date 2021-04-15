---
title: Adicionar ações de cartão em um bot
description: Descreve ações de cartão no Microsoft Teams e como usá-las em seus bots
ms.topic: conceptual
keywords: ações de cartões de bots do teams
ms.openlocfilehash: f02e195f619fdfa2ebbc4b2ef00669a1cb5b38f6
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696021"
---
# <a name="card-actions"></a><span data-ttu-id="756de-104">Ações de cartão</span><span class="sxs-lookup"><span data-stu-id="756de-104">Card actions</span></span>

<span data-ttu-id="756de-105">Os cartões usados por bots e extensões de mensagens no Teams suportam os seguintes tipos de atividade ( [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) )</span><span class="sxs-lookup"><span data-stu-id="756de-105">Cards used by bots and messaging extensions in Teams support the following activity ([`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards)) types.</span></span> <span data-ttu-id="756de-106">Observe que essas ações diferem dos cartões do `potentialActions` Conector do Office 365 quando usados de Conectores.</span><span class="sxs-lookup"><span data-stu-id="756de-106">Note that these actions differ from `potentialActions` for Office 365 Connector cards when used from Connectors.</span></span>

| <span data-ttu-id="756de-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="756de-107">Type</span></span> | <span data-ttu-id="756de-108">Action</span><span class="sxs-lookup"><span data-stu-id="756de-108">Action</span></span> |
| --- | --- |
| `openUrl` | <span data-ttu-id="756de-109">Abre uma URL no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="756de-109">Opens a URL in the default browser.</span></span> |
| `messageBack` | <span data-ttu-id="756de-110">Envia uma mensagem e uma carga para o bot (do usuário que clicou no botão ou tocou no cartão) e envia uma mensagem separada para o fluxo de chat.</span><span class="sxs-lookup"><span data-stu-id="756de-110">Sends a message and payload to the bot (from the user who clicked the button or tapped the card) and sends a separate message to the chat stream.</span></span> |
| `imBack`| <span data-ttu-id="756de-111">Envia uma mensagem para o bot (do usuário que clicou no botão ou tocou no cartão).</span><span class="sxs-lookup"><span data-stu-id="756de-111">Sends a message to the bot (from the user who clicked the button or tapped the card).</span></span> <span data-ttu-id="756de-112">Essa mensagem (de usuário para bot) é visível para todos os participantes da conversa.</span><span class="sxs-lookup"><span data-stu-id="756de-112">This message (from user to bot) is visible to all conversation participants.</span></span> |
| `invoke` | <span data-ttu-id="756de-113">Envia uma mensagem e uma carga para o bot (do usuário que clicou no botão ou tocou no cartão).</span><span class="sxs-lookup"><span data-stu-id="756de-113">Sends a message and payload to the bot (from the user who clicked the button or tapped the card).</span></span> <span data-ttu-id="756de-114">Esta mensagem não está visível.</span><span class="sxs-lookup"><span data-stu-id="756de-114">This message is not visible.</span></span> |
| `signin` | <span data-ttu-id="756de-115">Inicia o fluxo OAuth, permitindo que os bots se conectem com serviços seguros.</span><span class="sxs-lookup"><span data-stu-id="756de-115">Initiates OAuth flow, allowing bots to connect with secure services.</span></span> |

> [!NOTE]
>* <span data-ttu-id="756de-116">O Teams não dá suporte `CardAction` a tipos não listados na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="756de-116">Teams does not support `CardAction` types not listed in the preceding table.</span></span>
>* <span data-ttu-id="756de-117">O Teams não dá suporte à `potentialActions` propriedade.</span><span class="sxs-lookup"><span data-stu-id="756de-117">Teams does not support the `potentialActions` property.</span></span>
>* <span data-ttu-id="756de-118">As ações de cartão são diferentes [das ações sugeridas](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) no Serviço bot framework/bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="756de-118">Card actions are different than [suggested actions](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework/Azure Bot Service.</span></span> <span data-ttu-id="756de-119">Ações sugeridas não são suportadas no Microsoft Teams: se você quiser que os botões apareçam em uma mensagem de bot do Teams, use um cartão.</span><span class="sxs-lookup"><span data-stu-id="756de-119">Suggested actions are not supported in Microsoft Teams: if you want buttons to appear on a Teams bot message, use a card.</span></span>
>* <span data-ttu-id="756de-120">Se você estiver usando uma ação de cartão como parte de uma extensão de mensagens, as ações não funcionarão até que o cartão seja enviado ao canal (eles não funcionarão enquanto o cartão estiver na caixa de mensagem de redação).</span><span class="sxs-lookup"><span data-stu-id="756de-120">If you're using a card action as part of a messaging extension, the actions will be not work until the card is submitted to the channel (they will not work while the card is in the compose message box).</span></span>

<span data-ttu-id="756de-121">O Teams também dá [suporte a ações de Cartões Adaptáveis](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), que são usadas apenas por Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="756de-121">Teams also supports [Adaptive Cards actions](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), which are only used by Adaptive Cards.</span></span> <span data-ttu-id="756de-122">Essas ações são listadas em sua própria seção no final desta referência.</span><span class="sxs-lookup"><span data-stu-id="756de-122">These actions are listed in their own section at the end of this reference.</span></span>

## <a name="openurl"></a><span data-ttu-id="756de-123">openUrl</span><span class="sxs-lookup"><span data-stu-id="756de-123">openUrl</span></span>

<span data-ttu-id="756de-124">Esse tipo de ação especifica uma URL a ser lançada no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="756de-124">This action type specifies a URL to launch in the default browser.</span></span> <span data-ttu-id="756de-125">Observe que o bot não recebe nenhum aviso sobre qual botão foi clicado.</span><span class="sxs-lookup"><span data-stu-id="756de-125">Note that your bot does not receive any notice on which button was clicked.</span></span>

<span data-ttu-id="756de-126">O `value` campo deve conter uma URL completa e corretamente formada.</span><span class="sxs-lookup"><span data-stu-id="756de-126">The `value` field must contain a full and properly formed URL.</span></span>

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a><span data-ttu-id="756de-127">messageBack</span><span class="sxs-lookup"><span data-stu-id="756de-127">messageBack</span></span>

<span data-ttu-id="756de-128">Com `messageBack` , você pode criar uma ação totalmente personalizada com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="756de-128">With `messageBack`, you can create a fully customized action with the following properties:</span></span>

| <span data-ttu-id="756de-129">Propriedade</span><span class="sxs-lookup"><span data-stu-id="756de-129">Property</span></span> | <span data-ttu-id="756de-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="756de-130">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="756de-131">Aparece como o rótulo do botão.</span><span class="sxs-lookup"><span data-stu-id="756de-131">Appears as the button label.</span></span> |
| `displayText` | <span data-ttu-id="756de-132">Opcional.</span><span class="sxs-lookup"><span data-stu-id="756de-132">Optional.</span></span> <span data-ttu-id="756de-133">Ecoado pelo usuário no fluxo de chat quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="756de-133">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="756de-134">Este texto não *é* enviado para seu bot.</span><span class="sxs-lookup"><span data-stu-id="756de-134">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="756de-135">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="756de-135">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="756de-136">Você pode codificar contexto para a ação, como identificadores exclusivos ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="756de-136">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="756de-137">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="756de-137">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="756de-138">Use essa propriedade para simplificar o desenvolvimento de bots: seu código pode verificar uma única propriedade de nível superior para despachar a lógica do bot.</span><span class="sxs-lookup"><span data-stu-id="756de-138">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="756de-139">A flexibilidade de meios que seu código pode optar por não deixar uma mensagem de usuário visível no `messageBack` histórico simplesmente não usando `displayText` .</span><span class="sxs-lookup"><span data-stu-id="756de-139">The flexibility of `messageBack` means that your code can choose not to leave a visible user message in the history simply by not using `displayText`.</span></span>

```json
{
  "buttons": [
    {
    "type": "messageBack",
    "title": "My MessageBack button",
    "displayText": "I clicked this button",
    "text": "User just clicked the MessageBack button",
    "value": "{\"property\": \"propertyValue\" }"
    }
  ]
}
```

<span data-ttu-id="756de-140">A `value` propriedade pode ser uma cadeia de caracteres JSON serializada ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="756de-140">The `value` property can be either a serialized JSON string or a JSON object.</span></span>

### <a name="inbound-message-example"></a><span data-ttu-id="756de-141">Exemplo de mensagem de entrada</span><span class="sxs-lookup"><span data-stu-id="756de-141">Inbound message example</span></span>

<span data-ttu-id="756de-142">`replyToId` contém a ID da mensagem de onde veio a ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="756de-142">`replyToId` contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="756de-143">Use-o se quiser atualizar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="756de-143">Use it if you want to update the message.</span></span>

```json
{
   "text":"User just clicked the MessageBack button",
   "value":{
      "property":"propertyValue"
   },
   "type":"message",
   "timestamp":"2017-06-22T22:38:47.407Z",
   "id":"f:5261769396935243054",
   "channelId":"msteams",
   "serviceUrl":"https://smba.trafficmanager.net/amer-client-ss.msg/",
   "from":{
      "id":"29:102jd210jd010icsoaeclaejcoa9ue09u",
      "name":"John Smith"
   },
   "conversation":{
      "id":"19:malejcou081i20ojmlcau0@thread.skype;messageid=1498171086622"
   },
   "recipient":{
      "id":"28:76096e45-119f-4736-859c-6dfff54395f7",
      "name":"MyBot"
   },
   "entities":[
      {
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "America/Los_Angeles",
        "type": "clientInfo" 
      }
   ],
   "channelData":{
      "channel":{
         "id":"19:malejcou081i20ojmlcau0@thread.skype"
      },
      "team":{
         "id":"19:12d021jdoijsaeoaue0u@thread.skype"
      },
      "tenant":{
         "id":"bec8e231-67ad-484e-87f4-3e5438390a77"
      }
   },
        "replyToId": "1575667808184",
}
```

## <a name="imback"></a><span data-ttu-id="756de-144">imBack</span><span class="sxs-lookup"><span data-stu-id="756de-144">imBack</span></span>

<span data-ttu-id="756de-145">Essa ação aciona uma mensagem de retorno para seu bot, como se o usuário a digitou em uma mensagem de chat normal.</span><span class="sxs-lookup"><span data-stu-id="756de-145">This action triggers a return message to your bot, as if the user typed it in a normal chat message.</span></span> <span data-ttu-id="756de-146">Seu usuário e todos os outros usuários, se em um canal, verão a resposta do botão.</span><span class="sxs-lookup"><span data-stu-id="756de-146">Your user, and all other users if in a channel, will see that button response.</span></span>

<span data-ttu-id="756de-147">O campo deve conter a cadeia de caracteres de texto `value` ecoada no chat e, portanto, enviada de volta para o bot.</span><span class="sxs-lookup"><span data-stu-id="756de-147">The `value` field should contain the text string echoed in the chat and therefore sent back to the bot.</span></span> <span data-ttu-id="756de-148">Este é o texto da mensagem que você processará em seu bot para executar a lógica desejada.</span><span class="sxs-lookup"><span data-stu-id="756de-148">This is the message text you will process in your bot to perform the desired logic.</span></span> <span data-ttu-id="756de-149">Observação: este campo é uma cadeia de caracteres simples - não há suporte para formatação ou caracteres ocultos.</span><span class="sxs-lookup"><span data-stu-id="756de-149">Note: this field is a simple string - there is no support for formatting or hidden characters.</span></span>

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a><span data-ttu-id="756de-150">invoke</span><span class="sxs-lookup"><span data-stu-id="756de-150">invoke</span></span>

<span data-ttu-id="756de-151">A `invoke` ação é usada para invocar [módulos de tarefa](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span><span class="sxs-lookup"><span data-stu-id="756de-151">The `invoke` action is used for invoking [task modules](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="756de-152">A `invoke` ação contém três propriedades: , e `type` `title` `value` .</span><span class="sxs-lookup"><span data-stu-id="756de-152">The `invoke` action contains three properties: `type`, `title`, and `value`.</span></span> <span data-ttu-id="756de-153">A `value` propriedade pode conter uma cadeia de caracteres, um objeto JSON stringified ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="756de-153">The `value` property can contain a string, a stringified JSON object, or a JSON object.</span></span>

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

<span data-ttu-id="756de-154">Quando um usuário clica no botão, seu bot receberá o `value` objeto com algumas informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="756de-154">When a user clicks the button, your bot will receive the `value` object with some additional info.</span></span> <span data-ttu-id="756de-155">Observe que o tipo de atividade será `invoke` em vez de ( `message` `activity.Type == "invoke"` ).</span><span class="sxs-lookup"><span data-stu-id="756de-155">Please note that the activity type will be `invoke` instead of `message` (`activity.Type == "invoke"`).</span></span>

### <a name="example-invoke-button-definition-net"></a><span data-ttu-id="756de-156">Exemplo: Invocar definição de botão (.NET)</span><span class="sxs-lookup"><span data-stu-id="756de-156">Example: Invoke button definition (.NET)</span></span>

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a><span data-ttu-id="756de-157">Exemplo: Mensagem de invocação de entrada</span><span class="sxs-lookup"><span data-stu-id="756de-157">Example: Incoming invoke message</span></span>

<span data-ttu-id="756de-158">A propriedade de nível superior contém a ID da mensagem de onde a `replyToId` ação do cartão veio.</span><span class="sxs-lookup"><span data-stu-id="756de-158">The top-level `replyToId` property contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="756de-159">Use-o se quiser atualizar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="756de-159">Use it if you want to update the message.</span></span>

```json
{
    "type": "invoke",
    "value": {
        "option": "opt1"
    },
    "timestamp": "2017-02-10T04:11:19.614Z",
    "localTimestamp": "2017-02-09T21:11:19.614-07:00",
    "id": "f:6894910862892785420",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1Eniglq0-uVL83xNB9GU6w_G5a4SZF0gcJLprZzhtEbel21G_5h-
    NgoprRw45mP0AXUIZVeqrsIHSYV4ntgfVJQ",
        "name": "John Doe"
    },
    "conversation": {
        "id": "19:97b1ec61-45bf-453c-9059-6e8984e0cef4_8d88f59b-ae61-4300-bec0-caace7d28446@unq.gbl.spaces"
    },
    "recipient": {
        "id": "28:8d88f59b-ae61-4300-bec0-caace7d28446",
        "name": "MyBot"
    },
    "entities": [
        {
            "locale": "en-US",
            "country": "US",
            "platform": "Web",
            "type": "clientInfo"
        }
    ],
    "channelData": {
        "channel": {
            "id": "19:dc5ba12695be4eb7bf457cad6b4709eb@thread.skype"
        },
        "team": {
            "id": "19:712c61d0ef384e5fa681ba90ca943398@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184"
}
```

## <a name="signin"></a><span data-ttu-id="756de-160">signin</span><span class="sxs-lookup"><span data-stu-id="756de-160">signin</span></span>

<span data-ttu-id="756de-161">Inicia um fluxo OAuth, permitindo que os bots se conectem com serviços seguros, conforme descrito em mais detalhes aqui: Fluxo de autenticação [em bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="756de-161">Initiates an OAuth flow, allowing bots to connect with secure services, as described in more detail here: [Authentication flow in bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

## <a name="adaptive-cards-actions"></a><span data-ttu-id="756de-162">Ações de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="756de-162">Adaptive Cards actions</span></span>

<span data-ttu-id="756de-163">Os Cartões Adaptáveis suportam três tipos de ação:</span><span class="sxs-lookup"><span data-stu-id="756de-163">Adaptive Cards support three action types:</span></span>

* [<span data-ttu-id="756de-164">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="756de-164">Action.OpenUrl</span></span>](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [<span data-ttu-id="756de-165">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="756de-165">Action.Submit</span></span>](http://adaptivecards.io/explorer/Action.Submit.html)
* [<span data-ttu-id="756de-166">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="756de-166">Action.ShowCard</span></span>](http://adaptivecards.io/explorer/Action.ShowCard.html)

<span data-ttu-id="756de-167">Além das ações mencionadas acima, você pode modificar a carga do Cartão Adaptável para dar suporte a ações existentes da Estrutura de Bot usando uma propriedade no `Action.Submit` `msteams` objeto de `data` `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="756de-167">In addition to the actions mentioned above, you can modify the Adaptive Card `Action.Submit` payload to support existing Bot Framework actions using a `msteams` property in the `data` object of `Action.Submit`.</span></span> <span data-ttu-id="756de-168">As seções a seguir detalham como usar ações da Estrutura de Bot existentes com Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="756de-168">The below sections detail how to use existing Bot Framework actions with Adaptive Cards.</span></span>

> [!NOTE]
> <span data-ttu-id="756de-169">Adicionar `msteams` aos dados, com uma ação da Estrutura de Bot, não funciona com um módulo de tarefa cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="756de-169">Adding `msteams` to data, with a Bot Framework action, does not work with an Adaptive Card task module.</span></span>

### <a name="adaptive-cards-with-messageback-action"></a><span data-ttu-id="756de-170">Cartões Adaptáveis com ação messageBack</span><span class="sxs-lookup"><span data-stu-id="756de-170">Adaptive Cards with messageBack action</span></span>

<span data-ttu-id="756de-171">Para incluir uma `messageBack` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="756de-171">To include a `messageBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="756de-172">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="756de-172">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="756de-173">Propriedade</span><span class="sxs-lookup"><span data-stu-id="756de-173">Property</span></span> | <span data-ttu-id="756de-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="756de-174">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="756de-175">Definir como `messageBack`</span><span class="sxs-lookup"><span data-stu-id="756de-175">Set to `messageBack`</span></span> |
| `displayText` | <span data-ttu-id="756de-176">Opcional.</span><span class="sxs-lookup"><span data-stu-id="756de-176">Optional.</span></span> <span data-ttu-id="756de-177">Ecoado pelo usuário no fluxo de chat quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="756de-177">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="756de-178">Este texto não *é* enviado para seu bot.</span><span class="sxs-lookup"><span data-stu-id="756de-178">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="756de-179">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="756de-179">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="756de-180">Você pode codificar contexto para a ação, como identificadores exclusivos ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="756de-180">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="756de-181">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="756de-181">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="756de-182">Use essa propriedade para simplificar o desenvolvimento de bots: seu código pode verificar uma única propriedade de nível superior para despachar a lógica do bot.</span><span class="sxs-lookup"><span data-stu-id="756de-182">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

#### <a name="example"></a><span data-ttu-id="756de-183">Exemplo</span><span class="sxs-lookup"><span data-stu-id="756de-183">Example</span></span>

```json
{
  "type": "Action.Submit",
  "title": "Click me for messageBack",
  "data": {
    "msteams": {
        "type": "messageBack",
        "displayText": "I clicked this button",
        "text": "text to bots",
        "value": "{\"bfKey\": \"bfVal\", \"conflictKey\": \"from value\"}"
    }
  }
}
```

### <a name="adaptive-cards-with-imback-action"></a><span data-ttu-id="756de-184">Cartões Adaptáveis com ação imBack</span><span class="sxs-lookup"><span data-stu-id="756de-184">Adaptive Cards with imBack action</span></span>

<span data-ttu-id="756de-185">Para incluir uma `imBack` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="756de-185">To include a `imBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="756de-186">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="756de-186">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="756de-187">Propriedade</span><span class="sxs-lookup"><span data-stu-id="756de-187">Property</span></span> | <span data-ttu-id="756de-188">Descrição</span><span class="sxs-lookup"><span data-stu-id="756de-188">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="756de-189">Definir como `imBack`</span><span class="sxs-lookup"><span data-stu-id="756de-189">Set to `imBack`</span></span> |
| `value` | <span data-ttu-id="756de-190">Cadeia de caracteres que precisa ser ecoada no chat</span><span class="sxs-lookup"><span data-stu-id="756de-190">String that needs to be echoed back in the chat</span></span> |

#### <a name="example"></a><span data-ttu-id="756de-191">Exemplo</span><span class="sxs-lookup"><span data-stu-id="756de-191">Example</span></span>

```json
{
  "type": "Action.Submit",
  "title": "Click me for imBack",
  "data": {
    "msteams": {
        "type": "imBack",
        "value": "Text to reply in chat"
    }
  }
}
```

### <a name="adaptive-cards-with-signin-action"></a><span data-ttu-id="756de-192">Cartões Adaptáveis com ação de signin</span><span class="sxs-lookup"><span data-stu-id="756de-192">Adaptive Cards with signin action</span></span>

<span data-ttu-id="756de-193">Para incluir uma `signin` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="756de-193">To include a `signin` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="756de-194">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="756de-194">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="756de-195">Propriedade</span><span class="sxs-lookup"><span data-stu-id="756de-195">Property</span></span> | <span data-ttu-id="756de-196">Descrição</span><span class="sxs-lookup"><span data-stu-id="756de-196">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="756de-197">Definir como `signin`</span><span class="sxs-lookup"><span data-stu-id="756de-197">Set to `signin`</span></span> |
| `value` | <span data-ttu-id="756de-198">Definir para a URL para a que você deseja redirecionar</span><span class="sxs-lookup"><span data-stu-id="756de-198">Set to the URL that you want to redirect to</span></span>  |

#### <a name="example"></a><span data-ttu-id="756de-199">Exemplo</span><span class="sxs-lookup"><span data-stu-id="756de-199">Example</span></span>

```json
{
  "type": "Action.Submit",
  "title": "Click me for signin",
  "data": {
    "msteams": {
        "type": "signin",
        "value": "https://signin.com"
    }
  }
}
```

### <a name="adaptive-cards-with-invoke-action"></a><span data-ttu-id="756de-200">Cartões Adaptáveis com ação de invocação</span><span class="sxs-lookup"><span data-stu-id="756de-200">Adaptive Cards with invoke action</span></span>
 
<span data-ttu-id="756de-201">Para incluir uma `invoke` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="756de-201">To include a `invoke` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="756de-202">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="756de-202">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="756de-203">Propriedade</span><span class="sxs-lookup"><span data-stu-id="756de-203">Property</span></span> | <span data-ttu-id="756de-204">Descrição</span><span class="sxs-lookup"><span data-stu-id="756de-204">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="756de-205">Definir como `task/fetch`</span><span class="sxs-lookup"><span data-stu-id="756de-205">Set to `task/fetch`</span></span> |
| `data` | <span data-ttu-id="756de-206">Definir o valor</span><span class="sxs-lookup"><span data-stu-id="756de-206">Set the value</span></span>  |

#### <a name="example"></a><span data-ttu-id="756de-207">Exemplo</span><span class="sxs-lookup"><span data-stu-id="756de-207">Example</span></span>

```json
{
  "type": "Action.Submit",
  "title": "submit"
  "data": {
    "msteams": {
        "type": "task/fetch"
    }
  }
}
```

#### <a name="example-2-with-additional-payload-data"></a><span data-ttu-id="756de-208">Exemplo 2 (com dados de carga adicionais)</span><span class="sxs-lookup"><span data-stu-id="756de-208">Example 2 (with additional payload data)</span></span>

```json
{
  "type": "Action.Submit",
  "title": "submit"
  "data": {
    "msteams": {
        "type": "task/fetch"
    },
    "Value1": "some value"
  }
}
```
