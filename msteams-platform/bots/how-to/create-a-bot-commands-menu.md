---
title: Criar um menu de comando para seu bot
author: clearab
description: Como criar um menu de comando para seu Microsoft Teams bot
ms.topic: how-to
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: f89c564a2843aaee010774e6b262a96ce4d6530f
ms.sourcegitcommit: c59d90ae03eae32996db49f162855965b55c52fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2021
ms.locfileid: "52668831"
---
# <a name="bot-command-menus"></a><span data-ttu-id="2f6d1-103">Menus de comando bot</span><span class="sxs-lookup"><span data-stu-id="2f6d1-103">Bot command menus</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="2f6d1-104">Para definir um conjunto de comandos principais aos quais o bot pode responder, você pode adicionar um menu de comando com uma lista lista de comandos suspensos para seu bot.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-104">To define a set of core commands that your bot can respond to, you can add a command menu with a drop-down list of commands for your bot.</span></span> <span data-ttu-id="2f6d1-105">A lista de comandos é apresentada aos usuários na área de mensagem de composição quando eles estão em conversa com seu bot.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-105">The list of commands is presented to the users in the compose message area when they are in conversation with your bot.</span></span> <span data-ttu-id="2f6d1-106">Selecione um comando na lista para inserir a cadeia de caracteres de comando na caixa de mensagem de composição e selecione **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-106">Select a command from the list to insert the command string into the compose message box and select **Send**.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2f6d1-107">Desktop</span><span class="sxs-lookup"><span data-stu-id="2f6d1-107">Desktop</span></span>](#tab/desktop)

![Menu de comando bot](./conversations/media/bot-menu-sample.png)

# <a name="mobile"></a>[<span data-ttu-id="2f6d1-109">Mobile</span><span class="sxs-lookup"><span data-stu-id="2f6d1-109">Mobile</span></span>](#tab/mobile)

![Menu de comando de bot móvel](./conversations/media/mobile-bot-menu-sample.png)

* * *

## <a name="create-a-command-menu-for-your-bot"></a><span data-ttu-id="2f6d1-111">Criar um menu de comando para seu bot</span><span class="sxs-lookup"><span data-stu-id="2f6d1-111">Create a command menu for your bot</span></span>

<span data-ttu-id="2f6d1-112">Os menus de comando são definidos no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-112">Command menus are defined in your app manifest.</span></span> <span data-ttu-id="2f6d1-113">Você pode usar o **App Studio para** criar ou adicioná-los manualmente no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-113">You can either use **App Studio** to create them or add them manually in the app manifest.</span></span>

### <a name="create-a-command-menu-for-your-bot-using-app-studio"></a><span data-ttu-id="2f6d1-114">Criar um menu de comando para seu bot usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="2f6d1-114">Create a command menu for your bot using App Studio</span></span>

<span data-ttu-id="2f6d1-115">Um pré-requisito para criar um menu de comando para seu bot é que você deve editar um manifesto de aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-115">A prerequisite to create a command menu for your bot is that you must edit an existing app manifest.</span></span> <span data-ttu-id="2f6d1-116">As etapas para adicionar um menu de comando são as mesmas, se você criar um novo manifesto ou editar um existente.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-116">The steps to add a command menu are the same, whether you create a new manifest or edit an existing one.</span></span>

<span data-ttu-id="2f6d1-117">**Para criar um menu de comando para seu bot usando o App Studio**</span><span class="sxs-lookup"><span data-stu-id="2f6d1-117">**To create a command menu for your bot using App Studio**</span></span>

1. <span data-ttu-id="2f6d1-118">Abra Teams e selecione **Aplicativos** no painel esquerdo.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-118">Open Teams and select **Apps** from the left pane.</span></span> <span data-ttu-id="2f6d1-119">Na página **Aplicativos,** procure o **App Studio** e selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-119">In the **Apps** page, search for **App Studio**, and select **Open**.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="2f6d1-120">Se você não tiver o **App Studio,** poderá baixá-lo.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-120">If you do not have **App Studio**, you can download it.</span></span> <span data-ttu-id="2f6d1-121">Para obter mais informações, [consulte installing App Studio](~/concepts/build-and-test/app-studio-overview.md#installing-app-studio).</span><span class="sxs-lookup"><span data-stu-id="2f6d1-121">For more information, see [installing App Studio](~/concepts/build-and-test/app-studio-overview.md#installing-app-studio).</span></span>

    ![App Studio](./conversations/media/AppStudio.png)

2. <span data-ttu-id="2f6d1-123">No **App Studio,** selecione a **guia Editor de** manifesto. Se você não tiver um pacote de aplicativos existente, poderá criar ou importar um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-123">In **App Studio**, select the **Manifest editor** tab. If you do not have an existing app package, you can create or import an existing app.</span></span> <span data-ttu-id="2f6d1-124">Para obter mais informações, [consulte atualizar um pacote de aplicativos](~/tutorials/get-started-dotnet-app-studio.md#use-app-studio-to-update-the-app-package).</span><span class="sxs-lookup"><span data-stu-id="2f6d1-124">For more information, see [update an app package](~/tutorials/get-started-dotnet-app-studio.md#use-app-studio-to-update-the-app-package).</span></span>

3. <span data-ttu-id="2f6d1-125">No painel esquerdo do editor **de manifesto** e na seção **Recursos,** selecione **Bots**.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-125">In the left pane of the **Manifest editor** and in the **Capabilities** section, select **Bots**.</span></span>

4. <span data-ttu-id="2f6d1-126">No painel direito do editor **de manifesto** e na seção **Comandos,** selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-126">In the right pane of the **Manifest editor** and in the **Commands** section, select **Add**.</span></span> <span data-ttu-id="2f6d1-127">A **tela Novo Comando** é exibida.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-127">The **New Command** screen appears.</span></span>

    ![Menu Comandos do App Studio Adicionar botão](./conversations/media/AppStudio-CommandMenu-Add.png)

5. <span data-ttu-id="2f6d1-129">Insira o **texto Comando** que deve aparecer como o menu de comando do bot.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-129">Enter the **Command text** that must appear as the command menu for your bot.</span></span>

6. <span data-ttu-id="2f6d1-130">Insira o **texto da Ajuda** que deve aparecer sob o texto do comando no menu.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-130">Enter the **Help text** that must appear under the command text in the menu.</span></span> <span data-ttu-id="2f6d1-131">**O texto da** ajuda deve ser uma breve explicação sobre a finalidade do comando.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-131">**Help text** must be a brief explanation of the purpose of the command.</span></span>

7. <span data-ttu-id="2f6d1-132">Selecione as **caixas de** seleção Escopo para selecionar onde esse menu de comando deve aparecer e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-132">Select the **Scope** check boxes to select where this command menu must appear, and select **Save**.</span></span>

    ![Botão de menu novos comandos do App Studio](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a><span data-ttu-id="2f6d1-134">Criar um menu de comando para seu bot editando Manifest.json</span><span class="sxs-lookup"><span data-stu-id="2f6d1-134">Create a command menu for your bot by editing Manifest.json</span></span>

<span data-ttu-id="2f6d1-135">Outra maneira de criar um menu de comando é cria-lo diretamente no arquivo de manifesto enquanto desenvolve o código-fonte do bot.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-135">Another way to create a command menu is to create it directly in the manifest file while developing your bot source code.</span></span> <span data-ttu-id="2f6d1-136">Para usar esse método, siga estes pontos:</span><span class="sxs-lookup"><span data-stu-id="2f6d1-136">To use this method, follow these points:</span></span>

* <span data-ttu-id="2f6d1-137">Cada menu dá suporte a até dez comandos.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-137">Each menu supports up to ten commands.</span></span>
* <span data-ttu-id="2f6d1-138">Crie um único menu de comando que funcione em todos os escopos.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-138">Create a single command menu that works in all scopes.</span></span>
* <span data-ttu-id="2f6d1-139">Crie um menu de comando diferente para cada escopo.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-139">Create a different command menu for each scope.</span></span>

#### <a name="manifest-example-for-single-menu-for-both-scopes"></a><span data-ttu-id="2f6d1-140">Exemplo de manifesto para menu único para ambos os escopos</span><span class="sxs-lookup"><span data-stu-id="2f6d1-140">Manifest example for single menu for both scopes</span></span>

<span data-ttu-id="2f6d1-141">O código de exemplo de manifesto para menu único para ambos os escopos é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2f6d1-141">The manifest example code for single menu for both scopes is as follows:</span></span>

```json
{
  ⋮
  "bots":[
    {
      "botId":"[Microsoft App ID for your bot]",
      "scopes": [
        "personal",
        "team"
      ],
      "commandLists":[
        {
          "scopes":[
            "team",
            "personal"
          ],
          "commands":[
            {
              "title":"Help",
              "description":"Displays this help message"
            },
            {
              "title":"Search Flights",
              "description":"Search flights from Seattle to Phoenix May 2-5 departing after 3pm"
            },
            {
              "title":"Search Hotels",
              "description":"Search hotels in Portland tonight"
            },
            {
              "title":"Best Time to Fly",
              "description":"Best time to fly to London for a 5 day trip this summer"
            }
          ]
        }
      ]
    }
  ],
  ...
}
```

#### <a name="manifest-example-for-the-menu-for-each-scope"></a><span data-ttu-id="2f6d1-142">Exemplo de manifesto para o menu para cada escopo</span><span class="sxs-lookup"><span data-stu-id="2f6d1-142">Manifest example for the menu for each scope</span></span>

<span data-ttu-id="2f6d1-143">O código de exemplo de manifesto para o menu para cada escopo é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2f6d1-143">The manifest example code for the menu for each scope is as follows:</span></span>

```json
{
  ...
  "bots":[
    {
      "botId":"<Microsoft app ID for your bot>",
      "scopes": [
        "groupChat",
        "team"
      ],
      "commandLists":[
        {
          "scopes":[
            "team"
          ],
          "commands":[
            {
            "title":"help",
            "description":"Displays this help message for channels"
            }
          ]
        },
        {
          "scopes":[
            "groupChat"
          ],
          "commands":[
            {
            "title":"help",
            "description":"Displays this help message for group chat"
            }
          ]
        }
      ]
    }
  ],
  ...
}
```

<span data-ttu-id="2f6d1-144">Você deve manipular comandos de menu em seu código de bot à medida que lida com qualquer mensagem dos usuários.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-144">You must handle menu commands in your bot code as you handle any message from users.</span></span> <span data-ttu-id="2f6d1-145">Você pode manipular comandos de menu em seu código de bot ao analisar a parte **\@ Menção** do texto da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-145">You can handle menu commands in your bot code by parsing out the **\@Mention** portion of the message text.</span></span>

## <a name="handle-menu-commands-in-your-bot-code"></a><span data-ttu-id="2f6d1-146">Manipular comandos de menu em seu código de bot</span><span class="sxs-lookup"><span data-stu-id="2f6d1-146">Handle menu commands in your bot code</span></span>

<span data-ttu-id="2f6d1-147">Os bots em um grupo ou canal respondem somente quando são mencionados `@botname` em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-147">Bots in a group or channel respond only when they are mentioned `@botname` in a message.</span></span> <span data-ttu-id="2f6d1-148">Cada mensagem recebida por um bot quando em um escopo de grupo ou canal contém seu nome no texto da mensagem retornado.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-148">Every message received by a bot when in a group or channel scope contains its name in the message text returned.</span></span> <span data-ttu-id="2f6d1-149">Antes de manipular o comando que está sendo retornado, a análise da mensagem deve manipular a mensagem recebida por um bot com seu nome.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-149">Before handling the command being returned, your message parsing must handle the message received by a bot with its name.</span></span>

> [!NOTE]
> <span data-ttu-id="2f6d1-150">Para manipular os comandos em código, eles são enviados para o bot como uma mensagem regular.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-150">To handle the commands in code, they are sent to your bot as a regular message.</span></span> <span data-ttu-id="2f6d1-151">Você deve lidar com eles como faria com qualquer outra mensagem de seus usuários.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-151">You must handle them as you would handle any other message from your users.</span></span> <span data-ttu-id="2f6d1-152">Os comandos no código inseram texto pré-configurado na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-152">The commands in code insert pre-configured text into the text box.</span></span> <span data-ttu-id="2f6d1-153">Em seguida, o usuário deve enviar esse texto como faz para qualquer outra mensagem.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-153">The user must then send that text as they do for any other message.</span></span>

# <a name="c"></a>[<span data-ttu-id="2f6d1-154">C#</span><span class="sxs-lookup"><span data-stu-id="2f6d1-154">C#</span></span>](#tab/dotnet)

<span data-ttu-id="2f6d1-155">Você pode analisar a parte **\@ Menção** do texto da mensagem usando um método estático fornecido com o Microsoft Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-155">You can parse out the **\@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework.</span></span> <span data-ttu-id="2f6d1-156">É um método da classe `Activity` chamada `RemoveRecipientMention` .</span><span class="sxs-lookup"><span data-stu-id="2f6d1-156">It is a method of the `Activity` class named `RemoveRecipientMention`.</span></span>

<span data-ttu-id="2f6d1-157">O C# código para analisar a parte **\@ Menção** do texto da mensagem é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2f6d1-157">The C# code to parse out the **\@Mention** portion of the message text is as follows:</span></span>

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascript"></a>[<span data-ttu-id="2f6d1-158">JavaScript</span><span class="sxs-lookup"><span data-stu-id="2f6d1-158">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="2f6d1-159">Você pode analisar a parte **\@ Menção** do texto da mensagem usando um método estático fornecido com a Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-159">You can parse out the **\@Mention** portion of the message text using a static method provided with the Bot Framework.</span></span> <span data-ttu-id="2f6d1-160">É um método da classe `TurnContext` chamada `removeMentionText` .</span><span class="sxs-lookup"><span data-stu-id="2f6d1-160">It is a method of the `TurnContext` class named `removeMentionText`.</span></span>

<span data-ttu-id="2f6d1-161">O código JavaScript para analisar a parte **\@ Menção** do texto da mensagem é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2f6d1-161">The JavaScript code to parse out the **\@Mention** portion of the message text is as follows:</span></span>

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[<span data-ttu-id="2f6d1-162">Python</span><span class="sxs-lookup"><span data-stu-id="2f6d1-162">Python</span></span>](#tab/python)

<span data-ttu-id="2f6d1-163">Você pode analisar a parte **@Mention** do texto da mensagem usando um método estático fornecido com a Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-163">You can parse out the **@Mention** portion of the message text using a static method provided with the Bot Framework.</span></span> <span data-ttu-id="2f6d1-164">É um método da classe `TurnContext` chamada `remove_recipient_mention` .</span><span class="sxs-lookup"><span data-stu-id="2f6d1-164">It is a method of the `TurnContext` class named `remove_recipient_mention`.</span></span>

<span data-ttu-id="2f6d1-165">O código Python para analisar a parte **\@ Menção** do texto da mensagem é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2f6d1-165">The Python code to parse out the **\@Mention** portion of the message text is as follows:</span></span>

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

<span data-ttu-id="2f6d1-166">Para habilitar o funcionamento suave do código do bot, há poucas práticas recomendadas que você deve seguir.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-166">To enable smooth functioning of your bot code, there are few best practices that you must follow.</span></span>

## <a name="command-menu-best-practices"></a><span data-ttu-id="2f6d1-167">Práticas recomendadas do menu de comando</span><span class="sxs-lookup"><span data-stu-id="2f6d1-167">Command menu best practices</span></span>

<span data-ttu-id="2f6d1-168">A seguir estão as práticas recomendadas do menu de comando:</span><span class="sxs-lookup"><span data-stu-id="2f6d1-168">Following are the command menu best practices:</span></span>

* <span data-ttu-id="2f6d1-169">Mantenha-o simples: o menu bot deve apresentar os principais recursos do bot.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-169">Keep it simple: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="2f6d1-170">Mantenha-o curto: as opções de menu não devem ser longas e não devem ser instruções de idioma natural complexas.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-170">Keep it short: Menu options must not be long and must not be complex natural language statements.</span></span> <span data-ttu-id="2f6d1-171">Eles devem ser comandos simples.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-171">They must be simple commands.</span></span>
* <span data-ttu-id="2f6d1-172">Mantenha-o invocavel: ações ou comandos de menu bot devem estar sempre disponíveis, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-172">Keep it invokable: Bot menu actions or commands must always be available, regardless of the state of the conversation or the dialog the bot is in.</span></span>

> [!NOTE]
> <span data-ttu-id="2f6d1-173">Se você remover quaisquer comandos do manifesto, reimplante seu aplicativo para implementar as alterações.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-173">If you remove any commands from your manifest, you must redeploy your app to implement the changes.</span></span> <span data-ttu-id="2f6d1-174">Em geral, quaisquer alterações no manifesto exigem que você reimplante seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f6d1-174">In general, any changes to the manifest require you to redeploy your app.</span></span>

## <a name="next-step"></a><span data-ttu-id="2f6d1-175">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="2f6d1-175">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f6d1-176">Conversas em canal e em grupo</span><span class="sxs-lookup"><span data-stu-id="2f6d1-176">Channel and group conversations</span></span>](~/bots/how-to/conversations/channel-and-group-conversations.md)
