---
title: Autenticação para bots usando o Azure Active Directory
description: Descreve a autenticação do Azure AD no Microsoft Teams e como usá-la em seus bots
keywords: AAD de bots de autenticação de equipes
ms.date: 03/01/2018
ms.openlocfilehash: 268af02c51b21b65214bce4673b54ac564a125ae
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672758"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-bot"></a><span data-ttu-id="79410-104">Autenticar um usuário em um bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="79410-104">Authenticate a user in a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="79410-105">Há muitos serviços que você pode desejar usar dentro do seu aplicativo do Microsoft Teams e a maioria desses serviços requer autenticação e autorização para obter acesso ao serviço.</span><span class="sxs-lookup"><span data-stu-id="79410-105">There are many services that you may wish to consume inside your Teams app, and most of those services require authentication and authorization to get access to the service.</span></span> <span data-ttu-id="79410-106">Os serviços incluem o Facebook, o Twitter e o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="79410-106">Services include Facebook, Twitter, and of course Teams.</span></span> <span data-ttu-id="79410-107">Os usuários de Teams têm informações de perfil de usuário armazenadas no Azure Active Directory (Azure AD) usando o Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="79410-107">Users of Teams have user profile information stored in Azure Active Directory (Azure AD) using Microsoft Graph.</span></span> <span data-ttu-id="79410-108">Este artigo se concentrará na autenticação usando o Azure AD para obter acesso a essas informações.</span><span class="sxs-lookup"><span data-stu-id="79410-108">This article will focus on authentication using Azure AD to get access to this information.</span></span>

<span data-ttu-id="79410-109">O OAuth 2,0 é um padrão aberto para autenticação usada pelo Azure AD e muitos outros provedores de serviços.</span><span class="sxs-lookup"><span data-stu-id="79410-109">OAuth 2.0 is an open standard for authentication used by Azure AD and many other service providers.</span></span> <span data-ttu-id="79410-110">A compreensão do OAuth 2,0 é um pré-requisito para trabalhar com autenticação no Teams e no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="79410-110">Understanding OAuth 2.0 is a prerequisite for working with authentication in Teams and Azure AD.</span></span> <span data-ttu-id="79410-111">Os exemplos abaixo usam o fluxo de concessão implícita do OAuth 2,0 com o objetivo de eventualmente ler as informações de perfil do usuário do Azure AD e do Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="79410-111">The examples below use the OAuth 2.0 Implicit Grant flow with the goal of eventually reading the user's profile information from Azure AD and Microsoft Graph.</span></span>

<span data-ttu-id="79410-112">O fluxo de autenticação descrito neste artigo é muito semelhante ao das guias, exceto pelo fato de que as guias podem usar o fluxo de autenticação baseado na Web, e os bots exigem que a autenticação seja conduzida a partir do código.</span><span class="sxs-lookup"><span data-stu-id="79410-112">The authentication flow described in this article is very similar to that of tabs except that tabs can use web based authentication flow, and bots require authentication to be driven from code.</span></span> <span data-ttu-id="79410-113">Os conceitos neste artigo também serão úteis na implementação da autenticação da plataforma móvel.</span><span class="sxs-lookup"><span data-stu-id="79410-113">The concepts in this article will also be useful when implementing authentication from the mobile platform.</span></span>

<span data-ttu-id="79410-114">Para obter uma visão geral do fluxo de autenticação para bots, consulte o tópico [fluxo de autenticação em bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="79410-114">For a general overview of authentication flow for bots see the topic [Authentication flow in bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).</span></span>

## <a name="configuring-identity-providers"></a><span data-ttu-id="79410-115">Configurando provedores de identidade</span><span class="sxs-lookup"><span data-stu-id="79410-115">Configuring identity providers</span></span>

<span data-ttu-id="79410-116">Consulte o tópico [Configure Identity Providers](~/concepts/authentication/configure-identity-provider.md) para obter etapas detalhadas sobre como configurar URLs de redirecionamento de retorno de chamada OAuth 2,0 ao usar o Azure Active Directory como um provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="79410-116">See the topic [Configure identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps on configuring OAuth 2.0 callback redirect URL(s) when using Azure Active Directory as an identity provider.</span></span>

## <a name="initiate-authentication-flow"></a><span data-ttu-id="79410-117">Iniciar o fluxo de autenticação</span><span class="sxs-lookup"><span data-stu-id="79410-117">Initiate authentication flow</span></span>

<span data-ttu-id="79410-118">O fluxo de autenticação deve ser acionado por uma ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="79410-118">Authentication flow should be triggered by a user action.</span></span> <span data-ttu-id="79410-119">Você não deve abrir o pop-up de autenticação automaticamente porque isso provavelmente disparará o bloqueador de pop-ups do navegador, além de confundir o usuário.</span><span class="sxs-lookup"><span data-stu-id="79410-119">You should not open the authentication pop-up automatically because this is likely to trigger the browser's pop-up blocker as well as confuse the user.</span></span>

## <a name="add-ui-to-start-authentication"></a><span data-ttu-id="79410-120">Adicionar interface do usuário para iniciar a autenticação</span><span class="sxs-lookup"><span data-stu-id="79410-120">Add UI to start authentication</span></span>

<span data-ttu-id="79410-121">Adicione interface do usuário ao bot para permitir que o usuário entre quando necessário.</span><span class="sxs-lookup"><span data-stu-id="79410-121">Add UI to the bot to enable the user to sign in when needed.</span></span> <span data-ttu-id="79410-122">Isso é feito a partir de um cartão de miniatura, no TypeScript:</span><span class="sxs-lookup"><span data-stu-id="79410-122">Here it is done from a Thumbnail card, in TypeScript:</span></span>

```typescript
// Show prompt of options
protected async promptForAction(session: builder.Session): Promise<void> {
    let msg = new builder.Message(session)
        .addAttachment(new builder.ThumbnailCard(session)
            .title(this.providerDisplayName)
            .buttons([
                 builder.CardAction.messageBack(session, "{}", "Sign in")
                     .text("SignIn")
                     .displayText("Sign in"),
                  builder.CardAction.messageBack(session, "{}", "Show profile")
                     .text("ShowProfile")
                     .displayText("Show profile"),
                  builder.CardAction.messageBack(session, "{}", "Sign out")
                     .text("SignOut")
                     .displayText("Sign out"),
            ]));
    session.send(msg);
}
```

<span data-ttu-id="79410-123">Três botões foram adicionados ao cartão herói: entrar, mostrar perfil e sair.</span><span class="sxs-lookup"><span data-stu-id="79410-123">Three buttons have been added to the Hero Card: Sign in, Show Profile, and Sign out.</span></span>

## <a name="sign-the-user-in"></a><span data-ttu-id="79410-124">Inscrever o usuário em</span><span class="sxs-lookup"><span data-stu-id="79410-124">Sign the user in</span></span>

<span data-ttu-id="79410-125">Por causa da validação que deve ser executada por motivos de segurança e o suporte para as versões móveis do Teams, o código não é mostrado aqui, mas [aqui está um exemplo de código que inicia o processo quando o usuário pressiona o botão entrar.](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/e84020562d7c8b83f4a357a4a4d91298c5d2989d/src/dialogs/BaseIdentityDialog.ts#L154-L195)..</span><span class="sxs-lookup"><span data-stu-id="79410-125">Because of the validation that must be performed for security reasons and the support for the mobile versions of Teams, the code isn't shown here, but [here's an example of the code that kicks off the process when the user presses the Sign in button.](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/e84020562d7c8b83f4a357a4a4d91298c5d2989d/src/dialogs/BaseIdentityDialog.ts#L154-L195).</span></span>

<span data-ttu-id="79410-126">A validação e o suporte móvel são explicados no [fluxo de autenticação do tópico em bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="79410-126">The validation and mobile support are explained in the topic [Authentication flow in bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).</span></span>

<span data-ttu-id="79410-127">Certifique-se de adicionar o domínio de sua URL de redirecionamento de autenticação à [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) seção do manifesto.</span><span class="sxs-lookup"><span data-stu-id="79410-127">Be sure to add the domain of your authentication redirect URL to the [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) section of the manifest.</span></span> <span data-ttu-id="79410-128">Caso contrário, o pop-up de logon não será exibido.</span><span class="sxs-lookup"><span data-stu-id="79410-128">If you don't, the login popup will not appear.</span></span>

## <a name="showing-user-profile-information"></a><span data-ttu-id="79410-129">Mostrando informações de perfil de usuário</span><span class="sxs-lookup"><span data-stu-id="79410-129">Showing user profile information</span></span>

<span data-ttu-id="79410-130">Embora obter um token de acesso seja difícil devido a todas as transições de frente e para trás em diferentes sites e os problemas de segurança que devem ser resolvidos, quando você tiver um token, obter informações do Azure Active Directory é simples.</span><span class="sxs-lookup"><span data-stu-id="79410-130">Although getting an access token is difficult because of all the transitions back and forth across different websites and the security issues that must be addressed, once you have a token, obtaining information from Azure Active Directory is straightforward.</span></span> <span data-ttu-id="79410-131">O bot faz uma chamada para o `me` ponto de extremidade do gráfico com o token de acesso.</span><span class="sxs-lookup"><span data-stu-id="79410-131">The bot makes a call to the `me` Graph endpoint with the access token.</span></span> <span data-ttu-id="79410-132">O Graph responde com as informações do usuário para a pessoa que fez logon.</span><span class="sxs-lookup"><span data-stu-id="79410-132">Graph responds with the user information for the person who logged in.</span></span> <span data-ttu-id="79410-133">As informações da resposta são usadas para criar um cartão de bot e enviados.</span><span class="sxs-lookup"><span data-stu-id="79410-133">Information from the response is used to construct a bot card and sent.</span></span>

```typescript
// Show user profile
protected async showUserProfile(session: builder.Session): Promise<void> {
    let azureADApi = this.authProvider as AzureADv1Provider;
    let userToken = this.getUserToken(session);

    if (userToken) {
        let profile = await azureADApi.getProfileAsync(userToken.accessToken);
        let profileCard = new builder.ThumbnailCard()
            .title(profile.displayName)
            .subtitle(profile.mail)
            .text(`${profile.jobTitle}<br/> ${profile.officeLocation}`);
        session.send(new builder.Message().addAttachment(profileCard));
    } else {
        session.send("Please sign in to AzureAD so I can access your profile.");
    }

    await this.promptForAction(session);
}

// Helper function to make the Graph API call
public async getProfileAsync(accessToken: string): Promise<any> {
    let options = {
        url: "https://graph.microsoft.com/v1.0/me",
        json: true,
        headers: {
            "Authorization": `Bearer ${accessToken}`,
        },
    };
    return await request.get(options);
}
```

<span data-ttu-id="79410-134">Se o usuário não estiver conectado, ele será solicitado a fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="79410-134">If the user is not signed in they are prompted to do so.</span></span>

## <a name="sign-the-user-out"></a><span data-ttu-id="79410-135">Cancelar a inscrição do usuário</span><span class="sxs-lookup"><span data-stu-id="79410-135">Sign the user out</span></span>

```typescript
// Handle user logout request
private async handleLogout(session: builder.Session): Promise<void> {
    if (!utils.getUserToken(session, this.providerName)) {
        session.send(`You're already signed out of ${this.providerDisplayName}.`);
    } else {
        utils.setUserToken(session, this.providerName, null);
        session.send(`You're now signed out of ${this.providerDisplayName}.`);
    }

    await this.promptForAction(session);
}
```

## <a name="other-samples"></a><span data-ttu-id="79410-136">Outros exemplos</span><span class="sxs-lookup"><span data-stu-id="79410-136">Other samples</span></span>

<span data-ttu-id="79410-137">Para ver o código de exemplo que mostra o processo de autenticação do bot, confira:</span><span class="sxs-lookup"><span data-stu-id="79410-137">For sample code showing the bot authentication process see:</span></span>

* [<span data-ttu-id="79410-138">Exemplo de autenticação de bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="79410-138">Microsoft Teams bot authentication sample</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
