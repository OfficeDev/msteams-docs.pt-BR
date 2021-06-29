---
title: Criar Conectores do Office 365
author: laujan
description: Descreve como começar a usar Office 365 conectores no Microsoft Teams
keywords: conector do o365 no teams
localization_priority: Normal
ms.topic: conceptual
ms.date: 06/16/2021
ms.openlocfilehash: 28a2b35e868baf34e35a11a00e10b30b0f09c236
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179752"
---
# <a name="create-office-365-connectors"></a><span data-ttu-id="2be12-104">Criar Conectores do Office 365</span><span class="sxs-lookup"><span data-stu-id="2be12-104">Create Office 365 Connectors</span></span>

<span data-ttu-id="2be12-105">Com Microsoft Teams aplicativos, você pode adicionar seu conector de Office 365 existente ou criar um novo dentro Teams.</span><span class="sxs-lookup"><span data-stu-id="2be12-105">With Microsoft Teams apps, you can add your existing Office 365 Connector or build a new one within Teams.</span></span> <span data-ttu-id="2be12-106">Para obter mais informações, consulte [build your own connector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector).</span><span class="sxs-lookup"><span data-stu-id="2be12-106">For more information, see [build your own connector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector).</span></span>

## <a name="add-a-connector-to-teams-app"></a><span data-ttu-id="2be12-107">Adicionar um conector ao Teams app</span><span class="sxs-lookup"><span data-stu-id="2be12-107">Add a connector to Teams app</span></span>

<span data-ttu-id="2be12-108">Você pode [empacotá-lo](~/concepts/build-and-test/apps-package.md) [e publicar](~/concepts/deploy-and-publish/apps-publish.md) seu conector como parte do envio do AppSource.</span><span class="sxs-lookup"><span data-stu-id="2be12-108">You can [package](~/concepts/build-and-test/apps-package.md) and [publish](~/concepts/deploy-and-publish/apps-publish.md) your connector as part of your AppSource submission.</span></span> <span data-ttu-id="2be12-109">Você pode distribuir seu conector registrado como parte do pacote Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2be12-109">You can distribute your registered connector as part of your Teams app package.</span></span> <span data-ttu-id="2be12-110">Para obter informações sobre pontos de entrada para Teams aplicativo, consulte [capabilities](~/concepts/extensibility-points.md).</span><span class="sxs-lookup"><span data-stu-id="2be12-110">For information on entry points for Teams app, see [capabilities](~/concepts/extensibility-points.md).</span></span> <span data-ttu-id="2be12-111">Você também pode fornecer o pacote aos usuários diretamente para carregar no Teams.</span><span class="sxs-lookup"><span data-stu-id="2be12-111">You can also provide the package to users directly for uploading within Teams.</span></span>

<span data-ttu-id="2be12-112">Para distribuir seu conector, você deve se registrar por [meio do Painel de Desenvolvedores conectores.](https://outlook.office.com/connectors/home/login/#/publish)</span><span class="sxs-lookup"><span data-stu-id="2be12-112">To distribute your connector, you must register through [Connectors Developer Dashboard](https://outlook.office.com/connectors/home/login/#/publish).</span></span> <span data-ttu-id="2be12-113">Quando um conector é registrado, presume-se que ele funcione em todos os produtos Office 365 que suportam aplicativos, incluindo Outlook e Teams.</span><span class="sxs-lookup"><span data-stu-id="2be12-113">When a connector is registered, it is assumed that it works in all Office 365 products that support applications, including Outlook and Teams.</span></span> <span data-ttu-id="2be12-114">Se esse não for o caso e você deve criar um conector que funcione apenas no Microsoft Teams, entre em contato: Microsoft Teams [email envios de aplicativo.](mailto:teamsubm@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="2be12-114">If that is not the case and you must create a connector that only works in Microsoft Teams, contact: [Microsoft Teams App Submissions email](mailto:teamsubm@microsoft.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2be12-115">Seu conector é registrado depois que você seleciona **Salvar** no Painel do Desenvolvedor de Conectores.</span><span class="sxs-lookup"><span data-stu-id="2be12-115">Your connector is registered after you select **Save** in the Connectors Developer Dashboard.</span></span> <span data-ttu-id="2be12-116">Se você quiser publicar seu conector no AppSource, siga as instruções em publicar seu aplicativo Microsoft Teams [no AppSource](~/concepts/deploy-and-publish/apps-publish.md).</span><span class="sxs-lookup"><span data-stu-id="2be12-116">If you want to publish your connector in AppSource, follow the instructions in [publish your Microsoft Teams app to AppSource](~/concepts/deploy-and-publish/apps-publish.md).</span></span> <span data-ttu-id="2be12-117">Se você não quiser publicar seu aplicativo no AppSource, distribua-o diretamente para a organização.</span><span class="sxs-lookup"><span data-stu-id="2be12-117">If you do not want to publish your app in AppSource, distribute it directly to the organization.</span></span> <span data-ttu-id="2be12-118">Após [a publicação de conectores para sua](#publish-connectors-for-the-organization)organização, nenhuma ação é necessária no Painel do Conector.</span><span class="sxs-lookup"><span data-stu-id="2be12-118">After [publishing connectors for your organization](#publish-connectors-for-the-organization), no further action is required on the Connector Dashboard.</span></span>

### <a name="integrate-the-configuration-experience"></a><span data-ttu-id="2be12-119">Integrar a experiência de configuração</span><span class="sxs-lookup"><span data-stu-id="2be12-119">Integrate the configuration experience</span></span>

<span data-ttu-id="2be12-120">Os usuários podem concluir toda a experiência de configuração do conector sem precisar sair do Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="2be12-120">Users can complete the entire connector configuration experience without having to leave the Teams client.</span></span> <span data-ttu-id="2be12-121">Para obter a experiência, Teams pode incorporar sua página de configuração diretamente em um iframe.</span><span class="sxs-lookup"><span data-stu-id="2be12-121">To get the experience, Teams can embed your configuration page directly within an iframe.</span></span> <span data-ttu-id="2be12-122">A sequência de operações é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="2be12-122">The sequence of operations is as follows:</span></span>

1. <span data-ttu-id="2be12-123">O usuário seleciona o conector para iniciar o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2be12-123">The user selects the connector to begin the configuration process.</span></span>
1. <span data-ttu-id="2be12-124">O usuário interage com a experiência da Web para concluir a configuração.</span><span class="sxs-lookup"><span data-stu-id="2be12-124">The user interacts with the web experience to complete the configuration.</span></span>
1. <span data-ttu-id="2be12-125">O usuário seleciona **Salvar**, que dispara um retorno de chamada no código.</span><span class="sxs-lookup"><span data-stu-id="2be12-125">The user selects **Save**, which triggers a callback in code.</span></span>

    > [!NOTE]
    > * <span data-ttu-id="2be12-126">O código pode processar o evento save recuperando as configurações de webhook.</span><span class="sxs-lookup"><span data-stu-id="2be12-126">The code can process the save event by retrieving the webhook settings.</span></span> <span data-ttu-id="2be12-127">Seu código armazena o webhook para postar eventos mais tarde.</span><span class="sxs-lookup"><span data-stu-id="2be12-127">Your code stores the webhook to post events later.</span></span>
    > * <span data-ttu-id="2be12-128">A experiência de configuração é carregada em linha Teams.</span><span class="sxs-lookup"><span data-stu-id="2be12-128">The configuration experience is loaded inline within Teams.</span></span>

<span data-ttu-id="2be12-129">Você pode reutilizar sua experiência de configuração da Web existente ou criar uma versão separada para ser hospedada especificamente em Teams.</span><span class="sxs-lookup"><span data-stu-id="2be12-129">You can reuse your existing web configuration experience or create a separate version to be hosted specifically in Teams.</span></span> <span data-ttu-id="2be12-130">Seu código deve incluir o Microsoft Teams JavaScript SDK.</span><span class="sxs-lookup"><span data-stu-id="2be12-130">Your code must include the Microsoft Teams JavaScript SDK.</span></span> <span data-ttu-id="2be12-131">Isso fornece acesso de código a APIs para executar operações comuns, como obter o usuário, canal ou contexto de equipe atual e iniciar fluxos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="2be12-131">This gives your code access to APIs to perform common operations, such as getting the current user, channel, or team context and initiate authentication flows.</span></span>

<span data-ttu-id="2be12-132">**Para integrar a experiência de configuração**</span><span class="sxs-lookup"><span data-stu-id="2be12-132">**To integrate the configuration experience**</span></span>

1. <span data-ttu-id="2be12-133">Inicializar o SDK chamando `microsoftTeams.initialize()`.</span><span class="sxs-lookup"><span data-stu-id="2be12-133">Initialize the SDK by calling `microsoftTeams.initialize()`.</span></span>
1. <span data-ttu-id="2be12-134">Chamada `microsoftTeams.settings.setValidityState(true)` para habilitar **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="2be12-134">Call `microsoftTeams.settings.setValidityState(true)` to enable **Save**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2be12-135">Você deve chamar `microsoftTeams.settings.setValidityState(true)` como uma resposta à seleção do usuário ou à atualização de campo.</span><span class="sxs-lookup"><span data-stu-id="2be12-135">You must call `microsoftTeams.settings.setValidityState(true)` as a response to user selection or field update.</span></span>

1. <span data-ttu-id="2be12-136">Registrar  `microsoftTeams.settings.registerOnSaveHandler()` manipulador de eventos, que é chamado quando o usuário seleciona **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="2be12-136">Register  `microsoftTeams.settings.registerOnSaveHandler()` event handler, which is called when the user selects **Save**.</span></span>
1. <span data-ttu-id="2be12-137">Chame `microsoftTeams.settings.setSettings()` para salvar as configurações do conector.</span><span class="sxs-lookup"><span data-stu-id="2be12-137">Call `microsoftTeams.settings.setSettings()` to save the connector settings.</span></span> <span data-ttu-id="2be12-138">As configurações salvas também serão mostradas na caixa de diálogo de configuração se o usuário tentar atualizar uma configuração existente para o conector.</span><span class="sxs-lookup"><span data-stu-id="2be12-138">The saved settings are also shown in the configuration dialog if the user tries to update an existing configuration for your connector.</span></span>
1. <span data-ttu-id="2be12-139">Chame `microsoftTeams.settings.getSettings()` para buscar propriedades de webhook, incluindo a URL.</span><span class="sxs-lookup"><span data-stu-id="2be12-139">Call `microsoftTeams.settings.getSettings()` to fetch webhook properties, including the URL.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2be12-140">Você deve chamar `microsoftTeams.settings.getSettings()` quando sua página for carregada pela primeira vez em caso de reconfiguração.</span><span class="sxs-lookup"><span data-stu-id="2be12-140">You must call `microsoftTeams.settings.getSettings()` when your page is first loaded in case of reconfiguration.</span></span>

1. <span data-ttu-id="2be12-141">Registre `microsoftTeams.settings.registerOnRemoveHandler()` o manipulador de eventos, que é chamado quando o usuário remove o conector.</span><span class="sxs-lookup"><span data-stu-id="2be12-141">Register `microsoftTeams.settings.registerOnRemoveHandler()` event handler, which is called when the user removes connector.</span></span>

<span data-ttu-id="2be12-142">Esse evento oferece ao seu serviço a oportunidade de executar qualquer ação de limpeza.</span><span class="sxs-lookup"><span data-stu-id="2be12-142">This event gives your service an opportunity to perform any cleanup actions.</span></span>

<span data-ttu-id="2be12-143">O código a seguir fornece um HTML de exemplo para criar uma página de configuração do conector sem o serviço e o suporte ao cliente:</span><span class="sxs-lookup"><span data-stu-id="2be12-143">The following code provides a sample HTML to create a connector configuration page without the customer service and support:</span></span>

```html
<h2>Send notifications when tasks are:</h2>
<div class="col-md-8">
    <section id="configSection">
        <form id="configForm">
            <input type="radio" name="notificationType" value="Create" onclick="onClick()"> Created
            <br>
            <br>
            <input type="radio" name="notificationType" value="Update" onclick="onClick()"> Updated
        </form>
    </section>
</div>

<script src="https://statics.teams.microsoft.com/sdk/v1.5.2/js/MicrosoftTeams.min.js" crossorigin="anonymous"></script>
<script src="/Scripts/jquery-1.10.2.js"></script>

<script type="text/javascript">

        function onClick() {
            microsoftTeams.settings.setValidityState(true);
        }

        microsoftTeams.initialize();
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            var radios = document.getElementsByName('notificationType');

            var eventType = '';
            if (radios[0].checked) {
                eventType = radios[0].value;
            } else {
                eventType = radios[1].value;
            }

            microsoftTeams.settings.setSettings({
                 entityId: eventType,
                contentUrl: "https://YourSite/Connector/Setup",
                removeUrl:"https://YourSite/Connector/Setup",
                 configName: eventType
                });

            microsoftTeams.settings.getSettings(function (settings) {
                // We get the Webhook URL in settings.webhookUrl which needs to be saved. 
                // This can be used later to send notification.
            });

            saveEvent.notifySuccess();
        });

        microsoftTeams.settings.registerOnRemoveHandler(function (removeEvent) {
            alert("Removed" + JSON.stringify(removeEvent));
        });

</script>
```

<span data-ttu-id="2be12-144">Para autenticar o usuário como parte [](~/tabs/how-to/authentication/auth-flow-tab.md) do carregamento de sua página, consulte fluxo de autenticação para que as guias se integrem ao entrar quando sua página for incorporada.</span><span class="sxs-lookup"><span data-stu-id="2be12-144">To authenticate the user as part of loading your page, see [authentication flow for tabs](~/tabs/how-to/authentication/auth-flow-tab.md) to integrate sign in when your page is embedded.</span></span>

> [!NOTE]
> <span data-ttu-id="2be12-145">Devido a motivos de compatibilidade entre clientes, seu código deve chamar com a URL e métodos de retorno de chamada de sucesso ou falha `microsoftTeams.authentication.registerAuthenticationHandlers()` antes de chamar `authenticate()` .</span><span class="sxs-lookup"><span data-stu-id="2be12-145">Due to cross client compatibility reasons, your code must call `microsoftTeams.authentication.registerAuthenticationHandlers()` with the URL and success or failure callback methods before calling `authenticate()`.</span></span>

#### <a name="getsettings-response-properties"></a><span data-ttu-id="2be12-146">`GetSettings` propriedades de resposta</span><span class="sxs-lookup"><span data-stu-id="2be12-146">`GetSettings` response properties</span></span>

>[!NOTE]
><span data-ttu-id="2be12-147">Os parâmetros retornados pela chamada são diferentes quando você invoca esse método de uma guia e difere daqueles `getSettings` documentados nas [configurações js](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="2be12-147">The parameters returned by the `getSettings` call are different when you invoke this method from a tab and differ from those documented in [js settings](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true).</span></span>

<span data-ttu-id="2be12-148">A tabela a seguir fornece os parâmetros e os detalhes das propriedades `GetSetting` de resposta:</span><span class="sxs-lookup"><span data-stu-id="2be12-148">The following table provides the parameters and the details of `GetSetting` response properties:</span></span>

| <span data-ttu-id="2be12-149">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2be12-149">Parameters</span></span>   | <span data-ttu-id="2be12-150">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2be12-150">Details</span></span> |
|-------------|---------|
| `entityId`       | <span data-ttu-id="2be12-151">A ID da entidade, conforme definido pelo código ao chamar `setSettings()` .</span><span class="sxs-lookup"><span data-stu-id="2be12-151">The entity ID, as set by your code when calling `setSettings()`.</span></span> |
| `configName`  | <span data-ttu-id="2be12-152">O nome da configuração, conforme definido pelo código ao chamar `setSettings()` .</span><span class="sxs-lookup"><span data-stu-id="2be12-152">The configuration name, as set by your code when calling `setSettings()`.</span></span> |
| `contentUrl` | <span data-ttu-id="2be12-153">A URL da página de configuração, conforme definido pelo código ao chamar `setSettings()` .</span><span class="sxs-lookup"><span data-stu-id="2be12-153">The URL of the configuration page, as set by your code when calling `setSettings()`.</span></span> |
| `webhookUrl` | <span data-ttu-id="2be12-154">A URL de webhook criada para o conector.</span><span class="sxs-lookup"><span data-stu-id="2be12-154">The webhook URL created for the connector.</span></span> <span data-ttu-id="2be12-155">Use a URL do webhook para POST JSON estruturado para enviar cartões para o canal.</span><span class="sxs-lookup"><span data-stu-id="2be12-155">Use the webhook URL to POST structured JSON to send cards to the channel.</span></span> <span data-ttu-id="2be12-156">O `webhookUrl` é retornado somente quando o aplicativo retorna dados com êxito.</span><span class="sxs-lookup"><span data-stu-id="2be12-156">The `webhookUrl` is returned only when the application returns data successfully.</span></span> |
| `appType` | <span data-ttu-id="2be12-157">Os valores retornados podem ser , ou correspondentes ao `mail` Office 365 `groups` `teams` Mail, Office 365 Grupos ou Microsoft Teams respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2be12-157">The values returned can be `mail`, `groups`, or `teams` corresponding to the Office 365 Mail, Office 365 Groups, or Microsoft Teams respectively.</span></span> |
| `userObjectId` | <span data-ttu-id="2be12-158">A ID exclusiva correspondente ao usuário Office 365 que iniciou a configuração do conector.</span><span class="sxs-lookup"><span data-stu-id="2be12-158">The unique ID corresponding to the Office 365 user who initiated the set up of the connector.</span></span> <span data-ttu-id="2be12-159">Ele deve ser protegido.</span><span class="sxs-lookup"><span data-stu-id="2be12-159">It must be secured.</span></span> <span data-ttu-id="2be12-160">Esse valor pode ser usado para associar o usuário Office 365, que definiu a configuração em seu serviço.</span><span class="sxs-lookup"><span data-stu-id="2be12-160">This value can be used to associate the user in Office 365, who has set up the configuration in your service.</span></span> |

#### <a name="handle-edits"></a><span data-ttu-id="2be12-161">Manipular edições</span><span class="sxs-lookup"><span data-stu-id="2be12-161">Handle edits</span></span>

<span data-ttu-id="2be12-162">Seu código deve manipular os usuários que retornam para editar uma configuração de conector existente.</span><span class="sxs-lookup"><span data-stu-id="2be12-162">Your code must handle users who return to edit an existing connector configuration.</span></span> <span data-ttu-id="2be12-163">Para fazer isso, chame `microsoftTeams.settings.setSettings()` durante a configuração inicial com os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="2be12-163">To do this, call `microsoftTeams.settings.setSettings()` during the initial configuration with the following parameters:</span></span>

- <span data-ttu-id="2be12-164">`entityId` é a ID personalizada que representa o que o usuário configurou e entendeu pelo seu serviço.</span><span class="sxs-lookup"><span data-stu-id="2be12-164">`entityId` is the custom ID that represents what the user has configured and understood by your service.</span></span>
- <span data-ttu-id="2be12-165">`configName` é um nome que o código de configuração pode recuperar.</span><span class="sxs-lookup"><span data-stu-id="2be12-165">`configName` is a name that configuration code can retrieve.</span></span>
- <span data-ttu-id="2be12-166">`contentUrl` é uma URL personalizada que é carregada quando um usuário edita uma configuração de conector existente.</span><span class="sxs-lookup"><span data-stu-id="2be12-166">`contentUrl` is a custom URL that gets loaded when a user edits an existing connector configuration.</span></span>

<span data-ttu-id="2be12-167">Essa chamada é feita como parte do manipulador de eventos save.</span><span class="sxs-lookup"><span data-stu-id="2be12-167">This call is made as part of your save event handler.</span></span> <span data-ttu-id="2be12-168">Em seguida, quando o é carregado, seu código deve chamar para preencher previamente quaisquer `contentUrl` `getSettings()` configurações ou formulários em sua interface de usuário de configuração.</span><span class="sxs-lookup"><span data-stu-id="2be12-168">Then, when the `contentUrl` is loaded, your code must call `getSettings()` to pre populate any settings or forms in your configuration user interface.</span></span>

#### <a name="handle-removals"></a><span data-ttu-id="2be12-169">Manipular remoções</span><span class="sxs-lookup"><span data-stu-id="2be12-169">Handle removals</span></span>

<span data-ttu-id="2be12-170">Você pode executar um manipulador de eventos quando o usuário remover uma configuração de conector existente.</span><span class="sxs-lookup"><span data-stu-id="2be12-170">You can execute an event handler when the user removes an existing connector configuration.</span></span> <span data-ttu-id="2be12-171">Você registra esse manipulador chamando `microsoftTeams.settings.registerOnRemoveHandler()` .</span><span class="sxs-lookup"><span data-stu-id="2be12-171">You register this handler by calling `microsoftTeams.settings.registerOnRemoveHandler()`.</span></span> <span data-ttu-id="2be12-172">Esse manipulador é usado para executar operações de limpeza, como a remoção de entradas de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="2be12-172">This handler is used to perform cleanup operations, such as removing entries from a database.</span></span>

### <a name="include-the-connector-in-your-manifest"></a><span data-ttu-id="2be12-173">Incluir o conector em seu Manifesto</span><span class="sxs-lookup"><span data-stu-id="2be12-173">Include the connector in your Manifest</span></span>

<span data-ttu-id="2be12-174">Baixe o auto gerado `Teams app manifest` do portal.</span><span class="sxs-lookup"><span data-stu-id="2be12-174">Download the auto generated `Teams app manifest` from the portal.</span></span> <span data-ttu-id="2be12-175">Execute as etapas a seguir, antes de testar ou publicar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="2be12-175">Perform the following steps, before testing or publishing the app:</span></span>

1. <span data-ttu-id="2be12-176">[Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="2be12-176">[Include two icons](../../concepts/build-and-test/apps-package.md#app-icons).</span></span>
1. <span data-ttu-id="2be12-177">Modifique `icons` a parte do manifesto para incluir os nomes de arquivo dos ícones em vez de URLs.</span><span class="sxs-lookup"><span data-stu-id="2be12-177">Modify the `icons` portion of the manifest to include the file names of the icons instead of URLs.</span></span>

<span data-ttu-id="2be12-178">O seguinte manifest.jsno arquivo contém os elementos necessários para testar e enviar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="2be12-178">The following manifest.json file contains the elements needed to test and submit the app:</span></span>

> [!NOTE]
> <span data-ttu-id="2be12-179">Substitua `id` `connectorId` e, no exemplo a seguir, pelo GUID do conector.</span><span class="sxs-lookup"><span data-stu-id="2be12-179">Replace `id` and `connectorId` in the following example with the GUID of the connector.</span></span>

#### <a name="example-of-manifestjson-with-connector"></a><span data-ttu-id="2be12-180">Exemplo de manifest.jscom conector</span><span class="sxs-lookup"><span data-stu-id="2be12-180">Example of manifest.json with connector</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "id": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
  "version": "1.0",
  "packageName": "com.sampleapp",
  "developer": {
    "name": "Publisher",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.microsoft.com",
    "termsOfUseUrl": "https://www.microsoft.com"
  },
  "description": {
    "full": "This is a small sample app we made for you! This app has samples of all capabilities Microsoft Teams supports.",
    "short": "This is a small sample app we made for you!"
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App"
  },
  "accentColor": "#FFFFFF",
  "needsIdentity": "true"
}
```

## <a name="enable-or-disable-connectors-in-teams"></a><span data-ttu-id="2be12-181">Habilitar ou desabilitar conectores Teams</span><span class="sxs-lookup"><span data-stu-id="2be12-181">Enable or disable connectors in Teams</span></span>

<span data-ttu-id="2be12-182">O módulo Exchange Online PowerShell V2 usa autenticação moderna e funciona com autenticação multifatória, chamada MFA para se conectar Exchange todos os ambientes relacionados ao PowerShell no Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2be12-182">The Exchange Online PowerShell V2 module uses modern authentication and works with multi factor authentication, called MFA for connecting to all Exchange related PowerShell environments in Microsoft 365.</span></span> <span data-ttu-id="2be12-183">Os administradores podem usar Exchange Online PowerShell para desabilitar conectores para um locatário inteiro ou uma caixa de correio de grupo específica, afetando todos os usuários nesse locatário ou caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="2be12-183">Admins can use Exchange Online PowerShell to disable connectors for an entire tenant or a specific group mailbox, affecting all users in that tenant or mailbox.</span></span> <span data-ttu-id="2be12-184">Não é possível desabilitar para alguns e não para outros.</span><span class="sxs-lookup"><span data-stu-id="2be12-184">It is not possible to disable for some and not others.</span></span> <span data-ttu-id="2be12-185">Além disso, os conectores são desabilitados por padrão para Nuvem da Comunidade Governamental, chamados GCC locatários.</span><span class="sxs-lookup"><span data-stu-id="2be12-185">Also, connectors are disabled by default for Government Community Cloud, called GCC tenants.</span></span>

<span data-ttu-id="2be12-186">A configuração de nível de locatário substitui a configuração de nível de grupo.</span><span class="sxs-lookup"><span data-stu-id="2be12-186">The tenant level setting overrides the group level setting.</span></span> <span data-ttu-id="2be12-187">Por exemplo, se um administrador habilitar conectores para o grupo e desabilitá-los no locatário, os conectores do grupo são desabilitados.</span><span class="sxs-lookup"><span data-stu-id="2be12-187">For example, if an admin enables connectors for the group and disables them on the tenant, connectors for the group is disabled.</span></span> <span data-ttu-id="2be12-188">Para habilitar um conector Teams, conecte-se [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) usando autenticação moderna com ou sem MFA.</span><span class="sxs-lookup"><span data-stu-id="2be12-188">To enable a connector in Teams, [connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) using modern authentication with or without MFA.</span></span>

### <a name="commands-to-enable-or-disable-connectors"></a><span data-ttu-id="2be12-189">Comandos para habilitar ou desabilitar conectores</span><span class="sxs-lookup"><span data-stu-id="2be12-189">Commands to enable or disable connectors</span></span>

<span data-ttu-id="2be12-190">Execute os seguintes comandos no PowerShell do Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="2be12-190">Run the following commands in Exchange Online PowerShell:</span></span>

* <span data-ttu-id="2be12-191">Para desabilitar conectores para o locatário: `Set-OrganizationConfig -ConnectorsEnabled:$false` .</span><span class="sxs-lookup"><span data-stu-id="2be12-191">To disable connectors for the tenant: `Set-OrganizationConfig -ConnectorsEnabled:$false`.</span></span>
* <span data-ttu-id="2be12-192">Para desabilitar mensagens ativas para o locatário: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false` .</span><span class="sxs-lookup"><span data-stu-id="2be12-192">To disable actionable messages for the tenant: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false`.</span></span>
* <span data-ttu-id="2be12-193">Para habilitar conectores para Teams, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="2be12-193">To enable connectors for Teams, run the following commands:</span></span>
  * `Set-OrganizationConfig -ConnectorsEnabled:$true `
  * `Set-OrganizationConfig -ConnectorsEnabledForTeams:$true`
  * `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$true`

<span data-ttu-id="2be12-194">Para obter mais informações sobre a troca de módulos do PowerShell, consulte [Set-OrganizationConfig](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="2be12-194">For more information on PowerShell module exchange, see [Set-OrganizationConfig](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true).</span></span> <span data-ttu-id="2be12-195">Para habilitar ou desabilitar Outlook conectores, [conecte aplicativos aos seus grupos em Outlook](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab?ui=en-us&rs=en-us&ad=us).</span><span class="sxs-lookup"><span data-stu-id="2be12-195">To enable or disable Outlook connectors, [connect apps to your groups in Outlook](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab?ui=en-us&rs=en-us&ad=us).</span></span>

## <a name="test-your-connector"></a><span data-ttu-id="2be12-196">Testar seu conector</span><span class="sxs-lookup"><span data-stu-id="2be12-196">Test your connector</span></span>

<span data-ttu-id="2be12-197">Para testar seu conector, carregue-o em uma equipe com qualquer outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2be12-197">To test your connector, upload it to a team with any other app.</span></span> <span data-ttu-id="2be12-198">Você pode criar um pacote .zip usando o arquivo de manifesto dos dois arquivos de ícone e conectores do Painel do Desenvolvedor, modificados conforme direcionado em Incluir o conector [em seu Manifesto](#include-the-connector-in-your-manifest).</span><span class="sxs-lookup"><span data-stu-id="2be12-198">You can create a .zip package using the manifest file from the two icon files and connectors Developer Dashboard, modified as directed in [Include the connector in your Manifest](#include-the-connector-in-your-manifest).</span></span>

<span data-ttu-id="2be12-199">Depois de carregar o aplicativo, abra a lista de conectores de qualquer canal.</span><span class="sxs-lookup"><span data-stu-id="2be12-199">After you upload the app, open the connectors list from any channel.</span></span> <span data-ttu-id="2be12-200">Role até a parte inferior para ver seu aplicativo na **seção Carregado:**</span><span class="sxs-lookup"><span data-stu-id="2be12-200">Scroll to the bottom to see your app in the **Uploaded** section:</span></span>

![Captura de tela de uma seção carregada na caixa de diálogo conector](~/assets/images/connectors/connector_dialog_uploaded.png)

> [!NOTE]
> <span data-ttu-id="2be12-202">O fluxo ocorre inteiramente dentro Microsoft Teams como uma experiência hospedada.</span><span class="sxs-lookup"><span data-stu-id="2be12-202">The flow occurs entirely within Microsoft Teams as a hosted experience.</span></span>

<span data-ttu-id="2be12-203">Para verificar se a `HttpPOST` ação está funcionando corretamente, [envie mensagens para seu conector](~/webhooks-and-connectors/how-to/connectors-using.md).</span><span class="sxs-lookup"><span data-stu-id="2be12-203">To verify that `HttpPOST` action is working correctly, [send messages to your connector](~/webhooks-and-connectors/how-to/connectors-using.md).</span></span>

## <a name="publish-connectors-for-the-organization"></a><span data-ttu-id="2be12-204">Publicar conectores para a organização</span><span class="sxs-lookup"><span data-stu-id="2be12-204">Publish connectors for the organization</span></span>

<span data-ttu-id="2be12-205">Se você quiser que o conector seja disponibilizado apenas para os usuários em sua organização, você pode carregar seu aplicativo de conector personalizado no catálogo de aplicativos [da sua organização.](~/concepts/deploy-and-publish/apps-publish.md)</span><span class="sxs-lookup"><span data-stu-id="2be12-205">If you want the connector to be available only to the users in your organization, you can upload your custom connector app to your [organization's app catalog](~/concepts/deploy-and-publish/apps-publish.md).</span></span>

<span data-ttu-id="2be12-206">Depois de carregar o pacote de aplicativos para configurar e usar o conector em uma equipe, instale o conector do catálogo de aplicativos da organização.</span><span class="sxs-lookup"><span data-stu-id="2be12-206">After uploading the app package to configure and use the connector in a team, install the connector from the organization's app catalog.</span></span>

<span data-ttu-id="2be12-207">**Para configurar um conector**</span><span class="sxs-lookup"><span data-stu-id="2be12-207">**To set up a connector**</span></span>

1. <span data-ttu-id="2be12-208">Selecione **Aplicativos** na barra de navegação esquerda.</span><span class="sxs-lookup"><span data-stu-id="2be12-208">Select **Apps** from the left navigation bar.</span></span>
1. <span data-ttu-id="2be12-209">Na seção **Aplicativos,** selecione **Conectores**.</span><span class="sxs-lookup"><span data-stu-id="2be12-209">In the **Apps** section, select **Connectors**.</span></span>
1. <span data-ttu-id="2be12-210">Selecione o conector que você deseja adicionar.</span><span class="sxs-lookup"><span data-stu-id="2be12-210">Select the connector that you want to add.</span></span> <span data-ttu-id="2be12-211">Uma janela de diálogo pop-up é exibida.</span><span class="sxs-lookup"><span data-stu-id="2be12-211">A pop up dialog window appears.</span></span>
1. <span data-ttu-id="2be12-212">No menu suspenso, selecione **Adicionar a uma equipe**.</span><span class="sxs-lookup"><span data-stu-id="2be12-212">From the dropdown menu, select **Add to a team**.</span></span>
1. <span data-ttu-id="2be12-213">Na caixa de pesquisa, digite um nome de equipe ou canal.</span><span class="sxs-lookup"><span data-stu-id="2be12-213">In the search box, type a team or channel name.</span></span>
1. <span data-ttu-id="2be12-214">Selecione **Configurar um Conector no** menu suspenso no canto inferior direito da janela de diálogo.</span><span class="sxs-lookup"><span data-stu-id="2be12-214">Select **Set up a Connector** from the dropdown menu in the bottom right corner of the dialog window.</span></span>

<span data-ttu-id="2be12-215">O conector está disponível na seção &#9679;&#9679;&#9679; > **Mais opções** Conectores Todos os Conectores  >    >    >  **para sua equipe** para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="2be12-215">The connector is available in the section &#9679;&#9679;&#9679; > **More options** > **Connectors** > **All** > **Connectors for your team** for that team.</span></span> <span data-ttu-id="2be12-216">Você pode navegar rolando até esta seção ou pesquisar o aplicativo do conector.</span><span class="sxs-lookup"><span data-stu-id="2be12-216">You can navigate by scrolling to this section or search for the connector app.</span></span> <span data-ttu-id="2be12-217">Para configurar ou modificar o conector, selecione **Configurar**.</span><span class="sxs-lookup"><span data-stu-id="2be12-217">To configure or modify the connector, select **Configure**.</span></span>

## <a name="distribute-webhook-and-connector"></a><span data-ttu-id="2be12-218">Distribuir webhook e conector</span><span class="sxs-lookup"><span data-stu-id="2be12-218">Distribute webhook and connector</span></span>

1. <span data-ttu-id="2be12-219">[Configurar um Webhook de entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md?branch=pr-en-us-3076#create-incoming-webhook) diretamente para sua equipe.</span><span class="sxs-lookup"><span data-stu-id="2be12-219">[Set up an Incoming Webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md?branch=pr-en-us-3076#create-incoming-webhook) directly for your team.</span></span>
1. <span data-ttu-id="2be12-220">Adicione uma [página de configuração](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#integrate-the-configuration-experience) e [publique seu Webhook de Entrada](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#publish-connectors-for-the-organization) em um Conector O365.</span><span class="sxs-lookup"><span data-stu-id="2be12-220">Add a [configuration page](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#integrate-the-configuration-experience) and [publish your Incoming Webhook](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#publish-connectors-for-the-organization) in a O365 Connector.</span></span>
1. <span data-ttu-id="2be12-221">Empacote e publique seu conector como parte do envio [do AppSource.](~/concepts/deploy-and-publish/office-store-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="2be12-221">Package and publish your connector as part of your [AppSource](~/concepts/deploy-and-publish/office-store-guidance.md) submission.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2be12-222">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="2be12-222">Code sample</span></span>

<span data-ttu-id="2be12-223">A tabela a seguir fornece o nome de exemplo e sua descrição:</span><span class="sxs-lookup"><span data-stu-id="2be12-223">The following table provides the sample name and its description:</span></span>

|<span data-ttu-id="2be12-224">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="2be12-224">**Sample name**</span></span> | <span data-ttu-id="2be12-225">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2be12-225">**Description**</span></span> | <span data-ttu-id="2be12-226">**.NET**</span><span class="sxs-lookup"><span data-stu-id="2be12-226">**.NET**</span></span> | <span data-ttu-id="2be12-227">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="2be12-227">**Node.js**</span></span> |
|----------------|------------------|--------|----------------|
| <span data-ttu-id="2be12-228">Conectores</span><span class="sxs-lookup"><span data-stu-id="2be12-228">Connectors</span></span>    | <span data-ttu-id="2be12-229">Exemplo Office 365 conector gerando notificações para Teams canal.</span><span class="sxs-lookup"><span data-stu-id="2be12-229">Sample Office 365 Connector generating notifications to Teams channel.</span></span>|   [<span data-ttu-id="2be12-230">View</span><span class="sxs-lookup"><span data-stu-id="2be12-230">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [<span data-ttu-id="2be12-231">View</span><span class="sxs-lookup"><span data-stu-id="2be12-231">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| <span data-ttu-id="2be12-232">Exemplo de conectores genéricos</span><span class="sxs-lookup"><span data-stu-id="2be12-232">Generic connectors sample</span></span> |<span data-ttu-id="2be12-233">Código de exemplo para um conector genérico que é fácil de personalizar para qualquer sistema que oferece suporte a webhooks.</span><span class="sxs-lookup"><span data-stu-id="2be12-233">Sample code for a generic connector that is easy to customize for any system that supports webhooks.</span></span>|  | [<span data-ttu-id="2be12-234">View</span><span class="sxs-lookup"><span data-stu-id="2be12-234">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|

## <a name="see-also"></a><span data-ttu-id="2be12-235">Confira também</span><span class="sxs-lookup"><span data-stu-id="2be12-235">See also</span></span>

* [<span data-ttu-id="2be12-236">Criar e enviar mensagens</span><span class="sxs-lookup"><span data-stu-id="2be12-236">Create and send messages</span></span>](~/webhooks-and-connectors/how-to/connectors-using.md)
* [<span data-ttu-id="2be12-237">Criar um Webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="2be12-237">Create an Incoming Webhook</span></span>](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [<span data-ttu-id="2be12-238">Criar um conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="2be12-238">Create an Office 365 Connector</span></span>](~/webhooks-and-connectors/how-to/connectors-creating.md)
