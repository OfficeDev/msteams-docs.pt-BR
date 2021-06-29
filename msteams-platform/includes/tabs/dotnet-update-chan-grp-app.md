### <a name="_layoutcshtml"></a><span data-ttu-id="44546-101">_Layout.cshtml</span><span class="sxs-lookup"><span data-stu-id="44546-101">_Layout.cshtml</span></span>

<span data-ttu-id="44546-102">Para que sua guia seja exibida Teams, você deve incluir o **SDK** do cliente JavaScript Microsoft Teams e incluir uma chamada depois que a página `microsoftTeams.initialize()` for carregada.</span><span class="sxs-lookup"><span data-stu-id="44546-102">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="44546-103">É assim que sua guia e o cliente Teams se comunicam:</span><span class="sxs-lookup"><span data-stu-id="44546-103">This is how your tab and the Teams client communicate:</span></span>

<span data-ttu-id="44546-104">Vá para **a pasta Shared,** abra **_Layout.cshtml** e adicione o seguinte à `<head>` marca:</span><span class="sxs-lookup"><span data-stu-id="44546-104">Go to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tag:</span></span>

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

>[!IMPORTANT]
> <span data-ttu-id="44546-105">Não copie e colará as URLs desta página, pois elas `<script src="...">` podem não representar a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="44546-105">Do not copy and paste the `<script src="...">` URLs from this page, as they may not represent the latest version.</span></span> <span data-ttu-id="44546-106">Para obter a versão mais recente do SDK, sempre vá [para Microsoft Teams API JavaScript](https://www.npmjs.com/package/@microsoft/teams-js).</span><span class="sxs-lookup"><span data-stu-id="44546-106">To get the latest version of the SDK, always go to [Microsoft Teams JavaScript API](https://www.npmjs.com/package/@microsoft/teams-js).</span></span>

### <a name="tabcshtml"></a><span data-ttu-id="44546-107">Tab.cshtml</span><span class="sxs-lookup"><span data-stu-id="44546-107">Tab.cshtml</span></span>

<span data-ttu-id="44546-108">**Para atualizar o script incorporado**</span><span class="sxs-lookup"><span data-stu-id="44546-108">**To update the embedded script**</span></span>

1. <span data-ttu-id="44546-109">Em Visual Studio, abra **Tab.cshtml** para atualizar o `<script>` .</span><span class="sxs-lookup"><span data-stu-id="44546-109">In Visual Studio, open **Tab.cshtml** to update the embedded `<script>`.</span></span>

1. <span data-ttu-id="44546-110">Na parte superior do script, chame `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="44546-110">At the top of the script, call `microsoftTeams.initialize()`.</span></span>

1. <span data-ttu-id="44546-111">Atualize `websiteUrl` os valores e em cada função com a URL de `contentUrl` ngrok HTTPS para sua guia.</span><span class="sxs-lookup"><span data-stu-id="44546-111">Update the `websiteUrl` and `contentUrl` values in each function with the HTTPS ngrok URL to your tab.</span></span>

    <span data-ttu-id="44546-112">Seu código agora deve ter a seguinte aparência com **y8rCgT2b** substituído pela URL do ngrok:</span><span class="sxs-lookup"><span data-stu-id="44546-112">Your code should now look like the following with **y8rCgT2b** replaced with your ngrok URL:</span></span>

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

1. <span data-ttu-id="44546-113">Certifique-se de salvar **o Tab.cshtml atualizado.**</span><span class="sxs-lookup"><span data-stu-id="44546-113">Make sure to save the updated **Tab.cshtml**.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="44546-114">Criar e executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="44546-114">Build and run your application</span></span>

<span data-ttu-id="44546-115">Em Visual Studio, pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="44546-115">In Visual Studio, press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="44546-116">Verifique se **o ngrok** está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="44546-116">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> [!TIP]
> <span data-ttu-id="44546-117">Você precisa ter seu aplicativo em execução Visual Studio e ngrok.</span><span class="sxs-lookup"><span data-stu-id="44546-117">You need to have both your application in Visual Studio and ngrok running.</span></span> <span data-ttu-id="44546-118">Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar **nele, mantenha o ngrok em execução.**</span><span class="sxs-lookup"><span data-stu-id="44546-118">If you need to stop running your application in Visual Studio to work on it **keep ngrok running**.</span></span> <span data-ttu-id="44546-119">Ele continuará escutando e retomará o roteamento da solicitação do aplicativo quando ele for reiniciado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44546-119">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="44546-120">Se você tiver que reiniciar o serviço ngrok, ele retornará uma nova URL e você terá que atualizar seu aplicativo com a nova URL.</span><span class="sxs-lookup"><span data-stu-id="44546-120">If you have to restart the ngrok service, it will return a new URL and you will have to update your application with the new URL.</span></span>

## <a name="upload-your-tab"></a><span data-ttu-id="44546-121">Upload sua guia</span><span class="sxs-lookup"><span data-stu-id="44546-121">Upload your tab</span></span>

>[!Note]
> <span data-ttu-id="44546-122">O App Studio pode ser usado para editar seu **manifest.jsno** arquivo e carregar o pacote concluído para Teams.</span><span class="sxs-lookup"><span data-stu-id="44546-122">App Studio can be used to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="44546-123">Você também pode editar manualmente o **manifest.jsno** arquivo, se preferir.</span><span class="sxs-lookup"><span data-stu-id="44546-123">You can also manually edit the **manifest.json** file if you prefer.</span></span> <span data-ttu-id="44546-124">Se fizer isso, certifique-se de criar a solução novamente para criar o arquivo **tab.zip** para carregar.</span><span class="sxs-lookup"><span data-stu-id="44546-124">If you do, be sure to build the solution again to create the **tab.zip** file to upload.</span></span>

<span data-ttu-id="44546-125">**Para carregar sua guia**</span><span class="sxs-lookup"><span data-stu-id="44546-125">**To upload your tab**</span></span>

1. <span data-ttu-id="44546-126">Vá para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="44546-126">Go to Microsoft Teams.</span></span> <span data-ttu-id="44546-127">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="44546-127">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

1. <span data-ttu-id="44546-128">Vá para **o App Studio** e selecione a guia Editor **de** manifesto.</span><span class="sxs-lookup"><span data-stu-id="44546-128">Go to **App Studio** and select the **Manifest editor** tab.</span></span>

1. <span data-ttu-id="44546-129">Selecione **Importar um aplicativo existente** no editor de Manifesto para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente completo.</span><span class="sxs-lookup"><span data-stu-id="44546-129">Select **Import an existing app** in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="44546-130">O nome do pacote do aplicativo é **tab.zip**.</span><span class="sxs-lookup"><span data-stu-id="44546-130">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="44546-131">Ele está disponível aqui:</span><span class="sxs-lookup"><span data-stu-id="44546-131">It is available here:</span></span>

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

1. <span data-ttu-id="44546-132">Upload **tab.zip** App Studio.</span><span class="sxs-lookup"><span data-stu-id="44546-132">Upload **tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="44546-133">Atualizar seu pacote de aplicativos com o editor de manifesto</span><span class="sxs-lookup"><span data-stu-id="44546-133">Update your app package with Manifest editor</span></span>

<span data-ttu-id="44546-134">Depois de carregar seu pacote de aplicativos no App Studio, você deve terminar de configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="44546-134">After you have uploaded your app package into App Studio, you must finish configuring it.</span></span>

<span data-ttu-id="44546-135">Selecione o azulejo para sua guia recém-importada no painel direito da página de boas-vindas do editor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="44546-135">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="44546-136">Há uma lista de etapas no lado esquerdo do editor de Manifesto e, à direita, uma lista de propriedades que devem ter valores para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="44546-136">There is a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that must have values for each of those steps.</span></span> <span data-ttu-id="44546-137">Grande parte das informações foram fornecidas pelo seumanifest.js **on,** mas há alguns campos que você deve atualizar:</span><span class="sxs-lookup"><span data-stu-id="44546-137">Much of the information has been provided by your **manifest.json** but there are a few fields that you must update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="44546-138">Detalhes: Detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="44546-138">Details: App details</span></span>

<span data-ttu-id="44546-139">Na seção **Detalhes do** aplicativo:</span><span class="sxs-lookup"><span data-stu-id="44546-139">In the **App details** section:</span></span>

1. <span data-ttu-id="44546-140">Em **Identificação**, selecione **Gerar** para substituir a ID do espaço reservado pelo GUID necessário para sua guia.</span><span class="sxs-lookup"><span data-stu-id="44546-140">Under **Identification**, select **Generate** to replace the placeholder ID with the required GUID for your tab.</span></span>

1. <span data-ttu-id="44546-141">Em **Informações do desenvolvedor**, **atualize Site** com sua URL HTTPS **ngrok.**</span><span class="sxs-lookup"><span data-stu-id="44546-141">Under **Developer information**, update **Website** with your **ngrok** HTTPS URL.</span></span>

1. <span data-ttu-id="44546-142">Em **URLs do aplicativo,** atualize a **instrução Privacy** para `https://<yourngrokurl>/privacy` e Termos de **uso** para `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="44546-142">Under **App URLs**, update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="44546-143">Recursos: guias</span><span class="sxs-lookup"><span data-stu-id="44546-143">Capabilities: Tabs</span></span>

<span data-ttu-id="44546-144">Na seção **Guias:**</span><span class="sxs-lookup"><span data-stu-id="44546-144">In the **Tabs** section:</span></span>

1. <span data-ttu-id="44546-145">Na **guia Equipe,** selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="44546-145">Under **Team tab**, select **Add**.</span></span>

1. <span data-ttu-id="44546-146">Na janela **pop-up da guia** Equipe, atualize a URL de **configuração** para `https://<yourngrokurl>/tab` .</span><span class="sxs-lookup"><span data-stu-id="44546-146">In the **Team tab** pop-up window, update the **Configuration URL** to `https://<yourngrokurl>/tab`.</span></span>

1. <span data-ttu-id="44546-147">Verifique se as caixas de seleção Pode **atualizar configuração?**, **Equipe** e **Chat** de Grupo estão selecionadas e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="44546-147">Ensure the **Can update configuration?**, **Team**, and **Group chat** checkboxes are selected and select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="44546-148">Concluir: domínios e permissões</span><span class="sxs-lookup"><span data-stu-id="44546-148">Finish: Domains and permissions</span></span>

<span data-ttu-id="44546-149">Na seção **Domínios e** permissões, **domínios** de suas guias devem conter sua URL ngrok sem o prefixo HTTPS `<yourngrokurl>.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="44546-149">In the **Domains and permissions** section, **Domains from your tabs** must contain your ngrok URL without the HTTPS prefix `<yourngrokurl>.ngrok.io/`.</span></span>

#### <a name="finish-test-and-distribute"></a><span data-ttu-id="44546-150">Concluir: Testar e distribuir</span><span class="sxs-lookup"><span data-stu-id="44546-150">Finish: Test and distribute</span></span>

>[!IMPORTANT]
> <span data-ttu-id="44546-151">À direita, em **Descrição,** você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="44546-151">On the right, in **Description**, you see the following warning:</span></span>
>
> <span data-ttu-id="44546-152">&#9888; "**A matriz 'validDomains' não pode conter um site de tunelamento...**"</span><span class="sxs-lookup"><span data-stu-id="44546-152">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
> <span data-ttu-id="44546-153">Esse aviso pode ser ignorado durante o teste da guia.</span><span class="sxs-lookup"><span data-stu-id="44546-153">This warning can be ignored while testing your tab.</span></span>

1. <span data-ttu-id="44546-154">Na seção **Testar e Distribuir,** selecione **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="44546-154">In the **Test and Distribute** section, select **Install**.</span></span>

1. <span data-ttu-id="44546-155">Na caixa de diálogo pop-up, selecione **Adicionar a** uma equipe ou no drop-down, selecione Adicionar a **um chat**.</span><span class="sxs-lookup"><span data-stu-id="44546-155">In the pop-up dialog box, select **Add to a team** or from the drop-down, select **Add to a chat**.</span></span>

1. <span data-ttu-id="44546-156">Escolha a equipe ou o chat onde você deseja que a guia seja exibida e selecione **Configurar uma guia**.</span><span class="sxs-lookup"><span data-stu-id="44546-156">Choose the team or chat where you want the tab to be displayed and select **Set up a tab**.</span></span>

1. <span data-ttu-id="44546-157">Na próxima caixa de diálogo pop-up, escolha **Selecionar** Cinza ou **Selecionar Vermelho** e **selecione Salvar**.</span><span class="sxs-lookup"><span data-stu-id="44546-157">In the next pop-up dialog box, choose either **Select Gray** or **Select Red**, and select **Save**.</span></span>

1. <span data-ttu-id="44546-158">Para exibir sua guia, vá para a equipe onde você instalou a guia e selecione-a na barra de guias.</span><span class="sxs-lookup"><span data-stu-id="44546-158">To view your tab, go to the team where you installed the tab, and select it from the tab bar.</span></span> <span data-ttu-id="44546-159">A página escolhida durante a configuração é exibida.</span><span class="sxs-lookup"><span data-stu-id="44546-159">The page that you chose during configuration is displayed.</span></span>

    ![Guia canal ASPNETMVC carregado](../../assets/images/tab-images/channeltabaspnetmvcuploaded.png)

