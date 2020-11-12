---
title: Enviar mensagens a Conectores e WebHooks
description: Descreve como usar Conectores do Office 365 no Microsoft Teams
localization_priority: Priority
keywords: conector do o365 no teams
ms.openlocfilehash: 913e441e6953102eeef2295625ce3e0734934bd9
ms.sourcegitcommit: 0aeb60027f423d8ceff3b377db8c3efbb6da4d17
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48998004"
---
# <a name="sending-messages-to-connectors-and-webhooks"></a>Enviar mensagens a conectores e webhooks

Para enviar uma mensagem por meio do Conector do Office 365 ou do Webhook de entrada, poste uma carga JSON na URL do Webhook. Geralmente, essa carga estará no formato de [Cartão do Conector do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

Também é possível usar esse JSON para criar cartões contendo entradas avançadas, como entrada de texto, seleção múltipla ou escolha de data e hora. O código que gera o cartão e as postagens na URL do Webhook pode ser executado em qualquer serviço hospedado. Esses cartões são definidos como parte de mensagens acionáveis e também são compatíveis com [cartões](~/task-modules-and-cards/what-are-cards.md) usados nos bots do Teams e nas Extensões de mensagens.

### <a name="example-connector-message"></a>Exemplo de mensagem do conector

```json
{
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "themeColor": "0076D7",
    "summary": "Larry Bryant created a new task",
    "sections": [{
        "activityTitle": "![TestImage](https://47a92947.ngrok.io/Content/Images/default.png)Larry Bryant created a new task",
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
            "target": "http://..."
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
            "target": "http://..."
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
            "target": "http://..."
        }]
    }]
}
```

Essa mensagem produz o seguinte cartão no canal.

![Captura de tela de um Cartão do conector](~/assets/images/connectors/connector_message.png)

## <a name="creating-actionable-messages"></a>Criar mensagens acionáveis

O exemplo na seção anterior inclui três botões visíveis no cartão. Cada botão é definido na propriedade `potentialAction` da mensagem usando ações `ActionCard`, cada uma contendo um tipo de entrada: um campo de texto, um seletor de datas ou uma lista de várias opções. Cada ação `ActionCard` tem uma ação associada, por exemplo `HttpPOST`.

Os cartões do conector oferecem suporte a três tipos de ações:

- `ActionCard` Apresenta um ou mais tipos de entrada e ações associadas
- `HttpPOST` Envia uma solicitação POST a uma URL
- `OpenUri` Abre um URI em um navegador ou aplicativo separado; a opção visa URIs diferentes com base em sistemas operacionais

(Uma quarta ação, `ViewAction`, ainda tem suporte, mas não é mais necessária; use `OpenUri` em vez disso.)

A ação `ActionCard` oferece suporte a três tipos de entrada:

- `TextInput` Um campo de texto de linha única ou de várias linhas com um limite de comprimento opcional
- `DateInput` Um seletor de data com um seletor de tempo opcional
- `MultichoiceInput` Uma lista enumerada de opções que oferece uma seleção única ou múltipla.

`MultichoiceInput` oferece suporte a uma propriedade `style` que controla se a lista já aparecerá totalmente expandida. O valor padrão de `style` depende do valor de `isMultiSelect`.

| `isMultiSelect` | Padrão `style` |
| --- | --- |
| `false` ou não especificado  | `compact` |
| `true` | `expanded` |

Se desejar que uma lista de seleção múltipla seja exibida inicialmente no estilo compacto, especifique `"isMultiSelect": true` e `"style": true`.

> [!NOTE]
> Especificar `compact` para a propriedade `style` no Microsoft Teams é o mesmo que especificar `normal` para a propriedade `style` no Microsoft Outlook.

Para todos os outros detalhes sobre as Ações do cartão do conector, confira **[Ações](/outlook/actionable-messages/card-reference#actions)** na referência do cartão de mensagem acionável.

## <a name="setting-up-a-custom-incoming-webhook"></a>Configurando um webhook de entrada personalizado

Siga estas etapas para ver como enviar um cartão simples para um Conector.

1. No Microsoft Teams, escolha **Mais opções** ( **&#8943;** ) ao lado do nome do canal e escolha **Conectores**.
2. Role pela lista de Conectores para o **Webhook de entrada** e escolha **Adicionar**.
3. Digite um nome para o Webhook, carregue uma imagem para associar aos dados dele e escolha **Criar**.
4. Copie o Webhook para a área de transferência e salve-o. Será necessário a URL do Webhook para enviar informações ao Microsoft Teams.
5. Escolha **Concluído**.

### <a name="post-a-message-to-the-webhook-using-curl"></a>Postar uma mensagem no Webhook usando cURL

As etapas a seguir usam [cURL](https://curl.haxx.se/). Iremos supor que você o tenha instalado e esteja familiarizado com seu uso básico.

1. Na linha de comando, insira o seguinte comando cURL:

   ```bash
   // on macOS or Linux
   curl -H 'Content-Type: application/json' -d '{"text": "Hello World"}' <YOUR WEBHOOK URL>
   ```

   ```bash
   // on Windows
   curl.exe -H "Content-Type:application/json" -d "{'text':'Hello World'}" <YOUR WEBHOOK URL>
   ```

2. Se o POST tiver êxito, você verá uma saída **1** simples por `curl`.
3. Verifique o cliente do Microsoft Team. Você deverá ver o novo cartão postado na equipe.

### <a name="post-a-message-to-the-webhook-using-powershell"></a>Postar uma mensagem no Webhook usando PowerShell

As etapas a seguir usam o PowerShell. Iremos supor que você o tenha instalado e esteja familiarizado com seu uso básico.

1. Digite o seguinte comando no prompt do PowerShell:

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

2. Se o POST tiver êxito, você verá uma saída **1** simples por `Invoke-RestMethod`.
3. Verifique o canal do Microsoft Teams associado à URL do Webhook. Você deverá ver o novo cartão postado no canal.

- Inclua dois ícones, seguindo as instruções nos [ícones](~/concepts/build-and-test/apps-package.md#icons).
- Modifique a parte dos `icons` do manifesto para se referir aos nomes de arquivo dos ícones em vez das URLs.

O seguinte arquivo manifest.json contém os elementos básicos necessários para testar e enviar seu aplicativo.

> [!NOTE]
> Substitua `id` e `connectorId` no exemplo a seguir pelo GUID do Conector.

#### <a name="example-manifestjson-with-connector"></a>Exemplo de manifest.json com o conector

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

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a>Envie cartões adaptáveis usando um webhook de entrada

> [!NOTE]
>
> ✔ Todos os elementos nativos do esquema de placa adaptável, exceto `Action.Submit`, são totalmente suportados.
>
> ✔ As ações suportadas são [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), and [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).

### <a name="the-flow-for-sending-adaptive-cards-via-an-incoming-webhook-is-as-follows"></a>O fluxo para o envio de [cartões adaptáveis](../../task-modules-and-cards/cards/cards-reference.md#adaptive-card) por meio de um webhook de entrada é o seguinte:

**1.** [Configure um webhook personalizado](#setting-up-a-custom-incoming-webhook) no Teams.</br></br>
**2.** Crie seu arquivo JSON de cartão adaptável:

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
                "text": "For Samples and Templates, see https://adaptivecards.io/samples](https://adaptivecards.io/samples)",
                }
            ]
         }
      }
   ]
}
```

> [!div class="checklist"]
>
> - O campo `"type"` deve ser `"message"`.
> - A matriz `"attachments"` contém um conjunto de objetos de cartão.
> - O campo `"contentType"` deve ser definido para o tipo de cartão adaptável.
> - O objeto `"content"` é o cartão formatado em JSON.

**3.** Teste seu cartão adaptável com o Postman

Você pode testar seu cartão adaptável usando o [Postman](https://www.postman.com) para enviar uma solicitação POST para o URL que você criou ao configurar o webhook de entrada. Cole seu arquivo JSON no corpo da solicitação e visualize sua mensagem de cartão adaptável no Teams.

>[!TIP]
> Você pode usar o código do cartão adaptável [Amostras e Modelos](https://adaptivecards.io/samples) para o corpo do seu teste de solicitação Post.

## <a name="testing-your-connector"></a>Testar o conector

Para testar o Conector, carregue-o em uma equipe, como em qualquer outro aplicativo. Você pode criar um pacote .zip usando o arquivo de manifesto do Painel do Desenvolvedor do Connectors (modificado conforme indicado na seção anterior) e os dois arquivos de ícone.

Depois de carregar o aplicativo, abra a lista de conectores em qualquer canal. Role até a parte inferior para ver o aplicativo na seção **Carregado**.

![Captura de tela da seção carregada na caixa de diálogo do Conector](~/assets/images/connectors/connector_dialog_uploaded.png)

Agora você pode iniciar a experiência de configuração. Lembre-se de que esse fluxo ocorre inteiramente no Microsoft Teams por meio de uma janela pop-up. Atualmente, esse comportamento difere da experiência de configuração nos conectores que criamos; estamos trabalhando para unificar as experiências.

Para verificar se uma ação `HttpPOST` está funcionando corretamente, use o [Webhook de entrada personalizado](#setting-up-a-custom-incoming-webhook).

## <a name="rate-limiting-for-connectors"></a>Limitação de taxa para conectores

Os limites de taxa de aplicativos controlam o tráfego que um conector ou um webhook de entrada tem permissão para gerar em um canal. O Teams acompanha as solicitações por meio de uma janela de taxa fixa e de um contador incremental medido em segundos.  Se houver muitas solicitações, a conexão do cliente será limitada até que a janela seja atualizada, isto é, pela duração da taxa fixa.

### <a name="transactions-per-second-thresholds"></a>**Limites de transações por segundo**

| Tempo (segundos)  | Máximo de solicitações permitidas  |
|---|---|
| 1   | 4  |  
| 30   | 60  |  
| 3600   | 100  |
| 7200 | 150  |
| 86400  | 1800  |

*Confira também* [Conectores do Office 365 — Microsoft Teams](https://docs.microsoft.com/connectors/teams/)

Uma [lógica de repetição com retirada exponencial](/azure/architecture/patterns/retry) como abaixo reduziria a limitação da taxa nos casos em que as solicitações excederem os limites em um segundo. Siga as [práticas recomendadas](../../bots/how-to/rate-limit.md#best-practices) para evitar atingir os limites de taxa.

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
