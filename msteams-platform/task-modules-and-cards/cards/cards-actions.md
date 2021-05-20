---
title: Adicionar ações de cartão em um bot
description: Descreve ações de cartão em Microsoft Teams e como usá-las em seus bots
localization_priority: Normal
ms.topic: conceptual
keywords: equipes bots ações cartões
ms.openlocfilehash: b9276c7197070df43ba447707e6fa4d3d4098591
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566849"
---
# <a name="card-actions"></a><span data-ttu-id="b1c11-104">Ações de cartão</span><span class="sxs-lookup"><span data-stu-id="b1c11-104">Card actions</span></span>

<span data-ttu-id="b1c11-105">Cartões usados por bots e extensões de mensagens em Teams suportam os [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) seguintes tipos de atividade () .</span><span class="sxs-lookup"><span data-stu-id="b1c11-105">Cards used by bots and messaging extensions in Teams support the following activity ([`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards)) types.</span></span> <span data-ttu-id="b1c11-106">Observe que essas ações diferem de `potentialActions` Office 365 cartões Connector quando usadas a partir de Conectores.</span><span class="sxs-lookup"><span data-stu-id="b1c11-106">Note that these actions differ from `potentialActions` for Office 365 Connector cards when used from Connectors.</span></span>

| <span data-ttu-id="b1c11-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="b1c11-107">Type</span></span> | <span data-ttu-id="b1c11-108">Action</span><span class="sxs-lookup"><span data-stu-id="b1c11-108">Action</span></span> |
| --- | --- |
| `openUrl` | <span data-ttu-id="b1c11-109">Abre uma URL no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="b1c11-109">Opens a URL in the default browser.</span></span> |
| `messageBack` | <span data-ttu-id="b1c11-110">Envia uma mensagem e carga para o bot do usuário que clicou no botão ou tocou no cartão e envia uma mensagem separada para o fluxo de bate-papo.</span><span class="sxs-lookup"><span data-stu-id="b1c11-110">Sends a message and payload to the bot from the user who clicked the button or tapped the card and sends a separate message to the chat stream.</span></span> |
| `imBack`| <span data-ttu-id="b1c11-111">Envia uma mensagem para o bot do usuário que clicou no botão ou tocou no cartão.</span><span class="sxs-lookup"><span data-stu-id="b1c11-111">Sends a message to the bot from the user who clicked the button or tapped the card.</span></span> <span data-ttu-id="b1c11-112">Esta mensagem (de usuário para bot) é visível para todos os participantes da conversa.</span><span class="sxs-lookup"><span data-stu-id="b1c11-112">This message (from user to bot) is visible to all conversation participants.</span></span> |
| `invoke` | <span data-ttu-id="b1c11-113">Envia uma mensagem e carga para o bot do usuário que clicou no botão ou tocou no cartão.</span><span class="sxs-lookup"><span data-stu-id="b1c11-113">Sends a message and payload to the bot from the user who clicked the button or tapped the card.</span></span> <span data-ttu-id="b1c11-114">Esta mensagem não é visível.</span><span class="sxs-lookup"><span data-stu-id="b1c11-114">This message is not visible.</span></span> |
| `signin` | <span data-ttu-id="b1c11-115">Inicia o fluxo OAuth, permitindo que os bots se conectem com serviços seguros.</span><span class="sxs-lookup"><span data-stu-id="b1c11-115">Initiates OAuth flow, allowing bots to connect with secure services.</span></span> |

> [!NOTE]
>* <span data-ttu-id="b1c11-116">Teams não suporta `CardAction` tipos não listados na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="b1c11-116">Teams does not support `CardAction` types not listed in the preceding table.</span></span>
>* <span data-ttu-id="b1c11-117">Teams não suporta a `potentialActions` propriedade.</span><span class="sxs-lookup"><span data-stu-id="b1c11-117">Teams does not support the `potentialActions` property.</span></span>
>* <span data-ttu-id="b1c11-118">As ações do cartão são diferentes das [ações sugeridas](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) no Bot Framework/Azure Bot Service.</span><span class="sxs-lookup"><span data-stu-id="b1c11-118">Card actions are different than [suggested actions](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework/Azure Bot Service.</span></span> <span data-ttu-id="b1c11-119">As ações sugeridas não são suportadas em Microsoft Teams: se você quiser que os botões apareçam em uma mensagem de bot Teams, use um cartão.</span><span class="sxs-lookup"><span data-stu-id="b1c11-119">Suggested actions are not supported in Microsoft Teams: if you want buttons to appear on a Teams bot message, use a card.</span></span>
>* <span data-ttu-id="b1c11-120">Se você estiver usando uma ação de cartão como parte de uma extensão de mensagens, as ações não funcionam até que a carteira seja enviada ao canal.</span><span class="sxs-lookup"><span data-stu-id="b1c11-120">If you are using a card action as part of a messaging extension, the actions do not work until the card is submitted to the channel.</span></span> <span data-ttu-id="b1c11-121">Eles não funcionam enquanto o cartão está na caixa de mensagens de composição.</span><span class="sxs-lookup"><span data-stu-id="b1c11-121">They do not work while the card is in the compose message box.</span></span>

<span data-ttu-id="b1c11-122">Teams também suporta [ações de Cartões Adaptativos,](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)que são usadas apenas por Cartões Adaptativos.</span><span class="sxs-lookup"><span data-stu-id="b1c11-122">Teams also supports [Adaptive Cards actions](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), which are only used by Adaptive Cards.</span></span> <span data-ttu-id="b1c11-123">Essas ações estão listadas em sua própria seção no final desta referência.</span><span class="sxs-lookup"><span data-stu-id="b1c11-123">These actions are listed in their own section at the end of this reference.</span></span>

## <a name="openurl"></a><span data-ttu-id="b1c11-124">openUrl</span><span class="sxs-lookup"><span data-stu-id="b1c11-124">openUrl</span></span>

<span data-ttu-id="b1c11-125">Esse tipo de ação especifica uma URL para ser lançada no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="b1c11-125">This action type specifies a URL to launch in the default browser.</span></span> <span data-ttu-id="b1c11-126">Observe que seu bot não recebe nenhum aviso sobre qual botão foi clicado.</span><span class="sxs-lookup"><span data-stu-id="b1c11-126">Note that your bot does not receive any notice on which button was clicked.</span></span>

<span data-ttu-id="b1c11-127">O `value` campo deve conter uma URL completa e devidamente formada.</span><span class="sxs-lookup"><span data-stu-id="b1c11-127">The `value` field must contain a full and properly formed URL.</span></span>

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a><span data-ttu-id="b1c11-128">mensagemBack</span><span class="sxs-lookup"><span data-stu-id="b1c11-128">messageBack</span></span>

<span data-ttu-id="b1c11-129">Com `messageBack` , você pode criar uma ação totalmente personalizada com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b1c11-129">With `messageBack`, you can create a fully customized action with the following properties:</span></span>

| <span data-ttu-id="b1c11-130">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b1c11-130">Property</span></span> | <span data-ttu-id="b1c11-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1c11-131">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="b1c11-132">Aparece como a etiqueta do botão.</span><span class="sxs-lookup"><span data-stu-id="b1c11-132">Appears as the button label.</span></span> |
| `displayText` | <span data-ttu-id="b1c11-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b1c11-133">Optional.</span></span> <span data-ttu-id="b1c11-134">Ecoado pelo usuário no fluxo de bate-papo quando a ação é realizada.</span><span class="sxs-lookup"><span data-stu-id="b1c11-134">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="b1c11-135">Este texto *não* é enviado para o seu bot.</span><span class="sxs-lookup"><span data-stu-id="b1c11-135">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="b1c11-136">Enviado para o seu bot quando a ação é realizada.</span><span class="sxs-lookup"><span data-stu-id="b1c11-136">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="b1c11-137">Você pode codificar o contexto da ação, como identificadores exclusivos ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="b1c11-137">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="b1c11-138">Enviado para o seu bot quando a ação é realizada.</span><span class="sxs-lookup"><span data-stu-id="b1c11-138">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="b1c11-139">Use esta propriedade para simplificar o desenvolvimento de bots: seu código pode verificar uma única propriedade de alto nível para despachar a lógica do bot.</span><span class="sxs-lookup"><span data-stu-id="b1c11-139">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="b1c11-140">A flexibilidade de `messageBack` meios que seu código pode optar por não deixar uma mensagem de usuário visível no histórico simplesmente não usando `displayText` .</span><span class="sxs-lookup"><span data-stu-id="b1c11-140">The flexibility of `messageBack` means that your code can choose not to leave a visible user message in the history simply by not using `displayText`.</span></span>

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

<span data-ttu-id="b1c11-141">A `value` propriedade pode ser uma sequência JSON serializada ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="b1c11-141">The `value` property can be either a serialized JSON string or a JSON object.</span></span>

### <a name="inbound-message-example"></a><span data-ttu-id="b1c11-142">Exemplo de mensagem de entrada</span><span class="sxs-lookup"><span data-stu-id="b1c11-142">Inbound message example</span></span>

<span data-ttu-id="b1c11-143">`replyToId` contém a identificação da mensagem de onde veio a ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="b1c11-143">`replyToId` contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="b1c11-144">Use-o se quiser atualizar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="b1c11-144">Use it if you want to update the message.</span></span>

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

## <a name="imback"></a><span data-ttu-id="b1c11-145">imBack</span><span class="sxs-lookup"><span data-stu-id="b1c11-145">imBack</span></span>

<span data-ttu-id="b1c11-146">Essa ação aciona uma mensagem de retorno ao seu bot, como se o usuário digitasse em uma mensagem de chat normal.</span><span class="sxs-lookup"><span data-stu-id="b1c11-146">This action triggers a return message to your bot, as if the user typed it in a normal chat message.</span></span> <span data-ttu-id="b1c11-147">Seu usuário, e todos os outros usuários se em um canal, verão essa resposta ao botão.</span><span class="sxs-lookup"><span data-stu-id="b1c11-147">Your user, and all other users if in a channel, will see that button response.</span></span>

<span data-ttu-id="b1c11-148">O `value` campo deve conter a sequência de texto ecoada no chat e, portanto, enviada de volta para o bot.</span><span class="sxs-lookup"><span data-stu-id="b1c11-148">The `value` field should contain the text string echoed in the chat and therefore sent back to the bot.</span></span> <span data-ttu-id="b1c11-149">Este é o texto de mensagem que você processará em seu bot para executar a lógica desejada.</span><span class="sxs-lookup"><span data-stu-id="b1c11-149">This is the message text you will process in your bot to perform the desired logic.</span></span> <span data-ttu-id="b1c11-150">Nota: este campo é uma sequência simples - não há suporte para formatação ou caracteres ocultos.</span><span class="sxs-lookup"><span data-stu-id="b1c11-150">Note: this field is a simple string - there is no support for formatting or hidden characters.</span></span>

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a><span data-ttu-id="b1c11-151">invocar</span><span class="sxs-lookup"><span data-stu-id="b1c11-151">invoke</span></span>

<span data-ttu-id="b1c11-152">A `invoke` ação é usada para invocar [módulos de tarefas.](~/task-modules-and-cards/task-modules/task-modules-bots.md)</span><span class="sxs-lookup"><span data-stu-id="b1c11-152">The `invoke` action is used for invoking [task modules](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="b1c11-153">A `invoke` ação contém três propriedades: `type` , , e `title` `value` .</span><span class="sxs-lookup"><span data-stu-id="b1c11-153">The `invoke` action contains three properties: `type`, `title`, and `value`.</span></span> <span data-ttu-id="b1c11-154">A `value` propriedade pode conter uma sequência, um objeto JSON stringified ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="b1c11-154">The `value` property can contain a string, a stringified JSON object, or a JSON object.</span></span>

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

<span data-ttu-id="b1c11-155">Quando um usuário clica no botão, o bot receberá o `value` objeto com algumas informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="b1c11-155">When a user clicks the button, your bot will receive the `value` object with some additional info.</span></span> <span data-ttu-id="b1c11-156">Por favor, note que o tipo de atividade será `invoke` em vez de ( `message` `activity.Type == "invoke"` .</span><span class="sxs-lookup"><span data-stu-id="b1c11-156">Please note that the activity type will be `invoke` instead of `message` (`activity.Type == "invoke"`).</span></span>

### <a name="example-invoke-button-definition-net"></a><span data-ttu-id="b1c11-157">Exemplo: Invocar definição de botão (.NET)</span><span class="sxs-lookup"><span data-stu-id="b1c11-157">Example: Invoke button definition (.NET)</span></span>

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a><span data-ttu-id="b1c11-158">Exemplo: Mensagem de invocação recebida</span><span class="sxs-lookup"><span data-stu-id="b1c11-158">Example: Incoming invoke message</span></span>

<span data-ttu-id="b1c11-159">A propriedade de alto nível `replyToId` contém a identificação da mensagem de onde a ação do cartão veio.</span><span class="sxs-lookup"><span data-stu-id="b1c11-159">The top-level `replyToId` property contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="b1c11-160">Use-o se quiser atualizar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="b1c11-160">Use it if you want to update the message.</span></span>

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

## <a name="signin"></a><span data-ttu-id="b1c11-161">signin</span><span class="sxs-lookup"><span data-stu-id="b1c11-161">signin</span></span>

<span data-ttu-id="b1c11-162">Inicia um fluxo OAuth, permitindo que os bots se conectem com serviços seguros, conforme descrito em mais detalhes aqui: [Fluxo de autenticação em bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="b1c11-162">Initiates an OAuth flow, allowing bots to connect with secure services, as described in more detail here: [Authentication flow in bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

## <a name="adaptive-cards-actions"></a><span data-ttu-id="b1c11-163">Ações de Cartões Adaptativos</span><span class="sxs-lookup"><span data-stu-id="b1c11-163">Adaptive Cards actions</span></span>

<span data-ttu-id="b1c11-164">Cartões adaptativos suportam quatro tipos de ação:</span><span class="sxs-lookup"><span data-stu-id="b1c11-164">Adaptive Cards support four action types:</span></span>

* [<span data-ttu-id="b1c11-165">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="b1c11-165">Action.OpenUrl</span></span>](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [<span data-ttu-id="b1c11-166">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="b1c11-166">Action.Submit</span></span>](http://adaptivecards.io/explorer/Action.Submit.html)
* [<span data-ttu-id="b1c11-167">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="b1c11-167">Action.ShowCard</span></span>](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [<span data-ttu-id="b1c11-168">Action.Exefofo</span><span class="sxs-lookup"><span data-stu-id="b1c11-168">Action.Execute</span></span>](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

<span data-ttu-id="b1c11-169">Além das ações mencionadas acima, você pode modificar a carga de cartão adaptável `Action.Submit` para apoiar as ações existentes do Bot Framework usando uma propriedade no objeto de `msteams` `data` `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="b1c11-169">In addition to the actions mentioned above, you can modify the Adaptive Card `Action.Submit` payload to support existing Bot Framework actions using a `msteams` property in the `data` object of `Action.Submit`.</span></span> <span data-ttu-id="b1c11-170">As seções abaixo detalham como usar as ações existentes do Bot Framework com cartões adaptativos.</span><span class="sxs-lookup"><span data-stu-id="b1c11-170">The below sections detail how to use existing Bot Framework actions with Adaptive Cards.</span></span>

> [!NOTE]
> <span data-ttu-id="b1c11-171">Adicionar `msteams` dados, com uma ação do Bot Framework, não funciona com um módulo de tarefa de cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="b1c11-171">Adding `msteams` to data, with a Bot Framework action, does not work with an Adaptive Card task module.</span></span>

### <a name="adaptive-cards-with-messageback-action"></a><span data-ttu-id="b1c11-172">Cartões adaptativos com ação messageBack</span><span class="sxs-lookup"><span data-stu-id="b1c11-172">Adaptive Cards with messageBack action</span></span>

<span data-ttu-id="b1c11-173">Para incluir uma `messageBack` ação com uma placa adaptativa inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="b1c11-173">To include a `messageBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="b1c11-174">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="b1c11-174">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="b1c11-175">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b1c11-175">Property</span></span> | <span data-ttu-id="b1c11-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1c11-176">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="b1c11-177">Definido para `messageBack`</span><span class="sxs-lookup"><span data-stu-id="b1c11-177">Set to `messageBack`</span></span> |
| `displayText` | <span data-ttu-id="b1c11-178">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b1c11-178">Optional.</span></span> <span data-ttu-id="b1c11-179">Ecoado pelo usuário no fluxo de bate-papo quando a ação é realizada.</span><span class="sxs-lookup"><span data-stu-id="b1c11-179">Echoed by the user into the chat stream when the action is performed.</span></span> <span data-ttu-id="b1c11-180">Este texto *não* é enviado para o seu bot.</span><span class="sxs-lookup"><span data-stu-id="b1c11-180">This text is *not* sent to your bot.</span></span> |
| `value` | <span data-ttu-id="b1c11-181">Enviado para o seu bot quando a ação é realizada.</span><span class="sxs-lookup"><span data-stu-id="b1c11-181">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="b1c11-182">Você pode codificar o contexto da ação, como identificadores exclusivos ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="b1c11-182">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="b1c11-183">Enviado para o seu bot quando a ação é realizada.</span><span class="sxs-lookup"><span data-stu-id="b1c11-183">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="b1c11-184">Use esta propriedade para simplificar o desenvolvimento de bots: seu código pode verificar uma única propriedade de alto nível para despachar a lógica do bot.</span><span class="sxs-lookup"><span data-stu-id="b1c11-184">Use this property to simplify bot development: Your code can check a single top-level property to dispatch bot logic.</span></span> |

#### <a name="example"></a><span data-ttu-id="b1c11-185">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1c11-185">Example</span></span>

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

### <a name="adaptive-cards-with-imback-action"></a><span data-ttu-id="b1c11-186">Cartões adaptativos com ação imBack</span><span class="sxs-lookup"><span data-stu-id="b1c11-186">Adaptive Cards with imBack action</span></span>

<span data-ttu-id="b1c11-187">Para incluir uma `imBack` ação com uma placa adaptativa inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="b1c11-187">To include a `imBack` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="b1c11-188">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="b1c11-188">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="b1c11-189">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b1c11-189">Property</span></span> | <span data-ttu-id="b1c11-190">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1c11-190">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="b1c11-191">Definido para `imBack`</span><span class="sxs-lookup"><span data-stu-id="b1c11-191">Set to `imBack`</span></span> |
| `value` | <span data-ttu-id="b1c11-192">String que precisa ser ecoado de volta no bate-papo</span><span class="sxs-lookup"><span data-stu-id="b1c11-192">String that needs to be echoed back in the chat</span></span> |

#### <a name="example"></a><span data-ttu-id="b1c11-193">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1c11-193">Example</span></span>

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

### <a name="adaptive-cards-with-signin-action"></a><span data-ttu-id="b1c11-194">Cartões Adaptativos com ação signin</span><span class="sxs-lookup"><span data-stu-id="b1c11-194">Adaptive Cards with signin action</span></span>

<span data-ttu-id="b1c11-195">Para incluir uma `signin` ação com uma placa adaptativa inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="b1c11-195">To include a `signin` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="b1c11-196">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="b1c11-196">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="b1c11-197">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b1c11-197">Property</span></span> | <span data-ttu-id="b1c11-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1c11-198">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="b1c11-199">Pronto para `signin` .</span><span class="sxs-lookup"><span data-stu-id="b1c11-199">Set to `signin`.</span></span> |
| `value` | <span data-ttu-id="b1c11-200">Defina para a URL para a que você deseja redirecionar.</span><span class="sxs-lookup"><span data-stu-id="b1c11-200">Set to the URL that you want to redirect to.</span></span>  |

#### <a name="example"></a><span data-ttu-id="b1c11-201">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1c11-201">Example</span></span>

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

### <a name="adaptive-cards-with-invoke-action"></a><span data-ttu-id="b1c11-202">Cartões Adaptativos com ação de invocação</span><span class="sxs-lookup"><span data-stu-id="b1c11-202">Adaptive Cards with invoke action</span></span>
 
<span data-ttu-id="b1c11-203">Para incluir uma `invoke` ação com uma placa adaptativa inclua os seguintes detalhes no `msteams` objeto.</span><span class="sxs-lookup"><span data-stu-id="b1c11-203">To include a `invoke` action with an Adaptive Card include the following details in the `msteams` object.</span></span> <span data-ttu-id="b1c11-204">Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="b1c11-204">Note that you can include additional hidden properties in the `data` object if needed.</span></span>

| <span data-ttu-id="b1c11-205">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b1c11-205">Property</span></span> | <span data-ttu-id="b1c11-206">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1c11-206">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="b1c11-207">Definido para `task/fetch`</span><span class="sxs-lookup"><span data-stu-id="b1c11-207">Set to `task/fetch`</span></span> |
| `data` | <span data-ttu-id="b1c11-208">Defina o valor</span><span class="sxs-lookup"><span data-stu-id="b1c11-208">Set the value</span></span>  |

#### <a name="example"></a><span data-ttu-id="b1c11-209">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1c11-209">Example</span></span>

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

#### <a name="example-2-with-additional-payload-data"></a><span data-ttu-id="b1c11-210">Exemplo 2 (com dados adicionais de carga)</span><span class="sxs-lookup"><span data-stu-id="b1c11-210">Example 2 (with additional payload data)</span></span>

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
