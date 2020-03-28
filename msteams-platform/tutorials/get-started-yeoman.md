---
title: Introdução ao gerador Yeoman para o Microsoft Teams
description: Introdução à criação de aplicativos ótimos com o gerador Yeoman para o Microsoft Teams
keywords: Getting Started node. js NodeJS Yeoman
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: 217c0900e067a61e083e7ffb0b121afdaa51c49f
ms.sourcegitcommit: b13b38a104946c32cd5245a7af706070e534927d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2020
ms.locfileid: "43034040"
---
# <a name="build-your-first-microsoft-teams-app"></a><span data-ttu-id="4360e-104">Criar seu primeiro aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4360e-104">Build your First Microsoft Teams App</span></span>

>[!Note]
><span data-ttu-id="4360e-105">Este tutorial é proveniente do [gerador Yeoman para o Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)</span><span class="sxs-lookup"><span data-stu-id="4360e-105">This tutorial comes from the [yeoman generator for Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)</span></span>

<span data-ttu-id="4360e-106">Neste tutorial, vamos examinar a criação de seu primeiro aplicativo do Microsoft Teams usando o gerador Yeoman do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4360e-106">In this tutorial we will walk through creating your very first Microsoft Teams app using the Microsoft Teams Yeoman generator.</span></span> <span data-ttu-id="4360e-107">Ele pressupõe que você [habilitou o carregamento lateral de aplicativos do Microsoft Teams](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="4360e-107">It assumes that you have [enabled side-loading of Microsoft Teams apps](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

![gerador Yeoman git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a><span data-ttu-id="4360e-109">Configurar e preparar sua máquina</span><span class="sxs-lookup"><span data-stu-id="4360e-109">Setup and prepare your machine</span></span>

<span data-ttu-id="4360e-110">Você precisa instalar o seguinte em sua máquina antes de começar a usar o gerador de Teams.</span><span class="sxs-lookup"><span data-stu-id="4360e-110">You need to install the following on your machine before starting to use the Teams Generator.</span></span>

### <a name="install-node"></a><span data-ttu-id="4360e-111">Nó de instalação</span><span class="sxs-lookup"><span data-stu-id="4360e-111">Install Node</span></span>

<span data-ttu-id="4360e-112">Você precisa ter o NodeJS instalado em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="4360e-112">You need to have NodeJS installed on your machine.</span></span> <span data-ttu-id="4360e-113">Você deve usar a versão mais recente do [LTS](https://nodejs.org/dist/latest-v8.x/).</span><span class="sxs-lookup"><span data-stu-id="4360e-113">You should use the latest [LTS version](https://nodejs.org/dist/latest-v8.x/).</span></span>

### <a name="install-a-code-editor"></a><span data-ttu-id="4360e-114">Instalar um editor de códigos</span><span class="sxs-lookup"><span data-stu-id="4360e-114">Install a code editor</span></span>

<span data-ttu-id="4360e-115">Você também precisa de um editor de códigos, fique à vontade para usar qualquer editor de texto que preferir.</span><span class="sxs-lookup"><span data-stu-id="4360e-115">You also need a code editor, feel free to use whatever text editor you prefer.</span></span> <span data-ttu-id="4360e-116">No entanto, a maioria desta documentação e capturas de tela se referem ao uso do [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="4360e-116">However most of this documentation and screenshots refer to using [Visual Studio Code](https://code.visualstudio.com).</span></span>

### <a name="install-yeoman-and-gulp-cli"></a><span data-ttu-id="4360e-117">Instalar a CLI do Yeoman e do Gulp</span><span class="sxs-lookup"><span data-stu-id="4360e-117">Install Yeoman and Gulp CLI</span></span>

<span data-ttu-id="4360e-118">Para poder estruturarr projetos usando o gerador de equipes, você precisa instalar a ferramenta Yeoman, bem como o Gerenciador de tarefas CLI do Gulp.</span><span class="sxs-lookup"><span data-stu-id="4360e-118">To be able to scaffold projects using the Teams generator you need to install the Yeoman tool as well as the Gulp CLI task manager.</span></span>

<span data-ttu-id="4360e-119">Abra um prompt de comando e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4360e-119">Open up a command prompt and type the following:</span></span>

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-microsoft-teams-apps-generator---yo-teams"></a><span data-ttu-id="4360e-120">Instalar o gerador de aplicativos do Microsoft Teams-Yo</span><span class="sxs-lookup"><span data-stu-id="4360e-120">Install the Microsoft Teams Apps generator - Yo Teams</span></span>

<span data-ttu-id="4360e-121">O gerador Yeoman para os aplicativos do Microsoft Teams é instalado com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4360e-121">The Yeoman generator for Microsoft Teams apps are installed with the following command:</span></span>

```bash
npm install generator-teams --global
```

#### <a name="install-preview-versions"></a><span data-ttu-id="4360e-122">Instalar versões prévias</span><span class="sxs-lookup"><span data-stu-id="4360e-122">Install preview versions</span></span>

<span data-ttu-id="4360e-123">Se você deseja instalar versões prévias do gerador de Teams com este comando:</span><span class="sxs-lookup"><span data-stu-id="4360e-123">If you want to install preview versions of the Teams generator with this command:</span></span>

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a><span data-ttu-id="4360e-124">Gerar seu projeto</span><span class="sxs-lookup"><span data-stu-id="4360e-124">Generate your project</span></span>

<span data-ttu-id="4360e-125">Abra um prompt de comando e crie um novo diretório no qual você deseja criar seu projeto e, nesse diretório, digite o `yo teams`comando.</span><span class="sxs-lookup"><span data-stu-id="4360e-125">Open up a command prompt and create a new directory where you want to create your project and in that directory type the command `yo teams`.</span></span> <span data-ttu-id="4360e-126">Isso iniciará o gerador de aplicativos do Teams e você será solicitado a fornecer um conjunto de perguntas.</span><span class="sxs-lookup"><span data-stu-id="4360e-126">This will start the Teams Apps generator and you will be asked a set of questions.</span></span>

![Times Yo](~/assets/yeoman-images/teams-first-app-1.png)

<span data-ttu-id="4360e-128">A primeira pergunta é sobre o nome do projeto, você pode deixá-lo como está pressionando ENTER.</span><span class="sxs-lookup"><span data-stu-id="4360e-128">The first question is about your project name, you can leave it as is by pressing enter.</span></span> <span data-ttu-id="4360e-129">A pergunta seguinte pergunta se você deseja criar um novo diretório ou usar o atual.</span><span class="sxs-lookup"><span data-stu-id="4360e-129">Next question asks you if you want to create a new directory or use the current one.</span></span> <span data-ttu-id="4360e-130">Como já estamos no diretório desejado, basta pressionar Enter.</span><span class="sxs-lookup"><span data-stu-id="4360e-130">As we already are in the directory we want, we just press enter.</span></span>

<span data-ttu-id="4360e-131">A etapa a seguir solicita um título do seu projeto, este título será usado no manifesto e na descrição do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4360e-131">The following step asks for a title of your project, this title will be used in the manifest and description of your app.</span></span> <span data-ttu-id="4360e-132">E, em seguida, você será solicitado a fornecer um nome de empresa, que também será usado no manifesto.</span><span class="sxs-lookup"><span data-stu-id="4360e-132">And then you will be asked for a company name, which also will be used in the manifest.</span></span>

<span data-ttu-id="4360e-133">A quinta pergunta pergunta sobre qual versão do manifesto você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="4360e-133">The fifth question asks you about what version of the manifest you want to use.</span></span> <span data-ttu-id="4360e-134">Para este tutorial, `v1.5`selecione, que é o esquema geral disponível atual.</span><span class="sxs-lookup"><span data-stu-id="4360e-134">For this tutorial select `v1.5`, which is the current general available schema.</span></span>

<span data-ttu-id="4360e-135">Depois disso, o gerador solicitará quais itens você deseja adicionar ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="4360e-135">After this the generator will ask you for what items you want to add to your project.</span></span> <span data-ttu-id="4360e-136">Você pode selecionar um único ou qualquer combinação de itens.</span><span class="sxs-lookup"><span data-stu-id="4360e-136">You can select a single one or any combination of items.</span></span> <span data-ttu-id="4360e-137">Por enquanto, basta selecionar *uma guia*.</span><span class="sxs-lookup"><span data-stu-id="4360e-137">For now, just select *a Tab*.</span></span>

![seleção de item](~/assets/yeoman-images/teams-first-app-2.png)

<span data-ttu-id="4360e-139">Com base nos itens selecionados, você será solicitado a fornecer um conjunto de perguntas de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="4360e-139">Based on what items you select, you will be asked a set of follow-up questions.</span></span>

<span data-ttu-id="4360e-140">Agora você precisa inserir uma URL de onde você hospedará sua solução.</span><span class="sxs-lookup"><span data-stu-id="4360e-140">Now you need to enter a URL of where you will host your solution.</span></span> <span data-ttu-id="4360e-141">Pode ser qualquer URL, mas, por padrão, o gerador sugere uma URL de sites do Azure.</span><span class="sxs-lookup"><span data-stu-id="4360e-141">This can be any URL, but by default the generator suggests an Azure Web Sites URL.</span></span>

<span data-ttu-id="4360e-142">O gerador tem vários recursos avançados internos que você pode optar por aceitar ou recusar o.</span><span class="sxs-lookup"><span data-stu-id="4360e-142">The generator has a lot of built-in advanced features that you can opt-in or opt-out of.</span></span> <span data-ttu-id="4360e-143">Após a pergunta de URL, você será perguntado se deseja incluir testes de unidade para sua solução, o padrão é sim.</span><span class="sxs-lookup"><span data-stu-id="4360e-143">Following the URL question you will be asked if you want to include unit-testing for your solution, default is yes.</span></span> <span data-ttu-id="4360e-144">Se você escolher este projeto gerado terá uma estrutura de teste de unidade e alguns testes de unidade padrão para os diferentes itens sendo estruturado.</span><span class="sxs-lookup"><span data-stu-id="4360e-144">If you choose this the generated project will have a unit testing framework and some default unit tests for the different items being scaffolded.</span></span> <span data-ttu-id="4360e-145">Para este tutorial, opte por não incluir uma estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="4360e-145">For this tutorial choose not to include a test framework.</span></span>

<span data-ttu-id="4360e-146">Para facilitar o registro em log, você também será perguntado se deseja usar o Azure Application insights para registro em log.</span><span class="sxs-lookup"><span data-stu-id="4360e-146">In order to make logging easy for you, you will also be asked if you want to use Azure Application Insights for logging.</span></span> <span data-ttu-id="4360e-147">Se você escolher Sim, será necessário fornecer uma chave do Azure Application insights.</span><span class="sxs-lookup"><span data-stu-id="4360e-147">If you choose Yes, you will need to provide a Azure Application Insights key.</span></span> <span data-ttu-id="4360e-148">Para este tutorial, opte por usar o Application insights.</span><span class="sxs-lookup"><span data-stu-id="4360e-148">For this tutorial opt-out of using Application Insights.</span></span>

<span data-ttu-id="4360e-149">O próximo conjunto de perguntas será baseado na seleção de itens anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4360e-149">The next set of questions will be based on your selection of items previously.</span></span> <span data-ttu-id="4360e-150">Para uma guia, você só precisa fornecer um nome e, opcionalmente, escolher se deseja poder usar este aplicativo como uma Web Part do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4360e-150">For a tab you only need to provide a name and optionally choose if you want to be able to use this app as a SharePoint Online web part.</span></span> <span data-ttu-id="4360e-151">Depois de fornecer esse nome, o gerador gerará o projeto e instalará todas as dependências.</span><span class="sxs-lookup"><span data-stu-id="4360e-151">Once you have provided this name the generator will generate the project and install all dependencies.</span></span> <span data-ttu-id="4360e-152">Isso levará um minuto ou dois.</span><span class="sxs-lookup"><span data-stu-id="4360e-152">This will take a minute or two.</span></span>

## <a name="add-some-code-to-your-tab"></a><span data-ttu-id="4360e-153">Adicionar um código à sua guia</span><span class="sxs-lookup"><span data-stu-id="4360e-153">Add some code to your tab</span></span>

<span data-ttu-id="4360e-154">Depois que o gerador for concluído, você poderá abrir a solução em seu editor de código favorito.</span><span class="sxs-lookup"><span data-stu-id="4360e-154">Once the generator is done you can open up the solution in your favorite code editor.</span></span> <span data-ttu-id="4360e-155">Reserve um minuto ou dois e familiarize-se com o modo como o código está organizado-você pode ler mais sobre isso na documentação da [estrutura do projeto](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) .</span><span class="sxs-lookup"><span data-stu-id="4360e-155">Take a minute or two and familiarize yourself with how the code is organized - you can read more about that in the [Project Structure](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) documentation.</span></span>

<span data-ttu-id="4360e-156">Sua guia estará localizada no `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` arquivo.</span><span class="sxs-lookup"><span data-stu-id="4360e-156">Your Tab will be located in the `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` file.</span></span> <span data-ttu-id="4360e-157">Esta é a classe baseada em reagir do TypeScript para sua guia. `render()` localize o método e adicione uma linha de código `<PanelBody>` dentro do controle para que ele tenha a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="4360e-157">This is the TypeScript React based class for your Tab. Locate the `render()` method and add a line of code inside the `<PanelBody>` control so it looks like this:</span></span>

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

<span data-ttu-id="4360e-158">Salve o arquivo e retorne ao prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="4360e-158">Save the file and return to the command prompt.</span></span>

## <a name="build-your-app"></a><span data-ttu-id="4360e-159">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4360e-159">Build your app</span></span>

<span data-ttu-id="4360e-160">Agora você pode criar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="4360e-160">You can now build your project.</span></span> <span data-ttu-id="4360e-161">Isso é feito em duas etapas (ou uma etapa, veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="4360e-161">This is done in two steps (or one step, see below).</span></span>

<span data-ttu-id="4360e-162">Primeiro, você precisa criar o arquivo de manifesto do aplicativo Teams, que você carrega/Sideload no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4360e-162">First you need to create the Teams App manifest file, that you upload/sideload into Microsoft Teams.</span></span> <span data-ttu-id="4360e-163">Isso é feito pela tarefa `gulp manifest`Gulp.</span><span class="sxs-lookup"><span data-stu-id="4360e-163">This is done by the Gulp task `gulp manifest`.</span></span> <span data-ttu-id="4360e-164">Isso validará o manifesto e criará um arquivo zip no `./package` diretório.</span><span class="sxs-lookup"><span data-stu-id="4360e-164">This will validate the manifest and create a zip file in the `./package` directory.</span></span>

<span data-ttu-id="4360e-165">Para compilar a solução, use o `gulp build` comando.</span><span class="sxs-lookup"><span data-stu-id="4360e-165">To build your solution you use the `gulp build` command.</span></span> <span data-ttu-id="4360e-166">Isso irá transcompilar sua solução na `./dist` pasta.</span><span class="sxs-lookup"><span data-stu-id="4360e-166">This will transpile your solution into the `./dist` folder.</span></span> 

## <a name="run-your-app"></a><span data-ttu-id="4360e-167">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="4360e-167">Run your app</span></span>

<span data-ttu-id="4360e-168">Para executar o aplicativo, use o `gulp serve` comando.</span><span class="sxs-lookup"><span data-stu-id="4360e-168">To run your app you use the `gulp serve` command.</span></span> <span data-ttu-id="4360e-169">Isso criará e iniciará um servidor Web local para testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4360e-169">This will build and start a local web server for you to test your app.</span></span> <span data-ttu-id="4360e-170">O comando também recriará o aplicativo sempre que você salvar um arquivo em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="4360e-170">The command will also rebuild the application whenever you save a file in your project.</span></span> 

<span data-ttu-id="4360e-171">Agora você poderá navegar até `http://localhost:3007/myFirstAppTab/` para garantir que sua guia está sendo renderizada.</span><span class="sxs-lookup"><span data-stu-id="4360e-171">You should now be able to browse to `http://localhost:3007/myFirstAppTab/` to ensure that your tab is rendering.</span></span> <span data-ttu-id="4360e-172">No entanto, ainda não no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4360e-172">However, not in Microsoft Teams yet.</span></span>

![exibir seu site em um navegador](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a><span data-ttu-id="4360e-174">Executar o aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4360e-174">Run your app in Microsoft Teams</span></span>

<span data-ttu-id="4360e-175">O Microsoft Teams não permite que seu aplicativo hospedado no localhost, portanto, você precisa publicá-lo em uma URL pública ou usar um proxy, como ngrok.</span><span class="sxs-lookup"><span data-stu-id="4360e-175">Microsoft Teams does not allow you to have your app hosted on localhost, so you need to either publish it to a public URL or use a proxy such as ngrok.</span></span>

<span data-ttu-id="4360e-176">Boa notícia é que o projeto estruturado tem esse interno.</span><span class="sxs-lookup"><span data-stu-id="4360e-176">Good news is that the scaffolded project has this built-in.</span></span> <span data-ttu-id="4360e-177">Quando você executar `gulp ngrok-serve` o serviço ngrok será iniciado em segundo plano, com uma entrada DNS exclusiva e pública e também empacotará o manifesto com essa URL exclusiva e, em seguida, fará exatamente a mesma coisa `gulp serve`que.</span><span class="sxs-lookup"><span data-stu-id="4360e-177">When you run `gulp ngrok-serve` the ngrok service will be started in the background, with a unique and public DNS entry and it will also package the manifest with that unique URL and then do the exact same thing as `gulp serve`.</span></span>

<span data-ttu-id="4360e-178">Depois de `gulp ngrok-serve`executar o, criar uma nova equipe do Microsoft Teams e quando ela for criada clique no nome da equipe, vá para as configurações do Teams e selecione *aplicativos*.</span><span class="sxs-lookup"><span data-stu-id="4360e-178">After running `gulp ngrok-serve`, create a new Microsoft Teams team and when it is created click on the Team name, to go to the teams settings and then select *Apps*.</span></span> <span data-ttu-id="4360e-179">No canto inferior direito, você verá um link *carregar um aplicativo personalizado*, selecione-o e navegue até a pasta do projeto e a subpasta `package`chamada.</span><span class="sxs-lookup"><span data-stu-id="4360e-179">In the lower right corner you should see a link *Upload a custom app*, select it and then browse to your project folder and the subfolder called `package`.</span></span> <span data-ttu-id="4360e-180">Selecione o arquivo zip nessa pasta e escolha abrir.</span><span class="sxs-lookup"><span data-stu-id="4360e-180">Select the zip file in that folder and choose open.</span></span> <span data-ttu-id="4360e-181">Seu aplicativo agora está suplementos foi feito no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4360e-181">Your App is now sideloaded into Microsoft Teams.</span></span>

![aplicativo Suplementos foi feito](~/assets/yeoman-images/teams-first-app-4.png)

<span data-ttu-id="4360e-183">Volte para o canal *geral* e selecione *+* para adicionar uma nova guia. Você deve ver sua guia na lista de guias.</span><span class="sxs-lookup"><span data-stu-id="4360e-183">Go back to the *General* channel and select *+* to add a new Tab. You should see your tab in the list of tabs.</span></span>

![guia Configurar](~/assets/yeoman-images/teams-first-app-5.png)

<span data-ttu-id="4360e-185">Escolha sua guia e siga as instruções para adicioná-la.</span><span class="sxs-lookup"><span data-stu-id="4360e-185">Choose your tab and follow the instructions to add it.</span></span> <span data-ttu-id="4360e-186">Observe que você tem uma caixa de diálogo de configuração personalizada, para a qual é possível editar a fonte.</span><span class="sxs-lookup"><span data-stu-id="4360e-186">Notice that you have a custom configuration dialog, for which you can edit the source.</span></span> <span data-ttu-id="4360e-187">Selecione *salvar* para adicionar sua guia ao canal.</span><span class="sxs-lookup"><span data-stu-id="4360e-187">Select *Save* to add your tab to the channel.</span></span> <span data-ttu-id="4360e-188">Após a conclusão, a guia deve ser carregada no Microsoft Teams!</span><span class="sxs-lookup"><span data-stu-id="4360e-188">Once done your tab should be loaded inside Microsoft Teams!</span></span>

![guia executando no Teams](~/assets/yeoman-images/teams-first-app-6.png)

<span data-ttu-id="4360e-190">**Parabéns! Você criou e implantou seu primeiro aplicativo do Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="4360e-190">**Congrats! You built and deployed your first Microsoft Teams App**</span></span>
