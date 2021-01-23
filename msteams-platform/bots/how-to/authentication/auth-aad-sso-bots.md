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
# <a name="single-sign-on-sso-support-for-bots"></a><span data-ttu-id="91b9f-105">Suporte a SSO (single sign-on) para bots</span><span class="sxs-lookup"><span data-stu-id="91b9f-105">Single sign-on (SSO) support for bots</span></span>

<span data-ttu-id="91b9f-106">A autenticação de login único no Azure Active Directory (AAD) minimiza o número de vezes que os usuários precisam inserir suas credenciais de entrada ao atualizar silenciosamente o token de autenticação.</span><span class="sxs-lookup"><span data-stu-id="91b9f-106">Single sign-on authentication in Azure Active Directory (AAD) minimizes the number of times users need to enter their sign in credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="91b9f-107">Se os usuários concordarem em usar seu aplicativo, eles não precisarão dar consentimento novamente em outro dispositivo e poderão entrar automaticamente.</span><span class="sxs-lookup"><span data-stu-id="91b9f-107">If users agree to use your app, they need not provide consent again on another device and can sign in automatically.</span></span> <span data-ttu-id="91b9f-108">O fluxo é semelhante ao do suporte ao SSO da guia [Do Microsoft Teams,](../../../tabs/how-to/authentication/auth-aad-sso.md)no entanto, a diferença está no protocolo de como um bot solicita [tokens](#request-a-bot-token) e recebe [respostas.](#receive-the-bot-token)</span><span class="sxs-lookup"><span data-stu-id="91b9f-108">The flow is similar to that of [Microsoft Teams tab SSO support](../../../tabs/how-to/authentication/auth-aad-sso.md), however, the difference is in the protocol for how a bot [requests tokens](#request-a-bot-token) and [receives responses](#receive-the-bot-token).</span></span>

>[!NOTE]
> <span data-ttu-id="91b9f-109">O OAuth 2.0 é um padrão aberto para autenticação e autorização usados pelo AAD e muitos outros provedores de identidade.</span><span class="sxs-lookup"><span data-stu-id="91b9f-109">OAuth 2.0 is an open standard for authentication and authorization used by AAD and many other identity providers.</span></span> <span data-ttu-id="91b9f-110">Uma compreensão básica do OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams.</span><span class="sxs-lookup"><span data-stu-id="91b9f-110">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

## <a name="bot-sso-at-runtime"></a><span data-ttu-id="91b9f-111">SSO de bot em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="91b9f-111">Bot SSO at runtime</span></span>

![SSO do bot no diagrama de tempo de execução](../../../assets/images/bots/bots-sso-diagram.png)

<span data-ttu-id="91b9f-113">Conclua as seguintes etapas para obter tokens de aplicativo de bot e autenticação:</span><span class="sxs-lookup"><span data-stu-id="91b9f-113">Complete the following steps to get authentication and bot application tokens:</span></span>

1. <span data-ttu-id="91b9f-114">O bot envia uma mensagem com um OAuthCard que contém a `tokenExchangeResource` propriedade.</span><span class="sxs-lookup"><span data-stu-id="91b9f-114">The bot sends a message with an OAuthCard that contains the `tokenExchangeResource` property.</span></span> <span data-ttu-id="91b9f-115">Ele informa ao Teams para obter um token de autenticação para o aplicativo bot.</span><span class="sxs-lookup"><span data-stu-id="91b9f-115">It tells Teams to obtain an authentication token for the bot application.</span></span> <span data-ttu-id="91b9f-116">O usuário recebe mensagens em todos os pontos de extremidade do usuário ativo.</span><span class="sxs-lookup"><span data-stu-id="91b9f-116">The user receives messages at all the active user endpoints.</span></span>

    > [!NOTE]
    >* <span data-ttu-id="91b9f-117">Um usuário pode ter mais de um ponto de extremidade ativo por vez.</span><span class="sxs-lookup"><span data-stu-id="91b9f-117">A user can have more than one active endpoint at a time.</span></span>
    >* <span data-ttu-id="91b9f-118">O token de bot é recebido de cada ponto de extremidade de usuário ativo.</span><span class="sxs-lookup"><span data-stu-id="91b9f-118">The bot token is received from every active user endpoint.</span></span>
    >* <span data-ttu-id="91b9f-119">O aplicativo deve ser instalado no escopo pessoal para suporte a SSO.</span><span class="sxs-lookup"><span data-stu-id="91b9f-119">The app must be installed in personal scope for SSO support.</span></span>

2. <span data-ttu-id="91b9f-120">Se o usuário atual estiver usando seu aplicativo bot pela primeira vez, um prompt de solicitação será exibido solicitando que o usuário faça um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="91b9f-120">If the current user is using your bot application for the first time, a request prompt appears requesting the user to do one of the following:</span></span>
    * <span data-ttu-id="91b9f-121">Forneça consentimento, se necessário.</span><span class="sxs-lookup"><span data-stu-id="91b9f-121">Provide consent, if required.</span></span>
    * <span data-ttu-id="91b9f-122">Tratar a autenticação de etapa, como a autenticação de dois fatores.</span><span class="sxs-lookup"><span data-stu-id="91b9f-122">Handle step-up authentication, such as two-factor authentication.</span></span>

3. <span data-ttu-id="91b9f-123">O Teams solicita o token do aplicativo bot do ponto de extremidade do AAD para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="91b9f-123">Teams requests the bot application token from the AAD endpoint for the current user.</span></span>

4. <span data-ttu-id="91b9f-124">O AAD envia o token do aplicativo bot para o aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="91b9f-124">AAD sends the bot application token to the Teams application.</span></span>

5. <span data-ttu-id="91b9f-125">O Teams envia o token para o bot como parte do objeto de valor retornado pela atividade de invocação com o nome **entrar/tokenExchange**.</span><span class="sxs-lookup"><span data-stu-id="91b9f-125">Teams sends the token to the bot as part of the value object returned by the invoke activity with the name **sign-in/tokenExchange**.</span></span>
  
6. <span data-ttu-id="91b9f-126">O token analisado no aplicativo bot fornece as informações necessárias, como o endereço de email do usuário.</span><span class="sxs-lookup"><span data-stu-id="91b9f-126">The parsed token in the bot application provides the required information, such as the user's email address.</span></span>
  
## <a name="develop-an-sso-teams-bot"></a><span data-ttu-id="91b9f-127">Desenvolver um bot do SSO Teams</span><span class="sxs-lookup"><span data-stu-id="91b9f-127">Develop an SSO Teams bot</span></span>
  
<span data-ttu-id="91b9f-128">Conclua as seguintes etapas para desenvolver um bot do SSO Teams:</span><span class="sxs-lookup"><span data-stu-id="91b9f-128">Complete the following steps to develop an SSO Teams bot:</span></span>

1. <span data-ttu-id="91b9f-129">[Registre seu aplicativo por meio do portal do AAD.](#register-your-app-through-the-aad-portal)</span><span class="sxs-lookup"><span data-stu-id="91b9f-129">[Register your app through the AAD portal](#register-your-app-through-the-aad-portal).</span></span>
2. <span data-ttu-id="91b9f-130">[Atualize o manifesto do aplicativo Teams para seu bot.](#update-your-teams-application-manifest-for-your-bot)</span><span class="sxs-lookup"><span data-stu-id="91b9f-130">[Update your Teams application manifest for your bot](#update-your-teams-application-manifest-for-your-bot).</span></span>
3. <span data-ttu-id="91b9f-131">[Adicione o código para solicitar e receber um token de bot.](#add-the-code-to-request-and-receive-a-bot-token)</span><span class="sxs-lookup"><span data-stu-id="91b9f-131">[Add the code to request and receive a bot token](#add-the-code-to-request-and-receive-a-bot-token).</span></span>

### <a name="register-your-app-through-the-aad-portal"></a><span data-ttu-id="91b9f-132">Registrar seu aplicativo por meio do portal do AAD</span><span class="sxs-lookup"><span data-stu-id="91b9f-132">Register your app through the AAD portal</span></span>

<span data-ttu-id="91b9f-133">As etapas para registrar seu aplicativo por meio do portal do AAD são semelhantes ao [fluxo SSO da guia.](../../../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="91b9f-133">The steps to register your app through the AAD portal are similar to the [tab SSO flow](../../../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="91b9f-134">Conclua as seguintes etapas para registrar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="91b9f-134">Complete the following steps to register your app:</span></span>

1. <span data-ttu-id="91b9f-135">Registre um novo aplicativo no [Azure Active Directory – portal de Registros de Aplicativos.](https://go.microsoft.com/fwlink/?linkid=2083908)</span><span class="sxs-lookup"><span data-stu-id="91b9f-135">Register a new application in the [Azure Active Directory – App Registrations](https://go.microsoft.com/fwlink/?linkid=2083908) portal.</span></span>
2. <span data-ttu-id="91b9f-136">Selecione **Novo Registro.**</span><span class="sxs-lookup"><span data-stu-id="91b9f-136">Select **New Registration**.</span></span> <span data-ttu-id="91b9f-137">A **página Registrar um aplicativo** é exibida.</span><span class="sxs-lookup"><span data-stu-id="91b9f-137">The **Register an application** page appears.</span></span>
3. <span data-ttu-id="91b9f-138">Na página **Registrar um aplicativo,** insira os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="91b9f-138">In the **Register an application** page, enter the following values:</span></span>
    1. <span data-ttu-id="91b9f-139">Insira um **nome** para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91b9f-139">Enter a **Name** for your app.</span></span>
    2. <span data-ttu-id="91b9f-140">Escolha os **tipos de conta com suporte,** selecione o tipo de conta de locatário único ou de vários locatários.</span><span class="sxs-lookup"><span data-stu-id="91b9f-140">Choose the **Supported account types**, select single tenant or multitenant account type.</span></span>

        > [!NOTE]
        >
        > <span data-ttu-id="91b9f-141">Os usuários não são solicitados a consentir e são concedidos tokens de acesso imediatamente, se o aplicativo AAD estiver registrado no mesmo locatário em que estão fazendo uma solicitação de autenticação no Teams.</span><span class="sxs-lookup"><span data-stu-id="91b9f-141">The users are not asked for consent and are granted access tokens right away, if the AAD app is registered in the same tenant where they are making an authentication request in Teams.</span></span> <span data-ttu-id="91b9f-142">No entanto, os usuários devem dar consentimento para as permissões, se o aplicativo AAD estiver registrado em um locatário diferente.</span><span class="sxs-lookup"><span data-stu-id="91b9f-142">However, the users must provide consent to the permissions, if the AAD app is registered in a different tenant.</span></span>

    3. <span data-ttu-id="91b9f-143">Escolha **Registrar**.</span><span class="sxs-lookup"><span data-stu-id="91b9f-143">Choose **Register**.</span></span>
4. <span data-ttu-id="91b9f-144">Na página de visão geral, copie e salve a **ID do aplicativo (cliente).**</span><span class="sxs-lookup"><span data-stu-id="91b9f-144">On the overview page, copy and save the **Application (client) ID**.</span></span> <span data-ttu-id="91b9f-145">Você precisará dele mais tarde ao atualizar seu manifesto de aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="91b9f-145">You need it later when updating your Teams application manifest.</span></span>
5. <span data-ttu-id="91b9f-146">Em **Gerenciar**, selecione **Expor uma API**.</span><span class="sxs-lookup"><span data-stu-id="91b9f-146">Under **Manage**, select **Expose an API**.</span></span> 

   > [!IMPORTANT]
    > * <span data-ttu-id="91b9f-147">Se você estiver criando um bot autônomo, insira o URI da ID do Aplicativo como `api://botid-{YourBotId}` .</span><span class="sxs-lookup"><span data-stu-id="91b9f-147">If you are building a standalone bot, enter the Application ID URI as `api://botid-{YourBotId}`.</span></span> <span data-ttu-id="91b9f-148">Aqui, **YourBotId** é sua ID de aplicativo do AAD.</span><span class="sxs-lookup"><span data-stu-id="91b9f-148">Here **YourBotId** is your AAD application ID.</span></span>
    > * <span data-ttu-id="91b9f-149">Se você estiver criando um aplicativo com um bot e uma guia, insira o URI da ID do Aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}` .</span><span class="sxs-lookup"><span data-stu-id="91b9f-149">If you are building an app with a bot and a tab, enter the Application ID URI as `api://fully-qualified-domain-name.com/botid-{YourBotId}`.</span></span>

5. <span data-ttu-id="91b9f-150">Selecione as permissões que seu aplicativo precisa para o ponto de extremidade do AAD e, opcionalmente, para o Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="91b9f-150">Select the permissions that your application needs for the AAD endpoint and, optionally, for Microsoft Graph.</span></span>
6. <span data-ttu-id="91b9f-151">[Conceda permissões para aplicativos](/azure/active-directory/develop/v2-permissions-and-consent) móveis, da web e da área de trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="91b9f-151">[Grant permissions](/azure/active-directory/develop/v2-permissions-and-consent) for Teams desktop, web, and mobile applications.</span></span>
7. <span data-ttu-id="91b9f-152">Selecione **Adicionar um escopo.**</span><span class="sxs-lookup"><span data-stu-id="91b9f-152">Select **Add a scope**.</span></span>
8. <span data-ttu-id="91b9f-153">No painel que é aberto, adicione um aplicativo cliente inserindo `access_as_user` como o nome do **escopo.**</span><span class="sxs-lookup"><span data-stu-id="91b9f-153">In the panel that opens, add a client app by entering `access_as_user` as the **Scope name**.</span></span>

    >[!NOTE]
    > <span data-ttu-id="91b9f-154">O escopo "access_as_user" usado para adicionar um aplicativo cliente é para "Administradores e usuários".</span><span class="sxs-lookup"><span data-stu-id="91b9f-154">The "access_as_user" scope used to add a client app is for "Administrators and users".</span></span>
    >
    > <span data-ttu-id="91b9f-155">Você deve estar ciente das seguintes restrições importantes:</span><span class="sxs-lookup"><span data-stu-id="91b9f-155">You must be aware of the following important restrictions:</span></span>
    >
    > * <span data-ttu-id="91b9f-156">Somente as permissões da API do Microsoft Graph em nível de usuário, como email, perfil, offline_access e OpenId, são suportadas.</span><span class="sxs-lookup"><span data-stu-id="91b9f-156">Only user-level Microsoft Graph API permissions, such as email, profile, offline_access, and OpenId are supported.</span></span> <span data-ttu-id="91b9f-157">Se você precisar de acesso a outros escopos do Microsoft Graph, como `User.Read` `Mail.Read` ou, confira [a solução alternativa recomendada.](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-microsoft-graph-scopes)</span><span class="sxs-lookup"><span data-stu-id="91b9f-157">If you need access to other Microsoft Graph scopes, such as `User.Read` or `Mail.Read`, see [recommended workaround](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-microsoft-graph-scopes).</span></span>
    > * <span data-ttu-id="91b9f-158">O nome de domínio do seu aplicativo deve ser igual ao nome de domínio que você registrou para seu aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="91b9f-158">Your application's domain name must be same as the domain name that you have registered for your AAD application.</span></span>
    > * <span data-ttu-id="91b9f-159">Atualmente, não há suporte para vários domínios por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91b9f-159">Multiple domains per app are currently not supported.</span></span>
    > * <span data-ttu-id="91b9f-160">Aplicativos que usam `azurewebsites.net` o domínio não são suportados porque é comum e pode ser um risco à segurança.</span><span class="sxs-lookup"><span data-stu-id="91b9f-160">Applications that use the `azurewebsites.net` domain are not supported because it is common and may be a security risk.</span></span>

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a><span data-ttu-id="91b9f-161">Atualizar o portal do Azure com a conexão OAuth</span><span class="sxs-lookup"><span data-stu-id="91b9f-161">Update the Azure portal with the OAuth connection</span></span>

<span data-ttu-id="91b9f-162">Conclua as seguintes etapas para atualizar o portal do Azure com a conexão OAuth:</span><span class="sxs-lookup"><span data-stu-id="91b9f-162">Complete the following steps to update the Azure portal with the OAuth connection:</span></span>

1. <span data-ttu-id="91b9f-163">No Portal do Azure, navegue até Registro **de Canais de Bot.**</span><span class="sxs-lookup"><span data-stu-id="91b9f-163">In the Azure Portal, navigate to **Bot Channels Registration**.</span></span>

2. <span data-ttu-id="91b9f-164">Vá para **permissões de API.**</span><span class="sxs-lookup"><span data-stu-id="91b9f-164">Go to **API Permissions**.</span></span> <span data-ttu-id="91b9f-165">Selecione **Adicionar uma permissão permissões**  >  **delegadas** do Microsoft Graph e, em  >  seguida, adicione as seguintes permissões da API do Microsoft Graph:</span><span class="sxs-lookup"><span data-stu-id="91b9f-165">Select **Add a permission** > **Microsoft Graph** > **Delegated permissions**, then add the following permissions from Microsoft Graph API:</span></span>
    * <span data-ttu-id="91b9f-166">User.Read (habilitado por padrão)</span><span class="sxs-lookup"><span data-stu-id="91b9f-166">User.Read (enabled by default)</span></span>
    * <span data-ttu-id="91b9f-167">email</span><span class="sxs-lookup"><span data-stu-id="91b9f-167">email</span></span>
    * <span data-ttu-id="91b9f-168">offline_access</span><span class="sxs-lookup"><span data-stu-id="91b9f-168">offline_access</span></span>
    * <span data-ttu-id="91b9f-169">OpenId</span><span class="sxs-lookup"><span data-stu-id="91b9f-169">OpenId</span></span>
    * <span data-ttu-id="91b9f-170">perfil</span><span class="sxs-lookup"><span data-stu-id="91b9f-170">profile</span></span>

3. <span data-ttu-id="91b9f-171">Selecione **Configurações** no painel esquerdo e escolha **Adicionar** Configuração na seção Configurações de Conexão **OAuth.**</span><span class="sxs-lookup"><span data-stu-id="91b9f-171">Select **Settings** on the left pane and choose **Add Setting** under the **OAuth Connection Settings** section.</span></span>

    ![Exibição SSOBotHandle2](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

4. <span data-ttu-id="91b9f-173">Execute as seguintes etapas para concluir o formulário **Nova Configuração de** Conexão:</span><span class="sxs-lookup"><span data-stu-id="91b9f-173">Perform the following steps to complete the **New Connection Setting** form:</span></span>

    >[!NOTE]
    > <span data-ttu-id="91b9f-174">**A concessão** implícita pode ser necessária no aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="91b9f-174">**Implicit grant** may be required in the AAD application.</span></span>

    1. <span data-ttu-id="91b9f-175">Insira um **nome na** página **Nova Configuração de** Conexão.</span><span class="sxs-lookup"><span data-stu-id="91b9f-175">Enter a **Name** in the **New Connection Setting** page.</span></span> <span data-ttu-id="91b9f-176">Esse é o nome que é referenciado dentro das configurações do seu código de serviço de bot na etapa *5* do Bot SSO em [tempo de execução.](#bot-sso-at-runtime)</span><span class="sxs-lookup"><span data-stu-id="91b9f-176">This is the name that is referred to inside the settings of your bot service code in *step 5* of [Bot SSO at runtime](#bot-sso-at-runtime).</span></span>
    2. <span data-ttu-id="91b9f-177">Na lista **drop-down** do Provedor de Serviços, selecione **Azure Active Directory v2**.</span><span class="sxs-lookup"><span data-stu-id="91b9f-177">From the **Service Provider** drop-down, select **Azure Active Directory v2**.</span></span>
    3. <span data-ttu-id="91b9f-178">Insira as credenciais do cliente, como **id do** cliente e **segredo do cliente** para o aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="91b9f-178">Enter the client credentials, such as **Client id** and **Client secret** for the AAD application.</span></span>
    4. <span data-ttu-id="91b9f-179">Para a **URL do Exchange de token,** use o valor de escopo definido em Atualizar seu manifesto de aplicativo do Teams para seu [bot.](#update-your-teams-application-manifest-for-your-bot)</span><span class="sxs-lookup"><span data-stu-id="91b9f-179">For the **Token Exchange URL**, use the scope value defined in [Update your Teams application manifest for your bot](#update-your-teams-application-manifest-for-your-bot).</span></span> <span data-ttu-id="91b9f-180">A URL do Exchange de token indica ao SDK que esse aplicativo AAD está configurado para SSO.</span><span class="sxs-lookup"><span data-stu-id="91b9f-180">The Token Exchange URL indicates to the SDK that this AAD application is configured for SSO.</span></span>
    5. <span data-ttu-id="91b9f-181">Na caixa **ID de locatário,** insira *comum*.</span><span class="sxs-lookup"><span data-stu-id="91b9f-181">In the **Tenant ID** box, enter *common*.</span></span>
    6. <span data-ttu-id="91b9f-182">Adicione todos os **Escopos configurados** ao especificar permissões para APIs downstream para seu aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="91b9f-182">Add all the **Scopes** configured when specifying permissions to downstream APIs for your AAD application.</span></span> <span data-ttu-id="91b9f-183">Com a ID do cliente e o segredo do cliente fornecidos, o armazenamento de token troca o token por um token de gráfico com permissões definidas.</span><span class="sxs-lookup"><span data-stu-id="91b9f-183">With the Client id and Client secret provided, the token store exchanges the token for a graph token with defined permissions.</span></span>
    7. <span data-ttu-id="91b9f-184">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="91b9f-184">Select **Save**.</span></span>

    ![Exibição de configuração VuSSOBotConnection](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a><span data-ttu-id="91b9f-186">Atualizar o manifesto do aplicativo Teams para seu bot</span><span class="sxs-lookup"><span data-stu-id="91b9f-186">Update your Teams application manifest for your bot</span></span>

<span data-ttu-id="91b9f-187">Se o aplicativo contiver um bot autônomo, use o código a seguir para adicionar novas propriedades ao manifesto do aplicativo Teams:</span><span class="sxs-lookup"><span data-stu-id="91b9f-187">If the application contains a standalone bot, then use the following code to add new properties to the Teams application manifest:</span></span>

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```
<span data-ttu-id="91b9f-188">Se o aplicativo contiver um bot e uma guia, use o código a seguir para adicionar novas propriedades ao manifesto do aplicativo Teams:</span><span class="sxs-lookup"><span data-stu-id="91b9f-188">If the application contains a bot and a tab, then use the following code to add new properties to the Teams application manifest:</span></span>

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

<span data-ttu-id="91b9f-189">**webApplicationInfo** é o pai dos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="91b9f-189">**webApplicationInfo** is the parent of the following elements:</span></span>

* <span data-ttu-id="91b9f-190">**id** - A ID do cliente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91b9f-190">**id** - The client ID of the application.</span></span> <span data-ttu-id="91b9f-191">Essa é a ID do aplicativo que você obteve como parte do registro do aplicativo no AAD.</span><span class="sxs-lookup"><span data-stu-id="91b9f-191">This is the application ID that you obtained as part of registering the application with AAD.</span></span>
* <span data-ttu-id="91b9f-192">**resource** - O domínio e o subdomínio do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91b9f-192">**resource** - The domain and subdomain of your application.</span></span> <span data-ttu-id="91b9f-193">Esse é o mesmo URI, incluindo o protocolo que você registrou ao criar seu aplicativo em Registrar seu aplicativo por meio `api://` `scope` do portal do [AAD.](#register-your-app-through-the-aad-portal)</span><span class="sxs-lookup"><span data-stu-id="91b9f-193">This is the same URI, including the `api://` protocol that you registered when creating your `scope` in [Register your app through the AAD portal](#register-your-app-through-the-aad-portal).</span></span> <span data-ttu-id="91b9f-194">Você não deve incluir `access_as_user` o caminho em seu recurso.</span><span class="sxs-lookup"><span data-stu-id="91b9f-194">You must not include the `access_as_user` path in your resource.</span></span> <span data-ttu-id="91b9f-195">A parte de domínio desse URI deve corresponder ao domínio e aos sub-domínios usados nas URLs do manifesto do aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="91b9f-195">The domain part of this URI must match the domain and subdomains used in the URLs of your Teams application manifest.</span></span>

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a><span data-ttu-id="91b9f-196">Adicionar o código para solicitar e receber um token de bot</span><span class="sxs-lookup"><span data-stu-id="91b9f-196">Add the code to request and receive a bot token</span></span>

#### <a name="request-a-bot-token"></a><span data-ttu-id="91b9f-197">Solicitar um token de bot</span><span class="sxs-lookup"><span data-stu-id="91b9f-197">Request a bot token</span></span>

<span data-ttu-id="91b9f-198">A solicitação para obter o token é uma solicitação de mensagem POST normal usando o esquema de mensagens existente.</span><span class="sxs-lookup"><span data-stu-id="91b9f-198">The request to get the token is a normal POST message request using the existing message schema.</span></span> <span data-ttu-id="91b9f-199">Ele está incluído nos anexos de um OAuthCard.</span><span class="sxs-lookup"><span data-stu-id="91b9f-199">It is included in the attachments of an OAuthCard.</span></span> <span data-ttu-id="91b9f-200">O esquema para a classe OAuthCard é definido no [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) e é semelhante a um cartão de login.</span><span class="sxs-lookup"><span data-stu-id="91b9f-200">The schema for the OAuthCard class is defined in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) and it is similar to a sign-in card.</span></span> <span data-ttu-id="91b9f-201">O Teams trata essa solicitação como uma aquisição de token silencioso `TokenExchangeResource` se a propriedade estiver preenchida no cartão.</span><span class="sxs-lookup"><span data-stu-id="91b9f-201">Teams treats this request as a silent token acquisition if the `TokenExchangeResource` property is populated on the card.</span></span> <span data-ttu-id="91b9f-202">Para o canal do Teams, apenas a propriedade, que `Id` identifica exclusivamente uma solicitação de token, é aumenteda.</span><span class="sxs-lookup"><span data-stu-id="91b9f-202">For the Teams channel, only the `Id` property, which uniquely identifies a token request, is honored.</span></span>

>[!NOTE]
> <span data-ttu-id="91b9f-203">O Microsoft Bot Framework ou o Microsoft Bot Framework `OAuthPrompt` `MultiProviderAuthDialog` tem suporte para autenticação SSO.</span><span class="sxs-lookup"><span data-stu-id="91b9f-203">The Microsoft Bot Framework `OAuthPrompt` or the `MultiProviderAuthDialog` is supported for SSO authentication.</span></span>

<span data-ttu-id="91b9f-204">Se o usuário estiver usando o aplicativo pela primeira vez e o consentimento do usuário for necessário, a caixa de diálogo a seguir parece continuar com a experiência de consentimento:</span><span class="sxs-lookup"><span data-stu-id="91b9f-204">If the user is using the application for the first time and user consent is required, the following dialog box appears to continue with the consent experience:</span></span>

![Caixa de diálogo consentimento](../../../assets/images/bots/bots-consent-dialogbox.png)

<span data-ttu-id="91b9f-206">Quando o usuário seleciona **Continuar,** ocorrem os seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="91b9f-206">When the user selects **Continue**, the following events occur:</span></span>

* <span data-ttu-id="91b9f-207">Se o bot definir um botão de logon, o fluxo de logon para bots será disparado de forma semelhante ao fluxo de logon de um botão de cartão OAuth em um fluxo de mensagens.</span><span class="sxs-lookup"><span data-stu-id="91b9f-207">If the bot defines a sign-in button, the sign in flow for bots is triggered similar to the sign in flow from an OAuth card button in a message stream.</span></span> <span data-ttu-id="91b9f-208">O desenvolvedor deve decidir quais permissões exigem o consentimento do usuário.</span><span class="sxs-lookup"><span data-stu-id="91b9f-208">The developer must decide which permissions require user's consent.</span></span> <span data-ttu-id="91b9f-209">Essa abordagem é recomendada se você exigir um token com permissões além `openId` .</span><span class="sxs-lookup"><span data-stu-id="91b9f-209">This approach is recommended if you require a token with permissions beyond `openId`.</span></span> <span data-ttu-id="91b9f-210">Por exemplo, se você quiser trocar o token por recursos gráficos.</span><span class="sxs-lookup"><span data-stu-id="91b9f-210">For example, if you want to exchange the token for graph resources.</span></span>

* <span data-ttu-id="91b9f-211">Se o bot não estiver fornecendo um botão de logon no cartão OAuth, o consentimento do usuário será necessário para um conjunto mínimo de permissões.</span><span class="sxs-lookup"><span data-stu-id="91b9f-211">If the bot is not providing a sign-in button on the OAuth card, user consent is required for a minimal set of permissions.</span></span> <span data-ttu-id="91b9f-212">Esse token é útil para autenticação básica e para obter o endereço de email do usuário.</span><span class="sxs-lookup"><span data-stu-id="91b9f-212">This token is useful for basic authentication and to get the user's email address.</span></span>

##### <a name="c-token-request-without-a-sign-in-button"></a><span data-ttu-id="91b9f-213">Solicitação de token C# sem um botão de logon</span><span class="sxs-lookup"><span data-stu-id="91b9f-213">C# token request without a sign-in button</span></span>

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

#### <a name="receive-the-bot-token"></a><span data-ttu-id="91b9f-214">Receber o token de bot</span><span class="sxs-lookup"><span data-stu-id="91b9f-214">Receive the bot token</span></span>

<span data-ttu-id="91b9f-215">A resposta com o token é enviada por meio de uma atividade de invocação com o mesmo esquema de outras atividades de invocação que os bots recebem hoje.</span><span class="sxs-lookup"><span data-stu-id="91b9f-215">The response with the token is sent through an invoke activity with the same schema as other invoke activities that the bots receive today.</span></span> <span data-ttu-id="91b9f-216">A única diferença é o nome de invocação, **o sign-in/tokenExchange** e o **campo de** valor.</span><span class="sxs-lookup"><span data-stu-id="91b9f-216">The only difference is the invoke name, **sign-in/tokenExchange** and the **value** field.</span></span> <span data-ttu-id="91b9f-217">O **campo** de valor contém a **Id**, uma cadeia de caracteres da solicitação inicial para obter o token e o campo **de token,** um valor de cadeia de caracteres incluindo o token.</span><span class="sxs-lookup"><span data-stu-id="91b9f-217">The **value** field contains the **Id**, a string of the initial request to get the token and the **token** field, a string value including the token.</span></span>

>[!NOTE]
> <span data-ttu-id="91b9f-218">Você pode receber várias respostas para uma determinada solicitação se o usuário tiver vários pontos de extremidade ativos.</span><span class="sxs-lookup"><span data-stu-id="91b9f-218">You might receive multiple responses for a given request if the user has multiple active endpoints.</span></span> <span data-ttu-id="91b9f-219">Você deve duplicar as respostas com o token.</span><span class="sxs-lookup"><span data-stu-id="91b9f-219">You must deduplicate the responses with the token.</span></span>

##### <a name="c-code-to-handle-the-invoke-activity"></a><span data-ttu-id="91b9f-220">Código C# para manipular a atividade de invocação</span><span class="sxs-lookup"><span data-stu-id="91b9f-220">C# code to handle the invoke activity</span></span>

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

<span data-ttu-id="91b9f-221">É `turnContext.activity.value` do tipo [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) e contém o token que pode ser usado ainda mais pelo seu bot.</span><span class="sxs-lookup"><span data-stu-id="91b9f-221">The `turnContext.activity.value` is of type [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) and contains the token that can be further used by your bot.</span></span> <span data-ttu-id="91b9f-222">Você deve armazenar os tokens por motivos de desempenho e atualize-os.</span><span class="sxs-lookup"><span data-stu-id="91b9f-222">You must store the tokens for performance reasons and refresh them.</span></span>

### <a name="update-the-auth-sample"></a><span data-ttu-id="91b9f-223">Atualizar o exemplo de auth</span><span class="sxs-lookup"><span data-stu-id="91b9f-223">Update the auth sample</span></span>

<span data-ttu-id="91b9f-224">Abra [o exemplo de auth do Teams](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) e conclua as seguintes etapas para atualizá-lo:</span><span class="sxs-lookup"><span data-stu-id="91b9f-224">Open [Teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) and then complete the following steps to update it:</span></span>

1. <span data-ttu-id="91b9f-225">Atualize o TeamsBot para manipular a dedudução da solicitação de entrada incluindo o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="91b9f-225">Update the TeamsBot to handle the deduping of the incoming request by including the following code:</span></span>

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
  
2. <span data-ttu-id="91b9f-226">Atualização para incluir o , senha e o nome de conexão definido em Atualizar o `appsettings.json` `botId` portal do [Azure com a conexão OAuth](#update-the-azure-portal-with-the-oauth-connection).</span><span class="sxs-lookup"><span data-stu-id="91b9f-226">Update `appsettings.json` to include the `botId`, password, and the connection name defined in [Update the Azure portal with the OAuth connection](#update-the-azure-portal-with-the-oauth-connection).</span></span>
3. <span data-ttu-id="91b9f-227">Atualize o manifesto e verifique `token.botframework.com` se ele está na lista de domínios válidos.</span><span class="sxs-lookup"><span data-stu-id="91b9f-227">Update the manifest and ensure that `token.botframework.com` is in the valid domains list.</span></span> <span data-ttu-id="91b9f-228">Para saber mais, confira [o exemplo de auth do Teams.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth)</span><span class="sxs-lookup"><span data-stu-id="91b9f-228">For more information, see [Teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span></span>
4. <span data-ttu-id="91b9f-229">Zip the manifest with the profile images and install it in Teams.</span><span class="sxs-lookup"><span data-stu-id="91b9f-229">Zip the manifest with the profile images and install it in Teams.</span></span>

#### <a name="additional-code-samples"></a><span data-ttu-id="91b9f-230">Exemplos de código adicionais</span><span class="sxs-lookup"><span data-stu-id="91b9f-230">Additional code samples</span></span>

* <span data-ttu-id="91b9f-231">[Exemplo de C# usando o SDK da Estrutura de Bot.](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore)</span><span class="sxs-lookup"><span data-stu-id="91b9f-231">[C# sample using the Bot Framework SDK](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore).</span></span>
