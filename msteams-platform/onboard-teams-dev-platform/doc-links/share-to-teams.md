---
title: Adicionar um botão compartilhar ao Teams ao seu site
description: Como adicionar o botão compartilhar ao Teams incorporado no seu site
keywords: Compartilhar o Microsoft Teams para o Teams
ms.openlocfilehash: 0ebd47af068bf523f27c19241b85d2137af3ada6
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651833"
---
# <a name="adding-a-share-to-teams-button-to-your-website"></a><span data-ttu-id="0395e-104">Adicionar um botão compartilhar ao Teams ao seu site</span><span class="sxs-lookup"><span data-stu-id="0395e-104">Adding a Share to Teams button to your website</span></span>

>[!NOTE]
> * <span data-ttu-id="0395e-105">Só há suporte para as versões de área de trabalho do Edge e do Chrome.</span><span class="sxs-lookup"><span data-stu-id="0395e-105">Only the desktop versions of Edge and Chrome are supported.</span></span>
> * <span data-ttu-id="0395e-106">Não há suporte para o uso de contas de convidado ou freemium.</span><span class="sxs-lookup"><span data-stu-id="0395e-106">Use of Freemium or guest accounts is not supported.</span></span>

<span data-ttu-id="0395e-107">Sites de terceiros podem usar o script iniciador para inserir o compartilhamento para os botões do teams em suas páginas da Web, que iniciarão o compartilhamento com a experiência do teams em uma janela pop-up quando clicado.</span><span class="sxs-lookup"><span data-stu-id="0395e-107">Third-party websites can use the launcher script to embed Share to Teams buttons on their webpages which will launch the Share to Teams experience in a popup window when clicked.</span></span> <span data-ttu-id="0395e-108">Isso permitirá que você compartilhe um link diretamente para qualquer pessoa ou canal do Microsoft Teams sem alterar o contexto.</span><span class="sxs-lookup"><span data-stu-id="0395e-108">This will allow you to share a link directly to any person or Microsoft Teams channel without switching context.</span></span>

![Pop-up compartilhar com o Teams](~/assets/images/share-to-teams-popup.png)

## <a name="how-to-embed-a-share-to-teams-button"></a><span data-ttu-id="0395e-110">Como inserir um compartilhamento no botão Teams</span><span class="sxs-lookup"><span data-stu-id="0395e-110">How to embed a Share to Teams button</span></span>

<span data-ttu-id="0395e-111">Primeiro, você precisará adicionar o `launcher.js` script na sua página da Web.</span><span class="sxs-lookup"><span data-stu-id="0395e-111">First, you'll need to add the `launcher.js` script on your webpage.</span></span>

```html
<script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
```

<span data-ttu-id="0395e-112">Em seguida, adicione um elemento HTML na sua página da Web com o `teams-share-button` atributo Class e o link para compartilhar no `data-href` atributo.</span><span class="sxs-lookup"><span data-stu-id="0395e-112">Next, add an HTML element on your webpage with the `teams-share-button` class attribute and the link to share in the `data-href` attribute.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>">
</div>
```

<span data-ttu-id="0395e-113">Isso adicionará o ícone do Microsoft Teams ao seu site.</span><span class="sxs-lookup"><span data-stu-id="0395e-113">This will add the Microsoft Teams icon to your website.</span></span>

![Ícone compartilhar com o Teams](~/assets/icons/share-to-teams-icon.png)

<span data-ttu-id="0395e-115">Opcionalmente, se você quiser um tamanho de ícone diferente para o botão compartilhar com Teams, use o `data-icon-px-size` atributo.</span><span class="sxs-lookup"><span data-stu-id="0395e-115">Optionally, if you want a different icon size for the Share to Teams button, use the `data-icon-px-size` attribute.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-icon-px-size="64">
</div>
```

<span data-ttu-id="0395e-116">Se você souber que a URL de visualização do link a ser compartilhado não renderizará bem no Teams (por exemplo, o link exigirá autenticação do usuário), você poderá desabilitar a visualização da URL adicionando o `data-preview` atributo definido para `false` .</span><span class="sxs-lookup"><span data-stu-id="0395e-116">If you know that the URL preview from your link to be shared won't render well in Teams (for example the link would require user authentication) you can disable the URL preview by adding the `data-preview` attribute set to `false`.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-preview="false">
</div>
```

<span data-ttu-id="0395e-117">Se sua página renderiza dinamicamente o conteúdo, você pode usar o `shareToMicrosoftTeams.renderButtons()` método para forçar o botão **compartilhar** para renderizar no local apropriado no pipeline.</span><span class="sxs-lookup"><span data-stu-id="0395e-117">If your page dynamically renders content, you can use the the `shareToMicrosoftTeams.renderButtons()` method to force the **Share** button to render at the appropriate place in the pipeline.</span></span>

## <a name="crafting-your-website-preview"></a><span data-ttu-id="0395e-118">Como criar sua versão prévia do site</span><span class="sxs-lookup"><span data-stu-id="0395e-118">Crafting your website preview</span></span>

<span data-ttu-id="0395e-119">Quando o seu site é compartilhado para o Microsoft Teams, o cartão que é inserido no canal selecionado conterá uma visualização do seu site.</span><span class="sxs-lookup"><span data-stu-id="0395e-119">When your website is shared to Teams, the card that is inserted into the selected channel will contain a preview of your website.</span></span> <span data-ttu-id="0395e-120">Você pode controlar o comportamento dessa visualização garantindo que os metadados apropriados sejam adicionados ao site que está sendo compartilhado (a `data-href` URL).</span><span class="sxs-lookup"><span data-stu-id="0395e-120">You can control the behavior of this preview by ensuring the appropriate meta-data is added to the website being shared (the `data-href` URL).</span></span> <span data-ttu-id="0395e-121">A tabela abaixo descreve as marcas necessárias.</span><span class="sxs-lookup"><span data-stu-id="0395e-121">The table below outlines the necessary tags.</span></span> <span data-ttu-id="0395e-122">Você pode usar as versões padrão HTML ou a versão aberta do Graph.</span><span class="sxs-lookup"><span data-stu-id="0395e-122">You can use either the html default versions, or the Open Graph version.</span></span>

<span data-ttu-id="0395e-123">Para que a visualização seja exibida, você deve:</span><span class="sxs-lookup"><span data-stu-id="0395e-123">In order for the preview to be displayed you must:</span></span>

* <span data-ttu-id="0395e-124">Inclua uma imagem em miniatura ou um título e uma descrição (para obter os melhores resultados, inclua todos os três).</span><span class="sxs-lookup"><span data-stu-id="0395e-124">Include either a Thumbnail image, or both a Title and Description (for best results, include all three).</span></span>
* <span data-ttu-id="0395e-125">A URL que está sendo compartilhada não pode exigir autenticação.</span><span class="sxs-lookup"><span data-stu-id="0395e-125">The URL being shared cannot require authentication.</span></span> <span data-ttu-id="0395e-126">Se você ainda pode compartilhá-lo, mas a visualização não será criada.</span><span class="sxs-lookup"><span data-stu-id="0395e-126">If it does you can still share it, but the preview will not be created.</span></span>

|<span data-ttu-id="0395e-127">Valor</span><span class="sxs-lookup"><span data-stu-id="0395e-127">Value</span></span>|<span data-ttu-id="0395e-128">Marca Meta</span><span class="sxs-lookup"><span data-stu-id="0395e-128">Meta tag</span></span>| <span data-ttu-id="0395e-129">Abrir gráfico</span><span class="sxs-lookup"><span data-stu-id="0395e-129">Open Graph</span></span>|
|----|----|----|
|<span data-ttu-id="0395e-130">Título</span><span class="sxs-lookup"><span data-stu-id="0395e-130">Title</span></span>|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|<span data-ttu-id="0395e-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="0395e-131">Description</span></span>|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|<span data-ttu-id="0395e-132">Imagem em miniatura</span><span class="sxs-lookup"><span data-stu-id="0395e-132">Thumbnail Image</span></span>| <span data-ttu-id="0395e-133">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="0395e-133">none</span></span> |`<meta property="og:image" content="http://example.com/image.jpg">`|

## <a name="share-to-teams-for-education"></a><span data-ttu-id="0395e-134">Compartilhar com o Microsoft Teams para educação</span><span class="sxs-lookup"><span data-stu-id="0395e-134">Share to Teams for Education</span></span>

<span data-ttu-id="0395e-135">Para professores usando o botão compartilhar para equipes, você receberá uma opção adicional para `Create an Assignment` .</span><span class="sxs-lookup"><span data-stu-id="0395e-135">For teachers using the Share to Teams button you'll be given an additional option to `Create an Assignment`.</span></span> <span data-ttu-id="0395e-136">Isso permite que você crie rapidamente uma atribuição na equipe escolhida com base no link compartilhado.</span><span class="sxs-lookup"><span data-stu-id="0395e-136">This enables you to quickly create an assignment in the chosen Team based on the shared link.</span></span>

![Pop-up compartilhar com o Teams](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a><span data-ttu-id="0395e-138">Definição de launcher.js completa</span><span class="sxs-lookup"><span data-stu-id="0395e-138">Full launcher.js definition</span></span>

| <span data-ttu-id="0395e-139">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0395e-139">Property</span></span> | <span data-ttu-id="0395e-140">Atributo HTML</span><span class="sxs-lookup"><span data-stu-id="0395e-140">HTML attribute</span></span> | <span data-ttu-id="0395e-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="0395e-141">Type</span></span> | <span data-ttu-id="0395e-142">Padrão</span><span class="sxs-lookup"><span data-stu-id="0395e-142">Default</span></span> | <span data-ttu-id="0395e-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="0395e-143">Description</span></span> |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="0395e-144">href</span><span class="sxs-lookup"><span data-stu-id="0395e-144">href</span></span> | `data-href` | <span data-ttu-id="0395e-145">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0395e-145">string</span></span> | <span data-ttu-id="0395e-146">n/d</span><span class="sxs-lookup"><span data-stu-id="0395e-146">n/a</span></span> | <span data-ttu-id="0395e-147">O href do conteúdo a ser compartilhado.</span><span class="sxs-lookup"><span data-stu-id="0395e-147">The href of the content to share.</span></span> |
| <span data-ttu-id="0395e-148">visualização</span><span class="sxs-lookup"><span data-stu-id="0395e-148">preview</span></span> | `data-preview` | <span data-ttu-id="0395e-149">booliano (como uma cadeia de caracteres)</span><span class="sxs-lookup"><span data-stu-id="0395e-149">boolean (as a string)</span></span> | `true` | <span data-ttu-id="0395e-150">Se mostrar ou não uma visualização do conteúdo a ser compartilhado.</span><span class="sxs-lookup"><span data-stu-id="0395e-150">Whether or not to show a preview of the content to share.</span></span> |
| <span data-ttu-id="0395e-151">iconPxSize</span><span class="sxs-lookup"><span data-stu-id="0395e-151">iconPxSize</span></span> | `data-icon-px-size` | <span data-ttu-id="0395e-152">número (como uma cadeia de caracteres)</span><span class="sxs-lookup"><span data-stu-id="0395e-152">number (as a string)</span></span> | `32` | <span data-ttu-id="0395e-153">O tamanho em pixels do botão Share-to-Teams a ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="0395e-153">The size in pixels of the Share-to-Teams button to render.</span></span> |
| <span data-ttu-id="0395e-154">msgText</span><span class="sxs-lookup"><span data-stu-id="0395e-154">msgText</span></span> | `data-msg-text` | <span data-ttu-id="0395e-155">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0395e-155">string</span></span> | <span data-ttu-id="0395e-156">n/d</span><span class="sxs-lookup"><span data-stu-id="0395e-156">n/a</span></span> | <span data-ttu-id="0395e-157">Texto padrão a ser inserido antes do link na caixa de composição de mensagem (limite de caracteres de 200)</span><span class="sxs-lookup"><span data-stu-id="0395e-157">Default Text to be inserted before the link in the message compose box (200 character limit)</span></span> |
| <span data-ttu-id="0395e-158">assignInstr</span><span class="sxs-lookup"><span data-stu-id="0395e-158">assignInstr</span></span> | `data-assign-instr` | <span data-ttu-id="0395e-159">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0395e-159">string</span></span> | <span data-ttu-id="0395e-160">n/d</span><span class="sxs-lookup"><span data-stu-id="0395e-160">n/a</span></span> | <span data-ttu-id="0395e-161">Texto padrão a ser inserido no campo atribuições "instruções" (limite de caracteres 200)</span><span class="sxs-lookup"><span data-stu-id="0395e-161">Default Text to be inserted in the assignments "Instructions" field (200 character limit)</span></span> |
| <span data-ttu-id="0395e-162">assignTitle</span><span class="sxs-lookup"><span data-stu-id="0395e-162">assignTitle</span></span> | `data-assign-title` | <span data-ttu-id="0395e-163">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0395e-163">string</span></span> | <span data-ttu-id="0395e-164">n/d</span><span class="sxs-lookup"><span data-stu-id="0395e-164">n/a</span></span> | <span data-ttu-id="0395e-165">Texto padrão a ser inserido no campo "título" das atribuições (limite de caracteres de 50)</span><span class="sxs-lookup"><span data-stu-id="0395e-165">Default Text to be inserted in the assignments "Title" field (50 character limit)</span></span> |

### <a name="methods"></a><span data-ttu-id="0395e-166">Métodos</span><span class="sxs-lookup"><span data-stu-id="0395e-166">Methods</span></span>

**`shareToMicrosoftTeams.renderButtons(options)`**

<span data-ttu-id="0395e-167">`options` (opcional): `{ elements?: HTMLElement[] }`</span><span class="sxs-lookup"><span data-stu-id="0395e-167">`options` (optional): `{ elements?: HTMLElement[] }`</span></span>

<span data-ttu-id="0395e-168">Processa todos os botões de compartilhamento atualmente na página.</span><span class="sxs-lookup"><span data-stu-id="0395e-168">Renders all share buttons currently on the page.</span></span> <span data-ttu-id="0395e-169">Se um `options` objeto opcional for fornecido com uma lista de elementos, esses elementos serão renderizados em botões de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="0395e-169">If an optional `options` object is supplied with a list of elements, those elements will be rendered into share buttons.</span></span>

### <a name="setting-default-form-values"></a><span data-ttu-id="0395e-170">Definindo valores de formulário padrão</span><span class="sxs-lookup"><span data-stu-id="0395e-170">Setting default form values</span></span>

<span data-ttu-id="0395e-171">Opcionalmente, você pode optar por definir valores padrão para os seguintes campos no formulário compartilhar com o Teams:</span><span class="sxs-lookup"><span data-stu-id="0395e-171">Optionally, you can choose to set default values for the following fields on the Share to Teams form:</span></span>

* <span data-ttu-id="0395e-172">Diga algo sobre isso ( `msgText` )</span><span class="sxs-lookup"><span data-stu-id="0395e-172">Say something about this (`msgText`)</span></span>
* <span data-ttu-id="0395e-173">Instruções de atribuição ( `assignInstr` )</span><span class="sxs-lookup"><span data-stu-id="0395e-173">Assignment Instructions (`assignInstr`)</span></span>
* <span data-ttu-id="0395e-174">Título da atribuição ( `assignTitle` )</span><span class="sxs-lookup"><span data-stu-id="0395e-174">Assignment Title (`assignTitle`)</span></span>

#### <a name="example-default-form-values"></a><span data-ttu-id="0395e-175">Exemplo: valores de formulário padrão</span><span class="sxs-lookup"><span data-stu-id="0395e-175">Example: Default form values</span></span>

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```
