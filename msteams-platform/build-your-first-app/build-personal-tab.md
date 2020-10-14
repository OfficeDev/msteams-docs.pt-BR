---
title: Introdução-criar uma guia pessoal
author: heath-hamilton
description: Crie rapidamente uma guia pessoal do Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 7c12c87fff5126662f9473ecb0c5838b61f5faf2
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452740"
---
# <a name="build-a-personal-tab-for-microsoft-teams"></a>Criar uma guia pessoal para o Microsoft Teams

As guias são uma maneira simples de fazer a superfície de conteúdo em seu aplicativo, incorporando essencialmente uma página da Web no Microsoft Teams.

Há dois tipos de guias no Microsoft Teams. Neste tutorial, você criará uma *guia pessoal*, uma página de conteúdo de tela inteira para usuários individuais. (As guias pessoais são as coisas mais próximas de uma experiência de site tradicional no Microsoft Teams.)

## <a name="before-you-begin"></a>Antes de começar

Você precisa de uma guia pessoal em execução básica para começar. Se você não tiver um, confira [Compilar e executar seu primeiro aplicativo do Microsoft Teams](../build-your-first-app/build-and-run.md).

## <a name="your-assignment"></a>Sua atribuição

As pessoas da sua organização têm problemas para localizar informações básicas de contato para funções importantes (Help Desk, HR, etc.). Você está encarregado de garantir que eles possam encontrar rapidamente essas informações em um só lugar. Como fazer isso? Uma guia pessoal do Teams, naturalmente.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Identificar algumas das propriedades de manifesto do aplicativo e scaffolding relevantes para guias pessoais
> * Criar conteúdo de guia
> * Atualizar o tema de cores de uma guia com base na preferência do usuário

## <a name="1-identify-relevant-app-project-components"></a>1. identificar componentes de projeto de aplicativo relevantes

Grande parte do manifesto do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit. Vamos examinar os principais componentes para criar uma guia pessoal.

### <a name="app-manifest"></a>Manifesto do aplicativo

O trecho de código a seguir do manifesto de aplicativo (o `manifest.json` arquivo no diretório do seu projeto `.publish` ) mostra [`staticTabs`](../resources/schema/manifest-schema.md#statictabs) , que inclui propriedades e valores padrão relevantes para guias pessoais.

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

* `entityId`: Um identificador exclusivo para a página exibida pela guia.
* `name`: O nome de exibição da guia (por exemplo, "meus contatos").
* `contentUrl`: A URL do host da página de conteúdo da guia (deve ser HTTPS).
* `scopes`: Especifica a guia é somente para uso pessoal.

### <a name="app-scaffolding"></a>Aplicativo scaffolding

O aplicativo scaffolding fornece os componentes para renderizar sua guia no Teams. Há muitas coisas com as quais você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:

* `Tab.js` arquivo no `src/components` diretório do projeto
* SDK do cliente JavaScript do Microsoft Teams, que vem pré-carregado nos componentes front-end do seu projeto

## <a name="2-customize-your-tab-content-page"></a>2. personalizar a página de conteúdo da guia

Compilar uma lista de contatos importantes em sua organização. Copie e atualize o trecho de código a seguir com informações relevantes para você ou, para fins de tempo, use o código como está.

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

Vá para o `src/components` diretório e abra `Tab.js` . Localize a `render()` função e cole o conteúdo dentro `return()` (conforme mostrado).

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

Adicione a regra a seguir para `App.css` que os links de email sejam mais fáceis de ler, independentemente de qual tema é usado.

```CSS
a {
  color: inherit;
}
```

Salve suas alterações. Vá para a guia do aplicativo no Microsoft Teams para exibir o novo conteúdo.

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-content.png" alt-text="Captura de tela de uma guia pessoal com conteúdo estático.":::

## <a name="3-update-the-tab-theme"></a>3. atualizar o tema da guia

Bons aplicativos se sentem nativos para o Microsoft Teams, portanto, é importante que as mesclagens de tabulação com o tema do teams que seus usuários preferem: padrão (claro), escuro ou alto contraste. Como você pode ter notado na última captura de tela, sua guia ainda tem um plano de fundo claro quando o cliente está usando o tema escuro. Essa não é uma experiência de usuário recomendada.

O [SDK de cliente do Microsoft Teams](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) pode tornar seu aplicativo ciente e reagir às alterações de tema no cliente. Vamos examinar como fazer isso.

### <a name="get-context-about-the-teams-client"></a>Obter contexto sobre o cliente Teams

No `Tab.js` arquivo, há uma `microsoftTeams.getContext()` chamada que fornece alguns [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) , entre outros detalhes, o tema de cliente configurado. Graças ao aplicativo scaffolding, use este código como é para acessar a `context` interface e suas propriedades.

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

### <a name="create-a-theme-change-handler"></a>Criar um manipulador de alteração de temas

Com as `context` Propriedades em mãos, seu aplicativo tem uma compreensão sólida do que está acontecendo em relação ao Microsoft Teams. Mas o aplicativo ainda não sabe que sua aparência deve refletir qualquer tema escolhido pelo usuário.

Você precisa de um manipulador para que o estado do aplicativo seja alterado com o tema. Insira o seguinte manipulador de alteração de tema imediatamente após a `microsoftTeams.getContext()` chamada.

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a>Coincidir estilos de tema

Seu manipulador de alteração de tema está no local, mas você precisa de algum código que responda às alterações e alinhe as cores da guia com o tema atual.

> [!NOTE]
> O exemplo a seguir é apenas uma maneira de aplicar estilos à sua guia. Use o código como está, expanda nele ou escreva seu próprio.

Armazenar o estado fornecido pelo manipulador de alteração de tema no `isTheme` .

```JavaScript
  const isTheme = this.state.theme
```

Forneça algumas lógicas condicionais para renderizar os estilos da guia com base no tema atual. O exemplo a seguir mostra uma maneira básica de fazer isso por 1) verificando o tema atual em `isTheme` , 2) criando um `newTheme` objeto com as propriedades de CSS relevantes para o tema atual e 3) aplicando o CSS ao elemento HTML raiz do conteúdo da guia ( `<div>` ).

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

Verifique sua guia no Microsoft Teams. A aparência deve corresponder ao tema escuro.

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-updated-theme.png" alt-text="Captura de tela de uma guia pessoal com conteúdo estático.":::

## <a name="well-done"></a>Muito bem

Parabéns! Você tem um aplicativo do teams com uma guia pessoal que facilita a localização de contatos importantes em sua organização.

## <a name="learn-more"></a>Saiba mais

* [Guia autenticar usuários com SSO](../tabs/how-to/authentication/auth-aad-sso.md): se você quiser apenas que usuários autorizados exibam sua guia, configure o logon único (SSO) por meio do Azure Active Directory (AD).
* [Inserir conteúdo de um aplicativo Web existente ou página da Web](../tabs/how-to/add-tab.md#tab-requirements): mostramos como criar novo conteúdo para uma guia pessoal, mas você também pode carregar o conteúdo de uma URL externa.
* [Criar uma experiência perfeita para sua guia](../tabs/design/tabs.md): consulte as diretrizes recomendadas para a criação de guias do teams.
* [Criar guias para celular](../tabs/design/tabs-mobile.md): entenda como desenvolver guias para telefones e tablets.
* [Integrar com a API do Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview)
* [Criar uma guia sem o kit de ferramentas](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a>Próxima lição

Você sabe como criar uma guia para uso pessoal. Vejamos o que é necessário para criar uma guia para os canais de equipe e chats.

> [!div class="nextstepaction"]
> [Construir uma guia de canal](../build-your-first-app/build-channel-tab.md)
