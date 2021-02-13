### <a name="use-app-studio-to-update-the-app-package"></a><span data-ttu-id="c8d9e-101">Usar o App Studio para atualizar o pacote do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c8d9e-101">Use App Studio to update the app package</span></span>

<span data-ttu-id="c8d9e-102">O App Studio é um aplicativo do Teams que você pode instalar na loja do Teams.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-102">App Studio is a Teams app that you can install from the Teams store.</span></span> <span data-ttu-id="c8d9e-103">Isso simplifica a criação e o registro de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-103">It simplifies the creation and registration of an app.</span></span>

<span data-ttu-id="c8d9e-104">Para instalar o App Studio  no Teams, selecione o ícone Aplicativos na parte inferior da barra esquerda e procure o **App Studio.**</span><span class="sxs-lookup"><span data-stu-id="c8d9e-104">To install App Studio in Teams, select the **Apps** icon at the bottom of the left-hand bar, and search for **App Studio**.</span></span>

<img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

<span data-ttu-id="c8d9e-105">Selecione o **tile do App Studio** e escolha **Instalar.**</span><span class="sxs-lookup"><span data-stu-id="c8d9e-105">Select the **App Studio** tile and choose **Install**.</span></span> <span data-ttu-id="c8d9e-106">O App Studio está instalado.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-106">The App Studio is installed.</span></span>

<img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

<span data-ttu-id="c8d9e-107">Selecione a **guia Editor de** manifesto para criar o pacote do aplicativo para seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-107">Select the **Manifest editor** tab to create the app package for your Teams app.</span></span>

<img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

<span data-ttu-id="c8d9e-108">O exemplo vem com seu próprio manifesto pré-criado e foi projetado para criar um pacote do aplicativo quando o projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-108">The sample comes with its own pre-made manifest and is designed to build an app package when the project is built.</span></span> <span data-ttu-id="c8d9e-109">No .NET, isso é feito no Visual Studio e, no Nó JS, isso é feito digitando na linha de comando no diretório `gulp` raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-109">On .NET this is done in Visual Studio, and on Node JS this is done by typing `gulp` at the command line in the root directory of the project.</span></span>

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

<span data-ttu-id="c8d9e-110">O nome do pacote do aplicativo gerado é **helloworldapp.zip**.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-110">The name of the generated app package is **helloworldapp.zip**.</span></span> <span data-ttu-id="c8d9e-111">Você pode procurar esse arquivo se o local não estiver claro na ferramenta que está usando.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-111">You can search for this file if the location is not clear in the tool you are using.</span></span>

<span data-ttu-id="c8d9e-112">Agora, para modificar esse pacote do aplicativo, selecione o pacote Importar um **aplicativo** existente no **editor de manifesto.**</span><span class="sxs-lookup"><span data-stu-id="c8d9e-112">Now to modify this app package, select the **Import an existing app** tile in the **Manifest editor**.</span></span>

<img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

<span data-ttu-id="c8d9e-113">Clique no **lado do lado** hello world do aplicativo recém-importado.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-113">Click the **Hello World** tile for your newly imported app.</span></span>

<img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

<span data-ttu-id="c8d9e-114">A imagem a seguir mostra o pacote do aplicativo importado no App Studio:</span><span class="sxs-lookup"><span data-stu-id="c8d9e-114">The following image shows the imported app package in App Studio:</span></span>

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

<span data-ttu-id="c8d9e-115">Há uma lista de etapas no lado esquerdo do editor de Manifesto e no lado direito, uma lista de propriedades que precisam ser preenchidas para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-115">There is a list of steps on the left-hand side of the Manifest editor and on the right-hand side, a list of properties that need to be filled in for each of those steps.</span></span> <span data-ttu-id="c8d9e-116">Desde que você começou com um aplicativo de exemplo, grande parte das informações já está preenchida. As próximas etapas o ajudarão a alterar as partes que ainda precisam ser atualizadas.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-116">Since you started with a sample app, much of the information is already filled out. The next steps will walk you through changing the parts that still need to be updated.</span></span>

#### <a name="app-details"></a><span data-ttu-id="c8d9e-117">Detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c8d9e-117">App details</span></span>

<span data-ttu-id="c8d9e-118">Clique na entrada *de detalhes do* aplicativo em *Detalhes.*</span><span class="sxs-lookup"><span data-stu-id="c8d9e-118">Click on the *App details* entry under *Details*.</span></span> <span data-ttu-id="c8d9e-119">Clique no *botão Gerar* para criar uma nova ID de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-119">Click the *Generate* button to create a new app id.</span></span>

<span data-ttu-id="c8d9e-120">Sua nova ID de aplicativo deve se parecer com: `2322041b-72bf-459d-b107-f4f335bc35bd` .</span><span class="sxs-lookup"><span data-stu-id="c8d9e-120">Your new app id should look something like: `2322041b-72bf-459d-b107-f4f335bc35bd`.</span></span>

<span data-ttu-id="c8d9e-121">Procure o restante dos detalhes do aplicativo no painel à direita e familiarize-se  com algumas das entradas, como informações do desenvolvedor e *identidade visual.*</span><span class="sxs-lookup"><span data-stu-id="c8d9e-121">Look through the rest of the App details in the right-hand pane, and familiarize yourself with some of the entries such as *Developer information* and *Branding*.</span></span> <span data-ttu-id="c8d9e-122">Essas seções são importantes se você estiver escrevendo um novo aplicativo para distribuição.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-122">These sections are important if you are writing a new app for distribution.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="c8d9e-123">Recursos: guias</span><span class="sxs-lookup"><span data-stu-id="c8d9e-123">Capabilities: Tabs</span></span>

<span data-ttu-id="c8d9e-124">As guias estão entre os elementos mais simples a adicionar a um aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-124">Tabs are among the simplest elements to add to a Teams app.</span></span> <span data-ttu-id="c8d9e-125">O aplicativo de exemplo já dá suporte a várias guias, e você pode habilita-las da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-125">The sample app already supports several tabs, and you can enable them as follows.</span></span>

##### <a name="team-tab"></a><span data-ttu-id="c8d9e-126">Guia Equipe</span><span class="sxs-lookup"><span data-stu-id="c8d9e-126">Team tab</span></span>

<span data-ttu-id="c8d9e-127">Seu aplicativo só pode ter uma guia Equipe.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-127">Your app can only have one Team tab.</span></span>

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

<span data-ttu-id="c8d9e-128">Neste exemplo, a guia Equipe é onde sua página de configuração vai.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-128">In this sample, the Team tab is where your configuration page goes.</span></span> <span data-ttu-id="c8d9e-129">Clique no *símbolo ...* no final da entrada e escolha *Editar* no drop-down.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-129">Click on the *...* symbol at the end of the entry and choose *Edit* from the drop-down.</span></span> <span data-ttu-id="c8d9e-130">Altere a URL `https://yourteamsapp.ngrok.io/configure` para onde deve ser substituída pela URL que você usou acima ao hospedar seu `yourteamsapp.ngrok.io` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-130">Change the URL to `https://yourteamsapp.ngrok.io/configure` where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

##### <a name="personal-tabs"></a><span data-ttu-id="c8d9e-131">Guias pessoais</span><span class="sxs-lookup"><span data-stu-id="c8d9e-131">Personal tabs</span></span>

<span data-ttu-id="c8d9e-132">Seu aplicativo pode ter até 16 guias, incluindo a guia da equipe.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-132">Your app can have up to 16 tabs, including the team tab.</span></span>

<span data-ttu-id="c8d9e-133">As guias pessoais são representadas de forma diferente da guia da equipe. Você deverá ver *a guia Hello* já listada na lista de guias pessoais.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-133">Personal tabs are represented differently from the team tab. You should see *Hello Tab* already listed in the personal tabs list.</span></span> <span data-ttu-id="c8d9e-134">No momento, ele tem um valor de espaço `com.contoso.helloworld.hellotab` reservado.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-134">At the moment it has a placeholder value `com.contoso.helloworld.hellotab`.</span></span> <span data-ttu-id="c8d9e-135">Clique no *símbolo ...* no final da entrada e escolha *Editar* no drop-down.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-135">Click on the *...* symbol at the end of the entry and choose *Edit* from the drop-down.</span></span> <span data-ttu-id="c8d9e-136">A caixa de diálogo a seguir será exibida.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-136">The following dialog will appear.</span></span>

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

<span data-ttu-id="c8d9e-137">Há dois campos que você precisa atualizar com a URL do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-137">There are two fields that you need to update with your app URL.</span></span>

- <span data-ttu-id="c8d9e-138">Alterar a URL de Conteúdo para `https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="c8d9e-138">Change Content URL to `https://yourteamsapp.ngrok.io/hello`</span></span>
- <span data-ttu-id="c8d9e-139">Alterar a URL do site para `https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="c8d9e-139">Change Website URL to `https://yourteamsapp.ngrok.io/hello`</span></span>

<span data-ttu-id="c8d9e-140">Onde deve ser substituído pela URL que você `yourteamsapp.ngrok.io` usou acima ao hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-140">Where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

#### <a name="bots"></a><span data-ttu-id="c8d9e-141">Bots</span><span class="sxs-lookup"><span data-stu-id="c8d9e-141">Bots</span></span>

<span data-ttu-id="c8d9e-142">Os bots são a maneira mais comum de adicionar funcionalidade ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-142">Bots are the most common way to add functionality to your app.</span></span> <span data-ttu-id="c8d9e-143">O exemplo hello world já tem um bot como parte do exemplo, mas ele ainda não foi registrado com a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-143">The hello world sample already has a bot as part of the sample, but it has not been registered with Microsoft yet.</span></span>

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

<span data-ttu-id="c8d9e-144">O bot que foi importado da amostra ainda não tem uma ID de aplicativo associada a ele.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-144">The bot that was imported from the sample does not have an App ID associated with it yet.</span></span> <span data-ttu-id="c8d9e-145">Você terá que criar um novo bot para que o App Studio possa criar uma nova ID de aplicativo e registrá-la na Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-145">You will have to create a new bot so that App Studio can create a new App ID and register it with Microsoft.</span></span> <span data-ttu-id="c8d9e-146">Observe que essa é a ID do aplicativo para o bot, que é diferente da ID do aplicativo criada para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-146">Note that this is the App ID for the bot, which is different from the App ID created for the app.</span></span> <span data-ttu-id="c8d9e-147">Cada bot em um aplicativo requer sua própria ID de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-147">Each bot in an app requires its own App ID.</span></span>

<span data-ttu-id="c8d9e-148">Clique no *botão excluir* ao lado do *bot importado* na lista de bots.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-148">Click the *delete* button next to the *Imported bot* in the bot list.</span></span>

<span data-ttu-id="c8d9e-149">Agora não há bots a mostrar.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-149">Now there are no bots left to show.</span></span> <span data-ttu-id="c8d9e-150">Clique *em Instalação.*</span><span class="sxs-lookup"><span data-stu-id="c8d9e-150">Click *Setup*.</span></span> <span data-ttu-id="c8d9e-151">Isso exibirá a caixa de diálogo Configurar *um bot.*</span><span class="sxs-lookup"><span data-stu-id="c8d9e-151">This will display the *Set up a bot* dialog.</span></span>

<img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

<span data-ttu-id="c8d9e-152">Adicione um nome de bot, como `Contoso bot` , e selecione todos os três botões em **Escopo**.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-152">Add a bot name such as `Contoso bot`, and select all three buttons under **Scope**.</span></span>

<span data-ttu-id="c8d9e-153">Escolha *Criar bot* para sair da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-153">Choose *Create bot* to exit the dialog.</span></span> <span data-ttu-id="c8d9e-154">O App Studio registra seu bot na Microsoft e exibe seu novo bot na lista de bots.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-154">App Studio registers your bot with Microsoft and displays your new bot in the bot list.</span></span> <span data-ttu-id="c8d9e-155">Agora seria um bom momento para abrir um arquivo de texto no bloco de notas e copiar e colar sua nova ID de bot nele.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-155">Now would be a good time to open a text file in notepad and copy and paste your new bot id into it.</span></span> <span data-ttu-id="c8d9e-156">Você precisará dessa ID mais tarde.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-156">You will need this id later.</span></span>

<span data-ttu-id="c8d9e-157">Clique *em Gerar* Nova Senha e anote a senha no mesmo arquivo de texto em que você anotou sua ID de aplicativo bot.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-157">Click *Generate New Password*, and make a note of the password in the same text file you noted your Bot app ID in.</span></span> <span data-ttu-id="c8d9e-158">Esta é a única vez que sua senha será mostrada, portanto, certifique-se de fazer isso agora.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-158">This is the only time your password will be shown, so be sure to do this now.</span></span>

<span data-ttu-id="c8d9e-159">Atualize *o endereço do ponto* de extremidade bot para , onde deve ser substituído pela URL que você usou acima ao hospedar seu `https://yourteamsapp.ngrok.io/api/messages` `yourteamsapp.ngrok.io` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-159">Update the *Bot endpoint address* to `https://yourteamsapp.ngrok.io/api/messages`, where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

<span data-ttu-id="c8d9e-160">Agora seria um bom momento para salvar seu arquivo de texto se você ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-160">Now would be a good time to save your text file if you have not done so already.</span></span> <span data-ttu-id="c8d9e-161">Você adicionará essas informações ao seu aplicativo hospedado posteriormente neste passo a passo, o que permitirá uma comunicação segura com seu bot.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-161">You will add this information to your hosted app later in this walkthrough, which will allow secure communication with your bot.</span></span>

#### <a name="messaging-extensions"></a><span data-ttu-id="c8d9e-162">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="c8d9e-162">Messaging extensions</span></span>

<span data-ttu-id="c8d9e-163">As extensões de mensagens permitem que os usuários peçam informações do seu serviço e postem essas informações, na forma de cartões, direto para a conversa do canal.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-163">Messaging extensions let users ask for information from your service and post that information, in the form of cards, right into the channel conversation.</span></span> <span data-ttu-id="c8d9e-164">As extensões de mensagens aparecem na parte inferior da caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-164">Messaging extensions appear along the bottom of the compose box.</span></span>

<span data-ttu-id="c8d9e-165">Selecione **extensões de Mensagens** em **Funcionalidades** na coluna à esquerda do App Studio para configurar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-165">Select **Messaging extensions** under **Capabilities** in the left-hand column of App Studio to configure the messaging extension.</span></span>

<img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

<span data-ttu-id="c8d9e-166">A extensão de mensagens de exemplo está listada no painel à direita em **Extensões de Mensagens.**</span><span class="sxs-lookup"><span data-stu-id="c8d9e-166">The sample messaging extension is listed in the right-hand pane under **Messaging Extensions**.</span></span> <span data-ttu-id="c8d9e-167">Selecione **Excluir** novamente para remover essa  entrada e clique no botão Configurar seguindo as mesmas etapas que você seguiu para bots.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-167">Select **Delete** again to remove this entry, and then click the *Set up* button following the same steps as you followed for bots.</span></span> <span data-ttu-id="c8d9e-168">Isso exibirá a caixa *de diálogo Extensão de* Mensagens.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-168">This will display the *Messaging Extension* dialog.</span></span>

<span data-ttu-id="c8d9e-169">Selecione a *guia Usar bot* existente e selecione de um dos meus *bots existentes.*</span><span class="sxs-lookup"><span data-stu-id="c8d9e-169">Select the *Use existing bot* tab, then *Select from one of my existing bots*.</span></span> <span data-ttu-id="c8d9e-170">No menu suspenso, selecione o bot que você criou na seção acima.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-170">In the drop-down menu, select the bot you created in the section above.</span></span> <span data-ttu-id="c8d9e-171">Adicione um *nome de bot e* clique em *Salvar* para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-171">Add a *Bot name* and click *Save* to close the dialog.</span></span>

<span data-ttu-id="c8d9e-172">Na seção *Comando,* clique em *Adicionar*.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-172">Under the *Command* section, click *Add*.</span></span> <span data-ttu-id="c8d9e-173">Estamos adicionando um comando baseado em pesquisa, portanto, escolha a opção Permitir que os usuários *consultem seu serviço...*</span><span class="sxs-lookup"><span data-stu-id="c8d9e-173">We're adding a search-based command, so choose the *Allow users to query your service...* option.</span></span>

<span data-ttu-id="c8d9e-174">Na caixa **de diálogo Novo** comando, insira os seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-174">In the **New command** dialog, enter the following values.</span></span>

<span data-ttu-id="c8d9e-175">Em *Novo comando:*</span><span class="sxs-lookup"><span data-stu-id="c8d9e-175">Under *New command*:</span></span>

- <span data-ttu-id="c8d9e-176">*ID do comando*  = getRandomText</span><span class="sxs-lookup"><span data-stu-id="c8d9e-176">*Command ID*  = getRandomText</span></span>
- <span data-ttu-id="c8d9e-177">*Title*       = Obter algum texto aleatório por diversão</span><span class="sxs-lookup"><span data-stu-id="c8d9e-177">*Title*       = Get some random text for fun</span></span>
- <span data-ttu-id="c8d9e-178">*Descrição* = obtém texto aleatório e imagens</span><span class="sxs-lookup"><span data-stu-id="c8d9e-178">*Description* = Gets some random text and images</span></span>

<span data-ttu-id="c8d9e-179">Sob *Parâmetro:*</span><span class="sxs-lookup"><span data-stu-id="c8d9e-179">Under *Parameter*:</span></span>

- <span data-ttu-id="c8d9e-180">*Name*        = cardTitle</span><span class="sxs-lookup"><span data-stu-id="c8d9e-180">*Name*        = cardTitle</span></span>
- <span data-ttu-id="c8d9e-181">*Título*       = Título do cartão</span><span class="sxs-lookup"><span data-stu-id="c8d9e-181">*Title*       = Card title</span></span>
- <span data-ttu-id="c8d9e-182">*Descrição* = Título do cartão a ser usado</span><span class="sxs-lookup"><span data-stu-id="c8d9e-182">*Description* = Card title to use</span></span>

<span data-ttu-id="c8d9e-183">Quando você for inserido nas informações, clique em *Salvar* para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-183">Once you're entered the information, click *Save* to close the dialog.</span></span>

#### <a name="register-your-app-in-teams"></a><span data-ttu-id="c8d9e-184">Registrar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="c8d9e-184">Register your app in Teams</span></span>

<span data-ttu-id="c8d9e-185">Agora você concluiu a inserção dos detalhes do seu aplicativo, mas as duas etapas a seguir permanecem:</span><span class="sxs-lookup"><span data-stu-id="c8d9e-185">You have now completed entering the details of your app, but the following two steps remain:</span></span>
1. <span data-ttu-id="c8d9e-186">Use a seção Testar e Distribuir do App Studio para instalar seu aplicativo no Teams.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-186">Use the Test and Distribute section of App Studio to install your app in Teams.</span></span>
1. <span data-ttu-id="c8d9e-187">Atualize seu aplicativo hospedado com a ID do aplicativo e a senha do seu bot.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-187">Update your hosted application with the App ID and password for your bot.</span></span> <span data-ttu-id="c8d9e-188">Lembre-se de que o exemplo espera usar a mesma ID de aplicativo e senha para o bot e a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-188">Remember that the sample expects to use the same App ID and password for both the bot and the messaging extension.</span></span>

<span data-ttu-id="c8d9e-189">Selecione o **teste e distribua** o item **em Concluir** na coluna à esquerda do App Studio.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-189">Select the **Test and distribute** item under **Finish** in the left-hand column of App Studio.</span></span>

<img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

<span data-ttu-id="c8d9e-190">Para carregar seu aplicativo no Teams, clique no botão *Instalar* em *Testar e Distribuir.*</span><span class="sxs-lookup"><span data-stu-id="c8d9e-190">In order to upload your app to Teams, click the *Install* button under *Test and Distribute*.</span></span>

<img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

<span data-ttu-id="c8d9e-191">Selecione a **caixa Pesquisar** na seção Adicionar a **uma equipe** e selecione uma equipe para adicionar o aplicativo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-191">Select the **Search** box in the **Add to a team** section and select a team to add the sample app to.</span></span> <span data-ttu-id="c8d9e-192">Normalmente, você pode configurar uma equipe especial para teste.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-192">Usually, you can set up a special team for testing.</span></span>

<span data-ttu-id="c8d9e-193">Selecione o **botão** Instalar na parte inferior da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-193">Select the **Install** button at the bottom of the dialog.</span></span>

<span data-ttu-id="c8d9e-194">Isso finaliza a parte do App Studio deste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-194">This finishes the App Studio portion of this walkthrough.</span></span> <span data-ttu-id="c8d9e-195">Agora você deve ver seu aplicativo em execução no Teams, no entanto, o bot e a extensão de mensagens não funcionarão até que você atualize o ambiente de aplicativos hospedados para saber quais são as IDs de aplicativo e senhas.</span><span class="sxs-lookup"><span data-stu-id="c8d9e-195">You should now see your app running in Teams, however, the bot and the messaging extension will not work until you update the hosted applications environment to know what the App IDs and passwords are.</span></span>

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
