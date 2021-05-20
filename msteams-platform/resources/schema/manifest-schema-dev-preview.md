---
title: Referência de esquema de manifesto de visualização do desenvolvedor
description: Descreve o esquema apoiado pelo manifesto para Microsoft Teams
ms.topic: reference
keywords: equipes manifestam esquema Visualização desenvolvedor
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: b52d52f96312dc2978844b07a0f7ebb1d817166d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566702"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="04ccb-104">Esquema de manifesto de visualização de desenvolvedores para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="04ccb-104">Developer preview manifest schema for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="04ccb-105">Consulte [o Developer Preview](~/resources/dev-preview/developer-preview-intro.md) para obter informações sobre o programa e como você pode participar.</span><span class="sxs-lookup"><span data-stu-id="04ccb-105">See [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for information on the program and how you can join.</span></span>
> <span data-ttu-id="04ccb-106">Se você não estiver usando a visualização do desenvolvedor, você não deve usar esta versão do manifesto.</span><span class="sxs-lookup"><span data-stu-id="04ccb-106">If you are not using the developer preview you should not be using this version of the manifest.</span></span> <span data-ttu-id="04ccb-107">Veja [Referência: Manifesto esquema para Microsoft Teams](~/resources/schema/manifest-schema.md) para a versão pública do manifesto.</span><span class="sxs-lookup"><span data-stu-id="04ccb-107">See [Reference: Manifest schema for Microsoft Teams](~/resources/schema/manifest-schema.md) for the public version of the manifest.</span></span>

<span data-ttu-id="04ccb-108">O manifesto Microsoft Teams descreve como o aplicativo se integra ao produto Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="04ccb-108">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="04ccb-109">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="04ccb-109">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="04ccb-110">Para obter mais informações sobre os recursos disponíveis, consulte: [Recursos na pré-visualização do desenvolvedor público para Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span><span class="sxs-lookup"><span data-stu-id="04ccb-110">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="04ccb-111">Amostra de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="04ccb-111">Sample full manifest</span></span>

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
   "configurableProperties": [
     "name",
     "shortDescription",
     "longDescription",
     "smallImageUrl", 
     "largeImageUrl", 
     "accentColor",
     "websiteUrl",
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

<span data-ttu-id="04ccb-112">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="04ccb-112">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="04ccb-113">$schema</span><span class="sxs-lookup"><span data-stu-id="04ccb-113">$schema</span></span>

<span data-ttu-id="04ccb-114">*Opcional, mas recomendado* &ndash; corda</span><span class="sxs-lookup"><span data-stu-id="04ccb-114">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="04ccb-115">A URL https:// fazendo referência ao Esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="04ccb-115">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="04ccb-116">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="04ccb-116">manifestVersion</span></span>

<span data-ttu-id="04ccb-117">**Necessário** &ndash; corda</span><span class="sxs-lookup"><span data-stu-id="04ccb-117">**Required** &ndash; String</span></span>

<span data-ttu-id="04ccb-118">A versão do esquema manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="04ccb-118">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="04ccb-119">Deve ser "devPreview".</span><span class="sxs-lookup"><span data-stu-id="04ccb-119">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="04ccb-120">versão</span><span class="sxs-lookup"><span data-stu-id="04ccb-120">version</span></span>

<span data-ttu-id="04ccb-121">**Necessário** &ndash; corda</span><span class="sxs-lookup"><span data-stu-id="04ccb-121">**Required** &ndash; String</span></span>

<span data-ttu-id="04ccb-122">A versão do aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="04ccb-122">The version of the specific app.</span></span> <span data-ttu-id="04ccb-123">Se você atualizar algo em seu manifesto, a versão deve ser incrementada também.</span><span class="sxs-lookup"><span data-stu-id="04ccb-123">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="04ccb-124">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="04ccb-124">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="04ccb-125">Se este aplicativo foi enviado para a loja, o novo manifesto terá que ser remetido e revalidado.</span><span class="sxs-lookup"><span data-stu-id="04ccb-125">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="04ccb-126">Em seguida, os usuários deste app receberão o novo manifesto atualizado automaticamente em poucas horas, depois de aprovado.</span><span class="sxs-lookup"><span data-stu-id="04ccb-126">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="04ccb-127">Se o aplicativo solicitar a alteração das permissões, os usuários serão solicitados a atualizar e re consentir com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-127">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="04ccb-128">Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (MAJOR. menor. PATCH).</span><span class="sxs-lookup"><span data-stu-id="04ccb-128">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="04ccb-129">id</span><span class="sxs-lookup"><span data-stu-id="04ccb-129">id</span></span>

<span data-ttu-id="04ccb-130">**Necessário** &ndash; ID do aplicativo da Microsoft</span><span class="sxs-lookup"><span data-stu-id="04ccb-130">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="04ccb-131">O identificador exclusivo gerado pela Microsoft para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-131">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="04ccb-132">Se você registrou um bot através do Microsoft Bot Framework, ou o aplicativo web da sua guia já entra na Microsoft, você já deve ter um ID e deve inseri-lo aqui.</span><span class="sxs-lookup"><span data-stu-id="04ccb-132">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="04ccb-133">Caso contrário, você deve gerar um novo ID no Portal de Registro de Aplicativos da Microsoft ([Meus Aplicativos), inseri-lo](https://apps.dev.microsoft.com)aqui e, em seguida, reutilizá-lo quando você [adicionar um bot](~/bots/how-to/create-a-bot-for-teams.md).</span><span class="sxs-lookup"><span data-stu-id="04ccb-133">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="04ccb-134">packageName</span><span class="sxs-lookup"><span data-stu-id="04ccb-134">packageName</span></span>

<span data-ttu-id="04ccb-135">**Necessário** &ndash; corda</span><span class="sxs-lookup"><span data-stu-id="04ccb-135">**Required** &ndash; String</span></span>

<span data-ttu-id="04ccb-136">Um identificador exclusivo para este aplicativo em notação de domínio reverso; por exemplo, com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="04ccb-136">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="04ccb-137">developer</span><span class="sxs-lookup"><span data-stu-id="04ccb-137">developer</span></span>

<span data-ttu-id="04ccb-138">**Required**</span><span class="sxs-lookup"><span data-stu-id="04ccb-138">**Required**</span></span>

<span data-ttu-id="04ccb-139">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="04ccb-139">Specifies information about your company.</span></span> <span data-ttu-id="04ccb-140">Para aplicativos submetidos ao AppSource (anteriormente Office Store), esses valores devem corresponder às informações na sua entrada AppSource.</span><span class="sxs-lookup"><span data-stu-id="04ccb-140">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="04ccb-141">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-141">Name</span></span>| <span data-ttu-id="04ccb-142">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-142">Maximum size</span></span> | <span data-ttu-id="04ccb-143">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-143">Required</span></span> | <span data-ttu-id="04ccb-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="04ccb-145">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-145">32 characters</span></span>|<span data-ttu-id="04ccb-146">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-146">✔</span></span>|<span data-ttu-id="04ccb-147">O nome de exibição para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="04ccb-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="04ccb-148">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-148">2048 characters</span></span>|<span data-ttu-id="04ccb-149">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-149">✔</span></span>|<span data-ttu-id="04ccb-150">O https:// URL para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="04ccb-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="04ccb-151">Este link deve levar os usuários para sua empresa ou página de landing específica do produto.</span><span class="sxs-lookup"><span data-stu-id="04ccb-151">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="04ccb-152">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-152">2048 characters</span></span>|<span data-ttu-id="04ccb-153">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-153">✔</span></span>|<span data-ttu-id="04ccb-154">O https:// URL para a política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="04ccb-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="04ccb-155">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-155">2048 characters</span></span>|<span data-ttu-id="04ccb-156">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-156">✔</span></span>|<span data-ttu-id="04ccb-157">O https:// URL para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="04ccb-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="04ccb-158">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-158">10 characters</span></span>|<span data-ttu-id="04ccb-159">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-159">✔</span></span>|<span data-ttu-id="04ccb-160">**Opcional** O Microsoft Partner Network ID que identifica a organização parceira que está construindo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-160">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="04ccb-161">localizaçãoInfo</span><span class="sxs-lookup"><span data-stu-id="04ccb-161">localizationInfo</span></span>

<span data-ttu-id="04ccb-162">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="04ccb-162">**Optional**</span></span>

<span data-ttu-id="04ccb-163">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="04ccb-163">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="04ccb-164">Veja [a localização.](~/concepts/build-and-test/apps-localization.md)</span><span class="sxs-lookup"><span data-stu-id="04ccb-164">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="04ccb-165">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-165">Name</span></span>| <span data-ttu-id="04ccb-166">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-166">Maximum size</span></span> | <span data-ttu-id="04ccb-167">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-167">Required</span></span> | <span data-ttu-id="04ccb-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-168">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="04ccb-169">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-169">4 characters</span></span>|<span data-ttu-id="04ccb-170">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-170">✔</span></span>|<span data-ttu-id="04ccb-171">A tag de idioma das strings neste arquivo manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="04ccb-171">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="04ccb-172">localizaçãoInfo.additionalLíguas</span><span class="sxs-lookup"><span data-stu-id="04ccb-172">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="04ccb-173">Uma variedade de objetos especificando traduções adicionais de idiomas.</span><span class="sxs-lookup"><span data-stu-id="04ccb-173">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="04ccb-174">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-174">Name</span></span>| <span data-ttu-id="04ccb-175">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-175">Maximum size</span></span> | <span data-ttu-id="04ccb-176">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-176">Required</span></span> | <span data-ttu-id="04ccb-177">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-177">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="04ccb-178">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-178">4 characters</span></span>|<span data-ttu-id="04ccb-179">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-179">✔</span></span>|<span data-ttu-id="04ccb-180">A tag de idioma das strings no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="04ccb-180">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="04ccb-181">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-181">4 characters</span></span>|<span data-ttu-id="04ccb-182">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-182">✔</span></span>|<span data-ttu-id="04ccb-183">Um caminho relativo de arquivo para um arquivo .json contendo as strings traduzidas.</span><span class="sxs-lookup"><span data-stu-id="04ccb-183">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="04ccb-184">nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-184">name</span></span>

<span data-ttu-id="04ccb-185">**Required**</span><span class="sxs-lookup"><span data-stu-id="04ccb-185">**Required**</span></span>

<span data-ttu-id="04ccb-186">O nome da experiência do seu aplicativo, exibido aos usuários na experiência Teams.</span><span class="sxs-lookup"><span data-stu-id="04ccb-186">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="04ccb-187">Para aplicativos submetidos ao AppSource, esses valores devem corresponder às informações na sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="04ccb-187">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="04ccb-188">Os valores `short` de e não devem ser os `full` mesmos.</span><span class="sxs-lookup"><span data-stu-id="04ccb-188">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="04ccb-189">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-189">Name</span></span>| <span data-ttu-id="04ccb-190">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-190">Maximum size</span></span> | <span data-ttu-id="04ccb-191">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-191">Required</span></span> | <span data-ttu-id="04ccb-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-192">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="04ccb-193">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-193">30 characters</span></span>|<span data-ttu-id="04ccb-194">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-194">✔</span></span>|<span data-ttu-id="04ccb-195">O nome de exibição curto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-195">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="04ccb-196">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-196">100 characters</span></span>||<span data-ttu-id="04ccb-197">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="04ccb-197">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="04ccb-198">descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-198">description</span></span>

<span data-ttu-id="04ccb-199">**Required**</span><span class="sxs-lookup"><span data-stu-id="04ccb-199">**Required**</span></span>

<span data-ttu-id="04ccb-200">Descreve seu aplicativo para os usuários.</span><span class="sxs-lookup"><span data-stu-id="04ccb-200">Describes your app to users.</span></span> <span data-ttu-id="04ccb-201">Para aplicativos submetidos ao AppSource, esses valores devem corresponder às informações na sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="04ccb-201">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="04ccb-202">Certifique-se de que sua descrição descreve com precisão sua experiência e fornece informações para ajudar os clientes em potencial a entender o que sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="04ccb-202">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="04ccb-203">Você também deve observar, na descrição completa, se uma conta externa é necessária para uso.</span><span class="sxs-lookup"><span data-stu-id="04ccb-203">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="04ccb-204">Os valores `short` de e não devem ser os `full` mesmos.</span><span class="sxs-lookup"><span data-stu-id="04ccb-204">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="04ccb-205">Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir qualquer outro nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-205">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="04ccb-206">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-206">Name</span></span>| <span data-ttu-id="04ccb-207">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-207">Maximum size</span></span> | <span data-ttu-id="04ccb-208">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-208">Required</span></span> | <span data-ttu-id="04ccb-209">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-209">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="04ccb-210">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-210">80 characters</span></span>|<span data-ttu-id="04ccb-211">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-211">✔</span></span>|<span data-ttu-id="04ccb-212">Uma breve descrição da sua experiência de aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="04ccb-212">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="04ccb-213">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-213">4000 characters</span></span>|<span data-ttu-id="04ccb-214">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-214">✔</span></span>|<span data-ttu-id="04ccb-215">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-215">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="04ccb-216">ícones</span><span class="sxs-lookup"><span data-stu-id="04ccb-216">icons</span></span>

<span data-ttu-id="04ccb-217">**Required**</span><span class="sxs-lookup"><span data-stu-id="04ccb-217">**Required**</span></span>

<span data-ttu-id="04ccb-218">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="04ccb-218">Icons used within the Teams app.</span></span> <span data-ttu-id="04ccb-219">Os arquivos de ícone devem ser incluídos como parte do pacote de upload.</span><span class="sxs-lookup"><span data-stu-id="04ccb-219">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="04ccb-220">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-220">Name</span></span>| <span data-ttu-id="04ccb-221">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-221">Maximum size</span></span> | <span data-ttu-id="04ccb-222">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-222">Required</span></span> | <span data-ttu-id="04ccb-223">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="04ccb-224">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-224">2048 characters</span></span>|<span data-ttu-id="04ccb-225">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-225">✔</span></span>|<span data-ttu-id="04ccb-226">Um caminho relativo de arquivo para um ícone transparente de contorno 32x32 PNG.</span><span class="sxs-lookup"><span data-stu-id="04ccb-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="04ccb-227">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-227">2048 characters</span></span>|<span data-ttu-id="04ccb-228">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-228">✔</span></span>|<span data-ttu-id="04ccb-229">Um caminho relativo de arquivo para um ícone PNG de cor completa 192x192.</span><span class="sxs-lookup"><span data-stu-id="04ccb-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="04ccb-230">sotaqueColor</span><span class="sxs-lookup"><span data-stu-id="04ccb-230">accentColor</span></span>

<span data-ttu-id="04ccb-231">**Necessário** &ndash; corda</span><span class="sxs-lookup"><span data-stu-id="04ccb-231">**Required** &ndash; String</span></span>

<span data-ttu-id="04ccb-232">Uma cor para usar em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="04ccb-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="04ccb-233">O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="04ccb-234">configurávelTabs</span><span class="sxs-lookup"><span data-stu-id="04ccb-234">configurableTabs</span></span>

<span data-ttu-id="04ccb-235">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="04ccb-235">**Optional**</span></span>

<span data-ttu-id="04ccb-236">Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="04ccb-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="04ccb-237">As guias configuráveis são suportadas apenas no escopo das equipes e, atualmente, apenas uma guia por aplicativo é suportada.</span><span class="sxs-lookup"><span data-stu-id="04ccb-237">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="04ccb-238">O objeto é uma matriz com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-238">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="04ccb-239">Este bloco é necessário apenas para soluções que forneçam uma solução de guia de canal configurável.</span><span class="sxs-lookup"><span data-stu-id="04ccb-239">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="04ccb-240">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-240">Name</span></span>| <span data-ttu-id="04ccb-241">Tipo</span><span class="sxs-lookup"><span data-stu-id="04ccb-241">Type</span></span>| <span data-ttu-id="04ccb-242">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-242">Maximum size</span></span> | <span data-ttu-id="04ccb-243">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-243">Required</span></span> | <span data-ttu-id="04ccb-244">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="04ccb-245">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-245">String</span></span>|<span data-ttu-id="04ccb-246">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-246">2048 characters</span></span>|<span data-ttu-id="04ccb-247">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-247">✔</span></span>|<span data-ttu-id="04ccb-248">A https:// URL a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="04ccb-248">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="04ccb-249">Booliano</span><span class="sxs-lookup"><span data-stu-id="04ccb-249">Boolean</span></span>|||<span data-ttu-id="04ccb-250">Um valor indicando se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="04ccb-250">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="04ccb-251">inadimplência: `true`</span><span class="sxs-lookup"><span data-stu-id="04ccb-251">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="04ccb-252">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="04ccb-252">Array of enum</span></span>|<span data-ttu-id="04ccb-253">1</span><span class="sxs-lookup"><span data-stu-id="04ccb-253">1</span></span>|<span data-ttu-id="04ccb-254">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-254">✔</span></span>|<span data-ttu-id="04ccb-255">Atualmente, as guias configuráveis suportam apenas os `team` `groupchat` escopos e escopos.</span><span class="sxs-lookup"><span data-stu-id="04ccb-255">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="04ccb-256">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-256">String</span></span>|<span data-ttu-id="04ccb-257">2048</span><span class="sxs-lookup"><span data-stu-id="04ccb-257">2048</span></span>||<span data-ttu-id="04ccb-258">Um caminho relativo de arquivo para uma imagem de visualização de guia para uso em SharePoint.</span><span class="sxs-lookup"><span data-stu-id="04ccb-258">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="04ccb-259">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="04ccb-259">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="04ccb-260">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="04ccb-260">Array of enum</span></span>|<span data-ttu-id="04ccb-261">1</span><span class="sxs-lookup"><span data-stu-id="04ccb-261">1</span></span>||<span data-ttu-id="04ccb-262">Define como sua guia será disponibilizada em SharePoint.</span><span class="sxs-lookup"><span data-stu-id="04ccb-262">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="04ccb-263">As opções são `sharePointFullPage` e `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="04ccb-263">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="04ccb-264">staticTabs</span><span class="sxs-lookup"><span data-stu-id="04ccb-264">staticTabs</span></span>

<span data-ttu-id="04ccb-265">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="04ccb-265">**Optional**</span></span>

<span data-ttu-id="04ccb-266">Define um conjunto de guias que podem ser "fixadas" por padrão, sem que o usuário as adicione manualmente.</span><span class="sxs-lookup"><span data-stu-id="04ccb-266">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="04ccb-267">As guias estáticas declaradas no `personal` escopo são sempre fixadas à experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-267">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="04ccb-268">As guias estáticas declaradas no `team` escopo não são suportadas no momento.</span><span class="sxs-lookup"><span data-stu-id="04ccb-268">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="04ccb-269">O objeto é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-269">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="04ccb-270">Este bloco é necessário apenas para soluções que forneçam uma solução de guia estática.</span><span class="sxs-lookup"><span data-stu-id="04ccb-270">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="04ccb-271">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-271">Name</span></span>| <span data-ttu-id="04ccb-272">Tipo</span><span class="sxs-lookup"><span data-stu-id="04ccb-272">Type</span></span>| <span data-ttu-id="04ccb-273">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-273">Maximum size</span></span> | <span data-ttu-id="04ccb-274">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-274">Required</span></span> | <span data-ttu-id="04ccb-275">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-275">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="04ccb-276">String</span><span class="sxs-lookup"><span data-stu-id="04ccb-276">String</span></span>|<span data-ttu-id="04ccb-277">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-277">64 characters</span></span>|<span data-ttu-id="04ccb-278">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-278">✔</span></span>|<span data-ttu-id="04ccb-279">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="04ccb-279">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="04ccb-280">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-280">String</span></span>|<span data-ttu-id="04ccb-281">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-281">128 characters</span></span>|<span data-ttu-id="04ccb-282">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-282">✔</span></span>|<span data-ttu-id="04ccb-283">O nome de exibição da guia na interface do canal.</span><span class="sxs-lookup"><span data-stu-id="04ccb-283">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="04ccb-284">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-284">String</span></span>|<span data-ttu-id="04ccb-285">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-285">2048 characters</span></span>|<span data-ttu-id="04ccb-286">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-286">✔</span></span>|<span data-ttu-id="04ccb-287">A url https:// que aponta para a interface do usuário da entidade a ser exibida na tela Teams.</span><span class="sxs-lookup"><span data-stu-id="04ccb-287">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="04ccb-288">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-288">String</span></span>|<span data-ttu-id="04ccb-289">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-289">2048 characters</span></span>||<span data-ttu-id="04ccb-290">O https:// URL para apontar se um usuário optar por visualizar em um navegador.</span><span class="sxs-lookup"><span data-stu-id="04ccb-290">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="04ccb-291">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="04ccb-291">Array of enum</span></span>|<span data-ttu-id="04ccb-292">1</span><span class="sxs-lookup"><span data-stu-id="04ccb-292">1</span></span>|<span data-ttu-id="04ccb-293">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-293">✔</span></span>|<span data-ttu-id="04ccb-294">Atualmente, as guias estáticas suportam apenas o escopo, o `personal` que significa que ele só pode ser provisionado como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="04ccb-294">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="04ccb-295">Bots</span><span class="sxs-lookup"><span data-stu-id="04ccb-295">bots</span></span>

<span data-ttu-id="04ccb-296">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="04ccb-296">**Optional**</span></span>

<span data-ttu-id="04ccb-297">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="04ccb-297">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="04ccb-298">O objeto é uma matriz (no máximo 1 elemento &mdash; atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-298">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="04ccb-299">Este bloco é necessário apenas para soluções que forneçam uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="04ccb-299">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="04ccb-300">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-300">Name</span></span>| <span data-ttu-id="04ccb-301">Tipo</span><span class="sxs-lookup"><span data-stu-id="04ccb-301">Type</span></span>| <span data-ttu-id="04ccb-302">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-302">Maximum size</span></span> | <span data-ttu-id="04ccb-303">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-303">Required</span></span> | <span data-ttu-id="04ccb-304">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-304">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="04ccb-305">String</span><span class="sxs-lookup"><span data-stu-id="04ccb-305">String</span></span>|<span data-ttu-id="04ccb-306">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-306">64 characters</span></span>|<span data-ttu-id="04ccb-307">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-307">✔</span></span>|<span data-ttu-id="04ccb-308">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="04ccb-308">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="04ccb-309">Isso pode muito bem ser o mesmo que o [ID](#id)geral do aplicativo .</span><span class="sxs-lookup"><span data-stu-id="04ccb-309">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="04ccb-310">Boolean</span><span class="sxs-lookup"><span data-stu-id="04ccb-310">Boolean</span></span>|||<span data-ttu-id="04ccb-311">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="04ccb-311">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="04ccb-312">inadimplência: `false`</span><span class="sxs-lookup"><span data-stu-id="04ccb-312">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="04ccb-313">Boolean</span><span class="sxs-lookup"><span data-stu-id="04ccb-313">Boolean</span></span>|||<span data-ttu-id="04ccb-314">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="04ccb-314">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="04ccb-315">inadimplência: `false`</span><span class="sxs-lookup"><span data-stu-id="04ccb-315">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="04ccb-316">Boolean</span><span class="sxs-lookup"><span data-stu-id="04ccb-316">Boolean</span></span>|||<span data-ttu-id="04ccb-317">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="04ccb-317">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="04ccb-318">inadimplência: `false`</span><span class="sxs-lookup"><span data-stu-id="04ccb-318">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="04ccb-319">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="04ccb-319">Array of enum</span></span>|<span data-ttu-id="04ccb-320">3</span><span class="sxs-lookup"><span data-stu-id="04ccb-320">3</span></span>|<span data-ttu-id="04ccb-321">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-321">✔</span></span>|<span data-ttu-id="04ccb-322">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="04ccb-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="04ccb-323">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="04ccb-323">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="04ccb-324">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="04ccb-324">bots.commandLists</span></span>

<span data-ttu-id="04ccb-325">Uma lista opcional de comandos que o bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="04ccb-325">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="04ccb-326">O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo ; você deve definir uma lista de `object` comando separada para cada escopo que o seu bot suporta.</span><span class="sxs-lookup"><span data-stu-id="04ccb-326">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="04ccb-327">Para obter mais informações, consulte [menus bot](~/bots/how-to/create-a-bot-commands-menu.md).</span><span class="sxs-lookup"><span data-stu-id="04ccb-327">For more information, see [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md).</span></span>

|<span data-ttu-id="04ccb-328">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-328">Name</span></span>| <span data-ttu-id="04ccb-329">Tipo</span><span class="sxs-lookup"><span data-stu-id="04ccb-329">Type</span></span>| <span data-ttu-id="04ccb-330">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-330">Maximum size</span></span> | <span data-ttu-id="04ccb-331">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-331">Required</span></span> | <span data-ttu-id="04ccb-332">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-332">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="04ccb-333">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="04ccb-333">array of enum</span></span>|<span data-ttu-id="04ccb-334">3</span><span class="sxs-lookup"><span data-stu-id="04ccb-334">3</span></span>|<span data-ttu-id="04ccb-335">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-335">✔</span></span>|<span data-ttu-id="04ccb-336">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="04ccb-336">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="04ccb-337">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="04ccb-337">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="04ccb-338">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="04ccb-338">array of objects</span></span>|<span data-ttu-id="04ccb-339">10 </span><span class="sxs-lookup"><span data-stu-id="04ccb-339">10</span></span>|<span data-ttu-id="04ccb-340">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-340">✔</span></span>|<span data-ttu-id="04ccb-341">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="04ccb-341">An array of commands the bot supports:</span></span><br><span data-ttu-id="04ccb-342">`title`: o nome do comando do bot (string, 32).</span><span class="sxs-lookup"><span data-stu-id="04ccb-342">`title`: the bot command name (string, 32).</span></span><br><span data-ttu-id="04ccb-343">`description`: uma descrição simples ou exemplo da sintaxe de comando e seu argumento (string, 128).</span><span class="sxs-lookup"><span data-stu-id="04ccb-343">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

## <a name="connectors"></a><span data-ttu-id="04ccb-344">Conectores</span><span class="sxs-lookup"><span data-stu-id="04ccb-344">connectors</span></span>

<span data-ttu-id="04ccb-345">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="04ccb-345">**Optional**</span></span>

<span data-ttu-id="04ccb-346">O `connectors` bloco define um conector de Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-346">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="04ccb-347">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-347">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="04ccb-348">Este bloco é necessário apenas para soluções que forneçam um Conector.</span><span class="sxs-lookup"><span data-stu-id="04ccb-348">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="04ccb-349">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-349">Name</span></span>| <span data-ttu-id="04ccb-350">Tipo</span><span class="sxs-lookup"><span data-stu-id="04ccb-350">Type</span></span>| <span data-ttu-id="04ccb-351">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-351">Maximum size</span></span> | <span data-ttu-id="04ccb-352">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-352">Required</span></span> | <span data-ttu-id="04ccb-353">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-353">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="04ccb-354">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-354">String</span></span>|<span data-ttu-id="04ccb-355">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-355">2048 characters</span></span>|<span data-ttu-id="04ccb-356">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-356">✔</span></span>|<span data-ttu-id="04ccb-357">A https:// URL para usar ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="04ccb-357">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="04ccb-358">String</span><span class="sxs-lookup"><span data-stu-id="04ccb-358">String</span></span>|<span data-ttu-id="04ccb-359">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-359">64 characters</span></span>|<span data-ttu-id="04ccb-360">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-360">✔</span></span>|<span data-ttu-id="04ccb-361">Um identificador exclusivo para o Conector que corresponde ao seu ID no [Painel de Desenvolvedores de Conectores](https://aka.ms/connectorsdashboard).</span><span class="sxs-lookup"><span data-stu-id="04ccb-361">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="04ccb-362">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="04ccb-362">Array of enum</span></span>|<span data-ttu-id="04ccb-363">1</span><span class="sxs-lookup"><span data-stu-id="04ccb-363">1</span></span>|<span data-ttu-id="04ccb-364">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-364">✔</span></span>|<span data-ttu-id="04ccb-365">Especifica se o Conector oferece uma experiência no contexto de um canal em um `team` , ou uma experiência escopo para um usuário individual `personal` ().</span><span class="sxs-lookup"><span data-stu-id="04ccb-365">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="04ccb-366">Atualmente, apenas o `team` escopo é suportado.</span><span class="sxs-lookup"><span data-stu-id="04ccb-366">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="04ccb-367">comporTensões</span><span class="sxs-lookup"><span data-stu-id="04ccb-367">composeExtensions</span></span>

<span data-ttu-id="04ccb-368">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="04ccb-368">**Optional**</span></span>

<span data-ttu-id="04ccb-369">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-369">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="04ccb-370">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome manifesto permanece o mesmo para que as extensões existentes continuem funcionando.</span><span class="sxs-lookup"><span data-stu-id="04ccb-370">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="04ccb-371">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-371">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="04ccb-372">Este bloco é necessário apenas para soluções que forneçam uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="04ccb-372">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="04ccb-373">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-373">Name</span></span>| <span data-ttu-id="04ccb-374">Tipo</span><span class="sxs-lookup"><span data-stu-id="04ccb-374">Type</span></span> | <span data-ttu-id="04ccb-375">Tamanho Máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-375">Maximum Size</span></span> | <span data-ttu-id="04ccb-376">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-376">Required</span></span> | <span data-ttu-id="04ccb-377">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-377">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="04ccb-378">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-378">String</span></span>|<span data-ttu-id="04ccb-379">64</span><span class="sxs-lookup"><span data-stu-id="04ccb-379">64</span></span>|<span data-ttu-id="04ccb-380">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-380">✔</span></span>|<span data-ttu-id="04ccb-381">O ID exclusivo do aplicativo da Microsoft para o bot que apoia a extensão de mensagens, como registrado no Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="04ccb-381">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="04ccb-382">Isso pode muito bem ser o mesmo que o [ID](#id)geral do aplicativo .</span><span class="sxs-lookup"><span data-stu-id="04ccb-382">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="04ccb-383">Booliano</span><span class="sxs-lookup"><span data-stu-id="04ccb-383">Boolean</span></span>|||<span data-ttu-id="04ccb-384">Um valor indicando se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="04ccb-384">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="04ccb-385">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="04ccb-385">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="04ccb-386">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="04ccb-386">Array of object</span></span>|<span data-ttu-id="04ccb-387">10 </span><span class="sxs-lookup"><span data-stu-id="04ccb-387">10</span></span>|<span data-ttu-id="04ccb-388">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-388">✔</span></span>|<span data-ttu-id="04ccb-389">Matriz de comandos que a extensão de mensagens suporta</span><span class="sxs-lookup"><span data-stu-id="04ccb-389">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="04ccb-390">comporExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="04ccb-390">composeExtensions.commands</span></span>

<span data-ttu-id="04ccb-391">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="04ccb-391">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="04ccb-392">Cada comando aparece em Microsoft Teams como uma interação potencial do ponto de entrada baseado em interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="04ccb-392">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="04ccb-393">Há um máximo de 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="04ccb-393">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="04ccb-394">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="04ccb-394">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="04ccb-395">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-395">Name</span></span>| <span data-ttu-id="04ccb-396">Tipo</span><span class="sxs-lookup"><span data-stu-id="04ccb-396">Type</span></span>| <span data-ttu-id="04ccb-397">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-397">Maximum size</span></span> | <span data-ttu-id="04ccb-398">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-398">Required</span></span> | <span data-ttu-id="04ccb-399">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-399">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="04ccb-400">String</span><span class="sxs-lookup"><span data-stu-id="04ccb-400">String</span></span>|<span data-ttu-id="04ccb-401">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-401">64 characters</span></span>|<span data-ttu-id="04ccb-402">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-402">✔</span></span>|<span data-ttu-id="04ccb-403">A responsabilidade pelo comando.</span><span class="sxs-lookup"><span data-stu-id="04ccb-403">The ID for the command.</span></span>|
|`type`|<span data-ttu-id="04ccb-404">String</span><span class="sxs-lookup"><span data-stu-id="04ccb-404">String</span></span>|<span data-ttu-id="04ccb-405">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-405">64 characters</span></span>||<span data-ttu-id="04ccb-406">Tipo de comando.</span><span class="sxs-lookup"><span data-stu-id="04ccb-406">Type of the command.</span></span> <span data-ttu-id="04ccb-407">Um de `query` ou `action` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-407">One of `query` or `action`.</span></span> <span data-ttu-id="04ccb-408">inadimplência: `query`</span><span class="sxs-lookup"><span data-stu-id="04ccb-408">Default: `query`</span></span>|
|`title`|<span data-ttu-id="04ccb-409">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-409">String</span></span>|<span data-ttu-id="04ccb-410">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-410">32 characters</span></span>|<span data-ttu-id="04ccb-411">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-411">✔</span></span>|<span data-ttu-id="04ccb-412">O nome de comando fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="04ccb-412">The user-friendly command name.</span></span>|
|`description`|<span data-ttu-id="04ccb-413">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-413">String</span></span>|<span data-ttu-id="04ccb-414">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-414">128 characters</span></span>||<span data-ttu-id="04ccb-415">A descrição que aparece aos usuários para indicar o propósito deste comando.</span><span class="sxs-lookup"><span data-stu-id="04ccb-415">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="04ccb-416">Booliano</span><span class="sxs-lookup"><span data-stu-id="04ccb-416">Boolean</span></span>|||<span data-ttu-id="04ccb-417">Um valor booleano que indica se o comando deve ser executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="04ccb-417">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="04ccb-418">inadimplência: `false`</span><span class="sxs-lookup"><span data-stu-id="04ccb-418">Default: `false`</span></span>|
|`context`|<span data-ttu-id="04ccb-419">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-419">Array of Strings</span></span>|<span data-ttu-id="04ccb-420">3</span><span class="sxs-lookup"><span data-stu-id="04ccb-420">3</span></span>||<span data-ttu-id="04ccb-421">Define de onde a extensão da mensagem pode ser invocada.</span><span class="sxs-lookup"><span data-stu-id="04ccb-421">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="04ccb-422">Qualquer combinação `compose` `commandBox` de, `message` . .</span><span class="sxs-lookup"><span data-stu-id="04ccb-422">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="04ccb-423">Padrão é `["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="04ccb-423">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="04ccb-424">Booliano</span><span class="sxs-lookup"><span data-stu-id="04ccb-424">Boolean</span></span>|||<span data-ttu-id="04ccb-425">Um valor booleano que indica se ele deve buscar o módulo de tarefa dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="04ccb-425">A boolean value that indicates if it should fetch the task module dynamically.</span></span>|
|`taskInfo`|<span data-ttu-id="04ccb-426">Objeto</span><span class="sxs-lookup"><span data-stu-id="04ccb-426">Object</span></span>|||<span data-ttu-id="04ccb-427">Especifique o módulo de tarefa para pré-carregar ao usar um comando de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="04ccb-427">Specify the task module to preload when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="04ccb-428">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-428">String</span></span>|<span data-ttu-id="04ccb-429">64</span><span class="sxs-lookup"><span data-stu-id="04ccb-429">64</span></span>||<span data-ttu-id="04ccb-430">Título de diálogo inicial.</span><span class="sxs-lookup"><span data-stu-id="04ccb-430">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="04ccb-431">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-431">String</span></span>|||<span data-ttu-id="04ccb-432">Largura de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.</span><span class="sxs-lookup"><span data-stu-id="04ccb-432">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="04ccb-433">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-433">String</span></span>|||<span data-ttu-id="04ccb-434">Altura de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.</span><span class="sxs-lookup"><span data-stu-id="04ccb-434">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="04ccb-435">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-435">String</span></span>|||<span data-ttu-id="04ccb-436">URL inicial do webview.</span><span class="sxs-lookup"><span data-stu-id="04ccb-436">Initial webview URL.</span></span>|
|`messageHandlers`|<span data-ttu-id="04ccb-437">Matriz de Objetos</span><span class="sxs-lookup"><span data-stu-id="04ccb-437">Array of Objects</span></span>|<span data-ttu-id="04ccb-438">5 </span><span class="sxs-lookup"><span data-stu-id="04ccb-438">5</span></span>||<span data-ttu-id="04ccb-439">Uma lista de manipuladores que permitem que os aplicativos sejam invocados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="04ccb-439">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="04ccb-440">Os domínios também devem ser listados em `validDomains` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-440">Domains must also be listed in `validDomains`.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="04ccb-441">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-441">String</span></span>|||<span data-ttu-id="04ccb-442">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="04ccb-442">The type of message handler.</span></span> <span data-ttu-id="04ccb-443">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="04ccb-443">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="04ccb-444">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-444">Array of Strings</span></span>|||<span data-ttu-id="04ccb-445">Matriz de domínios para os que o manipulador de mensagens de link pode registrar.</span><span class="sxs-lookup"><span data-stu-id="04ccb-445">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="04ccb-446">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="04ccb-446">Array of object</span></span>|<span data-ttu-id="04ccb-447">5 </span><span class="sxs-lookup"><span data-stu-id="04ccb-447">5</span></span>|<span data-ttu-id="04ccb-448">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-448">✔</span></span>|<span data-ttu-id="04ccb-449">A lista de parâmetros que o comando toma.</span><span class="sxs-lookup"><span data-stu-id="04ccb-449">The list of parameters the command takes.</span></span> <span data-ttu-id="04ccb-450">Mínimo: 1; máximo: 5</span><span class="sxs-lookup"><span data-stu-id="04ccb-450">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="04ccb-451">String</span><span class="sxs-lookup"><span data-stu-id="04ccb-451">String</span></span>|<span data-ttu-id="04ccb-452">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-452">64 characters</span></span>|<span data-ttu-id="04ccb-453">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-453">✔</span></span>|<span data-ttu-id="04ccb-454">O nome do parâmetro como aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="04ccb-454">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="04ccb-455">Isso está incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="04ccb-455">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="04ccb-456">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-456">String</span></span>|<span data-ttu-id="04ccb-457">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-457">32 characters</span></span>|<span data-ttu-id="04ccb-458">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-458">✔</span></span>|<span data-ttu-id="04ccb-459">Título fácil de usar para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="04ccb-459">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="04ccb-460">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-460">String</span></span>|<span data-ttu-id="04ccb-461">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-461">128 characters</span></span>||<span data-ttu-id="04ccb-462">String fácil de usar que descreve o propósito deste parâmetro.</span><span class="sxs-lookup"><span data-stu-id="04ccb-462">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="04ccb-463">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-463">String</span></span>|<span data-ttu-id="04ccb-464">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-464">128 characters</span></span>||<span data-ttu-id="04ccb-465">Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-465">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="04ccb-466">Um `text` `textarea` deles, `number` , , , , `date` `time` `toggle` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-466">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`.</span></span>|
|`parameter.choices`|<span data-ttu-id="04ccb-467">Matriz de Objetos</span><span class="sxs-lookup"><span data-stu-id="04ccb-467">Array of Objects</span></span>|<span data-ttu-id="04ccb-468">10 </span><span class="sxs-lookup"><span data-stu-id="04ccb-468">10</span></span>||<span data-ttu-id="04ccb-469">As opções de escolha para o `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-469">The choice options for the `choiceset`.</span></span> <span data-ttu-id="04ccb-470">Use somente quando `parameter.inputType` estiver `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-470">Use only when `parameter.inputType` is `choiceset`.</span></span>|
|`parameter.choices.title`|<span data-ttu-id="04ccb-471">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-471">String</span></span>|<span data-ttu-id="04ccb-472">128</span><span class="sxs-lookup"><span data-stu-id="04ccb-472">128</span></span>||<span data-ttu-id="04ccb-473">O título da escolha.</span><span class="sxs-lookup"><span data-stu-id="04ccb-473">Title of the choice.</span></span>|
|`parameter.choices.value`|<span data-ttu-id="04ccb-474">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-474">String</span></span>|<span data-ttu-id="04ccb-475">512</span><span class="sxs-lookup"><span data-stu-id="04ccb-475">512</span></span>||<span data-ttu-id="04ccb-476">O valor da escolha.</span><span class="sxs-lookup"><span data-stu-id="04ccb-476">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="04ccb-477">permissões</span><span class="sxs-lookup"><span data-stu-id="04ccb-477">permissions</span></span>

<span data-ttu-id="04ccb-478">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="04ccb-478">**Optional**</span></span>

<span data-ttu-id="04ccb-479">Um conjunto especifica `string` quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão será real.</span><span class="sxs-lookup"><span data-stu-id="04ccb-479">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="04ccb-480">As seguintes opções não são exclusivas:</span><span class="sxs-lookup"><span data-stu-id="04ccb-480">The following options are non-exclusive:</span></span>

* <span data-ttu-id="04ccb-481">`identity`&emsp;Requer informações de identidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="04ccb-481">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="04ccb-482">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="04ccb-482">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="04ccb-483">Alterar essas permissões ao atualizar seu aplicativo fará com que seus usuários repitam o processo de consentimento na primeira vez que executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="04ccb-483">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="04ccb-484">dispositivosPermissões</span><span class="sxs-lookup"><span data-stu-id="04ccb-484">devicePermissions</span></span>

<span data-ttu-id="04ccb-485">**Opcional** Matriz de Cordas</span><span class="sxs-lookup"><span data-stu-id="04ccb-485">**Optional** Array of Strings</span></span>

<span data-ttu-id="04ccb-486">Especifica os recursos nativos no dispositivo do usuário aos quais seu aplicativo pode solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="04ccb-486">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="04ccb-487">As opções são:</span><span class="sxs-lookup"><span data-stu-id="04ccb-487">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="04ccb-488">validDomains</span><span class="sxs-lookup"><span data-stu-id="04ccb-488">validDomains</span></span>

<span data-ttu-id="04ccb-489">**Opcional**, exceto **Necessário** quando observado</span><span class="sxs-lookup"><span data-stu-id="04ccb-489">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="04ccb-490">Uma lista de domínios válidos dos quais o aplicativo espera carregar qualquer conteúdo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-490">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="04ccb-491">As listagens de domínio podem incluir curingas, por `*.example.com` exemplo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-491">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="04ccb-492">Isso corresponde exatamente a um segmento do domínio; se você precisar `a.b.example.com` combinar, então use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-492">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="04ccb-493">Se a configuração da guia ou a interface do conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de guia, esse domínio deve ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="04ccb-493">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="04ccb-494">No entanto, **não** é necessário incluir os domínios dos provedores de identidade que você deseja suportar em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-494">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="04ccb-495">Por exemplo, para autenticar usando um ID do Google, é necessário redirecionar para accounts.google.com, mas você não deve incluir accounts.google.com em `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-495">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04ccb-496">Não adicione domínios que estejam fora do seu controle, diretamente ou através de curingas.</span><span class="sxs-lookup"><span data-stu-id="04ccb-496">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="04ccb-497">Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="04ccb-497">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="04ccb-498">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-498">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="04ccb-499">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="04ccb-499">webApplicationInfo</span></span>

<span data-ttu-id="04ccb-500">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="04ccb-500">**Optional**</span></span>

<span data-ttu-id="04ccb-501">Especifique seu ID do aplicativo AAD e Graph informações para ajudar os usuários a entrar perfeitamente em seu aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="04ccb-501">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="04ccb-502">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-502">Name</span></span>| <span data-ttu-id="04ccb-503">Tipo</span><span class="sxs-lookup"><span data-stu-id="04ccb-503">Type</span></span>| <span data-ttu-id="04ccb-504">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-504">Maximum size</span></span> | <span data-ttu-id="04ccb-505">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-505">Required</span></span> | <span data-ttu-id="04ccb-506">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-506">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="04ccb-507">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-507">String</span></span>|<span data-ttu-id="04ccb-508">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-508">36 characters</span></span>|<span data-ttu-id="04ccb-509">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-509">✔</span></span>|<span data-ttu-id="04ccb-510">ID de aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-510">AAD application id of the app.</span></span> <span data-ttu-id="04ccb-511">Esta id deve ser uma GUID.</span><span class="sxs-lookup"><span data-stu-id="04ccb-511">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="04ccb-512">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-512">String</span></span>|<span data-ttu-id="04ccb-513">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-513">2048 characters</span></span>|<span data-ttu-id="04ccb-514">✔</span><span class="sxs-lookup"><span data-stu-id="04ccb-514">✔</span></span>|<span data-ttu-id="04ccb-515">Url de recurso do aplicativo para aquisição de token auth para SSO.</span><span class="sxs-lookup"><span data-stu-id="04ccb-515">Resource url of app for acquiring auth token for SSO.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="04ccb-516">configurávelProperties</span><span class="sxs-lookup"><span data-stu-id="04ccb-516">configurableProperties</span></span>

<span data-ttu-id="04ccb-517">**Opcionais** - matriz</span><span class="sxs-lookup"><span data-stu-id="04ccb-517">**Optional** - array</span></span>

<span data-ttu-id="04ccb-518">O `configurableProperties` bloco define as propriedades do aplicativo que Teams administrador pode personalizar.</span><span class="sxs-lookup"><span data-stu-id="04ccb-518">The `configurableProperties` block defines the app properties that Teams admin can customize.</span></span> <span data-ttu-id="04ccb-519">Para obter mais informações, consulte [personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="04ccb-519">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="04ccb-520">Um mínimo de uma propriedade deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="04ccb-520">A minimum of one property must be defined.</span></span> <span data-ttu-id="04ccb-521">Você pode definir um máximo de nove propriedades neste bloco.</span><span class="sxs-lookup"><span data-stu-id="04ccb-521">You can define a maximum of nine properties in this block.</span></span>
> <span data-ttu-id="04ccb-522">Como uma prática recomendada, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes seguirem ao personalizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-522">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span> 

<span data-ttu-id="04ccb-523">Você pode definir qualquer uma das seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="04ccb-523">You can define any of the following properties:</span></span>
* <span data-ttu-id="04ccb-524">`name`: Permite que o administrador altere o nome de exibição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-524">`name`: Allows admin to change the app's display name.</span></span>
* <span data-ttu-id="04ccb-525">`shortDescription`: Permite que o administrador altere a descrição curta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-525">`shortDescription`: Allows admin to change the app's short description.</span></span>
* <span data-ttu-id="04ccb-526">`longDescription`: Permite que o administrador altere a descrição detalhada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-526">`longDescription`: Allows admin to change the app's detailed description.</span></span>
* <span data-ttu-id="04ccb-527">`smallImageUrl`: É a `outline` propriedade no bloco do `icons` manifesto.</span><span class="sxs-lookup"><span data-stu-id="04ccb-527">`smallImageUrl`: It is the `outline` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="04ccb-528">`largeImageUrl`: É a `color` propriedade no bloco do `icons` manifesto.</span><span class="sxs-lookup"><span data-stu-id="04ccb-528">`largeImageUrl`: It is the `color` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="04ccb-529">`accentColor`: É a cor para usar em conjunto e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="04ccb-529">`accentColor`: It is the color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="04ccb-530">`websiteUrl`: É a url https:// para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="04ccb-530">`websiteUrl`: It is the https:// URL to the developer's website.</span></span>
* <span data-ttu-id="04ccb-531">`privacyUrl`: É a https:// URL da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="04ccb-531">`privacyUrl`: It is the https:// URL to the developer's privacy policy.</span></span>
* <span data-ttu-id="04ccb-532">`termsOfUseUrl`: É a url https:// para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="04ccb-532">`termsOfUseUrl`: It is the https:// URL to the developer's terms of use.</span></span>

## <a name="defaultinstallscope"></a><span data-ttu-id="04ccb-533">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="04ccb-533">defaultInstallScope</span></span>

<span data-ttu-id="04ccb-534">**Opcional** - string</span><span class="sxs-lookup"><span data-stu-id="04ccb-534">**Optional** - string</span></span>

<span data-ttu-id="04ccb-535">Especifica o escopo de instalação definido para este aplicativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="04ccb-535">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="04ccb-536">O escopo definido será a opção exibida no botão quando um usuário tentar adicionar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-536">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="04ccb-537">As opções são:</span><span class="sxs-lookup"><span data-stu-id="04ccb-537">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="04ccb-538">padrãoGroupCapability</span><span class="sxs-lookup"><span data-stu-id="04ccb-538">defaultGroupCapability</span></span>

<span data-ttu-id="04ccb-539">**Opcional** - objeto</span><span class="sxs-lookup"><span data-stu-id="04ccb-539">**Optional** - object</span></span>

<span data-ttu-id="04ccb-540">Quando um escopo de instalação de grupo é selecionado, ele definirá o recurso padrão quando o usuário instalar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04ccb-540">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="04ccb-541">As opções são:</span><span class="sxs-lookup"><span data-stu-id="04ccb-541">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="04ccb-542">Nome</span><span class="sxs-lookup"><span data-stu-id="04ccb-542">Name</span></span>| <span data-ttu-id="04ccb-543">Tipo</span><span class="sxs-lookup"><span data-stu-id="04ccb-543">Type</span></span>| <span data-ttu-id="04ccb-544">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="04ccb-544">Maximum size</span></span> | <span data-ttu-id="04ccb-545">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="04ccb-545">Required</span></span> | <span data-ttu-id="04ccb-546">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccb-546">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="04ccb-547">string</span><span class="sxs-lookup"><span data-stu-id="04ccb-547">string</span></span>|||<span data-ttu-id="04ccb-548">Quando o escopo de instalação selecionado `team` é, este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="04ccb-548">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="04ccb-549">Opções: `tab` `bot` , , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-549">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="04ccb-550">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-550">string</span></span>|||<span data-ttu-id="04ccb-551">Quando o escopo de instalação selecionado `groupchat` é, este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="04ccb-551">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="04ccb-552">Opções: `tab` `bot` , , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-552">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="04ccb-553">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04ccb-553">string</span></span>|||<span data-ttu-id="04ccb-554">Quando o escopo de instalação selecionado `meetings` é, este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="04ccb-554">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="04ccb-555">Opções: `tab` `bot` , , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="04ccb-555">Options: `tab`, `bot`, or `connector`.</span></span>|

