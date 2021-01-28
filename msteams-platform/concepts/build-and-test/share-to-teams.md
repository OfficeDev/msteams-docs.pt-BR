---
title: Criar um botão compartilhar para o Teams
description: Como adicionar o botão Compartilhar ao Teams inserido em seu site
ms.topic: reference
keywords: Compartilhar o compartilhamento do Teams com o Teams
ms.openlocfilehash: 46091c957137cc871095ca6a57c0d61fa79d9458
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014331"
---
# <a name="create-a-share-to-teams-button-for-your-website"></a><span data-ttu-id="5d138-104">Criar um botão Compartilhar no Teams para o seu site</span><span class="sxs-lookup"><span data-stu-id="5d138-104">Create a Share-to-Teams button for your website</span></span>

>[!NOTE]
> * <span data-ttu-id="5d138-105">Há suporte apenas para as versões de área de trabalho do Edge e do Chrome.</span><span class="sxs-lookup"><span data-stu-id="5d138-105">Only the desktop versions of Edge and Chrome are supported.</span></span>
> * <span data-ttu-id="5d138-106">Não há suporte para o uso de contas de convidado ou Freemium.</span><span class="sxs-lookup"><span data-stu-id="5d138-106">Use of Freemium or guest accounts is not supported.</span></span>

<span data-ttu-id="5d138-107">Sites de terceiros podem usar o script do launcher para inserir botões de compartilhamento no Teams em suas páginas da Web, que iniciarão a experiência Compartilhar com o Teams em uma janela pop-up quando clicado.</span><span class="sxs-lookup"><span data-stu-id="5d138-107">Third-party websites can use the launcher script to embed Share to Teams buttons on their webpages which will launch the Share to Teams experience in a popup window when clicked.</span></span> <span data-ttu-id="5d138-108">Isso permitirá que você compartilhe um link diretamente com qualquer pessoa ou canal do Microsoft Teams sem alternar contexto.</span><span class="sxs-lookup"><span data-stu-id="5d138-108">This will allow you to share a link directly to any person or Microsoft Teams channel without switching context.</span></span>

![Compartilhar com o pop-up do Teams](~/assets/images/share-to-teams-popup.png)

## <a name="how-to-embed-a-share-to-teams-button"></a><span data-ttu-id="5d138-110">Como inserir um botão Compartilhar no Teams</span><span class="sxs-lookup"><span data-stu-id="5d138-110">How to embed a Share to Teams button</span></span>

<span data-ttu-id="5d138-111">Primeiro, você precisará adicionar o `launcher.js` script à sua página da Web.</span><span class="sxs-lookup"><span data-stu-id="5d138-111">First, you'll need to add the `launcher.js` script on your webpage.</span></span>

```html
<script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
```

<span data-ttu-id="5d138-112">Em seguida, adicione um elemento HTML à sua página da Web com o atributo de classe e `teams-share-button` o link para compartilhar no `data-href` atributo.</span><span class="sxs-lookup"><span data-stu-id="5d138-112">Next, add an HTML element on your webpage with the `teams-share-button` class attribute and the link to share in the `data-href` attribute.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>">
</div>
```

<span data-ttu-id="5d138-113">Isso adicionará o ícone do Microsoft Teams ao seu site.</span><span class="sxs-lookup"><span data-stu-id="5d138-113">This will add the Microsoft Teams icon to your website.</span></span>

![Ícone Compartilhar com o Teams](~/assets/icons/share-to-teams-icon.png)

<span data-ttu-id="5d138-115">Opcionalmente, se você quiser um tamanho de ícone diferente para o botão Compartilhar com o Teams, use o `data-icon-px-size` atributo.</span><span class="sxs-lookup"><span data-stu-id="5d138-115">Optionally, if you want a different icon size for the Share to Teams button, use the `data-icon-px-size` attribute.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-icon-px-size="64">
</div>
```

<span data-ttu-id="5d138-116">Se você sabe que a visualização da URL do seu link a ser compartilhada não renderizará bem no Teams (por exemplo, o link exigiria autenticação do usuário), você pode desabilitar a visualização da URL adicionando o atributo `data-preview` definido como `false` .</span><span class="sxs-lookup"><span data-stu-id="5d138-116">If you know that the URL preview from your link to be shared won't render well in Teams (for example the link would require user authentication) you can disable the URL preview by adding the `data-preview` attribute set to `false`.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-preview="false">
</div>
```

<span data-ttu-id="5d138-117">Se sua página renderizar dinamicamente o conteúdo, você poderá usar o método para forçar o botão Compartilhar a renderizar no `shareToMicrosoftTeams.renderButtons()` local apropriado no pipeline. </span><span class="sxs-lookup"><span data-stu-id="5d138-117">If your page dynamically renders content, you can use the the `shareToMicrosoftTeams.renderButtons()` method to force the **Share** button to render at the appropriate place in the pipeline.</span></span>

## <a name="crafting-your-website-preview"></a><span data-ttu-id="5d138-118">Criar a visualização do seu site</span><span class="sxs-lookup"><span data-stu-id="5d138-118">Crafting your website preview</span></span>

<span data-ttu-id="5d138-119">Quando seu site for compartilhado com o Teams, o cartão inserido no canal selecionado conterá uma visualização do seu site.</span><span class="sxs-lookup"><span data-stu-id="5d138-119">When your website is shared to Teams, the card that is inserted into the selected channel will contain a preview of your website.</span></span> <span data-ttu-id="5d138-120">Você pode controlar o comportamento dessa visualização garantindo que os metadados apropriados são adicionados ao site que está sendo compartilhado (a `data-href` URL).</span><span class="sxs-lookup"><span data-stu-id="5d138-120">You can control the behavior of this preview by ensuring the appropriate meta-data is added to the website being shared (the `data-href` URL).</span></span> <span data-ttu-id="5d138-121">A tabela abaixo descreve as marcas necessárias.</span><span class="sxs-lookup"><span data-stu-id="5d138-121">The table below outlines the necessary tags.</span></span> <span data-ttu-id="5d138-122">Você pode usar as versões padrão html ou a versão do Open Graph.</span><span class="sxs-lookup"><span data-stu-id="5d138-122">You can use either the html default versions, or the Open Graph version.</span></span>

<span data-ttu-id="5d138-123">Para que a visualização seja exibida, você deve:</span><span class="sxs-lookup"><span data-stu-id="5d138-123">In order for the preview to be displayed you must:</span></span>

* <span data-ttu-id="5d138-124">Inclua uma imagem em miniatura ou um título e uma descrição (para melhores resultados, inclua todos os três).</span><span class="sxs-lookup"><span data-stu-id="5d138-124">Include either a Thumbnail image, or both a Title and Description (for best results, include all three).</span></span>
* <span data-ttu-id="5d138-125">A URL que está sendo compartilhada não pode exigir autenticação.</span><span class="sxs-lookup"><span data-stu-id="5d138-125">The URL being shared cannot require authentication.</span></span> <span data-ttu-id="5d138-126">Se isso acontecer, você ainda poderá compartilhá-lo, mas a visualização não será criada.</span><span class="sxs-lookup"><span data-stu-id="5d138-126">If it does you can still share it, but the preview will not be created.</span></span>

|<span data-ttu-id="5d138-127">Valor</span><span class="sxs-lookup"><span data-stu-id="5d138-127">Value</span></span>|<span data-ttu-id="5d138-128">Marca Meta</span><span class="sxs-lookup"><span data-stu-id="5d138-128">Meta tag</span></span>| <span data-ttu-id="5d138-129">Abrir o Graph</span><span class="sxs-lookup"><span data-stu-id="5d138-129">Open Graph</span></span>|
|----|----|----|
|<span data-ttu-id="5d138-130">Título</span><span class="sxs-lookup"><span data-stu-id="5d138-130">Title</span></span>|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|<span data-ttu-id="5d138-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d138-131">Description</span></span>|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|<span data-ttu-id="5d138-132">Imagem em miniatura</span><span class="sxs-lookup"><span data-stu-id="5d138-132">Thumbnail Image</span></span>| <span data-ttu-id="5d138-133">nenhum</span><span class="sxs-lookup"><span data-stu-id="5d138-133">none</span></span> |`<meta property="og:image" content="http://example.com/image.jpg">`|

## <a name="share-to-teams-for-education"></a><span data-ttu-id="5d138-134">Compartilhar com o Teams para Educação</span><span class="sxs-lookup"><span data-stu-id="5d138-134">Share to Teams for Education</span></span>

<span data-ttu-id="5d138-135">Para professores que usam o botão Compartilhar com o Teams, você terá uma opção adicional `Create an Assignment` para.</span><span class="sxs-lookup"><span data-stu-id="5d138-135">For teachers using the Share to Teams button you'll be given an additional option to `Create an Assignment`.</span></span> <span data-ttu-id="5d138-136">Isso permite que você crie rapidamente uma atribuição na Equipe escolhida com base no link compartilhado.</span><span class="sxs-lookup"><span data-stu-id="5d138-136">This enables you to quickly create an assignment in the chosen Team based on the shared link.</span></span>

![Compartilhar com o pop-up do Teams](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a><span data-ttu-id="5d138-138">Definição launcher.js completa</span><span class="sxs-lookup"><span data-stu-id="5d138-138">Full launcher.js definition</span></span>

| <span data-ttu-id="5d138-139">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5d138-139">Property</span></span> | <span data-ttu-id="5d138-140">Atributo HTML</span><span class="sxs-lookup"><span data-stu-id="5d138-140">HTML attribute</span></span> | <span data-ttu-id="5d138-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="5d138-141">Type</span></span> | <span data-ttu-id="5d138-142">Padrão</span><span class="sxs-lookup"><span data-stu-id="5d138-142">Default</span></span> | <span data-ttu-id="5d138-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d138-143">Description</span></span> |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="5d138-144">href</span><span class="sxs-lookup"><span data-stu-id="5d138-144">href</span></span> | `data-href` | <span data-ttu-id="5d138-145">string</span><span class="sxs-lookup"><span data-stu-id="5d138-145">string</span></span> | <span data-ttu-id="5d138-146">n/d</span><span class="sxs-lookup"><span data-stu-id="5d138-146">n/a</span></span> | <span data-ttu-id="5d138-147">O href do conteúdo a ser compartilhá-lo.</span><span class="sxs-lookup"><span data-stu-id="5d138-147">The href of the content to share.</span></span> |
| <span data-ttu-id="5d138-148">visualização</span><span class="sxs-lookup"><span data-stu-id="5d138-148">preview</span></span> | `data-preview` | <span data-ttu-id="5d138-149">booliana (como uma cadeia de caracteres)</span><span class="sxs-lookup"><span data-stu-id="5d138-149">boolean (as a string)</span></span> | `true` | <span data-ttu-id="5d138-150">Se deve ou não mostrar uma visualização do conteúdo a ser compartilhá-lo.</span><span class="sxs-lookup"><span data-stu-id="5d138-150">Whether or not to show a preview of the content to share.</span></span> |
| <span data-ttu-id="5d138-151">iconPxSize</span><span class="sxs-lookup"><span data-stu-id="5d138-151">iconPxSize</span></span> | `data-icon-px-size` | <span data-ttu-id="5d138-152">número (como uma cadeia de caracteres)</span><span class="sxs-lookup"><span data-stu-id="5d138-152">number (as a string)</span></span> | `32` | <span data-ttu-id="5d138-153">O tamanho em pixels do botão Compartilhar para Teams a ser renderização.</span><span class="sxs-lookup"><span data-stu-id="5d138-153">The size in pixels of the Share-to-Teams button to render.</span></span> |
| <span data-ttu-id="5d138-154">msgText</span><span class="sxs-lookup"><span data-stu-id="5d138-154">msgText</span></span> | `data-msg-text` | <span data-ttu-id="5d138-155">string</span><span class="sxs-lookup"><span data-stu-id="5d138-155">string</span></span> | <span data-ttu-id="5d138-156">n/d</span><span class="sxs-lookup"><span data-stu-id="5d138-156">n/a</span></span> | <span data-ttu-id="5d138-157">Texto padrão a ser inserido antes do link na caixa de redação de mensagem (limite de 200 caracteres)</span><span class="sxs-lookup"><span data-stu-id="5d138-157">Default Text to be inserted before the link in the message compose box (200 character limit)</span></span> |
| <span data-ttu-id="5d138-158">assignInstr</span><span class="sxs-lookup"><span data-stu-id="5d138-158">assignInstr</span></span> | `data-assign-instr` | <span data-ttu-id="5d138-159">string</span><span class="sxs-lookup"><span data-stu-id="5d138-159">string</span></span> | <span data-ttu-id="5d138-160">n/d</span><span class="sxs-lookup"><span data-stu-id="5d138-160">n/a</span></span> | <span data-ttu-id="5d138-161">Texto padrão a ser inserido no campo de atribuições "Instruções" (limite de 200 caracteres)</span><span class="sxs-lookup"><span data-stu-id="5d138-161">Default Text to be inserted in the assignments "Instructions" field (200 character limit)</span></span> |
| <span data-ttu-id="5d138-162">assignTitle</span><span class="sxs-lookup"><span data-stu-id="5d138-162">assignTitle</span></span> | `data-assign-title` | <span data-ttu-id="5d138-163">string</span><span class="sxs-lookup"><span data-stu-id="5d138-163">string</span></span> | <span data-ttu-id="5d138-164">n/d</span><span class="sxs-lookup"><span data-stu-id="5d138-164">n/a</span></span> | <span data-ttu-id="5d138-165">Texto padrão a ser inserido no campo de atribuições "Título" (limite de 50 caracteres)</span><span class="sxs-lookup"><span data-stu-id="5d138-165">Default Text to be inserted in the assignments "Title" field (50 character limit)</span></span> |

### <a name="methods"></a><span data-ttu-id="5d138-166">Métodos</span><span class="sxs-lookup"><span data-stu-id="5d138-166">Methods</span></span>

**`shareToMicrosoftTeams.renderButtons(options)`**

<span data-ttu-id="5d138-167">`options` (opcional): `{ elements?: HTMLElement[] }`</span><span class="sxs-lookup"><span data-stu-id="5d138-167">`options` (optional): `{ elements?: HTMLElement[] }`</span></span>

<span data-ttu-id="5d138-168">Renderiza todos os botões de compartilhamento atualmente na página.</span><span class="sxs-lookup"><span data-stu-id="5d138-168">Renders all share buttons currently on the page.</span></span> <span data-ttu-id="5d138-169">Se um objeto opcional for fornecido com uma lista de elementos, esses elementos `options` serão renderizados em botões de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="5d138-169">If an optional `options` object is supplied with a list of elements, those elements will be rendered into share buttons.</span></span>

### <a name="setting-default-form-values"></a><span data-ttu-id="5d138-170">Definindo valores de formulário padrão</span><span class="sxs-lookup"><span data-stu-id="5d138-170">Setting default form values</span></span>

<span data-ttu-id="5d138-171">Opcionalmente, você pode optar por definir valores padrão para os seguintes campos no formulário Compartilhar com o Teams:</span><span class="sxs-lookup"><span data-stu-id="5d138-171">Optionally, you can choose to set default values for the following fields on the Share to Teams form:</span></span>

* <span data-ttu-id="5d138-172">Diga algo sobre isso ( `msgText` )</span><span class="sxs-lookup"><span data-stu-id="5d138-172">Say something about this (`msgText`)</span></span>
* <span data-ttu-id="5d138-173">Instruções de atribuição ( `assignInstr` )</span><span class="sxs-lookup"><span data-stu-id="5d138-173">Assignment Instructions (`assignInstr`)</span></span>
* <span data-ttu-id="5d138-174">Título da Atribuição ( `assignTitle` )</span><span class="sxs-lookup"><span data-stu-id="5d138-174">Assignment Title (`assignTitle`)</span></span>

#### <a name="example-default-form-values"></a><span data-ttu-id="5d138-175">Exemplo: valores de formulário padrão</span><span class="sxs-lookup"><span data-stu-id="5d138-175">Example: Default form values</span></span>

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```
