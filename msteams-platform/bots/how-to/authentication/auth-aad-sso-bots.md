---
title: Suporte de logon único para bots
description: Descreve como obter um token de usuário. Atualmente, um desenvolvedor de bots pode usar um cartão de sinalização ou o serviço de bot azure com o suporte ao cartão OAuth.
keywords: token, token de usuário, suporte sso para bots
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: a43c2a46561149ff97d039a3ba8fe9f4472e2073
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566074"
---
# <a name="single-sign-on-sso-support-for-bots"></a>Suporte de login único (SSO) para bots

A autenticação de logoi único em Azure Active Directory (AAD) minimiza o número de vezes que os usuários precisam inserir seu sinal em credenciais, atualizando silenciosamente o token de autenticação. Se os usuários concordarem em usar seu aplicativo, eles não precisam fornecer consentimento novamente em outro dispositivo e podem fazer login automaticamente. O fluxo é semelhante ao do [suporte Microsoft Teams guia SSO,](../../../tabs/how-to/authentication/auth-aad-sso.md)no entanto, a diferença está no protocolo de como um bot [solicita tokens](#request-a-bot-token) e [recebe respostas](#receive-the-bot-token).

>[!NOTE]
> OAuth 2.0 é um padrão aberto para autenticação e autorização usado pela AAD e muitos outros provedores de identidade. Um entendimento básico do OAuth 2.0 é um pré-requisito para trabalhar com autenticação em Teams.

## <a name="bot-sso-at-runtime"></a>Bot SSO em tempo de execução

![Bot SSO no diagrama de tempo de execução](../../../assets/images/bots/bots-sso-diagram.png)

Complete as seguintes etapas para obter a autenticação e os tokens de aplicativos de bot:

1. O bot envia uma mensagem com um OAuthCard que contém a `tokenExchangeResource` propriedade. Ele diz ao Teams para obter um token de autenticação para o aplicativo bot. O usuário recebe mensagens em todos os pontos finais ativos do usuário.

    > [!NOTE]
    >* Um usuário pode ter mais de um ponto final ativo por vez.
    >* O token bot é recebido de todos os pontos finais ativos do usuário.
    >* O aplicativo deve ser instalado em escopo pessoal para suporte ao SSO.

1. Se o usuário atual estiver usando seu aplicativo de bot pela primeira vez, um prompt de solicitação será solicitado solicitando ao usuário que faça um dos seguintes:
    * Fornecer consentimento, se necessário.
    * Manuseie a autenticação intensificada, como autenticação de dois fatores.

1. Teams solicita o token do aplicativo bot do ponto final AAD para o usuário atual.

1. AAD envia o token de aplicativo de bot para o aplicativo Teams.

1. Teams envia o token para o bot como parte do objeto de valor devolvido pela atividade de invocação com o nome **login/tokenExchange**.
  
1. O token analisado no aplicativo bot fornece as informações necessárias, como o endereço de e-mail do usuário.
  
## <a name="develop-an-sso-teams-bot"></a>Desenvolva um bot de Teams SSO
  
Complete as seguintes etapas para desenvolver um bot de Teams SSO:

1. [Cadastre seu aplicativo através do portal AAD](#register-your-app-through-the-aad-portal).
1. [Atualize seu manifesto de aplicativo Teams para o seu bot](#update-your-teams-application-manifest-for-your-bot).
1. [Adicione o código para solicitar e receba um token de bot](#add-the-code-to-request-and-receive-a-bot-token).

### <a name="register-your-app-through-the-aad-portal"></a>Cadastre seu aplicativo através do portal AAD

As etapas para registrar seu aplicativo através do portal AAD são semelhantes ao [fluxo SSO](../../../tabs/how-to/authentication/auth-aad-sso.md)da guia . Complete as seguintes etapas para registrar seu aplicativo:

1. Cadastre um novo aplicativo no [portal Azure Active Directory – App Registrations.](https://go.microsoft.com/fwlink/?linkid=2083908)
2. Selecione **Novo Registro**. A página **do registro de um aplicativo** é exibida.
3. Na página **de registro de um aplicativo,** digite os seguintes valores:
    1. Digite um **nome** para o seu aplicativo.
    2. Escolha os **tipos de conta suportada,** selecione o tipo de conta de inquilino único ou multitenente.

        > [!NOTE]
        >
        > Os usuários não são solicitados a consentimento e recebem tokens de acesso imediatamente, se o aplicativo AAD estiver registrado no mesmo inquilino onde eles estão fazendo uma solicitação de autenticação em Teams. No entanto, os usuários devem fornecer consentimento para as permissões, se o aplicativo AAD estiver registrado em um inquilino diferente.

    3. Escolha **Registrar**.
4. Na página de visão geral, copie e salve o **ID do aplicativo (cliente).** Você precisa dele mais tarde ao atualizar seu manifesto de solicitação de Teams.
5. Em **Gerenciar**, selecione **Expor uma API**. 

   > [!IMPORTANT]
    > * Se você estiver construindo um bot autônomo, digite o ID URI de aplicativo como `api://botid-{YourBotId}` . Aqui **o YourBotId** é o seu ID de aplicação AAD.
    > * Se você estiver construindo um aplicativo com um bot e uma guia, digite o ID URI do aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}` .

5. Selecione as permissões que seu aplicativo precisa para o ponto final AAD e, opcionalmente, para a Microsoft Graph.
6. [Conceder permissões](/azure/active-directory/develop/v2-permissions-and-consent) para Teams aplicativos de desktop, web e mobile.
7. Selecione **Adicionar um escopo**.
8. No painel que abre, adicione um aplicativo cliente digitando `access_as_user` como o nome **Escopo**.

    >[!NOTE]
    > O escopo "access_as_user" usado para adicionar um aplicativo ao cliente é para "Administradores e usuários".
    >
    > Você deve estar ciente das seguintes restrições importantes:
    >
    > * Apenas as permissões de API de nível de usuário da Microsoft Graph, como e-mail, perfil, offline_access e OpenId são suportadas. Se você precisar de acesso a outros escopos Graph Microsoft, como `User.Read` ou , ver solução `Mail.Read` [recomendada](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-graph-scopes).
    > * O nome de domínio do seu aplicativo deve ser o mesmo que o nome de domínio que você registrou para o aplicativo AAD.
    > * Vários domínios por aplicativo não são suportados no momento.
    > * Aplicativos que usam o `azurewebsites.net` domínio não são suportados porque é comum e pode ser um risco à segurança.

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Atualize o portal Azure com a conexão OAuth

Complete as seguintes etapas para atualizar o portal Azure com a conexão OAuth:

1. No Portal Azure, navegue até **os registros do App.**

2. Vá para **permissões de API**. Selecione **Adicionar uma permissão**  >  **que a Microsoft Graph** as  >  **permissões delegadas** e, em seguida, adicionar as seguintes permissões da API Graph Microsoft:
    * User.Read (ativado por padrão)
    * email
    * offline_access
    * OpenId
    * perfil

3. No Portal Azure, navegue até o **Registro de Canais de Bot**.

4. Selecione **Configurações** no painel esquerdo e escolha **Adicionar configuração** na seção **Configurações conexão OAuth.**

    ![Exibição SSOBotHandle2](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

5. Execute as seguintes etapas para completar o **formulário Configuração da nova conexão:**

    >[!NOTE]
    > **A concessão implícita** pode ser necessária na aplicação AAD.

    1. Digite um **nome** na página Configuração de **nova conexão.** Este é o nome que é referido dentro das configurações do seu código de serviço bot na *etapa 5* do [Bot SSO no tempo de execução](#bot-sso-at-runtime).
    2. Na entrega do Provedor de **Serviços,** selecione **Azure Active Directory v2**.
    3. Digite as credenciais do cliente, como **o cliente e** o segredo do **cliente** para o aplicativo AAD.
    4. Para o **Token Exchange URL,** use o valor do escopo definido em [Atualizar seu manifesto de aplicativo Teams para o seu bot](#update-your-teams-application-manifest-for-your-bot). A URL de token Exchange indica ao SDK que este aplicativo AAD está configurado para SSO.
    5. Na caixa **de ID do Inquilino,** digite *comum.*
    6. Adicione todos os **Escopos** configurados ao especificar permissões às APIs a jusante para o aplicativo AAD. Com a identidade do cliente e o segredo do cliente fornecidas, a loja de tokens troca o token por um token gráfico com permissões definidas.
    7. Selecione **Salvar**.

    ![Visualização de configuração vussobotconnection](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a>Atualize seu manifesto de aplicativo de Teams para o seu bot

Se o aplicativo contiver um bot autônomo, use o seguinte código para adicionar novas propriedades ao manifesto de Teams aplicativo:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```
Se o aplicativo contiver um bot e uma guia, use o seguinte código para adicionar novas propriedades ao manifesto de Teams aplicativo:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

**webApplicationInfo** é o pai dos seguintes elementos:

* **id** - O ID do cliente do aplicativo. Este é o ID de aplicação que você obteve como parte do registro do aplicativo com AAD.
* **recurso** - O domínio e o subdomínio do seu aplicativo. Este é o mesmo URI, incluindo o `api://` protocolo que você registrou ao criar o seu in `scope` [Registre seu aplicativo através do portal AAD](#register-your-app-through-the-aad-portal). Você não deve incluir o `access_as_user` caminho em seu recurso. A parte de domínio deste URI deve corresponder ao domínio e subdomínios usados nos URLs do seu manifesto de aplicação Teams.

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a>Adicione o código para solicitar e receba um token de bot

#### <a name="request-a-bot-token"></a>Solicite um token de bot

A solicitação para obter o token é uma solicitação normal de mensagem POST usando o esquema de mensagem existente. Está incluído nos anexos de um OAuthCard. O esquema para a classe OAuthCard é definido no [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) e é semelhante a um cartão de login. Teams trata esse pedido como uma aquisição silenciosa de token se a `TokenExchangeResource` propriedade estiver preenchida no cartão. Para o canal Teams, apenas a `Id` propriedade, que identifica exclusivamente um pedido de token, é honrada.

>[!NOTE]
> O Microsoft Bot Framework `OAuthPrompt` ou o suporte para `MultiProviderAuthDialog` autenticação SSO.

Se o usuário estiver usando o aplicativo pela primeira vez e o consentimento do usuário for necessário, a seguinte caixa de diálogo aparecerá para continuar com a experiência de consentimento:

![Caixa de diálogo de consentimento](../../../assets/images/bots/bots-consent-dialogbox.png)

Quando o usuário seleciona **Continuar,** ocorrem os seguintes eventos:

* Se o bot definir um botão de login, o fluxo de sinal para bots será acionado semelhante ao fluxo de sinal de um botão de cartão OAuth em um fluxo de mensagens. O desenvolvedor deve decidir quais permissões requerem o consentimento do usuário. Esta abordagem é recomendada se você precisar de um token com permissões além `openId` . Por exemplo, se você quiser trocar o token por recursos gráficos.

* Se o bot não estiver fornecendo um botão de login no cartão OAuth, o consentimento do usuário será necessário para um conjunto mínimo de permissões. Este token é útil para autenticação básica e para obter o endereço de e-mail do usuário.

##### <a name="c-token-request-without-a-sign-in-button"></a>Solicitação de token C# sem um botão de login

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

#### <a name="receive-the-bot-token"></a>Receba o token de bot

A resposta com o token é enviada através de uma atividade de invocação com o mesmo esquema que outras atividades de invocação que os bots recebem hoje. A única diferença é o nome de invocação, **o login/tokenExchange** e o campo **de valor.** O campo **de valor** contém o **ID**, uma sequência da solicitação inicial para obter o token e o campo **de token,** um valor de sequência incluindo o token.

>[!NOTE]
> Você pode receber várias respostas para uma determinada solicitação se o usuário tiver vários pontos finais ativos. Você deve deduplicar as respostas com o token.

##### <a name="c-code-to-handle-the-invoke-activity"></a>Código C# para lidar com a atividade de invocação

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

O `turnContext.activity.value` é do tipo [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) e contém o token que pode ser usado ainda mais pelo seu bot. Você deve armazenar os tokens por razões de desempenho e atualizá-los.

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

Para entender o que o bot faz quando a exchange de token não aciona um prompt de consentimento, consulte as seguintes etapas:

>[!NOTE]
> Nenhuma ação do usuário é necessária para ser tomada à medida que o bot toma as ações quando a troca de tokens falha.

1. O cliente inicia uma conversa com o bot desencadeando um cenário OAuth.
2. O bot envia um cartão OAuth para o cliente.
3. O cliente intercepta o cartão OAuth antes de exibi-lo ao usuário e verifica se ele contém uma `TokenExchangeResource` propriedade.
4. Se a propriedade existir, o cliente envia um `TokenExchangeInvokeRequest` para o bot. O cliente deve ter um token comercializável para o usuário, que deve ser um token Azure AD v2 e cujo público deve ser o mesmo que `TokenExchangeResource.Uri` propriedade. O cliente envia uma atividade de invocação para o bot com o seguinte código:

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

5. O bot processa o `TokenExchangeInvokeRequest` e retorna de volta ao `TokenExchangeInvokeResponse` cliente. O cliente deve esperar até receber o `TokenExchangeInvokeResponse` .

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

6. Se o `TokenExchangeInvokeResponse` tem um de , então o cliente não mostra o cartão `status` `200` OAuth. Veja a [imagem de fluxo normal](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true). Para qualquer outro `status` ou se o não for `TokenExchangeInvokeResponse` recebido, então o cliente mostra o cartão OAuth ao usuário. Veja a imagem de [fluxo de recuo](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true). Isso garante que o fluxo SSO volte ao fluxo normal do OAuthCard em caso de erros ou dependências não atendidas, como o consentimento do usuário.


### <a name="update-the-auth-sample"></a>Atualize a amostra de auth

Abra Teams amostra de [auth](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) e, em seguida, complete as seguintes etapas para atualizá-la:

1. Atualize o TeamsBot para lidar com a deduping da solicitação recebida, incluindo o seguinte código:

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
  
2. Atualização `appsettings.json` para incluir a senha e o nome de `botId` conexão definido no Update the [Azure portal com a conexão OAuth](#update-the-azure-portal-with-the-oauth-connection).
3. Atualize o manifesto e certifique-se de que `token.botframework.com` está na lista de domínios válidos. Para obter mais informações, consulte [Teams amostra de auth](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).
4. Feche o manifesto com as imagens do perfil e instale-o em Teams.

## <a name="code-sample"></a>Exemplo de código
|**Nome da amostra** | **Descrição** |**.NET** | 
|----------------|-----------------|--------------|
|Estrutura de bot SDK | Amostra para usar a estrutura do bot SDK. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore)|
