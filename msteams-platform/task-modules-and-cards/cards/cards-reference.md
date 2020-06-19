---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Microsoft Teams
keywords: referência de cartões de bots
ms.openlocfilehash: 9cd868e504e426cbe56ed1c5d05c8e6adc1e1ddf
ms.sourcegitcommit: 61edf47c9dd1dbc1df03d0d9fb83bfedca4c423b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "44800980"
---
# <a name="cards-reference"></a><span data-ttu-id="776f8-104">Referência de cartões</span><span class="sxs-lookup"><span data-stu-id="776f8-104">Cards Reference</span></span>

<span data-ttu-id="776f8-105">Os cartões listados nesta seção têm suporte em bots para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="776f8-105">The cards listed in this section are supported in bots for Teams.</span></span> <span data-ttu-id="776f8-106">Eles são baseados em cartões definidos pela estrutura de bot, mas o Microsoft Teams não dá suporte a todas as placas de estrutura de bot e adicionou alguns dos seus próprios.</span><span class="sxs-lookup"><span data-stu-id="776f8-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span> <span data-ttu-id="776f8-107">As diferenças são chamadas nas referências abaixo.</span><span class="sxs-lookup"><span data-stu-id="776f8-107">Differences are called out in the references below.</span></span>

## <a name="card-examples"></a><span data-ttu-id="776f8-108">Exemplos de cartões</span><span class="sxs-lookup"><span data-stu-id="776f8-108">Card examples</span></span>

<span data-ttu-id="776f8-109">Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do bot Builder (v3).</span><span class="sxs-lookup"><span data-stu-id="776f8-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK (v3).</span></span> <span data-ttu-id="776f8-110">Há também exemplos de código disponíveis no repositório do Microsoft/BotBuilder-Samples no GitHub.</span><span class="sxs-lookup"><span data-stu-id="776f8-110">There are also code samples available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="776f8-111">.NET</span><span class="sxs-lookup"><span data-stu-id="776f8-111">.NET</span></span>
  * [<span data-ttu-id="776f8-112">Adicionar cartões como anexos a mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-112">Add cards as attachments to messages</span></span>](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [<span data-ttu-id="776f8-113">Código de exemplo de cartões (Construtor de bot v3)</span><span class="sxs-lookup"><span data-stu-id="776f8-113">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/CSharp/cards-RichCards)
* <span data-ttu-id="776f8-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="776f8-114">Node.js</span></span>
  * [<span data-ttu-id="776f8-115">Adicionar cartões como anexos a mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-115">Add cards as attachments to messages</span></span>](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [<span data-ttu-id="776f8-116">Código de exemplo de cartões (Construtor de bot v3)</span><span class="sxs-lookup"><span data-stu-id="776f8-116">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/Node/cards-RichCards)

## <a name="types-of-cards"></a><span data-ttu-id="776f8-117">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="776f8-117">Types of cards</span></span>

<span data-ttu-id="776f8-118">Esta tabela mostra os tipos de cartões disponíveis para você.</span><span class="sxs-lookup"><span data-stu-id="776f8-118">This table shows the types of cards available to you.</span></span>

| <span data-ttu-id="776f8-119">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="776f8-119">Card Type</span></span> | <span data-ttu-id="776f8-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="776f8-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="776f8-121">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="776f8-121">Adaptive Card</span></span>](#adaptive-card) | <span data-ttu-id="776f8-122">Cartão altamente personalizável que pode conter qualquer combinação de texto, voz, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="776f8-122">Highly customizable card that can contain any combination of text, speech, images, buttons and input fields.</span></span> |
| [<span data-ttu-id="776f8-123">Cartão herói</span><span class="sxs-lookup"><span data-stu-id="776f8-123">Hero Card</span></span>](#hero-card) | <span data-ttu-id="776f8-124">Normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="776f8-124">Typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="776f8-125">Cartão de lista</span><span class="sxs-lookup"><span data-stu-id="776f8-125">List Card</span></span>](#list-card) | <span data-ttu-id="776f8-126">Uma lista de rolagem dos itens.</span><span class="sxs-lookup"><span data-stu-id="776f8-126">A scrolling list of items.</span></span> |
| [<span data-ttu-id="776f8-127">Cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="776f8-127">Office 365 Connector Card</span></span>](#office-365-connector-card) | <span data-ttu-id="776f8-128">Layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="776f8-128">Flexible layout with multiple sections, fields, images and actions.</span></span> |
| [<span data-ttu-id="776f8-129">Cartão de recibo</span><span class="sxs-lookup"><span data-stu-id="776f8-129">Receipt Card</span></span>](#receipt-card) | <span data-ttu-id="776f8-130">Fornece um recibo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="776f8-130">Provides a receipt to the user.</span></span> |
| [<span data-ttu-id="776f8-131">Cartão de conexão</span><span class="sxs-lookup"><span data-stu-id="776f8-131">Signin Card</span></span>](#signin-card) | <span data-ttu-id="776f8-132">Permite que um bot solicite a entrada de um usuário.</span><span class="sxs-lookup"><span data-stu-id="776f8-132">Enables a bot to request that a user sign in.</span></span> |
| [<span data-ttu-id="776f8-133">Cartão de miniaturas</span><span class="sxs-lookup"><span data-stu-id="776f8-133">Thumbnail Card</span></span>](#thumbnail-card) | <span data-ttu-id="776f8-134">Normalmente contém uma única imagem em miniatura, um texto curto e um ou mais botões.</span><span class="sxs-lookup"><span data-stu-id="776f8-134">Typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="776f8-135">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="776f8-135">Card Collections</span></span>](#card-collections) | <span data-ttu-id="776f8-136">Usado para retornar vários itens em uma única resposta</span><span class="sxs-lookup"><span data-stu-id="776f8-136">Used to return multiple items in a single response</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="776f8-137">Propriedades comuns de todos os cartões</span><span class="sxs-lookup"><span data-stu-id="776f8-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="776f8-138">Imagens de cartões embutidos</span><span class="sxs-lookup"><span data-stu-id="776f8-138">Inline card images</span></span>

<span data-ttu-id="776f8-139">Seu cartão pode conter uma imagem embutida, incluindo um link para a imagem publicamente disponível.</span><span class="sxs-lookup"><span data-stu-id="776f8-139">Your card can contain an inline image by including a link to your publicly available image.</span></span> <span data-ttu-id="776f8-140">Para fins de desempenho, recomendamos enfaticamente que você hospede sua imagem em uma CDN (rede de distribuição de conteúdo) pública.</span><span class="sxs-lookup"><span data-stu-id="776f8-140">For performance purposes we highly recommend you host your image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="776f8-141">As imagens são dimensionadas para cima ou para baixo em tamanho, mantendo a taxa de proporção para cobrir a área da imagem e, em seguida, cortadas do centro para obter a taxa de proporção apropriada para o cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="776f8-142">As imagens devem ter no máximo 1024 × 1024 e 1 MB no formato PNG, JPEG ou GIF; GIF animado não é oficialmente suportado.</span><span class="sxs-lookup"><span data-stu-id="776f8-142">Images must be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF is not officially supported.</span></span>

| <span data-ttu-id="776f8-143">Propriedade</span><span class="sxs-lookup"><span data-stu-id="776f8-143">Property</span></span> | <span data-ttu-id="776f8-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="776f8-144">Type</span></span>  | <span data-ttu-id="776f8-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="776f8-145">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="776f8-146">url</span><span class="sxs-lookup"><span data-stu-id="776f8-146">url</span></span> | <span data-ttu-id="776f8-147">URL</span><span class="sxs-lookup"><span data-stu-id="776f8-147">URL</span></span> | <span data-ttu-id="776f8-148">URL HTTPS para a imagem</span><span class="sxs-lookup"><span data-stu-id="776f8-148">HTTPS URL to the image</span></span> |
| <span data-ttu-id="776f8-149">alt</span><span class="sxs-lookup"><span data-stu-id="776f8-149">alt</span></span> | <span data-ttu-id="776f8-150">String</span><span class="sxs-lookup"><span data-stu-id="776f8-150">String</span></span> | <span data-ttu-id="776f8-151">Descrição acessível da imagem</span><span class="sxs-lookup"><span data-stu-id="776f8-151">Accessible description of the image</span></span> |

### <a name="buttons"></a><span data-ttu-id="776f8-152">Botões</span><span class="sxs-lookup"><span data-stu-id="776f8-152">Buttons</span></span>

<span data-ttu-id="776f8-153">Os botões são exibidos empilhados na parte inferior do cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-153">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="776f8-154">O texto do botão está sempre em uma única linha e será truncado se o texto exceder a largura do botão.</span><span class="sxs-lookup"><span data-stu-id="776f8-154">Button text is always on a single line and will be truncated if the text exceeds the button width.</span></span> <span data-ttu-id="776f8-155">Qualquer outro botão além do número máximo suportado pelo cartão não será exibido.</span><span class="sxs-lookup"><span data-stu-id="776f8-155">Any additional buttons beyond the maximum number supported by the card will not be shown.</span></span>

<span data-ttu-id="776f8-156">Consulte [ações do cartão](~/task-modules-and-cards/cards/cards-actions.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="776f8-156">See [Card Actions](~/task-modules-and-cards/cards/cards-actions.md) for more information.</span></span>

### <a name="card-formatting"></a><span data-ttu-id="776f8-157">Formatação de cartão</span><span class="sxs-lookup"><span data-stu-id="776f8-157">Card Formatting</span></span>

<span data-ttu-id="776f8-158">Consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para obter mais informações sobre formatação de texto em cartões.</span><span class="sxs-lookup"><span data-stu-id="776f8-158">See [Card Formatting](~/task-modules-and-cards/cards/cards-format.md) for more information on text formatting in cards.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="776f8-159">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="776f8-159">Adaptive card</span></span>

<span data-ttu-id="776f8-160">Um cartão personalizável que pode conter qualquer combinação de texto, fala, imagem, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="776f8-160">A customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="776f8-161">*Veja* [cartões adaptáveis v 1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="776f8-161">*See* [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="776f8-162">Suporte para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="776f8-162">Support for Adaptive cards</span></span>

| <span data-ttu-id="776f8-163">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-163">Bots in Teams</span></span> | <span data-ttu-id="776f8-164">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-164">Messaging Extensions</span></span>  | <span data-ttu-id="776f8-165">Conectores</span><span class="sxs-lookup"><span data-stu-id="776f8-165">Connectors</span></span> | <span data-ttu-id="776f8-166">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="776f8-166">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="776f8-167">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-167">✔</span></span> | <span data-ttu-id="776f8-168">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-168">✔</span></span> | <span data-ttu-id="776f8-169">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-169">✖</span></span> | <span data-ttu-id="776f8-170">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-170">✔</span></span> |
|

### <a name="example-adaptive-card"></a><span data-ttu-id="776f8-171">Cartão adaptável de exemplo</span><span class="sxs-lookup"><span data-stu-id="776f8-171">Example Adaptive card</span></span>

![Exemplo de um cartão de cartão adaptável](~/assets/images/cards/adaptivecard.png)

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

#### <a name="for-more-information-on-adaptive-cards"></a><span data-ttu-id="776f8-173">Para obter mais informações sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="776f8-173">For more information on Adaptive cards</span></span>

* [<span data-ttu-id="776f8-174">Visão geral de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="776f8-174">Adaptive Cards Overview</span></span>](/adaptive-cards/)
* [<span data-ttu-id="776f8-175">Ações de cartão adaptável no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-175">Adaptive card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)

## <a name="hero-card"></a><span data-ttu-id="776f8-176">Cartão herói</span><span class="sxs-lookup"><span data-stu-id="776f8-176">Hero card</span></span>

<span data-ttu-id="776f8-177">Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="776f8-177">A card that typically contains a single large image, one or more buttons and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="776f8-178">Suporte para cartões herói</span><span class="sxs-lookup"><span data-stu-id="776f8-178">Support for Hero cards</span></span>

| <span data-ttu-id="776f8-179">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-179">Bots in Teams</span></span> | <span data-ttu-id="776f8-180">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-180">Messaging Extensions</span></span>  | <span data-ttu-id="776f8-181">Conectores</span><span class="sxs-lookup"><span data-stu-id="776f8-181">Connectors</span></span> | <span data-ttu-id="776f8-182">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="776f8-182">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="776f8-183">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-183">✔</span></span> | <span data-ttu-id="776f8-184">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-184">✔</span></span> | <span data-ttu-id="776f8-185">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-185">✖</span></span> | <span data-ttu-id="776f8-186">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-186">✔</span></span> |
|

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="776f8-187">Propriedades de um cartão herói</span><span class="sxs-lookup"><span data-stu-id="776f8-187">Properties of a Hero card</span></span>

| <span data-ttu-id="776f8-188">Propriedade</span><span class="sxs-lookup"><span data-stu-id="776f8-188">Property</span></span> | <span data-ttu-id="776f8-189">Tipo</span><span class="sxs-lookup"><span data-stu-id="776f8-189">Type</span></span>  | <span data-ttu-id="776f8-190">Descrição</span><span class="sxs-lookup"><span data-stu-id="776f8-190">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="776f8-191">title</span><span class="sxs-lookup"><span data-stu-id="776f8-191">title</span></span> | <span data-ttu-id="776f8-192">Rich text </span><span class="sxs-lookup"><span data-stu-id="776f8-192">Rich text</span></span> | <span data-ttu-id="776f8-193">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-193">Title of the card.</span></span> <span data-ttu-id="776f8-194">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="776f8-194">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="776f8-195">título</span><span class="sxs-lookup"><span data-stu-id="776f8-195">subtitle</span></span> | <span data-ttu-id="776f8-196">Rich text </span><span class="sxs-lookup"><span data-stu-id="776f8-196">Rich text</span></span> | <span data-ttu-id="776f8-197">Subtítulo do cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-197">Subtitle of the card.</span></span> <span data-ttu-id="776f8-198">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="776f8-198">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="776f8-199">texto</span><span class="sxs-lookup"><span data-stu-id="776f8-199">text</span></span> | <span data-ttu-id="776f8-200">Rich text </span><span class="sxs-lookup"><span data-stu-id="776f8-200">Rich text</span></span> | <span data-ttu-id="776f8-201">O texto aparece logo abaixo do subtítulo; Veja [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação</span><span class="sxs-lookup"><span data-stu-id="776f8-201">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="776f8-202">imagem</span><span class="sxs-lookup"><span data-stu-id="776f8-202">images</span></span> | <span data-ttu-id="776f8-203">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="776f8-203">Array of images</span></span> | <span data-ttu-id="776f8-204">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-204">Image displayed at top of card.</span></span> <span data-ttu-id="776f8-205">Taxa de proporção 16:9</span><span class="sxs-lookup"><span data-stu-id="776f8-205">Aspect ratio 16:9</span></span> |
| <span data-ttu-id="776f8-206">recolhe</span><span class="sxs-lookup"><span data-stu-id="776f8-206">buttons</span></span> | <span data-ttu-id="776f8-207">Matriz de objetos Action</span><span class="sxs-lookup"><span data-stu-id="776f8-207">Array of action objects</span></span> | <span data-ttu-id="776f8-208">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="776f8-208">Set of actions applicable to the current card.</span></span> <span data-ttu-id="776f8-209">Máximo de 6</span><span class="sxs-lookup"><span data-stu-id="776f8-209">Maximum 6</span></span> |
| <span data-ttu-id="776f8-210">Aproveite</span><span class="sxs-lookup"><span data-stu-id="776f8-210">tap</span></span> | <span data-ttu-id="776f8-211">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="776f8-211">Action object</span></span> | <span data-ttu-id="776f8-212">Esta ação será ativada quando o usuário tocar no próprio cartão</span><span class="sxs-lookup"><span data-stu-id="776f8-212">This action will be activated when the user taps on the card itself</span></span> |
|

### <a name="example-hero-card"></a><span data-ttu-id="776f8-213">Cartão herói de exemplo</span><span class="sxs-lookup"><span data-stu-id="776f8-213">Example Hero card</span></span>

![Exemplo de um cartão herói](~/assets/images/cards/hero.png)

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

### <a name="for-more-information-on-hero-cards"></a><span data-ttu-id="776f8-215">Para obter mais informações sobre cartões de herói</span><span class="sxs-lookup"><span data-stu-id="776f8-215">For more information on Hero cards</span></span>

<span data-ttu-id="776f8-216">Referência da estrutura do bot:</span><span class="sxs-lookup"><span data-stu-id="776f8-216">Bot Framework reference:</span></span>

* [<span data-ttu-id="776f8-217">Nó do cartão herói</span><span class="sxs-lookup"><span data-stu-id="776f8-217">Hero card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/herocard)
* [<span data-ttu-id="776f8-218">Cartão herói C #</span><span class="sxs-lookup"><span data-stu-id="776f8-218">Hero card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.herocard?view=botbuilder-dotnet-3.0)

## <a name="list-card"></a><span data-ttu-id="776f8-219">Cartão de lista</span><span class="sxs-lookup"><span data-stu-id="776f8-219">List card</span></span>

<span data-ttu-id="776f8-220">O cartão de lista foi adicionado pelo Microsoft Teams para fornecer funções além do que a coleção List pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="776f8-220">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="776f8-221">O cartão de lista fornece uma lista de rolagem dos itens.</span><span class="sxs-lookup"><span data-stu-id="776f8-221">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="776f8-222">Suporte para cartões de lista</span><span class="sxs-lookup"><span data-stu-id="776f8-222">Support for List cards</span></span>

| <span data-ttu-id="776f8-223">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-223">Bots in Teams</span></span> | <span data-ttu-id="776f8-224">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-224">Messaging Extensions</span></span>  | <span data-ttu-id="776f8-225">Conectores</span><span class="sxs-lookup"><span data-stu-id="776f8-225">Connectors</span></span> | <span data-ttu-id="776f8-226">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="776f8-226">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="776f8-227">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-227">✔</span></span> | <span data-ttu-id="776f8-228">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-228">✖</span></span> | <span data-ttu-id="776f8-229">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-229">✖</span></span> |<span data-ttu-id="776f8-230">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-230">✔</span></span> |
|

### <a name="properties-of-a-list-card"></a><span data-ttu-id="776f8-231">Propriedades de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="776f8-231">Properties of a List card</span></span>

| <span data-ttu-id="776f8-232">Propriedade</span><span class="sxs-lookup"><span data-stu-id="776f8-232">Property</span></span> | <span data-ttu-id="776f8-233">Tipo</span><span class="sxs-lookup"><span data-stu-id="776f8-233">Type</span></span>  | <span data-ttu-id="776f8-234">Descrição</span><span class="sxs-lookup"><span data-stu-id="776f8-234">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="776f8-235">title</span><span class="sxs-lookup"><span data-stu-id="776f8-235">title</span></span> | <span data-ttu-id="776f8-236">Rich text </span><span class="sxs-lookup"><span data-stu-id="776f8-236">Rich text</span></span> | <span data-ttu-id="776f8-237">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-237">Title of the card.</span></span> <span data-ttu-id="776f8-238">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="776f8-238">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="776f8-239">items</span><span class="sxs-lookup"><span data-stu-id="776f8-239">items</span></span> | <span data-ttu-id="776f8-240">Matriz de itens de lista</span><span class="sxs-lookup"><span data-stu-id="776f8-240">Array of list items</span></span>  ||
| <span data-ttu-id="776f8-241">recolhe</span><span class="sxs-lookup"><span data-stu-id="776f8-241">buttons</span></span> | <span data-ttu-id="776f8-242">Matriz de objetos Action</span><span class="sxs-lookup"><span data-stu-id="776f8-242">Array of action objects</span></span> | <span data-ttu-id="776f8-243">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="776f8-243">Set of actions applicable to the current card.</span></span> <span data-ttu-id="776f8-244">Máximo de 6.</span><span class="sxs-lookup"><span data-stu-id="776f8-244">Maximum 6.</span></span> <span data-ttu-id="776f8-245">Não processa em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="776f8-245">Does not render on mobile.</span></span> |
|

### <a name="example-list-card"></a><span data-ttu-id="776f8-246">Exemplo de cartão de lista</span><span class="sxs-lookup"><span data-stu-id="776f8-246">Example List card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="776f8-247">Cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="776f8-247">Office 365 connector card</span></span>

<span data-ttu-id="776f8-248">Com suporte no Teams, não na estrutura de bot.</span><span class="sxs-lookup"><span data-stu-id="776f8-248">Supported in Teams, not in Bot Framework.</span></span>

<span data-ttu-id="776f8-249">O cartão de conexão do Office 365 fornece um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="776f8-249">The Office 365 Connector card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="776f8-250">Este cartão encapsula um cartão de conexão para que possa ser usado por bots.</span><span class="sxs-lookup"><span data-stu-id="776f8-250">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="776f8-251">Consulte a seção observações para ver as diferenças entre os cartões de conector e o cartão do O365.</span><span class="sxs-lookup"><span data-stu-id="776f8-251">See the notes section for differences between connector cards and the O365 card.</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="776f8-252">Suporte para cartões conectores do Office 365</span><span class="sxs-lookup"><span data-stu-id="776f8-252">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="776f8-253">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-253">Bots in Teams</span></span> | <span data-ttu-id="776f8-254">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-254">Messaging Extensions</span></span>  | <span data-ttu-id="776f8-255">Conectores</span><span class="sxs-lookup"><span data-stu-id="776f8-255">Connectors</span></span> | <span data-ttu-id="776f8-256">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="776f8-256">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="776f8-257">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-257">✔</span></span> | <span data-ttu-id="776f8-258">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-258">✔</span></span> | <span data-ttu-id="776f8-259">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-259">✔</span></span> | <span data-ttu-id="776f8-260">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-260">✖</span></span> |
|

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="776f8-261">Propriedades do cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="776f8-261">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="776f8-262">Propriedade</span><span class="sxs-lookup"><span data-stu-id="776f8-262">Property</span></span> | <span data-ttu-id="776f8-263">Tipo</span><span class="sxs-lookup"><span data-stu-id="776f8-263">Type</span></span>  | <span data-ttu-id="776f8-264">Descrição</span><span class="sxs-lookup"><span data-stu-id="776f8-264">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="776f8-265">title</span><span class="sxs-lookup"><span data-stu-id="776f8-265">title</span></span> | <span data-ttu-id="776f8-266">Rich text </span><span class="sxs-lookup"><span data-stu-id="776f8-266">Rich text</span></span> | <span data-ttu-id="776f8-267">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-267">Title of the card.</span></span> <span data-ttu-id="776f8-268">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="776f8-268">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="776f8-269">summary</span><span class="sxs-lookup"><span data-stu-id="776f8-269">summary</span></span> | <span data-ttu-id="776f8-270">Rich text </span><span class="sxs-lookup"><span data-stu-id="776f8-270">Rich text</span></span> | <span data-ttu-id="776f8-271">Resumo do cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-271">Summary of the card.</span></span> <span data-ttu-id="776f8-272">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="776f8-272">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="776f8-273">texto</span><span class="sxs-lookup"><span data-stu-id="776f8-273">text</span></span> | <span data-ttu-id="776f8-274">Rich text </span><span class="sxs-lookup"><span data-stu-id="776f8-274">Rich text</span></span> | <span data-ttu-id="776f8-275">O texto aparece logo abaixo do subtítulo; Veja [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação</span><span class="sxs-lookup"><span data-stu-id="776f8-275">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="776f8-276">themeColor</span><span class="sxs-lookup"><span data-stu-id="776f8-276">themeColor</span></span> | <span data-ttu-id="776f8-277">Cadeia de caracteres HEX</span><span class="sxs-lookup"><span data-stu-id="776f8-277">HEX string</span></span> | <span data-ttu-id="776f8-278">cor que substitui o accentColor fornecido do manifesto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="776f8-278">color that overrides the accentColor provided from the application manifest</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="776f8-279">Observações sobre o cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="776f8-279">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="776f8-280">Os cartões conectores do Office 365 funcionam corretamente no Microsoft Teams, incluindo [ações ActionCard](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="776f8-280">Office 365 Connector cards function properly on Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="776f8-281">Uma diferença importante entre o uso de cartões de conexão de um conector e o uso de cartões de conector no bot é a manipulação de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-281">One important difference between using Connector cards from a Connector and using Connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="776f8-282">Para um conector, o ponto de extremidade recebe a carga do cartão via HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="776f8-282">For a Connector, the endpoint receives the card payload via HTTP POST.</span></span>
* <span data-ttu-id="776f8-283">Para um bot, a `HttpPOST` ação dispara uma `invoke` atividade que envia apenas a ID e o corpo da ação para o bot.</span><span class="sxs-lookup"><span data-stu-id="776f8-283">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="776f8-284">Cada placa de conector pode exibir um máximo de 10 seções e cada seção pode conter no máximo 5 imagens e 5 ações.</span><span class="sxs-lookup"><span data-stu-id="776f8-284">Each Connector card can display a maximum of 10 sections, and each section can contain a maximum of 5 images and 5 actions.</span></span>

> [!NOTE]
> <span data-ttu-id="776f8-285">Quaisquer seções, imagens ou ações adicionais em uma mensagem não serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="776f8-285">Any additional sections, images, or actions in a message will not appear.</span></span>

<span data-ttu-id="776f8-286">Todos os campos de texto dão suporte a redução e HTML.</span><span class="sxs-lookup"><span data-stu-id="776f8-286">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="776f8-287">Você pode controlar quais seções usam a redução ou HTML, definindo a `markdown` propriedade em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="776f8-287">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="776f8-288">Por padrão, `markdown` é definido como `true` ; se você deseja usar HTML em vez disso, defina `markdown` como `false` .</span><span class="sxs-lookup"><span data-stu-id="776f8-288">By default, `markdown` is set to `true`; if you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="776f8-289">Se você especificar a `themeColor` propriedade, ela substituirá a `accentColor` propriedade no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="776f8-289">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="776f8-290">Para especificar o estilo de renderização para `activityImage` , você pode definir `activityImageType` como a seguir.</span><span class="sxs-lookup"><span data-stu-id="776f8-290">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows.</span></span>

| <span data-ttu-id="776f8-291">Valor</span><span class="sxs-lookup"><span data-stu-id="776f8-291">Value</span></span> | <span data-ttu-id="776f8-292">Descrição</span><span class="sxs-lookup"><span data-stu-id="776f8-292">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="776f8-293">Será `activityImage`será cortado como um círculo</span><span class="sxs-lookup"><span data-stu-id="776f8-293">Default; `activityImage` will be cropped as a circle</span></span> |
| `article` | <span data-ttu-id="776f8-294">`activityImage`será exibido como um retângulo e manterá sua taxa de proporção</span><span class="sxs-lookup"><span data-stu-id="776f8-294">`activityImage` will be displayed as a rectangle and retain its aspect ratio</span></span> |

<span data-ttu-id="776f8-295">Para todos os outros detalhes sobre as propriedades do cartão de conexão, confira a [referência de cartão de mensagem acionável](/outlook/actionable-messages/card-reference).</span><span class="sxs-lookup"><span data-stu-id="776f8-295">For all other details about Connector card properties, see the [Actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="776f8-296">As únicas propriedades da placa de conector que o Microsoft Teams não suporta atualmente são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="776f8-296">The only Connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="776f8-297">`startGroup`(sempre tratado como `true` no Teams)</span><span class="sxs-lookup"><span data-stu-id="776f8-297">`startGroup` (always treated as `true` in Teams)</span></span>
* `originator`
* `correlationId`

### <a name="example-office-365-connector-card"></a><span data-ttu-id="776f8-298">Cartão de conexão de exemplo do Office 365</span><span class="sxs-lookup"><span data-stu-id="776f8-298">Example Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="776f8-299">Cartão de recibo</span><span class="sxs-lookup"><span data-stu-id="776f8-299">Receipt card</span></span>

<span data-ttu-id="776f8-300">Com suporte no Teams.</span><span class="sxs-lookup"><span data-stu-id="776f8-300">Supported in Teams.</span></span>

<span data-ttu-id="776f8-301">Um cartão que permite que um bot forneça um recibo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="776f8-301">A card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="776f8-302">Normalmente, ela contém a lista de itens a serem incluídos no recebimento, no imposto e nas informações totais e em outros textos.</span><span class="sxs-lookup"><span data-stu-id="776f8-302">It typically contains the list of items to include on the receipt, tax and total information, and other text.</span></span>

### <a name="support-for-receipts-cards"></a><span data-ttu-id="776f8-303">Suporte para cartões de recibos</span><span class="sxs-lookup"><span data-stu-id="776f8-303">Support for Receipts cards</span></span>

| <span data-ttu-id="776f8-304">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-304">Bots in Teams</span></span> | <span data-ttu-id="776f8-305">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-305">Messaging Extensions</span></span>  | <span data-ttu-id="776f8-306">Conectores</span><span class="sxs-lookup"><span data-stu-id="776f8-306">Connectors</span></span> | <span data-ttu-id="776f8-307">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="776f8-307">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="776f8-308">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-308">✔</span></span> | <span data-ttu-id="776f8-309">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-309">✔</span></span> | <span data-ttu-id="776f8-310">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-310">✖</span></span> | <span data-ttu-id="776f8-311">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-311">✔</span></span> |
|

### <a name="for-more-information-on-receipt-cards"></a><span data-ttu-id="776f8-312">Para obter mais informações sobre cartões de recibo</span><span class="sxs-lookup"><span data-stu-id="776f8-312">For more information on Receipt cards</span></span>

<span data-ttu-id="776f8-313">Referência da estrutura do bot:</span><span class="sxs-lookup"><span data-stu-id="776f8-313">Bot Framework reference:</span></span>

* [<span data-ttu-id="776f8-314">Nó do cartão de recibo</span><span class="sxs-lookup"><span data-stu-id="776f8-314">Receipt card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest)
* [<span data-ttu-id="776f8-315">Cartão de recibo C #</span><span class="sxs-lookup"><span data-stu-id="776f8-315">Receipt card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.receiptcard?view=botbuilder-dotnet-3.0)

## <a name="signin-card"></a><span data-ttu-id="776f8-316">Cartão de conexão</span><span class="sxs-lookup"><span data-stu-id="776f8-316">Signin card</span></span>

<span data-ttu-id="776f8-317">Um cartão que permite que um bot solicite a entrada de um usuário.</span><span class="sxs-lookup"><span data-stu-id="776f8-317">A card that enables a bot to request that a user sign in.</span></span> <span data-ttu-id="776f8-318">Suportado no Teams em um formato levemente diferente do que é encontrado na estrutura de bot.</span><span class="sxs-lookup"><span data-stu-id="776f8-318">Supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="776f8-319">O cartão de entrada no Microsoft Teams é semelhante ao cartão de entrada na estrutura de bot com a exceção de que o cartão de entrada no Microsoft Teams suporta apenas duas ações: `signin` e `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="776f8-319">The signin card in Teams is similar to the signin card in the bot framework with the exception that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="776f8-320">A *ação de entrada* pode ser usada de qualquer cartão no Microsoft Teams, e não apenas do cartão de entrada.</span><span class="sxs-lookup"><span data-stu-id="776f8-320">The *signin action* can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="776f8-321">Consulte o tópico [Microsoft Teams Authentication Flow para bots](~/bots/how-to/authentication/auth-flow-bot.md) para obter mais detalhes sobre autenticação.</span><span class="sxs-lookup"><span data-stu-id="776f8-321">See the topic [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md) for more details on authentication.</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="776f8-322">Suporte para placas de entrada</span><span class="sxs-lookup"><span data-stu-id="776f8-322">Support for Signin cards</span></span>

| <span data-ttu-id="776f8-323">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-323">Bots in Teams</span></span> | <span data-ttu-id="776f8-324">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-324">Messaging Extensions</span></span>  | <span data-ttu-id="776f8-325">Conectores</span><span class="sxs-lookup"><span data-stu-id="776f8-325">Connectors</span></span> | <span data-ttu-id="776f8-326">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="776f8-326">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="776f8-327">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-327">✔</span></span> | <span data-ttu-id="776f8-328">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-328">✖</span></span> | <span data-ttu-id="776f8-329">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-329">✖</span></span> | <span data-ttu-id="776f8-330">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-330">✔</span></span> |
|

### <a name="for-more-information-on-signin-cards"></a><span data-ttu-id="776f8-331">Para obter mais informações sobre cartões de conexão</span><span class="sxs-lookup"><span data-stu-id="776f8-331">For more information on Signin cards</span></span>

<span data-ttu-id="776f8-332">Referência da estrutura do bot:</span><span class="sxs-lookup"><span data-stu-id="776f8-332">Bot Framework reference:</span></span>

* [<span data-ttu-id="776f8-333">Nó do cartão de entrada</span><span class="sxs-lookup"><span data-stu-id="776f8-333">Signin card Node</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest)
* [<span data-ttu-id="776f8-334">Cartão de entrada C #</span><span class="sxs-lookup"><span data-stu-id="776f8-334">Signin card C#</span></span>](/dotnet/api/microsoft.bot.connector.signincard?view=botbuilder-dotnet-3.0)

## <a name="thumbnail-card"></a><span data-ttu-id="776f8-335">Cartão de miniaturas</span><span class="sxs-lookup"><span data-stu-id="776f8-335">Thumbnail card</span></span>

<span data-ttu-id="776f8-336">Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="776f8-336">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="776f8-337">Suporte para cartões em miniatura</span><span class="sxs-lookup"><span data-stu-id="776f8-337">Support for Thumbnail cards</span></span>

| <span data-ttu-id="776f8-338">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-338">Bots in Teams</span></span> | <span data-ttu-id="776f8-339">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-339">Messaging Extensions</span></span>  | <span data-ttu-id="776f8-340">Conectores</span><span class="sxs-lookup"><span data-stu-id="776f8-340">Connectors</span></span> | <span data-ttu-id="776f8-341">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="776f8-341">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="776f8-342">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-342">✔</span></span> | <span data-ttu-id="776f8-343">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-343">✔</span></span> | <span data-ttu-id="776f8-344">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-344">✖</span></span> | <span data-ttu-id="776f8-345">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-345">✔</span></span> |
|

![Exemplo de um cartão em miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="776f8-347">Propriedades de um cartão em miniatura</span><span class="sxs-lookup"><span data-stu-id="776f8-347">Properties of a Thumbnail card</span></span>

| <span data-ttu-id="776f8-348">Propriedade</span><span class="sxs-lookup"><span data-stu-id="776f8-348">Property</span></span> | <span data-ttu-id="776f8-349">Tipo</span><span class="sxs-lookup"><span data-stu-id="776f8-349">Type</span></span>  | <span data-ttu-id="776f8-350">Descrição</span><span class="sxs-lookup"><span data-stu-id="776f8-350">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="776f8-351">title</span><span class="sxs-lookup"><span data-stu-id="776f8-351">title</span></span> | <span data-ttu-id="776f8-352">Rich text </span><span class="sxs-lookup"><span data-stu-id="776f8-352">Rich text</span></span> | <span data-ttu-id="776f8-353">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-353">Title of the card.</span></span> <span data-ttu-id="776f8-354">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="776f8-354">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="776f8-355">título</span><span class="sxs-lookup"><span data-stu-id="776f8-355">subtitle</span></span> | <span data-ttu-id="776f8-356">Rich text </span><span class="sxs-lookup"><span data-stu-id="776f8-356">Rich text</span></span> | <span data-ttu-id="776f8-357">Subtítulo do cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-357">Subtitle of the card.</span></span> <span data-ttu-id="776f8-358">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="776f8-358">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="776f8-359">texto</span><span class="sxs-lookup"><span data-stu-id="776f8-359">text</span></span> | <span data-ttu-id="776f8-360">Rich text </span><span class="sxs-lookup"><span data-stu-id="776f8-360">Rich text</span></span> | <span data-ttu-id="776f8-361">O texto aparece logo abaixo do subtítulo; Veja [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação</span><span class="sxs-lookup"><span data-stu-id="776f8-361">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="776f8-362">imagem</span><span class="sxs-lookup"><span data-stu-id="776f8-362">images</span></span> | <span data-ttu-id="776f8-363">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="776f8-363">Array of images</span></span> | <span data-ttu-id="776f8-364">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="776f8-364">Image displayed at top of card.</span></span> <span data-ttu-id="776f8-365">Taxa de proporção 1:1 (quadrado)</span><span class="sxs-lookup"><span data-stu-id="776f8-365">Aspect ratio 1:1 (square)</span></span> |
| <span data-ttu-id="776f8-366">recolhe</span><span class="sxs-lookup"><span data-stu-id="776f8-366">buttons</span></span> | <span data-ttu-id="776f8-367">Matriz de objetos Action</span><span class="sxs-lookup"><span data-stu-id="776f8-367">Array of action objects</span></span> | <span data-ttu-id="776f8-368">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="776f8-368">Set of actions applicable to the current card.</span></span> <span data-ttu-id="776f8-369">Máximo de 6</span><span class="sxs-lookup"><span data-stu-id="776f8-369">Maximum 6</span></span> |
| <span data-ttu-id="776f8-370">Aproveite</span><span class="sxs-lookup"><span data-stu-id="776f8-370">tap</span></span> | <span data-ttu-id="776f8-371">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="776f8-371">Action object</span></span> | <span data-ttu-id="776f8-372">Esta ação será ativada quando o usuário tocar no próprio cartão</span><span class="sxs-lookup"><span data-stu-id="776f8-372">This action will be activated when the user taps on the card itself</span></span> |
|

### <a name="example-thumbnail-card"></a><span data-ttu-id="776f8-373">Cartão de miniatura de exemplo</span><span class="sxs-lookup"><span data-stu-id="776f8-373">Example Thumbnail card</span></span>

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

### <a name="for-more-information"></a><span data-ttu-id="776f8-374">Para saber mais</span><span class="sxs-lookup"><span data-stu-id="776f8-374">For more information</span></span>

<span data-ttu-id="776f8-375">Referência da estrutura do bot:</span><span class="sxs-lookup"><span data-stu-id="776f8-375">Bot Framework reference:</span></span>

* [<span data-ttu-id="776f8-376">Nó de cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="776f8-376">Thumbnail card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest)
* [<span data-ttu-id="776f8-377">Cartão-miniatura C #</span><span class="sxs-lookup"><span data-stu-id="776f8-377">Thumbnail card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.thumbnailcard?view=botbuilder-dotnet-3.0)

## <a name="card-collections"></a><span data-ttu-id="776f8-378">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="776f8-378">Card collections</span></span>

<span data-ttu-id="776f8-379">As coleções de cartões têm suporte no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="776f8-379">Card collections are supported in Teams.</span></span>

<span data-ttu-id="776f8-380">As coleções de cartões são fornecidas pela estrutura de bot: `builder.AttachmentLayout.carousel` e `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="776f8-380">Card collections are provided by the Bot Framework: `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="776f8-381">Essas coleções podem conter cartões adaptáveis, herói ou de miniaturas.</span><span class="sxs-lookup"><span data-stu-id="776f8-381">These collections can contain Adaptive, Hero, or Thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="776f8-382">Coleção carrossel</span><span class="sxs-lookup"><span data-stu-id="776f8-382">Carousel collection</span></span>

<span data-ttu-id="776f8-383">O [layout do carrossel](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0) mostra um carrossel de cartões, opcionalmente, com os botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="776f8-383">The [carousel layout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="776f8-384">Suporte para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="776f8-384">Support for Carousel collections</span></span>

| <span data-ttu-id="776f8-385">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-385">Bots in Teams</span></span> | <span data-ttu-id="776f8-386">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-386">Messaging Extensions</span></span>  | <span data-ttu-id="776f8-387">Conectores</span><span class="sxs-lookup"><span data-stu-id="776f8-387">Connectors</span></span> | <span data-ttu-id="776f8-388">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="776f8-388">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="776f8-389">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-389">✔</span></span> | <span data-ttu-id="776f8-390">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-390">✖</span></span> | <span data-ttu-id="776f8-391">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-391">✖</span></span> | <span data-ttu-id="776f8-392">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-392">✔</span></span> |
|

> [!NOTE]
> <span data-ttu-id="776f8-393">Um carrossel pode exibir no máximo 10 cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="776f8-393">A carousel can display a maximum of 10 cards per message.</span></span>

### <a name="example-carousel-collection"></a><span data-ttu-id="776f8-394">Coleção de carrossel de exemplo</span><span class="sxs-lookup"><span data-stu-id="776f8-394">Example Carousel collection</span></span>

![Exemplo de um carrossel de cartões](~/assets/images/cards/carousel.png)

<span data-ttu-id="776f8-396">As propriedades são as mesmas do herói ou do cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="776f8-396">Properties are the same as for the hero or thumbnail card.</span></span>

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="776f8-397">Sintaxe de coleções do carrossel</span><span class="sxs-lookup"><span data-stu-id="776f8-397">Syntax for Carousel collections</span></span>

`builder.AttachmentLayout.carousel`

## <a name="list-collection"></a><span data-ttu-id="776f8-398">Coleção List</span><span class="sxs-lookup"><span data-stu-id="776f8-398">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="776f8-399">Suporte para coleções de listas</span><span class="sxs-lookup"><span data-stu-id="776f8-399">Support for List collections</span></span>

<span data-ttu-id="776f8-400">O layout de lista mostra uma lista de cartões empilhados verticalmente, opcionalmente com os botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="776f8-400">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="776f8-401">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-401">Bots in Teams</span></span> | <span data-ttu-id="776f8-402">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="776f8-402">Messaging Extensions</span></span>  | <span data-ttu-id="776f8-403">Conectores</span><span class="sxs-lookup"><span data-stu-id="776f8-403">Connectors</span></span> | <span data-ttu-id="776f8-404">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="776f8-404">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="776f8-405">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-405">✔</span></span> | <span data-ttu-id="776f8-406">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-406">✔</span></span> | <span data-ttu-id="776f8-407">✖</span><span class="sxs-lookup"><span data-stu-id="776f8-407">✖</span></span> | <span data-ttu-id="776f8-408">✔</span><span class="sxs-lookup"><span data-stu-id="776f8-408">✔</span></span> |
|

### <a name="example-list-collection"></a><span data-ttu-id="776f8-409">Exemplo de coleção List</span><span class="sxs-lookup"><span data-stu-id="776f8-409">Example List collection</span></span>

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

<span data-ttu-id="776f8-411">As propriedades são as mesmas do herói ou do cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="776f8-411">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="776f8-412">Uma lista pode exibir no máximo 10 cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="776f8-412">A list can display a maximum of 10 cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="776f8-413">Algumas combinações de cartões de lista ainda não são suportadas no iOS e no Android.</span><span class="sxs-lookup"><span data-stu-id="776f8-413">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="776f8-414">Sintaxe para coleções de listas</span><span class="sxs-lookup"><span data-stu-id="776f8-414">Syntax for List collections</span></span>

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="776f8-415">Cartões não suportados no Teams</span><span class="sxs-lookup"><span data-stu-id="776f8-415">Cards not supported in Teams</span></span>

<span data-ttu-id="776f8-416">Os seguintes cartões são implementados pela estrutura do bot, mas não são suportados pelo Teams.</span><span class="sxs-lookup"><span data-stu-id="776f8-416">The following cards are implemented by the Bot Framework, but are NOT supported by Teams.</span></span>

* <span data-ttu-id="776f8-417">Cartões de animação</span><span class="sxs-lookup"><span data-stu-id="776f8-417">Animation cards</span></span>
* <span data-ttu-id="776f8-418">Placas de áudio</span><span class="sxs-lookup"><span data-stu-id="776f8-418">Audio cards</span></span>
* <span data-ttu-id="776f8-419">Placas de vídeo</span><span class="sxs-lookup"><span data-stu-id="776f8-419">Video cards</span></span>
