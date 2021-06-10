---
title: Autenticação para bots usando Azure Active Directory
description: Descreve a autenticação do Azure AD no Teams e como usá-la em seus bots
keywords: bots de autenticação do teams AAD
localization_priority: Normal
ms.topic: conceptual
ms.date: 03/01/2018
ms.openlocfilehash: c3f2f7fe3eb6b10faef2b24b3212081a881d6f8f
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020685"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-bot"></a>Autenticar um usuário em um Microsoft Teams bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Há muitos serviços que você pode querer consumir dentro do seu aplicativo Teams, e a maioria desses serviços exige autenticação e autorização para obter acesso ao serviço. Os serviços incluem Facebook, Twitter e, claro, Teams. Os usuários de Teams têm informações de perfil de usuário armazenadas no Azure Active Directory (Azure AD) usando o Microsoft Graph. Este artigo se concentrará na autenticação usando o Azure AD para obter acesso a essas informações.

OAuth 2.0 é um padrão aberto para autenticação usado pelo Azure AD e muitos outros provedores de serviços. Noções básicas sobre o OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams e no Azure AD. Os exemplos a seguir usam o fluxo de Concessão Implícita OAuth 2.0 com o objetivo de, eventualmente, ler as informações de perfil do usuário do Azure AD e do Microsoft Graph.

O fluxo de autenticação descrito neste artigo é muito semelhante ao das guias, exceto que as guias podem usar o fluxo de autenticação baseado na Web, e os bots exigem que a autenticação seja controlada do código. Os conceitos neste artigo também serão úteis ao implementar a autenticação da plataforma móvel.

Para uma visão geral do fluxo de autenticação para bots, consulte o tópico [Fluxo de autenticação em bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).

## <a name="configuring-identity-providers"></a>Configurando provedores de identidade

Consulte o tópico [Configure identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps on configuring OAuth 2.0 callback redirect URL(s) when using Azure Active Directory as an identity provider.

## <a name="initiate-authentication-flow"></a>Iniciar fluxo de autenticação

O fluxo de autenticação deve ser disparado por uma ação do usuário. Você não deve abrir o pop-up de autenticação automaticamente porque isso provavelmente disparará o bloqueador pop-up do navegador, bem como confundirá o usuário.

## <a name="add-ui-to-start-authentication"></a>Adicionar interface do usuário para iniciar a autenticação

Adicione a interface do usuário ao bot para permitir que o usuário entre quando necessário. Aqui, ele é feito a partir de um cartão Thumbnail, em TypeScript:

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

Três botões foram adicionados ao Cartão de Herói: Entrar, Mostrar Perfil e Sair.

## <a name="sign-the-user-in"></a>Entrar no usuário

Devido à validação que deve ser executada por motivos de segurança e o suporte para as versões móveis do Teams, o código não é mostrado aqui, mas aqui está um exemplo do código que inicia o processo quando o usuário pressiona o botão [Entrar.](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/e84020562d7c8b83f4a357a4a4d91298c5d2989d/src/dialogs/BaseIdentityDialog.ts#L154-L195).

A validação e o suporte móvel são explicados no tópico [Fluxo de autenticação em bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).

Certifique-se de adicionar o domínio da URL de redirecionamento de autenticação à [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) seção do manifesto. Caso não o faça, o pop-up de logon não aparecerá.

## <a name="showing-user-profile-information"></a>Mostrando informações de perfil de usuário

Embora a obtenção de um token de acesso seja difícil devido a todas as transições de ida e volta em diferentes sites e os problemas de segurança que devem ser resolvidos, depois de ter um token, obter informações do Azure Active Directory é simples. O bot faz uma chamada para o `me` ponto de extremidade Graph com o token de acesso. Graph responde com as informações do usuário para a pessoa que fez logor. As informações da resposta são usadas para construir um cartão de bot e enviadas.

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

Se o usuário não estiver assinado, ele será solicitado a fazer isso.

## <a name="sign-the-user-out"></a>Cancelar a inscrição do usuário

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

## <a name="other-samples"></a>Outros exemplos

Para um código de exemplo que mostra o processo de autenticação do bot, consulte:

* [Microsoft Teams exemplo de autenticação de bot](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
