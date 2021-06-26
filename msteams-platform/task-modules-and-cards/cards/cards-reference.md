---
title: Tipos de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Teams
localization_priority: Normal
keywords: referência de cartões bots
ms.topic: reference
ms.openlocfilehash: be38454daac519530d0fdf10b5170e128219f6fc
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140456"
---
# <a name="types-of-cards"></a><span data-ttu-id="1a4cc-104">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="1a4cc-104">Types of cards</span></span>

<span data-ttu-id="1a4cc-105">Adaptável, herói, lista, conector Office 365, recibo, entrada e coleções de cartões de miniatura são suportados em bots para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-105">Adaptive, hero, list, Office 365 Connector, receipt, signin, and thumbnail cards and card collections are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="1a4cc-106">Eles são baseados em cartões definidos pela Estrutura de Bot, mas Teams não dá suporte a todos os cartões da Estrutura de Bot e adicionou alguns de seus próprios.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span>

<span data-ttu-id="1a4cc-107">Antes de identificar os diferentes tipos de cartão, entenda como criar um cartão de herói, um cartão de miniatura ou um Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-107">Before you identify the different card types, understand how to create a a hero card, thumbnail card, or Adaptive Card.</span></span>

## <a name="create-a-hero-card-thumbnail-card-or-adaptive-card"></a><span data-ttu-id="1a4cc-108">Criar um cartão de herói, um cartão em miniatura ou um Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="1a4cc-108">Create a hero card, thumbnail card, or Adaptive Card</span></span>

<span data-ttu-id="1a4cc-109">**Para criar um cartão de herói, um cartão em miniatura ou um Cartão Adaptável do App Studio**</span><span class="sxs-lookup"><span data-stu-id="1a4cc-109">**To create a hero card, thumbnail card, or Adaptive Card from App Studio**</span></span>

1. <span data-ttu-id="1a4cc-110">Vá para **o App Studio** Teams.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-110">Go to **App Studio** from Teams.</span></span>
1. <span data-ttu-id="1a4cc-111">Selecione **Editor de cartão**.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-111">Select **Card editor**.</span></span>
1. <span data-ttu-id="1a4cc-112">Selecione **Criar um novo cartão**.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-112">Select **Create a new card**.</span></span>
1. <span data-ttu-id="1a4cc-113">Selecione **Criar** para um dos cartões de **Cartão de Herói,** **Cartão de** Miniatura ou **Cartão Adaptável.**</span><span class="sxs-lookup"><span data-stu-id="1a4cc-113">Select **Create** for one of the cards from **Hero Card**, **Thumbnail Card**, or **Adaptive Card**.</span></span> <span data-ttu-id="1a4cc-114">Os exemplos de detalhes de metadados, botões e json, csharp e código de nó são mostrados para esse cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-114">The metadata details, buttons, and json, csharp, and node code examples are shown for that card.</span></span>

    ![Detalhes do cartão de herói](~/assets/images/Cards/Herocarddetails.png)

1. <span data-ttu-id="1a4cc-116">Selecione Enviar este cartão para **mim.**</span><span class="sxs-lookup"><span data-stu-id="1a4cc-116">Select **Send me this card**.</span></span> <span data-ttu-id="1a4cc-117">O cartão é enviado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-117">The card is sent to you as a chat message.</span></span>

## <a name="card-examples"></a><span data-ttu-id="1a4cc-118">Exemplos de cartão</span><span class="sxs-lookup"><span data-stu-id="1a4cc-118">Card examples</span></span>

<span data-ttu-id="1a4cc-119">Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do Construtor de Bots v3.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-119">You can find additional information on how to use cards in the documentation for the Bot Builder SDK v3.</span></span> <span data-ttu-id="1a4cc-120">Exemplos de código também estão disponíveis no **repositório Microsoft/BotBuilder-Samples** no GitHub.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-120">Code samples are also available in the **Microsoft/BotBuilder-Samples** repository on GitHub.</span></span> <span data-ttu-id="1a4cc-121">A seguir estão alguns exemplos de cartão:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-121">Following are a few card examples:</span></span>

* <span data-ttu-id="1a4cc-122">.NET</span><span class="sxs-lookup"><span data-stu-id="1a4cc-122">.NET</span></span>
  * <span data-ttu-id="1a4cc-123">[Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-123">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="1a4cc-124">[Código de exemplo de cartões Construtor de bots v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-124">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span></span>

* <span data-ttu-id="1a4cc-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="1a4cc-125">Node.js</span></span>
  * <span data-ttu-id="1a4cc-126">[Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-126">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="1a4cc-127">[Código de exemplo de cartões Construtor de bots v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-127">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span></span>

## <a name="card-types"></a><span data-ttu-id="1a4cc-128">Tipos de cartão</span><span class="sxs-lookup"><span data-stu-id="1a4cc-128">Card types</span></span>

<span data-ttu-id="1a4cc-129">Você pode identificar e usar diferentes tipos de cartões com base nos requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-129">You can identify and use different types of cards based on your application requirements.</span></span> <span data-ttu-id="1a4cc-130">A tabela a seguir mostra os tipos de cartões disponíveis para você:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-130">The following table shows the types of cards available to you:</span></span>

| <span data-ttu-id="1a4cc-131">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="1a4cc-131">Card type</span></span> | <span data-ttu-id="1a4cc-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a4cc-132">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="1a4cc-133">Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="1a4cc-133">Adaptive Card</span></span>](#adaptive-card) | <span data-ttu-id="1a4cc-134">Esse cartão é altamente personalizável e pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-134">This card is highly customizable and can contain any combination of text, speech, images, buttons, and input fields.</span></span> |
| [<span data-ttu-id="1a4cc-135">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="1a4cc-135">Hero card</span></span>](#hero-card) | <span data-ttu-id="1a4cc-136">Esse cartão normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-136">This card typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="1a4cc-137">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="1a4cc-137">List card</span></span>](#list-card) | <span data-ttu-id="1a4cc-138">Este cartão contém uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-138">This card contains a scrolling list of items.</span></span> |
| [<span data-ttu-id="1a4cc-139">Office 365 Cartão conector</span><span class="sxs-lookup"><span data-stu-id="1a4cc-139">Office 365 Connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="1a4cc-140">Esse cartão tem um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-140">This card has a flexible layout with multiple sections, fields, images, and actions.</span></span> |
| [<span data-ttu-id="1a4cc-141">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="1a4cc-141">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="1a4cc-142">Este cartão fornece um recibo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-142">This card provides a receipt to the user.</span></span> |
| [<span data-ttu-id="1a4cc-143">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="1a4cc-143">Signin card</span></span>](#signin-card) | <span data-ttu-id="1a4cc-144">Esse cartão permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-144">This card enables a bot to request that a user signs in.</span></span> |
| [<span data-ttu-id="1a4cc-145">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="1a4cc-145">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="1a4cc-146">Esse cartão normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-146">This card typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="1a4cc-147">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="1a4cc-147">Card collections</span></span>](#card-collections) | <span data-ttu-id="1a4cc-148">Essa coleção de cartões é usada para retornar vários itens em uma única resposta.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-148">This card collection is used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="1a4cc-149">Propriedades comuns para todos os cartões</span><span class="sxs-lookup"><span data-stu-id="1a4cc-149">Common properties for all cards</span></span>

<span data-ttu-id="1a4cc-150">Você pode passar por algumas propriedades comuns que são aplicáveis a todos os cartões.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-150">You can go through some common properties that are applicable to all cards.</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="1a4cc-151">Imagens de cartão em linha</span><span class="sxs-lookup"><span data-stu-id="1a4cc-151">Inline card images</span></span>

<span data-ttu-id="1a4cc-152">O cartão pode conter uma imagem em linha incluindo um link para a imagem disponível publicamente.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-152">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="1a4cc-153">Para fins de desempenho, é altamente recomendável hospedar a imagem em uma Rede de Distribuição de Conteúdo pública (CDN).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-153">For performance purposes, it is highly recommended you host the image on a public Content Delivery Network (CDN).</span></span>

<span data-ttu-id="1a4cc-154">As imagens são dimensionados para cima ou para baixo em tamanho para manter a taxa de proporção para cobrir a área da imagem.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-154">Images are scaled up or down in size to maintain the aspect ratio for covering the image area.</span></span> <span data-ttu-id="1a4cc-155">Em seguida, as imagens são cortadas do centro para atingir a proporção apropriada para o cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-155">Images are then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="1a4cc-156">As imagens devem ter no máximo 1024×1024 e no formato PNG, JPEG ou GIF.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-156">Images must be at most 1024×1024 and in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="1a4cc-157">Gif animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-157">Animated GIF is not supported.</span></span>

<span data-ttu-id="1a4cc-158">A tabela a seguir fornece as propriedades das imagens de cartão em linha:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-158">The following table provides the properties of inline card images:</span></span>

| <span data-ttu-id="1a4cc-159">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1a4cc-159">Property</span></span> | <span data-ttu-id="1a4cc-160">Tipo</span><span class="sxs-lookup"><span data-stu-id="1a4cc-160">Type</span></span>  | <span data-ttu-id="1a4cc-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a4cc-161">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="1a4cc-162">url</span><span class="sxs-lookup"><span data-stu-id="1a4cc-162">url</span></span> | <span data-ttu-id="1a4cc-163">URL</span><span class="sxs-lookup"><span data-stu-id="1a4cc-163">URL</span></span> | <span data-ttu-id="1a4cc-164">URL HTTPS para a imagem.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-164">HTTPS URL to the image.</span></span> |
| <span data-ttu-id="1a4cc-165">alt</span><span class="sxs-lookup"><span data-stu-id="1a4cc-165">alt</span></span> | <span data-ttu-id="1a4cc-166">String</span><span class="sxs-lookup"><span data-stu-id="1a4cc-166">String</span></span> | <span data-ttu-id="1a4cc-167">Descrição acessível da imagem.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-167">Accessible description of the image.</span></span> |

> [!NOTE]
> <span data-ttu-id="1a4cc-168">Se um cartão incluir uma URL de imagem redirecionada antes da imagem final, o redirecionamento na URL da imagem não será suportado.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-168">If a card includes an image URL that is redirected before the final image, the redirect in image URL is not supported.</span></span> <span data-ttu-id="1a4cc-169">Isso ocorre para imagens compartilhadas na nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-169">This occurs for images shared on the public cloud.</span></span>

### <a name="buttons"></a><span data-ttu-id="1a4cc-170">Botões</span><span class="sxs-lookup"><span data-stu-id="1a4cc-170">Buttons</span></span>

<span data-ttu-id="1a4cc-171">Os botões são mostrados empilhados na parte inferior do cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-171">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="1a4cc-172">O texto do botão está sempre em uma única linha e é truncado se o texto exceder a largura do botão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-172">Button text is always on a single line and is truncated if the text exceeds the button width.</span></span> <span data-ttu-id="1a4cc-173">Quaisquer botões adicionais além do número máximo suportado pelo cartão não são mostrados.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-173">Any additional buttons beyond the maximum number supported by the card are not shown.</span></span>

<span data-ttu-id="1a4cc-174">Para obter mais informações, consulte [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-174">For more information, see [card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

### <a name="card-formatting"></a><span data-ttu-id="1a4cc-175">Formatação de cartão</span><span class="sxs-lookup"><span data-stu-id="1a4cc-175">Card formatting</span></span>

<span data-ttu-id="1a4cc-176">Para obter mais informações sobre formatação de texto em cartões, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-176">For more information on text formatting in cards, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

<span data-ttu-id="1a4cc-177">Depois de identificar as propriedades comuns para todos os cartões, agora você pode trabalhar com Cartões Adaptáveis, que ajudam a aumentar o envolvimento e a eficiência adicionando seu conteúdo a ação diretamente aos aplicativos que você usa.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-177">After identifying the common properties for all cards, you can now work with Adaptive Cards, which help you increase engagement and efficiency by adding your actionable content directly into the apps you use.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="1a4cc-178">Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="1a4cc-178">Adaptive Card</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/J12lKt717Ws]

<span data-ttu-id="1a4cc-179">Um Cartão Adaptável é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-179">An Adaptive Card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="1a4cc-180">Para obter mais informações, [consulte Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-180">For more information, see [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="1a4cc-181">Suporte para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="1a4cc-181">Support for Adaptive Cards</span></span>

<span data-ttu-id="1a4cc-182">A tabela a seguir fornece os recursos que suportam Cartões Adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-182">The following table provides the features that support Adaptive Cards:</span></span>

| <span data-ttu-id="1a4cc-183">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-183">Bots in Teams</span></span> | <span data-ttu-id="1a4cc-184">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-184">Messaging extensions</span></span>  | <span data-ttu-id="1a4cc-185">Conectores</span><span class="sxs-lookup"><span data-stu-id="1a4cc-185">Connectors</span></span> | <span data-ttu-id="1a4cc-186">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="1a4cc-186">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="1a4cc-187">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-187">✔</span></span> | <span data-ttu-id="1a4cc-188">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-188">✔</span></span> | <span data-ttu-id="1a4cc-189">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-189">✖</span></span> | <span data-ttu-id="1a4cc-190">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-190">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="1a4cc-191">Teams plataforma suporta v1.2 ou anterior de recursos de Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-191">Teams platform supports v1.2 or earlier of Adaptive Card features.</span></span>
> * <span data-ttu-id="1a4cc-192">O estilo de ação positivo ou destrutivo não é suportado em Cartões Adaptáveis na Teams plataforma.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-192">Positive or destructive action styling is not supported in Adaptive Cards on the Teams platform.</span></span>
> * <span data-ttu-id="1a4cc-193">No momento, os elementos de mídia não têm suporte no Cartão Adaptável na Teams plataforma.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-193">Media elements are currently not supported in Adaptive Card on the Teams platform.</span></span>

### <a name="example-of-adaptive-card"></a><span data-ttu-id="1a4cc-194">Exemplo de cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="1a4cc-194">Example of Adaptive Card</span></span>

![Exemplo de um cartão adaptável](~/assets/images/cards/adaptivecard.png)

<span data-ttu-id="1a4cc-196">O código a seguir mostra um exemplo de um Cartão Adaptável:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-196">The following code shows an example of an Adaptive Card:</span></span>

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

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="1a4cc-197">Informações adicionais sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="1a4cc-197">Additional information on Adaptive Cards</span></span>

<span data-ttu-id="1a4cc-198">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-198">Bot Framework reference:</span></span>

* [<span data-ttu-id="1a4cc-199">Nó de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="1a4cc-199">Adaptive Cards Node</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="1a4cc-200">Cartão Adaptável C #</span><span class="sxs-lookup"><span data-stu-id="1a4cc-200">Adaptive Card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

<span data-ttu-id="1a4cc-201">Agora você pode trabalhar com um cartão de herói, que é um cartão multiuso usado para realçar visualmente uma seleção de usuário potencial.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-201">You can now work with a hero card, which is a multipurpose card used to visually highlight a potential user selection.</span></span>

## <a name="hero-card"></a><span data-ttu-id="1a4cc-202">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="1a4cc-202">Hero card</span></span>

<span data-ttu-id="1a4cc-203">Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-203">A card that typically contains a single large image, one or more buttons, and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="1a4cc-204">Suporte para cartões de herói</span><span class="sxs-lookup"><span data-stu-id="1a4cc-204">Support for hero cards</span></span>

<span data-ttu-id="1a4cc-205">A tabela a seguir fornece os recursos que suportam cartões de herói:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-205">The following table provides the features that support hero cards:</span></span>

| <span data-ttu-id="1a4cc-206">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-206">Bots in Teams</span></span> | <span data-ttu-id="1a4cc-207">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-207">Messaging extensions</span></span>  | <span data-ttu-id="1a4cc-208">Conectores</span><span class="sxs-lookup"><span data-stu-id="1a4cc-208">Connectors</span></span> | <span data-ttu-id="1a4cc-209">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="1a4cc-209">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="1a4cc-210">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-210">✔</span></span> | <span data-ttu-id="1a4cc-211">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-211">✔</span></span> | <span data-ttu-id="1a4cc-212">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-212">✖</span></span> | <span data-ttu-id="1a4cc-213">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-213">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="1a4cc-214">Propriedades de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="1a4cc-214">Properties of a hero card</span></span>

<span data-ttu-id="1a4cc-215">A tabela a seguir fornece as propriedades de um cartão de herói:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-215">The following table provides the properties of a hero card:</span></span>

| <span data-ttu-id="1a4cc-216">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1a4cc-216">Property</span></span> | <span data-ttu-id="1a4cc-217">Tipo</span><span class="sxs-lookup"><span data-stu-id="1a4cc-217">Type</span></span>  | <span data-ttu-id="1a4cc-218">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a4cc-218">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="1a4cc-219">title</span><span class="sxs-lookup"><span data-stu-id="1a4cc-219">title</span></span> | <span data-ttu-id="1a4cc-220">Rich text </span><span class="sxs-lookup"><span data-stu-id="1a4cc-220">Rich text</span></span> | <span data-ttu-id="1a4cc-221">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-221">Title of the card.</span></span> <span data-ttu-id="1a4cc-222">Máximo de duas linhas.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-222">Maximum two lines.</span></span> |
| <span data-ttu-id="1a4cc-223">subtitle</span><span class="sxs-lookup"><span data-stu-id="1a4cc-223">subtitle</span></span> | <span data-ttu-id="1a4cc-224">Rich text </span><span class="sxs-lookup"><span data-stu-id="1a4cc-224">Rich text</span></span> | <span data-ttu-id="1a4cc-225">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-225">Subtitle of the card.</span></span> <span data-ttu-id="1a4cc-226">Máximo de duas linhas.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-226">Maximum two lines.</span></span>|
| <span data-ttu-id="1a4cc-227">texto</span><span class="sxs-lookup"><span data-stu-id="1a4cc-227">text</span></span> | <span data-ttu-id="1a4cc-228">Rich text </span><span class="sxs-lookup"><span data-stu-id="1a4cc-228">Rich text</span></span> | <span data-ttu-id="1a4cc-229">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-229">Text appears under the subtitle.</span></span> <span data-ttu-id="1a4cc-230">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-230">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="1a4cc-231">images</span><span class="sxs-lookup"><span data-stu-id="1a4cc-231">images</span></span> | <span data-ttu-id="1a4cc-232">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-232">Array of images</span></span> | <span data-ttu-id="1a4cc-233">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-233">Image displayed at the top of the card.</span></span> <span data-ttu-id="1a4cc-234">Taxa de proporção 16:9.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-234">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="1a4cc-235">botões</span><span class="sxs-lookup"><span data-stu-id="1a4cc-235">buttons</span></span> | <span data-ttu-id="1a4cc-236">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="1a4cc-236">Array of action objects</span></span> | <span data-ttu-id="1a4cc-237">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-237">Set of actions applicable to the current card.</span></span> <span data-ttu-id="1a4cc-238">Máximo de seis.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-238">Maximum six.</span></span> |
| <span data-ttu-id="1a4cc-239">tap</span><span class="sxs-lookup"><span data-stu-id="1a4cc-239">tap</span></span> | <span data-ttu-id="1a4cc-240">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="1a4cc-240">Action object</span></span> | <span data-ttu-id="1a4cc-241">Ativado quando o usuário toca no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-241">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="1a4cc-242">Exemplo de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="1a4cc-242">Example of a hero card</span></span>

![Exemplo de um cartão de herói](~/assets/images/cards/hero.png)

<span data-ttu-id="1a4cc-244">O código a seguir mostra um exemplo de um cartão de herói:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-244">The following code shows an example of a hero card:</span></span>

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

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="1a4cc-245">Informações adicionais sobre cartões de herói</span><span class="sxs-lookup"><span data-stu-id="1a4cc-245">Additional information on hero cards</span></span>

<span data-ttu-id="1a4cc-246">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-246">Bot Framework reference:</span></span>

* [<span data-ttu-id="1a4cc-247">Cartão de herói Node.js</span><span class="sxs-lookup"><span data-stu-id="1a4cc-247">Hero card Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="1a4cc-248">Cartão de herói C #</span><span class="sxs-lookup"><span data-stu-id="1a4cc-248">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="1a4cc-249">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="1a4cc-249">List card</span></span>

<span data-ttu-id="1a4cc-250">O cartão de lista foi adicionado por Teams para fornecer funções além do que a coleção de listas pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-250">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="1a4cc-251">O cartão de listagem fornece uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-251">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="1a4cc-252">Suporte para cartões de lista</span><span class="sxs-lookup"><span data-stu-id="1a4cc-252">Support for list cards</span></span>

<span data-ttu-id="1a4cc-253">A tabela a seguir fornece os recursos que suportam cartões de lista:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-253">The following table provides the features that support list cards:</span></span>

| <span data-ttu-id="1a4cc-254">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-254">Bots in Teams</span></span> | <span data-ttu-id="1a4cc-255">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-255">Messaging extensions</span></span>  | <span data-ttu-id="1a4cc-256">Conectores</span><span class="sxs-lookup"><span data-stu-id="1a4cc-256">Connectors</span></span> | <span data-ttu-id="1a4cc-257">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="1a4cc-257">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="1a4cc-258">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-258">✔</span></span> | <span data-ttu-id="1a4cc-259">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-259">✖</span></span> | <span data-ttu-id="1a4cc-260">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-260">✖</span></span> |<span data-ttu-id="1a4cc-261">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-261">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="1a4cc-262">Propriedades de um cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="1a4cc-262">Properties of a list card</span></span>

<span data-ttu-id="1a4cc-263">A tabela a seguir fornece as propriedades de um cartão de listagem:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-263">The following table provides the properties of a list card:</span></span>

| <span data-ttu-id="1a4cc-264">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1a4cc-264">Property</span></span> | <span data-ttu-id="1a4cc-265">Tipo</span><span class="sxs-lookup"><span data-stu-id="1a4cc-265">Type</span></span>  | <span data-ttu-id="1a4cc-266">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a4cc-266">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="1a4cc-267">title</span><span class="sxs-lookup"><span data-stu-id="1a4cc-267">title</span></span> | <span data-ttu-id="1a4cc-268">Rich text </span><span class="sxs-lookup"><span data-stu-id="1a4cc-268">Rich text</span></span> | <span data-ttu-id="1a4cc-269">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-269">Title of the card.</span></span> <span data-ttu-id="1a4cc-270">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-270">Maximum 2 lines.</span></span>|
| <span data-ttu-id="1a4cc-271">itens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-271">items</span></span> | <span data-ttu-id="1a4cc-272">Matriz de itens de lista</span><span class="sxs-lookup"><span data-stu-id="1a4cc-272">Array of list items</span></span> | <span data-ttu-id="1a4cc-273">Conjunto de itens aplicáveis ao cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-273">Set of items applicable to the card.</span></span>|
| <span data-ttu-id="1a4cc-274">botões</span><span class="sxs-lookup"><span data-stu-id="1a4cc-274">buttons</span></span> | <span data-ttu-id="1a4cc-275">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="1a4cc-275">Array of action objects</span></span> | <span data-ttu-id="1a4cc-276">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-276">Set of actions applicable to the current card.</span></span> <span data-ttu-id="1a4cc-277">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-277">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="1a4cc-278">Exemplo de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="1a4cc-278">Example of a list card</span></span>

<span data-ttu-id="1a4cc-279">O código a seguir mostra um exemplo de um cartão de lista:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-279">The following code shows an example of a list card:</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="1a4cc-280">Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="1a4cc-280">Office 365 connector card</span></span>

<span data-ttu-id="1a4cc-281">Você pode trabalhar com um cartão Office 365 Conector que fornece um layout flexível e é uma ótima maneira de obter informações úteis.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-281">You can work with an Office 365 Connector card that provides a flexible layout and is a great way to get useful information.</span></span> <span data-ttu-id="1a4cc-282">O Office 365 conector de usuário é compatível com Teams, não na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-282">The Office 365 connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="1a4cc-283">Este cartão fornece um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-283">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="1a4cc-284">Esse cartão contém um cartão conector para que possa ser usado por bots.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-284">This card contains a connector card so that it can be used by bots.</span></span> <span data-ttu-id="1a4cc-285">Para obter diferenças entre cartões de conector e o cartão Office 365 conector, consulte Informações adicionais [sobre o cartão Office 365 Connector.](#additional-information-on-the-office-365-connector-card)</span><span class="sxs-lookup"><span data-stu-id="1a4cc-285">For differences between connector cards and the Office 365 Connector card, see [Additional information on the Office 365 Connector card](#additional-information-on-the-office-365-connector-card).</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="1a4cc-286">Suporte para cartões Office 365 Conector</span><span class="sxs-lookup"><span data-stu-id="1a4cc-286">Support for Office 365 Connector cards</span></span>

<span data-ttu-id="1a4cc-287">A tabela a seguir fornece os recursos que suportam Office 365 conectores:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-287">The following table provides the features that support Office 365 Connector cards:</span></span>

| <span data-ttu-id="1a4cc-288">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-288">Bots in Teams</span></span> | <span data-ttu-id="1a4cc-289">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-289">Messaging extensions</span></span>  | <span data-ttu-id="1a4cc-290">Conectores</span><span class="sxs-lookup"><span data-stu-id="1a4cc-290">Connectors</span></span> | <span data-ttu-id="1a4cc-291">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="1a4cc-291">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="1a4cc-292">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-292">✔</span></span> | <span data-ttu-id="1a4cc-293">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-293">✔</span></span> | <span data-ttu-id="1a4cc-294">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-294">✔</span></span> | <span data-ttu-id="1a4cc-295">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-295">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="1a4cc-296">Propriedades do cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="1a4cc-296">Properties of the Office 365 Connector card</span></span>

<span data-ttu-id="1a4cc-297">A tabela a seguir fornece as propriedades do cartão Office 365 conector:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-297">The following table provides the properties of the Office 365 connector card:</span></span>

| <span data-ttu-id="1a4cc-298">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1a4cc-298">Property</span></span> | <span data-ttu-id="1a4cc-299">Tipo</span><span class="sxs-lookup"><span data-stu-id="1a4cc-299">Type</span></span>  | <span data-ttu-id="1a4cc-300">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a4cc-300">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="1a4cc-301">title</span><span class="sxs-lookup"><span data-stu-id="1a4cc-301">title</span></span> | <span data-ttu-id="1a4cc-302">Rich text </span><span class="sxs-lookup"><span data-stu-id="1a4cc-302">Rich text</span></span> | <span data-ttu-id="1a4cc-303">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-303">Title of the card.</span></span> <span data-ttu-id="1a4cc-304">Máximo de duas linhas.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-304">Maximum two lines.</span></span> |
| <span data-ttu-id="1a4cc-305">summary</span><span class="sxs-lookup"><span data-stu-id="1a4cc-305">summary</span></span> | <span data-ttu-id="1a4cc-306">Rich text </span><span class="sxs-lookup"><span data-stu-id="1a4cc-306">Rich text</span></span> | <span data-ttu-id="1a4cc-307">Resumo do cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-307">Summary of the card.</span></span> <span data-ttu-id="1a4cc-308">Máximo de duas linhas.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-308">Maximum two lines.</span></span> |
| <span data-ttu-id="1a4cc-309">texto</span><span class="sxs-lookup"><span data-stu-id="1a4cc-309">text</span></span> | <span data-ttu-id="1a4cc-310">Rich text </span><span class="sxs-lookup"><span data-stu-id="1a4cc-310">Rich text</span></span> | <span data-ttu-id="1a4cc-311">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-311">Text appears under the subtitle.</span></span> <span data-ttu-id="1a4cc-312">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-312">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="1a4cc-313">themeColor</span><span class="sxs-lookup"><span data-stu-id="1a4cc-313">themeColor</span></span> | <span data-ttu-id="1a4cc-314">Cadeia de caracteres HEX</span><span class="sxs-lookup"><span data-stu-id="1a4cc-314">HEX string</span></span> | <span data-ttu-id="1a4cc-315">Cor que substitui o `accentColor` fornecido do manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-315">Color that overrides the `accentColor` provided from the application manifest.</span></span> |

### <a name="additional-information-on-the-office-365-connector-card"></a><span data-ttu-id="1a4cc-316">Informações adicionais sobre o cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="1a4cc-316">Additional information on the Office 365 Connector card</span></span>

<span data-ttu-id="1a4cc-317">Office 365 Os cartões conectores funcionam corretamente Microsoft Teams, incluindo [ `ActionCard` ações](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-317">Office 365 Connector cards function properly in Microsoft Teams, including [`ActionCard` actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="1a4cc-318">A diferença importante entre o uso de cartões de conector de um conector e o uso de cartões de conector no bot é o tratamento de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-318">The important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span> <span data-ttu-id="1a4cc-319">A tabela a seguir lista a diferença:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-319">The following table lists the difference:</span></span>

| <span data-ttu-id="1a4cc-320">Conector</span><span class="sxs-lookup"><span data-stu-id="1a4cc-320">Connector</span></span> | <span data-ttu-id="1a4cc-321">Bot</span><span class="sxs-lookup"><span data-stu-id="1a4cc-321">Bot</span></span> |
| --- | --- |
| <span data-ttu-id="1a4cc-322">O ponto de extremidade recebe a carga de cartão por meio de HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-322">The endpoint receives the card payload through HTTP POST.</span></span> | <span data-ttu-id="1a4cc-323">A ação dispara uma atividade que envia apenas a ID de ação `HttpPOST` e o corpo para o `invoke` bot.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-323">The `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>|

<span data-ttu-id="1a4cc-324">Cada cartão de conector pode exibir no máximo dez seções, e cada seção pode conter no máximo cinco imagens e cinco ações.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-324">Each connector card can display a maximum of ten sections, and each section can contain a maximum of five images and five actions.</span></span>

> [!NOTE]
> <span data-ttu-id="1a4cc-325">Quaisquer seções, imagens ou ações adicionais em uma mensagem não são exibidas.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-325">Any additional sections, images, or actions in a message do not appear.</span></span>

<span data-ttu-id="1a4cc-326">Todos os campos de texto suportam Markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-326">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="1a4cc-327">Você pode controlar quais seções usam Markdown ou HTML definindo `markdown` a propriedade em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-327">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="1a4cc-328">Por padrão, `markdown` é definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="1a4cc-328">By default, `markdown` is set to `true`.</span></span> <span data-ttu-id="1a4cc-329">Se você quiser usar HTML em vez disso, de definir `markdown` como `false` .</span><span class="sxs-lookup"><span data-stu-id="1a4cc-329">If you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="1a4cc-330">Se você especificar a `themeColor` propriedade, ela substituirá `accentColor` a propriedade no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-330">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="1a4cc-331">Para especificar o estilo de renderização `activityImage` para , você pode definir como mostrado na tabela a `activityImageType` seguir:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-331">To specify the rendering style for `activityImage`, you can set `activityImageType` as shown in the following table:</span></span>

| <span data-ttu-id="1a4cc-332">Valor</span><span class="sxs-lookup"><span data-stu-id="1a4cc-332">Value</span></span> | <span data-ttu-id="1a4cc-333">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a4cc-333">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="1a4cc-334">Padrão, `activityImage` é cortada como um círculo.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-334">Default, `activityImage` is cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="1a4cc-335">`activityImage` é exibido como um retângulo e mantém sua taxa de proporção.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-335">`activityImage` is displayed as a rectangle and retains its aspect ratio.</span></span> |

<span data-ttu-id="1a4cc-336">Para obter todos os outros detalhes sobre as propriedades do cartão do conector, consulte referência de cartão de mensagem a [ação.](/outlook/actionable-messages/card-reference)</span><span class="sxs-lookup"><span data-stu-id="1a4cc-336">For all other details about connector card properties, see [actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="1a4cc-337">As únicas propriedades de cartão de conector que Teams atualmente não suportam são as seguinte:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-337">The only connector card properties that Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="1a4cc-338">`startGroup`sempre tratado como `true` em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-338">`startGroup` always treated as `true` in Teams</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="1a4cc-339">Exemplo de um cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="1a4cc-339">Example of an Office 365 Connector card</span></span>

<span data-ttu-id="1a4cc-340">O código a seguir mostra um exemplo de um cartão Office 365 Connector:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-340">The following code shows an example of an Office 365 Connector card:</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="1a4cc-341">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="1a4cc-341">Receipt card</span></span>

<span data-ttu-id="1a4cc-342">Teams dá suporte ao cartão de recebimento.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-342">Teams supports receipt card.</span></span> <span data-ttu-id="1a4cc-343">É um cartão que permite que um bot forneça um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-343">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="1a4cc-344">Normalmente, ele contém a lista de itens a ser incluídos no recibo, como informações fiscais e totais.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-344">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="1a4cc-345">Suporte para cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="1a4cc-345">Support for receipt cards</span></span>

<span data-ttu-id="1a4cc-346">A tabela a seguir fornece os recursos que suportam cartões de recebimento:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-346">The following table provides the features that support receipt cards:</span></span>

| <span data-ttu-id="1a4cc-347">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-347">Bots in Teams</span></span> | <span data-ttu-id="1a4cc-348">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-348">Messaging extensions</span></span>  | <span data-ttu-id="1a4cc-349">Conectores</span><span class="sxs-lookup"><span data-stu-id="1a4cc-349">Connectors</span></span> | <span data-ttu-id="1a4cc-350">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="1a4cc-350">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="1a4cc-351">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-351">✔</span></span> | <span data-ttu-id="1a4cc-352">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-352">✔</span></span> | <span data-ttu-id="1a4cc-353">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-353">✖</span></span> | <span data-ttu-id="1a4cc-354">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-354">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="1a4cc-355">Exemplo de um cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="1a4cc-355">Example of a receipt card</span></span>

![Exemplo de um cartão de confirmação](~/assets/images/cards/receipt.png)

<span data-ttu-id="1a4cc-357">O código a seguir mostra um exemplo de um cartão de recebimento:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-357">The following code shows an example of a receipt card:</span></span>

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

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="1a4cc-358">Informações adicionais sobre cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="1a4cc-358">Additional information on receipt cards</span></span>

<span data-ttu-id="1a4cc-359">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-359">Bot Framework reference:</span></span>

* [<span data-ttu-id="1a4cc-360">Cartão de Node.js</span><span class="sxs-lookup"><span data-stu-id="1a4cc-360">Receipt card Node.js</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="1a4cc-361">Cartão de recebimento C #</span><span class="sxs-lookup"><span data-stu-id="1a4cc-361">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="1a4cc-362">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="1a4cc-362">Signin card</span></span>

<span data-ttu-id="1a4cc-363">O cartão de Teams é semelhante ao cartão de assinatura na Estrutura de Bot, exceto que o cartão de signin no Teams suporta apenas duas ações `signin` e `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="1a4cc-363">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions `signin` and `openUrl`.</span></span>

<span data-ttu-id="1a4cc-364">A ação de signin pode ser usada de qualquer cartão Teams, não apenas o cartão de assinatura.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-364">The signin action can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="1a4cc-365">Para obter mais informações, [consulte Teams fluxo de autenticação para bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-365">For more information, see [Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="1a4cc-366">Suporte para cartões de assinatura</span><span class="sxs-lookup"><span data-stu-id="1a4cc-366">Support for signin cards</span></span>

<span data-ttu-id="1a4cc-367">A tabela a seguir fornece os recursos que suportam cartões de assinatura:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-367">The following table provides the features that support signin cards:</span></span>

| <span data-ttu-id="1a4cc-368">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-368">Bots in Teams</span></span> | <span data-ttu-id="1a4cc-369">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-369">Messaging extensions</span></span>  | <span data-ttu-id="1a4cc-370">Conectores</span><span class="sxs-lookup"><span data-stu-id="1a4cc-370">Connectors</span></span> | <span data-ttu-id="1a4cc-371">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="1a4cc-371">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="1a4cc-372">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-372">✔</span></span> | <span data-ttu-id="1a4cc-373">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-373">✖</span></span> | <span data-ttu-id="1a4cc-374">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-374">✖</span></span> | <span data-ttu-id="1a4cc-375">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-375">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="1a4cc-376">Informações adicionais sobre cartões de assinatura</span><span class="sxs-lookup"><span data-stu-id="1a4cc-376">Additional information on signin cards</span></span>

<span data-ttu-id="1a4cc-377">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-377">Bot Framework reference:</span></span>

* [<span data-ttu-id="1a4cc-378">Cartão de Node.js</span><span class="sxs-lookup"><span data-stu-id="1a4cc-378">Signin card Node.js</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="1a4cc-379">Signin card C #</span><span class="sxs-lookup"><span data-stu-id="1a4cc-379">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="1a4cc-380">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="1a4cc-380">Thumbnail card</span></span>

<span data-ttu-id="1a4cc-381">Você pode trabalhar com um cartão de miniatura que é usado para enviar uma mensagem a ação simples.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-381">You can work with a thumbnail card that is used for sending a simple actionable message.</span></span> <span data-ttu-id="1a4cc-382">Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-382">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="1a4cc-383">Suporte para cartões de miniatura</span><span class="sxs-lookup"><span data-stu-id="1a4cc-383">Support for thumbnail cards</span></span>

<span data-ttu-id="1a4cc-384">A tabela a seguir fornece os recursos que suportam cartões de miniatura:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-384">The following table provides the features that support thumbnail cards:</span></span>

| <span data-ttu-id="1a4cc-385">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-385">Bots in Teams</span></span> | <span data-ttu-id="1a4cc-386">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-386">Messaging extensions</span></span>  | <span data-ttu-id="1a4cc-387">Conectores</span><span class="sxs-lookup"><span data-stu-id="1a4cc-387">Connectors</span></span> | <span data-ttu-id="1a4cc-388">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="1a4cc-388">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="1a4cc-389">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-389">✔</span></span> | <span data-ttu-id="1a4cc-390">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-390">✔</span></span> | <span data-ttu-id="1a4cc-391">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-391">✖</span></span> | <span data-ttu-id="1a4cc-392">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-392">✔</span></span> |

![Exemplo de um cartão de miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="1a4cc-394">Propriedades de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="1a4cc-394">Properties of a thumbnail card</span></span>

<span data-ttu-id="1a4cc-395">A tabela a seguir fornece as propriedades de um cartão de miniatura:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-395">The following table provides the properties of a thumbnail card:</span></span>

| <span data-ttu-id="1a4cc-396">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1a4cc-396">Property</span></span> | <span data-ttu-id="1a4cc-397">Tipo</span><span class="sxs-lookup"><span data-stu-id="1a4cc-397">Type</span></span>  | <span data-ttu-id="1a4cc-398">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a4cc-398">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="1a4cc-399">title</span><span class="sxs-lookup"><span data-stu-id="1a4cc-399">title</span></span> | <span data-ttu-id="1a4cc-400">Rich text </span><span class="sxs-lookup"><span data-stu-id="1a4cc-400">Rich text</span></span> | <span data-ttu-id="1a4cc-401">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-401">Title of the card.</span></span> <span data-ttu-id="1a4cc-402">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-402">Maximum 2 lines.</span></span>|
| <span data-ttu-id="1a4cc-403">subtitle</span><span class="sxs-lookup"><span data-stu-id="1a4cc-403">subtitle</span></span> | <span data-ttu-id="1a4cc-404">Rich text </span><span class="sxs-lookup"><span data-stu-id="1a4cc-404">Rich text</span></span> | <span data-ttu-id="1a4cc-405">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-405">Subtitle of the card.</span></span> <span data-ttu-id="1a4cc-406">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-406">Maximum 2 lines.</span></span>|
| <span data-ttu-id="1a4cc-407">texto</span><span class="sxs-lookup"><span data-stu-id="1a4cc-407">text</span></span> | <span data-ttu-id="1a4cc-408">Rich text </span><span class="sxs-lookup"><span data-stu-id="1a4cc-408">Rich text</span></span> | <span data-ttu-id="1a4cc-409">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-409">Text appears under the subtitle.</span></span> <span data-ttu-id="1a4cc-410">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="1a4cc-410">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="1a4cc-411">images</span><span class="sxs-lookup"><span data-stu-id="1a4cc-411">images</span></span> | <span data-ttu-id="1a4cc-412">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-412">Array of images</span></span> | <span data-ttu-id="1a4cc-413">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-413">Image displayed at the top of the card.</span></span> <span data-ttu-id="1a4cc-414">Taxa de proporção 1:1 quadrado.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-414">Aspect ratio 1:1 square.</span></span> |
| <span data-ttu-id="1a4cc-415">botões</span><span class="sxs-lookup"><span data-stu-id="1a4cc-415">buttons</span></span> | <span data-ttu-id="1a4cc-416">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="1a4cc-416">Array of action objects</span></span> | <span data-ttu-id="1a4cc-417">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-417">Set of actions applicable to the current card.</span></span> <span data-ttu-id="1a4cc-418">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-418">Maximum 6.</span></span> |
| <span data-ttu-id="1a4cc-419">tap</span><span class="sxs-lookup"><span data-stu-id="1a4cc-419">tap</span></span> | <span data-ttu-id="1a4cc-420">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="1a4cc-420">Action object</span></span> | <span data-ttu-id="1a4cc-421">Ativado quando o usuário toca no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-421">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="1a4cc-422">Exemplo de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="1a4cc-422">Example of a thumbnail card</span></span>

<span data-ttu-id="1a4cc-423">O código a seguir mostra um exemplo de um cartão de miniatura:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-423">The following code shows an example of a thumbnail card:</span></span>

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

### <a name="additional-information"></a><span data-ttu-id="1a4cc-424">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="1a4cc-424">Additional information</span></span>

<span data-ttu-id="1a4cc-425">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-425">Bot Framework reference:</span></span>

* [<span data-ttu-id="1a4cc-426">Cartão de miniatura Node.js</span><span class="sxs-lookup"><span data-stu-id="1a4cc-426">Thumbnail card Node.js</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="1a4cc-427">Cartão de miniatura C #</span><span class="sxs-lookup"><span data-stu-id="1a4cc-427">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="1a4cc-428">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="1a4cc-428">Card collections</span></span>

<span data-ttu-id="1a4cc-429">Você pode trabalhar com coleções de cartões que incluem carrossel e coleções de lista.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-429">You can work with card collections that include carousel and list collections.</span></span> <span data-ttu-id="1a4cc-430">Teams dá suporte a coleções de cartões.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-430">Teams supports card collections.</span></span> <span data-ttu-id="1a4cc-431">As coleções de cartões `builder.AttachmentLayout.carousel` incluem `builder.AttachmentLayout.list` e .</span><span class="sxs-lookup"><span data-stu-id="1a4cc-431">Card collections include `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="1a4cc-432">Essas coleções contêm cartões adaptáveis, herois ou miniaturas.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-432">These collections contain Adaptive, hero, or thumbnail cards.</span></span>

### <a name="carousel-collection"></a><span data-ttu-id="1a4cc-433">Coleção Carousel</span><span class="sxs-lookup"><span data-stu-id="1a4cc-433">Carousel collection</span></span>

<span data-ttu-id="1a4cc-434">O [layout do carrossel](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-434">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

#### <a name="support-for-carousel-collections"></a><span data-ttu-id="1a4cc-435">Suporte para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="1a4cc-435">Support for carousel collections</span></span>

<span data-ttu-id="1a4cc-436">A tabela a seguir fornece os recursos que suportam coleções de carrossel:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-436">The following table provides the features that support carousel collections:</span></span>

| <span data-ttu-id="1a4cc-437">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-437">Bots in Teams</span></span> | <span data-ttu-id="1a4cc-438">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-438">Messaging extensions</span></span>  | <span data-ttu-id="1a4cc-439">Conectores</span><span class="sxs-lookup"><span data-stu-id="1a4cc-439">Connectors</span></span> | <span data-ttu-id="1a4cc-440">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="1a4cc-440">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="1a4cc-441">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-441">✔</span></span> | <span data-ttu-id="1a4cc-442">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-442">✖</span></span> | <span data-ttu-id="1a4cc-443">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-443">✖</span></span> | <span data-ttu-id="1a4cc-444">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-444">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="1a4cc-445">Um carrossel pode exibir no máximo dez cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-445">A carousel can display a maximum of ten cards per message.</span></span>

#### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="1a4cc-446">Propriedades de um cartão de carrossel</span><span class="sxs-lookup"><span data-stu-id="1a4cc-446">Properties of a carousel card</span></span>

<span data-ttu-id="1a4cc-447">As propriedades de um cartão de carrossel são as mesmas que as de herói e miniatura.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-447">Properties of a carousel card are same as the hero and thumbnail cards.</span></span>

#### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="1a4cc-448">Exemplo de uma coleção de carrossel</span><span class="sxs-lookup"><span data-stu-id="1a4cc-448">Example of a carousel collection</span></span>

![Exemplo de um carrossel de cartões](~/assets/images/cards/carousel.png)

<span data-ttu-id="1a4cc-450">O código a seguir mostra um exemplo de uma coleção de carrossel:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-450">The following code shows an example of a carousel collection:</span></span>

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

#### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="1a4cc-451">Sintaxe para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="1a4cc-451">Syntax for carousel collections</span></span>

<span data-ttu-id="1a4cc-452">`builder.AttachmentLayoutTypes.Carousel` é a sintaxe para coleções de carrossel.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-452">`builder.AttachmentLayoutTypes.Carousel` is the syntax for carousel collections.</span></span>

### <a name="list-collection"></a><span data-ttu-id="1a4cc-453">Coleção List</span><span class="sxs-lookup"><span data-stu-id="1a4cc-453">List collection</span></span>

<span data-ttu-id="1a4cc-454">O layout da lista mostra uma lista verticalmente empilhada de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-454">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

#### <a name="support-for-list-collections"></a><span data-ttu-id="1a4cc-455">Suporte para coleções de lista</span><span class="sxs-lookup"><span data-stu-id="1a4cc-455">Support for list collections</span></span>

<span data-ttu-id="1a4cc-456">A tabela a seguir fornece os recursos que suportam coleções de lista:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-456">The following table provides the features that support list collections:</span></span>

| <span data-ttu-id="1a4cc-457">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-457">Bots in Teams</span></span> | <span data-ttu-id="1a4cc-458">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1a4cc-458">Messaging extensions</span></span>  | <span data-ttu-id="1a4cc-459">Conectores</span><span class="sxs-lookup"><span data-stu-id="1a4cc-459">Connectors</span></span> | <span data-ttu-id="1a4cc-460">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="1a4cc-460">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="1a4cc-461">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-461">✔</span></span> | <span data-ttu-id="1a4cc-462">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-462">✔</span></span> | <span data-ttu-id="1a4cc-463">✖</span><span class="sxs-lookup"><span data-stu-id="1a4cc-463">✖</span></span> | <span data-ttu-id="1a4cc-464">✔</span><span class="sxs-lookup"><span data-stu-id="1a4cc-464">✔</span></span> |

#### <a name="example-of-a-list-collection"></a><span data-ttu-id="1a4cc-465">Exemplo de uma coleção de listas</span><span class="sxs-lookup"><span data-stu-id="1a4cc-465">Example of a list collection</span></span>

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

<span data-ttu-id="1a4cc-467">As propriedades das coleções de lista são as mesmas que os cartões de miniatura ou herói.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-467">Properties of list collections are same as the hero or thumbnail cards.</span></span>

<span data-ttu-id="1a4cc-468">Uma lista pode exibir no máximo dez cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-468">A list can display a maximum of ten cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="1a4cc-469">Algumas combinações de cartões de lista ainda não são suportadas no iOS e no Android.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-469">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

#### <a name="syntax-for-list-collections"></a><span data-ttu-id="1a4cc-470">Sintaxe para coleções de lista</span><span class="sxs-lookup"><span data-stu-id="1a4cc-470">Syntax for list collections</span></span>

<span data-ttu-id="1a4cc-471">`builder.AttachmentLayout.list` é a sintaxe para coleções de lista.</span><span class="sxs-lookup"><span data-stu-id="1a4cc-471">`builder.AttachmentLayout.list` is the syntax for list collections.</span></span>

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="1a4cc-472">Cartões não suportados em Teams</span><span class="sxs-lookup"><span data-stu-id="1a4cc-472">Cards not supported in Teams</span></span>

<span data-ttu-id="1a4cc-473">Os cartões a seguir são implementados pela Estrutura de Bot, mas não são suportados por Teams:</span><span class="sxs-lookup"><span data-stu-id="1a4cc-473">The following cards are implemented by the Bot Framework, but are not supported by Teams:</span></span>

* <span data-ttu-id="1a4cc-474">Cartões de animação</span><span class="sxs-lookup"><span data-stu-id="1a4cc-474">Animation cards</span></span>
* <span data-ttu-id="1a4cc-475">Cartões de áudio</span><span class="sxs-lookup"><span data-stu-id="1a4cc-475">Audio cards</span></span>
* <span data-ttu-id="1a4cc-476">Cartões de vídeo</span><span class="sxs-lookup"><span data-stu-id="1a4cc-476">Video cards</span></span>

## <a name="see-also"></a><span data-ttu-id="1a4cc-477">Também consulte</span><span class="sxs-lookup"><span data-stu-id="1a4cc-477">See also</span></span>

* [<span data-ttu-id="1a4cc-478">Módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="1a4cc-478">Task modules</span></span>](~/task-modules-and-cards/what-are-task-modules.md)
* [<span data-ttu-id="1a4cc-479">Formatar cartões</span><span class="sxs-lookup"><span data-stu-id="1a4cc-479">Format cards</span></span>](~/task-modules-and-cards/cards/cards-format.md)
