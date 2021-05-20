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
# <a name="single-sign-on-sso-support-for-bots"></a><span data-ttu-id="20660-105">Suporte de login único (SSO) para bots</span><span class="sxs-lookup"><span data-stu-id="20660-105">Single sign-on (SSO) support for bots</span></span>

<span data-ttu-id="20660-106">A autenticação de logoi único em Azure Active Directory (AAD) minimiza o número de vezes que os usuários precisam inserir seu sinal em credenciais, atualizando silenciosamente o token de autenticação.</span><span class="sxs-lookup"><span data-stu-id="20660-106">Single sign-on authentication in Azure Active Directory (AAD) minimizes the number of times users need to enter their sign in credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="20660-107">Se os usuários concordarem em usar seu aplicativo, eles não precisam fornecer consentimento novamente em outro dispositivo e podem fazer login automaticamente.</span><span class="sxs-lookup"><span data-stu-id="20660-107">If users agree to use your app, they need not provide consent again on another device and can sign in automatically.</span></span> <span data-ttu-id="20660-108">O fluxo é semelhante ao do [suporte Microsoft Teams guia SSO,](../../../tabs/how-to/authentication/auth-aad-sso.md)no entanto, a diferença está no protocolo de como um bot [solicita tokens](#request-a-bot-token) e [recebe respostas](#receive-the-bot-token).</span><span class="sxs-lookup"><span data-stu-id="20660-108">The flow is similar to that of [Microsoft Teams tab SSO support](../../../tabs/how-to/authentication/auth-aad-sso.md), however, the difference is in the protocol for how a bot [requests tokens](#request-a-bot-token) and [receives responses](#receive-the-bot-token).</span></span>

>[!NOTE]
> <span data-ttu-id="20660-109">OAuth 2.0 é um padrão aberto para autenticação e autorização usado pela AAD e muitos outros provedores de identidade.</span><span class="sxs-lookup"><span data-stu-id="20660-109">OAuth 2.0 is an open standard for authentication and authorization used by AAD and many other identity providers.</span></span> <span data-ttu-id="20660-110">Um entendimento básico do OAuth 2.0 é um pré-requisito para trabalhar com autenticação em Teams.</span><span class="sxs-lookup"><span data-stu-id="20660-110">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

## <a name="bot-sso-at-runtime"></a><span data-ttu-id="20660-111">Bot SSO em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="20660-111">Bot SSO at runtime</span></span>

![Bot SSO no diagrama de tempo de execução](../../../assets/images/bots/bots-sso-diagram.png)

<span data-ttu-id="20660-113">Complete as seguintes etapas para obter a autenticação e os tokens de aplicativos de bot:</span><span class="sxs-lookup"><span data-stu-id="20660-113">Complete the following steps to get authentication and bot application tokens:</span></span>

1. <span data-ttu-id="20660-114">O bot envia uma mensagem com um OAuthCard que contém a `tokenExchangeResource` propriedade.</span><span class="sxs-lookup"><span data-stu-id="20660-114">The bot sends a message with an OAuthCard that contains the `tokenExchangeResource` property.</span></span> <span data-ttu-id="20660-115">Ele diz ao Teams para obter um token de autenticação para o aplicativo bot.</span><span class="sxs-lookup"><span data-stu-id="20660-115">It tells Teams to obtain an authentication token for the bot application.</span></span> <span data-ttu-id="20660-116">O usuário recebe mensagens em todos os pontos finais ativos do usuário.</span><span class="sxs-lookup"><span data-stu-id="20660-116">The user receives messages at all the active user endpoints.</span></span>

    > [!NOTE]
    >* <span data-ttu-id="20660-117">Um usuário pode ter mais de um ponto final ativo por vez.</span><span class="sxs-lookup"><span data-stu-id="20660-117">A user can have more than one active endpoint at a time.</span></span>
    >* <span data-ttu-id="20660-118">O token bot é recebido de todos os pontos finais ativos do usuário.</span><span class="sxs-lookup"><span data-stu-id="20660-118">The bot token is received from every active user endpoint.</span></span>
    >* <span data-ttu-id="20660-119">O aplicativo deve ser instalado em escopo pessoal para suporte ao SSO.</span><span class="sxs-lookup"><span data-stu-id="20660-119">The app must be installed in personal scope for SSO support.</span></span>

1. <span data-ttu-id="20660-120">Se o usuário atual estiver usando seu aplicativo de bot pela primeira vez, um prompt de solicitação será solicitado solicitando ao usuário que faça um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="20660-120">If the current user is using your bot application for the first time, a request prompt appears requesting the user to do one of the following:</span></span>
    * <span data-ttu-id="20660-121">Fornecer consentimento, se necessário.</span><span class="sxs-lookup"><span data-stu-id="20660-121">Provide consent, if required.</span></span>
    * <span data-ttu-id="20660-122">Manuseie a autenticação intensificada, como autenticação de dois fatores.</span><span class="sxs-lookup"><span data-stu-id="20660-122">Handle step-up authentication, such as two-factor authentication.</span></span>

1. <span data-ttu-id="20660-123">Teams solicita o token do aplicativo bot do ponto final AAD para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="20660-123">Teams requests the bot application token from the AAD endpoint for the current user.</span></span>

1. <span data-ttu-id="20660-124">AAD envia o token de aplicativo de bot para o aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="20660-124">AAD sends the bot application token to the Teams application.</span></span>

1. <span data-ttu-id="20660-125">Teams envia o token para o bot como parte do objeto de valor devolvido pela atividade de invocação com o nome **login/tokenExchange**.</span><span class="sxs-lookup"><span data-stu-id="20660-125">Teams sends the token to the bot as part of the value object returned by the invoke activity with the name **sign-in/tokenExchange**.</span></span>
  
1. <span data-ttu-id="20660-126">O token analisado no aplicativo bot fornece as informações necessárias, como o endereço de e-mail do usuário.</span><span class="sxs-lookup"><span data-stu-id="20660-126">The parsed token in the bot application provides the required information, such as the user's email address.</span></span>
  
## <a name="develop-an-sso-teams-bot"></a><span data-ttu-id="20660-127">Desenvolva um bot de Teams SSO</span><span class="sxs-lookup"><span data-stu-id="20660-127">Develop an SSO Teams bot</span></span>
  
<span data-ttu-id="20660-128">Complete as seguintes etapas para desenvolver um bot de Teams SSO:</span><span class="sxs-lookup"><span data-stu-id="20660-128">Complete the following steps to develop an SSO Teams bot:</span></span>

1. <span data-ttu-id="20660-129">[Cadastre seu aplicativo através do portal AAD](#register-your-app-through-the-aad-portal).</span><span class="sxs-lookup"><span data-stu-id="20660-129">[Register your app through the AAD portal](#register-your-app-through-the-aad-portal).</span></span>
1. <span data-ttu-id="20660-130">[Atualize seu manifesto de aplicativo Teams para o seu bot](#update-your-teams-application-manifest-for-your-bot).</span><span class="sxs-lookup"><span data-stu-id="20660-130">[Update your Teams application manifest for your bot](#update-your-teams-application-manifest-for-your-bot).</span></span>
1. <span data-ttu-id="20660-131">[Adicione o código para solicitar e receba um token de bot](#add-the-code-to-request-and-receive-a-bot-token).</span><span class="sxs-lookup"><span data-stu-id="20660-131">[Add the code to request and receive a bot token](#add-the-code-to-request-and-receive-a-bot-token).</span></span>

### <a name="register-your-app-through-the-aad-portal"></a><span data-ttu-id="20660-132">Cadastre seu aplicativo através do portal AAD</span><span class="sxs-lookup"><span data-stu-id="20660-132">Register your app through the AAD portal</span></span>

<span data-ttu-id="20660-133">As etapas para registrar seu aplicativo através do portal AAD são semelhantes ao [fluxo SSO](../../../tabs/how-to/authentication/auth-aad-sso.md)da guia .</span><span class="sxs-lookup"><span data-stu-id="20660-133">The steps to register your app through the AAD portal are similar to the [tab SSO flow](../../../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="20660-134">Complete as seguintes etapas para registrar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="20660-134">Complete the following steps to register your app:</span></span>

1. <span data-ttu-id="20660-135">Cadastre um novo aplicativo no [portal Azure Active Directory – App Registrations.](https://go.microsoft.com/fwlink/?linkid=2083908)</span><span class="sxs-lookup"><span data-stu-id="20660-135">Register a new application in the [Azure Active Directory – App Registrations](https://go.microsoft.com/fwlink/?linkid=2083908) portal.</span></span>
2. <span data-ttu-id="20660-136">Selecione **Novo Registro**.</span><span class="sxs-lookup"><span data-stu-id="20660-136">Select **New Registration**.</span></span> <span data-ttu-id="20660-137">A página **do registro de um aplicativo** é exibida.</span><span class="sxs-lookup"><span data-stu-id="20660-137">The **Register an application** page appears.</span></span>
3. <span data-ttu-id="20660-138">Na página **de registro de um aplicativo,** digite os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="20660-138">In the **Register an application** page, enter the following values:</span></span>
    1. <span data-ttu-id="20660-139">Digite um **nome** para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20660-139">Enter a **Name** for your app.</span></span>
    2. <span data-ttu-id="20660-140">Escolha os **tipos de conta suportada,** selecione o tipo de conta de inquilino único ou multitenente.</span><span class="sxs-lookup"><span data-stu-id="20660-140">Choose the **Supported account types**, select single tenant or multitenant account type.</span></span>

        > [!NOTE]
        >
        > <span data-ttu-id="20660-141">Os usuários não são solicitados a consentimento e recebem tokens de acesso imediatamente, se o aplicativo AAD estiver registrado no mesmo inquilino onde eles estão fazendo uma solicitação de autenticação em Teams.</span><span class="sxs-lookup"><span data-stu-id="20660-141">The users are not asked for consent and are granted access tokens right away, if the AAD app is registered in the same tenant where they are making an authentication request in Teams.</span></span> <span data-ttu-id="20660-142">No entanto, os usuários devem fornecer consentimento para as permissões, se o aplicativo AAD estiver registrado em um inquilino diferente.</span><span class="sxs-lookup"><span data-stu-id="20660-142">However, the users must provide consent to the permissions, if the AAD app is registered in a different tenant.</span></span>

    3. <span data-ttu-id="20660-143">Escolha **Registrar**.</span><span class="sxs-lookup"><span data-stu-id="20660-143">Choose **Register**.</span></span>
4. <span data-ttu-id="20660-144">Na página de visão geral, copie e salve o **ID do aplicativo (cliente).**</span><span class="sxs-lookup"><span data-stu-id="20660-144">On the overview page, copy and save the **Application (client) ID**.</span></span> <span data-ttu-id="20660-145">Você precisa dele mais tarde ao atualizar seu manifesto de solicitação de Teams.</span><span class="sxs-lookup"><span data-stu-id="20660-145">You need it later when updating your Teams application manifest.</span></span>
5. <span data-ttu-id="20660-146">Em **Gerenciar**, selecione **Expor uma API**.</span><span class="sxs-lookup"><span data-stu-id="20660-146">Under **Manage**, select **Expose an API**.</span></span> 

   > [!IMPORTANT]
    > * <span data-ttu-id="20660-147">Se você estiver construindo um bot autônomo, digite o ID URI de aplicativo como `api://botid-{YourBotId}` .</span><span class="sxs-lookup"><span data-stu-id="20660-147">If you are building a standalone bot, enter the Application ID URI as `api://botid-{YourBotId}`.</span></span> <span data-ttu-id="20660-148">Aqui **o YourBotId** é o seu ID de aplicação AAD.</span><span class="sxs-lookup"><span data-stu-id="20660-148">Here **YourBotId** is your AAD application ID.</span></span>
    > * <span data-ttu-id="20660-149">Se você estiver construindo um aplicativo com um bot e uma guia, digite o ID URI do aplicativo como `api://fully-qualified-domain-name.com/botid-{YourBotId}` .</span><span class="sxs-lookup"><span data-stu-id="20660-149">If you are building an app with a bot and a tab, enter the Application ID URI as `api://fully-qualified-domain-name.com/botid-{YourBotId}`.</span></span>

5. <span data-ttu-id="20660-150">Selecione as permissões que seu aplicativo precisa para o ponto final AAD e, opcionalmente, para a Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="20660-150">Select the permissions that your application needs for the AAD endpoint and, optionally, for Microsoft Graph.</span></span>
6. <span data-ttu-id="20660-151">[Conceder permissões](/azure/active-directory/develop/v2-permissions-and-consent) para Teams aplicativos de desktop, web e mobile.</span><span class="sxs-lookup"><span data-stu-id="20660-151">[Grant permissions](/azure/active-directory/develop/v2-permissions-and-consent) for Teams desktop, web, and mobile applications.</span></span>
7. <span data-ttu-id="20660-152">Selecione **Adicionar um escopo**.</span><span class="sxs-lookup"><span data-stu-id="20660-152">Select **Add a scope**.</span></span>
8. <span data-ttu-id="20660-153">No painel que abre, adicione um aplicativo cliente digitando `access_as_user` como o nome **Escopo**.</span><span class="sxs-lookup"><span data-stu-id="20660-153">In the panel that opens, add a client app by entering `access_as_user` as the **Scope name**.</span></span>

    >[!NOTE]
    > <span data-ttu-id="20660-154">O escopo "access_as_user" usado para adicionar um aplicativo ao cliente é para "Administradores e usuários".</span><span class="sxs-lookup"><span data-stu-id="20660-154">The "access_as_user" scope used to add a client app is for "Administrators and users".</span></span>
    >
    > <span data-ttu-id="20660-155">Você deve estar ciente das seguintes restrições importantes:</span><span class="sxs-lookup"><span data-stu-id="20660-155">You must be aware of the following important restrictions:</span></span>
    >
    > * <span data-ttu-id="20660-156">Apenas as permissões de API de nível de usuário da Microsoft Graph, como e-mail, perfil, offline_access e OpenId são suportadas.</span><span class="sxs-lookup"><span data-stu-id="20660-156">Only user-level Microsoft Graph API permissions, such as email, profile, offline_access, and OpenId are supported.</span></span> <span data-ttu-id="20660-157">Se você precisar de acesso a outros escopos Graph Microsoft, como `User.Read` ou , ver solução `Mail.Read` [recomendada](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-graph-scopes).</span><span class="sxs-lookup"><span data-stu-id="20660-157">If you need access to other Microsoft Graph scopes, such as `User.Read` or `Mail.Read`, see [recommended workaround](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-graph-scopes).</span></span>
    > * <span data-ttu-id="20660-158">O nome de domínio do seu aplicativo deve ser o mesmo que o nome de domínio que você registrou para o aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="20660-158">Your application's domain name must be same as the domain name that you have registered for your AAD application.</span></span>
    > * <span data-ttu-id="20660-159">Vários domínios por aplicativo não são suportados no momento.</span><span class="sxs-lookup"><span data-stu-id="20660-159">Multiple domains per app are currently not supported.</span></span>
    > * <span data-ttu-id="20660-160">Aplicativos que usam o `azurewebsites.net` domínio não são suportados porque é comum e pode ser um risco à segurança.</span><span class="sxs-lookup"><span data-stu-id="20660-160">Applications that use the `azurewebsites.net` domain are not supported because it is common and may be a security risk.</span></span>

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a><span data-ttu-id="20660-161">Atualize o portal Azure com a conexão OAuth</span><span class="sxs-lookup"><span data-stu-id="20660-161">Update the Azure portal with the OAuth connection</span></span>

<span data-ttu-id="20660-162">Complete as seguintes etapas para atualizar o portal Azure com a conexão OAuth:</span><span class="sxs-lookup"><span data-stu-id="20660-162">Complete the following steps to update the Azure portal with the OAuth connection:</span></span>

1. <span data-ttu-id="20660-163">No Portal Azure, navegue até **os registros do App.**</span><span class="sxs-lookup"><span data-stu-id="20660-163">In the Azure Portal, navigate to **App registrations**.</span></span>

2. <span data-ttu-id="20660-164">Vá para **permissões de API**.</span><span class="sxs-lookup"><span data-stu-id="20660-164">Go to **API Permissions**.</span></span> <span data-ttu-id="20660-165">Selecione **Adicionar uma permissão**  >  **que a Microsoft Graph** as  >  **permissões delegadas** e, em seguida, adicionar as seguintes permissões da API Graph Microsoft:</span><span class="sxs-lookup"><span data-stu-id="20660-165">Select **Add a permission** > **Microsoft Graph** > **Delegated permissions**, then add the following permissions from Microsoft Graph API:</span></span>
    * <span data-ttu-id="20660-166">User.Read (ativado por padrão)</span><span class="sxs-lookup"><span data-stu-id="20660-166">User.Read (enabled by default)</span></span>
    * <span data-ttu-id="20660-167">email</span><span class="sxs-lookup"><span data-stu-id="20660-167">email</span></span>
    * <span data-ttu-id="20660-168">offline_access</span><span class="sxs-lookup"><span data-stu-id="20660-168">offline_access</span></span>
    * <span data-ttu-id="20660-169">OpenId</span><span class="sxs-lookup"><span data-stu-id="20660-169">OpenId</span></span>
    * <span data-ttu-id="20660-170">perfil</span><span class="sxs-lookup"><span data-stu-id="20660-170">profile</span></span>

3. <span data-ttu-id="20660-171">No Portal Azure, navegue até o **Registro de Canais de Bot**.</span><span class="sxs-lookup"><span data-stu-id="20660-171">In the Azure Portal, navigate to **Bot Channels Registration**.</span></span>

4. <span data-ttu-id="20660-172">Selecione **Configurações** no painel esquerdo e escolha **Adicionar configuração** na seção **Configurações conexão OAuth.**</span><span class="sxs-lookup"><span data-stu-id="20660-172">Select **Settings** on the left pane and choose **Add Setting** under the **OAuth Connection Settings** section.</span></span>

    ![Exibição SSOBotHandle2](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

5. <span data-ttu-id="20660-174">Execute as seguintes etapas para completar o **formulário Configuração da nova conexão:**</span><span class="sxs-lookup"><span data-stu-id="20660-174">Perform the following steps to complete the **New Connection Setting** form:</span></span>

    >[!NOTE]
    > <span data-ttu-id="20660-175">**A concessão implícita** pode ser necessária na aplicação AAD.</span><span class="sxs-lookup"><span data-stu-id="20660-175">**Implicit grant** may be required in the AAD application.</span></span>

    1. <span data-ttu-id="20660-176">Digite um **nome** na página Configuração de **nova conexão.**</span><span class="sxs-lookup"><span data-stu-id="20660-176">Enter a **Name** in the **New Connection Setting** page.</span></span> <span data-ttu-id="20660-177">Este é o nome que é referido dentro das configurações do seu código de serviço bot na *etapa 5* do [Bot SSO no tempo de execução](#bot-sso-at-runtime).</span><span class="sxs-lookup"><span data-stu-id="20660-177">This is the name that is referred to inside the settings of your bot service code in *step 5* of [Bot SSO at runtime](#bot-sso-at-runtime).</span></span>
    2. <span data-ttu-id="20660-178">Na entrega do Provedor de **Serviços,** selecione **Azure Active Directory v2**.</span><span class="sxs-lookup"><span data-stu-id="20660-178">From the **Service Provider** drop-down, select **Azure Active Directory v2**.</span></span>
    3. <span data-ttu-id="20660-179">Digite as credenciais do cliente, como **o cliente e** o segredo do **cliente** para o aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="20660-179">Enter the client credentials, such as **Client id** and **Client secret** for the AAD application.</span></span>
    4. <span data-ttu-id="20660-180">Para o **Token Exchange URL,** use o valor do escopo definido em [Atualizar seu manifesto de aplicativo Teams para o seu bot](#update-your-teams-application-manifest-for-your-bot).</span><span class="sxs-lookup"><span data-stu-id="20660-180">For the **Token Exchange URL**, use the scope value defined in [Update your Teams application manifest for your bot](#update-your-teams-application-manifest-for-your-bot).</span></span> <span data-ttu-id="20660-181">A URL de token Exchange indica ao SDK que este aplicativo AAD está configurado para SSO.</span><span class="sxs-lookup"><span data-stu-id="20660-181">The Token Exchange URL indicates to the SDK that this AAD application is configured for SSO.</span></span>
    5. <span data-ttu-id="20660-182">Na caixa **de ID do Inquilino,** digite *comum.*</span><span class="sxs-lookup"><span data-stu-id="20660-182">In the **Tenant ID** box, enter *common*.</span></span>
    6. <span data-ttu-id="20660-183">Adicione todos os **Escopos** configurados ao especificar permissões às APIs a jusante para o aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="20660-183">Add all the **Scopes** configured when specifying permissions to downstream APIs for your AAD application.</span></span> <span data-ttu-id="20660-184">Com a identidade do cliente e o segredo do cliente fornecidas, a loja de tokens troca o token por um token gráfico com permissões definidas.</span><span class="sxs-lookup"><span data-stu-id="20660-184">With the Client id and Client secret provided, the token store exchanges the token for a graph token with defined permissions.</span></span>
    7. <span data-ttu-id="20660-185">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="20660-185">Select **Save**.</span></span>

    ![Visualização de configuração vussobotconnection](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a><span data-ttu-id="20660-187">Atualize seu manifesto de aplicativo de Teams para o seu bot</span><span class="sxs-lookup"><span data-stu-id="20660-187">Update your Teams application manifest for your bot</span></span>

<span data-ttu-id="20660-188">Se o aplicativo contiver um bot autônomo, use o seguinte código para adicionar novas propriedades ao manifesto de Teams aplicativo:</span><span class="sxs-lookup"><span data-stu-id="20660-188">If the application contains a standalone bot, then use the following code to add new properties to the Teams application manifest:</span></span>

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```
<span data-ttu-id="20660-189">Se o aplicativo contiver um bot e uma guia, use o seguinte código para adicionar novas propriedades ao manifesto de Teams aplicativo:</span><span class="sxs-lookup"><span data-stu-id="20660-189">If the application contains a bot and a tab, then use the following code to add new properties to the Teams application manifest:</span></span>

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

<span data-ttu-id="20660-190">**webApplicationInfo** é o pai dos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="20660-190">**webApplicationInfo** is the parent of the following elements:</span></span>

* <span data-ttu-id="20660-191">**id** - O ID do cliente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20660-191">**id** - The client ID of the application.</span></span> <span data-ttu-id="20660-192">Este é o ID de aplicação que você obteve como parte do registro do aplicativo com AAD.</span><span class="sxs-lookup"><span data-stu-id="20660-192">This is the application ID that you obtained as part of registering the application with AAD.</span></span>
* <span data-ttu-id="20660-193">**recurso** - O domínio e o subdomínio do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20660-193">**resource** - The domain and subdomain of your application.</span></span> <span data-ttu-id="20660-194">Este é o mesmo URI, incluindo o `api://` protocolo que você registrou ao criar o seu in `scope` [Registre seu aplicativo através do portal AAD](#register-your-app-through-the-aad-portal).</span><span class="sxs-lookup"><span data-stu-id="20660-194">This is the same URI, including the `api://` protocol that you registered when creating your `scope` in [Register your app through the AAD portal](#register-your-app-through-the-aad-portal).</span></span> <span data-ttu-id="20660-195">Você não deve incluir o `access_as_user` caminho em seu recurso.</span><span class="sxs-lookup"><span data-stu-id="20660-195">You must not include the `access_as_user` path in your resource.</span></span> <span data-ttu-id="20660-196">A parte de domínio deste URI deve corresponder ao domínio e subdomínios usados nos URLs do seu manifesto de aplicação Teams.</span><span class="sxs-lookup"><span data-stu-id="20660-196">The domain part of this URI must match the domain and subdomains used in the URLs of your Teams application manifest.</span></span>

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a><span data-ttu-id="20660-197">Adicione o código para solicitar e receba um token de bot</span><span class="sxs-lookup"><span data-stu-id="20660-197">Add the code to request and receive a bot token</span></span>

#### <a name="request-a-bot-token"></a><span data-ttu-id="20660-198">Solicite um token de bot</span><span class="sxs-lookup"><span data-stu-id="20660-198">Request a bot token</span></span>

<span data-ttu-id="20660-199">A solicitação para obter o token é uma solicitação normal de mensagem POST usando o esquema de mensagem existente.</span><span class="sxs-lookup"><span data-stu-id="20660-199">The request to get the token is a normal POST message request using the existing message schema.</span></span> <span data-ttu-id="20660-200">Está incluído nos anexos de um OAuthCard.</span><span class="sxs-lookup"><span data-stu-id="20660-200">It is included in the attachments of an OAuthCard.</span></span> <span data-ttu-id="20660-201">O esquema para a classe OAuthCard é definido no [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) e é semelhante a um cartão de login.</span><span class="sxs-lookup"><span data-stu-id="20660-201">The schema for the OAuthCard class is defined in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) and it is similar to a sign-in card.</span></span> <span data-ttu-id="20660-202">Teams trata esse pedido como uma aquisição silenciosa de token se a `TokenExchangeResource` propriedade estiver preenchida no cartão.</span><span class="sxs-lookup"><span data-stu-id="20660-202">Teams treats this request as a silent token acquisition if the `TokenExchangeResource` property is populated on the card.</span></span> <span data-ttu-id="20660-203">Para o canal Teams, apenas a `Id` propriedade, que identifica exclusivamente um pedido de token, é honrada.</span><span class="sxs-lookup"><span data-stu-id="20660-203">For the Teams channel, only the `Id` property, which uniquely identifies a token request, is honored.</span></span>

>[!NOTE]
> <span data-ttu-id="20660-204">O Microsoft Bot Framework `OAuthPrompt` ou o suporte para `MultiProviderAuthDialog` autenticação SSO.</span><span class="sxs-lookup"><span data-stu-id="20660-204">The Microsoft Bot Framework `OAuthPrompt` or the `MultiProviderAuthDialog` is supported for SSO authentication.</span></span>

<span data-ttu-id="20660-205">Se o usuário estiver usando o aplicativo pela primeira vez e o consentimento do usuário for necessário, a seguinte caixa de diálogo aparecerá para continuar com a experiência de consentimento:</span><span class="sxs-lookup"><span data-stu-id="20660-205">If the user is using the application for the first time and user consent is required, the following dialog box appears to continue with the consent experience:</span></span>

![Caixa de diálogo de consentimento](../../../assets/images/bots/bots-consent-dialogbox.png)

<span data-ttu-id="20660-207">Quando o usuário seleciona **Continuar,** ocorrem os seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="20660-207">When the user selects **Continue**, the following events occur:</span></span>

* <span data-ttu-id="20660-208">Se o bot definir um botão de login, o fluxo de sinal para bots será acionado semelhante ao fluxo de sinal de um botão de cartão OAuth em um fluxo de mensagens.</span><span class="sxs-lookup"><span data-stu-id="20660-208">If the bot defines a sign-in button, the sign in flow for bots is triggered similar to the sign in flow from an OAuth card button in a message stream.</span></span> <span data-ttu-id="20660-209">O desenvolvedor deve decidir quais permissões requerem o consentimento do usuário.</span><span class="sxs-lookup"><span data-stu-id="20660-209">The developer must decide which permissions require user's consent.</span></span> <span data-ttu-id="20660-210">Esta abordagem é recomendada se você precisar de um token com permissões além `openId` .</span><span class="sxs-lookup"><span data-stu-id="20660-210">This approach is recommended if you require a token with permissions beyond `openId`.</span></span> <span data-ttu-id="20660-211">Por exemplo, se você quiser trocar o token por recursos gráficos.</span><span class="sxs-lookup"><span data-stu-id="20660-211">For example, if you want to exchange the token for graph resources.</span></span>

* <span data-ttu-id="20660-212">Se o bot não estiver fornecendo um botão de login no cartão OAuth, o consentimento do usuário será necessário para um conjunto mínimo de permissões.</span><span class="sxs-lookup"><span data-stu-id="20660-212">If the bot is not providing a sign-in button on the OAuth card, user consent is required for a minimal set of permissions.</span></span> <span data-ttu-id="20660-213">Este token é útil para autenticação básica e para obter o endereço de e-mail do usuário.</span><span class="sxs-lookup"><span data-stu-id="20660-213">This token is useful for basic authentication and to get the user's email address.</span></span>

##### <a name="c-token-request-without-a-sign-in-button"></a><span data-ttu-id="20660-214">Solicitação de token C# sem um botão de login</span><span class="sxs-lookup"><span data-stu-id="20660-214">C# token request without a sign-in button</span></span>

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

#### <a name="receive-the-bot-token"></a><span data-ttu-id="20660-215">Receba o token de bot</span><span class="sxs-lookup"><span data-stu-id="20660-215">Receive the bot token</span></span>

<span data-ttu-id="20660-216">A resposta com o token é enviada através de uma atividade de invocação com o mesmo esquema que outras atividades de invocação que os bots recebem hoje.</span><span class="sxs-lookup"><span data-stu-id="20660-216">The response with the token is sent through an invoke activity with the same schema as other invoke activities that the bots receive today.</span></span> <span data-ttu-id="20660-217">A única diferença é o nome de invocação, **o login/tokenExchange** e o campo **de valor.**</span><span class="sxs-lookup"><span data-stu-id="20660-217">The only difference is the invoke name, **sign-in/tokenExchange** and the **value** field.</span></span> <span data-ttu-id="20660-218">O campo **de valor** contém o **ID**, uma sequência da solicitação inicial para obter o token e o campo **de token,** um valor de sequência incluindo o token.</span><span class="sxs-lookup"><span data-stu-id="20660-218">The **value** field contains the **Id**, a string of the initial request to get the token and the **token** field, a string value including the token.</span></span>

>[!NOTE]
> <span data-ttu-id="20660-219">Você pode receber várias respostas para uma determinada solicitação se o usuário tiver vários pontos finais ativos.</span><span class="sxs-lookup"><span data-stu-id="20660-219">You might receive multiple responses for a given request if the user has multiple active endpoints.</span></span> <span data-ttu-id="20660-220">Você deve deduplicar as respostas com o token.</span><span class="sxs-lookup"><span data-stu-id="20660-220">You must deduplicate the responses with the token.</span></span>

##### <a name="c-code-to-handle-the-invoke-activity"></a><span data-ttu-id="20660-221">Código C# para lidar com a atividade de invocação</span><span class="sxs-lookup"><span data-stu-id="20660-221">C# code to handle the invoke activity</span></span>

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

<span data-ttu-id="20660-222">O `turnContext.activity.value` é do tipo [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) e contém o token que pode ser usado ainda mais pelo seu bot.</span><span class="sxs-lookup"><span data-stu-id="20660-222">The `turnContext.activity.value` is of type [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) and contains the token that can be further used by your bot.</span></span> <span data-ttu-id="20660-223">Você deve armazenar os tokens por razões de desempenho e atualizá-los.</span><span class="sxs-lookup"><span data-stu-id="20660-223">You must store the tokens for performance reasons and refresh them.</span></span>

### <a name="token-exchange-failure"></a><span data-ttu-id="20660-224">Falha na troca de tokens</span><span class="sxs-lookup"><span data-stu-id="20660-224">Token exchange failure</span></span>

<span data-ttu-id="20660-225">Em caso de falha na troca de tokens, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="20660-225">In case of token exchange failure, use the following code:</span></span>

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

<span data-ttu-id="20660-226">Para entender o que o bot faz quando a exchange de token não aciona um prompt de consentimento, consulte as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="20660-226">To understand what the bot does when the token exchange fails to trigger a consent prompt, see the following steps:</span></span>

>[!NOTE]
> <span data-ttu-id="20660-227">Nenhuma ação do usuário é necessária para ser tomada à medida que o bot toma as ações quando a troca de tokens falha.</span><span class="sxs-lookup"><span data-stu-id="20660-227">No user action is required to be taken as the bot takes the actions when the token exchange fails.</span></span>

1. <span data-ttu-id="20660-228">O cliente inicia uma conversa com o bot desencadeando um cenário OAuth.</span><span class="sxs-lookup"><span data-stu-id="20660-228">The client starts a conversation with the bot triggering an OAuth scenario.</span></span>
2. <span data-ttu-id="20660-229">O bot envia um cartão OAuth para o cliente.</span><span class="sxs-lookup"><span data-stu-id="20660-229">The bot sends back an OAuth card to the client.</span></span>
3. <span data-ttu-id="20660-230">O cliente intercepta o cartão OAuth antes de exibi-lo ao usuário e verifica se ele contém uma `TokenExchangeResource` propriedade.</span><span class="sxs-lookup"><span data-stu-id="20660-230">The client intercepts the OAuth card before displaying it to the user and checks if it contains a `TokenExchangeResource` property.</span></span>
4. <span data-ttu-id="20660-231">Se a propriedade existir, o cliente envia um `TokenExchangeInvokeRequest` para o bot.</span><span class="sxs-lookup"><span data-stu-id="20660-231">If the property exists, the client sends a `TokenExchangeInvokeRequest` to the bot.</span></span> <span data-ttu-id="20660-232">O cliente deve ter um token comercializável para o usuário, que deve ser um token Azure AD v2 e cujo público deve ser o mesmo que `TokenExchangeResource.Uri` propriedade.</span><span class="sxs-lookup"><span data-stu-id="20660-232">The client must have an exchangeable token for the user, which must be an Azure AD v2 token and whose audience must be the same as `TokenExchangeResource.Uri` property.</span></span> <span data-ttu-id="20660-233">O cliente envia uma atividade de invocação para o bot com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="20660-233">The client sends an invoke activity to the bot with the following code:</span></span>

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

5. <span data-ttu-id="20660-234">O bot processa o `TokenExchangeInvokeRequest` e retorna de volta ao `TokenExchangeInvokeResponse` cliente.</span><span class="sxs-lookup"><span data-stu-id="20660-234">The bot processes the `TokenExchangeInvokeRequest` and returns a `TokenExchangeInvokeResponse` back to the client.</span></span> <span data-ttu-id="20660-235">O cliente deve esperar até receber o `TokenExchangeInvokeResponse` .</span><span class="sxs-lookup"><span data-stu-id="20660-235">The client must wait till it receives the `TokenExchangeInvokeResponse`.</span></span>

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

6. <span data-ttu-id="20660-236">Se o `TokenExchangeInvokeResponse` tem um de , então o cliente não mostra o cartão `status` `200` OAuth.</span><span class="sxs-lookup"><span data-stu-id="20660-236">If the `TokenExchangeInvokeResponse` has a `status` of `200`, then the client does not show the OAuth card.</span></span> <span data-ttu-id="20660-237">Veja a [imagem de fluxo normal](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="20660-237">See the [normal flow image](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true).</span></span> <span data-ttu-id="20660-238">Para qualquer outro `status` ou se o não for `TokenExchangeInvokeResponse` recebido, então o cliente mostra o cartão OAuth ao usuário.</span><span class="sxs-lookup"><span data-stu-id="20660-238">For any other `status` or if the `TokenExchangeInvokeResponse` is not received, then the client shows the OAuth card to the user.</span></span> <span data-ttu-id="20660-239">Veja a imagem de [fluxo de recuo](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="20660-239">See the [fallback flow image](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true).</span></span> <span data-ttu-id="20660-240">Isso garante que o fluxo SSO volte ao fluxo normal do OAuthCard em caso de erros ou dependências não atendidas, como o consentimento do usuário.</span><span class="sxs-lookup"><span data-stu-id="20660-240">This ensures that the SSO flow falls back to normal OAuthCard flow in case of any errors or unmet dependencies like user consent.</span></span>


### <a name="update-the-auth-sample"></a><span data-ttu-id="20660-241">Atualize a amostra de auth</span><span class="sxs-lookup"><span data-stu-id="20660-241">Update the auth sample</span></span>

<span data-ttu-id="20660-242">Abra Teams amostra de [auth](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) e, em seguida, complete as seguintes etapas para atualizá-la:</span><span class="sxs-lookup"><span data-stu-id="20660-242">Open [Teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) and then complete the following steps to update it:</span></span>

1. <span data-ttu-id="20660-243">Atualize o TeamsBot para lidar com a deduping da solicitação recebida, incluindo o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="20660-243">Update the TeamsBot to handle the deduping of the incoming request by including the following code:</span></span>

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
  
2. <span data-ttu-id="20660-244">Atualização `appsettings.json` para incluir a senha e o nome de `botId` conexão definido no Update the [Azure portal com a conexão OAuth](#update-the-azure-portal-with-the-oauth-connection).</span><span class="sxs-lookup"><span data-stu-id="20660-244">Update `appsettings.json` to include the `botId`, password, and the connection name defined in [Update the Azure portal with the OAuth connection](#update-the-azure-portal-with-the-oauth-connection).</span></span>
3. <span data-ttu-id="20660-245">Atualize o manifesto e certifique-se de que `token.botframework.com` está na lista de domínios válidos.</span><span class="sxs-lookup"><span data-stu-id="20660-245">Update the manifest and ensure that `token.botframework.com` is in the valid domains list.</span></span> <span data-ttu-id="20660-246">Para obter mais informações, consulte [Teams amostra de auth](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span><span class="sxs-lookup"><span data-stu-id="20660-246">For more information, see [Teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span></span>
4. <span data-ttu-id="20660-247">Feche o manifesto com as imagens do perfil e instale-o em Teams.</span><span class="sxs-lookup"><span data-stu-id="20660-247">Zip the manifest with the profile images and install it in Teams.</span></span>

## <a name="code-sample"></a><span data-ttu-id="20660-248">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="20660-248">Code sample</span></span>
|<span data-ttu-id="20660-249">**Nome da amostra**</span><span class="sxs-lookup"><span data-stu-id="20660-249">**Sample name**</span></span> | <span data-ttu-id="20660-250">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="20660-250">**Description**</span></span> |<span data-ttu-id="20660-251">**.NET**</span><span class="sxs-lookup"><span data-stu-id="20660-251">**.NET**</span></span> | 
|----------------|-----------------|--------------|
|<span data-ttu-id="20660-252">Estrutura de bot SDK</span><span class="sxs-lookup"><span data-stu-id="20660-252">Bot framework SDK</span></span> | <span data-ttu-id="20660-253">Amostra para usar a estrutura do bot SDK.</span><span class="sxs-lookup"><span data-stu-id="20660-253">Sample for using the bot framework SDK.</span></span> |[<span data-ttu-id="20660-254">View</span><span class="sxs-lookup"><span data-stu-id="20660-254">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore)|
