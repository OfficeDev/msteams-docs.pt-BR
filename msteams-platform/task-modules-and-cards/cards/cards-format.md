---
title: Formatação de texto em cartões
description: Descreve a formatação de texto do cartão em Microsoft Teams
keywords: formato de cartões de bots do teams
localization_priority: Normal
ms.topic: reference
ms.date: 03/29/2018
ms.openlocfilehash: 877a16f884e91138dc656434438a5fe1dd2ffd6e
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140581"
---
# <a name="format-cards-in-microsoft-teams"></a><span data-ttu-id="96279-104">Formatar cartões em Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="96279-104">Format cards in Microsoft Teams</span></span>

<span data-ttu-id="96279-105">A seguir estão as duas maneiras de adicionar formatação de texto rich aos cartões:</span><span class="sxs-lookup"><span data-stu-id="96279-105">Following are the two ways to add rich text formatting to your cards:</span></span>
* [<span data-ttu-id="96279-106">Markdown</span><span class="sxs-lookup"><span data-stu-id="96279-106">Markdown</span></span>](#format-cards-with-markdown)
* [<span data-ttu-id="96279-107">HTML</span><span class="sxs-lookup"><span data-stu-id="96279-107">HTML</span></span>](#format-cards-with-html)

<span data-ttu-id="96279-108">Os cartões suportam formatação somente na propriedade text, não nas propriedades title ou subtitle.</span><span class="sxs-lookup"><span data-stu-id="96279-108">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="96279-109">A formatação pode ser especificada usando um subconjunto de formatação XML ou HTML ou Markdown, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="96279-109">Formatting can be specified using a subset of XML or HTML formatting or Markdown, depending on the card type.</span></span> <span data-ttu-id="96279-110">Para o desenvolvimento atual e futuro de Cartões Adaptáveis, a formatação markdown é recomendada.</span><span class="sxs-lookup"><span data-stu-id="96279-110">For current and future development of Adaptive Cards, Markdown formatting is recommended.</span></span>

<span data-ttu-id="96279-111">O suporte à formatação difere entre tipos de cartão.</span><span class="sxs-lookup"><span data-stu-id="96279-111">Formatting support differs between card types.</span></span> <span data-ttu-id="96279-112">A renderização do cartão pode diferir ligeiramente entre a área de trabalho e os clientes de Microsoft Teams móveis, bem como Teams no navegador da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="96279-112">Rendering of the card can differ slightly between the desktop and the mobile Microsoft Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="96279-113">Você pode incluir uma imagem em linha com qualquer Teams cartão.</span><span class="sxs-lookup"><span data-stu-id="96279-113">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="96279-114">As imagens podem ser formatadas como , ou arquivos e não devem exceder `.png` `.jpg` `.gif` 1024 ×1024 px ou 1 MB.</span><span class="sxs-lookup"><span data-stu-id="96279-114">Images can be formatted as `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="96279-115">Gif animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="96279-115">Animated GIF is not supported.</span></span> <span data-ttu-id="96279-116">Para obter mais informações, consulte [tipos de cartões](./cards-reference.md#inline-card-images).</span><span class="sxs-lookup"><span data-stu-id="96279-116">For more information, see [types of cards](./cards-reference.md#inline-card-images).</span></span>

<span data-ttu-id="96279-117">Você pode formatar cartões adaptáveis e Office 365 conector com Markdown que incluem determinados estilos com suporte.</span><span class="sxs-lookup"><span data-stu-id="96279-117">You can format Adaptive Cards and Office 365 Connector cards with Markdown that include certain supported styles.</span></span>

## <a name="format-cards-with-markdown"></a><span data-ttu-id="96279-118">Formatar cartões com Markdown</span><span class="sxs-lookup"><span data-stu-id="96279-118">Format cards with Markdown</span></span>

<span data-ttu-id="96279-119">Os seguintes tipos de cartão suportam a formatação markdown Teams:</span><span class="sxs-lookup"><span data-stu-id="96279-119">The following card types support Markdown formatting in Teams:</span></span>

* <span data-ttu-id="96279-120">Cartões Adaptáveis: a marcação é suportada no campo Cartão `Textblock` Adaptável, bem como e `Fact.Title` `Fact.Value` .</span><span class="sxs-lookup"><span data-stu-id="96279-120">Adaptive Cards: Markdown is supported in Adaptive Card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="96279-121">HTML não é suportado em Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="96279-121">HTML is not supported in Adaptive Cards.</span></span>
* <span data-ttu-id="96279-122">Cartões do conector O365: Markdown e HTML limitado são suportados em cartões conectores O365 nos campos de texto.</span><span class="sxs-lookup"><span data-stu-id="96279-122">O365 Connector cards: Markdown and limited HTML is supported in O365 Connector cards in the text fields.</span></span>

<span data-ttu-id="96279-123">Você pode usar linhas novas para Cartões Adaptáveis usando ou sequências de escape `\r` para linhas novas em `\n` listas.</span><span class="sxs-lookup"><span data-stu-id="96279-123">You can use newlines for Adaptive Cards using `\r` or `\n` escape sequences for newlines in lists.</span></span> <span data-ttu-id="96279-124">A formatação é diferente entre a área de trabalho e as versões móveis Teams para Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="96279-124">Formatting is different between the desktop and the mobile versions of Teams for Adaptive Cards.</span></span> <span data-ttu-id="96279-125">As menções baseadas em cartão são suportadas em clientes web, desktop e móveis.</span><span class="sxs-lookup"><span data-stu-id="96279-125">Card-based mentions are supported in web, desktop, and mobile clients.</span></span> <span data-ttu-id="96279-126">Você pode usar a propriedade de mascaramento de informações para mascarar informações específicas, como senha ou informações confidenciais de usuários dentro do elemento de entrada Cartão `Input.Text` Adaptável.</span><span class="sxs-lookup"><span data-stu-id="96279-126">You can use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive Card `Input.Text` input element.</span></span> <span data-ttu-id="96279-127">Você pode expandir a largura de um Cartão Adaptável usando o `width` objeto.</span><span class="sxs-lookup"><span data-stu-id="96279-127">You can expand the width of an Adaptive Card using the `width` object.</span></span> <span data-ttu-id="96279-128">Você pode habilitar o suporte typeahead em Cartões Adaptáveis e filtrar o conjunto de opções de entrada à medida que o usuário digita a entrada.</span><span class="sxs-lookup"><span data-stu-id="96279-128">You can enable typeahead support within Adaptive Cards and filter the set of input choices as the user types the input.</span></span> <span data-ttu-id="96279-129">Você pode usar a `msteams` propriedade para adicionar a capacidade de exibir imagens no exibição de estágio seletivamente.</span><span class="sxs-lookup"><span data-stu-id="96279-129">You can use the `msteams` property to add the ability to display images in stage view selectively.</span></span>

<span data-ttu-id="96279-130">A formatação é diferente entre a área de trabalho e as versões móveis do Teams para Cartões Adaptáveis e cartões de conector.</span><span class="sxs-lookup"><span data-stu-id="96279-130">Formatting is different between the desktop and the mobile versions of Teams for Adaptive Cards and connector cards.</span></span> <span data-ttu-id="96279-131">Nesta seção, você pode passar pelo exemplo de formato Markdown para Cartões Adaptáveis e cartões de conector.</span><span class="sxs-lookup"><span data-stu-id="96279-131">In this section, you can go through the Markdown format example for Adaptive Cards and connector cards.</span></span>

# <a name="markdown-format-for-adaptive-cards"></a>[<span data-ttu-id="96279-132">Formato de marcação para Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="96279-132">Markdown format for Adaptive Cards</span></span>](#tab/adaptive-md)

 <span data-ttu-id="96279-133">A tabela a seguir fornece os estilos com suporte `Textblock` para , `Fact.Title` e `Fact.Value` :</span><span class="sxs-lookup"><span data-stu-id="96279-133">The following table provides the supported styles for `Textblock`, `Fact.Title`, and `Fact.Value`:</span></span>

| <span data-ttu-id="96279-134">Style</span><span class="sxs-lookup"><span data-stu-id="96279-134">Style</span></span> | <span data-ttu-id="96279-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96279-135">Example</span></span> | <span data-ttu-id="96279-136">Markdown</span><span class="sxs-lookup"><span data-stu-id="96279-136">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="96279-137">Negrito</span><span class="sxs-lookup"><span data-stu-id="96279-137">Bold</span></span> | <span data-ttu-id="96279-138">**Negrito**</span><span class="sxs-lookup"><span data-stu-id="96279-138">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="96279-139">Itálico</span><span class="sxs-lookup"><span data-stu-id="96279-139">Italic</span></span> | <span data-ttu-id="96279-140">_Itálico_</span><span class="sxs-lookup"><span data-stu-id="96279-140">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="96279-141">Lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="96279-141">Unordered list</span></span> | <ul><li><span data-ttu-id="96279-142">texto</span><span class="sxs-lookup"><span data-stu-id="96279-142">text</span></span></li><li><span data-ttu-id="96279-143">texto</span><span class="sxs-lookup"><span data-stu-id="96279-143">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="96279-144">Lista ordenada</span><span class="sxs-lookup"><span data-stu-id="96279-144">Ordered list</span></span> | <ol><li><span data-ttu-id="96279-145">texto</span><span class="sxs-lookup"><span data-stu-id="96279-145">text</span></span></li><li><span data-ttu-id="96279-146">texto</span><span class="sxs-lookup"><span data-stu-id="96279-146">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="96279-147">Hiperlinks</span><span class="sxs-lookup"><span data-stu-id="96279-147">Hyperlinks</span></span> |[<span data-ttu-id="96279-148">Bing</span><span class="sxs-lookup"><span data-stu-id="96279-148">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="96279-149">As seguintes marcas Markdown não são suportadas:</span><span class="sxs-lookup"><span data-stu-id="96279-149">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="96279-150">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="96279-150">Headers</span></span>
* <span data-ttu-id="96279-151">Tabelas</span><span class="sxs-lookup"><span data-stu-id="96279-151">Tables</span></span>
* <span data-ttu-id="96279-152">Imagens</span><span class="sxs-lookup"><span data-stu-id="96279-152">Images</span></span>
* <span data-ttu-id="96279-153">Texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="96279-153">Preformatted text</span></span>
* <span data-ttu-id="96279-154">Blockquotes</span><span class="sxs-lookup"><span data-stu-id="96279-154">Blockquotes</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="96279-155">Linhas novas para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="96279-155">Newlines for Adaptive Cards</span></span>

<span data-ttu-id="96279-156">Você pode usar as `\r` sequências de `\n` escape ou para linhas novas em listas.</span><span class="sxs-lookup"><span data-stu-id="96279-156">You can use the `\r` or `\n` escape sequences for newlines in lists.</span></span> <span data-ttu-id="96279-157">O uso em listas faz com que o `\n\n` próximo elemento da lista seja recuado.</span><span class="sxs-lookup"><span data-stu-id="96279-157">Using `\n\n` in lists causes the next element in the list to be indented.</span></span> <span data-ttu-id="96279-158">Se você precisar de linhas novas em outro lugar no TextBlock, use `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="96279-158">If you require newlines elsewhere in the TextBlock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="96279-159">Diferenças de dispositivos móveis e de área de trabalho para Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="96279-159">Mobile and desktop differences for Adaptive Cards</span></span>

<span data-ttu-id="96279-160">Na área de trabalho, a formatação adaptável de Marcação de Cartão aparece como mostrado na imagem a seguir, tanto em navegadores da Web quanto no aplicativo cliente Teams cliente:</span><span class="sxs-lookup"><span data-stu-id="96279-160">On the desktop, Adaptive Card Markdown formatting appears as shown in the following image in both web browsers and in the Teams client application:</span></span>

![Formatação de Marcação de Cartão Adaptável no cliente da área de trabalho](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="96279-162">No iOS, a formatação adaptável de Marcação de Cartão aparece conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-162">On iOS, Adaptive Card Markdown formatting appears as shown in the following image:</span></span>

![Formatação de Marcação de Cartão Adaptável no iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="96279-164">No Android, a formatação adaptável de Marcação de Cartão aparece conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-164">On Android, Adaptive Card Markdown formatting appears as shown in the following image:</span></span>

![Formatação de Marcação de Cartão Adaptável no Android](../../assets/images/cards/Adaptive-markdown-Android.png)

<span data-ttu-id="96279-166">Para obter mais informações, consulte [recursos de texto em Cartões Adaptáveis](/adaptive-cards/create/textfeatures).</span><span class="sxs-lookup"><span data-stu-id="96279-166">For more information, see [text features in Adaptive Cards](/adaptive-cards/create/textfeatures).</span></span>

> [!NOTE]
> <span data-ttu-id="96279-167">Os recursos de data e localização mencionados nesta seção não são suportados Teams.</span><span class="sxs-lookup"><span data-stu-id="96279-167">The date and localization features mentioned in this section are not supported in Teams.</span></span>

### <a name="adaptive-cards-format-sample"></a><span data-ttu-id="96279-168">Exemplo de formato de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="96279-168">Adaptive Cards format sample</span></span>

<span data-ttu-id="96279-169">O código a seguir mostra um exemplo de formatação de Cartões Adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="96279-169">The following code shows an example of Adaptive Cards formatting:</span></span>

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

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="96279-170">Mencionar suporte em Cartões Adaptáveis v1.2</span><span class="sxs-lookup"><span data-stu-id="96279-170">Mention support within Adaptive Cards v1.2</span></span>

<span data-ttu-id="96279-171">Você pode adicionar @mentions em um corpo de Cartão Adaptável para bots e respostas de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="96279-171">You can add @mentions within an Adaptive Card body for bots and messaging extension responses.</span></span> <span data-ttu-id="96279-172">Para adicionar @mentions cartões, siga a mesma lógica de notificação e renderização das menções baseadas em mensagens em conversas de chat de canal [e grupo.](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions)</span><span class="sxs-lookup"><span data-stu-id="96279-172">To add @mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).</span></span>

<span data-ttu-id="96279-173">Bots e extensões de mensagens podem incluir menções no conteúdo do cartão nos [elementos TextBlock](https://adaptivecards.io/explorer/TextBlock.html) e [FactSet.](https://adaptivecards.io/explorer/FactSet.html)</span><span class="sxs-lookup"><span data-stu-id="96279-173">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="96279-174">[Atualmente,](https://adaptivecards.io/explorer/Media.html) os elementos de mídia não têm suporte em Cartões Adaptáveis v1.2 na plataforma Teams adaptável.</span><span class="sxs-lookup"><span data-stu-id="96279-174">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive Cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="96279-175">As menções de canal e equipe não são suportadas em mensagens bot.</span><span class="sxs-lookup"><span data-stu-id="96279-175">Channel and team mentions are not supported in bot messages.</span></span>

<span data-ttu-id="96279-176">Para incluir uma menção em um Cartão Adaptável, seu aplicativo precisa incluir os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="96279-176">To include a mention in an Adaptive Card, your app needs to include the following elements:</span></span>

* <span data-ttu-id="96279-177">`<at>username</at>` nos elementos do Cartão Adaptável com suporte.</span><span class="sxs-lookup"><span data-stu-id="96279-177">`<at>username</at>` in the supported Adaptive Card elements.</span></span>
* <span data-ttu-id="96279-178">O objeto dentro de uma propriedade no conteúdo do cartão inclui Teams ID do usuário que está `mention` `msteams` sendo mencionado.</span><span class="sxs-lookup"><span data-stu-id="96279-178">The `mention` object inside of an `msteams` property in the card content includes the Teams user ID of the user being mentioned.</span></span>
* <span data-ttu-id="96279-179">O `userId` é exclusivo da ID do bot e de um usuário específico.</span><span class="sxs-lookup"><span data-stu-id="96279-179">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="96279-180">Ele pode ser usado para @mention um usuário específico.</span><span class="sxs-lookup"><span data-stu-id="96279-180">It can be used to @mention a particular user.</span></span> <span data-ttu-id="96279-181">O `userId` pode ser recuperado usando uma das opções mencionadas em obter a [ID do usuário](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span><span class="sxs-lookup"><span data-stu-id="96279-181">The `userId` can be retrieved using one of the options mentioned in [get the user ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="96279-182">Cartão Adaptável de Exemplo com uma menção</span><span class="sxs-lookup"><span data-stu-id="96279-182">Sample Adaptive Card with a mention</span></span>

<span data-ttu-id="96279-183">O código a seguir mostra um exemplo de Cartão Adaptável com uma menção:</span><span class="sxs-lookup"><span data-stu-id="96279-183">The following code shows an example of Adaptive Card with a mention:</span></span>

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

### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="96279-184">Mascaramento de informações em Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="96279-184">Information masking in Adaptive Cards</span></span>

<span data-ttu-id="96279-185">Use a propriedade mascarar informações para mascarar informações específicas, como senha ou informações confidenciais de usuários dentro do elemento de entrada Cartão [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Adaptável.</span><span class="sxs-lookup"><span data-stu-id="96279-185">Use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive Card [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) input element.</span></span>

> [!NOTE]
> <span data-ttu-id="96279-186">O recurso só dá suporte ao mascaramento de informações do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="96279-186">The feature only supports client side information masking.</span></span> <span data-ttu-id="96279-187">O texto de entrada mascarada é enviado como texto claro para o endereço de ponto de extremidade HTTPS especificado durante a configuração [do bot.](../../build-your-first-app/build-bot.md#4-register-your-bot-endpoint)</span><span class="sxs-lookup"><span data-stu-id="96279-187">The masked input text is sent as clear text to the HTTPS endpoint address that was specified during [bot configuration](../../build-your-first-app/build-bot.md#4-register-your-bot-endpoint).</span></span>

<span data-ttu-id="96279-188">Para mascarar informações em Cartões Adaptáveis, adicione a propriedade para `isMasked` **digitar** e de definir seu valor `Input.Text` como **true**.</span><span class="sxs-lookup"><span data-stu-id="96279-188">To mask information in Adaptive Cards, add the `isMasked` property to **type** `Input.Text`, and set its value to **true**.</span></span>

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="96279-189">Cartão Adaptável de Exemplo com a propriedade mascaramento</span><span class="sxs-lookup"><span data-stu-id="96279-189">Sample Adaptive Card with masking property</span></span>

<span data-ttu-id="96279-190">O código a seguir mostra um exemplo de Cartão Adaptável com a propriedade mascaramento:</span><span class="sxs-lookup"><span data-stu-id="96279-190">The following code shows an example of Adaptive Card with masking property:</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
},
```

<span data-ttu-id="96279-191">A imagem a seguir é um exemplo de informações de mascaramento em Cartões Adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="96279-191">The following image is an example of masking information in Adaptive Cards:</span></span>

![Imagem de informações de mascaramento](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="96279-193">Cartão Adaptável de largura total</span><span class="sxs-lookup"><span data-stu-id="96279-193">Full width Adaptive Card</span></span>

<span data-ttu-id="96279-194">Você pode usar a `msteams` propriedade para expandir a largura de um Cartão Adaptável e usar espaço adicional de tela.</span><span class="sxs-lookup"><span data-stu-id="96279-194">You can use the `msteams` property to expand the width of an Adaptive Card and make use of additional canvas space.</span></span> <span data-ttu-id="96279-195">A próxima seção fornece informações sobre como usar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="96279-195">The next section provides information on how to use the property.</span></span>

#### <a name="construct-full-width-cards"></a><span data-ttu-id="96279-196">Construir cartões de largura total</span><span class="sxs-lookup"><span data-stu-id="96279-196">Construct full width cards</span></span>

<span data-ttu-id="96279-197">Para fazer um Cartão Adaptável de largura total, o objeto na propriedade no conteúdo do cartão deve `width` `msteams` ser definido como `Full` .</span><span class="sxs-lookup"><span data-stu-id="96279-197">To make a full width Adaptive Card, the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="96279-198">Cartão Adaptável de Exemplo com largura total</span><span class="sxs-lookup"><span data-stu-id="96279-198">Sample Adaptive Card with full width</span></span>

<span data-ttu-id="96279-199">Para fazer um Cartão Adaptável de largura total, seu aplicativo deve incluir os elementos do exemplo de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-199">To make a full width Adaptive Card, your app must include the elements from the following code sample:</span></span>

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

<span data-ttu-id="96279-200">A imagem a seguir mostra um Cartão Adaptável de largura total:</span><span class="sxs-lookup"><span data-stu-id="96279-200">The following image shows a full width Adaptive Card:</span></span>

![Exibição cartão adaptável de largura total](../../assets/images/cards/full-width-adaptive-card.png)

<span data-ttu-id="96279-202">A imagem a seguir mostra o modo de exibição padrão do Cartão Adaptável quando você não definiu a `width` propriedade como **Full**:</span><span class="sxs-lookup"><span data-stu-id="96279-202">The following image shows the default view of the Adaptive Card when you have not set the `width` property to **Full**:</span></span>

![Exibição cartão adaptável de largura pequena](../../assets/images/cards/small-width-adaptive-card.png)

### <a name="typeahead-support"></a><span data-ttu-id="96279-204">Suporte a Typeahead</span><span class="sxs-lookup"><span data-stu-id="96279-204">Typeahead support</span></span>

<span data-ttu-id="96279-205">Dentro do elemento de esquema, pedir que os usuários filtrem e selecionem um número considerável de opções podem reduzir significativamente a conclusão [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) da tarefa.</span><span class="sxs-lookup"><span data-stu-id="96279-205">Within the [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) schema element, asking users to filter and select a sizeable number of choices can significantly slow down task completion.</span></span> <span data-ttu-id="96279-206">O suporte typeahead em Cartões Adaptáveis pode simplificar a seleção de entrada restringindo ou filtrando o conjunto de opções de entrada à medida que o usuário digita a entrada.</span><span class="sxs-lookup"><span data-stu-id="96279-206">Typeahead support within Adaptive Cards can simplify input selection by narrowing or filtering the set of input choices as the user types the input.</span></span>

<span data-ttu-id="96279-207">Para habilitar typeahead no `Input.Choiceset` , definir como e garantir que está definido como `style` `filtered` `isMultiSelect` `false` .</span><span class="sxs-lookup"><span data-stu-id="96279-207">To enable typeahead within the `Input.Choiceset`, set `style` to `filtered` and ensure `isMultiSelect` is set to `false`.</span></span>

#### <a name="sample-adaptive-card-with-typeahead-support"></a><span data-ttu-id="96279-208">Cartão Adaptável de Exemplo com suporte a typeahead</span><span class="sxs-lookup"><span data-stu-id="96279-208">Sample Adaptive Card with typeahead support</span></span>

<span data-ttu-id="96279-209">O código a seguir mostra um exemplo de Cartão Adaptável com suporte a typeahead:</span><span class="sxs-lookup"><span data-stu-id="96279-209">The following code shows an example of Adaptive Card with typeahead support:</span></span>

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

### <a name="stage-view-for-images-in-adaptive-cards"></a><span data-ttu-id="96279-210">Exibição de estágio para imagens em Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="96279-210">Stage view for images in Adaptive Cards</span></span>

<span data-ttu-id="96279-211">Em um Cartão Adaptável, você pode usar a propriedade para adicionar a capacidade de exibir imagens na exibição `msteams` de estágio seletivamente.</span><span class="sxs-lookup"><span data-stu-id="96279-211">In an Adaptive Card, you can use the `msteams` property to add the ability to display images in stage view selectively.</span></span> <span data-ttu-id="96279-212">Quando os usuários pairam sobre as imagens, eles podem ver um ícone de expansão, para o qual o `allowExpand` atributo é definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="96279-212">When users hover over the images, they can see an expand icon, for which the `allowExpand` attribute is set to `true`.</span></span> <span data-ttu-id="96279-213">Para obter informações sobre como usar a propriedade, consulte o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-213">For information on how to use the property, see the following example:</span></span>

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

<span data-ttu-id="96279-214">Quando os usuários passar o mouse sobre a imagem, um ícone de expansão aparece no canto superior direito, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-214">When users hover over the image, an expand icon appears at the top right corner as shown in the following image:</span></span>

![Cartão Adaptável com imagem expansível](../../assets/images/cards/adaptivecard-hover-expand-icon.png)

<span data-ttu-id="96279-216">A imagem aparece no exibição de estágio quando o usuário seleciona o ícone de expansão, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-216">The image appears in stage view when the user selects the expand icon as shown in the following image:</span></span>

![Imagem expandida para exibição de estágio](../../assets/images/cards/adaptivecard-expand-image.png)

<span data-ttu-id="96279-218">Na exibição de estágio, os usuários podem ampliar e diminuir o zoom da imagem.</span><span class="sxs-lookup"><span data-stu-id="96279-218">In the stage view, users can zoom in and zoom out of the image.</span></span> <span data-ttu-id="96279-219">Você pode selecionar as imagens em seu Cartão Adaptável que devem ter esse recurso.</span><span class="sxs-lookup"><span data-stu-id="96279-219">You can select the images in your Adaptive Card that must have this capability.</span></span>

> [!NOTE]
> * <span data-ttu-id="96279-220">A funcionalidade de zoom e zoom só se aplica aos elementos de imagem que são tipo de imagem em um Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="96279-220">Zoom in and zoom out capability applies only to the image elements that is image type in an Adaptive Card.</span></span>
> * <span data-ttu-id="96279-221">Para Teams aplicativos móveis, a funcionalidade de exibição de estágio para imagens em Cartões Adaptáveis está disponível por padrão.</span><span class="sxs-lookup"><span data-stu-id="96279-221">For Teams mobile apps, stage view functionality for images in Adaptive Cards is available by default.</span></span> <span data-ttu-id="96279-222">Os usuários podem exibir imagens do Cartão Adaptável na exibição de estágio simplesmente tocando na imagem, independentemente de o `allowExpand` atributo estar presente ou não.</span><span class="sxs-lookup"><span data-stu-id="96279-222">Users can view Adaptive Card images in stage view by simply tapping on the image, irrespective of whether the `allowExpand` attribute is present or not.</span></span>

# <a name="markdown-format-for-o365-connector-cards"></a>[<span data-ttu-id="96279-223">Formato de marcação para cartões conectores O365</span><span class="sxs-lookup"><span data-stu-id="96279-223">Markdown format for O365 Connector cards</span></span>](#tab/connector-md)

<span data-ttu-id="96279-224">Os cartões conectores suportam a formatação limitada markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="96279-224">Connector cards support limited Markdown and HTML formatting.</span></span>

| <span data-ttu-id="96279-225">Style</span><span class="sxs-lookup"><span data-stu-id="96279-225">Style</span></span> | <span data-ttu-id="96279-226">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96279-226">Example</span></span> | <span data-ttu-id="96279-227">Markdown</span><span class="sxs-lookup"><span data-stu-id="96279-227">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="96279-228">Negrito</span><span class="sxs-lookup"><span data-stu-id="96279-228">Bold</span></span> | <span data-ttu-id="96279-229">**text**</span><span class="sxs-lookup"><span data-stu-id="96279-229">**text**</span></span> | `**text**` |
| <span data-ttu-id="96279-230">Itálico</span><span class="sxs-lookup"><span data-stu-id="96279-230">Italic</span></span> | <span data-ttu-id="96279-231">*text*</span><span class="sxs-lookup"><span data-stu-id="96279-231">*text*</span></span> | `*text*` |
| <span data-ttu-id="96279-232">Header (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="96279-232">Header (levels 1&ndash;3)</span></span> | <span data-ttu-id="96279-233">**Texto**</span><span class="sxs-lookup"><span data-stu-id="96279-233">**Text**</span></span> | `### Text`|
| <span data-ttu-id="96279-234">Tachado</span><span class="sxs-lookup"><span data-stu-id="96279-234">Strikethrough</span></span> | <span data-ttu-id="96279-235">~~text~~</span><span class="sxs-lookup"><span data-stu-id="96279-235">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="96279-236">Lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="96279-236">Unordered list</span></span> | <ul><li><span data-ttu-id="96279-237">texto</span><span class="sxs-lookup"><span data-stu-id="96279-237">text</span></span></li><li><span data-ttu-id="96279-238">texto</span><span class="sxs-lookup"><span data-stu-id="96279-238">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="96279-239">Lista ordenada</span><span class="sxs-lookup"><span data-stu-id="96279-239">Ordered list</span></span> | <ol><li><span data-ttu-id="96279-240">texto</span><span class="sxs-lookup"><span data-stu-id="96279-240">text</span></span></li><li><span data-ttu-id="96279-241">texto</span><span class="sxs-lookup"><span data-stu-id="96279-241">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="96279-242">Texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="96279-242">Preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="96279-243">Blockquote</span><span class="sxs-lookup"><span data-stu-id="96279-243">Blockquote</span></span> | <span data-ttu-id="96279-244">>texto blockquote</span><span class="sxs-lookup"><span data-stu-id="96279-244">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="96279-245">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="96279-245">Hyperlink</span></span> | [<span data-ttu-id="96279-246">Bing</span><span class="sxs-lookup"><span data-stu-id="96279-246">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="96279-247">Link de imagem</span><span class="sxs-lookup"><span data-stu-id="96279-247">Image link</span></span> |![Duck on a rock](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="96279-249">Em cartões de conector, as linhas novas são renderizadas `\n\n` para , mas não para ou `\n` `\r` .</span><span class="sxs-lookup"><span data-stu-id="96279-249">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards"></a><span data-ttu-id="96279-250">Diferenças de dispositivos móveis e de área de trabalho para cartões de conector</span><span class="sxs-lookup"><span data-stu-id="96279-250">Mobile and desktop differences for connector cards</span></span>

<span data-ttu-id="96279-251">Na área de trabalho, a formatação markdown para cartões de conector aparece como mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-251">On the desktop, Markdown formatting for connector cards appears as shown in the following image:</span></span>

![Formatação de marcação para cartões conectores no cliente desktop](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="96279-253">No iOS, a formatação markdown para cartões de conector aparece conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-253">On iOS, Markdown formatting for connector cards appears as shown in the following image:</span></span>

![Formatação de marcação para cartões conectores no cliente iOS](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="96279-255">Os cartões conectores que usam Markdown para iOS incluem os seguintes problemas:</span><span class="sxs-lookup"><span data-stu-id="96279-255">Connector cards using Markdown for iOS include the following issues:</span></span>

* <span data-ttu-id="96279-256">O cliente iOS para Teams não renderiza imagens em linha Markdown ou HTML em cartões de conector.</span><span class="sxs-lookup"><span data-stu-id="96279-256">The iOS client for Teams does not render Markdown or HTML inline images in connector cards.</span></span>
* <span data-ttu-id="96279-257">As blockquotes são renderizadas como recuadas, mas sem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="96279-257">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="96279-258">No Android, a formatação markdown para cartões de conector aparece como mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-258">On Android, Markdown formatting for connector cards appears as shown in the following image:</span></span>

![Formatação de marcação para cartões conectores no cliente Android](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="format-example-for-markdown-connector-cards"></a><span data-ttu-id="96279-260">Exemplo de formato para cartões de conector Markdown</span><span class="sxs-lookup"><span data-stu-id="96279-260">Format example for Markdown connector cards</span></span>

<span data-ttu-id="96279-261">O código a seguir mostra um exemplo de formatação para cartões de conector Markdown:</span><span class="sxs-lookup"><span data-stu-id="96279-261">The following code shows an example of formatting for Markdown connector cards:</span></span>

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

## <a name="format-cards-with-html"></a><span data-ttu-id="96279-262">Formatar cartões com HTML</span><span class="sxs-lookup"><span data-stu-id="96279-262">Format cards with HTML</span></span>

<span data-ttu-id="96279-263">Os seguintes tipos de cartão suportam formatação HTML Teams:</span><span class="sxs-lookup"><span data-stu-id="96279-263">The following card types support HTML formatting in Teams:</span></span>

* <span data-ttu-id="96279-264">Cartões do conector O365: Marcação limitada e formatação HTML é suportada em cartões Office 365 Connector.</span><span class="sxs-lookup"><span data-stu-id="96279-264">O365 Connector cards: Limited Markdown and HTML formatting is supported in Office 365 Connector cards.</span></span>
* <span data-ttu-id="96279-265">Cartões de herói e miniatura: as marcas HTML são suportadas para cartões simples, como cartões de herói e miniatura.</span><span class="sxs-lookup"><span data-stu-id="96279-265">Hero and thumbnail cards: HTML tags are supported for simple cards, such as the hero and thumbnail cards.</span></span>

<span data-ttu-id="96279-266">A formatação é diferente entre a área de trabalho e as versões móveis do Teams para cartões conectores O365 e cartões simples.</span><span class="sxs-lookup"><span data-stu-id="96279-266">Formatting is different between the desktop and the mobile versions of Teams for O365 Connector cards and simple cards.</span></span> <span data-ttu-id="96279-267">Nesta seção, você pode passar pelo exemplo de formato HTML para cartões de conector e cartões simples.</span><span class="sxs-lookup"><span data-stu-id="96279-267">In this section, you can go through the HTML format example for connector cards and simple cards.</span></span>

# <a name="html-format-for-o365-connector-cards"></a>[<span data-ttu-id="96279-268">Formato HTML para cartões conectores O365</span><span class="sxs-lookup"><span data-stu-id="96279-268">HTML format for O365 Connector cards</span></span>](#tab/connector-html)

<span data-ttu-id="96279-269">Os cartões conectores suportam a formatação limitada markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="96279-269">Connector cards support limited Markdown and HTML formatting.</span></span>

| <span data-ttu-id="96279-270">Style</span><span class="sxs-lookup"><span data-stu-id="96279-270">Style</span></span> | <span data-ttu-id="96279-271">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96279-271">Example</span></span> | <span data-ttu-id="96279-272">HTML</span><span class="sxs-lookup"><span data-stu-id="96279-272">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="96279-273">Negrito</span><span class="sxs-lookup"><span data-stu-id="96279-273">Bold</span></span> | <span data-ttu-id="96279-274">**text**</span><span class="sxs-lookup"><span data-stu-id="96279-274">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="96279-275">Itálico</span><span class="sxs-lookup"><span data-stu-id="96279-275">Italic</span></span> | <span data-ttu-id="96279-276">*text*</span><span class="sxs-lookup"><span data-stu-id="96279-276">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="96279-277">Header (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="96279-277">Header (levels 1&ndash;3)</span></span> | <span data-ttu-id="96279-278">**Texto**</span><span class="sxs-lookup"><span data-stu-id="96279-278">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="96279-279">Tachado</span><span class="sxs-lookup"><span data-stu-id="96279-279">Strikethrough</span></span> | <span data-ttu-id="96279-280">~~text~~</span><span class="sxs-lookup"><span data-stu-id="96279-280">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="96279-281">Lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="96279-281">Unordered list</span></span> | <ul><li><span data-ttu-id="96279-282">texto</span><span class="sxs-lookup"><span data-stu-id="96279-282">text</span></span></li><li><span data-ttu-id="96279-283">texto</span><span class="sxs-lookup"><span data-stu-id="96279-283">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="96279-284">Lista ordenada</span><span class="sxs-lookup"><span data-stu-id="96279-284">Ordered list</span></span> | <ol><li><span data-ttu-id="96279-285">texto</span><span class="sxs-lookup"><span data-stu-id="96279-285">text</span></span></li><li><span data-ttu-id="96279-286">texto</span><span class="sxs-lookup"><span data-stu-id="96279-286">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="96279-287">Texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="96279-287">Preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="96279-288">Blockquote</span><span class="sxs-lookup"><span data-stu-id="96279-288">Blockquote</span></span> | <blockquote><span data-ttu-id="96279-289">texto</span><span class="sxs-lookup"><span data-stu-id="96279-289">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="96279-290">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="96279-290">Hyperlink</span></span> | [<span data-ttu-id="96279-291">Bing</span><span class="sxs-lookup"><span data-stu-id="96279-291">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="96279-292">Link de imagem</span><span class="sxs-lookup"><span data-stu-id="96279-292">Image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="96279-293">Em cartões de conector, as linhas novas são renderizadas em HTML usando a `<p>` marca.</span><span class="sxs-lookup"><span data-stu-id="96279-293">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards"></a><span data-ttu-id="96279-294">Diferenças de dispositivos móveis e de área de trabalho para cartões de conector</span><span class="sxs-lookup"><span data-stu-id="96279-294">Mobile and desktop differences for connector cards</span></span>

<span data-ttu-id="96279-295">Na área de trabalho, a formatação HTML para cartões de conector aparece como mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-295">On the desktop, HTML formatting for connector cards appears as shown in the following image:</span></span>

![Formatação HTML para cartões conectores no cliente da área de trabalho](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="96279-297">No iOS, a formatação HTML aparece conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-297">On iOS, HTML formatting appears as shown in the following image:</span></span>

![Formatação HTML para cartões de conector no cliente iOS](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="96279-299">Os cartões conectores que usam HTML para iOS incluem os seguintes problemas:</span><span class="sxs-lookup"><span data-stu-id="96279-299">Connector cards using HTML for iOS include the following issues:</span></span>

* <span data-ttu-id="96279-300">Imagens em linha não são renderizadas no iOS usando Markdown ou HTML em cartões de conector.</span><span class="sxs-lookup"><span data-stu-id="96279-300">Inline images are not rendered on iOS using either Markdown or HTML in connector cards.</span></span>
* <span data-ttu-id="96279-301">O texto pré-formatado é renderizado, mas não tem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="96279-301">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="96279-302">No Android, a formatação HTML aparece conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-302">On Android, HTML formatting appears as shown in the following image:</span></span>

![Formatação HTML para cartões de conector no cliente Android](../../assets/images/cards/connector-android-html-combined.png)

### <a name="format-sample-for-html-connector-cards"></a><span data-ttu-id="96279-304">Exemplo de formato para cartões de conector HTML</span><span class="sxs-lookup"><span data-stu-id="96279-304">Format sample for HTML connector cards</span></span>

<span data-ttu-id="96279-305">O código a seguir mostra um exemplo de formatação para cartões de conector HTML:</span><span class="sxs-lookup"><span data-stu-id="96279-305">The following code shows an example of formatting for HTML connector cards:</span></span>

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

# <a name="html-format-for-hero-and-thumbnail-cards"></a>[<span data-ttu-id="96279-306">Formato HTML para cartões de herói e miniatura</span><span class="sxs-lookup"><span data-stu-id="96279-306">HTML format for hero and thumbnail cards</span></span>](#tab/simple-html)

<span data-ttu-id="96279-307">As marcas HTML são suportadas para cartões simples, como cartões de herói e miniatura.</span><span class="sxs-lookup"><span data-stu-id="96279-307">HTML tags are supported for simple cards, such as the hero and thumbnail cards.</span></span> <span data-ttu-id="96279-308">Não há suporte para markdown.</span><span class="sxs-lookup"><span data-stu-id="96279-308">Markdown is not supported.</span></span>

| <span data-ttu-id="96279-309">Style</span><span class="sxs-lookup"><span data-stu-id="96279-309">Style</span></span> | <span data-ttu-id="96279-310">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96279-310">Example</span></span> | <span data-ttu-id="96279-311">HTML</span><span class="sxs-lookup"><span data-stu-id="96279-311">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="96279-312">Negrito</span><span class="sxs-lookup"><span data-stu-id="96279-312">Bold</span></span> | <span data-ttu-id="96279-313">**text**</span><span class="sxs-lookup"><span data-stu-id="96279-313">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="96279-314">Itálico</span><span class="sxs-lookup"><span data-stu-id="96279-314">Italic</span></span> | <span data-ttu-id="96279-315">*text*</span><span class="sxs-lookup"><span data-stu-id="96279-315">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="96279-316">Header (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="96279-316">Header (levels 1&ndash;3)</span></span> | <span data-ttu-id="96279-317">**Texto**</span><span class="sxs-lookup"><span data-stu-id="96279-317">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="96279-318">Tachado</span><span class="sxs-lookup"><span data-stu-id="96279-318">Strikethrough</span></span> | <span data-ttu-id="96279-319">~~text~~</span><span class="sxs-lookup"><span data-stu-id="96279-319">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="96279-320">Lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="96279-320">Unordered list</span></span> | <ul><li><span data-ttu-id="96279-321">texto</span><span class="sxs-lookup"><span data-stu-id="96279-321">text</span></span></li><li><span data-ttu-id="96279-322">texto</span><span class="sxs-lookup"><span data-stu-id="96279-322">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="96279-323">Lista ordenada</span><span class="sxs-lookup"><span data-stu-id="96279-323">Ordered list</span></span> | <ol><li><span data-ttu-id="96279-324">texto</span><span class="sxs-lookup"><span data-stu-id="96279-324">text</span></span></li><li><span data-ttu-id="96279-325">texto</span><span class="sxs-lookup"><span data-stu-id="96279-325">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="96279-326">Texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="96279-326">Preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="96279-327">Blockquote</span><span class="sxs-lookup"><span data-stu-id="96279-327">Blockquote</span></span> | <blockquote><span data-ttu-id="96279-328">texto</span><span class="sxs-lookup"><span data-stu-id="96279-328">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="96279-329">Hiperlink</span><span class="sxs-lookup"><span data-stu-id="96279-329">Hyperlink</span></span> | [<span data-ttu-id="96279-330">Bing</span><span class="sxs-lookup"><span data-stu-id="96279-330">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="96279-331">Link de imagem</span><span class="sxs-lookup"><span data-stu-id="96279-331">Image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="96279-332">Diferenças de dispositivos móveis e de área de trabalho para cartões simples</span><span class="sxs-lookup"><span data-stu-id="96279-332">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="96279-333">Como há diferenças de resolução entre a área de trabalho e a plataforma móvel, a formatação é diferente entre a área de trabalho e a versão móvel do Teams.</span><span class="sxs-lookup"><span data-stu-id="96279-333">As there are resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="96279-334">Na área de trabalho, a formatação HTML aparece conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-334">On the desktop, HTML formatting appears as shown in the following image:</span></span>

![Formatação HTML no cliente da área de trabalho](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="96279-336">No iOS, a formatação HTML aparece conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-336">On iOS, HTML formatting appears as shown in the following image:</span></span>

![Formatação HTML no cliente iOS](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="96279-338">A formatação de caracteres, como negrito e itálico, não é renderizada no iOS.</span><span class="sxs-lookup"><span data-stu-id="96279-338">Character formatting, such as bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="96279-339">No Android, a formatação HTML aparece conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96279-339">On Android, HTML formatting appears as shown in the following image:</span></span>

![Formatação HTML no cliente Android](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="96279-341">Formatação de caracteres, como negrito e exibição itálico corretamente no Android.</span><span class="sxs-lookup"><span data-stu-id="96279-341">Character formatting, such as bold and italic display correctly on Android.</span></span>

### <a name="format-example-for-simple-cards"></a><span data-ttu-id="96279-342">Exemplo de formato para cartões simples</span><span class="sxs-lookup"><span data-stu-id="96279-342">Format example for simple cards</span></span>

<span data-ttu-id="96279-343">As imagens na seção anterior foram criadas usando Teams **App Studio**, onde a propriedade de texto de um cartão de herói é definida como a seguinte cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="96279-343">The images in the previous section were created using Teams **App Studio**, where the text property of a hero card is set to the following string:</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

<span data-ttu-id="96279-344">Você pode testar a formatação em seus próprios cartões modificando esse código.</span><span class="sxs-lookup"><span data-stu-id="96279-344">You can test formatting in your own cards by modifying this code.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="96279-345">Também consulte</span><span class="sxs-lookup"><span data-stu-id="96279-345">See also</span></span>

* [<span data-ttu-id="96279-346">Ações de cartão</span><span class="sxs-lookup"><span data-stu-id="96279-346">Card actions</span></span>](./cards-actions.md)
* [<span data-ttu-id="96279-347">Módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="96279-347">Task modules</span></span>](~/task-modules-and-cards/cards/cards-format.md)
