---
title: Suporte de logon único para bots
description: Saiba como obter um token de usuário e um desenvolvedor de bot pode usar um cartão de entrada ou o serviço de bot do Azure com o suporte a cartão OAuth.
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: 37c7fcd62c6b85c2220e9db57060da03437d79da
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144142"
---
# <a name="single-sign-on-sso-support-for-bots"></a>Suporte de logon único (SSO) para bots

A autenticação de logon único no Microsoft Azure Active Directory (Azure AD) atualiza silenciosamente o token de autenticação para minimizar o número de vezes que os usuários precisam inserir suas credenciais de entrada. Se os usuários concordarem em usar seu aplicativo, eles não precisarão fornecer consentimento novamente em outro dispositivo, pois eles são conectados automaticamente. Guias e bots têm um fluxo semelhante para suporte a SSO. Mas o bot [solicita tokens](#request-a-bot-token) e [recebe respostas](#receive-the-bot-token) com um protocolo diferente.

>[!NOTE]
> O OAuth 2.0 é um padrão aberto para autenticação e autorização usada pelo Azure AD e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams.

## <a name="bot-sso-at-runtime"></a>SSO do Bot em runtime

A imagem a seguir ilustra o fluxo de SSO em bots:

![Diagrama de SSO do bot em runtime](../../../assets/images/bots/bots-sso-diagram.png)

As etapas a seguir ajudam você com autenticação e tokens de aplicativo de bot:

1. O bot envia uma mensagem ao Teams com um OAuthCard que contém `tokenExchangeResource` para obter um token de autenticação para o aplicativo bot. O usuário recebe mensagens em todos os pontos de extremidade dos usuário ativos.

   > [!NOTE]
   >
   > * Um usuário pode ter mais de um ponto de extremidade ativo por vez.
   > * O token do bot é recebido a partir de cada ponto de extremidade de usuário ativo.
   > * O aplicativo deve ser instalado no escopo pessoal para suporte do SSO.

1. Se o usuário atual estiver usando seu aplicativo de bot pela primeira vez, um prompt de solicitação será exibido ao usuário para executar uma das seguintes ações:
    * Forneça o consentimento, se necessário.
    * Lidar com a autenticação avançada, como a autenticação de dois fatores.

1. O Teams solicita o token do aplicativo bot do ponto de extremidade do Azure AD para o usuário atual.

1. O Azure AD envia o token do aplicativo bot para o aplicativo Teams.

1. O Teams envia o token para o bot como parte do objeto de valor retornado pela invocação com **entrada/tokenExchange**.
  
1. O token analisado no aplicativo bot fornece as informações necessárias, tais como o endereço de email do usuário.
  
## <a name="develop-an-sso-teams-bot"></a>Desenvolver um bot do Teams de SSO
  
As etapas a seguir orientam você a desenvolver um bot do Teams de SSO:

1. [Registrar seu aplicativo por meio do portal do Azure AD](#register-your-app-through-the-azure-ad-portal).
1. [Atualizar o manifesto do aplicativo Teams para seu bot](#update-your-teams-application-manifest-for-your-bot).
1. [Adicionar o código para solicitar e receber um token de bot](#add-the-code-to-request-and-receive-a-bot-token).

### <a name="register-your-app-through-the-azure-ad-portal"></a>Registrar seu aplicativo por meio do portal do Azure AD

As etapas para registrar seu aplicativo por meio do portal do Azure AD são semelhantes ao [guia fluxo SSO](../../../tabs/how-to/authentication/tab-sso-overview.md). As etapas a seguir orientam você a registrar seu aplicativo:

1. Registrar um novo aplicativo no portal [Azure Active Directory – Registros de Aplicativo](https://go.microsoft.com/fwlink/?linkid=2083908).

1. Selecione **Novo registro**. A página **Registrar um aplicativo** é exibida.

    ![Novo registro](~/assets/images/authentication/SSO-bots-auth/app-registration.png)

1. Em **Registrar um aplicativo**, execute as seguintes etapas:

   > [!NOTE]
   >
   > Os usuários não recebem consentimento e recebem tokens de acesso imediatamente, se o aplicativo do Azure AD estiver registrado no mesmo locatário em que estão fazendo uma solicitação de autenticação no Teams. No entanto, os usuários devem fornecer consentimento para as permissões, se o aplicativo do Azure AD estiver registrado em um locatário diferente.

    * Insira um **Nome** para seu aplicativo.
    * Selecione **Tipos de conta compatíveis**, como locatário único ou multilocatário.
    * Selecione **Registrar**.

    ![Registrar um aplicativo](~/assets/images/authentication/SSO-bots-auth/register-application.png)

1. Vá para a página de visão geral.
1. Copie o valor de **ID do Aplicativo (cliente)**.
1. Em **Gerenciar**, vá para **Expor uma API**

   > [!TIP]
   > Para atualizar o manifesto do aplicativo mais tarde, salve o valor de **ID do Aplicativo (cliente)**.

   > [!IMPORTANT]
   >
   > * Se você estiver criando um bot autônomo, insira o URI da ID do Aplicativo como `api://botid-{YourBotId}`. Aqui *YourBotId* é sua ID de aplicativo do Azure AD.
   > * Se você estiver criando um aplicativo com um bot e uma guia, insira o URI de ID do aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}`.

1. Selecione **Adicionar um escopo**.
1. No painel que solicita, insira `access_as_user` como o **Nome de escopo**.

   >[!NOTE]
   > O escopo "access_as_user" usado para adicionar um aplicativo cliente é para "Administradores e usuários".
   >
   > Você deve estar ciente das seguintes restrições importantes:
   >
   > * Há suporte apenas para Microsoft Graph de API de nível de usuário, como email, perfil, offline_access e OpenId. Se você precisar de acesso a outros escopos do Microsoft Graph, `User.Read` `Mail.Read`como ou, consulte Estender aplicativo de guia com permissões e escopo do [Microsoft Graph microsoft](../../../tabs/how-to/authentication/tab-sso-graph-api.md).
   > * O nome de domínio do aplicativo deve ser igual ao nome de domínio que você registrou para seu aplicativo do Azure AD.
   > * Não há suporte para vários domínios por aplicativo no momento.
   > * Não há suporte para aplicativos que usam o domínio `azurewebsites.net` porque é comum e pode ser um risco à segurança.

1. Em **Quem pode consentir?**, insira **Administradores e usuários**.
1. Insira os detalhes a seguir para configurar os prompts de consentimento do administrador e do usuário com valores apropriados para o `access_as_user`escopo.
    * **Nome de exibição de consentimento do administrador**: O Teams pode acessar o perfil do usuário.
    * **Descrição de consentimento do administrador**: o Teams pode chamar as APIs da web do aplicativo como o usuário atual.
    * **Nome de exibição de consentimento do usuário**: O Teams pode acessar seu perfil e fazer solicitações em seu nome.
    * **Descrição de consentimento do usuário**: O Teams pode chamar as APIs deste aplicativo com os mesmos direitos que você tem.

    ![administrador e usuários](~/assets/images/authentication/SSO-bots-auth/add-a-scope.png)

1. Verifique se o estado está definido como **Habilitado**.

    ![Estado](~/assets/images/authentication/SSO-bots-auth/enabled-state.png)

1. Selecione **Adicionar escopo** para salvar os detalhes. A parte de domínio do **Nome do escopo** exibido deve corresponder automaticamente ao URI **ID de Aplicativo** definido na etapa anterior, com `/access_as_user` acrescentado ao final `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user`.

1. Em **aplicativos cliente autorizados**, identifique os aplicativos que você deseja autorizar para o aplicativo Web do aplicativo.
1. Selecione **Adicionar um aplicativo cliente**.

    ![aplicativo cliente](~/assets/images/authentication/SSO-bots-auth/add-client-application.png)

1. Insira cada uma das seguintes IDs de cliente e selecione o escopo autorizado criado na etapa anterior:
    * Aplicativo da área de trabalho ou móvel `1fec8e78-bce4-4aaf-ab1b-5451cc387264` para Teams.
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` para aplicativo web do Teams.

    ![ID do cliente](~/assets/images/authentication/SSO-bots-auth/add-client-id.png)

1. Vá para **Autenticação**.
1. Em **Configurações da plataforma**, selecione **Adicionar uma plataforma**.

    ![plataforma](~/assets/images/authentication/SSO-bots-auth/platform-configuration.png)

1. Selecione **Web**.

    ![Configurar plataforma](~/assets/images/authentication/SSO-bots-auth/configure-platform.png)

1. Insira **URIs de redirecionamento** para seu aplicativo.

   >[!NOTE]
   > Esse URI deve ser um nome de domínio totalmente qualificado. Ele também é seguido pela rota da API para a qual uma resposta de autenticação é enviada. Se você estiver seguindo qualquer uma das amostras do Teams, o URI será `https://token.botframework.com/.auth/web/redirect`. Para obter mais informações, confira [Fluxo de código de autorização OAuth 2.0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

    ![URIs de redirecionamento](~/assets/images/authentication/SSO-bots-auth/configure-web.png)

1. As etapas a seguir ajudarão você a habilitar a concessão implícita:
    * Selecione **Autenticação** no painel esquerdo.
    * Marque as caixas de seleção **Tokens de acesso** e **Tokens de ID**.

    ![Fluxo de concessão](~/assets/images/authentication/SSO-bots-auth/grant-flow.png)

    * Selecione **Salvar** para salvar as alterações.

1. Adicione as **Permissões de API** necessárias.
    * Selecione **Permissões de API** no painel esquerdo.
    * Selecione **Adicionar uma plataforma** para adicionar as permissões que seu aplicativo requer para APIs downstream, por exemplo, User.Read.

#### <a name="update-manifest-in-microsoft-azure-portal"></a>Atualizar manifesto no portal do Microsoft Azure

As etapas a seguir orientarão você a atualizar o manifesto do bot portal do Azure:

1. Selecione **Manifesto** no painel esquerdo.
1. Verifique se o item de configuração está definido como **"accessTokenAcceptedVersion": 2**. Caso contrário, altere seu valor para **2**.

    ![Atualizar manifesto](~/assets/images/bots/update-manifest.png)

   >[!NOTE]
   > Se você já estiver testando seu bot no Teams, deverá sair deste aplicativo e sair do Teams. Em seguida, entre novamente para ver essa alteração.

1. Selecione **Salvar**.

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Atualizar o portal do Azure com a conexão OAuth

As etapas a seguir orientarão você a atualizar o portal do Azure com a conexão OAuth:

1. No portal do Azure, vá para [**AzureBot**](https://ms.portal.azure.com/#create/Microsoft.AzureBot)
1. Vá para **Configuração** no painel esquerdo.
1. Selecione **Adicionar Configurações de Conexão OAuth**.

    ![Definição de configuração](~/assets/images/authentication/SSO-bots-auth/auth-setting2.png)

1. As etapas a seguir orientarão você a concluir o formulário **Nova Configuração de Conexão**:

   >[!NOTE]
   > A **concessão implícita** pode ser necessária no aplicativo do Azure AD.

    * Insira **Nome** na página **Nova Configuração de Conexão**.

    >[!NOTE]
    > O **Nome** é referenciado às configurações do código do serviço de bot na *etapa 5* de [Bot SSO em runtime](#bot-sso-at-runtime).

    * Na lista suspensa **Provedor de Serviços**, selecione **Azure Active Directory v2**.
    * Insira as credenciais do cliente, como **ID do cliente** e **Segredo do cliente** para o aplicativo do Azure AD.
    * Para **URL de Troca de Tokens**, use o valor de escopo definido em [Atualizar o manifesto do aplicativo Teams para o bot](#update-your-teams-application-manifest-for-your-bot), por exemplo, `api://botid-<your-app-id>/`. A URL do Token Exchange indica ao SDK que esse aplicativo do Azure AD está configurado para SSO.
    * Na **ID locatário**, insira *comum*.
    * Adicione todos os **Escopos** configurados ao especificar permissões para APIs downstream para seu aplicativo do Azure AD. Com a ID do Cliente e o segredo do cliente fornecidos, o repositório de tokens troca o token por um token de grafo com permissões definidas.
    * Selecione **Salvar**.
    * Selecione **Aplicar**.

    ![Configuração de conexão](~/assets/images/authentication/Bot-connection-setting.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a>Atualizar o manifesto do aplicativo Teams para o bot

Se o aplicativo contiver um bot autônomo, use o seguinte código para adicionar novas propriedades ao manifesto do aplicativo Teams:

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

* **id** - A ID do cliente do aplicativo. É a ID do aplicativo que você obteve como parte do registro do aplicativo no Azure AD. Não compartilhe essa ID do Aplicativo com vários aplicativos do Teams. Crie um novo aplicativo do Azure AD para cada manifesto do aplicativo que usa `webApplicationInfo`.
* **resource** - O domínio e o subdomínio do seu aplicativo. É o mesmo URI, incluindo o protocolo `api://` que você registrou ao criar seu `scope` em [Registrar seu aplicativo por meio do portal do Azure AD](#register-your-app-through-the-azure-ad-portal). Não inclua o caminho `access_as_user` em seu recurso. A parte de domínio desse URI deve corresponder ao domínio e aos subdomínios usados nas URLs do manifesto do aplicativo Teams.

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a>Adicionar o código para solicitar e receber um token de bot

#### <a name="request-a-bot-token"></a>Solicitar um token de bot

A solicitação para obter o token é uma solicitação de mensagem POST normal usando o esquema de mensagem existente. Ele está incluído nos anexos de um OAuthCard. O esquema para a classe OAuthCard é definido em [Esquema do Microsoft Bot 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) e é semelhante a um cartão de entrada. O Teams tratará essa solicitação como uma aquisição de token silenciosa se a propriedade `TokenExchangeResource` for preenchida no cartão. Para o canal do Teams, somente a propriedade `Id`, que identifica exclusivamente uma solicitação de token, é respeitada.

>[!NOTE]
> O Microsoft Bot Framework `OAuthPrompt` ou o `MultiProviderAuthDialog` tem suporte para autenticação de SSO.

Se o usuário estiver usando o aplicativo pela primeira vez e o consentimento do usuário for necessário, a seguinte caixa de diálogo será exibida para continuar com a experiência de consentimento:

![Caixa de diálogo consentimento](~/assets/images/authentication/SSO-bots-auth/bot-consent-box.png)

Quando o usuário seleciona **Continuar**, ocorrem os seguintes eventos:

* Se o bot definir um botão de entrada, o fluxo de entrada para bots será ativado semelhante ao fluxo de entrada de um botão de cartão OAuth em um fluxo de mensagens. O desenvolvedor deve decidir quais permissões exigirão o consentimento do usuário. Essa abordagem é recomendada se você precisar de um token com permissões além de `openId`. Por exemplo, se você quiser trocar o token por recursos de grafo.

* Se o bot não estiver fornecendo um botão de entrada no cartão OAuth, o consentimento do usuário será necessário para um conjunto mínimo de permissões. Esse token é útil para autenticação básica e para obter o endereço de email do usuário.

##### <a name="c-token-request-without-a-sign-in-button"></a>Solicitação de token C# sem um botão de entrada

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

A resposta com o token é enviada por meio de uma atividade de invocação com o mesmo esquema que outras atividades de invocação que os bots recebem hoje. A única diferença é o nome de invocação, **entrada/tokenExchange** e o campo **value**. O campo **valor** contém a **ID**, uma cadeia de caracteres da solicitação inicial para obter o token e o campo **token**, um valor de cadeia de caracteres incluindo o token.

>[!NOTE]
> Você poderá receber várias respostas para uma determinada solicitação se o usuário tiver vários pontos de extremidade ativos. Você deve duplicar as respostas com o token.

##### <a name="c-code-to-handle-the-invoke-activity"></a>Código C# para manipular a atividade de invocação

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

O `turnContext.activity.value` é do tipo [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) e contém o token que pode ser usado ainda mais pelo bot. Você deve armazenar os tokens por motivos de desempenho e atualizá-los.

### <a name="token-exchange-failure"></a>Falha na troca de tokens

Se houver uma falha de troca de token, use o seguinte código:

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

Para entender o que o bot faz quando a troca de token falha ao disparar uma solicitação de consentimento, consulte as seguintes etapas:

>[!NOTE]
> Nenhuma ação do usuário é necessária para ser executada, pois o bot executa as ações quando a troca de token falha.

1. O cliente inicia uma conversa com o bot disparando um cenário OAuth.
2. O bot envia de volta um cartão OAuth para o cliente.
3. O cliente intercepta o cartão OAuth antes de exibi-lo para o usuário e verifica se ele contém uma propriedade `TokenExchangeResource`.
4. Se a propriedade existir, o cliente enviará um `TokenExchangeInvokeRequest` ao bot. O cliente deve ter um token que pode ser trocado para o usuário, que deve ser um token do Azure AD v2 e cuja audiência deve ser igual à propriedade `TokenExchangeResource.Uri`. O cliente envia uma atividade de invocação para o bot com o seguinte código:

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

5. O bot processa o `TokenExchangeInvokeRequest` e retorna um `TokenExchangeInvokeResponse` de volta para o cliente. O cliente deve aguardar até receber o `TokenExchangeInvokeResponse`.

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

6. Se o `TokenExchangeInvokeResponse` tiver um `status` de `200`, o cliente não mostrará o cartão OAuth. Consulte a [imagem de fluxo normal](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true). Para qualquer outro `status` ou se o `TokenExchangeInvokeResponse` não for recebido, o cliente mostrará o cartão OAuth para o usuário. Consulte a [imagem de fluxo fallback](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true). Se houver erros ou dependências não atendidas listadas, como o consentimento do usuário, essa atividade garantirá que o fluxo de SSO volte ao fluxo normal do OAuthCard.

### <a name="update-the-auth-sample"></a>Atualizar o exemplo de autenticação

Abra [exemplo de autenticação do Teams](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) e conclua as seguintes etapas para atualizá-lo:

1. Atualize o TeamsBot para lidar com a eliminação da solicitação de entrada incluindo o seguinte código:

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
  
2. Atualize `appsettings.json` para incluir o `botId`, a senha e o nome da conexão definidos em [Update o portal do Azure com a conexão OAuth](#update-the-azure-portal-with-the-oauth-connection).
3. Atualize o manifesto e verifique se `token.botframework.com` está na lista de domínios válidos. Para obter mais informações, [ Amostra de autenticação de ](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).
4. Compacte o manifesto com as imagens de perfil e instale-o no Teams.

## <a name="code-sample"></a>Exemplo de código

|**Nome de exemplo** | **Descrição** |**.NET** |**C#** |**Node.js** |
|----------------|-----------------|--------------|--------------|--------------|
|SDK do Bot framework | Este código de exemplo demonstra como começar a usar a autenticação em um bot para Microsoft Teams. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/46.teams-auth)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-conversation-sso-quickstart/csharp_dotnetcore/BotConversationSsoQuickstart)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-conversation-sso-quickstart/js)|

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo](../../../sbs-bots-with-sso.yml) para criar um bot com autenticação de SSO.
