---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Teams
localization_priority: Normal
keywords: referência de cartões bots
ms.topic: reference
ms.openlocfilehash: cab7f1659759f40beb1aba59531ee6c1a84662c1
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566856"
---
# <a name="cards-reference"></a><span data-ttu-id="5e535-104">Referência de cartões</span><span class="sxs-lookup"><span data-stu-id="5e535-104">Cards reference</span></span>

<span data-ttu-id="5e535-105">Os cartões listados neste documento são suportados em bots para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="5e535-105">The cards listed in this document are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="5e535-106">Eles são baseados em cartões definidos pela Estrutura de Bot, mas Teams não suporta todos os cartões da Estrutura de Bot e, em vez disso, alguns cartões Teams foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="5e535-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and instead some Teams cards have been added.</span></span> <span data-ttu-id="5e535-107">As diferenças são chamadas nas referências neste documento.</span><span class="sxs-lookup"><span data-stu-id="5e535-107">Differences are called out in the references in this document.</span></span>

## <a name="card-examples"></a><span data-ttu-id="5e535-108">Exemplos de cartão</span><span class="sxs-lookup"><span data-stu-id="5e535-108">Card examples</span></span>

<span data-ttu-id="5e535-109">Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do Construtor de Bots v3.</span><span class="sxs-lookup"><span data-stu-id="5e535-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK v3.</span></span> <span data-ttu-id="5e535-110">Exemplos de código também estão disponíveis no repositório Microsoft/BotBuilder-Samples no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5e535-110">Code samples are also available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="5e535-111">.NET</span><span class="sxs-lookup"><span data-stu-id="5e535-111">.NET</span></span>
  * <span data-ttu-id="5e535-112">[Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="5e535-112">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="5e535-113">[Código de exemplo de cartões Construtor de bots v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="5e535-113">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span></span>

* <span data-ttu-id="5e535-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="5e535-114">Node.js</span></span>
  * <span data-ttu-id="5e535-115">[Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="5e535-115">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="5e535-116">[Código de exemplo de cartões Construtor de bots v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="5e535-116">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span></span>

## <a name="types-of-cards"></a><span data-ttu-id="5e535-117">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="5e535-117">Types of cards</span></span>

<span data-ttu-id="5e535-118">Esta tabela mostra os tipos de cartões disponíveis para você:</span><span class="sxs-lookup"><span data-stu-id="5e535-118">This table shows the types of cards available to you:</span></span>

| <span data-ttu-id="5e535-119">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="5e535-119">Card type</span></span> | <span data-ttu-id="5e535-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e535-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="5e535-121">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="5e535-121">Adaptive card</span></span>](#adaptive-card) | <span data-ttu-id="5e535-122">Esse cartão é um cartão altamente personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="5e535-122">This card is highly customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> |
| [<span data-ttu-id="5e535-123">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="5e535-123">Hero card</span></span>](#hero-card) | <span data-ttu-id="5e535-124">Esse cartão normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="5e535-124">This card typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="5e535-125">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="5e535-125">List card</span></span>](#list-card) | <span data-ttu-id="5e535-126">Este cartão é uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="5e535-126">This card is a scrolling list of items.</span></span> |
| [<span data-ttu-id="5e535-127">Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="5e535-127">Office 365 connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="5e535-128">Esse cartão tem um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="5e535-128">This card has a flexible layout with multiple sections, fields, images, and actions.</span></span> |
| [<span data-ttu-id="5e535-129">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="5e535-129">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="5e535-130">Este cartão fornece um recibo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="5e535-130">This card provides a receipt to the user.</span></span> |
| [<span data-ttu-id="5e535-131">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="5e535-131">Signin card</span></span>](#signin-card) | <span data-ttu-id="5e535-132">Esse cartão permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="5e535-132">This card enables a bot to request that a user signs in.</span></span> |
| [<span data-ttu-id="5e535-133">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="5e535-133">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="5e535-134">Esse cartão normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões.</span><span class="sxs-lookup"><span data-stu-id="5e535-134">This card typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="5e535-135">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="5e535-135">Card collections</span></span>](#card-collections) | <span data-ttu-id="5e535-136">Esses cartões são usados para retornar vários itens em uma única resposta.</span><span class="sxs-lookup"><span data-stu-id="5e535-136">This cards is used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="5e535-137">Propriedades comuns para todos os cartões</span><span class="sxs-lookup"><span data-stu-id="5e535-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="5e535-138">Imagens de cartão em linha</span><span class="sxs-lookup"><span data-stu-id="5e535-138">Inline card images</span></span>

<span data-ttu-id="5e535-139">O cartão pode conter uma imagem em linha incluindo um link para a imagem disponível publicamente.</span><span class="sxs-lookup"><span data-stu-id="5e535-139">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="5e535-140">Para fins de desempenho, é altamente recomendável hospedar a imagem em uma rede pública de distribuição de conteúdo (CDN).</span><span class="sxs-lookup"><span data-stu-id="5e535-140">For performance purposes, it is highly recommended you host the image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="5e535-141">As imagens são dimensionados para cima ou para baixo em tamanho, mantendo a proporção para cobrir a área da imagem.</span><span class="sxs-lookup"><span data-stu-id="5e535-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area.</span></span> <span data-ttu-id="5e535-142">Em seguida, as imagens são cortadas do centro para atingir a proporção apropriada para o cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-142">Images are then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="5e535-143">As imagens devem ter, no máximo, 1024×1024, no formato PNG, JPEG ou GIF e não suportam GIF animado.</span><span class="sxs-lookup"><span data-stu-id="5e535-143">Images must be at most 1024×1024, in PNG, JPEG, or GIF format, and do not support animated GIF.</span></span>

| <span data-ttu-id="5e535-144">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5e535-144">Property</span></span> | <span data-ttu-id="5e535-145">Tipo</span><span class="sxs-lookup"><span data-stu-id="5e535-145">Type</span></span>  | <span data-ttu-id="5e535-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e535-146">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="5e535-147">url</span><span class="sxs-lookup"><span data-stu-id="5e535-147">url</span></span> | <span data-ttu-id="5e535-148">URL</span><span class="sxs-lookup"><span data-stu-id="5e535-148">URL</span></span> | <span data-ttu-id="5e535-149">URL HTTPS para a imagem.</span><span class="sxs-lookup"><span data-stu-id="5e535-149">HTTPS URL to the image.</span></span> |
| <span data-ttu-id="5e535-150">alt</span><span class="sxs-lookup"><span data-stu-id="5e535-150">alt</span></span> | <span data-ttu-id="5e535-151">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="5e535-151">String</span></span> | <span data-ttu-id="5e535-152">Descrição acessível da imagem.</span><span class="sxs-lookup"><span data-stu-id="5e535-152">Accessible description of the image.</span></span> |

> [!NOTE]
> <span data-ttu-id="5e535-153">Se um cartão incluir uma URL de imagem que passa por um redirecionamento antes da imagem final, não há suporte para o redirecionamento na URL da imagem.</span><span class="sxs-lookup"><span data-stu-id="5e535-153">If a card includes an image URL that goes through a redirect before the final image, the redirect in image URL is not supported.</span></span> <span data-ttu-id="5e535-154">Isso ocorre para imagens compartilhadas na nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="5e535-154">This occurs for images shared on the public cloud.</span></span>

### <a name="buttons"></a><span data-ttu-id="5e535-155">Botões</span><span class="sxs-lookup"><span data-stu-id="5e535-155">Buttons</span></span>

<span data-ttu-id="5e535-156">Os botões são mostrados empilhados na parte inferior do cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-156">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="5e535-157">O texto do botão está sempre em uma única linha e é truncado se o texto exceder a largura do botão.</span><span class="sxs-lookup"><span data-stu-id="5e535-157">Button text is always on a single line and is truncated if the text exceeds the button width.</span></span> <span data-ttu-id="5e535-158">Quaisquer botões adicionais além do número máximo suportado pelo cartão não são mostrados.</span><span class="sxs-lookup"><span data-stu-id="5e535-158">Any additional buttons beyond the maximum number supported by the card are not shown.</span></span>

<span data-ttu-id="5e535-159">Para obter mais informações, consulte [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="5e535-159">For more information, see [card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

### <a name="card-formatting"></a><span data-ttu-id="5e535-160">Formatação de cartão</span><span class="sxs-lookup"><span data-stu-id="5e535-160">Card formatting</span></span>

<span data-ttu-id="5e535-161">Para obter mais informações sobre formatação de texto em cartões, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="5e535-161">For more information on text formatting in cards, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="5e535-162">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="5e535-162">Adaptive card</span></span>

<span data-ttu-id="5e535-163">Um cartão adaptável é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="5e535-163">An adaptive card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="5e535-164">Para obter mais informações, [consulte cartões adaptáveis v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="5e535-164">For more information, see [adaptive cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="5e535-165">Suporte para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="5e535-165">Support for adaptive cards</span></span>

| <span data-ttu-id="5e535-166">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-166">Bots in Teams</span></span> | <span data-ttu-id="5e535-167">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="5e535-167">Messaging extensions</span></span>  | <span data-ttu-id="5e535-168">Conectores</span><span class="sxs-lookup"><span data-stu-id="5e535-168">Connectors</span></span> | <span data-ttu-id="5e535-169">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="5e535-169">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="5e535-170">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-170">✔</span></span> | <span data-ttu-id="5e535-171">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-171">✔</span></span> | <span data-ttu-id="5e535-172">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-172">✖</span></span> | <span data-ttu-id="5e535-173">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-173">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="5e535-174">Teams plataforma suporta v1.2 ou anterior de recursos de cartão adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="5e535-174">Teams platform supports v1.2 or earlier of adaptive card features.</span></span>
> * <span data-ttu-id="5e535-175">Atualmente, os elementos de mídia não têm suporte no cartão adaptável v1.2 na plataforma Teams adaptável.</span><span class="sxs-lookup"><span data-stu-id="5e535-175">Media elements are currently not supported in adaptive card v1.2 on the Teams platform.</span></span>

### <a name="example-of-an-adaptive-card"></a><span data-ttu-id="5e535-176">Exemplo de um cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="5e535-176">Example of an adaptive card</span></span>

![Exemplo de um cartão adaptável](~/assets/images/cards/adaptivecard.png)

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

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="5e535-178">Informações adicionais sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="5e535-178">Additional information on adaptive cards</span></span>

<span data-ttu-id="5e535-179">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="5e535-179">Bot Framework reference:</span></span>

* [<span data-ttu-id="5e535-180">Cartões adaptáveis Node.js</span><span class="sxs-lookup"><span data-stu-id="5e535-180">Adaptive cards Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="5e535-181">Cartão adaptável C #</span><span class="sxs-lookup"><span data-stu-id="5e535-181">Adaptive card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

## <a name="hero-card"></a><span data-ttu-id="5e535-182">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="5e535-182">Hero card</span></span>

<span data-ttu-id="5e535-183">Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="5e535-183">A card that typically contains a single large image, one or more buttons, and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="5e535-184">Suporte para cartões de herói</span><span class="sxs-lookup"><span data-stu-id="5e535-184">Support for hero cards</span></span>

| <span data-ttu-id="5e535-185">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-185">Bots in Teams</span></span> | <span data-ttu-id="5e535-186">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="5e535-186">Messaging extensions</span></span>  | <span data-ttu-id="5e535-187">Conectores</span><span class="sxs-lookup"><span data-stu-id="5e535-187">Connectors</span></span> | <span data-ttu-id="5e535-188">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="5e535-188">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="5e535-189">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-189">✔</span></span> | <span data-ttu-id="5e535-190">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-190">✔</span></span> | <span data-ttu-id="5e535-191">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-191">✖</span></span> | <span data-ttu-id="5e535-192">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-192">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="5e535-193">Propriedades de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="5e535-193">Properties of a hero card</span></span>

| <span data-ttu-id="5e535-194">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5e535-194">Property</span></span> | <span data-ttu-id="5e535-195">Tipo</span><span class="sxs-lookup"><span data-stu-id="5e535-195">Type</span></span>  | <span data-ttu-id="5e535-196">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e535-196">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="5e535-197">title</span><span class="sxs-lookup"><span data-stu-id="5e535-197">title</span></span> | <span data-ttu-id="5e535-198">Rich text </span><span class="sxs-lookup"><span data-stu-id="5e535-198">Rich text</span></span> | <span data-ttu-id="5e535-199">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-199">Title of the card.</span></span> <span data-ttu-id="5e535-200">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="5e535-200">Maximum 2 lines.</span></span> |
| <span data-ttu-id="5e535-201">subtitle</span><span class="sxs-lookup"><span data-stu-id="5e535-201">subtitle</span></span> | <span data-ttu-id="5e535-202">Rich text </span><span class="sxs-lookup"><span data-stu-id="5e535-202">Rich text</span></span> | <span data-ttu-id="5e535-203">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-203">Subtitle of the card.</span></span> <span data-ttu-id="5e535-204">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="5e535-204">Maximum 2 lines.</span></span>|
| <span data-ttu-id="5e535-205">texto</span><span class="sxs-lookup"><span data-stu-id="5e535-205">text</span></span> | <span data-ttu-id="5e535-206">Rich text </span><span class="sxs-lookup"><span data-stu-id="5e535-206">Rich text</span></span> | <span data-ttu-id="5e535-207">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="5e535-207">Text appears under the subtitle.</span></span> <span data-ttu-id="5e535-208">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="5e535-208">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="5e535-209">images</span><span class="sxs-lookup"><span data-stu-id="5e535-209">images</span></span> | <span data-ttu-id="5e535-210">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="5e535-210">Array of images</span></span> | <span data-ttu-id="5e535-211">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-211">Image displayed at the top of the card.</span></span> <span data-ttu-id="5e535-212">Taxa de proporção 16:9.</span><span class="sxs-lookup"><span data-stu-id="5e535-212">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="5e535-213">botões</span><span class="sxs-lookup"><span data-stu-id="5e535-213">buttons</span></span> | <span data-ttu-id="5e535-214">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="5e535-214">Array of action objects</span></span> | <span data-ttu-id="5e535-215">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="5e535-215">Set of actions applicable to the current card.</span></span> <span data-ttu-id="5e535-216">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="5e535-216">Maximum 6.</span></span> |
| <span data-ttu-id="5e535-217">tap</span><span class="sxs-lookup"><span data-stu-id="5e535-217">tap</span></span> | <span data-ttu-id="5e535-218">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="5e535-218">Action object</span></span> | <span data-ttu-id="5e535-219">Ativado quando o usuário toca no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-219">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="5e535-220">Exemplo de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="5e535-220">Example of a hero card</span></span>

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

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="5e535-222">Informações adicionais sobre cartões de herói</span><span class="sxs-lookup"><span data-stu-id="5e535-222">Additional information on hero cards</span></span>

<span data-ttu-id="5e535-223">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="5e535-223">Bot Framework reference:</span></span>

* [<span data-ttu-id="5e535-224">Cartão de herói Node.js</span><span class="sxs-lookup"><span data-stu-id="5e535-224">Hero card Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="5e535-225">Cartão de herói C #</span><span class="sxs-lookup"><span data-stu-id="5e535-225">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="5e535-226">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="5e535-226">List card</span></span>

<span data-ttu-id="5e535-227">O cartão de lista foi adicionado por Teams para fornecer funções além do que a coleção de listas pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="5e535-227">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="5e535-228">O cartão de listagem fornece uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="5e535-228">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="5e535-229">Suporte para cartões de lista</span><span class="sxs-lookup"><span data-stu-id="5e535-229">Support for list cards</span></span>

| <span data-ttu-id="5e535-230">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-230">Bots in Teams</span></span> | <span data-ttu-id="5e535-231">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="5e535-231">Messaging extensions</span></span>  | <span data-ttu-id="5e535-232">Conectores</span><span class="sxs-lookup"><span data-stu-id="5e535-232">Connectors</span></span> | <span data-ttu-id="5e535-233">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="5e535-233">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="5e535-234">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-234">✔</span></span> | <span data-ttu-id="5e535-235">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-235">✖</span></span> | <span data-ttu-id="5e535-236">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-236">✖</span></span> |<span data-ttu-id="5e535-237">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-237">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="5e535-238">Propriedades de um cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="5e535-238">Properties of a list card</span></span>

| <span data-ttu-id="5e535-239">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5e535-239">Property</span></span> | <span data-ttu-id="5e535-240">Tipo</span><span class="sxs-lookup"><span data-stu-id="5e535-240">Type</span></span>  | <span data-ttu-id="5e535-241">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e535-241">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="5e535-242">title</span><span class="sxs-lookup"><span data-stu-id="5e535-242">title</span></span> | <span data-ttu-id="5e535-243">Rich text </span><span class="sxs-lookup"><span data-stu-id="5e535-243">Rich text</span></span> | <span data-ttu-id="5e535-244">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-244">Title of the card.</span></span> <span data-ttu-id="5e535-245">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="5e535-245">Maximum 2 lines.</span></span>|
| <span data-ttu-id="5e535-246">itens</span><span class="sxs-lookup"><span data-stu-id="5e535-246">items</span></span> | <span data-ttu-id="5e535-247">Matriz de itens de lista</span><span class="sxs-lookup"><span data-stu-id="5e535-247">Array of list items</span></span> ||
| <span data-ttu-id="5e535-248">botões</span><span class="sxs-lookup"><span data-stu-id="5e535-248">buttons</span></span> | <span data-ttu-id="5e535-249">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="5e535-249">Array of action objects</span></span> | <span data-ttu-id="5e535-250">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="5e535-250">Set of actions applicable to the current card.</span></span> <span data-ttu-id="5e535-251">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="5e535-251">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="5e535-252">Exemplo de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="5e535-252">Example of a list card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="5e535-253">Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="5e535-253">Office 365 connector card</span></span>

<span data-ttu-id="5e535-254">O Office 365 conector de usuário é compatível com Teams, não na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="5e535-254">The Office 365 connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="5e535-255">Este cartão fornece um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="5e535-255">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="5e535-256">Esse cartão encapsula um cartão de conector para que ele possa ser usado por bots.</span><span class="sxs-lookup"><span data-stu-id="5e535-256">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="5e535-257">Para diferenças entre cartões de conector e o cartão O365, consulte [Notes on the Office 365 connector card](#notes-on-the-office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="5e535-257">For differences between connector cards and the O365 card, see [Notes on the Office 365 connector card](#notes-on-the-office-365-connector-card).</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="5e535-258">Suporte para cartões Office 365 conectores</span><span class="sxs-lookup"><span data-stu-id="5e535-258">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="5e535-259">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-259">Bots in Teams</span></span> | <span data-ttu-id="5e535-260">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="5e535-260">Messaging extensions</span></span>  | <span data-ttu-id="5e535-261">Conectores</span><span class="sxs-lookup"><span data-stu-id="5e535-261">Connectors</span></span> | <span data-ttu-id="5e535-262">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="5e535-262">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="5e535-263">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-263">✔</span></span> | <span data-ttu-id="5e535-264">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-264">✔</span></span> | <span data-ttu-id="5e535-265">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-265">✔</span></span> | <span data-ttu-id="5e535-266">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-266">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="5e535-267">Propriedades do cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="5e535-267">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="5e535-268">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5e535-268">Property</span></span> | <span data-ttu-id="5e535-269">Tipo</span><span class="sxs-lookup"><span data-stu-id="5e535-269">Type</span></span>  | <span data-ttu-id="5e535-270">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e535-270">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="5e535-271">title</span><span class="sxs-lookup"><span data-stu-id="5e535-271">title</span></span> | <span data-ttu-id="5e535-272">Rich text </span><span class="sxs-lookup"><span data-stu-id="5e535-272">Rich text</span></span> | <span data-ttu-id="5e535-273">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-273">Title of the card.</span></span> <span data-ttu-id="5e535-274">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="5e535-274">Maximum 2 lines.</span></span> |
| <span data-ttu-id="5e535-275">summary</span><span class="sxs-lookup"><span data-stu-id="5e535-275">summary</span></span> | <span data-ttu-id="5e535-276">Rich text </span><span class="sxs-lookup"><span data-stu-id="5e535-276">Rich text</span></span> | <span data-ttu-id="5e535-277">Resumo do cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-277">Summary of the card.</span></span> <span data-ttu-id="5e535-278">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="5e535-278">Maximum 2 lines.</span></span> |
| <span data-ttu-id="5e535-279">texto</span><span class="sxs-lookup"><span data-stu-id="5e535-279">text</span></span> | <span data-ttu-id="5e535-280">Rich text </span><span class="sxs-lookup"><span data-stu-id="5e535-280">Rich text</span></span> | <span data-ttu-id="5e535-281">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="5e535-281">Text appears under the subtitle.</span></span> <span data-ttu-id="5e535-282">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="5e535-282">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="5e535-283">themeColor</span><span class="sxs-lookup"><span data-stu-id="5e535-283">themeColor</span></span> | <span data-ttu-id="5e535-284">Cadeia de caracteres HEX</span><span class="sxs-lookup"><span data-stu-id="5e535-284">HEX string</span></span> | <span data-ttu-id="5e535-285">Cor que substitui o accentColor fornecido do manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e535-285">Color that overrides the accentColor provided from the application manifest.</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="5e535-286">Observações no cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="5e535-286">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="5e535-287">Office 365 conectores funcionam corretamente no Microsoft Teams, incluindo [ações actionCard](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="5e535-287">Office 365 connector cards function properly in Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="5e535-288">Uma diferença importante entre o uso de cartões conectores de um conector e o uso de cartões de conector no bot é o tratamento de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-288">One important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="5e535-289">Para um conector, o ponto de extremidade recebe a carga de cartão por meio de HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="5e535-289">For a connector, the endpoint receives the card payload through HTTP POST.</span></span>
* <span data-ttu-id="5e535-290">Para um bot, a ação dispara uma atividade que envia apenas a ID de ação `HttpPOST` e o corpo para o `invoke` bot.</span><span class="sxs-lookup"><span data-stu-id="5e535-290">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="5e535-291">Cada cartão de conector pode exibir no máximo dez seções, e cada seção pode conter no máximo cinco imagens e cinco ações.</span><span class="sxs-lookup"><span data-stu-id="5e535-291">Each connector card can display a maximum of ten sections, and each section can contain a maximum of five images and five actions.</span></span>

> [!NOTE]
> <span data-ttu-id="5e535-292">Quaisquer seções, imagens ou ações adicionais em uma mensagem não são exibidas.</span><span class="sxs-lookup"><span data-stu-id="5e535-292">Any additional sections, images, or actions in a message do not appear.</span></span>

<span data-ttu-id="5e535-293">Todos os campos de texto suportam marcação e HTML.</span><span class="sxs-lookup"><span data-stu-id="5e535-293">All text fields support markdown and HTML.</span></span> <span data-ttu-id="5e535-294">Você pode controlar quais seções usam markdown ou HTML definindo `markdown` a propriedade em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="5e535-294">You can control which sections use markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="5e535-295">Por padrão, `markdown` é definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="5e535-295">By default, `markdown` is set to `true`.</span></span> <span data-ttu-id="5e535-296">Se você quiser usar HTML em vez disso, de definir `markdown` como `false` .</span><span class="sxs-lookup"><span data-stu-id="5e535-296">If you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="5e535-297">Se você especificar a `themeColor` propriedade, ela substituirá `accentColor` a propriedade no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e535-297">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="5e535-298">Para especificar o estilo de renderização `activityImage` para , você pode definir da seguinte `activityImageType` forma:</span><span class="sxs-lookup"><span data-stu-id="5e535-298">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows:</span></span>

| <span data-ttu-id="5e535-299">Valor</span><span class="sxs-lookup"><span data-stu-id="5e535-299">Value</span></span> | <span data-ttu-id="5e535-300">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e535-300">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="5e535-301">Padrão; `activityImage` é cortada como um círculo.</span><span class="sxs-lookup"><span data-stu-id="5e535-301">Default; `activityImage` is cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="5e535-302">`activityImage` é exibido como um retângulo e mantém sua taxa de proporção.</span><span class="sxs-lookup"><span data-stu-id="5e535-302">`activityImage` is displayed as a rectangle and retains its aspect ratio.</span></span> |

<span data-ttu-id="5e535-303">Para obter todos os outros detalhes sobre as propriedades do cartão do conector, consulte referência de cartão de mensagem a [ação.](/outlook/actionable-messages/card-reference)</span><span class="sxs-lookup"><span data-stu-id="5e535-303">For all other details about connector card properties, see [actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="5e535-304">As únicas propriedades de cartão de conector Microsoft Teams atualmente não são compatíveis com:</span><span class="sxs-lookup"><span data-stu-id="5e535-304">The only connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="5e535-305">`startGroup`sempre tratado como `true` em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-305">`startGroup` always treated as `true` in Teams</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="5e535-306">Exemplo de um cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="5e535-306">Example of an Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="5e535-307">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="5e535-307">Receipt card</span></span>

<span data-ttu-id="5e535-308">Teams dá suporte ao cartão de recebimento.</span><span class="sxs-lookup"><span data-stu-id="5e535-308">Teams supports receipt card.</span></span> <span data-ttu-id="5e535-309">É um cartão que permite que um bot forneça um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="5e535-309">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="5e535-310">Normalmente, ele contém a lista de itens a ser incluídos no recibo, como informações fiscais e totais.</span><span class="sxs-lookup"><span data-stu-id="5e535-310">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="5e535-311">Suporte para cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="5e535-311">Support for receipt cards</span></span>

| <span data-ttu-id="5e535-312">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-312">Bots in Teams</span></span> | <span data-ttu-id="5e535-313">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="5e535-313">Messaging extensions</span></span>  | <span data-ttu-id="5e535-314">Conectores</span><span class="sxs-lookup"><span data-stu-id="5e535-314">Connectors</span></span> | <span data-ttu-id="5e535-315">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="5e535-315">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="5e535-316">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-316">✔</span></span> | <span data-ttu-id="5e535-317">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-317">✔</span></span> | <span data-ttu-id="5e535-318">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-318">✖</span></span> | <span data-ttu-id="5e535-319">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-319">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="5e535-320">Exemplo de um cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="5e535-320">Example of a receipt card</span></span>

![Exemplo de um cartão de confirmação](~/assets/images/cards/receipt.png)

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

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="5e535-322">Informações adicionais sobre cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="5e535-322">Additional information on receipt cards</span></span>

<span data-ttu-id="5e535-323">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="5e535-323">Bot Framework reference:</span></span>

* [<span data-ttu-id="5e535-324">Cartão de Node.js</span><span class="sxs-lookup"><span data-stu-id="5e535-324">Receipt card Node.js</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="5e535-325">Cartão de recebimento C #</span><span class="sxs-lookup"><span data-stu-id="5e535-325">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="5e535-326">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="5e535-326">Signin card</span></span>

<span data-ttu-id="5e535-327">O cartão de login permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="5e535-327">Signin card enables a bot to request a user to sign in.</span></span> <span data-ttu-id="5e535-328">Ele é suportado no Teams em uma forma ligeiramente diferente da encontrada na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="5e535-328">It is supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="5e535-329">O cartão de Teams é semelhante ao cartão de signin na Estrutura de Bot, exceto que o cartão de signin no Teams suporta apenas duas ações: `signin` e `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="5e535-329">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="5e535-330">A ação de signin pode ser usada de qualquer cartão Teams, não apenas o cartão de assinatura.</span><span class="sxs-lookup"><span data-stu-id="5e535-330">The signin action can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="5e535-331">Para obter mais informações sobre autenticação, [consulte Microsoft Teams fluxo de autenticação para bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="5e535-331">For more information on authentication, see [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="5e535-332">Suporte para cartões de assinatura</span><span class="sxs-lookup"><span data-stu-id="5e535-332">Support for signin cards</span></span>

| <span data-ttu-id="5e535-333">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-333">Bots in Teams</span></span> | <span data-ttu-id="5e535-334">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="5e535-334">Messaging extensions</span></span>  | <span data-ttu-id="5e535-335">Conectores</span><span class="sxs-lookup"><span data-stu-id="5e535-335">Connectors</span></span> | <span data-ttu-id="5e535-336">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="5e535-336">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="5e535-337">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-337">✔</span></span> | <span data-ttu-id="5e535-338">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-338">✖</span></span> | <span data-ttu-id="5e535-339">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-339">✖</span></span> | <span data-ttu-id="5e535-340">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-340">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="5e535-341">Informações adicionais sobre cartões de assinatura</span><span class="sxs-lookup"><span data-stu-id="5e535-341">Additional information on signin cards</span></span>

<span data-ttu-id="5e535-342">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="5e535-342">Bot Framework reference:</span></span>

* [<span data-ttu-id="5e535-343">Cartão de Node.js</span><span class="sxs-lookup"><span data-stu-id="5e535-343">Signin card Node.js</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="5e535-344">Signin card C #</span><span class="sxs-lookup"><span data-stu-id="5e535-344">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="5e535-345">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="5e535-345">Thumbnail card</span></span>

<span data-ttu-id="5e535-346">Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="5e535-346">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="5e535-347">Suporte para cartões de miniatura</span><span class="sxs-lookup"><span data-stu-id="5e535-347">Support for thumbnail cards</span></span>

| <span data-ttu-id="5e535-348">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-348">Bots in Teams</span></span> | <span data-ttu-id="5e535-349">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="5e535-349">Messaging extensions</span></span>  | <span data-ttu-id="5e535-350">Conectores</span><span class="sxs-lookup"><span data-stu-id="5e535-350">Connectors</span></span> | <span data-ttu-id="5e535-351">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="5e535-351">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="5e535-352">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-352">✔</span></span> | <span data-ttu-id="5e535-353">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-353">✔</span></span> | <span data-ttu-id="5e535-354">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-354">✖</span></span> | <span data-ttu-id="5e535-355">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-355">✔</span></span> |

![Exemplo de um cartão de miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="5e535-357">Propriedades de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="5e535-357">Properties of a thumbnail card</span></span>

| <span data-ttu-id="5e535-358">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5e535-358">Property</span></span> | <span data-ttu-id="5e535-359">Tipo</span><span class="sxs-lookup"><span data-stu-id="5e535-359">Type</span></span>  | <span data-ttu-id="5e535-360">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e535-360">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="5e535-361">title</span><span class="sxs-lookup"><span data-stu-id="5e535-361">title</span></span> | <span data-ttu-id="5e535-362">Rich text </span><span class="sxs-lookup"><span data-stu-id="5e535-362">Rich text</span></span> | <span data-ttu-id="5e535-363">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-363">Title of the card.</span></span> <span data-ttu-id="5e535-364">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="5e535-364">Maximum 2 lines.</span></span>|
| <span data-ttu-id="5e535-365">subtitle</span><span class="sxs-lookup"><span data-stu-id="5e535-365">subtitle</span></span> | <span data-ttu-id="5e535-366">Rich text </span><span class="sxs-lookup"><span data-stu-id="5e535-366">Rich text</span></span> | <span data-ttu-id="5e535-367">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-367">Subtitle of the card.</span></span> <span data-ttu-id="5e535-368">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="5e535-368">Maximum 2 lines.</span></span>|
| <span data-ttu-id="5e535-369">texto</span><span class="sxs-lookup"><span data-stu-id="5e535-369">text</span></span> | <span data-ttu-id="5e535-370">Rich text </span><span class="sxs-lookup"><span data-stu-id="5e535-370">Rich text</span></span> | <span data-ttu-id="5e535-371">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="5e535-371">Text appears under the subtitle.</span></span> <span data-ttu-id="5e535-372">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="5e535-372">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="5e535-373">images</span><span class="sxs-lookup"><span data-stu-id="5e535-373">images</span></span> | <span data-ttu-id="5e535-374">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="5e535-374">Array of images</span></span> | <span data-ttu-id="5e535-375">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-375">Image displayed at the top of the card.</span></span> <span data-ttu-id="5e535-376">Taxa de proporção 1:1 quadrado.</span><span class="sxs-lookup"><span data-stu-id="5e535-376">Aspect ratio 1:1 square.</span></span> |
| <span data-ttu-id="5e535-377">botões</span><span class="sxs-lookup"><span data-stu-id="5e535-377">buttons</span></span> | <span data-ttu-id="5e535-378">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="5e535-378">Array of action objects</span></span> | <span data-ttu-id="5e535-379">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="5e535-379">Set of actions applicable to the current card.</span></span> <span data-ttu-id="5e535-380">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="5e535-380">Maximum 6.</span></span> |
| <span data-ttu-id="5e535-381">tap</span><span class="sxs-lookup"><span data-stu-id="5e535-381">tap</span></span> | <span data-ttu-id="5e535-382">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="5e535-382">Action object</span></span> | <span data-ttu-id="5e535-383">Ativado quando o usuário toca no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="5e535-383">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="5e535-384">Exemplo de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="5e535-384">Example of a thumbnail card</span></span>

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

### <a name="additional-information"></a><span data-ttu-id="5e535-385">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="5e535-385">Additional information</span></span>

<span data-ttu-id="5e535-386">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="5e535-386">Bot Framework reference:</span></span>

* [<span data-ttu-id="5e535-387">Cartão de miniatura Node.js</span><span class="sxs-lookup"><span data-stu-id="5e535-387">Thumbnail card Node.js</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="5e535-388">Cartão de miniatura C #</span><span class="sxs-lookup"><span data-stu-id="5e535-388">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="5e535-389">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="5e535-389">Card collections</span></span>

<span data-ttu-id="5e535-390">Teams dá suporte a coleções card.</span><span class="sxs-lookup"><span data-stu-id="5e535-390">Teams supports Card collections.</span></span>

<span data-ttu-id="5e535-391">As coleções de cartões `builder.AttachmentLayout.carousel` incluem `builder.AttachmentLayout.list` e .</span><span class="sxs-lookup"><span data-stu-id="5e535-391">Card collections include `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="5e535-392">Essas coleções contêm cartões adaptáveis, herois ou miniaturas.</span><span class="sxs-lookup"><span data-stu-id="5e535-392">These collections contain adaptive, hero, or thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="5e535-393">Coleção Carousel</span><span class="sxs-lookup"><span data-stu-id="5e535-393">Carousel collection</span></span>

<span data-ttu-id="5e535-394">O [layout do carrossel](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="5e535-394">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="5e535-395">Suporte para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="5e535-395">Support for carousel collections</span></span>

| <span data-ttu-id="5e535-396">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-396">Bots in Teams</span></span> | <span data-ttu-id="5e535-397">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="5e535-397">Messaging extensions</span></span>  | <span data-ttu-id="5e535-398">Conectores</span><span class="sxs-lookup"><span data-stu-id="5e535-398">Connectors</span></span> | <span data-ttu-id="5e535-399">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="5e535-399">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="5e535-400">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-400">✔</span></span> | <span data-ttu-id="5e535-401">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-401">✖</span></span> | <span data-ttu-id="5e535-402">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-402">✖</span></span> | <span data-ttu-id="5e535-403">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-403">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="5e535-404">Um carrossel pode exibir no máximo dez cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="5e535-404">A carousel can display a maximum of ten cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="5e535-405">Propriedades de um cartão de carrossel</span><span class="sxs-lookup"><span data-stu-id="5e535-405">Properties of a carousel card</span></span>

<span data-ttu-id="5e535-406">As propriedades de um cartão de carrossel são as mesmas dos cartões de herói e miniatura.</span><span class="sxs-lookup"><span data-stu-id="5e535-406">Properties of a carousel card are same as those of the hero and thumbnail cards.</span></span>

### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="5e535-407">Exemplo de uma coleção de carrossel</span><span class="sxs-lookup"><span data-stu-id="5e535-407">Example of a carousel collection</span></span>

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="5e535-409">Sintaxe para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="5e535-409">Syntax for carousel collections</span></span>

<span data-ttu-id="5e535-410">`builder.AttachmentLayoutTypes.Carousel` é a sintaxe para coleções de carrossel.</span><span class="sxs-lookup"><span data-stu-id="5e535-410">`builder.AttachmentLayoutTypes.Carousel` is the syntax for carousel collections.</span></span>

## <a name="list-collection"></a><span data-ttu-id="5e535-411">Coleção List</span><span class="sxs-lookup"><span data-stu-id="5e535-411">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="5e535-412">Suporte para coleções de lista</span><span class="sxs-lookup"><span data-stu-id="5e535-412">Support for list collections</span></span>

<span data-ttu-id="5e535-413">O layout da lista mostra uma lista verticalmente empilhada de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="5e535-413">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="5e535-414">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-414">Bots in Teams</span></span> | <span data-ttu-id="5e535-415">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="5e535-415">Messaging extensions</span></span>  | <span data-ttu-id="5e535-416">Conectores</span><span class="sxs-lookup"><span data-stu-id="5e535-416">Connectors</span></span> | <span data-ttu-id="5e535-417">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="5e535-417">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="5e535-418">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-418">✔</span></span> | <span data-ttu-id="5e535-419">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-419">✔</span></span> | <span data-ttu-id="5e535-420">✖</span><span class="sxs-lookup"><span data-stu-id="5e535-420">✖</span></span> | <span data-ttu-id="5e535-421">✔</span><span class="sxs-lookup"><span data-stu-id="5e535-421">✔</span></span> |

### <a name="example-of-a-list-collection"></a><span data-ttu-id="5e535-422">Exemplo de uma coleção de listas</span><span class="sxs-lookup"><span data-stu-id="5e535-422">Example of a list collection</span></span>

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

<span data-ttu-id="5e535-424">As propriedades são as mesmas do cartão herói ou miniatura.</span><span class="sxs-lookup"><span data-stu-id="5e535-424">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="5e535-425">Uma lista pode exibir no máximo dez cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="5e535-425">A list can display a maximum of ten cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="5e535-426">Algumas combinações de cartões de lista ainda não são suportadas no iOS e no Android.</span><span class="sxs-lookup"><span data-stu-id="5e535-426">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="5e535-427">Sintaxe para coleções de lista</span><span class="sxs-lookup"><span data-stu-id="5e535-427">Syntax for list collections</span></span>

<span data-ttu-id="5e535-428">`builder.AttachmentLayout.list` é a sintaxe para coleções de lista.</span><span class="sxs-lookup"><span data-stu-id="5e535-428">`builder.AttachmentLayout.list` is the syntax for list collections.</span></span>

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="5e535-429">Cartões não suportados em Teams</span><span class="sxs-lookup"><span data-stu-id="5e535-429">Cards not supported in Teams</span></span>

<span data-ttu-id="5e535-430">Os cartões a seguir são implementados pela Estrutura de Bot, mas não são suportados por Teams:</span><span class="sxs-lookup"><span data-stu-id="5e535-430">The following cards are implemented by the Bot Framework, but are not supported by Teams:</span></span>

* <span data-ttu-id="5e535-431">Cartões de animação</span><span class="sxs-lookup"><span data-stu-id="5e535-431">Animation cards</span></span>
* <span data-ttu-id="5e535-432">Cartões de áudio</span><span class="sxs-lookup"><span data-stu-id="5e535-432">Audio cards</span></span>
* <span data-ttu-id="5e535-433">Cartões de vídeo</span><span class="sxs-lookup"><span data-stu-id="5e535-433">Video cards</span></span>
