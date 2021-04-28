---
title: Criar um botão Compartilhar para o Teams
description: Como adicionar o botão Compartilhar ao Teams inserido em seu site
ms.topic: reference
localization_priority: Normal
keywords: Compartilhar o Teams Share-to-Teams
ms.openlocfilehash: c8bbb371e2d68bf063c3aa5e02c7cf3ec911c0b8
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058471"
---
# <a name="create-share-to-teams-button"></a><span data-ttu-id="df73d-104">Criar um botão Compartilhar para o Teams</span><span class="sxs-lookup"><span data-stu-id="df73d-104">Create Share-to-Teams button</span></span>

<span data-ttu-id="df73d-105">Sites de terceiros podem usar o script do launcher para incorporar botões do Share-to-Teams em suas páginas da Web.</span><span class="sxs-lookup"><span data-stu-id="df73d-105">Third-party websites can use the launcher script to embed Share-to-Teams buttons on their webpages.</span></span> <span data-ttu-id="df73d-106">Quando você seleciona, ele inicia a experiência do Share-to-Teams em uma janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="df73d-106">When you select, it launches the Share-to-Teams experience in a pop-up window.</span></span> <span data-ttu-id="df73d-107">Isso permite compartilhar um link diretamente com qualquer pessoa ou canal do Microsoft Teams sem alternar o contexto.</span><span class="sxs-lookup"><span data-stu-id="df73d-107">This allows you to share a link directly to any person or Microsoft Teams channel without switching the context.</span></span> <span data-ttu-id="df73d-108">Este documento orienta você sobre como criar e inserir um botão Compartilhar para o Teams para seu site, criar a visualização do site e estender o Share-to-Teams para Educação.</span><span class="sxs-lookup"><span data-stu-id="df73d-108">This document guides you on how to create, and embed a Share-to-Teams button for your website, craft your website preview, and extend Share-to-Teams for Education.</span></span>

> [!NOTE]
> * <span data-ttu-id="df73d-109">Somente as versões da área de trabalho do Edge e do Chrome têm suporte.</span><span class="sxs-lookup"><span data-stu-id="df73d-109">Only the desktop versions of Edge and Chrome are supported.</span></span>
> * <span data-ttu-id="df73d-110">Não há suporte para o uso de contas de convidado ou de Freemium.</span><span class="sxs-lookup"><span data-stu-id="df73d-110">Use of Freemium or guest accounts is not supported.</span></span>  

<span data-ttu-id="df73d-111">A imagem a seguir exibe a experiência pop-up Share-to-Teams:</span><span class="sxs-lookup"><span data-stu-id="df73d-111">The following image displays the Share-to-Teams pop-up experience:</span></span>

![Pop-up Share-to-Teams](~/assets/images/share-to-teams-popup.png)

## <a name="embed-a-share-to-teams-button"></a><span data-ttu-id="df73d-113">Inserir um botão Compartilhar para o Teams</span><span class="sxs-lookup"><span data-stu-id="df73d-113">Embed a Share to Teams button</span></span>

1. <span data-ttu-id="df73d-114">Adicione o `launcher.js` script em sua página da Web.</span><span class="sxs-lookup"><span data-stu-id="df73d-114">Add the `launcher.js` script on your webpage.</span></span>

    ```html
    <script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
    ```

1. <span data-ttu-id="df73d-115">Adicione um elemento HTML em sua página da Web com o atributo de classe e `teams-share-button` o link para compartilhar no `data-href` atributo.</span><span class="sxs-lookup"><span data-stu-id="df73d-115">Add a HTML element on your webpage with the `teams-share-button` class attribute and the link to share in the `data-href` attribute.</span></span>

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>">
    </div>
    ```

    <span data-ttu-id="df73d-116">Depois de concluir isso, o ícone do Microsoft Teams é adicionado ao seu site.</span><span class="sxs-lookup"><span data-stu-id="df73d-116">After completing this, the Microsoft Teams icon gets added to your website.</span></span> <span data-ttu-id="df73d-117">A imagem a seguir mostra o ícone Do Share-to-Teams:</span><span class="sxs-lookup"><span data-stu-id="df73d-117">The following image shows Share-to-Teams icon:</span></span>

    ![Ícone Compartilhar com o Teams](~/assets/icons/share-to-teams-icon.png)

1. <span data-ttu-id="df73d-119">Como alternativa, se você quiser um tamanho de ícone diferente para o botão Compartilhar com o Teams, use o `data-icon-px-size` atributo.</span><span class="sxs-lookup"><span data-stu-id="df73d-119">Alternatively, if you want a different icon size for the Share-to Teams button, use the `data-icon-px-size` attribute.</span></span>

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-icon-px-size="64">
    </div>
    ```
1. <span data-ttu-id="df73d-120">Se o link compartilhado exigir autenticação do usuário e a visualização da URL do link a ser compartilhado não renderizar bem no Teams, você poderá desabilitar a visualização da URL adicionando o atributo `data-preview` definido como `false` .</span><span class="sxs-lookup"><span data-stu-id="df73d-120">If the shared link requires user authentication, and the URL preview from your link to be shared does not render well in Teams then, you can disable the URL preview by adding the `data-preview` attribute set to `false`.</span></span>

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-preview="false">
    </div>
    ```

1. <span data-ttu-id="df73d-121">Se sua página renderizar dinamicamente o conteúdo, você poderá usar o método para forçar o botão Compartilhar a renderizar no `shareToMicrosoftTeams.renderButtons()` local apropriado no pipeline. </span><span class="sxs-lookup"><span data-stu-id="df73d-121">If your page dynamically renders content, you can use the the `shareToMicrosoftTeams.renderButtons()` method to force the **Share** button to render at the appropriate place in the pipeline.</span></span>

## <a name="craft-your-website-preview"></a><span data-ttu-id="df73d-122">Criar a visualização do site</span><span class="sxs-lookup"><span data-stu-id="df73d-122">Craft your website preview</span></span>

<span data-ttu-id="df73d-123">Quando seu site é compartilhado com o Teams, o cartão inserido no canal selecionado contém uma visualização do seu site.</span><span class="sxs-lookup"><span data-stu-id="df73d-123">When your website is shared to Teams, the card that is inserted into the selected channel contains a preview of your website.</span></span> <span data-ttu-id="df73d-124">Você pode controlar o comportamento dessa visualização garantindo que os metadados apropriados são adicionados ao site que está sendo compartilhado, como a `data-href` URL.</span><span class="sxs-lookup"><span data-stu-id="df73d-124">You can control the behavior of this preview by ensuring the appropriate meta-data is added to the website being shared, such as the `data-href` URL.</span></span>  

<span data-ttu-id="df73d-125">**Para exibir a visualização**</span><span class="sxs-lookup"><span data-stu-id="df73d-125">**To display the preview**</span></span>

* <span data-ttu-id="df73d-126">Você deve incluir uma imagem **thumbnail** ou um **título** e uma **descrição.**</span><span class="sxs-lookup"><span data-stu-id="df73d-126">You must include either a **Thumbnail image**, or both a **Title** and **Description**.</span></span> <span data-ttu-id="df73d-127">Para melhores resultados, inclua todos os três.</span><span class="sxs-lookup"><span data-stu-id="df73d-127">For best results, include all three.</span></span>
* <span data-ttu-id="df73d-128">A URL compartilhada não exige autenticação.</span><span class="sxs-lookup"><span data-stu-id="df73d-128">The shared URL does not require authentication.</span></span> <span data-ttu-id="df73d-129">Se ela exigir autenticação, você poderá compartilhá-la, mas a visualização não será criada.</span><span class="sxs-lookup"><span data-stu-id="df73d-129">If it requires authentication, you can share it, but the preview is not created.</span></span>

<span data-ttu-id="df73d-130">A tabela a seguir descreve as marcas necessárias:</span><span class="sxs-lookup"><span data-stu-id="df73d-130">The following table outlines the necessary tags:</span></span>

|<span data-ttu-id="df73d-131">Valor</span><span class="sxs-lookup"><span data-stu-id="df73d-131">Value</span></span>|<span data-ttu-id="df73d-132">Marca Meta</span><span class="sxs-lookup"><span data-stu-id="df73d-132">Meta tag</span></span>| <span data-ttu-id="df73d-133">Abrir Graph</span><span class="sxs-lookup"><span data-stu-id="df73d-133">Open Graph</span></span>|
|----|----|----|
|<span data-ttu-id="df73d-134">Título</span><span class="sxs-lookup"><span data-stu-id="df73d-134">Title</span></span>|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|<span data-ttu-id="df73d-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="df73d-135">Description</span></span>|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|<span data-ttu-id="df73d-136">Imagem de miniatura</span><span class="sxs-lookup"><span data-stu-id="df73d-136">Thumbnail Image</span></span>| <span data-ttu-id="df73d-137">none.</span><span class="sxs-lookup"><span data-stu-id="df73d-137">none.</span></span> |`<meta property="og:image" content="http://example.com/image.jpg">`|

<span data-ttu-id="df73d-138">Você pode usar as versões padrão html ou a versão do Open Graph.</span><span class="sxs-lookup"><span data-stu-id="df73d-138">You can use either the html default versions, or the Open Graph version.</span></span>

## <a name="share-to-teams-for-education"></a><span data-ttu-id="df73d-139">Compartilhar com o Teams para Educação</span><span class="sxs-lookup"><span data-stu-id="df73d-139">Share to Teams for Education</span></span>

<span data-ttu-id="df73d-140">Para professores que usam o botão Compartilhar com o Teams, há uma opção adicional para `Create an Assignment` .</span><span class="sxs-lookup"><span data-stu-id="df73d-140">For teachers using the Share to Teams button, there is an additional option to `Create an Assignment`.</span></span> <span data-ttu-id="df73d-141">Isso permite que você crie rapidamente uma atribuição na Equipe escolhida, com base no link compartilhado.</span><span class="sxs-lookup"><span data-stu-id="df73d-141">This enables you to quickly create an assignment in the chosen Team, based on the shared link.</span></span> <span data-ttu-id="df73d-142">A imagem a seguir exibe o Share-to-Teams para educação:</span><span class="sxs-lookup"><span data-stu-id="df73d-142">The following image displays Share-to-Teams for education:</span></span> 

![Compartilhar com a educação pop-up do Teams](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a><span data-ttu-id="df73d-144">Definição launcher.js completa</span><span class="sxs-lookup"><span data-stu-id="df73d-144">Full launcher.js definition</span></span>

| <span data-ttu-id="df73d-145">Propriedade</span><span class="sxs-lookup"><span data-stu-id="df73d-145">Property</span></span> | <span data-ttu-id="df73d-146">Atributo HTML</span><span class="sxs-lookup"><span data-stu-id="df73d-146">HTML attribute</span></span> | <span data-ttu-id="df73d-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="df73d-147">Type</span></span> | <span data-ttu-id="df73d-148">Padrão</span><span class="sxs-lookup"><span data-stu-id="df73d-148">Default</span></span> | <span data-ttu-id="df73d-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="df73d-149">Description</span></span> |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="df73d-150">href</span><span class="sxs-lookup"><span data-stu-id="df73d-150">href</span></span> | `data-href` | <span data-ttu-id="df73d-151">string</span><span class="sxs-lookup"><span data-stu-id="df73d-151">string</span></span> | <span data-ttu-id="df73d-152">n/d</span><span class="sxs-lookup"><span data-stu-id="df73d-152">n/a</span></span> | <span data-ttu-id="df73d-153">O href do conteúdo a ser compartilhá-lo.</span><span class="sxs-lookup"><span data-stu-id="df73d-153">The href of the content to share.</span></span> |
| <span data-ttu-id="df73d-154">visualização</span><span class="sxs-lookup"><span data-stu-id="df73d-154">preview</span></span> | `data-preview` | <span data-ttu-id="df73d-155">booleano (como uma cadeia de caracteres)</span><span class="sxs-lookup"><span data-stu-id="df73d-155">boolean (as a string)</span></span> | `true` | <span data-ttu-id="df73d-156">Se deve ou não mostrar uma visualização do conteúdo a ser compartilhá-lo.</span><span class="sxs-lookup"><span data-stu-id="df73d-156">Whether or not to show a preview of the content to share.</span></span> |
| <span data-ttu-id="df73d-157">iconPxSize</span><span class="sxs-lookup"><span data-stu-id="df73d-157">iconPxSize</span></span> | `data-icon-px-size` | <span data-ttu-id="df73d-158">number (como uma cadeia de caracteres)</span><span class="sxs-lookup"><span data-stu-id="df73d-158">number (as a string)</span></span> | `32` | <span data-ttu-id="df73d-159">O tamanho em pixels do botão Compartilhar para Equipes a ser render.</span><span class="sxs-lookup"><span data-stu-id="df73d-159">The size in pixels of the Share-to-Teams button to render.</span></span> |
| <span data-ttu-id="df73d-160">msgText</span><span class="sxs-lookup"><span data-stu-id="df73d-160">msgText</span></span> | `data-msg-text` | <span data-ttu-id="df73d-161">string</span><span class="sxs-lookup"><span data-stu-id="df73d-161">string</span></span> | <span data-ttu-id="df73d-162">n/d</span><span class="sxs-lookup"><span data-stu-id="df73d-162">n/a</span></span> | <span data-ttu-id="df73d-163">Texto padrão a ser inserido antes do link na caixa de redação da mensagem.</span><span class="sxs-lookup"><span data-stu-id="df73d-163">Default Text to be inserted before the link in the message compose box.</span></span> <span data-ttu-id="df73d-164">O número máximo de caracteres é 200.</span><span class="sxs-lookup"><span data-stu-id="df73d-164">Maximum number of characters is 200.</span></span> |
| <span data-ttu-id="df73d-165">assignInstr</span><span class="sxs-lookup"><span data-stu-id="df73d-165">assignInstr</span></span> | `data-assign-instr` | <span data-ttu-id="df73d-166">string</span><span class="sxs-lookup"><span data-stu-id="df73d-166">string</span></span> | <span data-ttu-id="df73d-167">n/d</span><span class="sxs-lookup"><span data-stu-id="df73d-167">n/a</span></span> | <span data-ttu-id="df73d-168">Texto padrão a ser inserido no campo "Instruções" de atribuições.</span><span class="sxs-lookup"><span data-stu-id="df73d-168">Default Text to be inserted in the assignments "Instructions" field.</span></span> <span data-ttu-id="df73d-169">O número máximo de caracteres é 200.</span><span class="sxs-lookup"><span data-stu-id="df73d-169">Maximum number of characters is 200.</span></span> |
| <span data-ttu-id="df73d-170">assignTitle</span><span class="sxs-lookup"><span data-stu-id="df73d-170">assignTitle</span></span> | `data-assign-title` | <span data-ttu-id="df73d-171">string</span><span class="sxs-lookup"><span data-stu-id="df73d-171">string</span></span> | <span data-ttu-id="df73d-172">n/d</span><span class="sxs-lookup"><span data-stu-id="df73d-172">n/a</span></span> | <span data-ttu-id="df73d-173">Texto padrão a ser inserido no campo "Título" de atribuições.</span><span class="sxs-lookup"><span data-stu-id="df73d-173">Default Text to be inserted in the assignments "Title" field.</span></span> <span data-ttu-id="df73d-174">O número máximo de caracteres é 50.</span><span class="sxs-lookup"><span data-stu-id="df73d-174">Maximum number of characters is 50.</span></span> |

### <a name="methods"></a><span data-ttu-id="df73d-175">Métodos</span><span class="sxs-lookup"><span data-stu-id="df73d-175">Methods</span></span>

**`shareToMicrosoftTeams.renderButtons(options)`**

<span data-ttu-id="df73d-176">`options` (opcional): `{ elements?: HTMLElement[] }`</span><span class="sxs-lookup"><span data-stu-id="df73d-176">`options` (optional): `{ elements?: HTMLElement[] }`</span></span>

<span data-ttu-id="df73d-177">Atualmente, todos os botões de compartilhamento são renderizados na página.</span><span class="sxs-lookup"><span data-stu-id="df73d-177">Currently, all share buttons are rendered on the page.</span></span> <span data-ttu-id="df73d-178">Se um objeto `options` opcional for fornecido com uma lista de elementos, esses elementos serão renderizados em botões de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="df73d-178">If an optional `options` object is supplied with a list of elements, those elements are rendered into share buttons.</span></span>

### <a name="set-default-form-values"></a><span data-ttu-id="df73d-179">Definir valores de formulário padrão</span><span class="sxs-lookup"><span data-stu-id="df73d-179">Set default form values</span></span>

<span data-ttu-id="df73d-180">Você pode selecionar para definir valores padrão para os seguintes campos no formulário Compartilhar para o Teams:</span><span class="sxs-lookup"><span data-stu-id="df73d-180">You can select to set default values for the following fields on the Share to Teams form:</span></span>

* <span data-ttu-id="df73d-181">Diga algo sobre isso: `msgText`</span><span class="sxs-lookup"><span data-stu-id="df73d-181">Say something about this: `msgText`</span></span>
* <span data-ttu-id="df73d-182">Instruções de atribuição: `assignInstr`</span><span class="sxs-lookup"><span data-stu-id="df73d-182">Assignment Instructions: `assignInstr`</span></span>
* <span data-ttu-id="df73d-183">Título da atribuição: `assignTitle`</span><span class="sxs-lookup"><span data-stu-id="df73d-183">Assignment Title: `assignTitle`</span></span>

#### <a name="example"></a><span data-ttu-id="df73d-184">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df73d-184">Example</span></span>

 <span data-ttu-id="df73d-185">Os valores de formulário padrão são dados no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="df73d-185">Default form values are given in the following example:</span></span>

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```

## <a name="see-also"></a><span data-ttu-id="df73d-186">Confira também</span><span class="sxs-lookup"><span data-stu-id="df73d-186">See also</span></span>

- [<span data-ttu-id="df73d-187">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="df73d-187">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
