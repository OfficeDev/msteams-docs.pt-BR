---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Teams
keywords: referência de cartões de bots
ms.topic: reference
ms.openlocfilehash: 839430baa5ce5e8950a21a1472036c6fd96f4edf
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911889"
---
# <a name="cards-reference"></a><span data-ttu-id="b09ba-104">Referência de cartões</span><span class="sxs-lookup"><span data-stu-id="b09ba-104">Cards reference</span></span>

<span data-ttu-id="b09ba-105">Os cartões listados nesta seção têm suporte em bots para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="b09ba-105">The cards listed in this section are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="b09ba-106">Eles são baseados em cartões definidos pela Estrutura de Bot, mas o Teams não dá suporte a todos os cartões do Bot Framework e adicionou alguns de seus próprios cartões.</span><span class="sxs-lookup"><span data-stu-id="b09ba-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span> <span data-ttu-id="b09ba-107">Diferenças são destacadas nas referências neste documento.</span><span class="sxs-lookup"><span data-stu-id="b09ba-107">Differences are called out in the references in this document.</span></span>

## <a name="card-examples"></a><span data-ttu-id="b09ba-108">Exemplos de cartão</span><span class="sxs-lookup"><span data-stu-id="b09ba-108">Card examples</span></span>

<span data-ttu-id="b09ba-109">Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do Construtor de Bots (v3).</span><span class="sxs-lookup"><span data-stu-id="b09ba-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK (v3).</span></span> <span data-ttu-id="b09ba-110">Exemplos de código também estão disponíveis no repositório Microsoft/BotBuilder-Samples no GitHub.</span><span class="sxs-lookup"><span data-stu-id="b09ba-110">Code samples are also available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="b09ba-111">.NET</span><span class="sxs-lookup"><span data-stu-id="b09ba-111">.NET</span></span>
  * [<span data-ttu-id="b09ba-112">Adicionar cartões como anexos a mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-112">Add cards as attachments to messages</span></span>](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [<span data-ttu-id="b09ba-113">Código de exemplo de cartões (Construtor de Bots v3)</span><span class="sxs-lookup"><span data-stu-id="b09ba-113">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/CSharp/cards-RichCards)
* <span data-ttu-id="b09ba-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="b09ba-114">Node.js</span></span>
  * [<span data-ttu-id="b09ba-115">Adicionar cartões como anexos a mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-115">Add cards as attachments to messages</span></span>](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [<span data-ttu-id="b09ba-116">Código de exemplo de cartões (Construtor de Bots v3)</span><span class="sxs-lookup"><span data-stu-id="b09ba-116">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/Node/cards-RichCards)

## <a name="types-of-cards"></a><span data-ttu-id="b09ba-117">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="b09ba-117">Types of cards</span></span>

<span data-ttu-id="b09ba-118">Esta tabela mostra os tipos de cartões disponíveis para você:</span><span class="sxs-lookup"><span data-stu-id="b09ba-118">This table shows the types of cards available to you:</span></span>

| <span data-ttu-id="b09ba-119">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="b09ba-119">Card type</span></span> | <span data-ttu-id="b09ba-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b09ba-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="b09ba-121">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="b09ba-121">Adaptive card</span></span>](#adaptive-card) | <span data-ttu-id="b09ba-122">Cartão altamente personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="b09ba-122">Highly customizable card that can contain any combination of text, speech, images, buttons and input fields.</span></span> |
| [<span data-ttu-id="b09ba-123">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="b09ba-123">Hero card</span></span>](#hero-card) | <span data-ttu-id="b09ba-124">Normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="b09ba-124">Typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="b09ba-125">Cartão de lista</span><span class="sxs-lookup"><span data-stu-id="b09ba-125">List card</span></span>](#list-card) | <span data-ttu-id="b09ba-126">Uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="b09ba-126">A scrolling list of items.</span></span> |
| [<span data-ttu-id="b09ba-127">Cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="b09ba-127">Office 365 connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="b09ba-128">Layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="b09ba-128">Flexible layout with multiple sections, fields, images and actions.</span></span> |
| [<span data-ttu-id="b09ba-129">Cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="b09ba-129">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="b09ba-130">Fornece um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="b09ba-130">Provides a receipt to the user.</span></span> |
| [<span data-ttu-id="b09ba-131">Signin card</span><span class="sxs-lookup"><span data-stu-id="b09ba-131">Signin card</span></span>](#signin-card) | <span data-ttu-id="b09ba-132">Permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="b09ba-132">Enables a bot to request that a user sign in.</span></span> |
| [<span data-ttu-id="b09ba-133">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="b09ba-133">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="b09ba-134">Normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões.</span><span class="sxs-lookup"><span data-stu-id="b09ba-134">Typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="b09ba-135">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="b09ba-135">Card collections</span></span>](#card-collections) | <span data-ttu-id="b09ba-136">Usado para retornar vários itens em uma única resposta.</span><span class="sxs-lookup"><span data-stu-id="b09ba-136">Used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="b09ba-137">Propriedades comuns para todos os cartões</span><span class="sxs-lookup"><span data-stu-id="b09ba-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="b09ba-138">Imagens de cartão em linha</span><span class="sxs-lookup"><span data-stu-id="b09ba-138">Inline card images</span></span>

<span data-ttu-id="b09ba-139">O cartão pode conter uma imagem em linha incluindo um link para a imagem publicamente disponível.</span><span class="sxs-lookup"><span data-stu-id="b09ba-139">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="b09ba-140">Para fins de desempenho, é altamente recomendável que você hospede a imagem em uma CDN (rede pública de distribuição de conteúdo).</span><span class="sxs-lookup"><span data-stu-id="b09ba-140">For performance purposes, it is highly recommended you host the image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="b09ba-141">As imagens são dimensionados para cima ou para baixo em tamanho, mantendo a taxa de proporção para cobrir a área da imagem e, em seguida, cortadas do centro para obter a taxa de proporção apropriada para o cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="b09ba-142">As imagens devem ter, no máximo, 1024×1024, em formato PNG, JPEG ou GIF, e GIF animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="b09ba-142">Images must be at most 1024×1024, in PNG, JPEG, or GIF format, and animated GIF is not supported.</span></span>

| <span data-ttu-id="b09ba-143">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b09ba-143">Property</span></span> | <span data-ttu-id="b09ba-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="b09ba-144">Type</span></span>  | <span data-ttu-id="b09ba-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="b09ba-145">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b09ba-146">url</span><span class="sxs-lookup"><span data-stu-id="b09ba-146">url</span></span> | <span data-ttu-id="b09ba-147">URL</span><span class="sxs-lookup"><span data-stu-id="b09ba-147">URL</span></span> | <span data-ttu-id="b09ba-148">URL HTTPS para a imagem</span><span class="sxs-lookup"><span data-stu-id="b09ba-148">HTTPS URL to the image</span></span> |
| <span data-ttu-id="b09ba-149">alt</span><span class="sxs-lookup"><span data-stu-id="b09ba-149">alt</span></span> | <span data-ttu-id="b09ba-150">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b09ba-150">String</span></span> | <span data-ttu-id="b09ba-151">Descrição acessível da imagem</span><span class="sxs-lookup"><span data-stu-id="b09ba-151">Accessible description of the image</span></span> |

### <a name="buttons"></a><span data-ttu-id="b09ba-152">Botões</span><span class="sxs-lookup"><span data-stu-id="b09ba-152">Buttons</span></span>

<span data-ttu-id="b09ba-153">Os botões são mostrados empilhados na parte inferior do cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-153">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="b09ba-154">O texto do botão está sempre em uma única linha e será truncado se o texto exceder a largura do botão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-154">Button text is always on a single line and will be truncated if the text exceeds the button width.</span></span> <span data-ttu-id="b09ba-155">Quaisquer botões adicionais além do número máximo suportado pelo cartão não serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="b09ba-155">Any additional buttons beyond the maximum number supported by the card will not be shown.</span></span>

<span data-ttu-id="b09ba-156">Consulte [Ações do Cartão](~/task-modules-and-cards/cards/cards-actions.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b09ba-156">See [Card Actions](~/task-modules-and-cards/cards/cards-actions.md) for more information.</span></span>

### <a name="card-formatting"></a><span data-ttu-id="b09ba-157">Formatação de cartão</span><span class="sxs-lookup"><span data-stu-id="b09ba-157">Card formatting</span></span>

<span data-ttu-id="b09ba-158">Consulte [Formatação de Cartão](~/task-modules-and-cards/cards/cards-format.md) para obter mais informações sobre formatação de texto em cartões.</span><span class="sxs-lookup"><span data-stu-id="b09ba-158">See [Card Formatting](~/task-modules-and-cards/cards/cards-format.md) for more information on text formatting in cards.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="b09ba-159">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="b09ba-159">Adaptive card</span></span>

<span data-ttu-id="b09ba-160">Um cartão adaptável é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="b09ba-160">An adaptive card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="b09ba-161">Consulte [Cartões Adaptáveis v1.2.0.](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0)</span><span class="sxs-lookup"><span data-stu-id="b09ba-161">See [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="b09ba-162">Suporte para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="b09ba-162">Support for adaptive cards</span></span>

| <span data-ttu-id="b09ba-163">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-163">Bots in Teams</span></span> | <span data-ttu-id="b09ba-164">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-164">Messaging extensions</span></span>  | <span data-ttu-id="b09ba-165">Conectores</span><span class="sxs-lookup"><span data-stu-id="b09ba-165">Connectors</span></span> | <span data-ttu-id="b09ba-166">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b09ba-166">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b09ba-167">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-167">✔</span></span> | <span data-ttu-id="b09ba-168">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-168">✔</span></span> | <span data-ttu-id="b09ba-169">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-169">✖</span></span> | <span data-ttu-id="b09ba-170">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-170">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="b09ba-171">A plataforma do Teams é compatível com a versão 1.2 ou anterior dos recursos de cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="b09ba-171">Teams platform supports v1.2 or earlier of Adaptive card features.</span></span>
> * <span data-ttu-id="b09ba-172">Atualmente, os elementos de mídia não têm suporte no cartão adaptável v1.2 na plataforma do Teams.</span><span class="sxs-lookup"><span data-stu-id="b09ba-172">Media elements are currently not supported in Adaptive card v1.2 on the Teams platform.</span></span>

### <a name="example-of-an-adaptive-card"></a><span data-ttu-id="b09ba-173">Exemplo de um cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="b09ba-173">Example of an adaptive card</span></span>

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

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="b09ba-175">Informações adicionais sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="b09ba-175">Additional information on adaptive cards</span></span>

* [<span data-ttu-id="b09ba-176">Visão geral dos cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="b09ba-176">Adaptive cards overview</span></span>](/adaptive-cards/)
* [<span data-ttu-id="b09ba-177">Ações de cartão adaptáveis no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-177">Adaptive card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)

## <a name="hero-card"></a><span data-ttu-id="b09ba-178">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="b09ba-178">Hero card</span></span>

<span data-ttu-id="b09ba-179">Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="b09ba-179">A card that typically contains a single large image, one or more buttons and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="b09ba-180">Suporte para cartões de herói</span><span class="sxs-lookup"><span data-stu-id="b09ba-180">Support for hero cards</span></span>

| <span data-ttu-id="b09ba-181">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-181">Bots in Teams</span></span> | <span data-ttu-id="b09ba-182">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-182">Messaging Extensions</span></span>  | <span data-ttu-id="b09ba-183">Conectores</span><span class="sxs-lookup"><span data-stu-id="b09ba-183">Connectors</span></span> | <span data-ttu-id="b09ba-184">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b09ba-184">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b09ba-185">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-185">✔</span></span> | <span data-ttu-id="b09ba-186">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-186">✔</span></span> | <span data-ttu-id="b09ba-187">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-187">✖</span></span> | <span data-ttu-id="b09ba-188">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-188">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="b09ba-189">Propriedades de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="b09ba-189">Properties of a hero card</span></span>

| <span data-ttu-id="b09ba-190">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b09ba-190">Property</span></span> | <span data-ttu-id="b09ba-191">Tipo</span><span class="sxs-lookup"><span data-stu-id="b09ba-191">Type</span></span>  | <span data-ttu-id="b09ba-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="b09ba-192">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b09ba-193">title</span><span class="sxs-lookup"><span data-stu-id="b09ba-193">title</span></span> | <span data-ttu-id="b09ba-194">Rich text </span><span class="sxs-lookup"><span data-stu-id="b09ba-194">Rich text</span></span> | <span data-ttu-id="b09ba-195">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-195">Title of the card.</span></span> <span data-ttu-id="b09ba-196">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="b09ba-196">Maximum 2 lines.</span></span> |
| <span data-ttu-id="b09ba-197">subtitle</span><span class="sxs-lookup"><span data-stu-id="b09ba-197">subtitle</span></span> | <span data-ttu-id="b09ba-198">Rich text </span><span class="sxs-lookup"><span data-stu-id="b09ba-198">Rich text</span></span> | <span data-ttu-id="b09ba-199">Subtítulo do cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-199">Subtitle of the card.</span></span> <span data-ttu-id="b09ba-200">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="b09ba-200">Maximum 2 lines.</span></span>|
| <span data-ttu-id="b09ba-201">texto</span><span class="sxs-lookup"><span data-stu-id="b09ba-201">text</span></span> | <span data-ttu-id="b09ba-202">Rich text </span><span class="sxs-lookup"><span data-stu-id="b09ba-202">Rich text</span></span> | <span data-ttu-id="b09ba-203">O texto aparece logo abaixo do subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação.</span><span class="sxs-lookup"><span data-stu-id="b09ba-203">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="b09ba-204">images</span><span class="sxs-lookup"><span data-stu-id="b09ba-204">images</span></span> | <span data-ttu-id="b09ba-205">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-205">Array of images</span></span> | <span data-ttu-id="b09ba-206">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-206">Image displayed at top of card.</span></span> <span data-ttu-id="b09ba-207">Taxa de proporção 16:9.</span><span class="sxs-lookup"><span data-stu-id="b09ba-207">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="b09ba-208">buttons</span><span class="sxs-lookup"><span data-stu-id="b09ba-208">buttons</span></span> | <span data-ttu-id="b09ba-209">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="b09ba-209">Array of action objects</span></span> | <span data-ttu-id="b09ba-210">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="b09ba-210">Set of actions applicable to the current card.</span></span> <span data-ttu-id="b09ba-211">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="b09ba-211">Maximum 6.</span></span> |
| <span data-ttu-id="b09ba-212">tocar</span><span class="sxs-lookup"><span data-stu-id="b09ba-212">tap</span></span> | <span data-ttu-id="b09ba-213">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="b09ba-213">Action object</span></span> | <span data-ttu-id="b09ba-214">Essa ação será ativada quando o usuário tocar no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-214">This action will be activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="b09ba-215">Exemplo de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="b09ba-215">Example of a hero card</span></span>

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

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="b09ba-217">Informações adicionais sobre cartões de herói</span><span class="sxs-lookup"><span data-stu-id="b09ba-217">Additional information on hero cards</span></span>

<span data-ttu-id="b09ba-218">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="b09ba-218">Bot Framework reference:</span></span>

* [<span data-ttu-id="b09ba-219">Nó de cartão de herói</span><span class="sxs-lookup"><span data-stu-id="b09ba-219">Hero card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/herocard)
* [<span data-ttu-id="b09ba-220">Cartão de herói C #</span><span class="sxs-lookup"><span data-stu-id="b09ba-220">Hero card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.herocard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="b09ba-221">Cartão de lista</span><span class="sxs-lookup"><span data-stu-id="b09ba-221">List card</span></span>

<span data-ttu-id="b09ba-222">O cartão de lista foi adicionado pelo Teams para fornecer funções além do que a coleção de listas pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="b09ba-222">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="b09ba-223">O cartão de lista fornece uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="b09ba-223">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="b09ba-224">Suporte para cartões de lista</span><span class="sxs-lookup"><span data-stu-id="b09ba-224">Support for list cards</span></span>

| <span data-ttu-id="b09ba-225">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-225">Bots in Teams</span></span> | <span data-ttu-id="b09ba-226">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-226">Messaging extensions</span></span>  | <span data-ttu-id="b09ba-227">Conectores</span><span class="sxs-lookup"><span data-stu-id="b09ba-227">Connectors</span></span> | <span data-ttu-id="b09ba-228">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b09ba-228">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b09ba-229">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-229">✔</span></span> | <span data-ttu-id="b09ba-230">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-230">✖</span></span> | <span data-ttu-id="b09ba-231">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-231">✖</span></span> |<span data-ttu-id="b09ba-232">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-232">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="b09ba-233">Propriedades de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="b09ba-233">Properties of a list card</span></span>

| <span data-ttu-id="b09ba-234">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b09ba-234">Property</span></span> | <span data-ttu-id="b09ba-235">Tipo</span><span class="sxs-lookup"><span data-stu-id="b09ba-235">Type</span></span>  | <span data-ttu-id="b09ba-236">Descrição</span><span class="sxs-lookup"><span data-stu-id="b09ba-236">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b09ba-237">title</span><span class="sxs-lookup"><span data-stu-id="b09ba-237">title</span></span> | <span data-ttu-id="b09ba-238">Rich text </span><span class="sxs-lookup"><span data-stu-id="b09ba-238">Rich text</span></span> | <span data-ttu-id="b09ba-239">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-239">Title of the card.</span></span> <span data-ttu-id="b09ba-240">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="b09ba-240">Maximum 2 lines.</span></span>|
| <span data-ttu-id="b09ba-241">items</span><span class="sxs-lookup"><span data-stu-id="b09ba-241">items</span></span> | <span data-ttu-id="b09ba-242">Matriz de itens de lista</span><span class="sxs-lookup"><span data-stu-id="b09ba-242">Array of list items</span></span>  ||
| <span data-ttu-id="b09ba-243">buttons</span><span class="sxs-lookup"><span data-stu-id="b09ba-243">buttons</span></span> | <span data-ttu-id="b09ba-244">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="b09ba-244">Array of action objects</span></span> | <span data-ttu-id="b09ba-245">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="b09ba-245">Set of actions applicable to the current card.</span></span> <span data-ttu-id="b09ba-246">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="b09ba-246">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="b09ba-247">Exemplo de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="b09ba-247">Example of a list card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="b09ba-248">Cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="b09ba-248">Office 365 connector card</span></span>

<span data-ttu-id="b09ba-249">O cartão do Conector do Office 365 é compatível com o Teams, não no Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="b09ba-249">The Office 365 Connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="b09ba-250">Este cartão fornece um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="b09ba-250">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="b09ba-251">Esse cartão encapsula um cartão de conector para que ele possa ser usado por bots.</span><span class="sxs-lookup"><span data-stu-id="b09ba-251">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="b09ba-252">Consulte a seção de observações para ver as diferenças entre cartões de conector e o cartão O365.</span><span class="sxs-lookup"><span data-stu-id="b09ba-252">See the notes section for differences between connector cards and the O365 card.</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="b09ba-253">Suporte para cartões de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="b09ba-253">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="b09ba-254">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-254">Bots in Teams</span></span> | <span data-ttu-id="b09ba-255">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-255">Messaging extensions</span></span>  | <span data-ttu-id="b09ba-256">Conectores</span><span class="sxs-lookup"><span data-stu-id="b09ba-256">Connectors</span></span> | <span data-ttu-id="b09ba-257">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b09ba-257">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b09ba-258">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-258">✔</span></span> | <span data-ttu-id="b09ba-259">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-259">✔</span></span> | <span data-ttu-id="b09ba-260">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-260">✔</span></span> | <span data-ttu-id="b09ba-261">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-261">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="b09ba-262">Propriedades do cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="b09ba-262">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="b09ba-263">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b09ba-263">Property</span></span> | <span data-ttu-id="b09ba-264">Tipo</span><span class="sxs-lookup"><span data-stu-id="b09ba-264">Type</span></span>  | <span data-ttu-id="b09ba-265">Descrição</span><span class="sxs-lookup"><span data-stu-id="b09ba-265">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b09ba-266">title</span><span class="sxs-lookup"><span data-stu-id="b09ba-266">title</span></span> | <span data-ttu-id="b09ba-267">Rich text </span><span class="sxs-lookup"><span data-stu-id="b09ba-267">Rich text</span></span> | <span data-ttu-id="b09ba-268">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-268">Title of the card.</span></span> <span data-ttu-id="b09ba-269">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="b09ba-269">Maximum 2 lines.</span></span> |
| <span data-ttu-id="b09ba-270">summary</span><span class="sxs-lookup"><span data-stu-id="b09ba-270">summary</span></span> | <span data-ttu-id="b09ba-271">Rich text </span><span class="sxs-lookup"><span data-stu-id="b09ba-271">Rich text</span></span> | <span data-ttu-id="b09ba-272">Resumo do cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-272">Summary of the card.</span></span> <span data-ttu-id="b09ba-273">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="b09ba-273">Maximum 2 lines.</span></span> |
| <span data-ttu-id="b09ba-274">texto</span><span class="sxs-lookup"><span data-stu-id="b09ba-274">text</span></span> | <span data-ttu-id="b09ba-275">Rich text </span><span class="sxs-lookup"><span data-stu-id="b09ba-275">Rich text</span></span> | <span data-ttu-id="b09ba-276">O texto aparece logo abaixo do subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação.</span><span class="sxs-lookup"><span data-stu-id="b09ba-276">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="b09ba-277">themeColor</span><span class="sxs-lookup"><span data-stu-id="b09ba-277">themeColor</span></span> | <span data-ttu-id="b09ba-278">Cadeia de caracteres HEX</span><span class="sxs-lookup"><span data-stu-id="b09ba-278">HEX string</span></span> | <span data-ttu-id="b09ba-279">Cor que substitui a accentColor fornecida do manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b09ba-279">Color that overrides the accentColor provided from the application manifest.</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="b09ba-280">Observações sobre o cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="b09ba-280">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="b09ba-281">Cartões de conector do Office 365 funcionam corretamente no Microsoft Teams, incluindo [ações actionCard](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="b09ba-281">Office 365 connector cards function properly in Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="b09ba-282">Uma diferença importante entre usar cartões de conector de um conector e usar cartões de conector em seu bot é o tratamento de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-282">One important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="b09ba-283">Para um conector, o ponto de extremidade recebe a carga do cartão via HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="b09ba-283">For a connector, the endpoint receives the card payload via HTTP POST.</span></span>
* <span data-ttu-id="b09ba-284">Para um bot, a ação dispara uma atividade que envia apenas a ID de ação `HttpPOST` e o corpo para o `invoke` bot.</span><span class="sxs-lookup"><span data-stu-id="b09ba-284">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="b09ba-285">Cada cartão de conector pode exibir no máximo 10 seções, e cada seção pode conter no máximo 5 imagens e 5 ações.</span><span class="sxs-lookup"><span data-stu-id="b09ba-285">Each connector card can display a maximum of 10 sections, and each section can contain a maximum of 5 images and 5 actions.</span></span>

> [!NOTE]
> <span data-ttu-id="b09ba-286">Quaisquer seções, imagens ou ações adicionais em uma mensagem não serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="b09ba-286">Any additional sections, images, or actions in a message will not appear.</span></span>

<span data-ttu-id="b09ba-287">Todos os campos de texto suportam Markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="b09ba-287">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="b09ba-288">Você pode controlar quais seções usam Markdown ou HTML definindo `markdown` a propriedade em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="b09ba-288">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="b09ba-289">Por padrão, `markdown` é definido como ; se você quiser usar HTML em vez `true` disso, de definida como `markdown` `false` .</span><span class="sxs-lookup"><span data-stu-id="b09ba-289">By default, `markdown` is set to `true`; if you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="b09ba-290">Se você especificar a `themeColor` propriedade, ela substituirá `accentColor` a propriedade no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b09ba-290">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="b09ba-291">Para especificar o estilo de `activityImage` renderização, você pode definir `activityImageType` da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="b09ba-291">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows:</span></span>

| <span data-ttu-id="b09ba-292">Valor</span><span class="sxs-lookup"><span data-stu-id="b09ba-292">Value</span></span> | <span data-ttu-id="b09ba-293">Descrição</span><span class="sxs-lookup"><span data-stu-id="b09ba-293">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="b09ba-294">Padrão; `activityImage` será cortada como um círculo.</span><span class="sxs-lookup"><span data-stu-id="b09ba-294">Default; `activityImage` will be cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="b09ba-295">`activityImage` será exibido como um retângulo e manterá sua taxa de proporção.</span><span class="sxs-lookup"><span data-stu-id="b09ba-295">`activityImage` will be displayed as a rectangle and retain its aspect ratio.</span></span> |

<span data-ttu-id="b09ba-296">Para obter todos os outros detalhes sobre as propriedades do cartão do conector, consulte a referência [de cartão de mensagem a actionable.](/outlook/actionable-messages/card-reference)</span><span class="sxs-lookup"><span data-stu-id="b09ba-296">For all other details about connector card properties, see the [Actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="b09ba-297">As únicas propriedades de cartão de conector que o Microsoft Teams não dá suporte no momento são as seguinte:</span><span class="sxs-lookup"><span data-stu-id="b09ba-297">The only connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="b09ba-298">`startGroup` (sempre tratado como `true` no Teams)</span><span class="sxs-lookup"><span data-stu-id="b09ba-298">`startGroup` (always treated as `true` in Teams)</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="b09ba-299">Exemplo de um cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="b09ba-299">Example of an Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="b09ba-300">Cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="b09ba-300">Receipt card</span></span>

<span data-ttu-id="b09ba-301">O Teams dá suporte ao cartão de confirmação.</span><span class="sxs-lookup"><span data-stu-id="b09ba-301">Teams supports receipt card.</span></span> <span data-ttu-id="b09ba-302">É um cartão que permite que um bot forneça um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="b09ba-302">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="b09ba-303">Normalmente, ele contém a lista de itens a incluir no recibo, como imposto e informações totais.</span><span class="sxs-lookup"><span data-stu-id="b09ba-303">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="b09ba-304">Suporte para cartões de confirmação</span><span class="sxs-lookup"><span data-stu-id="b09ba-304">Support for receipt cards</span></span>

| <span data-ttu-id="b09ba-305">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-305">Bots in Teams</span></span> | <span data-ttu-id="b09ba-306">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-306">Messaging extensions</span></span>  | <span data-ttu-id="b09ba-307">Conectores</span><span class="sxs-lookup"><span data-stu-id="b09ba-307">Connectors</span></span> | <span data-ttu-id="b09ba-308">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b09ba-308">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b09ba-309">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-309">✔</span></span> | <span data-ttu-id="b09ba-310">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-310">✔</span></span> | <span data-ttu-id="b09ba-311">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-311">✖</span></span> | <span data-ttu-id="b09ba-312">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-312">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="b09ba-313">Exemplo de um cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="b09ba-313">Example of a receipt card</span></span>

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

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="b09ba-315">Informações adicionais sobre cartões de confirmação</span><span class="sxs-lookup"><span data-stu-id="b09ba-315">Additional information on receipt cards</span></span>

<span data-ttu-id="b09ba-316">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="b09ba-316">Bot Framework reference:</span></span>

* [<span data-ttu-id="b09ba-317">Nó do cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="b09ba-317">Receipt card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="b09ba-318">Cartão de confirmação C #</span><span class="sxs-lookup"><span data-stu-id="b09ba-318">Receipt card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.receiptcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="b09ba-319">Signin card</span><span class="sxs-lookup"><span data-stu-id="b09ba-319">Signin card</span></span>

<span data-ttu-id="b09ba-320">O cartão de acesso permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="b09ba-320">Signin card enables a bot to request a user to sign in.</span></span> <span data-ttu-id="b09ba-321">Com suporte no Teams de uma forma ligeiramente diferente da encontrada na Estrutura do Bot.</span><span class="sxs-lookup"><span data-stu-id="b09ba-321">Supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="b09ba-322">O cartão de login no Teams é semelhante ao cartão de login na Estrutura do Bot, exceto pelo fato de que o cartão de login no Teams só dá suporte a duas ações: `signin` e `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="b09ba-322">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="b09ba-323">A *ação de entrar* pode ser usada em qualquer cartão no Teams, não apenas no cartão de visita.</span><span class="sxs-lookup"><span data-stu-id="b09ba-323">The *signin action* can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="b09ba-324">Para obter mais detalhes sobre autenticação, confira [o fluxo de autenticação do Microsoft Teams para bots.](~/bots/how-to/authentication/auth-flow-bot.md)</span><span class="sxs-lookup"><span data-stu-id="b09ba-324">For more details on authentication, see [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="b09ba-325">Suporte para cartões de login</span><span class="sxs-lookup"><span data-stu-id="b09ba-325">Support for Signin cards</span></span>

| <span data-ttu-id="b09ba-326">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-326">Bots in Teams</span></span> | <span data-ttu-id="b09ba-327">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-327">Messaging extensions</span></span>  | <span data-ttu-id="b09ba-328">Conectores</span><span class="sxs-lookup"><span data-stu-id="b09ba-328">Connectors</span></span> | <span data-ttu-id="b09ba-329">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b09ba-329">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b09ba-330">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-330">✔</span></span> | <span data-ttu-id="b09ba-331">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-331">✖</span></span> | <span data-ttu-id="b09ba-332">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-332">✖</span></span> | <span data-ttu-id="b09ba-333">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-333">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="b09ba-334">Informações adicionais sobre cartões de assinatura</span><span class="sxs-lookup"><span data-stu-id="b09ba-334">Additional information on signin cards</span></span>

<span data-ttu-id="b09ba-335">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="b09ba-335">Bot Framework reference:</span></span>

* [<span data-ttu-id="b09ba-336">Nó do cartão de conexão</span><span class="sxs-lookup"><span data-stu-id="b09ba-336">Signin card Node</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="b09ba-337">Signin card C #</span><span class="sxs-lookup"><span data-stu-id="b09ba-337">Signin card C#</span></span>](/dotnet/api/microsoft.bot.connector.signincard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="b09ba-338">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="b09ba-338">Thumbnail card</span></span>

<span data-ttu-id="b09ba-339">Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="b09ba-339">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="b09ba-340">Suporte para cartões de miniatura</span><span class="sxs-lookup"><span data-stu-id="b09ba-340">Support for thumbnail cards</span></span>

| <span data-ttu-id="b09ba-341">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-341">Bots in Teams</span></span> | <span data-ttu-id="b09ba-342">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-342">Messaging extensions</span></span>  | <span data-ttu-id="b09ba-343">Conectores</span><span class="sxs-lookup"><span data-stu-id="b09ba-343">Connectors</span></span> | <span data-ttu-id="b09ba-344">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b09ba-344">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b09ba-345">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-345">✔</span></span> | <span data-ttu-id="b09ba-346">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-346">✔</span></span> | <span data-ttu-id="b09ba-347">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-347">✖</span></span> | <span data-ttu-id="b09ba-348">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-348">✔</span></span> |

![Exemplo de um cartão em miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="b09ba-350">Propriedades de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="b09ba-350">Properties of a thumbnail card</span></span>

| <span data-ttu-id="b09ba-351">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b09ba-351">Property</span></span> | <span data-ttu-id="b09ba-352">Tipo</span><span class="sxs-lookup"><span data-stu-id="b09ba-352">Type</span></span>  | <span data-ttu-id="b09ba-353">Descrição</span><span class="sxs-lookup"><span data-stu-id="b09ba-353">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b09ba-354">title</span><span class="sxs-lookup"><span data-stu-id="b09ba-354">title</span></span> | <span data-ttu-id="b09ba-355">Rich text </span><span class="sxs-lookup"><span data-stu-id="b09ba-355">Rich text</span></span> | <span data-ttu-id="b09ba-356">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-356">Title of the card.</span></span> <span data-ttu-id="b09ba-357">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="b09ba-357">Maximum 2 lines.</span></span>|
| <span data-ttu-id="b09ba-358">subtitle</span><span class="sxs-lookup"><span data-stu-id="b09ba-358">subtitle</span></span> | <span data-ttu-id="b09ba-359">Rich text </span><span class="sxs-lookup"><span data-stu-id="b09ba-359">Rich text</span></span> | <span data-ttu-id="b09ba-360">Subtítulo do cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-360">Subtitle of the card.</span></span> <span data-ttu-id="b09ba-361">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="b09ba-361">Maximum 2 lines.</span></span>|
| <span data-ttu-id="b09ba-362">texto</span><span class="sxs-lookup"><span data-stu-id="b09ba-362">text</span></span> | <span data-ttu-id="b09ba-363">Rich text </span><span class="sxs-lookup"><span data-stu-id="b09ba-363">Rich text</span></span> | <span data-ttu-id="b09ba-364">O texto aparece logo abaixo do subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação.</span><span class="sxs-lookup"><span data-stu-id="b09ba-364">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="b09ba-365">images</span><span class="sxs-lookup"><span data-stu-id="b09ba-365">images</span></span> | <span data-ttu-id="b09ba-366">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-366">Array of images</span></span> | <span data-ttu-id="b09ba-367">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-367">Image displayed at top of card.</span></span> <span data-ttu-id="b09ba-368">Taxa de proporção 1:1 (quadrado).</span><span class="sxs-lookup"><span data-stu-id="b09ba-368">Aspect ratio 1:1 (square).</span></span> |
| <span data-ttu-id="b09ba-369">buttons</span><span class="sxs-lookup"><span data-stu-id="b09ba-369">buttons</span></span> | <span data-ttu-id="b09ba-370">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="b09ba-370">Array of action objects</span></span> | <span data-ttu-id="b09ba-371">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="b09ba-371">Set of actions applicable to the current card.</span></span> <span data-ttu-id="b09ba-372">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="b09ba-372">Maximum 6.</span></span> |
| <span data-ttu-id="b09ba-373">tocar</span><span class="sxs-lookup"><span data-stu-id="b09ba-373">tap</span></span> | <span data-ttu-id="b09ba-374">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="b09ba-374">Action object</span></span> | <span data-ttu-id="b09ba-375">Essa ação será ativada quando o usuário tocar no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="b09ba-375">This action will be activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="b09ba-376">Exemplo de um cartão em miniatura</span><span class="sxs-lookup"><span data-stu-id="b09ba-376">Example of a thumbnail card</span></span>

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

### <a name="additional-information"></a><span data-ttu-id="b09ba-377">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="b09ba-377">Additional information</span></span>

<span data-ttu-id="b09ba-378">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="b09ba-378">Bot Framework reference:</span></span>

* [<span data-ttu-id="b09ba-379">Nó do cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="b09ba-379">Thumbnail card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="b09ba-380">Cartão de miniatura C #</span><span class="sxs-lookup"><span data-stu-id="b09ba-380">Thumbnail card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.thumbnailcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="b09ba-381">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="b09ba-381">Card collections</span></span>

<span data-ttu-id="b09ba-382">O Teams dá suporte a coleções de cartões.</span><span class="sxs-lookup"><span data-stu-id="b09ba-382">Teams supports Card collections.</span></span>

<span data-ttu-id="b09ba-383">Coleções de cartões: `builder.AttachmentLayout.carousel` e `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="b09ba-383">Card collections: `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="b09ba-384">Essas coleções contêm cartões adaptáveis, em forma de herói ou em miniatura.</span><span class="sxs-lookup"><span data-stu-id="b09ba-384">These collections contain adaptive, hero, or thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="b09ba-385">Coleção Carousel</span><span class="sxs-lookup"><span data-stu-id="b09ba-385">Carousel collection</span></span>

<span data-ttu-id="b09ba-386">O [layout do carrossel](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="b09ba-386">The [carousel layout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="b09ba-387">Suporte para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="b09ba-387">Support for carousel collections</span></span>

| <span data-ttu-id="b09ba-388">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-388">Bots in Teams</span></span> | <span data-ttu-id="b09ba-389">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-389">Messaging extensions</span></span>  | <span data-ttu-id="b09ba-390">Conectores</span><span class="sxs-lookup"><span data-stu-id="b09ba-390">Connectors</span></span> | <span data-ttu-id="b09ba-391">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b09ba-391">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b09ba-392">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-392">✔</span></span> | <span data-ttu-id="b09ba-393">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-393">✖</span></span> | <span data-ttu-id="b09ba-394">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-394">✖</span></span> | <span data-ttu-id="b09ba-395">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-395">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="b09ba-396">Um carrossel pode exibir no máximo 10 cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="b09ba-396">A carousel can display a maximum of 10 cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="b09ba-397">Propriedades de um cartão de carrossel</span><span class="sxs-lookup"><span data-stu-id="b09ba-397">Properties of a carousel card</span></span>

<span data-ttu-id="b09ba-398">As propriedades de um cartão carrossel são iguais às dos cartões Hero e Thumbnail.</span><span class="sxs-lookup"><span data-stu-id="b09ba-398">Properties of a Carousel card are same as those of the Hero and Thumbnail cards.</span></span>

### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="b09ba-399">Exemplo de uma coleção de carrossel</span><span class="sxs-lookup"><span data-stu-id="b09ba-399">Example of a carousel collection</span></span>

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="b09ba-401">Sintaxe para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="b09ba-401">Syntax for carousel collections</span></span>

`builder.AttachmentLayoutTypes.Carousel`

## <a name="list-collection"></a><span data-ttu-id="b09ba-402">Listar coleção</span><span class="sxs-lookup"><span data-stu-id="b09ba-402">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="b09ba-403">Suporte para coleções de listas</span><span class="sxs-lookup"><span data-stu-id="b09ba-403">Support for list collections</span></span>

<span data-ttu-id="b09ba-404">O layout da lista mostra uma lista de cartões empilhados verticalmente, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="b09ba-404">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="b09ba-405">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-405">Bots in Teams</span></span> | <span data-ttu-id="b09ba-406">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="b09ba-406">Messaging extensions</span></span>  | <span data-ttu-id="b09ba-407">Conectores</span><span class="sxs-lookup"><span data-stu-id="b09ba-407">Connectors</span></span> | <span data-ttu-id="b09ba-408">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b09ba-408">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b09ba-409">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-409">✔</span></span> | <span data-ttu-id="b09ba-410">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-410">✔</span></span> | <span data-ttu-id="b09ba-411">✖</span><span class="sxs-lookup"><span data-stu-id="b09ba-411">✖</span></span> | <span data-ttu-id="b09ba-412">✔</span><span class="sxs-lookup"><span data-stu-id="b09ba-412">✔</span></span> |

### <a name="example-of-a-list-collection"></a><span data-ttu-id="b09ba-413">Exemplo de uma coleção de listas</span><span class="sxs-lookup"><span data-stu-id="b09ba-413">Example of a list collection</span></span>

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

<span data-ttu-id="b09ba-415">As propriedades são iguais às do herói ou da miniatura.</span><span class="sxs-lookup"><span data-stu-id="b09ba-415">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="b09ba-416">Uma lista pode exibir no máximo 10 cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="b09ba-416">A list can display a maximum of 10 cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="b09ba-417">Algumas combinações de cartões de lista ainda não têm suporte no iOS e no Android.</span><span class="sxs-lookup"><span data-stu-id="b09ba-417">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="b09ba-418">Sintaxe para coleções de listas</span><span class="sxs-lookup"><span data-stu-id="b09ba-418">Syntax for list collections</span></span>

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="b09ba-419">Cartões não suportados no Teams</span><span class="sxs-lookup"><span data-stu-id="b09ba-419">Cards not supported in Teams</span></span>

<span data-ttu-id="b09ba-420">Os cartões a seguir são implementados pela Estrutura de Bot, mas NÃO são suportados pelo Teams.</span><span class="sxs-lookup"><span data-stu-id="b09ba-420">The following cards are implemented by the Bot Framework, but are NOT supported by Teams.</span></span>

* <span data-ttu-id="b09ba-421">Cartões de animação</span><span class="sxs-lookup"><span data-stu-id="b09ba-421">Animation cards</span></span>
* <span data-ttu-id="b09ba-422">Cartões de áudio</span><span class="sxs-lookup"><span data-stu-id="b09ba-422">Audio cards</span></span>
* <span data-ttu-id="b09ba-423">Placas de vídeo</span><span class="sxs-lookup"><span data-stu-id="b09ba-423">Video cards</span></span>
