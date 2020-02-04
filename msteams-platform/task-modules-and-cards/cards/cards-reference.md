---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Microsoft Teams
keywords: referência de cartões de bots
ms.openlocfilehash: 76b9cb7e2508d300deb2e3cd4f392fdb9850062d
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672657"
---
# <a name="cards-reference"></a><span data-ttu-id="50a5c-104">Referência de cartões</span><span class="sxs-lookup"><span data-stu-id="50a5c-104">Cards Reference</span></span>

<span data-ttu-id="50a5c-105">Os cartões listados nesta seção têm suporte em bots para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="50a5c-105">The cards listed in this section are supported in bots for Teams.</span></span> <span data-ttu-id="50a5c-106">Eles são baseados em cartões definidos pela estrutura de bot, mas o Microsoft Teams não dá suporte a todas as placas de estrutura de bot e adicionou alguns dos seus próprios.</span><span class="sxs-lookup"><span data-stu-id="50a5c-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span> <span data-ttu-id="50a5c-107">As diferenças são chamadas nas referências abaixo.</span><span class="sxs-lookup"><span data-stu-id="50a5c-107">Differences are called out in the references below.</span></span>

## <a name="card-examples"></a><span data-ttu-id="50a5c-108">Exemplos de cartões</span><span class="sxs-lookup"><span data-stu-id="50a5c-108">Card examples</span></span>

<span data-ttu-id="50a5c-109">Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do bot Builder (v3).</span><span class="sxs-lookup"><span data-stu-id="50a5c-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK (v3).</span></span> <span data-ttu-id="50a5c-110">Há também exemplos de código disponíveis no repositório do Microsoft/BotBuilder-Samples no GitHub.</span><span class="sxs-lookup"><span data-stu-id="50a5c-110">There are also code samples available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="50a5c-111">.NET</span><span class="sxs-lookup"><span data-stu-id="50a5c-111">.NET</span></span>
  * [<span data-ttu-id="50a5c-112">Adicionar cartões como anexos a mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-112">Add cards as attachments to messages</span></span>](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [<span data-ttu-id="50a5c-113">Código de exemplo de cartões (Construtor de bot v3)</span><span class="sxs-lookup"><span data-stu-id="50a5c-113">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/CSharp/cards-RichCards)
* <span data-ttu-id="50a5c-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="50a5c-114">Node.js</span></span>
  * [<span data-ttu-id="50a5c-115">Adicionar cartões como anexos a mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-115">Add cards as attachments to messages</span></span>](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [<span data-ttu-id="50a5c-116">Código de exemplo de cartões (Construtor de bot v3)</span><span class="sxs-lookup"><span data-stu-id="50a5c-116">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/Node/cards-RichCards)

## <a name="types-of-cards"></a><span data-ttu-id="50a5c-117">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="50a5c-117">Types of cards</span></span>

<span data-ttu-id="50a5c-118">Esta tabela mostra os tipos de cartões disponíveis para você.</span><span class="sxs-lookup"><span data-stu-id="50a5c-118">This table shows the types of cards available to you.</span></span>

| <span data-ttu-id="50a5c-119">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="50a5c-119">Card Type</span></span> | <span data-ttu-id="50a5c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="50a5c-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="50a5c-121">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="50a5c-121">Adaptive Card</span></span>](#adaptive-card) | <span data-ttu-id="50a5c-122">Cartão altamente personalizável que pode conter qualquer combinação de texto, voz, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="50a5c-122">Highly customizable card that can contain any combination of text, speech, images, buttons and input fields.</span></span> |
| [<span data-ttu-id="50a5c-123">Cartão herói</span><span class="sxs-lookup"><span data-stu-id="50a5c-123">Hero Card</span></span>](#hero-card) | <span data-ttu-id="50a5c-124">Normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="50a5c-124">Typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="50a5c-125">Cartão de lista</span><span class="sxs-lookup"><span data-stu-id="50a5c-125">List Card</span></span>](#list-card) | <span data-ttu-id="50a5c-126">Uma lista de rolagem dos itens.</span><span class="sxs-lookup"><span data-stu-id="50a5c-126">A scrolling list of items.</span></span> |
| [<span data-ttu-id="50a5c-127">Cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="50a5c-127">Office 365 Connector Card</span></span>](#office-365-connector-card) | <span data-ttu-id="50a5c-128">Layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="50a5c-128">Flexible layout with multiple sections, fields, images and actions.</span></span> |
| [<span data-ttu-id="50a5c-129">Cartão de recibo</span><span class="sxs-lookup"><span data-stu-id="50a5c-129">Receipt Card</span></span>](#receipt-card) | <span data-ttu-id="50a5c-130">Fornece um recibo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="50a5c-130">Provides a receipt to the user.</span></span> |
| [<span data-ttu-id="50a5c-131">Cartão de conexão</span><span class="sxs-lookup"><span data-stu-id="50a5c-131">Signin Card</span></span>](#signin-card) | <span data-ttu-id="50a5c-132">Permite que um bot solicite a entrada de um usuário.</span><span class="sxs-lookup"><span data-stu-id="50a5c-132">Enables a bot to request that a user sign in.</span></span> |
| [<span data-ttu-id="50a5c-133">Cartão de miniaturas</span><span class="sxs-lookup"><span data-stu-id="50a5c-133">Thumbnail Card</span></span>](#thumbnail-card) | <span data-ttu-id="50a5c-134">Normalmente contém uma única imagem em miniatura, um texto curto e um ou mais botões.</span><span class="sxs-lookup"><span data-stu-id="50a5c-134">Typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="50a5c-135">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="50a5c-135">Card Collections</span></span>](#card-collections) | <span data-ttu-id="50a5c-136">Usado para retornar vários itens em uma única resposta</span><span class="sxs-lookup"><span data-stu-id="50a5c-136">Used to return multiple items in a single response</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="50a5c-137">Propriedades comuns de todos os cartões</span><span class="sxs-lookup"><span data-stu-id="50a5c-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="50a5c-138">Imagens de cartões embutidos</span><span class="sxs-lookup"><span data-stu-id="50a5c-138">Inline card images</span></span>

<span data-ttu-id="50a5c-139">O cartão pode conter uma imagem embutida, incluindo um link para a imagem disponível publicamente.</span><span class="sxs-lookup"><span data-stu-id="50a5c-139">Your card can contain an inline image by including a link to your publically available image.</span></span> <span data-ttu-id="50a5c-140">Para fins de desempenho, recomendamos enfaticamente que você hospede sua imagem em uma CDN (rede de distribuição de conteúdo) pública.</span><span class="sxs-lookup"><span data-stu-id="50a5c-140">For performance purposes we highly recommend you host your image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="50a5c-141">As imagens são dimensionadas para cima ou para baixo em tamanho, mantendo a taxa de proporção para cobrir a área da imagem e, em seguida, cortadas do centro para obter a taxa de proporção apropriada para o cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="50a5c-142">As imagens devem ter no máximo 1024 × 1024 e 1 MB no formato PNG, JPEG ou GIF; GIF animado não é oficialmente suportado.</span><span class="sxs-lookup"><span data-stu-id="50a5c-142">Images must be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF is not officially supported.</span></span>

| <span data-ttu-id="50a5c-143">Propriedade</span><span class="sxs-lookup"><span data-stu-id="50a5c-143">Property</span></span> | <span data-ttu-id="50a5c-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="50a5c-144">Type</span></span>  | <span data-ttu-id="50a5c-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="50a5c-145">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="50a5c-146">url</span><span class="sxs-lookup"><span data-stu-id="50a5c-146">url</span></span> | <span data-ttu-id="50a5c-147">URL</span><span class="sxs-lookup"><span data-stu-id="50a5c-147">URL</span></span> | <span data-ttu-id="50a5c-148">URL HTTPS para a imagem</span><span class="sxs-lookup"><span data-stu-id="50a5c-148">HTTPS URL to the image</span></span> |
| <span data-ttu-id="50a5c-149">alt</span><span class="sxs-lookup"><span data-stu-id="50a5c-149">alt</span></span> | <span data-ttu-id="50a5c-150">String</span><span class="sxs-lookup"><span data-stu-id="50a5c-150">String</span></span> | <span data-ttu-id="50a5c-151">Descrição acessível da imagem</span><span class="sxs-lookup"><span data-stu-id="50a5c-151">Accessible description of the image</span></span> |

### <a name="buttons"></a><span data-ttu-id="50a5c-152">Botões</span><span class="sxs-lookup"><span data-stu-id="50a5c-152">Buttons</span></span>

<span data-ttu-id="50a5c-153">Os botões são exibidos empilhados na parte inferior do cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-153">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="50a5c-154">O texto do botão está sempre em uma única linha e será truncado se o texto exceder a largura do botão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-154">Button text is always on a single line and will be truncated if the text exceeds the button width.</span></span> <span data-ttu-id="50a5c-155">Qualquer outro botão além do número máximo suportado pelo cartão não será exibido.</span><span class="sxs-lookup"><span data-stu-id="50a5c-155">Any additional buttons beyond the maximum number supported by the card will not be shown.</span></span>

<span data-ttu-id="50a5c-156">Consulte [ações do cartão](~/task-modules-and-cards/cards/cards-actions.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="50a5c-156">See [Card Actions](~/task-modules-and-cards/cards/cards-actions.md) for more information.</span></span>

### <a name="card-formatting"></a><span data-ttu-id="50a5c-157">Formatação de cartão</span><span class="sxs-lookup"><span data-stu-id="50a5c-157">Card Formatting</span></span>

<span data-ttu-id="50a5c-158">Consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para obter mais informações sobre formatação de texto em cartões.</span><span class="sxs-lookup"><span data-stu-id="50a5c-158">See [Card Formatting](~/task-modules-and-cards/cards/cards-format.md) for more information on text formatting in cards.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="50a5c-159">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="50a5c-159">Adaptive card</span></span>

> [!NOTE]
> <span data-ttu-id="50a5c-160">Somente a versão 1,0 de cartões adaptáveis é suportada para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="50a5c-160">Only version 1.0 of Adaptive Cards is supported for all users.</span></span> <span data-ttu-id="50a5c-161">A versão 1,2 está atualmente disponível apenas na visualização do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="50a5c-161">Version 1.2 is currently available only in Developer Preview</span></span>

<span data-ttu-id="50a5c-162">Um cartão personalizável que pode conter qualquer combinação de texto, fala, imagem, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="50a5c-162">A customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="50a5c-163">Suporte para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="50a5c-163">Support for Adaptive cards</span></span>

| <span data-ttu-id="50a5c-164">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-164">Bots in Teams</span></span> | <span data-ttu-id="50a5c-165">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-165">Messaging Extensions</span></span>  | <span data-ttu-id="50a5c-166">Conectores</span><span class="sxs-lookup"><span data-stu-id="50a5c-166">Connectors</span></span> | <span data-ttu-id="50a5c-167">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="50a5c-167">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="50a5c-168">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-168">✔</span></span> | <span data-ttu-id="50a5c-169">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-169">✔</span></span> | <span data-ttu-id="50a5c-170">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-170">✖</span></span> | <span data-ttu-id="50a5c-171">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-171">✔</span></span> |
|

### <a name="example-adaptive-card"></a><span data-ttu-id="50a5c-172">Cartão adaptável de exemplo</span><span class="sxs-lookup"><span data-stu-id="50a5c-172">Example Adaptive card</span></span>

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

#### <a name="for-more-information-on-adaptive-cards"></a><span data-ttu-id="50a5c-174">Para obter mais informações sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="50a5c-174">For more information on Adaptive cards</span></span>

* [<span data-ttu-id="50a5c-175">Visão geral de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="50a5c-175">Adaptive Cards Overview</span></span>](/adaptive-cards/)
* [<span data-ttu-id="50a5c-176">Ações de cartão adaptável no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-176">Adaptive card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)

## <a name="hero-card"></a><span data-ttu-id="50a5c-177">Cartão herói</span><span class="sxs-lookup"><span data-stu-id="50a5c-177">Hero card</span></span>

<span data-ttu-id="50a5c-178">Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="50a5c-178">A card that typically contains a single large image, one or more buttons and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="50a5c-179">Suporte para cartões herói</span><span class="sxs-lookup"><span data-stu-id="50a5c-179">Support for Hero cards</span></span>

| <span data-ttu-id="50a5c-180">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-180">Bots in Teams</span></span> | <span data-ttu-id="50a5c-181">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-181">Messaging Extensions</span></span>  | <span data-ttu-id="50a5c-182">Conectores</span><span class="sxs-lookup"><span data-stu-id="50a5c-182">Connectors</span></span> | <span data-ttu-id="50a5c-183">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="50a5c-183">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="50a5c-184">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-184">✔</span></span> | <span data-ttu-id="50a5c-185">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-185">✔</span></span> | <span data-ttu-id="50a5c-186">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-186">✖</span></span> | <span data-ttu-id="50a5c-187">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-187">✔</span></span> |
|

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="50a5c-188">Propriedades de um cartão herói</span><span class="sxs-lookup"><span data-stu-id="50a5c-188">Properties of a Hero card</span></span>

| <span data-ttu-id="50a5c-189">Propriedade</span><span class="sxs-lookup"><span data-stu-id="50a5c-189">Property</span></span> | <span data-ttu-id="50a5c-190">Tipo</span><span class="sxs-lookup"><span data-stu-id="50a5c-190">Type</span></span>  | <span data-ttu-id="50a5c-191">Descrição</span><span class="sxs-lookup"><span data-stu-id="50a5c-191">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="50a5c-192">title</span><span class="sxs-lookup"><span data-stu-id="50a5c-192">title</span></span> | <span data-ttu-id="50a5c-193">Rich text </span><span class="sxs-lookup"><span data-stu-id="50a5c-193">Rich text</span></span> | <span data-ttu-id="50a5c-194">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-194">Title of the card.</span></span> <span data-ttu-id="50a5c-195">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="50a5c-195">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="50a5c-196">título</span><span class="sxs-lookup"><span data-stu-id="50a5c-196">subtitle</span></span> | <span data-ttu-id="50a5c-197">Rich text </span><span class="sxs-lookup"><span data-stu-id="50a5c-197">Rich text</span></span> | <span data-ttu-id="50a5c-198">Subtítulo do cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-198">Subtitle of the card.</span></span> <span data-ttu-id="50a5c-199">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="50a5c-199">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="50a5c-200">texto</span><span class="sxs-lookup"><span data-stu-id="50a5c-200">text</span></span> | <span data-ttu-id="50a5c-201">Rich text </span><span class="sxs-lookup"><span data-stu-id="50a5c-201">Rich text</span></span> | <span data-ttu-id="50a5c-202">O texto aparece logo abaixo do subtítulo; Veja [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação</span><span class="sxs-lookup"><span data-stu-id="50a5c-202">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="50a5c-203">imagem</span><span class="sxs-lookup"><span data-stu-id="50a5c-203">images</span></span> | <span data-ttu-id="50a5c-204">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-204">Array of images</span></span> | <span data-ttu-id="50a5c-205">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-205">Image displayed at top of card.</span></span> <span data-ttu-id="50a5c-206">Taxa de proporção 16:9</span><span class="sxs-lookup"><span data-stu-id="50a5c-206">Aspect ratio 16:9</span></span> |
| <span data-ttu-id="50a5c-207">recolhe</span><span class="sxs-lookup"><span data-stu-id="50a5c-207">buttons</span></span> | <span data-ttu-id="50a5c-208">Matriz de objetos Action</span><span class="sxs-lookup"><span data-stu-id="50a5c-208">Array of action objects</span></span> | <span data-ttu-id="50a5c-209">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="50a5c-209">Set of actions applicable to the current card.</span></span> <span data-ttu-id="50a5c-210">Máximo de 6</span><span class="sxs-lookup"><span data-stu-id="50a5c-210">Maximum 6</span></span> |
| <span data-ttu-id="50a5c-211">Aproveite</span><span class="sxs-lookup"><span data-stu-id="50a5c-211">tap</span></span> | <span data-ttu-id="50a5c-212">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="50a5c-212">Action object</span></span> | <span data-ttu-id="50a5c-213">Esta ação será ativada quando o usuário tocar no próprio cartão</span><span class="sxs-lookup"><span data-stu-id="50a5c-213">This action will be activated when the user taps on the card itself</span></span> |
|

### <a name="example-hero-card"></a><span data-ttu-id="50a5c-214">Cartão herói de exemplo</span><span class="sxs-lookup"><span data-stu-id="50a5c-214">Example Hero card</span></span>

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

### <a name="for-more-information-on-hero-cards"></a><span data-ttu-id="50a5c-216">Para obter mais informações sobre cartões de herói</span><span class="sxs-lookup"><span data-stu-id="50a5c-216">For more information on Hero cards</span></span>

<span data-ttu-id="50a5c-217">Referência da estrutura do bot:</span><span class="sxs-lookup"><span data-stu-id="50a5c-217">Bot Framework reference:</span></span>

* [<span data-ttu-id="50a5c-218">Nó do cartão herói</span><span class="sxs-lookup"><span data-stu-id="50a5c-218">Hero card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/herocard)
* [<span data-ttu-id="50a5c-219">Cartão herói C #</span><span class="sxs-lookup"><span data-stu-id="50a5c-219">Hero card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.herocard?view=botbuilder-dotnet-3.0)

## <a name="list-card"></a><span data-ttu-id="50a5c-220">Cartão de lista</span><span class="sxs-lookup"><span data-stu-id="50a5c-220">List card</span></span>

<span data-ttu-id="50a5c-221">O cartão de lista foi adicionado pelo Microsoft Teams para fornecer funções além do que a coleção List pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="50a5c-221">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="50a5c-222">O cartão de lista fornece uma lista de rolagem dos itens.</span><span class="sxs-lookup"><span data-stu-id="50a5c-222">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="50a5c-223">Suporte para cartões de lista</span><span class="sxs-lookup"><span data-stu-id="50a5c-223">Support for List cards</span></span>

| <span data-ttu-id="50a5c-224">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-224">Bots in Teams</span></span> | <span data-ttu-id="50a5c-225">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-225">Messaging Extensions</span></span>  | <span data-ttu-id="50a5c-226">Conectores</span><span class="sxs-lookup"><span data-stu-id="50a5c-226">Connectors</span></span> | <span data-ttu-id="50a5c-227">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="50a5c-227">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="50a5c-228">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-228">✔</span></span> | <span data-ttu-id="50a5c-229">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-229">✖</span></span> | <span data-ttu-id="50a5c-230">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-230">✖</span></span> |<span data-ttu-id="50a5c-231">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-231">✔</span></span> |
|

### <a name="properties-of-a-list-card"></a><span data-ttu-id="50a5c-232">Propriedades de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="50a5c-232">Properties of a List card</span></span>

| <span data-ttu-id="50a5c-233">Propriedade</span><span class="sxs-lookup"><span data-stu-id="50a5c-233">Property</span></span> | <span data-ttu-id="50a5c-234">Tipo</span><span class="sxs-lookup"><span data-stu-id="50a5c-234">Type</span></span>  | <span data-ttu-id="50a5c-235">Descrição</span><span class="sxs-lookup"><span data-stu-id="50a5c-235">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="50a5c-236">title</span><span class="sxs-lookup"><span data-stu-id="50a5c-236">title</span></span> | <span data-ttu-id="50a5c-237">Rich text </span><span class="sxs-lookup"><span data-stu-id="50a5c-237">Rich text</span></span> | <span data-ttu-id="50a5c-238">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-238">Title of the card.</span></span> <span data-ttu-id="50a5c-239">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="50a5c-239">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="50a5c-240">items</span><span class="sxs-lookup"><span data-stu-id="50a5c-240">items</span></span> | <span data-ttu-id="50a5c-241">Matriz de itens de lista</span><span class="sxs-lookup"><span data-stu-id="50a5c-241">Array of list items</span></span>  ||
| <span data-ttu-id="50a5c-242">recolhe</span><span class="sxs-lookup"><span data-stu-id="50a5c-242">buttons</span></span> | <span data-ttu-id="50a5c-243">Matriz de objetos Action</span><span class="sxs-lookup"><span data-stu-id="50a5c-243">Array of action objects</span></span> | <span data-ttu-id="50a5c-244">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="50a5c-244">Set of actions applicable to the current card.</span></span> <span data-ttu-id="50a5c-245">Máximo de 6.</span><span class="sxs-lookup"><span data-stu-id="50a5c-245">Maximum 6.</span></span> <span data-ttu-id="50a5c-246">Não processa em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="50a5c-246">Does not render on mobile.</span></span> |
|

### <a name="example-list-card"></a><span data-ttu-id="50a5c-247">Exemplo de cartão de lista</span><span class="sxs-lookup"><span data-stu-id="50a5c-247">Example List card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="50a5c-248">Cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="50a5c-248">Office 365 connector card</span></span>

<span data-ttu-id="50a5c-249">Com suporte no Teams, não na estrutura de bot.</span><span class="sxs-lookup"><span data-stu-id="50a5c-249">Supported in Teams, not in Bot Framework.</span></span>

<span data-ttu-id="50a5c-250">O cartão de conexão do Office 365 fornece um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="50a5c-250">The Office 365 Connector card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="50a5c-251">Este cartão encapsula um cartão de conexão para que possa ser usado por bots.</span><span class="sxs-lookup"><span data-stu-id="50a5c-251">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="50a5c-252">Consulte a seção observações para ver as diferenças entre os cartões de conector e o cartão do O365.</span><span class="sxs-lookup"><span data-stu-id="50a5c-252">See the notes section for differences between connector cards and the O365 card.</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="50a5c-253">Suporte para cartões conectores do Office 365</span><span class="sxs-lookup"><span data-stu-id="50a5c-253">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="50a5c-254">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-254">Bots in Teams</span></span> | <span data-ttu-id="50a5c-255">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-255">Messaging Extensions</span></span>  | <span data-ttu-id="50a5c-256">Conectores</span><span class="sxs-lookup"><span data-stu-id="50a5c-256">Connectors</span></span> | <span data-ttu-id="50a5c-257">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="50a5c-257">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="50a5c-258">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-258">✔</span></span> | <span data-ttu-id="50a5c-259">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-259">✔</span></span> | <span data-ttu-id="50a5c-260">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-260">✔</span></span> | <span data-ttu-id="50a5c-261">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-261">✖</span></span> |
|

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="50a5c-262">Propriedades do cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="50a5c-262">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="50a5c-263">Propriedade</span><span class="sxs-lookup"><span data-stu-id="50a5c-263">Property</span></span> | <span data-ttu-id="50a5c-264">Tipo</span><span class="sxs-lookup"><span data-stu-id="50a5c-264">Type</span></span>  | <span data-ttu-id="50a5c-265">Descrição</span><span class="sxs-lookup"><span data-stu-id="50a5c-265">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="50a5c-266">title</span><span class="sxs-lookup"><span data-stu-id="50a5c-266">title</span></span> | <span data-ttu-id="50a5c-267">Rich text </span><span class="sxs-lookup"><span data-stu-id="50a5c-267">Rich text</span></span> | <span data-ttu-id="50a5c-268">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-268">Title of the card.</span></span> <span data-ttu-id="50a5c-269">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="50a5c-269">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="50a5c-270">summary</span><span class="sxs-lookup"><span data-stu-id="50a5c-270">summary</span></span> | <span data-ttu-id="50a5c-271">Rich text </span><span class="sxs-lookup"><span data-stu-id="50a5c-271">Rich text</span></span> | <span data-ttu-id="50a5c-272">Resumo do cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-272">Summary of the card.</span></span> <span data-ttu-id="50a5c-273">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="50a5c-273">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="50a5c-274">texto</span><span class="sxs-lookup"><span data-stu-id="50a5c-274">text</span></span> | <span data-ttu-id="50a5c-275">Rich text </span><span class="sxs-lookup"><span data-stu-id="50a5c-275">Rich text</span></span> | <span data-ttu-id="50a5c-276">O texto aparece logo abaixo do subtítulo; Veja [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação</span><span class="sxs-lookup"><span data-stu-id="50a5c-276">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="50a5c-277">themeColor</span><span class="sxs-lookup"><span data-stu-id="50a5c-277">themeColor</span></span> | <span data-ttu-id="50a5c-278">Cadeia de caracteres HEX</span><span class="sxs-lookup"><span data-stu-id="50a5c-278">HEX string</span></span> | <span data-ttu-id="50a5c-279">cor que substitui o accentColor fornecido do manifesto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="50a5c-279">color that overrides the accentColor provided from the application manifest</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="50a5c-280">Observações sobre o cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="50a5c-280">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="50a5c-281">Os cartões conectores do Office 365 funcionam corretamente no Microsoft Teams, incluindo [ações ActionCard](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="50a5c-281">Office 365 Connector cards function properly on Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="50a5c-282">Uma diferença importante entre o uso de cartões de conexão de um conector e o uso de cartões de conector no bot é a manipulação de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-282">One important difference between using Connector cards from a Connector and using Connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="50a5c-283">Para um conector, o ponto de extremidade recebe a carga do cartão via HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="50a5c-283">For a Connector, the endpoint receives the card payload via HTTP POST.</span></span>
* <span data-ttu-id="50a5c-284">Para um bot, a `HttpPOST` ação dispara uma `invoke` atividade que envia apenas a ID e o corpo da ação para o bot.</span><span class="sxs-lookup"><span data-stu-id="50a5c-284">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="50a5c-285">Cada placa de conector pode exibir um máximo de 10 seções e cada seção pode conter no máximo 5 imagens e 5 ações.</span><span class="sxs-lookup"><span data-stu-id="50a5c-285">Each Connector card can display a maximum of 10 sections, and each section can contain a maximum of 5 images and 5 actions.</span></span>

> [!NOTE]
> <span data-ttu-id="50a5c-286">Quaisquer seções, imagens ou ações adicionais em uma mensagem não serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="50a5c-286">Any additional sections, images, or actions in a message will not appear.</span></span>

<span data-ttu-id="50a5c-287">Todos os campos de texto dão suporte a redução e HTML.</span><span class="sxs-lookup"><span data-stu-id="50a5c-287">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="50a5c-288">Você pode controlar quais seções usam a redução ou HTML, definindo `markdown` a propriedade em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="50a5c-288">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="50a5c-289">Por padrão, `markdown` é definido como `true`; Se você quiser usar HTML em vez disso, `markdown` defina `false`como.</span><span class="sxs-lookup"><span data-stu-id="50a5c-289">By default, `markdown` is set to `true`; if you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="50a5c-290">Se você especificar a `themeColor` Propriedade, ela substituirá `accentColor` a propriedade no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="50a5c-290">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="50a5c-291">Para especificar o estilo de renderização `activityImage`para, você pode `activityImageType` definir como a seguir.</span><span class="sxs-lookup"><span data-stu-id="50a5c-291">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows.</span></span>

| <span data-ttu-id="50a5c-292">Valor</span><span class="sxs-lookup"><span data-stu-id="50a5c-292">Value</span></span> | <span data-ttu-id="50a5c-293">Descrição</span><span class="sxs-lookup"><span data-stu-id="50a5c-293">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="50a5c-294">Será `activityImage` será cortado como um círculo</span><span class="sxs-lookup"><span data-stu-id="50a5c-294">Default; `activityImage` will be cropped as a circle</span></span> |
| `article` | <span data-ttu-id="50a5c-295">`activityImage`será exibido como um retângulo e manterá sua taxa de proporção</span><span class="sxs-lookup"><span data-stu-id="50a5c-295">`activityImage` will be displayed as a rectangle and retain its aspect ratio</span></span> |

<span data-ttu-id="50a5c-296">Para todos os outros detalhes sobre as propriedades do cartão de conexão, confira a [referência de cartão de mensagem acionável](/outlook/actionable-messages/card-reference).</span><span class="sxs-lookup"><span data-stu-id="50a5c-296">For all other details about Connector card properties, see the [Actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="50a5c-297">As únicas propriedades da placa de conector que o Microsoft Teams não suporta atualmente são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="50a5c-297">The only Connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="50a5c-298">`startGroup`(sempre tratado como `true` no Teams)</span><span class="sxs-lookup"><span data-stu-id="50a5c-298">`startGroup` (always treated as `true` in Teams)</span></span>
* `originator`
* `correlationId`

### <a name="example-office-365-connector-card"></a><span data-ttu-id="50a5c-299">Cartão de conexão de exemplo do Office 365</span><span class="sxs-lookup"><span data-stu-id="50a5c-299">Example Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="50a5c-300">Cartão de recibo</span><span class="sxs-lookup"><span data-stu-id="50a5c-300">Receipt card</span></span>

<span data-ttu-id="50a5c-301">Com suporte no Teams.</span><span class="sxs-lookup"><span data-stu-id="50a5c-301">Supported in Teams.</span></span>

<span data-ttu-id="50a5c-302">Um cartão que permite que um bot forneça um recibo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="50a5c-302">A card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="50a5c-303">Normalmente, ela contém a lista de itens a serem incluídos no recebimento, no imposto e nas informações totais e em outros textos.</span><span class="sxs-lookup"><span data-stu-id="50a5c-303">It typically contains the list of items to include on the receipt, tax and total information, and other text.</span></span>

### <a name="support-for-receipts-cards"></a><span data-ttu-id="50a5c-304">Suporte para cartões de recibos</span><span class="sxs-lookup"><span data-stu-id="50a5c-304">Support for Receipts cards</span></span>

| <span data-ttu-id="50a5c-305">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-305">Bots in Teams</span></span> | <span data-ttu-id="50a5c-306">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-306">Messaging Extensions</span></span>  | <span data-ttu-id="50a5c-307">Conectores</span><span class="sxs-lookup"><span data-stu-id="50a5c-307">Connectors</span></span> | <span data-ttu-id="50a5c-308">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="50a5c-308">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="50a5c-309">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-309">✔</span></span> | <span data-ttu-id="50a5c-310">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-310">✔</span></span> | <span data-ttu-id="50a5c-311">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-311">✖</span></span> | <span data-ttu-id="50a5c-312">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-312">✔</span></span> |
|

### <a name="for-more-information-on-receipt-cards"></a><span data-ttu-id="50a5c-313">Para obter mais informações sobre cartões de recibo</span><span class="sxs-lookup"><span data-stu-id="50a5c-313">For more information on Receipt cards</span></span>

<span data-ttu-id="50a5c-314">Referência da estrutura do bot:</span><span class="sxs-lookup"><span data-stu-id="50a5c-314">Bot Framework reference:</span></span>

* [<span data-ttu-id="50a5c-315">Nó do cartão de recibo</span><span class="sxs-lookup"><span data-stu-id="50a5c-315">Receipt card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest)
* [<span data-ttu-id="50a5c-316">Cartão de recibo C #</span><span class="sxs-lookup"><span data-stu-id="50a5c-316">Receipt card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.receiptcard?view=botbuilder-dotnet-3.0)

## <a name="signin-card"></a><span data-ttu-id="50a5c-317">Cartão de conexão</span><span class="sxs-lookup"><span data-stu-id="50a5c-317">Signin card</span></span>

<span data-ttu-id="50a5c-318">Um cartão que permite que um bot solicite a entrada de um usuário.</span><span class="sxs-lookup"><span data-stu-id="50a5c-318">A card that enables a bot to request that a user sign in.</span></span> <span data-ttu-id="50a5c-319">Suportado no Teams em um formato levemente diferente do que é encontrado na estrutura de bot.</span><span class="sxs-lookup"><span data-stu-id="50a5c-319">Supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="50a5c-320">O cartão de entrada no Microsoft Teams é semelhante ao cartão de entrada na estrutura de bot com a exceção de que o cartão de entrada no Microsoft Teams suporta `signin` apenas `openUrl`duas ações: e.</span><span class="sxs-lookup"><span data-stu-id="50a5c-320">The signin card in Teams is similar to the signin card in the bot framework with the exception that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="50a5c-321">A *ação de entrada* pode ser usada de qualquer cartão no Microsoft Teams, e não apenas do cartão de entrada.</span><span class="sxs-lookup"><span data-stu-id="50a5c-321">The *signin action* can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="50a5c-322">Consulte o tópico [Microsoft Teams Authentication Flow para bots](~/bots/how-to/authentication/auth-flow-bot.md) para obter mais detalhes sobre autenticação.</span><span class="sxs-lookup"><span data-stu-id="50a5c-322">See the topic [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md) for more details on authentication.</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="50a5c-323">Suporte para placas de entrada</span><span class="sxs-lookup"><span data-stu-id="50a5c-323">Support for Signin cards</span></span>

| <span data-ttu-id="50a5c-324">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-324">Bots in Teams</span></span> | <span data-ttu-id="50a5c-325">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-325">Messaging Extensions</span></span>  | <span data-ttu-id="50a5c-326">Conectores</span><span class="sxs-lookup"><span data-stu-id="50a5c-326">Connectors</span></span> | <span data-ttu-id="50a5c-327">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="50a5c-327">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="50a5c-328">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-328">✔</span></span> | <span data-ttu-id="50a5c-329">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-329">✖</span></span> | <span data-ttu-id="50a5c-330">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-330">✖</span></span> | <span data-ttu-id="50a5c-331">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-331">✔</span></span> |
|

### <a name="for-more-information-on-signin-cards"></a><span data-ttu-id="50a5c-332">Para obter mais informações sobre cartões de conexão</span><span class="sxs-lookup"><span data-stu-id="50a5c-332">For more information on Signin cards</span></span>

<span data-ttu-id="50a5c-333">Referência da estrutura do bot:</span><span class="sxs-lookup"><span data-stu-id="50a5c-333">Bot Framework reference:</span></span>

* [<span data-ttu-id="50a5c-334">Nó do cartão de entrada</span><span class="sxs-lookup"><span data-stu-id="50a5c-334">Signin card Node</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest)
* [<span data-ttu-id="50a5c-335">Cartão de entrada C #</span><span class="sxs-lookup"><span data-stu-id="50a5c-335">Signin card C#</span></span>](/dotnet/api/microsoft.bot.connector.signincard?view=botbuilder-dotnet-3.0)

## <a name="thumbnail-card"></a><span data-ttu-id="50a5c-336">Cartão de miniaturas</span><span class="sxs-lookup"><span data-stu-id="50a5c-336">Thumbnail card</span></span>

<span data-ttu-id="50a5c-337">Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="50a5c-337">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="50a5c-338">Suporte para cartões em miniatura</span><span class="sxs-lookup"><span data-stu-id="50a5c-338">Support for Thumbnail cards</span></span>

| <span data-ttu-id="50a5c-339">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-339">Bots in Teams</span></span> | <span data-ttu-id="50a5c-340">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-340">Messaging Extensions</span></span>  | <span data-ttu-id="50a5c-341">Conectores</span><span class="sxs-lookup"><span data-stu-id="50a5c-341">Connectors</span></span> | <span data-ttu-id="50a5c-342">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="50a5c-342">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="50a5c-343">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-343">✔</span></span> | <span data-ttu-id="50a5c-344">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-344">✔</span></span> | <span data-ttu-id="50a5c-345">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-345">✖</span></span> | <span data-ttu-id="50a5c-346">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-346">✔</span></span> |
|

![Exemplo de um cartão em miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="50a5c-348">Propriedades de um cartão em miniatura</span><span class="sxs-lookup"><span data-stu-id="50a5c-348">Properties of a Thumbnail card</span></span>

| <span data-ttu-id="50a5c-349">Propriedade</span><span class="sxs-lookup"><span data-stu-id="50a5c-349">Property</span></span> | <span data-ttu-id="50a5c-350">Tipo</span><span class="sxs-lookup"><span data-stu-id="50a5c-350">Type</span></span>  | <span data-ttu-id="50a5c-351">Descrição</span><span class="sxs-lookup"><span data-stu-id="50a5c-351">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="50a5c-352">title</span><span class="sxs-lookup"><span data-stu-id="50a5c-352">title</span></span> | <span data-ttu-id="50a5c-353">Rich text </span><span class="sxs-lookup"><span data-stu-id="50a5c-353">Rich text</span></span> | <span data-ttu-id="50a5c-354">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-354">Title of the card.</span></span> <span data-ttu-id="50a5c-355">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="50a5c-355">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="50a5c-356">título</span><span class="sxs-lookup"><span data-stu-id="50a5c-356">subtitle</span></span> | <span data-ttu-id="50a5c-357">Rich text </span><span class="sxs-lookup"><span data-stu-id="50a5c-357">Rich text</span></span> | <span data-ttu-id="50a5c-358">Subtítulo do cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-358">Subtitle of the card.</span></span> <span data-ttu-id="50a5c-359">Máximo de 2 linhas; formatação não suportada atualmente</span><span class="sxs-lookup"><span data-stu-id="50a5c-359">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="50a5c-360">texto</span><span class="sxs-lookup"><span data-stu-id="50a5c-360">text</span></span> | <span data-ttu-id="50a5c-361">Rich text </span><span class="sxs-lookup"><span data-stu-id="50a5c-361">Rich text</span></span> | <span data-ttu-id="50a5c-362">O texto aparece logo abaixo do subtítulo; Veja [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação</span><span class="sxs-lookup"><span data-stu-id="50a5c-362">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="50a5c-363">imagem</span><span class="sxs-lookup"><span data-stu-id="50a5c-363">images</span></span> | <span data-ttu-id="50a5c-364">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-364">Array of images</span></span> | <span data-ttu-id="50a5c-365">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="50a5c-365">Image displayed at top of card.</span></span> <span data-ttu-id="50a5c-366">Taxa de proporção 1:1 (quadrado)</span><span class="sxs-lookup"><span data-stu-id="50a5c-366">Aspect ratio 1:1 (square)</span></span> |
| <span data-ttu-id="50a5c-367">recolhe</span><span class="sxs-lookup"><span data-stu-id="50a5c-367">buttons</span></span> | <span data-ttu-id="50a5c-368">Matriz de objetos Action</span><span class="sxs-lookup"><span data-stu-id="50a5c-368">Array of action objects</span></span> | <span data-ttu-id="50a5c-369">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="50a5c-369">Set of actions applicable to the current card.</span></span> <span data-ttu-id="50a5c-370">Máximo de 6</span><span class="sxs-lookup"><span data-stu-id="50a5c-370">Maximum 6</span></span> |
| <span data-ttu-id="50a5c-371">Aproveite</span><span class="sxs-lookup"><span data-stu-id="50a5c-371">tap</span></span> | <span data-ttu-id="50a5c-372">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="50a5c-372">Action object</span></span> | <span data-ttu-id="50a5c-373">Esta ação será ativada quando o usuário tocar no próprio cartão</span><span class="sxs-lookup"><span data-stu-id="50a5c-373">This action will be activated when the user taps on the card itself</span></span> |
|

### <a name="example-thumbnail-card"></a><span data-ttu-id="50a5c-374">Cartão de miniatura de exemplo</span><span class="sxs-lookup"><span data-stu-id="50a5c-374">Example Thumbnail card</span></span>

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

### <a name="for-more-information"></a><span data-ttu-id="50a5c-375">Para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="50a5c-375">For more information</span></span>

<span data-ttu-id="50a5c-376">Referência da estrutura do bot:</span><span class="sxs-lookup"><span data-stu-id="50a5c-376">Bot Framework reference:</span></span>

* [<span data-ttu-id="50a5c-377">Nó de cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="50a5c-377">Thumbnail card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest)
* [<span data-ttu-id="50a5c-378">Cartão-miniatura C #</span><span class="sxs-lookup"><span data-stu-id="50a5c-378">Thumbnail card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.thumbnailcard?view=botbuilder-dotnet-3.0)

## <a name="card-collections"></a><span data-ttu-id="50a5c-379">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="50a5c-379">Card collections</span></span>

<span data-ttu-id="50a5c-380">As coleções de cartões têm suporte no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="50a5c-380">Card collections are supported in Teams.</span></span>

<span data-ttu-id="50a5c-381">As coleções de cartões são fornecidas pela estrutura de `builder.AttachmentLayout.carousel` bot `builder.AttachmentLayout.list`: e.</span><span class="sxs-lookup"><span data-stu-id="50a5c-381">Card collections are provided by the Bot Framework: `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="50a5c-382">Essas coleções podem conter cartões adaptáveis, herói ou de miniaturas.</span><span class="sxs-lookup"><span data-stu-id="50a5c-382">These collections can contain Adaptive, Hero, or Thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="50a5c-383">Coleção carrossel</span><span class="sxs-lookup"><span data-stu-id="50a5c-383">Carousel collection</span></span>

<span data-ttu-id="50a5c-384">O [layout do carrossel](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0) mostra um carrossel de cartões, opcionalmente, com os botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="50a5c-384">The [carousel layout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="50a5c-385">Suporte para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="50a5c-385">Support for Carousel collections</span></span>

| <span data-ttu-id="50a5c-386">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-386">Bots in Teams</span></span> | <span data-ttu-id="50a5c-387">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-387">Messaging Extensions</span></span>  | <span data-ttu-id="50a5c-388">Conectores</span><span class="sxs-lookup"><span data-stu-id="50a5c-388">Connectors</span></span> | <span data-ttu-id="50a5c-389">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="50a5c-389">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="50a5c-390">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-390">✔</span></span> | <span data-ttu-id="50a5c-391">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-391">✖</span></span> | <span data-ttu-id="50a5c-392">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-392">✖</span></span> | <span data-ttu-id="50a5c-393">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-393">✔</span></span> |
|

> [!NOTE]
> <span data-ttu-id="50a5c-394">Um carrossel pode exibir no máximo 10 cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="50a5c-394">A carousel can display a maximum of 10 cards per message.</span></span>

### <a name="example-carousel-collection"></a><span data-ttu-id="50a5c-395">Coleção de carrossel de exemplo</span><span class="sxs-lookup"><span data-stu-id="50a5c-395">Example Carousel collection</span></span>

![Exemplo de um carrossel de cartões](~/assets/images/cards/carousel.png)

<span data-ttu-id="50a5c-397">As propriedades são as mesmas do herói ou do cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="50a5c-397">Properties are the same as for the hero or thumbnail card.</span></span>

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="50a5c-398">Sintaxe de coleções do carrossel</span><span class="sxs-lookup"><span data-stu-id="50a5c-398">Syntax for Carousel collections</span></span>

`builder.AttachmentLayout.carousel`

## <a name="list-collection"></a><span data-ttu-id="50a5c-399">Coleção List</span><span class="sxs-lookup"><span data-stu-id="50a5c-399">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="50a5c-400">Suporte para coleções de listas</span><span class="sxs-lookup"><span data-stu-id="50a5c-400">Support for List collections</span></span>

<span data-ttu-id="50a5c-401">O layout de lista mostra uma lista de cartões empilhados verticalmente, opcionalmente com os botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="50a5c-401">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="50a5c-402">Bots no Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-402">Bots in Teams</span></span> | <span data-ttu-id="50a5c-403">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="50a5c-403">Messaging Extensions</span></span>  | <span data-ttu-id="50a5c-404">Conectores</span><span class="sxs-lookup"><span data-stu-id="50a5c-404">Connectors</span></span> | <span data-ttu-id="50a5c-405">Estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="50a5c-405">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="50a5c-406">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-406">✔</span></span> | <span data-ttu-id="50a5c-407">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-407">✔</span></span> | <span data-ttu-id="50a5c-408">✖</span><span class="sxs-lookup"><span data-stu-id="50a5c-408">✖</span></span> | <span data-ttu-id="50a5c-409">✔</span><span class="sxs-lookup"><span data-stu-id="50a5c-409">✔</span></span> |
|

### <a name="example-list-collection"></a><span data-ttu-id="50a5c-410">Exemplo de coleção List</span><span class="sxs-lookup"><span data-stu-id="50a5c-410">Example List collection</span></span>

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

<span data-ttu-id="50a5c-412">As propriedades são as mesmas do herói ou do cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="50a5c-412">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="50a5c-413">Uma lista pode exibir no máximo 10 cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="50a5c-413">A list can display a maximum of 10 cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="50a5c-414">Algumas combinações de cartões de lista ainda não são suportadas no iOS e no Android.</span><span class="sxs-lookup"><span data-stu-id="50a5c-414">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="50a5c-415">Sintaxe para coleções de listas</span><span class="sxs-lookup"><span data-stu-id="50a5c-415">Syntax for List collections</span></span>

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="50a5c-416">Cartões não suportados no Teams</span><span class="sxs-lookup"><span data-stu-id="50a5c-416">Cards not supported in Teams</span></span>

<span data-ttu-id="50a5c-417">Os seguintes cartões são implementados pela estrutura do bot, mas não são suportados pelo Teams.</span><span class="sxs-lookup"><span data-stu-id="50a5c-417">The following cards are implemented by the Bot Framework, but are NOT supported by Teams.</span></span>

* <span data-ttu-id="50a5c-418">Cartões de animação</span><span class="sxs-lookup"><span data-stu-id="50a5c-418">Animation cards</span></span>
* <span data-ttu-id="50a5c-419">Placas de áudio</span><span class="sxs-lookup"><span data-stu-id="50a5c-419">Audio cards</span></span>
* <span data-ttu-id="50a5c-420">Placas de vídeo</span><span class="sxs-lookup"><span data-stu-id="50a5c-420">Video cards</span></span>
