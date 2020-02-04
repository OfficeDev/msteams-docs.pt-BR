---
title: Usando o serviço de bot do Azure para autenticação no Microsoft Teams
description: Descreve o serviço do Azure bot OAuthCard e como ele é usado para autenticação
keywords: OAuthCard de autenticação do Microsoft Teams serviço de bot do Azure de cartões OAuth
ms.openlocfilehash: 0397c45b39470d97c1158b2681462038de618a39
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672759"
---
# <a name="using-azure-bot-service-for-authentication-in-teams"></a>Usando o serviço de bot do Azure para autenticação no Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sem o OAuthCard do serviço de bot do Azure, é complicado implementar a autenticação em um bot. É um desafio de pilha total que envolve a criação de uma experiência da Web, a integração com provedores OAuth externos, o gerenciamento de tokens e a manipulação das chamadas de API de servidor para servidor certas para concluir o fluxo de autenticação com segurança. Isso pode resultar em experiências do clunky que exijam a entrada de "números mágicos".

Com o OAuthCard do serviço do Azure bot, é mais fácil para o bot do Microsoft Teams assinar seus usuários e acessar provedores de dados externos. Se você já implementou a autenticação e deseja alternar para algo mais simples, ou se você está procurando adicionar autenticação ao serviço de bot pela primeira vez, o OAuthCard pode facilitar.

Outros tópicos da [autenticação](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) descrevem a autenticação sem usar o OAuthCard, portanto, se você quiser entender a autenticação no Microsoft Teams mais profundamente ou se tiver uma situação em que não possa usar o OAuthCard, ainda poderá fazer referência a esses tópicos.

## <a name="support-for-the-oauthcard"></a>Suporte para o OAuthCard

No momento, há algumas restrições para onde você pode usar o OAuthCard. Entre elas:

* O cartão não funcionará com [acesso de convidado](/MicrosoftTeams/guest-access)
* Ele não funcionará com [o Microsoft Teams gratuitamente](https://products.office.com/microsoft-teams/free)
* Ele só pode ser usado para a autenticação de bot
* Ele funciona apenas para bots registrados no [serviço do Azure bot](https://azure.microsoft.com/services/bot-service/)

## <a name="how-does-the-azure-bot-service-help-me-do-authentication"></a>Como o serviço do Azure bot ajuda a fazer a autenticação?

A documentação completa usando o OAuthCard está disponível no tópico: [Adicionar autenticação ao bot por meio do serviço de bot do Azure](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0). Observe que este tópico está no conjunto de documentação do Azure bot Framework e não é específico para o Teams.

As seções a seguir explicam como usar o OAuthCard no Microsoft Teams.

## <a name="main-benefits-for-teams-developers"></a>Principais benefícios para desenvolvedores de equipes

O OAuthCard ajuda com a autenticação das seguintes maneiras:

* Fornece um fluxo de autenticação sem uso baseado na Web: você não precisa mais escrever e hospedar uma página da Web para direcionar as experiências de login externas ou fornecer um redirecionamento.
* O é perfeito para usuários finais: conclua a experiência de entrada completa no Teams.
* Inclui o gerenciamento fácil de tokens: você não precisa mais implementar um sistema de armazenamento de token – em vez disso, o serviço bot cuida do cache de token e fornece um mecanismo seguro para buscar esses tokens.
* O é suportado por SDKs completos: fácil de integrar e consumir do serviço de bot.
* Tem suporte pronto para vários provedores OAuth populares, como o Azure AD/MSA, Facebook e Google.

## <a name="when-should-i-implement-my-own-solution"></a>Quando devo implementar minha própria solução?

Como os tokens de acesso são informações confidenciais, talvez você não queira armazená-los em um serviço externo. Nesse caso, você pode optar por ainda implementar seu próprio sistema de gerenciamento de tokens e a experiência de logon no Teams, conforme descrito no restante dos tópicos de [autenticação](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) do Microsoft Teams.

## <a name="getting-started-with-oauthcard-in-teams"></a>Introdução ao OAuthCard no Microsoft Teams

> [!NOTE]
> Este guia está usando o SDK da estrutura de bot v3. Você pode encontrar a implementação v4 [aqui](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp). Você ainda precisará criar um manifesto e incluir token.botframework.com na `validDomains` seção, pois, caso contrário, o botão entrar não abrirá a janela de autenticação. Use o [app Studio](~/concepts/build-and-test/app-studio-overview.md) para gerar seu manifesto.

Primeiro, você precisará configurar o serviço do Azure bot para configurar os provedores de autenticação externa. Leia [Configuring Identity Providers](~/concepts/authentication/configure-identity-provider.md) for detailed etapas.

Para habilitar a autenticação usando o serviço do Azure bot, você precisará fazer essas inclusões no seu código:

1. Inclua token.botframework.com na `validDomains` seção do manifesto do aplicativo, pois o Teams incorporará a página de logon do serviço de bot.
2. Busque o token do serviço bot sempre que seu bot precisar acessar os recursos autenticados. Se nenhum token estiver disponível, envie uma mensagem com um OAuthCard para que o usuário solicite o logon no serviço externo.
3. Manipular a atividade de conclusão de logon. Isso garante que a solicitação de autenticação e o token estejam associados ao usuário que está interagindo atualmente com seu bot.
4. Recupere o token sempre que o bot precisar executar ações autenticadas, como chamar APIs REST externas.

No seu código de caixa de diálogo, você precisará adicionar este trecho de código (C#), que verifica um token de acesso existente:

```CSharp
// First ask Bot Service if it already has a token for this user
var token = await context.GetUserTokenAsync(ConnectionName).ConfigureAwait(false);
if (token != null)
{
    // use the token to do exciting things!
}
else
{
    // If Bot Service does not have a token, send an OAuth card to sign in 
    await SendOAuthCardAsync(context, (Activity)context.Activity);
}
```

Se não houver um token de acesso, seu código enviará uma mensagem com um OAuthCard para o usuário:

```CSharp
private async Task SendOAuthCardAsync(IDialogContext context, Activity activity)
{
    await context.PostAsync($"To do this, you'll first need to sign in.");

    var reply = await context.Activity.CreateOAuthReplyAsync(_connectionName, _signInMessage, _buttonLabel).ConfigureAwait(false);
    await context.PostAsync(reply);

    context.Wait(WaitForToken);
}
```

Para lidar com a atividade de logon concluído, você precisará processar essa invocação:

```CSharp
if (activity.Name == "signin/verifyState")
{
  // We do this so that we can pass handling to the right logic in the dialog. You can
  // set this to be whatever string you want.
  activity.Text = "loginComplete";
  await Conversation.SendAsync(activity, () => new Dialogs.RootDialog());

  return Request.CreateResponse(HttpStatusCode.OK);
}
```

No seu código de caixa de diálogo, você pode recuperar o token do serviço de autenticação do bot:

```CSharp
if (text.Contains("loginComplete"))
  {
    // Handle login completion event.
    JObject ctx = activity.Value as JObject;

    if (ctx != null)
    {
      string code = ctx["state"].ToString();

      var oauthClient = activity.GetOAuthClient();
      var token = await oauthClient.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName, magicCode: code).ConfigureAwait(false);
      if (token != null)
      {
        // Make whatever API calls here you want
        await context.PostAsync($"Success! You are now signed in.");
      }
    }
  // Need to respond to the Invoke.
  return;
}
```

## <a name="using-oauthcard-with-messaging-extensions"></a>Usando o OAuthCard com extensões de mensagens

Você também pode usar o serviço do Azure bot para conectar provedores de terceiros à sua extensão de mensagens. O fluxo é o mesmo que com um bot, exceto em vez de retornar um OAuthCard, o serviço retornará um prompt de logon.

O trecho a seguir (C#) ilustra como criar a resposta de logon:

```CSharp
var token = await client.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName).ConfigureAwait(false);

if (token == null)
{
  // Send the login response with the auth link.
  string link = await client.OAuthApi.GetSignInLinkAsync(activity, ConnectionName);

  response = new ComposeExtensionResponse()
  {
    ComposeExtension = new ComposeExtensionResult()
  };
  response.ComposeExtension.Type = "auth";
  response.ComposeExtension.SuggestedActions = new ComposeExtensionSuggestedAction()
  {
    Actions = new List<CardAction>()
      {
        new CardAction(ActionTypes.OpenUrl, title: "Sign into this app", value: link)
      }
    };
  return response;
}
```

Observe que, no exemplo acima, você precisa fazer a chamada `GetSignInLinkAsync` diretamente em relação à `client.OAuthApi` propriedade.

Quando o usuário concluir a sequência de logon com êxito, o serviço receberá outra solicitação de chamada que contém a consulta de usuário original, juntamente com uma cadeia de caracteres de parâmetro de estado que contém o "código mágico". Agora você pode buscar o token usando essa cadeia de caracteres, juntamente com a ID de usuário e o nome da conexão.

```CSharp
var query = activity.GetComposeExtensionQueryData();
JObject data = activity.Value as JObject;

var client = activity.GetOAuthClient();

// Check if the request comes with login state
if (data != null && data["state"] != null)
{
  var token = await client.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName, data["state"].ToString());

  // Do stuff with the token here.

}
```
