---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Teams
keywords: referência de cartões de bots
ms.openlocfilehash: 22a4faa932173387cbefe900e30106d063c49e50
ms.sourcegitcommit: 5739245903278d521ec920427248b6b48676e637
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49778391"
---
# <a name="cards-reference"></a><span data-ttu-id="38535-104">Referência de cartões</span><span class="sxs-lookup"><span data-stu-id="38535-104">Cards Reference</span></span>

<span data-ttu-id="38535-105">Os cartões listados nesta seção têm suporte em bots para o Teams.</span><span class="sxs-lookup"><span data-stu-id="38535-105">The cards listed in this section are supported in bots for Teams.</span></span> <span data-ttu-id="38535-106">Eles são baseados em cartões definidos pela Estrutura de Bot, mas o Teams não dá suporte a todos os cartões do Bot Framework e adicionou alguns de seus próprios cartões.</span><span class="sxs-lookup"><span data-stu-id="38535-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span> <span data-ttu-id="38535-107">As diferenças são destacadas nas referências abaixo.</span><span class="sxs-lookup"><span data-stu-id="38535-107">Differences are called out in the references below.</span></span>

## <a name="card-examples"></a><span data-ttu-id="38535-108">Exemplos de cartão</span><span class="sxs-lookup"><span data-stu-id="38535-108">Card examples</span></span>

<span data-ttu-id="38535-109">Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do Construtor de Bots (v3).</span><span class="sxs-lookup"><span data-stu-id="38535-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK (v3).</span></span> <span data-ttu-id="38535-110">Também há exemplos de código disponíveis no repositório Microsoft/BotBuilder-Samples no GitHub.</span><span class="sxs-lookup"><span data-stu-id="38535-110">There are also code samples available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="38535-111">.NET</span><span class="sxs-lookup"><span data-stu-id="38535-111">.NET</span></span>
  * [<span data-ttu-id="38535-112">Adicionar cartões como anexos a mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-112">Add cards as attachments to messages</span></span>](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [<span data-ttu-id="38535-113">Código de exemplo de cartões (Construtor de Bots v3)</span><span class="sxs-lookup"><span data-stu-id="38535-113">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/CSharp/cards-RichCards)
* <span data-ttu-id="38535-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="38535-114">Node.js</span></span>
  * [<span data-ttu-id="38535-115">Adicionar cartões como anexos a mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-115">Add cards as attachments to messages</span></span>](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [<span data-ttu-id="38535-116">Código de exemplo de cartões (Construtor de Bots v3)</span><span class="sxs-lookup"><span data-stu-id="38535-116">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/Node/cards-RichCards)

## <a name="types-of-cards"></a><span data-ttu-id="38535-117">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="38535-117">Types of cards</span></span>

<span data-ttu-id="38535-118">Esta tabela mostra os tipos de cartões disponíveis para você.</span><span class="sxs-lookup"><span data-stu-id="38535-118">This table shows the types of cards available to you.</span></span>

| <span data-ttu-id="38535-119">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="38535-119">Card Type</span></span> | <span data-ttu-id="38535-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="38535-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="38535-121">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="38535-121">Adaptive Card</span></span>](#adaptive-card) | <span data-ttu-id="38535-122">Cartão altamente personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="38535-122">Highly customizable card that can contain any combination of text, speech, images, buttons and input fields.</span></span> |
| [<span data-ttu-id="38535-123">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="38535-123">Hero Card</span></span>](#hero-card) | <span data-ttu-id="38535-124">Normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="38535-124">Typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="38535-125">Cartão de lista</span><span class="sxs-lookup"><span data-stu-id="38535-125">List Card</span></span>](#list-card) | <span data-ttu-id="38535-126">Uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="38535-126">A scrolling list of items.</span></span> |
| [<span data-ttu-id="38535-127">Cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="38535-127">Office 365 Connector Card</span></span>](#office-365-connector-card) | <span data-ttu-id="38535-128">Layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="38535-128">Flexible layout with multiple sections, fields, images and actions.</span></span> |
| [<span data-ttu-id="38535-129">Cartão de Confirmação</span><span class="sxs-lookup"><span data-stu-id="38535-129">Receipt Card</span></span>](#receipt-card) | <span data-ttu-id="38535-130">Fornece um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="38535-130">Provides a receipt to the user.</span></span> |
| [<span data-ttu-id="38535-131">Signin Card</span><span class="sxs-lookup"><span data-stu-id="38535-131">Signin Card</span></span>](#signin-card) | <span data-ttu-id="38535-132">Permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="38535-132">Enables a bot to request that a user sign in.</span></span> |
| [<span data-ttu-id="38535-133">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="38535-133">Thumbnail Card</span></span>](#thumbnail-card) | <span data-ttu-id="38535-134">Normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões.</span><span class="sxs-lookup"><span data-stu-id="38535-134">Typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="38535-135">Coleções de Cartões</span><span class="sxs-lookup"><span data-stu-id="38535-135">Card Collections</span></span>](#card-collections) | <span data-ttu-id="38535-136">Usado para retornar vários itens em uma única resposta</span><span class="sxs-lookup"><span data-stu-id="38535-136">Used to return multiple items in a single response</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="38535-137">Propriedades comuns para todos os cartões</span><span class="sxs-lookup"><span data-stu-id="38535-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="38535-138">Imagens de cartão em linha</span><span class="sxs-lookup"><span data-stu-id="38535-138">Inline card images</span></span>

<span data-ttu-id="38535-139">Seu cartão pode conter uma imagem em linha incluindo um link para sua imagem publicamente disponível.</span><span class="sxs-lookup"><span data-stu-id="38535-139">Your card can contain an inline image by including a link to your publicly available image.</span></span> <span data-ttu-id="38535-140">Para fins de desempenho, recomendamos que você hospede sua imagem em uma CDN (rede pública de distribuição de conteúdo).</span><span class="sxs-lookup"><span data-stu-id="38535-140">For performance purposes we highly recommend you host your image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="38535-141">As imagens são dimensionados para cima ou para baixo em tamanho, mantendo a taxa de proporção para cobrir a área da imagem e, em seguida, cortadas do centro para obter a taxa de proporção apropriada para o cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="38535-142">As imagens devem ter, no máximo, 1024×1024 em formato PNG, JPEG ou GIF; GIF animado não tem suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="38535-142">Images must be at most 1024×1024 in PNG, JPEG, or GIF format; animated GIF is not officially supported.</span></span>

| <span data-ttu-id="38535-143">Propriedade</span><span class="sxs-lookup"><span data-stu-id="38535-143">Property</span></span> | <span data-ttu-id="38535-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="38535-144">Type</span></span>  | <span data-ttu-id="38535-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="38535-145">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="38535-146">url</span><span class="sxs-lookup"><span data-stu-id="38535-146">url</span></span> | <span data-ttu-id="38535-147">URL</span><span class="sxs-lookup"><span data-stu-id="38535-147">URL</span></span> | <span data-ttu-id="38535-148">URL HTTPS para a imagem</span><span class="sxs-lookup"><span data-stu-id="38535-148">HTTPS URL to the image</span></span> |
| <span data-ttu-id="38535-149">alt</span><span class="sxs-lookup"><span data-stu-id="38535-149">alt</span></span> | <span data-ttu-id="38535-150">String</span><span class="sxs-lookup"><span data-stu-id="38535-150">String</span></span> | <span data-ttu-id="38535-151">Descrição acessível da imagem</span><span class="sxs-lookup"><span data-stu-id="38535-151">Accessible description of the image</span></span> |

### <a name="buttons"></a><span data-ttu-id="38535-152">Botões</span><span class="sxs-lookup"><span data-stu-id="38535-152">Buttons</span></span>

<span data-ttu-id="38535-153">Os botões são mostrados empilhados na parte inferior do cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-153">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="38535-154">O texto do botão está sempre em uma única linha e será truncado se o texto exceder a largura do botão.</span><span class="sxs-lookup"><span data-stu-id="38535-154">Button text is always on a single line and will be truncated if the text exceeds the button width.</span></span> <span data-ttu-id="38535-155">Quaisquer botões adicionais além do número máximo suportado pelo cartão não serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="38535-155">Any additional buttons beyond the maximum number supported by the card will not be shown.</span></span>

<span data-ttu-id="38535-156">Consulte [Ações do Cartão](~/task-modules-and-cards/cards/cards-actions.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="38535-156">See [Card Actions](~/task-modules-and-cards/cards/cards-actions.md) for more information.</span></span>

### <a name="card-formatting"></a><span data-ttu-id="38535-157">Formatação de Cartão</span><span class="sxs-lookup"><span data-stu-id="38535-157">Card Formatting</span></span>

<span data-ttu-id="38535-158">Consulte [Formatação de Cartão](~/task-modules-and-cards/cards/cards-format.md) para obter mais informações sobre formatação de texto em cartões.</span><span class="sxs-lookup"><span data-stu-id="38535-158">See [Card Formatting](~/task-modules-and-cards/cards/cards-format.md) for more information on text formatting in cards.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="38535-159">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="38535-159">Adaptive card</span></span>

<span data-ttu-id="38535-160">Um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="38535-160">A customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="38535-161">*Consulte* [Cartões Adaptáveis v1.2.0.](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0)</span><span class="sxs-lookup"><span data-stu-id="38535-161">*See* [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="38535-162">Suporte para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="38535-162">Support for Adaptive cards</span></span>

| <span data-ttu-id="38535-163">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-163">Bots in Teams</span></span> | <span data-ttu-id="38535-164">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-164">Messaging Extensions</span></span>  | <span data-ttu-id="38535-165">Conectores</span><span class="sxs-lookup"><span data-stu-id="38535-165">Connectors</span></span> | <span data-ttu-id="38535-166">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="38535-166">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="38535-167">✔</span><span class="sxs-lookup"><span data-stu-id="38535-167">✔</span></span> | <span data-ttu-id="38535-168">✔</span><span class="sxs-lookup"><span data-stu-id="38535-168">✔</span></span> | <span data-ttu-id="38535-169">✖</span><span class="sxs-lookup"><span data-stu-id="38535-169">✖</span></span> | <span data-ttu-id="38535-170">✔</span><span class="sxs-lookup"><span data-stu-id="38535-170">✔</span></span> |
|

> [!NOTE]
> * <span data-ttu-id="38535-171">A plataforma do Teams é compatível com a versão 1.2 ou anterior dos recursos de cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="38535-171">Teams platform supports v1.2 or earlier of Adaptive card features.</span></span>
> * <span data-ttu-id="38535-172">Atualmente, os elementos de mídia não têm suporte no cartão adaptável v1.2 na plataforma do Teams.</span><span class="sxs-lookup"><span data-stu-id="38535-172">Media elements are currently not supported in Adaptive card v1.2 on the Teams platform.</span></span>
### <a name="example-adaptive-card"></a><span data-ttu-id="38535-173">Cartão adaptável de exemplo</span><span class="sxs-lookup"><span data-stu-id="38535-173">Example Adaptive card</span></span>

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

#### <a name="for-more-information-on-adaptive-cards"></a><span data-ttu-id="38535-175">Para obter mais informações sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="38535-175">For more information on Adaptive cards</span></span>

* [<span data-ttu-id="38535-176">Visão geral dos cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="38535-176">Adaptive Cards Overview</span></span>](/adaptive-cards/)
* [<span data-ttu-id="38535-177">Ações de cartão adaptáveis no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-177">Adaptive card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)

## <a name="hero-card"></a><span data-ttu-id="38535-178">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="38535-178">Hero card</span></span>

<span data-ttu-id="38535-179">Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="38535-179">A card that typically contains a single large image, one or more buttons and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="38535-180">Suporte para cartões hero</span><span class="sxs-lookup"><span data-stu-id="38535-180">Support for Hero cards</span></span>

| <span data-ttu-id="38535-181">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-181">Bots in Teams</span></span> | <span data-ttu-id="38535-182">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-182">Messaging Extensions</span></span>  | <span data-ttu-id="38535-183">Conectores</span><span class="sxs-lookup"><span data-stu-id="38535-183">Connectors</span></span> | <span data-ttu-id="38535-184">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="38535-184">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="38535-185">✔</span><span class="sxs-lookup"><span data-stu-id="38535-185">✔</span></span> | <span data-ttu-id="38535-186">✔</span><span class="sxs-lookup"><span data-stu-id="38535-186">✔</span></span> | <span data-ttu-id="38535-187">✖</span><span class="sxs-lookup"><span data-stu-id="38535-187">✖</span></span> | <span data-ttu-id="38535-188">✔</span><span class="sxs-lookup"><span data-stu-id="38535-188">✔</span></span> |
|

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="38535-189">Propriedades de um cartão Hero</span><span class="sxs-lookup"><span data-stu-id="38535-189">Properties of a Hero card</span></span>

| <span data-ttu-id="38535-190">Propriedade</span><span class="sxs-lookup"><span data-stu-id="38535-190">Property</span></span> | <span data-ttu-id="38535-191">Tipo</span><span class="sxs-lookup"><span data-stu-id="38535-191">Type</span></span>  | <span data-ttu-id="38535-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="38535-192">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="38535-193">title</span><span class="sxs-lookup"><span data-stu-id="38535-193">title</span></span> | <span data-ttu-id="38535-194">Rich text </span><span class="sxs-lookup"><span data-stu-id="38535-194">Rich text</span></span> | <span data-ttu-id="38535-195">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-195">Title of the card.</span></span> <span data-ttu-id="38535-196">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="38535-196">Maximum 2 lines.</span></span> |
| <span data-ttu-id="38535-197">subtitle</span><span class="sxs-lookup"><span data-stu-id="38535-197">subtitle</span></span> | <span data-ttu-id="38535-198">Rich text </span><span class="sxs-lookup"><span data-stu-id="38535-198">Rich text</span></span> | <span data-ttu-id="38535-199">Subtítulo do cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-199">Subtitle of the card.</span></span> <span data-ttu-id="38535-200">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="38535-200">Maximum 2 lines.</span></span>|
| <span data-ttu-id="38535-201">texto</span><span class="sxs-lookup"><span data-stu-id="38535-201">text</span></span> | <span data-ttu-id="38535-202">Rich text </span><span class="sxs-lookup"><span data-stu-id="38535-202">Rich text</span></span> | <span data-ttu-id="38535-203">O texto aparece logo abaixo do subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação</span><span class="sxs-lookup"><span data-stu-id="38535-203">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="38535-204">images</span><span class="sxs-lookup"><span data-stu-id="38535-204">images</span></span> | <span data-ttu-id="38535-205">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="38535-205">Array of images</span></span> | <span data-ttu-id="38535-206">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-206">Image displayed at top of card.</span></span> <span data-ttu-id="38535-207">Taxa de proporção 16:9</span><span class="sxs-lookup"><span data-stu-id="38535-207">Aspect ratio 16:9</span></span> |
| <span data-ttu-id="38535-208">buttons</span><span class="sxs-lookup"><span data-stu-id="38535-208">buttons</span></span> | <span data-ttu-id="38535-209">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="38535-209">Array of action objects</span></span> | <span data-ttu-id="38535-210">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="38535-210">Set of actions applicable to the current card.</span></span> <span data-ttu-id="38535-211">Máximo de 6</span><span class="sxs-lookup"><span data-stu-id="38535-211">Maximum 6</span></span> |
| <span data-ttu-id="38535-212">tocar</span><span class="sxs-lookup"><span data-stu-id="38535-212">tap</span></span> | <span data-ttu-id="38535-213">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="38535-213">Action object</span></span> | <span data-ttu-id="38535-214">Essa ação será ativada quando o usuário tocar no próprio cartão</span><span class="sxs-lookup"><span data-stu-id="38535-214">This action will be activated when the user taps on the card itself</span></span> |
|

### <a name="example-hero-card"></a><span data-ttu-id="38535-215">Cartão hero de exemplo</span><span class="sxs-lookup"><span data-stu-id="38535-215">Example Hero card</span></span>

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

### <a name="for-more-information-on-hero-cards"></a><span data-ttu-id="38535-217">Para obter mais informações sobre cartões Hero</span><span class="sxs-lookup"><span data-stu-id="38535-217">For more information on Hero cards</span></span>

<span data-ttu-id="38535-218">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="38535-218">Bot Framework reference:</span></span>

* [<span data-ttu-id="38535-219">Nó de cartão de herói</span><span class="sxs-lookup"><span data-stu-id="38535-219">Hero card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/herocard)
* [<span data-ttu-id="38535-220">Cartão de herói C #</span><span class="sxs-lookup"><span data-stu-id="38535-220">Hero card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.herocard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="38535-221">Cartão de lista</span><span class="sxs-lookup"><span data-stu-id="38535-221">List card</span></span>

<span data-ttu-id="38535-222">O cartão de lista foi adicionado pelo Teams para fornecer funções além do que a coleção de listas pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="38535-222">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="38535-223">O cartão de lista fornece uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="38535-223">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="38535-224">Suporte para cartões de lista</span><span class="sxs-lookup"><span data-stu-id="38535-224">Support for List cards</span></span>

| <span data-ttu-id="38535-225">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-225">Bots in Teams</span></span> | <span data-ttu-id="38535-226">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-226">Messaging Extensions</span></span>  | <span data-ttu-id="38535-227">Conectores</span><span class="sxs-lookup"><span data-stu-id="38535-227">Connectors</span></span> | <span data-ttu-id="38535-228">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="38535-228">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="38535-229">✔</span><span class="sxs-lookup"><span data-stu-id="38535-229">✔</span></span> | <span data-ttu-id="38535-230">✖</span><span class="sxs-lookup"><span data-stu-id="38535-230">✖</span></span> | <span data-ttu-id="38535-231">✖</span><span class="sxs-lookup"><span data-stu-id="38535-231">✖</span></span> |<span data-ttu-id="38535-232">✔</span><span class="sxs-lookup"><span data-stu-id="38535-232">✔</span></span> |
|

### <a name="properties-of-a-list-card"></a><span data-ttu-id="38535-233">Propriedades de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="38535-233">Properties of a List card</span></span>

| <span data-ttu-id="38535-234">Propriedade</span><span class="sxs-lookup"><span data-stu-id="38535-234">Property</span></span> | <span data-ttu-id="38535-235">Tipo</span><span class="sxs-lookup"><span data-stu-id="38535-235">Type</span></span>  | <span data-ttu-id="38535-236">Descrição</span><span class="sxs-lookup"><span data-stu-id="38535-236">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="38535-237">title</span><span class="sxs-lookup"><span data-stu-id="38535-237">title</span></span> | <span data-ttu-id="38535-238">Rich text </span><span class="sxs-lookup"><span data-stu-id="38535-238">Rich text</span></span> | <span data-ttu-id="38535-239">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-239">Title of the card.</span></span> <span data-ttu-id="38535-240">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="38535-240">Maximum 2 lines.</span></span>|
| <span data-ttu-id="38535-241">items</span><span class="sxs-lookup"><span data-stu-id="38535-241">items</span></span> | <span data-ttu-id="38535-242">Matriz de itens de lista</span><span class="sxs-lookup"><span data-stu-id="38535-242">Array of list items</span></span>  ||
| <span data-ttu-id="38535-243">buttons</span><span class="sxs-lookup"><span data-stu-id="38535-243">buttons</span></span> | <span data-ttu-id="38535-244">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="38535-244">Array of action objects</span></span> | <span data-ttu-id="38535-245">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="38535-245">Set of actions applicable to the current card.</span></span> <span data-ttu-id="38535-246">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="38535-246">Maximum 6.</span></span> |

### <a name="example-list-card"></a><span data-ttu-id="38535-247">Cartão de lista de exemplo</span><span class="sxs-lookup"><span data-stu-id="38535-247">Example List card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="38535-248">Cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="38535-248">Office 365 connector card</span></span>

<span data-ttu-id="38535-249">Com suporte no Teams, não no Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="38535-249">Supported in Teams, not in Bot Framework.</span></span>

<span data-ttu-id="38535-250">O cartão do Conector do Office 365 fornece um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="38535-250">The Office 365 Connector card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="38535-251">Esse cartão encapsula um cartão de conector para que ele possa ser usado por bots.</span><span class="sxs-lookup"><span data-stu-id="38535-251">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="38535-252">Consulte a seção de observações para ver as diferenças entre cartões de conector e o cartão O365.</span><span class="sxs-lookup"><span data-stu-id="38535-252">See the notes section for differences between connector cards and the O365 card.</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="38535-253">Suporte para cartões de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="38535-253">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="38535-254">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-254">Bots in Teams</span></span> | <span data-ttu-id="38535-255">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-255">Messaging Extensions</span></span>  | <span data-ttu-id="38535-256">Conectores</span><span class="sxs-lookup"><span data-stu-id="38535-256">Connectors</span></span> | <span data-ttu-id="38535-257">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="38535-257">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="38535-258">✔</span><span class="sxs-lookup"><span data-stu-id="38535-258">✔</span></span> | <span data-ttu-id="38535-259">✔</span><span class="sxs-lookup"><span data-stu-id="38535-259">✔</span></span> | <span data-ttu-id="38535-260">✔</span><span class="sxs-lookup"><span data-stu-id="38535-260">✔</span></span> | <span data-ttu-id="38535-261">✖</span><span class="sxs-lookup"><span data-stu-id="38535-261">✖</span></span> |
|

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="38535-262">Propriedades do cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="38535-262">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="38535-263">Propriedade</span><span class="sxs-lookup"><span data-stu-id="38535-263">Property</span></span> | <span data-ttu-id="38535-264">Tipo</span><span class="sxs-lookup"><span data-stu-id="38535-264">Type</span></span>  | <span data-ttu-id="38535-265">Descrição</span><span class="sxs-lookup"><span data-stu-id="38535-265">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="38535-266">title</span><span class="sxs-lookup"><span data-stu-id="38535-266">title</span></span> | <span data-ttu-id="38535-267">Rich text </span><span class="sxs-lookup"><span data-stu-id="38535-267">Rich text</span></span> | <span data-ttu-id="38535-268">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-268">Title of the card.</span></span> <span data-ttu-id="38535-269">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="38535-269">Maximum 2 lines.</span></span> |
| <span data-ttu-id="38535-270">summary</span><span class="sxs-lookup"><span data-stu-id="38535-270">summary</span></span> | <span data-ttu-id="38535-271">Rich text </span><span class="sxs-lookup"><span data-stu-id="38535-271">Rich text</span></span> | <span data-ttu-id="38535-272">Resumo do cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-272">Summary of the card.</span></span> <span data-ttu-id="38535-273">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="38535-273">Maximum 2 lines.</span></span> |
| <span data-ttu-id="38535-274">texto</span><span class="sxs-lookup"><span data-stu-id="38535-274">text</span></span> | <span data-ttu-id="38535-275">Rich text </span><span class="sxs-lookup"><span data-stu-id="38535-275">Rich text</span></span> | <span data-ttu-id="38535-276">O texto aparece logo abaixo do subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação</span><span class="sxs-lookup"><span data-stu-id="38535-276">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="38535-277">themeColor</span><span class="sxs-lookup"><span data-stu-id="38535-277">themeColor</span></span> | <span data-ttu-id="38535-278">Cadeia de caracteres HEX</span><span class="sxs-lookup"><span data-stu-id="38535-278">HEX string</span></span> | <span data-ttu-id="38535-279">color that overrides the accentColor provided from the application manifest</span><span class="sxs-lookup"><span data-stu-id="38535-279">color that overrides the accentColor provided from the application manifest</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="38535-280">Observações sobre o cartão de conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="38535-280">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="38535-281">Os cartões do Conector do Office 365 funcionam corretamente no Microsoft Teams, incluindo [ações ActionCard.](/outlook/actionable-messages/card-reference#actioncard-action)</span><span class="sxs-lookup"><span data-stu-id="38535-281">Office 365 Connector cards function properly on Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="38535-282">Uma diferença importante entre usar cartões do Conector de um Conector e usar cartões do Conector em seu bot é o tratamento de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-282">One important difference between using Connector cards from a Connector and using Connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="38535-283">Para um Conector, o ponto de extremidade recebe a carga do cartão via HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="38535-283">For a Connector, the endpoint receives the card payload via HTTP POST.</span></span>
* <span data-ttu-id="38535-284">Para um bot, a ação dispara uma atividade que envia apenas a ID de ação `HttpPOST` e o corpo para o `invoke` bot.</span><span class="sxs-lookup"><span data-stu-id="38535-284">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="38535-285">Cada cartão do Conector pode exibir no máximo 10 seções, e cada seção pode conter no máximo 5 imagens e 5 ações.</span><span class="sxs-lookup"><span data-stu-id="38535-285">Each Connector card can display a maximum of 10 sections, and each section can contain a maximum of 5 images and 5 actions.</span></span>

> [!NOTE]
> <span data-ttu-id="38535-286">Quaisquer seções, imagens ou ações adicionais em uma mensagem não serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="38535-286">Any additional sections, images, or actions in a message will not appear.</span></span>

<span data-ttu-id="38535-287">Todos os campos de texto suportam Markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="38535-287">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="38535-288">Você pode controlar quais seções usam Markdown ou HTML definindo `markdown` a propriedade em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="38535-288">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="38535-289">Por padrão, `markdown` é definido como ; se você quiser usar HTML em vez `true` disso, de definida como `markdown` `false` .</span><span class="sxs-lookup"><span data-stu-id="38535-289">By default, `markdown` is set to `true`; if you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="38535-290">Se você especificar a `themeColor` propriedade, ela substituirá `accentColor` a propriedade no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38535-290">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="38535-291">Para especificar o estilo de `activityImage` renderização, você pode definir `activityImageType` da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="38535-291">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows.</span></span>

| <span data-ttu-id="38535-292">Valor</span><span class="sxs-lookup"><span data-stu-id="38535-292">Value</span></span> | <span data-ttu-id="38535-293">Descrição</span><span class="sxs-lookup"><span data-stu-id="38535-293">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="38535-294">Padrão; `activityImage` será cortada como um círculo</span><span class="sxs-lookup"><span data-stu-id="38535-294">Default; `activityImage` will be cropped as a circle</span></span> |
| `article` | <span data-ttu-id="38535-295">`activityImage` será exibido como um retângulo e manterá sua taxa de proporção</span><span class="sxs-lookup"><span data-stu-id="38535-295">`activityImage` will be displayed as a rectangle and retain its aspect ratio</span></span> |

<span data-ttu-id="38535-296">Para obter todos os outros detalhes sobre as propriedades do cartão do Conector, consulte a referência [de cartão de mensagem a actionable.](/outlook/actionable-messages/card-reference)</span><span class="sxs-lookup"><span data-stu-id="38535-296">For all other details about Connector card properties, see the [Actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="38535-297">As únicas propriedades de cartão conector que o Microsoft Teams não dá suporte no momento são as seguinte:</span><span class="sxs-lookup"><span data-stu-id="38535-297">The only Connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="38535-298">`startGroup` (sempre tratado como `true` no Teams)</span><span class="sxs-lookup"><span data-stu-id="38535-298">`startGroup` (always treated as `true` in Teams)</span></span>
* `originator`
* `correlationId`

### <a name="example-office-365-connector-card"></a><span data-ttu-id="38535-299">Cartão de conector do Office 365 de exemplo</span><span class="sxs-lookup"><span data-stu-id="38535-299">Example Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="38535-300">Cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="38535-300">Receipt card</span></span>

<span data-ttu-id="38535-301">Com suporte no Teams.</span><span class="sxs-lookup"><span data-stu-id="38535-301">Supported in Teams.</span></span>

<span data-ttu-id="38535-302">Um cartão que permite que um bot forneça um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="38535-302">A card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="38535-303">Normalmente, ele contém a lista de itens a incluir no recibo, imposto e informações totais e outros textos.</span><span class="sxs-lookup"><span data-stu-id="38535-303">It typically contains the list of items to include on the receipt, tax and total information, and other text.</span></span>

### <a name="support-for-receipts-cards"></a><span data-ttu-id="38535-304">Suporte para cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="38535-304">Support for Receipts cards</span></span>

| <span data-ttu-id="38535-305">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-305">Bots in Teams</span></span> | <span data-ttu-id="38535-306">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-306">Messaging Extensions</span></span>  | <span data-ttu-id="38535-307">Conectores</span><span class="sxs-lookup"><span data-stu-id="38535-307">Connectors</span></span> | <span data-ttu-id="38535-308">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="38535-308">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="38535-309">✔</span><span class="sxs-lookup"><span data-stu-id="38535-309">✔</span></span> | <span data-ttu-id="38535-310">✔</span><span class="sxs-lookup"><span data-stu-id="38535-310">✔</span></span> | <span data-ttu-id="38535-311">✖</span><span class="sxs-lookup"><span data-stu-id="38535-311">✖</span></span> | <span data-ttu-id="38535-312">✔</span><span class="sxs-lookup"><span data-stu-id="38535-312">✔</span></span> |
|

### <a name="for-more-information-on-receipt-cards"></a><span data-ttu-id="38535-313">Para obter mais informações sobre cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="38535-313">For more information on Receipt cards</span></span>

<span data-ttu-id="38535-314">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="38535-314">Bot Framework reference:</span></span>

* [<span data-ttu-id="38535-315">Nó do cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="38535-315">Receipt card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="38535-316">Cartão de confirmação C #</span><span class="sxs-lookup"><span data-stu-id="38535-316">Receipt card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.receiptcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="38535-317">Signin card</span><span class="sxs-lookup"><span data-stu-id="38535-317">Signin card</span></span>

<span data-ttu-id="38535-318">Um cartão que permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="38535-318">A card that enables a bot to request that a user sign in.</span></span> <span data-ttu-id="38535-319">Com suporte no Teams de uma forma ligeiramente diferente da encontrada na Estrutura do Bot.</span><span class="sxs-lookup"><span data-stu-id="38535-319">Supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="38535-320">O cartão de visita no Teams é semelhante ao cartão de login na estrutura do bot, com a exceção de que o cartão de login no Teams só dá suporte a duas ações: `signin` e `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="38535-320">The signin card in Teams is similar to the signin card in the bot framework with the exception that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="38535-321">A *ação de entrar* pode ser usada em qualquer cartão no Teams, não apenas no cartão de visita.</span><span class="sxs-lookup"><span data-stu-id="38535-321">The *signin action* can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="38535-322">Confira o tópico Fluxo [de autenticação do Microsoft Teams para bots](~/bots/how-to/authentication/auth-flow-bot.md) para obter mais detalhes sobre autenticação.</span><span class="sxs-lookup"><span data-stu-id="38535-322">See the topic [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md) for more details on authentication.</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="38535-323">Suporte para cartões de login</span><span class="sxs-lookup"><span data-stu-id="38535-323">Support for Signin cards</span></span>

| <span data-ttu-id="38535-324">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-324">Bots in Teams</span></span> | <span data-ttu-id="38535-325">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-325">Messaging Extensions</span></span>  | <span data-ttu-id="38535-326">Conectores</span><span class="sxs-lookup"><span data-stu-id="38535-326">Connectors</span></span> | <span data-ttu-id="38535-327">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="38535-327">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="38535-328">✔</span><span class="sxs-lookup"><span data-stu-id="38535-328">✔</span></span> | <span data-ttu-id="38535-329">✖</span><span class="sxs-lookup"><span data-stu-id="38535-329">✖</span></span> | <span data-ttu-id="38535-330">✖</span><span class="sxs-lookup"><span data-stu-id="38535-330">✖</span></span> | <span data-ttu-id="38535-331">✔</span><span class="sxs-lookup"><span data-stu-id="38535-331">✔</span></span> |
|

### <a name="for-more-information-on-signin-cards"></a><span data-ttu-id="38535-332">Para obter mais informações sobre cartões de login</span><span class="sxs-lookup"><span data-stu-id="38535-332">For more information on Signin cards</span></span>

<span data-ttu-id="38535-333">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="38535-333">Bot Framework reference:</span></span>

* [<span data-ttu-id="38535-334">Nó do cartão de conexão</span><span class="sxs-lookup"><span data-stu-id="38535-334">Signin card Node</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="38535-335">Signin card C #</span><span class="sxs-lookup"><span data-stu-id="38535-335">Signin card C#</span></span>](/dotnet/api/microsoft.bot.connector.signincard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="38535-336">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="38535-336">Thumbnail card</span></span>

<span data-ttu-id="38535-337">Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="38535-337">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="38535-338">Suporte para cartões de miniatura</span><span class="sxs-lookup"><span data-stu-id="38535-338">Support for Thumbnail cards</span></span>

| <span data-ttu-id="38535-339">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-339">Bots in Teams</span></span> | <span data-ttu-id="38535-340">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-340">Messaging Extensions</span></span>  | <span data-ttu-id="38535-341">Conectores</span><span class="sxs-lookup"><span data-stu-id="38535-341">Connectors</span></span> | <span data-ttu-id="38535-342">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="38535-342">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="38535-343">✔</span><span class="sxs-lookup"><span data-stu-id="38535-343">✔</span></span> | <span data-ttu-id="38535-344">✔</span><span class="sxs-lookup"><span data-stu-id="38535-344">✔</span></span> | <span data-ttu-id="38535-345">✖</span><span class="sxs-lookup"><span data-stu-id="38535-345">✖</span></span> | <span data-ttu-id="38535-346">✔</span><span class="sxs-lookup"><span data-stu-id="38535-346">✔</span></span> |
|

![Exemplo de um cartão em miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="38535-348">Propriedades de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="38535-348">Properties of a Thumbnail card</span></span>

| <span data-ttu-id="38535-349">Propriedade</span><span class="sxs-lookup"><span data-stu-id="38535-349">Property</span></span> | <span data-ttu-id="38535-350">Tipo</span><span class="sxs-lookup"><span data-stu-id="38535-350">Type</span></span>  | <span data-ttu-id="38535-351">Descrição</span><span class="sxs-lookup"><span data-stu-id="38535-351">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="38535-352">title</span><span class="sxs-lookup"><span data-stu-id="38535-352">title</span></span> | <span data-ttu-id="38535-353">Rich text </span><span class="sxs-lookup"><span data-stu-id="38535-353">Rich text</span></span> | <span data-ttu-id="38535-354">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-354">Title of the card.</span></span> <span data-ttu-id="38535-355">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="38535-355">Maximum 2 lines.</span></span>|
| <span data-ttu-id="38535-356">subtitle</span><span class="sxs-lookup"><span data-stu-id="38535-356">subtitle</span></span> | <span data-ttu-id="38535-357">Rich text </span><span class="sxs-lookup"><span data-stu-id="38535-357">Rich text</span></span> | <span data-ttu-id="38535-358">Subtítulo do cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-358">Subtitle of the card.</span></span> <span data-ttu-id="38535-359">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="38535-359">Maximum 2 lines.</span></span>|
| <span data-ttu-id="38535-360">texto</span><span class="sxs-lookup"><span data-stu-id="38535-360">text</span></span> | <span data-ttu-id="38535-361">Rich text </span><span class="sxs-lookup"><span data-stu-id="38535-361">Rich text</span></span> | <span data-ttu-id="38535-362">O texto aparece logo abaixo do subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação</span><span class="sxs-lookup"><span data-stu-id="38535-362">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="38535-363">images</span><span class="sxs-lookup"><span data-stu-id="38535-363">images</span></span> | <span data-ttu-id="38535-364">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="38535-364">Array of images</span></span> | <span data-ttu-id="38535-365">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="38535-365">Image displayed at top of card.</span></span> <span data-ttu-id="38535-366">Taxa de proporção 1:1 (quadrado)</span><span class="sxs-lookup"><span data-stu-id="38535-366">Aspect ratio 1:1 (square)</span></span> |
| <span data-ttu-id="38535-367">buttons</span><span class="sxs-lookup"><span data-stu-id="38535-367">buttons</span></span> | <span data-ttu-id="38535-368">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="38535-368">Array of action objects</span></span> | <span data-ttu-id="38535-369">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="38535-369">Set of actions applicable to the current card.</span></span> <span data-ttu-id="38535-370">Máximo de 6</span><span class="sxs-lookup"><span data-stu-id="38535-370">Maximum 6</span></span> |
| <span data-ttu-id="38535-371">tocar</span><span class="sxs-lookup"><span data-stu-id="38535-371">tap</span></span> | <span data-ttu-id="38535-372">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="38535-372">Action object</span></span> | <span data-ttu-id="38535-373">Essa ação será ativada quando o usuário tocar no próprio cartão</span><span class="sxs-lookup"><span data-stu-id="38535-373">This action will be activated when the user taps on the card itself</span></span> |
|

### <a name="example-thumbnail-card"></a><span data-ttu-id="38535-374">Cartão de miniatura de exemplo</span><span class="sxs-lookup"><span data-stu-id="38535-374">Example Thumbnail card</span></span>

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

### <a name="for-more-information"></a><span data-ttu-id="38535-375">Para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="38535-375">For more information</span></span>

<span data-ttu-id="38535-376">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="38535-376">Bot Framework reference:</span></span>

* [<span data-ttu-id="38535-377">Nó do cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="38535-377">Thumbnail card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="38535-378">Cartão de miniatura C #</span><span class="sxs-lookup"><span data-stu-id="38535-378">Thumbnail card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.thumbnailcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="38535-379">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="38535-379">Card collections</span></span>

<span data-ttu-id="38535-380">As coleções de cartões são suportadas no Teams.</span><span class="sxs-lookup"><span data-stu-id="38535-380">Card collections are supported in Teams.</span></span>

<span data-ttu-id="38535-381">Coleções de cartões: `builder.AttachmentLayout.carousel` e `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="38535-381">Card collections: `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="38535-382">Essas coleções contêm cartões adaptáveis, em forma de herói ou em miniatura.</span><span class="sxs-lookup"><span data-stu-id="38535-382">These collections contain Adaptive, Hero, or Thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="38535-383">Coleção Carousel</span><span class="sxs-lookup"><span data-stu-id="38535-383">Carousel collection</span></span>

<span data-ttu-id="38535-384">O [layout do carrossel](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="38535-384">The [carousel layout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="38535-385">Suporte para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="38535-385">Support for Carousel collections</span></span>

| <span data-ttu-id="38535-386">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-386">Bots in Teams</span></span> | <span data-ttu-id="38535-387">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-387">Messaging Extensions</span></span>  | <span data-ttu-id="38535-388">Conectores</span><span class="sxs-lookup"><span data-stu-id="38535-388">Connectors</span></span> | <span data-ttu-id="38535-389">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="38535-389">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="38535-390">✔</span><span class="sxs-lookup"><span data-stu-id="38535-390">✔</span></span> | <span data-ttu-id="38535-391">✖</span><span class="sxs-lookup"><span data-stu-id="38535-391">✖</span></span> | <span data-ttu-id="38535-392">✖</span><span class="sxs-lookup"><span data-stu-id="38535-392">✖</span></span> | <span data-ttu-id="38535-393">✔</span><span class="sxs-lookup"><span data-stu-id="38535-393">✔</span></span> |
|

> [!NOTE]
> <span data-ttu-id="38535-394">Um carrossel pode exibir no máximo 10 cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="38535-394">A carousel can display a maximum of 10 cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="38535-395">Propriedades de um cartão de carrossel</span><span class="sxs-lookup"><span data-stu-id="38535-395">Properties of a Carousel card</span></span>

<span data-ttu-id="38535-396">As propriedades de um cartão carrossel são iguais às dos cartões Hero e Thumbnail.</span><span class="sxs-lookup"><span data-stu-id="38535-396">Properties of a Carousel card are same as those of the Hero and Thumbnail cards.</span></span>

### <a name="example-carousel-collection"></a><span data-ttu-id="38535-397">Coleção Carousel de exemplo</span><span class="sxs-lookup"><span data-stu-id="38535-397">Example Carousel collection</span></span>

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="38535-399">Sintaxe para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="38535-399">Syntax for Carousel collections</span></span>

`builder.AttachmentLayoutTypes.Carousel`

## <a name="list-collection"></a><span data-ttu-id="38535-400">Listar coleção</span><span class="sxs-lookup"><span data-stu-id="38535-400">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="38535-401">Suporte para coleções de listas</span><span class="sxs-lookup"><span data-stu-id="38535-401">Support for List collections</span></span>

<span data-ttu-id="38535-402">O layout da lista mostra uma lista de cartões empilhados verticalmente, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="38535-402">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="38535-403">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-403">Bots in Teams</span></span> | <span data-ttu-id="38535-404">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="38535-404">Messaging Extensions</span></span>  | <span data-ttu-id="38535-405">Conectores</span><span class="sxs-lookup"><span data-stu-id="38535-405">Connectors</span></span> | <span data-ttu-id="38535-406">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="38535-406">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="38535-407">✔</span><span class="sxs-lookup"><span data-stu-id="38535-407">✔</span></span> | <span data-ttu-id="38535-408">✔</span><span class="sxs-lookup"><span data-stu-id="38535-408">✔</span></span> | <span data-ttu-id="38535-409">✖</span><span class="sxs-lookup"><span data-stu-id="38535-409">✖</span></span> | <span data-ttu-id="38535-410">✔</span><span class="sxs-lookup"><span data-stu-id="38535-410">✔</span></span> |
|

### <a name="example-list-collection"></a><span data-ttu-id="38535-411">Exemplo de coleção de listas</span><span class="sxs-lookup"><span data-stu-id="38535-411">Example List collection</span></span>

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

<span data-ttu-id="38535-413">As propriedades são iguais às do herói ou da miniatura.</span><span class="sxs-lookup"><span data-stu-id="38535-413">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="38535-414">Uma lista pode exibir no máximo 10 cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="38535-414">A list can display a maximum of 10 cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="38535-415">Algumas combinações de cartões de lista ainda não têm suporte no iOS e no Android.</span><span class="sxs-lookup"><span data-stu-id="38535-415">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="38535-416">Sintaxe para coleções de listas</span><span class="sxs-lookup"><span data-stu-id="38535-416">Syntax for List collections</span></span>

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="38535-417">Cartões não suportados no Teams</span><span class="sxs-lookup"><span data-stu-id="38535-417">Cards not supported in Teams</span></span>

<span data-ttu-id="38535-418">Os cartões a seguir são implementados pela Estrutura de Bot, mas NÃO são suportados pelo Teams.</span><span class="sxs-lookup"><span data-stu-id="38535-418">The following cards are implemented by the Bot Framework, but are NOT supported by Teams.</span></span>

* <span data-ttu-id="38535-419">Cartões de animação</span><span class="sxs-lookup"><span data-stu-id="38535-419">Animation cards</span></span>
* <span data-ttu-id="38535-420">Cartões de áudio</span><span class="sxs-lookup"><span data-stu-id="38535-420">Audio cards</span></span>
* <span data-ttu-id="38535-421">Placas de vídeo</span><span class="sxs-lookup"><span data-stu-id="38535-421">Video cards</span></span>
