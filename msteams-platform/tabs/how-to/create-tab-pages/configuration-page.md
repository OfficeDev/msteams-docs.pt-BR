---
title: Criar uma página de configuração
author: surbhigupta
description: como criar uma página de configuração
keywords: canal de grupo de guias do teams configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 041ef78fcc6e3f5203842e808949e86e8dd3aae4
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069214"
---
# <a name="create-a-configuration-page"></a>Criar uma página de configuração

Uma página de configuração é um tipo especial [de página de conteúdo.](content-page.md) Os usuários configuram alguns aspectos do aplicativo Microsoft Teams usando a página de configuração e usam essa configuração como parte do seguinte:

* Uma guia de chat de canal ou grupo: Coletar informações dos usuários e definir a `contentUrl` página de conteúdo a ser exibida.
* Uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md).
* Um [Office 365 Conector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="configuring-a-channel-or-group-chat-tab"></a>Configurando uma guia de chat de canal ou grupo

O aplicativo deve fazer referência Microsoft Teams [SDK do cliente JavaScript](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) e chamar `microsoft.initialize()` . Além disso, as URLs usadas devem ser pontos de extremidade HTTPS protegidos e disponíveis na nuvem. 

### <a name="example"></a>Exemplo

Um exemplo de página de configuração é mostrado na imagem a seguir: 

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

O código correspondente para a página de configuração é mostrado na seção a seguir:

```html
<head>
<script src='https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js'></script>
</head>
    <body>
        <button onclick="(document.getElementById('icon').src = '/images/iconGray.png'); colorClickGray()">Select Gray</button>
        <img id="icon" src="/images/teamsIcon.png" alt="icon" style="width:100px" />
        <button onclick="(document.getElementById('icon').src = '/images/iconRed.png'); colorClickRed()">Select Red</button>

        <script>
            microsoftTeams.initialize();
            let saveGray = () => {
                microsoftTeams.settings.registerOnSaveHandler((saveEvent) => {
                    microsoftTeams.settings.setSettings({
                        websiteUrl: "https://yourWebsite.com",
                        contentUrl: "https://yourWebsite.com/gray",
                        entityId: "grayIconTab",
                        suggestedDisplayName: "MyNewTab"
                    });
                    saveEvent.notifySuccess();
                });
            }
            let saveRed = () => {
                microsoftTeams.settings.registerOnSaveHandler((saveEvent) => {
                    microsoftTeams.settings.setSettings({
                        websiteUrl: "https://yourWebsite.com",
                        contentUrl: "https://yourWebsite.com/red",
                        entityId: "redIconTab",
                        suggestedDisplayName: "MyNewTab"
                    });
                    saveEvent.notifySuccess();
                });
            }

            let gr = document.getElementById("gray").style;
            let rd = document.getElementById("red").style;

            const colorClickGray = () => {
                gr.display = "block";
                rd.display = "none";
                microsoftTeams.settings.setValidityState(true);
                saveGray()
            }

            const colorClickRed = () => {
                rd.display = "block";
                gr.display = "none";
                microsoftTeams.settings.setValidityState(true);
                saveRed();
            }
        </script>
    </body>
...
```

Escolha Selecionar **Botão Cinza** ou **Selecione Vermelho** na página de configuração, para exibir o conteúdo da guia com um ícone cinza ou vermelho. 

A imagem a seguir exibe o conteúdo da guia com ícone cinza:

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

A imagem a seguir exibe o conteúdo da guia com o ícone vermelho:

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

Escolher o botão relativo dispara `saveGray()` ou , e invoca o `saveRed()` seguinte:

1. O `settings.setValidityState(true)` é definido como true.
1. O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é acionado.
1. O **botão Salvar** na página de configuração do aplicativo, carregado Teams, está habilitado.

O código da página de configuração informa ao Teams que os requisitos de configuração estão satisfeitos e que a instalação pode continuar. Quando o usuário seleciona **Salvar**, os parâmetros de `settings.setSettings()` são definidos, conforme definido pela `Settings` interface. Para obter mais informações, [consulte Configurações interface](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true). Na última etapa, é `saveEvent.notifySuccess()` chamado para indicar que a URL de conteúdo foi resolvida com êxito.

>[!NOTE]
>
>* Se você registrar um manipulador de salvar usando , o retorno de chamada deverá invocar ou `microsoftTeams.settings.registerOnSaveHandler()` indicar o resultado da `saveEvent.notifySuccess()` `saveEvent.notifyFailure()` configuração.
>* Se você não registrar um manipulador de salvar, a chamada será feita automaticamente quando o `saveEvent.notifySuccess()` usuário selecionar **Salvar**.

### <a name="get-context-data-for-your-tab-settings"></a>Obter dados de contexto para suas configurações de tabulação

Sua guia pode exigir informações contextuais para exibir conteúdo relevante. As informações contextuais aprimora ainda mais o apelo da guia, fornecendo uma experiência de usuário mais personalizada.

Para obter mais informações sobre as propriedades usadas para a configuração de tabulação, consulte [Context interface](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true). Colete os valores das variáveis de dados de contexto das duas seguintes maneiras:

1. Inserir os espaço reservados da cadeia de caracteres de consulta de URL no `configurationURL` seu manifesto.

1. Use o [Teams SDK.](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})`

#### <a name="insert-placeholders-in-the-configurationurl"></a>Inserir espaço reservados no `configurationUrl`

Adicione os espaço reservados de interface de contexto à sua base `configurationUrl` . Por exemplo:

##### <a name="base-url"></a>Base URL

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a>URL base com cadeias de caracteres de consulta

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

Depois que sua página é carregada, o Teams atualiza os espaço reservados da cadeia de caracteres de consulta com valores relevantes. Inclua lógica na página de configuração para recuperar e usar esses valores. Para obter mais informações sobre como trabalhar com cadeias de caracteres de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) em MDN Web Docs. O exemplo a seguir descreve a maneira de extrair um valor da `configurationUrl` propriedade:

```html
<script>
   microsoftTeams.initialize();
   const getId = () => {
        let urlParams = new URLSearchParams(document.location.search.substring(1));
        let blueTeamId = urlParams.get('team');
        return blueTeamId
    }
//For testing, you can invoke the following to view the pertinent value:
document.write(getId());
</script>
```

### <a name="use-the-getcontext-function-to-retrieve-context"></a>Usar a `getContext()` função para recuperar o contexto

A `microsoftTeams.getContext((context) => {})` função recupera a interface context [quando](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) invocada. Adicione essa função à página de configuração para recuperar valores de contexto:

```html
<!-- `userPrincipalName` will render in the span with the id "user". -->

<span id="user"></span>
...
<script>
    microsoftTeams.getContext((context) =>{
        let userId = document.getElementById('user');
        userId.innerHTML = context.userPrincipalName;
    });
</script>
...
```

## <a name="context-and-authentication"></a>Contexto e autenticação

 Autenticar antes de permitir que um usuário configure seu aplicativo. Caso contrário, seu conteúdo pode incluir fontes que tenham seus protocolos de autenticação. Para obter mais informações, [consulte Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use informações de contexto para construir as URLs da página de autorização e solicitações de autenticação.
Verifique se todos os domínios usados em suas páginas de tabulação estão listados `manifest.json` na matriz `validDomains` e.

## <a name="modify-or-remove-a-tab"></a>Modificar ou remover uma guia

As opções de remoção suportadas refinam ainda mais a experiência do usuário. De definir a propriedade do manifesto como , que permite aos usuários `canUpdateConfiguration` `true` modificar, reconfigurar ou renomear uma guia de grupo ou canal. Além disso, indique o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no aplicativo e definindo um valor para a propriedade `removeUrl` na  `setSettings()` configuração. O usuário pode desinstalar as guias Pessoais, mas não pode modificá-las. Para obter mais informações, [consulte Criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md).

Microsoft Teams configuração setSettings() para página de remoção:

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

## <a name="mobile-clients"></a>Clientes móveis

Se você optar por fazer com que seu canal ou guia de grupo apareça no Teams clientes móveis, a configuração deve ter `setSettings()` um valor para `websiteUrl` . Para obter mais informações, [consulte diretrizes para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md).
