---
title: Criar e enviar mensagens
author: laujan
description: Descreve como usar Conectores do Office 365 no Microsoft Teams
ms.topic: how-to
ms.localizationpriority: medium
keywords: conector do o365 no teams
ms.openlocfilehash: 46a0bc8ad797d5fc856e44fe662faf208cb7b5bb
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887389"
---
# <a name="create-and-send-messages"></a>Criar e enviar mensagens

Você pode criar mensagens ativas e enviá-las por meio do Webhook de entrada ou Office 365 Connector.

## <a name="create-actionable-messages"></a>Criar mensagens ativas

As mensagens ativas incluem três botões visíveis no cartão. Cada botão é definido na propriedade da mensagem usando ações, cada uma com um tipo de entrada, um campo de texto, um selador de datas ou uma lista `potentialAction` `ActionCard` de várias opções. Cada `ActionCard` uma tem uma ação associada, por exemplo `HttpPOST` .

Os cartões conectores suportam as seguintes ações:

- `ActionCard`: Apresenta um ou mais tipos de entrada e ações associadas.
- `HttpPOST`: Envia solicitação POST a uma URL.
- `OpenUri`: Abre o URI em um navegador ou aplicativo separado, opcionalmente direciona URIs diferentes com base em sistemas operacionais.

A ação `ActionCard` oferece suporte a três tipos de entrada:

- `TextInput`: Um campo de texto de linha única ou de várias linhas com um limite de comprimento opcional.
- `DateInput`: Um seletor de datas com um seletor de hora opcional.
- `MultichoiceInput`: Uma lista enumerada de opções oferecendo uma única seleção ou várias seleções.

`MultichoiceInput` oferece suporte a uma propriedade `style` que controla se a lista já aparecerá totalmente expandida. O valor padrão `style` de depende do valor `isMultiSelect` de:

| `isMultiSelect` | Padrão `style` |
| --- | --- |
| `false` ou não especificado  | `compact` |
| `true` | `expanded` |

Para exibir a lista de várias seleções no estilo compacto, você deve especificar `"isMultiSelect": true` ambos e `"style": true` .

Para obter mais informações sobre ações de cartão de conector, consulte [Actions](/outlook/actionable-messages/card-reference#actions).

> [!NOTE]
> * Especificar `compact` para a propriedade `style` no Microsoft Teams é o mesmo que especificar `normal` para a propriedade `style` no Microsoft Outlook.
> * Para a ação HttpPOST, o token do portador é incluído com as solicitações. Esse token inclui a identidade do Azure AD do usuário do Office 365 que executou a ação.

## <a name="send-a-message-through-incoming-webhook-or-office-365-connector"></a>Enviar uma mensagem por meio de Webhook de entrada ou Office 365 Conector

Para enviar uma mensagem por meio do Webhook de entrada ou Office 365 Conector, poste uma carga JSON na URL do webhook. Essa carga deve estar na forma de um cartão [Office 365 conector.](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)

Você também pode usar esse JSON para criar cartões contendo entradas ricas, como entrada de texto, várias seleções ou seleção de data e hora. O código que gera o cartão e o posta na URL do webhook pode ser executado em qualquer serviço hospedado. Esses cartões são definidos como parte de mensagens ativas e também são suportados em cartões [,](~/task-modules-and-cards/what-are-cards.md)usados Teams bots e extensões de mensagens.

### <a name="example-of-connector-message"></a>Exemplo de mensagem de conector

Um exemplo de mensagem do conector é o seguinte:

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

Esta mensagem fornece o seguinte cartão no canal:

![Captura de tela de um cartão do conector](~/assets/images/connectorcard.png)

## <a name="send-messages-using-curl-and-powershell"></a>Enviar mensagens usando cURL e PowerShell

# <a name="curl"></a>[cURL](#tab/cURL)

**Para postar uma mensagem no webhook com cURL**

1. Instalar cURL usando: https://curl.haxx.se/ .

1. Na linha de comando, insira o seguinte comando cURL:

   ```bash
   // on macOS or Linux
   curl -H 'Content-Type: application/json' -d '{"text": "Hello World"}' <YOUR WEBHOOK URL>
   ```

   ```bash
   // on Windows
   curl.exe -H "Content-Type:application/json" -d "{'text':'Hello World'}" <YOUR WEBHOOK URL>
   ```

    > [!NOTE]
    > Se o POST for bem-sucedido, você deverá ver uma saída **simples 1** por `curl` .

1. Verifique o Microsoft Teams cliente do novo cartão postado.

# <a name="powershell"></a>[PowerShell](#tab/PowerShell)

 Pré-requisito: Instalação do PowerShell e familiarização com seu uso básico.

**Para postar uma mensagem no webhook com o PowerShell**

1. Digite o seguinte comando no prompt do PowerShell:

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

    > [!NOTE]
    > Se o POST for bem-sucedido, você deverá ver uma saída **simples 1** por `Invoke-RestMethod` .

1. Verifique o canal do Microsoft Teams associado à URL do Webhook. Você pode ver o novo cartão postado no canal. Antes de usar o conector para testar ou publicar seu aplicativo, faça o seguinte:

    - [Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).
    - Modifique `icons` a parte do manifesto para os nomes de arquivo dos ícones em vez de URLs.

---

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a>Enviar cartões adaptáveis usando um Webhook de entrada

> [!NOTE]
> * Todos os elementos de esquema de Cartão Adaptável nativos, exceto `Action.Submit` , são totalmente suportados.
> * As ações suportadas são [**Action.OpenURL,**](https://adaptivecards.io/explorer/Action.OpenUrl.html) [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html)e [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).

**Para enviar cartões adaptáveis por meio de um Webhook de entrada**

1. [Configurar um webhook personalizado](~/webhooks-and-connectors/how-to/add-incoming-webhook.md) Teams.
1. Criar arquivo JSON de cartão adaptável usando o seguinte código:

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

    As propriedades do arquivo JSON do Cartão Adaptável são as seguinte:

    * O campo `"type"` deve ser `"message"`.
    * A matriz `"attachments"` contém um conjunto de objetos de cartão.
    * O `"contentType"` campo deve ser definido como Tipo de Cartão Adaptável.
    * O objeto `"content"` é o cartão formatado em JSON.

1. Teste seu Cartão Adaptável com Postman:

    * Teste o Cartão Adaptável usando [o Postman](https://www.postman.com) para enviar uma solicitação POST para a URL, criada para configurar o Webhook de Entrada.
    * Colar o arquivo JSON no corpo da solicitação e exibir a mensagem Cartão Adaptável em Teams.

> [!TIP]
> Use [exemplos](https://adaptivecards.io/samples) e modelos de código de Cartão Adaptável para testar o corpo da solicitação POST.

## <a name="rate-limiting-for-connectors"></a>Limitação de taxa para conectores

Os limites de taxa de aplicativo controlam o tráfego que um conector ou um Webhook de Entrada tem permissão para gerar em um canal. Teams rastrear solicitações usando uma janela de taxa fixa e um contador incremental medido em segundos. Se mais de quatro solicitações são feitas em um segundo, a conexão do cliente é acelerada até que a janela seja atualizada durante a duração da taxa fixa.

### <a name="transactions-per-second-thresholds"></a>Limites de transações por segundo

A tabela a seguir fornece os detalhes da transação baseada em hora:

| Tempo em segundos  | Máximo de solicitações permitidas  |
|---|---|
| 1   | 4  |  
| 30   | 60  |  
| 3600   | 100  |
| 7200 | 150  |
| 86400  | 1800  |

Uma [lógica de nova tentativa com back-off](/azure/architecture/patterns/retry) exponencial pode reduzir a limitação de taxa para casos em que as solicitações estão excedendo os limites em um segundo. Siga [as práticas recomendadas](../../bots/how-to/rate-limit.md) para evitar atingir os limites de taxa.

> [!NOTE]
> Uma [lógica de nova tentativa com back-off](/azure/architecture/patterns/retry) exponencial pode reduzir a limitação de taxa para casos em que as solicitações estão excedendo os limites em um segundo. Referir [Respostas HTTP 429](../../bots/how-to/rate-limit.md#handle-http-429-responses) para evitar atingir os limites da taxa.

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

Esses limites estão no local para reduzir a spam de um canal por um conector e garante uma experiência ideal para os usuários.

## <a name="see-also"></a>Confira também

* [Office 365 Conectores para Microsoft Teams](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Criar um Webhook de entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Criar um Webhook de Saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [Limitação de taxa para Teams bots](~/bots/how-to/rate-limit.md)
* [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)
