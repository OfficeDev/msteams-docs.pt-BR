---
title: TeamsFx SDK
author: MuyangAmigo
description: Neste módulo, saiba mais sobre o SDK do TeamsFx, os principais conceitos e a estrutura de código, personalização avançada e cenários
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 4889f4a9f97ff6606ebb283156d42963816cd269
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66557859"
---
# <a name="teamsfx-sdk"></a>TeamsFx SDK

O TeamsFx ajuda a reduzir as tarefas do desenvolvedor usando o SSO do Teams e acessando recursos na nuvem até instruções de linha única com configuração zero. O SDK do TeamsFx foi criado para ser usado no navegador e no ambiente node.js, cenários comuns incluem:

* Aplicativo de guia do Teams
* Função do Azure
* Bot do Teams

Você pode usar o SDK do TeamsFx para:

* Acesse as principais funcionalidades no ambiente de cliente e servidor.
* Escreva o código de autenticação do usuário de maneira simplificada.

## <a name="prerequisites"></a>Pré-requisitos

Instale as seguintes ferramentas e configure seu ambiente de desenvolvimento:

* Versão mais recente do Node.js
* Se seu projeto instalou `botbuilder` [pacotes](https://github.com/Microsoft/botbuilder-js#packages) relacionados como dependências, verifique se eles são da mesma versão. Atualmente, a versão necessária é 4.15.0 ou posterior, para obter mais informações, consulte [os pacotes do construtor de bot devem ser da mesma versão](https://github.com/BotBuilderCommunity/botbuilder-community-js/issues/57#issuecomment-508538548).

Você deve ter conhecimento prático do seguinte:

* [Código-fonte](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk)
* [Pacote (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx)
* [Documentação de referência de API](https://aka.ms/teamsfx-sdk-help)
* [Exemplos](https://github.com/OfficeDev/TeamsFx-Samples)

## <a name="get-started"></a>Introdução

O SDK do TeamsFx é pré-configurado no projeto com scaffolding usando o Kit de Ferramentas do TeamsFx ou a CLI.
Para obter mais informações, [Project de aplicativo Teams](https://github.com/OfficeDev/TeamsFx/blob/main/packages/vscode-extension/README.md).

### <a name="install-the-microsoftteamsfx-package"></a>Instalar o pacote `@microsoft/teamsfx`

Instale o SDK do TeamsFx para TypeScript ou JavaScript com `npm`:

```bash
npm install @microsoft/teamsfx
```

### <a name="create-microsoftgraphclient-service"></a>Criar `MicrosoftGraphClient` serviço

Para criar um objeto cliente do Graph e acessar a API do Microsoft Graph, é necessário que as credenciais sejam autenticadas. O SDK fornece as APIs a serem configuradas para os desenvolvedores.

<br>

<details>
<summary><b>Invoque API do Graph em nome do Usuário do Teams (Identidade do Usuário)</b></summary>

Use o seguinte trecho:

```ts
// Equivalent to:
// const teamsfx = new TeamsFx(IdentityType.User, {
//   initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
//   clientId: process.env.REACT_APP_CLIENT_ID,
// }
const teamsfx = new TeamsFx();
const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
const profile = await graphClient.api("/me").get(); // Get the profile of current user
```

</details>

<br>

<details>
<summary><b>Invoque API do Graph sem usuário (Identidade do Aplicativo)</b></summary>

Ele não requer a interação com o usuário do Teams. Você pode chamar Microsoft Graph como identidade do aplicativo.

Use o seguinte trecho:

```ts
// Equivalent to:
// const teamsfx = new TeamsFx(IdentityType.App, {
//   initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
//   clientId: process.env.REACT_APP_CLIENT_ID,
// });
const teamsfx = new TeamsFx(IdentityType.App);
const graphClient = createMicrosoftGraphClient(teamsfx);
const profile = await graphClient.api("/users/{object_id_of_another_people}").get(); // Get the profile of certain user
```

</details>

<br>

## <a name="core-concepts-and-code-structure"></a>Principais conceitos e estrutura de código

### <a name="teamsfx-class"></a>Classe TeamsFx

A instância da classe TeamsFx acessa todas as configurações do TeamsFx de variáveis de ambiente por padrão. Você também pode definir valores de configuração personalizados para substituir os valores padrão. Verifique a [configuração de substituição](#override-configuration) para obter detalhes.
Ao criar uma instância do TeamsFx, você também precisa especificar o tipo de identidade.
Há dois tipos de identidade:

* Identidade do Usuário
* Identidade do Aplicativo

#### <a name="user-identity"></a>Identidade do Usuário

| Comando | Descrição |
|----------------|-------------|
| `new TeamsFx(IdentityType.User)`| O aplicativo é autenticado como usuário atual do Teams. |
| `TeamsFx:setSsoToken()`| Identidade do usuário no ambiente node.js (sem navegador). |
| `TeamsFx:getUserInfo()` | Para obter informações básicas do usuário. |
| `TeamsFx:login()` | Ele é usado para permitir que o usuário execute o processo de consentimento, se desejar usar o SSO para obter o token de acesso para determinados escopos do OAuth. |

> [!NOTE]
> Você pode acessar recursos em nome do usuário atual do Teams.

#### <a name="application-identity"></a>Identidade do Aplicativo

| Comando | Descrição |
|----------------|-------------|
| `new TeamsFx(IdentityType.App)`| O aplicativo  está autenticado como um aplicativo. A permissão geralmente precisa da aprovação do administrador.|
| `TeamsFx:getCredential()`| Ele fornece instâncias de credencial correspondentes automaticamente ao tipo de identidade. |

> [!NOTE]
> Você precisa do consentimento do administrador para recursos.

### <a name="credential"></a>Credential

Você deve escolher o tipo de identidade ao inicializar o TeamsFx. Depois de especificar o tipo de identidade ao inicializar o TeamsFx, o SDK utiliza diferentes tipos de classe de credenciais para representar a identidade e obter o token de acesso pelo fluxo de autenticação correspondente.

Há três classes de credenciais para simplificar a autenticação. [pasta de credenciais](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/credential). As classes de credencial implementam a interface `TokenCredential`, que é amplamente usada nas APIs da biblioteca do Azure, projetada para fornecer tokens de acesso para escopos específicos. Outras APIs dependem da chamada da credencial `TeamsFx:getCredential()` para obter uma instância de `TokenCredential`.

Aqui estão os cenários correspondentes para cada meta de classe de credencial.

#### <a name="user-identity-in-browser-environment"></a>Identidade do Usuário no ambiente do navegador

`TeamsUserCredential` representa a identidade do usuário atual do Teams. O uso dessa credencial solicitará o consentimento do usuário na primeira vez. Ele aproveita o SSO do Teams e o fluxo On-Behalf-Of para fazer a troca de tokens. O SDK usa esta credencial quando os desenvolvedores escolhem a identidade do usuário no ambiente do navegador.

Configuração necessária: `initiateLoginEndpoint`, `clientId`.

#### <a name="user-identity-in-nodejs-environment"></a>Identidade do Usuário no ambiente do Node.js

`OnBehalfOfUserCredential` usa o fluxo On-Behalf-Of e precisa do token de SSO do Teams. Ele foi projetado para ser usado em cenários de função ou bot do Azure. O SDK usa esta credencial quando os desenvolvedores escolhem a identidade do usuário no ambiente Node.js.

Configuração necessária: `authorityHost`, `tenantId`, `clientId`, `clientSecret` ou `certificateContent`.

#### <a name="application-identity-in-nodejs-environment"></a>Identidade do Aplicativo no ambiente do Node.js

`AppCredential` representa a identidade do aplicativo. Ele é usado quando o usuário não está envolvido como um trabalho de automação acionado por tempo. O SDK usa esta credencial quando os desenvolvedores escolhem a identidade do aplicativo no ambiente Node.js.

Configuração necessária: `tenantId`, `clientId`, `clientSecret` ou `certificateContent`.

### <a name="bot-sso"></a>Bot SSO

Classes relacionadas ao bot são armazenadas em [bot](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/bot).

`TeamsBotSsoPrompt` tem uma boa integração com a estrutura do bot. Ele simplifica o processo de autenticação quando você desenvolve o aplicativo de bot e deseja aproveitar o SSO do bot.

Configuração necessária: `initiateLoginEndpoint`, `tenantId`, `clientId` e `applicationIdUri`.

### <a name="supported-functions"></a>Funções com suporte

O SDK do TeamsFx fornece várias funções para facilitar a configuração de bibliotecas de terceiros. Eles estão localizados na [pasta principal](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/core).

* Serviço Microsoft Graph:`createMicrosoftGraphClient` e `MsGraphAuthProvider` ajudam a criar uma instância autenticada do Graph.
* SQL:`getTediousConnectionConfig` retorna uma configuração de conexão entediante.

Configuração necessária:

* `sqlServerEndpoint`, `sqlUsername`se `sqlPassword` você quiser usar a identidade do usuário.
* `sqlServerEndpoint`, `sqlIdentityId` se você quiser usar a identidade MSI.

### <a name="error-handling"></a>Tratamento de erros

A resposta a erros de API `ErrorWithCode`, que contém o código de erro e a mensagem de erro. Por exemplo, para filtrar um erro específico, você pode usar o seguinte trecho de código:

```ts
try {
  const teamsfx = new TeamsFx();
  await teamsfx.login("User.Read");
} catch (err: unknown) {
  if (err instanceof ErrorWithCode && err.code !== ErrorCode.ConsentFailed) {
    throw err;
  } else {
    // Silently fail because user cancels the consent dialog
        return;
  }
}
```

Se a instância de credencial for usada em outra biblioteca, como Microsoft Graph, é possível que o erro seja capturado e transformado.

```ts
try {
  const teamsfx = new TeamsFx();
  const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
  const profile = await graphClient.api("/me").get();
} catch (err: unknown) {
  // ErrorWithCode is handled by Graph client
  if (err instanceof GraphError && err.code?.includes(ErrorCode.UiRequiredError)) {
    this.setState({
      showLoginBtn: true,
    });
  }
}
```

## <a name="scenarios"></a>Cenários

A seção a seguir fornece vários trechos de código para cenários comuns:

<br>

<details>
<summary><b>Use API do Graph no aplicativo guia</b></summary>

Use `TeamsFx` e `createMicrosoftGraphClient`.

```ts
const teamsfx = new TeamsFx();
const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]);
const profile = await graphClient.api("/me").get();
```

</details>

<br>

<details>
<summary><b>Criar um cliente de API para chamar a API existente no Bot ou no Azure Functions</b></summary>

:::image type="content" source="~/assets/images/teams-toolkit-v2/teams toolkit fundamentals/createapi-client.PNG" alt-text="Criar cliente de API":::

</details>

<br>

<details>
<summary><b>Chamar função do Azure no aplicativo guia</b></summary>

Use `axios` para fazer uma solicitação HTTP para a Função do Azure.

```ts
const teamsfx = new TeamsFx();
const credential = teamsfx.getCredential(); //Create an API Client that uses SSO token to authenticate requests
const apiClient = CreateApiClient(teamsfx.getConfig("apiEndpoint")),
new BearerTokenAuthProvider(async () =>  (await credential.getToken(""))!.token);// Call API hosted in Azure Functions on behalf of user
const response = await apiClient.get("/api/" + functionName);
```

</details>

<br>

<details>
<summary><b>Acessar ao Banco de dados SQL in Função do Azure</b></summary>

Use a biblioteca `tedious` para acessar o SQL e aproveitar `DefaultTediousConnectionConfiguration` que gerencia a autenticação.
Além de `tedious`, você também pode compor a configuração de conexão de outras bibliotecas SQL com base no resultado de `sqlConnectionConfig.getConfig()`.

```ts
// Equivalent to:
// const sqlConnectConfig = new DefaultTediousConnectionConfiguration({
//    sqlServerEndpoint: process.env.SQL_ENDPOINT,
//    sqlUsername: process.env.SQL_USER_NAME,
//    sqlPassword: process.env.SQL_PASSWORD,
// });
const teamsfx = new TeamsFx();
// If there's only one SQL database
const config = await getTediousConnectionConfig(teamsfx);
// If there are multiple SQL databases
const config2 = await getTediousConnectionConfig(teamsfx "your database name");
const connection = new Connection(config);
connection.on("connect", (error) => {
  if (error) {
    console.log(error);
  }
});
```

</details>

<br>

<details>
<summary><b>Use a autenticação baseada em certificado na função do Azure</b></summary>

```ts
const authConfig = {
  clientId: process.env.M365_CLIENT_ID,
  certificateContent: "The content of a PEM-encoded public/private key certificate",
  authorityHost: process.env.M365_AUTHORITY_HOST,
  tenantId: process.env.M365_TENANT_ID,
};
const teamsfx = new TeamsFx(IdentityType.App);
teamsfx.setCustomeConfig({
  certificateContent: "The content of a PEM-encoded public/private key certificate"
});
const token = teamsfx.getCredential().getToken();
```

</details>

<br>

<details>
<summary><b>Use API do Graph no aplicativo bot</b></summary>

Adicione `TeamsBotSsoPrompt` ao conjunto de diálogos.

```ts
const { ConversationState, MemoryStorage } = require("botbuilder");
const { DialogSet, WaterfallDialog } = require("botbuilder-dialogs");
const { TeamsBotSsoPrompt } = require("@microsoft/teamsfx");

const convoState = new ConversationState(new MemoryStorage());
const dialogState = convoState.createProperty("dialogState");
const dialogs = new DialogSet(dialogState);

const teamsfx = new TeamsFx();
dialogs.add(
  new TeamsBotSsoPrompt(teamsfx, "TeamsBotSsoPrompt", {
    scopes: ["User.Read"],
  })
);

dialogs.add(
  new WaterfallDialog("taskNeedingLogin", [
    async (step) => {
      return await step.beginDialog("TeamsBotSsoPrompt");
    },
    async (step) => {
      const token = step.result;
      if (token) {
        // ... continue with task needing access token ...
      } else {
        await step.context.sendActivity(`Sorry... We couldn't log you in. Try again later.`);
        return await step.endDialog();
      }
    },
  ])
);
```

</details>

<br>

## <a name="advanced-customization"></a>Personalização avançada

### <a name="configure-log"></a>Configurar log

Você pode definir o nível de log do cliente e redirecionar as saídas ao usar essa biblioteca. O registro em log está desativado por padrão. Você pode ativá-lo definindo o nível de log.

#### <a name="enable-log-by-setting-log-level"></a>Habilitar o log definindo o nível de log

O registro em log é habilitado somente quando você define o nível de log. Por padrão, ele imprime informações de log no console.

Defina o nível de log usando o seguinte trecho de código:

```ts
// Only need the warning and error messages.
setLogLevel(LogLevel.Warn);
```

Você pode redirecionar a saída do log definindo o agente personalizado ou a função de log.

#### <a name="redirect-by-setting-custom-logger"></a>Redirecionar definindo o agente personalizado

```ts
setLogLevel(LogLevel.Info);
// Set another logger if you want to redirect to Application Insights in Azure Function
setLogger(context.log);
```

#### <a name="redirect-by-setting-custom-log-function"></a>Redirecionar definindo a função de log personalizada

> [!NOTE]
> A função de log não terá efeito se você definir um agente personalizado.

```ts
setLogLevel(LogLevel.Info);
// Only log error message to Application Insights in bot application.
setLogFunction((level: LogLevel, message: string) => {
  if (level === LogLevel.Error) {
    this.telemetryClient.trackTrace({
      message: message,
      severityLevel: Severity.Error,
    });
  }
});
```

## <a name="override-configuration"></a>Substituir configuração

Você pode passar a configuração personalizada ao criar a instância do TeamsFx para substituir a configuração padrão ou definir campos obrigatórios quando as variáveis de ambiente estão ausentes.

* Se você tiver criado um projeto de guia usando o Kit de Ferramentas do VS Code, os seguintes valores de configuração serão usados de variáveis de ambiente pré-configuradas:
  * authorityHost (REACT_APP_AUTHORITY_HOST)
  * tenantId (REACT_APP_TENANT_ID)
  * clientId (REACT_APP_CLIENT_ID)
  * initiateLoginEndpoint (REACT_APP_START_LOGIN_PAGE_URL)
  * applicationIdUri (REACT_APP_START_LOGIN_PAGE_URL)
  * apiEndpoint (REACT_APP_FUNC_ENDPOINT)
  * apiName (REACT_APP_FUNC_NAME)

* Se você tiver criado a Função do Azure/projeto de bot usando o Kit de Ferramentas do VS Code, os seguintes valores de configuração serão usados de variáveis de ambiente pré-configuradas:
  * initiateLoginEndpoint (INITIATE_LOGIN_ENDPOINT)
  * authorityHost (M365_AUTHORITY_HOST)
  * tenantId (M365_TENANT_ID)
  * clientId (M365_CLIENT_ID)
  * clientSecret (M365_CLIENT_SECRET)
  * applicationIdUri (M365_APPLICATION_ID_URI)
  * apiEndpoint (API_ENDPOINT)
  * sqlServerEndpoint (SQL_ENDPOINT)
  * sqlUsername (SQL_USER_NAME)
  * sqlPassword (SQL_PASSWORD)
  * sqlDatabaseName (SQL_DATABASE_NAME)
  * sqlIdentityId (IDENTITY_ID)

## <a name="upgrade-latest-sdk-version"></a>Atualizar a versão mais recente do SDK

Se você estiver usando a versão do SDK que tem `loadConfiguration()`, siga estas etapas para atualizar para a versão mais recente do SDK.

1. Remova `loadConfiguration()` e passe as configurações personalizadas usando `new TeamsFx(IdentityType.User, { ...customConfig })`
2. Substituir `new TeamsUserCredential()` por `new TeamsFx()`
3. Substituir `new M365TenantCredential()` por `new TeamsFx(IdentityType.App)`
4. Substituir `new OnBehalfOfUserCredential(ssoToken)` por `new TeamsFx().setSsoToken(ssoToken)`
5. Passe a instância de `TeamsFx` para funções auxiliares para substituir a instância de credencial

Para obter mais informações, consulte [uma classe TeamsFx](#teamsfx-class).

## <a name="next-step"></a>Próxima etapa

[Exemplos](https://github.com/OfficeDev/TeamsFx-Samples) do projeto para exemplos detalhados sobre como usar o TeamsFx SDK.

## <a name="see-also"></a>Confira também

[Galeria de exemplos do Microsoft TeamsFx](https://github.com/OfficeDev/TeamsFx-Samples).
