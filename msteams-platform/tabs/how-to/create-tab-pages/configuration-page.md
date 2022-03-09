---
title: Criar uma página de configuração
author: surbhigupta
description: Saiba como criar uma página de configuração para configurar um canal ou chat de grupo para configurações, como, obter dados de contexto, inserir espaço reservados e autenticação usando exemplos de código.
keywords: canal de grupo de guias do teams configurável
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: ed4f60e3071b882f73662c0b666f87c484b4e77b
ms.sourcegitcommit: 830fdc80556a5fde642850dd6b4d1b7efda3609d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63398726"
---
# <a name="create-a-configuration-page"></a>Criar uma página de configuração

Uma página de configuração é um tipo especial [de página de conteúdo](content-page.md). Os usuários configuram alguns aspectos do aplicativo Microsoft Teams usando a página de configuração e usam essa configuração como parte do seguinte:

* Uma guia de chat de canal ou grupo: Coletar informações dos usuários e definir `contentUrl` a página de conteúdo a ser exibida.
* Uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md).
* Um [Office 365 Conector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="configure-a-channel-or-group-chat-tab"></a>Configurar um canal ou uma guia de chat de grupo

O aplicativo deve fazer referência Microsoft Teams [SDK do cliente JavaScript](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) e chamar `microsoft.initialize()`. As URLs usadas devem ser pontos de extremidade HTTPS protegidos e disponíveis na nuvem.

### <a name="example"></a>Exemplo

Um exemplo de página de configuração é mostrado na imagem a seguir:

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

O código a seguir é um exemplo de código correspondente para a página de configuração:

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
    ...
</body>
```

Escolha Selecionar **Botão Cinza** ou **Selecione Vermelho** na página de configuração, para exibir o conteúdo da guia com um ícone cinza ou vermelho.

A imagem a seguir exibe o conteúdo da guia com **o ícone Cinza** selecionado:

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

A imagem a seguir exibe o conteúdo da guia com **o ícone** Vermelho selecionado:

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

Escolher o botão apropriado dispara ou `saveGray()` `saveRed()`, e invoca o seguinte:

* Definir `settings.setValidityState(true)` como true.
* O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é acionado.
* **Salvar** na página de configuração do aplicativo está habilitado.

O código da página de configuração informa Teams que os requisitos de configuração estão satisfeitos e que a instalação pode continuar. Quando o usuário seleciona **Salvar**, os parâmetros de `settings.setSettings()` são definidos, conforme definido pela `Settings` interface. Para obter mais informações, consulte [interface de configurações](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true). `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.

>[!NOTE]
>
>* Você tem 30 segundos para concluir a operação de salvar (o retorno de chamada para registerOnSaveHandler) antes do tempo final. Após o tempo de tempo, uma mensagem de erro genérica é exibida.
>* Se você registrar um manipulador de salvar usando `microsoftTeams.settings.registerOnSaveHandler()`, o retorno de chamada deverá invocar `saveEvent.notifySuccess()` `saveEvent.notifyFailure()` ou indicar o resultado da configuração.
>* Se você não registrar um manipulador de salvar, `saveEvent.notifySuccess()` a chamada será feita automaticamente quando o usuário selecionar **Salvar**.

### <a name="get-context-data-for-your-tab-settings"></a>Obter dados de contexto para suas configurações de tabulação

Sua guia requer informações contextuais para exibir conteúdo relevante. As informações contextuais aprimora ainda mais o apelo da guia, fornecendo uma experiência de usuário mais personalizada.

Para obter mais informações sobre as propriedades usadas para configuração de tabulação, consulte [interface de contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true). Colete os valores das variáveis de dados de contexto das duas seguintes maneiras:

* Inserir os espaço reservados da cadeia de caracteres de consulta de URL no seu manifesto.`configurationURL`

* Use o [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)`microsoftTeams.getContext((context) =>{})`.

#### <a name="insert-placeholders-in-the-configurationurl"></a>Inserir espaço reservados no `configurationUrl`

Adicione os espaço reservados de interface de contexto à sua base `configurationUrl`. Por exemplo:

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

Depois que sua página é carregada, Teams atualiza os espaço reservados da cadeia de caracteres de consulta com valores relevantes. Inclua lógica na página de configuração para recuperar e usar esses valores. Para obter mais informações sobre como trabalhar com cadeias de caracteres de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) em MDN Web Docs. O exemplo de código a seguir fornece a maneira de extrair um valor da `configurationUrl` propriedade:

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

A `microsoftTeams.getContext((context) => {})` função recupera a [interface de contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) quando invocada.

O código a seguir fornece um exemplo de adição dessa função à página de configuração para recuperar valores de contexto:

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

Autenticar antes de permitir que um usuário configure seu aplicativo. Caso contrário, seu conteúdo pode incluir fontes que tenham seus protocolos de autenticação. Para obter mais informações, [consulte authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use informações de contexto para construir as URLs da página de autorização e solicitações de autenticação. Verifique se todos os domínios usados em suas páginas de tabulação estão listados na `manifest.json` matriz e `validDomains` .

## <a name="modify-or-remove-a-tab"></a>Modificar ou remover uma guia

De definir a propriedade do `canUpdateConfiguration` manifesto `true`como , que permite que os usuários modifiquem, reconfigurem ou renomeiem um canal ou uma guia de grupo. Além disso, indique o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no aplicativo e definindo um valor para a `removeUrl` propriedade na configuração  `setSettings()` . O usuário pode desinstalar guias pessoais, mas não pode modificá-las. Para obter mais informações, [consulte create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).

`setSettings()` Microsoft Teams para página de remoção:

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add a unique identifier here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

## <a name="mobile-clients"></a>Clientes móveis

Se você optar por ter seu canal ou guia de grupo exibido no Teams clientes móveis, `setSettings()` a configuração deve ter um valor para `websiteUrl`. Para obter mais informações, [consulte diretrizes para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md)

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Criar uma página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
