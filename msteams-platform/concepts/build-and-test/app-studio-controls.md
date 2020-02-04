---
title: Usando a biblioteca de controle
description: Como usar a biblioteca de controle fornecida pelo Microsoft Teams app Studio
keywords: Biblioteca de controle do teams app Studio
ms.openlocfilehash: d817f55bd75216f77375b7848c5c32cbd29304c2
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672573"
---
# <a name="using-the-control-library-in-app-studio"></a><span data-ttu-id="39831-104">Usando a biblioteca de controle no app Studio</span><span class="sxs-lookup"><span data-stu-id="39831-104">Using the control library in App Studio</span></span>

<span data-ttu-id="39831-105">O [Microsoft Teams app Studio](~/get-started/get-started-app-studio.md) fornece um conjunto de controles que você pode usar em seus próprios aplicativos.</span><span class="sxs-lookup"><span data-stu-id="39831-105">[Microsoft Teams App Studio](~/get-started/get-started-app-studio.md) provides you with a set of controls that you can use in your own apps.</span></span> <span data-ttu-id="39831-106">Esses controles são fornecidos na guia *biblioteca de controle* do App Studio.</span><span class="sxs-lookup"><span data-stu-id="39831-106">These controls are provided in the *Control Library* tab of App Studio.</span></span>

<span data-ttu-id="39831-107">Esses controles foram criados pelos designers do Microsoft Teams para simplificar seus próprios fluxos de trabalho, padronizar o comportamento de controle e os temas padrão da equipe de suporte.</span><span class="sxs-lookup"><span data-stu-id="39831-107">These controls were created by the Microsoft Teams designers to streamline their own workflows, standardize control behavior and support Team's default themes.</span></span> <span data-ttu-id="39831-108">Você pode usar essa biblioteca em seus próprios aplicativos para obter uma aparência unificada.</span><span class="sxs-lookup"><span data-stu-id="39831-108">You can use this library in your own apps to achieve a unified look and feel.</span></span>

<span data-ttu-id="39831-109">Os controles incluem:</span><span class="sxs-lookup"><span data-stu-id="39831-109">Controls include:</span></span>

* <span data-ttu-id="39831-110">Botões</span><span class="sxs-lookup"><span data-stu-id="39831-110">Buttons</span></span>
* <span data-ttu-id="39831-111">Menus suspensos</span><span class="sxs-lookup"><span data-stu-id="39831-111">Dropdowns</span></span>
* <span data-ttu-id="39831-112">Caixas</span><span class="sxs-lookup"><span data-stu-id="39831-112">Checkboxes</span></span>
* <span data-ttu-id="39831-113">Botões de opção</span><span class="sxs-lookup"><span data-stu-id="39831-113">Radio Buttons</span></span>
* <span data-ttu-id="39831-114">Alterna</span><span class="sxs-lookup"><span data-stu-id="39831-114">Toggles</span></span>
* <span data-ttu-id="39831-115">Áreas de teste</span><span class="sxs-lookup"><span data-stu-id="39831-115">Test Areas</span></span>
* <span data-ttu-id="39831-116">Links</span><span class="sxs-lookup"><span data-stu-id="39831-116">Links</span></span>
* <span data-ttu-id="39831-117">Guias</span><span class="sxs-lookup"><span data-stu-id="39831-117">Tabs</span></span>
* <span data-ttu-id="39831-118">Tabelas</span><span class="sxs-lookup"><span data-stu-id="39831-118">Tables</span></span>
* <span data-ttu-id="39831-119">Ícones</span><span class="sxs-lookup"><span data-stu-id="39831-119">Icons</span></span>

## <a name="optionally-use-react-controls"></a><span data-ttu-id="39831-120">Opcionalmente, use os controles de reagir</span><span class="sxs-lookup"><span data-stu-id="39831-120">Optionally use React controls</span></span>

<span data-ttu-id="39831-121">A biblioteca de controle do Microsoft Teams usa a [estrutura de interface do usuário do JavaScript](https://reactjs.org/) , no entanto, ela é criada de forma que não seja associada a uma estrutura de interface do usuário específica.</span><span class="sxs-lookup"><span data-stu-id="39831-121">The full Teams control library uses the [React JavaScript UI framework](https://reactjs.org/) however it is built so that it is not tied to a specific UI framework.</span></span> <span data-ttu-id="39831-122">Há quatro pacotes do NPM diferentes:</span><span class="sxs-lookup"><span data-stu-id="39831-122">There are four different npm packages:</span></span>

* <span data-ttu-id="39831-123">**msteams-UI-Styles-Core** Os principais estilos CSS dos componentes da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="39831-123">**msteams-ui-styles-core** The core CSS styles of UI components.</span></span> <span data-ttu-id="39831-124">É independente de qualquer estrutura de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="39831-124">It’s independent of any UI framework.</span></span>
* <span data-ttu-id="39831-125">**msteams-UI-ícones-núcleo** O conjunto principal de ícones do teams.</span><span class="sxs-lookup"><span data-stu-id="39831-125">**msteams-ui-icons-core** The core set of Teams icons.</span></span>
* <span data-ttu-id="39831-126">**msteams-UI-Components-reagir** A biblioteca de associação reagem.</span><span class="sxs-lookup"><span data-stu-id="39831-126">**msteams-ui-components-react** The React binding library.</span></span> <span data-ttu-id="39831-127">Depende de msteams-UI-Styles-Core.</span><span class="sxs-lookup"><span data-stu-id="39831-127">It depends on msteams-ui-styles-core.</span></span>
* <span data-ttu-id="39831-128">**msteams-UI-ícones-reagir** A biblioteca de associação reagir para o conjunto de ícones do teams.</span><span class="sxs-lookup"><span data-stu-id="39831-128">**msteams-ui-icons-react** The React binding library for the set of Teams icons.</span></span> <span data-ttu-id="39831-129">Depende de msteams-UI-ícones-Core.</span><span class="sxs-lookup"><span data-stu-id="39831-129">It depends on msteams-ui-icons-core.</span></span>

<span data-ttu-id="39831-130">Essas bibliotecas são todas abertas e você pode usar o msteams-UI-Styles-Core e o msteams-UI-ícones-Core sem reagir.</span><span class="sxs-lookup"><span data-stu-id="39831-130">These libraries are all open source, and you can use msteams-ui-styles-core and msteams-ui-icons-core without React.</span></span>

## <a name="adding-the-control-library"></a><span data-ttu-id="39831-131">Adicionando a biblioteca de controle</span><span class="sxs-lookup"><span data-stu-id="39831-131">Adding the control library</span></span>

<span data-ttu-id="39831-132">Instale a biblioteca de controle e sua dependência `typestyle`de pares:</span><span class="sxs-lookup"><span data-stu-id="39831-132">Install the control library and its peer dependency `typestyle`:</span></span>

```terminal
npm install --save typestyle && npm install --save msteams-ui-components-react
```

<span data-ttu-id="39831-133">*Opcional:* Instale os ícones do teams.</span><span class="sxs-lookup"><span data-stu-id="39831-133">*Optional:* Install the Teams icons.</span></span>

```terminal
npm install --save msteams-ui-icons-react
```

<span data-ttu-id="39831-134">Localize e abra `src/App.js` e substitua seu conteúdo pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="39831-134">Find and open `src/App.js` and replace its content with following code:</span></span>

```javascript
import React, { Component } from ‘react’;
import { TeamsComponentContext, ThemeStyle, PrimaryButton } from ‘msteams-ui-components-react’

class App extends Component {
   render() {
      // Sets up the top-level context for the library. It accepts global
      // configurations such as font size and theme. fontSize is your page’s
      // default font size. We made it a parameter so that you could use this
      // library with CSS frameworks such as Bootstrap. Some CSS frameworks
      // set the default font size for the page; retrieve it and use it
      // instead of {16} in the block.
      // This library uses the power of CSS to do most of the work for you.
      // Instead of passing themes as a parameter to every UI component,
      // we set it on a parent HTML element. All HTML elements nested within
      // that parent will inherit these properties.

      return (
        <TeamsComponentContext
            fontSize={16}
            theme={ThemeStyle.Light}
        />
      );
   }
}
export default App;
```

<span data-ttu-id="39831-135">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="39831-135">Run the app</span></span>

```terminal
npm run start
```

<span data-ttu-id="39831-136">Ao navegar até http://localhost:3000, você verá a seguinte tela:</span><span class="sxs-lookup"><span data-stu-id="39831-136">When you navigate to http://localhost:3000, you should see the following screen:</span></span>

<img width="530px" src="~/assets/images/get-started/control-library-button.png" title="Botão biblioteca de controle"/>

## <a name="dynamically-handling-theme-changes"></a><span data-ttu-id="39831-138">Manipulação dinâmica de alterações de temas</span><span class="sxs-lookup"><span data-stu-id="39831-138">Dynamically handling theme changes</span></span>

<span data-ttu-id="39831-139">Seu aplicativo precisa lidar com temas quando:</span><span class="sxs-lookup"><span data-stu-id="39831-139">Your app needs to handle themes when:</span></span>

* <span data-ttu-id="39831-140">A guia é inicialmente carregada</span><span class="sxs-lookup"><span data-stu-id="39831-140">The tab is initially loaded</span></span>
* <span data-ttu-id="39831-141">Um usuário altera o tema após a guia já ter sido carregada</span><span class="sxs-lookup"><span data-stu-id="39831-141">A user changes the theme after the tab is already loaded</span></span>

<span data-ttu-id="39831-142">O tema é incluído no [contexto](/javascript/api/@microsoft/teams-js/context&view=msteams-client-js-latest)de uma guia, que pode ser recuperado antes de a guia ser carregada por valores de espaço reservado de URL ou a qualquer momento usando o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/%40microsoft/teams-js/context).</span><span class="sxs-lookup"><span data-stu-id="39831-142">The theme is included in a tab’s [Context](/javascript/api/@microsoft/teams-js/context&view=msteams-client-js-latest), which can be retrieved before the tab is loaded via URL placeholder values, or at any time by using the [Microsoft Teams JavaScript client SDK](/javascript/api/%40microsoft/teams-js/context).</span></span>

<span data-ttu-id="39831-143">Como o tema atual é recuperado e como responder às alterações de temas é discutido aqui: [obter contexto para a guia do Microsoft Teams](~/concepts/tabs/tabs-context.md).</span><span class="sxs-lookup"><span data-stu-id="39831-143">How the current theme is retrieved and how to respond to theme changes is discussed here: [Get context for your Microsoft Teams tab](~/concepts/tabs/tabs-context.md).</span></span>

<span data-ttu-id="39831-144">Este código de exemplo mostra como isso é feito.</span><span class="sxs-lookup"><span data-stu-id="39831-144">This sample code shows how this is done.</span></span>

```js
componentWillMount() {
    // If you are deploying your site as a MS Teams static or configurable tab,
    // you should add “?theme={theme}” to your tabs URL in the manifest.
    // That way you will get the current theme before it’s loaded; getContext()
    // is called only after the tab is loaded, which will cause the tab to flash
    // if the current theme is different than the default.
    this.updateTheme(this.getQueryVariable('theme'));
    this.setState({
        fontSize: this.pageFontSize(),
    });

    // If you are not using the MS Teams Javascript SDK, you can remove this entire
    // if block, but if you want theme changes in the MS Teams client to propagate
    // to the tab, leave it here.
    microsoftTeams.initialize();
    microsoftTeams.registerOnThemeChangeHandler(this.updateTheme);
}
```

## <a name="connect-your-own-component-to-the-teamscomponentcontext"></a><span data-ttu-id="39831-145">Conectar seu próprio componente ao TeamsComponentContext</span><span class="sxs-lookup"><span data-stu-id="39831-145">Connect your own component to the TeamsComponentContext</span></span>

<span data-ttu-id="39831-146">Se você quiser usar seu próprio código CSS, ainda poderá responder às alterações de tema e usar cores definidas pelo Teams.</span><span class="sxs-lookup"><span data-stu-id="39831-146">If you want to use your own CSS code you can still respond to theme changes and use colors defined by teams.</span></span> <span data-ttu-id="39831-147">O TeamsComponentContext permite que você faça isso.</span><span class="sxs-lookup"><span data-stu-id="39831-147">TeamsComponentContext allows you to do this.</span></span>

<span data-ttu-id="39831-148">Novamente, edite o `src/App.js` arquivo e substitua o conteúdo pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="39831-148">Once again, edit your `src/App.js` file and replace its content with following code:</span></span>

```javascript
import React, { Component } from ‘react’;
import { TeamsComponentContext, ThemeStyle, ConnectedComponent } from ‘msteams-ui-components-react’

class App extends Component {
    render() {
        return (
            <TeamsComponentContext
                fontSize={16}
                theme={ThemeStyle.HighContrast}>
                <MyComponent />
            </TeamsComponentContext>
        );
    }
}

class MyComponent extends Component {
    render() {
        return (
            <ConnectedComponent render={(props) => {
                const context = props.context;

                switch (context.style) {
                case ThemeStyle.Dark:
                    return <div style={{ color: context.colors.dark.brand00 }}>Dark theme!</div>;
                case ThemeStyle.HighContrast:
                    return <div style={{ color: context.colors.highContrast.black }}>High Contrast theme!</div>;
                case ThemeStyle.Light:
                    return <div style={{ color: context.colors.light.brand00 }}>Light theme!</div>;
                }
            }} />
        );
    }
}

export default App;
```

<span data-ttu-id="39831-149">Nesse código, um novo componente é definido chamado myComponent.</span><span class="sxs-lookup"><span data-stu-id="39831-149">In this code, a new component is defined called MyComponent.</span></span> <span data-ttu-id="39831-150">Em seguida, um componente especial da biblioteca de controle chamado ConnectedComponent é adicionado.</span><span class="sxs-lookup"><span data-stu-id="39831-150">Then a special component from the control library called ConnectedComponent is added.</span></span> <span data-ttu-id="39831-151">ConnectedComponent tem uma propriedade chamada `render` que tem uma função como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="39831-151">ConnectedComponent has a property called `render` which takes a function as a parameter.</span></span> <span data-ttu-id="39831-152">No momento da renderização, essa função será chamada com o contexto apropriado para sua guia. O contexto inclui o tema em que a página está sendo renderizada, bem como o objeto Color global, que você pode usar para aplicar as cores do teams à sua guia. Como você pode ver na `switch` instrução, o apropriado `<div>` é escolhido com base no tema.</span><span class="sxs-lookup"><span data-stu-id="39831-152">At render time this function will be called with the appropriate context for your tab. The context includes the theme that the page is being rendered in as well as the global color object that you can use to apply Teams colors to your tab. As you can see in the `switch` statement, the appropriate `<div>` is chosen based on the theme.</span></span>

<span data-ttu-id="39831-153">Para alterar os temas, precisamos passar o nível de raiz TeamsComponentContext um tema diferente.</span><span class="sxs-lookup"><span data-stu-id="39831-153">To change themes, we need to pass the root-level TeamsComponentContext a different theme.</span></span> <span data-ttu-id="39831-154">Quando um tema é alterado, todos os elementos filho dispostos no ConnectedComponent serão renderizados novamente.</span><span class="sxs-lookup"><span data-stu-id="39831-154">When a theme changes, all the child elements wrapped in ConnectedComponent will be re-rendered.</span></span> <span data-ttu-id="39831-155">Consulte a seção anterior "lidar dinamicamente com alterações de tema".</span><span class="sxs-lookup"><span data-stu-id="39831-155">See previous section “Dynamically Handle Theme Changes.”</span></span>

<span data-ttu-id="39831-156">Há outras maneiras de conectar seu componente ao TeamsComponentContext.</span><span class="sxs-lookup"><span data-stu-id="39831-156">There are other ways to connect your component to TeamsComponentContext.</span></span> <span data-ttu-id="39831-157">Se estiver familiarizado com o [Redux](https://redux.js.org/basics/usage-with-react), você pode preferir o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="39831-157">If you’re familiar with [Redux](https://redux.js.org/basics/usage-with-react), you may prefer the following pattern:</span></span>

```js
import React, { Component } from ‘react’;
import { TeamsComponentContext, ThemeStyle, connectTeamsComponent } from ‘msteams-ui-components-react’

class App extends Component {
    render() {
        return (
            <TeamsComponentContext
                fontSize={16}
                theme={ThemeStyle.HighContrast}>
                <MyComponent />
            </TeamsComponentContext>
        );
    }
}

class MyComponentInner extends Component {
    render() {
        const context = this.props.context;
        switch (context.style) {
            case ThemeStyle.Dark:
                return <div style={{ color: context.colors.dark.brand00 }}>Dark theme!</div>;
            case ThemeStyle.HighContrast:
                return <div style={{ color: context.colors.highContrast.black }}>High Contrast theme!</div>;
            case ThemeStyle.Light:
                return <div style={{ color: context.colors.light.brand00 }}>Light theme!</div>;
        }
    }
}

const MyComponent = connectTeamsComponent(MyComponentInner);

export default App;
```

<span data-ttu-id="39831-158">Neste método, em vez de usar o ConnectedComponent, você usa a função connectTeamsComponent.</span><span class="sxs-lookup"><span data-stu-id="39831-158">In this method, instead of using ConnectedComponent, you use the connectTeamsComponent function.</span></span> <span data-ttu-id="39831-159">A função connectTeamsComponent leva seu componente atual e retorna um novo componente com o objeto Context injetado.</span><span class="sxs-lookup"><span data-stu-id="39831-159">The connectTeamsComponent function takes your current component and returns a new component with the context object injected.</span></span>

## <a name="next-steps"></a><span data-ttu-id="39831-160">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="39831-160">Next steps</span></span>

<span data-ttu-id="39831-161">Head to Teams app Studio e confira todos os controles que oferecemos e exemplos de código para usá-los.</span><span class="sxs-lookup"><span data-stu-id="39831-161">Head to Teams App Studio and check out all the controls we offer and sample code of how to use them.</span></span> <span data-ttu-id="39831-162">Não se esqueça de explorá-las em temas diferentes.</span><span class="sxs-lookup"><span data-stu-id="39831-162">Don’t forget to explore them in different themes.</span></span>