---
title: Referência do esquema de manifesto do Developer Preview público
description: Arquivo de manifesto de exemplo e descrição de todos os seus componentes com suporte para o Microsoft Teams
ms.topic: reference
keywords: Developer Preview do esquema de manifesto do Teams
ms.localizationpriority: medium
ms.date: 11/15/2021
ms.openlocfilehash: 82f1a4fd9a51089069d1f8ed40d5e169f49b62c7
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757490"
---
# <a name="reference-public-developer-preview-manifest-schema-for-microsoft-teams"></a>Referência: esquema do manifesto do Developer Preview público para o Microsoft Teams

Para obter informações sobre como habilitar o Developer Preview, confira [Developer Preview público para Microsoft Teams](~/resources/dev-preview/developer-preview-intro.md).

> [!NOTE]
> Se você não estiver usando recursos do Developer Preview, incluindo a execução de [guias pessoais e extensões de mensagem do Teams no Outlook e no Office](../../m365-apps/overview.md), use o [manifesto do aplicativo para recursos de GA](~/resources/schema/manifest-schema.md).

O manifesto do Microsoft Teams descreve como o aplicativo se integra à plataforma do Microsoft Teams. O seu manifesto deve estar em conformidade com o esquema hospedado em [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).

## <a name="sample-full-manifest"></a>Amostra de manifesto completo

```json
{
    "$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion": "devPreview",
    "version": "1.0.0",
    "id": "%MICROSOFT-APP-ID%",
    "packageName": "com.example.myapp",
    "devicePermissions": [
        "geolocation",
        "media"
    ],
    "developer": {
        "name": "Publisher Name",
        "websiteUrl": "https://website.com/",
        "privacyUrl": "https://website.com/privacy",
        "termsOfUseUrl": "https://website.com/app-tos",
        "mpnId": "1234567890"
    },
    "localizationInfo": {
        "defaultLanguageTag": "es-es",
        "additionalLanguages": [
            {
                "languageTag": "en-us",
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
            "scopes": [
                "team",
                "groupchat"
            ]"context": []
        }
    ],
    "staticTabs": [
        {
            "entityId": "idForPage",
            "name": "Display name of tab",
            "contentUrl": "https://contoso.com/content?host=msteams",
            "contentBotId": "Specifies to the app that tab is an Adaptive Card Tab. You can either provide the contentBotId or contentUrl.",
            "websiteUrl": "https://contoso.com/content",
            "scopes": [
                "personal"
            ]
        }
    ],
    "bots": [
        {
            "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
            "needsChannelSelector": false,
            "isNotificationOnly": false,
            "scopes": [
                "team",
                "personal",
                "groupchat"
            ],
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
                            "title": "Command N",
                            "description": "Description of Command N"
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
            "configurationUrl": "https://contoso.com/teamsconnector/configure",
            "scopes": [
                "team"
            ]
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
                    "type": "search",
                    "context": [
                        "compose",
                        "commandBox"
                    ],
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
                    "type": "action",
                    "fetchTask": true,
                    "context": [
                        "message"
                    ],
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
                    "id": "exampleMessageHandler",
                    "title": "Message Handler",
                    "description": "Domains that will create a preview when pasted into the compose box",
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
    "defaultInstallScope": "meetings",
    "defaultGroupCapability": {
        "meetings": "tab",
        "team": "bot",
        "groupchat": "bot"
    },
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

*Opcional, mas recomendado* &ndash; Cadeia de caracteres

A URL `https://` referenciando o esquema JSON para o manifesto.

## <a name="manifestversion"></a>manifestVersion

**Obrigatório** &ndash; Cadeia de caracteres

A versão do esquema do manifesto que este manifesto está usando.

## <a name="version"></a>versão

**Obrigatório** &ndash; Cadeia de caracteres

A versão do aplicativo específico. Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada. Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade. Se esse aplicativo tiver sido enviado para a loja, o novo manifesto precisará ser enviado novamente e validado novamente. Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, depois que ele for aprovado.

Se as permissões solicitadas do aplicativo mudarem, os usuários serão solicitados a atualizar e concordar novamente com o aplicativo.

Esta cadeia de caracteres da versão deve seguir o padrão [semver](http://semver.org/) (MAJOR.MINOR.PATCH).

## <a name="id"></a>id

**Obrigatório** &ndash; ID do aplicativo da Microsoft

O identificador exclusivo gerado pela Microsoft para esse aplicativo. Se você registrou um bot por meio do Microsoft Bot Framework ou o aplicativo Web da guia já entra com a Microsoft, você já deve ter uma ID e deve inseri-la aqui. Caso contrário, você deve gerar uma nova ID no Portal de Registro de Aplicativos da [Microsoft (Meus](https://apps.dev.microsoft.com) Aplicativos), inseri-la aqui e reutilizá-la quando [adicionar um bot](~/bots/how-to/create-a-bot-for-teams.md).

## <a name="packagename"></a>packageName

**Obrigatório** &ndash; Cadeia de caracteres

Um identificador exclusivo para esse aplicativo em notação de domínio reverso, por exemplo, com.example.myapp.

## <a name="developer"></a>developer

Obrigatório:

Especifica informações sobre a sua empresa. Para aplicativos enviados ao AppSource (anteriormente Office Store), esses valores devem corresponder às informações na entrada do AppSource.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`name`|32 caracteres|✔|O nome de exibição do desenvolvedor.|
|`websiteUrl`|2048 caracteres|✔|A URL https:// para o site do desenvolvedor. Esse link deve levar os usuários à página de aterrissagem específica da sua empresa ou do produto.|
|`privacyUrl`|2048 caracteres|✔|A URL https:// para a política de privacidade do desenvolvedor.|
|`termsOfUseUrl`|2048 caracteres|✔|A URL https:// para os termos de uso do desenvolvedor.|
|`mpnId`|10 caracteres|✔|**Opcional** A ID do Microsoft Partner Network que identifica a organização parceira criadora do aplicativo.|

## <a name="localizationinfo"></a>localizationInfo

Opcional:

Permite a especificação de um idioma padrão e ponteiros para arquivos de idioma adicionais. Consulte a [localização](~/concepts/build-and-test/apps-localization.md).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`defaultLanguageTag`|4 caracteres|✔|A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Uma matriz de objetos especificando traduções de idiomas adicionais.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`languageTag`|4 caracteres|✔|A marca de idioma das cadeias de caracteres no arquivo fornecido.|
|`file`|4 caracteres|✔|Um caminho de arquivo relativo para o arquivo .json que contém as cadeias de caracteres traduzidas.|

## <a name="name"></a>nome

Obrigatório:

O nome da sua experiência de aplicativo, exibido aos usuários na experiência do Teams. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações na entrada do AppSource. Os valores de `short` e `full` não devem ser os mesmos.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|30 caracteres|✔|O nome de exibição curto para o aplicativo.|
|`full`|100 caracteres||O nome completo do aplicativo, utilizado se o nome completo do aplicativo exceder 30 caracteres.|

## <a name="description"></a>descrição

Obrigatório:

Descreve o seu aplicativo para os usuários. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações na entrada do AppSource.

Certifique-se de que a sua descrição detalhe corretamente a sua experiência e forneça informações para ajudar clientes em potencial a entender o que sua experiência faz. Você também deve observar, na descrição completa, se uma conta externa é necessária para uso. Os valores de `short` e `full` não devem ser os mesmos.  A sua descrição curta não deve ser repetida na descrição longa e não deve incluir nenhum outro nome de aplicativo.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|80 caracteres|✔|Uma descrição curta da experiência do seu aplicativo, usada quando o espaço é limitado.|
|`full`|4000 caracteres|✔|A descrição completa do seu aplicativo.|

## <a name="icons"></a>ícones

Obrigatório:

Ícones usados no aplicativo Teams. Os arquivos de ícone devem ser incluídos como parte do pacote de upload.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`outline`|2048 caracteres|✔|Um caminho de arquivo relativo para um ícone de contorno PNG transparente de 32x32.|
|`color`|2048 caracteres|✔|Um caminho de arquivo relativo para um ícone PNG colorido de 192x192.|

## <a name="accentcolor"></a>accentColor

**Obrigatório** &ndash; Cadeia de caracteres

Uma cor a ser usada com e como plano de fundo para seus ícones de estrutura de tópicos.

O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee`.

## <a name="configurabletabs"></a>configurbleTabs

Opcional:

Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada. As guias configuráveis têm suporte apenas no escopo das equipes e, atualmente, há suporte apenas para uma guia por aplicativo.

O objeto é uma matriz com todos os elementos do tipo `object`. Esse bloco é necessário apenas para soluções que fornecem uma solução de guia de canal configurável.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|Cadeia de caracteres|2048 caracteres|✔|A URL https:// a ser usada ao configurar a guia.|
|`canUpdateConfiguration`|Boolean|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Padrão: `true`|
|`scopes`|Matriz de enumeração|1|✔|Atualmente, as guias configuráveis são compatíveis apenas com os escopos `team` e `groupchat`. |
|`context` |matriz de enumerações|6 ||O conjunto de `contextItem` escopos em que uma [guia é compatível](../../tabs/how-to/access-teams-context.md). Padrão: `channelTab`, `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel` e `meetingStage`.|
|`sharePointPreviewImage`|Cadeia de caracteres|2048||Um caminho de arquivo relativo para uma imagem de visualização de guia para uso no SharePoint. Tamanho 1024x768. |
|`supportedSharePointHosts`|Matriz de enumeração|1||Define como sua guia será disponibilizada no SharePoint. As opções são `sharePointFullPage` e `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

Opcional:

Define um conjunto de guias que podem ser "fixadas" por padrão, sem que o usuário as adicione manualmente. As guias estáticas declaradas no escopo `personal` são sempre vinculadas à experiência pessoal do aplicativo. As guias estáticas declaradas no escopo `team` não são suportadas no momento.

Renderize guias com Cartões Adaptáveis especificando `contentBotId` em vez de `contentUrl` no bloco **staticTabs**.

O objeto é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object`. Esse bloco é necessário apenas para soluções que fornecem uma solução de guia estática.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|String|64 caracteres|✔|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|Cadeia de caracteres|128 caracteres|✔|O nome de exibição da guia na interface de canal.|
|`contentUrl`|Cadeia de caracteres|2048 caracteres|✔|A URL https:// que aponta para a interface do usuário da entidade a ser exibida na tela do Teams.|
|`contentBotId`|   | | | A ID do Aplicativo do Microsoft Teams especificada para o bot no portal do Bot Framework. |
|`websiteUrl`|Cadeia de caracteres|2048 caracteres||A URL https:// para apontar se um usuário optar por visualizar em um navegador.|
|`scopes`|Matriz de enumeração|1|✔|Atualmente, as guias estáticas oferecem suporte apenas ao escopo `personal`, o que significa que elas podem ser provisionadas apenas como parte da experiência pessoal.|

## <a name="bots"></a>bots

Opcional:

Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.

O objeto é uma matriz (máximo de apenas um elemento &mdash;, atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object`. Esse bloco é necessário apenas para soluções que fornecem uma experiência de bot.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|String|64 caracteres|✔|O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Isso pode ser o mesmo que a [ID de aplicativo](#id) geral.|
|`needsChannelSelector`|Boolean|||Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico. Padrão: `false`|
|`isNotificationOnly`|Boolean|||Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa. Padrão: `false`|
|`supportsFiles`|Boolean|||Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal. Padrão: `false`|
|`scopes`|Matriz de enumeração|3|✔|Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`). Essas opções são não exclusivas.|

### <a name="botscommandlists"></a>bots.commandLists

Uma lista opcional de comandos que seu bot pode recomendar aos usuários. O objeto é uma matriz (máximo de dois elementos) com todos os elementos do tipo `object`. Você deve definir uma lista de comandos separada para cada escopo que o seu bot oferece suporte. Para obter mais informações, confira [Menus de Bot](~/bots/how-to/create-a-bot-commands-menu.md).

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de enumeração|3|✔|Especifica o escopo para o qual a lista de comandos é válida. As opções são `team`, `personal` e `groupchat`.|
|`items.commands`|matriz de objetos|10|✔|Uma matriz de comandos que o bot suporta:<br>`title`: o nome do comando do bot (cadeia de caracteres, 32).<br>`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)|

## <a name="connectors"></a>conectores

Opcional:

O bloco `connectors` define um conector do Office 365 para o aplicativo.

O objeto é uma matriz (máximo de um elemento) com todos os elementos do tipo `object`. Este bloco é necessário apenas para soluções que fornecem um Conector.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|Cadeia de caracteres|2048 caracteres|✔|A URL https:// a ser usada ao configurar o conector.|
|`connectorId`|String|64 caracteres|✔|Um identificador exclusivo para o Conector que corresponde a sua ID no [Painel do Desenvolvedor de Conectores](https://aka.ms/connectorsdashboard).|
|`scopes`|Matriz de enumeração|1|✔|Especifica se o Conector oferece uma experiência no contexto de um canal em um `team`, ou uma experiência com escopo apenas para um usuário individual (`personal`). Atualmente, somente o escopo `team` é compatível.|

## <a name="composeextensions"></a>composeExtensions

Opcional:

Define uma extensão de mensagem para o aplicativo.

> [!NOTE]
> O nome do recurso foi alterado de “extensão de texto” para “extensão de mensagem” em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem funcionando.

O objeto é uma matriz (máximo de um elemento) com todos os elementos do tipo `object`. Este bloco é necessário apenas para soluções que fornecem uma extensão de mensagem.

|Nome| Tipo | Tamanho Máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|Cadeia de caracteres|64|✔|A ID exclusiva do aplicativo da Microsoft para o bot que oferece suporte à extensão de mensagem, conforme registrado no Bot Framework. Isso pode ser o mesmo que a [ID de aplicativo](#id) geral.|
|`canUpdateConfiguration`|Boolean|||Um valor que indica se a configuração de uma extensão de mensagem pode ser atualizada pelo usuário. O padrão é `false`.|
|`commands`|Matriz de objeto|10|✔|Matriz de comandos com suporte da extensão de mensagem.|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Sua extensão de mensagem deve declarar um ou mais comandos. Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário. Há um máximo de 10 comandos.

Cada item de comando é um objeto com a seguinte estrutura:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|String|64 caracteres|✔|A ID do comando.|
|`type`|String|64 caracteres||O tipo do comando. Um de `query` ou `action`. Padrão: `query`|
|`title`|Cadeia de caracteres|32 caracteres|✔|O nome do comando amigável.|
|`description`|Cadeia de caracteres|128 caracteres||A descrição que aparece para os usuários para indicar a finalidade deste comando.|
|`initialRun`|Booliano|||Um valor booliano que indica se o comando deve ser executado inicialmente sem parâmetros. Padrão: `false`|
|`context`|Matriz de cadeias de caracteres|3||Define de onde a extensão da mensagem pode ser invocada. Qualquer combinação de `compose`, `commandBox` e `message`. O padrão é `["compose", "commandBox"]`|
|`fetchTask`|Boolean|||Um valor booliano que indica se deve buscar o módulo de tarefa dinamicamente.|
|`taskInfo`|Objeto|||Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagem.|
|`taskInfo.title`|Cadeia de caracteres|64||Título inicial da caixa de diálogo.|
|`taskInfo.width`|Cadeia de caracteres|||Largura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.height`|Cadeia de caracteres|||Altura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.url`|Cadeia de caracteres|||URL inicial da webview.|
|`messageHandlers`|Matriz de Objetos|5||Uma lista de manipuladores que permitem que aplicativos sejam invocados quando determinadas condições são atendidas. Os domínios também devem ser listados em `validDomains`.|
|`messageHandlers.type`|Cadeia de caracteres|||O tipo de manipulador de mensagens. Deve ser `"link"`.|
|`messageHandlers.value.domains`|Matriz de cadeias de caracteres|||Matriz de domínios para os quais o manipulador de mensagens de link pode se registrar.|
|`parameters`|Matriz de objeto|5|✔|A lista de parâmetros que o comando usa. Mínimo: 1; máximo: 5.|
|`parameter.name`|String|64 caracteres|✔|O nome do parâmetro como aparece no cliente. Isso está incluído na solicitação de usuário.|
|`parameter.title`|Cadeia de caracteres|32 caracteres|✔|Título amigável para o parâmetro.|
|`parameter.description`|Cadeia de caracteres|128 caracteres||Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.|
|`parameter.inputType`|Cadeia de caracteres|128 caracteres||Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true`. Um de `text`, `textarea`, `number`, `date`, `time`, `toggle` e `choiceset`.|
|`parameter.choices`|Matriz de Objetos|10||As opções de escolha para `choiceset`. Use apenas quando `parameter.inputType` for `choiceset`.|
|`parameter.choices.title`|Cadeia de caracteres|128||Títulor da escolha.|
|`parameter.choices.value`|Cadeia de caracteres|512||O valor da escolha.|

## <a name="permissions"></a>permissões

Opcional:

Uma matriz de `string`, que especifica quais permissões o aplicativo solicita, que permite que os usuários finais saibam como a extensão será executada. As seguintes opções não são exclusivas:

* `identity`&emsp; Requer informações de identidade do usuário.
* `messageTeamMembers`&emsp; Requer permissão para enviar mensagens diretas aos membros da equipe.

Alterar essas permissões ao atualizar o aplicativo fará com que seus usuários repitam o processo de consentimento na primeira vez que executam o aplicativo atualizado.

## <a name="devicepermissions"></a>devicePermissions

**Opcional** Matriz de cadeias de caracteres

Especifica os recursos nativos no dispositivo de um usuário aos quais o seu aplicativo pode solicitar acesso. As opções são:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Opcional**, exceto **Obrigatório** onde indicado.

Uma lista de domínios válidos dos quais o aplicativo espera carregar qualquer conteúdo. As listagens de domínio podem incluir caracteres curinga, por exemplo, `*.example.com`. Isso corresponde exatamente a um segmento do domínio; se você precisar corresponder `a.b.example.com`, use `*.*.example.com`. Se a sua configuração de guias ou interface do usuário de conteúdo precisa navegar para qualquer outro domínio além do usado para a configuração de guias, esse domínio deve ser especificado aqui.

Entretanto, **não** é necessário incluir os domínios dos provedores de identidade aos quais você deseja oferecer suporte em seu aplicativo. Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve incluir accounts.google.com em `validDomains[]`.

> [!IMPORTANT]
> Não adicione domínios que estão fora de seu controle, seja diretamente ou por meio de curingas. Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.

O objeto é uma matriz com todos os elementos do tipo `string`.

## <a name="webapplicationinfo"></a>webApplicationInfo

Opcional:

Especifique Microsoft Azure Active Directory (Azure AD) id do aplicativo e Graph informações para ajudar os usuários a entrar diretamente em seu Azure AD aplicativo.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|Cadeia de caracteres|36 caracteres|✔|ID de aplicativo do Microsoft Azure Active Directory (Azure AD) do aplicativo. Essa ID deve ser um GUID.|
|`resource`|Cadeia de caracteres|2048 caracteres|✔|URL de recurso do aplicativo para adquirir token de autenticação para logon único.|
|`applicationPermissions`|Matriz|Máximo de 100 itens|✔|Permissões de recurso para o aplicativo.|

## <a name="graphconnector"></a>graphConnector

**Opcional**—objeto

Especifique a configuração do conector de gráfico do aplicativo. Se estiver presente, [webApplicationInfo.id](#webapplicationinfo) também deve ser especificado.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`notificationUrl`|string|2048 caracteres|✔|A URL para a qual as notificações do conector do Graph para o aplicativo devem ser enviadas.|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Opcional**—booliano

Indica se o indicador de carregamento deve ou não ser mostrado quando um aplicativo ou guia está sendo carregado. O padrão é **false**.
> [!NOTE]
> Se você selecionar `showLoadingIndicator` como true no manifesto do aplicativo, para carregar a página corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa conforme descrito em [Mostrar um documento de indicador de carregamento nativo](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator).

## <a name="isfullscreen"></a>isFullScreen

 **Opcional**—booliano

Indique onde um aplicativo pessoal é renderizado com ou sem uma barra de cabeçalho de guia. O padrão é **false**.

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

## <a name="configurableproperties"></a>configurableProperties

**Opcional** - matriz

O bloco `configurableProperties` define as propriedades do aplicativo que os administradores do Teams podem personalizar. Para obter mais informações, consulte [habilitar a personalização do aplicativo](~/concepts/design/enable-app-customization.md).

> [!NOTE]
> Um mínimo de uma propriedade deve ser definido. Você pode definir um máximo de nove propriedades neste bloco.

Você pode definir qualquer uma das seguintes propriedades:

* `name`: O nome de exibição do aplicativo.
* `shortDescription`: A breve descrição do aplicativo.
* `longDescription`: descrição detalhada do aplicativo.
* `smallImageUrl`: O ícone de contorno do aplicativo.
* `largeImageUrl`: O ícone de cor do aplicativo.
* `accentColor`: a cor a ser usada com e como plano de fundo para seus ícones de estrutura de tópicos.
* `developerUrl`: A URL HTTPS do site do desenvolvedor.
* `privacyUrl`: A URL HTTPS da política de privacidade do desenvolvedor.
* `termsOfUseUrl`: A URL HTTPS dos termos de uso do desenvolvedor.

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
|`meetings`|string|||Quando o escopo de instalação selecionado é `meetings`, este campo especifica o recurso padrão disponível. Opções: `tab`, `bot`ou `connector`.|

## <a name="subscriptionoffer"></a>subscriptionOffer

**Opcional** - objeto

Especifica a oferta de SaaS associada ao seu aplicativo.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
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

* **Permissões específicas de recursos para Teams compartilhamento ao vivo**

   |Nome| Descrição |
   | ----- | ----- |
   |`LiveShareSession.ReadWrite.Chat`|<!--- need info --->|
   |`LiveShareSession.ReadWrite.Channel`|<!--- need info --->|
   |`MeetingStage.Write.Chat`|<!--- need info --->|
   |`OnlineMeetingIncomingAudio.Detect.Chat`|<!--- need info --->|

## <a name="see-also"></a>Confira também

* [Compreender a estrutura do aplicativo Microsoft Teams](~/concepts/design/app-structure.md)
* [Habilitar personalização de aplicativo](~/concepts/design/enable-app-customization.md)
* [Localizar o aplicativo](~/concepts/build-and-test/apps-localization.md)
* [Integrar recursos de mídia](~/concepts/device-capabilities/mobile-camera-image-permissions.md)
