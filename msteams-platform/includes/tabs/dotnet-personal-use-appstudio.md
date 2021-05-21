## <a name="upload-your-tab-to-teams-with-app-studio"></a><span data-ttu-id="146ca-101">Upload sua guia para Teams com o App Studio</span><span class="sxs-lookup"><span data-stu-id="146ca-101">Upload your tab to Teams with App Studio</span></span>

>[!NOTE]
> <span data-ttu-id="146ca-102">Usamos o App Studio para editar seu **manifest.jsno** arquivo e carregar o pacote concluído para Teams.</span><span class="sxs-lookup"><span data-stu-id="146ca-102">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="146ca-103">Você também pode editar manualmente **manifest.jsem,** se preferir.</span><span class="sxs-lookup"><span data-stu-id="146ca-103">You can also manually edit **manifest.json** if you prefer.</span></span> <span data-ttu-id="146ca-104">Se fizer isso, certifique-se de criar a solução novamente para criar o arquivo **Tab.zip** para carregar.</span><span class="sxs-lookup"><span data-stu-id="146ca-104">If you do, be sure to build the solution again to create the **Tab.zip** file to upload.</span></span>

- <span data-ttu-id="146ca-105">Abra o Microsoft Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="146ca-105">Open the Microsoft Teams client.</span></span> <span data-ttu-id="146ca-106">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="146ca-106">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="146ca-107">Abra o studio app e selecione a **guia Editor de manifesto.**</span><span class="sxs-lookup"><span data-stu-id="146ca-107">Open App studio and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="146ca-108">Selecione o **pacote Importar um aplicativo existente** no editor de Manifesto para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente completo.</span><span class="sxs-lookup"><span data-stu-id="146ca-108">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="146ca-109">O nome do pacote do aplicativo é **tab.zip**.</span><span class="sxs-lookup"><span data-stu-id="146ca-109">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="146ca-110">Ele deve ser encontrado aqui:</span><span class="sxs-lookup"><span data-stu-id="146ca-110">It should be found here:</span></span>

    ```bash
    /bin/Debug/netcoreapp2.2/Tab.zip
    ```

- <span data-ttu-id="146ca-111">Upload **Tab.zip** App Studio.</span><span class="sxs-lookup"><span data-stu-id="146ca-111">Upload **Tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="146ca-112">Atualizar seu pacote de aplicativos com o editor de manifesto</span><span class="sxs-lookup"><span data-stu-id="146ca-112">Update your app package with Manifest editor</span></span>

<span data-ttu-id="146ca-113">Depois de carregar seu pacote de aplicativos no App Studio, você precisará terminar de configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="146ca-113">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="146ca-114">Selecione o azulejo para sua guia recém-importada no painel direito da página de boas-vindas do editor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="146ca-114">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="146ca-115">Há uma lista de etapas no lado esquerdo do editor de Manifesto e, à direita, uma lista de propriedades que precisam ter valores para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="146ca-115">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="146ca-116">Grande parte das informações foram fornecidas pelo seumanifest.js *on,* mas há alguns campos que você precisará atualizar:</span><span class="sxs-lookup"><span data-stu-id="146ca-116">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="146ca-117">Detalhes: Detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="146ca-117">Details: App details</span></span>

<span data-ttu-id="146ca-118">Na seção **Detalhes do** aplicativo:</span><span class="sxs-lookup"><span data-stu-id="146ca-118">In the **App details** section:</span></span>

- <span data-ttu-id="146ca-119">Em **Identificação,** **selecione Gerar** para gerar uma nova ID do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="146ca-119">Under **Identification** select **Generate** to generate a new App Id for your app.</span></span>

- <span data-ttu-id="146ca-120">Em **Informações do desenvolvedor** atualize a URL do **site** com sua URL HTTPS **ngrok.**</span><span class="sxs-lookup"><span data-stu-id="146ca-120">Under **Developer information** update the **Website URL** with your **ngrok** HTTPS URL.</span></span>

- <span data-ttu-id="146ca-121">Em **URLs do aplicativo,** atualize a **instrução Privacy** para `https://<yourngrokurl>/privacy` e Os Termos de **uso** para `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="146ca-121">Under **App URLs** update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="146ca-122">Recursos: guias</span><span class="sxs-lookup"><span data-stu-id="146ca-122">Capabilities: Tabs</span></span>

<span data-ttu-id="146ca-123">Na seção *Guias:*</span><span class="sxs-lookup"><span data-stu-id="146ca-123">In the *Tabs* section:</span></span>

- <span data-ttu-id="146ca-124">Em **Adicionar uma guia pessoal,** selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="146ca-124">Under **Add a personal tab** select **Add**.</span></span> <span data-ttu-id="146ca-125">Você receberá uma janela de diálogo pop-up.</span><span class="sxs-lookup"><span data-stu-id="146ca-125">You will be presented with a pop-up dialogue window.</span></span>

- <span data-ttu-id="146ca-126">Conclua **o campo Nome.**</span><span class="sxs-lookup"><span data-stu-id="146ca-126">Complete the **Name** field.</span></span>

- <span data-ttu-id="146ca-127">Conclua **o campo ID da** entidade.</span><span class="sxs-lookup"><span data-stu-id="146ca-127">Complete the **Entity Id** field.</span></span>

- <span data-ttu-id="146ca-128">Atualize o **campo URL** de conteúdo com `https://<yourngrokurl>/personalTab` para .</span><span class="sxs-lookup"><span data-stu-id="146ca-128">Update the **Content URL** field with to `https://<yourngrokurl>/personalTab`.</span></span>

- <span data-ttu-id="146ca-129">Deixe o **campo URL do site** em branco.</span><span class="sxs-lookup"><span data-stu-id="146ca-129">Leave the **Website URL** field blank.</span></span>

- <span data-ttu-id="146ca-130">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="146ca-130">Select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="146ca-131">Concluir: domínios e permissões</span><span class="sxs-lookup"><span data-stu-id="146ca-131">Finish: Domains and permissions</span></span>

<span data-ttu-id="146ca-132">Na seção **Domínios e** permissões, o **campo Domínios** de suas guias deve conter sua URL ngrok sem o prefixo HTTPS - `<yourngrokurl>.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="146ca-132">In the **Domains and permissions** section, the **Domains from your tabs** field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

##### <a name="finish-test-and-distribute"></a><span data-ttu-id="146ca-133">Concluir: Testar e distribuir</span><span class="sxs-lookup"><span data-stu-id="146ca-133">Finish: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="146ca-134">No campo **Descrição** à direita, você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="146ca-134">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="146ca-135">&#9888; "**A matriz 'validDomains' não pode conter um site de tunelamento...**"</span><span class="sxs-lookup"><span data-stu-id="146ca-135">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="146ca-136">Esse aviso pode ser ignorado durante o teste da guia.</span><span class="sxs-lookup"><span data-stu-id="146ca-136">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="146ca-137">Na seção **Testar e distribuir:**</span><span class="sxs-lookup"><span data-stu-id="146ca-137">In the **Test and distribute** section:</span></span>

- <span data-ttu-id="146ca-138">Selecionar **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="146ca-138">Select **Install**.</span></span>

- <span data-ttu-id="146ca-139">Na janela pop-up, certifique-se de que **Add for you** está definido como **Sim** e Adicionar a uma equipe ou **chat** está definido como **Não**.</span><span class="sxs-lookup"><span data-stu-id="146ca-139">In the pop-up window make sure that **Add for you** is set to **Yes** and **Add to a team or chat** is set to **No**.</span></span>

- <span data-ttu-id="146ca-140">Selecionar **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="146ca-140">Select **Install**.</span></span>

- <span data-ttu-id="146ca-141">Na próxima janela pop-up, selecione **Abrir** e sua guia será exibida.</span><span class="sxs-lookup"><span data-stu-id="146ca-141">In the next pop-up window select **Open** and your tab will be displayed.</span></span>

## <a name="view-your-personal-tab"></a><span data-ttu-id="146ca-142">Exibir sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="146ca-142">View your personal tab</span></span>

- <span data-ttu-id="146ca-143">Na barra de navegação localizada à extrema esquerda do Teams App, selecione o `...` menu.</span><span class="sxs-lookup"><span data-stu-id="146ca-143">In the navigation bar located at the far-left of the Teams App, select the `...` menu.</span></span> <span data-ttu-id="146ca-144">Você será apresentado com uma lista de aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="146ca-144">You'll be presented with a list of personal apps.</span></span>

- <span data-ttu-id="146ca-145">Selecione sua guia na lista a ser visualizada.</span><span class="sxs-lookup"><span data-stu-id="146ca-145">Select your tab from the list to view.</span></span>
