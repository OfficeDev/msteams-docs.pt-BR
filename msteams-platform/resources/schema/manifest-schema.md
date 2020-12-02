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
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referência: esquema de manifesto para o Microsoft Teams

O manifesto do Microsoft Teams descreve como o aplicativo integra-se ao produto Microsoft Teams. Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json) . As versões anteriores 1.0-1.4 também são suportadas (usando "v1. x" na URL).

O seguinte exemplo de esquema mostra todas as opções de extensibilidade.

## <a name="sample-full-manifest"></a>Exemplo de manifesto completo

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

O esquema define as seguintes propriedades:

## <a name="schema"></a>$schema

*Opcional, mas recomendado* — cadeia de caracteres

A URL https://que faz referência ao esquema JSON para o manifesto.

## <a name="manifestversion"></a>manifestVersion

**Obrigatório** — cadeia de caracteres

A versão do esquema de manifesto que este manifesto está usando. Ele deve ser "1,7".

## <a name="version"></a>versão

**Obrigatório** — cadeia de caracteres

A versão do aplicativo específico. Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada. Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade. Se este aplicativo foi enviado para o repositório, o novo manifesto terá que ser reenviado e validado novamente. Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, após serem aprovados.

Se as permissões solicitadas pelo aplicativo forem alteradas, os usuários serão solicitados a atualizar e a dar o consentimento novamente para o aplicativo.

Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (principal. Mínima. PATCH).

## <a name="id"></a>id

**Obrigatório** – ID do aplicativo da Microsoft

O identificador exclusivo gerado pela Microsoft para este aplicativo. Se você tiver registrado um bot por meio da Microsoft bot Framework, ou se o aplicativo Web da sua guia já estiver conectado com a Microsoft, você já deve ter um ID e deve inseri-lo aqui. Caso contrário, você deve gerar uma nova ID no portal de registro de aplicativos da Microsoft ([meus aplicativos](https://apps.dev.microsoft.com)), inseri-la aqui e reutilizá-la quando você adicionar um bot. Observação: se você estiver enviando uma atualização para o seu aplicativo existente no AppSource, a ID em seu manifesto não deverá ser modificada.

## <a name="developer"></a>developer

**Obrigatório** — objeto

Especifica informações sobre sua empresa. Para aplicativos enviados para o AppSource (anteriormente Office Store), esses valores devem corresponder às informações na entrada do AppSource. Veja nossas [diretrizes de publicação](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) para obter mais informações.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`name`|32 caracteres|✔|O nome de exibição para o desenvolvedor.|
|`websiteUrl`|2048 caracteres|✔|A URL do https://para o site do desenvolvedor. Este link deve levar os usuários à sua página de aterrissagem específica da empresa ou do produto.|
|`privacyUrl`|2048 caracteres|✔|A URL do https://para a política de privacidade do desenvolvedor.|
|`termsOfUseUrl`|2048 caracteres|✔|A URL do https://para os termos de uso do desenvolvedor.|
|`mpnId`|10 caracteres| |**Opcional** A ID de rede do parceiro da Microsoft que identifica a organização do parceiro que está criando o aplicativo.|

## <a name="name"></a>nome

**Obrigatório** — objeto

O nome da sua experiência de aplicativo, exibido aos usuários na experiência do teams. Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource. Os valores de `short` e `full` não devem ser os mesmos.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|30 caracteres|✔|O nome de exibição curto para o aplicativo.|
|`full`|100 caracteres||O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.|

## <a name="description"></a>description

**Obrigatório** — objeto

Descreve seu aplicativo para os usuários. Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.

Certifique-se de que sua descrição descreve precisamente sua experiência e fornece informações para ajudar os clientes potenciais a entender o que a sua experiência faz. Você também deve observar, na descrição completa, se for necessário usar uma conta externa. Os valores de `short` e `full` não devem ser os mesmos.  Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir nenhum outro nome de aplicativo.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|80 caracteres|✔|Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.|
|`full`|4000 caracteres|✔|A descrição completa do seu aplicativo.|

## <a name="packagename"></a>Packagenamena

**Opcional** — cadeia de caracteres

Um identificador exclusivo para esse aplicativo na notação de domínio reverso; por exemplo, com. example. MyApp. Comprimento máximo: 64 caracteres.

## <a name="localizationinfo"></a>localizationInfo

**Opcional** — objeto

Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais. Confira [localização](~/concepts/build-and-test/apps-localization.md).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`defaultLanguageTag`||✔|A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Uma matriz de objetos especificando traduções de idiomas adicionais.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`languageTag`||✔|A marca de idioma das cadeias de caracteres no arquivo fornecido.|
|`file`||✔|Um caminho de arquivo relativo para um arquivo. JSON que contém as cadeias de caracteres traduzidas.|

## <a name="icons"></a>ícones

**Obrigatório** — objeto

Ícones usados no aplicativo Teams. Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento. Consulte [ícones](~/concepts/build-and-test/apps-package.md#icons) para obter mais informações.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`outline`|32 x 32 pixels|✔|Um caminho de arquivo relativo para um ícone de estrutura de tópicos de PNG de 32 x 32 transparente.|
|`color`|192 x 192 pixels|✔|Um caminho de arquivo relativo para um ícone de 192x192 do PNG completo.|

## <a name="accentcolor"></a>accentColor

**Opcional** – código de cor hex HTML

Uma cor a ser usada em conjunto com e como um plano de fundo para seus ícones de estrutura de tópicos.

O valor deve ser um código de cor HTML válido começando com ' # ', por exemplo `#4464ee` .

## <a name="configurabletabs"></a>configurableTabs

**Opcional** — array

Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração adicional antes de ser adicionada. Guias configuráveis têm suporte apenas no escopo Teams (não pessoal), e atualmente só há suporte para **uma** guia por aplicativo.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔|A URL do https://a ser usada ao configurar a guia.|
|`scopes`|matriz de enums|1|✔|No momento, as guias configuráveis só dão suporte a `team` e os `groupchat` escopos. |
|`canUpdateConfiguration`|booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Padrão: **true**.|
|`context` |matriz de enums|6 ||O conjunto de `contextItem` escopos onde há suporte para uma tabulação. Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|cadeia de caracteres|2048||Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso no SharePoint. Tamanho 1024x768. |
|`supportedSharePointHosts`|matriz de enums|1||Define como sua guia será disponibilizada no SharePoint. Opções são `sharePointFullPage` e `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Opcional** — array

Define um conjunto de guias que podem ser "fixadas" por padrão, sem o usuário adicioná-las manualmente. As guias estáticas declaradas no `personal` escopo são sempre fixadas para a experiência pessoal do aplicativo. Guias static declaradas no `team` escopo não são suportadas atualmente.

Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` . Esse bloco é necessário somente para soluções que oferecem uma solução de guia estática.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|string|64 caracteres|✔|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|cadeia de caracteres|128 caracteres|✔|O nome de exibição da guia na interface de canal.|
|`contentUrl`|cadeia de caracteres||✔|A URL https://que aponta para a interface do usuário da entidade a ser exibida na tela do teams.|
|`websiteUrl`|cadeia de caracteres|||A URL do https://para apontar para o modo de exibição de um usuário em um navegador.|
|`searchUrl`|cadeia de caracteres|||A URL do https://para apontar para as consultas de pesquisa de um usuário.|
|`scopes`|matriz de enums|1|✔|Atualmente, as guias estáticas oferecem suporte somente ao `personal` escopo, o que significa que ela pode ser provisionada somente como parte da experiência pessoal.|
|`context` | matriz de enums| duas|| O conjunto de `contextItem` escopos onde há suporte para uma tabulação.|

> [!NOTE]
> Se suas guias exigirem informações dependentes de contexto para exibir conteúdo relevante ou para iniciar um fluxo de autenticação, *consulte* [obter contexto para a guia do Microsoft Teams](../../tabs/how-to/access-teams-context.md).

## <a name="bots"></a>robôs

**Opcional** — array

Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.

O item é uma matriz (máximo de apenas 1 elemento &mdash; atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object` . Esse bloco é necessário somente para soluções que oferecem uma experiência de bot.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64 caracteres|✔|O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Isso pode ser o mesmo que a ID de [aplicativo](#id)geral.|
|`scopes`|matriz de enums|3D|✔|Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`). Essas opções são não exclusivas.|
|`needsChannelSelector`|booliano|||Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico. Será **`false`**|
|`isNotificationOnly`|booliano|||Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa. Será `**false**`|
|`supportsFiles`|booliano|||Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal. Será **`false`**|
|`supportsCalling`|booliano|||Um valor que indica onde um bot dá suporte à chamada de áudio. **Importante**: esta propriedade é experimental no momento. As propriedades experimental podem não ser concluídas e podem sofrer alterações antes de ficarem totalmente disponíveis.  Ele é fornecido apenas para fins de teste e exploração, e não deve ser usado em aplicativos de produção. Será **`false`**|
|`supportsVideo`|booliano|||Um valor que indica onde um bot dá suporte à chamada de vídeo. **Importante**: esta propriedade é experimental no momento. As propriedades experimental podem não ser concluídas e podem sofrer alterações antes de ficarem totalmente disponíveis.  Ele é fornecido apenas para fins de teste e exploração, e não deve ser usado em aplicativos de produção. Será **`false`**|

### <a name="botscommandlists"></a>bots. commandLists

Uma lista opcional de comandos que seu bot pode recomendar aos usuários. O objeto é uma matriz (máximo de dois elementos) com todos os elementos do tipo `object` ; você deve definir uma lista de comandos separada para cada escopo que seu bot suporta. Consulte [menus de bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de enums|3D|✔|Especifica o escopo para o qual a lista de comandos é válida. As opção são `team`, `personal` e `groupchat`.|
|`items.commands`|matriz de objetos|10 |✔|Uma matriz de comandos que o bot suporta:<br>`title`: o nome do comando bot (cadeia, 32)<br>`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)|

### <a name="botscommandlistscommands"></a>bots. commandLists. Commands

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|title|string|12 |✔|O nome do comando do bot|
|description|string|128 caracteres|✔|Uma descrição de texto simples ou um exemplo da sintaxe de comando e seus argumentos.|

## <a name="connectors"></a>conectores

**Opcional** — array

O `connectors` bloco define um conector do Office 365 para o aplicativo.

O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Esse bloco é necessário somente para soluções que fornecem um conector.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔|A URL do https://a ser usada ao configurar o conector.|
|`scopes`|matriz de enums|1|✔|Especifica se o conector oferece uma experiência no contexto de um canal em uma `team` ou uma experiência com escopo para um usuário individual ( `personal` ). Atualmente, só `team` há suporte para o escopo.|
|`connectorId`|cadeia de caracteres|64 caracteres|✔|Um identificador exclusivo para o conector que corresponde à sua ID no [painel do desenvolvedor de conectores](https://aka.ms/connectorsdashboard).|

## <a name="composeextensions"></a>composeExtensions

**Opcional** — array

Define uma extensão de mensagens para o aplicativo.

> [!NOTE]
> O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem a funcionar.

O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Esse bloco é necessário somente para soluções que forneçam uma extensão de mensagens.

|Nome| Tipo | Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64|✔|A ID exclusiva do aplicativo da Microsoft para o bot que faz a extensão do sistema de mensagens, conforme registrado na estrutura do bot. Isso pode ser o mesmo que a ID de aplicativo geral.|
|`commands`|matriz de objetos|10 |✔|matriz de comandos que a extensão de mensagens oferece suporte|
|`canUpdateConfiguration`|booliano|||Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário. Padrão: **false**.|
|`messageHandlers`|matriz de objetos|5 ||Uma lista de manipuladores que permitem que os aplicativos sejam chamados quando determinadas condições são atendidas. Os domínios também devem ser listados no `validDomains`|
|`messageHandlers.type`|cadeia de caracteres|||O tipo de manipulador de mensagens. Deve ser `"link"`.|
|`messageHandlers.value.domains`|matriz de cadeias de caracteres|||matriz de domínios para o qual o manipulador de mensagens de link pode se registrar.|

### <a name="composeextensionscommands"></a>composeExtensions. Commands

Sua extensão de mensagens deve declarar um ou mais comandos. Cada comando aparece no Microsoft Teams como uma possível interação do ponto de entrada baseado na interface do usuário. Há um máximo de 10 comandos.

Cada item de comando é um objeto com a seguinte estrutura:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|64 caracteres|✔|A ID do comando.|
|`title`|cadeia de caracteres|32 caracteres|✔|O nome do comando amigável.|
|`type`|cadeia de caracteres|64 caracteres||Tipo do comando. Um `query` ou `action` . Padrão: **consulta**.|
|`description`|cadeia de caracteres|128 caracteres||A descrição que aparece para os usuários para indicar a finalidade desse comando.|
|`initialRun`|booliano|||Um valor Boolean que indica se o comando deve ser executado inicialmente sem parâmetros. Padrão: **false**.|
|`context`|matriz de cadeias de caracteres|3D||Define onde a extensão de mensagem pode ser chamada. Qualquer combinação de `compose` , `commandBox` , `message` . O padrão é `["compose","commandBox"]`.|
|`fetchTask`|booliano|||Um valor Boolean que indica se ele deve buscar o módulo de tarefa dinamicamente. Padrão: **false**.|
|`taskInfo`|objeto|||Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagem.|
|`taskInfo.title`|cadeia de caracteres|64 caracteres||Título inicial da caixa de diálogo.|
|`taskInfo.width`|cadeia de caracteres|||Largura da caixa de diálogo: um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '.|
|`taskInfo.height`|cadeia de caracteres|||Altura da caixa de diálogo-um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '.|
|`taskInfo.url`|cadeia de caracteres|||URL do WebView inicial.|
|`parameters`|matriz de objeto|5 itens|✔|A lista de parâmetros que o comando utiliza. Mínimo: 1; máximo: 5.|
|`parameters.name`|cadeia de caracteres|64 caracteres|✔|O nome do parâmetro conforme ele aparece no cliente. Isso é incluído na solicitação do usuário.|
|`parameters.title`|cadeia de caracteres|32 caracteres|✔|Título amigável para o parâmetro.|
|`parameters.description`|cadeia de caracteres|128 caracteres||Cadeia de caracteres amigável que descreve a finalidade deste parâmetro.|
|`parameters.value`|cadeia de caracteres|512 caracteres||Valor inicial para o parâmetro.|
|`parameters.inputType`|cadeia de caracteres|128 caracteres||Define o tipo de controle exibido em um módulo de tarefas para o `fetchTask: true` . Um de `text, textarea, number, date, time, toggle, choiceset` .|
|`parameters.choices`|matriz de objetos|10 itens||As opções de escolha para o `choiceset` . Use somente quando o `parameter.inputType` é `choiceset` .|
|`parameters.choices.title`|cadeia de caracteres|128 caracteres|✔|Título da escolha.|
|`parameters.choices.value`|cadeia de caracteres|512 caracteres|✔|O valor da escolha.|

## <a name="permissions"></a>permissões

**Opcional** — matriz de cadeias de caracteres

Uma matriz `string` que especifica quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão será executada. As opções a seguir são não exclusivas:

* `identity`&emsp;Requer informações de identidade do usuário
* `messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas para membros da equipe

A alteração dessas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado. Veja [atualização do seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) para obter mais informações.

## <a name="devicepermissions"></a>devicePermissions

**Opcional** — matriz de cadeias de caracteres

Especifica os recursos nativos no dispositivo de um usuário para o qual seu aplicativo pode solicitar acesso. As opções são:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Opcional**, exceto quando **necessário** , onde observado

Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do teams. As listagens de domínio podem incluir curingas, por exemplo `*.example.com` . Isso corresponde exatamente a um segmento do domínio; Se você precisar coincidir `a.b.example.com` e usar `*.*.example.com` . Se a configuração de sua guia ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além daquele usado para configuração de guia, esse domínio deverá ser especificado aqui.

No entanto, **não** é necessário incluir os domínios de provedores de identidade que você deseja suportar no seu aplicativo. Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve incluir o accounts.google.com no `validDomains[]` .

Aplicativos do teams que exigem suas próprias URLs do SharePoint para funcionar bem, podem incluir "{teamsitedomain}" em sua lista de domínios válida.

> [!IMPORTANT]
> Não adicione domínios que estejam fora do seu controle, seja diretamente ou via curingas. Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.

O objeto é uma matriz com todos os elementos do tipo `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Opcional** — objeto

Especifique a ID do aplicativo do Azure Active Directory (Azure AD) e as informações do Microsoft Graph para ajudar os usuários a entrarem diretamente no seu aplicativo. Se seu aplicativo estiver registrado no Azure AD, você deve fornecer a ID do aplicativo, para que os administradores possam facilmente revisar permissões e conceder consentimento no centro de administração do Microsoft Teams.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|36 caracteres|✔|ID do aplicativo AAD do aplicativo. Esta ID deve ser um GUID.|
|`resource`|cadeia de caracteres|2048 caracteres|✔|URL de recurso do aplicativo para aquisição de token de autenticação para SSO.|
|`applicationPermissions`|matriz de cadeia de caracteres|128 caracteres||Especificar [consentimento específico de recurso](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions) granular|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Opcional** — Boolean

Indica se o indicador de carregamento deve ou não ser mostrado quando um app/Tab é carregado. Padrão: **false**.
>[!NOTE]
>Se você definir "showLoadingIndicator: true" em seu manifesto de aplicativo, para que a página seja carregada corretamente, você deve modificar as páginas de conteúdo de suas guias e módulos de tarefa, de acordo com o protocolo descrito em [Mostrar um documento indicador de carregamento nativo](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) .


## <a name="isfullscreen"></a>isFullScreen

 **Opcional** — Boolean

Indicar onde um aplicativo pessoal é renderizado com ou sem uma barra de cabeçalho de tabulação. Padrão: **false**.

## <a name="activities"></a>activities

**Opcional** — objeto

Defina as propriedades que seu aplicativo usará para postar em um feed de atividades do usuário.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`activityTypes`|matriz de objetos|128 itens| | Especifique os tipos de atividades que seu aplicativo pode postar para um feed de atividades do usuário.|

### <a name="activitiesactivitytypes"></a>Activities. Activityfiles

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`type`|string|32 caracteres|✔|O tipo de notificação. *Veja abaixo*.|
|`description`|cadeia de caracteres|128 caracteres|✔|Uma breve descrição da notificação. *Veja abaixo*.|
|`templateText`|cadeia de caracteres|128 caracteres|✔|Ex: "{actor} tarefa criada {TaskId} para você"|

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
