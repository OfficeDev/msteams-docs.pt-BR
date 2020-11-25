---
title: Suporte de logon único para bots
description: Descreve como obter um token de usuário. Atualmente, um desenvolvedor de bot pode usar um cartão de entrada ou o serviço do Azure bot com o suporte a cartão OAuth.
keywords: token, token de usuário, suporte SSO para bots
ms.openlocfilehash: f2f04cefdea874c42961404339f54b8eb581c7ee
ms.sourcegitcommit: aca9990e1f84b07b9e77c08bfeca4440eb4e64f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "49409096"
---
# <a name="single-sign-on-sso-support-for-bots"></a>Suporte de logon único (SSO) para bots

A autenticação de logon único no Azure Active Directory (Azure AD) minimiza o número de vezes que os usuários precisam inserir suas credenciais de logon, atualizando silenciosamente o token de autenticação. Se os usuários concordarem em usar seu aplicativo, eles não precisarão ser consentidos novamente em outro dispositivo e serão conectados automaticamente. O fluxo é muito semelhante ao [suporte de SSO da guia do teams]( ../../../tabs/how-to/authentication/auth-aad-sso.md). A diferença é o protocolo de como um bot solicita tokens e recebe respostas.

O OAuth 2,0 é um padrão aberto para autenticação e autorização usados pelo Azure Active Directory (Azure AD) e muitos outros provedores de identidade. Uma compreensão básica do OAuth 2,0 é um pré-requisito para trabalhar com autenticação no Microsoft Teams.

## <a name="bot-sso-at-runtime"></a>SSO do bot no tempo de execução

![SSO do bot no diagrama de tempo de execução](../../../assets/images/bots/bots-sso-diagram.png)

1. O bot envia uma mensagem com um OAuthCard que contém a `tokenExchangeResource` propriedade. Ele diz às Teams para obter um token de autenticação para o aplicativo bot. O usuário recebe mensagens em todos os pontos de extremidade ativos do usuário.

> [!NOTE]
>* Um usuário pode ter mais de um ponto de extremidade ativo por vez.  
>* O token de bot é recebido de todos os pontos de extremidade ativos do usuário.
>* No momento, o suporte a logon único exige que o aplicativo seja instalado no escopo pessoal.

2. Se esta for a primeira vez que o usuário atual usou seu aplicativo bot, haverá um prompt de solicitação para o consentimento (se o consentimento for necessário) ou para lidar com a autenticação de depuração (como a autenticação de dois fatores).

3. O Microsoft Teams solicita o token do aplicativo bot do ponto de extremidade do Azure AD para o usuário atual.

4. O Azure AD envia o token do aplicativo bot para o aplicativo Teams.

5. O Microsoft Teams envia o token para o bot como parte do objeto de valor retornado pela atividade Invoke com o nome de entrada/tokenExchange.
  
6. O token será analisado no aplicativo bot para extrair as informações necessárias, como o endereço de email do usuário.
  
## <a name="develop-a-single-sign-on-microsoft-teams-bot"></a>Desenvolver um bot de logon único do Microsoft Teams
  
As etapas a seguir são necessárias para desenvolver um bot do Microsoft Teams SSO:

1. [Criar uma conta gratuita do Azure](#create-an-azure-account)
2. [Atualizar o manifesto do aplicativo do Microsoft Teams](#update-your-app-manifest)
3. [Adicionar o código para solicitar e receber o token de bot](#request-a-bot-token)

### <a name="create-an-azure-account"></a>Crie uma conta do Azure

Esta etapa é semelhante ao [fluxo de SSO de guia](../../../tabs/how-to/authentication/auth-aad-sso.md):

1. Obter sua [ID de aplicativo do Azure ad](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in) para o Teams desktop, o Web ou o cliente móvel.
2. Especifique as permissões de que seu aplicativo precisa para o ponto de extremidade do Azure AD e, opcionalmente, o Microsoft Graph.
3. [Conceder permissões](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) para aplicativos de desktop, Web e móveis do teams.
4. Adicione um aplicativo cliente selecionando o botão **Adicionar um escopo** e no painel que é aberto, Enter `access_as_user` como o **nome do escopo**.

>[!NOTE]
> O escopo "access_as_user" usado para adicionar um aplicativo cliente é para "administradores e usuários".

> [!IMPORTANT]
> * Se você estiver criando um bot autônomo, defina o URI da ID do aplicativo como `api://botid-{YourBotId}` aqui, **YourBotId** refere-se à sua ID de aplicativo do Azure AD.
> * Se você estiver criando um aplicativo com um bot e uma guia, defina o URI da ID do aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}` .

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

Adicione novas propriedades ao manifesto do Microsoft Teams:

**WebApplicationInfo** -o pai dos seguintes elementos:

> [!div class="checklist"]
>
> * **ID** – a ID do cliente do aplicativo. Esta é a ID do aplicativo que você obteve como parte do registro do aplicativo com o Azure AD.
>* **Resource** -o domínio e o subdomínio do aplicativo. Este é o mesmo URI (incluindo o `api://` protocolo) que você registrou ao criar seu `scope` na etapa 6 acima. Você não deve incluir o `access_as_user` caminho em seu recurso. A parte de domínio desse URI deve corresponder ao domínio, incluindo todos os subdomínios, usados nas URLs do manifesto de aplicativo do Microsoft Teams.

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

### <a name="request-a-bot-token"></a>Solicitar um token de bot

A solicitação para obter o token é uma solicitação de mensagem POST normal (usando o esquema de mensagens existente). Ele está incluído nos anexos de um OAuthCard. O esquema da classe OAuthCard é definido no [esquema do Microsoft Bot 4,0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) e é muito semelhante a um cartão de conexão. O Microsoft Teams tratará essa solicitação como uma aquisição de token silencioso se a `TokenExchangeResource` propriedade for preenchida no cartão. Para o canal Teams, honramos apenas a `Id` propriedade, que identifica exclusivamente uma solicitação de token.

>[!NOTE]
> A estrutura de bot `OAuthPrompt` ou o `MultiProviderAuthDialog` tem suporte para autenticação de logon único (SSO).

Se esta for a primeira vez que o usuário está usando seu aplicativo e o consentimento do usuário for necessário, o usuário será mostrado em uma caixa de diálogo para continuar com a experiência de consentimento semelhante à seguinte. Quando o usuário seleciona **continue**, duas coisas diferentes ocorrem dependendo se o bot está definido ou não e um botão de entrada no OAuthCard.

![Caixa de diálogo de consentimento](../../../assets/images/bots/bots-consent-dialogbox.png)

Se o bot definir um botão de entrada, o fluxo de entrada para bots será disparado de forma semelhante ao fluxo de entrada de um botão de cartão em um fluxo de mensagens. O desenvolvedor deve decidir quais permissões solicitar ao usuário para o consentimento. Essa abordagem é recomendada se você precisar de um token com permissões além disso `openId` , por exemplo, se você deseja trocar o token para recursos de Graph.

Se o bot não fornecer um botão de entrada no cartão, ele acionará o consentimento do usuário para um conjunto mínimo de permissões. Esse token é útil para a autenticação básica e obter o endereço de email do usuário.

**Solicitação de token C# sem um botão de entrada**:

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

#### <a name="receiving-the-token"></a>Recebendo o token

A resposta com o token é enviada por meio de uma atividade Invoke com o mesmo esquema que outras pessoas invocam atividades que os bots recebem hoje. A única diferença é o nome de chamada, de **entrada/tokenExchange** e o campo de **valor** que conterá a **ID** (uma cadeia de caracteres) da solicitação inicial para obter o token e o campo de **token** (um valor de cadeia de caracteres incluindo o token). Observe que você pode receber várias respostas para uma determinada solicitação se o usuário tiver vários pontos de extremidade ativos. Você precisará desduplicar as respostas com o token.

**Código C# para responder à manipulação da atividade de invocação**:

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

O `turnContext.activity.value` é do tipo [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) e contém o token que pode ser usado com seu bot. Armazene os tokens com segurança por motivos de desempenho e atualize-os.

### <a name="update-the-azure-portal-with-the-oauth-connection"></a>Atualizar o portal do Azure com a conexão OAuth

1. No portal do Azure, volte para o **registro de canais de bot**.

2. Alterne para a folha **configurações** e escolha **Adicionar configuração** na seção Configurações de conexão OAuth.

![Exibição SSOBotHandle2](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

3. Preencha o formulário de **configuração de conexão** :

> [!div class="checklist"]
>
> * Insira um nome para a nova configuração de conexão. Este será o nome que é referenciado dentro das configurações do código do serviço de bot na **etapa 5**.
> * No menu suspenso provedor de serviços, selecione **Azure Active Directory v2**.
>* Insira as credenciais do cliente para o aplicativo AAD.

>[!NOTE]
> A **concessão implícita** pode ser necessária no aplicativo AAD.

>* Para a URL do token do Exchange, use o valor de escopo definido na etapa anterior do aplicativo AAD. A presença da URL de token do Exchange indica ao SDK que este aplicativo AAD está configurado para SSO.
>* Especifique "comum" como a **ID do locatário**.
>* Adicione todos os escopos configurados ao especificar permissões para APIs de downstream para seu aplicativo AAD. Com a ID do cliente e o segredo do cliente fornecidos, o repositório de tokens irá trocar o token de um token de gráfico com permissões definidas para você.
>* Selecione **Salvar**.

![Exibição de configuração de VuSSOBotConnection](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-the-auth-sample"></a>Atualizar o exemplo de autenticação

Comece com o [exemplo de autenticação do Microsoft Teams](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).

1. Atualize o TeamsBot para incluir o seguinte. Para lidar com o deduping da solicitação de entrada, confira a seguir:

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
  
2. Atualize o `appsettings.json` para incluir o `botId` , senha e o nome da conexão definido acima.
3. Atualize o manifesto e verifique se `token.botframework.com` está na seção domínios válidos.
4. Zip o manifesto com as imagens de perfil e instalá-lo no Microsoft Teams.

#### <a name="additional-code-samples"></a>Exemplos de código adicionais

* [Amostra C# usando o SDK da estrutura de bot](https://microsoft-my.sharepoint-df.com/:u:/p/vul/ETZQfeTViDlCv-frjgTIincB7dvk2HOnma1TLvcoeGGIxg?e=uPq62c).

* [Exemplo C# usando o SDK da estrutura de bot para reduplicar a solicitação de token](https://microsoft.sharepoint.com/:u:/t/ExtensibilityandFundamentals/Ea36rUGiN1BGt1RiLOb-mY8BGMF8NwPtronYGym0sCGOTw?e=4bB682).

* [Amostra C# sem usar o repositório de token do SDK da estrutura do bot](https://microsoft-my.sharepoint-df.com/:u:/p/tac/EceKDXrkMn5AuGbh6iGid8ABKEVQ6hkxArxK1y7-M8OVPw)
