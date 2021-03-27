---
title: Enviar mensagens a Conectores e WebHooks
description: Descreve como usar Conectores do Office 365 no Microsoft Teams
ms.topic: how-to
localization_priority: Priority
keywords: conector do o365 no teams
ms.openlocfilehash: 6554a9cc1db0ffdae65f1cb875ca7a4c47c21259
ms.sourcegitcommit: 3727fc58e84b6f1752612884c2e0b25e207fb56e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2021
ms.locfileid: "51382328"
---
# <a name="sending-messages-to-connectors-and-webhooks"></a><span data-ttu-id="1832d-104">Enviar mensagens a conectores e webhooks</span><span class="sxs-lookup"><span data-stu-id="1832d-104">Sending messages to connectors and webhooks</span></span>

<span data-ttu-id="1832d-105">Para enviar uma mensagem por meio do Conector do Office 365 ou do Webhook de entrada, poste uma carga JSON na URL do Webhook.</span><span class="sxs-lookup"><span data-stu-id="1832d-105">To send a message through your Office 365 Connector or incoming webhook, you post a JSON payload to the webhook URL.</span></span> <span data-ttu-id="1832d-106">Geralmente, essa carga estará no formato de [Cartão do Conector do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="1832d-106">Typically this payload will be in the form of an [Office 365 Connector Card](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="1832d-107">Também é possível usar esse JSON para criar cartões contendo entradas avançadas, como entrada de texto, seleção múltipla ou escolha de data e hora.</span><span class="sxs-lookup"><span data-stu-id="1832d-107">You can also use this JSON to create cards containing rich inputs, such as text entry, multi-select, or picking a date and time.</span></span> <span data-ttu-id="1832d-108">O código que gera o cartão e as postagens na URL do Webhook pode ser executado em qualquer serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="1832d-108">The code that generates the card and posts to the webhook URL can be running on any hosted service.</span></span> <span data-ttu-id="1832d-109">Esses cartões são definidos como parte de mensagens acionáveis e também são compatíveis com [cartões](~/task-modules-and-cards/what-are-cards.md) usados nos bots do Teams e nas Extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1832d-109">These cards are defined as part of actionable messages, and are also supported in [cards](~/task-modules-and-cards/what-are-cards.md) used in Teams bots and Messaging extensions.</span></span>

### <a name="example-connector-message"></a><span data-ttu-id="1832d-110">Exemplo de mensagem do conector</span><span class="sxs-lookup"><span data-stu-id="1832d-110">Example connector message</span></span>

```json
{
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "themeColor": "0076D7",
    "summary": "Larry Bryant created a new task",
    "sections": [{
        "activityTitle": "Larry Bryant created a new task",
        "activitySubtitle": "On Project Tango",
        "activityImage": "https://teamsnodesample.azurewebsites.net/static/img/image5.png",
        "facts": [{
            "name": "Assigned to",
            "value": "Unassigned"
        }, {
            "name": "Due date",
            "value": "Mon May 01 2017 17:07:18 GMT-0700 (Pacific Daylight Time)"
        }, {
            "name": "Status",
            "value": "Not started"
        }],
        "markdown": true
    }],
    "potentialAction": [{
        "@type": "ActionCard",
        "name": "Add a comment",
        "inputs": [{
            "@type": "TextInput",
            "id": "comment",
            "isMultiline": false,
            "title": "Add a comment here for this task"
        }],
        "actions": [{
            "@type": "HttpPOST",
            "name": "Add comment",
            "target": "https://docs.microsoft.com/outlook/actionable-messages"
        }]
    }, {
        "@type": "ActionCard",
        "name": "Set due date",
        "inputs": [{
            "@type": "DateInput",
            "id": "dueDate",
            "title": "Enter a due date for this task"
        }],
        "actions": [{
            "@type": "HttpPOST",
            "name": "Save",
            "target": "https://docs.microsoft.com/outlook/actionable-messages"
        }]
    }, {
        "@type": "OpenUri",
        "name": "Learn More",
        "targets": [{
            "os": "default",
            "uri": "https://docs.microsoft.com/outlook/actionable-messages"
        }]
    }, {
        "@type": "ActionCard",
        "name": "Change status",
        "inputs": [{
            "@type": "MultichoiceInput",
            "id": "list",
            "title": "Select a status",
            "isMultiSelect": "false",
            "choices": [{
                "display": "In Progress",
                "value": "1"
            }, {
                "display": "Active",
                "value": "2"
            }, {
                "display": "Closed",
                "value": "3"
            }]
        }],
        "actions": [{
            "@type": "HttpPOST",
            "name": "Save",
            "target": "https://docs.microsoft.com/outlook/actionable-messages"
        }]
    }]
}
```

<span data-ttu-id="1832d-111">Essa mensagem produz o seguinte cartão no canal.</span><span class="sxs-lookup"><span data-stu-id="1832d-111">This message produces the following card in the channel.</span></span>

![Captura de tela de um Cartão do conector](~/assets/images/connectors/connector_message.png)

## <a name="creating-actionable-messages"></a><span data-ttu-id="1832d-113">Criar mensagens acionáveis</span><span class="sxs-lookup"><span data-stu-id="1832d-113">Creating actionable messages</span></span>

<span data-ttu-id="1832d-114">O exemplo na seção anterior inclui três botões visíveis no cartão.</span><span class="sxs-lookup"><span data-stu-id="1832d-114">The example in the preceding section includes three visible buttons on the card.</span></span> <span data-ttu-id="1832d-115">Cada botão é definido na propriedade `potentialAction` da mensagem usando ações `ActionCard`, cada uma contendo um tipo de entrada: um campo de texto, um seletor de datas ou uma lista de várias opções.</span><span class="sxs-lookup"><span data-stu-id="1832d-115">Each button is defined in the `potentialAction` property of the message by using `ActionCard` actions, each containing an input type: a text field, a date picker, or a multi-choice list.</span></span> <span data-ttu-id="1832d-116">Cada ação `ActionCard` tem uma ação associada, por exemplo `HttpPOST`.</span><span class="sxs-lookup"><span data-stu-id="1832d-116">Each `ActionCard` action has an associated action, for example `HttpPOST`.</span></span>

<span data-ttu-id="1832d-117">Os cartões do conector oferecem suporte a três tipos de ações:</span><span class="sxs-lookup"><span data-stu-id="1832d-117">Connector cards support three types of actions:</span></span>

- <span data-ttu-id="1832d-118">`ActionCard` Apresenta um ou mais tipos de entrada e ações associadas</span><span class="sxs-lookup"><span data-stu-id="1832d-118">`ActionCard` Presents one or more input types and associated actions</span></span>
- <span data-ttu-id="1832d-119">`HttpPOST` Envia uma solicitação POST a uma URL</span><span class="sxs-lookup"><span data-stu-id="1832d-119">`HttpPOST` Sends a POST request to a URL</span></span>
- <span data-ttu-id="1832d-120">`OpenUri` Abre um URI em um navegador ou aplicativo separado; a opção visa URIs diferentes com base em sistemas operacionais</span><span class="sxs-lookup"><span data-stu-id="1832d-120">`OpenUri` Opens a URI in a separate browser or app; optionally targets different URIs based on operating systems</span></span>

<span data-ttu-id="1832d-121">A ação `ActionCard` oferece suporte a três tipos de entrada:</span><span class="sxs-lookup"><span data-stu-id="1832d-121">The `ActionCard` action supports three input types:</span></span>

- <span data-ttu-id="1832d-122">`TextInput` Um campo de texto de linha única ou de várias linhas com um limite de comprimento opcional</span><span class="sxs-lookup"><span data-stu-id="1832d-122">`TextInput` A single-line or multiline text field with an optional length limit</span></span>
- <span data-ttu-id="1832d-123">`DateInput` Um seletor de data com um seletor de tempo opcional</span><span class="sxs-lookup"><span data-stu-id="1832d-123">`DateInput` A date selector with an optional time selector</span></span>
- <span data-ttu-id="1832d-124">`MultichoiceInput` Uma lista enumerada de opções que oferece uma seleção única ou múltipla.</span><span class="sxs-lookup"><span data-stu-id="1832d-124">`MultichoiceInput` A enumerated list of choices offering either a single selection or multiple selections</span></span>

<span data-ttu-id="1832d-125">`MultichoiceInput` oferece suporte a uma propriedade `style` que controla se a lista já aparecerá totalmente expandida.</span><span class="sxs-lookup"><span data-stu-id="1832d-125">`MultichoiceInput` supports a `style` property that controls whether the list initially appears fully expanded.</span></span> <span data-ttu-id="1832d-126">O valor padrão de `style` depende do valor de `isMultiSelect`.</span><span class="sxs-lookup"><span data-stu-id="1832d-126">The default value of `style` depends on the value of `isMultiSelect`.</span></span>

| `isMultiSelect` | <span data-ttu-id="1832d-127">Padrão `style`</span><span class="sxs-lookup"><span data-stu-id="1832d-127">`style` default</span></span> |
| --- | --- |
| <span data-ttu-id="1832d-128">`false` ou não especificado </span><span class="sxs-lookup"><span data-stu-id="1832d-128">`false` or not specified</span></span> | `compact` |
| `true` | `expanded` |

<span data-ttu-id="1832d-129">Se desejar que uma lista de seleção múltipla seja exibida inicialmente no estilo compacto, especifique `"isMultiSelect": true` e `"style": true`.</span><span class="sxs-lookup"><span data-stu-id="1832d-129">If you want a multiselect list initially displayed in the compact style, you must specify both `"isMultiSelect": true` and `"style": true`.</span></span>

<span data-ttu-id="1832d-130">Para obter mais informações sobre as ações do cartão de conector, consulte **{Actions}**(/outlook/actionable-messages/card-reference#actions) na referência do cartão de mensagem acionável.</span><span class="sxs-lookup"><span data-stu-id="1832d-130">For more information on Connector card actions, see **[Actions]**(/outlook/actionable-messages/card-reference#actions) in the actionable message card reference.</span></span>

> [!NOTE]
> <span data-ttu-id="1832d-131">Especificando `compact`para a `style` propriedade no Microsoft Teams é o mesmo que especificar `normal` para a `style` propriedade no Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="1832d-131">Specifying `compact` for the `style` property in Microsoft Teams is the same as specifying `normal` for the `style` property in Microsoft Outlook.</span></span>
> 
> <span data-ttu-id="1832d-132">Para a ação HttpPOST, o token do portador é incluído com as solicitações.</span><span class="sxs-lookup"><span data-stu-id="1832d-132">For the HttpPOST action, the bearer token is included with the requests.</span></span> <span data-ttu-id="1832d-133">Esse token inclui a identidade do Azure AD do usuário do Office 365 que executou a ação.</span><span class="sxs-lookup"><span data-stu-id="1832d-133">This token includes the Azure AD identity of the Office 365 user who took the action.</span></span>

## <a name="setting-up-a-custom-incoming-webhook"></a><span data-ttu-id="1832d-134">Configurando um webhook de entrada personalizado</span><span class="sxs-lookup"><span data-stu-id="1832d-134">Setting up a custom incoming webhook</span></span>

<span data-ttu-id="1832d-135">Siga estas etapas para ver como enviar um cartão simples para um Conector.</span><span class="sxs-lookup"><span data-stu-id="1832d-135">Follow these steps to see how to send a simple card to a Connector.</span></span>

1. <span data-ttu-id="1832d-136">No Microsoft Teams, escolha **Mais opções** (**&#8943;**) ao lado do nome do canal e escolha **Conectores**.</span><span class="sxs-lookup"><span data-stu-id="1832d-136">In Microsoft Teams, choose **More options** (**&#8943;**) next to the channel name and then choose **Connectors**.</span></span>
2. <span data-ttu-id="1832d-137">Role pela lista de Conectores para o **Webhook de entrada** e escolha **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="1832d-137">Scroll through the list of Connectors to **Incoming Webhook**, and choose **Add**.</span></span>
3. <span data-ttu-id="1832d-138">Digite um nome para o Webhook, carregue uma imagem para associar aos dados dele e escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="1832d-138">Enter a name for the webhook, upload an image to associate with data from the webhook, and choose **Create**.</span></span>
4. <span data-ttu-id="1832d-139">Copie o Webhook para a área de transferência e salve-o.</span><span class="sxs-lookup"><span data-stu-id="1832d-139">Copy the webhook to the clipboard and save it.</span></span> <span data-ttu-id="1832d-140">Será necessário a URL do Webhook para enviar informações ao Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="1832d-140">You'll need the webhook URL for sending information to Microsoft Teams.</span></span>
5. <span data-ttu-id="1832d-141">Escolha **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="1832d-141">Choose **Done**.</span></span>

### <a name="post-a-message-to-the-webhook-using-curl"></a><span data-ttu-id="1832d-142">Postar uma mensagem no Webhook usando cURL</span><span class="sxs-lookup"><span data-stu-id="1832d-142">Post a message to the webhook using cURL</span></span>

<span data-ttu-id="1832d-143">As etapas a seguir usam [cURL](https://curl.haxx.se/).</span><span class="sxs-lookup"><span data-stu-id="1832d-143">The following steps use [cURL](https://curl.haxx.se/).</span></span> <span data-ttu-id="1832d-144">Iremos supor que você o tenha instalado e esteja familiarizado com seu uso básico.</span><span class="sxs-lookup"><span data-stu-id="1832d-144">We assume that you have this installed and are familiar with its basic usage.</span></span>

1. <span data-ttu-id="1832d-145">Na linha de comando, insira o seguinte comando cURL:</span><span class="sxs-lookup"><span data-stu-id="1832d-145">From the command line, enter the following cURL command:</span></span>

   ```bash
   // on macOS or Linux
   curl -H 'Content-Type: application/json' -d '{"text": "Hello World"}' <YOUR WEBHOOK URL>
   ```

   ```bash
   // on Windows
   curl.exe -H "Content-Type:application/json" -d "{'text':'Hello World'}" <YOUR WEBHOOK URL>
   ```

2. <span data-ttu-id="1832d-146">Se o POST tiver êxito, você verá uma saída **1** simples por `curl`.</span><span class="sxs-lookup"><span data-stu-id="1832d-146">If the POST succeeds, you should see a simple **1** output by `curl`.</span></span>
3. <span data-ttu-id="1832d-147">Verifique o cliente do Microsoft Team.</span><span class="sxs-lookup"><span data-stu-id="1832d-147">Check the Microsoft Team client.</span></span> <span data-ttu-id="1832d-148">Você deverá ver o novo cartão postado na equipe.</span><span class="sxs-lookup"><span data-stu-id="1832d-148">You should see the new card posted to the team.</span></span>

### <a name="post-a-message-to-the-webhook-using-powershell"></a><span data-ttu-id="1832d-149">Postar uma mensagem no Webhook usando PowerShell</span><span class="sxs-lookup"><span data-stu-id="1832d-149">Post a message to the webhook using PowerShell</span></span>

<span data-ttu-id="1832d-150">As etapas a seguir usam o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1832d-150">The following steps use PowerShell.</span></span> <span data-ttu-id="1832d-151">Iremos supor que você o tenha instalado e esteja familiarizado com seu uso básico.</span><span class="sxs-lookup"><span data-stu-id="1832d-151">We assume that you have this installed and are familiar with its basic usage.</span></span>

1. <span data-ttu-id="1832d-152">Digite o seguinte comando no prompt do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1832d-152">From the PowerShell prompt, enter the following command:</span></span>

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

2. <span data-ttu-id="1832d-153">Se o POST tiver êxito, você verá uma saída **1** simples por `Invoke-RestMethod`.</span><span class="sxs-lookup"><span data-stu-id="1832d-153">If the POST succeeds, you should see a simple **1** output by `Invoke-RestMethod`.</span></span>
3. <span data-ttu-id="1832d-154">Verifique o canal do Microsoft Teams associado à URL do Webhook.</span><span class="sxs-lookup"><span data-stu-id="1832d-154">Check the Microsoft Teams channel associated with the webhook URL.</span></span> <span data-ttu-id="1832d-155">Você deverá ver o novo cartão postado no canal.</span><span class="sxs-lookup"><span data-stu-id="1832d-155">You should see the new card posted to the channel.</span></span>

- <span data-ttu-id="1832d-156">[Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="1832d-156">[Include two icons](../../concepts/build-and-test/apps-package.md#app-icons).</span></span>
- <span data-ttu-id="1832d-157">Modifique a parte dos `icons` do manifesto para se referir aos nomes de arquivo dos ícones em vez das URLs.</span><span class="sxs-lookup"><span data-stu-id="1832d-157">Modify the `icons` portion of the manifest to refer to the file names of the icons instead of URLs.</span></span>

<span data-ttu-id="1832d-158">O seguinte arquivo manifest.json contém os elementos básicos necessários para testar e enviar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1832d-158">The following manifest.json file contains the basic elements needed to test and submit your app.</span></span>

> [!NOTE]
> <span data-ttu-id="1832d-159">Substitua `id` e `connectorId` no exemplo a seguir pelo GUID do Conector.</span><span class="sxs-lookup"><span data-stu-id="1832d-159">Replace `id` and `connectorId` in the following example with the GUID of your Connector.</span></span>

#### <a name="example-manifestjson-with-connector"></a><span data-ttu-id="1832d-160">Exemplo de manifest.json com o conector</span><span class="sxs-lookup"><span data-stu-id="1832d-160">Example manifest.json with connector</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "id": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
  "version": "1.0",
  "packageName": "com.sampleapp",
  "developer": {
    "name": "Publisher",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.microsoft.com",
    "termsOfUseUrl": "https://www.microsoft.com"
  },
  "description": {
    "full": "This is a small sample app we made for you! This app has samples of all capabilities Microsoft Teams supports.",
    "short": "This is a small sample app we made for you!"
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App"
  },
  "accentColor": "#FFFFFF",
  "needsIdentity": "true"
}
```

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a><span data-ttu-id="1832d-161">Envie cartões adaptáveis usando um webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="1832d-161">Send adaptive cards using an incoming webhook</span></span>

> [!NOTE]
>
> <span data-ttu-id="1832d-162">✔ Todos os elementos nativos do esquema de placa adaptável, exceto `Action.Submit`, são totalmente suportados.</span><span class="sxs-lookup"><span data-stu-id="1832d-162">✔ All native adaptive card schema elements, except `Action.Submit`, are fully supported.</span></span>
>
> <span data-ttu-id="1832d-163">✔ As ações suportadas são [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), and [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span><span class="sxs-lookup"><span data-stu-id="1832d-163">✔ The supported Actions are [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), and [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span></span>

### <a name="the-flow-for-sending-adaptive-cards-via-an-incoming-webhook-is-as-follows"></a><span data-ttu-id="1832d-164">O fluxo para o envio de [cartões adaptáveis](../../task-modules-and-cards/cards/cards-reference.md#adaptive-card) por meio de um webhook de entrada é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1832d-164">The flow for sending [adaptive cards](../../task-modules-and-cards/cards/cards-reference.md#adaptive-card) via an incoming webhook is as follows:</span></span>

<span data-ttu-id="1832d-165">**1.** [Configure um webhook personalizado](#setting-up-a-custom-incoming-webhook) no Teams.</span><span class="sxs-lookup"><span data-stu-id="1832d-165">**1.** [Setup a custom webhook](#setting-up-a-custom-incoming-webhook) in Teams.</span></span></br></br>
<span data-ttu-id="1832d-166">**2.** Crie seu arquivo JSON de cartão adaptável:</span><span class="sxs-lookup"><span data-stu-id="1832d-166">**2.** Create your adaptive card JSON file:</span></span>

```json
{
   "type":"message",
   "attachments":[
      {
         "contentType":"application/vnd.microsoft.card.adaptive",
         "contentUrl":null,
         "content":{
            "$schema":"http://adaptivecards.io/schemas/adaptive-card.json",
            "type":"AdaptiveCard",
            "version":"1.2",
            "body":[
                {
                "type": "TextBlock",
                "text": "For Samples and Templates, see [https://adaptivecards.io/samples](https://adaptivecards.io/samples)"
                }
            ]
         }
      }
   ]
}
```

> [!div class="checklist"]
>
> - <span data-ttu-id="1832d-167">O campo `"type"` deve ser `"message"`.</span><span class="sxs-lookup"><span data-stu-id="1832d-167">The `"type"` field must be `"message"`.</span></span>
> - <span data-ttu-id="1832d-168">A matriz `"attachments"` contém um conjunto de objetos de cartão.</span><span class="sxs-lookup"><span data-stu-id="1832d-168">The `"attachments"` array contains a set of card objects.</span></span>
> - <span data-ttu-id="1832d-169">O campo `"contentType"` deve ser definido para o tipo de cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="1832d-169">The `"contentType"` field must be set to adaptive card type.</span></span>
> - <span data-ttu-id="1832d-170">O objeto `"content"` é o cartão formatado em JSON.</span><span class="sxs-lookup"><span data-stu-id="1832d-170">The `"content"` object is the card formatted in JSON.</span></span>

<span data-ttu-id="1832d-171">**3.** Teste seu cartão adaptável com o Postman</span><span class="sxs-lookup"><span data-stu-id="1832d-171">**3.** Test your adaptive card with Postman</span></span>

<span data-ttu-id="1832d-172">Você pode testar seu cartão adaptável usando o [Postman](https://www.postman.com) para enviar uma solicitação POST para o URL que você criou ao configurar o webhook de entrada.</span><span class="sxs-lookup"><span data-stu-id="1832d-172">You can test your adaptive card using [Postman](https://www.postman.com) to send a POST request to the URL that you created when you setup your incoming webhook.</span></span> <span data-ttu-id="1832d-173">Cole seu arquivo JSON no corpo da solicitação e visualize sua mensagem de cartão adaptável no Teams.</span><span class="sxs-lookup"><span data-stu-id="1832d-173">Paste your JSON file in the body of the request and view your adaptive card message in Teams.</span></span>

>[!TIP]
> <span data-ttu-id="1832d-174">Você pode usar o código do cartão adaptável [Amostras e Modelos](https://adaptivecards.io/samples) para o corpo do seu teste de solicitação Post.</span><span class="sxs-lookup"><span data-stu-id="1832d-174">You can use adaptive card code [Samples and Templates](https://adaptivecards.io/samples) for the body of your test Post request.</span></span>

## <a name="testing-your-connector"></a><span data-ttu-id="1832d-175">Testar o conector</span><span class="sxs-lookup"><span data-stu-id="1832d-175">Testing your connector</span></span>

<span data-ttu-id="1832d-176">Para testar o Conector, carregue-o em uma equipe, como em qualquer outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1832d-176">To test your Connector, upload it to a team as you would with any other app.</span></span> <span data-ttu-id="1832d-177">Você pode criar um pacote .zip usando o arquivo de manifesto do Painel do Desenvolvedor do Connectors (modificado conforme indicado na seção anterior) e os dois arquivos de ícone.</span><span class="sxs-lookup"><span data-stu-id="1832d-177">You can create a .zip package using the manifest file from the Connectors Developer Dashboard (modified as directed in the preceding section) and the two icon files.</span></span>

<span data-ttu-id="1832d-178">Depois de carregar o aplicativo, abra a lista de conectores em qualquer canal.</span><span class="sxs-lookup"><span data-stu-id="1832d-178">After you upload the app, open the Connectors list from any channel.</span></span> <span data-ttu-id="1832d-179">Role até a parte inferior para ver o aplicativo na seção **Carregado**.</span><span class="sxs-lookup"><span data-stu-id="1832d-179">Scroll to the bottom to see your app in the **Uploaded** section.</span></span>

![Captura de tela da seção carregada na caixa de diálogo do Conector](~/assets/images/connectors/connector_dialog_uploaded.png)

<span data-ttu-id="1832d-181">Agora você pode iniciar a experiência de configuração.</span><span class="sxs-lookup"><span data-stu-id="1832d-181">You can now launch the configuration experience.</span></span> <span data-ttu-id="1832d-182">Lembre-se de que esse fluxo ocorre inteiramente no Microsoft Teams por meio de uma janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="1832d-182">Be aware that this flow occurs entirely within Microsoft Teams through a pop-up window.</span></span> <span data-ttu-id="1832d-183">Atualmente, esse comportamento difere da experiência de configuração nos conectores que criamos; estamos trabalhando para unificar as experiências.</span><span class="sxs-lookup"><span data-stu-id="1832d-183">Currently, this behavior differs from the configuration experience in Connectors that we created; we are working on unifying the experiences.</span></span>

<span data-ttu-id="1832d-184">Para verificar se uma ação `HttpPOST` está funcionando corretamente, use o [Webhook de entrada personalizado](#setting-up-a-custom-incoming-webhook).</span><span class="sxs-lookup"><span data-stu-id="1832d-184">To verify that an `HttpPOST` action is working correctly, use your [custom incoming webhook](#setting-up-a-custom-incoming-webhook).</span></span>

## <a name="rate-limiting-for-connectors"></a><span data-ttu-id="1832d-185">Limitação de taxa para conectores</span><span class="sxs-lookup"><span data-stu-id="1832d-185">Rate limiting for connectors</span></span>

<span data-ttu-id="1832d-186">Os limites de taxa de aplicativos controlam o tráfego que um conector ou um webhook de entrada tem permissão para gerar em um canal.</span><span class="sxs-lookup"><span data-stu-id="1832d-186">Application rate limits control the traffic that a connector or an incoming webhook is allowed to generate on a channel.</span></span> <span data-ttu-id="1832d-187">O Teams acompanha as solicitações por meio de uma janela de taxa fixa e de um contador incremental medido em segundos.</span><span class="sxs-lookup"><span data-stu-id="1832d-187">Teams tracks requests via a fixed-rate window and incremental counter measured in seconds.</span></span>  <span data-ttu-id="1832d-188">Se houver muitas solicitações, a conexão do cliente será limitada até que a janela seja atualizada, isto é, pela duração da taxa fixa.</span><span class="sxs-lookup"><span data-stu-id="1832d-188">If too many requests are made, the client connection will be throttled until the window refreshes, i.e., for the duration of the fixed rate.</span></span>

### <a name="transactions-per-second-thresholds"></a><span data-ttu-id="1832d-189">**Limites de transações por segundo**</span><span class="sxs-lookup"><span data-stu-id="1832d-189">**Transactions per second thresholds**</span></span>

| <span data-ttu-id="1832d-190">Tempo (segundos)</span><span class="sxs-lookup"><span data-stu-id="1832d-190">Time (seconds)</span></span>  | <span data-ttu-id="1832d-191">Máximo de solicitações permitidas</span><span class="sxs-lookup"><span data-stu-id="1832d-191">Maximum allowed requests</span></span>  |
|---|---|
| <span data-ttu-id="1832d-192">1</span><span class="sxs-lookup"><span data-stu-id="1832d-192">1</span></span>   | <span data-ttu-id="1832d-193">4</span><span class="sxs-lookup"><span data-stu-id="1832d-193">4</span></span>  |  
| <span data-ttu-id="1832d-194">30</span><span class="sxs-lookup"><span data-stu-id="1832d-194">30</span></span>   | <span data-ttu-id="1832d-195">60</span><span class="sxs-lookup"><span data-stu-id="1832d-195">60</span></span>  |  
| <span data-ttu-id="1832d-196">3600</span><span class="sxs-lookup"><span data-stu-id="1832d-196">3600</span></span>   | <span data-ttu-id="1832d-197">100</span><span class="sxs-lookup"><span data-stu-id="1832d-197">100</span></span>  |
| <span data-ttu-id="1832d-198">7200</span><span class="sxs-lookup"><span data-stu-id="1832d-198">7200</span></span> | <span data-ttu-id="1832d-199">150</span><span class="sxs-lookup"><span data-stu-id="1832d-199">150</span></span>  |
| <span data-ttu-id="1832d-200">86400</span><span class="sxs-lookup"><span data-stu-id="1832d-200">86400</span></span>  | <span data-ttu-id="1832d-201">1800</span><span class="sxs-lookup"><span data-stu-id="1832d-201">1800</span></span>  |

<span data-ttu-id="1832d-202">*Confira também* [Conectores do Office 365 — Microsoft Teams](https://docs.microsoft.com/connectors/teams/)</span><span class="sxs-lookup"><span data-stu-id="1832d-202">*See also* [Office 365 Connectors — Microsoft Teams](https://docs.microsoft.com/connectors/teams/)</span></span>

<span data-ttu-id="1832d-203">Uma [lógica de repetição com retirada exponencial](/azure/architecture/patterns/retry) como abaixo reduziria a limitação da taxa nos casos em que as solicitações excederem os limites em um segundo.</span><span class="sxs-lookup"><span data-stu-id="1832d-203">A [retry logic with exponential back-off](/azure/architecture/patterns/retry) like below would mitigate rate limiting for cases where requests are exceeding the limits within a second.</span></span> <span data-ttu-id="1832d-204">Siga as [práticas recomendadas](../../bots/how-to/rate-limit.md#best-practices) para evitar atingir os limites de taxa.</span><span class="sxs-lookup"><span data-stu-id="1832d-204">Please follow [best practices](../../bots/how-to/rate-limit.md#best-practices) to avoid hitting the rate limits.</span></span>

```csharp
// Please note that response body needs to be extracted and read 
// as Connectors do not throw 429s
try
{
    // Perform Connector POST operation     
    var httpResponseMessage = await _client.PostAsync(IncomingWebhookUrl, new StringContent(content));
    // Read response content
    var responseContent = await httpResponseMessage.Content.ReadAsStringAsync();
    if (responseContent.Contains("Microsoft Teams endpoint returned HTTP error 429")) 
    {
        // initiate retry logic
    }
}
```
 
<span data-ttu-id="1832d-205">Esses limites existem para reduzir o spam em um canal por um conector e garantem uma experiência ideal para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="1832d-205">These limits are in place to reduce spamming a channel by a connector and ensures an optimal experience to your end users.</span></span>
