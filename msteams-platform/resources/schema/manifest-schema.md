---
title: Referência de esquema manifesto
description: Descreve o esquema manifesto para Microsoft Teams
ms.topic: reference
ms.author: lajanuar
localization_priority: Normal
keywords: equipes manifestam esquema
ms.openlocfilehash: 6c7cd02480f78d19aed269b5d78d0c6f470621d2
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566443"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="c5c86-104">Referência: Manifesto esquema para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c5c86-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="c5c86-105">O manifesto Teams descreve como o aplicativo se integra ao produto Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="c5c86-105">The Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="c5c86-106">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="c5c86-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="c5c86-107">As versões anteriores 1.0, 1.1,..., 1.6 e assim por diante também são suportadas (usando "v1.x" na URL).</span><span class="sxs-lookup"><span data-stu-id="c5c86-107">Previous versions 1.0, 1.1,..., 1.6, and so on are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="c5c86-108">A seguinte amostra de esquema mostra todas as opções de extensibilidade:</span><span class="sxs-lookup"><span data-stu-id="c5c86-108">The following schema sample shows all extensibility options:</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="c5c86-109">Amostra de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="c5c86-109">Sample full manifest</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json",
  "manifestVersion": "1.10",
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
  },
  "defaultInstallScope": "meetings",
  "defaultGroupCapability": {
    "meetings": "tab", 
    "team": "bot", 
    "groupchat": "bot"
  },
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

<span data-ttu-id="c5c86-110">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c5c86-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="c5c86-111">$schema</span><span class="sxs-lookup"><span data-stu-id="c5c86-111">$schema</span></span>

<span data-ttu-id="c5c86-112">Opcional, mas recomendado — string</span><span class="sxs-lookup"><span data-stu-id="c5c86-112">Optional, but recommended — string</span></span>

<span data-ttu-id="c5c86-113">A URL https:// fazendo referência ao Esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="c5c86-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="c5c86-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="c5c86-114">manifestVersion</span></span>

<span data-ttu-id="c5c86-115">**Obrigatório** — string</span><span class="sxs-lookup"><span data-stu-id="c5c86-115">**Required** — string</span></span>

<span data-ttu-id="c5c86-116">A versão do esquema manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="c5c86-116">The version of manifest schema this manifest is using.</span></span> <span data-ttu-id="c5c86-117">Deve ser 1,10.</span><span class="sxs-lookup"><span data-stu-id="c5c86-117">It must be 1.10.</span></span>

## <a name="version"></a><span data-ttu-id="c5c86-118">versão</span><span class="sxs-lookup"><span data-stu-id="c5c86-118">version</span></span>

<span data-ttu-id="c5c86-119">**Obrigatório** — string</span><span class="sxs-lookup"><span data-stu-id="c5c86-119">**Required** — string</span></span>

<span data-ttu-id="c5c86-120">A versão de um aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="c5c86-120">The version of a specific app.</span></span> <span data-ttu-id="c5c86-121">Se você atualizar algo em seu manifesto, a versão deve ser incrementada também.</span><span class="sxs-lookup"><span data-stu-id="c5c86-121">If you update something in your manifest, the version must be incremented too.</span></span> <span data-ttu-id="c5c86-122">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="c5c86-122">This way, when the new manifest is installed, it overwrites the existing one and the user receives the new functionality.</span></span> <span data-ttu-id="c5c86-123">Se este aplicativo foi enviado à loja, o novo manifesto deve ser remetido e revalidado.</span><span class="sxs-lookup"><span data-stu-id="c5c86-123">If this app was submitted to the store, the new manifest must be re-submitted and re-validated.</span></span> <span data-ttu-id="c5c86-124">Os usuários do aplicativo recebem o novo manifesto atualizado automaticamente poucas horas após a aprovação do manifesto.</span><span class="sxs-lookup"><span data-stu-id="c5c86-124">The app users receive the new updated manifest automatically within few hours after the manifest is approved.</span></span>

<span data-ttu-id="c5c86-125">Se o aplicativo solicitar permissões mudar, os usuários ãovoquem e re consentam com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-125">If the app requests for permissions change, the users are prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="c5c86-126">Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (MAJOR. menor. PATCH).</span><span class="sxs-lookup"><span data-stu-id="c5c86-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="c5c86-127">id</span><span class="sxs-lookup"><span data-stu-id="c5c86-127">id</span></span>

<span data-ttu-id="c5c86-128">**Obrigatório** — ID do aplicativo da Microsoft</span><span class="sxs-lookup"><span data-stu-id="c5c86-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="c5c86-129">O ID é um identificador exclusivo gerado pela Microsoft para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-129">The ID is a unique Microsoft-generated identifier for the app.</span></span> <span data-ttu-id="c5c86-130">Você tem um ID se o seu bot estiver registrado através do Microsoft Bot Framework ou o aplicativo web da sua guia já entra na Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c5c86-130">You have an ID if your bot is registered through the Microsoft Bot Framework or your tab's web app already signs in with Microsoft.</span></span> <span data-ttu-id="c5c86-131">Você deve entrar na 19.</span><span class="sxs-lookup"><span data-stu-id="c5c86-131">You must enter the ID here.</span></span> <span data-ttu-id="c5c86-132">Caso contrário, você deve gerar um novo ID no [Portal de Registro de Aplicativos da Microsoft](https://aka.ms/appregistrations).</span><span class="sxs-lookup"><span data-stu-id="c5c86-132">Otherwise, you must generate a new ID at the [Microsoft Application Registration Portal](https://aka.ms/appregistrations).</span></span> <span data-ttu-id="c5c86-133">Use o mesmo ID se adicionar um bot.</span><span class="sxs-lookup"><span data-stu-id="c5c86-133">Use the same ID if you add a bot.</span></span>

> [!NOTE]
> <span data-ttu-id="c5c86-134">Se você estiver enviando uma atualização para o seu aplicativo existente no AppSource, o ID em seu manifesto não deve ser modificado.</span><span class="sxs-lookup"><span data-stu-id="c5c86-134">If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="c5c86-135">developer</span><span class="sxs-lookup"><span data-stu-id="c5c86-135">developer</span></span>

<span data-ttu-id="c5c86-136">**Necessário** — objeto</span><span class="sxs-lookup"><span data-stu-id="c5c86-136">**Required** — object</span></span>

<span data-ttu-id="c5c86-137">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="c5c86-137">Specifies information about your company.</span></span> <span data-ttu-id="c5c86-138">Para aplicativos submetidos à loja Teams, esses valores devem corresponder às informações na listagem da sua loja.</span><span class="sxs-lookup"><span data-stu-id="c5c86-138">For apps submitted to the Teams store, these values must match the information in your store listing.</span></span> <span data-ttu-id="c5c86-139">Para obter mais informações, consulte as [diretrizes de publicação de Teams loja](~/concepts/deploy-and-publish/appsource/publish.md).</span><span class="sxs-lookup"><span data-stu-id="c5c86-139">For more information, see the [Teams store publishing guidelines](~/concepts/deploy-and-publish/appsource/publish.md).</span></span>

|<span data-ttu-id="c5c86-140">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-140">Name</span></span>| <span data-ttu-id="c5c86-141">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-141">Maximum size</span></span> | <span data-ttu-id="c5c86-142">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-142">Required</span></span> | <span data-ttu-id="c5c86-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-143">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="c5c86-144">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-144">32 characters</span></span>|<span data-ttu-id="c5c86-145">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-145">✔</span></span>|<span data-ttu-id="c5c86-146">O nome de exibição para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="c5c86-146">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="c5c86-147">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-147">2048 characters</span></span>|<span data-ttu-id="c5c86-148">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-148">✔</span></span>|<span data-ttu-id="c5c86-149">O https:// URL para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="c5c86-149">The https:// URL to the developer's website.</span></span> <span data-ttu-id="c5c86-150">Este link deve levar os usuários para sua empresa ou página de landing específica do produto.</span><span class="sxs-lookup"><span data-stu-id="c5c86-150">This link must take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="c5c86-151">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-151">2048 characters</span></span>|<span data-ttu-id="c5c86-152">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-152">✔</span></span>|<span data-ttu-id="c5c86-153">O https:// URL para a política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="c5c86-153">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="c5c86-154">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-154">2048 characters</span></span>|<span data-ttu-id="c5c86-155">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-155">✔</span></span>|<span data-ttu-id="c5c86-156">O https:// URL para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="c5c86-156">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="c5c86-157">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-157">10 characters</span></span>| |<span data-ttu-id="c5c86-158">**Opcional** O Microsoft Partner Network ID que identifica a organização parceira que está construindo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-158">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="c5c86-159">nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-159">name</span></span>

<span data-ttu-id="c5c86-160">**Necessário** — objeto</span><span class="sxs-lookup"><span data-stu-id="c5c86-160">**Required** — object</span></span>

<span data-ttu-id="c5c86-161">O nome da experiência do seu aplicativo, exibido aos usuários na experiência Teams.</span><span class="sxs-lookup"><span data-stu-id="c5c86-161">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="c5c86-162">Para aplicativos submetidos ao AppSource, esses valores devem corresponder às informações na sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="c5c86-162">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="c5c86-163">Os valores `short` de e devem ser `full` diferentes.</span><span class="sxs-lookup"><span data-stu-id="c5c86-163">The values of `short` and `full` must be different.</span></span>

|<span data-ttu-id="c5c86-164">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-164">Name</span></span>| <span data-ttu-id="c5c86-165">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-165">Maximum size</span></span> | <span data-ttu-id="c5c86-166">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-166">Required</span></span> | <span data-ttu-id="c5c86-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-167">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="c5c86-168">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-168">30 characters</span></span>|<span data-ttu-id="c5c86-169">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-169">✔</span></span>|<span data-ttu-id="c5c86-170">O nome de exibição curto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-170">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="c5c86-171">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-171">100 characters</span></span>||<span data-ttu-id="c5c86-172">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="c5c86-172">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="c5c86-173">descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-173">description</span></span>

<span data-ttu-id="c5c86-174">**Necessário** — objeto</span><span class="sxs-lookup"><span data-stu-id="c5c86-174">**Required** — object</span></span>

<span data-ttu-id="c5c86-175">Descreve seu aplicativo para os usuários.</span><span class="sxs-lookup"><span data-stu-id="c5c86-175">Describes your app to users.</span></span> <span data-ttu-id="c5c86-176">Para aplicativos submetidos ao AppSource, esses valores devem corresponder às informações na sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="c5c86-176">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="c5c86-177">Certifique-se de que sua descrição descreve com precisão sua experiência e fornece informações para ajudar os clientes em potencial a entender o que sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="c5c86-177">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="c5c86-178">Você deve observar na descrição completa, se uma conta externa for necessária para uso.</span><span class="sxs-lookup"><span data-stu-id="c5c86-178">You must note in the full description, if an external account is required for use.</span></span> <span data-ttu-id="c5c86-179">Os valores `short` de e devem ser `full` diferentes.</span><span class="sxs-lookup"><span data-stu-id="c5c86-179">The values of `short` and `full` must be different.</span></span> <span data-ttu-id="c5c86-180">Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir qualquer outro nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-180">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="c5c86-181">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-181">Name</span></span>| <span data-ttu-id="c5c86-182">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-182">Maximum size</span></span> | <span data-ttu-id="c5c86-183">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-183">Required</span></span> | <span data-ttu-id="c5c86-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-184">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="c5c86-185">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-185">80 characters</span></span>|<span data-ttu-id="c5c86-186">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-186">✔</span></span>|<span data-ttu-id="c5c86-187">Uma breve descrição da sua experiência de aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="c5c86-187">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="c5c86-188">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-188">4000 characters</span></span>|<span data-ttu-id="c5c86-189">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-189">✔</span></span>|<span data-ttu-id="c5c86-190">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-190">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="c5c86-191">packageName</span><span class="sxs-lookup"><span data-stu-id="c5c86-191">packageName</span></span>

<span data-ttu-id="c5c86-192">**Opcional** — string</span><span class="sxs-lookup"><span data-stu-id="c5c86-192">**Optional** — string</span></span>

<span data-ttu-id="c5c86-193">Um identificador exclusivo para o aplicativo em notação de domínio reverso; por exemplo, com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="c5c86-193">A unique identifier for the app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="c5c86-194">Comprimento máximo: 64 caracteres.</span><span class="sxs-lookup"><span data-stu-id="c5c86-194">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="c5c86-195">localizaçãoInfo</span><span class="sxs-lookup"><span data-stu-id="c5c86-195">localizationInfo</span></span>

<span data-ttu-id="c5c86-196">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="c5c86-196">**Optional** — object</span></span>

<span data-ttu-id="c5c86-197">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="c5c86-197">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="c5c86-198">Para obter mais informações, consulte [localização.](~/concepts/build-and-test/apps-localization.md)</span><span class="sxs-lookup"><span data-stu-id="c5c86-198">For more information, see [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="c5c86-199">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-199">Name</span></span>| <span data-ttu-id="c5c86-200">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-200">Maximum size</span></span> | <span data-ttu-id="c5c86-201">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-201">Required</span></span> | <span data-ttu-id="c5c86-202">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-202">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="c5c86-203">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-203">✔</span></span>|<span data-ttu-id="c5c86-204">A tag de idioma das strings neste arquivo manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="c5c86-204">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="c5c86-205">localizaçãoInfo.additionalLíguas</span><span class="sxs-lookup"><span data-stu-id="c5c86-205">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="c5c86-206">Uma variedade de objetos especificando traduções adicionais de idiomas.</span><span class="sxs-lookup"><span data-stu-id="c5c86-206">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="c5c86-207">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-207">Name</span></span>| <span data-ttu-id="c5c86-208">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-208">Maximum size</span></span> | <span data-ttu-id="c5c86-209">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-209">Required</span></span> | <span data-ttu-id="c5c86-210">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-210">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="c5c86-211">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-211">✔</span></span>|<span data-ttu-id="c5c86-212">A tag de idioma das strings no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="c5c86-212">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="c5c86-213">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-213">✔</span></span>|<span data-ttu-id="c5c86-214">Um caminho relativo de arquivo para um arquivo .json contendo as strings traduzidas.</span><span class="sxs-lookup"><span data-stu-id="c5c86-214">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="c5c86-215">ícones</span><span class="sxs-lookup"><span data-stu-id="c5c86-215">icons</span></span>

<span data-ttu-id="c5c86-216">**Necessário** — objeto</span><span class="sxs-lookup"><span data-stu-id="c5c86-216">**Required** — object</span></span>

<span data-ttu-id="c5c86-217">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="c5c86-217">Icons used within the Teams app.</span></span> <span data-ttu-id="c5c86-218">Os arquivos de ícone devem ser incluídos como parte do pacote de upload.</span><span class="sxs-lookup"><span data-stu-id="c5c86-218">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="c5c86-219">Consulte [Ícones](../../concepts/build-and-test/apps-package.md#app-icons) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c5c86-219">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="c5c86-220">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-220">Name</span></span>| <span data-ttu-id="c5c86-221">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-221">Maximum size</span></span> | <span data-ttu-id="c5c86-222">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-222">Required</span></span> | <span data-ttu-id="c5c86-223">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="c5c86-224">32 x 32 pixels</span><span class="sxs-lookup"><span data-stu-id="c5c86-224">32 x 32 pixels</span></span>|<span data-ttu-id="c5c86-225">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-225">✔</span></span>|<span data-ttu-id="c5c86-226">Um caminho relativo de arquivo para um ícone transparente de contorno 32x32 PNG.</span><span class="sxs-lookup"><span data-stu-id="c5c86-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="c5c86-227">192 x 192 pixels</span><span class="sxs-lookup"><span data-stu-id="c5c86-227">192 x 192 pixels</span></span>|<span data-ttu-id="c5c86-228">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-228">✔</span></span>|<span data-ttu-id="c5c86-229">Um caminho relativo de arquivo para um ícone PNG de cor completa 192x192.</span><span class="sxs-lookup"><span data-stu-id="c5c86-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="c5c86-230">sotaqueColor</span><span class="sxs-lookup"><span data-stu-id="c5c86-230">accentColor</span></span>

<span data-ttu-id="c5c86-231">**Opcional** — Código de cor HTML Hex</span><span class="sxs-lookup"><span data-stu-id="c5c86-231">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="c5c86-232">Uma cor para usar em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="c5c86-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="c5c86-233">O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="c5c86-234">configurávelTabs</span><span class="sxs-lookup"><span data-stu-id="c5c86-234">configurableTabs</span></span>

<span data-ttu-id="c5c86-235">**Opcionais** — matriz</span><span class="sxs-lookup"><span data-stu-id="c5c86-235">**Optional** — array</span></span>

<span data-ttu-id="c5c86-236">Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="c5c86-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="c5c86-237">As guias configuráveis são suportadas apenas no escopo das equipes e você pode configurar as mesmas guias várias vezes.</span><span class="sxs-lookup"><span data-stu-id="c5c86-237">Configurable tabs are supported only in the teams scope and you can configure the same tabs multiple times.</span></span> <span data-ttu-id="c5c86-238">No entanto, você pode defini-lo no manifesto apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="c5c86-238">However, you can define it in the manifest only once.</span></span>

|<span data-ttu-id="c5c86-239">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-239">Name</span></span>| <span data-ttu-id="c5c86-240">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-240">Type</span></span>| <span data-ttu-id="c5c86-241">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-241">Maximum size</span></span> | <span data-ttu-id="c5c86-242">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-242">Required</span></span> | <span data-ttu-id="c5c86-243">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-243">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="c5c86-244">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-244">string</span></span>|<span data-ttu-id="c5c86-245">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-245">2048 characters</span></span>|<span data-ttu-id="c5c86-246">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-246">✔</span></span>|<span data-ttu-id="c5c86-247">A https:// URL a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="c5c86-247">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="c5c86-248">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="c5c86-248">array of enums</span></span>|<span data-ttu-id="c5c86-249">1</span><span class="sxs-lookup"><span data-stu-id="c5c86-249">1</span></span>|<span data-ttu-id="c5c86-250">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-250">✔</span></span>|<span data-ttu-id="c5c86-251">Atualmente, as guias configuráveis suportam apenas os `team` `groupchat` escopos e escopos.</span><span class="sxs-lookup"><span data-stu-id="c5c86-251">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="c5c86-252">booliano</span><span class="sxs-lookup"><span data-stu-id="c5c86-252">boolean</span></span>|||<span data-ttu-id="c5c86-253">Um valor indicando se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="c5c86-253">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="c5c86-254">Padrão: **verdadeiro**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-254">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="c5c86-255">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="c5c86-255">array of enums</span></span>|<span data-ttu-id="c5c86-256">6 </span><span class="sxs-lookup"><span data-stu-id="c5c86-256">6</span></span>||<span data-ttu-id="c5c86-257">O conjunto de `contextItem` escopos onde uma [guia é suportada](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="c5c86-257">The set of `contextItem` scopes where a [tab is supported](../../tabs/how-to/access-teams-context.md).</span></span> <span data-ttu-id="c5c86-258">Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-258">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="c5c86-259">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-259">string</span></span>|<span data-ttu-id="c5c86-260">2048</span><span class="sxs-lookup"><span data-stu-id="c5c86-260">2048</span></span>||<span data-ttu-id="c5c86-261">Um caminho relativo de arquivo para uma imagem de visualização de guia para uso em SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c5c86-261">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="c5c86-262">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="c5c86-262">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="c5c86-263">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="c5c86-263">array of enums</span></span>|<span data-ttu-id="c5c86-264">1</span><span class="sxs-lookup"><span data-stu-id="c5c86-264">1</span></span>||<span data-ttu-id="c5c86-265">Define como sua guia é disponibilizada em SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c5c86-265">Defines how your tab is made available in SharePoint.</span></span> <span data-ttu-id="c5c86-266">As opções são `sharePointFullPage` e `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="c5c86-266">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="c5c86-267">staticTabs</span><span class="sxs-lookup"><span data-stu-id="c5c86-267">staticTabs</span></span>

<span data-ttu-id="c5c86-268">**Opcionais** — matriz</span><span class="sxs-lookup"><span data-stu-id="c5c86-268">**Optional** — array</span></span>

<span data-ttu-id="c5c86-269">Define um conjunto de guias que podem ser "fixadas" por padrão, sem que o usuário as adicione manualmente.</span><span class="sxs-lookup"><span data-stu-id="c5c86-269">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="c5c86-270">As guias estáticas declaradas no `personal` escopo são sempre fixadas à experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-270">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="c5c86-271">As guias estáticas declaradas no `team` escopo não são suportadas no momento.</span><span class="sxs-lookup"><span data-stu-id="c5c86-271">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="c5c86-272">Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-272">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="c5c86-273">Este bloco é necessário apenas para soluções que forneçam uma solução de guia estática.</span><span class="sxs-lookup"><span data-stu-id="c5c86-273">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="c5c86-274">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-274">Name</span></span>| <span data-ttu-id="c5c86-275">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-275">Type</span></span>| <span data-ttu-id="c5c86-276">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-276">Maximum size</span></span> | <span data-ttu-id="c5c86-277">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-277">Required</span></span> | <span data-ttu-id="c5c86-278">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-278">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="c5c86-279">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-279">string</span></span>|<span data-ttu-id="c5c86-280">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-280">64 characters</span></span>|<span data-ttu-id="c5c86-281">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-281">✔</span></span>|<span data-ttu-id="c5c86-282">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="c5c86-282">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="c5c86-283">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-283">string</span></span>|<span data-ttu-id="c5c86-284">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-284">128 characters</span></span>|<span data-ttu-id="c5c86-285">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-285">✔</span></span>|<span data-ttu-id="c5c86-286">O nome de exibição da guia na interface do canal.</span><span class="sxs-lookup"><span data-stu-id="c5c86-286">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="c5c86-287">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-287">string</span></span>||<span data-ttu-id="c5c86-288">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-288">✔</span></span>|<span data-ttu-id="c5c86-289">A url https:// que aponta para a interface do usuário da entidade a ser exibida na tela Teams.</span><span class="sxs-lookup"><span data-stu-id="c5c86-289">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="c5c86-290">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-290">string</span></span>|||<span data-ttu-id="c5c86-291">O https:// URL para apontar se um usuário opta por visualizar em um navegador.</span><span class="sxs-lookup"><span data-stu-id="c5c86-291">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="c5c86-292">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-292">string</span></span>|||<span data-ttu-id="c5c86-293">O https:// URL para apontar para consultas de pesquisa de um usuário.</span><span class="sxs-lookup"><span data-stu-id="c5c86-293">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="c5c86-294">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="c5c86-294">array of enums</span></span>|<span data-ttu-id="c5c86-295">1</span><span class="sxs-lookup"><span data-stu-id="c5c86-295">1</span></span>|<span data-ttu-id="c5c86-296">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-296">✔</span></span>|<span data-ttu-id="c5c86-297">Atualmente, as guias estáticas suportam apenas o escopo, o `personal` que significa que ele só pode ser provisionado como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="c5c86-297">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="c5c86-298">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="c5c86-298">array of enums</span></span>| <span data-ttu-id="c5c86-299">2</span><span class="sxs-lookup"><span data-stu-id="c5c86-299">2</span></span>|| <span data-ttu-id="c5c86-300">O conjunto de `contextItem` escopos onde uma guia é suportada.</span><span class="sxs-lookup"><span data-stu-id="c5c86-300">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
>  <span data-ttu-id="c5c86-301">O recurso searchUrl não está disponível para desenvolvedores de terceiros.</span><span class="sxs-lookup"><span data-stu-id="c5c86-301">The searchUrl feature is not available for the third-party developers.</span></span>
> <span data-ttu-id="c5c86-302">Se suas guias exigirem informações dependentes do contexto para exibir conteúdo relevante ou para iniciar um fluxo de autenticação, Para obter mais informações, consulte [Obter contexto para sua guia Microsoft Teams](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="c5c86-302">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, For more information, see [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="c5c86-303">Bots</span><span class="sxs-lookup"><span data-stu-id="c5c86-303">bots</span></span>

<span data-ttu-id="c5c86-304">**Opcionais** — matriz</span><span class="sxs-lookup"><span data-stu-id="c5c86-304">**Optional** — array</span></span>

<span data-ttu-id="c5c86-305">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="c5c86-305">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="c5c86-306">O item é uma matriz (no máximo 1 elemento &mdash; atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-306">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="c5c86-307">Este bloco é necessário apenas para soluções que forneçam uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="c5c86-307">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="c5c86-308">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-308">Name</span></span>| <span data-ttu-id="c5c86-309">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-309">Type</span></span>| <span data-ttu-id="c5c86-310">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-310">Maximum size</span></span> | <span data-ttu-id="c5c86-311">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-311">Required</span></span> | <span data-ttu-id="c5c86-312">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-312">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="c5c86-313">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-313">string</span></span>|<span data-ttu-id="c5c86-314">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-314">64 characters</span></span>|<span data-ttu-id="c5c86-315">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-315">✔</span></span>|<span data-ttu-id="c5c86-316">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="c5c86-316">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="c5c86-317">Isso pode muito bem ser o mesmo que o [ID](#id)geral do aplicativo .</span><span class="sxs-lookup"><span data-stu-id="c5c86-317">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="c5c86-318">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="c5c86-318">array of enums</span></span>|<span data-ttu-id="c5c86-319">3</span><span class="sxs-lookup"><span data-stu-id="c5c86-319">3</span></span>|<span data-ttu-id="c5c86-320">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-320">✔</span></span>|<span data-ttu-id="c5c86-321">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="c5c86-321">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="c5c86-322">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="c5c86-322">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="c5c86-323">booliano</span><span class="sxs-lookup"><span data-stu-id="c5c86-323">boolean</span></span>|||<span data-ttu-id="c5c86-324">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="c5c86-324">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="c5c86-325">inadimplência: **`false`**</span><span class="sxs-lookup"><span data-stu-id="c5c86-325">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="c5c86-326">booliano</span><span class="sxs-lookup"><span data-stu-id="c5c86-326">boolean</span></span>|||<span data-ttu-id="c5c86-327">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="c5c86-327">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="c5c86-328">inadimplência: **`false`**</span><span class="sxs-lookup"><span data-stu-id="c5c86-328">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="c5c86-329">booliano</span><span class="sxs-lookup"><span data-stu-id="c5c86-329">boolean</span></span>|||<span data-ttu-id="c5c86-330">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="c5c86-330">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="c5c86-331">inadimplência: **`false`**</span><span class="sxs-lookup"><span data-stu-id="c5c86-331">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="c5c86-332">booliano</span><span class="sxs-lookup"><span data-stu-id="c5c86-332">boolean</span></span>|||<span data-ttu-id="c5c86-333">Um valor indicando onde um bot suporta chamadas de áudio.</span><span class="sxs-lookup"><span data-stu-id="c5c86-333">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="c5c86-334">**IMPORTANTE**: Esta propriedade é atualmente experimental.</span><span class="sxs-lookup"><span data-stu-id="c5c86-334">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="c5c86-335">As propriedades experimentais podem não estar completas e podem sofrer alterações antes de ficarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c5c86-335">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="c5c86-336">Está previsto apenas para fins de teste e exploração e não deve ser utilizado em aplicações de produção.</span><span class="sxs-lookup"><span data-stu-id="c5c86-336">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="c5c86-337">inadimplência: **`false`**</span><span class="sxs-lookup"><span data-stu-id="c5c86-337">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="c5c86-338">booliano</span><span class="sxs-lookup"><span data-stu-id="c5c86-338">boolean</span></span>|||<span data-ttu-id="c5c86-339">Um valor indicando onde um bot suporta chamadas de vídeo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-339">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="c5c86-340">**IMPORTANTE**: Esta propriedade é atualmente experimental.</span><span class="sxs-lookup"><span data-stu-id="c5c86-340">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="c5c86-341">As propriedades experimentais podem não estar completas e podem sofrer alterações antes de ficarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c5c86-341">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="c5c86-342">Está previsto apenas para fins de teste e exploração e não deve ser utilizado em aplicações de produção.</span><span class="sxs-lookup"><span data-stu-id="c5c86-342">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="c5c86-343">inadimplência: **`false`**</span><span class="sxs-lookup"><span data-stu-id="c5c86-343">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="c5c86-344">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="c5c86-344">bots.commandLists</span></span>

<span data-ttu-id="c5c86-345">Uma lista opcional de comandos que o bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="c5c86-345">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="c5c86-346">O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo ; você deve definir uma lista de `object` comando separada para cada escopo que o seu bot suporta.</span><span class="sxs-lookup"><span data-stu-id="c5c86-346">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="c5c86-347">Consulte [menus bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c5c86-347">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="c5c86-348">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-348">Name</span></span>| <span data-ttu-id="c5c86-349">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-349">Type</span></span>| <span data-ttu-id="c5c86-350">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-350">Maximum size</span></span> | <span data-ttu-id="c5c86-351">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-351">Required</span></span> | <span data-ttu-id="c5c86-352">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-352">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="c5c86-353">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="c5c86-353">array of enums</span></span>|<span data-ttu-id="c5c86-354">3</span><span class="sxs-lookup"><span data-stu-id="c5c86-354">3</span></span>|<span data-ttu-id="c5c86-355">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-355">✔</span></span>|<span data-ttu-id="c5c86-356">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="c5c86-356">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="c5c86-357">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="c5c86-357">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="c5c86-358">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="c5c86-358">array of objects</span></span>|<span data-ttu-id="c5c86-359">10 </span><span class="sxs-lookup"><span data-stu-id="c5c86-359">10</span></span>|<span data-ttu-id="c5c86-360">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-360">✔</span></span>|<span data-ttu-id="c5c86-361">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="c5c86-361">An array of commands the bot supports:</span></span><br><span data-ttu-id="c5c86-362">`title`: o nome do comando bot (cadeia, 32)</span><span class="sxs-lookup"><span data-stu-id="c5c86-362">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="c5c86-363">`description`: uma descrição simples ou exemplo da sintaxe de comando e seu argumento (string, 128).</span><span class="sxs-lookup"><span data-stu-id="c5c86-363">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="c5c86-364">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="c5c86-364">bots.commandLists.commands</span></span>

|<span data-ttu-id="c5c86-365">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-365">Name</span></span>| <span data-ttu-id="c5c86-366">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-366">Type</span></span>| <span data-ttu-id="c5c86-367">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-367">Maximum size</span></span> | <span data-ttu-id="c5c86-368">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-368">Required</span></span> | <span data-ttu-id="c5c86-369">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-369">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="c5c86-370">title</span><span class="sxs-lookup"><span data-stu-id="c5c86-370">title</span></span>|<span data-ttu-id="c5c86-371">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-371">string</span></span>|<span data-ttu-id="c5c86-372">12 </span><span class="sxs-lookup"><span data-stu-id="c5c86-372">12</span></span>|<span data-ttu-id="c5c86-373">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-373">✔</span></span>|<span data-ttu-id="c5c86-374">O nome do comando do bot.</span><span class="sxs-lookup"><span data-stu-id="c5c86-374">The bot command name.</span></span>|
|<span data-ttu-id="c5c86-375">description</span><span class="sxs-lookup"><span data-stu-id="c5c86-375">description</span></span>|<span data-ttu-id="c5c86-376">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-376">string</span></span>|<span data-ttu-id="c5c86-377">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-377">128 characters</span></span>|<span data-ttu-id="c5c86-378">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-378">✔</span></span>|<span data-ttu-id="c5c86-379">Uma simples descrição de texto ou um exemplo da sintaxe de comando e seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="c5c86-379">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="c5c86-380">Conectores</span><span class="sxs-lookup"><span data-stu-id="c5c86-380">connectors</span></span>

<span data-ttu-id="c5c86-381">**Opcionais** — matriz</span><span class="sxs-lookup"><span data-stu-id="c5c86-381">**Optional** — array</span></span>

<span data-ttu-id="c5c86-382">O `connectors` bloco define um conector de Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-382">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="c5c86-383">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-383">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="c5c86-384">Este bloco é necessário apenas para soluções que forneçam um Conector.</span><span class="sxs-lookup"><span data-stu-id="c5c86-384">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="c5c86-385">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-385">Name</span></span>| <span data-ttu-id="c5c86-386">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-386">Type</span></span>| <span data-ttu-id="c5c86-387">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-387">Maximum size</span></span> | <span data-ttu-id="c5c86-388">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-388">Required</span></span> | <span data-ttu-id="c5c86-389">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-389">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="c5c86-390">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-390">string</span></span>|<span data-ttu-id="c5c86-391">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-391">2048 characters</span></span>|<span data-ttu-id="c5c86-392">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-392">✔</span></span>|<span data-ttu-id="c5c86-393">A https:// URL para usar ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="c5c86-393">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="c5c86-394">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="c5c86-394">array of enums</span></span>|<span data-ttu-id="c5c86-395">1</span><span class="sxs-lookup"><span data-stu-id="c5c86-395">1</span></span>|<span data-ttu-id="c5c86-396">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-396">✔</span></span>|<span data-ttu-id="c5c86-397">Especifica se o Conector oferece uma experiência no contexto de um canal em um `team` , ou uma experiência escopo para um usuário individual `personal` ().</span><span class="sxs-lookup"><span data-stu-id="c5c86-397">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="c5c86-398">Atualmente, apenas o `team` escopo é suportado.</span><span class="sxs-lookup"><span data-stu-id="c5c86-398">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="c5c86-399">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-399">string</span></span>|<span data-ttu-id="c5c86-400">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-400">64 characters</span></span>|<span data-ttu-id="c5c86-401">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-401">✔</span></span>|<span data-ttu-id="c5c86-402">Um identificador exclusivo para o Conector que corresponde ao seu ID no [Painel de Desenvolvedores de Conectores](https://aka.ms/connectorsdashboard).</span><span class="sxs-lookup"><span data-stu-id="c5c86-402">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="c5c86-403">comporTensões</span><span class="sxs-lookup"><span data-stu-id="c5c86-403">composeExtensions</span></span>

<span data-ttu-id="c5c86-404">**Opcionais** — matriz</span><span class="sxs-lookup"><span data-stu-id="c5c86-404">**Optional** — array</span></span>

<span data-ttu-id="c5c86-405">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-405">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="c5c86-406">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome manifesto permanece o mesmo para que as extensões existentes continuem funcionando.</span><span class="sxs-lookup"><span data-stu-id="c5c86-406">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="c5c86-407">O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-407">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="c5c86-408">Este bloco é necessário apenas para soluções que forneçam uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c5c86-408">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="c5c86-409">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-409">Name</span></span>| <span data-ttu-id="c5c86-410">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-410">Type</span></span> | <span data-ttu-id="c5c86-411">Tamanho Máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-411">Maximum Size</span></span> | <span data-ttu-id="c5c86-412">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-412">Required</span></span> | <span data-ttu-id="c5c86-413">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-413">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="c5c86-414">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-414">string</span></span>|<span data-ttu-id="c5c86-415">64</span><span class="sxs-lookup"><span data-stu-id="c5c86-415">64</span></span>|<span data-ttu-id="c5c86-416">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-416">✔</span></span>|<span data-ttu-id="c5c86-417">O ID exclusivo do aplicativo da Microsoft para o bot que apoia a extensão de mensagens, como registrado no Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="c5c86-417">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="c5c86-418">Isso pode muito bem ser o mesmo que o ID geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-418">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="c5c86-419">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="c5c86-419">array of objects</span></span>|<span data-ttu-id="c5c86-420">10 </span><span class="sxs-lookup"><span data-stu-id="c5c86-420">10</span></span>|<span data-ttu-id="c5c86-421">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-421">✔</span></span>|<span data-ttu-id="c5c86-422">Matriz de comandos que a extensão de mensagens suporta.</span><span class="sxs-lookup"><span data-stu-id="c5c86-422">Array of commands the messaging extension supports.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="c5c86-423">booliano</span><span class="sxs-lookup"><span data-stu-id="c5c86-423">boolean</span></span>|||<span data-ttu-id="c5c86-424">Um valor indicando se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c5c86-424">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="c5c86-425">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-425">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="c5c86-426">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="c5c86-426">array of Objects</span></span>|<span data-ttu-id="c5c86-427">5 </span><span class="sxs-lookup"><span data-stu-id="c5c86-427">5</span></span>||<span data-ttu-id="c5c86-428">Uma lista de manipuladores que permitem que os aplicativos sejam invocados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="c5c86-428">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="c5c86-429">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-429">string</span></span>|||<span data-ttu-id="c5c86-430">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c5c86-430">The type of message handler.</span></span> <span data-ttu-id="c5c86-431">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="c5c86-431">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="c5c86-432">matriz de Strings</span><span class="sxs-lookup"><span data-stu-id="c5c86-432">array of Strings</span></span>|||<span data-ttu-id="c5c86-433">Matriz de domínios para os que o manipulador de mensagens de link pode registrar.</span><span class="sxs-lookup"><span data-stu-id="c5c86-433">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="c5c86-434">comporExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="c5c86-434">composeExtensions.commands</span></span>

<span data-ttu-id="c5c86-435">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="c5c86-435">Your messaging extension must declare one or more commands.</span></span> <span data-ttu-id="c5c86-436">Cada comando aparece em Microsoft Teams como uma interação potencial do ponto de entrada baseado em interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="c5c86-436">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="c5c86-437">Há um máximo de 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="c5c86-437">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="c5c86-438">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="c5c86-438">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="c5c86-439">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-439">Name</span></span>| <span data-ttu-id="c5c86-440">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-440">Type</span></span>| <span data-ttu-id="c5c86-441">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-441">Maximum size</span></span> | <span data-ttu-id="c5c86-442">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-442">Required</span></span> | <span data-ttu-id="c5c86-443">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-443">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="c5c86-444">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-444">string</span></span>|<span data-ttu-id="c5c86-445">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-445">64 characters</span></span>|<span data-ttu-id="c5c86-446">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-446">✔</span></span>|<span data-ttu-id="c5c86-447">A responsabilidade pelo comando.</span><span class="sxs-lookup"><span data-stu-id="c5c86-447">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="c5c86-448">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-448">string</span></span>|<span data-ttu-id="c5c86-449">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-449">32 characters</span></span>|<span data-ttu-id="c5c86-450">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-450">✔</span></span>|<span data-ttu-id="c5c86-451">O nome de comando fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="c5c86-451">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="c5c86-452">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-452">string</span></span>|<span data-ttu-id="c5c86-453">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-453">64 characters</span></span>||<span data-ttu-id="c5c86-454">Tipo de comando.</span><span class="sxs-lookup"><span data-stu-id="c5c86-454">Type of the command.</span></span> <span data-ttu-id="c5c86-455">Um de `query` ou `action` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-455">One of `query` or `action`.</span></span> <span data-ttu-id="c5c86-456">Padrão: **consulta**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-456">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="c5c86-457">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-457">string</span></span>|<span data-ttu-id="c5c86-458">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-458">128 characters</span></span>||<span data-ttu-id="c5c86-459">A descrição que aparece aos usuários para indicar o propósito deste comando.</span><span class="sxs-lookup"><span data-stu-id="c5c86-459">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="c5c86-460">booliano</span><span class="sxs-lookup"><span data-stu-id="c5c86-460">boolean</span></span>|||<span data-ttu-id="c5c86-461">Um valor booleano indica se o comando é executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c5c86-461">A boolean value indicates whether the command runs initially with no parameters.</span></span> <span data-ttu-id="c5c86-462">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-462">Default is **false**.</span></span>|
|`context`|<span data-ttu-id="c5c86-463">matriz de Strings</span><span class="sxs-lookup"><span data-stu-id="c5c86-463">array of Strings</span></span>|<span data-ttu-id="c5c86-464">3</span><span class="sxs-lookup"><span data-stu-id="c5c86-464">3</span></span>||<span data-ttu-id="c5c86-465">Define de onde a extensão da mensagem pode ser invocada.</span><span class="sxs-lookup"><span data-stu-id="c5c86-465">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="c5c86-466">Qualquer combinação `compose` `commandBox` de, `message` . .</span><span class="sxs-lookup"><span data-stu-id="c5c86-466">Any combination of`compose`,`commandBox`,`message`.</span></span> <span data-ttu-id="c5c86-467">O padrão é `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="c5c86-467">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="c5c86-468">booliano</span><span class="sxs-lookup"><span data-stu-id="c5c86-468">boolean</span></span>|||<span data-ttu-id="c5c86-469">Um valor booleano que indica se ele deve buscar o módulo de tarefa dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="c5c86-469">A boolean value that indicates if it must fetch the task module dynamically.</span></span> <span data-ttu-id="c5c86-470">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-470">Default is **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="c5c86-471">objeto</span><span class="sxs-lookup"><span data-stu-id="c5c86-471">object</span></span>|||<span data-ttu-id="c5c86-472">Especifique o módulo de tarefa para pré-carregar ao usar um comando de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c5c86-472">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="c5c86-473">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-473">string</span></span>|<span data-ttu-id="c5c86-474">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-474">64 characters</span></span>||<span data-ttu-id="c5c86-475">Título de diálogo inicial.</span><span class="sxs-lookup"><span data-stu-id="c5c86-475">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="c5c86-476">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-476">string</span></span>|||<span data-ttu-id="c5c86-477">Largura de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.</span><span class="sxs-lookup"><span data-stu-id="c5c86-477">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="c5c86-478">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-478">string</span></span>|||<span data-ttu-id="c5c86-479">Altura de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.</span><span class="sxs-lookup"><span data-stu-id="c5c86-479">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="c5c86-480">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-480">string</span></span>|||<span data-ttu-id="c5c86-481">URL inicial do webview.</span><span class="sxs-lookup"><span data-stu-id="c5c86-481">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="c5c86-482">matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="c5c86-482">array of object</span></span>|<span data-ttu-id="c5c86-483">5 itens</span><span class="sxs-lookup"><span data-stu-id="c5c86-483">5 items</span></span>|<span data-ttu-id="c5c86-484">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-484">✔</span></span>|<span data-ttu-id="c5c86-485">A lista de parâmetros que o comando toma.</span><span class="sxs-lookup"><span data-stu-id="c5c86-485">The list of parameters the command takes.</span></span> <span data-ttu-id="c5c86-486">Mínimo: 1; máximo: 5.</span><span class="sxs-lookup"><span data-stu-id="c5c86-486">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="c5c86-487">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-487">string</span></span>|<span data-ttu-id="c5c86-488">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-488">64 characters</span></span>|<span data-ttu-id="c5c86-489">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-489">✔</span></span>|<span data-ttu-id="c5c86-490">O nome do parâmetro como aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="c5c86-490">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="c5c86-491">Isso está incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="c5c86-491">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="c5c86-492">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-492">string</span></span>|<span data-ttu-id="c5c86-493">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-493">32 characters</span></span>|<span data-ttu-id="c5c86-494">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-494">✔</span></span>|<span data-ttu-id="c5c86-495">Título fácil de usar para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c5c86-495">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="c5c86-496">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-496">string</span></span>|<span data-ttu-id="c5c86-497">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-497">128 characters</span></span>||<span data-ttu-id="c5c86-498">String fácil de usar que descreve o propósito deste parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c5c86-498">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="c5c86-499">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-499">string</span></span>|<span data-ttu-id="c5c86-500">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-500">512 characters</span></span>||<span data-ttu-id="c5c86-501">Valor inicial para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c5c86-501">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="c5c86-502">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-502">string</span></span>|<span data-ttu-id="c5c86-503">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-503">128 characters</span></span>||<span data-ttu-id="c5c86-504">Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-504">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="c5c86-505">Um `text, textarea, number, date, time, toggle, choiceset` de.</span><span class="sxs-lookup"><span data-stu-id="c5c86-505">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="c5c86-506">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="c5c86-506">array of objects</span></span>|<span data-ttu-id="c5c86-507">10 itens</span><span class="sxs-lookup"><span data-stu-id="c5c86-507">10 items</span></span>||<span data-ttu-id="c5c86-508">As opções de escolha para o `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-508">The choice options for the`choiceset`.</span></span> <span data-ttu-id="c5c86-509">Use somente quando `parameter.inputType` estiver `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-509">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="c5c86-510">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-510">string</span></span>|<span data-ttu-id="c5c86-511">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-511">128 characters</span></span>|<span data-ttu-id="c5c86-512">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-512">✔</span></span>|<span data-ttu-id="c5c86-513">O título da escolha.</span><span class="sxs-lookup"><span data-stu-id="c5c86-513">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="c5c86-514">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-514">string</span></span>|<span data-ttu-id="c5c86-515">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-515">512 characters</span></span>|<span data-ttu-id="c5c86-516">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-516">✔</span></span>|<span data-ttu-id="c5c86-517">O valor da escolha.</span><span class="sxs-lookup"><span data-stu-id="c5c86-517">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="c5c86-518">permissões</span><span class="sxs-lookup"><span data-stu-id="c5c86-518">permissions</span></span>

<span data-ttu-id="c5c86-519">**Opcional** — matriz de cordas</span><span class="sxs-lookup"><span data-stu-id="c5c86-519">**Optional** — array of strings</span></span>

<span data-ttu-id="c5c86-520">Um conjunto especifica `string` quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão se sai.</span><span class="sxs-lookup"><span data-stu-id="c5c86-520">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension performs.</span></span> <span data-ttu-id="c5c86-521">As seguintes opções não são exclusivas:</span><span class="sxs-lookup"><span data-stu-id="c5c86-521">The following options are non-exclusive:</span></span>

* <span data-ttu-id="c5c86-522">`identity`&emsp;Requer informações de identidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="c5c86-522">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="c5c86-523">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="c5c86-523">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="c5c86-524">Alterar essas permissões durante a atualização do aplicativo faz com que seus usuários repitam o processo de consentimento depois de executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="c5c86-524">Changing these permissions during app update, causes your users to repeat the consent process after they run the updated app.</span></span> <span data-ttu-id="c5c86-525">Consulte [Atualizando seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c5c86-525">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="c5c86-526">dispositivosPermissões</span><span class="sxs-lookup"><span data-stu-id="c5c86-526">devicePermissions</span></span>

<span data-ttu-id="c5c86-527">**Opcional** — matriz de cordas</span><span class="sxs-lookup"><span data-stu-id="c5c86-527">**Optional** — array of strings</span></span>

<span data-ttu-id="c5c86-528">Fornece os recursos nativos no dispositivo do usuário ao que seu aplicativo solicita acesso.</span><span class="sxs-lookup"><span data-stu-id="c5c86-528">Provides the native features on a user's device that your app requests access to.</span></span> <span data-ttu-id="c5c86-529">As opções são:</span><span class="sxs-lookup"><span data-stu-id="c5c86-529">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="c5c86-530">validDomains</span><span class="sxs-lookup"><span data-stu-id="c5c86-530">validDomains</span></span>

<span data-ttu-id="c5c86-531">**Opcional,** exceto **Necessário** quando observado.</span><span class="sxs-lookup"><span data-stu-id="c5c86-531">**Optional**, except **Required** where noted.</span></span>

<span data-ttu-id="c5c86-532">Uma lista de domínios válidos para sites que o aplicativo espera carregar dentro do Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="c5c86-532">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="c5c86-533">As listagens de domínio podem incluir curingas, por `*.example.com` exemplo, .</span><span class="sxs-lookup"><span data-stu-id="c5c86-533">Domain listings can include wildcards, for example, `*.example.com`.</span></span> <span data-ttu-id="c5c86-534">Isso corresponde exatamente a um segmento do domínio; se você precisar `a.b.example.com` combinar, então use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-534">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="c5c86-535">Se a configuração da guia ou a interface do conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de guia, esse domínio deve ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="c5c86-535">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="c5c86-536">**Não** é necessário incluir os domínios dos provedores de identidade que você deseja suportar em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-536">It is **not** necessary to include the domains of identity providers you want to support in your app.</span></span> <span data-ttu-id="c5c86-537">Por exemplo, para autenticar usando um ID do Google, é necessário redirecionar para accounts.google.com, no entanto, você não deve incluir accounts.google.com em `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-537">For example, to authenticate using a Google ID, it is required to redirect to accounts.google.com, however, you must not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="c5c86-538">Teams aplicativos que exigem que seus próprios URLs de ponto de compartilhamento funcionem bem, inclui "{teamsitedomain}" em sua lista de domínios válida.</span><span class="sxs-lookup"><span data-stu-id="c5c86-538">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5c86-539">Não adicione domínios que estejam fora do seu controle, diretamente ou através de curingas.</span><span class="sxs-lookup"><span data-stu-id="c5c86-539">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="c5c86-540">Por exemplo, `yourapp.onmicrosoft.com` é válido, no entanto, `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="c5c86-540">For example, `yourapp.onmicrosoft.com` is valid, however, `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="c5c86-541">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-541">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="c5c86-542">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="c5c86-542">webApplicationInfo</span></span>

<span data-ttu-id="c5c86-543">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="c5c86-543">**Optional** — object</span></span>

<span data-ttu-id="c5c86-544">Forneça informações sobre o aplicativo Azure Active Directory (AAD) e a Microsoft Graph para ajudar os usuários a entrar em seu aplicativo perfeitamente.</span><span class="sxs-lookup"><span data-stu-id="c5c86-544">Provide your Azure Active Directory (AAD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="c5c86-545">Se o seu aplicativo estiver registrado no AAD, você deve fornecer o ID do aplicativo, para que os administradores possam facilmente rever permissões e conceder consentimento em Teams centro administrativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-545">If your app is registered in AAD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="c5c86-546">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-546">Name</span></span>| <span data-ttu-id="c5c86-547">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-547">Type</span></span>| <span data-ttu-id="c5c86-548">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-548">Maximum size</span></span> | <span data-ttu-id="c5c86-549">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-549">Required</span></span> | <span data-ttu-id="c5c86-550">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-550">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="c5c86-551">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-551">string</span></span>|<span data-ttu-id="c5c86-552">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-552">36 characters</span></span>|<span data-ttu-id="c5c86-553">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-553">✔</span></span>|<span data-ttu-id="c5c86-554">ID de aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-554">AAD application id of the app.</span></span> <span data-ttu-id="c5c86-555">Esta id deve ser uma GUID.</span><span class="sxs-lookup"><span data-stu-id="c5c86-555">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="c5c86-556">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-556">string</span></span>|<span data-ttu-id="c5c86-557">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-557">2048 characters</span></span>|<span data-ttu-id="c5c86-558">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-558">✔</span></span>|<span data-ttu-id="c5c86-559">URL de recurso do aplicativo para aquisição de token auth para SSO.</span><span class="sxs-lookup"><span data-stu-id="c5c86-559">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="c5c86-560">**NOTA:** Se você não estiver usando o SSO, certifique-se de inserir um valor de sequência de caracteres falso neste campo no manifesto do seu aplicativo, por exemplo, https://notapplicable para evitar uma resposta de erro.</span><span class="sxs-lookup"><span data-stu-id="c5c86-560">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="c5c86-561">matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-561">array of strings</span></span>|<span data-ttu-id="c5c86-562">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-562">128 characters</span></span>||<span data-ttu-id="c5c86-563">Especifique [o consentimento específico do recurso](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)granular .</span><span class="sxs-lookup"><span data-stu-id="c5c86-563">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="c5c86-564">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="c5c86-564">showLoadingIndicator</span></span>

<span data-ttu-id="c5c86-565">**Opcional** — booleano</span><span class="sxs-lookup"><span data-stu-id="c5c86-565">**Optional** — boolean</span></span>

<span data-ttu-id="c5c86-566">Indica se deve ou não mostrar o indicador de carregamento quando um aplicativo ou guia está carregando.</span><span class="sxs-lookup"><span data-stu-id="c5c86-566">Indicates whether or not to show the loading indicator when an app or tab is loading.</span></span> <span data-ttu-id="c5c86-567">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-567">Default is **false**.</span></span>
>[!NOTE]
><span data-ttu-id="c5c86-568">Se você selecionar `showLoadingIndicator` como verdadeiro no manifesto do aplicativo, para carregar a página corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa, conforme descrito em Mostrar um documento indicador de carregamento [nativo.](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)</span><span class="sxs-lookup"><span data-stu-id="c5c86-568">If you select`showLoadingIndicator` as true in your app manifest, to load the page correctly, modify the content pages of your tabs and task modules as described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="c5c86-569">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="c5c86-569">isFullScreen</span></span>

 <span data-ttu-id="c5c86-570">**Opcional** — booleano</span><span class="sxs-lookup"><span data-stu-id="c5c86-570">**Optional** — boolean</span></span>

<span data-ttu-id="c5c86-571">Indique onde um aplicativo pessoal é renderizado com ou sem uma barra de cabeçalho de guia.</span><span class="sxs-lookup"><span data-stu-id="c5c86-571">Indicate where a personal app is rendered with or without a tab header bar.</span></span> <span data-ttu-id="c5c86-572">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="c5c86-572">Default is **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="c5c86-573">activities</span><span class="sxs-lookup"><span data-stu-id="c5c86-573">activities</span></span>

<span data-ttu-id="c5c86-574">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="c5c86-574">**Optional** — object</span></span>

<span data-ttu-id="c5c86-575">Defina as propriedades que seu aplicativo usa para postar um feed de atividade do usuário.</span><span class="sxs-lookup"><span data-stu-id="c5c86-575">Define the properties your app uses to post a user activity feed.</span></span>

|<span data-ttu-id="c5c86-576">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-576">Name</span></span>| <span data-ttu-id="c5c86-577">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-577">Type</span></span>| <span data-ttu-id="c5c86-578">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-578">Maximum size</span></span> | <span data-ttu-id="c5c86-579">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-579">Required</span></span> | <span data-ttu-id="c5c86-580">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-580">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="c5c86-581">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="c5c86-581">array of Objects</span></span>|<span data-ttu-id="c5c86-582">128 itens</span><span class="sxs-lookup"><span data-stu-id="c5c86-582">128 items</span></span>| | <span data-ttu-id="c5c86-583">Forneça os tipos de atividades que seu aplicativo pode postar para um feed de atividades dos usuários.</span><span class="sxs-lookup"><span data-stu-id="c5c86-583">Provide the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="c5c86-584">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="c5c86-584">activities.activityTypes</span></span>

|<span data-ttu-id="c5c86-585">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-585">Name</span></span>| <span data-ttu-id="c5c86-586">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-586">Type</span></span>| <span data-ttu-id="c5c86-587">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-587">Maximum size</span></span> | <span data-ttu-id="c5c86-588">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-588">Required</span></span> | <span data-ttu-id="c5c86-589">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-589">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="c5c86-590">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-590">string</span></span>|<span data-ttu-id="c5c86-591">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-591">32 characters</span></span>|<span data-ttu-id="c5c86-592">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-592">✔</span></span>|<span data-ttu-id="c5c86-593">O tipo de notificação.</span><span class="sxs-lookup"><span data-stu-id="c5c86-593">The notification type.</span></span> <span data-ttu-id="c5c86-594">*Veja abaixo*.</span><span class="sxs-lookup"><span data-stu-id="c5c86-594">*See below*.</span></span>|
|`description`|<span data-ttu-id="c5c86-595">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-595">string</span></span>|<span data-ttu-id="c5c86-596">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-596">128 characters</span></span>|<span data-ttu-id="c5c86-597">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-597">✔</span></span>|<span data-ttu-id="c5c86-598">Uma breve descrição da notificação.</span><span class="sxs-lookup"><span data-stu-id="c5c86-598">A brief description of the notification.</span></span> <span data-ttu-id="c5c86-599">*Veja abaixo*.</span><span class="sxs-lookup"><span data-stu-id="c5c86-599">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="c5c86-600">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-600">string</span></span>|<span data-ttu-id="c5c86-601">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-601">128 characters</span></span>|<span data-ttu-id="c5c86-602">✔</span><span class="sxs-lookup"><span data-stu-id="c5c86-602">✔</span></span>|<span data-ttu-id="c5c86-603">Ex: "{ator} criou tarefa {taskId} para você"</span><span class="sxs-lookup"><span data-stu-id="c5c86-603">Ex: "{actor} created task {taskId} for you"</span></span>|

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

## <a name="defaultinstallscope"></a><span data-ttu-id="c5c86-604">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="c5c86-604">defaultInstallScope</span></span>

<span data-ttu-id="c5c86-605">**Opcional** - string</span><span class="sxs-lookup"><span data-stu-id="c5c86-605">**Optional** - string</span></span>

<span data-ttu-id="c5c86-606">Especifica o escopo de instalação definido para este aplicativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="c5c86-606">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="c5c86-607">O escopo definido será a opção exibida no botão quando um usuário tentar adicionar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-607">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="c5c86-608">As opções são:</span><span class="sxs-lookup"><span data-stu-id="c5c86-608">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="c5c86-609">padrãoGroupCapability</span><span class="sxs-lookup"><span data-stu-id="c5c86-609">defaultGroupCapability</span></span>

<span data-ttu-id="c5c86-610">**Opcional** - objeto</span><span class="sxs-lookup"><span data-stu-id="c5c86-610">**Optional** - object</span></span>

<span data-ttu-id="c5c86-611">Quando um escopo de instalação de grupo é selecionado, ele definirá o recurso padrão quando o usuário instalar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-611">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="c5c86-612">As opções são:</span><span class="sxs-lookup"><span data-stu-id="c5c86-612">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="c5c86-613">Nome</span><span class="sxs-lookup"><span data-stu-id="c5c86-613">Name</span></span>| <span data-ttu-id="c5c86-614">Tipo</span><span class="sxs-lookup"><span data-stu-id="c5c86-614">Type</span></span>| <span data-ttu-id="c5c86-615">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="c5c86-615">Maximum size</span></span> | <span data-ttu-id="c5c86-616">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="c5c86-616">Required</span></span> | <span data-ttu-id="c5c86-617">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5c86-617">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="c5c86-618">string</span><span class="sxs-lookup"><span data-stu-id="c5c86-618">string</span></span>|||<span data-ttu-id="c5c86-619">Quando o escopo de instalação selecionado `team` é, este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="c5c86-619">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="c5c86-620">Opções: `tab` `bot` , , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-620">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="c5c86-621">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-621">string</span></span>|||<span data-ttu-id="c5c86-622">Quando o escopo de instalação selecionado `groupchat` é, este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="c5c86-622">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="c5c86-623">Opções: `tab` `bot` , , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-623">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="c5c86-624">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5c86-624">string</span></span>|||<span data-ttu-id="c5c86-625">Quando o escopo de instalação selecionado `meetings` é, este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="c5c86-625">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="c5c86-626">Opções: `tab` `bot` , , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="c5c86-626">Options: `tab`, `bot`, or `connector`.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="c5c86-627">configurávelProperties</span><span class="sxs-lookup"><span data-stu-id="c5c86-627">configurableProperties</span></span>

<span data-ttu-id="c5c86-628">**Opcionais** - matriz</span><span class="sxs-lookup"><span data-stu-id="c5c86-628">**Optional** - array</span></span>

<span data-ttu-id="c5c86-629">O `configurableProperties` bloco define as propriedades do aplicativo que Teams administrador pode personalizar.</span><span class="sxs-lookup"><span data-stu-id="c5c86-629">The `configurableProperties` block defines the app properties that Teams admin can customize.</span></span> <span data-ttu-id="c5c86-630">Para obter mais informações, consulte [personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="c5c86-630">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="c5c86-631">Um mínimo de uma propriedade deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="c5c86-631">A minimum of one property must be defined.</span></span> <span data-ttu-id="c5c86-632">Você pode definir um máximo de nove propriedades neste bloco.</span><span class="sxs-lookup"><span data-stu-id="c5c86-632">You can define a maximum of nine properties in this block.</span></span>
> <span data-ttu-id="c5c86-633">Como uma prática recomendada, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes seguirem ao personalizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-633">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span>

<span data-ttu-id="c5c86-634">Você pode definir qualquer uma das seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c5c86-634">You can define any of the following properties:</span></span>
* <span data-ttu-id="c5c86-635">`name`: Permite que o administrador altere o nome de exibição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-635">`name`: Allows admin to change the app's display name.</span></span>
* <span data-ttu-id="c5c86-636">`shortDescription`: Permite que o administrador altere a descrição curta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-636">`shortDescription`: Allows admin to change the app's short description.</span></span>
* <span data-ttu-id="c5c86-637">`longDescription`: Permite que o administrador altere a descrição detalhada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5c86-637">`longDescription`: Allows admin to change the app's detailed description.</span></span>
* <span data-ttu-id="c5c86-638">`smallImageUrl`: É a `outline` propriedade no bloco do `icons` manifesto.</span><span class="sxs-lookup"><span data-stu-id="c5c86-638">`smallImageUrl`: It is the `outline` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="c5c86-639">`largeImageUrl`: É a `color` propriedade no bloco do `icons` manifesto.</span><span class="sxs-lookup"><span data-stu-id="c5c86-639">`largeImageUrl`: It is the `color` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="c5c86-640">`accentColor`: É a cor para usar em conjunto e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="c5c86-640">`accentColor`: It is the color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="c5c86-641">`websiteUrl`: É a url https:// para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="c5c86-641">`websiteUrl`: It is the https:// URL to the developer's website.</span></span>
* <span data-ttu-id="c5c86-642">`privacyUrl`: É a https:// URL da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="c5c86-642">`privacyUrl`: It is the https:// URL to the developer's privacy policy.</span></span>
* <span data-ttu-id="c5c86-643">`termsOfUseUrl`: É a url https:// para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="c5c86-643">`termsOfUseUrl`: It is the https:// URL to the developer's terms of use.</span></span>


