---
title: Introdução-criar uma guia pessoal
author: heath-hamilton
description: Crie rapidamente uma guia pessoal do Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: tutorial
ms.openlocfilehash: a82d3dcfd9529d88160c4193d27105c3468fe654
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346802"
---
# <a name="build-a-personal-tab-for-microsoft-teams"></a><span data-ttu-id="03515-103">Criar uma guia pessoal para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="03515-103">Build a personal tab for Microsoft Teams</span></span>

<span data-ttu-id="03515-104">As guias são uma maneira simples de fazer a superfície de conteúdo em seu aplicativo, incorporando essencialmente uma página da Web no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="03515-104">Tabs are a simple way to surface content in your app by essentially embedding a webpage in Teams.</span></span>

<span data-ttu-id="03515-105">Há dois tipos de guias no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="03515-105">There are two types of tabs in Teams.</span></span> <span data-ttu-id="03515-106">Neste tutorial, você criará uma *guia pessoal*, uma página de conteúdo de tela inteira para usuários individuais.</span><span class="sxs-lookup"><span data-stu-id="03515-106">In this tutorial, you'll build basic a *personal tab*, a full-screen content page for individual users.</span></span> <span data-ttu-id="03515-107">(As guias pessoais são as coisas mais próximas de uma experiência de site tradicional no Microsoft Teams.)</span><span class="sxs-lookup"><span data-stu-id="03515-107">(Personal tabs are the closest thing to a traditional website experience in Teams.)</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="03515-108">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="03515-108">Before you begin</span></span>

<span data-ttu-id="03515-109">Você precisa de uma guia pessoal em execução básica para começar.</span><span class="sxs-lookup"><span data-stu-id="03515-109">You need a basic running personal tab to get started.</span></span> <span data-ttu-id="03515-110">Se você não tiver um, confira [Compilar e executar seu primeiro aplicativo do Microsoft Teams](../build-your-first-app/build-and-run.md).</span><span class="sxs-lookup"><span data-stu-id="03515-110">If you don't have one, see [build and run your first Teams app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="03515-111">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="03515-111">Your assignment</span></span>

<span data-ttu-id="03515-112">As pessoas da sua organização têm problemas para localizar informações básicas de contato para funções importantes (Help Desk, HR, etc.).</span><span class="sxs-lookup"><span data-stu-id="03515-112">People in your organization have trouble finding basic contact information for important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="03515-113">Você está encarregado de garantir que eles possam encontrar rapidamente essas informações em um só lugar.</span><span class="sxs-lookup"><span data-stu-id="03515-113">You're in charge of making sure they can quickly find this information in one place.</span></span> <span data-ttu-id="03515-114">Como fazer isso?</span><span class="sxs-lookup"><span data-stu-id="03515-114">How would you do that?</span></span> <span data-ttu-id="03515-115">Uma guia pessoal do Teams, naturalmente.</span><span class="sxs-lookup"><span data-stu-id="03515-115">A Teams personal tab, of course.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="03515-116">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="03515-116">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="03515-117">Identificar algumas das configurações do aplicativo e scaffolding relevantes para guias pessoais</span><span class="sxs-lookup"><span data-stu-id="03515-117">Identify some of the app configurations and scaffolding relevant to personal tabs</span></span>
> * <span data-ttu-id="03515-118">Criar conteúdo de guia</span><span class="sxs-lookup"><span data-stu-id="03515-118">Create tab content</span></span>
> * <span data-ttu-id="03515-119">Atualizar o tema de cores de uma guia com base na preferência do usuário</span><span class="sxs-lookup"><span data-stu-id="03515-119">Update a tab's color theme based on user preference</span></span>

## <a name="1-identify-relevant-app-project-components"></a><span data-ttu-id="03515-120">1. identificar componentes de projeto de aplicativo relevantes</span><span class="sxs-lookup"><span data-stu-id="03515-120">1. Identify relevant app project components</span></span>

<span data-ttu-id="03515-121">Grande parte das configurações do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="03515-121">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="03515-122">Vamos examinar os principais componentes para criar uma guia pessoal.</span><span class="sxs-lookup"><span data-stu-id="03515-122">Let's look at the main components for building a personal tab.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="03515-123">Configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="03515-123">App configurations</span></span>

<span data-ttu-id="03515-124">Você pode exibir e atualizar suas configurações de aplicativo usando o app Studio, que está incluído no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="03515-124">You can view and update your app configurations using App Studio, which is included in the toolkit.</span></span>

<span data-ttu-id="03515-125">Durante a instalação, o kit de ferramentas configurou inicialmente a página de conteúdo da guia, onde você exibe o conteúdo principal.</span><span class="sxs-lookup"><span data-stu-id="03515-125">During setup, the toolkit initially configured your tab content page, which is where you display your primary content.</span></span> <span data-ttu-id="03515-126">No kit de ferramentas, vá para o **app Studio** e selecione **guias** para ver a configuração.</span><span class="sxs-lookup"><span data-stu-id="03515-126">In the toolkit, go to **App Studio** and select **Tabs** to see the configuration.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="03515-127">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="03515-127">App scaffolding</span></span>

<span data-ttu-id="03515-128">O aplicativo scaffolding fornece os componentes para renderizar sua guia pessoal no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="03515-128">The app scaffolding provides the components for rendering your personal tab in Teams.</span></span> <span data-ttu-id="03515-129">Há muitas coisas com as quais você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:</span><span class="sxs-lookup"><span data-stu-id="03515-129">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="03515-130">`Tab.js` arquivo no `src/components` diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="03515-130">`Tab.js` file in the `src/components` directory of your project.</span></span> <span data-ttu-id="03515-131">Isso é para o processamento da página de conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="03515-131">This is for for rendering your tab content page.</span></span>
* <span data-ttu-id="03515-132">SDK do cliente JavaScript do Microsoft Teams, que vem pré-carregado nos componentes de front-end do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="03515-132">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="2-customize-your-tab-content-page"></a><span data-ttu-id="03515-133">2. personalizar a página de conteúdo da guia</span><span class="sxs-lookup"><span data-stu-id="03515-133">2. Customize your tab content page</span></span>

<span data-ttu-id="03515-134">Compilar uma lista de contatos importantes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="03515-134">Compile a list of important contacts in your organization.</span></span> <span data-ttu-id="03515-135">Copie e atualize o trecho de código a seguir com informações relevantes para você ou, para fins de tempo, use o código como está.</span><span class="sxs-lookup"><span data-stu-id="03515-135">Copy and update the following snippet with information that's relevant to you or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="03515-136">Vá para o `src/components` diretório e abra `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="03515-136">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="03515-137">Localize a `render()` função e cole o conteúdo dentro `return()` (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="03515-137">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="03515-138">Adicione a regra a seguir para `App.css` que os links de email sejam mais fáceis de ler, independentemente de qual tema é usado.</span><span class="sxs-lookup"><span data-stu-id="03515-138">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

<span data-ttu-id="03515-139">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="03515-139">Save your changes.</span></span> <span data-ttu-id="03515-140">Vá para a guia do aplicativo no Microsoft Teams para exibir o novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="03515-140">Go to your app's tab in Teams to view the new content.</span></span>

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-content.png" alt-text="Captura de tela de uma guia pessoal com conteúdo estático.":::

## <a name="3-update-the-tab-theme"></a><span data-ttu-id="03515-142">3. atualizar o tema da guia</span><span class="sxs-lookup"><span data-stu-id="03515-142">3. Update the tab theme</span></span>

<span data-ttu-id="03515-143">Bons aplicativos se sentem nativos para o Microsoft Teams, portanto, é importante que as mesclagens de tabulação com o tema do teams que seus usuários preferem: padrão (claro), escuro ou alto contraste.</span><span class="sxs-lookup"><span data-stu-id="03515-143">Good apps feel native to Teams, so it's important your tab blends with the Teams theme your users prefer: default (light), dark, or high contrast.</span></span> <span data-ttu-id="03515-144">Como você pode ter notado na última captura de tela, sua guia ainda tem um plano de fundo claro quando o cliente está usando o tema escuro.</span><span class="sxs-lookup"><span data-stu-id="03515-144">As you might have noticed in the last screenshot, your tab still has a light background when the client's using the dark theme.</span></span> <span data-ttu-id="03515-145">Essa não é uma experiência de usuário recomendada.</span><span class="sxs-lookup"><span data-stu-id="03515-145">This is not a recommended user experience.</span></span>

<span data-ttu-id="03515-146">O [SDK de cliente do Microsoft Teams](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) pode tornar seu aplicativo ciente e reagir às alterações de tema no cliente.</span><span class="sxs-lookup"><span data-stu-id="03515-146">The [Teams JavaScript client SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) can make your app aware of and react to theme changes in the client.</span></span> <span data-ttu-id="03515-147">Vamos examinar como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="03515-147">Let's walk through how to do this.</span></span>

### <a name="get-context-about-the-teams-client"></a><span data-ttu-id="03515-148">Obter contexto sobre o cliente Teams</span><span class="sxs-lookup"><span data-stu-id="03515-148">Get context about the Teams client</span></span>

<span data-ttu-id="03515-149">No `Tab.js` arquivo, há uma `microsoftTeams.getContext()` chamada que fornece alguns [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) , entre outros detalhes, o tema de cliente configurado.</span><span class="sxs-lookup"><span data-stu-id="03515-149">In your `Tab.js` file, there's a `microsoftTeams.getContext()` call that provides some [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) about, among other details, the configured client theme.</span></span> <span data-ttu-id="03515-150">Graças ao aplicativo scaffolding, use este código como é para acessar a `context` interface e suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="03515-150">Thanks to the app scaffolding, use this code as is to access the `context` interface and its properties.</span></span>

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

### <a name="create-a-theme-change-handler"></a><span data-ttu-id="03515-151">Criar um manipulador de alteração de temas</span><span class="sxs-lookup"><span data-stu-id="03515-151">Create a theme change handler</span></span>

<span data-ttu-id="03515-152">Com as `context` Propriedades em mãos, seu aplicativo tem uma compreensão sólida do que está acontecendo em relação ao Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="03515-152">With the `context` properties in hand, your app has a solid understanding of what's happening around it in Teams.</span></span> <span data-ttu-id="03515-153">Mas o aplicativo ainda não sabe que sua aparência deve refletir qualquer tema escolhido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="03515-153">But the app still doesn't know its appearance should reflect whatever theme a user chooses.</span></span>

<span data-ttu-id="03515-154">Você precisa de um manipulador para que o estado do aplicativo seja alterado com o tema.</span><span class="sxs-lookup"><span data-stu-id="03515-154">You need a handler so that your app's state changes with the theme.</span></span> <span data-ttu-id="03515-155">Insira o seguinte manipulador de alteração de tema imediatamente após a `microsoftTeams.getContext()` chamada.</span><span class="sxs-lookup"><span data-stu-id="03515-155">Insert the following theme change handler immediately after the `microsoftTeams.getContext()` call.</span></span>

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a><span data-ttu-id="03515-156">Coincidir estilos de tema</span><span class="sxs-lookup"><span data-stu-id="03515-156">Match theme styles</span></span>

<span data-ttu-id="03515-157">Seu manipulador de alteração de tema está no local, mas você precisa de algum código que responda às alterações e alinhe as cores da guia com o tema atual.</span><span class="sxs-lookup"><span data-stu-id="03515-157">Your theme change handler is in place, but you need some code that responds to those changes and aligns your tab's colors with the current theme.</span></span>

> [!NOTE]
> <span data-ttu-id="03515-158">O exemplo a seguir é apenas uma maneira de aplicar estilos à sua guia. Use o código como está, expanda nele ou escreva seu próprio.</span><span class="sxs-lookup"><span data-stu-id="03515-158">The following example is just one way you might apply styles to your tab. Use the code as is, expand on it, or write your own.</span></span>

<span data-ttu-id="03515-159">Armazenar o estado fornecido pelo manipulador de alteração de tema no `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="03515-159">Store the state provided by the theme change handler in `isTheme`.</span></span>

```JavaScript
  const isTheme = this.state.theme
```

<span data-ttu-id="03515-160">Forneça algumas lógicas condicionais para renderizar os estilos da guia com base no tema atual.</span><span class="sxs-lookup"><span data-stu-id="03515-160">Provide some conditional logic to render your tab's styles based on the current theme.</span></span> <span data-ttu-id="03515-161">O exemplo a seguir mostra uma maneira básica de fazer isso por 1) verificando o tema atual em `isTheme` , 2) criando um `newTheme` objeto com as propriedades de CSS relevantes para o tema atual e 3) aplicando o CSS ao elemento HTML raiz do conteúdo da guia ( `<div>` ).</span><span class="sxs-lookup"><span data-stu-id="03515-161">The following example shows a basic way to do this by 1) checking the current theme in `isTheme`, 2) creating a `newTheme` object with CSS properties relevant to the current theme, and 3) applying the CSS to your tab content's root HTML element (`<div>`).</span></span>

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

<span data-ttu-id="03515-162">Verifique sua guia no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="03515-162">Check your tab in Teams.</span></span> <span data-ttu-id="03515-163">A aparência deve corresponder ao tema escuro.</span><span class="sxs-lookup"><span data-stu-id="03515-163">The appearance should closely match the dark theme.</span></span>

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-updated-theme.png" alt-text="Captura de tela de uma guia pessoal com visualização de conteúdo estático.":::

## <a name="well-done"></a><span data-ttu-id="03515-165">Muito bem</span><span class="sxs-lookup"><span data-stu-id="03515-165">Well done</span></span>

<span data-ttu-id="03515-166">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="03515-166">Congratulations!</span></span> <span data-ttu-id="03515-167">Você tem um aplicativo do teams com uma guia pessoal que facilita a localização de contatos importantes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="03515-167">You have a Teams app with a personal tab that makes it easier to find important contacts in your organization.</span></span>

## <a name="learn-more"></a><span data-ttu-id="03515-168">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="03515-168">Learn more</span></span>

* <span data-ttu-id="03515-169">[Guia autenticar usuários com SSO](../tabs/how-to/authentication/auth-aad-sso.md): se você quiser apenas que usuários autorizados exibam sua guia, configure o logon único (SSO) por meio do Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="03515-169">[Authenticate tab users with SSO](../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="03515-170">[Inserir conteúdo de um aplicativo Web existente ou página da Web](../tabs/how-to/add-tab.md#tab-requirements): mostramos como criar novo conteúdo para uma guia pessoal, mas você também pode carregar o conteúdo de uma URL externa.</span><span class="sxs-lookup"><span data-stu-id="03515-170">[Embed content from an existing web app or webpage](../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="03515-171">[Criar uma experiência perfeita para sua guia](../tabs/design/tabs.md): consulte as diretrizes recomendadas para a criação de guias do teams.</span><span class="sxs-lookup"><span data-stu-id="03515-171">[Create a seamless experience for your tab](../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="03515-172">[Criar guias para celular](../tabs/design/tabs-mobile.md): entenda como desenvolver guias para telefones e tablets.</span><span class="sxs-lookup"><span data-stu-id="03515-172">[Build tabs for mobile](../tabs/design/tabs-mobile.md): Understand how to develop tabs for phones and tablets.</span></span>
* [<span data-ttu-id="03515-173">Usar os dados do teams com a API do Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="03515-173">Utilize Teams data with the Microsoft Graph API</span></span>](https://docs.microsoft.com/graph/teams-concept-overview)
* [<span data-ttu-id="03515-174">Criar uma guia sem o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="03515-174">Create a tab without the toolkit</span></span>](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a><span data-ttu-id="03515-175">Próxima lição</span><span class="sxs-lookup"><span data-stu-id="03515-175">Next lesson</span></span>

<span data-ttu-id="03515-176">Você sabe como criar uma guia para uso pessoal.</span><span class="sxs-lookup"><span data-stu-id="03515-176">You know how to build a tab for personal use.</span></span> <span data-ttu-id="03515-177">Vejamos o que é necessário para criar uma guia para os canais de equipe e chats.</span><span class="sxs-lookup"><span data-stu-id="03515-177">Let's look at what it takes to build a tab for team channels and chats.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="03515-178">Construir uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="03515-178">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
