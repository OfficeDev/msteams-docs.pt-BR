---
title: Introdução-criar uma guia canal e grupo
author: heath-hamilton
description: Crie rapidamente uma guia de canal e grupo do Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: bb87d34974469057287cf63725e7722125c57c34
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605242"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a>Criar uma guia de canal e grupo para o Microsoft Teams

Neste tutorial, você criará uma guia de *canal* básica (também conhecida como uma *Guia de grupo*), que é uma página de tela inteira de um canal de equipe ou bate-papo. Ao contrário de uma guia pessoal, os usuários podem configurar alguns aspectos desse tipo de guia (por exemplo, renomear a guia de forma que ela seja significativa para o canal).

## <a name="your-assignment"></a>Sua atribuição

Não há muito tempo, sua organização criou um aplicativo Teams que usa uma guia para exibir informações importantes de contato (Help Desk, HR, etc.). No entanto, como é uma guia pessoal, cada usuário deve instalar a guia para vê-la e a adoção é menor do que o esperado. Em outras palavras, muitos trabalhadores ainda não sabem como alcançar o suporte técnico.

Você pode facilitar a localização dessas informações criando uma guia de canal, o que removerá o ônus de exigir que todos instalem um aplicativo. Em vez disso, um usuário pode adicionar a guia em um canal ou chat para o benefício de um grupo inteiro.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo usando o Microsoft Teams Toolkit para o Visual Studio Code
> * Identificar algumas das configurações do aplicativo e scaffolding relevantes para as guias canal e grupo
> * Criar conteúdo de guia
> * Criar conteúdo para a página de configuração de uma guia
> * Fornecer um nome de guia sugerido
> * Criar e executar seu aplicativo localmente
> * Sideload seu aplicativo no Teams para teste

## <a name="before-you-begin"></a>Antes de começar

Se você ainda não tiver feito isso, não se esqueça de [entender e instalar os pré-requisitos de desenvolvimento do teams](build-first-app-overview.md#get-prerequisites).

## <a name="1-create-your-app-project"></a>1. criar seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda a configurar seu aplicativo e configurar o scaffolding relevante para as guias canal e grupo, incluindo uma página de configuração básica e uma página de conteúdo que exibe um "Hello, World!" Mensagem.

> [!TIP]
> Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos** , selecione **Tab** e **Avançar**.
1. Insira um nome para seu aplicativo do Microsoft Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)
1. Verifique as opções de guia **pessoal** , **grupo ou canal Teams** . (Você saberá em breve por que precisa de ambos os tipos de guias.)
1. Selecione **concluir** na parte inferior da tela para configurar seu projeto.  

## <a name="2-identify-relevant-app-project-components"></a>2. identificar componentes de projeto de aplicativo relevantes

Grande parte das configurações do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit. Vamos examinar os principais componentes para a criação de uma guia canal e grupo.

### <a name="app-configurations"></a>Configurações do aplicativo

Você pode exibir e atualizar suas configurações de aplicativo usando o app Studio, que está incluído no kit de ferramentas.

Durante a instalação, o kit de ferramentas configurou inicialmente dois componentes essenciais de guias de canal e Grupo:

* **Página de configuração**: a janela restrita para adicionar uma guia a um canal ou chat. (No app Studio, você pode encontrar esta página acessando **guias > equipe**.)
* **Página de conteúdo**: onde você exibe o conteúdo principal. (No app Studio, você pode encontrar esta página acessando **guias > adicionar uma guia pessoal**.)

### <a name="app-scaffolding"></a>Aplicativo scaffolding

O aplicativo scaffolding fornece os componentes para renderizar sua guia pessoal no Microsoft Teams. Há muitas coisas com as quais você pode trabalhar, mas, por enquanto, você só precisa se concentrar no seguinte:

* Dois arquivos localizados no `src/components` diretório do projeto:
  * `Tab.js` para renderizar a página de conteúdo da guia.
  * `TabConfig.js` para renderizar a página de configuração da guia.
* SDK do cliente JavaScript do Microsoft Teams, que vem pré-carregado nos componentes de front-end do seu projeto.

## <a name="3-customize-your-tab-content-page"></a>3. personalizar a página de conteúdo da guia

Copie e atualize o trecho de código a seguir, com informações relevantes para a sua organização ou, para fins de tempo, use o código como está.

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

Adicione a seguinte regra a `App.css` (também localizada `src/components` ) para que os links de email sejam mais fáceis de ler, independentemente de qual tema é usado.

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a>4. personalizar a página de configuração da guia

Cada guia em um canal ou chat tem uma página de configuração, uma janela restrita com pelo menos uma opção de configuração exibida quando os usuários adicionam seu aplicativo. A página de configuração, por padrão, pergunta aos usuários se eles desejam notificar o canal ou chat quando a guia é instalada.

Adicione um conteúdo personalizado à sua página de configuração. Vá para o diretório do seu projeto `src/components` , abra `TabConfig.js` e atualize o conteúdo do espaço reservado dentro `return()` (conforme mostrado no exemplo a seguir).

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
> No mínimo, forneça algumas breves informações sobre o aplicativo nesta página, pois essa pode ser a primeira vez que os usuários estão aprendendo. Você também pode incluir opções de configuração personalizada ou um [fluxo de trabalho de autenticação](../tabs/how-to/authentication/auth-aad-sso.md), que é comum nas páginas de configuração da guia.

## <a name="5-provide-a-suggested-tab-name"></a>5. forneça um nome de guia sugerido

Quando você adiciona uma guia de canal ou grupo, por padrão, o nome do aplicativo é exibido (por exemplo, **First-app**).

Isso pode ser bem, dependendo do que você chama no seu aplicativo, mas talvez você queira fornecer um nome que faça mais sentido no contexto de colaboração de grupo (por exemplo, **contatos da equipe**).

No `TabConfig.js` , vá para `microsoftTeams.settings.setSettings` . Adicione a `suggestedDisplayName` propriedade com o nome da guia que você deseja exibir por padrão (conforme mostrado). Use o nome fornecido ou crie o seu próprio. (Por padrão, os usuários podem alterar o nome se desejarem).

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://localhost:3000/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="6-build-and-run-your-app"></a>6. Compilar e executar o aplicativo

Nos juros de tempo, você criará e executará seu aplicativo localmente.

(Essas informações também estão disponíveis no kit de ferramentas `README` .)

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Após a conclusão, há uma **compilação bem-sucedida!** mensagem no terminal. O aplicativo está sendo executado `https://localhost:3000` .

## <a name="7-sideload-your-app-in-teams"></a>7. Sideload seu aplicativo no Microsoft Teams

Seu aplicativo está pronto para teste no Teams. Para fazer isso, você deve ter uma conta que permita o aplicativo Sideload. (Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma [conta de desenvolvimento do teams](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)

1. No Visual Studio Code, pressione a tecla **F5** para iniciar um cliente Web do teams.
1. Para exibir o conteúdo do aplicativo no Teams, especifique o local em que o aplicativo está em execução ( `localhost` ) é confiável:
   1. Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão), aberta após pressionar **F5**.
   1. Vá até `https://localhost:3000/tab` a página e vá até ela.
1. Volte para o Microsoft Teams. Na janela restrita, selecione **Adicionar a uma equipe** ou **Adicionar a um chat** e localize um canal ou chat que você possa usar para teste.
1. Selecione **Configurar uma guia**. A página de configuração é exibida em uma janela restrita.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração da guia canal.":::
1. Selecione **salvar** para configurar a guia. A página de conteúdo é exibida.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma guia canal com visualização de conteúdo estático.":::

## <a name="well-done"></a>Muito bem

Parabéns! Você tem um aplicativo do teams com uma guia para exibir conteúdo útil em canais e chats.

## <a name="learn-more"></a>Saiba mais

* [Guia autenticar usuários com SSO](../tabs/how-to/authentication/auth-aad-sso.md): se você quiser apenas que usuários autorizados exibam sua guia, configure o logon único (SSO) por meio do Azure Active Directory (AD).
* [Inserir conteúdo de um aplicativo Web existente ou página da Web](../tabs/how-to/add-tab.md#tab-requirements): mostramos como criar novo conteúdo para uma guia pessoal, mas você também pode carregar o conteúdo de uma URL externa.
* [Criar uma experiência perfeita para sua guia](../tabs/design/tabs.md): consulte as diretrizes recomendadas para a criação de guias do teams.
* [Criar guias para celular](../tabs/design/tabs-mobile.md): entenda como desenvolver guias para telefones e tablets.
* [Usar os dados do teams com a API do Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview)
* [Criar uma guia sem o kit de ferramentas](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a>Próxima lição

Você sabe como criar uma guia para colaboração. Deseja tentar criar um tipo diferente de aplicativo do teams?

> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)
