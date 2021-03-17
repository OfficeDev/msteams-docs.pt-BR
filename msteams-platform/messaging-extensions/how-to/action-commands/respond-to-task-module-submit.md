---
title: Responder à ação de envio do módulo de tarefas
author: clearab
description: Descreve como responder à ação de envio do módulo de tarefa de um comando de ação de extensão de mensagens
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: fecc0ace5f767da3764529a9e8a590b37e547bb0
ms.sourcegitcommit: 1ce74ed167bb81bf09f7f6f8d518093efafb549e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2021
ms.locfileid: "50827939"
---
# <a name="respond-to-the-task-module-submit-action"></a><span data-ttu-id="7cb66-103">Responder à ação de envio do módulo de tarefas</span><span class="sxs-lookup"><span data-stu-id="7cb66-103">Respond to the task module submit action</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="7cb66-104">Depois que um usuário envia o módulo de tarefa, seu serviço Web recebe uma mensagem de invocação com a ID de comando e os valores `composeExtension/submitAction` de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7cb66-104">After a user submits the task module, your web service receives a `composeExtension/submitAction` invoke message with the command ID and parameter values.</span></span> <span data-ttu-id="7cb66-105">Seu aplicativo tem cinco segundos para responder à invocação,  caso contrário, o usuário recebe uma mensagem de erro Não é possível alcançar o aplicativo e qualquer resposta à invocação é ignorada pelo cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="7cb66-105">Your app has five seconds to respond to the invoke, otherwise the user receives an error message **Unable to reach the app** and any reply to the invoke is ignored by the Teams client.</span></span>

<span data-ttu-id="7cb66-106">Você tem as seguintes opções para responder:</span><span class="sxs-lookup"><span data-stu-id="7cb66-106">You have the following options for responding:</span></span>

* <span data-ttu-id="7cb66-107">Sem resposta - Você pode optar por usar a ação enviar para disparar um processo em um sistema externo e não fornecer comentários ao usuário.</span><span class="sxs-lookup"><span data-stu-id="7cb66-107">No response - You can choose to use the submit action to trigger a process in an external system, and not provide any feedback to the user.</span></span> <span data-ttu-id="7cb66-108">Isso pode ser útil para processos de longa duração e você pode optar por fornecer comentários de outra maneira (por exemplo, com uma [mensagem proativa](~/bots/how-to/conversations/send-proactive-messages.md).</span><span class="sxs-lookup"><span data-stu-id="7cb66-108">This can be useful for long-running processes, and you may choose to provide feedback in another manner (for example, with a [proactive message](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>
* <span data-ttu-id="7cb66-109">[Outro módulo de](#respond-with-another-task-module) tarefa - Você pode responder com um módulo de tarefa adicional como parte de uma interação em várias etapas.</span><span class="sxs-lookup"><span data-stu-id="7cb66-109">[Another task module](#respond-with-another-task-module) - You can respond with an additional task module as part of a multi-step interaction.</span></span>
* <span data-ttu-id="7cb66-110">[Resposta de](#respond-with-a-card-inserted-into-the-compose-message-area) cartão - Você pode responder com um cartão com o que o usuário pode interagir e/ou inserir em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="7cb66-110">[Card response](#respond-with-a-card-inserted-into-the-compose-message-area) - You can respond with a card that the user can then interact with and/or insert into a message.</span></span>
* <span data-ttu-id="7cb66-111">[Cartão Adaptável do bot](#bot-response-with-adaptive-card) - Insira um Cartão Adaptável diretamente na conversa.</span><span class="sxs-lookup"><span data-stu-id="7cb66-111">[Adaptive Card from bot](#bot-response-with-adaptive-card) - Insert an Adaptive Card directly into the conversation.</span></span>
* [<span data-ttu-id="7cb66-112">Solicitar a autenticação do usuário</span><span class="sxs-lookup"><span data-stu-id="7cb66-112">Request the user authenticate</span></span>](~/messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="7cb66-113">Solicitar que o usuário forneça configuração adicional</span><span class="sxs-lookup"><span data-stu-id="7cb66-113">Request the user provide additional configuration</span></span>](~/messaging-extensions/how-to/add-configuration-page.md)

<span data-ttu-id="7cb66-114">Para autenticação ou configuração, depois que o usuário concluir o fluxo, a invocação original será re-enviada ao seu serviço Web.</span><span class="sxs-lookup"><span data-stu-id="7cb66-114">For authentication or configuration, after the user completes the flow the original invoke is re-sent to your web service.</span></span> <span data-ttu-id="7cb66-115">A tabela a seguir mostra quais tipos de respostas estão disponíveis com base no local de `commandContext` invocação da extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="7cb66-115">The following table shows which types of responses are available based on the invoke location `commandContext` of the messaging extension:</span></span> 

|<span data-ttu-id="7cb66-116">Tipo de resposta</span><span class="sxs-lookup"><span data-stu-id="7cb66-116">Response Type</span></span> | <span data-ttu-id="7cb66-117">compose</span><span class="sxs-lookup"><span data-stu-id="7cb66-117">compose</span></span> | <span data-ttu-id="7cb66-118">barra de comandos</span><span class="sxs-lookup"><span data-stu-id="7cb66-118">command bar</span></span> | <span data-ttu-id="7cb66-119">mensagem</span><span class="sxs-lookup"><span data-stu-id="7cb66-119">message</span></span> |
|--------------|:-------------:|:-------------:|:---------:|
|<span data-ttu-id="7cb66-120">Resposta de cartão</span><span class="sxs-lookup"><span data-stu-id="7cb66-120">Card response</span></span> | <span data-ttu-id="7cb66-121">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-121">x</span></span> | <span data-ttu-id="7cb66-122">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-122">x</span></span> | <span data-ttu-id="7cb66-123">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-123">x</span></span> |
|<span data-ttu-id="7cb66-124">Outro módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="7cb66-124">Another task module</span></span> | <span data-ttu-id="7cb66-125">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-125">x</span></span> | <span data-ttu-id="7cb66-126">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-126">x</span></span> | <span data-ttu-id="7cb66-127">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-127">x</span></span> |
|<span data-ttu-id="7cb66-128">Bot com Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="7cb66-128">Bot with Adaptive Card</span></span> | <span data-ttu-id="7cb66-129">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-129">x</span></span> |  | <span data-ttu-id="7cb66-130">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-130">x</span></span> |
| <span data-ttu-id="7cb66-131">Sem resposta</span><span class="sxs-lookup"><span data-stu-id="7cb66-131">No response</span></span> | <span data-ttu-id="7cb66-132">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-132">x</span></span> | <span data-ttu-id="7cb66-133">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-133">x</span></span> | <span data-ttu-id="7cb66-134">x</span><span class="sxs-lookup"><span data-stu-id="7cb66-134">x</span></span> |

> [!NOTE]
> * <span data-ttu-id="7cb66-135">Quando você seleciona **Action.Submit** through ME cards, ele envia atividades invocadas com o nome **composeExtension**, onde o valor é igual à carga normal.</span><span class="sxs-lookup"><span data-stu-id="7cb66-135">When you select **Action.Submit** through ME cards, it sends invoke activity with the name **composeExtension**, where the value is equal to the usual payload.</span></span>
> * <span data-ttu-id="7cb66-136">Quando você seleciona **Action.Submit** por meio de conversa, recebe atividade de mensagem com o nome **onCardButtonClicked**, onde o valor é igual à carga normal.</span><span class="sxs-lookup"><span data-stu-id="7cb66-136">When you select **Action.Submit** through conversation, you receive message activity with the name **onCardButtonClicked**, where the value is equal to the usual payload.</span></span>

## <a name="the-submitaction-invoke-event"></a><span data-ttu-id="7cb66-137">O evento invoke submitAction</span><span class="sxs-lookup"><span data-stu-id="7cb66-137">The submitAction invoke event</span></span>

<span data-ttu-id="7cb66-138">Os exemplos de recebimento da mensagem de invocação são:</span><span class="sxs-lookup"><span data-stu-id="7cb66-138">Examples of receiving the invoke message are as follows:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7cb66-139">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7cb66-139">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken) {
  //code to handle the submit action
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="7cb66-140">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7cb66-140">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  constructor() {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
  
  //code to handle the submit action
    }
  }
}
```

# <a name="json"></a>[<span data-ttu-id="7cb66-141">JSON</span><span class="sxs-lookup"><span data-stu-id="7cb66-141">JSON</span></span>](#tab/json)

<span data-ttu-id="7cb66-142">Este é um exemplo do objeto JSON que você recebe.</span><span class="sxs-lookup"><span data-stu-id="7cb66-142">This is an example of the JSON object you receive.</span></span> <span data-ttu-id="7cb66-143">O parâmetro indica de onde a extensão de mensagens `commandContext` foi disparada.</span><span class="sxs-lookup"><span data-stu-id="7cb66-143">The `commandContext` parameter indicates where your messaging extension was triggered from.</span></span> <span data-ttu-id="7cb66-144">O `data` objeto contém os campos no formulário como parâmetros e os valores enviados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7cb66-144">The `data` object contains the fields on the form as parameters, and the values the user submitted.</span></span> <span data-ttu-id="7cb66-145">O objeto JSON aqui é reduzido para realçar os campos mais relevantes.</span><span class="sxs-lookup"><span data-stu-id="7cb66-145">The JSON object here is shortened to highlight the most relevant fields.</span></span>

```json
{
  "name": "composeExtension/submitAction",
  "imdisplayname": "Bob Smith",
  "serviceUrl": "https://smba.trafficmanager.net/amer/",
  "value": {
    "commandId": "giveKudos",
    "commandContext": "compose",
    "context": {
      "theme": "default"
    },
    "data": {
      "id": "submitButton",
      "formField1": "formField1_value",
      "formField2": "formField2_value",
      "formField3": "formField3_value"
    }
  },
  "conversation": {
    "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
  }
}
```

* * *

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a><span data-ttu-id="7cb66-146">Responder com um cartão inserido na área de mensagem de composição</span><span class="sxs-lookup"><span data-stu-id="7cb66-146">Respond with a card inserted into the compose message area</span></span>

<span data-ttu-id="7cb66-147">A maneira mais comum de responder à solicitação `composeExtension/submitAction` é com um cartão inserido na área de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="7cb66-147">The most common way to respond to the `composeExtension/submitAction` request is with a card inserted into the compose message area.</span></span> <span data-ttu-id="7cb66-148">Em seguida, o usuário pode optar por enviar o cartão para a conversa.</span><span class="sxs-lookup"><span data-stu-id="7cb66-148">The user can then choose to submit the card to the conversation.</span></span> <span data-ttu-id="7cb66-149">Para obter mais informações sobre como usar cartões, consulte [cartões e ações de cartão.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="7cb66-149">For more information on using cards see [cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7cb66-150">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7cb66-150">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
    var response = new MessagingExtensionActionResponse
    {
        ComposeExtension = new MessagingExtensionResult
        {
            AttachmentLayout = "list",
            Type = "result",
        },
    };
    var createCardData = ((JObject)action.Data).ToObject<CreateCardData>();
var card = new HeroCard
{
     Title = createCardData.Title,
     Subtitle = createCardData.Subtitle,
     Text = createCardData.Text,
};
    var attachments = new List<MessagingExtensionAttachment>();
    attachments.Add(new MessagingExtensionAttachment
    {
        Content = card,
        ContentType = HeroCard.ContentType,
        Preview = card.ToAttachment(),
    });
    response.ComposeExtension.Attachments = attachments;
    return response;
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="7cb66-151">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7cb66-151">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
    const data = action.data;
    const heroCard = CardFactory.heroCard(data.title, data.text);
    heroCard.content.subtitle = data.subTitle;
    const attachment = { contentType: heroCard.contentType, content: heroCard.content, preview: heroCard };

    return {
      composeExtension: {
        type: 'result',
        attachmentLayout: 'list',
        attachments: [
          attachment
        ]
      }
    }
  }
}
```

# <a name="json"></a>[<span data-ttu-id="7cb66-152">JSON</span><span class="sxs-lookup"><span data-stu-id="7cb66-152">JSON</span></span>](#tab/json)

```json
{
  "composeExtension": {
    "attachmentLayout": "list",
    "type": "result",
    "attachments": [
      {
        "preview": {
          "contentType": "application/vnd.microsoft.card.hero",
          "content": {
            "title": "formField1_value",
            "subtitle": "formField2_value",
            "text": "formField3_value"
          }
        },
        "contentType": "application/vnd.microsoft.card.hero",
        "content": {
          "title": "formField1_value",
          "subtitle": "formField2_value",
          "text": "formField3_value"
        }
      }
    ]
  }
}
```

* * *

## <a name="respond-with-another-task-module"></a><span data-ttu-id="7cb66-153">Responder com outro módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="7cb66-153">Respond with another task module</span></span>

<span data-ttu-id="7cb66-154">Você pode optar por responder ao `submitAction` evento com um módulo de tarefa adicional.</span><span class="sxs-lookup"><span data-stu-id="7cb66-154">You can choose to respond to the `submitAction` event with an additional task module.</span></span> <span data-ttu-id="7cb66-155">Isso pode ser útil quando:</span><span class="sxs-lookup"><span data-stu-id="7cb66-155">This can be useful when:</span></span>

* <span data-ttu-id="7cb66-156">Você precisa coletar grandes quantidades de informações.</span><span class="sxs-lookup"><span data-stu-id="7cb66-156">You need to collect large amounts of information.</span></span>
* <span data-ttu-id="7cb66-157">Se você precisar alterar dinamicamente quais informações você está coletando com base na entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="7cb66-157">If you need to dynamically change what information you are collecting based on user input</span></span>
* <span data-ttu-id="7cb66-158">Se você precisar validar as informações enviadas pelo usuário e potencialmente resendá-lo com uma mensagem de erro se algo estiver errado.</span><span class="sxs-lookup"><span data-stu-id="7cb66-158">If you need to validate the information submitted by the user and potentially resend the form with an error message if something is wrong.</span></span> 

<span data-ttu-id="7cb66-159">O método de resposta é o mesmo que [responder ao evento `fetchTask` inicial](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span><span class="sxs-lookup"><span data-stu-id="7cb66-159">The method for response is the same as [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span></span> <span data-ttu-id="7cb66-160">Se você estiver usando o SDK da Estrutura de Bots, o mesmo evento dispara para ambas as ações de envio.</span><span class="sxs-lookup"><span data-stu-id="7cb66-160">If you are using the Bot Framework SDK the same event triggers for both submit actions.</span></span> <span data-ttu-id="7cb66-161">Isso significa que você deve adicionar lógica que determina a resposta correta.</span><span class="sxs-lookup"><span data-stu-id="7cb66-161">This means you must add logic which determines the correct response.</span></span>

## <a name="bot-response-with-adaptive-card"></a><span data-ttu-id="7cb66-162">Resposta bot com Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="7cb66-162">Bot response with Adaptive Card</span></span>

>[!Note]
><span data-ttu-id="7cb66-163">Esse fluxo exige que você adicione o objeto ao manifesto do aplicativo e que você `bot` tenha o escopo necessário definido para o bot.</span><span class="sxs-lookup"><span data-stu-id="7cb66-163">This flow requires that you add the `bot` object to your app manifest, and that you have the necessary scope defined for the bot.</span></span> <span data-ttu-id="7cb66-164">Use a mesma ID da extensão de mensagens do bot.</span><span class="sxs-lookup"><span data-stu-id="7cb66-164">Use the same ID as your messaging extension for your bot.</span></span>

<span data-ttu-id="7cb66-165">Você também pode responder à ação enviar inserindo uma mensagem com um Cartão Adaptável no canal com um bot.</span><span class="sxs-lookup"><span data-stu-id="7cb66-165">You can also respond to the submit action by inserting a message with an Adaptive Card into the channel with a bot.</span></span> <span data-ttu-id="7cb66-166">O usuário pode visualizar a mensagem antes de enviar e, potencialmente, editar ou interagir com ela também.</span><span class="sxs-lookup"><span data-stu-id="7cb66-166">Your user can preview the message before submitting it, and potentially edit or interact with it as well.</span></span> <span data-ttu-id="7cb66-167">Isso pode ser muito útil em cenários em que você coleta informações de seus usuários antes de criar uma resposta de cartão adaptável ou quando você atualiza o cartão depois que alguém interage com ele.</span><span class="sxs-lookup"><span data-stu-id="7cb66-167">This can be very useful in scenarios where you gather information from your users before creating an adaptive card response, or when you update the card after someone interacts with it.</span></span> <span data-ttu-id="7cb66-168">O cenário a seguir mostra como o aplicativo Polly usa esse fluxo para configurar uma sondagem sem incluir as etapas de configuração na conversa do canal:</span><span class="sxs-lookup"><span data-stu-id="7cb66-168">The following scenario shows how the app Polly uses this flow to configure a poll without including the configuration steps in the channel conversation:</span></span>

1. <span data-ttu-id="7cb66-169">O usuário seleciona a extensão de mensagens para disparar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="7cb66-169">The user selects the messaging extension to trigger the task module.</span></span>
2. <span data-ttu-id="7cb66-170">O usuário configura a sondagem com o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="7cb66-170">The user configures the poll with the task module.</span></span>
3. <span data-ttu-id="7cb66-171">Depois de enviar o módulo de tarefas, o aplicativo usa as informações fornecidas para criar a sondagem como um Cartão Adaptável e a envia como uma resposta `botMessagePreview` ao cliente.</span><span class="sxs-lookup"><span data-stu-id="7cb66-171">After submitting the task module the app uses the information provided to build the poll as an Adaptive Card and sends it as a `botMessagePreview` response to the client.</span></span>
4. <span data-ttu-id="7cb66-172">Em seguida, o usuário pode visualizar a mensagem de cartão adaptável antes que o bot a insere no canal.</span><span class="sxs-lookup"><span data-stu-id="7cb66-172">The user can then preview the adaptive card message before the bot inserts it into the channel.</span></span> <span data-ttu-id="7cb66-173">Se o aplicativo ainda não for membro do canal, a seleção `Send` o adiciona.</span><span class="sxs-lookup"><span data-stu-id="7cb66-173">If the app is not already a member of the channel, selecting `Send` adds it.</span></span>
   1. <span data-ttu-id="7cb66-174">O usuário também pode escolher `Edit` a mensagem, que retorna para o módulo de tarefa original.</span><span class="sxs-lookup"><span data-stu-id="7cb66-174">The user can also choose to `Edit` the message, which returns them to the original task module.</span></span>
5. <span data-ttu-id="7cb66-175">Interagir com o cartão adaptável altera a mensagem antes de enviá-la.</span><span class="sxs-lookup"><span data-stu-id="7cb66-175">Interacting with the adaptive card changes the message before sending it.</span></span>
6. <span data-ttu-id="7cb66-176">Depois que o usuário selecionar `Send` o bot, poste a mensagem no canal.</span><span class="sxs-lookup"><span data-stu-id="7cb66-176">After the user selects `Send` the bot posts the message to the channel.</span></span>

### <a name="respond-to-initial-submit-action"></a><span data-ttu-id="7cb66-177">Responder à ação inicial de envio</span><span class="sxs-lookup"><span data-stu-id="7cb66-177">Respond to initial submit action</span></span>

<span data-ttu-id="7cb66-178">Para habilitar esse fluxo, seu módulo de tarefa deve responder à mensagem inicial com uma visualização do `composeExtension/submitAction` cartão que o bot envia para o canal.</span><span class="sxs-lookup"><span data-stu-id="7cb66-178">To enable this flow your task module should respond to the initial `composeExtension/submitAction` message with a preview of the card that the bot send to the channel.</span></span> <span data-ttu-id="7cb66-179">Isso oferece ao usuário a oportunidade de verificar o cartão antes de enviar e também tentar instalar seu bot na conversa se ele ainda não estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="7cb66-179">This gives the user the opportunity to verify the card before sending, and also attempt to install your bot in the conversation if it is not already installed.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7cb66-180">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7cb66-180">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  dynamic createCardData = ((JObject) action.Data).ToObject(typeof(JObject));
  var response = new MessagingExtensionActionResponse
  {
    ComposeExtension = new MessagingExtensionResult
    {
      Type = "botMessagePreview",
      ActivityPreview = MessageFactory.Attachment(new Attachment
      {
        Content = new AdaptiveCard("1.0")
        {
          Body = new List<AdaptiveElement>()
          {
            new AdaptiveTextBlock() { Text = "FormField1 value was:", Size = AdaptiveTextSize.Large },
            new AdaptiveTextBlock() { Text = Data["FormField1"] as string }
          },
          Height = AdaptiveHeight.Auto,
          Actions = new List<AdaptiveAction>()
          {
            new AdaptiveSubmitAction
            {
              Type = AdaptiveSubmitAction.TypeName,
              Title = "Submit",
              Data = new JObject { { "submitLocation", "messagingExtensionFetchTask" } },
            },
          }
        },
        ContentType = AdaptiveCard.ContentType
      }) as Activity
    }
  };

  return response;
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="7cb66-181">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7cb66-181">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
    const submittedData = action.data;
    const adaptiveCard = CardFactory.adaptiveCard({
      actions: [
        { type: 'Action.Submit', title: 'Submit', data: { submitLocation: 'messagingExtensionSubmit' } }
      ],
      body: [
          { text: 'Adaptive Card from Task Module', type: 'TextBlock', weight: 'bolder' },
          { text: `${ submittedData.Question }`, type: 'TextBlock', id: 'Question' },
          { id: 'Answer', placeholder: 'Answer here...', type: 'Input.Text' },
        {
          choices: [
            { title: submittedData.Option1, value: submittedData.Option1 },
            { title: submittedData.Option2, value: submittedData.Option2 },
            { title: submittedData.Option3, value: submittedData.Option3 }
          ],
          id: 'Choices',
          isMultiSelect: submittedData.MultiSelect,
          style: 'expanded',
          type: 'Input.ChoiceSet'
        }
      ],
      type: 'AdaptiveCard',
      version: '1.0'
    });
    return {
      composeExtension: {
        activityPreview: MessageFactory.attachment(adaptiveCard, null, null, InputHints.ExpectingInput),
        type: 'botMessagePreview'
      }
    };
  }
}
```

# <a name="json"></a>[<span data-ttu-id="7cb66-182">JSON</span><span class="sxs-lookup"><span data-stu-id="7cb66-182">JSON</span></span>](#tab/json)

>[!Note]
><span data-ttu-id="7cb66-183">O `activityPreview` deve conter uma atividade com exatamente `message` 1 anexo de cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="7cb66-183">The `activityPreview` must contain a `message` activity with exactly 1 adaptive card attachment.</span></span> <span data-ttu-id="7cb66-184">O `<< Card Payload >>` valor é um espaço reservado para o cartão que você deseja enviar.</span><span class="sxs-lookup"><span data-stu-id="7cb66-184">The `<< Card Payload >>` value is a placeholder for the card you wish to send.</span></span>

```json
{
  "composeExtension": {
    "type": "botMessagePreview",
    "activityPreview": {
      "type": "message",
      "attachments":  [
        {
          "contentType": "application/vnd.microsoft.card.adaptive",
          "content": << Card Payload >>
        }
      ]
    }
  }
}
```

* * *

### <a name="the-botmessagepreview-send-and-edit-events"></a><span data-ttu-id="7cb66-185">Os eventos de envio e edição do botMessagePreview</span><span class="sxs-lookup"><span data-stu-id="7cb66-185">The botMessagePreview send and edit events</span></span>

<span data-ttu-id="7cb66-186">Sua extensão de mensagem deve responder agora a duas novas variedades da `composeExtension/submitAction` invocação, onde `value.botMessagePreviewAction = "send"` e `value.botMessagePreviewAction = "edit"` .</span><span class="sxs-lookup"><span data-stu-id="7cb66-186">Your message extension must respond now to two new varieties of the `composeExtension/submitAction` invoke, where `value.botMessagePreviewAction = "send"`and `value.botMessagePreviewAction = "edit"`.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7cb66-187">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7cb66-187">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewEditAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle the event
}

protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewSendAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle the event
}

```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="7cb66-188">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7cb66-188">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionBotMessagePreviewEdit(context, action) {

    //handle the event
  }
  
  handleTeamsMessagingExtensionBotMessagePreviewSend(context, action) {

    //handle the event
  }
}

```

# <a name="json"></a>[<span data-ttu-id="7cb66-189">JSON</span><span class="sxs-lookup"><span data-stu-id="7cb66-189">JSON</span></span>](#tab/json)

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "edit | send",
    "botActivityPreview": [
      {
        "type": "message/card",
        "attachments": [
          {
            "content":
              {
                "type": "AdaptiveCard",
                "body": [{<<card payload>>}]
              },
            "contentType" : "application/vnd.microsoft.card.adaptive"
          }
        ],
        "context": { "theme": "default" }
      }
    ],
  }
}
```

* * *

### <a name="respond-to-botmessagepreview-edit"></a><span data-ttu-id="7cb66-190">Responder à edição botMessagePreview</span><span class="sxs-lookup"><span data-stu-id="7cb66-190">Respond to botMessagePreview edit</span></span>

<span data-ttu-id="7cb66-191">Se o usuário editar o cartão antes de enviar selecionando o **botão Editar,** você receberá uma `composeExtension/submitAction` invocação com `value.botMessagePreviewAction = edit` .</span><span class="sxs-lookup"><span data-stu-id="7cb66-191">If the user edits the card before sending by selecting the **Edit** button, you receive a `composeExtension/submitAction` invoke with `value.botMessagePreviewAction = edit`.</span></span> <span data-ttu-id="7cb66-192">Normalmente, você deve responder retornando o módulo de tarefa enviado em resposta à invocação inicial `composeExtension/fetchTask` que iniciou a interação.</span><span class="sxs-lookup"><span data-stu-id="7cb66-192">You should typically respond by returning the task module you sent in response to the initial `composeExtension/fetchTask` invoke that began the interaction.</span></span> <span data-ttu-id="7cb66-193">Isso permite que o usuário inicie o processo de novo inserindo as informações originais.</span><span class="sxs-lookup"><span data-stu-id="7cb66-193">This allows the user to start the process over by re-entering the original information.</span></span> <span data-ttu-id="7cb66-194">Use as informações disponíveis para preencher previamente o módulo de tarefas para que o usuário não tenha que preencher todas as informações do zero.</span><span class="sxs-lookup"><span data-stu-id="7cb66-194">Use the available information to pre-populate the task module so the user does not have to fill out all of the information from scratch.</span></span>

<span data-ttu-id="7cb66-195">Consulte [responder ao evento `fetchTask` inicial](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span><span class="sxs-lookup"><span data-stu-id="7cb66-195">See [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span></span>

### <a name="respond-to-botmessagepreview-send"></a><span data-ttu-id="7cb66-196">Responder ao envio de botMessagePreview</span><span class="sxs-lookup"><span data-stu-id="7cb66-196">Respond to botMessagePreview send</span></span>

<span data-ttu-id="7cb66-197">Depois que o usuário selecionar o **botão Enviar,** você receberá uma `composeExtension/submitAction` invocação com `value.botMessagePreviewAction = send` .</span><span class="sxs-lookup"><span data-stu-id="7cb66-197">After the user selects the **Send** button, you receive a `composeExtension/submitAction` invoke with `value.botMessagePreviewAction = send`.</span></span> <span data-ttu-id="7cb66-198">Seu serviço Web precisa criar e enviar uma mensagem proativa com o Cartão Adaptável para a conversa e também responder à invocação.</span><span class="sxs-lookup"><span data-stu-id="7cb66-198">Your web service has to create and send a proactive message with the Adaptive Card to the conversation, and also reply to the invoke.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7cb66-199">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7cb66-199">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewSendAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var activityPreview = action.BotActivityPreview[0];
  var attachmentContent = activityPreview.Attachments[0].Content;
  var previewedCard = JsonConvert.DeserializeObject<AdaptiveCard>(attachmentContent.ToString(),
          new JsonSerializerSettings { NullValueHandling = NullValueHandling.Ignore });
  
  previewedCard.Version = "1.0";

  var responseActivity = Activity.CreateMessageActivity();
  Attachment attachment = new Attachment()
  {
    ContentType = AdaptiveCard.ContentType,
    Content = previewedCard
  };
  responseActivity.Attachments.Add(attachment);
  
  // Attribute the message to the user on whose behalf the bot is posting
  responseActivity.ChannelData = new {
    OnBehalfOf = new []
    {
      new
      {
        ItemId = 0,
        MentionType = "person",
        Mri = turnContext.Activity.From.Id,
        DisplayName = turnContext.Activity.From.Name
      }  
    }
  };
  
  await turnContext.SendActivityAsync(responseActivity);

  return new MessagingExtensionActionResponse();
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="7cb66-200">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7cb66-200">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionBotMessagePreviewSend(context, action) {
      // The data has been returned to the bot in the action structure.
      const activityPreview = action.botActivityPreview[0];
      const attachmentContent = activityPreview.attachments[0].content;
      const userText = attachmentContent.body[1].text;
      const choiceSet = attachmentContent.body[3];

      const submitData = {
        MultiSelect: choiceSet.isMultiSelect ? 'true' : 'false',
        Option1: choiceSet.choices[0].title,
        Option2: choiceSet.choices[1].title,
        Option3: choiceSet.choices[2].title,
        Question: userText
      };

      const adaptiveCard = CardFactory.adaptiveCard({
        actions: [
          { type: 'Action.Submit', title: 'Submit', data: { submitLocation: 'messagingExtensionSubmit' } }
        ],
        body: [
          { text: 'Adaptive Card from Task Module', type: 'TextBlock', weight: 'bolder' },
          { text: `${ submitData.Question }`, type: 'TextBlock', id: 'Question' },
          { id: 'Answer', placeholder: 'Answer here...', type: 'Input.Text' },
          {
            choices: [
                { title: submitData.Option1, value: submitData.Option1 },
                { title: submitData.Option2, value: submitData.Option2 },
                { title: submitData.Option3, value: submitData.Option3 }
            ],
            id: 'Choices',
            isMultiSelect: submitData.MultiSelect,
            style: 'expanded',
            type: 'Input.ChoiceSet'
          }
        ],
        type: 'AdaptiveCard',
        version: '1.0'
      });
      const responseActivity = { type: 'message', attachments: [adaptiveCard], channelData: {
          onBehalfOf: [
              { itemId: 0, mentionType: 'person', mri: context.activity.from.id, displayname: context.activity.from.name }
          ]
      }};

      await context.sendActivity(responseActivity);
    }
}
```

# <a name="json"></a>[<span data-ttu-id="7cb66-201">JSON</span><span class="sxs-lookup"><span data-stu-id="7cb66-201">JSON</span></span>](#tab/json)

<span data-ttu-id="7cb66-202">Você recebe uma nova `composeExtension/submitAction` mensagem semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="7cb66-202">You receive a new `composeExtension/submitAction` message similar to the following:</span></span>

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "send",
    "botActivityPreview": [
      {
        "type": "message/card",
        "attachments": [
          {
            "content":
              {
                "type": "AdaptiveCard",
                "body": [{<<card payload>>}]
              },
            "contentType" : "application/vnd.microsoft.card.adaptive"
          }
        ],
        "context": { "theme": "default" }
      }
    ],
  }
}
```

* * *

### <a name="user-attribution-for-bots-messages"></a><span data-ttu-id="7cb66-203">Atribuição do usuário para mensagens de bots</span><span class="sxs-lookup"><span data-stu-id="7cb66-203">User attribution for bots messages</span></span> 

<span data-ttu-id="7cb66-204">Em cenários em que um bot envia mensagens em nome de um usuário, atribuir a mensagem a esse usuário pode ajudar no envolvimento e mostrar um fluxo de interação mais natural.</span><span class="sxs-lookup"><span data-stu-id="7cb66-204">In scenarios where a bot sends messages on behalf of a user, attributing the message to that user can help with engagement and showcase a more natural interaction flow.</span></span> <span data-ttu-id="7cb66-205">Esse recurso permite que você atribua uma mensagem de seu bot a um usuário em cujo nome ela foi enviada.</span><span class="sxs-lookup"><span data-stu-id="7cb66-205">This feature allows you to attribute a message from your bot to a user on whose behalf it was sent.</span></span>

<span data-ttu-id="7cb66-206">Na imagem a seguir, à esquerda está uma mensagem de cartão enviada por um *bot* sem atribuição do usuário e à direita está um cartão enviado por um *bot* com atribuição do usuário.</span><span class="sxs-lookup"><span data-stu-id="7cb66-206">In the following image, on the left is a card message sent by a bot *without* user attribution and on the right is a card sent by a bot *with* user attribution.</span></span>

![Captura de tela](../../../assets/images/messaging-extension/user-attribution-bots.png)

<span data-ttu-id="7cb66-208">Para usar a atribuição do usuário em equipes, você deve adicionar a entidade de menção à sua `OnBehalfOf` carga que é enviada ao `ChannelData` `Activity` Teams.</span><span class="sxs-lookup"><span data-stu-id="7cb66-208">To use the user attribution in teams, you must  add the `OnBehalfOf` mention entity to `ChannelData` in your `Activity` payload that is sent to Teams.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7cb66-209">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7cb66-209">C#/.NET</span></span>](#tab/dotnet-1)

```csharp
    OnBehalfOf = new []
    {
      new
      {
        ItemId = 0,
        MentionType = "person",
        Mri = turnContext.Activity.From.Id,
        DisplayName = turnContext.Activity.From.Name
      }  
    }

```

# <a name="json"></a>[<span data-ttu-id="7cb66-210">JSON</span><span class="sxs-lookup"><span data-stu-id="7cb66-210">JSON</span></span>](#tab/json-1)

```json
{
    "text": "Hello World!",
    "ChannelData": {
        "OnBehalfOf": [{
            "itemid": 0,
            "mentionType": "person",
            "mri": "29:orgid:89e6508d-6c0f-4ffe-9f6a-b58416d965ae",
            "displayName": "Sowrabh N R S"
        }]
    }
}
```

* * *

<span data-ttu-id="7cb66-211">A seção a seguir é uma descrição das entidades na `OnBehalfOf` matriz:</span><span class="sxs-lookup"><span data-stu-id="7cb66-211">The following section is a description of the entities in the `OnBehalfOf` of Array:</span></span>

#### <a name="details-of--onbehalfof-entity-schema"></a><span data-ttu-id="7cb66-212">Detalhes do  `OnBehalfOf` esquema de entidade</span><span class="sxs-lookup"><span data-stu-id="7cb66-212">Details of  `OnBehalfOf` entity schema</span></span>

|<span data-ttu-id="7cb66-213">Campo</span><span class="sxs-lookup"><span data-stu-id="7cb66-213">Field</span></span>|<span data-ttu-id="7cb66-214">Tipo</span><span class="sxs-lookup"><span data-stu-id="7cb66-214">Type</span></span>|<span data-ttu-id="7cb66-215">Descrição</span><span class="sxs-lookup"><span data-stu-id="7cb66-215">Description</span></span>|
|:---|:---|:---|
|`itemId`|<span data-ttu-id="7cb66-216">Inteiro</span><span class="sxs-lookup"><span data-stu-id="7cb66-216">Integer</span></span>|<span data-ttu-id="7cb66-217">Deve ser 0</span><span class="sxs-lookup"><span data-stu-id="7cb66-217">Should be 0</span></span>|
|`mentionType`|<span data-ttu-id="7cb66-218">String</span><span class="sxs-lookup"><span data-stu-id="7cb66-218">String</span></span>|<span data-ttu-id="7cb66-219">Deve ser "pessoa"</span><span class="sxs-lookup"><span data-stu-id="7cb66-219">Should be "person"</span></span>|
|`mri`|<span data-ttu-id="7cb66-220">String</span><span class="sxs-lookup"><span data-stu-id="7cb66-220">String</span></span>|<span data-ttu-id="7cb66-221">Identificador de recurso de mensagem (MRI) da pessoa em cujo nome a mensagem é enviada.</span><span class="sxs-lookup"><span data-stu-id="7cb66-221">Message resource identifier (MRI) of the person on whose behalf the message is sent.</span></span> <span data-ttu-id="7cb66-222">O nome do remetente da mensagem seria exibido como " \<user\> via \<bot name\> ".</span><span class="sxs-lookup"><span data-stu-id="7cb66-222">Message sender name would appear as "\<user\> via \<bot name\>".</span></span>|
|`displayName`|<span data-ttu-id="7cb66-223">String</span><span class="sxs-lookup"><span data-stu-id="7cb66-223">String</span></span>|<span data-ttu-id="7cb66-224">Nome da pessoa.</span><span class="sxs-lookup"><span data-stu-id="7cb66-224">Name of the person.</span></span> <span data-ttu-id="7cb66-225">Usado como fallback em caso de resolução de nome não disponível.</span><span class="sxs-lookup"><span data-stu-id="7cb66-225">Used as fallback in case name resolution is unavailable.</span></span>|
  
## <a name="next-steps"></a><span data-ttu-id="7cb66-226">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7cb66-226">Next Steps</span></span>

<span data-ttu-id="7cb66-227">Adicionar um comando de pesquisa</span><span class="sxs-lookup"><span data-stu-id="7cb66-227">Add a search command</span></span>

* [<span data-ttu-id="7cb66-228">Definir comandos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="7cb66-228">Define search commands</span></span>](~/messaging-extensions/how-to/search-commands/define-search-command.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
