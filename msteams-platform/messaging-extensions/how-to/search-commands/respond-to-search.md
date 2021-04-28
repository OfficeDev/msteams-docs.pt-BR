---
title: Responder ao comando de pesquisa
author: clearab
description: Como responder ao comando de pesquisa de uma extensão de mensagens em um aplicativo do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 044c6eebe9489ed404c9fa89b29c306cde8c7363
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058583"
---
# <a name="respond-to-search-command"></a>Responder ao comando de pesquisa

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Depois que o usuário envia o comando de pesquisa, seu serviço Web recebe uma mensagem de invocação que contém um `composeExtension/query` `value` objeto com os parâmetros de pesquisa. Essa invocação é disparada com as seguintes condições:

* À medida que os caracteres são inseridos na caixa de pesquisa.
* `initialRun` é definido como true no manifesto do aplicativo, você recebe a mensagem de invocação assim que o comando de pesquisa é invocado. Para obter mais informações, consulte [consulta padrão](#default-query).

Este documento orienta você sobre como responder a solicitações de usuário na forma de cartões e visualizações e as condições em que o Microsoft Teams emite uma consulta padrão.

Os parâmetros de solicitação são encontrados no objeto na `value` solicitação, que inclui as seguintes propriedades:

| Nome da propriedade | Objetivo |
|---|---|
| `commandId` | O nome do comando invocado pelo usuário, correspondendo a um dos comandos declarados no manifesto do aplicativo. |
| `parameters` | Matriz de parâmetros. Cada objeto de parâmetro contém o nome do parâmetro, juntamente com o valor do parâmetro fornecido pelo usuário. |
| `queryOptions` | Parâmetros paginação: <br>`skip`: Ignorar contagem para essa consulta <br>`count`: Número de elementos a retornar. |

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

## <a name="respond-to-user-requests"></a>Responder a solicitações de usuário

Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona ao seu serviço. Nesse ponto, seu código tem `5` segundos para fornecer uma resposta HTTP à solicitação. Durante esse tempo, seu serviço pode realizar uma consulta adicional ou qualquer outra lógica de negócios necessária para atender à solicitação.

Seu serviço deve responder com os resultados correspondentes à consulta do usuário. A resposta deve indicar um código de status HTTP e `200 OK` um aplicativo ou objeto JSON válido com as seguintes propriedades:

|Nome da propriedade|Objetivo|
|---|---|
|`composeExtension`|Envelope de resposta de nível superior.|
|`composeExtension.type`|Tipo de resposta. Os seguintes tipos são suportados: <br>`result`: Exibe uma lista de resultados da pesquisa <br>`auth`: Pede ao usuário para autenticar <br>`config`: Pede ao usuário para configurar a extensão de mensagens <br>`message`: Exibe uma mensagem de texto sem texto |
|`composeExtension.attachmentLayout`|Especifica o layout dos anexos. Usado para respostas do tipo `result` . <br>Atualmente, os seguintes tipos são suportados: <br>`list`: Uma lista de objetos de cartão que contêm campos de miniatura, título e texto <br>`grid`: uma grade de imagens em miniatura |
|`composeExtension.attachments`|Matriz de objetos de anexo válidos. Usado para respostas do tipo `result` . <br>Atualmente, os seguintes tipos são suportados: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Ações sugeridas. Usado para respostas de tipo `auth` ou `config` . |
|`composeExtension.text`|Mensagem a ser exibida. Usado para respostas do tipo `message` . |

### <a name="response-card-types-and-previews"></a>Tipos de cartão de resposta e visualizações

O Teams dá suporte aos seguintes tipos de cartão:

* [Cartão de miniatura](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Cartão de herói](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Cartão do Conector do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão Adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Para ter uma melhor compreensão e visão geral sobre cartões, consulte [o que são cartões](~/task-modules-and-cards/what-are-cards.md).

Para saber como usar os tipos de miniatura e cartão de herói, consulte [adicionar cartões e ações de cartão.](~/task-modules-and-cards/cards/cards-actions.md)

Para obter informações adicionais sobre o cartão conector do Office 365, consulte [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

A lista de resultados é exibida na interface do usuário do Microsoft Teams com uma visualização de cada item. A visualização é gerada de uma das duas maneiras:

* Usando a `preview` propriedade dentro do `attachment` objeto. O `preview` anexo só pode ser um cartão Hero ou Thumbnail.
* Extraído das propriedades `title` básicas `text` , e do `image` anexo. Eles são usados somente se `preview` a propriedade não estiver definida e essas propriedades estarão disponíveis.
* O botão cartão Hero ou Thumbnail e as ações de toque, exceto invocar, não são suportadas no cartão de visualização.

Você pode exibir uma visualização de um cartão adaptável ou cartão conector do Office 365 na lista de resultados usando sua propriedade de visualização. A propriedade preview não será necessária se os resultados já são cartões Hero ou Thumbnail. Se você usar o anexo de visualização, ele deve ser um cartão Hero ou Thumbnail. Se nenhuma propriedade preview for especificada, a visualização do cartão falhará e nada será exibido.

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

## <a name="default-query"></a>Consulta padrão

Se você definir como no manifesto, o Microsoft Teams emite uma consulta padrão quando o usuário abre pela primeira vez a extensão `initialRun` `true` de mensagens.  Seu serviço pode responder a essa consulta com um conjunto de resultados pré-preenchidos. Isso é útil quando o comando de pesquisa exige autenticação ou configuração, exibindo itens, favoritos ou qualquer outra informação que não dependa da entrada do usuário.

A consulta padrão tem a mesma estrutura que qualquer consulta de usuário regular, com o campo definido como e definido como mostrado `name` `initialRun` no seguinte `value` `true` objeto:

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

| Exemplo de nome           | Descrição | .NET    | Node.js   |   
|:---------------------|:--------------|:---------|:--------|
|Ação de extensão de mensagens do Teams| Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Pesquisa de extensão de mensagens do Teams   |  Descreve como definir comandos de pesquisa e responder a pesquisas.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="see-also"></a>Confira também

- [Adicionar configuração a uma extensão de mensagens](~/messaging-extensions/how-to/add-configuration-page.md)
 
## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Adicionar autenticação a uma extensão de mensagens](~/messaging-extensions/how-to/add-authentication.md)



