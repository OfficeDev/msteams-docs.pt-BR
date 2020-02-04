---
title: Adicionar ações de cartão em um bot
description: Descreve as ações do cartão no Microsoft Teams e como usá-las em seus bots
keywords: ações de cartões de bots da equipe
ms.openlocfilehash: e0b050cde9adf5bd811d5d95ce1c6f1bf60546a1
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672658"
---
# <a name="card-actions"></a><span data-ttu-id="b4a3d-104">Ações de cartão</span><span class="sxs-lookup"><span data-stu-id="b4a3d-104">Card actions</span></span>

<span data-ttu-id="b4a3d-105">Os cartões usados por bots e extensões de mensagens no Microsoft Teams dão[`CardAction`](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards)suporte aos seguintes tipos de atividade ().</span><span class="sxs-lookup"><span data-stu-id="b4a3d-105">Cards used by bots and messaging extensions in Teams support the following activity ([`CardAction`](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards)) types.</span></span> <span data-ttu-id="b4a3d-106">Observe que essas ações diferem de `potentialActions` cartões conectores do Office 365 quando usadas de conectores.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-106">Note that these actions differ from `potentialActions` for Office 365 Connector cards when used from Connectors.</span></span>

| <span data-ttu-id="b4a3d-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="b4a3d-107">Type</span></span> | <span data-ttu-id="b4a3d-108">Action</span><span class="sxs-lookup"><span data-stu-id="b4a3d-108">Action</span></span> |
| --- | --- |
| `openUrl` | <span data-ttu-id="b4a3d-109">Abre uma URL no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-109">Opens a URL in the default browser.</span></span> |
| `messageBack` | <span data-ttu-id="b4a3d-110">Envia uma mensagem e uma carga para o bot (do usuário que clicou no botão ou tocou no cartão) e envia uma mensagem separada para o fluxo de chat.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-110">Sends a message and payload to the bot (from the user who clicked the button or tapped the card) and sends a separate message to the chat stream.</span></span> |
| `imBack`| <span data-ttu-id="b4a3d-111">Envia uma mensagem para o bot (do usuário que clicou no botão ou tocou no cartão).</span><span class="sxs-lookup"><span data-stu-id="b4a3d-111">Sends a message to the bot (from the user who clicked the button or tapped the card).</span></span> <span data-ttu-id="b4a3d-112">Esta mensagem (de usuário para bot) fica visível para todos os participantes da conversa.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-112">This message (from user to bot) is visible to all conversation participants.</span></span> |
| `invoke` | <span data-ttu-id="b4a3d-113">Envia uma mensagem e uma carga para o bot (do usuário que clicou no botão ou tocou no cartão).</span><span class="sxs-lookup"><span data-stu-id="b4a3d-113">Sends a message and payload to the bot (from the user who clicked the button or tapped the card).</span></span> <span data-ttu-id="b4a3d-114">Esta mensagem não está visível.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-114">This message is not visible.</span></span> |
| `signin` | <span data-ttu-id="b4a3d-115">Inicia o fluxo do OAuth, permitindo que os bots se conectem com serviços seguros.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-115">Initiates OAuth flow, allowing bots to connect with secure services.</span></span> |

> [!NOTE]
>* <span data-ttu-id="b4a3d-116">O Microsoft Teams `CardAction` não dá suporte a tipos não listados na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-116">Teams does not support `CardAction` types not listed in the preceding table.</span></span>
>* <span data-ttu-id="b4a3d-117">O Microsoft Teams não `potentialActions` oferece suporte à propriedade.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-117">Teams does not support the `potentialActions` property.</span></span>
>* <span data-ttu-id="b4a3d-118">As ações do cartão são diferentes das [ações sugeridas](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button) no serviço bot Framework/Azure bot.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-118">Card actions are different than [suggested actions](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button) in Bot Framework/Azure Bot Service.</span></span> <span data-ttu-id="b4a3d-119">As ações sugeridas não são suportadas no Microsoft Teams: se você deseja que os botões apareçam em uma mensagem do bot do Teams, use um cartão.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-119">Suggested actions are not supported in Microsoft Teams: if you want buttons to appear on a Teams bot message, use a card.</span></span>
>* <span data-ttu-id="b4a3d-120">Se você estiver usando uma ação de cartão como parte de uma extensão de mensagens, as ações não funcionarão até que o cartão seja enviado para o canal (eles não funcionarão enquanto o cartão estiver na caixa de mensagem de composição).</span><span class="sxs-lookup"><span data-stu-id="b4a3d-120">If you're using a card action as part of a messaging extension, the actions will be not work until the card is submitted to the channel (they will not work while the card is in the compose message box).</span></span>

<span data-ttu-id="b4a3d-121">O Microsoft Teams também oferece suporte a [ações de cartões adaptáveis](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), que são usados apenas por cartões adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-121">Teams also supports [Adaptive Cards actions](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), which are only used by Adaptive Cards.</span></span> <span data-ttu-id="b4a3d-122">Essas ações estão listadas em suas próprias seções no final desta referência.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-122">These actions are listed in their own section at the end of this reference.</span></span>

## <a name="openurl"></a><span data-ttu-id="b4a3d-123">openUrl</span><span class="sxs-lookup"><span data-stu-id="b4a3d-123">openUrl</span></span>

<span data-ttu-id="b4a3d-124">Este tipo de ação especifica uma URL a ser iniciada no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-124">This action type specifies a URL to launch in the default browser.</span></span> <span data-ttu-id="b4a3d-125">Observe que seu bot não recebe qualquer aviso em que botão foi clicado.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-125">Note that your bot does not receive any notice on which button was clicked.</span></span>

<span data-ttu-id="b4a3d-126">O `value` campo deve conter uma URL completa e corretamente formada.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-126">The `value` field must contain a full and properly formed URL.</span></span>

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a><span data-ttu-id="b4a3d-127">messageBack</span><span class="sxs-lookup"><span data-stu-id="b4a3d-127">messageBack</span></span>

<span data-ttu-id="b4a3d-128">Com `messageBack`o, você pode criar uma ação totalmente personalizada com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b4a3d-128">With `messageBack`, you can create a fully customized action with the following properties:</span></span>

| <span data-ttu-id="b4a3d-129">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b4a3d-129">Property</span></span> | <span data-ttu-id="b4a3d-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4a3d-130">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="b4a3d-131">Aparece como o rótulo do botão.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-131">Appears as the button label.</span></span> |
| `displayText` | <span data-ttu-id="b4a3d-132">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-132">Optional.</span></span> <span data-ttu-id="b4a3d-133">Ecoado pelo usuário para o fluxo de chat quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-133">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="b4a3d-134">Este texto *não* é enviado ao bot.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-134">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="b4a3d-135">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-135">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="b4a3d-136">Você pode codificar o contexto da ação, como identificadores exclusivos ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-136">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="b4a3d-137">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-137">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="b4a3d-138">Use esta propriedade para simplificar o desenvolvimento de bot: seu código pode verificar uma única propriedade de nível superior para a lógica de bot de expedição.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-138">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="b4a3d-139">A flexibilidade do `messageBack` significa que o código pode optar por não deixar uma mensagem de usuário visível no histórico simplesmente não usando `displayText`.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-139">The flexibility of `messageBack` means that your code can choose not to leave a visible user message in the history simply by not using `displayText`.</span></span>

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

<span data-ttu-id="b4a3d-140">A `value` propriedade pode ser uma cadeia de caracteres JSON serializada ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-140">The `value` property can be either a serialized JSON string or a JSON object.</span></span>

### <a name="inbound-message-example"></a><span data-ttu-id="b4a3d-141">Exemplo de mensagem de entrada</span><span class="sxs-lookup"><span data-stu-id="b4a3d-141">Inbound message example</span></span>

<span data-ttu-id="b4a3d-142">`replyToId`contém a ID da mensagem da qual a ação do cartão veio.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-142">`replyToId` contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="b4a3d-143">Use-o se você quiser atualizar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-143">Use it if you want to update the message.</span></span>

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

## <a name="imback"></a><span data-ttu-id="b4a3d-144">Failback</span><span class="sxs-lookup"><span data-stu-id="b4a3d-144">imBack</span></span>

<span data-ttu-id="b4a3d-145">Esta ação dispara uma mensagem de retorno ao bot, como se o usuário a tivesse digitado em uma mensagem de chat normal.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-145">This action triggers a return message to your bot, as if the user typed it in a normal chat message.</span></span> <span data-ttu-id="b4a3d-146">O usuário e todos os outros usuários se estiverem em um canal, verá essa resposta de botão.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-146">Your user, and all other users if in a channel, will see that button response.</span></span>

<span data-ttu-id="b4a3d-147">O `value` campo deve conter a cadeia de caracteres de texto ecoada no chat e, portanto, enviada de volta para o bot.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-147">The `value` field should contain the text string echoed in the chat and therefore sent back to the bot.</span></span> <span data-ttu-id="b4a3d-148">Este é o texto da mensagem que será processado no bot para executar a lógica desejada.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-148">This is the message text you will process in your bot to perform the desired logic.</span></span> <span data-ttu-id="b4a3d-149">Observação: Este campo é uma cadeia de caracteres simples – não há suporte para formatação ou caracteres ocultos.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-149">Note: this field is a simple string - there is no support for formatting or hidden characters.</span></span>

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a><span data-ttu-id="b4a3d-150">Ative</span><span class="sxs-lookup"><span data-stu-id="b4a3d-150">invoke</span></span>

<span data-ttu-id="b4a3d-151">A `invoke` ação é usada para invocar [módulos de tarefa](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span><span class="sxs-lookup"><span data-stu-id="b4a3d-151">The `invoke` action is used for invoking [task modules](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="b4a3d-152">A `invoke` ação contém três propriedades: `type`, `title`e `value`.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-152">The `invoke` action contains three properties: `type`, `title`, and `value`.</span></span> <span data-ttu-id="b4a3d-153">A `value` propriedade pode conter uma cadeia de caracteres, um objeto JSON em formato ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-153">The `value` property can contain a string, a stringified JSON object, or a JSON object.</span></span>

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

<span data-ttu-id="b4a3d-154">Quando um usuário clica no botão, seu bot receberá o `value` objeto com algumas informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-154">When a user clicks the button, your bot will receive the `value` object with some additional info.</span></span> <span data-ttu-id="b4a3d-155">Observe que o tipo de atividade será `invoke` em vez de `message` (`activity.Type == "invoke"`).</span><span class="sxs-lookup"><span data-stu-id="b4a3d-155">Please note that the activity type will be `invoke` instead of `message` (`activity.Type == "invoke"`).</span></span>

### <a name="example-invoke-button-definition-net"></a><span data-ttu-id="b4a3d-156">Exemplo: chamar definição de botão (.NET)</span><span class="sxs-lookup"><span data-stu-id="b4a3d-156">Example: Invoke button definition (.NET)</span></span>

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a><span data-ttu-id="b4a3d-157">Exemplo: mensagem de invocação de entrada</span><span class="sxs-lookup"><span data-stu-id="b4a3d-157">Example: Incoming invoke message</span></span>

<span data-ttu-id="b4a3d-158">A propriedade de nível `replyToId` superior contém a ID da mensagem da qual a ação do cartão veio.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-158">The top-level `replyToId` property contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="b4a3d-159">Use-o se você quiser atualizar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-159">Use it if you want to update the message.</span></span>

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

## <a name="signin"></a><span data-ttu-id="b4a3d-160">SignIn</span><span class="sxs-lookup"><span data-stu-id="b4a3d-160">signin</span></span>

<span data-ttu-id="b4a3d-161">Inicia um fluxo OAuth, permitindo que os bots se conectem com serviços seguros, conforme descrito em mais detalhes aqui: [fluxo de autenticação em bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="b4a3d-161">Initiates an OAuth flow, allowing bots to connect with secure services, as described in more detail here: [Authentication flow in bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

## <a name="adaptive-cards-actions"></a><span data-ttu-id="b4a3d-162">Ações de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="b4a3d-162">Adaptive Cards actions</span></span>

<span data-ttu-id="b4a3d-163">Os cartões adaptáveis dão suporte a três tipos de ação:</span><span class="sxs-lookup"><span data-stu-id="b4a3d-163">Adaptive Cards support three action types:</span></span>

* [<span data-ttu-id="b4a3d-164">Ação. OpenUrl</span><span class="sxs-lookup"><span data-stu-id="b4a3d-164">Action.OpenUrl</span></span>](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [<span data-ttu-id="b4a3d-165">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="b4a3d-165">Action.Submit</span></span>](http://adaptivecards.io/explorer/Action.Submit.html)
* [<span data-ttu-id="b4a3d-166">Cartão Action.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-166">Action.ShowCard</span></span>](http://adaptivecards.io/explorer/Action.ShowCard.html)

<span data-ttu-id="b4a3d-167">Além das ações mencionadas acima, você pode modificar a `Action.Submit` carga de cartão adaptável para dar suporte a ações da estrutura de bot `msteams` existentes usando uma `data` Propriedade no `Action.Submit`objeto of.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-167">In addition to the actions mentioned above, you can modify the Adaptive Card `Action.Submit` payload to support existing Bot Framework actions using a `msteams` property in the `data` object of `Action.Submit`.</span></span> <span data-ttu-id="b4a3d-168">As seções abaixo detalham como usar ações da estrutura de bot existentes com cartões adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-168">The below sections detail how to use existing Bot Framework actions with Adaptive Cards.</span></span>

### <a name="adaptive-cards-with-messageback-action"></a><span data-ttu-id="b4a3d-169">Cartões adaptáveis com ação messageBack</span><span class="sxs-lookup"><span data-stu-id="b4a3d-169">Adaptive Cards with messageBack action</span></span>

<span data-ttu-id="b4a3d-170">Para incluir uma `messageBack` ação com um cartão adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-170">To include a `messageBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="b4a3d-171">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-171">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="b4a3d-172">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b4a3d-172">Property</span></span> | <span data-ttu-id="b4a3d-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4a3d-173">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="b4a3d-174">Definido como`messageBack`</span><span class="sxs-lookup"><span data-stu-id="b4a3d-174">Set to `messageBack`</span></span> |
| `displayText` | <span data-ttu-id="b4a3d-175">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-175">Optional.</span></span> <span data-ttu-id="b4a3d-176">Ecoado pelo usuário para o fluxo de chat quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-176">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="b4a3d-177">Este texto *não* é enviado ao bot.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-177">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="b4a3d-178">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-178">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="b4a3d-179">Você pode codificar o contexto da ação, como identificadores exclusivos ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-179">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="b4a3d-180">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-180">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="b4a3d-181">Use esta propriedade para simplificar o desenvolvimento de bot: seu código pode verificar uma única propriedade de nível superior para a lógica de bot de expedição.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-181">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

#### <a name="example"></a><span data-ttu-id="b4a3d-182">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4a3d-182">Example</span></span>

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

### <a name="adaptive-cards-with-imback-action"></a><span data-ttu-id="b4a3d-183">Cartões adaptáveis com ação de inversão</span><span class="sxs-lookup"><span data-stu-id="b4a3d-183">Adaptive Cards with imBack action</span></span>

<span data-ttu-id="b4a3d-184">Para incluir uma `imBack` ação com um cartão adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-184">To include a `imBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="b4a3d-185">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-185">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="b4a3d-186">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b4a3d-186">Property</span></span> | <span data-ttu-id="b4a3d-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4a3d-187">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="b4a3d-188">Definido como`imBack`</span><span class="sxs-lookup"><span data-stu-id="b4a3d-188">Set to `imBack`</span></span> |
| `value` | <span data-ttu-id="b4a3d-189">Cadeia de caracteres que precisa ser ecoada de volta no chat</span><span class="sxs-lookup"><span data-stu-id="b4a3d-189">String that needs to be echoed back in the chat</span></span> |

#### <a name="example"></a><span data-ttu-id="b4a3d-190">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4a3d-190">Example</span></span>

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

### <a name="adaptive-cards-with-signin-action"></a><span data-ttu-id="b4a3d-191">Cartões adaptáveis com ação de entrada</span><span class="sxs-lookup"><span data-stu-id="b4a3d-191">Adaptive Cards with signin action</span></span>

<span data-ttu-id="b4a3d-192">Para incluir uma `signin` ação com um cartão adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-192">To include a `signin` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="b4a3d-193">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="b4a3d-193">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="b4a3d-194">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b4a3d-194">Property</span></span> | <span data-ttu-id="b4a3d-195">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4a3d-195">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="b4a3d-196">Definido como`signin`</span><span class="sxs-lookup"><span data-stu-id="b4a3d-196">Set to `signin`</span></span> |
| `value` | <span data-ttu-id="b4a3d-197">Defina como a URL para a qual você deseja redirecionar</span><span class="sxs-lookup"><span data-stu-id="b4a3d-197">Set to the URL that you want to redirect to</span></span>  |

#### <a name="example"></a><span data-ttu-id="b4a3d-198">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4a3d-198">Example</span></span>

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
