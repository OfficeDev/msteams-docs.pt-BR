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
# <a name="build-a-basic-personal-tab-for-microsoft-teams"></a>Criar uma guia pessoal básica para o Microsoft Teams

Este tutorial ensina você a criar uma guia pessoal básica no Microsoft Teams. As guias são uma maneira simples de surgir informações em seu aplicativo hospedando conteúdo da Web no Teams. Guias são um recurso comum de aplicativos pessoais que fornecem um espaço de trabalho privado para usuários individuais. As guias pessoais são a coisa mais próxima de uma experiência da Web tradicional no Teams. 

## <a name="what-youll-learn"></a>O que você aprenderá

* Entenda as configurações do aplicativo e os scaffolding relevantes para as guias pessoais.
* Crie um conteúdo de guia com uma lista de contatos da sua organização.
* Atualize o tema de cor de uma guia com base na preferência do usuário.

## <a name="prerequisites"></a>Pré-requisitos

Certifique-se de entender como configurar e criar um aplicativo simples do Teams. Para obter mais informações, [consulte criar seu primeiro aplicativo do Microsoft Teams "Hello, World!".](../build-your-first-app/build-and-run.md)

## <a name="1-understand-your-app-project-components"></a>1. Entenda os componentes do projeto do aplicativo

Depois de criar uma guia pessoal básica, o scaffold de aplicativo gerado fornece os componentes para renderizar sua guia pessoal no Teams. Há muito com o que você pode trabalhar, mas, por enquanto, vamos nos concentrar no seguinte: 

* `Tab.js` no diretório `src/components` do seu projeto. Isso é para renderizar sua página de conteúdo de tabulação.
* SDK do cliente JavaScript do Microsoft Teams, que é pré-carregado nos componentes front-end do seu projeto.

Como você pode observar na seção na parte superior do arquivo, o código de exemplo usa React , uma biblioteca JavaScript de código aberto para criar `import` `Tabs.js` a interface do usuário. [](https://reactjs.org/) 

> [!NOTE]
> Embora o uso do React _não seja_ necessário para o desenvolvimento do Teams, este tutorial ensina você com React.

## <a name="2-customize-your-tab-content-page"></a>2. Personalizar sua página de conteúdo de tabulação

Você pode personalizar sua página de conteúdo de tabulação para renderizar uma lista de contatos importantes em sua organização. 

**Para personalizar sua página de conteúdo de tabulação**

1. Copie e modifique o exemplo de código a seguir com informações relevantes para você. Você também pode usar o código como está: 
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
1. Chegou ao `src/components` diretório e abrir o `Tab.js` arquivo. 
1. Vá para `render()` e substitua o código do modelo pelo código modificado dentro, conforme mostrado no exemplo a `return()` seguir:
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
1. Vá para o diretório e modifique o arquivo com o seguinte código para tornar os links de email mais fáceis de ler com qualquer `src/components` `App.css` tema usado:
    ```CSS
    a {
      color: inherit;
    }
    ```
1. Salve suas alterações. 

   Você pode exibir o novo conteúdo na guia do aplicativo no Teams.

   :::image type="content" source="../assets/images/build-your-first-app/personal-tab-tutorial-content.png" alt-text="Captura de tela de uma guia pessoal com conteúdo estático.":::

## <a name="3-update-your-tab-theme"></a>3. Atualize o tema da guia

É importante que sua guia tenha um tema nativo do Teams. Você deve mesclar sua guia com o tema do Teams. Seus usuários geralmente preferem temas padrão (claro), escuro ou de alto contraste. Como você deve ter notado na última captura de tela, sua guia ainda tem um plano de fundo claro quando o usuário está usando o tema escuro. Essa não é uma experiência de usuário recomendada.

O SDK do cliente JavaScript do Teams pode tornar seu aplicativo ciente e reagir às alterações de tema no cliente. Para fazer isso, siga estas etapas:

1. **Obter contexto sobre o tema do cliente do Teams configurado** A `microsoftTeams.getContext()` chamada em seu arquivo fornece algum contexto sobre o tema do cliente configurado `Tab.js` (como tema escuro). O código a seguir acessa a `context` interface e suas propriedades:

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
1. **Criar um manipulador de alterações de tema** Com as propriedades em mãos, seu aplicativo tem uma compreensão sólida do que está acontecendo ao `context` seu redor no Teams. No entanto, o aplicativo ainda não tem uma aparência que reflita o tema quando um usuário o atualiza.

   Você precisa de um manipulador para atualizar o estado do aplicativo com o tema. Para criar um manipulador, insira o seguinte manipulador de alterações de tema imediatamente após a `microsoftTeams.getContext()` chamada:

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
1. **Corresponder aos estilos de tema** Seu manipulador de alterações de tema está no local, no entanto, você ainda precisa responder às alterações e alinhar as cores da guia com o tema atual.

   Na `render()` função, armazene o estado fornecido pelo manipulador de alterações de tema em `isTheme` :

    ```JavaScript
      const isTheme = this.state.context.theme
    ```
    
    > [!NOTE]
    > Este exemplo é apenas uma maneira de você aplicar estilos à sua guia. Use o código como está, expanda-o ou escreva seu próprio.

    Depois de armazenar o estado fornecido pelo manipulador de alterações de tema, forneça a lógica condicional para renderizar os estilos da guia com base no tema atual. O exemplo a seguir mostra uma maneira básica de fazer isso:

    1. Vá para `render()` e verifique o tema atual em `isTheme` .
    1. Crie um `newTheme` objeto com propriedades CSS relevantes para o tema atual.
    1. Aplique o seguinte CSS ao elemento HTML raiz do conteúdo de tabulação ( `<div style={newTheme}>` ):

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

       Verifique sua guia no Teams. A aparência agora corresponde de perto ao tema escuro.

       :::image type="content" source="../assets/images/build-your-first-app/personal-tab-tutorial-updated-theme.png" alt-text="Captura de tela de uma guia pessoal com exibição de conteúdo estático.":::

## <a name="see-also"></a>Confira também

* [SDK do cliente JavaScript do Teams](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [Projetando sua guia para a área de trabalho e a Web do Microsoft Teams](../tabs/design/tabs.md) 
* [Interface de contexto](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true)
* [Projetando seu aplicativo do Microsoft Teams com modelos de interface do usuário](../concepts/design/design-teams-app-ui-templates.md) 
* [Guias em dispositivos móveis](../tabs/design/tabs-mobile.md)
* [Suporte a SSO (login único) para guias](../tabs/how-to/authentication/auth-aad-sso.md)
* [Visão geral da API do Microsoft Teams](https://docs.microsoft.com/graph/teams-concept-overview)
* [Criar uma guia pessoal personalizada com Node.js e o Gerador Yeoman para o Microsoft Teams](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Construir uma guia de canal](../build-your-first-app/build-channel-tab.md)