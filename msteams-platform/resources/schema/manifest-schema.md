---
title: Referência de esquema de manifesto
description: Descreve o esquema de manifesto do Microsoft Teams
ms.topic: reference
ms.author: lajanuar
keywords: esquema de manifesto do teams
ms.openlocfilehash: fa1c1cfd732fe5a30fc5fc32b693dd21b2e8ee82
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696042"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referência: esquema de manifesto para o Microsoft Teams

O manifesto do Teams descreve como o aplicativo se integra ao produto do Microsoft Teams. Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json) . Versões anteriores 1.0-1.4 também são suportadas (usando "v1.x" na URL).

O exemplo de esquema a seguir mostra todas as opções de extensibilidade.

## <a name="sample-full-manifest"></a>Exemplo de manifesto completo

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

O esquema define as seguintes propriedades:

## <a name="schema"></a>$schema

Opcional, mas recomendado — cadeia de caracteres

A https:// URL de referência do Esquema JSON para o manifesto.

## <a name="manifestversion"></a>manifestVersion

**Obrigatório —** cadeia de caracteres

A versão do esquema de manifesto que este manifesto está usando. Deve ser 1,9.

## <a name="version"></a>versão

**Obrigatório —** cadeia de caracteres

A versão de um aplicativo específico. Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada. Dessa forma, quando o novo manifesto é instalado, ele substitui o existente e o usuário recebe a nova funcionalidade. Se esse aplicativo foi enviado para a loja, o novo manifesto deve ser re-enviado e validado. Os usuários do aplicativo recebem o novo manifesto atualizado automaticamente dentro de algumas horas após a aprovação do manifesto.

Se as solicitações de aplicativos para permissões mudarem, os usuários serão solicitados a atualizar e consentir de novo para o aplicativo.

Esta cadeia de caracteres de versão deve seguir o padrão [de semver](http://semver.org/) (MAJOR. MINOR. PATCH).

## <a name="id"></a>id

**Obrigatório** — ID do aplicativo Microsoft

A ID é um identificador exclusivo gerado pela Microsoft para o aplicativo. Você tem uma ID se o bot estiver registrado por meio da Estrutura do Microsoft Bot ou do aplicativo Web da guia já entrar com a Microsoft. Você deve inserir a ID aqui. Caso contrário, você deve gerar uma nova ID no Portal de [Registro de Aplicativos da Microsoft.](https://aka.ms/appregistrations) Use a mesma ID se você adicionar um bot.

> [!NOTE]
> Se você estiver enviando uma atualização para seu aplicativo existente no AppSource, a ID em seu manifesto não deve ser modificada.

## <a name="developer"></a>developer

**Obrigatório —** objeto

Fornece informações sobre sua empresa. Para aplicativos enviados ao AppSource (antigo Office Store), esses valores devem corresponder às informações em sua entrada appSource. Consulte as [diretrizes de publicação](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) para obter informações adicionais.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`name`|32 caracteres|✔|O nome de exibição do desenvolvedor.|
|`websiteUrl`|2048 caracteres|✔|A https:// URL do site do desenvolvedor. Este link deve levar os usuários para a sua empresa ou página de aterrissagem específica do produto.|
|`privacyUrl`|2048 caracteres|✔|A https:// URL da política de privacidade do desenvolvedor.|
|`termsOfUseUrl`|2048 caracteres|✔|A https:// URL dos termos de uso do desenvolvedor.|
|`mpnId`|10 caracteres| |**Opcional** A ID da Rede de Parceiros da Microsoft que identifica a organização do parceiro que está criando o aplicativo.|

## <a name="name"></a>nome

**Obrigatório —** objeto

O nome da experiência do aplicativo, exibido para os usuários na experiência do Teams. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource. Os valores de `short` e `full` devem ser diferentes.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|30 caracteres|✔|O nome de exibição curto do aplicativo.|
|`full`|100 caracteres||O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.|

## <a name="description"></a>description

**Obrigatório —** objeto

Descreve seu aplicativo para usuários. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada appSource.

Verifique se sua descrição descreve com precisão sua experiência e fornece informações para ajudar os clientes em potencial a entender o que sua experiência faz. Você deve observar na descrição completa, se uma conta externa for necessária para uso. Os valores de `short` e `full` devem ser diferentes. Sua breve descrição não deve ser repetida na descrição longa e não deve incluir nenhum outro nome de aplicativo.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|80 caracteres|✔|Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.|
|`full`|4000 caracteres|✔|A descrição completa do seu aplicativo.|

## <a name="packagename"></a>packageName

**Opcional** — cadeia de caracteres

Um identificador exclusivo para o aplicativo na notação de domínio reverso; por exemplo, com.example.myapp. Comprimento máximo: 64 caracteres.

## <a name="localizationinfo"></a>localizationInfo

**Opcional** — objeto

Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais. Consulte [localização](~/concepts/build-and-test/apps-localization.md).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`defaultLanguageTag`||✔|A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Uma matriz de objetos que especifica traduções de idioma adicionais.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`languageTag`||✔|A marca de idioma das cadeias de caracteres no arquivo fornecido.|
|`file`||✔|Um caminho de arquivo relativo para um arquivo .json que contém as cadeias de caracteres traduzidas.|

## <a name="icons"></a>ícones

**Obrigatório —** objeto

Ícones usados no aplicativo teams. Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento. Consulte [Ícones](../../concepts/build-and-test/apps-package.md#app-icons) para obter mais informações.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`outline`|32 x 32 pixels|✔|Um caminho de arquivo relativo para um ícone de contorno PNG 32x32 transparente.|
|`color`|192 x 192 pixels|✔|Um caminho de arquivo relativo para um ícone PNG de cor total 192x192.|

## <a name="accentcolor"></a>accentColor

**Opcional** — código de cor de Hex HTML

Uma cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.

O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee` .

## <a name="configurabletabs"></a>configurbleTabs

**Opcional** — matriz

Usado quando a experiência do aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada. As guias configuráveis têm suporte apenas no escopo das equipes (não pessoal) e atualmente há suporte para apenas uma **guia** por aplicativo.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔|A https:// URL a ser usada ao configurar a guia.|
|`scopes`|matriz de números|1|✔|Atualmente, as guias configuráveis suportam apenas `team` os `groupchat` escopos e. |
|`canUpdateConfiguration`|booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Padrão: **true**.|
|`context` |matriz de números|6 ||O conjunto de `contextItem` escopos em que há suporte para uma guia. Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|string|2048||Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso no SharePoint. Tamanho 1024x768. |
|`supportedSharePointHosts`|matriz de números|1||Define como sua guia é disponibilizada no SharePoint. As opções `sharePointFullPage` são e `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Opcional** — matriz

Define um conjunto de guias que podem ser "fixados" por padrão, sem que o usuário as adicione manualmente. As guias estáticas declaradas no `personal` escopo são sempre fixadas à experiência pessoal do aplicativo. No momento, as guias estáticas declaradas no `team` escopo não são suportadas.

Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` . Esse bloco só é necessário para soluções que fornecem uma solução de tabulação estática.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|string|64 caracteres|✔|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|string|128 caracteres|✔|O nome de exibição da guia na interface do canal.|
|`contentUrl`|string||✔|A https:// URL que aponta para a interface do usuário da entidade a ser exibida na tela do Teams.|
|`websiteUrl`|string|||A https:// URL para apontar se um usuário optar por exibir em um navegador.|
|`searchUrl`|string|||A https:// URL a ser apontada para as consultas de pesquisa de um usuário.|
|`scopes`|matriz de números|1|✔|Atualmente, as guias estáticas suportam apenas o escopo, o que significa que ele só pode ser `personal` provisionado como parte da experiência pessoal.|
|`context` | matriz de números| 2|| O conjunto de `contextItem` escopos em que há suporte para uma guia.|

> [!NOTE]
> Se suas guias exigirem informações dependentes de contexto para exibir  conteúdo relevante ou para iniciar um fluxo de autenticação, consulte Obter contexto para a [guia Microsoft Teams](../../tabs/how-to/access-teams-context.md).

## <a name="bots"></a>bots

**Opcional** — matriz

Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.

O item é uma matriz (máximo de apenas 1 elemento atualmente, apenas um bot é permitido por aplicativo) com todos os elementos &mdash; do tipo `object` . Esse bloco só é necessário para soluções que fornecem uma experiência de bot.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64 caracteres|✔|O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Isso pode ser o mesmo da ID geral [do aplicativo.](#id)|
|`scopes`|matriz de números|3|✔|Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`). Essas opções são não exclusivas.|
|`needsChannelSelector`|booliano|||Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico. Padrão: **`false`**|
|`isNotificationOnly`|booliano|||Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa. Padrão: **`false`**|
|`supportsFiles`|booliano|||Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal. Padrão: **`false`**|
|`supportsCalling`|booliano|||Um valor que indica onde um bot dá suporte à chamada de áudio. **IMPORTANTE**: Esta propriedade é experimental no momento. As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.  Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção. Padrão: **`false`**|
|`supportsVideo`|booliano|||Um valor que indica onde um bot dá suporte à chamada de vídeo. **IMPORTANTE**: Esta propriedade é experimental no momento. As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.  Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção. Padrão: **`false`**|

### <a name="botscommandlists"></a>bots.commandLists

Uma lista opcional de comandos que seu bot pode recomendar aos usuários. O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo; você deve definir uma lista de comandos separada para cada escopo que `object` seu bot oferece suporte. Consulte [Menus bot para](~/bots/how-to/create-a-bot-commands-menu.md) obter mais informações.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de números|3|✔|Especifica o escopo para o qual a lista de comandos é válida. As opção são `team`, `personal` e `groupchat`.|
|`items.commands`|matriz de objetos|10 |✔|Uma matriz de comandos que o bot suporta:<br>`title`: o nome do comando bot (cadeia, 32)<br>`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)|

### <a name="botscommandlistscommands"></a>bots.commandLists.commands

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|title|string|12 |✔|O nome do comando bot|
|description|string|128 caracteres|✔|Uma descrição de texto simples ou um exemplo da sintaxe de comando e seus argumentos.|

## <a name="connectors"></a>conectores

**Opcional** — matriz

O `connectors` bloco define um Conector do Office 365 para o aplicativo.

O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Esse bloco só é necessário para soluções que fornecem um Conector.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔|A https:// URL a ser usada ao configurar o conector.|
|`scopes`|matriz de números|1|✔|Especifica se o Conector oferece uma experiência no contexto de um canal em um , ou uma experiência com escopo apenas para um `team` usuário individual ( `personal` ). Atualmente, apenas o `team` escopo é suportado.|
|`connectorId`|string|64 caracteres|✔|Um identificador exclusivo para o Conector que corresponde à sua ID no [Painel do Desenvolvedor de Conectores.](https://aka.ms/connectorsdashboard)|

## <a name="composeextensions"></a>composeExtensions

**Opcional** — matriz

Define uma extensão de mensagens para o aplicativo.

> [!NOTE]
> O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem funcionando.

O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Esse bloco só é necessário para soluções que fornecem uma extensão de mensagens.

|Nome| Tipo | Tamanho Máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64|✔|A ID de aplicativo exclusiva da Microsoft para o bot que é o suporte à extensão de mensagens, conforme registrado na Estrutura de Bot. Isso pode ser o mesmo que a ID geral do aplicativo.|
|`commands`|matriz de objetos|10 |✔|Matriz de comandos com suporte da extensão de mensagens|
|`canUpdateConfiguration`|booliano|||Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário. Padrão: **false**.|
|`messageHandlers`|matriz de objetos|5 ||Uma lista de manipuladores que permitem que os aplicativos sejam invocados quando determinadas condições são atendidas.|
|`messageHandlers.type`|string|||O tipo de manipulador de mensagens. Deve ser `"link"`.|
|`messageHandlers.value.domains`|matriz de cadeias de caracteres|||Matriz de domínios que o manipulador de mensagens de link pode registrar.|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Sua extensão de mensagens deve declarar um ou mais comandos. Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário. Há no máximo 10 comandos.

Cada item de comando é um objeto com a seguinte estrutura:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|64 caracteres|✔|A ID do comando.|
|`title`|string|32 caracteres|✔|O nome de comando amigável.|
|`type`|string|64 caracteres||Tipo do comando. Um dos `query` ou `action` . Padrão: **consulta**.|
|`description`|string|128 caracteres||A descrição que aparece para os usuários para indicar a finalidade deste comando.|
|`initialRun`|booliano|||Um valor booleano indica se o comando é executado inicialmente sem parâmetros. O padrão é **false**.|
|`context`|matriz de cadeias de caracteres|3||Define de onde a extensão da mensagem pode ser invocada. Qualquer combinação `compose` de , , `commandBox` `message` . O padrão é `["compose","commandBox"]`.|
|`fetchTask`|booliano|||Um valor booleano que indica se ele deve buscar o módulo de tarefa dinamicamente. O padrão é **false**.|
|`taskInfo`|objeto|||Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens.|
|`taskInfo.title`|string|64 caracteres||Título da caixa de diálogo inicial.|
|`taskInfo.width`|string|||Largura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.height`|string|||Altura da caixa de diálogo - um número em pixels ou layout padrão, como "grande", "médio" ou "pequeno".|
|`taskInfo.url`|string|||URL do webview inicial.|
|`parameters`|matriz de objeto|5 itens|✔|A lista de parâmetros que o comando assume. Mínimo: 1; máximo: 5.|
|`parameters.name`|string|64 caracteres|✔|O nome do parâmetro como ele aparece no cliente. Isso está incluído na solicitação do usuário.|
|`parameters.title`|string|32 caracteres|✔|Título amigável para o parâmetro.|
|`parameters.description`|string|128 caracteres||Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.|
|`parameters.value`|string|512 caracteres||Valor inicial do parâmetro.|
|`parameters.inputType`|string|128 caracteres||Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` . Um de `text, textarea, number, date, time, toggle, choiceset` .|
|`parameters.choices`|matriz de objetos|10 itens||As opções de escolha para `choiceset` o . Use somente quando `parameter.inputType` for `choiceset` .|
|`parameters.choices.title`|string|128 caracteres|✔|Título da escolha.|
|`parameters.choices.value`|string|512 caracteres|✔|O valor da escolha.|

## <a name="permissions"></a>permissões

**Opcional** — matriz de cadeias de caracteres

Uma matriz da qual especifica quais permissões o aplicativo solicita, o que permite que os usuários finais `string` saibam como a extensão se executa. As seguintes opções não são exclusivas:

* `identity`&emsp;Requer informações de identidade do usuário
* `messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe

Alterar essas permissões durante a atualização do aplicativo faz com que os usuários repitam o processo de consentimento após executarem o aplicativo atualizado. Consulte [Atualizando seu aplicativo para](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) obter mais informações.

## <a name="devicepermissions"></a>devicePermissions

**Opcional** — matriz de cadeias de caracteres

Fornece os recursos nativos no dispositivo de um usuário ao que seu aplicativo solicita acesso. As opções são:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Opcional**, exceto **Obrigatório quando** notado

Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do Teams. Listagem de domínio pode incluir caracteres curinga, por exemplo, `*.example.com` . Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` . Se a configuração de tabulação ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de tabulação, esse domínio deve ser especificado aqui.

Não é **necessário** incluir os domínios de provedores de identidade que você deseja dar suporte ao seu aplicativo. Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para accounts.google.com, no entanto, você não deve incluir accounts.google.com em `validDomains[]` .

Os aplicativos do Teams que exigem suas próprias URLs do sharepoint funcionam bem, inclui "{teamsitedomain}" em sua lista de domínios válida.

> [!IMPORTANT]
> Não adicione domínios que estão fora do seu controle, diretamente ou por meio de caracteres curinga. Por exemplo, `yourapp.onmicrosoft.com` é válido, no entanto, `*.onmicrosoft.com` não é válido.

O objeto é uma matriz com todos os elementos do tipo `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Opcional** — objeto

Forneça suas informações de ID de aplicativo do Azure Active Directory (AAD) e do Microsoft Graph para ajudar os usuários a entrar perfeitamente em seu aplicativo. Se seu aplicativo estiver registrado no AAD, você deverá fornecer a ID do aplicativo, para que os administradores possam revisar facilmente as permissões e conceder consentimento no Centro de administração do Teams.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|36 caracteres|✔|ID do aplicativo AAD do aplicativo. Essa id deve ser um GUID.|
|`resource`|string|2048 caracteres|✔|URL de recurso do aplicativo para adquirir token de autenticação para SSO. </br> **OBSERVAÇÃO:** Se você não estiver usando o SSO, certifique-se de inserir um valor de cadeia de caracteres fictício neste campo para o manifesto do aplicativo, por exemplo, para evitar https://notapplicable uma resposta de erro. |
|`applicationPermissions`|matriz de cadeia de caracteres|128 caracteres||Especifique o [consentimento específico do recurso granular](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Opcional** — booleano

Indica se é ou não para mostrar o indicador de carregamento quando um aplicativo ou guia está sendo carregado. O padrão é **false**.
>[!NOTE]
>Se você selecionar como true no manifesto do aplicativo, para carregar a página corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa conforme descrito em Mostrar um documento indicador de carregamento `showLoadingIndicator` nativo. [](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)


## <a name="isfullscreen"></a>isFullScreen

 **Opcional** — booleano

Indica onde um aplicativo pessoal é renderizado com ou sem uma barra de header de tabulação. O padrão é **false**.

## <a name="activities"></a>activities

**Opcional** — objeto

Defina as propriedades que seu aplicativo usa para postar um feed de atividade do usuário.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`activityTypes`|matriz de objetos|128 itens| | Forneça os tipos de atividades que seu aplicativo pode postar em um feed de atividades dos usuários.|

### <a name="activitiesactivitytypes"></a>activities.activityTypes

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`type`|string|32 caracteres|✔|O tipo de notificação. *Consulte abaixo*.|
|`description`|string|128 caracteres|✔|Uma breve descrição da notificação. *Consulte abaixo*.|
|`templateText`|string|128 caracteres|✔|Ex: "{actor} criado tarefa {taskId} para você"|

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


