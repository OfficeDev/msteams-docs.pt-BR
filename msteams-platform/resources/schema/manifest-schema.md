---
title: Referência de esquema de manifesto
description: Descreve o esquema de manifesto para Microsoft Teams
ms.topic: reference
ms.author: lajanuar
localization_priority: Normal
keywords: esquema de manifesto do teams
ms.openlocfilehash: 75c29a1cf9c2897d7b419b45bfc1a4f0447c7aa3
ms.sourcegitcommit: 37325179a532897fafbe827dcf9a7ca5fa5e7d0b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2021
ms.locfileid: "52853526"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="25fca-104">Referência: esquema de manifesto para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="25fca-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="25fca-105">O Teams descreve como o aplicativo se integra ao Microsoft Teams produto.</span><span class="sxs-lookup"><span data-stu-id="25fca-105">The Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="25fca-106">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="25fca-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="25fca-107">As versões anteriores 1.0, 1.1,..., 1.6 e assim por diante também são suportadas (usando "v1.x" na URL).</span><span class="sxs-lookup"><span data-stu-id="25fca-107">Previous versions 1.0, 1.1,..., 1.6, and so on are also supported (using "v1.x" in the URL).</span></span>
<span data-ttu-id="25fca-108">Para obter mais informações sobre as alterações feitas em cada versão, consulte [log de alterações de manifesto](https://github.com/OfficeDev/microsoft-teams-app-schema/releases).</span><span class="sxs-lookup"><span data-stu-id="25fca-108">For more information on the changes made in each version, see [manifest change log](https://github.com/OfficeDev/microsoft-teams-app-schema/releases).</span></span>

<span data-ttu-id="25fca-109">O exemplo de esquema a seguir mostra todas as opções de extensibilidade:</span><span class="sxs-lookup"><span data-stu-id="25fca-109">The following schema sample shows all extensibility options:</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="25fca-110">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="25fca-110">Sample full manifest</span></span>

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
     "developerUrl",
     "privacyUrl",
     "termsOfUseUrl"        
  ]              
}
```

<span data-ttu-id="25fca-111">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="25fca-111">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="25fca-112">$schema</span><span class="sxs-lookup"><span data-stu-id="25fca-112">$schema</span></span>

<span data-ttu-id="25fca-113">Opcional, mas recomendado — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-113">Optional, but recommended — string</span></span>

<span data-ttu-id="25fca-114">A https:// URL de referência do Esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="25fca-114">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="25fca-115">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="25fca-115">manifestVersion</span></span>

<span data-ttu-id="25fca-116">**Obrigatório —** cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-116">**Required** — string</span></span>

<span data-ttu-id="25fca-117">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="25fca-117">The version of manifest schema this manifest is using.</span></span> <span data-ttu-id="25fca-118">Deve ser 1,10.</span><span class="sxs-lookup"><span data-stu-id="25fca-118">It must be 1.10.</span></span>

## <a name="version"></a><span data-ttu-id="25fca-119">versão</span><span class="sxs-lookup"><span data-stu-id="25fca-119">version</span></span>

<span data-ttu-id="25fca-120">**Obrigatório —** cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-120">**Required** — string</span></span>

<span data-ttu-id="25fca-121">A versão de um aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="25fca-121">The version of a specific app.</span></span> <span data-ttu-id="25fca-122">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="25fca-122">If you update something in your manifest, the version must be incremented too.</span></span> <span data-ttu-id="25fca-123">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="25fca-123">This way, when the new manifest is installed, it overwrites the existing one and the user receives the new functionality.</span></span> <span data-ttu-id="25fca-124">Se esse aplicativo foi enviado para a loja, o novo manifesto deve ser re-enviado e validado.</span><span class="sxs-lookup"><span data-stu-id="25fca-124">If this app was submitted to the store, the new manifest must be re-submitted and re-validated.</span></span> <span data-ttu-id="25fca-125">Os usuários do aplicativo recebem o novo manifesto atualizado automaticamente dentro de algumas horas após a aprovação do manifesto.</span><span class="sxs-lookup"><span data-stu-id="25fca-125">The app users receive the new updated manifest automatically within few hours after the manifest is approved.</span></span>

<span data-ttu-id="25fca-126">Se as solicitações de aplicativos para permissões mudarem, os usuários serão solicitados a atualizar e consentir de novo para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-126">If the app requests for permissions change, the users are prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="25fca-127">Esta cadeia de caracteres de versão deve seguir o padrão [de semver](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="25fca-127">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="25fca-128">id</span><span class="sxs-lookup"><span data-stu-id="25fca-128">id</span></span>

<span data-ttu-id="25fca-129">**Obrigatório** — ID do aplicativo Microsoft</span><span class="sxs-lookup"><span data-stu-id="25fca-129">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="25fca-130">A ID é um identificador exclusivo gerado pela Microsoft para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-130">The ID is a unique Microsoft-generated identifier for the app.</span></span> <span data-ttu-id="25fca-131">Você tem uma ID se seu bot estiver registrado por meio do Microsoft Bot Framework ou o aplicativo Web da guia já entrar com a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25fca-131">You have an ID if your bot is registered through the Microsoft Bot Framework or your tab's web app already signs in with Microsoft.</span></span> <span data-ttu-id="25fca-132">Você deve inserir a ID aqui.</span><span class="sxs-lookup"><span data-stu-id="25fca-132">You must enter the ID here.</span></span> <span data-ttu-id="25fca-133">Caso contrário, você deve gerar uma nova ID no Portal de [Registro de Aplicativos da Microsoft.](https://aka.ms/appregistrations)</span><span class="sxs-lookup"><span data-stu-id="25fca-133">Otherwise, you must generate a new ID at the [Microsoft Application Registration Portal](https://aka.ms/appregistrations).</span></span> <span data-ttu-id="25fca-134">Use a mesma ID se você adicionar um bot.</span><span class="sxs-lookup"><span data-stu-id="25fca-134">Use the same ID if you add a bot.</span></span>

> [!NOTE]
> <span data-ttu-id="25fca-135">Se você estiver enviando uma atualização para seu aplicativo existente no AppSource, a ID em seu manifesto não deve ser modificada.</span><span class="sxs-lookup"><span data-stu-id="25fca-135">If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="25fca-136">developer</span><span class="sxs-lookup"><span data-stu-id="25fca-136">developer</span></span>

<span data-ttu-id="25fca-137">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="25fca-137">**Required** — object</span></span>

<span data-ttu-id="25fca-138">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="25fca-138">Specifies information about your company.</span></span> <span data-ttu-id="25fca-139">Para aplicativos enviados ao Teams, esses valores devem corresponder às informações na listagem da loja.</span><span class="sxs-lookup"><span data-stu-id="25fca-139">For apps submitted to the Teams store, these values must match the information in your store listing.</span></span> <span data-ttu-id="25fca-140">Para obter mais informações, consulte [as diretrizes Teams de](~/concepts/deploy-and-publish/appsource/publish.md)publicação do Teams store.</span><span class="sxs-lookup"><span data-stu-id="25fca-140">For more information, see the [Teams store publishing guidelines](~/concepts/deploy-and-publish/appsource/publish.md).</span></span>

|<span data-ttu-id="25fca-141">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-141">Name</span></span>| <span data-ttu-id="25fca-142">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-142">Maximum size</span></span> | <span data-ttu-id="25fca-143">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-143">Required</span></span> | <span data-ttu-id="25fca-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="25fca-145">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-145">32 characters</span></span>|<span data-ttu-id="25fca-146">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-146">✔</span></span>|<span data-ttu-id="25fca-147">O nome de exibição do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="25fca-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="25fca-148">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-148">2048 characters</span></span>|<span data-ttu-id="25fca-149">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-149">✔</span></span>|<span data-ttu-id="25fca-150">A https:// URL do site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="25fca-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="25fca-151">Este link deve levar os usuários para a sua empresa ou página de aterrissagem específica do produto.</span><span class="sxs-lookup"><span data-stu-id="25fca-151">This link must take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="25fca-152">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-152">2048 characters</span></span>|<span data-ttu-id="25fca-153">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-153">✔</span></span>|<span data-ttu-id="25fca-154">A https:// URL da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="25fca-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="25fca-155">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-155">2048 characters</span></span>|<span data-ttu-id="25fca-156">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-156">✔</span></span>|<span data-ttu-id="25fca-157">A https:// URL dos termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="25fca-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="25fca-158">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-158">10 characters</span></span>| |<span data-ttu-id="25fca-159">**Opcional** A ID da Rede de Parceiros da Microsoft que identifica a organização do parceiro que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-159">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="25fca-160">nome</span><span class="sxs-lookup"><span data-stu-id="25fca-160">name</span></span>

<span data-ttu-id="25fca-161">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="25fca-161">**Required** — object</span></span>

<span data-ttu-id="25fca-162">O nome da experiência do aplicativo, exibido para os usuários na Teams experiência.</span><span class="sxs-lookup"><span data-stu-id="25fca-162">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="25fca-163">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="25fca-163">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="25fca-164">Os valores de `short` e `full` devem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="25fca-164">The values of `short` and `full` must be different.</span></span>

|<span data-ttu-id="25fca-165">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-165">Name</span></span>| <span data-ttu-id="25fca-166">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-166">Maximum size</span></span> | <span data-ttu-id="25fca-167">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-167">Required</span></span> | <span data-ttu-id="25fca-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-168">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="25fca-169">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-169">30 characters</span></span>|<span data-ttu-id="25fca-170">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-170">✔</span></span>|<span data-ttu-id="25fca-171">O nome de exibição curto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-171">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="25fca-172">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-172">100 characters</span></span>||<span data-ttu-id="25fca-173">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="25fca-173">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="25fca-174">descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-174">description</span></span>

<span data-ttu-id="25fca-175">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="25fca-175">**Required** — object</span></span>

<span data-ttu-id="25fca-176">Descreve seu aplicativo para usuários.</span><span class="sxs-lookup"><span data-stu-id="25fca-176">Describes your app to users.</span></span> <span data-ttu-id="25fca-177">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="25fca-177">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="25fca-178">Verifique se sua descrição descreve com precisão sua experiência e fornece informações para ajudar os clientes em potencial a entender o que sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="25fca-178">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="25fca-179">Você deve observar na descrição completa, se uma conta externa for necessária para uso.</span><span class="sxs-lookup"><span data-stu-id="25fca-179">You must note in the full description, if an external account is required for use.</span></span> <span data-ttu-id="25fca-180">Os valores de `short` e `full` devem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="25fca-180">The values of `short` and `full` must be different.</span></span> <span data-ttu-id="25fca-181">Sua breve descrição não deve ser repetida na descrição longa e não deve incluir nenhum outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-181">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="25fca-182">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-182">Name</span></span>| <span data-ttu-id="25fca-183">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-183">Maximum size</span></span> | <span data-ttu-id="25fca-184">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-184">Required</span></span> | <span data-ttu-id="25fca-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-185">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="25fca-186">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-186">80 characters</span></span>|<span data-ttu-id="25fca-187">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-187">✔</span></span>|<span data-ttu-id="25fca-188">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="25fca-188">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="25fca-189">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-189">4000 characters</span></span>|<span data-ttu-id="25fca-190">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-190">✔</span></span>|<span data-ttu-id="25fca-191">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-191">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="25fca-192">packageName</span><span class="sxs-lookup"><span data-stu-id="25fca-192">packageName</span></span>

<span data-ttu-id="25fca-193">**Opcional** — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-193">**Optional** — string</span></span>

<span data-ttu-id="25fca-194">Um identificador exclusivo para o aplicativo na notação de domínio reverso; por exemplo, com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="25fca-194">A unique identifier for the app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="25fca-195">Comprimento máximo: 64 caracteres.</span><span class="sxs-lookup"><span data-stu-id="25fca-195">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="25fca-196">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="25fca-196">localizationInfo</span></span>

<span data-ttu-id="25fca-197">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="25fca-197">**Optional** — object</span></span>

<span data-ttu-id="25fca-198">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="25fca-198">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="25fca-199">Para obter mais informações, consulte [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="25fca-199">For more information, see [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="25fca-200">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-200">Name</span></span>| <span data-ttu-id="25fca-201">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-201">Maximum size</span></span> | <span data-ttu-id="25fca-202">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-202">Required</span></span> | <span data-ttu-id="25fca-203">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-203">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="25fca-204">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-204">✔</span></span>|<span data-ttu-id="25fca-205">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="25fca-205">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="25fca-206">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="25fca-206">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="25fca-207">Uma matriz de objetos que especifica traduções de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="25fca-207">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="25fca-208">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-208">Name</span></span>| <span data-ttu-id="25fca-209">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-209">Maximum size</span></span> | <span data-ttu-id="25fca-210">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-210">Required</span></span> | <span data-ttu-id="25fca-211">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-211">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="25fca-212">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-212">✔</span></span>|<span data-ttu-id="25fca-213">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="25fca-213">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="25fca-214">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-214">✔</span></span>|<span data-ttu-id="25fca-215">Um caminho de arquivo relativo para um arquivo .json que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="25fca-215">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="25fca-216">ícones</span><span class="sxs-lookup"><span data-stu-id="25fca-216">icons</span></span>

<span data-ttu-id="25fca-217">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="25fca-217">**Required** — object</span></span>

<span data-ttu-id="25fca-218">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="25fca-218">Icons used within the Teams app.</span></span> <span data-ttu-id="25fca-219">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="25fca-219">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="25fca-220">Consulte [Ícones](../../concepts/build-and-test/apps-package.md#app-icons) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="25fca-220">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="25fca-221">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-221">Name</span></span>| <span data-ttu-id="25fca-222">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-222">Maximum size</span></span> | <span data-ttu-id="25fca-223">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-223">Required</span></span> | <span data-ttu-id="25fca-224">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-224">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="25fca-225">32 x 32 pixels</span><span class="sxs-lookup"><span data-stu-id="25fca-225">32 x 32 pixels</span></span>|<span data-ttu-id="25fca-226">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-226">✔</span></span>|<span data-ttu-id="25fca-227">Um caminho de arquivo relativo para um ícone de contorno PNG 32x32 transparente.</span><span class="sxs-lookup"><span data-stu-id="25fca-227">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="25fca-228">192 x 192 pixels</span><span class="sxs-lookup"><span data-stu-id="25fca-228">192 x 192 pixels</span></span>|<span data-ttu-id="25fca-229">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-229">✔</span></span>|<span data-ttu-id="25fca-230">Um caminho de arquivo relativo para um ícone PNG de cor total 192x192.</span><span class="sxs-lookup"><span data-stu-id="25fca-230">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="25fca-231">accentColor</span><span class="sxs-lookup"><span data-stu-id="25fca-231">accentColor</span></span>

<span data-ttu-id="25fca-232">**Opcional** — código de cor de Hex HTML</span><span class="sxs-lookup"><span data-stu-id="25fca-232">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="25fca-233">Uma cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="25fca-233">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="25fca-234">O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="25fca-234">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="25fca-235">configurbleTabs</span><span class="sxs-lookup"><span data-stu-id="25fca-235">configurableTabs</span></span>

<span data-ttu-id="25fca-236">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="25fca-236">**Optional** — array</span></span>

<span data-ttu-id="25fca-237">Usado quando a experiência do aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="25fca-237">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="25fca-238">As guias configuráveis têm suporte apenas no escopo das equipes e você pode configurar as mesmas guias várias vezes.</span><span class="sxs-lookup"><span data-stu-id="25fca-238">Configurable tabs are supported only in the teams scope and you can configure the same tabs multiple times.</span></span> <span data-ttu-id="25fca-239">No entanto, você pode defini-lo no manifesto apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="25fca-239">However, you can define it in the manifest only once.</span></span>

|<span data-ttu-id="25fca-240">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-240">Name</span></span>| <span data-ttu-id="25fca-241">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-241">Type</span></span>| <span data-ttu-id="25fca-242">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-242">Maximum size</span></span> | <span data-ttu-id="25fca-243">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-243">Required</span></span> | <span data-ttu-id="25fca-244">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="25fca-245">string</span><span class="sxs-lookup"><span data-stu-id="25fca-245">string</span></span>|<span data-ttu-id="25fca-246">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-246">2048 characters</span></span>|<span data-ttu-id="25fca-247">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-247">✔</span></span>|<span data-ttu-id="25fca-248">A https:// URL a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="25fca-248">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="25fca-249">matriz de números</span><span class="sxs-lookup"><span data-stu-id="25fca-249">array of enums</span></span>|<span data-ttu-id="25fca-250">1</span><span class="sxs-lookup"><span data-stu-id="25fca-250">1</span></span>|<span data-ttu-id="25fca-251">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-251">✔</span></span>|<span data-ttu-id="25fca-252">Atualmente, as guias configuráveis suportam apenas `team` os `groupchat` escopos e.</span><span class="sxs-lookup"><span data-stu-id="25fca-252">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="25fca-253">booliano</span><span class="sxs-lookup"><span data-stu-id="25fca-253">boolean</span></span>|||<span data-ttu-id="25fca-254">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="25fca-254">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="25fca-255">Padrão: **true**.</span><span class="sxs-lookup"><span data-stu-id="25fca-255">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="25fca-256">matriz de números</span><span class="sxs-lookup"><span data-stu-id="25fca-256">array of enums</span></span>|<span data-ttu-id="25fca-257">6 </span><span class="sxs-lookup"><span data-stu-id="25fca-257">6</span></span>||<span data-ttu-id="25fca-258">O conjunto de `contextItem` escopos em que há suporte para [uma guia](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="25fca-258">The set of `contextItem` scopes where a [tab is supported](../../tabs/how-to/access-teams-context.md).</span></span> <span data-ttu-id="25fca-259">Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="25fca-259">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="25fca-260">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-260">string</span></span>|<span data-ttu-id="25fca-261">2048</span><span class="sxs-lookup"><span data-stu-id="25fca-261">2048</span></span>||<span data-ttu-id="25fca-262">Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso SharePoint.</span><span class="sxs-lookup"><span data-stu-id="25fca-262">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="25fca-263">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="25fca-263">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="25fca-264">matriz de números</span><span class="sxs-lookup"><span data-stu-id="25fca-264">array of enums</span></span>|<span data-ttu-id="25fca-265">1</span><span class="sxs-lookup"><span data-stu-id="25fca-265">1</span></span>||<span data-ttu-id="25fca-266">Define como sua guia é disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="25fca-266">Defines how your tab is made available in SharePoint.</span></span> <span data-ttu-id="25fca-267">As opções `sharePointFullPage` são e `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="25fca-267">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="25fca-268">staticTabs</span><span class="sxs-lookup"><span data-stu-id="25fca-268">staticTabs</span></span>

<span data-ttu-id="25fca-269">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="25fca-269">**Optional** — array</span></span>

<span data-ttu-id="25fca-270">Define um conjunto de guias que podem ser "fixados" por padrão, sem que o usuário as adicione manualmente.</span><span class="sxs-lookup"><span data-stu-id="25fca-270">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="25fca-271">As guias estáticas declaradas no `personal` escopo são sempre fixadas à experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-271">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="25fca-272">No momento, as guias estáticas declaradas no `team` escopo não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="25fca-272">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="25fca-273">Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="25fca-273">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="25fca-274">Esse bloco só é necessário para soluções que fornecem uma solução de tabulação estática.</span><span class="sxs-lookup"><span data-stu-id="25fca-274">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="25fca-275">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-275">Name</span></span>| <span data-ttu-id="25fca-276">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-276">Type</span></span>| <span data-ttu-id="25fca-277">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-277">Maximum size</span></span> | <span data-ttu-id="25fca-278">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-278">Required</span></span> | <span data-ttu-id="25fca-279">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-279">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="25fca-280">string</span><span class="sxs-lookup"><span data-stu-id="25fca-280">string</span></span>|<span data-ttu-id="25fca-281">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-281">64 characters</span></span>|<span data-ttu-id="25fca-282">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-282">✔</span></span>|<span data-ttu-id="25fca-283">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="25fca-283">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="25fca-284">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-284">string</span></span>|<span data-ttu-id="25fca-285">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-285">128 characters</span></span>|<span data-ttu-id="25fca-286">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-286">✔</span></span>|<span data-ttu-id="25fca-287">O nome de exibição da guia na interface do canal.</span><span class="sxs-lookup"><span data-stu-id="25fca-287">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="25fca-288">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-288">string</span></span>||<span data-ttu-id="25fca-289">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-289">✔</span></span>|<span data-ttu-id="25fca-290">A https:// URL que aponta para a interface do usuário da entidade a ser exibida na tela Teams.</span><span class="sxs-lookup"><span data-stu-id="25fca-290">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="25fca-291">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-291">string</span></span>|||<span data-ttu-id="25fca-292">A https:// URL para apontar se um usuário optar por exibir em um navegador.</span><span class="sxs-lookup"><span data-stu-id="25fca-292">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="25fca-293">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-293">string</span></span>|||<span data-ttu-id="25fca-294">A https:// URL a ser apontada para as consultas de pesquisa de um usuário.</span><span class="sxs-lookup"><span data-stu-id="25fca-294">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="25fca-295">matriz de números</span><span class="sxs-lookup"><span data-stu-id="25fca-295">array of enums</span></span>|<span data-ttu-id="25fca-296">1</span><span class="sxs-lookup"><span data-stu-id="25fca-296">1</span></span>|<span data-ttu-id="25fca-297">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-297">✔</span></span>|<span data-ttu-id="25fca-298">Atualmente, as guias estáticas suportam apenas o escopo, o que significa que ele só pode ser `personal` provisionado como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="25fca-298">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="25fca-299">matriz de números</span><span class="sxs-lookup"><span data-stu-id="25fca-299">array of enums</span></span>| <span data-ttu-id="25fca-300">2</span><span class="sxs-lookup"><span data-stu-id="25fca-300">2</span></span>|| <span data-ttu-id="25fca-301">O conjunto de `contextItem` escopos em que há suporte para uma guia.</span><span class="sxs-lookup"><span data-stu-id="25fca-301">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
>  <span data-ttu-id="25fca-302">O recurso searchUrl não está disponível para desenvolvedores de terceiros.</span><span class="sxs-lookup"><span data-stu-id="25fca-302">The searchUrl feature is not available for the third-party developers.</span></span>
> <span data-ttu-id="25fca-303">Se suas guias exigirem informações dependentes de contexto para exibir conteúdo relevante ou para iniciar um fluxo de autenticação, para obter mais informações, consulte Obter contexto para sua Microsoft Teams [guia](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="25fca-303">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, For more information, see [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="25fca-304">bots</span><span class="sxs-lookup"><span data-stu-id="25fca-304">bots</span></span>

<span data-ttu-id="25fca-305">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="25fca-305">**Optional** — array</span></span>

<span data-ttu-id="25fca-306">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="25fca-306">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="25fca-307">O item é uma matriz (máximo de apenas 1 elemento atualmente, apenas um bot é permitido por aplicativo) com todos os elementos &mdash; do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="25fca-307">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="25fca-308">Esse bloco só é necessário para soluções que fornecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="25fca-308">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="25fca-309">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-309">Name</span></span>| <span data-ttu-id="25fca-310">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-310">Type</span></span>| <span data-ttu-id="25fca-311">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-311">Maximum size</span></span> | <span data-ttu-id="25fca-312">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-312">Required</span></span> | <span data-ttu-id="25fca-313">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-313">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="25fca-314">string</span><span class="sxs-lookup"><span data-stu-id="25fca-314">string</span></span>|<span data-ttu-id="25fca-315">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-315">64 characters</span></span>|<span data-ttu-id="25fca-316">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-316">✔</span></span>|<span data-ttu-id="25fca-317">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="25fca-317">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="25fca-318">Isso pode ser o mesmo da ID geral [do aplicativo.](#id)</span><span class="sxs-lookup"><span data-stu-id="25fca-318">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="25fca-319">matriz de números</span><span class="sxs-lookup"><span data-stu-id="25fca-319">array of enums</span></span>|<span data-ttu-id="25fca-320">3</span><span class="sxs-lookup"><span data-stu-id="25fca-320">3</span></span>|<span data-ttu-id="25fca-321">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-321">✔</span></span>|<span data-ttu-id="25fca-322">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="25fca-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="25fca-323">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="25fca-323">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="25fca-324">booliano</span><span class="sxs-lookup"><span data-stu-id="25fca-324">boolean</span></span>|||<span data-ttu-id="25fca-325">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="25fca-325">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="25fca-326">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="25fca-326">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="25fca-327">booliano</span><span class="sxs-lookup"><span data-stu-id="25fca-327">boolean</span></span>|||<span data-ttu-id="25fca-328">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="25fca-328">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="25fca-329">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="25fca-329">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="25fca-330">booliano</span><span class="sxs-lookup"><span data-stu-id="25fca-330">boolean</span></span>|||<span data-ttu-id="25fca-331">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="25fca-331">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="25fca-332">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="25fca-332">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="25fca-333">booliano</span><span class="sxs-lookup"><span data-stu-id="25fca-333">boolean</span></span>|||<span data-ttu-id="25fca-334">Um valor que indica onde um bot dá suporte à chamada de áudio.</span><span class="sxs-lookup"><span data-stu-id="25fca-334">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="25fca-335">**IMPORTANTE**: Esta propriedade é experimental no momento.</span><span class="sxs-lookup"><span data-stu-id="25fca-335">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="25fca-336">As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="25fca-336">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="25fca-337">Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="25fca-337">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="25fca-338">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="25fca-338">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="25fca-339">booliano</span><span class="sxs-lookup"><span data-stu-id="25fca-339">boolean</span></span>|||<span data-ttu-id="25fca-340">Um valor que indica onde um bot dá suporte à chamada de vídeo.</span><span class="sxs-lookup"><span data-stu-id="25fca-340">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="25fca-341">**IMPORTANTE**: Esta propriedade é experimental no momento.</span><span class="sxs-lookup"><span data-stu-id="25fca-341">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="25fca-342">As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="25fca-342">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="25fca-343">Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="25fca-343">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="25fca-344">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="25fca-344">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="25fca-345">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="25fca-345">bots.commandLists</span></span>

<span data-ttu-id="25fca-346">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="25fca-346">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="25fca-347">O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo; você deve definir uma lista de comandos separada para cada escopo que `object` seu bot oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="25fca-347">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="25fca-348">Consulte [Menus bot para](~/bots/how-to/create-a-bot-commands-menu.md) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="25fca-348">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="25fca-349">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-349">Name</span></span>| <span data-ttu-id="25fca-350">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-350">Type</span></span>| <span data-ttu-id="25fca-351">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-351">Maximum size</span></span> | <span data-ttu-id="25fca-352">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-352">Required</span></span> | <span data-ttu-id="25fca-353">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-353">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="25fca-354">matriz de números</span><span class="sxs-lookup"><span data-stu-id="25fca-354">array of enums</span></span>|<span data-ttu-id="25fca-355">3</span><span class="sxs-lookup"><span data-stu-id="25fca-355">3</span></span>|<span data-ttu-id="25fca-356">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-356">✔</span></span>|<span data-ttu-id="25fca-357">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="25fca-357">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="25fca-358">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="25fca-358">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="25fca-359">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="25fca-359">array of objects</span></span>|<span data-ttu-id="25fca-360">10 </span><span class="sxs-lookup"><span data-stu-id="25fca-360">10</span></span>|<span data-ttu-id="25fca-361">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-361">✔</span></span>|<span data-ttu-id="25fca-362">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="25fca-362">An array of commands the bot supports:</span></span><br><span data-ttu-id="25fca-363">`title`: o nome do comando bot (cadeia, 32)</span><span class="sxs-lookup"><span data-stu-id="25fca-363">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="25fca-364">`description`: uma descrição simples ou um exemplo da sintaxe de comando e seu argumento (cadeia de caracteres, 128).</span><span class="sxs-lookup"><span data-stu-id="25fca-364">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="25fca-365">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="25fca-365">bots.commandLists.commands</span></span>

|<span data-ttu-id="25fca-366">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-366">Name</span></span>| <span data-ttu-id="25fca-367">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-367">Type</span></span>| <span data-ttu-id="25fca-368">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-368">Maximum size</span></span> | <span data-ttu-id="25fca-369">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-369">Required</span></span> | <span data-ttu-id="25fca-370">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-370">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="25fca-371">title</span><span class="sxs-lookup"><span data-stu-id="25fca-371">title</span></span>|<span data-ttu-id="25fca-372">string</span><span class="sxs-lookup"><span data-stu-id="25fca-372">string</span></span>|<span data-ttu-id="25fca-373">12 </span><span class="sxs-lookup"><span data-stu-id="25fca-373">12</span></span>|<span data-ttu-id="25fca-374">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-374">✔</span></span>|<span data-ttu-id="25fca-375">O nome do comando bot.</span><span class="sxs-lookup"><span data-stu-id="25fca-375">The bot command name.</span></span>|
|<span data-ttu-id="25fca-376">description</span><span class="sxs-lookup"><span data-stu-id="25fca-376">description</span></span>|<span data-ttu-id="25fca-377">string</span><span class="sxs-lookup"><span data-stu-id="25fca-377">string</span></span>|<span data-ttu-id="25fca-378">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-378">128 characters</span></span>|<span data-ttu-id="25fca-379">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-379">✔</span></span>|<span data-ttu-id="25fca-380">Uma descrição de texto simples ou um exemplo da sintaxe de comando e seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="25fca-380">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="25fca-381">conectores</span><span class="sxs-lookup"><span data-stu-id="25fca-381">connectors</span></span>

<span data-ttu-id="25fca-382">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="25fca-382">**Optional** — array</span></span>

<span data-ttu-id="25fca-383">O `connectors` bloco define um conector Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-383">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="25fca-384">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="25fca-384">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="25fca-385">Esse bloco só é necessário para soluções que fornecem um Conector.</span><span class="sxs-lookup"><span data-stu-id="25fca-385">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="25fca-386">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-386">Name</span></span>| <span data-ttu-id="25fca-387">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-387">Type</span></span>| <span data-ttu-id="25fca-388">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-388">Maximum size</span></span> | <span data-ttu-id="25fca-389">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-389">Required</span></span> | <span data-ttu-id="25fca-390">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-390">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="25fca-391">string</span><span class="sxs-lookup"><span data-stu-id="25fca-391">string</span></span>|<span data-ttu-id="25fca-392">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-392">2048 characters</span></span>|<span data-ttu-id="25fca-393">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-393">✔</span></span>|<span data-ttu-id="25fca-394">A https:// URL a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="25fca-394">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="25fca-395">matriz de números</span><span class="sxs-lookup"><span data-stu-id="25fca-395">array of enums</span></span>|<span data-ttu-id="25fca-396">1</span><span class="sxs-lookup"><span data-stu-id="25fca-396">1</span></span>|<span data-ttu-id="25fca-397">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-397">✔</span></span>|<span data-ttu-id="25fca-398">Especifica se o Conector oferece uma experiência no contexto de um canal em um , ou uma experiência com escopo apenas para um `team` usuário individual ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="25fca-398">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="25fca-399">Atualmente, apenas o `team` escopo é suportado.</span><span class="sxs-lookup"><span data-stu-id="25fca-399">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="25fca-400">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-400">string</span></span>|<span data-ttu-id="25fca-401">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-401">64 characters</span></span>|<span data-ttu-id="25fca-402">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-402">✔</span></span>|<span data-ttu-id="25fca-403">Um identificador exclusivo para o Conector que corresponde à sua ID no [Painel do Desenvolvedor de Conectores.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="25fca-403">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="25fca-404">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="25fca-404">composeExtensions</span></span>

<span data-ttu-id="25fca-405">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="25fca-405">**Optional** — array</span></span>

<span data-ttu-id="25fca-406">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-406">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="25fca-407">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem funcionando.</span><span class="sxs-lookup"><span data-stu-id="25fca-407">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="25fca-408">O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="25fca-408">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="25fca-409">Esse bloco só é necessário para soluções que fornecem uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="25fca-409">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="25fca-410">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-410">Name</span></span>| <span data-ttu-id="25fca-411">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-411">Type</span></span> | <span data-ttu-id="25fca-412">Tamanho Máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-412">Maximum Size</span></span> | <span data-ttu-id="25fca-413">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-413">Required</span></span> | <span data-ttu-id="25fca-414">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-414">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="25fca-415">string</span><span class="sxs-lookup"><span data-stu-id="25fca-415">string</span></span>|<span data-ttu-id="25fca-416">64</span><span class="sxs-lookup"><span data-stu-id="25fca-416">64</span></span>|<span data-ttu-id="25fca-417">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-417">✔</span></span>|<span data-ttu-id="25fca-418">A ID de aplicativo exclusiva da Microsoft para o bot que é o suporte à extensão de mensagens, conforme registrado na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="25fca-418">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="25fca-419">Isso pode ser o mesmo que a ID geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-419">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="25fca-420">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="25fca-420">array of objects</span></span>|<span data-ttu-id="25fca-421">10 </span><span class="sxs-lookup"><span data-stu-id="25fca-421">10</span></span>|<span data-ttu-id="25fca-422">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-422">✔</span></span>|<span data-ttu-id="25fca-423">Matriz de comandos com suporte da extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="25fca-423">Array of commands the messaging extension supports.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="25fca-424">booliano</span><span class="sxs-lookup"><span data-stu-id="25fca-424">boolean</span></span>|||<span data-ttu-id="25fca-425">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="25fca-425">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="25fca-426">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="25fca-426">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="25fca-427">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="25fca-427">array of Objects</span></span>|<span data-ttu-id="25fca-428">5 </span><span class="sxs-lookup"><span data-stu-id="25fca-428">5</span></span>||<span data-ttu-id="25fca-429">Uma lista de manipuladores que permitem que os aplicativos sejam invocados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="25fca-429">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="25fca-430">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-430">string</span></span>|||<span data-ttu-id="25fca-431">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="25fca-431">The type of message handler.</span></span> <span data-ttu-id="25fca-432">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="25fca-432">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="25fca-433">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-433">array of Strings</span></span>|||<span data-ttu-id="25fca-434">Matriz de domínios que o manipulador de mensagens de link pode registrar.</span><span class="sxs-lookup"><span data-stu-id="25fca-434">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="25fca-435">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="25fca-435">composeExtensions.commands</span></span>

<span data-ttu-id="25fca-436">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="25fca-436">Your messaging extension must declare one or more commands.</span></span> <span data-ttu-id="25fca-437">Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="25fca-437">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="25fca-438">Há no máximo 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="25fca-438">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="25fca-439">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="25fca-439">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="25fca-440">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-440">Name</span></span>| <span data-ttu-id="25fca-441">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-441">Type</span></span>| <span data-ttu-id="25fca-442">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-442">Maximum size</span></span> | <span data-ttu-id="25fca-443">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-443">Required</span></span> | <span data-ttu-id="25fca-444">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-444">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="25fca-445">string</span><span class="sxs-lookup"><span data-stu-id="25fca-445">string</span></span>|<span data-ttu-id="25fca-446">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-446">64 characters</span></span>|<span data-ttu-id="25fca-447">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-447">✔</span></span>|<span data-ttu-id="25fca-448">A ID do comando.</span><span class="sxs-lookup"><span data-stu-id="25fca-448">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="25fca-449">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-449">string</span></span>|<span data-ttu-id="25fca-450">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-450">32 characters</span></span>|<span data-ttu-id="25fca-451">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-451">✔</span></span>|<span data-ttu-id="25fca-452">O nome de comando amigável.</span><span class="sxs-lookup"><span data-stu-id="25fca-452">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="25fca-453">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-453">string</span></span>|<span data-ttu-id="25fca-454">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-454">64 characters</span></span>||<span data-ttu-id="25fca-455">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="25fca-455">Type of the command.</span></span> <span data-ttu-id="25fca-456">Um dos `query` ou `action` .</span><span class="sxs-lookup"><span data-stu-id="25fca-456">One of `query` or `action`.</span></span> <span data-ttu-id="25fca-457">Padrão: **consulta**.</span><span class="sxs-lookup"><span data-stu-id="25fca-457">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="25fca-458">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-458">string</span></span>|<span data-ttu-id="25fca-459">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-459">128 characters</span></span>||<span data-ttu-id="25fca-460">A descrição que aparece para os usuários para indicar a finalidade deste comando.</span><span class="sxs-lookup"><span data-stu-id="25fca-460">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="25fca-461">booliano</span><span class="sxs-lookup"><span data-stu-id="25fca-461">boolean</span></span>|||<span data-ttu-id="25fca-462">Um valor booleano indica se o comando é executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="25fca-462">A boolean value indicates whether the command runs initially with no parameters.</span></span> <span data-ttu-id="25fca-463">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="25fca-463">Default is **false**.</span></span>|
|`context`|<span data-ttu-id="25fca-464">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-464">array of Strings</span></span>|<span data-ttu-id="25fca-465">3</span><span class="sxs-lookup"><span data-stu-id="25fca-465">3</span></span>||<span data-ttu-id="25fca-466">Define de onde a extensão da mensagem pode ser invocada.</span><span class="sxs-lookup"><span data-stu-id="25fca-466">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="25fca-467">Qualquer combinação `compose` de , , `commandBox` `message` .</span><span class="sxs-lookup"><span data-stu-id="25fca-467">Any combination of`compose`,`commandBox`,`message`.</span></span> <span data-ttu-id="25fca-468">O padrão é `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="25fca-468">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="25fca-469">booliano</span><span class="sxs-lookup"><span data-stu-id="25fca-469">boolean</span></span>|||<span data-ttu-id="25fca-470">Um valor booleano que indica se ele deve buscar o módulo de tarefa dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="25fca-470">A boolean value that indicates if it must fetch the task module dynamically.</span></span> <span data-ttu-id="25fca-471">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="25fca-471">Default is **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="25fca-472">objeto</span><span class="sxs-lookup"><span data-stu-id="25fca-472">object</span></span>|||<span data-ttu-id="25fca-473">Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="25fca-473">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="25fca-474">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-474">string</span></span>|<span data-ttu-id="25fca-475">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-475">64 characters</span></span>||<span data-ttu-id="25fca-476">Título da caixa de diálogo inicial.</span><span class="sxs-lookup"><span data-stu-id="25fca-476">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="25fca-477">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-477">string</span></span>|||<span data-ttu-id="25fca-478">Largura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.</span><span class="sxs-lookup"><span data-stu-id="25fca-478">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="25fca-479">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-479">string</span></span>|||<span data-ttu-id="25fca-480">Altura da caixa de diálogo - um número em pixels ou layout padrão, como "grande", "médio" ou "pequeno".</span><span class="sxs-lookup"><span data-stu-id="25fca-480">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="25fca-481">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-481">string</span></span>|||<span data-ttu-id="25fca-482">URL do webview inicial.</span><span class="sxs-lookup"><span data-stu-id="25fca-482">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="25fca-483">matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="25fca-483">array of object</span></span>|<span data-ttu-id="25fca-484">5 itens</span><span class="sxs-lookup"><span data-stu-id="25fca-484">5 items</span></span>|<span data-ttu-id="25fca-485">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-485">✔</span></span>|<span data-ttu-id="25fca-486">A lista de parâmetros que o comando assume.</span><span class="sxs-lookup"><span data-stu-id="25fca-486">The list of parameters the command takes.</span></span> <span data-ttu-id="25fca-487">Mínimo: 1; máximo: 5.</span><span class="sxs-lookup"><span data-stu-id="25fca-487">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="25fca-488">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-488">string</span></span>|<span data-ttu-id="25fca-489">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-489">64 characters</span></span>|<span data-ttu-id="25fca-490">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-490">✔</span></span>|<span data-ttu-id="25fca-491">O nome do parâmetro como ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="25fca-491">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="25fca-492">Isso está incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="25fca-492">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="25fca-493">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-493">string</span></span>|<span data-ttu-id="25fca-494">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-494">32 characters</span></span>|<span data-ttu-id="25fca-495">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-495">✔</span></span>|<span data-ttu-id="25fca-496">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="25fca-496">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="25fca-497">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-497">string</span></span>|<span data-ttu-id="25fca-498">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-498">128 characters</span></span>||<span data-ttu-id="25fca-499">Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="25fca-499">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="25fca-500">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-500">string</span></span>|<span data-ttu-id="25fca-501">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-501">512 characters</span></span>||<span data-ttu-id="25fca-502">Valor inicial do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="25fca-502">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="25fca-503">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-503">string</span></span>|<span data-ttu-id="25fca-504">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-504">128 characters</span></span>||<span data-ttu-id="25fca-505">Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="25fca-505">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="25fca-506">Um de `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="25fca-506">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="25fca-507">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="25fca-507">array of objects</span></span>|<span data-ttu-id="25fca-508">10 itens</span><span class="sxs-lookup"><span data-stu-id="25fca-508">10 items</span></span>||<span data-ttu-id="25fca-509">As opções de escolha para `choiceset` o .</span><span class="sxs-lookup"><span data-stu-id="25fca-509">The choice options for the`choiceset`.</span></span> <span data-ttu-id="25fca-510">Use somente quando `parameter.inputType` for `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="25fca-510">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="25fca-511">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-511">string</span></span>|<span data-ttu-id="25fca-512">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-512">128 characters</span></span>|<span data-ttu-id="25fca-513">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-513">✔</span></span>|<span data-ttu-id="25fca-514">Título da escolha.</span><span class="sxs-lookup"><span data-stu-id="25fca-514">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="25fca-515">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-515">string</span></span>|<span data-ttu-id="25fca-516">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-516">512 characters</span></span>|<span data-ttu-id="25fca-517">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-517">✔</span></span>|<span data-ttu-id="25fca-518">O valor da escolha.</span><span class="sxs-lookup"><span data-stu-id="25fca-518">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="25fca-519">permissões</span><span class="sxs-lookup"><span data-stu-id="25fca-519">permissions</span></span>

<span data-ttu-id="25fca-520">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-520">**Optional** — array of strings</span></span>

<span data-ttu-id="25fca-521">Uma matriz da qual especifica quais permissões o aplicativo solicita, o que permite que os usuários finais `string` saibam como a extensão se executa.</span><span class="sxs-lookup"><span data-stu-id="25fca-521">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension performs.</span></span> <span data-ttu-id="25fca-522">As seguintes opções não são exclusivas:</span><span class="sxs-lookup"><span data-stu-id="25fca-522">The following options are non-exclusive:</span></span>

* <span data-ttu-id="25fca-523">`identity`&emsp;Requer informações de identidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="25fca-523">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="25fca-524">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="25fca-524">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="25fca-525">Alterar essas permissões durante a atualização do aplicativo faz com que os usuários repitam o processo de consentimento após executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="25fca-525">Changing these permissions during app update, causes your users to repeat the consent process after they run the updated app.</span></span> <span data-ttu-id="25fca-526">Consulte [Atualizando seu aplicativo para](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="25fca-526">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="25fca-527">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="25fca-527">devicePermissions</span></span>

<span data-ttu-id="25fca-528">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-528">**Optional** — array of strings</span></span>

<span data-ttu-id="25fca-529">Fornece os recursos nativos no dispositivo de um usuário ao que seu aplicativo solicita acesso.</span><span class="sxs-lookup"><span data-stu-id="25fca-529">Provides the native features on a user's device that your app requests access to.</span></span> <span data-ttu-id="25fca-530">As opções são:</span><span class="sxs-lookup"><span data-stu-id="25fca-530">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="25fca-531">validDomains</span><span class="sxs-lookup"><span data-stu-id="25fca-531">validDomains</span></span>

<span data-ttu-id="25fca-532">**Opcional**, exceto **Obrigatório quando** notado.</span><span class="sxs-lookup"><span data-stu-id="25fca-532">**Optional**, except **Required** where noted.</span></span>

<span data-ttu-id="25fca-533">Uma lista de domínios válidos para sites que o aplicativo espera carregar no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="25fca-533">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="25fca-534">Listagem de domínio pode incluir caracteres curinga, por exemplo, `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="25fca-534">Domain listings can include wildcards, for example, `*.example.com`.</span></span> <span data-ttu-id="25fca-535">Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="25fca-535">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="25fca-536">Se a configuração de tabulação ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de tabulação, esse domínio deve ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="25fca-536">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="25fca-537">Não é **necessário** incluir os domínios de provedores de identidade que você deseja dar suporte ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-537">It is **not** necessary to include the domains of identity providers you want to support in your app.</span></span> <span data-ttu-id="25fca-538">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para accounts.google.com, no entanto, você não deve incluir accounts.google.com em `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="25fca-538">For example, to authenticate using a Google ID, it is required to redirect to accounts.google.com, however, you must not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="25fca-539">Teams aplicativos que exigem que suas próprias URLs do sharepoint funcionem bem, inclui "{teamsitedomain}" em sua lista de domínios válida.</span><span class="sxs-lookup"><span data-stu-id="25fca-539">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25fca-540">Não adicione domínios que estão fora do seu controle, diretamente ou por meio de caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="25fca-540">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="25fca-541">Por exemplo, `yourapp.onmicrosoft.com` é válido, no entanto, `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="25fca-541">For example, `yourapp.onmicrosoft.com` is valid, however, `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="25fca-542">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="25fca-542">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="25fca-543">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="25fca-543">webApplicationInfo</span></span>

<span data-ttu-id="25fca-544">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="25fca-544">**Optional** — object</span></span>

<span data-ttu-id="25fca-545">Forneça sua Azure Active Directory (AAD) app ID e informações do Microsoft Graph para ajudar os usuários a entrar perfeitamente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-545">Provide your Azure Active Directory (AAD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="25fca-546">Se seu aplicativo estiver registrado no AAD, você deverá fornecer a ID do aplicativo, para que os administradores possam revisar facilmente as permissões e conceder consentimento Teams centro de administração.</span><span class="sxs-lookup"><span data-stu-id="25fca-546">If your app is registered in AAD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="25fca-547">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-547">Name</span></span>| <span data-ttu-id="25fca-548">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-548">Type</span></span>| <span data-ttu-id="25fca-549">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-549">Maximum size</span></span> | <span data-ttu-id="25fca-550">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-550">Required</span></span> | <span data-ttu-id="25fca-551">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-551">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="25fca-552">string</span><span class="sxs-lookup"><span data-stu-id="25fca-552">string</span></span>|<span data-ttu-id="25fca-553">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-553">36 characters</span></span>|<span data-ttu-id="25fca-554">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-554">✔</span></span>|<span data-ttu-id="25fca-555">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-555">AAD application id of the app.</span></span> <span data-ttu-id="25fca-556">Essa id deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="25fca-556">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="25fca-557">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-557">string</span></span>|<span data-ttu-id="25fca-558">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-558">2048 characters</span></span>|<span data-ttu-id="25fca-559">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-559">✔</span></span>|<span data-ttu-id="25fca-560">URL de recurso do aplicativo para adquirir token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="25fca-560">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="25fca-561">**OBSERVAÇÃO:** Se você não estiver usando o SSO, certifique-se de inserir um valor de cadeia de caracteres fictício neste campo para o manifesto do aplicativo, por exemplo, para evitar https://notapplicable uma resposta de erro.</span><span class="sxs-lookup"><span data-stu-id="25fca-561">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="25fca-562">matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-562">array of strings</span></span>|<span data-ttu-id="25fca-563">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-563">128 characters</span></span>||<span data-ttu-id="25fca-564">Especifique o [consentimento específico do recurso granular](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="25fca-564">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="25fca-565">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="25fca-565">showLoadingIndicator</span></span>

<span data-ttu-id="25fca-566">**Opcional** — booleano</span><span class="sxs-lookup"><span data-stu-id="25fca-566">**Optional** — boolean</span></span>

<span data-ttu-id="25fca-567">Indica se é ou não para mostrar o indicador de carregamento quando um aplicativo ou guia está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="25fca-567">Indicates whether or not to show the loading indicator when an app or tab is loading.</span></span> <span data-ttu-id="25fca-568">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="25fca-568">Default is **false**.</span></span>
>[!NOTE]
><span data-ttu-id="25fca-569">Se você selecionar como true no manifesto do aplicativo, para carregar a página corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa conforme descrito em Mostrar um documento indicador de carregamento `showLoadingIndicator` nativo. [](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)</span><span class="sxs-lookup"><span data-stu-id="25fca-569">If you select`showLoadingIndicator` as true in your app manifest, to load the page correctly, modify the content pages of your tabs and task modules as described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="25fca-570">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="25fca-570">isFullScreen</span></span>

 <span data-ttu-id="25fca-571">**Opcional** — booleano</span><span class="sxs-lookup"><span data-stu-id="25fca-571">**Optional** — boolean</span></span>

<span data-ttu-id="25fca-572">Indica onde um aplicativo pessoal é renderizado com ou sem uma barra de header de tabulação.</span><span class="sxs-lookup"><span data-stu-id="25fca-572">Indicate where a personal app is rendered with or without a tab header bar.</span></span> <span data-ttu-id="25fca-573">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="25fca-573">Default is **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="25fca-574">activities</span><span class="sxs-lookup"><span data-stu-id="25fca-574">activities</span></span>

<span data-ttu-id="25fca-575">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="25fca-575">**Optional** — object</span></span>

<span data-ttu-id="25fca-576">Defina as propriedades que seu aplicativo usa para postar um feed de atividade do usuário.</span><span class="sxs-lookup"><span data-stu-id="25fca-576">Define the properties your app uses to post a user activity feed.</span></span>

|<span data-ttu-id="25fca-577">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-577">Name</span></span>| <span data-ttu-id="25fca-578">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-578">Type</span></span>| <span data-ttu-id="25fca-579">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-579">Maximum size</span></span> | <span data-ttu-id="25fca-580">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-580">Required</span></span> | <span data-ttu-id="25fca-581">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-581">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="25fca-582">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="25fca-582">array of Objects</span></span>|<span data-ttu-id="25fca-583">128 itens</span><span class="sxs-lookup"><span data-stu-id="25fca-583">128 items</span></span>| | <span data-ttu-id="25fca-584">Forneça os tipos de atividades que seu aplicativo pode postar em um feed de atividades dos usuários.</span><span class="sxs-lookup"><span data-stu-id="25fca-584">Provide the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="25fca-585">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="25fca-585">activities.activityTypes</span></span>

|<span data-ttu-id="25fca-586">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-586">Name</span></span>| <span data-ttu-id="25fca-587">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-587">Type</span></span>| <span data-ttu-id="25fca-588">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-588">Maximum size</span></span> | <span data-ttu-id="25fca-589">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-589">Required</span></span> | <span data-ttu-id="25fca-590">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-590">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="25fca-591">string</span><span class="sxs-lookup"><span data-stu-id="25fca-591">string</span></span>|<span data-ttu-id="25fca-592">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-592">32 characters</span></span>|<span data-ttu-id="25fca-593">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-593">✔</span></span>|<span data-ttu-id="25fca-594">O tipo de notificação.</span><span class="sxs-lookup"><span data-stu-id="25fca-594">The notification type.</span></span> <span data-ttu-id="25fca-595">*Consulte abaixo*.</span><span class="sxs-lookup"><span data-stu-id="25fca-595">*See below*.</span></span>|
|`description`|<span data-ttu-id="25fca-596">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-596">string</span></span>|<span data-ttu-id="25fca-597">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-597">128 characters</span></span>|<span data-ttu-id="25fca-598">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-598">✔</span></span>|<span data-ttu-id="25fca-599">Uma breve descrição da notificação.</span><span class="sxs-lookup"><span data-stu-id="25fca-599">A brief description of the notification.</span></span> <span data-ttu-id="25fca-600">*Consulte abaixo*.</span><span class="sxs-lookup"><span data-stu-id="25fca-600">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="25fca-601">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-601">string</span></span>|<span data-ttu-id="25fca-602">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-602">128 characters</span></span>|<span data-ttu-id="25fca-603">✔</span><span class="sxs-lookup"><span data-stu-id="25fca-603">✔</span></span>|<span data-ttu-id="25fca-604">Ex: "{actor} criado tarefa {taskId} para você"</span><span class="sxs-lookup"><span data-stu-id="25fca-604">Ex: "{actor} created task {taskId} for you"</span></span>|

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

## <a name="defaultinstallscope"></a><span data-ttu-id="25fca-605">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="25fca-605">defaultInstallScope</span></span>

<span data-ttu-id="25fca-606">**Opcional** - cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-606">**Optional** - string</span></span>

<span data-ttu-id="25fca-607">Especifica o escopo de instalação definido para este aplicativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="25fca-607">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="25fca-608">O escopo definido será a opção exibida no botão quando um usuário tentar adicionar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-608">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="25fca-609">As opções são:</span><span class="sxs-lookup"><span data-stu-id="25fca-609">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="25fca-610">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="25fca-610">defaultGroupCapability</span></span>

<span data-ttu-id="25fca-611">**Opcional** - objeto</span><span class="sxs-lookup"><span data-stu-id="25fca-611">**Optional** - object</span></span>

<span data-ttu-id="25fca-612">Quando um escopo de instalação de grupo é selecionado, ele define o recurso padrão quando o usuário instala o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-612">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="25fca-613">As opções são:</span><span class="sxs-lookup"><span data-stu-id="25fca-613">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="25fca-614">Nome</span><span class="sxs-lookup"><span data-stu-id="25fca-614">Name</span></span>| <span data-ttu-id="25fca-615">Tipo</span><span class="sxs-lookup"><span data-stu-id="25fca-615">Type</span></span>| <span data-ttu-id="25fca-616">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="25fca-616">Maximum size</span></span> | <span data-ttu-id="25fca-617">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="25fca-617">Required</span></span> | <span data-ttu-id="25fca-618">Descrição</span><span class="sxs-lookup"><span data-stu-id="25fca-618">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="25fca-619">string</span><span class="sxs-lookup"><span data-stu-id="25fca-619">string</span></span>|||<span data-ttu-id="25fca-620">Quando o escopo de instalação selecionado for `team` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="25fca-620">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="25fca-621">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="25fca-621">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="25fca-622">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-622">string</span></span>|||<span data-ttu-id="25fca-623">Quando o escopo de instalação selecionado for `groupchat` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="25fca-623">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="25fca-624">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="25fca-624">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="25fca-625">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fca-625">string</span></span>|||<span data-ttu-id="25fca-626">Quando o escopo de instalação selecionado for `meetings` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="25fca-626">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="25fca-627">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="25fca-627">Options: `tab`, `bot`, or `connector`.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="25fca-628">configurableProperties</span><span class="sxs-lookup"><span data-stu-id="25fca-628">configurableProperties</span></span>

<span data-ttu-id="25fca-629">**Opcional** - matriz</span><span class="sxs-lookup"><span data-stu-id="25fca-629">**Optional** - array</span></span>

<span data-ttu-id="25fca-630">O `configurableProperties` bloco define as propriedades do aplicativo que os Teams administradores podem personalizar.</span><span class="sxs-lookup"><span data-stu-id="25fca-630">The `configurableProperties` block defines the app properties that Teams admins can customize.</span></span> <span data-ttu-id="25fca-631">Para obter mais informações, consulte [enable app customization](~/concepts/design/enable-app-customization.md).</span><span class="sxs-lookup"><span data-stu-id="25fca-631">For more information, see [enable app customization](~/concepts/design/enable-app-customization.md).</span></span>

> [!NOTE]
> <span data-ttu-id="25fca-632">Um mínimo de uma propriedade deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="25fca-632">A minimum of one property must be defined.</span></span> <span data-ttu-id="25fca-633">Você pode definir um máximo de nove propriedades neste bloco.</span><span class="sxs-lookup"><span data-stu-id="25fca-633">You can define a maximum of nine properties in this block.</span></span>

<span data-ttu-id="25fca-634">Você pode definir qualquer uma das seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="25fca-634">You can define any of the following properties:</span></span>

* <span data-ttu-id="25fca-635">`name`: O nome de exibição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-635">`name`: The app's display name.</span></span>
* <span data-ttu-id="25fca-636">`shortDescription`: A descrição curta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-636">`shortDescription`: The app's short description.</span></span>
* <span data-ttu-id="25fca-637">`longDescription`: A descrição detalhada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-637">`longDescription`: The app's detailed description.</span></span>
* <span data-ttu-id="25fca-638">`smallImageUrl`: O ícone de contorno do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-638">`smallImageUrl`: The app's outline icon.</span></span>
* <span data-ttu-id="25fca-639">`largeImageUrl`: O ícone de cor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25fca-639">`largeImageUrl`: The app's color icon.</span></span>
* <span data-ttu-id="25fca-640">`accentColor`: A cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="25fca-640">`accentColor`: The color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="25fca-641">`developerUrl`: A URL HTTPS do site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="25fca-641">`developerUrl`: The HTTPS URL of the developer's website.</span></span>
* <span data-ttu-id="25fca-642">`privacyUrl`: A URL HTTPS da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="25fca-642">`privacyUrl`: The HTTPS URL of the developer's privacy policy.</span></span>
* <span data-ttu-id="25fca-643">`termsOfUseUrl`: A URL HTTPS dos termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="25fca-643">`termsOfUseUrl`: The HTTPS URL of the developer's terms of use.</span></span>
