---
title: Referência de esquema de manifesto
description: Descreve o esquema suportado pelo manifesto para o Microsoft Teams
keywords: esquema de manifesto do teams
ms.openlocfilehash: d4a2864c18a5066673bafab42a46733a0ab5f116
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672728"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="7db56-104">Referência: esquema de manifesto para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7db56-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="7db56-105">O manifesto do Microsoft Teams descreve como o aplicativo integra-se ao produto Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="7db56-105">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="7db56-106">Seu manifesto deve estar em conformidade com o esquema [`https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json)hospedado em.</span><span class="sxs-lookup"><span data-stu-id="7db56-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="7db56-107">As versões anteriores 1.0-1.4 também são suportadas (usando "v1. x" na URL).</span><span class="sxs-lookup"><span data-stu-id="7db56-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="7db56-108">O seguinte exemplo de esquema mostra todas as opções de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="7db56-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="7db56-109">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="7db56-109">Sample full manifest</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
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
    "defaultLanguageTag": "en-us",
    "additionalLanguages": [
      {
        "languageTag": "es-es",
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
        }
      ],
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
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
     "contoso.com",
     "mysite.someplace.com",
     "othersite.someplace.com"
  ]
}
```

<span data-ttu-id="7db56-110">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="7db56-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="7db56-111">$schema</span><span class="sxs-lookup"><span data-stu-id="7db56-111">$schema</span></span>

<span data-ttu-id="7db56-112">*Opcional, mas* &ndash; a cadeia de caracteres recomendada</span><span class="sxs-lookup"><span data-stu-id="7db56-112">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="7db56-113">A URL https://que faz referência ao esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="7db56-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="7db56-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="7db56-114">manifestVersion</span></span>

<span data-ttu-id="7db56-115">Cadeia de caracteres **obrigatória** &ndash;</span><span class="sxs-lookup"><span data-stu-id="7db56-115">**Required** &ndash; String</span></span>

<span data-ttu-id="7db56-116">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="7db56-116">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="7db56-117">Ele deve ser "1,5".</span><span class="sxs-lookup"><span data-stu-id="7db56-117">It should be "1.5".</span></span>

## <a name="version"></a><span data-ttu-id="7db56-118">versão</span><span class="sxs-lookup"><span data-stu-id="7db56-118">version</span></span>

<span data-ttu-id="7db56-119">Cadeia de caracteres **obrigatória** &ndash;</span><span class="sxs-lookup"><span data-stu-id="7db56-119">**Required** &ndash; String</span></span>

<span data-ttu-id="7db56-120">A versão do aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="7db56-120">The version of the specific app.</span></span> <span data-ttu-id="7db56-121">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="7db56-121">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="7db56-122">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="7db56-122">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="7db56-123">Se este aplicativo foi enviado para o repositório, o novo manifesto terá que ser reenviado e validado novamente.</span><span class="sxs-lookup"><span data-stu-id="7db56-123">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="7db56-124">Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, após serem aprovados.</span><span class="sxs-lookup"><span data-stu-id="7db56-124">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="7db56-125">Se as permissões solicitadas pelo aplicativo forem alteradas, os usuários serão solicitados a atualizar e a dar o consentimento novamente para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-125">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="7db56-126">Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (principal. Mínima. PATCH).</span><span class="sxs-lookup"><span data-stu-id="7db56-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="7db56-127">id</span><span class="sxs-lookup"><span data-stu-id="7db56-127">id</span></span>

<span data-ttu-id="7db56-128">ID de aplicativo da Microsoft **necessária** &ndash;</span><span class="sxs-lookup"><span data-stu-id="7db56-128">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="7db56-129">O identificador exclusivo gerado pela Microsoft para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-129">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="7db56-130">Se você tiver registrado um bot por meio da Microsoft bot Framework, ou se o aplicativo Web da sua guia já estiver conectado com a Microsoft, você já deve ter um ID e deve inseri-lo aqui.</span><span class="sxs-lookup"><span data-stu-id="7db56-130">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="7db56-131">Caso contrário, você deve gerar uma nova ID no portal de registro de aplicativos da Microsoft ([meus aplicativos](https://apps.dev.microsoft.com)), inseri-la aqui e reutilizá-la quando você adicionar um bot. Observação: se você estiver enviando uma atualização para o seu aplicativo existente no AppSource, a ID em seu manifesto não deverá ser modificada.</span><span class="sxs-lookup"><span data-stu-id="7db56-131">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you add a bot.Note: If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="packagename"></a><span data-ttu-id="7db56-132">Packagenamena</span><span class="sxs-lookup"><span data-stu-id="7db56-132">packageName</span></span>

<span data-ttu-id="7db56-133">Cadeia de caracteres **obrigatória** &ndash;</span><span class="sxs-lookup"><span data-stu-id="7db56-133">**Required** &ndash; String</span></span>

<span data-ttu-id="7db56-134">Um identificador exclusivo para esse aplicativo na notação de domínio reverso; por exemplo, com. example. MyApp.</span><span class="sxs-lookup"><span data-stu-id="7db56-134">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="7db56-135">developer</span><span class="sxs-lookup"><span data-stu-id="7db56-135">developer</span></span>

<span data-ttu-id="7db56-136">**Required**</span><span class="sxs-lookup"><span data-stu-id="7db56-136">**Required**</span></span>

<span data-ttu-id="7db56-137">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="7db56-137">Specifies information about your company.</span></span> <span data-ttu-id="7db56-138">Para aplicativos enviados para o AppSource (anteriormente Office Store), esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="7db56-138">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="7db56-139">Veja nossas [diretrizes de publicação](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="7db56-139">See our [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="7db56-140">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-140">Name</span></span>| <span data-ttu-id="7db56-141">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-141">Maximum size</span></span> | <span data-ttu-id="7db56-142">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-142">Required</span></span> | <span data-ttu-id="7db56-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-143">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="7db56-144">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-144">32 characters</span></span>|<span data-ttu-id="7db56-145">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-145">✔</span></span>|<span data-ttu-id="7db56-146">O nome de exibição para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="7db56-146">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="7db56-147">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-147">2048 characters</span></span>|<span data-ttu-id="7db56-148">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-148">✔</span></span>|<span data-ttu-id="7db56-149">A URL do https://para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="7db56-149">The https:// URL to the developer's website.</span></span> <span data-ttu-id="7db56-150">Este link deve levar os usuários à sua página de aterrissagem específica da empresa ou do produto.</span><span class="sxs-lookup"><span data-stu-id="7db56-150">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="7db56-151">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-151">2048 characters</span></span>|<span data-ttu-id="7db56-152">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-152">✔</span></span>|<span data-ttu-id="7db56-153">A URL do https://para a política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="7db56-153">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="7db56-154">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-154">2048 characters</span></span>|<span data-ttu-id="7db56-155">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-155">✔</span></span>|<span data-ttu-id="7db56-156">A URL do https://para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="7db56-156">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="7db56-157">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-157">10 characters</span></span>| |<span data-ttu-id="7db56-158">**Opcional** A ID de rede do parceiro da Microsoft que identifica a organização do parceiro que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-158">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="7db56-159">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="7db56-159">localizationInfo</span></span>

<span data-ttu-id="7db56-160">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="7db56-160">**Optional**</span></span>

<span data-ttu-id="7db56-161">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="7db56-161">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="7db56-162">Confira [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="7db56-162">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="7db56-163">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-163">Name</span></span>| <span data-ttu-id="7db56-164">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-164">Maximum size</span></span> | <span data-ttu-id="7db56-165">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-165">Required</span></span> | <span data-ttu-id="7db56-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-166">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="7db56-167">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-167">✔</span></span>|<span data-ttu-id="7db56-168">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="7db56-168">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="7db56-169">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="7db56-169">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="7db56-170">Uma matriz de objetos especificando traduções de idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="7db56-170">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="7db56-171">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-171">Name</span></span>| <span data-ttu-id="7db56-172">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-172">Maximum size</span></span> | <span data-ttu-id="7db56-173">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-173">Required</span></span> | <span data-ttu-id="7db56-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-174">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="7db56-175">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-175">✔</span></span>|<span data-ttu-id="7db56-176">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="7db56-176">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="7db56-177">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-177">✔</span></span>|<span data-ttu-id="7db56-178">Um caminho de arquivo relativo para um arquivo. JSON que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="7db56-178">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="7db56-179">nome</span><span class="sxs-lookup"><span data-stu-id="7db56-179">name</span></span>

<span data-ttu-id="7db56-180">**Required**</span><span class="sxs-lookup"><span data-stu-id="7db56-180">**Required**</span></span>

<span data-ttu-id="7db56-181">O nome da sua experiência de aplicativo, exibido aos usuários na experiência do teams.</span><span class="sxs-lookup"><span data-stu-id="7db56-181">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="7db56-182">Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="7db56-182">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="7db56-183">Os valores de `short` e `full` não devem ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="7db56-183">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="7db56-184">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-184">Name</span></span>| <span data-ttu-id="7db56-185">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-185">Maximum size</span></span> | <span data-ttu-id="7db56-186">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-186">Required</span></span> | <span data-ttu-id="7db56-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-187">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="7db56-188">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-188">30 characters</span></span>|<span data-ttu-id="7db56-189">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-189">✔</span></span>|<span data-ttu-id="7db56-190">O nome de exibição curto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-190">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="7db56-191">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-191">100 characters</span></span>||<span data-ttu-id="7db56-192">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="7db56-192">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="7db56-193">description</span><span class="sxs-lookup"><span data-stu-id="7db56-193">description</span></span>

<span data-ttu-id="7db56-194">**Required**</span><span class="sxs-lookup"><span data-stu-id="7db56-194">**Required**</span></span>

<span data-ttu-id="7db56-195">Descreve seu aplicativo para os usuários.</span><span class="sxs-lookup"><span data-stu-id="7db56-195">Describes your app to users.</span></span> <span data-ttu-id="7db56-196">Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="7db56-196">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="7db56-197">Certifique-se de que sua descrição descreve precisamente sua experiência e fornece informações para ajudar os clientes potenciais a entender o que a sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="7db56-197">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="7db56-198">Você também deve observar, na descrição completa, se for necessário usar uma conta externa.</span><span class="sxs-lookup"><span data-stu-id="7db56-198">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="7db56-199">Os valores de `short` e `full` não devem ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="7db56-199">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="7db56-200">Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir nenhum outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-200">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="7db56-201">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-201">Name</span></span>| <span data-ttu-id="7db56-202">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-202">Maximum size</span></span> | <span data-ttu-id="7db56-203">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-203">Required</span></span> | <span data-ttu-id="7db56-204">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-204">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="7db56-205">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-205">80 characters</span></span>|<span data-ttu-id="7db56-206">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-206">✔</span></span>|<span data-ttu-id="7db56-207">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="7db56-207">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="7db56-208">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-208">4000 characters</span></span>|<span data-ttu-id="7db56-209">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-209">✔</span></span>|<span data-ttu-id="7db56-210">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-210">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="7db56-211">ícones</span><span class="sxs-lookup"><span data-stu-id="7db56-211">icons</span></span>

<span data-ttu-id="7db56-212">**Required**</span><span class="sxs-lookup"><span data-stu-id="7db56-212">**Required**</span></span>

<span data-ttu-id="7db56-213">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="7db56-213">Icons used within the Teams app.</span></span> <span data-ttu-id="7db56-214">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="7db56-214">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="7db56-215">Consulte [ícones](~/concepts/build-and-test/apps-package.md#icons) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="7db56-215">See [Icons](~/concepts/build-and-test/apps-package.md#icons) for more information.</span></span>

|<span data-ttu-id="7db56-216">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-216">Name</span></span>| <span data-ttu-id="7db56-217">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-217">Maximum size</span></span> | <span data-ttu-id="7db56-218">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-218">Required</span></span> | <span data-ttu-id="7db56-219">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-219">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="7db56-220">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-220">2048 characters</span></span>|<span data-ttu-id="7db56-221">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-221">✔</span></span>|<span data-ttu-id="7db56-222">Um caminho de arquivo relativo para um ícone de estrutura de tópicos de PNG de 32 x 32 transparente.</span><span class="sxs-lookup"><span data-stu-id="7db56-222">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="7db56-223">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-223">2048 characters</span></span>|<span data-ttu-id="7db56-224">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-224">✔</span></span>|<span data-ttu-id="7db56-225">Um caminho de arquivo relativo para um ícone de 192x192 do PNG completo.</span><span class="sxs-lookup"><span data-stu-id="7db56-225">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="7db56-226">accentColor</span><span class="sxs-lookup"><span data-stu-id="7db56-226">accentColor</span></span>

<span data-ttu-id="7db56-227">Cadeia de caracteres **obrigatória** &ndash;</span><span class="sxs-lookup"><span data-stu-id="7db56-227">**Required** &ndash; String</span></span>

<span data-ttu-id="7db56-228">Uma cor a ser usada em conjunto com e como um plano de fundo para seus ícones de estrutura de tópicos.</span><span class="sxs-lookup"><span data-stu-id="7db56-228">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="7db56-229">O valor deve ser um código de cor HTML válido começando com ' # ', por `#4464ee`exemplo.</span><span class="sxs-lookup"><span data-stu-id="7db56-229">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="7db56-230">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="7db56-230">configurableTabs</span></span>

<span data-ttu-id="7db56-231">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="7db56-231">**Optional**</span></span>

<span data-ttu-id="7db56-232">Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração adicional antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="7db56-232">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="7db56-233">Guias configuráveis têm suporte apenas no escopo Teams, e atualmente só há suporte para uma guia por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-233">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="7db56-234">O objeto é uma matriz com todos os elementos do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="7db56-234">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="7db56-235">Esse bloco só é necessário para soluções que oferecem uma solução de guia de canal configurável.</span><span class="sxs-lookup"><span data-stu-id="7db56-235">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="7db56-236">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-236">Name</span></span>| <span data-ttu-id="7db56-237">Tipo</span><span class="sxs-lookup"><span data-stu-id="7db56-237">Type</span></span>| <span data-ttu-id="7db56-238">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-238">Maximum size</span></span> | <span data-ttu-id="7db56-239">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-239">Required</span></span> | <span data-ttu-id="7db56-240">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-240">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="7db56-241">String</span><span class="sxs-lookup"><span data-stu-id="7db56-241">String</span></span>|<span data-ttu-id="7db56-242">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-242">2048 characters</span></span>|<span data-ttu-id="7db56-243">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-243">✔</span></span>|<span data-ttu-id="7db56-244">A URL do https://a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="7db56-244">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="7db56-245">Boolean</span><span class="sxs-lookup"><span data-stu-id="7db56-245">Boolean</span></span>|||<span data-ttu-id="7db56-246">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="7db56-246">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="7db56-247">Será`true`</span><span class="sxs-lookup"><span data-stu-id="7db56-247">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="7db56-248">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="7db56-248">Array of enum</span></span>|<span data-ttu-id="7db56-249">1 </span><span class="sxs-lookup"><span data-stu-id="7db56-249">1</span></span>|<span data-ttu-id="7db56-250">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-250">✔</span></span>|<span data-ttu-id="7db56-251">No momento, as guias configuráveis `team` só `groupchat` dão suporte a e os escopos.</span><span class="sxs-lookup"><span data-stu-id="7db56-251">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="7db56-252">String</span><span class="sxs-lookup"><span data-stu-id="7db56-252">String</span></span>|<span data-ttu-id="7db56-253">2048</span><span class="sxs-lookup"><span data-stu-id="7db56-253">2048</span></span>||<span data-ttu-id="7db56-254">Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="7db56-254">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="7db56-255">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="7db56-255">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="7db56-256">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="7db56-256">Array of enum</span></span>|<span data-ttu-id="7db56-257">1 </span><span class="sxs-lookup"><span data-stu-id="7db56-257">1</span></span>||<span data-ttu-id="7db56-258">Define como sua guia será disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="7db56-258">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="7db56-259">Opções são `sharePointFullPage` e`sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="7db56-259">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="7db56-260">staticTabs</span><span class="sxs-lookup"><span data-stu-id="7db56-260">staticTabs</span></span>

<span data-ttu-id="7db56-261">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="7db56-261">**Optional**</span></span>

<span data-ttu-id="7db56-262">Define um conjunto de guias que podem ser "fixadas" por padrão, sem o usuário adicioná-las manualmente.</span><span class="sxs-lookup"><span data-stu-id="7db56-262">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="7db56-263">As guias estáticas `personal` declaradas no escopo são sempre fixadas para a experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-263">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="7db56-264">Guias static declaradas `team` no escopo não são suportadas atualmente.</span><span class="sxs-lookup"><span data-stu-id="7db56-264">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="7db56-265">O objeto é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="7db56-265">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="7db56-266">Esse bloco é necessário somente para soluções que oferecem uma solução de guia estática.</span><span class="sxs-lookup"><span data-stu-id="7db56-266">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="7db56-267">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-267">Name</span></span>| <span data-ttu-id="7db56-268">Tipo</span><span class="sxs-lookup"><span data-stu-id="7db56-268">Type</span></span>| <span data-ttu-id="7db56-269">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-269">Maximum size</span></span> | <span data-ttu-id="7db56-270">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-270">Required</span></span> | <span data-ttu-id="7db56-271">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-271">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="7db56-272">String</span><span class="sxs-lookup"><span data-stu-id="7db56-272">String</span></span>|<span data-ttu-id="7db56-273">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-273">64 characters</span></span>|<span data-ttu-id="7db56-274">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-274">✔</span></span>|<span data-ttu-id="7db56-275">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="7db56-275">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="7db56-276">String</span><span class="sxs-lookup"><span data-stu-id="7db56-276">String</span></span>|<span data-ttu-id="7db56-277">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-277">128 characters</span></span>|<span data-ttu-id="7db56-278">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-278">✔</span></span>|<span data-ttu-id="7db56-279">O nome de exibição da guia na interface de canal.</span><span class="sxs-lookup"><span data-stu-id="7db56-279">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="7db56-280">String</span><span class="sxs-lookup"><span data-stu-id="7db56-280">String</span></span>|<span data-ttu-id="7db56-281">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-281">2048 characters</span></span>|<span data-ttu-id="7db56-282">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-282">✔</span></span>|<span data-ttu-id="7db56-283">A URL https://que aponta para a interface do usuário da entidade a ser exibida na tela do teams.</span><span class="sxs-lookup"><span data-stu-id="7db56-283">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="7db56-284">String</span><span class="sxs-lookup"><span data-stu-id="7db56-284">String</span></span>|<span data-ttu-id="7db56-285">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-285">2048 characters</span></span>||<span data-ttu-id="7db56-286">A URL do https://para apontar para o modo de exibição de um usuário em um navegador.</span><span class="sxs-lookup"><span data-stu-id="7db56-286">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="7db56-287">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="7db56-287">Array of enum</span></span>|<span data-ttu-id="7db56-288">1 </span><span class="sxs-lookup"><span data-stu-id="7db56-288">1</span></span>|<span data-ttu-id="7db56-289">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-289">✔</span></span>|<span data-ttu-id="7db56-290">Atualmente, as guias estáticas oferecem `personal` suporte somente ao escopo, o que significa que ela pode ser provisionada somente como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="7db56-290">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="7db56-291">robôs</span><span class="sxs-lookup"><span data-stu-id="7db56-291">bots</span></span>

<span data-ttu-id="7db56-292">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="7db56-292">**Optional**</span></span>

<span data-ttu-id="7db56-293">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="7db56-293">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="7db56-294">O objeto é uma matriz (máximo de apenas 1 elemento&mdash;atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="7db56-294">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="7db56-295">Esse bloco é necessário somente para soluções que oferecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="7db56-295">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="7db56-296">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-296">Name</span></span>| <span data-ttu-id="7db56-297">Tipo</span><span class="sxs-lookup"><span data-stu-id="7db56-297">Type</span></span>| <span data-ttu-id="7db56-298">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-298">Maximum size</span></span> | <span data-ttu-id="7db56-299">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-299">Required</span></span> | <span data-ttu-id="7db56-300">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-300">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="7db56-301">String</span><span class="sxs-lookup"><span data-stu-id="7db56-301">String</span></span>|<span data-ttu-id="7db56-302">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-302">64 characters</span></span>|<span data-ttu-id="7db56-303">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-303">✔</span></span>|<span data-ttu-id="7db56-304">A ID exclusiva do aplicativo da Microsoft para o bot, conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="7db56-304">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="7db56-305">Isso pode ser o mesmo que a ID de [aplicativo](#id)geral.</span><span class="sxs-lookup"><span data-stu-id="7db56-305">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="7db56-306">Boolean</span><span class="sxs-lookup"><span data-stu-id="7db56-306">Boolean</span></span>|||<span data-ttu-id="7db56-307">Descreve se o bot utiliza ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="7db56-307">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="7db56-308">Será`false`</span><span class="sxs-lookup"><span data-stu-id="7db56-308">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="7db56-309">Boolean</span><span class="sxs-lookup"><span data-stu-id="7db56-309">Boolean</span></span>|||<span data-ttu-id="7db56-310">Indica se um bot é um bot unidirecional somente de notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="7db56-310">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="7db56-311">Será`false`</span><span class="sxs-lookup"><span data-stu-id="7db56-311">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="7db56-312">Boolean</span><span class="sxs-lookup"><span data-stu-id="7db56-312">Boolean</span></span>|||<span data-ttu-id="7db56-313">Indica se o bot dá suporte à capacidade de carregar/baixar arquivos no chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="7db56-313">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="7db56-314">Será`false`</span><span class="sxs-lookup"><span data-stu-id="7db56-314">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="7db56-315">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="7db56-315">Array of enum</span></span>|<span data-ttu-id="7db56-316">3 </span><span class="sxs-lookup"><span data-stu-id="7db56-316">3</span></span>|<span data-ttu-id="7db56-317">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-317">✔</span></span>|<span data-ttu-id="7db56-318">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência com escopo para um usuário individual sozinho (`personal`).</span><span class="sxs-lookup"><span data-stu-id="7db56-318">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="7db56-319">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="7db56-319">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="7db56-320">bots. commandLists</span><span class="sxs-lookup"><span data-stu-id="7db56-320">bots.commandLists</span></span>

<span data-ttu-id="7db56-321">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="7db56-321">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="7db56-322">O objeto é uma matriz (máximo de dois elementos) com todos os elementos do `object`tipo; Você deve definir uma lista de comandos separada para cada escopo que seu bot suporta.</span><span class="sxs-lookup"><span data-stu-id="7db56-322">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="7db56-323">Consulte [menus de bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="7db56-323">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="7db56-324">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-324">Name</span></span>| <span data-ttu-id="7db56-325">Tipo</span><span class="sxs-lookup"><span data-stu-id="7db56-325">Type</span></span>| <span data-ttu-id="7db56-326">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-326">Maximum size</span></span> | <span data-ttu-id="7db56-327">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-327">Required</span></span> | <span data-ttu-id="7db56-328">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-328">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="7db56-329">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="7db56-329">array of enum</span></span>|<span data-ttu-id="7db56-330">3 </span><span class="sxs-lookup"><span data-stu-id="7db56-330">3</span></span>|<span data-ttu-id="7db56-331">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-331">✔</span></span>|<span data-ttu-id="7db56-332">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="7db56-332">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="7db56-333">As opções `team`são `personal`, e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="7db56-333">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="7db56-334">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="7db56-334">array of objects</span></span>|<span data-ttu-id="7db56-335">10 </span><span class="sxs-lookup"><span data-stu-id="7db56-335">10</span></span>|<span data-ttu-id="7db56-336">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-336">✔</span></span>|<span data-ttu-id="7db56-337">Uma matriz de comandos para a qual o bot oferece suporte:</span><span class="sxs-lookup"><span data-stu-id="7db56-337">An array of commands the bot supports:</span></span><br><span data-ttu-id="7db56-338">`title`: o nome do comando do bot (cadeia de caracteres, 32)</span><span class="sxs-lookup"><span data-stu-id="7db56-338">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="7db56-339">`description`: uma simples descrição ou exemplo da sintaxe do comando e seu argumento (String, 128)</span><span class="sxs-lookup"><span data-stu-id="7db56-339">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

## <a name="connectors"></a><span data-ttu-id="7db56-340">conectores</span><span class="sxs-lookup"><span data-stu-id="7db56-340">connectors</span></span>

<span data-ttu-id="7db56-341">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="7db56-341">**Optional**</span></span>

<span data-ttu-id="7db56-342">O `connectors` bloco define um conector do Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-342">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="7db56-343">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do `object`tipo.</span><span class="sxs-lookup"><span data-stu-id="7db56-343">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="7db56-344">Esse bloco é necessário somente para soluções que fornecem um conector.</span><span class="sxs-lookup"><span data-stu-id="7db56-344">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="7db56-345">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-345">Name</span></span>| <span data-ttu-id="7db56-346">Tipo</span><span class="sxs-lookup"><span data-stu-id="7db56-346">Type</span></span>| <span data-ttu-id="7db56-347">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-347">Maximum size</span></span> | <span data-ttu-id="7db56-348">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-348">Required</span></span> | <span data-ttu-id="7db56-349">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-349">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="7db56-350">String</span><span class="sxs-lookup"><span data-stu-id="7db56-350">String</span></span>|<span data-ttu-id="7db56-351">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-351">2048 characters</span></span>|<span data-ttu-id="7db56-352">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-352">✔</span></span>|<span data-ttu-id="7db56-353">A URL do https://a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="7db56-353">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="7db56-354">String</span><span class="sxs-lookup"><span data-stu-id="7db56-354">String</span></span>|<span data-ttu-id="7db56-355">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-355">64 characters</span></span>|<span data-ttu-id="7db56-356">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-356">✔</span></span>|<span data-ttu-id="7db56-357">Um identificador exclusivo para o conector que corresponde à sua ID no [painel do desenvolvedor de conectores](https://aka.ms/connectorsdashboard).</span><span class="sxs-lookup"><span data-stu-id="7db56-357">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="7db56-358">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="7db56-358">Array of enum</span></span>|<span data-ttu-id="7db56-359">1 </span><span class="sxs-lookup"><span data-stu-id="7db56-359">1</span></span>|<span data-ttu-id="7db56-360">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-360">✔</span></span>|<span data-ttu-id="7db56-361">Especifica se o conector oferece uma experiência no contexto de um canal em uma `team`ou uma experiência com escopo para um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="7db56-361">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="7db56-362">Atualmente, só há `team` suporte para o escopo.</span><span class="sxs-lookup"><span data-stu-id="7db56-362">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="7db56-363">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="7db56-363">composeExtensions</span></span>

<span data-ttu-id="7db56-364">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="7db56-364">**Optional**</span></span>

<span data-ttu-id="7db56-365">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-365">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="7db56-366">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem a funcionar.</span><span class="sxs-lookup"><span data-stu-id="7db56-366">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="7db56-367">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do `object`tipo.</span><span class="sxs-lookup"><span data-stu-id="7db56-367">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="7db56-368">Esse bloco é necessário somente para soluções que forneçam uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="7db56-368">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="7db56-369">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-369">Name</span></span>| <span data-ttu-id="7db56-370">Tipo</span><span class="sxs-lookup"><span data-stu-id="7db56-370">Type</span></span> | <span data-ttu-id="7db56-371">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-371">Maximum Size</span></span> | <span data-ttu-id="7db56-372">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-372">Required</span></span> | <span data-ttu-id="7db56-373">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-373">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="7db56-374">String</span><span class="sxs-lookup"><span data-stu-id="7db56-374">String</span></span>|<span data-ttu-id="7db56-375">64</span><span class="sxs-lookup"><span data-stu-id="7db56-375">64</span></span>|<span data-ttu-id="7db56-376">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-376">✔</span></span>|<span data-ttu-id="7db56-377">A ID exclusiva do aplicativo da Microsoft para o bot que faz a extensão do sistema de mensagens, conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="7db56-377">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="7db56-378">Isso pode ser o mesmo que a ID de aplicativo geral.</span><span class="sxs-lookup"><span data-stu-id="7db56-378">This may well be the same as the overall App ID.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="7db56-379">Boolean</span><span class="sxs-lookup"><span data-stu-id="7db56-379">Boolean</span></span>|||<span data-ttu-id="7db56-380">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7db56-380">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="7db56-381">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="7db56-381">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="7db56-382">Matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="7db56-382">Array of object</span></span>|<span data-ttu-id="7db56-383">10 </span><span class="sxs-lookup"><span data-stu-id="7db56-383">10</span></span>|<span data-ttu-id="7db56-384">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-384">✔</span></span>|<span data-ttu-id="7db56-385">Matriz de comandos que a extensão de mensagens oferece suporte</span><span class="sxs-lookup"><span data-stu-id="7db56-385">Array of commands the messaging extension supports</span></span>|
|`messageHandlers`|<span data-ttu-id="7db56-386">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="7db56-386">Array of Objects</span></span>|<span data-ttu-id="7db56-387">5 </span><span class="sxs-lookup"><span data-stu-id="7db56-387">5</span></span>||<span data-ttu-id="7db56-388">Uma lista de manipuladores que permitem que os aplicativos sejam chamados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="7db56-388">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="7db56-389">Os domínios também devem ser listados no`validDomains`</span><span class="sxs-lookup"><span data-stu-id="7db56-389">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="7db56-390">String</span><span class="sxs-lookup"><span data-stu-id="7db56-390">String</span></span>|||<span data-ttu-id="7db56-391">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="7db56-391">The type of message handler.</span></span> <span data-ttu-id="7db56-392">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="7db56-392">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="7db56-393">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-393">Array of Strings</span></span>|||<span data-ttu-id="7db56-394">Matriz de domínios para o qual o manipulador de mensagens de link pode se registrar.</span><span class="sxs-lookup"><span data-stu-id="7db56-394">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="7db56-395">composeExtensions. Commands</span><span class="sxs-lookup"><span data-stu-id="7db56-395">composeExtensions.commands</span></span>

<span data-ttu-id="7db56-396">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="7db56-396">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="7db56-397">Cada comando aparece no Microsoft Teams como uma possível interação do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7db56-397">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="7db56-398">Há um máximo de 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="7db56-398">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="7db56-399">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="7db56-399">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="7db56-400">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-400">Name</span></span>| <span data-ttu-id="7db56-401">Tipo</span><span class="sxs-lookup"><span data-stu-id="7db56-401">Type</span></span>| <span data-ttu-id="7db56-402">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-402">Maximum size</span></span> | <span data-ttu-id="7db56-403">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-403">Required</span></span> | <span data-ttu-id="7db56-404">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-404">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="7db56-405">String</span><span class="sxs-lookup"><span data-stu-id="7db56-405">String</span></span>|<span data-ttu-id="7db56-406">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-406">64 characters</span></span>|<span data-ttu-id="7db56-407">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-407">✔</span></span>|<span data-ttu-id="7db56-408">A ID do comando</span><span class="sxs-lookup"><span data-stu-id="7db56-408">The ID for the command</span></span>|
|`type`|<span data-ttu-id="7db56-409">String</span><span class="sxs-lookup"><span data-stu-id="7db56-409">String</span></span>|<span data-ttu-id="7db56-410">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-410">64 characters</span></span>||<span data-ttu-id="7db56-411">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="7db56-411">Type of the command.</span></span> <span data-ttu-id="7db56-412">Um `query` ou `action`.</span><span class="sxs-lookup"><span data-stu-id="7db56-412">One of `query` or `action`.</span></span> <span data-ttu-id="7db56-413">Será`query`</span><span class="sxs-lookup"><span data-stu-id="7db56-413">Default: `query`</span></span>|
|`title`|<span data-ttu-id="7db56-414">String</span><span class="sxs-lookup"><span data-stu-id="7db56-414">String</span></span>|<span data-ttu-id="7db56-415">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-415">32 characters</span></span>|<span data-ttu-id="7db56-416">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-416">✔</span></span>|<span data-ttu-id="7db56-417">O nome do comando amigável</span><span class="sxs-lookup"><span data-stu-id="7db56-417">The user-friendly command name</span></span>|
|`description`|<span data-ttu-id="7db56-418">String</span><span class="sxs-lookup"><span data-stu-id="7db56-418">String</span></span>|<span data-ttu-id="7db56-419">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-419">128 characters</span></span>||<span data-ttu-id="7db56-420">A descrição que aparece para os usuários para indicar a finalidade desse comando</span><span class="sxs-lookup"><span data-stu-id="7db56-420">The description that appears to users to indicate the purpose of this command</span></span>|
|`initialRun`|<span data-ttu-id="7db56-421">Boolean</span><span class="sxs-lookup"><span data-stu-id="7db56-421">Boolean</span></span>|||<span data-ttu-id="7db56-422">Um valor Boolean que indica se o comando deve ser executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7db56-422">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="7db56-423">Será`false`</span><span class="sxs-lookup"><span data-stu-id="7db56-423">Default: `false`</span></span>|
|`context`|<span data-ttu-id="7db56-424">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-424">Array of Strings</span></span>|<span data-ttu-id="7db56-425">3 </span><span class="sxs-lookup"><span data-stu-id="7db56-425">3</span></span>||<span data-ttu-id="7db56-426">Define onde a extensão de mensagem pode ser chamada.</span><span class="sxs-lookup"><span data-stu-id="7db56-426">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="7db56-427">Qualquer combinação de `compose`, `commandBox`, `message`.</span><span class="sxs-lookup"><span data-stu-id="7db56-427">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="7db56-428">O padrão é`["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="7db56-428">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="7db56-429">Boolean</span><span class="sxs-lookup"><span data-stu-id="7db56-429">Boolean</span></span>|||<span data-ttu-id="7db56-430">Um valor Boolean que indica se deve buscar o módulo de tarefa dinamicamente</span><span class="sxs-lookup"><span data-stu-id="7db56-430">A boolean value that indicates if it should fetch the task module dynamically</span></span>|
|`taskInfo`|<span data-ttu-id="7db56-431">Objeto</span><span class="sxs-lookup"><span data-stu-id="7db56-431">Object</span></span>|||<span data-ttu-id="7db56-432">Especificar o módulo de tarefa a ser pré-carregar ao usar um comando de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="7db56-432">Specify the task module to preload when using a messaging extension command</span></span>|
|`taskInfo.title`|<span data-ttu-id="7db56-433">String</span><span class="sxs-lookup"><span data-stu-id="7db56-433">String</span></span>|<span data-ttu-id="7db56-434">64</span><span class="sxs-lookup"><span data-stu-id="7db56-434">64</span></span>||<span data-ttu-id="7db56-435">Título inicial da caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="7db56-435">Initial dialog title</span></span>|
|`taskInfo.width`|<span data-ttu-id="7db56-436">String</span><span class="sxs-lookup"><span data-stu-id="7db56-436">String</span></span>|||<span data-ttu-id="7db56-437">Largura da caixa de diálogo: um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '</span><span class="sxs-lookup"><span data-stu-id="7db56-437">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.height`|<span data-ttu-id="7db56-438">String</span><span class="sxs-lookup"><span data-stu-id="7db56-438">String</span></span>|||<span data-ttu-id="7db56-439">Altura da caixa de diálogo-um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '</span><span class="sxs-lookup"><span data-stu-id="7db56-439">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.url`|<span data-ttu-id="7db56-440">String</span><span class="sxs-lookup"><span data-stu-id="7db56-440">String</span></span>|||<span data-ttu-id="7db56-441">URL do WebView inicial</span><span class="sxs-lookup"><span data-stu-id="7db56-441">Initial webview URL</span></span>|
|`parameters`|<span data-ttu-id="7db56-442">Matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="7db56-442">Array of object</span></span>|<span data-ttu-id="7db56-443">5 </span><span class="sxs-lookup"><span data-stu-id="7db56-443">5</span></span>|<span data-ttu-id="7db56-444">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-444">✔</span></span>|<span data-ttu-id="7db56-445">A lista de parâmetros que o comando utiliza.</span><span class="sxs-lookup"><span data-stu-id="7db56-445">The list of parameters the command takes.</span></span> <span data-ttu-id="7db56-446">Mínimo: 1; máximo: 5</span><span class="sxs-lookup"><span data-stu-id="7db56-446">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="7db56-447">String</span><span class="sxs-lookup"><span data-stu-id="7db56-447">String</span></span>|<span data-ttu-id="7db56-448">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-448">64 characters</span></span>|<span data-ttu-id="7db56-449">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-449">✔</span></span>|<span data-ttu-id="7db56-450">O nome do parâmetro conforme ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="7db56-450">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="7db56-451">Isso é incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="7db56-451">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="7db56-452">String</span><span class="sxs-lookup"><span data-stu-id="7db56-452">String</span></span>|<span data-ttu-id="7db56-453">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-453">32 characters</span></span>|<span data-ttu-id="7db56-454">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-454">✔</span></span>|<span data-ttu-id="7db56-455">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7db56-455">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="7db56-456">String</span><span class="sxs-lookup"><span data-stu-id="7db56-456">String</span></span>|<span data-ttu-id="7db56-457">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-457">128 characters</span></span>||<span data-ttu-id="7db56-458">Cadeia de caracteres amigável que descreve a finalidade deste parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7db56-458">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="7db56-459">String</span><span class="sxs-lookup"><span data-stu-id="7db56-459">String</span></span>|<span data-ttu-id="7db56-460">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-460">128 characters</span></span>||<span data-ttu-id="7db56-461">Define o tipo de controle exibido em um módulo de tarefas `fetchTask: true`para o.</span><span class="sxs-lookup"><span data-stu-id="7db56-461">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="7db56-462">Um de `text`, `textarea`, `number`, `date`, `time`, `toggle`,`choiceset`</span><span class="sxs-lookup"><span data-stu-id="7db56-462">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`</span></span>|
|`parameter.choices`|<span data-ttu-id="7db56-463">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="7db56-463">Array of Objects</span></span>|<span data-ttu-id="7db56-464">10 </span><span class="sxs-lookup"><span data-stu-id="7db56-464">10</span></span>||<span data-ttu-id="7db56-465">As opções de escolha para `choiceset`o.</span><span class="sxs-lookup"><span data-stu-id="7db56-465">The choice options for the `choiceset`.</span></span> <span data-ttu-id="7db56-466">Use somente quando `parameter.inputType` o é`choiceset`</span><span class="sxs-lookup"><span data-stu-id="7db56-466">Use only when `parameter.inputType` is `choiceset`</span></span>|
|`parameter.choices.title`|<span data-ttu-id="7db56-467">String</span><span class="sxs-lookup"><span data-stu-id="7db56-467">String</span></span>|<span data-ttu-id="7db56-468">128</span><span class="sxs-lookup"><span data-stu-id="7db56-468">128</span></span>||<span data-ttu-id="7db56-469">Título da opção</span><span class="sxs-lookup"><span data-stu-id="7db56-469">Title of the choice</span></span>|
|`parameter.choices.value`|<span data-ttu-id="7db56-470">String</span><span class="sxs-lookup"><span data-stu-id="7db56-470">String</span></span>|<span data-ttu-id="7db56-471">512</span><span class="sxs-lookup"><span data-stu-id="7db56-471">512</span></span>||<span data-ttu-id="7db56-472">Valor da opção</span><span class="sxs-lookup"><span data-stu-id="7db56-472">Value of the choice</span></span>|

## <a name="permissions"></a><span data-ttu-id="7db56-473">permissões</span><span class="sxs-lookup"><span data-stu-id="7db56-473">permissions</span></span>

<span data-ttu-id="7db56-474">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="7db56-474">**Optional**</span></span>

<span data-ttu-id="7db56-475">Uma matriz `string` que especifica quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão será executada.</span><span class="sxs-lookup"><span data-stu-id="7db56-475">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="7db56-476">As opções a seguir são não exclusivas:</span><span class="sxs-lookup"><span data-stu-id="7db56-476">The following options are non-exclusive:</span></span>

* <span data-ttu-id="7db56-477">`identity`&emsp; Requer informações de identidade do usuário</span><span class="sxs-lookup"><span data-stu-id="7db56-477">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="7db56-478">`messageTeamMembers`&emsp; Requer permissão para enviar mensagens diretas para membros da equipe</span><span class="sxs-lookup"><span data-stu-id="7db56-478">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="7db56-479">A alteração dessas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="7db56-479">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span> <span data-ttu-id="7db56-480">Veja [atualização do seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="7db56-480">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="7db56-481">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="7db56-481">devicePermissions</span></span>

<span data-ttu-id="7db56-482">**Opcional** Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-482">**Optional** Array of Strings</span></span>

<span data-ttu-id="7db56-483">Especifica os recursos nativos no dispositivo de um usuário para o qual seu aplicativo pode solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="7db56-483">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="7db56-484">As opções são:</span><span class="sxs-lookup"><span data-stu-id="7db56-484">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="7db56-485">validDomains</span><span class="sxs-lookup"><span data-stu-id="7db56-485">validDomains</span></span>

<span data-ttu-id="7db56-486">**Opcional**, exceto quando **necessário** , onde observado</span><span class="sxs-lookup"><span data-stu-id="7db56-486">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="7db56-487">Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="7db56-487">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="7db56-488">As listagens de domínio podem incluir curingas, `*.example.com`por exemplo.</span><span class="sxs-lookup"><span data-stu-id="7db56-488">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="7db56-489">Isso corresponde exatamente a um segmento do domínio; Se você precisar coincidir `a.b.example.com` e usar `*.*.example.com`.</span><span class="sxs-lookup"><span data-stu-id="7db56-489">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="7db56-490">Se a configuração de sua guia ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além daquele usado para configuração de guia, esse domínio deverá ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="7db56-490">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="7db56-491">No entanto, **não** é necessário incluir os domínios de provedores de identidade que você deseja suportar no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-491">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="7db56-492">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve `validDomains[]`incluir o accounts.google.com no.</span><span class="sxs-lookup"><span data-stu-id="7db56-492">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="7db56-493">Aplicativos do teams que exigem suas próprias URLs do SharePoint para funcionar bem, podem incluir "{teamsitedomain}" em sua lista de domínios válida.</span><span class="sxs-lookup"><span data-stu-id="7db56-493">Teams apps that require their own sharepoint URLs to function well, may include "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7db56-494">Não adicione domínios que estejam fora do seu controle, seja diretamente ou via curingas.</span><span class="sxs-lookup"><span data-stu-id="7db56-494">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="7db56-495">Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="7db56-495">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="7db56-496">O objeto é uma matriz com todos os elementos do tipo `string`.</span><span class="sxs-lookup"><span data-stu-id="7db56-496">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="7db56-497">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="7db56-497">webApplicationInfo</span></span>

<span data-ttu-id="7db56-498">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="7db56-498">**Optional**</span></span>

<span data-ttu-id="7db56-499">Especifique a ID do aplicativo AAD e as informações do gráfico para ajudar os usuários a entrarem diretamente no aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="7db56-499">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="7db56-500">Nome</span><span class="sxs-lookup"><span data-stu-id="7db56-500">Name</span></span>| <span data-ttu-id="7db56-501">Tipo</span><span class="sxs-lookup"><span data-stu-id="7db56-501">Type</span></span>| <span data-ttu-id="7db56-502">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="7db56-502">Maximum size</span></span> | <span data-ttu-id="7db56-503">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7db56-503">Required</span></span> | <span data-ttu-id="7db56-504">Descrição</span><span class="sxs-lookup"><span data-stu-id="7db56-504">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="7db56-505">String</span><span class="sxs-lookup"><span data-stu-id="7db56-505">String</span></span>|<span data-ttu-id="7db56-506">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-506">36 characters</span></span>|<span data-ttu-id="7db56-507">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-507">✔</span></span>|<span data-ttu-id="7db56-508">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7db56-508">AAD application id of the app.</span></span> <span data-ttu-id="7db56-509">Esta ID deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="7db56-509">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="7db56-510">String</span><span class="sxs-lookup"><span data-stu-id="7db56-510">String</span></span>|<span data-ttu-id="7db56-511">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="7db56-511">2048 characters</span></span>|<span data-ttu-id="7db56-512">✔</span><span class="sxs-lookup"><span data-stu-id="7db56-512">✔</span></span>|<span data-ttu-id="7db56-513">URL de recurso do aplicativo para aquisição de token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="7db56-513">Resource url of app for acquiring auth token for SSO.</span></span>|
