---
title: Suporte de logon único para bots
description: Descreve como obter um token de usuário. Atualmente, um desenvolvedor de bot pode usar um cartão de visita ou o serviço de bot do Azure com o suporte ao cartão OAuth.
keywords: token, token de usuário, suporte a SSO para bots, permissão, Microsoft Graph, AAD
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: f9934d29b9c340b7e3543420a212ae9304ba22e6
ms.sourcegitcommit: 4892d8d0fa38a472edab047754ef85b1a85be495
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2021
ms.locfileid: "61608444"
---
# <a name="single-sign-on-sso-support-for-bots"></a>Suporte a SSO (login único) para bots

A autenticação de entrada única no Azure Active Directory (AAD) atualiza silenciosamente o token de autenticação para minimizar o número de vezes que os usuários precisam inserir suas credenciais de entrada. Se os usuários concordarem em usar seu aplicativo, eles não precisam fornecer consentimento novamente em outro dispositivo à medida que estão conectados automaticamente. Guias e bots têm fluxo semelhante para suporte a SSO. Mas o [bot solicita tokens](#request-a-bot-token) [e recebe respostas](#receive-the-bot-token) com um protocolo diferente.

>[!NOTE]
> OAuth 2.0 é um padrão aberto para autenticação e autorização usada por AAD e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams.

## <a name="bot-sso-at-runtime"></a>SSO de bot em tempo de execução

A imagem a seguir ilustra o fluxo de SSO em bots:

![SSO de bot no diagrama de tempo de execução](../../../assets/images/bots/bots-sso-diagram.png)

As etapas a seguir ajudam você com tokens de aplicativo de bot e autenticação:

1. O bot envia uma mensagem para Teams com um OAuthCard que contém para obter um token de `tokenExchangeResource` autenticação para o aplicativo bot. O usuário recebe mensagens em todos os pontos de extremidade dos usuário ativos.

   > [!NOTE]
   >
   > * Um usuário pode ter mais de um ponto de extremidade ativo por vez.
   > * O token do bot é recebido a partir de cada ponto de extremidade de usuário ativo.
   > * O aplicativo deve ser instalado no escopo pessoal para suporte do SSO.


1. Se o usuário atual estiver usando seu aplicativo bot pela primeira vez, um prompt de solicitação aparecerá para o usuário para fazer uma das seguintes ações:
    * Forneça o consentimento, se necessário.
    * Lidar com a autenticação avançada, como a autenticação de dois fatores.

1. Teams solicita o token de aplicativo bot AAD ponto de extremidade do usuário atual.

1. AAD envia o token de aplicativo bot para o Teams aplicativo.

1. Teams envia o token para o bot como parte do objeto value retornado pela invocação com **logon/tokenExchange**.
  
1. O token analisado no aplicativo bot fornece as informações necessárias, tais como o endereço de email do usuário.
  
## <a name="develop-an-sso-teams-bot"></a>Desenvolver um bot de Teams SSO
  
As etapas a seguir orientam você a desenvolver o Teams SSO:

1. [Registre seu aplicativo por meio do portal AAD .](#register-your-app-through-the-aad-portal)
1. [Atualize seu Teams de aplicativo para seu bot.](#update-your-teams-application-manifest-for-your-bot)
1. [Adicione o código para solicitar e receber um token de bot](#add-the-code-to-request-and-receive-a-bot-token).

### <a name="register-your-app-through-the-aad-portal"></a>Registre seu aplicativo por meio do portal AAD site

As etapas para registrar seu aplicativo por meio do portal AAD são semelhantes ao [fluxo de SSO da guia](../../../tabs/how-to/authentication/auth-aad-sso.md). As etapas a seguir orientam você a registrar seu aplicativo:

1. Registre um novo aplicativo no [portal Azure Active Directory – Registros de Aplicativos.](https://go.microsoft.com/fwlink/?linkid=2083908)

1. Selecione **Novo Registro**. A **página Registrar um aplicativo** é exibida.

    ![Novo registro](~/assets/images/authentication/SSO-bots-auth/app-registration.png)

1. No aplicativo **Registrar um,** faça as seguintes etapas:

   > [!NOTE]
   >
   > Os usuários não são solicitados a consentir e são concedidos tokens de acesso imediatamente, se o aplicativo AAD estiver registrado no mesmo locatário em que eles estão fazendo uma solicitação de autenticação no Teams. No entanto, os usuários devem fornecer consentimento para as permissões, se o aplicativo AAD estiver registrado em um locatário diferente.

    * Insira **Nome** para seu aplicativo.
    * Selecione **Tipos de conta com suporte,** como locatário único ou multitenente.
    * Selecione **Registrar**.

    ![Registrar um aplicativo](~/assets/images/authentication/SSO-bots-auth/register-application.png)

1. Vá para a página visão geral.
1. Copie o valor da **ID do Aplicativo (cliente).**
1. Em **Gerenciar**, vá para **Expor uma API**


   > [!TIP] 
   > Para atualizar o manifesto do aplicativo mais tarde, salve o valor de **ID do** aplicativo (cliente).


   > [!IMPORTANT]
   > * Se você estiver criando um bot autônomo, insira o URI de ID do Aplicativo como `api://botid-{YourBotId}` . Aqui, **YourBotId** é sua AAD ID do aplicativo.
   > * Se você estiver criando um aplicativo com um bot e uma guia, insira o URI de ID do aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}` .

1. Selecione as permissões que seu aplicativo precisa para o ponto de extremidade AAD e, opcionalmente, para o Microsoft Graph.
1. [Conceda permissões](/azure/active-directory/develop/v2-permissions-and-consent) para Teams desktop, web e aplicativos móveis.
1. Selecione **Adicionar um escopo**.
1. No painel que solicita, digite `access_as_user` como o nome do **escopo**.

   >[!NOTE]
   > O escopo "access_as_user" usado para adicionar um aplicativo cliente é para "Administradores e usuários".
   >
   > Você deve estar ciente das seguintes restrições importantes:
   >
   > * Somente as permissões de API microsoft Graph nível do usuário, como email, perfil, offline_access e OpenId são suportadas. Se você precisar de acesso a outros escopos Graph microsoft, como ou , consulte Obter um token de acesso com Graph `User.Read` `Mail.Read` [permissões](../../../tabs/how-to/authentication/auth-aad-sso.md#get-an-access-token-with-graph-permissions).
   > * O nome de domínio do seu aplicativo deve ser igual ao nome de domínio que você registrou para seu aplicativo AAD aplicativo.
   > * No momento, não há suporte para vários domínios por aplicativo.
   > * Os aplicativos que usam `azurewebsites.net` o domínio não têm suporte porque é comum e pode ser um risco de segurança.

1. No Who **pode consentir?**, insira **Administradores e usuários**.
1. Insira os seguintes detalhes para configurar os prompts de consentimento do administrador e do usuário com valores apropriados para o `access_as_user` escopo.
    * **Nome de exibição de** consentimento do administrador : Teams pode acessar o perfil do usuário.
    * **Descrição do** consentimento do administrador : Teams pode chamar as APIs web do aplicativo como o usuário atual.
    * **Nome de exibição** de consentimento do usuário : Teams pode acessar seu perfil e fazer solicitações em seu nome.
    * **Descrição do** consentimento do usuário : Teams pode chamar as APIs desse aplicativo com os mesmos direitos que você tem.

    ![admin e users](~/assets/images/authentication/SSO-bots-auth/add-a-scope.png)

1. Verifique se o estado está definido como **Habilitado**.

    ![Estado](~/assets/images/authentication/SSO-bots-auth/enabled-state.png)

1. Selecione **Adicionar escopo** para salvar os detalhes. A parte de domínio do **nome do** Escopo exibido deve corresponder automaticamente ao conjunto de URI **de ID** do Aplicativo na etapa anterior, com anexado `/access_as_user` ao final `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user` .

1. Nos **aplicativos cliente autorizados,** identifique os aplicativos que você deseja autorizar para o aplicativo Web do seu aplicativo.
1. Selecione **Adicionar um aplicativo cliente**.

    ![aplicativo cliente](~/assets/images/authentication/SSO-bots-auth/add-client-application.png)

1. Insira cada uma das seguintes IDs de cliente e selecione o escopo autorizado criado na etapa anterior:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264`para Teams aplicativo móvel ou desktop.
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346`para Teams web.

    ![id do cliente](~/assets/images/authentication/SSO-bots-auth/add-client-id.png)

1. Vá para **Autenticação**.
1. Em **Configurações de plataforma,** selecione **Adicionar uma plataforma**.

    ![plataforma](~/assets/images/authentication/SSO-bots-auth/platform-configuration.png)

1. Selecione **Web**.

    ![Configurar plataforma](~/assets/images/authentication/SSO-bots-auth/configure-platform.png)

1. Insira os **URIs de redirecionamento** para seu aplicativo.

   >[!NOTE]
   > Esse URI deve ser um nome de domínio totalmente qualificado. Ele também é seguido pela rota da API para a qual uma resposta de autenticação é enviada. Se você estiver seguindo qualquer uma das amostras Teams, o URI será `https://token.botframework.com/.auth/web/redirect` . Para obter mais informações, consulte [OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

    ![Redirecionar uris](~/assets/images/authentication/SSO-bots-auth/configure-web.png)

1. Adicionar permissões **de API necessárias.**
    * Selecione **permissões de API** no plano esquerdo.
    * Selecione **Adicionar uma plataforma para** adicionar quaisquer permissões delegadas pelo usuário que seu aplicativo exija para APIs de downstream, por exemplo, User.Read.

1. As etapas a seguir ajudarão você a habilitar a concessão implícita:
    * Selecione **Autenticação** no painel esquerdo.
    * Selecione as **caixas de seleção Tokens de** Acesso e tokens de **ID.**
    
    ![Conceder fluxo](~/assets/images/authentication/SSO-bots-auth/grant-flow.png)
    
    * Selecione **Salvar** para salvar as alterações.

#### <a name="update-manifest-in-azure-portal"></a>Manifesto de atualização no portal do Azure

As etapas a seguir orientarão você a atualizar o manifesto do bot no portal do Azure:

1. Selecione **Manifesto** no painel esquerdo.
1. Verifique se o item config está definido como **"accessTokenAcceptedVersion": 2**. Caso não seja, altere seu valor para **2**.

    ![Manifesto de atualização](~/assets/images/bots/update-manifest.png)


   >[!NOTE]
   > Se você já estiver testando seu bot Teams, saia deste aplicativo e saia do Teams. Em seguida, entre novamente para ver essa alteração.

1. Selecione **Salvar**.

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Atualizar o portal do Azure com a conexão OAuth

As etapas a seguir orientarão você a atualizar o portal do Azure com a conexão OAuth:

1. No portal do Azure, acesse [ **AzureBot**](https://ms.portal.azure.com/#create/Microsoft.AzureBot)
1. Vá para **Configuração** no painel esquerdo.
1. Selecione **Adicionar conexão OAuth Configurações**.

    ![Definição de configuração](~/assets/images/authentication/SSO-bots-auth/auth-setting2.png)

1. As etapas a seguir orientarão você a concluir o formulário **Nova Configuração de** Conexão:

   >[!NOTE]
   > **A concessão** implícita pode ser necessária no AAD aplicativo.

    * Insira **Nome** na página **Nova Configuração de** Conexão.

    >[!NOTE]
    > O **Nome** é referenciado às configurações do código de serviço de bot na *etapa 5* do [SSO bot no tempo de execução](#bot-sso-at-runtime).

    * No drop-down **Provedor de** Serviços, selecione **Azure Active Directory v2**.
    * Insira as credenciais do cliente, como **id do cliente** e **segredo** do cliente para o AAD aplicativo.
    * Para a **URL token Exchange**, use o valor de escopo definido em Atualizar seu manifesto do aplicativo Teams para seu [bot](#update-your-teams-application-manifest-for-your-bot). A URL Exchange Token indica ao SDK que esse aplicativo AAD está configurado para SSO.
    * Na **ID do Locatário,** insira *comum*.
    * Adicione todos os **Escopos configurados** ao especificar permissões para APIs de downstream para seu AAD aplicativo. Com a ID do Cliente e o segredo do cliente fornecido, o armazenamento de tokens troca o token por um token de gráfico com permissões definidas.
    * Selecione **Salvar**.
    * Selecione **Aplicar**.
   
    ![Configuração de conexão](~/assets/images/authentication/Bot-connection-setting.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a>Atualizar o manifesto Teams aplicativo do seu bot

Se o aplicativo contiver um bot autônomo, use o seguinte código para adicionar novas propriedades ao manifesto Teams aplicativo:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```
Se o aplicativo contiver um bot e uma guia, use o seguinte código para adicionar novas propriedades ao manifesto Teams aplicativo:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

**webApplicationInfo** é o pai dos seguintes elementos:

* **id** - A ID do cliente do aplicativo. É a ID do aplicativo que você obteve como parte do registro do aplicativo com AAD. Não compartilhe essa ID de aplicativo com vários Teams aplicativos. Crie um novo aplicativo AAD para cada manifesto de aplicativo que usa `webApplicationInfo` .
* **resource** - O domínio e o subdomínio do seu aplicativo. É o mesmo URI, incluindo o protocolo que você registrou ao criar seu em Registrar seu aplicativo por meio do `api://` `scope` portal AAD [.](#register-your-app-through-the-aad-portal) Não inclua o `access_as_user` caminho em seu recurso. A parte de domínio deste URI deve corresponder ao domínio e aos subdomas usados nas URLs do seu manifesto Teams aplicativo.

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a>Adicionar o código para solicitar e receber um token de bot

#### <a name="request-a-bot-token"></a>Solicitar um token de bot

A solicitação para obter o token é uma solicitação de mensagem POST normal usando o esquema de mensagem existente. Ele está incluído nos anexos de um OAuthCard. O esquema da classe OAuthCard é definido no Esquema do [Microsoft Bot 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) e é semelhante a um cartão de visita. Teams trata essa solicitação como uma aquisição de token silencioso se a `TokenExchangeResource` propriedade for preenchida no cartão. Para o canal Teams, somente a propriedade, que identifica exclusivamente uma solicitação `Id` de token, é adida.

>[!NOTE]
> O Microsoft Bot Framework `OAuthPrompt` ou o é suportado para `MultiProviderAuthDialog` autenticação SSO.

Se o usuário estiver usando o aplicativo pela primeira vez e o consentimento do usuário for necessário, a caixa de diálogo a seguir aparecerá para continuar com a experiência de consentimento:

![Caixa de diálogo Consentimento](~/assets/images/authentication/SSO-bots-auth/bot-consent-box.png)

Quando o usuário seleciona **Continuar**, ocorrem os seguintes eventos:

* Se o bot definir um botão de logon, o fluxo de logon para bots será ativado semelhante ao fluxo de logon de um botão de cartão OAuth em um fluxo de mensagens. O desenvolvedor deve decidir quais permissões exigirão o consentimento do usuário. Essa abordagem é recomendada se você exigir um token com permissões além `openId` de . Por exemplo, se você quiser trocar o token por recursos de gráfico.

* Se o bot não estiver fornecendo um botão de entrada no cartão OAuth, será necessário o consentimento do usuário para um conjunto mínimo de permissões. Esse token é útil para autenticação básica e para obter o endereço de email do usuário.

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

6. Se o `TokenExchangeInvokeResponse` tiver um de , o cliente não `status` `200` mostrará o cartão OAuth. Consulte a [imagem de fluxo normal](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true). Para qualquer outro ou se o não for recebido, o cliente mostra o `status` `TokenExchangeInvokeResponse` cartão OAuth para o usuário. Consulte a [imagem de fluxo de fallback](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true). Se houver algum erro ou dependências não amet como consentimento do usuário, essa atividade garante que o fluxo de SSO volte ao fluxo OAuthCard normal.


### <a name="update-the-auth-sample"></a>Atualizar o exemplo de auth

Abra [Teams exemplo de auth](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) e conclua as seguintes etapas para atualizá-lo:

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
3. Atualize o manifesto e verifique `token.botframework.com` se está na lista de domínios válidos. Para obter mais informações, [consulte Teams exemplo de auth](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).
4. Feche o manifesto com as imagens de perfil e instale-o Teams.

## <a name="code-sample"></a>Exemplo de código
|**Nome do exemplo** | **Descrição** |**.NET** | 
|----------------|-----------------|--------------|
|SDK da estrutura bot | Exemplo para usar o SDK da estrutura de bot. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/46.teams-auth)|

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo](../../../sbs-bots-with-sso.yml)a passo , que ajuda você a criar um bot com a autenticação SSO habilitada.
