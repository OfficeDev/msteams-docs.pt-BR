---
title: Criar uma guia de canal para o Microsoft Teams
author: heath-hamilton
description: Saiba como criar uma guia de canal em seu primeiro aplicativo do Microsoft Teams.
ms.topic: tutorial
ms.openlocfilehash: f0c59328219b5611efc02c9eb04db6fdc517ca08
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651864"
---
# <a name="create-a-channel-tab-for-teams"></a>Criar uma guia de canal para o Microsoft Teams

Neste tutorial, você criará uma *guia canal*básico, uma página de conteúdo de tela inteira para um canal de equipe ou chat. Ao contrário de uma guia pessoal, os usuários podem configurar alguns aspectos de uma guia de canal (por exemplo, renomear a guia de forma que ela seja significativa para o canal).

## <a name="before-you-begin"></a>Antes de começar

Você precisa de um aplicativo básico em execução para começar. Se você não tiver um, siga as instruções em [Compilar e execute o primeiro aplicativo do Microsoft Teams](build-and-run-with-toolkit.md). Ao criar seu projeto de aplicativo, escolha somente a opção de **guia canal ou grupo Teams** .

## <a name="your-assignment"></a>Sua atribuição

Não há muito tempo, sua organização criou uma guia do teams com informações sobre como entrar em contato com funções importantes (Help Desk, HR, etc.). No entanto, como a guia era escopoda somente para uso pessoal, cada usuário deve instalar a guia para vê-la e a adoção é menor do que o esperado. Em outras palavras, muitos trabalhadores ainda não sabem como alcançar o suporte técnico.

Você pode facilitar a localização dessas informações criando uma guia de canal, o que removerá o ônus de exigir que todos instalem um aplicativo. Em vez disso, um usuário pode instalar a guia em um canal ou chat para o benefício de um grupo inteiro.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Identificar o manifesto do aplicativo e os componentes do scaffolding relevantes para as guias de canal
> * Criar conteúdo para sua guia
> * Criar conteúdo para a página de configuração de uma guia
> * Permitir que a guia seja configurada e instalada
> * Fornecer um nome de guia sugerido

## <a name="identify-relevant-app-manifest-and-scaffolding-components"></a>Identificar manifesto de aplicativo relevante e componentes do scaffolding

Grande parte do aplicativo de guia canal scaffolding e manifesto é configurada automaticamente quando você cria seu projeto com o Teams Toolkit. Vamos examinar os principais componentes para criar uma guia canal.

### <a name="app-manifest"></a>Manifesto do aplicativo

O trecho de código a seguir do manifesto de aplicativo mostra [`configurableTabs`](../../resources/schema/manifest-schema.md#configurabletabs) , que inclui as propriedades e os valores padrão relevantes para as guias de canal.

```JSON
    "configurableTabs": [
        {
            "configurationUrl": "{baseUrl0}/config",
            "canUpdateConfiguration": true,
            "scopes": [
                "team",
                "groupchat"
            ]
        }
    ],
```

* `configurationUrl`: A URL do host para a página de configuração da guia (deve ser HTTPS).
* `canUpdateConfiguration`: Se definido como `true` , os usuários podem alterar as configurações de tabulação, renomear a guia ou removê-la de um canal ou chat.
* `scopes`: Especifica se os usuários podem instalar o aplicativo em canais ( `team` ) e chats ( `groupchat` ). É necessário pelo menos um valor.

### <a name="app-scaffolding"></a>Aplicativo scaffolding

O aplicativo scaffolding fornece um `TabConfig.js` arquivo, localizado no `src/components` diretório do seu projeto, para renderizar a página de configuração da guia (mais sobre isso em breve).

## <a name="create-your-tab-content"></a>Criar seu conteúdo de guia

Abra o manifesto do aplicativo ( `manifest.json` ) e defina as propriedades a seguir no [`staticTabs`](../../resources/schema/manifest-schema.md#statictabs) , que define a página de conteúdo da guia.

```JSON
    "staticTabs": [
        {
            "entityId": "index",
            "name": "My Contacts",
            "contentUrl": "{baseUrl0}/tab",
            "scopes": [ "personal" ]
        }
    ],
```

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

Adicione a regra a seguir para `App.css` que os links de email sejam mais fáceis de ler, independentemente de qual tema é usado.

```CSS
  a {
    color: inherit;
  }
```

## <a name="create-your-tab-configuration-page"></a>Criar a página de configuração da guia

Cada guia de canal tem uma página de configuração, modal com pelo menos uma opção de configuração que é exibida ao instalar o aplicativo. A página de configuração, por padrão, pergunta aos usuários se eles desejam notificar o canal ou chat quando a guia é instalada.

Adicione algum conteúdo à sua página de configuração. Vá para o diretório do seu projeto `src/components` , abra `TabConfig.js` e insira algum conteúdo dentro `return()` (conforme mostrado).

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
> No mínimo, forneça algumas breves informações sobre o aplicativo nesta página, pois essa pode ser a primeira vez que os usuários estão aprendendo. Você também pode incluir opções de configuração personalizada ou um [fluxo de trabalho de autenticação](../../tabs/how-to/authentication/auth-aad-sso.md), que é comum nas páginas de configuração da guia.

## <a name="allow-the-tab-to-be-configured-and-installed"></a>Permitir que a guia seja configurada e instalada

Para que os usuários configurem e instalem com êxito a guia canal, você deve adicionar a URL de host que você configurou ao [criar e executar seu primeiro aplicativo](build-and-run-with-toolkit.md) no componente da página de configuração.

Vá para `TabConfig.js` e localize `microsoftTeams.settings.setSettings` . Para `"contentUrl"` , substitua a `localhost:3000` parte da URL pelo domínio em que você está hospedando o conteúdo da guia (conforme mostrado).

```JavaScript
    microsoftTeams.settings.setSettings({
      "contentUrl": "https://<MY_HOST_DOMAIN>/tab"
    });
```

Além disso, certifique-se de que `microsoftTeams.settings.setValidityState(true);` . Ele é, por padrão, se definido como `false` , o botão **salvar** está desabilitado na página de configuração.

## <a name="provide-a-suggested-tab-name"></a>Fornecer um nome de guia sugerido

Quando você instala uma guia para uso pessoal, o nome para exibição é a `name` Propriedade na `staticTabs` parte do manifesto do aplicativo (por exemplo, **meus contatos**). Quando você instala uma guia canal, por padrão, o nome do aplicativo é exibido (por exemplo, **First-app**).

Isso pode ser bem, dependendo do que você chama no seu aplicativo, mas talvez você queira fornecer um nome que faça mais sentido no contexto de colaboração de grupo (por exemplo, **contatos da equipe**).

No `TabConfig.js` , volte para `microsoftTeams.settings.setSettings` . Adicione a `suggestedDisplayName` propriedade com o nome da guia que você deseja exibir por padrão (conforme mostrado). Use o nome fornecido ou crie o seu próprio. Lembre-se, no manifesto, de que você está permitindo que os usuários alterem o nome se desejarem.

```JavaScript
    microsoftTeams.settings.setSettings({
      "contentUrl": "https://<MY_HOST_DOMAIN>/tab",
      "suggestedDisplayName": "Team Contacts"
    });
```

## <a name="view-the-channel-tab"></a>Exibir a guia canal

Para ver as páginas de configuração e conteúdo da guia canal, você deve instalá-lo em um canal ou chat.

1. No cliente do Microsoft Teams, selecione **aplicativos**.
1. Selecione **carregar um aplicativo personalizado** e escolha o seu aplicativo `Development.zip` .
1. Escolha **Adicionar a uma equipe** ou **Adicionar a um chat** e localize um canal ou chat que você possa usar para teste.
1. Selecione **Configurar uma guia**. A página de configuração é exibida.

:::image type="content" source="../doc-links/images/channel-tab-tutorial-content.png" alt-text="Captura de tela de exemplo de uma página de configuração da guia canal":::

Depois de selecionar **salvar** para configurar a guia, o conteúdo é exibido.

![Captura de tela de exemplo de uma guia de canal com conteúdo estático](../doc-links/images/channel-tab-tutorial-content-installed.png)

## <a name="well-done"></a>Muito bem

Parabéns! Você tem um aplicativo Teams com uma guia de canal para exibir conteúdo útil em canais e chats.

## <a name="learn-more"></a>Saiba mais

* [Guia autenticar usuários com SSO](../../tabs/how-to/authentication/auth-aad-sso.md): se você quiser apenas que usuários autorizados exibam sua guia, configure o logon único (SSO) por meio do Azure Active Directory (AD).
* [Inserir conteúdo de um aplicativo Web existente ou página da Web](../../tabs/how-to/add-tab.md#tab-requirements): mostramos como criar novo conteúdo para uma guia pessoal, mas você também pode carregar o conteúdo de uma URL externa.
* [Criar uma experiência perfeita para sua guia](../../tabs/design/tabs.md): consulte as diretrizes recomendadas para a criação de guias do teams.
* [Criar guias para dispositivos móveis](../../tabs/design/tabs-mobile.md): entenda como desenvolver guias para smartphones e tablets.
