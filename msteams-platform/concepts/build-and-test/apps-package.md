---
title: Empacotar seu aplicativo
description: Saiba como empacotar seu aplicativo para teste, upload e publicação no Microsoft Teams
keywords: pacote de aplicativos do teams
ms.topic: conceptual
ms.openlocfilehash: 66131f37f9f68c8fd54412d41068f6124da94453
ms.sourcegitcommit: 6c786434b56cc8c2765a14aa1f6149870245f309
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "44801038"
---
# <a name="create-an-app-package-for-your-microsoft-teams-app"></a><span data-ttu-id="f3fd4-104">Criar um pacote de aplicativos para seu aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f3fd4-104">Create an app package for your Microsoft Teams app</span></span>

<span data-ttu-id="f3fd4-105">Os aplicativos no Teams são definidos por um arquivo JSON de manifesto de aplicativo e agrupados em um pacote de aplicativos com seus ícones.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-105">Apps in Teams are defined by an app manifest JSON file, and bundled in an app package with their icons.</span></span> <span data-ttu-id="f3fd4-106">Você precisará de um pacote de aplicativos para carregar e instalar seu aplicativo no Microsoft Teams e publicar no catálogo de aplicativos de sua linha de negócios ou no AppSource.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-106">You'll need an app package to upload and install your app in Teams, and to publish to either your Line of Business app catalog or to AppSource.</span></span>

<span data-ttu-id="f3fd4-107">Um pacote de aplicativos do Microsoft Teams é um arquivo. zip que contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f3fd4-107">A Teams app package is a .zip file containing the following:</span></span>

* <span data-ttu-id="f3fd4-108">Um arquivo de manifesto chamado "manifest.js", que especifica os atributos do seu aplicativo e aponta para os recursos necessários para sua experiência, como o local da sua página de configuração da guia ou a ID do aplicativo da Microsoft para seu bot.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-108">A manifest file named "manifest.json", which specifies attributes of your app and points to required resources for your experience, such the location of its tab configuration page or the Microsoft app ID for its bot.</span></span>
* <span data-ttu-id="f3fd4-109">Um ícone de "estrutura de tópicos" transparente e um ícone de "cor" completo.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-109">A transparent "outline" icon and a full "color" icon.</span></span> <span data-ttu-id="f3fd4-110">Consulte os [ícones](#icons) mais adiante neste tópico para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-110">See [Icons](#icons) later in this topic for more information.</span></span>

## <a name="creating-a-manifest"></a><span data-ttu-id="f3fd4-111">Criar um manifesto</span><span class="sxs-lookup"><span data-stu-id="f3fd4-111">Creating a manifest</span></span>

<span data-ttu-id="f3fd4-112">O *Teams app Studio* pode ajudar a configurar seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-112">*Teams App Studio* can help configure your manifest.</span></span> <span data-ttu-id="f3fd4-113">Ele também contém uma biblioteca de controle React e amostras configuráveis para cartões.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-113">It also contains a React control library and configurable samples for cards.</span></span> <span data-ttu-id="f3fd4-114">Confira [visão geral do App Studio](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f3fd4-114">See [App Studio Overview](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="f3fd4-115">O arquivo de manifesto deve ser nomeado como "manifest.js" e estar no nível superior do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-115">Your manifest file must be named "manifest.json" and be at the top level of the upload package.</span></span> <span data-ttu-id="f3fd4-116">Observe que manifestos e pacotes criados anteriormente podem oferecer suporte a uma versão mais antiga do esquema.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-116">Note that manifests and packages built previously might support an older version of the schema.</span></span> <span data-ttu-id="f3fd4-117">Para aplicativos do Teams e especialmente o envio do AppSource (anteriormente Office Store), você deve usar o [esquema de manifesto](~/resources/schema/manifest-schema.md)atual.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-117">For Teams apps and especially AppSource (formerly Office Store) submission, you must use the current [manifest schema](~/resources/schema/manifest-schema.md).</span></span>

> [!TIP]
> <span data-ttu-id="f3fd4-118">Especifique o esquema no início do manifesto para habilitar o IntelliSense ou suporte semelhante do editor de código:</span><span class="sxs-lookup"><span data-stu-id="f3fd4-118">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor:</span></span>
>
> `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",`

## <a name="icons"></a><span data-ttu-id="f3fd4-119">Ícones</span><span class="sxs-lookup"><span data-stu-id="f3fd4-119">Icons</span></span>

> [!Note]
> <span data-ttu-id="f3fd4-120">Se seu aplicativo contiver um bot ou uma extensão de mensagens, os ícones usados serão os ícones carregados no seu registro de bot na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-120">If your app contains a bot or messaging extension, the icons used will be the icons uploaded to your bot registration in the Bot Framework.</span></span>

<span data-ttu-id="f3fd4-121">O Microsoft Teams requer dois ícones para a sua experiência de aplicativo, para serem usados no produto.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-121">Microsoft Teams requires two icons for your app experience, to be used within the product.</span></span> <span data-ttu-id="f3fd4-122">Os ícones devem ser incluídos no pacote e referenciados por meio de caminhos relativos no manifesto.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-122">Icons must be included in the package and referenced via relative paths in the manifest.</span></span> <span data-ttu-id="f3fd4-123">O comprimento máximo de cada caminho é de 2048 bytes, e o formato do ícone é. png.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-123">The maximum length of each path is 2048 bytes, and the format of the icon is .png.</span></span>

### <a name="color"></a><span data-ttu-id="f3fd4-124">color</span><span class="sxs-lookup"><span data-stu-id="f3fd4-124">color</span></span>

<span data-ttu-id="f3fd4-125">O `color` ícone é usado no Microsoft Teams (em aplicativos e galerias de guias, bots, submenus e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="f3fd4-125">The `color` icon is used throughout Microsoft Teams (in app and tab galleries, bots, flyouts, and so on).</span></span> <span data-ttu-id="f3fd4-126">Este ícone deve ser 192x192 pixels.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-126">This icon should be 192x192 pixels.</span></span> <span data-ttu-id="f3fd4-127">Seu ícone pode ser qualquer cor (ou cores), mas o plano de fundo deve ser a cor de destaque da marca.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-127">Your icon can be any color (or colors), but the background should be your branded accent color.</span></span> <span data-ttu-id="f3fd4-128">Ela também deve ter uma pequena quantidade de preenchimento em torno do ícone para acomodar o corte de hexágonos para a versão de bot do ícone.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-128">It should also have a small amount of padding surrounding the icon to accommodate the hexagonal cropping for the bot version of the icon.</span></span>

### <a name="outline"></a><span data-ttu-id="f3fd4-129">outline</span><span class="sxs-lookup"><span data-stu-id="f3fd4-129">outline</span></span>

<span data-ttu-id="f3fd4-130">O `outline` ícone é usado nestes lugares: a barra de aplicativos e as extensões de mensagens que o usuário marcou como "favorito".</span><span class="sxs-lookup"><span data-stu-id="f3fd4-130">The `outline` icon is used in these places: the app bar and messaging extensions the user has marked as a "favorite."</span></span> <span data-ttu-id="f3fd4-131">Este ícone deve ter 32x32 pixels.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-131">This icon must be 32x32 pixels.</span></span> <span data-ttu-id="f3fd4-132">O ícone de estrutura de tópicos deve conter somente branco e transparência (sem outras cores).</span><span class="sxs-lookup"><span data-stu-id="f3fd4-132">Your outline icon must contain only white and transparency (no other colors).</span></span> <span data-ttu-id="f3fd4-133">O ícone pode ser branco com um plano de fundo transparente ou transparente com um plano de fundo branco.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-133">The icon can be white with transparent background or transparent with a white background.</span></span> <span data-ttu-id="f3fd4-134">O ícone de estrutura de tópicos não deve ter preenchimento adicional ao redor do ícone e deve ser tão cortado possível e ainda manter as dimensões de 32x32.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-134">The outline icon should not have extra padding surrounding the icon and should be as tightly cropped as possible while still maintaining the 32x32 dimensions.</span></span> <span data-ttu-id="f3fd4-135">Veja alguns exemplos bons:</span><span class="sxs-lookup"><span data-stu-id="f3fd4-135">Here are a few good examples:</span></span>

![Exemplos de ícones de tópicos](~/assets/images/icons/sample20x20s.png)

<span data-ttu-id="f3fd4-137">Por exemplo, digamos que sua empresa seja contoso.</span><span class="sxs-lookup"><span data-stu-id="f3fd4-137">For example, say your company is Contoso.</span></span> <span data-ttu-id="f3fd4-138">Você enviaria dois ícones:</span><span class="sxs-lookup"><span data-stu-id="f3fd4-138">You'd submit two icons:</span></span>

![Apresentação de ícones](~/assets/images/framework/framework_submit_icon.png)

<span data-ttu-id="f3fd4-140">Veja como os ícones aparecerão na interface do usuário:</span><span class="sxs-lookup"><span data-stu-id="f3fd4-140">Here's how the icons would appear in the UI:</span></span>

#### <a name="bot-and-chiclet-in-channel-view"></a><span data-ttu-id="f3fd4-141">Bot e Chiclet no modo de exibição de canal</span><span class="sxs-lookup"><span data-stu-id="f3fd4-141">Bot and chiclet in Channel view</span></span>

![Bot e UX do Chiclet](~/assets/images/icons/botandchiclet.png)

#### <a name="flyout"></a><span data-ttu-id="f3fd4-143">Janelas</span><span class="sxs-lookup"><span data-stu-id="f3fd4-143">Flyout</span></span>

![Exemplo de ícones da contoso](~/assets/images/icons/flyout.png)

#### <a name="app-bar-and-home-screen"></a><span data-ttu-id="f3fd4-145">Barra de aplicativos e tela inicial</span><span class="sxs-lookup"><span data-stu-id="f3fd4-145">App bar and home screen</span></span>

![Exemplo de ícones da contoso](~/assets/images/icons/appbarhomescreen.png)
