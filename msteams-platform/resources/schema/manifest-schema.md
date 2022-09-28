---
title: Referência de esquema de manifesto
description: Neste artigo, você terá a versão mais recente do esquema de manifesto público para referência, esquema e manifesto completo de exemplo do Microsoft Teams.
ms.topic: reference
ms.localizationpriority: high
ms.openlocfilehash: 23bdb87bd1f5f3ea1fadb2527f64b5bebec0b157
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100165"
---
# <a name="app-manifest-schema-for-teams"></a>Esquema de manifesto do aplicativo do Teams

O manifesto do aplicativo Microsoft Teams descreve como seu aplicativo se integra ao produto Microsoft Teams. O manifesto do seu aplicativo deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json). As versões anteriores 1.0, 1.1,...,1.13, e a versão atual 1.14 são cada uma  suportadas (usando "v1.x" no URL).
Para obter mais informações sobre as alterações feitas em cada versão, consulte o [registro de alterações do manifesto](https://github.com/OfficeDev/microsoft-teams-app-schema/releases).

A tabela a seguir lista as versões do TeamsJS e do manifesto do aplicativo de acordo com diferentes cenários de aplicativo:

[!INCLUDE [pre-release-label](~/includes/teamjs-version-details.md)]

A amostra do esquema a seguir mostra todas as opções de extensibilidade:

## <a name="sample-full-manifest"></a>Amostra de manifesto completo

```json
{
    "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json",
    "manifestVersion": "1.14",
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
            "context": [
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
            "context": [
                "personalTab",
                "channelTab"
            ],
            "name": "Display name of tab",
            "contentUrl": "https://contoso.com/content (displayed in Teams canvas)",
            "websiteUrl": "https://contoso.com/content (displayed in web browser)",
            "searchUrl": "https://contoso.com/content (displayed in web browser)"
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
                    "description": "Command Description; e.g., Add a customer",
                    "initialRun": true,
                    "fetchTask": false ,
                    "parameters": [
                        {
                            "name": "custinfo",
                            "title": "Customer name",
                            "description": "Enter a customer name",
                            "inputType": "text"
                        }
                    ]
                },
                {
                    "id": "exampleCmd3",
                    "title": "Example Command 3",
                    "type": "action",
                    "context": [
                        "compose",
                        "commandBox",
                        "message"
                    ],
                    "description": "Command Description; e.g., Add a customer",
                    "fetchTask": false,
                    "taskInfo": {
                        "title": "Initial dialog title",
                        "width": "Dialog width",
                        "height": "Dialog height",
                        "url": "Initial webview URL"
                    }
                }
            ],
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
        "resource": "Resource URL for acquiring auth token for SSO"
    },
    "authorization": {
        "permissions": {
            "resourceSpecific": [
                {
                    "type": "Application",
                    "name": "ChannelSettings.Read.Group"
                },
                {
                    "type": "Delegated",
                    "name": "ChannelMeetingParticipant.Read.Group"
                }
            ]
        }
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
    "defaultBlockUntilAdminAction": true,
    "publisherDocsUrl": "https://website.com/app-info",
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
    ],
    "subscriptionOffer": {
        "offerId": "publisherId.offerId"
    },
    "meetingExtensionDefinition": {
        "scenes": [
            {
                "id": "9082c811-7e6a-4174-8173-6ccd57d377e6",
                "name": "Getting started sample",
                "file": "scenes/sceneMetadata.json",
                "preview": "scenes/scenePreview.png",
                "maxAudience": 15,
                "seatsReservedForOrganizersOrPresenters": 0
            },
            {
                "id": "afeaed22-f89b-48e1-98b4-46a514344e4a",
                "name": "Sample-1",
                "file": "scenes/sceneMetadata.json",
                "preview": "scenes/scenePreview.png",
                "maxAudience": 15,
                "seatsReservedForOrganizersOrPresenters": 3
            }
        ]
    }
}
```

O esquema define as seguintes propriedades:

## <a name="schema"></a>$esquema

Opcional, mas recomendado—cadeia de caracteres

A URL https:// referenciando o esquema JSON para o manifesto.

## <a name="manifestversion"></a>manifestVersion

**Obrigatório**—cadeia de caracteres

A versão do esquema de manifesto que este manifesto está usando. Use `1.13` para habilitar o suporte ao aplicativo Teams no Outlook e no Office; use `1.12` (ou anterior) para aplicativos somente para equipes.

## <a name="version"></a>versão

**Obrigatório**—cadeia de caracteres

A versão de um aplicativo específico. Quando você atualiza algo no seu manifesto, a versão também deve ser incrementada. Dessa forma, quando o novo manifesto é instalado, ele substitui o existente e o usuário recebe a nova funcionalidade. Quando este aplicativo foi enviado para a loja, o novo manifesto deve ser reenviado e revalidado. Os usuários do aplicativo recebem o novo manifesto atualizado automaticamente algumas horas após a aprovação do manifesto.

Se as solicitações de permissões do aplicativo forem alteradas, os usuários serão solicitados a atualizar e consentir novamente com o aplicativo..

Esta cadeia de caracteres da versão deve seguir o padrão [semver](http://semver.org/) (MAJOR.MINOR.PATCH).

## <a name="id"></a>ID

**Obrigatório**—ID do aplicativo da Microsoft

A ID é um identificador exclusivo gerado pela Microsoft para o aplicativo. Você tem uma ID se seu bot estiver registrado por meio do Microsoft Bot Framework. Você tem uma ID se o aplicativo web da sua guia já entrar com a Microsoft. Você deve inserir a ID aqui. Caso contrário, você deverá gerar uma nova ID no [Portal de Registro de Aplicativos da Microsoft](https://aka.ms/appregistrations). Use a mesma ID se você adicionar um bot.

> [!NOTE]
> Se você estiver enviando uma atualização para o seu aplicativo existente no AppSource, a ID em seu manifesto não deve ser modificada.

## <a name="developer"></a>developer

**Obrigatório**—objeto

Especifica informações sobre a sua empresa. Para aplicativos enviados à loja do Teams, esses valores devem corresponder às informações na listagem da loja. Para obter mais informações, consulte as [Diretrizes de publicação da loja do Teams](~/concepts/deploy-and-publish/appsource/publish.md).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`name`|32 caracteres|✔️|O nome de exibição do desenvolvedor.|
|`websiteUrl`|2048 caracteres|✔️|A URL https:// para o site do desenvolvedor. Esse link deve levar os usuários à página de destino específica da sua empresa ou do produto.|
|`privacyUrl`|2048 caracteres|✔️|A URL https:// para a política de privacidade do desenvolvedor.|
|`termsOfUseUrl`|2048 caracteres|✔️|A URL https:// para os termos de uso do desenvolvedor.|
|`mpnId`|10 caracteres| |**Opcional** A ID do Microsoft Partner Network que identifica a organização parceira criadora do aplicativo.|

## <a name="name"></a>nome

**Obrigatório**—objeto

O nome da sua experiência de aplicativo, exibido aos usuários na experiência do Teams. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações na entrada do AppSource. Os valores de `short` e `full` devem ser diferentes.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|30 caracteres|✔️|O nome de exibição curto para o aplicativo.|
|`full`|100 caracteres||O nome completo do aplicativo, utilizado se o nome completo do aplicativo exceder 30 caracteres.|

## <a name="description"></a>descrição

**Obrigatório**—objeto

Descreve o seu aplicativo para os usuários. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações na entrada do AppSource.

Certifique-se de que a sua descrição detalhe a sua experiência e ajude os clientes em potencial a entender o que sua experiência faz. Você deve anotar na descrição completa, se uma conta externa for necessária para uso. Os valores de `short` e `full` devem ser diferentes. Sua breve descrição não pode ser repetida dentro da descrição longa e não deve incluir nenhum outro nome de aplicativo.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|80 caracteres|✔️|Uma descrição curta da experiência do seu aplicativo, usada quando o espaço é limitado.|
|`full`|4000 caracteres|✔️|A descrição completa do seu aplicativo.|

## <a name="packagename"></a>packageName

Cadeia de caracteres—**opcional**

A unique identifier for the app in reverse domain notation; for example, com.example.myapp. Maximum length: 64 characters.

## <a name="localizationinfo"></a>localizationInfo

**Opcional**—objeto

Allows the specification of a default language and provides pointers to more language files. For more information, see [localization](~/concepts/build-and-test/apps-localization.md).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`defaultLanguageTag`||✔️|A marca de idioma das cadeia de caracteres neste arquivo de manifesto de nível superior.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Uma matriz de objetos especificando mais traduções de idiomas.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`languageTag`||✔️|A marca de idioma das cadeias de caracteres no arquivo fornecido.|
|`file`||✔️|Um caminho de arquivo relativo para o arquivo .json que contém as cadeias de caracteres traduzidas.|

## <a name="icons"></a>ícones

**Obrigatório**—objeto

Ícones usados no aplicativo Teams. Os arquivos de ícone devem ser incluídos como parte do pacote de upload. Para obter mais informações, consulte [Ícones](../../concepts/build-and-test/apps-package.md#app-icons).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`outline`|32 x 32 pixels|✔️|Um caminho de arquivo relativo para um ícone de contorno PNG transparente de 32x32.|
|`color`|192 x 192 pixels|✔️|Um caminho de arquivo relativo para um ícone PNG colorido de 192x192.|

## <a name="accentcolor"></a>accentColor

**Obrigatório**—Código de cores HTML hexadecimal

Uma cor para usar e como plano de fundo para os seus ícones de contorno.

O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee`.

## <a name="configurabletabs"></a>configurbleTabs

**Opcional**—matriz

Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada. As guias configuráveis são compatíveis apenas nos escopos `team` e `groupchat`, sendo que você pode configurar as mesmas guias várias vezes. No entanto, você pode defini-la no manifesto apenas uma vez.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔️|A URL https:// a ser usada ao configurar a guia.|
|`scopes`|matriz de enumerações|1|✔️|Atualmente, as guias configuráveis são compatíveis apenas com os escopos `team` e `groupchat`. |
|`canUpdateConfiguration`|Booliano|||A value indicating whether an instance of the tab's configuration can be updated by the user after creation. Default: **true**.|
|`context` |matriz de enumerações|6||O conjunto de `contextItem` escopos em que uma [guia é compatível](../../tabs/how-to/access-teams-context.md). Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|string|2048||A relative file path to a tab preview image for use in SharePoint. Size 1024x768. |
|`supportedSharePointHosts`|matriz de enumerações|1||Defines how your tab is made available in SharePoint. Options are `sharePointFullPage` and `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Opcional**—matriz

Define um conjunto de guias que podem ser "fixadas" por padrão, sem que o usuário as adicione manualmente. As guias estáticas declaradas no escopo `personal` são sempre vinculadas à experiência pessoal do aplicativo. As guias estáticas declaradas no escopo `team` não são suportadas no momento.

Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object`. Esse bloco é necessário apenas para soluções que fornecem uma solução de guia estática.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|string|64 caracteres|✔️|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|string|128 caracteres|✔️|O nome de exibição da guia na interface de canal.|
|`contentUrl`|string||✔️|A URL https:// que aponta para a interface do usuário da entidade a ser exibida na tela do Teams.|
|`websiteUrl`|string|||A URL https:// para apontar se um usuário optar por visualizar em um navegador.|
|`searchUrl`|string|||A URL https:// para apontar para as consultas de pesquisa de um usuário.|
|`scopes`|matriz de enumerações|1|✔️|Atualmente, as guias estáticas oferecem suporte apenas ao escopo `personal`, o que significa que elas podem ser provisionadas apenas como parte da experiência pessoal.|
|`context` | matriz de enumerações| 2|| O conjunto de `contextItem` escopos em que uma guia é compatível.|

> [!NOTE]
> The searchUrl feature is not available for the third-party developers.
> If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, For more information, see [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).

## <a name="bots"></a>bots

**Opcional**—matriz

Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.

O item é uma matriz (máximo de apenas um elemento &mdash;, atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object`. Esse bloco é necessário apenas para soluções que fornecem uma experiência de bot.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64 caracteres|✔️|O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. A ID pode ser igual a [ID do aplicativo](#id) geral.|
|`scopes`|matriz de enumerações|3|✔️|Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`). These options are non-exclusive.|
|`needsChannelSelector`|Boolean|||Describes whether or not the bot uses a user hint to add the bot to a specific channel. Default: **`false`**|
|`isNotificationOnly`|Boolean|||Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot. Default: **`false`**|
|`supportsFiles`|Boolean|||Indicates whether the bot supports the ability to upload/download files in personal chat. Default: **`false`**|
|`supportsCalling`|Booliano|||Um valor que indica onde um bot dá suporte a chamadas de áudio. **IMPORTANTE**: Esta propriedade é experimental no momento. As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.  A propriedade é fornecida apenas para fins de teste e exploração e não deve ser usada em aplicativos de produção. Padrão: **`false`**|
|`supportsVideo`|Booliano|||Um valor que indica onde um bot oferece suporte a chamadas com vídeo. **IMPORTANTE**: Esta propriedade é experimental no momento. As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.  A propriedade é fornecida apenas para fins de teste e exploração e não deve ser usada em aplicativos de produção. Padrão: **`false`**|

### <a name="botscommandlists"></a>bots.commandLists

Uma lista de comandos que seu bot pode recomendar aos usuários. O objeto é uma matriz (máximo de dois elementos) com todos os elementos do tipo `object`; você deve definir uma lista de comandos separada para cada escopo que o seu bot oferece suporte. Para obter mais informações, confira [Menus de bot](~/bots/how-to/create-a-bot-commands-menu.md).

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de enumerações|3|✔️|Specifies the scope for which the command list is valid. Options are `team`, `personal`, and `groupchat`.|
|`items.commands`|matriz de objetos|10|✔️|Uma matriz de comandos que o bot suporta:<br>`title`: o nome do comando bot (cadeia, 32)<br>`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)|

### <a name="botscommandlistscommands"></a>bots.commandLists.commands

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|title|string|12 |✔️|O nome do comando do bot.|
|description|string|128 caracteres|✔️|Uma descrição de texto simples ou um exemplo da sintaxe do comando e seus argumentos.|

## <a name="connectors"></a>conectores

**Opcional**—matriz

O bloco `connectors` define um conector do Office 365 para o aplicativo.

O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo `object`. Este bloco é necessário apenas para soluções que fornecem um Conector.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔️|A URL https:// a ser usada ao configurar o conector.|
|`scopes`|matriz de enumerações|1|✔️|Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`). Currently, only the `team` scope is supported.|
|`connectorId`|string|64 caracteres|✔️|Um identificador exclusivo para o Conector que corresponde a sua ID no [Painel do Desenvolvedor de Conectores](https://aka.ms/connectorsdashboard).|

## <a name="composeextensions"></a>composeExtensions

**Opcional**—matriz

Define uma extensão de mensagens para o aplicativo.

> [!NOTE]
> O nome do recurso foi alterado de "extensão de texto " para "extensão de mensagem" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem funcionando.

O item é uma matriz (máximo de um elemento) com todos os elementos do tipo `object`. Este bloco é necessário apenas para soluções que fornecem uma extensão de mensagens.

|Nome| Tipo | Tamanho Máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64|✔️|A ID exclusiva do aplicativo da Microsoft para o bot que oferece suporte à extensão de mensagens, conforme registrado no Bot Framework. A ID pode ser igual à ID geral do aplicativo.|
|`commands`|matriz de objetos|10|✔️|Matriz de comandos com suporte da extensão de mensagens.|
|`canUpdateConfiguration`|Booliano|||A value indicating whether the configuration of a message extension can be updated by the user. Default: **false**.|
|`messageHandlers`|matriz de Objetos|5||Uma lista de manipuladores que permitem que aplicativos sejam invocados quando determinadas condições são atendidas.|
|`messageHandlers.type`|string|||The type of message handler. Must be `"link"`.|
|`messageHandlers.value.domains`|matriz de Cadeias de Caracteres|||Matriz de domínios para os quais o manipulador de mensagens de link pode se registrar.|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Sua extensão de mensagens deve declarar um ou mais comandos com no máximo 10 comandos. Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário.

Cada item de comando é um objeto com a seguinte estrutura:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|64 caracteres|✔️|A ID do comando.|
|`title`|string|32 caracteres|✔️|O nome do comando amigável.|
|`type`|string|64 caracteres||O tipo do comando. Um de `query` ou `action`. Padrão: **consulta**.|
|`description`|string|128 caracteres||A descrição que aparece para os usuários para indicar a finalidade deste comando.|
|`initialRun`|Booliano|||A Boolean value indicates whether the command runs initially with no parameters. Default is **false**.|
|`context`|matriz de Cadeias de Caracteres|3||Define de onde a extensão da mensagem pode ser invocada. Qualquer combinação de `compose`,`commandBox`,`message`. O padrão é `["compose","commandBox"]`.|
|`fetchTask`|Booliano|||A Boolean value that indicates if it must fetch the task module dynamically. Default is **false**.|
|`taskInfo`|objeto|||Especifique o módulo de tarefa para pré-carregar ao usar um comando de extensão do sistema de mensagens.|
|`taskInfo.title`|string|64 caracteres||Título inicial da caixa de diálogo.|
|`taskInfo.width`|string|||Largura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.height`|string|||Altura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.url`|string|||URL inicial da webview.|
|`parameters`|matriz de objeto|5 itens|✔️|A lista de parâmetros que o comando usa. Mínimo: 1; máximo: 5.|
|`parameters.name`|string|64 caracteres|✔️|The name of the parameter as it appears in the client. The parameter name is included in the user request.|
|`parameters.title`|string|32 caracteres|✔️|Título amigável para o parâmetro.|
|`parameters.description`|string|128 caracteres||Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.|
|`parameters.value`|string|512 caracteres||Valor inicial para o parâmetro. Atualmente, não há suporte para o valor|
|`parameters.inputType`|string|128 caracteres||Defines the type of control displayed on a task module for`fetchTask: false` . One of `text, textarea, number, date, time, toggle, choiceset` .|
|`parameters.choices`|matriz de objetos|10 itens||As opções de escolha para `choiceset`. Use apenas quando `parameter.inputType` for `choiceset`.|
|`parameters.choices.title`|string|128 caracteres|✔️|Títulor da escolha.|
|`parameters.choices.value`|string|512 caracteres|✔️|O valor da escolha.|

## <a name="permissions"></a>permissões

**Opcional**—matriz de cadeias de caracteres

An array of `string`, which specifies which permissions the app requests, which let end users know how the extension does. The following options are non-exclusive:

* `identity`&emsp; Requer informações de identidade do usuário.
* `messageTeamMembers`&emsp; Requer permissão para enviar mensagens diretas aos membros da equipe.

Changing these permissions during app update, causes your users to repeat the consent process after they run the updated app. For more information, see [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md).

> [!NOTE]
> As permissões estão preteridas agora.

## <a name="devicepermissions"></a>devicePermissions

**Opcional**—matriz de cadeias de caracteres

Provides the native features on a user's device that your app requests access to. Options are:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Opcional**, exceto **Obrigatório** onde indicado.

Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do Teams. As listagens de domínio podem incluir curingas, por exemplo, `*.example.com`. O domínio válido corresponde exatamente a um segmento do domínio; se você precisar combinar `a.b.example.com`, use `*.*.example.com`. Se a sua configuração de guias ou interface do usuário de conteúdo navegar para qualquer outro domínio que não seja a configuração de guias, esse domínio deverá ser especificado aqui.

**Não** inclua os domínios dos provedores de identidade aos quais você deseja oferecer suporte em seu aplicativo. Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para accounts.google.com, no entanto, você não deve incluir accounts.google.com em `validDomains[]`.

Os aplicativos do Teams que exigem que suas próprias URLs do SharePoint funcionem bem incluem "{teamsitedomain}" em sua lista de domínios válida.

> [!IMPORTANT]
> Não adicione domínios que estão fora de seu controle, seja diretamente ou por meio de curingas. Por exemplo, `yourapp.onmicrosoft.com` é válido, no entanto, `*.onmicrosoft.com` não é válido.

O objeto é uma matriz com todos os elementos do tipo `string`.

## <a name="webapplicationinfo"></a>webApplicationInfo

**Opcional**—objeto

Forneça a ID do aplicativo do Microsoft Azure AD e as informações do Microsoft Graph para ajudar os usuários a entrarem facilmente no seu aplicativo. Se o seu aplicativo estiver registrado no Microsoft Azure Active Directory (Azure AD), você deverá fornecer a ID do aplicativo. Os administradores podem revisar facilmente as permissões e conceder consentimento no centro de administração do Teams.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|36 caracteres|✔️|ID do aplicativo do Microsoft Azure AD do aplicativo. Essa ID deve ser um GUID.|
|`resource`|string|2048 caracteres|✔️|URL de recurso do aplicativo para adquirir token de autenticação para SSO. </br> **NOTA:** Se você não estiver usando o SSO, insira um valor de cadeia de caracteres fictício nesse campo para o manifesto do aplicativo, por exemplo, `https://notapplicable` para evitar uma resposta de erro. |

## <a name="graphconnector"></a>graphConnector

**Opcional**—objeto

Especifique a configuração do conector de gráfico do aplicativo. Se isso estiver presente, [webApplicationInfo.id](#webapplicationinfo) também deverá ser especificado.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`notificationUrl`|string|2048 caracteres|✔️|A URL para a qual as notificações do conector do Graph para o aplicativo devem ser enviadas.|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Opcional**—booliano

Indicates if or not to show the loading indicator when an app or tab is loading. Default is **false**.
>[!NOTE]
>Se você selecionar `showLoadingIndicator` como true no manifesto do aplicativo, para carregar a página corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa conforme descrito em [Mostrar um documento de indicador de carregamento nativo](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator).

## <a name="isfullscreen"></a>isFullScreen

 **Opcional**—booliano

Indica se um aplicativo pessoal é renderizado sem uma barra de cabeçalho de guia (significando o modo de tela inteira). O padrão é **false**.

> [!NOTE]
>
> * `isFullScreen` funciona apenas para aplicativos publicados em sua organização. Aplicativos de terceiros transferidos por sideload e publicados não podem usar essa propriedade (ela é ignorada).
>
> * `isFullScreen=true` remove a barra de cabeçalho e o título fornecidos pelo Teams de aplicativos pessoais e das caixas de diálogo do módulo de tarefa.

## <a name="activities"></a>activities

**Opcional**—objeto

Defina as propriedades que o seu aplicativo usa para postar um feed de atividades do usuário..

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`activityTypes`|matriz de Objetos|128 itens| | Forneça os tipos de atividades que seu aplicativo pode postar no feed de atividades de um usuário.|

### <a name="activitiesactivitytypes"></a>activities.activityTypes

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`type`|string|32 caracteres|✔️|O tipo de notificação. *Confira a seguir*.|
|`description`|string|128 caracteres|✔️|A brief description of the notification. *See below*.|
|`templateText`|string|128 caracteres|✔️|Ex: "{actor} criou a tarefa {taskId} para você"|

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

## <a name="defaultinstallscope"></a>defaultInstallScope

Cadeia de caracteres - **opcional**.

Especifica o escopo de instalação definido para este aplicativo por padrão. O escopo definido será a opção exibida no botão quando um usuário tentar adicionar o aplicativo. As opções são:

* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a>defaultGroupCapability

**Opcional** - objeto

When a group install scope is selected, it will define the default capability when the user installs the app. Options are:

* `team`
* `groupchat`
* `meetings`

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`team`|string|||When the install scope selected is `team`, this field specifies the default capability available. Options: `tab`, `bot`, or `connector`.|
|`groupchat`|string|||When the install scope selected is `groupchat`, this field specifies the default capability available. Options: `tab`, `bot`, or `connector`.|
|`meetings`|string|||When the install scope selected is `meetings`, this field specifies the default capability available. Options: `tab`, `bot`, or `connector`.|

## <a name="configurableproperties"></a>configurableProperties

**Opcional** - matriz

O bloco `configurableProperties` define as propriedades do aplicativo que os administradores do Teams podem personalizar. Para obter mais informações, consulte [habilitar a personalização do aplicativo](~/concepts/design/enable-app-customization.md). O recurso de personalização do aplicativo não é compatível com aplicativos personalizados ou LOB.

> [!NOTE]
> Um mínimo de uma propriedade deve ser definido. Você pode definir um máximo de nove propriedades neste bloco.

Você pode definir qualquer uma das seguintes propriedades:

* [nome](#name): o nome de exibição do aplicativo.
* [shortDescription](#description): a breve descrição do aplicativo.
* [longDescription](#description): a descrição longa do aplicativo.
* [smallImageUrl](#icons): o ícone de estrutura de tópicos do aplicativo.
* [largeImageUrl](#icons): o ícone de cor do aplicativo.
* [accentColor](#accentcolor): a cor a ser usada e uma tela de fundo para seus ícones de estrutura de tópicos.
* [developerUrl](#developer): a URL HTTPS do site do desenvolvedor.
* [privacyUrl](#developer): a URL HTTPS da política de privacidade do desenvolvedor.
* [termsOfUseUrl](#developer): a URL HTTPS dos termos de uso do desenvolvedor.

## <a name="supportedchanneltypes"></a>supportedChannelTypes

**Opcional** - matriz

Habilita seu aplicativo em canais não-padronizados. Se seu aplicativo der suporte a um escopo de equipe e esta propriedade for definida, o Teams habilita seu aplicativo em cada tipo de canal adequadamente. Atualmente, há suporte para os tipos de canais privados e compartilhados.

> [!NOTE]
>
> * Se seu aplicativo der suporte a um escopo de equipe, ele funciona nos canais padrão independentemente dos valores que são definidos nesta propriedade.
> * Seu aplicativo pode levar em conta as propriedades únicas de cada um dos tipos de canal para funcionar corretamente. Para habilitar sua guia para canais privados e compartilhados, consulte [recuperar o contexto](~/tabs/how-to/access-teams-context.md#retrieve-context-in-private-channels) em canais privados e [obter contexto em canais compartilhados](../../tabs/how-to/access-teams-context.md#get-context-in-shared-channels)

## <a name="defaultblockuntiladminaction"></a>defaultBlockUntilAdminAction

**Opcional** - booliano

Quando a propriedade `defaultBlockUntilAdminAction` é definida como **true**, o aplicativo fica oculto dos usuários por padrão até que o administrador permita. Se definido como **true**, o aplicativo ficará oculto para todos os locatários e usuários finais. Os administradores de locatários podem ver o aplicativo no centro de administração do Teams e tomar medidas para permitir ou bloquear o aplicativo. O valor padrão é **falso**. Para obter mais informações sobre o bloco de aplicativo padrão, consulte [Bloquear aplicativos por padrão para usuários até que um administrador aprove](../../concepts/design/enable-app-customization.md#block-apps-by-default-for-users-until-an-admin-approves)

## <a name="publisherdocsurl"></a>publisherDocsUrl

Cadeia de caracteres - **opcional**.

**Tamanho máximo** - 128 caracteres

O `publisherDocsUrl` é uma URL HTTPS para uma página de informações para que os administradores obtenham diretrizes antes de permitir um aplicativo, que é bloqueado por padrão. Ele também pode ser usado para fornecer instruções ou informações sobre o aplicativo que podem ser úteis para o administrador do locatário.

## <a name="subscriptionoffer"></a>subscriptionOffer

**Opcional** - objeto

Especifica a oferta de SaaS associada ao seu aplicativo.

|Nome| Tipo|Tamanho máximo|Obrigatório|Descrição|
|---|---|---|---|---|
|`offerId`| string | 2,048 caracteres | ✔️ | A unique identifier that includes your Publisher ID and Offer ID, which you can find in [Partner Center](https://partner.microsoft.com/dashboard). You must format the string as `publisherId.offerId`.|

## <a name="meetingextensiondefinition"></a>meetingExtensionDefinition

**Opcional** - objeto

Specify meeting extension definition. For more information, see [custom Together Mode scenes in Teams](../../apps-in-teams-meetings/teams-together-mode.md).

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`scenes`|matriz de objetos| 5 itens||Cenas suportadas da reunião.|
|`supportsStreaming`|Booliano|||Um valor que indica se um aplicativo pode transmitir o conteúdo de áudio e vídeo da reunião para um ponto de extremidade de protocolo de reunião em tempo real (RTMP). O valor padrão é **falso**.|

### <a name="meetingextensiondefinitionscenes"></a>meetingExtensionDefinition.scenes

|Nome| Tipo|Tamanho máximo|Obrigatório |Descrição|
|---|---|---|---|---|
|`id`|||✔️| O identificador exclusivo para a cena. Essa ID deve ser um GUID. |
|`name`| string | 128 caracteres |✔️| O nome da cena. |
|`file`|||✔️| O caminho do arquivo relativo para o arquivo JSON de metadados das cenas. |
|`preview`|||✔️| O caminho do arquivo relativo para o ícone de visualização PNG das cenas. |
|`maxAudience`| inteiro | 50  |✔️| O número máximo de audiências suportadas na cena. |
|`seatsReservedForOrganizersOrPresenters`| inteiro | 50 |✔️| O número de assentos reservados para organizadores ou apresentadores.|

## <a name="authorization"></a>autorização

**Opcional** - objeto

> [!NOTE]
> If you set the `manifestVersion` property to 1.12, the authorization property is incompatible with the older versions (version 1.11 or earlier) of the manifest. Authorization is supported for manifest version 1.12.

Especifique e consolide as informações relacionadas à autorização para o aplicativo.

|Nome| Tipo|Tamanho máximo|Obrigatório |Descrição|
|---|---|---|---|---|
|`permissions`||||Lista de permissões que o aplicativo precisa para funcionar.|

### <a name="authorizationpermissions"></a>authorization.permissions

|Nome| Tipo|Tamanho máximo|Obrigatório |Descrição|
|---|---|---|---|---|
|`resourceSpecific`| matriz de objetos|16 itens||Permissões que protegem o acesso a dados no nível da instância do recurso.|

### <a name="authorizationpermissionsresourcespecific"></a>authorization.permissions.resourceSpecific

|Nome| Tipo|Tamanho máximo|Obrigatório |Descrição|
|---|---|---|---|---|
|`type`|string||✔️| The type of the resource-specific permission. Options: `Application` and `Delegated`.|
|`name`|string|128 caracteres|✔️|O nome da permissão específica do recurso. Para obter mais informações, consulte [Permissões de aplicativo específicas do recurso](#resource-specific-application-permissions) e [Permissões delegadas específicas do recurso](#resource-specific-delegated-permissions)|

#### <a name="resource-specific-application-permissions"></a>Permissões de aplicativo específicas do recurso

As permissões do aplicativo permitem que o aplicativo acesse dados sem um usuário conectado. Para obter informações sobre permissões de aplicativos, consulte [Consentimento específico de recursos para MS Graph e MS BotSDK](../../graph-api/rsc/resource-specific-consent.md).

#### <a name="resource-specific-delegated-permissions"></a>Permissões delegadas específicas do recurso

As permissões delegadas permitem que o aplicativo acesse dados em nome do usuário conectado.

* **Permissões delegadas específicas de recursos para equipes**

    |**Name**|**Descrição**|
    |---|---|
    |`ChannelMeetingParticipant.Read.Group`| Permite que o aplicativo leia as informações dos participantes, incluindo nome, função, ID, horários de ingresso e de saída, de reuniões de canal associadas a esta equipe, em nome do usuário conectado.|
    |`InAppPurchase.Allow.Group`| Permite que o aplicativo mostre ofertas do marketplace aos usuários nesta equipe e conclua suas compras dentro do aplicativo, em nome do usuário conectado.|
    |`ChannelMeetingStage.Write.Group`| Permite que o aplicativo mostre o conteúdo na janela de conteúdo compartilhado nas reuniões de canal associadas a essa equipe, em nome do usuário conectado.|
    |`LiveShareSession.ReadWrite.Group`|Permite que o aplicativo crie e sincronize sessões do Live Share para reuniões associadas a essa equipe e acesse informações relacionadas sobre a lista de participantes da reunião, como a função de reunião do membro, em nome do usuário conectado.|

* **Permissões delegadas específicas do recurso para chats ou reuniões**

    |**Name**|**Descrição**|
    |---|---|
    |`InAppPurchase.Allow.Chat`|Permite que o aplicativo mostre ofertas do marketplace aos usuários neste chat e em qualquer reunião associada e conclua suas compras dentro aplicativo, em nome do usuário conectado.|
    |`MeetingStage.Write.Chat`|Permite que o aplicativo mostre o conteúdo na janela de conteúdo compartilhado nas reuniões associadas a este chat, em nome do usuário conectado.|
    |`OnlineMeetingParticipant.Read.Chat`|Permite que o aplicativo leia as informações do participante, incluindo nome, função, ID, horários de ingresso e de saída, da reuniões associadas a este chat, em nome do usuário conectado.|
    |`OnlineMeetingParticipant.ToggleIncomingAudio.Chat`|Permite que o aplicativo alterne o áudio de entrada para participantes em reuniões associadas a este chat, em nome do usuário conectado.|
    |`LiveShareSession.ReadWrite.Chat`|Permite que o aplicativo crie e sincronize sessões do Live Share para reuniões associadas a esse chat e acesse informações relacionadas sobre a lista de participantes da reunião, como a função de reunião do membro, em nome do usuário conectado.|
   |`OnlineMeetingIncomingAudio.Detect.Chat`|Permite que o aplicativo detecte alterações no status do áudio de entrada em reuniões associadas a esse chat, em nome do usuário conectado.|

* **Permissões delegadas específicas do recurso para usuários**

    |**Name**|**Descrição**|
    |---|---|
    |`InAppPurchase.Allow.User`|Permite que o aplicativo mostrar as ofertas do marketplace do usuário e conclua as compras do usuário dentro do aplicativo, em nome do usuário conectado.|

## <a name="create-a-manifest-file"></a>Criar um arquivo de manifesto

Se seu aplicativo não tem um arquivo de manifesto do aplicativo Teams, você precisará criá-lo.

Para criar um arquivo de manifesto do aplicativo Teams:

1. Use a [amostra do esquema de manifesto](#sample-full-manifest) para criar um arquivo .json.
1. Salve-o na raiz da pasta do seu projeto como `manifest.json`.

<br>
<details>
<summary>Aqui está um exemplo de uma amostra de esquema de manifesto para um aplicativo de guia com o logon único habilitado:</summary>
<br>

> [!NOTE]
> O conteúdo de exemplo de manifesto mostrado aqui é apenas para um aplicativo de guia. Ele usa valores de exemplo para a URI do domínio terciário e o nome do pacote. Para obter mais informações, confira [amostra do esquema de manifesto](#sample-full-manifest).

  ```json
{ 
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json", 
 "manifestVersion": "1.12", 
 "version": "1.0.0", 
 "id": "{new GUID for this Teams app - not the Azure AD App ID}", 
 "packageName": "com.contoso.teamsauthsso", 
 "developer": { 
 "name": "Microsoft", 
 "websiteUrl": "https://www.microsoft.com", 
 "privacyUrl": "https://www.microsoft.com/privacy", 
 "termsOfUseUrl": "https://www.microsoft.com/termsofuse" 
  }, 

  "name": { 
    "short": "Teams Auth SSO", 
    "full": "Teams Auth SSO" 
  }, 


  "description": { 
    "short": "Teams Auth SSO app", 
    "full": "The Teams Auth SSO app" 
  }, 

  "icons": { 
    "outline": "outline.png", 
    "color": "color.png" 
  }, 

  "accentColor": "#60A18E", 
  "staticTabs": [ 
    { 
     "entityId": "auth", 
     "name": "Auth", 
     "contentUrl": "https://https://subdomain.example.com/Home/Index", 
     "scopes": [ "personal" ] 
    } 
  ], 

  "configurableTabs": [ 
    { 
     "configurationUrl": "https://subdomain.example.com/Home/Configure", 
     "canUpdateConfiguration": true, 
     "scopes": [ 
     "team" 
      ] 
    } 
  ], 
  "permissions": [ "identity", "messageTeamMembers" ], 
  "validDomains": [ 
   "{subdomain or ngrok url}" 
  ], 
  "webApplicationInfo": { 
    "id": "{Azure AD AppId}", 
    "resource": "api://subdomain.example.com/{Azure AD AppId}" 
  }
} 
```

</details>

## <a name="see-also"></a>Confira também

* [Compreender a estrutura do aplicativo Microsoft Teams](~/concepts/design/app-structure.md)
* [Habilitar personalização de aplicativo](~/concepts/design/enable-app-customization.md)
* [Localizar o aplicativo](~/concepts/build-and-test/apps-localization.md)
* [Integrar recursos de mídia](~/concepts/device-capabilities/media-capabilities.md)
* [Esquema do manifesto de visualização pública do desenvolvedor para o Microsoft Teams](manifest-schema-dev-preview.md)
