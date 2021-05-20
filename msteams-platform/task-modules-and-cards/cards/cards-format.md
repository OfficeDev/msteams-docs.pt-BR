---
title: Formatação de texto em cartões
description: Descreve a formatação de texto de cartão em Microsoft Teams
keywords: equipes bots formato de cartões
localization_priority: Normal
ms.topic: reference
ms.date: 03/29/2018
ms.openlocfilehash: 848656097f2c865705cc0d91dece93049d8c6790
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566576"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="05b8b-104">Cartões de formato em Teams</span><span class="sxs-lookup"><span data-stu-id="05b8b-104">Format cards in Teams</span></span>

<span data-ttu-id="05b8b-105">Você pode adicionar formatação de texto rica em seus cartões usando markdown ou HTML, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="05b8b-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="05b8b-106">Os cartões suportam a formatação apenas na propriedade de texto, não nas propriedades do título ou da legenda.</span><span class="sxs-lookup"><span data-stu-id="05b8b-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="05b8b-107">A formatação pode ser especificada usando um subconjunto de formatação XML (HTML) ou Markdown, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="05b8b-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="05b8b-108">Para o desenvolvimento atual e futuro, é recomendado cartões adaptativos usando a formatação markdown.</span><span class="sxs-lookup"><span data-stu-id="05b8b-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="05b8b-109">O suporte de formatação difere entre diferentes tipos de cartão, e a renderização do cartão pode diferir ligeiramente entre o desktop e o celular Teams clientes, bem como Teams no navegador de desktop.</span><span class="sxs-lookup"><span data-stu-id="05b8b-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="05b8b-110">Você pode incluir uma imagem inline com qualquer cartão Teams.</span><span class="sxs-lookup"><span data-stu-id="05b8b-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="05b8b-111">As imagens são formatadas  `.png` `.jpg` como, ou `.gif` arquivos, e não devem exceder 1024 ×1024 px ou 1 MB.</span><span class="sxs-lookup"><span data-stu-id="05b8b-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="05b8b-112">Gif animado não é suportado oficialmente.</span><span class="sxs-lookup"><span data-stu-id="05b8b-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="05b8b-113">Para obter mais informações, consulte [referência de Cartões](./cards-reference.md#inline-card-images).</span><span class="sxs-lookup"><span data-stu-id="05b8b-113">For more information, see [Cards reference](./cards-reference.md#inline-card-images).</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="05b8b-114">Cartões de formatação com Markdown</span><span class="sxs-lookup"><span data-stu-id="05b8b-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="05b8b-115">Existem dois tipos de cartões que suportam markdown em Teams:</span><span class="sxs-lookup"><span data-stu-id="05b8b-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="05b8b-116">**Cartões adaptativos**: A marcação é suportada no campo de cartas `Textblock` adaptativas, bem como `Fact.Title` . `Fact.Value`</span><span class="sxs-lookup"><span data-stu-id="05b8b-116">**Adaptive cards**: Markdown is supported in Adaptive card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="05b8b-117">HTML não é suportado em cartões adaptativos.</span><span class="sxs-lookup"><span data-stu-id="05b8b-117">HTML is not supported in Adaptive cards.</span></span>
> * <span data-ttu-id="05b8b-118">**Placas conectoras O365**: Markdown e HTML limitado são suportados em Office 365 placas Connector nos campos de texto.</span><span class="sxs-lookup"><span data-stu-id="05b8b-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="05b8b-119">**Formatação de markdown: Cartões adaptativos**</span><span class="sxs-lookup"><span data-stu-id="05b8b-119">**Markdown formatting: Adaptive cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="05b8b-120">Os estilos suportados para `Textblock` , `Fact.Title` e `Fact.Value` são:</span><span class="sxs-lookup"><span data-stu-id="05b8b-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="05b8b-121">Style</span><span class="sxs-lookup"><span data-stu-id="05b8b-121">Style</span></span> | <span data-ttu-id="05b8b-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05b8b-122">Example</span></span> | <span data-ttu-id="05b8b-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="05b8b-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="05b8b-124">bold</span><span class="sxs-lookup"><span data-stu-id="05b8b-124">bold</span></span> | <span data-ttu-id="05b8b-125">**Negrito**</span><span class="sxs-lookup"><span data-stu-id="05b8b-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="05b8b-126">italic</span><span class="sxs-lookup"><span data-stu-id="05b8b-126">italic</span></span> | <span data-ttu-id="05b8b-127">_Itálico_</span><span class="sxs-lookup"><span data-stu-id="05b8b-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="05b8b-128">lista não rdenada</span><span class="sxs-lookup"><span data-stu-id="05b8b-128">unordered list</span></span> | <ul><li><span data-ttu-id="05b8b-129">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-129">text</span></span></li><li><span data-ttu-id="05b8b-130">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="05b8b-131">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="05b8b-131">ordered list</span></span> | <ol><li><span data-ttu-id="05b8b-132">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-132">text</span></span></li><li><span data-ttu-id="05b8b-133">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="05b8b-134">Hiperlinks</span><span class="sxs-lookup"><span data-stu-id="05b8b-134">Hyperlinks</span></span> |[<span data-ttu-id="05b8b-135">Bing</span><span class="sxs-lookup"><span data-stu-id="05b8b-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="05b8b-136">As seguintes tags Markdown não são suportadas:</span><span class="sxs-lookup"><span data-stu-id="05b8b-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="05b8b-137">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="05b8b-137">Headers</span></span>
* <span data-ttu-id="05b8b-138">Tabelas</span><span class="sxs-lookup"><span data-stu-id="05b8b-138">Tables</span></span>
* <span data-ttu-id="05b8b-139">Imagens</span><span class="sxs-lookup"><span data-stu-id="05b8b-139">Images</span></span>
* <span data-ttu-id="05b8b-140">Texto pré-formado</span><span class="sxs-lookup"><span data-stu-id="05b8b-140">Preformatted text</span></span>
* <span data-ttu-id="05b8b-141">Cotas de bloqueio</span><span class="sxs-lookup"><span data-stu-id="05b8b-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05b8b-142">As placas adaptativas não suportam formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="05b8b-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="05b8b-143">Linhas novas para cartões adaptativos</span><span class="sxs-lookup"><span data-stu-id="05b8b-143">Newlines for Adaptive cards</span></span>

<span data-ttu-id="05b8b-144">Em listas você pode usar as `\r` `\n` sequências ou escape para linhas novas.</span><span class="sxs-lookup"><span data-stu-id="05b8b-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="05b8b-145">O uso `\n\n` em uma lista fará com que o próximo elemento da lista seja recuado.</span><span class="sxs-lookup"><span data-stu-id="05b8b-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="05b8b-146">Se você precisar de novas linhas em outros lugares no bloco de texto, use `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="05b8b-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="05b8b-147">Diferenças móveis e desktop para cartões adaptativos</span><span class="sxs-lookup"><span data-stu-id="05b8b-147">Mobile and desktop differences for Adaptive cards</span></span>

<span data-ttu-id="05b8b-148">A formatação é ligeiramente diferente entre a área de trabalho e as versões móveis de Teams.</span><span class="sxs-lookup"><span data-stu-id="05b8b-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="05b8b-149">No desktop, a formatação de marcação de cartão adaptável aparece assim tanto em navegadores da Web quanto no aplicativo Teams cliente:</span><span class="sxs-lookup"><span data-stu-id="05b8b-149">On the desktop, Adaptive card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Marcação de marcação de cartão adaptativo no cliente de desktop](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="05b8b-151">No iOS, a formatação de marcação de cartão adaptável aparece assim:</span><span class="sxs-lookup"><span data-stu-id="05b8b-151">On iOS, Adaptive card Markdown formatting appears like this:</span></span>

![Marcação de cartão adaptativo no iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="05b8b-153">No Android, a formatação de marcação de cartão adaptativo aparece assim:</span><span class="sxs-lookup"><span data-stu-id="05b8b-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Marcação de cartão adaptativo no Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="05b8b-155">Mais informações sobre cartões adaptativos</span><span class="sxs-lookup"><span data-stu-id="05b8b-155">More information on Adaptive cards</span></span>

<span data-ttu-id="05b8b-156">[Recursos de texto em cartões adaptativos](/adaptive-cards/create/textfeatures) As características de data e localização mencionadas neste tópico não são suportadas em Teams.</span><span class="sxs-lookup"><span data-stu-id="05b8b-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="05b8b-157">Amostra de formatação para cartões adaptativos</span><span class="sxs-lookup"><span data-stu-id="05b8b-157">Formatting sample for Adaptive cards</span></span>

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

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="05b8b-158">Mencionar suporte em cartões adaptativos v1.2</span><span class="sxs-lookup"><span data-stu-id="05b8b-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="05b8b-159">As menções baseadas em cartões são suportadas em clientes web, desktop e mobile.</span><span class="sxs-lookup"><span data-stu-id="05b8b-159">Card based mentions are supported in web, desktop and mobile clients.</span></span> <span data-ttu-id="05b8b-160">Você pode adicionar @ menções dentro de um corpo de cartão adaptativo para bots e respostas de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="05b8b-160">You can add @ mentions within an adaptive card body for bots and messaging extension responses.</span></span> <span data-ttu-id="05b8b-161">Para adicionar @ menções em cartões, siga a mesma lógica de notificação e renderização que a das [menções baseadas em mensagens em conversas de bate-papo de canal e grupo](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).</span><span class="sxs-lookup"><span data-stu-id="05b8b-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).</span></span>

<span data-ttu-id="05b8b-162">Bots e extensões de mensagens podem incluir menções dentro do conteúdo do cartão nos elementos [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) e [FactSet.](https://adaptivecards.io/explorer/FactSet.html)</span><span class="sxs-lookup"><span data-stu-id="05b8b-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="05b8b-163">[Atualmente, os elementos](https://adaptivecards.io/explorer/Media.html) de mídia não são suportados em cartões adaptáveis v1.2 na plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="05b8b-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="05b8b-164">As menções da Equipe de & do canal não são suportadas em mensagens de bot.</span><span class="sxs-lookup"><span data-stu-id="05b8b-164">Channel & Team mentions are not supported in bot messages.</span></span>

#### <a name="constructing-mentions"></a><span data-ttu-id="05b8b-165">Construindo menções</span><span class="sxs-lookup"><span data-stu-id="05b8b-165">Constructing mentions</span></span>

<span data-ttu-id="05b8b-166">Para incluir uma menção em um Cartão Adaptativo, seu aplicativo precisa incluir os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="05b8b-166">To include a mention in an Adaptive Card your app needs to include the following elements:</span></span>

* <span data-ttu-id="05b8b-167">`<at>username</at>` nos elementos de cartão adaptável suportados.</span><span class="sxs-lookup"><span data-stu-id="05b8b-167">`<at>username</at>` in the supported Adaptive card elements.</span></span>
* <span data-ttu-id="05b8b-168">O `mention` objeto dentro de uma propriedade no conteúdo do `msteams` cartão, que inclui a Teams identificação do usuário do usuário sendo mencionado.</span><span class="sxs-lookup"><span data-stu-id="05b8b-168">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned.</span></span>
* <span data-ttu-id="05b8b-169">O `userId` é exclusivo do seu ID do bot e de um determinado usuário.</span><span class="sxs-lookup"><span data-stu-id="05b8b-169">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="05b8b-170">Ele pode ser usado para @mention um determinado usuário.</span><span class="sxs-lookup"><span data-stu-id="05b8b-170">It can be used to @mention a particular user.</span></span> <span data-ttu-id="05b8b-171">O `userId` pode ser recuperado usando uma das opções mencionadas na [ção do ID do usuário](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span><span class="sxs-lookup"><span data-stu-id="05b8b-171">The `userId` can be retrieved using one of the options mentioned in [get the user ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="05b8b-172">Cartão adaptável da amostra com uma menção</span><span class="sxs-lookup"><span data-stu-id="05b8b-172">Sample Adaptive card with a mention</span></span>

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

### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="05b8b-173">Mascaramento de informações em cartões adaptativos</span><span class="sxs-lookup"><span data-stu-id="05b8b-173">Information masking in Adaptive cards</span></span>
<span data-ttu-id="05b8b-174">Use a propriedade de mascaramento de informações para mascarar informações específicas, como senha ou informações confidenciais dos usuários dentro do elemento de entrada do cartão [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Adaptive.</span><span class="sxs-lookup"><span data-stu-id="05b8b-174">Use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive card [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) input element.</span></span> 

> [!NOTE]
> <span data-ttu-id="05b8b-175">O recurso suporta apenas o mascaramento de informações do lado do cliente, o texto de entrada mascarado é enviado como texto claro para o endereço final https especificado durante a [configuração do bot](../../build-your-first-app/build-bot.md).</span><span class="sxs-lookup"><span data-stu-id="05b8b-175">The feature only supports client side information masking, the masked input text is sent as clear text to the https endpoint address that was specified during [bot configuration](../../build-your-first-app/build-bot.md).</span></span> 

> [!NOTE]
> <span data-ttu-id="05b8b-176">A propriedade de mascaramento de informações está disponível apenas na pré-visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="05b8b-176">The information masking property is currently available in the developer preview only.</span></span>

<span data-ttu-id="05b8b-177">Para mascarar informações em cartões adaptativos, adicione a `isMasked` propriedade ao **tipo** `Input.Text` e defina seu valor como *verdadeiro*.</span><span class="sxs-lookup"><span data-stu-id="05b8b-177">To mask information in Adaptive cards, add the `isMasked` property to **type** `Input.Text`, and set its value to *true*.</span></span>

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="05b8b-178">Cartão adaptável de amostra com propriedade de mascaramento</span><span class="sxs-lookup"><span data-stu-id="05b8b-178">Sample Adaptive card with masking property</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
    "isMasked": true
  },
```

<span data-ttu-id="05b8b-179">A imagem a seguir é um exemplo de mascarar informações em cartões adaptativos:</span><span class="sxs-lookup"><span data-stu-id="05b8b-179">The following image is an example of masking information in Adaptive cards:</span></span>

![Mascarando imagens de informações](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="05b8b-181">Placa adaptativa de largura completa</span><span class="sxs-lookup"><span data-stu-id="05b8b-181">Full width Adaptive card</span></span>
<span data-ttu-id="05b8b-182">Você pode usar a `msteams` propriedade para expandir a largura de uma placa Adaptive e fazer uso de espaço adicional de lona.</span><span class="sxs-lookup"><span data-stu-id="05b8b-182">You can use the `msteams` property to expand the width of an Adaptive card and make use of additional canvas space.</span></span> <span data-ttu-id="05b8b-183">Para obter informações sobre como usar o imóvel, consulte o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="05b8b-183">For information on how to use the property, see the following example:</span></span>

#### <a name="constructing-full-width-cards"></a><span data-ttu-id="05b8b-184">Construindo cartões de largura total</span><span class="sxs-lookup"><span data-stu-id="05b8b-184">Constructing full width cards</span></span>
<span data-ttu-id="05b8b-185">Para fazer uma placa adaptativa de largura total, o `width` objeto em propriedade no conteúdo do cartão deve ser definido para `msteams` `Full` .</span><span class="sxs-lookup"><span data-stu-id="05b8b-185">To make a full width Adaptive card the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>
<span data-ttu-id="05b8b-186">Além disso, seu aplicativo deve incluir os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="05b8b-186">In addition, your app must include the following elements:</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="05b8b-187">Cartão adaptativo de amostra com largura total</span><span class="sxs-lookup"><span data-stu-id="05b8b-187">Sample adaptive card with full width</span></span>

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

<span data-ttu-id="05b8b-188">Uma placa adaptativa de largura total aparece da seguinte forma: ![ Visão de cartão adaptativo de largura total](../../assets/images/cards/full-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="05b8b-188">A full width Adaptive Card appears as follows: ![Full width Adaptive Card view](../../assets/images/cards/full-width-adaptive-card.png)</span></span>

<span data-ttu-id="05b8b-189">Se você não tiver definido a `width` propriedade como *Full,* então a exibição padrão da Placa Adaptativa é a seguinte: ![ Exibição de cartão adaptativo de pequena largura](../../assets/images/cards/small-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="05b8b-189">If you have not set the `width` property to *Full*, then the default view of the Adaptive Card is as follows: ![Small width Adaptive Card view](../../assets/images/cards/small-width-adaptive-card.png)</span></span>

### <a name="typeahead-support"></a><span data-ttu-id="05b8b-190">Suporte tipoahead</span><span class="sxs-lookup"><span data-stu-id="05b8b-190">Typeahead support</span></span>

<span data-ttu-id="05b8b-191">Dentro do [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) elemento esquema, pedir aos usuários que filtram e selecionem através de um número considerável de opções pode retardar significativamente a conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="05b8b-191">Within the [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) schema element, asking users to filter through and select through a sizable number of choices can significantly slow down task completion.</span></span> <span data-ttu-id="05b8b-192">O suporte tipo-cabeça dentro de cartões Adaptive pode simplificar a seleção de entrada, estreitando ou filtrando o conjunto de opções de entrada à medida que um usuário está digitando a entrada.</span><span class="sxs-lookup"><span data-stu-id="05b8b-192">Typeahead support within Adaptive cards can simplify input selection by narrowing or filtering the set of input choices as a user is typing the input.</span></span> 

#### <a name="enable-typeahead-in-adaptive-cards"></a><span data-ttu-id="05b8b-193">Habilitar typeahead em cartões adaptativos</span><span class="sxs-lookup"><span data-stu-id="05b8b-193">Enable typeahead in Adaptive cards</span></span>

<span data-ttu-id="05b8b-194">Para habilitar a cabeça de digitar dentro do `Input.Choiceset` conjunto para e garantir que seja definido para `style` `filtered` `isMultiSelect` `false` .</span><span class="sxs-lookup"><span data-stu-id="05b8b-194">To enable typeahead within the `Input.Choiceset` set `style` to `filtered` and ensure `isMultiSelect` is set to `false`.</span></span> 

#### <a name="sample-adaptive-card-with-typeahead-support"></a><span data-ttu-id="05b8b-195">Cartão adaptativo de amostra com suporte de cabeça de digitar</span><span class="sxs-lookup"><span data-stu-id="05b8b-195">Sample adaptive card with typeahead support</span></span>

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

### <a name="stage-view-for-images-in-adaptive-cards"></a><span data-ttu-id="05b8b-196">Exibição de palco para imagens em Cartões Adaptativos</span><span class="sxs-lookup"><span data-stu-id="05b8b-196">Stage view for images in Adaptive Cards</span></span>

> [!NOTE]
> <span data-ttu-id="05b8b-197">Este recurso está atualmente disponível apenas na pré-visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="05b8b-197">This feature is currently available in developer preview only.</span></span>
 
<span data-ttu-id="05b8b-198">Em uma placa Adaptativa, você pode usar a `msteams` propriedade para adicionar a capacidade de exibir imagens na visualização do palco seletivamente.</span><span class="sxs-lookup"><span data-stu-id="05b8b-198">In an Adaptive card, you can use the `msteams` property to add the ability to display images in stage view selectively.</span></span> <span data-ttu-id="05b8b-199">Quando os usuários pairam sobre as imagens, eles veriam um ícone de expansão, para o qual o `allowExpand` atributo é definido `true` .</span><span class="sxs-lookup"><span data-stu-id="05b8b-199">When users hover over the images, they would see an expand icon, for which the `allowExpand` attribute is set to `true`.</span></span> <span data-ttu-id="05b8b-200">Para obter informações sobre como usar o imóvel, consulte o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="05b8b-200">For information on how to use the property, see the following example:</span></span>

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

<span data-ttu-id="05b8b-201">Quando os usuários pairam sobre a imagem, um ícone de expansão aparece no canto superior direito da imagem: ![ Cartão adaptativo com imagem expansível](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span><span class="sxs-lookup"><span data-stu-id="05b8b-201">When users hover over the image, an expand icon appears at top right corner of the image: ![Adaptive card with expandable image](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span></span>

<span data-ttu-id="05b8b-202">A imagem aparece na visualização do palco quando o usuário seleciona o botão expandir: ![ Imagem expandida para exibição de palco](../../assets/images/cards/adaptivecard-expand-image.png)</span><span class="sxs-lookup"><span data-stu-id="05b8b-202">The image appears in stage view when the user selects the expand button: ![Image expanded to stage view](../../assets/images/cards/adaptivecard-expand-image.png)</span></span>

<span data-ttu-id="05b8b-203">Na visualização do palco, os usuários podem ampliar e diminuir o zoom da imagem.</span><span class="sxs-lookup"><span data-stu-id="05b8b-203">In the stage view, users can zoom in and zoom out of the image.</span></span> <span data-ttu-id="05b8b-204">Você pode selecionar quais imagens em sua placa Adaptive precisam ter esse recurso.</span><span class="sxs-lookup"><span data-stu-id="05b8b-204">You can select which images in your Adaptive card needs to have this capability.</span></span>

> [!NOTE]
> <span data-ttu-id="05b8b-205">O recurso de zoom e zoom out se aplica apenas aos elementos de imagem (tipo de imagem) em uma placa Adaptive.</span><span class="sxs-lookup"><span data-stu-id="05b8b-205">Zoom in and zoom out capability applies only to the image elements (Image type) in an Adaptive card.</span></span>

> [!NOTE]
> <span data-ttu-id="05b8b-206">Para Teams aplicativos móveis, a funcionalidade de visualização de palco para imagens em Cartões Adaptativos está disponível por padrão e os usuários poderão visualizar imagens de placas adaptativas na visualização do palco simplesmente tocando na imagem, independentemente de o `allowExpand` atributo estar presente ou não.</span><span class="sxs-lookup"><span data-stu-id="05b8b-206">For Teams mobile apps, stage view functionality for images in Adaptive Cards are available by default and users will be able to view Adaptive card images in stage view by simply tapping on the image, irrespective of whether the `allowExpand` attribute is present or not.</span></span>

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="05b8b-207">**Formatação de markdown: Placas conectoras O365**</span><span class="sxs-lookup"><span data-stu-id="05b8b-207">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="05b8b-208">As placas conectoras suportam formatação limitada de Markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="05b8b-208">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="05b8b-209">O suporte html é descrito na última seção.</span><span class="sxs-lookup"><span data-stu-id="05b8b-209">HTML support is described in the last section.</span></span>

| <span data-ttu-id="05b8b-210">Style</span><span class="sxs-lookup"><span data-stu-id="05b8b-210">Style</span></span> | <span data-ttu-id="05b8b-211">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05b8b-211">Example</span></span> | <span data-ttu-id="05b8b-212">Markdown</span><span class="sxs-lookup"><span data-stu-id="05b8b-212">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="05b8b-213">bold</span><span class="sxs-lookup"><span data-stu-id="05b8b-213">bold</span></span> | <span data-ttu-id="05b8b-214">**text**</span><span class="sxs-lookup"><span data-stu-id="05b8b-214">**text**</span></span> | `**text**` |
| <span data-ttu-id="05b8b-215">italic</span><span class="sxs-lookup"><span data-stu-id="05b8b-215">italic</span></span> | <span data-ttu-id="05b8b-216">*text*</span><span class="sxs-lookup"><span data-stu-id="05b8b-216">*text*</span></span> | `*text*` |
| <span data-ttu-id="05b8b-217">cabeçalho (níveis &ndash; 13)</span><span class="sxs-lookup"><span data-stu-id="05b8b-217">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="05b8b-218">**Texto**</span><span class="sxs-lookup"><span data-stu-id="05b8b-218">**Text**</span></span> | `### Text`|
| <span data-ttu-id="05b8b-219">strikethrough</span><span class="sxs-lookup"><span data-stu-id="05b8b-219">strikethrough</span></span> | <span data-ttu-id="05b8b-220">~~text~~</span><span class="sxs-lookup"><span data-stu-id="05b8b-220">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="05b8b-221">lista não rdenada</span><span class="sxs-lookup"><span data-stu-id="05b8b-221">unordered list</span></span> | <ul><li><span data-ttu-id="05b8b-222">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-222">text</span></span></li><li><span data-ttu-id="05b8b-223">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-223">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="05b8b-224">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="05b8b-224">ordered list</span></span> | <ol><li><span data-ttu-id="05b8b-225">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-225">text</span></span></li><li><span data-ttu-id="05b8b-226">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-226">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="05b8b-227">texto pré-formado</span><span class="sxs-lookup"><span data-stu-id="05b8b-227">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="05b8b-228">blockquote</span><span class="sxs-lookup"><span data-stu-id="05b8b-228">blockquote</span></span> | <span data-ttu-id="05b8b-229">>texto de cota de bloqueio</span><span class="sxs-lookup"><span data-stu-id="05b8b-229">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="05b8b-230">hiperlink</span><span class="sxs-lookup"><span data-stu-id="05b8b-230">hyperlink</span></span> | [<span data-ttu-id="05b8b-231">Bing</span><span class="sxs-lookup"><span data-stu-id="05b8b-231">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="05b8b-232">link de imagem</span><span class="sxs-lookup"><span data-stu-id="05b8b-232">image link</span></span> |![Pato em uma pedra](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="05b8b-234">Em cartões conectores, novas linhas são renderizadas para `\n\n` , mas não para ou `\n` `\r` .</span><span class="sxs-lookup"><span data-stu-id="05b8b-234">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="05b8b-235">Diferenças móveis e desktop para cartões conectores usando Markdown</span><span class="sxs-lookup"><span data-stu-id="05b8b-235">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="05b8b-236">No desktop, a formatação do Markdown para placas conectoras é assim:</span><span class="sxs-lookup"><span data-stu-id="05b8b-236">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Formatação de marcação para cartões conectores no cliente Desktop](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="05b8b-238">No iOS, a formatação do Markdown para placas conectoras é assim:</span><span class="sxs-lookup"><span data-stu-id="05b8b-238">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Formatação de marcação para cartões conectores no cliente iOS](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="05b8b-240">Questões:</span><span class="sxs-lookup"><span data-stu-id="05b8b-240">Issues:</span></span>

* <span data-ttu-id="05b8b-241">O cliente iOS para Teams não renderiza imagens em linha de Markdown ou HTML em Placas Conectoras.</span><span class="sxs-lookup"><span data-stu-id="05b8b-241">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="05b8b-242">As cotas de bloqueio são renderizadas como recuadas, mas sem fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="05b8b-242">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="05b8b-243">No Android, a formatação do Markdown para placas conectoras é assim:</span><span class="sxs-lookup"><span data-stu-id="05b8b-243">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Formatação de markdown para cartões conectores no cliente Android](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="05b8b-245">Formatação exemplo para cartões conectores markdown</span><span class="sxs-lookup"><span data-stu-id="05b8b-245">Formatting example for Markdown Connector Cards</span></span>

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

## <a name="formatting-cards-with-html"></a><span data-ttu-id="05b8b-246">Cartões de formatação com HTML</span><span class="sxs-lookup"><span data-stu-id="05b8b-246">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="05b8b-247">**Formatação HTML: Placas conectoras O365**</span><span class="sxs-lookup"><span data-stu-id="05b8b-247">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="05b8b-248">As placas conectoras suportam formatação limitada de Markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="05b8b-248">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="05b8b-249">Markdown é descrito na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="05b8b-249">Markdown is described in the next section.</span></span>

| <span data-ttu-id="05b8b-250">Style</span><span class="sxs-lookup"><span data-stu-id="05b8b-250">Style</span></span> | <span data-ttu-id="05b8b-251">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05b8b-251">Example</span></span> | <span data-ttu-id="05b8b-252">HTML</span><span class="sxs-lookup"><span data-stu-id="05b8b-252">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="05b8b-253">bold</span><span class="sxs-lookup"><span data-stu-id="05b8b-253">bold</span></span> | <span data-ttu-id="05b8b-254">**text**</span><span class="sxs-lookup"><span data-stu-id="05b8b-254">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="05b8b-255">italic</span><span class="sxs-lookup"><span data-stu-id="05b8b-255">italic</span></span> | <span data-ttu-id="05b8b-256">*text*</span><span class="sxs-lookup"><span data-stu-id="05b8b-256">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="05b8b-257">cabeçalho (níveis &ndash; 13)</span><span class="sxs-lookup"><span data-stu-id="05b8b-257">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="05b8b-258">**Texto**</span><span class="sxs-lookup"><span data-stu-id="05b8b-258">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="05b8b-259">strikethrough</span><span class="sxs-lookup"><span data-stu-id="05b8b-259">strikethrough</span></span> | <span data-ttu-id="05b8b-260">~~text~~</span><span class="sxs-lookup"><span data-stu-id="05b8b-260">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="05b8b-261">lista não rdenada</span><span class="sxs-lookup"><span data-stu-id="05b8b-261">unordered list</span></span> | <ul><li><span data-ttu-id="05b8b-262">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-262">text</span></span></li><li><span data-ttu-id="05b8b-263">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-263">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="05b8b-264">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="05b8b-264">ordered list</span></span> | <ol><li><span data-ttu-id="05b8b-265">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-265">text</span></span></li><li><span data-ttu-id="05b8b-266">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-266">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="05b8b-267">texto pré-formado</span><span class="sxs-lookup"><span data-stu-id="05b8b-267">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="05b8b-268">blockquote</span><span class="sxs-lookup"><span data-stu-id="05b8b-268">blockquote</span></span> | <blockquote><span data-ttu-id="05b8b-269">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-269">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="05b8b-270">hiperlink</span><span class="sxs-lookup"><span data-stu-id="05b8b-270">hyperlink</span></span> | [<span data-ttu-id="05b8b-271">Bing</span><span class="sxs-lookup"><span data-stu-id="05b8b-271">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="05b8b-272">link de imagem</span><span class="sxs-lookup"><span data-stu-id="05b8b-272">image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="05b8b-273">Nas placas de conector, as linhas novas são renderizadas em HTML usando a `<p>` tag.</span><span class="sxs-lookup"><span data-stu-id="05b8b-273">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="05b8b-274">Diferenças móveis e desktop para placas conectoras usando HTML</span><span class="sxs-lookup"><span data-stu-id="05b8b-274">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="05b8b-275">Na área de trabalho, a formatação HTML para placas conectoras é assim:</span><span class="sxs-lookup"><span data-stu-id="05b8b-275">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![Formatação HTML para cartões conectores no cliente Desktop](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="05b8b-277">No iOS, a formatação HTML é assim:</span><span class="sxs-lookup"><span data-stu-id="05b8b-277">On iOS, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões conectores no cliente iOS](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="05b8b-279">Questões:</span><span class="sxs-lookup"><span data-stu-id="05b8b-279">Issues:</span></span>

* <span data-ttu-id="05b8b-280">As imagens inline não são renderizadas no iOS usando markdown ou HTML em placas conectoras.</span><span class="sxs-lookup"><span data-stu-id="05b8b-280">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="05b8b-281">O texto pré-formado é renderizado, mas não tem um fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="05b8b-281">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="05b8b-282">No Android, a formatação HTML se parece com isso:</span><span class="sxs-lookup"><span data-stu-id="05b8b-282">On Android, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões conectores no cliente Android](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="05b8b-284">Amostra de formatação para placas de conector HTML</span><span class="sxs-lookup"><span data-stu-id="05b8b-284">Formatting sample for HTML Connector Cards</span></span>

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="05b8b-285">**Formatação HTML: cartões de herói e miniatura**</span><span class="sxs-lookup"><span data-stu-id="05b8b-285">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="05b8b-286">As tags HTML são suportadas para cartões simples, como o hero e a placa de miniatura.</span><span class="sxs-lookup"><span data-stu-id="05b8b-286">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="05b8b-287">Markdown não é apoiado.</span><span class="sxs-lookup"><span data-stu-id="05b8b-287">Markdown is not supported.</span></span>

| <span data-ttu-id="05b8b-288">Style</span><span class="sxs-lookup"><span data-stu-id="05b8b-288">Style</span></span> | <span data-ttu-id="05b8b-289">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05b8b-289">Example</span></span> | <span data-ttu-id="05b8b-290">HTML</span><span class="sxs-lookup"><span data-stu-id="05b8b-290">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="05b8b-291">bold</span><span class="sxs-lookup"><span data-stu-id="05b8b-291">bold</span></span> | <span data-ttu-id="05b8b-292">**text**</span><span class="sxs-lookup"><span data-stu-id="05b8b-292">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="05b8b-293">italic</span><span class="sxs-lookup"><span data-stu-id="05b8b-293">italic</span></span> | <span data-ttu-id="05b8b-294">*text*</span><span class="sxs-lookup"><span data-stu-id="05b8b-294">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="05b8b-295">cabeçalho (níveis &ndash; 13)</span><span class="sxs-lookup"><span data-stu-id="05b8b-295">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="05b8b-296">**Texto**</span><span class="sxs-lookup"><span data-stu-id="05b8b-296">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="05b8b-297">strikethrough</span><span class="sxs-lookup"><span data-stu-id="05b8b-297">strikethrough</span></span> | <span data-ttu-id="05b8b-298">~~text~~</span><span class="sxs-lookup"><span data-stu-id="05b8b-298">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="05b8b-299">lista não rdenada</span><span class="sxs-lookup"><span data-stu-id="05b8b-299">unordered list</span></span> | <ul><li><span data-ttu-id="05b8b-300">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-300">text</span></span></li><li><span data-ttu-id="05b8b-301">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-301">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="05b8b-302">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="05b8b-302">ordered list</span></span> | <ol><li><span data-ttu-id="05b8b-303">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-303">text</span></span></li><li><span data-ttu-id="05b8b-304">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-304">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="05b8b-305">texto pré-formado</span><span class="sxs-lookup"><span data-stu-id="05b8b-305">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="05b8b-306">blockquote</span><span class="sxs-lookup"><span data-stu-id="05b8b-306">blockquote</span></span> | <blockquote><span data-ttu-id="05b8b-307">texto</span><span class="sxs-lookup"><span data-stu-id="05b8b-307">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="05b8b-308">hiperlink</span><span class="sxs-lookup"><span data-stu-id="05b8b-308">hyperlink</span></span> | [<span data-ttu-id="05b8b-309">Bing</span><span class="sxs-lookup"><span data-stu-id="05b8b-309">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="05b8b-310">link de imagem</span><span class="sxs-lookup"><span data-stu-id="05b8b-310">image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="05b8b-311">Diferenças móveis e desktop para cartões simples</span><span class="sxs-lookup"><span data-stu-id="05b8b-311">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="05b8b-312">Devido às diferenças de resolução entre a plataforma desktop e mobile, a formatação é diferente entre o desktop e a versão móvel de Teams.</span><span class="sxs-lookup"><span data-stu-id="05b8b-312">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="05b8b-313">No desktop, a formatação HTML aparece assim:</span><span class="sxs-lookup"><span data-stu-id="05b8b-313">On the desktop, HTML formatting appears like this:</span></span>

![Formatação html no cliente Desktop](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="05b8b-315">No iOS, a formatação HTML aparece assim:</span><span class="sxs-lookup"><span data-stu-id="05b8b-315">On iOS, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente iOS](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="05b8b-317">Questões:</span><span class="sxs-lookup"><span data-stu-id="05b8b-317">Issues:</span></span>

* <span data-ttu-id="05b8b-318">A formatação de caracteres como negrito e itálico não são renderizadas no iOS.</span><span class="sxs-lookup"><span data-stu-id="05b8b-318">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="05b8b-319">No Android, a formatação HTML aparece assim:</span><span class="sxs-lookup"><span data-stu-id="05b8b-319">On Android, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente Android](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="05b8b-321">Formatação de caracteres como exibição em negrito e itálico corretamente no Android.</span><span class="sxs-lookup"><span data-stu-id="05b8b-321">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="05b8b-322">Amostra de formatação para formatação HTML em cartões simples</span><span class="sxs-lookup"><span data-stu-id="05b8b-322">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="05b8b-323">Essas capturas de tela foram criadas usando Teams AppStudio, onde a propriedade de texto de um cartão herói foi definida para a sequência seguinte.</span><span class="sxs-lookup"><span data-stu-id="05b8b-323">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="05b8b-324">Você pode testar a formatação em seus próprios cartões modificando este código.</span><span class="sxs-lookup"><span data-stu-id="05b8b-324">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
