---
title: Comece - Construa um canal e uma guia de grupo
author: girliemac
description: Crie rapidamente uma guia de canal e grupo Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/22/2020
ms.topic: tutorial
ms.openlocfilehash: ff9cfbfb7d099db52966f119add4ce8729929aa1
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566065"
---
# <a name="build-your-first-channel-and-group-tab-for-microsoft-teams"></a>Crie seu primeiro canal e guia de grupo para Microsoft Teams

Este tutorial ensina você a construir uma guia básica *de canal* também conhecida como guia *de grupo,* que é uma página em tela cheia para um canal de equipe ou bate-papo. Você também pode configurar alguns aspectos desse tipo de guia, por exemplo, renomear a guia para que seja significativa para o canal deles, o que você não pode fazer em uma Guia Pessoal.

## <a name="what-youll-learn"></a>O que você vai aprender

* Crie um projeto de aplicativo usando o Microsoft Teams Toolkit para Visual Studio Code.
* Entenda as configurações do aplicativo e andaimes relevantes para as guias do canal.
* Criar conteúdo de guia e configuração de guia.
* Construa e execute seu aplicativo em equipes para testes.

## <a name="prerequisites"></a>Pré-requisitos

Certifique-se de entender como configurar e construir um aplicativo de Teams simples. Para obter mais informações, consulte [criar seu primeiro Microsoft Teams aplicativo "Hello, World!".](../build-your-first-app/build-and-run.md)

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda você a configurar seu aplicativo e configurar os andaimes relevantes para as guias de canais e grupos. Ele também contém uma página de configuração básica e uma página de conteúdo que exibe um "Olá, Mundo!" Mensagem.

**Para criar seu projeto de aplicativo**

1. Vá para Visual Studio Code e selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na Barra de Atividades esquerda.
1. Faça login com sua conta de desenvolvimento Microsoft 365 quando solicitado a fazê-lo.
1. Na tela do **projeto Select,** selecione **JS** (JavaScript) no **aplicativo de canal e grupo**.
1. Digite um nome para o aplicativo Teams. 

    > [!NOTE]
    > Este é o nome padrão do seu aplicativo e também o nome do diretório de projetos do aplicativo em sua máquina local.

1. Selecione **a guia Grupo ou Teams de canais**.
1. Selecione **Concluir** na parte inferior da tela para configurar seu projeto e salvar seu projeto em sua máquina local.  

## <a name="2-understand-your-app-project-components"></a>2. Entenda os componentes do projeto do seu aplicativo

Muitas das configurações e andaimes do aplicativo são configuradas automaticamente quando você cria seu projeto com o kit de ferramentas. Vejamos os principais componentes para a construção de uma guia de canal.

* **Configurações do** aplicativo : Abra o **App Studio** no kit de ferramentas para visualizar e atualizar as configurações do aplicativo.
* **Andaimes de** aplicativos : O andaime do aplicativo fornece os componentes necessários para renderizar sua guia de canal em Teams. Há muita coisa com que você pode trabalhar, no entanto, por enquanto, vamos nos concentrar no seguinte:
  * Os arquivos localizados no `src/components` diretório do seu projeto:
    * `Tab.js` para renderizar a página de conteúdo da sua guia.
    * `TabConfig.js` para renderizar a página de configuração da sua guia.
  * Microsoft Teams Cliente JavaScript SDK, que vem pré-carregado nos componentes front-end do seu projeto.

## <a name="3-customize-your-tab-content-page"></a>3. Personalize sua página de conteúdo de guia

1. Copie e modifique a seguinte amostra de código com informações relevantes para sua organização. Você também pode usar o trecho como ele é:
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
    
1. Vá ao `src/components` diretório e abra o `Tab.js` arquivo. Localize a `render()` função e cole seu código no `return()` interior, conforme mostrado no exemplo a seguir:
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
    
1. Vá para o `src/components` diretório e atualize o `App.css` arquivo com o seguinte código para tornar os links de e-mail mais fáceis de ler em qualquer tema que seja usado:
    ```CSS
    a {
      color: inherit;
    }
    ```

## <a name="4-customize-your-tab-configuration-page"></a>4. Personalize sua página de configuração de guia

Cada guia em um canal ou chat tem uma página de configuração, um modal com pelo menos uma opção de configuração que é exibida quando os usuários adicionam seu aplicativo. A página de configuração por padrão pergunta aos usuários se eles querem notificar o canal ou o chat quando a guia estiver instalada. Você pode personalizar a página de configuração adicionando conteúdo personalizado.

Para adicionar conteúdo personalizado, abra `TabConfig.js` o arquivo do diretório e `src/components` atualize o conteúdo do espaço reservado `return()` dentro, conforme mostrado no exemplo a seguir:

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
> Dê uma breve informação sobre seu aplicativo nesta página, já que esta seria a primeira vez que os usuários estão lendo sobre ele. Você também pode incluir opções de configuração personalizadas ou um [fluxo de trabalho de autenticação,](../tabs/how-to/authentication/auth-aad-sso.md)o que é comum em páginas de configuração de guias.

## <a name="5-customize-your-tab-name"></a>5. Personalize seu nome de guia

Quando você adiciona uma guia de canal, o nome do aplicativo é exibido por padrão, por exemplo, **primeiro aplicativo**. Você também pode fornecer um nome que faça mais sentido no contexto da colaboração em grupo, por exemplo, **Contatos de Equipe**:

1. Vá ao `src/components` diretório e abra o `TabConfig.js` arquivo.
1. Adicione a `suggestedDisplayName` propriedade com o nome da guia que deseja exibir por `microsoftTeams.settings.setSettings` padrão, conforme mostrado no exemplo a seguir:

    ```JavaScript
        microsoftTeams.settings.setSettings({
        "contentUrl": "https://localhost:3000/tab",
        "suggestedDisplayName": "Team Contacts"
      });
      ```

## <a name="6-build-and-run-your-app"></a>6. Construa e execute seu aplicativo

Este tutorial ensina você a construir e executar seu aplicativo localmente. 

1. Vá para o diretório raiz do seu projeto de aplicativo no Terminal.
1. `npm install`Corra.
1. `npm start`Corra.

Essas informações também estão presentes na `README` seção do kit de ferramentas.
Seu aplicativo está sendo executado `https://localhost:3000` após o Compilado com **sucesso!** mensagem aparece no terminal. 

## <a name="7-sideload-your-app-in-teams"></a>7. Carregar lateralmente seu aplicativo em Teams

Seu aplicativo está pronto para testar em Teams. Para fazer isso, você deve ter uma conta que permita o sideload do aplicativo. 

1. Abra um cliente web Teams em Visual Studio Code com a chave **F5.**
1. Adicione ( `localhost` ) como confiável seguindo essas etapas para permitir que o conteúdo do aplicativo será exibido em Teams:

   1. Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão) que abriu com a tecla **F5.**
   1. Abra `https://localhost:3000/tab` e siga para a página.

1. Selecione **Adicionar a uma equipe** ou Adicionar a um **chat** e localizar um canal ou chat que você pode usar para testar a partir do modal em Teams.
1. Selecione **Configurar uma guia**. A página de configuração é exibida em um modal.

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração de guia de canal.":::

1. Selecione **Salvar** para configurar a guia. A seguinte página de conteúdo é exibida:

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma guia de canal com exibição de conteúdo estático.":::

## <a name="see-also"></a>Confira também

* [Construa e execute seu primeiro aplicativo de Microsoft Teams](../build-your-first-app/build-and-run.md) 
* [SDK do cliente JavaScript do Teams](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [Projetando sua guia para Microsoft Teams desktop e web](../tabs/design/tabs.md) 
* [Projetando seu aplicativo de Microsoft Teams com modelos de interface do usuário](../concepts/design/design-teams-app-ui-templates.md) 
* [Guias em dispositivos móveis](../tabs/design/tabs-mobile.md)
* [Suporte de login único (SSO) para guias](../tabs/how-to/authentication/auth-aad-sso.md)
* [Visão geral da API do Microsoft Teams](/graph/teams-concept-overview)
* [Crie uma guia pessoal personalizada com Node.js e o Gerador Yeoman para Microsoft Teams](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)

> [!div class="nextstepaction"]
> [Construir uma extensão de mensagens](../build-your-first-app/build-messaging-extension.md)
