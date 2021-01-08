---
title: Suporte de logon único para bots
description: Descreve como obter um token de usuário. Atualmente, um desenvolvedor de bot pode usar um cartão de entrada ou o serviço do Azure bot com o suporte a cartão OAuth.
keywords: token, token de usuário, suporte SSO para bots
ms.openlocfilehash: ee9dbee063acf90f5596fc95d002caf53f88a08a
ms.sourcegitcommit: 0a9e91c65d88512eda895c21371b3cd4051dca0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2020
ms.locfileid: "49729066"
---
# <a name="single-sign-on-sso-support-for-bots"></a><span data-ttu-id="85821-105">Suporte de logon único (SSO) para bots</span><span class="sxs-lookup"><span data-stu-id="85821-105">Single sign-on (SSO) support for bots</span></span>

<span data-ttu-id="85821-106">A autenticação de logon único no Azure Active Directory (Azure AD) minimiza o número de vezes que os usuários precisam inserir suas credenciais de logon, atualizando silenciosamente o token de autenticação.</span><span class="sxs-lookup"><span data-stu-id="85821-106">Single sign-on authentication in Azure Active Directory (Azure AD) minimizes the number of times users need to enter their login credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="85821-107">Se os usuários concordarem em usar seu aplicativo, eles não precisarão ser consentidos novamente em outro dispositivo e serão conectados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="85821-107">If users agree to use your app, they will not have to consent again on another device and will be signed in automatically.</span></span> <span data-ttu-id="85821-108">O fluxo é muito semelhante ao [suporte de SSO da guia do teams]( ../../../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="85821-108">The flow is very similar to the [Teams tab SSO support]( ../../../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="85821-109">A diferença é o protocolo de como um bot solicita tokens e recebe respostas.</span><span class="sxs-lookup"><span data-stu-id="85821-109">The difference is the protocol for how a bot requests tokens and receives responses.</span></span>

<span data-ttu-id="85821-110">O OAuth 2,0 é um padrão aberto para autenticação e autorização usados pelo Azure Active Directory (Azure AD) e muitos outros provedores de identidade.</span><span class="sxs-lookup"><span data-stu-id="85821-110">OAuth 2.0 is an open standard for authentication and authorization used by Azure Active Directory (Azure AD) and many other identity providers.</span></span> <span data-ttu-id="85821-111">Uma compreensão básica do OAuth 2,0 é um pré-requisito para trabalhar com autenticação no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="85821-111">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

## <a name="bot-sso-at-runtime"></a><span data-ttu-id="85821-112">SSO do bot no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="85821-112">Bot SSO at runtime</span></span>

![SSO do bot no diagrama de tempo de execução](../../../assets/images/bots/bots-sso-diagram.png)

1. <span data-ttu-id="85821-114">O bot envia uma mensagem com um OAuthCard que contém a `tokenExchangeResource` propriedade.</span><span class="sxs-lookup"><span data-stu-id="85821-114">The bot sends a message with an OAuthCard that contains the `tokenExchangeResource` property.</span></span> <span data-ttu-id="85821-115">Ele diz às Teams para obter um token de autenticação para o aplicativo bot.</span><span class="sxs-lookup"><span data-stu-id="85821-115">It tells Teams to obtain an authentication token for the bot application.</span></span> <span data-ttu-id="85821-116">O usuário recebe mensagens em todos os pontos de extremidade ativos do usuário.</span><span class="sxs-lookup"><span data-stu-id="85821-116">The user receives messages at all the active endpoints of the user.</span></span>

    > [!NOTE]
    >* <span data-ttu-id="85821-117">Um usuário pode ter mais de um ponto de extremidade ativo por vez.</span><span class="sxs-lookup"><span data-stu-id="85821-117">A user can have more than one active endpoint at a time.</span></span>  
    >* <span data-ttu-id="85821-118">O token de bot é recebido de todos os pontos de extremidade ativos do usuário.</span><span class="sxs-lookup"><span data-stu-id="85821-118">The bot token is received from every active endpoint of the user.</span></span>
    >* <span data-ttu-id="85821-119">No momento, o suporte a logon único exige que o aplicativo seja instalado no escopo pessoal.</span><span class="sxs-lookup"><span data-stu-id="85821-119">Single sign-on support currently requires the app to be installed in personal scope.</span></span>

2. <span data-ttu-id="85821-120">Se esta for a primeira vez que o usuário atual usou seu aplicativo bot, haverá um prompt de solicitação para o consentimento (se o consentimento for necessário) ou para lidar com a autenticação de depuração (como a autenticação de dois fatores).</span><span class="sxs-lookup"><span data-stu-id="85821-120">If it is the first time the current user has used your bot application, there will be a request prompt to consent (if consent is required) or to handle step-up authentication (such as two-factor authentication).</span></span>

3. <span data-ttu-id="85821-121">O Microsoft Teams solicita o token do aplicativo bot do ponto de extremidade do Azure AD para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="85821-121">Microsoft Teams requests the bot application token from the Azure AD endpoint for the current user.</span></span>

4. <span data-ttu-id="85821-122">O Azure AD envia o token do aplicativo bot para o aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="85821-122">Azure AD sends the bot application token to the Teams application.</span></span>

5. <span data-ttu-id="85821-123">O Microsoft Teams envia o token para o bot como parte do objeto de valor retornado pela atividade Invoke com o nome de entrada/tokenExchange.</span><span class="sxs-lookup"><span data-stu-id="85821-123">Microsoft Teams sends the token to the bot as part of the value object returned by the invoke activity with the name sign-in/tokenExchange.</span></span>
  
6. <span data-ttu-id="85821-124">O token será analisado no aplicativo bot para extrair as informações necessárias, como o endereço de email do usuário.</span><span class="sxs-lookup"><span data-stu-id="85821-124">The token will be parsed in the bot application to extract the needed information, such as the user's email address.</span></span>
  
## <a name="develop-a-single-sign-on-microsoft-teams-bot"></a><span data-ttu-id="85821-125">Desenvolver um bot de logon único do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="85821-125">Develop a Single sign-on Microsoft Teams bot</span></span>
  
<span data-ttu-id="85821-126">As etapas a seguir são necessárias para desenvolver um bot do Microsoft Teams SSO:</span><span class="sxs-lookup"><span data-stu-id="85821-126">The following steps are required to develop an SSO Microsoft Teams bot:</span></span>

1. [<span data-ttu-id="85821-127">Criar uma conta gratuita do Azure</span><span class="sxs-lookup"><span data-stu-id="85821-127">Create an Azure free account</span></span>](#create-an-azure-account)
2. [<span data-ttu-id="85821-128">Atualizar o manifesto do aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="85821-128">Update your Teams app manifest</span></span>](#update-your-app-manifest)
3. [<span data-ttu-id="85821-129">Adicionar o código para solicitar e receber o token de bot</span><span class="sxs-lookup"><span data-stu-id="85821-129">Add the code to request and receive the bot token</span></span>](#request-a-bot-token)

### <a name="create-an-azure-account"></a><span data-ttu-id="85821-130">Crie uma conta do Azure</span><span class="sxs-lookup"><span data-stu-id="85821-130">Create an Azure account</span></span>

<span data-ttu-id="85821-131">Esta etapa é semelhante ao [fluxo de SSO de guia](../../../tabs/how-to/authentication/auth-aad-sso.md):</span><span class="sxs-lookup"><span data-stu-id="85821-131">This step is similar to the [tab SSO flow](../../../tabs/how-to/authentication/auth-aad-sso.md):</span></span>

1. <span data-ttu-id="85821-132">Obter sua [ID de aplicativo do Azure ad](/graph/concepts/auth-register-app-v2) para o Teams desktop, o Web ou o cliente móvel.</span><span class="sxs-lookup"><span data-stu-id="85821-132">Get your [Azure AD Application ID](/graph/concepts/auth-register-app-v2) for Teams desktop, web, or mobile client.</span></span>
2. <span data-ttu-id="85821-133">Especifique as permissões de que seu aplicativo precisa para o ponto de extremidade do Azure AD e, opcionalmente, o Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="85821-133">Specify the permissions that your application needs for the Azure AD endpoint and, optionally, Microsoft Graph.</span></span>
3. <span data-ttu-id="85821-134">[Conceder permissões](/azure/active-directory/develop/v2-permissions-and-consent) para aplicativos de desktop, Web e móveis do teams.</span><span class="sxs-lookup"><span data-stu-id="85821-134">[Grant permissions](/azure/active-directory/develop/v2-permissions-and-consent) for Teams desktop, web, and mobile applications.</span></span>
4. <span data-ttu-id="85821-135">Selecione **Adicionar um escopo**.</span><span class="sxs-lookup"><span data-stu-id="85821-135">Select **Add a scope**.</span></span>
5. <span data-ttu-id="85821-136">No painel que é aberto, adicione um aplicativo cliente inserindo `access_as_user` como o **nome do escopo**.</span><span class="sxs-lookup"><span data-stu-id="85821-136">In the panel that opens, add a client app by entering `access_as_user` as the **Scope name**.</span></span>

    >[!NOTE]
    > <span data-ttu-id="85821-137">O escopo "access_as_user" usado para adicionar um aplicativo cliente é para "administradores e usuários".</span><span class="sxs-lookup"><span data-stu-id="85821-137">The "access_as_user" scope used to add a client app is for "Administrators and users".</span></span>

    > [!IMPORTANT]
    > * <span data-ttu-id="85821-138">Se você estiver criando um bot autônomo, defina o URI da ID do aplicativo como `api://botid-{YourBotId}` aqui, **YourBotId** refere-se à sua ID de aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="85821-138">If you are building a standalone bot, set the Application ID URI to `api://botid-{YourBotId}` Here, **YourBotId** refers to your Azure AD application ID.</span></span>
    > * <span data-ttu-id="85821-139">Se você estiver criando um aplicativo com um bot e uma guia, defina o URI da ID do aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}` .</span><span class="sxs-lookup"><span data-stu-id="85821-139">If you are building an app with a bot and a tab, set the Application ID URI to `api://fully-qualified-domain-name.com/botid-{YourBotId}`.</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="85821-140">Atualizar o manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="85821-140">Update your app manifest</span></span>

<span data-ttu-id="85821-141">Adicione novas propriedades ao manifesto do Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="85821-141">Add new properties to your Microsoft Teams manifest:</span></span>

<span data-ttu-id="85821-142">**WebApplicationInfo** -o pai dos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="85821-142">**WebApplicationInfo** - The parent of the following elements:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="85821-143">**ID** – a ID do cliente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85821-143">**id** - The client ID of the application.</span></span> <span data-ttu-id="85821-144">Esta é a ID do aplicativo que você obteve como parte do registro do aplicativo com o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="85821-144">This is the application ID that you obtained as part of registering the application with Azure AD.</span></span>
>* <span data-ttu-id="85821-145">**Resource** -o domínio e o subdomínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85821-145">**resource** - The domain and subdomain of your application.</span></span> <span data-ttu-id="85821-146">Este é o mesmo URI (incluindo o `api://` protocolo) que você registrou ao criar seu `scope` na etapa 6 acima.</span><span class="sxs-lookup"><span data-stu-id="85821-146">This is the same URI (including the `api://` protocol) that you registered when creating your `scope` in step 6 above.</span></span> <span data-ttu-id="85821-147">Você não deve incluir o `access_as_user` caminho em seu recurso.</span><span class="sxs-lookup"><span data-stu-id="85821-147">You shouldn't include the `access_as_user` path in your resource.</span></span> <span data-ttu-id="85821-148">A parte de domínio desse URI deve corresponder ao domínio, incluindo todos os subdomínios, usados nas URLs do manifesto de aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="85821-148">The domain part of this URI should match the domain, including any subdomains, used in the URLs of your Teams application manifest.</span></span>

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

### <a name="request-a-bot-token"></a><span data-ttu-id="85821-149">Solicitar um token de bot</span><span class="sxs-lookup"><span data-stu-id="85821-149">Request a bot token</span></span>

<span data-ttu-id="85821-150">A solicitação para obter o token é uma solicitação de mensagem POST normal (usando o esquema de mensagens existente).</span><span class="sxs-lookup"><span data-stu-id="85821-150">The request to get the token is a normal POST message request (using the existing message schema).</span></span> <span data-ttu-id="85821-151">Ele está incluído nos anexos de um OAuthCard.</span><span class="sxs-lookup"><span data-stu-id="85821-151">It is included in the attachments of an OAuthCard.</span></span> <span data-ttu-id="85821-152">O esquema da classe OAuthCard é definido no [esquema do Microsoft Bot 4,0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) e é muito semelhante a um cartão de conexão.</span><span class="sxs-lookup"><span data-stu-id="85821-152">The schema for the OAuthCard class is defined in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) and it is very similar to a sign-in card.</span></span> <span data-ttu-id="85821-153">O Microsoft Teams tratará essa solicitação como uma aquisição de token silencioso se a `TokenExchangeResource` propriedade for preenchida no cartão.</span><span class="sxs-lookup"><span data-stu-id="85821-153">Teams will treat this request as a silent token acquisition if the `TokenExchangeResource` property is populated on the card.</span></span> <span data-ttu-id="85821-154">Para o canal Teams, honramos apenas a `Id` propriedade, que identifica exclusivamente uma solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="85821-154">For the Teams channel, we honor only the `Id` property, which uniquely identifies a token request.</span></span>

>[!NOTE]
> <span data-ttu-id="85821-155">A estrutura de bot `OAuthPrompt` ou o `MultiProviderAuthDialog` tem suporte para autenticação de logon único (SSO).</span><span class="sxs-lookup"><span data-stu-id="85821-155">The Bot Framework `OAuthPrompt` or the `MultiProviderAuthDialog` is supported for single sign-on (SSO) authentication.</span></span>

<span data-ttu-id="85821-156">Se esta for a primeira vez que o usuário está usando seu aplicativo e o consentimento do usuário for necessário, o usuário será mostrado em uma caixa de diálogo para continuar com a experiência de consentimento semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="85821-156">If this is the first time the user is using your application and the user consent is required, the user will be shown a dialog to continue with the consent experience similar to the one below.</span></span> <span data-ttu-id="85821-157">Quando o usuário seleciona **continue**, duas coisas diferentes ocorrem dependendo se o bot está definido ou não e um botão de entrada no OAuthCard.</span><span class="sxs-lookup"><span data-stu-id="85821-157">When the user selects **Continue**, two different things occur depending on whether the bot is defined or not and a sign-in button on the OAuthCard.</span></span>

![Caixa de diálogo de consentimento](../../../assets/images/bots/bots-consent-dialogbox.png)

<span data-ttu-id="85821-159">Se o bot definir um botão de entrada, o fluxo de entrada para bots será disparado de forma semelhante ao fluxo de entrada de um botão de cartão em um fluxo de mensagens.</span><span class="sxs-lookup"><span data-stu-id="85821-159">If the bot defines a sign-in button, the sign-in flow for bots will be triggered similarly to the sign-in flow from a card button in a message stream.</span></span> <span data-ttu-id="85821-160">O desenvolvedor deve decidir quais permissões solicitar ao usuário para o consentimento.</span><span class="sxs-lookup"><span data-stu-id="85821-160">It is up to the developer to decide which permissions to ask for the user to consent.</span></span> <span data-ttu-id="85821-161">Essa abordagem é recomendada se você precisar de um token com permissões além disso `openId` , por exemplo, se você deseja trocar o token para recursos de Graph.</span><span class="sxs-lookup"><span data-stu-id="85821-161">This approach is recommended if you need a token with permissions beyond `openId`, for example, if you want to exchange the token for graph resources.</span></span>

<span data-ttu-id="85821-162">Se o bot não fornecer um botão de entrada no cartão, ele acionará o consentimento do usuário para um conjunto mínimo de permissões.</span><span class="sxs-lookup"><span data-stu-id="85821-162">If the bot is not providing a sign-in button on the card, it triggers user consent for a minimal set of permissions.</span></span> <span data-ttu-id="85821-163">Esse token é útil para a autenticação básica e obter o endereço de email do usuário.</span><span class="sxs-lookup"><span data-stu-id="85821-163">This token is useful for basic authentication and getting the user's email address.</span></span>

<span data-ttu-id="85821-164">**Solicitação de token C# sem um botão de entrada**:</span><span class="sxs-lookup"><span data-stu-id="85821-164">**C# token request without a sign-in button**:</span></span>

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

#### <a name="receiving-the-token"></a><span data-ttu-id="85821-165">Recebendo o token</span><span class="sxs-lookup"><span data-stu-id="85821-165">Receiving the token</span></span>

<span data-ttu-id="85821-166">A resposta com o token é enviada por meio de uma atividade Invoke com o mesmo esquema que outras pessoas invocam atividades que os bots recebem hoje.</span><span class="sxs-lookup"><span data-stu-id="85821-166">The response with the token is sent through an invoke activity with the same schema as others invoke activities the bots receive today.</span></span> <span data-ttu-id="85821-167">A única diferença é o nome de chamada, de **entrada/tokenExchange** e o campo de **valor** que conterá a **ID** (uma cadeia de caracteres) da solicitação inicial para obter o token e o campo de **token** (um valor de cadeia de caracteres incluindo o token).</span><span class="sxs-lookup"><span data-stu-id="85821-167">The only difference is the invoke name, **sign-in/tokenExchange** and the **value** field which will contain the **Id** (a string) of the initial request to get the token and the **token** field (a string value including the token).</span></span> <span data-ttu-id="85821-168">Observe que você pode receber várias respostas para uma determinada solicitação se o usuário tiver vários pontos de extremidade ativos.</span><span class="sxs-lookup"><span data-stu-id="85821-168">Please note that you might receive multiple responses for a given request if the user has multiple active endpoints.</span></span> <span data-ttu-id="85821-169">Você precisará desduplicar as respostas com o token.</span><span class="sxs-lookup"><span data-stu-id="85821-169">It is up to you to deduplicate the responses with the token.</span></span>

<span data-ttu-id="85821-170">**Código C# para responder à manipulação da atividade de invocação**:</span><span class="sxs-lookup"><span data-stu-id="85821-170">**C# code to respond to handle the invoke activity**:</span></span>

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

<span data-ttu-id="85821-171">O `turnContext.activity.value` é do tipo [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) e contém o token que pode ser usado com seu bot.</span><span class="sxs-lookup"><span data-stu-id="85821-171">The `turnContext.activity.value` is of type [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) and contains the token that can be further used by your bot.</span></span> <span data-ttu-id="85821-172">Armazene os tokens com segurança por motivos de desempenho e atualize-os.</span><span class="sxs-lookup"><span data-stu-id="85821-172">Store the tokens securely for performance reasons and refresh them.</span></span>

### <a name="update-the-azure-portal-with-the-oauth-connection"></a><span data-ttu-id="85821-173">Atualizar o portal do Azure com a conexão OAuth</span><span class="sxs-lookup"><span data-stu-id="85821-173">Update the Azure portal with the OAuth connection</span></span>

1. <span data-ttu-id="85821-174">No portal do Azure, volte para o **registro de canais de bot**.</span><span class="sxs-lookup"><span data-stu-id="85821-174">In the Azure Portal, navigate back to the **Bot Channels Registration**.</span></span>

2. <span data-ttu-id="85821-175">Alterne para a folha **configurações** e escolha **Adicionar configuração** na seção Configurações de conexão OAuth.</span><span class="sxs-lookup"><span data-stu-id="85821-175">Switch to the **Settings** blade and choose **Add Setting** under the OAuth Connection Settings section.</span></span>

    ![Exibição SSOBotHandle2](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

3. <span data-ttu-id="85821-177">Preencha o formulário de **configuração de conexão** :</span><span class="sxs-lookup"><span data-stu-id="85821-177">Complete the **Connection Setting** form:</span></span>

    > [!div class="checklist"]
    >
    > * <span data-ttu-id="85821-178">Insira um nome para a nova configuração de conexão.</span><span class="sxs-lookup"><span data-stu-id="85821-178">Enter a name for your new Connection Setting.</span></span> <span data-ttu-id="85821-179">Este será o nome que é referenciado dentro das configurações do código do serviço de bot na **etapa 5**.</span><span class="sxs-lookup"><span data-stu-id="85821-179">This will be the name that gets referenced inside the settings of your bot service code in **step 5**.</span></span>
    > * <span data-ttu-id="85821-180">No menu suspenso provedor de serviços, selecione **Azure Active Directory v2**.</span><span class="sxs-lookup"><span data-stu-id="85821-180">In the Service Provider dropdown, select **Azure Active Directory V2**.</span></span>
    >* <span data-ttu-id="85821-181">Insira as credenciais do cliente para o aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="85821-181">Enter the client credentials for the AAD application.</span></span>

    >[!NOTE]
    > <span data-ttu-id="85821-182">A **concessão implícita** pode ser necessária no aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="85821-182">**Implicit grant** may be required in the AAD application.</span></span>

    >* <span data-ttu-id="85821-183">Para a URL do token do Exchange, use o valor de escopo definido na etapa anterior do aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="85821-183">For the Token Exchange URL, use the scope value defined in the previous step of your AAD application.</span></span> <span data-ttu-id="85821-184">A presença da URL de token do Exchange indica ao SDK que este aplicativo AAD está configurado para SSO.</span><span class="sxs-lookup"><span data-stu-id="85821-184">The presence of the Token Exchange URL is indicating to the SDK that this AAD application is configured for SSO.</span></span>
    >* <span data-ttu-id="85821-185">Especifique "comum" como a **ID do locatário**.</span><span class="sxs-lookup"><span data-stu-id="85821-185">Specify "common" as the **Tenant ID**.</span></span>
    >* <span data-ttu-id="85821-186">Adicione todos os escopos configurados ao especificar permissões para APIs de downstream para seu aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="85821-186">Add all the scopes configured when specifying permissions to downstream APIs for your AAD application.</span></span> <span data-ttu-id="85821-187">Com a ID do cliente e o segredo do cliente fornecidos, o repositório de tokens irá trocar o token de um token de gráfico com permissões definidas para você.</span><span class="sxs-lookup"><span data-stu-id="85821-187">With the client id and client secret provided, the token store will exchange the token for a graph token with defined permissions for you.</span></span>
    >* <span data-ttu-id="85821-188">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="85821-188">Select **Save**.</span></span>

    ![Exibição de configuração de VuSSOBotConnection](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-the-auth-sample"></a><span data-ttu-id="85821-190">Atualizar o exemplo de autenticação</span><span class="sxs-lookup"><span data-stu-id="85821-190">Update the auth sample</span></span>

<span data-ttu-id="85821-191">Comece com o [exemplo de autenticação do Microsoft Teams](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span><span class="sxs-lookup"><span data-stu-id="85821-191">Start with the [teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span></span>

1. <span data-ttu-id="85821-192">Atualize o TeamsBot para incluir o seguinte.</span><span class="sxs-lookup"><span data-stu-id="85821-192">Update the TeamsBot to include the following.</span></span> <span data-ttu-id="85821-193">Para lidar com o deduping da solicitação de entrada, confira a seguir:</span><span class="sxs-lookup"><span data-stu-id="85821-193">To handle the deduping of the incoming request, see below:</span></span>

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
  
2. <span data-ttu-id="85821-194">Atualize o `appsettings.json` para incluir o `botId` , senha e o nome da conexão definido acima.</span><span class="sxs-lookup"><span data-stu-id="85821-194">Update the `appsettings.json` to include the `botId`, password, and the connection name defined above.</span></span>
3. <span data-ttu-id="85821-195">Atualize o manifesto e verifique se `token.botframework.com` está na seção domínios válidos.</span><span class="sxs-lookup"><span data-stu-id="85821-195">Update the manifest and ensure that `token.botframework.com` is in the valid domains section.</span></span>
4. <span data-ttu-id="85821-196">Zip o manifesto com as imagens de perfil e instalá-lo no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="85821-196">Zip the manifest with the profile images and install it in Teams.</span></span>

#### <a name="additional-code-samples"></a><span data-ttu-id="85821-197">Exemplos de código adicionais</span><span class="sxs-lookup"><span data-stu-id="85821-197">Additional code samples</span></span>

* <span data-ttu-id="85821-198">[Amostra C# usando o SDK da estrutura de bot](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore).</span><span class="sxs-lookup"><span data-stu-id="85821-198">[C# sample using the Bot Framework SDK](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore).</span></span>

* <span data-ttu-id="85821-199">[Exemplo C# usando o SDK da estrutura de bot para reduplicar a solicitação de token](https://microsoft.sharepoint.com/:u:/t/ExtensibilityandFundamentals/Ea36rUGiN1BGt1RiLOb-mY8BGMF8NwPtronYGym0sCGOTw?e=4bB682).</span><span class="sxs-lookup"><span data-stu-id="85821-199">[C# sample using the Bot Framework SDK to deduplicate the token request](https://microsoft.sharepoint.com/:u:/t/ExtensibilityandFundamentals/Ea36rUGiN1BGt1RiLOb-mY8BGMF8NwPtronYGym0sCGOTw?e=4bB682).</span></span>

* <span data-ttu-id="85821-200">[Amostra C# sem usar o repositório de token do SDK da estrutura de bot](https://microsoft-my.sharepoint-df.com/:u:/p/tac/EceKDXrkMn5AuGbh6iGid8ABKEVQ6hkxArxK1y7-M8OVPw).</span><span class="sxs-lookup"><span data-stu-id="85821-200">[C# sample without using the Bot Framework SDK token store](https://microsoft-my.sharepoint-df.com/:u:/p/tac/EceKDXrkMn5AuGbh6iGid8ABKEVQ6hkxArxK1y7-M8OVPw).</span></span>
