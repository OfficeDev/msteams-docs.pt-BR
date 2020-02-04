---
title: Referência de esquema de manifesto
description: Descreve o esquema suportado pelo manifesto para o Microsoft Teams
keywords: esquema de manifesto do teams
ms.openlocfilehash: d4a2864c18a5066673bafab42a46733a0ab5f116
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672728"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referência: esquema de manifesto para o Microsoft Teams

O manifesto do Microsoft Teams descreve como o aplicativo integra-se ao produto Microsoft Teams. Seu manifesto deve estar em conformidade com o esquema [`https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json)hospedado em. As versões anteriores 1.0-1.4 também são suportadas (usando "v1. x" na URL).

O seguinte exemplo de esquema mostra todas as opções de extensibilidade.

## <a name="sample-full-manifest"></a>Exemplo de manifesto completo

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
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
    "defaultLanguageTag": "en-us",
    "additionalLanguages": [
      {
        "languageTag": "es-es",
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
        }
      ],
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
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
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

*Opcional, mas* &ndash; a cadeia de caracteres recomendada

A URL https://que faz referência ao esquema JSON para o manifesto.

## <a name="manifestversion"></a>manifestVersion

Cadeia de caracteres **obrigatória** &ndash;

A versão do esquema de manifesto que este manifesto está usando. Ele deve ser "1,5".

## <a name="version"></a>versão

Cadeia de caracteres **obrigatória** &ndash;

A versão do aplicativo específico. Se você atualizar algo em seu manifesto, a versão também deverá ser incrementada. Dessa forma, quando o novo manifesto é instalado, ele substitui o existente, e o usuário recebe a nova funcionalidade. Se este aplicativo foi enviado para o repositório, o novo manifesto terá que ser reenviado e validado novamente. Em seguida, os usuários desse aplicativo receberão o novo manifesto atualizado automaticamente em algumas horas, após serem aprovados.

Se as permissões solicitadas pelo aplicativo forem alteradas, os usuários serão solicitados a atualizar e a dar o consentimento novamente para o aplicativo.

Esta sequência de versão deve seguir o padrão [semver](http://semver.org/) (principal. Mínima. PATCH).

## <a name="id"></a>id

ID de aplicativo da Microsoft **necessária** &ndash;

O identificador exclusivo gerado pela Microsoft para este aplicativo. Se você tiver registrado um bot por meio da Microsoft bot Framework, ou se o aplicativo Web da sua guia já estiver conectado com a Microsoft, você já deve ter um ID e deve inseri-lo aqui. Caso contrário, você deve gerar uma nova ID no portal de registro de aplicativos da Microsoft ([meus aplicativos](https://apps.dev.microsoft.com)), inseri-la aqui e reutilizá-la quando você adicionar um bot. Observação: se você estiver enviando uma atualização para o seu aplicativo existente no AppSource, a ID em seu manifesto não deverá ser modificada.

## <a name="packagename"></a>Packagenamena

Cadeia de caracteres **obrigatória** &ndash;

Um identificador exclusivo para esse aplicativo na notação de domínio reverso; por exemplo, com. example. MyApp.

## <a name="developer"></a>developer

**Required**

Especifica informações sobre sua empresa. Para aplicativos enviados para o AppSource (anteriormente Office Store), esses valores devem corresponder às informações na entrada do AppSource. Veja nossas [diretrizes de publicação](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) para obter mais informações.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`name`|32 caracteres|✔|O nome de exibição para o desenvolvedor.|
|`websiteUrl`|2048 caracteres|✔|A URL do https://para o site do desenvolvedor. Este link deve levar os usuários à sua página de aterrissagem específica da empresa ou do produto.|
|`privacyUrl`|2048 caracteres|✔|A URL do https://para a política de privacidade do desenvolvedor.|
|`termsOfUseUrl`|2048 caracteres|✔|A URL do https://para os termos de uso do desenvolvedor.|
|`mpnId`|10 caracteres| |**Opcional** A ID de rede do parceiro da Microsoft que identifica a organização do parceiro que está criando o aplicativo.|

## <a name="localizationinfo"></a>localizationInfo

**Opcional**

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

## <a name="name"></a>nome

**Required**

O nome da sua experiência de aplicativo, exibido aos usuários na experiência do teams. Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource. Os valores de `short` e `full` não devem ser os mesmos.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|30 caracteres|✔|O nome de exibição curto para o aplicativo.|
|`full`|100 caracteres||O nome completo do aplicativo, usado se o nome completo do aplicativo exceder 30 caracteres.|

## <a name="description"></a>description

**Required**

Descreve seu aplicativo para os usuários. Para aplicativos enviados para o AppSource, esses valores devem corresponder às informações na entrada do AppSource.

Certifique-se de que sua descrição descreve precisamente sua experiência e fornece informações para ajudar os clientes potenciais a entender o que a sua experiência faz. Você também deve observar, na descrição completa, se for necessário usar uma conta externa. Os valores de `short` e `full` não devem ser os mesmos.  Sua descrição curta não deve ser repetida dentro da descrição longa e não deve incluir nenhum outro nome de aplicativo.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`short`|80 caracteres|✔|Uma breve descrição da experiência do aplicativo, usada quando o espaço é limitado.|
|`full`|4000 caracteres|✔|A descrição completa do seu aplicativo.|

## <a name="icons"></a>ícones

**Required**

Ícones usados no aplicativo Teams. Os arquivos de ícone devem ser incluídos como parte do pacote de carregamento. Consulte [ícones](~/concepts/build-and-test/apps-package.md#icons) para obter mais informações.

|Nome| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|
|`outline`|2048 caracteres|✔|Um caminho de arquivo relativo para um ícone de estrutura de tópicos de PNG de 32 x 32 transparente.|
|`color`|2048 caracteres|✔|Um caminho de arquivo relativo para um ícone de 192x192 do PNG completo.|

## <a name="accentcolor"></a>accentColor

Cadeia de caracteres **obrigatória** &ndash;

Uma cor a ser usada em conjunto com e como um plano de fundo para seus ícones de estrutura de tópicos.

O valor deve ser um código de cor HTML válido começando com ' # ', por `#4464ee`exemplo.

## <a name="configurabletabs"></a>configurableTabs

**Opcional**

Usado quando sua experiência de aplicativo tem uma experiência de guia de canal de equipe que requer configuração adicional antes de ser adicionada. Guias configuráveis têm suporte apenas no escopo Teams, e atualmente só há suporte para uma guia por aplicativo.

O objeto é uma matriz com todos os elementos do tipo `object`. Esse bloco só é necessário para soluções que oferecem uma solução de guia de canal configurável.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|String|2048 caracteres|✔|A URL do https://a ser usada ao configurar a guia.|
|`canUpdateConfiguration`|Boolean|||Um valor que indica se uma instância da configuração da guia pode ser atualizada pelo usuário após a criação. Será`true`|
|`scopes`|Matriz de enumeração|1 |✔|No momento, as guias configuráveis `team` só `groupchat` dão suporte a e os escopos. |
|`sharePointPreviewImage`|String|2048||Um caminho de arquivo relativo para uma imagem de visualização de tabulação para uso no SharePoint. Tamanho 1024x768. |
|`supportedSharePointHosts`|Matriz de enumeração|1 ||Define como sua guia será disponibilizada no SharePoint. Opções são `sharePointFullPage` e`sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Opcional**

Define um conjunto de guias que podem ser "fixadas" por padrão, sem o usuário adicioná-las manualmente. As guias estáticas `personal` declaradas no escopo são sempre fixadas para a experiência pessoal do aplicativo. Guias static declaradas `team` no escopo não são suportadas atualmente.

O objeto é uma matriz (máximo de 16 elementos) com todos os elementos do tipo `object`. Esse bloco é necessário somente para soluções que oferecem uma solução de guia estática.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`entityId`|String|64 caracteres|✔|Um identificador exclusivo para a entidade que a guia exibe.|
|`name`|String|128 caracteres|✔|O nome de exibição da guia na interface de canal.|
|`contentUrl`|String|2048 caracteres|✔|A URL https://que aponta para a interface do usuário da entidade a ser exibida na tela do teams.|
|`websiteUrl`|String|2048 caracteres||A URL do https://para apontar para o modo de exibição de um usuário em um navegador.|
|`scopes`|Matriz de enumeração|1 |✔|Atualmente, as guias estáticas oferecem `personal` suporte somente ao escopo, o que significa que ela pode ser provisionada somente como parte da experiência pessoal.|

## <a name="bots"></a>robôs

**Opcional**

Define uma solução de bot, juntamente com informações opcionais, como propriedades de comando padrão.

O objeto é uma matriz (máximo de apenas 1 elemento&mdash;atualmente apenas um bot é permitido por aplicativo) com todos os elementos do tipo `object`. Esse bloco é necessário somente para soluções que oferecem uma experiência de bot.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|String|64 caracteres|✔|A ID exclusiva do aplicativo da Microsoft para o bot, conforme registrado na estrutura do bot. Isso pode ser o mesmo que a ID de [aplicativo](#id)geral.|
|`needsChannelSelector`|Boolean|||Descreve se o bot utiliza ou não uma dica de usuário para adicionar o bot a um canal específico. Será`false`|
|`isNotificationOnly`|Boolean|||Indica se um bot é um bot unidirecional somente de notificação, em vez de um bot de conversa. Será`false`|
|`supportsFiles`|Boolean|||Indica se o bot dá suporte à capacidade de carregar/baixar arquivos no chat pessoal. Será`false`|
|`scopes`|Matriz de enumeração|3 |✔|Especifica se o bot oferece uma experiência no contexto de um canal em um `team`, em um chat de grupo (`groupchat`) ou uma experiência com escopo para um usuário individual sozinho (`personal`). Essas opções são não exclusivas.|

### <a name="botscommandlists"></a>bots. commandLists

Uma lista opcional de comandos que seu bot pode recomendar aos usuários. O objeto é uma matriz (máximo de dois elementos) com todos os elementos do `object`tipo; Você deve definir uma lista de comandos separada para cada escopo que seu bot suporta. Consulte [menus de bot](~/bots/how-to/create-a-bot-commands-menu.md) para obter mais informações.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`items.scopes`|matriz de enumeração|3 |✔|Especifica o escopo para o qual a lista de comandos é válida. As opções `team`são `personal`, e `groupchat`.|
|`items.commands`|matriz de objetos|10 |✔|Uma matriz de comandos para a qual o bot oferece suporte:<br>`title`: o nome do comando do bot (cadeia de caracteres, 32)<br>`description`: uma simples descrição ou exemplo da sintaxe do comando e seu argumento (String, 128)|

## <a name="connectors"></a>conectores

**Opcional**

O `connectors` bloco define um conector do Office 365 para o aplicativo.

O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do `object`tipo. Esse bloco é necessário somente para soluções que fornecem um conector.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`configurationUrl`|String|2048 caracteres|✔|A URL do https://a ser usada ao configurar o conector.|
|`connectorId`|String|64 caracteres|✔|Um identificador exclusivo para o conector que corresponde à sua ID no [painel do desenvolvedor de conectores](https://aka.ms/connectorsdashboard).|
|`scopes`|Matriz de enumeração|1 |✔|Especifica se o conector oferece uma experiência no contexto de um canal em uma `team`ou uma experiência com escopo para um usuário individual (`personal`). Atualmente, só há `team` suporte para o escopo.|

## <a name="composeextensions"></a>composeExtensions

**Opcional**

Define uma extensão de mensagens para o aplicativo.

> [!NOTE]
> O nome do recurso foi alterado de "extensão de composição" para "extensão de mensagens" em novembro de 2017, mas o nome do manifesto permanece o mesmo para que as extensões existentes continuem a funcionar.

O objeto é uma matriz (máximo de 1 elemento) com todos os elementos do `object`tipo. Esse bloco é necessário somente para soluções que forneçam uma extensão de mensagens.

|Nome| Tipo | Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`botId`|String|64|✔|A ID exclusiva do aplicativo da Microsoft para o bot que faz a extensão do sistema de mensagens, conforme registrado na estrutura do bot. Isso pode ser o mesmo que a ID de aplicativo geral.|
|`canUpdateConfiguration`|Boolean|||Um valor que indica se a configuração de uma extensão de mensagens pode ser atualizada pelo usuário. O padrão é `false`.|
|`commands`|Matriz de objeto|10 |✔|Matriz de comandos que a extensão de mensagens oferece suporte|
|`messageHandlers`|Matriz de objetos|5 ||Uma lista de manipuladores que permitem que os aplicativos sejam chamados quando determinadas condições são atendidas. Os domínios também devem ser listados no`validDomains`|
|`messageHandlers.type`|String|||O tipo de manipulador de mensagens. Deve ser `"link"`.|
|`messageHandlers.value.domains`|Matriz de cadeias de caracteres|||Matriz de domínios para o qual o manipulador de mensagens de link pode se registrar.|

### <a name="composeextensionscommands"></a>composeExtensions. Commands

Sua extensão de mensagens deve declarar um ou mais comandos. Cada comando aparece no Microsoft Teams como uma possível interação do ponto de entrada baseado na interface do usuário. Há um máximo de 10 comandos.

Cada item de comando é um objeto com a seguinte estrutura:

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|String|64 caracteres|✔|A ID do comando|
|`type`|String|64 caracteres||Tipo do comando. Um `query` ou `action`. Será`query`|
|`title`|String|32 caracteres|✔|O nome do comando amigável|
|`description`|String|128 caracteres||A descrição que aparece para os usuários para indicar a finalidade desse comando|
|`initialRun`|Boolean|||Um valor Boolean que indica se o comando deve ser executado inicialmente sem parâmetros. Será`false`|
|`context`|Matriz de cadeias de caracteres|3 ||Define onde a extensão de mensagem pode ser chamada. Qualquer combinação de `compose`, `commandBox`, `message`. O padrão é`["compose", "commandBox"]`|
|`fetchTask`|Boolean|||Um valor Boolean que indica se deve buscar o módulo de tarefa dinamicamente|
|`taskInfo`|Objeto|||Especificar o módulo de tarefa a ser pré-carregar ao usar um comando de extensão de mensagens|
|`taskInfo.title`|String|64||Título inicial da caixa de diálogo|
|`taskInfo.width`|String|||Largura da caixa de diálogo: um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '|
|`taskInfo.height`|String|||Altura da caixa de diálogo-um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '|
|`taskInfo.url`|String|||URL do WebView inicial|
|`parameters`|Matriz de objeto|5 |✔|A lista de parâmetros que o comando utiliza. Mínimo: 1; máximo: 5|
|`parameter.name`|String|64 caracteres|✔|O nome do parâmetro conforme ele aparece no cliente. Isso é incluído na solicitação do usuário.|
|`parameter.title`|String|32 caracteres|✔|Título amigável para o parâmetro.|
|`parameter.description`|String|128 caracteres||Cadeia de caracteres amigável que descreve a finalidade deste parâmetro.|
|`parameter.inputType`|String|128 caracteres||Define o tipo de controle exibido em um módulo de tarefas `fetchTask: true`para o. Um de `text`, `textarea`, `number`, `date`, `time`, `toggle`,`choiceset`|
|`parameter.choices`|Matriz de objetos|10 ||As opções de escolha para `choiceset`o. Use somente quando `parameter.inputType` o é`choiceset`|
|`parameter.choices.title`|String|128||Título da opção|
|`parameter.choices.value`|String|512||Valor da opção|

## <a name="permissions"></a>permissões

**Opcional**

Uma matriz `string` que especifica quais permissões o aplicativo solicita, o que permite que os usuários finais saibam como a extensão será executada. As opções a seguir são não exclusivas:

* `identity`&emsp; Requer informações de identidade do usuário
* `messageTeamMembers`&emsp; Requer permissão para enviar mensagens diretas para membros da equipe

A alteração dessas permissões ao atualizar seu aplicativo fará com que os usuários repitam o processo de consentimento na primeira vez em que executarem o aplicativo atualizado. Veja [atualização do seu aplicativo](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) para obter mais informações.

## <a name="devicepermissions"></a>devicePermissions

**Opcional** Matriz de cadeias de caracteres

Especifica os recursos nativos no dispositivo de um usuário para o qual seu aplicativo pode solicitar acesso. As opções são:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Opcional**, exceto quando **necessário** , onde observado

Uma lista de domínios válidos para sites que o aplicativo espera carregar no cliente do teams. As listagens de domínio podem incluir curingas, `*.example.com`por exemplo. Isso corresponde exatamente a um segmento do domínio; Se você precisar coincidir `a.b.example.com` e usar `*.*.example.com`. Se a configuração de sua guia ou a interface do usuário de conteúdo precisar navegar para qualquer outro domínio além daquele usado para configuração de guia, esse domínio deverá ser especificado aqui.

No entanto, **não** é necessário incluir os domínios de provedores de identidade que você deseja suportar no seu aplicativo. Por exemplo, para autenticar usando uma ID do Google, é necessário redirecionar para o accounts.google.com, mas você não deve `validDomains[]`incluir o accounts.google.com no.

Aplicativos do teams que exigem suas próprias URLs do SharePoint para funcionar bem, podem incluir "{teamsitedomain}" em sua lista de domínios válida.

> [!IMPORTANT]
> Não adicione domínios que estejam fora do seu controle, seja diretamente ou via curingas. Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.

O objeto é uma matriz com todos os elementos do tipo `string`.

## <a name="webapplicationinfo"></a>webApplicationInfo

**Opcional**

Especifique a ID do aplicativo AAD e as informações do gráfico para ajudar os usuários a entrarem diretamente no aplicativo AAD.

|Nome| Tipo| Tamanho máximo | Obrigatório | Descrição|
|---|---|---|---|---|
|`id`|String|36 caracteres|✔|ID do aplicativo AAD do aplicativo. Esta ID deve ser um GUID.|
|`resource`|String|2048 caracteres|✔|URL de recurso do aplicativo para aquisição de token de autenticação para SSO.|
