---
title: Referência do esquema de Manifesto de Visualização do Desenvolvedor
description: Descreve o esquema suportado pelo manifesto para Microsoft Teams
ms.topic: reference
keywords: Teams manifest schema Developer Preview
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: c2009038341a22664b0f055fa9756a9d1eba87b9
ms.sourcegitcommit: 64c1cf2a268ef101a519bc31d171618d0f6cd12a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2021
ms.locfileid: "52915087"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="94ba3-104">Esquema de manifesto de visualização do desenvolvedor para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="94ba3-104">Developer preview manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="94ba3-105">Para obter informações sobre como habilitar a visualização do desenvolvedor, consulte [visualização do](~/resources/dev-preview/developer-preview-intro.md)desenvolvedor público para Microsoft Teams .</span><span class="sxs-lookup"><span data-stu-id="94ba3-105">For information on how to enable developer preview, see [public developer preview for Microsoft Teams](~/resources/dev-preview/developer-preview-intro.md).</span></span>

> [!NOTE]
> * <span data-ttu-id="94ba3-106">Se você não estiver usando recursos de visualização do desenvolvedor, use o manifesto [do aplicativo para recursos GA.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="94ba3-106">If you aren't using developer preview features, use the [app manifest for GA features](~/resources/schema/manifest-schema.md) instead.</span></span>

<span data-ttu-id="94ba3-107">O Microsoft Teams descreve como o aplicativo se integra ao Microsoft Teams produto.</span><span class="sxs-lookup"><span data-stu-id="94ba3-107">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="94ba3-108">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="94ba3-108">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="94ba3-109">Para obter mais informações sobre os recursos disponíveis, consulte: [Recursos na Visualização](~/resources/dev-preview/developer-preview-features.md)do Desenvolvedor Público para Microsoft Teams .</span><span class="sxs-lookup"><span data-stu-id="94ba3-109">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="94ba3-110">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="94ba3-110">Sample full manifest</span></span>

```json
{
  "$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
  "manifestVersion": "devPreview",
  "version": "1.0.0",
  "id": "%MICROSOFT-APP-ID%",
  "packageName": "com.example.myapp",
  "devicePermissions" : [ "geolocation", "media" ],
  "developer": {
    "name": "Publisher Name",
    "websiteUrl": "https://website.com/",
    "privacyUrl": "https://website.com/privacy",
    "termsOfUseUrl": "https://website.com/app-tos",
    "mpnId": "1234567890"
  },
  "localizationInfo": {
    "defaultLanguageTag": "es-es",
    "additionalLanguages": [
      {
        "languageTag": "en-us",
        "file": "en-us.json"
      }
    ]
  },
  "name": {
    "short": "Name of your app (<=30 chars)",
    "full": "Full name of app, if longer than 30 characters"
  },
  "description": {
    "short": "Short description of your app",
    "full": "Full description of your app"
  },
  "icons": {
    "outline": "%FILENAME-32x32px%",
    "color": "%FILENAME-192x192px"
  },
  "accentColor": "%HEX-COLOR%",
  "configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [ "team", "groupchat" ]
    }
  ],
  "staticTabs": [
    {
      "entityId": "idForPage",
      "name": "Display name of tab",
      "contentUrl": "https://contoso.com/content?host=msteams",
      "contentBotId": "Specifies to the app that tab is an Adaptive Card Tab. You can either provide the contentBotId or contentUrl.",
      "websiteUrl": "https://contoso.com/content",
      "scopes": [ "personal" ]
    }
  ],
  "bots": [
    {
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "needsChannelSelector": false,
      "isNotificationOnly": false,
      "scopes": [ "team", "personal", "groupchat" ],
      "supportsFiles": true,
      "commandLists": [
        {
          "scopes": [ "team", "groupchat" ],
          "commands": [
            {
              "title": "Command 1",
              "description": "Description of Command 1"
            },
            {
              "title": "Command N",
              "description": "Description of Command N"
            }
          ]
        },
        {
          "scopes": [ "personal", "groupchat" ],
          "commands": [
            {
              "title": "Personal command 1",
              "description": "Description of Personal command 1"
            },
            {
              "title": "Personal command N",
              "description": "Description of Personal command N"
            }
          ]
        }
      ]
    }
  ],
  "connectors": [
    {
      "connectorId": "GUID-FROM-CONNECTOR-DEV-PORTAL%",
      "configurationUrl": "https://contoso.com/teamsconnector/configure",
      "scopes": [ "team"]
    }
  ],
  "composeExtensions": [
    {
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "canUpdateConfiguration": true,
      "commands": [
        {
          "id": "exampleCmd1",
          "title": "Example Command",
          "description": "Command Description; e.g., Search on the web",
          "initialRun": true,
          "type" : "search",
          "context" : ["compose", "commandBox"],
          "parameters": [
            {
              "name": "keyword",
              "title": "Search keywords",
              "description": "Enter the keywords to search for"
            }
          ]
        },
        {
          "id": "exampleCmd2",
          "title": "Example Command 2",
          "description": "Command Description; e.g., Search for a customer",
          "initialRun": true,
          "type" : "action",
          "fetchTask" : true,
          "context" : ["message"],
          "parameters": [
            {
              "name": "custinfo",
              "title": "Customer name",
              "description": "Enter a customer name",
              "inputType" : "text"
            }
          ]
        },
        {
          "id": "exampleMessageHandler",
          "title": "Message Handler",
          "description": "Domains that will create a preview when pasted into the compose box",
          "messageHandlers": [
            {
              "type" : "link",
              "value" : {
                "domains" : [
                  "mysite.someplace.com",
                  "othersite.someplace.com"
                ]
              }
            }
          ]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers",
  ],
  "validDomains": [
     "contoso.com",
     "mysite.someplace.com",
     "othersite.someplace.com"
  ],
  "webApplicationInfo": {
    "id": "AAD App ID",
    "resource": "Resource URL for acquiring auth token for SSO",
    "applicationPermissions": [
      "TeamSettings.Read.Group",
      "ChannelSettings.Read.Group",
      "ChannelSettings.Edit.Group",
      "Channel.Create.Group",
      "Channel.Delete.Group",
      "ChannelMessage.Read.Group",
      "TeamsApp.Read.Group",
      "TeamsTab.Read.Group",
      "TeamsTab.Create.Group",
      "TeamsTab.Edit.Group",
      "TeamsTab.Delete.Group",
      "Member.Read.Group",
      "Owner.Read.Group",
      "Member.ReadWrite.Group",
      "Owner.ReadWrite.Group"
    ],
  },
   "configurableProperties": [
     "name",
     "shortDescription",
     "longDescription",
     "smallImageUrl", 
     "largeImageUrl", 
     "accentColor",
     "developerUrl",
     "privacyUrl",
     "termsOfUseUrl"        
  ],
  "defaultInstallScope": "meetings",
  "defaultGroupCapability": {
    "meetings": "tab", 
    "team": "bot", 
    "groupchat": "bot"
  }
}
```

<span data-ttu-id="94ba3-111">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="94ba3-111">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="94ba3-112">$schema</span><span class="sxs-lookup"><span data-stu-id="94ba3-112">$schema</span></span>

<span data-ttu-id="94ba3-113">*Opcional, mas recomendado* &ndash; Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-113">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="94ba3-114">A https:// URL de referência do Esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="94ba3-114">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="94ba3-115">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="94ba3-115">manifestVersion</span></span>

<span data-ttu-id="94ba3-116">**Obrigatório** &ndash; Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-116">**Required** &ndash; String</span></span>

<span data-ttu-id="94ba3-117">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="94ba3-117">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="94ba3-118">Deve ser "devPreview".</span><span class="sxs-lookup"><span data-stu-id="94ba3-118">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="94ba3-119">versão</span><span class="sxs-lookup"><span data-stu-id="94ba3-119">version</span></span>

<span data-ttu-id="94ba3-120">**Obrigatório** &ndash; Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-120">**Required** &ndash; String</span></span>

<span data-ttu-id="94ba3-121">A versão do aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="94ba3-121">The version of the specific app.</span></span> <span data-ttu-id="94ba3-122">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="94ba3-122">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="94ba3-123">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="94ba3-123">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="94ba3-124">Se esse aplicativo foi enviado para a loja, o novo manifesto terá que ser re-enviado e validado.</span><span class="sxs-lookup"><span data-stu-id="94ba3-124">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="94ba3-125">Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, depois que ele for aprovado.</span><span class="sxs-lookup"><span data-stu-id="94ba3-125">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="94ba3-126">Se as permissões solicitadas pelo aplicativo mudarem, os usuários serão solicitados a atualizar e consentir de novo no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-126">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="94ba3-127">Esta cadeia de caracteres de versão deve seguir o padrão [de semver](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="94ba3-127">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="94ba3-128">id</span><span class="sxs-lookup"><span data-stu-id="94ba3-128">id</span></span>

<span data-ttu-id="94ba3-129">**Obrigatório** &ndash; ID do aplicativo Microsoft</span><span class="sxs-lookup"><span data-stu-id="94ba3-129">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="94ba3-130">O identificador exclusivo gerado pela Microsoft para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-130">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="94ba3-131">Se você tiver registrado um bot por meio do Microsoft Bot Framework, ou o aplicativo Web da guia já estiver entrando com a Microsoft, você já deve ter uma ID e deve insira-a aqui.</span><span class="sxs-lookup"><span data-stu-id="94ba3-131">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="94ba3-132">Caso contrário, você deve gerar uma nova ID no Portal de Registro de Aplicativos da Microsoft ([Meus](https://apps.dev.microsoft.com)Aplicativos ), insira-o aqui e, em seguida, reutiliza-o quando você [adiciona um bot](~/bots/how-to/create-a-bot-for-teams.md).</span><span class="sxs-lookup"><span data-stu-id="94ba3-132">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="94ba3-133">packageName</span><span class="sxs-lookup"><span data-stu-id="94ba3-133">packageName</span></span>

<span data-ttu-id="94ba3-134">**Obrigatório** &ndash; Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-134">**Required** &ndash; String</span></span>

<span data-ttu-id="94ba3-135">Um identificador exclusivo para este aplicativo na notação de domínio reverso; por exemplo, com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="94ba3-135">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="94ba3-136">developer</span><span class="sxs-lookup"><span data-stu-id="94ba3-136">developer</span></span>

<span data-ttu-id="94ba3-137">**Required**</span><span class="sxs-lookup"><span data-stu-id="94ba3-137">**Required**</span></span>

<span data-ttu-id="94ba3-138">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="94ba3-138">Specifies information about your company.</span></span> <span data-ttu-id="94ba3-139">Para aplicativos enviados ao AppSource (anteriormente Office Store), esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="94ba3-139">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="94ba3-140">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-140">Name</span></span>| <span data-ttu-id="94ba3-141">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-141">Maximum size</span></span> | <span data-ttu-id="94ba3-142">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-142">Required</span></span> | <span data-ttu-id="94ba3-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-143">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="94ba3-144">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-144">32 characters</span></span>|<span data-ttu-id="94ba3-145">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-145">✔</span></span>|<span data-ttu-id="94ba3-146">O nome de exibição do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="94ba3-146">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="94ba3-147">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-147">2048 characters</span></span>|<span data-ttu-id="94ba3-148">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-148">✔</span></span>|<span data-ttu-id="94ba3-149">A https:// URL do site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="94ba3-149">The https:// URL to the developer's website.</span></span> <span data-ttu-id="94ba3-150">Este link deve levar os usuários para a sua empresa ou página de aterrissagem específica do produto.</span><span class="sxs-lookup"><span data-stu-id="94ba3-150">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="94ba3-151">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-151">2048 characters</span></span>|<span data-ttu-id="94ba3-152">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-152">✔</span></span>|<span data-ttu-id="94ba3-153">A https:// URL da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="94ba3-153">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="94ba3-154">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-154">2048 characters</span></span>|<span data-ttu-id="94ba3-155">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-155">✔</span></span>|<span data-ttu-id="94ba3-156">A https:// URL dos termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="94ba3-156">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="94ba3-157">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-157">10 characters</span></span>|<span data-ttu-id="94ba3-158">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-158">✔</span></span>|<span data-ttu-id="94ba3-159">**Opcional** A ID da Rede de Parceiros da Microsoft que identifica a organização do parceiro que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-159">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="94ba3-160">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="94ba3-160">localizationInfo</span></span>

<span data-ttu-id="94ba3-161">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="94ba3-161">**Optional**</span></span>

<span data-ttu-id="94ba3-162">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="94ba3-162">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="94ba3-163">Consulte [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="94ba3-163">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="94ba3-164">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-164">Name</span></span>| <span data-ttu-id="94ba3-165">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-165">Maximum size</span></span> | <span data-ttu-id="94ba3-166">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-166">Required</span></span> | <span data-ttu-id="94ba3-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-167">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="94ba3-168">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-168">4 characters</span></span>|<span data-ttu-id="94ba3-169">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-169">✔</span></span>|<span data-ttu-id="94ba3-170">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="94ba3-170">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="94ba3-171">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="94ba3-171">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="94ba3-172">Uma matriz de objetos que especifica traduções de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="94ba3-172">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="94ba3-173">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-173">Name</span></span>| <span data-ttu-id="94ba3-174">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-174">Maximum size</span></span> | <span data-ttu-id="94ba3-175">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-175">Required</span></span> | <span data-ttu-id="94ba3-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-176">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="94ba3-177">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-177">4 characters</span></span>|<span data-ttu-id="94ba3-178">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-178">✔</span></span>|<span data-ttu-id="94ba3-179">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="94ba3-179">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="94ba3-180">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-180">4 characters</span></span>|<span data-ttu-id="94ba3-181">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-181">✔</span></span>|<span data-ttu-id="94ba3-182">Um caminho de arquivo relativo para um arquivo .json que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="94ba3-182">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="94ba3-183">nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-183">name</span></span>

<span data-ttu-id="94ba3-184">**Required**</span><span class="sxs-lookup"><span data-stu-id="94ba3-184">**Required**</span></span>

<span data-ttu-id="94ba3-185">O nome da experiência do aplicativo, exibido para os usuários na Teams experiência.</span><span class="sxs-lookup"><span data-stu-id="94ba3-185">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="94ba3-186">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="94ba3-186">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="94ba3-187">Os valores de `short` e não devem ser os `full` mesmos.</span><span class="sxs-lookup"><span data-stu-id="94ba3-187">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="94ba3-188">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-188">Name</span></span>| <span data-ttu-id="94ba3-189">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-189">Maximum size</span></span> | <span data-ttu-id="94ba3-190">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-190">Required</span></span> | <span data-ttu-id="94ba3-191">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-191">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="94ba3-192">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-192">30 characters</span></span>|<span data-ttu-id="94ba3-193">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-193">✔</span></span>|<span data-ttu-id="94ba3-194">O nome de exibição curto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-194">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="94ba3-195">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-195">100 characters</span></span>||<span data-ttu-id="94ba3-196">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="94ba3-196">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="94ba3-197">descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-197">description</span></span>

<span data-ttu-id="94ba3-198">**Required**</span><span class="sxs-lookup"><span data-stu-id="94ba3-198">**Required**</span></span>

<span data-ttu-id="94ba3-199">Descreve seu aplicativo para usuários.</span><span class="sxs-lookup"><span data-stu-id="94ba3-199">Describes your app to users.</span></span> <span data-ttu-id="94ba3-200">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="94ba3-200">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="94ba3-201">Verifique se sua descrição descreve com precisão sua experiência e fornece informações para ajudar os clientes em potencial a entender o que sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="94ba3-201">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="94ba3-202">Você também deve observar, na descrição completa, se uma conta externa for necessária para uso.</span><span class="sxs-lookup"><span data-stu-id="94ba3-202">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="94ba3-203">Os valores de `short` e não devem ser os `full` mesmos.</span><span class="sxs-lookup"><span data-stu-id="94ba3-203">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="94ba3-204">Sua breve descrição não deve ser repetida na descrição longa e não deve incluir nenhum outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-204">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="94ba3-205">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-205">Name</span></span>| <span data-ttu-id="94ba3-206">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-206">Maximum size</span></span> | <span data-ttu-id="94ba3-207">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-207">Required</span></span> | <span data-ttu-id="94ba3-208">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-208">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="94ba3-209">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-209">80 characters</span></span>|<span data-ttu-id="94ba3-210">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-210">✔</span></span>|<span data-ttu-id="94ba3-211">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="94ba3-211">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="94ba3-212">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-212">4000 characters</span></span>|<span data-ttu-id="94ba3-213">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-213">✔</span></span>|<span data-ttu-id="94ba3-214">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-214">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="94ba3-215">ícones</span><span class="sxs-lookup"><span data-stu-id="94ba3-215">icons</span></span>

<span data-ttu-id="94ba3-216">**Required**</span><span class="sxs-lookup"><span data-stu-id="94ba3-216">**Required**</span></span>

<span data-ttu-id="94ba3-217">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="94ba3-217">Icons used within the Teams app.</span></span> <span data-ttu-id="94ba3-218">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="94ba3-218">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="94ba3-219">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-219">Name</span></span>| <span data-ttu-id="94ba3-220">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-220">Maximum size</span></span> | <span data-ttu-id="94ba3-221">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-221">Required</span></span> | <span data-ttu-id="94ba3-222">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-222">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="94ba3-223">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-223">2048 characters</span></span>|<span data-ttu-id="94ba3-224">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-224">✔</span></span>|<span data-ttu-id="94ba3-225">Um caminho de arquivo relativo para um ícone de contorno PNG 32x32 transparente.</span><span class="sxs-lookup"><span data-stu-id="94ba3-225">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="94ba3-226">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-226">2048 characters</span></span>|<span data-ttu-id="94ba3-227">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-227">✔</span></span>|<span data-ttu-id="94ba3-228">Um caminho de arquivo relativo para um ícone PNG de cor total 192x192.</span><span class="sxs-lookup"><span data-stu-id="94ba3-228">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="94ba3-229">accentColor</span><span class="sxs-lookup"><span data-stu-id="94ba3-229">accentColor</span></span>

<span data-ttu-id="94ba3-230">**Obrigatório** &ndash; Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-230">**Required** &ndash; String</span></span>

<span data-ttu-id="94ba3-231">Uma cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="94ba3-231">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="94ba3-232">O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-232">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="94ba3-233">configurbleTabs</span><span class="sxs-lookup"><span data-stu-id="94ba3-233">configurableTabs</span></span>

<span data-ttu-id="94ba3-234">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="94ba3-234">**Optional**</span></span>

<span data-ttu-id="94ba3-235">Usado quando a experiência do aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="94ba3-235">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="94ba3-236">As guias configuráveis têm suporte apenas no escopo das equipes e, atualmente, há suporte para apenas uma guia por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-236">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="94ba3-237">O objeto é uma matriz com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-237">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="94ba3-238">Esse bloco é necessário apenas para soluções que fornecem uma solução de guia de canal configurável.</span><span class="sxs-lookup"><span data-stu-id="94ba3-238">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="94ba3-239">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-239">Name</span></span>| <span data-ttu-id="94ba3-240">Tipo</span><span class="sxs-lookup"><span data-stu-id="94ba3-240">Type</span></span>| <span data-ttu-id="94ba3-241">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-241">Maximum size</span></span> | <span data-ttu-id="94ba3-242">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-242">Required</span></span> | <span data-ttu-id="94ba3-243">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-243">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="94ba3-244">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-244">String</span></span>|<span data-ttu-id="94ba3-245">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-245">2048 characters</span></span>|<span data-ttu-id="94ba3-246">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-246">✔</span></span>|<span data-ttu-id="94ba3-247">A https:// URL a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="94ba3-247">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="94ba3-248">Booliano</span><span class="sxs-lookup"><span data-stu-id="94ba3-248">Boolean</span></span>|||<span data-ttu-id="94ba3-249">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="94ba3-249">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="94ba3-250">Padrão: `true`</span><span class="sxs-lookup"><span data-stu-id="94ba3-250">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="94ba3-251">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="94ba3-251">Array of enum</span></span>|<span data-ttu-id="94ba3-252">1</span><span class="sxs-lookup"><span data-stu-id="94ba3-252">1</span></span>|<span data-ttu-id="94ba3-253">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-253">✔</span></span>|<span data-ttu-id="94ba3-254">Atualmente, as guias configuráveis suportam apenas `team` os `groupchat` escopos e.</span><span class="sxs-lookup"><span data-stu-id="94ba3-254">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="94ba3-255">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-255">String</span></span>|<span data-ttu-id="94ba3-256">2048</span><span class="sxs-lookup"><span data-stu-id="94ba3-256">2048</span></span>||<span data-ttu-id="94ba3-257">Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso SharePoint.</span><span class="sxs-lookup"><span data-stu-id="94ba3-257">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="94ba3-258">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="94ba3-258">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="94ba3-259">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="94ba3-259">Array of enum</span></span>|<span data-ttu-id="94ba3-260">1</span><span class="sxs-lookup"><span data-stu-id="94ba3-260">1</span></span>||<span data-ttu-id="94ba3-261">Define como sua guia será disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="94ba3-261">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="94ba3-262">As opções `sharePointFullPage` são e `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="94ba3-262">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="94ba3-263">staticTabs</span><span class="sxs-lookup"><span data-stu-id="94ba3-263">staticTabs</span></span>

<span data-ttu-id="94ba3-264">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="94ba3-264">**Optional**</span></span>

<span data-ttu-id="94ba3-265">Define um conjunto de guias que podem ser "fixados" por padrão, sem que o usuário as adicione manualmente.</span><span class="sxs-lookup"><span data-stu-id="94ba3-265">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="94ba3-266">As guias estáticas declaradas no `personal` escopo são sempre fixadas à experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-266">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="94ba3-267">No momento, as guias estáticas declaradas no `team` escopo não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="94ba3-267">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="94ba3-268">Renderizar guias com Cartões Adaptáveis especificando em `contentBotId` vez de no bloco `contentUrl` **staticTabs.**</span><span class="sxs-lookup"><span data-stu-id="94ba3-268">Render tabs with Adaptive Cards by specifying `contentBotId` instead of `contentUrl` in the **staticTabs** block.</span></span>

<span data-ttu-id="94ba3-269">O objeto é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-269">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="94ba3-270">Esse bloco só é necessário para soluções que fornecem uma solução de tabulação estática.</span><span class="sxs-lookup"><span data-stu-id="94ba3-270">This block is required only for solutions that provide a static tab solution.</span></span>


|<span data-ttu-id="94ba3-271">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-271">Name</span></span>| <span data-ttu-id="94ba3-272">Tipo</span><span class="sxs-lookup"><span data-stu-id="94ba3-272">Type</span></span>| <span data-ttu-id="94ba3-273">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-273">Maximum size</span></span> | <span data-ttu-id="94ba3-274">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-274">Required</span></span> | <span data-ttu-id="94ba3-275">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-275">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="94ba3-276">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-276">String</span></span>|<span data-ttu-id="94ba3-277">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-277">64 characters</span></span>|<span data-ttu-id="94ba3-278">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-278">✔</span></span>|<span data-ttu-id="94ba3-279">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="94ba3-279">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="94ba3-280">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-280">String</span></span>|<span data-ttu-id="94ba3-281">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-281">128 characters</span></span>|<span data-ttu-id="94ba3-282">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-282">✔</span></span>|<span data-ttu-id="94ba3-283">O nome de exibição da guia na interface do canal.</span><span class="sxs-lookup"><span data-stu-id="94ba3-283">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="94ba3-284">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-284">String</span></span>|<span data-ttu-id="94ba3-285">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-285">2048 characters</span></span>|<span data-ttu-id="94ba3-286">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-286">✔</span></span>|<span data-ttu-id="94ba3-287">A https:// URL que aponta para a interface do usuário da entidade a ser exibida na tela Teams.</span><span class="sxs-lookup"><span data-stu-id="94ba3-287">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`contentBotId`|   | | | <span data-ttu-id="94ba3-288">A Microsoft Teams ID do aplicativo especificada para o bot no portal da Estrutura de Bots.</span><span class="sxs-lookup"><span data-stu-id="94ba3-288">The Microsoft Teams app ID specified for the bot in the Bot Framework portal.</span></span> |
|`websiteUrl`|<span data-ttu-id="94ba3-289">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-289">String</span></span>|<span data-ttu-id="94ba3-290">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-290">2048 characters</span></span>||<span data-ttu-id="94ba3-291">A https:// URL para apontar se um usuário optar por exibir em um navegador.</span><span class="sxs-lookup"><span data-stu-id="94ba3-291">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="94ba3-292">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="94ba3-292">Array of enum</span></span>|<span data-ttu-id="94ba3-293">1</span><span class="sxs-lookup"><span data-stu-id="94ba3-293">1</span></span>|<span data-ttu-id="94ba3-294">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-294">✔</span></span>|<span data-ttu-id="94ba3-295">Atualmente, as guias estáticas suportam apenas o escopo, o que significa que ele só pode ser `personal` provisionado como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="94ba3-295">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="94ba3-296">bots</span><span class="sxs-lookup"><span data-stu-id="94ba3-296">bots</span></span>

<span data-ttu-id="94ba3-297">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="94ba3-297">**Optional**</span></span>

<span data-ttu-id="94ba3-298">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="94ba3-298">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="94ba3-299">O objeto é uma matriz (no máximo, apenas 1 elemento atualmente, apenas um bot é permitido por aplicativo) com todos os &mdash; elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-299">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="94ba3-300">Esse bloco só é necessário para soluções que fornecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="94ba3-300">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="94ba3-301">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-301">Name</span></span>| <span data-ttu-id="94ba3-302">Tipo</span><span class="sxs-lookup"><span data-stu-id="94ba3-302">Type</span></span>| <span data-ttu-id="94ba3-303">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-303">Maximum size</span></span> | <span data-ttu-id="94ba3-304">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-304">Required</span></span> | <span data-ttu-id="94ba3-305">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-305">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="94ba3-306">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-306">String</span></span>|<span data-ttu-id="94ba3-307">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-307">64 characters</span></span>|<span data-ttu-id="94ba3-308">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-308">✔</span></span>|<span data-ttu-id="94ba3-309">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="94ba3-309">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="94ba3-310">Isso pode ser o mesmo da ID geral [do aplicativo.](#id)</span><span class="sxs-lookup"><span data-stu-id="94ba3-310">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="94ba3-311">Boolean</span><span class="sxs-lookup"><span data-stu-id="94ba3-311">Boolean</span></span>|||<span data-ttu-id="94ba3-312">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="94ba3-312">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="94ba3-313">Padrão: `false`</span><span class="sxs-lookup"><span data-stu-id="94ba3-313">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="94ba3-314">Boolean</span><span class="sxs-lookup"><span data-stu-id="94ba3-314">Boolean</span></span>|||<span data-ttu-id="94ba3-315">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="94ba3-315">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="94ba3-316">Padrão: `false`</span><span class="sxs-lookup"><span data-stu-id="94ba3-316">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="94ba3-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="94ba3-317">Boolean</span></span>|||<span data-ttu-id="94ba3-318">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="94ba3-318">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="94ba3-319">Padrão: `false`</span><span class="sxs-lookup"><span data-stu-id="94ba3-319">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="94ba3-320">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="94ba3-320">Array of enum</span></span>|<span data-ttu-id="94ba3-321">3</span><span class="sxs-lookup"><span data-stu-id="94ba3-321">3</span></span>|<span data-ttu-id="94ba3-322">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-322">✔</span></span>|<span data-ttu-id="94ba3-323">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="94ba3-323">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="94ba3-324">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="94ba3-324">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="94ba3-325">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="94ba3-325">bots.commandLists</span></span>

<span data-ttu-id="94ba3-326">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="94ba3-326">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="94ba3-327">O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo; você deve definir uma lista de comandos separada para cada escopo que `object` seu bot oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="94ba3-327">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="94ba3-328">Para obter mais informações, consulte [Menus bot](~/bots/how-to/create-a-bot-commands-menu.md).</span><span class="sxs-lookup"><span data-stu-id="94ba3-328">For more information, see [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md).</span></span>

|<span data-ttu-id="94ba3-329">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-329">Name</span></span>| <span data-ttu-id="94ba3-330">Tipo</span><span class="sxs-lookup"><span data-stu-id="94ba3-330">Type</span></span>| <span data-ttu-id="94ba3-331">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-331">Maximum size</span></span> | <span data-ttu-id="94ba3-332">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-332">Required</span></span> | <span data-ttu-id="94ba3-333">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-333">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="94ba3-334">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="94ba3-334">array of enum</span></span>|<span data-ttu-id="94ba3-335">3</span><span class="sxs-lookup"><span data-stu-id="94ba3-335">3</span></span>|<span data-ttu-id="94ba3-336">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-336">✔</span></span>|<span data-ttu-id="94ba3-337">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="94ba3-337">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="94ba3-338">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="94ba3-338">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="94ba3-339">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="94ba3-339">array of objects</span></span>|<span data-ttu-id="94ba3-340">10 </span><span class="sxs-lookup"><span data-stu-id="94ba3-340">10</span></span>|<span data-ttu-id="94ba3-341">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-341">✔</span></span>|<span data-ttu-id="94ba3-342">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="94ba3-342">An array of commands the bot supports:</span></span><br><span data-ttu-id="94ba3-343">`title`: o nome do comando bot (cadeia de caracteres, 32).</span><span class="sxs-lookup"><span data-stu-id="94ba3-343">`title`: the bot command name (string, 32).</span></span><br><span data-ttu-id="94ba3-344">`description`: uma descrição simples ou um exemplo da sintaxe de comando e seu argumento (cadeia de caracteres, 128).</span><span class="sxs-lookup"><span data-stu-id="94ba3-344">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

## <a name="connectors"></a><span data-ttu-id="94ba3-345">conectores</span><span class="sxs-lookup"><span data-stu-id="94ba3-345">connectors</span></span>

<span data-ttu-id="94ba3-346">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="94ba3-346">**Optional**</span></span>

<span data-ttu-id="94ba3-347">O `connectors` bloco define um conector Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-347">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="94ba3-348">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-348">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="94ba3-349">Esse bloco só é necessário para soluções que fornecem um Conector.</span><span class="sxs-lookup"><span data-stu-id="94ba3-349">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="94ba3-350">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-350">Name</span></span>| <span data-ttu-id="94ba3-351">Tipo</span><span class="sxs-lookup"><span data-stu-id="94ba3-351">Type</span></span>| <span data-ttu-id="94ba3-352">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-352">Maximum size</span></span> | <span data-ttu-id="94ba3-353">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-353">Required</span></span> | <span data-ttu-id="94ba3-354">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-354">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="94ba3-355">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-355">String</span></span>|<span data-ttu-id="94ba3-356">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-356">2048 characters</span></span>|<span data-ttu-id="94ba3-357">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-357">✔</span></span>|<span data-ttu-id="94ba3-358">A https:// URL a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="94ba3-358">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="94ba3-359">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-359">String</span></span>|<span data-ttu-id="94ba3-360">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-360">64 characters</span></span>|<span data-ttu-id="94ba3-361">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-361">✔</span></span>|<span data-ttu-id="94ba3-362">Um identificador exclusivo para o Conector que corresponde à sua ID no [Painel do Desenvolvedor de Conectores.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="94ba3-362">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="94ba3-363">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="94ba3-363">Array of enum</span></span>|<span data-ttu-id="94ba3-364">1</span><span class="sxs-lookup"><span data-stu-id="94ba3-364">1</span></span>|<span data-ttu-id="94ba3-365">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-365">✔</span></span>|<span data-ttu-id="94ba3-366">Especifica se o Conector oferece uma experiência no contexto de um canal em um , ou uma experiência com escopo apenas para um `team` usuário individual ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="94ba3-366">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="94ba3-367">Atualmente, apenas o `team` escopo é suportado.</span><span class="sxs-lookup"><span data-stu-id="94ba3-367">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="94ba3-368">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="94ba3-368">composeExtensions</span></span>

<span data-ttu-id="94ba3-369">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="94ba3-369">**Optional**</span></span>

<span data-ttu-id="94ba3-370">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-370">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="94ba3-371">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem funcionando.</span><span class="sxs-lookup"><span data-stu-id="94ba3-371">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="94ba3-372">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-372">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="94ba3-373">Esse bloco só é necessário para soluções que fornecem uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="94ba3-373">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="94ba3-374">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-374">Name</span></span>| <span data-ttu-id="94ba3-375">Tipo</span><span class="sxs-lookup"><span data-stu-id="94ba3-375">Type</span></span> | <span data-ttu-id="94ba3-376">Tamanho Máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-376">Maximum Size</span></span> | <span data-ttu-id="94ba3-377">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-377">Required</span></span> | <span data-ttu-id="94ba3-378">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-378">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="94ba3-379">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-379">String</span></span>|<span data-ttu-id="94ba3-380">64</span><span class="sxs-lookup"><span data-stu-id="94ba3-380">64</span></span>|<span data-ttu-id="94ba3-381">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-381">✔</span></span>|<span data-ttu-id="94ba3-382">A ID de aplicativo exclusiva da Microsoft para o bot que é o suporte à extensão de mensagens, conforme registrado na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="94ba3-382">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="94ba3-383">Isso pode ser o mesmo da ID geral [do aplicativo.](#id)</span><span class="sxs-lookup"><span data-stu-id="94ba3-383">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="94ba3-384">Booliano</span><span class="sxs-lookup"><span data-stu-id="94ba3-384">Boolean</span></span>|||<span data-ttu-id="94ba3-385">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="94ba3-385">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="94ba3-386">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="94ba3-386">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="94ba3-387">Matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="94ba3-387">Array of object</span></span>|<span data-ttu-id="94ba3-388">10 </span><span class="sxs-lookup"><span data-stu-id="94ba3-388">10</span></span>|<span data-ttu-id="94ba3-389">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-389">✔</span></span>|<span data-ttu-id="94ba3-390">Matriz de comandos com suporte da extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="94ba3-390">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="94ba3-391">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="94ba3-391">composeExtensions.commands</span></span>

<span data-ttu-id="94ba3-392">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="94ba3-392">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="94ba3-393">Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="94ba3-393">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="94ba3-394">Há no máximo 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="94ba3-394">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="94ba3-395">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="94ba3-395">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="94ba3-396">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-396">Name</span></span>| <span data-ttu-id="94ba3-397">Tipo</span><span class="sxs-lookup"><span data-stu-id="94ba3-397">Type</span></span>| <span data-ttu-id="94ba3-398">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-398">Maximum size</span></span> | <span data-ttu-id="94ba3-399">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-399">Required</span></span> | <span data-ttu-id="94ba3-400">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-400">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="94ba3-401">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-401">String</span></span>|<span data-ttu-id="94ba3-402">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-402">64 characters</span></span>|<span data-ttu-id="94ba3-403">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-403">✔</span></span>|<span data-ttu-id="94ba3-404">A ID do comando.</span><span class="sxs-lookup"><span data-stu-id="94ba3-404">The ID for the command.</span></span>|
|`type`|<span data-ttu-id="94ba3-405">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-405">String</span></span>|<span data-ttu-id="94ba3-406">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-406">64 characters</span></span>||<span data-ttu-id="94ba3-407">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="94ba3-407">Type of the command.</span></span> <span data-ttu-id="94ba3-408">Um dos `query` ou `action` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-408">One of `query` or `action`.</span></span> <span data-ttu-id="94ba3-409">Padrão: `query`</span><span class="sxs-lookup"><span data-stu-id="94ba3-409">Default: `query`</span></span>|
|`title`|<span data-ttu-id="94ba3-410">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-410">String</span></span>|<span data-ttu-id="94ba3-411">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-411">32 characters</span></span>|<span data-ttu-id="94ba3-412">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-412">✔</span></span>|<span data-ttu-id="94ba3-413">O nome de comando amigável.</span><span class="sxs-lookup"><span data-stu-id="94ba3-413">The user-friendly command name.</span></span>|
|`description`|<span data-ttu-id="94ba3-414">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-414">String</span></span>|<span data-ttu-id="94ba3-415">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-415">128 characters</span></span>||<span data-ttu-id="94ba3-416">A descrição que aparece para os usuários para indicar a finalidade deste comando.</span><span class="sxs-lookup"><span data-stu-id="94ba3-416">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="94ba3-417">Booliano</span><span class="sxs-lookup"><span data-stu-id="94ba3-417">Boolean</span></span>|||<span data-ttu-id="94ba3-418">Um valor Boolean que indica se o comando deve ser executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="94ba3-418">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="94ba3-419">Padrão: `false`</span><span class="sxs-lookup"><span data-stu-id="94ba3-419">Default: `false`</span></span>|
|`context`|<span data-ttu-id="94ba3-420">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-420">Array of Strings</span></span>|<span data-ttu-id="94ba3-421">3</span><span class="sxs-lookup"><span data-stu-id="94ba3-421">3</span></span>||<span data-ttu-id="94ba3-422">Define de onde a extensão da mensagem pode ser invocada.</span><span class="sxs-lookup"><span data-stu-id="94ba3-422">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="94ba3-423">Qualquer combinação `compose` de , , `commandBox` `message` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-423">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="94ba3-424">O padrão é `["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="94ba3-424">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="94ba3-425">Booliano</span><span class="sxs-lookup"><span data-stu-id="94ba3-425">Boolean</span></span>|||<span data-ttu-id="94ba3-426">Um valor booleano que indica se ele deve buscar o módulo de tarefa dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="94ba3-426">A boolean value that indicates if it should fetch the task module dynamically.</span></span>|
|`taskInfo`|<span data-ttu-id="94ba3-427">Objeto</span><span class="sxs-lookup"><span data-stu-id="94ba3-427">Object</span></span>|||<span data-ttu-id="94ba3-428">Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="94ba3-428">Specify the task module to preload when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="94ba3-429">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-429">String</span></span>|<span data-ttu-id="94ba3-430">64</span><span class="sxs-lookup"><span data-stu-id="94ba3-430">64</span></span>||<span data-ttu-id="94ba3-431">Título da caixa de diálogo inicial.</span><span class="sxs-lookup"><span data-stu-id="94ba3-431">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="94ba3-432">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-432">String</span></span>|||<span data-ttu-id="94ba3-433">Largura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.</span><span class="sxs-lookup"><span data-stu-id="94ba3-433">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="94ba3-434">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-434">String</span></span>|||<span data-ttu-id="94ba3-435">Altura da caixa de diálogo - um número em pixels ou layout padrão, como "grande", "médio" ou "pequeno".</span><span class="sxs-lookup"><span data-stu-id="94ba3-435">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="94ba3-436">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-436">String</span></span>|||<span data-ttu-id="94ba3-437">URL do webview inicial.</span><span class="sxs-lookup"><span data-stu-id="94ba3-437">Initial webview URL.</span></span>|
|`messageHandlers`|<span data-ttu-id="94ba3-438">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="94ba3-438">Array of Objects</span></span>|<span data-ttu-id="94ba3-439">5 </span><span class="sxs-lookup"><span data-stu-id="94ba3-439">5</span></span>||<span data-ttu-id="94ba3-440">Uma lista de manipuladores que permitem que os aplicativos sejam invocados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="94ba3-440">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="94ba3-441">Os domínios também devem ser listados em `validDomains` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-441">Domains must also be listed in `validDomains`.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="94ba3-442">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-442">String</span></span>|||<span data-ttu-id="94ba3-443">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="94ba3-443">The type of message handler.</span></span> <span data-ttu-id="94ba3-444">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="94ba3-444">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="94ba3-445">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-445">Array of Strings</span></span>|||<span data-ttu-id="94ba3-446">Matriz de domínios que o manipulador de mensagens de link pode registrar.</span><span class="sxs-lookup"><span data-stu-id="94ba3-446">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="94ba3-447">Matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="94ba3-447">Array of object</span></span>|<span data-ttu-id="94ba3-448">5 </span><span class="sxs-lookup"><span data-stu-id="94ba3-448">5</span></span>|<span data-ttu-id="94ba3-449">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-449">✔</span></span>|<span data-ttu-id="94ba3-450">A lista de parâmetros que o comando assume.</span><span class="sxs-lookup"><span data-stu-id="94ba3-450">The list of parameters the command takes.</span></span> <span data-ttu-id="94ba3-451">Mínimo: 1; máximo: 5</span><span class="sxs-lookup"><span data-stu-id="94ba3-451">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="94ba3-452">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-452">String</span></span>|<span data-ttu-id="94ba3-453">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-453">64 characters</span></span>|<span data-ttu-id="94ba3-454">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-454">✔</span></span>|<span data-ttu-id="94ba3-455">O nome do parâmetro como ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="94ba3-455">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="94ba3-456">Isso está incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="94ba3-456">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="94ba3-457">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-457">String</span></span>|<span data-ttu-id="94ba3-458">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-458">32 characters</span></span>|<span data-ttu-id="94ba3-459">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-459">✔</span></span>|<span data-ttu-id="94ba3-460">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="94ba3-460">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="94ba3-461">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-461">String</span></span>|<span data-ttu-id="94ba3-462">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-462">128 characters</span></span>||<span data-ttu-id="94ba3-463">Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="94ba3-463">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="94ba3-464">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-464">String</span></span>|<span data-ttu-id="94ba3-465">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-465">128 characters</span></span>||<span data-ttu-id="94ba3-466">Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-466">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="94ba3-467">Um de `text` , , , , , , `textarea` `number` `date` `time` `toggle` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-467">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`.</span></span>|
|`parameter.choices`|<span data-ttu-id="94ba3-468">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="94ba3-468">Array of Objects</span></span>|<span data-ttu-id="94ba3-469">10 </span><span class="sxs-lookup"><span data-stu-id="94ba3-469">10</span></span>||<span data-ttu-id="94ba3-470">As opções de escolha para `choiceset` o .</span><span class="sxs-lookup"><span data-stu-id="94ba3-470">The choice options for the `choiceset`.</span></span> <span data-ttu-id="94ba3-471">Use somente quando `parameter.inputType` for `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-471">Use only when `parameter.inputType` is `choiceset`.</span></span>|
|`parameter.choices.title`|<span data-ttu-id="94ba3-472">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-472">String</span></span>|<span data-ttu-id="94ba3-473">128</span><span class="sxs-lookup"><span data-stu-id="94ba3-473">128</span></span>||<span data-ttu-id="94ba3-474">Título da escolha.</span><span class="sxs-lookup"><span data-stu-id="94ba3-474">Title of the choice.</span></span>|
|`parameter.choices.value`|<span data-ttu-id="94ba3-475">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-475">String</span></span>|<span data-ttu-id="94ba3-476">512</span><span class="sxs-lookup"><span data-stu-id="94ba3-476">512</span></span>||<span data-ttu-id="94ba3-477">O valor da escolha.</span><span class="sxs-lookup"><span data-stu-id="94ba3-477">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="94ba3-478">permissões</span><span class="sxs-lookup"><span data-stu-id="94ba3-478">permissions</span></span>

<span data-ttu-id="94ba3-479">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="94ba3-479">**Optional**</span></span>

<span data-ttu-id="94ba3-480">Uma matriz que especifica quais permissões o aplicativo solicita, o que permite que os usuários finais saibam `string` como a extensão será efetivada.</span><span class="sxs-lookup"><span data-stu-id="94ba3-480">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="94ba3-481">As seguintes opções não são exclusivas:</span><span class="sxs-lookup"><span data-stu-id="94ba3-481">The following options are non-exclusive:</span></span>

* <span data-ttu-id="94ba3-482">`identity`&emsp;Requer informações de identidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="94ba3-482">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="94ba3-483">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="94ba3-483">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="94ba3-484">Alterar essas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="94ba3-484">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="94ba3-485">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="94ba3-485">devicePermissions</span></span>

<span data-ttu-id="94ba3-486">**Opcional** Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-486">**Optional** Array of Strings</span></span>

<span data-ttu-id="94ba3-487">Especifica os recursos nativos no dispositivo de um usuário ao que seu aplicativo pode solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="94ba3-487">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="94ba3-488">As opções são:</span><span class="sxs-lookup"><span data-stu-id="94ba3-488">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="94ba3-489">validDomains</span><span class="sxs-lookup"><span data-stu-id="94ba3-489">validDomains</span></span>

<span data-ttu-id="94ba3-490">**Opcional**, exceto **Obrigatório quando** notado</span><span class="sxs-lookup"><span data-stu-id="94ba3-490">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="94ba3-491">Uma lista de domínios válidos dos quais o aplicativo espera carregar qualquer conteúdo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-491">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="94ba3-492">Listagem de domínio pode incluir caracteres curinga, por exemplo `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-492">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="94ba3-493">Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-493">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="94ba3-494">Se a configuração de tabulação ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de tabulação, esse domínio deve ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="94ba3-494">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="94ba3-495">No **entanto,** não é necessário incluir os domínios de provedores de identidade que você deseja dar suporte ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-495">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="94ba3-496">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para accounts.google.com, mas você não deve incluir accounts.google.com em `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-496">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94ba3-497">Não adicione domínios que estejam fora do seu controle, diretamente ou por meio de caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="94ba3-497">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="94ba3-498">Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="94ba3-498">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="94ba3-499">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-499">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="94ba3-500">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="94ba3-500">webApplicationInfo</span></span>

<span data-ttu-id="94ba3-501">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="94ba3-501">**Optional**</span></span>

<span data-ttu-id="94ba3-502">Especifique sua ID do Aplicativo AAD e Graph informações para ajudar os usuários a entrar perfeitamente em seu aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="94ba3-502">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="94ba3-503">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-503">Name</span></span>| <span data-ttu-id="94ba3-504">Tipo</span><span class="sxs-lookup"><span data-stu-id="94ba3-504">Type</span></span>| <span data-ttu-id="94ba3-505">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-505">Maximum size</span></span> | <span data-ttu-id="94ba3-506">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-506">Required</span></span> | <span data-ttu-id="94ba3-507">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-507">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="94ba3-508">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-508">String</span></span>|<span data-ttu-id="94ba3-509">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-509">36 characters</span></span>|<span data-ttu-id="94ba3-510">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-510">✔</span></span>|<span data-ttu-id="94ba3-511">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-511">AAD application id of the app.</span></span> <span data-ttu-id="94ba3-512">Essa id deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="94ba3-512">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="94ba3-513">String</span><span class="sxs-lookup"><span data-stu-id="94ba3-513">String</span></span>|<span data-ttu-id="94ba3-514">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-514">2048 characters</span></span>|<span data-ttu-id="94ba3-515">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-515">✔</span></span>|<span data-ttu-id="94ba3-516">URL de recurso do aplicativo para adquirir token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="94ba3-516">Resource url of app for acquiring auth token for SSO.</span></span>|
|`applicationPermissions`|<span data-ttu-id="94ba3-517">Matriz</span><span class="sxs-lookup"><span data-stu-id="94ba3-517">Array</span></span>|<span data-ttu-id="94ba3-518">Máximo de 100 itens</span><span class="sxs-lookup"><span data-stu-id="94ba3-518">Maximum 100 items</span></span>|<span data-ttu-id="94ba3-519">✔</span><span class="sxs-lookup"><span data-stu-id="94ba3-519">✔</span></span>|<span data-ttu-id="94ba3-520">Permissões de recurso para aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-520">Resource permissions for application.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="94ba3-521">configurableProperties</span><span class="sxs-lookup"><span data-stu-id="94ba3-521">configurableProperties</span></span>

<span data-ttu-id="94ba3-522">**Opcional** - matriz</span><span class="sxs-lookup"><span data-stu-id="94ba3-522">**Optional** - array</span></span>

<span data-ttu-id="94ba3-523">O `configurableProperties` bloco define as propriedades do aplicativo que os Teams administradores podem personalizar.</span><span class="sxs-lookup"><span data-stu-id="94ba3-523">The `configurableProperties` block defines the app properties that Teams admins can customize.</span></span> <span data-ttu-id="94ba3-524">Para obter mais informações, consulte [enable app customization](~/concepts/design/enable-app-customization.md).</span><span class="sxs-lookup"><span data-stu-id="94ba3-524">For more information, see [enable app customization](~/concepts/design/enable-app-customization.md).</span></span>

> [!NOTE]
> <span data-ttu-id="94ba3-525">Um mínimo de uma propriedade deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="94ba3-525">A minimum of one property must be defined.</span></span> <span data-ttu-id="94ba3-526">Você pode definir um máximo de nove propriedades neste bloco.</span><span class="sxs-lookup"><span data-stu-id="94ba3-526">You can define a maximum of nine properties in this block.</span></span>

<span data-ttu-id="94ba3-527">Você pode definir qualquer uma das seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="94ba3-527">You can define any of the following properties:</span></span>

* <span data-ttu-id="94ba3-528">`name`: O nome de exibição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-528">`name`: The app's display name.</span></span>
* <span data-ttu-id="94ba3-529">`shortDescription`: A descrição curta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-529">`shortDescription`: The app's short description.</span></span>
* <span data-ttu-id="94ba3-530">`longDescription`: A descrição detalhada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-530">`longDescription`: The app's detailed description.</span></span>
* <span data-ttu-id="94ba3-531">`smallImageUrl`: O ícone de contorno do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-531">`smallImageUrl`: The app's outline icon.</span></span>
* <span data-ttu-id="94ba3-532">`largeImageUrl`: O ícone de cor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-532">`largeImageUrl`: The app's color icon.</span></span>
* <span data-ttu-id="94ba3-533">`accentColor`: A cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="94ba3-533">`accentColor`: The color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="94ba3-534">`developerUrl`: A URL HTTPS do site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="94ba3-534">`developerUrl`: The HTTPS URL of the developer's website.</span></span>
* <span data-ttu-id="94ba3-535">`privacyUrl`: A URL HTTPS da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="94ba3-535">`privacyUrl`: The HTTPS URL of the developer's privacy policy.</span></span>
* <span data-ttu-id="94ba3-536">`termsOfUseUrl`: A URL HTTPS dos termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="94ba3-536">`termsOfUseUrl`: The HTTPS URL of the developer's terms of use.</span></span>

## <a name="defaultinstallscope"></a><span data-ttu-id="94ba3-537">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="94ba3-537">defaultInstallScope</span></span>

<span data-ttu-id="94ba3-538">**Opcional** - cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="94ba3-538">**Optional** - string</span></span>

<span data-ttu-id="94ba3-539">Especifica o escopo de instalação definido para este aplicativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="94ba3-539">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="94ba3-540">O escopo definido será a opção exibida no botão quando um usuário tentar adicionar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-540">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="94ba3-541">As opções são:</span><span class="sxs-lookup"><span data-stu-id="94ba3-541">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="94ba3-542">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="94ba3-542">defaultGroupCapability</span></span>

<span data-ttu-id="94ba3-543">**Opcional** - objeto</span><span class="sxs-lookup"><span data-stu-id="94ba3-543">**Optional** - object</span></span>

<span data-ttu-id="94ba3-544">Quando um escopo de instalação de grupo é selecionado, ele define o recurso padrão quando o usuário instala o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94ba3-544">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="94ba3-545">As opções são:</span><span class="sxs-lookup"><span data-stu-id="94ba3-545">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="94ba3-546">Nome</span><span class="sxs-lookup"><span data-stu-id="94ba3-546">Name</span></span>| <span data-ttu-id="94ba3-547">Tipo</span><span class="sxs-lookup"><span data-stu-id="94ba3-547">Type</span></span>| <span data-ttu-id="94ba3-548">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="94ba3-548">Maximum size</span></span> | <span data-ttu-id="94ba3-549">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="94ba3-549">Required</span></span> | <span data-ttu-id="94ba3-550">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ba3-550">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="94ba3-551">string</span><span class="sxs-lookup"><span data-stu-id="94ba3-551">string</span></span>|||<span data-ttu-id="94ba3-552">Quando o escopo de instalação selecionado for `team` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="94ba3-552">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="94ba3-553">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-553">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="94ba3-554">string</span><span class="sxs-lookup"><span data-stu-id="94ba3-554">string</span></span>|||<span data-ttu-id="94ba3-555">Quando o escopo de instalação selecionado for `groupchat` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="94ba3-555">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="94ba3-556">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-556">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="94ba3-557">string</span><span class="sxs-lookup"><span data-stu-id="94ba3-557">string</span></span>|||<span data-ttu-id="94ba3-558">Quando o escopo de instalação selecionado for `meetings` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="94ba3-558">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="94ba3-559">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="94ba3-559">Options: `tab`, `bot`, or `connector`.</span></span>|
