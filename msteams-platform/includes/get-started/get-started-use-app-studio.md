### <a name="use-app-studio-to-update-the-app-package"></a><span data-ttu-id="04371-101">Usar o app Studio para atualizar o pacote de aplicativos</span><span class="sxs-lookup"><span data-stu-id="04371-101">Use App Studio to update the app package</span></span>

<span data-ttu-id="04371-102">O app Studio é um aplicativo do teams que você pode instalar a partir da loja do teams.</span><span class="sxs-lookup"><span data-stu-id="04371-102">App Studio is a Teams app that you can install from the Teams store.</span></span> <span data-ttu-id="04371-103">Ele simplifica a criação e o registro de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04371-103">It simplifies the creation and registration of an app.</span></span>

<span data-ttu-id="04371-104">Para instalar o app Studio no Microsoft Teams, clique no ícone do repositório de aplicativos na parte inferior da barra esquerda e pesquise o app Studio.</span><span class="sxs-lookup"><span data-stu-id="04371-104">To install App Studio in Teams, click on the app store icon at the bottom of the left hand bar, and search for App Studio.</span></span>

<img  width="450px" title="Localizando o app Studio no repositório" src="~/assets/images/get-started/app-studio-store.png"/>

<span data-ttu-id="04371-106">Depois de encontrar o bloco para o app Studio, clique nele e escolha *instalar* na caixa de diálogo exibida.</span><span class="sxs-lookup"><span data-stu-id="04371-106">Once you find the tile for App Studio, click on it and choose *install* in the dialog that pops up.</span></span>

<img  width="450px" title="Instalando o app Studio" src="~/assets/images/get-started/app-studio-install.png"/>

<span data-ttu-id="04371-108">Após a instalação do App Studio, clique na guia Editor de manifesto para começar a criar o pacote de aplicativos para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="04371-108">Once App Studio is installed click on the Manifest editor tab to begin creating the app package for your Teams app.</span></span>

<img  width="450px" title="App Studio" src="~/assets/images/get-started/app-studio.png"/>

<span data-ttu-id="04371-110">O exemplo vem com seu próprio manifesto predefinido e foi projetado para compilar um pacote de aplicativos quando o projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="04371-110">The sample comes with its own pre-made manifest, and is designed to build an app package when the project is built.</span></span> <span data-ttu-id="04371-111">No .NET, isso é feito no Visual Studio e no nó JS isso é feito digitando `gulp` na linha de comando no diretório raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="04371-111">On .NET this is done in Visual Studio, and on Node JS this is done by typing `gulp` at the command line in the root directory of the project.</span></span>

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

<span data-ttu-id="04371-112">O nome do pacote de aplicativos gerado é *HelloWorldApp. zip*.</span><span class="sxs-lookup"><span data-stu-id="04371-112">The name of the generated app package is *helloworldapp.zip*.</span></span> <span data-ttu-id="04371-113">Você pode pesquisar esse arquivo se o local não estiver limpo na ferramenta que você está usando.</span><span class="sxs-lookup"><span data-stu-id="04371-113">You can search for this file if the location is not clear in the tool you are using.</span></span>

<span data-ttu-id="04371-114">Na próxima parte desta explicação passo a passo, você irá modificar esse pacote de aplicativos selecionando o bloco *importar um aplicativo existente* no editor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="04371-114">In the next part of this walkthrough you are going to modify this app package by selecting the *Import an existing app* tile in the Manifest Editor.</span></span>

<img  width="450px" title="Importando um aplicativo" src="~/assets/images/get-started/app-studio-import.png"/>

<span data-ttu-id="04371-116">Depois que o pacote do aplicativo tiver sido importado, o app Studio deverá ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="04371-116">Once the app package has been imported App Studio should look like this:</span></span>

<img  width="450px" title="Importando um aplicativo" src="~/assets/images/get-started/app-studio-imported-app.png"/>

<span data-ttu-id="04371-118">Clique no bloco para seu aplicativo recentemente importado, *Olá mundo*.</span><span class="sxs-lookup"><span data-stu-id="04371-118">Click on the tile for your newly imported app, *Hello World*.</span></span>

<img  width="450px" title="Importando um aplicativo" src="~/assets/images/get-started/app-studio-manifest-editor.png"/>

<span data-ttu-id="04371-120">Há uma lista de etapas no lado esquerdo do editor de manifestos e, à direita, uma lista de propriedades que precisam ser preenchidas para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="04371-120">There is a list of steps in the left-hand side of the Manifest editor, and on the right a list of properties that need to be filled in for each of those steps.</span></span> <span data-ttu-id="04371-121">Desde que você começou com um exemplo de aplicativo, muitas das informações já estão preenchidas. As etapas a seguir irão orientá-lo durante a alteração das partes que ainda precisam ser atualizadas.</span><span class="sxs-lookup"><span data-stu-id="04371-121">Since you started with a sample app, much of the information is already filled out. The next steps will walk you through changing the parts that still need to be updated.</span></span>

#### <a name="app-details"></a><span data-ttu-id="04371-122">Detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="04371-122">App details</span></span>

<span data-ttu-id="04371-123">Clique na entrada de *detalhes do aplicativo* em *detalhes*.</span><span class="sxs-lookup"><span data-stu-id="04371-123">Click on the *App details* entry under *Details*.</span></span> <span data-ttu-id="04371-124">Clique no botão *gerar* para criar uma nova ID de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04371-124">Click the *Generate* button to create a new app id.</span></span>

<span data-ttu-id="04371-125">Sua nova ID de aplicativo deve ser semelhante a `2322041b-72bf-459d-b107-f4f335bc35bd`:.</span><span class="sxs-lookup"><span data-stu-id="04371-125">Your new app id should look something like: `2322041b-72bf-459d-b107-f4f335bc35bd`.</span></span>

<span data-ttu-id="04371-126">Examine o restante dos detalhes do aplicativo no painel à direita e familiarize-se com algumas das entradas, como informações de *desenvolvedor* e *identidade visual*.</span><span class="sxs-lookup"><span data-stu-id="04371-126">Look through the rest of the App details in the right hand pane, and familiarize yourself with some of the entries such as *Developer information* and *Branding*.</span></span> <span data-ttu-id="04371-127">Essas seções são importantes se você estiver escrevendo um novo aplicativo para distribuição.</span><span class="sxs-lookup"><span data-stu-id="04371-127">These sections are important if you are writing a new app for distribution.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="04371-128">Recursos: guias</span><span class="sxs-lookup"><span data-stu-id="04371-128">Capabilities: Tabs</span></span>

<span data-ttu-id="04371-129">As guias estão entre os elementos mais simples a serem adicionados a um aplicativo do teams.</span><span class="sxs-lookup"><span data-stu-id="04371-129">Tabs are among the simplest elements to add to a Teams app.</span></span> <span data-ttu-id="04371-130">O aplicativo de exemplo já oferece suporte a várias guias, e você pode habilitá-los da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="04371-130">The sample app already supports several tabs, and you can enable them as follows.</span></span>

##### <a name="team-tab"></a><span data-ttu-id="04371-131">Guia equipe</span><span class="sxs-lookup"><span data-stu-id="04371-131">Team tab</span></span>

<span data-ttu-id="04371-132">Seu aplicativo pode ter apenas uma guia de equipe.</span><span class="sxs-lookup"><span data-stu-id="04371-132">Your app can only have one Team tab.</span></span>

<img  width="450px" title="Adicionando uma guia do teams" src="~/assets/images/get-started/app-studio-manifest-editor-tabs.png"/>

<span data-ttu-id="04371-134">Neste exemplo, a guia equipe é onde a página de configuração vai.</span><span class="sxs-lookup"><span data-stu-id="04371-134">In this sample, the Team tab is where your configuration page goes.</span></span> <span data-ttu-id="04371-135">Clique no símbolo *...* no final da entrada e escolha *Editar* na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="04371-135">Click on the *...* symbol at the end of the entry and choose *Edit* from the drop-down.</span></span> <span data-ttu-id="04371-136">Altere a URL para `https://yourteamsapp.ngrok.io/configure` onde `yourteamsapp.ngrok.io` ela deve ser substituída pela URL que você usou acima ao hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04371-136">Change the URL to `https://yourteamsapp.ngrok.io/configure` where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

##### <a name="personal-tabs"></a><span data-ttu-id="04371-137">Guias pessoais</span><span class="sxs-lookup"><span data-stu-id="04371-137">Personal tabs</span></span>

<span data-ttu-id="04371-138">Seu aplicativo pode ter até 16 guias, incluindo a guia equipe.</span><span class="sxs-lookup"><span data-stu-id="04371-138">Your app can have up to 16 tabs, including the team tab.</span></span>

<span data-ttu-id="04371-139">As guias pessoais são representadas de forma diferente da guia equipe. Você deve ver a *guia saudação* já listada na lista guias pessoais.</span><span class="sxs-lookup"><span data-stu-id="04371-139">Personal tabs are represented differently from the team tab. You should see *Hello Tab* already listed in the personal tabs list.</span></span> <span data-ttu-id="04371-140">No momento, ele tem um valor `com.contoso.helloworld.hellotab`de espaço reservado.</span><span class="sxs-lookup"><span data-stu-id="04371-140">At the moment it has a placeholder value `com.contoso.helloworld.hellotab`.</span></span> <span data-ttu-id="04371-141">Clique no símbolo *...* no final da entrada e escolha *Editar* na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="04371-141">Click on the *...* symbol at the end of the entry and choose *Edit* from the drop-down.</span></span> <span data-ttu-id="04371-142">A caixa de diálogo a seguir será exibida.</span><span class="sxs-lookup"><span data-stu-id="04371-142">The following dialog will appear.</span></span>

<img  width="450px" title="Adicionar uma caixa de diálogo de guia pessoal" src="~/assets/images/get-started/app-studio-manifest-editor-p-tabs-dialog.png"/>

<span data-ttu-id="04371-144">Há dois campos que você precisa atualizar com a URL do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04371-144">There are two fields that you need to update with your app URL.</span></span>

- <span data-ttu-id="04371-145">Alterar URL de conteúdo para`https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="04371-145">Change Content URL to `https://yourteamsapp.ngrok.io/hello`</span></span>
- <span data-ttu-id="04371-146">Altere a URL do site para`https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="04371-146">Change Website URL to `https://yourteamsapp.ngrok.io/hello`</span></span>

<span data-ttu-id="04371-147">Onde `yourteamsapp.ngrok.io` o deve ser substituído pela URL que você usou acima ao hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04371-147">Where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

#### <a name="bots"></a><span data-ttu-id="04371-148">Bots</span><span class="sxs-lookup"><span data-stu-id="04371-148">Bots</span></span>

<span data-ttu-id="04371-149">Os bots são a maneira mais comum de adicionar funcionalidade ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04371-149">Bots are the most common way to add functionality to your app.</span></span> <span data-ttu-id="04371-150">O exemplo Hello World já tem um bot como parte da amostra, mas ainda não foi registrado com a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="04371-150">The hello world sample already has a bot as part of the sample, but it has not been registered with Microsoft yet.</span></span>

<img  width="450px" title="Adicionar um bot" src="~/assets/images/get-started/app-studio-manifest-editor-bots.png"/>

<span data-ttu-id="04371-152">O bot que foi importado do exemplo ainda não tem uma ID de aplicativo associada a ele.</span><span class="sxs-lookup"><span data-stu-id="04371-152">The bot that was imported from the sample does not have an App ID associated with it yet.</span></span> <span data-ttu-id="04371-153">Você precisará criar um novo bot para que o app Studio possa criar uma nova ID de aplicativo e registrá-lo com a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="04371-153">You will have to create a new bot so that App Studio can create a new App ID and register it with Microsoft.</span></span> <span data-ttu-id="04371-154">Observe que esta é a ID do aplicativo do bot, que é diferente da ID do aplicativo que criamos para o aplicativo em uma etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="04371-154">Note that this is the App ID for the bot, which is different from the App ID that we created for the app in a earlier step.</span></span> <span data-ttu-id="04371-155">Cada bot em um aplicativo requer sua própria ID de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04371-155">Each bot in an app requires its own App ID.</span></span>

<span data-ttu-id="04371-156">Clique no botão *excluir* ao lado do *bot importado* na lista bot.</span><span class="sxs-lookup"><span data-stu-id="04371-156">Click the *delete* button next to the *Imported bot* in the bot list.</span></span>

<span data-ttu-id="04371-157">Agora não há bots para mostrar.</span><span class="sxs-lookup"><span data-stu-id="04371-157">Now there are no bots left to show.</span></span> <span data-ttu-id="04371-158">Clique em *Configurar*.</span><span class="sxs-lookup"><span data-stu-id="04371-158">Click *Setup*.</span></span> <span data-ttu-id="04371-159">Isso exibirá a caixa de diálogo *configurar um bot* .</span><span class="sxs-lookup"><span data-stu-id="04371-159">This will display the *Set up a bot* dialog.</span></span>

<img  width="450px" title="Adicionar uma caixa de diálogo de bot" src="~/assets/images/get-started/app-studio-manifest-editor-bots-setup-dialog.png"/>

<span data-ttu-id="04371-161">Adicione um nome de bot, `Contoso bot`como e clique em ambos os botões em *escopo*.</span><span class="sxs-lookup"><span data-stu-id="04371-161">Add a bot name such as `Contoso bot`, and click both the buttons under *scope*.</span></span>

<span data-ttu-id="04371-162">Escolha *criar bot* para sair da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="04371-162">Choose *Create bot* to exit the dialog.</span></span> <span data-ttu-id="04371-163">O app Studio gastará um momento registrando seu bot com a Microsoft e, em seguida, deverá exibir o novo bot na lista de bot.</span><span class="sxs-lookup"><span data-stu-id="04371-163">App Studio will spend a moment registering your bot with Microsoft, and then should display your new bot in the bot list.</span></span> <span data-ttu-id="04371-164">Agora seria uma boa hora para abrir um arquivo de texto no bloco de notas e copiar e colar sua nova ID de bot nela.</span><span class="sxs-lookup"><span data-stu-id="04371-164">Now would be a good time to open a text file in notepad and copy and paste your new bot id into it.</span></span> <span data-ttu-id="04371-165">Você precisará dessa ID mais tarde.</span><span class="sxs-lookup"><span data-stu-id="04371-165">You will need this id later.</span></span>

<span data-ttu-id="04371-166">Clique em *gerar nova senha*e anote a senha no mesmo arquivo de texto em que você ANOTOU a ID do aplicativo do bot.</span><span class="sxs-lookup"><span data-stu-id="04371-166">Click *Generate New Password*, and make a note of the password in the same text file you noted your Bot app ID in.</span></span> <span data-ttu-id="04371-167">Esta é a única vez que a senha será mostrada, portanto, certifique-se de fazer isso agora.</span><span class="sxs-lookup"><span data-stu-id="04371-167">This is the only time your password will be shown, so be sure to do this now.</span></span>

<span data-ttu-id="04371-168">Atualize o *endereço do ponto* de `https://yourteamsapp.ngrok.io/api/messages`extremidade do `yourteamsapp.ngrok.io` bot para, onde deve ser substituído pela URL que você usou acima ao hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04371-168">Update the *Bot endpoint address* to `https://yourteamsapp.ngrok.io/api/messages`, where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

<span data-ttu-id="04371-169">Agora seria uma boa hora para salvar seu arquivo de texto se você ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="04371-169">Now would be a good time to save your text file if you have not done so already.</span></span> <span data-ttu-id="04371-170">Você adicionará essas informações ao seu aplicativo hospedado posteriormente nesta explicação passo a passo, que permitirá a comunicação segura com o bot.</span><span class="sxs-lookup"><span data-stu-id="04371-170">You will add this information to your hosted app later in this walkthrough, which will allow secure communication with your bot.</span></span>

#### <a name="messaging-extensions"></a><span data-ttu-id="04371-171">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="04371-171">Messaging extensions</span></span>

<span data-ttu-id="04371-172">As extensões de mensagens permitem aos usuários solicitar informações do seu serviço e postá-las, na forma de cartões, diretamente na conversa do canal.</span><span class="sxs-lookup"><span data-stu-id="04371-172">Messaging extensions let users ask for information from your service and post that information, in the form of cards, right into the channel conversation.</span></span> <span data-ttu-id="04371-173">As extensões de mensagens aparecem ao longo da parte inferior da caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="04371-173">Messaging extensions appear along the bottom of the compose box.</span></span>

<span data-ttu-id="04371-174">Clique em *extensões de mensagens* em *recursos* na coluna esquerda do App Studio para começar a configurar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="04371-174">Click on *Messaging extensions* under *Capabilities* in the left hand column of App Studio to begin configuring the messaging extension.</span></span>

<img  width="450px" title="Adicionando uma extensão de mensagens" src="~/assets/images/get-started/app-studio-manifest-editor-mess-ext.png"/>

<span data-ttu-id="04371-176">O exemplo de extensão de mensagens está listado no painel direito em *extensões de mensagens*.</span><span class="sxs-lookup"><span data-stu-id="04371-176">The sample messaging extension is listed in the right hand pane under *Messaging Extensions*.</span></span> <span data-ttu-id="04371-177">Clique em *excluir* novamente para remover essa entrada e clique no botão *Configurar* seguindo as mesmas etapas que você seguiu para os bots.</span><span class="sxs-lookup"><span data-stu-id="04371-177">Click *Delete* again to remove this entry, and then click the *Set up* button following the same steps as you followed for bots.</span></span> <span data-ttu-id="04371-178">Isso exibirá a caixa de diálogo *extensão de mensagens* .</span><span class="sxs-lookup"><span data-stu-id="04371-178">This will display the *Messaging Extension* dialog.</span></span>

<span data-ttu-id="04371-179">Selecione a guia *usar bot existente* e, em seguida, *Selecione um dos meus bots existentes*.</span><span class="sxs-lookup"><span data-stu-id="04371-179">Select the *Use existing bot* tab, then *Select from one of my existing bots*.</span></span> <span data-ttu-id="04371-180">No menu suspenso, selecione o bot que você criou na seção acima.</span><span class="sxs-lookup"><span data-stu-id="04371-180">In the drop-down menu, select the bot you created in the section above.</span></span> <span data-ttu-id="04371-181">Adicione um *nome de bot* e clique em *salvar* para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="04371-181">Add a *Bot name* and click *Save* to close the dialog.</span></span>

<span data-ttu-id="04371-182">Na seção *comando* , clique em *Adicionar*.</span><span class="sxs-lookup"><span data-stu-id="04371-182">Under the *Command* section, click *Add*.</span></span> <span data-ttu-id="04371-183">Estamos adicionando um comando baseado em pesquisa, portanto, escolha a opção *permitir que os usuários consultem seu serviço...* .</span><span class="sxs-lookup"><span data-stu-id="04371-183">We're adding a search-based command, so choose the *Allow users to query your service...* option.</span></span>

<span data-ttu-id="04371-184">Na caixa de diálogo *novo comando* , insira os seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="04371-184">In the *New command* dialog enter the following values.</span></span>

<span data-ttu-id="04371-185">Em *novo comando*:</span><span class="sxs-lookup"><span data-stu-id="04371-185">Under *New command*:</span></span>

- <span data-ttu-id="04371-186">*ID do comando* = getRandomText</span><span class="sxs-lookup"><span data-stu-id="04371-186">*Command ID*  = getRandomText</span></span>
- <span data-ttu-id="04371-187">*Título* = obter texto aleatório para diversão</span><span class="sxs-lookup"><span data-stu-id="04371-187">*Title*       = Get some random text for fun</span></span>
- <span data-ttu-id="04371-188">*Descrição* = Obtém alguns textos e imagens aleatórias</span><span class="sxs-lookup"><span data-stu-id="04371-188">*Description* = Gets some random text and images</span></span>

<span data-ttu-id="04371-189">Em *Parameter*:</span><span class="sxs-lookup"><span data-stu-id="04371-189">Under *Parameter*:</span></span>

- <span data-ttu-id="04371-190">*Name* = cardTitle</span><span class="sxs-lookup"><span data-stu-id="04371-190">*Name*        = cardTitle</span></span>
- <span data-ttu-id="04371-191">*Título* = título do cartão</span><span class="sxs-lookup"><span data-stu-id="04371-191">*Title*       = Card title</span></span>
- <span data-ttu-id="04371-192">*Descrição* = título do cartão a ser usado</span><span class="sxs-lookup"><span data-stu-id="04371-192">*Description* = Card title to use</span></span>

<span data-ttu-id="04371-193">Depois de inserir as informações, clique em *salvar* para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="04371-193">Once you're entered the information, click *Save* to close the dialog.</span></span>

#### <a name="register-your-app-in-teams"></a><span data-ttu-id="04371-194">Registrar seu aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="04371-194">Register your app in Teams</span></span>

<span data-ttu-id="04371-195">Você já concluiu a inserção dos detalhes do seu aplicativo, mas duas etapas permanecem.</span><span class="sxs-lookup"><span data-stu-id="04371-195">You have now completed entering the details of your app, but two steps remain.</span></span> <span data-ttu-id="04371-196">Primeiro, você deve usar a seção testar e distribuir do App Studio para instalar seu aplicativo no Microsoft Teams e, em seguida, você deve atualizar seu aplicativo hospedado com a ID do aplicativo e a senha do bot.</span><span class="sxs-lookup"><span data-stu-id="04371-196">First you must use the Test and Distribute section of App Studio to install your app in Teams, and second you must update your hosted application with the App ID and password for your bot.</span></span> <span data-ttu-id="04371-197">Lembre-se de que o exemplo espera usar a mesma ID de aplicativo e senha para o bot e a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="04371-197">Remember that the sample expects to use the same App ID and password for both the bot and the messaging extension.</span></span>

<span data-ttu-id="04371-198">Clique no botão *testar e distribuir* item em *concluir* , na coluna esquerda do App Studio.</span><span class="sxs-lookup"><span data-stu-id="04371-198">Click on the *Test and distribute* item under *Finish* in the left hand column of App Studio.</span></span>

<img  width="450px" title="Testando seu aplicativo" src="~/assets/images/get-started/app-studio-manifest-editor-test.png"/>

<span data-ttu-id="04371-200">Para carregar o aplicativo no Microsoft Teams, clique no botão *instalar* em *testar e distribuir*.</span><span class="sxs-lookup"><span data-stu-id="04371-200">In order to upload your app to Teams, click the *Install* button under *Test and Distribute*.</span></span>

<img  width="450px" title="Adicionar uma caixa de diálogo de extensão de mensagens" src="~/assets/images/get-started/app-studio-manifest-editor-test-dialog.png"/>

<span data-ttu-id="04371-202">Clique na caixa de *pesquisa* na seção *Adicionar a uma equipe* e selecione uma equipe para adicionar o aplicativo de exemplo ao.</span><span class="sxs-lookup"><span data-stu-id="04371-202">Click on the *Search* box in the *Add to a team* section and select a team to add the sample app to.</span></span> <span data-ttu-id="04371-203">Normalmente, você deve configurar uma equipe especial para teste.</span><span class="sxs-lookup"><span data-stu-id="04371-203">Usually you will want to set up a special team for testing.</span></span>

<span data-ttu-id="04371-204">Clique no botão *instalar* na parte inferior da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="04371-204">Click the *Install* button at the bottom of the dialog.</span></span>

<span data-ttu-id="04371-205">Isso termina a parte do App Studio deste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="04371-205">This finishes the App Studio portion of this walkthrough.</span></span> <span data-ttu-id="04371-206">Agora você deve ver seu aplicativo em execução no Teams, mas o bot e a extensão de mensagens não funcionarão até que você atualize o ambiente de aplicativos hospedados para saber quais são as IDs de aplicativo e senhas.</span><span class="sxs-lookup"><span data-stu-id="04371-206">You should now see your app running in Teams, however the bot and the messaging extension will not work until you update the hosted applications environment to know what the App IDs and passwords are.</span></span>

<img  width="450px" title="O aplicativo concluído" src="~/assets/images/get-started/app-studio-finished-app.png"/>