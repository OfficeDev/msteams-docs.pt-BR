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
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referência: Manifesto esquema para Microsoft Teams

O manifesto Teams descreve como o aplicativo se integra ao produto Microsoft Teams. Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json) . As versões anteriores 1.0, 1.1,..., 1.6 e assim por diante também são suportadas (usando "v1.x" na URL).

A seguinte amostra de esquema mostra todas as opções de extensibilidade:

## <a name="sample-full-manifest"></a>Amostra de manifesto completo

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

O esquema define as seguintes propriedades:

## <a name="schema"></a>$schema

Opcional, mas recomendado — string

A URL https:// fazendo referência ao Esquema JSON para o manifesto.

## <a name="manifestversion"></a>manifestVersion

**Obrigatório** — string

A versão do esquema manifesto que este manifesto está usando. Deve ser 1,10.

## <a name="version"></a>versão

**Obrigatório** — string

A versão de um aplicativo específico. Se você atualizar algo em seu manifesto, a versão deve ser incrementada também. Dessa forma, quando o novo manifesto é instalado, ele substitui o existente e o usuário recebe a nova funcionalidade. Se este aplicativo foi enviado à loja, o novo manifesto deve ser remetido e revalidado. Os usuários do aplicativo recebem o novo manifesto atualizado automaticamente poucas horas após a aprovação do manifesto.

Se o aplicativo solicitar permissões mudar, os usuários ãovoquem e re consentam com o aplicativo.

Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (MAJOR. menor. PATCH).

## <a name="id"></a>id

**Obrigatório** — ID do aplicativo da Microsoft

O ID é um identificador exclusivo gerado pela Microsoft para o aplicativo. Você tem um ID se o seu bot estiver registrado através do Microsoft Bot Framework ou o aplicativo web da sua guia já entra na Microsoft. Você deve entrar na 19. Caso contrário, você deve gerar um novo ID no [Portal de Registro de Aplicativos da Microsoft](https://aka.ms/appregistrations). Use o mesmo ID se adicionar um bot.

> [!NOTE]
> Se você estiver enviando uma atualização para o seu aplicativo existente no AppSource, o ID em seu manifesto não deve ser modificado.

## <a name="developer"></a>developer

**Necessário** — objeto

Especifica informações sobre sua empresa. Para aplicativos submetidos à loja Teams, esses valores devem corresponder às informações na listagem da sua loja. Para obter mais informações, consulte as [diretrizes de publicação de Teams loja](~/concepts/deploy-and-publish/appsource/publish.md).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`name`|32 caracteres|✔|O nome de exibição para o desenvolvedor.|
|`websiteUrl`|2048 caracteres|✔|O https:// URL para o site do desenvolvedor. Este link deve levar os usuários para sua empresa ou página de landing específica do produto.|
|`privacyUrl`|2048 caracteres|✔|O https:// URL para a política de privacidade do desenvolvedor.|
|`termsOfUseUrl`|2048 caracteres|✔|O https:// URL para os termos de uso do desenvolvedor.|
|`mpnId`|10 caracteres| |**Opcional** O Microsoft Partner Network ID que identifica a organização parceira que está construindo o aplicativo.|

## <a name="name"></a>nome

**Necessário** — objeto

O nome da experiência do seu aplicativo, exibido aos usuários na experiência Teams. Para aplicativos submetidos ao AppSource, esses valores devem corresponder às informações na sua entrada appSource. Os valores `short` de e devem ser `full` diferentes.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|30 caracteres|✔|O nome de exibição curto para o aplicativo.|
|`full`|100 caracteres||O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.|

## <a name="description"></a>descrição

**Necessário** — objeto

Descreve seu aplicativo para os usuários. Para aplicativos submetidos ao AppSource, esses valores devem corresponder às informações na sua entrada appSource.

Certifique-se de que sua descrição descreve com precisão sua experiência e fornece informações para ajudar os clientes em potencial a entender o que sua experiência faz. Você deve observar na descrição completa, se uma conta externa for necessária para uso. Os valores `short` de e devem ser `full` diferentes. Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir qualquer outro nome do aplicativo.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|80 caracteres|✔|Uma breve descrição da sua experiência de aplicativo, usada quando o espaço é limitado.|
|`full`|4000 caracteres|✔|A descrição completa do seu aplicativo.|

## <a name="packagename"></a>packageName

**Opcional** — string

Um identificador exclusivo para o aplicativo em notação de domínio reverso; por exemplo, com.example.myapp. Comprimento máximo: 64 caracteres.

## <a name="localizationinfo"></a>localizaçãoInfo

**Opcional** — objeto

Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais. Para obter mais informações, consulte [localização.](~/concepts/build-and-test/apps-localization.md)

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`defaultLanguageTag`||✔|A tag de idioma das strings neste arquivo manifesto de nível superior.|

### <a name="localizationinfoadditionallanguages"></a>localizaçãoInfo.additionalLíguas

Uma variedade de objetos especificando traduções adicionais de idiomas.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`languageTag`||✔|A tag de idioma das strings no arquivo fornecido.|
|`file`||✔|Um caminho relativo de arquivo para um arquivo .json contendo as strings traduzidas.|

## <a name="icons"></a>ícones

**Necessário** — objeto

Ícones usados no aplicativo Teams. Os arquivos de ícone devem ser incluídos como parte do pacote de upload. Consulte [Ícones](../../concepts/build-and-test/apps-package.md#app-icons) para obter mais informações.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`outline`|32 x 32 pixels|✔|Um caminho relativo de arquivo para um ícone transparente de contorno 32x32 PNG.|
|`color`|192 x 192 pixels|✔|Um caminho relativo de arquivo para um ícone PNG de cor completa 192x192.|

## <a name="accentcolor"></a>sotaqueColor

**Opcional** — Código de cor HTML Hex

Uma cor para usar em conjunto com e como plano de fundo para seus ícones de contorno.

O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee` .

## <a name="configurabletabs"></a>configurávelTabs

**Opcionais** — matriz

Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada. As guias configuráveis são suportadas apenas no escopo das equipes e você pode configurar as mesmas guias várias vezes. No entanto, você pode defini-lo no manifesto apenas uma vez.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔|A https:// URL a ser usada ao configurar a guia.|
|`scopes`|matriz de enums|1|✔|Atualmente, as guias configuráveis suportam apenas os `team` `groupchat` escopos e escopos. |
|`canUpdateConfiguration`|booliano|||Um valor indicando se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Padrão: **verdadeiro**.|
|`context` |matriz de enums|6 ||O conjunto de `contextItem` escopos onde uma [guia é suportada](../../tabs/how-to/access-teams-context.md). Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|cadeia de caracteres|2048||Um caminho relativo de arquivo para uma imagem de visualização de guia para uso em SharePoint. Tamanho 1024x768. |
|`supportedSharePointHosts`|matriz de enums|1||Define como sua guia é disponibilizada em SharePoint. As opções são `sharePointFullPage` e `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Opcionais** — matriz

Define um conjunto de guias que podem ser "fixadas" por padrão, sem que o usuário as adicione manualmente. As guias estáticas declaradas no `personal` escopo são sempre fixadas à experiência pessoal do aplicativo. As guias estáticas declaradas no `team` escopo não são suportadas no momento.

Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` . Este bloco é necessário apenas para soluções que forneçam uma solução de guia estática.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|string|64 caracteres|✔|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|cadeia de caracteres|128 caracteres|✔|O nome de exibição da guia na interface do canal.|
|`contentUrl`|cadeia de caracteres||✔|A url https:// que aponta para a interface do usuário da entidade a ser exibida na tela Teams.|
|`websiteUrl`|cadeia de caracteres|||O https:// URL para apontar se um usuário opta por visualizar em um navegador.|
|`searchUrl`|cadeia de caracteres|||O https:// URL para apontar para consultas de pesquisa de um usuário.|
|`scopes`|matriz de enums|1|✔|Atualmente, as guias estáticas suportam apenas o escopo, o `personal` que significa que ele só pode ser provisionado como parte da experiência pessoal.|
|`context` | matriz de enums| 2|| O conjunto de `contextItem` escopos onde uma guia é suportada.|

> [!NOTE]
>  O recurso searchUrl não está disponível para desenvolvedores de terceiros.
> Se suas guias exigirem informações dependentes do contexto para exibir conteúdo relevante ou para iniciar um fluxo de autenticação, Para obter mais informações, consulte [Obter contexto para sua guia Microsoft Teams](../../tabs/how-to/access-teams-context.md).

## <a name="bots"></a>Bots

**Opcionais** — matriz

Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.

O item é uma matriz (no máximo 1 elemento &mdash; atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object` . Este bloco é necessário apenas para soluções que forneçam uma experiência de bot.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64 caracteres|✔|O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Isso pode muito bem ser o mesmo que o [ID](#id)geral do aplicativo .|
|`scopes`|matriz de enums|3|✔|Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`). Essas opções são não exclusivas.|
|`needsChannelSelector`|booliano|||Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico. inadimplência: **`false`**|
|`isNotificationOnly`|booliano|||Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa. inadimplência: **`false`**|
|`supportsFiles`|booliano|||Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal. inadimplência: **`false`**|
|`supportsCalling`|booliano|||Um valor indicando onde um bot suporta chamadas de áudio. **IMPORTANTE**: Esta propriedade é atualmente experimental. As propriedades experimentais podem não estar completas e podem sofrer alterações antes de ficarem totalmente disponíveis.  Está previsto apenas para fins de teste e exploração e não deve ser utilizado em aplicações de produção. inadimplência: **`false`**|
|`supportsVideo`|booliano|||Um valor indicando onde um bot suporta chamadas de vídeo. **IMPORTANTE**: Esta propriedade é atualmente experimental. As propriedades experimentais podem não estar completas e podem sofrer alterações antes de ficarem totalmente disponíveis.  Está previsto apenas para fins de teste e exploração e não deve ser utilizado em aplicações de produção. inadimplência: **`false`**|

### <a name="botscommandlists"></a>bots.commandLists

Uma lista opcional de comandos que o bot pode recomendar aos usuários. O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo ; você deve definir uma lista de `object` comando separada para cada escopo que o seu bot suporta. Consulte [menus bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de enums|3|✔|Especifica o escopo para o qual a lista de comandos é válida. As opção são `team`, `personal` e `groupchat`.|
|`items.commands`|matriz de objetos|10 |✔|Uma matriz de comandos que o bot suporta:<br>`title`: o nome do comando bot (cadeia, 32)<br>`description`: uma descrição simples ou exemplo da sintaxe de comando e seu argumento (string, 128).|

### <a name="botscommandlistscommands"></a>bots.commandLists.commands

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|title|string|12 |✔|O nome do comando do bot.|
|description|string|128 caracteres|✔|Uma simples descrição de texto ou um exemplo da sintaxe de comando e seus argumentos.|

## <a name="connectors"></a>Conectores

**Opcionais** — matriz

O `connectors` bloco define um conector de Office 365 para o aplicativo.

O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Este bloco é necessário apenas para soluções que forneçam um Conector.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔|A https:// URL para usar ao configurar o conector.|
|`scopes`|matriz de enums|1|✔|Especifica se o Conector oferece uma experiência no contexto de um canal em um `team` , ou uma experiência escopo para um usuário individual `personal` (). Atualmente, apenas o `team` escopo é suportado.|
|`connectorId`|cadeia de caracteres|64 caracteres|✔|Um identificador exclusivo para o Conector que corresponde ao seu ID no [Painel de Desenvolvedores de Conectores](https://aka.ms/connectorsdashboard).|

## <a name="composeextensions"></a>comporTensões

**Opcionais** — matriz

Define uma extensão de mensagens para o aplicativo.

> [!NOTE]
> O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome manifesto permanece o mesmo para que as extensões existentes continuem funcionando.

O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Este bloco é necessário apenas para soluções que forneçam uma extensão de mensagens.

|Nome| Tipo | Tamanho Máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64|✔|O ID exclusivo do aplicativo da Microsoft para o bot que apoia a extensão de mensagens, como registrado no Bot Framework. Isso pode muito bem ser o mesmo que o ID geral do aplicativo.|
|`commands`|matriz de objetos|10 |✔|Matriz de comandos que a extensão de mensagens suporta.|
|`canUpdateConfiguration`|booliano|||Um valor indicando se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário. Padrão: **false**.|
|`messageHandlers`|matriz de objetos|5 ||Uma lista de manipuladores que permitem que os aplicativos sejam invocados quando determinadas condições são atendidas.|
|`messageHandlers.type`|cadeia de caracteres|||O tipo de manipulador de mensagens. Deve ser `"link"`.|
|`messageHandlers.value.domains`|matriz de Strings|||Matriz de domínios para os que o manipulador de mensagens de link pode registrar.|

### <a name="composeextensionscommands"></a>comporExtensions.commands

Sua extensão de mensagens deve declarar um ou mais comandos. Cada comando aparece em Microsoft Teams como uma interação potencial do ponto de entrada baseado em interface do usuário. Há um máximo de 10 comandos.

Cada item de comando é um objeto com a seguinte estrutura:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|64 caracteres|✔|A responsabilidade pelo comando.|
|`title`|cadeia de caracteres|32 caracteres|✔|O nome de comando fácil de usar.|
|`type`|cadeia de caracteres|64 caracteres||Tipo de comando. Um de `query` ou `action` . Padrão: **consulta**.|
|`description`|cadeia de caracteres|128 caracteres||A descrição que aparece aos usuários para indicar o propósito deste comando.|
|`initialRun`|booliano|||Um valor booleano indica se o comando é executado inicialmente sem parâmetros. O padrão é **false**.|
|`context`|matriz de Strings|3||Define de onde a extensão da mensagem pode ser invocada. Qualquer combinação `compose` `commandBox` de, `message` . . O padrão é `["compose","commandBox"]`.|
|`fetchTask`|booliano|||Um valor booleano que indica se ele deve buscar o módulo de tarefa dinamicamente. O padrão é **false**.|
|`taskInfo`|objeto|||Especifique o módulo de tarefa para pré-carregar ao usar um comando de extensão de mensagens.|
|`taskInfo.title`|cadeia de caracteres|64 caracteres||Título de diálogo inicial.|
|`taskInfo.width`|cadeia de caracteres|||Largura de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.height`|cadeia de caracteres|||Altura de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.url`|cadeia de caracteres|||URL inicial do webview.|
|`parameters`|matriz de objeto|5 itens|✔|A lista de parâmetros que o comando toma. Mínimo: 1; máximo: 5.|
|`parameters.name`|cadeia de caracteres|64 caracteres|✔|O nome do parâmetro como aparece no cliente. Isso está incluído na solicitação do usuário.|
|`parameters.title`|cadeia de caracteres|32 caracteres|✔|Título fácil de usar para o parâmetro.|
|`parameters.description`|cadeia de caracteres|128 caracteres||String fácil de usar que descreve o propósito deste parâmetro.|
|`parameters.value`|cadeia de caracteres|512 caracteres||Valor inicial para o parâmetro.|
|`parameters.inputType`|cadeia de caracteres|128 caracteres||Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` . Um `text, textarea, number, date, time, toggle, choiceset` de.|
|`parameters.choices`|matriz de objetos|10 itens||As opções de escolha para o `choiceset` . Use somente quando `parameter.inputType` estiver `choiceset` .|
|`parameters.choices.title`|cadeia de caracteres|128 caracteres|✔|O título da escolha.|
|`parameters.choices.value`|cadeia de caracteres|512 caracteres|✔|O valor da escolha.|

## <a name="permissions"></a>permissões

**Opcional** — matriz de cordas

Um conjunto especifica `string` quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão se sai. As seguintes opções não são exclusivas:

* `identity`&emsp;Requer informações de identidade do usuário.
* `messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe.

Alterar essas permissões durante a atualização do aplicativo faz com que seus usuários repitam o processo de consentimento depois de executarem o aplicativo atualizado. Consulte [Atualizando seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) para obter mais informações.

## <a name="devicepermissions"></a>dispositivosPermissões

**Opcional** — matriz de cordas

Fornece os recursos nativos no dispositivo do usuário ao que seu aplicativo solicita acesso. As opções são:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Opcional,** exceto **Necessário** quando observado.

Uma lista de domínios válidos para sites que o aplicativo espera carregar dentro do Teams cliente. As listagens de domínio podem incluir curingas, por `*.example.com` exemplo, . Isso corresponde exatamente a um segmento do domínio; se você precisar `a.b.example.com` combinar, então use `*.*.example.com` . Se a configuração da guia ou a interface do conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de guia, esse domínio deve ser especificado aqui.

**Não** é necessário incluir os domínios dos provedores de identidade que você deseja suportar em seu aplicativo. Por exemplo, para autenticar usando um ID do Google, é necessário redirecionar para accounts.google.com, no entanto, você não deve incluir accounts.google.com em `validDomains[]` .

Teams aplicativos que exigem que seus próprios URLs de ponto de compartilhamento funcionem bem, inclui "{teamsitedomain}" em sua lista de domínios válida.

> [!IMPORTANT]
> Não adicione domínios que estejam fora do seu controle, diretamente ou através de curingas. Por exemplo, `yourapp.onmicrosoft.com` é válido, no entanto, `*.onmicrosoft.com` não é válido.

O objeto é uma matriz com todos os elementos do tipo `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Opcional** — objeto

Forneça informações sobre o aplicativo Azure Active Directory (AAD) e a Microsoft Graph para ajudar os usuários a entrar em seu aplicativo perfeitamente. Se o seu aplicativo estiver registrado no AAD, você deve fornecer o ID do aplicativo, para que os administradores possam facilmente rever permissões e conceder consentimento em Teams centro administrativo.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|36 caracteres|✔|ID de aplicativo AAD do aplicativo. Esta id deve ser uma GUID.|
|`resource`|cadeia de caracteres|2048 caracteres|✔|URL de recurso do aplicativo para aquisição de token auth para SSO. </br> **NOTA:** Se você não estiver usando o SSO, certifique-se de inserir um valor de sequência de caracteres falso neste campo no manifesto do seu aplicativo, por exemplo, https://notapplicable para evitar uma resposta de erro. |
|`applicationPermissions`|matriz de cadeia de caracteres|128 caracteres||Especifique [o consentimento específico do recurso](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)granular .|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Opcional** — booleano

Indica se deve ou não mostrar o indicador de carregamento quando um aplicativo ou guia está carregando. O padrão é **false**.
>[!NOTE]
>Se você selecionar `showLoadingIndicator` como verdadeiro no manifesto do aplicativo, para carregar a página corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa, conforme descrito em Mostrar um documento indicador de carregamento [nativo.](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)


## <a name="isfullscreen"></a>isFullScreen

 **Opcional** — booleano

Indique onde um aplicativo pessoal é renderizado com ou sem uma barra de cabeçalho de guia. O padrão é **false**.

## <a name="activities"></a>activities

**Opcional** — objeto

Defina as propriedades que seu aplicativo usa para postar um feed de atividade do usuário.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`activityTypes`|matriz de objetos|128 itens| | Forneça os tipos de atividades que seu aplicativo pode postar para um feed de atividades dos usuários.|

### <a name="activitiesactivitytypes"></a>activities.activityTypes

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`type`|string|32 caracteres|✔|O tipo de notificação. *Veja abaixo*.|
|`description`|cadeia de caracteres|128 caracteres|✔|Uma breve descrição da notificação. *Veja abaixo*.|
|`templateText`|cadeia de caracteres|128 caracteres|✔|Ex: "{ator} criou tarefa {taskId} para você"|

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

**Opcional** - string

Especifica o escopo de instalação definido para este aplicativo por padrão. O escopo definido será a opção exibida no botão quando um usuário tentar adicionar o aplicativo. As opções são:
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a>padrãoGroupCapability

**Opcional** - objeto

Quando um escopo de instalação de grupo é selecionado, ele definirá o recurso padrão quando o usuário instalar o aplicativo. As opções são:
* `team`
* `groupchat`
* `meetings`
 
|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`team`|string|||Quando o escopo de instalação selecionado `team` é, este campo especifica o recurso padrão disponível. Opções: `tab` `bot` , , ou `connector` .|
|`groupchat`|cadeia de caracteres|||Quando o escopo de instalação selecionado `groupchat` é, este campo especifica o recurso padrão disponível. Opções: `tab` `bot` , , ou `connector` .|
|`meetings`|cadeia de caracteres|||Quando o escopo de instalação selecionado `meetings` é, este campo especifica o recurso padrão disponível. Opções: `tab` `bot` , , ou `connector` .|

## <a name="configurableproperties"></a>configurávelProperties

**Opcionais** - matriz

O `configurableProperties` bloco define as propriedades do aplicativo que Teams administrador pode personalizar. Para obter mais informações, consulte [personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).

> [!NOTE]
> Um mínimo de uma propriedade deve ser definido. Você pode definir um máximo de nove propriedades neste bloco.
> Como uma prática recomendada, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes seguirem ao personalizar seu aplicativo.

Você pode definir qualquer uma das seguintes propriedades:
* `name`: Permite que o administrador altere o nome de exibição do aplicativo.
* `shortDescription`: Permite que o administrador altere a descrição curta do aplicativo.
* `longDescription`: Permite que o administrador altere a descrição detalhada do aplicativo.
* `smallImageUrl`: É a `outline` propriedade no bloco do `icons` manifesto.
* `largeImageUrl`: É a `color` propriedade no bloco do `icons` manifesto.
* `accentColor`: É a cor para usar em conjunto e como plano de fundo para seus ícones de contorno.
* `websiteUrl`: É a url https:// para o site do desenvolvedor.
* `privacyUrl`: É a https:// URL da política de privacidade do desenvolvedor.
* `termsOfUseUrl`: É a url https:// para os termos de uso do desenvolvedor.


