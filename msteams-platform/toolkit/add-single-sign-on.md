---
title: Adicionar logon único aos aplicativos do Teams
author: zyxiaoyuer
description: Neste módulo, saiba como adicionar o SSO (logon único) do Teams Toolkit, habilitar o suporte ao SSO, atualizar seu aplicativo para usar o SSO
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/20/2022
ms.openlocfilehash: b2016cefcdf476e32860f80a76606c04bf892f5d
ms.sourcegitcommit: dccb48902e08484692ab927415bcd3d61dc50db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2022
ms.locfileid: "67806791"
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

### <a name="add-sso-using-visual-studio-code"></a>Adicionar SSO usando Visual Studio Code

As etapas a seguir ajudam você a adicionar o SSO usando o Teams Toolkit no Visual Studio Code

1. Abra o **Microsoft Visual Studio Code**.
2. Selecione Adicionar barra lateral :::image type="content" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png" alt-text="do SSO do Kit"::: de Ferramentas do Teams na barra de navegação esquerda.
3. Selecione **Adicionar recursos em** **DESENVOLVIMENTO**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-sso/sso-add features.png" alt-text="recursos de adição de SSO":::

    * Você também pode abrir a paleta de comandos e selecionar **Teams: Adicionar recursos**

4. Selecione **Logon Único**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/add-sso/sso-select features.png" alt-text="sso select":::

### <a name="add-sso-using-teamsfx-cli"></a>Adicionar SSO usando a CLI do TeamsFx

Você pode executar o `teamsfx add sso` comando no diretório **raiz do projeto**

> [!Note]
> O recurso habilita o SSO para todos os recursos aplicáveis existentes. Siga as mesmas etapas para habilitar o SSO se você adicionar funcionalidade posteriormente ao projeto.

## <a name="customize-your-project-using-teams-toolkit"></a>Personalizar seu projeto usando o Kit de Ferramentas do Teams

A tabela a seguir lista as alterações que o Kit de Ferramentas do Teams faz em seu projeto:

   |**Tipo**|**Arquivo**|**Objetivo**|
   |--------|--------|-----------|
   |Criar|`aad.template.json` Sob `template/appPackage`|Azure AD manifesto do aplicativo representa seu Azure AD aplicativo. `template/appPackage`ajuda a registrar um aplicativo Azure AD durante o estágio local de depuração ou provisionamento.|
   |Modificar|`manifest.template.json` Sob `template/appPackage`|Um `webApplicationInfo` objeto é adicionado ao modelo de manifesto do aplicativo Teams. O Teams requer esse campo para habilitar o SSO. A alteração está em vigor quando você dispara a depuração ou provisionamento local.|
   |Criar|`auth/tab`|O código de referência, as páginas de redirecionamento de autenticação e um `README.md` arquivo são gerados nesse caminho para um projeto de guia.|
   |Criar|`auth/bot`|O código de referência, as páginas de redirecionamento de autenticação e um `README.md` arquivo são gerados nesse caminho para um projeto de bot.|

> [!Note]
> Ao adicionar o SSO, o Teams Toolkit não altera nada na nuvem até que você dispare a depuração local. Atualize seu código para garantir que o SSO esteja funcionando no projeto.

## <a name="update-your-application-to-use-sso"></a>Atualizar seu aplicativo para usar o SSO

As etapas a seguir ajudam você a habilitar o SSO em seu aplicativo.

> [!NOTE]
> Essas alterações são baseadas nos modelos que fazemos scaffold.

---
<br>
<br><details>
<summary><b>Projeto de guia </b></summary>

1. Copiar `auth-start.html` e `auth-end.htm`** na `auth/public` pasta para `tabs/public/`. O Kit de Ferramentas do Teams registra esses dois pontos de Azure AD para Azure AD fluxo de redirecionamento.

2. Copiar `sso` pasta em `auth/tab` .`tabs/src/sso/`

    * `InitTeamsFx`: o arquivo implementa uma função que inicializa o SDK `GetUserProfile` do TeamsFx e abre o componente após a inicialização do SDK

    * `GetUserProfile`: o arquivo implementa uma função que chama o Microsoft API do Graph para obter informações do usuário

3. Executar `npm install @microsoft/teamsfx-react` em `tabs/`.

4. Adicione as seguintes linhas a serem `tabs/src/components/sample/Welcome.tsx` importadas `InitTeamsFx`:

    ```Bash

    import { InitTeamsFx } from "../../sso/InitTeamsFx";

    ```

5. Substitua a seguinte linha: `<AddSSO />` para `<InitTeamsFx />` substituir o componente `AddSso` pelo `InitTeamsFx` componente.

</details>
<details>
<summary><b>Projeto de bot </b></summary>

1. Copiar `auth/bot/public` pasta para `bot/src`. As duas pastas contêm páginas HTML usadas para redirecionamento de autenticação. `bot/src/index` Você precisa modificar o arquivo para adicionar o roteamento a essas páginas.

2. Copiar `auth/bot/sso` pasta para `bot/src`. As duas pastas contêm três arquivos como referência para implementação de SSO:

    * `showUserInfo`: ele implementa uma função para obter informações do usuário com o token de SSO. Você pode seguir isso para criar seu próprio método que requer token de SSO.

    * `ssoDialog`: ele cria um [ComponentDialog](/javascript/api/botbuilder-dialogs/componentdialog?view=botbuilder-ts-latest&preserve-view=true) que é usado para SSO.

    * `teamsSsoBot`: ele cria um [TeamsActivityHandler](/javascript/api/botbuilder/teamsactivityhandler?view=botbuilder-ts-latest&preserve-view=true) com `ssoDialog` e adiciona `showUserInfo` como um comando que pode ser disparado.

3. Siga o exemplo de código e registre seu próprio comando `addCommand` neste arquivo (opcional).

4. Executar `npm install isomorphic-fetch` em `bot/`.

5. Execute `npm install copyfiles` em `bot/` e substitua a seguinte linha em package.json:
  
   ```JSON

   "build": "tsc --build",

    ```

    com 

   ```JSON

   "build": "tsc --build && copyfiles public/*.html lib/",

   ```

   As páginas HTML usadas para redirecionamento de autenticação são copiadas durante a criação desse projeto de bot.

6. Depois de adicionar os arquivos a seguir, você precisará criar uma nova instância `teamsSsoBot` no `bot/src/index` arquivo. Substitua o seguinte código:

   ```Bash
  
   // Process Teams activity with Bot Framework.
   server.post("/api/messages", async (req, res) => {
   await commandBot.requestHandler(req, res);
   });  

   ```

    com 

   ```Bash

   const handler = new TeamsSsoBot();
   // Process Teams activity with Bot Framework.
   server.post("/api/messages", async (req, res) => {
       await commandBot.requestHandler(req, res, async (context)=> {
           await handler.run(context);
       });
   });

   ```

7. Adicione as rotas HTML no `bot/src/index` arquivo:

   ```Bash

   server.get(
       "/auth-*.html",
       restify.plugins.serveStatic({
           directory: path.join(__dirname, "public"),
       })
   );

   ```

8. Adicione as seguintes linhas a serem `bot/src/index` importadas `teamsSsoBot` e `path`:

   ```Bash

   // For ts:
   import { TeamsSsoBot } from "./sso/teamsSsoBot";
   const path = require("path");

   // For js:
   const { TeamsSsoBot } = require("./sso/teamsSsoBot");
   const path = require("path");

   ```

9. Registre seu comando no manifesto do aplicativo Teams. Abra `templates/appPackage/manifest.template.json`e adicione as seguintes linhas em `command` seu `commandLists` bot:

   ```JSON

   {
       "title": "show",
       "description": "Show user profile using Single Sign On feature"
   }

   ```

</details>
<details>
<summary><b>Adicionar um novo comando ao bot </b></summary>

> [!NOTE]
> Atualmente, essas instruções se aplicam a `command bot`. Se você começar com um `bot`exemplo de [bot-sso](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2/bot-sso).

As etapas a seguir ajudam você a adicionar um novo comando, depois de adicionar o SSO ao seu projeto:

1. Crie um novo arquivo (`todo.ts`ou`todo.js`) em `bot/src/` e adicione sua própria lógica de negócios para chamar API do Graph:

# <a name="typescript"></a>[TypeScript](#tab/typescript)

   ```typescript
   // for TypeScript:
export async function showUserImage(
    context: TurnContext,
    ssoToken: string,
    param: any[]
): Promise<DialogTurnResult> {
    await context.sendActivity("Retrieving user photo from Microsoft Graph ...");

    // Init TeamsFx instance with SSO token
    const teamsfx = new TeamsFx().setSsoToken(ssoToken);

    // Update scope here. For example: Mail.Read, etc.
    const graphClient = createMicrosoftGraphClient(teamsfx, param[0]);
    
    // You can add following code to get your photo:
    // let photoUrl = "";
    // try {
    //   const photo = await graphClient.api("/me/photo/$value").get();
    //   photoUrl = URL.createObjectURL(photo);
    // } catch {
    //   // Could not fetch photo from user's profile, return empty string as placeholder.
    // }
    // if (photoUrl) {
    //   await context.sendActivity(
    //     `You can find your photo here: ${photoUrl}`
    //   );
    // } else {
    //   await context.sendActivity("Could not retrieve your photo from Microsoft Graph. Please make sure you have uploaded your photo.");
    // }

    return;
}  
   ```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

   ```javaScript
   // for JavaScript:
export async function showUserImage(context, ssoToken, param) {
    await context.sendActivity("Retrieving user photo from Microsoft Graph ...");

    // Init TeamsFx instance with SSO token
    const teamsfx = new TeamsFx().setSsoToken(ssoToken);

    // Update scope here. For example: Mail.Read, etc.
    const graphClient = createMicrosoftGraphClient(teamsfx, param[0]);
    
    // You can add following code to get your photo:
    // let photoUrl = "";
    // try {
    //   const photo = await graphClient.api("/me/photo/$value").get();
    //   photoUrl = URL.createObjectURL(photo);
    // } catch {
    //   // Could not fetch photo from user's profile, return empty string as placeholder.
    // }
    // if (photoUrl) {
    //   await context.sendActivity(
    //     `You can find your photo here: ${photoUrl}`
    //   );
    // } else {
    //   await context.sendActivity("Could not retrieve your photo from Microsoft Graph. Please make sure you have uploaded your photo.");
    // }

    return;
}
   ```

---

2. Registrar um novo comando

   * Adicione a seguinte linha para o novo registro de comando usando `addCommand` em `teamsSsoBot`:

     ```bash

     this.dialog.addCommand("ShowUserProfile", "show", showUserInfo);

     ```

   * Adicione as seguintes linhas após a linha acima para registrar um novo comando `photo` e conectar-se ao método `showUserImage` adicionado acima:

     ```bash

     // As shown here, you can add your own parameter into the `showUserImage` method
     // You can also use regular expression for the command here
     const scope = ["User.Read"];
     this.dialog.addCommand("ShowUserPhoto", new RegExp("photo\s*.*"), showUserImage, scope);

     ```

3. Registre seu comando no manifesto do aplicativo Teams. Abra `templates/appPackage/manifest.template.json`e adicione as seguintes linhas em `command` seu `commandLists` bot:

   ```JSON

   {
       "title": "photo",
       "description": "Show user photo using Single Sign On feature"
   }

   ```

</details>
<br>

## <a name="debug-your-application"></a>Depurar seu aplicativo

Pressione F5 para depurar seu aplicativo. O Teams Toolkit usa o Azure AD de manifesto para registrar um Azure AD aplicativo para SSO. Para funcionalidades locais de depuração do Kit de Ferramentas do Teams, consulte [Depurar seu aplicativo teams localmente](debug-local.md).

## <a name="customize-azure-ad-application-registration"></a>Personalizar Azure AD registro de aplicativo

O [Azure AD do aplicativo](/azure/active-directory/develop/reference-app-manifest) permite que você personalize vários aspectos do registro do aplicativo. Você pode atualizar o manifesto conforme necessário. Se você precisar incluir permissões de API adicionais para acessar as APIs desejadas, consulte as permissões de [API para acessar as APIs desejadas](https://github.com/OfficeDev/TeamsFx/wiki/#customize-aad-manifest-template).
Para exibir seu Azure AD aplicativo no Portal do Azure, consulte [Exibir Azure AD aplicativo no portal do Azure](https://github.com/OfficeDev/TeamsFx/wiki/Manage-AAD-application-in-Teams-Toolkit#How-to-view-the-AAD-app-on-the-Azure-portal).

## <a name="sso-authentication-concepts"></a>Conceitos de autenticação de SSO

Os seguintes conceitos ajudam você a autenticação de SSO:

### <a name="working-of-sso-in-teams"></a>Trabalhando com SSO no Teams

A autenticação de SSO (logon único) no Microsoft Azure Active Directory (Azure AD) atualiza silenciosamente o token de autenticação para minimizar o número de vezes que os usuários precisam inserir suas credenciais de entrada. Se os usuários concordarem em usar seu aplicativo, eles não precisarão fornecer consentimento novamente em outro dispositivo, pois eles são conectados automaticamente.

Guias e bots do Teams têm um fluxo semelhante para suporte a SSO. Para obter mais informações, consulte:

1. [Autenticação de SSO (logon único) no Tabs](../tabs/how-to/authentication/tab-sso-overview.md)
2. [Autenticação de SSO (logon único) no Bots](../bots/how-to/authentication/auth-aad-sso-bots.md)

### <a name="simplified-sso-with-teamsfx"></a>SSO simplificado com o TeamsFx

O TeamsFx ajuda a reduzir as tarefas do desenvolvedor usando o SSO e acessando recursos de nuvem para instruções de linha única sem configuração.

Com o SDK do TeamsFx, você pode escrever código de autenticação de usuário de maneira simplificada usando Credenciais:

1. Identidade do usuário no ambiente do navegador: `TeamsUserCredential` representa a identidade do usuário atual do Teams.
2. Identidade do usuário Node.js ambiente: `OnBehalfOfUserCredential` usa o fluxo On-Behalf-Of e o token de SSO.
3. Identidade do aplicativo Node.js ambiente: `AppCredential` representa a identidade do aplicativo.

Para obter mais informações sobre o SDK do TeamsFx, consulte:

* [Referência de API ou SDK do TeamsFx](TeamsFx-SDK.md) [](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true)
* [Galeria de exemplos do Microsoft Teams Framework (TeamsFx)](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2)

## <a name="see-also"></a>Confira também

* [Pré-requisitos para criar seu aplicativo teams](tools-prerequisites.md)
