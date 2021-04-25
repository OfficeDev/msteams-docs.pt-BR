---
title: Referência de esquema de manifesto
description: Descreve o esquema de manifesto do Microsoft Teams
ms.topic: reference
ms.author: lajanuar
keywords: esquema de manifesto do teams
ms.openlocfilehash: d4dd299a9e848820e81f87361460b5b8b14f15b7
ms.sourcegitcommit: 7b4f383b506d4bc68a1b5641d6e0f404edbfbc6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2021
ms.locfileid: "51946442"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="9cdd6-104">Referência: esquema de manifesto para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9cdd6-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="9cdd6-105">O manifesto do Teams descreve como o aplicativo se integra ao produto do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-105">The Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="9cdd6-106">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="9cdd6-107">Versões anteriores 1.0-1.4 também são suportadas (usando "v1.x" na URL).</span><span class="sxs-lookup"><span data-stu-id="9cdd6-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="9cdd6-108">O exemplo de esquema a seguir mostra todas as opções de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="9cdd6-109">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-109">Sample full manifest</span></span>

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

<span data-ttu-id="9cdd6-110">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="9cdd6-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="9cdd6-111">$schema</span><span class="sxs-lookup"><span data-stu-id="9cdd6-111">$schema</span></span>

<span data-ttu-id="9cdd6-112">Opcional, mas recomendado — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-112">Optional, but recommended — string</span></span>

<span data-ttu-id="9cdd6-113">A https:// URL de referência do Esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="9cdd6-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="9cdd6-114">manifestVersion</span></span>

<span data-ttu-id="9cdd6-115">**Obrigatório —** cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-115">**Required** — string</span></span>

<span data-ttu-id="9cdd6-116">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-116">The version of manifest schema this manifest is using.</span></span> <span data-ttu-id="9cdd6-117">Deve ser 1,9.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-117">It must be 1.9.</span></span>

## <a name="version"></a><span data-ttu-id="9cdd6-118">versão</span><span class="sxs-lookup"><span data-stu-id="9cdd6-118">version</span></span>

<span data-ttu-id="9cdd6-119">**Obrigatório —** cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-119">**Required** — string</span></span>

<span data-ttu-id="9cdd6-120">A versão de um aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-120">The version of a specific app.</span></span> <span data-ttu-id="9cdd6-121">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-121">If you update something in your manifest, the version must be incremented too.</span></span> <span data-ttu-id="9cdd6-122">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-122">This way, when the new manifest is installed, it overwrites the existing one and the user receives the new functionality.</span></span> <span data-ttu-id="9cdd6-123">Se esse aplicativo foi enviado para a loja, o novo manifesto deve ser re-enviado e validado.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-123">If this app was submitted to the store, the new manifest must be re-submitted and re-validated.</span></span> <span data-ttu-id="9cdd6-124">Os usuários do aplicativo recebem o novo manifesto atualizado automaticamente dentro de algumas horas após a aprovação do manifesto.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-124">The app users receive the new updated manifest automatically within few hours after the manifest is approved.</span></span>

<span data-ttu-id="9cdd6-125">Se as solicitações de aplicativos para permissões mudarem, os usuários serão solicitados a atualizar e consentir de novo para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-125">If the app requests for permissions change, the users are prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="9cdd6-126">Esta cadeia de caracteres de versão deve seguir o padrão [de semver](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="9cdd6-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="9cdd6-127">id</span><span class="sxs-lookup"><span data-stu-id="9cdd6-127">id</span></span>

<span data-ttu-id="9cdd6-128">**Obrigatório** — ID do aplicativo Microsoft</span><span class="sxs-lookup"><span data-stu-id="9cdd6-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="9cdd6-129">A ID é um identificador exclusivo gerado pela Microsoft para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-129">The ID is a unique Microsoft-generated identifier for the app.</span></span> <span data-ttu-id="9cdd6-130">Você tem uma ID se o bot estiver registrado por meio da Estrutura do Microsoft Bot ou do aplicativo Web da guia já entrar com a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-130">You have an ID if your bot is registered through the Microsoft Bot Framework or your tab's web app already signs in with Microsoft.</span></span> <span data-ttu-id="9cdd6-131">Você deve inserir a ID aqui.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-131">You must enter the ID here.</span></span> <span data-ttu-id="9cdd6-132">Caso contrário, você deve gerar uma nova ID no Portal de [Registro de Aplicativos da Microsoft.](https://aka.ms/appregistrations)</span><span class="sxs-lookup"><span data-stu-id="9cdd6-132">Otherwise, you must generate a new ID at the [Microsoft Application Registration Portal](https://aka.ms/appregistrations).</span></span> <span data-ttu-id="9cdd6-133">Use a mesma ID se você adicionar um bot.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-133">Use the same ID if you add a bot.</span></span>

> [!NOTE]
> <span data-ttu-id="9cdd6-134">Se você estiver enviando uma atualização para seu aplicativo existente no AppSource, a ID em seu manifesto não deve ser modificada.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-134">If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="9cdd6-135">developer</span><span class="sxs-lookup"><span data-stu-id="9cdd6-135">developer</span></span>

<span data-ttu-id="9cdd6-136">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="9cdd6-136">**Required** — object</span></span>

<span data-ttu-id="9cdd6-137">Fornece informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-137">Gives information about your company.</span></span> <span data-ttu-id="9cdd6-138">Para aplicativos enviados ao AppSource (antigo Office Store), esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-138">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="9cdd6-139">Consulte as [diretrizes de publicação](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) para obter informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-139">See the [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="9cdd6-140">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-140">Name</span></span>| <span data-ttu-id="9cdd6-141">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-141">Maximum size</span></span> | <span data-ttu-id="9cdd6-142">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-142">Required</span></span> | <span data-ttu-id="9cdd6-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-143">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="9cdd6-144">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-144">32 characters</span></span>|<span data-ttu-id="9cdd6-145">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-145">✔</span></span>|<span data-ttu-id="9cdd6-146">O nome de exibição do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-146">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="9cdd6-147">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-147">2048 characters</span></span>|<span data-ttu-id="9cdd6-148">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-148">✔</span></span>|<span data-ttu-id="9cdd6-149">A https:// URL do site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-149">The https:// URL to the developer's website.</span></span> <span data-ttu-id="9cdd6-150">Este link deve levar os usuários para a sua empresa ou página de aterrissagem específica do produto.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-150">This link must take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="9cdd6-151">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-151">2048 characters</span></span>|<span data-ttu-id="9cdd6-152">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-152">✔</span></span>|<span data-ttu-id="9cdd6-153">A https:// URL da política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-153">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="9cdd6-154">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-154">2048 characters</span></span>|<span data-ttu-id="9cdd6-155">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-155">✔</span></span>|<span data-ttu-id="9cdd6-156">A https:// URL dos termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-156">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="9cdd6-157">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-157">10 characters</span></span>| |<span data-ttu-id="9cdd6-158">**Opcional** A ID da Rede de Parceiros da Microsoft que identifica a organização do parceiro que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-158">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="9cdd6-159">nome</span><span class="sxs-lookup"><span data-stu-id="9cdd6-159">name</span></span>

<span data-ttu-id="9cdd6-160">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="9cdd6-160">**Required** — object</span></span>

<span data-ttu-id="9cdd6-161">O nome da experiência do aplicativo, exibido para os usuários na experiência do Teams.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-161">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="9cdd6-162">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-162">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="9cdd6-163">Os valores de `short` e `full` devem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-163">The values of `short` and `full` must be different.</span></span>

|<span data-ttu-id="9cdd6-164">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-164">Name</span></span>| <span data-ttu-id="9cdd6-165">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-165">Maximum size</span></span> | <span data-ttu-id="9cdd6-166">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-166">Required</span></span> | <span data-ttu-id="9cdd6-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-167">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="9cdd6-168">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-168">30 characters</span></span>|<span data-ttu-id="9cdd6-169">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-169">✔</span></span>|<span data-ttu-id="9cdd6-170">O nome de exibição curto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-170">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="9cdd6-171">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-171">100 characters</span></span>||<span data-ttu-id="9cdd6-172">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-172">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="9cdd6-173">description</span><span class="sxs-lookup"><span data-stu-id="9cdd6-173">description</span></span>

<span data-ttu-id="9cdd6-174">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="9cdd6-174">**Required** — object</span></span>

<span data-ttu-id="9cdd6-175">Descreve seu aplicativo para usuários.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-175">Describes your app to users.</span></span> <span data-ttu-id="9cdd6-176">Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-176">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="9cdd6-177">Verifique se sua descrição descreve com precisão sua experiência e fornece informações para ajudar os clientes em potencial a entender o que sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-177">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="9cdd6-178">Você deve observar na descrição completa, se uma conta externa for necessária para uso.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-178">You must note in the full description, if an external account is required for use.</span></span> <span data-ttu-id="9cdd6-179">Os valores de `short` e `full` devem ser diferentes.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-179">The values of `short` and `full` must be different.</span></span> <span data-ttu-id="9cdd6-180">Sua breve descrição não deve ser repetida na descrição longa e não deve incluir nenhum outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-180">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="9cdd6-181">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-181">Name</span></span>| <span data-ttu-id="9cdd6-182">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-182">Maximum size</span></span> | <span data-ttu-id="9cdd6-183">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-183">Required</span></span> | <span data-ttu-id="9cdd6-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-184">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="9cdd6-185">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-185">80 characters</span></span>|<span data-ttu-id="9cdd6-186">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-186">✔</span></span>|<span data-ttu-id="9cdd6-187">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-187">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="9cdd6-188">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-188">4000 characters</span></span>|<span data-ttu-id="9cdd6-189">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-189">✔</span></span>|<span data-ttu-id="9cdd6-190">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-190">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="9cdd6-191">packageName</span><span class="sxs-lookup"><span data-stu-id="9cdd6-191">packageName</span></span>

<span data-ttu-id="9cdd6-192">**Opcional** — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-192">**Optional** — string</span></span>

<span data-ttu-id="9cdd6-193">Um identificador exclusivo para o aplicativo na notação de domínio reverso; por exemplo, com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-193">A unique identifier for the app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="9cdd6-194">Comprimento máximo: 64 caracteres.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-194">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="9cdd6-195">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-195">localizationInfo</span></span>

<span data-ttu-id="9cdd6-196">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="9cdd6-196">**Optional** — object</span></span>

<span data-ttu-id="9cdd6-197">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-197">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="9cdd6-198">Consulte [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="9cdd6-198">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="9cdd6-199">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-199">Name</span></span>| <span data-ttu-id="9cdd6-200">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-200">Maximum size</span></span> | <span data-ttu-id="9cdd6-201">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-201">Required</span></span> | <span data-ttu-id="9cdd6-202">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-202">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="9cdd6-203">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-203">✔</span></span>|<span data-ttu-id="9cdd6-204">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-204">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="9cdd6-205">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="9cdd6-205">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="9cdd6-206">Uma matriz de objetos que especifica traduções de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-206">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="9cdd6-207">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-207">Name</span></span>| <span data-ttu-id="9cdd6-208">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-208">Maximum size</span></span> | <span data-ttu-id="9cdd6-209">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-209">Required</span></span> | <span data-ttu-id="9cdd6-210">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-210">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="9cdd6-211">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-211">✔</span></span>|<span data-ttu-id="9cdd6-212">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-212">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="9cdd6-213">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-213">✔</span></span>|<span data-ttu-id="9cdd6-214">Um caminho de arquivo relativo para um arquivo .json que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-214">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="9cdd6-215">ícones</span><span class="sxs-lookup"><span data-stu-id="9cdd6-215">icons</span></span>

<span data-ttu-id="9cdd6-216">**Obrigatório —** objeto</span><span class="sxs-lookup"><span data-stu-id="9cdd6-216">**Required** — object</span></span>

<span data-ttu-id="9cdd6-217">Ícones usados no aplicativo teams.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-217">Icons used within the Teams app.</span></span> <span data-ttu-id="9cdd6-218">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-218">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="9cdd6-219">Consulte [Ícones](../../concepts/build-and-test/apps-package.md#app-icons) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-219">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="9cdd6-220">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-220">Name</span></span>| <span data-ttu-id="9cdd6-221">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-221">Maximum size</span></span> | <span data-ttu-id="9cdd6-222">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-222">Required</span></span> | <span data-ttu-id="9cdd6-223">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="9cdd6-224">32 x 32 pixels</span><span class="sxs-lookup"><span data-stu-id="9cdd6-224">32 x 32 pixels</span></span>|<span data-ttu-id="9cdd6-225">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-225">✔</span></span>|<span data-ttu-id="9cdd6-226">Um caminho de arquivo relativo para um ícone de contorno PNG 32x32 transparente.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="9cdd6-227">192 x 192 pixels</span><span class="sxs-lookup"><span data-stu-id="9cdd6-227">192 x 192 pixels</span></span>|<span data-ttu-id="9cdd6-228">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-228">✔</span></span>|<span data-ttu-id="9cdd6-229">Um caminho de arquivo relativo para um ícone PNG de cor total 192x192.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="9cdd6-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="9cdd6-230">accentColor</span></span>

<span data-ttu-id="9cdd6-231">**Opcional** — código de cor de Hex HTML</span><span class="sxs-lookup"><span data-stu-id="9cdd6-231">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="9cdd6-232">Uma cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="9cdd6-233">O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="9cdd6-234">configurbleTabs</span><span class="sxs-lookup"><span data-stu-id="9cdd6-234">configurableTabs</span></span>

<span data-ttu-id="9cdd6-235">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="9cdd6-235">**Optional** — array</span></span>

<span data-ttu-id="9cdd6-236">Usado quando a experiência do aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="9cdd6-237">As guias configuráveis têm suporte apenas no escopo das equipes (não pessoal) e atualmente há suporte para apenas uma **guia** por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-237">Configurable tabs are supported only in the teams scope (not personal), and currently only **one** tab per app is supported.</span></span>

|<span data-ttu-id="9cdd6-238">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-238">Name</span></span>| <span data-ttu-id="9cdd6-239">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-239">Type</span></span>| <span data-ttu-id="9cdd6-240">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-240">Maximum size</span></span> | <span data-ttu-id="9cdd6-241">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-241">Required</span></span> | <span data-ttu-id="9cdd6-242">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-242">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="9cdd6-243">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-243">string</span></span>|<span data-ttu-id="9cdd6-244">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-244">2048 characters</span></span>|<span data-ttu-id="9cdd6-245">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-245">✔</span></span>|<span data-ttu-id="9cdd6-246">A https:// URL a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-246">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="9cdd6-247">matriz de números</span><span class="sxs-lookup"><span data-stu-id="9cdd6-247">array of enums</span></span>|<span data-ttu-id="9cdd6-248">1</span><span class="sxs-lookup"><span data-stu-id="9cdd6-248">1</span></span>|<span data-ttu-id="9cdd6-249">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-249">✔</span></span>|<span data-ttu-id="9cdd6-250">Atualmente, as guias configuráveis suportam apenas `team` os `groupchat` escopos e.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-250">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="9cdd6-251">booliano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-251">boolean</span></span>|||<span data-ttu-id="9cdd6-252">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-252">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="9cdd6-253">Padrão: **true**.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-253">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="9cdd6-254">matriz de números</span><span class="sxs-lookup"><span data-stu-id="9cdd6-254">array of enums</span></span>|<span data-ttu-id="9cdd6-255">6 </span><span class="sxs-lookup"><span data-stu-id="9cdd6-255">6</span></span>||<span data-ttu-id="9cdd6-256">O conjunto de `contextItem` escopos em que há suporte para uma guia.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-256">The set of `contextItem` scopes where a tab is supported.</span></span> <span data-ttu-id="9cdd6-257">Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-257">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="9cdd6-258">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-258">string</span></span>|<span data-ttu-id="9cdd6-259">2048</span><span class="sxs-lookup"><span data-stu-id="9cdd6-259">2048</span></span>||<span data-ttu-id="9cdd6-260">Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-260">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="9cdd6-261">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-261">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="9cdd6-262">matriz de números</span><span class="sxs-lookup"><span data-stu-id="9cdd6-262">array of enums</span></span>|<span data-ttu-id="9cdd6-263">1</span><span class="sxs-lookup"><span data-stu-id="9cdd6-263">1</span></span>||<span data-ttu-id="9cdd6-264">Define como sua guia é disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-264">Defines how your tab is made available in SharePoint.</span></span> <span data-ttu-id="9cdd6-265">As opções `sharePointFullPage` são e `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="9cdd6-265">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="9cdd6-266">staticTabs</span><span class="sxs-lookup"><span data-stu-id="9cdd6-266">staticTabs</span></span>

<span data-ttu-id="9cdd6-267">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="9cdd6-267">**Optional** — array</span></span>

<span data-ttu-id="9cdd6-268">Define um conjunto de guias que podem ser "fixados" por padrão, sem que o usuário as adicione manualmente.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-268">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="9cdd6-269">As guias estáticas declaradas no `personal` escopo são sempre fixadas à experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-269">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="9cdd6-270">No momento, as guias estáticas declaradas no `team` escopo não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-270">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="9cdd6-271">Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-271">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="9cdd6-272">Esse bloco só é necessário para soluções que fornecem uma solução de tabulação estática.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-272">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="9cdd6-273">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-273">Name</span></span>| <span data-ttu-id="9cdd6-274">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-274">Type</span></span>| <span data-ttu-id="9cdd6-275">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-275">Maximum size</span></span> | <span data-ttu-id="9cdd6-276">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-276">Required</span></span> | <span data-ttu-id="9cdd6-277">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-277">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="9cdd6-278">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-278">string</span></span>|<span data-ttu-id="9cdd6-279">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-279">64 characters</span></span>|<span data-ttu-id="9cdd6-280">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-280">✔</span></span>|<span data-ttu-id="9cdd6-281">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-281">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="9cdd6-282">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-282">string</span></span>|<span data-ttu-id="9cdd6-283">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-283">128 characters</span></span>|<span data-ttu-id="9cdd6-284">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-284">✔</span></span>|<span data-ttu-id="9cdd6-285">O nome de exibição da guia na interface do canal.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-285">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="9cdd6-286">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-286">string</span></span>||<span data-ttu-id="9cdd6-287">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-287">✔</span></span>|<span data-ttu-id="9cdd6-288">A https:// URL que aponta para a interface do usuário da entidade a ser exibida na tela do Teams.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-288">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="9cdd6-289">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-289">string</span></span>|||<span data-ttu-id="9cdd6-290">A https:// URL para apontar se um usuário optar por exibir em um navegador.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-290">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="9cdd6-291">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-291">string</span></span>|||<span data-ttu-id="9cdd6-292">A https:// URL a ser apontada para as consultas de pesquisa de um usuário.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-292">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="9cdd6-293">matriz de números</span><span class="sxs-lookup"><span data-stu-id="9cdd6-293">array of enums</span></span>|<span data-ttu-id="9cdd6-294">1</span><span class="sxs-lookup"><span data-stu-id="9cdd6-294">1</span></span>|<span data-ttu-id="9cdd6-295">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-295">✔</span></span>|<span data-ttu-id="9cdd6-296">Atualmente, as guias estáticas suportam apenas o escopo, o que significa que ele só pode ser `personal` provisionado como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-296">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="9cdd6-297">matriz de números</span><span class="sxs-lookup"><span data-stu-id="9cdd6-297">array of enums</span></span>| <span data-ttu-id="9cdd6-298">2</span><span class="sxs-lookup"><span data-stu-id="9cdd6-298">2</span></span>|| <span data-ttu-id="9cdd6-299">O conjunto de `contextItem` escopos em que há suporte para uma guia.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-299">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
> <span data-ttu-id="9cdd6-300">Se suas guias exigirem informações dependentes de contexto para exibir  conteúdo relevante ou para iniciar um fluxo de autenticação, consulte Obter contexto para a [guia Microsoft Teams](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="9cdd6-300">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="9cdd6-301">bots</span><span class="sxs-lookup"><span data-stu-id="9cdd6-301">bots</span></span>

<span data-ttu-id="9cdd6-302">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="9cdd6-302">**Optional** — array</span></span>

<span data-ttu-id="9cdd6-303">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-303">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="9cdd6-304">O item é uma matriz (máximo de apenas 1 elemento atualmente, apenas um bot é permitido por aplicativo) com todos os elementos &mdash; do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-304">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="9cdd6-305">Esse bloco só é necessário para soluções que fornecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-305">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="9cdd6-306">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-306">Name</span></span>| <span data-ttu-id="9cdd6-307">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-307">Type</span></span>| <span data-ttu-id="9cdd6-308">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-308">Maximum size</span></span> | <span data-ttu-id="9cdd6-309">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-309">Required</span></span> | <span data-ttu-id="9cdd6-310">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-310">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="9cdd6-311">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-311">string</span></span>|<span data-ttu-id="9cdd6-312">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-312">64 characters</span></span>|<span data-ttu-id="9cdd6-313">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-313">✔</span></span>|<span data-ttu-id="9cdd6-314">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-314">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="9cdd6-315">Isso pode ser o mesmo da ID geral [do aplicativo.](#id)</span><span class="sxs-lookup"><span data-stu-id="9cdd6-315">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="9cdd6-316">matriz de números</span><span class="sxs-lookup"><span data-stu-id="9cdd6-316">array of enums</span></span>|<span data-ttu-id="9cdd6-317">3</span><span class="sxs-lookup"><span data-stu-id="9cdd6-317">3</span></span>|<span data-ttu-id="9cdd6-318">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-318">✔</span></span>|<span data-ttu-id="9cdd6-319">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="9cdd6-319">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="9cdd6-320">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-320">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="9cdd6-321">booliano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-321">boolean</span></span>|||<span data-ttu-id="9cdd6-322">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-322">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="9cdd6-323">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="9cdd6-323">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="9cdd6-324">booliano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-324">boolean</span></span>|||<span data-ttu-id="9cdd6-325">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-325">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="9cdd6-326">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="9cdd6-326">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="9cdd6-327">booliano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-327">boolean</span></span>|||<span data-ttu-id="9cdd6-328">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-328">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="9cdd6-329">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="9cdd6-329">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="9cdd6-330">booliano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-330">boolean</span></span>|||<span data-ttu-id="9cdd6-331">Um valor que indica onde um bot dá suporte à chamada de áudio.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-331">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="9cdd6-332">**IMPORTANTE**: Esta propriedade é experimental no momento.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-332">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="9cdd6-333">As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-333">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="9cdd6-334">Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-334">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="9cdd6-335">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="9cdd6-335">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="9cdd6-336">booliano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-336">boolean</span></span>|||<span data-ttu-id="9cdd6-337">Um valor que indica onde um bot dá suporte à chamada de vídeo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-337">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="9cdd6-338">**IMPORTANTE**: Esta propriedade é experimental no momento.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-338">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="9cdd6-339">As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-339">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="9cdd6-340">Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-340">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="9cdd6-341">Padrão: **`false`**</span><span class="sxs-lookup"><span data-stu-id="9cdd6-341">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="9cdd6-342">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="9cdd6-342">bots.commandLists</span></span>

<span data-ttu-id="9cdd6-343">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-343">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="9cdd6-344">O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo; você deve definir uma lista de comandos separada para cada escopo que `object` seu bot oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-344">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="9cdd6-345">Consulte [Menus bot para](~/bots/how-to/create-a-bot-commands-menu.md) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-345">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="9cdd6-346">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-346">Name</span></span>| <span data-ttu-id="9cdd6-347">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-347">Type</span></span>| <span data-ttu-id="9cdd6-348">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-348">Maximum size</span></span> | <span data-ttu-id="9cdd6-349">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-349">Required</span></span> | <span data-ttu-id="9cdd6-350">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-350">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="9cdd6-351">matriz de números</span><span class="sxs-lookup"><span data-stu-id="9cdd6-351">array of enums</span></span>|<span data-ttu-id="9cdd6-352">3</span><span class="sxs-lookup"><span data-stu-id="9cdd6-352">3</span></span>|<span data-ttu-id="9cdd6-353">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-353">✔</span></span>|<span data-ttu-id="9cdd6-354">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-354">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="9cdd6-355">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-355">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="9cdd6-356">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="9cdd6-356">array of objects</span></span>|<span data-ttu-id="9cdd6-357">10 </span><span class="sxs-lookup"><span data-stu-id="9cdd6-357">10</span></span>|<span data-ttu-id="9cdd6-358">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-358">✔</span></span>|<span data-ttu-id="9cdd6-359">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="9cdd6-359">An array of commands the bot supports:</span></span><br><span data-ttu-id="9cdd6-360">`title`: o nome do comando bot (cadeia, 32)</span><span class="sxs-lookup"><span data-stu-id="9cdd6-360">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="9cdd6-361">`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)</span><span class="sxs-lookup"><span data-stu-id="9cdd6-361">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="9cdd6-362">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="9cdd6-362">bots.commandLists.commands</span></span>

|<span data-ttu-id="9cdd6-363">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-363">Name</span></span>| <span data-ttu-id="9cdd6-364">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-364">Type</span></span>| <span data-ttu-id="9cdd6-365">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-365">Maximum size</span></span> | <span data-ttu-id="9cdd6-366">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-366">Required</span></span> | <span data-ttu-id="9cdd6-367">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-367">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="9cdd6-368">title</span><span class="sxs-lookup"><span data-stu-id="9cdd6-368">title</span></span>|<span data-ttu-id="9cdd6-369">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-369">string</span></span>|<span data-ttu-id="9cdd6-370">12 </span><span class="sxs-lookup"><span data-stu-id="9cdd6-370">12</span></span>|<span data-ttu-id="9cdd6-371">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-371">✔</span></span>|<span data-ttu-id="9cdd6-372">O nome do comando bot</span><span class="sxs-lookup"><span data-stu-id="9cdd6-372">The bot command name</span></span>|
|<span data-ttu-id="9cdd6-373">description</span><span class="sxs-lookup"><span data-stu-id="9cdd6-373">description</span></span>|<span data-ttu-id="9cdd6-374">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-374">string</span></span>|<span data-ttu-id="9cdd6-375">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-375">128 characters</span></span>|<span data-ttu-id="9cdd6-376">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-376">✔</span></span>|<span data-ttu-id="9cdd6-377">Uma descrição de texto simples ou um exemplo da sintaxe de comando e seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-377">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="9cdd6-378">conectores</span><span class="sxs-lookup"><span data-stu-id="9cdd6-378">connectors</span></span>

<span data-ttu-id="9cdd6-379">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="9cdd6-379">**Optional** — array</span></span>

<span data-ttu-id="9cdd6-380">O `connectors` bloco define um Conector do Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-380">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="9cdd6-381">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-381">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="9cdd6-382">Esse bloco só é necessário para soluções que fornecem um Conector.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-382">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="9cdd6-383">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-383">Name</span></span>| <span data-ttu-id="9cdd6-384">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-384">Type</span></span>| <span data-ttu-id="9cdd6-385">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-385">Maximum size</span></span> | <span data-ttu-id="9cdd6-386">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-386">Required</span></span> | <span data-ttu-id="9cdd6-387">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-387">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="9cdd6-388">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-388">string</span></span>|<span data-ttu-id="9cdd6-389">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-389">2048 characters</span></span>|<span data-ttu-id="9cdd6-390">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-390">✔</span></span>|<span data-ttu-id="9cdd6-391">A https:// URL a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-391">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="9cdd6-392">matriz de números</span><span class="sxs-lookup"><span data-stu-id="9cdd6-392">array of enums</span></span>|<span data-ttu-id="9cdd6-393">1</span><span class="sxs-lookup"><span data-stu-id="9cdd6-393">1</span></span>|<span data-ttu-id="9cdd6-394">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-394">✔</span></span>|<span data-ttu-id="9cdd6-395">Especifica se o Conector oferece uma experiência no contexto de um canal em um , ou uma experiência com escopo apenas para um `team` usuário individual ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="9cdd6-395">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="9cdd6-396">Atualmente, apenas o `team` escopo é suportado.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-396">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="9cdd6-397">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-397">string</span></span>|<span data-ttu-id="9cdd6-398">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-398">64 characters</span></span>|<span data-ttu-id="9cdd6-399">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-399">✔</span></span>|<span data-ttu-id="9cdd6-400">Um identificador exclusivo para o Conector que corresponde à sua ID no [Painel do Desenvolvedor de Conectores.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="9cdd6-400">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="9cdd6-401">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="9cdd6-401">composeExtensions</span></span>

<span data-ttu-id="9cdd6-402">**Opcional** — matriz</span><span class="sxs-lookup"><span data-stu-id="9cdd6-402">**Optional** — array</span></span>

<span data-ttu-id="9cdd6-403">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-403">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="9cdd6-404">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem funcionando.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-404">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="9cdd6-405">O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-405">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="9cdd6-406">Esse bloco só é necessário para soluções que fornecem uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-406">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="9cdd6-407">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-407">Name</span></span>| <span data-ttu-id="9cdd6-408">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-408">Type</span></span> | <span data-ttu-id="9cdd6-409">Tamanho Máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-409">Maximum Size</span></span> | <span data-ttu-id="9cdd6-410">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-410">Required</span></span> | <span data-ttu-id="9cdd6-411">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-411">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="9cdd6-412">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-412">string</span></span>|<span data-ttu-id="9cdd6-413">64</span><span class="sxs-lookup"><span data-stu-id="9cdd6-413">64</span></span>|<span data-ttu-id="9cdd6-414">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-414">✔</span></span>|<span data-ttu-id="9cdd6-415">A ID de aplicativo exclusiva da Microsoft para o bot que é o suporte à extensão de mensagens, conforme registrado na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-415">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="9cdd6-416">Isso pode ser o mesmo que a ID geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-416">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="9cdd6-417">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="9cdd6-417">array of objects</span></span>|<span data-ttu-id="9cdd6-418">10 </span><span class="sxs-lookup"><span data-stu-id="9cdd6-418">10</span></span>|<span data-ttu-id="9cdd6-419">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-419">✔</span></span>|<span data-ttu-id="9cdd6-420">Matriz de comandos com suporte da extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="9cdd6-420">Array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="9cdd6-421">booliano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-421">boolean</span></span>|||<span data-ttu-id="9cdd6-422">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-422">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="9cdd6-423">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-423">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="9cdd6-424">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="9cdd6-424">array of Objects</span></span>|<span data-ttu-id="9cdd6-425">5 </span><span class="sxs-lookup"><span data-stu-id="9cdd6-425">5</span></span>||<span data-ttu-id="9cdd6-426">Uma lista de manipuladores que permitem que os aplicativos sejam invocados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-426">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="9cdd6-427">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-427">string</span></span>|||<span data-ttu-id="9cdd6-428">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-428">The type of message handler.</span></span> <span data-ttu-id="9cdd6-429">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-429">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="9cdd6-430">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-430">array of Strings</span></span>|||<span data-ttu-id="9cdd6-431">Matriz de domínios que o manipulador de mensagens de link pode registrar.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-431">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="9cdd6-432">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="9cdd6-432">composeExtensions.commands</span></span>

<span data-ttu-id="9cdd6-433">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-433">Your messaging extension must declare one or more commands.</span></span> <span data-ttu-id="9cdd6-434">Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-434">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="9cdd6-435">Há no máximo 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-435">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="9cdd6-436">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="9cdd6-436">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="9cdd6-437">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-437">Name</span></span>| <span data-ttu-id="9cdd6-438">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-438">Type</span></span>| <span data-ttu-id="9cdd6-439">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-439">Maximum size</span></span> | <span data-ttu-id="9cdd6-440">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-440">Required</span></span> | <span data-ttu-id="9cdd6-441">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-441">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="9cdd6-442">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-442">string</span></span>|<span data-ttu-id="9cdd6-443">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-443">64 characters</span></span>|<span data-ttu-id="9cdd6-444">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-444">✔</span></span>|<span data-ttu-id="9cdd6-445">A ID do comando.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-445">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="9cdd6-446">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-446">string</span></span>|<span data-ttu-id="9cdd6-447">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-447">32 characters</span></span>|<span data-ttu-id="9cdd6-448">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-448">✔</span></span>|<span data-ttu-id="9cdd6-449">O nome de comando amigável.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-449">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="9cdd6-450">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-450">string</span></span>|<span data-ttu-id="9cdd6-451">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-451">64 characters</span></span>||<span data-ttu-id="9cdd6-452">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-452">Type of the command.</span></span> <span data-ttu-id="9cdd6-453">Um dos `query` ou `action` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-453">One of `query` or `action`.</span></span> <span data-ttu-id="9cdd6-454">Padrão: **consulta**.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-454">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="9cdd6-455">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-455">string</span></span>|<span data-ttu-id="9cdd6-456">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-456">128 characters</span></span>||<span data-ttu-id="9cdd6-457">A descrição que aparece para os usuários para indicar a finalidade deste comando.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-457">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="9cdd6-458">booliano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-458">boolean</span></span>|||<span data-ttu-id="9cdd6-459">Um valor booleano indica se o comando é executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-459">A boolean value indicates whether the command runs initially with no parameters.</span></span> <span data-ttu-id="9cdd6-460">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-460">Default is **false**.</span></span>|
|`context`|<span data-ttu-id="9cdd6-461">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-461">array of Strings</span></span>|<span data-ttu-id="9cdd6-462">3</span><span class="sxs-lookup"><span data-stu-id="9cdd6-462">3</span></span>||<span data-ttu-id="9cdd6-463">Define de onde a extensão da mensagem pode ser invocada.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-463">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="9cdd6-464">Qualquer combinação `compose` de , , `commandBox` `message` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-464">Any combination of`compose`,`commandBox`,`message`.</span></span> <span data-ttu-id="9cdd6-465">O padrão é `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-465">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="9cdd6-466">booliano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-466">boolean</span></span>|||<span data-ttu-id="9cdd6-467">Um valor booleano que indica se ele deve buscar o módulo de tarefa dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-467">A boolean value that indicates if it must fetch the task module dynamically.</span></span> <span data-ttu-id="9cdd6-468">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-468">Default is **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="9cdd6-469">objeto</span><span class="sxs-lookup"><span data-stu-id="9cdd6-469">object</span></span>|||<span data-ttu-id="9cdd6-470">Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-470">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="9cdd6-471">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-471">string</span></span>|<span data-ttu-id="9cdd6-472">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-472">64 characters</span></span>||<span data-ttu-id="9cdd6-473">Título da caixa de diálogo inicial.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-473">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="9cdd6-474">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-474">string</span></span>|||<span data-ttu-id="9cdd6-475">Largura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-475">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="9cdd6-476">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-476">string</span></span>|||<span data-ttu-id="9cdd6-477">Altura da caixa de diálogo - um número em pixels ou layout padrão, como "grande", "médio" ou "pequeno".</span><span class="sxs-lookup"><span data-stu-id="9cdd6-477">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="9cdd6-478">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-478">string</span></span>|||<span data-ttu-id="9cdd6-479">URL do webview inicial.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-479">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="9cdd6-480">matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="9cdd6-480">array of object</span></span>|<span data-ttu-id="9cdd6-481">5 itens</span><span class="sxs-lookup"><span data-stu-id="9cdd6-481">5 items</span></span>|<span data-ttu-id="9cdd6-482">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-482">✔</span></span>|<span data-ttu-id="9cdd6-483">A lista de parâmetros que o comando assume.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-483">The list of parameters the command takes.</span></span> <span data-ttu-id="9cdd6-484">Mínimo: 1; máximo: 5.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-484">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="9cdd6-485">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-485">string</span></span>|<span data-ttu-id="9cdd6-486">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-486">64 characters</span></span>|<span data-ttu-id="9cdd6-487">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-487">✔</span></span>|<span data-ttu-id="9cdd6-488">O nome do parâmetro como ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-488">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="9cdd6-489">Isso está incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-489">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="9cdd6-490">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-490">string</span></span>|<span data-ttu-id="9cdd6-491">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-491">32 characters</span></span>|<span data-ttu-id="9cdd6-492">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-492">✔</span></span>|<span data-ttu-id="9cdd6-493">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-493">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="9cdd6-494">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-494">string</span></span>|<span data-ttu-id="9cdd6-495">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-495">128 characters</span></span>||<span data-ttu-id="9cdd6-496">Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-496">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="9cdd6-497">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-497">string</span></span>|<span data-ttu-id="9cdd6-498">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-498">512 characters</span></span>||<span data-ttu-id="9cdd6-499">Valor inicial do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-499">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="9cdd6-500">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-500">string</span></span>|<span data-ttu-id="9cdd6-501">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-501">128 characters</span></span>||<span data-ttu-id="9cdd6-502">Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-502">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="9cdd6-503">Um de `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-503">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="9cdd6-504">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="9cdd6-504">array of objects</span></span>|<span data-ttu-id="9cdd6-505">10 itens</span><span class="sxs-lookup"><span data-stu-id="9cdd6-505">10 items</span></span>||<span data-ttu-id="9cdd6-506">As opções de escolha para `choiceset` o .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-506">The choice options for the`choiceset`.</span></span> <span data-ttu-id="9cdd6-507">Use somente quando `parameter.inputType` for `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-507">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="9cdd6-508">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-508">string</span></span>|<span data-ttu-id="9cdd6-509">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-509">128 characters</span></span>|<span data-ttu-id="9cdd6-510">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-510">✔</span></span>|<span data-ttu-id="9cdd6-511">Título da escolha.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-511">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="9cdd6-512">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-512">string</span></span>|<span data-ttu-id="9cdd6-513">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-513">512 characters</span></span>|<span data-ttu-id="9cdd6-514">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-514">✔</span></span>|<span data-ttu-id="9cdd6-515">O valor da escolha.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-515">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="9cdd6-516">permissões</span><span class="sxs-lookup"><span data-stu-id="9cdd6-516">permissions</span></span>

<span data-ttu-id="9cdd6-517">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-517">**Optional** — array of strings</span></span>

<span data-ttu-id="9cdd6-518">Uma matriz da qual especifica quais permissões o aplicativo solicita, o que permite que os usuários finais `string` saibam como a extensão se executa.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-518">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension performs.</span></span> <span data-ttu-id="9cdd6-519">As seguintes opções não são exclusivas:</span><span class="sxs-lookup"><span data-stu-id="9cdd6-519">The following options are non-exclusive:</span></span>

* <span data-ttu-id="9cdd6-520">`identity`&emsp;Requer informações de identidade do usuário</span><span class="sxs-lookup"><span data-stu-id="9cdd6-520">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="9cdd6-521">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe</span><span class="sxs-lookup"><span data-stu-id="9cdd6-521">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="9cdd6-522">Alterar essas permissões durante a atualização do aplicativo faz com que os usuários repitam o processo de consentimento após executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-522">Changing these permissions during app update, causes your users to repeat the consent process after they run the updated app.</span></span> <span data-ttu-id="9cdd6-523">Consulte [Atualizando seu aplicativo para](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-523">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="9cdd6-524">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="9cdd6-524">devicePermissions</span></span>

<span data-ttu-id="9cdd6-525">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-525">**Optional** — array of strings</span></span>

<span data-ttu-id="9cdd6-526">Fornece os recursos nativos no dispositivo de um usuário ao que seu aplicativo solicita acesso.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-526">Provides the native features on a user's device that your app requests access to.</span></span> <span data-ttu-id="9cdd6-527">As opções são:</span><span class="sxs-lookup"><span data-stu-id="9cdd6-527">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="9cdd6-528">validDomains</span><span class="sxs-lookup"><span data-stu-id="9cdd6-528">validDomains</span></span>

<span data-ttu-id="9cdd6-529">**Opcional**, exceto **Obrigatório quando** notado</span><span class="sxs-lookup"><span data-stu-id="9cdd6-529">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="9cdd6-530">Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-530">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="9cdd6-531">Listagem de domínio pode incluir caracteres curinga, por exemplo, `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-531">Domain listings can include wildcards, for example, `*.example.com`.</span></span> <span data-ttu-id="9cdd6-532">Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-532">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="9cdd6-533">Se a configuração de tabulação ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de tabulação, esse domínio deve ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-533">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="9cdd6-534">Não é **necessário** incluir os domínios de provedores de identidade que você deseja dar suporte ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-534">It is **not** necessary to include the domains of identity providers you want to support in your app.</span></span> <span data-ttu-id="9cdd6-535">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para accounts.google.com, no entanto, você não deve incluir accounts.google.com em `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-535">For example, to authenticate using a Google ID, it is required to redirect to accounts.google.com, however, you must not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="9cdd6-536">Os aplicativos do Teams que exigem suas próprias URLs do sharepoint funcionam bem, inclui "{teamsitedomain}" em sua lista de domínios válida.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-536">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9cdd6-537">Não adicione domínios que estão fora do seu controle, diretamente ou por meio de caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-537">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="9cdd6-538">Por exemplo, `yourapp.onmicrosoft.com` é válido, no entanto, `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-538">For example, `yourapp.onmicrosoft.com` is valid, however, `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="9cdd6-539">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-539">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="9cdd6-540">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-540">webApplicationInfo</span></span>

<span data-ttu-id="9cdd6-541">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="9cdd6-541">**Optional** — object</span></span>

<span data-ttu-id="9cdd6-542">Forneça suas informações de ID de aplicativo do Azure Active Directory (AAD) e do Microsoft Graph para ajudar os usuários a entrar perfeitamente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-542">Provide your Azure Active Directory (AAD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="9cdd6-543">Se seu aplicativo estiver registrado no AAD, você deverá fornecer a ID do aplicativo, para que os administradores possam revisar facilmente as permissões e conceder consentimento no Centro de administração do Teams.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-543">If your app is registered in AAD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="9cdd6-544">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-544">Name</span></span>| <span data-ttu-id="9cdd6-545">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-545">Type</span></span>| <span data-ttu-id="9cdd6-546">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-546">Maximum size</span></span> | <span data-ttu-id="9cdd6-547">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-547">Required</span></span> | <span data-ttu-id="9cdd6-548">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-548">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="9cdd6-549">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-549">string</span></span>|<span data-ttu-id="9cdd6-550">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-550">36 characters</span></span>|<span data-ttu-id="9cdd6-551">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-551">✔</span></span>|<span data-ttu-id="9cdd6-552">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-552">AAD application id of the app.</span></span> <span data-ttu-id="9cdd6-553">Essa id deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-553">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="9cdd6-554">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-554">string</span></span>|<span data-ttu-id="9cdd6-555">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-555">2048 characters</span></span>|<span data-ttu-id="9cdd6-556">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-556">✔</span></span>|<span data-ttu-id="9cdd6-557">URL de recurso do aplicativo para adquirir token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-557">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="9cdd6-558">**OBSERVAÇÃO:** Se você não estiver usando o SSO, certifique-se de inserir um valor de cadeia de caracteres fictício neste campo para o manifesto do aplicativo, por exemplo, para evitar https://notapplicable uma resposta de erro.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-558">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="9cdd6-559">matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-559">array of strings</span></span>|<span data-ttu-id="9cdd6-560">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-560">128 characters</span></span>||<span data-ttu-id="9cdd6-561">Especifique o [consentimento específico do recurso granular](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="9cdd6-561">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="9cdd6-562">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="9cdd6-562">showLoadingIndicator</span></span>

<span data-ttu-id="9cdd6-563">**Opcional** — booleano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-563">**Optional** — boolean</span></span>

<span data-ttu-id="9cdd6-564">Indica se é ou não para mostrar o indicador de carregamento quando um aplicativo ou guia está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-564">Indicates whether or not to show the loading indicator when an app or tab is loading.</span></span> <span data-ttu-id="9cdd6-565">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-565">Default is **false**.</span></span>
>[!NOTE]
><span data-ttu-id="9cdd6-566">Se você selecionar como true no manifesto do aplicativo, para carregar a página corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa conforme descrito em Mostrar um documento indicador de carregamento `showLoadingIndicator` nativo. [](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)</span><span class="sxs-lookup"><span data-stu-id="9cdd6-566">If you select`showLoadingIndicator` as true in your app manifest, to load the page correctly, modify the content pages of your tabs and task modules as described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="9cdd6-567">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="9cdd6-567">isFullScreen</span></span>

 <span data-ttu-id="9cdd6-568">**Opcional** — booleano</span><span class="sxs-lookup"><span data-stu-id="9cdd6-568">**Optional** — boolean</span></span>

<span data-ttu-id="9cdd6-569">Indica onde um aplicativo pessoal é renderizado com ou sem uma barra de header de tabulação.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-569">Indicate where a personal app is rendered with or without a tab header bar.</span></span> <span data-ttu-id="9cdd6-570">O padrão é **false**.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-570">Default is **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="9cdd6-571">activities</span><span class="sxs-lookup"><span data-stu-id="9cdd6-571">activities</span></span>

<span data-ttu-id="9cdd6-572">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="9cdd6-572">**Optional** — object</span></span>

<span data-ttu-id="9cdd6-573">Defina as propriedades que seu aplicativo usa para postar um feed de atividade do usuário.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-573">Define the properties your app uses to post a user activity feed.</span></span>

|<span data-ttu-id="9cdd6-574">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-574">Name</span></span>| <span data-ttu-id="9cdd6-575">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-575">Type</span></span>| <span data-ttu-id="9cdd6-576">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-576">Maximum size</span></span> | <span data-ttu-id="9cdd6-577">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-577">Required</span></span> | <span data-ttu-id="9cdd6-578">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-578">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="9cdd6-579">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="9cdd6-579">array of Objects</span></span>|<span data-ttu-id="9cdd6-580">128 itens</span><span class="sxs-lookup"><span data-stu-id="9cdd6-580">128 items</span></span>| | <span data-ttu-id="9cdd6-581">Forneça os tipos de atividades que seu aplicativo pode postar em um feed de atividades dos usuários.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-581">Provide the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="9cdd6-582">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="9cdd6-582">activities.activityTypes</span></span>

|<span data-ttu-id="9cdd6-583">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-583">Name</span></span>| <span data-ttu-id="9cdd6-584">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-584">Type</span></span>| <span data-ttu-id="9cdd6-585">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-585">Maximum size</span></span> | <span data-ttu-id="9cdd6-586">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-586">Required</span></span> | <span data-ttu-id="9cdd6-587">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-587">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="9cdd6-588">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-588">string</span></span>|<span data-ttu-id="9cdd6-589">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-589">32 characters</span></span>|<span data-ttu-id="9cdd6-590">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-590">✔</span></span>|<span data-ttu-id="9cdd6-591">O tipo de notificação.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-591">The notification type.</span></span> <span data-ttu-id="9cdd6-592">*Consulte abaixo*.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-592">*See below*.</span></span>|
|`description`|<span data-ttu-id="9cdd6-593">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-593">string</span></span>|<span data-ttu-id="9cdd6-594">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-594">128 characters</span></span>|<span data-ttu-id="9cdd6-595">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-595">✔</span></span>|<span data-ttu-id="9cdd6-596">Uma breve descrição da notificação.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-596">A brief description of the notification.</span></span> <span data-ttu-id="9cdd6-597">*Consulte abaixo*.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-597">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="9cdd6-598">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-598">string</span></span>|<span data-ttu-id="9cdd6-599">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-599">128 characters</span></span>|<span data-ttu-id="9cdd6-600">✔</span><span class="sxs-lookup"><span data-stu-id="9cdd6-600">✔</span></span>|<span data-ttu-id="9cdd6-601">Ex: "{actor} criado tarefa {taskId} para você"</span><span class="sxs-lookup"><span data-stu-id="9cdd6-601">Ex: "{actor} created task {taskId} for you"</span></span>|

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

## <a name="defaultinstallscope"></a><span data-ttu-id="9cdd6-602">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="9cdd6-602">defaultInstallScope</span></span>

<span data-ttu-id="9cdd6-603">**Opcional** - cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-603">**Optional** - string</span></span>

<span data-ttu-id="9cdd6-604">Especifica o escopo de instalação definido para este aplicativo por padrão.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-604">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="9cdd6-605">O escopo definido será a opção exibida no botão quando um usuário tentar adicionar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-605">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="9cdd6-606">As opções são:</span><span class="sxs-lookup"><span data-stu-id="9cdd6-606">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="9cdd6-607">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="9cdd6-607">defaultGroupCapability</span></span>

<span data-ttu-id="9cdd6-608">**Opcional** - objeto</span><span class="sxs-lookup"><span data-stu-id="9cdd6-608">**Optional** - object</span></span>

<span data-ttu-id="9cdd6-609">Quando um escopo de instalação de grupo é selecionado, ele define o recurso padrão quando o usuário instala o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-609">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="9cdd6-610">As opções são:</span><span class="sxs-lookup"><span data-stu-id="9cdd6-610">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="9cdd6-611">Name</span><span class="sxs-lookup"><span data-stu-id="9cdd6-611">Name</span></span>| <span data-ttu-id="9cdd6-612">Tipo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-612">Type</span></span>| <span data-ttu-id="9cdd6-613">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="9cdd6-613">Maximum size</span></span> | <span data-ttu-id="9cdd6-614">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9cdd6-614">Required</span></span> | <span data-ttu-id="9cdd6-615">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdd6-615">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="9cdd6-616">string</span><span class="sxs-lookup"><span data-stu-id="9cdd6-616">string</span></span>|||<span data-ttu-id="9cdd6-617">Quando o escopo de instalação selecionado for `team` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-617">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="9cdd6-618">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-618">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="9cdd6-619">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-619">string</span></span>|||<span data-ttu-id="9cdd6-620">Quando o escopo de instalação selecionado for `groupchat` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-620">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="9cdd6-621">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-621">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="9cdd6-622">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9cdd6-622">string</span></span>|||<span data-ttu-id="9cdd6-623">Quando o escopo de instalação selecionado for `meetings` , este campo especifica o recurso padrão disponível.</span><span class="sxs-lookup"><span data-stu-id="9cdd6-623">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="9cdd6-624">Opções: `tab` `bot` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="9cdd6-624">Options: `tab`, `bot`, or `connector`.</span></span>|


