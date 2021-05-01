---
title: Empacote seu aplicativo
description: Saiba como empacotar seu aplicativo Microsoft Teams para testar, carregar e armazenar publicação.
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: e477539a9b8eaa0c869a2070fcd20b74aecfe490
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101699"
---
# <a name="create-a-microsoft-teams-app-package"></a><span data-ttu-id="80edc-103">Criar um pacote Microsoft Teams aplicativo</span><span class="sxs-lookup"><span data-stu-id="80edc-103">Create a Microsoft Teams app package</span></span>

<span data-ttu-id="80edc-104">Você precisa de um pacote de aplicativos, no entanto, planeja distribuir seu Microsoft Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80edc-104">You need an app package however you plan to distribute your Microsoft Teams app.</span></span> <span data-ttu-id="80edc-105">Um pacote válido é um arquivo ZIP que contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="80edc-105">A valid package is a ZIP file that contains the following:</span></span>

* <span data-ttu-id="80edc-106">**Manifesto do aplicativo**: descreve como seu aplicativo está configurado, incluindo seus recursos, recursos necessários e outros atributos importantes.</span><span class="sxs-lookup"><span data-stu-id="80edc-106">**App manifest**: Describes how your app is configured, including its capabilities, required resources, and other important attributes.</span></span>
* <span data-ttu-id="80edc-107">**Ícones do aplicativo:** cada pacote requer uma cor e um ícone de contorno para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80edc-107">**App icons**: Each package requires a color and outline icon for your app.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="80edc-108">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="80edc-108">App manifest</span></span>

<span data-ttu-id="80edc-109">O arquivo de manifesto do aplicativo deve estar no nível superior do pacote com o nome `manifest.json` .</span><span class="sxs-lookup"><span data-stu-id="80edc-109">Your app manifest file must be at the top level of the package with the name `manifest.json`.</span></span> 

<span data-ttu-id="80edc-110">Ao publicar no Teams, certifique-se de que seu manifesto faça referência ao [esquema mais recente.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="80edc-110">When publishing to the Teams store, make sure your manifest references the latest [schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="app-icons"></a><span data-ttu-id="80edc-111">Ícones de aplicativo</span><span class="sxs-lookup"><span data-stu-id="80edc-111">App icons</span></span>

<span data-ttu-id="80edc-112">Seu pacote de aplicativos deve incluir duas versões PNG do ícone do aplicativo: uma versão de cor e de contorno.</span><span class="sxs-lookup"><span data-stu-id="80edc-112">Your app package must include two PNG versions of your app icon: A color and outline version.</span></span>

> [!Note]
> <span data-ttu-id="80edc-113">Se seu aplicativo tiver um bot ou uma extensão de mensagens, seus ícones também serão incluídos no registro do serviço Microsoft Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="80edc-113">If your app has a bot or messaging extension, your icons also will be included in your Microsoft Azure Bot Service registration.</span></span>

<span data-ttu-id="80edc-114">Para que seu aplicativo passe na Teams de armazenamento, esses ícones devem atender aos seguintes requisitos de tamanho.</span><span class="sxs-lookup"><span data-stu-id="80edc-114">For your app to pass Teams store review, these icons must meet the following size requirements.</span></span>

### <a name="color-icon"></a><span data-ttu-id="80edc-115">Ícone de cor</span><span class="sxs-lookup"><span data-stu-id="80edc-115">Color icon</span></span>

<span data-ttu-id="80edc-116">A versão colorida do ícone é exibida na maioria Teams cenários e deve ter 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="80edc-116">The color version of your icon displays in most Teams scenarios and must be 192x192 pixels.</span></span> <span data-ttu-id="80edc-117">Seu símbolo de ícone (96 x 96 pixels) pode ser qualquer cor, mas deve estar em um plano de fundo quadrado sólido ou totalmente transparente.</span><span class="sxs-lookup"><span data-stu-id="80edc-117">Your icon symbol (96x96 pixels) can be any color, but it must sit on a solid or fully transparent square background.</span></span>

<span data-ttu-id="80edc-118">Teams automaticamente seu ícone para exibir um quadrado com cantos arredondados em vários cenários e uma forma hexagonal em cenários de bot.</span><span class="sxs-lookup"><span data-stu-id="80edc-118">Teams automatically crops your icon to display a square with rounded corners in multiple scenarios and a hexagonal shape in bot scenarios.</span></span> <span data-ttu-id="80edc-119">Para cortar o símbolo sem perder detalhes, inclua 48 pixels de preenchimento ao redor do símbolo.</span><span class="sxs-lookup"><span data-stu-id="80edc-119">To crop the symbol without losing any detail, include 48 pixels of padding around your symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Teams de cores e diretrizes de design." border="false":::

### <a name="outline-icon"></a><span data-ttu-id="80edc-121">Ícone de contorno</span><span class="sxs-lookup"><span data-stu-id="80edc-121">Outline icon</span></span>

<span data-ttu-id="80edc-122">Um ícone de contorno é exibido em dois cenários:</span><span class="sxs-lookup"><span data-stu-id="80edc-122">An outline icon displays in two scenarios:</span></span>

* <span data-ttu-id="80edc-123">Quando seu aplicativo estiver em uso e "içada" na barra de aplicativos no lado esquerdo do Teams.</span><span class="sxs-lookup"><span data-stu-id="80edc-123">When your app is in use and “hoisted” on the app bar on the left side of Teams.</span></span>
* <span data-ttu-id="80edc-124">Quando um usuário fixa a extensão de mensagens do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80edc-124">When a user pins your app's messaging extension.</span></span>

<span data-ttu-id="80edc-125">O ícone deve ter 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="80edc-125">The icon must be 32x32 pixels.</span></span> <span data-ttu-id="80edc-126">Ele pode ser branco com um plano de fundo transparente ou transparente com um plano de fundo branco (nenhuma outra cor é permitida).</span><span class="sxs-lookup"><span data-stu-id="80edc-126">It can be white with a transparent background or transparent with a white background (no other colors are permitted).</span></span> <span data-ttu-id="80edc-127">O ícone de contorno não deve ter nenhum preenchimento extra ao redor do símbolo.</span><span class="sxs-lookup"><span data-stu-id="80edc-127">The outline icon should not have any extra padding around the symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Teams diretrizes de design de ícone de estrutura." border="false":::

### <a name="best-practices"></a><span data-ttu-id="80edc-129">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="80edc-129">Best practices</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Ilustração mostrando como projetar ícones do aplicativo." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a><span data-ttu-id="80edc-131">Fazer: siga as diretrizes precisas do ícone de contorno</span><span class="sxs-lookup"><span data-stu-id="80edc-131">Do: Follow the precise outline icon guidelines</span></span>

<span data-ttu-id="80edc-132">Os valores RGB de branco usados em seu ícone devem ser Vermelho: 255, Verde: 255, Azul: 255.</span><span class="sxs-lookup"><span data-stu-id="80edc-132">The RGB values of white used in your icon must be Red: 255, Green: 255, Blue: 255.</span></span> <span data-ttu-id="80edc-133">Todas as outras partes do ícone de contorno devem ser totalmente transparentes, com o canal alfa definido como 0.</span><span class="sxs-lookup"><span data-stu-id="80edc-133">All other parts of the outline icon must be fully transparent, with the alpha channel set to 0.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Ilustração mostrando como não projetar ícones do aplicativo." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a><span data-ttu-id="80edc-135">Não: Corte em uma forma quadrada circular ou arredondada</span><span class="sxs-lookup"><span data-stu-id="80edc-135">Don't: Crop in a circular or rounded square shape</span></span>

<span data-ttu-id="80edc-136">O ícone de cor enviado no pacote do aplicativo deve ser quadrado.</span><span class="sxs-lookup"><span data-stu-id="80edc-136">The color icon submitted in your app package must be square.</span></span> <span data-ttu-id="80edc-137">Não arredonde os cantos do ícone.</span><span class="sxs-lookup"><span data-stu-id="80edc-137">Don’t round the corners of your icon.</span></span> <span data-ttu-id="80edc-138">Teams ajusta automaticamente o raio do canto.</span><span class="sxs-lookup"><span data-stu-id="80edc-138">Teams automatically adjusts the corner radius.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="dont-copy-other-brands"></a><span data-ttu-id="80edc-139">Não: copiar outras marcas</span><span class="sxs-lookup"><span data-stu-id="80edc-139">Don't: Copy other brands</span></span>

<span data-ttu-id="80edc-140">Seus ícones não devem imitar produtos protegidos por direitos autorais que você não possui (por exemplo, um design semelhante a um produto ou marca da Microsoft).</span><span class="sxs-lookup"><span data-stu-id="80edc-140">Your icons must not mimic any copyrighted products that you don't own (for example, a design similar to a Microsoft product or brand).</span></span>

### <a name="examples"></a><span data-ttu-id="80edc-141">Exemplos</span><span class="sxs-lookup"><span data-stu-id="80edc-141">Examples</span></span>

<span data-ttu-id="80edc-142">Veja como os ícones de aplicativo aparecem em diferentes Teams recursos e contextos.</span><span class="sxs-lookup"><span data-stu-id="80edc-142">Here's how app icons appear in different Teams capabilities and contexts.</span></span>

#### <a name="personal-app"></a><span data-ttu-id="80edc-143">Aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="80edc-143">Personal app</span></span>

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Exemplo mostrando a aparência de um ícone de aplicativo em um aplicativo pessoal." border="false":::

#### <a name="bot-channel"></a><span data-ttu-id="80edc-145">Bot (canal)</span><span class="sxs-lookup"><span data-stu-id="80edc-145">Bot (channel)</span></span>

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo fica em um bot dentro do canal." border="false":::

#### <a name="messaging-extension"></a><span data-ttu-id="80edc-147">Extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="80edc-147">Messaging extension</span></span>

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<texto alt>" border="false":::

## <a name="next-step"></a><span data-ttu-id="80edc-149">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="80edc-149">Next step</span></span>

<span data-ttu-id="80edc-150">Escolha como você planeja distribuir seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="80edc-150">Choose how you plan to distribute your app:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="80edc-151">Fazer sideload do aplicativo Teams</span><span class="sxs-lookup"><span data-stu-id="80edc-151">Sideload your app in Teams</span></span>](~/concepts/deploy-and-publish/apps-upload.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="80edc-152">Publicar seu aplicativo em sua organização</span><span class="sxs-lookup"><span data-stu-id="80edc-152">Publish your app to your org</span></span>](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
> [!div class="nextstepaction"]
> [<span data-ttu-id="80edc-153">Publicar seu aplicativo na loja</span><span class="sxs-lookup"><span data-stu-id="80edc-153">Publish your app to the store</span></span>](~/concepts/deploy-and-publish/appsource/publish.md)
