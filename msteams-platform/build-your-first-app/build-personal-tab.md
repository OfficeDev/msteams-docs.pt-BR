---
title: Começar - Criar uma guia pessoal
author: girliemac
description: Crie rapidamente uma guia pessoal do Microsoft Teams usando o microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/16/2020
ms.topic: tutorial
ms.openlocfilehash: 05ef9913e338a54c7e6ebc301825b27d4bec9705
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068574"
---
# <a name="build-a-basic-personal-tab-for-microsoft-teams"></a><span data-ttu-id="1a7ae-103">Criar uma guia pessoal básica para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1a7ae-103">Build a basic personal tab for Microsoft Teams</span></span>

<span data-ttu-id="1a7ae-104">Este tutorial ensina você a criar uma guia pessoal básica no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-104">This tutorial teaches you to build a basic personal tab in Microsoft Teams.</span></span> <span data-ttu-id="1a7ae-105">As guias são uma maneira simples de surgir informações em seu aplicativo hospedando conteúdo da Web no Teams.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-105">Tabs are a simple way to surface information in your app by hosting web content in Teams.</span></span> <span data-ttu-id="1a7ae-106">Guias são um recurso comum de aplicativos pessoais que fornecem um espaço de trabalho privado para usuários individuais.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-106">Tabs are a common feature of personal apps that provide a private workspace for individual users.</span></span> <span data-ttu-id="1a7ae-107">As guias pessoais são a coisa mais próxima de uma experiência da Web tradicional no Teams.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-107">Personal tabs are the closest thing to a traditional web experience in Teams.</span></span> 

## <a name="what-youll-learn"></a><span data-ttu-id="1a7ae-108">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="1a7ae-108">What you'll learn</span></span>

* <span data-ttu-id="1a7ae-109">Entenda as configurações do aplicativo e os scaffolding relevantes para as guias pessoais.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-109">Understand the app configurations and scaffolding relevant to personal tabs.</span></span>
* <span data-ttu-id="1a7ae-110">Crie um conteúdo de guia com uma lista de contatos da sua organização.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-110">Create a tab content with a contact list of your organization.</span></span>
* <span data-ttu-id="1a7ae-111">Atualize o tema de cor de uma guia com base na preferência do usuário.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-111">Update a tab's color theme based on user preference.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1a7ae-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1a7ae-112">Prerequisites</span></span>

<span data-ttu-id="1a7ae-113">Certifique-se de entender como configurar e criar um aplicativo simples do Teams.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-113">Make sure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="1a7ae-114">Para obter mais informações, [consulte criar seu primeiro aplicativo do Microsoft Teams "Hello, World!".](../build-your-first-app/build-and-run.md)</span><span class="sxs-lookup"><span data-stu-id="1a7ae-114">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="1-understand-your-app-project-components"></a><span data-ttu-id="1a7ae-115">1. Entenda os componentes do projeto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="1a7ae-115">1. Understand your app project components</span></span>

<span data-ttu-id="1a7ae-116">Depois de criar uma guia pessoal básica, o scaffold de aplicativo gerado fornece os componentes para renderizar sua guia pessoal no Teams.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-116">After you have created a basic personal tab, the generated app scaffold provides the components for rendering your personal tab in Teams.</span></span> <span data-ttu-id="1a7ae-117">Há muito com o que você pode trabalhar, mas, por enquanto, vamos nos concentrar no seguinte:</span><span class="sxs-lookup"><span data-stu-id="1a7ae-117">There's a lot you can work with, but for now let us focus on the following:</span></span> 

* <span data-ttu-id="1a7ae-118">`Tab.js` no diretório `src/components` do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-118">`Tab.js` file in the `src/components` directory of your project.</span></span> <span data-ttu-id="1a7ae-119">Isso é para renderizar sua página de conteúdo de tabulação.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-119">This is for rendering your tab content page.</span></span>
* <span data-ttu-id="1a7ae-120">SDK do cliente JavaScript do Microsoft Teams, que é pré-carregado nos componentes front-end do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-120">Microsoft Teams JavaScript client SDK, which is pre-loaded in your project's front-end components.</span></span>

<span data-ttu-id="1a7ae-121">Como você pode observar na seção na parte superior do arquivo, o código de exemplo usa React , uma biblioteca JavaScript de código aberto para criar `import` `Tabs.js` a interface do usuário. [](https://reactjs.org/)</span><span class="sxs-lookup"><span data-stu-id="1a7ae-121">As you may notice from the `import` section at the top of `Tabs.js` file, the sample code uses [React](https://reactjs.org/), an open-source JavaScript library for building user-interface.</span></span> 

> [!NOTE]
> <span data-ttu-id="1a7ae-122">Embora o uso do React _não seja_ necessário para o desenvolvimento do Teams, este tutorial ensina você com React.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-122">Although using React is _not_ required for Teams development, this tutorial teaches you with React.</span></span>

## <a name="2-customize-your-tab-content-page"></a><span data-ttu-id="1a7ae-123">2. Personalizar sua página de conteúdo de tabulação</span><span class="sxs-lookup"><span data-stu-id="1a7ae-123">2. Customize your tab content page</span></span>

<span data-ttu-id="1a7ae-124">Você pode personalizar sua página de conteúdo de tabulação para renderizar uma lista de contatos importantes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-124">You can customize your tab content page to render a list of important contacts in your organization.</span></span> 

<span data-ttu-id="1a7ae-125">**Para personalizar sua página de conteúdo de tabulação**</span><span class="sxs-lookup"><span data-stu-id="1a7ae-125">**To customize your tab content page**</span></span>

1. <span data-ttu-id="1a7ae-126">Copie e modifique o exemplo de código a seguir com informações relevantes para você.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-126">Copy and modify the following code sample with information that's relevant to you.</span></span> <span data-ttu-id="1a7ae-127">Você também pode usar o código como está:</span><span class="sxs-lookup"><span data-stu-id="1a7ae-127">You can also use the code as is:</span></span> 
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
1. <span data-ttu-id="1a7ae-128">Chegou ao `src/components` diretório e abrir o `Tab.js` arquivo.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-128">Got to the `src/components` directory and open the `Tab.js` file.</span></span> 
1. <span data-ttu-id="1a7ae-129">Vá para `render()` e substitua o código do modelo pelo código modificado dentro, conforme mostrado no exemplo a `return()` seguir:</span><span class="sxs-lookup"><span data-stu-id="1a7ae-129">Go to `render()` and replace the template code with the modified code inside `return()` as shown in the following example:</span></span>
    ```JavaScript
    render() {
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
1. <span data-ttu-id="1a7ae-130">Vá para o diretório e modifique o arquivo com o seguinte código para tornar os links de email mais fáceis de ler com qualquer `src/components` `App.css` tema usado:</span><span class="sxs-lookup"><span data-stu-id="1a7ae-130">Go to the `src/components` directory and modify the `App.css` file with the following code to make the email links easier to read with any theme that is used:</span></span>
    ```CSS
    a {
      color: inherit;
    }
    ```
1. <span data-ttu-id="1a7ae-131">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-131">Save your changes.</span></span> 

   <span data-ttu-id="1a7ae-132">Você pode exibir o novo conteúdo na guia do aplicativo no Teams.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-132">You can view the new content in your app's tab in Teams.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/personal-tab-tutorial-content.png" alt-text="Captura de tela de uma guia pessoal com conteúdo estático.":::

## <a name="3-update-your-tab-theme"></a><span data-ttu-id="1a7ae-134">3. Atualize o tema da guia</span><span class="sxs-lookup"><span data-stu-id="1a7ae-134">3. Update your tab theme</span></span>

<span data-ttu-id="1a7ae-135">É importante que sua guia tenha um tema nativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-135">It is important for your tab to have a theme that feels native to Teams.</span></span> <span data-ttu-id="1a7ae-136">Você deve mesclar sua guia com o tema do Teams.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-136">You must blend your tab with the Teams theme.</span></span> <span data-ttu-id="1a7ae-137">Seus usuários geralmente preferem temas padrão (claro), escuro ou de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-137">Your users generally prefer default (light), dark, or high contrast themes.</span></span> <span data-ttu-id="1a7ae-138">Como você deve ter notado na última captura de tela, sua guia ainda tem um plano de fundo claro quando o usuário está usando o tema escuro.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-138">As you might have noticed in the last screenshot, your tab still has a light background when your user is using the dark theme.</span></span> <span data-ttu-id="1a7ae-139">Essa não é uma experiência de usuário recomendada.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-139">This is not a recommended user experience.</span></span>

<span data-ttu-id="1a7ae-140">O SDK do cliente JavaScript do Teams pode tornar seu aplicativo ciente e reagir às alterações de tema no cliente.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-140">The Teams JavaScript client SDK can make your app aware of and react to theme changes in the client.</span></span> <span data-ttu-id="1a7ae-141">Para fazer isso, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="1a7ae-141">To do this, follow these steps:</span></span>

1. <span data-ttu-id="1a7ae-142">**Obter contexto sobre o tema do cliente do Teams configurado** A `microsoftTeams.getContext()` chamada em seu arquivo fornece algum contexto sobre o tema do cliente configurado `Tab.js` (como tema escuro).</span><span class="sxs-lookup"><span data-stu-id="1a7ae-142">**Get context about the configured Teams client theme** The `microsoftTeams.getContext()` call in your `Tab.js` file, provides some context about the configured client theme (such as dark theme).</span></span> <span data-ttu-id="1a7ae-143">O código a seguir acessa a `context` interface e suas propriedades:</span><span class="sxs-lookup"><span data-stu-id="1a7ae-143">The following code accesses the `context` interface and its properties:</span></span>

    ```JavaScript
    componentDidMount(){
      // Get the user context from Teams and set it in the state
      microsoftTeams.getContext((context, error) => {
        this.setState({
          context: context,
          theme: context.theme
        });
      });
    }
    ```
1. <span data-ttu-id="1a7ae-144">**Criar um manipulador de alterações de tema** Com as propriedades em mãos, seu aplicativo tem uma compreensão sólida do que está acontecendo ao `context` seu redor no Teams.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-144">**Create a theme change handler** With the `context` properties in hand, your app has a solid understanding of what's happening around it in Teams.</span></span> <span data-ttu-id="1a7ae-145">No entanto, o aplicativo ainda não tem uma aparência que reflita o tema quando um usuário o atualiza.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-145">However, the app still doesn't have an appearance reflecting the theme when a user updates it.</span></span>

   <span data-ttu-id="1a7ae-146">Você precisa de um manipulador para atualizar o estado do aplicativo com o tema.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-146">You need a handler to update your app's state with the theme.</span></span> <span data-ttu-id="1a7ae-147">Para criar um manipulador, insira o seguinte manipulador de alterações de tema imediatamente após a `microsoftTeams.getContext()` chamada:</span><span class="sxs-lookup"><span data-stu-id="1a7ae-147">To create a handler, insert the following theme change handler immediately after the `microsoftTeams.getContext()` call:</span></span>

    ```JavaScript
    microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.context.theme) {
    this.setState({
      context: {
      ...this.state.context,
      theme
      }
      })   
      }
    });
      ```
1. <span data-ttu-id="1a7ae-148">**Corresponder aos estilos de tema** Seu manipulador de alterações de tema está no local, no entanto, você ainda precisa responder às alterações e alinhar as cores da guia com o tema atual.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-148">**Match the theme styles** Your theme change handler is in place, however, you still have to respond to changes and align your tab's colors with the current theme.</span></span>

   <span data-ttu-id="1a7ae-149">Na `render()` função, armazene o estado fornecido pelo manipulador de alterações de tema em `isTheme` :</span><span class="sxs-lookup"><span data-stu-id="1a7ae-149">In the `render()` function, store the state provided by the theme change handler in `isTheme`:</span></span>

    ```JavaScript
      const isTheme = this.state.context.theme
    ```
    
    > [!NOTE]
    > <span data-ttu-id="1a7ae-150">Este exemplo é apenas uma maneira de você aplicar estilos à sua guia. Use o código como está, expanda-o ou escreva seu próprio.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-150">This example is just one way you might apply styles to your tab. Use the code as is, expand on it, or write your own.</span></span>

    <span data-ttu-id="1a7ae-151">Depois de armazenar o estado fornecido pelo manipulador de alterações de tema, forneça a lógica condicional para renderizar os estilos da guia com base no tema atual.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-151">After storing the state provided by the theme change handler, provide the conditional logic to render your tab's styles based on the current theme.</span></span> <span data-ttu-id="1a7ae-152">O exemplo a seguir mostra uma maneira básica de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="1a7ae-152">The following example shows a basic way to do this:</span></span>

    1. <span data-ttu-id="1a7ae-153">Vá para `render()` e verifique o tema atual em `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="1a7ae-153">Go to `render()` and check the current theme in `isTheme`.</span></span>
    1. <span data-ttu-id="1a7ae-154">Crie um `newTheme` objeto com propriedades CSS relevantes para o tema atual.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-154">Create a `newTheme` object with CSS properties relevant to the current theme.</span></span>
    1. <span data-ttu-id="1a7ae-155">Aplique o seguinte CSS ao elemento HTML raiz do conteúdo de tabulação ( `<div style={newTheme}>` ):</span><span class="sxs-lookup"><span data-stu-id="1a7ae-155">Apply the following CSS to your tab content's root HTML element (`<div style={newTheme}>`):</span></span>

        ```JavaScript
         let newTheme
          if (isTheme === "default") {
            newTheme = {
              backgroundColor: "#EEF1F5",
              color: "#16233A"
            };
          } else {
            newTheme = {
              backgroundColor: "#2B2B30",
              color: "#FFFFFF"
            };
          }
        ```

       <span data-ttu-id="1a7ae-156">Verifique sua guia no Teams.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-156">Check your tab in Teams.</span></span> <span data-ttu-id="1a7ae-157">A aparência agora corresponde de perto ao tema escuro.</span><span class="sxs-lookup"><span data-stu-id="1a7ae-157">The appearance now closely matches the dark theme.</span></span>

       :::image type="content" source="../assets/images/build-your-first-app/personal-tab-tutorial-updated-theme.png" alt-text="Captura de tela de uma guia pessoal com exibição de conteúdo estático.":::

## <a name="see-also"></a><span data-ttu-id="1a7ae-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="1a7ae-159">See also</span></span>

* [<span data-ttu-id="1a7ae-160">SDK do cliente JavaScript do Teams</span><span class="sxs-lookup"><span data-stu-id="1a7ae-160">Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [<span data-ttu-id="1a7ae-161">Projetando sua guia para a área de trabalho e a Web do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1a7ae-161">Designing your tab for Microsoft Teams desktop and web</span></span>](../tabs/design/tabs.md) 
* [<span data-ttu-id="1a7ae-162">Interface de contexto</span><span class="sxs-lookup"><span data-stu-id="1a7ae-162">Context interface</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true)
* [<span data-ttu-id="1a7ae-163">Projetando seu aplicativo do Microsoft Teams com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1a7ae-163">Designing your Microsoft Teams app with UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md) 
* [<span data-ttu-id="1a7ae-164">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="1a7ae-164">Tabs on mobile</span></span>](../tabs/design/tabs-mobile.md)
* [<span data-ttu-id="1a7ae-165">Suporte a SSO (login único) para guias</span><span class="sxs-lookup"><span data-stu-id="1a7ae-165">Single sign-on (SSO) support for tabs</span></span>](../tabs/how-to/authentication/auth-aad-sso.md)
* [<span data-ttu-id="1a7ae-166">Visão geral da API do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1a7ae-166">Microsoft Teams API overview</span></span>](https://docs.microsoft.com/graph/teams-concept-overview)
* [<span data-ttu-id="1a7ae-167">Criar uma guia pessoal personalizada com Node.js e o Gerador Yeoman para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1a7ae-167">Create a custom personal tab with Node.js and the Yeoman Generator for Microsoft Teams</span></span>](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a><span data-ttu-id="1a7ae-168">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="1a7ae-168">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1a7ae-169">Construir uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="1a7ae-169">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)