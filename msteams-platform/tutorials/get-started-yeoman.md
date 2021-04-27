---
title: Tutorial - Criar seu primeiro aplicativo usando o gerador Yeoman
description: Saiba como começar a criar aplicativos do Microsoft Teams com o gerador Yeoman.
keywords: getting started node.js nodejs yeoman
localization_priority: Normal
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: 9efbe6f6e6502120f1afdadb9b538182f1406c56
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52018429"
---
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a><span data-ttu-id="518be-104">Criar seu primeiro aplicativo do Microsoft Teams usando o gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="518be-104">Create your first Microsoft Teams app using the Yeoman generator</span></span>

> [!Note]
> <span data-ttu-id="518be-105">Este tutorial vem do gerador [Yeoman para o Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span><span class="sxs-lookup"><span data-stu-id="518be-105">This tutorial comes from the [Yeoman generator for Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span>

<span data-ttu-id="518be-106">Neste tutorial, vamos continuar criando seu primeiro aplicativo do Microsoft Teams usando o gerador Yeoman do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="518be-106">In this tutorial, we will walk through creating your very first Microsoft Teams app using the Microsoft Teams Yeoman generator.</span></span> <span data-ttu-id="518be-107">Ele também o orienta pelo processo de atualização do Teams usando o gerador Yeoman.</span><span class="sxs-lookup"><span data-stu-id="518be-107">It also walks you through the process of upgrading your Teams using the Yeoman generator.</span></span> <span data-ttu-id="518be-108">O pré-requisito para começar com este tutorial é que você tem uma conta do Teams que permite o [sideload de aplicativos.](~/concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="518be-108">The prerequisite to start with this tutorial is that you have a Teams account that allows [app sideloading](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

![git do gerador yeoman](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a><span data-ttu-id="518be-110">Configurar e preparar seu computador</span><span class="sxs-lookup"><span data-stu-id="518be-110">Setup and prepare your machine</span></span>

<span data-ttu-id="518be-111">Você precisa instalar o seguinte em seu computador antes de começar a usar o gerador Yeoman.</span><span class="sxs-lookup"><span data-stu-id="518be-111">You need to install the following on your machine before starting to use the Yeoman generator.</span></span>

### <a name="install-nodejs"></a><span data-ttu-id="518be-112">Instale o Node.js.</span><span class="sxs-lookup"><span data-stu-id="518be-112">Install Node.js</span></span>

<span data-ttu-id="518be-113">Você precisa ter Node.js instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="518be-113">You need to have Node.js installed on your machine.</span></span> <span data-ttu-id="518be-114">Você deve usar a versão [LTS mais recente.](https://nodejs.org)</span><span class="sxs-lookup"><span data-stu-id="518be-114">You should use the latest [LTS version](https://nodejs.org).</span></span>

### <a name="install-a-code-editor"></a><span data-ttu-id="518be-115">Instalar um editor de códigos</span><span class="sxs-lookup"><span data-stu-id="518be-115">Install a code editor</span></span>

<span data-ttu-id="518be-116">Você precisa de um editor de código.</span><span class="sxs-lookup"><span data-stu-id="518be-116">You need a code editor.</span></span> <span data-ttu-id="518be-117">A maioria dessa documentação e imagens se refere ao uso [Visual Studio Código](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="518be-117">Most of this documentation and images refer to using [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="518be-118">No entanto, sinta-se à vontade para usar qualquer editor de texto que preferir.</span><span class="sxs-lookup"><span data-stu-id="518be-118">However, feel free to use whatever text editor you prefer.</span></span>

### <a name="install-yeoman-and-gulp-cli"></a><span data-ttu-id="518be-119">Instalar Yeoman e Gulp CLI</span><span class="sxs-lookup"><span data-stu-id="518be-119">Install Yeoman and Gulp CLI</span></span>

<span data-ttu-id="518be-120">Para scaffold projetos usando o gerador, você deve instalar a ferramenta Yeoman e o gerenciador de tarefas cli gulp.</span><span class="sxs-lookup"><span data-stu-id="518be-120">To scaffold projects using the generator, you must install the Yeoman tool and Gulp CLI task manager.</span></span>

<span data-ttu-id="518be-121">Abra um prompt de comando e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="518be-121">Open up a command prompt and type the following:</span></span>

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-generator"></a><span data-ttu-id="518be-122">Instalar o gerador</span><span class="sxs-lookup"><span data-stu-id="518be-122">Install the generator</span></span>

<span data-ttu-id="518be-123">Instale o gerador Yeoman do Teams com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="518be-123">Install the Teams Yeoman generator with the following command:</span></span>

```bash
npm install generator-teams --global
```

<span data-ttu-id="518be-124">Instale a versão de visualização do gerador com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="518be-124">Install the preview version of the generator with the following command:</span></span>

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a><span data-ttu-id="518be-125">Gerar seu projeto</span><span class="sxs-lookup"><span data-stu-id="518be-125">Generate your project</span></span>

<span data-ttu-id="518be-126">Esta seção orienta você pelas etapas para gerar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="518be-126">This section walks you through the steps for generating your project.</span></span>

<span data-ttu-id="518be-127">**Para gerar seu projeto**</span><span class="sxs-lookup"><span data-stu-id="518be-127">**To generate your project**</span></span>

1. <span data-ttu-id="518be-128">Abra um prompt de comando e crie um novo diretório onde você deseja criar seu projeto e, nesse diretório, execute o comando `yo teams` .</span><span class="sxs-lookup"><span data-stu-id="518be-128">Open up a command prompt and create a new directory where you want to create your project, and in that directory run the command `yo teams`.</span></span> <span data-ttu-id="518be-129">O gerador é iniciado.</span><span class="sxs-lookup"><span data-stu-id="518be-129">The generator starts.</span></span>
1. <span data-ttu-id="518be-130">Responda ao conjunto de perguntas solicitado pelo gerador.</span><span class="sxs-lookup"><span data-stu-id="518be-130">Respond to the set of questions prompted by the generator.</span></span>

   ![yo teams](~/assets/yeoman-images/teams-first-app-1.png)

   1. <span data-ttu-id="518be-132">A primeira pergunta é sobre o nome do seu projeto, você pode deixá-lo como está pressionando enter.</span><span class="sxs-lookup"><span data-stu-id="518be-132">The first question is about your project name, you can leave it as is by pressing enter.</span></span>
   1. <span data-ttu-id="518be-133">A próxima pergunta pergunta se você deseja criar um novo diretório ou usar o atual.</span><span class="sxs-lookup"><span data-stu-id="518be-133">Next question asks you if you want to create a new directory or use the current one.</span></span> <span data-ttu-id="518be-134">Como você já está no diretório que deseja, pressione enter.</span><span class="sxs-lookup"><span data-stu-id="518be-134">As you are already in the directory you want, just press enter.</span></span>
   1. <span data-ttu-id="518be-135">Na próxima pergunta, digite o título do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="518be-135">In the next question, type the title of your project.</span></span> <span data-ttu-id="518be-136">Esse título será usado no manifesto e na descrição do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="518be-136">This title will be used in the manifest and description of your app.</span></span> 
   1. <span data-ttu-id="518be-137">Em seguida, será solicitado um nome da empresa, que também será usado no manifesto.</span><span class="sxs-lookup"><span data-stu-id="518be-137">Next, you will be asked for a company name, which also will be used in the manifest.</span></span>
   1. <span data-ttu-id="518be-138">A quinta pergunta pergunta sobre qual versão do manifesto você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="518be-138">The fifth question asks you about what version of the manifest you want to use.</span></span> <span data-ttu-id="518be-139">Para este tutorial, selecione `v1.5` , que é o esquema disponível geral atual.</span><span class="sxs-lookup"><span data-stu-id="518be-139">For this tutorial select `v1.5`, which is the current general available schema.</span></span>
   1. <span data-ttu-id="518be-140">Em seguida, o gerador perguntará quais itens você deseja adicionar ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="518be-140">Next, the generator will ask you for what items you want to add to your project.</span></span> <span data-ttu-id="518be-141">Você pode selecionar um único ou qualquer combinação de itens.</span><span class="sxs-lookup"><span data-stu-id="518be-141">You can select a single one or any combination of items.</span></span> <span data-ttu-id="518be-142">Para este tutorial, basta selecionar *uma guia*.</span><span class="sxs-lookup"><span data-stu-id="518be-142">For this tutorials, just select *a Tab*.</span></span>

    ![seleção de item](~/assets/yeoman-images/teams-first-app-2.png)

1. <span data-ttu-id="518be-144">Responda ao próximo conjunto de perguntas de acompanhamento que aparecem com base nos itens selecionados na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="518be-144">Respond to the next set of follow-up questions that appear based on the items you selected in step 2.</span></span>
1. <span data-ttu-id="518be-145">Insira uma URL de onde você hospedará sua solução.</span><span class="sxs-lookup"><span data-stu-id="518be-145">Enter a URL of where you will host your solution.</span></span> 

   > [!NOTE]
   > <span data-ttu-id="518be-146">A URL pode ser qualquer URL, mas, por padrão, o gerador sugere uma URL do site do Azure.</span><span class="sxs-lookup"><span data-stu-id="518be-146">The URL can be any URL, but by default the generator suggests an Azure web site URL.</span></span>

1. <span data-ttu-id="518be-147">Na próxima pergunta, confirme se você deseja incluir testes de unidade para sua solução.</span><span class="sxs-lookup"><span data-stu-id="518be-147">In the next question, confirm if you want to include unit-testing for your solution.</span></span> <span data-ttu-id="518be-148">A resposta padrão é *sim*.</span><span class="sxs-lookup"><span data-stu-id="518be-148">The default response is *yes*.</span></span> <span data-ttu-id="518be-149">Se você optar por incluir teste de unidade, o projeto gerado terá uma estrutura de teste de unidade e alguns testes de unidade padrão para os diferentes itens que estão sendo scaffolded.</span><span class="sxs-lookup"><span data-stu-id="518be-149">If you choose to include unit-testing, the generated project will have a unit testing framework and some default unit tests for the different items being scaffolded.</span></span> 
   > [!NOTE]
   > * <span data-ttu-id="518be-150">Para este tutorial, escolha não incluir uma estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="518be-150">For this tutorial choose not to include a test framework.</span></span>
   > * <span data-ttu-id="518be-151">O gerador tem muitos recursos avançados integrados que você pode optar ou não.</span><span class="sxs-lookup"><span data-stu-id="518be-151">The generator has a lot of built-in advanced features that you can opt-in or opt-out of.</span></span>

1. <span data-ttu-id="518be-152">Para facilitar a sua assinatura, você também será perguntado se deseja usar o Azure Application Insights para entrar.</span><span class="sxs-lookup"><span data-stu-id="518be-152">In order to make signing-in easy for you, you will also be asked if you want to use Azure Application Insights for signing-in.</span></span> <span data-ttu-id="518be-153">Se você escolher *Sim*, será necessário fornecer uma chave do Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="518be-153">If you choose *Yes*, you will need to provide an Azure Application Insights key.</span></span> 

   > [!NOTE]
   > <span data-ttu-id="518be-154">Para este tutorial, opt-out of using Application Insights.</span><span class="sxs-lookup"><span data-stu-id="518be-154">For this tutorial opt-out of using Application Insights.</span></span>

<span data-ttu-id="518be-155">O próximo conjunto de perguntas será baseado nos itens selecionados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="518be-155">The next set of questions will be based on the previously selected items.</span></span> <span data-ttu-id="518be-156">Para uma guia, você só precisa fornecer um nome e, opcionalmente, escolher se deseja usar esse aplicativo como uma web part do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="518be-156">For a tab you only need to provide a name and optionally choose if you want to be able to use this app as a SharePoint Online web part.</span></span> <span data-ttu-id="518be-157">Depois de fornecer o nome, o gerador gerará o projeto e instalará todas as dependências.</span><span class="sxs-lookup"><span data-stu-id="518be-157">After you provide the name the generator will generate the project and install all dependencies.</span></span> <span data-ttu-id="518be-158">Isso levará um minuto ou dois.</span><span class="sxs-lookup"><span data-stu-id="518be-158">This will take a minute or two.</span></span>

## <a name="add-some-code-to-your-tab"></a><span data-ttu-id="518be-159">Adicionar algum código à sua guia</span><span class="sxs-lookup"><span data-stu-id="518be-159">Add some code to your tab</span></span>

<span data-ttu-id="518be-160">Depois que o gerador for feito, você poderá abrir a solução no editor de código favorito.</span><span class="sxs-lookup"><span data-stu-id="518be-160">After the generator is done you can open up the solution in your favorite code editor.</span></span> <span data-ttu-id="518be-161">Tome um minuto ou dois e familiarize-se com como o código é organizado.</span><span class="sxs-lookup"><span data-stu-id="518be-161">Take a minute or two and familiarize yourself with how the code is organized.</span></span> <span data-ttu-id="518be-162">Para obter mais informações, consulte [Documentação da Estrutura do](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) Projeto.</span><span class="sxs-lookup"><span data-stu-id="518be-162">For more information, see [Project Structure](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) documentation.</span></span>

<span data-ttu-id="518be-163">Sua guia está no `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` arquivo.</span><span class="sxs-lookup"><span data-stu-id="518be-163">Your tab is in the `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` file.</span></span> <span data-ttu-id="518be-164">Esta é a classe baseada em TypeScript React para sua guia. Localize `render()` o método e adicione uma linha de código dentro do controle para que ele tenha esta `<PanelBody>` aparência:</span><span class="sxs-lookup"><span data-stu-id="518be-164">This is the TypeScript React-based class for your tab. Locate the `render()` method and add a line of code inside the `<PanelBody>` control so it looks like this:</span></span>

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

<span data-ttu-id="518be-165">Salve o arquivo e retorne ao prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="518be-165">Save the file and return to the command prompt.</span></span>

## <a name="build-your-app"></a><span data-ttu-id="518be-166">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="518be-166">Build your app</span></span>

<span data-ttu-id="518be-167">Agora você pode criar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="518be-167">You can now build your project.</span></span> <span data-ttu-id="518be-168">Isso é feito em duas etapas (ou em uma etapa, consulte abaixo).</span><span class="sxs-lookup"><span data-stu-id="518be-168">This is done in two steps (or one step, see below).</span></span>

<span data-ttu-id="518be-169">Primeiro, você precisa criar o arquivo de manifesto do Aplicativo do Teams, que você carrega/carrega no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="518be-169">First you need to create the Teams App manifest file, that you upload/sideload into Microsoft Teams.</span></span> <span data-ttu-id="518be-170">Isso é feito pela tarefa `gulp manifest` Gulp.</span><span class="sxs-lookup"><span data-stu-id="518be-170">This is done by the Gulp task `gulp manifest`.</span></span> <span data-ttu-id="518be-171">Isso validará o manifesto e criará um arquivo zip no `./package` diretório.</span><span class="sxs-lookup"><span data-stu-id="518be-171">This will validate the manifest and create a zip file in the `./package` directory.</span></span>

<span data-ttu-id="518be-172">Para criar sua solução, use o `gulp build` comando.</span><span class="sxs-lookup"><span data-stu-id="518be-172">To build your solution you use the `gulp build` command.</span></span> <span data-ttu-id="518be-173">Isso transpile sua solução para a `./dist` pasta.</span><span class="sxs-lookup"><span data-stu-id="518be-173">This will transpile your solution into the `./dist` folder.</span></span> 

## <a name="run-your-app"></a><span data-ttu-id="518be-174">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="518be-174">Run your app</span></span>

<span data-ttu-id="518be-175">Para executar seu aplicativo, use o `gulp serve` comando.</span><span class="sxs-lookup"><span data-stu-id="518be-175">To run your app you use the `gulp serve` command.</span></span> <span data-ttu-id="518be-176">Isso criará e iniciará um servidor Web local para você testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="518be-176">This will build and start a local web server for you to test your app.</span></span> <span data-ttu-id="518be-177">O comando também reconstruirá o aplicativo sempre que você salvar um arquivo em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="518be-177">The command will also rebuild the application whenever you save a file in your project.</span></span> 

<span data-ttu-id="518be-178">Agora você deve ser capaz de navegar para `http://localhost:3007/myFirstAppTab/` garantir que sua guia seja renderização.</span><span class="sxs-lookup"><span data-stu-id="518be-178">You should now be able to browse to `http://localhost:3007/myFirstAppTab/` to ensure that your tab is rendering.</span></span> <span data-ttu-id="518be-179">No entanto, ainda não no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="518be-179">However, not in Microsoft Teams yet.</span></span>

![exibir seu site em um navegador](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a><span data-ttu-id="518be-181">Executar seu aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="518be-181">Run your app in Microsoft Teams</span></span>

<span data-ttu-id="518be-182">O Microsoft Teams não permite que você tenha seu aplicativo hospedado no localhost, portanto, você precisa publicá-lo em uma URL pública ou usar um proxy como o ngrok.</span><span class="sxs-lookup"><span data-stu-id="518be-182">Microsoft Teams does not allow you to have your app hosted on localhost, so you need to either publish it to a public URL or use a proxy such as ngrok.</span></span>

<span data-ttu-id="518be-183">A boa notícia é que o projeto scaffolded tem esse projeto integrado.</span><span class="sxs-lookup"><span data-stu-id="518be-183">Good news is that the scaffolded project has this built-in.</span></span> <span data-ttu-id="518be-184">Quando você executar o serviço ngrok será iniciado em segundo plano, com uma entrada DNS pública e exclusiva e ele também empacota o manifesto com essa URL exclusiva e, em seguida, fará exatamente a mesma coisa `gulp ngrok-serve` que `gulp serve` .</span><span class="sxs-lookup"><span data-stu-id="518be-184">When you run `gulp ngrok-serve` the ngrok service will be started in the background, with a unique and public DNS entry and it will also package the manifest with that unique URL and then do the exact same thing as `gulp serve`.</span></span>

<span data-ttu-id="518be-185">Depois de executar, crie uma nova equipe do Microsoft Teams e, quando for criada, clique no nome da equipe, para ir até as configurações de equipe e selecione `gulp ngrok-serve` *Aplicativos*.</span><span class="sxs-lookup"><span data-stu-id="518be-185">After running `gulp ngrok-serve`, create a new Microsoft Teams team and when it is created click on the Team name, to go to the teams settings and then select *Apps*.</span></span> <span data-ttu-id="518be-186">No canto inferior direito, você deve ver um link Carregar um aplicativo personalizado, selecione-o e navegue até *a* pasta do projeto e a subpasta chamada `package` .</span><span class="sxs-lookup"><span data-stu-id="518be-186">In the lower right corner you should see a link *Upload a custom app*, select it and then browse to your project folder and the subfolder called `package`.</span></span> <span data-ttu-id="518be-187">Selecione o arquivo zip nessa pasta e escolha abrir.</span><span class="sxs-lookup"><span data-stu-id="518be-187">Select the zip file in that folder and choose open.</span></span> <span data-ttu-id="518be-188">Seu aplicativo agora é sideload no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="518be-188">Your App is now sideloaded into Microsoft Teams.</span></span>

![aplicativo sideloaded](~/assets/yeoman-images/teams-first-app-4.png)

<span data-ttu-id="518be-190">Volte para o *canal Geral* e selecione para adicionar uma *+* nova Guia. Você deve ver sua guia na lista de guias.</span><span class="sxs-lookup"><span data-stu-id="518be-190">Go back to the *General* channel and select *+* to add a new Tab. You should see your tab in the list of tabs.</span></span>

![configurar guia](~/assets/yeoman-images/teams-first-app-5.png)

<span data-ttu-id="518be-192">Escolha sua guia e siga as instruções para adicioná-la.</span><span class="sxs-lookup"><span data-stu-id="518be-192">Choose your tab and follow the instructions to add it.</span></span> <span data-ttu-id="518be-193">Observe que você tem uma caixa de diálogo de configuração personalizada, para a qual você pode editar a origem.</span><span class="sxs-lookup"><span data-stu-id="518be-193">Notice that you have a custom configuration dialog, for which you can edit the source.</span></span> <span data-ttu-id="518be-194">Selecione *Salvar* para adicionar sua guia ao canal.</span><span class="sxs-lookup"><span data-stu-id="518be-194">Select *Save* to add your tab to the channel.</span></span> <span data-ttu-id="518be-195">Depois de terminar, sua guia deve ser carregada dentro do Microsoft Teams!</span><span class="sxs-lookup"><span data-stu-id="518be-195">Once done your tab should be loaded inside Microsoft Teams!</span></span>

![guia de execução em equipes](~/assets/yeoman-images/teams-first-app-6.png)

## <a name="upgrade-microsoft-teams"></a><span data-ttu-id="518be-197">Atualizar o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="518be-197">Upgrade Microsoft Teams</span></span>

<span data-ttu-id="518be-198">Você também pode atualizar sua versão atual do Microsoft Teams para a versão mais recente usando o gerador Yeoman do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="518be-198">You can also upgrade your current Microsoft Teams version to the latest version using the Microsoft Teams Yeoman generator.</span></span>

<span data-ttu-id="518be-199">**Para atualizar o Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="518be-199">**To upgrade Microsoft Teams**</span></span>

1. <span data-ttu-id="518be-200">Obter a versão atual do Teams com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="518be-200">Get current version of Teams with the following command:</span></span>

   ```PowerShell
    yo teams --version
   ```
2. <span data-ttu-id="518be-201">Use o seguinte comando para selecionar atualizar seu gerador:</span><span class="sxs-lookup"><span data-stu-id="518be-201">Use the following command to select update your generator:</span></span>

   ```PowerShell
    yo
   ```
3. <span data-ttu-id="518be-202">Use as teclas de seta para escolher **Atualizar seus Geradores**.</span><span class="sxs-lookup"><span data-stu-id="518be-202">Use the  arrow keys to choose **Update your Generators**.</span></span>

   ![imagem de YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

4. <span data-ttu-id="518be-204">Selecione o gerador que você deseja na lista de geradores.</span><span class="sxs-lookup"><span data-stu-id="518be-204">Select the generator you want from the list of generators.</span></span>
   > [!NOTE]
   > <span data-ttu-id="518be-205">Use a barra de espaços para selecionar ou limpar uma versão selecionada do Teams nas opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="518be-205">Use the space bar to select or clear a selected Teams version from the available options.</span></span>

    ![imagem de UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)
    

   > [!NOTE]
   > <span data-ttu-id="518be-207">Leva alguns segundos para a instalação do Teams ser concluída.</span><span class="sxs-lookup"><span data-stu-id="518be-207">It takes few seconds to minutes for Teams installation to complete.</span></span>

5. <span data-ttu-id="518be-208">Depois que a instalação for concluída, use o seguinte comando para verificar a versão instalada:</span><span class="sxs-lookup"><span data-stu-id="518be-208">After the installation is complete, use the following command to check the installed version:</span></span>

   ```PowerShell
    yo teams --version
   ```
   
<span data-ttu-id="518be-209">**Parabéns! Você criou e implantou seu primeiro aplicativo do Microsoft Teams. Você também atualizou o Microsoft Teams.**</span><span class="sxs-lookup"><span data-stu-id="518be-209">**Congrats! You built and deployed your first Microsoft Teams app. You also upgraded Microsoft Teams.**</span></span>
