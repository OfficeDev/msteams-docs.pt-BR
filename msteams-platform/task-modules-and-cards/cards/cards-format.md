---
title: Formatação de texto em cartões
description: Descreve a formatação de texto do cartão em Microsoft Teams
keywords: formato de cartões de bots do teams
localization_priority: Normal
ms.topic: reference
ms.date: 03/29/2018
ms.openlocfilehash: 6a420ca549cd5131afc50813b5c8267f28073e5b
ms.sourcegitcommit: 9f499908437655d6ebdc6c4b3c3603ee220315b7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2021
ms.locfileid: "52949760"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="82468-104">Formatar cartões em Teams</span><span class="sxs-lookup"><span data-stu-id="82468-104">Format cards in Teams</span></span>

<span data-ttu-id="82468-105">Você pode adicionar formatação de rich text aos cartões usando Markdown ou HTML, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="82468-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="82468-106">Os cartões suportam formatação somente na propriedade text, não nas propriedades title ou subtitle.</span><span class="sxs-lookup"><span data-stu-id="82468-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="82468-107">A formatação pode ser especificada usando um subconjunto de formatação XML (HTML) ou Markdown, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="82468-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="82468-108">Para cartões adaptáveis de desenvolvimento atual e futuro usando formatação Markdown é recomendável.</span><span class="sxs-lookup"><span data-stu-id="82468-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="82468-109">O suporte à formatação difere entre diferentes tipos de cartão, e a renderização do cartão pode diferir ligeiramente entre a área de trabalho e os clientes Teams móveis, bem como Teams no navegador da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="82468-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="82468-110">Você pode incluir uma imagem em linha com qualquer Teams cartão.</span><span class="sxs-lookup"><span data-stu-id="82468-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="82468-111">Imagens formatadas como , ou arquivos e não devem exceder  `.png` `.jpg` `.gif` 1024 ×1024 px ou 1 MB.</span><span class="sxs-lookup"><span data-stu-id="82468-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="82468-112">Gif animado não tem suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="82468-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="82468-113">Para obter mais informações, consulte [Referência de cartões](./cards-reference.md#inline-card-images).</span><span class="sxs-lookup"><span data-stu-id="82468-113">For more information, see [Cards reference](./cards-reference.md#inline-card-images).</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="82468-114">Formatação de cartões com Markdown</span><span class="sxs-lookup"><span data-stu-id="82468-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="82468-115">Há dois tipos de cartão que suportam Markdown em Teams:</span><span class="sxs-lookup"><span data-stu-id="82468-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="82468-116">**Cartões adaptáveis**: a marcação é suportada no campo cartão `Textblock` adaptável, bem como `Fact.Title` e `Fact.Value` .</span><span class="sxs-lookup"><span data-stu-id="82468-116">**Adaptive cards**: Markdown is supported in Adaptive card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="82468-117">HTML não é suportado em cartões adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="82468-117">HTML is not supported in Adaptive cards.</span></span>
> * <span data-ttu-id="82468-118">**Cartões de conector O365**: Markdown e HTML limitado são compatíveis com Office 365 conectores nos campos de texto.</span><span class="sxs-lookup"><span data-stu-id="82468-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="82468-119">**Formatação de marcação: cartões adaptáveis**</span><span class="sxs-lookup"><span data-stu-id="82468-119">**Markdown formatting: Adaptive cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="82468-120">Os estilos com suporte `Textblock` para e `Fact.Title` `Fact.Value` são:</span><span class="sxs-lookup"><span data-stu-id="82468-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="82468-121">Style</span><span class="sxs-lookup"><span data-stu-id="82468-121">Style</span></span> | <span data-ttu-id="82468-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82468-122">Example</span></span> | <span data-ttu-id="82468-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="82468-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="82468-124">bold</span><span class="sxs-lookup"><span data-stu-id="82468-124">bold</span></span> | <span data-ttu-id="82468-125">**Negrito**</span><span class="sxs-lookup"><span data-stu-id="82468-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="82468-126">italic</span><span class="sxs-lookup"><span data-stu-id="82468-126">italic</span></span> | <span data-ttu-id="82468-127">_Itálico_</span><span class="sxs-lookup"><span data-stu-id="82468-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="82468-128">lista semordenagem</span><span class="sxs-lookup"><span data-stu-id="82468-128">unordered list</span></span> | <ul><li><span data-ttu-id="82468-129">texto</span><span class="sxs-lookup"><span data-stu-id="82468-129">text</span></span></li><li><span data-ttu-id="82468-130">texto</span><span class="sxs-lookup"><span data-stu-id="82468-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="82468-131">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="82468-131">ordered list</span></span> | <ol><li><span data-ttu-id="82468-132">texto</span><span class="sxs-lookup"><span data-stu-id="82468-132">text</span></span></li><li><span data-ttu-id="82468-133">texto</span><span class="sxs-lookup"><span data-stu-id="82468-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="82468-134">Hiperlinks</span><span class="sxs-lookup"><span data-stu-id="82468-134">Hyperlinks</span></span> |[<span data-ttu-id="82468-135">Bing</span><span class="sxs-lookup"><span data-stu-id="82468-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="82468-136">As seguintes marcas Markdown não são suportadas:</span><span class="sxs-lookup"><span data-stu-id="82468-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="82468-137">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="82468-137">Headers</span></span>
* <span data-ttu-id="82468-138">Tabelas</span><span class="sxs-lookup"><span data-stu-id="82468-138">Tables</span></span>
* <span data-ttu-id="82468-139">Imagens</span><span class="sxs-lookup"><span data-stu-id="82468-139">Images</span></span>
* <span data-ttu-id="82468-140">Texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="82468-140">Preformatted text</span></span>
* <span data-ttu-id="82468-141">Blockquotes</span><span class="sxs-lookup"><span data-stu-id="82468-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82468-142">Cartões adaptáveis não suportam formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="82468-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="82468-143">Linhas novas para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="82468-143">Newlines for Adaptive cards</span></span>

<span data-ttu-id="82468-144">Em listas, você pode usar `\r` as `\n` sequências de escape ou para newlines.</span><span class="sxs-lookup"><span data-stu-id="82468-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="82468-145">Usar `\n\n` em uma lista fará com que o próximo elemento da lista seja recuado.</span><span class="sxs-lookup"><span data-stu-id="82468-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="82468-146">Se você precisar de linhas novas em outro lugar do bloco de texto, use `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="82468-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="82468-147">Diferenças de dispositivos móveis e de área de trabalho para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="82468-147">Mobile and desktop differences for Adaptive cards</span></span>

<span data-ttu-id="82468-148">A formatação é ligeiramente diferente entre a área de trabalho e as versões móveis Teams.</span><span class="sxs-lookup"><span data-stu-id="82468-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="82468-149">Na área de trabalho, a formatação De marcação de cartão adaptável aparece assim nos navegadores da Web e no aplicativo cliente Teams cliente:</span><span class="sxs-lookup"><span data-stu-id="82468-149">On the desktop, Adaptive card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatação de markdown de cartão adaptável no cliente da área de trabalho](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="82468-151">No iOS, a formatação De marcação de cartão adaptável aparece assim:</span><span class="sxs-lookup"><span data-stu-id="82468-151">On iOS, Adaptive card Markdown formatting appears like this:</span></span>

![Formatação de markdown de cartão adaptável no iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="82468-153">No Android, a formatação adaptável de Marcação de Cartão aparece assim:</span><span class="sxs-lookup"><span data-stu-id="82468-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Formatação de markdown de cartão adaptável no Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="82468-155">Mais informações sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="82468-155">More information on Adaptive cards</span></span>

<span data-ttu-id="82468-156">[Recursos de texto em cartões adaptáveis](/adaptive-cards/create/textfeatures) Os recursos de data e localização mencionados neste tópico não são suportados Teams.</span><span class="sxs-lookup"><span data-stu-id="82468-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="82468-157">Exemplo de formatação para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="82468-157">Formatting sample for Adaptive cards</span></span>

``` json
{
    "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](https://adaptivecards.io)"
        }
    ]
}
```

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="82468-158">Mencionar suporte em cartões adaptáveis v1.2</span><span class="sxs-lookup"><span data-stu-id="82468-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="82468-159">As menções baseadas em cartão são suportadas em clientes web, desktop e móveis.</span><span class="sxs-lookup"><span data-stu-id="82468-159">Card based mentions are supported in web, desktop and mobile clients.</span></span> <span data-ttu-id="82468-160">Você pode adicionar @ menções em um corpo de cartão adaptável para bots e respostas de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="82468-160">You can add @ mentions within an adaptive card body for bots and messaging extension responses.</span></span> <span data-ttu-id="82468-161">Para adicionar @ menções em cartões, siga a mesma lógica de notificação e renderização das menções baseadas em mensagens em conversas de chat de canal [e grupo.](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions)</span><span class="sxs-lookup"><span data-stu-id="82468-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).</span></span>

<span data-ttu-id="82468-162">Bots e extensões de mensagens podem incluir menções no conteúdo do cartão nos [elementos TextBlock](https://adaptivecards.io/explorer/TextBlock.html) e [FactSet.](https://adaptivecards.io/explorer/FactSet.html)</span><span class="sxs-lookup"><span data-stu-id="82468-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="82468-163">[Atualmente,](https://adaptivecards.io/explorer/Media.html) os elementos de mídia não têm suporte em cartões adaptáveis v1.2 na plataforma Teams adaptável.</span><span class="sxs-lookup"><span data-stu-id="82468-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="82468-164">As & de equipe não são suportadas em mensagens bot.</span><span class="sxs-lookup"><span data-stu-id="82468-164">Channel & Team mentions are not supported in bot messages.</span></span>

#### <a name="constructing-mentions"></a><span data-ttu-id="82468-165">Criar menções</span><span class="sxs-lookup"><span data-stu-id="82468-165">Constructing mentions</span></span>

<span data-ttu-id="82468-166">Para incluir uma menção em um Cartão Adaptável, seu aplicativo precisa incluir os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="82468-166">To include a mention in an Adaptive Card your app needs to include the following elements:</span></span>

* <span data-ttu-id="82468-167">`<at>username</at>` nos elementos de cartão adaptáveis com suporte.</span><span class="sxs-lookup"><span data-stu-id="82468-167">`<at>username</at>` in the supported Adaptive card elements.</span></span>
* <span data-ttu-id="82468-168">O objeto dentro de uma propriedade no conteúdo do cartão, que inclui Teams id de usuário do `mention` usuário que está sendo `msteams` mencionado.</span><span class="sxs-lookup"><span data-stu-id="82468-168">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned.</span></span>
* <span data-ttu-id="82468-169">O `userId` é exclusivo da ID do bot e de um usuário específico.</span><span class="sxs-lookup"><span data-stu-id="82468-169">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="82468-170">Ele pode ser usado para @mention um usuário específico.</span><span class="sxs-lookup"><span data-stu-id="82468-170">It can be used to @mention a particular user.</span></span> <span data-ttu-id="82468-171">O `userId` pode ser recuperado usando uma das opções mencionadas em obter a [ID do usuário](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span><span class="sxs-lookup"><span data-stu-id="82468-171">The `userId` can be retrieved using one of the options mentioned in [get the user ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="82468-172">Exemplo de cartão adaptável com uma menção</span><span class="sxs-lookup"><span data-stu-id="82468-172">Sample Adaptive card with a mention</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.card.adaptive",
  "content": {
    "type": "AdaptiveCard",
    "body": [
      {
        "type": "TextBlock",
        "text": "Hi <at>John Doe</at>"
      }
    ],
    "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.0",
    "msteams": {
      "entities": [
        {
          "type": "mention",
          "text": "<at>John Doe</at>",
          "mentioned": {
            "id": "29:123124124124",
            "name": "John Doe"
          }
        }
      ]
    }
  }
}
```

### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="82468-173">Mascaramento de informações em cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="82468-173">Information masking in Adaptive cards</span></span>
<span data-ttu-id="82468-174">Use a propriedade mascarar informações para mascarar informações específicas, como senha ou informações confidenciais de usuários dentro do elemento de entrada de cartão [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) adaptável.</span><span class="sxs-lookup"><span data-stu-id="82468-174">Use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive card [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) input element.</span></span> 

> [!NOTE]
> <span data-ttu-id="82468-175">O recurso só dá suporte ao mascaramento de informações do lado do cliente, o texto de entrada mascarada é enviado como texto claro para o endereço de ponto de extremidade https especificado durante a configuração [do bot.](../../build-your-first-app/build-bot.md)</span><span class="sxs-lookup"><span data-stu-id="82468-175">The feature only supports client side information masking, the masked input text is sent as clear text to the https endpoint address that was specified during [bot configuration](../../build-your-first-app/build-bot.md).</span></span> 

> [!NOTE]
> <span data-ttu-id="82468-176">A propriedade de mascaramento de informações está disponível apenas na visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="82468-176">The information masking property is currently available in the developer preview only.</span></span>

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="82468-177">Cartão adaptável de exemplo com a propriedade mascaramento</span><span class="sxs-lookup"><span data-stu-id="82468-177">Sample Adaptive card with masking property</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
},
```

<span data-ttu-id="82468-178">A imagem a seguir é um exemplo de informações de mascaramento em cartões adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="82468-178">The following image is an example of masking information in Adaptive cards:</span></span>

![Imagem de informações de mascaramento](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="82468-180">Cartão adaptável de largura total</span><span class="sxs-lookup"><span data-stu-id="82468-180">Full width Adaptive card</span></span>
<span data-ttu-id="82468-181">Você pode usar a propriedade para expandir a largura de um `msteams` cartão Adaptável e usar espaço adicional de tela.</span><span class="sxs-lookup"><span data-stu-id="82468-181">You can use the `msteams` property to expand the width of an Adaptive card and make use of additional canvas space.</span></span> <span data-ttu-id="82468-182">Para obter informações sobre como usar a propriedade, consulte o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="82468-182">For information on how to use the property, see the following example:</span></span>

#### <a name="constructing-full-width-cards"></a><span data-ttu-id="82468-183">Construir cartões de largura total</span><span class="sxs-lookup"><span data-stu-id="82468-183">Constructing full width cards</span></span>
<span data-ttu-id="82468-184">Para fazer um cartão adaptável de largura total, o objeto na propriedade no conteúdo do cartão deve `width` `msteams` ser definido como `Full` .</span><span class="sxs-lookup"><span data-stu-id="82468-184">To make a full width Adaptive card the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>
<span data-ttu-id="82468-185">Além disso, seu aplicativo deve incluir os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="82468-185">In addition, your app must include the following elements:</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="82468-186">Exemplo de cartão adaptável com largura total</span><span class="sxs-lookup"><span data-stu-id="82468-186">Sample adaptive card with full width</span></span>

``` json
{
    "type": "AdaptiveCard",
    "body": [{
        "type": "Container",
        "items": [{
            "type": "TextBlock",
            "text": "Digest card",
            "size": "Large",
            "weight": "Bolder"
        }]
    }],

    "msteams": {
        "width": "Full"
    },
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

<span data-ttu-id="82468-187">Um Cartão Adaptável de largura total aparece da seguinte forma: Exibição de Cartão Adaptável de largura ![ total](../../assets/images/cards/full-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="82468-187">A full width Adaptive Card appears as follows: ![Full width Adaptive Card view](../../assets/images/cards/full-width-adaptive-card.png)</span></span>

<span data-ttu-id="82468-188">Se você não tiver definido a propriedade como Full , o modo de exibição padrão do Cartão Adaptável aparecerá da seguinte forma: Modo de exibição cartão adaptável de largura `width`  ![ pequena](../../assets/images/cards/small-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="82468-188">If you have not set the `width` property to *Full*, then the default view of the Adaptive Card appears as follows: ![Small width Adaptive Card view](../../assets/images/cards/small-width-adaptive-card.png)</span></span>

### <a name="typeahead-support"></a><span data-ttu-id="82468-189">Suporte a Typeahead</span><span class="sxs-lookup"><span data-stu-id="82468-189">Typeahead support</span></span>

<span data-ttu-id="82468-190">Dentro do elemento de esquema, pedir que os usuários filtrem e selecionem por meio de um número considerável de opções podem reduzir significativamente a conclusão [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) da tarefa.</span><span class="sxs-lookup"><span data-stu-id="82468-190">Within the [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) schema element, asking users to filter through and select through a sizable number of choices can significantly slow down task completion.</span></span> <span data-ttu-id="82468-191">O suporte a typeahead em cartões adaptáveis pode simplificar a seleção de entrada restringindo ou filtrando o conjunto de opções de entrada enquanto um usuário digita a entrada.</span><span class="sxs-lookup"><span data-stu-id="82468-191">Typeahead support within Adaptive cards can simplify input selection by narrowing or filtering the set of input choices as a user is typing the input.</span></span> 

#### <a name="enable-typeahead-in-adaptive-cards"></a><span data-ttu-id="82468-192">Habilitar typeahead em cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="82468-192">Enable typeahead in Adaptive cards</span></span>

<span data-ttu-id="82468-193">Para habilitar typeahead dentro `Input.Choiceset` do conjunto para e garantir que está definido como `style` `filtered` `isMultiSelect` `false` .</span><span class="sxs-lookup"><span data-stu-id="82468-193">To enable typeahead within the `Input.Choiceset` set `style` to `filtered` and ensure `isMultiSelect` is set to `false`.</span></span> 

#### <a name="sample-adaptive-card-with-typeahead-support"></a><span data-ttu-id="82468-194">Exemplo de cartão adaptável com suporte a typeahead</span><span class="sxs-lookup"><span data-stu-id="82468-194">Sample adaptive card with typeahead support</span></span>

``` json
{
   "type": "Input.ChoiceSet",
   "label": "Select a user",
   "isMultiSelect": false,
   "choices":  [
      { "title": "User 1", "value": "User1" },
      { "title": "User 2", "value": "User2" }
    ],
   "style": "filtered"
}
``` 

### <a name="stage-view-for-images-in-adaptive-cards"></a><span data-ttu-id="82468-195">Exibição de estágio para imagens em Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="82468-195">Stage view for images in Adaptive Cards</span></span>

<span data-ttu-id="82468-196">Em um cartão Adaptável, você pode usar a propriedade para adicionar a capacidade de exibir imagens na exibição `msteams` de estágio seletivamente.</span><span class="sxs-lookup"><span data-stu-id="82468-196">In an Adaptive card, you can use the `msteams` property to add the ability to display images in stage view selectively.</span></span> <span data-ttu-id="82468-197">Quando os usuários pairam sobre as imagens, eles veriam um ícone de expansão, para o qual o `allowExpand` atributo é definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="82468-197">When users hover over the images, they would see an expand icon, for which the `allowExpand` attribute is set to `true`.</span></span> <span data-ttu-id="82468-198">Para obter informações sobre como usar a propriedade, consulte o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="82468-198">For information on how to use the property, see the following example:</span></span>

``` json
{
    "type": "AdaptiveCard",
     "body": [
          {
            "type": "Image",
            "url": "https://picsum.photos/200/200?image=110",
            "msTeams": {
              "allowExpand": true
            }
          },
     ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

<span data-ttu-id="82468-199">Quando os usuários pairam sobre a imagem, um ícone de expansão aparece no canto superior direito da imagem: cartão adaptável com imagem ![ expansível](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span><span class="sxs-lookup"><span data-stu-id="82468-199">When users hover over the image, an expand icon appears at top right corner of the image: ![Adaptive card with expandable image](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span></span>

<span data-ttu-id="82468-200">A imagem aparece no exibição de estágio quando o usuário seleciona o botão expandir: ![ Imagem expandida para exibição de estágio](../../assets/images/cards/adaptivecard-expand-image.png)</span><span class="sxs-lookup"><span data-stu-id="82468-200">The image appears in stage view when the user selects the expand button: ![Image expanded to stage view](../../assets/images/cards/adaptivecard-expand-image.png)</span></span>

<span data-ttu-id="82468-201">Na exibição de estágio, os usuários podem ampliar e diminuir o zoom da imagem.</span><span class="sxs-lookup"><span data-stu-id="82468-201">In the stage view, users can zoom in and zoom out of the image.</span></span> <span data-ttu-id="82468-202">Você pode selecionar quais imagens em seu cartão adaptável precisam ter esse recurso.</span><span class="sxs-lookup"><span data-stu-id="82468-202">You can select which images in your Adaptive card needs to have this capability.</span></span>

> [!NOTE]
> <span data-ttu-id="82468-203">A funcionalidade de zoom e zoom só se aplica aos elementos de imagem (tipo de imagem) em um cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="82468-203">Zoom in and zoom out capability applies only to the image elements (Image type) in an Adaptive card.</span></span>

> [!NOTE]
> <span data-ttu-id="82468-204">Para aplicativos móveis do Teams, a funcionalidade de exibição de estágio para imagens em Cartões Adaptáveis está disponível por padrão e os usuários poderão exibir imagens de cartão adaptáveis no modo de exibição de estágio simplesmente tocando na imagem, independentemente de o atributo estar presente ou `allowExpand` não.</span><span class="sxs-lookup"><span data-stu-id="82468-204">For Teams mobile apps, stage view functionality for images in Adaptive Cards are available by default and users will be able to view Adaptive card images in stage view by simply tapping on the image, irrespective of whether the `allowExpand` attribute is present or not.</span></span>

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="82468-205">**Formatação de marcação: cartões de conector O365**</span><span class="sxs-lookup"><span data-stu-id="82468-205">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="82468-206">Os cartões conectores suportam a formatação limitada markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="82468-206">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="82468-207">O suporte HTML é descrito na última seção.</span><span class="sxs-lookup"><span data-stu-id="82468-207">HTML support is described in the last section.</span></span>

| <span data-ttu-id="82468-208">Style</span><span class="sxs-lookup"><span data-stu-id="82468-208">Style</span></span> | <span data-ttu-id="82468-209">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82468-209">Example</span></span> | <span data-ttu-id="82468-210">Markdown</span><span class="sxs-lookup"><span data-stu-id="82468-210">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="82468-211">bold</span><span class="sxs-lookup"><span data-stu-id="82468-211">bold</span></span> | <span data-ttu-id="82468-212">**text**</span><span class="sxs-lookup"><span data-stu-id="82468-212">**text**</span></span> | `**text**` |
| <span data-ttu-id="82468-213">italic</span><span class="sxs-lookup"><span data-stu-id="82468-213">italic</span></span> | <span data-ttu-id="82468-214">*text*</span><span class="sxs-lookup"><span data-stu-id="82468-214">*text*</span></span> | `*text*` |
| <span data-ttu-id="82468-215">header (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="82468-215">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="82468-216">**Texto**</span><span class="sxs-lookup"><span data-stu-id="82468-216">**Text**</span></span> | `### Text`|
| <span data-ttu-id="82468-217">strikethrough</span><span class="sxs-lookup"><span data-stu-id="82468-217">strikethrough</span></span> | <span data-ttu-id="82468-218">~~text~~</span><span class="sxs-lookup"><span data-stu-id="82468-218">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="82468-219">lista semordenagem</span><span class="sxs-lookup"><span data-stu-id="82468-219">unordered list</span></span> | <ul><li><span data-ttu-id="82468-220">texto</span><span class="sxs-lookup"><span data-stu-id="82468-220">text</span></span></li><li><span data-ttu-id="82468-221">texto</span><span class="sxs-lookup"><span data-stu-id="82468-221">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="82468-222">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="82468-222">ordered list</span></span> | <ol><li><span data-ttu-id="82468-223">texto</span><span class="sxs-lookup"><span data-stu-id="82468-223">text</span></span></li><li><span data-ttu-id="82468-224">texto</span><span class="sxs-lookup"><span data-stu-id="82468-224">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="82468-225">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="82468-225">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="82468-226">blockquote</span><span class="sxs-lookup"><span data-stu-id="82468-226">blockquote</span></span> | <span data-ttu-id="82468-227">>texto blockquote</span><span class="sxs-lookup"><span data-stu-id="82468-227">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="82468-228">hiperlink</span><span class="sxs-lookup"><span data-stu-id="82468-228">hyperlink</span></span> | [<span data-ttu-id="82468-229">Bing</span><span class="sxs-lookup"><span data-stu-id="82468-229">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="82468-230">link de imagem</span><span class="sxs-lookup"><span data-stu-id="82468-230">image link</span></span> |![Duck on a rock](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="82468-232">Em cartões de conector, as linhas novas são renderizadas `\n\n` para , mas não para ou `\n` `\r` .</span><span class="sxs-lookup"><span data-stu-id="82468-232">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="82468-233">Diferenças de dispositivos móveis e de área de trabalho para cartões de conector usando Markdown</span><span class="sxs-lookup"><span data-stu-id="82468-233">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="82468-234">Na área de trabalho, a formatação markdown para cartões de conector tem a mesma aparência:</span><span class="sxs-lookup"><span data-stu-id="82468-234">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Formatação de marcação para cartões conectores no cliente desktop](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="82468-236">No iOS, a formatação markdown para cartões de conector tem a aparência:</span><span class="sxs-lookup"><span data-stu-id="82468-236">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Formatação de marcação para cartões conectores no cliente iOS](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="82468-238">Problemas:</span><span class="sxs-lookup"><span data-stu-id="82468-238">Issues:</span></span>

* <span data-ttu-id="82468-239">O cliente iOS para Teams não renderiza imagens em linha Markdown ou HTML em Cartões conectores.</span><span class="sxs-lookup"><span data-stu-id="82468-239">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="82468-240">As blockquotes são renderizadas como recuadas, mas sem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="82468-240">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="82468-241">No Android, a formatação markdown para cartões de conector tem a aparência:</span><span class="sxs-lookup"><span data-stu-id="82468-241">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Formatação de marcação para cartões conectores no cliente Android](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="82468-243">Exemplo de formatação para Cartões de Conector de Markdown</span><span class="sxs-lookup"><span data-stu-id="82468-243">Formatting example for Markdown Connector Cards</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "https://schema.org/extensions",
    "summary": "Summary",
    "title": "Connector Card Markdown formatting",
    "sections": [
        {
            "text": "This is some **bold** text"
        },
        {
            "text": "This is some _italic_ text"
        },
        {
            "text": "# Header 1\r## Header 2\r### Header 3"
        },
        {
            "text": "- Bullet \r- List \r"
        },
        {
            "text": "1. Numbered\r1. List \r"
        },
        {
            "text": "Link: [Bing](https://www.bing.com)"
        },
        {
            "text": "embedded image link: ![Duck on a rock](https://aka.ms/Fo983c)"
        },
        {
            "text": "`preformatted text`"
        },
        {
            "text": "Newlines (backslash n, backslash n):\n\nline a\n\nline b\n\nline c"
        },
        {
            "text": ">This is a blockquote"
        }
     ]
  }
}

```

---

## <a name="formatting-cards-with-html"></a><span data-ttu-id="82468-244">Formatação de cartões com HTML</span><span class="sxs-lookup"><span data-stu-id="82468-244">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="82468-245">**Formatação HTML: Cartões de conector O365**</span><span class="sxs-lookup"><span data-stu-id="82468-245">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="82468-246">Os cartões conectores suportam a formatação limitada markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="82468-246">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="82468-247">Markdown é descrito na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="82468-247">Markdown is described in the next section.</span></span>

| <span data-ttu-id="82468-248">Style</span><span class="sxs-lookup"><span data-stu-id="82468-248">Style</span></span> | <span data-ttu-id="82468-249">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82468-249">Example</span></span> | <span data-ttu-id="82468-250">HTML</span><span class="sxs-lookup"><span data-stu-id="82468-250">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="82468-251">bold</span><span class="sxs-lookup"><span data-stu-id="82468-251">bold</span></span> | <span data-ttu-id="82468-252">**text**</span><span class="sxs-lookup"><span data-stu-id="82468-252">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="82468-253">italic</span><span class="sxs-lookup"><span data-stu-id="82468-253">italic</span></span> | <span data-ttu-id="82468-254">*text*</span><span class="sxs-lookup"><span data-stu-id="82468-254">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="82468-255">header (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="82468-255">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="82468-256">**Texto**</span><span class="sxs-lookup"><span data-stu-id="82468-256">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="82468-257">strikethrough</span><span class="sxs-lookup"><span data-stu-id="82468-257">strikethrough</span></span> | <span data-ttu-id="82468-258">~~text~~</span><span class="sxs-lookup"><span data-stu-id="82468-258">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="82468-259">lista semordenagem</span><span class="sxs-lookup"><span data-stu-id="82468-259">unordered list</span></span> | <ul><li><span data-ttu-id="82468-260">texto</span><span class="sxs-lookup"><span data-stu-id="82468-260">text</span></span></li><li><span data-ttu-id="82468-261">texto</span><span class="sxs-lookup"><span data-stu-id="82468-261">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="82468-262">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="82468-262">ordered list</span></span> | <ol><li><span data-ttu-id="82468-263">texto</span><span class="sxs-lookup"><span data-stu-id="82468-263">text</span></span></li><li><span data-ttu-id="82468-264">texto</span><span class="sxs-lookup"><span data-stu-id="82468-264">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="82468-265">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="82468-265">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="82468-266">blockquote</span><span class="sxs-lookup"><span data-stu-id="82468-266">blockquote</span></span> | <blockquote><span data-ttu-id="82468-267">texto</span><span class="sxs-lookup"><span data-stu-id="82468-267">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="82468-268">hiperlink</span><span class="sxs-lookup"><span data-stu-id="82468-268">hyperlink</span></span> | [<span data-ttu-id="82468-269">Bing</span><span class="sxs-lookup"><span data-stu-id="82468-269">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="82468-270">link de imagem</span><span class="sxs-lookup"><span data-stu-id="82468-270">image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="82468-271">Em cartões de conector, as linhas novas são renderizadas em HTML usando a `<p>` marca.</span><span class="sxs-lookup"><span data-stu-id="82468-271">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="82468-272">Diferenças de dispositivos móveis e de área de trabalho para cartões de conector usando HTML</span><span class="sxs-lookup"><span data-stu-id="82468-272">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="82468-273">Na área de trabalho, a formatação HTML para cartões de conector tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="82468-273">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente desktop](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="82468-275">No iOS, a formatação HTML tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="82468-275">On iOS, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente iOS](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="82468-277">Problemas:</span><span class="sxs-lookup"><span data-stu-id="82468-277">Issues:</span></span>

* <span data-ttu-id="82468-278">As imagens em linha não são renderizadas no iOS usando Markdown ou HTML em Cartões de Conector.</span><span class="sxs-lookup"><span data-stu-id="82468-278">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="82468-279">O texto pré-formatado é renderizado, mas não tem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="82468-279">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="82468-280">No Android, a formatação HTML tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="82468-280">On Android, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente Android](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="82468-282">Exemplo de formatação para cartões de conector HTML</span><span class="sxs-lookup"><span data-stu-id="82468-282">Formatting sample for HTML Connector Cards</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "https://schema.org/extensions",
    "summary": "Summary",
    "title": "Connector Card HTML formatting",
    "sections": [
        {
            "text": "This is some <strong>bold</strong> text"
        },
        {
            "text": "This is some <em>italic</em> text"
        },
        {
            "text": "This is some <strike>strikethrough</strike> text"
        },
        {
            "text": "<h1>Header 1</h1>\r<h2>Header 2</h2>\r <h3>Header 3</h3>"
        },
        {
            "text": "bullet list <ul><li>text</li><li>text</li></ul>"
        },
        {
            "text": "ordered list <ol><li>text</li><li>text</li></ol>"
        },
        {
            "text": "hyperlink <a href=\"https://www.bing.com/\">Bing</a>"
        },
        {
            "text": "embedded image <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img>"
        },
        {
            "text": "preformatted text <pre>text</pre>"
        },
        {
            "text": "Paragraphs <p>Line a</p><p>Line b</p>"
        },
        {
            "text": "<blockquote>Blockquote text</blockquote>"
        }
     ]
  }
}

```

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="82468-283">**Formatação HTML: cartões de herói e miniatura**</span><span class="sxs-lookup"><span data-stu-id="82468-283">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="82468-284">As marcas HTML são suportadas para cartões simples, como o herói e o cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="82468-284">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="82468-285">Não há suporte para markdown.</span><span class="sxs-lookup"><span data-stu-id="82468-285">Markdown is not supported.</span></span>

| <span data-ttu-id="82468-286">Style</span><span class="sxs-lookup"><span data-stu-id="82468-286">Style</span></span> | <span data-ttu-id="82468-287">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82468-287">Example</span></span> | <span data-ttu-id="82468-288">HTML</span><span class="sxs-lookup"><span data-stu-id="82468-288">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="82468-289">bold</span><span class="sxs-lookup"><span data-stu-id="82468-289">bold</span></span> | <span data-ttu-id="82468-290">**text**</span><span class="sxs-lookup"><span data-stu-id="82468-290">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="82468-291">italic</span><span class="sxs-lookup"><span data-stu-id="82468-291">italic</span></span> | <span data-ttu-id="82468-292">*text*</span><span class="sxs-lookup"><span data-stu-id="82468-292">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="82468-293">header (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="82468-293">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="82468-294">**Texto**</span><span class="sxs-lookup"><span data-stu-id="82468-294">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="82468-295">strikethrough</span><span class="sxs-lookup"><span data-stu-id="82468-295">strikethrough</span></span> | <span data-ttu-id="82468-296">~~text~~</span><span class="sxs-lookup"><span data-stu-id="82468-296">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="82468-297">lista semordenagem</span><span class="sxs-lookup"><span data-stu-id="82468-297">unordered list</span></span> | <ul><li><span data-ttu-id="82468-298">texto</span><span class="sxs-lookup"><span data-stu-id="82468-298">text</span></span></li><li><span data-ttu-id="82468-299">texto</span><span class="sxs-lookup"><span data-stu-id="82468-299">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="82468-300">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="82468-300">ordered list</span></span> | <ol><li><span data-ttu-id="82468-301">texto</span><span class="sxs-lookup"><span data-stu-id="82468-301">text</span></span></li><li><span data-ttu-id="82468-302">texto</span><span class="sxs-lookup"><span data-stu-id="82468-302">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="82468-303">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="82468-303">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="82468-304">blockquote</span><span class="sxs-lookup"><span data-stu-id="82468-304">blockquote</span></span> | <blockquote><span data-ttu-id="82468-305">texto</span><span class="sxs-lookup"><span data-stu-id="82468-305">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="82468-306">hiperlink</span><span class="sxs-lookup"><span data-stu-id="82468-306">hyperlink</span></span> | [<span data-ttu-id="82468-307">Bing</span><span class="sxs-lookup"><span data-stu-id="82468-307">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="82468-308">link de imagem</span><span class="sxs-lookup"><span data-stu-id="82468-308">image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="82468-309">Diferenças de dispositivos móveis e de área de trabalho para cartões simples</span><span class="sxs-lookup"><span data-stu-id="82468-309">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="82468-310">Devido às diferenças de resolução entre a área de trabalho e a plataforma móvel, a formatação é diferente entre a área de trabalho e a versão móvel do Teams.</span><span class="sxs-lookup"><span data-stu-id="82468-310">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="82468-311">Na área de trabalho, a formatação HTML aparece assim:</span><span class="sxs-lookup"><span data-stu-id="82468-311">On the desktop, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente desktop](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="82468-313">No iOS, a formatação HTML aparece assim:</span><span class="sxs-lookup"><span data-stu-id="82468-313">On iOS, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente iOS](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="82468-315">Problemas:</span><span class="sxs-lookup"><span data-stu-id="82468-315">Issues:</span></span>

* <span data-ttu-id="82468-316">A formatação de caracteres como negrito e itálico não é renderizada no iOS.</span><span class="sxs-lookup"><span data-stu-id="82468-316">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="82468-317">No Android, a formatação HTML aparece assim:</span><span class="sxs-lookup"><span data-stu-id="82468-317">On Android, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente Android](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="82468-319">Formatação de caracteres como negrito e exibição itálico corretamente no Android.</span><span class="sxs-lookup"><span data-stu-id="82468-319">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="82468-320">Exemplo de formatação para formatação HTML em cartões simples</span><span class="sxs-lookup"><span data-stu-id="82468-320">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="82468-321">Essas capturas de tela foram criadas usando Teams AppStudio, onde a propriedade de texto de um cartão de herói foi definida como a cadeia de caracteres a seguir.</span><span class="sxs-lookup"><span data-stu-id="82468-321">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="82468-322">Você pode testar a formatação em seus próprios cartões modificando esse código.</span><span class="sxs-lookup"><span data-stu-id="82468-322">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
