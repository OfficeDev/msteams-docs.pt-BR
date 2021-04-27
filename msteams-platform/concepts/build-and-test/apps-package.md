---
title: Empacote seu aplicativo
description: Saiba como empacotar seu aplicativo do Microsoft Teams para testar, carregar e armazenar publicação.
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: c8341f3d83b5e6610e44276d6732affa1d1c1e91
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020137"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a><span data-ttu-id="2c46e-103">Criar um pacote de aplicativos para seu aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="2c46e-103">Create an app package for your Microsoft Teams app</span></span>

<span data-ttu-id="2c46e-104">Os aplicativos no Teams são definidos por um arquivo JSON de manifesto do aplicativo e agrupados em um pacote de aplicativos com seus ícones.</span><span class="sxs-lookup"><span data-stu-id="2c46e-104">Apps in Teams are defined by an app manifest JSON file, and bundled in an app package with their icons.</span></span> <span data-ttu-id="2c46e-105">Você precisará de um pacote de aplicativos para carregar e instalar seu aplicativo no Teams e publicar no catálogo de aplicativos linha de negócios ou no AppSource.</span><span class="sxs-lookup"><span data-stu-id="2c46e-105">You'll need an app package to upload and install your app in Teams and publish to either your Line of Business app catalog or to AppSource.</span></span>

<span data-ttu-id="2c46e-106">Um pacote de aplicativos do Teams é um arquivo .zip que contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2c46e-106">A Teams app package is a .zip file containing the following:</span></span>

* <span data-ttu-id="2c46e-107">Um arquivo de manifesto chamado , que especifica atributos do seu aplicativo e aponta para os recursos necessários para sua experiência, como o local de sua página de configuração de tabulação ou a ID do aplicativo Microsoft para seu `manifest.json` bot.</span><span class="sxs-lookup"><span data-stu-id="2c46e-107">A manifest file named `manifest.json`, which specifies attributes of your app and points to required resources for your experience, such the location of its tab configuration page or the Microsoft app ID for its bot.</span></span>
* <span data-ttu-id="2c46e-108">[Ícones de cor e de contorno para seu aplicativo](#app-icons).</span><span class="sxs-lookup"><span data-stu-id="2c46e-108">[Color and outline icons for your app](#app-icons).</span></span>

## <a name="creating-a-manifest"></a><span data-ttu-id="2c46e-109">Criando um manifesto</span><span class="sxs-lookup"><span data-stu-id="2c46e-109">Creating a manifest</span></span>

<span data-ttu-id="2c46e-110">**O Teams App Studio** pode ajudar a configurar seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="2c46e-110">**Teams App Studio** can help configure your manifest.</span></span> <span data-ttu-id="2c46e-111">Ele também contém uma biblioteca de controle React e amostras configuráveis para cartões.</span><span class="sxs-lookup"><span data-stu-id="2c46e-111">It also contains a React control library and configurable samples for cards.</span></span> <span data-ttu-id="2c46e-112">Para obter mais informações, consulte [Visão geral do App Studio](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2c46e-112">For more information, see [App Studio Overview](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="2c46e-113">Seu arquivo de manifesto deve ser chamado de "manifest.json" e estar no nível superior do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="2c46e-113">Your manifest file must be named "manifest.json" and be at the top level of the upload package.</span></span> <span data-ttu-id="2c46e-114">Observe que manifestos e pacotes construídos anteriormente podem dar suporte a uma versão mais antiga do esquema.</span><span class="sxs-lookup"><span data-stu-id="2c46e-114">Note that manifests and packages built previously might support an older version of the schema.</span></span> <span data-ttu-id="2c46e-115">Para aplicativos do Teams e especialmente o envio do AppSource (antigo Office Store), você deve usar o esquema de [manifesto atual.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="2c46e-115">For Teams apps and especially AppSource (formerly Office Store) submission, you must use the current [manifest schema](~/resources/schema/manifest-schema.md).</span></span>

> [!TIP]
> <span data-ttu-id="2c46e-116">Especifique o esquema no início do manifesto para habilitar IntelliSense suporte semelhante do editor de código:</span><span class="sxs-lookup"><span data-stu-id="2c46e-116">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor:</span></span>
>
> `"$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.9/MicrosoftTeams.schema.json",`
 
## <a name="app-icons"></a><span data-ttu-id="2c46e-117">Ícones de aplicativo</span><span class="sxs-lookup"><span data-stu-id="2c46e-117">App icons</span></span>

<span data-ttu-id="2c46e-118">Seu pacote de aplicativos deve incluir duas versões PNG do ícone do aplicativo: um ícone de cor e um ícone de contorno.</span><span class="sxs-lookup"><span data-stu-id="2c46e-118">Your app package must include two PNG versions of your app icon—a color icon and an outline icon.</span></span> <span data-ttu-id="2c46e-119">Para que seu aplicativo passe na revisão do AppSource, esses ícones devem atender aos seguintes requisitos de tamanho.</span><span class="sxs-lookup"><span data-stu-id="2c46e-119">For your app to pass the AppSource review, these icons must meet the following size requirements.</span></span>

> [!Note]
> <span data-ttu-id="2c46e-120">Se seu aplicativo tiver um bot ou extensão de mensagens, seus ícones também serão incluídos no registro do Serviço de Bot do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="2c46e-120">If your app has a bot or messaging extension, your icons also will be included in your Microsoft Azure Bot Service registration.</span></span>

### <a name="color-icon"></a><span data-ttu-id="2c46e-121">Ícone de cor</span><span class="sxs-lookup"><span data-stu-id="2c46e-121">Color icon</span></span>

<span data-ttu-id="2c46e-122">A versão colorida do ícone é exibida na maioria dos cenários do Teams e deve ter 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="2c46e-122">The color version of your icon displays in most Teams scenarios and must be 192x192 pixels.</span></span> <span data-ttu-id="2c46e-123">Seu símbolo de ícone (96 x 96 pixels) pode ser qualquer cor ou cores, mas deve estar em um plano de fundo quadrado sólido ou totalmente transparente.</span><span class="sxs-lookup"><span data-stu-id="2c46e-123">Your icon symbol (96x96 pixels) can be any color or colors, but it must sit on a solid or fully transparent square background.</span></span>

<span data-ttu-id="2c46e-124">O Teams cria automaticamente seu ícone para exibir um quadrado com cantos arredondados em vários cenários e uma forma hexagonal em cenários de bot.</span><span class="sxs-lookup"><span data-stu-id="2c46e-124">Teams automatically crops your icon to display a square with rounded corners in multiple scenarios and a hexagonal shape in bot scenarios.</span></span> <span data-ttu-id="2c46e-125">Inclua 48 pixels de preenchimento ao redor do símbolo para que essas colheitas possam ser feitas sem perder detalhes.</span><span class="sxs-lookup"><span data-stu-id="2c46e-125">Include 48 pixels of padding around your symbol so these crops can be made without losing any detail.</span></span>

:::image type="content" source="../../assets/images/icons/design-color-icon.png" alt-text="Ícone de cores e diretrizes de design do Teams." border="false":::

### <a name="outline-icon"></a><span data-ttu-id="2c46e-127">Ícone de contorno</span><span class="sxs-lookup"><span data-stu-id="2c46e-127">Outline icon</span></span>

<span data-ttu-id="2c46e-128">Um ícone de contorno é exibido em dois cenários:</span><span class="sxs-lookup"><span data-stu-id="2c46e-128">An outline icon displays in two scenarios:</span></span>

* <span data-ttu-id="2c46e-129">Quando seu aplicativo está em uso e "içada" na barra de aplicativos à esquerda do Teams.</span><span class="sxs-lookup"><span data-stu-id="2c46e-129">When your app is in use and “hoisted” on the app bar on the left of Teams.</span></span>
* <span data-ttu-id="2c46e-130">quando um usuário fixa a extensão de mensagens do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c46e-130">when a user pins your app's messaging extension.</span></span>

<span data-ttu-id="2c46e-131">O ícone deve ter 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="2c46e-131">The icon must be 32x32 pixels.</span></span> <span data-ttu-id="2c46e-132">Ele pode ser branco com um plano de fundo transparente ou transparente com um plano de fundo branco (nenhuma outra cor é permitida).</span><span class="sxs-lookup"><span data-stu-id="2c46e-132">It can be white with a transparent background or transparent with a white background (no other colors are permitted).</span></span> <span data-ttu-id="2c46e-133">O ícone de contorno não deve ter nenhum preenchimento extra ao redor do símbolo.</span><span class="sxs-lookup"><span data-stu-id="2c46e-133">The outline icon should not have any extra padding around the symbol.</span></span>

:::image type="content" source="../../assets/images/icons/design-outline-icon.png" alt-text="Diretrizes de design de ícone de estrutura do Teams." border="false":::

### <a name="best-practices"></a><span data-ttu-id="2c46e-135">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="2c46e-135">Best practices</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-do.png" alt-text="Ilustração mostrando como projetar ícones do aplicativo." border="false":::

#### <a name="do-follow-the-precise-outline-icon-guidelines"></a><span data-ttu-id="2c46e-137">Fazer: siga as diretrizes precisas do ícone de contorno</span><span class="sxs-lookup"><span data-stu-id="2c46e-137">Do: Follow the precise outline icon guidelines</span></span>

<span data-ttu-id="2c46e-138">Os valores RGB de branco usados em seu ícone devem ser Vermelho: 255, Verde: 255, Azul: 255.</span><span class="sxs-lookup"><span data-stu-id="2c46e-138">The RGB values of white used in your icon must be Red: 255, Green: 255, Blue: 255.</span></span> <span data-ttu-id="2c46e-139">Todas as outras partes do ícone de contorno devem ser totalmente transparentes, com o canal alfa definido como 0.</span><span class="sxs-lookup"><span data-stu-id="2c46e-139">All other parts of the outline icon must be fully transparent, with the alpha channel set to 0.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/icons/design-icon-dont.png" alt-text="Ilustração mostrando como não projetar ícones do aplicativo." border="false":::

#### <a name="dont-crop-in-a-circular-or-rounded-square-shape"></a><span data-ttu-id="2c46e-141">Não: Corte em uma forma quadrada circular ou arredondada</span><span class="sxs-lookup"><span data-stu-id="2c46e-141">Don't: Crop in a circular or rounded square shape</span></span>

<span data-ttu-id="2c46e-142">O ícone de cor enviado no pacote do aplicativo deve ser quadrado.</span><span class="sxs-lookup"><span data-stu-id="2c46e-142">The color icon submitted in your app package must be square.</span></span> <span data-ttu-id="2c46e-143">Não arredonde os cantos do ícone.</span><span class="sxs-lookup"><span data-stu-id="2c46e-143">Don’t round the corners of your icon.</span></span> <span data-ttu-id="2c46e-144">O Teams ajusta automaticamente o raio de canto.</span><span class="sxs-lookup"><span data-stu-id="2c46e-144">Teams automatically adjusts the corner radius.</span></span>

   :::column-end:::
:::row-end:::

### <a name="examples"></a><span data-ttu-id="2c46e-145">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2c46e-145">Examples</span></span>

<span data-ttu-id="2c46e-146">Veja como os ícones de aplicativo aparecem em diferentes recursos e contextos do Teams.</span><span class="sxs-lookup"><span data-stu-id="2c46e-146">Here's how app icons appear in different Teams capabilities and contexts.</span></span>

#### <a name="personal-app"></a><span data-ttu-id="2c46e-147">Aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="2c46e-147">Personal app</span></span>

:::image type="content" source="../../assets/images/icons/personal-app-icon-example.png" alt-text="Exemplo mostrando a aparência de um ícone de aplicativo em um aplicativo pessoal." border="false":::

#### <a name="bot-channel"></a><span data-ttu-id="2c46e-149">Bot (canal)</span><span class="sxs-lookup"><span data-stu-id="2c46e-149">Bot (channel)</span></span>

:::image type="content" source="../../assets/images/icons/bot-icon-example.png" alt-text="Exemplo mostrando como um ícone de aplicativo fica em um bot dentro do canal." border="false":::

#### <a name="messaging-extension"></a><span data-ttu-id="2c46e-151">Extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="2c46e-151">Messaging extension</span></span>

:::image type="content" source="../../assets/images/icons/messaging-extension-icon-example.png" alt-text="<texto alt>" border="false":::
