---
title: Criar uma página de configuração
author: surbhigupta
description: Saiba como criar uma página de configuração para configurar um canal ou chat em grupo para configurações, como obter dados de contexto, inserir espaços reservados e autenticação usando exemplos de código.
keywords: equipes guias grupo canal configurável
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 912e38fc63d8c897f086d27362ad249688ce7ce9
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111637"
---
# <a name="create-a-configuration-page"></a>Criar uma página de configuração

Uma página de configuração é um tipo especial de [página de conteúdo](content-page.md). Os usuários configuram alguns aspectos do aplicativo Microsoft Teams usando a página de configuração e usam essa configuração como parte do seguinte:

* Um canal ou guia de chat em grupo: colete informações dos usuários e defina o `contentUrl` da página de conteúdo a ser exibida.
* Uma [extensão de mensagem](~/messaging-extensions/what-are-messaging-extensions.md).
* Um [Conector do Office 365](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="configure-a-channel-or-group-chat-tab"></a>Configurar um canal ou guia de chat em grupo

O aplicativo deve fazer referência ao [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) e chamar `microsoft.initialize()`. Os URLs usados ​​devem ser pontos de extremidade HTTPS seguros e disponíveis na nuvem.

### <a name="example"></a>Exemplo

Um exemplo de uma página de configuração é mostrado na imagem a seguir:

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

Escolha o botão **Selecionar cinza** ou **Selecionar vermelho** na página de configuração para exibir o conteúdo da guia com um ícone cinza ou vermelho.

A imagem a seguir exibe o conteúdo da guia com o ícone **Cinza** selecionado:

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

A imagem a seguir exibe o conteúdo da guia com o ícone **Vermelho** selecionado:

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

Escolher o botão apropriado aciona `saveGray()` ou `saveRed()` e invoca o seguinte:

* Defina `settings.setValidityState(true)` como verdadeiro.
* O manipulador de eventos `microsoftTeams.settings.registerOnSaveHandler()` é acionado.
* **Salvar** na página de configuração do aplicativo, está habilitado.

O código da página de configuração informa ao Teams que os requisitos de configuração foram atendidos e a instalação pode prosseguir. Quando o usuário seleciona **Salvar**, os parâmetros de `settings.setSettings()` são definidos, conforme definido pela interface `Settings`. Para obter mais informações, consulte a [interface de configurações](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true). `saveEvent.notifySuccess()` é chamado para indicar que a URL do conteúdo foi resolvida com sucesso.

>[!NOTE]
>
>* Você tem 30 segundos para concluir a operação de salvamento (o retorno de chamada para registerOnSaveHandler) antes do tempo limite. Após o tempo limite, uma mensagem de erro genérica é exibida.
>* Se você registrar um manipulador de salvamento usando `microsoftTeams.settings.registerOnSaveHandler()`, o retorno de chamada deverá invocar `saveEvent.notifySuccess()` ou `saveEvent.notifyFailure()` para indicar o resultado da configuração.
>* Se você não registrar um manipulador de salvamento, a chamada `saveEvent.notifySuccess()` será feita automaticamente quando o usuário selecionar **Salvar**.

### <a name="get-context-data-for-your-tab-settings"></a>Obter dados de contexto para suas configurações de guia

Sua guia requer informações contextuais para exibir conteúdo relevante. As informações contextuais aprimoram ainda mais o apelo de sua guia, fornecendo uma experiência de usuário mais personalizada.

Para obter mais informações sobre as propriedades usadas para configuração de guias, consulte [interface de contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true). Colete os valores das variáveis ​​de dados de contexto das duas maneiras a seguir:

* Insira marcadores de cadeia de caracteres de consulta de URL no `configurationURL` do seu manifesto.

* Use o método [SDK do Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})`.

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a>Use a função `getContext()` para recuperar o contexto

A função `microsoftTeams.getContext((context) => {})` recupera a [interface de contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) quando invocada.

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

Autentique antes de permitir que um usuário configure seu aplicativo. Caso contrário, seu conteúdo pode incluir fontes que tenham seus protocolos de autenticação. Para obter mais informações, consulte [autenticar um usuário em uma guia do Microsoft Teams](~/tabs/how-to/authentication/auth-flow-tab.md). Use as informações de contexto para construir as solicitações de autenticação e os URLs da página de autorização. Certifique-se de que todos os domínios usados ​​em suas páginas de guia estejam listados na matriz `manifest.json` e `validDomains`.

## <a name="modify-or-remove-a-tab"></a>Modificar ou remover uma guia

Defina a propriedade `canUpdateConfiguration` do seu manifesto como `true`, que permite que os usuários modifiquem, reconfigurem ou renomeiem um canal ou guia de grupo. Além disso, indique o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no aplicativo e definindo um valor para a propriedade `removeUrl` na configuração `setSettings()`. O usuário pode desinstalar guias pessoais, mas não pode modificá-las. Para obter mais informações, consulte [criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md).

Configuração do Microsoft Teams `setSettings()` para página de remoção:

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

Se você optar por exibir sua guia de canal ou grupo nos clientes móveis do Teams, a configuração `setSettings()` deve ter um valor para `websiteUrl`. Para obter mais informações, consulte [orientação para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md)

## <a name="see-also"></a>Confira também

* [Guias de equipes](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Criar uma página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
