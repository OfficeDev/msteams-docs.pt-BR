---
title: Criar Conectores do Office 365
author: laujan
description: Neste módulo, saiba como começar a usar os conectores Office 365 e adicionar conector ao aplicativo Teams no Microsoft Teams
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 06/16/2021
ms.openlocfilehash: bb4bd02553ebb49752fa6450cd0f94f41dcc7ac8
ms.sourcegitcommit: 217025a61ed9c3b76b507fe95563142abc6d0318
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2022
ms.locfileid: "67363478"
---
# <a name="create-office-365-connectors"></a>Criar Conectores do Office 365

Com os aplicativos do Microsoft Teams, você pode adicionar seu Conector do Office 365 existente ou criar um novo dentro do Teams. Para saber mais, confira [Criar seu próprio conector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector).

Confira o vídeo a seguir para saber como criar um Office 365 Conectores:
<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OIzv]
<br>

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="add-a-connector-to-teams-app"></a>Adicionar um conector ao aplicativo Teams

Você pode criar um [pacote](~/concepts/build-and-test/apps-package.md) e [publicar](~/concepts/deploy-and-publish/apps-publish.md) seu conector como parte do envio do AppSource. Você pode distribuir seu conector registrado como parte do pacote de aplicativos do Teams. Para obter informações sobre pontos de entrada para o aplicativo Teams, consulte [capacidades](~/concepts/extensibility-points.md). Você também pode fornecer o pacote aos usuários diretamente para carregar no Teams.

Para distribuir o conector, registre-o no [Painel do Desenvolvedor de Conectores](https://aka.ms/connectorsdashboard).

Para que um conector funcione somente no Teams, siga as instruções para enviar o conector ao [publicar seu aplicativo no artigo da loja do Microsoft Teams](~/concepts/deploy-and-publish/appsource/publish.md) . Caso contrário, um conector registrado funciona em todos os produtos do Office 365 que dão suporte a aplicativos, incluindo o Outlook e o Teams.

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

Você pode reutilizar sua experiência de configuração da Web existente ou criar uma versão separada para ser hospedada especificamente no Teams. Seu código deve incluir o SDK do JavaScript do Teams. Isso fornece acesso de código a APIs para executar operações comuns, como obter o usuário atual, canal ou contexto de equipe e iniciar fluxos de autenticação.

Para integrar a experiência de configuração:

> [!NOTE]
> A partir do SDK do cliente JavaScript do Teams (TeamsJS) v.2.0.0, as APIs no namespace de configurações foram preteridas em favor de APIs *equivalentes* *no namespace* de páginas, `pages.getConfig()` incluindo e outras APIs `pages.config` no sub-namespace. Para obter mais informações, [consulte Novidades no TeamsJS versão 2.0](../../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20)

1. Inicializar o SDK chamando `app.initialize()`.
1. Chame `pages.config.setValidityState(true)` para habilitar **Salvar**.

    > [!NOTE]
    > Você deve chamar `microsoftTeams.pages.config.setValidityState(true)` como uma resposta à seleção do usuário ou à atualização de campo.

1. Registre `microsoftTeams.pages.config.registerOnSaveHandler()` manipulador de eventos, que é chamado quando o usuário seleciona **Salvar**.
1. Chame `microsoftTeams.pages.config.setConfig()` para salvar as configurações do conector. As configurações salvas também são mostradas na caixa de diálogo de configuração se o usuário tentar atualizar uma configuração existente para o conector.
1. Chame `microsoftTeams.pages.getConfig()` para buscar propriedades de webhook, incluindo a URL.

    > [!NOTE]
    > Você deve chamar `microsoftTeams.pages.getConfig()` quando a página for carregada pela primeira vez em caso de reconfiguração.

1. Registre `microsoftTeams.pages.config.registerOnRemoveHandler()` manipulador de eventos, que é chamado quando o usuário remove o conector.

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

<script src="https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js" integrity="sha384-Q2Z9S56exI6Oz/ThvYaV0SUn8j4HwS8BveGPmuwLXe4CvCUEGlL80qSzHMnvGqee" crossorigin="anonymous"></script>
<script src="/Scripts/jquery-1.10.2.js"></script>

<script type="module">
        import {app, pages} from 'https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js';
        
        function onClick() {
            pages.config.setValidityState(true);
        }

        await app.initialize();
        pages.config.registerOnSaveHandler(function (saveEvent) {
            var radios = document.getElementsByName('notificationType');

            var eventType = '';
            if (radios[0].checked) {
                eventType = radios[0].value;
            } else {
                eventType = radios[1].value;
            }

            await pages.config.setConfig({
                entityId: eventType,
                contentUrl: "https://YourSite/Connector/Setup",
                removeUrl:"https://YourSite/Connector/Setup",
                configName: eventType
                });

            pages.getConfig().then(async (config) {
                // We get the Webhook URL from config.webhookUrl which needs to be saved. 
                // This can be used later to send notification.
            });

            saveEvent.notifySuccess();
        });

        pages.config.registerOnRemoveHandler(function (removeEvent) {
            alert("Removed" + JSON.stringify(removeEvent));
        });

</script>
```

Para autenticar o usuário como parte do carregamento de sua página, consulte [fluxo de autenticação para guias](~/tabs/how-to/authentication/auth-flow-tab.md) para integrar a entrada quando sua página for inserida.

> [!NOTE]
> Antes do TeamsJS v.2.0.0, `microsoftTeams.authentication.registerAuthenticationHandlers()` seu código deve chamar com a URL `authenticate()` e métodos de retorno de chamada de êxito ou falha antes de chamar devido a motivos de compatibilidade entre clientes. A partir do TeamsJS v.2.0.0, *registerAuthenticationHandlers* foi preterido em favor de chamar [authenticate()](/javascript/api/@microsoft/teams-js/authentication#@microsoft-teams-js-authentication-authenticate) diretamente com os parâmetros de autenticação necessários.

#### <a name="getconfig-response-properties"></a>`getConfig` propriedades de resposta

>[!NOTE]
>Os parâmetros retornados pela `getConfig` chamada são diferentes quando você invoca esse método de uma guia e difere daqueles documentados na [referência](/javascript/api/@microsoft/teams-js/pages#@microsoft-teams-js-pages-getconfig).

A tabela a seguir fornece os parâmetros e os detalhes de `getConfig` propriedades de resposta:

| Parâmetros   | Detalhes |
|-------------|---------|
| `entityId`       | A ID da entidade, conforme definido pelo código ao chamar `setConfig()`. |
| `configName`  | O nome da configuração, conforme definido pelo código ao chamar `setConfig()`. |
| `contentUrl` | A URL da página de configuração, conforme definido pelo código ao chamar `setConfig()`. |
| `webhookUrl` | A URL do webhook criada para o conector. Use a URL do webhook para POSTAR JSON estruturado para enviar cartões para o canal. O `webhookUrl` é retornado somente quando o aplicativo retorna dados com êxito. |
| `appType` | Os valores retornados podem ser `mail`, `groups`ou `teams` correspondentes ao Office 365 Mail, Office 365 Grupos ou Teams, respectivamente. |
| `userObjectId` | A ID exclusiva correspondente ao usuário do Office 365 que iniciou a configuração do conector. Ele deve ser protegido. Esse valor pode ser usado para associar o usuário no Office 365, que configurou a configuração em seu serviço. |

#### <a name="handle-edits"></a>Manipular edições

Seu código deve lidar com usuários que retornam para editar uma configuração de conector existente. Para fazer isso, chame `microsoftTeams.pages.config.setConfig()` durante a configuração inicial com os seguintes parâmetros:

* `entityId` é a ID personalizada que representa o que o usuário configurou e entendeu pelo seu serviço.
* `configName` é um nome que o código de configuração pode recuperar.
* `contentUrl` é uma URL personalizada que é carregada quando um usuário edita uma configuração de conector existente.

Essa chamada é feita como parte do manipulador de eventos de salvamento. Em seguida, quando o `contentUrl` for carregado, seu código deverá chamar `getConfig()` para preencher previamente as configurações ou formulários na interface do usuário de configuração.

#### <a name="handle-removals"></a>Lidar com remoções

Você pode executar um manipulador de eventos quando o usuário remove uma configuração de conector existente. Registre esse manipulador chamando `microsoftTeams.pages.config.registerOnRemoveHandler()`. Esse manipulador é usado para executar operações de limpeza, como a remoção de entradas de um banco de dados.

### <a name="include-the-connector-in-your-manifest"></a>Incluir o conector em seu Manifesto

Baixe o manifesto do aplicativo *Teams gerado automaticamente* no Portal do Desenvolvedor (<https://dev.teams.microsoft.com>). Execute as seguintes etapas antes de testar ou publicar o aplicativo:

1. [Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).
1. Modifique `icons` parte do manifesto para incluir os nomes de arquivo dos ícones em vez de URLs.

O seguinte *arquivo manifest.json* contém os elementos necessários para testar e enviar o aplicativo:

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
> O fluxo ocorre inteiramente no Teams como uma experiência hospedada.

Para verificar se a ação `HttpPOST` está funcionando corretamente, [envie mensagens ao conector](~/webhooks-and-connectors/how-to/connectors-using.md).

Siga o [guia passo a passo para](../../sbs-teams-connectors.yml) criar e testar os conectores em seu Teams.

## <a name="distribute-webhook-and-connector"></a>Distribuir webhook e conector

1. [Conjunto um Webhook de Entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md#create-an-incoming-webhook) diretamente para sua equipe.

1. Adicione uma [página de configuração](~/webhooks-and-connectors/how-to/connectors-creating.md?#integrate-the-configuration-experience) e publique seu Webhook de entrada em um Office 365 Connector.

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
* [Compilar um bot de notificação com JavaScript](../../sbs-gs-notificationbot.yml)
* [Crie seu primeiro aplicativo de bot usando JavaScript](../../sbs-gs-bot.yml)
