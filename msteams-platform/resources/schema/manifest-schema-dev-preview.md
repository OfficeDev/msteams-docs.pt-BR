---
title: Referência de esquema de manifesto de visualização do desenvolvedor
description: Descreve o esquema apoiado pelo manifesto para Microsoft Teams
ms.topic: reference
keywords: equipes manifestam esquema Visualização desenvolvedor
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: b52d52f96312dc2978844b07a0f7ebb1d817166d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566702"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a>Esquema de manifesto de visualização de desenvolvedores para Microsoft Teams

> [!NOTE]
> Consulte [o Developer Preview](~/resources/dev-preview/developer-preview-intro.md) para obter informações sobre o programa e como você pode participar.
> Se você não estiver usando a visualização do desenvolvedor, você não deve usar esta versão do manifesto. Veja [Referência: Manifesto esquema para Microsoft Teams](~/resources/schema/manifest-schema.md) para a versão pública do manifesto.

O manifesto Microsoft Teams descreve como o aplicativo se integra ao produto Microsoft Teams. Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) .

Para obter mais informações sobre os recursos disponíveis, consulte: [Recursos na pré-visualização do desenvolvedor público para Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).

## <a name="sample-full-manifest"></a>Amostra de manifesto completo

```json
{
  "$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
  "manifestVersion": "devPreview",
  "version": "1.0.0",
  "id": "%MICROSOFT-APP-ID%",
  "packageName": "com.example.myapp",
  "devicePermissions" : [ "geolocation", "media" ],
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
      "scopes": [ "team", "groupchat" ]
    }
  ],
  "staticTabs": [
    {
      "entityId": "idForPage",
      "name": "Display name of tab",
      "contentUrl": "https://contoso.com/content?host=msteams",
      "websiteUrl": "https://contoso.com/content",
      "scopes": [ "personal" ]
    }
  ],
  "bots": [
    {
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "needsChannelSelector": false,
      "isNotificationOnly": false,
      "scopes": [ "team", "personal", "groupchat" ],
      "supportsFiles": true,
      "commandLists": [
        {
          "scopes": [ "team", "groupchat" ],
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
          "scopes": [ "personal", "groupchat" ],
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
      "scopes": [ "team"]
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
          "type" : "search",
          "context" : ["compose", "commandBox"],
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
          "type" : "action",
          "fetchTask" : true,
          "context" : ["message"],
          "parameters": [
            {
              "name": "custinfo",
              "title": "Customer name",
              "description": "Enter a customer name",
              "inputType" : "text"
            }
          ]
        },
        {
          "id": "exampleMessageHandler",
          "title": "Message Handler",
          "description": "Domains that will create a preview when pasted into the compose box",
          "messageHandlers": [
            {
              "type" : "link",
              "value" : {
                "domains" : [
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
    "messageTeamMembers",
  ],
  "validDomains": [
     "contoso.com",
     "mysite.someplace.com",
     "othersite.someplace.com"
  ],
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
  ],
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

*Opcional, mas recomendado* &ndash; corda

A URL https:// fazendo referência ao Esquema JSON para o manifesto.

## <a name="manifestversion"></a>manifestVersion

**Necessário** &ndash; corda

A versão do esquema manifesto que este manifesto está usando. Deve ser "devPreview".

## <a name="version"></a>versão

**Necessário** &ndash; corda

A versão do aplicativo específico. Se você atualizar algo em seu manifesto, a versão deve ser incrementada também. Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade. Se este aplicativo foi enviado para a loja, o novo manifesto terá que ser remetido e revalidado. Em seguida, os usuários deste app receberão o novo manifesto atualizado automaticamente em poucas horas, depois de aprovado.

Se o aplicativo solicitar a alteração das permissões, os usuários serão solicitados a atualizar e re consentir com o aplicativo.

Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (MAJOR. menor. PATCH).

## <a name="id"></a>id

**Necessário** &ndash; ID do aplicativo da Microsoft

O identificador exclusivo gerado pela Microsoft para este aplicativo. Se você registrou um bot através do Microsoft Bot Framework, ou o aplicativo web da sua guia já entra na Microsoft, você já deve ter um ID e deve inseri-lo aqui. Caso contrário, você deve gerar um novo ID no Portal de Registro de Aplicativos da Microsoft ([Meus Aplicativos), inseri-lo](https://apps.dev.microsoft.com)aqui e, em seguida, reutilizá-lo quando você [adicionar um bot](~/bots/how-to/create-a-bot-for-teams.md).

## <a name="packagename"></a>packageName

**Necessário** &ndash; corda

Um identificador exclusivo para este aplicativo em notação de domínio reverso; por exemplo, com.example.myapp.

## <a name="developer"></a>developer

**Required**

Especifica informações sobre sua empresa. Para aplicativos submetidos ao AppSource (anteriormente Office Store), esses valores devem corresponder às informações na sua entrada AppSource.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`name`|32 caracteres|✔|O nome de exibição para o desenvolvedor.|
|`websiteUrl`|2048 caracteres|✔|O https:// URL para o site do desenvolvedor. Este link deve levar os usuários para sua empresa ou página de landing específica do produto.|
|`privacyUrl`|2048 caracteres|✔|O https:// URL para a política de privacidade do desenvolvedor.|
|`termsOfUseUrl`|2048 caracteres|✔|O https:// URL para os termos de uso do desenvolvedor.|
|`mpnId`|10 caracteres|✔|**Opcional** O Microsoft Partner Network ID que identifica a organização parceira que está construindo o aplicativo.|

## <a name="localizationinfo"></a>localizaçãoInfo

**Opcional**

Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais. Veja [a localização.](~/concepts/build-and-test/apps-localization.md)

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`defaultLanguageTag`|4 caracteres|✔|A tag de idioma das strings neste arquivo manifesto de nível superior.|

### <a name="localizationinfoadditionallanguages"></a>localizaçãoInfo.additionalLíguas

Uma variedade de objetos especificando traduções adicionais de idiomas.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`languageTag`|4 caracteres|✔|A tag de idioma das strings no arquivo fornecido.|
|`file`|4 caracteres|✔|Um caminho relativo de arquivo para um arquivo .json contendo as strings traduzidas.|

## <a name="name"></a>nome

**Required**

O nome da experiência do seu aplicativo, exibido aos usuários na experiência Teams. Para aplicativos submetidos ao AppSource, esses valores devem corresponder às informações na sua entrada appSource. Os valores `short` de e não devem ser os `full` mesmos.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|30 caracteres|✔|O nome de exibição curto para o aplicativo.|
|`full`|100 caracteres||O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.|

## <a name="description"></a>descrição

**Required**

Descreve seu aplicativo para os usuários. Para aplicativos submetidos ao AppSource, esses valores devem corresponder às informações na sua entrada appSource.

Certifique-se de que sua descrição descreve com precisão sua experiência e fornece informações para ajudar os clientes em potencial a entender o que sua experiência faz. Você também deve observar, na descrição completa, se uma conta externa é necessária para uso. Os valores `short` de e não devem ser os `full` mesmos.  Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir qualquer outro nome do aplicativo.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|80 caracteres|✔|Uma breve descrição da sua experiência de aplicativo, usada quando o espaço é limitado.|
|`full`|4000 caracteres|✔|A descrição completa do seu aplicativo.|

## <a name="icons"></a>ícones

**Required**

Ícones usados no aplicativo Teams. Os arquivos de ícone devem ser incluídos como parte do pacote de upload.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`outline`|2048 caracteres|✔|Um caminho relativo de arquivo para um ícone transparente de contorno 32x32 PNG.|
|`color`|2048 caracteres|✔|Um caminho relativo de arquivo para um ícone PNG de cor completa 192x192.|

## <a name="accentcolor"></a>sotaqueColor

**Necessário** &ndash; corda

Uma cor para usar em conjunto com e como plano de fundo para seus ícones de contorno.

O valor deve ser um código de cor HTML válido começando com '#', por exemplo `#4464ee` .

## <a name="configurabletabs"></a>configurávelTabs

**Opcional**

Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração extra antes de ser adicionada. As guias configuráveis são suportadas apenas no escopo das equipes e, atualmente, apenas uma guia por aplicativo é suportada.

O objeto é uma matriz com todos os elementos do tipo `object` . Este bloco é necessário apenas para soluções que forneçam uma solução de guia de canal configurável.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|Cadeia de caracteres|2048 caracteres|✔|A https:// URL a ser usada ao configurar a guia.|
|`canUpdateConfiguration`|Booliano|||Um valor indicando se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. inadimplência: `true`|
|`scopes`|Matriz de enumeração|1|✔|Atualmente, as guias configuráveis suportam apenas os `team` `groupchat` escopos e escopos. |
|`sharePointPreviewImage`|Cadeia de caracteres|2048||Um caminho relativo de arquivo para uma imagem de visualização de guia para uso em SharePoint. Tamanho 1024x768. |
|`supportedSharePointHosts`|Matriz de enumeração|1||Define como sua guia será disponibilizada em SharePoint. As opções são `sharePointFullPage` e `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Opcional**

Define um conjunto de guias que podem ser "fixadas" por padrão, sem que o usuário as adicione manualmente. As guias estáticas declaradas no `personal` escopo são sempre fixadas à experiência pessoal do aplicativo. As guias estáticas declaradas no `team` escopo não são suportadas no momento.

O objeto é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` . Este bloco é necessário apenas para soluções que forneçam uma solução de guia estática.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|String|64 caracteres|✔|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|Cadeia de caracteres|128 caracteres|✔|O nome de exibição da guia na interface do canal.|
|`contentUrl`|Cadeia de caracteres|2048 caracteres|✔|A url https:// que aponta para a interface do usuário da entidade a ser exibida na tela Teams.|
|`websiteUrl`|Cadeia de caracteres|2048 caracteres||O https:// URL para apontar se um usuário optar por visualizar em um navegador.|
|`scopes`|Matriz de enumeração|1|✔|Atualmente, as guias estáticas suportam apenas o escopo, o `personal` que significa que ele só pode ser provisionado como parte da experiência pessoal.|

## <a name="bots"></a>Bots

**Opcional**

Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.

O objeto é uma matriz (no máximo 1 elemento &mdash; atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object` . Este bloco é necessário apenas para soluções que forneçam uma experiência de bot.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|String|64 caracteres|✔|O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Isso pode muito bem ser o mesmo que o [ID](#id)geral do aplicativo .|
|`needsChannelSelector`|Boolean|||Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico. inadimplência: `false`|
|`isNotificationOnly`|Boolean|||Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa. inadimplência: `false`|
|`supportsFiles`|Boolean|||Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal. inadimplência: `false`|
|`scopes`|Matriz de enumeração|3|✔|Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`). Essas opções são não exclusivas.|

### <a name="botscommandlists"></a>bots.commandLists

Uma lista opcional de comandos que o bot pode recomendar aos usuários. O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo ; você deve definir uma lista de `object` comando separada para cada escopo que o seu bot suporta. Para obter mais informações, consulte [menus bot](~/bots/how-to/create-a-bot-commands-menu.md).

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de enumeração|3|✔|Especifica o escopo para o qual a lista de comandos é válida. As opção são `team`, `personal` e `groupchat`.|
|`items.commands`|matriz de objetos|10 |✔|Uma matriz de comandos que o bot suporta:<br>`title`: o nome do comando do bot (string, 32).<br>`description`: uma descrição simples ou exemplo da sintaxe de comando e seu argumento (string, 128).|

## <a name="connectors"></a>Conectores

**Opcional**

O `connectors` bloco define um conector de Office 365 para o aplicativo.

O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Este bloco é necessário apenas para soluções que forneçam um Conector.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|Cadeia de caracteres|2048 caracteres|✔|A https:// URL para usar ao configurar o conector.|
|`connectorId`|String|64 caracteres|✔|Um identificador exclusivo para o Conector que corresponde ao seu ID no [Painel de Desenvolvedores de Conectores](https://aka.ms/connectorsdashboard).|
|`scopes`|Matriz de enumeração|1|✔|Especifica se o Conector oferece uma experiência no contexto de um canal em um `team` , ou uma experiência escopo para um usuário individual `personal` (). Atualmente, apenas o `team` escopo é suportado.|

## <a name="composeextensions"></a>comporTensões

**Opcional**

Define uma extensão de mensagens para o aplicativo.

> [!NOTE]
> O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome manifesto permanece o mesmo para que as extensões existentes continuem funcionando.

O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Este bloco é necessário apenas para soluções que forneçam uma extensão de mensagens.

|Nome| Tipo | Tamanho Máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|Cadeia de caracteres|64|✔|O ID exclusivo do aplicativo da Microsoft para o bot que apoia a extensão de mensagens, como registrado no Bot Framework. Isso pode muito bem ser o mesmo que o [ID](#id)geral do aplicativo .|
|`canUpdateConfiguration`|Booliano|||Um valor indicando se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário. O padrão é `false`.|
|`commands`|Matriz de objetos|10 |✔|Matriz de comandos que a extensão de mensagens suporta|

### <a name="composeextensionscommands"></a>comporExtensions.commands

Sua extensão de mensagens deve declarar um ou mais comandos. Cada comando aparece em Microsoft Teams como uma interação potencial do ponto de entrada baseado em interface do usuário. Há um máximo de 10 comandos.

Cada item de comando é um objeto com a seguinte estrutura:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|String|64 caracteres|✔|A responsabilidade pelo comando.|
|`type`|String|64 caracteres||Tipo de comando. Um de `query` ou `action` . inadimplência: `query`|
|`title`|Cadeia de caracteres|32 caracteres|✔|O nome de comando fácil de usar.|
|`description`|Cadeia de caracteres|128 caracteres||A descrição que aparece aos usuários para indicar o propósito deste comando.|
|`initialRun`|Booliano|||Um valor booleano que indica se o comando deve ser executado inicialmente sem parâmetros. inadimplência: `false`|
|`context`|Matriz de cadeias de caracteres|3||Define de onde a extensão da mensagem pode ser invocada. Qualquer combinação `compose` `commandBox` de, `message` . . Padrão é `["compose", "commandBox"]`|
|`fetchTask`|Booliano|||Um valor booleano que indica se ele deve buscar o módulo de tarefa dinamicamente.|
|`taskInfo`|Objeto|||Especifique o módulo de tarefa para pré-carregar ao usar um comando de extensão de mensagens.|
|`taskInfo.title`|Cadeia de caracteres|64||Título de diálogo inicial.|
|`taskInfo.width`|Cadeia de caracteres|||Largura de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.height`|Cadeia de caracteres|||Altura de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'.|
|`taskInfo.url`|Cadeia de caracteres|||URL inicial do webview.|
|`messageHandlers`|Matriz de Objetos|5 ||Uma lista de manipuladores que permitem que os aplicativos sejam invocados quando determinadas condições são atendidas. Os domínios também devem ser listados em `validDomains` .|
|`messageHandlers.type`|Cadeia de caracteres|||O tipo de manipulador de mensagens. Deve ser `"link"`.|
|`messageHandlers.value.domains`|Matriz de cadeias de caracteres|||Matriz de domínios para os que o manipulador de mensagens de link pode registrar.|
|`parameters`|Matriz de objetos|5 |✔|A lista de parâmetros que o comando toma. Mínimo: 1; máximo: 5|
|`parameter.name`|String|64 caracteres|✔|O nome do parâmetro como aparece no cliente. Isso está incluído na solicitação do usuário.|
|`parameter.title`|Cadeia de caracteres|32 caracteres|✔|Título fácil de usar para o parâmetro.|
|`parameter.description`|Cadeia de caracteres|128 caracteres||String fácil de usar que descreve o propósito deste parâmetro.|
|`parameter.inputType`|Cadeia de caracteres|128 caracteres||Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` . Um `text` `textarea` deles, `number` , , , , `date` `time` `toggle` `choiceset` .|
|`parameter.choices`|Matriz de Objetos|10 ||As opções de escolha para o `choiceset` . Use somente quando `parameter.inputType` estiver `choiceset` .|
|`parameter.choices.title`|Cadeia de caracteres|128||O título da escolha.|
|`parameter.choices.value`|Cadeia de caracteres|512||O valor da escolha.|

## <a name="permissions"></a>permissões

**Opcional**

Um conjunto especifica `string` quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão será real. As seguintes opções não são exclusivas:

* `identity`&emsp;Requer informações de identidade do usuário.
* `messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe.

Alterar essas permissões ao atualizar seu aplicativo fará com que seus usuários repitam o processo de consentimento na primeira vez que executarem o aplicativo atualizado.

## <a name="devicepermissions"></a>dispositivosPermissões

**Opcional** Matriz de Cordas

Especifica os recursos nativos no dispositivo do usuário aos quais seu aplicativo pode solicitar acesso. As opções são:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Opcional**, exceto **Necessário** quando observado

Uma lista de domínios válidos dos quais o aplicativo espera carregar qualquer conteúdo. As listagens de domínio podem incluir curingas, por `*.example.com` exemplo. Isso corresponde exatamente a um segmento do domínio; se você precisar `a.b.example.com` combinar, então use `*.*.example.com` . Se a configuração da guia ou a interface do conteúdo precisar navegar para qualquer outro domínio além do uso para configuração de guia, esse domínio deve ser especificado aqui.

No entanto, **não** é necessário incluir os domínios dos provedores de identidade que você deseja suportar em seu aplicativo. Por exemplo, para autenticar usando um ID do Google, é necessário redirecionar para accounts.google.com, mas você não deve incluir accounts.google.com em `validDomains[]` .

> [!IMPORTANT]
> Não adicione domínios que estejam fora do seu controle, diretamente ou através de curingas. Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.

O objeto é uma matriz com todos os elementos do tipo `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Opcional**

Especifique seu ID do aplicativo AAD e Graph informações para ajudar os usuários a entrar perfeitamente em seu aplicativo AAD.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|Cadeia de caracteres|36 caracteres|✔|ID de aplicativo AAD do aplicativo. Esta id deve ser uma GUID.|
|`resource`|Cadeia de caracteres|2048 caracteres|✔|Url de recurso do aplicativo para aquisição de token auth para SSO.|

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

