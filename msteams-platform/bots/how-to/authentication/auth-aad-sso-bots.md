---
title: Suporte de logon único para bots
description: Descreve como obter um token de usuário. Atualmente, um desenvolvedor de bot pode usar um cartão de visita ou o serviço de bot do azure com o suporte ao cartão OAuth.
keywords: token, token de usuário, suporte a SSO para bots
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 8da2591c3685b5bd3dffd272abd77babe94ab04c
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020046"
---
# <a name="single-sign-on-sso-support-for-bots"></a>Suporte a SSO (login único) para bots

A autenticação de entrada única no Azure Active Directory (AAD) minimiza o número de vezes que os usuários precisam inserir suas credenciais de entrada atualize silenciosamente o token de autenticação. Se os usuários concordarem em usar seu aplicativo, eles não precisarão fornecer consentimento novamente em outro dispositivo e podem entrar automaticamente. O fluxo é semelhante ao do suporte ao [SSO](../../../tabs/how-to/authentication/auth-aad-sso.md)da guia do Microsoft Teams , no entanto, a diferença está no protocolo de como um bot solicita [tokens](#request-a-bot-token) e recebe [respostas.](#receive-the-bot-token)

>[!NOTE]
> OAuth 2.0 é um padrão aberto para autenticação e autorização usada pela AAD e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams.

## <a name="bot-sso-at-runtime"></a>SSO de bot em tempo de execução

![SSO de bot no diagrama de tempo de execução](../../../assets/images/bots/bots-sso-diagram.png)

Conclua as etapas a seguir para obter tokens de aplicativo de bot e autenticação:

1. O bot envia uma mensagem com um OAuthCard que contém a `tokenExchangeResource` propriedade. Ele diz ao Teams para obter um token de autenticação para o aplicativo bot. O usuário recebe mensagens em todos os pontos de extremidade do usuário ativo.

    > [!NOTE]
    >* Um usuário pode ter mais de um ponto de extremidade ativo por vez.
    >* O token de bot é recebido de cada ponto de extremidade do usuário ativo.
    >* O aplicativo deve ser instalado em escopo pessoal para suporte a SSO.

2. Se o usuário atual estiver usando seu aplicativo bot pela primeira vez, um prompt de solicitação será exibido solicitando que o usuário faça um dos seguintes:
    * Forneça consentimento, se necessário.
    * Manipular a autenticação de etapa, como a autenticação de dois fatores.

3. O Teams solicita o token de aplicativo bot do ponto de extremidade do AAD para o usuário atual.

4. O AAD envia o token de aplicativo bot para o aplicativo teams.

5. O Teams envia o token para o bot como parte do objeto value retornado pela atividade de invocação com o nome **entrar/tokenExchange**.
  
6. O token analisado no aplicativo bot fornece as informações necessárias, como o endereço de email do usuário.
  
## <a name="develop-an-sso-teams-bot"></a>Desenvolver um bot do SSO Teams
  
Conclua as etapas a seguir para desenvolver um bot do SSO Teams:

1. [Registre seu aplicativo por meio do portal do AAD.](#register-your-app-through-the-aad-portal)
2. [Atualize seu manifesto de aplicativo do Teams para seu bot](#update-your-teams-application-manifest-for-your-bot).
3. [Adicione o código para solicitar e receber um token de bot](#add-the-code-to-request-and-receive-a-bot-token).

### <a name="register-your-app-through-the-aad-portal"></a>Registrar seu aplicativo por meio do portal do AAD

As etapas para registrar seu aplicativo por meio do portal do AAD são semelhantes ao [fluxo de SSO da guia](../../../tabs/how-to/authentication/auth-aad-sso.md). Conclua as etapas a seguir para registrar seu aplicativo:

1. Registre um novo aplicativo no [portal do Azure Active Directory – Registros de Aplicativos.](https://go.microsoft.com/fwlink/?linkid=2083908)
2. Selecione **Novo Registro**. A **página Registrar um aplicativo** é exibida.
3. Na página **Registrar um aplicativo,** insira os seguintes valores:
    1. Insira um **Nome** para seu aplicativo.
    2. Escolha os **tipos de conta com** suporte, selecione locatário único ou tipo de conta multitenant.

        > [!NOTE]
        >
        > Os usuários não são solicitados a consentir e são concedidos tokens de acesso imediatamente, se o aplicativo AAD estiver registrado no mesmo locatário em que eles estão fazendo uma solicitação de autenticação no Teams. No entanto, os usuários devem fornecer consentimento para as permissões, se o aplicativo AAD estiver registrado em um locatário diferente.

    3. Escolha **Registrar**.
4. Na página visão geral, copie e salve a **ID do aplicativo (cliente).** Você precisará mais tarde ao atualizar o manifesto do aplicativo do Teams.
5. Em **Gerenciar**, selecione **Expor uma API**. 

   > [!IMPORTANT]
    > * Se você estiver criando um bot autônomo, insira o URI de ID do Aplicativo como `api://botid-{YourBotId}` . Aqui **YourBotId** é sua ID do aplicativo AAD.
    > * Se você estiver criando um aplicativo com um bot e uma guia, insira o URI de ID do aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}` .

5. Selecione as permissões que seu aplicativo precisa para o ponto de extremidade do AAD e, opcionalmente, para o Microsoft Graph.
6. [Conceda permissões](/azure/active-directory/develop/v2-permissions-and-consent) para aplicativos desktop, web e móveis do Teams.
7. Selecione **Adicionar um escopo**.
8. No painel que é aberto, adicione um aplicativo cliente inserindo `access_as_user` como o nome do **escopo**.

    >[!NOTE]
    > O escopo "access_as_user" usado para adicionar um aplicativo cliente é para "Administradores e usuários".
    >
    > Você deve estar ciente das seguintes restrições importantes:
    >
    > * Somente as permissões de API do Microsoft Graph no nível do usuário, como email, perfil, offline_access e OpenId são suportadas. Se você precisar de acesso a outros escopos do Microsoft Graph, como `User.Read` ou , consulte a solução alternativa `Mail.Read` [recomendada](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-graph-scopes).
    > * O nome de domínio do aplicativo deve ser igual ao nome de domínio que você registrou para seu aplicativo AAD.
    > * No momento, não há suporte para vários domínios por aplicativo.
    > * Os aplicativos que usam `azurewebsites.net` o domínio não têm suporte porque é comum e pode ser um risco de segurança.

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Atualizar o portal do Azure com a conexão OAuth

Conclua as etapas a seguir para atualizar o portal do Azure com a conexão OAuth:

1. No Portal do Azure, navegue até **Registros de aplicativo.**

2. Vá para **Permissões de API**. Selecione **Adicionar uma permissão permissões** Delegadas do Microsoft Graph e adicione as seguintes permissões da API do Microsoft  >    >  Graph:
    * User.Read (habilitado por padrão)
    * email
    * offline_access
    * OpenId
    * perfil

3. No Portal do Azure, navegue até **Bot Channels Registration**.

4. Selecione **Configurações** no painel esquerdo e escolha **Adicionar Configuração** na seção Configurações de Conexão **OAuth.**

    ![Exibição SSOBotHandle2](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

5. Execute as etapas a seguir para concluir o **formulário Nova Configuração de** Conexão:

    >[!NOTE]
    > **A concessão** implícita pode ser necessária no aplicativo AAD.

    1. Insira um **Nome** na página **Nova Configuração de** Conexão. Esse é o nome que é referido dentro das configurações do código de serviço de bot na etapa *5* do [SSO](#bot-sso-at-runtime)bot no tempo de execução .
    2. No drop-down **Provedor de** Serviços, selecione **Azure Active Directory v2**.
    3. Insira as credenciais do cliente, como **id do** cliente e **segredo do cliente** para o aplicativo AAD.
    4. Para a **URL do Exchange de Tokens,** use o valor de escopo definido em Atualizar seu manifesto de aplicativo do Teams para seu [bot](#update-your-teams-application-manifest-for-your-bot). A URL do Exchange de Tokens indica ao SDK que esse aplicativo AAD está configurado para SSO.
    5. Na caixa **ID do locatário,** insira *comum*.
    6. Adicione todos os **Escopos configurados** ao especificar permissões para APIs downstream para seu aplicativo AAD. Com a ID do cliente e o segredo do cliente fornecido, o armazenamento de tokens troca o token por um token de gráfico com permissões definidas.
    7. Selecione **Salvar**.

    ![Exibição de configuração VuSSOBotConnection](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a>Atualizar seu manifesto de aplicativo do Teams para seu bot

Se o aplicativo contiver um bot autônomo, use o seguinte código para adicionar novas propriedades ao manifesto do aplicativo teams:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```
Se o aplicativo contiver um bot e uma guia, use o seguinte código para adicionar novas propriedades ao manifesto do aplicativo Teams:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

**webApplicationInfo** é o pai dos seguintes elementos:

* **id** - A ID do cliente do aplicativo. Essa é a ID do aplicativo que você obteve como parte do registro do aplicativo com o AAD.
* **resource** - O domínio e o subdomínio do seu aplicativo. Esse é o mesmo URI, incluindo o protocolo que você registrou ao criar o seu em Registrar seu aplicativo por meio `api://` `scope` do portal do [AAD.](#register-your-app-through-the-aad-portal) Você não deve incluir o `access_as_user` caminho em seu recurso. A parte de domínio deste URI deve corresponder ao domínio e aos subdomas usados nas URLs do manifesto do aplicativo teams.

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a>Adicionar o código para solicitar e receber um token de bot

#### <a name="request-a-bot-token"></a>Solicitar um token de bot

A solicitação para obter o token é uma solicitação de mensagem POST normal usando o esquema de mensagem existente. Ele está incluído nos anexos de um OAuthCard. O esquema da classe OAuthCard é definido no Esquema do [Microsoft Bot 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) e é semelhante a um cartão de visita. O Teams trata essa solicitação como uma aquisição de token silencioso se `TokenExchangeResource` a propriedade for preenchida no cartão. Para o canal do Teams, somente a propriedade, que identifica exclusivamente uma solicitação `Id` de token, é adida.

>[!NOTE]
> O Microsoft Bot Framework `OAuthPrompt` ou o é suportado para `MultiProviderAuthDialog` autenticação SSO.

Se o usuário estiver usando o aplicativo pela primeira vez e o consentimento do usuário for necessário, a caixa de diálogo a seguir aparecerá para continuar com a experiência de consentimento:

![Caixa de diálogo Consentimento](../../../assets/images/bots/bots-consent-dialogbox.png)

Quando o usuário seleciona **Continuar**, os seguintes eventos ocorrem:

* Se o bot definir um botão de logon, o fluxo de logon para bots será disparado de forma semelhante ao fluxo de logon de um botão de cartão OAuth em um fluxo de mensagens. O desenvolvedor deve decidir quais permissões exigem o consentimento do usuário. Essa abordagem é recomendada se você exigir um token com permissões além `openId` de . Por exemplo, se você quiser trocar o token por recursos de gráfico.

* Se o bot não estiver fornecendo um botão de logon no cartão OAuth, o consentimento do usuário será necessário para um conjunto mínimo de permissões. Esse token é útil para autenticação básica e para obter o endereço de email do usuário.

##### <a name="c-token-request-without-a-sign-in-button"></a>C# solicitação de token sem um botão de login

```csharp
    var attachment = new Attachment
            {
                Content = new OAuthCard
                {
                    TokenExchangeResource = new TokenExchangeResource
                    {
                        Id = requestId
                    }
                },
                ContentType = OAuthCard.ContentType,
            };
            var activity = MessageFactory.Attachment(attachment);

            // NOTE: This activity needs to be sent in the 1:1 conversation between the bot and the user. 
            // If the bot supports group and channel scope, this code should be updated to send the request to the 1:1 chat. 

       await turnContext.SendActivityAsync(activity, cancellationToken);
```

#### <a name="receive-the-bot-token"></a>Receber o token de bot

A resposta com o token é enviada por meio de uma atividade de invocação com o mesmo esquema que outras atividades de invocação que os bots recebem hoje. A única diferença é o nome da invocação, **o login/tokenExchange** e o **campo de** valor. O **campo** valor contém a **Id**, uma cadeia de caracteres da solicitação inicial para obter o token e o **campo de token,** um valor de cadeia de caracteres, incluindo o token.

>[!NOTE]
> Você pode receber várias respostas para uma determinada solicitação se o usuário tiver vários pontos de extremidade ativos. Você deve deduplicar as respostas com o token.

##### <a name="c-code-to-handle-the-invoke-activity"></a>C# código para manipular a atividade de invocação

```csharp
    protected override async Task<InvokeResponse> OnInvokeActivityAsync
    (ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
            {
                try
                {
                    if (turnContext.Activity.Name == SignInConstants.TokenExchangeOperationName && turnContext.Activity.ChannelId == Channels.Msteams)
                    {
                        await OnTokenResponseEventAsync(turnContext, cancellationToken);
                        return new InvokeResponse() { Status = 200 };
                    }
                    else
                    {
                        return await base.OnInvokeActivityAsync(turnContext, cancellationToken);
                    }
                }
                catch (InvokeResponseException e)
                {
                    return e.CreateInvokeResponse();
                }
            }
```

O `turnContext.activity.value` é do tipo [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) e contém o token que pode ser mais usado pelo bot. Você deve armazenar os tokens por motivos de desempenho e atualize-os.

### <a name="token-exchange-failure"></a>Falha na troca de tokens

Em caso de falha na troca de tokens, use o seguinte código:

```json
{ 
    "status": "<response code>", 
    "body": 
    { 
        "id":"<unique Id>", 
        "connectionName": "<connection Name on the bot (from the OAuth card)>", 
        "failureDetail": "<failure reason if status code is not 200, null otherwise>" 
    } 
}
```

Para entender o que o bot faz quando a troca de token falha ao disparar um prompt de consentimento, consulte as seguintes etapas:

>[!NOTE]
> Nenhuma ação do usuário é necessária para ser tomada à medida que o bot assume as ações quando a troca de token falha.

1. O cliente inicia uma conversa com o bot disparando um cenário OAuth.
2. O bot envia de volta um cartão OAuth para o cliente.
3. O cliente intercepta o cartão OAuth antes de exibi-lo para o usuário e verifica se ele contém uma `TokenExchangeResource` propriedade.
4. Se a propriedade existir, o cliente enviará um `TokenExchangeInvokeRequest` para o bot. O cliente deve ter um token exchangeable para o usuário, que deve ser um token do Azure AD v2 e cuja audiência deve ser igual à `TokenExchangeResource.Uri` propriedade. O cliente envia uma atividade de invocação para o bot com o seguinte código:

    ```json
    {
        "type": "Invoke",
        "name": "signin/tokenExchange",
        "value": 
        {
            "id": "<any unique Id>",
            "connectionName": "<connection Name on the skill bot (from the OAuth card)>",
            "token": "<exchangeable token>"
        }
    }
    ```

5. O bot processa `TokenExchangeInvokeRequest` o e retorna uma volta para o `TokenExchangeInvokeResponse` cliente. O cliente deve aguardar até receber o `TokenExchangeInvokeResponse` .

    ```json
    {
        "status": "<response code>",
        "body": 
        {
            "id":"<unique Id>",
            "connectionName": "<connection Name on the skill bot (from the OAuth card)>",
            "failureDetail": "<failure reason if status code is not 200, null otherwise>"
        }
    }
    ```

6. Se o `TokenExchangeInvokeResponse` tiver um de , o cliente não `status` `200` mostrará o cartão OAuth. Consulte a [imagem de fluxo normal](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true). Para qualquer outro ou se o não for recebido, o cliente mostrará o cartão `status` `TokenExchangeInvokeResponse` OAuth para o usuário. Consulte a [imagem de fluxo de fallback](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true). Isso garante que o fluxo de SSO volte ao fluxo normal do OAuthCard em caso de erros ou dependências não a ativas, como o consentimento do usuário.


### <a name="update-the-auth-sample"></a>Atualizar o exemplo de auth

Abra [o exemplo de auth do Teams](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) e conclua as seguintes etapas para atualizá-lo:

1. Atualize o TeamsBot para lidar com a dedução da solicitação de entrada incluindo o seguinte código:

    ```csharp
        protected override async Task OnSignInInvokeAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
            {
                await Dialog.RunAsync(turnContext, ConversationState.CreateProperty<DialogState>(nameof(DialogState)), cancellationToken);
            }
        protected override async Task OnTokenResponseEventAsync(ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
            {
                await Dialog.RunAsync(turnContext, ConversationState.CreateProperty<DialogState>(nameof(DialogState)), cancellationToken);
            }
    ```
  
2. Atualizar para incluir a , senha e o nome da conexão definido em `appsettings.json` Atualizar o portal do `botId` [Azure com a conexão OAuth](#update-the-azure-portal-with-the-oauth-connection).
3. Atualize o manifesto e verifique `token.botframework.com` se está na lista de domínios válidos. Para obter mais informações, consulte [Teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).
4. Feche o manifesto com as imagens de perfil e instale-o no Teams.

## <a name="code-sample"></a>Exemplo de código
|**Exemplo de nome** | **Descrição** |**.NET** | 
|----------------|-----------------|--------------|
|SDK da estrutura bot | Exemplo para usar o SDK da estrutura de bot. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore)|
