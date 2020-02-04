## <a name="upload-your-tab-to-teams-with-app-studio"></a><span data-ttu-id="cf897-101">Carregar sua guia para o Teams com o app Studio</span><span class="sxs-lookup"><span data-stu-id="cf897-101">Upload your tab to Teams with App Studio</span></span>

>[!NOTE]
> <span data-ttu-id="cf897-102">Usamos o app Studio para editar o arquivo **manifest. JSON** e carregar o pacote concluído para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="cf897-102">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="cf897-103">Você também pode editar manualmente o arquivo **manifest. JSON** , se preferir.</span><span class="sxs-lookup"><span data-stu-id="cf897-103">You can also manually edit the **manifest.json** file if you prefer.</span></span> <span data-ttu-id="cf897-104">Se você fizer isso, certifique-se de compilar a solução novamente para criar o arquivo **Tab. zip** para carregar.</span><span class="sxs-lookup"><span data-stu-id="cf897-104">If you do, be sure to build the solution again to create the **tab.zip** file to upload.</span></span>

- <span data-ttu-id="cf897-105">Abra o cliente do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="cf897-105">Open the Microsoft Teams client.</span></span> <span data-ttu-id="cf897-106">Se você usar a [versão baseada na Web](https://teams.microsoft.com) , poderá inspecionar seu código de front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md)do navegador.</span><span class="sxs-lookup"><span data-stu-id="cf897-106">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="cf897-107">Abra o aplicativo App Studio e selecione a guia **Editor de manifesto** .</span><span class="sxs-lookup"><span data-stu-id="cf897-107">Open the App Studio app and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="cf897-108">Selecione o bloco **importar um aplicativo existente** no editor de manifesto para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente concluído.</span><span class="sxs-lookup"><span data-stu-id="cf897-108">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="cf897-109">O nome do seu pacote de aplicativos é **Tab. zip**.</span><span class="sxs-lookup"><span data-stu-id="cf897-109">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="cf897-110">Ele deve ser encontrado aqui:</span><span class="sxs-lookup"><span data-stu-id="cf897-110">It should be found here:</span></span>

```bash
/bin/Debug/netcoreapp2.2/tab.zip
```

- <span data-ttu-id="cf897-111">Carregar **Tab. zip** para o app Studio.</span><span class="sxs-lookup"><span data-stu-id="cf897-111">Upload **tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="cf897-112">Atualizar seu pacote de aplicativos com o editor de manifesto</span><span class="sxs-lookup"><span data-stu-id="cf897-112">Update your app package with Manifest editor</span></span>

<span data-ttu-id="cf897-113">Depois de carregar seu pacote de aplicativos no app Studio, você precisará concluir a configuração.</span><span class="sxs-lookup"><span data-stu-id="cf897-113">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="cf897-114">Selecione o bloco para a guia recentemente importada no painel direito da página de boas-vindas do editor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="cf897-114">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="cf897-115">Há uma lista de etapas no lado esquerdo do editor de manifestos e, à direita, uma lista de propriedades que precisam ter valores para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="cf897-115">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="cf897-116">Muitas das informações foram fornecidas pelo *manifesto. JSON* , mas há alguns campos que você precisará atualizar:</span><span class="sxs-lookup"><span data-stu-id="cf897-116">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="cf897-117">Detalhes: detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="cf897-117">Details: App details</span></span>

- <span data-ttu-id="cf897-118">Em *identificação* selecione **gerar** para gerar uma nova ID de aplicativo para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf897-118">Under *Identification* select **Generate** to generate a new App Id for your app.</span></span>

- <span data-ttu-id="cf897-119">Em *informações do desenvolvedor* , atualize o campo **URL do site** com sua URL https do *ngrok* .</span><span class="sxs-lookup"><span data-stu-id="cf897-119">Under *Developer information* update the **Website URL** field with your *ngrok* HTTPS URL.</span></span>

- <span data-ttu-id="cf897-120">Em *URLs de aplicativo* `https://<yourngrokurl>/privacy` , atualize a **declaração de privacidade** e **termos de uso** para `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="cf897-120">Under *App URLs* update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="cf897-121">Recursos: guias</span><span class="sxs-lookup"><span data-stu-id="cf897-121">Capabilities: Tabs</span></span>

<span data-ttu-id="cf897-122">Na seção *guias* :</span><span class="sxs-lookup"><span data-stu-id="cf897-122">In the *Tabs* section:</span></span>

- <span data-ttu-id="cf897-123">Na *guia equipe* selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="cf897-123">Under *Team Tab* select **Add**.</span></span>

- <span data-ttu-id="cf897-124">Na janela pop-up da guia equipe atualizar a *URL* de configuração `https://<yourngrokurl>/tab`para.</span><span class="sxs-lookup"><span data-stu-id="cf897-124">In the Team tab pop-up window update the *Configuration URL* to `https://<yourngrokurl>/tab`.</span></span>

- <span data-ttu-id="cf897-125">Por fim, certifique-se de que a *configuração pode atualizar? Equipe*e caixas de *chat de grupo* são verificados e selecione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="cf897-125">Finally, make sure the *can update configuration? Team*, and *Group chat* boxes are checked and select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="cf897-126">Concluir: domínios e permissões</span><span class="sxs-lookup"><span data-stu-id="cf897-126">Finish: Domains and permissions</span></span>

<span data-ttu-id="cf897-127">Na seção *domínios e permissões* , os *domínios do campo Tabs* devem conter a URL do NGROK sem o prefixo HTTPS- `<yourngrokurl>.ngrok.io/`.</span><span class="sxs-lookup"><span data-stu-id="cf897-127">In the *Domains and permissions* section, the *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

#### <a name="finish-test-and-distribute"></a><span data-ttu-id="cf897-128">Concluir: testar e distribuir</span><span class="sxs-lookup"><span data-stu-id="cf897-128">Finish: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="cf897-129">No campo **Descrição** à direita, você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="cf897-129">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="cf897-130">&#9888; "**a matriz ' validDomains ' não pode conter um site de tunelamento...**"</span><span class="sxs-lookup"><span data-stu-id="cf897-130">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="cf897-131">Este aviso pode ser ignorado durante o teste da guia.</span><span class="sxs-lookup"><span data-stu-id="cf897-131">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="cf897-132">Na seção *testar e distribuir* :</span><span class="sxs-lookup"><span data-stu-id="cf897-132">In the *Test and distribute* section:</span></span>

- <span data-ttu-id="cf897-133">Selecionar **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="cf897-133">Select **Install**.</span></span>

- <span data-ttu-id="cf897-134">Na janela pop-up *Adicionar a um campo de equipe ou chat* , insira sua equipe e selecione **instalar**.</span><span class="sxs-lookup"><span data-stu-id="cf897-134">In the pop-up window's *Add to a team or chat* field enter your team and select **Install**.</span></span>

- <span data-ttu-id="cf897-135">Na próxima janela pop-up, escolha o canal de equipe onde você deseja exibir a guia e selecione **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="cf897-135">In the next pop-up window choose the team channel where you would like the tab displayed and select **Set up**.</span></span>

- <span data-ttu-id="cf897-136">Na janela pop-up final, selecione um valor para a página da guia (um ícone vermelho ou cinza) e selecione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="cf897-136">In the final pop-up window select a value for the tab page (either a red or gray icon) and select **Save**.</span></span>

<span data-ttu-id="cf897-137">Para exibir sua guia, navegue até a equipe na qual você a instalou e selecione-a na barra de guias.</span><span class="sxs-lookup"><span data-stu-id="cf897-137">To view your tab, navigate to the team you installed it on, and select it from the tab bar.</span></span> <span data-ttu-id="cf897-138">A página que você escolheu durante a configuração deve ser exibida.</span><span class="sxs-lookup"><span data-stu-id="cf897-138">The page that you chose during configuration should be displayed.</span></span>
