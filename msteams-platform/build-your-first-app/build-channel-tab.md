---
title: Começar - Criar um canal e uma guia de grupo
author: heath-hamilton
description: Crie rapidamente um canal do Microsoft Teams e uma guia de grupo usando o microsoft Teams Toolkit.
ms.author: lajanuar
localization_priority: Normal
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: aadab4b6826b026eadd5ed564b6e5de5c29b4b1d
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020874"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a>Criar um canal e uma guia de grupo para o Microsoft Teams

Neste tutorial, você criará uma guia de canal *básico* (também conhecida como guia de grupo *),* que é uma página de tela inteira para um canal de equipe ou chat. Ao contrário de uma guia pessoal, os usuários podem configurar alguns aspectos desse tipo de guia (por exemplo, renomear a guia para que ela seja significativa para seu canal).

## <a name="your-assignment"></a>Sua atribuição

Não há muito tempo, sua organização criou um aplicativo do Teams que usa uma guia para exibir informações de contato importantes (help desk, RH, etc.). No entanto, como é uma guia pessoal, cada usuário deve instalar a guia para vê-la e a adoção é menor do que o esperado. Em outras palavras, muitos funcionários ainda não sabem como chegar ao help desk.

Você pode tornar essas informações mais fáceis de encontrar criando uma guia de canal, o que removerá a carga de exigir que todos instalem um aplicativo. Em vez disso, um usuário pode adicionar a guia em um canal ou chat para benefício de um grupo inteiro.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo usando o Microsoft Teams Toolkit para Visual Studio Código
> * Identificar algumas das configurações do aplicativo e os scaffolding relevantes para as guias de canal
> * Criar conteúdo de guia
> * Criar conteúdo para a página de configuração de uma guia
> * Fornecer um nome de guia sugerido
> * Criar e executar seu aplicativo localmente
> * Fazer sideload do aplicativo no Teams para teste

## <a name="before-you-begin"></a>Antes de começar

Se você ainda não entendeu e instalou os [pré-requisitos de](build-first-app-overview.md#get-prerequisites)desenvolvimento do Teams.

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

O microsoft Teams Toolkit ajuda a configurar seu aplicativo e configurar estruturas relevantes para guias de canal e grupo, incluindo uma página de configuração básica e uma página de conteúdo que exibe um "Hello, World!" Mensagem.

> [!TIP]
> Se você não tiver criado um projeto de aplicativo do [](../build-your-first-app/build-and-run.md) Teams antes, talvez seja útil seguir estas instruções que explicam os projetos com mais detalhes.

1. Em Visual Studio Código, selecione **Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos,** selecione **Tab** e **Next**.
1. Insira um nome para seu aplicativo do Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.) Selecione **Guia Grupo ou Canal do Teams**.
1. Selecione **Concluir** na parte inferior da tela para configurar seu projeto.  

## <a name="2-identify-relevant-app-project-components"></a>2. Identificar componentes relevantes do projeto do aplicativo

Grande parte das configurações e scaffolding do aplicativo são configuradas automaticamente quando você cria seu projeto com o kit de ferramentas. Vamos ver os principais componentes para a criação de uma guia de canal.

### <a name="app-configurations"></a>Configurações de aplicativo

No kit de ferramentas, vá para **o App Studio** para exibir e atualizar as configurações do aplicativo.

### <a name="app-scaffolding"></a>Scaffolding de aplicativos

O scaffolding do aplicativo fornece os componentes para renderizar sua guia de canal no Teams. Há muito com o que você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:

* Dois arquivos localizados no `src/components` diretório do seu projeto:
  * `Tab.js` para renderizar a página de conteúdo da guia.
  * `TabConfig.js` para renderizar a página de configuração da guia.
* SDK do cliente JavaScript do Microsoft Teams, que vem pré-carregado nos componentes front-end do seu projeto.

## <a name="3-customize-your-tab-content-page"></a>3. Personalizar sua página de conteúdo de tabulação

Copie e atualize o trecho a seguir com informações relevantes para sua organização ou, por questão de tempo, use o código como está.

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

Vá para o `src/components` diretório e abra `Tab.js` . Localize `render()` a função e colar seu conteúdo dentro `return()` (conforme mostrado).

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

Adicione a seguinte regra a (também localizada em ) para que os links de email sejam mais fáceis de `App.css` `src/components` ler, independentemente do tema usado.

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a>4. Personalizar sua página de configuração de tabulação

Cada guia em um canal ou chat tem uma página de configuração, um modal com pelo menos uma opção de configuração que é exibida quando os usuários adicionam seu aplicativo. A página de configuração por padrão pergunta aos usuários se eles querem notificar o canal ou o chat quando a guia estiver instalada.

Adicione algum conteúdo personalizado à sua página de configuração. Vá para o diretório do seu projeto, abra e atualize o conteúdo de espaço reservado dentro `src/components` `TabConfig.js` `return()` (conforme mostrado no exemplo a seguir).

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
> No mínimo, forneça algumas informações breves sobre seu aplicativo nesta página, pois essa pode ser a primeira vez que os usuários estão aprendendo sobre ele. Você também pode incluir opções de configuração personalizadas ou [um](../tabs/how-to/authentication/auth-aad-sso.md)fluxo de trabalho de autenticação , o que é comum nas páginas de configuração de tabulação.

## <a name="5-provide-a-suggested-tab-name"></a>5. Forneça um nome de guia sugerido

Quando você adiciona uma guia de canal, por padrão, o nome do aplicativo é exibido (por exemplo, **primeiro aplicativo**).

Isso pode ser bom dependendo do que você chama seu aplicativo, mas talvez você queira fornecer um nome que faça mais sentido no contexto da colaboração em grupo (por exemplo, **Contatos de Equipe**).

1. Em `TabConfig.js` , vá para `microsoftTeams.settings.setSettings` .
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

(Essas informações também estão disponíveis no kit de ferramentas `README` .)

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Depois de concluído, há um **Compilado com êxito!** mensagem no terminal. Seu aplicativo está sendo executado em `https://localhost:3000` .

## <a name="7-sideload-your-app-in-teams"></a>7. Fazer sideload do aplicativo no Teams

Seu aplicativo está pronto para teste no Teams. Para fazer isso, você deve ter uma conta que permita o sideload de aplicativos. (Se você não tem certeza de que tem isso, saiba mais sobre como obter uma conta [de desenvolvimento do Teams](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)

1. Em Visual Studio Código, pressione a **tecla F5** para iniciar um cliente Web do Teams.
1. Para exibir o conteúdo do aplicativo no Teams, especifique que onde seu aplicativo está sendo executado ( `localhost` ) é confiável:
   1. Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão) que foi aberta após pressionar **F5**.
   1. Vá para `https://localhost:3000/tab` e prossiga para a página.
1. Volte para o Teams. No modal, selecione **Adicionar a uma equipe** ou Adicionar a um **chat** e localize um canal ou chat que você pode usar para teste.
1. Selecione **Configurar uma guia**. A página de configuração é exibida em um modal.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração de guia de canal.":::
1. Selecione **Salvar** para configurar a guia. A página de conteúdo é exibida.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma guia de canal com exibição de conteúdo estático.":::

## <a name="well-done"></a>Muito bem

Parabéns! Você tem um aplicativo do Teams com uma guia para exibir conteúdo útil em canais e chats.

## <a name="learn-more"></a>Saiba mais

* Siga nossas [diretrizes de design](../tabs/design/tabs.md) e crie com modelos [de interface](../concepts/design/design-teams-app-ui-templates.md) do usuário prontos para produção para criar uma experiência perfeita.
* Entenda [as considerações móveis](../tabs/design/tabs-mobile.md) para guias.
* [Adicione a autenticação SSO à sua guia](../tabs/how-to/authentication/auth-aad-sso.md).
* Utilize dados do Teams com [o Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).
* [Criar uma guia sem o kit de ferramentas](../tabs/quickstarts/create-channel-group-tab-node-yeoman.md)

## <a name="next-lesson"></a>Próxima lição

Você sabe como criar uma guia para colaboração. Quer tentar criar um tipo diferente de aplicativo do Teams?

> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)
