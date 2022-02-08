---
title: Criar e enviar mensagens
author: laujan
description: Descreve como usar Conectores do Office 365 no Microsoft Teams
ms.topic: how-to
ms.localizationpriority: high
keywords: conector do Office365 para equipes
ms.openlocfilehash: 478bf9805c5f045e1f8c43ff7647dd418f6bd8af
ms.sourcegitcommit: c66da76fb766df6270095265e1da8c49a3afd195
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2022
ms.locfileid: "62435863"
---
# <a name="create-and-send-messages"></a>Criar e enviar mensagens

Você pode criar e enviar mensagens acionáveis por meio do Webhook de Entrada ou do Conector do Office 365.

## <a name="create-actionable-messages"></a>Criar mensagens acionáveis

As mensagens acionáveis incluem seis botões visíveis no cartão. Cada botão é definido na propriedade `potentialAction` da mensagem usando ações `ActionCard`, cada uma contendo um tipo de entrada: um campo de texto, um seletor de datas ou uma lista de várias opções. Cada ação `ActionCard` tem uma ação associada, por exemplo `HttpPOST`.

Os cartões de conector dão suporte às seguintes ações:

- `ActionCard`: Apresenta um ou mais tipos de entrada e ações associadas.
- `HttpPOST`: Envia uma solicitação POST a uma URL.
- `OpenUri`: Abre um URI em um navegador ou aplicativo separado; a opção visa URIs diferentes com base em sistemas operacionais.

A ação `ActionCard` oferece suporte a três tipos de entrada:

- `TextInput`: Um campo de texto de linha única ou de várias linhas com um limite de comprimento opcional.
- `DateInput`: Um seletor de data com um seletor de tempo opcional.
- `MultichoiceInput`: Uma lista enumerada de opções que oferece uma seleção única ou múltipla.

`MultichoiceInput` oferece suporte a uma propriedade `style` que controla se a lista já aparecerá totalmente expandida. O valor padrão de `style` depende do valor de `isMultiSelect` como segue:

| `isMultiSelect` | Padrão `style` |
| --- | --- |
| `false` ou não especificado  | `compact` |
| `true` | `expanded` |

Para exibir a lista de seleção múltipla no estilo compacto, você deve especificar `"isMultiSelect": true` e `"style": true`.

Para obter mais informações sobre ações de cartão do conector, veja [ Ações](/outlook/actionable-messages/card-reference#actions).

> [!NOTE]
> * Especificar `compact` para a propriedade `style` no Microsoft Teams é o mesmo que especificar `normal` para a propriedade `style` no Microsoft Outlook.
> * Para a ação HttpPOST, o token do portador é incluído com as solicitações. Esse token inclui a identidade do Azure AD do usuário do Office 365 que executou a ação.

## <a name="send-a-message-through-incoming-webhook-or-office-365-connector"></a>Enviar uma mensagem por meio do Webhook de Entrada ou do Conector do Office 365

Para enviar uma mensagem por meio do Conector do Office 365 ou do Webhook de entrada, poste uma carga JSON na URL do Webhook. Essa carga deve estar na forma de um [cartão conector Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

Também é possível usar esse JSON para criar cartões contendo entradas avançadas, como entrada de texto, seleção múltipla ou escolha de data e hora. O código que gera o cartão e as postagens na URL do Webhook pode ser executado em qualquer serviço hospedado. Esses cartões são definidos como parte de mensagens acionáveis e também são compatíveis com [cartões](~/task-modules-and-cards/what-are-cards.md) usados nos bots do Teams e nas Extensões de mensagens.

### <a name="example-of-connector-message"></a>Exemplo de mensagem do conector

Um exemplo de mensagem de conector é o seguinte:

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

Essa mensagem produz o seguinte cartão no canal:

![Captura de tela de um cartão do conector](~/assets/images/connectorcard.png)

## <a name="send-messages-using-curl-and-powershell"></a>Enviar mensagens usando cURL e PowerShell

# <a name="curl"></a>[cURL](#tab/cURL)

**Para postar uma mensagem no webhook com um cURL**

1. Instale o cURL usando: https://curl.haxx.se/.

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
    > Se o POST tiver êxito, você verá uma saída **1** simples por `curl`.

1. Verifique o cliente do Microsoft Teams para o novo cartão postado.

# <a name="powershell"></a>[PowerShell](#tab/PowerShell)

 Pré-requisito: Instalação do PowerShell e familiarização com seu uso básico.

**Para postar uma mensagem no webhook com o PowerShell**

1. Digite o seguinte comando no prompt do PowerShell:

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

    > [!NOTE]
    > Se o POST tiver êxito, você verá uma saída **1** simples por `Invoke-RestMethod`.

1. Verifique o canal do Microsoft Teams associado à URL do Webhook. Você deverá ver o novo cartão postado no canal. Antes de usar o conector para testar ou publicar seu aplicativo, você deve fazer o seguinte:

    - [Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).
    - Modifique a parte dos `icons` do manifesto para se referir aos nomes de arquivo dos ícones em vez das URLs.

---

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a>Envie Cartões Adaptáveis usando um Webhook de Entrada

> [!NOTE]
> * Todos os elementos de esquema dos Cartões Adaptáveis nativos, exceto `Action.Submit`, são totalmente suportados.
> * As ações suportadas são [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), e [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).

**Para enviar Cartões Adaptáveis através de um Webhook de Entrada**

1. [ Configurar um webhook personalizado](~/webhooks-and-connectors/how-to/add-incoming-webhook.md) no Teams.
1. Crie um arquivo JSON de Cartão Adaptável usando o seguinte código:

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

    As propriedades do arquivo JSON do Cartão Adaptável são as seguintes:

    * O campo `"type"` deve ser `"message"`.
    * A matriz `"attachments"` contém um conjunto de objetos de cartão.
    * O campo `"contentType"` deve ser definido para o tipo de Cartão adaptável.
    * O objeto `"content"` é o cartão formatado em JSON.

1. Teste seu Cartão Adaptável com o Postman:

    * Teste o Cartão Adaptável usando [Postman](https://www.postman.com) para enviar uma solicitação POST para a URL, criada para configurar o Webhook de Entrada.
    * Cole seu arquivo JSON no corpo da solicitação e visualize sua mensagem de cartão adaptável no Teams.

> [!TIP]
> Use o Cartão Adaptável [exemplos de código e formatos](https://adaptivecards.io/samples) para testar o corpo do pedido da PUBLICAÇÃO.

## <a name="rate-limiting-for-connectors"></a>Limitação de taxa para conectores

Os limites de taxa de aplicativos controlam o tráfego que um conector ou um Webhook de Entrada tem permissão para gerar em um canal. O Teams acompanha as solicitações por meio de uma janela de taxa fixa e de um contador incremental medido em segundos. Se mais de quatro solicitações forem feitas em um segundo, a conexão do cliente será limitada até que a janela seja atualizada durante a taxa fixa.

### <a name="transactions-per-second-thresholds"></a>Limites de transações por segundo

A tabela a seguir fornece os detalhes da transação baseada em tempo:

| Tempo em segundos  | Máximo de solicitações permitidas  |
|---|---|
| 1   | 4  |  
| 30   | 60  |  
| 3600   | 100  |
| 7200 | 150  |
| 86400  | 1800  |

Uma [lógica de repetição com retirada exponencial](/azure/architecture/patterns/retry) como abaixo reduziria a limitação da taxa nos casos em que as solicitações excederem os limites em um segundo. Siga as [práticas recomendadas](../../bots/how-to/rate-limit.md) para evitar atingir os limites de taxa.

> [!NOTE]
> Uma [lógica de repetição com retirada exponencial](/azure/architecture/patterns/retry) como abaixo reduziria a limitação da taxa nos casos em que as solicitações excederem os limites em um segundo. Referir [Respostas HTTP 429](../../bots/how-to/rate-limit.md#handle-http-429-responses) para evitar atingir os limites da taxa.

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

Esses limites existem para reduzir o spam em um canal por um conector e garantem uma experiência ideal para os usuários finais.

## <a name="see-also"></a>Confira também

* [Office 365 Connectors para Microsoft Teams](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Criar um webhook de Entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Criar um Webhook de Saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [A limitação de taxas para mensagens de bots do Teams](~/bots/how-to/rate-limit.md)
* [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Formatar cartões no Microsoft Teams](~/task-modules-and-cards/cards/cards-format.md)
