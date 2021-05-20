---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots em Teams
localization_priority: Normal
keywords: referência de cartões de bots
ms.topic: reference
ms.openlocfilehash: cab7f1659759f40beb1aba59531ee6c1a84662c1
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566856"
---
# <a name="cards-reference"></a><span data-ttu-id="57294-104">Referência de cartões</span><span class="sxs-lookup"><span data-stu-id="57294-104">Cards reference</span></span>

<span data-ttu-id="57294-105">Os cartões listados neste documento são suportados em bots para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="57294-105">The cards listed in this document are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="57294-106">Eles são baseados em cartões definidos pelo Bot Framework, mas Teams não suporta todos os cartões Bot Framework e, em vez disso, alguns cartões Teams foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="57294-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and instead some Teams cards have been added.</span></span> <span data-ttu-id="57294-107">As diferenças são chamadas nas referências deste documento.</span><span class="sxs-lookup"><span data-stu-id="57294-107">Differences are called out in the references in this document.</span></span>

## <a name="card-examples"></a><span data-ttu-id="57294-108">Exemplos de cartões</span><span class="sxs-lookup"><span data-stu-id="57294-108">Card examples</span></span>

<span data-ttu-id="57294-109">Você pode encontrar informações adicionais sobre como usar cartões na documentação para o Bot Builder SDK v3.</span><span class="sxs-lookup"><span data-stu-id="57294-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK v3.</span></span> <span data-ttu-id="57294-110">As amostras de código também estão disponíveis no repositório Microsoft/BotBuilder-Samples em GitHub.</span><span class="sxs-lookup"><span data-stu-id="57294-110">Code samples are also available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="57294-111">.NET</span><span class="sxs-lookup"><span data-stu-id="57294-111">.NET</span></span>
  * <span data-ttu-id="57294-112">[Adicione cartões como anexos às mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="57294-112">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="57294-113">[Código de amostra de cartões Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="57294-113">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span></span>

* <span data-ttu-id="57294-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="57294-114">Node.js</span></span>
  * <span data-ttu-id="57294-115">[Adicione cartões como anexos às mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="57294-115">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="57294-116">[Código de amostra de cartões Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="57294-116">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span></span>

## <a name="types-of-cards"></a><span data-ttu-id="57294-117">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="57294-117">Types of cards</span></span>

<span data-ttu-id="57294-118">Esta tabela mostra os tipos de cartões disponíveis para você:</span><span class="sxs-lookup"><span data-stu-id="57294-118">This table shows the types of cards available to you:</span></span>

| <span data-ttu-id="57294-119">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="57294-119">Card type</span></span> | <span data-ttu-id="57294-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="57294-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="57294-121">Cartão adaptativo</span><span class="sxs-lookup"><span data-stu-id="57294-121">Adaptive card</span></span>](#adaptive-card) | <span data-ttu-id="57294-122">Este cartão é altamente personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="57294-122">This card is highly customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> |
| [<span data-ttu-id="57294-123">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="57294-123">Hero card</span></span>](#hero-card) | <span data-ttu-id="57294-124">Este cartão normalmente contém uma única imagem grande, um ou mais botões, e uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="57294-124">This card typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="57294-125">Cartão de lista</span><span class="sxs-lookup"><span data-stu-id="57294-125">List card</span></span>](#list-card) | <span data-ttu-id="57294-126">Este cartão é uma lista de itens de rolagem.</span><span class="sxs-lookup"><span data-stu-id="57294-126">This card is a scrolling list of items.</span></span> |
| [<span data-ttu-id="57294-127">cartão conector Office 365</span><span class="sxs-lookup"><span data-stu-id="57294-127">Office 365 connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="57294-128">Este cartão tem um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="57294-128">This card has a flexible layout with multiple sections, fields, images, and actions.</span></span> |
| [<span data-ttu-id="57294-129">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="57294-129">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="57294-130">Este cartão fornece um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="57294-130">This card provides a receipt to the user.</span></span> |
| [<span data-ttu-id="57294-131">Cartão de sinalização</span><span class="sxs-lookup"><span data-stu-id="57294-131">Signin card</span></span>](#signin-card) | <span data-ttu-id="57294-132">Este cartão permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="57294-132">This card enables a bot to request that a user signs in.</span></span> |
| [<span data-ttu-id="57294-133">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="57294-133">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="57294-134">Esta placa normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões.</span><span class="sxs-lookup"><span data-stu-id="57294-134">This card typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="57294-135">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="57294-135">Card collections</span></span>](#card-collections) | <span data-ttu-id="57294-136">Este cartão é usado para retornar vários itens em uma única resposta.</span><span class="sxs-lookup"><span data-stu-id="57294-136">This cards is used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="57294-137">Propriedades comuns para todos os cartões</span><span class="sxs-lookup"><span data-stu-id="57294-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="57294-138">Imagens de cartão inline</span><span class="sxs-lookup"><span data-stu-id="57294-138">Inline card images</span></span>

<span data-ttu-id="57294-139">O cartão pode conter uma imagem inline, incluindo um link para a imagem disponível publicamente.</span><span class="sxs-lookup"><span data-stu-id="57294-139">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="57294-140">Para fins de desempenho, é altamente recomendável que você hospede a imagem em uma rede pública de entrega de conteúdo (CDN).</span><span class="sxs-lookup"><span data-stu-id="57294-140">For performance purposes, it is highly recommended you host the image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="57294-141">As imagens são dimensionadas para cima ou para baixo em tamanho, mantendo a proporção para cobrir a área da imagem.</span><span class="sxs-lookup"><span data-stu-id="57294-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area.</span></span> <span data-ttu-id="57294-142">As imagens são então cortadas do centro para alcançar a proporção apropriada para o cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-142">Images are then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="57294-143">As imagens devem ser no máximo 1024×1024, no formato PNG, JPEG ou GIF, e não suportam GIF animado.</span><span class="sxs-lookup"><span data-stu-id="57294-143">Images must be at most 1024×1024, in PNG, JPEG, or GIF format, and do not support animated GIF.</span></span>

| <span data-ttu-id="57294-144">Propriedade</span><span class="sxs-lookup"><span data-stu-id="57294-144">Property</span></span> | <span data-ttu-id="57294-145">Tipo</span><span class="sxs-lookup"><span data-stu-id="57294-145">Type</span></span>  | <span data-ttu-id="57294-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="57294-146">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="57294-147">url</span><span class="sxs-lookup"><span data-stu-id="57294-147">url</span></span> | <span data-ttu-id="57294-148">URL</span><span class="sxs-lookup"><span data-stu-id="57294-148">URL</span></span> | <span data-ttu-id="57294-149">URL HTTPS para a imagem.</span><span class="sxs-lookup"><span data-stu-id="57294-149">HTTPS URL to the image.</span></span> |
| <span data-ttu-id="57294-150">alt</span><span class="sxs-lookup"><span data-stu-id="57294-150">alt</span></span> | <span data-ttu-id="57294-151">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="57294-151">String</span></span> | <span data-ttu-id="57294-152">Descrição acessível da imagem.</span><span class="sxs-lookup"><span data-stu-id="57294-152">Accessible description of the image.</span></span> |

> [!NOTE]
> <span data-ttu-id="57294-153">Se um cartão incluir uma URL de imagem que passa por um redirecionamento antes da imagem final, o redirecionamento na URL de imagem não será suportado.</span><span class="sxs-lookup"><span data-stu-id="57294-153">If a card includes an image URL that goes through a redirect before the final image, the redirect in image URL is not supported.</span></span> <span data-ttu-id="57294-154">Isso ocorre para imagens compartilhadas na nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="57294-154">This occurs for images shared on the public cloud.</span></span>

### <a name="buttons"></a><span data-ttu-id="57294-155">Botões</span><span class="sxs-lookup"><span data-stu-id="57294-155">Buttons</span></span>

<span data-ttu-id="57294-156">Os botões são mostrados empilhados na parte inferior do cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-156">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="57294-157">O texto do botão está sempre em uma única linha e é truncado se o texto exceder a largura do botão.</span><span class="sxs-lookup"><span data-stu-id="57294-157">Button text is always on a single line and is truncated if the text exceeds the button width.</span></span> <span data-ttu-id="57294-158">Não são mostrados botões adicionais além do número máximo suportado pelo cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-158">Any additional buttons beyond the maximum number supported by the card are not shown.</span></span>

<span data-ttu-id="57294-159">Para obter mais informações, consulte [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="57294-159">For more information, see [card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

### <a name="card-formatting"></a><span data-ttu-id="57294-160">Formatação de cartões</span><span class="sxs-lookup"><span data-stu-id="57294-160">Card formatting</span></span>

<span data-ttu-id="57294-161">Para obter mais informações sobre a formatação de texto em cartões, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="57294-161">For more information on text formatting in cards, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="57294-162">Cartão adaptativo</span><span class="sxs-lookup"><span data-stu-id="57294-162">Adaptive card</span></span>

<span data-ttu-id="57294-163">Uma placa adaptativa é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="57294-163">An adaptive card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="57294-164">Para obter mais informações, consulte [cartões adaptativos v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="57294-164">For more information, see [adaptive cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="57294-165">Suporte para cartões adaptativos</span><span class="sxs-lookup"><span data-stu-id="57294-165">Support for adaptive cards</span></span>

| <span data-ttu-id="57294-166">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-166">Bots in Teams</span></span> | <span data-ttu-id="57294-167">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="57294-167">Messaging extensions</span></span>  | <span data-ttu-id="57294-168">Conectores</span><span class="sxs-lookup"><span data-stu-id="57294-168">Connectors</span></span> | <span data-ttu-id="57294-169">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="57294-169">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="57294-170">✔</span><span class="sxs-lookup"><span data-stu-id="57294-170">✔</span></span> | <span data-ttu-id="57294-171">✔</span><span class="sxs-lookup"><span data-stu-id="57294-171">✔</span></span> | <span data-ttu-id="57294-172">✖</span><span class="sxs-lookup"><span data-stu-id="57294-172">✖</span></span> | <span data-ttu-id="57294-173">✔</span><span class="sxs-lookup"><span data-stu-id="57294-173">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="57294-174">Teams plataforma suporta v1.2 ou anteriores dos recursos de placas adaptativas.</span><span class="sxs-lookup"><span data-stu-id="57294-174">Teams platform supports v1.2 or earlier of adaptive card features.</span></span>
> * <span data-ttu-id="57294-175">Atualmente, os elementos de mídia não são suportados na placa adaptativa v1.2 na plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="57294-175">Media elements are currently not supported in adaptive card v1.2 on the Teams platform.</span></span>

### <a name="example-of-an-adaptive-card"></a><span data-ttu-id="57294-176">Exemplo de cartão adaptativo</span><span class="sxs-lookup"><span data-stu-id="57294-176">Example of an adaptive card</span></span>

![Exemplo de cartão adaptativo](~/assets/images/cards/adaptivecard.png)

```json
{
  "contentType": "application/vnd.microsoft.card.adaptive",
  "content": {
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Publish Adaptive Card schema",
            "weight": "bolder",
            "size": "medium"
          },
          {
            "type": "ColumnSet",
            "columns": [
              {
                "type": "Column",
                "width": "auto",
                "items": [
                  {
                    "type": "Image",
                    "url": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
                    "size": "small",
                    "style": "person"
                  }
                ]
              },
              {
                "type": "Column",
                "width": "stretch",
                "items": [
                  {
                    "type": "TextBlock",
                    "text": "Matt Hidinger",
                    "weight": "bolder",
                    "wrap": true
                  },
                  {
                    "type": "TextBlock",
                    "spacing": "none",
                    "text": "Created {{DATE(2017-02-14T06:08:39Z, SHORT)}}",
                    "isSubtle": true,
                    "wrap": true
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Now that we have defined the main rules and features of the format, we need to produce a schema and publish it to GitHub. The schema will be the starting point of our reference documentation.",
            "wrap": true
          },
          {
            "type": "FactSet",
            "facts": [
              {
                "title": "Board:",
                "value": "Adaptive Card"
              },
              {
                "title": "List:",
                "value": "Backlog"
              },
              {
                "title": "Assigned to:",
                "value": "Matt Hidinger"
              },
              {
                "title": "Due date:",
                "value": "Not set"
              }
            ]
          }
        ]
      }
    ],
    "actions": [
      {
        "type": "Action.ShowCard",
        "title": "Set due date",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Date",
              "id": "dueDate"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      },
      {
        "type": "Action.ShowCard",
        "title": "Comment",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Text",
              "id": "comment",
              "isMultiline": true,
              "placeholder": "Enter your comment"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      }
    ]
  }  
}
```

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="57294-178">Informações adicionais sobre cartões adaptativos</span><span class="sxs-lookup"><span data-stu-id="57294-178">Additional information on adaptive cards</span></span>

<span data-ttu-id="57294-179">Referência do Bot Framework:</span><span class="sxs-lookup"><span data-stu-id="57294-179">Bot Framework reference:</span></span>

* [<span data-ttu-id="57294-180">Cartões adaptativos Node.js</span><span class="sxs-lookup"><span data-stu-id="57294-180">Adaptive cards Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="57294-181">Cartão adaptativo C #</span><span class="sxs-lookup"><span data-stu-id="57294-181">Adaptive card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

## <a name="hero-card"></a><span data-ttu-id="57294-182">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="57294-182">Hero card</span></span>

<span data-ttu-id="57294-183">Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="57294-183">A card that typically contains a single large image, one or more buttons, and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="57294-184">Suporte para cartões de herói</span><span class="sxs-lookup"><span data-stu-id="57294-184">Support for hero cards</span></span>

| <span data-ttu-id="57294-185">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-185">Bots in Teams</span></span> | <span data-ttu-id="57294-186">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="57294-186">Messaging extensions</span></span>  | <span data-ttu-id="57294-187">Conectores</span><span class="sxs-lookup"><span data-stu-id="57294-187">Connectors</span></span> | <span data-ttu-id="57294-188">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="57294-188">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="57294-189">✔</span><span class="sxs-lookup"><span data-stu-id="57294-189">✔</span></span> | <span data-ttu-id="57294-190">✔</span><span class="sxs-lookup"><span data-stu-id="57294-190">✔</span></span> | <span data-ttu-id="57294-191">✖</span><span class="sxs-lookup"><span data-stu-id="57294-191">✖</span></span> | <span data-ttu-id="57294-192">✔</span><span class="sxs-lookup"><span data-stu-id="57294-192">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="57294-193">Propriedades de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="57294-193">Properties of a hero card</span></span>

| <span data-ttu-id="57294-194">Propriedade</span><span class="sxs-lookup"><span data-stu-id="57294-194">Property</span></span> | <span data-ttu-id="57294-195">Tipo</span><span class="sxs-lookup"><span data-stu-id="57294-195">Type</span></span>  | <span data-ttu-id="57294-196">Descrição</span><span class="sxs-lookup"><span data-stu-id="57294-196">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="57294-197">title</span><span class="sxs-lookup"><span data-stu-id="57294-197">title</span></span> | <span data-ttu-id="57294-198">Rich text </span><span class="sxs-lookup"><span data-stu-id="57294-198">Rich text</span></span> | <span data-ttu-id="57294-199">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-199">Title of the card.</span></span> <span data-ttu-id="57294-200">No máximo 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="57294-200">Maximum 2 lines.</span></span> |
| <span data-ttu-id="57294-201">subtítulo</span><span class="sxs-lookup"><span data-stu-id="57294-201">subtitle</span></span> | <span data-ttu-id="57294-202">Rich text </span><span class="sxs-lookup"><span data-stu-id="57294-202">Rich text</span></span> | <span data-ttu-id="57294-203">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-203">Subtitle of the card.</span></span> <span data-ttu-id="57294-204">No máximo 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="57294-204">Maximum 2 lines.</span></span>|
| <span data-ttu-id="57294-205">texto</span><span class="sxs-lookup"><span data-stu-id="57294-205">text</span></span> | <span data-ttu-id="57294-206">Rich text </span><span class="sxs-lookup"><span data-stu-id="57294-206">Rich text</span></span> | <span data-ttu-id="57294-207">O texto aparece na legenda.</span><span class="sxs-lookup"><span data-stu-id="57294-207">Text appears under the subtitle.</span></span> <span data-ttu-id="57294-208">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="57294-208">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="57294-209">Imagens</span><span class="sxs-lookup"><span data-stu-id="57294-209">images</span></span> | <span data-ttu-id="57294-210">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="57294-210">Array of images</span></span> | <span data-ttu-id="57294-211">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-211">Image displayed at the top of the card.</span></span> <span data-ttu-id="57294-212">Proporção 16:9.</span><span class="sxs-lookup"><span data-stu-id="57294-212">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="57294-213">Botões</span><span class="sxs-lookup"><span data-stu-id="57294-213">buttons</span></span> | <span data-ttu-id="57294-214">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="57294-214">Array of action objects</span></span> | <span data-ttu-id="57294-215">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="57294-215">Set of actions applicable to the current card.</span></span> <span data-ttu-id="57294-216">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="57294-216">Maximum 6.</span></span> |
| <span data-ttu-id="57294-217">torneira</span><span class="sxs-lookup"><span data-stu-id="57294-217">tap</span></span> | <span data-ttu-id="57294-218">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="57294-218">Action object</span></span> | <span data-ttu-id="57294-219">Ativado quando o usuário toca no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-219">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="57294-220">Exemplo de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="57294-220">Example of a hero card</span></span>

![Exemplo de um cartão de herói](~/assets/images/cards/hero.png)

```json
{
   "contentType": "application/vnd.microsoft.card.hero",
   "content": {
     "title": "Seattle Center Monorail",
     "subtitle": "Seattle Center Monorail",
     "text": "The Seattle Center Monorail is an elevated train line between Seattle Center (near the Space Needle) and downtown Seattle. It was built for the 1962 World's Fair. Its original two trains, completed in 1961, are still in service.",
     "images": [
       {
         "url":"https://upload.wikimedia.org/wikipedia/commons/thumb/4/49/Seattle_monorail01_2008-02-25.jpg/1024px-Seattle_monorail01_2008-02-25.jpg"
       }
     ],
    "buttons": [
      {
         "type": "openUrl",
         "title": "Official website",
         "value": "https://www.seattlemonorail.com"
       },
      {
        "type": "openUrl",
        "title": "Wikipeda page",
        "value": "https://en.wikipedia.org/wiki/Seattle_Center_Monorail"
       }
     ]
   }
}

```

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="57294-222">Informações adicionais sobre cartões de herói</span><span class="sxs-lookup"><span data-stu-id="57294-222">Additional information on hero cards</span></span>

<span data-ttu-id="57294-223">Referência do Bot Framework:</span><span class="sxs-lookup"><span data-stu-id="57294-223">Bot Framework reference:</span></span>

* [<span data-ttu-id="57294-224">cartão de herói Node.js</span><span class="sxs-lookup"><span data-stu-id="57294-224">Hero card Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="57294-225">Cartão de herói C #</span><span class="sxs-lookup"><span data-stu-id="57294-225">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="57294-226">Cartão de lista</span><span class="sxs-lookup"><span data-stu-id="57294-226">List card</span></span>

<span data-ttu-id="57294-227">O cartão de lista foi adicionado por Teams para fornecer funções além do que a coleção de listas pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="57294-227">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="57294-228">O cartão de lista fornece uma lista de itens de rolagem.</span><span class="sxs-lookup"><span data-stu-id="57294-228">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="57294-229">Suporte para cartões de lista</span><span class="sxs-lookup"><span data-stu-id="57294-229">Support for list cards</span></span>

| <span data-ttu-id="57294-230">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-230">Bots in Teams</span></span> | <span data-ttu-id="57294-231">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="57294-231">Messaging extensions</span></span>  | <span data-ttu-id="57294-232">Conectores</span><span class="sxs-lookup"><span data-stu-id="57294-232">Connectors</span></span> | <span data-ttu-id="57294-233">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="57294-233">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="57294-234">✔</span><span class="sxs-lookup"><span data-stu-id="57294-234">✔</span></span> | <span data-ttu-id="57294-235">✖</span><span class="sxs-lookup"><span data-stu-id="57294-235">✖</span></span> | <span data-ttu-id="57294-236">✖</span><span class="sxs-lookup"><span data-stu-id="57294-236">✖</span></span> |<span data-ttu-id="57294-237">✔</span><span class="sxs-lookup"><span data-stu-id="57294-237">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="57294-238">Propriedades de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="57294-238">Properties of a list card</span></span>

| <span data-ttu-id="57294-239">Propriedade</span><span class="sxs-lookup"><span data-stu-id="57294-239">Property</span></span> | <span data-ttu-id="57294-240">Tipo</span><span class="sxs-lookup"><span data-stu-id="57294-240">Type</span></span>  | <span data-ttu-id="57294-241">Descrição</span><span class="sxs-lookup"><span data-stu-id="57294-241">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="57294-242">title</span><span class="sxs-lookup"><span data-stu-id="57294-242">title</span></span> | <span data-ttu-id="57294-243">Rich text </span><span class="sxs-lookup"><span data-stu-id="57294-243">Rich text</span></span> | <span data-ttu-id="57294-244">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-244">Title of the card.</span></span> <span data-ttu-id="57294-245">No máximo 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="57294-245">Maximum 2 lines.</span></span>|
| <span data-ttu-id="57294-246">itens</span><span class="sxs-lookup"><span data-stu-id="57294-246">items</span></span> | <span data-ttu-id="57294-247">Matriz de itens de lista</span><span class="sxs-lookup"><span data-stu-id="57294-247">Array of list items</span></span> ||
| <span data-ttu-id="57294-248">Botões</span><span class="sxs-lookup"><span data-stu-id="57294-248">buttons</span></span> | <span data-ttu-id="57294-249">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="57294-249">Array of action objects</span></span> | <span data-ttu-id="57294-250">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="57294-250">Set of actions applicable to the current card.</span></span> <span data-ttu-id="57294-251">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="57294-251">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="57294-252">Exemplo de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="57294-252">Example of a list card</span></span>

```json
{
  "contentType": "application/vnd.microsoft.teams.card.list",
  "content": {
    "title": "Card title",
    "items": [
      {
        "type": "file",
        "id": "https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx",
        "title": "Report",
        "subtitle": "teams > new > design",
        "tap": {
          "type": "imBack",
          "value": "editOnline https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx"
        }
      },
      {
        "type": "resultItem",
        "icon": "https://cdn2.iconfinder.com/data/icons/social-icons-33/128/Trello-128.png",
        "title": "Trello title",
        "subtitle": "A Trello subtitle",
        "tap": {
          "type": "openUrl",
          "value": "http://trello.com"
        }
      },
      {
        "type": "section",
        "title": "Manager"
      },
      {
        "type": "person",
        "id": "JohnDoe@contoso.com",
        "title": "John Doe",
        "subtitle": "Manager",
        "tap": {
          "type": "imBack",
          "value": "whois JohnDoe@contoso.com"
        }
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Select",
        "value": "whois"
      }
    ]
  }
}
```

## <a name="office-365-connector-card"></a><span data-ttu-id="57294-253">cartão conector Office 365</span><span class="sxs-lookup"><span data-stu-id="57294-253">Office 365 connector card</span></span>

<span data-ttu-id="57294-254">A placa de conector Office 365 é suportada em Teams, não no Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="57294-254">The Office 365 connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="57294-255">Este cartão fornece um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="57294-255">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="57294-256">Esta placa encapsula uma placa conectora para que possa ser usada por bots.</span><span class="sxs-lookup"><span data-stu-id="57294-256">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="57294-257">Para obter diferenças entre as placas conectoras e a placa O365, consulte [Notas na placa de conector Office 365](#notes-on-the-office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="57294-257">For differences between connector cards and the O365 card, see [Notes on the Office 365 connector card](#notes-on-the-office-365-connector-card).</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="57294-258">Suporte para cartões de conectores Office 365</span><span class="sxs-lookup"><span data-stu-id="57294-258">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="57294-259">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-259">Bots in Teams</span></span> | <span data-ttu-id="57294-260">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="57294-260">Messaging extensions</span></span>  | <span data-ttu-id="57294-261">Conectores</span><span class="sxs-lookup"><span data-stu-id="57294-261">Connectors</span></span> | <span data-ttu-id="57294-262">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="57294-262">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="57294-263">✔</span><span class="sxs-lookup"><span data-stu-id="57294-263">✔</span></span> | <span data-ttu-id="57294-264">✔</span><span class="sxs-lookup"><span data-stu-id="57294-264">✔</span></span> | <span data-ttu-id="57294-265">✔</span><span class="sxs-lookup"><span data-stu-id="57294-265">✔</span></span> | <span data-ttu-id="57294-266">✖</span><span class="sxs-lookup"><span data-stu-id="57294-266">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="57294-267">Propriedades da placa de conector Office 365</span><span class="sxs-lookup"><span data-stu-id="57294-267">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="57294-268">Propriedade</span><span class="sxs-lookup"><span data-stu-id="57294-268">Property</span></span> | <span data-ttu-id="57294-269">Tipo</span><span class="sxs-lookup"><span data-stu-id="57294-269">Type</span></span>  | <span data-ttu-id="57294-270">Descrição</span><span class="sxs-lookup"><span data-stu-id="57294-270">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="57294-271">title</span><span class="sxs-lookup"><span data-stu-id="57294-271">title</span></span> | <span data-ttu-id="57294-272">Rich text </span><span class="sxs-lookup"><span data-stu-id="57294-272">Rich text</span></span> | <span data-ttu-id="57294-273">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-273">Title of the card.</span></span> <span data-ttu-id="57294-274">No máximo 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="57294-274">Maximum 2 lines.</span></span> |
| <span data-ttu-id="57294-275">summary</span><span class="sxs-lookup"><span data-stu-id="57294-275">summary</span></span> | <span data-ttu-id="57294-276">Rich text </span><span class="sxs-lookup"><span data-stu-id="57294-276">Rich text</span></span> | <span data-ttu-id="57294-277">Resumo do cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-277">Summary of the card.</span></span> <span data-ttu-id="57294-278">No máximo 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="57294-278">Maximum 2 lines.</span></span> |
| <span data-ttu-id="57294-279">texto</span><span class="sxs-lookup"><span data-stu-id="57294-279">text</span></span> | <span data-ttu-id="57294-280">Rich text </span><span class="sxs-lookup"><span data-stu-id="57294-280">Rich text</span></span> | <span data-ttu-id="57294-281">O texto aparece na legenda.</span><span class="sxs-lookup"><span data-stu-id="57294-281">Text appears under the subtitle.</span></span> <span data-ttu-id="57294-282">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="57294-282">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="57294-283">themeColor</span><span class="sxs-lookup"><span data-stu-id="57294-283">themeColor</span></span> | <span data-ttu-id="57294-284">Corda HEX</span><span class="sxs-lookup"><span data-stu-id="57294-284">HEX string</span></span> | <span data-ttu-id="57294-285">Cor que substitui o acentoColor fornecido a partir do manifesto de aplicação.</span><span class="sxs-lookup"><span data-stu-id="57294-285">Color that overrides the accentColor provided from the application manifest.</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="57294-286">Notas no cartão de conector Office 365</span><span class="sxs-lookup"><span data-stu-id="57294-286">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="57294-287">Office 365 as placas de conectore funcionam corretamente em Microsoft Teams, incluindo [ações do ActionCard](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="57294-287">Office 365 connector cards function properly in Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="57294-288">Uma diferença importante entre o uso de cartões conectores de um conector e o uso de cartões conectores no seu bot é o manuseio de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-288">One important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="57294-289">Para um conector, o ponto final recebe a carga útil do cartão através do HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="57294-289">For a connector, the endpoint receives the card payload through HTTP POST.</span></span>
* <span data-ttu-id="57294-290">Para um bot, `HttpPOST` a ação desencadeia uma `invoke` atividade que envia apenas o ID de ação e o corpo para o bot.</span><span class="sxs-lookup"><span data-stu-id="57294-290">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="57294-291">Cada placa conectora pode exibir no máximo dez seções, e cada seção pode conter um máximo de cinco imagens e cinco ações.</span><span class="sxs-lookup"><span data-stu-id="57294-291">Each connector card can display a maximum of ten sections, and each section can contain a maximum of five images and five actions.</span></span>

> [!NOTE]
> <span data-ttu-id="57294-292">Não aparecem seções, imagens ou ações adicionais em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="57294-292">Any additional sections, images, or actions in a message do not appear.</span></span>

<span data-ttu-id="57294-293">Todos os campos de texto suportam marcação e HTML.</span><span class="sxs-lookup"><span data-stu-id="57294-293">All text fields support markdown and HTML.</span></span> <span data-ttu-id="57294-294">Você pode controlar quais seções usam marcação ou HTML definindo a `markdown` propriedade em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="57294-294">You can control which sections use markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="57294-295">Por padrão, `markdown` está definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="57294-295">By default, `markdown` is set to `true`.</span></span> <span data-ttu-id="57294-296">Se você quiser usar HTML em vez disso, defina `markdown` para `false` .</span><span class="sxs-lookup"><span data-stu-id="57294-296">If you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="57294-297">Se você especificar a `themeColor` propriedade, ela substitui a `accentColor` propriedade no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="57294-297">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="57294-298">Para especificar o estilo de renderização `activityImage` para , você pode definir o `activityImageType` seguinte:</span><span class="sxs-lookup"><span data-stu-id="57294-298">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows:</span></span>

| <span data-ttu-id="57294-299">Valor</span><span class="sxs-lookup"><span data-stu-id="57294-299">Value</span></span> | <span data-ttu-id="57294-300">Descrição</span><span class="sxs-lookup"><span data-stu-id="57294-300">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="57294-301">Padrão; `activityImage` é cortado como um círculo.</span><span class="sxs-lookup"><span data-stu-id="57294-301">Default; `activityImage` is cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="57294-302">`activityImage` é exibido como um retângulo e mantém sua proporção.</span><span class="sxs-lookup"><span data-stu-id="57294-302">`activityImage` is displayed as a rectangle and retains its aspect ratio.</span></span> |

<span data-ttu-id="57294-303">Para obter todos os outros detalhes sobre as propriedades do cartão conector, consulte [referência acionável do cartão de mensagem](/outlook/actionable-messages/card-reference).</span><span class="sxs-lookup"><span data-stu-id="57294-303">For all other details about connector card properties, see [actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="57294-304">As únicas propriedades de cartão de conector que Microsoft Teams não suportam atualmente são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="57294-304">The only connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="57294-305">`startGroup`sempre tratado como `true` em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-305">`startGroup` always treated as `true` in Teams</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="57294-306">Exemplo de uma placa de conector Office 365</span><span class="sxs-lookup"><span data-stu-id="57294-306">Example of an Office 365 connector card</span></span>

```json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "summary": "John Doe commented on Trello",
    "title": "Project Tango",
    "sections": [
        {
            "activityTitle": "John Doe commented",
            "activitySubtitle": "On Project Tango",
            "activityText": "\"Here are the designs\"",
            "activityImage": "http://connectorsdemo.azurewebsites.net/images/MSC12_Oscar_002.jpg"
        },
        {
            "title": "Details",
            "facts": [
                {
                    "name": "Labels",
                    "value": "Designs, redlines"
                },
                {
                    "name": "Due date",
                    "value": "Dec 7, 2016"
                },
                {
                    "name": "Attachments",
                    "value": "[final.jpg](http://connectorsdemo.azurewebsites.net/images/WIN14_Jan_04.jpg)"
                }
            ]
        },
        {
            "title": "Images",
            "images": [
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/MicrosoftSurface_024_Cafe_OH-06315_VS_R1c.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Scene_01.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Anthony_02.jpg"
                }
            ]
        }
    ],
    "potentialAction": [
        {
            "@context": "http://schema.org",
            "@type": "ViewAction",
            "name": "View in Trello",
            "target": [
                "https://trello.com/c/1101/"
            ]
        }
    ]
  }
}
```

## <a name="receipt-card"></a><span data-ttu-id="57294-307">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="57294-307">Receipt card</span></span>

<span data-ttu-id="57294-308">Teams suporta cartão de recebimento.</span><span class="sxs-lookup"><span data-stu-id="57294-308">Teams supports receipt card.</span></span> <span data-ttu-id="57294-309">É um cartão que permite que um bot forneça um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="57294-309">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="57294-310">Ele normalmente contém a lista de itens a serem incluos no recibo, como impostos e informações totais.</span><span class="sxs-lookup"><span data-stu-id="57294-310">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="57294-311">Suporte para cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="57294-311">Support for receipt cards</span></span>

| <span data-ttu-id="57294-312">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-312">Bots in Teams</span></span> | <span data-ttu-id="57294-313">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="57294-313">Messaging extensions</span></span>  | <span data-ttu-id="57294-314">Conectores</span><span class="sxs-lookup"><span data-stu-id="57294-314">Connectors</span></span> | <span data-ttu-id="57294-315">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="57294-315">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="57294-316">✔</span><span class="sxs-lookup"><span data-stu-id="57294-316">✔</span></span> | <span data-ttu-id="57294-317">✔</span><span class="sxs-lookup"><span data-stu-id="57294-317">✔</span></span> | <span data-ttu-id="57294-318">✖</span><span class="sxs-lookup"><span data-stu-id="57294-318">✖</span></span> | <span data-ttu-id="57294-319">✔</span><span class="sxs-lookup"><span data-stu-id="57294-319">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="57294-320">Exemplo de um cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="57294-320">Example of a receipt card</span></span>

![Exemplo de um cartão de recebimento](~/assets/images/cards/receipt.png)

```json
{
  "contentType": "application/vnd.microsoft.card.receipt",
  "content": {
    "title": "John Doe",
    "facts": [
      {
        "key": "Order Number",
        "value": "1234"
      },
      {
        "key": "Payment Method",
        "value": "VISA 5555-****"
      }
    ],
    "items": [
      {
        "title": "Data Transfer",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/traffic-manager.png"
        },
        "price": "$ 38.45",
        "quantity": "368"
      },
      {
        "title": "App Service",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/cloud-service.png"
        },
        "price": "$ 45.00",
        "quantity": "720"
      }
    ],
    "total": "$ 90.95",
    "tax": "$ 7.50",
    "buttons": [
      {
        "type": "openUrl",
        "title": "More information",
        "image": "https://account.windowsazure.com/content/6.10.1.38-.8225.160809-1618/aux-pre/images/offer-icon-freetrial.png",
        "value": "https://azure.microsoft.com/en-us/pricing/"
      }
    ]
  }
}
```

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="57294-322">Informações adicionais sobre cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="57294-322">Additional information on receipt cards</span></span>

<span data-ttu-id="57294-323">Referência do Bot Framework:</span><span class="sxs-lookup"><span data-stu-id="57294-323">Bot Framework reference:</span></span>

* [<span data-ttu-id="57294-324">Node.jsdo cartão de recebimento </span><span class="sxs-lookup"><span data-stu-id="57294-324">Receipt card Node.js</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="57294-325">Cartão de recebimento C #</span><span class="sxs-lookup"><span data-stu-id="57294-325">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="57294-326">Cartão de sinalização</span><span class="sxs-lookup"><span data-stu-id="57294-326">Signin card</span></span>

<span data-ttu-id="57294-327">O cartão de sinalização permite que um bot solicite que um usuário faça login.</span><span class="sxs-lookup"><span data-stu-id="57294-327">Signin card enables a bot to request a user to sign in.</span></span> <span data-ttu-id="57294-328">Ele é suportado em Teams de forma ligeiramente diferente do encontrado no Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="57294-328">It is supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="57294-329">O cartão de sinalização em Teams é semelhante ao cartão de sinalização no Bot Framework, exceto que o cartão de sinalização em Teams só suporta duas ações: `signin` e `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="57294-329">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="57294-330">A ação signin pode ser usada a partir de qualquer cartão em Teams, não apenas o cartão de sinalização.</span><span class="sxs-lookup"><span data-stu-id="57294-330">The signin action can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="57294-331">Para obter mais informações sobre autenticação, consulte [Microsoft Teams fluxo de autenticação para bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="57294-331">For more information on authentication, see [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="57294-332">Suporte para cartões de sinalização</span><span class="sxs-lookup"><span data-stu-id="57294-332">Support for signin cards</span></span>

| <span data-ttu-id="57294-333">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-333">Bots in Teams</span></span> | <span data-ttu-id="57294-334">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="57294-334">Messaging extensions</span></span>  | <span data-ttu-id="57294-335">Conectores</span><span class="sxs-lookup"><span data-stu-id="57294-335">Connectors</span></span> | <span data-ttu-id="57294-336">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="57294-336">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="57294-337">✔</span><span class="sxs-lookup"><span data-stu-id="57294-337">✔</span></span> | <span data-ttu-id="57294-338">✖</span><span class="sxs-lookup"><span data-stu-id="57294-338">✖</span></span> | <span data-ttu-id="57294-339">✖</span><span class="sxs-lookup"><span data-stu-id="57294-339">✖</span></span> | <span data-ttu-id="57294-340">✔</span><span class="sxs-lookup"><span data-stu-id="57294-340">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="57294-341">Informações adicionais sobre cartões de sinalização</span><span class="sxs-lookup"><span data-stu-id="57294-341">Additional information on signin cards</span></span>

<span data-ttu-id="57294-342">Referência do Bot Framework:</span><span class="sxs-lookup"><span data-stu-id="57294-342">Bot Framework reference:</span></span>

* [<span data-ttu-id="57294-343">Node.jsdo cartão de sinalização </span><span class="sxs-lookup"><span data-stu-id="57294-343">Signin card Node.js</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="57294-344">Cartão de sinalização C #</span><span class="sxs-lookup"><span data-stu-id="57294-344">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="57294-345">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="57294-345">Thumbnail card</span></span>

<span data-ttu-id="57294-346">Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="57294-346">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="57294-347">Suporte para cartões de miniatura</span><span class="sxs-lookup"><span data-stu-id="57294-347">Support for thumbnail cards</span></span>

| <span data-ttu-id="57294-348">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-348">Bots in Teams</span></span> | <span data-ttu-id="57294-349">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="57294-349">Messaging extensions</span></span>  | <span data-ttu-id="57294-350">Conectores</span><span class="sxs-lookup"><span data-stu-id="57294-350">Connectors</span></span> | <span data-ttu-id="57294-351">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="57294-351">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="57294-352">✔</span><span class="sxs-lookup"><span data-stu-id="57294-352">✔</span></span> | <span data-ttu-id="57294-353">✔</span><span class="sxs-lookup"><span data-stu-id="57294-353">✔</span></span> | <span data-ttu-id="57294-354">✖</span><span class="sxs-lookup"><span data-stu-id="57294-354">✖</span></span> | <span data-ttu-id="57294-355">✔</span><span class="sxs-lookup"><span data-stu-id="57294-355">✔</span></span> |

![Exemplo de cartão de miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="57294-357">Propriedades de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="57294-357">Properties of a thumbnail card</span></span>

| <span data-ttu-id="57294-358">Propriedade</span><span class="sxs-lookup"><span data-stu-id="57294-358">Property</span></span> | <span data-ttu-id="57294-359">Tipo</span><span class="sxs-lookup"><span data-stu-id="57294-359">Type</span></span>  | <span data-ttu-id="57294-360">Descrição</span><span class="sxs-lookup"><span data-stu-id="57294-360">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="57294-361">title</span><span class="sxs-lookup"><span data-stu-id="57294-361">title</span></span> | <span data-ttu-id="57294-362">Rich text </span><span class="sxs-lookup"><span data-stu-id="57294-362">Rich text</span></span> | <span data-ttu-id="57294-363">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-363">Title of the card.</span></span> <span data-ttu-id="57294-364">No máximo 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="57294-364">Maximum 2 lines.</span></span>|
| <span data-ttu-id="57294-365">subtítulo</span><span class="sxs-lookup"><span data-stu-id="57294-365">subtitle</span></span> | <span data-ttu-id="57294-366">Rich text </span><span class="sxs-lookup"><span data-stu-id="57294-366">Rich text</span></span> | <span data-ttu-id="57294-367">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-367">Subtitle of the card.</span></span> <span data-ttu-id="57294-368">No máximo 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="57294-368">Maximum 2 lines.</span></span>|
| <span data-ttu-id="57294-369">texto</span><span class="sxs-lookup"><span data-stu-id="57294-369">text</span></span> | <span data-ttu-id="57294-370">Rich text </span><span class="sxs-lookup"><span data-stu-id="57294-370">Rich text</span></span> | <span data-ttu-id="57294-371">O texto aparece na legenda.</span><span class="sxs-lookup"><span data-stu-id="57294-371">Text appears under the subtitle.</span></span> <span data-ttu-id="57294-372">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="57294-372">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="57294-373">Imagens</span><span class="sxs-lookup"><span data-stu-id="57294-373">images</span></span> | <span data-ttu-id="57294-374">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="57294-374">Array of images</span></span> | <span data-ttu-id="57294-375">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-375">Image displayed at the top of the card.</span></span> <span data-ttu-id="57294-376">Proporção 1:1 quadrado.</span><span class="sxs-lookup"><span data-stu-id="57294-376">Aspect ratio 1:1 square.</span></span> |
| <span data-ttu-id="57294-377">Botões</span><span class="sxs-lookup"><span data-stu-id="57294-377">buttons</span></span> | <span data-ttu-id="57294-378">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="57294-378">Array of action objects</span></span> | <span data-ttu-id="57294-379">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="57294-379">Set of actions applicable to the current card.</span></span> <span data-ttu-id="57294-380">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="57294-380">Maximum 6.</span></span> |
| <span data-ttu-id="57294-381">torneira</span><span class="sxs-lookup"><span data-stu-id="57294-381">tap</span></span> | <span data-ttu-id="57294-382">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="57294-382">Action object</span></span> | <span data-ttu-id="57294-383">Ativado quando o usuário toca no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="57294-383">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="57294-384">Exemplo de cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="57294-384">Example of a thumbnail card</span></span>

```json
{
  "contentType": "application/vnd.microsoft.card.thumbnail",
  "content": {
    "title": "Bender",
    "subtitle": "tale of a robot who dared to love",
    "text": "Bender Bending Rodríguez is a main character in the animated television series Futurama. He was created by series creators Matt Groening and David X. Cohen, and is voiced by John DiMaggio",
    "images": [
      {
        "url": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
        "alt": "Bender Rodríguez"
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Thumbs Up",
        "image": "http://moopz.com/assets_c/2012/06/emoji-thumbs-up-150-thumb-autox125-140616.jpg",
        "value": "I like it"
      },
      {
        "type": "imBack",
        "title": "Thumbs Down",
        "image": "http://yourfaceisstupid.com/wp-content/uploads/2014/08/thumbs-down.png",
        "value": "I don't like it"
      },
      {
        "type": "openUrl",
        "title": "I feel lucky",
        "image": "http://thumb9.shutterstock.com/photos/thumb_large/683806/148441982.jpg",
        "value": "https://www.bing.com/images/search?q=bender&qpvt=bender&qpvt=bender&qpvt=bender&FORM=IGRE"
      }
    ],
    "tap": {
      "type": "imBack",
      "value": "Tapped it!"
    }
  }
}
```

### <a name="additional-information"></a><span data-ttu-id="57294-385">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="57294-385">Additional information</span></span>

<span data-ttu-id="57294-386">Referência do Bot Framework:</span><span class="sxs-lookup"><span data-stu-id="57294-386">Bot Framework reference:</span></span>

* [<span data-ttu-id="57294-387">cartão de miniatura Node.js</span><span class="sxs-lookup"><span data-stu-id="57294-387">Thumbnail card Node.js</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="57294-388">Cartão de miniatura C #</span><span class="sxs-lookup"><span data-stu-id="57294-388">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="57294-389">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="57294-389">Card collections</span></span>

<span data-ttu-id="57294-390">Teams suporta coleções de cartões.</span><span class="sxs-lookup"><span data-stu-id="57294-390">Teams supports Card collections.</span></span>

<span data-ttu-id="57294-391">As coleções de cartões incluem `builder.AttachmentLayout.carousel` e `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="57294-391">Card collections include `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="57294-392">Essas coleções contêm cartões adaptativos, heróis ou miniaturas.</span><span class="sxs-lookup"><span data-stu-id="57294-392">These collections contain adaptive, hero, or thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="57294-393">Coleção carrossel</span><span class="sxs-lookup"><span data-stu-id="57294-393">Carousel collection</span></span>

<span data-ttu-id="57294-394">O [layout do carrossel](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="57294-394">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="57294-395">Suporte para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="57294-395">Support for carousel collections</span></span>

| <span data-ttu-id="57294-396">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-396">Bots in Teams</span></span> | <span data-ttu-id="57294-397">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="57294-397">Messaging extensions</span></span>  | <span data-ttu-id="57294-398">Conectores</span><span class="sxs-lookup"><span data-stu-id="57294-398">Connectors</span></span> | <span data-ttu-id="57294-399">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="57294-399">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="57294-400">✔</span><span class="sxs-lookup"><span data-stu-id="57294-400">✔</span></span> | <span data-ttu-id="57294-401">✖</span><span class="sxs-lookup"><span data-stu-id="57294-401">✖</span></span> | <span data-ttu-id="57294-402">✖</span><span class="sxs-lookup"><span data-stu-id="57294-402">✖</span></span> | <span data-ttu-id="57294-403">✔</span><span class="sxs-lookup"><span data-stu-id="57294-403">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="57294-404">Um carrossel pode exibir no máximo dez cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="57294-404">A carousel can display a maximum of ten cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="57294-405">Propriedades de um cartão de carrossel</span><span class="sxs-lookup"><span data-stu-id="57294-405">Properties of a carousel card</span></span>

<span data-ttu-id="57294-406">As propriedades de um cartão de carrossel são as mesmas do herói e cartões de miniatura.</span><span class="sxs-lookup"><span data-stu-id="57294-406">Properties of a carousel card are same as those of the hero and thumbnail cards.</span></span>

### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="57294-407">Exemplo de coleção de carrossel</span><span class="sxs-lookup"><span data-stu-id="57294-407">Example of a carousel collection</span></span>

![Exemplo de um carrossel de cartões](~/assets/images/cards/carousel.png)

```json
{
 "attachmentLayout": "carousel",
 "attachments":[
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "extraLarge",
                "weight": "bolder",
                "text": "Welcome to Employee Connect",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "size": "medium",
                "weight": "bolder",
                "text": "Add events to your calendar",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "The bot can send \r\rnotification to remind \r\ryou about the latest \r\revents and trainings.",
                "wrap": true,
                "height": "stretch"
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.2",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee connect"
              },
              {
                "type": "TextBlock",
                "text": "The bot can send notifications \r\rto remind you about the latest \r\r events and trainings",
                "wrap": true,
                "maxWidth": 2
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee Connect final"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Create and manage your tasks",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "text": "The app identifies all your pending tasks \r\r and helps you manage everything at \r\r one place.",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Try these commands \r\r- Pending Submissions \r\r- Pending Approvals- My Tools",
                "wrap": true,
                "height": "stretch"
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    }
  ]
}
```

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="57294-409">Sintaxe para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="57294-409">Syntax for carousel collections</span></span>

<span data-ttu-id="57294-410">`builder.AttachmentLayoutTypes.Carousel` é a sintaxe para coleções de carrossel.</span><span class="sxs-lookup"><span data-stu-id="57294-410">`builder.AttachmentLayoutTypes.Carousel` is the syntax for carousel collections.</span></span>

## <a name="list-collection"></a><span data-ttu-id="57294-411">Coleção de listas</span><span class="sxs-lookup"><span data-stu-id="57294-411">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="57294-412">Suporte para coleções de listas</span><span class="sxs-lookup"><span data-stu-id="57294-412">Support for list collections</span></span>

<span data-ttu-id="57294-413">O layout da lista mostra uma lista de cartões empilhadas verticalmente, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="57294-413">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="57294-414">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-414">Bots in Teams</span></span> | <span data-ttu-id="57294-415">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="57294-415">Messaging extensions</span></span>  | <span data-ttu-id="57294-416">Conectores</span><span class="sxs-lookup"><span data-stu-id="57294-416">Connectors</span></span> | <span data-ttu-id="57294-417">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="57294-417">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="57294-418">✔</span><span class="sxs-lookup"><span data-stu-id="57294-418">✔</span></span> | <span data-ttu-id="57294-419">✔</span><span class="sxs-lookup"><span data-stu-id="57294-419">✔</span></span> | <span data-ttu-id="57294-420">✖</span><span class="sxs-lookup"><span data-stu-id="57294-420">✖</span></span> | <span data-ttu-id="57294-421">✔</span><span class="sxs-lookup"><span data-stu-id="57294-421">✔</span></span> |

### <a name="example-of-a-list-collection"></a><span data-ttu-id="57294-422">Exemplo de uma coleção de listas</span><span class="sxs-lookup"><span data-stu-id="57294-422">Example of a list collection</span></span>

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

<span data-ttu-id="57294-424">As propriedades são as mesmas do herói ou da miniatura.</span><span class="sxs-lookup"><span data-stu-id="57294-424">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="57294-425">Uma lista pode exibir no máximo dez cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="57294-425">A list can display a maximum of ten cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="57294-426">Algumas combinações de cartões de lista ainda não são suportadas no iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="57294-426">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="57294-427">Sintaxe para coleções de listas</span><span class="sxs-lookup"><span data-stu-id="57294-427">Syntax for list collections</span></span>

<span data-ttu-id="57294-428">`builder.AttachmentLayout.list` é a sintaxe para coleções de listas.</span><span class="sxs-lookup"><span data-stu-id="57294-428">`builder.AttachmentLayout.list` is the syntax for list collections.</span></span>

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="57294-429">Cartões não suportados em Teams</span><span class="sxs-lookup"><span data-stu-id="57294-429">Cards not supported in Teams</span></span>

<span data-ttu-id="57294-430">Os seguintes cartões são implementados pelo Bot Framework, mas não são suportados por Teams:</span><span class="sxs-lookup"><span data-stu-id="57294-430">The following cards are implemented by the Bot Framework, but are not supported by Teams:</span></span>

* <span data-ttu-id="57294-431">Cartões de animação</span><span class="sxs-lookup"><span data-stu-id="57294-431">Animation cards</span></span>
* <span data-ttu-id="57294-432">Cartões de áudio</span><span class="sxs-lookup"><span data-stu-id="57294-432">Audio cards</span></span>
* <span data-ttu-id="57294-433">Cartões de vídeo</span><span class="sxs-lookup"><span data-stu-id="57294-433">Video cards</span></span>
