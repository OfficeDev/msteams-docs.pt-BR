---
title: Criar uma guia pessoal para o Microsoft Teams
author: heath-hamilton
description: Saiba como criar uma guia pessoal no seu primeiro aplicativo do Microsoft Teams.
ms.topic: tutorial
ms.openlocfilehash: 1c782adce2201550d30d658907d507dc6a1337f3
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651863"
---
# <a name="create-a-personal-tab-for-teams"></a><span data-ttu-id="d8f8c-103">Criar uma guia pessoal para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d8f8c-103">Create a personal tab for Teams</span></span>

<span data-ttu-id="d8f8c-104">As guias são uma maneira simples de fazer a superfície de conteúdo em seu aplicativo, incorporando essencialmente uma página da Web no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-104">Tabs are a simple way to surface content in your app by essentially embedding a webpage in Teams.</span></span>

<span data-ttu-id="d8f8c-105">Há dois tipos de guias no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-105">There are two types of tabs in Teams.</span></span> <span data-ttu-id="d8f8c-106">Neste tutorial, você criará uma *guia pessoal*, uma página de conteúdo de tela inteira para usuários individuais.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-106">In this tutorial, you'll build basic a *personal tab*, a full-screen content page for individual users.</span></span> <span data-ttu-id="d8f8c-107">(As guias pessoais são as coisas mais próximas de uma experiência de site tradicional no Microsoft Teams.)</span><span class="sxs-lookup"><span data-stu-id="d8f8c-107">(Personal tabs are the closest thing to a traditional website experience in Teams.)</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="d8f8c-108">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="d8f8c-108">Before you begin</span></span>

<span data-ttu-id="d8f8c-109">Você precisa de um aplicativo básico em execução para começar.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-109">You need a basic running app to get started.</span></span> <span data-ttu-id="d8f8c-110">Se você não tiver um, confira [Compilar e executar seu primeiro aplicativo do Microsoft Teams](build-and-run-with-toolkit.md).</span><span class="sxs-lookup"><span data-stu-id="d8f8c-110">If you don't have one, see [build and run your first Teams app](build-and-run-with-toolkit.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="d8f8c-111">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="d8f8c-111">Your assignment</span></span>

<span data-ttu-id="d8f8c-112">As pessoas da sua organização têm problemas para localizar informações básicas de contato para funções importantes (Help Desk, HR, etc.).</span><span class="sxs-lookup"><span data-stu-id="d8f8c-112">People in your organization have trouble finding basic contact information for important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="d8f8c-113">Você está encarregado de garantir que eles possam encontrar rapidamente essas informações em um só lugar.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-113">You're in charge of making sure they can quickly find this information in one place.</span></span> <span data-ttu-id="d8f8c-114">Como fazer isso?</span><span class="sxs-lookup"><span data-stu-id="d8f8c-114">How would you do that?</span></span> <span data-ttu-id="d8f8c-115">Uma guia pessoal do Teams, naturalmente.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-115">A Teams personal tab, of course.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="d8f8c-116">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="d8f8c-116">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d8f8c-117">Identificar as propriedades de manifesto do aplicativo e scaffolding relevantes para guias pessoais</span><span class="sxs-lookup"><span data-stu-id="d8f8c-117">Identify the app manifest properties and scaffolding relevant to personal tabs</span></span>
> * <span data-ttu-id="d8f8c-118">Criar conteúdo para sua guia</span><span class="sxs-lookup"><span data-stu-id="d8f8c-118">Create content for your tab</span></span>
> * <span data-ttu-id="d8f8c-119">Atualizar o tema de cores da guia com base na preferência do usuário</span><span class="sxs-lookup"><span data-stu-id="d8f8c-119">Update your tab's color theme based on user preference</span></span>

## <a name="identify-relevant-app-manifest-and-scaffolding-components"></a><span data-ttu-id="d8f8c-120">Identificar manifesto de aplicativo relevante e componentes do scaffolding</span><span class="sxs-lookup"><span data-stu-id="d8f8c-120">Identify relevant app manifest and scaffolding components</span></span>

<span data-ttu-id="d8f8c-121">Grande parte do aplicativo de guia scaffolding e do manifesto é configurada automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-121">Much of the personal tab app scaffolding and manifest is set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="d8f8c-122">Vamos examinar os principais componentes para criar uma guia pessoal.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-122">Let's look at the main components for building a personal tab.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="d8f8c-123">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d8f8c-123">App manifest</span></span>

<span data-ttu-id="d8f8c-124">O trecho de código a seguir do manifesto de aplicativo (o `manifest.json` arquivo no diretório do seu projeto `.publish` ) mostra [`staticTabs`](../../resources/schema/manifest-schema.md#statictabs) , que inclui propriedades e valores padrão relevantes para guias pessoais.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-124">The following snippet from the app manifest (the `manifest.json` file in your project's `.publish` directory) shows [`staticTabs`](../../resources/schema/manifest-schema.md#statictabs), which includes properties and default values relevant to personal tabs.</span></span>

```JSON
    "staticTabs": [
        {
            "entityId": "index",
            "name": "Personal Tab",
            "contentUrl": "{baseUrl0}/tab",
            "scopes": [ "personal" ]
        }
    ],
```

* <span data-ttu-id="d8f8c-125">`entityId`: Um identificador exclusivo para a página exibida pela guia.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-125">`entityId`: A unique identifier for the page displayed by the tab.</span></span>
* <span data-ttu-id="d8f8c-126">`name`: O nome de exibição da guia (por exemplo, "meus contatos").</span><span class="sxs-lookup"><span data-stu-id="d8f8c-126">`name`: The tab's display name (for example, "My Contacts").</span></span>
* <span data-ttu-id="d8f8c-127">`contentUrl`: A URL do host da página de conteúdo da guia (deve ser HTTPS).</span><span class="sxs-lookup"><span data-stu-id="d8f8c-127">`contentUrl`: The host URL the tab content page (must be HTTPS).</span></span>
* <span data-ttu-id="d8f8c-128">`scopes`: Especifica a guia é somente para uso pessoal.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-128">`scopes`: Specifies the tab is for personal use only.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="d8f8c-129">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="d8f8c-129">App scaffolding</span></span>

<span data-ttu-id="d8f8c-130">O aplicativo scaffolding fornece os componentes para renderizar sua guia no Teams.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-130">The app scaffolding provides the components for rendering your tab in Teams.</span></span> <span data-ttu-id="d8f8c-131">Há muitas coisas com as quais você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:</span><span class="sxs-lookup"><span data-stu-id="d8f8c-131">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="d8f8c-132">`Tab.js`arquivo no `src/components` diretório do projeto</span><span class="sxs-lookup"><span data-stu-id="d8f8c-132">`Tab.js` file in the `src/components` directory of your project</span></span>
* <span data-ttu-id="d8f8c-133">SDK do cliente JavaScript do Microsoft Teams, que vem pré-carregado nos componentes front-end do seu projeto</span><span class="sxs-lookup"><span data-stu-id="d8f8c-133">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components</span></span>

## <a name="create-your-tab-content"></a><span data-ttu-id="d8f8c-134">Criar seu conteúdo de guia</span><span class="sxs-lookup"><span data-stu-id="d8f8c-134">Create your tab content</span></span>

<span data-ttu-id="d8f8c-135">Compilar uma lista de contatos importantes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-135">Compile a list of important contacts in your organization.</span></span> <span data-ttu-id="d8f8c-136">Copie e atualize o trecho de código a seguir com informações relevantes para você ou, para fins de tempo, use o código como está.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-136">Copy and update the following snippet with information that's relevant to you or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="d8f8c-137">Vá para o `src/components` diretório e abra `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="d8f8c-137">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="d8f8c-138">Localize a `render()` função e cole o conteúdo dentro `return()` (conforme mostrado).</span><span class="sxs-lookup"><span data-stu-id="d8f8c-138">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="d8f8c-139">Adicione a regra a seguir para `App.css` que os links de email sejam mais fáceis de ler, independentemente de qual tema é usado.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-139">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
  a {
    color: inherit;
  }
```

<span data-ttu-id="d8f8c-140">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-140">Save your changes.</span></span> <span data-ttu-id="d8f8c-141">Vá para a guia do aplicativo no Microsoft Teams para exibir o novo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-141">Go to your app's tab in Teams to view the new content.</span></span>

![Captura de tela de exemplo de uma guia pessoal com conteúdo estático](../doc-links/images/personal-tab-tutorial-content.png)

## <a name="update-the-tab-theme"></a><span data-ttu-id="d8f8c-143">Atualizar o tema da guia</span><span class="sxs-lookup"><span data-stu-id="d8f8c-143">Update the tab theme</span></span>

<span data-ttu-id="d8f8c-144">Bons aplicativos se sentem nativos para o Microsoft Teams, portanto, é importante que as mesclagens de tabulação com o tema do teams que seus usuários preferem: padrão (claro), escuro ou alto contraste.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-144">Good apps feel native to Teams, so it's important your tab blends with the Teams theme your users prefer: default (light), dark, or high contrast.</span></span> <span data-ttu-id="d8f8c-145">Como você pode ter notado na última captura de tela, sua guia ainda tem um plano de fundo claro quando o cliente está usando o tema escuro.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-145">As you might have noticed in the last screenshot, your tab still has a light background when the client's using the dark theme.</span></span> <span data-ttu-id="d8f8c-146">Essa não é uma experiência de usuário recomendada.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-146">This is not a recommended user experience.</span></span>

<span data-ttu-id="d8f8c-147">O [SDK de cliente do Microsoft Teams](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest) pode tornar seu aplicativo ciente e reagir às alterações de tema no cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-147">The [Teams JavaScript client SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest) can make your app aware of and react to theme changes in the client.</span></span> <span data-ttu-id="d8f8c-148">Vamos examinar como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-148">Let's walk through how to do this.</span></span>

### <a name="get-context-about-the-teams-client"></a><span data-ttu-id="d8f8c-149">Obter contexto sobre o cliente Teams</span><span class="sxs-lookup"><span data-stu-id="d8f8c-149">Get context about the Teams client</span></span>

<span data-ttu-id="d8f8c-150">No `Tab.js` arquivo, há uma `microsoftTeams.getContext()` chamada que fornece alguns [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) , entre outros detalhes, o tema de cliente configurado.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-150">In your `Tab.js` file, there's a `microsoftTeams.getContext()` call that provides some [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) about, among other details, the configured client theme.</span></span> <span data-ttu-id="d8f8c-151">Graças ao aplicativo scaffolding, use este código como é para acessar a `context` interface e suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-151">Thanks to the app scaffolding, use this code as is to access the `context` interface and its properties.</span></span>

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

### <a name="create-a-theme-change-handler"></a><span data-ttu-id="d8f8c-152">Criar um manipulador de alteração de temas</span><span class="sxs-lookup"><span data-stu-id="d8f8c-152">Create a theme change handler</span></span>

<span data-ttu-id="d8f8c-153">Com as `context` Propriedades em mãos, seu aplicativo tem uma compreensão sólida do que está acontecendo em relação ao Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-153">With the `context` properties in hand, your app has a solid understanding of what's happening around it in Teams.</span></span> <span data-ttu-id="d8f8c-154">Mas o aplicativo ainda não sabe que sua aparência deve refletir qualquer tema escolhido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-154">But the app still doesn't know its appearance should reflect whatever theme a user chooses.</span></span>

<span data-ttu-id="d8f8c-155">Você precisa de um manipulador para que o estado do aplicativo seja alterado com o tema.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-155">You need a handler so that your app's state changes with the theme.</span></span> <span data-ttu-id="d8f8c-156">Insira o seguinte manipulador de alteração de tema imediatamente após a `microsoftTeams.getContext()` chamada.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-156">Insert the following theme change handler immediately after the `microsoftTeams.getContext()` call.</span></span>

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a><span data-ttu-id="d8f8c-157">Coincidir estilos de tema</span><span class="sxs-lookup"><span data-stu-id="d8f8c-157">Match theme styles</span></span>

<span data-ttu-id="d8f8c-158">Seu manipulador de alteração de tema está no local, mas você precisa de algum código que responda às alterações e alinhe as cores da guia com o tema atual.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-158">Your theme change handler is in place, but you need some code that responds to those changes and aligns your tab's colors with the current theme.</span></span>

> [!NOTE]
> <span data-ttu-id="d8f8c-159">O exemplo a seguir é apenas uma maneira de aplicar estilos à sua guia. Use o código como está, expanda nele ou escreva o seu próprio.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-159">The following example is just one way you might apply styles to your tab. Use the code as is, expand on it, or write your own.</span></span>

<span data-ttu-id="d8f8c-160">Armazenar o estado fornecido pelo manipulador de alteração de tema no `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="d8f8c-160">Store the state provided by the theme change handler in `isTheme`.</span></span>

```JavaScript
  const isTheme = this.state.theme
```

<span data-ttu-id="d8f8c-161">Forneça algumas lógicas condicionais para renderizar os estilos da guia com base no tema atual.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-161">Provide some conditional logic to render your tab's styles based on the current theme.</span></span> <span data-ttu-id="d8f8c-162">O exemplo a seguir mostra uma maneira básica de fazer isso por 1) verificando o tema atual em `isTheme` , 2) criando um `newTheme` objeto com as propriedades de CSS relevantes para o tema atual e 3) aplicando o CSS ao elemento HTML raiz do conteúdo da guia ( `<div>` ).</span><span class="sxs-lookup"><span data-stu-id="d8f8c-162">The following example shows a basic way to do this by 1) checking the current theme in `isTheme`, 2) creating a `newTheme` object with CSS properties relevant to the current theme, and 3) applying the CSS to your tab content's root HTML element (`<div>`).</span></span>

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

<span data-ttu-id="d8f8c-163">Verifique sua guia no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-163">Check your tab in Teams.</span></span> <span data-ttu-id="d8f8c-164">A aparência deve corresponder ao tema escuro.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-164">The appearance should closely match the dark theme.</span></span>

![Captura de tela de exemplo de uma guia pessoal com conteúdo estático](../doc-links/images/personal-tab-tutorial-updated-theme.png)

## <a name="well-done"></a><span data-ttu-id="d8f8c-166">Muito bem</span><span class="sxs-lookup"><span data-stu-id="d8f8c-166">Well done</span></span>

<span data-ttu-id="d8f8c-167">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="d8f8c-167">Congratulations!</span></span> <span data-ttu-id="d8f8c-168">Você tem um aplicativo do teams com uma guia pessoal que facilita a localização de contatos importantes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-168">You have a Teams app with a personal tab that makes it easier to find important contacts in your organization.</span></span>

## <a name="next-step"></a><span data-ttu-id="d8f8c-169">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="d8f8c-169">Next step</span></span>

<span data-ttu-id="d8f8c-170">Você sabe como criar uma guia para uso pessoal.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-170">You know how to build a tab for personal use.</span></span> <span data-ttu-id="d8f8c-171">Vejamos o que é necessário para criar uma guia para os canais de equipe e chats.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-171">Let's look at what it takes to build a tab for team channels and chats.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d8f8c-172">Criar uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="d8f8c-172">Build a channel tab</span></span>](add-channel-tab.md)

## <a name="learn-more"></a><span data-ttu-id="d8f8c-173">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="d8f8c-173">Learn more</span></span>

* <span data-ttu-id="d8f8c-174">[Guia autenticar usuários com SSO](../../tabs/how-to/authentication/auth-aad-sso.md): se você quiser apenas que usuários autorizados exibam sua guia, configure o logon único (SSO) por meio do Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="d8f8c-174">[Authenticate tab users with SSO](../../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="d8f8c-175">[Inserir conteúdo de um aplicativo Web existente ou página da Web](../../tabs/how-to/add-tab.md#tab-requirements): mostramos como criar novo conteúdo para uma guia pessoal, mas você também pode carregar o conteúdo de uma URL externa.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-175">[Embed content from an existing web app or webpage](../../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="d8f8c-176">[Criar uma experiência perfeita para sua guia](../../tabs/design/tabs.md): consulte as diretrizes recomendadas para a criação de guias do teams.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-176">[Create a seamless experience for your tab](../../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="d8f8c-177">[Criar guias para dispositivos móveis](../../tabs/design/tabs-mobile.md): entenda como desenvolver guias para smartphones e tablets.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-177">[Build tabs for mobile](../../tabs/design/tabs-mobile.md): Understand how to develop tabs for smartphones and tablets.</span></span>

