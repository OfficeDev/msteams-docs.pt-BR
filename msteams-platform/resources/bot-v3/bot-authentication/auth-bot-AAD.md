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
# <a name="authenticate-a-user-in-a-microsoft-teams-bot"></a>Autenticar um usuário em um bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Há muitos serviços que você pode desejar usar dentro do seu aplicativo do Microsoft Teams e a maioria desses serviços requer autenticação e autorização para obter acesso ao serviço. Os serviços incluem o Facebook, o Twitter e o Microsoft Teams. Os usuários de Teams têm informações de perfil de usuário armazenadas no Azure Active Directory (Azure AD) usando o Microsoft Graph. Este artigo se concentrará na autenticação usando o Azure AD para obter acesso a essas informações.

O OAuth 2,0 é um padrão aberto para autenticação usada pelo Azure AD e muitos outros provedores de serviços. A compreensão do OAuth 2,0 é um pré-requisito para trabalhar com autenticação no Teams e no Azure AD. Os exemplos abaixo usam o fluxo de concessão implícita do OAuth 2,0 com o objetivo de eventualmente ler as informações de perfil do usuário do Azure AD e do Microsoft Graph.

O fluxo de autenticação descrito neste artigo é muito semelhante ao das guias, exceto pelo fato de que as guias podem usar o fluxo de autenticação baseado na Web, e os bots exigem que a autenticação seja conduzida a partir do código. Os conceitos neste artigo também serão úteis na implementação da autenticação da plataforma móvel.

Para obter uma visão geral do fluxo de autenticação para bots, consulte o tópico [fluxo de autenticação em bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).

## <a name="configuring-identity-providers"></a>Configurando provedores de identidade

Consulte o tópico [Configure Identity Providers](~/concepts/authentication/configure-identity-provider.md) para obter etapas detalhadas sobre como configurar URLs de redirecionamento de retorno de chamada OAuth 2,0 ao usar o Azure Active Directory como um provedor de identidade.

## <a name="initiate-authentication-flow"></a>Iniciar o fluxo de autenticação

O fluxo de autenticação deve ser acionado por uma ação do usuário. Você não deve abrir o pop-up de autenticação automaticamente porque isso provavelmente disparará o bloqueador de pop-ups do navegador, além de confundir o usuário.

## <a name="add-ui-to-start-authentication"></a>Adicionar interface do usuário para iniciar a autenticação

Adicione interface do usuário ao bot para permitir que o usuário entre quando necessário. Isso é feito a partir de um cartão de miniatura, no TypeScript:

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

Três botões foram adicionados ao cartão herói: entrar, mostrar perfil e sair.

## <a name="sign-the-user-in"></a>Inscrever o usuário em

Por causa da validação que deve ser executada por motivos de segurança e o suporte para as versões móveis do Teams, o código não é mostrado aqui, mas [aqui está um exemplo de código que inicia o processo quando o usuário pressiona o botão entrar.](https://github.com/OfficeDev/microsoft-teams-sample-auth-node/blob/e84020562d7c8b83f4a357a4a4d91298c5d2989d/src/dialogs/BaseIdentityDialog.ts#L154-L195)..

A validação e o suporte móvel são explicados no [fluxo de autenticação do tópico em bots](~/resources/bot-v3/bot-authentication/auth-flow-bot.md).

Certifique-se de adicionar o domínio de sua URL de redirecionamento de autenticação à [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) seção do manifesto. Caso contrário, o pop-up de logon não será exibido.

## <a name="showing-user-profile-information"></a>Mostrando informações de perfil de usuário

Embora obter um token de acesso seja difícil devido a todas as transições de frente e para trás em diferentes sites e os problemas de segurança que devem ser resolvidos, quando você tiver um token, obter informações do Azure Active Directory é simples. O bot faz uma chamada para o `me` ponto de extremidade do gráfico com o token de acesso. O Graph responde com as informações do usuário para a pessoa que fez logon. As informações da resposta são usadas para criar um cartão de bot e enviados.

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

Se o usuário não estiver conectado, ele será solicitado a fazê-lo.

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

Para ver o código de exemplo que mostra o processo de autenticação do bot, confira:

* [Exemplo de autenticação de bot do Microsoft Teams](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
