---
title: Referência de esquema de manifesto
description: Descreve o esquema suportado pelo manifesto para o Microsoft Teams
keywords: esquema de manifesto do teams
ms.openlocfilehash: 061b39430cf8eba229b4e0c3012a5bbf752a5e85
ms.sourcegitcommit: 6c786434b56cc8c2765a14aa1f6149870245f309
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "44801041"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="64062-104">Referência: esquema de manifesto para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="64062-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="64062-105">O manifesto do Microsoft Teams descreve como o aplicativo integra-se ao produto Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="64062-105">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="64062-106">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="64062-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="64062-107">As versões anteriores 1.0-1.4 também são suportadas (usando "v1. x" na URL).</span><span class="sxs-lookup"><span data-stu-id="64062-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="64062-108">O seguinte exemplo de esquema mostra todas as opções de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="64062-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="64062-109">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="64062-109">Sample full manifest</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
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
          "type" : "query",
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

<span data-ttu-id="64062-110">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="64062-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="64062-111">$schema</span><span class="sxs-lookup"><span data-stu-id="64062-111">$schema</span></span>

<span data-ttu-id="64062-112">*Opcional, mas recomendado* &ndash; Sequência</span><span class="sxs-lookup"><span data-stu-id="64062-112">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="64062-113">A URL https://que faz referência ao esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="64062-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="64062-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="64062-114">manifestVersion</span></span>

<span data-ttu-id="64062-115">**Necessárias** &ndash; Sequência</span><span class="sxs-lookup"><span data-stu-id="64062-115">**Required** &ndash; String</span></span>

<span data-ttu-id="64062-116">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="64062-116">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="64062-117">Ele deve ser "1,5".</span><span class="sxs-lookup"><span data-stu-id="64062-117">It should be "1.5".</span></span>

## <a name="version"></a><span data-ttu-id="64062-118">versão</span><span class="sxs-lookup"><span data-stu-id="64062-118">version</span></span>

<span data-ttu-id="64062-119">**Necessárias** &ndash; Sequência</span><span class="sxs-lookup"><span data-stu-id="64062-119">**Required** &ndash; String</span></span>

<span data-ttu-id="64062-120">A versão do aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="64062-120">The version of the specific app.</span></span> <span data-ttu-id="64062-121">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="64062-121">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="64062-122">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="64062-122">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="64062-123">Se este aplicativo foi enviado para o repositório, o novo manifesto terá que ser reenviado e validado novamente.</span><span class="sxs-lookup"><span data-stu-id="64062-123">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="64062-124">Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, após serem aprovados.</span><span class="sxs-lookup"><span data-stu-id="64062-124">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="64062-125">Se as permissões solicitadas pelo aplicativo forem alteradas, os usuários serão solicitados a atualizar e a dar o consentimento novamente para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-125">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="64062-126">Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (principal. Mínima. PATCH).</span><span class="sxs-lookup"><span data-stu-id="64062-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="64062-127">id</span><span class="sxs-lookup"><span data-stu-id="64062-127">id</span></span>

<span data-ttu-id="64062-128">**Necessárias** &ndash; ID do aplicativo da Microsoft</span><span class="sxs-lookup"><span data-stu-id="64062-128">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="64062-129">O identificador exclusivo gerado pela Microsoft para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-129">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="64062-130">Se você tiver registrado um bot por meio da Microsoft bot Framework, ou se o aplicativo Web da sua guia já estiver conectado com a Microsoft, você já deve ter um ID e deve inseri-lo aqui.</span><span class="sxs-lookup"><span data-stu-id="64062-130">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="64062-131">Caso contrário, você deve gerar uma nova ID no portal de registro de aplicativos da Microsoft ([meus aplicativos](https://apps.dev.microsoft.com)), inseri-la aqui e reutilizá-la quando você adicionar um bot. Observação: se você estiver enviando uma atualização para o seu aplicativo existente no AppSource, a ID em seu manifesto não deverá ser modificada.</span><span class="sxs-lookup"><span data-stu-id="64062-131">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you add a bot.Note: If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="packagename"></a><span data-ttu-id="64062-132">Packagenamena</span><span class="sxs-lookup"><span data-stu-id="64062-132">packageName</span></span>

<span data-ttu-id="64062-133">**Necessárias** &ndash; Sequência</span><span class="sxs-lookup"><span data-stu-id="64062-133">**Required** &ndash; String</span></span>

<span data-ttu-id="64062-134">Um identificador exclusivo para esse aplicativo na notação de domínio reverso; por exemplo, com. example. MyApp.</span><span class="sxs-lookup"><span data-stu-id="64062-134">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="64062-135">developer</span><span class="sxs-lookup"><span data-stu-id="64062-135">developer</span></span>

<span data-ttu-id="64062-136">**Required**</span><span class="sxs-lookup"><span data-stu-id="64062-136">**Required**</span></span>

<span data-ttu-id="64062-137">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="64062-137">Specifies information about your company.</span></span> <span data-ttu-id="64062-138">Para aplicativos enviados para o AppSource (anteriormente Office Store), esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="64062-138">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="64062-139">Veja nossas [diretrizes de publicação](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="64062-139">See our [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="64062-140">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-140">Name</span></span>| <span data-ttu-id="64062-141">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-141">Maximum size</span></span> | <span data-ttu-id="64062-142">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-142">Required</span></span> | <span data-ttu-id="64062-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-143">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="64062-144">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-144">32 characters</span></span>|<span data-ttu-id="64062-145">✔</span><span class="sxs-lookup"><span data-stu-id="64062-145">✔</span></span>|<span data-ttu-id="64062-146">O nome de exibição para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="64062-146">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="64062-147">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-147">2048 characters</span></span>|<span data-ttu-id="64062-148">✔</span><span class="sxs-lookup"><span data-stu-id="64062-148">✔</span></span>|<span data-ttu-id="64062-149">A URL do https://para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="64062-149">The https:// URL to the developer's website.</span></span> <span data-ttu-id="64062-150">Este link deve levar os usuários à sua página de aterrissagem específica da empresa ou do produto.</span><span class="sxs-lookup"><span data-stu-id="64062-150">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="64062-151">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-151">2048 characters</span></span>|<span data-ttu-id="64062-152">✔</span><span class="sxs-lookup"><span data-stu-id="64062-152">✔</span></span>|<span data-ttu-id="64062-153">A URL do https://para a política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="64062-153">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="64062-154">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-154">2048 characters</span></span>|<span data-ttu-id="64062-155">✔</span><span class="sxs-lookup"><span data-stu-id="64062-155">✔</span></span>|<span data-ttu-id="64062-156">A URL do https://para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="64062-156">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="64062-157">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-157">10 characters</span></span>| |<span data-ttu-id="64062-158">**Opcional** A ID de rede do parceiro da Microsoft que identifica a organização do parceiro que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-158">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="64062-159">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="64062-159">localizationInfo</span></span>

<span data-ttu-id="64062-160">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="64062-160">**Optional**</span></span>

<span data-ttu-id="64062-161">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="64062-161">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="64062-162">Confira [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="64062-162">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="64062-163">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-163">Name</span></span>| <span data-ttu-id="64062-164">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-164">Maximum size</span></span> | <span data-ttu-id="64062-165">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-165">Required</span></span> | <span data-ttu-id="64062-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-166">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="64062-167">✔</span><span class="sxs-lookup"><span data-stu-id="64062-167">✔</span></span>|<span data-ttu-id="64062-168">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="64062-168">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="64062-169">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="64062-169">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="64062-170">Uma matriz de objetos especificando traduções de idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="64062-170">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="64062-171">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-171">Name</span></span>| <span data-ttu-id="64062-172">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-172">Maximum size</span></span> | <span data-ttu-id="64062-173">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-173">Required</span></span> | <span data-ttu-id="64062-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-174">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="64062-175">✔</span><span class="sxs-lookup"><span data-stu-id="64062-175">✔</span></span>|<span data-ttu-id="64062-176">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="64062-176">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="64062-177">✔</span><span class="sxs-lookup"><span data-stu-id="64062-177">✔</span></span>|<span data-ttu-id="64062-178">Um caminho de arquivo relativo para um arquivo. JSON que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="64062-178">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="64062-179">nome</span><span class="sxs-lookup"><span data-stu-id="64062-179">name</span></span>

<span data-ttu-id="64062-180">**Required**</span><span class="sxs-lookup"><span data-stu-id="64062-180">**Required**</span></span>

<span data-ttu-id="64062-181">O nome da sua experiência de aplicativo, exibido aos usuários na experiência do teams.</span><span class="sxs-lookup"><span data-stu-id="64062-181">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="64062-182">Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="64062-182">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="64062-183">Os valores de `short` e `full` não devem ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="64062-183">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="64062-184">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-184">Name</span></span>| <span data-ttu-id="64062-185">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-185">Maximum size</span></span> | <span data-ttu-id="64062-186">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-186">Required</span></span> | <span data-ttu-id="64062-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-187">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="64062-188">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-188">30 characters</span></span>|<span data-ttu-id="64062-189">✔</span><span class="sxs-lookup"><span data-stu-id="64062-189">✔</span></span>|<span data-ttu-id="64062-190">O nome de exibição curto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-190">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="64062-191">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-191">100 characters</span></span>||<span data-ttu-id="64062-192">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="64062-192">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="64062-193">description</span><span class="sxs-lookup"><span data-stu-id="64062-193">description</span></span>

<span data-ttu-id="64062-194">**Required**</span><span class="sxs-lookup"><span data-stu-id="64062-194">**Required**</span></span>

<span data-ttu-id="64062-195">Descreve seu aplicativo para os usuários.</span><span class="sxs-lookup"><span data-stu-id="64062-195">Describes your app to users.</span></span> <span data-ttu-id="64062-196">Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="64062-196">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="64062-197">Certifique-se de que sua descrição descreve precisamente sua experiência e fornece informações para ajudar os clientes potenciais a entender o que a sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="64062-197">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="64062-198">Você também deve observar, na descrição completa, se for necessário usar uma conta externa.</span><span class="sxs-lookup"><span data-stu-id="64062-198">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="64062-199">Os valores de `short` e `full` não devem ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="64062-199">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="64062-200">Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir nenhum outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-200">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="64062-201">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-201">Name</span></span>| <span data-ttu-id="64062-202">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-202">Maximum size</span></span> | <span data-ttu-id="64062-203">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-203">Required</span></span> | <span data-ttu-id="64062-204">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-204">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="64062-205">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-205">80 characters</span></span>|<span data-ttu-id="64062-206">✔</span><span class="sxs-lookup"><span data-stu-id="64062-206">✔</span></span>|<span data-ttu-id="64062-207">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="64062-207">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="64062-208">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-208">4000 characters</span></span>|<span data-ttu-id="64062-209">✔</span><span class="sxs-lookup"><span data-stu-id="64062-209">✔</span></span>|<span data-ttu-id="64062-210">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-210">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="64062-211">ícones</span><span class="sxs-lookup"><span data-stu-id="64062-211">icons</span></span>

<span data-ttu-id="64062-212">**Required**</span><span class="sxs-lookup"><span data-stu-id="64062-212">**Required**</span></span>

<span data-ttu-id="64062-213">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="64062-213">Icons used within the Teams app.</span></span> <span data-ttu-id="64062-214">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="64062-214">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="64062-215">Consulte [ícones](~/concepts/build-and-test/apps-package.md#icons) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="64062-215">See [Icons](~/concepts/build-and-test/apps-package.md#icons) for more information.</span></span>

|<span data-ttu-id="64062-216">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-216">Name</span></span>| <span data-ttu-id="64062-217">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-217">Maximum size</span></span> | <span data-ttu-id="64062-218">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-218">Required</span></span> | <span data-ttu-id="64062-219">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-219">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="64062-220">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-220">2048 characters</span></span>|<span data-ttu-id="64062-221">✔</span><span class="sxs-lookup"><span data-stu-id="64062-221">✔</span></span>|<span data-ttu-id="64062-222">Um caminho de arquivo relativo para um ícone de estrutura de tópicos de PNG de 32 x 32 transparente.</span><span class="sxs-lookup"><span data-stu-id="64062-222">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="64062-223">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-223">2048 characters</span></span>|<span data-ttu-id="64062-224">✔</span><span class="sxs-lookup"><span data-stu-id="64062-224">✔</span></span>|<span data-ttu-id="64062-225">Um caminho de arquivo relativo para um ícone de 192x192 do PNG completo.</span><span class="sxs-lookup"><span data-stu-id="64062-225">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="64062-226">accentColor</span><span class="sxs-lookup"><span data-stu-id="64062-226">accentColor</span></span>

<span data-ttu-id="64062-227">**Necessárias** &ndash; Sequência</span><span class="sxs-lookup"><span data-stu-id="64062-227">**Required** &ndash; String</span></span>

<span data-ttu-id="64062-228">Uma cor a ser usada em conjunto com e como um plano de fundo para seus ícones de estrutura de tópicos.</span><span class="sxs-lookup"><span data-stu-id="64062-228">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="64062-229">O valor deve ser um código de cor HTML válido começando com ' # ', por exemplo `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="64062-229">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="64062-230">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="64062-230">configurableTabs</span></span>

<span data-ttu-id="64062-231">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="64062-231">**Optional**</span></span>

<span data-ttu-id="64062-232">Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração adicional antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="64062-232">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="64062-233">Guias configuráveis têm suporte apenas no escopo Teams, e atualmente só há suporte para uma guia por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-233">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="64062-234">O objeto é uma matriz com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="64062-234">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="64062-235">Esse bloco só é necessário para soluções que oferecem uma solução de guia de canal configurável.</span><span class="sxs-lookup"><span data-stu-id="64062-235">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="64062-236">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-236">Name</span></span>| <span data-ttu-id="64062-237">Tipo</span><span class="sxs-lookup"><span data-stu-id="64062-237">Type</span></span>| <span data-ttu-id="64062-238">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-238">Maximum size</span></span> | <span data-ttu-id="64062-239">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-239">Required</span></span> | <span data-ttu-id="64062-240">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-240">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="64062-241">String</span><span class="sxs-lookup"><span data-stu-id="64062-241">String</span></span>|<span data-ttu-id="64062-242">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-242">2048 characters</span></span>|<span data-ttu-id="64062-243">✔</span><span class="sxs-lookup"><span data-stu-id="64062-243">✔</span></span>|<span data-ttu-id="64062-244">A URL do https://a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="64062-244">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="64062-245">Boolean</span><span class="sxs-lookup"><span data-stu-id="64062-245">Boolean</span></span>|||<span data-ttu-id="64062-246">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="64062-246">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="64062-247">Será`true`</span><span class="sxs-lookup"><span data-stu-id="64062-247">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="64062-248">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="64062-248">Array of enum</span></span>|<span data-ttu-id="64062-249">1 </span><span class="sxs-lookup"><span data-stu-id="64062-249">1</span></span>|<span data-ttu-id="64062-250">✔</span><span class="sxs-lookup"><span data-stu-id="64062-250">✔</span></span>|<span data-ttu-id="64062-251">No momento, as guias configuráveis só dão suporte a `team` e os `groupchat` escopos.</span><span class="sxs-lookup"><span data-stu-id="64062-251">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="64062-252">String</span><span class="sxs-lookup"><span data-stu-id="64062-252">String</span></span>|<span data-ttu-id="64062-253">2048</span><span class="sxs-lookup"><span data-stu-id="64062-253">2048</span></span>||<span data-ttu-id="64062-254">Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="64062-254">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="64062-255">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="64062-255">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="64062-256">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="64062-256">Array of enum</span></span>|<span data-ttu-id="64062-257">1 </span><span class="sxs-lookup"><span data-stu-id="64062-257">1</span></span>||<span data-ttu-id="64062-258">Define como sua guia será disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="64062-258">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="64062-259">Opções são `sharePointFullPage` e`sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="64062-259">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="64062-260">staticTabs</span><span class="sxs-lookup"><span data-stu-id="64062-260">staticTabs</span></span>

<span data-ttu-id="64062-261">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="64062-261">**Optional**</span></span>

<span data-ttu-id="64062-262">Define um conjunto de guias que podem ser "fixadas" por padrão, sem o usuário adicioná-las manualmente.</span><span class="sxs-lookup"><span data-stu-id="64062-262">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="64062-263">As guias estáticas declaradas no `personal` escopo são sempre fixadas para a experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-263">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="64062-264">Guias static declaradas no `team` escopo não são suportadas atualmente.</span><span class="sxs-lookup"><span data-stu-id="64062-264">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="64062-265">O objeto é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="64062-265">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="64062-266">Esse bloco é necessário somente para soluções que oferecem uma solução de guia estática.</span><span class="sxs-lookup"><span data-stu-id="64062-266">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="64062-267">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-267">Name</span></span>| <span data-ttu-id="64062-268">Tipo</span><span class="sxs-lookup"><span data-stu-id="64062-268">Type</span></span>| <span data-ttu-id="64062-269">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-269">Maximum size</span></span> | <span data-ttu-id="64062-270">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-270">Required</span></span> | <span data-ttu-id="64062-271">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-271">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="64062-272">String</span><span class="sxs-lookup"><span data-stu-id="64062-272">String</span></span>|<span data-ttu-id="64062-273">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-273">64 characters</span></span>|<span data-ttu-id="64062-274">✔</span><span class="sxs-lookup"><span data-stu-id="64062-274">✔</span></span>|<span data-ttu-id="64062-275">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="64062-275">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="64062-276">String</span><span class="sxs-lookup"><span data-stu-id="64062-276">String</span></span>|<span data-ttu-id="64062-277">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-277">128 characters</span></span>|<span data-ttu-id="64062-278">✔</span><span class="sxs-lookup"><span data-stu-id="64062-278">✔</span></span>|<span data-ttu-id="64062-279">O nome de exibição da guia na interface de canal.</span><span class="sxs-lookup"><span data-stu-id="64062-279">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="64062-280">String</span><span class="sxs-lookup"><span data-stu-id="64062-280">String</span></span>|<span data-ttu-id="64062-281">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-281">2048 characters</span></span>|<span data-ttu-id="64062-282">✔</span><span class="sxs-lookup"><span data-stu-id="64062-282">✔</span></span>|<span data-ttu-id="64062-283">A URL https://que aponta para a interface do usuário da entidade a ser exibida na tela do teams.</span><span class="sxs-lookup"><span data-stu-id="64062-283">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="64062-284">String</span><span class="sxs-lookup"><span data-stu-id="64062-284">String</span></span>|<span data-ttu-id="64062-285">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-285">2048 characters</span></span>||<span data-ttu-id="64062-286">A URL do https://para apontar para o modo de exibição de um usuário em um navegador.</span><span class="sxs-lookup"><span data-stu-id="64062-286">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="64062-287">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="64062-287">Array of enum</span></span>|<span data-ttu-id="64062-288">1 </span><span class="sxs-lookup"><span data-stu-id="64062-288">1</span></span>|<span data-ttu-id="64062-289">✔</span><span class="sxs-lookup"><span data-stu-id="64062-289">✔</span></span>|<span data-ttu-id="64062-290">Atualmente, as guias estáticas oferecem suporte somente ao `personal` escopo, o que significa que ela pode ser provisionada somente como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="64062-290">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

> [!NOTE]
> <span data-ttu-id="64062-291">Se suas guias exigirem informações dependentes de contexto para exibir conteúdo relevante ou para iniciar um fluxo de autenticação, *consulte* [obter contexto para a guia do Microsoft Teams](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="64062-291">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="64062-292">robôs</span><span class="sxs-lookup"><span data-stu-id="64062-292">bots</span></span>

<span data-ttu-id="64062-293">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="64062-293">**Optional**</span></span>

<span data-ttu-id="64062-294">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="64062-294">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="64062-295">O objeto é uma matriz (máximo de apenas 1 elemento &mdash; atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="64062-295">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="64062-296">Esse bloco é necessário somente para soluções que oferecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="64062-296">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="64062-297">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-297">Name</span></span>| <span data-ttu-id="64062-298">Tipo</span><span class="sxs-lookup"><span data-stu-id="64062-298">Type</span></span>| <span data-ttu-id="64062-299">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-299">Maximum size</span></span> | <span data-ttu-id="64062-300">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-300">Required</span></span> | <span data-ttu-id="64062-301">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-301">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="64062-302">String</span><span class="sxs-lookup"><span data-stu-id="64062-302">String</span></span>|<span data-ttu-id="64062-303">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-303">64 characters</span></span>|<span data-ttu-id="64062-304">✔</span><span class="sxs-lookup"><span data-stu-id="64062-304">✔</span></span>|<span data-ttu-id="64062-305">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="64062-305">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="64062-306">Isso pode ser o mesmo que a ID de [aplicativo](#id)geral.</span><span class="sxs-lookup"><span data-stu-id="64062-306">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="64062-307">Boolean</span><span class="sxs-lookup"><span data-stu-id="64062-307">Boolean</span></span>|||<span data-ttu-id="64062-308">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="64062-308">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="64062-309">Será`false`</span><span class="sxs-lookup"><span data-stu-id="64062-309">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="64062-310">Boolean</span><span class="sxs-lookup"><span data-stu-id="64062-310">Boolean</span></span>|||<span data-ttu-id="64062-311">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="64062-311">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="64062-312">Será`false`</span><span class="sxs-lookup"><span data-stu-id="64062-312">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="64062-313">Boolean</span><span class="sxs-lookup"><span data-stu-id="64062-313">Boolean</span></span>|||<span data-ttu-id="64062-314">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="64062-314">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="64062-315">Será`false`</span><span class="sxs-lookup"><span data-stu-id="64062-315">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="64062-316">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="64062-316">Array of enum</span></span>|<span data-ttu-id="64062-317">3D</span><span class="sxs-lookup"><span data-stu-id="64062-317">3</span></span>|<span data-ttu-id="64062-318">✔</span><span class="sxs-lookup"><span data-stu-id="64062-318">✔</span></span>|<span data-ttu-id="64062-319">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="64062-319">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="64062-320">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="64062-320">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="64062-321">bots. commandLists</span><span class="sxs-lookup"><span data-stu-id="64062-321">bots.commandLists</span></span>

<span data-ttu-id="64062-322">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="64062-322">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="64062-323">O objeto é uma matriz (máximo de dois elementos) com todos os elementos do tipo `object` ; você deve definir uma lista de comandos separada para cada escopo que seu bot suporta.</span><span class="sxs-lookup"><span data-stu-id="64062-323">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="64062-324">Consulte [menus de bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="64062-324">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="64062-325">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-325">Name</span></span>| <span data-ttu-id="64062-326">Tipo</span><span class="sxs-lookup"><span data-stu-id="64062-326">Type</span></span>| <span data-ttu-id="64062-327">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-327">Maximum size</span></span> | <span data-ttu-id="64062-328">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-328">Required</span></span> | <span data-ttu-id="64062-329">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-329">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="64062-330">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="64062-330">array of enum</span></span>|<span data-ttu-id="64062-331">3D</span><span class="sxs-lookup"><span data-stu-id="64062-331">3</span></span>|<span data-ttu-id="64062-332">✔</span><span class="sxs-lookup"><span data-stu-id="64062-332">✔</span></span>|<span data-ttu-id="64062-333">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="64062-333">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="64062-334">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="64062-334">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="64062-335">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="64062-335">array of objects</span></span>|<span data-ttu-id="64062-336">10 </span><span class="sxs-lookup"><span data-stu-id="64062-336">10</span></span>|<span data-ttu-id="64062-337">✔</span><span class="sxs-lookup"><span data-stu-id="64062-337">✔</span></span>|<span data-ttu-id="64062-338">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="64062-338">An array of commands the bot supports:</span></span><br><span data-ttu-id="64062-339">`title`: o nome do comando bot (cadeia, 32)</span><span class="sxs-lookup"><span data-stu-id="64062-339">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="64062-340">`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)</span><span class="sxs-lookup"><span data-stu-id="64062-340">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

## <a name="connectors"></a><span data-ttu-id="64062-341">conectores</span><span class="sxs-lookup"><span data-stu-id="64062-341">connectors</span></span>

<span data-ttu-id="64062-342">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="64062-342">**Optional**</span></span>

<span data-ttu-id="64062-343">O `connectors` bloco define um conector do Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-343">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="64062-344">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="64062-344">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="64062-345">Esse bloco é necessário somente para soluções que fornecem um conector.</span><span class="sxs-lookup"><span data-stu-id="64062-345">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="64062-346">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-346">Name</span></span>| <span data-ttu-id="64062-347">Tipo</span><span class="sxs-lookup"><span data-stu-id="64062-347">Type</span></span>| <span data-ttu-id="64062-348">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-348">Maximum size</span></span> | <span data-ttu-id="64062-349">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-349">Required</span></span> | <span data-ttu-id="64062-350">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-350">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="64062-351">String</span><span class="sxs-lookup"><span data-stu-id="64062-351">String</span></span>|<span data-ttu-id="64062-352">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-352">2048 characters</span></span>|<span data-ttu-id="64062-353">✔</span><span class="sxs-lookup"><span data-stu-id="64062-353">✔</span></span>|<span data-ttu-id="64062-354">A URL do https://a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="64062-354">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="64062-355">String</span><span class="sxs-lookup"><span data-stu-id="64062-355">String</span></span>|<span data-ttu-id="64062-356">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-356">64 characters</span></span>|<span data-ttu-id="64062-357">✔</span><span class="sxs-lookup"><span data-stu-id="64062-357">✔</span></span>|<span data-ttu-id="64062-358">Um identificador exclusivo para o conector que corresponde à sua ID no [painel do desenvolvedor de conectores](https://aka.ms/connectorsdashboard).</span><span class="sxs-lookup"><span data-stu-id="64062-358">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="64062-359">Matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="64062-359">Array of enum</span></span>|<span data-ttu-id="64062-360">1 </span><span class="sxs-lookup"><span data-stu-id="64062-360">1</span></span>|<span data-ttu-id="64062-361">✔</span><span class="sxs-lookup"><span data-stu-id="64062-361">✔</span></span>|<span data-ttu-id="64062-362">Especifica se o conector oferece uma experiência no contexto de um canal em uma `team` ou uma experiência com escopo para um usuário individual ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="64062-362">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="64062-363">Atualmente, só `team` há suporte para o escopo.</span><span class="sxs-lookup"><span data-stu-id="64062-363">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="64062-364">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="64062-364">composeExtensions</span></span>

<span data-ttu-id="64062-365">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="64062-365">**Optional**</span></span>

<span data-ttu-id="64062-366">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-366">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="64062-367">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem a funcionar.</span><span class="sxs-lookup"><span data-stu-id="64062-367">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="64062-368">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="64062-368">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="64062-369">Esse bloco é necessário somente para soluções que forneçam uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="64062-369">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="64062-370">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-370">Name</span></span>| <span data-ttu-id="64062-371">Tipo</span><span class="sxs-lookup"><span data-stu-id="64062-371">Type</span></span> | <span data-ttu-id="64062-372">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-372">Maximum Size</span></span> | <span data-ttu-id="64062-373">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-373">Required</span></span> | <span data-ttu-id="64062-374">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-374">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="64062-375">String</span><span class="sxs-lookup"><span data-stu-id="64062-375">String</span></span>|<span data-ttu-id="64062-376">64</span><span class="sxs-lookup"><span data-stu-id="64062-376">64</span></span>|<span data-ttu-id="64062-377">✔</span><span class="sxs-lookup"><span data-stu-id="64062-377">✔</span></span>|<span data-ttu-id="64062-378">A ID exclusiva do aplicativo da Microsoft para o bot que faz a extensão do sistema de mensagens, conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="64062-378">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="64062-379">Isso pode ser o mesmo que a ID de aplicativo geral.</span><span class="sxs-lookup"><span data-stu-id="64062-379">This may well be the same as the overall App ID.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="64062-380">Boolean</span><span class="sxs-lookup"><span data-stu-id="64062-380">Boolean</span></span>|||<span data-ttu-id="64062-381">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="64062-381">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="64062-382">O padrão é `false` .</span><span class="sxs-lookup"><span data-stu-id="64062-382">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="64062-383">Matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="64062-383">Array of object</span></span>|<span data-ttu-id="64062-384">10 </span><span class="sxs-lookup"><span data-stu-id="64062-384">10</span></span>|<span data-ttu-id="64062-385">✔</span><span class="sxs-lookup"><span data-stu-id="64062-385">✔</span></span>|<span data-ttu-id="64062-386">Matriz de comandos que a extensão de mensagens oferece suporte</span><span class="sxs-lookup"><span data-stu-id="64062-386">Array of commands the messaging extension supports</span></span>|
|`messageHandlers`|<span data-ttu-id="64062-387">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="64062-387">Array of Objects</span></span>|<span data-ttu-id="64062-388">5 </span><span class="sxs-lookup"><span data-stu-id="64062-388">5</span></span>||<span data-ttu-id="64062-389">Uma lista de manipuladores que permitem que os aplicativos sejam chamados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="64062-389">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="64062-390">Os domínios também devem ser listados no`validDomains`</span><span class="sxs-lookup"><span data-stu-id="64062-390">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="64062-391">String</span><span class="sxs-lookup"><span data-stu-id="64062-391">String</span></span>|||<span data-ttu-id="64062-392">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="64062-392">The type of message handler.</span></span> <span data-ttu-id="64062-393">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="64062-393">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="64062-394">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-394">Array of Strings</span></span>|||<span data-ttu-id="64062-395">Matriz de domínios para o qual o manipulador de mensagens de link pode se registrar.</span><span class="sxs-lookup"><span data-stu-id="64062-395">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="64062-396">composeExtensions. Commands</span><span class="sxs-lookup"><span data-stu-id="64062-396">composeExtensions.commands</span></span>

<span data-ttu-id="64062-397">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="64062-397">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="64062-398">Cada comando aparece no Microsoft Teams como uma possível interação do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="64062-398">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="64062-399">Há um máximo de 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="64062-399">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="64062-400">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="64062-400">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="64062-401">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-401">Name</span></span>| <span data-ttu-id="64062-402">Tipo</span><span class="sxs-lookup"><span data-stu-id="64062-402">Type</span></span>| <span data-ttu-id="64062-403">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-403">Maximum size</span></span> | <span data-ttu-id="64062-404">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-404">Required</span></span> | <span data-ttu-id="64062-405">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-405">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="64062-406">String</span><span class="sxs-lookup"><span data-stu-id="64062-406">String</span></span>|<span data-ttu-id="64062-407">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-407">64 characters</span></span>|<span data-ttu-id="64062-408">✔</span><span class="sxs-lookup"><span data-stu-id="64062-408">✔</span></span>|<span data-ttu-id="64062-409">A ID do comando</span><span class="sxs-lookup"><span data-stu-id="64062-409">The ID for the command</span></span>|
|`type`|<span data-ttu-id="64062-410">String</span><span class="sxs-lookup"><span data-stu-id="64062-410">String</span></span>|<span data-ttu-id="64062-411">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-411">64 characters</span></span>||<span data-ttu-id="64062-412">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="64062-412">Type of the command.</span></span> <span data-ttu-id="64062-413">Um `query` ou `action` .</span><span class="sxs-lookup"><span data-stu-id="64062-413">One of `query` or `action`.</span></span> <span data-ttu-id="64062-414">Será`query`</span><span class="sxs-lookup"><span data-stu-id="64062-414">Default: `query`</span></span>|
|`title`|<span data-ttu-id="64062-415">String</span><span class="sxs-lookup"><span data-stu-id="64062-415">String</span></span>|<span data-ttu-id="64062-416">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-416">32 characters</span></span>|<span data-ttu-id="64062-417">✔</span><span class="sxs-lookup"><span data-stu-id="64062-417">✔</span></span>|<span data-ttu-id="64062-418">O nome do comando amigável</span><span class="sxs-lookup"><span data-stu-id="64062-418">The user-friendly command name</span></span>|
|`description`|<span data-ttu-id="64062-419">String</span><span class="sxs-lookup"><span data-stu-id="64062-419">String</span></span>|<span data-ttu-id="64062-420">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-420">128 characters</span></span>||<span data-ttu-id="64062-421">A descrição que aparece para os usuários para indicar a finalidade desse comando</span><span class="sxs-lookup"><span data-stu-id="64062-421">The description that appears to users to indicate the purpose of this command</span></span>|
|`initialRun`|<span data-ttu-id="64062-422">Boolean</span><span class="sxs-lookup"><span data-stu-id="64062-422">Boolean</span></span>|||<span data-ttu-id="64062-423">Um valor Boolean que indica se o comando deve ser executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="64062-423">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="64062-424">Será`false`</span><span class="sxs-lookup"><span data-stu-id="64062-424">Default: `false`</span></span>|
|`context`|<span data-ttu-id="64062-425">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-425">Array of Strings</span></span>|<span data-ttu-id="64062-426">3D</span><span class="sxs-lookup"><span data-stu-id="64062-426">3</span></span>||<span data-ttu-id="64062-427">Define onde a extensão de mensagem pode ser chamada.</span><span class="sxs-lookup"><span data-stu-id="64062-427">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="64062-428">Qualquer combinação de `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="64062-428">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="64062-429">O padrão é`["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="64062-429">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="64062-430">Boolean</span><span class="sxs-lookup"><span data-stu-id="64062-430">Boolean</span></span>|||<span data-ttu-id="64062-431">Um valor Boolean que indica se deve buscar o módulo de tarefa dinamicamente</span><span class="sxs-lookup"><span data-stu-id="64062-431">A boolean value that indicates if it should fetch the task module dynamically</span></span>|
|`taskInfo`|<span data-ttu-id="64062-432">Objeto</span><span class="sxs-lookup"><span data-stu-id="64062-432">Object</span></span>|||<span data-ttu-id="64062-433">Especificar o módulo de tarefa a ser pré-carregar ao usar um comando de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="64062-433">Specify the task module to preload when using a messaging extension command</span></span>|
|`taskInfo.title`|<span data-ttu-id="64062-434">String</span><span class="sxs-lookup"><span data-stu-id="64062-434">String</span></span>|<span data-ttu-id="64062-435">64</span><span class="sxs-lookup"><span data-stu-id="64062-435">64</span></span>||<span data-ttu-id="64062-436">Título inicial da caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="64062-436">Initial dialog title</span></span>|
|`taskInfo.width`|<span data-ttu-id="64062-437">String</span><span class="sxs-lookup"><span data-stu-id="64062-437">String</span></span>|||<span data-ttu-id="64062-438">Largura da caixa de diálogo: um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '</span><span class="sxs-lookup"><span data-stu-id="64062-438">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.height`|<span data-ttu-id="64062-439">String</span><span class="sxs-lookup"><span data-stu-id="64062-439">String</span></span>|||<span data-ttu-id="64062-440">Altura da caixa de diálogo-um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '</span><span class="sxs-lookup"><span data-stu-id="64062-440">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.url`|<span data-ttu-id="64062-441">String</span><span class="sxs-lookup"><span data-stu-id="64062-441">String</span></span>|||<span data-ttu-id="64062-442">URL do WebView inicial</span><span class="sxs-lookup"><span data-stu-id="64062-442">Initial webview URL</span></span>|
|`parameters`|<span data-ttu-id="64062-443">Matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="64062-443">Array of object</span></span>|<span data-ttu-id="64062-444">5 </span><span class="sxs-lookup"><span data-stu-id="64062-444">5</span></span>|<span data-ttu-id="64062-445">✔</span><span class="sxs-lookup"><span data-stu-id="64062-445">✔</span></span>|<span data-ttu-id="64062-446">A lista de parâmetros que o comando utiliza.</span><span class="sxs-lookup"><span data-stu-id="64062-446">The list of parameters the command takes.</span></span> <span data-ttu-id="64062-447">Mínimo: 1; máximo: 5</span><span class="sxs-lookup"><span data-stu-id="64062-447">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="64062-448">String</span><span class="sxs-lookup"><span data-stu-id="64062-448">String</span></span>|<span data-ttu-id="64062-449">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-449">64 characters</span></span>|<span data-ttu-id="64062-450">✔</span><span class="sxs-lookup"><span data-stu-id="64062-450">✔</span></span>|<span data-ttu-id="64062-451">O nome do parâmetro conforme ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="64062-451">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="64062-452">Isso é incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="64062-452">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="64062-453">String</span><span class="sxs-lookup"><span data-stu-id="64062-453">String</span></span>|<span data-ttu-id="64062-454">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-454">32 characters</span></span>|<span data-ttu-id="64062-455">✔</span><span class="sxs-lookup"><span data-stu-id="64062-455">✔</span></span>|<span data-ttu-id="64062-456">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="64062-456">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="64062-457">String</span><span class="sxs-lookup"><span data-stu-id="64062-457">String</span></span>|<span data-ttu-id="64062-458">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-458">128 characters</span></span>||<span data-ttu-id="64062-459">Cadeia de caracteres amigável que descreve a finalidade deste parâmetro.</span><span class="sxs-lookup"><span data-stu-id="64062-459">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="64062-460">String</span><span class="sxs-lookup"><span data-stu-id="64062-460">String</span></span>|<span data-ttu-id="64062-461">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-461">128 characters</span></span>||<span data-ttu-id="64062-462">Define o tipo de controle exibido em um módulo de tarefas para o `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="64062-462">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="64062-463">Um de `text` , `textarea` , `number` , `date` , `time` , `toggle` ,`choiceset`</span><span class="sxs-lookup"><span data-stu-id="64062-463">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`</span></span>|
|`parameter.choices`|<span data-ttu-id="64062-464">Matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="64062-464">Array of Objects</span></span>|<span data-ttu-id="64062-465">10 </span><span class="sxs-lookup"><span data-stu-id="64062-465">10</span></span>||<span data-ttu-id="64062-466">As opções de escolha para o `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="64062-466">The choice options for the `choiceset`.</span></span> <span data-ttu-id="64062-467">Use somente quando o `parameter.inputType` é`choiceset`</span><span class="sxs-lookup"><span data-stu-id="64062-467">Use only when `parameter.inputType` is `choiceset`</span></span>|
|`parameter.choices.title`|<span data-ttu-id="64062-468">String</span><span class="sxs-lookup"><span data-stu-id="64062-468">String</span></span>|<span data-ttu-id="64062-469">128</span><span class="sxs-lookup"><span data-stu-id="64062-469">128</span></span>||<span data-ttu-id="64062-470">Título da opção</span><span class="sxs-lookup"><span data-stu-id="64062-470">Title of the choice</span></span>|
|`parameter.choices.value`|<span data-ttu-id="64062-471">String</span><span class="sxs-lookup"><span data-stu-id="64062-471">String</span></span>|<span data-ttu-id="64062-472">512</span><span class="sxs-lookup"><span data-stu-id="64062-472">512</span></span>||<span data-ttu-id="64062-473">Valor da opção</span><span class="sxs-lookup"><span data-stu-id="64062-473">Value of the choice</span></span>|

## <a name="permissions"></a><span data-ttu-id="64062-474">permissões</span><span class="sxs-lookup"><span data-stu-id="64062-474">permissions</span></span>

<span data-ttu-id="64062-475">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="64062-475">**Optional**</span></span>

<span data-ttu-id="64062-476">Uma matriz `string` que especifica quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão será executada.</span><span class="sxs-lookup"><span data-stu-id="64062-476">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="64062-477">As opções a seguir são não exclusivas:</span><span class="sxs-lookup"><span data-stu-id="64062-477">The following options are non-exclusive:</span></span>

* <span data-ttu-id="64062-478">`identity`&emsp;Requer informações de identidade do usuário</span><span class="sxs-lookup"><span data-stu-id="64062-478">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="64062-479">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas para membros da equipe</span><span class="sxs-lookup"><span data-stu-id="64062-479">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="64062-480">A alteração dessas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="64062-480">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span> <span data-ttu-id="64062-481">Veja [atualização do seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="64062-481">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="64062-482">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="64062-482">devicePermissions</span></span>

<span data-ttu-id="64062-483">**Opcional** Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-483">**Optional** Array of Strings</span></span>

<span data-ttu-id="64062-484">Especifica os recursos nativos no dispositivo de um usuário para o qual seu aplicativo pode solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="64062-484">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="64062-485">As opções são:</span><span class="sxs-lookup"><span data-stu-id="64062-485">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="64062-486">validDomains</span><span class="sxs-lookup"><span data-stu-id="64062-486">validDomains</span></span>

<span data-ttu-id="64062-487">**Opcional**, exceto quando **necessário** , onde observado</span><span class="sxs-lookup"><span data-stu-id="64062-487">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="64062-488">Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="64062-488">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="64062-489">As listagens de domínio podem incluir curingas, por exemplo `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="64062-489">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="64062-490">Isso corresponde exatamente a um segmento do domínio; Se você precisar coincidir `a.b.example.com` e usar `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="64062-490">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="64062-491">Se a configuração de sua guia ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além daquele usado para configuração de guia, esse domínio deverá ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="64062-491">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="64062-492">No entanto, **não** é necessário incluir os domínios de provedores de identidade que você deseja suportar no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-492">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="64062-493">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve incluir o accounts.google.com no `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="64062-493">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="64062-494">Aplicativos do teams que exigem suas próprias URLs do SharePoint para funcionar bem, podem incluir "{teamsitedomain}" em sua lista de domínios válida.</span><span class="sxs-lookup"><span data-stu-id="64062-494">Teams apps that require their own sharepoint URLs to function well, may include "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64062-495">Não adicione domínios que estejam fora do seu controle, seja diretamente ou via curingas.</span><span class="sxs-lookup"><span data-stu-id="64062-495">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="64062-496">Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="64062-496">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="64062-497">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="64062-497">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="64062-498">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="64062-498">webApplicationInfo</span></span>

<span data-ttu-id="64062-499">**Opcional**</span><span class="sxs-lookup"><span data-stu-id="64062-499">**Optional**</span></span>

<span data-ttu-id="64062-500">Especifique a ID do aplicativo AAD e as informações do gráfico para ajudar os usuários a entrarem diretamente no aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="64062-500">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="64062-501">Nome</span><span class="sxs-lookup"><span data-stu-id="64062-501">Name</span></span>| <span data-ttu-id="64062-502">Tipo</span><span class="sxs-lookup"><span data-stu-id="64062-502">Type</span></span>| <span data-ttu-id="64062-503">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="64062-503">Maximum size</span></span> | <span data-ttu-id="64062-504">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="64062-504">Required</span></span> | <span data-ttu-id="64062-505">Descrição</span><span class="sxs-lookup"><span data-stu-id="64062-505">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="64062-506">String</span><span class="sxs-lookup"><span data-stu-id="64062-506">String</span></span>|<span data-ttu-id="64062-507">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-507">36 characters</span></span>|<span data-ttu-id="64062-508">✔</span><span class="sxs-lookup"><span data-stu-id="64062-508">✔</span></span>|<span data-ttu-id="64062-509">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64062-509">AAD application id of the app.</span></span> <span data-ttu-id="64062-510">Esta ID deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="64062-510">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="64062-511">String</span><span class="sxs-lookup"><span data-stu-id="64062-511">String</span></span>|<span data-ttu-id="64062-512">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="64062-512">2048 characters</span></span>|<span data-ttu-id="64062-513">✔</span><span class="sxs-lookup"><span data-stu-id="64062-513">✔</span></span>|<span data-ttu-id="64062-514">URL de recurso do aplicativo para aquisição de token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="64062-514">Resource url of app for acquiring auth token for SSO.</span></span>|
