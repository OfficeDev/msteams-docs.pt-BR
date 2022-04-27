---
title: TeamsFx SDK
author: MuyangAmigo
description: Sobre o SDK do TeamsFx
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: ade31e39d48b92cca4309b16762dc95afccf1925
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073094"
---
# <a name="teamsfx-sdk"></a>TeamsFx SDK

O TeamsFx ajuda a reduzir as tarefas do desenvolvedor aproveitando o SSO do Teams e acessando recursos de nuvem para instruções de linha única sem configuração. O SDK do TeamsFx foi criado para ser usado no navegador e Node.js ambiente, cenários comuns incluem:

* Teams aplicativo guia
* Função do Azure
* Teams bot

Você pode usar o SDK do TeamsFx para:

* Acessar as principais funcionalidades no ambiente de cliente e servidor 
* Escrever código de autenticação de usuário de maneira simplificada

## <a name="prerequisites"></a>Pré-requisitos

Instale as seguintes ferramentas e configure seu ambiente de desenvolvimento:

* Versão mais recente do Node.js
* Se o projeto tiver instalado pacotes `botbuilder` [relacionados como](https://github.com/Microsoft/botbuilder-js#packages) dependências, verifique se eles são da mesma versão. Atualmente, a versão necessária é a 4.15.0 ou posterior. Para obter mais informações, consulte pacotes do construtor de bot devem ser [da mesma versão](https://github.com/BotBuilderCommunity/botbuilder-community-js/issues/57#issuecomment-508538548).

Você deve ter conhecimento prático do seguinte:

* [Código-fonte](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk)
* [Pacote (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx)
* [Documentação de referência de API](https://aka.ms/teamsfx-sdk-help)
* [Exemplos](https://github.com/OfficeDev/TeamsFx-Samples)

## <a name="get-started"></a>Introdução

O SDK do TeamsFx é pré-configurado no projeto com scaffolding usando o TeamsFx Toolkit ou a CLI.
Para obter mais informações, [consulte Teams projeto de aplicativo](https://github.com/OfficeDev/TeamsFx/blob/main/packages/vscode-extension/README.md).

### <a name="install-the-microsoftteamsfx-package"></a>Instalar o `@microsoft/teamsfx` pacote

Instale o SDK do TeamsFx para TypeScript ou JavaScript com `npm`:

```bash
npm install @microsoft/teamsfx
```

### <a name="create-microsoftgraphclient-service"></a>Criar `MicrosoftGraphClient` serviço

Para criar um objeto de cliente de grafo e acessar o microsoft API do Graph, você precisa das credenciais para autenticar. O SDK fornece APIs para configurar para desenvolvedores.

<br>

<details>
<summary><b>Invocar API do Graph em nome de Teams usuário (Identidade do Usuário)</b></summary>

Use o seguinte snippet:

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
<summary><b>Invocar API do Graph sem usuário (Identidade do Aplicativo)</b></summary>

Ele não requer a interação com o Teams usuário. Você pode chamar o Microsoft Graph como identidade do aplicativo.

Use o seguinte snippet:

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

A instância da classe TeamsFx acessa todas as configurações do TeamsFx de variáveis de ambiente por padrão. Você também pode definir valores de configuração personalizados para substituir os valores padrão. Verifique a [configuração de substituição](#override-configuration) para obter detalhes. Ao criar uma instância do TeamsFx, você também precisa especificar o tipo de identidade. Há dois tipos de identidade:

* Identidade do Usuário
* Identidade do Aplicativo

#### <a name="user-identity"></a>Identidade do Usuário

| Comando | Descrição |
|----------------|-------------|
| `new TeamsFx(IdentityType.User)`| O aplicativo é autenticado como usuário Teams atual. |
| `TeamsFx:setSsoToken()`| Identidade do usuário Node.js ambiente (sem navegador). |
| `TeamsFx:getUserInfo()` | Para obter informações básicas do usuário. |
| `TeamsFx:login()` | Ele é usado para permitir que o usuário execute o processo de consentimento, se você quiser usar o SSO para obter o token de acesso para determinados escopos do OAuth. |

> [!NOTE]
> Você pode acessar recursos em nome do usuário Teams atual.

#### <a name="application-identity"></a>Identidade do Aplicativo

| Comando | Descrição |
|----------------|-------------|
| `new TeamsFx(IdentityType.App)`| O aplicativo é autenticado como um aplicativo. A permissão geralmente precisa da aprovação do administrador.|
| `TeamsFx:getCredential()`| Ele fornece instâncias de credencial correspondentes automaticamente ao tipo de identidade. |

> [!NOTE]
> Você precisa do consentimento do administrador para recursos.

### <a name="credential"></a>Credential

Você deve escolher o tipo de identidade ao inicializar o TeamsFx. Depois de especificar o tipo de identidade ao inicializar o TeamsFx, o SDK usará diferentes tipos de classe de credencial para representar a identidade e obter o token de acesso pelo fluxo de autenticação correspondente.

Há três classes de credenciais para simplificar a autenticação. [pasta de credenciais](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/credential). As classes de credencial `TokenCredential` implementam a interface, que é amplamente usada em APIs de biblioteca do Azure, projetadas para fornecer tokens de acesso para escopos específicos. Outras APIs dependem da chamada de credencial `TeamsFx:getCredential()` para obter uma instância de `TokenCredential`.

Aqui estão os cenários correspondentes para cada destino de classe de credencial.

#### <a name="user-identity-in-browser-environment"></a>Identidade do Usuário no ambiente do navegador
`TeamsUserCredential`representa Teams identidade do usuário atual. O uso dessa credencial solicitará o consentimento do usuário na primeira vez. Ele aproveita o Teams SSO e o fluxo On-Behalf-Of para fazer a troca de tokens. O SDK usa essa credencial quando o desenvolvedor escolhe a identidade do usuário no ambiente do navegador.

Configuração necessária: `initiateLoginEndpoint`, `clientId`.

#### <a name="user-identity-in-nodejs-environment"></a>Identidade do usuário no Node.js ambiente
`OnBehalfOfUserCredential`usa o fluxo On-Behalf-Of e precisa Teams token de SSO. Ele foi projetado para ser usado em cenários de função ou bot do Azure. O SDK usa essa credencial quando o desenvolvedor escolhe a identidade do usuário Node.js ambiente.

Configuração necessária: `authorityHost`, `tenantId`, `clientId`ou `clientSecret` `certificateContent`.

#### <a name="application-identity-in-nodejs-environment"></a>Identidade do aplicativo no Node.js ambiente
`AppCredential` representa a identidade do aplicativo. Geralmente, ele é usado quando o usuário não está envolvido, como o trabalho de automação disparado por tempo. O SDK usa essa credencial quando o desenvolvedor escolhe a identidade do aplicativo Node.js ambiente.

Configuração necessária: `tenantId`, `clientId`ou `clientSecret` `certificateContent`.

### <a name="bot-sso"></a>Bot SSO

As classes relacionadas ao bot são armazenadas na [pasta do bot](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/bot).

`TeamsBotSsoPrompt` tem uma boa integração com o bot framework. Ele simplifica o processo de autenticação quando você desenvolve um aplicativo de bot e deseja aproveitar o SSO do bot.

Configuração necessária: `initiateLoginEndpoint`, `tenantId`, `clientId`e `applicationIdUri`.

### <a name="supported-functions"></a>Funções com suporte

O SDK do TeamsFx fornece várias funções para facilitar a configuração de bibliotecas de terceiros. Eles estão localizados na [pasta principal](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/core).

*  Microsoft Graph Service:`createMicrosoftGraphClient` e ajuda `MsGraphAuthProvider` para criar uma instância Graph autenticada.
*  SQL: retorna`getTediousConnectionConfig` uma configuração de conexão entediante.

Configuração necessária:
* `sqlServerEndpoint`, `sqlUsername`se `sqlPassword` você quiser usar a identidade do usuário
* `sqlServerEndpoint`, `sqlIdentityId` se você quiser usar a identidade MSI

### <a name="error-handling"></a>Tratamento de erros

A resposta de erro da `ErrorWithCode`API é , que contém o código de erro e a mensagem de erro. Por exemplo, para filtrar um erro específico, você pode usar o seguinte snippet:

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

Se a instância de credencial for usada em outra biblioteca, como o Microsoft Graph, é possível que o erro seja capturado e transformado.

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

A seção a seguir fornece vários snippets de código para cenários comuns:

<br>

<details>
<summary><b>Usar API do Graph aplicativo guia</b></summary>
 
Use `TeamsFx` e `createMicrosoftGraphClient`.

```ts
const teamsfx = new TeamsFx();
const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]);
const profile = await graphClient.api("/me").get();
```

</details>

<br>

<details>
<summary><b>Chamar a Função do Azure no aplicativo guia</b></summary>

Use `axios` a biblioteca para fazer uma solicitação HTTP para o Azure Function.

```ts
const teamsfx = new TeamsFx();
const token = teamsfx.getCredential().getToken(""); // Get SSO token for the use
// Call API hosted in Azure Functions on behalf of user
const apiEndpoint = teamsfx.getConfig("apiEndpoint");
const response = await axios.default.get(apiEndpoint + "api/httptrigger1", {
  headers: {
    authorization: "Bearer " + token,
  },
});
```

</details>

<br>

<details>
<summary><b>Acessar SQL banco de dados no Azure Functions</b></summary>


Use `tedious` a biblioteca para acessar SQL e aproveitar `DefaultTediousConnectionConfiguration` que gerencia a autenticação.
Além disso`tedious`, você também pode compor a configuração de conexão de SQL bibliotecas com base no resultado de `sqlConnectionConfig.getConfig()`.

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
<summary><b>Usar a autenticação baseada em certificado no Azure Functions</b></summary>

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
<summary><b>Usar API do Graph no aplicativo de bot</b></summary>

Adicionar `TeamsBotSsoPrompt` ao conjunto de diálogos.

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

Você pode definir o nível de log do cliente e redirecionar as saídas ao usar essa biblioteca. O registro em log é desativado por padrão. Você pode ativá-lo definindo o nível de log.

#### <a name="enable-log-by-setting-log-level"></a>Habilitar o log definindo o nível de log

O registro em log é habilitado somente quando você define o nível de log. Por padrão, ele imprime informações de log no console.

Defina o nível de log usando o seguinte snippet:

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
Você pode passar a configuração personalizada ao criar uma instância do TeamsFx para substituir a configuração padrão ou definir campos obrigatórios quando as variáveis de ambiente estiverem ausentes.

- Se você tiver criado um projeto guia usando VS Code Toolkit, os seguintes valores de configuração serão usados de variáveis de ambiente pré-configuradas:
  * authorityHost (REACT_APP_AUTHORITY_HOST)
  * tenantId (REACT_APP_TENANT_ID)
  * clientId (REACT_APP_CLIENT_ID)
  * initiateLoginEndpoint (REACT_APP_START_LOGIN_PAGE_URL)
  * applicationIdUri (REACT_APP_START_LOGIN_PAGE_URL)
  * apiEndpoint (REACT_APP_FUNC_ENDPOINT)
  * apiName (REACT_APP_FUNC_NAME)

- Se você tiver criado um projeto de função/bot do Azure usando VS Code Toolkit, os seguintes valores de configuração serão usados de variáveis de ambiente pré-configuradas:
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

Se você estiver usando a versão do SDK `loadConfiguration()`que tem, siga estas etapas para atualizar para a versão mais recente do SDK.
1. Remover `loadConfiguration()` e passar configurações personalizadas usando `new TeamsFx(IdentityType.User, { ...customConfig })`
2. Substituir `new TeamsUserCredential()` por `new TeamsFx()`
3. Substituir `new M365TenantCredential()` por `new TeamsFx(IdentityType.App)`
4. Substituir `new OnBehalfOfUserCredential(ssoToken)` por `new TeamsFx().setSsoToken(ssoToken)`
5. Passar a instância de `TeamsFx` funções auxiliares para substituir a instância de credencial

Para obter mais informações, consulte [a classe TeamsFx](#teamsfx-class).

## <a name="next-step"></a>Próxima etapa

[Exemplos](https://github.com/OfficeDev/TeamsFx-Samples) de projeto para exemplos detalhados sobre como usar o SDK do TeamsFx.

## <a name="see-also"></a>Confira também

[Galeria de exemplos do Microsoft TeamsFx](https://github.com/OfficeDev/TeamsFx-Samples).
