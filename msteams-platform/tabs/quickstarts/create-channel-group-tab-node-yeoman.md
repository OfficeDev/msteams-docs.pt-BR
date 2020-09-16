---
title: Criar uma guia de canal e grupo personalizado com Node.js e o gerador Yeoman para o Microsoft Teams
author: laujan
description: Um guia de início rápido para criar uma guia de canal e grupo com o gerador Yeoman para o Microsoft Teams.
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 77081f83c753f812032ccfebe2accd3cb8859f99
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "47818931"
---
# <a name="create-a-custom-channel-and-group-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="636d4-103">Criar uma guia de canal e grupo personalizado com Node.js e o gerador Yeoman para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="636d4-103">Create a custom channel and group tab with Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="636d4-104">Este QuickStart segue as etapas descritas no [Build Your First Microsoft Teams app](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) wiki encontrado no repositório do GitHub do Microsoft OfficeDev.</span><span class="sxs-lookup"><span data-stu-id="636d4-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="636d4-105">Neste QuickStart, vamos examinar a criação de uma guia de canal e de grupo personalizada usando o [gerador Yeoman do teams](https://github.com/OfficeDev/generator-teams/).</span><span class="sxs-lookup"><span data-stu-id="636d4-105">In this quickstart we'll walk-through creating a custom channel and group tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/).</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="636d4-106">**Você deseja criar uma guia configurável ou estática?**</span><span class="sxs-lookup"><span data-stu-id="636d4-106">**Do you want to create a configurable or static tab?**</span></span>

<span data-ttu-id="636d4-107">Use as teclas de seta para selecionar a guia configurável.</span><span class="sxs-lookup"><span data-stu-id="636d4-107">Use the arrow keys to select configurable tab.</span></span>

<span data-ttu-id="636d4-108">**Quais escopos você pretende usar para sua guia?**</span><span class="sxs-lookup"><span data-stu-id="636d4-108">**What scopes do you intend to use for your Tab?**</span></span>

<span data-ttu-id="636d4-109">Você pode selecionar uma equipe e/ou um chat de grupo</span><span class="sxs-lookup"><span data-stu-id="636d4-109">You can select a Team and/or a group chat</span></span>

<span data-ttu-id="636d4-110">**Deseja que esta guia esteja disponível no SharePoint Online? (S/n)**</span><span class="sxs-lookup"><span data-stu-id="636d4-110">**Do you want this tab to be available in SharePoint Online? (Y/n)**</span></span> 

<span data-ttu-id="636d4-111">Selecione **n**.</span><span class="sxs-lookup"><span data-stu-id="636d4-111">Select **n**.</span></span>

>[!IMPORTANT]
><span data-ttu-id="636d4-112">O componente de caminho **yourDefaultTabNameTab**, referenciado neste QuickStart, é o valor que você inseriu no gerador para o **nome de guia padrão** mais a **guia**Word.</span><span class="sxs-lookup"><span data-stu-id="636d4-112">The path component **yourDefaultTabNameTab**, referenced in this quickstart, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span></span>
>
><span data-ttu-id="636d4-113">Por exemplo: DefaultTabName: **MyTab**  =>  **/MyTabTab/**</span><span class="sxs-lookup"><span data-stu-id="636d4-113">For example: DefaultTabName: **MyTab** => **/MyTabTab/**</span></span>

<span data-ttu-id="636d4-114">No diretório do projeto, navegue até o seguinte:</span><span class="sxs-lookup"><span data-stu-id="636d4-114">In your project directory, navigate to the following:</span></span>

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

<span data-ttu-id="636d4-115">É aí que você encontrará sua lógica de tabulação.</span><span class="sxs-lookup"><span data-stu-id="636d4-115">That is where you'll find your tab logic.</span></span> <span data-ttu-id="636d4-116">Localize o `render()` método e adicione a seguinte `<div>` marca e conteúdo à parte superior do `<PanelBody>` código do contêiner:</span><span class="sxs-lookup"><span data-stu-id="636d4-116">Locate the `render()` method and add the following `<div>` tag and content to the top of the `<PanelBody>` container code:</span></span>

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

<span data-ttu-id="636d4-117">Certifique-se de salvar o arquivo atualizado.</span><span class="sxs-lookup"><span data-stu-id="636d4-117">Make sure to save the updated file.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="636d4-118">Criar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="636d4-118">Build and Run Your Application</span></span>

<span data-ttu-id="636d4-119">Abra um prompt de comando no diretório do projeto para concluir as próximas tarefas.</span><span class="sxs-lookup"><span data-stu-id="636d4-119">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="636d4-120">Para exibir a página de configuração de guia, vá para `https://localhost:3007/<yourDefaultAppNameTab>/config.html` .</span><span class="sxs-lookup"><span data-stu-id="636d4-120">To view your tab configuration page go to `https://localhost:3007/<yourDefaultAppNameTab>/config.html`.</span></span> <span data-ttu-id="636d4-121">Você verá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="636d4-121">You should see the following:</span></span>

![captura de tela da página de configuração](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="636d4-123">Estabelecer um túnel seguro para sua guia</span><span class="sxs-lookup"><span data-stu-id="636d4-123">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="636d4-124">O Microsoft Teams é um produto totalmente baseado em nuvem e exige que o conteúdo da guia esteja disponível na nuvem usando pontos de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="636d4-124">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="636d4-125">O Microsoft Teams não permite hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exporá sua porta local para uma URL voltada para a Internet.</span><span class="sxs-lookup"><span data-stu-id="636d4-125">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="636d4-126">Para testar sua extensão de guia, você usará o [ngrok](https://ngrok.com/docs), que é integrado a esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="636d4-126">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="636d4-127">O Ngrok é uma ferramenta de software de proxy reverso que criará um túnel para os pontos de extremidade HTTPS publicamente disponíveis do servidor Web em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="636d4-127">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="636d4-128">Os pontos de extremidade da Web do seu servidor estarão disponíveis durante a sessão atual em sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="636d4-128">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="636d4-129">Quando o computador é desligado ou vai para a suspensão, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="636d4-129">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="636d4-130">No prompt de comando, saia do localhost e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="636d4-130">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="636d4-131">Depois que a guia tiver sido carregada no Microsoft Teams e salva com êxito, você poderá exibi-la na Galeria de guias, adicioná-la à barra de guias e interagir com ela até que a sessão de túnel do ngrok seja encerrada.</span><span class="sxs-lookup"><span data-stu-id="636d4-131">After your tab has been uploaded to Microsoft teams and successfully saved, you can view it in the tabs gallery, add it to the tabs bar, and interact with it until your ngrok tunnel session ends.</span></span> <span data-ttu-id="636d4-132">Se você reiniciar sua sessão do ngrok, será necessário atualizar seu aplicativo com a nova URL.</span><span class="sxs-lookup"><span data-stu-id="636d4-132">If you restart your ngrok session, you'll need to update your app with the new URL.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="636d4-133">Carregar seu aplicativo para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="636d4-133">Upload your application to Teams</span></span>

- <span data-ttu-id="636d4-134">Abra o cliente do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="636d4-134">Open the Microsoft Teams client.</span></span> <span data-ttu-id="636d4-135">Se você usar a [versão baseada na Web](https://teams.microsoft.com) , poderá inspecionar seu código de front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md)do navegador.</span><span class="sxs-lookup"><span data-stu-id="636d4-135">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="636d4-136">No painel *YourTeams* à esquerda, selecione o `...` menu ao lado da equipe que você está usando para testar sua guia e escolha **Gerenciar equipe**.</span><span class="sxs-lookup"><span data-stu-id="636d4-136">In the *YourTeams* panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="636d4-137">No painel principal, selecione **aplicativos** na barra de guias e escolha **carregar um aplicativo personalizado** localizado no canto inferior direito da página.</span><span class="sxs-lookup"><span data-stu-id="636d4-137">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="636d4-138">Abra o diretório do projeto, navegue até a pasta **./Package** , selecione a pasta zip do pacote de aplicativos e escolha **abrir**.</span><span class="sxs-lookup"><span data-stu-id="636d4-138">Open your project directory, browse to the **./package** folder, select the app package zip folder and choose **Open**.</span></span> <span data-ttu-id="636d4-139">Sua guia será carregada no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="636d4-139">Your tab will upload into Teams.</span></span>
- <span data-ttu-id="636d4-140">Retorne à sua equipe, escolha o canal onde você deseja exibir a guia, selecione ➕ na barra de guias e escolha sua guia na galeria.</span><span class="sxs-lookup"><span data-stu-id="636d4-140">Return to your team, choose the channel where you would like to display the tab, select ➕ from the tab bar, and choose your tab from the gallery.</span></span>
- <span data-ttu-id="636d4-141">Siga as instruções para adicionar uma guia. Observe que há uma caixa de diálogo de configuração personalizada para a guia canal/grupo.</span><span class="sxs-lookup"><span data-stu-id="636d4-141">Follow the directions for adding a tab. Note that there's a custom configuration dialog for your channel/group tab.</span></span>
- <span data-ttu-id="636d4-142">Selecione **salvar** e sua guia será adicionada à barra de guias do canal.</span><span class="sxs-lookup"><span data-stu-id="636d4-142">Select **Save** and your tab will be added to the channel's tab bar.</span></span>
