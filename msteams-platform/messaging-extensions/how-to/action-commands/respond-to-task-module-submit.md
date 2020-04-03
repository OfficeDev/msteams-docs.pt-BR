---
title: Responder à ação de envio do módulo de tarefa
author: clearab
description: Descreve como responder à ação enviar do módulo de tarefa a partir de um comando de ação de extensão de mensagens
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 6372a683a7c9f08551a9c0d126a0db2ab9212e66
ms.sourcegitcommit: 058b7bbd817af5f513e0e018f2ef562dc3086a84
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "43120259"
---
# <a name="respond-to-the-task-module-submit-action"></a><span data-ttu-id="661de-103">Responder à ação de envio do módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="661de-103">Respond to the task module submit action</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="661de-104">Quando um usuário envia o módulo de tarefa, seu serviço Web receberá uma `composeExtension/submitAction` mensagem de invocação com os valores de ID de comando e de parâmetro definidos.</span><span class="sxs-lookup"><span data-stu-id="661de-104">Once a user submits the task module, your web service will receive a `composeExtension/submitAction` invoke message with the command id and parameter values set.</span></span> <span data-ttu-id="661de-105">Seu aplicativo terá cinco segundos para responder à invocação, caso contrário, o usuário receberá uma mensagem de erro "não é possível acessar o aplicativo" e qualquer resposta à invocação será ignorada pelo cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="661de-105">Your app will have five seconds to respond to the invoke, otherwise the user will receive an "Unable to reach the app" error message, and any reply to the invoke will be ignored by the Teams client.</span></span>

<span data-ttu-id="661de-106">Você tem as seguintes opções para responder.</span><span class="sxs-lookup"><span data-stu-id="661de-106">You have the following options for responding.</span></span>

* <span data-ttu-id="661de-107">Sem resposta-você pode optar por usar a ação enviar para acionar um processo em um sistema externo e não fornecer nenhum feedback para o usuário.</span><span class="sxs-lookup"><span data-stu-id="661de-107">No response - You can choose to use the submit action to trigger a process in an external system, and not provide any feedback to the user.</span></span> <span data-ttu-id="661de-108">Isso pode ser útil para processos de execução longa, e você pode optar por fornecer comentários de outra maneira (por exemplo, com uma [mensagem proativa](~/bots/how-to/conversations/send-proactive-messages.md).</span><span class="sxs-lookup"><span data-stu-id="661de-108">This can be useful for long-running processes, and you may choose to provide feedback in another manner (for example, with a [proactive message](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>
* <span data-ttu-id="661de-109">[Outro módulo de tarefa](#respond-with-another-task-module) : você pode responder com um módulo de tarefa adicional como parte de uma interação de várias etapas.</span><span class="sxs-lookup"><span data-stu-id="661de-109">[Another task module](#respond-with-another-task-module) - You can respond with an additional task module as part of a multi-step interaction.</span></span>
* <span data-ttu-id="661de-110">[Resposta do cartão](#respond-with-a-card-inserted-into-the-compose-message-area) -você pode responder com um cartão em que o usuário pode interagir e/ou inserir em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="661de-110">[Card response](#respond-with-a-card-inserted-into-the-compose-message-area) - You can respond with a card that the user can then interact with and/or insert into a message.</span></span>
* <span data-ttu-id="661de-111">[Cartão adaptável do bot](#bot-response-with-adaptive-card) -Insira um cartão adaptável diretamente na conversa.</span><span class="sxs-lookup"><span data-stu-id="661de-111">[Adaptive Card from bot](#bot-response-with-adaptive-card) - Insert an Adaptive Card directly into the conversation.</span></span>
* [<span data-ttu-id="661de-112">Solicitar que o usuário autentique</span><span class="sxs-lookup"><span data-stu-id="661de-112">Request the user authenticate</span></span>](~/messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="661de-113">Solicitar que o usuário forneça configuração adicional</span><span class="sxs-lookup"><span data-stu-id="661de-113">Request the user provide additional configuration</span></span>](~/messaging-extensions/how-to/add-configuration-page.md)

<span data-ttu-id="661de-114">A tabela abaixo mostra quais tipos de respostas estão disponíveis com base no local de invocação (`commandContext`) da extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="661de-114">The table below shows which types of responses are available based on the invoke location (`commandContext`) of the messaging extension.</span></span> <span data-ttu-id="661de-115">Para autenticação ou configuração, depois que o usuário concluir o fluxo, a chamada original será reenviada ao seu serviço Web.</span><span class="sxs-lookup"><span data-stu-id="661de-115">For authentication or configuration, once the user completes the flow the original invoke will be re-sent to your web service.</span></span>

|<span data-ttu-id="661de-116">Tipo de resposta</span><span class="sxs-lookup"><span data-stu-id="661de-116">Response Type</span></span> | <span data-ttu-id="661de-117">Redação</span><span class="sxs-lookup"><span data-stu-id="661de-117">compose</span></span> | <span data-ttu-id="661de-118">barra de comandos</span><span class="sxs-lookup"><span data-stu-id="661de-118">command bar</span></span> | <span data-ttu-id="661de-119">message</span><span class="sxs-lookup"><span data-stu-id="661de-119">message</span></span> |
|--------------|:-------------:|:-------------:|:---------:|
|<span data-ttu-id="661de-120">Resposta de cartão</span><span class="sxs-lookup"><span data-stu-id="661de-120">Card response</span></span> | <span data-ttu-id="661de-121">x</span><span class="sxs-lookup"><span data-stu-id="661de-121">x</span></span> | <span data-ttu-id="661de-122">x</span><span class="sxs-lookup"><span data-stu-id="661de-122">x</span></span> | <span data-ttu-id="661de-123">x</span><span class="sxs-lookup"><span data-stu-id="661de-123">x</span></span> |
|<span data-ttu-id="661de-124">Outro módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="661de-124">Another task module</span></span> | <span data-ttu-id="661de-125">x</span><span class="sxs-lookup"><span data-stu-id="661de-125">x</span></span> | <span data-ttu-id="661de-126">x</span><span class="sxs-lookup"><span data-stu-id="661de-126">x</span></span> | <span data-ttu-id="661de-127">x</span><span class="sxs-lookup"><span data-stu-id="661de-127">x</span></span> |
|<span data-ttu-id="661de-128">Bot com cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="661de-128">Bot with Adaptive Card</span></span> | <span data-ttu-id="661de-129">x</span><span class="sxs-lookup"><span data-stu-id="661de-129">x</span></span> |  | <span data-ttu-id="661de-130">x</span><span class="sxs-lookup"><span data-stu-id="661de-130">x</span></span> |
| <span data-ttu-id="661de-131">Nenhuma resposta</span><span class="sxs-lookup"><span data-stu-id="661de-131">No response</span></span> | <span data-ttu-id="661de-132">x</span><span class="sxs-lookup"><span data-stu-id="661de-132">x</span></span> | <span data-ttu-id="661de-133">x</span><span class="sxs-lookup"><span data-stu-id="661de-133">x</span></span> | <span data-ttu-id="661de-134">x</span><span class="sxs-lookup"><span data-stu-id="661de-134">x</span></span> |

## <a name="the-submitaction-invoke-event"></a><span data-ttu-id="661de-135">O evento de chamar enviaraction</span><span class="sxs-lookup"><span data-stu-id="661de-135">The submitAction invoke event</span></span>

<span data-ttu-id="661de-136">Veja a seguir alguns exemplos de como receber a mensagem Invoke.</span><span class="sxs-lookup"><span data-stu-id="661de-136">Below are examples of receiving the invoke message.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="661de-137">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="661de-137">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken) {
  //code to handle the submit action
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="661de-138">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="661de-138">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  constructor() {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
  
  //code to handle the submit action
    }
  }
}
```

# <a name="json"></a>[<span data-ttu-id="661de-139">JSON</span><span class="sxs-lookup"><span data-stu-id="661de-139">JSON</span></span>](#tab/json)

<span data-ttu-id="661de-140">Este é um exemplo do objeto JSON que você receberá.</span><span class="sxs-lookup"><span data-stu-id="661de-140">This is an example of the JSON object you will receive.</span></span> <span data-ttu-id="661de-141">O `commandContext` parâmetro indica onde sua extensão de mensagens foi disparada.</span><span class="sxs-lookup"><span data-stu-id="661de-141">The `commandContext` parameter indicates where your messaging extension was triggered from.</span></span> <span data-ttu-id="661de-142">O `data` objeto contém os campos no formulário como parâmetros e os valores que o usuário enviou.</span><span class="sxs-lookup"><span data-stu-id="661de-142">The `data` object contains the fields on the form as parameters, and the values the user submitted.</span></span> <span data-ttu-id="661de-143">O objeto JSON aqui é reduzido para realçar os campos mais relevantes.</span><span class="sxs-lookup"><span data-stu-id="661de-143">The JSON object here is shortened to highlight the most relevant fields.</span></span>

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

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a><span data-ttu-id="661de-144">Responder com um cartão inserido na área de mensagem de composição</span><span class="sxs-lookup"><span data-stu-id="661de-144">Respond with a card inserted into the compose message area</span></span>

<span data-ttu-id="661de-145">A maneira mais comum de responder à `composeExtension/submitAction` solicitação é com um cartão inserido na área de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="661de-145">The most common way to respond to the `composeExtension/submitAction` request is with a card inserted into the compose message area.</span></span> <span data-ttu-id="661de-146">O usuário pode então optar por enviar o cartão para a conversa.</span><span class="sxs-lookup"><span data-stu-id="661de-146">The user can then choose to submit the card to the conversation.</span></span> <span data-ttu-id="661de-147">Para obter mais informações sobre o uso de cartões [, consulte cartões e ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="661de-147">For more information on using cards see [cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

# <a name="cnet"></a>[<span data-ttu-id="661de-148">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="661de-148">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
    dynamic Data = JObject.Parse(action.Data.ToString());
    var response = new MessagingExtensionActionResponse
    {
        ComposeExtension = new MessagingExtensionResult
        {
            AttachmentLayout = "list",
            Type = "result",
        },
    };
    var card = new HeroCard
    {
        Title = Data["formField1"] as string,
        Subtitle = Data["formField2"]  as string,
        Text = Data["formField3"]  as string,
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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="661de-149">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="661de-149">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="661de-150">JSON</span><span class="sxs-lookup"><span data-stu-id="661de-150">JSON</span></span>](#tab/json)

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

## <a name="respond-with-another-task-module"></a><span data-ttu-id="661de-151">Responder com outro módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="661de-151">Respond with another task module</span></span>

<span data-ttu-id="661de-152">Você pode optar por responder ao `submitAction` evento com um módulo de tarefa adicional.</span><span class="sxs-lookup"><span data-stu-id="661de-152">You can choose to respond to the `submitAction` event with an additional task module.</span></span> <span data-ttu-id="661de-153">Isso pode ser útil quando:</span><span class="sxs-lookup"><span data-stu-id="661de-153">This can be useful when:</span></span>

* <span data-ttu-id="661de-154">Você precisa coletar grandes quantidades de informações.</span><span class="sxs-lookup"><span data-stu-id="661de-154">You need to collect large amounts of information.</span></span>
* <span data-ttu-id="661de-155">Se você precisar alterar dinamicamente quais informações você está coletando com base na entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="661de-155">If you need to dynamically change what information you're collecting based on user input</span></span>
* <span data-ttu-id="661de-156">Se você precisar validar as informações enviadas pelo usuário e, potencialmente, reenviar o formulário com uma mensagem de erro, se houver algum problema.</span><span class="sxs-lookup"><span data-stu-id="661de-156">If you need to validate the information submitted by the user and potentially resend the form with an error message if something is wrong.</span></span> 

<span data-ttu-id="661de-157">O método de resposta é o mesmo que [responder ao evento inicial `fetchTask` ](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span><span class="sxs-lookup"><span data-stu-id="661de-157">The method for response is the same as [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span></span> <span data-ttu-id="661de-158">Se você estiver usando o SDK da estrutura de bot, o mesmo evento será disparado para as duas ações de envio.</span><span class="sxs-lookup"><span data-stu-id="661de-158">If you're using the Bot Framework SDK the same event will trigger for both submit actions.</span></span> <span data-ttu-id="661de-159">Isso significa que você precisa certificar-se de adicionar lógica que determina a resposta correta.</span><span class="sxs-lookup"><span data-stu-id="661de-159">This mean you need to be sure to add logic which determines the correct response.</span></span>

## <a name="bot-response-with-adaptive-card"></a><span data-ttu-id="661de-160">Resposta de bot com cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="661de-160">Bot response with Adaptive Card</span></span>

>[!Note]
><span data-ttu-id="661de-161">Esse fluxo requer que você adicione o `bot` objeto ao manifesto do seu aplicativo e que você tenha o escopo necessário definido para o bot.</span><span class="sxs-lookup"><span data-stu-id="661de-161">This flow requires that you add the `bot` object to your app manifest, and that you have the necessary scope defined for the bot.</span></span> <span data-ttu-id="661de-162">Use a mesma ID que sua extensão de mensagens para o bot.</span><span class="sxs-lookup"><span data-stu-id="661de-162">Use the same Id as your messaging extension for your bot.</span></span>

<span data-ttu-id="661de-163">Você também pode responder à ação de envio inserindo uma mensagem com um cartão adaptável no canal com um bot.</span><span class="sxs-lookup"><span data-stu-id="661de-163">You can also respond to the submit action by inserting a message with an Adaptive Card into the channel with a bot.</span></span> <span data-ttu-id="661de-164">O usuário poderá visualizar a mensagem antes de enviá-la e potencialmente editar/interagir com ela também.</span><span class="sxs-lookup"><span data-stu-id="661de-164">Your user will be able to preview the message before submitting it, and potentially edit/interact with it as well.</span></span> <span data-ttu-id="661de-165">Isso pode ser muito útil em cenários em que você precisa coletar informações de seus usuários antes de criar uma resposta de cartão adaptável ou quando precisar atualizar o cartão após alguém interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="661de-165">This can be very useful in scenarios where you need to gather information from your users before creating an adaptive card response, or when you're going to need to update the card after someone interacts with it.</span></span> <span data-ttu-id="661de-166">O cenário a seguir mostra como o aplicativo Polly usa esse fluxo para configurar uma pesquisa sem incluir as etapas de configuração na conversa do canal.</span><span class="sxs-lookup"><span data-stu-id="661de-166">The following scenario shows how the app Polly uses this flow to configure a poll without including the configuration steps in the channel conversation.</span></span>

1. <span data-ttu-id="661de-167">O usuário clica na extensão de mensagens para disparar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="661de-167">The user clicks the messaging extension to trigger the task module.</span></span>
2. <span data-ttu-id="661de-168">O usuário configura a pesquisa com o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="661de-168">The user configures the poll with the task module.</span></span>
3. <span data-ttu-id="661de-169">Depois de enviar o módulo de tarefa, o aplicativo usa as informações fornecidas para compilar a pesquisa como um cartão adaptável e a `botMessagePreview` envia como resposta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="661de-169">After submitting the task module the app uses the information provided to build the poll as an Adaptive Card and sends it as a `botMessagePreview` response to the client.</span></span>
4. <span data-ttu-id="661de-170">O usuário pode visualizar a mensagem de cartão adaptável antes do bot inseri-la no canal.</span><span class="sxs-lookup"><span data-stu-id="661de-170">The user can then preview the adaptive card message before the bot inserts it into the channel.</span></span> <span data-ttu-id="661de-171">Se o aplicativo ainda não for um membro do canal, clique em `Send` adicionará a ele.</span><span class="sxs-lookup"><span data-stu-id="661de-171">If the app is not already a member of the channel, clicking `Send` will add the it.</span></span>
   1. <span data-ttu-id="661de-172">O usuário também pode escolher `Edit` a mensagem, que as retorna para o módulo de tarefa original.</span><span class="sxs-lookup"><span data-stu-id="661de-172">The user can also chose to `Edit` the message, which returns them to the original task module.</span></span>
5. <span data-ttu-id="661de-173">Interagir com o cartão adaptável altera a mensagem antes de enviá-la.</span><span class="sxs-lookup"><span data-stu-id="661de-173">Interacting with the adaptive card changes the message before sending it.</span></span>
6. <span data-ttu-id="661de-174">Quando o usuário clica `Send` no bot envia a mensagem para o canal.</span><span class="sxs-lookup"><span data-stu-id="661de-174">Once the user clicks `Send` the bot posts the message to the channel.</span></span>

### <a name="respond-to-initial-submit-action"></a><span data-ttu-id="661de-175">Responder à ação de envio inicial</span><span class="sxs-lookup"><span data-stu-id="661de-175">Respond to initial submit action</span></span>

<span data-ttu-id="661de-176">Para habilitar esse fluxo, seu módulo de tarefa deve responder à `composeExtension/submitAction` mensagem inicial com uma visualização do cartão que o bot enviará ao canal.</span><span class="sxs-lookup"><span data-stu-id="661de-176">To enable this flow your task module should respond to the initial `composeExtension/submitAction` message with a preview of the card that the bot will send to the channel.</span></span> <span data-ttu-id="661de-177">Isso dá ao usuário a oportunidade de verificar o cartão antes de enviá-lo e também tentará instalar o bot na conversa se ele ainda não estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="661de-177">This gives the user the opportunity to verify the card before sending, and also will attempt to install your bot in the conversation if it is not already installed.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="661de-178">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="661de-178">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  dynamic Data = JObject.Parse(action.Data.ToString());
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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="661de-179">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="661de-179">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="661de-180">JSON</span><span class="sxs-lookup"><span data-stu-id="661de-180">JSON</span></span>](#tab/json)

>[!Note]
><span data-ttu-id="661de-181">O `activityPreview` deve conter uma `message` atividade com exatamente 1 anexo de cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="661de-181">The `activityPreview` must contain a `message` activity with exactly 1 adaptive card attachment.</span></span> <span data-ttu-id="661de-182">O `<< Card Payload >>` valor é um espaço reservado para o cartão que você deseja enviar.</span><span class="sxs-lookup"><span data-stu-id="661de-182">The `<< Card Payload >>` value is a placeholder for the card you wish to send.</span></span>

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

### <a name="the-botmessagepreview-send-and-edit-events"></a><span data-ttu-id="661de-183">Eventos de envio e edição do botMessagePreview</span><span class="sxs-lookup"><span data-stu-id="661de-183">The botMessagePreview send and edit events</span></span>

<span data-ttu-id="661de-184">Sua extensão de mensagem agora precisará responder a duas novas variedades da `composeExtension/submitAction` invocação, onde `value.botMessagePreviewAction = "send"`e `value.botMessagePreviewAction = "edit"`.</span><span class="sxs-lookup"><span data-stu-id="661de-184">Your message extension will now need to respond to two new varieties of the `composeExtension/submitAction` invoke, where `value.botMessagePreviewAction = "send"`and `value.botMessagePreviewAction = "edit"`.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="661de-185">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="661de-185">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="661de-186">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="661de-186">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="661de-187">JSON</span><span class="sxs-lookup"><span data-stu-id="661de-187">JSON</span></span>](#tab/json)

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

### <a name="respond-to-botmessagepreview-edit"></a><span data-ttu-id="661de-188">Responder à edição do botMessagePreview</span><span class="sxs-lookup"><span data-stu-id="661de-188">Respond to botMessagePreview edit</span></span>

<span data-ttu-id="661de-189">Se o usuário decidir editar o cartão antes de enviá-lo clicando no botão **Editar** , você receberá `composeExtension/submitAction` uma chamada `value.botMessagePreviewAction = edit`.</span><span class="sxs-lookup"><span data-stu-id="661de-189">If the user decides to edit the card before sending by clicking the **Edit** button, you will receive a `composeExtension/submitAction` invoke with `value.botMessagePreviewAction = edit`.</span></span> <span data-ttu-id="661de-190">Normalmente, você deve responder retornando o módulo de tarefa enviado em resposta à chamada `composeExtension/fetchTask` inicial que iniciou a interação.</span><span class="sxs-lookup"><span data-stu-id="661de-190">You should typically respond by returning the task module you sent in response to the initial `composeExtension/fetchTask` invoke that began the interaction.</span></span> <span data-ttu-id="661de-191">Isso permite que o usuário inicie o processo, inserindo novamente as informações originais.</span><span class="sxs-lookup"><span data-stu-id="661de-191">This allows the user to start the process over by re-entering the original information.</span></span> <span data-ttu-id="661de-192">Você também deve considerar o uso das informações que agora estão disponíveis para preencher previamente o módulo de tarefa, para que o usuário não tenha preenchido todas as informações do zero.</span><span class="sxs-lookup"><span data-stu-id="661de-192">You should also consider using the information you now have available to pre-populate the task module so the user doesn't have fill out all of the information from scratch.</span></span>

<span data-ttu-id="661de-193">Confira [responder ao evento `fetchTask` inicial](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span><span class="sxs-lookup"><span data-stu-id="661de-193">See [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span></span>

### <a name="respond-to-botmessagepreview-send"></a><span data-ttu-id="661de-194">Responder a botMessagePreview enviar</span><span class="sxs-lookup"><span data-stu-id="661de-194">Respond to botMessagePreview send</span></span>

<span data-ttu-id="661de-195">Quando o usuário clicar no botão **Enviar** , você receberá uma `composeExtension/submitAction` chamada com `value.botMessagePreviewAction = send`.</span><span class="sxs-lookup"><span data-stu-id="661de-195">Once the user clicks the **Send** button, you will receive a `composeExtension/submitAction` invoke with `value.botMessagePreviewAction = send`.</span></span> <span data-ttu-id="661de-196">Seu serviço Web precisará criar e enviar uma mensagem proativa com o cartão adaptável à conversa e também responder à invocação.</span><span class="sxs-lookup"><span data-stu-id="661de-196">Your web service will need to create and send a proactive message with the Adaptive Card to the conversation, and also reply to the invoke.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="661de-197">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="661de-197">C#/.NET</span></span>](#tab/dotnet)

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
  
  await turnContext.SendActivityAsync(responseActivity);

  return new MessagingExtensionActionResponse();
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="661de-198">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="661de-198">JavaScript/Node.js</span></span>](#tab/javascript)

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
      const responseActivity = { type: 'message', attachments: [adaptiveCard] };
    
      await context.sendActivity(responseActivity);
    }
}
```

# <a name="json"></a>[<span data-ttu-id="661de-199">JSON</span><span class="sxs-lookup"><span data-stu-id="661de-199">JSON</span></span>](#tab/json)

<span data-ttu-id="661de-200">Você receberá uma nova `composeExtension/submitAction` mensagem semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="661de-200">You will receive a new `composeExtension/submitAction` message similar to the one below.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="661de-201">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="661de-201">Next Steps</span></span>

<span data-ttu-id="661de-202">Adicionar um comando de pesquisa</span><span class="sxs-lookup"><span data-stu-id="661de-202">Add a search command</span></span>

* [<span data-ttu-id="661de-203">Definir comandos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="661de-203">Define search commands</span></span>](~/messaging-extensions/how-to/search-commands/define-search-command.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
