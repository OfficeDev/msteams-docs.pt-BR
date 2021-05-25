---
title: Conectores de Office 365
description: Descreve como começar a usar Office 365 conectores no Microsoft Teams
keywords: conector do o365 no teams
localization_priority: Normal
ms.topic: conceptual
ms.date: 04/19/2019
ms.openlocfilehash: ace546853d7dfe9773055288a0fc3471fe656652
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52629820"
---
# <a name="creating-office-365-connectors-for-microsoft-teams"></a><span data-ttu-id="f5580-104">Criando Office 365 conectores para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f5580-104">Creating Office 365 Connectors for Microsoft Teams</span></span>

<span data-ttu-id="f5580-105">Com Microsoft Teams aplicativos, você pode adicionar seu conector de Office 365 existente ou criar um novo para incluir no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="f5580-105">With Microsoft Teams apps, you can add your existing Office 365 Connector or build a new one to include in Microsoft Teams.</span></span> <span data-ttu-id="f5580-106">Confira [Criar seu próprio Conector para](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="f5580-106">See [Build your own Connector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector) for more information.</span></span>

## <a name="adding-a-connector-to-your-teams-app"></a><span data-ttu-id="f5580-107">Adicionando um Conector ao seu Teams App</span><span class="sxs-lookup"><span data-stu-id="f5580-107">Adding a Connector to your Teams App</span></span>

<span data-ttu-id="f5580-108">Você pode distribuir seu Conector registrado como parte do pacote de aplicativos do Teams.</span><span class="sxs-lookup"><span data-stu-id="f5580-108">You can distribute your registered Connector as part of your Teams app package.</span></span> <span data-ttu-id="f5580-109">Seja como uma solução autônoma ou [](~/concepts/extensibility-points.md) um dos vários recursos que sua experiência [](~/concepts/build-and-test/apps-package.md) habilita no Teams, você pode empacotar e publicar seu Conector como parte do envio do AppSource ou você pode fornecer aos usuários diretamente para carregar no Teams. [](~/concepts/deploy-and-publish/apps-publish.md)</span><span class="sxs-lookup"><span data-stu-id="f5580-109">Whether as a standalone solution, or one of several [capabilities](~/concepts/extensibility-points.md) that your experience enables in Teams, you can [package](~/concepts/build-and-test/apps-package.md) and [publish](~/concepts/deploy-and-publish/apps-publish.md) your Connector as part of your AppSource submission, or you can provide it to users directly for uploading within Teams.</span></span>

<span data-ttu-id="f5580-110">Para distribuir seu Conector, você precisa se registrar usando o Painel do Desenvolvedor [de Conectores.](https://outlook.office.com/connectors/home/login/#/publish)</span><span class="sxs-lookup"><span data-stu-id="f5580-110">To distribute your Connector, you need to register by using the [Connectors Developer Dashboard](https://outlook.office.com/connectors/home/login/#/publish).</span></span> <span data-ttu-id="f5580-111">Por padrão, uma vez que um Conector é registrado, presume-se que o conector funcionará em todos os produtos Office 365 que os suportam, incluindo Outlook e Teams.</span><span class="sxs-lookup"><span data-stu-id="f5580-111">By default, once a Connector is registered, it's assumed that your Connector will work in all Office 365 products that support them, including Outlook and Teams.</span></span> <span data-ttu-id="f5580-112">Se esse não _for_ o caso e você precisar criar um Conector que funcione apenas no Microsoft Teams, entre em contato conosco diretamente [Microsoft Teams Envios de Aplicativo.](mailto:teamsubm@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="f5580-112">If that is _not_ the case and you need to create a Connector that only works in Microsoft Teams, contact us directly at [Microsoft Teams App Submissions](mailto:teamsubm@microsoft.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5580-113">Depois de escolher **Salvar** no Painel do Desenvolvedor de Conectores, seu Conector será registrado.</span><span class="sxs-lookup"><span data-stu-id="f5580-113">After you choose **Save** in the Connectors Developer Dashboard, your Connector is registered.</span></span> <span data-ttu-id="f5580-114">Se você quiser publicar seu Conector no AppSource, siga as instruções em Publicar seu aplicativo Microsoft Teams [no AppSource](~/concepts/deploy-and-publish/apps-publish.md).</span><span class="sxs-lookup"><span data-stu-id="f5580-114">If you want to publish your Connector in AppSource, follow the instructions in [Publish your Microsoft Teams app to AppSource](~/concepts/deploy-and-publish/apps-publish.md).</span></span> <span data-ttu-id="f5580-115">Se você não quiser publicar seu aplicativo no AppSource e, em vez disso, simplesmente distribuí-lo diretamente para sua organização, você pode fazer isso publicando em [sua organização.](#publish-connectors-for-your-organization)</span><span class="sxs-lookup"><span data-stu-id="f5580-115">If you do not wish to publish your app in AppSource, and rather simply distribute it directly to your organization only, you can do so by [publishing to your organization](#publish-connectors-for-your-organization).</span></span> <span data-ttu-id="f5580-116">Se você quiser apenas publicar em sua organização, nenhuma ação será necessária no painel conector.</span><span class="sxs-lookup"><span data-stu-id="f5580-116">If you only want to publish to your organization, no further action is necessary on the Connector dashboard.</span></span>

### <a name="integrating-the-configuration-experience"></a><span data-ttu-id="f5580-117">Integrando a experiência de configuração</span><span class="sxs-lookup"><span data-stu-id="f5580-117">Integrating the configuration experience</span></span>

<span data-ttu-id="f5580-118">Seus usuários concluirão toda a experiência de configuração do Conector sem precisar sair do cliente Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="f5580-118">Your users will complete the entire Connector configuration experience without having to leave the Teams client.</span></span> <span data-ttu-id="f5580-119">Para obter essa experiência, Teams inserirá sua página de configuração diretamente em um iframe.</span><span class="sxs-lookup"><span data-stu-id="f5580-119">To achieve this experience, Teams will embed your configuration page directly within an iframe.</span></span> <span data-ttu-id="f5580-120">A sequência de operações é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="f5580-120">The sequence of operations is as follows:</span></span>

1. <span data-ttu-id="f5580-121">O usuário clica no conector para iniciar o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f5580-121">The user clicks on your connector to begin the configuration process.</span></span>
2. <span data-ttu-id="f5580-122">Teams carregará sua experiência de configuração em linha.</span><span class="sxs-lookup"><span data-stu-id="f5580-122">Teams will load your configuration experience in line.</span></span>
3. <span data-ttu-id="f5580-123">O usuário interage com sua experiência da Web para concluir a configuração.</span><span class="sxs-lookup"><span data-stu-id="f5580-123">The user interacts with your web experience to complete the configuration.</span></span>
4. <span data-ttu-id="f5580-124">O usuário pressiona "Salvar", que dispara um retorno de chamada em seu código.</span><span class="sxs-lookup"><span data-stu-id="f5580-124">The user presses "Save", which triggers a callback in your code.</span></span>
5. <span data-ttu-id="f5580-125">Seu código processará o evento save recuperando as configurações de webhook (documentadas abaixo).</span><span class="sxs-lookup"><span data-stu-id="f5580-125">Your code will process the save event by retrieving the webhook settings (documented below).</span></span> <span data-ttu-id="f5580-126">Em seguida, seu código deve armazenar o webhook para postar eventos posteriormente.</span><span class="sxs-lookup"><span data-stu-id="f5580-126">Your code should then store the webhook to post events later.</span></span>

<span data-ttu-id="f5580-127">Você pode reutilizar sua experiência de configuração da Web existente ou criar uma versão separada para ser hospedada especificamente em Teams.</span><span class="sxs-lookup"><span data-stu-id="f5580-127">You can reuse your existing web configuration experience or create a separate version to be hosted specifically in Teams.</span></span> <span data-ttu-id="f5580-128">Seu código deve:</span><span class="sxs-lookup"><span data-stu-id="f5580-128">Your code should:</span></span>

1. <span data-ttu-id="f5580-129">Inclua o Microsoft Teams JavaScript SDK.</span><span class="sxs-lookup"><span data-stu-id="f5580-129">Include the Microsoft Teams JavaScript SDK.</span></span> <span data-ttu-id="f5580-130">Isso fornece acesso de código a APIs para executar operações comuns, como obter o contexto atual de usuário/canal/equipe e iniciar fluxos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="f5580-130">This gives your code access to APIs to perform common operations like getting the current user/channel/team context and initiating authentication flows.</span></span> <span data-ttu-id="f5580-131">Inicializar o SDK chamando `microsoftTeams.initialize()`.</span><span class="sxs-lookup"><span data-stu-id="f5580-131">Initialize the SDK by calling `microsoftTeams.initialize()`.</span></span>
2. <span data-ttu-id="f5580-132">Chame `microsoftTeams.settings.setValidityState(true)` quando quiser habilitar o botão Salvar.</span><span class="sxs-lookup"><span data-stu-id="f5580-132">Call `microsoftTeams.settings.setValidityState(true)` when you want to enable the Save button.</span></span> <span data-ttu-id="f5580-133">Você deve fazer isso como uma resposta à entrada de usuário válida, como uma seleção ou uma atualização de campo.</span><span class="sxs-lookup"><span data-stu-id="f5580-133">You should do this as a response to valid user input, such as a selection or field update.</span></span>
3. <span data-ttu-id="f5580-134">Registre `microsoftTeams.settings.registerOnSaveHandler()` um manipulador de eventos, que é chamado quando o usuário clica em Salvar.</span><span class="sxs-lookup"><span data-stu-id="f5580-134">Register a `microsoftTeams.settings.registerOnSaveHandler()` event handler, which gets called when the user clicks Save.</span></span>
4. <span data-ttu-id="f5580-135">Chame `microsoftTeams.settings.setSettings()` para salvar as configurações do conector.</span><span class="sxs-lookup"><span data-stu-id="f5580-135">Call `microsoftTeams.settings.setSettings()` to save the connector settings.</span></span> <span data-ttu-id="f5580-136">O que é salvo aqui também é o que será mostrado na caixa de diálogo de configuração se o usuário tentar atualizar uma configuração existente para o conector.</span><span class="sxs-lookup"><span data-stu-id="f5580-136">What's saved here is also what will be shown in the configuration dialog if the user tries to update an existing configuration for your connector.</span></span>
5. <span data-ttu-id="f5580-137">Chame `microsoftTeams.settings.getSettings()` para buscar propriedades de webhook, incluindo a PRÓPRIA URL.</span><span class="sxs-lookup"><span data-stu-id="f5580-137">Call `microsoftTeams.settings.getSettings()` to fetch webhook properties, including the URL itself.</span></span> <span data-ttu-id="f5580-138">Você deve chamar isso Além de durante o evento save, você também deve chamar isso quando sua página for carregada pela primeira vez no caso de uma nova configuração.</span><span class="sxs-lookup"><span data-stu-id="f5580-138">You should call this  In addition to during the save event, you should also call this when your page is first loaded in the case of a re-configuration.</span></span>
6. <span data-ttu-id="f5580-139">(Opcional) Registre `microsoftTeams.settings.registerOnRemoveHandler()` um manipulador de eventos, que é chamado quando o usuário remove o conector.</span><span class="sxs-lookup"><span data-stu-id="f5580-139">(Optional) Register a `microsoftTeams.settings.registerOnRemoveHandler()` event handler, which gets called when the user removes your connector.</span></span> <span data-ttu-id="f5580-140">Esse evento oferece ao seu serviço a oportunidade de executar qualquer ação de limpeza.</span><span class="sxs-lookup"><span data-stu-id="f5580-140">This event gives your service an opportunity to perform any cleanup actions.</span></span>

<span data-ttu-id="f5580-141">Aqui está um HTML de exemplo para criar uma página de configuração do Conector sem o CSS:</span><span class="sxs-lookup"><span data-stu-id="f5580-141">Here's a sample HTML to create a Connector configuration page without the CSS:</span></span>

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

#### <a name="getsettings-response-properties"></a><span data-ttu-id="f5580-142">`GetSettings()` propriedades de resposta</span><span class="sxs-lookup"><span data-stu-id="f5580-142">`GetSettings()` response properties</span></span>

>[!Note]
><span data-ttu-id="f5580-143">Os parâmetros retornados pela chamada aqui são diferentes do que se você fosse invocar esse método de uma guia e diferir daqueles `getSettings` documentados [aqui](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="f5580-143">The parameters returned by the `getSettings` call here are different than if you were to invoke this method from a tab, and differ from those documented [here](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true).</span></span>

| <span data-ttu-id="f5580-144">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f5580-144">Parameter</span></span>   | <span data-ttu-id="f5580-145">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f5580-145">Details</span></span> |
|-------------|---------|
| `entityId`       | <span data-ttu-id="f5580-146">A ID da entidade, conforme definido pelo código ao chamar `setSettings()` .</span><span class="sxs-lookup"><span data-stu-id="f5580-146">The entity ID, as set by your code when calling `setSettings()`.</span></span> |
| `configName`  | <span data-ttu-id="f5580-147">O nome da configuração, conforme definido pelo código ao chamar `setSettings()` .</span><span class="sxs-lookup"><span data-stu-id="f5580-147">The configuration name, as set by your code when calling `setSettings()`.</span></span> |
| `contentUrl` | <span data-ttu-id="f5580-148">A URL da página de configuração, conforme definido pelo código ao chamar `setSettings()` .</span><span class="sxs-lookup"><span data-stu-id="f5580-148">The URL of the configuration page, as set by your code when calling `setSettings()`.</span></span> |
| `webhookUrl` | <span data-ttu-id="f5580-149">A URL de webhook criada para esse conector.</span><span class="sxs-lookup"><span data-stu-id="f5580-149">The webhook URL created for this connector.</span></span> <span data-ttu-id="f5580-150">Persista a URL do webhook e use-a para POSTAR JSON estruturado para enviar cartões para o canal.</span><span class="sxs-lookup"><span data-stu-id="f5580-150">Persist the webhook URL and use it to POST structured JSON to send cards to the channel.</span></span> <span data-ttu-id="f5580-151">A `webhookUrl` é retornada quando o aplicativo retorna com êxito.</span><span class="sxs-lookup"><span data-stu-id="f5580-151">The `webhookUrl` is returned only when application returns successfully.</span></span> |
| `appType` | <span data-ttu-id="f5580-152">Os valores retornados podem ser `mail`, `groups` ou `teams` correspondente ao Email do Office 365, Grupos do Office 365 ou Microsoft Teams respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f5580-152">The values returned can be `mail`, `groups` or `teams` corresponding to the Office 365 Mail, Office 365 Groups or Microsoft Teams respectively.</span></span> |
| `userObjectId` | <span data-ttu-id="f5580-153">Esta é a ID exclusiva correspondente ao usuário Office 365 que iniciou a instalação do conector.</span><span class="sxs-lookup"><span data-stu-id="f5580-153">This is the unique id corresponding to the Office 365 user who initiated setup of the connector.</span></span> <span data-ttu-id="f5580-154">Ela deve ser protegida.</span><span class="sxs-lookup"><span data-stu-id="f5580-154">It should be secured.</span></span> <span data-ttu-id="f5580-155">Este valor pode ser usado para associar o usuário no Office 365 que realizou a configuração para o usuário no seu serviço.</span><span class="sxs-lookup"><span data-stu-id="f5580-155">This value can be used to associate the user in Office 365 who set up the configuration to the user in your service.</span></span> |

<span data-ttu-id="f5580-156">Se você precisar autenticar o usuário como parte do carregamento de sua página na etapa 2 acima, consulte este [link](~/tabs/how-to/authentication/auth-flow-tab.md) para obter detalhes sobre como você pode integrar o logon quando sua página é incorporada.</span><span class="sxs-lookup"><span data-stu-id="f5580-156">If you need to authenticate the user as part of loading your page in step 2 above, refer to [this link](~/tabs/how-to/authentication/auth-flow-tab.md) for details on how you can integrate login when your page is embedded.</span></span>

> [!NOTE]
> <span data-ttu-id="f5580-157">Devido a motivos de compatibilidade entre clientes, seu código precisará chamar com a URL e os métodos de retorno de chamada de `microsoftTeams.authentication.registerAuthenticationHandlers()` sucesso/falha antes de chamar `authenticate()` .</span><span class="sxs-lookup"><span data-stu-id="f5580-157">Due to cross-client compatibility reasons, your code will need to call `microsoftTeams.authentication.registerAuthenticationHandlers()` with the URL and success/failure callback methods before calling `authenticate()`.</span></span>

#### <a name="handling-edits"></a><span data-ttu-id="f5580-158">Manipulando edições</span><span class="sxs-lookup"><span data-stu-id="f5580-158">Handling edits</span></span>

<span data-ttu-id="f5580-159">O código deve lidar com o retorno de usuários para editar uma configuração de conector existente.</span><span class="sxs-lookup"><span data-stu-id="f5580-159">Your code should handle users returning to edit an existing connector configuration.</span></span> <span data-ttu-id="f5580-160">Para fazer isso, chame `microsoftTeams.settings.setSettings()` durante a configuração inicial com os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="f5580-160">To do this, call `microsoftTeams.settings.setSettings()` during the initial configuration with the following parameters:</span></span>

- <span data-ttu-id="f5580-161">`entityId` é a ID personalizada que é compreendida pelo seu serviço e representa o que o usuário configurou.</span><span class="sxs-lookup"><span data-stu-id="f5580-161">`entityId` is the custom ID that is understood by your service and represents what the user has configured.</span></span>
- <span data-ttu-id="f5580-162">`configName` é um nome amigável que seu código de configuração pode recuperar</span><span class="sxs-lookup"><span data-stu-id="f5580-162">`configName` is a friendly name that your configuration code can retrieve</span></span>
- <span data-ttu-id="f5580-163">`contentUrl` é uma URL personalizada que é carregada quando um usuário edita uma configuração de conector existente.</span><span class="sxs-lookup"><span data-stu-id="f5580-163">`contentUrl` is a custom URL that gets loaded when a user edits an existing connector configuration.</span></span> <span data-ttu-id="f5580-164">Você pode usar essa URL para facilitar o seu código lidar com o caso de edição.</span><span class="sxs-lookup"><span data-stu-id="f5580-164">You can use this URL to make it easier for your code to handle the edit case.</span></span>

<span data-ttu-id="f5580-165">Normalmente, essa chamada é feita como parte do manipulador de eventos save.</span><span class="sxs-lookup"><span data-stu-id="f5580-165">Typically, this call is made as part of your save event handler.</span></span> <span data-ttu-id="f5580-166">Em seguida, quando o acima for carregado, seu código deverá chamar para pré-estipular quaisquer configurações ou formulários na interface do usuário `contentUrl` `getSettings()` de configuração.</span><span class="sxs-lookup"><span data-stu-id="f5580-166">Then, when the `contentUrl` above is loaded, your code should call `getSettings()` to prepopulate any settings or forms in your configuration UI.</span></span>

#### <a name="handling-removals"></a><span data-ttu-id="f5580-167">Manipulando remoções</span><span class="sxs-lookup"><span data-stu-id="f5580-167">Handling removals</span></span>

<span data-ttu-id="f5580-168">Opcionalmente, você pode executar um manipulador de eventos quando o usuário remover uma configuração de conector existente.</span><span class="sxs-lookup"><span data-stu-id="f5580-168">You can optionally execute an event handler when the user removes an existing connector configuration.</span></span> <span data-ttu-id="f5580-169">Você registra esse manipulador chamando `microsoftTeams.settings.registerOnRemoveHandler()` .</span><span class="sxs-lookup"><span data-stu-id="f5580-169">You register this handler by calling `microsoftTeams.settings.registerOnRemoveHandler()`.</span></span> <span data-ttu-id="f5580-170">Esse manipulador pode ser usado para executar operações de limpeza, como a remoção de entradas de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f5580-170">This handler can be used to perform cleanup operations such as removing entries from a database.</span></span>

### <a name="including-the-connector-in-your-manifest"></a><span data-ttu-id="f5580-171">Incluindo o Conector em seu Manifesto</span><span class="sxs-lookup"><span data-stu-id="f5580-171">Including the Connector in your Manifest</span></span>

<span data-ttu-id="f5580-172">Você pode baixar o manifesto do aplicativo gerado automaticamente Teams no portal.</span><span class="sxs-lookup"><span data-stu-id="f5580-172">You can download the auto-generated Teams app manifest from the portal.</span></span> <span data-ttu-id="f5580-173">Antes de usá-lo para testar ou publicar seu aplicativo, você deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f5580-173">Before you can use it to test or publish your app, though, you must do the following:</span></span>

- <span data-ttu-id="f5580-174">[Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="f5580-174">[Include two icons](../../concepts/build-and-test/apps-package.md#app-icons).</span></span>
- <span data-ttu-id="f5580-175">Modifique a parte dos `icons` do manifesto para se referir aos nomes de arquivo dos ícones em vez das URLs.</span><span class="sxs-lookup"><span data-stu-id="f5580-175">Modify the `icons` portion of the manifest to refer to the file names of the icons instead of URLs.</span></span>

<span data-ttu-id="f5580-176">O seguinte arquivo manifest.json contém os elementos básicos necessários para testar e enviar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f5580-176">The following manifest.json file contains the basic elements needed to test and submit your app.</span></span>

> [!NOTE]
> <span data-ttu-id="f5580-177">Substitua `id` e `connectorId` no exemplo a seguir pelo GUID do Conector.</span><span class="sxs-lookup"><span data-stu-id="f5580-177">Replace `id` and `connectorId` in the following example with the GUID of your Connector.</span></span>

#### <a name="example-manifestjson-with-connector"></a><span data-ttu-id="f5580-178">Exemplo de manifest.json com o Conector</span><span class="sxs-lookup"><span data-stu-id="f5580-178">Example manifest.json with Connector</span></span>

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
    "full": "This is a sample manifest for an app with a connector with an inline configuration experience.",
    "short": "This is a sample manifest for an app with a connector."
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "configurationUrl": "https://teamstodoappconnectorwithinlineconfig.azurewebsites.net/Connector/Setup",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App Long Name"
  },
  "accentColor": "#FFFFFF"
}
```

## <a name="disable-or-enable-connectors-in-teams"></a><span data-ttu-id="f5580-179">Desabilitar ou habilitar conectores Teams</span><span class="sxs-lookup"><span data-stu-id="f5580-179">Disable or enable connectors in Teams</span></span>

<span data-ttu-id="f5580-180">O módulo Exchange Online PowerShell V2 usa autenticação moderna e funciona com autenticação multifatória (MFA) para se conectar Exchange todos os ambientes do PowerShell relacionados Exchange no Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f5580-180">The Exchange Online PowerShell V2 module uses modern authentication and works with multi-factor authentication (MFA) for connecting to all Exchange-related PowerShell environments in Microsoft 365.</span></span> <span data-ttu-id="f5580-181">Os administradores podem usar Exchange Online PowerShell para desabilitar conectores para um locatário inteiro ou uma caixa de correio de grupo específica, afetando todos os usuários nesse locatário ou caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="f5580-181">Admins can use Exchange Online PowerShell to disable connectors for an entire tenant or a specific group mailbox, affecting all users in that tenant or mailbox.</span></span> <span data-ttu-id="f5580-182">Não é possível desabilitar para alguns e não para outros.</span><span class="sxs-lookup"><span data-stu-id="f5580-182">It is not possible to disable for some and not others.</span></span> <span data-ttu-id="f5580-183">Além disso, os conectores são desabilitados por padrão para GCC locatários.</span><span class="sxs-lookup"><span data-stu-id="f5580-183">Also, connectors are disabled by default for GCC tenants.</span></span>

<span data-ttu-id="f5580-184">A configuração no nível do locatário substitui a configuração de nível de grupo.</span><span class="sxs-lookup"><span data-stu-id="f5580-184">The tenant-level setting overrides the group-level setting.</span></span> <span data-ttu-id="f5580-185">Por exemplo, se um administrador habilitar conectores para o grupo e desabilitá-los no locatário, os conectores do grupo serão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="f5580-185">For example, if an admin enables connectors for the group and disables them on the tenant, connectors for the group will be disabled.</span></span> <span data-ttu-id="f5580-186">Para habilitar um conector Teams, conecte-se [Exchange Online PowerShell](/docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) usando autenticação moderna com ou sem MFA.</span><span class="sxs-lookup"><span data-stu-id="f5580-186">To enable a connector in Teams, [connect to Exchange Online PowerShell](/docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) using modern authentication with or without MFA.</span></span>

### <a name="commands-to-disable-or-enable-connectors"></a><span data-ttu-id="f5580-187">Comandos para desabilitar ou habilitar conectores</span><span class="sxs-lookup"><span data-stu-id="f5580-187">Commands to disable or enable connectors</span></span>

<span data-ttu-id="f5580-188">**Execute o comando no Exchange Online PowerShell**</span><span class="sxs-lookup"><span data-stu-id="f5580-188">**Run the command in Exchange Online PowerShell**</span></span>

* <span data-ttu-id="f5580-189">Para desabilitar conectores para o locatário: `Set-OrganizationConfig -ConnectorsEnabled:$false` .</span><span class="sxs-lookup"><span data-stu-id="f5580-189">To disable connectors for the tenant: `Set-OrganizationConfig -ConnectorsEnabled:$false`.</span></span>
* <span data-ttu-id="f5580-190">Para desabilitar mensagens ativas para o locatário: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false` .</span><span class="sxs-lookup"><span data-stu-id="f5580-190">To disable actionable messages for the tenant: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false`.</span></span>
* <span data-ttu-id="f5580-191">Para habilitar conectores para Teams, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="f5580-191">To enable connectors for Teams, run the following commands:</span></span>
    * `Set-OrganizationConfig -ConnectorsEnabled:$true `
    * `Set-OrganizationConfig -ConnectorsEnabledForTeams:$true`
    * `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$true`

<span data-ttu-id="f5580-192">Para obter mais informações sobre a troca de módulos do PowerShell, consulte [Set-OrganizationConfig](/docs.microsoft.com/powershell/module/exchange/Set-OrganizationConfig.md?view=exchange-ps&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="f5580-192">For more information on PowerShell module exchange, see [Set-OrganizationConfig](/docs.microsoft.com/powershell/module/exchange/Set-OrganizationConfig.md?view=exchange-ps&preserve-view=true).</span></span> <span data-ttu-id="f5580-193">Para habilitar ou desabilitar Outlook conectores, [conecte aplicativos aos seus grupos em Outlook](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab?ui=en-us&rs=en-us&ad=us).</span><span class="sxs-lookup"><span data-stu-id="f5580-193">To enable or disable Outlook connectors, [connect apps to your groups in Outlook](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab?ui=en-us&rs=en-us&ad=us).</span></span>

## <a name="testing-your-connector"></a><span data-ttu-id="f5580-194">Testar o Conector</span><span class="sxs-lookup"><span data-stu-id="f5580-194">Testing your Connector</span></span>

<span data-ttu-id="f5580-195">Para testar o Conector, carregue-o em uma equipe, como em qualquer outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f5580-195">To test your Connector, upload it to a team as you would with any other app.</span></span> <span data-ttu-id="f5580-196">Você pode criar um pacote .zip usando o arquivo de manifesto do Painel do Desenvolvedor do Connectors (modificado conforme indicado na seção anterior) e os dois arquivos de ícone.</span><span class="sxs-lookup"><span data-stu-id="f5580-196">You can create a .zip package using the manifest file from the Connectors Developer Dashboard (modified as directed in the preceding section) and the two icon files.</span></span>

<span data-ttu-id="f5580-197">Depois de carregar o aplicativo, abra a lista de conectores em qualquer canal.</span><span class="sxs-lookup"><span data-stu-id="f5580-197">After you upload the app, open the Connectors list from any channel.</span></span> <span data-ttu-id="f5580-198">Role até a parte inferior para ver o aplicativo na seção **Carregado**.</span><span class="sxs-lookup"><span data-stu-id="f5580-198">Scroll to the bottom to see your app in the **Uploaded** section.</span></span>

![Captura de tela da seção carregada na caixa de diálogo do Conector](~/assets/images/connectors/connector_dialog_uploaded.png)

<span data-ttu-id="f5580-200">Agora você pode iniciar a experiência de configuração.</span><span class="sxs-lookup"><span data-stu-id="f5580-200">You can now launch the configuration experience.</span></span> <span data-ttu-id="f5580-201">Esteja ciente de que esse fluxo ocorre inteiramente dentro Microsoft Teams como uma experiência hospedada.</span><span class="sxs-lookup"><span data-stu-id="f5580-201">Be aware that this flow occurs entirely within Microsoft Teams as a hosted experience.</span></span>

<span data-ttu-id="f5580-202">Para verificar se uma `HttpPOST` ação está funcionando corretamente, [envie mensagens para seu conector](~/webhooks-and-connectors/how-to/connectors-using.md).</span><span class="sxs-lookup"><span data-stu-id="f5580-202">To verify that an `HttpPOST` action is working correctly, [send messages to your connector](~/webhooks-and-connectors/how-to/connectors-using.md).</span></span>

## <a name="publish-connectors-for-your-organization"></a><span data-ttu-id="f5580-203">Publicar Conectores para sua organização</span><span class="sxs-lookup"><span data-stu-id="f5580-203">Publish Connectors for your organization</span></span>

<span data-ttu-id="f5580-204">Às vezes, talvez você não queira publicar seu aplicativo conector na AppSource/Store pública, mas gostaria que ele fosse disponibilizado apenas para os usuários em sua organização.</span><span class="sxs-lookup"><span data-stu-id="f5580-204">Sometimes, you may not want to publish your connector app to the public AppSource/Store but would like it to be available only to the users in your organization.</span></span> <span data-ttu-id="f5580-205">Nesses casos, você pode carregar seu aplicativo de conector personalizado no Catálogo de [Aplicativos da sua organização.](~/concepts/deploy-and-publish/apps-publish.md)</span><span class="sxs-lookup"><span data-stu-id="f5580-205">In such cases, you can upload your custom connector app to your [organization's App Catalog](~/concepts/deploy-and-publish/apps-publish.md).</span></span> <span data-ttu-id="f5580-206">Dessa forma, seu aplicativo conector estará disponível apenas para essa organização e você não precisará publicar seu conector no armazenamento público.</span><span class="sxs-lookup"><span data-stu-id="f5580-206">This way, your connector app will be available only to that organization, and you will not need to publish your connector to the public store.</span></span>

<span data-ttu-id="f5580-207">Depois de carregar seu pacote de aplicativos, para configurar e usar o conector em uma Equipe, ele pode ser instalado no catálogo de aplicativos da organização seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="f5580-207">Once you've uploaded your app package, to configure and use the connector in a Team it can be installed from the organization's app catalog by following these steps:</span></span>

1. <span data-ttu-id="f5580-208">Selecione o ícone de aplicativos na barra de navegação vertical extrema esquerda.</span><span class="sxs-lookup"><span data-stu-id="f5580-208">Select the apps icon from the far left vertical navigation bar.</span></span>
1. <span data-ttu-id="f5580-209">Na janela **Aplicativos,** selecione **Conectores**.</span><span class="sxs-lookup"><span data-stu-id="f5580-209">In the **Apps** window select **Connectors**.</span></span>
1. <span data-ttu-id="f5580-210">Selecione o conector que você deseja adicionar e uma janela de diálogo pop-up será exibida.</span><span class="sxs-lookup"><span data-stu-id="f5580-210">Select the connector that you want to add and a pop-up dialog window will display.</span></span>
1. <span data-ttu-id="f5580-211">Selecione a **barra Adicionar a uma equipe.**</span><span class="sxs-lookup"><span data-stu-id="f5580-211">Select the **Add to a team** bar.</span></span>
1. <span data-ttu-id="f5580-212">Na próxima janela de diálogo, digite um nome de equipe ou canal.</span><span class="sxs-lookup"><span data-stu-id="f5580-212">In the next dialog window type a team or channel name.</span></span>
1. <span data-ttu-id="f5580-213">Selecione a **barra Configurar um conector** no canto inferior direito da janela de diálogo.</span><span class="sxs-lookup"><span data-stu-id="f5580-213">Select the **Set up a connector** bar from the bottom right corner of dialog window.</span></span>
1. <span data-ttu-id="f5580-214">O conector estará disponível na seção &#9679;&#9679;&#9679; => *Mais* opções Conectores Todos os Conectores para você  =>    =>    =>  *equipe* para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="f5580-214">The connector will be available in the  section &#9679;&#9679;&#9679; => *More options* => *Connectors* => *All* => *Connectors for you team* for that team.</span></span> <span data-ttu-id="f5580-215">Você pode navegar rolando até esta seção ou pesquisar o aplicativo do conector.</span><span class="sxs-lookup"><span data-stu-id="f5580-215">You can navigate by scrolling to this section or search for the connector app.</span></span>
1. <span data-ttu-id="f5580-216">Para configurar ou modificar o conector, selecione a **barra Configurar.**</span><span class="sxs-lookup"><span data-stu-id="f5580-216">To configure or modify the connector select the **Configure** bar.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f5580-217">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f5580-217">Code sample</span></span>
|<span data-ttu-id="f5580-218">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="f5580-218">**Sample name**</span></span> | <span data-ttu-id="f5580-219">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="f5580-219">**Description**</span></span> | <span data-ttu-id="f5580-220">**.NET**</span><span class="sxs-lookup"><span data-stu-id="f5580-220">**.NET**</span></span> | <span data-ttu-id="f5580-221">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="f5580-221">**Node.js**</span></span> |
|----------------|------------------|--------|----------------|
| <span data-ttu-id="f5580-222">Conectores</span><span class="sxs-lookup"><span data-stu-id="f5580-222">Connectors</span></span>    | <span data-ttu-id="f5580-223">Exemplo Office 365 conector gerando notificações para o canal de equipes.</span><span class="sxs-lookup"><span data-stu-id="f5580-223">Sample Office 365 Connector generating notifications to teams channel.</span></span>|   [<span data-ttu-id="f5580-224">View</span><span class="sxs-lookup"><span data-stu-id="f5580-224">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [<span data-ttu-id="f5580-225">View</span><span class="sxs-lookup"><span data-stu-id="f5580-225">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| <span data-ttu-id="f5580-226">Exemplo de conectores genéricos</span><span class="sxs-lookup"><span data-stu-id="f5580-226">Generic connectors sample</span></span> |<span data-ttu-id="f5580-227">Exemplo de código para um conector genérico que é fácil de personalizar para qualquer sistema que oferece suporte a webhooks.</span><span class="sxs-lookup"><span data-stu-id="f5580-227">Sample code for a generic connector that's easy to customize for any system which supports webhooks.</span></span>|  | [<span data-ttu-id="f5580-228">View</span><span class="sxs-lookup"><span data-stu-id="f5580-228">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|
