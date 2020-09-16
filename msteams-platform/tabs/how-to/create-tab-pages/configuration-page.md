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
# <a name="create-a-configuration-page"></a><span data-ttu-id="a5e7b-104">Criar uma página de configuração</span><span class="sxs-lookup"><span data-stu-id="a5e7b-104">Create a configuration page</span></span>

<span data-ttu-id="a5e7b-105">Uma página de configuração é um tipo especial de [página de conteúdo](content-page.md) que permite que os usuários configurem alguns aspectos de seu aplicativo do teams.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-105">A configuration page is a special type of [content page](content-page.md) that allows your users to configure some aspect of your Teams app.</span></span> <span data-ttu-id="a5e7b-106">Normalmente, são usados como parte de:</span><span class="sxs-lookup"><span data-stu-id="a5e7b-106">Typically these are used as part of:</span></span>

* <span data-ttu-id="a5e7b-107">Guia chat de grupo ou canal-a página de configuração permite coletar informações de seus usuários e definir a `contentUrl` página de conteúdo a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-107">A channel or group chat tab - The configuration page allows you to collect information from your users and set the `contentUrl` of the content page to display.</span></span>
* <span data-ttu-id="a5e7b-108">Uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="a5e7b-108">A [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md)</span></span>
* <span data-ttu-id="a5e7b-109">Um [conector do Office 365](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span><span class="sxs-lookup"><span data-stu-id="a5e7b-109">A [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span></span>

## <a name="configuring-a-channel-or-group-chat-tab"></a><span data-ttu-id="a5e7b-110">Configurando uma guia chat de grupo ou canal</span><span class="sxs-lookup"><span data-stu-id="a5e7b-110">Configuring a channel or group chat tab</span></span>

<span data-ttu-id="a5e7b-111">Uma página de configuração informa a página de conteúdo como ela deve renderizar.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-111">A configuration page informs the content page how it should render.</span></span> <span data-ttu-id="a5e7b-112">O aplicativo deve fazer referência ao SDK e à chamada do [cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) `microsoft.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="a5e7b-112">Your application must reference the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) and call `microsoft.initialize()`.</span></span> <span data-ttu-id="a5e7b-113">Além disso, suas URLs devem ser pontos de extremidade HTTPS seguros e disponíveis na nuvem.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-113">Additionally, your URLs must be secure HTTPS endpoints and available from the cloud.</span></span> <span data-ttu-id="a5e7b-114">Veja a seguir um exemplo de página de configuração.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-114">Below is a configuration page example.</span></span>

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

<span data-ttu-id="a5e7b-115">Aqui, os usuários são apresentados com dois botões de opção, **selecione cinza** ou **selecione vermelho** para exibir o conteúdo da guia com um ícone vermelho ou cinza.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-115">Here, the user is presented with two option buttons, **Select Gray** or **Select Red** to display the tab content with either a red or gray icon.</span></span> <span data-ttu-id="a5e7b-116">A escolha do botão relativo dispara `saveGray()` ou `saveRed()` invoca o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a5e7b-116">Choosing the relative button fires `saveGray()` or `saveRed()` and invokes the following:</span></span>

1. <span data-ttu-id="a5e7b-117">O `settings.setValidityState(true)` é definido como true.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-117">The `settings.setValidityState(true)` is set to true.</span></span>
1. <span data-ttu-id="a5e7b-118">O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é disparado.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-118">The `microsoftTeams.settings.registerOnSaveHandler()` event handler is triggered.</span></span>
1. <span data-ttu-id="a5e7b-119">O botão **salvar** na página de configuração do aplicativo, carregado no Microsoft Teams, está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-119">The **Save** button on the app's configuration page, uploaded in Teams, is enabled.</span></span>

<span data-ttu-id="a5e7b-120">Esse código permite que as equipes saibam que os requisitos de configuração foram satisfeitos e a instalação pode continuar.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-120">This code lets Teams know that the configuration requirements have been satisfied and the installation can proceed.</span></span> <span data-ttu-id="a5e7b-121">Ao **salvar**, os parâmetros de `settings.setSettings()` são definidos, conforme definido pela `Settings` interface, para a instância atual (consulte [interface de configurações](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest) ).</span><span class="sxs-lookup"><span data-stu-id="a5e7b-121">On **Save**, the parameters of `settings.setSettings()` are set, as defined by the `Settings` interface, for the current instance (See [Settings interface](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest) ).</span></span> <span data-ttu-id="a5e7b-122">Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-122">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

>[!NOTE]
>
>* <span data-ttu-id="a5e7b-123">Se um manipulador de gravação foi registrado usando `microsoftTeams.settings.registerOnSaveHandler()` o, o retorno de chamada deve invocar `saveEvent.notifySuccess()` ou `saveEvent.notifyFailure()` indicar o resultado da configuração.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-123">If a save handler was registered using `microsoftTeams.settings.registerOnSaveHandler()`, the callback must invoke `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to indicate the outcome of the configuration.</span></span>
>* <span data-ttu-id="a5e7b-124">Se nenhum manipulador de salvamento foi registrado, a `saveEvent.notifySuccess()` chamada é automaticamente feita imediatamente após o usuário selecionando o botão **salvar** .</span><span class="sxs-lookup"><span data-stu-id="a5e7b-124">If no save handler was registered, the `saveEvent.notifySuccess()` call is automatically made immediately upon the user selecting the **Save** button.</span></span>

### <a name="get-context-data-for-your-tab-settings"></a><span data-ttu-id="a5e7b-125">Obter dados de contexto para suas configurações de guia</span><span class="sxs-lookup"><span data-stu-id="a5e7b-125">Get context data for your tab settings</span></span>

<span data-ttu-id="a5e7b-126">Sua guia pode exigir informações contextuais para exibir conteúdo relevante.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-126">Your tab might require contextual information to display relevant content.</span></span> <span data-ttu-id="a5e7b-127">As informações contextuais podem aprimorar ainda mais o apelo da guia ao fornecer uma experiência de usuário mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-127">Contextual information can further enhance your tab's appeal by providing a more customized user experience.</span></span>

<span data-ttu-id="a5e7b-128">A [interface de contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) do Microsoft Teams define as propriedades que podem ser usadas para sua configuração de guia.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-128">The Teams [Context interface](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) defines the properties that can be used for your tab configuration.</span></span> <span data-ttu-id="a5e7b-129">Você pode coletar os valores de variáveis de dados de contexto de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="a5e7b-129">You can collect the values of context data variables in two ways:</span></span>

1. <span data-ttu-id="a5e7b-130">Insira espaços reservados para cadeia de caracteres de consulta de URL no seu manifesto `configurationURL` .</span><span class="sxs-lookup"><span data-stu-id="a5e7b-130">Insert URL query string placeholders in your manifest's `configurationURL`.</span></span>

1. <span data-ttu-id="a5e7b-131">Use o método [SDK do teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) `microsoftTeams.getContext((context) =>{}` .</span><span class="sxs-lookup"><span data-stu-id="a5e7b-131">Use the [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) `microsoftTeams.getContext((context) =>{}` method.</span></span>

#### <a name="insert-placeholders-in-the-configurationurl"></a><span data-ttu-id="a5e7b-132">Inserir espaços reservados no `configurationURL`</span><span class="sxs-lookup"><span data-stu-id="a5e7b-132">Insert placeholders in the `configurationURL`</span></span>

<span data-ttu-id="a5e7b-133">Os espaços reservados de interface de contexto podem ser adicionados à sua base `configurationUrl` .</span><span class="sxs-lookup"><span data-stu-id="a5e7b-133">Context interface placeholders can be added to your base `configurationUrl`.</span></span> <span data-ttu-id="a5e7b-134">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a5e7b-134">For example:</span></span>

##### <a name="base-url"></a><span data-ttu-id="a5e7b-135">URL base</span><span class="sxs-lookup"><span data-stu-id="a5e7b-135">Base Url</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a><span data-ttu-id="a5e7b-136">URL base com cadeias de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="a5e7b-136">Base URL with query strings</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

<span data-ttu-id="a5e7b-137">Depois que a página for carregada, os espaços reservados de cadeia de caracteres de consulta serão atualizados pelo Teams com os valores relevantes.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-137">After your page has uploaded, the query string placeholders will be updated by Teams with the relevant values.</span></span> <span data-ttu-id="a5e7b-138">Você pode incluir lógica na página de configuração para recuperar e usar esses valores.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-138">You can include logic in your configuration page to retrieve and use those values.</span></span> <span data-ttu-id="a5e7b-139">Para obter mais informações sobre como trabalhar com cadeias de caracteres de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web docs. Veja um exemplo de como extrair um valor da `configurationURL` Propriedade acima:</span><span class="sxs-lookup"><span data-stu-id="a5e7b-139">For more information on working with URL query strings see [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN web docs. Here is an example of how to extract a value from the above `configurationURL` property:</span></span>

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a><span data-ttu-id="a5e7b-140">Usar a `getContext()` função para recuperar o contexto</span><span class="sxs-lookup"><span data-stu-id="a5e7b-140">Use the `getContext()` function to retrieve context</span></span>

<span data-ttu-id="a5e7b-141">Quando invocado, a `microsoftTeams.getContext((context) => {})` função recupera a [interface de contexto](/javascript/api/@microsoft/teams-js//microsoftteams.context?view=msteams-client-js-latest).</span><span class="sxs-lookup"><span data-stu-id="a5e7b-141">When invoked, the `microsoftTeams.getContext((context) => {})` function retrieves the [Context interface](/javascript/api/@microsoft/teams-js//microsoftteams.context?view=msteams-client-js-latest).</span></span> <span data-ttu-id="a5e7b-142">Você pode adicionar essa função à página de configuração para recuperar os valores de contexto:</span><span class="sxs-lookup"><span data-stu-id="a5e7b-142">You can add this function to your configuration page to retrieve context values:</span></span>

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

## <a name="context-and-authentication"></a><span data-ttu-id="a5e7b-143">Contexto e autenticação</span><span class="sxs-lookup"><span data-stu-id="a5e7b-143">Context and Authentication</span></span>

<span data-ttu-id="a5e7b-144">Você pode exigir autenticação antes de permitir que um usuário configure seu aplicativo ou seu conteúdo pode incluir fontes que têm seus próprios protocolos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-144">You might require authentication before allowing a user to configure your app or your content might include sources that have their own authentication protocols.</span></span> <span data-ttu-id="a5e7b-145">Consulte [autenticar um usuário em uma guia do Microsoft Teams](~/tabs/how-to/authentication/auth-flow-tab.md) as informações de contexto podem ser usadas para ajudar a construir solicitações de autenticação e URLs de página de autorização.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-145">See [Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md) Context information can be used to help construct authentication requests and authorization page URLs.</span></span>
<span data-ttu-id="a5e7b-146">Certifique-se de que todos os domínios usados nas páginas da guia estão listados na `manifest.json` `validDomains` matriz.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-146">Make sure that all domains used in your tab pages are listed in the `manifest.json` `validDomains` array.</span></span>

## <a name="modify-or-remove-a-tab"></a><span data-ttu-id="a5e7b-147">Modificar ou remover uma guia</span><span class="sxs-lookup"><span data-stu-id="a5e7b-147">Modify or remove a tab</span></span>

<span data-ttu-id="a5e7b-148">As opções de remoção suportadas podem aprimorar ainda mais a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-148">Supported removal options can further refine the user experience.</span></span> <span data-ttu-id="a5e7b-149">Você pode permitir que os usuários modifiquem, reconfigurem ou renomeie uma guia de grupo/canal, definindo a propriedade do manifesto `canUpdateConfiguration` como `true` .</span><span class="sxs-lookup"><span data-stu-id="a5e7b-149">You can enable users to modify, reconfigure, or rename a group/channel tab by setting your manifest's `canUpdateConfiguration` property to `true`.</span></span>  <span data-ttu-id="a5e7b-150">Além disso, você pode designar o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no seu aplicativo e definir um valor para a `removeUrl` Propriedade na  `setSettings()` configuração (veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="a5e7b-150">In addition, you can designate what happens to the content when a tab is removed by including a removal options page in your app and setting a value for the `removeUrl` property in the  `setSettings()` configuration (see below).</span></span> <span data-ttu-id="a5e7b-151">As guias pessoais não podem ser modificadas, mas podem ser desinstaladas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-151">Personal tabs can't be modified but can be uninstalled by the user.</span></span> <span data-ttu-id="a5e7b-152">Para obter mais informações, consulte [criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md).</span><span class="sxs-lookup"><span data-stu-id="a5e7b-152">For more information, see [Create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span></span>

## <a name="mobile-clients"></a><span data-ttu-id="a5e7b-153">Clientes móveis</span><span class="sxs-lookup"><span data-stu-id="a5e7b-153">Mobile clients</span></span>

<span data-ttu-id="a5e7b-154">Se você optar por ter a guia canal/grupo exibida em clientes móveis do Microsoft Teams, a `setSettings()` configuração deverá ter um valor para a `websiteUrl` Propriedade (veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="a5e7b-154">If you choose to have your channel/group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property (see below).</span></span> <span data-ttu-id="a5e7b-155">O suporte completo para guias em clientes móveis será lançado em breve.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-155">Full support for tabs on mobile clients will be released soon.</span></span> <span data-ttu-id="a5e7b-156">Para se preparar para a atualização, siga as [orientações para guias em celular](~/tabs/design/tabs-mobile.md) ao criar suas guias.</span><span class="sxs-lookup"><span data-stu-id="a5e7b-156">To prepare for the update, you should follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span>

<span data-ttu-id="a5e7b-157">Configuração do Microsoft Teams SetSettings () para a página de remoção e/ou clientes móveis:</span><span class="sxs-lookup"><span data-stu-id="a5e7b-157">Microsoft Teams setSettings() configuration for removal page and/or mobile clients:</span></span>

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "URL REQUIRED FOR MOBILE CLIENTS",
    removeUrl: "ADD REMOVAL PAGE URL HERE"
});
```
