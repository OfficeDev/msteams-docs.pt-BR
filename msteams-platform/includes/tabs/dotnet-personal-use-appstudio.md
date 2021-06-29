## <a name="upload-your-tab-with-app-studio"></a><span data-ttu-id="3be7e-101">Upload sua guia com o App Studio</span><span class="sxs-lookup"><span data-stu-id="3be7e-101">Upload your tab with App Studio</span></span>

>[!NOTE]
> <span data-ttu-id="3be7e-102">Usamos **o App Studio** para editar seumanifest.js **no** arquivo e carregar o pacote concluído para Teams.</span><span class="sxs-lookup"><span data-stu-id="3be7e-102">We use **App Studio** to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="3be7e-103">Você também pode editar manualmente **manifest.jsem**.</span><span class="sxs-lookup"><span data-stu-id="3be7e-103">You can also manually edit **manifest.json**.</span></span> <span data-ttu-id="3be7e-104">Se fizer isso, certifique-se de criar a solução novamente para criar o arquivo **Tab.zip** para carregar.</span><span class="sxs-lookup"><span data-stu-id="3be7e-104">If you do, ensure that you build the solution again to create the **Tab.zip** file to upload.</span></span>

<span data-ttu-id="3be7e-105">**Para carregar sua guia com o App Studio**</span><span class="sxs-lookup"><span data-stu-id="3be7e-105">**To upload your tab with App Studio**</span></span>

1. <span data-ttu-id="3be7e-106">Vá para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3be7e-106">Go to Microsoft Teams.</span></span> <span data-ttu-id="3be7e-107">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="3be7e-107">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

1. <span data-ttu-id="3be7e-108">Vá para **o App Studio** e selecione a guia Editor **de** manifesto.</span><span class="sxs-lookup"><span data-stu-id="3be7e-108">Go to **App Studio** and select the **Manifest editor** tab.</span></span>

1. <span data-ttu-id="3be7e-109">Selecione **Importar um aplicativo existente** no editor de **Manifesto** para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente completo.</span><span class="sxs-lookup"><span data-stu-id="3be7e-109">Select **Import an existing app** in the **Manifest editor** to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="3be7e-110">O nome do pacote do aplicativo é **tab.zip**.</span><span class="sxs-lookup"><span data-stu-id="3be7e-110">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="3be7e-111">Ele está disponível no seguinte caminho:</span><span class="sxs-lookup"><span data-stu-id="3be7e-111">It is available from the following path:</span></span>

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

1. <span data-ttu-id="3be7e-112">Upload **tab.zip** App **Studio.**</span><span class="sxs-lookup"><span data-stu-id="3be7e-112">Upload **tab.zip** to **App Studio**.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="3be7e-113">Atualizar seu pacote de aplicativos com o editor de manifesto</span><span class="sxs-lookup"><span data-stu-id="3be7e-113">Update your app package with Manifest editor</span></span>

<span data-ttu-id="3be7e-114">Depois de carregar seu pacote de aplicativos no App Studio, você deve configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="3be7e-114">After you have uploaded your app package into App Studio, you must configure it.</span></span>

<span data-ttu-id="3be7e-115">Selecione o azulejo para sua guia recém-importada no painel direito da página de boas-vindas do editor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="3be7e-115">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="3be7e-116">Há uma lista de etapas no lado esquerdo do editor de Manifesto e, à direita, uma lista de propriedades que devem ter valores para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="3be7e-116">There is a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that must have values for each of those steps.</span></span> <span data-ttu-id="3be7e-117">Grande parte das informações foi fornecida pelo seumanifest.js **em,** mas há campos que você deve atualizar.</span><span class="sxs-lookup"><span data-stu-id="3be7e-117">Much of the information has been provided by your **manifest.json** but there are fields that you must update.</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="3be7e-118">Detalhes: Detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3be7e-118">Details: App details</span></span>

<span data-ttu-id="3be7e-119">Na seção **Detalhes do** aplicativo:</span><span class="sxs-lookup"><span data-stu-id="3be7e-119">In the **App details** section:</span></span>

1. <span data-ttu-id="3be7e-120">Em **Identificação**, selecione **Gerar** para gerar uma nova ID do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3be7e-120">Under **Identification**, select **Generate** to generate a new App Id for your app.</span></span>

1. <span data-ttu-id="3be7e-121">Em **Informações do desenvolvedor,** atualize o **Site** com sua URL HTTPS **ngrok.**</span><span class="sxs-lookup"><span data-stu-id="3be7e-121">Under **Developer information**, update the **Website** with your **ngrok** HTTPS URL.</span></span>

1. <span data-ttu-id="3be7e-122">Em **URLs do aplicativo,** atualize a **instrução Privacy** para `https://<yourngrokurl>/privacy` e Termos de **uso** para `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="3be7e-122">Under **App URLs**, update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="3be7e-123">Recursos: guias</span><span class="sxs-lookup"><span data-stu-id="3be7e-123">Capabilities: Tabs</span></span>

<span data-ttu-id="3be7e-124">Na seção **Guias:**</span><span class="sxs-lookup"><span data-stu-id="3be7e-124">In the **Tabs** section:</span></span>

1. <span data-ttu-id="3be7e-125">Em **Adicionar uma guia pessoal,** selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="3be7e-125">Under **Add a personal tab**, select **Add**.</span></span> <span data-ttu-id="3be7e-126">Uma caixa de diálogo pop-up é exibida.</span><span class="sxs-lookup"><span data-stu-id="3be7e-126">A pop-up dialog box appears.</span></span>

1. <span data-ttu-id="3be7e-127">Insira um nome para a guia pessoal em **Nome**.</span><span class="sxs-lookup"><span data-stu-id="3be7e-127">Enter a name for the personal tab in **Name**.</span></span>

1. <span data-ttu-id="3be7e-128">Insira a **ID da entidade**.</span><span class="sxs-lookup"><span data-stu-id="3be7e-128">Enter the **Entity ID**.</span></span>

1. <span data-ttu-id="3be7e-129">Atualizar **a URL de conteúdo** com `https://<yourngrokurl>/personalTab` .</span><span class="sxs-lookup"><span data-stu-id="3be7e-129">Update **Content URL** with `https://<yourngrokurl>/personalTab`.</span></span>

    <span data-ttu-id="3be7e-130">Deixe o **campo URL do site** em branco.</span><span class="sxs-lookup"><span data-stu-id="3be7e-130">Leave the **Website URL** field blank.</span></span>

1. <span data-ttu-id="3be7e-131">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="3be7e-131">Select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="3be7e-132">Concluir: domínios e permissões</span><span class="sxs-lookup"><span data-stu-id="3be7e-132">Finish: Domains and permissions</span></span>

<span data-ttu-id="3be7e-133">Na seção **Domínios e** permissões, o **campo Domínios** de suas guias deve conter sua URL ngrok sem o prefixo HTTPS `<yourngrokurl>.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="3be7e-133">In the **Domains and permissions** section, the **Domains from your tabs** field must contain your ngrok URL without the HTTPS prefix `<yourngrokurl>.ngrok.io/`.</span></span>

##### <a name="finish-test-and-distribute"></a><span data-ttu-id="3be7e-134">Concluir: Testar e distribuir</span><span class="sxs-lookup"><span data-stu-id="3be7e-134">Finish: Test and distribute</span></span>

>[!IMPORTANT]
> <span data-ttu-id="3be7e-135">À direita, em **Descrição,** você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="3be7e-135">On the right, in **Description**, you see the following warning:</span></span>
>
> <span data-ttu-id="3be7e-136">&#9888; A **matriz 'validDomains' não pode conter um site de tunelamento...**</span><span class="sxs-lookup"><span data-stu-id="3be7e-136">&#9888; **The 'validDomains' array cannot contain a tunneling site...**</span></span>
>
><span data-ttu-id="3be7e-137">Esse aviso pode ser ignorado durante o teste da guia.</span><span class="sxs-lookup"><span data-stu-id="3be7e-137">This warning can be ignored while testing your tab.</span></span>

1. <span data-ttu-id="3be7e-138">Na seção **Testar e Distribuir,** selecione **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="3be7e-138">In the **Test and Distribute** section, select **Install**.</span></span>

1. <span data-ttu-id="3be7e-139">Na caixa de diálogo pop-up, selecione **Adicionar** e sua guia é exibida com duas opções.</span><span class="sxs-lookup"><span data-stu-id="3be7e-139">In the pop-up dialog box, select **Add** and your tab is displayed with two options.</span></span>

1. <span data-ttu-id="3be7e-140">Nas opções na guia, escolha **Selecionar Cinza** ou **Selecionar Vermelho**.</span><span class="sxs-lookup"><span data-stu-id="3be7e-140">From the options in the tab, choose either **Select Gray** or **Select Red**.</span></span> <span data-ttu-id="3be7e-141">A guia é exibida de acordo com a cor selecionada.</span><span class="sxs-lookup"><span data-stu-id="3be7e-141">The tab is displayed according to the color you selected.</span></span>
 
    ![Guia pessoal ASPNETMVC carregada](../../assets/images/tab-images/personaltabaspnetmvcuploaded.png)

## <a name="view-your-personal-tab"></a><span data-ttu-id="3be7e-143">Exibir sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="3be7e-143">View your personal tab</span></span>

1. <span data-ttu-id="3be7e-144">Na barra de navegação localizada à extrema esquerda do aplicativo Teams, selecione as releições &#x25CF;&#x25CF;&#x25CF;.</span><span class="sxs-lookup"><span data-stu-id="3be7e-144">In the navigation bar located at the far left of the Teams app, select the ellipses &#x25CF;&#x25CF;&#x25CF;.</span></span> <span data-ttu-id="3be7e-145">Uma lista de aplicativos pessoais é mostrada.</span><span class="sxs-lookup"><span data-stu-id="3be7e-145">A list of personal apps is shown.</span></span>

1. <span data-ttu-id="3be7e-146">Selecione sua guia na lista para exibi-la.</span><span class="sxs-lookup"><span data-stu-id="3be7e-146">Select your tab from the list to view it.</span></span>
