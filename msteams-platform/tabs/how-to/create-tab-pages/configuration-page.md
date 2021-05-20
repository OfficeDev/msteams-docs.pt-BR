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
# <a name="create-a-configuration-page"></a><span data-ttu-id="522ab-104">Criar uma página de configuração</span><span class="sxs-lookup"><span data-stu-id="522ab-104">Create a configuration page</span></span>

<span data-ttu-id="522ab-105">Uma página de configuração é um tipo especial de página de [conteúdo](content-page.md).</span><span class="sxs-lookup"><span data-stu-id="522ab-105">A configuration page is a special type of [content page](content-page.md).</span></span> <span data-ttu-id="522ab-106">Os usuários configuram alguns aspectos do aplicativo Microsoft Teams usando a página de configuração e usam essa configuração como parte do seguinte:</span><span class="sxs-lookup"><span data-stu-id="522ab-106">The users configure some aspects of the Microsoft Teams app using the configuration page and use that configuration as part of the following:</span></span>

* <span data-ttu-id="522ab-107">Uma guia de bate-papo de canal ou grupo: coletar informações dos usuários e definir a `contentUrl` página de conteúdo para exibir.</span><span class="sxs-lookup"><span data-stu-id="522ab-107">A channel or group chat tab: Collect information from the users and set the `contentUrl` of the content page to display.</span></span>
* <span data-ttu-id="522ab-108">Uma [extensão de mensagens.](~/messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="522ab-108">A [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md).</span></span>
* <span data-ttu-id="522ab-109">Um [conector de Office 365.](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span><span class="sxs-lookup"><span data-stu-id="522ab-109">An [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).</span></span>

## <a name="configuring-a-channel-or-group-chat-tab"></a><span data-ttu-id="522ab-110">Configuração de uma guia de bate-papo de canal ou grupo</span><span class="sxs-lookup"><span data-stu-id="522ab-110">Configuring a channel or group chat tab</span></span>

<span data-ttu-id="522ab-111">O aplicativo deve fazer referência ao [Microsoft Teams cliente JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) e ligar `microsoft.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="522ab-111">The application must reference the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and call `microsoft.initialize()`.</span></span> <span data-ttu-id="522ab-112">Além disso, os URLs utilizados devem ser protegidos de pontos finais HTTPS e disponíveis na nuvem.</span><span class="sxs-lookup"><span data-stu-id="522ab-112">Also, the URLs used must be secured HTTPS endpoints and available from the cloud.</span></span> 

### <a name="example"></a><span data-ttu-id="522ab-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="522ab-113">Example</span></span>

<span data-ttu-id="522ab-114">Um exemplo de uma página de configuração é mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="522ab-114">An example of a configuration page is shown in the following image:</span></span> 

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

<span data-ttu-id="522ab-115">O código correspondente para a página de configuração é mostrado na seguinte seção:</span><span class="sxs-lookup"><span data-stu-id="522ab-115">The corresponding code for configuration page is shown in the following section:</span></span>

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

<span data-ttu-id="522ab-116">Escolha **selecionar o** botão Cinza ou **Selecionar Vermelho** na página de configuração, para exibir o conteúdo da guia com um ícone cinza ou vermelho.</span><span class="sxs-lookup"><span data-stu-id="522ab-116">Choose either **Select Gray** or **Select Red** button in the configuration page, to display the tab content with a gray or red icon.</span></span> 

<span data-ttu-id="522ab-117">A imagem a seguir exibe o conteúdo da guia com o ícone cinza:</span><span class="sxs-lookup"><span data-stu-id="522ab-117">The following image displays the tab content with gray icon:</span></span>

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

<span data-ttu-id="522ab-118">A imagem a seguir exibe o conteúdo da guia com o ícone vermelho:</span><span class="sxs-lookup"><span data-stu-id="522ab-118">The following image displays the tab content with red icon:</span></span>

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

<span data-ttu-id="522ab-119">Escolher o botão relativo aciona `saveGray()` ou , e invoca o `saveRed()` seguinte:</span><span class="sxs-lookup"><span data-stu-id="522ab-119">Choosing the relative button triggers either `saveGray()` or `saveRed()`, and invokes the following:</span></span>

1. <span data-ttu-id="522ab-120">O `settings.setValidityState(true)` está definido para a verdade.</span><span class="sxs-lookup"><span data-stu-id="522ab-120">The `settings.setValidityState(true)` is set to true.</span></span>
1. <span data-ttu-id="522ab-121">O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é acionado.</span><span class="sxs-lookup"><span data-stu-id="522ab-121">The `microsoftTeams.settings.registerOnSaveHandler()` event handler is triggered.</span></span>
1. <span data-ttu-id="522ab-122">O botão **Salvar** na página de configuração do aplicativo, carregado em Teams, está ativado.</span><span class="sxs-lookup"><span data-stu-id="522ab-122">The **Save** button on the app's configuration page, uploaded in Teams, is enabled.</span></span>

<span data-ttu-id="522ab-123">O código da página de configuração informa o Teams que os requisitos de configuração estão satisfeitos e a instalação pode prosseguir.</span><span class="sxs-lookup"><span data-stu-id="522ab-123">The configuration page code informs the Teams that the configuration requirements are satisfied and the installation can proceed.</span></span> <span data-ttu-id="522ab-124">Quando o usuário seleciona **Salvar,** os parâmetros `settings.setSettings()` são definidos, conforme definido pela `Settings` interface.</span><span class="sxs-lookup"><span data-stu-id="522ab-124">When the user selects **Save**, the parameters of `settings.setSettings()` are set, as defined by the `Settings` interface.</span></span> <span data-ttu-id="522ab-125">Para obter mais informações, consulte [Configurações interface](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="522ab-125">For more information, see [Settings interface](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="522ab-126">Na última etapa, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com sucesso.</span><span class="sxs-lookup"><span data-stu-id="522ab-126">In the last step, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

>[!NOTE]
>
>* <span data-ttu-id="522ab-127">Se você registrar um manipulador de salvamento `microsoftTeams.settings.registerOnSaveHandler()` usando, o retorno de chamada deve invocar `saveEvent.notifySuccess()` ou indicar o resultado da `saveEvent.notifyFailure()` configuração.</span><span class="sxs-lookup"><span data-stu-id="522ab-127">If you register a save handler using `microsoftTeams.settings.registerOnSaveHandler()`, the callback must invoke `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to indicate the outcome of the configuration.</span></span>
>* <span data-ttu-id="522ab-128">Se você não registrar um manipulador de salvamento, a `saveEvent.notifySuccess()` chamada será feita automaticamente quando o usuário selecionar **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="522ab-128">If you don't register a save handler, the `saveEvent.notifySuccess()` call is made automatically when the user selects **Save**.</span></span>

### <a name="get-context-data-for-your-tab-settings"></a><span data-ttu-id="522ab-129">Obtenha dados de contexto para as configurações de suas guias</span><span class="sxs-lookup"><span data-stu-id="522ab-129">Get context data for your tab settings</span></span>

<span data-ttu-id="522ab-130">Sua guia pode exigir informações contextuais para exibir conteúdo relevante.</span><span class="sxs-lookup"><span data-stu-id="522ab-130">Your tab might require contextual information to display relevant content.</span></span> <span data-ttu-id="522ab-131">As informações contextuais aumentam ainda mais o apelo da sua guia, fornecendo uma experiência de usuário mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="522ab-131">Contextual information further enhances your tab's appeal by providing a more customized user experience.</span></span>

<span data-ttu-id="522ab-132">Para obter mais informações sobre as propriedades usadas para configuração de guias, consulte [interface Contexto](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="522ab-132">For more information on the properties used for tab configuration, see [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="522ab-133">Coletar os valores das variáveis de dados de contexto das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="522ab-133">Collect the values of context data variables in the following two ways:</span></span>

1. <span data-ttu-id="522ab-134">Insira os espaços reservados de sequência de sequência de perguntas de URL no manifesto do seu manifesto `configurationURL` .</span><span class="sxs-lookup"><span data-stu-id="522ab-134">Insert URL query string placeholders in your manifest's `configurationURL`.</span></span>

1. <span data-ttu-id="522ab-135">Use o método [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` Teams.</span><span class="sxs-lookup"><span data-stu-id="522ab-135">Use the [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` method.</span></span>

#### <a name="insert-placeholders-in-the-configurationurl"></a><span data-ttu-id="522ab-136">Inserir espaços reservados no `configurationUrl`</span><span class="sxs-lookup"><span data-stu-id="522ab-136">Insert placeholders in the `configurationUrl`</span></span>

<span data-ttu-id="522ab-137">Adicione espaços reservados de interface de contexto à sua base `configurationUrl` .</span><span class="sxs-lookup"><span data-stu-id="522ab-137">Add context interface placeholders to your base `configurationUrl`.</span></span> <span data-ttu-id="522ab-138">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="522ab-138">For example:</span></span>

##### <a name="base-url"></a><span data-ttu-id="522ab-139">Base URL</span><span class="sxs-lookup"><span data-stu-id="522ab-139">Base URL</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a><span data-ttu-id="522ab-140">URL base com strings de consulta</span><span class="sxs-lookup"><span data-stu-id="522ab-140">Base URL with query strings</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

<span data-ttu-id="522ab-141">Após o upload da página, o Teams atualiza os espaços reservados de sequência de caracteres de consulta com valores relevantes.</span><span class="sxs-lookup"><span data-stu-id="522ab-141">After your page uploads, the Teams updates the query string placeholders with relevant values.</span></span> <span data-ttu-id="522ab-142">Inclua lógica na página de configuração para recuperar e usar esses valores.</span><span class="sxs-lookup"><span data-stu-id="522ab-142">Include logic in the configuration page to retrieve and use those values.</span></span> <span data-ttu-id="522ab-143">Para obter mais informações sobre como trabalhar com strings de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) no MDN Web Docs. O exemplo a seguir descreve a maneira de extrair um valor da `configurationUrl` propriedade:</span><span class="sxs-lookup"><span data-stu-id="522ab-143">For more information on working with URL query strings, see [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. The following example describes the way to extract a value from the `configurationUrl` property:</span></span>

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a><span data-ttu-id="522ab-144">Use a `getContext()` função para recuperar o contexto</span><span class="sxs-lookup"><span data-stu-id="522ab-144">Use the `getContext()` function to retrieve context</span></span>

<span data-ttu-id="522ab-145">A `microsoftTeams.getContext((context) => {})` função recupera a interface [Contexto](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) quando invocada.</span><span class="sxs-lookup"><span data-stu-id="522ab-145">The `microsoftTeams.getContext((context) => {})` function retrieves the [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) when invoked.</span></span> <span data-ttu-id="522ab-146">Adicione esta função à página de configuração para recuperar valores de contexto:</span><span class="sxs-lookup"><span data-stu-id="522ab-146">Add this function to the configuration page to retrieve context values:</span></span>

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

## <a name="context-and-authentication"></a><span data-ttu-id="522ab-147">Contexto e autenticação</span><span class="sxs-lookup"><span data-stu-id="522ab-147">Context and authentication</span></span>

 <span data-ttu-id="522ab-148">Autentique antes de permitir que um usuário configure seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="522ab-148">Authenticate before allowing a user to configure your app.</span></span> <span data-ttu-id="522ab-149">Caso contrário, seu conteúdo pode incluir fontes que têm seus protocolos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="522ab-149">Otherwise, your content might include sources that have their authentication protocols.</span></span> <span data-ttu-id="522ab-150">Para obter mais informações, consulte [Autenticar um usuário em uma guia Microsoft Teams](~/tabs/how-to/authentication/auth-flow-tab.md). Use informações de contexto para construir as solicitações de autenticação e as URLs da página de autorização.</span><span class="sxs-lookup"><span data-stu-id="522ab-150">For more information, see [Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Use context information to construct the authentication requests and authorization page URLs.</span></span>
<span data-ttu-id="522ab-151">Certifique-se de que todos os domínios usados em suas páginas de guia estejam listados no `manifest.json` e `validDomains` no array.</span><span class="sxs-lookup"><span data-stu-id="522ab-151">Ensure that all domains used in your tab pages are listed in the `manifest.json` and `validDomains` array.</span></span>

## <a name="modify-or-remove-a-tab"></a><span data-ttu-id="522ab-152">Modifique ou remova uma guia</span><span class="sxs-lookup"><span data-stu-id="522ab-152">Modify or remove a tab</span></span>

<span data-ttu-id="522ab-153">Opções de remoção suportadas refinam ainda mais a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="522ab-153">Supported removal options further refine the user experience.</span></span> <span data-ttu-id="522ab-154">Defina a propriedade do manifesto `canUpdateConfiguration` para , que permite que os usuários `true` modifiquem, reconfigurem ou renomeiem uma guia de grupo ou canal. Além disso, indique o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no aplicativo e definindo um valor para a `removeUrl` propriedade na  `setSettings()` configuração.</span><span class="sxs-lookup"><span data-stu-id="522ab-154">Set your manifest's `canUpdateConfiguration` property to `true`, that enables the users to modify, reconfigure, or rename a group or channel tab. Also, indicate what happens to the content when a tab is removed, by including a removal options page in the app and setting a value for the `removeUrl` property in the  `setSettings()` configuration.</span></span> <span data-ttu-id="522ab-155">O usuário pode desinstalar as guias Pessoais, mas não pode modificá-las.</span><span class="sxs-lookup"><span data-stu-id="522ab-155">The user can uninstall the Personal tabs but cannot modify them.</span></span> <span data-ttu-id="522ab-156">Para obter mais informações, consulte [Criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md).</span><span class="sxs-lookup"><span data-stu-id="522ab-156">For more information, see [Create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span></span>

<span data-ttu-id="522ab-157">Microsoft Teams configuração setSettings() para a página de remoção:</span><span class="sxs-lookup"><span data-stu-id="522ab-157">Microsoft Teams setSettings() configuration for removal page:</span></span>

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

## <a name="mobile-clients"></a><span data-ttu-id="522ab-158">Clientes móveis</span><span class="sxs-lookup"><span data-stu-id="522ab-158">Mobile clients</span></span>

<span data-ttu-id="522ab-159">Se você optar por ter seu canal ou aba de grupo aparecendo na Teams clientes móveis, a `setSettings()` configuração deve ter um valor para o `websiteUrl` imóvel.</span><span class="sxs-lookup"><span data-stu-id="522ab-159">If you choose to have your channel or group tab appear on the Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property.</span></span> <span data-ttu-id="522ab-160">Para obter mais informações, consulte [orientação para guias no celular](~/tabs/design/tabs-mobile.md).</span><span class="sxs-lookup"><span data-stu-id="522ab-160">For more information, see [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md).</span></span>
