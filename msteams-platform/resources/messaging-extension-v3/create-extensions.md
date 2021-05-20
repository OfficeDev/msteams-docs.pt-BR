---
title: Iniciar ações com extensões de mensagens
description: Crie extensões de mensagens baseadas em ação para permitir que os usuários acionem serviços externos
localization_priority: Normal
ms.topic: how-to
keywords: equipes de extensões de mensagens de extensões de mensagens pesquisa
ms.openlocfilehash: bfb3295726c355164f080c15e3759ea36a99d914
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566737"
---
# <a name="initiate-actions-with-messaging-extensions"></a><span data-ttu-id="c913e-104">Iniciar ações com extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="c913e-104">Initiate actions with messaging extensions</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

<span data-ttu-id="c913e-105">As extensões de mensagens baseadas em ação permitem que seus usuários acionem ações em serviços externos enquanto estão dentro de Teams.</span><span class="sxs-lookup"><span data-stu-id="c913e-105">Action-based messaging extensions allow your users to trigger actions in external services while inside of Teams.</span></span>

![Exemplo de cartão de extensão de mensagens](~/assets/images/compose-extensions/ceexample.png)

<span data-ttu-id="c913e-107">As seções a seguir descrevem como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="c913e-107">The following sections describe how to do this.</span></span>

[!include[Common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="action-type-message-extensions"></a><span data-ttu-id="c913e-108">Extensões de mensagem tipo ação</span><span class="sxs-lookup"><span data-stu-id="c913e-108">Action type message extensions</span></span>

<span data-ttu-id="c913e-109">Para iniciar ações a partir de uma extensão de mensagens, defina o `type` parâmetro para `action` .</span><span class="sxs-lookup"><span data-stu-id="c913e-109">To initiate actions from a  messaging extension set the `type` parameter to `action`.</span></span> <span data-ttu-id="c913e-110">Abaixo está um exemplo de um manifesto com uma pesquisa e um comando de criação.</span><span class="sxs-lookup"><span data-stu-id="c913e-110">Below is an example of a manifest with a search and a create command.</span></span> <span data-ttu-id="c913e-111">Uma única extensão de mensagens pode ter até 10 comandos diferentes.</span><span class="sxs-lookup"><span data-stu-id="c913e-111">A single messaging extension can have up to 10 different commands.</span></span> <span data-ttu-id="c913e-112">Isso pode incluir vários comandos baseados em pesquisa e vários comandos baseados em ação.</span><span class="sxs-lookup"><span data-stu-id="c913e-112">This can include both multiple search and multiple action-based commands.</span></span>

#### <a name="complete-app-manifest-example"></a><span data-ttu-id="c913e-113">Exemplo completo de manifesto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="c913e-113">Complete app manifest example</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0",
  "id": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
  "packageName": "com.microsoft.teams.samples.Todo",
  "developer": {
    "name": "John Developer",
    "websiteUrl": "http://todobotservice.azurewebsites.net/",
    "privacyUrl": "http://todobotservice.azurewebsites.net/privacy",
    "termsOfUseUrl": "http://todobotservice.azurewebsites.net/termsofuse"
  },
  "name": {
    "short": "To Do",
    "full": "To Do"
  },
  "description": {
    "short": "Find or create a new task in To Do",
    "full": "Find or create a new task in To Do"
  },
  "icons": {
    "outline": "todo-outline.jpg",
    "color": "todo-color.jpg"
  },
  "accentColor": "#ff6a00",
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [
        {
          "id": "searchCmd",
          "description": "Search you Todo's",
          "title": "Search",
          "initialRun": true,
          "context": ["commandBox", "compose"],
          "parameters": [
            {
              "name": "searchKeyword",
              "description": "Enter your search keywords",
              "title": "Keywords"
            }
          ]
        },
        {
          "id": "addTodo",
          "description": "Create a To Do item",
          "title": "Create To Do",
          "type": "action",
          "context": ["commandBox", "message", "compose"],
          "parameters": [
            {
              "name": "Name",
              "description": "To Do Title",
              "title": "Title",
              "inputType": "text"
            },
            {
              "name": "Description",
              "description": "Description of the task",
              "title": "Description",
              "inputType": "textarea"
            },
            {
              "name": "Date",
              "description": "Due date for the task",
              "title": "Date",
              "inputType": "date"
            }
          ]
        },
        {
          "id": "reassignTodo",
          "description": "Reassign a todo item",
          "title": "Reassign a todo item",
          "type": "action",
          "fetchTask": true,
          "parameters": [
            {
              "name": "Name",
              "title": "Title"
            }
          ]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "todobotservice.azurewebsites.net",
    "*.todobotservice.azurewebsites.net"
  ]
}
```

### <a name="initiate-actions-from-messages"></a><span data-ttu-id="c913e-114">Iniciar ações a partir de mensagens</span><span class="sxs-lookup"><span data-stu-id="c913e-114">Initiate actions from messages</span></span>

<span data-ttu-id="c913e-115">Além de iniciar ações da área de compor mensagens, você também pode usar sua extensão de mensagens para iniciar uma ação a partir de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="c913e-115">In addition to initiating actions from the compose message area, you can also use your messaging extension to initiate an action from a message.</span></span> <span data-ttu-id="c913e-116">Isso permitirá que você envie o conteúdo da mensagem para o seu bot para processamento e, opcionalmente, responda a essa mensagem com uma resposta usando o método descrito em [Responder ao envio](#responding-to-submit).</span><span class="sxs-lookup"><span data-stu-id="c913e-116">This will allow you to send the contents of the message to your bot for processing, and optionally reply to that message with a response using the method described in [Responding to submit](#responding-to-submit).</span></span> <span data-ttu-id="c913e-117">A resposta será inserida como resposta à mensagem que seus usuários podem editar antes de enviar.</span><span class="sxs-lookup"><span data-stu-id="c913e-117">The response will be inserted as a reply to the message that your users can edit before submitting.</span></span> <span data-ttu-id="c913e-118">Seus usuários podem acessar sua extensão de mensagens a partir do menu de estouro `...` e, em seguida, selecionar `Take action` como na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="c913e-118">Your users can access your messaging extension from the overflow `...` menu and then selecting `Take action` as in the following image:</span></span>

![Exemplo de iniciar uma ação a partir de uma mensagem](~/assets/images/compose-extensions/messageextensions_messageaction.png)

<span data-ttu-id="c913e-120">Para permitir que sua extensão de mensagens funcione a partir de uma mensagem, você precisará adicionar o `context` parâmetro ao objeto da extensão de mensagens no manifesto do `commands` aplicativo, conforme o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="c913e-120">To enable your messaging extension to work from a message you'll need to add the `context` parameter to your messaging extension's `commands` object in your app manifest as in the example below.</span></span> <span data-ttu-id="c913e-121">As cordas válidas para a `context` matriz são , e `"message"` `"commandBox"` `"compose"` .</span><span class="sxs-lookup"><span data-stu-id="c913e-121">Valid strings for the `context` array are `"message"`, `"commandBox"`, and `"compose"`.</span></span> <span data-ttu-id="c913e-122">O valor padrão é `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="c913e-122">The default value is `["compose", "commandBox"]`.</span></span> <span data-ttu-id="c913e-123">Consulte a seção [definir comandos](#define-commands) para obter detalhes completos no `context` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c913e-123">See the [define commands](#define-commands) section for complete details on the `context` parameter.</span></span>

```json
"composeExtensions": [
  {
    "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "reassignTodo",
        "description": "Reassign a todo item",
        "title": "Create To Do",
        "type": "Action",
        "context": ["message"],
        "fetchTask": true
    }]
    ...

```

<span data-ttu-id="c913e-124">Abaixo está um exemplo do `value` objeto contendo os detalhes da mensagem que serão enviados como parte da `composeExtension` solicitação a ser enviada ao seu bot.</span><span class="sxs-lookup"><span data-stu-id="c913e-124">Below is an example of the `value` object containing the message details that will be sent as part of the `composeExtension` request be sent to your bot.</span></span>

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
...
  "value": {
    "commandId": "setReminder",
    "commandContext": "message",
    "messagePayload": {
      "id": "1111111111",
      "replyToId": null,
      "createdDateTime": "2019-02-25T21:29:36.065Z",
      "lastModifiedDateTime": null,
      "deleted": false,
      "subject": "Message subject",
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "body": {
        "contentType": "html",
        "content": "this is the message"
    },
      "from": {
        "device": null,
        "conversation": null,
        "user": {
          "userIdentityType": "aadUser",
          "id": "wxyz12ab8-ab12-cd34-ef56-098abc123876",
          "displayName": "Jamie Smythe"
        },
        "application": null
      },
      "reactions": [
        {
          "reactionType": "like",
          "createdDateTime": "2019-02-25T22:40:40.806Z",
          "user": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "qrst12346-ab12-cd34-ef56-098abc123876",
              "displayName": "Jim Brown"
            },
            "application": null
          }
        }
      ],
      "mentions": [
        {
          "id": 0,
          "mentionText": "Sarah",
          "mentioned": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "ab12345678-ab12-cd34-ef56-098abc123876",
              "displayName": "Sarah"
            },
            "application": null
          }
        }
      ]
    }
  ...
```

### <a name="test-via-uploading"></a><span data-ttu-id="c913e-125">Teste via upload</span><span class="sxs-lookup"><span data-stu-id="c913e-125">Test via uploading</span></span>

<span data-ttu-id="c913e-126">Você pode testar sua extensão de mensagens carregando seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c913e-126">You can test your messaging extension by uploading your app.</span></span> <span data-ttu-id="c913e-127">Para obter mais informações, consulte [Uploading do seu aplicativo em uma equipe](~/concepts/deploy-and-publish/apps-upload.md).</span><span class="sxs-lookup"><span data-stu-id="c913e-127">For more information, see [Uploading your app in a team](~/concepts/deploy-and-publish/apps-upload.md).</span></span>

<span data-ttu-id="c913e-128">Para abrir sua extensão de mensagens, navegue até qualquer um de seus chats ou canais.</span><span class="sxs-lookup"><span data-stu-id="c913e-128">To open your messaging extension, navigate to any of your chats or channels.</span></span> <span data-ttu-id="c913e-129">Escolha o botão **Mais opções** (**&#8943;)** na caixa de composição e escolha sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c913e-129">Choose the **More options** (**&#8943;**) button in the compose box, and choose your messaging extension.</span></span>

## <a name="collecting-input-from-users"></a><span data-ttu-id="c913e-130">Coletando entradas dos usuários</span><span class="sxs-lookup"><span data-stu-id="c913e-130">Collecting input from users</span></span>

<span data-ttu-id="c913e-131">Existem três maneiras de coletar informações de um usuário final em Teams.</span><span class="sxs-lookup"><span data-stu-id="c913e-131">There are three ways to collect information from an end user in Teams.</span></span>

### <a name="static-parameter-list"></a><span data-ttu-id="c913e-132">Lista de parâmetros estáticos</span><span class="sxs-lookup"><span data-stu-id="c913e-132">Static parameter list</span></span>

<span data-ttu-id="c913e-133">Neste método, tudo o que você precisa fazer é definir uma lista estática de parâmetros no manifesto, conforme mostrado acima no comando "Criar To Do".</span><span class="sxs-lookup"><span data-stu-id="c913e-133">In this method, all you need to do is define a static list of parameters in the manifest as shown above in the "Create To Do" command.</span></span> <span data-ttu-id="c913e-134">Para usar este método, `fetchTask` certifique-se de que está definido e que você define seus `false` parâmetros no manifesto.</span><span class="sxs-lookup"><span data-stu-id="c913e-134">To use this method ensure `fetchTask` is set to `false` and that you define your parameters in the manifest.</span></span>

<span data-ttu-id="c913e-135">Quando um usuário escolhe um comando com parâmetros estáticos, Teams gerará um formulário em um Módulo de Tarefa com os parâmetros definidos no manifesto.</span><span class="sxs-lookup"><span data-stu-id="c913e-135">When a user chooses a command with static parameters, Teams will generate a form in a Task Module with the parameters defined in the manifest.</span></span> <span data-ttu-id="c913e-136">Ao bater Enviar a `composeExtension/submitAction` é enviado para o bot.</span><span class="sxs-lookup"><span data-stu-id="c913e-136">On hitting Submit a `composeExtension/submitAction` is sent to the bot.</span></span> <span data-ttu-id="c913e-137">Para obter mais informações sobre o conjunto de respostas esperado, consulte [Responding to submit](#responding-to-submit).</span><span class="sxs-lookup"><span data-stu-id="c913e-137">For more information on the expected set of responses, see [Responding to submit](#responding-to-submit).</span></span>

### <a name="dynamic-input-using-an-adaptive-card"></a><span data-ttu-id="c913e-138">Entrada dinâmica usando uma placa adaptativa</span><span class="sxs-lookup"><span data-stu-id="c913e-138">Dynamic input using an adaptive card</span></span>

<span data-ttu-id="c913e-139">Neste método, seu serviço pode definir um cartão adaptativo personalizado para coletar a entrada do usuário final.</span><span class="sxs-lookup"><span data-stu-id="c913e-139">In this method, your service can define a custom adaptive card to collect the end user input.</span></span> <span data-ttu-id="c913e-140">Para esta abordagem, defina o `fetchTask` parâmetro `true` para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="c913e-140">For this approach, set the `fetchTask` parameter to `true` in the manifest.</span></span> <span data-ttu-id="c913e-141">Observe que se você definir `fetchTask` para `true` quaisquer parâmetros estáticos definidos para o comando será ignorado.</span><span class="sxs-lookup"><span data-stu-id="c913e-141">Note that if you set `fetchTask` to `true` any static parameters defined for the command will be ignored.</span></span>

<span data-ttu-id="c913e-142">Neste método, seu serviço receberá um `composeExtension/fetchTask` evento e precisa responder com uma resposta do módulo de [tarefas](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)baseado em cartão adaptativo .</span><span class="sxs-lookup"><span data-stu-id="c913e-142">In this method your service will receive a `composeExtension/fetchTask` event and needs to respond with an adaptive card based [task module response](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object).</span></span> <span data-ttu-id="c913e-143">A seguir está uma resposta amostral com um cartão adaptativo:</span><span class="sxs-lookup"><span data-stu-id="c913e-143">Following is a sample response with an adaptive card:</span></span>

```json
{
    "task": {
        "type": "continue",
        "value": {
            "card": {
                "contentType": "application/vnd.microsoft.card.adaptive",
                "content": {
                    "body": [
                        {
                            "type": "TextBlock",
                            "text": "Please enter the following information:"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Name"
                        },
                        {
                            "type": "Input.Text",
                            "spacing": "None",
                            "title": "New Input.Toggle",
                            "placeholder": "Placeholder text"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Date of birth"
                        },
                        {
                            "type": "Input.Date",
                            "spacing": "None",
                            "title": "New Input.Toggle"
                        }
                    ],
                    "type": "AdaptiveCard",
                    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
                    "version": "1.0"
                }
            }
        }
    }
}
```

<span data-ttu-id="c913e-144">O bot também pode responder com uma resposta auth/config se o usuário precisar autenticar ou configurar a extensão antes de obter a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="c913e-144">The bot can also respond with an auth/config response if the user needs to authenticate or configure the extension before getting the user input.</span></span>

### <a name="dynamic-input-using-a-web-view"></a><span data-ttu-id="c913e-145">Entrada dinâmica usando uma visão web</span><span class="sxs-lookup"><span data-stu-id="c913e-145">Dynamic input using a web view</span></span>

<span data-ttu-id="c913e-146">Neste método, o serviço pode mostrar um `<iframe>` widget baseado para mostrar qualquer interface do usuário personalizada e coletar a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="c913e-146">In this method your service can show an `<iframe>` based widget to show any custom UI and collect user input.</span></span> <span data-ttu-id="c913e-147">Para esta abordagem, defina o `fetchTask` parâmetro `true` para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="c913e-147">For this approach, set the `fetchTask` parameter to `true` in the manifest.</span></span>

<span data-ttu-id="c913e-148">Assim como no fluxo de cartão adaptativo, seu serviço será enviado a um `fetchTask` evento e precisa responder com uma resposta do módulo de [tarefa](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)baseado em URL .</span><span class="sxs-lookup"><span data-stu-id="c913e-148">Just like in the adaptive card flow your service will be send a `fetchTask` event and needs to respond with a URL based [task module response](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object).</span></span> <span data-ttu-id="c913e-149">A seguir está uma resposta amostral com um cartão Adaptive:</span><span class="sxs-lookup"><span data-stu-id="c913e-149">Following is a sample response with an Adaptive card:</span></span>

```json
{
    "task": {
        "value": {
            "url": "http://mywebapp.com/input"
        },
        "type": "continue"
    }
}
```

### <a name="request-to-install-your-conversational-bot"></a><span data-ttu-id="c913e-150">Solicite a instalação do seu bot de conversação</span><span class="sxs-lookup"><span data-stu-id="c913e-150">Request to install your conversational bot</span></span>

<span data-ttu-id="c913e-151">Se o aplicativo também contiver um bot de conversação, pode ser necessário garantir que seu bot esteja instalado na conversa antes de carregar o módulo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="c913e-151">If your app also contains a conversational bot, it may be necessary to ensure that your bot is installed in the conversation before loading your task module.</span></span> <span data-ttu-id="c913e-152">Isso pode ser útil em situações em que você precisa obter um contexto adicional para o módulo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="c913e-152">This can be useful in situations where you need to get additional context for you task module.</span></span> <span data-ttu-id="c913e-153">Por exemplo, você pode precisar buscar a lista para preencher o controle de um catador de pessoas, ou a lista de canais em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="c913e-153">For example, you may need to fetch the roster to populate a people picker control, or the list of channels in a team.</span></span>

<span data-ttu-id="c913e-154">Para facilitar esse fluxo, quando sua extensão de mensagens recebe pela primeira vez a `composeExtension/fetchTask` verificação de invocação para ver se seu bot está instalado no contexto atual.</span><span class="sxs-lookup"><span data-stu-id="c913e-154">To facilitate this flow, when your messaging extension first receives the `composeExtension/fetchTask` invoke check to see if your bot is installed in the current context.</span></span> <span data-ttu-id="c913e-155">Você pode conseguir isso tentando a chamada da lista de visitas, por exemplo, Se o bot não estiver instalado, você retorna um Cartão Adaptável com uma ação que solicita ao usuário a instalação do seu bot Veja o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="c913e-155">You could accomplish this by attempting the get roster call, for example, If your bot is not installed, you return an Adaptive Card with an action that requests the user to install your bot See the example below.</span></span> <span data-ttu-id="c913e-156">Observe que isso exige que o usuário tenha permissão para instalar aplicativos naquele local; se eles não puderem, eles serão apresentados com uma mensagem pedindo-lhes para entrar em contato com seu administrador.</span><span class="sxs-lookup"><span data-stu-id="c913e-156">Note that this requires the user to have permission to install apps in that location; if they cannot they will be presented with a message asking them to contact their administrator.</span></span>

<span data-ttu-id="c913e-157">Aqui está um exemplo da resposta:</span><span class="sxs-lookup"><span data-stu-id="c913e-157">Here's an example of the response:</span></span>

```json
{
  "type": "AdaptiveCard",
  "body": [
    {
      "type": "TextBlock",
      "text": "Looks like you haven't used Disco in this team/chat"
    }
  ],
  "actions": [
    {
      "type": "Action.Submit",
      "title": "Continue",
      "data": {
        "msteams": {
          "justInTimeInstall": true
        }
      }
    }
  ],
  "version": "1.0"
}
```

<span data-ttu-id="c913e-158">Uma vez que o usuário complete a instalação, o bot receberá outra mensagem de invocação com `name = composeExtension/submitAction` , e `value.data.msteams.justInTimeInstall = true` .</span><span class="sxs-lookup"><span data-stu-id="c913e-158">Once the user completes the installation, your bot will receive another invoke message with `name = composeExtension/submitAction`, and `value.data.msteams.justInTimeInstall = true`.</span></span>

<span data-ttu-id="c913e-159">Aqui está um exemplo da invocação:</span><span class="sxs-lookup"><span data-stu-id="c913e-159">Here's an example of the invoke:</span></span>

```json
{
  "value": {
    "commandId": "giveKudos",
    "commandContext": "compose",
    "context": {
      "theme": "default"
    },
    "data": {
      "msteams": {
        "justInTimeInstall": true
      }
    }
  },
  "conversation": {
    "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
  },
  "name": "composeExtension/submitAction",
  "imdisplayname": "Bob Smith"
}
```

<span data-ttu-id="c913e-160">Você deve responder a esta invocação com a mesma resposta de tarefa com a que você teria respondido se o bot já estivesse instalado.</span><span class="sxs-lookup"><span data-stu-id="c913e-160">You should respond to this invoke with the same task response you would have responded with if the bot was already installed.</span></span>

## <a name="responding-to-submit"></a><span data-ttu-id="c913e-161">Respondendo ao envio</span><span class="sxs-lookup"><span data-stu-id="c913e-161">Responding to submit</span></span>

<span data-ttu-id="c913e-162">Uma vez que um usuário complete a entrada, seu bot receberá um `composeExtension/submitAction` evento com o conjunto de valores de identificação de comando e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c913e-162">Once a user completes entering their input your bot will receive a `composeExtension/submitAction` event with the command id and parameter values set.</span></span>

<span data-ttu-id="c913e-163">Estas são as diferentes respostas esperadas a um `submitAction` .</span><span class="sxs-lookup"><span data-stu-id="c913e-163">These are the different expected responses to a `submitAction`.</span></span>

### <a name="task-module-response"></a><span data-ttu-id="c913e-164">Resposta do módulo de tarefas</span><span class="sxs-lookup"><span data-stu-id="c913e-164">Task Module response</span></span>

<span data-ttu-id="c913e-165">Isso é usado quando sua extensão precisa emarar diálogos para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c913e-165">This is used when your extension needs to chain dialogs together to get more information.</span></span> <span data-ttu-id="c913e-166">A resposta é exatamente a mesma `fetchTask` mencionada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c913e-166">The response is exactly the same as `fetchTask` mentioned earlier.</span></span>

### <a name="compose-extension-authconfig-response"></a><span data-ttu-id="c913e-167">Compor auth/config resposta de extensão</span><span class="sxs-lookup"><span data-stu-id="c913e-167">Compose extension auth/config response</span></span>

<span data-ttu-id="c913e-168">Isso é usado quando sua extensão precisa autenticar ou configurar para continuar.</span><span class="sxs-lookup"><span data-stu-id="c913e-168">This is used when your extension needs to either authenticate or configure in order to continue.</span></span> <span data-ttu-id="c913e-169">Para obter mais informações, consulte a [seção de autenticação](~/resources/messaging-extension-v3/search-extensions.md#authentication) na seção de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c913e-169">For more information, see [authentication section](~/resources/messaging-extension-v3/search-extensions.md#authentication) in the search section.</span></span>

### <a name="compose-extension-result-response"></a><span data-ttu-id="c913e-170">Compor resposta de resultado de extensão</span><span class="sxs-lookup"><span data-stu-id="c913e-170">Compose extension result response</span></span>

<span data-ttu-id="c913e-171">Isso costumava inserir uma carta na caixa de composição como resultado de um comando.</span><span class="sxs-lookup"><span data-stu-id="c913e-171">This used to insert a card into the compose box as a result of a the command.</span></span> <span data-ttu-id="c913e-172">É a mesma resposta que é usada no comando de pesquisa, mas está limitada a um cartão ou um resultado na matriz.</span><span class="sxs-lookup"><span data-stu-id="c913e-172">It's the same response that's used in the search command, but it's limited to one card or one result in the array.</span></span>

```json
{
  "composeExtension": {
    "type": "result",
    "attachmentLayout": "list",
    "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "85069: Create a cool app",
            "images": [
              {
                "url": "https://placekitten.com/200/200"
              }
            ]
          }
        },
    "attachments": [
      {  
        "contentType": "application/vnd.microsoft.teams.card.o365connector",
        "content": {
          "sections": [
            {
              "activityTitle": "[85069]: Create a cool app",
              "activityImage&quot;: &quot;https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value&quot;: &quot;[Larry Brown](mailto:larryb@example.com)"
                },
                {
                  "name": "State:",
                  "value": "Active"
                }
              ]
            }
          ]
        }
      }
    ]
  }
}
```

### <a name="respond-with-an-adaptive-card-message-sent-from-a-bot"></a><span data-ttu-id="c913e-173">Responda com uma mensagem de cartão adaptativo enviada de um bot</span><span class="sxs-lookup"><span data-stu-id="c913e-173">Respond with an adaptive card message sent from a bot</span></span>

<span data-ttu-id="c913e-174">Você também pode responder à ação de envio inserindo uma mensagem com um Cartão Adaptável no canal com um bot.</span><span class="sxs-lookup"><span data-stu-id="c913e-174">You can also respond to the submit action by inserting a message with an Adaptive Card into the channel with a bot.</span></span> <span data-ttu-id="c913e-175">Seu usuário poderá visualizar a mensagem antes de submetê-la e potencialmente editar/interagir com ela também.</span><span class="sxs-lookup"><span data-stu-id="c913e-175">Your user will be able to preview the message before submitting it, and potentially edit/interact with it as well.</span></span> <span data-ttu-id="c913e-176">Isso pode ser muito útil em cenários onde você precisa coletar informações de seus usuários antes de criar uma resposta de cartão adaptativo.</span><span class="sxs-lookup"><span data-stu-id="c913e-176">This can be very useful in scenarios where you need to gather information from your users before creating an adaptive card response.</span></span> <span data-ttu-id="c913e-177">O cenário a seguir mostra como você pode usar esse fluxo para configurar uma enquete sem incluir as etapas de configuração na mensagem do canal.</span><span class="sxs-lookup"><span data-stu-id="c913e-177">The following scenario shows how you can use this flow to configure a poll without including the configuration steps in the channel message.</span></span>

1. <span data-ttu-id="c913e-178">O usuário clica na extensão de mensagens para acionar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="c913e-178">The user clicks the messaging extension to trigger the task module.</span></span>
1. <span data-ttu-id="c913e-179">O usuário usa o módulo de tarefa para configurar a enquete.</span><span class="sxs-lookup"><span data-stu-id="c913e-179">The user uses the task module to configure the poll.</span></span>
1. <span data-ttu-id="c913e-180">Após enviar o módulo de tarefa de configuração, o aplicativo usa as informações fornecidas no módulo de tarefa para criar um cartão adaptativo e envia-o como resposta `botMessagePreview` ao cliente.</span><span class="sxs-lookup"><span data-stu-id="c913e-180">After submitting the configuration task module the app uses the information provided in the task module to craft an adaptive card and sends it as a `botMessagePreview` response to the client.</span></span>
1. <span data-ttu-id="c913e-181">Em seguida, o usuário pode visualizar a mensagem do cartão adaptativo antes que o bot a insira no canal.</span><span class="sxs-lookup"><span data-stu-id="c913e-181">The user can then preview the adaptive card message before the bot will inserts it into the channel.</span></span> <span data-ttu-id="c913e-182">Se o bot ainda não for um membro do canal, clicar `Send` adicionará o bot.</span><span class="sxs-lookup"><span data-stu-id="c913e-182">If the bot is not already a member of the channel, clicking `Send` will add the bot.</span></span>
1. <span data-ttu-id="c913e-183">Interagir com o cartão adaptativo mudará a mensagem antes de enviá-la.</span><span class="sxs-lookup"><span data-stu-id="c913e-183">Interacting with the adaptive card will change the message before sending it.</span></span>
1. <span data-ttu-id="c913e-184">Uma vez que o usuário clique `Send` no bot, postará a mensagem no canal.</span><span class="sxs-lookup"><span data-stu-id="c913e-184">Once the user clicks `Send` the bot will post the message to the channel.</span></span>

<span data-ttu-id="c913e-185">Para habilitar esse fluxo, seu módulo de tarefa deve responder como no exemplo abaixo, que apresentará a mensagem de visualização ao usuário.</span><span class="sxs-lookup"><span data-stu-id="c913e-185">To enable this flow your task module should respond as in the example below, which will present the preview message to the user.</span></span>

>[!Note]
><span data-ttu-id="c913e-186">O `activityPreview` deve conter uma atividade com `message` exatamente 1 acessório de cartão adaptativo.</span><span class="sxs-lookup"><span data-stu-id="c913e-186">The `activityPreview` must contain a `message` activity with exactly 1 adaptive card attachment.</span></span>

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

<span data-ttu-id="c913e-187">Sua extensão de mensagem agora precisará responder a dois novos tipos de `value.botMessagePreviewAction = "send"` interações, e `value.botMessagePreviewAction = "edit"` .</span><span class="sxs-lookup"><span data-stu-id="c913e-187">Your message extension will now need to respond to two new types of interactions, `value.botMessagePreviewAction = "send"` and `value.botMessagePreviewAction = "edit"`.</span></span> <span data-ttu-id="c913e-188">Abaixo está um exemplo do `value` objeto que você precisará processar:</span><span class="sxs-lookup"><span data-stu-id="c913e-188">Below is an example of the `value` object you will need to process:</span></span>

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "send" | "edit",
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

<span data-ttu-id="c913e-189">Ao responder à `edit` solicitação, você deve responder com uma `task` resposta com os valores preenchidos com as informações que o usuário já enviou.</span><span class="sxs-lookup"><span data-stu-id="c913e-189">When responding to the `edit` request you should respond with a `task` response with the values populated with the information the user has already submitted.</span></span> <span data-ttu-id="c913e-190">Ao responder à `send` solicitação, você deve enviar uma mensagem para o canal contendo o cartão adaptativo finalizado.</span><span class="sxs-lookup"><span data-stu-id="c913e-190">When responding to the `send` request you should send a message to the channel containing the finalized adaptive card.</span></span>

# <a name="typescriptnodejs"></a>[<span data-ttu-id="c913e-191">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="c913e-191">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
teamChatConnector.onComposeExtensionSubmitAction((
    event: builder.IEvent,
    request: teamBuilder.IComposeExtensionActionCommandRequest,
    callback: (err: Error, result: any, statusCode: number) => void) => {
        let invokeValue = (<any> event).value;

        if (invokeValue.botMessagePreviewAction ) {
            let attachment = invokeValue.botActivityPreview[0].attachments[0];

            if (invokeValue.botMessagePreviewAction === 'send') {
                let msg = new builder.Message()
                    .address(event.address)
                    .addAttachment(attachment);
                teamChatConnector.send([msg.toMessage()],
                    (error) => {
                        if(error){
                            //TODO: Handle error and callback
                        }
                        else {
                            callback(null, null, 200);
                        }
                    }
                );
            }

            else if (invokeValue.botMessagePreviewAction === 'edit') {
              // Create the card and populate with user-inputted information
              let card = { ... }

              let taskResponse = {
                task: {
                  type: "continue",
                  value: {
                    title: "Card Preview",
                    card: {
                      contentType: 'application/vnd.microsoft.card.adaptive',
                      content: card
                    }
                  }
                }
              }
              callback(null, taskResponse, 200);
            }

        else {
            let attachment = {
                  //create adaptive card
                };
            let activity = new builder.Message().addAttachment(attachment).toMessage();
            let response = teamBuilder.ComposeExtensionResponse.messagePreview()
                .preview(activity)
                .toResponse();
            callback(null, response, 200);
        }
    });
```

# <a name="cnet"></a>[<span data-ttu-id="c913e-192">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="c913e-192">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="c913e-193">Esta amostra mostra esse fluxo usando o [Microsoft.Bot.Connector.Teams SDK (v3)](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams).</span><span class="sxs-lookup"><span data-stu-id="c913e-193">This sample shows this flow using the [Microsoft.Bot.Connector.Teams SDK (v3)](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams).</span></span>

```csharp
public class MessagesController : ApiController
{

    [BotAuthentication]
    public async Task<HttpResponseMessage> Post([FromBody]Activity activity)
    {
        MicrosoftAppCredentials.TrustServiceUrl(activity.ServiceUrl, DateTime.MaxValue);
        ConnectorClient connectorClient = new ConnectorClient(
            new Uri(activity.ServiceUrl),
            ConfigurationManager.AppSettings[MicrosoftAppCredentials.MicrosoftAppIdKey],
            ConfigurationManager.AppSettings[MicrosoftAppCredentials.MicrosoftAppPasswordKey]);

        if (activity.Type == ActivityTypes.Invoke)
        {
            // Initial task module presented to the user
            if (activity.Name == "composeExtension/fetchTask")
            {
                string task = GetTaskModule();

                return Request.CreateResponse(HttpStatusCode.OK, JObject.Parse(task));
            }
            else if (activity.Name == "composeExtension/submitAction")
            {
                dynamic activityValue = JObject.FromObject(activity.Value);
                string botMessagePreviewAction = activityValue["botMessagePreviewAction"];

                //This is the initial card response sent after the task module is submitted
                if (botMessagePreviewAction is null)
                {
                    string text = activityValue.data.cardMessage;

                    AdaptiveCard card = new AdaptiveCard(new AdaptiveSchemaVersion("1.0"));
                    card.Body.Add(new AdaptiveTextBlock()
                    {
                        Text = "This card will be inserted into the conversation by the bot.",
                        Size = AdaptiveTextSize.Large,
                        Wrap = true
                    });
                    card.Body.Add(new AdaptiveTextBlock()
                    {
                        Text = "The text below is what you provided."
                    });
                    card.Body.Add(new AdaptiveTextBlock()
                    {
                        Text = text,
                    });

                    string cardJson = card.ToJson();

                    string cardMessage = $@"{{
                        'composeExtension': {{
                        'type': 'botMessagePreview',
                        'activityPreview': {{
                            'type': 'message',
                            'attachments': [{{
                                'contentType': 'application/vnd.microsoft.card.adaptive',
                                'content': {cardJson}
                            }}]
                        }}
                        }}
                    }}";

                    JObject res = JObject.Parse(cardMessage);
                    return Request.CreateResponse(HttpStatusCode.OK, res);

                }
                else
                {
                    //This is the "send the card to the channel" event
                    if (botMessagePreviewAction.Equals("send"))
                    {
                        string cardJson = JsonConvert.SerializeObject(activityValue.botActivityPreview[0].attachments[0].content);

                        AdaptiveCardParseResult cardResult = AdaptiveCard.FromJson(cardJson);
                        AdaptiveCard card = cardResult.Card;
                        Attachment cardAttachment = new Attachment
                        {
                            ContentType = AdaptiveCard.ContentType,
                            Content = card
                        };


                        Activity response = activity.CreateReply();
                        response.Attachments.Add(cardAttachment);

                        var result = await connectorClient.Conversations.SendToConversationAsync(response);
                    }
                    //This is fired if the user edits the card before sending it
                    else if (botMessagePreviewAction.Equals("edit"))
                    {
                        string task = GetTaskModule();

                        return Request.CreateResponse(HttpStatusCode.OK, JObject.Parse(task));
                    }
                    else
                    {
                        return Request.CreateResponse(HttpStatusCode.NotImplemented);
                    }
                }
            }
        }

        return Request.CreateResponse(HttpStatusCode.NotImplemented);

    }

    private static string GetTaskModule()
    {
        AdaptiveCard card = new AdaptiveCard(new AdaptiveSchemaVersion("1.0"));
        card.Body.Add(new AdaptiveTextBlock()
        {
            Text = "Please enter the following information:",
            Size = AdaptiveTextSize.Large
        });
        card.Body.Add(new AdaptiveTextBlock()
        {
            Text = "Card Message:"
        });
        card.Body.Add(new AdaptiveTextInput()
        {
            Id = "cardMessage",
            Spacing = AdaptiveSpacing.None,
            Placeholder = "Card message goes here."
        });
        card.Actions.Add(new AdaptiveSubmitAction()
        {
            Title = "Submit"
        });

        string cardJson = card.ToJson();

        //Create the task module response
        string task = $@"{{
                            'task': {{
                                'type': 'continue',
                                'value': {{
                                    'card': {{
                                        'contentType': 'application/vnd.microsoft.card.adaptive',
                                        'content': {cardJson}
                                        }}
                                    }}
                                }}
                            }}";
        return task;
    }

}
```

## <a name="see-also"></a><span data-ttu-id="c913e-194">Confira também</span><span class="sxs-lookup"><span data-stu-id="c913e-194">See also</span></span>

[<span data-ttu-id="c913e-195">Amostras do Bot Framework</span><span class="sxs-lookup"><span data-stu-id="c913e-195">Bot Framework samples</span></span>](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)