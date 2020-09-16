---
title: Criar uma página de configuração
author: laujan
description: como criar uma página de configuração
keywords: guias do teams com o canal de grupo configurável
ms.topic: conceptualF
ms.author: lajanuar
ms.openlocfilehash: 6288fc8c296ebf0aa85ffe8e08234e5faf22a1ef
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "47819022"
---
# <a name="create-a-configuration-page"></a>Criar uma página de configuração

Uma página de configuração é um tipo especial de [página de conteúdo](content-page.md) que permite que os usuários configurem alguns aspectos de seu aplicativo do teams. Normalmente, são usados como parte de:

* Guia chat de grupo ou canal-a página de configuração permite coletar informações de seus usuários e definir a `contentUrl` página de conteúdo a ser exibida.
* Uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md)
* Um [conector do Office 365](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)

## <a name="configuring-a-channel-or-group-chat-tab"></a>Configurando uma guia chat de grupo ou canal

Uma página de configuração informa a página de conteúdo como ela deve renderizar. O aplicativo deve fazer referência ao SDK e à chamada do [cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) `microsoft.initialize()` . Além disso, suas URLs devem ser pontos de extremidade HTTPS seguros e disponíveis na nuvem. Veja a seguir um exemplo de página de configuração.

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

Aqui, os usuários são apresentados com dois botões de opção, **selecione cinza** ou **selecione vermelho** para exibir o conteúdo da guia com um ícone vermelho ou cinza. A escolha do botão relativo dispara `saveGray()` ou `saveRed()` invoca o seguinte:

1. O `settings.setValidityState(true)` é definido como true.
1. O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é disparado.
1. O botão **salvar** na página de configuração do aplicativo, carregado no Microsoft Teams, está habilitado.

Esse código permite que as equipes saibam que os requisitos de configuração foram satisfeitos e a instalação pode continuar. Ao **salvar**, os parâmetros de `settings.setSettings()` são definidos, conforme definido pela `Settings` interface, para a instância atual (consulte [interface de configurações](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest) ). Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.

>[!NOTE]
>
>* Se um manipulador de gravação foi registrado usando `microsoftTeams.settings.registerOnSaveHandler()` o, o retorno de chamada deve invocar `saveEvent.notifySuccess()` ou `saveEvent.notifyFailure()` indicar o resultado da configuração.
>* Se nenhum manipulador de salvamento foi registrado, a `saveEvent.notifySuccess()` chamada é automaticamente feita imediatamente após o usuário selecionando o botão **salvar** .

### <a name="get-context-data-for-your-tab-settings"></a>Obter dados de contexto para suas configurações de guia

Sua guia pode exigir informações contextuais para exibir conteúdo relevante. As informações contextuais podem aprimorar ainda mais o apelo da guia ao fornecer uma experiência de usuário mais personalizada.

A [interface de contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) do Microsoft Teams define as propriedades que podem ser usadas para sua configuração de guia. Você pode coletar os valores de variáveis de dados de contexto de duas maneiras:

1. Insira espaços reservados para cadeia de caracteres de consulta de URL no seu manifesto `configurationURL` .

1. Use o método [SDK do teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) `microsoftTeams.getContext((context) =>{}` .

#### <a name="insert-placeholders-in-the-configurationurl"></a>Inserir espaços reservados no `configurationURL`

Os espaços reservados de interface de contexto podem ser adicionados à sua base `configurationUrl` . Por exemplo:

##### <a name="base-url"></a>URL base

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

Depois que a página for carregada, os espaços reservados de cadeia de caracteres de consulta serão atualizados pelo Teams com os valores relevantes. Você pode incluir lógica na página de configuração para recuperar e usar esses valores. Para obter mais informações sobre como trabalhar com cadeias de caracteres de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web docs. Veja um exemplo de como extrair um valor da `configurationURL` Propriedade acima:

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

Quando invocado, a `microsoftTeams.getContext((context) => {})` função recupera a [interface de contexto](/javascript/api/@microsoft/teams-js//microsoftteams.context?view=msteams-client-js-latest). Você pode adicionar essa função à página de configuração para recuperar os valores de contexto:

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

Você pode exigir autenticação antes de permitir que um usuário configure seu aplicativo ou seu conteúdo pode incluir fontes que têm seus próprios protocolos de autenticação. Consulte [autenticar um usuário em uma guia do Microsoft Teams](~/tabs/how-to/authentication/auth-flow-tab.md) as informações de contexto podem ser usadas para ajudar a construir solicitações de autenticação e URLs de página de autorização.
Certifique-se de que todos os domínios usados nas páginas da guia estão listados na `manifest.json` `validDomains` matriz.

## <a name="modify-or-remove-a-tab"></a>Modificar ou remover uma guia

As opções de remoção suportadas podem aprimorar ainda mais a experiência do usuário. Você pode permitir que os usuários modifiquem, reconfigurem ou renomeie uma guia de grupo/canal, definindo a propriedade do manifesto `canUpdateConfiguration` como `true` .  Além disso, você pode designar o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no seu aplicativo e definir um valor para a `removeUrl` Propriedade na  `setSettings()` configuração (veja abaixo). As guias pessoais não podem ser modificadas, mas podem ser desinstaladas pelo usuário. Para obter mais informações, consulte [criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md).

## <a name="mobile-clients"></a>Clientes móveis

Se você optar por ter a guia canal/grupo exibida em clientes móveis do Microsoft Teams, a `setSettings()` configuração deverá ter um valor para a `websiteUrl` Propriedade (veja abaixo). O suporte completo para guias em clientes móveis será lançado em breve. Para se preparar para a atualização, siga as [orientações para guias em celular](~/tabs/design/tabs-mobile.md) ao criar suas guias.

Configuração do Microsoft Teams SetSettings () para a página de remoção e/ou clientes móveis:

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "URL REQUIRED FOR MOBILE CLIENTS",
    removeUrl: "ADD REMOVAL PAGE URL HERE"
});
```
