---
title: Referência de esquema do manifesto da visualização do desenvolvedor
description: Descreve o esquema suportado pelo manifesto para o Microsoft Teams
keywords: Visualização do desenvolvedor do esquema de manifesto do teams
ms.date: 05/20/2019
ms.openlocfilehash: b99e1ae99b7fd1edd4c695f43f3ac25270f0c710
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672475"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="92a23-104">Esquema de manifesto da visualização do desenvolvedor para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="92a23-104">Developer preview manifest schema for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="92a23-105">Consulte [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) para obter informações sobre o programa e como você pode participar.</span><span class="sxs-lookup"><span data-stu-id="92a23-105">See [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for information on the program and how you can join.</span></span>
> <span data-ttu-id="92a23-106">Se você não estiver usando a visualização do desenvolvedor, não deverá usar esta versão do manifesto.</span><span class="sxs-lookup"><span data-stu-id="92a23-106">If you are not using the developer preview you should not be using this version of the manifest.</span></span> <span data-ttu-id="92a23-107">Consulte [referência: esquema de manifesto para o Microsoft Teams](~/resources/schema/manifest-schema.md) para a versão pública do manifesto.</span><span class="sxs-lookup"><span data-stu-id="92a23-107">See [Reference: Manifest schema for Microsoft Teams](~/resources/schema/manifest-schema.md) for the public version of the manifest.</span></span>

<span data-ttu-id="92a23-108">O manifesto do Microsoft Teams descreve como o aplicativo integra-se ao produto Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="92a23-108">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="92a23-109">Seu manifesto deve estar em conformidade com o esquema [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json)hospedado em.</span><span class="sxs-lookup"><span data-stu-id="92a23-109">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="92a23-110">Para obter mais informações sobre os recursos disponíveis, consulte: [recursos no Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span><span class="sxs-lookup"><span data-stu-id="92a23-110">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="92a23-111">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="92a23-111">Sample full manifest</span></span>

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
  ]
}
```

<span data-ttu-id="92a23-112">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="92a23-112">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="92a23-113">$schema</span><span class="sxs-lookup"><span data-stu-id="92a23-113">$schema</span></span>

<span data-ttu-id="92a23-114">*Opcional, mas* &ndash; a cadeia de caracteres recomendada</span><span class="sxs-lookup"><span data-stu-id="92a23-114">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="92a23-115">A URL https://que faz referência ao esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="92a23-115">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="92a23-116">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="92a23-116">manifestVersion</span></span>

<span data-ttu-id="92a23-117">Cadeia de caracteres **obrigatória** &ndash;</span><span class="sxs-lookup"><span data-stu-id="92a23-117">**Required** &ndash; String</span></span>

<span data-ttu-id="92a23-118">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="92a23-118">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="92a23-119">Deve ser "devPreview".</span><span class="sxs-lookup"><span data-stu-id="92a23-119">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="92a23-120">versão</span><span class="sxs-lookup"><span data-stu-id="92a23-120">version</span></span>

<span data-ttu-id="92a23-121">Cadeia de caracteres **obrigatória** &ndash;</span><span class="sxs-lookup"><span data-stu-id="92a23-121">**Required** &ndash; String</span></span>

<span data-ttu-id="92a23-122">A versão do aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="92a23-122">The version of the specific app.</span></span> <span data-ttu-id="92a23-123">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="92a23-123">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="92a23-124">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="92a23-124">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="92a23-125">Se este aplicativo foi enviado para o repositório, o novo manifesto terá que ser reenviado e validado novamente.</span><span class="sxs-lookup"><span data-stu-id="92a23-125">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="92a23-126">Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, após serem aprovados.</span><span class="sxs-lookup"><span data-stu-id="92a23-126">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="92a23-127">Se as permissões solicitadas pelo aplicativo forem alteradas, os usuários serão solicitados a atualizar e a dar o consentimento novamente para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-127">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="92a23-128">Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (principal. Mínima. PATCH).</span><span class="sxs-lookup"><span data-stu-id="92a23-128">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="92a23-129">id</span><span class="sxs-lookup"><span data-stu-id="92a23-129">id</span></span>

<span data-ttu-id="92a23-130">ID de aplicativo da Microsoft **necessária** &ndash;</span><span class="sxs-lookup"><span data-stu-id="92a23-130">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="92a23-131">O identificador exclusivo gerado pela Microsoft para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-131">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="92a23-132">Se você tiver registrado um bot por meio da Microsoft bot Framework, ou se o aplicativo Web da sua guia já estiver conectado com a Microsoft, você já deve ter um ID e deve inseri-lo aqui.</span><span class="sxs-lookup"><span data-stu-id="92a23-132">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="92a23-133">Caso contrário, você deve gerar uma nova ID no portal de registro de aplicativos da Microsoft ([meus aplicativos](https://apps.dev.microsoft.com)), inseri-la aqui e reutilizá-la quando você [Adicionar um bot](~/bots/how-to/create-a-bot-for-teams.md).</span><span class="sxs-lookup"><span data-stu-id="92a23-133">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="92a23-134">Packagenamena</span><span class="sxs-lookup"><span data-stu-id="92a23-134">packageName</span></span>

<span data-ttu-id="92a23-135">Cadeia de caracteres **obrigatória** &ndash;</span><span class="sxs-lookup"><span data-stu-id="92a23-135">**Required** &ndash; String</span></span>

<span data-ttu-id="92a23-136">Um identificador exclusivo para esse aplicativo na notação de domínio reverso; por exemplo, com. example. MyApp.</span><span class="sxs-lookup"><span data-stu-id="92a23-136">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="92a23-137">developer</span><span class="sxs-lookup"><span data-stu-id="92a23-137">developer</span></span>

<span data-ttu-id="92a23-138">**Required**</span><span class="sxs-lookup"><span data-stu-id="92a23-138">**Required**</span></span>

<span data-ttu-id="92a23-139">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="92a23-139">Specifies information about your company.</span></span> <span data-ttu-id="92a23-140">Para aplicativos enviados para o AppSource (anteriormente Office Store), esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="92a23-140">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="92a23-141">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-141">Name</span></span>| <span data-ttu-id="92a23-142">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-142">Maximum size</span></span> | <span data-ttu-id="92a23-143">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-143">Required</span></span> | <span data-ttu-id="92a23-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="92a23-145">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-145">32 characters</span></span>|<span data-ttu-id="92a23-146">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-146">✔</span></span>|<span data-ttu-id="92a23-147">O nome de exibição para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="92a23-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="92a23-148">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-148">2048 characters</span></span>|<span data-ttu-id="92a23-149">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-149">✔</span></span>|<span data-ttu-id="92a23-150">A URL do https://para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="92a23-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="92a23-151">Este link deve levar os usuários à sua página de aterrissagem específica da empresa ou do produto.</span><span class="sxs-lookup"><span data-stu-id="92a23-151">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="92a23-152">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-152">2048 characters</span></span>|<span data-ttu-id="92a23-153">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-153">✔</span></span>|<span data-ttu-id="92a23-154">A URL do https://para a política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="92a23-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="92a23-155">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-155">2048 characters</span></span>|<span data-ttu-id="92a23-156">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-156">✔</span></span>|<span data-ttu-id="92a23-157">A URL do https://para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="92a23-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="92a23-158">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-158">10 characters</span></span>|<span data-ttu-id="92a23-159">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-159">✔</span></span>|<span data-ttu-id="92a23-160">**Opcional** A ID de rede do parceiro da Microsoft que identifica a organização do parceiro que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-160">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="92a23-161">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="92a23-161">localizationInfo</span></span>

<span data-ttu-id="92a23-162">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="92a23-162">**Optional**</span></span>

<span data-ttu-id="92a23-163">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="92a23-163">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="92a23-164">Confira [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="92a23-164">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="92a23-165">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-165">Name</span></span>| <span data-ttu-id="92a23-166">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-166">Maximum size</span></span> | <span data-ttu-id="92a23-167">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-167">Required</span></span> | <span data-ttu-id="92a23-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-168">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="92a23-169">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-169">4 characters</span></span>|<span data-ttu-id="92a23-170">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-170">✔</span></span>|<span data-ttu-id="92a23-171">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="92a23-171">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="92a23-172">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="92a23-172">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="92a23-173">Uma matriz de objetos especificando traduções de idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="92a23-173">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="92a23-174">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-174">Name</span></span>| <span data-ttu-id="92a23-175">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-175">Maximum size</span></span> | <span data-ttu-id="92a23-176">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-176">Required</span></span> | <span data-ttu-id="92a23-177">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-177">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="92a23-178">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-178">4 characters</span></span>|<span data-ttu-id="92a23-179">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-179">✔</span></span>|<span data-ttu-id="92a23-180">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="92a23-180">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="92a23-181">4 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-181">4 characters</span></span>|<span data-ttu-id="92a23-182">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-182">✔</span></span>|<span data-ttu-id="92a23-183">Um caminho de arquivo relativo para um arquivo. JSON que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="92a23-183">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="92a23-184">nome</span><span class="sxs-lookup"><span data-stu-id="92a23-184">name</span></span>

<span data-ttu-id="92a23-185">**Required**</span><span class="sxs-lookup"><span data-stu-id="92a23-185">**Required**</span></span>

<span data-ttu-id="92a23-186">O nome da sua experiência de aplicativo, exibido aos usuários na experiência do teams.</span><span class="sxs-lookup"><span data-stu-id="92a23-186">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="92a23-187">Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="92a23-187">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="92a23-188">Os valores de `short` e `full` não devem ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="92a23-188">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="92a23-189">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-189">Name</span></span>| <span data-ttu-id="92a23-190">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-190">Maximum size</span></span> | <span data-ttu-id="92a23-191">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-191">Required</span></span> | <span data-ttu-id="92a23-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-192">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="92a23-193">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-193">30 characters</span></span>|<span data-ttu-id="92a23-194">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-194">✔</span></span>|<span data-ttu-id="92a23-195">O nome de exibição curto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-195">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="92a23-196">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-196">100 characters</span></span>||<span data-ttu-id="92a23-197">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="92a23-197">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="92a23-198">description</span><span class="sxs-lookup"><span data-stu-id="92a23-198">description</span></span>

<span data-ttu-id="92a23-199">**Required**</span><span class="sxs-lookup"><span data-stu-id="92a23-199">**Required**</span></span>

<span data-ttu-id="92a23-200">Descreve seu aplicativo para os usuários.</span><span class="sxs-lookup"><span data-stu-id="92a23-200">Describes your app to users.</span></span> <span data-ttu-id="92a23-201">Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="92a23-201">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="92a23-202">Certifique-se de que sua descrição descreve precisamente sua experiência e fornece informações para ajudar os clientes potenciais a entender o que a sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="92a23-202">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="92a23-203">Você também deve observar, na descrição completa, se for necessário usar uma conta externa.</span><span class="sxs-lookup"><span data-stu-id="92a23-203">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="92a23-204">Os valores de `short` e `full` não devem ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="92a23-204">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="92a23-205">Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir nenhum outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-205">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="92a23-206">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-206">Name</span></span>| <span data-ttu-id="92a23-207">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-207">Maximum size</span></span> | <span data-ttu-id="92a23-208">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-208">Required</span></span> | <span data-ttu-id="92a23-209">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-209">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="92a23-210">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-210">80 characters</span></span>|<span data-ttu-id="92a23-211">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-211">✔</span></span>|<span data-ttu-id="92a23-212">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="92a23-212">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="92a23-213">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-213">4000 characters</span></span>|<span data-ttu-id="92a23-214">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-214">✔</span></span>|<span data-ttu-id="92a23-215">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-215">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="92a23-216">ícones</span><span class="sxs-lookup"><span data-stu-id="92a23-216">icons</span></span>

<span data-ttu-id="92a23-217">**Required**</span><span class="sxs-lookup"><span data-stu-id="92a23-217">**Required**</span></span>

<span data-ttu-id="92a23-218">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="92a23-218">Icons used within the Teams app.</span></span> <span data-ttu-id="92a23-219">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="92a23-219">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="92a23-220">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-220">Name</span></span>| <span data-ttu-id="92a23-221">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-221">Maximum size</span></span> | <span data-ttu-id="92a23-222">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-222">Required</span></span> | <span data-ttu-id="92a23-223">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="92a23-224">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-224">2048 characters</span></span>|<span data-ttu-id="92a23-225">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-225">✔</span></span>|<span data-ttu-id="92a23-226">Um caminho de arquivo relativo para um ícone de estrutura de tópicos de PNG de 32 x 32 transparente.</span><span class="sxs-lookup"><span data-stu-id="92a23-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="92a23-227">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-227">2048 characters</span></span>|<span data-ttu-id="92a23-228">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-228">✔</span></span>|<span data-ttu-id="92a23-229">Um caminho de arquivo relativo para um ícone de 192x192 do PNG completo.</span><span class="sxs-lookup"><span data-stu-id="92a23-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="92a23-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="92a23-230">accentColor</span></span>

<span data-ttu-id="92a23-231">Cadeia de caracteres **obrigatória** &ndash;</span><span class="sxs-lookup"><span data-stu-id="92a23-231">**Required** &ndash; String</span></span>

<span data-ttu-id="92a23-232">Uma cor a ser usada em conjunto com e como um plano de fundo para seus ícones de estrutura de tópicos.</span><span class="sxs-lookup"><span data-stu-id="92a23-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="92a23-233">O valor deve ser um código de cor HTML válido começando com ' # ', por `#4464ee`exemplo.</span><span class="sxs-lookup"><span data-stu-id="92a23-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="92a23-234">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="92a23-234">configurableTabs</span></span>

<span data-ttu-id="92a23-235">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="92a23-235">**Optional**</span></span>

<span data-ttu-id="92a23-236">Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração adicional antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="92a23-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="92a23-237">Guias configuráveis têm suporte apenas no escopo Teams, e atualmente só há suporte para uma guia por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-237">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="92a23-238">O objeto é uma matriz com todos os elementos do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="92a23-238">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="92a23-239">Esse bloco só é necessário para soluções que oferecem uma solução de guia de canal configurável.</span><span class="sxs-lookup"><span data-stu-id="92a23-239">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="92a23-240">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-240">Name</span></span>| <span data-ttu-id="92a23-241">Tipo</span><span class="sxs-lookup"><span data-stu-id="92a23-241">Type</span></span>| <span data-ttu-id="92a23-242">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-242">Maximum size</span></span> | <span data-ttu-id="92a23-243">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-243">Required</span></span> | <span data-ttu-id="92a23-244">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="92a23-245">String</span><span class="sxs-lookup"><span data-stu-id="92a23-245">String</span></span>|<span data-ttu-id="92a23-246">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-246">2048 characters</span></span>|<span data-ttu-id="92a23-247">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-247">✔</span></span>|<span data-ttu-id="92a23-248">A URL do https://a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="92a23-248">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="92a23-249">Boolean</span><span class="sxs-lookup"><span data-stu-id="92a23-249">Boolean</span></span>|||<span data-ttu-id="92a23-250">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="92a23-250">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="92a23-251">Será`true`</span><span class="sxs-lookup"><span data-stu-id="92a23-251">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="92a23-252">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="92a23-252">Array of enum</span></span>|<span data-ttu-id="92a23-253">1 </span><span class="sxs-lookup"><span data-stu-id="92a23-253">1</span></span>|<span data-ttu-id="92a23-254">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-254">✔</span></span>|<span data-ttu-id="92a23-255">No momento, as guias configuráveis `team` só `groupchat` dão suporte a e os escopos.</span><span class="sxs-lookup"><span data-stu-id="92a23-255">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="92a23-256">String</span><span class="sxs-lookup"><span data-stu-id="92a23-256">String</span></span>|<span data-ttu-id="92a23-257">2048</span><span class="sxs-lookup"><span data-stu-id="92a23-257">2048</span></span>||<span data-ttu-id="92a23-258">Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="92a23-258">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="92a23-259">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="92a23-259">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="92a23-260">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="92a23-260">Array of enum</span></span>|<span data-ttu-id="92a23-261">1 </span><span class="sxs-lookup"><span data-stu-id="92a23-261">1</span></span>||<span data-ttu-id="92a23-262">Define como sua guia será disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="92a23-262">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="92a23-263">Opções são `sharePointFullPage` e`sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="92a23-263">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="92a23-264">staticTabs</span><span class="sxs-lookup"><span data-stu-id="92a23-264">staticTabs</span></span>

<span data-ttu-id="92a23-265">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="92a23-265">**Optional**</span></span>

<span data-ttu-id="92a23-266">Define um conjunto de guias que podem ser "fixadas" por padrão, sem o usuário adicioná-las manualmente.</span><span class="sxs-lookup"><span data-stu-id="92a23-266">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="92a23-267">As guias estáticas `personal` declaradas no escopo são sempre fixadas para a experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-267">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="92a23-268">Guias static declaradas `team` no escopo não são suportadas atualmente.</span><span class="sxs-lookup"><span data-stu-id="92a23-268">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="92a23-269">O objeto é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="92a23-269">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="92a23-270">Esse bloco é necessário somente para soluções que oferecem uma solução de guia estática.</span><span class="sxs-lookup"><span data-stu-id="92a23-270">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="92a23-271">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-271">Name</span></span>| <span data-ttu-id="92a23-272">Tipo</span><span class="sxs-lookup"><span data-stu-id="92a23-272">Type</span></span>| <span data-ttu-id="92a23-273">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-273">Maximum size</span></span> | <span data-ttu-id="92a23-274">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-274">Required</span></span> | <span data-ttu-id="92a23-275">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-275">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="92a23-276">String</span><span class="sxs-lookup"><span data-stu-id="92a23-276">String</span></span>|<span data-ttu-id="92a23-277">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-277">64 characters</span></span>|<span data-ttu-id="92a23-278">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-278">✔</span></span>|<span data-ttu-id="92a23-279">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="92a23-279">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="92a23-280">String</span><span class="sxs-lookup"><span data-stu-id="92a23-280">String</span></span>|<span data-ttu-id="92a23-281">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-281">128 characters</span></span>|<span data-ttu-id="92a23-282">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-282">✔</span></span>|<span data-ttu-id="92a23-283">O nome de exibição da guia na interface de canal.</span><span class="sxs-lookup"><span data-stu-id="92a23-283">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="92a23-284">String</span><span class="sxs-lookup"><span data-stu-id="92a23-284">String</span></span>|<span data-ttu-id="92a23-285">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-285">2048 characters</span></span>|<span data-ttu-id="92a23-286">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-286">✔</span></span>|<span data-ttu-id="92a23-287">A URL https://que aponta para a interface do usuário da entidade a ser exibida na tela do teams.</span><span class="sxs-lookup"><span data-stu-id="92a23-287">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="92a23-288">String</span><span class="sxs-lookup"><span data-stu-id="92a23-288">String</span></span>|<span data-ttu-id="92a23-289">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-289">2048 characters</span></span>||<span data-ttu-id="92a23-290">A URL do https://para apontar para o modo de exibição de um usuário em um navegador.</span><span class="sxs-lookup"><span data-stu-id="92a23-290">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="92a23-291">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="92a23-291">Array of enum</span></span>|<span data-ttu-id="92a23-292">1 </span><span class="sxs-lookup"><span data-stu-id="92a23-292">1</span></span>|<span data-ttu-id="92a23-293">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-293">✔</span></span>|<span data-ttu-id="92a23-294">Atualmente, as guias estáticas oferecem `personal` suporte somente ao escopo, o que significa que ela pode ser provisionada somente como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="92a23-294">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="92a23-295">robôs</span><span class="sxs-lookup"><span data-stu-id="92a23-295">bots</span></span>

<span data-ttu-id="92a23-296">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="92a23-296">**Optional**</span></span>

<span data-ttu-id="92a23-297">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="92a23-297">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="92a23-298">O objeto é uma matriz (máximo de apenas 1 elemento&mdash;atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="92a23-298">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="92a23-299">Esse bloco é necessário somente para soluções que oferecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="92a23-299">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="92a23-300">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-300">Name</span></span>| <span data-ttu-id="92a23-301">Tipo</span><span class="sxs-lookup"><span data-stu-id="92a23-301">Type</span></span>| <span data-ttu-id="92a23-302">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-302">Maximum size</span></span> | <span data-ttu-id="92a23-303">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-303">Required</span></span> | <span data-ttu-id="92a23-304">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-304">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="92a23-305">String</span><span class="sxs-lookup"><span data-stu-id="92a23-305">String</span></span>|<span data-ttu-id="92a23-306">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-306">64 characters</span></span>|<span data-ttu-id="92a23-307">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-307">✔</span></span>|<span data-ttu-id="92a23-308">A ID exclusiva do aplicativo da Microsoft para o bot, conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="92a23-308">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="92a23-309">Isso pode ser o mesmo que a ID de [aplicativo](#id)geral.</span><span class="sxs-lookup"><span data-stu-id="92a23-309">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="92a23-310">Boolean</span><span class="sxs-lookup"><span data-stu-id="92a23-310">Boolean</span></span>|||<span data-ttu-id="92a23-311">Descreve se o bot utiliza ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="92a23-311">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="92a23-312">Será`false`</span><span class="sxs-lookup"><span data-stu-id="92a23-312">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="92a23-313">Boolean</span><span class="sxs-lookup"><span data-stu-id="92a23-313">Boolean</span></span>|||<span data-ttu-id="92a23-314">Indica se um bot é um bot unidirecional somente de notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="92a23-314">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="92a23-315">Será`false`</span><span class="sxs-lookup"><span data-stu-id="92a23-315">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="92a23-316">Boolean</span><span class="sxs-lookup"><span data-stu-id="92a23-316">Boolean</span></span>|||<span data-ttu-id="92a23-317">Indica se o bot dá suporte à capacidade de carregar/baixar arquivos no chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="92a23-317">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="92a23-318">Será`false`</span><span class="sxs-lookup"><span data-stu-id="92a23-318">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="92a23-319">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="92a23-319">Array of enum</span></span>|<span data-ttu-id="92a23-320">3 </span><span class="sxs-lookup"><span data-stu-id="92a23-320">3</span></span>|<span data-ttu-id="92a23-321">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-321">✔</span></span>|<span data-ttu-id="92a23-322">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência com escopo para um usuário individual sozinho (`personal`).</span><span class="sxs-lookup"><span data-stu-id="92a23-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="92a23-323">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="92a23-323">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="92a23-324">bots. commandLists</span><span class="sxs-lookup"><span data-stu-id="92a23-324">bots.commandLists</span></span>

<span data-ttu-id="92a23-325">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="92a23-325">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="92a23-326">O objeto é uma matriz (máximo de dois elementos) com todos os elementos do `object`tipo; Você deve definir uma lista de comandos separada para cada escopo que seu bot suporta.</span><span class="sxs-lookup"><span data-stu-id="92a23-326">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="92a23-327">Consulte [menus de bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="92a23-327">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="92a23-328">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-328">Name</span></span>| <span data-ttu-id="92a23-329">Tipo</span><span class="sxs-lookup"><span data-stu-id="92a23-329">Type</span></span>| <span data-ttu-id="92a23-330">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-330">Maximum size</span></span> | <span data-ttu-id="92a23-331">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-331">Required</span></span> | <span data-ttu-id="92a23-332">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-332">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="92a23-333">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="92a23-333">array of enum</span></span>|<span data-ttu-id="92a23-334">3 </span><span class="sxs-lookup"><span data-stu-id="92a23-334">3</span></span>|<span data-ttu-id="92a23-335">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-335">✔</span></span>|<span data-ttu-id="92a23-336">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="92a23-336">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="92a23-337">As opções `team`são `personal`, e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="92a23-337">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="92a23-338">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="92a23-338">array of objects</span></span>|<span data-ttu-id="92a23-339">10 </span><span class="sxs-lookup"><span data-stu-id="92a23-339">10</span></span>|<span data-ttu-id="92a23-340">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-340">✔</span></span>|<span data-ttu-id="92a23-341">Uma matriz de comandos para a qual o bot oferece suporte:</span><span class="sxs-lookup"><span data-stu-id="92a23-341">An array of commands the bot supports:</span></span><br><span data-ttu-id="92a23-342">`title`: o nome do comando do bot (cadeia de caracteres, 32)</span><span class="sxs-lookup"><span data-stu-id="92a23-342">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="92a23-343">`description`: uma simples descrição ou exemplo da sintaxe do comando e seu argumento (String, 128)</span><span class="sxs-lookup"><span data-stu-id="92a23-343">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

## <a name="connectors"></a><span data-ttu-id="92a23-344">conectores</span><span class="sxs-lookup"><span data-stu-id="92a23-344">connectors</span></span>

<span data-ttu-id="92a23-345">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="92a23-345">**Optional**</span></span>

<span data-ttu-id="92a23-346">O `connectors` bloco define um conector do Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-346">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="92a23-347">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do `object`tipo.</span><span class="sxs-lookup"><span data-stu-id="92a23-347">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="92a23-348">Esse bloco é necessário somente para soluções que fornecem um conector.</span><span class="sxs-lookup"><span data-stu-id="92a23-348">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="92a23-349">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-349">Name</span></span>| <span data-ttu-id="92a23-350">Tipo</span><span class="sxs-lookup"><span data-stu-id="92a23-350">Type</span></span>| <span data-ttu-id="92a23-351">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-351">Maximum size</span></span> | <span data-ttu-id="92a23-352">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-352">Required</span></span> | <span data-ttu-id="92a23-353">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-353">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="92a23-354">String</span><span class="sxs-lookup"><span data-stu-id="92a23-354">String</span></span>|<span data-ttu-id="92a23-355">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-355">2048 characters</span></span>|<span data-ttu-id="92a23-356">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-356">✔</span></span>|<span data-ttu-id="92a23-357">A URL do https://a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="92a23-357">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="92a23-358">String</span><span class="sxs-lookup"><span data-stu-id="92a23-358">String</span></span>|<span data-ttu-id="92a23-359">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-359">64 characters</span></span>|<span data-ttu-id="92a23-360">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-360">✔</span></span>|<span data-ttu-id="92a23-361">Um identificador exclusivo para o conector que corresponde à sua ID no [painel do desenvolvedor de conectores](https://aka.ms/connectorsdashboard).</span><span class="sxs-lookup"><span data-stu-id="92a23-361">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="92a23-362">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="92a23-362">Array of enum</span></span>|<span data-ttu-id="92a23-363">1 </span><span class="sxs-lookup"><span data-stu-id="92a23-363">1</span></span>|<span data-ttu-id="92a23-364">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-364">✔</span></span>|<span data-ttu-id="92a23-365">Especifica se o conector oferece uma experiência no contexto de um canal em uma `team`ou uma experiência com escopo para um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="92a23-365">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="92a23-366">Atualmente, só há `team` suporte para o escopo.</span><span class="sxs-lookup"><span data-stu-id="92a23-366">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="92a23-367">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="92a23-367">composeExtensions</span></span>

<span data-ttu-id="92a23-368">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="92a23-368">**Optional**</span></span>

<span data-ttu-id="92a23-369">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-369">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="92a23-370">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem a funcionar.</span><span class="sxs-lookup"><span data-stu-id="92a23-370">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="92a23-371">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do `object`tipo.</span><span class="sxs-lookup"><span data-stu-id="92a23-371">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="92a23-372">Esse bloco é necessário somente para soluções que forneçam uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="92a23-372">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="92a23-373">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-373">Name</span></span>| <span data-ttu-id="92a23-374">Tipo</span><span class="sxs-lookup"><span data-stu-id="92a23-374">Type</span></span> | <span data-ttu-id="92a23-375">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-375">Maximum Size</span></span> | <span data-ttu-id="92a23-376">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-376">Required</span></span> | <span data-ttu-id="92a23-377">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-377">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="92a23-378">String</span><span class="sxs-lookup"><span data-stu-id="92a23-378">String</span></span>|<span data-ttu-id="92a23-379">64</span><span class="sxs-lookup"><span data-stu-id="92a23-379">64</span></span>|<span data-ttu-id="92a23-380">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-380">✔</span></span>|<span data-ttu-id="92a23-381">A ID exclusiva do aplicativo da Microsoft para o bot que faz a extensão do sistema de mensagens, conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="92a23-381">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="92a23-382">Isso pode ser o mesmo que a ID de [aplicativo](#id)geral.</span><span class="sxs-lookup"><span data-stu-id="92a23-382">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="92a23-383">Boolean</span><span class="sxs-lookup"><span data-stu-id="92a23-383">Boolean</span></span>|||<span data-ttu-id="92a23-384">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="92a23-384">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="92a23-385">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="92a23-385">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="92a23-386">Matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="92a23-386">Array of object</span></span>|<span data-ttu-id="92a23-387">10 </span><span class="sxs-lookup"><span data-stu-id="92a23-387">10</span></span>|<span data-ttu-id="92a23-388">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-388">✔</span></span>|<span data-ttu-id="92a23-389">Matriz de comandos que a extensão de mensagens oferece suporte</span><span class="sxs-lookup"><span data-stu-id="92a23-389">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="92a23-390">composeExtensions. Commands</span><span class="sxs-lookup"><span data-stu-id="92a23-390">composeExtensions.commands</span></span>

<span data-ttu-id="92a23-391">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="92a23-391">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="92a23-392">Cada comando aparece no Microsoft Teams como uma possível interação do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="92a23-392">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="92a23-393">Há um máximo de 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="92a23-393">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="92a23-394">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="92a23-394">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="92a23-395">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-395">Name</span></span>| <span data-ttu-id="92a23-396">Tipo</span><span class="sxs-lookup"><span data-stu-id="92a23-396">Type</span></span>| <span data-ttu-id="92a23-397">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-397">Maximum size</span></span> | <span data-ttu-id="92a23-398">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-398">Required</span></span> | <span data-ttu-id="92a23-399">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-399">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="92a23-400">String</span><span class="sxs-lookup"><span data-stu-id="92a23-400">String</span></span>|<span data-ttu-id="92a23-401">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-401">64 characters</span></span>|<span data-ttu-id="92a23-402">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-402">✔</span></span>|<span data-ttu-id="92a23-403">A ID do comando</span><span class="sxs-lookup"><span data-stu-id="92a23-403">The ID for the command</span></span>|
|`type`|<span data-ttu-id="92a23-404">String</span><span class="sxs-lookup"><span data-stu-id="92a23-404">String</span></span>|<span data-ttu-id="92a23-405">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-405">64 characters</span></span>||<span data-ttu-id="92a23-406">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="92a23-406">Type of the command.</span></span> <span data-ttu-id="92a23-407">Um `query` ou `action`.</span><span class="sxs-lookup"><span data-stu-id="92a23-407">One of `query` or `action`.</span></span> <span data-ttu-id="92a23-408">Será`query`</span><span class="sxs-lookup"><span data-stu-id="92a23-408">Default: `query`</span></span>|
|`title`|<span data-ttu-id="92a23-409">String</span><span class="sxs-lookup"><span data-stu-id="92a23-409">String</span></span>|<span data-ttu-id="92a23-410">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-410">32 characters</span></span>|<span data-ttu-id="92a23-411">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-411">✔</span></span>|<span data-ttu-id="92a23-412">O nome do comando amigável</span><span class="sxs-lookup"><span data-stu-id="92a23-412">The user-friendly command name</span></span>|
|`description`|<span data-ttu-id="92a23-413">String</span><span class="sxs-lookup"><span data-stu-id="92a23-413">String</span></span>|<span data-ttu-id="92a23-414">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-414">128 characters</span></span>||<span data-ttu-id="92a23-415">A descrição que aparece para os usuários para indicar a finalidade desse comando</span><span class="sxs-lookup"><span data-stu-id="92a23-415">The description that appears to users to indicate the purpose of this command</span></span>|
|`initialRun`|<span data-ttu-id="92a23-416">Boolean</span><span class="sxs-lookup"><span data-stu-id="92a23-416">Boolean</span></span>|||<span data-ttu-id="92a23-417">Um valor Boolean que indica se o comando deve ser executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="92a23-417">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="92a23-418">Será`false`</span><span class="sxs-lookup"><span data-stu-id="92a23-418">Default: `false`</span></span>|
|`context`|<span data-ttu-id="92a23-419">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-419">Array of Strings</span></span>|<span data-ttu-id="92a23-420">3 </span><span class="sxs-lookup"><span data-stu-id="92a23-420">3</span></span>||<span data-ttu-id="92a23-421">Define onde a extensão de mensagem pode ser chamada.</span><span class="sxs-lookup"><span data-stu-id="92a23-421">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="92a23-422">Qualquer combinação de `compose`, `commandBox`, `message`.</span><span class="sxs-lookup"><span data-stu-id="92a23-422">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="92a23-423">O padrão é`["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="92a23-423">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="92a23-424">Boolean</span><span class="sxs-lookup"><span data-stu-id="92a23-424">Boolean</span></span>|||<span data-ttu-id="92a23-425">Um valor Boolean que indica se deve buscar o módulo de tarefa dinamicamente</span><span class="sxs-lookup"><span data-stu-id="92a23-425">A boolean value that indicates if it should fetch the task module dynamically</span></span>|
|`taskInfo`|<span data-ttu-id="92a23-426">Objeto</span><span class="sxs-lookup"><span data-stu-id="92a23-426">Object</span></span>|||<span data-ttu-id="92a23-427">Especificar o módulo de tarefa a ser pré-carregar ao usar um comando de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="92a23-427">Specify the task module to preload when using a messaging extension command</span></span>|
|`taskInfo.title`|<span data-ttu-id="92a23-428">String</span><span class="sxs-lookup"><span data-stu-id="92a23-428">String</span></span>|<span data-ttu-id="92a23-429">64</span><span class="sxs-lookup"><span data-stu-id="92a23-429">64</span></span>||<span data-ttu-id="92a23-430">Título inicial da caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="92a23-430">Initial dialog title</span></span>|
|`taskInfo.width`|<span data-ttu-id="92a23-431">String</span><span class="sxs-lookup"><span data-stu-id="92a23-431">String</span></span>|||<span data-ttu-id="92a23-432">Largura da caixa de diálogo: um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '</span><span class="sxs-lookup"><span data-stu-id="92a23-432">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.height`|<span data-ttu-id="92a23-433">String</span><span class="sxs-lookup"><span data-stu-id="92a23-433">String</span></span>|||<span data-ttu-id="92a23-434">Altura da caixa de diálogo-um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '</span><span class="sxs-lookup"><span data-stu-id="92a23-434">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.url`|<span data-ttu-id="92a23-435">String</span><span class="sxs-lookup"><span data-stu-id="92a23-435">String</span></span>|||<span data-ttu-id="92a23-436">URL do WebView inicial</span><span class="sxs-lookup"><span data-stu-id="92a23-436">Initial webview URL</span></span>|
|`messageHandlers`|<span data-ttu-id="92a23-437">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="92a23-437">Array of Objects</span></span>|<span data-ttu-id="92a23-438">5 </span><span class="sxs-lookup"><span data-stu-id="92a23-438">5</span></span>||<span data-ttu-id="92a23-439">Uma lista de manipuladores que permitem que os aplicativos sejam chamados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="92a23-439">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="92a23-440">Os domínios também devem ser listados no`validDomains`</span><span class="sxs-lookup"><span data-stu-id="92a23-440">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="92a23-441">String</span><span class="sxs-lookup"><span data-stu-id="92a23-441">String</span></span>|||<span data-ttu-id="92a23-442">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="92a23-442">The type of message handler.</span></span> <span data-ttu-id="92a23-443">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="92a23-443">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="92a23-444">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-444">Array of Strings</span></span>|||<span data-ttu-id="92a23-445">Matriz de domínios para o qual o manipulador de mensagens de link pode se registrar.</span><span class="sxs-lookup"><span data-stu-id="92a23-445">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="92a23-446">Matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="92a23-446">Array of object</span></span>|<span data-ttu-id="92a23-447">5 </span><span class="sxs-lookup"><span data-stu-id="92a23-447">5</span></span>|<span data-ttu-id="92a23-448">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-448">✔</span></span>|<span data-ttu-id="92a23-449">A lista de parâmetros que o comando utiliza.</span><span class="sxs-lookup"><span data-stu-id="92a23-449">The list of parameters the command takes.</span></span> <span data-ttu-id="92a23-450">Mínimo: 1; máximo: 5</span><span class="sxs-lookup"><span data-stu-id="92a23-450">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="92a23-451">String</span><span class="sxs-lookup"><span data-stu-id="92a23-451">String</span></span>|<span data-ttu-id="92a23-452">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-452">64 characters</span></span>|<span data-ttu-id="92a23-453">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-453">✔</span></span>|<span data-ttu-id="92a23-454">O nome do parâmetro conforme ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="92a23-454">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="92a23-455">Isso é incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="92a23-455">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="92a23-456">String</span><span class="sxs-lookup"><span data-stu-id="92a23-456">String</span></span>|<span data-ttu-id="92a23-457">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-457">32 characters</span></span>|<span data-ttu-id="92a23-458">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-458">✔</span></span>|<span data-ttu-id="92a23-459">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="92a23-459">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="92a23-460">String</span><span class="sxs-lookup"><span data-stu-id="92a23-460">String</span></span>|<span data-ttu-id="92a23-461">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-461">128 characters</span></span>||<span data-ttu-id="92a23-462">Cadeia de caracteres amigável que descreve a finalidade deste parâmetro.</span><span class="sxs-lookup"><span data-stu-id="92a23-462">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="92a23-463">String</span><span class="sxs-lookup"><span data-stu-id="92a23-463">String</span></span>|<span data-ttu-id="92a23-464">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-464">128 characters</span></span>||<span data-ttu-id="92a23-465">Define o tipo de controle exibido em um módulo de tarefas `fetchTask: true`para o.</span><span class="sxs-lookup"><span data-stu-id="92a23-465">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="92a23-466">Um de `text`, `textarea`, `number`, `date`, `time`, `toggle`,`choiceset`</span><span class="sxs-lookup"><span data-stu-id="92a23-466">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`</span></span>|
|`parameter.choices`|<span data-ttu-id="92a23-467">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="92a23-467">Array of Objects</span></span>|<span data-ttu-id="92a23-468">10 </span><span class="sxs-lookup"><span data-stu-id="92a23-468">10</span></span>||<span data-ttu-id="92a23-469">As opções de escolha para `choiceset`o.</span><span class="sxs-lookup"><span data-stu-id="92a23-469">The choice options for the `choiceset`.</span></span> <span data-ttu-id="92a23-470">Use somente quando `parameter.inputType` o é`choiceset`</span><span class="sxs-lookup"><span data-stu-id="92a23-470">Use only when `parameter.inputType` is `choiceset`</span></span>|
|`parameter.choices.title`|<span data-ttu-id="92a23-471">String</span><span class="sxs-lookup"><span data-stu-id="92a23-471">String</span></span>|<span data-ttu-id="92a23-472">128</span><span class="sxs-lookup"><span data-stu-id="92a23-472">128</span></span>||<span data-ttu-id="92a23-473">Título da opção</span><span class="sxs-lookup"><span data-stu-id="92a23-473">Title of the choice</span></span>|
|`parameter.choices.value`|<span data-ttu-id="92a23-474">String</span><span class="sxs-lookup"><span data-stu-id="92a23-474">String</span></span>|<span data-ttu-id="92a23-475">512</span><span class="sxs-lookup"><span data-stu-id="92a23-475">512</span></span>||<span data-ttu-id="92a23-476">Valor da opção</span><span class="sxs-lookup"><span data-stu-id="92a23-476">Value of the choice</span></span>|

## <a name="permissions"></a><span data-ttu-id="92a23-477">permissões</span><span class="sxs-lookup"><span data-stu-id="92a23-477">permissions</span></span>

<span data-ttu-id="92a23-478">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="92a23-478">**Optional**</span></span>

<span data-ttu-id="92a23-479">Uma matriz `string` que especifica quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão será executada.</span><span class="sxs-lookup"><span data-stu-id="92a23-479">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="92a23-480">As opções a seguir são não exclusivas:</span><span class="sxs-lookup"><span data-stu-id="92a23-480">The following options are non-exclusive:</span></span>

* <span data-ttu-id="92a23-481">`identity`&emsp; Requer informações de identidade do usuário</span><span class="sxs-lookup"><span data-stu-id="92a23-481">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="92a23-482">`messageTeamMembers`&emsp; Requer permissão para enviar mensagens diretas para membros da equipe</span><span class="sxs-lookup"><span data-stu-id="92a23-482">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="92a23-483">A alteração dessas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="92a23-483">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="92a23-484">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="92a23-484">devicePermissions</span></span>

<span data-ttu-id="92a23-485">**Opcional** Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-485">**Optional** Array of Strings</span></span>

<span data-ttu-id="92a23-486">Especifica os recursos nativos no dispositivo de um usuário para o qual seu aplicativo pode solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="92a23-486">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="92a23-487">As opções são:</span><span class="sxs-lookup"><span data-stu-id="92a23-487">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="92a23-488">validDomains</span><span class="sxs-lookup"><span data-stu-id="92a23-488">validDomains</span></span>

<span data-ttu-id="92a23-489">**Opcional**, exceto quando **necessário** , onde observado</span><span class="sxs-lookup"><span data-stu-id="92a23-489">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="92a23-490">Uma lista de domínios válidos a partir dos quais o aplicativo espera carregar qualquer conteúdo.</span><span class="sxs-lookup"><span data-stu-id="92a23-490">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="92a23-491">As listagens de domínio podem incluir curingas, `*.example.com`por exemplo.</span><span class="sxs-lookup"><span data-stu-id="92a23-491">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="92a23-492">Isso corresponde exatamente a um segmento do domínio; Se você precisar coincidir `a.b.example.com` e usar `*.*.example.com`.</span><span class="sxs-lookup"><span data-stu-id="92a23-492">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="92a23-493">Se a configuração de sua guia ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além daquele usado para configuração de guia, esse domínio deverá ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="92a23-493">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="92a23-494">No entanto, **não** é necessário incluir os domínios de provedores de identidade que você deseja suportar no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-494">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="92a23-495">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve `validDomains[]`incluir o accounts.google.com no.</span><span class="sxs-lookup"><span data-stu-id="92a23-495">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="92a23-496">Não adicione domínios que estejam fora do seu controle, seja diretamente ou via curingas.</span><span class="sxs-lookup"><span data-stu-id="92a23-496">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="92a23-497">Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="92a23-497">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="92a23-498">O objeto é uma matriz com todos os elementos do tipo `string`.</span><span class="sxs-lookup"><span data-stu-id="92a23-498">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="92a23-499">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="92a23-499">webApplicationInfo</span></span>

<span data-ttu-id="92a23-500">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="92a23-500">**Optional**</span></span>

<span data-ttu-id="92a23-501">Especifique a ID do aplicativo AAD e as informações do gráfico para ajudar os usuários a entrarem diretamente no aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="92a23-501">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="92a23-502">Nome</span><span class="sxs-lookup"><span data-stu-id="92a23-502">Name</span></span>| <span data-ttu-id="92a23-503">Tipo</span><span class="sxs-lookup"><span data-stu-id="92a23-503">Type</span></span>| <span data-ttu-id="92a23-504">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="92a23-504">Maximum size</span></span> | <span data-ttu-id="92a23-505">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="92a23-505">Required</span></span> | <span data-ttu-id="92a23-506">Descrição</span><span class="sxs-lookup"><span data-stu-id="92a23-506">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="92a23-507">String</span><span class="sxs-lookup"><span data-stu-id="92a23-507">String</span></span>|<span data-ttu-id="92a23-508">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-508">36 characters</span></span>|<span data-ttu-id="92a23-509">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-509">✔</span></span>|<span data-ttu-id="92a23-510">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92a23-510">AAD application id of the app.</span></span> <span data-ttu-id="92a23-511">Esta ID deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="92a23-511">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="92a23-512">String</span><span class="sxs-lookup"><span data-stu-id="92a23-512">String</span></span>|<span data-ttu-id="92a23-513">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="92a23-513">2048 characters</span></span>|<span data-ttu-id="92a23-514">✔</span><span class="sxs-lookup"><span data-stu-id="92a23-514">✔</span></span>|<span data-ttu-id="92a23-515">URL de recurso do aplicativo para aquisição de token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="92a23-515">Resource url of app for acquiring auth token for SSO.</span></span>|