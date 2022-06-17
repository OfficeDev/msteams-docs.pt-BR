---
title: Referência de esquema de manifesto
description: Neste artigo, você terá o esquema de manifesto para referência, esquema e manifesto completo de exemplo do Microsoft Teams.
ms.topic: reference
ms.localizationpriority: high
ms.openlocfilehash: 49b3b1714d05f50ee6a4b186ff7a1a85d6209083
ms.sourcegitcommit: b4986bf529c74444db67b7ce522b3b0d2c2a8e28
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66130505"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referência: esquema de manifesto para o Microsoft Teams

O manifesto do aplicativo Microsoft Teams descreve como seu aplicativo se integra ao produto Microsoft Teams. O manifesto do seu aplicativo deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json). As versões anteriores 1.0, 1.1,...,1.12 e a versão 1.13 atual (veja a nota abaixo) são suportadas (usando "v1.x" no URL).
Para obter mais informações sobre as alterações feitas em cada versão, consulte o [registro de alterações do manifesto](https://github.com/OfficeDev/microsoft-teams-app-schema/releases).

A tabela a seguir lista as versões do TeamsJS e do manifesto do aplicativo de acordo com diferentes cenários de aplicativo:

[!INCLUDE [pre-release-label](~/includes/teamjs-version-details.md)]

A amostra do esquema a seguir mostra todas as opções de extensibilidade:

## <a name="sample-full-manifest"></a>Amostra de manifesto completo

```json
{
    "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json",
    "manifestVersion": "1.13",
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
                    "fetchTask": true,
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

## <a name="id"></a>id

**Obrigatório**—ID do aplicativo da Microsoft

A ID é um identificador exclusivo gerado pela Microsoft para o aplicativo. Você tem uma ID se seu bot estiver registrado por meio do Microsoft Bot Framework. Você tem uma ID se o aplicativo web da sua guia já entrar com a Microsoft. Você deve inserir a ID aqui. Caso contrário, você deverá gerar uma nova ID no [Portal de Registro de Aplicativos da Microsoft](https://aka.ms/appregistrations). Use a mesma ID se você adicionar um bot.

> [!NOTE]
> Se você estiver enviando uma atualização para o seu aplicativo existente no AppSource, a ID em seu manifesto não deve ser modificada.

## <a name="developer"></a>developer

**Obrigatório**—objeto

Especifica informações sobre a sua empresa. Para aplicativos enviados à loja do Teams, esses valores devem corresponder às informações na listagem da loja. Para obter mais informações, consulte as [Diretrizes de publicação da loja do Teams](~/concepts/deploy-and-publish/appsource/publish.md).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`name`|32 caracteres|✔|O nome de exibição do desenvolvedor.|
|`websiteUrl`|2048 caracteres|✔|A URL https:// para o site do desenvolvedor. Esse link deve levar os usuários à página de destino específica da sua empresa ou do produto.|
|`privacyUrl`|2048 caracteres|✔|A URL https:// para a política de privacidade do desenvolvedor.|
|`termsOfUseUrl`|2048 caracteres|✔|A URL https:// para os termos de uso do desenvolvedor.|
|`mpnId`|10 caracteres| |**Opcional** A ID do Microsoft Partner Network que identifica a organização parceira criadora do aplicativo.|

## <a name="name"></a>nome

**Obrigatório**—objeto

O nome da sua experiência de aplicativo, exibido aos usuários na experiência do Teams. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações na entrada do AppSource. Os valores de `short` e `full` devem ser diferentes.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|30 caracteres|✔|O nome de exibição curto para o aplicativo.|
|`full`|100 caracteres||O nome completo do aplicativo, utilizado se o nome completo do aplicativo exceder 30 caracteres.|

## <a name="description"></a>descrição

**Obrigatório**—objeto

Descreve o seu aplicativo para os usuários. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações na entrada do AppSource.

Certifique-se de que a sua descrição detalhe a sua experiência e ajude os clientes em potencial a entender o que sua experiência faz. Você deve anotar na descrição completa, se uma conta externa for necessária para uso. Os valores de `short` e `full` devem ser diferentes. A sua descrição curta não pode ser repetida na descrição longa e não deve incluir nenhum outro nome de aplicativo.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|80 caracteres|✔|Uma descrição curta da experiência do seu aplicativo, usada quando o espaço é limitado.|
|`full`|4000 caracteres|✔|A descrição completa do seu aplicativo.|

## <a name="packagename"></a>packageName

Cadeia de caracteres—**opcional**

Um identificador exclusivo para o aplicativo em notação de domínio reverso; por exemplo, com.example.myapp. Comprimento máximo: 64 caracteres.

## <a name="localizationinfo"></a>localizationInfo

**Opcional**—objeto

Permite a especificação de um idioma padrão e fornece ponteiros para mais arquivos de idioma. Para obter mais informações, consulte [localização](~/concepts/build-and-test/apps-localization.md).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`defaultLanguageTag`||✔|A marca de idioma das cadeia de caracteres neste arquivo de manifesto de nível superior.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Uma matriz de objetos especificando mais traduções de idiomas.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`languageTag`||✔|A marca de idioma das cadeias de caracteres no arquivo fornecido.|
|`file`||✔|Um caminho de arquivo relativo para o arquivo .json que contém as cadeias de caracteres traduzidas.|

## <a name="icons"></a>ícones

**Obrigatório**—objeto

Ícones usados no aplicativo Teams. Os arquivos de ícone devem ser incluídos como parte do pacote de upload. Para obter mais informações, consulte [Ícones](../../concepts/build-and-test/apps-package.md#app-icons).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`outline`|32 x 32 pixels|✔|Um caminho de arquivo relativo para um ícone de contorno PNG transparente de 32x32.|
|`color`|192 x 192 pixels|✔|Um caminho de arquivo relativo para um ícone PNG colorido de 192x192.|

## <a name="accentcolor"></a>accentColor

**Obrigatório**—Código de cores HTML hexadecimal

Uma cor para usar e como plano de fundo para os seus ícones de contorno.

O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee`.

## <a name="configurabletabs"></a>configurbleTabs

**Opcional**—matriz

Usado quando a sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada. As guias configuráveis são compatíveis apenas nos escopos `team` e `groupchat`, sendo que você pode configurar as mesmas guias várias vezes. No entanto, você pode defini-la no manifesto apenas uma vez.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔|A URL https:// a ser usada ao configurar a guia.|
|`scopes`|matriz de enumerações|1|✔|Atualmente, as guias configuráveis são compatíveis apenas com os escopos `team` e `groupchat`. |
|`canUpdateConfiguration`|Booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Padrão: **true**.|
|`context` |matriz de enumerações|6 ||O conjunto de `contextItem` escopos em que uma [guia é compatível](../../tabs/how-to/access-teams-context.md). Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|string|2048||Um caminho de arquivo relativo para uma imagem de visualização de guia para uso no SharePoint. Tamanho 1024x768. |
|`supportedSharePointHosts`|matriz de enumerações|1||Define como sua guia é disponibilizada no SharePoint. As opções são `sharePointFullPage` e `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Opcional**—matriz

Define um conjunto de guias que podem ser "fixadas" por padrão, sem que o usuário as adicione manualmente. As guias estáticas declaradas no escopo `personal` são sempre vinculadas à experiência pessoal do aplicativo. As guias estáticas declaradas no escopo `team` não são suportadas no momento.

Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object`. Esse bloco é necessário apenas para soluções que fornecem uma solução de guia estática.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|string|64 caracteres|✔|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|string|128 caracteres|✔|O nome de exibição da guia na interface de canal.|
|`contentUrl`|string||✔|A URL https:// que aponta para a interface do usuário da entidade a ser exibida na tela do Teams.|
|`websiteUrl`|string|||A URL https:// para apontar se um usuário optar por visualizar em um navegador.|
|`searchUrl`|string|||A URL https:// para apontar para as consultas de pesquisa de um usuário.|
|`scopes`|matriz de enumerações|1|✔|Atualmente, as guias estáticas oferecem suporte apenas ao escopo `personal`, o que significa que elas podem ser provisionadas apenas como parte da experiência pessoal.|
|`context` | matriz de enumerações| 2|| O conjunto de `contextItem` escopos em que uma guia é compatível.|

> [!NOTE]
> O recurso searchUrl não está disponível para desenvolvedores de terceiros. Se as suas guias exigirem informações dependentes do contexto para exibir conteúdo relevante ou para iniciar um fluxo de autenticação, para obter mais informações, consulte [Obter contexto para sua guia do Microsoft Teams](../../tabs/how-to/access-teams-context.md).

## <a name="bots"></a>bots

**Opcional**—matriz

Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.

O item é uma matriz (máximo de apenas um elemento &mdash;, atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object`. Esse bloco é necessário apenas para soluções que fornecem uma experiência de bot.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64 caracteres|✔|O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. A ID pode ser igual a [ID do aplicativo](#id) geral.|
|`scopes`|matriz de enumerações|3|✔|Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`). Essas opções são não exclusivas.|
|`needsChannelSelector`|Booliano|||Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico. Padrão: **`false`**|
|`isNotificationOnly`|Booliano|||Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa. Padrão: **`false`**|
|`supportsFiles`|Booliano|||Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal. Padrão: **`false`**|
|`supportsCalling`|Booliano|||Um valor que indica onde um bot dá suporte a chamadas de áudio. **IMPORTANTE**: Esta propriedade é experimental no momento. As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.  A propriedade é fornecida apenas para fins de teste e exploração e não deve ser usada em aplicativos de produção. Padrão: **`false`**|
|`supportsVideo`|Booliano|||Um valor que indica onde um bot oferece suporte a chamadas com vídeo. **IMPORTANTE**: Esta propriedade é experimental no momento. As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.  A propriedade é fornecida apenas para fins de teste e exploração e não deve ser usada em aplicativos de produção. Padrão: **`false`**|

### <a name="botscommandlists"></a>bots.commandLists

Uma lista opcional de comandos que seu bot pode recomendar aos usuários. O objeto é uma matriz (máximo de dois elementos) com todos os elementos do tipo `object`; você deve definir uma lista de comandos separada para cada escopo que o seu bot oferece suporte. Para obter mais informações, confira [Menus de bot](~/bots/how-to/create-a-bot-commands-menu.md).

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de enumerações|3|✔|Especifica o escopo para o qual a lista de comandos é válida. As opções são `team`, `personal` e `groupchat`.|
|`items.commands`|matriz de objetos|10 |✔|Uma matriz de comandos que o bot suporta:<br>`title`: o nome do comando bot (cadeia, 32)<br>`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)|

### <a name="botscommandlistscommands"></a>bots.commandLists.commands

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|title|string|12 |✔|O nome do comando do bot.|
|description|string|128 caracteres|✔|Uma descrição de texto simples ou um exemplo da sintaxe do comando e seus argumentos.|

## <a name="connectors"></a>conectores

**Opcional**—matriz

O bloco `connectors` define um conector do Office 365 para o aplicativo.

O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo `object`. Este bloco é necessário apenas para soluções que fornecem um Conector.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔|A URL https:// a ser usada ao configurar o conector.|
|`scopes`|matriz de enumerações|1|✔|Especifica se o Conector oferece uma experiência no contexto de um canal em um `team`, ou uma experiência com escopo apenas para um usuário individual (`personal`). Atualmente, somente o escopo `team` é compatível.|
|`connectorId`|string|64 caracteres|✔|Um identificador exclusivo para o Conector que corresponde a sua ID no [Painel do Desenvolvedor de Conectores](https://aka.ms/connectorsdashboard).|

## <a name="composeextensions"></a>composeExtensions

**Opcional**—matriz

Define uma extensão de mensagens para o aplicativo.

> [!NOTE]
> O nome do recurso foi alterado de "extensão de texto " para "extensão de mensagem" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem funcionando.

O item é uma matriz (máximo de um elemento) com todos os elementos do tipo `object`. Este bloco é necessário apenas para soluções que fornecem uma extensão de mensagens.

|Nome| Tipo | Tamanho Máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64|✔|A ID exclusiva do aplicativo da Microsoft para o bot que oferece suporte à extensão de mensagens, conforme registrado no Bot Framework. A ID pode ser igual à ID geral do aplicativo.|
|`commands`|matriz de objetos|10 |✔|Matriz de comandos com suporte da extensão de mensagens.|
|`canUpdateConfiguration`|Booliano|||Um valor que indica se a configuração de uma extensão do sistema de mensagens pode ser atualizada pelo usuário. Padrão: **false**.|
|`messageHandlers`|matriz de Objetos|5||Uma lista de manipuladores que permitem que aplicativos sejam invocados quando determinadas condições são atendidas.|
|`messageHandlers.type`|string|||O tipo de manipulador de mensagens. Deve ser `"link"`.|
|`messageHandlers.value.domains`|matriz de Cadeias de Caracteres|||Matriz de domínios para os quais o manipulador de mensagens de link pode se registrar.|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Sua extensão de mensagens deve declarar um ou mais comandos com no máximo 10 comandos. Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário.

Cada item de comando é um objeto com a seguinte estrutura:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|64 caracteres|✔|A ID do comando.|
|`title`|string|32 caracteres|✔|O nome do comando amigável.|
|`type`|string|64 caracteres||O tipo do comando. Um de `query` ou `action`. Padrão: **consulta**.|
|`description`|string|128 caracteres||A descrição que aparece para os usuários para indicar a finalidade deste comando.|
|`initialRun`|Booliano|||Um valor booleano indica se o comando é executado inicialmente sem parâmetros. O padrão é **false**.|
|`context`|matriz de Cadeias de Caracteres|3||Define de onde a extensão da mensagem pode ser invocada. Qualquer combinação de `compose`,`commandBox`,`message`. O padrão é `["compose","commandBox"]`.|
|`fetchTask`|Booliano|||Um valor booleano que indica se deve buscar o módulo de tarefa dinamicamente. O padrão é **false**.|
|`taskInfo`|objeto|||Especifique o módulo de tarefa para pré-carregar ao usar um comando de extensão do sistema de mensagens.|
|`taskInfo.title`|string|64 caracteres||Título inicial da caixa de diálogo.|
|`taskInfo.width`|string|||Largura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.height`|string|||Altura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.url`|string|||URL inicial da webview.|
|`parameters`|matriz de objeto|5 itens|✔|A lista de parâmetros que o comando usa. Mínimo: 1; máximo: 5.|
|`parameters.name`|string|64 caracteres|✔|O nome do parâmetro como ele aparece no cliente. O nome do parâmetro está incluído na solicitação do usuário.|
|`parameters.title`|string|32 caracteres|✔|Título amigável para o parâmetro.|
|`parameters.description`|string|128 caracteres||Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.|
|`parameters.value`|string|512 caracteres||Valor inicial para o parâmetro. Atualmente o valor não é suportado|
|`parameters.inputType`|string|128 caracteres||Define o tipo de controle exibido em um módulo de tarefa para`fetchTask: true`. Um de `text, textarea, number, date, time, toggle, choiceset`.|
|`parameters.choices`|matriz de objetos|10 itens||As opções de escolha para `choiceset`. Use apenas quando `parameter.inputType` for `choiceset`.|
|`parameters.choices.title`|string|128 caracteres|✔|Títulor da escolha.|
|`parameters.choices.value`|string|512 caracteres|✔|O valor da escolha.|

## <a name="permissions"></a>permissões

**Opcional**—matriz de cadeias de caracteres

Uma matriz de `string`, que especifica quais permissões o aplicativo solicita, que permite que os usuários finais saibam como a extensão funciona. As seguintes opções não são exclusivas:

* `identity`&emsp; Requer informações de identidade do usuário.
* `messageTeamMembers`&emsp; Requer permissão para enviar mensagens diretas aos membros da equipe.

Alterar essas permissões durante a atualização do aplicativo faz com que seus usuários repitam o processo de consentimento depois de executar o aplicativo atualizado. Para saber mais, veja [atualizando seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md).

> [!NOTE]
> As permissões estão preteridas agora.

## <a name="devicepermissions"></a>devicePermissions

**Opcional**—matriz de cadeias de caracteres

Fornece os recursos nativos no dispositivo de um usuário aos quais o seu aplicativo solicita acesso. As opções são:

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
|`id`|string|36 caracteres|✔|ID do aplicativo do Microsoft Azure AD do aplicativo. Essa ID deve ser um GUID.|
|`resource`|string|2048 caracteres|✔|URL de recurso do aplicativo para adquirir token de autenticação para SSO. </br> **OBSERVAÇÃO:** Se você não estiver usando SSO, certifique-se de inserir um valor de cadeia de caracteres fictício nesse campo para o manifesto do aplicativo, por exemplo, <https://notapplicable> para evitar uma resposta de erro. |

## <a name="graphconnector"></a>graphConnector

**Opcional**—objeto

Especifique a configuração do conector de gráfico do aplicativo. Se estiver presente, [webApplicationInfo.id](#webapplicationinfo) também deve ser especificado.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`notificationUrl`|string|2048 caracteres|✔|A URL para a qual as notificações do conector do Graph para o aplicativo devem ser enviadas.|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Opcional**—booliano

Indica se deve ou não mostrar o indicador de carregamento quando um aplicativo ou guia está carregando. O padrão é **false**.
>[!NOTE]
>Se você selecionar `showLoadingIndicator` como true no manifesto do aplicativo, para carregar a página corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa conforme descrito em [Mostrar um documento de indicador de carregamento nativo](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator).

## <a name="isfullscreen"></a>isFullScreen

 **Opcional**—booliano

Indica se um aplicativo pessoal é renderizado sem uma barra de cabeçalho de guia (significando o modo de tela inteira). O padrão é **false**.

> [!NOTE]
> `isFullScreen` funciona apenas para aplicativos publicados em sua organização.

## <a name="activities"></a>activities

**Opcional**—objeto

Defina as propriedades que o seu aplicativo usa para postar um feed de atividades do usuário..

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`activityTypes`|matriz de Objetos|128 itens| | Forneça os tipos de atividades que seu aplicativo pode postar no feed de atividades de um usuário.|

### <a name="activitiesactivitytypes"></a>activities.activityTypes

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`type`|string|32 caracteres|✔|O tipo de notificação. *Confira a seguir*.|
|`description`|string|128 caracteres|✔|Uma breve descrição da notificação. *Veja abaixo*.|
|`templateText`|string|128 caracteres|✔|Ex: "{actor} criou a tarefa {taskId} para você"|

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

Quando um escopo de instalação de grupo é selecionado, ele definirá o recurso padrão quando o usuário instalar o aplicativo. As opções são:

* `team`
* `groupchat`
* `meetings`

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`team`|string|||Quando o escopo de instalação selecionado é `team`, este campo especifica o recurso padrão disponível. Opções: `tab`, `bot`ou `connector`.|
|`groupchat`|string|||Quando o escopo de instalação selecionado é `groupchat`, este campo especifica o recurso padrão disponível. Opções: `tab`, `bot`ou `connector`.|
|`meetings`|cadeia de caracteres|||Quando o escopo de instalação selecionado é `meetings`, este campo especifica o recurso padrão disponível. Opções: `tab`, `bot`ou `connector`.|

## <a name="configurableproperties"></a>configurableProperties

**Opcional** - matriz

O bloco `configurableProperties` define as propriedades do aplicativo que os administradores do Teams podem personalizar. Para obter mais informações, consulte [habilitar a personalização do aplicativo](~/concepts/design/enable-app-customization.md). O recurso de personalização do aplicativo não é compatível com aplicativos personalizados ou LOB.

> [!NOTE]
> Um mínimo de uma propriedade deve ser definido. Você pode definir um máximo de nove propriedades neste bloco.

Você pode definir qualquer uma das seguintes propriedades:

* `name`: O nome de exibição do aplicativo.
* `shortDescription`: A breve descrição do aplicativo.
* `longDescription`: A descrição longa do aplicativo.
* `smallImageUrl`: O ícone de contorno do aplicativo.
* `largeImageUrl`: O ícone de cor do aplicativo.
* `accentColor`: A cor a ser usada e um plano de fundo para seus ícones de contorno.
* `developerUrl`: A URL HTTPS do site do desenvolvedor.
* `privacyUrl`: A URL HTTPS da política de privacidade do desenvolvedor.
* `termsOfUseUrl`: A URL HTTPS dos termos de uso do desenvolvedor.

## <a name="defaultblockuntiladminaction"></a>defaultBlockUntilAdminAction

**Opcional**—booliano

Quando a propriedade `defaultBlockUntilAdminAction` é definida como **true**, o aplicativo fica oculto dos usuários por padrão até que o administrador permita. Se definido como **true**, o aplicativo ficará oculto para todos os locatários e usuários finais. Os administradores de locatários podem ver o aplicativo no centro de administração do Teams e tomar medidas para permitir ou bloquear o aplicativo. O valor padrão é **falso**. Para obter mais informações sobre o bloqueio de aplicativos padrão, consulte [Ocultar o aplicativo Teams até a aprovação pelo administrador](~/concepts/design/enable-app-customization.md#hide-teams-app-until-admin-approves).

## <a name="publisherdocsurl"></a>publisherDocsUrl

Cadeia de caracteres - **opcional**.

**Tamanho máximo** - 128 caracteres

O `publisherDocsUrl` é uma URL HTTPS para uma página de informações para que os administradores obtenham diretrizes antes de permitir um aplicativo, que é bloqueado por padrão. Ele também pode ser usado para fornecer instruções ou informações sobre o aplicativo que podem ser úteis para o administrador do locatário.

## <a name="subscriptionoffer"></a>subscriptionOffer

**Opcional** - objeto

Especifica a oferta de SaaS associada ao seu aplicativo.

|Nome| Tipo|Tamanho máximo|Obrigatório|Descrição|
|---|---|---|---|---|
|`offerId`| string | 2,048 caracteres | ✔ | Um identificador exclusivo que inclui a sua ID de editor e ID de oferta, que você pode encontrar no [Partner Center](https://partner.microsoft.com/dashboard). Você deve formatar a cadeia de caracteres como `publisherId.offerId`.|

## <a name="meetingextensiondefinition"></a>meetingExtensionDefinition

**Opcional** - objeto

Para obter mais informações, consulte [cenas personalizadas do Modo Juntos no Teams](../../apps-in-teams-meetings/teams-together-mode.md).

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`scenes`|matriz de objetos| 5 itens||Cenas suportadas da reunião.|

### <a name="meetingextensiondefinitionscenes"></a>meetingExtensionDefinition.scenes

|Nome| Tipo|Tamanho máximo|Obrigatório |Descrição|
|---|---|---|---|---|
|`id`|||✔| O identificador exclusivo para a cena. Essa ID deve ser um GUID. |
|`name`| string | 128 caracteres |✔| O nome da cena. |
|`file`|||✔| O caminho do arquivo relativo para o arquivo JSON de metadados das cenas. |
|`preview`|||✔| O caminho do arquivo relativo para o ícone de visualização PNG das cenas. |
|`maxAudience`| inteiro | 50  |✔| O número máximo de audiências suportadas na cena. |
|`seatsReservedForOrganizersOrPresenters`| inteiro | 50 |✔| O número de assentos reservados para organizadores ou apresentadores.|

## <a name="authorization"></a>autorização

**Opcional** - objeto

> [!NOTE]
> Se você definir a propriedade `manifestVersion` como 1.12, a propriedade de autorização será incompatível com as versões mais antigas (versão 1.11 ou anterior) do manifesto. A autorização é suportada pela versão 1.12 do manifesto.

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
|`type`|string||✔| O tipo da permissão específica do recurso. Opções: `Application` e `Delegated`.|
|`name`|string|128 caracteres|✔|O nome da permissão específica do recurso. Para obter mais informações, consulte [Permissões de aplicativo específicas do recurso](#resource-specific-application-permissions) e [Permissões delegadas específicas do recurso](#resource-specific-delegated-permissions)|

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

* **Permissões delegadas específicas do recurso para chats ou reuniões**

    |**Name**|**Descrição**|
    |---|---|
    |`InAppPurchase.Allow.Chat`|Permite que o aplicativo mostre ofertas do marketplace aos usuários neste chat e em qualquer reunião associada e conclua suas compras dentro aplicativo, em nome do usuário conectado.|
    |`MeetingStage.Write.Chat`|Permite que o aplicativo mostre o conteúdo na janela de conteúdo compartilhado nas reuniões associadas a este chat, em nome do usuário conectado.|
    |`OnlineMeetingParticipant.Read.Chat`|Permite que o aplicativo leia as informações do participante, incluindo nome, função, ID, horários de ingresso e de saída, da reuniões associadas a este chat, em nome do usuário conectado.|
    |`OnlineMeetingParticipant.ToggleIncomingAudio.Chat`|Permite que o aplicativo alterne o áudio de entrada para participantes em reuniões associadas a este chat, em nome do usuário conectado.|

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
