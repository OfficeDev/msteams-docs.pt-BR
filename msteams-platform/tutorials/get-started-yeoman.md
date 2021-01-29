---
title: 'Tutorial : Criar seu primeiro aplicativo usando o gerador Yeoman'
description: Saiba como começar a criar aplicativos do Microsoft Teams com o gerador Yeoman.
keywords: getting started node.js nodejs yeoman
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: f7f0fb3ba1be28dfa7d343be3af9d122b4ad090d
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037001"
---
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a><span data-ttu-id="eee2f-104">Criar seu primeiro aplicativo Microsoft Teams usando o gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="eee2f-104">Create your first Microsoft Teams app using the Yeoman generator</span></span>

>[!Note]
><span data-ttu-id="eee2f-105">Este tutorial vem do gerador [Yeoman para wiki do Teams.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)</span><span class="sxs-lookup"><span data-stu-id="eee2f-105">This tutorial comes from the [Yeoman generator for Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span>

<span data-ttu-id="eee2f-106">Neste tutorial, vamos dar um passo a passo para criar seu primeiro aplicativo Microsoft Teams usando o gerador Yeoman do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="eee2f-106">In this tutorial we will walk through creating your very first Microsoft Teams app using the Microsoft Teams Yeoman generator.</span></span> <span data-ttu-id="eee2f-107">Ele supõe que você tenha uma conta do Teams que permite o [sideload do aplicativo.](~/concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="eee2f-107">It assumes that you have a Teams account that allows [app sideloading](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

![yeoman generator git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a><span data-ttu-id="eee2f-109">Configurar e preparar seu computador</span><span class="sxs-lookup"><span data-stu-id="eee2f-109">Setup and prepare your machine</span></span>

<span data-ttu-id="eee2f-110">Você precisa instalar o seguinte em seu computador antes de começar a usar o gerador Yeoman.</span><span class="sxs-lookup"><span data-stu-id="eee2f-110">You need to install the following on your machine before starting to use the Yeoman generator.</span></span>

### <a name="install-nodejs"></a><span data-ttu-id="eee2f-111">Instale o Node.js.</span><span class="sxs-lookup"><span data-stu-id="eee2f-111">Install Node.js</span></span>

<span data-ttu-id="eee2f-112">Você precisa ter Node.js instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="eee2f-112">You need to have Node.js installed on your machine.</span></span> <span data-ttu-id="eee2f-113">Você deve usar a versão [mais recente do LTS.](https://nodejs.org)</span><span class="sxs-lookup"><span data-stu-id="eee2f-113">You should use the latest [LTS version](https://nodejs.org).</span></span>

### <a name="install-a-code-editor"></a><span data-ttu-id="eee2f-114">Instalar um editor de códigos</span><span class="sxs-lookup"><span data-stu-id="eee2f-114">Install a code editor</span></span>

<span data-ttu-id="eee2f-115">Você também precisa de um editor de código, sinta-se à vontade para usar o editor de texto de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="eee2f-115">You also need a code editor, feel free to use whatever text editor you prefer.</span></span> <span data-ttu-id="eee2f-116">No entanto, a maioria desta documentação e capturas de tela se refere ao uso do [Visual Studio Code.](https://code.visualstudio.com)</span><span class="sxs-lookup"><span data-stu-id="eee2f-116">However most of this documentation and screenshots refer to using [Visual Studio Code](https://code.visualstudio.com).</span></span>

### <a name="install-yeoman-and-gulp-cli"></a><span data-ttu-id="eee2f-117">Instalar Yeoman e Gulp CLI</span><span class="sxs-lookup"><span data-stu-id="eee2f-117">Install Yeoman and Gulp CLI</span></span>

<span data-ttu-id="eee2f-118">Para fazer scaffold dos projetos usando o gerador do Teams, você precisa instalar a ferramenta Yeoman, bem como o gerenciador de tarefas da CLI gulp.</span><span class="sxs-lookup"><span data-stu-id="eee2f-118">To be able to scaffold projects using the Teams generator you need to install the Yeoman tool as well as the Gulp CLI task manager.</span></span>

<span data-ttu-id="eee2f-119">Abra um prompt de comando e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="eee2f-119">Open up a command prompt and type the following:</span></span>

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-generator"></a><span data-ttu-id="eee2f-120">Instalar o gerador</span><span class="sxs-lookup"><span data-stu-id="eee2f-120">Install the generator</span></span>

<span data-ttu-id="eee2f-121">Instale o gerador Yeoman do Teams com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="eee2f-121">Install the Teams Yeoman generator with the following command:</span></span>

```bash
npm install generator-teams --global
```

<span data-ttu-id="eee2f-122">Para instalar versões de visualização do gerador, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="eee2f-122">To install preview versions of the generator, run this command:</span></span>

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a><span data-ttu-id="eee2f-123">Gerar seu projeto</span><span class="sxs-lookup"><span data-stu-id="eee2f-123">Generate your project</span></span>

<span data-ttu-id="eee2f-124">Abra um prompt de comando e crie um novo diretório onde você deseja criar seu projeto e, nesse diretório, execute o `yo teams` comando.</span><span class="sxs-lookup"><span data-stu-id="eee2f-124">Open up a command prompt and create a new directory where you want to create your project and in that directory run the command `yo teams`.</span></span>

<span data-ttu-id="eee2f-125">Isso inicia o gerador, que solicita um conjunto de perguntas.</span><span class="sxs-lookup"><span data-stu-id="eee2f-125">This starts the generator, which prompts you with a set of questions.</span></span>

![yo teams](~/assets/yeoman-images/teams-first-app-1.png)

<span data-ttu-id="eee2f-127">A primeira pergunta é sobre o nome do seu projeto, você pode deixá-lo como está pressionando Enter.</span><span class="sxs-lookup"><span data-stu-id="eee2f-127">The first question is about your project name, you can leave it as is by pressing enter.</span></span> <span data-ttu-id="eee2f-128">A próxima pergunta pergunta se você deseja criar um novo diretório ou usar o atual.</span><span class="sxs-lookup"><span data-stu-id="eee2f-128">Next question asks you if you want to create a new directory or use the current one.</span></span> <span data-ttu-id="eee2f-129">Como já estamos no diretório que queremos, basta pressionar Enter.</span><span class="sxs-lookup"><span data-stu-id="eee2f-129">As we already are in the directory we want, we just press enter.</span></span>

<span data-ttu-id="eee2f-130">A etapa a seguir solicita um título do seu projeto. Esse título será usado no manifesto e na descrição do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eee2f-130">The following step asks for a title of your project, this title will be used in the manifest and description of your app.</span></span> <span data-ttu-id="eee2f-131">E, em seguida, você será solicitado a usar um nome de empresa, que também será usado no manifesto.</span><span class="sxs-lookup"><span data-stu-id="eee2f-131">And then you will be asked for a company name, which also will be used in the manifest.</span></span>

<span data-ttu-id="eee2f-132">A quinta pergunta pergunta sobre qual versão do manifesto você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="eee2f-132">The fifth question asks you about what version of the manifest you want to use.</span></span> <span data-ttu-id="eee2f-133">Para este `v1.5` tutorial, selecione , que é o esquema disponível geral atual.</span><span class="sxs-lookup"><span data-stu-id="eee2f-133">For this tutorial select `v1.5`, which is the current general available schema.</span></span>

<span data-ttu-id="eee2f-134">Depois disso, o gerador perguntará quais itens você deseja adicionar ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="eee2f-134">After this the generator will ask you for what items you want to add to your project.</span></span> <span data-ttu-id="eee2f-135">Você pode selecionar um único item ou qualquer combinação de itens.</span><span class="sxs-lookup"><span data-stu-id="eee2f-135">You can select a single one or any combination of items.</span></span> <span data-ttu-id="eee2f-136">Por enquanto, basta selecionar *uma guia*.</span><span class="sxs-lookup"><span data-stu-id="eee2f-136">For now, just select *a Tab*.</span></span>

![seleção de itens](~/assets/yeoman-images/teams-first-app-2.png)

<span data-ttu-id="eee2f-138">Com base nos itens selecionados, você será solicitado a fazer um conjunto de perguntas de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="eee2f-138">Based on what items you select, you will be asked a set of follow-up questions.</span></span>

<span data-ttu-id="eee2f-139">Agora você precisa inserir uma URL de onde hospedará sua solução.</span><span class="sxs-lookup"><span data-stu-id="eee2f-139">Now you need to enter a URL of where you will host your solution.</span></span> <span data-ttu-id="eee2f-140">Pode ser qualquer URL, mas, por padrão, o gerador sugere uma URL de Sites do Azure.</span><span class="sxs-lookup"><span data-stu-id="eee2f-140">This can be any URL, but by default the generator suggests an Azure Web Sites URL.</span></span>

<span data-ttu-id="eee2f-141">O gerador tem muitos recursos avançados integrados que você pode optar ou não.</span><span class="sxs-lookup"><span data-stu-id="eee2f-141">The generator has a lot of built-in advanced features that you can opt-in or opt-out of.</span></span> <span data-ttu-id="eee2f-142">Seguindo a pergunta da URL, você será solicitado se quiser incluir testes de unidade para sua solução, o padrão é Sim.</span><span class="sxs-lookup"><span data-stu-id="eee2f-142">Following the URL question you will be asked if you want to include unit-testing for your solution, default is yes.</span></span> <span data-ttu-id="eee2f-143">Se você escolher isso, o projeto gerado terá uma estrutura de teste de unidade e alguns testes de unidade padrão para os diferentes itens que estão sendo scaffolded.</span><span class="sxs-lookup"><span data-stu-id="eee2f-143">If you choose this the generated project will have a unit testing framework and some default unit tests for the different items being scaffolded.</span></span> <span data-ttu-id="eee2f-144">Para este tutorial, opte por não incluir uma estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="eee2f-144">For this tutorial choose not to include a test framework.</span></span>

<span data-ttu-id="eee2f-145">Para facilitar o registro em log para você, você também será perguntado se deseja usar o Azure Application Insights para registrar em log.</span><span class="sxs-lookup"><span data-stu-id="eee2f-145">In order to make logging easy for you, you will also be asked if you want to use Azure Application Insights for logging.</span></span> <span data-ttu-id="eee2f-146">Se você escolher Sim, precisará fornecer uma chave do Insights do Aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="eee2f-146">If you choose Yes, you will need to provide a Azure Application Insights key.</span></span> <span data-ttu-id="eee2f-147">Para este tutorial, opte por não usar o Application Insights.</span><span class="sxs-lookup"><span data-stu-id="eee2f-147">For this tutorial opt-out of using Application Insights.</span></span>

<span data-ttu-id="eee2f-148">O próximo conjunto de perguntas será baseado em sua seleção de itens anteriormente.</span><span class="sxs-lookup"><span data-stu-id="eee2f-148">The next set of questions will be based on your selection of items previously.</span></span> <span data-ttu-id="eee2f-149">Para uma guia, você só precisa fornecer um nome e, opcionalmente, escolher se deseja usar esse aplicativo como uma Web Part do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="eee2f-149">For a tab you only need to provide a name and optionally choose if you want to be able to use this app as a SharePoint Online web part.</span></span> <span data-ttu-id="eee2f-150">Depois de ter fornecido esse nome, o gerador gerará o projeto e instalará todas as dependências.</span><span class="sxs-lookup"><span data-stu-id="eee2f-150">Once you have provided this name the generator will generate the project and install all dependencies.</span></span> <span data-ttu-id="eee2f-151">Isso levará um minuto ou dois.</span><span class="sxs-lookup"><span data-stu-id="eee2f-151">This will take a minute or two.</span></span>

## <a name="add-some-code-to-your-tab"></a><span data-ttu-id="eee2f-152">Adicionar código à guia</span><span class="sxs-lookup"><span data-stu-id="eee2f-152">Add some code to your tab</span></span>

<span data-ttu-id="eee2f-153">Quando o gerador for feito, você poderá abrir a solução em seu editor de código favorito.</span><span class="sxs-lookup"><span data-stu-id="eee2f-153">Once the generator is done you can open up the solution in your favorite code editor.</span></span> <span data-ttu-id="eee2f-154">Leve um minuto ou dois e familiarize-se com a forma como o código é organizado. Você pode ler mais sobre isso na documentação da [Estrutura do](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) Projeto.</span><span class="sxs-lookup"><span data-stu-id="eee2f-154">Take a minute or two and familiarize yourself with how the code is organized - you can read more about that in the [Project Structure](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) documentation.</span></span>

<span data-ttu-id="eee2f-155">A guia estará localizada no `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` arquivo.</span><span class="sxs-lookup"><span data-stu-id="eee2f-155">Your Tab will be located in the `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` file.</span></span> <span data-ttu-id="eee2f-156">Esta é a classe baseada em TypeScript React para sua guia. Localize o método e adicione uma linha de código dentro do controle para `render()` que ele tenha esta `<PanelBody>` aparência:</span><span class="sxs-lookup"><span data-stu-id="eee2f-156">This is the TypeScript React based class for your Tab. Locate the `render()` method and add a line of code inside the `<PanelBody>` control so it looks like this:</span></span>

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

<span data-ttu-id="eee2f-157">Salve o arquivo e retorne ao prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="eee2f-157">Save the file and return to the command prompt.</span></span>

## <a name="build-your-app"></a><span data-ttu-id="eee2f-158">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="eee2f-158">Build your app</span></span>

<span data-ttu-id="eee2f-159">Agora você pode criar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="eee2f-159">You can now build your project.</span></span> <span data-ttu-id="eee2f-160">Isso é feito em duas etapas (ou em uma etapa, veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="eee2f-160">This is done in two steps (or one step, see below).</span></span>

<span data-ttu-id="eee2f-161">Primeiro, você precisa criar o arquivo de manifesto do aplicativo Teams, que você carrega/faz sideload no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="eee2f-161">First you need to create the Teams App manifest file, that you upload/sideload into Microsoft Teams.</span></span> <span data-ttu-id="eee2f-162">Isso é feito pela tarefa `gulp manifest` gulp.</span><span class="sxs-lookup"><span data-stu-id="eee2f-162">This is done by the Gulp task `gulp manifest`.</span></span> <span data-ttu-id="eee2f-163">Isso validará o manifesto e criará um arquivo zip no `./package` diretório.</span><span class="sxs-lookup"><span data-stu-id="eee2f-163">This will validate the manifest and create a zip file in the `./package` directory.</span></span>

<span data-ttu-id="eee2f-164">Para criar sua solução, use o `gulp build` comando.</span><span class="sxs-lookup"><span data-stu-id="eee2f-164">To build your solution you use the `gulp build` command.</span></span> <span data-ttu-id="eee2f-165">Isso transpile sua solução para a `./dist` pasta.</span><span class="sxs-lookup"><span data-stu-id="eee2f-165">This will transpile your solution into the `./dist` folder.</span></span> 

## <a name="run-your-app"></a><span data-ttu-id="eee2f-166">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="eee2f-166">Run your app</span></span>

<span data-ttu-id="eee2f-167">Para executar seu aplicativo, use o `gulp serve` comando.</span><span class="sxs-lookup"><span data-stu-id="eee2f-167">To run your app you use the `gulp serve` command.</span></span> <span data-ttu-id="eee2f-168">Isso criará e iniciará um servidor Web local para você testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eee2f-168">This will build and start a local web server for you to test your app.</span></span> <span data-ttu-id="eee2f-169">O comando também recriará o aplicativo sempre que você salvar um arquivo em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="eee2f-169">The command will also rebuild the application whenever you save a file in your project.</span></span> 

<span data-ttu-id="eee2f-170">Agora você deve ser capaz de navegar para `http://localhost:3007/myFirstAppTab/` garantir que sua guia seja renderização.</span><span class="sxs-lookup"><span data-stu-id="eee2f-170">You should now be able to browse to `http://localhost:3007/myFirstAppTab/` to ensure that your tab is rendering.</span></span> <span data-ttu-id="eee2f-171">No entanto, ainda não está no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="eee2f-171">However, not in Microsoft Teams yet.</span></span>

![exibir seu site em um navegador](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a><span data-ttu-id="eee2f-173">Executar seu aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="eee2f-173">Run your app in Microsoft Teams</span></span>

<span data-ttu-id="eee2f-174">O Microsoft Teams não permite que você tenha seu aplicativo hospedado no localhost, portanto, você precisa publicá-lo em uma URL pública ou usar um proxy como o ngrok.</span><span class="sxs-lookup"><span data-stu-id="eee2f-174">Microsoft Teams does not allow you to have your app hosted on localhost, so you need to either publish it to a public URL or use a proxy such as ngrok.</span></span>

<span data-ttu-id="eee2f-175">Uma boa notícia é que o projeto com scaffolded tem esse projeto integrado.</span><span class="sxs-lookup"><span data-stu-id="eee2f-175">Good news is that the scaffolded project has this built-in.</span></span> <span data-ttu-id="eee2f-176">Quando você executar o serviço ngrok será iniciado em segundo plano, com uma entrada DNS exclusiva e pública e ele também empacota o manifesto com essa URL exclusiva e, em seguida, faz exatamente o mesmo `gulp ngrok-serve` que `gulp serve` .</span><span class="sxs-lookup"><span data-stu-id="eee2f-176">When you run `gulp ngrok-serve` the ngrok service will be started in the background, with a unique and public DNS entry and it will also package the manifest with that unique URL and then do the exact same thing as `gulp serve`.</span></span>

<span data-ttu-id="eee2f-177">Depois de executar, crie uma nova equipe do Microsoft Teams e, quando ela for criada, clique no nome da equipe, para ir para as configurações de equipe e, em seguida, `gulp ngrok-serve` selecione *Aplicativos.*</span><span class="sxs-lookup"><span data-stu-id="eee2f-177">After running `gulp ngrok-serve`, create a new Microsoft Teams team and when it is created click on the Team name, to go to the teams settings and then select *Apps*.</span></span> <span data-ttu-id="eee2f-178">No canto inferior direito, você verá um link Carregar um aplicativo personalizado, selecione-o e navegue até *a* pasta do projeto e a subpasta `package` chamada.</span><span class="sxs-lookup"><span data-stu-id="eee2f-178">In the lower right corner you should see a link *Upload a custom app*, select it and then browse to your project folder and the subfolder called `package`.</span></span> <span data-ttu-id="eee2f-179">Selecione o arquivo zip nessa pasta e escolha abrir.</span><span class="sxs-lookup"><span data-stu-id="eee2f-179">Select the zip file in that folder and choose open.</span></span> <span data-ttu-id="eee2f-180">Seu aplicativo agora está em sideload no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="eee2f-180">Your App is now sideloaded into Microsoft Teams.</span></span>

![aplicativo de sideload](~/assets/yeoman-images/teams-first-app-4.png)

<span data-ttu-id="eee2f-182">Volte para o *canal Geral* e selecione adicionar uma *+* nova guia. Você deverá ver sua guia na lista de guias.</span><span class="sxs-lookup"><span data-stu-id="eee2f-182">Go back to the *General* channel and select *+* to add a new Tab. You should see your tab in the list of tabs.</span></span>

![configurar guia](~/assets/yeoman-images/teams-first-app-5.png)

<span data-ttu-id="eee2f-184">Escolha sua guia e siga as instruções para adicioná-la.</span><span class="sxs-lookup"><span data-stu-id="eee2f-184">Choose your tab and follow the instructions to add it.</span></span> <span data-ttu-id="eee2f-185">Observe que você tem uma caixa de diálogo de configuração personalizada, para a qual você pode editar a origem.</span><span class="sxs-lookup"><span data-stu-id="eee2f-185">Notice that you have a custom configuration dialog, for which you can edit the source.</span></span> <span data-ttu-id="eee2f-186">Selecione *Salvar* para adicionar sua guia ao canal.</span><span class="sxs-lookup"><span data-stu-id="eee2f-186">Select *Save* to add your tab to the channel.</span></span> <span data-ttu-id="eee2f-187">Quando terminar, sua guia deverá ser carregada no Microsoft Teams!</span><span class="sxs-lookup"><span data-stu-id="eee2f-187">Once done your tab should be loaded inside Microsoft Teams!</span></span>

![guia em execução nas equipes](~/assets/yeoman-images/teams-first-app-6.png)

<span data-ttu-id="eee2f-189">**Parabéns! Você criou e implantou seu primeiro aplicativo Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="eee2f-189">**Congrats! You built and deployed your first Microsoft Teams app**</span></span>
