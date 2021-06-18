### <a name="use-app-studio-to-update-the-app-package"></a><span data-ttu-id="42327-101">Usar o App Studio para atualizar o pacote de aplicativos</span><span class="sxs-lookup"><span data-stu-id="42327-101">Use App Studio to update the app package</span></span>

<span data-ttu-id="42327-102">O App Studio é um Teams que você pode instalar na Teams store.</span><span class="sxs-lookup"><span data-stu-id="42327-102">App Studio is a Teams app that you can install from the Teams store.</span></span> <span data-ttu-id="42327-103">Simplifica a criação e o registro de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="42327-103">It simplifies the creation and registration of an app.</span></span>

<span data-ttu-id="42327-104">Conclua as etapas a seguir para atualizar o pacote do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="42327-104">Complete the following steps to update the app package:</span></span>

1. <span data-ttu-id="42327-105">Para instalar o App Studio Teams, selecione o ícone **Aplicativos** na parte inferior da barra à esquerda e procure **o App Studio**:</span><span class="sxs-lookup"><span data-stu-id="42327-105">To install App Studio in Teams, select the **Apps** icon at the bottom of the left-hand bar, and search for **App Studio**:</span></span>

    <img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

1. <span data-ttu-id="42327-106">Selecione o **telha do App Studio** e escolha **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="42327-106">Select the **App Studio** tile and choose **Install**.</span></span> <span data-ttu-id="42327-107">O App Studio está instalado:</span><span class="sxs-lookup"><span data-stu-id="42327-107">The App Studio is installed:</span></span>

    <img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

1. <span data-ttu-id="42327-108">Para criar o pacote de aplicativos para seu Teams aplicativo, selecione a guia **Editor de manifesto** no App **Studio**:</span><span class="sxs-lookup"><span data-stu-id="42327-108">To create the app package for your Teams app, select the **Manifest editor** tab in **App Studio**:</span></span>

    <img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

    <span data-ttu-id="42327-109">O exemplo vem com seu próprio manifesto e foi projetado para criar um pacote de aplicativos quando o projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="42327-109">The sample comes with its own manifest and is designed to build an app package when the project is built.</span></span> <span data-ttu-id="42327-110">Você pode criar o pacote de aplicativos no .NET com Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="42327-110">You can build the app package on .NET with Visual Studio.</span></span> <span data-ttu-id="42327-111">Em Visual Studio, o arquivo manifest.json está localizado em **em Manifesto** em `Microsoft.Teams.Samples.HelloWorld.Web` .</span><span class="sxs-lookup"><span data-stu-id="42327-111">In Visual Studio, the manifest.json file is located in under **Manifest** in `Microsoft.Teams.Samples.HelloWorld.Web`.</span></span> <span data-ttu-id="42327-112">Esta etapa é descrita pela imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="42327-112">This step is described by the following image:</span></span>  
    
    <img  width="450px" alt="Build the app package on .NET with Visual Studio" src="~/assets/images/get-started/app-package-on-.NET-with-Visual-Studio.png"/>
    
    <span data-ttu-id="42327-113">Você pode criar o pacote do aplicativo Node.js digitando na linha de comando no `gulp` diretório raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="42327-113">You can build the app package on Node.js by typing `gulp` at the command line in the root directory of the project.</span></span>

    ```bash
    $ gulp
    [13:39:27] Using gulpfile ~\documents\github\msteams-samples-hello-world-nodejs\gulpfile.js
    [13:39:27] Starting 'clean'...
    [13:39:27] Starting 'generate-manifest'...
    [13:39:27] Finished 'generate-manifest' after 11 ms
    [13:39:27] Finished 'clean' after 21 ms
    [13:39:27] Starting 'default'...
    Build completed. Output in manifest folder
    [13:39:27] Finished 'default' after 62 μs
    ```

    <span data-ttu-id="42327-114">O nome do pacote de aplicativos gerado é **helloworldapp.zip**.</span><span class="sxs-lookup"><span data-stu-id="42327-114">The name of the generated app package is **helloworldapp.zip**.</span></span> <span data-ttu-id="42327-115">Você pode pesquisar esse arquivo se o local não estiver claro na ferramenta que você está usando.</span><span class="sxs-lookup"><span data-stu-id="42327-115">You can search for this file if the location is not clear in the tool you are using.</span></span>

1. <span data-ttu-id="42327-116">Agora, para modificar este pacote de aplicativos, selecione **Importar um aplicativo existente** no editor de **Manifesto:**</span><span class="sxs-lookup"><span data-stu-id="42327-116">Now to modify this app package, select **Import an existing app** in the **Manifest editor**:</span></span>

    <img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

1. <span data-ttu-id="42327-117">Selecione o **azulejo Hello World** para seu aplicativo recém-importado:</span><span class="sxs-lookup"><span data-stu-id="42327-117">Select the **Hello World** tile for your newly imported app:</span></span>

    <img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

<span data-ttu-id="42327-118">A imagem a seguir mostra o pacote de aplicativos importado no App Studio:</span><span class="sxs-lookup"><span data-stu-id="42327-118">The following image shows the imported app package in App Studio:</span></span>

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

<span data-ttu-id="42327-119">No lado esquerdo do editor de Manifesto há uma lista de etapas.</span><span class="sxs-lookup"><span data-stu-id="42327-119">On the left-hand side of the Manifest editor there is a list of steps.</span></span> <span data-ttu-id="42327-120">No lado direito, há uma lista de propriedades que precisam ser preenchidas para cada etapa.</span><span class="sxs-lookup"><span data-stu-id="42327-120">On the right-hand side there is a list of properties that need to be filled in for each step.</span></span> <span data-ttu-id="42327-121">Conforme você começou com um aplicativo de exemplo, grande parte das informações já foi concluída.</span><span class="sxs-lookup"><span data-stu-id="42327-121">As you started with a sample app, much of the information is already completed.</span></span> <span data-ttu-id="42327-122">As próximas etapas permitem que você atualize as propriedades do aplicativo Hello World.</span><span class="sxs-lookup"><span data-stu-id="42327-122">The next steps enable you to update the properties of the Hello World app.</span></span>

#### <a name="app-details"></a><span data-ttu-id="42327-123">Detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="42327-123">App details</span></span>

<span data-ttu-id="42327-124">Selecione **Detalhes do aplicativo** em **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="42327-124">Select **App details** under **Details**.</span></span> <span data-ttu-id="42327-125">Selecione o **botão Gerar** para criar uma nova ID do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="42327-125">Select the **Generate** button to create a new App ID.</span></span>

<span data-ttu-id="42327-126">Sua nova ID do aplicativo é semelhante a `2322041b-72bf-459d-b107-f4f335bc35bd` .</span><span class="sxs-lookup"><span data-stu-id="42327-126">Your new App ID is similar to `2322041b-72bf-459d-b107-f4f335bc35bd`.</span></span>

<span data-ttu-id="42327-127">Veja os detalhes do aplicativo no painel à direita, incluindo informações **do desenvolvedor** e detalhes **de identidade** visual.</span><span class="sxs-lookup"><span data-stu-id="42327-127">Go through the app details in the right-hand pane including **Developer information** and **Branding** details.</span></span> <span data-ttu-id="42327-128">Esses detalhes são importantes se você estiver escrevendo um novo aplicativo para distribuição.</span><span class="sxs-lookup"><span data-stu-id="42327-128">These details are important if you are writing a new app for distribution.</span></span>

#### <a name="tabs"></a><span data-ttu-id="42327-129">Guias</span><span class="sxs-lookup"><span data-stu-id="42327-129">Tabs</span></span>

<span data-ttu-id="42327-130">É simples adicionar guias a um Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="42327-130">It is simple to add tabs to a Teams app.</span></span> <span data-ttu-id="42327-131">O aplicativo de exemplo já dá suporte a várias guias e você pode habilita-las.</span><span class="sxs-lookup"><span data-stu-id="42327-131">The sample app already supports several tabs, and you can enable them.</span></span>

##### <a name="team-tab"></a><span data-ttu-id="42327-132">Guia Equipe</span><span class="sxs-lookup"><span data-stu-id="42327-132">Team tab</span></span>

<span data-ttu-id="42327-133">Seu aplicativo só pode ter uma guia Equipe:</span><span class="sxs-lookup"><span data-stu-id="42327-133">Your app can only have one Team tab:</span></span>

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

<span data-ttu-id="42327-134">Neste exemplo, a guia Equipe é onde sua página de configuração é exibida.</span><span class="sxs-lookup"><span data-stu-id="42327-134">In this sample, the Team tab is where your configuration page is displayed.</span></span> <span data-ttu-id="42327-135">Selecione o **símbolo ...** da url de configuração **de tabulação** e escolha **Editar** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="42327-135">Select the **...** symbol of the **Tab configuration url** and choose **Edit** from the drop-down menu.</span></span> <span data-ttu-id="42327-136">Altere a URL para onde deve ser substituída pela URL que `https://yourteamsapp.ngrok.io/configure` você usou ao hospedar seu `yourteamsapp.ngrok.io` [aplicativo](#host-the-sample-app).</span><span class="sxs-lookup"><span data-stu-id="42327-136">Change the URL to `https://yourteamsapp.ngrok.io/configure` where `yourteamsapp.ngrok.io` must be replaced with the URL that you used when [hosting your app](#host-the-sample-app).</span></span>

##### <a name="personal-tabs"></a><span data-ttu-id="42327-137">Guias pessoais</span><span class="sxs-lookup"><span data-stu-id="42327-137">Personal tabs</span></span>

<span data-ttu-id="42327-138">Seu aplicativo pode ter até 16 guias, incluindo a guia Equipe.</span><span class="sxs-lookup"><span data-stu-id="42327-138">Your app can have up to 16 tabs, including the Team tab.</span></span>

<span data-ttu-id="42327-139">As guias pessoais são diferentes da guia Equipe. A Guia **Hello** já está listada na lista de guias pessoais com um valor de espaço reservado `com.contoso.helloworld.hellotab` .</span><span class="sxs-lookup"><span data-stu-id="42327-139">Personal tabs are different from the Team tab. **Hello Tab** is already listed in the personal tabs list with a placeholder value `com.contoso.helloworld.hellotab`.</span></span> <span data-ttu-id="42327-140">Selecione o **símbolo ...** da url de configuração **de tabulação** e escolha **Editar** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="42327-140">Select the **...** symbol of the **Tab configuration url** and choose **Edit** from the drop-down menu.</span></span> <span data-ttu-id="42327-141">A caixa de diálogo a seguir é exibida:</span><span class="sxs-lookup"><span data-stu-id="42327-141">The following dialog box appears:</span></span>

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

<span data-ttu-id="42327-142">Atualize as caixas a seguir com a URL do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="42327-142">Update the following boxes with your app URL:</span></span>

- <span data-ttu-id="42327-143">Alterar a **caixa URL** de conteúdo para `https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="42327-143">Change the **Content URL** box to `https://yourteamsapp.ngrok.io/hello`</span></span>
- <span data-ttu-id="42327-144">Alterar a **caixa URL do** site para `https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="42327-144">Change the **Website URL** box to `https://yourteamsapp.ngrok.io/hello`</span></span>

<span data-ttu-id="42327-145">Substitua `yourteamsapp.ngrok.io` pela URL que você usou ao hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="42327-145">Replace `yourteamsapp.ngrok.io` by the URL that you used when hosting your app.</span></span>

#### <a name="bots"></a><span data-ttu-id="42327-146">Bots</span><span class="sxs-lookup"><span data-stu-id="42327-146">Bots</span></span>

<span data-ttu-id="42327-147">É fácil adicionar a funcionalidade de bots ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="42327-147">It is easy to add the bots functionality to your app.</span></span> <span data-ttu-id="42327-148">O aplicativo de exemplo **Hello World** já tem um bot como parte do exemplo, mas você deve registrá-lo com a Microsoft:</span><span class="sxs-lookup"><span data-stu-id="42327-148">The **Hello World** sample app already has a bot as part of the sample, but you must register it with Microsoft:</span></span>

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

<span data-ttu-id="42327-149">O bot importado do exemplo não tem uma ID de aplicativo associada.</span><span class="sxs-lookup"><span data-stu-id="42327-149">The bot that was imported from the sample does not have an associated App ID.</span></span> <span data-ttu-id="42327-150">Você deve criar um novo bot para que o App Studio possa criar uma nova ID de aplicativo e registrá-la na Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42327-150">You must create a new bot so that App Studio can create a new App ID and register it with Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="42327-151">A ID do aplicativo criada pelo App Studio para o bot é diferente da ID do aplicativo criada para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="42327-151">The App ID created by App Studio for the bot is different from the App ID created for the app.</span></span> <span data-ttu-id="42327-152">Cada bot em um aplicativo requer sua própria ID de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="42327-152">Each bot in an app requires its own App ID.</span></span>

<span data-ttu-id="42327-153">Conclua as etapas a seguir para configurar seu bot:</span><span class="sxs-lookup"><span data-stu-id="42327-153">Complete the following steps to setup your bot:</span></span>

1. <span data-ttu-id="42327-154">Selecione **Excluir** ao lado do bot importado na lista de bots.</span><span class="sxs-lookup"><span data-stu-id="42327-154">Select **Delete** next to the imported bot in the bot list.</span></span> <span data-ttu-id="42327-155">Agora não há mais bots para mostrar.</span><span class="sxs-lookup"><span data-stu-id="42327-155">Now there are no bots left to show.</span></span> 
1. <span data-ttu-id="42327-156">Selecione **Configurar para** exibir a caixa de diálogo Configurar um **bot.**</span><span class="sxs-lookup"><span data-stu-id="42327-156">Select **Setup** to display the **Set up a bot** dialog box.</span></span>

    <img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

1. <span data-ttu-id="42327-157">Adicione um bot nome **contoso bot** e selecione todas as três caixas de seleção em **Escopo**.</span><span class="sxs-lookup"><span data-stu-id="42327-157">Add a bot name **Contoso bot** and select all three check boxes under **Scope**.</span></span>
1. <span data-ttu-id="42327-158">Escolha **Salvar** para sair da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="42327-158">Choose **Save** to exit the dialog box.</span></span> <span data-ttu-id="42327-159">O App Studio registra seu bot com a Microsoft e exibe seu novo bot na lista de bots.</span><span class="sxs-lookup"><span data-stu-id="42327-159">App Studio registers your bot with Microsoft and displays your new bot in the bot list.</span></span> 
1. <span data-ttu-id="42327-160">Agora abra um arquivo de texto no bloco de notas e copie e colar sua nova ID de bot nele.</span><span class="sxs-lookup"><span data-stu-id="42327-160">Now open a text file in notepad and copy and paste your new bot ID into it.</span></span>
1. <span data-ttu-id="42327-161">Clique **em Gerar Nova Senha** e anote a senha no mesmo arquivo de texto que você anotou a ID do aplicativo bot.</span><span class="sxs-lookup"><span data-stu-id="42327-161">Click **Generate New Password**, and note the password in the same text file you noted your bot App ID.</span></span>
1. <span data-ttu-id="42327-162">Atualize **o endereço de ponto de** extremidade bot para e substitua pela URL que você usou ao hospedar seu `https://yourteamsapp.ngrok.io/api/messages` `yourteamsapp.ngrok.io` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="42327-162">Update the **Bot endpoint address** to `https://yourteamsapp.ngrok.io/api/messages`, and replace `yourteamsapp.ngrok.io` with the URL that you used when hosting your app.</span></span>
1. <span data-ttu-id="42327-163">Agora salve seu arquivo de texto, pois você deve adicionar as informações do arquivo ao seu aplicativo hospedado para permitir a comunicação segura com seu bot.</span><span class="sxs-lookup"><span data-stu-id="42327-163">Now save your text file as you must add the information from the file to your hosted app to allow secure communication with your bot.</span></span>

#### <a name="messaging-extensions"></a><span data-ttu-id="42327-164">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="42327-164">Messaging extensions</span></span>

<span data-ttu-id="42327-165">As extensões de mensagens permitem que os usuários peçam informações do seu serviço e postem essas informações.</span><span class="sxs-lookup"><span data-stu-id="42327-165">Messaging extensions let users ask for information from your service and post that information.</span></span> <span data-ttu-id="42327-166">As informações são postadas na forma de cartões na conversa do canal.</span><span class="sxs-lookup"><span data-stu-id="42327-166">The information is posted in the form of cards into the channel conversation.</span></span> <span data-ttu-id="42327-167">As extensões de mensagens aparecem na parte inferior da caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="42327-167">Messaging extensions appear at the bottom of the compose box.</span></span>

<span data-ttu-id="42327-168">Conclua as etapas a seguir para configurar sua extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="42327-168">Complete the following steps to setup your messaging extension:</span></span>

1. <span data-ttu-id="42327-169">Selecione **Extensões de mensagens** em **Recursos** no painel esquerdo do App Studio para configurar a extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="42327-169">Select **Messaging extensions** under **Capabilities** in the left-hand pane of App Studio to configure the messaging extension:</span></span>

    <img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

    <span data-ttu-id="42327-170">A extensão de mensagens de exemplo está listada no painel **Extensões de** Mensagens.</span><span class="sxs-lookup"><span data-stu-id="42327-170">The sample messaging extension is listed in the **Messaging Extensions** pane.</span></span>

1. <span data-ttu-id="42327-171">Selecione **Excluir** para remover a extensão de mensagens, selecione **Configurar** e siga as mesmas etapas usadas para [bots](#bots).</span><span class="sxs-lookup"><span data-stu-id="42327-171">Select **Delete** to remove the messaging extension, select **Set up**, and follow the same steps used for [bots](#bots).</span></span> <span data-ttu-id="42327-172">A **caixa de diálogo Extensão** de Mensagens é exibida.</span><span class="sxs-lookup"><span data-stu-id="42327-172">The **Messaging Extension** dialog box is displayed.</span></span>
1. <span data-ttu-id="42327-173">Selecione a **guia Usar bot existente** e Selecione de um dos meus **bots existentes.**</span><span class="sxs-lookup"><span data-stu-id="42327-173">Select the **Use existing bot** tab and **Select from one of my existing bots**.</span></span>
1. <span data-ttu-id="42327-174">Selecione o bot criado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="42327-174">Select the bot you created from the drop-down menu.</span></span> <span data-ttu-id="42327-175">Adicione um **nome de Bot** e selecione **Salvar** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="42327-175">Add a **Bot name** and select **Save** to close the dialog box.</span></span>
1. <span data-ttu-id="42327-176">Na seção **Comando,** selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="42327-176">Under the **Command** section, select **Add**.</span></span> <span data-ttu-id="42327-177">Para adicionar um comando baseado em pesquisa, selecione a opção Permitir que os usuários consultem seu serviço para obter informações e **insira-o em uma opção de** mensagem.</span><span class="sxs-lookup"><span data-stu-id="42327-177">To add a search-based command, select the **Allow users to query your service for information and insert that into a message** option.</span></span>
1. <span data-ttu-id="42327-178">Na caixa **de diálogo** Novo comando, insira os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="42327-178">In the **New command** dialog box, enter the following values:</span></span>

    <span data-ttu-id="42327-179">Em **Novo comando**:</span><span class="sxs-lookup"><span data-stu-id="42327-179">Under **New command**:</span></span>

    - <span data-ttu-id="42327-180">**ID do comando**: Insira texto aleatório</span><span class="sxs-lookup"><span data-stu-id="42327-180">**Command ID**: Enter random text</span></span>
    - <span data-ttu-id="42327-181">**Título**: Insira título aleatório</span><span class="sxs-lookup"><span data-stu-id="42327-181">**Title**: Enter random title</span></span>
    - <span data-ttu-id="42327-182">**Descrição**: Insira a descrição aleatória</span><span class="sxs-lookup"><span data-stu-id="42327-182">**Description**: Enter random description</span></span>

    <span data-ttu-id="42327-183">Em **Parâmetro**:</span><span class="sxs-lookup"><span data-stu-id="42327-183">Under **Parameter**:</span></span>

    - <span data-ttu-id="42327-184">**Nome**: Insira o nome do parâmetro</span><span class="sxs-lookup"><span data-stu-id="42327-184">**Name**: Enter the parameter name</span></span>
    - <span data-ttu-id="42327-185">**Título**: Insira o título do cartão</span><span class="sxs-lookup"><span data-stu-id="42327-185">**Title**: Enter the card title</span></span>
    - <span data-ttu-id="42327-186">**Descrição**: Insira a descrição do cartão</span><span class="sxs-lookup"><span data-stu-id="42327-186">**Description**: Enter card description</span></span>

1. <span data-ttu-id="42327-187">Depois de inserir as informações, selecione **Salvar** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="42327-187">After you enter the information, select **Save** to close the dialog box.</span></span>

#### <a name="register-your-app-in-teams"></a><span data-ttu-id="42327-188">Registre seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="42327-188">Register your app in Teams</span></span>

<span data-ttu-id="42327-189">Depois de inserir os detalhes do seu aplicativo, conclua as seguintes etapas para registrar seu aplicativo Teams:</span><span class="sxs-lookup"><span data-stu-id="42327-189">After entering the details of your app, complete the following steps to register your app in Teams:</span></span>

1. <span data-ttu-id="42327-190">Use **Test and distribute** of App Studio to install your app in Teams.</span><span class="sxs-lookup"><span data-stu-id="42327-190">Use **Test and distribute** of App Studio to install your app in Teams.</span></span> 
1. <span data-ttu-id="42327-191">Atualize seu aplicativo hospedado com a ID do aplicativo e a senha do bot.</span><span class="sxs-lookup"><span data-stu-id="42327-191">Update your hosted application with the App ID and password for your bot.</span></span> <span data-ttu-id="42327-192">Para o aplicativo de exemplo, use a mesma ID de aplicativo e senha para bot e extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="42327-192">For the sample app, use the same App ID and password for both bot and messaging extension.</span></span> 
1. <span data-ttu-id="42327-193">Selecione **Testar e distribuir**  em **Concluir** no painel esquerdo do App Studio:</span><span class="sxs-lookup"><span data-stu-id="42327-193">Select **Test and distribute**  under **Finish** in the left-hand pane of App Studio:</span></span>

    <img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

1. <span data-ttu-id="42327-194">Para carregar seu aplicativo no Teams, selecione o botão **Instalar** em **Testar e Distribuir:**</span><span class="sxs-lookup"><span data-stu-id="42327-194">To upload your app to Teams, select the **Install** button under **Test and Distribute**:</span></span>

    <img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

1. <span data-ttu-id="42327-195">Selecione a **caixa Pesquisar** na seção Adicionar a **uma equipe** e selecione uma equipe para adicionar o aplicativo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="42327-195">Select the **Search** box in the **Add to a team** section and select a team to add the sample app.</span></span> <span data-ttu-id="42327-196">Você pode configurar uma equipe especial para teste.</span><span class="sxs-lookup"><span data-stu-id="42327-196">You can set up a special team for testing.</span></span>
1. <span data-ttu-id="42327-197">Selecione o **botão Instalar** na parte inferior da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="42327-197">Select the **Install** button at the bottom of the dialog box.</span></span>

<span data-ttu-id="42327-198">Seu aplicativo agora está disponível no Teams.</span><span class="sxs-lookup"><span data-stu-id="42327-198">Your app is now available in Teams.</span></span> <span data-ttu-id="42327-199">No entanto, o bot e a extensão de mensagens não funcionarão até que você atualize o ambiente de aplicativos hospedados com as IDs de aplicativo e senhas.</span><span class="sxs-lookup"><span data-stu-id="42327-199">However, the bot and the messaging extension will not work until you update the hosted applications environment with the App IDs and passwords.</span></span>

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
