## <a name="upload-your-tab-to-teams-with-app-studio"></a><span data-ttu-id="98c40-101">Upload sua guia para Teams com o App Studio</span><span class="sxs-lookup"><span data-stu-id="98c40-101">Upload your tab to Teams with App Studio</span></span>

>[!NOTE]
> <span data-ttu-id="98c40-102">Usamos o App Studio para editar sua **manifest.jsno** arquivo e carregar o pacote completo para Teams.</span><span class="sxs-lookup"><span data-stu-id="98c40-102">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="98c40-103">Você também pode editar manualmente **manifest.js** se preferir.</span><span class="sxs-lookup"><span data-stu-id="98c40-103">You can also manually edit **manifest.json** if you prefer.</span></span> <span data-ttu-id="98c40-104">Se você fizer isso, certifique-se de construir a solução novamente para criar o **arquivoTab.zip** para carregar.</span><span class="sxs-lookup"><span data-stu-id="98c40-104">If you do, be sure to build the solution again to create the **Tab.zip** file to upload.</span></span>

- <span data-ttu-id="98c40-105">Abra o cliente Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="98c40-105">Open the Microsoft Teams client.</span></span> <span data-ttu-id="98c40-106">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) você pode inspecionar seu código frontal usando [as ferramentas](~/tabs/how-to/developer-tools.md)de desenvolvedor do seu navegador .</span><span class="sxs-lookup"><span data-stu-id="98c40-106">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="98c40-107">Abra o estúdio App e selecione a guia **Do editor Manifest.**</span><span class="sxs-lookup"><span data-stu-id="98c40-107">Open App studio and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="98c40-108">Selecione **a máquina de importar um aplicativo existente** no editor Manifest para começar a atualizar o pacote de aplicativos para sua guia. O código fonte vem com seu próprio manifesto parcialmente completo.</span><span class="sxs-lookup"><span data-stu-id="98c40-108">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="98c40-109">O nome do seu pacote de aplicativos é **tab.zip**.</span><span class="sxs-lookup"><span data-stu-id="98c40-109">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="98c40-110">Deve ser encontrado aqui:</span><span class="sxs-lookup"><span data-stu-id="98c40-110">It should be found here:</span></span>

    ```bash
    /bin/Debug/netcoreapp2.2/Tab.zip
    ```

- <span data-ttu-id="98c40-111">Upload **Tab.zip** para o App Studio.</span><span class="sxs-lookup"><span data-stu-id="98c40-111">Upload **Tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="98c40-112">Atualize seu pacote de aplicativos com o editor manifest</span><span class="sxs-lookup"><span data-stu-id="98c40-112">Update your app package with Manifest editor</span></span>

<span data-ttu-id="98c40-113">Depois de carregar seu pacote de aplicativos no App Studio, você precisará terminar de configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="98c40-113">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="98c40-114">Selecione a telha para sua guia recém-importada no painel direito da página de boas-vindas do editor Manifest.</span><span class="sxs-lookup"><span data-stu-id="98c40-114">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="98c40-115">Há uma lista de passos no lado esquerdo do editor do Manifest, e à direita, uma lista de propriedades que precisam ter valores para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="98c40-115">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="98c40-116">Muitas das informações foram fornecidas pelo seu *manifest.js,* mas existem alguns campos que você precisará atualizar:</span><span class="sxs-lookup"><span data-stu-id="98c40-116">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="98c40-117">Detalhes: Detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="98c40-117">Details: App details</span></span>

<span data-ttu-id="98c40-118">Na seção detalhes do **Aplicativo:**</span><span class="sxs-lookup"><span data-stu-id="98c40-118">In the **App details** section:</span></span>

- <span data-ttu-id="98c40-119">Em **Identificação** selecione **Gerar** para gerar um novo App ID para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98c40-119">Under **Identification** select **Generate** to generate a new App Id for your app.</span></span>

- <span data-ttu-id="98c40-120">Em **informações do Desenvolvedor,** atualize a **URL do site** com sua URL **HTTPS ngrok.**</span><span class="sxs-lookup"><span data-stu-id="98c40-120">Under **Developer information** update the **Website URL** with your **ngrok** HTTPS URL.</span></span>

- <span data-ttu-id="98c40-121">De acordo com **os URLs** do App, atualize a **declaração** de Privacidade `https://<yourngrokurl>/privacy` e os Termos de **uso** para `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="98c40-121">Under **App URLs** update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="98c40-122">Recursos: Guias</span><span class="sxs-lookup"><span data-stu-id="98c40-122">Capabilities: Tabs</span></span>

<span data-ttu-id="98c40-123">Na seção *Guias:*</span><span class="sxs-lookup"><span data-stu-id="98c40-123">In the *Tabs* section:</span></span>

- <span data-ttu-id="98c40-124">Em **Adicionar uma guia pessoal** selecionar **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="98c40-124">Under **Add a personal tab** select **Add**.</span></span> <span data-ttu-id="98c40-125">Você será presenteado com uma janela de diálogo pop-up.</span><span class="sxs-lookup"><span data-stu-id="98c40-125">You will be presented with a pop-up dialogue window.</span></span>

- <span data-ttu-id="98c40-126">Complete o campo **Nome.**</span><span class="sxs-lookup"><span data-stu-id="98c40-126">Complete the **Name** field.</span></span>

- <span data-ttu-id="98c40-127">Complete o campo **de identidade da entidade.**</span><span class="sxs-lookup"><span data-stu-id="98c40-127">Complete the **Entity Id** field.</span></span>

- <span data-ttu-id="98c40-128">Atualize o campo **URL de conteúdo** com `https://<yourngrokurl>/personalTab` .</span><span class="sxs-lookup"><span data-stu-id="98c40-128">Update the **Content URL** field with to `https://<yourngrokurl>/personalTab`.</span></span>

- <span data-ttu-id="98c40-129">Deixe o campo url do **site** em branco.</span><span class="sxs-lookup"><span data-stu-id="98c40-129">Leave the **Website URL** field blank.</span></span>

- <span data-ttu-id="98c40-130">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="98c40-130">Select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="98c40-131">Acabamento: Domínios e permissões</span><span class="sxs-lookup"><span data-stu-id="98c40-131">Finish: Domains and permissions</span></span>

<span data-ttu-id="98c40-132">Na seção **Domínios e permissões,** os domínios do campo **de guias** devem conter sua URL ngrok sem o prefixo HTTPS - `<yourngrokurl>.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="98c40-132">In the **Domains and permissions** section, the **Domains from your tabs** field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

##### <a name="finish-test-and-distribute"></a><span data-ttu-id="98c40-133">Acabamento: Teste e distribua</span><span class="sxs-lookup"><span data-stu-id="98c40-133">Finish: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="98c40-134">No campo **Descrição** à direita você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="98c40-134">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="98c40-135">&#9888; "**A matriz 'validDomains' não pode conter um local de tunelamento...**"</span><span class="sxs-lookup"><span data-stu-id="98c40-135">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="98c40-136">Este aviso pode ser ignorado durante o teste da sua guia.</span><span class="sxs-lookup"><span data-stu-id="98c40-136">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="98c40-137">Na seção **Teste e distribua:**</span><span class="sxs-lookup"><span data-stu-id="98c40-137">In the **Test and distribute** section:</span></span>

- <span data-ttu-id="98c40-138">Selecionar **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="98c40-138">Select **Install**.</span></span>

- <span data-ttu-id="98c40-139">Na janela pop-up certifique-se de que **Adicionar para você** está definido como **Sim** e Adicionar a uma equipe **ou bate-papo** está definido como **No**.</span><span class="sxs-lookup"><span data-stu-id="98c40-139">In the pop-up window make sure that **Add for you** is set to **Yes** and **Add to a team or chat** is set to **No**.</span></span>

- <span data-ttu-id="98c40-140">Selecionar **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="98c40-140">Select **Install**.</span></span>

- <span data-ttu-id="98c40-141">Na próxima janela pop-up selecione **Abrir** e sua guia será exibida.</span><span class="sxs-lookup"><span data-stu-id="98c40-141">In the next pop-up window select **Open** and your tab will be displayed.</span></span>

## <a name="view-your-personal-tab"></a><span data-ttu-id="98c40-142">Veja sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="98c40-142">View your personal tab</span></span>

- <span data-ttu-id="98c40-143">Na barra de navegação localizada à esquerda do Teams App, selecione o `...` menu.</span><span class="sxs-lookup"><span data-stu-id="98c40-143">In the navigation bar located at the far-left of the Teams App, select the `...` menu.</span></span> <span data-ttu-id="98c40-144">Você será apresentado com uma lista de aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="98c40-144">You'll be presented with a list of personal apps.</span></span>

- <span data-ttu-id="98c40-145">Selecione sua guia na lista para visualizar.</span><span class="sxs-lookup"><span data-stu-id="98c40-145">Select your tab from the list to view.</span></span>
