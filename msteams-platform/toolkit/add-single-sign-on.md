---
title: Adicionar logon único aos aplicativos do Teams
author: zyxiaoyuer
description: Neste módulo, saiba como adicionar o SSO (logon único) do Teams Toolkit, habilitar o suporte ao SSO, atualizar seu aplicativo para usar o SSO
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/20/2022
ms.openlocfilehash: 7318ffbfe6c0fff852f493c90afe9a832a827110
ms.sourcegitcommit: e5c45071421d257d68a73406137edff5bdc5a722
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68654509"
---
# <a name="add-single-sign-on-to-teams-app"></a>Adicionar o logon único ao aplicativo do Teams

O Microsoft Teams fornece a função de logon único para que o aplicativo obtenha o token de usuário do Teams conectado para acessar o Microsoft Graph e outras APIs. O Kit de Ferramentas do Teams facilita a interação abstraindo alguns dos fluxos Azure AD e integrações por trás de algumas APIs simples. Isso permite que você adicione recursos de SSO (logon único) facilmente ao aplicativo Teams.

Para aplicativos que interagem com o usuário em um chat, uma equipe ou um canal, o SSO se manifesta como um Cartão Adaptável, com o qual o usuário pode interagir para invocar o fluxo de consentimento do Azure AD.

## <a name="enable-sso-support"></a>Habilitar suporte a SSO

O Kit de Ferramentas do Teams ajuda você a adicionar o SSO aos seguintes recursos do Teams:

* Tab
* Bot
* Bot de notificação: restify server
* Bot de comando
* Extensão de mensagem

### <a name="add-sso-using-visual-studio-code"></a>Adicionar SSO usando Visual Studio Code

Para adicionar o SSO usando o Teams Toolkit no Visual Studio Code, siga estas etapas:

1. Abra o **Microsoft Visual Studio Code**.
2. Selecionar Captura de tela do :::image type="content" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png" alt-text="Kit de Ferramentas do Teams é um exemplo da opção Kit de Ferramentas do Teams Visual Studio Code."::: da barra de navegação à esquerda.
3. Selecione **Adicionar recursos em** **DESENVOLVIMENTO**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/add-sso/sso-add features.png" alt-text="A captura de tela mostra a opção Adicionar recursos na opção Desenvolvimento no Visual Studio Code.":::

   * Você também pode abrir a paleta de comandos e selecionar **Teams: Adicionar recursos**.

4. Selecione **Logon Único**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/add-sso/sso-select features.png" alt-text="A captura de tela mostra o recurso logon único realçado em vermelho no Visual Studio Code.":::

### <a name="add-sso-using-teamsfx-cli"></a>Adicionar SSO usando a CLI do TeamsFx

Você pode executar o `teamsfx add sso` comando no diretório **raiz do projeto**.

> [!NOTE]
> O recurso habilita o SSO para todos os recursos aplicáveis existentes. Siga as mesmas etapas para habilitar o SSO se você adicionar funcionalidade posteriormente ao projeto.

## <a name="customize-your-project-using-teams-toolkit"></a>Personalizar seu projeto usando o Kit de Ferramentas do Teams

A tabela a seguir lista as alterações que o Kit de Ferramentas do Teams faz em seu projeto:

| **Tipo** | **Arquivo**                                             | **Objetivo**                                                                                                                                                                               |
| -------- | ---------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Criar   | `aad.template.json` Sob `template/appPackage`      | Azure AD manifesto do aplicativo representa seu Azure AD aplicativo. `template/appPackage`ajuda a registrar um aplicativo Azure AD durante o estágio local de depuração ou provisionamento.                                |
| Modificar   | `manifest.template.json` Sob `template/appPackage` | Um `webApplicationInfo` objeto é adicionado ao modelo de manifesto do aplicativo Teams. O Teams requer esse campo para habilitar o SSO. A alteração está em vigor quando você dispara a depuração ou provisionamento local. |
| Criar   | `auth/tab`                                           | Código de referência, páginas de redirecionamento de `README.md` autenticação e arquivos são gerados neste caminho para um projeto de guia.                                                                                  |
| Criar   | `auth/bot`                                           | O código de referência, as páginas de redirecionamento `README.md` de autenticação e os arquivos são gerados nesse caminho para um projeto de bot.                                                                                  |

> [!NOTE]
> Ao adicionar o SSO, o Teams Toolkit não altera nada na nuvem até que você dispare a depuração local. Atualize seu código para garantir que o SSO esteja funcionando no projeto.

## <a name="update-your-application-to-use-sso"></a>Atualizar seu aplicativo para usar o SSO

Para habilitar o SSO em seu aplicativo, siga estas etapas:

> [!NOTE]
> Essas alterações são baseadas nos modelos que fazemos scaffold.

---

<br>
<br><details>
<summary><b>Projeto de guia </b></summary>

1. Copiar `auth-start.html` e `auth-end.htm`\*\* na `auth/public` pasta para `tabs/public/`. O Kit de Ferramentas do Teams registra esses dois pontos de Azure AD para Azure AD fluxo de redirecionamento.

2. Copiar `sso` pasta em `auth/tab` .`tabs/src/sso/`

   * `InitTeamsFx`: o arquivo implementa uma função que inicializa o SDK `GetUserProfile` do TeamsFx e abre o componente após a inicialização do SDK.

   * `GetUserProfile`: o arquivo implementa uma função que chama o Microsoft API do Graph para obter informações do usuário.

3. Executar `npm install @microsoft/teamsfx-react` em `tabs/`.

4. Adicione as seguintes linhas a serem `tabs/src/components/sample/Welcome.tsx` importadas `InitTeamsFx`:

   ```Bash

   import { InitTeamsFx } from "../../sso/InitTeamsFx";

   ```

5. Substitua a seguinte linha:

   `<AddSSO />` para `<InitTeamsFx />` substituir o componente `AddSso` pelo `InitTeamsFx` componente.

</details>
<details>
<summary><b>Projeto de bot </b></summary>

#### <a name="set-up-the-azure-ad-redirects"></a>Configurar os redirecionamentos Azure AD dados

1. Mover a `auth/bot/public` pasta para `bot/src`. Essa pasta contém páginas HTML hospedadas pelo aplicativo bot. Quando o fluxo de logon único é iniciado com Azure AD, ele redireciona o usuário para as páginas HTML.
1. Modifique-o `bot/src/index` para adicionar as rotas apropriadas `restify` às páginas HTML.

   ```ts
   const path = require("path");

   server.get(
     "/auth-*.html",
     restify.plugins.serveStatic({
       directory: path.join(__dirname, "public"),
     })
   );
   ```

#### <a name="update-your-app"></a>Atualize seu aplicativo

O manipulador de comandos `ProfileSsoCommandHandler` SSO usa um token Azure AD para chamar o Microsoft Graph. Esse token é obtido usando o token de usuário do Teams conectado. O fluxo é agrupado em uma caixa de diálogo que exibe uma caixa de diálogo de consentimento, se necessário.

1. Mover `profileSsoCommandHandler` o arquivo na `auth/bot/sso` pasta para `bot/src`. `ProfileSsoCommandHandler` A classe  é um manipulador de comandos de SSO para obter informações do usuário com o token SSO, seguir esse método e criar seu próprio manipulador de comandos de SSO.
1. Abra `package.json` o arquivo e verifique se a versão do SDK do Teamsfx >= 1.2.0.
1. Execute o `npm install isomorphic-fetch --save` comando na `bot` pasta.
1. Para o script ts, execute o `npm install copyfiles --save-dev` comando na pasta `bot` e substitua as seguintes linhas em `package.json`:

   ```json
   "build": "tsc --build && shx cp -r ./src/adaptiveCards ./lib/src",
   ```

    com 

   ```json
   "build": "tsc --build && shx cp -r ./src/adaptiveCards ./lib/src && copyfiles src/public/*.html lib/",
   ```

   Isso copia as páginas HTML usadas para redirecionamento de autenticação ao compilar o projeto de bot.

1. Para fazer com que o fluxo de consentimento do SSO funcione, substitua o seguinte código no `bot/src/index` arquivo:

   ```ts
   server.post("/api/messages", async (req, res) => {
     await commandBot.requestHandler(req, res);
   });
   ```

    com 

   ```ts
   server.post("/api/messages", async (req, res) => {
     await commandBot.requestHandler(req, res).catch((err) => {
       // Error message including "412" means it is waiting for user's consent, which is a normal process of SSO, sholdn't throw this error.
       if (!err.message.includes("412")) {
         throw err;
       }
     });
   });
   ```

1. Substitua as opções, por `ConversationBot` exemplo, para `bot/src/internal/initialize` adicionar a configuração de SSO e o manipulador de comandos de SSO:

   ```ts
   export const commandBot = new ConversationBot({
       ...
       command: {
           enabled: true,
           commands: [new HelloWorldCommandHandler()],
       },
   });
   ```

    com 

   ```ts
   import { ProfileSsoCommandHandler } from "../profileSsoCommandHandler";

   export const commandBot = new ConversationBot({
       ...
       // To learn more about ssoConfig, please refer teamsfx sdk document: https://docs.microsoft.com/microsoftteams/platform/toolkit/teamsfx-sdk
       ssoConfig: {
           aad :{
               scopes:["User.Read"],
           },
       },
       command: {
           enabled: true,
           commands: [new HelloWorldCommandHandler() ],
           ssoCommands: [new ProfileSsoCommandHandler()],
       },
   });
   ```

1. Registre seu comando no manifesto do aplicativo Teams. Abra `templates/appPackage/manifest.template.json`e adicione as seguintes linhas em `commands` seu `commandLists` bot:

   ```json
   {
     "title": "profile",
     "description": "Show user profile using Single Sign On feature"
   }
   ```

#### <a name="add-a-new-sso-command-to-the-bot-optional"></a>Adicionar um novo comando de SSO ao bot (opcional)

Depois de adicionar com êxito o SSO em seu projeto, você pode adicionar um novo comando de SSO.

1. Crie um novo arquivo, como ou `photoSsoCommandHandler.ts` `photoSsoCommandHandler.js` em e adicione `bot/src/` seu próprio manipulador de comandos de SSO para chamar API do Graph:

   ```TypeScript
   // for TypeScript:
   import { Activity, TurnContext, ActivityTypes } from "botbuilder";
   import "isomorphic-fetch";
   import {
       CommandMessage,
       TriggerPatterns,
       TeamsFx,
       createMicrosoftGraphClient,
       TeamsFxBotSsoCommandHandler,
       TeamsBotSsoPromptTokenResponse,
   } from "@microsoft/teamsfx";

   export class PhotoSsoCommandHandler implements TeamsFxBotSsoCommandHandler {
       triggerPatterns: TriggerPatterns = "photo";

       async handleCommandReceived(
           context: TurnContext,
           message: CommandMessage,
           tokenResponse: TeamsBotSsoPromptTokenResponse,
       ): Promise<string | Partial<Activity> | void> {
           await context.sendActivity("Retrieving user information from Microsoft Graph ...");

           const teamsfx = new TeamsFx().setSsoToken(tokenResponse.ssoToken);

           const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]);

           let photoUrl = "";
           try {
               const photo = await graphClient.api("/me/photo/$value").get();
               const arrayBuffer = await photo.arrayBuffer();
               const buffer=Buffer.from(arrayBuffer, 'binary');
               photoUrl = "data:image/png;base64," + buffer.toString("base64");
           } catch {
               // Could not fetch photo from user's profile, return empty string as placeholder.
           }
           if (photoUrl) {
               const photoMessage: Partial<Activity> = {
                   type: ActivityTypes.Message,
                   text: 'This is your photo:',
                   attachments: [
                       {
                           name: 'photo.png',
                           contentType: 'image/png',
                           contentUrl: photoUrl
                       }
                   ]
               };
               return photoMessage;
           } else {
               return "Could not retrieve your photo from Microsoft Graph. Please make sure you have uploaded your photo.";
           }
       }
   }
   ```

   ```javascript
   // for JavaScript:
   const { ActivityTypes } = require("botbuilder");
   require("isomorphic-fetch");
   const {
     createMicrosoftGraphClient,
     TeamsFx,
   } = require("@microsoft/teamsfx");

   class PhotoSsoCommandHandler {
     triggerPatterns = "photo";

     async handleCommandReceived(context, message, tokenResponse) {
       await context.sendActivity(
         "Retrieving user information from Microsoft Graph ..."
       );

       const teamsfx = new TeamsFx().setSsoToken(tokenResponse.ssoToken);

       const graphClient = createMicrosoftGraphClient(teamsfx, ["User.Read"]);

       let photoUrl = "";
       try {
         const photo = await graphClient.api("/me/photo/$value").get();
         const arrayBuffer = await photo.arrayBuffer();
         const buffer = Buffer.from(arrayBuffer, "binary");
         photoUrl = "data:image/png;base64," + buffer.toString("base64");
       } catch {
         // Could not fetch photo from user's profile, return empty string as placeholder.
       }
       if (photoUrl) {
         const photoMessage = {
           type: ActivityTypes.Message,
           text: "This is your photo:",
           attachments: [
             {
               name: "photo.png",
               contentType: "image/png",
               contentUrl: photoUrl,
             },
           ],
         };
         return photoMessage;
       } else {
         return "Could not retrieve your photo from Microsoft Graph. Please make sure you have uploaded your photo.";
       }
     }
   }

   module.exports = {
     PhotoSsoCommandHandler,
   };
   ```

1. Adicionar `PhotoSsoCommandHandler` instância à `ssoCommands` matriz em `bot/src/internal/initialize.ts`:

   ```ts
   // for TypeScript:
   import { PhotoSsoCommandHandler } from "../photoSsoCommandHandler";

   export const commandBot = new ConversationBot({
       ...
       command: {
           ...
           ssoCommands: [new ProfileSsoCommandHandler(), new PhotoSsoCommandHandler()],
       },
   });
   ```

   ```javascript
   // for JavaScript:
   ...
   const { PhotoSsoCommandHandler } = require("../photoSsoCommandHandler");

   const commandBot = new ConversationBot({
       ...
       command: {
           ...
           ssoCommands: [new ProfileSsoCommandHandler(), new PhotoSsoCommandHandler()]
       },
   });
   ...

   ```

1. Registre seu comando no manifesto do aplicativo Teams. Abra `templates/appPackage/manifest.template.json`e adicione as seguintes linhas em `commands` seu `commandLists` bot:

   ```JSON

   {
       "title": "photo",
       "description": "Show user photo using Single Sign On feature"
   }

   ```

</details>

<details>
<summary><b>Projeto de extensão de mensagem </b></summary>

A lógica de negócios de exemplo fornece um manipulador `TeamsBot` que estende TeamsActivityHandler e substitui `handleTeamsMessagingExtensionQuery`.

Você pode atualizar a lógica de consulta no `handleMessageExtensionQueryWithToken` token com, que é obtido usando o token de usuário do Teams conectado.

Para fazer isso funcionar em seu aplicativo:

1. Mover a `auth/bot/public` pasta para `bot`. Essa pasta contém páginas HTML hospedadas pelo aplicativo bot. Quando os fluxos de logon único são iniciados com Azure AD, Azure AD redirecionará o usuário para essas páginas.

1. Modifique-o `bot/index` para adicionar as rotas `restify` apropriadas a essas páginas.

    ```ts
    const path = require("path");

    server.get(
        "/auth-*.html",
        restify.plugins.serveStatic({
            directory: path.join(__dirname, "public"),
        })
    );
    ```

1. Substitua `handleTeamsMessagingExtensionQuery` a interface em `bot/teamsBot`. Você pode seguir o código de exemplo para `handleMessageExtensionQueryWithToken` fazer sua própria lógica de consulta.

1. Abra `bot/package.json`, verifique se a `@microsoft/teamsfx` versão >= 1.2.0

1. Instale `isomorphic-fetch` pacotes npm em seu projeto de bot.

1. (Somente para ts) Instale `copyfiles` pacotes npm em seu projeto de bot, adicione ou atualize o `build` script `bot/package.json` da seguinte maneira:

    ```json
    "build": "tsc --build && copyfiles ./public/*.html lib/",
    ```

    Ao fazer isso, as páginas HTML usadas para redirecionamento de autenticação serão copiadas ao compilar esse projeto de bot.

1. Atualize `templates/appPackage/aad.template.json` seus escopos que foram usados em `handleMessageExtensionQueryWithToken`.

    ```json
    "requiredResourceAccess": [
        {
            "resourceAppId": "Microsoft Graph",
            "resourceAccess": [
                {
                    "id": "User.Read",
                    "type": "Scope"
                }
            ]
        }
    ]
    ```

</details>

<br>

## <a name="debug-your-application"></a>Depurar seu aplicativo

Pressione F5 para depurar seu aplicativo. O Teams Toolkit usa o Azure AD de manifesto para registrar um Azure AD aplicativo para SSO. Para funcionalidades locais de depuração do Kit de Ferramentas do Teams, consulte [Depurar seu aplicativo teams localmente](debug-local.md).

## <a name="customize-azure-ad-application-registration"></a>Personalizar Azure AD registro de aplicativo

O [Azure AD do aplicativo](/azure/active-directory/develop/reference-app-manifest) permite que você personalize vários aspectos do registro do aplicativo. Você pode atualizar o manifesto conforme necessário. Se você precisar incluir mais permissões de API para acessar as APIs desejadas, consulte as permissões de [API para acessar as APIs desejadas](https://github.com/OfficeDev/TeamsFx/wiki/#customize-aad-manifest-template).
Para exibir seu Azure AD no portal do Azure, consulte [Exibir Azure AD aplicativo em portal do Azure](https://github.com/OfficeDev/TeamsFx/wiki/Manage-AAD-application-in-Teams-Toolkit#How-to-view-the-AAD-app-on-the-Azure-portal).

## <a name="sso-authentication-concepts"></a>Conceitos de autenticação de SSO

Os seguintes conceitos ajudam você com a autenticação de SSO:

### <a name="working-of-sso-in-teams"></a>Trabalhando com SSO no Teams

A autenticação de SSO (logon único) no Microsoft Azure Active Directory (Azure AD) atualiza silenciosamente o token de autenticação para minimizar o número de vezes que os usuários precisam inserir suas credenciais de entrada. Se os usuários concordarem em usar seu aplicativo, eles não precisarão fornecer consentimento novamente em outro dispositivo, pois eles são conectados automaticamente.

Guias e bots do Teams têm um fluxo semelhante para suporte a SSO. Para saber mais, veja:

1. [Autenticação de SSO (logon único) no Tabs](../tabs/how-to/authentication/tab-sso-overview.md)
1. [Autenticação de SSO (logon único) no Bots](../bots/how-to/authentication/auth-aad-sso-bots.md)

### <a name="simplified-sso-with-teamsfx"></a>SSO simplificado com o TeamsFx

O TeamsFx ajuda a reduzir as tarefas do desenvolvedor usando o SSO e acessando recursos de nuvem para instruções de linha única sem configuração.

Com o SDK do TeamsFx, você pode escrever código de autenticação de usuário de maneira simplificada usando Credenciais:

1. Identidade do usuário no ambiente do navegador: `TeamsUserCredential` representa a identidade do usuário atual do Teams.
1. Identidade do usuário Node.js ambiente: `OnBehalfOfUserCredential` usa o fluxo On-Behalf-Of e o token de SSO.
1. Identidade do aplicativo Node.js ambiente: `AppCredential` representa a identidade do aplicativo.

Para obter mais informações sobre o SDK do TeamsFx, consulte:

* [Referência de API ou SDK do TeamsFx](TeamsFx-SDK.md) [](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true)
* [Galeria de exemplos do Microsoft Teams Framework (TeamsFx)](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2)

## <a name="see-also"></a>Confira também

[Pré-requisitos para criar seu aplicativo teams](tools-prerequisites.md)
