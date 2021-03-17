---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Teams
keywords: referência de cartões bots
ms.topic: reference
ms.openlocfilehash: 5cb289738f379dedf53f3a96a7dcff61b908e901
ms.sourcegitcommit: 1ce74ed167bb81bf09f7f6f8d518093efafb549e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2021
ms.locfileid: "50827932"
---
# <a name="cards-reference"></a><span data-ttu-id="fac08-104">Referência de cartões</span><span class="sxs-lookup"><span data-stu-id="fac08-104">Cards reference</span></span>

<span data-ttu-id="fac08-105">Os cartões listados nesta seção são suportados em bots para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="fac08-105">The cards listed in this section are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="fac08-106">Eles se baseiam em cartões definidos pela Estrutura de Bot, mas o Teams não dá suporte a todos os cartões da Estrutura de Bot e adicionou alguns de seus próprios.</span><span class="sxs-lookup"><span data-stu-id="fac08-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span> <span data-ttu-id="fac08-107">As diferenças são chamadas nas referências neste documento.</span><span class="sxs-lookup"><span data-stu-id="fac08-107">Differences are called out in the references in this document.</span></span>

## <a name="card-examples"></a><span data-ttu-id="fac08-108">Exemplos de cartão</span><span class="sxs-lookup"><span data-stu-id="fac08-108">Card examples</span></span>

<span data-ttu-id="fac08-109">Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do Construtor de Bots (v3).</span><span class="sxs-lookup"><span data-stu-id="fac08-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK (v3).</span></span> <span data-ttu-id="fac08-110">Exemplos de código também estão disponíveis no repositório Microsoft/BotBuilder-Samples no GitHub.</span><span class="sxs-lookup"><span data-stu-id="fac08-110">Code samples are also available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="fac08-111">.NET</span><span class="sxs-lookup"><span data-stu-id="fac08-111">.NET</span></span>
  * [<span data-ttu-id="fac08-112">Adicionar cartões como anexos a mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-112">Add cards as attachments to messages</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)
  * [<span data-ttu-id="fac08-113">Código de exemplo de cartões (Construtor de Bots v4)</span><span class="sxs-lookup"><span data-stu-id="fac08-113">Cards sample code (Bot Builder v4)</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards)

* <span data-ttu-id="fac08-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="fac08-114">Node.js</span></span>
  * [<span data-ttu-id="fac08-115">Adicionar cartões como anexos a mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-115">Add cards as attachments to messages</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
  * [<span data-ttu-id="fac08-116">Código de exemplo de cartões (Construtor de Bots v4)</span><span class="sxs-lookup"><span data-stu-id="fac08-116">Cards sample code (Bot Builder v4)</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards)

## <a name="types-of-cards"></a><span data-ttu-id="fac08-117">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="fac08-117">Types of cards</span></span>

<span data-ttu-id="fac08-118">Esta tabela mostra os tipos de cartões disponíveis para você:</span><span class="sxs-lookup"><span data-stu-id="fac08-118">This table shows the types of cards available to you:</span></span>

| <span data-ttu-id="fac08-119">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="fac08-119">Card type</span></span> | <span data-ttu-id="fac08-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="fac08-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="fac08-121">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="fac08-121">Adaptive card</span></span>](#adaptive-card) | <span data-ttu-id="fac08-122">Cartão altamente personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="fac08-122">Highly customizable card that can contain any combination of text, speech, images, buttons and input fields.</span></span> |
| [<span data-ttu-id="fac08-123">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="fac08-123">Hero card</span></span>](#hero-card) | <span data-ttu-id="fac08-124">Normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="fac08-124">Typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="fac08-125">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="fac08-125">List card</span></span>](#list-card) | <span data-ttu-id="fac08-126">Uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="fac08-126">A scrolling list of items.</span></span> |
| [<span data-ttu-id="fac08-127">Cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="fac08-127">Office 365 connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="fac08-128">Layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="fac08-128">Flexible layout with multiple sections, fields, images and actions.</span></span> |
| [<span data-ttu-id="fac08-129">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="fac08-129">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="fac08-130">Fornece um recibo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="fac08-130">Provides a receipt to the user.</span></span> |
| [<span data-ttu-id="fac08-131">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="fac08-131">Signin card</span></span>](#signin-card) | <span data-ttu-id="fac08-132">Permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="fac08-132">Enables a bot to request that a user sign in.</span></span> |
| [<span data-ttu-id="fac08-133">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="fac08-133">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="fac08-134">Normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões.</span><span class="sxs-lookup"><span data-stu-id="fac08-134">Typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="fac08-135">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="fac08-135">Card collections</span></span>](#card-collections) | <span data-ttu-id="fac08-136">Usado para retornar vários itens em uma única resposta.</span><span class="sxs-lookup"><span data-stu-id="fac08-136">Used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="fac08-137">Propriedades comuns para todos os cartões</span><span class="sxs-lookup"><span data-stu-id="fac08-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="fac08-138">Imagens de cartão em linha</span><span class="sxs-lookup"><span data-stu-id="fac08-138">Inline card images</span></span>

<span data-ttu-id="fac08-139">O cartão pode conter uma imagem em linha incluindo um link para a imagem disponível publicamente.</span><span class="sxs-lookup"><span data-stu-id="fac08-139">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="fac08-140">Para fins de desempenho, é altamente recomendável hospedar a imagem em uma CDN (rede pública de distribuição de conteúdo).</span><span class="sxs-lookup"><span data-stu-id="fac08-140">For performance purposes, it is highly recommended you host the image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="fac08-141">As imagens são dimensionados para cima ou para baixo em tamanho, mantendo a taxa de proporção para cobrir a área da imagem e, em seguida, cortadas do centro para obter a proporção apropriada para o cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="fac08-142">As imagens devem ter no máximo 1024×1024, no formato PNG, JPEG ou GIF e GIF animado não são suportados.</span><span class="sxs-lookup"><span data-stu-id="fac08-142">Images must be at most 1024×1024, in PNG, JPEG, or GIF format, and animated GIF is not supported.</span></span>

| <span data-ttu-id="fac08-143">Propriedade</span><span class="sxs-lookup"><span data-stu-id="fac08-143">Property</span></span> | <span data-ttu-id="fac08-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="fac08-144">Type</span></span>  | <span data-ttu-id="fac08-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="fac08-145">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="fac08-146">url</span><span class="sxs-lookup"><span data-stu-id="fac08-146">url</span></span> | <span data-ttu-id="fac08-147">URL</span><span class="sxs-lookup"><span data-stu-id="fac08-147">URL</span></span> | <span data-ttu-id="fac08-148">URL HTTPS para a imagem</span><span class="sxs-lookup"><span data-stu-id="fac08-148">HTTPS URL to the image</span></span> |
| <span data-ttu-id="fac08-149">alt</span><span class="sxs-lookup"><span data-stu-id="fac08-149">alt</span></span> | <span data-ttu-id="fac08-150">String</span><span class="sxs-lookup"><span data-stu-id="fac08-150">String</span></span> | <span data-ttu-id="fac08-151">Descrição acessível da imagem</span><span class="sxs-lookup"><span data-stu-id="fac08-151">Accessible description of the image</span></span> |

### <a name="buttons"></a><span data-ttu-id="fac08-152">Botões</span><span class="sxs-lookup"><span data-stu-id="fac08-152">Buttons</span></span>

<span data-ttu-id="fac08-153">Os botões são mostrados empilhados na parte inferior do cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-153">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="fac08-154">O texto do botão está sempre em uma única linha e será truncado se o texto exceder a largura do botão.</span><span class="sxs-lookup"><span data-stu-id="fac08-154">Button text is always on a single line and will be truncated if the text exceeds the button width.</span></span> <span data-ttu-id="fac08-155">Quaisquer botões adicionais além do número máximo suportado pelo cartão não serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="fac08-155">Any additional buttons beyond the maximum number supported by the card will not be shown.</span></span>

<span data-ttu-id="fac08-156">Consulte [Ações de Cartão](~/task-modules-and-cards/cards/cards-actions.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="fac08-156">See [Card Actions](~/task-modules-and-cards/cards/cards-actions.md) for more information.</span></span>

### <a name="card-formatting"></a><span data-ttu-id="fac08-157">Formatação de cartão</span><span class="sxs-lookup"><span data-stu-id="fac08-157">Card formatting</span></span>

<span data-ttu-id="fac08-158">Consulte [Formatação de Cartão](~/task-modules-and-cards/cards/cards-format.md) para obter mais informações sobre formatação de texto em cartões.</span><span class="sxs-lookup"><span data-stu-id="fac08-158">See [Card Formatting](~/task-modules-and-cards/cards/cards-format.md) for more information on text formatting in cards.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="fac08-159">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="fac08-159">Adaptive card</span></span>

<span data-ttu-id="fac08-160">Um cartão adaptável é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="fac08-160">An adaptive card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="fac08-161">Consulte [Cartões Adaptáveis v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="fac08-161">See [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="fac08-162">Suporte para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="fac08-162">Support for adaptive cards</span></span>

| <span data-ttu-id="fac08-163">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="fac08-163">Bots in Teams</span></span> | <span data-ttu-id="fac08-164">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-164">Messaging extensions</span></span>  | <span data-ttu-id="fac08-165">Conectores</span><span class="sxs-lookup"><span data-stu-id="fac08-165">Connectors</span></span> | <span data-ttu-id="fac08-166">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="fac08-166">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="fac08-167">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-167">✔</span></span> | <span data-ttu-id="fac08-168">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-168">✔</span></span> | <span data-ttu-id="fac08-169">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-169">✖</span></span> | <span data-ttu-id="fac08-170">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-170">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="fac08-171">A plataforma teams dá suporte a v1.2 ou anterior a recursos de cartão adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="fac08-171">Teams platform supports v1.2 or earlier of Adaptive card features.</span></span>
> * <span data-ttu-id="fac08-172">Os elementos de mídia atualmente não têm suporte no cartão adaptável v1.2 na plataforma teams.</span><span class="sxs-lookup"><span data-stu-id="fac08-172">Media elements are currently not supported in Adaptive card v1.2 on the Teams platform.</span></span>

### <a name="example-of-an-adaptive-card"></a><span data-ttu-id="fac08-173">Exemplo de um cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="fac08-173">Example of an adaptive card</span></span>

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

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="fac08-175">Informações adicionais sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="fac08-175">Additional information on adaptive cards</span></span>

<span data-ttu-id="fac08-176">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="fac08-176">Bot Framework reference:</span></span>

* [<span data-ttu-id="fac08-177">Nó de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="fac08-177">Adaptive cards Node</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="fac08-178">Cartão adaptável C #</span><span class="sxs-lookup"><span data-stu-id="fac08-178">Adaptive card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

## <a name="hero-card"></a><span data-ttu-id="fac08-179">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="fac08-179">Hero card</span></span>

<span data-ttu-id="fac08-180">Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="fac08-180">A card that typically contains a single large image, one or more buttons and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="fac08-181">Suporte para cartões de herói</span><span class="sxs-lookup"><span data-stu-id="fac08-181">Support for hero cards</span></span>

| <span data-ttu-id="fac08-182">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="fac08-182">Bots in Teams</span></span> | <span data-ttu-id="fac08-183">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-183">Messaging Extensions</span></span>  | <span data-ttu-id="fac08-184">Conectores</span><span class="sxs-lookup"><span data-stu-id="fac08-184">Connectors</span></span> | <span data-ttu-id="fac08-185">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="fac08-185">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="fac08-186">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-186">✔</span></span> | <span data-ttu-id="fac08-187">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-187">✔</span></span> | <span data-ttu-id="fac08-188">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-188">✖</span></span> | <span data-ttu-id="fac08-189">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-189">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="fac08-190">Propriedades de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="fac08-190">Properties of a hero card</span></span>

| <span data-ttu-id="fac08-191">Propriedade</span><span class="sxs-lookup"><span data-stu-id="fac08-191">Property</span></span> | <span data-ttu-id="fac08-192">Tipo</span><span class="sxs-lookup"><span data-stu-id="fac08-192">Type</span></span>  | <span data-ttu-id="fac08-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="fac08-193">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="fac08-194">title</span><span class="sxs-lookup"><span data-stu-id="fac08-194">title</span></span> | <span data-ttu-id="fac08-195">Rich text </span><span class="sxs-lookup"><span data-stu-id="fac08-195">Rich text</span></span> | <span data-ttu-id="fac08-196">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-196">Title of the card.</span></span> <span data-ttu-id="fac08-197">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="fac08-197">Maximum 2 lines.</span></span> |
| <span data-ttu-id="fac08-198">subtitle</span><span class="sxs-lookup"><span data-stu-id="fac08-198">subtitle</span></span> | <span data-ttu-id="fac08-199">Rich text </span><span class="sxs-lookup"><span data-stu-id="fac08-199">Rich text</span></span> | <span data-ttu-id="fac08-200">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-200">Subtitle of the card.</span></span> <span data-ttu-id="fac08-201">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="fac08-201">Maximum 2 lines.</span></span>|
| <span data-ttu-id="fac08-202">texto</span><span class="sxs-lookup"><span data-stu-id="fac08-202">text</span></span> | <span data-ttu-id="fac08-203">Rich text </span><span class="sxs-lookup"><span data-stu-id="fac08-203">Rich text</span></span> | <span data-ttu-id="fac08-204">O texto é exibido sob o subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação.</span><span class="sxs-lookup"><span data-stu-id="fac08-204">Text appears under the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="fac08-205">images</span><span class="sxs-lookup"><span data-stu-id="fac08-205">images</span></span> | <span data-ttu-id="fac08-206">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="fac08-206">Array of images</span></span> | <span data-ttu-id="fac08-207">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-207">Image displayed at top of card.</span></span> <span data-ttu-id="fac08-208">Taxa de proporção 16:9.</span><span class="sxs-lookup"><span data-stu-id="fac08-208">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="fac08-209">botões</span><span class="sxs-lookup"><span data-stu-id="fac08-209">buttons</span></span> | <span data-ttu-id="fac08-210">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="fac08-210">Array of action objects</span></span> | <span data-ttu-id="fac08-211">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="fac08-211">Set of actions applicable to the current card.</span></span> <span data-ttu-id="fac08-212">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="fac08-212">Maximum 6.</span></span> |
| <span data-ttu-id="fac08-213">tap</span><span class="sxs-lookup"><span data-stu-id="fac08-213">tap</span></span> | <span data-ttu-id="fac08-214">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="fac08-214">Action object</span></span> | <span data-ttu-id="fac08-215">Essa ação será ativada quando o usuário tocar no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-215">This action will be activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="fac08-216">Exemplo de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="fac08-216">Example of a hero card</span></span>

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

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="fac08-218">Informações adicionais sobre cartões de herói</span><span class="sxs-lookup"><span data-stu-id="fac08-218">Additional information on hero cards</span></span>

<span data-ttu-id="fac08-219">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="fac08-219">Bot Framework reference:</span></span>

* [<span data-ttu-id="fac08-220">Nó de cartão de herói</span><span class="sxs-lookup"><span data-stu-id="fac08-220">Hero card Node</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="fac08-221">Cartão de herói C #</span><span class="sxs-lookup"><span data-stu-id="fac08-221">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="fac08-222">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="fac08-222">List card</span></span>

<span data-ttu-id="fac08-223">O cartão de listagem foi adicionado pelo Teams para fornecer funções além do que a coleção de listas pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="fac08-223">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="fac08-224">O cartão de listagem fornece uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="fac08-224">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="fac08-225">Suporte para cartões de lista</span><span class="sxs-lookup"><span data-stu-id="fac08-225">Support for list cards</span></span>

| <span data-ttu-id="fac08-226">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="fac08-226">Bots in Teams</span></span> | <span data-ttu-id="fac08-227">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-227">Messaging extensions</span></span>  | <span data-ttu-id="fac08-228">Conectores</span><span class="sxs-lookup"><span data-stu-id="fac08-228">Connectors</span></span> | <span data-ttu-id="fac08-229">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="fac08-229">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="fac08-230">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-230">✔</span></span> | <span data-ttu-id="fac08-231">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-231">✖</span></span> | <span data-ttu-id="fac08-232">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-232">✖</span></span> |<span data-ttu-id="fac08-233">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-233">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="fac08-234">Propriedades de um cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="fac08-234">Properties of a list card</span></span>

| <span data-ttu-id="fac08-235">Propriedade</span><span class="sxs-lookup"><span data-stu-id="fac08-235">Property</span></span> | <span data-ttu-id="fac08-236">Tipo</span><span class="sxs-lookup"><span data-stu-id="fac08-236">Type</span></span>  | <span data-ttu-id="fac08-237">Descrição</span><span class="sxs-lookup"><span data-stu-id="fac08-237">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="fac08-238">title</span><span class="sxs-lookup"><span data-stu-id="fac08-238">title</span></span> | <span data-ttu-id="fac08-239">Rich text </span><span class="sxs-lookup"><span data-stu-id="fac08-239">Rich text</span></span> | <span data-ttu-id="fac08-240">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-240">Title of the card.</span></span> <span data-ttu-id="fac08-241">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="fac08-241">Maximum 2 lines.</span></span>|
| <span data-ttu-id="fac08-242">items</span><span class="sxs-lookup"><span data-stu-id="fac08-242">items</span></span> | <span data-ttu-id="fac08-243">Matriz de itens de lista</span><span class="sxs-lookup"><span data-stu-id="fac08-243">Array of list items</span></span>  ||
| <span data-ttu-id="fac08-244">botões</span><span class="sxs-lookup"><span data-stu-id="fac08-244">buttons</span></span> | <span data-ttu-id="fac08-245">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="fac08-245">Array of action objects</span></span> | <span data-ttu-id="fac08-246">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="fac08-246">Set of actions applicable to the current card.</span></span> <span data-ttu-id="fac08-247">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="fac08-247">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="fac08-248">Exemplo de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="fac08-248">Example of a list card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="fac08-249">Cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="fac08-249">Office 365 connector card</span></span>

<span data-ttu-id="fac08-250">O cartão conector do Office 365 tem suporte no Teams, não na Estrutura de Bots.</span><span class="sxs-lookup"><span data-stu-id="fac08-250">The Office 365 Connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="fac08-251">Este cartão fornece um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="fac08-251">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="fac08-252">Esse cartão encapsula um cartão de conector para que ele possa ser usado por bots.</span><span class="sxs-lookup"><span data-stu-id="fac08-252">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="fac08-253">Consulte a seção anotações para saber as diferenças entre cartões de conector e o cartão O365.</span><span class="sxs-lookup"><span data-stu-id="fac08-253">See the notes section for differences between connector cards and the O365 card.</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="fac08-254">Suporte para cartões de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="fac08-254">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="fac08-255">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="fac08-255">Bots in Teams</span></span> | <span data-ttu-id="fac08-256">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-256">Messaging extensions</span></span>  | <span data-ttu-id="fac08-257">Conectores</span><span class="sxs-lookup"><span data-stu-id="fac08-257">Connectors</span></span> | <span data-ttu-id="fac08-258">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="fac08-258">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="fac08-259">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-259">✔</span></span> | <span data-ttu-id="fac08-260">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-260">✔</span></span> | <span data-ttu-id="fac08-261">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-261">✔</span></span> | <span data-ttu-id="fac08-262">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-262">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="fac08-263">Propriedades do cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="fac08-263">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="fac08-264">Propriedade</span><span class="sxs-lookup"><span data-stu-id="fac08-264">Property</span></span> | <span data-ttu-id="fac08-265">Tipo</span><span class="sxs-lookup"><span data-stu-id="fac08-265">Type</span></span>  | <span data-ttu-id="fac08-266">Descrição</span><span class="sxs-lookup"><span data-stu-id="fac08-266">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="fac08-267">title</span><span class="sxs-lookup"><span data-stu-id="fac08-267">title</span></span> | <span data-ttu-id="fac08-268">Rich text </span><span class="sxs-lookup"><span data-stu-id="fac08-268">Rich text</span></span> | <span data-ttu-id="fac08-269">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-269">Title of the card.</span></span> <span data-ttu-id="fac08-270">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="fac08-270">Maximum 2 lines.</span></span> |
| <span data-ttu-id="fac08-271">summary</span><span class="sxs-lookup"><span data-stu-id="fac08-271">summary</span></span> | <span data-ttu-id="fac08-272">Rich text </span><span class="sxs-lookup"><span data-stu-id="fac08-272">Rich text</span></span> | <span data-ttu-id="fac08-273">Resumo do cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-273">Summary of the card.</span></span> <span data-ttu-id="fac08-274">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="fac08-274">Maximum 2 lines.</span></span> |
| <span data-ttu-id="fac08-275">texto</span><span class="sxs-lookup"><span data-stu-id="fac08-275">text</span></span> | <span data-ttu-id="fac08-276">Rich text </span><span class="sxs-lookup"><span data-stu-id="fac08-276">Rich text</span></span> | <span data-ttu-id="fac08-277">O texto é exibido sob o subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação.</span><span class="sxs-lookup"><span data-stu-id="fac08-277">Text appears under the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="fac08-278">themeColor</span><span class="sxs-lookup"><span data-stu-id="fac08-278">themeColor</span></span> | <span data-ttu-id="fac08-279">Cadeia de caracteres HEX</span><span class="sxs-lookup"><span data-stu-id="fac08-279">HEX string</span></span> | <span data-ttu-id="fac08-280">Cor que substitui o accentColor fornecido do manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fac08-280">Color that overrides the accentColor provided from the application manifest.</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="fac08-281">Observações sobre o cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="fac08-281">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="fac08-282">Os cartões conectores do Office 365 funcionam corretamente no Microsoft Teams, incluindo [ações do ActionCard.](/outlook/actionable-messages/card-reference#actioncard-action)</span><span class="sxs-lookup"><span data-stu-id="fac08-282">Office 365 connector cards function properly in Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="fac08-283">Uma diferença importante entre o uso de cartões conectores de um conector e o uso de cartões de conector no bot é o tratamento de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-283">One important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="fac08-284">Para um conector, o ponto de extremidade recebe a carga de cartão por meio de HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="fac08-284">For a connector, the endpoint receives the card payload through HTTP POST.</span></span>
* <span data-ttu-id="fac08-285">Para um bot, a ação dispara uma atividade que envia apenas a ID de ação `HttpPOST` e o corpo para o `invoke` bot.</span><span class="sxs-lookup"><span data-stu-id="fac08-285">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="fac08-286">Cada cartão de conector pode exibir no máximo 10 seções, e cada seção pode conter no máximo 5 imagens e 5 ações.</span><span class="sxs-lookup"><span data-stu-id="fac08-286">Each connector card can display a maximum of 10 sections, and each section can contain a maximum of 5 images and 5 actions.</span></span>

> [!NOTE]
> <span data-ttu-id="fac08-287">Quaisquer seções, imagens ou ações adicionais em uma mensagem não serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="fac08-287">Any additional sections, images, or actions in a message will not appear.</span></span>

<span data-ttu-id="fac08-288">Todos os campos de texto suportam Markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="fac08-288">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="fac08-289">Você pode controlar quais seções usam Markdown ou HTML definindo `markdown` a propriedade em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="fac08-289">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="fac08-290">Por padrão, é definido como ; se você quiser usar HTML em vez `markdown` `true` disso, de definida `markdown` como `false` .</span><span class="sxs-lookup"><span data-stu-id="fac08-290">By default, `markdown` is set to `true`; if you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="fac08-291">Se você especificar a `themeColor` propriedade, ela substituirá `accentColor` a propriedade no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fac08-291">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="fac08-292">Para especificar o estilo de renderização `activityImage` para , você pode definir da seguinte `activityImageType` forma:</span><span class="sxs-lookup"><span data-stu-id="fac08-292">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows:</span></span>

| <span data-ttu-id="fac08-293">Valor</span><span class="sxs-lookup"><span data-stu-id="fac08-293">Value</span></span> | <span data-ttu-id="fac08-294">Descrição</span><span class="sxs-lookup"><span data-stu-id="fac08-294">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="fac08-295">Padrão; `activityImage` será cortada como um círculo.</span><span class="sxs-lookup"><span data-stu-id="fac08-295">Default; `activityImage` will be cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="fac08-296">`activityImage` será exibido como um retângulo e manterá sua taxa de proporção.</span><span class="sxs-lookup"><span data-stu-id="fac08-296">`activityImage` will be displayed as a rectangle and retain its aspect ratio.</span></span> |

<span data-ttu-id="fac08-297">Para obter todos os outros detalhes sobre as propriedades do cartão do conector, consulte a referência de cartão de mensagem a [actionable](/outlook/actionable-messages/card-reference).</span><span class="sxs-lookup"><span data-stu-id="fac08-297">For all other details about connector card properties, see the [Actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="fac08-298">As únicas propriedades de cartão de conector que o Microsoft Teams não dá suporte no momento são as seguinte:</span><span class="sxs-lookup"><span data-stu-id="fac08-298">The only connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="fac08-299">`startGroup` (sempre tratado como `true` no Teams)</span><span class="sxs-lookup"><span data-stu-id="fac08-299">`startGroup` (always treated as `true` in Teams)</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="fac08-300">Exemplo de um cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="fac08-300">Example of an Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="fac08-301">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="fac08-301">Receipt card</span></span>

<span data-ttu-id="fac08-302">O Teams dá suporte ao cartão de confirmação.</span><span class="sxs-lookup"><span data-stu-id="fac08-302">Teams supports receipt card.</span></span> <span data-ttu-id="fac08-303">É um cartão que permite que um bot forneça um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="fac08-303">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="fac08-304">Normalmente, ele contém a lista de itens a ser incluídos no recibo, como informações fiscais e totais.</span><span class="sxs-lookup"><span data-stu-id="fac08-304">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="fac08-305">Suporte para cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="fac08-305">Support for receipt cards</span></span>

| <span data-ttu-id="fac08-306">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="fac08-306">Bots in Teams</span></span> | <span data-ttu-id="fac08-307">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-307">Messaging extensions</span></span>  | <span data-ttu-id="fac08-308">Conectores</span><span class="sxs-lookup"><span data-stu-id="fac08-308">Connectors</span></span> | <span data-ttu-id="fac08-309">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="fac08-309">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="fac08-310">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-310">✔</span></span> | <span data-ttu-id="fac08-311">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-311">✔</span></span> | <span data-ttu-id="fac08-312">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-312">✖</span></span> | <span data-ttu-id="fac08-313">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-313">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="fac08-314">Exemplo de um cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="fac08-314">Example of a receipt card</span></span>

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

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="fac08-316">Informações adicionais sobre cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="fac08-316">Additional information on receipt cards</span></span>

<span data-ttu-id="fac08-317">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="fac08-317">Bot Framework reference:</span></span>

* [<span data-ttu-id="fac08-318">Nó do cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="fac08-318">Receipt card Node</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="fac08-319">Cartão de recebimento C #</span><span class="sxs-lookup"><span data-stu-id="fac08-319">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="fac08-320">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="fac08-320">Signin card</span></span>

<span data-ttu-id="fac08-321">O cartão de login permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="fac08-321">Signin card enables a bot to request a user to sign in.</span></span> <span data-ttu-id="fac08-322">Suportado no Teams de uma forma ligeiramente diferente da encontrada na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="fac08-322">Supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="fac08-323">O cartão de signin no Teams é semelhante ao cartão de assinatura na Estrutura de Bot, exceto pelo fato de o cartão de inscrição no Teams dar suporte apenas a duas ações: `signin` e `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="fac08-323">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="fac08-324">A **ação de signin** pode ser usada de qualquer cartão no Teams, não apenas o cartão de assinatura.</span><span class="sxs-lookup"><span data-stu-id="fac08-324">The **signin action** can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="fac08-325">Para obter mais detalhes sobre autenticação, consulte Fluxo de [autenticação do Microsoft Teams para bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="fac08-325">For more details on authentication, see [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="fac08-326">Suporte para cartões Signin</span><span class="sxs-lookup"><span data-stu-id="fac08-326">Support for Signin cards</span></span>

| <span data-ttu-id="fac08-327">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="fac08-327">Bots in Teams</span></span> | <span data-ttu-id="fac08-328">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-328">Messaging extensions</span></span>  | <span data-ttu-id="fac08-329">Conectores</span><span class="sxs-lookup"><span data-stu-id="fac08-329">Connectors</span></span> | <span data-ttu-id="fac08-330">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="fac08-330">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="fac08-331">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-331">✔</span></span> | <span data-ttu-id="fac08-332">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-332">✖</span></span> | <span data-ttu-id="fac08-333">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-333">✖</span></span> | <span data-ttu-id="fac08-334">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-334">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="fac08-335">Informações adicionais sobre cartões de assinatura</span><span class="sxs-lookup"><span data-stu-id="fac08-335">Additional information on signin cards</span></span>

<span data-ttu-id="fac08-336">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="fac08-336">Bot Framework reference:</span></span>

* [<span data-ttu-id="fac08-337">Nó de cartão de signin</span><span class="sxs-lookup"><span data-stu-id="fac08-337">Signin card Node</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="fac08-338">Signin card C #</span><span class="sxs-lookup"><span data-stu-id="fac08-338">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="fac08-339">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="fac08-339">Thumbnail card</span></span>

<span data-ttu-id="fac08-340">Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="fac08-340">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="fac08-341">Suporte para cartões de miniatura</span><span class="sxs-lookup"><span data-stu-id="fac08-341">Support for thumbnail cards</span></span>

| <span data-ttu-id="fac08-342">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="fac08-342">Bots in Teams</span></span> | <span data-ttu-id="fac08-343">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-343">Messaging extensions</span></span>  | <span data-ttu-id="fac08-344">Conectores</span><span class="sxs-lookup"><span data-stu-id="fac08-344">Connectors</span></span> | <span data-ttu-id="fac08-345">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="fac08-345">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="fac08-346">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-346">✔</span></span> | <span data-ttu-id="fac08-347">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-347">✔</span></span> | <span data-ttu-id="fac08-348">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-348">✖</span></span> | <span data-ttu-id="fac08-349">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-349">✔</span></span> |

![Exemplo de um cartão de miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="fac08-351">Propriedades de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="fac08-351">Properties of a thumbnail card</span></span>

| <span data-ttu-id="fac08-352">Propriedade</span><span class="sxs-lookup"><span data-stu-id="fac08-352">Property</span></span> | <span data-ttu-id="fac08-353">Tipo</span><span class="sxs-lookup"><span data-stu-id="fac08-353">Type</span></span>  | <span data-ttu-id="fac08-354">Descrição</span><span class="sxs-lookup"><span data-stu-id="fac08-354">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="fac08-355">title</span><span class="sxs-lookup"><span data-stu-id="fac08-355">title</span></span> | <span data-ttu-id="fac08-356">Rich text </span><span class="sxs-lookup"><span data-stu-id="fac08-356">Rich text</span></span> | <span data-ttu-id="fac08-357">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-357">Title of the card.</span></span> <span data-ttu-id="fac08-358">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="fac08-358">Maximum 2 lines.</span></span>|
| <span data-ttu-id="fac08-359">subtitle</span><span class="sxs-lookup"><span data-stu-id="fac08-359">subtitle</span></span> | <span data-ttu-id="fac08-360">Rich text </span><span class="sxs-lookup"><span data-stu-id="fac08-360">Rich text</span></span> | <span data-ttu-id="fac08-361">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-361">Subtitle of the card.</span></span> <span data-ttu-id="fac08-362">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="fac08-362">Maximum 2 lines.</span></span>|
| <span data-ttu-id="fac08-363">texto</span><span class="sxs-lookup"><span data-stu-id="fac08-363">text</span></span> | <span data-ttu-id="fac08-364">Rich text </span><span class="sxs-lookup"><span data-stu-id="fac08-364">Rich text</span></span> | <span data-ttu-id="fac08-365">O texto é exibido sob o subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação.</span><span class="sxs-lookup"><span data-stu-id="fac08-365">Text appears under the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="fac08-366">images</span><span class="sxs-lookup"><span data-stu-id="fac08-366">images</span></span> | <span data-ttu-id="fac08-367">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="fac08-367">Array of images</span></span> | <span data-ttu-id="fac08-368">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-368">Image displayed at top of card.</span></span> <span data-ttu-id="fac08-369">Taxa de proporção 1:1 (quadrado).</span><span class="sxs-lookup"><span data-stu-id="fac08-369">Aspect ratio 1:1 (square).</span></span> |
| <span data-ttu-id="fac08-370">botões</span><span class="sxs-lookup"><span data-stu-id="fac08-370">buttons</span></span> | <span data-ttu-id="fac08-371">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="fac08-371">Array of action objects</span></span> | <span data-ttu-id="fac08-372">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="fac08-372">Set of actions applicable to the current card.</span></span> <span data-ttu-id="fac08-373">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="fac08-373">Maximum 6.</span></span> |
| <span data-ttu-id="fac08-374">tap</span><span class="sxs-lookup"><span data-stu-id="fac08-374">tap</span></span> | <span data-ttu-id="fac08-375">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="fac08-375">Action object</span></span> | <span data-ttu-id="fac08-376">Essa ação será ativada quando o usuário tocar no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="fac08-376">This action will be activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="fac08-377">Exemplo de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="fac08-377">Example of a thumbnail card</span></span>

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

### <a name="additional-information"></a><span data-ttu-id="fac08-378">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="fac08-378">Additional information</span></span>

<span data-ttu-id="fac08-379">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="fac08-379">Bot Framework reference:</span></span>

* [<span data-ttu-id="fac08-380">Nó do cartão thumbnail</span><span class="sxs-lookup"><span data-stu-id="fac08-380">Thumbnail card Node</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="fac08-381">Cartão de miniatura C #</span><span class="sxs-lookup"><span data-stu-id="fac08-381">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="fac08-382">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="fac08-382">Card collections</span></span>

<span data-ttu-id="fac08-383">O Teams dá suporte a coleções card.</span><span class="sxs-lookup"><span data-stu-id="fac08-383">Teams supports Card collections.</span></span>

<span data-ttu-id="fac08-384">Coleções de cartões: `builder.AttachmentLayout.carousel` e `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="fac08-384">Card collections: `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="fac08-385">Essas coleções contêm cartões adaptáveis, herois ou miniaturas.</span><span class="sxs-lookup"><span data-stu-id="fac08-385">These collections contain adaptive, hero, or thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="fac08-386">Coleção Carousel</span><span class="sxs-lookup"><span data-stu-id="fac08-386">Carousel collection</span></span>

<span data-ttu-id="fac08-387">O [layout do carrossel](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="fac08-387">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="fac08-388">Suporte para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="fac08-388">Support for carousel collections</span></span>

| <span data-ttu-id="fac08-389">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="fac08-389">Bots in Teams</span></span> | <span data-ttu-id="fac08-390">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-390">Messaging extensions</span></span>  | <span data-ttu-id="fac08-391">Conectores</span><span class="sxs-lookup"><span data-stu-id="fac08-391">Connectors</span></span> | <span data-ttu-id="fac08-392">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="fac08-392">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="fac08-393">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-393">✔</span></span> | <span data-ttu-id="fac08-394">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-394">✖</span></span> | <span data-ttu-id="fac08-395">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-395">✖</span></span> | <span data-ttu-id="fac08-396">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-396">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="fac08-397">Um carrossel pode exibir no máximo 10 cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="fac08-397">A carousel can display a maximum of 10 cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="fac08-398">Propriedades de um cartão de carrossel</span><span class="sxs-lookup"><span data-stu-id="fac08-398">Properties of a carousel card</span></span>

<span data-ttu-id="fac08-399">As propriedades de um cartão Carrossel são as mesmas das cartas Hero e Thumbnail.</span><span class="sxs-lookup"><span data-stu-id="fac08-399">Properties of a Carousel card are same as those of the Hero and Thumbnail cards.</span></span>

### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="fac08-400">Exemplo de uma coleção de carrossel</span><span class="sxs-lookup"><span data-stu-id="fac08-400">Example of a carousel collection</span></span>

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="fac08-402">Sintaxe para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="fac08-402">Syntax for carousel collections</span></span>

`builder.AttachmentLayoutTypes.Carousel`

## <a name="list-collection"></a><span data-ttu-id="fac08-403">Coleção List</span><span class="sxs-lookup"><span data-stu-id="fac08-403">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="fac08-404">Suporte para coleções de lista</span><span class="sxs-lookup"><span data-stu-id="fac08-404">Support for list collections</span></span>

<span data-ttu-id="fac08-405">O layout da lista mostra uma lista verticalmente empilhada de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="fac08-405">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="fac08-406">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="fac08-406">Bots in Teams</span></span> | <span data-ttu-id="fac08-407">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="fac08-407">Messaging extensions</span></span>  | <span data-ttu-id="fac08-408">Conectores</span><span class="sxs-lookup"><span data-stu-id="fac08-408">Connectors</span></span> | <span data-ttu-id="fac08-409">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="fac08-409">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="fac08-410">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-410">✔</span></span> | <span data-ttu-id="fac08-411">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-411">✔</span></span> | <span data-ttu-id="fac08-412">✖</span><span class="sxs-lookup"><span data-stu-id="fac08-412">✖</span></span> | <span data-ttu-id="fac08-413">✔</span><span class="sxs-lookup"><span data-stu-id="fac08-413">✔</span></span> |

### <a name="example-of-a-list-collection"></a><span data-ttu-id="fac08-414">Exemplo de uma coleção de listas</span><span class="sxs-lookup"><span data-stu-id="fac08-414">Example of a list collection</span></span>

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

<span data-ttu-id="fac08-416">As propriedades são as mesmas do cartão herói ou miniatura.</span><span class="sxs-lookup"><span data-stu-id="fac08-416">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="fac08-417">Uma lista pode exibir no máximo 10 cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="fac08-417">A list can display a maximum of 10 cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="fac08-418">Algumas combinações de cartões de lista ainda não são suportadas no iOS e no Android.</span><span class="sxs-lookup"><span data-stu-id="fac08-418">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="fac08-419">Sintaxe para coleções de lista</span><span class="sxs-lookup"><span data-stu-id="fac08-419">Syntax for list collections</span></span>

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="fac08-420">Cartões não suportados no Teams</span><span class="sxs-lookup"><span data-stu-id="fac08-420">Cards not supported in Teams</span></span>

<span data-ttu-id="fac08-421">Os cartões a seguir são implementados pela Estrutura de Bot, mas NÃO são suportados pelo Teams.</span><span class="sxs-lookup"><span data-stu-id="fac08-421">The following cards are implemented by the Bot Framework, but are NOT supported by Teams.</span></span>

* <span data-ttu-id="fac08-422">Cartões de animação</span><span class="sxs-lookup"><span data-stu-id="fac08-422">Animation cards</span></span>
* <span data-ttu-id="fac08-423">Cartões de áudio</span><span class="sxs-lookup"><span data-stu-id="fac08-423">Audio cards</span></span>
* <span data-ttu-id="fac08-424">Cartões de vídeo</span><span class="sxs-lookup"><span data-stu-id="fac08-424">Video cards</span></span>
