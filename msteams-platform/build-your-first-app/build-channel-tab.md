---
title: Introdução-criar uma guia canal e grupo
author: heath-hamilton
description: Crie rapidamente uma guia de canal e grupo do Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: bb87d34974469057287cf63725e7722125c57c34
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605242"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a><span data-ttu-id="30c8d-103">Criar uma guia de canal e grupo para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="30c8d-103">Build a channel and group tab for Microsoft Teams</span></span>

<span data-ttu-id="30c8d-104">Neste tutorial, você criará uma guia de *canal* básica (também conhecida como uma *Guia de grupo*), que é uma página de tela inteira de um canal de equipe ou bate-papo.</span><span class="sxs-lookup"><span data-stu-id="30c8d-104">In this tutorial, you'll build a basic *channel tab* (also known as a *group tab*), which is a full-screen page for a team channel or chat.</span></span> <span data-ttu-id="30c8d-105">Ao contrário de uma guia pessoal, os usuários podem configurar alguns aspectos desse tipo de guia (por exemplo, renomear a guia de forma que ela seja significativa para o canal).</span><span class="sxs-lookup"><span data-stu-id="30c8d-105">Unlike a personal tab, users can configure some aspects of this kind of tab (for example, rename the tab so it's meaningful to their channel).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="30c8d-106">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="30c8d-106">Your assignment</span></span>

<span data-ttu-id="30c8d-107">Não há muito tempo, sua organização criou um aplicativo Teams que usa uma guia para exibir informações importantes de contato (Help Desk, HR, etc.).</span><span class="sxs-lookup"><span data-stu-id="30c8d-107">Not long ago, your organization created a Teams app that uses a tab to display important contact information (help desk, HR, etc.).</span></span> <span data-ttu-id="30c8d-108">No entanto, como é uma guia pessoal, cada usuário deve instalar a guia para vê-la e a adoção é menor do que o esperado.</span><span class="sxs-lookup"><span data-stu-id="30c8d-108">However, since it's a personal tab, each user must install the tab to see it and adoption is lower than expected.</span></span> <span data-ttu-id="30c8d-109">Em outras palavras, muitos trabalhadores ainda não sabem como alcançar o suporte técnico.</span><span class="sxs-lookup"><span data-stu-id="30c8d-109">In other words, too many workers still don't know how to reach the help desk.</span></span>

<span data-ttu-id="30c8d-110">Você pode facilitar a localização dessas informações criando uma guia de canal, o que removerá o ônus de exigir que todos instalem um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30c8d-110">You can make this information easier to find by building a channel tab, which will remove the burden of requiring everyone to install an app.</span></span> <span data-ttu-id="30c8d-111">Em vez disso, um usuário pode adicionar a guia em um canal ou chat para o benefício de um grupo inteiro.</span><span class="sxs-lookup"><span data-stu-id="30c8d-111">Instead, one user can add the tab in a channel or chat for the benefit of an entire group.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="30c8d-112">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="30c8d-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="30c8d-113">Criar um projeto de aplicativo usando o Microsoft Teams Toolkit para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="30c8d-113">Create an app project using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="30c8d-114">Identificar algumas das configurações do aplicativo e scaffolding relevantes para as guias canal e grupo</span><span class="sxs-lookup"><span data-stu-id="30c8d-114">Identify some of the app configurations and scaffolding relevant to channel and group tabs</span></span>
> * <span data-ttu-id="30c8d-115">Criar conteúdo de guia</span><span class="sxs-lookup"><span data-stu-id="30c8d-115">Create tab content</span></span>
> * <span data-ttu-id="30c8d-116">Criar conteúdo para a página de configuração de uma guia</span><span class="sxs-lookup"><span data-stu-id="30c8d-116">Create content for a tab's configuration page</span></span>
> * <span data-ttu-id="30c8d-117">Fornecer um nome de guia sugerido</span><span class="sxs-lookup"><span data-stu-id="30c8d-117">Provide a suggested tab name</span></span>
> * <span data-ttu-id="30c8d-118">Criar e executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="30c8d-118">Build and run your app locally</span></span>
> * <span data-ttu-id="30c8d-119">Sideload seu aplicativo no Teams para teste</span><span class="sxs-lookup"><span data-stu-id="30c8d-119">Sideload your app in Teams for testing</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="30c8d-120">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="30c8d-120">Before you begin</span></span>

<span data-ttu-id="30c8d-121">Se você ainda não tiver feito isso, não se esqueça de [entender e instalar os pré-requisitos de desenvolvimento do teams](build-first-app-overview.md#get-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="30c8d-121">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="30c8d-122">1. criar seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="30c8d-122">1. Create your app project</span></span>

<span data-ttu-id="30c8d-123">O Microsoft Teams Toolkit ajuda a configurar seu aplicativo e configurar o scaffolding relevante para as guias canal e grupo, incluindo uma página de configuração básica e uma página de conteúdo que exibe um "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="30c8d-123">The Microsoft Teams Toolkit helps configure your app and set up scaffolding relevant to channel and group tabs, including a basic configuration page and content page that displays a "Hello, World!"</span></span> <span data-ttu-id="30c8d-124">Mensagem.</span><span class="sxs-lookup"><span data-stu-id="30c8d-124">message.</span></span>

> [!TIP]
> <span data-ttu-id="30c8d-125">Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="30c8d-125">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. <span data-ttu-id="30c8d-127">Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="30c8d-127">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="30c8d-128">Na tela **Adicionar recursos** , selecione **Tab** e **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="30c8d-128">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
1. <span data-ttu-id="30c8d-129">Insira um nome para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="30c8d-129">Enter a name for your Teams app.</span></span> <span data-ttu-id="30c8d-130">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)</span><span class="sxs-lookup"><span data-stu-id="30c8d-130">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="30c8d-131">Verifique as opções de guia **pessoal** , **grupo ou canal Teams** .</span><span class="sxs-lookup"><span data-stu-id="30c8d-131">Check the **Personal tab** and **Group or Teams channel tab** options.</span></span> <span data-ttu-id="30c8d-132">(Você saberá em breve por que precisa de ambos os tipos de guias.)</span><span class="sxs-lookup"><span data-stu-id="30c8d-132">(You'll soon learn why you need both types of tabs.)</span></span>
1. <span data-ttu-id="30c8d-133">Selecione **concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="30c8d-133">Select **Finish** at the bottom of the screen to configure your project.</span></span>  

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="30c8d-134">2. identificar componentes de projeto de aplicativo relevantes</span><span class="sxs-lookup"><span data-stu-id="30c8d-134">2. Identify relevant app project components</span></span>

<span data-ttu-id="30c8d-135">Grande parte das configurações do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="30c8d-135">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="30c8d-136">Vamos examinar os principais componentes para a criação de uma guia canal e grupo.</span><span class="sxs-lookup"><span data-stu-id="30c8d-136">Let's look at the main components for building a channel and group tab.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="30c8d-137">Configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="30c8d-137">App configurations</span></span>

<span data-ttu-id="30c8d-138">Você pode exibir e atualizar suas configurações de aplicativo usando o app Studio, que está incluído no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="30c8d-138">You can view and update your app configurations using App Studio, which is included in the toolkit.</span></span>

<span data-ttu-id="30c8d-139">Durante a instalação, o kit de ferramentas configurou inicialmente dois componentes essenciais de guias de canal e Grupo:</span><span class="sxs-lookup"><span data-stu-id="30c8d-139">During setup, the toolkit initially configured two essential components of channel and group tabs:</span></span>

* <span data-ttu-id="30c8d-140">**Página de configuração**: a janela restrita para adicionar uma guia a um canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="30c8d-140">**Configuration page**: The modal for adding a tab to a channel or chat.</span></span> <span data-ttu-id="30c8d-141">(No app Studio, você pode encontrar esta página acessando **guias > equipe**.)</span><span class="sxs-lookup"><span data-stu-id="30c8d-141">(In App Studio, you can find this page by going to **Tabs > Team tab**.)</span></span>
* <span data-ttu-id="30c8d-142">**Página de conteúdo**: onde você exibe o conteúdo principal.</span><span class="sxs-lookup"><span data-stu-id="30c8d-142">**Content page**: Where you display your primary content.</span></span> <span data-ttu-id="30c8d-143">(No app Studio, você pode encontrar esta página acessando **guias > adicionar uma guia pessoal**.)</span><span class="sxs-lookup"><span data-stu-id="30c8d-143">(In App Studio, you can find this page by going to **Tabs > Add a personal tab**.)</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="30c8d-144">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="30c8d-144">App scaffolding</span></span>

<span data-ttu-id="30c8d-145">O aplicativo scaffolding fornece os componentes para renderizar sua guia pessoal no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="30c8d-145">The app scaffolding provides the components for rendering your personal tab in Teams.</span></span> <span data-ttu-id="30c8d-146">Há muitas coisas com as quais você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:</span><span class="sxs-lookup"><span data-stu-id="30c8d-146">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="30c8d-147">Dois arquivos localizados no `src/components` diretório do projeto:</span><span class="sxs-lookup"><span data-stu-id="30c8d-147">Two files located in the `src/components` directory of your project:</span></span>
  * <span data-ttu-id="30c8d-148">`Tab.js` para renderizar a página de conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="30c8d-148">`Tab.js` for rendering your tab's content page.</span></span>
  * <span data-ttu-id="30c8d-149">`TabConfig.js` para renderizar a página de configuração da guia.</span><span class="sxs-lookup"><span data-stu-id="30c8d-149">`TabConfig.js` for rendering your tab's configuration page.</span></span>
* <span data-ttu-id="30c8d-150">SDK do cliente JavaScript do Microsoft Teams, que vem pré-carregado nos componentes de front-end do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="30c8d-150">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="3-customize-your-tab-content-page"></a><span data-ttu-id="30c8d-151">3. personalizar a página de conteúdo da guia</span><span class="sxs-lookup"><span data-stu-id="30c8d-151">3. Customize your tab content page</span></span>

<span data-ttu-id="30c8d-152">Copie e atualize o trecho de código a seguir, com informações relevantes para a sua organização ou, para fins de tempo, use o código como está.</span><span class="sxs-lookup"><span data-stu-id="30c8d-152">Copy and update the following snippet with information that's relevant to your organization or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="30c8d-153">Vá para o `src/components` diretório e abra `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="30c8d-153">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="30c8d-154">Localize a `render()` função e cole o conteúdo dentro `return()` (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="30c8d-154">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="30c8d-155">Adicione a seguinte regra a `App.css` (também localizada `src/components` ) para que os links de email sejam mais fáceis de ler, independentemente de qual tema é usado.</span><span class="sxs-lookup"><span data-stu-id="30c8d-155">Add the following rule to `App.css` (also located in `src/components`) so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a><span data-ttu-id="30c8d-156">4. personalizar a página de configuração da guia</span><span class="sxs-lookup"><span data-stu-id="30c8d-156">4. Customize your tab configuration page</span></span>

<span data-ttu-id="30c8d-157">Cada guia em um canal ou chat tem uma página de configuração, uma janela restrita com pelo menos uma opção de configuração exibida quando os usuários adicionam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30c8d-157">Every tab in a channel or chat has a configuration page, a modal with at least one setup option that displays when users add your app.</span></span> <span data-ttu-id="30c8d-158">A página de configuração, por padrão, pergunta aos usuários se eles desejam notificar o canal ou chat quando a guia é instalada.</span><span class="sxs-lookup"><span data-stu-id="30c8d-158">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span>

<span data-ttu-id="30c8d-159">Adicione um conteúdo personalizado à sua página de configuração.</span><span class="sxs-lookup"><span data-stu-id="30c8d-159">Add some custom content to your configuration page.</span></span> <span data-ttu-id="30c8d-160">Vá para o diretório do seu projeto `src/components` , abra `TabConfig.js` e atualize o conteúdo do espaço reservado dentro `return()` (conforme mostrado no exemplo a seguir).</span><span class="sxs-lookup"><span data-stu-id="30c8d-160">Go to your project's `src/components` directory, open `TabConfig.js`, and update the placeholder content inside `return()` (as shown in the following example).</span></span>

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
> <span data-ttu-id="30c8d-161">No mínimo, forneça algumas breves informações sobre o aplicativo nesta página, pois essa pode ser a primeira vez que os usuários estão aprendendo.</span><span class="sxs-lookup"><span data-stu-id="30c8d-161">At minimum, provide some brief information about your app on this page since this may be the first time users are learning about it.</span></span> <span data-ttu-id="30c8d-162">Você também pode incluir opções de configuração personalizada ou um [fluxo de trabalho de autenticação](../tabs/how-to/authentication/auth-aad-sso.md), que é comum nas páginas de configuração da guia.</span><span class="sxs-lookup"><span data-stu-id="30c8d-162">You also could include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="5-provide-a-suggested-tab-name"></a><span data-ttu-id="30c8d-163">5. forneça um nome de guia sugerido</span><span class="sxs-lookup"><span data-stu-id="30c8d-163">5. Provide a suggested tab name</span></span>

<span data-ttu-id="30c8d-164">Quando você adiciona uma guia de canal ou grupo, por padrão, o nome do aplicativo é exibido (por exemplo, **First-app**).</span><span class="sxs-lookup"><span data-stu-id="30c8d-164">When you add a channel or group tab, by default the app name displays (for example, **first-app**).</span></span>

<span data-ttu-id="30c8d-165">Isso pode ser bem, dependendo do que você chama no seu aplicativo, mas talvez você queira fornecer um nome que faça mais sentido no contexto de colaboração de grupo (por exemplo, **contatos da equipe**).</span><span class="sxs-lookup"><span data-stu-id="30c8d-165">This may be fine depending on what you call your app, but you may want to provide a name that makes more sense in the context of group collaboration (for example, **Team Contacts**).</span></span>

<span data-ttu-id="30c8d-166">No `TabConfig.js` , vá para `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="30c8d-166">In `TabConfig.js`, go to `microsoftTeams.settings.setSettings`.</span></span> <span data-ttu-id="30c8d-167">Adicione a `suggestedDisplayName` propriedade com o nome da guia que você deseja exibir por padrão (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="30c8d-167">Add the `suggestedDisplayName` property with the tab name you want to display by default (as shown).</span></span> <span data-ttu-id="30c8d-168">Use o nome fornecido ou crie o seu próprio.</span><span class="sxs-lookup"><span data-stu-id="30c8d-168">Use the provided name or create your own.</span></span> <span data-ttu-id="30c8d-169">(Por padrão, os usuários podem alterar o nome se desejarem).</span><span class="sxs-lookup"><span data-stu-id="30c8d-169">(By default, users to change the name if they want.)</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://localhost:3000/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="6-build-and-run-your-app"></a><span data-ttu-id="30c8d-170">6. Compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="30c8d-170">6. Build and run your app</span></span>

<span data-ttu-id="30c8d-171">Nos juros de tempo, você criará e executará seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="30c8d-171">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="30c8d-172">(Essas informações também estão disponíveis no kit de ferramentas `README` .)</span><span class="sxs-lookup"><span data-stu-id="30c8d-172">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="30c8d-173">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="30c8d-173">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="30c8d-174">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="30c8d-174">Run `npm start`.</span></span>

<span data-ttu-id="30c8d-175">Após a conclusão, há uma **compilação bem-sucedida!**</span><span class="sxs-lookup"><span data-stu-id="30c8d-175">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="30c8d-176">mensagem no terminal.</span><span class="sxs-lookup"><span data-stu-id="30c8d-176">message in the terminal.</span></span> <span data-ttu-id="30c8d-177">O aplicativo está sendo executado `https://localhost:3000` .</span><span class="sxs-lookup"><span data-stu-id="30c8d-177">Your app is running on `https://localhost:3000`.</span></span>

## <a name="7-sideload-your-app-in-teams"></a><span data-ttu-id="30c8d-178">7. Sideload seu aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="30c8d-178">7. Sideload your app in Teams</span></span>

<span data-ttu-id="30c8d-179">Seu aplicativo está pronto para teste no Teams.</span><span class="sxs-lookup"><span data-stu-id="30c8d-179">Your app is ready to test in Teams.</span></span> <span data-ttu-id="30c8d-180">Para fazer isso, você deve ter uma conta que permita o aplicativo Sideload.</span><span class="sxs-lookup"><span data-stu-id="30c8d-180">To do this, you must have an account that allows app sideloading.</span></span> <span data-ttu-id="30c8d-181">(Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma [conta de desenvolvimento do teams](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span><span class="sxs-lookup"><span data-stu-id="30c8d-181">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>

1. <span data-ttu-id="30c8d-182">No Visual Studio Code, pressione a tecla **F5** para iniciar um cliente Web do teams.</span><span class="sxs-lookup"><span data-stu-id="30c8d-182">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="30c8d-183">Para exibir o conteúdo do aplicativo no Teams, especifique o local em que o aplicativo está em execução ( `localhost` ) é confiável:</span><span class="sxs-lookup"><span data-stu-id="30c8d-183">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="30c8d-184">Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão), aberta após pressionar **F5**.</span><span class="sxs-lookup"><span data-stu-id="30c8d-184">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="30c8d-185">Vá até `https://localhost:3000/tab` a página e vá até ela.</span><span class="sxs-lookup"><span data-stu-id="30c8d-185">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="30c8d-186">Volte para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="30c8d-186">Go back to Teams.</span></span> <span data-ttu-id="30c8d-187">Na janela restrita, selecione **Adicionar a uma equipe** ou **Adicionar a um chat** e localize um canal ou chat que você possa usar para teste.</span><span class="sxs-lookup"><span data-stu-id="30c8d-187">In the modal, select **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing.</span></span>
1. <span data-ttu-id="30c8d-188">Selecione **Configurar uma guia**. A página de configuração é exibida em uma janela restrita.</span><span class="sxs-lookup"><span data-stu-id="30c8d-188">Select **Set up a tab**. The configuration page displays in a modal.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração da guia canal.":::
1. <span data-ttu-id="30c8d-190">Selecione **salvar** para configurar a guia. A página de conteúdo é exibida.</span><span class="sxs-lookup"><span data-stu-id="30c8d-190">Select **Save** to configure the tab. The content page displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma guia canal com visualização de conteúdo estático.":::

## <a name="well-done"></a><span data-ttu-id="30c8d-192">Muito bem</span><span class="sxs-lookup"><span data-stu-id="30c8d-192">Well done</span></span>

<span data-ttu-id="30c8d-193">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="30c8d-193">Congratulations!</span></span> <span data-ttu-id="30c8d-194">Você tem um aplicativo do teams com uma guia para exibir conteúdo útil em canais e chats.</span><span class="sxs-lookup"><span data-stu-id="30c8d-194">You have a Teams app with a tab for displaying useful content in channels and chats.</span></span>

## <a name="learn-more"></a><span data-ttu-id="30c8d-195">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="30c8d-195">Learn more</span></span>

* <span data-ttu-id="30c8d-196">[Guia autenticar usuários com SSO](../tabs/how-to/authentication/auth-aad-sso.md): se você quiser apenas que usuários autorizados exibam sua guia, configure o logon único (SSO) por meio do Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="30c8d-196">[Authenticate tab users with SSO](../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="30c8d-197">[Inserir conteúdo de um aplicativo Web existente ou página da Web](../tabs/how-to/add-tab.md#tab-requirements): mostramos como criar novo conteúdo para uma guia pessoal, mas você também pode carregar o conteúdo de uma URL externa.</span><span class="sxs-lookup"><span data-stu-id="30c8d-197">[Embed content from an existing web app or webpage](../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="30c8d-198">[Criar uma experiência perfeita para sua guia](../tabs/design/tabs.md): consulte as diretrizes recomendadas para a criação de guias do teams.</span><span class="sxs-lookup"><span data-stu-id="30c8d-198">[Create a seamless experience for your tab](../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="30c8d-199">[Criar guias para celular](../tabs/design/tabs-mobile.md): entenda como desenvolver guias para telefones e tablets.</span><span class="sxs-lookup"><span data-stu-id="30c8d-199">[Build tabs for mobile](../tabs/design/tabs-mobile.md): Understand how to develop tabs for phones and tablets.</span></span>
* [<span data-ttu-id="30c8d-200">Usar os dados do teams com a API do Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="30c8d-200">Utilize Teams data with the Microsoft Graph API</span></span>](https://docs.microsoft.com/graph/teams-concept-overview)
* [<span data-ttu-id="30c8d-201">Criar uma guia sem o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="30c8d-201">Create a tab without the toolkit</span></span>](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a><span data-ttu-id="30c8d-202">Próxima lição</span><span class="sxs-lookup"><span data-stu-id="30c8d-202">Next lesson</span></span>

<span data-ttu-id="30c8d-203">Você sabe como criar uma guia para colaboração.</span><span class="sxs-lookup"><span data-stu-id="30c8d-203">You know how to build a tab for collaboration.</span></span> <span data-ttu-id="30c8d-204">Deseja tentar criar um tipo diferente de aplicativo do teams?</span><span class="sxs-lookup"><span data-stu-id="30c8d-204">Want to try building a different kind of Teams app?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="30c8d-205">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="30c8d-205">Build a bot</span></span>](../build-your-first-app/build-bot.md)
