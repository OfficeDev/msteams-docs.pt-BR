---
title: 'Início rápido: criar uma guia pessoal personalizada com Node.js e o gerador Yeoman para o Microsoft Teams'
author: laujan
description: Um guia de início rápido para criar uma guia pessoal com o gerador Yeoman para o Microsoft Teams.
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: e39878d117b0b1b1f8c0e2450021d9238f5b7877
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "47818882"
---
# <a name="quickstart-create-a-custom-personal-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="5f37f-103">Início rápido: criar uma guia pessoal personalizada com Node.js e o gerador Yeoman para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5f37f-103">Quickstart: Create a custom personal tab with Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="5f37f-104">Este QuickStart segue as etapas descritas no [Build Your First Microsoft Teams app](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) wiki encontrado no repositório do GitHub do Microsoft OfficeDev.</span><span class="sxs-lookup"><span data-stu-id="5f37f-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="5f37f-105">Neste QuickStart, veremos como criar uma guia pessoal personalizada usando o [gerador Yeoman do teams](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span><span class="sxs-lookup"><span data-stu-id="5f37f-105">In this quickstart we'll walk-through creating a custom personal tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span> <span data-ttu-id="5f37f-106">Também carregaremos o aplicativo para a equipe.</span><span class="sxs-lookup"><span data-stu-id="5f37f-106">We'll also upload the application to Team.</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="5f37f-107">**Você deseja criar uma guia configurável ou estática?**</span><span class="sxs-lookup"><span data-stu-id="5f37f-107">**Do you want to create a configurable or static tab?**</span></span>

<span data-ttu-id="5f37f-108">Use as teclas de seta para selecionar a guia estático.</span><span class="sxs-lookup"><span data-stu-id="5f37f-108">Use the arrow keys to select static tab.</span></span>

>[!IMPORTANT]
><span data-ttu-id="5f37f-109">O componente de caminho *yourDefaultTabNameTab*, referenciado neste QuickStart, é o valor que você inseriu no gerador para o *nome de guia padrão* mais a *guia*Word.</span><span class="sxs-lookup"><span data-stu-id="5f37f-109">The path component *yourDefaultTabNameTab*, referenced in this quickstart, is the value that you entered in the generator for *Default Tab Name* plus the word *Tab*.</span></span>
>
><span data-ttu-id="5f37f-110">Por exemplo: DefaultTabName: *MyTab*  =>  */MyTabTab/*</span><span class="sxs-lookup"><span data-stu-id="5f37f-110">For example: DefaultTabName: *MyTab* => */MyTabTab/*</span></span>

## <a name="create-your-personal-tab"></a><span data-ttu-id="5f37f-111">Criar sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="5f37f-111">Create your personal tab</span></span>

<span data-ttu-id="5f37f-112">Para adicionar uma guia pessoal a este aplicativo, você criará uma página de conteúdo e atualizará os arquivos existentes:</span><span class="sxs-lookup"><span data-stu-id="5f37f-112">To add a personal tab to this application you'll create a content page and update existing files:</span></span>

- <span data-ttu-id="5f37f-113">No editor de códigos, crie um novo arquivo HTML, **personal.html** e adicione a marcação a seguir:</span><span class="sxs-lookup"><span data-stu-id="5f37f-113">In your code editor, create a new HTML file, **personal.html** and add the following markup:</span></span>

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

- <span data-ttu-id="5f37f-114">Salve **personal.html** na pasta **da Web** do seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="5f37f-114">Save **personal.html** in your application's **web** folder:</span></span>

```bash
./src/app/web/<yourDefaultTabNameTab>/personal.html
```

- <span data-ttu-id="5f37f-115">Abra o **manifest.jsno** editor de código:</span><span class="sxs-lookup"><span data-stu-id="5f37f-115">Open **manifest.json** in your code editor:</span></span>

```bash
./src/manifest/manifest.json/
```

<span data-ttu-id="5f37f-116">Adicione o seguinte à matriz vazia `staticTabs` ( `staticTabs":[]` ) e adicione o seguinte objeto JSON:</span><span class="sxs-lookup"><span data-stu-id="5f37f-116">Add the following to the empty `staticTabs` array (`staticTabs":[]`) and add the following JSON object:</span></span>

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

<span data-ttu-id="5f37f-117">Lembre-se de atualizar o componente de caminho **"contentURL"** **yourDefaultTabNameTab** com seu nome de guia real.</span><span class="sxs-lookup"><span data-stu-id="5f37f-117">Remember to update the **"contentURL"** path component **yourDefaultTabNameTab** with your actual tab name.</span></span>

- <span data-ttu-id="5f37f-118">Salve o **manifest.jsatualizado em**.</span><span class="sxs-lookup"><span data-stu-id="5f37f-118">Save the updated **manifest.json**.</span></span>

- <span data-ttu-id="5f37f-119">A página de conteúdo deve ser fornecida em um IFrame.</span><span class="sxs-lookup"><span data-stu-id="5f37f-119">Your content page must be served in an IFrame.</span></span> <span data-ttu-id="5f37f-120">Abra **Tab. TS** no editor de código:</span><span class="sxs-lookup"><span data-stu-id="5f37f-120">Open **Tab.ts** in your code editor:</span></span>

 ```bash
./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
```

- <span data-ttu-id="5f37f-121">Adicione o seguinte à lista de decoradores de IFrame:</span><span class="sxs-lookup"><span data-stu-id="5f37f-121">Add the following to the list of IFrame decorators:</span></span>

```typescript
 @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
```

- <span data-ttu-id="5f37f-122">Certifique-se de salvar o arquivo **Tab atualizado. TS** .</span><span class="sxs-lookup"><span data-stu-id="5f37f-122">Make sure to save the updated **Tab.ts** file.</span></span> <span data-ttu-id="5f37f-123">O código da guia está completo.</span><span class="sxs-lookup"><span data-stu-id="5f37f-123">Your tab code is complete.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="5f37f-124">Criar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="5f37f-124">Build and Run Your Application</span></span>

<span data-ttu-id="5f37f-125">Abra um prompt de comando no diretório do projeto para concluir as próximas tarefas.</span><span class="sxs-lookup"><span data-stu-id="5f37f-125">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="5f37f-126">Para exibir sua guia pessoal, vá para `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span><span class="sxs-lookup"><span data-stu-id="5f37f-126">To view your personal tab, go to `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span></span>

>![captura de tela pessoal](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="5f37f-128">Estabelecer um túnel seguro para sua guia</span><span class="sxs-lookup"><span data-stu-id="5f37f-128">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="5f37f-129">O Microsoft Teams é um produto totalmente baseado em nuvem e exige que o conteúdo da guia esteja disponível na nuvem usando pontos de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5f37f-129">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="5f37f-130">O Microsoft Teams não permite hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exporá sua porta local para uma URL voltada para a Internet.</span><span class="sxs-lookup"><span data-stu-id="5f37f-130">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="5f37f-131">Para testar sua extensão de guia, você usará o [ngrok](https://ngrok.com/docs), que é integrado a esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5f37f-131">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="5f37f-132">O Ngrok é uma ferramenta de software de proxy reverso que criará um túnel para os pontos de extremidade HTTPS publicamente disponíveis do servidor Web em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="5f37f-132">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="5f37f-133">Os pontos de extremidade da Web do seu servidor estarão disponíveis durante a sessão atual em sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="5f37f-133">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="5f37f-134">Quando o computador é desligado ou vai para a suspensão, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="5f37f-134">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="5f37f-135">No prompt de comando, saia do localhost e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5f37f-135">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="5f37f-136">Depois que a guia tiver sido carregada no Microsoft Teams, via *ngrok*e salva com êxito, você poderá exibi-la no Teams até que a sessão de túnel seja encerrada.</span><span class="sxs-lookup"><span data-stu-id="5f37f-136">After your tab has been uploaded to Microsoft teams, via *ngrok*, and successfully saved, you can view it in Teams until your tunnel session ends.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="5f37f-137">Carregar seu aplicativo para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5f37f-137">Upload your application to Teams</span></span>

- <span data-ttu-id="5f37f-138">Abra o cliente do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="5f37f-138">Open the Microsoft Teams client.</span></span> <span data-ttu-id="5f37f-139">Se você usar a [versão baseada na Web](https://teams.microsoft.com) , poderá inspecionar seu código de front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md)do navegador.</span><span class="sxs-lookup"><span data-stu-id="5f37f-139">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="5f37f-140">No painel *YourTeams* à esquerda, selecione o `...` menu ao lado da equipe que você está usando para testar sua guia e escolha **Gerenciar equipe**.</span><span class="sxs-lookup"><span data-stu-id="5f37f-140">In the *YourTeams* panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="5f37f-141">No painel principal, selecione **aplicativos** na barra de guias e escolha **carregar um aplicativo personalizado** localizado no canto inferior direito da página.</span><span class="sxs-lookup"><span data-stu-id="5f37f-141">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="5f37f-142">Abra o diretório do projeto, navegue até a pasta **./Package** , selecione a pasta zip, clique com o botão direito do mouse e escolha **abrir**.</span><span class="sxs-lookup"><span data-stu-id="5f37f-142">Open your project directory, browse to the **./package** folder, select the zip folder, right-click, and choose **Open**.</span></span> <span data-ttu-id="5f37f-143">Sua guia será carregada no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="5f37f-143">Your tab will upload into Teams.</span></span>

## <a name="view-your-personal-tabs"></a><span data-ttu-id="5f37f-144">Exibir suas guias pessoais</span><span class="sxs-lookup"><span data-stu-id="5f37f-144">View your personal tabs</span></span>

<span data-ttu-id="5f37f-145">Na barra de navegação localizada na extrema esquerda do cliente Teams, selecione o `...` menu e escolha seu aplicativo na lista.</span><span class="sxs-lookup"><span data-stu-id="5f37f-145">In the navbar located at the far-left of the Teams client, select the `...` menu and choose your app from the list.</span></span>
