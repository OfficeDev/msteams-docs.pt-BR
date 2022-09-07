---
title: TeamsFx SDK
author: surbhigupta
description: Neste módulo, saiba mais sobre o SDK do TeamsFx, os principais conceitos e a estrutura de código, personalização avançada e cenários
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: f4147a204fe4ff51c2015457fe62581adfd63c8d
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616867"
---
# <a name="teamsfx-sdk"></a>TeamsFx SDK

O TeamsFx ajuda a reduzir suas tarefas usando o SSO (Logon Único) do Microsoft Teams e acessando recursos de nuvem para instruções de linha única sem configuração. Você pode usar o SDK do TeamsFx no navegador e Node.js ambiente. As principais funcionalidades do TeamsFx podem ser acessadas no cliente, bem como no ambiente do servidor. Você pode escrever código de autenticação de usuário de maneira simplificada para:

* Guia Equipes
* Bot do Teams
* Função do Azure

## <a name="prerequisites"></a>Pré-requisitos

Você precisa instalar as seguintes ferramentas e configurar seu ambiente de desenvolvimento:

| &nbsp; | Instalar | Para usar... |
   | --- | --- | --- |
   | &nbsp; | [Visual Studio Code](https://code.visualstudio.com/download) | Ambientes de compilação JavaScript, TypeScript ou Estrutura do SharePoint (SPFx). Use a versão 1.55 ou posterior. |
   | &nbsp; | [Kit de ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)| Uma extensão Visual Studio Code Microsoft que cria um scaffolding de projeto para seu aplicativo. Use a versão 4.0.0. |
   | &nbsp; | [Node.js](https://nodejs.org/en/download/) | Ambiente de runtime do JavaScript de back-end. Use a versão mais recente do v16 LTS.|
   | &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | O Microsoft Teams para colaborar com todos com quem você trabalha por meio de aplicativos para chats, reuniões, chamadas - tudo em um só lugar.|
   | &nbsp; | [Microsoft&nbsp; Edge](https://www.microsoft.com/edge) (recomendado) ou [Google Chrome](https://www.google.com/chrome/) | Um navegador com ferramentas de desenvolvedor. |

> [!NOTE]
> Se seu projeto instalou `botbuilder` [pacotes](https://github.com/Microsoft/botbuilder-js#packages) relacionados como dependências, verifique se eles são da mesma versão.

Você deve ter conhecimento prático de:

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

## <a name="teamsfx-core-functionalities"></a>Principais funcionalidades do TeamsFx

### <a name="teamsfx-class"></a>Classe TeamsFx

A instância da classe TeamsFx acessa todas as configurações do TeamsFx de variáveis de ambiente por padrão. Você também pode definir valores de configuração personalizados para substituir os valores padrão. Verifique a [configuração de substituição](#override-configuration) para obter detalhes.
Ao criar uma instância do TeamsFx, você também precisa especificar o tipo de identidade.
Há dois tipos de identidade:

* **Identidade do** Usuário: representa o usuário atual do Teams.
* **Identidade do** Aplicativo: representa o próprio aplicativo.

    > [!NOTE]
    > Para esses dois tipos de identidade, os construtores e métodos do TeamsFx não são os mesmos.

Você pode saber mais sobre a identidade do usuário e a identidade do aplicativo na seção a seguir:

<details>
<summary><b> Identidade do usuário </b></summary>

| Comando | Descrição |
|----------------|-------------|
| `new TeamsFx(IdentityType.User)`| O aplicativo é autenticado como usuário atual do Teams. |
| `TeamsFx:setSsoToken()`| Identidade do usuário no ambiente node.js (sem navegador). |
| `TeamsFx:getUserInfo()` | Para obter informações básicas do usuário. |
| `TeamsFx:login()` | Ele é usado para permitir que o usuário execute o processo de consentimento, se desejar usar o SSO para obter o token de acesso para determinados escopos do OAuth. |

> [!NOTE]
> Você pode acessar recursos em nome do usuário atual do Teams.
</details>

<details>
<summary><b> Identidade do aplicativo </b></summary>

| Comando | Descrição |
|----------------|-------------|
| `new TeamsFx(IdentityType.App)`| O aplicativo  está autenticado como um aplicativo. A permissão geralmente precisa da aprovação do administrador.|
| `TeamsFx:getCredential()`| Ele fornece instâncias de credencial correspondentes automaticamente ao tipo de identidade. |

> [!NOTE]
> Você precisa do consentimento do administrador para recursos.
</details>

### <a name="credential"></a>Credential

Para inicializar o TeamsFx, você deve escolher o tipo de identidade necessário. Após especificar o tipo de identidade, o SDK usa um tipo diferente de classe de credencial. Eles ajudam a representar a identidade e obter o token de acesso pelo fluxo de autenticação correspondente. As classes de credencial `TokenCredential` implementam a interface amplamente usada nas APIs da biblioteca do Azure projetadas para fornecer tokens de acesso para escopos específicos. Outras APIs dependem da chamada da credencial `TeamsFx:getCredential()` para obter uma instância de `TokenCredential`. Para obter mais informações sobre classes relacionadas a credenciais e fluxo de autenticação, consulte [a pasta de credenciais](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/credential).

Há três classes de credenciais para simplificar a autenticação. Aqui estão os cenários correspondentes para cada meta de classe de credencial.

<details>
<summary><b> Identidade do Usuário no ambiente do navegador </b></summary>

`TeamsUserCredential` representa a identidade do usuário atual do Teams. Pela primeira vez, as credenciais do usuário são autenticadas, em seguida, o SSO do Teams faz o fluxo On-Behalf-Of para troca de tokens. O SDK usa essa credencial quando você escolhe a identidade do usuário no ambiente do navegador.

As configurações necessárias são: `initiateLoginEndpoint` e `clientId`.
</details>

<details>
<summary><b> Identidade do usuário no Node.js ambiente </b></summary>

`OnBehalfOfUserCredential` usa o fluxo On-Behalf-Of e exige o token de SSO do Teams, em cenários de função ou bot do Azure. O SDK do TeamsFx usa a seguinte credencial quando você escolhe a identidade do usuário Node.js ambiente.

Configuração necessária: `authorityHost`, `tenantId`, `clientId`, `clientSecret` ou `certificateContent`.
</details>

<details>
<summary><b> Identidade do aplicativo no Node.js ambiente </b></summary>

`AppCredential` representa a identidade do aplicativo. Você pode usar a identidade do aplicativo quando o usuário não está envolvido, por exemplo, em um trabalho de automação disparado por tempo. O SDK do TeamsFx usa a seguinte credencial quando você escolhe a identidade do aplicativo Node.js ambiente.

Configuração necessária: `tenantId`, `clientId`, `clientSecret` ou `certificateContent`.
</details>

### <a name="bot-sso"></a>Bot SSO

Classes relacionadas ao bot são armazenadas em [bot](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/bot).

`TeamsBotSsoPrompt` integra-se ao bot framework. Ele simplifica o processo de autenticação quando você desenvolve um aplicativo de bot e deseja usar o SSO do bot.

Configuração necessária: `initiateLoginEndpoint`, `tenantId`, `clientId` e `applicationIdUri`.

### <a name="supported-functions"></a>Funções com suporte

O SDK do TeamsFx fornece várias funções para facilitar a configuração de bibliotecas de terceiros. Eles estão localizados na [pasta principal](https://github.com/OfficeDev/TeamsFx/tree/main/packages/sdk/src/core).

* Serviço Microsoft Graph:`createMicrosoftGraphClient` e `MsGraphAuthProvider` ajudam a criar uma instância autenticada do Graph.
* SQL:`getTediousConnectionConfig` retorna uma configuração de conexão entediante.

Configuração necessária:

* Se você quiser usar a identidade do usuário `sqlServerEndpoint`e `sqlUsername` `sqlPassword` for necessário.
* Se você quiser usar a identidade MSI e `sqlServerEndpoint``sqlIdentityId` for necessário.

### <a name="override-configuration"></a>Substituir configuração

Você pode passar a configuração personalizada ao criar uma nova instância para substituir a `TeamsFx` configuração padrão ou definir campos obrigatórios quando `environment variables` estiverem ausentes.

<details>
<summary><b> Para projeto de guia </b> </summary>

Se você criou um projeto de guia usando o Microsoft Visual Studio Code Toolkit, os seguintes valores de configuração serão usados de variáveis de ambiente pré-configuradas:

* authorityHost (REACT_APP_AUTHORITY_HOST)
* tenantId (REACT_APP_TENANT_ID)
* clientId (REACT_APP_CLIENT_ID)
* initiateLoginEndpoint (REACT_APP_START_LOGIN_PAGE_URL)
* applicationIdUri (REACT_APP_START_LOGIN_PAGE_URL)
* apiEndpoint (REACT_APP_FUNC_ENDPOINT) // usado somente quando há uma função de back-end
* apiName (REACT_APP_FUNC_NAME) // usado somente quando há uma função de back-end

</details>

<details>
<summary><b> Para a função do Azure ou o projeto de bot </b></summary>

Se você criou uma função do Azure ou um projeto de bot usando o Visual Studio Code Toolkit, os seguintes valores de configuração serão usados de variáveis de ambiente pré-configuradas:

* initiateLoginEndpoint (INITIATE_LOGIN_ENDPOINT)
* authorityHost (M365_AUTHORITY_HOST)
* tenantId (M365_TENANT_ID)
* clientId (M365_CLIENT_ID)
* clientSecret (M365_CLIENT_SECRET)
* applicationIdUri (M365_APPLICATION_ID_URI)
* apiEndpoint (API_ENDPOINT)
* sqlServerEndpoint (SQL_ENDPOINT) // usado somente quando há uma instância sql
* sqlUsername (SQL_USER_NAME) // usado somente quando há uma instância sql
* sqlPassword (SQL_PASSWORD) // usado somente quando há uma instância sql
* sqlDatabaseName (SQL_DATABASE_NAME) // usado somente quando há uma instância sql
* sqlIdentityId (IDENTITY_ID) // usado somente quando há uma instância sql

</details>

### <a name="error-handling"></a>Tratamento de erros

O tipo básico de resposta de erro de API é `ErrorWithCode`, que contém o código de erro e a mensagem de erro. Por exemplo, para filtrar um erro específico, você pode usar o seguinte trecho de código:

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

## <a name="microsoft-graph-scenarios"></a>Cenários do Microsoft Graph

Esta seção fornece vários snippets de código para cenários comuns relacionados ao Microsoft Graph. Nesses cenários, o usuário pode chamar APIs usando permissões diferentes em diferentes extremidades (front-end/back-end).

* Permissão de representante do usuário no front-end (Usar TeamsUserCredential) <details>
    <summary><b>Usar a API do Graph no aplicativo guia</b></summary>

    Este snippet de código mostra como usar e `TeamsFx` obter `createMicrosoftGraphClient` perfis de usuário do Microsoft Graph. Ele também mostra como capturar e resolver um `GraphError`.

    1. Importe as classes necessárias.

    ```ts
    import {
      createMicrosoftGraphClient,
      TeamsFx,
    } from "@microsoft/teamsfx";
    ```

    2. Use `TeamsFx.login()` para obter o consentimento do usuário.

    ```ts
    // Put these code in a call-to-action callback function to avoid browser blocking automatically showing up pop-ups.
    await teamsfx.login(["User.Read"]); // Login with scope
    ```

    3. Você pode inicializar uma instância do TeamsFx e um cliente de grafo e obter informações do MS Graph por esse cliente.

    ```ts
    try {
      const teamsfx = new TeamsFx();
      const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]); // Initializes MS Graph SDK using our MsGraphAuthProvider
      const profile = await graphClient.api("/me").get();
    } catch (err: unknown) {
      // ErrorWithCode is handled by Graph client
      if (err instanceof GraphError && err.code?.includes(ErrorCode.UiRequiredError)) {
        // Need to show login button to ask for user consent.
      }
    }
    ```

    Para obter mais informações sobre como usar API do Graph aplicativo guia, consulte o exemplo [da guia Olá, Mundo](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/hello-world-tab).

    </details>

    <details>
    <summary><b>Integração com o Kit de Ferramentas do Microsoft Graph</b></summary>

    A [biblioteca do Kit de Ferramentas do Microsoft Graph (mgt)](https://aka.ms/mgt) é uma coleção de vários provedores de autenticação e componentes de interface do usuário da plataforma Microsoft Graph.

    O `@microsoft/mgt-teamsfx-provider` pacote expõe a classe `TeamsFxProvider` que usa a classe `TeamsFx` para conectar usuários e adquirir tokens para usar com o Graph.

    1. Você pode instalar os seguintes pacotes necessários:

    ```bash
    npm install @microsoft/mgt-element @microsoft/mgt-teamsfx-provider @microsoft/teamsfx
    ```

    2. Inicialize o provedor dentro do componente.

    ```ts
    // Import the providers and credential at the top of the page
    import {Providers} from '@microsoft/mgt-element';
    import {TeamsFxProvider} from '@microsoft/mgt-teamsfx-provider';
    import {TeamsUserCredential} from "@microsoft/teamsfx";

    const scope = ["User.Read"];
    const teamsfx = new TeamsFx();
    const provider = new TeamsFxProvider(teamsfx, scope);
    Providers.globalProvider = provider;
    ```

    3. Você pode usar o `teamsfx.login(scopes)` método para obter o token de acesso necessário.

    ```ts
    // Put these code in a call-to-action callback function to avoid browser blocking automatically showing up pop-ups. 
    await teamsfx.login(this.scope);
    Providers.globalProvider.setState(ProviderState.SignedIn);
    ```

    4. Agora você pode adicionar qualquer componente em sua página HTML `render()` ou em seu método com React para usar `TeamsFx` o contexto para acessar o Microsoft Graph.

    ```html
    <mgt-person query="me" view="threeLines"></mgt-person>
    ```

    ```ts
    public render(): void {
    return (
        <div>
            <Person personQuery="me" view={PersonViewType.threelines}></Person>
        </div>
    );
    }
    ```

    Para obter mais informações sobre o exemplo para inicializar o provedor TeamsFx, consulte o [exemplo exportador de contatos](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/graph-toolkit-contact-exporter).

    </details>

* Permissão de representante do usuário no back-end (Use OnBehalfOfUserCredential) <details>
    <summary><b>Usar API do Graph aplicativo de bot</b></summary>

    Este snippet de código mostra como usar `TeamsBotSsoPrompt` para definir uma caixa de diálogo e entrar para obter um token de acesso.

    1. Inicializar e adicionar ao `TeamsBotSsoPrompt` conjunto de diálogos.

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
    ```

    2. Inicie a caixa de diálogo e entre.

    ```ts
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

    Para obter mais informações sobre o exemplo para usar a API do graph no aplicativo de bot, consulte [o exemplo de bot-sso](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/bot-sso).

    </details>

    <details>
    <summary><b>Chamar a Função do Azure no aplicativo guia: Fluxo Em Nome de</b></summary>

    Este snippet de código `CreateApiClient` `axios` mostra como usar ou biblioteca para chamar o Azure Function e como chamar API do Graph função do Azure para obter perfis de usuário.

    1. Você pode usar o `CreateApiClient` SDK do TeamsFx para chamar o Azure Function:

    ```ts
    async function callFunction(teamsfx?: TeamsFx) {
      const teamsfx = new TeamsFx();

      // Get the credential.
      const credential = teamsfx.getCredential(); 
      // Create an API client by providing the token and endpoint.
      const apiClient = CreateApiClient(
        teamsfx.getConfig("YOUR_API_ENDPOINT"), // Create an API Client that uses SSO token to authenticate requests
        new BearerTokenAuthProvider(async () =>  (await credential.getToken(""))!.token) // Call API hosted in Azure Functions on behalf of user to inject token to request header
      );

      // Send a GET request to "RELATIVE_API_PATH", "/api/functionName" for example.
      const response = await apiClient.get("RELATIVE_API_PATH");
      return response.data;
    }
    ```

    Você também pode usar a `axios` biblioteca para chamar o Azure Function.

    ```ts
    async function callFunction(teamsfx?: TeamsFx) {
      const accessToken = await teamsfx.getCredential().getToken(""); // Get SSO token 
      // teamsfx.getConfig("apiEndpoint") will read REACT_APP_FUNC_ENDPOINT environment variable 
      const endpoint = teamsfx.getConfig("apiEndpoint");
      const response = await axios.default.get(endpoint + "/api/" + functionName, {
        headers: {
          authorization: "Bearer " + accessToken.token,
        },
      });
      return response.data;
    }
    ```

    2. Chame API do Graph na função do Azure em nome do usuário em resposta.

    ```ts
    export default async function run(
      context: Context,
      req: HttpRequest,
      teamsfxContext: TeamsfxContext
    ): Promise<Response> {
      const res: Response = { status: 200, body: {},};
      // ...
      teamsfx = new TeamsFx().setSsoToken(accessToken);
      // Query user's information from the access token.
      try {
        const currentUser: UserInfo = await teamsfx.getUserInfo();
        if (currentUser && currentUser.displayName) {
          res.body.userInfoMessage = `User display name is ${currentUser.displayName}.`;
        } else {
          res.body.userInfoMessage = "No user information was found in access token.";
        }
      } catch (e) {
      }
      // Create a graph client to access user's Microsoft 365 data after user has consented.
      try {
        const graphClient: Client = createMicrosoftGraphClient(teamsfx, [".default"]);
        const profile: any = await graphClient.api("/me").get();
        res.body.graphClientMessage = profile;
      } catch (e) {
      }
      return res;
    }
    ```

    Para obter mais informações sobre o exemplo para usar a API do graph no aplicativo de bot, consulte  [o exemplo hello-world-tab-with-backend](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/hello-world-tab-with-backend).

    </details>

* Permissão do aplicativo no back-end <details>
    <summary><b>Use a autenticação baseada em certificado na função do Azure</b></summary>

    Este snippet de código mostra como usar a permissão de aplicativo baseada em certificado para obter o token que pode ser usado para chamar API do Graph.

    1. Você pode inicializar fornecendo `authConfig` um `PEM-encoded key certificate`.

    ```ts
    const authConfig = {
      clientId: process.env.M365_CLIENT_ID,
      certificateContent: "The content of a PEM-encoded public/private key certificate",
      authorityHost: process.env.M365_AUTHORITY_HOST,
      tenantId: process.env.M365_TENANT_ID,
    };
    ```

    2. Você pode usar o `authConfig` token para obter o token.

    ```ts
    const teamsfx = new TeamsFx(IdentityType.App);
    teamsfx.setCustomeConfig(authConfig);
    const token = teamsfx.getCredential().getToken();
    ```

    </details>

    <details>
    <summary><b>Usar a autenticação de segredo do cliente no Azure Functions</b></summary>

    Este snippet de código mostra como usar a permissão de aplicativo de segredo do cliente para obter o token que pode ser usado para chamar API do Graph.

    1. Você pode inicializar fornecendo `authConfig` um `client secret`.

    ```ts
    const authConfig = {
      clientId: process.env.M365_CLIENT_ID,
      clientSecret: process.env.M365_CLIENT_SECRET,
      authorityHost: process.env.M365_AUTHORITY_HOST,
      tenantId: process.env.M365_TENANT_ID,
    };
    ```

    2. Você pode usar o `authConfig` token para obter o token.

    ```ts
    const teamsfx = new TeamsFx(IdentityType.App);
    teamsfx.setCustomeConfig(authConfig);
    const token = teamsfx.getCredential().getToken();
    ```

    Para obter mais informações sobre como usar a API do graph no aplicativo de bot, consulte o exemplo [hello-world-tab-with-backend](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/hello-world-tab-with-backend).

    </details>

## <a name="other-scenarios"></a>Outros cenários

Esta seção fornece vários snippets de código para outros cenários relacionados ao Microsoft Graph. Você pode criar um cliente de API no Bot ou no Azure Function e acessar o banco de dados SQL no Azure Functions.

  <details>
  <summary><b>Criar um cliente de API para chamar a API existente no Bot ou no Azure Functions</b></summary>

  Este snippet de código mostra como chamar uma API existente no Bot por `ApiKeyProvider`.

  ```ts
  const teamsfx = new TeamsFx();

  // Create an API Key auth provider. In addition to APiKeyProvider, following auth providers are also available:
  // BearerTokenAuthProvider, BasicAuthProvider, CertificateAuthProvider.
  const authProvider = new ApiKeyProvider("YOUR_API_KEY_NAME",
    teamsfx.getConfig("YOUR_API_KEY_VALUE"), // This reads the value of YOUR_API_KEY_VALUE environment variable.
    ApiKeyLocation.Header
  );

  // Create an API client using above auth provider.
  // You can also implement AuthProvider interface and use it here.
  const apiClient = createApiClient(
    teamsfx.getConfig("YOUR_API_ENDPOINT"), // This reads YOUR_API_ENDPOINT environment variable.
    authProvider
  );

  // Send a GET request to "RELATIVE_API_PATH", "/api/apiname" for example.
  const response = await apiClient.get("RELATIVE_API_PATH");
  ```

  </details>

  <details>
  <summary><b>Acessar ao Banco de dados SQL in Função do Azure</b></summary>

  Use `tedious` a biblioteca para acessar o SQL e usar que `DefaultTediousConnectionConfiguration` gerencia a autenticação. Você também pode compor a configuração de conexão de outras bibliotecas SQL com base no resultado de `sqlConnectionConfig.getConfig()`.

  1. Defina a configuração de conexão.

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
  const config2 = await getTediousConnectionConfig(teamsfx, "your database name");
  ```

  2. Conecte-se ao banco de dados.

  ```ts
  const connection = new Connection(config);
  connection.on("connect", (error) => {
    if (error) {
      console.log(error);
    }
  });
  ```

  > [!NOTE]
  > Para obter mais informações sobre o exemplo para acessar o banco de dados SQL na função do Azure, consulte [o exemplo de compartilhamento agora](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/share-now).

</details>

## <a name="advanced-customization"></a>Personalização avançada

### <a name="configure-log"></a>Configurar log

Você pode definir o nível de log do cliente e redirecionar as saídas ao usar essa biblioteca.

> [!NOTE]
> O registro em log está desativado por padrão. Você pode ativá-lo definindo o nível de log.

#### <a name="enable-log-by-setting-log-level"></a>Habilitar o log definindo o nível de log

Quando você define o nível de log, o log é habilitado. Ele imprime informações de log no console por padrão.

Defina o nível de log usando o seguinte trecho de código:

```ts
// Only need the warning and error messages.
setLogLevel(LogLevel.Warn);
```

> [!NOTE]
> Você pode redirecionar a saída do log definindo o agente personalizado ou a função de log.

#### <a name="redirect-by-setting-custom-logger"></a>Redirecionar definindo o agente personalizado

```ts
setLogLevel(LogLevel.Info);
// Set another logger if you want to redirect to Application Insights in Azure Function
setLogger(context.log);
```

#### <a name="redirect-by-setting-custom-log-function"></a>Redirecionar definindo a função de log personalizada

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

> [!NOTE]
> As funções de log não entrarão em vigor se você definir um agente personalizado.

## <a name="upgrade-latest-sdk-version"></a>Atualizar a versão mais recente do SDK

Se você estiver usando a versão do SDK `loadConfiguration()`que tem, siga estas etapas para atualizar para a versão mais recente do SDK:

1. Remova `loadConfiguration()` e passe as configurações personalizadas usando `new TeamsFx(IdentityType.User, { ...customConfig })`
2. Substitua `new TeamsUserCredential()` por `new TeamsFx()`.
3. Substitua `new M365TenantCredential()` por `new TeamsFx(IdentityType.App)`.
4. Substitua `new OnBehalfOfUserCredential(ssoToken)` por `new TeamsFx().setSsoToken(ssoToken)`.
5. Passe a instância de funções `TeamsFx` auxiliares para substituir a instância de credencial.

## <a name="next-step"></a>Próxima etapa

Para obter exemplos detalhados sobre como usar o projeto De [exemplos](https://github.com/OfficeDev/TeamsFx-Samples) do SDK do TeamsFx.

## <a name="see-also"></a>Confira também

[Galeria de exemplos do Microsoft TeamsFx](https://github.com/OfficeDev/TeamsFx-Samples).
