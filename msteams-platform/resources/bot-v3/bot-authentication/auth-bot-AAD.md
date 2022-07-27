---
title: Autenticação para bots usando o Azure Active Directory
description: Descreve Azure AD autenticação no Teams e como usá-la em seus bots
keywords: bots de autenticação Azure AD
localization_priority: Normal
ms.topic: conceptual
ms.date: 03/01/2018
ms.openlocfilehash: 2b467f6a7b4678110dece3b54a67227df6beeaf7
ms.sourcegitcommit: 1cda2fd3498a76c09e31ed7fd88175414ad428f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2022
ms.locfileid: "67035160"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-bot"></a>Autenticar um usuário em um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Há muitos serviços que talvez você queira consumir dentro de seu aplicativo do Teams, e a maioria desses serviços exige autenticação e autorização para obter acesso. Os serviços incluem Facebook, Twitter e Teams. Os usuários no Teams têm informações de perfil de usuário armazenadas no Azure Active Directory usando o Microsoft Graph. Este tópico se concentra na autenticação usando Azure AD para obter acesso.
OAuth 2.0 é um padrão aberto para autenticação usado pelo Microsoft Azure AD e muitos outros provedores de serviços. Entender o OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams e no Microsoft Azure AD. Os exemplos a seguir usam o fluxo de Concessão Implícita do OAuth 2.0 para, eventualmente, ler as informações de perfil do usuário do Azure AD e do Microsoft Graph.

O fluxo de autenticação descrito neste tópico é semelhante às guias, exceto que as guias podem usar o fluxo de autenticação baseado na Web e os bots exigem que a autenticação seja controlada do código. Os conceitos neste tópico também serão úteis ao implementar a autenticação da plataforma móvel.

Para obter uma visão geral do fluxo de autenticação para bots, consulte o tópico [Fluxo de autenticação em bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).

## <a name="configuring-identity-providers"></a>Configurando provedores de identidade

Consulte o tópico Configurar provedores de identidade para obter etapas [detalhadas](~/concepts/authentication/configure-identity-provider.md) sobre como configurar URLs de redirecionamento de retorno de chamada do OAuth 2.0 ao usar o Azure Active Directory como um provedor de identidade.

## <a name="initiate-authentication-flow"></a>Iniciar o fluxo de autenticação

O fluxo de autenticação deve ser disparado por uma ação do usuário. Não abra o pop-up de autenticação automaticamente, pois ele pode disparar o bloqueador pop-up do navegador e confundir o usuário.

## <a name="add-ui-to-start-authentication"></a>Adicionar interface do usuário para iniciar a autenticação

Adicione a interface do usuário ao bot para permitir que o usuário entre quando necessário. Aqui, ele é feito de um cartão em miniatura, em TypeScript:

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

Três botões foram adicionados ao Cartão Hero: Entrar, Mostrar Perfil e Sair.

## <a name="sign-the-user-in"></a>Conectar o usuário

Devido à validação que deve ser executada por motivos de segurança e o suporte para as versões móveis do Teams, o código não é mostrado aqui, mas aqui está um exemplo do código que inicia o processo quando o usuário pressiona o botão Entrar [.](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/e84020562d7c8b83f4a357a4a4d91298c5d2989d/src/dialogs/BaseIdentityDialog.ts#L154-L195).

A validação e o suporte móvel são explicados no tópico Fluxo [de autenticação em bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).

Certifique-se de adicionar o domínio da URL de redirecionamento de autenticação à [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) seção do manifesto. Se você não entrar, o pop-up não aparecerá.

## <a name="showing-user-profile-information"></a>Mostrando informações de perfil do usuário

Embora a obtenção de um token de acesso seja difícil devido a todas as transições entre sites diferentes e os problemas de segurança que devem ser resolvidos, quando você tiver um token, a obtenção de informações do Azure Active Directory é simples. O bot faz uma chamada para o ponto `me` de extremidade do Graph com o token de acesso. O Graph responde com as informações do usuário para a pessoa que fez logon. As informações da resposta são usadas para construir um cartão de bot e enviadas.

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

Se o usuário não estiver conectado, ele será solicitado a fazer isso.

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

Para obter o código de exemplo mostrando o processo de autenticação de bot, consulte:

* [Exemplo de autenticação de bot do Microsoft Teams](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
