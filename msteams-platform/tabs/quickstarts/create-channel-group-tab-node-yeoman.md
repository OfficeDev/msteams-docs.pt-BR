---
title: Criar um canal personalizado e uma guia de grupo com Node.js e o Gerador Yeoman para Microsoft Teams
author: laujan
description: Um guia de início rápido para criar um canal e uma guia de grupo com o Gerador Yeoman para Microsoft Teams.
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
# <a name="create-a-custom-channel-and-group-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="b24ad-103">Crie um canal personalizado e uma guia de grupo usando Node.js e o Gerador Yeoman para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b24ad-103">Create a custom channel and group tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="b24ad-104">Esse início rápido segue as etapas descritas no [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki encontrado no repositório do Microsoft OfficeDev GitHub.</span><span class="sxs-lookup"><span data-stu-id="b24ad-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="b24ad-105">Neste início rápido, vamos passo a passo criando um canal personalizado e uma guia de grupo usando o gerador [yeoman Teams .](https://github.com/OfficeDev/generator-teams/)</span><span class="sxs-lookup"><span data-stu-id="b24ad-105">In this quickstart we'll walk-through creating a custom channel and group tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/).</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="b24ad-106">**Você deseja criar uma guia configurável ou estática?**</span><span class="sxs-lookup"><span data-stu-id="b24ad-106">**Do you want to create a configurable or static tab?**</span></span>

<span data-ttu-id="b24ad-107">Use as teclas de seta para selecionar a guia configurável.</span><span class="sxs-lookup"><span data-stu-id="b24ad-107">Use the arrow keys to select configurable tab.</span></span>

<span data-ttu-id="b24ad-108">**Quais escopos você pretende usar para sua Guia?**</span><span class="sxs-lookup"><span data-stu-id="b24ad-108">**What scopes do you intend to use for your Tab?**</span></span>

<span data-ttu-id="b24ad-109">Você pode selecionar uma equipe e/ou um chat em grupo</span><span class="sxs-lookup"><span data-stu-id="b24ad-109">You can select a Team and/or a group chat</span></span>

<span data-ttu-id="b24ad-110">**Deseja que essa guia seja disponibilizada no SharePoint Online? (Y/n)**</span><span class="sxs-lookup"><span data-stu-id="b24ad-110">**Do you want this tab to be available in SharePoint Online? (Y/n)**</span></span> 

<span data-ttu-id="b24ad-111">Selecione **n**.</span><span class="sxs-lookup"><span data-stu-id="b24ad-111">Select **n**.</span></span>

>[!IMPORTANT]
><span data-ttu-id="b24ad-112">O componente de **caminho que seuDefaultTabNameTab**, referenciado neste início rápido, é o valor que você inscrevia no gerador para **Nome** da Guia Padrão mais a **palavra Tab**.</span><span class="sxs-lookup"><span data-stu-id="b24ad-112">The path component **yourDefaultTabNameTab**, referenced in this quickstart, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span></span>
>
><span data-ttu-id="b24ad-113">Por exemplo: DefaultTabName: **MyTab**  =>  **/MyTabTab/**</span><span class="sxs-lookup"><span data-stu-id="b24ad-113">For example: DefaultTabName: **MyTab** => **/MyTabTab/**</span></span>

<span data-ttu-id="b24ad-114">No diretório do projeto, navegue até o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b24ad-114">In your project directory, navigate to the following:</span></span>

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

<span data-ttu-id="b24ad-115">É aí que você encontrará sua lógica de tabulação.</span><span class="sxs-lookup"><span data-stu-id="b24ad-115">That is where you'll find your tab logic.</span></span> <span data-ttu-id="b24ad-116">Localize `render()` o método e adicione a seguinte marca e conteúdo à parte superior do código do `<div>` `<PanelBody>` contêiner:</span><span class="sxs-lookup"><span data-stu-id="b24ad-116">Locate the `render()` method and add the following `<div>` tag and content to the top of the `<PanelBody>` container code:</span></span>

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

<span data-ttu-id="b24ad-117">Certifique-se de salvar o arquivo atualizado.</span><span class="sxs-lookup"><span data-stu-id="b24ad-117">Make sure to save the updated file.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="b24ad-118">Criar e executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b24ad-118">Build and Run Your Application</span></span>

<span data-ttu-id="b24ad-119">Abra um prompt de comando no diretório do projeto para concluir as próximas tarefas.</span><span class="sxs-lookup"><span data-stu-id="b24ad-119">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="b24ad-120">Para exibir sua página de configuração de tabulação, vá para `https://localhost:3007/<yourDefaultAppNameTab>/config.html` .</span><span class="sxs-lookup"><span data-stu-id="b24ad-120">To view your tab configuration page go to `https://localhost:3007/<yourDefaultAppNameTab>/config.html`.</span></span> <span data-ttu-id="b24ad-121">Você verá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b24ad-121">You should see the following:</span></span>

![captura de tela da página de configuração](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="b24ad-123">Estabelecer um túnel seguro para sua guia</span><span class="sxs-lookup"><span data-stu-id="b24ad-123">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="b24ad-124">Microsoft Teams é um produto totalmente baseado em nuvem e exige que o conteúdo da guia seja disponibilizado na nuvem usando pontos de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b24ad-124">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="b24ad-125">Teams não permite a hospedagem local, portanto, você precisa publicar sua guia em uma URL pública ou usar um proxy que exponha sua porta local a uma URL voltada para a Internet.</span><span class="sxs-lookup"><span data-stu-id="b24ad-125">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="b24ad-126">Para testar sua extensão de tabulação, você usará [ngrok](https://ngrok.com/docs), que é integrado a esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b24ad-126">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="b24ad-127">O Ngrok é uma ferramenta de software de proxy reverso que criará um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="b24ad-127">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="b24ad-128">Os pontos de extremidade da Web do seu servidor estarão disponíveis durante a sessão atual no computador local.</span><span class="sxs-lookup"><span data-stu-id="b24ad-128">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="b24ad-129">Quando o computador é desligado ou vai para o sono, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="b24ad-129">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="b24ad-130">No prompt de comando, saia do localhost e insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b24ad-130">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="b24ad-131">Depois que sua guia for carregada para as equipes da Microsoft e salva com êxito, você poderá exibi-la na galeria de guias, adicioná-la à barra de guias e interagir com ela até que sua sessão de túnel de ngrok termine.</span><span class="sxs-lookup"><span data-stu-id="b24ad-131">After your tab has been uploaded to Microsoft teams and successfully saved, you can view it in the tabs gallery, add it to the tabs bar, and interact with it until your ngrok tunnel session ends.</span></span> <span data-ttu-id="b24ad-132">Se você reiniciar sua sessão de ngrok, precisará atualizar seu aplicativo com a nova URL.</span><span class="sxs-lookup"><span data-stu-id="b24ad-132">If you restart your ngrok session, you'll need to update your app with the new URL.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="b24ad-133">Upload seu aplicativo para Teams</span><span class="sxs-lookup"><span data-stu-id="b24ad-133">Upload your application to Teams</span></span>

- <span data-ttu-id="b24ad-134">Abra o Microsoft Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="b24ad-134">Open the Microsoft Teams client.</span></span> <span data-ttu-id="b24ad-135">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de [desenvolvedor do navegador.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="b24ad-135">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="b24ad-136">No painel *YourTeams* à esquerda, selecione o menu ao lado da equipe que você está usando para testar sua guia e `...` escolha Gerenciar **equipe**.</span><span class="sxs-lookup"><span data-stu-id="b24ad-136">In the *YourTeams* panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="b24ad-137">No painel principal, selecione **Aplicativos** **na** barra de guias e escolha Upload um aplicativo personalizado localizado no canto inferior direito da página.</span><span class="sxs-lookup"><span data-stu-id="b24ad-137">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="b24ad-138">Abra o diretório do projeto, navegue até a pasta **./package,** selecione a pasta zip do pacote do aplicativo e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="b24ad-138">Open your project directory, browse to the **./package** folder, select the app package zip folder and choose **Open**.</span></span> <span data-ttu-id="b24ad-139">Sua guia será carregada no Teams.</span><span class="sxs-lookup"><span data-stu-id="b24ad-139">Your tab will upload into Teams.</span></span>
- <span data-ttu-id="b24ad-140">Retorne à sua equipe, escolha o canal onde você gostaria de exibir a guia, selecione ➕ na barra de guias e escolha sua guia na galeria.</span><span class="sxs-lookup"><span data-stu-id="b24ad-140">Return to your team, choose the channel where you would like to display the tab, select ➕ from the tab bar, and choose your tab from the gallery.</span></span>
- <span data-ttu-id="b24ad-141">Siga as instruções para adicionar uma guia. Observe que há uma caixa de diálogo de configuração personalizada para sua guia canal/grupo.</span><span class="sxs-lookup"><span data-stu-id="b24ad-141">Follow the directions for adding a tab. Note that there's a custom configuration dialog for your channel/group tab.</span></span>
- <span data-ttu-id="b24ad-142">Selecione **Salvar** e sua guia será adicionada à barra de guias do canal.</span><span class="sxs-lookup"><span data-stu-id="b24ad-142">Select **Save** and your tab will be added to the channel's tab bar.</span></span>

## <a name="next-step"></a><span data-ttu-id="b24ad-143">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="b24ad-143">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b24ad-144">Criar um Canal Personalizado e Uma Guia de Grupo com ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="b24ad-144">Create a Custom Channel and Group Tab with ASP.NETCore</span></span>](~/tabs/quickstarts/create-channel-group-tab-dotnet-core.md)