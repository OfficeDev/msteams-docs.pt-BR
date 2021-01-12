---
title: Começar - Criar um canal e uma guia de grupo
author: heath-hamilton
description: Crie rapidamente um canal e uma guia de grupo do Microsoft Teams usando o Kit de Ferramentas do Microsoft Teams.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 2ad0474859118f302a39e823f7669dc54061d525
ms.sourcegitcommit: 5687a901d48bcf2f5a3a086e0f703f854e8b9c21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2021
ms.locfileid: "49795451"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a><span data-ttu-id="d9c9f-103">Criar uma guia de canal e grupo para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d9c9f-103">Build a channel and group tab for Microsoft Teams</span></span>

<span data-ttu-id="d9c9f-104">Neste tutorial, você criará uma guia de canal básico *(também* conhecida como guia de *grupo),* que é uma página de tela inteira para um canal de equipe ou chat.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-104">In this tutorial, you'll build a basic *channel tab* (also known as a *group tab*), which is a full-screen page for a team channel or chat.</span></span> <span data-ttu-id="d9c9f-105">Ao contrário de uma guia pessoal, os usuários podem configurar alguns aspectos desse tipo de guia (por exemplo, renomear a guia para que seja significativa para o canal).</span><span class="sxs-lookup"><span data-stu-id="d9c9f-105">Unlike a personal tab, users can configure some aspects of this kind of tab (for example, rename the tab so it's meaningful to their channel).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="d9c9f-106">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="d9c9f-106">Your assignment</span></span>

<span data-ttu-id="d9c9f-107">Há pouco tempo, sua organização criou um aplicativo do Teams que usa uma guia para exibir informações de contato importantes (help desk, RH, etc.).</span><span class="sxs-lookup"><span data-stu-id="d9c9f-107">Not long ago, your organization created a Teams app that uses a tab to display important contact information (help desk, HR, etc.).</span></span> <span data-ttu-id="d9c9f-108">No entanto, como é uma guia pessoal, cada usuário deve instalar a guia para vê-la e a adoção é menor do que o esperado.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-108">However, since it's a personal tab, each user must install the tab to see it and adoption is lower than expected.</span></span> <span data-ttu-id="d9c9f-109">Em outras palavras, muitos funcionários ainda não sabem como alcançar o help desk.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-109">In other words, too many workers still don't know how to reach the help desk.</span></span>

<span data-ttu-id="d9c9f-110">Você pode tornar essas informações mais fáceis de encontrar criando uma guia de canal, o que removerá a carga de exigir que todos instalem um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-110">You can make this information easier to find by building a channel tab, which will remove the burden of requiring everyone to install an app.</span></span> <span data-ttu-id="d9c9f-111">Em vez disso, um usuário pode adicionar a guia em um canal ou chat para beneficiar um grupo inteiro.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-111">Instead, one user can add the tab in a channel or chat for the benefit of an entire group.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="d9c9f-112">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="d9c9f-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d9c9f-113">Criar um projeto de aplicativo usando o Kit de Ferramentas do Microsoft Teams para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d9c9f-113">Create an app project using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="d9c9f-114">Identificar algumas das configurações do aplicativo e a scaffolding relevante para as guias de canal</span><span class="sxs-lookup"><span data-stu-id="d9c9f-114">Identify some of the app configurations and scaffolding relevant to channel tabs</span></span>
> * <span data-ttu-id="d9c9f-115">Criar conteúdo de guia</span><span class="sxs-lookup"><span data-stu-id="d9c9f-115">Create tab content</span></span>
> * <span data-ttu-id="d9c9f-116">Criar conteúdo para a página de configuração de uma guia</span><span class="sxs-lookup"><span data-stu-id="d9c9f-116">Create content for a tab's configuration page</span></span>
> * <span data-ttu-id="d9c9f-117">Forneça um nome de guia sugerido</span><span class="sxs-lookup"><span data-stu-id="d9c9f-117">Provide a suggested tab name</span></span>
> * <span data-ttu-id="d9c9f-118">Criar e executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="d9c9f-118">Build and run your app locally</span></span>
> * <span data-ttu-id="d9c9f-119">Realizar sideload do seu aplicativo no Teams para teste</span><span class="sxs-lookup"><span data-stu-id="d9c9f-119">Sideload your app in Teams for testing</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="d9c9f-120">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="d9c9f-120">Before you begin</span></span>

<span data-ttu-id="d9c9f-121">Se você ainda não o fez, entenda e instale os pré-requisitos de desenvolvimento [do Teams.](build-first-app-overview.md#get-prerequisites)</span><span class="sxs-lookup"><span data-stu-id="d9c9f-121">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="d9c9f-122">1. Criar seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="d9c9f-122">1. Create your app project</span></span>

<span data-ttu-id="d9c9f-123">O Microsoft Teams Toolkit ajuda a configurar seu aplicativo e configurar o scaffolding relevante para guias de canal e grupo, incluindo uma página de configuração básica e uma página de conteúdo que exibe um "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="d9c9f-123">The Microsoft Teams Toolkit helps configure your app and set up scaffolding relevant to channel and group tabs, including a basic configuration page and content page that displays a "Hello, World!"</span></span> <span data-ttu-id="d9c9f-124">message.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-124">message.</span></span>

> [!TIP]
> <span data-ttu-id="d9c9f-125">Se você ainda não criou um projeto de aplicativo do Teams antes, talvez seja útil seguir estas [instruções](../build-your-first-app/build-and-run.md) que explicam os projetos com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-125">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. No Visual Studio Code, selecione **o Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. <span data-ttu-id="d9c9f-127">Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-127">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="d9c9f-128">Na tela **Adicionar recursos,** selecione **Tab** e **Next.**</span><span class="sxs-lookup"><span data-stu-id="d9c9f-128">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
1. <span data-ttu-id="d9c9f-129">Insira um nome para seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-129">Enter a name for your Teams app.</span></span> <span data-ttu-id="d9c9f-130">(Esse é o nome padrão do seu aplicativo e também o nome do diretório do projeto do aplicativo no computador local.) Selecione **a guia Canal do Grupo ou do Teams.**</span><span class="sxs-lookup"><span data-stu-id="d9c9f-130">(This is the default name for your app and also the name of the app project directory on your local machine.) Select **Group or Teams channel tab**.</span></span>
1. <span data-ttu-id="d9c9f-131">Selecione **Concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-131">Select **Finish** at the bottom of the screen to configure your project.</span></span>  

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="d9c9f-132">2. Identifique componentes relevantes do projeto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d9c9f-132">2. Identify relevant app project components</span></span>

<span data-ttu-id="d9c9f-133">Grande parte das configurações e da scaffolding do aplicativo é configurada automaticamente quando você cria seu projeto com o kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-133">Much of the app configurations and scaffolding are set up automatically when you create your project with the toolkit.</span></span> <span data-ttu-id="d9c9f-134">Vejamos os componentes principais para a criação de uma guia de canal.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-134">Let's look at the main components for building a channel tab.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="d9c9f-135">Configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d9c9f-135">App configurations</span></span>

<span data-ttu-id="d9c9f-136">No kit de ferramentas, vá para o **App Studio** para exibir e atualizar as configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-136">In the toolkit, go to **App Studio** to view and update your app configurations.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="d9c9f-137">Scaffolding de aplicativos</span><span class="sxs-lookup"><span data-stu-id="d9c9f-137">App scaffolding</span></span>

<span data-ttu-id="d9c9f-138">O scaffolding do aplicativo fornece os componentes para renderizar sua guia de canal no Teams.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-138">The app scaffolding provides the components for rendering your channel tab in Teams.</span></span> <span data-ttu-id="d9c9f-139">Há muito com o que você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9c9f-139">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="d9c9f-140">Dois arquivos localizados no `src/components` diretório do seu projeto:</span><span class="sxs-lookup"><span data-stu-id="d9c9f-140">Two files located in the `src/components` directory of your project:</span></span>
  * <span data-ttu-id="d9c9f-141">`Tab.js` para renderizar a página de conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-141">`Tab.js` for rendering your tab's content page.</span></span>
  * <span data-ttu-id="d9c9f-142">`TabConfig.js` para renderizar a página de configuração da guia.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-142">`TabConfig.js` for rendering your tab's configuration page.</span></span>
* <span data-ttu-id="d9c9f-143">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-143">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="3-customize-your-tab-content-page"></a><span data-ttu-id="d9c9f-144">3. Personalizar a página de conteúdo da guia</span><span class="sxs-lookup"><span data-stu-id="d9c9f-144">3. Customize your tab content page</span></span>

<span data-ttu-id="d9c9f-145">Copie e atualize o trecho a seguir com informações relevantes para sua organização ou, por um tempo, use o código como estão.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-145">Copy and update the following snippet with information that's relevant to your organization or, for the sake of time, use the code as is.</span></span>

```JSX
<div>
  <h1>Important Contacts</h1>
    <ul>
      <li>Help Desk: <a href="mailto:support@company.com">support@company.com</a></li>
      <li>Human Resources: <a href="mailto:hr@company.com">hr@company.com</a></li>
      <li>Facilities: <a href="mailto:facilities@company.com">facilities@company.com</a></li>
    </ul>
</div>
```

<span data-ttu-id="d9c9f-146">Vá para o `src/components` diretório e `Tab.js` abra.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-146">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="d9c9f-147">Localize `render()` a função e colar o conteúdo dentro `return()` (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="d9c9f-147">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

```JavaScript
render() {

    let userName = Object.keys(this.state.context).length > 0 ? this.state.context['upn'] : "";

    return (
    <div>
      <h1>Important Contacts</h1>
        <ul>
          <li>Help Desk: <a href="mailto:support@company.com">support@company.com</a></li>
          <li>Human Resources: <a href="mailto:hr@company.com">hr@company.com</a></li>
          <li>Facilities: <a href="mailto:facilities@company.com">facilities@company.com</a></li>
        </ul>
    </div>
    );
}
```

<span data-ttu-id="d9c9f-148">Adicione a regra a seguir (também localizada em) para que os links de email sejam mais fáceis de `App.css` `src/components` ler, independentemente do tema usado.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-148">Add the following rule to `App.css` (also located in `src/components`) so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a><span data-ttu-id="d9c9f-149">4. Personalizar a página de configuração da guia</span><span class="sxs-lookup"><span data-stu-id="d9c9f-149">4. Customize your tab configuration page</span></span>

<span data-ttu-id="d9c9f-150">Cada guia em um canal ou chat tem uma página de configuração, uma modal com pelo menos uma opção de configuração exibida quando os usuários adicionam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-150">Every tab in a channel or chat has a configuration page, a modal with at least one setup option that displays when users add your app.</span></span> <span data-ttu-id="d9c9f-151">Por padrão, a página de configuração pergunta aos usuários se eles querem notificar o canal ou o chat quando a guia é instalada.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-151">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span>

<span data-ttu-id="d9c9f-152">Adicione algum conteúdo personalizado à sua página de configuração.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-152">Add some custom content to your configuration page.</span></span> <span data-ttu-id="d9c9f-153">Vá para o diretório do projeto, abra e atualize o conteúdo do espaço reservado `src/components` `TabConfig.js` dentro `return()` (conforme mostrado no exemplo a seguir).</span><span class="sxs-lookup"><span data-stu-id="d9c9f-153">Go to your project's `src/components` directory, open `TabConfig.js`, and update the placeholder content inside `return()` (as shown in the following example).</span></span>

```JavaScript
return (
    <div>
      <h1>Add My Contoso Contacts</h1>
      <div>
        Select <b>Save</b> to add our organization's important contacts to this workspace.
      </div>
    </div>
);
```
 
> [!TIP]
> <span data-ttu-id="d9c9f-154">No mínimo, forneça algumas breves informações sobre seu aplicativo nesta página, pois essa pode ser a primeira vez que os usuários estão aprendendo sobre ele.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-154">At minimum, provide some brief information about your app on this page since this may be the first time users are learning about it.</span></span> <span data-ttu-id="d9c9f-155">Você também pode incluir opções de configuração personalizadas ou um fluxo [de](../tabs/how-to/authentication/auth-aad-sso.md)trabalho de autenticação, o que é comum nas páginas de configuração de guia.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-155">You also could include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="5-provide-a-suggested-tab-name"></a><span data-ttu-id="d9c9f-156">5. Forneça um nome de guia sugerido</span><span class="sxs-lookup"><span data-stu-id="d9c9f-156">5. Provide a suggested tab name</span></span>

<span data-ttu-id="d9c9f-157">Quando você adiciona uma guia de canal, por padrão o nome do aplicativo é exibido (por exemplo, **primeiro aplicativo).**</span><span class="sxs-lookup"><span data-stu-id="d9c9f-157">When you add a channel tab, by default the app name displays (for example, **first-app**).</span></span>

<span data-ttu-id="d9c9f-158">Isso pode ser bom dependendo do que você chama seu aplicativo, mas talvez você queira fornecer um nome que faça mais sentido no contexto de colaboração em grupo (por exemplo, Contatos **de Equipe).**</span><span class="sxs-lookup"><span data-stu-id="d9c9f-158">This may be fine depending on what you call your app, but you may want to provide a name that makes more sense in the context of group collaboration (for example, **Team Contacts**).</span></span>

1. <span data-ttu-id="d9c9f-159">Em, `TabConfig.js` vá para `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="d9c9f-159">In `TabConfig.js`, go to `microsoftTeams.settings.setSettings`.</span></span>
2. <span data-ttu-id="d9c9f-160">Adicione a `suggestedDisplayName` propriedade com o nome da guia que você deseja exibir por padrão.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-160">Add the `suggestedDisplayName` property with the tab name you want to display by default.</span></span> 
3. <span data-ttu-id="d9c9f-161">Use o nome fornecido no exemplo a seguir ou digite seu nome.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-161">Use the name provided in the following example or type your name.</span></span> <span data-ttu-id="d9c9f-162">(Por padrão, os usuários podem alterar o nome.)</span><span class="sxs-lookup"><span data-stu-id="d9c9f-162">(By default, users can change the name.)</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://localhost:3000/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="6-build-and-run-your-app"></a><span data-ttu-id="d9c9f-163">6. Crie e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d9c9f-163">6. Build and run your app</span></span>

<span data-ttu-id="d9c9f-164">No interesse de tempo, você criará e executará seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-164">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="d9c9f-165">(Essas informações também estão disponíveis no kit de `README` ferramentas.)</span><span class="sxs-lookup"><span data-stu-id="d9c9f-165">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="d9c9f-166">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e `npm install` execute.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-166">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="d9c9f-167">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="d9c9f-167">Run `npm start`.</span></span>

<span data-ttu-id="d9c9f-168">Depois de concluído, há um **compilado com êxito!**</span><span class="sxs-lookup"><span data-stu-id="d9c9f-168">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="d9c9f-169">no terminal.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-169">message in the terminal.</span></span> <span data-ttu-id="d9c9f-170">Seu aplicativo está sendo executado `https://localhost:3000` em.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-170">Your app is running on `https://localhost:3000`.</span></span>

## <a name="7-sideload-your-app-in-teams"></a><span data-ttu-id="d9c9f-171">7. Fazer sideload do aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="d9c9f-171">7. Sideload your app in Teams</span></span>

<span data-ttu-id="d9c9f-172">Seu aplicativo está pronto para ser testado no Teams.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-172">Your app is ready to test in Teams.</span></span> <span data-ttu-id="d9c9f-173">Para fazer isso, você deve ter uma conta que permita o sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-173">To do this, you must have an account that allows app sideloading.</span></span> <span data-ttu-id="d9c9f-174">(Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma conta [de desenvolvimento do Teams.)](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account)</span><span class="sxs-lookup"><span data-stu-id="d9c9f-174">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>

1. <span data-ttu-id="d9c9f-175">No Visual Studio Code, pressione a **tecla F5** para iniciar um cliente Web do Teams.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-175">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="d9c9f-176">Para exibir o conteúdo do aplicativo no Teams, especifique que onde o aplicativo está sendo executado ( `localhost` ) é confiável:</span><span class="sxs-lookup"><span data-stu-id="d9c9f-176">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="d9c9f-177">Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão) que foi aberta após pressionar **F5**.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-177">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="d9c9f-178">Vá para `https://localhost:3000/tab` a página e prossiga para a página.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-178">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="d9c9f-179">Volte para o Teams.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-179">Go back to Teams.</span></span> <span data-ttu-id="d9c9f-180">Na modalidade, selecione **Adicionar a uma equipe** ou Adicionar a um **chat** e localize um canal ou chat que você possa usar para teste.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-180">In the modal, select **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing.</span></span>
1. <span data-ttu-id="d9c9f-181">Selecione **Configurar uma guia.** A página de configuração é exibida em uma modalidade.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-181">Select **Set up a tab**. The configuration page displays in a modal.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração de guia de canal.":::
1. <span data-ttu-id="d9c9f-183">Selecione **Salvar** para configurar a guia. A página de conteúdo é exibida.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-183">Select **Save** to configure the tab. The content page displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma guia de canal com exibição de conteúdo estático.":::

## <a name="well-done"></a><span data-ttu-id="d9c9f-185">Bem feito</span><span class="sxs-lookup"><span data-stu-id="d9c9f-185">Well done</span></span>

<span data-ttu-id="d9c9f-186">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="d9c9f-186">Congratulations!</span></span> <span data-ttu-id="d9c9f-187">Você tem um aplicativo teams com uma guia para exibir conteúdo útil em canais e chats.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-187">You have a Teams app with a tab for displaying useful content in channels and chats.</span></span>

## <a name="learn-more"></a><span data-ttu-id="d9c9f-188">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="d9c9f-188">Learn more</span></span>

* <span data-ttu-id="d9c9f-189">Autenticar usuários de guia com [SSO:](../tabs/how-to/authentication/auth-aad-sso.md)se você quiser apenas usuários autorizados exibindo sua guia, configurar o SSO (single sign-on) por meio do Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="d9c9f-189">[Authenticate tab users with SSO](../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="d9c9f-190">[Inserir conteúdo de um](../tabs/how-to/add-tab.md#tab-requirements)aplicativo Web ou página da Web existente: mostramos como criar novo conteúdo para uma guia, mas você também pode carregar conteúdo de uma URL externa.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-190">[Embed content from an existing web app or webpage](../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="d9c9f-191">[Crie uma experiência de guia perfeita:](../tabs/design/tabs.md)confira as diretrizes recomendadas para projetar guias do Teams.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-191">[Create a seamless tab experience](../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="d9c9f-192">[Criar guias para dispositivos móveis:](../tabs/design/tabs-mobile.md)entenda como desenvolver guias para telefones e tablets.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-192">[Build tabs for mobile](../tabs/design/tabs-mobile.md): Understand how to develop tabs for phones and tablets.</span></span>
* [<span data-ttu-id="d9c9f-193">Usar dados do Teams com a API do Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="d9c9f-193">Utilize Teams data with the Microsoft Graph API</span></span>](https://docs.microsoft.com/graph/teams-concept-overview)
* [<span data-ttu-id="d9c9f-194">Criar uma guia sem o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="d9c9f-194">Create a tab without the toolkit</span></span>](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a><span data-ttu-id="d9c9f-195">Próxima lição</span><span class="sxs-lookup"><span data-stu-id="d9c9f-195">Next lesson</span></span>

<span data-ttu-id="d9c9f-196">Você sabe como criar uma guia para colaboração.</span><span class="sxs-lookup"><span data-stu-id="d9c9f-196">You know how to build a tab for collaboration.</span></span> <span data-ttu-id="d9c9f-197">Deseja tentar criar um tipo diferente de aplicativo do Teams?</span><span class="sxs-lookup"><span data-stu-id="d9c9f-197">Want to try building a different kind of Teams app?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d9c9f-198">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="d9c9f-198">Build a bot</span></span>](../build-your-first-app/build-bot.md)
