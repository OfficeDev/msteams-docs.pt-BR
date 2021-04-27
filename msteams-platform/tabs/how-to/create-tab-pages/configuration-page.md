---
title: Criar uma página de configuração
author: laujan
description: como criar uma página de configuração
keywords: canal de grupo de guias do teams configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 0866d11442f79cee33d4454dbd4ed4d6b4b1a840
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019591"
---
# <a name="create-a-configuration-page"></a><span data-ttu-id="5cf8e-104">Criar uma página de configuração</span><span class="sxs-lookup"><span data-stu-id="5cf8e-104">Create a configuration page</span></span>

<span data-ttu-id="5cf8e-105">Uma página de configuração é um tipo especial [de página de conteúdo.](content-page.md)</span><span class="sxs-lookup"><span data-stu-id="5cf8e-105">A configuration page is a special type of [content page](content-page.md).</span></span> <span data-ttu-id="5cf8e-106">Os usuários configuram alguns aspectos do aplicativo do Microsoft Teams usando a página de configuração e usam essa configuração como parte do seguinte:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-106">The users configure some aspects of the Microsoft Teams app using the configuration page and use that configuration as part of the following:</span></span>

* <span data-ttu-id="5cf8e-107">Uma guia de chat de canal ou grupo - Coletar informações dos usuários e definir a `contentUrl` página de conteúdo a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-107">A channel or group chat tab - Collect information from the users and set the `contentUrl` of the content page to display.</span></span>
* <span data-ttu-id="5cf8e-108">Uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="5cf8e-108">A [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md)</span></span>
* <span data-ttu-id="5cf8e-109">Um [conector do Office 365](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span><span class="sxs-lookup"><span data-stu-id="5cf8e-109">An [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span></span>

## <a name="configuring-a-channel-or-group-chat-tab"></a><span data-ttu-id="5cf8e-110">Configurando uma guia de chat de canal ou grupo</span><span class="sxs-lookup"><span data-stu-id="5cf8e-110">Configuring a channel or group chat tab</span></span>

<span data-ttu-id="5cf8e-111">O aplicativo deve fazer referência ao [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript do Microsoft Teams e chamar `microsoft.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="5cf8e-111">The application must reference the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and call `microsoft.initialize()`.</span></span> <span data-ttu-id="5cf8e-112">Além disso, as URLs usadas devem ser pontos de extremidade HTTPS protegidos e disponíveis na nuvem.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-112">Also, the URLs used must be secured HTTPS endpoints and available from the cloud.</span></span> 

### <a name="example"></a><span data-ttu-id="5cf8e-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5cf8e-113">Example</span></span>

<span data-ttu-id="5cf8e-114">Um exemplo de página de configuração é mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-114">An example of a configuration page is shown in the following image:</span></span> 

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

<span data-ttu-id="5cf8e-115">O código correspondente para a página de configuração é mostrado na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-115">The corresponding code for configuration page is shown in the following section:</span></span>

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

<span data-ttu-id="5cf8e-116">Escolha Selecionar **Botão Cinza** ou **Selecione Vermelho** na página de configuração, para exibir o conteúdo da guia com um ícone cinza ou vermelho.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-116">Choose either **Select Gray** or **Select Red** button in the configuration page, to display the tab content with a gray or red icon.</span></span> 

<span data-ttu-id="5cf8e-117">A imagem a seguir exibe o conteúdo da guia com ícone cinza:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-117">The following image displays the tab content with gray icon:</span></span>

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

<span data-ttu-id="5cf8e-118">A imagem a seguir exibe o conteúdo da guia com o ícone vermelho:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-118">The following image displays the tab content with red icon:</span></span>

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

<span data-ttu-id="5cf8e-119">Escolher o botão relativo dispara `saveGray()` ou , e invoca o `saveRed()` seguinte:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-119">Choosing the relative button triggers either `saveGray()` or `saveRed()`, and invokes the following:</span></span>

1. <span data-ttu-id="5cf8e-120">O `settings.setValidityState(true)` é definido como true.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-120">The `settings.setValidityState(true)` is set to true.</span></span>
1. <span data-ttu-id="5cf8e-121">O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é acionado.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-121">The `microsoftTeams.settings.registerOnSaveHandler()` event handler is triggered.</span></span>
1. <span data-ttu-id="5cf8e-122">O **botão Salvar** na página de configuração do aplicativo, carregado no Teams, está habilitado.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-122">The **Save** button on the app's configuration page, uploaded in Teams, is enabled.</span></span>

<span data-ttu-id="5cf8e-123">O código da página de configuração informa ao Teams que os requisitos de configuração estão satisfeitos e que a instalação pode continuar.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-123">The configuration page code informs the Teams that the configuration requirements are satisfied and the installation can proceed.</span></span> <span data-ttu-id="5cf8e-124">Quando o usuário seleciona **Salvar**, os parâmetros de `settings.setSettings()` são definidos, conforme definido pela `Settings` interface.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-124">When the user selects **Save**, the parameters of `settings.setSettings()` are set, as defined by the `Settings` interface.</span></span> <span data-ttu-id="5cf8e-125">Para obter mais informações, consulte [Configurações interface](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="5cf8e-125">For more information, see [Settings interface](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="5cf8e-126">Na última etapa, é `saveEvent.notifySuccess()` chamado para indicar que a URL de conteúdo foi resolvida com êxito.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-126">In the last step, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

>[!NOTE]
>
>* <span data-ttu-id="5cf8e-127">Se você registrar um manipulador de salvar usando , o retorno de chamada deverá invocar ou `microsoftTeams.settings.registerOnSaveHandler()` indicar o resultado da `saveEvent.notifySuccess()` `saveEvent.notifyFailure()` configuração.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-127">If you register a save handler using `microsoftTeams.settings.registerOnSaveHandler()`, the callback must invoke `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to indicate the outcome of the configuration.</span></span>
>* <span data-ttu-id="5cf8e-128">Se você não registrar um manipulador de salvar, a chamada será feita automaticamente quando o `saveEvent.notifySuccess()` usuário selecionar **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-128">If you don't register a save handler, the `saveEvent.notifySuccess()` call is made automatically when the user selects **Save**.</span></span>

### <a name="get-context-data-for-your-tab-settings"></a><span data-ttu-id="5cf8e-129">Obter dados de contexto para suas configurações de tabulação</span><span class="sxs-lookup"><span data-stu-id="5cf8e-129">Get context data for your tab settings</span></span>

<span data-ttu-id="5cf8e-130">Sua guia pode exigir informações contextuais para exibir conteúdo relevante.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-130">Your tab might require contextual information to display relevant content.</span></span> <span data-ttu-id="5cf8e-131">As informações contextuais aprimora ainda mais o apelo da guia, fornecendo uma experiência de usuário mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-131">Contextual information further enhances your tab's appeal by providing a more customized user experience.</span></span>

<span data-ttu-id="5cf8e-132">Para obter mais informações sobre as propriedades usadas para a configuração de tabulação, consulte [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="5cf8e-132">For more information on the properties used for tab configuration, see [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="5cf8e-133">Colete os valores das variáveis de dados de contexto das duas seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-133">Collect the values of context data variables in the following two ways:</span></span>

1. <span data-ttu-id="5cf8e-134">Inserir os espaço reservados da cadeia de caracteres de consulta de URL no `configurationURL` seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-134">Insert URL query string placeholders in your manifest's `configurationURL`.</span></span>

1. <span data-ttu-id="5cf8e-135">Use o [método SDK do](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` Teams.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-135">Use the [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` method.</span></span>

#### <a name="insert-placeholders-in-the-configurationurl"></a><span data-ttu-id="5cf8e-136">Inserir espaço reservados no `configurationUrl`</span><span class="sxs-lookup"><span data-stu-id="5cf8e-136">Insert placeholders in the `configurationUrl`</span></span>

<span data-ttu-id="5cf8e-137">Adicione os espaço reservados de interface de contexto à sua base `configurationUrl` .</span><span class="sxs-lookup"><span data-stu-id="5cf8e-137">Add context interface placeholders to your base `configurationUrl`.</span></span> <span data-ttu-id="5cf8e-138">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-138">For example:</span></span>

##### <a name="base-url"></a><span data-ttu-id="5cf8e-139">Base URL</span><span class="sxs-lookup"><span data-stu-id="5cf8e-139">Base URL</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a><span data-ttu-id="5cf8e-140">URL base com cadeias de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="5cf8e-140">Base URL with query strings</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

<span data-ttu-id="5cf8e-141">Depois que sua página é carregada, o Teams atualiza os espaço reservados da cadeia de caracteres de consulta com valores relevantes.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-141">After your page uploads, the Teams updates the query string placeholders with relevant values.</span></span> <span data-ttu-id="5cf8e-142">Inclua lógica na página de configuração para recuperar e usar esses valores.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-142">Include logic in the configuration page to retrieve and use those values.</span></span> <span data-ttu-id="5cf8e-143">Para obter mais informações sobre como trabalhar com cadeias de caracteres de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) em MDN Web Docs. O exemplo a seguir descreve a maneira de extrair um valor da `configurationUrl` propriedade:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-143">For more information on working with URL query strings, see [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. The following example describes the way to extract a value from the `configurationUrl` property:</span></span>

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a><span data-ttu-id="5cf8e-144">Usar a `getContext()` função para recuperar o contexto</span><span class="sxs-lookup"><span data-stu-id="5cf8e-144">Use the `getContext()` function to retrieve context</span></span>

<span data-ttu-id="5cf8e-145">A `microsoftTeams.getContext((context) => {})` função recupera a interface context [quando](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) invocada.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-145">The `microsoftTeams.getContext((context) => {})` function retrieves the [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) when invoked.</span></span> <span data-ttu-id="5cf8e-146">Adicione essa função à página de configuração para recuperar valores de contexto:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-146">Add this function to the configuration page to retrieve context values:</span></span>

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

## <a name="context-and-authentication"></a><span data-ttu-id="5cf8e-147">Contexto e autenticação</span><span class="sxs-lookup"><span data-stu-id="5cf8e-147">Context and authentication</span></span>

 <span data-ttu-id="5cf8e-148">Autenticar antes de permitir que um usuário configure seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-148">Authenticate before allowing a user to configure your app.</span></span> <span data-ttu-id="5cf8e-149">Caso contrário, seu conteúdo pode incluir fontes que tenham seus protocolos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-149">Otherwise, your content might include sources that have their authentication protocols.</span></span> <span data-ttu-id="5cf8e-150">Para obter mais informações, [consulte Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use informações de contexto para construir as URLs da página de autorização e solicitações de autenticação.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-150">For more information, see [Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use context information to construct the authentication requests and authorization page URLs.</span></span>
<span data-ttu-id="5cf8e-151">Verifique se todos os domínios usados em suas páginas de tabulação estão listados `manifest.json` na matriz `validDomains` e.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-151">Ensure that all domains used in your tab pages are listed in the `manifest.json` and `validDomains` array.</span></span>

## <a name="modify-or-remove-a-tab"></a><span data-ttu-id="5cf8e-152">Modificar ou remover uma guia</span><span class="sxs-lookup"><span data-stu-id="5cf8e-152">Modify or remove a tab</span></span>

<span data-ttu-id="5cf8e-153">As opções de remoção suportadas refinam ainda mais a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-153">Supported removal options further refine the user experience.</span></span> <span data-ttu-id="5cf8e-154">De definir a propriedade do manifesto como , que permite aos usuários `canUpdateConfiguration` `true` modificar, reconfigurar ou renomear uma guia de grupo ou canal. Além disso, indique o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no aplicativo e definindo um valor para a propriedade `removeUrl` na  `setSettings()` configuração.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-154">Set your manifest's `canUpdateConfiguration` property to `true`, that enables the users to modify, reconfigure, or rename a group or channel tab. Also, indicate what happens to the content when a tab is removed, by including a removal options page in the app and setting a value for the `removeUrl` property in the  `setSettings()` configuration.</span></span> <span data-ttu-id="5cf8e-155">O usuário pode desinstalar as guias Pessoais, mas não pode modificá-las.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-155">The user can uninstall the Personal tabs but cannot modify them.</span></span> <span data-ttu-id="5cf8e-156">Para obter mais informações, [consulte Criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md).</span><span class="sxs-lookup"><span data-stu-id="5cf8e-156">For more information, see [Create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span></span>

<span data-ttu-id="5cf8e-157">Configuração do Microsoft Teams setSettings() para página de remoção:</span><span class="sxs-lookup"><span data-stu-id="5cf8e-157">Microsoft Teams setSettings() configuration for removal page:</span></span>

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

## <a name="mobile-clients"></a><span data-ttu-id="5cf8e-158">Clientes móveis</span><span class="sxs-lookup"><span data-stu-id="5cf8e-158">Mobile clients</span></span>

<span data-ttu-id="5cf8e-159">Se você optar por fazer com que seu canal ou guia de grupo apareça nos clientes móveis do Teams, a configuração deve ter um `setSettings()` valor para a `websiteUrl` propriedade.</span><span class="sxs-lookup"><span data-stu-id="5cf8e-159">If you choose to have your channel or group tab appear on the Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property.</span></span> <span data-ttu-id="5cf8e-160">Para obter mais informações, [consulte diretrizes para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md).</span><span class="sxs-lookup"><span data-stu-id="5cf8e-160">For more information, see [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md).</span></span>
