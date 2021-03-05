---
title: Conectores de Office 365
description: Descreve como começar a usar os Conectores do Office 365 no Microsoft Teams
keywords: conector do o365 no teams
ms.topic: conceptual
ms.date: 04/19/2019
ms.openlocfilehash: 8f9fcc40ca0634ead0a6c5d7d0653ad4ab993860
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449252"
---
# <a name="creating-office-365-connectors-for-microsoft-teams"></a><span data-ttu-id="fdb2d-104">Criando conectores do Office 365 para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="fdb2d-104">Creating Office 365 Connectors for Microsoft Teams</span></span>

><span data-ttu-id="fdb2d-105">Com os aplicativos do Microsoft Teams, você pode adicionar seu Conector do Office 365 existente ou criar um novo para incluir no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-105">With Microsoft Teams apps, you can add your existing Office 365 Connector or build a new one to include in Microsoft Teams.</span></span> <span data-ttu-id="fdb2d-106">Confira [Criar seu próprio Conector para](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-106">See [Build your own Connector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector) for more information.</span></span>

## <a name="adding-a-connector-to-your-teams-app"></a><span data-ttu-id="fdb2d-107">Adicionando um Conector ao seu Aplicativo do Teams</span><span class="sxs-lookup"><span data-stu-id="fdb2d-107">Adding a Connector to your Teams App</span></span>

<span data-ttu-id="fdb2d-108">Você pode distribuir seu Conector registrado como parte do pacote de aplicativos do Teams.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-108">You can distribute your registered Connector as part of your Teams app package.</span></span> <span data-ttu-id="fdb2d-109">Seja como uma solução autônoma ou um dos vários recursos que sua [](~/concepts/build-and-test/apps-package.md) experiência [](~/concepts/deploy-and-publish/apps-publish.md) habilita no Teams, você pode empacotar e publicar seu Conector como parte do envio do AppSource ou você pode fornecer aos usuários diretamente para carregar no Teams. [](~/concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="fdb2d-109">Whether as a standalone solution, or one of several [capabilities](~/concepts/extensibility-points.md) that your experience enables in Teams, you can [package](~/concepts/build-and-test/apps-package.md) and [publish](~/concepts/deploy-and-publish/apps-publish.md) your Connector as part of your AppSource submission, or you can provide it to users directly for uploading within Teams.</span></span>

<span data-ttu-id="fdb2d-110">Para distribuir seu Conector, você precisa se registrar usando o Painel do Desenvolvedor [de Conectores.](https://outlook.office.com/connectors/home/login/#/publish)</span><span class="sxs-lookup"><span data-stu-id="fdb2d-110">To distribute your Connector, you need to register by using the [Connectors Developer Dashboard](https://outlook.office.com/connectors/home/login/#/publish).</span></span> <span data-ttu-id="fdb2d-111">Por padrão, depois que um Conector é registrado, presume-se que seu Conector funcionará em todos os produtos do Office 365 que os suportam, incluindo Outlook e Teams.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-111">By default, once a Connector is registered, it's assumed that your Connector will work in all Office 365 products that support them, including Outlook and Teams.</span></span> <span data-ttu-id="fdb2d-112">Se esse não _for o_ caso e você precisar criar um Conector que funcione apenas no Microsoft Teams, entre em contato conosco diretamente em Envios de [Aplicativos do Microsoft Teams.](mailto:teamsubm@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="fdb2d-112">If that is _not_ the case and you need to create a Connector that only works in Microsoft Teams, contact us directly at [Microsoft Teams App Submissions](mailto:teamsubm@microsoft.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fdb2d-113">Depois de escolher **Salvar** no Painel do Desenvolvedor de Conectores, seu Conector será registrado.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-113">After you choose **Save** in the Connectors Developer Dashboard, your Connector is registered.</span></span> <span data-ttu-id="fdb2d-114">Se você quiser publicar seu Conector no AppSource, siga as instruções em Publicar seu [aplicativo do Microsoft Teams no AppSource](~/concepts/deploy-and-publish/apps-publish.md).</span><span class="sxs-lookup"><span data-stu-id="fdb2d-114">If you want to publish your Connector in AppSource, follow the instructions in [Publish your Microsoft Teams app to AppSource](~/concepts/deploy-and-publish/apps-publish.md).</span></span> <span data-ttu-id="fdb2d-115">Se você não quiser publicar seu aplicativo no AppSource e, em vez disso, simplesmente distribuí-lo diretamente para sua organização, você pode fazer isso publicando em [sua organização.](#publish-connectors-for-your-organization)</span><span class="sxs-lookup"><span data-stu-id="fdb2d-115">If you do not wish to publish your app in AppSource, and rather simply distribute it directly to your organization only, you can do so by [publishing to your organization](#publish-connectors-for-your-organization).</span></span> <span data-ttu-id="fdb2d-116">Se você quiser apenas publicar em sua organização, nenhuma ação será necessária no painel conector.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-116">If you only want to publish to your organization, no further action is necessary on the Connector dashboard.</span></span>

### <a name="integrating-the-configuration-experience"></a><span data-ttu-id="fdb2d-117">Integrando a experiência de configuração</span><span class="sxs-lookup"><span data-stu-id="fdb2d-117">Integrating the configuration experience</span></span>

<span data-ttu-id="fdb2d-118">Seus usuários concluirão toda a experiência de configuração do Conector sem precisar sair do cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-118">Your users will complete the entire Connector configuration experience without having to leave the Teams client.</span></span> <span data-ttu-id="fdb2d-119">Para atingir essa experiência, o Teams incorporará sua página de configuração diretamente em um iframe.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-119">To achieve this experience, Teams will embed your configuration page directly within an iframe.</span></span> <span data-ttu-id="fdb2d-120">A sequência de operações é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="fdb2d-120">The sequence of operations is as follows:</span></span>

1. <span data-ttu-id="fdb2d-121">O usuário clica no conector para iniciar o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-121">The user clicks on your connector to begin the configuration process.</span></span>
2. <span data-ttu-id="fdb2d-122">O Teams carregará sua experiência de configuração em linha.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-122">Teams will load your configuration experience in line.</span></span>
3. <span data-ttu-id="fdb2d-123">O usuário interage com sua experiência da Web para concluir a configuração.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-123">The user interacts with your web experience to complete the configuration.</span></span>
4. <span data-ttu-id="fdb2d-124">O usuário pressiona "Salvar", que dispara um retorno de chamada em seu código.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-124">The user presses "Save", which triggers a callback in your code.</span></span>
5. <span data-ttu-id="fdb2d-125">Seu código processará o evento save recuperando as configurações de webhook (documentadas abaixo).</span><span class="sxs-lookup"><span data-stu-id="fdb2d-125">Your code will process the save event by retrieving the webhook settings (documented below).</span></span> <span data-ttu-id="fdb2d-126">Em seguida, seu código deve armazenar o webhook para postar eventos posteriormente.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-126">Your code should then store the webhook to post events later.</span></span>

<span data-ttu-id="fdb2d-127">Você pode reutilizar sua experiência de configuração da Web existente ou criar uma versão separada para ser hospedada especificamente no Teams.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-127">You can reuse your existing web configuration experience or create a separate version to be hosted specifically in Teams.</span></span> <span data-ttu-id="fdb2d-128">Seu código deve:</span><span class="sxs-lookup"><span data-stu-id="fdb2d-128">Your code should:</span></span>

1. <span data-ttu-id="fdb2d-129">Inclua o SDK JavaScript do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-129">Include the Microsoft Teams JavaScript SDK.</span></span> <span data-ttu-id="fdb2d-130">Isso fornece acesso de código a APIs para executar operações comuns, como obter o contexto atual de usuário/canal/equipe e iniciar fluxos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-130">This gives your code access to APIs to perform common operations like getting the current user/channel/team context and initiating authentication flows.</span></span> <span data-ttu-id="fdb2d-131">Inicializar o SDK chamando `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="fdb2d-131">Initialize the SDK by calling `microsoftTeams.initialize()`.</span></span>
2. <span data-ttu-id="fdb2d-132">Chame `microsoftTeams.settings.setValidityState(true)` quando quiser habilitar o botão Salvar.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-132">Call `microsoftTeams.settings.setValidityState(true)` when you want to enable the Save button.</span></span> <span data-ttu-id="fdb2d-133">Você deve fazer isso como uma resposta à entrada de usuário válida, como uma seleção ou uma atualização de campo.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-133">You should do this as a response to valid user input, such as a selection or field update.</span></span>
3. <span data-ttu-id="fdb2d-134">Registre `microsoftTeams.settings.registerOnSaveHandler()` um manipulador de eventos, que é chamado quando o usuário clica em Salvar.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-134">Register a `microsoftTeams.settings.registerOnSaveHandler()` event handler, which gets called when the user clicks Save.</span></span>
4. <span data-ttu-id="fdb2d-135">Chame `microsoftTeams.settings.setSettings()` para salvar as configurações do conector.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-135">Call `microsoftTeams.settings.setSettings()` to save the connector settings.</span></span> <span data-ttu-id="fdb2d-136">O que é salvo aqui também é o que será mostrado na caixa de diálogo de configuração se o usuário tentar atualizar uma configuração existente para o conector.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-136">What's saved here is also what will be shown in the configuration dialog if the user tries to update an existing configuration for your connector.</span></span>
5. <span data-ttu-id="fdb2d-137">Chame `microsoftTeams.settings.getSettings()` para buscar propriedades de webhook, incluindo a PRÓPRIA URL.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-137">Call `microsoftTeams.settings.getSettings()` to fetch webhook properties, including the URL itself.</span></span> <span data-ttu-id="fdb2d-138">Você deve chamar isso Além de durante o evento save, você também deve chamar isso quando sua página for carregada pela primeira vez no caso de uma nova configuração.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-138">You should call this  In addition to during the save event, you should also call this when your page is first loaded in the case of a re-configuration.</span></span>
6. <span data-ttu-id="fdb2d-139">(Opcional) Registre `microsoftTeams.settings.registerOnRemoveHandler()` um manipulador de eventos, que é chamado quando o usuário remove o conector.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-139">(Optional) Register a `microsoftTeams.settings.registerOnRemoveHandler()` event handler, which gets called when the user removes your connector.</span></span> <span data-ttu-id="fdb2d-140">Esse evento oferece ao seu serviço a oportunidade de executar qualquer ação de limpeza.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-140">This event gives your service an opportunity to perform any cleanup actions.</span></span>

<span data-ttu-id="fdb2d-141">Aqui está um HTML de exemplo para criar uma página de configuração do Conector sem o CSS:</span><span class="sxs-lookup"><span data-stu-id="fdb2d-141">Here's a sample HTML to create a Connector configuration page without the CSS:</span></span>

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
            var removeCalled = true;
            alert("Removed" + JSON.stringify(removeEvent));
        });

</script>
```

#### <a name="getsettings-response-properties"></a><span data-ttu-id="fdb2d-142">`GetSettings()` propriedades de resposta</span><span class="sxs-lookup"><span data-stu-id="fdb2d-142">`GetSettings()` response properties</span></span>

>[!Note]
><span data-ttu-id="fdb2d-143">Os parâmetros retornados pela chamada aqui são diferentes do que se você fosse invocar esse método de uma guia e diferir daqueles `getSettings` documentados [aqui](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="fdb2d-143">The parameters returned by the `getSettings` call here are different than if you were to invoke this method from a tab, and differ from those documented [here](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true).</span></span>

| <span data-ttu-id="fdb2d-144">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="fdb2d-144">Parameter</span></span>   | <span data-ttu-id="fdb2d-145">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fdb2d-145">Details</span></span> |
|-------------|---------|
| `entityId`       | <span data-ttu-id="fdb2d-146">A ID da entidade, conforme definido pelo código ao chamar `setSettings()` .</span><span class="sxs-lookup"><span data-stu-id="fdb2d-146">The entity ID, as set by your code when calling `setSettings()`.</span></span> |
| `configName`  | <span data-ttu-id="fdb2d-147">O nome da configuração, conforme definido pelo código ao chamar `setSettings()` .</span><span class="sxs-lookup"><span data-stu-id="fdb2d-147">The configuration name, as set by your code when calling `setSettings()`.</span></span> |
| `contentUrl` | <span data-ttu-id="fdb2d-148">A URL da página de configuração, conforme definido pelo código ao chamar `setSettings()`</span><span class="sxs-lookup"><span data-stu-id="fdb2d-148">The URL of the configuration page, as set by your code when calling `setSettings()`</span></span> |
| `webhookUrl` | <span data-ttu-id="fdb2d-149">A URL de webhook criada para esse conector.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-149">The webhook URL created for this connector.</span></span> <span data-ttu-id="fdb2d-150">Persista a URL do webhook e use-a para POSTAR JSON estruturado para enviar cartões para o canal.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-150">Persist the webhook URL and use it to POST structured JSON to send cards to the channel.</span></span> <span data-ttu-id="fdb2d-151">A `webhookUrl` é retornada quando o aplicativo retorna com êxito.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-151">The `webhookUrl` is returned only when application returns successfully.</span></span> |
| `appType` | <span data-ttu-id="fdb2d-152">Os valores retornados podem ser `mail`, `groups` ou `teams` correspondente ao Email do Office 365, Grupos do Office 365 ou Microsoft Teams respectivamente.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-152">The values returned can be `mail`, `groups` or `teams` corresponding to the Office 365 Mail, Office 365 Groups or Microsoft Teams respectively.</span></span> |
| `userObjectId` | <span data-ttu-id="fdb2d-153">Esta é a id exclusiva correspondente ao usuário do Office 365 que iniciou a instalação do conector.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-153">This is the unique id corresponding to the Office 365 user who initiated setup of the connector.</span></span> <span data-ttu-id="fdb2d-154">Ela deve ser protegida.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-154">It should be secured.</span></span> <span data-ttu-id="fdb2d-155">Este valor pode ser usado para associar o usuário no Office 365 que realizou a configuração para o usuário no seu serviço.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-155">This value can be used to associate the user in Office 365 who set up the configuration to the user in your service.</span></span> |

<span data-ttu-id="fdb2d-156">Se você precisar autenticar o usuário como parte do carregamento de sua página na etapa 2 acima, consulte este [link](~/tabs/how-to/authentication/auth-flow-tab.md) para obter detalhes sobre como você pode integrar o logon quando sua página é incorporada.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-156">If you need to authenticate the user as part of loading your page in step 2 above, refer to [this link](~/tabs/how-to/authentication/auth-flow-tab.md) for details on how you can integrate login when your page is embedded.</span></span>

> [!NOTE]
> <span data-ttu-id="fdb2d-157">Devido a motivos de compatibilidade entre clientes, seu código precisará chamar com a URL e os métodos de retorno de chamada de `microsoftTeams.authentication.registerAuthenticationHandlers()` sucesso/falha antes de chamar `authenticate()` .</span><span class="sxs-lookup"><span data-stu-id="fdb2d-157">Due to cross-client compatibility reasons, your code will need to call `microsoftTeams.authentication.registerAuthenticationHandlers()` with the URL and success/failure callback methods before calling `authenticate()`.</span></span>

#### <a name="handling-edits"></a><span data-ttu-id="fdb2d-158">Manipulando edições</span><span class="sxs-lookup"><span data-stu-id="fdb2d-158">Handling edits</span></span>

<span data-ttu-id="fdb2d-159">Seu código deve manipular os usuários que retornam para editar uma configuração de conector existente.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-159">Your code should handle users returning to edit an existing connector configuration.</span></span> <span data-ttu-id="fdb2d-160">Para fazer isso, chame `microsoftTeams.settings.setSettings()` durante a configuração inicial com os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="fdb2d-160">To do this, call `microsoftTeams.settings.setSettings()` during the initial configuration with the following parameters:</span></span>

- <span data-ttu-id="fdb2d-161">`entityId` é a ID personalizada que é compreendida pelo seu serviço e representa o que o usuário configurou.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-161">`entityId` is the custom ID that is understood by your service and represents what the user has configured.</span></span>
- <span data-ttu-id="fdb2d-162">`configName` é um nome amigável que seu código de configuração pode recuperar</span><span class="sxs-lookup"><span data-stu-id="fdb2d-162">`configName` is a friendly name that your configuration code can retrieve</span></span>
- <span data-ttu-id="fdb2d-163">`contentUrl` é uma URL personalizada que é carregada quando um usuário edita uma configuração de conector existente.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-163">`contentUrl` is a custom URL that gets loaded when a user edits an existing connector configuration.</span></span> <span data-ttu-id="fdb2d-164">Você pode usar essa URL para facilitar o seu código lidar com o caso de edição.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-164">You can use this URL to make it easier for your code to handle the edit case.</span></span>

<span data-ttu-id="fdb2d-165">Normalmente, essa chamada é feita como parte do manipulador de eventos save.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-165">Typically, this call is made as part of your save event handler.</span></span> <span data-ttu-id="fdb2d-166">Em seguida, quando o acima for carregado, seu código deverá chamar para pré-estipular quaisquer configurações ou formulários na interface do usuário `contentUrl` `getSettings()` de configuração.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-166">Then, when the `contentUrl` above is loaded, your code should call `getSettings()` to prepopulate any settings or forms in your configuration UI.</span></span>

#### <a name="handling-removals"></a><span data-ttu-id="fdb2d-167">Manipulando remoções</span><span class="sxs-lookup"><span data-stu-id="fdb2d-167">Handling removals</span></span>

<span data-ttu-id="fdb2d-168">Opcionalmente, você pode executar um manipulador de eventos quando o usuário remover uma configuração de conector existente.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-168">You can optionally execute an event handler when the user removes an existing connector configuration.</span></span> <span data-ttu-id="fdb2d-169">Você registra esse manipulador chamando `microsoftTeams.settings.registerOnRemoveHandler()` .</span><span class="sxs-lookup"><span data-stu-id="fdb2d-169">You register this handler by calling `microsoftTeams.settings.registerOnRemoveHandler()`.</span></span> <span data-ttu-id="fdb2d-170">Esse manipulador pode ser usado para executar operações de limpeza, como a remoção de entradas de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-170">This handler can be used to perform cleanup operations such as removing entries from a database.</span></span>

### <a name="including-the-connector-in-your-manifest"></a><span data-ttu-id="fdb2d-171">Incluindo o Conector em seu Manifesto</span><span class="sxs-lookup"><span data-stu-id="fdb2d-171">Including the Connector in your Manifest</span></span>

<span data-ttu-id="fdb2d-172">Você pode baixar o manifesto do aplicativo do Teams gerado automaticamente no portal.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-172">You can download the auto-generated Teams app manifest from the portal.</span></span> <span data-ttu-id="fdb2d-173">Antes de usá-lo para testar ou publicar seu aplicativo, você deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fdb2d-173">Before you can use it to test or publish your app, though, you must do the following:</span></span>

- <span data-ttu-id="fdb2d-174">[Incluir dois ícones](../../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="fdb2d-174">[Include two icons](../../concepts/build-and-test/apps-package.md#app-icons).</span></span>
- <span data-ttu-id="fdb2d-175">Modifique a parte dos `icons` do manifesto para se referir aos nomes de arquivo dos ícones em vez das URLs.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-175">Modify the `icons` portion of the manifest to refer to the file names of the icons instead of URLs.</span></span>

<span data-ttu-id="fdb2d-176">O seguinte arquivo manifest.json contém os elementos básicos necessários para testar e enviar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-176">The following manifest.json file contains the basic elements needed to test and submit your app.</span></span>

> [!NOTE]
> <span data-ttu-id="fdb2d-177">Substitua `id` e `connectorId` no exemplo a seguir pelo GUID do Conector.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-177">Replace `id` and `connectorId` in the following example with the GUID of your Connector.</span></span>

#### <a name="example-manifestjson-with-connector"></a><span data-ttu-id="fdb2d-178">Exemplo de manifest.json com o Conector</span><span class="sxs-lookup"><span data-stu-id="fdb2d-178">Example manifest.json with Connector</span></span>

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

## <a name="testing-your-connector"></a><span data-ttu-id="fdb2d-179">Testar o Conector</span><span class="sxs-lookup"><span data-stu-id="fdb2d-179">Testing your Connector</span></span>

<span data-ttu-id="fdb2d-180">Para testar o Conector, carregue-o em uma equipe, como em qualquer outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-180">To test your Connector, upload it to a team as you would with any other app.</span></span> <span data-ttu-id="fdb2d-181">Você pode criar um pacote .zip usando o arquivo de manifesto do Painel do Desenvolvedor do Connectors (modificado conforme indicado na seção anterior) e os dois arquivos de ícone.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-181">You can create a .zip package using the manifest file from the Connectors Developer Dashboard (modified as directed in the preceding section) and the two icon files.</span></span>

<span data-ttu-id="fdb2d-182">Depois de carregar o aplicativo, abra a lista de conectores em qualquer canal.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-182">After you upload the app, open the Connectors list from any channel.</span></span> <span data-ttu-id="fdb2d-183">Role até a parte inferior para ver o aplicativo na seção **Carregado**.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-183">Scroll to the bottom to see your app in the **Uploaded** section.</span></span>

![Captura de tela da seção carregada na caixa de diálogo do Conector](~/assets/images/connectors/connector_dialog_uploaded.png)

<span data-ttu-id="fdb2d-185">Agora você pode iniciar a experiência de configuração.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-185">You can now launch the configuration experience.</span></span> <span data-ttu-id="fdb2d-186">Esteja ciente de que esse fluxo ocorre inteiramente dentro do Microsoft Teams como uma experiência hospedada.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-186">Be aware that this flow occurs entirely within Microsoft Teams as a hosted experience.</span></span>

<span data-ttu-id="fdb2d-187">Para verificar se uma `HttpPOST` ação está funcionando corretamente, [envie mensagens para seu conector](~/webhooks-and-connectors/how-to/connectors-using.md).</span><span class="sxs-lookup"><span data-stu-id="fdb2d-187">To verify that an `HttpPOST` action is working correctly, [send messages to your connector](~/webhooks-and-connectors/how-to/connectors-using.md).</span></span>

## <a name="publish-connectors-for-your-organization"></a><span data-ttu-id="fdb2d-188">Publicar Conectores para sua organização</span><span class="sxs-lookup"><span data-stu-id="fdb2d-188">Publish Connectors for your organization</span></span>

<span data-ttu-id="fdb2d-189">Às vezes, talvez você não queira publicar seu aplicativo conector na AppSource/Store pública, mas gostaria que ele fosse disponibilizado apenas para os usuários em sua organização.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-189">Sometimes, you may not want to publish your connector app to the public AppSource/Store but would like it to be available only to the users in your organization.</span></span> <span data-ttu-id="fdb2d-190">Nesses casos, você pode carregar seu aplicativo de conector personalizado no Catálogo de [Aplicativos da sua organização.](~/concepts/deploy-and-publish/apps-publish.md)</span><span class="sxs-lookup"><span data-stu-id="fdb2d-190">In such cases, you can upload your custom connector app to your [organization's App Catalog](~/concepts/deploy-and-publish/apps-publish.md).</span></span> <span data-ttu-id="fdb2d-191">Dessa forma, seu aplicativo conector estará disponível apenas para essa organização e você não precisará publicar seu conector no armazenamento público.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-191">This way, your connector app will be available only to that organization, and you will not need to publish your connector to the public store.</span></span>

<span data-ttu-id="fdb2d-192">Depois de carregar seu pacote de aplicativos, para configurar e usar o conector em uma Equipe, ele pode ser instalado no catálogo de aplicativos da organização seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="fdb2d-192">Once you've uploaded your app package, to configure and use the connector in a Team it can be installed from the organization's app catalog by following these steps:</span></span>

1. <span data-ttu-id="fdb2d-193">Selecione o ícone de aplicativos na barra de navegação vertical extrema esquerda.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-193">Select the apps icon from the far left vertical navigation bar.</span></span>
1. <span data-ttu-id="fdb2d-194">Na janela **Aplicativos,** selecione **Conectores**.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-194">In the **Apps** window select **Connectors**.</span></span>
1. <span data-ttu-id="fdb2d-195">Selecione o conector que você deseja adicionar e uma janela de diálogo pop-up será exibida.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-195">Select the connector that you want to add and a pop-up dialog window will display.</span></span>
1. <span data-ttu-id="fdb2d-196">Selecione a **barra Adicionar a uma equipe.**</span><span class="sxs-lookup"><span data-stu-id="fdb2d-196">Select the **Add to a team** bar.</span></span>
1. <span data-ttu-id="fdb2d-197">Na próxima janela de diálogo, digite um nome de equipe ou canal.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-197">In the next dialog window type a team or channel name.</span></span>
1. <span data-ttu-id="fdb2d-198">Selecione a **barra Configurar um conector** no canto inferior direito da janela de diálogo.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-198">Select the **Set up a connector** bar from the bottom right corner of dialog window.</span></span>
1. <span data-ttu-id="fdb2d-199">O conector estará disponível na seção &#9679;&#9679;&#9679; => *Mais* opções Conectores Todos os Conectores para você  =>    =>    =>  *equipe* para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-199">The connector will be available in the  section &#9679;&#9679;&#9679; => *More options* => *Connectors* => *All* => *Connectors for you team* for that team.</span></span> <span data-ttu-id="fdb2d-200">Você pode navegar rolando até esta seção ou pesquisar o aplicativo do conector.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-200">You can navigate by scrolling to this section or search for the connector app.</span></span>
1. <span data-ttu-id="fdb2d-201">Para configurar ou modificar o conector, selecione a **barra Configurar.**</span><span class="sxs-lookup"><span data-stu-id="fdb2d-201">To configure or modify the connector select the **Configure** bar.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fdb2d-202">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="fdb2d-202">Code sample</span></span>
|<span data-ttu-id="fdb2d-203">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="fdb2d-203">**Sample name**</span></span> | <span data-ttu-id="fdb2d-204">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="fdb2d-204">**Description**</span></span> | <span data-ttu-id="fdb2d-205">**.NET**</span><span class="sxs-lookup"><span data-stu-id="fdb2d-205">**.NET**</span></span> | <span data-ttu-id="fdb2d-206">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="fdb2d-206">**Node.js**</span></span> |
|----------------|------------------|--------|----------------|
| <span data-ttu-id="fdb2d-207">Conectores</span><span class="sxs-lookup"><span data-stu-id="fdb2d-207">Connectors</span></span>    | <span data-ttu-id="fdb2d-208">Exemplo do Conector do Office 365 gerando notificações para o canal do Teams.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-208">Sample Office 365 Connector generating notifications to teams channel.</span></span>|   [<span data-ttu-id="fdb2d-209">View</span><span class="sxs-lookup"><span data-stu-id="fdb2d-209">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [<span data-ttu-id="fdb2d-210">View</span><span class="sxs-lookup"><span data-stu-id="fdb2d-210">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| <span data-ttu-id="fdb2d-211">Exemplo de conectores genéricos</span><span class="sxs-lookup"><span data-stu-id="fdb2d-211">Generic connectors sample</span></span> |<span data-ttu-id="fdb2d-212">Exemplo de código para um conector genérico que é fácil de personalizar para qualquer sistema que oferece suporte a webhooks.</span><span class="sxs-lookup"><span data-stu-id="fdb2d-212">Sample code for a generic connector that's easy to customize for any system which supports webhooks.</span></span>|  | [<span data-ttu-id="fdb2d-213">View</span><span class="sxs-lookup"><span data-stu-id="fdb2d-213">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|
