---
title: 'Início rápido: crie uma guia pessoal personalizada com Node.js e o Gerador Yeoman para Microsoft Teams'
author: laujan
description: Um guia de início rápido para criar uma guia pessoal com o Gerador Yeoman para Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 88ad05aacaed69d695bc918e3e8a44ec18e560ae
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566597"
---
# <a name="create-a-custom-personal-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="d28d4-103">Crie uma guia pessoal personalizada usando Node.js e o Gerador Yeoman para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d28d4-103">Create a custom personal tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="d28d4-104">Esse início rápido segue as etapas descritas no [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki encontrado no repositório do Microsoft OfficeDev GitHub.</span><span class="sxs-lookup"><span data-stu-id="d28d4-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="d28d4-105">Neste início rápido, vamos passo a passo criando uma guia pessoal personalizada usando o gerador [Yeoman Teams yeoman](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span><span class="sxs-lookup"><span data-stu-id="d28d4-105">In this quickstart we'll walk-through creating a custom personal tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span> <span data-ttu-id="d28d4-106">Também carregaremos o aplicativo para a Equipe.</span><span class="sxs-lookup"><span data-stu-id="d28d4-106">We'll also upload the application to Team.</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="d28d4-107">**Criar uma guia configurável ou estática**</span><span class="sxs-lookup"><span data-stu-id="d28d4-107">**Create a configurable or static tab**</span></span>

<span data-ttu-id="d28d4-108">Use as teclas de seta para selecionar a guia estática.</span><span class="sxs-lookup"><span data-stu-id="d28d4-108">Use the arrow keys to select static tab.</span></span>

>[!IMPORTANT]
><span data-ttu-id="d28d4-109">O componente de *caminho que seuDefaultTabNameTab*, referenciado neste início rápido, é o valor que você inscrevia no gerador para *Nome* da Guia Padrão mais a *palavra Tab*.</span><span class="sxs-lookup"><span data-stu-id="d28d4-109">The path component *yourDefaultTabNameTab*, referenced in this quickstart, is the value that you entered in the generator for *Default Tab Name* plus the word *Tab*.</span></span>
>
><span data-ttu-id="d28d4-110">Por exemplo: DefaultTabName: *MyTab*  =>  */MyTabTab/*</span><span class="sxs-lookup"><span data-stu-id="d28d4-110">For example: DefaultTabName: *MyTab* => */MyTabTab/*</span></span>

## <a name="create-your-personal-tab"></a><span data-ttu-id="d28d4-111">Criar sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="d28d4-111">Create your personal tab</span></span>

<span data-ttu-id="d28d4-112">Para adicionar uma guia pessoal a esse aplicativo, você criará uma página de conteúdo e atualizará arquivos existentes:</span><span class="sxs-lookup"><span data-stu-id="d28d4-112">To add a personal tab to this application you'll create a content page and update existing files:</span></span>

- <span data-ttu-id="d28d4-113">No editor de código, crie um novo arquivo HTML, **personal.html** e adicione a seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="d28d4-113">In your code editor, create a new HTML file, **personal.html** and add the following markup:</span></span>

    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8">
            <title>
                <!-- Todo: add your a title here -->
            </title>
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <!-- inject:css -->
            <!-- endinject -->
        </head>
            <body>
                <h1>Personal Tab</h1>
                <p><img src="/assets/icon.png"></p>
                <p>This is your personal tab!</p>
            </body>
    </html>
    ```

- <span data-ttu-id="d28d4-114">Salve **personal.html** na pasta web do **aplicativo:**</span><span class="sxs-lookup"><span data-stu-id="d28d4-114">Save **personal.html** in your application's **web** folder:</span></span>

    ```bash
    ./src/app/web/<yourDefaultTabNameTab>/personal.html
    ```

- <span data-ttu-id="d28d4-115">Abra **manifest.jsno** editor de código:</span><span class="sxs-lookup"><span data-stu-id="d28d4-115">Open **manifest.json** in your code editor:</span></span>

    ```bash
    ./src/manifest/manifest.json/
    ```

<span data-ttu-id="d28d4-116">Adicione o seguinte à matriz `staticTabs` vazia ( ) e adicione o seguinte objeto `staticTabs":[]` JSON:</span><span class="sxs-lookup"><span data-stu-id="d28d4-116">Add the following to the empty `staticTabs` array (`staticTabs":[]`) and add the following JSON object:</span></span>

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

<span data-ttu-id="d28d4-117">Lembre-se de atualizar o componente de caminho **"contentURL"** **yourDefaultTabNameTab** com o nome da guia real.</span><span class="sxs-lookup"><span data-stu-id="d28d4-117">Remember to update the **"contentURL"** path component **yourDefaultTabNameTab** with your actual tab name.</span></span>

- <span data-ttu-id="d28d4-118">Salve omanifest.js **atualizado em**.</span><span class="sxs-lookup"><span data-stu-id="d28d4-118">Save the updated **manifest.json**.</span></span>

- <span data-ttu-id="d28d4-119">Sua página de conteúdo deve ser atendida em um IFrame.</span><span class="sxs-lookup"><span data-stu-id="d28d4-119">Your content page must be served in an IFrame.</span></span> <span data-ttu-id="d28d4-120">Abra **Tab.ts no** editor de código:</span><span class="sxs-lookup"><span data-stu-id="d28d4-120">Open **Tab.ts** in your code editor:</span></span>

    ```bash
    ./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

- <span data-ttu-id="d28d4-121">Adicione o seguinte à lista de decoradores IFrame:</span><span class="sxs-lookup"><span data-stu-id="d28d4-121">Add the following to the list of IFrame decorators:</span></span>

    ```typescript
     @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
    ```

- <span data-ttu-id="d28d4-122">Salve o arquivo **Tab.ts** atualizado.</span><span class="sxs-lookup"><span data-stu-id="d28d4-122">Make sure to save the updated **Tab.ts** file.</span></span> <span data-ttu-id="d28d4-123">Seu código de tabulação está completo.</span><span class="sxs-lookup"><span data-stu-id="d28d4-123">Your tab code is complete.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="d28d4-124">Criar e executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d28d4-124">Build and Run Your Application</span></span>

<span data-ttu-id="d28d4-125">Abra um prompt de comando no diretório do projeto para concluir as próximas tarefas.</span><span class="sxs-lookup"><span data-stu-id="d28d4-125">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="d28d4-126">Para exibir sua guia pessoal, vá para `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span><span class="sxs-lookup"><span data-stu-id="d28d4-126">To view your personal tab, go to `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span></span>

>![captura de tela de guia pessoal](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="d28d4-128">Estabelecer um túnel seguro para sua guia</span><span class="sxs-lookup"><span data-stu-id="d28d4-128">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="d28d4-129">Microsoft Teams é um produto totalmente baseado em nuvem e exige que o conteúdo da guia seja disponibilizado na nuvem usando pontos de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d28d4-129">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="d28d4-130">Teams não permite a hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exponha sua porta local a uma URL voltada para a Internet.</span><span class="sxs-lookup"><span data-stu-id="d28d4-130">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="d28d4-131">Para testar sua extensão de tabulação, você usará [ngrok](https://ngrok.com/docs), que é integrado a esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d28d4-131">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="d28d4-132">O Ngrok é uma ferramenta de software de proxy reverso que criará um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="d28d4-132">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="d28d4-133">Os pontos de extremidade da Web do seu servidor estarão disponíveis durante a sessão atual no computador local.</span><span class="sxs-lookup"><span data-stu-id="d28d4-133">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="d28d4-134">Quando o computador é desligado ou vai para o sono, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="d28d4-134">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="d28d4-135">No prompt de comando, saia do localhost e insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d28d4-135">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="d28d4-136">Depois que sua guia for carregada para o Microsoft Teams, por meio do **ngrok** e salva com êxito, você poderá exibi-la no Teams até que a sessão de túnel termine.</span><span class="sxs-lookup"><span data-stu-id="d28d4-136">After your tab has been uploaded to Microsoft teams, via **ngrok**, and successfully saved, you can view it in Teams until your tunnel session ends.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="d28d4-137">Upload seu aplicativo para Teams</span><span class="sxs-lookup"><span data-stu-id="d28d4-137">Upload your application to Teams</span></span>

- <span data-ttu-id="d28d4-138">Abra o Microsoft Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="d28d4-138">Open the Microsoft Teams client.</span></span> <span data-ttu-id="d28d4-139">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="d28d4-139">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="d28d4-140">No painel **YourTeams** à esquerda, selecione o menu ao lado da equipe que você está usando para testar sua guia e `...` escolha Gerenciar **equipe**.</span><span class="sxs-lookup"><span data-stu-id="d28d4-140">In the **YourTeams** panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="d28d4-141">No painel principal, selecione **Aplicativos** **na** barra de guias e escolha Upload um aplicativo personalizado localizado no canto inferior direito da página.</span><span class="sxs-lookup"><span data-stu-id="d28d4-141">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="d28d4-142">Abra o diretório do projeto, navegue até a pasta **./package,** selecione a pasta zip, clique com o botão direito do mouse e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="d28d4-142">Open your project directory, browse to the **./package** folder, select the zip folder, right-click, and choose **Open**.</span></span> <span data-ttu-id="d28d4-143">Sua guia será carregada no Teams.</span><span class="sxs-lookup"><span data-stu-id="d28d4-143">Your tab will upload into Teams.</span></span>

## <a name="view-your-personal-tabs"></a><span data-ttu-id="d28d4-144">Exibir suas guias pessoais</span><span class="sxs-lookup"><span data-stu-id="d28d4-144">View your personal tabs</span></span>

<span data-ttu-id="d28d4-145">Na barra de entrada localizada à extrema esquerda do cliente Teams, selecione o menu e escolha seu `...` aplicativo na lista.</span><span class="sxs-lookup"><span data-stu-id="d28d4-145">In the navbar located at the far-left of the Teams client, select the `...` menu and choose your app from the list.</span></span>

## <a name="next-step"></a><span data-ttu-id="d28d4-146">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="d28d4-146">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d28d4-147">Criar uma guia pessoal usando ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="d28d4-147">Create a personal tab using ASP.NETCore</span></span>](~/tabs/quickstarts/create-personal-tab-dotnet-core.md)
