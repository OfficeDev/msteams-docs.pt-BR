---
title: Referência de esquema de manifesto
description: Descreve o esquema de manifesto para o Microsoft Teams
keywords: esquema de manifesto do teams
author: laujan
ms.author: lajanuar
ms.openlocfilehash: 26c6ca0ed6edceb9b34c84c28a43a63f65a348de
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552553"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="11854-104">Referência: esquema de manifesto para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11854-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="11854-105">O manifesto do Microsoft Teams descreve como o aplicativo integra-se ao produto Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="11854-105">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="11854-106">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="11854-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="11854-107">As versões anteriores 1.0-1.4 também são suportadas (usando "v1. x" na URL).</span><span class="sxs-lookup"><span data-stu-id="11854-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="11854-108">O seguinte exemplo de esquema mostra todas as opções de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="11854-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="11854-109">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="11854-109">Sample full manifest</span></span>

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

<span data-ttu-id="11854-110">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="11854-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="11854-111">$schema</span><span class="sxs-lookup"><span data-stu-id="11854-111">$schema</span></span>

<span data-ttu-id="11854-112">*Opcional, mas recomendado* — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-112">*Optional, but recommended* — string</span></span>

<span data-ttu-id="11854-113">A URL https://que faz referência ao esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="11854-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="11854-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="11854-114">manifestVersion</span></span>

<span data-ttu-id="11854-115">**Obrigatório** — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-115">**Required** — string</span></span>

<span data-ttu-id="11854-116">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="11854-116">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="11854-117">Ele deve ser "1,7".</span><span class="sxs-lookup"><span data-stu-id="11854-117">It should be "1.7".</span></span>

## <a name="version"></a><span data-ttu-id="11854-118">versão</span><span class="sxs-lookup"><span data-stu-id="11854-118">version</span></span>

<span data-ttu-id="11854-119">**Obrigatório** — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-119">**Required** — string</span></span>

<span data-ttu-id="11854-120">A versão do aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="11854-120">The version of the specific app.</span></span> <span data-ttu-id="11854-121">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="11854-121">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="11854-122">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="11854-122">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="11854-123">Se este aplicativo foi enviado para o repositório, o novo manifesto terá que ser reenviado e validado novamente.</span><span class="sxs-lookup"><span data-stu-id="11854-123">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="11854-124">Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, após serem aprovados.</span><span class="sxs-lookup"><span data-stu-id="11854-124">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="11854-125">Se as permissões solicitadas pelo aplicativo forem alteradas, os usuários serão solicitados a atualizar e a dar o consentimento novamente para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-125">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="11854-126">Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (principal. Mínima. PATCH).</span><span class="sxs-lookup"><span data-stu-id="11854-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="11854-127">id</span><span class="sxs-lookup"><span data-stu-id="11854-127">id</span></span>

<span data-ttu-id="11854-128">**Obrigatório** – ID do aplicativo da Microsoft</span><span class="sxs-lookup"><span data-stu-id="11854-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="11854-129">O identificador exclusivo gerado pela Microsoft para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-129">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="11854-130">Se você tiver registrado um bot por meio da Microsoft bot Framework, ou se o aplicativo Web da sua guia já estiver conectado com a Microsoft, você já deve ter um ID e deve inseri-lo aqui.</span><span class="sxs-lookup"><span data-stu-id="11854-130">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="11854-131">Caso contrário, você deve gerar uma nova ID no portal de registro de aplicativos da Microsoft ([meus aplicativos](https://apps.dev.microsoft.com)), inseri-la aqui e reutilizá-la quando você adicionar um bot. Observação: se você estiver enviando uma atualização para o seu aplicativo existente no AppSource, a ID em seu manifesto não deverá ser modificada.</span><span class="sxs-lookup"><span data-stu-id="11854-131">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you add a bot.Note: If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="11854-132">developer</span><span class="sxs-lookup"><span data-stu-id="11854-132">developer</span></span>

<span data-ttu-id="11854-133">**Obrigatório** — objeto</span><span class="sxs-lookup"><span data-stu-id="11854-133">**Required** — object</span></span>

<span data-ttu-id="11854-134">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="11854-134">Specifies information about your company.</span></span> <span data-ttu-id="11854-135">Para aplicativos enviados para o AppSource (anteriormente Office Store), esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="11854-135">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="11854-136">Veja nossas [diretrizes de publicação](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="11854-136">See our [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="11854-137">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-137">Name</span></span>| <span data-ttu-id="11854-138">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-138">Maximum size</span></span> | <span data-ttu-id="11854-139">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-139">Required</span></span> | <span data-ttu-id="11854-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-140">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="11854-141">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-141">32 characters</span></span>|<span data-ttu-id="11854-142">✔</span><span class="sxs-lookup"><span data-stu-id="11854-142">✔</span></span>|<span data-ttu-id="11854-143">O nome de exibição para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="11854-143">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="11854-144">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-144">2048 characters</span></span>|<span data-ttu-id="11854-145">✔</span><span class="sxs-lookup"><span data-stu-id="11854-145">✔</span></span>|<span data-ttu-id="11854-146">A URL do https://para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="11854-146">The https:// URL to the developer's website.</span></span> <span data-ttu-id="11854-147">Este link deve levar os usuários à sua página de aterrissagem específica da empresa ou do produto.</span><span class="sxs-lookup"><span data-stu-id="11854-147">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="11854-148">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-148">2048 characters</span></span>|<span data-ttu-id="11854-149">✔</span><span class="sxs-lookup"><span data-stu-id="11854-149">✔</span></span>|<span data-ttu-id="11854-150">A URL do https://para a política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="11854-150">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="11854-151">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-151">2048 characters</span></span>|<span data-ttu-id="11854-152">✔</span><span class="sxs-lookup"><span data-stu-id="11854-152">✔</span></span>|<span data-ttu-id="11854-153">A URL do https://para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="11854-153">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="11854-154">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-154">10 characters</span></span>| |<span data-ttu-id="11854-155">**Opcional** A ID de rede do parceiro da Microsoft que identifica a organização do parceiro que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-155">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="11854-156">nome</span><span class="sxs-lookup"><span data-stu-id="11854-156">name</span></span>

<span data-ttu-id="11854-157">**Obrigatório** — objeto</span><span class="sxs-lookup"><span data-stu-id="11854-157">**Required** — object</span></span>

<span data-ttu-id="11854-158">O nome da sua experiência de aplicativo, exibido aos usuários na experiência do teams.</span><span class="sxs-lookup"><span data-stu-id="11854-158">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="11854-159">Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="11854-159">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="11854-160">Os valores de `short` e `full` não devem ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="11854-160">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="11854-161">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-161">Name</span></span>| <span data-ttu-id="11854-162">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-162">Maximum size</span></span> | <span data-ttu-id="11854-163">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-163">Required</span></span> | <span data-ttu-id="11854-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-164">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="11854-165">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-165">30 characters</span></span>|<span data-ttu-id="11854-166">✔</span><span class="sxs-lookup"><span data-stu-id="11854-166">✔</span></span>|<span data-ttu-id="11854-167">O nome de exibição curto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-167">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="11854-168">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-168">100 characters</span></span>||<span data-ttu-id="11854-169">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="11854-169">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="11854-170">description</span><span class="sxs-lookup"><span data-stu-id="11854-170">description</span></span>

<span data-ttu-id="11854-171">**Obrigatório** — objeto</span><span class="sxs-lookup"><span data-stu-id="11854-171">**Required** — object</span></span>

<span data-ttu-id="11854-172">Descreve seu aplicativo para os usuários.</span><span class="sxs-lookup"><span data-stu-id="11854-172">Describes your app to users.</span></span> <span data-ttu-id="11854-173">Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="11854-173">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="11854-174">Certifique-se de que sua descrição descreve precisamente sua experiência e fornece informações para ajudar os clientes potenciais a entender o que a sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="11854-174">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="11854-175">Você também deve observar, na descrição completa, se for necessário usar uma conta externa.</span><span class="sxs-lookup"><span data-stu-id="11854-175">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="11854-176">Os valores de `short` e `full` não devem ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="11854-176">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="11854-177">Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir nenhum outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-177">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="11854-178">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-178">Name</span></span>| <span data-ttu-id="11854-179">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-179">Maximum size</span></span> | <span data-ttu-id="11854-180">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-180">Required</span></span> | <span data-ttu-id="11854-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-181">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="11854-182">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-182">80 characters</span></span>|<span data-ttu-id="11854-183">✔</span><span class="sxs-lookup"><span data-stu-id="11854-183">✔</span></span>|<span data-ttu-id="11854-184">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="11854-184">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="11854-185">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-185">4000 characters</span></span>|<span data-ttu-id="11854-186">✔</span><span class="sxs-lookup"><span data-stu-id="11854-186">✔</span></span>|<span data-ttu-id="11854-187">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-187">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="11854-188">Packagenamena</span><span class="sxs-lookup"><span data-stu-id="11854-188">packageName</span></span>

<span data-ttu-id="11854-189">**Opcional** — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-189">**Optional** — string</span></span>

<span data-ttu-id="11854-190">Um identificador exclusivo para esse aplicativo na notação de domínio reverso; por exemplo, com. example. MyApp.</span><span class="sxs-lookup"><span data-stu-id="11854-190">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="11854-191">Comprimento máximo: 64 caracteres.</span><span class="sxs-lookup"><span data-stu-id="11854-191">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="11854-192">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="11854-192">localizationInfo</span></span>

<span data-ttu-id="11854-193">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="11854-193">**Optional** — object</span></span>

<span data-ttu-id="11854-194">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="11854-194">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="11854-195">Confira [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="11854-195">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="11854-196">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-196">Name</span></span>| <span data-ttu-id="11854-197">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-197">Maximum size</span></span> | <span data-ttu-id="11854-198">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-198">Required</span></span> | <span data-ttu-id="11854-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-199">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="11854-200">✔</span><span class="sxs-lookup"><span data-stu-id="11854-200">✔</span></span>|<span data-ttu-id="11854-201">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="11854-201">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="11854-202">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="11854-202">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="11854-203">Uma matriz de objetos especificando traduções de idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="11854-203">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="11854-204">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-204">Name</span></span>| <span data-ttu-id="11854-205">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-205">Maximum size</span></span> | <span data-ttu-id="11854-206">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-206">Required</span></span> | <span data-ttu-id="11854-207">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-207">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="11854-208">✔</span><span class="sxs-lookup"><span data-stu-id="11854-208">✔</span></span>|<span data-ttu-id="11854-209">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="11854-209">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="11854-210">✔</span><span class="sxs-lookup"><span data-stu-id="11854-210">✔</span></span>|<span data-ttu-id="11854-211">Um caminho de arquivo relativo para um arquivo. JSON que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="11854-211">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="11854-212">ícones</span><span class="sxs-lookup"><span data-stu-id="11854-212">icons</span></span>

<span data-ttu-id="11854-213">**Obrigatório** — objeto</span><span class="sxs-lookup"><span data-stu-id="11854-213">**Required** — object</span></span>

<span data-ttu-id="11854-214">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="11854-214">Icons used within the Teams app.</span></span> <span data-ttu-id="11854-215">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="11854-215">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="11854-216">Consulte [ícones](~/concepts/build-and-test/apps-package.md#icons) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="11854-216">See [Icons](~/concepts/build-and-test/apps-package.md#icons) for more information.</span></span>

|<span data-ttu-id="11854-217">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-217">Name</span></span>| <span data-ttu-id="11854-218">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-218">Maximum size</span></span> | <span data-ttu-id="11854-219">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-219">Required</span></span> | <span data-ttu-id="11854-220">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-220">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="11854-221">32 x 32 pixels</span><span class="sxs-lookup"><span data-stu-id="11854-221">32 x 32 pixels</span></span>|<span data-ttu-id="11854-222">✔</span><span class="sxs-lookup"><span data-stu-id="11854-222">✔</span></span>|<span data-ttu-id="11854-223">Um caminho de arquivo relativo para um ícone de estrutura de tópicos de PNG de 32 x 32 transparente.</span><span class="sxs-lookup"><span data-stu-id="11854-223">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="11854-224">192 x 192 pixels</span><span class="sxs-lookup"><span data-stu-id="11854-224">192 x 192 pixels</span></span>|<span data-ttu-id="11854-225">✔</span><span class="sxs-lookup"><span data-stu-id="11854-225">✔</span></span>|<span data-ttu-id="11854-226">Um caminho de arquivo relativo para um ícone de 192x192 do PNG completo.</span><span class="sxs-lookup"><span data-stu-id="11854-226">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="11854-227">accentColor</span><span class="sxs-lookup"><span data-stu-id="11854-227">accentColor</span></span>

<span data-ttu-id="11854-228">**Opcional** – código de cor hex HTML</span><span class="sxs-lookup"><span data-stu-id="11854-228">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="11854-229">Uma cor a ser usada em conjunto com e como um plano de fundo para seus ícones de estrutura de tópicos.</span><span class="sxs-lookup"><span data-stu-id="11854-229">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="11854-230">O valor deve ser um código de cor HTML válido começando com ' # ', por exemplo `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="11854-230">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="11854-231">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="11854-231">configurableTabs</span></span>

<span data-ttu-id="11854-232">**Opcional** — array</span><span class="sxs-lookup"><span data-stu-id="11854-232">**Optional** — array</span></span>

<span data-ttu-id="11854-233">Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração adicional antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="11854-233">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="11854-234">Guias configuráveis têm suporte apenas no escopo Teams (não pessoal), e atualmente só há suporte para **uma** guia por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-234">Configurable tabs are supported only in the teams scope (not personal), and currently only **one** tab per app is supported.</span></span>

|<span data-ttu-id="11854-235">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-235">Name</span></span>| <span data-ttu-id="11854-236">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-236">Type</span></span>| <span data-ttu-id="11854-237">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-237">Maximum size</span></span> | <span data-ttu-id="11854-238">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-238">Required</span></span> | <span data-ttu-id="11854-239">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-239">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="11854-240">string</span><span class="sxs-lookup"><span data-stu-id="11854-240">string</span></span>|<span data-ttu-id="11854-241">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-241">2048 characters</span></span>|<span data-ttu-id="11854-242">✔</span><span class="sxs-lookup"><span data-stu-id="11854-242">✔</span></span>|<span data-ttu-id="11854-243">A URL do https://a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="11854-243">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="11854-244">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="11854-244">array of enums</span></span>|<span data-ttu-id="11854-245">1</span><span class="sxs-lookup"><span data-stu-id="11854-245">1</span></span>|<span data-ttu-id="11854-246">✔</span><span class="sxs-lookup"><span data-stu-id="11854-246">✔</span></span>|<span data-ttu-id="11854-247">No momento, as guias configuráveis só dão suporte a `team` e os `groupchat` escopos.</span><span class="sxs-lookup"><span data-stu-id="11854-247">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="11854-248">booliano</span><span class="sxs-lookup"><span data-stu-id="11854-248">boolean</span></span>|||<span data-ttu-id="11854-249">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="11854-249">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="11854-250">Padrão: **true**.</span><span class="sxs-lookup"><span data-stu-id="11854-250">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="11854-251">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="11854-251">array of enums</span></span>|<span data-ttu-id="11854-252">6 </span><span class="sxs-lookup"><span data-stu-id="11854-252">6</span></span>||<span data-ttu-id="11854-253">O conjunto de `contextItem` escopos onde há suporte para uma tabulação.</span><span class="sxs-lookup"><span data-stu-id="11854-253">The set of `contextItem` scopes where a tab is supported.</span></span> <span data-ttu-id="11854-254">Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="11854-254">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="11854-255">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-255">string</span></span>|<span data-ttu-id="11854-256">2048</span><span class="sxs-lookup"><span data-stu-id="11854-256">2048</span></span>||<span data-ttu-id="11854-257">Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="11854-257">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="11854-258">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="11854-258">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="11854-259">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="11854-259">array of enums</span></span>|<span data-ttu-id="11854-260">1</span><span class="sxs-lookup"><span data-stu-id="11854-260">1</span></span>||<span data-ttu-id="11854-261">Define como sua guia será disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="11854-261">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="11854-262">Opções são `sharePointFullPage` e `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="11854-262">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="11854-263">staticTabs</span><span class="sxs-lookup"><span data-stu-id="11854-263">staticTabs</span></span>

<span data-ttu-id="11854-264">**Opcional** — array</span><span class="sxs-lookup"><span data-stu-id="11854-264">**Optional** — array</span></span>

<span data-ttu-id="11854-265">Define um conjunto de guias que podem ser "fixadas" por padrão, sem o usuário adicioná-las manualmente.</span><span class="sxs-lookup"><span data-stu-id="11854-265">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="11854-266">As guias estáticas declaradas no `personal` escopo são sempre fixadas para a experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-266">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="11854-267">Guias static declaradas no `team` escopo não são suportadas atualmente.</span><span class="sxs-lookup"><span data-stu-id="11854-267">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="11854-268">Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="11854-268">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="11854-269">Esse bloco é necessário somente para soluções que oferecem uma solução de guia estática.</span><span class="sxs-lookup"><span data-stu-id="11854-269">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="11854-270">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-270">Name</span></span>| <span data-ttu-id="11854-271">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-271">Type</span></span>| <span data-ttu-id="11854-272">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-272">Maximum size</span></span> | <span data-ttu-id="11854-273">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-273">Required</span></span> | <span data-ttu-id="11854-274">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-274">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="11854-275">string</span><span class="sxs-lookup"><span data-stu-id="11854-275">string</span></span>|<span data-ttu-id="11854-276">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-276">64 characters</span></span>|<span data-ttu-id="11854-277">✔</span><span class="sxs-lookup"><span data-stu-id="11854-277">✔</span></span>|<span data-ttu-id="11854-278">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="11854-278">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="11854-279">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-279">string</span></span>|<span data-ttu-id="11854-280">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-280">128 characters</span></span>|<span data-ttu-id="11854-281">✔</span><span class="sxs-lookup"><span data-stu-id="11854-281">✔</span></span>|<span data-ttu-id="11854-282">O nome de exibição da guia na interface de canal.</span><span class="sxs-lookup"><span data-stu-id="11854-282">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="11854-283">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-283">string</span></span>||<span data-ttu-id="11854-284">✔</span><span class="sxs-lookup"><span data-stu-id="11854-284">✔</span></span>|<span data-ttu-id="11854-285">A URL https://que aponta para a interface do usuário da entidade a ser exibida na tela do teams.</span><span class="sxs-lookup"><span data-stu-id="11854-285">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="11854-286">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-286">string</span></span>|||<span data-ttu-id="11854-287">A URL do https://para apontar para o modo de exibição de um usuário em um navegador.</span><span class="sxs-lookup"><span data-stu-id="11854-287">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="11854-288">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-288">string</span></span>|||<span data-ttu-id="11854-289">A URL do https://para apontar para as consultas de pesquisa de um usuário.</span><span class="sxs-lookup"><span data-stu-id="11854-289">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="11854-290">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="11854-290">array of enums</span></span>|<span data-ttu-id="11854-291">1</span><span class="sxs-lookup"><span data-stu-id="11854-291">1</span></span>|<span data-ttu-id="11854-292">✔</span><span class="sxs-lookup"><span data-stu-id="11854-292">✔</span></span>|<span data-ttu-id="11854-293">Atualmente, as guias estáticas oferecem suporte somente ao `personal` escopo, o que significa que ela pode ser provisionada somente como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="11854-293">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="11854-294">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="11854-294">array of enums</span></span>| <span data-ttu-id="11854-295">duas</span><span class="sxs-lookup"><span data-stu-id="11854-295">2</span></span>|| <span data-ttu-id="11854-296">O conjunto de `contextItem` escopos onde há suporte para uma tabulação.</span><span class="sxs-lookup"><span data-stu-id="11854-296">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
> <span data-ttu-id="11854-297">Se suas guias exigirem informações dependentes de contexto para exibir conteúdo relevante ou para iniciar um fluxo de autenticação, *consulte* [obter contexto para a guia do Microsoft Teams](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="11854-297">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="11854-298">robôs</span><span class="sxs-lookup"><span data-stu-id="11854-298">bots</span></span>

<span data-ttu-id="11854-299">**Opcional** — array</span><span class="sxs-lookup"><span data-stu-id="11854-299">**Optional** — array</span></span>

<span data-ttu-id="11854-300">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="11854-300">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="11854-301">O item é uma matriz (máximo de apenas 1 elemento &mdash; atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="11854-301">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="11854-302">Esse bloco é necessário somente para soluções que oferecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="11854-302">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="11854-303">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-303">Name</span></span>| <span data-ttu-id="11854-304">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-304">Type</span></span>| <span data-ttu-id="11854-305">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-305">Maximum size</span></span> | <span data-ttu-id="11854-306">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-306">Required</span></span> | <span data-ttu-id="11854-307">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-307">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="11854-308">string</span><span class="sxs-lookup"><span data-stu-id="11854-308">string</span></span>|<span data-ttu-id="11854-309">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-309">64 characters</span></span>|<span data-ttu-id="11854-310">✔</span><span class="sxs-lookup"><span data-stu-id="11854-310">✔</span></span>|<span data-ttu-id="11854-311">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="11854-311">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="11854-312">Isso pode ser o mesmo que a ID de [aplicativo](#id)geral.</span><span class="sxs-lookup"><span data-stu-id="11854-312">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="11854-313">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="11854-313">array of enums</span></span>|<span data-ttu-id="11854-314">3D</span><span class="sxs-lookup"><span data-stu-id="11854-314">3</span></span>|<span data-ttu-id="11854-315">✔</span><span class="sxs-lookup"><span data-stu-id="11854-315">✔</span></span>|<span data-ttu-id="11854-316">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="11854-316">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="11854-317">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="11854-317">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="11854-318">booliano</span><span class="sxs-lookup"><span data-stu-id="11854-318">boolean</span></span>|||<span data-ttu-id="11854-319">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="11854-319">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="11854-320">Será **`false`**</span><span class="sxs-lookup"><span data-stu-id="11854-320">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="11854-321">booliano</span><span class="sxs-lookup"><span data-stu-id="11854-321">boolean</span></span>|||<span data-ttu-id="11854-322">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="11854-322">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="11854-323">Será `**false**`</span><span class="sxs-lookup"><span data-stu-id="11854-323">Default: `**false**`</span></span>|
|`supportsFiles`|<span data-ttu-id="11854-324">booliano</span><span class="sxs-lookup"><span data-stu-id="11854-324">boolean</span></span>|||<span data-ttu-id="11854-325">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="11854-325">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="11854-326">Será **`false`**</span><span class="sxs-lookup"><span data-stu-id="11854-326">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="11854-327">booliano</span><span class="sxs-lookup"><span data-stu-id="11854-327">boolean</span></span>|||<span data-ttu-id="11854-328">Um valor que indica onde um bot dá suporte à chamada de áudio.</span><span class="sxs-lookup"><span data-stu-id="11854-328">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="11854-329">**Importante**: esta propriedade é experimental no momento.</span><span class="sxs-lookup"><span data-stu-id="11854-329">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="11854-330">As propriedades experimental podem não ser concluídas e podem sofrer alterações antes de ficarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="11854-330">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="11854-331">Ele é fornecido apenas para fins de teste e exploração, e não deve ser usado em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="11854-331">It is provided for testing and exploration purposes only and should not be used in production applications.</span></span> <span data-ttu-id="11854-332">Será **`false`**</span><span class="sxs-lookup"><span data-stu-id="11854-332">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="11854-333">booliano</span><span class="sxs-lookup"><span data-stu-id="11854-333">boolean</span></span>|||<span data-ttu-id="11854-334">Um valor que indica onde um bot dá suporte à chamada de vídeo.</span><span class="sxs-lookup"><span data-stu-id="11854-334">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="11854-335">**Importante**: esta propriedade é experimental no momento.</span><span class="sxs-lookup"><span data-stu-id="11854-335">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="11854-336">As propriedades experimental podem não ser concluídas e podem sofrer alterações antes de ficarem totalmente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="11854-336">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="11854-337">Ele é fornecido apenas para fins de teste e exploração, e não deve ser usado em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="11854-337">It is provided for testing and exploration purposes only and should not be used in production applications.</span></span> <span data-ttu-id="11854-338">Será **`false`**</span><span class="sxs-lookup"><span data-stu-id="11854-338">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="11854-339">bots. commandLists</span><span class="sxs-lookup"><span data-stu-id="11854-339">bots.commandLists</span></span>

<span data-ttu-id="11854-340">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="11854-340">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="11854-341">O objeto é uma matriz (máximo de dois elementos) com todos os elementos do tipo `object` ; você deve definir uma lista de comandos separada para cada escopo que seu bot suporta.</span><span class="sxs-lookup"><span data-stu-id="11854-341">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="11854-342">Consulte [menus de bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="11854-342">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="11854-343">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-343">Name</span></span>| <span data-ttu-id="11854-344">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-344">Type</span></span>| <span data-ttu-id="11854-345">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-345">Maximum size</span></span> | <span data-ttu-id="11854-346">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-346">Required</span></span> | <span data-ttu-id="11854-347">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-347">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="11854-348">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="11854-348">array of enums</span></span>|<span data-ttu-id="11854-349">3D</span><span class="sxs-lookup"><span data-stu-id="11854-349">3</span></span>|<span data-ttu-id="11854-350">✔</span><span class="sxs-lookup"><span data-stu-id="11854-350">✔</span></span>|<span data-ttu-id="11854-351">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="11854-351">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="11854-352">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="11854-352">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="11854-353">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="11854-353">array of objects</span></span>|<span data-ttu-id="11854-354">10 </span><span class="sxs-lookup"><span data-stu-id="11854-354">10</span></span>|<span data-ttu-id="11854-355">✔</span><span class="sxs-lookup"><span data-stu-id="11854-355">✔</span></span>|<span data-ttu-id="11854-356">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="11854-356">An array of commands the bot supports:</span></span><br><span data-ttu-id="11854-357">`title`: o nome do comando bot (cadeia, 32)</span><span class="sxs-lookup"><span data-stu-id="11854-357">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="11854-358">`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)</span><span class="sxs-lookup"><span data-stu-id="11854-358">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="11854-359">bots. commandLists. Commands</span><span class="sxs-lookup"><span data-stu-id="11854-359">bots.commandLists.commands</span></span>

|<span data-ttu-id="11854-360">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-360">Name</span></span>| <span data-ttu-id="11854-361">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-361">Type</span></span>| <span data-ttu-id="11854-362">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-362">Maximum size</span></span> | <span data-ttu-id="11854-363">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-363">Required</span></span> | <span data-ttu-id="11854-364">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-364">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="11854-365">title</span><span class="sxs-lookup"><span data-stu-id="11854-365">title</span></span>|<span data-ttu-id="11854-366">string</span><span class="sxs-lookup"><span data-stu-id="11854-366">string</span></span>|<span data-ttu-id="11854-367">12 </span><span class="sxs-lookup"><span data-stu-id="11854-367">12</span></span>|<span data-ttu-id="11854-368">✔</span><span class="sxs-lookup"><span data-stu-id="11854-368">✔</span></span>|<span data-ttu-id="11854-369">O nome do comando do bot</span><span class="sxs-lookup"><span data-stu-id="11854-369">The bot command name</span></span>|
|<span data-ttu-id="11854-370">description</span><span class="sxs-lookup"><span data-stu-id="11854-370">description</span></span>|<span data-ttu-id="11854-371">string</span><span class="sxs-lookup"><span data-stu-id="11854-371">string</span></span>|<span data-ttu-id="11854-372">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-372">128 characters</span></span>|<span data-ttu-id="11854-373">✔</span><span class="sxs-lookup"><span data-stu-id="11854-373">✔</span></span>|<span data-ttu-id="11854-374">Uma descrição de texto simples ou um exemplo da sintaxe de comando e seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="11854-374">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="11854-375">conectores</span><span class="sxs-lookup"><span data-stu-id="11854-375">connectors</span></span>

<span data-ttu-id="11854-376">**Opcional** — array</span><span class="sxs-lookup"><span data-stu-id="11854-376">**Optional** — array</span></span>

<span data-ttu-id="11854-377">O `connectors` bloco define um conector do Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-377">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="11854-378">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="11854-378">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="11854-379">Esse bloco é necessário somente para soluções que fornecem um conector.</span><span class="sxs-lookup"><span data-stu-id="11854-379">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="11854-380">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-380">Name</span></span>| <span data-ttu-id="11854-381">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-381">Type</span></span>| <span data-ttu-id="11854-382">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-382">Maximum size</span></span> | <span data-ttu-id="11854-383">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-383">Required</span></span> | <span data-ttu-id="11854-384">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-384">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="11854-385">string</span><span class="sxs-lookup"><span data-stu-id="11854-385">string</span></span>|<span data-ttu-id="11854-386">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-386">2048 characters</span></span>|<span data-ttu-id="11854-387">✔</span><span class="sxs-lookup"><span data-stu-id="11854-387">✔</span></span>|<span data-ttu-id="11854-388">A URL do https://a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="11854-388">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="11854-389">matriz de enums</span><span class="sxs-lookup"><span data-stu-id="11854-389">array of enums</span></span>|<span data-ttu-id="11854-390">1</span><span class="sxs-lookup"><span data-stu-id="11854-390">1</span></span>|<span data-ttu-id="11854-391">✔</span><span class="sxs-lookup"><span data-stu-id="11854-391">✔</span></span>|<span data-ttu-id="11854-392">Especifica se o conector oferece uma experiência no contexto de um canal em uma `team` ou uma experiência com escopo para um usuário individual ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="11854-392">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="11854-393">Atualmente, só `team` há suporte para o escopo.</span><span class="sxs-lookup"><span data-stu-id="11854-393">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="11854-394">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-394">string</span></span>|<span data-ttu-id="11854-395">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-395">64 characters</span></span>|<span data-ttu-id="11854-396">✔</span><span class="sxs-lookup"><span data-stu-id="11854-396">✔</span></span>|<span data-ttu-id="11854-397">Um identificador exclusivo para o conector que corresponde à sua ID no [painel do desenvolvedor de conectores](https://aka.ms/connectorsdashboard).</span><span class="sxs-lookup"><span data-stu-id="11854-397">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="11854-398">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="11854-398">composeExtensions</span></span>

<span data-ttu-id="11854-399">**Opcional** — array</span><span class="sxs-lookup"><span data-stu-id="11854-399">**Optional** — array</span></span>

<span data-ttu-id="11854-400">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-400">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="11854-401">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem a funcionar.</span><span class="sxs-lookup"><span data-stu-id="11854-401">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="11854-402">O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="11854-402">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="11854-403">Esse bloco é necessário somente para soluções que forneçam uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="11854-403">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="11854-404">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-404">Name</span></span>| <span data-ttu-id="11854-405">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-405">Type</span></span> | <span data-ttu-id="11854-406">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-406">Maximum Size</span></span> | <span data-ttu-id="11854-407">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-407">Required</span></span> | <span data-ttu-id="11854-408">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-408">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="11854-409">string</span><span class="sxs-lookup"><span data-stu-id="11854-409">string</span></span>|<span data-ttu-id="11854-410">64</span><span class="sxs-lookup"><span data-stu-id="11854-410">64</span></span>|<span data-ttu-id="11854-411">✔</span><span class="sxs-lookup"><span data-stu-id="11854-411">✔</span></span>|<span data-ttu-id="11854-412">A ID exclusiva do aplicativo da Microsoft para o bot que faz a extensão do sistema de mensagens, conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="11854-412">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="11854-413">Isso pode ser o mesmo que a ID de aplicativo geral.</span><span class="sxs-lookup"><span data-stu-id="11854-413">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="11854-414">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="11854-414">array of objects</span></span>|<span data-ttu-id="11854-415">10 </span><span class="sxs-lookup"><span data-stu-id="11854-415">10</span></span>|<span data-ttu-id="11854-416">✔</span><span class="sxs-lookup"><span data-stu-id="11854-416">✔</span></span>|<span data-ttu-id="11854-417">matriz de comandos que a extensão de mensagens oferece suporte</span><span class="sxs-lookup"><span data-stu-id="11854-417">array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="11854-418">booliano</span><span class="sxs-lookup"><span data-stu-id="11854-418">boolean</span></span>|||<span data-ttu-id="11854-419">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="11854-419">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="11854-420">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="11854-420">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="11854-421">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="11854-421">array of Objects</span></span>|<span data-ttu-id="11854-422">5 </span><span class="sxs-lookup"><span data-stu-id="11854-422">5</span></span>||<span data-ttu-id="11854-423">Uma lista de manipuladores que permitem que os aplicativos sejam chamados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="11854-423">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="11854-424">Os domínios também devem ser listados no `validDomains`</span><span class="sxs-lookup"><span data-stu-id="11854-424">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="11854-425">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-425">string</span></span>|||<span data-ttu-id="11854-426">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="11854-426">The type of message handler.</span></span> <span data-ttu-id="11854-427">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="11854-427">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="11854-428">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-428">array of Strings</span></span>|||<span data-ttu-id="11854-429">matriz de domínios para o qual o manipulador de mensagens de link pode se registrar.</span><span class="sxs-lookup"><span data-stu-id="11854-429">array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="11854-430">composeExtensions. Commands</span><span class="sxs-lookup"><span data-stu-id="11854-430">composeExtensions.commands</span></span>

<span data-ttu-id="11854-431">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="11854-431">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="11854-432">Cada comando aparece no Microsoft Teams como uma possível interação do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="11854-432">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="11854-433">Há um máximo de 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="11854-433">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="11854-434">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="11854-434">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="11854-435">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-435">Name</span></span>| <span data-ttu-id="11854-436">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-436">Type</span></span>| <span data-ttu-id="11854-437">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-437">Maximum size</span></span> | <span data-ttu-id="11854-438">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-438">Required</span></span> | <span data-ttu-id="11854-439">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-439">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="11854-440">string</span><span class="sxs-lookup"><span data-stu-id="11854-440">string</span></span>|<span data-ttu-id="11854-441">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-441">64 characters</span></span>|<span data-ttu-id="11854-442">✔</span><span class="sxs-lookup"><span data-stu-id="11854-442">✔</span></span>|<span data-ttu-id="11854-443">A ID do comando.</span><span class="sxs-lookup"><span data-stu-id="11854-443">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="11854-444">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-444">string</span></span>|<span data-ttu-id="11854-445">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-445">32 characters</span></span>|<span data-ttu-id="11854-446">✔</span><span class="sxs-lookup"><span data-stu-id="11854-446">✔</span></span>|<span data-ttu-id="11854-447">O nome do comando amigável.</span><span class="sxs-lookup"><span data-stu-id="11854-447">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="11854-448">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-448">string</span></span>|<span data-ttu-id="11854-449">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-449">64 characters</span></span>||<span data-ttu-id="11854-450">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="11854-450">Type of the command.</span></span> <span data-ttu-id="11854-451">Um `query` ou `action` .</span><span class="sxs-lookup"><span data-stu-id="11854-451">One of `query` or `action`.</span></span> <span data-ttu-id="11854-452">Padrão: **consulta**.</span><span class="sxs-lookup"><span data-stu-id="11854-452">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="11854-453">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-453">string</span></span>|<span data-ttu-id="11854-454">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-454">128 characters</span></span>||<span data-ttu-id="11854-455">A descrição que aparece para os usuários para indicar a finalidade desse comando.</span><span class="sxs-lookup"><span data-stu-id="11854-455">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="11854-456">booliano</span><span class="sxs-lookup"><span data-stu-id="11854-456">boolean</span></span>|||<span data-ttu-id="11854-457">Um valor Boolean que indica se o comando deve ser executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="11854-457">A boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="11854-458">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="11854-458">Default: **false**.</span></span>|
|`context`|<span data-ttu-id="11854-459">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-459">array of Strings</span></span>|<span data-ttu-id="11854-460">3D</span><span class="sxs-lookup"><span data-stu-id="11854-460">3</span></span>||<span data-ttu-id="11854-461">Define onde a extensão de mensagem pode ser chamada.</span><span class="sxs-lookup"><span data-stu-id="11854-461">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="11854-462">Qualquer combinação de `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="11854-462">Any combination of`compose`,`commandBox`,`message` .</span></span> <span data-ttu-id="11854-463">O padrão é `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="11854-463">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="11854-464">booliano</span><span class="sxs-lookup"><span data-stu-id="11854-464">boolean</span></span>|||<span data-ttu-id="11854-465">Um valor Boolean que indica se ele deve buscar o módulo de tarefa dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="11854-465">A boolean value that indicates if it should fetch the task module dynamically.</span></span> <span data-ttu-id="11854-466">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="11854-466">Default: **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="11854-467">objeto</span><span class="sxs-lookup"><span data-stu-id="11854-467">object</span></span>|||<span data-ttu-id="11854-468">Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="11854-468">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="11854-469">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-469">string</span></span>|<span data-ttu-id="11854-470">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-470">64 characters</span></span>||<span data-ttu-id="11854-471">Título inicial da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="11854-471">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="11854-472">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-472">string</span></span>|||<span data-ttu-id="11854-473">Largura da caixa de diálogo: um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '.</span><span class="sxs-lookup"><span data-stu-id="11854-473">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="11854-474">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-474">string</span></span>|||<span data-ttu-id="11854-475">Altura da caixa de diálogo-um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '.</span><span class="sxs-lookup"><span data-stu-id="11854-475">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="11854-476">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-476">string</span></span>|||<span data-ttu-id="11854-477">URL do WebView inicial.</span><span class="sxs-lookup"><span data-stu-id="11854-477">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="11854-478">matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="11854-478">array of object</span></span>|<span data-ttu-id="11854-479">5 itens</span><span class="sxs-lookup"><span data-stu-id="11854-479">5 items</span></span>|<span data-ttu-id="11854-480">✔</span><span class="sxs-lookup"><span data-stu-id="11854-480">✔</span></span>|<span data-ttu-id="11854-481">A lista de parâmetros que o comando utiliza.</span><span class="sxs-lookup"><span data-stu-id="11854-481">The list of parameters the command takes.</span></span> <span data-ttu-id="11854-482">Mínimo: 1; máximo: 5.</span><span class="sxs-lookup"><span data-stu-id="11854-482">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="11854-483">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-483">string</span></span>|<span data-ttu-id="11854-484">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-484">64 characters</span></span>|<span data-ttu-id="11854-485">✔</span><span class="sxs-lookup"><span data-stu-id="11854-485">✔</span></span>|<span data-ttu-id="11854-486">O nome do parâmetro conforme ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="11854-486">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="11854-487">Isso é incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="11854-487">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="11854-488">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-488">string</span></span>|<span data-ttu-id="11854-489">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-489">32 characters</span></span>|<span data-ttu-id="11854-490">✔</span><span class="sxs-lookup"><span data-stu-id="11854-490">✔</span></span>|<span data-ttu-id="11854-491">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="11854-491">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="11854-492">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-492">string</span></span>|<span data-ttu-id="11854-493">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-493">128 characters</span></span>||<span data-ttu-id="11854-494">Cadeia de caracteres amigável que descreve a finalidade deste parâmetro.</span><span class="sxs-lookup"><span data-stu-id="11854-494">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="11854-495">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-495">string</span></span>|<span data-ttu-id="11854-496">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-496">512 characters</span></span>||<span data-ttu-id="11854-497">Valor inicial para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="11854-497">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="11854-498">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-498">string</span></span>|<span data-ttu-id="11854-499">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-499">128 characters</span></span>||<span data-ttu-id="11854-500">Define o tipo de controle exibido em um módulo de tarefas para o `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="11854-500">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="11854-501">Um de `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="11854-501">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="11854-502">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="11854-502">array of objects</span></span>|<span data-ttu-id="11854-503">10 itens</span><span class="sxs-lookup"><span data-stu-id="11854-503">10 items</span></span>||<span data-ttu-id="11854-504">As opções de escolha para o `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="11854-504">The choice options for the`choiceset`.</span></span> <span data-ttu-id="11854-505">Use somente quando o `parameter.inputType` é `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="11854-505">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="11854-506">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-506">string</span></span>|<span data-ttu-id="11854-507">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-507">128 characters</span></span>|<span data-ttu-id="11854-508">✔</span><span class="sxs-lookup"><span data-stu-id="11854-508">✔</span></span>|<span data-ttu-id="11854-509">Título da escolha.</span><span class="sxs-lookup"><span data-stu-id="11854-509">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="11854-510">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-510">string</span></span>|<span data-ttu-id="11854-511">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-511">512 characters</span></span>|<span data-ttu-id="11854-512">✔</span><span class="sxs-lookup"><span data-stu-id="11854-512">✔</span></span>|<span data-ttu-id="11854-513">O valor da escolha.</span><span class="sxs-lookup"><span data-stu-id="11854-513">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="11854-514">permissões</span><span class="sxs-lookup"><span data-stu-id="11854-514">permissions</span></span>

<span data-ttu-id="11854-515">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-515">**Optional** — array of strings</span></span>

<span data-ttu-id="11854-516">Uma matriz `string` que especifica quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão será executada.</span><span class="sxs-lookup"><span data-stu-id="11854-516">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="11854-517">As opções a seguir são não exclusivas:</span><span class="sxs-lookup"><span data-stu-id="11854-517">The following options are non-exclusive:</span></span>

* <span data-ttu-id="11854-518">`identity`&emsp;Requer informações de identidade do usuário</span><span class="sxs-lookup"><span data-stu-id="11854-518">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="11854-519">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas para membros da equipe</span><span class="sxs-lookup"><span data-stu-id="11854-519">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="11854-520">A alteração dessas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="11854-520">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span> <span data-ttu-id="11854-521">Veja [atualização do seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="11854-521">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="11854-522">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="11854-522">devicePermissions</span></span>

<span data-ttu-id="11854-523">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-523">**Optional** — array of strings</span></span>

<span data-ttu-id="11854-524">Especifica os recursos nativos no dispositivo de um usuário para o qual seu aplicativo pode solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="11854-524">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="11854-525">As opções são:</span><span class="sxs-lookup"><span data-stu-id="11854-525">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="11854-526">validDomains</span><span class="sxs-lookup"><span data-stu-id="11854-526">validDomains</span></span>

<span data-ttu-id="11854-527">**Opcional**, exceto quando **necessário** , onde observado</span><span class="sxs-lookup"><span data-stu-id="11854-527">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="11854-528">Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="11854-528">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="11854-529">As listagens de domínio podem incluir curingas, por exemplo `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="11854-529">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="11854-530">Isso corresponde exatamente a um segmento do domínio; Se você precisar coincidir `a.b.example.com` e usar `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="11854-530">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="11854-531">Se a configuração de sua guia ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além daquele usado para configuração de guia, esse domínio deverá ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="11854-531">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="11854-532">No entanto, **não** é necessário incluir os domínios de provedores de identidade que você deseja suportar no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-532">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="11854-533">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve incluir o accounts.google.com no `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="11854-533">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="11854-534">Aplicativos do teams que exigem suas próprias URLs do SharePoint para funcionar bem, podem incluir "{teamsitedomain}" em sua lista de domínios válida.</span><span class="sxs-lookup"><span data-stu-id="11854-534">Teams apps that require their own sharepoint URLs to function well, may include "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11854-535">Não adicione domínios que estejam fora do seu controle, seja diretamente ou via curingas.</span><span class="sxs-lookup"><span data-stu-id="11854-535">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="11854-536">Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="11854-536">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="11854-537">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="11854-537">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="11854-538">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="11854-538">webApplicationInfo</span></span>

<span data-ttu-id="11854-539">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="11854-539">**Optional** — object</span></span>

<span data-ttu-id="11854-540">Especifique a ID do aplicativo do Azure Active Directory (Azure AD) e as informações do Microsoft Graph para ajudar os usuários a entrarem diretamente no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-540">Specify your Azure Active Directory (Azure AD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="11854-541">Se seu aplicativo estiver registrado no Azure AD, você deve fornecer a ID do aplicativo, para que os administradores possam facilmente revisar permissões e conceder consentimento no centro de administração do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="11854-541">If your app is registered in Azure AD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="11854-542">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-542">Name</span></span>| <span data-ttu-id="11854-543">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-543">Type</span></span>| <span data-ttu-id="11854-544">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-544">Maximum size</span></span> | <span data-ttu-id="11854-545">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-545">Required</span></span> | <span data-ttu-id="11854-546">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-546">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="11854-547">string</span><span class="sxs-lookup"><span data-stu-id="11854-547">string</span></span>|<span data-ttu-id="11854-548">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-548">36 characters</span></span>|<span data-ttu-id="11854-549">✔</span><span class="sxs-lookup"><span data-stu-id="11854-549">✔</span></span>|<span data-ttu-id="11854-550">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11854-550">AAD application id of the app.</span></span> <span data-ttu-id="11854-551">Esta ID deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="11854-551">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="11854-552">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-552">string</span></span>|<span data-ttu-id="11854-553">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-553">2048 characters</span></span>|<span data-ttu-id="11854-554">✔</span><span class="sxs-lookup"><span data-stu-id="11854-554">✔</span></span>|<span data-ttu-id="11854-555">URL de recurso do aplicativo para aquisição de token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="11854-555">Resource url of app for acquiring auth token for SSO.</span></span>|
|`applicationPermissions`|<span data-ttu-id="11854-556">matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-556">array of strings</span></span>|<span data-ttu-id="11854-557">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-557">128 characters</span></span>||<span data-ttu-id="11854-558">Especificar [consentimento específico de recurso](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions) granular</span><span class="sxs-lookup"><span data-stu-id="11854-558">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="11854-559">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="11854-559">showLoadingIndicator</span></span>

<span data-ttu-id="11854-560">**Opcional** — Boolean</span><span class="sxs-lookup"><span data-stu-id="11854-560">**Optional** — boolean</span></span>

<span data-ttu-id="11854-561">Indica se o indicador de carregamento deve ou não ser mostrado quando um app/Tab é carregado.</span><span class="sxs-lookup"><span data-stu-id="11854-561">Indicate whether or not to show the loading indicator when an app/tab is loading.</span></span> <span data-ttu-id="11854-562">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="11854-562">Default: **false**.</span></span>
>[!NOTE]
><span data-ttu-id="11854-563">Se você definir "showLoadingIndicator: true" em seu manifesto de aplicativo, para que a página seja carregada corretamente, você deve modificar as páginas de conteúdo de suas guias e módulos de tarefa, de acordo com o protocolo descrito em [Mostrar um documento indicador de carregamento nativo](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) .</span><span class="sxs-lookup"><span data-stu-id="11854-563">If you set "showLoadingIndicator : true" in your app manifest, then for the page to load correctly, you must modify the content pages of your tabs and task modules as per the protocol described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="11854-564">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="11854-564">isFullScreen</span></span>

 <span data-ttu-id="11854-565">**Opcional** — Boolean</span><span class="sxs-lookup"><span data-stu-id="11854-565">**Optional** — boolean</span></span>

<span data-ttu-id="11854-566">Indicar onde um aplicativo pessoal é renderizado com ou sem uma barra de cabeçalho de tabulação.</span><span class="sxs-lookup"><span data-stu-id="11854-566">Indicate where a personal app is rendered with or without a tab-header bar.</span></span> <span data-ttu-id="11854-567">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="11854-567">Default: **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="11854-568">activities</span><span class="sxs-lookup"><span data-stu-id="11854-568">activities</span></span>

<span data-ttu-id="11854-569">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="11854-569">**Optional** — object</span></span>

<span data-ttu-id="11854-570">Defina as propriedades que seu aplicativo usará para postar em um feed de atividades do usuário.</span><span class="sxs-lookup"><span data-stu-id="11854-570">Define the properties your app will use to post to a user activity feed.</span></span>

|<span data-ttu-id="11854-571">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-571">Name</span></span>| <span data-ttu-id="11854-572">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-572">Type</span></span>| <span data-ttu-id="11854-573">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-573">Maximum size</span></span> | <span data-ttu-id="11854-574">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-574">Required</span></span> | <span data-ttu-id="11854-575">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-575">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="11854-576">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="11854-576">array of Objects</span></span>|<span data-ttu-id="11854-577">128 itens</span><span class="sxs-lookup"><span data-stu-id="11854-577">128 items</span></span>| | <span data-ttu-id="11854-578">Especifique os tipos de atividades que seu aplicativo pode postar para um feed de atividades do usuário.</span><span class="sxs-lookup"><span data-stu-id="11854-578">Specify the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="11854-579">Activities. Activityfiles</span><span class="sxs-lookup"><span data-stu-id="11854-579">activities.activityTypes</span></span>

|<span data-ttu-id="11854-580">Nome</span><span class="sxs-lookup"><span data-stu-id="11854-580">Name</span></span>| <span data-ttu-id="11854-581">Tipo</span><span class="sxs-lookup"><span data-stu-id="11854-581">Type</span></span>| <span data-ttu-id="11854-582">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="11854-582">Maximum size</span></span> | <span data-ttu-id="11854-583">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="11854-583">Required</span></span> | <span data-ttu-id="11854-584">Descrição</span><span class="sxs-lookup"><span data-stu-id="11854-584">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="11854-585">string</span><span class="sxs-lookup"><span data-stu-id="11854-585">string</span></span>|<span data-ttu-id="11854-586">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-586">32 characters</span></span>|<span data-ttu-id="11854-587">✔</span><span class="sxs-lookup"><span data-stu-id="11854-587">✔</span></span>|<span data-ttu-id="11854-588">O tipo de notificação.</span><span class="sxs-lookup"><span data-stu-id="11854-588">The notification type.</span></span> <span data-ttu-id="11854-589">*Veja abaixo*.</span><span class="sxs-lookup"><span data-stu-id="11854-589">*See below*.</span></span>|
|`description`|<span data-ttu-id="11854-590">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-590">string</span></span>|<span data-ttu-id="11854-591">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-591">128 characters</span></span>|<span data-ttu-id="11854-592">✔</span><span class="sxs-lookup"><span data-stu-id="11854-592">✔</span></span>|<span data-ttu-id="11854-593">Uma breve descrição da notificação.</span><span class="sxs-lookup"><span data-stu-id="11854-593">A brief description of the notification.</span></span> <span data-ttu-id="11854-594">*Veja abaixo*.</span><span class="sxs-lookup"><span data-stu-id="11854-594">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="11854-595">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-595">string</span></span>|<span data-ttu-id="11854-596">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="11854-596">128 characters</span></span>|<span data-ttu-id="11854-597">✔</span><span class="sxs-lookup"><span data-stu-id="11854-597">✔</span></span>|<span data-ttu-id="11854-598">Ex: "{actor} tarefa criada {TaskId} para você"</span><span class="sxs-lookup"><span data-stu-id="11854-598">Ex: "{actor} created task {taskId} for you"</span></span>|

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
