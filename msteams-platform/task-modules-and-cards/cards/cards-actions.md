---
title: Adicionar ações de cartão em um bot
description: Descreve ações de cartão em Microsoft Teams e como usá-las em seus bots
localization_priority: Normal
ms.topic: conceptual
keywords: ações de cartões de bots do teams
ms.openlocfilehash: b9276c7197070df43ba447707e6fa4d3d4098591
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566849"
---
# <a name="card-actions"></a><span data-ttu-id="1c98b-104">Ações de cartão</span><span class="sxs-lookup"><span data-stu-id="1c98b-104">Card actions</span></span>

<span data-ttu-id="1c98b-105">Os cartões usados por bots e extensões de mensagens em Teams suportam os seguintes tipos de atividade ( [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) )</span><span class="sxs-lookup"><span data-stu-id="1c98b-105">Cards used by bots and messaging extensions in Teams support the following activity ([`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards)) types.</span></span> <span data-ttu-id="1c98b-106">Observe que essas ações diferem das `potentialActions` Office 365 conectores quando usadas de Conectores.</span><span class="sxs-lookup"><span data-stu-id="1c98b-106">Note that these actions differ from `potentialActions` for Office 365 Connector cards when used from Connectors.</span></span>

| <span data-ttu-id="1c98b-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="1c98b-107">Type</span></span> | <span data-ttu-id="1c98b-108">Ação</span><span class="sxs-lookup"><span data-stu-id="1c98b-108">Action</span></span> |
| --- | --- |
| `openUrl` | <span data-ttu-id="1c98b-109">Abre uma URL no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="1c98b-109">Opens a URL in the default browser.</span></span> |
| `messageBack` | <span data-ttu-id="1c98b-110">Envia uma mensagem e uma carga para o bot do usuário que clicou no botão ou tocou no cartão e envia uma mensagem separada para o fluxo de chat.</span><span class="sxs-lookup"><span data-stu-id="1c98b-110">Sends a message and payload to the bot from the user who clicked the button or tapped the card and sends a separate message to the chat stream.</span></span> |
| `imBack`| <span data-ttu-id="1c98b-111">Envia uma mensagem para o bot do usuário que clicou no botão ou tocou no cartão.</span><span class="sxs-lookup"><span data-stu-id="1c98b-111">Sends a message to the bot from the user who clicked the button or tapped the card.</span></span> <span data-ttu-id="1c98b-112">Essa mensagem (de usuário para bot) é visível para todos os participantes da conversa.</span><span class="sxs-lookup"><span data-stu-id="1c98b-112">This message (from user to bot) is visible to all conversation participants.</span></span> |
| `invoke` | <span data-ttu-id="1c98b-113">Envia uma mensagem e uma carga para o bot do usuário que clicou no botão ou tocou no cartão.</span><span class="sxs-lookup"><span data-stu-id="1c98b-113">Sends a message and payload to the bot from the user who clicked the button or tapped the card.</span></span> <span data-ttu-id="1c98b-114">Esta mensagem não está visível.</span><span class="sxs-lookup"><span data-stu-id="1c98b-114">This message is not visible.</span></span> |
| `signin` | <span data-ttu-id="1c98b-115">Inicia o fluxo OAuth, permitindo que os bots se conectem com serviços seguros.</span><span class="sxs-lookup"><span data-stu-id="1c98b-115">Initiates OAuth flow, allowing bots to connect with secure services.</span></span> |

> [!NOTE]
>* <span data-ttu-id="1c98b-116">Teams não dá suporte a `CardAction` tipos não listados na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="1c98b-116">Teams does not support `CardAction` types not listed in the preceding table.</span></span>
>* <span data-ttu-id="1c98b-117">Teams não dá suporte à `potentialActions` propriedade.</span><span class="sxs-lookup"><span data-stu-id="1c98b-117">Teams does not support the `potentialActions` property.</span></span>
>* <span data-ttu-id="1c98b-118">As ações de cartão são diferentes [das ações sugeridas](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) no Serviço bot framework/bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="1c98b-118">Card actions are different than [suggested actions](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework/Azure Bot Service.</span></span> <span data-ttu-id="1c98b-119">As ações sugeridas não são suportadas Microsoft Teams: se você quiser que os botões apareçam em uma mensagem Teams bot, use um cartão.</span><span class="sxs-lookup"><span data-stu-id="1c98b-119">Suggested actions are not supported in Microsoft Teams: if you want buttons to appear on a Teams bot message, use a card.</span></span>
>* <span data-ttu-id="1c98b-120">Se você estiver usando uma ação de cartão como parte de uma extensão de mensagens, as ações não funcionarão até que o cartão seja enviado ao canal.</span><span class="sxs-lookup"><span data-stu-id="1c98b-120">If you are using a card action as part of a messaging extension, the actions do not work until the card is submitted to the channel.</span></span> <span data-ttu-id="1c98b-121">Eles não funcionam enquanto o cartão está na caixa de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="1c98b-121">They do not work while the card is in the compose message box.</span></span>

<span data-ttu-id="1c98b-122">Teams também oferece suporte [a ações de Cartões Adaptáveis](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), que são usadas apenas por Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="1c98b-122">Teams also supports [Adaptive Cards actions](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), which are only used by Adaptive Cards.</span></span> <span data-ttu-id="1c98b-123">Essas ações são listadas em sua própria seção no final desta referência.</span><span class="sxs-lookup"><span data-stu-id="1c98b-123">These actions are listed in their own section at the end of this reference.</span></span>

## <a name="openurl"></a><span data-ttu-id="1c98b-124">openUrl</span><span class="sxs-lookup"><span data-stu-id="1c98b-124">openUrl</span></span>

<span data-ttu-id="1c98b-125">Esse tipo de ação especifica uma URL a ser lançada no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="1c98b-125">This action type specifies a URL to launch in the default browser.</span></span> <span data-ttu-id="1c98b-126">Observe que o bot não recebe nenhum aviso sobre qual botão foi clicado.</span><span class="sxs-lookup"><span data-stu-id="1c98b-126">Note that your bot does not receive any notice on which button was clicked.</span></span>

<span data-ttu-id="1c98b-127">O `value` campo deve conter uma URL completa e corretamente formada.</span><span class="sxs-lookup"><span data-stu-id="1c98b-127">The `value` field must contain a full and properly formed URL.</span></span>

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a><span data-ttu-id="1c98b-128">messageBack</span><span class="sxs-lookup"><span data-stu-id="1c98b-128">messageBack</span></span>

<span data-ttu-id="1c98b-129">Com `messageBack` , você pode criar uma ação totalmente personalizada com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="1c98b-129">With `messageBack`, you can create a fully customized action with the following properties:</span></span>

| <span data-ttu-id="1c98b-130">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1c98b-130">Property</span></span> | <span data-ttu-id="1c98b-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c98b-131">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="1c98b-132">Aparece como o rótulo do botão.</span><span class="sxs-lookup"><span data-stu-id="1c98b-132">Appears as the button label.</span></span> |
| `displayText` | <span data-ttu-id="1c98b-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1c98b-133">Optional.</span></span> <span data-ttu-id="1c98b-134">Ecoado pelo usuário no fluxo de chat quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="1c98b-134">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="1c98b-135">Este texto não *é* enviado para seu bot.</span><span class="sxs-lookup"><span data-stu-id="1c98b-135">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="1c98b-136">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="1c98b-136">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="1c98b-137">Você pode codificar contexto para a ação, como identificadores exclusivos ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="1c98b-137">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="1c98b-138">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="1c98b-138">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="1c98b-139">Use essa propriedade para simplificar o desenvolvimento de bots: seu código pode verificar uma única propriedade de nível superior para despachar a lógica do bot.</span><span class="sxs-lookup"><span data-stu-id="1c98b-139">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="1c98b-140">A flexibilidade de meios que seu código pode optar por não deixar uma mensagem de usuário visível no `messageBack` histórico simplesmente não usando `displayText` .</span><span class="sxs-lookup"><span data-stu-id="1c98b-140">The flexibility of `messageBack` means that your code can choose not to leave a visible user message in the history simply by not using `displayText`.</span></span>

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

<span data-ttu-id="1c98b-141">A `value` propriedade pode ser uma cadeia de caracteres JSON serializada ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="1c98b-141">The `value` property can be either a serialized JSON string or a JSON object.</span></span>

### <a name="inbound-message-example"></a><span data-ttu-id="1c98b-142">Exemplo de mensagem de entrada</span><span class="sxs-lookup"><span data-stu-id="1c98b-142">Inbound message example</span></span>

<span data-ttu-id="1c98b-143">`replyToId` contém a ID da mensagem de onde veio a ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="1c98b-143">`replyToId` contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="1c98b-144">Use-o se quiser atualizar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="1c98b-144">Use it if you want to update the message.</span></span>

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

## <a name="imback"></a><span data-ttu-id="1c98b-145">imBack</span><span class="sxs-lookup"><span data-stu-id="1c98b-145">imBack</span></span>

<span data-ttu-id="1c98b-146">Essa ação aciona uma mensagem de retorno para seu bot, como se o usuário a digitou em uma mensagem de chat normal.</span><span class="sxs-lookup"><span data-stu-id="1c98b-146">This action triggers a return message to your bot, as if the user typed it in a normal chat message.</span></span> <span data-ttu-id="1c98b-147">Seu usuário e todos os outros usuários, se em um canal, verão a resposta do botão.</span><span class="sxs-lookup"><span data-stu-id="1c98b-147">Your user, and all other users if in a channel, will see that button response.</span></span>

<span data-ttu-id="1c98b-148">O campo deve conter a cadeia de caracteres de texto `value` ecoada no chat e, portanto, enviada de volta para o bot.</span><span class="sxs-lookup"><span data-stu-id="1c98b-148">The `value` field should contain the text string echoed in the chat and therefore sent back to the bot.</span></span> <span data-ttu-id="1c98b-149">Este é o texto da mensagem que você processará em seu bot para executar a lógica desejada.</span><span class="sxs-lookup"><span data-stu-id="1c98b-149">This is the message text you will process in your bot to perform the desired logic.</span></span> <span data-ttu-id="1c98b-150">Observação: este campo é uma cadeia de caracteres simples - não há suporte para formatação ou caracteres ocultos.</span><span class="sxs-lookup"><span data-stu-id="1c98b-150">Note: this field is a simple string - there is no support for formatting or hidden characters.</span></span>

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a><span data-ttu-id="1c98b-151">invoke</span><span class="sxs-lookup"><span data-stu-id="1c98b-151">invoke</span></span>

<span data-ttu-id="1c98b-152">A `invoke` ação é usada para invocar [módulos de tarefa](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span><span class="sxs-lookup"><span data-stu-id="1c98b-152">The `invoke` action is used for invoking [task modules](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="1c98b-153">A `invoke` ação contém três propriedades: , e `type` `title` `value` .</span><span class="sxs-lookup"><span data-stu-id="1c98b-153">The `invoke` action contains three properties: `type`, `title`, and `value`.</span></span> <span data-ttu-id="1c98b-154">A `value` propriedade pode conter uma cadeia de caracteres, um objeto JSON stringified ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="1c98b-154">The `value` property can contain a string, a stringified JSON object, or a JSON object.</span></span>

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

<span data-ttu-id="1c98b-155">Quando um usuário clica no botão, seu bot receberá o `value` objeto com algumas informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="1c98b-155">When a user clicks the button, your bot will receive the `value` object with some additional info.</span></span> <span data-ttu-id="1c98b-156">Observe que o tipo de atividade será `invoke` em vez de ( `message` `activity.Type == "invoke"` ).</span><span class="sxs-lookup"><span data-stu-id="1c98b-156">Please note that the activity type will be `invoke` instead of `message` (`activity.Type == "invoke"`).</span></span>

### <a name="example-invoke-button-definition-net"></a><span data-ttu-id="1c98b-157">Exemplo: Invocar definição de botão (.NET)</span><span class="sxs-lookup"><span data-stu-id="1c98b-157">Example: Invoke button definition (.NET)</span></span>

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a><span data-ttu-id="1c98b-158">Exemplo: Mensagem de invocação de entrada</span><span class="sxs-lookup"><span data-stu-id="1c98b-158">Example: Incoming invoke message</span></span>

<span data-ttu-id="1c98b-159">A propriedade de nível superior contém a ID da mensagem de onde a `replyToId` ação do cartão veio.</span><span class="sxs-lookup"><span data-stu-id="1c98b-159">The top-level `replyToId` property contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="1c98b-160">Use-o se quiser atualizar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="1c98b-160">Use it if you want to update the message.</span></span>

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

## <a name="signin"></a><span data-ttu-id="1c98b-161">signin</span><span class="sxs-lookup"><span data-stu-id="1c98b-161">signin</span></span>

<span data-ttu-id="1c98b-162">Inicia um fluxo OAuth, permitindo que os bots se conectem com serviços seguros, conforme descrito em mais detalhes aqui: Fluxo de autenticação [em bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="1c98b-162">Initiates an OAuth flow, allowing bots to connect with secure services, as described in more detail here: [Authentication flow in bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

## <a name="adaptive-cards-actions"></a><span data-ttu-id="1c98b-163">Ações de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="1c98b-163">Adaptive Cards actions</span></span>

<span data-ttu-id="1c98b-164">Os Cartões Adaptáveis suportam quatro tipos de ação:</span><span class="sxs-lookup"><span data-stu-id="1c98b-164">Adaptive Cards support four action types:</span></span>

* [<span data-ttu-id="1c98b-165">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="1c98b-165">Action.OpenUrl</span></span>](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [<span data-ttu-id="1c98b-166">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="1c98b-166">Action.Submit</span></span>](http://adaptivecards.io/explorer/Action.Submit.html)
* [<span data-ttu-id="1c98b-167">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="1c98b-167">Action.ShowCard</span></span>](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [<span data-ttu-id="1c98b-168">Action.Exebonito</span><span class="sxs-lookup"><span data-stu-id="1c98b-168">Action.Execute</span></span>](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

<span data-ttu-id="1c98b-169">Além das ações mencionadas acima, você pode modificar a carga do Cartão Adaptável para dar suporte a ações existentes da Estrutura de Bot usando uma propriedade no `Action.Submit` `msteams` objeto de `data` `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="1c98b-169">In addition to the actions mentioned above, you can modify the Adaptive Card `Action.Submit` payload to support existing Bot Framework actions using a `msteams` property in the `data` object of `Action.Submit`.</span></span> <span data-ttu-id="1c98b-170">As seções a seguir detalham como usar ações da Estrutura de Bot existentes com Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="1c98b-170">The below sections detail how to use existing Bot Framework actions with Adaptive Cards.</span></span>

> [!NOTE]
> <span data-ttu-id="1c98b-171">Adicionar `msteams` aos dados, com uma ação da Estrutura de Bot, não funciona com um módulo de tarefa cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="1c98b-171">Adding `msteams` to data, with a Bot Framework action, does not work with an Adaptive Card task module.</span></span>

### <a name="adaptive-cards-with-messageback-action"></a><span data-ttu-id="1c98b-172">Cartões Adaptáveis com ação messageBack</span><span class="sxs-lookup"><span data-stu-id="1c98b-172">Adaptive Cards with messageBack action</span></span>

<span data-ttu-id="1c98b-173">Para incluir uma `messageBack` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="1c98b-173">To include a `messageBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="1c98b-174">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="1c98b-174">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="1c98b-175">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1c98b-175">Property</span></span> | <span data-ttu-id="1c98b-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c98b-176">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="1c98b-177">Definir como `messageBack`</span><span class="sxs-lookup"><span data-stu-id="1c98b-177">Set to `messageBack`</span></span> |
| `displayText` | <span data-ttu-id="1c98b-178">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1c98b-178">Optional.</span></span> <span data-ttu-id="1c98b-179">Ecoado pelo usuário no fluxo de chat quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="1c98b-179">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="1c98b-180">Este texto não *é* enviado para seu bot.</span><span class="sxs-lookup"><span data-stu-id="1c98b-180">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="1c98b-181">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="1c98b-181">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="1c98b-182">Você pode codificar contexto para a ação, como identificadores exclusivos ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="1c98b-182">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="1c98b-183">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="1c98b-183">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="1c98b-184">Use essa propriedade para simplificar o desenvolvimento de bots: seu código pode verificar uma única propriedade de nível superior para despachar a lógica do bot.</span><span class="sxs-lookup"><span data-stu-id="1c98b-184">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

#### <a name="example"></a><span data-ttu-id="1c98b-185">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c98b-185">Example</span></span>

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

### <a name="adaptive-cards-with-imback-action"></a><span data-ttu-id="1c98b-186">Cartões Adaptáveis com ação imBack</span><span class="sxs-lookup"><span data-stu-id="1c98b-186">Adaptive Cards with imBack action</span></span>

<span data-ttu-id="1c98b-187">Para incluir uma `imBack` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="1c98b-187">To include a `imBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="1c98b-188">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="1c98b-188">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="1c98b-189">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1c98b-189">Property</span></span> | <span data-ttu-id="1c98b-190">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c98b-190">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="1c98b-191">Definir como `imBack`</span><span class="sxs-lookup"><span data-stu-id="1c98b-191">Set to `imBack`</span></span> |
| `value` | <span data-ttu-id="1c98b-192">Cadeia de caracteres que precisa ser ecoada no chat</span><span class="sxs-lookup"><span data-stu-id="1c98b-192">String that needs to be echoed back in the chat</span></span> |

#### <a name="example"></a><span data-ttu-id="1c98b-193">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c98b-193">Example</span></span>

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

### <a name="adaptive-cards-with-signin-action"></a><span data-ttu-id="1c98b-194">Cartões Adaptáveis com ação de signin</span><span class="sxs-lookup"><span data-stu-id="1c98b-194">Adaptive Cards with signin action</span></span>

<span data-ttu-id="1c98b-195">Para incluir uma `signin` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="1c98b-195">To include a `signin` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="1c98b-196">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="1c98b-196">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="1c98b-197">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1c98b-197">Property</span></span> | <span data-ttu-id="1c98b-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c98b-198">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="1c98b-199">Definir como `signin` .</span><span class="sxs-lookup"><span data-stu-id="1c98b-199">Set to `signin`.</span></span> |
| `value` | <span data-ttu-id="1c98b-200">De acordo com a URL para a que você deseja redirecionar.</span><span class="sxs-lookup"><span data-stu-id="1c98b-200">Set to the URL that you want to redirect to.</span></span>  |

#### <a name="example"></a><span data-ttu-id="1c98b-201">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c98b-201">Example</span></span>

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

### <a name="adaptive-cards-with-invoke-action"></a><span data-ttu-id="1c98b-202">Cartões Adaptáveis com ação de invocação</span><span class="sxs-lookup"><span data-stu-id="1c98b-202">Adaptive Cards with invoke action</span></span>
 
<span data-ttu-id="1c98b-203">Para incluir uma `invoke` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="1c98b-203">To include a `invoke` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="1c98b-204">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="1c98b-204">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="1c98b-205">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1c98b-205">Property</span></span> | <span data-ttu-id="1c98b-206">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c98b-206">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="1c98b-207">Definir como `task/fetch`</span><span class="sxs-lookup"><span data-stu-id="1c98b-207">Set to `task/fetch`</span></span> |
| `data` | <span data-ttu-id="1c98b-208">Definir o valor</span><span class="sxs-lookup"><span data-stu-id="1c98b-208">Set the value</span></span>  |

#### <a name="example"></a><span data-ttu-id="1c98b-209">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c98b-209">Example</span></span>

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

#### <a name="example-2-with-additional-payload-data"></a><span data-ttu-id="1c98b-210">Exemplo 2 (com dados de carga adicionais)</span><span class="sxs-lookup"><span data-stu-id="1c98b-210">Example 2 (with additional payload data)</span></span>

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
