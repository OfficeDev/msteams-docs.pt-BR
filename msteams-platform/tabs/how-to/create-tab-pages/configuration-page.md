---
title: Criar uma página de configuração
author: laujan
description: ''
keywords: guias do teams com o canal de grupo configurável
ms.topic: conceptualF
ms.author: laujan
ms.openlocfilehash: c7b6b636a342c650667a1131e7899908744beedf
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672457"
---
# <a name="create-a-configuration-page"></a><span data-ttu-id="91b1c-103">Criar uma página de configuração</span><span class="sxs-lookup"><span data-stu-id="91b1c-103">Create a configuration page</span></span>

<span data-ttu-id="91b1c-104">Uma página de configuração é um tipo especial de [página de conteúdo](content-page.md) que permite que os usuários configurem alguns aspectos de seu aplicativo do teams.</span><span class="sxs-lookup"><span data-stu-id="91b1c-104">A configuration page is a special type of [content page](content-page.md) that allows your users to configure some aspect of your Teams app.</span></span> <span data-ttu-id="91b1c-105">Normalmente, são usados como parte de:</span><span class="sxs-lookup"><span data-stu-id="91b1c-105">Typically these are used as part of:</span></span>

* <span data-ttu-id="91b1c-106">Guia chat de grupo ou canal-a página de configuração permite coletar informações de seus usuários e definir a `contentUrl` página de conteúdo a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="91b1c-106">A channel or group chat tab - The configuration page allows you to collect information from your users and set the `contentUrl` of the content page to display.</span></span>
* <span data-ttu-id="91b1c-107">Uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="91b1c-107">A [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md)</span></span>
* <span data-ttu-id="91b1c-108">Um [conector do Office 365](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span><span class="sxs-lookup"><span data-stu-id="91b1c-108">A [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)</span></span>

## <a name="configuring-a-channel-or-group-chat-tab"></a><span data-ttu-id="91b1c-109">Configurando uma guia chat de grupo ou canal</span><span class="sxs-lookup"><span data-stu-id="91b1c-109">Configuring a channel or group chat tab</span></span>

<span data-ttu-id="91b1c-110">Uma página de configuração informa a página de conteúdo como ela deve renderizar.</span><span class="sxs-lookup"><span data-stu-id="91b1c-110">A configuration page informs the content page how it should render.</span></span> <span data-ttu-id="91b1c-111">O aplicativo deve fazer referência ao SDK e à chamada `microsoft.initialize()`do [cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) .</span><span class="sxs-lookup"><span data-stu-id="91b1c-111">Your application must reference the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) and call `microsoft.initialize()`.</span></span> <span data-ttu-id="91b1c-112">Além disso, suas URLs devem ser pontos de extremidade HTTPS seguros e disponíveis na nuvem.</span><span class="sxs-lookup"><span data-stu-id="91b1c-112">Additionally, your URLs must be secure HTTPS endpoints and available from the cloud.</span></span> <span data-ttu-id="91b1c-113">Veja a seguir um exemplo de página de configuração.</span><span class="sxs-lookup"><span data-stu-id="91b1c-113">Below is a configuration page example.</span></span>

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

<span data-ttu-id="91b1c-114">Aqui, os usuários são apresentados com dois botões de opção, **selecione cinza** ou **selecione vermelho** para exibir o conteúdo da guia com um ícone vermelho ou cinza.</span><span class="sxs-lookup"><span data-stu-id="91b1c-114">Here, the user is presented with two option buttons, **Select Gray** or **Select Red** to display the tab content with either a red or gray icon.</span></span> <span data-ttu-id="91b1c-115">A escolha do botão relativo `saveGray()` dispara `saveRed()` ou invoca o seguinte:</span><span class="sxs-lookup"><span data-stu-id="91b1c-115">Choosing the relative button fires `saveGray()` or `saveRed()` and invokes the following:</span></span>

1. <span data-ttu-id="91b1c-116">O `settings.setValidityState(true)` é definido como true.</span><span class="sxs-lookup"><span data-stu-id="91b1c-116">The `settings.setValidityState(true)` is set to true.</span></span>
1. <span data-ttu-id="91b1c-117">O `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos é disparado.</span><span class="sxs-lookup"><span data-stu-id="91b1c-117">The `microsoftTeams.settings.registerOnSaveHandler()` event handler is triggered.</span></span>
1. <span data-ttu-id="91b1c-118">O botão **salvar** na página de configuração do aplicativo, carregado no Microsoft Teams, está habilitado.</span><span class="sxs-lookup"><span data-stu-id="91b1c-118">The **Save** button on the app's configuration page, uploaded in Teams, is enabled.</span></span>

<span data-ttu-id="91b1c-119">Esse código permite que as equipes saibam que os requisitos de configuração foram satisfeitos e a instalação pode continuar.</span><span class="sxs-lookup"><span data-stu-id="91b1c-119">This code lets Teams know that the configuration requirements have been satisfied and the installation can proceed.</span></span> <span data-ttu-id="91b1c-120">Ao **salvar**, os parâmetros de `settings.setSettings()` são definidos, conforme definido pela `Settings` interface, para a instância atual (consulte interface de [configurações](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest) ).</span><span class="sxs-lookup"><span data-stu-id="91b1c-120">On **Save**, the parameters of `settings.setSettings()` are set, as defined by the `Settings` interface, for the current instance (See [Settings interface](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest) ).</span></span> <span data-ttu-id="91b1c-121">Por fim `saveEvent.notifySuccess()` , é chamado para indicar que a URL de conteúdo foi resolvida com êxito.</span><span class="sxs-lookup"><span data-stu-id="91b1c-121">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

>[!NOTE]
>
>* <span data-ttu-id="91b1c-122">Se um manipulador de gravação foi registrado `microsoftTeams.settings.registerOnSaveHandler()`usando o, o retorno `saveEvent.notifySuccess()` de `saveEvent.notifyFailure()` chamada deve invocar ou indicar o resultado da configuração.</span><span class="sxs-lookup"><span data-stu-id="91b1c-122">If a save handler was registered using `microsoftTeams.settings.registerOnSaveHandler()`, the callback must invoke `saveEvent.notifySuccess()` or `saveEvent.notifyFailure()` to indicate the outcome of the configuration.</span></span>
>* <span data-ttu-id="91b1c-123">Se nenhum manipulador de salvamento foi registrado, `saveEvent.notifySuccess()` a chamada é automaticamente feita imediatamente após o usuário selecionando o botão **salvar** .</span><span class="sxs-lookup"><span data-stu-id="91b1c-123">If no save handler was registered, the `saveEvent.notifySuccess()` call is automatically made immediately upon the user selecting the **Save** button.</span></span>

### <a name="get-context-data-for-your-tab-settings"></a><span data-ttu-id="91b1c-124">Obter dados de contexto para suas configurações de guia</span><span class="sxs-lookup"><span data-stu-id="91b1c-124">Get context data for your tab settings</span></span>

<span data-ttu-id="91b1c-125">Sua guia pode exigir informações contextuais para exibir conteúdo relevante.</span><span class="sxs-lookup"><span data-stu-id="91b1c-125">Your tab might require contextual information to display relevant content.</span></span> <span data-ttu-id="91b1c-126">As informações contextuais podem aprimorar ainda mais o apelo da guia ao fornecer uma experiência de usuário mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="91b1c-126">Contextual information can further enhance your tab's appeal by providing a more customized user experience.</span></span>

<span data-ttu-id="91b1c-127">A [interface de contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) do Microsoft Teams define as propriedades que podem ser usadas para sua configuração de guia.</span><span class="sxs-lookup"><span data-stu-id="91b1c-127">The Teams [Context interface](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) defines the properties that can be used for your tab configuration.</span></span> <span data-ttu-id="91b1c-128">Você pode coletar os valores de variáveis de dados de contexto de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="91b1c-128">You can collect the values of context data variables in two ways:</span></span>

1. <span data-ttu-id="91b1c-129">Insira espaços reservados para cadeia de caracteres de consulta de `configurationURL`URL no seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="91b1c-129">Insert URL query string placeholders in your manifest's `configurationURL`.</span></span>

1. <span data-ttu-id="91b1c-130">Use o método [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) `microsoftTeams.getContext((context) =>{}` do teams.</span><span class="sxs-lookup"><span data-stu-id="91b1c-130">Use the [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) `microsoftTeams.getContext((context) =>{}` method.</span></span>

#### <a name="insert-placeholders-in-the-configurationurl"></a><span data-ttu-id="91b1c-131">Inserir espaços reservados no`configurationURL`</span><span class="sxs-lookup"><span data-stu-id="91b1c-131">Insert placeholders in the `configurationURL`</span></span>

<span data-ttu-id="91b1c-132">Os espaços reservados de interface de contexto podem ser adicionados `configurationUrl`à sua base.</span><span class="sxs-lookup"><span data-stu-id="91b1c-132">Context interface placeholders can be added to your base `configurationUrl`.</span></span> <span data-ttu-id="91b1c-133">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91b1c-133">For example:</span></span>

##### <a name="base-url"></a><span data-ttu-id="91b1c-134">URL base</span><span class="sxs-lookup"><span data-stu-id="91b1c-134">Base Url</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a><span data-ttu-id="91b1c-135">URL base com cadeias de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="91b1c-135">Base URL with query strings</span></span>

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

<span data-ttu-id="91b1c-136">Depois que a página for carregada, os espaços reservados de cadeia de caracteres de consulta serão atualizados pelo Teams com os valores relevantes.</span><span class="sxs-lookup"><span data-stu-id="91b1c-136">After your page has uploaded, the query string placeholders will be updated by Teams with the relevant values.</span></span> <span data-ttu-id="91b1c-137">Você pode incluir lógica na página de configuração para recuperar e usar esses valores.</span><span class="sxs-lookup"><span data-stu-id="91b1c-137">You can include logic in your configuration page to retrieve and use those values.</span></span> <span data-ttu-id="91b1c-138">Para obter mais informações sobre como trabalhar com cadeias de caracteres de consulta de URL, consulte [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web docs. Veja um exemplo de como extrair um valor da propriedade acima `configurationURL` :</span><span class="sxs-lookup"><span data-stu-id="91b1c-138">For more information on working with URL query strings see [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN web docs. Here is an example of how to extract a value from the above `configurationURL` property:</span></span>

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a><span data-ttu-id="91b1c-139">Usar a `getContext()` função para recuperar o contexto</span><span class="sxs-lookup"><span data-stu-id="91b1c-139">Use the `getContext()` function to retrieve context</span></span>

<span data-ttu-id="91b1c-140">Quando invocado, `microsoftTeams.getContext((context) => {})` a função recupera a [interface de contexto](/javascript/api/@microsoft/teams-js//microsoftteams.context?view=msteams-client-js-latest).</span><span class="sxs-lookup"><span data-stu-id="91b1c-140">When invoked, the `microsoftTeams.getContext((context) => {})` function retrieves the [Context interface](/javascript/api/@microsoft/teams-js//microsoftteams.context?view=msteams-client-js-latest).</span></span> <span data-ttu-id="91b1c-141">Você pode adicionar essa função à página de configuração para recuperar os valores de contexto:</span><span class="sxs-lookup"><span data-stu-id="91b1c-141">You can add this function to your configuration page to retrieve context values:</span></span>

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

## <a name="context-and-authentication"></a><span data-ttu-id="91b1c-142">Contexto e autenticação</span><span class="sxs-lookup"><span data-stu-id="91b1c-142">Context and Authentication</span></span>

<span data-ttu-id="91b1c-143">Você pode exigir autenticação antes de permitir que um usuário configure seu aplicativo ou seu conteúdo pode incluir fontes que têm seus próprios protocolos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="91b1c-143">You might require authentication before allowing a user to configure your app or your content might include sources that have their own authentication protocols.</span></span> <span data-ttu-id="91b1c-144">Consulte [autenticar um usuário em uma guia do Microsoft Teams](~/tabs/how-to/authentication/auth-flow-tab.md) as informações de contexto podem ser usadas para ajudar a construir solicitações de autenticação e URLs de página de autorização.</span><span class="sxs-lookup"><span data-stu-id="91b1c-144">See [Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md) Context information can be used to help construct authentication requests and authorization page URLs.</span></span>
<span data-ttu-id="91b1c-145">Certifique-se de que todos os domínios usados nas páginas da guia estão `manifest.json` `validDomains` listados na matriz.</span><span class="sxs-lookup"><span data-stu-id="91b1c-145">Make sure that all domains used in your tab pages are listed in the `manifest.json` `validDomains` array.</span></span>

## <a name="modify-or-remove-a-tab"></a><span data-ttu-id="91b1c-146">Modificar ou remover uma guia</span><span class="sxs-lookup"><span data-stu-id="91b1c-146">Modify or remove a tab</span></span>

<span data-ttu-id="91b1c-147">As opções de remoção suportadas podem aprimorar ainda mais a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="91b1c-147">Supported removal options can further refine the user experience.</span></span> <span data-ttu-id="91b1c-148">Você pode permitir que os usuários modifiquem, reconfigurem ou renomeie uma guia de grupo/ `canUpdateConfiguration` canal, `true`definindo a propriedade do manifesto como.</span><span class="sxs-lookup"><span data-stu-id="91b1c-148">You can enable users to modify, reconfigure, or rename a group/channel tab by setting your manifest's `canUpdateConfiguration` property to `true`.</span></span>  <span data-ttu-id="91b1c-149">Além disso, você pode designar o que acontece com o conteúdo quando uma guia é removida, incluindo uma página de opções de remoção no seu aplicativo e definir `removeUrl` um valor para `setSettings()` a propriedade na configuração (veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="91b1c-149">In addition, you can designate what happens to the content when a tab is removed by including a removal options page in your app and setting a value for the `removeUrl` property in the  `setSettings()` configuration (see below).</span></span> <span data-ttu-id="91b1c-150">As guias pessoais não podem ser modificadas, mas podem ser desinstaladas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="91b1c-150">Personal tabs can't be modified but can be uninstalled by the user.</span></span> <span data-ttu-id="91b1c-151">Para obter mais informações, consulte [criar uma página de remoção para sua guia](~/tabs/how-to/create-tab-pages/removal-page.md).</span><span class="sxs-lookup"><span data-stu-id="91b1c-151">For more information, see [Create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).</span></span>

## <a name="mobile-clients"></a><span data-ttu-id="91b1c-152">Clientes móveis</span><span class="sxs-lookup"><span data-stu-id="91b1c-152">Mobile clients</span></span>

<span data-ttu-id="91b1c-153">Se você optar por ter a guia canal/grupo exibida em clientes móveis do Microsoft Teams, a `setSettings()` configuração deverá ter um `websiteUrl` valor para a propriedade (veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="91b1c-153">If you choose to have your channel/group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property (see below).</span></span> <span data-ttu-id="91b1c-154">O suporte completo para guias em clientes móveis será lançado em breve.</span><span class="sxs-lookup"><span data-stu-id="91b1c-154">Full support for tabs on mobile clients will be released soon.</span></span> <span data-ttu-id="91b1c-155">Para se preparar para a atualização, siga as [orientações para guias em celular](~/tabs/design/tabs-mobile.md) ao criar suas guias.</span><span class="sxs-lookup"><span data-stu-id="91b1c-155">To prepare for the update, you should follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span>

<span data-ttu-id="91b1c-156">Configuração do Microsoft Teams SetSettings () para a página de remoção e/ou clientes móveis:</span><span class="sxs-lookup"><span data-stu-id="91b1c-156">Microsoft Teams setSettings() configuration for removal page and/or mobile clients:</span></span>

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "URL REQUIRED FOR MOBILE CLIENTS",
    removeUrl: "ADD REMOVAL PAGE URL HERE"
});
```
