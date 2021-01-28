---
title: Referência do esquema de manifesto do Developer Preview
description: Descreve o esquema com suporte no manifesto do Microsoft Teams
ms.topic: reference
keywords: teams manifest schema Developer Preview
ms.date: 05/20/2019
ms.openlocfilehash: 0776ced1704f46c95054308c8a1898ed938e47cb
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014100"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a>Esquema de manifesto da visualização do desenvolvedor para o Microsoft Teams

> [!NOTE]
> Consulte [a Visualização](~/resources/dev-preview/developer-preview-intro.md) do Desenvolvedor para obter informações sobre o programa e como você pode participar.
> Se você não estiver usando a visualização do desenvolvedor, não deverá usar essa versão do manifesto. Consulte [Referência: Esquema de manifesto do Microsoft Teams](~/resources/schema/manifest-schema.md) para a versão pública do manifesto.

O manifesto do Microsoft Teams descreve como o aplicativo se integra ao produto Microsoft Teams. Seu manifesto deve estar em conformidade com o esquema hospedado em [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) .

Para obter mais informações sobre os recursos disponíveis, consulte: [Recursos na Visualização pública do desenvolvedor para o Microsoft Teams.](~/resources/dev-preview/developer-preview-features.md)

## <a name="sample-full-manifest"></a>Exemplo de manifesto completo

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
  ]
}
```

O esquema define as seguintes propriedades:

## <a name="schema"></a>$schema

*Opcional, mas recomendado* &ndash; Cadeia de caracteres

A https:// URL que referencia o esquema JSON para o manifesto.

## <a name="manifestversion"></a>manifestVersion

**Obrigatório** &ndash; Cadeia de caracteres

A versão do esquema de manifesto que este manifesto está usando. Ele deve ser "devPreview".

## <a name="version"></a>versão

**Obrigatório** &ndash; Cadeia de caracteres

A versão do aplicativo específico. Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada. Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade. Se esse aplicativo foi enviado para a loja, o novo manifesto terá que ser re-enviado e revalidado. Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, depois que ele for aprovado.

Se o aplicativo solicitou a alteração de permissões, os usuários serão solicitados a atualizar e consentir de novo para o aplicativo.

Esta cadeia de caracteres de versão deve seguir [o padrão de semver](http://semver.org/) (MAJOR. MINOR. PATCH).

## <a name="id"></a>id

**Obrigatório** &ndash; ID do aplicativo da Microsoft

O identificador exclusivo gerado pela Microsoft para este aplicativo. Se você registrou um bot por meio do Microsoft Bot Framework ou se o aplicativo Web da guia já entra na Microsoft, você já deve ter uma ID e deve insira-a aqui. Caso contrário, você deve gerar uma nova ID no Portal de Registro de Aplicativos da Microsoft[(Meus](https://apps.dev.microsoft.com)Aplicativos), insira-a aqui e reutilizar ao adicionar [um bot.](~/bots/how-to/create-a-bot-for-teams.md)

## <a name="packagename"></a>packageName

**Obrigatório** &ndash; Cadeia de caracteres

Um identificador exclusivo para este aplicativo na notação de domínio reverso; por exemplo, com.example.myapp.

## <a name="developer"></a>developer

**Required**

Especifica informações sobre sua empresa. Para aplicativos enviados ao AppSource (antigo Office Store), esses valores devem corresponder às informações em sua entrada do AppSource.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`name`|32 caracteres|✔|O nome de exibição do desenvolvedor.|
|`websiteUrl`|2048 caracteres|✔|A https:// URL para o site do desenvolvedor. Este link deve levar os usuários para a sua empresa ou página de aterrissagem específica do produto.|
|`privacyUrl`|2048 caracteres|✔|A https:// URL da política de privacidade do desenvolvedor.|
|`termsOfUseUrl`|2048 caracteres|✔|A https:// URL para os termos de uso do desenvolvedor.|
|`mpnId`|10 caracteres|✔|**Opcional** A ID do Microsoft Partner Network que identifica a organização parceira que está criando o aplicativo.|

## <a name="localizationinfo"></a>localizationInfo

**Opcional**

Permite a especificação de um idioma padrão, bem como ponteiros para arquivos de idioma adicionais. Consulte [localização](~/concepts/build-and-test/apps-localization.md).

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`defaultLanguageTag`|4 caracteres|✔|A marca de idioma das cadeias de caracteres neste arquivo de manifesto de nível superior.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Uma matriz de objetos especificando traduções de idiomas adicionais.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`languageTag`|4 caracteres|✔|A marca de idioma das cadeias de caracteres no arquivo fornecido.|
|`file`|4 caracteres|✔|Um caminho de arquivo relativo para um arquivo .json que contém as cadeias de caracteres traduzidas.|

## <a name="name"></a>nome

**Required**

O nome da experiência do seu aplicativo, exibido aos usuários na experiência do Teams. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada do AppSource. Os valores `short` e não devem ser os `full` mesmos.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|30 caracteres|✔|O nome de exibição curto do aplicativo.|
|`full`|100 caracteres||O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.|

## <a name="description"></a>descrição

**Required**

Descreve seu aplicativo para os usuários. Para aplicativos enviados ao AppSource, esses valores devem corresponder às informações em sua entrada do AppSource.

Certifique-se de que sua descrição descreva com precisão sua experiência e fornece informações para ajudar clientes potenciais a entender o que sua experiência faz. Você também deve observar, na descrição completa, se uma conta externa for necessária para uso. Os valores `short` e não devem ser os `full` mesmos.  Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir qualquer outro nome de aplicativo.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|80 caracteres|✔|Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.|
|`full`|4.000 caracteres|✔|A descrição completa do seu aplicativo.|

## <a name="icons"></a>ícones

**Required**

Ícones usados no aplicativo Teams. Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`outline`|2048 caracteres|✔|Um caminho de arquivo relativo para um ícone transparente de contorno PNG de 32 x 32.|
|`color`|2048 caracteres|✔|Um caminho de arquivo relativo para um ícone PNG de 192 x 192 cores completas.|

## <a name="accentcolor"></a>accentColor

**Obrigatório** &ndash; Cadeia de caracteres

Uma cor a ser usada em conjunto com e como plano de fundo para seus ícones de contorno.

O valor deve ser um código de cor HTML válido começando com '#', por `#4464ee` exemplo.

## <a name="configurabletabs"></a>configurableTabs

**Opcional**

Usado quando a experiência do aplicativo tem uma experiência de guia de canal de equipe que exige configuração extra antes de ser adicionada. Guias configuráveis são suportadas apenas no escopo de equipes e, atualmente, só há suporte para uma guia por aplicativo.

O objeto é uma matriz com todos os elementos do tipo `object` . Esse bloco é necessário apenas para soluções que fornecem uma solução de guia de canal configurável.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|Cadeia de caracteres|2048 caracteres|✔|A https:// URL a ser usada ao configurar a guia.|
|`canUpdateConfiguration`|Booliano|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Padrão: `true`|
|`scopes`|Matriz de enumeração|1 |✔|Atualmente, as guias configuráveis suportam apenas `team` os `groupchat` escopos e os escopos. |
|`sharePointPreviewImage`|Cadeia de Caracteres|2048||Um caminho de arquivo relativo para uma imagem de visualização de guia para uso no SharePoint. Tamanho 1024x768. |
|`supportedSharePointHosts`|Matriz de enumeração|1 ||Define como sua guia será disponibilizada no SharePoint. As opções `sharePointFullPage` são e `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Opcional**

Define um conjunto de guias que podem ser "fixadas" por padrão, sem que o usuário as adicione manualmente. As guias estáticas declaradas `personal` no escopo são sempre fixadas à experiência pessoal do aplicativo. As guias estáticas declaradas no `team` escopo não são suportadas no momento.

O objeto é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object` . Esse bloco é necessário apenas para soluções que fornecem uma solução de guia estática.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|String|64 caracteres|✔|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|Cadeia de Caracteres|128 caracteres|✔|O nome de exibição da guia na interface do canal.|
|`contentUrl`|Cadeia de Caracteres|2048 caracteres|✔|A https:// URL que aponta para a interface do usuário da entidade a ser exibida na tela do Teams.|
|`websiteUrl`|Cadeia de Caracteres|2048 caracteres||A https:// URL para apontar se um usuário optar por exibir em um navegador.|
|`scopes`|Matriz de enumeração|1 |✔|Atualmente, as guias estáticas suportam apenas o escopo, o que significa que ele só pode ser provisionado como `personal` parte da experiência pessoal.|

## <a name="bots"></a>bots

**Opcional**

Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.

O objeto é uma matriz (máximo de apenas 1 elemento atualmente apenas um bot é permitido por aplicativo) com todos os &mdash; elementos do tipo `object` . Esse bloco é necessário apenas para soluções que fornecem uma experiência de bot.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|String|64 caracteres|✔|O ID exclusivo do aplicativo Microsoft para o bot conforme registrado na estrutura do bot. Isso pode ser o mesmo que a ID geral [do aplicativo.](#id)|
|`needsChannelSelector`|Boolean|||Descreve se o bot usa ou não uma dica de usuário para adicionar o bot a um canal específico. Padrão: `false`|
|`isNotificationOnly`|Boolean|||Indica se um bot é um bot unidirecional, somente para notificação, em vez de um bot de conversa. Padrão: `false`|
|`supportsFiles`|Boolean|||Indica se o bot é compatível com a capacidade de carregar/baixar arquivos em chat pessoal. Padrão: `false`|
|`scopes`|Matriz de enumeração|3|✔|Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência delimitada apenas a um usuário individual (`personal`). Essas opções são não exclusivas.|

### <a name="botscommandlists"></a>bots.commandLists

Uma lista opcional de comandos que seu bot pode recomendar aos usuários. O objeto é uma matriz (máximo de 2 elementos) com todos os elementos do tipo; você deve definir uma lista de comandos separada para cada escopo ao qual seu `object` bot oferece suporte. Consulte [menus de bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de enumeração|3|✔|Especifica o escopo para o qual a lista de comandos é válida. As opção são `team`, `personal` e `groupchat`.|
|`items.commands`|matriz de objetos|10 |✔|Uma matriz de comandos que o bot suporta:<br>`title`: o nome do comando bot (cadeia, 32)<br>`description`: uma descrição simples ou exemplo da sintaxe do comando e seu argumento (cadeia, 128)|

## <a name="connectors"></a>conectores

**Opcional**

O `connectors` bloco define um Conector do Office 365 para o aplicativo.

O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Esse bloco é necessário apenas para soluções que fornecem um Conector.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|Cadeia de caracteres|2048 caracteres|✔|A https:// URL a ser usada ao configurar o conector.|
|`connectorId`|String|64 caracteres|✔|Um identificador exclusivo para o Conector que corresponde a sua ID no [Painel do Desenvolvedor de Conectores.](https://aka.ms/connectorsdashboard)|
|`scopes`|Matriz de enumeração|1 |✔|Especifica se o Conector oferece uma experiência no contexto de um canal em um , ou uma experiência com escopo `team` para um usuário individual sozinho ( `personal` ). Atualmente, apenas o `team` escopo é suportado.|

## <a name="composeextensions"></a>composeExtensions

**Opcional**

Define uma extensão de mensagens para o aplicativo.

> [!NOTE]
> O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem a funcionar.

O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do tipo `object` . Esse bloco é necessário apenas para soluções que fornecem uma extensão de mensagens.

|Nome| Tipo | Tamanho Máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|Cadeia de caracteres|64|✔|A ID exclusiva do aplicativo da Microsoft para o bot que é o suporte à extensão de mensagens, conforme registrado na Estrutura do Bot. Isso pode ser o mesmo que a ID geral [do aplicativo.](#id)|
|`canUpdateConfiguration`|Booliano|||Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário. O padrão é `false` .|
|`commands`|Matriz de objeto|10 |✔|Matriz de comandos compatíveis com a extensão de mensagens|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Sua extensão de mensagens deve declarar um ou mais comandos. Cada comando aparece no Microsoft Teams como uma interação potencial do ponto de entrada baseado na interface do usuário. Há um máximo de 10 comandos.

Cada item de comando é um objeto com a seguinte estrutura:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|String|64 caracteres|✔|A ID do comando|
|`type`|String|64 caracteres||Tipo do comando. Um ou `query` `action` . Padrão: `query`|
|`title`|Cadeia de Caracteres|32 caracteres|✔|O nome do comando amigável|
|`description`|Cadeia de Caracteres|128 caracteres||A descrição que aparece para os usuários para indicar a finalidade deste comando|
|`initialRun`|Booliano|||Um valor Boolean que indica se o comando deve ser executado inicialmente sem parâmetros. Padrão: `false`|
|`context`|Matriz de cadeias de caracteres|3||Define de onde a extensão da mensagem pode ser invocada. Qualquer combinação de `compose` , `commandBox` `message` . O padrão é `["compose", "commandBox"]`|
|`fetchTask`|Booliano|||Um valor booliana que indica se ele deve buscar o módulo de tarefa dinamicamente|
|`taskInfo`|Objeto|||Especificar o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens|
|`taskInfo.title`|Cadeia de Caracteres|64||Título da caixa de diálogo inicial|
|`taskInfo.width`|Cadeia de Caracteres|||Largura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'|
|`taskInfo.height`|Cadeia de Caracteres|||Altura da caixa de diálogo - um número em pixels ou layout padrão, como 'grande', 'médio' ou 'pequeno'|
|`taskInfo.url`|Cadeia de Caracteres|||URL inicial do webview|
|`messageHandlers`|Matriz de objetos|5 ||Uma lista de manipuladores que permitem que aplicativos sejam invocados quando determinadas condições são atendidas. Os domínios também devem estar listados em `validDomains`|
|`messageHandlers.type`|Cadeia de Caracteres|||O tipo de manipulador de mensagens. Deve ser `"link"`.|
|`messageHandlers.value.domains`|Matriz de cadeias de caracteres|||Matriz de domínios em que o manipulador de mensagens de link pode se registrar.|
|`parameters`|Matriz de objeto|5 |✔|A lista de parâmetros que o comando leva. Mínimo: 1; máximo: 5|
|`parameter.name`|String|64 caracteres|✔|O nome do parâmetro como ele aparece no cliente. Isso está incluído na solicitação do usuário.|
|`parameter.title`|Cadeia de Caracteres|32 caracteres|✔|Título amigável para o parâmetro.|
|`parameter.description`|Cadeia de Caracteres|128 caracteres||Cadeia de caracteres amigável que descreve a finalidade desse parâmetro.|
|`parameter.inputType`|Cadeia de Caracteres|128 caracteres||Define o tipo de controle exibido em um módulo de tarefa para `fetchTask: true` . Um de `text` , , , , `textarea` `number` `date` `time` , `toggle``choiceset`|
|`parameter.choices`|Matriz de objetos|10 ||As opções de escolha para o `choiceset` . Use somente quando `parameter.inputType` for `choiceset`|
|`parameter.choices.title`|Cadeia de Caracteres|128||Título da escolha|
|`parameter.choices.value`|Cadeia de Caracteres|512||Valor da escolha|

## <a name="permissions"></a>permissões

**Opcional**

Uma matriz que especifica quais permissões o aplicativo solicita, o que permite que os usuários `string` finais saibam como a extensão será efetivada. As seguintes opções não são exclusivas:

* `identity`&emsp;Requer informações de identidade do usuário
* `messageTeamMembers`&emsp;Requer permissão para enviar mensagens diretas aos membros da equipe

Alterar essas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado.

## <a name="devicepermissions"></a>devicePermissions

**Opcional** Matriz de cadeias de caracteres

Especifica os recursos nativos no dispositivo de um usuário aos que seu aplicativo pode solicitar acesso. As opções são:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, except **Required** where noted

Uma lista de domínios válidos dos quais o aplicativo espera carregar qualquer conteúdo. As listagem de domínio podem incluir caracteres curinga, por `*.example.com` exemplo. Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` . Se a configuração da guia ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além do uso para a configuração de guia, esse domínio deverá ser especificado aqui.

No **entanto,** não é necessário incluir os domínios de provedores de identidade que você deseja suportar em seu aplicativo. Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve incluir accounts.google.com em `validDomains[]` .

> [!IMPORTANT]
> Não adicione domínios que estejam fora do seu controle, diretamente ou por meio de caracteres curinga. Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.

O objeto é uma matriz com todos os elementos do tipo `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Opcional**

Especifique a ID do aplicativo AAD e as informações do Graph para ajudar os usuários a entrar facilmente em seu aplicativo AAD.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|Cadeia de caracteres|36 caracteres|✔|ID do aplicativo AAD do aplicativo. Essa ID deve ser um GUID.|
|`resource`|Cadeia de Caracteres|2048 caracteres|✔|URL do recurso do aplicativo para adquirir um token de autenticação para SSO.|