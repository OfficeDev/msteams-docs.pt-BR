---
title: Referência de esquema de manifesto
description: Descreve o esquema de manifesto do Microsoft Teams
ms.topic: reference
keywords: esquema de manifesto do teams
author: laujan
ms.author: lajanuar
ms.openlocfilehash: 8fff56d229cc137df8356b06214893dc984396a0
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014604"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="02aea-104">Referência: esquema de manifesto para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="02aea-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="02aea-105">O manifesto do Microsoft Teams descreve como o aplicativo se integra ao produto Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="02aea-105">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="02aea-106">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="02aea-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="02aea-107">As versões anteriores 1.0-1.4 também têm suporte (usando "v1.x" na URL).</span><span class="sxs-lookup"><span data-stu-id="02aea-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="02aea-108">O exemplo de esquema a seguir mostra todas as opções de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="02aea-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="02aea-109">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="02aea-109">Sample full manifest</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.8",
  "version": "1.0.0",
  "id": "%MICROSOFT-APP-ID%",
  "packageName": "com.example.myapp",
  "localizationInfo": {
    "defaultLanguageTag": "en-us",
    "additionalLanguages": [
      {
        "languageTag": "es-es",
        "file": "en-us.json"
      }
    ]
  },
  "developer": {
    "name": "Publisher Name",
    "websiteUrl": "https://website.com/",
    "privacyUrl": "https://website.com/privacy",
    "termsOfUseUrl": "https://website.com/app-tos",
    "mpnId": "1234567890"
  },
  "name": {
    "short": "Name of your app (<=30 chars)",
    "full": "Full name of app, if longer than 30 characters (<=100 chars)"
  },
  "description": {
    "short": "Short description of your app (<= 80 chars)",
    "full": "Full description of your app (<= 4000 chars)"
  },
  "icons": {
    "outline": "A relative path to a transparent .png icon — 32px X 32px",
    "color": "A relative path to a full color .png icon — 192px X 192px"
  },
  "accentColor": "A valid HTML color code.",
  "configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "scopes": [
        "team",
        "groupchat"
      ],
      "canUpdateConfiguration": true,
      "context":[
        "channelTab",
        "privateChatTab",
        "meetingChatTab",
        "meetingDetailsTab",
        "meetingSidePanel",
        "meetingStage"
      ],
      "sharePointPreviewImage": "Relative path to a tab preview image for use in SharePoint — 1024px X 768",
      "supportedSharePointHosts": [
         "sharePointFullPage",
         "sharePointWebPart"
      ]
    }
  ],
  "staticTabs": [
    {
      "entityId": "unique Id for the page entity",
      "scopes": [
        "personal"
      ],
      "context":[
        "personalTab",
        "channelTab"
        ],
      "name": "Display name of tab",
      "contentUrl": "https://contoso.com/content (displayed in Teams canvas)",
      "websiteUrl": "https://contoso.com/content (displayed in web browser)",
       "searchUrl":  "https://contoso.com/content (displayed in web browser)"
    }
  ],
  "bots": [
    {
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "scopes": [
        "team",
        "personal",
        "groupchat"
      ],
      "needsChannelSelector": false,
      "isNotificationOnly": false,
      "supportsFiles": true,
      "supportsCalling": false,
      "supportsVideo": true,
      "commandLists": [
        {
          "scopes": [
            "team",
            "groupchat"
          ],
          "commands": [
            {
              "title": "Command 1",
              "description": "Description of Command 1"
            },
            {
              "title": "Command 2",
              "description": "Description of Command 2"
            }
          ]
        },
        {
          "scopes": [
            "personal",
            "groupchat"
          ],
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
      "scopes": [
        "team"
      ],
      "configurationUrl": "https://contoso.com/teamsconnector/configure"
    }
  ],
  "composeExtensions": [
    {
      "canUpdateConfiguration": true,
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "commands": [
        {
          "id": "exampleCmd1",
          "title": "Example Command",
          "type": "query",
          "context": [
            "compose",
            "commandBox"
          ],
          "description": "Command Description; e.g., Search on the web",
          "initialRun": true,
          "fetchTask": false,
          "parameters": [
            {
              "name": "keyword",
              "title": "Search keywords",
              "inputType": "text",
              "description": "Enter the keywords to search for",
              "value": "Initial value for the parameter",
              "choices": [
                {
                  "title": "Title of the choice",
                  "value": "Value of the choice"
                }
              ]
            }
          ]
        },
        {
          "id": "exampleCmd2",
          "title": "Example Command 2",
          "type": "action",
          "context": [
            "message"
          ],
          "description": "Command Description; e.g., Search for a customer",
          "initialRun": true,
          "fetchTask": true,
          "parameters": [
            {
              "name": "custinfo",
              "title": "Customer name",
              "description": "Enter a customer name",
              "inputType": "text"
            }
          ]
        }
      ],
      "taskInfo": {
        "title": "Initial dialog title",
        "width": "Dialog width",
        "height": "Dialog height",
        "url": "Initial webview URL"
      },
      "messageHandlers": [
        {
          "type": "link",
          "value": {
            "domains": [
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
  "devicePermissions": [
    "geolocation",
    "media",
    "notifications",
    "midi",
    "openExternal"
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
  "showLoadingIndicator": false,
  "isFullScreen": false,
  "activities": {
    "activityTypes": [
      {
        "type": "taskCreated",
        "description": "Task created activity",
        "templateText": "<team member> created task <taskId> for you"
      },
      {
        "type": "userMention",
        "description": "Personal mention activity",
        "templateText": "<team member> mentioned you"
      }
    ]
  }
}
```

<span data-ttu-id="02aea-110">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="02aea-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="02aea-111">$schema</span><span class="sxs-lookup"><span data-stu-id="02aea-111">$schema</span></span>

<span data-ttu-id="02aea-112">*Opcional, mas recomendado cadeia de* caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-112">*Optional, but recommended* — string</span></span>

<span data-ttu-id="02aea-113">A https:// URL que referencia o esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="02aea-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="02aea-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="02aea-114">manifestVersion</span></span>

<span data-ttu-id="02aea-115">**Obrigatório —** cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-115">**Required** — string</span></span>

<span data-ttu-id="02aea-116">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="02aea-116">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="02aea-117">Deve ser "1.7".</span><span class="sxs-lookup"><span data-stu-id="02aea-117">It should be "1.7".</span></span>

## <a name="version"></a><span data-ttu-id="02aea-118">versão</span><span class="sxs-lookup"><span data-stu-id="02aea-118">version</span></span>

<span data-ttu-id="02aea-119">**Obrigatório —** cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-119">**Required** — string</span></span>

<span data-ttu-id="02aea-120">A versão do aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="02aea-120">The version of the specific app.</span></span> <span data-ttu-id="02aea-121">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="02aea-121">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="02aea-122">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="02aea-122">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="02aea-123">Se esse aplicativo foi enviado para a loja, o novo manifesto terá que ser re-enviado e revalidado.</span><span class="sxs-lookup"><span data-stu-id="02aea-123">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="02aea-124">Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, depois que ele for aprovado.</span><span class="sxs-lookup"><span data-stu-id="02aea-124">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="02aea-125">Se o aplicativo solicitou a alteração de permissões, os usuários serão solicitados a atualizar e consentir de novo para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-125">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="02aea-126">Esta cadeia de caracteres de versão deve seguir [o padrão de semver](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="02aea-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="02aea-127">id</span><span class="sxs-lookup"><span data-stu-id="02aea-127">id</span></span>

<span data-ttu-id="02aea-128">**Obrigatório —** ID do aplicativo da Microsoft</span><span class="sxs-lookup"><span data-stu-id="02aea-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="02aea-129">O identificador exclusivo gerado pela Microsoft para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-129">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="02aea-130">Se você registrou um bot por meio do Microsoft Bot Framework ou se o aplicativo Web da guia já entra na Microsoft, você já deve ter uma ID e deve insira-a aqui.</span><span class="sxs-lookup"><span data-stu-id="02aea-130">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="02aea-131">Caso contrário, você deve gerar uma nova ID no Portal de Registro de Aplicativos da Microsoft[(Meus](https://apps.dev.microsoft.com)Aplicativos), insira-a aqui e, em seguida, reutilizar ao adicionar um bot. Observação: se você estiver enviando uma atualização para seu aplicativo existente no AppSource, a ID em seu manifesto não deverá ser modificada.</span><span class="sxs-lookup"><span data-stu-id="02aea-131">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you add a bot.Note: If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="02aea-132">developer</span><span class="sxs-lookup"><span data-stu-id="02aea-132">developer</span></span>

<span data-ttu-id="02aea-133">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="02aea-133">**Required** — object</span></span>

<span data-ttu-id="02aea-134">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="02aea-134">Specifies information about your company.</span></span> <span data-ttu-id="02aea-135">Para aplicativos enviados ao AppSource (antigo Office Store), esses valores devem corresponder às informações em sua entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="02aea-135">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="02aea-136">Consulte nossas [diretrizes de publicação para](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) obter informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="02aea-136">See our [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="02aea-137">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-137">Name</span></span>| <span data-ttu-id="02aea-138">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-138">Maximum size</span></span> | <span data-ttu-id="02aea-139">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-139">Required</span></span> | <span data-ttu-id="02aea-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-140">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="02aea-141">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-141">32 characters</span></span>|<span data-ttu-id="02aea-142">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-142">✔</span></span>|<span data-ttu-id="02aea-143">O nome de exibição do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="02aea-143">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="02aea-144">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-144">2048 characters</span></span>|<span data-ttu-id="02aea-145">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-145">✔</span></span>|<span data-ttu-id="02aea-146">A https:// URL para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="02aea-146">The https:// URL to the developer's website.</span></span> <span data-ttu-id="02aea-147">Esse link deve levar os usuários para a sua empresa ou página de aterrissagem específica do produto.</span><span class="sxs-lookup"><span data-stu-id="02aea-147">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="02aea-148">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-148">2048 characters</span></span>|<span data-ttu-id="02aea-149">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-149">✔</span></span>|<span data-ttu-id="02aea-150">A https:// URL da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="02aea-150">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="02aea-151">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-151">2048 characters</span></span>|<span data-ttu-id="02aea-152">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-152">✔</span></span>|<span data-ttu-id="02aea-153">A https:// URL para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="02aea-153">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="02aea-154">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-154">10 characters</span></span>| |<span data-ttu-id="02aea-155">**Opcional** A ID do Microsoft Partner Network que identifica a organização parceira que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-155">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="02aea-156">nome</span><span class="sxs-lookup"><span data-stu-id="02aea-156">name</span></span>

<span data-ttu-id="02aea-157">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="02aea-157">**Required** — object</span></span>

<span data-ttu-id="02aea-158">O nome da experiência do seu aplicativo, exibido aos usuários na experiência do Teams.</span><span class="sxs-lookup"><span data-stu-id="02aea-158">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="02aea-159">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="02aea-159">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="02aea-160">Os valores `short` e não devem ser os `full` mesmos.</span><span class="sxs-lookup"><span data-stu-id="02aea-160">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="02aea-161">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-161">Name</span></span>| <span data-ttu-id="02aea-162">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-162">Maximum size</span></span> | <span data-ttu-id="02aea-163">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-163">Required</span></span> | <span data-ttu-id="02aea-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-164">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="02aea-165">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-165">30 characters</span></span>|<span data-ttu-id="02aea-166">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-166">✔</span></span>|<span data-ttu-id="02aea-167">O nome de exibição curto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-167">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="02aea-168">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-168">100 characters</span></span>||<span data-ttu-id="02aea-169">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="02aea-169">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="02aea-170">descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-170">description</span></span>

<span data-ttu-id="02aea-171">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="02aea-171">**Required** — object</span></span>

<span data-ttu-id="02aea-172">Descreve seu aplicativo para os usuários.</span><span class="sxs-lookup"><span data-stu-id="02aea-172">Describes your app to users.</span></span> <span data-ttu-id="02aea-173">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="02aea-173">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="02aea-174">Certifique-se de que sua descrição descreva com precisão sua experiência e fornece informações para ajudar clientes potenciais a entender o que sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="02aea-174">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="02aea-175">Você também deve observar, na descrição completa, se uma conta externa for necessária para uso.</span><span class="sxs-lookup"><span data-stu-id="02aea-175">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="02aea-176">Os valores `short` e não devem ser os `full` mesmos.</span><span class="sxs-lookup"><span data-stu-id="02aea-176">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="02aea-177">Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir qualquer outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-177">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="02aea-178">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-178">Name</span></span>| <span data-ttu-id="02aea-179">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-179">Maximum size</span></span> | <span data-ttu-id="02aea-180">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-180">Required</span></span> | <span data-ttu-id="02aea-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-181">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="02aea-182">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-182">80 characters</span></span>|<span data-ttu-id="02aea-183">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-183">✔</span></span>|<span data-ttu-id="02aea-184">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="02aea-184">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="02aea-185">4.000 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-185">4000 characters</span></span>|<span data-ttu-id="02aea-186">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-186">✔</span></span>|<span data-ttu-id="02aea-187">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-187">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="02aea-188">packageName</span><span class="sxs-lookup"><span data-stu-id="02aea-188">packageName</span></span>

<span data-ttu-id="02aea-189">**Opcional** — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-189">**Optional** — string</span></span>

<span data-ttu-id="02aea-190">Um identificador exclusivo para este aplicativo na notação de domínio reverso; por exemplo, com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="02aea-190">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="02aea-191">Comprimento máximo: 64 caracteres.</span><span class="sxs-lookup"><span data-stu-id="02aea-191">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="02aea-192">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="02aea-192">localizationInfo</span></span>

<span data-ttu-id="02aea-193">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="02aea-193">**Optional** — object</span></span>

<span data-ttu-id="02aea-194">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="02aea-194">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="02aea-195">Consulte [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="02aea-195">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="02aea-196">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-196">Name</span></span>| <span data-ttu-id="02aea-197">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-197">Maximum size</span></span> | <span data-ttu-id="02aea-198">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-198">Required</span></span> | <span data-ttu-id="02aea-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-199">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="02aea-200">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-200">✔</span></span>|<span data-ttu-id="02aea-201">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="02aea-201">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="02aea-202">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="02aea-202">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="02aea-203">Uma matriz de objetos especificando traduções de idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="02aea-203">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="02aea-204">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-204">Name</span></span>| <span data-ttu-id="02aea-205">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-205">Maximum size</span></span> | <span data-ttu-id="02aea-206">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-206">Required</span></span> | <span data-ttu-id="02aea-207">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-207">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="02aea-208">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-208">✔</span></span>|<span data-ttu-id="02aea-209">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="02aea-209">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="02aea-210">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-210">✔</span></span>|<span data-ttu-id="02aea-211">Um caminho de arquivo relativo para um arquivo .json que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="02aea-211">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="02aea-212">ícones</span><span class="sxs-lookup"><span data-stu-id="02aea-212">icons</span></span>

<span data-ttu-id="02aea-213">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="02aea-213">**Required** — object</span></span>

<span data-ttu-id="02aea-214">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="02aea-214">Icons used within the Teams app.</span></span> <span data-ttu-id="02aea-215">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="02aea-215">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="02aea-216">Consulte [Ícones](../../concepts/build-and-test/apps-package.md#app-icons) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="02aea-216">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="02aea-217">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-217">Name</span></span>| <span data-ttu-id="02aea-218">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-218">Maximum size</span></span> | <span data-ttu-id="02aea-219">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-219">Required</span></span> | <span data-ttu-id="02aea-220">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-220">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="02aea-221">32 x 32 pixels</span><span class="sxs-lookup"><span data-stu-id="02aea-221">32 x 32 pixels</span></span>|<span data-ttu-id="02aea-222">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-222">✔</span></span>|<span data-ttu-id="02aea-223">Um caminho de arquivo relativo para um ícone transparente de contorno PNG de 32 x 32.</span><span class="sxs-lookup"><span data-stu-id="02aea-223">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="02aea-224">192 x 192 pixels</span><span class="sxs-lookup"><span data-stu-id="02aea-224">192 x 192 pixels</span></span>|<span data-ttu-id="02aea-225">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-225">✔</span></span>|<span data-ttu-id="02aea-226">Um caminho de arquivo relativo para um ícone PNG de 192 x 192 cores completas.</span><span class="sxs-lookup"><span data-stu-id="02aea-226">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="02aea-227">accentColor</span><span class="sxs-lookup"><span data-stu-id="02aea-227">accentColor</span></span>

<span data-ttu-id="02aea-228">**Opcional** — código de cor HEX HTML</span><span class="sxs-lookup"><span data-stu-id="02aea-228">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="02aea-229">Uma cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="02aea-229">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="02aea-230">O valor deve ser um código de cor HTML válido começando com '#', por `#4464ee` exemplo.</span><span class="sxs-lookup"><span data-stu-id="02aea-230">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="02aea-231">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="02aea-231">configurableTabs</span></span>

<span data-ttu-id="02aea-232">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="02aea-232">**Optional** — array</span></span>

<span data-ttu-id="02aea-233">Usado quando a experiência do aplicativo tem uma experiência de guia de canal de equipe que exige configuração extra antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="02aea-233">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="02aea-234">Guias configuráveis só têm suporte no escopo das equipes  (não pessoal) e, atualmente, só há suporte para uma guia por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-234">Configurable tabs are supported only in the teams scope (not personal), and currently only **one** tab per app is supported.</span></span>

|<span data-ttu-id="02aea-235">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-235">Name</span></span>| <span data-ttu-id="02aea-236">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-236">Type</span></span>| <span data-ttu-id="02aea-237">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-237">Maximum size</span></span> | <span data-ttu-id="02aea-238">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-238">Required</span></span> | <span data-ttu-id="02aea-239">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-239">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="02aea-240">string</span><span class="sxs-lookup"><span data-stu-id="02aea-240">string</span></span>|<span data-ttu-id="02aea-241">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-241">2048 characters</span></span>|<span data-ttu-id="02aea-242">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-242">✔</span></span>|<span data-ttu-id="02aea-243">A https:// URL a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="02aea-243">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="02aea-244">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="02aea-244">array of enums</span></span>|<span data-ttu-id="02aea-245">1 </span><span class="sxs-lookup"><span data-stu-id="02aea-245">1</span></span>|<span data-ttu-id="02aea-246">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-246">✔</span></span>|<span data-ttu-id="02aea-247">Atualmente, as guias configuráveis suportam apenas `team` os `groupchat` escopos e os escopos.</span><span class="sxs-lookup"><span data-stu-id="02aea-247">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="02aea-248">booliano</span><span class="sxs-lookup"><span data-stu-id="02aea-248">boolean</span></span>|||<span data-ttu-id="02aea-249">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="02aea-249">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="02aea-250">Padrão: **true**.</span><span class="sxs-lookup"><span data-stu-id="02aea-250">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="02aea-251">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="02aea-251">array of enums</span></span>|<span data-ttu-id="02aea-252">6 </span><span class="sxs-lookup"><span data-stu-id="02aea-252">6</span></span>||<span data-ttu-id="02aea-253">O conjunto de `contextItem` escopos nos quais há suporte para uma guia.</span><span class="sxs-lookup"><span data-stu-id="02aea-253">The set of `contextItem` scopes where a tab is supported.</span></span> <span data-ttu-id="02aea-254">Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="02aea-254">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="02aea-255">string</span><span class="sxs-lookup"><span data-stu-id="02aea-255">string</span></span>|<span data-ttu-id="02aea-256">2048</span><span class="sxs-lookup"><span data-stu-id="02aea-256">2048</span></span>||<span data-ttu-id="02aea-257">Um caminho de arquivo relativo para uma imagem de visualização de guia para uso no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="02aea-257">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="02aea-258">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="02aea-258">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="02aea-259">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="02aea-259">array of enums</span></span>|<span data-ttu-id="02aea-260">1 </span><span class="sxs-lookup"><span data-stu-id="02aea-260">1</span></span>||<span data-ttu-id="02aea-261">Define como sua guia será disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="02aea-261">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="02aea-262">As opções `sharePointFullPage` são e `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="02aea-262">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="02aea-263">staticTabs</span><span class="sxs-lookup"><span data-stu-id="02aea-263">staticTabs</span></span>

<span data-ttu-id="02aea-264">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="02aea-264">**Optional** — array</span></span>

<span data-ttu-id="02aea-265">Define um conjunto de guias que podem ser "fixadas" por padrão, sem que o usuário as adicione manualmente.</span><span class="sxs-lookup"><span data-stu-id="02aea-265">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="02aea-266">As guias estáticas declaradas `personal` no escopo são sempre fixadas à experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-266">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="02aea-267">As guias estáticas declaradas no `team` escopo não são suportadas no momento.</span><span class="sxs-lookup"><span data-stu-id="02aea-267">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="02aea-268">Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="02aea-268">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="02aea-269">Esse bloco é necessário apenas para soluções que fornecem uma solução de guia estática.</span><span class="sxs-lookup"><span data-stu-id="02aea-269">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="02aea-270">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-270">Name</span></span>| <span data-ttu-id="02aea-271">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-271">Type</span></span>| <span data-ttu-id="02aea-272">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-272">Maximum size</span></span> | <span data-ttu-id="02aea-273">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-273">Required</span></span> | <span data-ttu-id="02aea-274">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-274">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="02aea-275">string</span><span class="sxs-lookup"><span data-stu-id="02aea-275">string</span></span>|<span data-ttu-id="02aea-276">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-276">64 characters</span></span>|<span data-ttu-id="02aea-277">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-277">✔</span></span>|<span data-ttu-id="02aea-278">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="02aea-278">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="02aea-279">string</span><span class="sxs-lookup"><span data-stu-id="02aea-279">string</span></span>|<span data-ttu-id="02aea-280">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-280">128 characters</span></span>|<span data-ttu-id="02aea-281">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-281">✔</span></span>|<span data-ttu-id="02aea-282">O nome de exibição da guia na interface do canal.</span><span class="sxs-lookup"><span data-stu-id="02aea-282">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="02aea-283">string</span><span class="sxs-lookup"><span data-stu-id="02aea-283">string</span></span>||<span data-ttu-id="02aea-284">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-284">✔</span></span>|<span data-ttu-id="02aea-285">A https:// URL que aponta para a interface do usuário da entidade a ser exibida na tela do Teams.</span><span class="sxs-lookup"><span data-stu-id="02aea-285">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="02aea-286">string</span><span class="sxs-lookup"><span data-stu-id="02aea-286">string</span></span>|||<span data-ttu-id="02aea-287">A https:// URL para apontar se um usuário optar por exibir em um navegador.</span><span class="sxs-lookup"><span data-stu-id="02aea-287">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="02aea-288">string</span><span class="sxs-lookup"><span data-stu-id="02aea-288">string</span></span>|||<span data-ttu-id="02aea-289">A https:// URL a ser apontada para as consultas de pesquisa de um usuário.</span><span class="sxs-lookup"><span data-stu-id="02aea-289">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="02aea-290">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="02aea-290">array of enums</span></span>|<span data-ttu-id="02aea-291">1 </span><span class="sxs-lookup"><span data-stu-id="02aea-291">1</span></span>|<span data-ttu-id="02aea-292">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-292">✔</span></span>|<span data-ttu-id="02aea-293">Atualmente, as guias estáticas suportam apenas o escopo, o que significa que ele só pode ser provisionado como `personal` parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="02aea-293">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="02aea-294">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="02aea-294">array of enums</span></span>| <span data-ttu-id="02aea-295">2 </span><span class="sxs-lookup"><span data-stu-id="02aea-295">2</span></span>|| <span data-ttu-id="02aea-296">O conjunto de `contextItem` escopos nos quais há suporte para uma guia.</span><span class="sxs-lookup"><span data-stu-id="02aea-296">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
> <span data-ttu-id="02aea-297">Se suas guias exigem informações dependentes de contexto para exibir  conteúdo relevante ou para iniciar um fluxo de autenticação, confira Obter contexto para sua [guia do Microsoft Teams.](../../tabs/how-to/access-teams-context.md)</span><span class="sxs-lookup"><span data-stu-id="02aea-297">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="02aea-298">bots</span><span class="sxs-lookup"><span data-stu-id="02aea-298">bots</span></span>

<span data-ttu-id="02aea-299">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="02aea-299">**Optional** — array</span></span>

<span data-ttu-id="02aea-300">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="02aea-300">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="02aea-301">O item é uma matriz (máximo de apenas 1 elemento atualmente apenas um bot é permitido por aplicativo) com todos os &mdash; elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="02aea-301">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="02aea-302">Esse bloco é necessário apenas para soluções que fornecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="02aea-302">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="02aea-303">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-303">Name</span></span>| <span data-ttu-id="02aea-304">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-304">Type</span></span>| <span data-ttu-id="02aea-305">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-305">Maximum size</span></span> | <span data-ttu-id="02aea-306">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-306">Required</span></span> | <span data-ttu-id="02aea-307">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-307">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="02aea-308">string</span><span class="sxs-lookup"><span data-stu-id="02aea-308">string</span></span>|<span data-ttu-id="02aea-309">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-309">64 characters</span></span>|<span data-ttu-id="02aea-310">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-310">✔</span></span>|<span data-ttu-id="02aea-311">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="02aea-311">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="02aea-312">Isso pode ser o mesmo que a ID geral [do aplicativo.](#id)</span><span class="sxs-lookup"><span data-stu-id="02aea-312">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="02aea-313">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="02aea-313">array of enums</span></span>|<span data-ttu-id="02aea-314">3</span><span class="sxs-lookup"><span data-stu-id="02aea-314">3</span></span>|<span data-ttu-id="02aea-315">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-315">✔</span></span>|<span data-ttu-id="02aea-316">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="02aea-316">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="02aea-317">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="02aea-317">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="02aea-318">booliano</span><span class="sxs-lookup"><span data-stu-id="02aea-318">boolean</span></span>|||<span data-ttu-id="02aea-319">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="02aea-319">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="02aea-320">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="02aea-320">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="02aea-321">booliano</span><span class="sxs-lookup"><span data-stu-id="02aea-321">boolean</span></span>|||<span data-ttu-id="02aea-322">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="02aea-322">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="02aea-323">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="02aea-323">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="02aea-324">booliano</span><span class="sxs-lookup"><span data-stu-id="02aea-324">boolean</span></span>|||<span data-ttu-id="02aea-325">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="02aea-325">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="02aea-326">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="02aea-326">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="02aea-327">booliano</span><span class="sxs-lookup"><span data-stu-id="02aea-327">boolean</span></span>|||<span data-ttu-id="02aea-328">Um valor indicando onde um bot dá suporte a chamada de áudio.</span><span class="sxs-lookup"><span data-stu-id="02aea-328">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="02aea-329">**IMPORTANTE:** essa propriedade é experimental no momento.</span><span class="sxs-lookup"><span data-stu-id="02aea-329">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="02aea-330">As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="02aea-330">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="02aea-331">Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="02aea-331">It is provided for testing and exploration purposes only and should not be used in production applications.</span></span> <span data-ttu-id="02aea-332">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="02aea-332">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="02aea-333">booliano</span><span class="sxs-lookup"><span data-stu-id="02aea-333">boolean</span></span>|||<span data-ttu-id="02aea-334">Um valor que indica onde um bot dá suporte à chamada de vídeo.</span><span class="sxs-lookup"><span data-stu-id="02aea-334">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="02aea-335">**IMPORTANTE:** essa propriedade é experimental no momento.</span><span class="sxs-lookup"><span data-stu-id="02aea-335">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="02aea-336">As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="02aea-336">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="02aea-337">Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="02aea-337">It is provided for testing and exploration purposes only and should not be used in production applications.</span></span> <span data-ttu-id="02aea-338">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="02aea-338">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="02aea-339">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="02aea-339">bots.commandLists</span></span>

<span data-ttu-id="02aea-340">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="02aea-340">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="02aea-341">O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo; você deve definir uma lista de comandos separada para cada escopo ao qual seu `object` bot oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="02aea-341">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="02aea-342">Consulte [menus de Bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="02aea-342">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="02aea-343">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-343">Name</span></span>| <span data-ttu-id="02aea-344">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-344">Type</span></span>| <span data-ttu-id="02aea-345">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-345">Maximum size</span></span> | <span data-ttu-id="02aea-346">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-346">Required</span></span> | <span data-ttu-id="02aea-347">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-347">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="02aea-348">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="02aea-348">array of enums</span></span>|<span data-ttu-id="02aea-349">3</span><span class="sxs-lookup"><span data-stu-id="02aea-349">3</span></span>|<span data-ttu-id="02aea-350">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-350">✔</span></span>|<span data-ttu-id="02aea-351">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="02aea-351">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="02aea-352">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="02aea-352">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="02aea-353">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="02aea-353">array of objects</span></span>|<span data-ttu-id="02aea-354">10 </span><span class="sxs-lookup"><span data-stu-id="02aea-354">10</span></span>|<span data-ttu-id="02aea-355">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-355">✔</span></span>|<span data-ttu-id="02aea-356">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="02aea-356">An array of commands the bot supports:</span></span><br><span data-ttu-id="02aea-357">`title`: o nome do comando bot (cadeia, 32)</span><span class="sxs-lookup"><span data-stu-id="02aea-357">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="02aea-358">`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)</span><span class="sxs-lookup"><span data-stu-id="02aea-358">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="02aea-359">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="02aea-359">bots.commandLists.commands</span></span>

|<span data-ttu-id="02aea-360">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-360">Name</span></span>| <span data-ttu-id="02aea-361">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-361">Type</span></span>| <span data-ttu-id="02aea-362">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-362">Maximum size</span></span> | <span data-ttu-id="02aea-363">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-363">Required</span></span> | <span data-ttu-id="02aea-364">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-364">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="02aea-365">title</span><span class="sxs-lookup"><span data-stu-id="02aea-365">title</span></span>|<span data-ttu-id="02aea-366">string</span><span class="sxs-lookup"><span data-stu-id="02aea-366">string</span></span>|<span data-ttu-id="02aea-367">12 </span><span class="sxs-lookup"><span data-stu-id="02aea-367">12</span></span>|<span data-ttu-id="02aea-368">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-368">✔</span></span>|<span data-ttu-id="02aea-369">O nome do comando de bot</span><span class="sxs-lookup"><span data-stu-id="02aea-369">The bot command name</span></span>|
|<span data-ttu-id="02aea-370">description</span><span class="sxs-lookup"><span data-stu-id="02aea-370">description</span></span>|<span data-ttu-id="02aea-371">string</span><span class="sxs-lookup"><span data-stu-id="02aea-371">string</span></span>|<span data-ttu-id="02aea-372">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-372">128 characters</span></span>|<span data-ttu-id="02aea-373">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-373">✔</span></span>|<span data-ttu-id="02aea-374">Uma descrição de texto simples ou um exemplo da sintaxe do comando e seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="02aea-374">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="02aea-375">conectores</span><span class="sxs-lookup"><span data-stu-id="02aea-375">connectors</span></span>

<span data-ttu-id="02aea-376">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="02aea-376">**Optional** — array</span></span>

<span data-ttu-id="02aea-377">O `connectors` bloco define um Conector do Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-377">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="02aea-378">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="02aea-378">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="02aea-379">Esse bloco é necessário apenas para soluções que fornecem um Conector.</span><span class="sxs-lookup"><span data-stu-id="02aea-379">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="02aea-380">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-380">Name</span></span>| <span data-ttu-id="02aea-381">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-381">Type</span></span>| <span data-ttu-id="02aea-382">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-382">Maximum size</span></span> | <span data-ttu-id="02aea-383">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-383">Required</span></span> | <span data-ttu-id="02aea-384">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-384">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="02aea-385">string</span><span class="sxs-lookup"><span data-stu-id="02aea-385">string</span></span>|<span data-ttu-id="02aea-386">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-386">2048 characters</span></span>|<span data-ttu-id="02aea-387">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-387">✔</span></span>|<span data-ttu-id="02aea-388">A https:// URL a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="02aea-388">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="02aea-389">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="02aea-389">array of enums</span></span>|<span data-ttu-id="02aea-390">1 </span><span class="sxs-lookup"><span data-stu-id="02aea-390">1</span></span>|<span data-ttu-id="02aea-391">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-391">✔</span></span>|<span data-ttu-id="02aea-392">Especifica se o Conector oferece uma experiência no contexto de um canal em um , ou uma experiência com escopo `team` para um usuário individual sozinho ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="02aea-392">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="02aea-393">Atualmente, apenas o `team` escopo é suportado.</span><span class="sxs-lookup"><span data-stu-id="02aea-393">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="02aea-394">string</span><span class="sxs-lookup"><span data-stu-id="02aea-394">string</span></span>|<span data-ttu-id="02aea-395">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-395">64 characters</span></span>|<span data-ttu-id="02aea-396">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-396">✔</span></span>|<span data-ttu-id="02aea-397">Um identificador exclusivo para o Conector que corresponde a sua ID no [Painel do Desenvolvedor de Conectores.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="02aea-397">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="02aea-398">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="02aea-398">composeExtensions</span></span>

<span data-ttu-id="02aea-399">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="02aea-399">**Optional** — array</span></span>

<span data-ttu-id="02aea-400">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-400">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="02aea-401">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem a funcionar.</span><span class="sxs-lookup"><span data-stu-id="02aea-401">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="02aea-402">O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="02aea-402">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="02aea-403">Esse bloco é necessário apenas para soluções que fornecem uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="02aea-403">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="02aea-404">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-404">Name</span></span>| <span data-ttu-id="02aea-405">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-405">Type</span></span> | <span data-ttu-id="02aea-406">Tamanho Máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-406">Maximum Size</span></span> | <span data-ttu-id="02aea-407">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-407">Required</span></span> | <span data-ttu-id="02aea-408">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-408">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="02aea-409">string</span><span class="sxs-lookup"><span data-stu-id="02aea-409">string</span></span>|<span data-ttu-id="02aea-410">64</span><span class="sxs-lookup"><span data-stu-id="02aea-410">64</span></span>|<span data-ttu-id="02aea-411">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-411">✔</span></span>|<span data-ttu-id="02aea-412">A ID exclusiva do aplicativo da Microsoft para o bot que é o suporte à extensão de mensagens, conforme registrado na Estrutura do Bot.</span><span class="sxs-lookup"><span data-stu-id="02aea-412">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="02aea-413">Isso pode ser o mesmo que a ID geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-413">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="02aea-414">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="02aea-414">array of objects</span></span>|<span data-ttu-id="02aea-415">10 </span><span class="sxs-lookup"><span data-stu-id="02aea-415">10</span></span>|<span data-ttu-id="02aea-416">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-416">✔</span></span>|<span data-ttu-id="02aea-417">Matriz de comandos compatíveis com a extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="02aea-417">Array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="02aea-418">booliano</span><span class="sxs-lookup"><span data-stu-id="02aea-418">boolean</span></span>|||<span data-ttu-id="02aea-419">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="02aea-419">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="02aea-420">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="02aea-420">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="02aea-421">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="02aea-421">array of Objects</span></span>|<span data-ttu-id="02aea-422">5 </span><span class="sxs-lookup"><span data-stu-id="02aea-422">5</span></span>||<span data-ttu-id="02aea-423">Uma lista de manipuladores que permitem que aplicativos sejam invocados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="02aea-423">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="02aea-424">string</span><span class="sxs-lookup"><span data-stu-id="02aea-424">string</span></span>|||<span data-ttu-id="02aea-425">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="02aea-425">The type of message handler.</span></span> <span data-ttu-id="02aea-426">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="02aea-426">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="02aea-427">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-427">array of Strings</span></span>|||<span data-ttu-id="02aea-428">Matriz de domínios em que o manipulador de mensagens de link pode se registrar.</span><span class="sxs-lookup"><span data-stu-id="02aea-428">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="02aea-429">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="02aea-429">composeExtensions.commands</span></span>

<span data-ttu-id="02aea-430">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="02aea-430">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="02aea-431">Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="02aea-431">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="02aea-432">Há um máximo de 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="02aea-432">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="02aea-433">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="02aea-433">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="02aea-434">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-434">Name</span></span>| <span data-ttu-id="02aea-435">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-435">Type</span></span>| <span data-ttu-id="02aea-436">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-436">Maximum size</span></span> | <span data-ttu-id="02aea-437">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-437">Required</span></span> | <span data-ttu-id="02aea-438">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-438">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="02aea-439">string</span><span class="sxs-lookup"><span data-stu-id="02aea-439">string</span></span>|<span data-ttu-id="02aea-440">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-440">64 characters</span></span>|<span data-ttu-id="02aea-441">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-441">✔</span></span>|<span data-ttu-id="02aea-442">A ID do comando.</span><span class="sxs-lookup"><span data-stu-id="02aea-442">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="02aea-443">string</span><span class="sxs-lookup"><span data-stu-id="02aea-443">string</span></span>|<span data-ttu-id="02aea-444">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-444">32 characters</span></span>|<span data-ttu-id="02aea-445">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-445">✔</span></span>|<span data-ttu-id="02aea-446">O nome do comando amigável.</span><span class="sxs-lookup"><span data-stu-id="02aea-446">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="02aea-447">string</span><span class="sxs-lookup"><span data-stu-id="02aea-447">string</span></span>|<span data-ttu-id="02aea-448">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-448">64 characters</span></span>||<span data-ttu-id="02aea-449">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="02aea-449">Type of the command.</span></span> <span data-ttu-id="02aea-450">Um ou `query` `action` .</span><span class="sxs-lookup"><span data-stu-id="02aea-450">One of `query` or `action`.</span></span> <span data-ttu-id="02aea-451">Padrão: **consulta**.</span><span class="sxs-lookup"><span data-stu-id="02aea-451">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="02aea-452">string</span><span class="sxs-lookup"><span data-stu-id="02aea-452">string</span></span>|<span data-ttu-id="02aea-453">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-453">128 characters</span></span>||<span data-ttu-id="02aea-454">A descrição que aparece para os usuários para indicar a finalidade desse comando.</span><span class="sxs-lookup"><span data-stu-id="02aea-454">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="02aea-455">booliano</span><span class="sxs-lookup"><span data-stu-id="02aea-455">boolean</span></span>|||<span data-ttu-id="02aea-456">Um valor booliana que indica se o comando deve ser executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="02aea-456">A boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="02aea-457">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="02aea-457">Default: **false**.</span></span>|
|`context`|<span data-ttu-id="02aea-458">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-458">array of Strings</span></span>|<span data-ttu-id="02aea-459">3</span><span class="sxs-lookup"><span data-stu-id="02aea-459">3</span></span>||<span data-ttu-id="02aea-460">Define de onde a extensão da mensagem pode ser invocada.</span><span class="sxs-lookup"><span data-stu-id="02aea-460">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="02aea-461">Qualquer combinação de `compose` , `commandBox` `message` .</span><span class="sxs-lookup"><span data-stu-id="02aea-461">Any combination of`compose`,`commandBox`,`message` .</span></span> <span data-ttu-id="02aea-462">O padrão é `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="02aea-462">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="02aea-463">booliano</span><span class="sxs-lookup"><span data-stu-id="02aea-463">boolean</span></span>|||<span data-ttu-id="02aea-464">Um valor booliana que indica se ele deve buscar o módulo de tarefa dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="02aea-464">A boolean value that indicates if it should fetch the task module dynamically.</span></span> <span data-ttu-id="02aea-465">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="02aea-465">Default: **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="02aea-466">objeto</span><span class="sxs-lookup"><span data-stu-id="02aea-466">object</span></span>|||<span data-ttu-id="02aea-467">Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="02aea-467">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="02aea-468">string</span><span class="sxs-lookup"><span data-stu-id="02aea-468">string</span></span>|<span data-ttu-id="02aea-469">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-469">64 characters</span></span>||<span data-ttu-id="02aea-470">Título da caixa de diálogo inicial.</span><span class="sxs-lookup"><span data-stu-id="02aea-470">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="02aea-471">string</span><span class="sxs-lookup"><span data-stu-id="02aea-471">string</span></span>|||<span data-ttu-id="02aea-472">Largura da caixa de diálogo - um número em pixels ou layout padrão, como "grande", "médio" ou "pequeno".</span><span class="sxs-lookup"><span data-stu-id="02aea-472">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="02aea-473">string</span><span class="sxs-lookup"><span data-stu-id="02aea-473">string</span></span>|||<span data-ttu-id="02aea-474">Altura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.</span><span class="sxs-lookup"><span data-stu-id="02aea-474">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="02aea-475">string</span><span class="sxs-lookup"><span data-stu-id="02aea-475">string</span></span>|||<span data-ttu-id="02aea-476">URL inicial do webview.</span><span class="sxs-lookup"><span data-stu-id="02aea-476">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="02aea-477">matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="02aea-477">array of object</span></span>|<span data-ttu-id="02aea-478">5 itens</span><span class="sxs-lookup"><span data-stu-id="02aea-478">5 items</span></span>|<span data-ttu-id="02aea-479">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-479">✔</span></span>|<span data-ttu-id="02aea-480">A lista de parâmetros que o comando leva.</span><span class="sxs-lookup"><span data-stu-id="02aea-480">The list of parameters the command takes.</span></span> <span data-ttu-id="02aea-481">Mínimo: 1; máximo: 5.</span><span class="sxs-lookup"><span data-stu-id="02aea-481">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="02aea-482">string</span><span class="sxs-lookup"><span data-stu-id="02aea-482">string</span></span>|<span data-ttu-id="02aea-483">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-483">64 characters</span></span>|<span data-ttu-id="02aea-484">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-484">✔</span></span>|<span data-ttu-id="02aea-485">O nome do parâmetro como ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="02aea-485">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="02aea-486">Isso está incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="02aea-486">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="02aea-487">string</span><span class="sxs-lookup"><span data-stu-id="02aea-487">string</span></span>|<span data-ttu-id="02aea-488">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-488">32 characters</span></span>|<span data-ttu-id="02aea-489">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-489">✔</span></span>|<span data-ttu-id="02aea-490">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="02aea-490">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="02aea-491">string</span><span class="sxs-lookup"><span data-stu-id="02aea-491">string</span></span>|<span data-ttu-id="02aea-492">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-492">128 characters</span></span>||<span data-ttu-id="02aea-493">Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="02aea-493">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="02aea-494">string</span><span class="sxs-lookup"><span data-stu-id="02aea-494">string</span></span>|<span data-ttu-id="02aea-495">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-495">512 characters</span></span>||<span data-ttu-id="02aea-496">Valor inicial do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="02aea-496">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="02aea-497">string</span><span class="sxs-lookup"><span data-stu-id="02aea-497">string</span></span>|<span data-ttu-id="02aea-498">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-498">128 characters</span></span>||<span data-ttu-id="02aea-499">Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="02aea-499">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="02aea-500">Um dos `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="02aea-500">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="02aea-501">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="02aea-501">array of objects</span></span>|<span data-ttu-id="02aea-502">10 itens</span><span class="sxs-lookup"><span data-stu-id="02aea-502">10 items</span></span>||<span data-ttu-id="02aea-503">As opções de escolha para o `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="02aea-503">The choice options for the`choiceset`.</span></span> <span data-ttu-id="02aea-504">Use somente quando `parameter.inputType` for `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="02aea-504">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="02aea-505">string</span><span class="sxs-lookup"><span data-stu-id="02aea-505">string</span></span>|<span data-ttu-id="02aea-506">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-506">128 characters</span></span>|<span data-ttu-id="02aea-507">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-507">✔</span></span>|<span data-ttu-id="02aea-508">Título da escolha.</span><span class="sxs-lookup"><span data-stu-id="02aea-508">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="02aea-509">string</span><span class="sxs-lookup"><span data-stu-id="02aea-509">string</span></span>|<span data-ttu-id="02aea-510">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-510">512 characters</span></span>|<span data-ttu-id="02aea-511">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-511">✔</span></span>|<span data-ttu-id="02aea-512">O valor da escolha.</span><span class="sxs-lookup"><span data-stu-id="02aea-512">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="02aea-513">permissões</span><span class="sxs-lookup"><span data-stu-id="02aea-513">permissions</span></span>

<span data-ttu-id="02aea-514">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-514">**Optional** — array of strings</span></span>

<span data-ttu-id="02aea-515">Uma matriz que especifica quais permissões o aplicativo solicita, o que permite que os usuários `string` finais saibam como a extensão será efetivada.</span><span class="sxs-lookup"><span data-stu-id="02aea-515">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="02aea-516">As seguintes opções não são exclusivas:</span><span class="sxs-lookup"><span data-stu-id="02aea-516">The following options are non-exclusive:</span></span>

* <span data-ttu-id="02aea-517">`identity`&emsp;Requer informações de identidade do usuário</span><span class="sxs-lookup"><span data-stu-id="02aea-517">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="02aea-518">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe</span><span class="sxs-lookup"><span data-stu-id="02aea-518">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="02aea-519">Alterar essas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="02aea-519">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span> <span data-ttu-id="02aea-520">Consulte [Atualizando seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="02aea-520">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="02aea-521">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="02aea-521">devicePermissions</span></span>

<span data-ttu-id="02aea-522">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-522">**Optional** — array of strings</span></span>

<span data-ttu-id="02aea-523">Especifica os recursos nativos no dispositivo de um usuário aos que seu aplicativo pode solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="02aea-523">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="02aea-524">As opções são:</span><span class="sxs-lookup"><span data-stu-id="02aea-524">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="02aea-525">validDomains</span><span class="sxs-lookup"><span data-stu-id="02aea-525">validDomains</span></span>

<span data-ttu-id="02aea-526">**Optional**, except **Required** where noted</span><span class="sxs-lookup"><span data-stu-id="02aea-526">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="02aea-527">Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="02aea-527">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="02aea-528">As listagem de domínio podem incluir caracteres curinga, por `*.example.com` exemplo.</span><span class="sxs-lookup"><span data-stu-id="02aea-528">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="02aea-529">Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="02aea-529">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="02aea-530">Se a configuração da guia ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para a configuração de guia, esse domínio deverá ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="02aea-530">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="02aea-531">No **entanto,** não é necessário incluir os domínios de provedores de identidade que você deseja suportar em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-531">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="02aea-532">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve incluir accounts.google.com em `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="02aea-532">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="02aea-533">Os aplicativos do Teams que exigem suas próprias URLs do SharePoint para funcionarem bem podem incluir "{teamsitedomain}" em sua lista de domínios válida.</span><span class="sxs-lookup"><span data-stu-id="02aea-533">Teams apps that require their own sharepoint URLs to function well, may include "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="02aea-534">Não adicione domínios que estejam fora do seu controle, diretamente ou por meio de caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="02aea-534">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="02aea-535">Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="02aea-535">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="02aea-536">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="02aea-536">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="02aea-537">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="02aea-537">webApplicationInfo</span></span>

<span data-ttu-id="02aea-538">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="02aea-538">**Optional** — object</span></span>

<span data-ttu-id="02aea-539">Especifique a ID do aplicativo do Azure Active Directory (Azure AD) e as informações do Microsoft Graph para ajudar os usuários a entrar facilmente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-539">Specify your Azure Active Directory (Azure AD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="02aea-540">Se seu aplicativo estiver registrado no Azure AD, você deverá fornecer a ID do aplicativo, para que os administradores possam analisar facilmente as permissões e conceder consentimento no centro de administração do Teams.</span><span class="sxs-lookup"><span data-stu-id="02aea-540">If your app is registered in Azure AD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="02aea-541">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-541">Name</span></span>| <span data-ttu-id="02aea-542">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-542">Type</span></span>| <span data-ttu-id="02aea-543">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-543">Maximum size</span></span> | <span data-ttu-id="02aea-544">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-544">Required</span></span> | <span data-ttu-id="02aea-545">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-545">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="02aea-546">string</span><span class="sxs-lookup"><span data-stu-id="02aea-546">string</span></span>|<span data-ttu-id="02aea-547">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-547">36 characters</span></span>|<span data-ttu-id="02aea-548">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-548">✔</span></span>|<span data-ttu-id="02aea-549">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-549">AAD application id of the app.</span></span> <span data-ttu-id="02aea-550">Essa ID deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="02aea-550">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="02aea-551">string</span><span class="sxs-lookup"><span data-stu-id="02aea-551">string</span></span>|<span data-ttu-id="02aea-552">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-552">2048 characters</span></span>|<span data-ttu-id="02aea-553">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-553">✔</span></span>|<span data-ttu-id="02aea-554">URL do recurso do aplicativo para aquisição de token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="02aea-554">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="02aea-555">**OBSERVAÇÃO:** Se você não estiver usando o SSO, certifique-se de inserir um valor fictício de cadeia de caracteres nesse campo para o manifesto do aplicativo, por exemplo, para evitar https://notapplicable uma resposta de erro.</span><span class="sxs-lookup"><span data-stu-id="02aea-555">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="02aea-556">matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-556">array of strings</span></span>|<span data-ttu-id="02aea-557">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-557">128 characters</span></span>||<span data-ttu-id="02aea-558">Especifique o [consentimento específico do recurso granular.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span><span class="sxs-lookup"><span data-stu-id="02aea-558">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="02aea-559">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="02aea-559">showLoadingIndicator</span></span>

<span data-ttu-id="02aea-560">**Opcional** — booleano</span><span class="sxs-lookup"><span data-stu-id="02aea-560">**Optional** — boolean</span></span>

<span data-ttu-id="02aea-561">Indica se o indicador de carregamento será ou não mostre quando um aplicativo/guia estiver sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="02aea-561">Indicate whether or not to show the loading indicator when an app/tab is loading.</span></span> <span data-ttu-id="02aea-562">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="02aea-562">Default: **false**.</span></span>
>[!NOTE]
><span data-ttu-id="02aea-563">Se você definir "showLoadingIndicator : true" no manifesto do aplicativo, para [que a](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) página seja carregada corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa de acordo com o protocolo descrito em Mostrar um documento indicador de carregamento nativo.</span><span class="sxs-lookup"><span data-stu-id="02aea-563">If you set "showLoadingIndicator : true" in your app manifest, then for the page to load correctly, you must modify the content pages of your tabs and task modules as per the protocol described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="02aea-564">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="02aea-564">isFullScreen</span></span>

 <span data-ttu-id="02aea-565">**Opcional** — booleano</span><span class="sxs-lookup"><span data-stu-id="02aea-565">**Optional** — boolean</span></span>

<span data-ttu-id="02aea-566">Indica onde um aplicativo pessoal é renderizado com ou sem uma barra de controle guia.</span><span class="sxs-lookup"><span data-stu-id="02aea-566">Indicate where a personal app is rendered with or without a tab-header bar.</span></span> <span data-ttu-id="02aea-567">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="02aea-567">Default: **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="02aea-568">activities</span><span class="sxs-lookup"><span data-stu-id="02aea-568">activities</span></span>

<span data-ttu-id="02aea-569">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="02aea-569">**Optional** — object</span></span>

<span data-ttu-id="02aea-570">Defina as propriedades que seu aplicativo usará para postar em um feed de atividades do usuário.</span><span class="sxs-lookup"><span data-stu-id="02aea-570">Define the properties your app will use to post to a user activity feed.</span></span>

|<span data-ttu-id="02aea-571">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-571">Name</span></span>| <span data-ttu-id="02aea-572">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-572">Type</span></span>| <span data-ttu-id="02aea-573">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-573">Maximum size</span></span> | <span data-ttu-id="02aea-574">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-574">Required</span></span> | <span data-ttu-id="02aea-575">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-575">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="02aea-576">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="02aea-576">array of Objects</span></span>|<span data-ttu-id="02aea-577">128 itens</span><span class="sxs-lookup"><span data-stu-id="02aea-577">128 items</span></span>| | <span data-ttu-id="02aea-578">Especifique os tipos de atividades que seu aplicativo pode postar em um feed de atividades de usuários.</span><span class="sxs-lookup"><span data-stu-id="02aea-578">Specify the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="02aea-579">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="02aea-579">activities.activityTypes</span></span>

|<span data-ttu-id="02aea-580">Nome</span><span class="sxs-lookup"><span data-stu-id="02aea-580">Name</span></span>| <span data-ttu-id="02aea-581">Tipo</span><span class="sxs-lookup"><span data-stu-id="02aea-581">Type</span></span>| <span data-ttu-id="02aea-582">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="02aea-582">Maximum size</span></span> | <span data-ttu-id="02aea-583">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="02aea-583">Required</span></span> | <span data-ttu-id="02aea-584">Descrição</span><span class="sxs-lookup"><span data-stu-id="02aea-584">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="02aea-585">string</span><span class="sxs-lookup"><span data-stu-id="02aea-585">string</span></span>|<span data-ttu-id="02aea-586">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-586">32 characters</span></span>|<span data-ttu-id="02aea-587">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-587">✔</span></span>|<span data-ttu-id="02aea-588">O tipo de notificação.</span><span class="sxs-lookup"><span data-stu-id="02aea-588">The notification type.</span></span> <span data-ttu-id="02aea-589">*Veja abaixo.*</span><span class="sxs-lookup"><span data-stu-id="02aea-589">*See below*.</span></span>|
|`description`|<span data-ttu-id="02aea-590">string</span><span class="sxs-lookup"><span data-stu-id="02aea-590">string</span></span>|<span data-ttu-id="02aea-591">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-591">128 characters</span></span>|<span data-ttu-id="02aea-592">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-592">✔</span></span>|<span data-ttu-id="02aea-593">Uma breve descrição da notificação.</span><span class="sxs-lookup"><span data-stu-id="02aea-593">A brief description of the notification.</span></span> <span data-ttu-id="02aea-594">*Veja abaixo.*</span><span class="sxs-lookup"><span data-stu-id="02aea-594">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="02aea-595">string</span><span class="sxs-lookup"><span data-stu-id="02aea-595">string</span></span>|<span data-ttu-id="02aea-596">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="02aea-596">128 characters</span></span>|<span data-ttu-id="02aea-597">✔</span><span class="sxs-lookup"><span data-stu-id="02aea-597">✔</span></span>|<span data-ttu-id="02aea-598">Por exemplo: "{actor} criou a tarefa {taskId} para você"</span><span class="sxs-lookup"><span data-stu-id="02aea-598">Ex: "{actor} created task {taskId} for you"</span></span>|

```json
{
   "activities":{
      "activityTypes":[
         {
            "type":"taskCreated",
            "description":"Task Created Activity",
            "templateText":"{actor} created task {taskId} for you"
         },
         {
            "type":"teamMention",
            "description":"Team Mention Activity",
            "templateText":"{actor} mentioned team"
         },
         {
            "type":"channelMention",
            "description":"Channel Mention Activity",
            "templateText":"{actor} mentioned channel"
         },
         {
            "type":"userMention",
            "description":"Personal Mention Activity",
            "templateText":"{actor} mentioned user"
         },
         {
            "type":"calendarForward",
            "description":"Forwarding a Calendar Event",
            "templateText":"{actor} sent user an invite on behalf of {eventOwner}"
         },
         {
            "type":"calendarForward",
            "description":"Forwarding a Calendar Event",
            "templateText":"{actor} sent user an invite on behalf of {eventOwner}"
         },
         {
            "type":"creatorTaskCreated",
            "description":"Created Task Created",
            "templateText":"The Creator created task {taskId} for you"
         }
      ]
   }
}
```

***
>
>
