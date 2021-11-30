---
title: TeamsFx SDK
author: MuyangAmigo
description: Sobre o SDK teamsFx
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 63c5fad9c795c513b476f305c09d94ffad7c5d61
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2021
ms.locfileid: "61227915"
---
# <a name="teamsfx-sdk-for-typescript-or-javascript"></a>SDK teamsFx para TypeScript ou JavaScript

O TeamsFx tem como objetivo reduzir as tarefas de implementação de identidade e acesso a recursos de nuvem para instruções de linha única com "configuração zero".

Use a biblioteca para:

- Acessar as principais funcionalidades no ambiente de cliente e servidor de maneira semelhante.
- Escreva o código de autenticação do usuário de maneira simplificada.

   * [Código-fonte](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk) 
   * [Pacote (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx) 
   * [Documentação de referência de API](https://aka.ms/teamsfx-sdk-help) 
   * [Exemplos](https://github.com/OfficeDev/TeamsFx-Samples)

## <a name="get-started"></a>Introdução

O SDK teamsFx é pré-configurado no projeto em scaffolded usando o TeamsFx toolkit ou CLI.
Para obter mais informações sobre Teams de aplicativos, consulte [README](https://github.com/OfficeDev/TeamsFx/blob/main/packages/vscode-extension/README.md).

### <a name="prerequisites"></a>Pré-requisitos

- Node.js versão `10.x.x` ou superior.
- Se seu projeto instalou pacotes relacionados como dependências, verifique se eles são da `botbuilder` mesma versão e da versão [](https://github.com/Microsoft/botbuilder-js#packages) `>= 4.9.3` . ([Problema - todos os pacotes BOTBUILDER devem ser a mesma versão](https://github.com/BotBuilderCommunity/botbuilder-community-js/issues/57#issuecomment-508538548))

> [!TIP]
> Um projeto criado pelo TeamsFx toolkit VS Code extensão ou ferramenta CLI.

### <a name="install-the-microsoftteamsfx-package"></a>Instalar o `@microsoft/teamsfx` pacote

Instale o SDK do TeamsFx para TypeScript ou JavaScript com `npm` :

```bash
npm install @microsoft/teamsfx
```

### <a name="create-and-authenticate-a-microsoftgraphclient"></a>Criar e autenticar um `MicrosoftGraphClient`

Para criar um objeto cliente gráfico para acessar a API do Microsoft Graph, você precisará da credencial para fazer autenticação. O SDK fornece várias classes de credenciais para escolher que atendam a vários requisitos. Você precisa carregar a configuração antes de usar quaisquer credenciais.

- No ambiente do navegador, você precisa passar explicitamente os parâmetros de configuração. O projeto scaffolded React forneceu variáveis de ambiente a ser usadas.

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
    simpleAuthEndpoint: process.env.REACT_APP_TEAMSFX_ENDPOINT,
    clientId: process.env.REACT_APP_CLIENT_ID,
  },
});
```

- No ambiente NodeJS, como a Função Azure, você pode simplesmente chamar `loadConfiguration` . Ele será carregado de variáveis de ambiente por padrão.

```ts
loadConfiguration();
```

#### <a name="using-teams-app-user-credential"></a>Usando Teams de usuário do aplicativo

Use o trecho abaixo:

> [Observação] Você só pode usar essa classe de credencial no aplicativo do navegador como Teams Tab App.

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
    simpleAuthEndpoint: process.env.REACT_APP_TEAMSFX_ENDPOINT,
    clientId: process.env.REACT_APP_CLIENT_ID,
  },
});
const credential = new TeamsUserCredential();
const graphClient = createMicrosoftGraphClient(credential, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
const profile = await graphClient.api("/me").get();
```

#### <a name="using-microsoft-365-tenant-credential"></a>Usando Microsoft 365 de locatário

Ele não exige a interação com o usuário Teams App. Você pode chamar o Microsoft Graph como aplicativo.
Use o trecho abaixo:

```ts
loadConfiguration();
const credential = new M365TenantCredential();
const graphClient = createMicrosoftGraphClient(credential);
const profile = await graphClient.api("/users/{object_id_of_another_people}").get();
```

## <a name="core-concepts-and-code-structure"></a>Principais conceitos e estrutura de código

### <a name="credentials"></a>Credenciais

Há três classes de credencial localizadas na pasta [de](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/credential) credenciais para ajudar a simplificar a autenticação. 

Classes de credenciais `TokenCredential` implementam interface amplamente usada nas APIs da biblioteca do Azure. Eles foram projetados para fornecer token de acesso para escopos específicos.
As classes de credenciais representam identidade diferente em determinados cenários.

`TeamsUserCredential`representa Teams identidade do usuário atual. O uso dessa credencial solicitará o consentimento do usuário na primeira vez.
`M365TenantCredential`representa Microsoft 365 identidade de locatário. Geralmente é usado quando o usuário não está envolvido, como o trabalho de automação disparado pelo tempo.
`OnBehalfOfUserCredential` usa o fluxo em nome do fluxo. Ele precisa de um token de acesso e você pode obter um novo token para escopo diferente. Ele foi projetado para ser usado em cenários de Função do Azure ou Bot.

### <a name="bots"></a>Bots

As classes relacionadas a bot são armazenadas na [pasta bot.](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/bot)

`TeamsBotSsoPrompt` tem uma boa integração com a estrutura bot. Simplifica o processo de autenticação quando você desenvolve um aplicativo bot.

### <a name="helper-functions"></a>Funções auxiliares

O SDK teamsFx fornece funções auxiliares para facilitar a configuração para bibliotecas de terceiros. Eles estão localizados na [pasta](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/core) principal.

### <a name="error-handling"></a>Tratamento de erros

A API lançará `ErrorWithCode` se ocorrer um erro. Cada `ErrorWithCode` um contém o código de erro e a mensagem de erro.

Por exemplo, para filtrar um erro específico, você pode usar a seguinte verificação:

```ts
try {
  const credential = new TeamsUserCredential();
  await credential.login("User.Read");
} catch (err: unknown) {
  if (err instanceof ErrorWithCode && err.code !== ErrorCode.ConsentFailed) {
    throw err;
  } else {
    // Silently fail because user cancels the consent dialog
    return;
  }
}
```

E se a instância de credencial for usada em outra biblioteca como a Microsoft Graph, é possível que o erro seja capturado e transformado.

```ts
try {
  const credential = new TeamsUserCredential();
  const graphClient = createMicrosoftGraphClient(credential, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
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

As seções a seguir fornecem vários trechos de código que abrangem alguns dos cenários mais comuns:

- [Usar Graph API no aplicativo guia](#use-graph-api-in-tab-app)
- [Chamar a função do Azure no aplicativo guia](#call-azure-function-in-tab-app)
- [Acessar SQL banco de dados no Azure Function](#access-sql-database-in-azure-function)
- [Usar autenticação baseada em certificado na função Azure](#use-certificate-based-authentication-in-azure-function)
- [Usar Graph API no aplicativo Bot](#use-graph-api-in-bot-application)

### <a name="use-graph-api-in-tab-app"></a>Usar Graph API no aplicativo guia

Use `TeamsUserCredential` e `createMicrosoftGraphClient` .

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
    simpleAuthEndpoint: process.env.REACT_APP_TEAMSFX_ENDPOINT,
    clientId: process.env.REACT_APP_CLIENT_ID,
  },
});
const credential: any = new TeamsUserCredential();
const graphClient = createMicrosoftGraphClient(credential, ["User.Read"]);
const profile = await graphClient.api("/me").get();
```

### <a name="call-azure-function-in-tab-app"></a>Chamar a função do Azure no aplicativo guia

Use `axios` a biblioteca para fazer solicitação HTTP para a Função Azure.

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
    simpleAuthEndpoint: process.env.REACT_APP_TEAMSFX_ENDPOINT,
    clientId: process.env.REACT_APP_CLIENT_ID,
  },
});
const credential: any = new TeamsUserCredential();
const token = credential.getToken(""); // Get SSO token for the user
// Call API hosted in Azure Functions on behalf of user
const apiConfig = getResourceConfiguration(ResourceType.API);
const response = await axios.default.get(apiConfig.endpoint + "api/httptrigger1", {
  headers: {
    authorization: "Bearer " + token,
  },
});
```

### <a name="access-sql-database-in-azure-function"></a>Acessar SQL banco de dados no Azure Function

Use `tedious` a biblioteca para acessar SQL e aproveitar que gerencia a `DefaultTediousConnectionConfiguration` autenticação.
Além de , você também pode compor a configuração de conexão `tedious` de outras bibliotecas SQL com base no resultado de `sqlConnectionConfig.getConfig()` .

```ts
loadConfiguration();
const sqlConnectConfig = new DefaultTediousConnectionConfiguration();
const config = await sqlConnectConfig.getConfig();
const connection = new Connection(config);
connection.on("connect", (error) => {
  if (error) {
    console.log(error);
  }
});
```

### <a name="use-certificate-based-authentication-in-azure-function"></a>Usar autenticação baseada em certificado na função Azure

```ts
loadConfiguration({
  authentication: {
    clientId: process.env.M365_CLIENT_ID,
    certificateContent: "The content of a PEM-encoded public/private key certificate",
    authorityHost: process.env.M365_AUTHORITY_HOST,
    tenantId: process.env.M365_TENANT_ID,
  },
});
```

### <a name="use-graph-api-in-bot-application"></a>Usar Graph API no aplicativo Bot

Adicionar `TeamsBotSsoPrompt` ao conjunto de diálogo.

```ts
const { ConversationState, MemoryStorage } = require("botbuilder");
const { DialogSet, WaterfallDialog } = require("botbuilder-dialogs");
const { TeamsBotSsoPrompt } = require("@microsoft/teamsfx");

const convoState = new ConversationState(new MemoryStorage());
const dialogState = convoState.createProperty("dialogState");
const dialogs = new DialogSet(dialogState);

loadConfiguration();
dialogs.add(
  new TeamsBotSsoPrompt("TeamsBotSsoPrompt", {
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

## <a name="troubleshooting"></a>Solução de problemas

### <a name="configure-log"></a>Configurar log

Você pode definir o nível de log do cliente e as saídas de redirecionamento ao usar essa biblioteca.
O registro em log está desligado por padrão, você pode agará-lo definindo o nível de log.

#### <a name="enable-log-by-setting-log-level"></a>Habilitar o log definindo o nível de log

Quando o nível de log é definido, o log é habilitado. Imprime informações de log para console por padrão.

Definir o nível de log usando o trecho abaixo:

```ts
// Only need the warning and error messages.
setLogLevel(LogLevel.Warn);
```

Você pode redirecionar a saída do log definindo a função de log ou do log personalizado.

##### <a name="redirect-by-setting-custom-logger"></a>Redirecionar definindo o madeireiro personalizado

```ts
setLogLevel(LogLevel.Info);
// Set another logger if you want to redirect to Application Insights in Azure Function
setLogger(context.log);
```

##### <a name="redirect-by-setting-custom-log-function"></a>Redirecionar definindo a função de log personalizada

Observe que a função de log não terá efeito se você definir um madeireiro personalizado.

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

## <a name="see-also"></a>Confira também

[Galeria de exemplos do Microsoft TeamsFx](https://github.com/OfficeDev/TeamsFx-Samples)