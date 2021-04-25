---
title: Responder ao comando de pesquisa
author: clearab
description: Como responder ao comando de pesquisa de uma extensão de mensagens em um aplicativo do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 4dff59d0bd923618a3079c81cbb6f9e7aea2bab4
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2021
ms.locfileid: "51996006"
---
# <a name="respond-to-search-command"></a><span data-ttu-id="76f1a-103">Responder ao comando de pesquisa</span><span class="sxs-lookup"><span data-stu-id="76f1a-103">Respond to search command</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="76f1a-104">Depois que o usuário envia o comando de pesquisa, seu serviço Web recebe uma mensagem de invocação que contém um `composeExtension/query` `value` objeto com os parâmetros de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="76f1a-104">After the user submits the search command, your web service receives a `composeExtension/query` invoke message that contains a `value` object with the search parameters.</span></span> <span data-ttu-id="76f1a-105">Essa invocação é disparada com as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="76f1a-105">This invoke is triggered with the following conditions:</span></span>

* <span data-ttu-id="76f1a-106">À medida que os caracteres são inseridos na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="76f1a-106">As characters are entered into the search box.</span></span>
* <span data-ttu-id="76f1a-107">`initialRun` é definido como true no manifesto do aplicativo, você recebe a mensagem de invocação assim que o comando de pesquisa é invocado.</span><span class="sxs-lookup"><span data-stu-id="76f1a-107">`initialRun` is set to true in your app manifest, you receive the invoke message as soon as the search command is invoked.</span></span> <span data-ttu-id="76f1a-108">Para obter mais informações, consulte [consulta padrão](#default-query).</span><span class="sxs-lookup"><span data-stu-id="76f1a-108">For more information, see [default query](#default-query).</span></span>

<span data-ttu-id="76f1a-109">Este documento orienta você sobre como responder a solicitações de usuário na forma de cartões e visualizações e as condições em que o Microsoft Teams emite uma consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="76f1a-109">This document guides you on how to respond to user requests in the form of cards and previews, and the conditions under which Microsoft Teams issues a default query.</span></span>

<span data-ttu-id="76f1a-110">Os parâmetros de solicitação são encontrados no objeto na `value` solicitação, que inclui as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="76f1a-110">The request parameters are found in the `value` object in the request, which includes the following properties:</span></span>

| <span data-ttu-id="76f1a-111">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="76f1a-111">Property name</span></span> | <span data-ttu-id="76f1a-112">Objetivo</span><span class="sxs-lookup"><span data-stu-id="76f1a-112">Purpose</span></span> |
|---|---|
| `commandId` | <span data-ttu-id="76f1a-113">O nome do comando invocado pelo usuário, correspondendo a um dos comandos declarados no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76f1a-113">The name of the command invoked by the user, matching one of the commands declared in the app manifest.</span></span> |
| `parameters` | <span data-ttu-id="76f1a-114">Matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="76f1a-114">Array of parameters.</span></span> <span data-ttu-id="76f1a-115">Cada objeto de parâmetro contém o nome do parâmetro, juntamente com o valor do parâmetro fornecido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="76f1a-115">Each parameter object contains the parameter name, along with the parameter value provided by the user.</span></span> |
| `queryOptions` | <span data-ttu-id="76f1a-116">Parâmetros paginação:</span><span class="sxs-lookup"><span data-stu-id="76f1a-116">Pagination parameters:</span></span> <br><span data-ttu-id="76f1a-117">`skip`: Ignorar contagem para essa consulta</span><span class="sxs-lookup"><span data-stu-id="76f1a-117">`skip`: Skip count for this query</span></span> <br><span data-ttu-id="76f1a-118">`count`: Número de elementos a retornar.</span><span class="sxs-lookup"><span data-stu-id="76f1a-118">`count`: Number of elements to return.</span></span> |

# <a name="cnet"></a>[<span data-ttu-id="76f1a-119">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76f1a-119">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken)
{
  //code to handle the query
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76f1a-120">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76f1a-120">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
class TeamsMessagingExtensionsSearch extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionQuery(context, query) {
  //code to handle the query
    }
}
```

# <a name="json"></a>[<span data-ttu-id="76f1a-121">JSON</span><span class="sxs-lookup"><span data-stu-id="76f1a-121">JSON</span></span>](#tab/json)

<span data-ttu-id="76f1a-122">O JSON abaixo é reduzido para realçar as seções mais relevantes.</span><span class="sxs-lookup"><span data-stu-id="76f1a-122">The JSON below is shortened to highlight the most relevant sections.</span></span>

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

## <a name="respond-to-user-requests"></a><span data-ttu-id="76f1a-123">Responder a solicitações de usuário</span><span class="sxs-lookup"><span data-stu-id="76f1a-123">Respond to user requests</span></span>

<span data-ttu-id="76f1a-124">Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="76f1a-124">When the user performs a query, Microsoft Teams issues a synchronous HTTP request to your service.</span></span> <span data-ttu-id="76f1a-125">Nesse ponto, seu código tem `5` segundos para fornecer uma resposta HTTP à solicitação.</span><span class="sxs-lookup"><span data-stu-id="76f1a-125">At that point, your code has `5` seconds to provide an HTTP response to the request.</span></span> <span data-ttu-id="76f1a-126">Durante esse tempo, seu serviço pode realizar uma consulta adicional ou qualquer outra lógica de negócios necessária para atender à solicitação.</span><span class="sxs-lookup"><span data-stu-id="76f1a-126">During this time, your service can perform additional lookup, or any other business logic needed to serve the request.</span></span>

<span data-ttu-id="76f1a-127">Seu serviço deve responder com os resultados correspondentes à consulta do usuário.</span><span class="sxs-lookup"><span data-stu-id="76f1a-127">Your service must respond with the results matching the user query.</span></span> <span data-ttu-id="76f1a-128">A resposta deve indicar um código de status HTTP e `200 OK` um aplicativo ou objeto JSON válido com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="76f1a-128">The response must indicate an HTTP status code of `200 OK` and a valid application or JSON object with the following properties:</span></span>

|<span data-ttu-id="76f1a-129">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="76f1a-129">Property name</span></span>|<span data-ttu-id="76f1a-130">Objetivo</span><span class="sxs-lookup"><span data-stu-id="76f1a-130">Purpose</span></span>|
|---|---|
|`composeExtension`|<span data-ttu-id="76f1a-131">Envelope de resposta de nível superior.</span><span class="sxs-lookup"><span data-stu-id="76f1a-131">Top-level response envelope.</span></span>|
|`composeExtension.type`|<span data-ttu-id="76f1a-132">Tipo de resposta.</span><span class="sxs-lookup"><span data-stu-id="76f1a-132">Type of response.</span></span> <span data-ttu-id="76f1a-133">Os seguintes tipos são suportados:</span><span class="sxs-lookup"><span data-stu-id="76f1a-133">The following types are supported:</span></span> <br><span data-ttu-id="76f1a-134">`result`: Exibe uma lista de resultados da pesquisa</span><span class="sxs-lookup"><span data-stu-id="76f1a-134">`result`: Displays a list of search results</span></span> <br><span data-ttu-id="76f1a-135">`auth`: Pede ao usuário para autenticar</span><span class="sxs-lookup"><span data-stu-id="76f1a-135">`auth`: Asks the user to authenticate</span></span> <br><span data-ttu-id="76f1a-136">`config`: Pede ao usuário para configurar a extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="76f1a-136">`config`: Asks the user to set up the messaging extension</span></span> <br><span data-ttu-id="76f1a-137">`message`: Exibe uma mensagem de texto sem texto</span><span class="sxs-lookup"><span data-stu-id="76f1a-137">`message`: Displays a plain text message</span></span> |
|`composeExtension.attachmentLayout`|<span data-ttu-id="76f1a-138">Especifica o layout dos anexos.</span><span class="sxs-lookup"><span data-stu-id="76f1a-138">Specifies the layout of the attachments.</span></span> <span data-ttu-id="76f1a-139">Usado para respostas do tipo `result` .</span><span class="sxs-lookup"><span data-stu-id="76f1a-139">Used for responses of type `result`.</span></span> <br><span data-ttu-id="76f1a-140">Atualmente, os seguintes tipos são suportados:</span><span class="sxs-lookup"><span data-stu-id="76f1a-140">Currently, the following types are supported:</span></span> <br><span data-ttu-id="76f1a-141">`list`: Uma lista de objetos de cartão que contêm campos de miniatura, título e texto</span><span class="sxs-lookup"><span data-stu-id="76f1a-141">`list`: A list of card objects containing thumbnail, title, and text fields</span></span> <br><span data-ttu-id="76f1a-142">`grid`: uma grade de imagens em miniatura</span><span class="sxs-lookup"><span data-stu-id="76f1a-142">`grid`: A grid of thumbnail images</span></span> |
|`composeExtension.attachments`|<span data-ttu-id="76f1a-143">Matriz de objetos de anexo válidos.</span><span class="sxs-lookup"><span data-stu-id="76f1a-143">Array of valid attachment objects.</span></span> <span data-ttu-id="76f1a-144">Usado para respostas do tipo `result` .</span><span class="sxs-lookup"><span data-stu-id="76f1a-144">Used for responses of type `result`.</span></span> <br><span data-ttu-id="76f1a-145">Atualmente, os seguintes tipos são suportados:</span><span class="sxs-lookup"><span data-stu-id="76f1a-145">Currently, the following types are supported:</span></span> <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|<span data-ttu-id="76f1a-146">Ações sugeridas.</span><span class="sxs-lookup"><span data-stu-id="76f1a-146">Suggested actions.</span></span> <span data-ttu-id="76f1a-147">Usado para respostas de tipo `auth` ou `config` .</span><span class="sxs-lookup"><span data-stu-id="76f1a-147">Used for responses of type `auth` or `config`.</span></span> |
|`composeExtension.text`|<span data-ttu-id="76f1a-148">Mensagem a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="76f1a-148">Message to display.</span></span> <span data-ttu-id="76f1a-149">Usado para respostas do tipo `message` .</span><span class="sxs-lookup"><span data-stu-id="76f1a-149">Used for responses of type `message`.</span></span> |

### <a name="response-card-types-and-previews"></a><span data-ttu-id="76f1a-150">Tipos de cartão de resposta e visualizações</span><span class="sxs-lookup"><span data-stu-id="76f1a-150">Response card types and previews</span></span>

<span data-ttu-id="76f1a-151">O Teams dá suporte aos seguintes tipos de cartão:</span><span class="sxs-lookup"><span data-stu-id="76f1a-151">Teams supports the following card types:</span></span>

* [<span data-ttu-id="76f1a-152">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="76f1a-152">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="76f1a-153">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="76f1a-153">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="76f1a-154">Cartão do Conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="76f1a-154">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="76f1a-155">Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="76f1a-155">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="76f1a-156">Para ter uma melhor compreensão e visão geral sobre cartões, consulte [o que são cartões](~/task-modules-and-cards/what-are-cards.md).</span><span class="sxs-lookup"><span data-stu-id="76f1a-156">To have a better understanding and overview on cards, see [what are cards](~/task-modules-and-cards/what-are-cards.md).</span></span>

<span data-ttu-id="76f1a-157">Para saber como usar os tipos de miniatura e cartão de herói, consulte [adicionar cartões e ações de cartão.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="76f1a-157">To learn how to use the thumbnail and hero card types, see [add cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

<span data-ttu-id="76f1a-158">Para obter informações adicionais sobre o cartão conector do Office 365, consulte [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="76f1a-158">For additional information regarding the Office 365 Connector card, see [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="76f1a-159">A lista de resultados é exibida na interface do usuário do Microsoft Teams com uma visualização de cada item.</span><span class="sxs-lookup"><span data-stu-id="76f1a-159">The result list is displayed in the Microsoft Teams UI with a preview of each item.</span></span> <span data-ttu-id="76f1a-160">A visualização é gerada de uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="76f1a-160">The preview is generated in one of the two ways:</span></span>

* <span data-ttu-id="76f1a-161">Usando a `preview` propriedade dentro do `attachment` objeto.</span><span class="sxs-lookup"><span data-stu-id="76f1a-161">Using the `preview` property within the `attachment` object.</span></span> <span data-ttu-id="76f1a-162">O `preview` anexo só pode ser um cartão Hero ou Thumbnail.</span><span class="sxs-lookup"><span data-stu-id="76f1a-162">The `preview` attachment can only be a Hero or Thumbnail card.</span></span>
* <span data-ttu-id="76f1a-163">Extraído das propriedades `title` básicas `text` , e do `image` anexo.</span><span class="sxs-lookup"><span data-stu-id="76f1a-163">Extracted from the basic `title`, `text`, and `image` properties of the attachment.</span></span> <span data-ttu-id="76f1a-164">Eles são usados somente se `preview` a propriedade não estiver definida e essas propriedades estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="76f1a-164">These are used only if the `preview` property is not set and these properties are available.</span></span>
* <span data-ttu-id="76f1a-165">O botão cartão Hero ou Thumbnail e as ações de toque, exceto invocar, não são suportadas no cartão de visualização.</span><span class="sxs-lookup"><span data-stu-id="76f1a-165">The Hero or Thumbnail card button and tap actions, except invoke, are not supported in the preview card.</span></span>

<span data-ttu-id="76f1a-166">Você pode exibir uma visualização de um cartão adaptável ou cartão conector do Office 365 na lista de resultados usando sua propriedade de visualização.</span><span class="sxs-lookup"><span data-stu-id="76f1a-166">You can display a preview of an Adaptive Card or Office 365 Connector card in the result list using its preview property.</span></span> <span data-ttu-id="76f1a-167">A propriedade preview não será necessária se os resultados já são cartões Hero ou Thumbnail.</span><span class="sxs-lookup"><span data-stu-id="76f1a-167">The preview property is not necessary if the results are already Hero or Thumbnail cards.</span></span> <span data-ttu-id="76f1a-168">Se você usar o anexo de visualização, ele deve ser um cartão Hero ou Thumbnail.</span><span class="sxs-lookup"><span data-stu-id="76f1a-168">If you use the preview attachment, it must be either a Hero or Thumbnail card.</span></span> <span data-ttu-id="76f1a-169">Se nenhuma propriedade preview for especificada, a visualização do cartão falhará e nada será exibido.</span><span class="sxs-lookup"><span data-stu-id="76f1a-169">If no preview property is specified, the preview of the card fails and nothing is displayed.</span></span>

### <a name="response-example"></a><span data-ttu-id="76f1a-170">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="76f1a-170">Response example</span></span>

# <a name="cnet"></a>[<span data-ttu-id="76f1a-171">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="76f1a-171">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="76f1a-172">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="76f1a-172">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="76f1a-173">JSON</span><span class="sxs-lookup"><span data-stu-id="76f1a-173">JSON</span></span>](#tab/json)

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

## <a name="default-query"></a><span data-ttu-id="76f1a-174">Consulta padrão</span><span class="sxs-lookup"><span data-stu-id="76f1a-174">Default query</span></span>

<span data-ttu-id="76f1a-175">Se você definir como no manifesto, o Microsoft Teams emite uma consulta padrão quando o usuário abre pela primeira vez a extensão `initialRun` `true` de mensagens. </span><span class="sxs-lookup"><span data-stu-id="76f1a-175">If you set `initialRun` to `true` in the manifest, Microsoft Teams issues a **default** query when the user first opens the messaging extension.</span></span> <span data-ttu-id="76f1a-176">Seu serviço pode responder a essa consulta com um conjunto de resultados pré-preenchidos.</span><span class="sxs-lookup"><span data-stu-id="76f1a-176">Your service can respond to this query with a set of pre-populated results.</span></span> <span data-ttu-id="76f1a-177">Isso é útil quando o comando de pesquisa exige autenticação ou configuração, exibindo itens, favoritos ou qualquer outra informação que não dependa da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="76f1a-177">This is useful when your search command requires authentication or configuration, displaying recently viewed items, favorites, or any other information that is not dependent on user input.</span></span>

<span data-ttu-id="76f1a-178">A consulta padrão tem a mesma estrutura que qualquer consulta de usuário regular, com o campo definido como e definido como mostrado `name` `initialRun` no seguinte `value` `true` objeto:</span><span class="sxs-lookup"><span data-stu-id="76f1a-178">The default query has the same structure as any regular user query, with the `name` field set to `initialRun` and `value` set to `true` as shown in the following object:</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="76f1a-179">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="76f1a-179">Code sample</span></span>

| <span data-ttu-id="76f1a-180">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="76f1a-180">Sample Name</span></span>           | <span data-ttu-id="76f1a-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="76f1a-181">Description</span></span> | <span data-ttu-id="76f1a-182">.NET</span><span class="sxs-lookup"><span data-stu-id="76f1a-182">.NET</span></span>    | <span data-ttu-id="76f1a-183">Node.js</span><span class="sxs-lookup"><span data-stu-id="76f1a-183">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="76f1a-184">Ação de extensão de mensagens do Teams</span><span class="sxs-lookup"><span data-stu-id="76f1a-184">Teams messaging extension action</span></span>| <span data-ttu-id="76f1a-185">Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="76f1a-185">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="76f1a-186">View</span><span class="sxs-lookup"><span data-stu-id="76f1a-186">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="76f1a-187">View</span><span class="sxs-lookup"><span data-stu-id="76f1a-187">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="76f1a-188">Pesquisa de extensão de mensagens do Teams</span><span class="sxs-lookup"><span data-stu-id="76f1a-188">Teams messaging extension search</span></span>   |  <span data-ttu-id="76f1a-189">Descreve como definir comandos de pesquisa e responder a pesquisas.</span><span class="sxs-lookup"><span data-stu-id="76f1a-189">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="76f1a-190">View</span><span class="sxs-lookup"><span data-stu-id="76f1a-190">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="76f1a-191">View</span><span class="sxs-lookup"><span data-stu-id="76f1a-191">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="see-also"></a><span data-ttu-id="76f1a-192">Confira também</span><span class="sxs-lookup"><span data-stu-id="76f1a-192">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="76f1a-193">Adicionar configuração a uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="76f1a-193">Add configuration to a messaging extension</span></span>](~/messaging-extensions/how-to/add-configuration-page.md)
 
## <a name="next-step"></a><span data-ttu-id="76f1a-194">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="76f1a-194">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="76f1a-195">Adicionar autenticação a uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="76f1a-195">Add authentication to a messaging extension</span></span>](~/messaging-extensions/how-to/add-authentication.md)



