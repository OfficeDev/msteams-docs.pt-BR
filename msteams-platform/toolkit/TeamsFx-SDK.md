---
title: TeamsFx SDK
author: MuyangAmigo
description: Sobre o SDK teamsFx
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 1e78827d4105eefb112bef40d059804a94050f2d
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453618"
---
# <a name="teamsfx-sdk-for-typescript-or-javascript"></a>SDK teamsFx para TypeScript ou JavaScript

O TeamsFx tem como objetivo reduzir tarefas de implementação de identidade e acesso a recursos de nuvem para instruções de linha única com configuração zero.

Use a biblioteca para:

* Acessar as principais funcionalidades no ambiente de cliente e servidor de maneira semelhante.
* Escreva o código de autenticação do usuário de maneira simplificada.

## <a name="get-started"></a>Introdução

O SDK do TeamsFx é pré-configurado no projeto com scaffolding usando o Kit de Ferramentas do TeamsFx ou a CLI.
Para obter mais informações, [consulte Teams projeto do aplicativo](https://github.com/OfficeDev/TeamsFx/blob/main/packages/vscode-extension/README.md).

### <a name="prerequisites"></a>Pré-requisitos

* Node.js versão ou `10.x.x` posterior.
* Se seu projeto instalou pacotes `botbuilder` [relacionados como](https://github.com/Microsoft/botbuilder-js#packages) dependências, verifique se eles são da mesma versão e a versão é `>= 4.9.3`. ([Problema - todos os pacotes BOTBUILDER devem ser a mesma versão](https://github.com/BotBuilderCommunity/botbuilder-community-js/issues/57#issuecomment-508538548))

Para saber mais, confira:

* [Código-fonte](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk)
* [Pacote (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx)
* [Documentação de referência de API](https://aka.ms/teamsfx-sdk-help)
* [Exemplos](https://github.com/OfficeDev/TeamsFx-Samples)

### <a name="install-the-microsoftteamsfx-package"></a>Instalar o `@microsoft/teamsfx` pacote

Instale o SDK do TeamsFx para TypeScript ou JavaScript com `npm`:

```bash
npm install @microsoft/teamsfx
```

### <a name="create-and-authenticate-microsoftgraphclient"></a>Criar e autenticar `MicrosoftGraphClient`

Para criar o objeto cliente graph para acessar a API Graph Microsoft, você precisará das credenciais para autenticar. O SDK fornece várias classes de credenciais para escolher que atendam a vários requisitos. Você precisa carregar a configuração antes de usar quaisquer credenciais.

* No ambiente do navegador, você precisa passar explicitamente os parâmetros de configuração. O projeto scaffolded React forneceu variáveis de ambiente a ser usadas.

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
    clientId: process.env.REACT_APP_CLIENT_ID,
  },
});
```

* No ambiente NodeJS, como a Função Azure, você pode simplesmente chamar `loadConfiguration`. Ele será carregado de variáveis de ambiente por padrão.

```ts
loadConfiguration();
```

#### <a name="using-teams-app-user-credential"></a>Usando Teams de usuário do aplicativo

Use o seguinte trecho:

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
    clientId: process.env.REACT_APP_CLIENT_ID,
  },
});
const credential = new TeamsUserCredential();
const graphClient = createMicrosoftGraphClient(credential, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
const profile = await graphClient.api("/me").get();
```

> [!NOTE]
> Você pode usar essa classe de credencial no aplicativo do navegador, como Teams Tab App.

#### <a name="using-microsoft-365-tenant-credential"></a>Usando Microsoft 365 de locatário

Microsoft 365 credencial de locatário não exige interagir com Teams usuário do Aplicativo. Você pode chamar o Microsoft Graph como aplicativo.

Use o seguinte trecho:

```ts
loadConfiguration();
const credential = new M365TenantCredential();
const graphClient = createMicrosoftGraphClient(credential);
const profile = await graphClient.api("/users/{object_id_of_another_people}").get();
```

## <a name="core-concepts-and-code-structure"></a>Principais conceitos e estrutura de código

### <a name="credentials"></a>Credenciais

Há três classes de credencial localizadas na pasta [de credenciais para](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/credential) ajudar a simplificar a autenticação.

Classes de credenciais implementam `TokenCredential` interface amplamente usada nas APIs da biblioteca do Azure. Eles foram projetados para fornecer tokens de acesso para escopos específicos. As seguintes classes de credenciais representam identidade diferente em determinados cenários:

* `TeamsUserCredential`representam Teams identidade do usuário atual. O uso dessa credencial solicitará o consentimento do usuário na primeira vez.
* `M365TenantCredential`representa Microsoft 365 identidade de locatário. Geralmente é usado quando o usuário não está envolvido, como o trabalho de automação disparado pelo tempo.
* `OnBehalfOfUserCredential` usa o fluxo em nome do fluxo. Ele precisa de um token de acesso e você pode obter um novo token para escopo diferente. Ele foi projetado para ser usado em cenários de Função do Azure ou Bot.

### <a name="bots"></a>Bots

As classes relacionadas a bot são armazenadas na [pasta bot](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/bot).

`TeamsBotSsoPrompt` pode integrar-se à estrutura bot. Simplifica o processo de autenticação para o desenvolvimento de aplicativo bot.

### <a name="helper-functions"></a>Funções auxiliares

O SDK teamsFx fornece funções auxiliares para facilitar a configuração para bibliotecas de terceiros. Eles estão localizados na [pasta principal](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/core).

### <a name="error-handling"></a>Tratamento de erros

A resposta de erro da API é `ErrorWithCode`, que contém o código de erro e a mensagem de erro.

Por exemplo, para filtrar um erro específico, você pode usar o seguinte trecho:

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

E se a instância de credencial for usada em outra biblioteca, como o Microsoft Graph, é possível que o erro seja capturado e transformado.

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

A seção a seguir fornece vários trechos de código para cenários comuns:

### <a name="use-graph-api-in-tab-app"></a>Usar Graph API no aplicativo guia

Use `TeamsUserCredential` e `createMicrosoftGraphClient`.

```ts
loadConfiguration({
  authentication: {
    initiateLoginEndpoint: process.env.REACT_APP_START_LOGIN_PAGE_URL,
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

Use `tedious` a biblioteca para acessar SQL e aproveitar `DefaultTediousConnectionConfiguration` que gerencia a autenticação.
Além de `tedious`, você também pode compor a configuração de conexão de outras bibliotecas SQL com base no resultado de `sqlConnectionConfig.getConfig()`.

```ts
loadConfiguration();
const sqlConnectConfig = new DefaultTediousConnectionConfiguration();
// If there's only one SQL database
const config = await sqlConnectConfig.getConfig();
// If there are multiple SQL databases
const config2 = await sqlConnectConfig.getConfig("your database name");
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

Você pode definir o nível de log do cliente e as saídas de redirecionamento ao usar essa biblioteca. O registro em log está desligado por padrão, você pode agará-lo definindo o nível de log.

#### <a name="enable-log-by-setting-log-level"></a>Habilitar o log definindo o nível de log

O registro em log só é habilitado quando você definir o nível de log. Por padrão, imprime informações de log para console.

Definir o nível de log usando o seguinte trecho:

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

> [!NOTE]
> A função log não terá efeito, se você definir um madeireiro personalizado.

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
