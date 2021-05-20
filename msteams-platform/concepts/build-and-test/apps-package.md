---
title: Empacote seu aplicativo
description: Aprenda a empacotar seu aplicativo Microsoft Teams para testes, upload e publicação na loja.
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 219e2d5341707ed51b7e0a3a8077f93df9eac640
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565211"
---
# <a name="create-a-microsoft-teams-app-package"></a><span data-ttu-id="493c4-103">Crie um pacote de aplicativo Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="493c4-103">Create a Microsoft Teams app package</span></span>

<span data-ttu-id="493c4-104">Você precisa de um pacote de aplicativo no entanto, você planeja distribuir seu aplicativo Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="493c4-104">You need an app package however you plan to distribute your Microsoft Teams app.</span></span> <span data-ttu-id="493c4-105">Um pacote válido é um arquivo ZIP que contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="493c4-105">A valid package is a ZIP file that contains the following:</span></span>

* <span data-ttu-id="493c4-106">**Manifesto do aplicativo**: Descreve como seu aplicativo está configurado, incluindo seus recursos, recursos necessários e outros atributos importantes.</span><span class="sxs-lookup"><span data-stu-id="493c4-106">**App manifest**: Describes how your app is configured, including its capabilities, required resources, and other important attributes.</span></span>
* <span data-ttu-id="493c4-107">**Ícones do** aplicativo : Cada pacote requer um ícone de cor e contorno para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="493c4-107">**App icons**: Each package requires a color and outline icon for your app.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="493c4-108">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="493c4-108">App manifest</span></span>

<span data-ttu-id="493c4-109">Seu arquivo manifesto do aplicativo deve estar no nível superior do pacote com o nome `manifest.json` .</span><span class="sxs-lookup"><span data-stu-id="493c4-109">Your app manifest file must be at the top level of the package with the name `manifest.json`.</span></span> 

<span data-ttu-id="493c4-110">Ao publicar na loja Teams, certifique-se de que seu manifesto faz referência ao último [esquema](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="493c4-110">When publishing to the Teams store, make sure your manifest references the latest [schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="app-icons"></a><span data-ttu-id="493c4-111">Ícones de aplicativos</span><span class="sxs-lookup"><span data-stu-id="493c4-111">App icons</span></span>

<span data-ttu-id="493c4-112">Seu pacote de aplicativos deve incluir duas versões PNG do ícone do seu aplicativo: uma versão colorida e de contorno.</span><span class="sxs-lookup"><span data-stu-id="493c4-112">Your app package must include two PNG versions of your app icon: A color and outline version.</span></span>

> [!Note]
> <span data-ttu-id="493c4-113">Se o seu aplicativo tiver uma extensão de bot ou mensagens, seus ícones também serão incluídos no registro do seu Microsoft Azure Bot Service.</span><span class="sxs-lookup"><span data-stu-id="493c4-113">If your app has a bot or messaging extension, your icons also will be included in your Microsoft Azure Bot Service registration.</span></span>

<span data-ttu-id="493c4-114">Para que seu aplicativo passe Teams revisão da loja, esses ícones devem atender aos seguintes requisitos de tamanho.</span><span class="sxs-lookup"><span data-stu-id="493c4-114">For your app to pass Teams store review, these icons must meet the following size requirements.</span></span>

### <a name="color-icon"></a><span data-ttu-id="493c4-115">Ícone de cor</span><span class="sxs-lookup"><span data-stu-id="493c4-115">Color icon</span></span>

<span data-ttu-id="493c4-116">A versão colorida do seu ícone é exibida na maioria dos cenários Teams e deve ser de 192x192 pixels.</span><span class="sxs-lookup"><span data-stu-id="493c4-116">The color version of your icon displays in most Teams scenarios and must be 192x192 pixels.</span></span> <span data-ttu-id="493c4-117">Seu símbolo de ícone (96x96 pixels) pode ser de qualquer cor, mas deve sentar-se em um fundo quadrado sólido ou totalmente transparente.</span><span class="sxs-lookup"><span data-stu-id="493c4-117">Your icon symbol (96x96 pixels) can be any color, but it must sit on a solid or fully transparent square background.</span></span>

<span data-ttu-id="493c4-118">Teams planta automaticamente seu ícone para exibir um quadrado com cantos arredondados em vários cenários e uma forma hexagonal em cenários de bot.</span><span class="sxs-lookup"><span data-stu-id="493c4-118">Teams automatically crops your icon to display a square with rounded corners in multiple scenarios and a hexagonal shape in bot scenarios.</span></span> <span data-ttu-id="493c4-119">Para cortar o símbolo sem perder nenhum detalhe, inclua 48 pixels de preenchimento em torno de seu símbolo.</span><span class="sxs-lookup"><span data-stu-id="493c4-119">To crop the symbol without losing any detail, include 48 pixels of padding around your symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Teams ícone de cores e orientação de design." border="false":::

### <a name="outline-icon"></a><span data-ttu-id="493c4-121">Ícone de contorno</span><span class="sxs-lookup"><span data-stu-id="493c4-121">Outline icon</span></span>

<span data-ttu-id="493c4-122">Um ícone de contorno é exibido em dois cenários:</span><span class="sxs-lookup"><span data-stu-id="493c4-122">An outline icon displays in two scenarios:</span></span>

* <span data-ttu-id="493c4-123">Quando seu aplicativo está em uso e "içado" na barra de aplicativos no lado esquerdo de Teams.</span><span class="sxs-lookup"><span data-stu-id="493c4-123">When your app is in use and “hoisted” on the app bar on the left side of Teams.</span></span>
* <span data-ttu-id="493c4-124">Quando um usuário fixa a extensão de mensagens do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="493c4-124">When a user pins your app's messaging extension.</span></span>

<span data-ttu-id="493c4-125">O ícone deve ser de 32x32 pixels.</span><span class="sxs-lookup"><span data-stu-id="493c4-125">The icon must be 32x32 pixels.</span></span> <span data-ttu-id="493c4-126">Pode ser branco com um fundo transparente ou transparente com um fundo branco (nenhuma outra cor é permitida).</span><span class="sxs-lookup"><span data-stu-id="493c4-126">It can be white with a transparent background or transparent with a white background (no other colors are permitted).</span></span> <span data-ttu-id="493c4-127">O ícone de contorno não deve ter nenhum preenchimento extra em torno do símbolo.</span><span class="sxs-lookup"><span data-stu-id="493c4-127">The outline icon should not have any extra padding around the symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Teams orientação de design de ícones de contorno." border="false":::

### <a name="best-practices"></a><span data-ttu-id="493c4-129">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="493c4-129">Best practices</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Ilustração mostrando como projetar seus ícones de aplicativo." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a><span data-ttu-id="493c4-131">Faça: Siga as diretrizes precisas do ícone de contorno</span><span class="sxs-lookup"><span data-stu-id="493c4-131">Do: Follow the precise outline icon guidelines</span></span>

<span data-ttu-id="493c4-132">Os valores RGB de branco usados em seu ícone devem ser Vermelho: 255, Verde: 255, Azul: 255.</span><span class="sxs-lookup"><span data-stu-id="493c4-132">The RGB values of white used in your icon must be Red: 255, Green: 255, Blue: 255.</span></span> <span data-ttu-id="493c4-133">Todas as outras partes do ícone de contorno devem ser totalmente transparentes, com o canal alfa definido para 0.</span><span class="sxs-lookup"><span data-stu-id="493c4-133">All other parts of the outline icon must be fully transparent, with the alpha channel set to 0.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Ilustração mostrando como não projetar ícones do seu aplicativo." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a><span data-ttu-id="493c4-135">Não: Crop em uma forma quadrada circular ou arredondada</span><span class="sxs-lookup"><span data-stu-id="493c4-135">Don't: Crop in a circular or rounded square shape</span></span>

<span data-ttu-id="493c4-136">O ícone de cor enviado no pacote do aplicativo deve ser quadrado.</span><span class="sxs-lookup"><span data-stu-id="493c4-136">The color icon submitted in your app package must be square.</span></span> <span data-ttu-id="493c4-137">Não vire os cantos do seu ícone.</span><span class="sxs-lookup"><span data-stu-id="493c4-137">Don’t round the corners of your icon.</span></span> <span data-ttu-id="493c4-138">Teams ajusta automaticamente o raio do canto.</span><span class="sxs-lookup"><span data-stu-id="493c4-138">Teams automatically adjusts the corner radius.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a><span data-ttu-id="493c4-139">Não: Copie outras marcas</span><span class="sxs-lookup"><span data-stu-id="493c4-139">Don't: Copy other brands</span></span>

<span data-ttu-id="493c4-140">Seus ícones não devem imitar nenhum produto protegido por direitos autorais que você não possui.</span><span class="sxs-lookup"><span data-stu-id="493c4-140">Your icons must not mimic any copyrighted products that you don't own.</span></span> <span data-ttu-id="493c4-141">Por exemplo, um design semelhante a um produto ou marca da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="493c4-141">For example, a design similar to a Microsoft product or brand.</span></span>

### <a name="examples"></a><span data-ttu-id="493c4-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="493c4-142">Examples</span></span>

<span data-ttu-id="493c4-143">Veja como os ícones dos aplicativos aparecem em diferentes Teams recursos e contextos.</span><span class="sxs-lookup"><span data-stu-id="493c4-143">Here's how app icons appear in different Teams capabilities and contexts.</span></span>

#### <a name="personal-app"></a><span data-ttu-id="493c4-144">Aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="493c4-144">Personal app</span></span>

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo parece em um aplicativo pessoal." border="false":::

#### <a name="bot-channel"></a><span data-ttu-id="493c4-146">Bot (canal)</span><span class="sxs-lookup"><span data-stu-id="493c4-146">Bot (channel)</span></span>

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo fica em um bot dentro do canal." border="false":::

#### <a name="messaging-extension"></a><span data-ttu-id="493c4-148">Extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="493c4-148">Messaging extension</span></span>

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<>de texto alt " border="false":::

## <a name="next-step"></a><span data-ttu-id="493c4-150">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="493c4-150">Next step</span></span>

<span data-ttu-id="493c4-151">Escolha como planeja distribuir seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="493c4-151">Choose how you plan to distribute your app:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="493c4-152">Carregar lateralmente seu aplicativo em Teams</span><span class="sxs-lookup"><span data-stu-id="493c4-152">Sideload your app in Teams</span></span>](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="493c4-153">Publique seu aplicativo em sua organização</span><span class="sxs-lookup"><span data-stu-id="493c4-153">Publish your app to your org</span></span>](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [<span data-ttu-id="493c4-154">Publique seu aplicativo na loja</span><span class="sxs-lookup"><span data-stu-id="493c4-154">Publish your app to the store</span></span>](~/concepts/deploy-and-publish/appsource/publish.md)
