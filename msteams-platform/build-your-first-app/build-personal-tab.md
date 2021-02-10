---
title: Começar - Criar uma guia pessoal
author: heath-hamilton
description: Crie rapidamente uma guia pessoal do Microsoft Teams usando o Kit de Ferramentas do Microsoft Teams.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: tutorial
ms.openlocfilehash: 083d1425fe43a9b150732aa35bef34e2349c6ea6
ms.sourcegitcommit: b99ed616db734371e4af4594b7e895c5b05737c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50162898"
---
# <a name="build-a-personal-tab-for-microsoft-teams"></a>Criar uma guia pessoal para o Microsoft Teams

As guias são uma maneira simples de surgir conteúdo em seu aplicativo ao incorporar essencialmente uma página da Web no Teams.

Há dois tipos de guias no Teams. Neste tutorial, você criará uma guia pessoal *básica,* uma página de conteúdo em tela inteira para usuários individuais. (As guias pessoais são a coisa mais próxima de uma experiência de site tradicional no Teams.)

## <a name="before-you-begin"></a>Antes de começar

Você precisa de uma guia pessoal de execução básica para começar. Se você não tiver um, confira criar [e executar seu primeiro aplicativo teams.](../build-your-first-app/build-and-run.md)

## <a name="your-assignment"></a>Sua atribuição

As pessoas em sua organização têm problemas para encontrar informações básicas de contato para funções importantes (help desk, RH, etc.). Você é responsável por garantir que eles encontrem rapidamente essas informações em um só lugar. Como você faria isso? Uma guia pessoal do Teams, claro.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Identificar algumas das configurações do aplicativo e o scaffolding relevante para guias pessoais
> * Criar conteúdo de guia
> * Atualizar o tema de cores de uma guia com base na preferência do usuário

## <a name="1-identify-relevant-app-project-components"></a>1. Identifique componentes relevantes do projeto do aplicativo

Grande parte das configurações e da scaffolding do aplicativo é configurada automaticamente quando você cria seu projeto com o Kit de Ferramentas do Teams. Vamos dar uma olhada nos componentes principais para criar uma guia pessoal.

### <a name="app-configurations"></a>Configurações do aplicativo

No kit de ferramentas, vá para o **App Studio** para exibir e atualizar as configurações do aplicativo.

### <a name="app-scaffolding"></a>Scaffolding de aplicativos

O scaffolding do aplicativo fornece os componentes para renderizar sua guia pessoal no Teams. Há muito com o que você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:

* `Tab.js` no diretório `src/components` do projeto. Isso é para renderizar sua página de conteúdo de guia.
* Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.

## <a name="2-customize-your-tab-content-page"></a>2. Personalizar a página de conteúdo da guia

Compile uma lista de contatos importantes em sua organização. Copie e atualize o trecho a seguir com informações relevantes para você ou, por um tempo, use o código como estão.

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

Vá para o `src/components` diretório e `Tab.js` abra. Localize `render()` a função e colar o conteúdo dentro `return()` (conforme mostrado).

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

Adicione a regra a seguir para que os links de email sejam mais fáceis de `App.css` ler, independentemente do tema usado.

```CSS
a {
  color: inherit;
}
```

Salve suas alterações. Vá até a guia do seu aplicativo no Teams para exibir o novo conteúdo.

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-content.png" alt-text="Captura de tela de uma guia pessoal com conteúdo estático.":::

## <a name="3-update-the-tab-theme"></a>3. Atualizar o tema da guia

Os bons aplicativos são nativos para o Teams, portanto, é importante que sua guia se combina com o tema do Teams de sua preferência pelos usuários: padrão (claro), escuro ou alto contraste. Como você deve ter notado na última captura de tela, sua guia ainda tem um plano de fundo claro quando o cliente está usando o tema escuro. Essa não é uma experiência de usuário recomendada.

O [SDK do cliente JavaScript](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) do Teams pode fazer com que seu aplicativo saiba e reaja a alterações de tema no cliente. Vamos ver como fazer isso.

### <a name="get-context-about-the-teams-client"></a>Obter contexto sobre o cliente do Teams

No arquivo, há uma chamada que fornece alguns detalhes sobre o tema do `Tab.js` `microsoftTeams.getContext()` cliente [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) configurado, entre outros. Graças ao scaffolding do aplicativo, use esse código como está para acessar a `context` interface e suas propriedades.

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

### <a name="create-a-theme-change-handler"></a>Criar um manipulador de alteração de tema

Com as propriedades em mãos, seu aplicativo tem uma compreensão sólida do que está acontecendo em `context` torno dele no Teams. Mas o aplicativo ainda não sabe que sua aparência deve refletir qualquer tema que um usuário escolher.

Você precisa de um manipulador para que o estado do seu aplicativo mude com o tema. Insira o manipulador de alteração de tema a seguir imediatamente após a `microsoftTeams.getContext()` chamada.

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a>Corresponder estilos de tema

O manipulador de alterações de temas está em uso, mas você precisa de algum código que responda a essas alterações e alinhe as cores da guia com o tema atual.

> [!NOTE]
> O exemplo a seguir é apenas uma maneira de aplicar estilos à guia. Use o código como está, expanda-o ou escreva o seu próprio.

Na `render()` função, armazene o estado fornecido pelo manipulador de alteração de tema em `isTheme` .

```JavaScript
  const isTheme = this.state.theme
```

Depois de armazenar o estado fornecido pelo manipulador de alterações de tema, forneça alguma lógica condicional para renderizar os estilos da guia com base no tema atual. O exemplo a seguir mostra uma maneira básica de fazer isso:
1. Verifique o tema atual em `isTheme` .
2. Crie um `newTheme` objeto com propriedades CSS relevantes para o tema atual.
3. Aplicar o CSS ao elemento HTML raiz do conteúdo da guia ( `<div style={newTheme}>` ).

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

Verifique sua guia no Teams. A aparência deve corresponder muito ao tema escuro.

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-updated-theme.png" alt-text="Captura de tela de uma guia pessoal com exibição de conteúdo estático.":::

## <a name="well-done"></a>Bem feito

Parabéns! Você tem um aplicativo teams com uma guia pessoal que facilita a encontrar contatos importantes em sua organização.

## <a name="learn-more"></a>Saiba mais

* Siga nossas [diretrizes de design](../tabs/design/tabs.md) e crie com modelos de interface do usuário prontos para [produção](../concepts/design/design-teams-app-ui-templates.md) para criar uma experiência perfeita.
* Entenda [as considerações móveis](../tabs/design/tabs-mobile.md) para guias.
* [Adicione autenticação SSO à guia.](../tabs/how-to/authentication/auth-aad-sso.md)
* Utilize dados do Teams com [o Microsoft Graph.](https://docs.microsoft.com/graph/teams-concept-overview)
* [Crie uma guia sem o kit de ferramentas.](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-lesson"></a>Próxima lição

Você sabe como criar uma guia para uso pessoal. Vejamos o que é necessário para criar uma guia para canais e chats de equipe.

> [!div class="nextstepaction"]
> [Construir uma guia de canal](../build-your-first-app/build-channel-tab.md)
