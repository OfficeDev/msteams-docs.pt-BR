---
title: Criar uma página de configuração
author: surbhigupta
description: como criar uma página de configuração
keywords: canal de grupo de guias do teams configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 4fb7667cdcd060d44b64de1719bff69b3f96615f
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179766"
---
# <a name="create-a-configuration-page"></a><span data-ttu-id="dff97-104">Criar uma página de configuração</span><span class="sxs-lookup"><span data-stu-id="dff97-104">Create a configuration page</span></span>

<span data-ttu-id="dff97-105">Uma página de configuração é um tipo especial [de página de conteúdo.](content-page.md)</span><span class="sxs-lookup"><span data-stu-id="dff97-105">A configuration page is a special type of [content page](content-page.md).</span></span> <span data-ttu-id="dff97-106">Os usuários configuram alguns aspectos do aplicativo Microsoft Teams usando a página de configuração e usam essa configuração como parte do seguinte:</span><span class="sxs-lookup"><span data-stu-id="dff97-106">The users configure some aspects of the Microsoft Teams app using the configuration page and use that configuration as part of the following:</span></span>

* <span data-ttu-id="dff97-107">Uma guia de chat de canal ou grupo: Coletar informações dos usuários e definir a `contentUrl` página de conteúdo a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="dff97-107">A channel or group chat tab: Collect information from the users and set the `contentUrl` of the content page to be displayed.</span></span>
* <span data-ttu-id="dff97-108">Uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="dff97-108">A [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md).</span></span>
* <span data-ttu-id="dff97-109">Um [Office 365 Conector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).</span><span class="sxs-lookup"><span data-stu-id="dff97-109">An [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).</span></span>

## <a name="configure-a-channel-or-group-chat-tab"></a><span data-ttu-id="dff97-110">Configurar um canal ou uma guia de chat de grupo</span><span class="sxs-lookup"><span data-stu-id="dff97-110">Configure a channel or group chat tab</span></span>

<span data-ttu-id="dff97-111">O aplicativo deve fazer referência Microsoft Teams [SDK do cliente JavaScript](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) e chamar `microsoft.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="dff97-111">The application must reference the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and call `microsoft.initialize()`.</span></span> <span data-ttu-id="dff97-112">As URLs usadas devem ser pontos de extremidade HTTPS protegidos e disponíveis na nuvem.</span><span class="sxs-lookup"><span data-stu-id="dff97-112">The URLs used must be secured HTTPS endpoints and available from the cloud.</span></span>

### <a name="example"></a><span data-ttu-id="dff97-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dff97-113">Example</span></span>

<span data-ttu-id="dff97-114">Um exemplo de página de configuração é mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="dff97-114">An example of a configuration page is shown in the following image:</span></span>

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

<span data-ttu-id="dff97-115">O código a seguir é um exemplo de código correspondente para a página de configuração:</span><span class="sxs-lookup"><span data-stu-id="dff97-115">The following code is an example of corresponding code for the configuration page:</span></span>

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

<span data-ttu-id="dff97-116">Escolha Selecionar **Botão Cinza** ou **Selecione Vermelho** na página de configuração, para exibir o conteúdo da guia com um ícone cinza ou vermelho.</span><span class="sxs-lookup"><span data-stu-id="dff97-116">Choose either **Select Gray** or **Select Red** button in the configuration page, to display the tab content with a gray or red icon.</span></span>

<span data-ttu-id="dff97-117">A imagem a seguir exibe o conteúdo da guia com um ícone cinza:</span><span class="sxs-lookup"><span data-stu-id="dff97-117">The following image displays the tab content with a gray icon:</span></span>

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

<span data-ttu-id="dff97-118">A imagem a seguir exibe o conteúdo da guia com um ícone vermelho:</span><span class="sxs-lookup"><span data-stu-id="dff97-118">The following image displays the tab content with a red icon:</span></span>

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

<span data-ttu-id="dff97-119">Escolher o botão apropriado dispara `saveGray()` ou , e invoca o `saveRed()` seguinte:</span><span class="sxs-lookup"><span data-stu-id="dff97-119">Choosing the appropriate button triggers either `saveGray()` or `saveRed()`, and invokes the following:</span></span>

* <span data-ttu-id="dff97-120">Definir `settings.setValidityState(true)` como true.</span><span class="sxs-lookup"><span data-stu-id="dff97-120">Set `settings.setValidityState(true)` to true.</span></span> 
* <span data-ttu-id="dff97-121">O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é acionado.</span><span class="sxs-lookup"><span data-stu-id="dff97-121">The `microsoftTeams.settings.registerOnSaveHandler()` event handler is triggered.</span></span>
* <span data-ttu-id="dff97-122">**Salvar** na página de configuração do aplicativo está habilitado.</span><span class="sxs-lookup"><span data-stu-id="dff97-122">**Save** on the app's configuration page, is enabled.</span></span>

<span data-ttu-id="dff97-123">O código da página de configuração informa Teams que os requisitos de configuração estão satisfeitos e que a instalação pode continuar.</span><span class="sxs-lookup"><span data-stu-id="dff97-123">The configuration page code informs Teams that the configuration requirements are satisfied and the installation can proceed.</span></span> <span data-ttu-id="dff97-124">Quando o usuário seleciona **Salvar**, os parâmetros de `settings.setSettings()` são definidos, conforme definido pela `Settings` interface.</span><span class="sxs-lookup"><span data-stu-id="dff97-124">When the user selects **Save**, the parameters of `settings.setSettings()` are set, as defined by the `Settings` interface.</span></span> <span data-ttu-id="dff97-125">Para obter mais informações, consulte [interface de configurações](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="dff97-125">For more information, see [settings interface](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="dff97-126">`saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.</span><span class="sxs-lookup"><span data-stu-id="dff97-126">`saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

>[!NOTE]
>
>* <span data-ttu-id="dff97-127">Se você registrar um manipulador de salvar usando , o retorno de chamada deverá invocar ou `microsoftTeams.settings.registerOnSaveHandler()` indicar o resultado da `saveEvent.notifySuccess()` `saveEvent.notifyFailure()` configuração.</span><span class="sxs-lookup"><span data-stu-id="dff97-127">If you register a save handler using `microsoftTeams.settings.registerOnSaveHandler()`, the callback must invoke `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to indicate the outcome of the configuration.</span></span>
>* <span data-ttu-id="dff97-128">Se você não registrar um manipulador de salvar, a chamada será feita automaticamente quando o `saveEvent.notifySuccess()` usuário selecionar **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="dff97-128">If you do not register a save handler, the `saveEvent.notifySuccess()` call is made automatically when the user selects **Save**.</span></span>

### <a name="get-context-data-for-your-tab-settings"></a><span data-ttu-id="dff97-129">Obter dados de contexto para suas configurações de tabulação</span><span class="sxs-lookup"><span data-stu-id="dff97-129">Get context data for your tab settings</span></span>

<span data-ttu-id="dff97-130">Sua guia requer informações contextuais para exibir conteúdo relevante.</span><span class="sxs-lookup"><span data-stu-id="dff97-130">Your tab requires contextual information to display relevant content.</span></span> <span data-ttu-id="dff97-131">As informações contextuais aprimora ainda mais o apelo da guia, fornecendo uma experiência de usuário mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="dff97-131">Contextual information further enhances your tab's appeal by providing a more customized user experience.</span></span>

<span data-ttu-id="dff97-132">Para obter mais informações sobre as propriedades usadas para a configuração da guia, consulte [context interface](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="dff97-132">For more information on the properties used for tab configuration, see [context interface](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="dff97-133">Colete os valores das variáveis de dados de contexto das duas seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="dff97-133">Collect the values of context data variables in the following two ways:</span></span>

* <span data-ttu-id="dff97-134">Inserir os espaço reservados da cadeia de caracteres de consulta de URL no `configurationURL` seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="dff97-134">Insert URL query string placeholders in your manifest's `configurationURL`.</span></span>

* <span data-ttu-id="dff97-135">Use o [Teams SDK.](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})`</span><span class="sxs-lookup"><span data-stu-id="dff97-135">Use the [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` method.</span></span>

#### <a name="insert-placeholders-in-the-configurationurl"></a><span data-ttu-id="dff97-136">Inserir espaço reservados no `configurationUrl`</span><span class="sxs-lookup"><span data-stu-id="dff97-136">Insert placeholders in the `configurationUrl`</span></span>

<span data-ttu-id="dff97-137">Adicione os espaço reservados de interface de contexto à sua base `configurationUrl` .</span><span class="sxs-lookup"><span data-stu-id="dff97-137">Add context interface placeholders to your base `configurationUrl`.</span></span> <span data-ttu-id="dff97-138">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="dff97-138">For example:</span></span>

##### <a name="base-url"></a><span data-ttu-id="dff97-139">Base URL</span><span class="sxs-lookup"><span data-stu-id="dff97-139">Base URL</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a><span data-ttu-id="dff97-140">URL base com cadeias de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="dff97-140">Base URL with query strings</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

<span data-ttu-id="dff97-141">Depois que sua página é carregada, Teams atualiza os espaço reservados da cadeia de caracteres de consulta com valores relevantes.</span><span class="sxs-lookup"><span data-stu-id="dff97-141">After your page uploads, Teams updates the query string placeholders with relevant values.</span></span> <span data-ttu-id="dff97-142">Inclua lógica na página de configuração para recuperar e usar esses valores.</span><span class="sxs-lookup"><span data-stu-id="dff97-142">Include logic in the configuration page to retrieve and use those values.</span></span> <span data-ttu-id="dff97-143">Para obter mais informações sobre como trabalhar com cadeias de caracteres de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) em MDN Web Docs. O exemplo de código a seguir fornece a maneira de extrair um valor da `configurationUrl` propriedade:</span><span class="sxs-lookup"><span data-stu-id="dff97-143">For more information on working with URL query strings, see [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. The following code example provides the way to extract a value from the `configurationUrl` property:</span></span>

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a><span data-ttu-id="dff97-144">Usar a `getContext()` função para recuperar o contexto</span><span class="sxs-lookup"><span data-stu-id="dff97-144">Use the `getContext()` function to retrieve context</span></span>

<span data-ttu-id="dff97-145">A `microsoftTeams.getContext((context) => {})` função recupera a interface de [contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) quando invocada.</span><span class="sxs-lookup"><span data-stu-id="dff97-145">The `microsoftTeams.getContext((context) => {})` function retrieves the [context interface](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) when invoked.</span></span>

<span data-ttu-id="dff97-146">O código a seguir fornece um exemplo de adição dessa função à página de configuração para recuperar valores de contexto:</span><span class="sxs-lookup"><span data-stu-id="dff97-146">The following code provides an example of adding this function to the configuration page to retrieve context values:</span></span>

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

## <a name="context-and-authentication"></a><span data-ttu-id="dff97-147">Contexto e autenticação</span><span class="sxs-lookup"><span data-stu-id="dff97-147">Context and authentication</span></span>

<span data-ttu-id="dff97-148">Autenticar antes de permitir que um usuário configure seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dff97-148">Authenticate before allowing a user to configure your app.</span></span> <span data-ttu-id="dff97-149">Caso contrário, seu conteúdo pode incluir fontes que tenham seus protocolos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="dff97-149">Otherwise, your content might include sources that have their authentication protocols.</span></span> <span data-ttu-id="dff97-150">Para obter mais informações, [consulte authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use informações de contexto para construir as URLs da página de autorização e solicitações de autenticação.</span><span class="sxs-lookup"><span data-stu-id="dff97-150">For more information, see [authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use context information to construct the authentication requests and authorization page URLs.</span></span> <span data-ttu-id="dff97-151">Verifique se todos os domínios usados em suas páginas de tabulação estão listados `manifest.json` na matriz `validDomains` e.</span><span class="sxs-lookup"><span data-stu-id="dff97-151">Ensure that all domains used in your tab pages are listed in the `manifest.json` and `validDomains` array.</span></span>

## <a name="modify-or-remove-a-tab"></a><span data-ttu-id="dff97-152">Modificar ou remover uma guia</span><span class="sxs-lookup"><span data-stu-id="dff97-152">Modify or remove a tab</span></span>

<span data-ttu-id="dff97-153">De definir a propriedade do manifesto como , que permite que os usuários modifiquem, reconfigurem ou renomeiem um canal ou uma guia `canUpdateConfiguration` `true` de grupo. Além disso, indique o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no aplicativo e definindo um valor para a propriedade `removeUrl` na  `setSettings()` configuração.</span><span class="sxs-lookup"><span data-stu-id="dff97-153">Set your manifest's `canUpdateConfiguration` property to `true`, that enables the users to modify, reconfigure, or rename a channel or group tab. Also, indicate what happens to the content when a tab is removed, by including a removal options page in the app and setting a value for the `removeUrl` property in the  `setSettings()` configuration.</span></span> <span data-ttu-id="dff97-154">O usuário pode desinstalar guias pessoais, mas não pode modificá-las.</span><span class="sxs-lookup"><span data-stu-id="dff97-154">The user can uninstall personal tabs but cannot modify them.</span></span> <span data-ttu-id="dff97-155">Para obter mais informações, [consulte create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span><span class="sxs-lookup"><span data-stu-id="dff97-155">For more information, see [create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span></span>

<span data-ttu-id="dff97-156">`setSettings()`Microsoft Teams configuração para página de remoção:</span><span class="sxs-lookup"><span data-stu-id="dff97-156">Microsoft Teams `setSettings()` configuration for removal page:</span></span>

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

## <a name="mobile-clients"></a><span data-ttu-id="dff97-157">Clientes móveis</span><span class="sxs-lookup"><span data-stu-id="dff97-157">Mobile clients</span></span>

<span data-ttu-id="dff97-158">Se você optar por fazer com que seu canal ou guia de grupo apareça no Teams clientes móveis, a configuração deve ter `setSettings()` um valor para `websiteUrl` .</span><span class="sxs-lookup"><span data-stu-id="dff97-158">If you choose to have your channel or group tab appear on the Teams mobile clients, the `setSettings()` configuration must have a value for `websiteUrl`.</span></span> <span data-ttu-id="dff97-159">Para obter mais informações, [consulte diretrizes para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md).</span><span class="sxs-lookup"><span data-stu-id="dff97-159">For more information, see [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dff97-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="dff97-160">See also</span></span>

* [<span data-ttu-id="dff97-161">Teams guias</span><span class="sxs-lookup"><span data-stu-id="dff97-161">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="dff97-162">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="dff97-162">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="dff97-163">Criar um canal ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="dff97-163">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="dff97-164">Criar uma página de conteúdo</span><span class="sxs-lookup"><span data-stu-id="dff97-164">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
* [<span data-ttu-id="dff97-165">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="dff97-165">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)

## <a name="next-step"></a><span data-ttu-id="dff97-166">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="dff97-166">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dff97-167">Criar uma página de remoção para sua guia</span><span class="sxs-lookup"><span data-stu-id="dff97-167">Create a removal page for your tab</span></span>](~/tabs/how-to/create-tab-pages/removal-page.md)
