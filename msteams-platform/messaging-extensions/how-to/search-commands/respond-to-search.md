---
title: Responder ao comando de pesquisa
author: surbhigupta
description: Saiba como responder ao comando de pesquisa de uma extensão de mensagem em um aplicativo Microsoft Teams usando exemplos de código e exemplos
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: f02db887a83965eeaac9e905fd20b34f79b34a68
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111931"
---
# <a name="respond-to-search-command"></a>Responder ao comando de pesquisa

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Depois que o usuário envia o comando de pesquisa, seu serviço Web `composeExtension/query` `value` recebe uma mensagem de invocação que contém um objeto com os parâmetros de pesquisa. Essa invocação é disparada com as seguintes condições:

* À medida que os caracteres são inseridos na caixa de pesquisa.
* `initialRun` é definido como true no manifesto do aplicativo, você recebe a mensagem de invocação assim que o comando de pesquisa é invocado. Para obter mais informações, consulte [a consulta padrão](#default-query).

Este documento orienta você sobre como responder a solicitações de usuário na forma de cartões e visualizações e as condições sob as quais Microsoft Teams emite uma consulta padrão.

Os parâmetros de solicitação são encontrados no `value` objeto na solicitação, que inclui as seguintes propriedades:

| Nome da propriedade | Objetivo |
|---|---|
| `commandId` | O nome do comando invocado pelo usuário, correspondendo a um dos comandos declarados no manifesto do aplicativo. |
| `parameters` | Matriz de parâmetros. Cada objeto de parâmetro contém o nome do parâmetro, juntamente com o valor do parâmetro fornecido pelo usuário. |
| `queryOptions` | Parâmetros de paginação: <br>`skip`: ignorar a contagem para esta consulta <br>`count`: número de elementos a serem retornados. |

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken)
{
  //code to handle the query
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
class TeamsMessagingExtensionsSearch extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionQuery(context, query) {
  //code to handle the query
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

O JSON abaixo é reduzido para realçar as seções mais relevantes.

```json
{
  "type": "invoke",
  "name": "composeExtension/query",
  "value": {
    "commandId": "searchCmd",
    "parameters": [
      {
        "name": "searchKeywords",
        "value": "Toronto"
      }
    ],
    "queryOptions": {
      "skip": 0,
      "count": 25
    }
  },
...
}
```

* * *

## <a name="respond-to-user-requests"></a>Responder às solicitações do usuário

Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona para seu serviço. Nesse ponto, seu código tem segundos `5` para fornecer uma resposta HTTP à solicitação. Durante esse tempo, seu serviço pode executar uma pesquisa adicional ou qualquer outra lógica de negócios necessária para atender à solicitação.

Seu serviço deve responder com os resultados correspondentes à consulta do usuário. A resposta deve indicar um código de status HTTP de `200 OK` um aplicativo ou objeto JSON válido com as seguintes propriedades:

|Nome da propriedade|Objetivo|
|---|---|
|`composeExtension`|Envelope de resposta de nível superior.|
|`composeExtension.type`|Tipo de resposta. Há suporte para os seguintes tipos: <br>`result`: exibe uma lista de resultados da pesquisa <br>`auth`: solicita que o usuário se autentique <br>`config`: solicita que o usuário configure a extensão de mensagem <br>`message`: exibe uma mensagem de texto sem formatação |
|`composeExtension.attachmentLayout`|Especifica o layout dos anexos. Usado para respostas do tipo `result`. <br>Atualmente, há suporte para os seguintes tipos: <br>`list`: uma lista de objetos de cartão que contêm campos de miniatura, título e texto <br>`grid`: uma grade de imagens em miniatura |
|`composeExtension.attachments`|Matriz de objetos de anexo válidos. Usado para respostas do tipo `result`. <br>Atualmente, há suporte para os seguintes tipos: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Ações sugeridas. Usado para respostas de tipo `auth` ou `config`. |
|`composeExtension.text`|Mensagem a ser exibida. Usado para respostas do tipo `message`. |

### <a name="response-card-types-and-previews"></a>Tipos de cartão de resposta e visualizações

Teams dá suporte aos seguintes tipos de cartão:

* [cartão de Miniatura](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [cartão Hero](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [cartão do Conector do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão Adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Para ter uma melhor compreensão e visão geral sobre cartões, veja [o que são cartões](~/task-modules-and-cards/what-are-cards.md).

Para saber como usar os tipos de cartão em miniatura e hero, consulte [adicionar cartões e ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

Para obter informações adicionais sobre o cartão Office 365 Connector, consulte [Usando cartões Office 365 Connector](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

A lista de resultados é exibida na interface Microsoft Teams interface do usuário com uma visualização de cada item. A visualização é gerada de uma das duas maneiras:

* Usando a `preview` propriedade dentro do `attachment` objeto. O `preview` anexo só pode ser um cartão hero ou miniatura.
* Extraindo das propriedades básicas `title``text`e `image` do `attachment` objeto. As propriedades básicas serão usadas somente se `preview` a propriedade não for especificada.

Para cartão Hero ou Miniatura, exceto a ação de invocação, outras ações, como botão e toque, não têm suporte no cartão de visualização.

Para enviar um Cartão Adaptável ou um Office 365 Conector, você deve incluir uma versão prévia. A `preview` propriedade deve ser um cartão Hero ou Thumbnail. Se você não especificar a propriedade de visualização no objeto `attachment` , uma visualização não será gerada.

Para cartões Hero e Thumbnail, você não precisa especificar uma propriedade de visualização, uma visualização é gerada por padrão.

### <a name="response-example"></a>Exemplo de resposta

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken) 
{
  var text = query?.Parameters?[0]?.Value as string ?? string.Empty;

  //searches NuGet for a package
  var obj = JObject.Parse(await (new HttpClient()).GetStringAsync($"https://azuresearch-usnc.nuget.org/query?q=id:{text}&prerelease=true"));
  var packages = obj["data"].Select(item => (item["id"].ToString(), item["version"].ToString(), item["description"].ToString()));

  // We take every row of the results and wrap them in cards wrapped in in MessagingExtensionAttachment objects.
  // The Preview is optional, if it includes a Tap, that will trigger the OnTeamsMessagingExtensionSelectItemAsync event back on this bot.
  var attachments = packages.Select(package => new MessagingExtensionAttachment
      {
          ContentType = HeroCard.ContentType,
          Content = new HeroCard { Title = package.Item1 },
          Preview = new HeroCard { Title = package.Item1, Tap = new CardAction { Type = "invoke", Value = package } }.ToAttachment()
      })
      .ToList();

  // The list of MessagingExtensionAttachments must we wrapped in a MessagingExtensionResult wrapped in a MessagingExtensionResponse.
  return new MessagingExtensionResponse
  {
      ComposeExtension = new MessagingExtensionResult
      {
          Type = "result",
          AttachmentLayout = "list",
          Attachments = attachments
      }
  };
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
class TeamsMessagingExtensionsSearchBot extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionQuery(context, query) {
        const searchQuery = query.parameters[0].value;
        const response = await axios.get(`http://registry.npmjs.com/-/v1/search?${ querystring.stringify({ text: searchQuery, size: 8 }) }`);

        const attachments = [];
        response.data.objects.forEach(obj => {
            const heroCard = CardFactory.heroCard(obj.package.name);
            const preview = CardFactory.heroCard(obj.package.name);
            const attachment = { ...heroCard, preview };
            attachments.push(attachment);
        });

        return {
            composeExtension: {
                type: 'result',
                attachmentLayout: 'list',
                attachments: attachments
            }
        };
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "composeExtension": {
    "type": "result",
    "attachmentLayout": "list",
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
        },
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
        }
      },
      {
        "contentType": "application/vnd.microsoft.card.adaptive",
        "content": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Container",
              "items": [
                {
                  "type": "TextBlock",
                  "text": "Microsoft Corp (NASDAQ: MSFT)",
                  "size": "medium",
                  "isSubtle": true
                },
                {
                  "type": "TextBlock",
                  "text": "September 19, 4:00 PM EST",
                  "isSubtle": true
                }
              ]
            },
            {
              "type": "Container",
              "spacing": "none",
              "items": [
                {
                  "type": "ColumnSet",
                  "columns": [
                    {
                      "type": "Column",
                      "width": "stretch",
                      "items": [
                        {
                          "type": "TextBlock",
                          "text": "75.30",
                          "size": "extraLarge"
                        },
                        {
                          "type": "TextBlock",
                          "text": "▼ 0.20 (0.32%)",
                          "size": "small",
                          "color": "attention",
                          "spacing": "none"
                        }
                      ]
                    },
                    {
                      "type": "Column",
                      "width": "auto",
                      "items": [
                        {
                          "type": "FactSet",
                          "facts": [
                            {
                              "title": "Open",
                              "value": "62.24"
                            },
                            {
                              "title": "High",
                              "value": "62.98"
                            },
                            {
                              "title": "Low",
                              "value": "62.20"
                            }
                          ]
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          ],
          "version": "1.0"
        },
        "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "Microsoft Corp (NASDAQ: MSFT)",
            "text": "75.30 ▼ 0.20 (0.32%)"
          }
        }
      }
    ]
  }
}
```

* * *

### <a name="enable-and-handle-tap-actions"></a>Habilitar e manipular ações de toque

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override Task<MessagingExtensionResponse> OnTeamsMessagingExtensionSelectItemAsync(ITurnContext<IInvokeActivity> turnContext, JObject query, CancellationToken cancellationToken)
{
    // The Preview card's Tap should have a Value property assigned, this will be returned to the bot in this event. 
    var (packageId, version, description, projectUrl, iconUrl) = query.ToObject<(string, string, string, string, string)>();

    var card = new ThumbnailCard
    {
        Title = "Card Select Item",
        Subtitle = description
    };

    var attachment = new MessagingExtensionAttachment
    {
        ContentType = ThumbnailCard.ContentType,
        Content = card,
    };

    return Task.FromResult(new MessagingExtensionResponse
    {
        ComposeExtension = new MessagingExtensionResult
        {
            Type = "result",
            AttachmentLayout = "list",
            Attachments = new List<MessagingExtensionAttachment> { attachment }
        }
    });
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
async handleTeamsMessagingExtensionSelectItem(context, obj) {
        return {
            composeExtension: {
                  type: 'result',
                  attachmentLayout: 'list',
                  attachments: [CardFactory.thumbnailCard(obj.Item3)]
            }
        };
    } 
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
    "name": "composeExtension/selectItem",
    "type": "invoke",
    "value": {
        "Item1": "Package_Name",
        "Item2": "Version",
        "Item3": "Package Description"
    },
    .
    .
    .
}
```

* * *

> [!NOTE]
> `OnTeamsMessagingExtensionSelectItemAsync` não é disparado no aplicativo de equipes móveis.

## <a name="default-query"></a>Consulta padrão

Se você definir `initialRun` como `true` no manifesto, Microsoft Teams emite uma consulta padrão quando  o usuário abre a extensão da mensagem pela primeira vez. Seu serviço pode responder a essa consulta com um conjunto de resultados preenchidos previamente. Isso é útil quando o comando de pesquisa requer autenticação ou configuração, exibindo itens exibidos recentemente, favoritos ou qualquer outra informação que não dependa da entrada do usuário.

A consulta padrão tem a mesma estrutura que qualquer consulta de usuário regular, `name` `initialRun` `value` `true` com o campo definido como e definido como conforme mostrado no seguinte objeto:

```json
{
  "type": "invoke",
  "name": "composeExtension/query",
  "value": {
    "commandId": "searchCmd",
    "parameters": [
      {
        "name": "initialRun",
        "value": "true"
      }
    ],
    "queryOptions": {
      "skip": 0,
      "count": 25
    }
  },
  ⋮
}
```

## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo           | Descrição | .NET    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Teams de extensão de mensagem| Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) |
|Teams de extensão de mensagem   |  Descreve como definir comandos de pesquisa e responder a pesquisas.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Adicionar autenticação a uma extensão de mensagem](~/messaging-extensions/how-to/add-authentication.md)

## <a name="see-also"></a>Confira também

[Adicionar configuração a uma extensão de mensagem](~/get-started/first-message-extension.md)
