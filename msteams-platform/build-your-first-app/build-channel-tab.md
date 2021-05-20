---
title: Comece - Construa um canal e uma guia de grupo
author: girliemac
description: Crie rapidamente uma guia de canal e grupo Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/22/2020
ms.topic: tutorial
ms.openlocfilehash: ff9cfbfb7d099db52966f119add4ce8729929aa1
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566065"
---
# <a name="build-your-first-channel-and-group-tab-for-microsoft-teams"></a><span data-ttu-id="5a1e1-103">Crie seu primeiro canal e guia de grupo para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5a1e1-103">Build your first channel and group tab for Microsoft Teams</span></span>

<span data-ttu-id="5a1e1-104">Este tutorial ensina você a construir uma guia básica *de canal* também conhecida como guia *de grupo,* que é uma página em tela cheia para um canal de equipe ou bate-papo.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-104">This tutorial teaches you to build a basic *channel tab* also known as a *group tab*, which is a full-screen page for a team channel or chat.</span></span> <span data-ttu-id="5a1e1-105">Você também pode configurar alguns aspectos desse tipo de guia, por exemplo, renomear a guia para que seja significativa para o canal deles, o que você não pode fazer em uma Guia Pessoal.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-105">You can also configure some aspects of this kind of tab, for example, rename the tab so it's meaningful to their channel, which you cannot do in a Personal Tab.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="5a1e1-106">O que você vai aprender</span><span class="sxs-lookup"><span data-stu-id="5a1e1-106">What you'll learn</span></span>

* <span data-ttu-id="5a1e1-107">Crie um projeto de aplicativo usando o Microsoft Teams Toolkit para Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-107">Create an app project using the Microsoft Teams Toolkit for Visual Studio Code.</span></span>
* <span data-ttu-id="5a1e1-108">Entenda as configurações do aplicativo e andaimes relevantes para as guias do canal.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-108">Understand the app configurations and scaffolding relevant to channel tabs.</span></span>
* <span data-ttu-id="5a1e1-109">Criar conteúdo de guia e configuração de guia.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-109">Create tab content and tab configuration.</span></span>
* <span data-ttu-id="5a1e1-110">Construa e execute seu aplicativo em equipes para testes.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-110">Build and run your app in teams for testing.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5a1e1-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5a1e1-111">Prerequisites</span></span>

<span data-ttu-id="5a1e1-112">Certifique-se de entender como configurar e construir um aplicativo de Teams simples.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-112">Make sure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="5a1e1-113">Para obter mais informações, consulte [criar seu primeiro Microsoft Teams aplicativo "Hello, World!".](../build-your-first-app/build-and-run.md)</span><span class="sxs-lookup"><span data-stu-id="5a1e1-113">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="5a1e1-114">1. Crie seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="5a1e1-114">1. Create your app project</span></span>

<span data-ttu-id="5a1e1-115">O Microsoft Teams Toolkit ajuda você a configurar seu aplicativo e configurar os andaimes relevantes para as guias de canais e grupos.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-115">The Microsoft Teams Toolkit helps you to configure your app and set up the scaffolding relevant to channel and group tabs.</span></span> <span data-ttu-id="5a1e1-116">Ele também contém uma página de configuração básica e uma página de conteúdo que exibe um "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="5a1e1-116">It also contains a basic configuration page and content page that displays a "Hello, World!"</span></span> <span data-ttu-id="5a1e1-117">Mensagem.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-117">message.</span></span>

<span data-ttu-id="5a1e1-118">**Para criar seu projeto de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="5a1e1-118">**To create your app project**</span></span>

1. Vá para Visual Studio Code e selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na Barra de Atividades esquerda.
1. <span data-ttu-id="5a1e1-120">Faça login com sua conta de desenvolvimento Microsoft 365 quando solicitado a fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-120">Sign in with your Microsoft 365 development account when prompted to do so.</span></span>
1. <span data-ttu-id="5a1e1-121">Na tela do **projeto Select,** selecione **JS** (JavaScript) no **aplicativo de canal e grupo**.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-121">On the **Select project** screen, select **JS** (JavaScript) under **Channel and group app**.</span></span>
1. <span data-ttu-id="5a1e1-122">Digite um nome para o aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-122">Enter a name for your Teams app.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="5a1e1-123">Este é o nome padrão do seu aplicativo e também o nome do diretório de projetos do aplicativo em sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-123">This is the default name for your app and also the name of the app project directory on your local machine.</span></span>

1. <span data-ttu-id="5a1e1-124">Selecione **a guia Grupo ou Teams de canais**.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-124">Select **Group or Teams channel tab**.</span></span>
1. <span data-ttu-id="5a1e1-125">Selecione **Concluir** na parte inferior da tela para configurar seu projeto e salvar seu projeto em sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-125">Select **Finish** at the bottom of the screen to configure your project and save your project on your local machine.</span></span>  

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="5a1e1-126">2. Entenda os componentes do projeto do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="5a1e1-126">2. Understand your app project components</span></span>

<span data-ttu-id="5a1e1-127">Muitas das configurações e andaimes do aplicativo são configuradas automaticamente quando você cria seu projeto com o kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-127">Much of the app configurations and scaffolding are set up automatically when you create your project with the toolkit.</span></span> <span data-ttu-id="5a1e1-128">Vejamos os principais componentes para a construção de uma guia de canal.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-128">Let's look at the main components for building a channel tab.</span></span>

* <span data-ttu-id="5a1e1-129">**Configurações do** aplicativo : Abra o **App Studio** no kit de ferramentas para visualizar e atualizar as configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-129">**App configurations**: Open **App Studio** in the toolkit to view and update your app configurations.</span></span>
* <span data-ttu-id="5a1e1-130">**Andaimes de** aplicativos : O andaime do aplicativo fornece os componentes necessários para renderizar sua guia de canal em Teams.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-130">**App scaffolding**: The app scaffolding provides the components needed for rendering your channel tab in Teams.</span></span> <span data-ttu-id="5a1e1-131">Há muita coisa com que você pode trabalhar, no entanto, por enquanto, vamos nos concentrar no seguinte:</span><span class="sxs-lookup"><span data-stu-id="5a1e1-131">There's a lot you can work with, however, for now let's focus on the following:</span></span>
  * <span data-ttu-id="5a1e1-132">Os arquivos localizados no `src/components` diretório do seu projeto:</span><span class="sxs-lookup"><span data-stu-id="5a1e1-132">The files located in the `src/components` directory of your project:</span></span>
    * <span data-ttu-id="5a1e1-133">`Tab.js` para renderizar a página de conteúdo da sua guia.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-133">`Tab.js` for rendering your tab's content page.</span></span>
    * <span data-ttu-id="5a1e1-134">`TabConfig.js` para renderizar a página de configuração da sua guia.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-134">`TabConfig.js` for rendering your tab's configuration page.</span></span>
  * <span data-ttu-id="5a1e1-135">Microsoft Teams Cliente JavaScript SDK, que vem pré-carregado nos componentes front-end do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-135">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="3-customize-your-tab-content-page"></a><span data-ttu-id="5a1e1-136">3. Personalize sua página de conteúdo de guia</span><span class="sxs-lookup"><span data-stu-id="5a1e1-136">3. Customize your tab content page</span></span>

1. <span data-ttu-id="5a1e1-137">Copie e modifique a seguinte amostra de código com informações relevantes para sua organização.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-137">Copy and modify the following code sample with information that's relevant to your organization.</span></span> <span data-ttu-id="5a1e1-138">Você também pode usar o trecho como ele é:</span><span class="sxs-lookup"><span data-stu-id="5a1e1-138">You can also use the snippet as it is:</span></span>
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
    
1. <span data-ttu-id="5a1e1-139">Vá ao `src/components` diretório e abra o `Tab.js` arquivo.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-139">Go to the `src/components` directory and open the `Tab.js` file.</span></span> <span data-ttu-id="5a1e1-140">Localize a `render()` função e cole seu código no `return()` interior, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5a1e1-140">Locate the `render()` function and paste your code inside `return()` as shown in the following example:</span></span>
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
    
1. <span data-ttu-id="5a1e1-141">Vá para o `src/components` diretório e atualize o `App.css` arquivo com o seguinte código para tornar os links de e-mail mais fáceis de ler em qualquer tema que seja usado:</span><span class="sxs-lookup"><span data-stu-id="5a1e1-141">Go to the `src/components` directory and update the `App.css` file with the following code to make the email links easier to read in any theme that is used:</span></span>
    ```CSS
    a {
      color: inherit;
    }
    ```

## <a name="4-customize-your-tab-configuration-page"></a><span data-ttu-id="5a1e1-142">4. Personalize sua página de configuração de guia</span><span class="sxs-lookup"><span data-stu-id="5a1e1-142">4. Customize your tab configuration page</span></span>

<span data-ttu-id="5a1e1-143">Cada guia em um canal ou chat tem uma página de configuração, um modal com pelo menos uma opção de configuração que é exibida quando os usuários adicionam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-143">Every tab in a channel or chat has a configuration page, a modal with at least one setup option that displays when users add your app.</span></span> <span data-ttu-id="5a1e1-144">A página de configuração por padrão pergunta aos usuários se eles querem notificar o canal ou o chat quando a guia estiver instalada.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-144">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span> <span data-ttu-id="5a1e1-145">Você pode personalizar a página de configuração adicionando conteúdo personalizado.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-145">You can customize the configuration page by adding custom content.</span></span>

<span data-ttu-id="5a1e1-146">Para adicionar conteúdo personalizado, abra `TabConfig.js` o arquivo do diretório e `src/components` atualize o conteúdo do espaço reservado `return()` dentro, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5a1e1-146">To add custom content, open `TabConfig.js` file from the `src/components` directory and update the placeholder content inside `return()` as shown in the following example:</span></span>

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
> <span data-ttu-id="5a1e1-147">Dê uma breve informação sobre seu aplicativo nesta página, já que esta seria a primeira vez que os usuários estão lendo sobre ele.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-147">Give a brief information about your app on this page since this would be the first time users are reading about it.</span></span> <span data-ttu-id="5a1e1-148">Você também pode incluir opções de configuração personalizadas ou um [fluxo de trabalho de autenticação,](../tabs/how-to/authentication/auth-aad-sso.md)o que é comum em páginas de configuração de guias.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-148">You can also include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="5-customize-your-tab-name"></a><span data-ttu-id="5a1e1-149">5. Personalize seu nome de guia</span><span class="sxs-lookup"><span data-stu-id="5a1e1-149">5. Customize your tab name</span></span>

<span data-ttu-id="5a1e1-150">Quando você adiciona uma guia de canal, o nome do aplicativo é exibido por padrão, por exemplo, **primeiro aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-150">When you add a channel tab, the app name displays by default, for example, **first-app**.</span></span> <span data-ttu-id="5a1e1-151">Você também pode fornecer um nome que faça mais sentido no contexto da colaboração em grupo, por exemplo, **Contatos de Equipe**:</span><span class="sxs-lookup"><span data-stu-id="5a1e1-151">You can also provide a name that makes more sense in the context of group collaboration, for example, **Team Contacts**:</span></span>

1. <span data-ttu-id="5a1e1-152">Vá ao `src/components` diretório e abra o `TabConfig.js` arquivo.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-152">Go to the `src/components` directory and open the `TabConfig.js` file.</span></span>
1. <span data-ttu-id="5a1e1-153">Adicione a `suggestedDisplayName` propriedade com o nome da guia que deseja exibir por `microsoftTeams.settings.setSettings` padrão, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5a1e1-153">Add the `suggestedDisplayName` property with the tab name you want to display by default under `microsoftTeams.settings.setSettings` as shown in the following example:</span></span>

    ```JavaScript
        microsoftTeams.settings.setSettings({
        "contentUrl": "https://localhost:3000/tab",
        "suggestedDisplayName": "Team Contacts"
      });
      ```

## <a name="6-build-and-run-your-app"></a><span data-ttu-id="5a1e1-154">6. Construa e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="5a1e1-154">6. Build and run your app</span></span>

<span data-ttu-id="5a1e1-155">Este tutorial ensina você a construir e executar seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-155">This tutorial teaches you to build and run your app locally.</span></span> 

1. <span data-ttu-id="5a1e1-156">Vá para o diretório raiz do seu projeto de aplicativo no Terminal.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-156">Go to the root directory of your app project in Terminal.</span></span>
1. <span data-ttu-id="5a1e1-157">`npm install`Corra.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-157">Run `npm install`.</span></span>
1. <span data-ttu-id="5a1e1-158">`npm start`Corra.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-158">Run `npm start`.</span></span>

<span data-ttu-id="5a1e1-159">Essas informações também estão presentes na `README` seção do kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-159">This information is also present in the `README` section of the toolkit.</span></span>
<span data-ttu-id="5a1e1-160">Seu aplicativo está sendo executado `https://localhost:3000` após o Compilado com **sucesso!**</span><span class="sxs-lookup"><span data-stu-id="5a1e1-160">Your app is running on `https://localhost:3000` after the **Compiled successfully!**</span></span> <span data-ttu-id="5a1e1-161">mensagem aparece no terminal.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-161">message appears in the terminal.</span></span> 

## <a name="7-sideload-your-app-in-teams"></a><span data-ttu-id="5a1e1-162">7. Carregar lateralmente seu aplicativo em Teams</span><span class="sxs-lookup"><span data-stu-id="5a1e1-162">7. Sideload your app in Teams</span></span>

<span data-ttu-id="5a1e1-163">Seu aplicativo está pronto para testar em Teams.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-163">Your app is ready to test in Teams.</span></span> <span data-ttu-id="5a1e1-164">Para fazer isso, você deve ter uma conta que permita o sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-164">To do this, you must have an account that allows app sideloading.</span></span> 

1. <span data-ttu-id="5a1e1-165">Abra um cliente web Teams em Visual Studio Code com a chave **F5.**</span><span class="sxs-lookup"><span data-stu-id="5a1e1-165">Open a Teams web client in Visual Studio Code with the **F5** key.</span></span>
1. <span data-ttu-id="5a1e1-166">Adicione ( `localhost` ) como confiável seguindo essas etapas para permitir que o conteúdo do aplicativo será exibido em Teams:</span><span class="sxs-lookup"><span data-stu-id="5a1e1-166">Add (`localhost`) as trustworthy by following these steps to enable your app content to display in Teams:</span></span>

   1. <span data-ttu-id="5a1e1-167">Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão) que abriu com a tecla **F5.**</span><span class="sxs-lookup"><span data-stu-id="5a1e1-167">Open a new tab in the same browser window (Google Chrome by default) which opened with the **F5** key.</span></span>
   1. <span data-ttu-id="5a1e1-168">Abra `https://localhost:3000/tab` e siga para a página.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-168">Open `https://localhost:3000/tab` and proceed to the page.</span></span>

1. <span data-ttu-id="5a1e1-169">Selecione **Adicionar a uma equipe** ou Adicionar a um **chat** e localizar um canal ou chat que você pode usar para testar a partir do modal em Teams.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-169">Select **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing from the modal in Teams.</span></span>
1. <span data-ttu-id="5a1e1-170">Selecione **Configurar uma guia**. A página de configuração é exibida em um modal.</span><span class="sxs-lookup"><span data-stu-id="5a1e1-170">Select **Set up a tab**. The configuration page displays in a modal.</span></span>

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração de guia de canal.":::

1. <span data-ttu-id="5a1e1-172">Selecione **Salvar** para configurar a guia. A seguinte página de conteúdo é exibida:</span><span class="sxs-lookup"><span data-stu-id="5a1e1-172">Select **Save** to configure the tab. The following content page appears:</span></span>

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma guia de canal com exibição de conteúdo estático.":::

## <a name="see-also"></a><span data-ttu-id="5a1e1-174">Confira também</span><span class="sxs-lookup"><span data-stu-id="5a1e1-174">See also</span></span>

* [<span data-ttu-id="5a1e1-175">Construa e execute seu primeiro aplicativo de Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5a1e1-175">Build and run your first Microsoft Teams app</span></span>](../build-your-first-app/build-and-run.md) 
* [<span data-ttu-id="5a1e1-176">SDK do cliente JavaScript do Teams</span><span class="sxs-lookup"><span data-stu-id="5a1e1-176">Teams JavaScript client SDK</span></span>](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [<span data-ttu-id="5a1e1-177">Projetando sua guia para Microsoft Teams desktop e web</span><span class="sxs-lookup"><span data-stu-id="5a1e1-177">Designing your tab for Microsoft Teams desktop and web</span></span>](../tabs/design/tabs.md) 
* [<span data-ttu-id="5a1e1-178">Projetando seu aplicativo de Microsoft Teams com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5a1e1-178">Designing your Microsoft Teams app with UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md) 
* [<span data-ttu-id="5a1e1-179">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="5a1e1-179">Tabs on mobile</span></span>](../tabs/design/tabs-mobile.md)
* [<span data-ttu-id="5a1e1-180">Suporte de login único (SSO) para guias</span><span class="sxs-lookup"><span data-stu-id="5a1e1-180">Single sign-on (SSO) support for tabs</span></span>](../tabs/how-to/authentication/auth-aad-sso.md)
* [<span data-ttu-id="5a1e1-181">Visão geral da API do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5a1e1-181">Microsoft Teams API overview</span></span>](/graph/teams-concept-overview)
* [<span data-ttu-id="5a1e1-182">Crie uma guia pessoal personalizada com Node.js e o Gerador Yeoman para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5a1e1-182">Create a custom personal tab with Node.js and the Yeoman Generator for Microsoft Teams</span></span>](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a><span data-ttu-id="5a1e1-183">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="5a1e1-183">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5a1e1-184">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="5a1e1-184">Build a bot</span></span>](../build-your-first-app/build-bot.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="5a1e1-185">Construir uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="5a1e1-185">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
