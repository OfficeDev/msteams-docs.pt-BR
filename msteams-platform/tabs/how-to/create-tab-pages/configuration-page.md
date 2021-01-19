---
title: Criar uma página de configuração
author: laujan
description: criar uma página de configuração
keywords: canal de grupo de guias do teams configurável
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 2544454fd06348fa41269f3a8fd57cc71a07d140
ms.sourcegitcommit: 84f408aa2854aa7a5cefaa66ce9a373b19e0864a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2021
ms.locfileid: "49886734"
---
# <a name="create-a-configuration-page"></a>Criar uma página de configuração

Uma página de configuração é um tipo especial de [página de conteúdo.](content-page.md) Os usuários configuram alguns aspectos do aplicativo Microsoft Teams usando a página de configuração e usam essa configuração como parte do seguinte:

* Uma guia de chat de canal ou grupo - Coletar informações dos usuários e definir a `contentUrl` página de conteúdo a ser exibida.
* Uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md)
* Um [Conector do Office 365](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)

## <a name="configuring-a-channel-or-group-chat-tab"></a>Configurando uma guia de chat de canal ou grupo

O aplicativo deve fazer referência ao [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript do Microsoft Teams e `microsoft.initialize()` chamar. Além disso, as URLs usadas devem estar protegidas por pontos de extremidade HTTPS e disponíveis na nuvem. O código a seguir é um exemplo de uma página de configuração:

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

Escolha o **botão Selecionar** **Cinza** ou Selecionar Vermelho na página de configuração, para exibir o conteúdo da guia com um ícone cinza ou vermelho. Escolher o botão relativo dispara `saveGray()` ou `saveRed()` invoca o seguinte:

1. O `settings.setValidityState(true)` valor é definido como true.
1. O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é disparado.
1. O **botão** Salvar na página de configuração do aplicativo, carregado no Teams, está habilitado.

O código da página de configuração informa ao Teams que os requisitos de configuração foram atendidos e que a instalação pode prosseguir. Quando o usuário seleciona **Salvar,** os parâmetros são `settings.setSettings()` definidos, conforme definido pela `Settings` interface. Para obter mais informações, consulte [a interface Configurações.](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true) Na última etapa, é `saveEvent.notifySuccess()` chamado para indicar que a URL de conteúdo foi resolvida com êxito.

>[!NOTE]
>
>* Se você registrar um manipulador de salvar usando , o retorno de chamada deverá invocar ou `microsoftTeams.settings.registerOnSaveHandler()` indicar o resultado da `saveEvent.notifySuccess()` `saveEvent.notifyFailure()` configuração.
>* Se você não registrar um manipulador de salvar, a chamada será feita automaticamente `saveEvent.notifySuccess()` quando o usuário selecionar **Salvar**.

### <a name="get-context-data-for-your-tab-settings"></a>Obter dados de contexto para suas configurações de guia

Sua guia pode exigir informações contextuais para exibir conteúdo relevante. As informações contextuais aprimora ainda mais a atraente da guia, fornecendo uma experiência de usuário mais personalizada.

Para obter mais informações sobre as propriedades usadas para a configuração de guia, consulte [Interface de contexto.](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) Colete os valores das variáveis de dados de contexto das duas maneiras a seguir:

1. Inserir os espaço reservados da cadeia de caracteres de consulta url em seu `configurationURL` manifesto.

1. Use o [método SDK do](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` Teams.

#### <a name="insert-placeholders-in-the-configurationurl"></a>Inserir os espaço reservados no `configurationUrl`

Adicione os espaço reservados de interface de contexto à sua `configurationUrl` base. Por exemplo:

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

A `microsoftTeams.getContext((context) => {})` função recupera a interface de [contexto](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) quando invocada. Adicione essa função à página de configuração para recuperar valores de contexto:

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

 Autenticar antes de permitir que um usuário configure seu aplicativo. Caso contrário, seu conteúdo poderá incluir fontes que tenham seus protocolos de autenticação. Para saber mais, confira [Autenticar um usuário em uma guia do Microsoft Teams.](~/tabs/how-to/authentication/auth-flow-tab.md) Use informações de contexto para construir as URLs da página de autorização e solicitações de autenticação.
Verifique se todos os domínios usados em suas páginas de guia estão listados na `manifest.json` matriz e na `validDomains` matriz.

## <a name="modify-or-remove-a-tab"></a>Modificar ou remover uma guia

As opções de remoção com suporte refinam ainda mais a experiência do usuário. Definir a propriedade do manifesto como , que permite aos usuários `canUpdateConfiguration` `true` modificar, reconfigurar ou renomear um grupo ou guia de canal. Além disso, indique o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no aplicativo e definindo um valor para a propriedade `removeUrl` na  `setSettings()` configuração. Para obter mais informações, consulte [Clientes móveis.](#mobile-clients) O usuário pode desinstalar as guias Pessoais, mas não pode modificá-las. Para obter mais informações, [consulte Criar uma página de remoção para sua guia.](~/tabs/how-to/create-tab-pages/removal-page.md)

## <a name="mobile-clients"></a>Clientes móveis

Se você optar por que seu canal ou guia de grupo apareça nos clientes móveis do Teams, a configuração deverá ter `setSettings()` um valor para a `websiteUrl` propriedade. Para obter mais informações, [consulte as diretrizes para guias em dispositivos móveis.](~/tabs/design/tabs-mobile.md)

Configuração setSettings() do Microsoft Teams para página de remoção ou clientes móveis:

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "URL REQUIRED FOR MOBILE CLIENTS",
    removeUrl: "ADD REMOVAL PAGE URL HERE"
});
```
