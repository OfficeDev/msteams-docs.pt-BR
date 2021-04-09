---
title: Referência do esquema de Manifesto de Visualização do Desenvolvedor
description: Descreve o esquema suportado pelo manifesto do Microsoft Teams
ms.topic: reference
keywords: Teams manifest schema Developer Preview
ms.date: 05/20/2019
ms.openlocfilehash: f8c1842d6b9f9d07d8743f5bf7f868cacbd282af
ms.sourcegitcommit: b50f6d68482cad43a60642a9947d1be17809a7df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634485"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="872cb-104">Esquema de manifesto de visualização do desenvolvedor para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="872cb-104">Developer preview manifest schema for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="872cb-105">Consulte [Visualização do](~/resources/dev-preview/developer-preview-intro.md) Desenvolvedor para obter informações sobre o programa e como você pode participar.</span><span class="sxs-lookup"><span data-stu-id="872cb-105">See [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for information on the program and how you can join.</span></span>
> <span data-ttu-id="872cb-106">Se você não estiver usando a visualização do desenvolvedor, não deverá usar essa versão do manifesto.</span><span class="sxs-lookup"><span data-stu-id="872cb-106">If you are not using the developer preview you should not be using this version of the manifest.</span></span> <span data-ttu-id="872cb-107">Consulte [Referência: Esquema de manifesto do Microsoft Teams](~/resources/schema/manifest-schema.md) para a versão pública do manifesto.</span><span class="sxs-lookup"><span data-stu-id="872cb-107">See [Reference: Manifest schema for Microsoft Teams](~/resources/schema/manifest-schema.md) for the public version of the manifest.</span></span>

<span data-ttu-id="872cb-108">O manifesto do Microsoft Teams descreve como o aplicativo se integra ao produto do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="872cb-108">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="872cb-109">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="872cb-109">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="872cb-110">Para obter mais informações sobre os recursos disponíveis, consulte: [Recursos na Visualização](~/resources/dev-preview/developer-preview-features.md)de Desenvolvedor Público do Microsoft Teams .</span><span class="sxs-lookup"><span data-stu-id="872cb-110">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="872cb-111">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="872cb-111">Sample full manifest</span></span>

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
  ]              
}
```

<span data-ttu-id="872cb-112">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="872cb-112">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="872cb-113">$schema</span><span class="sxs-lookup"><span data-stu-id="872cb-113">$schema</span></span>

<span data-ttu-id="872cb-114">*Opcional, mas recomendado* &ndash; Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-114">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="872cb-115">A https:// URL de referência do Esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="872cb-115">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="872cb-116">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="872cb-116">manifestVersion</span></span>

<span data-ttu-id="872cb-117">**Obrigatório** &ndash; Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-117">**Required** &ndash; String</span></span>

<span data-ttu-id="872cb-118">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="872cb-118">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="872cb-119">Deve ser "devPreview".</span><span class="sxs-lookup"><span data-stu-id="872cb-119">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="872cb-120">versão</span><span class="sxs-lookup"><span data-stu-id="872cb-120">version</span></span>

<span data-ttu-id="872cb-121">**Obrigatório** &ndash; Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-121">**Required** &ndash; String</span></span>

<span data-ttu-id="872cb-122">A versão do aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="872cb-122">The version of the specific app.</span></span> <span data-ttu-id="872cb-123">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="872cb-123">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="872cb-124">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="872cb-124">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="872cb-125">Se esse aplicativo foi enviado para a loja, o novo manifesto terá que ser re-enviado e validado.</span><span class="sxs-lookup"><span data-stu-id="872cb-125">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="872cb-126">Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, depois que ele for aprovado.</span><span class="sxs-lookup"><span data-stu-id="872cb-126">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="872cb-127">Se as permissões solicitadas pelo aplicativo mudarem, os usuários serão solicitados a atualizar e consentir de novo no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-127">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="872cb-128">Esta cadeia de caracteres de versão deve seguir o padrão [de semver](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="872cb-128">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="872cb-129">id</span><span class="sxs-lookup"><span data-stu-id="872cb-129">id</span></span>

<span data-ttu-id="872cb-130">**Obrigatório** &ndash; ID do aplicativo Microsoft</span><span class="sxs-lookup"><span data-stu-id="872cb-130">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="872cb-131">O identificador exclusivo gerado pela Microsoft para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-131">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="872cb-132">Se você registrou um bot por meio da Estrutura do Microsoft Bot, ou o aplicativo Web da sua guia já entra com a Microsoft, você já deve ter uma ID e deve insira-a aqui.</span><span class="sxs-lookup"><span data-stu-id="872cb-132">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="872cb-133">Caso contrário, você deve gerar uma nova ID no Portal de Registro de Aplicativos da Microsoft ([Meus](https://apps.dev.microsoft.com)Aplicativos ), insira-o aqui e, em seguida, reutiliza-o quando você [adiciona um bot](~/bots/how-to/create-a-bot-for-teams.md).</span><span class="sxs-lookup"><span data-stu-id="872cb-133">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="872cb-134">packageName</span><span class="sxs-lookup"><span data-stu-id="872cb-134">packageName</span></span>

<span data-ttu-id="872cb-135">**Obrigatório** &ndash; Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-135">**Required** &ndash; String</span></span>

<span data-ttu-id="872cb-136">Um identificador exclusivo para este aplicativo na notação de domínio reverso; por exemplo, com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="872cb-136">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="872cb-137">developer</span><span class="sxs-lookup"><span data-stu-id="872cb-137">developer</span></span>

<span data-ttu-id="872cb-138">**Required**</span><span class="sxs-lookup"><span data-stu-id="872cb-138">**Required**</span></span>

<span data-ttu-id="872cb-139">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="872cb-139">Specifies information about your company.</span></span> <span data-ttu-id="872cb-140">Para aplicativos enviados ao AppSource (antigo Office Store), esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="872cb-140">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="872cb-141">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-141">Name</span></span>| <span data-ttu-id="872cb-142">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-142">Maximum size</span></span> | <span data-ttu-id="872cb-143">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-143">Required</span></span> | <span data-ttu-id="872cb-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="872cb-145">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-145">32 characters</span></span>|<span data-ttu-id="872cb-146">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-146">✔</span></span>|<span data-ttu-id="872cb-147">O nome de exibição do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="872cb-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="872cb-148">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-148">2048 characters</span></span>|<span data-ttu-id="872cb-149">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-149">✔</span></span>|<span data-ttu-id="872cb-150">A https:// URL do site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="872cb-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="872cb-151">Este link deve levar os usuários para a sua empresa ou página de aterrissagem específica do produto.</span><span class="sxs-lookup"><span data-stu-id="872cb-151">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="872cb-152">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-152">2048 characters</span></span>|<span data-ttu-id="872cb-153">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-153">✔</span></span>|<span data-ttu-id="872cb-154">A https:// URL da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="872cb-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="872cb-155">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-155">2048 characters</span></span>|<span data-ttu-id="872cb-156">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-156">✔</span></span>|<span data-ttu-id="872cb-157">A https:// URL dos termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="872cb-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="872cb-158">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-158">10 characters</span></span>|<span data-ttu-id="872cb-159">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-159">✔</span></span>|<span data-ttu-id="872cb-160">**Opcional** A ID da Rede de Parceiros da Microsoft que identifica a organização do parceiro que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-160">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="872cb-161">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="872cb-161">localizationInfo</span></span>

<span data-ttu-id="872cb-162">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="872cb-162">**Optional**</span></span>

<span data-ttu-id="872cb-163">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="872cb-163">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="872cb-164">Consulte [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="872cb-164">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="872cb-165">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-165">Name</span></span>| <span data-ttu-id="872cb-166">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-166">Maximum size</span></span> | <span data-ttu-id="872cb-167">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-167">Required</span></span> | <span data-ttu-id="872cb-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-168">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="872cb-169">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-169">4 characters</span></span>|<span data-ttu-id="872cb-170">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-170">✔</span></span>|<span data-ttu-id="872cb-171">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="872cb-171">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="872cb-172">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="872cb-172">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="872cb-173">Uma matriz de objetos que especifica traduções de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="872cb-173">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="872cb-174">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-174">Name</span></span>| <span data-ttu-id="872cb-175">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-175">Maximum size</span></span> | <span data-ttu-id="872cb-176">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-176">Required</span></span> | <span data-ttu-id="872cb-177">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-177">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="872cb-178">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-178">4 characters</span></span>|<span data-ttu-id="872cb-179">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-179">✔</span></span>|<span data-ttu-id="872cb-180">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="872cb-180">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="872cb-181">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-181">4 characters</span></span>|<span data-ttu-id="872cb-182">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-182">✔</span></span>|<span data-ttu-id="872cb-183">Um caminho de arquivo relativo para um arquivo .json que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="872cb-183">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="872cb-184">nome</span><span class="sxs-lookup"><span data-stu-id="872cb-184">name</span></span>

<span data-ttu-id="872cb-185">**Required**</span><span class="sxs-lookup"><span data-stu-id="872cb-185">**Required**</span></span>

<span data-ttu-id="872cb-186">O nome da experiência do aplicativo, exibido para os usuários na experiência do Teams.</span><span class="sxs-lookup"><span data-stu-id="872cb-186">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="872cb-187">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="872cb-187">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="872cb-188">Os valores de `short` e não devem ser os `full` mesmos.</span><span class="sxs-lookup"><span data-stu-id="872cb-188">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="872cb-189">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-189">Name</span></span>| <span data-ttu-id="872cb-190">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-190">Maximum size</span></span> | <span data-ttu-id="872cb-191">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-191">Required</span></span> | <span data-ttu-id="872cb-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-192">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="872cb-193">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-193">30 characters</span></span>|<span data-ttu-id="872cb-194">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-194">✔</span></span>|<span data-ttu-id="872cb-195">O nome de exibição curto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-195">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="872cb-196">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-196">100 characters</span></span>||<span data-ttu-id="872cb-197">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="872cb-197">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="872cb-198">description</span><span class="sxs-lookup"><span data-stu-id="872cb-198">description</span></span>

<span data-ttu-id="872cb-199">**Required**</span><span class="sxs-lookup"><span data-stu-id="872cb-199">**Required**</span></span>

<span data-ttu-id="872cb-200">Descreve seu aplicativo para usuários.</span><span class="sxs-lookup"><span data-stu-id="872cb-200">Describes your app to users.</span></span> <span data-ttu-id="872cb-201">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="872cb-201">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="872cb-202">Verifique se sua descrição descreve com precisão sua experiência e fornece informações para ajudar os clientes em potencial a entender o que sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="872cb-202">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="872cb-203">Você também deve observar, na descrição completa, se uma conta externa for necessária para uso.</span><span class="sxs-lookup"><span data-stu-id="872cb-203">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="872cb-204">Os valores de `short` e não devem ser os `full` mesmos.</span><span class="sxs-lookup"><span data-stu-id="872cb-204">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="872cb-205">Sua breve descrição não deve ser repetida na descrição longa e não deve incluir nenhum outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-205">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="872cb-206">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-206">Name</span></span>| <span data-ttu-id="872cb-207">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-207">Maximum size</span></span> | <span data-ttu-id="872cb-208">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-208">Required</span></span> | <span data-ttu-id="872cb-209">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-209">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="872cb-210">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-210">80 characters</span></span>|<span data-ttu-id="872cb-211">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-211">✔</span></span>|<span data-ttu-id="872cb-212">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="872cb-212">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="872cb-213">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-213">4000 characters</span></span>|<span data-ttu-id="872cb-214">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-214">✔</span></span>|<span data-ttu-id="872cb-215">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-215">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="872cb-216">ícones</span><span class="sxs-lookup"><span data-stu-id="872cb-216">icons</span></span>

<span data-ttu-id="872cb-217">**Required**</span><span class="sxs-lookup"><span data-stu-id="872cb-217">**Required**</span></span>

<span data-ttu-id="872cb-218">Ícones usados no aplicativo teams.</span><span class="sxs-lookup"><span data-stu-id="872cb-218">Icons used within the Teams app.</span></span> <span data-ttu-id="872cb-219">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="872cb-219">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="872cb-220">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-220">Name</span></span>| <span data-ttu-id="872cb-221">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-221">Maximum size</span></span> | <span data-ttu-id="872cb-222">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-222">Required</span></span> | <span data-ttu-id="872cb-223">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="872cb-224">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-224">2048 characters</span></span>|<span data-ttu-id="872cb-225">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-225">✔</span></span>|<span data-ttu-id="872cb-226">Um caminho de arquivo relativo para um ícone de contorno PNG 32x32 transparente.</span><span class="sxs-lookup"><span data-stu-id="872cb-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="872cb-227">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-227">2048 characters</span></span>|<span data-ttu-id="872cb-228">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-228">✔</span></span>|<span data-ttu-id="872cb-229">Um caminho de arquivo relativo para um ícone PNG de cor total 192x192.</span><span class="sxs-lookup"><span data-stu-id="872cb-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="872cb-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="872cb-230">accentColor</span></span>

<span data-ttu-id="872cb-231">**Obrigatório** &ndash; Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-231">**Required** &ndash; String</span></span>

<span data-ttu-id="872cb-232">Uma cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="872cb-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="872cb-233">O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="872cb-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="872cb-234">configurbleTabs</span><span class="sxs-lookup"><span data-stu-id="872cb-234">configurableTabs</span></span>

<span data-ttu-id="872cb-235">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="872cb-235">**Optional**</span></span>

<span data-ttu-id="872cb-236">Usado quando a experiência do aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="872cb-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="872cb-237">As guias configuráveis têm suporte apenas no escopo das equipes e, atualmente, há suporte para apenas uma guia por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-237">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="872cb-238">O objeto é uma matriz com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="872cb-238">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="872cb-239">Esse bloco é necessário apenas para soluções que fornecem uma solução de guia de canal configurável.</span><span class="sxs-lookup"><span data-stu-id="872cb-239">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="872cb-240">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-240">Name</span></span>| <span data-ttu-id="872cb-241">Tipo</span><span class="sxs-lookup"><span data-stu-id="872cb-241">Type</span></span>| <span data-ttu-id="872cb-242">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-242">Maximum size</span></span> | <span data-ttu-id="872cb-243">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-243">Required</span></span> | <span data-ttu-id="872cb-244">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="872cb-245">String</span><span class="sxs-lookup"><span data-stu-id="872cb-245">String</span></span>|<span data-ttu-id="872cb-246">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-246">2048 characters</span></span>|<span data-ttu-id="872cb-247">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-247">✔</span></span>|<span data-ttu-id="872cb-248">A https:// URL a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="872cb-248">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="872cb-249">Booliano</span><span class="sxs-lookup"><span data-stu-id="872cb-249">Boolean</span></span>|||<span data-ttu-id="872cb-250">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="872cb-250">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="872cb-251">Padrão: `true`</span><span class="sxs-lookup"><span data-stu-id="872cb-251">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="872cb-252">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="872cb-252">Array of enum</span></span>|<span data-ttu-id="872cb-253">1</span><span class="sxs-lookup"><span data-stu-id="872cb-253">1</span></span>|<span data-ttu-id="872cb-254">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-254">✔</span></span>|<span data-ttu-id="872cb-255">Atualmente, as guias configuráveis suportam apenas `team` os `groupchat` escopos e.</span><span class="sxs-lookup"><span data-stu-id="872cb-255">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="872cb-256">String</span><span class="sxs-lookup"><span data-stu-id="872cb-256">String</span></span>|<span data-ttu-id="872cb-257">2048</span><span class="sxs-lookup"><span data-stu-id="872cb-257">2048</span></span>||<span data-ttu-id="872cb-258">Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="872cb-258">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="872cb-259">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="872cb-259">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="872cb-260">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="872cb-260">Array of enum</span></span>|<span data-ttu-id="872cb-261">1</span><span class="sxs-lookup"><span data-stu-id="872cb-261">1</span></span>||<span data-ttu-id="872cb-262">Define como sua guia será disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="872cb-262">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="872cb-263">As opções `sharePointFullPage` são e `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="872cb-263">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="872cb-264">staticTabs</span><span class="sxs-lookup"><span data-stu-id="872cb-264">staticTabs</span></span>

<span data-ttu-id="872cb-265">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="872cb-265">**Optional**</span></span>

<span data-ttu-id="872cb-266">Define um conjunto de guias que podem ser "fixados" por padrão, sem que o usuário as adicione manualmente.</span><span class="sxs-lookup"><span data-stu-id="872cb-266">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="872cb-267">As guias estáticas declaradas no `personal` escopo são sempre fixadas à experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-267">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="872cb-268">No momento, as guias estáticas declaradas no `team` escopo não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="872cb-268">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="872cb-269">O objeto é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="872cb-269">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="872cb-270">Esse bloco só é necessário para soluções que fornecem uma solução de tabulação estática.</span><span class="sxs-lookup"><span data-stu-id="872cb-270">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="872cb-271">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-271">Name</span></span>| <span data-ttu-id="872cb-272">Tipo</span><span class="sxs-lookup"><span data-stu-id="872cb-272">Type</span></span>| <span data-ttu-id="872cb-273">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-273">Maximum size</span></span> | <span data-ttu-id="872cb-274">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-274">Required</span></span> | <span data-ttu-id="872cb-275">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-275">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="872cb-276">String</span><span class="sxs-lookup"><span data-stu-id="872cb-276">String</span></span>|<span data-ttu-id="872cb-277">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-277">64 characters</span></span>|<span data-ttu-id="872cb-278">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-278">✔</span></span>|<span data-ttu-id="872cb-279">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="872cb-279">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="872cb-280">String</span><span class="sxs-lookup"><span data-stu-id="872cb-280">String</span></span>|<span data-ttu-id="872cb-281">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-281">128 characters</span></span>|<span data-ttu-id="872cb-282">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-282">✔</span></span>|<span data-ttu-id="872cb-283">O nome de exibição da guia na interface do canal.</span><span class="sxs-lookup"><span data-stu-id="872cb-283">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="872cb-284">String</span><span class="sxs-lookup"><span data-stu-id="872cb-284">String</span></span>|<span data-ttu-id="872cb-285">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-285">2048 characters</span></span>|<span data-ttu-id="872cb-286">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-286">✔</span></span>|<span data-ttu-id="872cb-287">A https:// URL que aponta para a interface do usuário da entidade a ser exibida na tela do Teams.</span><span class="sxs-lookup"><span data-stu-id="872cb-287">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="872cb-288">String</span><span class="sxs-lookup"><span data-stu-id="872cb-288">String</span></span>|<span data-ttu-id="872cb-289">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-289">2048 characters</span></span>||<span data-ttu-id="872cb-290">A https:// URL para apontar se um usuário optar por exibir em um navegador.</span><span class="sxs-lookup"><span data-stu-id="872cb-290">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="872cb-291">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="872cb-291">Array of enum</span></span>|<span data-ttu-id="872cb-292">1</span><span class="sxs-lookup"><span data-stu-id="872cb-292">1</span></span>|<span data-ttu-id="872cb-293">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-293">✔</span></span>|<span data-ttu-id="872cb-294">Atualmente, as guias estáticas suportam apenas o escopo, o que significa que ele só pode ser `personal` provisionado como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="872cb-294">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="872cb-295">bots</span><span class="sxs-lookup"><span data-stu-id="872cb-295">bots</span></span>

<span data-ttu-id="872cb-296">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="872cb-296">**Optional**</span></span>

<span data-ttu-id="872cb-297">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="872cb-297">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="872cb-298">O objeto é uma matriz (no máximo, apenas 1 elemento atualmente, apenas um bot é permitido por aplicativo) com todos os &mdash; elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="872cb-298">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="872cb-299">Esse bloco só é necessário para soluções que fornecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="872cb-299">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="872cb-300">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-300">Name</span></span>| <span data-ttu-id="872cb-301">Tipo</span><span class="sxs-lookup"><span data-stu-id="872cb-301">Type</span></span>| <span data-ttu-id="872cb-302">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-302">Maximum size</span></span> | <span data-ttu-id="872cb-303">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-303">Required</span></span> | <span data-ttu-id="872cb-304">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-304">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="872cb-305">String</span><span class="sxs-lookup"><span data-stu-id="872cb-305">String</span></span>|<span data-ttu-id="872cb-306">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-306">64 characters</span></span>|<span data-ttu-id="872cb-307">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-307">✔</span></span>|<span data-ttu-id="872cb-308">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="872cb-308">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="872cb-309">Isso pode ser o mesmo da ID geral [do aplicativo.](#id)</span><span class="sxs-lookup"><span data-stu-id="872cb-309">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="872cb-310">Boolean</span><span class="sxs-lookup"><span data-stu-id="872cb-310">Boolean</span></span>|||<span data-ttu-id="872cb-311">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="872cb-311">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="872cb-312">Padrão: `false`</span><span class="sxs-lookup"><span data-stu-id="872cb-312">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="872cb-313">Boolean</span><span class="sxs-lookup"><span data-stu-id="872cb-313">Boolean</span></span>|||<span data-ttu-id="872cb-314">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="872cb-314">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="872cb-315">Padrão: `false`</span><span class="sxs-lookup"><span data-stu-id="872cb-315">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="872cb-316">Boolean</span><span class="sxs-lookup"><span data-stu-id="872cb-316">Boolean</span></span>|||<span data-ttu-id="872cb-317">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="872cb-317">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="872cb-318">Padrão: `false`</span><span class="sxs-lookup"><span data-stu-id="872cb-318">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="872cb-319">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="872cb-319">Array of enum</span></span>|<span data-ttu-id="872cb-320">3</span><span class="sxs-lookup"><span data-stu-id="872cb-320">3</span></span>|<span data-ttu-id="872cb-321">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-321">✔</span></span>|<span data-ttu-id="872cb-322">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="872cb-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="872cb-323">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="872cb-323">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="872cb-324">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="872cb-324">bots.commandLists</span></span>

<span data-ttu-id="872cb-325">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="872cb-325">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="872cb-326">O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo; você deve definir uma lista de comandos separada para cada escopo que `object` seu bot oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="872cb-326">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="872cb-327">Consulte [Menus bot para](~/bots/how-to/create-a-bot-commands-menu.md) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="872cb-327">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="872cb-328">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-328">Name</span></span>| <span data-ttu-id="872cb-329">Tipo</span><span class="sxs-lookup"><span data-stu-id="872cb-329">Type</span></span>| <span data-ttu-id="872cb-330">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-330">Maximum size</span></span> | <span data-ttu-id="872cb-331">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-331">Required</span></span> | <span data-ttu-id="872cb-332">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-332">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="872cb-333">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="872cb-333">array of enum</span></span>|<span data-ttu-id="872cb-334">3</span><span class="sxs-lookup"><span data-stu-id="872cb-334">3</span></span>|<span data-ttu-id="872cb-335">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-335">✔</span></span>|<span data-ttu-id="872cb-336">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="872cb-336">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="872cb-337">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="872cb-337">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="872cb-338">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="872cb-338">array of objects</span></span>|<span data-ttu-id="872cb-339">10 </span><span class="sxs-lookup"><span data-stu-id="872cb-339">10</span></span>|<span data-ttu-id="872cb-340">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-340">✔</span></span>|<span data-ttu-id="872cb-341">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="872cb-341">An array of commands the bot supports:</span></span><br><span data-ttu-id="872cb-342">`title`: o nome do comando bot (cadeia, 32)</span><span class="sxs-lookup"><span data-stu-id="872cb-342">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="872cb-343">`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)</span><span class="sxs-lookup"><span data-stu-id="872cb-343">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

## <a name="connectors"></a><span data-ttu-id="872cb-344">conectores</span><span class="sxs-lookup"><span data-stu-id="872cb-344">connectors</span></span>

<span data-ttu-id="872cb-345">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="872cb-345">**Optional**</span></span>

<span data-ttu-id="872cb-346">O `connectors` bloco define um Conector do Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-346">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="872cb-347">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="872cb-347">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="872cb-348">Esse bloco só é necessário para soluções que fornecem um Conector.</span><span class="sxs-lookup"><span data-stu-id="872cb-348">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="872cb-349">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-349">Name</span></span>| <span data-ttu-id="872cb-350">Tipo</span><span class="sxs-lookup"><span data-stu-id="872cb-350">Type</span></span>| <span data-ttu-id="872cb-351">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-351">Maximum size</span></span> | <span data-ttu-id="872cb-352">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-352">Required</span></span> | <span data-ttu-id="872cb-353">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-353">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="872cb-354">String</span><span class="sxs-lookup"><span data-stu-id="872cb-354">String</span></span>|<span data-ttu-id="872cb-355">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-355">2048 characters</span></span>|<span data-ttu-id="872cb-356">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-356">✔</span></span>|<span data-ttu-id="872cb-357">A https:// URL a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="872cb-357">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="872cb-358">String</span><span class="sxs-lookup"><span data-stu-id="872cb-358">String</span></span>|<span data-ttu-id="872cb-359">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-359">64 characters</span></span>|<span data-ttu-id="872cb-360">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-360">✔</span></span>|<span data-ttu-id="872cb-361">Um identificador exclusivo para o Conector que corresponde à sua ID no [Painel do Desenvolvedor de Conectores.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="872cb-361">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="872cb-362">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="872cb-362">Array of enum</span></span>|<span data-ttu-id="872cb-363">1</span><span class="sxs-lookup"><span data-stu-id="872cb-363">1</span></span>|<span data-ttu-id="872cb-364">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-364">✔</span></span>|<span data-ttu-id="872cb-365">Especifica se o Conector oferece uma experiência no contexto de um canal em um , ou uma experiência com escopo apenas para um `team` usuário individual ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="872cb-365">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="872cb-366">Atualmente, apenas o `team` escopo é suportado.</span><span class="sxs-lookup"><span data-stu-id="872cb-366">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="872cb-367">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="872cb-367">composeExtensions</span></span>

<span data-ttu-id="872cb-368">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="872cb-368">**Optional**</span></span>

<span data-ttu-id="872cb-369">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-369">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="872cb-370">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem funcionando.</span><span class="sxs-lookup"><span data-stu-id="872cb-370">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="872cb-371">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="872cb-371">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="872cb-372">Esse bloco só é necessário para soluções que fornecem uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="872cb-372">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="872cb-373">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-373">Name</span></span>| <span data-ttu-id="872cb-374">Tipo</span><span class="sxs-lookup"><span data-stu-id="872cb-374">Type</span></span> | <span data-ttu-id="872cb-375">Tamanho Máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-375">Maximum Size</span></span> | <span data-ttu-id="872cb-376">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-376">Required</span></span> | <span data-ttu-id="872cb-377">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-377">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="872cb-378">String</span><span class="sxs-lookup"><span data-stu-id="872cb-378">String</span></span>|<span data-ttu-id="872cb-379">64</span><span class="sxs-lookup"><span data-stu-id="872cb-379">64</span></span>|<span data-ttu-id="872cb-380">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-380">✔</span></span>|<span data-ttu-id="872cb-381">A ID de aplicativo exclusiva da Microsoft para o bot que é o suporte à extensão de mensagens, conforme registrado na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="872cb-381">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="872cb-382">Isso pode ser o mesmo da ID geral [do aplicativo.](#id)</span><span class="sxs-lookup"><span data-stu-id="872cb-382">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="872cb-383">Booliano</span><span class="sxs-lookup"><span data-stu-id="872cb-383">Boolean</span></span>|||<span data-ttu-id="872cb-384">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="872cb-384">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="872cb-385">O padrão é `false` .</span><span class="sxs-lookup"><span data-stu-id="872cb-385">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="872cb-386">Matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="872cb-386">Array of object</span></span>|<span data-ttu-id="872cb-387">10 </span><span class="sxs-lookup"><span data-stu-id="872cb-387">10</span></span>|<span data-ttu-id="872cb-388">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-388">✔</span></span>|<span data-ttu-id="872cb-389">Matriz de comandos com suporte da extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="872cb-389">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="872cb-390">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="872cb-390">composeExtensions.commands</span></span>

<span data-ttu-id="872cb-391">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="872cb-391">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="872cb-392">Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="872cb-392">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="872cb-393">Há no máximo 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="872cb-393">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="872cb-394">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="872cb-394">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="872cb-395">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-395">Name</span></span>| <span data-ttu-id="872cb-396">Tipo</span><span class="sxs-lookup"><span data-stu-id="872cb-396">Type</span></span>| <span data-ttu-id="872cb-397">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-397">Maximum size</span></span> | <span data-ttu-id="872cb-398">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-398">Required</span></span> | <span data-ttu-id="872cb-399">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-399">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="872cb-400">String</span><span class="sxs-lookup"><span data-stu-id="872cb-400">String</span></span>|<span data-ttu-id="872cb-401">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-401">64 characters</span></span>|<span data-ttu-id="872cb-402">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-402">✔</span></span>|<span data-ttu-id="872cb-403">A ID do comando</span><span class="sxs-lookup"><span data-stu-id="872cb-403">The ID for the command</span></span>|
|`type`|<span data-ttu-id="872cb-404">String</span><span class="sxs-lookup"><span data-stu-id="872cb-404">String</span></span>|<span data-ttu-id="872cb-405">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-405">64 characters</span></span>||<span data-ttu-id="872cb-406">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="872cb-406">Type of the command.</span></span> <span data-ttu-id="872cb-407">Um dos `query` ou `action` .</span><span class="sxs-lookup"><span data-stu-id="872cb-407">One of `query` or `action`.</span></span> <span data-ttu-id="872cb-408">Padrão: `query`</span><span class="sxs-lookup"><span data-stu-id="872cb-408">Default: `query`</span></span>|
|`title`|<span data-ttu-id="872cb-409">String</span><span class="sxs-lookup"><span data-stu-id="872cb-409">String</span></span>|<span data-ttu-id="872cb-410">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-410">32 characters</span></span>|<span data-ttu-id="872cb-411">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-411">✔</span></span>|<span data-ttu-id="872cb-412">O nome de comando amigável</span><span class="sxs-lookup"><span data-stu-id="872cb-412">The user-friendly command name</span></span>|
|`description`|<span data-ttu-id="872cb-413">String</span><span class="sxs-lookup"><span data-stu-id="872cb-413">String</span></span>|<span data-ttu-id="872cb-414">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-414">128 characters</span></span>||<span data-ttu-id="872cb-415">A descrição que aparece para os usuários para indicar a finalidade deste comando</span><span class="sxs-lookup"><span data-stu-id="872cb-415">The description that appears to users to indicate the purpose of this command</span></span>|
|`initialRun`|<span data-ttu-id="872cb-416">Booliano</span><span class="sxs-lookup"><span data-stu-id="872cb-416">Boolean</span></span>|||<span data-ttu-id="872cb-417">Um valor Boolean que indica se o comando deve ser executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="872cb-417">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="872cb-418">Padrão: `false`</span><span class="sxs-lookup"><span data-stu-id="872cb-418">Default: `false`</span></span>|
|`context`|<span data-ttu-id="872cb-419">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-419">Array of Strings</span></span>|<span data-ttu-id="872cb-420">3</span><span class="sxs-lookup"><span data-stu-id="872cb-420">3</span></span>||<span data-ttu-id="872cb-421">Define de onde a extensão da mensagem pode ser invocada.</span><span class="sxs-lookup"><span data-stu-id="872cb-421">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="872cb-422">Qualquer combinação `compose` de , , `commandBox` `message` .</span><span class="sxs-lookup"><span data-stu-id="872cb-422">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="872cb-423">O padrão é `["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="872cb-423">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="872cb-424">Booliano</span><span class="sxs-lookup"><span data-stu-id="872cb-424">Boolean</span></span>|||<span data-ttu-id="872cb-425">Um valor booleano que indica se ele deve buscar o módulo de tarefa dinamicamente</span><span class="sxs-lookup"><span data-stu-id="872cb-425">A boolean value that indicates if it should fetch the task module dynamically</span></span>|
|`taskInfo`|<span data-ttu-id="872cb-426">Objeto</span><span class="sxs-lookup"><span data-stu-id="872cb-426">Object</span></span>|||<span data-ttu-id="872cb-427">Especificar o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="872cb-427">Specify the task module to preload when using a messaging extension command</span></span>|
|`taskInfo.title`|<span data-ttu-id="872cb-428">String</span><span class="sxs-lookup"><span data-stu-id="872cb-428">String</span></span>|<span data-ttu-id="872cb-429">64</span><span class="sxs-lookup"><span data-stu-id="872cb-429">64</span></span>||<span data-ttu-id="872cb-430">Título da caixa de diálogo inicial</span><span class="sxs-lookup"><span data-stu-id="872cb-430">Initial dialog title</span></span>|
|`taskInfo.width`|<span data-ttu-id="872cb-431">String</span><span class="sxs-lookup"><span data-stu-id="872cb-431">String</span></span>|||<span data-ttu-id="872cb-432">Largura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'</span><span class="sxs-lookup"><span data-stu-id="872cb-432">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.height`|<span data-ttu-id="872cb-433">String</span><span class="sxs-lookup"><span data-stu-id="872cb-433">String</span></span>|||<span data-ttu-id="872cb-434">Altura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'</span><span class="sxs-lookup"><span data-stu-id="872cb-434">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.url`|<span data-ttu-id="872cb-435">String</span><span class="sxs-lookup"><span data-stu-id="872cb-435">String</span></span>|||<span data-ttu-id="872cb-436">URL do webview inicial</span><span class="sxs-lookup"><span data-stu-id="872cb-436">Initial webview URL</span></span>|
|`messageHandlers`|<span data-ttu-id="872cb-437">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="872cb-437">Array of Objects</span></span>|<span data-ttu-id="872cb-438">5 </span><span class="sxs-lookup"><span data-stu-id="872cb-438">5</span></span>||<span data-ttu-id="872cb-439">Uma lista de manipuladores que permitem que os aplicativos sejam invocados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="872cb-439">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="872cb-440">Os domínios também devem ser listados em `validDomains`</span><span class="sxs-lookup"><span data-stu-id="872cb-440">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="872cb-441">String</span><span class="sxs-lookup"><span data-stu-id="872cb-441">String</span></span>|||<span data-ttu-id="872cb-442">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="872cb-442">The type of message handler.</span></span> <span data-ttu-id="872cb-443">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="872cb-443">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="872cb-444">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-444">Array of Strings</span></span>|||<span data-ttu-id="872cb-445">Matriz de domínios que o manipulador de mensagens de link pode registrar.</span><span class="sxs-lookup"><span data-stu-id="872cb-445">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="872cb-446">Matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="872cb-446">Array of object</span></span>|<span data-ttu-id="872cb-447">5 </span><span class="sxs-lookup"><span data-stu-id="872cb-447">5</span></span>|<span data-ttu-id="872cb-448">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-448">✔</span></span>|<span data-ttu-id="872cb-449">A lista de parâmetros que o comando assume.</span><span class="sxs-lookup"><span data-stu-id="872cb-449">The list of parameters the command takes.</span></span> <span data-ttu-id="872cb-450">Mínimo: 1; máximo: 5</span><span class="sxs-lookup"><span data-stu-id="872cb-450">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="872cb-451">String</span><span class="sxs-lookup"><span data-stu-id="872cb-451">String</span></span>|<span data-ttu-id="872cb-452">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-452">64 characters</span></span>|<span data-ttu-id="872cb-453">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-453">✔</span></span>|<span data-ttu-id="872cb-454">O nome do parâmetro como ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="872cb-454">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="872cb-455">Isso está incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="872cb-455">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="872cb-456">String</span><span class="sxs-lookup"><span data-stu-id="872cb-456">String</span></span>|<span data-ttu-id="872cb-457">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-457">32 characters</span></span>|<span data-ttu-id="872cb-458">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-458">✔</span></span>|<span data-ttu-id="872cb-459">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="872cb-459">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="872cb-460">String</span><span class="sxs-lookup"><span data-stu-id="872cb-460">String</span></span>|<span data-ttu-id="872cb-461">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-461">128 characters</span></span>||<span data-ttu-id="872cb-462">Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="872cb-462">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="872cb-463">String</span><span class="sxs-lookup"><span data-stu-id="872cb-463">String</span></span>|<span data-ttu-id="872cb-464">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-464">128 characters</span></span>||<span data-ttu-id="872cb-465">Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="872cb-465">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="872cb-466">Um dos `text` , , , , , `textarea` `number` `date` `time` `toggle` , `choiceset`</span><span class="sxs-lookup"><span data-stu-id="872cb-466">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`</span></span>|
|`parameter.choices`|<span data-ttu-id="872cb-467">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="872cb-467">Array of Objects</span></span>|<span data-ttu-id="872cb-468">10 </span><span class="sxs-lookup"><span data-stu-id="872cb-468">10</span></span>||<span data-ttu-id="872cb-469">As opções de escolha para `choiceset` o .</span><span class="sxs-lookup"><span data-stu-id="872cb-469">The choice options for the `choiceset`.</span></span> <span data-ttu-id="872cb-470">Usar somente quando `parameter.inputType` for `choiceset`</span><span class="sxs-lookup"><span data-stu-id="872cb-470">Use only when `parameter.inputType` is `choiceset`</span></span>|
|`parameter.choices.title`|<span data-ttu-id="872cb-471">String</span><span class="sxs-lookup"><span data-stu-id="872cb-471">String</span></span>|<span data-ttu-id="872cb-472">128</span><span class="sxs-lookup"><span data-stu-id="872cb-472">128</span></span>||<span data-ttu-id="872cb-473">Título da escolha</span><span class="sxs-lookup"><span data-stu-id="872cb-473">Title of the choice</span></span>|
|`parameter.choices.value`|<span data-ttu-id="872cb-474">String</span><span class="sxs-lookup"><span data-stu-id="872cb-474">String</span></span>|<span data-ttu-id="872cb-475">512</span><span class="sxs-lookup"><span data-stu-id="872cb-475">512</span></span>||<span data-ttu-id="872cb-476">Valor da escolha</span><span class="sxs-lookup"><span data-stu-id="872cb-476">Value of the choice</span></span>|

## <a name="permissions"></a><span data-ttu-id="872cb-477">permissões</span><span class="sxs-lookup"><span data-stu-id="872cb-477">permissions</span></span>

<span data-ttu-id="872cb-478">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="872cb-478">**Optional**</span></span>

<span data-ttu-id="872cb-479">Uma matriz que especifica quais permissões o aplicativo solicita, o que permite que os usuários finais saibam `string` como a extensão será efetivada.</span><span class="sxs-lookup"><span data-stu-id="872cb-479">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="872cb-480">As seguintes opções não são exclusivas:</span><span class="sxs-lookup"><span data-stu-id="872cb-480">The following options are non-exclusive:</span></span>

* <span data-ttu-id="872cb-481">`identity`&emsp;Requer informações de identidade do usuário</span><span class="sxs-lookup"><span data-stu-id="872cb-481">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="872cb-482">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe</span><span class="sxs-lookup"><span data-stu-id="872cb-482">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="872cb-483">Alterar essas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="872cb-483">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="872cb-484">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="872cb-484">devicePermissions</span></span>

<span data-ttu-id="872cb-485">**Opcional** Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-485">**Optional** Array of Strings</span></span>

<span data-ttu-id="872cb-486">Especifica os recursos nativos no dispositivo de um usuário ao que seu aplicativo pode solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="872cb-486">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="872cb-487">As opções são:</span><span class="sxs-lookup"><span data-stu-id="872cb-487">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="872cb-488">validDomains</span><span class="sxs-lookup"><span data-stu-id="872cb-488">validDomains</span></span>

<span data-ttu-id="872cb-489">**Opcional**, exceto **Obrigatório quando** notado</span><span class="sxs-lookup"><span data-stu-id="872cb-489">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="872cb-490">Uma lista de domínios válidos dos quais o aplicativo espera carregar qualquer conteúdo.</span><span class="sxs-lookup"><span data-stu-id="872cb-490">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="872cb-491">Listagem de domínio pode incluir caracteres curinga, por exemplo `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="872cb-491">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="872cb-492">Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="872cb-492">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="872cb-493">Se a configuração de tabulação ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de tabulação, esse domínio deve ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="872cb-493">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="872cb-494">No **entanto,** não é necessário incluir os domínios de provedores de identidade que você deseja dar suporte ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-494">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="872cb-495">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para accounts.google.com, mas você não deve incluir accounts.google.com em `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="872cb-495">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="872cb-496">Não adicione domínios que estejam fora do seu controle, diretamente ou por meio de caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="872cb-496">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="872cb-497">Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="872cb-497">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="872cb-498">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="872cb-498">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="872cb-499">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="872cb-499">webApplicationInfo</span></span>

<span data-ttu-id="872cb-500">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="872cb-500">**Optional**</span></span>

<span data-ttu-id="872cb-501">Especifique suas informações do AAD App ID e do Graph para ajudar os usuários a entrar perfeitamente em seu aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="872cb-501">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="872cb-502">Nome</span><span class="sxs-lookup"><span data-stu-id="872cb-502">Name</span></span>| <span data-ttu-id="872cb-503">Tipo</span><span class="sxs-lookup"><span data-stu-id="872cb-503">Type</span></span>| <span data-ttu-id="872cb-504">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="872cb-504">Maximum size</span></span> | <span data-ttu-id="872cb-505">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="872cb-505">Required</span></span> | <span data-ttu-id="872cb-506">Descrição</span><span class="sxs-lookup"><span data-stu-id="872cb-506">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="872cb-507">String</span><span class="sxs-lookup"><span data-stu-id="872cb-507">String</span></span>|<span data-ttu-id="872cb-508">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-508">36 characters</span></span>|<span data-ttu-id="872cb-509">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-509">✔</span></span>|<span data-ttu-id="872cb-510">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-510">AAD application id of the app.</span></span> <span data-ttu-id="872cb-511">Essa id deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="872cb-511">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="872cb-512">String</span><span class="sxs-lookup"><span data-stu-id="872cb-512">String</span></span>|<span data-ttu-id="872cb-513">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="872cb-513">2048 characters</span></span>|<span data-ttu-id="872cb-514">✔</span><span class="sxs-lookup"><span data-stu-id="872cb-514">✔</span></span>|<span data-ttu-id="872cb-515">URL de recurso do aplicativo para adquirir token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="872cb-515">Resource url of app for acquiring auth token for SSO.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="872cb-516">configurableProperties</span><span class="sxs-lookup"><span data-stu-id="872cb-516">configurableProperties</span></span>

<span data-ttu-id="872cb-517">**Opcional** - matriz</span><span class="sxs-lookup"><span data-stu-id="872cb-517">**Optional** - array</span></span>

<span data-ttu-id="872cb-518">O `configurableProperties` bloco define as propriedades do aplicativo que o administrador do Teams pode personalizar.</span><span class="sxs-lookup"><span data-stu-id="872cb-518">The `configurableProperties` block defines the app properties that Teams admin can customize.</span></span> <span data-ttu-id="872cb-519">Para obter mais informações, consulte [personalizar aplicativos no Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="872cb-519">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="872cb-520">Um mínimo de uma propriedade deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="872cb-520">A minimum of one property must be defined.</span></span> <span data-ttu-id="872cb-521">Você pode definir um máximo de nove propriedades neste bloco.</span><span class="sxs-lookup"><span data-stu-id="872cb-521">You can define a maximum of nine properties in this block.</span></span>
> <span data-ttu-id="872cb-522">Como prática prática prática, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes a seguir ao personalizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-522">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span> 

<span data-ttu-id="872cb-523">Você pode definir qualquer uma das seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="872cb-523">You can define any of the following properties:</span></span>
* <span data-ttu-id="872cb-524">`name`: Permite que o administrador altere o nome de exibição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-524">`name`: Allows admin to change the app's display name.</span></span>
* <span data-ttu-id="872cb-525">`shortDescription`: Permite que o administrador altere a descrição curta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-525">`shortDescription`: Allows admin to change the app's short description.</span></span>
* <span data-ttu-id="872cb-526">`longDescription`: Permite que o administrador altere a descrição detalhada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="872cb-526">`longDescription`: Allows admin to change the app's detailed description.</span></span>
* <span data-ttu-id="872cb-527">`smallImageUrl`: É `outline` a propriedade no bloco do `icons` manifesto.</span><span class="sxs-lookup"><span data-stu-id="872cb-527">`smallImageUrl`: It is `outline` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="872cb-528">`largeImageUrl`: É a `color` propriedade no bloco do `icons` manifesto.</span><span class="sxs-lookup"><span data-stu-id="872cb-528">`largeImageUrl`: It is the `color` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="872cb-529">`accentColor`: É a cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="872cb-529">`accentColor`: It is the color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="872cb-530">`developerUrl`: É a URL https:// para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="872cb-530">`developerUrl`: It is the https:// URL to the developer's website.</span></span>
* <span data-ttu-id="872cb-531">`privacyUrl`: É a URL https:// da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="872cb-531">`privacyUrl`: It is the https:// URL to the developer's privacy policy.</span></span>
* <span data-ttu-id="872cb-532">`termsOfUseUrl`: É a URL https:// para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="872cb-532">`termsOfUseUrl`: It is the https:// URL to the developer's terms of use.</span></span>


