---
title: Começar - Criar um canal e uma guia de grupo
author: girliemac
description: Crie rapidamente um canal do Microsoft Teams e uma guia de grupo usando o microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/22/2020
ms.topic: tutorial
ms.openlocfilehash: 868a471499bf2015196b7b741e340d070d0ed458
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068737"
---
# <a name="build-your-first-channel-and-group-tab-for-microsoft-teams"></a>Crie seu primeiro canal e guia de grupo para o Microsoft Teams

Este tutorial ensina a criar  uma guia de canal básico também conhecida como uma guia de grupo *,* que é uma página de tela inteira para um canal de equipe ou chat. Você também pode configurar alguns aspectos desse tipo de guia, por exemplo, renomear a guia para que ela seja significativa para seu canal, o que você não pode fazer em uma Guia Pessoal.

## <a name="what-youll-learn"></a>O que você aprenderá

* Crie um projeto de aplicativo usando o Microsoft Teams Toolkit para Visual Studio Code.
* Entenda as configurações do aplicativo e os scaffolding relevantes para as guias de canal.
* Criar conteúdo de tabulação e configuração de tabulação.
* Crie e execute seu aplicativo em equipes para teste.

## <a name="prerequisites"></a>Pré-requisitos

Certifique-se de entender como configurar e criar um aplicativo simples do Teams. Para obter mais informações, [consulte criar seu primeiro aplicativo do Microsoft Teams "Hello, World!".](../build-your-first-app/build-and-run.md)

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

O microsoft Teams Toolkit ajuda você a configurar seu aplicativo e configurar o scaffolding relevante para as guias de canal e grupo. Ele também contém uma página de configuração básica e uma página de conteúdo que exibe um "Hello, World!" Mensagem.

**Para criar seu projeto de aplicativo**

1. Vá para Visual Studio Código e selecione **Microsoft Teams** na Barra de Atividades :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: à esquerda.
1. Entre com sua conta de desenvolvimento do Microsoft 365 quando solicitado a fazer isso.
1. Na tela **Selecionar projeto,** selecione **JS** (JavaScript) em **Canal e aplicativo de grupo.**
1. Insira um nome para seu aplicativo do Teams. 

    > [!NOTE]
    > Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.

1. Selecione **Guia Grupo ou Canal do Teams**.
1. Selecione **Concluir** na parte inferior da tela para configurar seu projeto e salvar seu projeto em seu computador local.  

## <a name="2-understand-your-app-project-components"></a>2. Entenda os componentes do projeto do aplicativo

Grande parte das configurações e scaffolding do aplicativo são configuradas automaticamente quando você cria seu projeto com o kit de ferramentas. Vamos ver os principais componentes para a criação de uma guia de canal.

* **Configurações do aplicativo**: Abra **o App Studio** no kit de ferramentas para exibir e atualizar as configurações do aplicativo.
* **Estrutura de aplicativos**: o scaffolding do aplicativo fornece os componentes necessários para renderizar sua guia de canal no Teams. Há muito com o que você pode trabalhar, no entanto, por enquanto, vamos nos concentrar no seguinte:
  * Os arquivos localizados no `src/components` diretório do seu projeto:
    * `Tab.js` para renderizar a página de conteúdo da guia.
    * `TabConfig.js` para renderizar a página de configuração da guia.
  * SDK do cliente JavaScript do Microsoft Teams, que vem pré-carregado nos componentes front-end do seu projeto.

## <a name="3-customize-your-tab-content-page"></a>3. Personalizar sua página de conteúdo de tabulação

1. Copie e modifique o exemplo de código a seguir com informações relevantes para sua organização. Você também pode usar o trecho de código como ele é:
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
1. Vá para o `src/components` diretório e abra o `Tab.js` arquivo. Localize `render()` a função e colar seu código `return()` dentro, conforme mostrado no exemplo a seguir:
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
1. Vá para o diretório e atualize o arquivo com o seguinte código para tornar os links de email mais fáceis de ler em qualquer `src/components` `App.css` tema usado:
    ```CSS
    a {
      color: inherit;
    }
    ```

## <a name="4-customize-your-tab-configuration-page"></a>4. Personalizar sua página de configuração de tabulação

Cada guia em um canal ou chat tem uma página de configuração, um modal com pelo menos uma opção de configuração que é exibida quando os usuários adicionam seu aplicativo. A página de configuração por padrão pergunta aos usuários se eles querem notificar o canal ou o chat quando a guia estiver instalada. Você pode personalizar a página de configuração adicionando conteúdo personalizado.

Para adicionar conteúdo personalizado, abra o arquivo do diretório e atualize o conteúdo de espaço reservado dentro, conforme `TabConfig.js` mostrado no exemplo a `src/components` `return()` seguir:

  ```JavaScript
  return (
      <div>
        <h1>Add My Contoso Contacts</h1>
        <div>
          Select <b>Save</b> to add our organization's important contacts to this workspace.
        </div>
      </div>
  );
  ```
 
> [!TIP]
> Dê uma breve informação sobre seu aplicativo nesta página, pois essa seria a primeira vez que os usuários estão lendo sobre ele. Você também pode incluir opções de configuração personalizadas ou um [fluxo](../tabs/how-to/authentication/auth-aad-sso.md)de trabalho de autenticação , o que é comum nas páginas de configuração de tabulação.

## <a name="5-customize-your-tab-name"></a>5. Personalizar o nome da guia

Quando você adiciona uma guia de canal, o nome do aplicativo é exibido por padrão, por exemplo, **o primeiro aplicativo**. Você também pode fornecer um nome que faça mais sentido no contexto da colaboração em grupo, por exemplo, **Contatos de Equipe**:

1. Vá para o `src/components` diretório e abra o `TabConfig.js` arquivo.
1. Adicione a `suggestedDisplayName` propriedade com o nome da guia que você deseja exibir por padrão, conforme mostrado no exemplo a `microsoftTeams.settings.setSettings` seguir:

  ```JavaScript
    microsoftTeams.settings.setSettings({
    "contentUrl": "https://localhost:3000/tab",
    "suggestedDisplayName": "Team Contacts"
  });
  ```

## <a name="6-build-and-run-your-app"></a>6. Crie e execute seu aplicativo

Este tutorial ensina você a criar e executar seu aplicativo localmente. 

1. Vá para o diretório raiz do seu projeto de aplicativo no Terminal.
1. Executar `npm install` .
1. Executar `npm start` .

Essas informações também estão presentes na `README` seção do kit de ferramentas.
Seu aplicativo está sendo executado `https://localhost:3000` após **a compilação com êxito!** aparece no terminal. 

## <a name="7-sideload-your-app-in-teams"></a>7. Fazer sideload do aplicativo no Teams

Seu aplicativo está pronto para teste no Teams. Para fazer isso, você deve ter uma conta que permita o sideload de aplicativos. 

1. Abra um cliente Web do Teams Visual Studio Código com a **tecla F5.**
1. Adicione ( ) como confiável seguindo estas etapas `localhost` para habilitar o conteúdo do aplicativo a ser exibido no Teams:

   1. Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão) que foi aberta com a **tecla F5.**
   1. Abra `https://localhost:3000/tab` e prossiga para a página.

1. Selecione **Adicionar a uma equipe ou** Adicionar a um **chat** e localize um canal ou chat que você pode usar para testes no modal no Teams.
1. Selecione **Configurar uma guia**. A página de configuração é exibida em um modal.

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração de guia de canal.":::

1. Selecione **Salvar** para configurar a guia. A página de conteúdo a seguir é exibida:

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma guia de canal com exibição de conteúdo estático.":::

## <a name="see-also"></a>Confira também

* [Criar e executar seu primeiro aplicativo do Microsoft Teams](../build-your-first-app/build-and-run.md) 
* [SDK do cliente JavaScript do Teams](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [Projetando sua guia para a área de trabalho e a Web do Microsoft Teams](../tabs/design/tabs.md) 
* [Projetando seu aplicativo do Microsoft Teams com modelos de interface do usuário](../concepts/design/design-teams-app-ui-templates.md) 
* [Guias em dispositivos móveis](../tabs/design/tabs-mobile.md)
* [Suporte a SSO (login único) para guias](../tabs/how-to/authentication/auth-aad-sso.md)
* [Visão geral da API do Microsoft Teams](https://docs.microsoft.com/graph/teams-concept-overview)
* [Criar uma guia pessoal personalizada com Node.js e o Gerador Yeoman para o Microsoft Teams](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)

> [!div class="nextstepaction"]
> [Construir uma extensão de mensagens](../build-your-first-app/build-messaging-extension.md)