---
title: Tutorial - Criar seu primeiro aplicativo usando o gerador Yeoman
description: Saiba como começar a criar Microsoft Teams aplicativos com o gerador Yeoman.
keywords: getting started node.js nodejs yeoman
localization_priority: Normal
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: a3519da1495dc51a811f4e95bc4ada9b11aa8292
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254326"
---
# <a name="build-your-first-microsoft-teams-app-using-the-yeoman-generator"></a><span data-ttu-id="14568-104">Crie seu primeiro aplicativo Microsoft Teams usando o gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="14568-104">Build your first Microsoft Teams app using the Yeoman generator</span></span>

> [!Note]
> <span data-ttu-id="14568-105">Este tutorial vem do gerador [Yeoman para Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span><span class="sxs-lookup"><span data-stu-id="14568-105">This tutorial comes from the [Yeoman generator for Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span>

<span data-ttu-id="14568-106">Neste tutorial, você aprenderá a criar seu primeiro aplicativo Microsoft Teams usando o Microsoft Teams yeoman.</span><span class="sxs-lookup"><span data-stu-id="14568-106">In this tutorial, you will learn how to build your very first Microsoft Teams app using the Microsoft Teams Yeoman generator.</span></span> <span data-ttu-id="14568-107">Ele também orienta você pelo processo de atualização do seu Teams usando o gerador Yeoman.</span><span class="sxs-lookup"><span data-stu-id="14568-107">It also walks you through the process of upgrading your Teams using the Yeoman generator.</span></span> <span data-ttu-id="14568-108">Antes de começar, você deve ter uma conta Teams que permita o [sideload de aplicativos](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="14568-108">Before you begin, you must have a Teams account that allows [app sideloading](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

![git do gerador yeoman](~/assets/yeoman-demo.gif)

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="14568-110">Obter Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="14568-110">Get Prerequisites</span></span>

<span data-ttu-id="14568-111">Você precisa instalar o seguinte em seu computador antes de começar a usar o gerador Yeoman:</span><span class="sxs-lookup"><span data-stu-id="14568-111">You need to install the following on your machine before starting to use the Yeoman generator:</span></span>

* <span data-ttu-id="14568-112">Node.js</span><span class="sxs-lookup"><span data-stu-id="14568-112">Node.js</span></span>

   <span data-ttu-id="14568-113">Você precisa ter Node.js instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="14568-113">You need to have Node.js installed on your machine.</span></span> <span data-ttu-id="14568-114">Você deve usar a versão [LTS mais recente.](https://nodejs.org)</span><span class="sxs-lookup"><span data-stu-id="14568-114">You should use the latest [LTS version](https://nodejs.org).</span></span>

* <span data-ttu-id="14568-115">Um editor de código</span><span class="sxs-lookup"><span data-stu-id="14568-115">A code editor</span></span>

   <span data-ttu-id="14568-116">Você precisa de um editor de código.</span><span class="sxs-lookup"><span data-stu-id="14568-116">You need a code editor.</span></span> <span data-ttu-id="14568-117">A maioria dessa documentação e imagens se refere ao uso [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="14568-117">Most of this documentation and images refer to using [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="14568-118">No entanto, sinta-se à vontade para usar qualquer editor de texto que preferir.</span><span class="sxs-lookup"><span data-stu-id="14568-118">However, feel free to use whatever text editor you prefer.</span></span>

* <span data-ttu-id="14568-119">Yeoman e Gulp CLI</span><span class="sxs-lookup"><span data-stu-id="14568-119">Yeoman and Gulp CLI</span></span>

   <span data-ttu-id="14568-120">Para scaffold projetos usando o gerador, você deve instalar a ferramenta Yeoman e o gerenciador de tarefas cli gulp.</span><span class="sxs-lookup"><span data-stu-id="14568-120">To scaffold projects using the generator, you must install the Yeoman tool and Gulp CLI task manager.</span></span>

   <span data-ttu-id="14568-121">Abra um prompt de comando e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="14568-121">Open up a command prompt and type the following:</span></span>

   ```bash
   npm install yo gulp-cli --global
   ```

## <a name="install-the-generator"></a><span data-ttu-id="14568-122">Instalar o gerador</span><span class="sxs-lookup"><span data-stu-id="14568-122">Install the generator</span></span>

<span data-ttu-id="14568-123">Instale o Teams yeoman com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="14568-123">Install the Teams Yeoman generator with the following command:</span></span>

```bash
npm init yo teams
```

<span data-ttu-id="14568-124">Instale a versão de visualização do gerador com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="14568-124">Install the preview version of the generator with the following command:</span></span>

```bash
npm init yo teams@preview
```

## <a name="generate-your-project"></a><span data-ttu-id="14568-125">Gerar seu projeto</span><span class="sxs-lookup"><span data-stu-id="14568-125">Generate your project</span></span>

<span data-ttu-id="14568-126">Esta seção orienta você pelas etapas para gerar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="14568-126">This section walks you through the steps to generate your project.</span></span>

<span data-ttu-id="14568-127">**Para gerar seu projeto**</span><span class="sxs-lookup"><span data-stu-id="14568-127">**To generate your project**</span></span>

1. <span data-ttu-id="14568-128">Abra um prompt de comando e crie um novo diretório onde você deseja criar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="14568-128">Open a command prompt and create a new directory where you want to create your project.</span></span>
1. <span data-ttu-id="14568-129">Vá para o diretório e execute o comando `yo teams` .</span><span class="sxs-lookup"><span data-stu-id="14568-129">Go to the directory, and run the command `yo teams`.</span></span> <span data-ttu-id="14568-130">O gerador é iniciado.</span><span class="sxs-lookup"><span data-stu-id="14568-130">The generator starts.</span></span>
1. <span data-ttu-id="14568-131">Responda ao conjunto de perguntas solicitado pelo gerador:</span><span class="sxs-lookup"><span data-stu-id="14568-131">Respond to the set of questions prompted by the generator:</span></span>

   ![yo teams](~/assets/yeoman-images/teams-first-app-1.png)

   1. <span data-ttu-id="14568-133">Insira um nome para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="14568-133">Enter a name for your project.</span></span> <span data-ttu-id="14568-134">Você pode deixá-lo como está pressionando Enter.</span><span class="sxs-lookup"><span data-stu-id="14568-134">You can leave it as is by pressing Enter.</span></span>
   1. <span data-ttu-id="14568-135">Insira um caminho para o novo diretório se quiser criar um novo diretório.</span><span class="sxs-lookup"><span data-stu-id="14568-135">Enter a path for the new directory if you want to create a new directory.</span></span> <span data-ttu-id="14568-136">Como você já está no diretório que deseja, pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="14568-136">As you are already in the directory you want, just press Enter.</span></span>
   1. <span data-ttu-id="14568-137">Insira o título do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="14568-137">Enter the title of your project.</span></span> <span data-ttu-id="14568-138">Esse título será usado no manifesto e na descrição do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="14568-138">This title will be used in the manifest and description of your app.</span></span> 
   1. <span data-ttu-id="14568-139">Insira um nome da empresa que também será usado no manifesto.</span><span class="sxs-lookup"><span data-stu-id="14568-139">Enter a company name which also will be used in the manifest.</span></span>
   1. <span data-ttu-id="14568-140">Insira a versão do manifesto que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="14568-140">Enter the version of the manifest you want to use.</span></span> <span data-ttu-id="14568-141">Para este tutorial, selecione `v1.5` , que é o esquema disponível geral atual.</span><span class="sxs-lookup"><span data-stu-id="14568-141">For this tutorial select `v1.5`, which is the current general available schema.</span></span>
   1. <span data-ttu-id="14568-142">Selecione os itens que você deseja adicionar ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="14568-142">Select the items you want to add to your project.</span></span> <span data-ttu-id="14568-143">Você pode selecionar um único ou qualquer combinação de itens.</span><span class="sxs-lookup"><span data-stu-id="14568-143">You can select a single one or any combination of items.</span></span> <span data-ttu-id="14568-144">Para este tutorial, basta selecionar *uma guia*:</span><span class="sxs-lookup"><span data-stu-id="14568-144">For this tutorials, just select *a Tab*:</span></span>

    ![seleção de item](~/assets/yeoman-images/teams-first-app-2.png)

1. <span data-ttu-id="14568-146">Responda ao próximo conjunto de perguntas de acompanhamento que aparecem com base nos itens selecionados na Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="14568-146">Respond to the next set of follow-up questions that appear based on the items you selected in Step 2.</span></span>
1. <span data-ttu-id="14568-147">Insira uma URL para o local onde você hospedará sua solução.</span><span class="sxs-lookup"><span data-stu-id="14568-147">Enter a URL for the location where you will host your solution.</span></span> 

   > [!NOTE]
   > <span data-ttu-id="14568-148">A URL pode ser qualquer URL, mas, por padrão, o gerador sugere uma URL do site do Azure.</span><span class="sxs-lookup"><span data-stu-id="14568-148">The URL can be any URL, but by default the generator suggests an Azure web site URL.</span></span>

1. <span data-ttu-id="14568-149">Confirme se você deseja incluir testes de unidade para sua solução.</span><span class="sxs-lookup"><span data-stu-id="14568-149">Confirm if you want to include unit-testing for your solution.</span></span> <span data-ttu-id="14568-150">A resposta padrão é **Sim**.</span><span class="sxs-lookup"><span data-stu-id="14568-150">The default response is **Yes**.</span></span> <span data-ttu-id="14568-151">Se você optar por incluir teste de unidade, o projeto gerado terá uma estrutura de teste de unidade e alguns testes de unidade padrão para os diferentes itens que estão sendo scaffolded.</span><span class="sxs-lookup"><span data-stu-id="14568-151">If you opt to include unit-testing, the generated project will have a unit testing framework and some default unit tests for the different items being scaffolded.</span></span> 
   > [!NOTE]
   > * <span data-ttu-id="14568-152">Para este tutorial, escolha não incluir uma estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="14568-152">For this tutorial choose not to include a test framework.</span></span>
   > * <span data-ttu-id="14568-153">O gerador tem muitos recursos avançados integrados que você pode optar ou não.</span><span class="sxs-lookup"><span data-stu-id="14568-153">The generator has a lot of built-in advanced features that you can opt-in or opt-out of.</span></span>

1. <span data-ttu-id="14568-154">Para facilitar a sua assinatura, você também será perguntado se deseja usar o aplicativo do Azure Insights para entrar.</span><span class="sxs-lookup"><span data-stu-id="14568-154">In order to make signing-in easy for you, you will also be asked if you want to use Azure Application Insights for signing-in.</span></span> <span data-ttu-id="14568-155">Se você selecionar **Sim**, será necessário fornecer uma chave de Insights aplicativo do Azure.</span><span class="sxs-lookup"><span data-stu-id="14568-155">If you select **Yes**, you will need to provide an Azure Application Insights key.</span></span> 

   > [!NOTE]
   > <span data-ttu-id="14568-156">Para este tutorial, opte por usar o aplicativo Insights.</span><span class="sxs-lookup"><span data-stu-id="14568-156">For this tutorial opt-out of using Application Insights.</span></span>

   <span data-ttu-id="14568-157">O próximo conjunto de perguntas será baseado nos itens selecionados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="14568-157">The next set of questions will be based on the previously selected items.</span></span> <span data-ttu-id="14568-158">Para uma guia, você só precisa fornecer um nome e, opcionalmente, escolher se deseja usar esse aplicativo como uma web part SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="14568-158">For a tab you only need to provide a name and optionally choose if you want to be able to use this app as a SharePoint Online web part.</span></span> <span data-ttu-id="14568-159">Depois de fornecer o nome, o gerador gerará o projeto e instalará todas as dependências.</span><span class="sxs-lookup"><span data-stu-id="14568-159">After you provide the name the generator will generate the project and install all dependencies.</span></span> <span data-ttu-id="14568-160">Isso levará um minuto ou dois.</span><span class="sxs-lookup"><span data-stu-id="14568-160">This will take a minute or two.</span></span>

## <a name="add-code-to-your-tab"></a><span data-ttu-id="14568-161">Adicionar código à guia</span><span class="sxs-lookup"><span data-stu-id="14568-161">Add code to your tab</span></span>

<span data-ttu-id="14568-162">Depois que o gerador for feito, você poderá abrir a solução no editor de código favorito.</span><span class="sxs-lookup"><span data-stu-id="14568-162">After the generator is done you can open up the solution in your favorite code editor.</span></span> <span data-ttu-id="14568-163">Tome um minuto ou dois e familiarize-se com como o código é organizado.</span><span class="sxs-lookup"><span data-stu-id="14568-163">Take a minute or two and familiarize yourself with how the code is organized.</span></span> <span data-ttu-id="14568-164">Para obter mais informações, [consulte Project Documentação de](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) estrutura.</span><span class="sxs-lookup"><span data-stu-id="14568-164">For more information, see [Project Structure](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) documentation.</span></span>

<span data-ttu-id="14568-165">Sua guia está no `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` arquivo.</span><span class="sxs-lookup"><span data-stu-id="14568-165">Your tab is in the `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` file.</span></span> <span data-ttu-id="14568-166">Esta é a classe typeScript React baseada em sua guia.</span><span class="sxs-lookup"><span data-stu-id="14568-166">This is the TypeScript React-based class for your tab.</span></span> 

1. <span data-ttu-id="14568-167">Localize `render()` o método e adicione uma linha de código dentro do controle para que ele tenha esta `<PanelBody>` aparência:</span><span class="sxs-lookup"><span data-stu-id="14568-167">Locate the `render()` method and add a line of code inside the `<PanelBody>` control so it looks like this:</span></span>

   ``` TypeScript
   <PanelBody>
      <div style={styles.section}>
      Hello World! Yo Teams rocks!
      </div>
   </PanelBody>
   ```
1. <span data-ttu-id="14568-168">Salve o arquivo e retorne ao prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="14568-168">Save the file and return to the command prompt.</span></span>

## <a name="build-your-app"></a><span data-ttu-id="14568-169">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="14568-169">Build your app</span></span>

<span data-ttu-id="14568-170">Agora você pode criar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="14568-170">You can now build your project.</span></span> <span data-ttu-id="14568-171">Isso é feito em duas etapas.</span><span class="sxs-lookup"><span data-stu-id="14568-171">This is done in two steps.</span></span>

1. <span data-ttu-id="14568-172">Crie o Teams de manifesto do aplicativo para o aplicativo que você carregou no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="14568-172">Create the Teams App manifest file for the app that you uploaded into Microsoft Teams.</span></span> <span data-ttu-id="14568-173">Isso é feito pela tarefa `gulp manifest` Gulp.</span><span class="sxs-lookup"><span data-stu-id="14568-173">This is done by the Gulp task `gulp manifest`.</span></span> <span data-ttu-id="14568-174">Isso validará o manifesto e criará um arquivo zip no `./package` diretório.</span><span class="sxs-lookup"><span data-stu-id="14568-174">This will validate the manifest and create a zip file in the `./package` directory.</span></span>
1. <span data-ttu-id="14568-175">Execute o `gulp build` comando para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="14568-175">Run the `gulp build` command to build the solution.</span></span> <span data-ttu-id="14568-176">Isso transpile sua solução para a `./dist` pasta.</span><span class="sxs-lookup"><span data-stu-id="14568-176">This will transpile your solution into the `./dist` folder.</span></span> 

## <a name="run-your-app"></a><span data-ttu-id="14568-177">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="14568-177">Run your app</span></span>

<span data-ttu-id="14568-178">Para executar seu aplicativo, use o `gulp serve` comando.</span><span class="sxs-lookup"><span data-stu-id="14568-178">To run your app, use the `gulp serve` command.</span></span> <span data-ttu-id="14568-179">Isso criará e iniciará um servidor Web local para você testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="14568-179">This will build and start a local web server for you to test your app.</span></span> <span data-ttu-id="14568-180">O comando também reconstruirá o aplicativo sempre que você salvar um arquivo em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="14568-180">The command will also rebuild the application whenever you save a file in your project.</span></span> 

<span data-ttu-id="14568-181">Agora você deve ir para e `http://localhost:3007/myFirstAppTab/` garantir que sua guia está renderização.</span><span class="sxs-lookup"><span data-stu-id="14568-181">You should now be go to `http://localhost:3007/myFirstAppTab/` and ensure that your tab is rendering.</span></span> <span data-ttu-id="14568-182">No entanto, ainda não Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="14568-182">However, it is not in Microsoft Teams yet.</span></span> 

<span data-ttu-id="14568-183">**Para renderizar sua guia em Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="14568-183">**To render your tab in Microsoft Teams**</span></span>

![exibir seu site em um navegador](~/assets/yeoman-images/teams-first-app-3.png)

### <a name="run-your-app-in-microsoft-teams"></a><span data-ttu-id="14568-185">Execute seu aplicativo em Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="14568-185">Run your app in Microsoft Teams</span></span>

<span data-ttu-id="14568-186">Microsoft Teams permite que você tenha seu aplicativo hospedado no localhost, portanto, você precisa publicá-lo em uma URL pública ou usar um proxy como ngrok.</span><span class="sxs-lookup"><span data-stu-id="14568-186">Microsoft Teams does not allow you to have your app hosted on localhost, so you need to either publish it to a public URL or use a proxy such as ngrok.</span></span> <span data-ttu-id="14568-187">A boa notícia é que o projeto scaffolded tem esse projeto integrado.</span><span class="sxs-lookup"><span data-stu-id="14568-187">Good news is that the scaffolded project has this built-in.</span></span> 

<span data-ttu-id="14568-188">**Para executar seu aplicativo em Teams**</span><span class="sxs-lookup"><span data-stu-id="14568-188">**To run your app in Teams**</span></span>

1. <span data-ttu-id="14568-189">Execute `gulp ngrok-serve` no Terminal.</span><span class="sxs-lookup"><span data-stu-id="14568-189">Run `gulp ngrok-serve` in Terminal.</span></span> <span data-ttu-id="14568-190">Quando você executar o serviço ngrok será iniciado em segundo plano, com uma entrada DNS pública e exclusiva e ele também empacota o manifesto com essa URL exclusiva e, em seguida, fará exatamente a mesma coisa `gulp ngrok-serve` que `gulp serve` .</span><span class="sxs-lookup"><span data-stu-id="14568-190">When you run `gulp ngrok-serve` the ngrok service will be started in the background, with a unique and public DNS entry and it will also package the manifest with that unique URL and then do the exact same thing as `gulp serve`.</span></span>
1. <span data-ttu-id="14568-191">Crie uma nova Microsoft Teams equipe.</span><span class="sxs-lookup"><span data-stu-id="14568-191">Create a new Microsoft Teams team.</span></span>
1. <span data-ttu-id="14568-192">Selecione o nome da equipe > Teams Configurações > Aplicativos.</span><span class="sxs-lookup"><span data-stu-id="14568-192">Select the Team name > Teams Settings > Apps.</span></span>
1. <span data-ttu-id="14568-193">No canto inferior direito, selecione **Upload um aplicativo personalizado.**</span><span class="sxs-lookup"><span data-stu-id="14568-193">From the lower right corner, select **Upload a custom app**.</span></span>
1. <span data-ttu-id="14568-194">Vá para a `package` pasta em sua pasta de projeto.</span><span class="sxs-lookup"><span data-stu-id="14568-194">Go to the `package` folder under your project folder.</span></span> 
1. <span data-ttu-id="14568-195">Selecione o arquivo zip nessa pasta e selecione abrir.</span><span class="sxs-lookup"><span data-stu-id="14568-195">Select the zip file in that folder and select open.</span></span> 
   <span data-ttu-id="14568-196">Seu aplicativo agora é sideload em Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="14568-196">Your App is now sideloaded into Microsoft Teams:</span></span>

   ![aplicativo sideloaded](~/assets/yeoman-images/teams-first-app-4.png)
1. <span data-ttu-id="14568-198">Volte para o **canal Geral** e selecione para adicionar uma **+** nova Guia. Você deve ver sua guia na lista de guias: ![ configurar guia](~/assets/yeoman-images/teams-first-app-5.png)</span><span class="sxs-lookup"><span data-stu-id="14568-198">Go back to the **General** channel and select **+** to add a new Tab. You should see your tab in the list of tabs: ![configure tab](~/assets/yeoman-images/teams-first-app-5.png)</span></span>
1. <span data-ttu-id="14568-199">Selecione sua guia e siga as instruções para adicioná-la.</span><span class="sxs-lookup"><span data-stu-id="14568-199">Select your tab and follow the instructions to add it.</span></span> <span data-ttu-id="14568-200">Observe que você tem uma caixa de diálogo de configuração personalizada, para a qual você pode editar a origem.</span><span class="sxs-lookup"><span data-stu-id="14568-200">Notice that you have a custom configuration dialog, for which you can edit the source.</span></span> <span data-ttu-id="14568-201">Selecione *Salvar* para adicionar sua guia ao canal.</span><span class="sxs-lookup"><span data-stu-id="14568-201">Select *Save* to add your tab to the channel.</span></span> <span data-ttu-id="14568-202">Sua guia agora é carregada dentro Microsoft Teams!</span><span class="sxs-lookup"><span data-stu-id="14568-202">Your tab is now loaded inside Microsoft Teams!</span></span>

   ![guia de execução em equipes](~/assets/yeoman-images/teams-first-app-6.png)

### <a name="upgrade-microsoft-teams"></a><span data-ttu-id="14568-204">Atualizar Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="14568-204">Upgrade Microsoft Teams</span></span>

<span data-ttu-id="14568-205">Você também pode atualizar sua versão Microsoft Teams atual para a versão mais recente usando o Microsoft Teams gerador Yeoman.</span><span class="sxs-lookup"><span data-stu-id="14568-205">You can also upgrade your current Microsoft Teams version to the latest version using the Microsoft Teams Yeoman generator.</span></span>

<span data-ttu-id="14568-206">**Para atualizar Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="14568-206">**To upgrade Microsoft Teams**</span></span>

1. <span data-ttu-id="14568-207">Obter a versão atual do Teams com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="14568-207">Get current version of Teams with the following command:</span></span>

   ```PowerShell
    yo teams --version
   ```
2. <span data-ttu-id="14568-208">Use o seguinte comando para selecionar e atualizar seu gerador:</span><span class="sxs-lookup"><span data-stu-id="14568-208">Use the following command to select and update your generator:</span></span>

   ```PowerShell
    yo
   ```
3. <span data-ttu-id="14568-209">Use as teclas de seta para selecionar **Atualizar seus Geradores**:</span><span class="sxs-lookup"><span data-stu-id="14568-209">Use the  arrow keys to select **Update your Generators**:</span></span>

   ![imagem de YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

4. <span data-ttu-id="14568-211">Selecione o gerador que você deseja na lista de geradores:</span><span class="sxs-lookup"><span data-stu-id="14568-211">Select the generator you want from the list of generators:</span></span>
   > [!NOTE]
   > <span data-ttu-id="14568-212">Use a barra de espaços para selecionar ou limpar uma versão Teams selecionada das opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="14568-212">Use the space bar to select or clear a selected Teams version from the available options.</span></span>

    ![imagem de UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)
    

   > [!NOTE]
   > <span data-ttu-id="14568-214">Leva alguns segundos para que a instalação Teams seja concluída.</span><span class="sxs-lookup"><span data-stu-id="14568-214">It takes few seconds to minutes for Teams installation to complete.</span></span>

5. <span data-ttu-id="14568-215">Depois que a instalação for concluída, use o seguinte comando para verificar a versão instalada:</span><span class="sxs-lookup"><span data-stu-id="14568-215">After the installation is complete, use the following command to check the installed version:</span></span>

   ```PowerShell
    yo teams --version
   ```
   <span data-ttu-id="14568-216">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="14568-216">Congrats!</span></span> <span data-ttu-id="14568-217">Você criou e implantou seu primeiro Microsoft Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="14568-217">You built and deployed your first Microsoft Teams app.</span></span> <span data-ttu-id="14568-218">Você também atualizou Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="14568-218">You also upgraded Microsoft Teams.</span></span>

 ## <a name="see-also"></a><span data-ttu-id="14568-219">Confira também</span><span class="sxs-lookup"><span data-stu-id="14568-219">See also</span></span>

* [<span data-ttu-id="14568-220">Visão geral dos tutoriais</span><span class="sxs-lookup"><span data-stu-id="14568-220">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="14568-221">Criar um programa bot de conversação</span><span class="sxs-lookup"><span data-stu-id="14568-221">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="14568-222">Criar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="14568-222">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="14568-223">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="14568-223">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)