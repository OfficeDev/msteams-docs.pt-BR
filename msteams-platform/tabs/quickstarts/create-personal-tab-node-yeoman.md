---
title: 'Quickstart: Crie uma guia pessoal personalizada com Node.js e o Gerador Yeoman para Microsoft Teams'
author: laujan
description: Um guia rápido para criar uma guia pessoal com o Gerador Yeoman para Microsoft Teams.
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
# <a name="create-a-custom-personal-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="86eb3-103">Crie uma guia pessoal personalizada usando Node.js e o Gerador Yeoman para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="86eb3-103">Create a custom personal tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="86eb3-104">Esta rápida partida segue os passos descritos no [Aplicativo Build Your First Microsoft Teams](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki encontrado no repositório de GitHub Microsoft OfficeDev.</span><span class="sxs-lookup"><span data-stu-id="86eb3-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="86eb3-105">Nesta partida rápida, vamos caminhar criando uma guia pessoal personalizada usando o [gerador Teams Yeoman](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span><span class="sxs-lookup"><span data-stu-id="86eb3-105">In this quickstart we'll walk-through creating a custom personal tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span> <span data-ttu-id="86eb3-106">Também enviaremos o aplicativo para a Equipe.</span><span class="sxs-lookup"><span data-stu-id="86eb3-106">We'll also upload the application to Team.</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="86eb3-107">**Crie uma guia configurável ou estática**</span><span class="sxs-lookup"><span data-stu-id="86eb3-107">**Create a configurable or static tab**</span></span>

<span data-ttu-id="86eb3-108">Use as teclas de seta para selecionar a guia estática.</span><span class="sxs-lookup"><span data-stu-id="86eb3-108">Use the arrow keys to select static tab.</span></span>

>[!IMPORTANT]
><span data-ttu-id="86eb3-109">O componente de caminho *que o seuDefaultTabNameTab,* referenciado nesta partida rápida, é o valor inserido no gerador para *nome de guia padrão* mais a palavra *Guia*.</span><span class="sxs-lookup"><span data-stu-id="86eb3-109">The path component *yourDefaultTabNameTab*, referenced in this quickstart, is the value that you entered in the generator for *Default Tab Name* plus the word *Tab*.</span></span>
>
><span data-ttu-id="86eb3-110">Por exemplo: DefaultTabName: *MyTab*  =>  */MyTabTab/*</span><span class="sxs-lookup"><span data-stu-id="86eb3-110">For example: DefaultTabName: *MyTab* => */MyTabTab/*</span></span>

## <a name="create-your-personal-tab"></a><span data-ttu-id="86eb3-111">Crie sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="86eb3-111">Create your personal tab</span></span>

<span data-ttu-id="86eb3-112">Para adicionar uma guia pessoal a este aplicativo, você criará uma página de conteúdo e atualizará arquivos existentes:</span><span class="sxs-lookup"><span data-stu-id="86eb3-112">To add a personal tab to this application you'll create a content page and update existing files:</span></span>

- <span data-ttu-id="86eb3-113">Em seu editor de código, crie um novo arquivo HTML, **personal.html** e adicione a seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="86eb3-113">In your code editor, create a new HTML file, **personal.html** and add the following markup:</span></span>

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

- <span data-ttu-id="86eb3-114">Salve **personal.html** na pasta **web** do seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="86eb3-114">Save **personal.html** in your application's **web** folder:</span></span>

    ```bash
    ./src/app/web/<yourDefaultTabNameTab>/personal.html
    ```

- <span data-ttu-id="86eb3-115">Abra **manifest.jsno** seu editor de código:</span><span class="sxs-lookup"><span data-stu-id="86eb3-115">Open **manifest.json** in your code editor:</span></span>

    ```bash
    ./src/manifest/manifest.json/
    ```

<span data-ttu-id="86eb3-116">Adicione o seguinte à matriz vazia `staticTabs` `staticTabs":[]` () e adicione o seguinte objeto JSON:</span><span class="sxs-lookup"><span data-stu-id="86eb3-116">Add the following to the empty `staticTabs` array (`staticTabs":[]`) and add the following JSON object:</span></span>

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

<span data-ttu-id="86eb3-117">Lembre-se de atualizar o componente de caminho **"contentURL"** **seuDefaultTabNameTab** com seu nome de guia real.</span><span class="sxs-lookup"><span data-stu-id="86eb3-117">Remember to update the **"contentURL"** path component **yourDefaultTabNameTab** with your actual tab name.</span></span>

- <span data-ttu-id="86eb3-118">Salve os **manifest.jsatualizados.**</span><span class="sxs-lookup"><span data-stu-id="86eb3-118">Save the updated **manifest.json**.</span></span>

- <span data-ttu-id="86eb3-119">Sua página de conteúdo deve servida em um IFrame.</span><span class="sxs-lookup"><span data-stu-id="86eb3-119">Your content page must be served in an IFrame.</span></span> <span data-ttu-id="86eb3-120">Abra **tab.ts** no seu editor de código:</span><span class="sxs-lookup"><span data-stu-id="86eb3-120">Open **Tab.ts** in your code editor:</span></span>

    ```bash
    ./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

- <span data-ttu-id="86eb3-121">Adicione o seguinte à lista de decoradores iFrame:</span><span class="sxs-lookup"><span data-stu-id="86eb3-121">Add the following to the list of IFrame decorators:</span></span>

    ```typescript
     @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
    ```

- <span data-ttu-id="86eb3-122">Certifique-se de salvar o arquivo **Tab.ts** atualizado.</span><span class="sxs-lookup"><span data-stu-id="86eb3-122">Make sure to save the updated **Tab.ts** file.</span></span> <span data-ttu-id="86eb3-123">Seu código de guia está completo.</span><span class="sxs-lookup"><span data-stu-id="86eb3-123">Your tab code is complete.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="86eb3-124">Construa e execute sua aplicação</span><span class="sxs-lookup"><span data-stu-id="86eb3-124">Build and Run Your Application</span></span>

<span data-ttu-id="86eb3-125">Abra uma solicitação de comando em seu diretório de projetos para concluir as próximas tarefas.</span><span class="sxs-lookup"><span data-stu-id="86eb3-125">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="86eb3-126">Para ver sua guia pessoal, vá para `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span><span class="sxs-lookup"><span data-stu-id="86eb3-126">To view your personal tab, go to `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span></span>

>![captura de tela de guia pessoal](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="86eb3-128">Estabeleça um túnel seguro para sua guia</span><span class="sxs-lookup"><span data-stu-id="86eb3-128">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="86eb3-129">Microsoft Teams é um produto inteiramente baseado em nuvem e exige que seu conteúdo de guia esteja disponível na nuvem usando pontos finais HTTPS.</span><span class="sxs-lookup"><span data-stu-id="86eb3-129">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="86eb3-130">Teams não permite hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exporá sua porta local a uma URL voltada para a Internet.</span><span class="sxs-lookup"><span data-stu-id="86eb3-130">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="86eb3-131">Para testar a extensão da guia, você usará [o ngrok](https://ngrok.com/docs), que é incorporado neste aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86eb3-131">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="86eb3-132">O Ngrok é uma ferramenta de software proxy reversa que criará um túnel para os pontos finais HTTPS disponíveis publicamente do servidor web.</span><span class="sxs-lookup"><span data-stu-id="86eb3-132">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="86eb3-133">Os pontos finais da web do servidor estarão disponíveis durante a sessão atual na sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="86eb3-133">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="86eb3-134">Quando a máquina estiver desligada ou dormir, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="86eb3-134">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="86eb3-135">Em seu prompt de comando, saia do localhost e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="86eb3-135">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="86eb3-136">Depois que sua guia for enviada para equipes da Microsoft, via **ngrok**, e salva com sucesso, você pode visualizá-la em Teams até que sua sessão de túnel termine.</span><span class="sxs-lookup"><span data-stu-id="86eb3-136">After your tab has been uploaded to Microsoft teams, via **ngrok**, and successfully saved, you can view it in Teams until your tunnel session ends.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="86eb3-137">Upload sua inscrição para Teams</span><span class="sxs-lookup"><span data-stu-id="86eb3-137">Upload your application to Teams</span></span>

- <span data-ttu-id="86eb3-138">Abra o cliente Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="86eb3-138">Open the Microsoft Teams client.</span></span> <span data-ttu-id="86eb3-139">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) você pode inspecionar seu código frontal usando [as ferramentas](~/tabs/how-to/developer-tools.md)de desenvolvedor do seu navegador .</span><span class="sxs-lookup"><span data-stu-id="86eb3-139">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="86eb3-140">No painel **Suas Equipes** à esquerda, selecione o `...` menu ao lado da equipe que você está usando para testar sua guia e escolher Gerenciar **equipe**.</span><span class="sxs-lookup"><span data-stu-id="86eb3-140">In the **YourTeams** panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="86eb3-141">No painel principal selecione **Aplicativos** na barra de guia e escolha **Upload um aplicativo personalizado** localizado no canto inferior direito da página.</span><span class="sxs-lookup"><span data-stu-id="86eb3-141">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="86eb3-142">Abra o diretório do projeto, navegue até a pasta **./package,** selecione a pasta zip, clique com o botão direito do mouse e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="86eb3-142">Open your project directory, browse to the **./package** folder, select the zip folder, right-click, and choose **Open**.</span></span> <span data-ttu-id="86eb3-143">Sua guia será enviada para Teams.</span><span class="sxs-lookup"><span data-stu-id="86eb3-143">Your tab will upload into Teams.</span></span>

## <a name="view-your-personal-tabs"></a><span data-ttu-id="86eb3-144">Veja suas guias pessoais</span><span class="sxs-lookup"><span data-stu-id="86eb3-144">View your personal tabs</span></span>

<span data-ttu-id="86eb3-145">No navbar localizado à esquerda do cliente Teams, selecione o `...` menu e escolha seu aplicativo na lista.</span><span class="sxs-lookup"><span data-stu-id="86eb3-145">In the navbar located at the far-left of the Teams client, select the `...` menu and choose your app from the list.</span></span>

## <a name="next-step"></a><span data-ttu-id="86eb3-146">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="86eb3-146">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86eb3-147">Crie uma guia pessoal usando o ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="86eb3-147">Create a personal tab using ASP.NETCore</span></span>](~/tabs/quickstarts/create-personal-tab-dotnet-core.md)
