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
# <a name="respond-to-the-search-command"></a><span data-ttu-id="536c2-103">Responder ao comando de pesquisa</span><span class="sxs-lookup"><span data-stu-id="536c2-103">Respond to the search command</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="536c2-104">Seu serviço Web receberá uma `composeExtension/query` mensagem de invocação que `value` contém um objeto com os parâmetros de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="536c2-104">Your web service will receive a `composeExtension/query` invoke message that contains a `value` object with the search parameters.</span></span> <span data-ttu-id="536c2-105">Essa invocação é disparada:</span><span class="sxs-lookup"><span data-stu-id="536c2-105">This invoke is triggered:</span></span>

* <span data-ttu-id="536c2-106">À medida que os caracteres são inseridos na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="536c2-106">As characters are entered into the search box.</span></span>
* <span data-ttu-id="536c2-107">Se `initialRun` for definido como true no manifesto do aplicativo, você receberá a mensagem de invocação assim que o comando de pesquisa for chamado.</span><span class="sxs-lookup"><span data-stu-id="536c2-107">If `initialRun` is set to true in your app manifest, you'll receive the invoke message as soon as the search command is invoked.</span></span> <span data-ttu-id="536c2-108">Consulte [consulta padrão](#default-query).</span><span class="sxs-lookup"><span data-stu-id="536c2-108">See [default query](#default-query).</span></span>

<span data-ttu-id="536c2-109">Os próprios parâmetros de solicitação são encontrados no `value` objeto na solicitação, que inclui as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="536c2-109">The request parameters itself are found in the `value` object in the request, which includes the following properties:</span></span>

| <span data-ttu-id="536c2-110">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="536c2-110">Property name</span></span> | <span data-ttu-id="536c2-111">Finalidade</span><span class="sxs-lookup"><span data-stu-id="536c2-111">Purpose</span></span> |
|---|---|
| `commandId` | <span data-ttu-id="536c2-112">O nome do comando invocado pelo usuário, correspondendo a um dos comandos declarados no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="536c2-112">The name of the command invoked by the user, matching one of the commands declared in the app manifest.</span></span> |
| `parameters` | <span data-ttu-id="536c2-113">Matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="536c2-113">Array of parameters.</span></span> <span data-ttu-id="536c2-114">Cada objeto Parameter contém o nome do parâmetro, juntamente com o valor do parâmetro fornecido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="536c2-114">Each parameter object contains the parameter name, along with the parameter value provided by the user.</span></span> |
| `queryOptions` | <span data-ttu-id="536c2-115">Parâmetros de paginação:</span><span class="sxs-lookup"><span data-stu-id="536c2-115">Pagination parameters:</span></span> <br><span data-ttu-id="536c2-116">`skip`: ignorar contagem para esta consulta</span><span class="sxs-lookup"><span data-stu-id="536c2-116">`skip`: skip count for this query</span></span> <br><span data-ttu-id="536c2-117">`count`: número de elementos a serem retornados</span><span class="sxs-lookup"><span data-stu-id="536c2-117">`count`: number of elements to return</span></span> |

# <a name="cnettabdotnet"></a>[<span data-ttu-id="536c2-118">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="536c2-118">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken)
{
  //code to handle the query
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="536c2-119">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="536c2-119">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
class TeamsMessagingExtensionsSearch extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionQuery(context, query) {
  //code to handle the query
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="536c2-120">JSON</span><span class="sxs-lookup"><span data-stu-id="536c2-120">JSON</span></span>](#tab/json)

<span data-ttu-id="536c2-121">O JSON abaixo é reduzido para realçar as seções mais relevantes.</span><span class="sxs-lookup"><span data-stu-id="536c2-121">The JSON below is shortened to highlight the most relevant sections.</span></span>

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

## <a name="respond-to-user-requests"></a><span data-ttu-id="536c2-122">Responder às solicitações do usuário</span><span class="sxs-lookup"><span data-stu-id="536c2-122">Respond to user requests</span></span>

<span data-ttu-id="536c2-123">Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona para o serviço.</span><span class="sxs-lookup"><span data-stu-id="536c2-123">When the user performs a query, Microsoft Teams issues a synchronous HTTP request to your service.</span></span> <span data-ttu-id="536c2-124">Nesse ponto, o código tem cinco segundos para fornecer uma resposta HTTP para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="536c2-124">At that point, your code has 5 seconds to provide an HTTP response to the request.</span></span> <span data-ttu-id="536c2-125">Durante esse tempo, o serviço pode executar pesquisa adicional ou qualquer outra lógica de negócios necessária para atender à solicitação.</span><span class="sxs-lookup"><span data-stu-id="536c2-125">During this time, your service can perform additional lookup, or any other business logic needed to serve the request.</span></span>

<span data-ttu-id="536c2-126">Seu serviço deve responder com os resultados que correspondem à consulta do usuário.</span><span class="sxs-lookup"><span data-stu-id="536c2-126">Your service should respond with the results matching the user query.</span></span> <span data-ttu-id="536c2-127">A resposta deve indicar um código de `200 OK` status HTTP e um objeto Application/JSON válido com o seguinte corpo:</span><span class="sxs-lookup"><span data-stu-id="536c2-127">The response must indicate an HTTP status code of `200 OK` and a valid application/json object with the following body:</span></span>

|<span data-ttu-id="536c2-128">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="536c2-128">Property name</span></span>|<span data-ttu-id="536c2-129">Finalidade</span><span class="sxs-lookup"><span data-stu-id="536c2-129">Purpose</span></span>|
|---|---|
|`composeExtension`|<span data-ttu-id="536c2-130">Envelope de resposta de nível superior.</span><span class="sxs-lookup"><span data-stu-id="536c2-130">Top-level response envelope.</span></span>|
|`composeExtension.type`|<span data-ttu-id="536c2-131">Tipo de resposta.</span><span class="sxs-lookup"><span data-stu-id="536c2-131">Type of response.</span></span> <span data-ttu-id="536c2-132">Há suporte para os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="536c2-132">The following types are supported:</span></span> <br><span data-ttu-id="536c2-133">`result`: exibe uma lista de resultados de pesquisa</span><span class="sxs-lookup"><span data-stu-id="536c2-133">`result`: displays a list of search results</span></span> <br><span data-ttu-id="536c2-134">`auth`: solicita que o usuário autentique</span><span class="sxs-lookup"><span data-stu-id="536c2-134">`auth`: asks the user to authenticate</span></span> <br><span data-ttu-id="536c2-135">`config`: solicita que o usuário configure a extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="536c2-135">`config`: asks the user to set up the messaging extension</span></span> <br><span data-ttu-id="536c2-136">`message`: exibe uma mensagem de texto sem formatação</span><span class="sxs-lookup"><span data-stu-id="536c2-136">`message`: displays a plain text message</span></span> |
|`composeExtension.attachmentLayout`|<span data-ttu-id="536c2-137">Especifica o layout dos anexos.</span><span class="sxs-lookup"><span data-stu-id="536c2-137">Specifies the layout of the attachments.</span></span> <span data-ttu-id="536c2-138">Usado para respostas do tipo `result`.</span><span class="sxs-lookup"><span data-stu-id="536c2-138">Used for responses of type `result`.</span></span> <br><span data-ttu-id="536c2-139">Atualmente, há suporte para os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="536c2-139">Currently the following types are supported:</span></span> <br><span data-ttu-id="536c2-140">`list`: uma lista de objetos Card contendo campos de miniatura, título e texto</span><span class="sxs-lookup"><span data-stu-id="536c2-140">`list`: a list of card objects containing thumbnail, title, and text fields</span></span> <br><span data-ttu-id="536c2-141">`grid`: uma grade de imagens em miniatura</span><span class="sxs-lookup"><span data-stu-id="536c2-141">`grid`: a grid of thumbnail images</span></span> |
|`composeExtension.attachments`|<span data-ttu-id="536c2-142">Matriz de objetos Attachment válidos.</span><span class="sxs-lookup"><span data-stu-id="536c2-142">Array of valid attachment objects.</span></span> <span data-ttu-id="536c2-143">Usado para respostas do tipo `result`.</span><span class="sxs-lookup"><span data-stu-id="536c2-143">Used for responses of type `result`.</span></span> <br><span data-ttu-id="536c2-144">Atualmente, há suporte para os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="536c2-144">Currently the following types are supported:</span></span> <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|<span data-ttu-id="536c2-145">Ações sugeridas.</span><span class="sxs-lookup"><span data-stu-id="536c2-145">Suggested actions.</span></span> <span data-ttu-id="536c2-146">Usado para respostas do tipo `auth` ou `config`.</span><span class="sxs-lookup"><span data-stu-id="536c2-146">Used for responses of type `auth` or `config`.</span></span> |
|`composeExtension.text`|<span data-ttu-id="536c2-147">Mensagem a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="536c2-147">Message to display.</span></span> <span data-ttu-id="536c2-148">Usado para respostas do tipo `message`.</span><span class="sxs-lookup"><span data-stu-id="536c2-148">Used for responses of type `message`.</span></span> |

### <a name="response-card-types-and-previews"></a><span data-ttu-id="536c2-149">Tipos e visualizações de cartões de resposta</span><span class="sxs-lookup"><span data-stu-id="536c2-149">Response card types and previews</span></span>

<span data-ttu-id="536c2-150">Oferecemos suporte para os seguintes tipos de anexo:</span><span class="sxs-lookup"><span data-stu-id="536c2-150">We support the following attachment types:</span></span>

* [<span data-ttu-id="536c2-151">Cartão de miniaturas</span><span class="sxs-lookup"><span data-stu-id="536c2-151">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="536c2-152">Cartão herói</span><span class="sxs-lookup"><span data-stu-id="536c2-152">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="536c2-153">Cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="536c2-153">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="536c2-154">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="536c2-154">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="536c2-155">Confira [o que são cartões](~/task-modules-and-cards/what-are-cards.md) para uma visão geral.</span><span class="sxs-lookup"><span data-stu-id="536c2-155">See [What are cards](~/task-modules-and-cards/what-are-cards.md) for an overview.</span></span>

<span data-ttu-id="536c2-156">Para saber como usar os tipos de cartão de miniatura e herói, confira [Adicionar cartões e ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="536c2-156">To learn how to use the thumbnail and hero card types, see [Add cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

<span data-ttu-id="536c2-157">Para obter documentação adicional sobre a placa de conector do Office 365, consulte [usando cartões de conector do office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="536c2-157">For additional documentation regarding the Office 365 Connector card, see [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="536c2-158">A lista de resultados é exibida na interface do usuário do Microsoft Teams com uma visualização de cada item.</span><span class="sxs-lookup"><span data-stu-id="536c2-158">The result list is displayed in the Microsoft Teams UI with a preview of each item.</span></span> <span data-ttu-id="536c2-159">A visualização é gerada de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="536c2-159">The preview is generated in one of two ways:</span></span>

* <span data-ttu-id="536c2-160">Usando a `preview` Propriedade dentro do `attachment` objeto.</span><span class="sxs-lookup"><span data-stu-id="536c2-160">Using the `preview` property within the `attachment` object.</span></span> <span data-ttu-id="536c2-161">O `preview` anexo só pode ser um herói ou cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="536c2-161">The `preview` attachment can only be a Hero or Thumbnail card.</span></span>
* <span data-ttu-id="536c2-162">Extraído do básico `title`, `text`e `image` das propriedades do anexo.</span><span class="sxs-lookup"><span data-stu-id="536c2-162">Extracted from the basic `title`, `text`, and `image` properties of the attachment.</span></span> <span data-ttu-id="536c2-163">Eles são usados apenas se a `preview` propriedade não estiver definida e essas propriedades estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="536c2-163">These are used only if the `preview` property is not set and these properties are available.</span></span>

<span data-ttu-id="536c2-164">Você pode exibir uma visualização de um cartão adaptável ou cartão de conexão com o Office 365 na lista de resultados, simplesmente pela propriedade Preview.</span><span class="sxs-lookup"><span data-stu-id="536c2-164">You can display a preview of an Adaptive Card or Office 365 Connector card in the result list simply by its preview property.</span></span> <span data-ttu-id="536c2-165">Isso não é necessário se os resultados já são herói ou cartões em miniatura.</span><span class="sxs-lookup"><span data-stu-id="536c2-165">This is not necessary if the results are already hero or thumbnail cards.</span></span> <span data-ttu-id="536c2-166">Se você usar o anexo de visualização, ele deve ser um herói ou cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="536c2-166">If you use the preview attachment, it must be either a Hero or Thumbnail card.</span></span> <span data-ttu-id="536c2-167">Se nenhuma propriedade Preview for especificada, a visualização do cartão falhará e nada será exibido.</span><span class="sxs-lookup"><span data-stu-id="536c2-167">If no preview property is specified, the preview of the card will fail and nothing will be displayed.</span></span>

### <a name="response-example"></a><span data-ttu-id="536c2-168">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="536c2-168">Response example</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="536c2-169">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="536c2-169">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="536c2-170">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="536c2-170">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="jsontabjson"></a>[<span data-ttu-id="536c2-171">JSON</span><span class="sxs-lookup"><span data-stu-id="536c2-171">JSON</span></span>](#tab/json)

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

## <a name="default-query"></a><span data-ttu-id="536c2-172">Consulta padrão</span><span class="sxs-lookup"><span data-stu-id="536c2-172">Default query</span></span>

<span data-ttu-id="536c2-173">Se você definir `initialRun` para `true` no manifesto, o Microsoft Teams emitirá uma consulta "padrão" quando o usuário abrir pela primeira vez a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="536c2-173">If you set `initialRun` to `true` in the manifest, Microsoft Teams issues a "default" query when the user first opens the messaging extension.</span></span> <span data-ttu-id="536c2-174">O serviço pode responder a essa consulta com um conjunto de resultados previamente preenchidos.</span><span class="sxs-lookup"><span data-stu-id="536c2-174">Your service can respond to this query with a set of pre-populated results.</span></span> <span data-ttu-id="536c2-175">Isso pode ser útil quando o comando de pesquisa requer autenticação ou configuração, exibindo itens exibidos recentemente, favoritos ou qualquer outra informação que não seja dependente da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="536c2-175">This can be useful when your search command requires authentication or configuration, displaying recently viewed items, favorites, or any other information that is not dependent on user input.</span></span>

<span data-ttu-id="536c2-176">A consulta padrão tem a mesma estrutura que qualquer consulta de usuário regular, com `name` o campo definido `initialRun` como `value` e definido `true` como no objeto abaixo.</span><span class="sxs-lookup"><span data-stu-id="536c2-176">The default query has the same structure as any regular user query, with the `name` field set to `initialRun` and `value` set to `true` as in the object below.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="536c2-177">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="536c2-177">Next Steps</span></span>

<span data-ttu-id="536c2-178">Adicionar autenticação e/ou configuração</span><span class="sxs-lookup"><span data-stu-id="536c2-178">Add authentication and/or configuration</span></span>

* [<span data-ttu-id="536c2-179">Adicionar autenticação a uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="536c2-179">Add authentication to a messaging extension</span></span>](~/messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="536c2-180">Adicionar configuração a uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="536c2-180">Add configuration to a messaging extension</span></span>](~/messaging-extensions/how-to/add-configuration-page.md)

<span data-ttu-id="536c2-181">Implantar configuração</span><span class="sxs-lookup"><span data-stu-id="536c2-181">Deploy configuration</span></span>

* [<span data-ttu-id="536c2-182">Implantar seu pacote de aplicativos</span><span class="sxs-lookup"><span data-stu-id="536c2-182">Deploy your app package</span></span>](~/concepts/deploy-and-publish/apps-upload.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
