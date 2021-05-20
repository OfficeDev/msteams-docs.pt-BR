---
title: Criar uma página de configuração
author: laujan
description: como criar uma página de configuração
keywords: equipes guias canal grupo configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: aeab1cf96d1e875db79d9143fefd0e46348f585a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566681"
---
# <a name="create-a-configuration-page"></a>Criar uma página de configuração

Uma página de configuração é um tipo especial de página de [conteúdo](content-page.md). Os usuários configuram alguns aspectos do aplicativo Microsoft Teams usando a página de configuração e usam essa configuração como parte do seguinte:

* Uma guia de bate-papo de canal ou grupo: coletar informações dos usuários e definir a `contentUrl` página de conteúdo para exibir.
* Uma [extensão de mensagens.](~/messaging-extensions/what-are-messaging-extensions.md)
* Um [conector de Office 365.](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)

## <a name="configuring-a-channel-or-group-chat-tab"></a>Configuração de uma guia de bate-papo de canal ou grupo

O aplicativo deve fazer referência ao [Microsoft Teams cliente JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) e ligar `microsoft.initialize()` . Além disso, os URLs utilizados devem ser protegidos de pontos finais HTTPS e disponíveis na nuvem. 

### <a name="example"></a>Exemplo

Um exemplo de uma página de configuração é mostrado na imagem a seguir: 

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

O código correspondente para a página de configuração é mostrado na seguinte seção:

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

Escolha **selecionar o** botão Cinza ou **Selecionar Vermelho** na página de configuração, para exibir o conteúdo da guia com um ícone cinza ou vermelho. 

A imagem a seguir exibe o conteúdo da guia com o ícone cinza:

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

A imagem a seguir exibe o conteúdo da guia com o ícone vermelho:

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

Escolher o botão relativo aciona `saveGray()` ou , e invoca o `saveRed()` seguinte:

1. O `settings.setValidityState(true)` está definido para a verdade.
1. O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é acionado.
1. O botão **Salvar** na página de configuração do aplicativo, carregado em Teams, está ativado.

O código da página de configuração informa o Teams que os requisitos de configuração estão satisfeitos e a instalação pode prosseguir. Quando o usuário seleciona **Salvar,** os parâmetros `settings.setSettings()` são definidos, conforme definido pela `Settings` interface. Para obter mais informações, consulte [Configurações interface](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true). Na última etapa, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com sucesso.

>[!NOTE]
>
>* Se você registrar um manipulador de salvamento `microsoftTeams.settings.registerOnSaveHandler()` usando, o retorno de chamada deve invocar `saveEvent.notifySuccess()` ou indicar o resultado da `saveEvent.notifyFailure()` configuração.
>* Se você não registrar um manipulador de salvamento, a `saveEvent.notifySuccess()` chamada será feita automaticamente quando o usuário selecionar **Salvar**.

### <a name="get-context-data-for-your-tab-settings"></a>Obtenha dados de contexto para as configurações de suas guias

Sua guia pode exigir informações contextuais para exibir conteúdo relevante. As informações contextuais aumentam ainda mais o apelo da sua guia, fornecendo uma experiência de usuário mais personalizada.

Para obter mais informações sobre as propriedades usadas para configuração de guias, consulte [interface Contexto](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true). Coletar os valores das variáveis de dados de contexto das seguintes maneiras:

1. Insira os espaços reservados de sequência de sequência de perguntas de URL no manifesto do seu manifesto `configurationURL` .

1. Use o método [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` Teams.

#### <a name="insert-placeholders-in-the-configurationurl"></a>Inserir espaços reservados no `configurationUrl`

Adicione espaços reservados de interface de contexto à sua base `configurationUrl` . Por exemplo:

##### <a name="base-url"></a>Base URL

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a>URL base com strings de consulta

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

Após o upload da página, o Teams atualiza os espaços reservados de sequência de caracteres de consulta com valores relevantes. Inclua lógica na página de configuração para recuperar e usar esses valores. Para obter mais informações sobre como trabalhar com strings de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) no MDN Web Docs. O exemplo a seguir descreve a maneira de extrair um valor da `configurationUrl` propriedade:

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a>Use a `getContext()` função para recuperar o contexto

A `microsoftTeams.getContext((context) => {})` função recupera a interface [Contexto](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) quando invocada. Adicione esta função à página de configuração para recuperar valores de contexto:

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

 Autentique antes de permitir que um usuário configure seu aplicativo. Caso contrário, seu conteúdo pode incluir fontes que têm seus protocolos de autenticação. Para obter mais informações, consulte [Autenticar um usuário em uma guia Microsoft Teams](~/tabs/how-to/authentication/auth-flow-tab.md). Use informações de contexto para construir as solicitações de autenticação e as URLs da página de autorização.
Certifique-se de que todos os domínios usados em suas páginas de guia estejam listados no `manifest.json` e `validDomains` no array.

## <a name="modify-or-remove-a-tab"></a>Modifique ou remova uma guia

Opções de remoção suportadas refinam ainda mais a experiência do usuário. Defina a propriedade do manifesto `canUpdateConfiguration` para , que permite que os usuários `true` modifiquem, reconfigurem ou renomeiem uma guia de grupo ou canal. Além disso, indique o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no aplicativo e definindo um valor para a `removeUrl` propriedade na  `setSettings()` configuração. O usuário pode desinstalar as guias Pessoais, mas não pode modificá-las. Para obter mais informações, consulte [Criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md).

Microsoft Teams configuração setSettings() para a página de remoção:

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

Se você optar por ter seu canal ou aba de grupo aparecendo na Teams clientes móveis, a `setSettings()` configuração deve ter um valor para o `websiteUrl` imóvel. Para obter mais informações, consulte [orientação para guias no celular](~/tabs/design/tabs-mobile.md).
