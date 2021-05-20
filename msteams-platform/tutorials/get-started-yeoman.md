---
title: Tutorial - Crie seu primeiro aplicativo usando o gerador Yeoman
description: Saiba como começar a construir aplicativos Microsoft Teams com o gerador Yeoman.
keywords: começando node.js nodejs yeoman
localization_priority: Normal
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: 96a4f64d487e1d16bf25abd978759fedeac1061c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566821"
---
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a><span data-ttu-id="3dd2c-104">Crie seu primeiro aplicativo de Microsoft Teams usando o gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="3dd2c-104">Create your first Microsoft Teams app using the Yeoman generator</span></span>

> [!Note]
> <span data-ttu-id="3dd2c-105">Este tutorial vem do [gerador Yeoman para Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span><span class="sxs-lookup"><span data-stu-id="3dd2c-105">This tutorial comes from the [Yeoman generator for Teams wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span>

<span data-ttu-id="3dd2c-106">Neste tutorial, vamos percorrer a criação do seu primeiro aplicativo Microsoft Teams usando o gerador Microsoft Teams Yeoman.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-106">In this tutorial, we will walk through creating your very first Microsoft Teams app using the Microsoft Teams Yeoman generator.</span></span> <span data-ttu-id="3dd2c-107">Ele também o acompanha no processo de atualizar seu Teams usando o gerador Yeoman.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-107">It also walks you through the process of upgrading your Teams using the Yeoman generator.</span></span> <span data-ttu-id="3dd2c-108">O pré-requisito para começar com este tutorial é que você tenha uma conta Teams que permite [o sideloading do aplicativo](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="3dd2c-108">The prerequisite to start with this tutorial is that you have a Teams account that allows [app sideloading](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

![yeoman gerador git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a><span data-ttu-id="3dd2c-110">Configure e prepare sua máquina</span><span class="sxs-lookup"><span data-stu-id="3dd2c-110">Setup and prepare your machine</span></span>

<span data-ttu-id="3dd2c-111">Você precisa instalar o seguinte em sua máquina antes de começar a usar o gerador Yeoman.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-111">You need to install the following on your machine before starting to use the Yeoman generator.</span></span>

### <a name="install-nodejs"></a><span data-ttu-id="3dd2c-112">Instale o Node.js.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-112">Install Node.js</span></span>

<span data-ttu-id="3dd2c-113">Você precisa ter Node.js instalado em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-113">You need to have Node.js installed on your machine.</span></span> <span data-ttu-id="3dd2c-114">Você deve usar a [versão LTS](https://nodejs.org)mais recente .</span><span class="sxs-lookup"><span data-stu-id="3dd2c-114">You should use the latest [LTS version](https://nodejs.org).</span></span>

### <a name="install-a-code-editor"></a><span data-ttu-id="3dd2c-115">Instalar um editor de códigos</span><span class="sxs-lookup"><span data-stu-id="3dd2c-115">Install a code editor</span></span>

<span data-ttu-id="3dd2c-116">Você precisa de um editor de código.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-116">You need a code editor.</span></span> <span data-ttu-id="3dd2c-117">A maioria desta documentação e imagens referem-se ao uso [de Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="3dd2c-117">Most of this documentation and images refer to using [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="3dd2c-118">No entanto, sinta-se livre para usar qualquer editor de texto que você preferir.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-118">However, feel free to use whatever text editor you prefer.</span></span>

### <a name="install-yeoman-and-gulp-cli"></a><span data-ttu-id="3dd2c-119">Instale Yeoman e Gulp CLI</span><span class="sxs-lookup"><span data-stu-id="3dd2c-119">Install Yeoman and Gulp CLI</span></span>

<span data-ttu-id="3dd2c-120">Para projetos de andaimes usando o gerador, você deve instalar a ferramenta Yeoman e o gerente de tarefas Gulp CLI.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-120">To scaffold projects using the generator, you must install the Yeoman tool and Gulp CLI task manager.</span></span>

<span data-ttu-id="3dd2c-121">Abra um prompt de comando e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-121">Open up a command prompt and type the following:</span></span>

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-generator"></a><span data-ttu-id="3dd2c-122">Instale o gerador</span><span class="sxs-lookup"><span data-stu-id="3dd2c-122">Install the generator</span></span>

<span data-ttu-id="3dd2c-123">Instale o gerador yeoman Teams com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-123">Install the Teams Yeoman generator with the following command:</span></span>

```bash
npm install generator-teams --global
```

<span data-ttu-id="3dd2c-124">Instale a versão de visualização do gerador com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-124">Install the preview version of the generator with the following command:</span></span>

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a><span data-ttu-id="3dd2c-125">Gere seu projeto</span><span class="sxs-lookup"><span data-stu-id="3dd2c-125">Generate your project</span></span>

<span data-ttu-id="3dd2c-126">Esta seção o percorre as etapas para gerar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-126">This section walks you through the steps for generating your project.</span></span>

<span data-ttu-id="3dd2c-127">**Para gerar seu projeto**</span><span class="sxs-lookup"><span data-stu-id="3dd2c-127">**To generate your project**</span></span>

1. <span data-ttu-id="3dd2c-128">Abra um prompt de comando e crie um novo diretório onde você deseja criar seu projeto, e nesse diretório execute o comando `yo teams` .</span><span class="sxs-lookup"><span data-stu-id="3dd2c-128">Open up a command prompt and create a new directory where you want to create your project, and in that directory run the command `yo teams`.</span></span> <span data-ttu-id="3dd2c-129">O gerador começa.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-129">The generator starts.</span></span>
1. <span data-ttu-id="3dd2c-130">Responda ao conjunto de perguntas solicitadas pelo gerador:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-130">Respond to the set of questions prompted by the generator:</span></span>

   ![yo equipes](~/assets/yeoman-images/teams-first-app-1.png)

   1. <span data-ttu-id="3dd2c-132">A primeira pergunta é sobre o nome do seu projeto, você pode deixá-lo como está pressionando enter.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-132">The first question is about your project name, you can leave it as is by pressing enter.</span></span>
   1. <span data-ttu-id="3dd2c-133">A próxima pergunta pergunta se você deseja criar um novo diretório ou usar o atual.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-133">Next question asks you if you want to create a new directory or use the current one.</span></span> <span data-ttu-id="3dd2c-134">Como você já está no diretório que você quer, basta pressionar enter.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-134">As you are already in the directory you want, just press enter.</span></span>
   1. <span data-ttu-id="3dd2c-135">Na próxima pergunta, digite o título do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-135">In the next question, type the title of your project.</span></span> <span data-ttu-id="3dd2c-136">Este título será usado no manifesto e descrição do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-136">This title will be used in the manifest and description of your app.</span></span> 
   1. <span data-ttu-id="3dd2c-137">Em seguida, será solicitado um nome da empresa, que também será usado no manifesto.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-137">Next, you will be asked for a company name, which also will be used in the manifest.</span></span>
   1. <span data-ttu-id="3dd2c-138">A quinta pergunta pergunta sobre qual versão do manifesto você quer usar.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-138">The fifth question asks you about what version of the manifest you want to use.</span></span> <span data-ttu-id="3dd2c-139">Para este tutorial selecione `v1.5` , que é o esquema geral disponível atual.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-139">For this tutorial select `v1.5`, which is the current general available schema.</span></span>
   1. <span data-ttu-id="3dd2c-140">Em seguida, o gerador perguntará quais itens você deseja adicionar ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-140">Next, the generator will ask you for what items you want to add to your project.</span></span> <span data-ttu-id="3dd2c-141">Você pode selecionar uma única ou qualquer combinação de itens.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-141">You can select a single one or any combination of items.</span></span> <span data-ttu-id="3dd2c-142">Para este tutorial, basta selecionar *uma guia*:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-142">For this tutorials, just select *a Tab*:</span></span>

    ![seleção de itens](~/assets/yeoman-images/teams-first-app-2.png)

1. <span data-ttu-id="3dd2c-144">Responda ao próximo conjunto de perguntas de acompanhamento que aparecem com base nos itens selecionados na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-144">Respond to the next set of follow-up questions that appear based on the items you selected in step 2.</span></span>
1. <span data-ttu-id="3dd2c-145">Digite uma URL de onde você hospedará sua solução.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-145">Enter a URL of where you will host your solution.</span></span> 

   > [!NOTE]
   > <span data-ttu-id="3dd2c-146">A URL pode ser qualquer URL, mas por padrão o gerador sugere uma URL do site do Azure.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-146">The URL can be any URL, but by default the generator suggests an Azure web site URL.</span></span>

1. <span data-ttu-id="3dd2c-147">Na próxima pergunta, confirme se você deseja incluir testes unitários para sua solução.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-147">In the next question, confirm if you want to include unit-testing for your solution.</span></span> <span data-ttu-id="3dd2c-148">A resposta padrão é *sim*.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-148">The default response is *yes*.</span></span> <span data-ttu-id="3dd2c-149">Se você optar por incluir testes unitários, o projeto gerado terá uma estrutura de teste de unidade e alguns testes de unidade padrão para os diferentes itens que estão sendo andaimes.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-149">If you choose to include unit-testing, the generated project will have a unit testing framework and some default unit tests for the different items being scaffolded.</span></span> 
   > [!NOTE]
   > * <span data-ttu-id="3dd2c-150">Para este tutorial, opte por não incluir uma estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-150">For this tutorial choose not to include a test framework.</span></span>
   > * <span data-ttu-id="3dd2c-151">O gerador tem um monte de recursos avançados incorporados que você pode optar ou optar por não participar.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-151">The generator has a lot of built-in advanced features that you can opt-in or opt-out of.</span></span>

1. <span data-ttu-id="3dd2c-152">A fim de facilitar a assinatura para você, você também será perguntado se você quer usar o Azure Application Insights para fazer login.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-152">In order to make signing-in easy for you, you will also be asked if you want to use Azure Application Insights for signing-in.</span></span> <span data-ttu-id="3dd2c-153">Se você escolher *Sim,* você precisará fornecer uma chave de Insights de Aplicativos Azure.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-153">If you choose *Yes*, you will need to provide an Azure Application Insights key.</span></span> 

   > [!NOTE]
   > <span data-ttu-id="3dd2c-154">Para este tutorial opt-out de usar o Application Insights.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-154">For this tutorial opt-out of using Application Insights.</span></span>

<span data-ttu-id="3dd2c-155">O próximo conjunto de perguntas será baseado nos itens selecionados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-155">The next set of questions will be based on the previously selected items.</span></span> <span data-ttu-id="3dd2c-156">Para uma guia, você só precisa fornecer um nome e, opcionalmente, escolher se você quiser ser capaz de usar este aplicativo como uma SharePoint parte da Web Online.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-156">For a tab you only need to provide a name and optionally choose if you want to be able to use this app as a SharePoint Online web part.</span></span> <span data-ttu-id="3dd2c-157">Depois de fornecer o nome, o gerador irá gerar o projeto e instalar todas as dependências.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-157">After you provide the name the generator will generate the project and install all dependencies.</span></span> <span data-ttu-id="3dd2c-158">Isso vai levar um minuto ou dois.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-158">This will take a minute or two.</span></span>

## <a name="add-some-code-to-your-tab"></a><span data-ttu-id="3dd2c-159">Adicione algum código à sua guia</span><span class="sxs-lookup"><span data-stu-id="3dd2c-159">Add some code to your tab</span></span>

<span data-ttu-id="3dd2c-160">Depois que o gerador estiver pronto, você pode abrir a solução no seu editor de código favorito.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-160">After the generator is done you can open up the solution in your favorite code editor.</span></span> <span data-ttu-id="3dd2c-161">Tire um minuto ou dois e familiarize-se com a forma como o código é organizado.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-161">Take a minute or two and familiarize yourself with how the code is organized.</span></span> <span data-ttu-id="3dd2c-162">Para obter mais informações, consulte [Project documentação da Estrutura.](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure)</span><span class="sxs-lookup"><span data-stu-id="3dd2c-162">For more information, see [Project Structure](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) documentation.</span></span>

<span data-ttu-id="3dd2c-163">Sua guia está no `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` arquivo.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-163">Your tab is in the `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` file.</span></span> <span data-ttu-id="3dd2c-164">Esta é a classe TypeScript React para sua guia. Localize o `render()` método e adicione uma linha de código dentro do controle para que ele se pareça com `<PanelBody>` este:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-164">This is the TypeScript React-based class for your tab. Locate the `render()` method and add a line of code inside the `<PanelBody>` control so it looks like this:</span></span>

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

<span data-ttu-id="3dd2c-165">Salve o arquivo e retorne ao prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-165">Save the file and return to the command prompt.</span></span>

## <a name="build-your-app"></a><span data-ttu-id="3dd2c-166">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3dd2c-166">Build your app</span></span>

<span data-ttu-id="3dd2c-167">Agora você pode construir seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-167">You can now build your project.</span></span> <span data-ttu-id="3dd2c-168">Isso é feito em duas etapas (ou um passo, veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="3dd2c-168">This is done in two steps (or one step, see below).</span></span>

<span data-ttu-id="3dd2c-169">Primeiro você precisa criar o arquivo manifesto do aplicativo Teams, que você carrega/sideload em Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-169">First you need to create the Teams App manifest file, that you upload/sideload into Microsoft Teams.</span></span> <span data-ttu-id="3dd2c-170">Isso é feito pela tarefa `gulp manifest` Gulp.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-170">This is done by the Gulp task `gulp manifest`.</span></span> <span data-ttu-id="3dd2c-171">Isso validará o manifesto e criará um arquivo zip no `./package` diretório.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-171">This will validate the manifest and create a zip file in the `./package` directory.</span></span>

<span data-ttu-id="3dd2c-172">Para construir sua solução, você usa o `gulp build` comando.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-172">To build your solution you use the `gulp build` command.</span></span> <span data-ttu-id="3dd2c-173">Isso transpilará sua solução para a `./dist` pasta.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-173">This will transpile your solution into the `./dist` folder.</span></span> 

## <a name="run-your-app"></a><span data-ttu-id="3dd2c-174">Execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3dd2c-174">Run your app</span></span>

<span data-ttu-id="3dd2c-175">Para executar seu aplicativo, você usa o `gulp serve` comando.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-175">To run your app you use the `gulp serve` command.</span></span> <span data-ttu-id="3dd2c-176">Isso irá construir e iniciar um servidor web local para você testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-176">This will build and start a local web server for you to test your app.</span></span> <span data-ttu-id="3dd2c-177">O comando também reconstruirá o aplicativo sempre que você salvar um arquivo em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-177">The command will also rebuild the application whenever you save a file in your project.</span></span> 

<span data-ttu-id="3dd2c-178">Agora você deve ser capaz de navegar `http://localhost:3007/myFirstAppTab/` para garantir que sua guia esteja renderizando.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-178">You should now be able to browse to `http://localhost:3007/myFirstAppTab/` to ensure that your tab is rendering.</span></span> <span data-ttu-id="3dd2c-179">No entanto, ainda não Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-179">However, not in Microsoft Teams yet:</span></span>

![exibir seu site em um navegador](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a><span data-ttu-id="3dd2c-181">Execute seu aplicativo em Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3dd2c-181">Run your app in Microsoft Teams</span></span>

<span data-ttu-id="3dd2c-182">Microsoft Teams não permite que você tenha seu aplicativo hospedado no site local, então você precisa publicá-lo em uma URL pública ou usar um proxy como ngrok.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-182">Microsoft Teams does not allow you to have your app hosted on localhost, so you need to either publish it to a public URL or use a proxy such as ngrok.</span></span>

<span data-ttu-id="3dd2c-183">A boa notícia é que o projeto do andaime tem esse embutido.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-183">Good news is that the scaffolded project has this built-in.</span></span> <span data-ttu-id="3dd2c-184">Quando você executar `gulp ngrok-serve` o serviço ngrok será iniciado em segundo plano, com uma entrada DNS única e pública e também embalará o manifesto com essa URL única e, em seguida, fará exatamente a mesma coisa que `gulp serve` .</span><span class="sxs-lookup"><span data-stu-id="3dd2c-184">When you run `gulp ngrok-serve` the ngrok service will be started in the background, with a unique and public DNS entry and it will also package the manifest with that unique URL and then do the exact same thing as `gulp serve`.</span></span>

<span data-ttu-id="3dd2c-185">Depois de `gulp ngrok-serve` executar, crie uma nova equipe de Microsoft Teams e quando for criada clique no nome da Equipe, para ir às configurações das equipes e, em seguida, selecionar *Aplicativos*.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-185">After running `gulp ngrok-serve`, create a new Microsoft Teams team and when it is created click on the Team name, to go to the teams settings and then select *Apps*.</span></span> <span data-ttu-id="3dd2c-186">No canto inferior direito, você deve ver um link *Upload um aplicativo personalizado,* selecione-o e, em seguida, navegue até a pasta do projeto e a subpasta chamada `package` .</span><span class="sxs-lookup"><span data-stu-id="3dd2c-186">In the lower right corner you should see a link *Upload a custom app*, select it and then browse to your project folder and the subfolder called `package`.</span></span> <span data-ttu-id="3dd2c-187">Selecione o arquivo zip nessa pasta e escolha abrir.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-187">Select the zip file in that folder and choose open.</span></span> <span data-ttu-id="3dd2c-188">Seu aplicativo está agora carregado de lado para Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-188">Your App is now sideloaded into Microsoft Teams:</span></span>

![aplicativo sideloaded](~/assets/yeoman-images/teams-first-app-4.png)

<span data-ttu-id="3dd2c-190">Volte para o canal *Geral* e selecione *+* adicionar uma nova Guia. Você deve ver sua guia na lista de guias:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-190">Go back to the *General* channel and select *+* to add a new Tab. You should see your tab in the list of tabs:</span></span>

![configurar aba](~/assets/yeoman-images/teams-first-app-5.png)

<span data-ttu-id="3dd2c-192">Escolha sua guia e siga as instruções para adicioná-la.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-192">Choose your tab and follow the instructions to add it.</span></span> <span data-ttu-id="3dd2c-193">Observe que você tem uma caixa de diálogo de configuração personalizada, para a qual você pode editar a fonte.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-193">Notice that you have a custom configuration dialog, for which you can edit the source.</span></span> <span data-ttu-id="3dd2c-194">Selecione *Salvar* para adicionar sua guia ao canal.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-194">Select *Save* to add your tab to the channel.</span></span> <span data-ttu-id="3dd2c-195">Uma vez feita sua guia deve ser carregada dentro Microsoft Teams!</span><span class="sxs-lookup"><span data-stu-id="3dd2c-195">Once done your tab should be loaded inside Microsoft Teams!</span></span>

![guia de execução em equipes](~/assets/yeoman-images/teams-first-app-6.png)

## <a name="upgrade-microsoft-teams"></a><span data-ttu-id="3dd2c-197">Microsoft Teams de upgrade</span><span class="sxs-lookup"><span data-stu-id="3dd2c-197">Upgrade Microsoft Teams</span></span>

<span data-ttu-id="3dd2c-198">Você também pode atualizar sua versão atual Microsoft Teams para a versão mais recente usando o gerador Microsoft Teams Yeoman.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-198">You can also upgrade your current Microsoft Teams version to the latest version using the Microsoft Teams Yeoman generator.</span></span>

<span data-ttu-id="3dd2c-199">**Para atualizar Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="3dd2c-199">**To upgrade Microsoft Teams**</span></span>

1. <span data-ttu-id="3dd2c-200">Obtenha a versão atual de Teams com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-200">Get current version of Teams with the following command:</span></span>

   ```PowerShell
    yo teams --version
   ```
2. <span data-ttu-id="3dd2c-201">Use o seguinte comando para selecionar atualizar seu gerador:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-201">Use the following command to select update your generator:</span></span>

   ```PowerShell
    yo
   ```
3. <span data-ttu-id="3dd2c-202">Use as teclas de seta para escolher **Atualizar seus geradores:**</span><span class="sxs-lookup"><span data-stu-id="3dd2c-202">Use the  arrow keys to choose **Update your Generators**:</span></span>

   ![imagem de YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

4. <span data-ttu-id="3dd2c-204">Selecione o gerador que deseja na lista de geradores:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-204">Select the generator you want from the list of generators:</span></span>
   > [!NOTE]
   > <span data-ttu-id="3dd2c-205">Use a barra de espaço para selecionar ou limpar uma versão Teams selecionada das opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-205">Use the space bar to select or clear a selected Teams version from the available options.</span></span>

    ![imagem do UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)
    

   > [!NOTE]
   > <span data-ttu-id="3dd2c-207">Leva alguns segundos a minutos para Teams instalação ser concluída.</span><span class="sxs-lookup"><span data-stu-id="3dd2c-207">It takes few seconds to minutes for Teams installation to complete.</span></span>

5. <span data-ttu-id="3dd2c-208">Após a instalação ser concluída, use o seguinte comando para verificar a versão instalada:</span><span class="sxs-lookup"><span data-stu-id="3dd2c-208">After the installation is complete, use the following command to check the installed version:</span></span>

   ```PowerShell
    yo teams --version
   ```
   
<span data-ttu-id="3dd2c-209">**Parabéns! Você construiu e implantou seu primeiro aplicativo de Microsoft Teams. Você também atualizou Microsoft Teams.**</span><span class="sxs-lookup"><span data-stu-id="3dd2c-209">**Congrats! You built and deployed your first Microsoft Teams app. You also upgraded Microsoft Teams.**</span></span>
