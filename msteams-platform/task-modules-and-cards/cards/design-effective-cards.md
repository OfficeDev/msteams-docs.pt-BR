---
title: Projetando Cartões Adaptáveis para seu aplicativo
description: Aprenda a projetar Cartões Adaptáveis para o Teams e obtenha o Kit de IU do Microsoft Teams.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 6d908c47585c44718e25ec92dc8e06bff0ef5c9e
ms.sourcegitcommit: 830fdc80556a5fde642850dd6b4d1b7efda3609d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63398621"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a>Projetando Cartões Adaptáveis para seu aplicativo Microsoft Teams

Um Cartão Adaptável contém um corpo de elementos de cartão de forma livre e um conjunto opcional de ações. Cartões Adaptáveis são fragmentos de conteúdo acionáveis que você pode adicionar a uma conversa por meio de um bot ou extensão de mensagem. Usando texto, gráficos e botões, esses cartões fornecem uma comunicação rica para seu público-alvo.

A estrutura de Cartão Adaptável é usada em muitos produtos da Microsoft, incluindo o Teams. Você pode enviar cartões dentro de mensagens para usuários por meio de bots ou extensões de mensagens. Os usuários também podem realizar ações em cartões quando presentes.

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Exemplo de visão geral de um Cartão Adaptável." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Kit de IU do Microsoft Teams

Você pode encontrar diretrizes de design mais abrangentes para Cartões Adaptáveis no Teams, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit de IU do Microsoft Teams. O kit de IU também cobre tópicos essenciais, como temas, acessibilidade e dimensionamento dinâmico.

> [!div class="nextstepaction"]
> [Obtenha o Kit de IU do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a>Designer de cartões adaptáveis

Você também pode começar a projetar seus Cartões Adaptáveis diretamente no navegador.

> [!div class="nextstepaction"]
> [Experimente o designer de cartões adaptáveis ](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a>Tipos de Cartões Adaptáveis

### <a name="hero"></a>Destaque

Nosso maior cartão. Uso para compartilhar artigos ou cenários onde uma imagem conta a maior parte da história.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-hero-card.png" alt-text="O exemplo mostra um cartão promocional personalizado do Cartão Adaptável no dispositivo móvel." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="O exemplo mostra um cartão promocional personalizado do Cartão Adaptável." border="false":::

### <a name="thumbnail"></a>Miniatura

Use para enviar uma mensagem acionável simples.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-thumbnail-card.png" alt-text="O exemplo mostra um cartão miniatura do Cartão Adaptável no dispositivo móvel." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="O exemplo mostra um cartão miniatura do Cartão Adaptável." border="false":::

### <a name="list"></a>List

Use em cenários em que você deseja que o usuário escolha um item de uma lista, mas os itens não precisam de muitas explicações.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-list-card.png" alt-text="O exemplo mostra um cartão de uma lista do Cartão Adaptável no dispositivo móvel." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="O exemplo mostra um cartão de uma lista do Cartão Adaptável." border="false":::

### <a name="digest"></a>Compilação

Use para resumos de notícias e postagens de referência. Observação: recomendamos o cartão miniatura para uma atualização ou item de notícias isolados.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-digest-card.png" alt-text="O exemplo mostra um cartão de compilação do Cartão Adaptável no dispositivo móvel" border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="O exemplo mostra um cartão de compilação do Cartão Adaptável." border="false":::

### <a name="media"></a>Mídia

Use quando quiser combinar texto e mídia, como áudio ou vídeo.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-media-card.png" alt-text="O exemplo mostra um cartão de mídia do Cartão Adaptável no dispositivo móvel." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="O exemplo mostra um cartão de mídia do Cartão Adaptável." border="false":::

### <a name="people"></a>Pessoas

Melhor usado para transmitir com eficiência quem está envolvido em uma tarefa.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-people-card.png" alt-text="O exemplo mostra um cartão de pessoas do Cartão Adaptável no dispositivo móvel." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="O exemplo mostra um cartão de pessoas do Cartão Adaptável." border="false":::

### <a name="request-ticket"></a>Solicitar ingresso

Use para obter entradas rápidas de um usuário para criar automaticamente uma tarefa ou tíquete.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-request-ticket-card.png" alt-text="O exemplo mostra um cartão de tíquete de solicitação do Cartão Adaptável no dispositivo móvel." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="O exemplo mostra um cartão de tíquete de solicitação do Cartão Adaptável." border="false":::

### <a name="imageset"></a>ImageSet

Use para enviar várias miniaturas de imagens.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-image-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de imagens do Cartão Adaptável no dispositivo móvel." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de imagens do Cartão Adaptável." border="false":::

### <a name="actionset"></a>ActionSet

Use quando quiser que o usuário selecione um botão e, em seguida, reúna a entrada adicional do usuário do mesmo cartão.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-action-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de ações do Cartão Adaptável no dispositivo móvel." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de ações do Cartão Adaptável." border="false":::

### <a name="choiceset"></a>ChoiceSet

Use para reunir várias entradas do usuário.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-choice-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de opções do Cartão Adaptável no dispositivo móvel." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de opções do Cartão Adaptável." border="false":::

## <a name="anatomy"></a>Anatomia

Os Cartões Adaptáveis têm muita flexibilidade. Mas, no mínimo, sugerimos fortemente incluir os seguintes componentes em cada cartão.

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/adaptive-cards/mobile-anatomy.png" alt-text="O exemplo mostra a anatomia do Cartão Adaptável no dispositivo móvel." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Cabeçalho**: Deixe seus cabeçalhos claros e concisos.|
|B|**Cópia do corpo**: Transmita detalhes que sejam muito longos ou não são importantes o suficiente para incluir no cabeçalho.|
|C|**Ações primárias**: Como prática recomendada, inclua 13 ações principais. Você pode ter até seis.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="O exemplo mostra a anatomia do Cartão Adaptável." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Cabeçalho**: Deixe seus cabeçalhos claros e concisos.|
|B|**Cópia do corpo**: Transmita detalhes que sejam muito longos ou não são importantes o suficiente para incluir no cabeçalho.|
|C|**Ações primárias**: Como prática recomendada, inclua 13 ações principais. Você pode ter até seis.|

## <a name="best-practices"></a>Práticas recomendadas

Cartões projetados para uma escala de tela estreita bem em telas mais amplas (o oposto não é verdadeiro). Você também deve supor que os usuários não exibirão apenas seus cartões na área de trabalho.

### <a name="column-layouts"></a>Layouts de coluna

Use [`ColumnSet`](https://adaptivecards.io/explorer/ColumnSet.html) para formatar o conteúdo do cartão em uma tabela ou grade. Existem várias opções para formatar a largura da coluna. Essas diretrizes o ajudam a entender quando usar cada uma delas.

* `"width": "auto"`: Tamanhos de cada coluna no `ColumnSet` para se ajustar a qualquer conteúdo de aplicativo que você incluir nessa coluna.
  * **Faça**: Use quando você tiver conteúdo de largura variável e não precisar priorizar uma coluna específica.
  * **Faça**: Para cada `TextBlock`, definido `"wrap": true` já que o texto não se quebra por padrão.
  * **Não faça**: Defina `"width": "auto"` para cada contêiner de coluna. Por exemplo, se você tiver uma entrada e um botão lado a lado, o botão poderá ser cortado em algumas telas. Em vez disso, defina `auto` para a coluna com botões e outros conteúdos que sempre devem estar completamente visíveis.
* `"width": "stretch"`: Tamanhos de colunas com base na largura `ColumnSet` disponível. Quando várias colunas usam o valor `"stretch"`, elas compartilham igualmente a largura disponível.
  * **Faça**: Use com uma coluna se todas as outras colunas tiverem uma largura estática. Por exemplo, você tem imagens em miniatura em uma coluna com todos os 50 pixels de largura.
* `"width": "<number>"`: dimensiona colunas usando uma proporção da largura `ColumnSet` disponível. Por exemplo, se você definir três colunas com `"width": "1"`, `"width": "4"` e `"width": "5"`, as colunas assumirão 10, 40 e 50% da largura disponível.
* `"width": "<number>px"`: Tamanhos de colunas para uma largura de pixel específica. Essa abordagem é útil ao criar tabelas.
  * **Faça**: Use quando a largura do que você está exibindo não precisa alterar (por exemplo, números e porcentagens).
  * **Não faça**: Exceda acidentalmente a largura do que o cartão pode exibir. Lembre-se de que a largura da tela disponível depende do dispositivo. O dispositivo móvel do Teams também não suporta rolagem horizontal como a área de trabalho do Teams.

#### <a name="example-knowing-when-to-stretch-columns"></a>Exemplo: saber quando estender colunas

# <a name="design"></a>[Design](#tab/design)

**Faça**: Nesta tela, existem duas colunas na parte inferior do cartão. A largura do componente de entrada é definida como `stretch`, enquanto a largura do botão **Selecionar** é definida como `auto`. Isso garante que o botão permaneça completamente em exibição.

:::image type="content" source="~/assets/images/adaptive-cards/width-auto-do.png" alt-text="A imagem mostra como definir a largura da coluna em Cartões Adaptáveis.":::

**Não faça**: Nesta tela, ambas as colunas foram `width` definidas como `auto`. Isso faz com que o botão **Selecionar** à direita seja ligeiramente cortado em comparação com a entrada.

:::image type="content" source="~/assets/images/adaptive-cards/width-auto-dont.png" alt-text="A imagem mostra como não definir a largura da coluna em Cartões Adaptáveis.":::

# <a name="code"></a>[Código](#tab/code)

Aqui está o código para implementar o exemplo de projeto que você deve seguir.

```json
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.2",
  "body": [
    {
      "type": "TextBlock",
      "text": "I wasn't able to identify the type of expense. Select from the list:",
      "wrap": true,
      "id": "typePrompt",
      "spacing": "Medium",
      "size": "Medium"
    },
    {
      "type": "ActionSet",
      "actions": [
        {
          "type": "Action.Submit",
          "title": "Phone Bill",
          "data": {
            "msteams": {
              "type": "messageBack",
              "displayText": "Phone Bill",
              "action": "Phone Bill"
            },
            "action": "Phone Bill"
          }
        },
        {
          "type": "Action.Submit",
          "title": "Taxi and Other Transportation",
          "data": {
            "msteams": {
              "type": "messageBack",
              "displayText": "Taxi and Other Transportation",
              "action": "Taxi and Other Transportation"
            },
            "action": "Taxi and Other Transportation"
          }
        },
        {
          "type": "Action.Submit",
          "title": "Entertainment_misc",
          "data": {
            "msteams": {
              "type": "messageBack",
              "displayText": "Entertainment_misc",
              "action": "Entertainment_misc"
            },
            "action": "Entertainment_misc"
          }
        },
        {
          "type": "Action.Submit",
          "title": "Car Rental",
          "data": {
            "msteams": {
              "type": "messageBack",
              "displayText": "Car Rental",
              "action": "Car Rental"
            },
            "action": "Car Rental"
          }
        },
        {
          "type": "Action.Submit",
          "title": "Airfare",
          "data": {
            "msteams": {
              "type": "messageBack",
              "displayText": "Airfare",
              "action": "Airfare"
            },
            "action": "Airfare"
          }
        }
      ],
      "spacing": "Medium"
    },
    {
      "type": "TextBlock",
      "text": "     ",
      "wrap": true
    },
    {
      "type": "ColumnSet",
      "columns": [
        {
          "type": "Column",
          "width": "stretch",
          "items": [
            {
              "type": "Input.ChoiceSet",
              "choices": [
                {
                  "title": "Meals",
                  "value": "Meals"
                },
                {
                  "title": "Parking/Tolls",
                  "value": "Parking/Tolls"
                },
                {
                  "title": "Accomodation",
                  "value": "Accomodation"
                },
                {
                  "title": "Fuel-Gas/Petrol/Diesel",
                  "value": "Fuel-Gas/Petrol/Diesel"
                },
                {
                  "title": "Hotel",
                  "value": "Hotel"
                },
                {
                  "title": "Meals - Employees Only",
                  "value": "Meals - Employees Only"
                },
                {
                  "title": "Accomodations",
                  "value": "Accomodations"
                },
                {
                  "title": "Misc.Expenses",
                  "value": "Misc.Expenses"
                },
                {
                  "title": "Please Categorize",
                  "value": "Please Categorize"
                }
              ],
              "placeholder": "All",
              "id": "expenseTypes",
              "value": "Meals - Employees Only"
            }
          ]
        },
        {
          "type": "Column",
          "width": "auto",
          "items": [
            {
              "type": "ActionSet",
              "actions": [
                {
                  "type": "Action.Submit",
                  "title": "Select",
                  "data": {
                    "msteams": {
                      "type": "messageBack",
                      "displayText": "Select",
                      "action": "applyType"
                    },
                    "action": "applyType"
                  }
                }
              ]
            }
          ]
        }
      ],
      "spacing": "ExtraLarge"
    }
  ]
}
```

---

#### <a name="example-using-fewer-columns"></a>Exemplo: usando menos colunas

**Faça**: Layouts tendem a ser exibidos melhor em dispositivos móveis com menos colunas.

:::image type="content" source="~/assets/images/adaptive-cards/column-amount-do.png" alt-text="A imagem mostra a quantidade certa de colunas em Cartões Adaptáveis.":::

**Não faça**: Uso de muitas colunas pode atrapalhar o conteúdo do cartão no celular.

:::image type="content" source="~/assets/images/adaptive-cards/column-amount-dont.png" alt-text="A imagem mostra como muitas colunas podem afetar negativamente o layout do Cartão Adaptável.":::

#### <a name="example-fixed-width-has-its-place"></a>Exemplo: a largura fixa tem seu lugar

# <a name="design"></a>[Design](#tab/design)

Quando o tamanho de algo que você está exibindo não precisa ser alterado, defina as colunas com uma largura de pixel específica. Este exemplo mostra a coluna esquerda com tamanho de 50 pixels, enquanto as descrições ao lado das miniaturas estendem o comprimento do cartão

:::image type="content" source="~/assets/images/adaptive-cards/width-auto-do.png" alt-text="A imagem mostra como definir a largura da coluna em Cartões Adaptáveis.":::

# <a name="code"></a>[Código](#tab/code)

Aqui está o código para implementar o exemplo de projeto.

```json
{
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "text": "Pick up where you left off?",
      "weight": "bolder"
    },
    {
      "type": "ColumnSet",
      "spacing": "medium",
      "columns": [
        {
          "type": "Column",
          "width": "50px",
          "items": [
            {
              "type": "Image",
              "url": "https://unsplash.it/80?image=1083",
              "size": "medium"
            }
          ]
        },
        {
          "type": "Column",
          "width": "stretch",
          "items": [
            {
              "type": "TextBlock",
              "text": "Silver Star Mountain Range"
            },
            {
              "type": "TextBlock",
              "text": "Maps",
              "isSubtle": true,
              "spacing": "none"
            }
          ]
        }
      ],
      "selectAction": {
        "type": "Action.OpenUrl",
        "url": "https://www.msn.com"
      }
    },
    {
      "type": "ColumnSet",
      "columns": [
        {
          "type": "Column",
          "width": "50px",
          "items": [
            {
              "type": "Image",
              "url": "https://unsplash.it/80?image=1082",
              "size": "medium"
            }
          ]
        },
        {
          "type": "Column",
          "width": "stretch",
          "style": "emphasis",
          "items": [
            {
              "type": "TextBlock",
              "text": "Kitchen Remodel for Homes"
            },
            {
              "type": "TextBlock",
              "text": "With EMPHASIS",
              "isSubtle": true,
              "spacing": "none"
            }
          ]
        }
      ],
      "selectAction": {
        "type": "Action.OpenUrl",
        "url": "https://www.AdaptiveCards.io"
      }
    },
    {
      "type": "ColumnSet",
      "columns": [
        {
          "type": "Column",
          "width": "50px",
          "items": [
            {
              "type": "Image",
              "url": "https://unsplash.it/80?image=1080",
              "size": "medium"
            }
          ]
        },
        {
          "type": "Column",
          "width": "stretch",
          "items": [
            {
              "type": "TextBlock",
              "text": "The Witcher: A Series"
            },
            {
              "type": "TextBlock",
              "text": "Netflix",
              "isSubtle": true,
              "spacing": "none"
            }
          ]
        }
      ],
      "selectAction": {
        "type": "Action.OpenUrl",
        "url": "https://www.outlook.com"
      }
    }
  ],
  "actions": [
    {
      "type": "Action.OpenUrl",
      "title": "Resume all",
      "url": "ms-cortana:resume-all"
    },
    {
      "type": "Action.OpenUrl",
      "title": "More activities",
      "url": "ms-cortana:more-activities"
    }
  ]
}
```

---

### <a name="text"></a>Texto

Se você estiver usando [`TextBlock`](https://adaptivecards.io/explorer/TextBlock.html), [`ColumnSet`](https://adaptivecards.io/explorer/ColumnSet.html) ou [`Input.ChoiceSet`](https://adaptivecards.io/explorer/Input.ChoiceSet.html), defina a propriedade `wrap` como `true` para que o texto do cartão não trunque no celular.

#### <a name="example-making-sure-text-doesnt-truncate"></a>Exemplo: certificando-se de que o texto não trunque

# <a name="design"></a>[Design](#tab/design)

**Faça**: Nesta tela, o cartão tem uma `wrap` propriedade definida como `true`. Isso permite que o texto se ajuste a qualquer tamanho de tela.

:::image type="content" source="~/assets/images/adaptive-cards/text-wrap-true.png" alt-text="A imagem mostra como quebrar texto em Cartões Adaptáveis.":::

**Não faça**: Nesta tela, o cartão não usa a propriedade `wrap`, portanto, o texto é cortado na tela do celular..

:::image type="content" source="~/assets/images/adaptive-cards/text-wrap-false.png" alt-text="A imagem mostra o que pode acontecer se você não quebra texto em Cartões Adaptáveis.":::

# <a name="code"></a>[Código](#tab/code)

Aqui está o código para implementar o exemplo de projeto que você deve seguir.

```json
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "text": "What cuisine do you want?"
    },
    {
      "type": "Input.ChoiceSet",
      "id": "myColor",
      "style": "compact",
      "isMultiSelect": false,
      "value": "1",
      "choices": [
        {
          "title": "Chineese",
          "value": "1"
        },
        {
          "title": "Indian",
          "value": "2"
        },
        {
          "title": "Italian",
          "value": "3"
        }
      ]
    },
    {
      "type": "TextBlock",
      "text": "Select the dishes that you like?"
    },
    {
      "type": "Input.ChoiceSet",
      "id": "myColor2",
      "style": "expanded",
      "wrap" : true,
      "isMultiSelect": false,
      "value": "1",
      "choices": [
        {
          "title": "Cauliflower with potatoes sautéed with garam masala",
          "wrap" : true,
          "value": "1"
        },
        {
          "title": "Patties of potato mixed with some vegetables fried",
          "wrap" : true,
          "value": "2"
        },
        {
          "title": "Green capsicum with potatoes sautéed with cumin seeds",
          "wrap" : true,
          "value": "3"
        }
      ]
    }
  ]
}
```

---

### <a name="containers"></a>Contêineres

Um `Container` permite agrupar um conjunto de elementos relacionados.

* **Faça**: Use a propriedade `style` para enfatizar um contêiner.
* **Faça**: Use a propriedade `selectAction` para associar uma ação a outros elementos no contêiner.
* **Faça**: Use a propriedade `Action.ToggleVisibility` para tornar um grupo de elementos recolhível.
* **Não faça**: Use contêineres por qualquer motivo diferente do mencionado anteriormente.

### <a name="images"></a>Imagens

Siga essas diretrizes ao incluir imagens em seus cartões.

* **Faça**: Projete imagens para telas DPI altas para evitar pixelação. É melhor exibir uma imagem de 100x100 pixels em 50x50 pixels do que o contrário.
* **Faça**: Se você precisa controlar o tamanho exato de suas imagens, use as propriedades `width` e `height`.
* **Não faça**: Inclua preenchimento em suas imagens. Isso normalmente introduz problemas indesejáveis de espaçamento e layout.
* Em relação à cor da tela de fundo:
  * **Faça**: Use fundos transparentes para que suas imagens se adaptem a qualquer tema do Teams.
  * **Não faça**: Inclua uma cor de fundo fixa, a menos que uma cor específica deva ser visível para seus usuários.
  * **Não faça**: Adicione uma cor de fundo a um `TextBlock` que prejudica a legibilidade. Por exemplo, se seu fundo for escuro, use uma cor de texto mais clara e vice-versa.

### <a name="actions"></a>Ações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Prática recomendada sobre como você deve incluir apenas um pequeno conjunto de ações em um Cartão Adaptável." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a>Faça: Usar até seis ações principais

Embora os Cartões Adaptáveis possam suportar seis ações primárias, a maioria dos cartões não precisa disso. As ações devem ser claras, concisas e diretas. Menos é mais.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Prática recomendada sobre como não sobrecarregar os usuários com demasiadas ações em um Cartão Adaptável." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a>Não faça: Usar mais de seis ações principais

Os Cartões Adaptáveis devem apresentar conteúdo rápido e prático. Muitas ações podem sobrecarregar um usuário.

   :::column-end:::
:::row-end:::

### <a name="frequency"></a>Frequência

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Práticas recomendadas sobre a frequência do Cartão Adaptável." border="false":::

#### <a name="do-be-concise"></a>Faça: Seja conciso

É fácil enviar vários cartões em uma conversa, mas quando os cartões saem da exibição, eles se tornam menos úteis. Experimente se limitar ao essencial. Isso é especialmente verdadeiro em um canal onde os usuários têm menos tolerância com o que percebem como "ruído".

## <a name="see-also"></a>Confira também

* [Cartões e módulos de tarefa](~/task-modules-and-cards/cards-and-task-modules.md)
* [Cartões e módulos de tarefa com suporte no bot do Teams](~/task-modules-and-cards/what-are-task-modules.md)
* [Trabalhar com Ações Universais para Cartões Adaptáveis](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/work-with-universal-actions-for-adaptive-cards.md)
* [Responder à ação de envio do módulo de tarefas](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)
* [Exibições Específicas do Usuário](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/user-specific-views.md)
