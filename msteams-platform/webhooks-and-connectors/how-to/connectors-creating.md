---
title: Criar Conectores do Office 365
author: laujan
description: Descreve como começar a usar Office 365 conectores no Microsoft Teams
keywords: conector do Office365 para equipes
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 06/16/2021
ms.openlocfilehash: 880bede3a33d974c8424bdcaeb8e250bdc97edca
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63356095"
---
# <a name="create-office-365-connectors"></a>Criar Conectores do Office 365

Com Microsoft Teams aplicativos, você pode adicionar seu conector de Office 365 existente ou criar um novo dentro Teams. Para obter mais informações, consulte [build your own connector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector).

## <a name="add-a-connector-to-teams-app"></a>Adicionar um conector ao Teams app

Você pode criar um [pacote e](~/concepts/build-and-test/apps-package.md) [publicar seu](~/concepts/deploy-and-publish/apps-publish.md) conector como parte do envio do AppSource. Você pode distribuir seu conector registrado como parte do pacote Teams aplicativo. Para obter informações sobre pontos de entrada para Teams aplicativo, consulte [capabilities](~/concepts/extensibility-points.md). Você também pode fornecer o pacote aos usuários diretamente para carregar no Teams.

Para distribuir seu conector, registre-o no [Painel de Desenvolvedores conectores](https://aka.ms/connectorsdashboard).

Para que um conector funcione somente Microsoft Teams, siga as instruções para enviar o conector ao publicar seu aplicativo no artigo [Microsoft Teams store.](~/concepts/deploy-and-publish/appsource/publish.md) Caso contrário, um conector registrado funciona em todos os Office 365 que suportam aplicativos, incluindo Outlook e Teams.

> [!IMPORTANT]
> Seu conector é registrado depois que você seleciona **Salvar** no Painel do Desenvolvedor de Conectores. Se você quiser publicar seu conector no AppSource, siga as instruções em publicar seu aplicativo Microsoft Teams [no AppSource](~/concepts/deploy-and-publish/apps-publish.md). Se você não quiser publicar seu aplicativo no AppSource, distribua-o diretamente para a organização. Após [a publicação de conectores para sua](#publish-connectors-for-the-organization) organização, nenhuma ação é necessária no Painel do Conector.

### <a name="integrate-the-configuration-experience"></a>Integrar a experiência de configuração

Os usuários podem concluir toda a experiência de configuração do conector sem precisar sair do Teams cliente. Para obter a experiência, Teams pode incorporar sua página de configuração diretamente em um iframe. A sequência de operações é a seguinte:

1. O usuário seleciona o conector para iniciar o processo de configuração.
1. O usuário interage com a experiência da Web para concluir a configuração.
1. O usuário seleciona **Salvar**, que dispara um retorno de chamada no código.

    > [!NOTE]
    > * O código pode processar o evento save recuperando as configurações de webhook. Seu código armazena o webhook para postar eventos mais tarde.
    > * A experiência de configuração é carregada em linha Teams.

Você pode reutilizar sua experiência de configuração da Web existente ou criar uma versão separada para ser hospedada especificamente em Teams. Seu código deve incluir o Microsoft Teams JavaScript SDK. Isso fornece acesso de código a APIs para executar operações comuns, como obter o usuário, canal ou contexto de equipe atual e iniciar fluxos de autenticação.

**Para integrar a experiência de configuração**

1. Inicializar o SDK chamando `microsoftTeams.initialize()`.
1. Chamada `microsoftTeams.settings.setValidityState(true)` para habilitar **Salvar**.

    > [!NOTE]
    > Você deve chamar `microsoftTeams.settings.setValidityState(true)` como uma resposta à seleção do usuário ou à atualização de campo.

1. Registre  `microsoftTeams.settings.registerOnSaveHandler()` o manipulador de eventos, que é chamado quando o usuário seleciona **Salvar**.
1. Chame `microsoftTeams.settings.setSettings()` para salvar as configurações do conector. As configurações salvas também serão mostradas na caixa de diálogo de configuração se o usuário tentar atualizar uma configuração existente para o conector.
1. Chame `microsoftTeams.settings.getSettings()` para buscar propriedades de webhook, incluindo a URL.

    > [!NOTE]
    > Você deve chamar `microsoftTeams.settings.getSettings()` quando sua página for carregada pela primeira vez em caso de reconfiguração.

1. Registre `microsoftTeams.settings.registerOnRemoveHandler()` o manipulador de eventos, que é chamado quando o usuário remove o conector.

Esse evento oferece ao seu serviço a oportunidade de executar qualquer ação de limpeza.

O código a seguir fornece um HTML de exemplo para criar uma página de configuração do conector sem o serviço e o suporte ao cliente:

```html
<h2>Send notifications when tasks are:</h2>
<div class="col-md-8">
    <section id="configSection">
        <form id="configForm">
            <input type="radio" name="notificationType" value="Create" onclick="onClick()"> Created
            <br>
            <br>
            <input type="radio" name="notificationType" value="Update" onclick="onClick()"> Updated
        </form>
    </section>
</div>

<script src="https://statics.teams.microsoft.com/sdk/v1.5.2/js/MicrosoftTeams.min.js" crossorigin="anonymous"></script>
<script src="/Scripts/jquery-1.10.2.js"></script>

<script type="text/javascript">

        function onClick() {
            microsoftTeams.settings.setValidityState(true);
        }

        microsoftTeams.initialize();
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            var radios = document.getElementsByName('notificationType');

            var eventType = '';
            if (radios[0].checked) {
                eventType = radios[0].value;
            } else {
                eventType = radios[1].value;
            }

            microsoftTeams.settings.setSettings({
                 entityId: eventType,
                contentUrl: "https://YourSite/Connector/Setup",
                removeUrl:"https://YourSite/Connector/Setup",
                 configName: eventType
                });

            microsoftTeams.settings.getSettings(function (settings) {
                // We get the Webhook URL in settings.webhookUrl which needs to be saved. 
                // This can be used later to send notification.
            });

            saveEvent.notifySuccess();
        });

        microsoftTeams.settings.registerOnRemoveHandler(function (removeEvent) {
            alert("Removed" + JSON.stringify(removeEvent));
        });

</script>
```

Para autenticar o usuário como parte do carregamento de sua página, [](~/tabs/how-to/authentication/auth-flow-tab.md) consulte fluxo de autenticação para que as guias se integrem ao entrar quando sua página for incorporada.

> [!NOTE]
> Devido a motivos de compatibilidade entre clientes, seu código `microsoftTeams.authentication.registerAuthenticationHandlers()` deve chamar com a URL e métodos de retorno de chamada de sucesso ou falha antes de chamar `authenticate()`.

#### <a name="getsettings-response-properties"></a>`GetSettings` propriedades de resposta

>[!NOTE]
>Os parâmetros retornados pela `getSettings` chamada são diferentes quando você invoca esse método de uma guia e difere daqueles documentados nas [configurações js](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true).

A tabela a seguir fornece os parâmetros e os detalhes das propriedades de `GetSetting` resposta:

| Parâmetros   | Detalhes |
|-------------|---------|
| `entityId`       | A ID da entidade, conforme definido pelo código ao chamar `setSettings()`. |
| `configName`  | O nome da configuração, conforme definido pelo código ao chamar `setSettings()`. |
| `contentUrl` | A URL da página de configuração, conforme definido pelo código ao chamar `setSettings()`. |
| `webhookUrl` | A URL de webhook criada para o conector. Use a URL do webhook para POST JSON estruturado para enviar cartões para o canal. O `webhookUrl` é retornado somente quando o aplicativo retorna dados com êxito. |
| `appType` | Os valores retornados podem ser `mail`, ou `teams` `groups`correspondentes ao Office 365 Mail, Office 365 Grupos ou Microsoft Teams respectivamente. |
| `userObjectId` | A ID exclusiva correspondente ao Office 365 usuário que iniciou a configuração do conector. Ele deve ser protegido. Esse valor pode ser usado para associar o usuário Office 365, que definiu a configuração em seu serviço. |

#### <a name="handle-edits"></a>Manipular edições

Seu código deve manipular os usuários que retornam para editar uma configuração de conector existente. Para fazer isso, chame `microsoftTeams.settings.setSettings()` durante a configuração inicial com os seguintes parâmetros:

- `entityId` é a ID personalizada que representa o que o usuário configurou e entendeu pelo seu serviço.
- `configName` é um nome que o código de configuração pode recuperar.
- `contentUrl` é uma URL personalizada que é carregada quando um usuário edita uma configuração de conector existente.

Essa chamada é feita como parte do manipulador de eventos save. Em seguida, quando o `contentUrl` é carregado, seu código deve `getSettings()` chamar para preencher previamente quaisquer configurações ou formulários em sua interface de usuário de configuração.

#### <a name="handle-removals"></a>Manipular remoções

Você pode executar um manipulador de eventos quando o usuário remover uma configuração de conector existente. Você registra esse manipulador chamando `microsoftTeams.settings.registerOnRemoveHandler()`. Esse manipulador é usado para executar operações de limpeza, como a remoção de entradas de um banco de dados.

### <a name="include-the-connector-in-your-manifest"></a>Incluir o conector em seu Manifesto

Baixe o auto gerado `Teams app manifest` do portal. Execute as etapas a seguir, antes de testar ou publicar o aplicativo:

1. [Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).
1. Modifique `icons` a parte do manifesto para incluir os nomes de arquivo dos ícones em vez de URLs.

O seguinte arquivo manifest.json contém os elementos necessários para testar e enviar o aplicativo:

> [!NOTE]
> Substitua `id` e `connectorId` , no exemplo a seguir, pelo GUID do conector.

#### <a name="example-of-manifestjson-with-connector"></a>Exemplo de manifest.json com conector

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "id": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
  "version": "1.0",
  "packageName": "com.sampleapp",
  "developer": {
    "name": "Publisher",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.microsoft.com",
    "termsOfUseUrl": "https://www.microsoft.com"
  },
  "description": {
    "full": "This is a small sample app we made for you! This app has samples of all capabilities Microsoft Teams supports.",
    "short": "This is a small sample app we made for you!"
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App"
  },
  "accentColor": "#FFFFFF",
  "needsIdentity": "true"
}
```

## <a name="enable-or-disable-connectors-in-teams"></a>Habilitar ou desabilitar conectores Teams

O módulo Exchange Online PowerShell V2 usa autenticação moderna e funciona com autenticação multifatória, chamada MFA para se conectar Exchange todos os ambientes relacionados do PowerShell no Microsoft 365. Os administradores podem usar Exchange Online PowerShell para desabilitar conectores para um locatário inteiro ou uma caixa de correio de grupo específica, afetando todos os usuários nesse locatário ou caixa de correio. Não é possível desabilitar para alguns e não para outros. Além disso, os conectores são desabilitados por padrão para Nuvem da Comunidade Governamental, chamados GCC locatários.

A configuração de nível de locatário substitui a configuração de nível de grupo. Por exemplo, se um administrador habilitar conectores para o grupo e desabilitá-los no locatário, os conectores do grupo são desabilitados. Para habilitar um conector Teams, conecte-se [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) usando autenticação moderna com ou sem MFA.

### <a name="commands-to-enable-or-disable-connectors"></a>Comandos para habilitar ou desabilitar conectores

Execute os seguintes comandos no PowerShell do Exchange Online:

* Para desabilitar conectores para o locatário: `Set-OrganizationConfig -ConnectorsEnabled:$false`.
* Para desabilitar mensagens ativas para o locatário: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false`.
* Para habilitar conectores para Teams, execute os seguintes comandos:
  * `Set-OrganizationConfig -ConnectorsEnabled:$true `
  * `Set-OrganizationConfig -ConnectorsEnabledForTeams:$true`
  * `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$true`

Para obter mais informações sobre o intercâmbio de módulos do PowerShell, consulte [Set-OrganizationConfig](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true). Para habilitar ou desabilitar Outlook conectores, [conecte aplicativos aos seus grupos em Outlook](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab?ui=en-us&rs=en-us&ad=us).

## <a name="test-your-connector"></a>Testar seu conector

Para testar seu conector, carregue-o em uma equipe com qualquer outro aplicativo. Você pode criar um pacote .zip usando o arquivo de manifesto dos dois arquivos de ícone e conectores do Painel do Desenvolvedor, modificados conforme direcionado em Incluir o conector [em seu Manifesto](#include-the-connector-in-your-manifest).

Depois de carregar o aplicativo, abra a lista de conectores de qualquer canal. Role até a parte inferior para ver seu aplicativo na **seção Carregado** :

![Captura de tela de uma seção carregada na caixa de diálogo conector](~/assets/images/connectors/connector_dialog_uploaded.png)

> [!NOTE]
> O fluxo ocorre inteiramente dentro Microsoft Teams como uma experiência hospedada.

Para verificar se a `HttpPOST` ação está funcionando corretamente, [envie mensagens para o conector](~/webhooks-and-connectors/how-to/connectors-using.md).

## <a name="publish-connectors-for-the-organization"></a>Publicar conectores para a organização

Se você quiser que o conector seja disponibilizado apenas para os usuários em sua organização, você pode carregar seu aplicativo de conector personalizado no catálogo de aplicativos [da sua organização](~/concepts/deploy-and-publish/apps-publish.md).

Depois de carregar o pacote de aplicativos para configurar e usar o conector em uma equipe, instale o conector do catálogo de aplicativos da organização.

**Para configurar um conector**

1. Selecione **Aplicativos** na barra de navegação esquerda.
1. Na seção **Aplicativos** , selecione **Conectores**.
1. Selecione o conector que você deseja adicionar. Uma janela de diálogo pop-up é exibida.
1. No menu suspenso, selecione **Adicionar a uma equipe**.
1. Na caixa de pesquisa, digite um nome de equipe ou canal.
1. Selecione **Configurar um Conector no** menu suspenso no canto inferior direito da janela de diálogo.

> [!IMPORTANT]
> Atualmente, os conectores personalizados não estão disponíveis em Nuvem da Comunidade Governamental (GCC), GCC-Alto e Departamento de Defesa (DOD).

O conector está disponível na seção &#9679;&#9679;&#9679; > **Mais** **opçõesConnectorsAllConnectors** >  >  >  **para sua equipe** para essa equipe. Você pode navegar rolando até esta seção ou pesquisar o aplicativo do conector. Para configurar ou modificar o conector, selecione **Configurar**.

## <a name="distribute-webhook-and-connector"></a>Distribuir webhook e conector

1. [Configurar um Webhook de entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md?branch=pr-en-us-3076#create-an-incoming-webhook) diretamente para sua equipe.
1. Adicione uma [página de configuração](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#integrate-the-configuration-experience) e [publique seu Webhook de Entrada](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#publish-connectors-for-the-organization) em um conector Office 365 de entrada.
1. Empacote e publique seu conector como parte do envio [do AppSource](~/concepts/deploy-and-publish/office-store-guidance.md) .

## <a name="code-sample"></a>Exemplo de código

A tabela a seguir fornece o nome de exemplo e sua descrição:

|**Nome de exemplo** | **Descrição** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Conectores    | Exemplo Office 365 conector gerando notificações para Teams canal.|   [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| Exemplo de conectores genéricos |Código de exemplo para um conector genérico que é fácil de personalizar para qualquer sistema que oferece suporte a webhooks.|  | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|

## <a name="see-also"></a>Confira também

* [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Criar um webhook de Entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md)
