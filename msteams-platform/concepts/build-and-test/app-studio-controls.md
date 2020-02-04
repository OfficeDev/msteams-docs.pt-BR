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
# <a name="using-the-control-library-in-app-studio"></a>Usando a biblioteca de controle no app Studio

O [Microsoft Teams app Studio](~/get-started/get-started-app-studio.md) fornece um conjunto de controles que você pode usar em seus próprios aplicativos. Esses controles são fornecidos na guia *biblioteca de controle* do App Studio.

Esses controles foram criados pelos designers do Microsoft Teams para simplificar seus próprios fluxos de trabalho, padronizar o comportamento de controle e os temas padrão da equipe de suporte. Você pode usar essa biblioteca em seus próprios aplicativos para obter uma aparência unificada.

Os controles incluem:

* Botões
* Menus suspensos
* Caixas
* Botões de opção
* Alterna
* Áreas de teste
* Links
* Guias
* Tabelas
* Ícones

## <a name="optionally-use-react-controls"></a>Opcionalmente, use os controles de reagir

A biblioteca de controle do Microsoft Teams usa a [estrutura de interface do usuário do JavaScript](https://reactjs.org/) , no entanto, ela é criada de forma que não seja associada a uma estrutura de interface do usuário específica. Há quatro pacotes do NPM diferentes:

* **msteams-UI-Styles-Core** Os principais estilos CSS dos componentes da interface do usuário. É independente de qualquer estrutura de interface do usuário.
* **msteams-UI-ícones-núcleo** O conjunto principal de ícones do teams.
* **msteams-UI-Components-reagir** A biblioteca de associação reagem. Depende de msteams-UI-Styles-Core.
* **msteams-UI-ícones-reagir** A biblioteca de associação reagir para o conjunto de ícones do teams. Depende de msteams-UI-ícones-Core.

Essas bibliotecas são todas abertas e você pode usar o msteams-UI-Styles-Core e o msteams-UI-ícones-Core sem reagir.

## <a name="adding-the-control-library"></a>Adicionando a biblioteca de controle

Instale a biblioteca de controle e sua dependência `typestyle`de pares:

```terminal
npm install --save typestyle && npm install --save msteams-ui-components-react
```

*Opcional:* Instale os ícones do teams.

```terminal
npm install --save msteams-ui-icons-react
```

Localize e abra `src/App.js` e substitua seu conteúdo pelo seguinte código:

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

Executar o aplicativo

```terminal
npm run start
```

Ao navegar até http://localhost:3000, você verá a seguinte tela:

<img width="530px" src="~/assets/images/get-started/control-library-button.png" title="Botão biblioteca de controle"/>

## <a name="dynamically-handling-theme-changes"></a>Manipulação dinâmica de alterações de temas

Seu aplicativo precisa lidar com temas quando:

* A guia é inicialmente carregada
* Um usuário altera o tema após a guia já ter sido carregada

O tema é incluído no [contexto](/javascript/api/@microsoft/teams-js/context&view=msteams-client-js-latest)de uma guia, que pode ser recuperado antes de a guia ser carregada por valores de espaço reservado de URL ou a qualquer momento usando o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/%40microsoft/teams-js/context).

Como o tema atual é recuperado e como responder às alterações de temas é discutido aqui: [obter contexto para a guia do Microsoft Teams](~/concepts/tabs/tabs-context.md).

Este código de exemplo mostra como isso é feito.

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

## <a name="connect-your-own-component-to-the-teamscomponentcontext"></a>Conectar seu próprio componente ao TeamsComponentContext

Se você quiser usar seu próprio código CSS, ainda poderá responder às alterações de tema e usar cores definidas pelo Teams. O TeamsComponentContext permite que você faça isso.

Novamente, edite o `src/App.js` arquivo e substitua o conteúdo pelo seguinte código:

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

Nesse código, um novo componente é definido chamado myComponent. Em seguida, um componente especial da biblioteca de controle chamado ConnectedComponent é adicionado. ConnectedComponent tem uma propriedade chamada `render` que tem uma função como um parâmetro. No momento da renderização, essa função será chamada com o contexto apropriado para sua guia. O contexto inclui o tema em que a página está sendo renderizada, bem como o objeto Color global, que você pode usar para aplicar as cores do teams à sua guia. Como você pode ver na `switch` instrução, o apropriado `<div>` é escolhido com base no tema.

Para alterar os temas, precisamos passar o nível de raiz TeamsComponentContext um tema diferente. Quando um tema é alterado, todos os elementos filho dispostos no ConnectedComponent serão renderizados novamente. Consulte a seção anterior "lidar dinamicamente com alterações de tema".

Há outras maneiras de conectar seu componente ao TeamsComponentContext. Se estiver familiarizado com o [Redux](https://redux.js.org/basics/usage-with-react), você pode preferir o seguinte padrão:

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

Neste método, em vez de usar o ConnectedComponent, você usa a função connectTeamsComponent. A função connectTeamsComponent leva seu componente atual e retorna um novo componente com o objeto Context injetado.

## <a name="next-steps"></a>Próximas etapas

Head to Teams app Studio e confira todos os controles que oferecemos e exemplos de código para usá-los. Não se esqueça de explorá-las em temas diferentes.