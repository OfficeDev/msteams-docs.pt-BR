### <a name="_layoutcshtml"></a><span data-ttu-id="593cb-101">_Layout. cshtml</span><span class="sxs-lookup"><span data-stu-id="593cb-101">_Layout.cshtml</span></span>

<span data-ttu-id="593cb-102">Para que sua guia seja exibida no Teams, você deve incluir o **SDK do cliente JavaScript do Microsoft Teams** e incluir uma chamada para depois que `microsoftTeams.initialize()` a página for carregada.</span><span class="sxs-lookup"><span data-stu-id="593cb-102">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="593cb-103">Esta é a maneira como sua guia e o cliente do teams se comunicam:</span><span class="sxs-lookup"><span data-stu-id="593cb-103">This is how your tab and the Teams client communicate:</span></span>

- <span data-ttu-id="593cb-104">Navegue até a pasta **compartilhada** , abra **_Layout. cshtml**e adicione o seguinte à `<head>` marca:</span><span class="sxs-lookup"><span data-stu-id="593cb-104">Navigate to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tag:</span></span>

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

>[!IMPORTANT]
><span data-ttu-id="593cb-105">Não copie/cole as `<script src="...">` URLs desta página, pois elas podem não representar a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="593cb-105">Don't copy/paste the `<script src="...">` URLs from this page, as they may not represent the latest version.</span></span> <span data-ttu-id="593cb-106">Para obter a versão mais recente do SDK, sempre vá para: [API JavaScript do Microsoft Teams](https://www.npmjs.com/package/@microsoft/teams-js.com).</span><span class="sxs-lookup"><span data-stu-id="593cb-106">To get the latest version of the SDK, always go to: [Microsoft Teams JavaScript API](https://www.npmjs.com/package/@microsoft/teams-js.com).</span></span>

### <a name="tabcshtml"></a><span data-ttu-id="593cb-107">Tab. cshtml</span><span class="sxs-lookup"><span data-stu-id="593cb-107">Tab.cshtml</span></span>

<span data-ttu-id="593cb-108">Abra **Tab. cshtml** e atualize o incorporado `<script>` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="593cb-108">Open **Tab.cshtml** and update the embedded `<script>` as follows:</span></span>

- <span data-ttu-id="593cb-109">Na parte superior do script, ligue `microsoftTeams.initialize()`para.</span><span class="sxs-lookup"><span data-stu-id="593cb-109">At the top of the script, call `microsoftTeams.initialize()`.</span></span>

- <span data-ttu-id="593cb-110">Atualize os `websiteUrl` valores `contentUrl` e em cada função com a URL https ngrok para sua guia.</span><span class="sxs-lookup"><span data-stu-id="593cb-110">Update the `websiteUrl` and `contentUrl` values in each function with the HTTPS ngrok URL to your tab.</span></span>

<span data-ttu-id="593cb-111">Agora, o código deve se parecer com o seguinte com o **y8rCgT2b** substituído pela URL do ngrok:</span><span class="sxs-lookup"><span data-stu-id="593cb-111">Your code should now look like the following with **y8rCgT2b** replaced with your ngrok URL:</span></span>

```javascript
    microsoftTeams.initialize();

    let saveGray = () => {
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            microsoftTeams.settings.setSettings({
                websiteUrl: `https://y8rCgT2b.ngrok.io`,
                contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                entityId: "grayIconTab",
                suggestedDisplayName: "MyNewTab"
            });
            saveEvent.notifySuccess();
        });
    }

    let saveRed = () => {
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            microsoftTeams.settings.setSettings({
                websiteUrl: `https://y8rCgT2b.ngrok.io`,
                contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                entityId: "redIconTab",
                suggestedDisplayName: "MyNewTab"
            });
            saveEvent.notifySuccess();
        });
    }
```

<span data-ttu-id="593cb-112">Certifique-se de salvar a **guia atualizada. cshtml**.</span><span class="sxs-lookup"><span data-stu-id="593cb-112">Make sure to save the updated **Tab.cshtml**.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="593cb-113">Criar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="593cb-113">Build and run your application</span></span>

- <span data-ttu-id="593cb-114">No Visual Studio, pressione **F5**ou escolha **Iniciar Depuração** no menu **depurar** .</span><span class="sxs-lookup"><span data-stu-id="593cb-114">In Visual Studio press **F5**, or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="593cb-115">Verifique se o **ngrok** está em execução e funcionando corretamente abrindo o navegador e acessando a página de conteúdo por meio da URL https do ngrok que foi fornecida na janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="593cb-115">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

>[!TIP]
><span data-ttu-id="593cb-116">Você precisa ter o aplicativo no Visual Studio e o ngrok em execução para concluir este QuickStart.</span><span class="sxs-lookup"><span data-stu-id="593cb-116">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="593cb-117">Se você precisar parar a execução do aplicativo no Visual Studio para trabalhar nele, **Mantenha o ngrok em execução**.</span><span class="sxs-lookup"><span data-stu-id="593cb-117">If you need to stop running your application in Visual Studio to work on it **keep ngrok running**.</span></span> <span data-ttu-id="593cb-118">Ele continuará a escutar e retomará o roteamento da solicitação do aplicativo quando ele for reiniciado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="593cb-118">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="593cb-119">Se for necessário reiniciar o serviço ngrok, ele retornará uma nova URL e você terá que atualizar seu aplicativo com a nova URL.</span><span class="sxs-lookup"><span data-stu-id="593cb-119">If you have to restart the ngrok service it will return a new URL and you'll have to update your application with the new URL.</span></span>

## <a name="upload-your-tab-to-teams-with-app-studio"></a><span data-ttu-id="593cb-120">Carregar sua guia para o Teams com o app Studio</span><span class="sxs-lookup"><span data-stu-id="593cb-120">Upload your tab to Teams with App Studio</span></span>

>[!Note]
> <span data-ttu-id="593cb-121">Usamos o app Studio para editar o arquivo **manifest. JSON** e carregar o pacote concluído para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="593cb-121">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="593cb-122">Você também pode editar manualmente o arquivo **manifest. JSON** , se preferir.</span><span class="sxs-lookup"><span data-stu-id="593cb-122">You can also manually edit the **manifest.json** file if you prefer.</span></span> <span data-ttu-id="593cb-123">Se você fizer isso, certifique-se de compilar a solução novamente para criar o arquivo **Tab. zip** para carregar.</span><span class="sxs-lookup"><span data-stu-id="593cb-123">If you do, be sure to build the solution again to create the **tab.zip** file to upload.</span></span>

- <span data-ttu-id="593cb-124">Abra o cliente do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="593cb-124">Open the Microsoft Teams client.</span></span> <span data-ttu-id="593cb-125">Se você usar a [versão baseada na Web](https://teams.microsoft.com) , poderá inspecionar seu código de front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md)do navegador.</span><span class="sxs-lookup"><span data-stu-id="593cb-125">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="593cb-126">Abra o app Studio e selecione a guia **Editor do manifesto** .</span><span class="sxs-lookup"><span data-stu-id="593cb-126">Open App studio and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="593cb-127">Selecione o bloco **importar um aplicativo existente** no editor de manifesto para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente concluído.</span><span class="sxs-lookup"><span data-stu-id="593cb-127">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="593cb-128">O nome do seu pacote de aplicativos é **Tab. zip**.</span><span class="sxs-lookup"><span data-stu-id="593cb-128">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="593cb-129">Ele deve ser encontrado aqui:</span><span class="sxs-lookup"><span data-stu-id="593cb-129">It should be found here:</span></span>

```bash
/bin/Debug/netcoreapp2.2/tab.zip
```

- <span data-ttu-id="593cb-130">Carregar **Tab. zip** para o app Studio.</span><span class="sxs-lookup"><span data-stu-id="593cb-130">Upload **tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="593cb-131">Atualizar seu pacote de aplicativos com o editor de manifesto</span><span class="sxs-lookup"><span data-stu-id="593cb-131">Update your app package with Manifest editor</span></span>

<span data-ttu-id="593cb-132">Depois de carregar seu pacote de aplicativos no app Studio, você precisará concluir a configuração.</span><span class="sxs-lookup"><span data-stu-id="593cb-132">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="593cb-133">Selecione o bloco para a guia recentemente importada no painel direito da página de boas-vindas do editor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="593cb-133">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="593cb-134">Há uma lista de etapas no lado esquerdo do editor de manifestos e, à direita, uma lista de propriedades que precisam ter valores para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="593cb-134">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="593cb-135">Muitas das informações foram fornecidas pelo *manifesto. JSON* , mas há alguns campos que você precisará atualizar:</span><span class="sxs-lookup"><span data-stu-id="593cb-135">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="593cb-136">Detalhes: detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="593cb-136">Details: App details</span></span>

- <span data-ttu-id="593cb-137">Em *identificação* selecione ***gerar*** para substituir a ID do espaço reservado pelo GUID necessário da guia.</span><span class="sxs-lookup"><span data-stu-id="593cb-137">Under *Identification* select ***Generate*** to replace the placeholder id with the required GUID for your tab.</span></span>

- <span data-ttu-id="593cb-138">Em *informações do desenvolvedor* , atualize o campo **URL do site** com sua URL https do *ngrok* .</span><span class="sxs-lookup"><span data-stu-id="593cb-138">Under *Developer information* update the **Website URL** field with your *ngrok* HTTPS URL.</span></span>

- <span data-ttu-id="593cb-139">Em *URLs de aplicativo* , atualize a **declaração de privacidade** e **termos de uso de campos de** URL com sua URL https do *ngrok* .</span><span class="sxs-lookup"><span data-stu-id="593cb-139">Under *App URLs* update the **Privacy statement** and **Terms of use** URL fields with your *ngrok* HTTPS URL.</span></span> <span data-ttu-id="593cb-140">Lembre-se de incluir os caminhos */Privacy* e */tou* no final das URLs.</span><span class="sxs-lookup"><span data-stu-id="593cb-140">Remember to include the */privacy* and */tou* paths at the end of the URLs.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="593cb-141">Recursos: guias</span><span class="sxs-lookup"><span data-stu-id="593cb-141">Capabilities: Tabs</span></span>

<span data-ttu-id="593cb-142">Na seção *guias* :</span><span class="sxs-lookup"><span data-stu-id="593cb-142">In the *Tabs* section:</span></span>

- <span data-ttu-id="593cb-143">Na *guia equipe* selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="593cb-143">Under *Team Tab* select **Add**.</span></span>

- <span data-ttu-id="593cb-144">Na janela pop-up da guia equipe atualizar a *URL* de configuração `https://<yourngrokurl>/tab`para.</span><span class="sxs-lookup"><span data-stu-id="593cb-144">In the Team tab pop-up window update the *Configuration URL* to `https://<yourngrokurl>/tab`.</span></span>

- <span data-ttu-id="593cb-145">Por fim, certifique-se de que a *configuração pode atualizar? Equipe*e caixas de *chat de grupo* são verificados e selecione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="593cb-145">Finally, make sure the *can update configuration? Team*, and *Group chat* boxes are checked and select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="593cb-146">Concluir: domínios e permissões</span><span class="sxs-lookup"><span data-stu-id="593cb-146">Finish: Domains and permissions</span></span>

<span data-ttu-id="593cb-147">Na seção *domínios e permissões* , os *domínios do campo Tabs* devem conter a URL do NGROK sem o prefixo HTTPS- `<yourngrokurl>.ngrok.io/`.</span><span class="sxs-lookup"><span data-stu-id="593cb-147">In the *Domains and permissions* section, the *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

#### <a name="test-and-distribute-test-and-distribute"></a><span data-ttu-id="593cb-148">Testar e distribuir: testar e distribuir</span><span class="sxs-lookup"><span data-stu-id="593cb-148">Test and distribute: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="593cb-149">No campo **Descrição** à direita, você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="593cb-149">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="593cb-150">&#9888; "**a matriz ' validDomains ' não pode conter um site de tunelamento...**"</span><span class="sxs-lookup"><span data-stu-id="593cb-150">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="593cb-151">Este aviso pode ser ignorado durante o teste da guia.</span><span class="sxs-lookup"><span data-stu-id="593cb-151">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="593cb-152">Na seção *testar e distribuir* :</span><span class="sxs-lookup"><span data-stu-id="593cb-152">In the *Test and distribute* section:</span></span>

- <span data-ttu-id="593cb-153">Selecionar **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="593cb-153">Select **Install**.</span></span>

- <span data-ttu-id="593cb-154">Na janela pop-up *Adicionar a um campo de equipe ou chat* , insira sua equipe e selecione **instalar**.</span><span class="sxs-lookup"><span data-stu-id="593cb-154">In the pop-up window's *Add to a team or chat* field enter your team and select **Install**.</span></span>

- <span data-ttu-id="593cb-155">Na próxima janela pop-up, escolha o canal de equipe onde você deseja exibir a guia e selecione **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="593cb-155">In the next pop-up window choose the team channel where you would like the tab displayed and select **Set up**.</span></span>

- <span data-ttu-id="593cb-156">Na janela pop-up final, selecione um valor para a página da guia (um ícone vermelho ou cinza) e selecione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="593cb-156">In the final pop-up window select a value for the tab page (either a red or gray icon) and select **Save**.</span></span>

<span data-ttu-id="593cb-157">Para exibir sua guia, navegue até a equipe na qual você a instalou e selecione-a na barra de guias.</span><span class="sxs-lookup"><span data-stu-id="593cb-157">To view your tab, navigate to the team you installed it on, and select it from the tab bar.</span></span> <span data-ttu-id="593cb-158">A página que você escolheu durante a configuração deve ser exibida.</span><span class="sxs-lookup"><span data-stu-id="593cb-158">The page that you chose during configuration should be displayed.</span></span>
