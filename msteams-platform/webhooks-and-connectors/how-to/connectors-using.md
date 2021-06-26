---
title: Criar e enviar mensagens
author: laujan
description: Descreve como usar Conectores do Office 365 no Microsoft Teams
ms.topic: how-to
localization_priority: Normal
keywords: conector do o365 no teams
ms.openlocfilehash: e396d0048831634f683b6df925853464698fb96a
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140521"
---
# <a name="create-and-send-messages"></a><span data-ttu-id="51580-104">Criar e enviar mensagens</span><span class="sxs-lookup"><span data-stu-id="51580-104">Create and send messages</span></span>

<span data-ttu-id="51580-105">Você pode criar mensagens ativas e enviá-las por meio do Webhook de entrada ou Office 365 Connector.</span><span class="sxs-lookup"><span data-stu-id="51580-105">You can create actionable messages and send it through Incoming Webhook or Office 365 Connector.</span></span>

## <a name="create-actionable-messages"></a><span data-ttu-id="51580-106">Criar mensagens ativas</span><span class="sxs-lookup"><span data-stu-id="51580-106">Create actionable messages</span></span>

<span data-ttu-id="51580-107">As mensagens ativas incluem três botões visíveis no cartão.</span><span class="sxs-lookup"><span data-stu-id="51580-107">The actionable messages include three visible buttons on the card.</span></span> <span data-ttu-id="51580-108">Cada botão é definido na propriedade da mensagem usando ações, cada uma com um tipo de entrada, um campo de texto, um selador de datas ou uma lista `potentialAction` `ActionCard` de várias opções.</span><span class="sxs-lookup"><span data-stu-id="51580-108">Each button is defined in the `potentialAction` property of the message by using `ActionCard` actions, each with an input type, a text field, a date picker, or a multi-choice list.</span></span> <span data-ttu-id="51580-109">Cada `ActionCard` uma tem uma ação associada, por exemplo `HttpPOST` .</span><span class="sxs-lookup"><span data-stu-id="51580-109">Each `ActionCard` has an associated action, for example `HttpPOST`.</span></span>

<span data-ttu-id="51580-110">Os cartões conectores suportam as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="51580-110">The connector cards support the following actions:</span></span>

- <span data-ttu-id="51580-111">`ActionCard`: Apresenta um ou mais tipos de entrada e ações associadas.</span><span class="sxs-lookup"><span data-stu-id="51580-111">`ActionCard`: Presents one or more input types and associated actions.</span></span>
- <span data-ttu-id="51580-112">`HttpPOST`: Envia solicitação POST a uma URL.</span><span class="sxs-lookup"><span data-stu-id="51580-112">`HttpPOST`: Sends POST request to a URL.</span></span>
- <span data-ttu-id="51580-113">`OpenUri`: Abre o URI em um navegador ou aplicativo separado, opcionalmente direciona URIs diferentes com base em sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="51580-113">`OpenUri`: Opens URI in a separate browser or app, optionally targets different URIs based on operating systems.</span></span>

<span data-ttu-id="51580-114">A ação `ActionCard` oferece suporte a três tipos de entrada:</span><span class="sxs-lookup"><span data-stu-id="51580-114">The `ActionCard` action supports three input types:</span></span>

- <span data-ttu-id="51580-115">`TextInput`: Um campo de texto de linha única ou de várias linhas com um limite de comprimento opcional.</span><span class="sxs-lookup"><span data-stu-id="51580-115">`TextInput`: A single line or multiline text field with an optional length limit.</span></span>
- <span data-ttu-id="51580-116">`DateInput`: Um seletor de datas com um seletor de hora opcional.</span><span class="sxs-lookup"><span data-stu-id="51580-116">`DateInput`: A date selector with an optional time selector.</span></span>
- <span data-ttu-id="51580-117">`MultichoiceInput`: Uma lista enumerada de opções oferecendo uma única seleção ou várias seleções.</span><span class="sxs-lookup"><span data-stu-id="51580-117">`MultichoiceInput`: An enumerated list of choices offering either a single selection or multiple selections.</span></span>

<span data-ttu-id="51580-118">`MultichoiceInput` oferece suporte a uma propriedade `style` que controla se a lista já aparecerá totalmente expandida.</span><span class="sxs-lookup"><span data-stu-id="51580-118">`MultichoiceInput` supports a `style` property that controls whether the list initially appears fully expanded.</span></span> <span data-ttu-id="51580-119">O valor padrão `style` de depende do valor `isMultiSelect` de:</span><span class="sxs-lookup"><span data-stu-id="51580-119">The default value of `style` depends on the value of `isMultiSelect` as follows:</span></span>

| `isMultiSelect` | <span data-ttu-id="51580-120">Padrão `style`</span><span class="sxs-lookup"><span data-stu-id="51580-120">`style` default</span></span> |
| --- | --- |
| <span data-ttu-id="51580-121">`false` ou não especificado </span><span class="sxs-lookup"><span data-stu-id="51580-121">`false` or not specified</span></span> | `compact` |
| `true` | `expanded` |

<span data-ttu-id="51580-122">Para exibir a lista de várias seleções no estilo compacto, você deve especificar `"isMultiSelect": true` ambos e `"style": true` .</span><span class="sxs-lookup"><span data-stu-id="51580-122">To display the multiselect list in the compact style, you must specify both `"isMultiSelect": true` and `"style": true`.</span></span>

<span data-ttu-id="51580-123">Para obter mais informações sobre ações de cartão de conector, consulte [Actions](/outlook/actionable-messages/card-reference#actions).</span><span class="sxs-lookup"><span data-stu-id="51580-123">For more information on connector card actions, see [Actions](/outlook/actionable-messages/card-reference#actions).</span></span>

> [!NOTE]
> * <span data-ttu-id="51580-124">Especificar `compact` para a propriedade `style` no Microsoft Teams é o mesmo que especificar `normal` para a propriedade `style` no Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="51580-124">Specifying `compact` for the `style` property in Microsoft Teams is the same as specifying `normal` for the `style` property in Microsoft Outlook.</span></span>
> * <span data-ttu-id="51580-125">Para a ação HttpPOST, o token do portador é incluído com as solicitações.</span><span class="sxs-lookup"><span data-stu-id="51580-125">For the HttpPOST action, the bearer token is included with the requests.</span></span> <span data-ttu-id="51580-126">Esse token inclui a identidade do Azure AD do usuário do Office 365 que executou a ação.</span><span class="sxs-lookup"><span data-stu-id="51580-126">This token includes the Azure AD identity of the Office 365 user who took the action.</span></span>

## <a name="send-a-message-through-incoming-webhook-or-office-365-connector"></a><span data-ttu-id="51580-127">Enviar uma mensagem por meio de Webhook de entrada ou Office 365 Conector</span><span class="sxs-lookup"><span data-stu-id="51580-127">Send a message through Incoming Webhook or Office 365 Connector</span></span>

<span data-ttu-id="51580-128">Para enviar uma mensagem por meio do Webhook de entrada ou Office 365 Conector, poste uma carga JSON na URL do webhook.</span><span class="sxs-lookup"><span data-stu-id="51580-128">To send a message through your Incoming Webhook or Office 365 Connector, post a JSON payload to the webhook URL.</span></span> <span data-ttu-id="51580-129">Essa carga deve estar na forma de um cartão [Office 365 conector.](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)</span><span class="sxs-lookup"><span data-stu-id="51580-129">This payload must be in the form of an [Office 365 connector card](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="51580-130">Você também pode usar esse JSON para criar cartões contendo entradas ricas, como entrada de texto, várias seleções ou seleção de data e hora.</span><span class="sxs-lookup"><span data-stu-id="51580-130">You can also use this JSON to create cards containing rich inputs, such as text entry, multiselect, or selecting date and time.</span></span> <span data-ttu-id="51580-131">O código que gera o cartão e o posta na URL do webhook pode ser executado em qualquer serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="51580-131">The code that generates the card and posts it to the webhook URL can run on any hosted service.</span></span> <span data-ttu-id="51580-132">Esses cartões são definidos como parte de mensagens ativas e também são suportados em cartões [,](~/task-modules-and-cards/what-are-cards.md)usados Teams bots e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="51580-132">These cards are defined as part of actionable messages and are also supported in [cards](~/task-modules-and-cards/what-are-cards.md), used in Teams bots and messaging extensions.</span></span>

### <a name="example-of-connector-message"></a><span data-ttu-id="51580-133">Exemplo de mensagem de conector</span><span class="sxs-lookup"><span data-stu-id="51580-133">Example of connector message</span></span>

<span data-ttu-id="51580-134">Um exemplo de mensagem do conector é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="51580-134">An example of connector message is as follows:</span></span>

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

<span data-ttu-id="51580-135">Esta mensagem fornece o seguinte cartão no canal:</span><span class="sxs-lookup"><span data-stu-id="51580-135">This message provides the following card in the channel:</span></span>

![Captura de tela de um cartão do conector](~/assets/images/connectorcard.png)

## <a name="send-messages-using-curl-and-powershell"></a><span data-ttu-id="51580-137">Enviar mensagens usando cURL e PowerShell</span><span class="sxs-lookup"><span data-stu-id="51580-137">Send messages using cURL and PowerShell</span></span>

# <a name="curl"></a>[<span data-ttu-id="51580-138">cURL</span><span class="sxs-lookup"><span data-stu-id="51580-138">cURL</span></span>](#tab/cURL)

<span data-ttu-id="51580-139">**Para postar uma mensagem no webhook com cURL**</span><span class="sxs-lookup"><span data-stu-id="51580-139">**To post a message in the webhook with cURL**</span></span>

1. <span data-ttu-id="51580-140">Instalar cURL usando: https://curl.haxx.se/ .</span><span class="sxs-lookup"><span data-stu-id="51580-140">Install cURL using: https://curl.haxx.se/.</span></span>

1. <span data-ttu-id="51580-141">Na linha de comando, insira o seguinte comando cURL:</span><span class="sxs-lookup"><span data-stu-id="51580-141">From the command line, enter the following cURL command:</span></span>

   ```bash
   // on macOS or Linux
   curl -H 'Content-Type: application/json' -d '{"text": "Hello World"}' <YOUR WEBHOOK URL>
   ```

   ```bash
   // on Windows
   curl.exe -H "Content-Type:application/json" -d "{'text':'Hello World'}" <YOUR WEBHOOK URL>
   ```

    > [!NOTE]
    > <span data-ttu-id="51580-142">Se o POST for bem-sucedido, você deverá ver uma saída **simples 1** por `curl` .</span><span class="sxs-lookup"><span data-stu-id="51580-142">If the POST succeeds, you must see a simple **1** output by `curl`.</span></span>

1. <span data-ttu-id="51580-143">Verifique o Microsoft Teams cliente do novo cartão postado.</span><span class="sxs-lookup"><span data-stu-id="51580-143">Check the Microsoft Teams client for the new card posted.</span></span>

# <a name="powershell"></a>[<span data-ttu-id="51580-144">PowerShell</span><span class="sxs-lookup"><span data-stu-id="51580-144">PowerShell</span></span>](#tab/PowerShell)

 <span data-ttu-id="51580-145">Pré-requisito: Instalação do PowerShell e familiarização com seu uso básico.</span><span class="sxs-lookup"><span data-stu-id="51580-145">Prerequisite: Installation of PowerShell and familiarization with its basic usage.</span></span>

<span data-ttu-id="51580-146">**Para postar uma mensagem no webhook com o PowerShell**</span><span class="sxs-lookup"><span data-stu-id="51580-146">**To post a message to the webhook with PowerShell**</span></span>

1. <span data-ttu-id="51580-147">Digite o seguinte comando no prompt do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="51580-147">From the PowerShell prompt, enter the following command:</span></span>

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

    > [!NOTE]
    > <span data-ttu-id="51580-148">Se o POST for bem-sucedido, você deverá ver uma saída **simples 1** por `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="51580-148">If the POST succeeds, you must see a simple **1** output by `Invoke-RestMethod`.</span></span>

1. <span data-ttu-id="51580-149">Verifique o canal do Microsoft Teams associado à URL do Webhook.</span><span class="sxs-lookup"><span data-stu-id="51580-149">Check the Microsoft Teams channel associated with the webhook URL.</span></span> <span data-ttu-id="51580-150">Você pode ver o novo cartão postado no canal.</span><span class="sxs-lookup"><span data-stu-id="51580-150">You can see the new card posted to the channel.</span></span> <span data-ttu-id="51580-151">Antes de usar o conector para testar ou publicar seu aplicativo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="51580-151">Before you use the connector to test or publish your app, you must do the following:</span></span>

    - <span data-ttu-id="51580-152">[Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="51580-152">[Include two icons](../../concepts/build-and-test/apps-package.md#app-icons).</span></span>
    - <span data-ttu-id="51580-153">Modifique `icons` a parte do manifesto para os nomes de arquivo dos ícones em vez de URLs.</span><span class="sxs-lookup"><span data-stu-id="51580-153">Modify the `icons` portion of the manifest to the file names of the icons instead of URLs.</span></span>

---

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a><span data-ttu-id="51580-154">Enviar cartões adaptáveis usando um Webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="51580-154">Send Adaptive Cards using an Incoming Webhook</span></span>

> [!NOTE]
> * <span data-ttu-id="51580-155">Todos os elementos de esquema de Cartão Adaptável nativos, exceto `Action.Submit` , são totalmente suportados.</span><span class="sxs-lookup"><span data-stu-id="51580-155">All native Adaptive Card schema elements, except `Action.Submit`, are fully supported.</span></span>
> * <span data-ttu-id="51580-156">As ações suportadas são [**Action.OpenURL,**](https://adaptivecards.io/explorer/Action.OpenUrl.html) [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html)e [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span><span class="sxs-lookup"><span data-stu-id="51580-156">The supported actions are [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), and [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span></span>

<span data-ttu-id="51580-157">**Para enviar cartões adaptáveis por meio de um Webhook de entrada**</span><span class="sxs-lookup"><span data-stu-id="51580-157">**To send Adaptive Cards through an Incoming Webhook**</span></span>

1. <span data-ttu-id="51580-158">[Configurar um webhook personalizado](/add-incoming-webhook.md) Teams.</span><span class="sxs-lookup"><span data-stu-id="51580-158">[Setup a custom webhook](/add-incoming-webhook.md) in Teams.</span></span>
1. <span data-ttu-id="51580-159">Criar arquivo JSON de cartão adaptável usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="51580-159">Create Adaptive Card JSON file using the following code:</span></span>

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

    <span data-ttu-id="51580-160">As propriedades do arquivo JSON do Cartão Adaptável são as seguinte:</span><span class="sxs-lookup"><span data-stu-id="51580-160">The properties for Adaptive Card JSON file are as follows:</span></span>

    * <span data-ttu-id="51580-161">O campo `"type"` deve ser `"message"`.</span><span class="sxs-lookup"><span data-stu-id="51580-161">The `"type"` field must be `"message"`.</span></span>
    * <span data-ttu-id="51580-162">A matriz `"attachments"` contém um conjunto de objetos de cartão.</span><span class="sxs-lookup"><span data-stu-id="51580-162">The `"attachments"` array contains a set of card objects.</span></span>
    * <span data-ttu-id="51580-163">O `"contentType"` campo deve ser definido como Tipo de Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="51580-163">The `"contentType"` field must be set to Adaptive Card type.</span></span>
    * <span data-ttu-id="51580-164">O objeto `"content"` é o cartão formatado em JSON.</span><span class="sxs-lookup"><span data-stu-id="51580-164">The `"content"` object is the card formatted in JSON.</span></span>

1. <span data-ttu-id="51580-165">Teste seu Cartão Adaptável com Postman:</span><span class="sxs-lookup"><span data-stu-id="51580-165">Test your Adaptive Card with Postman:</span></span>

    * <span data-ttu-id="51580-166">Teste o Cartão Adaptável usando [o Postman](https://www.postman.com) para enviar uma solicitação POST para a URL, criada para configurar o Webhook de Entrada.</span><span class="sxs-lookup"><span data-stu-id="51580-166">Test the Adaptive Card using [Postman](https://www.postman.com) to send a POST request to the URL, created to set up Incoming Webhook.</span></span>
    * <span data-ttu-id="51580-167">Colar o arquivo JSON no corpo da solicitação e exibir a mensagem Cartão Adaptável em Teams.</span><span class="sxs-lookup"><span data-stu-id="51580-167">Paste the JSON file in the body of the request and view the Adaptive Card message in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="51580-168">Use [exemplos](https://adaptivecards.io/samples) e modelos de código de Cartão Adaptável para testar o corpo da solicitação POST.</span><span class="sxs-lookup"><span data-stu-id="51580-168">Use Adaptive Card [code samples and templates](https://adaptivecards.io/samples) to test the body of POST request.</span></span>

## <a name="rate-limiting-for-connectors"></a><span data-ttu-id="51580-169">Limitação de taxa para conectores</span><span class="sxs-lookup"><span data-stu-id="51580-169">Rate limiting for connectors</span></span>

<span data-ttu-id="51580-170">Os limites de taxa de aplicativo controlam o tráfego que um conector ou um Webhook de Entrada tem permissão para gerar em um canal.</span><span class="sxs-lookup"><span data-stu-id="51580-170">Application rate limits control the traffic that a connector or an Incoming Webhook is permitted to generate on a channel.</span></span> <span data-ttu-id="51580-171">Teams rastrear solicitações usando uma janela de taxa fixa e um contador incremental medido em segundos.</span><span class="sxs-lookup"><span data-stu-id="51580-171">Teams track requests using a fixed rate window and incremental counter measured in seconds.</span></span> <span data-ttu-id="51580-172">Se mais de quatro solicitações são feitas em um segundo, a conexão do cliente é acelerada até que a janela seja atualizada durante a duração da taxa fixa.</span><span class="sxs-lookup"><span data-stu-id="51580-172">If more than four requests are made in a second, the client connection is throttled until the window refreshes for the duration of the fixed rate.</span></span>

### <a name="transactions-per-second-thresholds"></a><span data-ttu-id="51580-173">Limites de transações por segundo</span><span class="sxs-lookup"><span data-stu-id="51580-173">Transactions per second thresholds</span></span>

<span data-ttu-id="51580-174">A tabela a seguir fornece os detalhes da transação baseada em hora:</span><span class="sxs-lookup"><span data-stu-id="51580-174">The following table provides the time based transaction details:</span></span>

| <span data-ttu-id="51580-175">Tempo em segundos</span><span class="sxs-lookup"><span data-stu-id="51580-175">Time in seconds</span></span>  | <span data-ttu-id="51580-176">Máximo de solicitações permitidas</span><span class="sxs-lookup"><span data-stu-id="51580-176">Maximum allowed requests</span></span>  |
|---|---|
| <span data-ttu-id="51580-177">1 </span><span class="sxs-lookup"><span data-stu-id="51580-177">1</span></span>   | <span data-ttu-id="51580-178">4 </span><span class="sxs-lookup"><span data-stu-id="51580-178">4</span></span>  |  
| <span data-ttu-id="51580-179">30</span><span class="sxs-lookup"><span data-stu-id="51580-179">30</span></span>   | <span data-ttu-id="51580-180">60</span><span class="sxs-lookup"><span data-stu-id="51580-180">60</span></span>  |  
| <span data-ttu-id="51580-181">3600</span><span class="sxs-lookup"><span data-stu-id="51580-181">3600</span></span>   | <span data-ttu-id="51580-182">100</span><span class="sxs-lookup"><span data-stu-id="51580-182">100</span></span>  |
| <span data-ttu-id="51580-183">7200</span><span class="sxs-lookup"><span data-stu-id="51580-183">7200</span></span> | <span data-ttu-id="51580-184">150</span><span class="sxs-lookup"><span data-stu-id="51580-184">150</span></span>  |
| <span data-ttu-id="51580-185">86400</span><span class="sxs-lookup"><span data-stu-id="51580-185">86400</span></span>  | <span data-ttu-id="51580-186">1800</span><span class="sxs-lookup"><span data-stu-id="51580-186">1800</span></span>  |

<span data-ttu-id="51580-187">Uma [lógica de nova tentativa com back-off](/azure/architecture/patterns/retry) exponencial pode reduzir a limitação de taxa para casos em que as solicitações estão excedendo os limites em um segundo.</span><span class="sxs-lookup"><span data-stu-id="51580-187">A [retry logic with exponential back-off](/azure/architecture/patterns/retry) can mitigate rate limiting for cases where requests are exceeding the limits within a second.</span></span> <span data-ttu-id="51580-188">Siga [as práticas recomendadas](../../bots/how-to/rate-limit.md) para evitar atingir os limites de taxa.</span><span class="sxs-lookup"><span data-stu-id="51580-188">Follow [best practices](../../bots/how-to/rate-limit.md) to avoid hitting the rate limits.</span></span>

> [!NOTE]
> <span data-ttu-id="51580-189">Uma [lógica de nova tentativa com back-off](/azure/architecture/patterns/retry) exponencial pode reduzir a limitação de taxa para casos em que as solicitações estão excedendo os limites em um segundo.</span><span class="sxs-lookup"><span data-stu-id="51580-189">A [retry logic with exponential back-off](/azure/architecture/patterns/retry) can mitigate rate limiting for cases where requests are exceeding the limits within a second.</span></span> <span data-ttu-id="51580-190">Referir [Respostas HTTP 429](../../bots/how-to/rate-limit.md#handle-http-429-responses) para evitar atingir os limites da taxa.</span><span class="sxs-lookup"><span data-stu-id="51580-190">Refer [HTTP 429 responses](../../bots/how-to/rate-limit.md#handle-http-429-responses) to avoid hitting the rate limits.</span></span>

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

<span data-ttu-id="51580-191">Esses limites estão no local para reduzir a spam de um canal por um conector e garante uma experiência ideal para os usuários.</span><span class="sxs-lookup"><span data-stu-id="51580-191">These limits are in place to reduce spamming a channel by a connector and ensures an optimal experience to users.</span></span>

## <a name="see-also"></a><span data-ttu-id="51580-192">Também consulte</span><span class="sxs-lookup"><span data-stu-id="51580-192">See also</span></span>

* [<span data-ttu-id="51580-193">Office 365 Conectores para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="51580-193">Office 365 Connectors for Microsoft Teams</span></span>](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [<span data-ttu-id="51580-194">Criar um Webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="51580-194">Create an Incoming Webhook</span></span>](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [<span data-ttu-id="51580-195">Criar um Webhook de Saída</span><span class="sxs-lookup"><span data-stu-id="51580-195">Create an Outgoing Webhook</span></span>](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
