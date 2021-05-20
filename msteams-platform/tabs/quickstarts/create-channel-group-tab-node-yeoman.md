---
title: Crie um canal personalizado e tab em grupo com Node.js e o Gerador Yeoman para Microsoft Teams
author: laujan
description: Um guia rápido para criar uma guia de canal e grupo com o Gerador Yeoman para Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 559393884e3b8a4aad1787ea4ca8f9f4de54d151
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566639"
---
# <a name="create-a-custom-channel-and-group-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="a07a9-103">Crie uma guia personalizada de canal e grupo usando Node.js e o Gerador Yeoman para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a07a9-103">Create a custom channel and group tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="a07a9-104">Esta rápida partida segue os passos descritos no [Aplicativo Build Your First Microsoft Teams](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki encontrado no repositório de GitHub Microsoft OfficeDev.</span><span class="sxs-lookup"><span data-stu-id="a07a9-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="a07a9-105">Nesta partida rápida, vamos caminhar criando um canal personalizado e uma guia de grupo usando o [gerador Teams Yeoman](https://github.com/OfficeDev/generator-teams/).</span><span class="sxs-lookup"><span data-stu-id="a07a9-105">In this quickstart we'll walk-through creating a custom channel and group tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/).</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="a07a9-106">**Deseja criar uma guia configurável ou estática?**</span><span class="sxs-lookup"><span data-stu-id="a07a9-106">**Do you want to create a configurable or static tab?**</span></span>

<span data-ttu-id="a07a9-107">Use as teclas de seta para selecionar a guia configurável.</span><span class="sxs-lookup"><span data-stu-id="a07a9-107">Use the arrow keys to select configurable tab.</span></span>

<span data-ttu-id="a07a9-108">**Quais escopos você pretende usar para o seu Tab?**</span><span class="sxs-lookup"><span data-stu-id="a07a9-108">**What scopes do you intend to use for your Tab?**</span></span>

<span data-ttu-id="a07a9-109">Você pode selecionar uma equipe e/ou um bate-papo em grupo</span><span class="sxs-lookup"><span data-stu-id="a07a9-109">You can select a Team and/or a group chat</span></span>

<span data-ttu-id="a07a9-110">**Você deseja que esta guia esteja disponível em SharePoint Online? (Y/n)**</span><span class="sxs-lookup"><span data-stu-id="a07a9-110">**Do you want this tab to be available in SharePoint Online? (Y/n)**</span></span> 

<span data-ttu-id="a07a9-111">Selecione **n**.</span><span class="sxs-lookup"><span data-stu-id="a07a9-111">Select **n**.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a07a9-112">O componente de caminho **que o seuDefaultTabNameTab,** referenciado nesta partida rápida, é o valor inserido no gerador para **nome de guia padrão** mais a palavra **Guia**.</span><span class="sxs-lookup"><span data-stu-id="a07a9-112">The path component **yourDefaultTabNameTab**, referenced in this quickstart, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span></span>
>
><span data-ttu-id="a07a9-113">Por exemplo: DefaultTabName: **MyTab**  =>  **/MyTabTab/**</span><span class="sxs-lookup"><span data-stu-id="a07a9-113">For example: DefaultTabName: **MyTab** => **/MyTabTab/**</span></span>

<span data-ttu-id="a07a9-114">Em seu diretório de projetos, navegue até o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a07a9-114">In your project directory, navigate to the following:</span></span>

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

<span data-ttu-id="a07a9-115">É aí que você encontrará sua lógica de guia.</span><span class="sxs-lookup"><span data-stu-id="a07a9-115">That is where you'll find your tab logic.</span></span> <span data-ttu-id="a07a9-116">Localize o `render()` método e adicione a seguinte tag e conteúdo à parte superior do código do `<div>` `<PanelBody>` contêiner:</span><span class="sxs-lookup"><span data-stu-id="a07a9-116">Locate the `render()` method and add the following `<div>` tag and content to the top of the `<PanelBody>` container code:</span></span>

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

<span data-ttu-id="a07a9-117">Certifique-se de salvar o arquivo atualizado.</span><span class="sxs-lookup"><span data-stu-id="a07a9-117">Make sure to save the updated file.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="a07a9-118">Construa e execute sua aplicação</span><span class="sxs-lookup"><span data-stu-id="a07a9-118">Build and Run Your Application</span></span>

<span data-ttu-id="a07a9-119">Abra uma solicitação de comando em seu diretório de projetos para concluir as próximas tarefas.</span><span class="sxs-lookup"><span data-stu-id="a07a9-119">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="a07a9-120">Para exibir sua página de configuração de guia vá para `https://localhost:3007/<yourDefaultAppNameTab>/config.html` .</span><span class="sxs-lookup"><span data-stu-id="a07a9-120">To view your tab configuration page go to `https://localhost:3007/<yourDefaultAppNameTab>/config.html`.</span></span> <span data-ttu-id="a07a9-121">Você verá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a07a9-121">You should see the following:</span></span>

![captura de tela da página de configuração](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="a07a9-123">Estabeleça um túnel seguro para sua guia</span><span class="sxs-lookup"><span data-stu-id="a07a9-123">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="a07a9-124">Microsoft Teams é um produto inteiramente baseado em nuvem e exige que seu conteúdo de guia esteja disponível na nuvem usando pontos finais HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a07a9-124">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="a07a9-125">Teams não permite hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exporá sua porta local a uma URL voltada para a Internet.</span><span class="sxs-lookup"><span data-stu-id="a07a9-125">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="a07a9-126">Para testar a extensão da guia, você usará [o ngrok](https://ngrok.com/docs), que é incorporado neste aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a07a9-126">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="a07a9-127">O Ngrok é uma ferramenta de software proxy reversa que criará um túnel para os pontos finais HTTPS disponíveis publicamente do servidor web.</span><span class="sxs-lookup"><span data-stu-id="a07a9-127">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="a07a9-128">Os pontos finais da web do servidor estarão disponíveis durante a sessão atual na sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="a07a9-128">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="a07a9-129">Quando a máquina estiver desligada ou dormir, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="a07a9-129">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="a07a9-130">Em seu prompt de comando, saia do localhost e digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a07a9-130">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="a07a9-131">Depois que sua guia for enviada para equipes da Microsoft e salva com sucesso, você pode visualizá-la na galeria de guias, adicioná-la à barra de guias e interagir com ela até que a sessão do túnel ngrok termine.</span><span class="sxs-lookup"><span data-stu-id="a07a9-131">After your tab has been uploaded to Microsoft teams and successfully saved, you can view it in the tabs gallery, add it to the tabs bar, and interact with it until your ngrok tunnel session ends.</span></span> <span data-ttu-id="a07a9-132">Se você reiniciar sua sessão ngrok, você precisará atualizar seu aplicativo com a nova URL.</span><span class="sxs-lookup"><span data-stu-id="a07a9-132">If you restart your ngrok session, you'll need to update your app with the new URL.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="a07a9-133">Upload sua inscrição para Teams</span><span class="sxs-lookup"><span data-stu-id="a07a9-133">Upload your application to Teams</span></span>

- <span data-ttu-id="a07a9-134">Abra o cliente Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a07a9-134">Open the Microsoft Teams client.</span></span> <span data-ttu-id="a07a9-135">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) você pode inspecionar seu código frontal usando [as ferramentas](~/tabs/how-to/developer-tools.md)de desenvolvedor do seu navegador .</span><span class="sxs-lookup"><span data-stu-id="a07a9-135">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="a07a9-136">No painel *Suas Equipes* à esquerda, selecione o `...` menu ao lado da equipe que você está usando para testar sua guia e escolher Gerenciar **equipe**.</span><span class="sxs-lookup"><span data-stu-id="a07a9-136">In the *YourTeams* panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="a07a9-137">No painel principal selecione **Aplicativos** na barra de guia e escolha **Upload um aplicativo personalizado** localizado no canto inferior direito da página.</span><span class="sxs-lookup"><span data-stu-id="a07a9-137">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="a07a9-138">Abra o diretório do projeto, navegue até a pasta **./package,** selecione a pasta zip do pacote do aplicativo e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="a07a9-138">Open your project directory, browse to the **./package** folder, select the app package zip folder and choose **Open**.</span></span> <span data-ttu-id="a07a9-139">Sua guia será enviada para Teams.</span><span class="sxs-lookup"><span data-stu-id="a07a9-139">Your tab will upload into Teams.</span></span>
- <span data-ttu-id="a07a9-140">Retorne à sua equipe, escolha o canal onde deseja exibir a guia, selecione ➕ na barra de guia e escolha sua guia na galeria.</span><span class="sxs-lookup"><span data-stu-id="a07a9-140">Return to your team, choose the channel where you would like to display the tab, select ➕ from the tab bar, and choose your tab from the gallery.</span></span>
- <span data-ttu-id="a07a9-141">Siga as instruções para adicionar uma guia. Observe que há uma caixa de diálogo de configuração personalizada para sua guia canal/grupo.</span><span class="sxs-lookup"><span data-stu-id="a07a9-141">Follow the directions for adding a tab. Note that there's a custom configuration dialog for your channel/group tab.</span></span>
- <span data-ttu-id="a07a9-142">Selecione **Salvar** e sua guia será adicionada à barra de guias do canal.</span><span class="sxs-lookup"><span data-stu-id="a07a9-142">Select **Save** and your tab will be added to the channel's tab bar.</span></span>

## <a name="next-step"></a><span data-ttu-id="a07a9-143">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="a07a9-143">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a07a9-144">Crie uma guia de canal e grupo personalizada com ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="a07a9-144">Create a Custom Channel and Group Tab with ASP.NETCore</span></span>](~/tabs/quickstarts/create-channel-group-tab-dotnet-core.md)