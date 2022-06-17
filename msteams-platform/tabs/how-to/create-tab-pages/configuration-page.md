---
title: Criar uma página de configuração
author: surbhigupta
description: Neste módulo, saiba como criar uma página de configuração para definir um canal ou chat em grupo para configurações, como obter dados de contexto e muito mais
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 2c439b38c061ad5f61538bb841f8ce7b9267ec0a
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143953"
---
# <a name="create-a-configuration-page"></a>Criar uma página de configuração

Uma página de configuração é um tipo especial de [página de conteúdo](content-page.md). Os usuários configuram alguns aspectos do aplicativo Microsoft Teams usando a página de configuração e usam essa configuração como parte do seguinte:

* Um canal ou guia de chat em grupo: colete informações dos usuários e defina o `contentUrl` da página de conteúdo a ser exibida.
* Uma [extensão de mensagem](~/messaging-extensions/what-are-messaging-extensions.md).
* Um [Conector do Office 365](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

[!INCLUDE [sdk-include](~/includes/sdk-include.md)].

## <a name="configure-a-channel-or-group-chat-tab"></a>Configurar um canal ou guia de chat em grupo

O aplicativo deve fazer referência ao [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) e chamar `app.initialize()`. Os URLs usados ​​devem ser pontos de extremidade HTTPS seguros e disponíveis na nuvem.

### <a name="example"></a>Exemplo

Um exemplo de uma página de configuração é mostrado na imagem a seguir:

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

O código a seguir é um exemplo de código correspondente para a página de configuração:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<head>
    <script src='https://statics.teams.cdn.office.net/sdk/v2.0.0/js/MicrosoftTeams.min.js'></script>
</head>
<body>
    <button onclick="(document.getElementById('icon').src = '/images/iconGray.png'); colorClickGray()">Select Gray</button>
    <img id="icon" src="/images/teamsIcon.png" alt="icon" style="width:100px" />
    <button onclick="(document.getElementById('icon').src = '/images/iconRed.png'); colorClickRed()">Select Red</button>

    <script>
        app.initialize();
        let saveGray = () => {
            pages.config.registerOnSaveHandler((saveEvent) => {
                const configPromise = pages.config.setConfig({
                    websiteUrl: "https://yourWebsite.com",
                    contentUrl: "https://yourWebsite.com/gray",
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                configPromise.
                    then((result) => {saveEvent.notifySuccess()}).
                    catch((error) => {saveEvent.notifyFailure("failure message")});
            });
        }

        let saveRed = () => {
            pages.config.registerOnSaveHandler((saveEvent) => {
                const configPromise = pages.config.setConfig({
                    websiteUrl: "https://yourWebsite.com",
                    contentUrl: "https://yourWebsite.com/red",
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                configPromise.
                    then((result) => {saveEvent.notifySuccess();}).
                    catch((error) => {saveEvent.notifyFailure("failure message")});
            });
        }

        let gr = document.getElementById("gray").style;
        let rd = document.getElementById("red").style;

        const colorClickGray = () => {
            gr.display = "block";
            rd.display = "none";
            pages.config.setValidityState(true);
            saveGray()
        }

        const colorClickRed = () => {
            rd.display = "block";
            gr.display = "none";
            pages.config.setValidityState(true);
            saveRed();
        }
    </script>
    ...
</body>
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

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

***
Escolha o botão **Selecionar cinza** ou **Selecionar vermelho** na página de configuração para exibir o conteúdo da guia com um ícone cinza ou vermelho.

A imagem a seguir exibe o conteúdo da guia com o ícone **Cinza** selecionado:

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

A imagem a seguir exibe o conteúdo da guia com o ícone **Vermelho** selecionado:

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

Escolher o botão apropriado aciona `saveGray()` ou `saveRed()` e invoca o seguinte:

* Defina `pages.config.setValidityState(true)` como verdadeiro.
* O manipulador de eventos `pages.config.registerOnSaveHandler()` é acionado.
* **Salvar** na página de configuração do aplicativo, está habilitado.

O código da página de configuração informa ao Teams que os requisitos de configuração foram atendidos e a instalação pode prosseguir. Quando o usuário seleciona **Salvar**, os parâmetros de `pages.config.setConfig()` são definidos, conforme definido pela interface `Config`. Para obter mais informações, consulte [a interface de configuração](/javascript/api/@microsoft/teams-js/pages.config?). `saveEvent.notifySuccess()` é chamado para indicar que a URL do conteúdo foi resolvida com sucesso.

>[!NOTE]
>
>* Você tem 30 segundos para concluir a operação de salvamento (o retorno de chamada para registerOnSaveHandler) antes do tempo limite. Após o tempo limite, uma mensagem de erro genérica é exibida.
>* Se você registrar um manipulador de salvamento usando `registerOnSaveHandler()`, o retorno de chamada deverá invocar `saveEvent.notifySuccess()` ou `saveEvent.notifyFailure()` para indicar o resultado da configuração.
>* Se você não registrar um manipulador de salvamento, a chamada `saveEvent.notifySuccess()` será feita automaticamente quando o usuário selecionar **Salvar**.

### <a name="get-context-data-for-your-tab-settings"></a>Obter dados de contexto para suas configurações de guia

Sua guia requer informações contextuais para exibir conteúdo relevante. As informações contextuais aprimoram ainda mais o apelo de sua guia, fornecendo uma experiência de usuário mais personalizada.

Para obter mais informações sobre as propriedades usadas para configuração de guias, consulte [interface de contexto](/javascript/api/@microsoft/teams-js/app.context?view=msteams-client-js-latest&preserve-view=true). Colete os valores das variáveis ​​de dados de contexto das duas maneiras a seguir:

* Insira marcadores de cadeia de caracteres de consulta de URL no `configurationURL` do seu manifesto.

* Use o método [SDK do Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `app.getContext()`.

#### <a name="insert-placeholders-in-the-configurationurl"></a>Inserir espaços reservados no `configurationUrl`

Adicione marcadores de interface de contexto à sua base `configurationUrl`. Por exemplo:

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

Depois que a página é carregada, o Teams atualiza os espaços reservados da cadeia de caracteres de consulta com valores relevantes. Inclua lógica na página de configuração para recuperar e usar esses valores. Para obter mais informações sobre como trabalhar com cadeias de caracteres de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) em MDN Web Docs. O exemplo de código a seguir fornece a maneira de extrair um valor da propriedade `configurationUrl`:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<script>
   app.initialize();
   const getId = () => {
        let urlParams = new URLSearchParams(document.location.search.substring(1));
        let blueTeamId = urlParams.get('team');
        return blueTeamId
    }
//For testing, you can invoke the following to view the pertinent value:
document.write(getId());
</script>
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

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

***

### <a name="use-the-getcontext-function-to-retrieve-context"></a>Use a função `getContext()` para recuperar o contexto

A `app.getContext()` função retorna uma promessa que é resolvida com o objeto [de interface de](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest&preserve-view=true) contexto.

O código a seguir fornece um exemplo de adição dessa função à página de configuração para recuperar valores de contexto:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<!-- `userPrincipalName` will render in the span with the id "user". -->

<span id="user"></span>
...
<script>
    const contextPromise = app.getContext();
    contextPromise.
        then((context) => {
            let userId = document.getElementById('user');
            userId.innerHTML = context.user.userPrincipalName;
        }).
        catch((error) => {/*Unsuccessful operation*/});
</script>
...
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

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

***

## <a name="context-and-authentication"></a>Contexto e autenticação

Autentique antes de permitir que um usuário configure seu aplicativo. Caso contrário, seu conteúdo pode incluir fontes que tenham seus protocolos de autenticação. Para obter mais informações, consulte [autenticar um usuário em uma guia do Microsoft Teams](~/tabs/how-to/authentication/auth-flow-tab.md). Use as informações de contexto para construir as solicitações de autenticação e os URLs da página de autorização. Certifique-se de que todos os domínios usados ​​em suas páginas de guia estejam listados na matriz `manifest.json` e `validDomains`.

## <a name="modify-or-remove-a-tab"></a>Modificar ou remover uma guia

Defina a propriedade do manifesto `canUpdateConfiguration` como `true`. Ele permite que os usuários modifiquem, reconfigurem ou renomeiem uma guia de canal ou grupo. Informe o usuário sobre o impacto no conteúdo quando uma guia for removida. Para fazer isso, inclua uma página de opções de remoção no aplicativo e defina um valor para a `removeUrl` `setConfig()` propriedade na configuração ( `setSettings()`anteriormente). O usuário pode desinstalar guias pessoais, mas não pode modificá-las. Para obter mais informações, consulte [criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md).

`setConfig()` Microsoft Teams (anteriormente`setSettings()`) para página de remoção:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```javascript
const configPromise = pages.config.setConfig({
    contentUrl: "add content page URL here",
    entityId: "add a unique identifier here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
configPromise.
    then((result) => {/*Successful operation*/).
    catch((error) => {/*Unsuccessful operation*/});
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add a unique identifier here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

***

## <a name="mobile-clients"></a>Clientes móveis

Se você optar por exibir sua guia de canal ou grupo nos clientes móveis do Teams, a configuração `setConfig()` deve ter um valor para `websiteUrl`. Para obter mais informações, consulte [orientação para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md)

## <a name="see-also"></a>Confira também

* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Criar uma página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
