---
title: Introdução-criar uma guia canal e grupo
author: heath-hamilton
description: Crie rapidamente uma guia de canal e grupo do Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: f890754cdf4ca43f39c25e3ba24fcf47b08c5a9f
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452852"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a>Criar uma guia de canal e grupo para o Microsoft Teams

Neste tutorial, você criará uma guia de *canal* básica (também conhecida como uma *Guia de grupo*), que é uma página de tela inteira de um canal de equipe ou bate-papo. Ao contrário de uma guia pessoal, os usuários podem configurar alguns aspectos desse tipo de guia (por exemplo, renomear a guia de forma que ela seja significativa para o canal).

## <a name="your-assignment"></a>Sua atribuição

Não há muito tempo, sua organização criou uma guia do teams com informações sobre como entrar em contato com funções importantes (Help Desk, HR, etc.). No entanto, como a guia era escopoda somente para uso pessoal, cada usuário deve instalar a guia para vê-la e a adoção é menor do que o esperado. Em outras palavras, muitos trabalhadores ainda não sabem como alcançar o suporte técnico.

Você pode facilitar a localização dessas informações criando uma guia de canal, o que removerá o ônus de exigir que todos instalem um aplicativo. Em vez disso, um usuário pode instalar a guia em um canal ou chat para o benefício de um grupo inteiro.

## <a name="what-youll-learn"></a>O que você aprenderá

> [!div class="checklist"]
>
> * Criar um projeto de aplicativo usando o Microsoft Teams Toolkit para o Visual Studio Code
> * Identificar algumas das propriedades de manifesto do aplicativo e scaffolding relevantes para as guias canal e grupo
> * Hospedar um aplicativo localmente
> * Criar conteúdo de guia
> * Criar conteúdo para a página de configuração de uma guia
> * Permitir que uma guia seja configurada e instalada
> * Fornecer um nome de guia sugerido

## <a name="1-create-your-app-project"></a>1. criar seu projeto de aplicativo

O Microsoft Teams Toolkit ajuda você a configurar o manifesto do aplicativo e o scaffolding relevantes para as guias canal e grupo, incluindo uma página de configuração básica e uma página de conteúdo que exibe um "Olá, mundo!" Mensagem.

> [!TIP]
> Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. Insira um nome para seu aplicativo do Microsoft Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)
1. Na tela **Adicionar recursos** , selecione **Tab** , **grupo ou guia canal de equipe**.
1. Selecione **concluir** na parte inferior da tela para configurar seu projeto.  

## <a name="2-identify-relevant-app-project-components"></a>2. identificar componentes de projeto de aplicativo relevantes

Grande parte do manifesto do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit. Vamos examinar os principais componentes para a criação de uma guia canal e grupo.

### <a name="app-manifest"></a>Manifesto do aplicativo

O trecho de código a seguir do manifesto de aplicativo mostra [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs) , que inclui as propriedades e os valores padrão relevantes para as guias canal e grupo.

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

## <a name="3-run-your-app"></a>3. Execute seu aplicativo

Nos juros de tempo, você criará e executará seu aplicativo localmente.

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Após a conclusão, há uma **compilação bem-sucedida!** mensagem no terminal.

## <a name="4-set-up-a-secure-tunnel-to-your-app"></a>4. configurar um túnel seguro para seu aplicativo

Para fins de teste, vamos hospedar sua guia em um servidor Web local (porta 3000).

1. Em um terminal, execute `ngrok http 3000` .
1. Copie a URL HTTPS que você forneceu.
1. Em seu `.publish` diretório, abra `Development.env` .
1. Substitua o `baseUrl0` valor pela URL copiada. (Por exemplo, alterar `baseUrl0=http://localhost:3000` para `baseUrl0=https://85528b2b3ca5.ngrok.io` .)

O manifesto do aplicativo está apontando para o local em que você está hospedando a guia.

## <a name="5-customize-your-tab-content-page"></a>5. personalizar a página de conteúdo da guia

Abra o manifesto do aplicativo ( `manifest.json` ) no `.publish` diretório e defina as seguintes propriedades no [`staticTabs`](../resources/schema/manifest-schema.md#statictabs) , que define a página de conteúdo da guia.

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

## <a name="6-create-your-tab-configuration-page"></a>6. criar sua página de configuração de guia

Cada guia em um canal ou chat tem uma página de configuração, uma janela restrita com pelo menos uma opção de instalação que é exibida quando os usuários instalam seu aplicativo. A página de configuração, por padrão, pergunta aos usuários se eles desejam notificar o canal ou chat quando a guia é instalada.

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
> No mínimo, forneça algumas breves informações sobre o aplicativo nesta página, pois essa pode ser a primeira vez que os usuários estão aprendendo. Você também pode incluir opções de configuração personalizada ou um [fluxo de trabalho de autenticação](../tabs/how-to/authentication/auth-aad-sso.md), que é comum nas páginas de configuração da guia.

## <a name="7-allow-the-tab-to-be-configured-and-installed"></a>7. permitir que a guia seja configurada e instalada

Para que os usuários configurem e instalem a guia com êxito, você deve adicionar a [URL de host segura que você configurou](#4-set-up-a-secure-tunnel-to-your-app) ao componente da página de configuração.

Vá para `TabConfig.js` e localize `microsoftTeams.settings.setSettings` . Para `"contentUrl"` , substitua a `localhost:3000` parte da URL pelo domínio em que você está hospedando o conteúdo da guia (conforme mostrado).

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab"
});
```

Além disso, certifique-se de que `microsoftTeams.settings.setValidityState(true);` . Ele é, por padrão, se definido como `false` , o botão **salvar** está desabilitado na página de configuração.

## <a name="8-provide-a-suggested-tab-name"></a>8. fornecer um nome de guia sugerido

Quando você instala uma guia para uso pessoal, o nome para exibição é a `name` Propriedade na `staticTabs` parte do manifesto do aplicativo (por exemplo, **meus contatos**). Quando você instala uma guia canal, por padrão, o nome do aplicativo é exibido (por exemplo, **First-app**).

Isso pode ser bem, dependendo do que você chama no seu aplicativo, mas talvez você queira fornecer um nome que faça mais sentido no contexto de colaboração de grupo (por exemplo, **contatos da equipe**).

No `TabConfig.js` , volte para `microsoftTeams.settings.setSettings` . Adicione a `suggestedDisplayName` propriedade com o nome da guia que você deseja exibir por padrão (conforme mostrado). Use o nome fornecido ou crie o seu próprio. Lembre-se, no manifesto, de que você está permitindo que os usuários alterem o nome se desejarem.

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="9-view-the-tab"></a>9. exibir a guia

Para ver as páginas de configuração e conteúdo da guia, você deve instalá-lo em um canal ou chat.

1. No cliente do Microsoft Teams, selecione **aplicativos**.
1. Selecione **carregar um aplicativo personalizado** e escolha o seu aplicativo `Development.zip` .
1. Escolha **Adicionar a uma equipe** ou **Adicionar a um chat** e localize um canal ou chat que você possa usar para teste.
1. Selecione **Configurar uma guia**. A página de configuração é exibida.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Captura de tela de uma página de configuração da guia canal.":::
1. Selecione **salvar** para configurar a guia. O conteúdo é exibido.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Captura de tela de uma página de configuração da guia canal.":::

## <a name="well-done"></a>Muito bem

Parabéns! Você tem um aplicativo do teams com uma guia para exibir conteúdo útil em canais e chats.

## <a name="learn-more"></a>Saiba mais

* [Guia autenticar usuários com SSO](../tabs/how-to/authentication/auth-aad-sso.md): se você quiser apenas que usuários autorizados exibam sua guia, configure o logon único (SSO) por meio do Azure Active Directory (AD).
* [Inserir conteúdo de um aplicativo Web existente ou página da Web](../tabs/how-to/add-tab.md#tab-requirements): mostramos como criar novo conteúdo para uma guia pessoal, mas você também pode carregar o conteúdo de uma URL externa.
* [Criar uma experiência perfeita para sua guia](../tabs/design/tabs.md): consulte as diretrizes recomendadas para a criação de guias do teams.
* [Criar guias para celular](../tabs/design/tabs-mobile.md): entenda como desenvolver guias para telefones e tablets.
* [Criar uma guia sem o kit de ferramentas](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a>Próxima lição

Você sabe como criar uma guia para colaboração. Deseja tentar criar um tipo diferente de aplicativo do teams?

> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)
