---
title: Começar - Criar um canal e uma guia de grupo
author: heath-hamilton
description: Crie rapidamente um canal e uma guia de grupo do Microsoft Teams usando o Kit de Ferramentas do Microsoft Teams.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: ae06217cf9ffd99ce94aff981fbbec19136d4aeb
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797873"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a>Criar uma guia de canal e grupo para o Microsoft Teams

Neste tutorial, você criará uma guia de canal básico *(também* conhecida como guia de *grupo),* que é uma página de tela inteira para um canal de equipe ou chat. Ao contrário de uma guia pessoal, os usuários podem configurar alguns aspectos desse tipo de guia (por exemplo, renomear a guia para que seja significativa para o canal).

## <a name="your-assignment"></a>Sua atribuição

Há pouco tempo, sua organização criou um aplicativo do Teams que usa uma guia para exibir informações de contato importantes (help desk, RH, etc.). No entanto, como é uma guia pessoal, cada usuário deve instalar a guia para vê-la e a adoção é menor do que o esperado. Em outras palavras, muitos funcionários ainda não sabem como alcançar o help desk.

Você pode tornar essas informações mais fáceis de encontrar criando uma guia de canal, o que removerá a carga de exigir que todos instalem um aplicativo. Em vez disso, um usuário pode adicionar a guia em um canal ou chat para beneficiar um grupo inteiro.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo usando o Kit de Ferramentas do Microsoft Teams para Visual Studio Code
> * Identificar algumas das configurações do aplicativo e a scaffolding relevante para as guias de canal
> * Criar conteúdo de guia
> * Criar conteúdo para a página de configuração de uma guia
> * Forneça um nome de guia sugerido
> * Criar e executar seu aplicativo localmente
> * Realizar sideload do seu aplicativo no Teams para teste

## <a name="before-you-begin"></a>Antes de começar

Se ainda não o fez, entenda e instale os pré-requisitos de desenvolvimento [do Teams.](build-first-app-overview.md#get-prerequisites)

## <a name="1-create-your-app-project"></a>1. Criar seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda a configurar seu aplicativo e configurar o scaffolding relevante para as guias de canal e grupo, incluindo uma página de configuração básica e uma página de conteúdo que exibe um "Hello, World!" message.

> [!TIP]
> Se você ainda não criou um projeto de aplicativo do [](../build-your-first-app/build-and-run.md) Teams antes, talvez seja útil seguir estas instruções que explicam os projetos com mais detalhes.

1. No Visual Studio Code, selecione **o Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos,** selecione **Tab** e **Next.**
1. Insira um nome para seu aplicativo do Teams. (Esse é o nome padrão do seu aplicativo e também o nome do diretório do projeto do aplicativo no computador local.) Selecione **a guia Canal do Grupo ou do Teams.**
1. Selecione **Concluir** na parte inferior da tela para configurar seu projeto.  

## <a name="2-identify-relevant-app-project-components"></a>2. Identifique componentes relevantes do projeto do aplicativo

Grande parte das configurações e da scaffolding do aplicativo é configurada automaticamente quando você cria seu projeto com o kit de ferramentas. Vejamos os componentes principais para a criação de uma guia de canal.

### <a name="app-configurations"></a>Configurações do aplicativo

No kit de ferramentas, vá para o **App Studio** para exibir e atualizar as configurações do aplicativo.

### <a name="app-scaffolding"></a>Scaffolding de aplicativos

O scaffolding do aplicativo fornece os componentes para renderizar sua guia de canal no Teams. Há muito com o que você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:

* Dois arquivos localizados no `src/components` diretório do seu projeto:
  * `Tab.js` para renderizar a página de conteúdo da guia.
  * `TabConfig.js` para renderizar a página de configuração da guia.
* SDK do cliente JavaScript do Microsoft Teams, que vem pré-carregado nos componentes front-end do seu projeto.

## <a name="3-customize-your-tab-content-page"></a>3. Personalizar a página de conteúdo da guia

Copie e atualize o trecho a seguir com informações relevantes à sua organização ou, por um tempo, use o código como estão.

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

Adicione a regra a seguir (também localizada em) para que os links de email sejam mais fáceis de `App.css` `src/components` ler, independentemente do tema usado.

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a>4. Personalizar a página de configuração da guia

Cada guia em um canal ou chat tem uma página de configuração, uma modal com pelo menos uma opção de configuração exibida quando os usuários adicionam seu aplicativo. Por padrão, a página de configuração pergunta aos usuários se eles querem notificar o canal ou o chat quando a guia é instalada.

Adicione algum conteúdo personalizado à sua página de configuração. Vá para o diretório do projeto, abra e atualize o conteúdo do espaço reservado `src/components` `TabConfig.js` dentro `return()` (conforme mostrado no exemplo a seguir).

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
> No mínimo, forneça algumas breves informações sobre seu aplicativo nesta página, pois essa pode ser a primeira vez que os usuários o aprenderão. Você também pode incluir opções de configuração personalizadas ou um fluxo [de](../tabs/how-to/authentication/auth-aad-sso.md)trabalho de autenticação, o que é comum nas páginas de configuração de guia.

## <a name="5-provide-a-suggested-tab-name"></a>5. Forneça um nome de guia sugerido

Quando você adiciona uma guia de canal, por padrão o nome do aplicativo é exibido (por exemplo, **primeiro aplicativo).**

Isso pode ser bom dependendo do que você chama seu aplicativo, mas talvez você queira fornecer um nome que faça mais sentido no contexto de colaboração em grupo (por exemplo, Contatos **de Equipe).**

1. Em, `TabConfig.js` vá para `microsoftTeams.settings.setSettings` .
2. Adicione a `suggestedDisplayName` propriedade com o nome da guia que você deseja exibir por padrão. 
3. Use o nome fornecido no exemplo a seguir ou digite seu nome. (Por padrão, os usuários podem alterar o nome.)

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://localhost:3000/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="6-build-and-run-your-app"></a>6. Crie e execute seu aplicativo

No interesse do tempo, você criará e executará seu aplicativo localmente.

(Essas informações também estão disponíveis no kit de `README` ferramentas.)

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e `npm install` execute.
1. Executar `npm start` .

Depois de concluído, há um **compilado com êxito!** no terminal. Seu aplicativo está em `https://localhost:3000` execução.

## <a name="7-sideload-your-app-in-teams"></a>7. Fazer sideload do aplicativo no Teams

Seu aplicativo está pronto para ser testado no Teams. Para fazer isso, você deve ter uma conta que permita o sideload do aplicativo. (Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma conta [de desenvolvimento do Teams.)](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account)

1. No Visual Studio Code, pressione a **tecla F5** para iniciar um cliente Web do Teams.
1. Para exibir o conteúdo do aplicativo no Teams, especifique que onde seu aplicativo está sendo executado ( `localhost` ) é confiável:
   1. Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão) que foi aberta após pressionar **F5**.
   1. Vá para `https://localhost:3000/tab` a página e prossiga para a página.
1. Volte para o Teams. Na modalidade, selecione **Adicionar a uma equipe** ou Adicionar a um **chat** e localize um canal ou chat que você possa usar para teste.
1. Selecione **Configurar uma guia.** A página de configuração é exibida em uma modalidade.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração de guia de canal.":::
1. Selecione **Salvar** para configurar a guia. A página de conteúdo é exibida.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma guia de canal com exibição de conteúdo estático.":::

## <a name="well-done"></a>Bem feito

Parabéns! Você tem um aplicativo teams com uma guia para exibir conteúdo útil em canais e chats.

## <a name="learn-more"></a>Saiba mais

* Autenticar usuários de guia com [SSO:](../tabs/how-to/authentication/auth-aad-sso.md)se você quiser apenas usuários autorizados exibindo sua guia, de configurar o SSO (single sign-on) por meio do Azure Active Directory (AD).
* [Inserir conteúdo de um](../tabs/how-to/add-tab.md#tab-requirements)aplicativo Web ou página da Web existente: mostramos como criar novo conteúdo para uma guia, mas você também pode carregar conteúdo de uma URL externa.
* [Crie uma experiência de guia perfeita:](../tabs/design/tabs.md)confira as diretrizes recomendadas para projetar guias do Teams.
* [Criar guias para dispositivos móveis:](../tabs/design/tabs-mobile.md)entenda como desenvolver guias para telefones e tablets.
* [Criar uma guia sem o kit de ferramentas](../tabs/quickstarts/create-channel-group-tab-node-yeoman.md)
* [Utilizar dados do Teams com o Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview)

## <a name="next-lesson"></a>Próxima lição

Você sabe como criar uma guia para colaboração. Deseja tentar criar um tipo diferente de aplicativo do Teams?

> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)
