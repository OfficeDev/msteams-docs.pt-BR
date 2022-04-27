---
title: Pesquisa de preenchimento automático em cartões adaptáveis
author: Rajeshwari-v
description: Descreve a pesquisa typeahead com o controle Input.ChoiceSet em Cartões Adaptáveis
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: surbhigupta
ms.openlocfilehash: d33fce44cbf1ff550d9aa21686111746318bb17e
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073786"
---
# <a name="typeahead-search-in-adaptive-cards"></a>Pesquisa de preenchimento automático em cartões adaptáveis

A funcionalidade de pesquisa typeahead em Cartões Adaptáveis oferece uma experiência de pesquisa aprimorada no `input.choiceset` componente. Ele fornece uma lista de opções para inserir texto no campo de pesquisa. Você pode incorporar a pesquisa typeahead com Cartões Adaptáveis para pesquisar e selecionar dados.

Você pode usar a pesquisa typeahead para as seguintes pesquisas:

* [Pesquisa estática](#static-typeahead-search)
* [Pesquisa dinâmica](#dynamic-typeahead-search)

## <a name="static-typeahead-search"></a>Pesquisa de typeahead estático

A pesquisa de typeahead estático permite que os usuários pesquisem de valores especificados `input.choiceset` no conteúdo do Cartão Adaptável. A pesquisa de typeahead estático pode ser usada para mostrar várias opções para o usuário. O tamanho da carga na pesquisa estática aumenta com o número de opções especificadas na carga.
À medida que o usuário começa a inserir os textos, as opções são filtradas, que correspondem parcialmente à entrada. A lista suspensa realça os caracteres de entrada que correspondem à pesquisa.

A imagem a seguir demonstra a pesquisa de typeahead estático:

![Pesquisa de typeahead estático](~/assets/images/Cards/static-typeahead-search.gif)

## <a name="dynamic-typeahead-search"></a>Pesquisa de typeahead dinâmico

A pesquisa de typeahead dinâmico é útil para pesquisar e selecionar dados de grandes conjuntos de dados. Os conjuntos de dados são carregados dinamicamente do conjunto de dados especificado no conteúdo do cartão. A funcionalidade de tipo antecipado ajuda a filtrar as opções conforme o usuário digita.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/Cards/dynamic-typeahead-search-desktop.png" alt-text="Pesquisa de typeahead dinâmico":::

:::image type="content" source="../../assets/images/Cards/dynamic-typeahead-search-desktop-2.png" alt-text="Pesquisa de typeahead dinâmico 2":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

Os clientes móveis Android e iOS dão suporte à pesquisa de typeahead em Cartões Adaptáveis.

**Cenário**

João é um funcionário da loja que trabalha em uma loja de varejo do Xbox. A loja usa um bot para aceitar novas solicitações de compra dos clientes. Um cliente pode pesquisar de milhares de jogos disponíveis. A pesquisa de cabeça de tipo em Cartões Adaptáveis é usada para pesquisar e selecionar as opções dos clientes.

**Para usar a pesquisa typeahead em Cartões Adaptáveis**

1. O usuário A abre o bot da loja.
1. O usuário A envia um comando para o bot para uma **nova solicitação de cliente**. O bot responde com o Cartão Adaptável que tem componente `Input.ChoiceSet` .
1. O usuário A usa a pesquisa typeahead para pesquisar e selecionar as informações com base na escolha do cliente.

A imagem a seguir ilustra a experiência móvel da pesquisa typeahead:

![Pesquisa de typeahead estático](~/assets/images/Cards/static-typeahead-search.gif)

---

> [!NOTE]
> Você não pode obter experiências avançadas de cartão com pesquisa dinâmica, como extensões de mensagens baseadas em consulta.

## <a name="implement-typeahead-search"></a>Implementar a pesquisa typeahead

`Input.ChoiceSet` é um dos componentes de entrada importantes nos Cartões Adaptáveis. Você pode adicionar um controle de pesquisa typeahead ao componente `Input.ChoiceSet` para implementar a pesquisa typeahead. Você pode pesquisar e selecionar as informações necessárias com as seguintes seleções:

* Lista suspensa, como seleção expandida.
* Botão de opção, como seleção única.
* Caixas de seleção, como várias seleções.

> [!NOTE]
> O `Input.ChoiceSet` controle é baseado no estilo e nas `isMultiSelect` propriedades.

### <a name="schema-properties"></a>Propriedades do esquema

As propriedades a seguir são as novas adições ao esquema [`Input.ChoiceSet`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) para habilitar a pesquisa typeahead:

| Propriedade| Tipo | Obrigatório | Descrição |
|-----------|------|----------|-------------|
| style | Compact <br/> Expandido <br/> Filtered | Não | Adiciona estilo filtrado à lista de validações com suporte para o tipo estático antecipado.|
| choices.data | Data.Query | Não | Habilita o tipo dinâmico à medida que o usuário digita, buscando um conjunto remoto de opções de um back-end. |

### <a name="dataquery-definition"></a>Definição de Data.Query

| Propriedade| Tipo | Obrigatório | Descrição |
|-----------|------|----------|-------------|
| type | Data.Query | Sim | Especifica que é um objeto Data.Query.|
| Dataset | String | Sim | Especifica o tipo de dados que é buscado dinamicamente. |
| value | String | Não | Popula a solicitação de invocação para o bot com a entrada que o usuário forneceu ao `ChoiceSet`. |
| count | Número | Não | Popula a solicitação de invocação para o bot para especificar o número de elementos que devem ser retornados. O bot o ignorará se os usuários desejarem enviar um valor diferente. |
| skip | Número | Não | Popula a solicitação de invocação para o bot para indicar que os usuários querem paginar e avançar na lista. |

### <a name="example"></a>Exemplo

O conteúdo de exemplo que contém a pesquisa de typeahead estático e dinâmico com & opções de seleção única da seguinte maneira:

```json
{
  "type": "AdaptiveCard",
  "body": [
    {
      "columns": [
        {
          "width": "1",
          "items": [
            {
              "size": null,
              "url": "https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fi.imgur.com%2fhdOYxT8.png",
              "height": "auto",
              "type": "Image"
            }
          ],
          "type": "Column"
        },
        {
          "width": "2",
          "items": [
            {
              "size": "extraLarge",
              "text": "Game Purchase",
              "weight": "bolder",
              "wrap": true,
              "type": "TextBlock"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "text": "Please fill out the below form to send a game purchase request.",
      "wrap": true,
      "type": "TextBlock"
    },
    {
      "columns": [
        {
          "width": "auto",
          "items": [
            {
              "text": "Game: ",
              "wrap": true,
              "height": "stretch",
              "type": "TextBlock"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "columns": [
        {
          "width": "stretch",
          "items": [
            {
              "choices": [
                {
                  "title": "Call of Duty",
                  "value": "call_of_duty"
                },
                {
                  "title": "Death's Door",
                  "value": "deaths_door"
                },
                {
                  "title": "Grand Theft Auto V",
                  "value": "grand_theft"
                },
                {
                  "title": "Minecraft",
                  "value": "minecraft"
                }
              ],
              "style": "filtered",
              "placeholder": "Search for a game",
              "id": "choiceGameSingle",
              "type": "Input.ChoiceSet"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "columns": [
        {
          "width": "auto",
          "items": [
            {
              "text": "Multi-Game: ",
              "wrap": true,
              "height": "stretch",
              "type": "TextBlock"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "columns": [
        {
          "width": "stretch",
          "items": [
            {
              "choices": [
                {
                  "title": "Static Option 1",
                  "value": "static_option_1"
                },
                {
                  "title": "Static Option 2",
                  "value": "static_option_2"
                },
                {
                  "title": "Static Option 3",
                  "value": "static_option_3"
                }
              ],
              "isMultiSelect": true,
              "style": "filtered",
              "choices.data": {
                "type": "Data.Query",
                "dataset": "xbox"
              },
              "id": "choiceGameMulti",
              "type": "Input.ChoiceSet"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "columns": [
        {
          "width": "auto",
          "items": [
            {
              "text": "Needed by: ",
              "wrap": true,
              "height": "stretch",
              "type": "TextBlock"
            }
          ],
          "type": "Column"
        },
        {
          "width": "stretch",
          "items": [
            {
              "id": "choiceDate",
              "type": "Input.Date"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "text": "Buy and download digital games and content directly from your Xbox console, Windows 10 PC, or at Xbox.com.",
      "wrap": true,
      "type": "TextBlock"
    },
    {
      "text": "Earn points for what you already do on Xbox, then redeem your points on real rewards. Play more, get rewarded. Start earning today.",
      "wrap": true,
      "type": "TextBlock"
    }
  ],
  "actions": [
    {
      "data": {
        "msteams": {
          "type": "invoke",
          "value": {
            "type": "task/submit"
          }
        }
      },
      "title": "Request Purchase",
      "type": "Action.Submit"
    }
  ],
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "version": "1.2"
}
```

## <a name="code-snippets-for-invoke-request-and-response"></a>Snippets de código para invocar solicitação e resposta

### <a name="invoke-request"></a>Invocar Solicitação

```json
{
    "name": "application/search",
    "type": "invoke",
    "value": {
        "queryText": "fluentui",
        "queryOptions": {
            "skip": 0,
            "top": 15
        },
        "dataset": "npm"
    },
    "locale": "en-US",
    "localTimezone": "America/Los_Angeles",
    // …. other fields
}
```

### <a name="response"></a>Resposta

#### <a name="c"></a>[C#](#tab/csharp)

```csharp
protected override async Task<InvokeResponse> OnInvokeActivityAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
{
    if (turnContext.Activity.Name == "application/search")
    {
 var packages = new[] {
   new { title = "A very extensive set of extension methods", value = "FluentAssertions" },
   new { title = "Fluent UI Library", value = "FluentUI" }};

 var searchResponseData = new
 {
     type = "application/vnd.microsoft.search.searchResponse",
     value = new
     {
  results = packages
     }
 };
 var jsonString = JsonConvert.SerializeObject(searchResponseData);
 JObject jsonData = JObject.Parse(jsonString);
 return new InvokeResponse()
 {
     Status = 200,
     Body = jsonData
 };
    }

    return null;
}
```

#### <a name="nodejs"></a>[Node.js](#tab/nodejs)

```nodejs
  async onInvokeActivity(context) {
    if (context._activity.name == 'application/search') {
      // let searchQuery = context._activity.value.queryText;  // This can be used to filter the results
      var successResult = {
        status: 200,
        body: {
          "type": "application/vnd.microsoft.search.searchResponse",
          "value": {
            "results": [
              {
                "value": "FluentAssertions",
                "title": "A very extensive set of extension methods"
              },
              {
                "value": "FluentUI",
                "title": "Fluent UI Library"
              }
            ]
          }
        }
      }

      return successResult;

    }
  }
```

#### <a name="json"></a>[JSON](#tab/json)

```json
{
    "status": 200,
    "body" : {
        "type": "application/vnd.microsoft.search.searchResponse",
        "value": {
           "results": [
                {
                    "value": "FluentAssertions",
                    "title": "A very extensive set of extension methods."
                },
                {
                    "value": "FluentUI",
                    "title": "Fluent UI Library"
                }
            ]
        }
    }
}
```

---

## <a name="code-sample"></a>Exemplo de código

|**Nome de exemplo** | **Descrição** | **C#** | **Node.js** |
|----------------|-----------------|--------------|----------------|
| Controle de pesquisa typeahead em Cartões Adaptáveis | O exemplo mostra os recursos do controle de pesquisa typeahead estático e dinâmico em Cartões Adaptáveis. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-type-ahead-search-adaptive-cards/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-type-ahead-search-adaptive-cards/nodejs) |

## <a name="see-also"></a>Confira também

* [Ações Universais para Cartões Adaptáveis](Universal-actions-for-adaptive-cards/Overview.md)
* [Módulos de tarefas](../what-are-task-modules.md)
