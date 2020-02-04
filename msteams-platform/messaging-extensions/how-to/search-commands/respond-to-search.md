---
title: Responder ao comando de pesquisa
author: clearab
description: Como responder ao comando de pesquisa de uma extensão de mensagens em um aplicativo do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: e8b40dd8f422ffbd2537e8fa76a38c15eb6208de
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672949"
---
# <a name="respond-to-the-search-command"></a>Responder ao comando de pesquisa

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Seu serviço Web receberá uma `composeExtension/query` mensagem de invocação que `value` contém um objeto com os parâmetros de pesquisa. Essa invocação é disparada:

* À medida que os caracteres são inseridos na caixa de pesquisa.
* Se `initialRun` for definido como true no manifesto do aplicativo, você receberá a mensagem de invocação assim que o comando de pesquisa for chamado. Consulte [consulta padrão](#default-query).

Os próprios parâmetros de solicitação são encontrados no `value` objeto na solicitação, que inclui as seguintes propriedades:

| Nome da propriedade | Finalidade |
|---|---|
| `commandId` | O nome do comando invocado pelo usuário, correspondendo a um dos comandos declarados no manifesto do aplicativo. |
| `parameters` | Matriz de parâmetros. Cada objeto Parameter contém o nome do parâmetro, juntamente com o valor do parâmetro fornecido pelo usuário. |
| `queryOptions` | Parâmetros de paginação: <br>`skip`: ignorar contagem para esta consulta <br>`count`: número de elementos a serem retornados |

# <a name="cnettabdotnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken)
{
  //code to handle the query
}
```

# <a name="typescriptnodejstabtypescript"></a>[TypeScript/node. js](#tab/typescript)

```typescript
class TeamsMessagingExtensionsSearch extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionQuery(context, query) {
  //code to handle the query
    }
}
```

# <a name="jsontabjson"></a>[JSON](#tab/json)

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

Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona para o serviço. Nesse ponto, o código tem cinco segundos para fornecer uma resposta HTTP para a solicitação. Durante esse tempo, o serviço pode executar pesquisa adicional ou qualquer outra lógica de negócios necessária para atender à solicitação.

Seu serviço deve responder com os resultados que correspondem à consulta do usuário. A resposta deve indicar um código de `200 OK` status HTTP e um objeto Application/JSON válido com o seguinte corpo:

|Nome da propriedade|Finalidade|
|---|---|
|`composeExtension`|Envelope de resposta de nível superior.|
|`composeExtension.type`|Tipo de resposta. Há suporte para os seguintes tipos: <br>`result`: exibe uma lista de resultados de pesquisa <br>`auth`: solicita que o usuário autentique <br>`config`: solicita que o usuário configure a extensão de mensagens <br>`message`: exibe uma mensagem de texto sem formatação |
|`composeExtension.attachmentLayout`|Especifica o layout dos anexos. Usado para respostas do tipo `result`. <br>Atualmente, há suporte para os seguintes tipos: <br>`list`: uma lista de objetos Card contendo campos de miniatura, título e texto <br>`grid`: uma grade de imagens em miniatura |
|`composeExtension.attachments`|Matriz de objetos Attachment válidos. Usado para respostas do tipo `result`. <br>Atualmente, há suporte para os seguintes tipos: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Ações sugeridas. Usado para respostas do tipo `auth` ou `config`. |
|`composeExtension.text`|Mensagem a ser exibida. Usado para respostas do tipo `message`. |

### <a name="response-card-types-and-previews"></a>Tipos e visualizações de cartões de resposta

Oferecemos suporte para os seguintes tipos de anexo:

* [Cartão de miniaturas](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Cartão herói](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Cartão de conexão do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Confira [o que são cartões](~/task-modules-and-cards/what-are-cards.md) para uma visão geral.

Para saber como usar os tipos de cartão de miniatura e herói, confira [Adicionar cartões e ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

Para obter documentação adicional sobre a placa de conector do Office 365, consulte [usando cartões de conector do office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

A lista de resultados é exibida na interface do usuário do Microsoft Teams com uma visualização de cada item. A visualização é gerada de duas maneiras:

* Usando a `preview` Propriedade dentro do `attachment` objeto. O `preview` anexo só pode ser um herói ou cartão de miniatura.
* Extraído do básico `title`, `text`e `image` das propriedades do anexo. Eles são usados apenas se a `preview` propriedade não estiver definida e essas propriedades estiverem disponíveis.

Você pode exibir uma visualização de um cartão adaptável ou cartão de conexão com o Office 365 na lista de resultados, simplesmente pela propriedade Preview. Isso não é necessário se os resultados já são herói ou cartões em miniatura. Se você usar o anexo de visualização, ele deve ser um herói ou cartão de miniatura. Se nenhuma propriedade Preview for especificada, a visualização do cartão falhará e nada será exibido.

### <a name="response-example"></a>Exemplo de resposta

# <a name="cnettabdotnet"></a>[C#/.NET](#tab/dotnet)

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

# <a name="typescriptnodejstabtypescript"></a>[TypeScript/node. js](#tab/typescript)

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

# <a name="jsontabjson"></a>[JSON](#tab/json)

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
              "activityImage": "https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value": "[Larry Brown](mailto:larryb@example.com)"
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

Se você definir `initialRun` para `true` no manifesto, o Microsoft Teams emitirá uma consulta "padrão" quando o usuário abrir pela primeira vez a extensão de mensagens. O serviço pode responder a essa consulta com um conjunto de resultados previamente preenchidos. Isso pode ser útil quando o comando de pesquisa requer autenticação ou configuração, exibindo itens exibidos recentemente, favoritos ou qualquer outra informação que não seja dependente da entrada do usuário.

A consulta padrão tem a mesma estrutura que qualquer consulta de usuário regular, com `name` o campo definido `initialRun` como `value` e definido `true` como no objeto abaixo.

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

## <a name="next-steps"></a>Próximos passos

Adicionar autenticação e/ou configuração

* [Adicionar autenticação a uma extensão de mensagens](~/messaging-extensions/how-to/add-authentication.md)
* [Adicionar configuração a uma extensão de mensagens](~/messaging-extensions/how-to/add-configuration-page.md)

Implantar configuração

* [Implantar seu pacote de aplicativos](~/concepts/deploy-and-publish/apps-upload.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
