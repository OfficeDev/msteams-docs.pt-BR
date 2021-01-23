---
title: Suporte de logon único para bots
description: Descreve como obter um token de usuário. Atualmente, um desenvolvedor de bot pode usar um cartão de login ou o serviço de bot do azure com suporte para cartão OAuth.
keywords: token, token de usuário, suporte a SSO para bots
ms.topic: conceptual
ms.openlocfilehash: 55b930ba50eede6ac970fbe0f901d418605f3f91
ms.sourcegitcommit: 5662bf23fafdbcc6d06f826a647f3696cd17f5e5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49935251"
---
# <a name="single-sign-on-sso-support-for-bots"></a>Suporte a SSO (single sign-on) para bots

A autenticação de login único no Azure Active Directory (AAD) minimiza o número de vezes que os usuários precisam inserir suas credenciais de entrada ao atualizar silenciosamente o token de autenticação. Se os usuários concordarem em usar seu aplicativo, eles não precisarão dar consentimento novamente em outro dispositivo e poderão entrar automaticamente. O fluxo é semelhante ao do suporte ao SSO da guia [Do Microsoft Teams,](../../../tabs/how-to/authentication/auth-aad-sso.md)no entanto, a diferença está no protocolo de como um bot solicita [tokens](#request-a-bot-token) e recebe [respostas.](#receive-the-bot-token)

>[!NOTE]
> O OAuth 2.0 é um padrão aberto para autenticação e autorização usados pelo AAD e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams.

## <a name="bot-sso-at-runtime"></a>SSO de bot em tempo de execução

![SSO do bot no diagrama de tempo de execução](../../../assets/images/bots/bots-sso-diagram.png)

Conclua as seguintes etapas para obter tokens de aplicativo de bot e autenticação:

1. O bot envia uma mensagem com um OAuthCard que contém a `tokenExchangeResource` propriedade. Ele informa ao Teams para obter um token de autenticação para o aplicativo bot. O usuário recebe mensagens em todos os pontos de extremidade do usuário ativo.

    > [!NOTE]
    >* Um usuário pode ter mais de um ponto de extremidade ativo por vez.
    >* O token de bot é recebido de cada ponto de extremidade de usuário ativo.
    >* O aplicativo deve ser instalado no escopo pessoal para suporte a SSO.

2. Se o usuário atual estiver usando seu aplicativo bot pela primeira vez, um prompt de solicitação será exibido solicitando que o usuário faça um dos seguintes:
    * Forneça consentimento, se necessário.
    * Tratar a autenticação de etapa, como a autenticação de dois fatores.

3. O Teams solicita o token do aplicativo bot do ponto de extremidade do AAD para o usuário atual.

4. O AAD envia o token do aplicativo bot para o aplicativo do Teams.

5. O Teams envia o token para o bot como parte do objeto de valor retornado pela atividade de invocação com o nome **entrar/tokenExchange**.
  
6. O token analisado no aplicativo bot fornece as informações necessárias, como o endereço de email do usuário.
  
## <a name="develop-an-sso-teams-bot"></a>Desenvolver um bot do SSO Teams
  
Conclua as seguintes etapas para desenvolver um bot do SSO Teams:

1. [Registre seu aplicativo por meio do portal do AAD.](#register-your-app-through-the-aad-portal)
2. [Atualize o manifesto do aplicativo Teams para seu bot.](#update-your-teams-application-manifest-for-your-bot)
3. [Adicione o código para solicitar e receber um token de bot.](#add-the-code-to-request-and-receive-a-bot-token)

### <a name="register-your-app-through-the-aad-portal"></a>Registrar seu aplicativo por meio do portal do AAD

As etapas para registrar seu aplicativo por meio do portal do AAD são semelhantes ao [fluxo SSO da guia.](../../../tabs/how-to/authentication/auth-aad-sso.md) Conclua as seguintes etapas para registrar seu aplicativo:

1. Registre um novo aplicativo no [Azure Active Directory – portal de Registros de Aplicativos.](https://go.microsoft.com/fwlink/?linkid=2083908)
2. Selecione **Novo Registro.** A **página Registrar um aplicativo** é exibida.
3. Na página **Registrar um aplicativo,** insira os seguintes valores:
    1. Insira um **nome** para seu aplicativo.
    2. Escolha os **tipos de conta com suporte,** selecione o tipo de conta de locatário único ou de vários locatários.

        > [!NOTE]
        >
        > Os usuários não são solicitados a consentir e são concedidos tokens de acesso imediatamente, se o aplicativo AAD estiver registrado no mesmo locatário em que estão fazendo uma solicitação de autenticação no Teams. No entanto, os usuários devem dar consentimento para as permissões, se o aplicativo AAD estiver registrado em um locatário diferente.

    3. Escolha **Registrar**.
4. Na página de visão geral, copie e salve a **ID do aplicativo (cliente).** Você precisará dele mais tarde ao atualizar seu manifesto de aplicativo do Teams.
5. Em **Gerenciar**, selecione **Expor uma API**. 

   > [!IMPORTANT]
    > * Se você estiver criando um bot autônomo, insira o URI da ID do Aplicativo como `api://botid-{YourBotId}` . Aqui, **YourBotId** é sua ID de aplicativo do AAD.
    > * Se você estiver criando um aplicativo com um bot e uma guia, insira o URI da ID do Aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}` .

5. Selecione as permissões que seu aplicativo precisa para o ponto de extremidade do AAD e, opcionalmente, para o Microsoft Graph.
6. [Conceda permissões para aplicativos](/azure/active-directory/develop/v2-permissions-and-consent) móveis, da web e da área de trabalho do Teams.
7. Selecione **Adicionar um escopo.**
8. No painel que é aberto, adicione um aplicativo cliente inserindo `access_as_user` como o nome do **escopo.**

    >[!NOTE]
    > O escopo "access_as_user" usado para adicionar um aplicativo cliente é para "Administradores e usuários".
    >
    > Você deve estar ciente das seguintes restrições importantes:
    >
    > * Somente as permissões da API do Microsoft Graph em nível de usuário, como email, perfil, offline_access e OpenId, são suportadas. Se você precisar de acesso a outros escopos do Microsoft Graph, como `User.Read` `Mail.Read` ou, confira [a solução alternativa recomendada.](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-microsoft-graph-scopes)
    > * O nome de domínio do seu aplicativo deve ser igual ao nome de domínio que você registrou para seu aplicativo AAD.
    > * Atualmente, não há suporte para vários domínios por aplicativo.
    > * Aplicativos que usam `azurewebsites.net` o domínio não são suportados porque é comum e pode ser um risco à segurança.

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Atualizar o portal do Azure com a conexão OAuth

Conclua as seguintes etapas para atualizar o portal do Azure com a conexão OAuth:

1. No Portal do Azure, navegue até Registro **de Canais de Bot.**

2. Vá para **permissões de API.** Selecione **Adicionar uma permissão permissões**  >  **delegadas** do Microsoft Graph e, em  >  seguida, adicione as seguintes permissões da API do Microsoft Graph:
    * User.Read (habilitado por padrão)
    * email
    * offline_access
    * OpenId
    * perfil

3. Selecione **Configurações** no painel esquerdo e escolha **Adicionar** Configuração na seção Configurações de Conexão **OAuth.**

    ![Exibição SSOBotHandle2](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

4. Execute as seguintes etapas para concluir o formulário **Nova Configuração de** Conexão:

    >[!NOTE]
    > **A concessão** implícita pode ser necessária no aplicativo AAD.

    1. Insira um **nome na** página **Nova Configuração de** Conexão. Esse é o nome que é referenciado dentro das configurações do seu código de serviço de bot na etapa *5* do Bot SSO em [tempo de execução.](#bot-sso-at-runtime)
    2. Na lista **drop-down** do Provedor de Serviços, selecione **Azure Active Directory v2**.
    3. Insira as credenciais do cliente, como **id do** cliente e **segredo do cliente** para o aplicativo AAD.
    4. Para a **URL do Exchange de token,** use o valor de escopo definido em Atualizar seu manifesto de aplicativo do Teams para seu [bot.](#update-your-teams-application-manifest-for-your-bot) A URL do Exchange de token indica ao SDK que esse aplicativo AAD está configurado para SSO.
    5. Na caixa **ID de locatário,** insira *comum*.
    6. Adicione todos os **Escopos configurados** ao especificar permissões para APIs downstream para seu aplicativo AAD. Com a ID do cliente e o segredo do cliente fornecidos, o armazenamento de token troca o token por um token de gráfico com permissões definidas.
    7. Selecione **Salvar**.

    ![Exibição de configuração VuSSOBotConnection](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a>Atualizar o manifesto do aplicativo Teams para seu bot

Se o aplicativo contiver um bot autônomo, use o código a seguir para adicionar novas propriedades ao manifesto do aplicativo Teams:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```
Se o aplicativo contiver um bot e uma guia, use o código a seguir para adicionar novas propriedades ao manifesto do aplicativo Teams:

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

**webApplicationInfo** é o pai dos seguintes elementos:

* **id** - A ID do cliente do aplicativo. Essa é a ID do aplicativo que você obteve como parte do registro do aplicativo no AAD.
* **resource** - O domínio e o subdomínio do seu aplicativo. Esse é o mesmo URI, incluindo o protocolo que você registrou ao criar seu aplicativo em Registrar seu aplicativo por meio `api://` `scope` do portal do [AAD.](#register-your-app-through-the-aad-portal) Você não deve incluir `access_as_user` o caminho em seu recurso. A parte de domínio desse URI deve corresponder ao domínio e aos sub-domínios usados nas URLs do manifesto do aplicativo Teams.

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a>Adicionar o código para solicitar e receber um token de bot

#### <a name="request-a-bot-token"></a>Solicitar um token de bot

A solicitação para obter o token é uma solicitação de mensagem POST normal usando o esquema de mensagens existente. Ele está incluído nos anexos de um OAuthCard. O esquema para a classe OAuthCard é definido no [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) e é semelhante a um cartão de login. O Teams trata essa solicitação como uma aquisição de token silencioso `TokenExchangeResource` se a propriedade estiver preenchida no cartão. Para o canal do Teams, apenas a propriedade, que `Id` identifica exclusivamente uma solicitação de token, é aumenteda.

>[!NOTE]
> O Microsoft Bot Framework ou o Microsoft Bot Framework `OAuthPrompt` `MultiProviderAuthDialog` tem suporte para autenticação SSO.

Se o usuário estiver usando o aplicativo pela primeira vez e o consentimento do usuário for necessário, a caixa de diálogo a seguir parece continuar com a experiência de consentimento:

![Caixa de diálogo consentimento](../../../assets/images/bots/bots-consent-dialogbox.png)

Quando o usuário seleciona **Continuar,** ocorrem os seguintes eventos:

* Se o bot definir um botão de logon, o fluxo de logon para bots será disparado de forma semelhante ao fluxo de logon de um botão de cartão OAuth em um fluxo de mensagens. O desenvolvedor deve decidir quais permissões exigem o consentimento do usuário. Essa abordagem é recomendada se você exigir um token com permissões além `openId` . Por exemplo, se você quiser trocar o token por recursos gráficos.

* Se o bot não estiver fornecendo um botão de logon no cartão OAuth, o consentimento do usuário será necessário para um conjunto mínimo de permissões. Esse token é útil para autenticação básica e para obter o endereço de email do usuário.

##### <a name="c-token-request-without-a-sign-in-button"></a>Solicitação de token C# sem um botão de logon

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

A resposta com o token é enviada por meio de uma atividade de invocação com o mesmo esquema de outras atividades de invocação que os bots recebem hoje. A única diferença é o nome de invocação, **o sign-in/tokenExchange** e o **campo de** valor. O **campo** de valor contém a **Id**, uma cadeia de caracteres da solicitação inicial para obter o token e o campo **de token,** um valor de cadeia de caracteres incluindo o token.

>[!NOTE]
> Você pode receber várias respostas para uma determinada solicitação se o usuário tiver vários pontos de extremidade ativos. Você deve duplicar as respostas com o token.

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

É `turnContext.activity.value` do tipo [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) e contém o token que pode ser usado ainda mais pelo seu bot. Você deve armazenar os tokens por motivos de desempenho e atualize-os.

### <a name="update-the-auth-sample"></a>Atualizar o exemplo de auth

Abra [o exemplo de auth do Teams](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) e conclua as seguintes etapas para atualizá-lo:

1. Atualize o TeamsBot para manipular a dedudução da solicitação de entrada incluindo o seguinte código:

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
  
2. Atualização para incluir o , senha e o nome de conexão definido em Atualizar o `appsettings.json` `botId` portal do [Azure com a conexão OAuth](#update-the-azure-portal-with-the-oauth-connection).
3. Atualize o manifesto e verifique `token.botframework.com` se ele está na lista de domínios válidos. Para saber mais, confira [o exemplo de auth do Teams.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth)
4. Zip the manifest with the profile images and install it in Teams.

#### <a name="additional-code-samples"></a>Exemplos de código adicionais

* [Exemplo de C# usando o SDK da Estrutura de Bot.](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore)
