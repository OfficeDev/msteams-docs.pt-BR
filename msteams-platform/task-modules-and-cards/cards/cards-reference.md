---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Teams
localization_priority: Normal
keywords: referência de cartões bots
ms.topic: reference
ms.openlocfilehash: 741980ea79dd23659dd2b8a240d767b8292ca251
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994382"
---
# <a name="cards-reference"></a><span data-ttu-id="8341d-104">Referência de cartões</span><span class="sxs-lookup"><span data-stu-id="8341d-104">Cards reference</span></span>

<span data-ttu-id="8341d-105">Os cartões listados neste documento são suportados em bots para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8341d-105">The cards listed in this document are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="8341d-106">Eles se baseiam em cartões definidos pela Estrutura de Bot (BF), mas Teams não suporta todos os cartões da Estrutura de Bot e, em vez disso, alguns cartões Teams foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="8341d-106">They are based on cards defined by the Bot Framework (BF), but Teams does not support all Bot Framework cards and instead some Teams cards have been added.</span></span> <span data-ttu-id="8341d-107">As diferenças são chamadas nas referências neste documento.</span><span class="sxs-lookup"><span data-stu-id="8341d-107">Differences are called out in the references in this document.</span></span>

## <a name="card-examples"></a><span data-ttu-id="8341d-108">Exemplos de cartão</span><span class="sxs-lookup"><span data-stu-id="8341d-108">Card examples</span></span>

<span data-ttu-id="8341d-109">Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do Construtor de Bots v3.</span><span class="sxs-lookup"><span data-stu-id="8341d-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK v3.</span></span> <span data-ttu-id="8341d-110">Exemplos de código também estão disponíveis no repositório Microsoft/BotBuilder-Samples no GitHub.</span><span class="sxs-lookup"><span data-stu-id="8341d-110">Code samples are also available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="8341d-111">.NET</span><span class="sxs-lookup"><span data-stu-id="8341d-111">.NET</span></span>
  * <span data-ttu-id="8341d-112">[Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="8341d-112">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="8341d-113">[Código de exemplo de cartões Construtor de bots v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="8341d-113">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span></span>

* <span data-ttu-id="8341d-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="8341d-114">Node.js</span></span>
  * <span data-ttu-id="8341d-115">[Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="8341d-115">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="8341d-116">[Código de exemplo de cartões Construtor de bots v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="8341d-116">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span></span>

## <a name="types-of-cards"></a><span data-ttu-id="8341d-117">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="8341d-117">Types of cards</span></span>

<span data-ttu-id="8341d-118">Esta tabela mostra os tipos de cartões disponíveis para você:</span><span class="sxs-lookup"><span data-stu-id="8341d-118">This table shows the types of cards available to you:</span></span>

| <span data-ttu-id="8341d-119">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="8341d-119">Card type</span></span> | <span data-ttu-id="8341d-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="8341d-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="8341d-121">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="8341d-121">Adaptive card</span></span>](#adaptive-card) | <span data-ttu-id="8341d-122">Esse cartão é um cartão altamente personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="8341d-122">This card is highly customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> |
| [<span data-ttu-id="8341d-123">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="8341d-123">Hero card</span></span>](#hero-card) | <span data-ttu-id="8341d-124">Esse cartão normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="8341d-124">This card typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="8341d-125">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="8341d-125">List card</span></span>](#list-card) | <span data-ttu-id="8341d-126">Este cartão é uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="8341d-126">This card is a scrolling list of items.</span></span> |
| [<span data-ttu-id="8341d-127">Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="8341d-127">Office 365 connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="8341d-128">Esse cartão tem um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="8341d-128">This card has a flexible layout with multiple sections, fields, images, and actions.</span></span> |
| [<span data-ttu-id="8341d-129">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="8341d-129">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="8341d-130">Este cartão fornece um recibo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="8341d-130">This card provides a receipt to the user.</span></span> |
| [<span data-ttu-id="8341d-131">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="8341d-131">Signin card</span></span>](#signin-card) | <span data-ttu-id="8341d-132">Esse cartão permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="8341d-132">This card enables a bot to request that a user signs in.</span></span> |
| [<span data-ttu-id="8341d-133">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="8341d-133">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="8341d-134">Esse cartão normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões.</span><span class="sxs-lookup"><span data-stu-id="8341d-134">This card typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="8341d-135">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="8341d-135">Card collections</span></span>](#card-collections) | <span data-ttu-id="8341d-136">Esses cartões são usados para retornar vários itens em uma única resposta.</span><span class="sxs-lookup"><span data-stu-id="8341d-136">This cards is used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="8341d-137">Propriedades comuns para todos os cartões</span><span class="sxs-lookup"><span data-stu-id="8341d-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="8341d-138">Imagens de cartão em linha</span><span class="sxs-lookup"><span data-stu-id="8341d-138">Inline card images</span></span>

<span data-ttu-id="8341d-139">O cartão pode conter uma imagem em linha incluindo um link para a imagem disponível publicamente.</span><span class="sxs-lookup"><span data-stu-id="8341d-139">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="8341d-140">Para fins de desempenho, é altamente recomendável hospedar a imagem em uma rede pública de distribuição de conteúdo (CDN).</span><span class="sxs-lookup"><span data-stu-id="8341d-140">For performance purposes, it is highly recommended you host the image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="8341d-141">As imagens são dimensionados para cima ou para baixo em tamanho, mantendo a proporção para cobrir a área da imagem.</span><span class="sxs-lookup"><span data-stu-id="8341d-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area.</span></span> <span data-ttu-id="8341d-142">Em seguida, as imagens são cortadas do centro para atingir a proporção apropriada para o cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-142">Images are then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="8341d-143">As imagens devem ter, no máximo, 1024×1024, no formato PNG, JPEG ou GIF e não suportam GIF animado.</span><span class="sxs-lookup"><span data-stu-id="8341d-143">Images must be at most 1024×1024, in PNG, JPEG, or GIF format, and do not support animated GIF.</span></span>

| <span data-ttu-id="8341d-144">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8341d-144">Property</span></span> | <span data-ttu-id="8341d-145">Tipo</span><span class="sxs-lookup"><span data-stu-id="8341d-145">Type</span></span>  | <span data-ttu-id="8341d-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="8341d-146">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8341d-147">url</span><span class="sxs-lookup"><span data-stu-id="8341d-147">url</span></span> | <span data-ttu-id="8341d-148">URL</span><span class="sxs-lookup"><span data-stu-id="8341d-148">URL</span></span> | <span data-ttu-id="8341d-149">URL HTTPS para a imagem.</span><span class="sxs-lookup"><span data-stu-id="8341d-149">HTTPS URL to the image.</span></span> |
| <span data-ttu-id="8341d-150">alt</span><span class="sxs-lookup"><span data-stu-id="8341d-150">alt</span></span> | <span data-ttu-id="8341d-151">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8341d-151">String</span></span> | <span data-ttu-id="8341d-152">Descrição acessível da imagem.</span><span class="sxs-lookup"><span data-stu-id="8341d-152">Accessible description of the image.</span></span> |

> [!NOTE]
> <span data-ttu-id="8341d-153">Se um cartão incluir uma URL de imagem que passa por um redirecionamento antes da imagem final, não há suporte para o redirecionamento na URL da imagem.</span><span class="sxs-lookup"><span data-stu-id="8341d-153">If a card includes an image URL that goes through a redirect before the final image, the redirect in image URL is not supported.</span></span> <span data-ttu-id="8341d-154">Isso ocorre para imagens compartilhadas na nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="8341d-154">This occurs for images shared on the public cloud.</span></span>

### <a name="buttons"></a><span data-ttu-id="8341d-155">Botões</span><span class="sxs-lookup"><span data-stu-id="8341d-155">Buttons</span></span>

<span data-ttu-id="8341d-156">Os botões são mostrados empilhados na parte inferior do cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-156">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="8341d-157">O texto do botão está sempre em uma única linha e é truncado se o texto exceder a largura do botão.</span><span class="sxs-lookup"><span data-stu-id="8341d-157">Button text is always on a single line and is truncated if the text exceeds the button width.</span></span> <span data-ttu-id="8341d-158">Quaisquer botões adicionais além do número máximo suportado pelo cartão não são mostrados.</span><span class="sxs-lookup"><span data-stu-id="8341d-158">Any additional buttons beyond the maximum number supported by the card are not shown.</span></span>

<span data-ttu-id="8341d-159">Para obter mais informações, consulte [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="8341d-159">For more information, see [card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

### <a name="card-formatting"></a><span data-ttu-id="8341d-160">Formatação de cartão</span><span class="sxs-lookup"><span data-stu-id="8341d-160">Card formatting</span></span>

<span data-ttu-id="8341d-161">Para obter mais informações sobre formatação de texto em cartões, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="8341d-161">For more information on text formatting in cards, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="8341d-162">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="8341d-162">Adaptive card</span></span>

<span data-ttu-id="8341d-163">Um cartão adaptável é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="8341d-163">An adaptive card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="8341d-164">Para obter mais informações, [consulte cartões adaptáveis v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="8341d-164">For more information, see [adaptive cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="8341d-165">Suporte para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="8341d-165">Support for adaptive cards</span></span>

| <span data-ttu-id="8341d-166">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-166">Bots in Teams</span></span> | <span data-ttu-id="8341d-167">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8341d-167">Messaging extensions</span></span>  | <span data-ttu-id="8341d-168">Conectores</span><span class="sxs-lookup"><span data-stu-id="8341d-168">Connectors</span></span> | <span data-ttu-id="8341d-169">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="8341d-169">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="8341d-170">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-170">✔</span></span> | <span data-ttu-id="8341d-171">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-171">✔</span></span> | <span data-ttu-id="8341d-172">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-172">✖</span></span> | <span data-ttu-id="8341d-173">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-173">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="8341d-174">Teams plataforma suporta v1.2 ou anterior de recursos de cartão adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="8341d-174">Teams platform supports v1.2 or earlier of adaptive card features.</span></span>
> * <span data-ttu-id="8341d-175">O estilo de ação positivo ou destrutivo não é suportado em Cartões Adaptáveis na Teams plataforma.</span><span class="sxs-lookup"><span data-stu-id="8341d-175">Positive or destructive action styling is not supported in Adaptive Cards on the Teams platform.</span></span>
> * <span data-ttu-id="8341d-176">Atualmente, os elementos de mídia não têm suporte em Cartões Adaptáveis na plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="8341d-176">Media elements are currently not supported in Adaptive Cards on the Teams platform.</span></span>

### <a name="example-of-an-adaptive-card"></a><span data-ttu-id="8341d-177">Exemplo de um cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="8341d-177">Example of an adaptive card</span></span>

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

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="8341d-179">Informações adicionais sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="8341d-179">Additional information on adaptive cards</span></span>

<span data-ttu-id="8341d-180">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="8341d-180">Bot Framework reference:</span></span>

* [<span data-ttu-id="8341d-181">Cartões adaptáveis Node.js</span><span class="sxs-lookup"><span data-stu-id="8341d-181">Adaptive cards Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="8341d-182">Cartão adaptável C #</span><span class="sxs-lookup"><span data-stu-id="8341d-182">Adaptive card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

## <a name="hero-card"></a><span data-ttu-id="8341d-183">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="8341d-183">Hero card</span></span>

<span data-ttu-id="8341d-184">Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="8341d-184">A card that typically contains a single large image, one or more buttons, and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="8341d-185">Suporte para cartões de herói</span><span class="sxs-lookup"><span data-stu-id="8341d-185">Support for hero cards</span></span>

| <span data-ttu-id="8341d-186">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-186">Bots in Teams</span></span> | <span data-ttu-id="8341d-187">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8341d-187">Messaging extensions</span></span>  | <span data-ttu-id="8341d-188">Conectores</span><span class="sxs-lookup"><span data-stu-id="8341d-188">Connectors</span></span> | <span data-ttu-id="8341d-189">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="8341d-189">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="8341d-190">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-190">✔</span></span> | <span data-ttu-id="8341d-191">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-191">✔</span></span> | <span data-ttu-id="8341d-192">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-192">✖</span></span> | <span data-ttu-id="8341d-193">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-193">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="8341d-194">Propriedades de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="8341d-194">Properties of a hero card</span></span>

| <span data-ttu-id="8341d-195">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8341d-195">Property</span></span> | <span data-ttu-id="8341d-196">Tipo</span><span class="sxs-lookup"><span data-stu-id="8341d-196">Type</span></span>  | <span data-ttu-id="8341d-197">Descrição</span><span class="sxs-lookup"><span data-stu-id="8341d-197">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8341d-198">title</span><span class="sxs-lookup"><span data-stu-id="8341d-198">title</span></span> | <span data-ttu-id="8341d-199">Rich text </span><span class="sxs-lookup"><span data-stu-id="8341d-199">Rich text</span></span> | <span data-ttu-id="8341d-200">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-200">Title of the card.</span></span> <span data-ttu-id="8341d-201">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="8341d-201">Maximum 2 lines.</span></span> |
| <span data-ttu-id="8341d-202">subtitle</span><span class="sxs-lookup"><span data-stu-id="8341d-202">subtitle</span></span> | <span data-ttu-id="8341d-203">Rich text </span><span class="sxs-lookup"><span data-stu-id="8341d-203">Rich text</span></span> | <span data-ttu-id="8341d-204">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-204">Subtitle of the card.</span></span> <span data-ttu-id="8341d-205">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="8341d-205">Maximum 2 lines.</span></span>|
| <span data-ttu-id="8341d-206">texto</span><span class="sxs-lookup"><span data-stu-id="8341d-206">text</span></span> | <span data-ttu-id="8341d-207">Rich text </span><span class="sxs-lookup"><span data-stu-id="8341d-207">Rich text</span></span> | <span data-ttu-id="8341d-208">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="8341d-208">Text appears under the subtitle.</span></span> <span data-ttu-id="8341d-209">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="8341d-209">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="8341d-210">images</span><span class="sxs-lookup"><span data-stu-id="8341d-210">images</span></span> | <span data-ttu-id="8341d-211">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="8341d-211">Array of images</span></span> | <span data-ttu-id="8341d-212">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-212">Image displayed at the top of the card.</span></span> <span data-ttu-id="8341d-213">Taxa de proporção 16:9.</span><span class="sxs-lookup"><span data-stu-id="8341d-213">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="8341d-214">botões</span><span class="sxs-lookup"><span data-stu-id="8341d-214">buttons</span></span> | <span data-ttu-id="8341d-215">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="8341d-215">Array of action objects</span></span> | <span data-ttu-id="8341d-216">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="8341d-216">Set of actions applicable to the current card.</span></span> <span data-ttu-id="8341d-217">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="8341d-217">Maximum 6.</span></span> |
| <span data-ttu-id="8341d-218">tap</span><span class="sxs-lookup"><span data-stu-id="8341d-218">tap</span></span> | <span data-ttu-id="8341d-219">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="8341d-219">Action object</span></span> | <span data-ttu-id="8341d-220">Ativado quando o usuário toca no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-220">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="8341d-221">Exemplo de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="8341d-221">Example of a hero card</span></span>

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

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="8341d-223">Informações adicionais sobre cartões de herói</span><span class="sxs-lookup"><span data-stu-id="8341d-223">Additional information on hero cards</span></span>

<span data-ttu-id="8341d-224">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="8341d-224">Bot Framework reference:</span></span>

* [<span data-ttu-id="8341d-225">Cartão de herói Node.js</span><span class="sxs-lookup"><span data-stu-id="8341d-225">Hero card Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="8341d-226">Cartão de herói C #</span><span class="sxs-lookup"><span data-stu-id="8341d-226">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="8341d-227">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="8341d-227">List card</span></span>

<span data-ttu-id="8341d-228">O cartão de lista foi adicionado por Teams para fornecer funções além do que a coleção de listas pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="8341d-228">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="8341d-229">O cartão de listagem fornece uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="8341d-229">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="8341d-230">Suporte para cartões de lista</span><span class="sxs-lookup"><span data-stu-id="8341d-230">Support for list cards</span></span>

| <span data-ttu-id="8341d-231">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-231">Bots in Teams</span></span> | <span data-ttu-id="8341d-232">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8341d-232">Messaging extensions</span></span>  | <span data-ttu-id="8341d-233">Conectores</span><span class="sxs-lookup"><span data-stu-id="8341d-233">Connectors</span></span> | <span data-ttu-id="8341d-234">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="8341d-234">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="8341d-235">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-235">✔</span></span> | <span data-ttu-id="8341d-236">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-236">✖</span></span> | <span data-ttu-id="8341d-237">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-237">✖</span></span> |<span data-ttu-id="8341d-238">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-238">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="8341d-239">Propriedades de um cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="8341d-239">Properties of a list card</span></span>

| <span data-ttu-id="8341d-240">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8341d-240">Property</span></span> | <span data-ttu-id="8341d-241">Tipo</span><span class="sxs-lookup"><span data-stu-id="8341d-241">Type</span></span>  | <span data-ttu-id="8341d-242">Descrição</span><span class="sxs-lookup"><span data-stu-id="8341d-242">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8341d-243">title</span><span class="sxs-lookup"><span data-stu-id="8341d-243">title</span></span> | <span data-ttu-id="8341d-244">Rich text </span><span class="sxs-lookup"><span data-stu-id="8341d-244">Rich text</span></span> | <span data-ttu-id="8341d-245">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-245">Title of the card.</span></span> <span data-ttu-id="8341d-246">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="8341d-246">Maximum 2 lines.</span></span>|
| <span data-ttu-id="8341d-247">itens</span><span class="sxs-lookup"><span data-stu-id="8341d-247">items</span></span> | <span data-ttu-id="8341d-248">Matriz de itens de lista</span><span class="sxs-lookup"><span data-stu-id="8341d-248">Array of list items</span></span> ||
| <span data-ttu-id="8341d-249">botões</span><span class="sxs-lookup"><span data-stu-id="8341d-249">buttons</span></span> | <span data-ttu-id="8341d-250">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="8341d-250">Array of action objects</span></span> | <span data-ttu-id="8341d-251">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="8341d-251">Set of actions applicable to the current card.</span></span> <span data-ttu-id="8341d-252">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="8341d-252">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="8341d-253">Exemplo de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="8341d-253">Example of a list card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="8341d-254">Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="8341d-254">Office 365 connector card</span></span>

<span data-ttu-id="8341d-255">O Office 365 conector de usuário é compatível com Teams, não na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="8341d-255">The Office 365 connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="8341d-256">Este cartão fornece um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="8341d-256">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="8341d-257">Esse cartão encapsula um cartão de conector para que ele possa ser usado por bots.</span><span class="sxs-lookup"><span data-stu-id="8341d-257">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="8341d-258">Para diferenças entre cartões de conector e o cartão O365, consulte [Notes on the Office 365 connector card](#notes-on-the-office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="8341d-258">For differences between connector cards and the O365 card, see [Notes on the Office 365 connector card](#notes-on-the-office-365-connector-card).</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="8341d-259">Suporte para cartões Office 365 conectores</span><span class="sxs-lookup"><span data-stu-id="8341d-259">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="8341d-260">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-260">Bots in Teams</span></span> | <span data-ttu-id="8341d-261">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8341d-261">Messaging extensions</span></span>  | <span data-ttu-id="8341d-262">Conectores</span><span class="sxs-lookup"><span data-stu-id="8341d-262">Connectors</span></span> | <span data-ttu-id="8341d-263">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="8341d-263">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="8341d-264">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-264">✔</span></span> | <span data-ttu-id="8341d-265">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-265">✔</span></span> | <span data-ttu-id="8341d-266">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-266">✔</span></span> | <span data-ttu-id="8341d-267">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-267">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="8341d-268">Propriedades do cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="8341d-268">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="8341d-269">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8341d-269">Property</span></span> | <span data-ttu-id="8341d-270">Tipo</span><span class="sxs-lookup"><span data-stu-id="8341d-270">Type</span></span>  | <span data-ttu-id="8341d-271">Descrição</span><span class="sxs-lookup"><span data-stu-id="8341d-271">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8341d-272">title</span><span class="sxs-lookup"><span data-stu-id="8341d-272">title</span></span> | <span data-ttu-id="8341d-273">Rich text </span><span class="sxs-lookup"><span data-stu-id="8341d-273">Rich text</span></span> | <span data-ttu-id="8341d-274">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-274">Title of the card.</span></span> <span data-ttu-id="8341d-275">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="8341d-275">Maximum 2 lines.</span></span> |
| <span data-ttu-id="8341d-276">summary</span><span class="sxs-lookup"><span data-stu-id="8341d-276">summary</span></span> | <span data-ttu-id="8341d-277">Rich text </span><span class="sxs-lookup"><span data-stu-id="8341d-277">Rich text</span></span> | <span data-ttu-id="8341d-278">Resumo do cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-278">Summary of the card.</span></span> <span data-ttu-id="8341d-279">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="8341d-279">Maximum 2 lines.</span></span> |
| <span data-ttu-id="8341d-280">texto</span><span class="sxs-lookup"><span data-stu-id="8341d-280">text</span></span> | <span data-ttu-id="8341d-281">Rich text </span><span class="sxs-lookup"><span data-stu-id="8341d-281">Rich text</span></span> | <span data-ttu-id="8341d-282">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="8341d-282">Text appears under the subtitle.</span></span> <span data-ttu-id="8341d-283">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="8341d-283">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="8341d-284">themeColor</span><span class="sxs-lookup"><span data-stu-id="8341d-284">themeColor</span></span> | <span data-ttu-id="8341d-285">Cadeia de caracteres HEX</span><span class="sxs-lookup"><span data-stu-id="8341d-285">HEX string</span></span> | <span data-ttu-id="8341d-286">Cor que substitui o accentColor fornecido do manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8341d-286">Color that overrides the accentColor provided from the application manifest.</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="8341d-287">Observações no cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="8341d-287">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="8341d-288">Office 365 conectores funcionam corretamente no Microsoft Teams, incluindo [ações actionCard](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="8341d-288">Office 365 connector cards function properly in Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="8341d-289">Uma diferença importante entre o uso de cartões conectores de um conector e o uso de cartões de conector no bot é o tratamento de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-289">One important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="8341d-290">Para um conector, o ponto de extremidade recebe a carga de cartão por meio de HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="8341d-290">For a connector, the endpoint receives the card payload through HTTP POST.</span></span>
* <span data-ttu-id="8341d-291">Para um bot, a ação dispara uma atividade que envia apenas a ID de ação `HttpPOST` e o corpo para o `invoke` bot.</span><span class="sxs-lookup"><span data-stu-id="8341d-291">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="8341d-292">Cada cartão de conector pode exibir no máximo dez seções, e cada seção pode conter no máximo cinco imagens e cinco ações.</span><span class="sxs-lookup"><span data-stu-id="8341d-292">Each connector card can display a maximum of ten sections, and each section can contain a maximum of five images and five actions.</span></span>

> [!NOTE]
> <span data-ttu-id="8341d-293">Quaisquer seções, imagens ou ações adicionais em uma mensagem não são exibidas.</span><span class="sxs-lookup"><span data-stu-id="8341d-293">Any additional sections, images, or actions in a message do not appear.</span></span>

<span data-ttu-id="8341d-294">Todos os campos de texto suportam marcação e HTML.</span><span class="sxs-lookup"><span data-stu-id="8341d-294">All text fields support markdown and HTML.</span></span> <span data-ttu-id="8341d-295">Você pode controlar quais seções usam markdown ou HTML definindo `markdown` a propriedade em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="8341d-295">You can control which sections use markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="8341d-296">Por padrão, `markdown` é definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="8341d-296">By default, `markdown` is set to `true`.</span></span> <span data-ttu-id="8341d-297">Se você quiser usar HTML em vez disso, de definir `markdown` como `false` .</span><span class="sxs-lookup"><span data-stu-id="8341d-297">If you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="8341d-298">Se você especificar a `themeColor` propriedade, ela substituirá `accentColor` a propriedade no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8341d-298">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="8341d-299">Para especificar o estilo de renderização `activityImage` para , você pode definir da seguinte `activityImageType` forma:</span><span class="sxs-lookup"><span data-stu-id="8341d-299">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows:</span></span>

| <span data-ttu-id="8341d-300">Valor</span><span class="sxs-lookup"><span data-stu-id="8341d-300">Value</span></span> | <span data-ttu-id="8341d-301">Descrição</span><span class="sxs-lookup"><span data-stu-id="8341d-301">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="8341d-302">Padrão; `activityImage` é cortada como um círculo.</span><span class="sxs-lookup"><span data-stu-id="8341d-302">Default; `activityImage` is cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="8341d-303">`activityImage` é exibido como um retângulo e mantém sua taxa de proporção.</span><span class="sxs-lookup"><span data-stu-id="8341d-303">`activityImage` is displayed as a rectangle and retains its aspect ratio.</span></span> |

<span data-ttu-id="8341d-304">Para obter todos os outros detalhes sobre as propriedades do cartão do conector, consulte referência de cartão de mensagem a [ação.](/outlook/actionable-messages/card-reference)</span><span class="sxs-lookup"><span data-stu-id="8341d-304">For all other details about connector card properties, see [actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="8341d-305">As únicas propriedades de cartão de conector Microsoft Teams atualmente não são compatíveis com:</span><span class="sxs-lookup"><span data-stu-id="8341d-305">The only connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="8341d-306">`startGroup`sempre tratado como `true` em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-306">`startGroup` always treated as `true` in Teams</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="8341d-307">Exemplo de um cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="8341d-307">Example of an Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="8341d-308">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="8341d-308">Receipt card</span></span>

<span data-ttu-id="8341d-309">Teams dá suporte ao cartão de recebimento.</span><span class="sxs-lookup"><span data-stu-id="8341d-309">Teams supports receipt card.</span></span> <span data-ttu-id="8341d-310">É um cartão que permite que um bot forneça um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="8341d-310">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="8341d-311">Normalmente, ele contém a lista de itens a ser incluídos no recibo, como informações fiscais e totais.</span><span class="sxs-lookup"><span data-stu-id="8341d-311">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="8341d-312">Suporte para cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="8341d-312">Support for receipt cards</span></span>

| <span data-ttu-id="8341d-313">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-313">Bots in Teams</span></span> | <span data-ttu-id="8341d-314">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8341d-314">Messaging extensions</span></span>  | <span data-ttu-id="8341d-315">Conectores</span><span class="sxs-lookup"><span data-stu-id="8341d-315">Connectors</span></span> | <span data-ttu-id="8341d-316">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="8341d-316">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="8341d-317">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-317">✔</span></span> | <span data-ttu-id="8341d-318">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-318">✔</span></span> | <span data-ttu-id="8341d-319">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-319">✖</span></span> | <span data-ttu-id="8341d-320">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-320">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="8341d-321">Exemplo de um cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="8341d-321">Example of a receipt card</span></span>

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

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="8341d-323">Informações adicionais sobre cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="8341d-323">Additional information on receipt cards</span></span>

<span data-ttu-id="8341d-324">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="8341d-324">Bot Framework reference:</span></span>

* [<span data-ttu-id="8341d-325">Cartão de Node.js</span><span class="sxs-lookup"><span data-stu-id="8341d-325">Receipt card Node.js</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="8341d-326">Cartão de recebimento C #</span><span class="sxs-lookup"><span data-stu-id="8341d-326">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="8341d-327">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="8341d-327">Signin card</span></span>

<span data-ttu-id="8341d-328">O cartão de login permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="8341d-328">Signin card enables a bot to request a user to sign in.</span></span> <span data-ttu-id="8341d-329">Ele é suportado no Teams em uma forma ligeiramente diferente da encontrada na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="8341d-329">It is supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="8341d-330">O cartão de Teams é semelhante ao cartão de signin na Estrutura de Bot, exceto que o cartão de signin no Teams suporta apenas duas ações: `signin` e `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="8341d-330">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="8341d-331">A ação de signin pode ser usada de qualquer cartão Teams, não apenas o cartão de assinatura.</span><span class="sxs-lookup"><span data-stu-id="8341d-331">The signin action can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="8341d-332">Para obter mais informações sobre autenticação, [consulte Microsoft Teams fluxo de autenticação para bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="8341d-332">For more information on authentication, see [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="8341d-333">Suporte para cartões de assinatura</span><span class="sxs-lookup"><span data-stu-id="8341d-333">Support for signin cards</span></span>

| <span data-ttu-id="8341d-334">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-334">Bots in Teams</span></span> | <span data-ttu-id="8341d-335">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8341d-335">Messaging extensions</span></span>  | <span data-ttu-id="8341d-336">Conectores</span><span class="sxs-lookup"><span data-stu-id="8341d-336">Connectors</span></span> | <span data-ttu-id="8341d-337">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="8341d-337">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="8341d-338">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-338">✔</span></span> | <span data-ttu-id="8341d-339">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-339">✖</span></span> | <span data-ttu-id="8341d-340">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-340">✖</span></span> | <span data-ttu-id="8341d-341">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-341">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="8341d-342">Informações adicionais sobre cartões de assinatura</span><span class="sxs-lookup"><span data-stu-id="8341d-342">Additional information on signin cards</span></span>

<span data-ttu-id="8341d-343">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="8341d-343">Bot Framework reference:</span></span>

* [<span data-ttu-id="8341d-344">Cartão de Node.js</span><span class="sxs-lookup"><span data-stu-id="8341d-344">Signin card Node.js</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="8341d-345">Signin card C #</span><span class="sxs-lookup"><span data-stu-id="8341d-345">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="8341d-346">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="8341d-346">Thumbnail card</span></span>

<span data-ttu-id="8341d-347">Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="8341d-347">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="8341d-348">Suporte para cartões de miniatura</span><span class="sxs-lookup"><span data-stu-id="8341d-348">Support for thumbnail cards</span></span>

| <span data-ttu-id="8341d-349">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-349">Bots in Teams</span></span> | <span data-ttu-id="8341d-350">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8341d-350">Messaging extensions</span></span>  | <span data-ttu-id="8341d-351">Conectores</span><span class="sxs-lookup"><span data-stu-id="8341d-351">Connectors</span></span> | <span data-ttu-id="8341d-352">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="8341d-352">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="8341d-353">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-353">✔</span></span> | <span data-ttu-id="8341d-354">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-354">✔</span></span> | <span data-ttu-id="8341d-355">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-355">✖</span></span> | <span data-ttu-id="8341d-356">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-356">✔</span></span> |

![Exemplo de um cartão de miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="8341d-358">Propriedades de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="8341d-358">Properties of a thumbnail card</span></span>

| <span data-ttu-id="8341d-359">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8341d-359">Property</span></span> | <span data-ttu-id="8341d-360">Tipo</span><span class="sxs-lookup"><span data-stu-id="8341d-360">Type</span></span>  | <span data-ttu-id="8341d-361">Descrição</span><span class="sxs-lookup"><span data-stu-id="8341d-361">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8341d-362">title</span><span class="sxs-lookup"><span data-stu-id="8341d-362">title</span></span> | <span data-ttu-id="8341d-363">Rich text </span><span class="sxs-lookup"><span data-stu-id="8341d-363">Rich text</span></span> | <span data-ttu-id="8341d-364">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-364">Title of the card.</span></span> <span data-ttu-id="8341d-365">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="8341d-365">Maximum 2 lines.</span></span>|
| <span data-ttu-id="8341d-366">subtitle</span><span class="sxs-lookup"><span data-stu-id="8341d-366">subtitle</span></span> | <span data-ttu-id="8341d-367">Rich text </span><span class="sxs-lookup"><span data-stu-id="8341d-367">Rich text</span></span> | <span data-ttu-id="8341d-368">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-368">Subtitle of the card.</span></span> <span data-ttu-id="8341d-369">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="8341d-369">Maximum 2 lines.</span></span>|
| <span data-ttu-id="8341d-370">texto</span><span class="sxs-lookup"><span data-stu-id="8341d-370">text</span></span> | <span data-ttu-id="8341d-371">Rich text </span><span class="sxs-lookup"><span data-stu-id="8341d-371">Rich text</span></span> | <span data-ttu-id="8341d-372">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="8341d-372">Text appears under the subtitle.</span></span> <span data-ttu-id="8341d-373">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="8341d-373">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="8341d-374">images</span><span class="sxs-lookup"><span data-stu-id="8341d-374">images</span></span> | <span data-ttu-id="8341d-375">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="8341d-375">Array of images</span></span> | <span data-ttu-id="8341d-376">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-376">Image displayed at the top of the card.</span></span> <span data-ttu-id="8341d-377">Taxa de proporção 1:1 quadrado.</span><span class="sxs-lookup"><span data-stu-id="8341d-377">Aspect ratio 1:1 square.</span></span> |
| <span data-ttu-id="8341d-378">botões</span><span class="sxs-lookup"><span data-stu-id="8341d-378">buttons</span></span> | <span data-ttu-id="8341d-379">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="8341d-379">Array of action objects</span></span> | <span data-ttu-id="8341d-380">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="8341d-380">Set of actions applicable to the current card.</span></span> <span data-ttu-id="8341d-381">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="8341d-381">Maximum 6.</span></span> |
| <span data-ttu-id="8341d-382">tap</span><span class="sxs-lookup"><span data-stu-id="8341d-382">tap</span></span> | <span data-ttu-id="8341d-383">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="8341d-383">Action object</span></span> | <span data-ttu-id="8341d-384">Ativado quando o usuário toca no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="8341d-384">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="8341d-385">Exemplo de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="8341d-385">Example of a thumbnail card</span></span>

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

### <a name="additional-information"></a><span data-ttu-id="8341d-386">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="8341d-386">Additional information</span></span>

<span data-ttu-id="8341d-387">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="8341d-387">Bot Framework reference:</span></span>

* [<span data-ttu-id="8341d-388">Cartão de miniatura Node.js</span><span class="sxs-lookup"><span data-stu-id="8341d-388">Thumbnail card Node.js</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="8341d-389">Cartão de miniatura C #</span><span class="sxs-lookup"><span data-stu-id="8341d-389">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="8341d-390">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="8341d-390">Card collections</span></span>

<span data-ttu-id="8341d-391">Teams dá suporte a coleções card.</span><span class="sxs-lookup"><span data-stu-id="8341d-391">Teams supports Card collections.</span></span>

<span data-ttu-id="8341d-392">As coleções de cartões `builder.AttachmentLayout.carousel` incluem `builder.AttachmentLayout.list` e .</span><span class="sxs-lookup"><span data-stu-id="8341d-392">Card collections include `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="8341d-393">Essas coleções contêm cartões adaptáveis, herois ou miniaturas.</span><span class="sxs-lookup"><span data-stu-id="8341d-393">These collections contain adaptive, hero, or thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="8341d-394">Coleção Carousel</span><span class="sxs-lookup"><span data-stu-id="8341d-394">Carousel collection</span></span>

<span data-ttu-id="8341d-395">O [layout do carrossel](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="8341d-395">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="8341d-396">Suporte para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="8341d-396">Support for carousel collections</span></span>

| <span data-ttu-id="8341d-397">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-397">Bots in Teams</span></span> | <span data-ttu-id="8341d-398">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8341d-398">Messaging extensions</span></span>  | <span data-ttu-id="8341d-399">Conectores</span><span class="sxs-lookup"><span data-stu-id="8341d-399">Connectors</span></span> | <span data-ttu-id="8341d-400">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="8341d-400">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="8341d-401">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-401">✔</span></span> | <span data-ttu-id="8341d-402">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-402">✖</span></span> | <span data-ttu-id="8341d-403">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-403">✖</span></span> | <span data-ttu-id="8341d-404">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-404">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="8341d-405">Um carrossel pode exibir no máximo dez cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="8341d-405">A carousel can display a maximum of ten cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="8341d-406">Propriedades de um cartão de carrossel</span><span class="sxs-lookup"><span data-stu-id="8341d-406">Properties of a carousel card</span></span>

<span data-ttu-id="8341d-407">As propriedades de um cartão de carrossel são as mesmas dos cartões de herói e miniatura.</span><span class="sxs-lookup"><span data-stu-id="8341d-407">Properties of a carousel card are same as those of the hero and thumbnail cards.</span></span>

### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="8341d-408">Exemplo de uma coleção de carrossel</span><span class="sxs-lookup"><span data-stu-id="8341d-408">Example of a carousel collection</span></span>

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="8341d-410">Sintaxe para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="8341d-410">Syntax for carousel collections</span></span>

<span data-ttu-id="8341d-411">`builder.AttachmentLayoutTypes.Carousel` é a sintaxe para coleções de carrossel.</span><span class="sxs-lookup"><span data-stu-id="8341d-411">`builder.AttachmentLayoutTypes.Carousel` is the syntax for carousel collections.</span></span>

## <a name="list-collection"></a><span data-ttu-id="8341d-412">Coleção List</span><span class="sxs-lookup"><span data-stu-id="8341d-412">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="8341d-413">Suporte para coleções de lista</span><span class="sxs-lookup"><span data-stu-id="8341d-413">Support for list collections</span></span>

<span data-ttu-id="8341d-414">O layout da lista mostra uma lista verticalmente empilhada de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="8341d-414">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="8341d-415">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-415">Bots in Teams</span></span> | <span data-ttu-id="8341d-416">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8341d-416">Messaging extensions</span></span>  | <span data-ttu-id="8341d-417">Conectores</span><span class="sxs-lookup"><span data-stu-id="8341d-417">Connectors</span></span> | <span data-ttu-id="8341d-418">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="8341d-418">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="8341d-419">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-419">✔</span></span> | <span data-ttu-id="8341d-420">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-420">✔</span></span> | <span data-ttu-id="8341d-421">✖</span><span class="sxs-lookup"><span data-stu-id="8341d-421">✖</span></span> | <span data-ttu-id="8341d-422">✔</span><span class="sxs-lookup"><span data-stu-id="8341d-422">✔</span></span> |

### <a name="example-of-a-list-collection"></a><span data-ttu-id="8341d-423">Exemplo de uma coleção de listas</span><span class="sxs-lookup"><span data-stu-id="8341d-423">Example of a list collection</span></span>

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

<span data-ttu-id="8341d-425">As propriedades são as mesmas do cartão herói ou miniatura.</span><span class="sxs-lookup"><span data-stu-id="8341d-425">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="8341d-426">Uma lista pode exibir no máximo dez cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="8341d-426">A list can display a maximum of ten cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="8341d-427">Algumas combinações de cartões de lista ainda não são suportadas no iOS e no Android.</span><span class="sxs-lookup"><span data-stu-id="8341d-427">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="8341d-428">Sintaxe para coleções de lista</span><span class="sxs-lookup"><span data-stu-id="8341d-428">Syntax for list collections</span></span>

<span data-ttu-id="8341d-429">`builder.AttachmentLayout.list` é a sintaxe para coleções de lista.</span><span class="sxs-lookup"><span data-stu-id="8341d-429">`builder.AttachmentLayout.list` is the syntax for list collections.</span></span>

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="8341d-430">Cartões não suportados em Teams</span><span class="sxs-lookup"><span data-stu-id="8341d-430">Cards not supported in Teams</span></span>

<span data-ttu-id="8341d-431">Os cartões a seguir são implementados pela Estrutura de Bot, mas não são suportados por Teams:</span><span class="sxs-lookup"><span data-stu-id="8341d-431">The following cards are implemented by the Bot Framework, but are not supported by Teams:</span></span>

* <span data-ttu-id="8341d-432">Cartões de animação</span><span class="sxs-lookup"><span data-stu-id="8341d-432">Animation cards</span></span>
* <span data-ttu-id="8341d-433">Cartões de áudio</span><span class="sxs-lookup"><span data-stu-id="8341d-433">Audio cards</span></span>
* <span data-ttu-id="8341d-434">Cartões de vídeo</span><span class="sxs-lookup"><span data-stu-id="8341d-434">Video cards</span></span>
