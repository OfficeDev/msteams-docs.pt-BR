---
title: Referência de esquema de manifesto
description: Descreve o esquema de manifesto do Microsoft Teams
keywords: esquema de manifesto do teams
author: laujan
ms.author: lajanuar
ms.openlocfilehash: 17626df3aa4b076190413c67d9a0ecd7cd2eed31
ms.sourcegitcommit: 4275a502f9f7742da2900c79e19551e481c9e48a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797049"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referência: esquema de manifesto para o Microsoft Teams

O manifesto do Microsoft Teams descreve como o aplicativo se integra ao produto Microsoft Teams. Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json) . As versões anteriores 1.0-1.4 também têm suporte (usando "v1.x" na URL).

O exemplo de esquema a seguir mostra todas as opções de extensibilidade.

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

*Opcional, mas recomendado cadeia de* caracteres

A https:// URL que referencia o esquema JSON para o manifesto.

## <a name="manifestversion"></a>manifestVersion

**Obrigatório —** cadeia de caracteres

A versão do esquema de manifesto que este manifesto está usando. Deve ser "1.7".

## <a name="version"></a>versão

**Obrigatório —** cadeia de caracteres

A versão do aplicativo específico. Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada. Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade. Se esse aplicativo foi enviado para a loja, o novo manifesto terá que ser re-enviado e revalidado. Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, depois que ele for aprovado.

Se o aplicativo solicitou a alteração de permissões, os usuários serão solicitados a atualizar e consentir de novo para o aplicativo.

Esta cadeia de caracteres de versão deve seguir [o padrão de semver](http://semver.org/) (MAJOR. MINOR. PATCH).

## <a name="id"></a>id

**Obrigatório —** ID do aplicativo da Microsoft

O identificador exclusivo gerado pela Microsoft para este aplicativo. Se você registrou um bot por meio do Microsoft Bot Framework ou se o aplicativo Web da guia já entra na Microsoft, você já deve ter uma ID e deve insira-a aqui. Caso contrário, você deve gerar uma nova ID no Portal de Registro de Aplicativos da Microsoft[(Meus](https://apps.dev.microsoft.com)Aplicativos), insira-a aqui e, em seguida, reutilizar ao adicionar um bot. Observação: se você estiver enviando uma atualização para seu aplicativo existente no AppSource, a ID em seu manifesto não deverá ser modificada.

## <a name="developer"></a>developer

**Obrigatório —** objeto

Especifica informações sobre sua empresa. Para aplicativos enviados ao AppSource (antigo Office Store), esses valores devem corresponder às informações em sua entrada do AppSource. Consulte nossas [diretrizes de publicação para](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) obter informações adicionais.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`name`|32 caracteres|✔|O nome de exibição do desenvolvedor.|
|`websiteUrl`|2048 caracteres|✔|A https:// URL para o site do desenvolvedor. Este link deve levar os usuários para a sua empresa ou página de aterrissagem específica do produto.|
|`privacyUrl`|2048 caracteres|✔|A https:// URL da política de privacidade do desenvolvedor.|
|`termsOfUseUrl`|2048 caracteres|✔|A https:// URL para os termos de uso do desenvolvedor.|
|`mpnId`|10 caracteres| |**Opcional** A ID do Microsoft Partner Network que identifica a organização parceira que está criando o aplicativo.|

## <a name="name"></a>nome

**Obrigatório —** objeto

O nome da experiência do seu aplicativo, exibido aos usuários na experiência do Teams. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada do AppSource. Os valores `short` e não devem ser os `full` mesmos.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|30 caracteres|✔|O nome de exibição curto do aplicativo.|
|`full`|100 caracteres||O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.|

## <a name="description"></a>description

**Obrigatório —** objeto

Descreve seu aplicativo para os usuários. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada do AppSource.

Certifique-se de que sua descrição descreva com precisão sua experiência e fornece informações para ajudar clientes potenciais a entender o que sua experiência faz. Você também deve observar, na descrição completa, se uma conta externa for necessária para uso. Os valores `short` e não devem ser os `full` mesmos.  Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir qualquer outro nome de aplicativo.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|80 caracteres|✔|Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.|
|`full`|4.000 caracteres|✔|A descrição completa do seu aplicativo.|

## <a name="packagename"></a>packageName

**Opcional** — cadeia de caracteres

Um identificador exclusivo para este aplicativo na notação de domínio reverso; por exemplo, com.example.myapp. Comprimento máximo: 64 caracteres.

## <a name="localizationinfo"></a>localizationInfo

**Opcional** — objeto

Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais. Consulte [localização](~/concepts/build-and-test/apps-localization.md).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`defaultLanguageTag`||✔|A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Uma matriz de objetos especificando traduções de idiomas adicionais.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`languageTag`||✔|A marca de idioma das cadeias de caracteres no arquivo fornecido.|
|`file`||✔|Um caminho de arquivo relativo para um arquivo .json que contém as cadeias de caracteres traduzidas.|

## <a name="icons"></a>ícones

**Obrigatório —** objeto

Ícones usados no aplicativo Teams. Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento. Consulte [Ícones](../../concepts/build-and-test/apps-package.md#app-icons) para obter mais informações.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`outline`|32 x 32 pixels|✔|Um caminho de arquivo relativo para um ícone transparente de contorno PNG de 32 x 32.|
|`color`|192 x 192 pixels|✔|Um caminho de arquivo relativo para um ícone PNG de 192 x 192 cores completas.|

## <a name="accentcolor"></a>accentColor

**Opcional** — código de cor HEX HTML

Uma cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.

O valor deve ser um código de cor HTML válido começando com '#', por `#4464ee` exemplo.

## <a name="configurabletabs"></a>configurableTabs

**Opcional** — matriz

Usado quando a experiência do aplicativo tem uma experiência de guia de canal de equipe que exige configuração extra antes de ser adicionada. Guias configuráveis só têm suporte no escopo das equipes  (não pessoal) e, atualmente, só há suporte para uma guia por aplicativo.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔|A https:// URL a ser usada ao configurar a guia.|
|`scopes`|matriz de enums|1 |✔|Atualmente, as guias configuráveis suportam apenas `team` os `groupchat` escopos e os escopos. |
|`canUpdateConfiguration`|booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Padrão: **true**.|
|`context` |matriz de enums|6 ||O conjunto de `contextItem` escopos nos quais há suporte para uma guia. Padrão: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|string|2048||Um caminho de arquivo relativo para uma imagem de visualização de guia para uso no SharePoint. Tamanho 1024x768. |
|`supportedSharePointHosts`|matriz de enums|1 ||Define como sua guia será disponibilizada no SharePoint. As opções `sharePointFullPage` são e `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Opcional** — matriz

Define um conjunto de guias que podem ser "fixadas" por padrão, sem que o usuário as adicione manualmente. As guias estáticas declaradas `personal` no escopo são sempre fixadas à experiência pessoal do aplicativo. Atualmente, as guias estáticas declaradas no escopo `team` não são suportadas.

Este item é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` . Esse bloco é necessário apenas para soluções que fornecem uma solução de guia estática.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|string|64 caracteres|✔|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|string|128 caracteres|✔|O nome de exibição da guia na interface do canal.|
|`contentUrl`|string||✔|A https:// URL que aponta para a interface do usuário da entidade a ser exibida na tela do Teams.|
|`websiteUrl`|string|||A https:// URL para apontar se um usuário optar por exibir em um navegador.|
|`searchUrl`|string|||A https:// URL a ser apontada para as consultas de pesquisa de um usuário.|
|`scopes`|matriz de enums|1 |✔|Atualmente, as guias estáticas suportam apenas o escopo, o que significa que ele só pode ser provisionado como `personal` parte da experiência pessoal.|
|`context` | matriz de enums| 2 || O conjunto de `contextItem` escopos nos quais há suporte para uma guia.|

> [!NOTE]
> Se suas guias exigem informações dependentes de contexto para exibir  conteúdo relevante ou para iniciar um fluxo de autenticação, confira Obter contexto para sua [guia do Microsoft Teams.](../../tabs/how-to/access-teams-context.md)

## <a name="bots"></a>bots

**Opcional** — matriz

Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.

O item é uma matriz (máximo de apenas 1 elemento atualmente apenas um bot é permitido por aplicativo) com todos os &mdash; elementos do tipo `object` . Esse bloco é necessário apenas para soluções que fornecem uma experiência de bot.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64 caracteres|✔|O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Isso pode ser o mesmo que a ID geral [do aplicativo.](#id)|
|`scopes`|matriz de enums|3 |✔|Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`). Essas opções são não exclusivas.|
|`needsChannelSelector`|booliano|||Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico. Padrão: **`false`**|
|`isNotificationOnly`|booliano|||Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa. Padrão: **`false`**|
|`supportsFiles`|booliano|||Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal. Padrão: **`false`**|
|`supportsCalling`|booliano|||Um valor indicando onde um bot dá suporte a chamada de áudio. **IMPORTANTE:** esta propriedade é experimental no momento. As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.  Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção. Padrão: **`false`**|
|`supportsVideo`|booliano|||Um valor indicando onde um bot dá suporte à chamada de vídeo. **IMPORTANTE:** essa propriedade é experimental no momento. As propriedades experimentais podem não estar completas e podem sofrer alterações antes de se tornarem totalmente disponíveis.  Ele é fornecido apenas para fins de teste e exploração e não deve ser usado em aplicativos de produção. Padrão: **`false`**|

### <a name="botscommandlists"></a>bots.commandLists

Uma lista opcional de comandos que seu bot pode recomendar aos usuários. O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo; você deve definir uma lista de comandos separada para cada escopo ao qual seu `object` bot oferece suporte. Consulte [menus de bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de enums|3 |✔|Especifica o escopo para o qual a lista de comandos é válida. As opção são `team`, `personal` e `groupchat`.|
|`items.commands`|matriz de objetos|10 |✔|Uma matriz de comandos que o bot suporta:<br>`title`: o nome do comando bot (cadeia, 32)<br>`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)|

### <a name="botscommandlistscommands"></a>bots.commandLists.commands

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|title|string|12 |✔|O nome do comando de bot|
|description|string|128 caracteres|✔|Uma descrição de texto simples ou um exemplo da sintaxe do comando e seus argumentos.|

## <a name="connectors"></a>conectores

**Opcional** — matriz

O `connectors` bloco define um Conector do Office 365 para o aplicativo.

O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Esse bloco é necessário apenas para soluções que fornecem um Conector.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|string|2048 caracteres|✔|A https:// URL a ser usada ao configurar o conector.|
|`scopes`|matriz de enums|1 |✔|Especifica se o Conector oferece uma experiência no contexto de um canal em um , ou uma experiência com escopo `team` para um usuário individual sozinho ( `personal` ). Atualmente, apenas o `team` escopo é suportado.|
|`connectorId`|string|64 caracteres|✔|Um identificador exclusivo para o Conector que corresponde a sua ID no [Painel do Desenvolvedor de Conectores.](https://aka.ms/connectorsdashboard)|

## <a name="composeextensions"></a>composeExtensions

**Opcional** — matriz

Define uma extensão de mensagens para o aplicativo.

> [!NOTE]
> O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem a funcionar.

O item é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Esse bloqueio é necessário apenas para soluções que fornecem uma extensão de mensagens.

|Nome| Tipo | Tamanho Máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|string|64|✔|A ID exclusiva do aplicativo da Microsoft para o bot que é o suporte à extensão de mensagens, conforme registrado na Estrutura do Bot. Isso pode ser o mesmo que a ID geral do aplicativo.|
|`commands`|matriz de objetos|10 |✔|matriz de comandos com suporte da extensão de mensagens|
|`canUpdateConfiguration`|booliano|||Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário. Padrão: **false**.|
|`messageHandlers`|matriz de objetos|5 ||Uma lista de manipuladores que permitem que aplicativos sejam invocados quando determinadas condições são atendidas. Os domínios também devem estar listados em `validDomains`|
|`messageHandlers.type`|string|||O tipo de manipulador de mensagens. Deve ser `"link"`.|
|`messageHandlers.value.domains`|matriz de cadeias de caracteres|||matriz de domínios que o manipulador de mensagens de link pode registrar.|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Sua extensão de mensagens deve declarar um ou mais comandos. Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário. Há um máximo de 10 comandos.

Cada item de comando é um objeto com a seguinte estrutura:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|64 caracteres|✔|A ID do comando.|
|`title`|string|32 caracteres|✔|O nome do comando amigável.|
|`type`|string|64 caracteres||Tipo do comando. Um ou `query` `action` . Padrão: **consulta**.|
|`description`|string|128 caracteres||A descrição que aparece para os usuários para indicar a finalidade desse comando.|
|`initialRun`|booliano|||Um valor booliana que indica se o comando deve ser executado inicialmente sem parâmetros. Padrão: **false**.|
|`context`|matriz de cadeias de caracteres|3 ||Define de onde a extensão da mensagem pode ser invocada. Qualquer combinação de `compose` , `commandBox` `message` . O padrão é `["compose","commandBox"]`.|
|`fetchTask`|booliano|||Um valor booliana que indica se ele deve buscar o módulo de tarefa dinamicamente. Padrão: **false**.|
|`taskInfo`|objeto|||Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens.|
|`taskInfo.title`|string|64 caracteres||Título da caixa de diálogo inicial.|
|`taskInfo.width`|string|||Largura da caixa de diálogo - um número em pixels ou layout padrão, como "grande", "médio" ou "pequeno".|
|`taskInfo.height`|string|||Altura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.url`|string|||URL inicial do webview.|
|`parameters`|matriz de objeto|5 itens|✔|A lista de parâmetros que o comando leva. Mínimo: 1; máximo: 5.|
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

Uma matriz que especifica quais permissões o aplicativo solicita, o que permite que os usuários `string` finais saibam como a extensão será efetivada. As seguintes opções não são exclusivas:

* `identity`&emsp;Requer informações de identidade do usuário
* `messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe

Alterar essas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado. Consulte [Atualizando seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) para obter mais informações.

## <a name="devicepermissions"></a>devicePermissions

**Opcional** — matriz de cadeias de caracteres

Especifica os recursos nativos no dispositivo de um usuário aos que seu aplicativo pode solicitar acesso. As opções são:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, except **Required** where noted

Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do Teams. As listagem de domínio podem incluir caracteres curinga, por `*.example.com` exemplo. Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` . Se a configuração da guia ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para a configuração de guia, esse domínio deverá ser especificado aqui.

No **entanto,** não é necessário incluir os domínios de provedores de identidade que você deseja suportar em seu aplicativo. Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve incluir accounts.google.com em `validDomains[]` .

Os aplicativos do Teams que exigem suas próprias URLs do SharePoint para funcionarem bem podem incluir "{teamsitedomain}" em sua lista de domínios válida.

> [!IMPORTANT]
> Não adicione domínios que estejam fora do seu controle, diretamente ou por meio de caracteres curinga. Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.

O objeto é uma matriz com todos os elementos do tipo `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Opcional** — objeto

Especifique a ID do aplicativo do Azure Active Directory (Azure AD) e as informações do Microsoft Graph para ajudar os usuários a entrar facilmente em seu aplicativo. Se seu aplicativo estiver registrado no Azure AD, você deverá fornecer a ID do aplicativo, para que os administradores possam analisar facilmente as permissões e conceder consentimento no centro de administração do Teams.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|string|36 caracteres|✔|ID do aplicativo AAD do aplicativo. Essa ID deve ser um GUID.|
|`resource`|string|2048 caracteres|✔|URL do recurso do aplicativo para aquisição de token de autenticação para SSO. </br> **OBSERVAÇÃO:** Se você não estiver usando o SSO, certifique-se de inserir um valor fictício de cadeia de caracteres nesse campo para o manifesto do aplicativo, por exemplo, para https://notapplicable evitar uma resposta de erro. |
|`applicationPermissions`|matriz de cadeia de caracteres|128 caracteres||Especifique o [consentimento específico do recurso granular.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Opcional** — booleano

Indica se o indicador de carregamento será ou não mostre quando um aplicativo/guia estiver sendo carregado. Padrão: **false**.
>[!NOTE]
>Se você definir "showLoadingIndicator : true" no manifesto do aplicativo, para [que a](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) página seja carregada corretamente, modifique as páginas de conteúdo de suas guias e módulos de tarefa de acordo com o protocolo descrito em Mostrar um documento indicador de carregamento nativo.


## <a name="isfullscreen"></a>isFullScreen

 **Opcional** — booleano

Indica onde um aplicativo pessoal é renderizado com ou sem uma barra de controle guia. Padrão: **false**.

## <a name="activities"></a>activities

**Opcional** — objeto

Defina as propriedades que seu aplicativo usará para postar em um feed de atividades do usuário.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`activityTypes`|matriz de objetos|128 itens| | Especifique os tipos de atividades que seu aplicativo pode postar em um feed de atividades de usuários.|

### <a name="activitiesactivitytypes"></a>activities.activityTypes

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`type`|string|32 caracteres|✔|O tipo de notificação. *Veja abaixo.*|
|`description`|string|128 caracteres|✔|Uma breve descrição da notificação. *Veja abaixo.*|
|`templateText`|string|128 caracteres|✔|Por exemplo: "{actor} criou a tarefa {taskId} para você"|

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
