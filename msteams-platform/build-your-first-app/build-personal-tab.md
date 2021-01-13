---
title: Começar - Criar uma guia pessoal
author: heath-hamilton
description: Crie rapidamente uma guia pessoal do Microsoft Teams usando o Kit de Ferramentas do Microsoft Teams.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: tutorial
ms.openlocfilehash: 86be39503ec4e4fde5fafe63f83b3a4fb6d956bf
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797803"
---
# <a name="build-a-personal-tab-for-microsoft-teams"></a><span data-ttu-id="9a653-103">Criar uma guia pessoal para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9a653-103">Build a personal tab for Microsoft Teams</span></span>

<span data-ttu-id="9a653-104">As guias são uma maneira simples de surgir conteúdo em seu aplicativo ao incorporar essencialmente uma página da Web no Teams.</span><span class="sxs-lookup"><span data-stu-id="9a653-104">Tabs are a simple way to surface content in your app by essentially embedding a webpage in Teams.</span></span>

<span data-ttu-id="9a653-105">Há dois tipos de guias no Teams.</span><span class="sxs-lookup"><span data-stu-id="9a653-105">There are two types of tabs in Teams.</span></span> <span data-ttu-id="9a653-106">Neste tutorial, você criará uma guia pessoal *básica,* uma página de conteúdo em tela inteira para usuários individuais.</span><span class="sxs-lookup"><span data-stu-id="9a653-106">In this tutorial, you'll build basic a *personal tab*, a full-screen content page for individual users.</span></span> <span data-ttu-id="9a653-107">(As guias pessoais são a coisa mais próxima de uma experiência de site tradicional no Teams.)</span><span class="sxs-lookup"><span data-stu-id="9a653-107">(Personal tabs are the closest thing to a traditional website experience in Teams.)</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="9a653-108">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="9a653-108">Before you begin</span></span>

<span data-ttu-id="9a653-109">Você precisa de uma guia pessoal de execução básica para começar.</span><span class="sxs-lookup"><span data-stu-id="9a653-109">You need a basic running personal tab to get started.</span></span> <span data-ttu-id="9a653-110">Se você não tiver um, confira criar [e executar seu primeiro aplicativo teams.](../build-your-first-app/build-and-run.md)</span><span class="sxs-lookup"><span data-stu-id="9a653-110">If you don't have one, see [build and run your first Teams app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="9a653-111">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="9a653-111">Your assignment</span></span>

<span data-ttu-id="9a653-112">As pessoas em sua organização têm problemas para encontrar informações básicas de contato para funções importantes (help desk, RH, etc.).</span><span class="sxs-lookup"><span data-stu-id="9a653-112">People in your organization have trouble finding basic contact information for important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="9a653-113">Você é responsável por garantir que eles possam encontrar essas informações rapidamente em um só lugar.</span><span class="sxs-lookup"><span data-stu-id="9a653-113">You're in charge of making sure they can quickly find this information in one place.</span></span> <span data-ttu-id="9a653-114">Como você faria isso?</span><span class="sxs-lookup"><span data-stu-id="9a653-114">How would you do that?</span></span> <span data-ttu-id="9a653-115">Uma guia pessoal do Teams, claro.</span><span class="sxs-lookup"><span data-stu-id="9a653-115">A Teams personal tab, of course.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="9a653-116">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="9a653-116">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="9a653-117">Identificar algumas das configurações do aplicativo e o scaffolding relevante para guias pessoais</span><span class="sxs-lookup"><span data-stu-id="9a653-117">Identify some of the app configurations and scaffolding relevant to personal tabs</span></span>
> * <span data-ttu-id="9a653-118">Criar conteúdo de guia</span><span class="sxs-lookup"><span data-stu-id="9a653-118">Create tab content</span></span>
> * <span data-ttu-id="9a653-119">Atualizar o tema de cores de uma guia com base na preferência do usuário</span><span class="sxs-lookup"><span data-stu-id="9a653-119">Update a tab's color theme based on user preference</span></span>

## <a name="1-identify-relevant-app-project-components"></a><span data-ttu-id="9a653-120">1. Identifique componentes relevantes do projeto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="9a653-120">1. Identify relevant app project components</span></span>

<span data-ttu-id="9a653-121">Grande parte das configurações e da scaffolding do aplicativo é configurada automaticamente quando você cria seu projeto com o Kit de Ferramentas do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a653-121">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="9a653-122">Vamos dar uma olhada nos componentes principais para criar uma guia pessoal.</span><span class="sxs-lookup"><span data-stu-id="9a653-122">Let's look at the main components for building a personal tab.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="9a653-123">Configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="9a653-123">App configurations</span></span>

<span data-ttu-id="9a653-124">No kit de ferramentas, vá para o **App Studio** para exibir e atualizar as configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9a653-124">In the toolkit, go to **App Studio** to view and update your app configurations.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="9a653-125">Scaffolding de aplicativos</span><span class="sxs-lookup"><span data-stu-id="9a653-125">App scaffolding</span></span>

<span data-ttu-id="9a653-126">O scaffolding do aplicativo fornece os componentes para renderizar sua guia pessoal no Teams.</span><span class="sxs-lookup"><span data-stu-id="9a653-126">The app scaffolding provides the components for rendering your personal tab in Teams.</span></span> <span data-ttu-id="9a653-127">Há muito com o que você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:</span><span class="sxs-lookup"><span data-stu-id="9a653-127">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="9a653-128">`Tab.js` no diretório `src/components` do projeto.</span><span class="sxs-lookup"><span data-stu-id="9a653-128">`Tab.js` file in the `src/components` directory of your project.</span></span> <span data-ttu-id="9a653-129">Isso é para renderizar sua página de conteúdo de guia.</span><span class="sxs-lookup"><span data-stu-id="9a653-129">This is for rendering your tab content page.</span></span>
* <span data-ttu-id="9a653-130">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span><span class="sxs-lookup"><span data-stu-id="9a653-130">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="2-customize-your-tab-content-page"></a><span data-ttu-id="9a653-131">2. Personalizar a página de conteúdo da guia</span><span class="sxs-lookup"><span data-stu-id="9a653-131">2. Customize your tab content page</span></span>

<span data-ttu-id="9a653-132">Compile uma lista de contatos importantes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="9a653-132">Compile a list of important contacts in your organization.</span></span> <span data-ttu-id="9a653-133">Copie e atualize o trecho a seguir com informações relevantes para você ou, por um tempo, use o código como estão.</span><span class="sxs-lookup"><span data-stu-id="9a653-133">Copy and update the following snippet with information that's relevant to you or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="9a653-134">Vá para o `src/components` diretório e `Tab.js` abra.</span><span class="sxs-lookup"><span data-stu-id="9a653-134">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="9a653-135">Localize `render()` a função e colar o conteúdo dentro `return()` (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="9a653-135">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="9a653-136">Adicione a regra a seguir para que os links de email sejam mais fáceis de `App.css` ler, independentemente do tema usado.</span><span class="sxs-lookup"><span data-stu-id="9a653-136">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

<span data-ttu-id="9a653-137">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="9a653-137">Save your changes.</span></span> <span data-ttu-id="9a653-138">Vá até a guia do seu aplicativo no Teams para exibir o novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9a653-138">Go to your app's tab in Teams to view the new content.</span></span>

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-content.png" alt-text="Captura de tela de uma guia pessoal com conteúdo estático.":::

## <a name="3-update-the-tab-theme"></a><span data-ttu-id="9a653-140">3. Atualizar o tema da guia</span><span class="sxs-lookup"><span data-stu-id="9a653-140">3. Update the tab theme</span></span>

<span data-ttu-id="9a653-141">Os bons aplicativos são nativos para o Teams, portanto, é importante que sua guia se combina com o tema do Teams de sua preferência pelos usuários: padrão (claro), escuro ou alto contraste.</span><span class="sxs-lookup"><span data-stu-id="9a653-141">Good apps feel native to Teams, so it's important your tab blends with the Teams theme your users prefer: default (light), dark, or high contrast.</span></span> <span data-ttu-id="9a653-142">Como você deve ter notado na última captura de tela, sua guia ainda tem um plano de fundo claro quando o cliente está usando o tema escuro.</span><span class="sxs-lookup"><span data-stu-id="9a653-142">As you might have noticed in the last screenshot, your tab still has a light background when the client's using the dark theme.</span></span> <span data-ttu-id="9a653-143">Essa não é uma experiência de usuário recomendada.</span><span class="sxs-lookup"><span data-stu-id="9a653-143">This is not a recommended user experience.</span></span>

<span data-ttu-id="9a653-144">O [SDK do cliente JavaScript](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) do Teams pode fazer com que seu aplicativo saiba e reaja a alterações de tema no cliente.</span><span class="sxs-lookup"><span data-stu-id="9a653-144">The [Teams JavaScript client SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) can make your app aware of and react to theme changes in the client.</span></span> <span data-ttu-id="9a653-145">Vamos ver como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="9a653-145">Let's walk through how to do this.</span></span>

### <a name="get-context-about-the-teams-client"></a><span data-ttu-id="9a653-146">Obter contexto sobre o cliente do Teams</span><span class="sxs-lookup"><span data-stu-id="9a653-146">Get context about the Teams client</span></span>

<span data-ttu-id="9a653-147">Em seu arquivo, há uma chamada que fornece alguns detalhes sobre o tema do cliente configurado, entre `Tab.js` `microsoftTeams.getContext()` [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) outros.</span><span class="sxs-lookup"><span data-stu-id="9a653-147">In your `Tab.js` file, there's a `microsoftTeams.getContext()` call that provides some [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) about, among other details, the configured client theme.</span></span> <span data-ttu-id="9a653-148">Graças ao scaffolding do aplicativo, use esse código como está para acessar a `context` interface e suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="9a653-148">Thanks to the app scaffolding, use this code as is to access the `context` interface and its properties.</span></span>

```JavaScript
componentDidMount(){
  // Get the user context from Teams and set it in the state
  microsoftTeams.getContext((context, error) => {
    this.setState({
      context: context
    });
  });
  // Next steps: Error handling using the error object
}
```

### <a name="create-a-theme-change-handler"></a><span data-ttu-id="9a653-149">Criar um manipulador de alteração de tema</span><span class="sxs-lookup"><span data-stu-id="9a653-149">Create a theme change handler</span></span>

<span data-ttu-id="9a653-150">Com as propriedades em mãos, seu aplicativo tem uma compreensão sólida do que está acontecendo em `context` torno dele no Teams.</span><span class="sxs-lookup"><span data-stu-id="9a653-150">With the `context` properties in hand, your app has a solid understanding of what's happening around it in Teams.</span></span> <span data-ttu-id="9a653-151">Mas o aplicativo ainda não sabe que sua aparência deve refletir qualquer tema que um usuário escolher.</span><span class="sxs-lookup"><span data-stu-id="9a653-151">But the app still doesn't know its appearance should reflect whatever theme a user chooses.</span></span>

<span data-ttu-id="9a653-152">Você precisa de um manipulador para que o estado do seu aplicativo mude com o tema.</span><span class="sxs-lookup"><span data-stu-id="9a653-152">You need a handler so that your app's state changes with the theme.</span></span> <span data-ttu-id="9a653-153">Insira o manipulador de alteração de tema a seguir imediatamente após a `microsoftTeams.getContext()` chamada.</span><span class="sxs-lookup"><span data-stu-id="9a653-153">Insert the following theme change handler immediately after the `microsoftTeams.getContext()` call.</span></span>

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a><span data-ttu-id="9a653-154">Corresponder estilos de tema</span><span class="sxs-lookup"><span data-stu-id="9a653-154">Match theme styles</span></span>

<span data-ttu-id="9a653-155">O manipulador de alterações de temas está em uso, mas você precisa de alguns códigos que respondam a essas alterações e alinhe as cores da guia com o tema atual.</span><span class="sxs-lookup"><span data-stu-id="9a653-155">Your theme change handler is in place, but you need some code that responds to those changes and aligns your tab's colors with the current theme.</span></span>

> [!NOTE]
> <span data-ttu-id="9a653-156">O exemplo a seguir é apenas uma maneira de aplicar estilos à guia. Use o código como está, expanda-o ou escreva o seu próprio.</span><span class="sxs-lookup"><span data-stu-id="9a653-156">The following example is just one way you might apply styles to your tab. Use the code as is, expand on it, or write your own.</span></span>

<span data-ttu-id="9a653-157">Na `render()` função, armazene o estado fornecido pelo manipulador de alteração de tema em `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="9a653-157">In the `render()` function, store the state provided by the theme change handler in `isTheme`.</span></span>

```JavaScript
  const isTheme = this.state.theme
```

<span data-ttu-id="9a653-158">Depois de armazenar o estado fornecido pelo manipulador de alterações de tema, forneça alguma lógica condicional para renderizar os estilos da guia com base no tema atual.</span><span class="sxs-lookup"><span data-stu-id="9a653-158">After storing the state provided by the theme change handler, provide some conditional logic to render your tab's styles based on the current theme.</span></span> <span data-ttu-id="9a653-159">O exemplo a seguir mostra uma maneira básica de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="9a653-159">The following example shows a basic way to do this:</span></span>
1. <span data-ttu-id="9a653-160">Verifique o tema atual em `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="9a653-160">Check the current theme in `isTheme`.</span></span>
2. <span data-ttu-id="9a653-161">Crie um `newTheme` objeto com propriedades CSS relevantes para o tema atual.</span><span class="sxs-lookup"><span data-stu-id="9a653-161">Create a `newTheme` object with CSS properties relevant to the current theme.</span></span>
3. <span data-ttu-id="9a653-162">Aplicar o CSS ao elemento HTML raiz do conteúdo da guia ( `<div>` ).</span><span class="sxs-lookup"><span data-stu-id="9a653-162">Apply the CSS to your tab content's root HTML element (`<div>`).</span></span>

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

<span data-ttu-id="9a653-163">Verifique sua guia no Teams.</span><span class="sxs-lookup"><span data-stu-id="9a653-163">Check your tab in Teams.</span></span> <span data-ttu-id="9a653-164">A aparência deve corresponder muito ao tema escuro.</span><span class="sxs-lookup"><span data-stu-id="9a653-164">The appearance should closely match the dark theme.</span></span>

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-updated-theme.png" alt-text="Captura de tela de uma guia pessoal com exibição de conteúdo estático.":::

## <a name="well-done"></a><span data-ttu-id="9a653-166">Bem feito</span><span class="sxs-lookup"><span data-stu-id="9a653-166">Well done</span></span>

<span data-ttu-id="9a653-167">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="9a653-167">Congratulations!</span></span> <span data-ttu-id="9a653-168">Você tem um aplicativo teams com uma guia pessoal que facilita a encontrar contatos importantes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="9a653-168">You have a Teams app with a personal tab that makes it easier to find important contacts in your organization.</span></span>

## <a name="learn-more"></a><span data-ttu-id="9a653-169">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="9a653-169">Learn more</span></span>

* <span data-ttu-id="9a653-170">Autenticar usuários de guia com [SSO:](../tabs/how-to/authentication/auth-aad-sso.md)se você quiser apenas usuários autorizados exibindo sua guia, configurar o SSO (single sign-on) por meio do Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="9a653-170">[Authenticate tab users with SSO](../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="9a653-171">[Inserir conteúdo de](../tabs/how-to/tab-requirements.md)um aplicativo Web ou página da Web existente: mostramos como criar novo conteúdo para uma guia pessoal, mas você também pode carregar conteúdo de uma URL externa.</span><span class="sxs-lookup"><span data-stu-id="9a653-171">[Embed content from an existing web app or webpage](../tabs/how-to/tab-requirements.md): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="9a653-172">[Crie uma experiência perfeita para sua guia:](../tabs/design/tabs.md)confira as diretrizes recomendadas para projetar guias do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a653-172">[Create a seamless experience for your tab](../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="9a653-173">[Criar guias para dispositivos móveis:](../tabs/design/tabs-mobile.md)entenda como desenvolver guias para telefones e tablets.</span><span class="sxs-lookup"><span data-stu-id="9a653-173">[Build tabs for mobile](../tabs/design/tabs-mobile.md): Understand how to develop tabs for phones and tablets.</span></span>
* [<span data-ttu-id="9a653-174">Utilizar dados do Teams com o Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="9a653-174">Utilize Teams data with Microsoft Graph</span></span>](https://docs.microsoft.com/graph/teams-concept-overview)
* [<span data-ttu-id="9a653-175">Criar uma guia sem o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="9a653-175">Create a tab without the toolkit</span></span>](../tabs/quickstarts/create-channel-group-tab-node-yeoman.md)

## <a name="next-lesson"></a><span data-ttu-id="9a653-176">Próxima lição</span><span class="sxs-lookup"><span data-stu-id="9a653-176">Next lesson</span></span>

<span data-ttu-id="9a653-177">Você sabe como criar uma guia para uso pessoal.</span><span class="sxs-lookup"><span data-stu-id="9a653-177">You know how to build a tab for personal use.</span></span> <span data-ttu-id="9a653-178">Vejamos o que é necessário para criar uma guia para canais e chats de equipe.</span><span class="sxs-lookup"><span data-stu-id="9a653-178">Let's look at what it takes to build a tab for team channels and chats.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9a653-179">Construir uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="9a653-179">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
