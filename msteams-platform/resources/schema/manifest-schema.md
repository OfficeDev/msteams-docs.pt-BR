---
title: Referência de esquema de manifesto
description: Descreve o esquema suportado pelo manifesto para o Microsoft Teams
keywords: esquema de manifesto do teams
author: laujan
ms.author: lajanuar
ms.openlocfilehash: aea75276d37ae0a99ecc55b204d29706cc5a07c8
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237976"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="460ab-104">Referência: esquema de manifesto para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="460ab-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="460ab-105">O manifesto do Microsoft Teams descreve como o aplicativo integra-se ao produto Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="460ab-105">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="460ab-106">Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="460ab-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="460ab-107">As versões anteriores 1.0-1.4 também são suportadas (usando "v1. x" na URL).</span><span class="sxs-lookup"><span data-stu-id="460ab-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="460ab-108">O seguinte exemplo de esquema mostra todas as opções de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="460ab-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="460ab-109">Exemplo de manifesto completo</span><span class="sxs-lookup"><span data-stu-id="460ab-109">Sample full manifest</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
  "manifestVersion": "1.7",
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
      "sharePointPreviewImage": "Relative path to a tab preview image for use in SharePoint — 1024px X 768",
      "supportedSharePointHosts": "Define how your tab wil be made available in SharePoint (full page or web part)"
    }
  ],
  "staticTabs": [
    {
      "entityId": "unique Id for the page entity",
      "scopes": [
        "personal"
      ],
      "name": "Display name of tab",
      "contentUrl": "https://contoso.com/content (displayed in Teams canvas)",
      "websiteUrl": "https://contoso.com/content (displayed in web browser"
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

<span data-ttu-id="460ab-110">O esquema define as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="460ab-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="460ab-111">$schema</span><span class="sxs-lookup"><span data-stu-id="460ab-111">$schema</span></span>

<span data-ttu-id="460ab-112">*Opcional, mas recomendado* — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-112">*Optional, but recommended* — string</span></span>

<span data-ttu-id="460ab-113">A URL https://que faz referência ao esquema JSON para o manifesto.</span><span class="sxs-lookup"><span data-stu-id="460ab-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="460ab-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="460ab-114">manifestVersion</span></span>

<span data-ttu-id="460ab-115">**Obrigatório** — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-115">**Required** — string</span></span>

<span data-ttu-id="460ab-116">A versão do esquema de manifesto que este manifesto está usando.</span><span class="sxs-lookup"><span data-stu-id="460ab-116">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="460ab-117">Ele deve ser "1,5".</span><span class="sxs-lookup"><span data-stu-id="460ab-117">It should be "1.5".</span></span>

## <a name="version"></a><span data-ttu-id="460ab-118">versão</span><span class="sxs-lookup"><span data-stu-id="460ab-118">version</span></span>

<span data-ttu-id="460ab-119">**Obrigatório** — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-119">**Required** — string</span></span>

<span data-ttu-id="460ab-120">A versão do aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="460ab-120">The version of the specific app.</span></span> <span data-ttu-id="460ab-121">Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada.</span><span class="sxs-lookup"><span data-stu-id="460ab-121">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="460ab-122">Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="460ab-122">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="460ab-123">Se este aplicativo foi enviado para o repositório, o novo manifesto terá que ser reenviado e validado novamente.</span><span class="sxs-lookup"><span data-stu-id="460ab-123">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="460ab-124">Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, após serem aprovados.</span><span class="sxs-lookup"><span data-stu-id="460ab-124">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="460ab-125">Se as permissões solicitadas pelo aplicativo forem alteradas, os usuários serão solicitados a atualizar e a dar o consentimento novamente para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-125">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="460ab-126">Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (principal. Mínima. PATCH).</span><span class="sxs-lookup"><span data-stu-id="460ab-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="460ab-127">id</span><span class="sxs-lookup"><span data-stu-id="460ab-127">id</span></span>

<span data-ttu-id="460ab-128">**Obrigatório** – ID do aplicativo da Microsoft</span><span class="sxs-lookup"><span data-stu-id="460ab-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="460ab-129">O identificador exclusivo gerado pela Microsoft para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-129">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="460ab-130">Se você tiver registrado um bot por meio da Microsoft bot Framework, ou se o aplicativo Web da sua guia já estiver conectado com a Microsoft, você já deve ter um ID e deve inseri-lo aqui.</span><span class="sxs-lookup"><span data-stu-id="460ab-130">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="460ab-131">Caso contrário, você deve gerar uma nova ID no portal de registro de aplicativos da Microsoft ([meus aplicativos](https://apps.dev.microsoft.com)), inseri-la aqui e reutilizá-la quando você adicionar um bot. Observação: se você estiver enviando uma atualização para o seu aplicativo existente no AppSource, a ID em seu manifesto não deverá ser modificada.</span><span class="sxs-lookup"><span data-stu-id="460ab-131">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you add a bot.Note: If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="460ab-132">developer</span><span class="sxs-lookup"><span data-stu-id="460ab-132">developer</span></span>

<span data-ttu-id="460ab-133">**Obrigatório** — objeto</span><span class="sxs-lookup"><span data-stu-id="460ab-133">**Required** — object</span></span>

<span data-ttu-id="460ab-134">Especifica informações sobre sua empresa.</span><span class="sxs-lookup"><span data-stu-id="460ab-134">Specifies information about your company.</span></span> <span data-ttu-id="460ab-135">Para aplicativos enviados para o AppSource (anteriormente Office Store), esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="460ab-135">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="460ab-136">Veja nossas [diretrizes de publicação](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="460ab-136">See our [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="460ab-137">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-137">Name</span></span>| <span data-ttu-id="460ab-138">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-138">Maximum size</span></span> | <span data-ttu-id="460ab-139">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-139">Required</span></span> | <span data-ttu-id="460ab-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-140">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="460ab-141">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-141">32 characters</span></span>|<span data-ttu-id="460ab-142">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-142">✔</span></span>|<span data-ttu-id="460ab-143">O nome de exibição para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="460ab-143">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="460ab-144">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-144">2048 characters</span></span>|<span data-ttu-id="460ab-145">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-145">✔</span></span>|<span data-ttu-id="460ab-146">A URL do https://para o site do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="460ab-146">The https:// URL to the developer's website.</span></span> <span data-ttu-id="460ab-147">Este link deve levar os usuários à sua página de aterrissagem específica da empresa ou do produto.</span><span class="sxs-lookup"><span data-stu-id="460ab-147">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="460ab-148">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-148">2048 characters</span></span>|<span data-ttu-id="460ab-149">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-149">✔</span></span>|<span data-ttu-id="460ab-150">A URL do https://para a política de privacidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="460ab-150">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="460ab-151">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-151">2048 characters</span></span>|<span data-ttu-id="460ab-152">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-152">✔</span></span>|<span data-ttu-id="460ab-153">A URL do https://para os termos de uso do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="460ab-153">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="460ab-154">10 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-154">10 characters</span></span>| |<span data-ttu-id="460ab-155">**Opcional** A ID de rede do parceiro da Microsoft que identifica a organização do parceiro que está criando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-155">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="460ab-156">nome</span><span class="sxs-lookup"><span data-stu-id="460ab-156">name</span></span>

<span data-ttu-id="460ab-157">**Obrigatório** — objeto</span><span class="sxs-lookup"><span data-stu-id="460ab-157">**Required** — object</span></span>

<span data-ttu-id="460ab-158">O nome da sua experiência de aplicativo, exibido aos usuários na experiência do teams.</span><span class="sxs-lookup"><span data-stu-id="460ab-158">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="460ab-159">Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="460ab-159">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="460ab-160">Os valores de `short` e `full` não devem ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="460ab-160">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="460ab-161">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-161">Name</span></span>| <span data-ttu-id="460ab-162">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-162">Maximum size</span></span> | <span data-ttu-id="460ab-163">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-163">Required</span></span> | <span data-ttu-id="460ab-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-164">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="460ab-165">30 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-165">30 characters</span></span>|<span data-ttu-id="460ab-166">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-166">✔</span></span>|<span data-ttu-id="460ab-167">O nome de exibição curto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-167">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="460ab-168">100 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-168">100 characters</span></span>||<span data-ttu-id="460ab-169">O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.</span><span class="sxs-lookup"><span data-stu-id="460ab-169">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="460ab-170">descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-170">description</span></span>

<span data-ttu-id="460ab-171">**Obrigatório** — objeto</span><span class="sxs-lookup"><span data-stu-id="460ab-171">**Required** — object</span></span>

<span data-ttu-id="460ab-172">Descreve seu aplicativo para os usuários.</span><span class="sxs-lookup"><span data-stu-id="460ab-172">Describes your app to users.</span></span> <span data-ttu-id="460ab-173">Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.</span><span class="sxs-lookup"><span data-stu-id="460ab-173">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="460ab-174">Certifique-se de que sua descrição descreve precisamente sua experiência e fornece informações para ajudar os clientes potenciais a entender o que a sua experiência faz.</span><span class="sxs-lookup"><span data-stu-id="460ab-174">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="460ab-175">Você também deve observar, na descrição completa, se for necessário usar uma conta externa.</span><span class="sxs-lookup"><span data-stu-id="460ab-175">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="460ab-176">Os valores de `short` e `full` não devem ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="460ab-176">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="460ab-177">Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir nenhum outro nome de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-177">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="460ab-178">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-178">Name</span></span>| <span data-ttu-id="460ab-179">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-179">Maximum size</span></span> | <span data-ttu-id="460ab-180">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-180">Required</span></span> | <span data-ttu-id="460ab-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-181">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="460ab-182">80 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-182">80 characters</span></span>|<span data-ttu-id="460ab-183">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-183">✔</span></span>|<span data-ttu-id="460ab-184">Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.</span><span class="sxs-lookup"><span data-stu-id="460ab-184">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="460ab-185">4000 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-185">4000 characters</span></span>|<span data-ttu-id="460ab-186">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-186">✔</span></span>|<span data-ttu-id="460ab-187">A descrição completa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-187">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="460ab-188">Packagenamena</span><span class="sxs-lookup"><span data-stu-id="460ab-188">packageName</span></span>

<span data-ttu-id="460ab-189">**Opcional** — cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-189">**Optional** — string</span></span>

<span data-ttu-id="460ab-190">Um identificador exclusivo para esse aplicativo na notação de domínio reverso; por exemplo, com. example. MyApp.</span><span class="sxs-lookup"><span data-stu-id="460ab-190">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="460ab-191">Comprimento máximo: 64 caracteres.</span><span class="sxs-lookup"><span data-stu-id="460ab-191">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="460ab-192">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="460ab-192">localizationInfo</span></span>

<span data-ttu-id="460ab-193">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="460ab-193">**Optional** — object</span></span>

<span data-ttu-id="460ab-194">Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais.</span><span class="sxs-lookup"><span data-stu-id="460ab-194">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="460ab-195">Confira [localização](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="460ab-195">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="460ab-196">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-196">Name</span></span>| <span data-ttu-id="460ab-197">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-197">Maximum size</span></span> | <span data-ttu-id="460ab-198">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-198">Required</span></span> | <span data-ttu-id="460ab-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-199">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="460ab-200">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-200">✔</span></span>|<span data-ttu-id="460ab-201">A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.</span><span class="sxs-lookup"><span data-stu-id="460ab-201">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="460ab-202">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="460ab-202">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="460ab-203">Uma matriz de objetos especificando traduções de idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="460ab-203">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="460ab-204">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-204">Name</span></span>| <span data-ttu-id="460ab-205">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-205">Maximum size</span></span> | <span data-ttu-id="460ab-206">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-206">Required</span></span> | <span data-ttu-id="460ab-207">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-207">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="460ab-208">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-208">✔</span></span>|<span data-ttu-id="460ab-209">A marca de idioma das cadeias de caracteres no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="460ab-209">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="460ab-210">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-210">✔</span></span>|<span data-ttu-id="460ab-211">Um caminho de arquivo relativo para um arquivo. JSON que contém as cadeias de caracteres traduzidas.</span><span class="sxs-lookup"><span data-stu-id="460ab-211">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="460ab-212">ícones</span><span class="sxs-lookup"><span data-stu-id="460ab-212">icons</span></span>

<span data-ttu-id="460ab-213">**Obrigatório** — objeto</span><span class="sxs-lookup"><span data-stu-id="460ab-213">**Required** — object</span></span>

<span data-ttu-id="460ab-214">Ícones usados no aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="460ab-214">Icons used within the Teams app.</span></span> <span data-ttu-id="460ab-215">Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.</span><span class="sxs-lookup"><span data-stu-id="460ab-215">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="460ab-216">Consulte [ícones](~/concepts/build-and-test/apps-package.md#icons) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="460ab-216">See [Icons](~/concepts/build-and-test/apps-package.md#icons) for more information.</span></span>

|<span data-ttu-id="460ab-217">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-217">Name</span></span>| <span data-ttu-id="460ab-218">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-218">Maximum size</span></span> | <span data-ttu-id="460ab-219">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-219">Required</span></span> | <span data-ttu-id="460ab-220">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-220">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="460ab-221">32 x 32 pixels</span><span class="sxs-lookup"><span data-stu-id="460ab-221">32 x 32 pixels</span></span>|<span data-ttu-id="460ab-222">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-222">✔</span></span>|<span data-ttu-id="460ab-223">Um caminho de arquivo relativo para um ícone de estrutura de tópicos de PNG de 32 x 32 transparente.</span><span class="sxs-lookup"><span data-stu-id="460ab-223">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="460ab-224">192 x 192 pixels</span><span class="sxs-lookup"><span data-stu-id="460ab-224">192 x 192 pixels</span></span>|<span data-ttu-id="460ab-225">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-225">✔</span></span>|<span data-ttu-id="460ab-226">Um caminho de arquivo relativo para um ícone de 192x192 do PNG completo.</span><span class="sxs-lookup"><span data-stu-id="460ab-226">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="460ab-227">accentColor</span><span class="sxs-lookup"><span data-stu-id="460ab-227">accentColor</span></span>

<span data-ttu-id="460ab-228">**Opcional** – código de cor hex HTML</span><span class="sxs-lookup"><span data-stu-id="460ab-228">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="460ab-229">Uma cor a ser usada em conjunto com e como um plano de fundo para seus ícones de estrutura de tópicos.</span><span class="sxs-lookup"><span data-stu-id="460ab-229">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="460ab-230">O valor deve ser um código de cor HTML válido começando com ' # ', por exemplo `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="460ab-230">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="460ab-231">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="460ab-231">configurableTabs</span></span>

<span data-ttu-id="460ab-232">**Opcional** — array</span><span class="sxs-lookup"><span data-stu-id="460ab-232">**Optional** — array</span></span>

<span data-ttu-id="460ab-233">Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração adicional antes de ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="460ab-233">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="460ab-234">Guias configuráveis têm suporte apenas no escopo Teams (não pessoal), e atualmente só há suporte para **uma** guia por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-234">Configurable tabs are supported only in the teams scope (not personal), and currently only **one** tab per app is supported.</span></span>

|<span data-ttu-id="460ab-235">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-235">Name</span></span>| <span data-ttu-id="460ab-236">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-236">Type</span></span>| <span data-ttu-id="460ab-237">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-237">Maximum size</span></span> | <span data-ttu-id="460ab-238">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-238">Required</span></span> | <span data-ttu-id="460ab-239">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-239">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="460ab-240">string</span><span class="sxs-lookup"><span data-stu-id="460ab-240">string</span></span>|<span data-ttu-id="460ab-241">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-241">2048 characters</span></span>|<span data-ttu-id="460ab-242">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-242">✔</span></span>|<span data-ttu-id="460ab-243">A URL do https://a ser usada ao configurar a guia.</span><span class="sxs-lookup"><span data-stu-id="460ab-243">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="460ab-244">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="460ab-244">array of enum</span></span>|<span data-ttu-id="460ab-245">1</span><span class="sxs-lookup"><span data-stu-id="460ab-245">1</span></span>|<span data-ttu-id="460ab-246">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-246">✔</span></span>|<span data-ttu-id="460ab-247">No momento, as guias configuráveis só dão suporte a `team` e os `groupchat` escopos.</span><span class="sxs-lookup"><span data-stu-id="460ab-247">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="460ab-248">booliano</span><span class="sxs-lookup"><span data-stu-id="460ab-248">boolean</span></span>|||<span data-ttu-id="460ab-249">Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação.</span><span class="sxs-lookup"><span data-stu-id="460ab-249">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="460ab-250">Padrão: **true**.</span><span class="sxs-lookup"><span data-stu-id="460ab-250">Default: **true**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="460ab-251">string</span><span class="sxs-lookup"><span data-stu-id="460ab-251">string</span></span>|<span data-ttu-id="460ab-252">2048</span><span class="sxs-lookup"><span data-stu-id="460ab-252">2048</span></span>||<span data-ttu-id="460ab-253">Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="460ab-253">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="460ab-254">Tamanho 1024x768.</span><span class="sxs-lookup"><span data-stu-id="460ab-254">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="460ab-255">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="460ab-255">array of enum</span></span>|<span data-ttu-id="460ab-256">1</span><span class="sxs-lookup"><span data-stu-id="460ab-256">1</span></span>||<span data-ttu-id="460ab-257">Define como sua guia será disponibilizada no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="460ab-257">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="460ab-258">Opções são `sharePointFullPage` e `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="460ab-258">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="460ab-259">staticTabs</span><span class="sxs-lookup"><span data-stu-id="460ab-259">staticTabs</span></span>

<span data-ttu-id="460ab-260">**Opcional** — array</span><span class="sxs-lookup"><span data-stu-id="460ab-260">**Optional** — array</span></span>

<span data-ttu-id="460ab-261">Define um conjunto de guias que podem ser "fixadas" por padrão, sem o usuário adicioná-las manualmente.</span><span class="sxs-lookup"><span data-stu-id="460ab-261">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="460ab-262">As guias estáticas declaradas no `personal` escopo são sempre fixadas para a experiência pessoal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-262">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="460ab-263">Guias static declaradas no `team` escopo não são suportadas atualmente.</span><span class="sxs-lookup"><span data-stu-id="460ab-263">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="460ab-264">Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="460ab-264">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="460ab-265">Esse bloco é necessário somente para soluções que oferecem uma solução de guia estática.</span><span class="sxs-lookup"><span data-stu-id="460ab-265">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="460ab-266">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-266">Name</span></span>| <span data-ttu-id="460ab-267">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-267">Type</span></span>| <span data-ttu-id="460ab-268">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-268">Maximum size</span></span> | <span data-ttu-id="460ab-269">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-269">Required</span></span> | <span data-ttu-id="460ab-270">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-270">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="460ab-271">string</span><span class="sxs-lookup"><span data-stu-id="460ab-271">string</span></span>|<span data-ttu-id="460ab-272">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-272">64 characters</span></span>|<span data-ttu-id="460ab-273">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-273">✔</span></span>|<span data-ttu-id="460ab-274">Um identificador exclusivo para a entidade que a guia exibe.</span><span class="sxs-lookup"><span data-stu-id="460ab-274">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="460ab-275">string</span><span class="sxs-lookup"><span data-stu-id="460ab-275">string</span></span>|<span data-ttu-id="460ab-276">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-276">128 characters</span></span>|<span data-ttu-id="460ab-277">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-277">✔</span></span>|<span data-ttu-id="460ab-278">O nome de exibição da guia na interface de canal.</span><span class="sxs-lookup"><span data-stu-id="460ab-278">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="460ab-279">string</span><span class="sxs-lookup"><span data-stu-id="460ab-279">string</span></span>|<span data-ttu-id="460ab-280">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-280">2048 characters</span></span>|<span data-ttu-id="460ab-281">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-281">✔</span></span>|<span data-ttu-id="460ab-282">A URL https://que aponta para a interface do usuário da entidade a ser exibida na tela do teams.</span><span class="sxs-lookup"><span data-stu-id="460ab-282">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="460ab-283">string</span><span class="sxs-lookup"><span data-stu-id="460ab-283">string</span></span>|<span data-ttu-id="460ab-284">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-284">2048 characters</span></span>||<span data-ttu-id="460ab-285">A URL do https://para apontar para o modo de exibição de um usuário em um navegador.</span><span class="sxs-lookup"><span data-stu-id="460ab-285">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="460ab-286">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="460ab-286">array of enum</span></span>|<span data-ttu-id="460ab-287">1</span><span class="sxs-lookup"><span data-stu-id="460ab-287">1</span></span>|<span data-ttu-id="460ab-288">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-288">✔</span></span>|<span data-ttu-id="460ab-289">Atualmente, as guias estáticas oferecem suporte somente ao `personal` escopo, o que significa que ela pode ser provisionada somente como parte da experiência pessoal.</span><span class="sxs-lookup"><span data-stu-id="460ab-289">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

> [!NOTE]
> <span data-ttu-id="460ab-290">Se suas guias exigirem informações dependentes de contexto para exibir conteúdo relevante ou para iniciar um fluxo de autenticação, *consulte* [obter contexto para a guia do Microsoft Teams](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="460ab-290">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="460ab-291">robôs</span><span class="sxs-lookup"><span data-stu-id="460ab-291">bots</span></span>

<span data-ttu-id="460ab-292">**Opcional** — array</span><span class="sxs-lookup"><span data-stu-id="460ab-292">**Optional** — array</span></span>

<span data-ttu-id="460ab-293">Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="460ab-293">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="460ab-294">O item é uma matriz (máximo de apenas 1 elemento &mdash; atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="460ab-294">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="460ab-295">Esse bloco é necessário somente para soluções que oferecem uma experiência de bot.</span><span class="sxs-lookup"><span data-stu-id="460ab-295">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="460ab-296">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-296">Name</span></span>| <span data-ttu-id="460ab-297">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-297">Type</span></span>| <span data-ttu-id="460ab-298">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-298">Maximum size</span></span> | <span data-ttu-id="460ab-299">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-299">Required</span></span> | <span data-ttu-id="460ab-300">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-300">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="460ab-301">string</span><span class="sxs-lookup"><span data-stu-id="460ab-301">string</span></span>|<span data-ttu-id="460ab-302">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-302">64 characters</span></span>|<span data-ttu-id="460ab-303">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-303">✔</span></span>|<span data-ttu-id="460ab-304">O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="460ab-304">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="460ab-305">Isso pode ser o mesmo que a ID de [aplicativo](#id)geral.</span><span class="sxs-lookup"><span data-stu-id="460ab-305">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="460ab-306">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="460ab-306">array of enum</span></span>|<span data-ttu-id="460ab-307">3D</span><span class="sxs-lookup"><span data-stu-id="460ab-307">3</span></span>|<span data-ttu-id="460ab-308">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-308">✔</span></span>|<span data-ttu-id="460ab-309">Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`).</span><span class="sxs-lookup"><span data-stu-id="460ab-309">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="460ab-310">Essas opções são não exclusivas.</span><span class="sxs-lookup"><span data-stu-id="460ab-310">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="460ab-311">booliano</span><span class="sxs-lookup"><span data-stu-id="460ab-311">boolean</span></span>|||<span data-ttu-id="460ab-312">Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico.</span><span class="sxs-lookup"><span data-stu-id="460ab-312">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="460ab-313">Será **`false`**</span><span class="sxs-lookup"><span data-stu-id="460ab-313">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="460ab-314">booliano</span><span class="sxs-lookup"><span data-stu-id="460ab-314">boolean</span></span>|||<span data-ttu-id="460ab-315">Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="460ab-315">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="460ab-316">Será `**false**`</span><span class="sxs-lookup"><span data-stu-id="460ab-316">Default: `**false**`</span></span>|
|`supportsFiles`|<span data-ttu-id="460ab-317">booliano</span><span class="sxs-lookup"><span data-stu-id="460ab-317">boolean</span></span>|||<span data-ttu-id="460ab-318">Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="460ab-318">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="460ab-319">Será **`false`**</span><span class="sxs-lookup"><span data-stu-id="460ab-319">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="460ab-320">bots. commandLists</span><span class="sxs-lookup"><span data-stu-id="460ab-320">bots.commandLists</span></span>

<span data-ttu-id="460ab-321">Uma lista opcional de comandos que seu bot pode recomendar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="460ab-321">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="460ab-322">O objeto é uma matriz (máximo de dois elementos) com todos os elementos do tipo `object` ; você deve definir uma lista de comandos separada para cada escopo que seu bot suporta.</span><span class="sxs-lookup"><span data-stu-id="460ab-322">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="460ab-323">Consulte [menus de bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="460ab-323">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="460ab-324">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-324">Name</span></span>| <span data-ttu-id="460ab-325">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-325">Type</span></span>| <span data-ttu-id="460ab-326">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-326">Maximum size</span></span> | <span data-ttu-id="460ab-327">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-327">Required</span></span> | <span data-ttu-id="460ab-328">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-328">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="460ab-329">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="460ab-329">array of enum</span></span>|<span data-ttu-id="460ab-330">3D</span><span class="sxs-lookup"><span data-stu-id="460ab-330">3</span></span>|<span data-ttu-id="460ab-331">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-331">✔</span></span>|<span data-ttu-id="460ab-332">Especifica o escopo para o qual a lista de comandos é válida.</span><span class="sxs-lookup"><span data-stu-id="460ab-332">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="460ab-333">As opção são `team`, `personal` e `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="460ab-333">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="460ab-334">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="460ab-334">array of objects</span></span>|<span data-ttu-id="460ab-335">10 </span><span class="sxs-lookup"><span data-stu-id="460ab-335">10</span></span>|<span data-ttu-id="460ab-336">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-336">✔</span></span>|<span data-ttu-id="460ab-337">Uma matriz de comandos que o bot suporta:</span><span class="sxs-lookup"><span data-stu-id="460ab-337">An array of commands the bot supports:</span></span><br><span data-ttu-id="460ab-338">`title`: o nome do comando bot (cadeia, 32)</span><span class="sxs-lookup"><span data-stu-id="460ab-338">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="460ab-339">`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)</span><span class="sxs-lookup"><span data-stu-id="460ab-339">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="460ab-340">bots. commandLists. Commands</span><span class="sxs-lookup"><span data-stu-id="460ab-340">bots.commandLists.commands</span></span>

|<span data-ttu-id="460ab-341">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-341">Name</span></span>| <span data-ttu-id="460ab-342">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-342">Type</span></span>| <span data-ttu-id="460ab-343">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-343">Maximum size</span></span> | <span data-ttu-id="460ab-344">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-344">Required</span></span> | <span data-ttu-id="460ab-345">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-345">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="460ab-346">title</span><span class="sxs-lookup"><span data-stu-id="460ab-346">title</span></span>|<span data-ttu-id="460ab-347">string</span><span class="sxs-lookup"><span data-stu-id="460ab-347">string</span></span>|<span data-ttu-id="460ab-348">12 </span><span class="sxs-lookup"><span data-stu-id="460ab-348">12</span></span>|<span data-ttu-id="460ab-349">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-349">✔</span></span>|<span data-ttu-id="460ab-350">O nome do comando do bot</span><span class="sxs-lookup"><span data-stu-id="460ab-350">The bot command name</span></span>|
|<span data-ttu-id="460ab-351">description</span><span class="sxs-lookup"><span data-stu-id="460ab-351">description</span></span>|<span data-ttu-id="460ab-352">string</span><span class="sxs-lookup"><span data-stu-id="460ab-352">string</span></span>|<span data-ttu-id="460ab-353">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-353">128 characters</span></span>|<span data-ttu-id="460ab-354">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-354">✔</span></span>|<span data-ttu-id="460ab-355">Uma descrição de texto simples ou um exemplo da sintaxe de comando e seus argumentos.</span><span class="sxs-lookup"><span data-stu-id="460ab-355">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="460ab-356">conectores</span><span class="sxs-lookup"><span data-stu-id="460ab-356">connectors</span></span>

<span data-ttu-id="460ab-357">**Opcional** — array</span><span class="sxs-lookup"><span data-stu-id="460ab-357">**Optional** — array</span></span>

<span data-ttu-id="460ab-358">O `connectors` bloco define um conector do Office 365 para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-358">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="460ab-359">O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="460ab-359">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="460ab-360">Esse bloco é necessário somente para soluções que fornecem um conector.</span><span class="sxs-lookup"><span data-stu-id="460ab-360">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="460ab-361">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-361">Name</span></span>| <span data-ttu-id="460ab-362">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-362">Type</span></span>| <span data-ttu-id="460ab-363">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-363">Maximum size</span></span> | <span data-ttu-id="460ab-364">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-364">Required</span></span> | <span data-ttu-id="460ab-365">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-365">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="460ab-366">string</span><span class="sxs-lookup"><span data-stu-id="460ab-366">string</span></span>|<span data-ttu-id="460ab-367">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-367">2048 characters</span></span>|<span data-ttu-id="460ab-368">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-368">✔</span></span>|<span data-ttu-id="460ab-369">A URL do https://a ser usada ao configurar o conector.</span><span class="sxs-lookup"><span data-stu-id="460ab-369">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="460ab-370">matriz de enumeração</span><span class="sxs-lookup"><span data-stu-id="460ab-370">array of enum</span></span>|<span data-ttu-id="460ab-371">1</span><span class="sxs-lookup"><span data-stu-id="460ab-371">1</span></span>|<span data-ttu-id="460ab-372">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-372">✔</span></span>|<span data-ttu-id="460ab-373">Especifica se o conector oferece uma experiência no contexto de um canal em uma `team` ou uma experiência com escopo para um usuário individual ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="460ab-373">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="460ab-374">Atualmente, só `team` há suporte para o escopo.</span><span class="sxs-lookup"><span data-stu-id="460ab-374">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="460ab-375">string</span><span class="sxs-lookup"><span data-stu-id="460ab-375">string</span></span>|<span data-ttu-id="460ab-376">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-376">64 characters</span></span>|<span data-ttu-id="460ab-377">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-377">✔</span></span>|<span data-ttu-id="460ab-378">Um identificador exclusivo para o conector que corresponde à sua ID no [painel do desenvolvedor de conectores](https://aka.ms/connectorsdashboard).</span><span class="sxs-lookup"><span data-stu-id="460ab-378">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="460ab-379">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="460ab-379">composeExtensions</span></span>

<span data-ttu-id="460ab-380">**Opcional** — array</span><span class="sxs-lookup"><span data-stu-id="460ab-380">**Optional** — array</span></span>

<span data-ttu-id="460ab-381">Define uma extensão de mensagens para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-381">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="460ab-382">O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem a funcionar.</span><span class="sxs-lookup"><span data-stu-id="460ab-382">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="460ab-383">O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="460ab-383">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="460ab-384">Esse bloco é necessário somente para soluções que forneçam uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="460ab-384">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="460ab-385">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-385">Name</span></span>| <span data-ttu-id="460ab-386">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-386">Type</span></span> | <span data-ttu-id="460ab-387">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-387">Maximum Size</span></span> | <span data-ttu-id="460ab-388">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-388">Required</span></span> | <span data-ttu-id="460ab-389">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-389">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="460ab-390">string</span><span class="sxs-lookup"><span data-stu-id="460ab-390">string</span></span>|<span data-ttu-id="460ab-391">64</span><span class="sxs-lookup"><span data-stu-id="460ab-391">64</span></span>|<span data-ttu-id="460ab-392">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-392">✔</span></span>|<span data-ttu-id="460ab-393">A ID exclusiva do aplicativo da Microsoft para o bot que faz a extensão do sistema de mensagens, conforme registrado na estrutura do bot.</span><span class="sxs-lookup"><span data-stu-id="460ab-393">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="460ab-394">Isso pode ser o mesmo que a ID de aplicativo geral.</span><span class="sxs-lookup"><span data-stu-id="460ab-394">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="460ab-395">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="460ab-395">array of objects</span></span>|<span data-ttu-id="460ab-396">10 </span><span class="sxs-lookup"><span data-stu-id="460ab-396">10</span></span>|<span data-ttu-id="460ab-397">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-397">✔</span></span>|<span data-ttu-id="460ab-398">matriz de comandos que a extensão de mensagens oferece suporte</span><span class="sxs-lookup"><span data-stu-id="460ab-398">array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="460ab-399">booliano</span><span class="sxs-lookup"><span data-stu-id="460ab-399">boolean</span></span>|||<span data-ttu-id="460ab-400">Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="460ab-400">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="460ab-401">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="460ab-401">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="460ab-402">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="460ab-402">array of Objects</span></span>|<span data-ttu-id="460ab-403">5 </span><span class="sxs-lookup"><span data-stu-id="460ab-403">5</span></span>||<span data-ttu-id="460ab-404">Uma lista de manipuladores que permitem que os aplicativos sejam chamados quando determinadas condições são atendidas.</span><span class="sxs-lookup"><span data-stu-id="460ab-404">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="460ab-405">Os domínios também devem ser listados no `validDomains`</span><span class="sxs-lookup"><span data-stu-id="460ab-405">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="460ab-406">string</span><span class="sxs-lookup"><span data-stu-id="460ab-406">string</span></span>|||<span data-ttu-id="460ab-407">O tipo de manipulador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="460ab-407">The type of message handler.</span></span> <span data-ttu-id="460ab-408">Deve ser `"link"`.</span><span class="sxs-lookup"><span data-stu-id="460ab-408">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="460ab-409">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-409">array of Strings</span></span>|||<span data-ttu-id="460ab-410">matriz de domínios para o qual o manipulador de mensagens de link pode se registrar.</span><span class="sxs-lookup"><span data-stu-id="460ab-410">array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="460ab-411">composeExtensions. Commands</span><span class="sxs-lookup"><span data-stu-id="460ab-411">composeExtensions.commands</span></span>

<span data-ttu-id="460ab-412">Sua extensão de mensagens deve declarar um ou mais comandos.</span><span class="sxs-lookup"><span data-stu-id="460ab-412">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="460ab-413">Cada comando aparece no Microsoft Teams como uma possível interação do ponto de entrada baseado na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="460ab-413">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="460ab-414">Há um máximo de 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="460ab-414">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="460ab-415">Cada item de comando é um objeto com a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="460ab-415">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="460ab-416">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-416">Name</span></span>| <span data-ttu-id="460ab-417">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-417">Type</span></span>| <span data-ttu-id="460ab-418">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-418">Maximum size</span></span> | <span data-ttu-id="460ab-419">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-419">Required</span></span> | <span data-ttu-id="460ab-420">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-420">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="460ab-421">string</span><span class="sxs-lookup"><span data-stu-id="460ab-421">string</span></span>|<span data-ttu-id="460ab-422">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-422">64 characters</span></span>|<span data-ttu-id="460ab-423">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-423">✔</span></span>|<span data-ttu-id="460ab-424">A ID do comando.</span><span class="sxs-lookup"><span data-stu-id="460ab-424">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="460ab-425">string</span><span class="sxs-lookup"><span data-stu-id="460ab-425">string</span></span>|<span data-ttu-id="460ab-426">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-426">32 characters</span></span>|<span data-ttu-id="460ab-427">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-427">✔</span></span>|<span data-ttu-id="460ab-428">O nome do comando amigável.</span><span class="sxs-lookup"><span data-stu-id="460ab-428">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="460ab-429">string</span><span class="sxs-lookup"><span data-stu-id="460ab-429">string</span></span>|<span data-ttu-id="460ab-430">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-430">64 characters</span></span>||<span data-ttu-id="460ab-431">Tipo do comando.</span><span class="sxs-lookup"><span data-stu-id="460ab-431">Type of the command.</span></span> <span data-ttu-id="460ab-432">Um `query` ou `action` .</span><span class="sxs-lookup"><span data-stu-id="460ab-432">One of `query` or `action`.</span></span> <span data-ttu-id="460ab-433">Padrão: **consulta**.</span><span class="sxs-lookup"><span data-stu-id="460ab-433">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="460ab-434">string</span><span class="sxs-lookup"><span data-stu-id="460ab-434">string</span></span>|<span data-ttu-id="460ab-435">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-435">128 characters</span></span>||<span data-ttu-id="460ab-436">A descrição que aparece para os usuários para indicar a finalidade desse comando.</span><span class="sxs-lookup"><span data-stu-id="460ab-436">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="460ab-437">booliano</span><span class="sxs-lookup"><span data-stu-id="460ab-437">boolean</span></span>|||<span data-ttu-id="460ab-438">Um valor Boolean que indica se o comando deve ser executado inicialmente sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="460ab-438">A boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="460ab-439">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="460ab-439">Default: **false**.</span></span>|
|`context`|<span data-ttu-id="460ab-440">matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-440">array of Strings</span></span>|<span data-ttu-id="460ab-441">3D</span><span class="sxs-lookup"><span data-stu-id="460ab-441">3</span></span>||<span data-ttu-id="460ab-442">Define onde a extensão de mensagem pode ser chamada.</span><span class="sxs-lookup"><span data-stu-id="460ab-442">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="460ab-443">Qualquer combinação de `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="460ab-443">Any combination of`compose`,`commandBox`,`message` .</span></span> <span data-ttu-id="460ab-444">O padrão é `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="460ab-444">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="460ab-445">booliano</span><span class="sxs-lookup"><span data-stu-id="460ab-445">boolean</span></span>|||<span data-ttu-id="460ab-446">Um valor Boolean que indica se ele deve buscar o módulo de tarefa dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="460ab-446">A boolean value that indicates if it should fetch the task module dynamically.</span></span> <span data-ttu-id="460ab-447">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="460ab-447">Default: **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="460ab-448">objeto</span><span class="sxs-lookup"><span data-stu-id="460ab-448">object</span></span>|||<span data-ttu-id="460ab-449">Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="460ab-449">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="460ab-450">string</span><span class="sxs-lookup"><span data-stu-id="460ab-450">string</span></span>|<span data-ttu-id="460ab-451">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-451">64 characters</span></span>||<span data-ttu-id="460ab-452">Título inicial da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="460ab-452">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="460ab-453">string</span><span class="sxs-lookup"><span data-stu-id="460ab-453">string</span></span>|||<span data-ttu-id="460ab-454">Largura da caixa de diálogo: um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '.</span><span class="sxs-lookup"><span data-stu-id="460ab-454">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="460ab-455">string</span><span class="sxs-lookup"><span data-stu-id="460ab-455">string</span></span>|||<span data-ttu-id="460ab-456">Altura da caixa de diálogo-um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '.</span><span class="sxs-lookup"><span data-stu-id="460ab-456">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="460ab-457">string</span><span class="sxs-lookup"><span data-stu-id="460ab-457">string</span></span>|||<span data-ttu-id="460ab-458">URL do WebView inicial.</span><span class="sxs-lookup"><span data-stu-id="460ab-458">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="460ab-459">matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="460ab-459">array of object</span></span>|<span data-ttu-id="460ab-460">5 itens</span><span class="sxs-lookup"><span data-stu-id="460ab-460">5 items</span></span>|<span data-ttu-id="460ab-461">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-461">✔</span></span>|<span data-ttu-id="460ab-462">A lista de parâmetros que o comando utiliza.</span><span class="sxs-lookup"><span data-stu-id="460ab-462">The list of parameters the command takes.</span></span> <span data-ttu-id="460ab-463">Mínimo: 1; máximo: 5.</span><span class="sxs-lookup"><span data-stu-id="460ab-463">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="460ab-464">string</span><span class="sxs-lookup"><span data-stu-id="460ab-464">string</span></span>|<span data-ttu-id="460ab-465">64 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-465">64 characters</span></span>|<span data-ttu-id="460ab-466">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-466">✔</span></span>|<span data-ttu-id="460ab-467">O nome do parâmetro conforme ele aparece no cliente.</span><span class="sxs-lookup"><span data-stu-id="460ab-467">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="460ab-468">Isso é incluído na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="460ab-468">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="460ab-469">string</span><span class="sxs-lookup"><span data-stu-id="460ab-469">string</span></span>|<span data-ttu-id="460ab-470">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-470">32 characters</span></span>|<span data-ttu-id="460ab-471">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-471">✔</span></span>|<span data-ttu-id="460ab-472">Título amigável para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="460ab-472">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="460ab-473">string</span><span class="sxs-lookup"><span data-stu-id="460ab-473">string</span></span>|<span data-ttu-id="460ab-474">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-474">128 characters</span></span>||<span data-ttu-id="460ab-475">Cadeia de caracteres amigável que descreve a finalidade deste parâmetro.</span><span class="sxs-lookup"><span data-stu-id="460ab-475">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="460ab-476">string</span><span class="sxs-lookup"><span data-stu-id="460ab-476">string</span></span>|<span data-ttu-id="460ab-477">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-477">512 characters</span></span>||<span data-ttu-id="460ab-478">Valor inicial para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="460ab-478">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="460ab-479">string</span><span class="sxs-lookup"><span data-stu-id="460ab-479">string</span></span>|<span data-ttu-id="460ab-480">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-480">128 characters</span></span>||<span data-ttu-id="460ab-481">Define o tipo de controle exibido em um módulo de tarefas para o `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="460ab-481">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="460ab-482">Um de `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="460ab-482">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="460ab-483">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="460ab-483">array of objects</span></span>|<span data-ttu-id="460ab-484">10 itens</span><span class="sxs-lookup"><span data-stu-id="460ab-484">10 items</span></span>||<span data-ttu-id="460ab-485">As opções de escolha para o `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="460ab-485">The choice options for the`choiceset`.</span></span> <span data-ttu-id="460ab-486">Use somente quando o `parameter.inputType` é `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="460ab-486">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="460ab-487">string</span><span class="sxs-lookup"><span data-stu-id="460ab-487">string</span></span>|<span data-ttu-id="460ab-488">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-488">128 characters</span></span>|<span data-ttu-id="460ab-489">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-489">✔</span></span>|<span data-ttu-id="460ab-490">Título da escolha.</span><span class="sxs-lookup"><span data-stu-id="460ab-490">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="460ab-491">string</span><span class="sxs-lookup"><span data-stu-id="460ab-491">string</span></span>|<span data-ttu-id="460ab-492">512 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-492">512 characters</span></span>|<span data-ttu-id="460ab-493">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-493">✔</span></span>|<span data-ttu-id="460ab-494">O valor da escolha.</span><span class="sxs-lookup"><span data-stu-id="460ab-494">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="460ab-495">permissões</span><span class="sxs-lookup"><span data-stu-id="460ab-495">permissions</span></span>

<span data-ttu-id="460ab-496">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-496">**Optional** — array of strings</span></span>

<span data-ttu-id="460ab-497">Uma matriz `string` que especifica quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão será executada.</span><span class="sxs-lookup"><span data-stu-id="460ab-497">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="460ab-498">As opções a seguir são não exclusivas:</span><span class="sxs-lookup"><span data-stu-id="460ab-498">The following options are non-exclusive:</span></span>

* <span data-ttu-id="460ab-499">`identity`&emsp;Requer informações de identidade do usuário</span><span class="sxs-lookup"><span data-stu-id="460ab-499">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="460ab-500">`messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas para membros da equipe</span><span class="sxs-lookup"><span data-stu-id="460ab-500">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="460ab-501">A alteração dessas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado.</span><span class="sxs-lookup"><span data-stu-id="460ab-501">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span> <span data-ttu-id="460ab-502">Veja [atualização do seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="460ab-502">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="460ab-503">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="460ab-503">devicePermissions</span></span>

<span data-ttu-id="460ab-504">**Opcional** — matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-504">**Optional** — array of strings</span></span>

<span data-ttu-id="460ab-505">Especifica os recursos nativos no dispositivo de um usuário para o qual seu aplicativo pode solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="460ab-505">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="460ab-506">As opções são:</span><span class="sxs-lookup"><span data-stu-id="460ab-506">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="460ab-507">validDomains</span><span class="sxs-lookup"><span data-stu-id="460ab-507">validDomains</span></span>

<span data-ttu-id="460ab-508">**Opcional**, exceto quando **necessário** , onde observado</span><span class="sxs-lookup"><span data-stu-id="460ab-508">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="460ab-509">Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="460ab-509">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="460ab-510">As listagens de domínio podem incluir curingas, por exemplo `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="460ab-510">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="460ab-511">Isso corresponde exatamente a um segmento do domínio; Se você precisar coincidir `a.b.example.com` e usar `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="460ab-511">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="460ab-512">Se a configuração de sua guia ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além daquele usado para configuração de guia, esse domínio deverá ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="460ab-512">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="460ab-513">No entanto, **não** é necessário incluir os domínios de provedores de identidade que você deseja suportar no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-513">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="460ab-514">Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve incluir o accounts.google.com no `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="460ab-514">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="460ab-515">Aplicativos do teams que exigem suas próprias URLs do SharePoint para funcionar bem, podem incluir "{teamsitedomain}" em sua lista de domínios válida.</span><span class="sxs-lookup"><span data-stu-id="460ab-515">Teams apps that require their own sharepoint URLs to function well, may include "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="460ab-516">Não adicione domínios que estejam fora do seu controle, seja diretamente ou via curingas.</span><span class="sxs-lookup"><span data-stu-id="460ab-516">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="460ab-517">Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="460ab-517">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="460ab-518">O objeto é uma matriz com todos os elementos do tipo `string` .</span><span class="sxs-lookup"><span data-stu-id="460ab-518">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="460ab-519">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="460ab-519">webApplicationInfo</span></span>

<span data-ttu-id="460ab-520">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="460ab-520">**Optional** — object</span></span>

<span data-ttu-id="460ab-521">Especifique a ID do aplicativo AAD e as informações do gráfico para ajudar os usuários a entrarem diretamente no aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="460ab-521">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="460ab-522">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-522">Name</span></span>| <span data-ttu-id="460ab-523">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-523">Type</span></span>| <span data-ttu-id="460ab-524">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-524">Maximum size</span></span> | <span data-ttu-id="460ab-525">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-525">Required</span></span> | <span data-ttu-id="460ab-526">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-526">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="460ab-527">string</span><span class="sxs-lookup"><span data-stu-id="460ab-527">string</span></span>|<span data-ttu-id="460ab-528">36 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-528">36 characters</span></span>|<span data-ttu-id="460ab-529">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-529">✔</span></span>|<span data-ttu-id="460ab-530">ID do aplicativo AAD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460ab-530">AAD application id of the app.</span></span> <span data-ttu-id="460ab-531">Esta ID deve ser um GUID.</span><span class="sxs-lookup"><span data-stu-id="460ab-531">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="460ab-532">string</span><span class="sxs-lookup"><span data-stu-id="460ab-532">string</span></span>|<span data-ttu-id="460ab-533">2048 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-533">2048 characters</span></span>||<span data-ttu-id="460ab-534">URL de recurso do aplicativo para aquisição de token de autenticação para SSO.</span><span class="sxs-lookup"><span data-stu-id="460ab-534">Resource url of app for acquiring auth token for SSO.</span></span>|
|`applicationPermissions`|<span data-ttu-id="460ab-535">matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-535">array of strings</span></span>|<span data-ttu-id="460ab-536">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-536">128 characters</span></span>||<span data-ttu-id="460ab-537">Especificar [consentimento específico de recurso](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions) granular</span><span class="sxs-lookup"><span data-stu-id="460ab-537">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="460ab-538">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="460ab-538">showLoadingIndicator</span></span>

<span data-ttu-id="460ab-539">**Opcional** — Boolean</span><span class="sxs-lookup"><span data-stu-id="460ab-539">**Optional** — boolean</span></span>

<span data-ttu-id="460ab-540">Indica se o indicador de carregamento deve ou não ser mostrado quando um app/Tab é carregado.</span><span class="sxs-lookup"><span data-stu-id="460ab-540">Indicate whether or not to show the loading indicator when an app/tab is loading.</span></span> <span data-ttu-id="460ab-541">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="460ab-541">Default: **false**.</span></span>
>[!NOTE]
><span data-ttu-id="460ab-542">Se você definir "showLoadingIndicator: true" em seu manifesto de aplicativo, para que a página seja carregada corretamente, você deve modificar as páginas de conteúdo de suas guias e módulos de tarefa, de acordo com o protocolo descrito em [Mostrar um documento indicador de carregamento nativo](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) .</span><span class="sxs-lookup"><span data-stu-id="460ab-542">If you set "showLoadingIndicator : true" in your app manifest, then for the page to load correctly, you must modify the content pages of your tabs and task modules as per the protocol described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="460ab-543">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="460ab-543">isFullScreen</span></span>

 <span data-ttu-id="460ab-544">**Opcional** — Boolean</span><span class="sxs-lookup"><span data-stu-id="460ab-544">**Optional** — boolean</span></span>

<span data-ttu-id="460ab-545">Indicar onde um aplicativo pessoal é renderizado com ou sem uma barra de cabeçalho de tabulação.</span><span class="sxs-lookup"><span data-stu-id="460ab-545">Indicate where a personal app is rendered with or without a tab-header bar.</span></span> <span data-ttu-id="460ab-546">Padrão: **false**.</span><span class="sxs-lookup"><span data-stu-id="460ab-546">Default: **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="460ab-547">activities</span><span class="sxs-lookup"><span data-stu-id="460ab-547">activities</span></span>

<span data-ttu-id="460ab-548">**Opcional** — objeto</span><span class="sxs-lookup"><span data-stu-id="460ab-548">**Optional** — object</span></span>

<span data-ttu-id="460ab-549">Defina as propriedades que seu aplicativo usará para postar em um feed de atividades do usuário.</span><span class="sxs-lookup"><span data-stu-id="460ab-549">Define the properties your app will use to post to a user activity feed.</span></span>

|<span data-ttu-id="460ab-550">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-550">Name</span></span>| <span data-ttu-id="460ab-551">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-551">Type</span></span>| <span data-ttu-id="460ab-552">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-552">Maximum size</span></span> | <span data-ttu-id="460ab-553">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-553">Required</span></span> | <span data-ttu-id="460ab-554">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-554">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="460ab-555">matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="460ab-555">array of Objects</span></span>|<span data-ttu-id="460ab-556">128 itens</span><span class="sxs-lookup"><span data-stu-id="460ab-556">128 items</span></span>| | <span data-ttu-id="460ab-557">Especifique os tipos de atividades que seu aplicativo pode postar para um feed de atividades do usuário.</span><span class="sxs-lookup"><span data-stu-id="460ab-557">Specify the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="460ab-558">Activities. Activityfiles</span><span class="sxs-lookup"><span data-stu-id="460ab-558">activities.activityTypes</span></span>

|<span data-ttu-id="460ab-559">Nome</span><span class="sxs-lookup"><span data-stu-id="460ab-559">Name</span></span>| <span data-ttu-id="460ab-560">Tipo</span><span class="sxs-lookup"><span data-stu-id="460ab-560">Type</span></span>| <span data-ttu-id="460ab-561">Tamanho máximo</span><span class="sxs-lookup"><span data-stu-id="460ab-561">Maximum size</span></span> | <span data-ttu-id="460ab-562">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="460ab-562">Required</span></span> | <span data-ttu-id="460ab-563">Descrição</span><span class="sxs-lookup"><span data-stu-id="460ab-563">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="460ab-564">string</span><span class="sxs-lookup"><span data-stu-id="460ab-564">string</span></span>|<span data-ttu-id="460ab-565">32 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-565">32 characters</span></span>|<span data-ttu-id="460ab-566">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-566">✔</span></span>|<span data-ttu-id="460ab-567">O tipo de notificação.</span><span class="sxs-lookup"><span data-stu-id="460ab-567">The notification type.</span></span> <span data-ttu-id="460ab-568">*Veja abaixo*.</span><span class="sxs-lookup"><span data-stu-id="460ab-568">*See below*.</span></span>|
|`description`|<span data-ttu-id="460ab-569">string</span><span class="sxs-lookup"><span data-stu-id="460ab-569">string</span></span>|<span data-ttu-id="460ab-570">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-570">128 characters</span></span>|<span data-ttu-id="460ab-571">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-571">✔</span></span>|<span data-ttu-id="460ab-572">Uma breve descrição da notificação.</span><span class="sxs-lookup"><span data-stu-id="460ab-572">A brief description of the notification.</span></span> <span data-ttu-id="460ab-573">*Veja abaixo*.</span><span class="sxs-lookup"><span data-stu-id="460ab-573">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="460ab-574">string</span><span class="sxs-lookup"><span data-stu-id="460ab-574">string</span></span>|<span data-ttu-id="460ab-575">128 caracteres</span><span class="sxs-lookup"><span data-stu-id="460ab-575">128 characters</span></span>|<span data-ttu-id="460ab-576">✔</span><span class="sxs-lookup"><span data-stu-id="460ab-576">✔</span></span>|<span data-ttu-id="460ab-577">Ex: "{actor} tarefa criada {TaskId} para você"</span><span class="sxs-lookup"><span data-stu-id="460ab-577">Ex: "{actor} created task {taskId} for you"</span></span>|

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
