---
title: Criar Conectores do Office 365
author: laujan
description: Neste módulo, saiba como começar a usar o Office 365 Connectors e adicionar conector ao aplicativo Teams no Microsoft Teams
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 06/16/2021
ms.openlocfilehash: 53f5f6d9f360c465175b18d8b1b5eab9020d3ccf
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143554"
---
# <a name="create-office-365-connectors"></a>Criar Conectores do Office 365

Com os aplicativos do Microsoft Teams, você pode adicionar seu Conector do Office 365 existente ou criar um novo dentro do Teams. Para saber mais, confira [Criar seu próprio conector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector).

## <a name="add-a-connector-to-teams-app"></a>Adicionar um conector ao aplicativo Teams

Você pode criar um [pacote](~/concepts/build-and-test/apps-package.md) e [publicar](~/concepts/deploy-and-publish/apps-publish.md) seu conector como parte do envio do AppSource. Você pode distribuir seu conector registrado como parte do pacote de aplicativos do Teams. Para obter informações sobre pontos de entrada para o aplicativo Teams, consulte [capacidades](~/concepts/extensibility-points.md). Você também pode fornecer o pacote aos usuários diretamente para carregar no Teams.

Para distribuir o conector, registre-o no [Painel do Desenvolvedor de Conectores](https://aka.ms/connectorsdashboard).

Para que um conector funcione somente no Microsoft Teams, siga as instruções para enviar o conector no artigo [publicar seu aplicativo na loja do Microsoft Teams](~/concepts/deploy-and-publish/appsource/publish.md). Caso contrário, um conector registrado funciona em todos os produtos do Office 365 que dão suporte a aplicativos, incluindo o Outlook e o Teams.

> [!IMPORTANT]
> Seu conector é registrado depois que você seleciona **Salvar** no Painel do Desenvolvedor de Conectores. Se você quiser publicar seu conector no AppSource, siga as instruções em [publique seu aplicativo Microsoft Teams no AppSource](~/concepts/deploy-and-publish/apps-publish.md). Se você não quiser publicar seu aplicativo no AppSource, distribua-o diretamente para a organização. Após publicar os conectores para sua organização, nenhuma ação adicional será necessária no Painel do Conector.

### <a name="integrate-the-configuration-experience"></a>Integrar a experiência de configuração

Os usuários podem concluir toda a experiência de configuração do conector sem precisar sair do cliente do Teams. Para obter a experiência, o Teams pode inserir sua página de configuração diretamente em um iframe. A sequência de operações é a seguinte:

1. O usuário seleciona o conector para iniciar o processo de configuração.
1. O usuário interage com a experiência da Web para concluir a configuração.
1. O usuário seleciona **Salvar**, que dispara um retorno de chamada no código.

    > [!NOTE]
    >
    > * O código pode processar o evento de salvamento recuperando as configurações do webhook. Seu código armazena o webhook para postar eventos mais tarde.
    > * A experiência de configuração é carregada embutida no Teams.

Você pode reutilizar sua experiência de configuração da Web existente ou criar uma versão separada para ser hospedada especificamente no Teams. Seu código deve incluir o SDK javaScript do Microsoft Teams. Isso dá ao seu código acesso às APIs para executar operações comuns, como obter o usuário atual, canal ou contexto de equipe e iniciar fluxos de autenticação.

Para integrar a experiência de configuração:

1. Inicializar o SDK chamando `microsoftTeams.initialize()`.
1. Chame `microsoftTeams.settings.setValidityState(true)` para habilitar **Salvar**.

    > [!NOTE]
    > Você deve chamar `microsoftTeams.settings.setValidityState(true)` como uma resposta à seleção do usuário ou à atualização de campo.

1. Registre `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos, que é chamado quando o usuário seleciona **Salvar**.
1. Chame `microsoftTeams.settings.setSettings()` para salvar as configurações do conector. As configurações salvas também são mostradas na caixa de diálogo de configuração se o usuário tentar atualizar uma configuração existente para o conector.
1. Chame `microsoftTeams.settings.getSettings()` para buscar propriedades de webhook, incluindo a URL.

    > [!NOTE]
    > Você deve chamar `microsoftTeams.settings.getSettings()` quando a página for carregada pela primeira vez em caso de reconfiguração.

1. Registre `microsoftTeams.settings.registerOnRemoveHandler()` manipulador de eventos, que é chamado quando o usuário remove o conector.

Esse evento oferece ao seu serviço a oportunidade de executar qualquer ação de limpeza.

O código a seguir fornece um HTML de exemplo para criar uma página de configuração de conector sem o atendimento ao cliente e suporte:

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

Para autenticar o usuário como parte do carregamento de sua página, consulte [fluxo de autenticação para guias](~/tabs/how-to/authentication/auth-flow-tab.md) para integrar a entrada quando sua página for inserida.

> [!NOTE]
> Devido a motivos de compatibilidade entre clientes, seu código deve chamar `microsoftTeams.authentication.registerAuthenticationHandlers()` com a URL e os métodos de retorno de chamada de êxito ou falha antes de chamar `authenticate()`.

#### <a name="getsettings-response-properties"></a>`GetSettings` propriedades de resposta

>[!NOTE]
>Os parâmetros retornados pela chamada `getSettings` são diferentes quando você invoca esse método de uma guia e diferem daqueles documentados em [configurações js settings](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings).

A tabela a seguir fornece os parâmetros e os detalhes de `GetSetting` propriedades de resposta:

| Parâmetros   | Detalhes |
|-------------|---------|
| `entityId`       | A ID da entidade, conforme definido pelo código ao chamar `setSettings()`. |
| `configName`  | O nome da configuração, conforme definido pelo código ao chamar `setSettings()`. |
| `contentUrl` | A URL da página de configuração, conforme definido pelo código ao chamar `setSettings()`. |
| `webhookUrl` | A URL do webhook criada para o conector. Use a URL do webhook para POSTAR JSON estruturado para enviar cartões para o canal. O `webhookUrl` é retornado somente quando o aplicativo retorna dados com êxito. |
| `appType` | Os valores retornados podem ser `mail`, `groups` ou `teams` correspondentes ao Office 365 Mail, grupos do Office 365 ou Microsoft Teams, respectivamente. |
| `userObjectId` | A ID exclusiva correspondente ao usuário do Office 365 que iniciou a configuração do conector. Ele deve ser protegido. Esse valor pode ser usado para associar o usuário no Office 365, que configurou a configuração em seu serviço. |

#### <a name="handle-edits"></a>Manipular edições

Seu código deve lidar com usuários que retornam para editar uma configuração de conector existente. Para fazer isso, chame `microsoftTeams.settings.setSettings()` durante a configuração inicial com os seguintes parâmetros:

* `entityId` é a ID personalizada que representa o que o usuário configurou e entendeu pelo seu serviço.
* `configName` é um nome que o código de configuração pode recuperar.
* `contentUrl` é uma URL personalizada que é carregada quando um usuário edita uma configuração de conector existente.

Essa chamada é feita como parte do manipulador de eventos de salvamento. Em seguida, quando o `contentUrl` for carregado, seu código deverá chamar `getSettings()` para preencher previamente as configurações ou formulários na interface do usuário de configuração.

#### <a name="handle-removals"></a>Lidar com remoções

Você pode executar um manipulador de eventos quando o usuário remove uma configuração de conector existente. Registre esse manipulador chamando `microsoftTeams.settings.registerOnRemoveHandler()`. Esse manipulador é usado para executar operações de limpeza, como a remoção de entradas de um banco de dados.

### <a name="include-the-connector-in-your-manifest"></a>Incluir o conector em seu Manifesto

Baixe o `Teams app manifest` do portal. Execute as seguintes etapas antes de testar ou publicar o aplicativo:

1. [Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).
1. Modifique `icons` parte do manifesto para incluir os nomes de arquivo dos ícones em vez de URLs.

O seguinte arquivo manifest.json contém os elementos necessários para testar e enviar o aplicativo:

> [!NOTE]
> Substitua `id` e `connectorId` no exemplo a seguir com o GUID do conector.

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

## <a name="test-your-connector"></a>Testar seu conector

Para testar seu conector, carregue-o para uma equipe com qualquer outro aplicativo. Você pode criar um pacote .zip usando o arquivo de manifesto dos dois arquivos de ícone e conectores do Painel do Desenvolvedor, modificado conforme indicado em [Incluir o conector no seu manifesto](#include-the-connector-in-your-manifest).

Depois de carregar o aplicativo, abra a lista de conectores de qualquer canal. Role até a parte inferior para ver o aplicativo na seção **Carregado**:

![Captura de tela de uma seção carregada na caixa de diálogo do conector](~/assets/images/connectors/connector_dialog_uploaded.png)

> [!NOTE]
> O fluxo ocorre inteiramente no Microsoft Teams como uma experiência hospedada.

Para verificar se a ação `HttpPOST` está funcionando corretamente, [envie mensagens ao conector](~/webhooks-and-connectors/how-to/connectors-using.md).

Siga a [guia passo a passo](../../sbs-teams-connectors.yml) para criar e testar os conectores no Microsoft Teams.

## <a name="distribute-webhook-and-connector"></a>Distribuir webhook e conector

1. [Conjunto um Webhook de Entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md#create-an-incoming-webhook) diretamente para sua equipe.

1. Adicione uma [página de configuração](~/webhooks-and-connectors/how-to/connectors-creating.md?#integrate-the-configuration-experience) e publique seu Webhook de Entrada em um Conector do Office 365.

1. Empacote e publique seu conector como parte do sua entrega [AppSource](~/concepts/deploy-and-publish/office-store-guidance.md).

## <a name="code-sample"></a>Exemplo de código

A tabela a seguir fornece o nome do exemplo e sua descrição:

|**Nome de exemplo** | **Descrição** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Conectores | Exemplo de Conector do Office 365 gerando notificações para o canal do Teams.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| Exemplo de conectores genéricos |Código de exemplo para um conector genérico que é fácil de personalizar para qualquer sistema que dê suporte a webhooks.| | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o a [guia passo a passo](../../sbs-teams-connectors.yml) para criar e testar o conector no Teams.

## <a name="see-also"></a>Confira também

* [Criar e enviar mensagens](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Criar um webhook de Entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Como os administradores podem habilitar ou desabilitar conectores](/MicrosoftTeams/office-365-custom-connectors#enable-or-disable-connectors-in-teams)
* [Como os administradores podem publicar conectores personalizados na sua organização](/MicrosoftTeams/office-365-custom-connectors)
