---
title: Referência de esquema de manifesto
description: Descreve o esquema de manifesto para Microsoft Teams
ms.topic: reference
ms.author: lajanuar
localization_priority: Normal
keywords: esquema de manifesto do teams
ms.openlocfilehash: 984a5de5b2c8e24f79269e62c3a7fd422ecce63f
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101804"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="8a13e-104">Referência: esquema de manifesto para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8a13e-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="8a13e-105">O Teams descreve como o aplicativo se integra ao Microsoft Teams produto.</span><span class="sxs-lookup"><span data-stu-id="8a13e-105">The Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="8a13e-106">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="8a13e-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="8a13e-107">Versões anteriores 1.0-1.4 também são suportadas (usando "v1.x" na URL).</span><span class="sxs-lookup"><span data-stu-id="8a13e-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="8a13e-108">O exemplo de esquema a seguir mostra todas as opções de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="8a13e-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="8a13e-109">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="8a13e-109">Sample full manifest</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json",
  "manifestVersion": "1.9",
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
  }
}
```

<span data-ttu-id="8a13e-110">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="8a13e-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="8a13e-111">$schema</span><span class="sxs-lookup"><span data-stu-id="8a13e-111">$schema</span></span>

<span data-ttu-id="8a13e-112">Opcional, mas recomendado — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-112">Optional, but recommended — string</span></span>

<span data-ttu-id="8a13e-113">A https:// URL de referência do Esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="8a13e-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="8a13e-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="8a13e-114">manifestVersion</span></span>

<span data-ttu-id="8a13e-115">**Obrigatório —** cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-115">**Required** — string</span></span>

<span data-ttu-id="8a13e-116">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="8a13e-116">The version of manifest schema this manifest is using.</span></span> <span data-ttu-id="8a13e-117">Deve ser 1,9.</span><span class="sxs-lookup"><span data-stu-id="8a13e-117">It must be 1.9.</span></span>

## <a name="version"></a><span data-ttu-id="8a13e-118">versão</span><span class="sxs-lookup"><span data-stu-id="8a13e-118">version</span></span>

<span data-ttu-id="8a13e-119">**Obrigatório —** cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-119">**Required** — string</span></span>

<span data-ttu-id="8a13e-120">A versão de um aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="8a13e-120">The version of a specific app.</span></span> <span data-ttu-id="8a13e-121">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="8a13e-121">If you update something in your manifest, the version must be incremented too.</span></span> <span data-ttu-id="8a13e-122">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="8a13e-122">This way, when the new manifest is installed, it overwrites the existing one and the user receives the new functionality.</span></span> <span data-ttu-id="8a13e-123">Se esse aplicativo foi enviado para a loja, o novo manifesto deve ser re-enviado e validado.</span><span class="sxs-lookup"><span data-stu-id="8a13e-123">If this app was submitted to the store, the new manifest must be re-submitted and re-validated.</span></span> <span data-ttu-id="8a13e-124">Os usuários do aplicativo recebem o novo manifesto atualizado automaticamente dentro de algumas horas após a aprovação do manifesto.</span><span class="sxs-lookup"><span data-stu-id="8a13e-124">The app users receive the new updated manifest automatically within few hours after the manifest is approved.</span></span>

<span data-ttu-id="8a13e-125">Se as solicitações de aplicativos para permissões mudarem, os usuários serão solicitados a atualizar e consentir de novo para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-125">If the app requests for permissions change, the users are prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="8a13e-126">Esta cadeia de caracteres de versão deve seguir o padrão [de semver](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="8a13e-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="8a13e-127">id</span><span class="sxs-lookup"><span data-stu-id="8a13e-127">id</span></span>

<span data-ttu-id="8a13e-128">**Obrigatório** — ID do aplicativo Microsoft</span><span class="sxs-lookup"><span data-stu-id="8a13e-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="8a13e-129">A ID é um identificador exclusivo gerado pela Microsoft para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-129">The ID is a unique Microsoft-generated identifier for the app.</span></span> <span data-ttu-id="8a13e-130">Você tem uma ID se seu bot estiver registrado por meio do Microsoft Bot Framework ou o aplicativo Web da guia já entrar com a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8a13e-130">You have an ID if your bot is registered through the Microsoft Bot Framework or your tab's web app already signs in with Microsoft.</span></span> <span data-ttu-id="8a13e-131">Você deve inserir a ID aqui.</span><span class="sxs-lookup"><span data-stu-id="8a13e-131">You must enter the ID here.</span></span> <span data-ttu-id="8a13e-132">Caso contrário, você deve gerar uma nova ID no Portal de [Registro de Aplicativos da Microsoft.](https://aka.ms/appregistrations)</span><span class="sxs-lookup"><span data-stu-id="8a13e-132">Otherwise, you must generate a new ID at the [Microsoft Application Registration Portal](https://aka.ms/appregistrations).</span></span> <span data-ttu-id="8a13e-133">Use a mesma ID se você adicionar um bot.</span><span class="sxs-lookup"><span data-stu-id="8a13e-133">Use the same ID if you add a bot.</span></span>

> [!NOTE]
> <span data-ttu-id="8a13e-134">Se você estiver enviando uma atualização para seu aplicativo existente no AppSource, a ID em seu manifesto não deve ser modificada.</span><span class="sxs-lookup"><span data-stu-id="8a13e-134">If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="8a13e-135">developer</span><span class="sxs-lookup"><span data-stu-id="8a13e-135">developer</span></span>

<span data-ttu-id="8a13e-136">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="8a13e-136">**Required** — object</span></span>

<span data-ttu-id="8a13e-137">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="8a13e-137">Specifies information about your company.</span></span> <span data-ttu-id="8a13e-138">Para aplicativos enviados ao Teams, esses valores devem corresponder às informações na listagem da loja.</span><span class="sxs-lookup"><span data-stu-id="8a13e-138">For apps submitted to the Teams store, these values must match the information in your store listing.</span></span> <span data-ttu-id="8a13e-139">Para obter mais informações, consulte [as diretrizes Teams de](~/concepts/deploy-and-publish/appsource/publish.md)publicação do Teams store.</span><span class="sxs-lookup"><span data-stu-id="8a13e-139">For more information, see the [Teams store publishing guidelines](~/concepts/deploy-and-publish/appsource/publish.md).</span></span>

|<span data-ttu-id="8a13e-140">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-140">Name</span></span>| <span data-ttu-id="8a13e-141">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-141">Maximum size</span></span> | <span data-ttu-id="8a13e-142">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-142">Required</span></span> | <span data-ttu-id="8a13e-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-143">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="8a13e-144">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-144">32 characters</span></span>|<span data-ttu-id="8a13e-145">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-145">✔</span></span>|<span data-ttu-id="8a13e-146">O nome de exibição do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="8a13e-146">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="8a13e-147">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-147">2048 characters</span></span>|<span data-ttu-id="8a13e-148">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-148">✔</span></span>|<span data-ttu-id="8a13e-149">A https:// URL do site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="8a13e-149">The https:// URL to the developer's website.</span></span> <span data-ttu-id="8a13e-150">Este link deve levar os usuários para a sua empresa ou página de aterrissagem específica do produto.</span><span class="sxs-lookup"><span data-stu-id="8a13e-150">This link must take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="8a13e-151">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-151">2048 characters</span></span>|<span data-ttu-id="8a13e-152">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-152">✔</span></span>|<span data-ttu-id="8a13e-153">A https:// URL da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="8a13e-153">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="8a13e-154">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-154">2048 characters</span></span>|<span data-ttu-id="8a13e-155">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-155">✔</span></span>|<span data-ttu-id="8a13e-156">A https:// URL dos termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="8a13e-156">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="8a13e-157">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-157">10 characters</span></span>| |<span data-ttu-id="8a13e-158">**Opcional** A ID da Rede de Parceiros da Microsoft que identifica a organização do parceiro que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-158">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="8a13e-159">nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-159">name</span></span>

<span data-ttu-id="8a13e-160">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="8a13e-160">**Required** — object</span></span>

<span data-ttu-id="8a13e-161">O nome da experiência do aplicativo, exibido para os usuários na Teams experiência.</span><span class="sxs-lookup"><span data-stu-id="8a13e-161">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="8a13e-162">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="8a13e-162">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="8a13e-163">Os valores de `short` e `full` devem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="8a13e-163">The values of `short` and `full` must be different.</span></span>

|<span data-ttu-id="8a13e-164">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-164">Name</span></span>| <span data-ttu-id="8a13e-165">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-165">Maximum size</span></span> | <span data-ttu-id="8a13e-166">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-166">Required</span></span> | <span data-ttu-id="8a13e-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-167">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="8a13e-168">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-168">30 characters</span></span>|<span data-ttu-id="8a13e-169">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-169">✔</span></span>|<span data-ttu-id="8a13e-170">O nome de exibição curto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-170">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="8a13e-171">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-171">100 characters</span></span>||<span data-ttu-id="8a13e-172">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="8a13e-172">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="8a13e-173">description</span><span class="sxs-lookup"><span data-stu-id="8a13e-173">description</span></span>

<span data-ttu-id="8a13e-174">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="8a13e-174">**Required** — object</span></span>

<span data-ttu-id="8a13e-175">Descreve seu aplicativo para usuários.</span><span class="sxs-lookup"><span data-stu-id="8a13e-175">Describes your app to users.</span></span> <span data-ttu-id="8a13e-176">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="8a13e-176">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="8a13e-177">Verifique se sua descrição descreve com precisão sua experiência e fornece informações para ajudar os clientes em potencial a entender o que sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="8a13e-177">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="8a13e-178">Você deve observar na descrição completa, se uma conta externa for necessária para uso.</span><span class="sxs-lookup"><span data-stu-id="8a13e-178">You must note in the full description, if an external account is required for use.</span></span> <span data-ttu-id="8a13e-179">Os valores de `short` e `full` devem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="8a13e-179">The values of `short` and `full` must be different.</span></span> <span data-ttu-id="8a13e-180">Sua breve descrição não deve ser repetida na descrição longa e não deve incluir nenhum outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-180">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="8a13e-181">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-181">Name</span></span>| <span data-ttu-id="8a13e-182">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-182">Maximum size</span></span> | <span data-ttu-id="8a13e-183">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-183">Required</span></span> | <span data-ttu-id="8a13e-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-184">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="8a13e-185">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-185">80 characters</span></span>|<span data-ttu-id="8a13e-186">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-186">✔</span></span>|<span data-ttu-id="8a13e-187">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="8a13e-187">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="8a13e-188">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-188">4000 characters</span></span>|<span data-ttu-id="8a13e-189">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-189">✔</span></span>|<span data-ttu-id="8a13e-190">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-190">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="8a13e-191">packageName</span><span class="sxs-lookup"><span data-stu-id="8a13e-191">packageName</span></span>

<span data-ttu-id="8a13e-192">**Opcional** — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-192">**Optional** — string</span></span>

<span data-ttu-id="8a13e-193">Um identificador exclusivo para o aplicativo na notação de domínio reverso; por exemplo, com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="8a13e-193">A unique identifier for the app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="8a13e-194">Comprimento máximo: 64 caracteres.</span><span class="sxs-lookup"><span data-stu-id="8a13e-194">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="8a13e-195">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="8a13e-195">localizationInfo</span></span>

<span data-ttu-id="8a13e-196">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="8a13e-196">**Optional** — object</span></span>

<span data-ttu-id="8a13e-197">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="8a13e-197">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="8a13e-198">Consulte [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="8a13e-198">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="8a13e-199">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-199">Name</span></span>| <span data-ttu-id="8a13e-200">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-200">Maximum size</span></span> | <span data-ttu-id="8a13e-201">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-201">Required</span></span> | <span data-ttu-id="8a13e-202">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-202">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="8a13e-203">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-203">✔</span></span>|<span data-ttu-id="8a13e-204">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="8a13e-204">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="8a13e-205">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="8a13e-205">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="8a13e-206">Uma matriz de objetos que especifica traduções de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="8a13e-206">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="8a13e-207">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-207">Name</span></span>| <span data-ttu-id="8a13e-208">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-208">Maximum size</span></span> | <span data-ttu-id="8a13e-209">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-209">Required</span></span> | <span data-ttu-id="8a13e-210">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-210">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="8a13e-211">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-211">✔</span></span>|<span data-ttu-id="8a13e-212">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="8a13e-212">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="8a13e-213">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-213">✔</span></span>|<span data-ttu-id="8a13e-214">Um caminho de arquivo relativo para um arquivo .json que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="8a13e-214">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="8a13e-215">ícones</span><span class="sxs-lookup"><span data-stu-id="8a13e-215">icons</span></span>

<span data-ttu-id="8a13e-216">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="8a13e-216">**Required** — object</span></span>

<span data-ttu-id="8a13e-217">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="8a13e-217">Icons used within the Teams app.</span></span> <span data-ttu-id="8a13e-218">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="8a13e-218">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="8a13e-219">Consulte [Ícones](../../concepts/build-and-test/apps-package.md#app-icons) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="8a13e-219">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="8a13e-220">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-220">Name</span></span>| <span data-ttu-id="8a13e-221">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-221">Maximum size</span></span> | <span data-ttu-id="8a13e-222">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-222">Required</span></span> | <span data-ttu-id="8a13e-223">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="8a13e-224">32 x 32 pixels</span><span class="sxs-lookup"><span data-stu-id="8a13e-224">32 x 32 pixels</span></span>|<span data-ttu-id="8a13e-225">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-225">✔</span></span>|<span data-ttu-id="8a13e-226">Um caminho de arquivo relativo para um ícone de contorno PNG 32x32 transparente.</span><span class="sxs-lookup"><span data-stu-id="8a13e-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="8a13e-227">192 x 192 pixels</span><span class="sxs-lookup"><span data-stu-id="8a13e-227">192 x 192 pixels</span></span>|<span data-ttu-id="8a13e-228">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-228">✔</span></span>|<span data-ttu-id="8a13e-229">Um caminho de arquivo relativo para um ícone PNG de cor total 192x192.</span><span class="sxs-lookup"><span data-stu-id="8a13e-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="8a13e-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="8a13e-230">accentColor</span></span>

<span data-ttu-id="8a13e-231">**Opcional** — código de cor de Hex HTML</span><span class="sxs-lookup"><span data-stu-id="8a13e-231">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="8a13e-232">Uma cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="8a13e-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="8a13e-233">O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="8a13e-234">configurbleTabs</span><span class="sxs-lookup"><span data-stu-id="8a13e-234">configurableTabs</span></span>

<span data-ttu-id="8a13e-235">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="8a13e-235">**Optional** — array</span></span>

<span data-ttu-id="8a13e-236">Usado quando a experiência do aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="8a13e-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="8a13e-237">As guias configuráveis têm suporte apenas no escopo das equipes e você pode configurar as mesmas guias várias vezes.</span><span class="sxs-lookup"><span data-stu-id="8a13e-237">Configurable tabs are supported only in the teams scope and you can configure the same tabs multiple times.</span></span> <span data-ttu-id="8a13e-238">No entanto, você pode defini-lo no manifesto apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="8a13e-238">However, you can define it in the manifest only once.</span></span>

|<span data-ttu-id="8a13e-239">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-239">Name</span></span>| <span data-ttu-id="8a13e-240">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-240">Type</span></span>| <span data-ttu-id="8a13e-241">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-241">Maximum size</span></span> | <span data-ttu-id="8a13e-242">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-242">Required</span></span> | <span data-ttu-id="8a13e-243">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-243">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="8a13e-244">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-244">string</span></span>|<span data-ttu-id="8a13e-245">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-245">2048 characters</span></span>|<span data-ttu-id="8a13e-246">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-246">✔</span></span>|<span data-ttu-id="8a13e-247">A https:// URL a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="8a13e-247">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="8a13e-248">matriz de números</span><span class="sxs-lookup"><span data-stu-id="8a13e-248">array of enums</span></span>|<span data-ttu-id="8a13e-249">1</span><span class="sxs-lookup"><span data-stu-id="8a13e-249">1</span></span>|<span data-ttu-id="8a13e-250">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-250">✔</span></span>|<span data-ttu-id="8a13e-251">Atualmente, as guias configuráveis suportam apenas `team` os `groupchat` escopos e.</span><span class="sxs-lookup"><span data-stu-id="8a13e-251">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="8a13e-252">booliano</span><span class="sxs-lookup"><span data-stu-id="8a13e-252">boolean</span></span>|||<span data-ttu-id="8a13e-253">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="8a13e-253">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="8a13e-254">Padrão: **true**.</span><span class="sxs-lookup"><span data-stu-id="8a13e-254">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="8a13e-255">matriz de números</span><span class="sxs-lookup"><span data-stu-id="8a13e-255">array of enums</span></span>|<span data-ttu-id="8a13e-256">6 </span><span class="sxs-lookup"><span data-stu-id="8a13e-256">6</span></span>||<span data-ttu-id="8a13e-257">O conjunto de `contextItem` escopos em que há suporte para [uma guia](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="8a13e-257">The set of `contextItem` scopes where a [tab is supported](../../tabs/how-to/access-teams-context.md).</span></span> <span data-ttu-id="8a13e-258">Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="8a13e-258">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="8a13e-259">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-259">string</span></span>|<span data-ttu-id="8a13e-260">2048</span><span class="sxs-lookup"><span data-stu-id="8a13e-260">2048</span></span>||<span data-ttu-id="8a13e-261">Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8a13e-261">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="8a13e-262">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="8a13e-262">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="8a13e-263">matriz de números</span><span class="sxs-lookup"><span data-stu-id="8a13e-263">array of enums</span></span>|<span data-ttu-id="8a13e-264">1</span><span class="sxs-lookup"><span data-stu-id="8a13e-264">1</span></span>||<span data-ttu-id="8a13e-265">Define como sua guia é disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8a13e-265">Defines how your tab is made available in SharePoint.</span></span> <span data-ttu-id="8a13e-266">As opções `sharePointFullPage` são e `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="8a13e-266">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="8a13e-267">staticTabs</span><span class="sxs-lookup"><span data-stu-id="8a13e-267">staticTabs</span></span>

<span data-ttu-id="8a13e-268">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="8a13e-268">**Optional** — array</span></span>

<span data-ttu-id="8a13e-269">Define um conjunto de guias que podem ser "fixados" por padrão, sem que o usuário as adicione manualmente.</span><span class="sxs-lookup"><span data-stu-id="8a13e-269">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="8a13e-270">As guias estáticas declaradas no `personal` escopo são sempre fixadas à experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-270">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="8a13e-271">No momento, as guias estáticas declaradas no `team` escopo não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="8a13e-271">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="8a13e-272">Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-272">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="8a13e-273">Esse bloco só é necessário para soluções que fornecem uma solução de tabulação estática.</span><span class="sxs-lookup"><span data-stu-id="8a13e-273">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="8a13e-274">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-274">Name</span></span>| <span data-ttu-id="8a13e-275">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-275">Type</span></span>| <span data-ttu-id="8a13e-276">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-276">Maximum size</span></span> | <span data-ttu-id="8a13e-277">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-277">Required</span></span> | <span data-ttu-id="8a13e-278">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-278">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="8a13e-279">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-279">string</span></span>|<span data-ttu-id="8a13e-280">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-280">64 characters</span></span>|<span data-ttu-id="8a13e-281">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-281">✔</span></span>|<span data-ttu-id="8a13e-282">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="8a13e-282">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="8a13e-283">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-283">string</span></span>|<span data-ttu-id="8a13e-284">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-284">128 characters</span></span>|<span data-ttu-id="8a13e-285">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-285">✔</span></span>|<span data-ttu-id="8a13e-286">O nome de exibição da guia na interface do canal.</span><span class="sxs-lookup"><span data-stu-id="8a13e-286">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="8a13e-287">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-287">string</span></span>||<span data-ttu-id="8a13e-288">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-288">✔</span></span>|<span data-ttu-id="8a13e-289">A https:// URL que aponta para a interface do usuário da entidade a ser exibida na tela Teams.</span><span class="sxs-lookup"><span data-stu-id="8a13e-289">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="8a13e-290">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-290">string</span></span>|||<span data-ttu-id="8a13e-291">A https:// URL para apontar se um usuário optar por exibir em um navegador.</span><span class="sxs-lookup"><span data-stu-id="8a13e-291">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="8a13e-292">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-292">string</span></span>|||<span data-ttu-id="8a13e-293">A https:// URL a ser apontada para as consultas de pesquisa de um usuário.</span><span class="sxs-lookup"><span data-stu-id="8a13e-293">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="8a13e-294">matriz de números</span><span class="sxs-lookup"><span data-stu-id="8a13e-294">array of enums</span></span>|<span data-ttu-id="8a13e-295">1</span><span class="sxs-lookup"><span data-stu-id="8a13e-295">1</span></span>|<span data-ttu-id="8a13e-296">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-296">✔</span></span>|<span data-ttu-id="8a13e-297">Atualmente, as guias estáticas suportam apenas o escopo, o que significa que ele só pode ser `personal` provisionado como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="8a13e-297">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="8a13e-298">matriz de números</span><span class="sxs-lookup"><span data-stu-id="8a13e-298">array of enums</span></span>| <span data-ttu-id="8a13e-299">2</span><span class="sxs-lookup"><span data-stu-id="8a13e-299">2</span></span>|| <span data-ttu-id="8a13e-300">O conjunto de `contextItem` escopos em que há suporte para uma guia.</span><span class="sxs-lookup"><span data-stu-id="8a13e-300">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
>  <span data-ttu-id="8a13e-301">O recurso searchUrl não está disponível para desenvolvedores de terceiros.</span><span class="sxs-lookup"><span data-stu-id="8a13e-301">The searchUrl feature is not available for the third-party developers.</span></span>
> <span data-ttu-id="8a13e-302">Se suas guias exigirem informações dependentes de contexto para exibir  conteúdo relevante ou para iniciar um fluxo de autenticação, consulte Obter contexto para sua [guia Microsoft Teams.](../../tabs/how-to/access-teams-context.md)</span><span class="sxs-lookup"><span data-stu-id="8a13e-302">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="8a13e-303">bots</span><span class="sxs-lookup"><span data-stu-id="8a13e-303">bots</span></span>

<span data-ttu-id="8a13e-304">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="8a13e-304">**Optional** — array</span></span>

<span data-ttu-id="8a13e-305">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="8a13e-305">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="8a13e-306">O item é uma matriz (máximo de apenas 1 elemento atualmente, apenas um bot é permitido por aplicativo) com todos os elementos &mdash; do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-306">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="8a13e-307">Esse bloco só é necessário para soluções que fornecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="8a13e-307">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="8a13e-308">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-308">Name</span></span>| <span data-ttu-id="8a13e-309">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-309">Type</span></span>| <span data-ttu-id="8a13e-310">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-310">Maximum size</span></span> | <span data-ttu-id="8a13e-311">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-311">Required</span></span> | <span data-ttu-id="8a13e-312">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-312">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="8a13e-313">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-313">string</span></span>|<span data-ttu-id="8a13e-314">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-314">64 characters</span></span>|<span data-ttu-id="8a13e-315">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-315">✔</span></span>|<span data-ttu-id="8a13e-316">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="8a13e-316">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="8a13e-317">Isso pode ser o mesmo da ID geral [do aplicativo.](#id)</span><span class="sxs-lookup"><span data-stu-id="8a13e-317">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="8a13e-318">matriz de números</span><span class="sxs-lookup"><span data-stu-id="8a13e-318">array of enums</span></span>|<span data-ttu-id="8a13e-319">3</span><span class="sxs-lookup"><span data-stu-id="8a13e-319">3</span></span>|<span data-ttu-id="8a13e-320">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-320">✔</span></span>|<span data-ttu-id="8a13e-321">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="8a13e-321">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="8a13e-322">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="8a13e-322">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="8a13e-323">booliano</span><span class="sxs-lookup"><span data-stu-id="8a13e-323">boolean</span></span>|||<span data-ttu-id="8a13e-324">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="8a13e-324">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="8a13e-325">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="8a13e-325">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="8a13e-326">booliano</span><span class="sxs-lookup"><span data-stu-id="8a13e-326">boolean</span></span>|||<span data-ttu-id="8a13e-327">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="8a13e-327">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="8a13e-328">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="8a13e-328">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="8a13e-329">booliano</span><span class="sxs-lookup"><span data-stu-id="8a13e-329">boolean</span></span>|||<span data-ttu-id="8a13e-330">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="8a13e-330">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="8a13e-331">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="8a13e-331">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="8a13e-332">booliano</span><span class="sxs-lookup"><span data-stu-id="8a13e-332">boolean</span></span>|||<span data-ttu-id="8a13e-333">Um valor que indica onde um bot dá suporte à chamada de áudio.</span><span class="sxs-lookup"><span data-stu-id="8a13e-333">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="8a13e-334">**IMPORTANTE**: Esta propriedade é experimental no momento.</span><span class="sxs-lookup"><span data-stu-id="8a13e-334">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="8a13e-335">As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8a13e-335">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="8a13e-336">Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="8a13e-336">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="8a13e-337">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="8a13e-337">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="8a13e-338">booliano</span><span class="sxs-lookup"><span data-stu-id="8a13e-338">boolean</span></span>|||<span data-ttu-id="8a13e-339">Um valor que indica onde um bot dá suporte à chamada de vídeo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-339">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="8a13e-340">**IMPORTANTE**: Esta propriedade é experimental no momento.</span><span class="sxs-lookup"><span data-stu-id="8a13e-340">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="8a13e-341">As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8a13e-341">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="8a13e-342">Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="8a13e-342">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="8a13e-343">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="8a13e-343">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="8a13e-344">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="8a13e-344">bots.commandLists</span></span>

<span data-ttu-id="8a13e-345">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="8a13e-345">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="8a13e-346">O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo; você deve definir uma lista de comandos separada para cada escopo que `object` seu bot oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="8a13e-346">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="8a13e-347">Consulte [Menus bot para](~/bots/how-to/create-a-bot-commands-menu.md) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="8a13e-347">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="8a13e-348">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-348">Name</span></span>| <span data-ttu-id="8a13e-349">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-349">Type</span></span>| <span data-ttu-id="8a13e-350">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-350">Maximum size</span></span> | <span data-ttu-id="8a13e-351">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-351">Required</span></span> | <span data-ttu-id="8a13e-352">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-352">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="8a13e-353">matriz de números</span><span class="sxs-lookup"><span data-stu-id="8a13e-353">array of enums</span></span>|<span data-ttu-id="8a13e-354">3</span><span class="sxs-lookup"><span data-stu-id="8a13e-354">3</span></span>|<span data-ttu-id="8a13e-355">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-355">✔</span></span>|<span data-ttu-id="8a13e-356">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="8a13e-356">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="8a13e-357">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="8a13e-357">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="8a13e-358">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="8a13e-358">array of objects</span></span>|<span data-ttu-id="8a13e-359">10 </span><span class="sxs-lookup"><span data-stu-id="8a13e-359">10</span></span>|<span data-ttu-id="8a13e-360">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-360">✔</span></span>|<span data-ttu-id="8a13e-361">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="8a13e-361">An array of commands the bot supports:</span></span><br><span data-ttu-id="8a13e-362">`title`: o nome do comando bot (cadeia, 32)</span><span class="sxs-lookup"><span data-stu-id="8a13e-362">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="8a13e-363">`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)</span><span class="sxs-lookup"><span data-stu-id="8a13e-363">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="8a13e-364">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="8a13e-364">bots.commandLists.commands</span></span>

|<span data-ttu-id="8a13e-365">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-365">Name</span></span>| <span data-ttu-id="8a13e-366">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-366">Type</span></span>| <span data-ttu-id="8a13e-367">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-367">Maximum size</span></span> | <span data-ttu-id="8a13e-368">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-368">Required</span></span> | <span data-ttu-id="8a13e-369">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-369">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="8a13e-370">title</span><span class="sxs-lookup"><span data-stu-id="8a13e-370">title</span></span>|<span data-ttu-id="8a13e-371">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-371">string</span></span>|<span data-ttu-id="8a13e-372">12 </span><span class="sxs-lookup"><span data-stu-id="8a13e-372">12</span></span>|<span data-ttu-id="8a13e-373">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-373">✔</span></span>|<span data-ttu-id="8a13e-374">O nome do comando bot</span><span class="sxs-lookup"><span data-stu-id="8a13e-374">The bot command name</span></span>|
|<span data-ttu-id="8a13e-375">description</span><span class="sxs-lookup"><span data-stu-id="8a13e-375">description</span></span>|<span data-ttu-id="8a13e-376">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-376">string</span></span>|<span data-ttu-id="8a13e-377">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-377">128 characters</span></span>|<span data-ttu-id="8a13e-378">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-378">✔</span></span>|<span data-ttu-id="8a13e-379">Uma descrição de texto simples ou um exemplo da sintaxe de comando e seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="8a13e-379">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="8a13e-380">conectores</span><span class="sxs-lookup"><span data-stu-id="8a13e-380">connectors</span></span>

<span data-ttu-id="8a13e-381">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="8a13e-381">**Optional** — array</span></span>

<span data-ttu-id="8a13e-382">O `connectors` bloco define um conector Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-382">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="8a13e-383">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-383">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="8a13e-384">Esse bloco só é necessário para soluções que fornecem um Conector.</span><span class="sxs-lookup"><span data-stu-id="8a13e-384">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="8a13e-385">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-385">Name</span></span>| <span data-ttu-id="8a13e-386">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-386">Type</span></span>| <span data-ttu-id="8a13e-387">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-387">Maximum size</span></span> | <span data-ttu-id="8a13e-388">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-388">Required</span></span> | <span data-ttu-id="8a13e-389">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-389">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="8a13e-390">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-390">string</span></span>|<span data-ttu-id="8a13e-391">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-391">2048 characters</span></span>|<span data-ttu-id="8a13e-392">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-392">✔</span></span>|<span data-ttu-id="8a13e-393">A https:// URL a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="8a13e-393">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="8a13e-394">matriz de números</span><span class="sxs-lookup"><span data-stu-id="8a13e-394">array of enums</span></span>|<span data-ttu-id="8a13e-395">1</span><span class="sxs-lookup"><span data-stu-id="8a13e-395">1</span></span>|<span data-ttu-id="8a13e-396">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-396">✔</span></span>|<span data-ttu-id="8a13e-397">Especifica se o Conector oferece uma experiência no contexto de um canal em um , ou uma experiência com escopo apenas para um `team` usuário individual ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="8a13e-397">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="8a13e-398">Atualmente, apenas o `team` escopo é suportado.</span><span class="sxs-lookup"><span data-stu-id="8a13e-398">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="8a13e-399">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-399">string</span></span>|<span data-ttu-id="8a13e-400">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-400">64 characters</span></span>|<span data-ttu-id="8a13e-401">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-401">✔</span></span>|<span data-ttu-id="8a13e-402">Um identificador exclusivo para o Conector que corresponde à sua ID no [Painel do Desenvolvedor de Conectores.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="8a13e-402">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="8a13e-403">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="8a13e-403">composeExtensions</span></span>

<span data-ttu-id="8a13e-404">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="8a13e-404">**Optional** — array</span></span>

<span data-ttu-id="8a13e-405">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-405">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="8a13e-406">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem funcionando.</span><span class="sxs-lookup"><span data-stu-id="8a13e-406">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="8a13e-407">O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-407">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="8a13e-408">Esse bloco só é necessário para soluções que fornecem uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8a13e-408">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="8a13e-409">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-409">Name</span></span>| <span data-ttu-id="8a13e-410">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-410">Type</span></span> | <span data-ttu-id="8a13e-411">Tamanho Máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-411">Maximum Size</span></span> | <span data-ttu-id="8a13e-412">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-412">Required</span></span> | <span data-ttu-id="8a13e-413">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-413">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="8a13e-414">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-414">string</span></span>|<span data-ttu-id="8a13e-415">64</span><span class="sxs-lookup"><span data-stu-id="8a13e-415">64</span></span>|<span data-ttu-id="8a13e-416">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-416">✔</span></span>|<span data-ttu-id="8a13e-417">A ID de aplicativo exclusiva da Microsoft para o bot que é o suporte à extensão de mensagens, conforme registrado na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="8a13e-417">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="8a13e-418">Isso pode ser o mesmo que a ID geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-418">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="8a13e-419">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="8a13e-419">array of objects</span></span>|<span data-ttu-id="8a13e-420">10 </span><span class="sxs-lookup"><span data-stu-id="8a13e-420">10</span></span>|<span data-ttu-id="8a13e-421">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-421">✔</span></span>|<span data-ttu-id="8a13e-422">Matriz de comandos com suporte da extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="8a13e-422">Array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="8a13e-423">booliano</span><span class="sxs-lookup"><span data-stu-id="8a13e-423">boolean</span></span>|||<span data-ttu-id="8a13e-424">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="8a13e-424">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="8a13e-425">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="8a13e-425">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="8a13e-426">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="8a13e-426">array of Objects</span></span>|<span data-ttu-id="8a13e-427">5 </span><span class="sxs-lookup"><span data-stu-id="8a13e-427">5</span></span>||<span data-ttu-id="8a13e-428">Uma lista de manipuladores que permitem que os aplicativos sejam invocados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="8a13e-428">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="8a13e-429">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-429">string</span></span>|||<span data-ttu-id="8a13e-430">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8a13e-430">The type of message handler.</span></span> <span data-ttu-id="8a13e-431">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="8a13e-431">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="8a13e-432">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-432">array of Strings</span></span>|||<span data-ttu-id="8a13e-433">Matriz de domínios que o manipulador de mensagens de link pode registrar.</span><span class="sxs-lookup"><span data-stu-id="8a13e-433">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="8a13e-434">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="8a13e-434">composeExtensions.commands</span></span>

<span data-ttu-id="8a13e-435">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="8a13e-435">Your messaging extension must declare one or more commands.</span></span> <span data-ttu-id="8a13e-436">Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="8a13e-436">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="8a13e-437">Há no máximo 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="8a13e-437">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="8a13e-438">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="8a13e-438">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="8a13e-439">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-439">Name</span></span>| <span data-ttu-id="8a13e-440">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-440">Type</span></span>| <span data-ttu-id="8a13e-441">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-441">Maximum size</span></span> | <span data-ttu-id="8a13e-442">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-442">Required</span></span> | <span data-ttu-id="8a13e-443">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-443">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="8a13e-444">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-444">string</span></span>|<span data-ttu-id="8a13e-445">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-445">64 characters</span></span>|<span data-ttu-id="8a13e-446">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-446">✔</span></span>|<span data-ttu-id="8a13e-447">A ID do comando.</span><span class="sxs-lookup"><span data-stu-id="8a13e-447">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="8a13e-448">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-448">string</span></span>|<span data-ttu-id="8a13e-449">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-449">32 characters</span></span>|<span data-ttu-id="8a13e-450">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-450">✔</span></span>|<span data-ttu-id="8a13e-451">O nome de comando amigável.</span><span class="sxs-lookup"><span data-stu-id="8a13e-451">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="8a13e-452">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-452">string</span></span>|<span data-ttu-id="8a13e-453">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-453">64 characters</span></span>||<span data-ttu-id="8a13e-454">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="8a13e-454">Type of the command.</span></span> <span data-ttu-id="8a13e-455">Um dos `query` ou `action` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-455">One of `query` or `action`.</span></span> <span data-ttu-id="8a13e-456">Padrão: **consulta**.</span><span class="sxs-lookup"><span data-stu-id="8a13e-456">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="8a13e-457">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-457">string</span></span>|<span data-ttu-id="8a13e-458">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-458">128 characters</span></span>||<span data-ttu-id="8a13e-459">A descrição que aparece para os usuários para indicar a finalidade deste comando.</span><span class="sxs-lookup"><span data-stu-id="8a13e-459">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="8a13e-460">booliano</span><span class="sxs-lookup"><span data-stu-id="8a13e-460">boolean</span></span>|||<span data-ttu-id="8a13e-461">Um valor booleano indica se o comando é executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8a13e-461">A boolean value indicates whether the command runs initially with no parameters.</span></span> <span data-ttu-id="8a13e-462">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="8a13e-462">Default is **false**.</span></span>|
|`context`|<span data-ttu-id="8a13e-463">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-463">array of Strings</span></span>|<span data-ttu-id="8a13e-464">3</span><span class="sxs-lookup"><span data-stu-id="8a13e-464">3</span></span>||<span data-ttu-id="8a13e-465">Define de onde a extensão da mensagem pode ser invocada.</span><span class="sxs-lookup"><span data-stu-id="8a13e-465">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="8a13e-466">Qualquer combinação `compose` de , , `commandBox` `message` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-466">Any combination of`compose`,`commandBox`,`message`.</span></span> <span data-ttu-id="8a13e-467">O padrão é `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="8a13e-467">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="8a13e-468">booliano</span><span class="sxs-lookup"><span data-stu-id="8a13e-468">boolean</span></span>|||<span data-ttu-id="8a13e-469">Um valor booleano que indica se ele deve buscar o módulo de tarefa dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="8a13e-469">A boolean value that indicates if it must fetch the task module dynamically.</span></span> <span data-ttu-id="8a13e-470">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="8a13e-470">Default is **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="8a13e-471">objeto</span><span class="sxs-lookup"><span data-stu-id="8a13e-471">object</span></span>|||<span data-ttu-id="8a13e-472">Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8a13e-472">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="8a13e-473">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-473">string</span></span>|<span data-ttu-id="8a13e-474">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-474">64 characters</span></span>||<span data-ttu-id="8a13e-475">Título da caixa de diálogo inicial.</span><span class="sxs-lookup"><span data-stu-id="8a13e-475">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="8a13e-476">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-476">string</span></span>|||<span data-ttu-id="8a13e-477">Largura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.</span><span class="sxs-lookup"><span data-stu-id="8a13e-477">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="8a13e-478">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-478">string</span></span>|||<span data-ttu-id="8a13e-479">Altura da caixa de diálogo - um número em pixels ou layout padrão, como "grande", "médio" ou "pequeno".</span><span class="sxs-lookup"><span data-stu-id="8a13e-479">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="8a13e-480">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-480">string</span></span>|||<span data-ttu-id="8a13e-481">URL do webview inicial.</span><span class="sxs-lookup"><span data-stu-id="8a13e-481">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="8a13e-482">matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="8a13e-482">array of object</span></span>|<span data-ttu-id="8a13e-483">5 itens</span><span class="sxs-lookup"><span data-stu-id="8a13e-483">5 items</span></span>|<span data-ttu-id="8a13e-484">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-484">✔</span></span>|<span data-ttu-id="8a13e-485">A lista de parâmetros que o comando assume.</span><span class="sxs-lookup"><span data-stu-id="8a13e-485">The list of parameters the command takes.</span></span> <span data-ttu-id="8a13e-486">Mínimo: 1; máximo: 5.</span><span class="sxs-lookup"><span data-stu-id="8a13e-486">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="8a13e-487">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-487">string</span></span>|<span data-ttu-id="8a13e-488">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-488">64 characters</span></span>|<span data-ttu-id="8a13e-489">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-489">✔</span></span>|<span data-ttu-id="8a13e-490">O nome do parâmetro como ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="8a13e-490">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="8a13e-491">Isso está incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="8a13e-491">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="8a13e-492">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-492">string</span></span>|<span data-ttu-id="8a13e-493">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-493">32 characters</span></span>|<span data-ttu-id="8a13e-494">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-494">✔</span></span>|<span data-ttu-id="8a13e-495">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a13e-495">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="8a13e-496">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-496">string</span></span>|<span data-ttu-id="8a13e-497">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-497">128 characters</span></span>||<span data-ttu-id="8a13e-498">Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a13e-498">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="8a13e-499">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-499">string</span></span>|<span data-ttu-id="8a13e-500">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-500">512 characters</span></span>||<span data-ttu-id="8a13e-501">Valor inicial do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a13e-501">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="8a13e-502">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-502">string</span></span>|<span data-ttu-id="8a13e-503">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-503">128 characters</span></span>||<span data-ttu-id="8a13e-504">Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-504">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="8a13e-505">Um de `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-505">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="8a13e-506">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="8a13e-506">array of objects</span></span>|<span data-ttu-id="8a13e-507">10 itens</span><span class="sxs-lookup"><span data-stu-id="8a13e-507">10 items</span></span>||<span data-ttu-id="8a13e-508">As opções de escolha para `choiceset` o .</span><span class="sxs-lookup"><span data-stu-id="8a13e-508">The choice options for the`choiceset`.</span></span> <span data-ttu-id="8a13e-509">Use somente quando `parameter.inputType` for `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-509">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="8a13e-510">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-510">string</span></span>|<span data-ttu-id="8a13e-511">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-511">128 characters</span></span>|<span data-ttu-id="8a13e-512">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-512">✔</span></span>|<span data-ttu-id="8a13e-513">Título da escolha.</span><span class="sxs-lookup"><span data-stu-id="8a13e-513">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="8a13e-514">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-514">string</span></span>|<span data-ttu-id="8a13e-515">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-515">512 characters</span></span>|<span data-ttu-id="8a13e-516">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-516">✔</span></span>|<span data-ttu-id="8a13e-517">O valor da escolha.</span><span class="sxs-lookup"><span data-stu-id="8a13e-517">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="8a13e-518">permissões</span><span class="sxs-lookup"><span data-stu-id="8a13e-518">permissions</span></span>

<span data-ttu-id="8a13e-519">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-519">**Optional** — array of strings</span></span>

<span data-ttu-id="8a13e-520">Uma matriz da qual especifica quais permissões o aplicativo solicita, o que permite que os usuários finais `string` saibam como a extensão se executa.</span><span class="sxs-lookup"><span data-stu-id="8a13e-520">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension performs.</span></span> <span data-ttu-id="8a13e-521">As seguintes opções não são exclusivas:</span><span class="sxs-lookup"><span data-stu-id="8a13e-521">The following options are non-exclusive:</span></span>

* <span data-ttu-id="8a13e-522">`identity`&emsp;Requer informações de identidade do usuário</span><span class="sxs-lookup"><span data-stu-id="8a13e-522">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="8a13e-523">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe</span><span class="sxs-lookup"><span data-stu-id="8a13e-523">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="8a13e-524">Alterar essas permissões durante a atualização do aplicativo faz com que os usuários repitam o processo de consentimento após executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="8a13e-524">Changing these permissions during app update, causes your users to repeat the consent process after they run the updated app.</span></span> <span data-ttu-id="8a13e-525">Consulte [Atualizando seu aplicativo para](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="8a13e-525">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="8a13e-526">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="8a13e-526">devicePermissions</span></span>

<span data-ttu-id="8a13e-527">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-527">**Optional** — array of strings</span></span>

<span data-ttu-id="8a13e-528">Fornece os recursos nativos no dispositivo de um usuário ao que seu aplicativo solicita acesso.</span><span class="sxs-lookup"><span data-stu-id="8a13e-528">Provides the native features on a user's device that your app requests access to.</span></span> <span data-ttu-id="8a13e-529">As opções são:</span><span class="sxs-lookup"><span data-stu-id="8a13e-529">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="8a13e-530">validDomains</span><span class="sxs-lookup"><span data-stu-id="8a13e-530">validDomains</span></span>

<span data-ttu-id="8a13e-531">**Opcional**, exceto **Obrigatório quando** notado</span><span class="sxs-lookup"><span data-stu-id="8a13e-531">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="8a13e-532">Uma lista de domínios válidos para sites que o aplicativo espera carregar no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="8a13e-532">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="8a13e-533">Listagem de domínio pode incluir caracteres curinga, por exemplo, `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-533">Domain listings can include wildcards, for example, `*.example.com`.</span></span> <span data-ttu-id="8a13e-534">Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-534">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="8a13e-535">Se a configuração de tabulação ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de tabulação, esse domínio deve ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="8a13e-535">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="8a13e-536">Não é **necessário** incluir os domínios de provedores de identidade que você deseja dar suporte ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-536">It is **not** necessary to include the domains of identity providers you want to support in your app.</span></span> <span data-ttu-id="8a13e-537">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para accounts.google.com, no entanto, você não deve incluir accounts.google.com em `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-537">For example, to authenticate using a Google ID, it is required to redirect to accounts.google.com, however, you must not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="8a13e-538">Teams aplicativos que exigem que suas próprias URLs do sharepoint funcionem bem, inclui "{teamsitedomain}" em sua lista de domínios válida.</span><span class="sxs-lookup"><span data-stu-id="8a13e-538">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a13e-539">Não adicione domínios que estão fora do seu controle, diretamente ou por meio de caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="8a13e-539">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="8a13e-540">Por exemplo, `yourapp.onmicrosoft.com` é válido, no entanto, `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="8a13e-540">For example, `yourapp.onmicrosoft.com` is valid, however, `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="8a13e-541">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-541">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="8a13e-542">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="8a13e-542">webApplicationInfo</span></span>

<span data-ttu-id="8a13e-543">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="8a13e-543">**Optional** — object</span></span>

<span data-ttu-id="8a13e-544">Forneça sua Azure Active Directory (AAD) app ID e informações do Microsoft Graph para ajudar os usuários a entrar perfeitamente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-544">Provide your Azure Active Directory (AAD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="8a13e-545">Se seu aplicativo estiver registrado no AAD, você deverá fornecer a ID do aplicativo, para que os administradores possam revisar facilmente as permissões e conceder consentimento Teams centro de administração.</span><span class="sxs-lookup"><span data-stu-id="8a13e-545">If your app is registered in AAD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="8a13e-546">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-546">Name</span></span>| <span data-ttu-id="8a13e-547">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-547">Type</span></span>| <span data-ttu-id="8a13e-548">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-548">Maximum size</span></span> | <span data-ttu-id="8a13e-549">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-549">Required</span></span> | <span data-ttu-id="8a13e-550">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-550">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="8a13e-551">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-551">string</span></span>|<span data-ttu-id="8a13e-552">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-552">36 characters</span></span>|<span data-ttu-id="8a13e-553">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-553">✔</span></span>|<span data-ttu-id="8a13e-554">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-554">AAD application id of the app.</span></span> <span data-ttu-id="8a13e-555">Essa id deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="8a13e-555">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="8a13e-556">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-556">string</span></span>|<span data-ttu-id="8a13e-557">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-557">2048 characters</span></span>|<span data-ttu-id="8a13e-558">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-558">✔</span></span>|<span data-ttu-id="8a13e-559">URL de recurso do aplicativo para adquirir token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="8a13e-559">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="8a13e-560">**OBSERVAÇÃO:** Se você não estiver usando o SSO, certifique-se de inserir um valor de cadeia de caracteres fictício neste campo para o manifesto do aplicativo, por exemplo, para evitar https://notapplicable uma resposta de erro.</span><span class="sxs-lookup"><span data-stu-id="8a13e-560">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="8a13e-561">matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-561">array of strings</span></span>|<span data-ttu-id="8a13e-562">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-562">128 characters</span></span>||<span data-ttu-id="8a13e-563">Especifique o [consentimento específico do recurso granular](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="8a13e-563">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="8a13e-564">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="8a13e-564">showLoadingIndicator</span></span>

<span data-ttu-id="8a13e-565">**Opcional** — booleano</span><span class="sxs-lookup"><span data-stu-id="8a13e-565">**Optional** — boolean</span></span>

<span data-ttu-id="8a13e-566">Indica se é ou não para mostrar o indicador de carregamento quando um aplicativo ou guia está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="8a13e-566">Indicates whether or not to show the loading indicator when an app or tab is loading.</span></span> <span data-ttu-id="8a13e-567">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="8a13e-567">Default is **false**.</span></span>
>[!NOTE]
><span data-ttu-id="8a13e-568">Se você selecionar como true no manifesto do aplicativo, para carregar a página corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa conforme descrito em Mostrar um documento indicador de carregamento `showLoadingIndicator` nativo. [](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)</span><span class="sxs-lookup"><span data-stu-id="8a13e-568">If you select`showLoadingIndicator` as true in your app manifest, to load the page correctly, modify the content pages of your tabs and task modules as described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="8a13e-569">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="8a13e-569">isFullScreen</span></span>

 <span data-ttu-id="8a13e-570">**Opcional** — booleano</span><span class="sxs-lookup"><span data-stu-id="8a13e-570">**Optional** — boolean</span></span>

<span data-ttu-id="8a13e-571">Indica onde um aplicativo pessoal é renderizado com ou sem uma barra de header de tabulação.</span><span class="sxs-lookup"><span data-stu-id="8a13e-571">Indicate where a personal app is rendered with or without a tab header bar.</span></span> <span data-ttu-id="8a13e-572">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="8a13e-572">Default is **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="8a13e-573">activities</span><span class="sxs-lookup"><span data-stu-id="8a13e-573">activities</span></span>

<span data-ttu-id="8a13e-574">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="8a13e-574">**Optional** — object</span></span>

<span data-ttu-id="8a13e-575">Defina as propriedades que seu aplicativo usa para postar um feed de atividade do usuário.</span><span class="sxs-lookup"><span data-stu-id="8a13e-575">Define the properties your app uses to post a user activity feed.</span></span>

|<span data-ttu-id="8a13e-576">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-576">Name</span></span>| <span data-ttu-id="8a13e-577">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-577">Type</span></span>| <span data-ttu-id="8a13e-578">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-578">Maximum size</span></span> | <span data-ttu-id="8a13e-579">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-579">Required</span></span> | <span data-ttu-id="8a13e-580">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-580">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="8a13e-581">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="8a13e-581">array of Objects</span></span>|<span data-ttu-id="8a13e-582">128 itens</span><span class="sxs-lookup"><span data-stu-id="8a13e-582">128 items</span></span>| | <span data-ttu-id="8a13e-583">Forneça os tipos de atividades que seu aplicativo pode postar em um feed de atividades dos usuários.</span><span class="sxs-lookup"><span data-stu-id="8a13e-583">Provide the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="8a13e-584">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="8a13e-584">activities.activityTypes</span></span>

|<span data-ttu-id="8a13e-585">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-585">Name</span></span>| <span data-ttu-id="8a13e-586">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-586">Type</span></span>| <span data-ttu-id="8a13e-587">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-587">Maximum size</span></span> | <span data-ttu-id="8a13e-588">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-588">Required</span></span> | <span data-ttu-id="8a13e-589">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-589">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="8a13e-590">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-590">string</span></span>|<span data-ttu-id="8a13e-591">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-591">32 characters</span></span>|<span data-ttu-id="8a13e-592">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-592">✔</span></span>|<span data-ttu-id="8a13e-593">O tipo de notificação.</span><span class="sxs-lookup"><span data-stu-id="8a13e-593">The notification type.</span></span> <span data-ttu-id="8a13e-594">*Consulte abaixo*.</span><span class="sxs-lookup"><span data-stu-id="8a13e-594">*See below*.</span></span>|
|`description`|<span data-ttu-id="8a13e-595">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-595">string</span></span>|<span data-ttu-id="8a13e-596">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-596">128 characters</span></span>|<span data-ttu-id="8a13e-597">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-597">✔</span></span>|<span data-ttu-id="8a13e-598">Uma breve descrição da notificação.</span><span class="sxs-lookup"><span data-stu-id="8a13e-598">A brief description of the notification.</span></span> <span data-ttu-id="8a13e-599">*Consulte abaixo*.</span><span class="sxs-lookup"><span data-stu-id="8a13e-599">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="8a13e-600">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-600">string</span></span>|<span data-ttu-id="8a13e-601">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-601">128 characters</span></span>|<span data-ttu-id="8a13e-602">✔</span><span class="sxs-lookup"><span data-stu-id="8a13e-602">✔</span></span>|<span data-ttu-id="8a13e-603">Ex: "{actor} criado tarefa {taskId} para você"</span><span class="sxs-lookup"><span data-stu-id="8a13e-603">Ex: "{actor} created task {taskId} for you"</span></span>|

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

## <a name="defaultinstallscope"></a><span data-ttu-id="8a13e-604">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="8a13e-604">defaultInstallScope</span></span>

<span data-ttu-id="8a13e-605">**Opcional** - cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-605">**Optional** - string</span></span>

<span data-ttu-id="8a13e-606">Especifica o escopo de instalação definido para este aplicativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="8a13e-606">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="8a13e-607">O escopo definido será a opção exibida no botão quando um usuário tentar adicionar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-607">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="8a13e-608">As opções são:</span><span class="sxs-lookup"><span data-stu-id="8a13e-608">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="8a13e-609">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="8a13e-609">defaultGroupCapability</span></span>

<span data-ttu-id="8a13e-610">**Opcional** - objeto</span><span class="sxs-lookup"><span data-stu-id="8a13e-610">**Optional** - object</span></span>

<span data-ttu-id="8a13e-611">Quando um escopo de instalação de grupo é selecionado, ele define o recurso padrão quando o usuário instala o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a13e-611">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="8a13e-612">As opções são:</span><span class="sxs-lookup"><span data-stu-id="8a13e-612">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="8a13e-613">Nome</span><span class="sxs-lookup"><span data-stu-id="8a13e-613">Name</span></span>| <span data-ttu-id="8a13e-614">Tipo</span><span class="sxs-lookup"><span data-stu-id="8a13e-614">Type</span></span>| <span data-ttu-id="8a13e-615">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="8a13e-615">Maximum size</span></span> | <span data-ttu-id="8a13e-616">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="8a13e-616">Required</span></span> | <span data-ttu-id="8a13e-617">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a13e-617">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="8a13e-618">string</span><span class="sxs-lookup"><span data-stu-id="8a13e-618">string</span></span>|||<span data-ttu-id="8a13e-619">Quando o escopo de instalação selecionado for `team` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="8a13e-619">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="8a13e-620">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-620">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="8a13e-621">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-621">string</span></span>|||<span data-ttu-id="8a13e-622">Quando o escopo de instalação selecionado for `groupchat` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="8a13e-622">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="8a13e-623">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-623">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="8a13e-624">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a13e-624">string</span></span>|||<span data-ttu-id="8a13e-625">Quando o escopo de instalação selecionado for `meetings` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="8a13e-625">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="8a13e-626">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="8a13e-626">Options: `tab`, `bot`, or `connector`.</span></span>|


