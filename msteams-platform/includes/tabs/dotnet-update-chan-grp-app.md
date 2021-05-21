### <a name="_layoutcshtml"></a><span data-ttu-id="41d56-101">_Layout.cshtml</span><span class="sxs-lookup"><span data-stu-id="41d56-101">_Layout.cshtml</span></span>

<span data-ttu-id="41d56-102">Para que sua guia seja exibida Teams, você deve incluir o **SDK** do cliente JavaScript Microsoft Teams e incluir uma chamada depois que a página `microsoftTeams.initialize()` for carregada.</span><span class="sxs-lookup"><span data-stu-id="41d56-102">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="41d56-103">É assim que sua guia e o cliente Teams se comunicam:</span><span class="sxs-lookup"><span data-stu-id="41d56-103">This is how your tab and the Teams client communicate:</span></span>

- <span data-ttu-id="41d56-104">Navegue até **a pasta Shared,** **abra _Layout.cshtml** e adicione o seguinte à `<head>` marca:</span><span class="sxs-lookup"><span data-stu-id="41d56-104">Navigate to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tag:</span></span>

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

>[!IMPORTANT]
><span data-ttu-id="41d56-105">Não copie/colar as `<script src="...">` URLs desta página, pois elas podem não representar a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="41d56-105">Don't copy/paste the `<script src="...">` URLs from this page, as they may not represent the latest version.</span></span> <span data-ttu-id="41d56-106">Para obter a versão mais recente do SDK, sempre vá para: Microsoft Teams [API JavaScript](https://www.npmjs.com/package/@microsoft/teams-js).</span><span class="sxs-lookup"><span data-stu-id="41d56-106">To get the latest version of the SDK, always go to: [Microsoft Teams JavaScript API](https://www.npmjs.com/package/@microsoft/teams-js).</span></span>

### <a name="tabcshtml"></a><span data-ttu-id="41d56-107">Tab.cshtml</span><span class="sxs-lookup"><span data-stu-id="41d56-107">Tab.cshtml</span></span>

<span data-ttu-id="41d56-108">Abra **Tab.cshtml** e atualize o incorporado `<script>` da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="41d56-108">Open **Tab.cshtml** and update the embedded `<script>` as follows:</span></span>

- <span data-ttu-id="41d56-109">Na parte superior do script, chame `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="41d56-109">At the top of the script, call `microsoftTeams.initialize()`.</span></span>

- <span data-ttu-id="41d56-110">Atualize `websiteUrl` os valores e em cada função com a URL de `contentUrl` ngrok HTTPS para sua guia.</span><span class="sxs-lookup"><span data-stu-id="41d56-110">Update the `websiteUrl` and `contentUrl` values in each function with the HTTPS ngrok URL to your tab.</span></span>

<span data-ttu-id="41d56-111">Seu código agora deve ter a seguinte aparência com **y8rCgT2b** substituído pela URL do ngrok:</span><span class="sxs-lookup"><span data-stu-id="41d56-111">Your code should now look like the following with **y8rCgT2b** replaced with your ngrok URL:</span></span>

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

<span data-ttu-id="41d56-112">Certifique-se de salvar **o Tab.cshtml atualizado.**</span><span class="sxs-lookup"><span data-stu-id="41d56-112">Make sure to save the updated **Tab.cshtml**.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="41d56-113">Criar e executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="41d56-113">Build and run your application</span></span>

- <span data-ttu-id="41d56-114">Em Visual Studio pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="41d56-114">In Visual Studio press **F5**, or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="41d56-115">Verifique se **o ngrok** está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="41d56-115">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

>[!TIP]
><span data-ttu-id="41d56-116">Você precisa ter seu aplicativo em Visual Studio e ngrok em execução para concluir esse início rápido.</span><span class="sxs-lookup"><span data-stu-id="41d56-116">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="41d56-117">Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar **nele, mantenha o ngrok em execução.**</span><span class="sxs-lookup"><span data-stu-id="41d56-117">If you need to stop running your application in Visual Studio to work on it **keep ngrok running**.</span></span> <span data-ttu-id="41d56-118">Ele continuará escutando e retomará o roteamento da solicitação do aplicativo quando ele for reiniciado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41d56-118">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="41d56-119">Se você precisar reiniciar o serviço ngrok, ele retornará uma nova URL e você terá que atualizar seu aplicativo com a nova URL.</span><span class="sxs-lookup"><span data-stu-id="41d56-119">If you have to restart the ngrok service it will return a new URL and you'll have to update your application with the new URL.</span></span>

## <a name="upload-your-tab-to-teams"></a><span data-ttu-id="41d56-120">Upload sua guia para Teams</span><span class="sxs-lookup"><span data-stu-id="41d56-120">Upload your tab to Teams</span></span>

>[!Note]
> <span data-ttu-id="41d56-121">Usamos o App Studio para editar seu **manifest.jsno** arquivo e carregar o pacote concluído para Teams.</span><span class="sxs-lookup"><span data-stu-id="41d56-121">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="41d56-122">Você também pode editar manualmente o **manifest.jsno** arquivo, se preferir.</span><span class="sxs-lookup"><span data-stu-id="41d56-122">You can also manually edit the **manifest.json** file if you prefer.</span></span> <span data-ttu-id="41d56-123">Se fizer isso, certifique-se de criar a solução novamente para criar o arquivo **tab.zip** para carregar.</span><span class="sxs-lookup"><span data-stu-id="41d56-123">If you do, be sure to build the solution again to create the **tab.zip** file to upload.</span></span>

- <span data-ttu-id="41d56-124">Abra o Microsoft Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="41d56-124">Open the Microsoft Teams client.</span></span> <span data-ttu-id="41d56-125">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="41d56-125">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="41d56-126">Abra o studio app e selecione a **guia Editor de manifesto.**</span><span class="sxs-lookup"><span data-stu-id="41d56-126">Open App studio and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="41d56-127">Selecione o **pacote Importar um aplicativo existente** no editor de Manifesto para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente completo.</span><span class="sxs-lookup"><span data-stu-id="41d56-127">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="41d56-128">O nome do pacote do aplicativo é **tab.zip**.</span><span class="sxs-lookup"><span data-stu-id="41d56-128">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="41d56-129">Ele deve ser encontrado aqui:</span><span class="sxs-lookup"><span data-stu-id="41d56-129">It should be found here:</span></span>

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

- <span data-ttu-id="41d56-130">Upload **tab.zip** App Studio.</span><span class="sxs-lookup"><span data-stu-id="41d56-130">Upload **tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="41d56-131">Atualizar seu pacote de aplicativos com o editor de manifesto</span><span class="sxs-lookup"><span data-stu-id="41d56-131">Update your app package with Manifest editor</span></span>

<span data-ttu-id="41d56-132">Depois de carregar seu pacote de aplicativos no App Studio, você precisará terminar de configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="41d56-132">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="41d56-133">Selecione o azulejo para sua guia recém-importada no painel direito da página de boas-vindas do editor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="41d56-133">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="41d56-134">Há uma lista de etapas no lado esquerdo do editor de Manifesto e, à direita, uma lista de propriedades que precisam ter valores para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="41d56-134">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="41d56-135">Grande parte das informações foram fornecidas pelo seumanifest.js *on,* mas há alguns campos que você precisará atualizar:</span><span class="sxs-lookup"><span data-stu-id="41d56-135">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="41d56-136">Detalhes: Detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="41d56-136">Details: App details</span></span>

<span data-ttu-id="41d56-137">Na seção *Detalhes do* aplicativo:</span><span class="sxs-lookup"><span data-stu-id="41d56-137">In the *App details* section:</span></span>

- <span data-ttu-id="41d56-138">*Identificação*: selecione **Gerar** para substituir a id de espaço reservado pelo GUID necessário para sua guia.</span><span class="sxs-lookup"><span data-stu-id="41d56-138">*Identification*: select **Generate** to replace the placeholder id with the required GUID for your tab.</span></span>

- <span data-ttu-id="41d56-139">*Informações do* desenvolvedor : atualize o **campo URL do** site com sua URL HTTPS *ngrok.*</span><span class="sxs-lookup"><span data-stu-id="41d56-139">*Developer information*: update the **Website URL** field with your *ngrok* HTTPS URL.</span></span>

- <span data-ttu-id="41d56-140">*URLs do aplicativo:* atualize a **instrução Privacy** para `https://<yourngrokurl>/privacy` e Os Termos de **uso** para `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="41d56-140">*App URLs*: update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="41d56-141">Recursos: guias</span><span class="sxs-lookup"><span data-stu-id="41d56-141">Capabilities: Tabs</span></span>

<span data-ttu-id="41d56-142">Na seção *Guias:*</span><span class="sxs-lookup"><span data-stu-id="41d56-142">In the *Tabs* section:</span></span>

- <span data-ttu-id="41d56-143">*Guia Equipe*: selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="41d56-143">*Team Tab*: select **Add**.</span></span>

- <span data-ttu-id="41d56-144">Na janela pop-up da guia Equipe atualize a *URL de Configuração* para `https://<yourngrokurl>/tab` .</span><span class="sxs-lookup"><span data-stu-id="41d56-144">In the Team tab pop-up window update the *Configuration URL* to `https://<yourngrokurl>/tab`.</span></span>

- <span data-ttu-id="41d56-145">Por fim, certifique-se de que *a configuração pode ser atualizada? As* caixas de chat Equipe *e Grupo* são verificadas e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="41d56-145">Finally, make sure the *can update configuration? Team*, and *Group chat* boxes are checked and select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="41d56-146">Concluir: domínios e permissões</span><span class="sxs-lookup"><span data-stu-id="41d56-146">Finish: Domains and permissions</span></span>

<span data-ttu-id="41d56-147">Na seção *Domínios e permissões:*</span><span class="sxs-lookup"><span data-stu-id="41d56-147">In the *Domains and permissions* section:</span></span>

- <span data-ttu-id="41d56-148">Os *domínios do campo guias* devem conter sua URL ngrok sem o prefixo HTTPS - `<yourngrokurl>.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="41d56-148">The *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

#### <a name="finish-test-and-distribute"></a><span data-ttu-id="41d56-149">Concluir: Testar e distribuir</span><span class="sxs-lookup"><span data-stu-id="41d56-149">Finish: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="41d56-150">No campo **Descrição** à direita, você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="41d56-150">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="41d56-151">&#9888; "**A matriz 'validDomains' não pode conter um site de tunelamento...**"</span><span class="sxs-lookup"><span data-stu-id="41d56-151">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="41d56-152">Esse aviso pode ser ignorado durante o teste da guia.</span><span class="sxs-lookup"><span data-stu-id="41d56-152">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="41d56-153">Na seção *Testar e distribuir:*</span><span class="sxs-lookup"><span data-stu-id="41d56-153">In the *Test and distribute* section:</span></span>

- <span data-ttu-id="41d56-154">Selecionar **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="41d56-154">Select **Install**.</span></span>

- <span data-ttu-id="41d56-155">Na janela pop-up, Adicione a uma equipe ou *campo de chat* insira sua equipe e selecione **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="41d56-155">In the pop-up window's *Add to a team or chat* field enter your team and select **Install**.</span></span>

- <span data-ttu-id="41d56-156">Na próxima janela pop-up, escolha o canal de equipe onde você gostaria que a guia fosse exibida e selecione **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="41d56-156">In the next pop-up window choose the team channel where you would like the tab displayed and select **Set up**.</span></span>

- <span data-ttu-id="41d56-157">Na janela pop-up final, selecione um valor para a página de tabulação (um ícone vermelho ou cinza) e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="41d56-157">In the final pop-up window select a value for the tab page (either a red or gray icon) and select **Save**.</span></span>

<span data-ttu-id="41d56-158">Para exibir sua guia, navegue até a equipe em que você a instalou e selecione-a na barra de guias.</span><span class="sxs-lookup"><span data-stu-id="41d56-158">To view your tab, navigate to the team you installed it on, and select it from the tab bar.</span></span> <span data-ttu-id="41d56-159">A página escolhida durante a configuração deve ser exibida.</span><span class="sxs-lookup"><span data-stu-id="41d56-159">The page that you chose during configuration should be displayed.</span></span>
