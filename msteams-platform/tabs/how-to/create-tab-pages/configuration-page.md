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
# <a name="create-a-configuration-page"></a><span data-ttu-id="47720-104">Criar uma página de configuração</span><span class="sxs-lookup"><span data-stu-id="47720-104">Create a configuration page</span></span>

<span data-ttu-id="47720-105">Uma página de configuração é um tipo especial de [página de conteúdo.](content-page.md)</span><span class="sxs-lookup"><span data-stu-id="47720-105">A configuration page is a special type of [content page](content-page.md).</span></span> <span data-ttu-id="47720-106">Os usuários configuram alguns aspectos do aplicativo Microsoft Teams usando a página de configuração e usam essa configuração como parte do seguinte:</span><span class="sxs-lookup"><span data-stu-id="47720-106">The users configure some aspects of the Microsoft Teams app using the configuration page and use that configuration as part of the following:</span></span>

* <span data-ttu-id="47720-107">Uma guia de chat de canal ou grupo - Coletar informações dos usuários e definir a `contentUrl` página de conteúdo a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="47720-107">A channel or group chat tab - Collect information from the users and set the `contentUrl` of the content page to display.</span></span>
* <span data-ttu-id="47720-108">Uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="47720-108">A [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md)</span></span>
* <span data-ttu-id="47720-109">Um [Conector do Office 365](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span><span class="sxs-lookup"><span data-stu-id="47720-109">An [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span></span>

## <a name="configuring-a-channel-or-group-chat-tab"></a><span data-ttu-id="47720-110">Configurando uma guia de chat de canal ou grupo</span><span class="sxs-lookup"><span data-stu-id="47720-110">Configuring a channel or group chat tab</span></span>

<span data-ttu-id="47720-111">O aplicativo deve fazer referência ao [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript do Microsoft Teams e `microsoft.initialize()` chamar.</span><span class="sxs-lookup"><span data-stu-id="47720-111">The application must reference the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and call `microsoft.initialize()`.</span></span> <span data-ttu-id="47720-112">Além disso, as URLs usadas devem estar protegidas por pontos de extremidade HTTPS e disponíveis na nuvem.</span><span class="sxs-lookup"><span data-stu-id="47720-112">Also, the URLs used must be secured HTTPS endpoints and available from the cloud.</span></span> <span data-ttu-id="47720-113">O código a seguir é um exemplo de uma página de configuração:</span><span class="sxs-lookup"><span data-stu-id="47720-113">The following code is an example of a configuration page:</span></span>

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

<span data-ttu-id="47720-114">Escolha o **botão Selecionar** **Cinza** ou Selecionar Vermelho na página de configuração, para exibir o conteúdo da guia com um ícone cinza ou vermelho.</span><span class="sxs-lookup"><span data-stu-id="47720-114">Choose either **Select Gray** or **Select Red** button in the configuration page, to display the tab content with a gray or red icon.</span></span> <span data-ttu-id="47720-115">Escolher o botão relativo dispara `saveGray()` ou `saveRed()` invoca o seguinte:</span><span class="sxs-lookup"><span data-stu-id="47720-115">Choosing the relative button fires either `saveGray()` or `saveRed()`, and invokes the following:</span></span>

1. <span data-ttu-id="47720-116">O `settings.setValidityState(true)` valor é definido como true.</span><span class="sxs-lookup"><span data-stu-id="47720-116">The `settings.setValidityState(true)` is set to true.</span></span>
1. <span data-ttu-id="47720-117">O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é disparado.</span><span class="sxs-lookup"><span data-stu-id="47720-117">The `microsoftTeams.settings.registerOnSaveHandler()` event handler is triggered.</span></span>
1. <span data-ttu-id="47720-118">O **botão** Salvar na página de configuração do aplicativo, carregado no Teams, está habilitado.</span><span class="sxs-lookup"><span data-stu-id="47720-118">The **Save** button on the app's configuration page, uploaded in Teams, is enabled.</span></span>

<span data-ttu-id="47720-119">O código da página de configuração informa ao Teams que os requisitos de configuração foram atendidos e que a instalação pode prosseguir.</span><span class="sxs-lookup"><span data-stu-id="47720-119">The configuration page code informs the Teams that the configuration requirements are satisfied and the installation can proceed.</span></span> <span data-ttu-id="47720-120">Quando o usuário seleciona **Salvar,** os parâmetros são `settings.setSettings()` definidos, conforme definido pela `Settings` interface.</span><span class="sxs-lookup"><span data-stu-id="47720-120">When the user selects **Save**, the parameters of `settings.setSettings()` are set, as defined by the `Settings` interface.</span></span> <span data-ttu-id="47720-121">Para obter mais informações, consulte [a interface Configurações.](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="47720-121">For more information, see [Settings interface](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="47720-122">Na última etapa, é `saveEvent.notifySuccess()` chamado para indicar que a URL de conteúdo foi resolvida com êxito.</span><span class="sxs-lookup"><span data-stu-id="47720-122">In the last step, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

>[!NOTE]
>
>* <span data-ttu-id="47720-123">Se você registrar um manipulador de salvar usando , o retorno de chamada deverá invocar ou `microsoftTeams.settings.registerOnSaveHandler()` indicar o resultado da `saveEvent.notifySuccess()` `saveEvent.notifyFailure()` configuração.</span><span class="sxs-lookup"><span data-stu-id="47720-123">If you register a save handler using `microsoftTeams.settings.registerOnSaveHandler()`, the callback must invoke `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to indicate the outcome of the configuration.</span></span>
>* <span data-ttu-id="47720-124">Se você não registrar um manipulador de salvar, a chamada será feita automaticamente `saveEvent.notifySuccess()` quando o usuário selecionar **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="47720-124">If you don't register a save handler, the `saveEvent.notifySuccess()` call is made automatically when the user selects **Save**.</span></span>

### <a name="get-context-data-for-your-tab-settings"></a><span data-ttu-id="47720-125">Obter dados de contexto para suas configurações de guia</span><span class="sxs-lookup"><span data-stu-id="47720-125">Get context data for your tab settings</span></span>

<span data-ttu-id="47720-126">Sua guia pode exigir informações contextuais para exibir conteúdo relevante.</span><span class="sxs-lookup"><span data-stu-id="47720-126">Your tab might require contextual information to display relevant content.</span></span> <span data-ttu-id="47720-127">As informações contextuais aprimora ainda mais a atraente da guia, fornecendo uma experiência de usuário mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="47720-127">Contextual information further enhances your tab's appeal by providing a more customized user experience.</span></span>

<span data-ttu-id="47720-128">Para obter mais informações sobre as propriedades usadas para a configuração de guia, consulte [Interface de contexto.](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="47720-128">For more information on the properties used for tab configuration, see [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="47720-129">Colete os valores das variáveis de dados de contexto das duas maneiras a seguir:</span><span class="sxs-lookup"><span data-stu-id="47720-129">Collect the values of context data variables in the following two ways:</span></span>

1. <span data-ttu-id="47720-130">Inserir os espaço reservados da cadeia de caracteres de consulta url em seu `configurationURL` manifesto.</span><span class="sxs-lookup"><span data-stu-id="47720-130">Insert URL query string placeholders in your manifest's `configurationURL`.</span></span>

1. <span data-ttu-id="47720-131">Use o [método SDK do](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` Teams.</span><span class="sxs-lookup"><span data-stu-id="47720-131">Use the [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` method.</span></span>

#### <a name="insert-placeholders-in-the-configurationurl"></a><span data-ttu-id="47720-132">Inserir os espaço reservados no `configurationUrl`</span><span class="sxs-lookup"><span data-stu-id="47720-132">Insert placeholders in the `configurationUrl`</span></span>

<span data-ttu-id="47720-133">Adicione os espaço reservados de interface de contexto à sua `configurationUrl` base.</span><span class="sxs-lookup"><span data-stu-id="47720-133">Add context interface placeholders to your base `configurationUrl`.</span></span> <span data-ttu-id="47720-134">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="47720-134">For example:</span></span>

##### <a name="base-url"></a><span data-ttu-id="47720-135">Base URL</span><span class="sxs-lookup"><span data-stu-id="47720-135">Base URL</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a><span data-ttu-id="47720-136">URL base com cadeias de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="47720-136">Base URL with query strings</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

<span data-ttu-id="47720-137">Depois que sua página é carregada, o Teams atualiza os espaço reservados da cadeia de caracteres de consulta com valores relevantes.</span><span class="sxs-lookup"><span data-stu-id="47720-137">After your page uploads, the Teams updates the query string placeholders with relevant values.</span></span> <span data-ttu-id="47720-138">Inclua lógica na página de configuração para recuperar e usar esses valores.</span><span class="sxs-lookup"><span data-stu-id="47720-138">Include logic in the configuration page to retrieve and use those values.</span></span> <span data-ttu-id="47720-139">Para obter mais informações sobre como trabalhar com cadeias de caracteres de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) em MDN Web Docs. O exemplo a seguir descreve a maneira de extrair um valor da `configurationUrl` propriedade:</span><span class="sxs-lookup"><span data-stu-id="47720-139">For more information on working with URL query strings, see [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. The following example describes the way to extract a value from the `configurationUrl` property:</span></span>

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a><span data-ttu-id="47720-140">Usar a `getContext()` função para recuperar o contexto</span><span class="sxs-lookup"><span data-stu-id="47720-140">Use the `getContext()` function to retrieve context</span></span>

<span data-ttu-id="47720-141">A `microsoftTeams.getContext((context) => {})` função recupera a interface de [contexto](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) quando invocada.</span><span class="sxs-lookup"><span data-stu-id="47720-141">The `microsoftTeams.getContext((context) => {})` function retrieves the [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) when invoked.</span></span> <span data-ttu-id="47720-142">Adicione essa função à página de configuração para recuperar valores de contexto:</span><span class="sxs-lookup"><span data-stu-id="47720-142">Add this function to the configuration page to retrieve context values:</span></span>

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

## <a name="context-and-authentication"></a><span data-ttu-id="47720-143">Contexto e autenticação</span><span class="sxs-lookup"><span data-stu-id="47720-143">Context and authentication</span></span>

 <span data-ttu-id="47720-144">Autenticar antes de permitir que um usuário configure seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47720-144">Authenticate before allowing a user to configure your app.</span></span> <span data-ttu-id="47720-145">Caso contrário, seu conteúdo poderá incluir fontes que tenham seus protocolos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="47720-145">Otherwise, your content might include sources that have their authentication protocols.</span></span> <span data-ttu-id="47720-146">Para saber mais, confira [Autenticar um usuário em uma guia do Microsoft Teams.](~/tabs/how-to/authentication/auth-flow-tab.md) Use informações de contexto para construir as URLs da página de autorização e solicitações de autenticação.</span><span class="sxs-lookup"><span data-stu-id="47720-146">For more information, see [Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use context information to construct the authentication requests and authorization page URLs.</span></span>
<span data-ttu-id="47720-147">Verifique se todos os domínios usados em suas páginas de guia estão listados na `manifest.json` matriz e na `validDomains` matriz.</span><span class="sxs-lookup"><span data-stu-id="47720-147">Ensure that all domains used in your tab pages are listed in the `manifest.json` and `validDomains` array.</span></span>

## <a name="modify-or-remove-a-tab"></a><span data-ttu-id="47720-148">Modificar ou remover uma guia</span><span class="sxs-lookup"><span data-stu-id="47720-148">Modify or remove a tab</span></span>

<span data-ttu-id="47720-149">As opções de remoção com suporte refinam ainda mais a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="47720-149">Supported removal options further refine the user experience.</span></span> <span data-ttu-id="47720-150">Definir a propriedade do manifesto como , que permite aos usuários `canUpdateConfiguration` `true` modificar, reconfigurar ou renomear um grupo ou guia de canal. Além disso, indique o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no aplicativo e definindo um valor para a propriedade `removeUrl` na  `setSettings()` configuração.</span><span class="sxs-lookup"><span data-stu-id="47720-150">Set your manifest's `canUpdateConfiguration` property to `true`, that enables the users to modify, reconfigure, or rename a group or channel tab. Also, indicate what happens to the content when a tab is removed, by including a removal options page in the app and setting a value for the `removeUrl` property in the  `setSettings()` configuration.</span></span> <span data-ttu-id="47720-151">Para obter mais informações, consulte [Clientes móveis.](#mobile-clients)</span><span class="sxs-lookup"><span data-stu-id="47720-151">For more information, see [Mobile clients](#mobile-clients).</span></span> <span data-ttu-id="47720-152">O usuário pode desinstalar as guias Pessoais, mas não pode modificá-las.</span><span class="sxs-lookup"><span data-stu-id="47720-152">The user can uninstall the Personal tabs but cannot modify them.</span></span> <span data-ttu-id="47720-153">Para obter mais informações, [consulte Criar uma página de remoção para sua guia.](~/tabs/how-to/create-tab-pages/removal-page.md)</span><span class="sxs-lookup"><span data-stu-id="47720-153">For more information, see [Create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span></span>

## <a name="mobile-clients"></a><span data-ttu-id="47720-154">Clientes móveis</span><span class="sxs-lookup"><span data-stu-id="47720-154">Mobile clients</span></span>

<span data-ttu-id="47720-155">Se você optar por que seu canal ou guia de grupo apareça nos clientes móveis do Teams, a configuração deverá ter `setSettings()` um valor para a `websiteUrl` propriedade.</span><span class="sxs-lookup"><span data-stu-id="47720-155">If you choose to have your channel or group tab appear on the Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property.</span></span> <span data-ttu-id="47720-156">Para obter mais informações, [consulte as diretrizes para guias em dispositivos móveis.](~/tabs/design/tabs-mobile.md)</span><span class="sxs-lookup"><span data-stu-id="47720-156">For more information, see [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md).</span></span>

<span data-ttu-id="47720-157">Configuração setSettings() do Microsoft Teams para página de remoção ou clientes móveis:</span><span class="sxs-lookup"><span data-stu-id="47720-157">Microsoft Teams setSettings() configuration for removal page or mobile clients:</span></span>

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "URL REQUIRED FOR MOBILE CLIENTS",
    removeUrl: "ADD REMOVAL PAGE URL HERE"
});
```
