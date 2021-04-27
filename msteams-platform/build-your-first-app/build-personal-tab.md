---
title: Começar - Criar uma guia pessoal
author: heath-hamilton
description: Crie rapidamente uma guia pessoal do Microsoft Teams usando o microsoft Teams Toolkit.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/03/2020
ms.topic: tutorial
ms.openlocfilehash: dabe427142dd3e6a1d2f01f83601cbffd4a20dbd
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019976"
---
# <a name="build-a-personal-tab-for-microsoft-teams"></a><span data-ttu-id="0d269-103">Criar uma guia pessoal para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0d269-103">Build a personal tab for Microsoft Teams</span></span>

<span data-ttu-id="0d269-104">As guias são uma maneira simples de superfícier conteúdo em seu aplicativo incorporando essencialmente uma página da Web no Teams.</span><span class="sxs-lookup"><span data-stu-id="0d269-104">Tabs are a simple way to surface content in your app by essentially embedding a webpage in Teams.</span></span>

<span data-ttu-id="0d269-105">Há dois tipos de guias no Teams.</span><span class="sxs-lookup"><span data-stu-id="0d269-105">There are two types of tabs in Teams.</span></span> <span data-ttu-id="0d269-106">Neste tutorial, você criará uma guia *pessoal* básica , uma página de conteúdo de tela inteira para usuários individuais.</span><span class="sxs-lookup"><span data-stu-id="0d269-106">In this tutorial, you'll build basic a *personal tab*, a full-screen content page for individual users.</span></span> <span data-ttu-id="0d269-107">(As guias pessoais são a coisa mais próxima de uma experiência de site tradicional no Teams.)</span><span class="sxs-lookup"><span data-stu-id="0d269-107">(Personal tabs are the closest thing to a traditional website experience in Teams.)</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="0d269-108">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="0d269-108">Before you begin</span></span>

<span data-ttu-id="0d269-109">Você precisa de uma guia pessoal de execução básica para começar.</span><span class="sxs-lookup"><span data-stu-id="0d269-109">You need a basic running personal tab to get started.</span></span> <span data-ttu-id="0d269-110">Se você não tiver um, consulte [build and run your first Teams app](../build-your-first-app/build-and-run.md).</span><span class="sxs-lookup"><span data-stu-id="0d269-110">If you don't have one, see [build and run your first Teams app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="0d269-111">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="0d269-111">Your assignment</span></span>

<span data-ttu-id="0d269-112">As pessoas em sua organização têm problemas para encontrar informações básicas de contato para funções importantes (help desk, RH, etc.).</span><span class="sxs-lookup"><span data-stu-id="0d269-112">People in your organization have trouble finding basic contact information for important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="0d269-113">Você é responsável por garantir que eles possam encontrar essas informações rapidamente em um só lugar.</span><span class="sxs-lookup"><span data-stu-id="0d269-113">You're in charge of making sure they can quickly find this information in one place.</span></span> <span data-ttu-id="0d269-114">Como você faria isso?</span><span class="sxs-lookup"><span data-stu-id="0d269-114">How would you do that?</span></span> <span data-ttu-id="0d269-115">Uma guia pessoal do Teams, claro.</span><span class="sxs-lookup"><span data-stu-id="0d269-115">A Teams personal tab, of course.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="0d269-116">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="0d269-116">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="0d269-117">Identificar algumas das configurações do aplicativo e os scaffolding relevantes para guias pessoais</span><span class="sxs-lookup"><span data-stu-id="0d269-117">Identify some of the app configurations and scaffolding relevant to personal tabs</span></span>
> * <span data-ttu-id="0d269-118">Criar conteúdo de guia</span><span class="sxs-lookup"><span data-stu-id="0d269-118">Create tab content</span></span>
> * <span data-ttu-id="0d269-119">Atualizar o tema de cor de uma guia com base na preferência do usuário</span><span class="sxs-lookup"><span data-stu-id="0d269-119">Update a tab's color theme based on user preference</span></span>

## <a name="1-identify-relevant-app-project-components"></a><span data-ttu-id="0d269-120">1. Identificar componentes relevantes do projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="0d269-120">1. Identify relevant app project components</span></span>

<span data-ttu-id="0d269-121">Grande parte das configurações e scaffolding do aplicativo são configuradas automaticamente quando você cria seu projeto com o teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="0d269-121">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="0d269-122">Vamos ver os principais componentes para a criação de uma guia pessoal.</span><span class="sxs-lookup"><span data-stu-id="0d269-122">Let's look at the main components for building a personal tab.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="0d269-123">Configurações de aplicativo</span><span class="sxs-lookup"><span data-stu-id="0d269-123">App configurations</span></span>

<span data-ttu-id="0d269-124">No kit de ferramentas, vá para **o App Studio** para exibir e atualizar as configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0d269-124">In the toolkit, go to **App Studio** to view and update your app configurations.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="0d269-125">Scaffolding de aplicativos</span><span class="sxs-lookup"><span data-stu-id="0d269-125">App scaffolding</span></span>

<span data-ttu-id="0d269-126">O scaffolding do aplicativo fornece os componentes para renderizar sua guia pessoal no Teams.</span><span class="sxs-lookup"><span data-stu-id="0d269-126">The app scaffolding provides the components for rendering your personal tab in Teams.</span></span> <span data-ttu-id="0d269-127">Há muito com o que você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d269-127">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="0d269-128">`Tab.js` no diretório `src/components` do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="0d269-128">`Tab.js` file in the `src/components` directory of your project.</span></span> <span data-ttu-id="0d269-129">Isso é para renderizar sua página de conteúdo de tabulação.</span><span class="sxs-lookup"><span data-stu-id="0d269-129">This is for rendering your tab content page.</span></span>
* <span data-ttu-id="0d269-130">SDK do cliente JavaScript do Microsoft Teams, que vem pré-carregado nos componentes front-end do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="0d269-130">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="2-customize-your-tab-content-page"></a><span data-ttu-id="0d269-131">2. Personalizar sua página de conteúdo de tabulação</span><span class="sxs-lookup"><span data-stu-id="0d269-131">2. Customize your tab content page</span></span>

<span data-ttu-id="0d269-132">Compile uma lista de contatos importantes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="0d269-132">Compile a list of important contacts in your organization.</span></span> <span data-ttu-id="0d269-133">Copie e atualize o trecho a seguir com informações relevantes para você ou, por questão de tempo, use o código como está.</span><span class="sxs-lookup"><span data-stu-id="0d269-133">Copy and update the following snippet with information that's relevant to you or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="0d269-134">Vá para o `src/components` diretório e abra `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="0d269-134">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="0d269-135">Localize `render()` a função e colar seu conteúdo dentro `return()` (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="0d269-135">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="0d269-136">Adicione a regra a seguir para que os links de email sejam mais fáceis de `App.css` ler, independentemente do tema usado.</span><span class="sxs-lookup"><span data-stu-id="0d269-136">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

<span data-ttu-id="0d269-137">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="0d269-137">Save your changes.</span></span> <span data-ttu-id="0d269-138">Vá até a guia do seu aplicativo no Teams para exibir o novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0d269-138">Go to your app's tab in Teams to view the new content.</span></span>

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-content.png" alt-text="Captura de tela de uma guia pessoal com conteúdo estático.":::

## <a name="3-update-the-tab-theme"></a><span data-ttu-id="0d269-140">3. Atualizar o tema da guia</span><span class="sxs-lookup"><span data-stu-id="0d269-140">3. Update the tab theme</span></span>

<span data-ttu-id="0d269-141">Bons aplicativos se sentem nativos do Teams, portanto, é importante que sua guia se mescla com o tema do Teams que seus usuários preferem: padrão (claro), escuro ou alto contraste.</span><span class="sxs-lookup"><span data-stu-id="0d269-141">Good apps feel native to Teams, so it's important your tab blends with the Teams theme your users prefer: default (light), dark, or high contrast.</span></span> <span data-ttu-id="0d269-142">Como você deve ter notado na última captura de tela, sua guia ainda tem um plano de fundo claro quando o cliente está usando o tema escuro.</span><span class="sxs-lookup"><span data-stu-id="0d269-142">As you might have noticed in the last screenshot, your tab still has a light background when the client's using the dark theme.</span></span> <span data-ttu-id="0d269-143">Essa não é uma experiência de usuário recomendada.</span><span class="sxs-lookup"><span data-stu-id="0d269-143">This is not a recommended user experience.</span></span>

<span data-ttu-id="0d269-144">O [SDK do](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) cliente JavaScript do Teams pode tornar seu aplicativo ciente e reagir às alterações de tema no cliente.</span><span class="sxs-lookup"><span data-stu-id="0d269-144">The [Teams JavaScript client SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) can make your app aware of and react to theme changes in the client.</span></span> <span data-ttu-id="0d269-145">Vamos ver como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="0d269-145">Let's walk through how to do this.</span></span>

### <a name="get-context-about-the-teams-client"></a><span data-ttu-id="0d269-146">Obter contexto sobre o cliente do Teams</span><span class="sxs-lookup"><span data-stu-id="0d269-146">Get context about the Teams client</span></span>

<span data-ttu-id="0d269-147">Em seu arquivo, há uma chamada que fornece alguns detalhes `Tab.js` `microsoftTeams.getContext()` [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) sobre, entre outros detalhes, o tema do cliente configurado.</span><span class="sxs-lookup"><span data-stu-id="0d269-147">In your `Tab.js` file, there's a `microsoftTeams.getContext()` call that provides some [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) about, among other details, the configured client theme.</span></span> <span data-ttu-id="0d269-148">Graças ao scaffolding do aplicativo, use este código como é para acessar a `context` interface e suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="0d269-148">Thanks to the app scaffolding, use this code as is to access the `context` interface and its properties.</span></span>

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

### <a name="create-a-theme-change-handler"></a><span data-ttu-id="0d269-149">Criar um manipulador de alterações de tema</span><span class="sxs-lookup"><span data-stu-id="0d269-149">Create a theme change handler</span></span>

<span data-ttu-id="0d269-150">Com as propriedades em mãos, seu aplicativo tem uma compreensão sólida do que está acontecendo ao `context` seu redor no Teams.</span><span class="sxs-lookup"><span data-stu-id="0d269-150">With the `context` properties in hand, your app has a solid understanding of what's happening around it in Teams.</span></span> <span data-ttu-id="0d269-151">Mas o aplicativo ainda não sabe que sua aparência deve refletir qualquer tema escolhido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="0d269-151">But the app still doesn't know its appearance should reflect whatever theme a user chooses.</span></span>

<span data-ttu-id="0d269-152">Você precisa de um manipulador para que o estado do seu aplicativo mude com o tema.</span><span class="sxs-lookup"><span data-stu-id="0d269-152">You need a handler so that your app's state changes with the theme.</span></span> <span data-ttu-id="0d269-153">Insira o seguinte manipulador de alterações de tema imediatamente após a `microsoftTeams.getContext()` chamada.</span><span class="sxs-lookup"><span data-stu-id="0d269-153">Insert the following theme change handler immediately after the `microsoftTeams.getContext()` call.</span></span>

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a><span data-ttu-id="0d269-154">Corresponder estilos de tema</span><span class="sxs-lookup"><span data-stu-id="0d269-154">Match theme styles</span></span>

<span data-ttu-id="0d269-155">Seu manipulador de alterações de tema está no local, mas você precisa de algum código que responda a essas alterações e alinhe as cores da guia com o tema atual.</span><span class="sxs-lookup"><span data-stu-id="0d269-155">Your theme change handler is in place, but you need some code that responds to those changes and aligns your tab's colors with the current theme.</span></span>

> [!NOTE]
> <span data-ttu-id="0d269-156">O exemplo a seguir é apenas uma maneira de aplicar estilos à guia. Use o código como está, expanda-o ou escreva seu próprio.</span><span class="sxs-lookup"><span data-stu-id="0d269-156">The following example is just one way you might apply styles to your tab. Use the code as is, expand on it, or write your own.</span></span>

<span data-ttu-id="0d269-157">Na `render()` função, armazene o estado fornecido pelo manipulador de alterações de tema em `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="0d269-157">In the `render()` function, store the state provided by the theme change handler in `isTheme`.</span></span>

```JavaScript
  const isTheme = this.state.theme
```

<span data-ttu-id="0d269-158">Depois de armazenar o estado fornecido pelo manipulador de alterações de tema, forneça alguma lógica condicional para renderizar os estilos da guia com base no tema atual.</span><span class="sxs-lookup"><span data-stu-id="0d269-158">After storing the state provided by the theme change handler, provide some conditional logic to render your tab's styles based on the current theme.</span></span> <span data-ttu-id="0d269-159">O exemplo a seguir mostra uma maneira básica de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="0d269-159">The following example shows a basic way to do this:</span></span>
1. <span data-ttu-id="0d269-160">Verifique o tema atual em `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="0d269-160">Check the current theme in `isTheme`.</span></span>
2. <span data-ttu-id="0d269-161">Crie um `newTheme` objeto com propriedades CSS relevantes para o tema atual.</span><span class="sxs-lookup"><span data-stu-id="0d269-161">Create a `newTheme` object with CSS properties relevant to the current theme.</span></span>
3. <span data-ttu-id="0d269-162">Aplique o CSS ao elemento HTML raiz do conteúdo da guia ( `<div style={newTheme}>` ).</span><span class="sxs-lookup"><span data-stu-id="0d269-162">Apply the CSS to your tab content's root HTML element (`<div style={newTheme}>`).</span></span>

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

<span data-ttu-id="0d269-163">Verifique sua guia no Teams.</span><span class="sxs-lookup"><span data-stu-id="0d269-163">Check your tab in Teams.</span></span> <span data-ttu-id="0d269-164">A aparência deve corresponder de perto ao tema escuro.</span><span class="sxs-lookup"><span data-stu-id="0d269-164">The appearance should closely match the dark theme.</span></span>

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-updated-theme.png" alt-text="Captura de tela de uma guia pessoal com exibição de conteúdo estático.":::

## <a name="well-done"></a><span data-ttu-id="0d269-166">Muito bem</span><span class="sxs-lookup"><span data-stu-id="0d269-166">Well done</span></span>

<span data-ttu-id="0d269-167">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="0d269-167">Congratulations!</span></span> <span data-ttu-id="0d269-168">Você tem um aplicativo do Teams com uma guia pessoal que facilita a busca de contatos importantes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="0d269-168">You have a Teams app with a personal tab that makes it easier to find important contacts in your organization.</span></span>

## <a name="learn-more"></a><span data-ttu-id="0d269-169">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="0d269-169">Learn more</span></span>

* <span data-ttu-id="0d269-170">Siga nossas [diretrizes de design](../tabs/design/tabs.md) e crie com modelos [de interface](../concepts/design/design-teams-app-ui-templates.md) do usuário prontos para produção para criar uma experiência perfeita.</span><span class="sxs-lookup"><span data-stu-id="0d269-170">Follow our [design guidelines](../tabs/design/tabs.md) and build with [production-ready UI templates](../concepts/design/design-teams-app-ui-templates.md) to create a seamless experience.</span></span>
* <span data-ttu-id="0d269-171">Entenda [as considerações móveis](../tabs/design/tabs-mobile.md) para guias.</span><span class="sxs-lookup"><span data-stu-id="0d269-171">Understand [mobile considerations](../tabs/design/tabs-mobile.md) for tabs.</span></span>
* <span data-ttu-id="0d269-172">[Adicione a autenticação SSO à sua guia](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="0d269-172">[Add SSO authentication to your tab](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>
* <span data-ttu-id="0d269-173">Utilize dados do Teams com [o Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="0d269-173">Utilize Teams data with [Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).</span></span>
* <span data-ttu-id="0d269-174">[Crie uma guia sem o kit de ferramentas](../tabs/quickstarts/create-personal-tab-node-yeoman.md).</span><span class="sxs-lookup"><span data-stu-id="0d269-174">[Create a tab without the toolkit](../tabs/quickstarts/create-personal-tab-node-yeoman.md).</span></span>

## <a name="next-lesson"></a><span data-ttu-id="0d269-175">Próxima lição</span><span class="sxs-lookup"><span data-stu-id="0d269-175">Next lesson</span></span>

<span data-ttu-id="0d269-176">Você sabe como criar uma guia para uso pessoal.</span><span class="sxs-lookup"><span data-stu-id="0d269-176">You know how to build a tab for personal use.</span></span> <span data-ttu-id="0d269-177">Vamos ver o que é necessário para criar uma guia para canais de equipe e chats.</span><span class="sxs-lookup"><span data-stu-id="0d269-177">Let's look at what it takes to build a tab for team channels and chats.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0d269-178">Construir uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="0d269-178">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
