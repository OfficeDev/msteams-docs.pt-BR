---
title: Adicionar ações de cartão em um bot
description: Descreve ações de cartão em Microsoft Teams e como usá-las em seus bots
localization_priority: Normal
ms.topic: conceptual
keywords: ações de cartões de bots do teams
ms.openlocfilehash: 4af152f6179785687d4fd7371d202c56e1aee170
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254199"
---
# <a name="card-actions"></a><span data-ttu-id="6dfa2-104">Ações do cartão</span><span class="sxs-lookup"><span data-stu-id="6dfa2-104">Card actions</span></span>

<span data-ttu-id="6dfa2-105">Os cartões usados por bots e extensões de mensagens em Teams suportam os seguintes tipos de [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) atividade:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-105">Cards used by bots and messaging extensions in Teams support the following activity [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) types:</span></span>

> [!NOTE]
> <span data-ttu-id="6dfa2-106">As `CardAction` ações diferem `potentialActions` das Office 365 conectores quando usadas de conectores.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-106">The `CardAction` actions differ from `potentialActions` for Office 365 Connector cards when used from connectors.</span></span>

| <span data-ttu-id="6dfa2-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="6dfa2-107">Type</span></span> | <span data-ttu-id="6dfa2-108">Action</span><span class="sxs-lookup"><span data-stu-id="6dfa2-108">Action</span></span> |
| --- | --- |
| `openUrl` | <span data-ttu-id="6dfa2-109">Abre uma URL no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-109">Opens a URL in the default browser.</span></span> |
| `messageBack` | <span data-ttu-id="6dfa2-110">Envia uma mensagem e uma carga para o bot do usuário que selecionou o botão ou tocou no cartão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-110">Sends a message and payload to the bot from the user who selected the button or tapped the card.</span></span> <span data-ttu-id="6dfa2-111">Envia uma mensagem separada para o fluxo de chat.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-111">Sends a separate message to the chat stream.</span></span> |
| `imBack`| <span data-ttu-id="6dfa2-112">Envia uma mensagem para o bot do usuário que selecionou o botão ou tapped o cartão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-112">Sends a message to the bot from the user who selected the button or tapped the card.</span></span> <span data-ttu-id="6dfa2-113">Essa mensagem de usuário para bot é visível para todos os participantes da conversa.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-113">This message from user to bot is visible to all conversation participants.</span></span> |
| `invoke` | <span data-ttu-id="6dfa2-114">Envia uma mensagem e uma carga para o bot do usuário que selecionou o botão ou tocou no cartão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-114">Sends a message and payload to the bot from the user who selected the button or tapped the card.</span></span> <span data-ttu-id="6dfa2-115">Esta mensagem não está visível.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-115">This message is not visible.</span></span> |
| `signin` | <span data-ttu-id="6dfa2-116">Inicia o fluxo OAuth, permitindo que os bots se conectem com serviços seguros.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-116">Initiates OAuth flow, allowing bots to connect with secure services.</span></span> |

> [!NOTE]
>* <span data-ttu-id="6dfa2-117">Teams não dá suporte a `CardAction` tipos não listados na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-117">Teams does not support `CardAction` types not listed in the previous table.</span></span>
>* <span data-ttu-id="6dfa2-118">Teams não dá suporte à `potentialActions` propriedade.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-118">Teams does not support the `potentialActions` property.</span></span>
>* <span data-ttu-id="6dfa2-119">As ações de cartão são diferentes [das ações sugeridas](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) no Bot Framework ou no Serviço de Bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-119">Card actions are different than [suggested actions](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) in Bot Framework or Azure Bot Service.</span></span> <span data-ttu-id="6dfa2-120">Ações sugeridas não são suportadas Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-120">Suggested actions are not supported in Microsoft Teams.</span></span> <span data-ttu-id="6dfa2-121">Se quiser que os botões apareçam em uma mensagem Teams bot, use um cartão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-121">If you want buttons to appear on a Teams bot message, use a card.</span></span>
>* <span data-ttu-id="6dfa2-122">Se você estiver usando uma ação de cartão como parte de uma extensão de mensagens, as ações não funcionarão até que o cartão seja enviado ao canal.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-122">If you are using a card action as part of a messaging extension, the actions do not work until the card is submitted to the channel.</span></span> <span data-ttu-id="6dfa2-123">As ações não funcionam enquanto o cartão está na caixa de mensagem de redação.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-123">The actions do not work while the card is in the compose message box.</span></span>

## <a name="action-type-openurl"></a><span data-ttu-id="6dfa2-124">Tipo de ação openUrl</span><span class="sxs-lookup"><span data-stu-id="6dfa2-124">Action type openUrl</span></span>

<span data-ttu-id="6dfa2-125">`openUrl` tipo de ação especifica uma URL a ser lançada no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-125">`openUrl` action type specifies a URL to launch in the default browser.</span></span>

> [!NOTE]
> <span data-ttu-id="6dfa2-126">Seu bot não recebe nenhum aviso sobre qual botão foi selecionado.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-126">Your bot does not receive any notice on which button was selected.</span></span>

<span data-ttu-id="6dfa2-127">Com `openUrl` , você pode criar uma ação com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-127">With `openUrl`, you can create an action with the following properties:</span></span>

| <span data-ttu-id="6dfa2-128">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6dfa2-128">Property</span></span> | <span data-ttu-id="6dfa2-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfa2-129">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="6dfa2-130">Aparece como o rótulo do botão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-130">Appears as the button label.</span></span> |
| `value` | <span data-ttu-id="6dfa2-131">Esse campo deve conter uma URL completa e corretamente formada.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-131">This field must contain a full and properly formed URL.</span></span> |

# <a name="json"></a>[<span data-ttu-id="6dfa2-132">JSON</span><span class="sxs-lookup"><span data-stu-id="6dfa2-132">JSON</span></span>](#tab/json)

<span data-ttu-id="6dfa2-133">O código a seguir mostra um exemplo de `openUrl` tipo de ação em JSON:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-133">The following code shows an example of `openUrl` action type in JSON:</span></span>

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

# <a name="c"></a>[<span data-ttu-id="6dfa2-134">C#</span><span class="sxs-lookup"><span data-stu-id="6dfa2-134">C#</span></span>](#tab/csharp)

<span data-ttu-id="6dfa2-135">O código a seguir mostra um exemplo de `openUrl` tipo de ação C#:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-135">The following code shows an example of `openUrl` action type in C#:</span></span>

```csharp
var button = new CardAction()
{
    Type = ActionTypes.OpenUrl,
    Title = "Tabs in Teams",
    Value = "https://docs.microsoft.com/en-us/microsoftteams/platform/"
};
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="6dfa2-136">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="6dfa2-136">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="6dfa2-137">O código a seguir mostra um exemplo de `openUrl` tipo de ação em JavaScript:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-137">The following code shows an example of `openUrl` action type in JavaScript:</span></span>

```javascript
CardFactory.actions([
{
    type: 'openUrl',
    title: 'Tabs in Teams',
    value: 'https://docs.microsoft.com/en-us/microsoftteams/platform/'
}])
```

---

## <a name="action-type-messageback"></a><span data-ttu-id="6dfa2-138">Tipo de ação messageBack</span><span class="sxs-lookup"><span data-stu-id="6dfa2-138">Action type messageBack</span></span>

<span data-ttu-id="6dfa2-139">Com `messageBack` , você pode criar uma ação totalmente personalizada com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-139">With `messageBack`, you can create a fully customized action with the following properties:</span></span>

| <span data-ttu-id="6dfa2-140">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6dfa2-140">Property</span></span> | <span data-ttu-id="6dfa2-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfa2-141">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="6dfa2-142">Aparece como o rótulo do botão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-142">Appears as the button label.</span></span> |
| `displayText` | <span data-ttu-id="6dfa2-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-143">Optional.</span></span> <span data-ttu-id="6dfa2-144">Usado pelo usuário no fluxo de chat quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-144">Used by the user in the chat stream when the action is performed.</span></span> <span data-ttu-id="6dfa2-145">Este texto não é enviado para seu bot.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-145">This text is not sent to your bot.</span></span> |
| `value` | <span data-ttu-id="6dfa2-146">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-146">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="6dfa2-147">Você pode codificar contexto para a ação, como identificadores exclusivos ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-147">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="6dfa2-148">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-148">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="6dfa2-149">Use essa propriedade para simplificar o desenvolvimento de bots.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-149">Use this property to simplify bot development.</span></span> <span data-ttu-id="6dfa2-150">Seu código pode verificar uma única propriedade de nível superior para despachar a lógica do bot.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-150">Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="6dfa2-151">A flexibilidade de meios de que seu código não pode deixar uma mensagem de usuário visível no `messageBack` histórico simplesmente não usando `displayText` .</span><span class="sxs-lookup"><span data-stu-id="6dfa2-151">The flexibility of `messageBack` means that your code cannot leave a visible user message in the history simply by not using `displayText`.</span></span>

# <a name="json"></a>[<span data-ttu-id="6dfa2-152">JSON</span><span class="sxs-lookup"><span data-stu-id="6dfa2-152">JSON</span></span>](#tab/json)

<span data-ttu-id="6dfa2-153">O código a seguir mostra um exemplo de `messageBack` tipo de ação em JSON:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-153">The following code shows an example of `messageBack` action type in JSON:</span></span>

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

<span data-ttu-id="6dfa2-154">A `value` propriedade pode ser uma cadeia de caracteres JSON serializada ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-154">The `value` property can be either a serialized JSON string or a JSON object.</span></span>

# <a name="c"></a>[<span data-ttu-id="6dfa2-155">C#</span><span class="sxs-lookup"><span data-stu-id="6dfa2-155">C#</span></span>](#tab/csharp)

<span data-ttu-id="6dfa2-156">O código a seguir mostra um exemplo de `messageBack` tipo de ação C#:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-156">The following code shows an example of `messageBack` action type in C#:</span></span>

```csharp
var button = new CardAction()
{
    Type = ActionTypes.MessageBack,
    Title = "My MessageBack button",
    DisplayText = "I clicked this button",
    Text = "User just clicked the MessageBack button",
    Value = "{\"property\": \"propertyValue\" }"
};
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="6dfa2-157">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="6dfa2-157">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="6dfa2-158">O código a seguir mostra um exemplo de `messageBack` tipo de ação em JavaScript:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-158">The following code shows an example of `messageBack` action type in JavaScript:</span></span>

```javascript
CardFactory.actions([
{
    type: 'messageBack',
    title: "My MessageBack button",
    displayText: "I clicked this button",
    text: "User just clicked the MessageBack button",
    value: {property: "propertyValue" }
}])
```

---

### <a name="inbound-message-example"></a><span data-ttu-id="6dfa2-159">Exemplo de mensagem de entrada</span><span class="sxs-lookup"><span data-stu-id="6dfa2-159">Inbound message example</span></span>

<span data-ttu-id="6dfa2-160">`replyToId` contém a ID da mensagem de onde veio a ação do cartão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-160">`replyToId` contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="6dfa2-161">Use-o se quiser atualizar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-161">Use it if you want to update the message.</span></span>

<span data-ttu-id="6dfa2-162">O código a seguir mostra um exemplo de mensagem de entrada:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-162">The following code shows an example of inbound message:</span></span>

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

## <a name="action-type-imback"></a><span data-ttu-id="6dfa2-163">Tipo de ação imBack</span><span class="sxs-lookup"><span data-stu-id="6dfa2-163">Action type imBack</span></span>

<span data-ttu-id="6dfa2-164">A ação dispara uma mensagem de retorno para seu bot, como se o usuário a digitou `imBack` em uma mensagem de chat normal.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-164">The `imBack` action triggers a return message to your bot, as if the user typed it in a normal chat message.</span></span> <span data-ttu-id="6dfa2-165">Seu usuário e todos os outros usuários em um canal podem ver a resposta do botão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-165">Your user and all other users in a channel can see the button response.</span></span>

<span data-ttu-id="6dfa2-166">Com `imBack` , você pode criar uma ação com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-166">With `imBack`, you can create an action with the following properties:</span></span>

| <span data-ttu-id="6dfa2-167">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6dfa2-167">Property</span></span> | <span data-ttu-id="6dfa2-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfa2-168">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="6dfa2-169">Aparece como o rótulo do botão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-169">Appears as the button label.</span></span> |
| `value` | <span data-ttu-id="6dfa2-170">Esse campo deve conter a cadeia de caracteres de texto usada no chat e, portanto, enviada de volta para o bot.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-170">This field must contain the text string used in the chat and therefore sent back to the bot.</span></span> <span data-ttu-id="6dfa2-171">Este é o texto da mensagem que você processa em seu bot para executar a lógica desejada.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-171">This is the message text you process in your bot to perform the desired logic.</span></span> |

> [!NOTE]
> <span data-ttu-id="6dfa2-172">O `value` campo é uma cadeia de caracteres simples.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-172">The `value` field is a simple string.</span></span> <span data-ttu-id="6dfa2-173">Não há suporte para formatação ou caracteres ocultos.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-173">There is no support for formatting or hidden characters.</span></span>

# <a name="json"></a>[<span data-ttu-id="6dfa2-174">JSON</span><span class="sxs-lookup"><span data-stu-id="6dfa2-174">JSON</span></span>](#tab/json)

<span data-ttu-id="6dfa2-175">O código a seguir mostra um exemplo de `imBack` tipo de ação em JSON:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-175">The following code shows an example of `imBack` action type in JSON:</span></span>

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

# <a name="c"></a>[<span data-ttu-id="6dfa2-176">C#</span><span class="sxs-lookup"><span data-stu-id="6dfa2-176">C#</span></span>](#tab/csharp)

<span data-ttu-id="6dfa2-177">O código a seguir mostra um exemplo de `imBack` tipo de ação C#:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-177">The following code shows an example of `imBack` action type in C#:</span></span>

```csharp
var button = new CardAction()
{
    Type = ActionTypes.ImBack,
    Title = "More",
    Value = "Show me more"
};
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="6dfa2-178">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="6dfa2-178">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="6dfa2-179">O código a seguir mostra um exemplo de `imBack` tipo de ação em JavaScript:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-179">The following code shows an example of `imBack` action type in JavaScript:</span></span>

```javascript
CardFactory.actions([
{
    type: "imBack",
    title: "More",
    value: "Show me more"
}])
```

---

## <a name="action-type-invoke"></a><span data-ttu-id="6dfa2-180">Tipo de ação invocar</span><span class="sxs-lookup"><span data-stu-id="6dfa2-180">Action type invoke</span></span>

<span data-ttu-id="6dfa2-181">A `invoke` ação é usada para invocar [módulos de tarefa](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span><span class="sxs-lookup"><span data-stu-id="6dfa2-181">The `invoke` action is used for invoking [task modules](~/task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="6dfa2-182">A `invoke` ação contém três `type` propriedades, , e `title` `value` .</span><span class="sxs-lookup"><span data-stu-id="6dfa2-182">The `invoke` action contains three properties, `type`, `title`, and `value`.</span></span>

<span data-ttu-id="6dfa2-183">Com `invoke` , você pode criar uma ação com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-183">With `invoke`, you can create an action with the following properties:</span></span>

| <span data-ttu-id="6dfa2-184">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6dfa2-184">Property</span></span> | <span data-ttu-id="6dfa2-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfa2-185">Description</span></span> |
| --- | --- |
| `title` | <span data-ttu-id="6dfa2-186">Aparece como o rótulo do botão.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-186">Appears as the button label.</span></span> |
| `value` | <span data-ttu-id="6dfa2-187">Essa propriedade pode conter uma cadeia de caracteres, um objeto JSON stringified ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-187">This property can contain a string, a stringified JSON object, or a JSON object.</span></span> |

# <a name="json"></a>[<span data-ttu-id="6dfa2-188">JSON</span><span class="sxs-lookup"><span data-stu-id="6dfa2-188">JSON</span></span>](#tab/json)

<span data-ttu-id="6dfa2-189">O código a seguir mostra um exemplo de `invoke` tipo de ação em JSON:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-189">The following code shows an example of `invoke` action type in JSON:</span></span>

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

<span data-ttu-id="6dfa2-190">Quando um usuário seleciona o botão, seu bot recebe o `value` objeto com algumas informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-190">When a user selects the button, your bot receives the `value` object with some additional information.</span></span>

> [!NOTE]
> <span data-ttu-id="6dfa2-191">O tipo de atividade `invoke` é, em vez `message` disso, `activity.Type == "invoke"` é .</span><span class="sxs-lookup"><span data-stu-id="6dfa2-191">The activity type is `invoke` instead of `message` that is `activity.Type == "invoke"`.</span></span>

# <a name="c"></a>[<span data-ttu-id="6dfa2-192">C#</span><span class="sxs-lookup"><span data-stu-id="6dfa2-192">C#</span></span>](#tab/csharp)

<span data-ttu-id="6dfa2-193">O código a seguir mostra um exemplo de `invoke` tipo de ação C#:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-193">The following code shows an example of `invoke` action type in C#:</span></span>

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="6dfa2-194">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="6dfa2-194">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="6dfa2-195">O código a seguir mostra um exemplo de `invoke` tipo de ação Node.js:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-195">The following code shows an example of `invoke` action type in Node.js:</span></span>

```javascript
CardFactory.actions([
{
    type: "invoke",
    title: "Option 1",
    value: {
        option: "opt1"
    }
}])
```

---

### <a name="example-of-incoming-invoke-message"></a><span data-ttu-id="6dfa2-196">Exemplo de mensagem de invocação de entrada</span><span class="sxs-lookup"><span data-stu-id="6dfa2-196">Example of incoming invoke message</span></span>

<span data-ttu-id="6dfa2-197">A propriedade de nível superior contém a ID da mensagem de onde a `replyToId` ação do cartão veio.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-197">The top-level `replyToId` property contains the ID of the message that the card action came from.</span></span> <span data-ttu-id="6dfa2-198">Use-o se quiser atualizar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-198">Use it if you want to update the message.</span></span>

<span data-ttu-id="6dfa2-199">O código a seguir mostra um exemplo de mensagem de chamada de entrada:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-199">The following code shows an example of incoming invoke message:</span></span>

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

## <a name="action-type-signin"></a><span data-ttu-id="6dfa2-200">Signin do tipo de ação</span><span class="sxs-lookup"><span data-stu-id="6dfa2-200">Action type signin</span></span>

<span data-ttu-id="6dfa2-201">`signin` tipo de ação inicia um fluxo OAuth que permite que os bots se conectem com serviços seguros.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-201">`signin` action type initiates an OAuth flow that permits bots to connect with secure services.</span></span> <span data-ttu-id="6dfa2-202">Para obter mais informações, consulte [fluxo de autenticação em bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="6dfa2-202">For more information, see [authentication flow in bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

<span data-ttu-id="6dfa2-203">Teams também oferece suporte [a ações de Cartões Adaptáveis](#adaptive-cards-actions) que são usadas apenas por Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-203">Teams also supports [Adaptive Cards actions](#adaptive-cards-actions) that are only used by Adaptive Cards.</span></span>

# <a name="json"></a>[<span data-ttu-id="6dfa2-204">JSON</span><span class="sxs-lookup"><span data-stu-id="6dfa2-204">JSON</span></span>](#tab/json)

<span data-ttu-id="6dfa2-205">O código a seguir mostra um exemplo de `signin` tipo de ação em JSON:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-205">The following code shows an example of `signin` action type in JSON:</span></span>

```json
{
"type": "signin",
"title": "Click me for signin",
"value": "https://signin.com"
}
```

# <a name="c"></a>[<span data-ttu-id="6dfa2-206">C#</span><span class="sxs-lookup"><span data-stu-id="6dfa2-206">C#</span></span>](#tab/csharp)

<span data-ttu-id="6dfa2-207">O código a seguir mostra um exemplo de `signin` tipo de ação C#:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-207">The following code shows an example of `signin` action type in C#:</span></span>

```csharp
var button = new CardAction()
{
    Type = ActionTypes.Signin,
    Title = "Click me for signin",
    Value = "https://signin.com"
};
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="6dfa2-208">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="6dfa2-208">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="6dfa2-209">O código a seguir mostra um exemplo de `signin` tipo de ação em JavaScript:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-209">The following code shows an example of `signin` action type in JavaScript:</span></span>

```javascript
CardFactory.actions([
{
    type: "signin",
    title: "Click me for signin",
    value: "https://signin.com"
}])
```

---

## <a name="adaptive-cards-actions"></a><span data-ttu-id="6dfa2-210">Ações de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="6dfa2-210">Adaptive Cards actions</span></span>

<span data-ttu-id="6dfa2-211">Os Cartões Adaptáveis suportam quatro tipos de ação:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-211">Adaptive Cards support four action types:</span></span>

* [<span data-ttu-id="6dfa2-212">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="6dfa2-212">Action.OpenUrl</span></span>](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [<span data-ttu-id="6dfa2-213">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="6dfa2-213">Action.Submit</span></span>](http://adaptivecards.io/explorer/Action.Submit.html)
* [<span data-ttu-id="6dfa2-214">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="6dfa2-214">Action.ShowCard</span></span>](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [<span data-ttu-id="6dfa2-215">Action.Exebonito</span><span class="sxs-lookup"><span data-stu-id="6dfa2-215">Action.Execute</span></span>](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

<span data-ttu-id="6dfa2-216">Você também pode modificar a carga cartão adaptável para dar suporte a ações existentes da Estrutura de Bot usando uma propriedade `Action.Submit` `msteams` no objeto de `data` `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="6dfa2-216">You can also modify the Adaptive Card `Action.Submit` payload to support existing Bot Framework actions using an `msteams` property in the `data` object of `Action.Submit`.</span></span> <span data-ttu-id="6dfa2-217">A próxima seção fornece detalhes sobre como usar ações da Estrutura de Bot existentes com Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-217">The next section provide details on how to use existing Bot Framework actions with Adaptive Cards.</span></span>

> [!NOTE]
> <span data-ttu-id="6dfa2-218">Adicionar aos dados com uma ação da Estrutura de Bot não funciona com um módulo de tarefa `msteams` cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-218">Adding `msteams` to data with a Bot Framework action does not work with an Adaptive Card task module.</span></span>

### <a name="adaptive-cards-with-messageback-action"></a><span data-ttu-id="6dfa2-219">Cartões Adaptáveis com ação messageBack</span><span class="sxs-lookup"><span data-stu-id="6dfa2-219">Adaptive Cards with messageBack action</span></span>

<span data-ttu-id="6dfa2-220">Para incluir uma `messageBack` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-220">To include a `messageBack` action with an Adaptive Card include the following details in the `msteams` object:</span></span>

> [!NOTE]
> <span data-ttu-id="6dfa2-221">Você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-221">You can include additional hidden properties in the `data` object, if required.</span></span>

| <span data-ttu-id="6dfa2-222">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6dfa2-222">Property</span></span> | <span data-ttu-id="6dfa2-223">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfa2-223">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="6dfa2-224">Definir como `messageBack` .</span><span class="sxs-lookup"><span data-stu-id="6dfa2-224">Set to `messageBack`.</span></span> |
| `displayText` | <span data-ttu-id="6dfa2-225">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-225">Optional.</span></span> <span data-ttu-id="6dfa2-226">Usado pelo usuário no fluxo de chat quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-226">Used by the user in the chat stream when the action is performed.</span></span> <span data-ttu-id="6dfa2-227">Este texto não é enviado para seu bot.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-227">This text is not sent to your bot.</span></span> |
| `value` | <span data-ttu-id="6dfa2-228">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-228">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="6dfa2-229">Você pode codificar contexto para a ação, como identificadores exclusivos ou um objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-229">You can encode context for the action, such as unique identifiers or a JSON object.</span></span> |
| `text` | <span data-ttu-id="6dfa2-230">Enviado ao bot quando a ação é executada.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-230">Sent to your bot when the action is performed.</span></span> <span data-ttu-id="6dfa2-231">Use essa propriedade para simplificar o desenvolvimento de bots.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-231">Use this property to simplify bot development.</span></span> <span data-ttu-id="6dfa2-232">Seu código pode verificar uma única propriedade de nível superior para despachar a lógica do bot.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-232">Your code can check a single top-level property to dispatch bot logic.</span></span> |

<span data-ttu-id="6dfa2-233">O código a seguir mostra um exemplo de Cartões Adaptáveis com `messageBack` ação:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-233">The following code shows an example of Adaptive Cards with `messageBack` action:</span></span>

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

### <a name="adaptive-cards-with-imback-action"></a><span data-ttu-id="6dfa2-234">Cartões Adaptáveis com ação imBack</span><span class="sxs-lookup"><span data-stu-id="6dfa2-234">Adaptive Cards with imBack action</span></span>

<span data-ttu-id="6dfa2-235">Para incluir uma `imBack` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-235">To include an `imBack` action with an Adaptive Card include the following details in the `msteams` object:</span></span>

> [!NOTE]
> <span data-ttu-id="6dfa2-236">Você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-236">You can include additional hidden properties in the `data` object, if required.</span></span>

| <span data-ttu-id="6dfa2-237">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6dfa2-237">Property</span></span> | <span data-ttu-id="6dfa2-238">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfa2-238">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="6dfa2-239">Definir como `imBack` .</span><span class="sxs-lookup"><span data-stu-id="6dfa2-239">Set to `imBack`.</span></span> |
| `value` | <span data-ttu-id="6dfa2-240">Cadeia de caracteres que precisa ser ecoada novamente no chat.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-240">String that needs to be echoed back in the chat.</span></span> |

<span data-ttu-id="6dfa2-241">O código a seguir mostra um exemplo de Cartões Adaptáveis com `imBack` ação:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-241">The following code shows an example of Adaptive Cards with `imBack` action:</span></span>

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

### <a name="adaptive-cards-with-signin-action"></a><span data-ttu-id="6dfa2-242">Cartões Adaptáveis com ação de signin</span><span class="sxs-lookup"><span data-stu-id="6dfa2-242">Adaptive Cards with signin action</span></span>

<span data-ttu-id="6dfa2-243">Para incluir uma `signin` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-243">To include a `signin` action with an Adaptive Card include the following details in the `msteams` object:</span></span>

> [!NOTE]
> <span data-ttu-id="6dfa2-244">Você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-244">You can include additional hidden properties in the `data` object, if required.</span></span>

| <span data-ttu-id="6dfa2-245">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6dfa2-245">Property</span></span> | <span data-ttu-id="6dfa2-246">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfa2-246">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="6dfa2-247">Definir como `signin` .</span><span class="sxs-lookup"><span data-stu-id="6dfa2-247">Set to `signin`.</span></span> |
| `value` | <span data-ttu-id="6dfa2-248">De acordo com a URL para a qual você deseja redirecionar.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-248">Set to the URL where you want to redirect.</span></span>  |

<span data-ttu-id="6dfa2-249">O código a seguir mostra um exemplo de Cartões Adaptáveis com `signin` ação:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-249">The following code shows an example of Adaptive Cards with `signin` action:</span></span>

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

### <a name="adaptive-cards-with-invoke-action"></a><span data-ttu-id="6dfa2-250">Cartões Adaptáveis com ação de invocação</span><span class="sxs-lookup"><span data-stu-id="6dfa2-250">Adaptive Cards with invoke action</span></span>

<span data-ttu-id="6dfa2-251">Para incluir uma `invoke` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-251">To include an `invoke` action with an Adaptive Card include the following details in the `msteams` object:</span></span>

> [!NOTE]
> <span data-ttu-id="6dfa2-252">Você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-252">You can include additional hidden properties in the `data` object, if required.</span></span>

| <span data-ttu-id="6dfa2-253">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6dfa2-253">Property</span></span> | <span data-ttu-id="6dfa2-254">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfa2-254">Description</span></span> |
| --- | --- |
| `type` | <span data-ttu-id="6dfa2-255">Definir como `task/fetch` .</span><span class="sxs-lookup"><span data-stu-id="6dfa2-255">Set to `task/fetch`.</span></span> |
| `data` | <span data-ttu-id="6dfa2-256">De definir o valor.</span><span class="sxs-lookup"><span data-stu-id="6dfa2-256">Set the value.</span></span>  |

<span data-ttu-id="6dfa2-257">O código a seguir mostra um exemplo de Cartões Adaptáveis com `invoke` ação:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-257">The following code shows an example of Adaptive Cards with `invoke` action:</span></span>

```json
{
  "type": "Action.Submit",
  "title": "submit",
  "data": {
    "msteams": {
        "type": "task/fetch"
    }
  }
}
```

<span data-ttu-id="6dfa2-258">O código a seguir mostra um exemplo de Cartões Adaptáveis com `invoke` ação com dados de carga adicionais:</span><span class="sxs-lookup"><span data-stu-id="6dfa2-258">The following code shows an example of Adaptive Cards with `invoke` action with additional payload data:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6dfa2-259">Confira também</span><span class="sxs-lookup"><span data-stu-id="6dfa2-259">See also</span></span>

[<span data-ttu-id="6dfa2-260">Referência de cartões</span><span class="sxs-lookup"><span data-stu-id="6dfa2-260">Cards reference</span></span>](./cards-reference.md)

## <a name="next-step"></a><span data-ttu-id="6dfa2-261">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="6dfa2-261">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6dfa2-262">Ações Universais para Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="6dfa2-262">Universal Actions for Adaptive Cards</span></span>](../cards/Universal-actions-for-adaptive-cards/Overview.md)
