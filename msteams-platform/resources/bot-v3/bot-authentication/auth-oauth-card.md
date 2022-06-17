---
title: Usando o Azure Serviço de Bot autenticação no Teams
description: Descreve o Azure Serviço de Bot OAuthCard e como ele é usado para autenticação
ms.topic: conceptual
localization_priority: Normal
keywords: autenticação do teams OAuthCard OAuth cartão Azure Serviço de Bot
ms.openlocfilehash: 7731e4d1148e50c748d9c5e1b55371628a78dea7
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143162"
---
# <a name="using-azure-bot-service-for-authentication-in-teams"></a>Usando o Azure Serviço de Bot autenticação no Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sem o OAuthCard do Serviço de Bot do Azure, é complicado implementar a autenticação em um bot. É um desafio de pilha completa que envolve a criação de uma experiência da Web, a integração com provedores OAuth externos, o gerenciamento de tokens e o tratamento das chamadas de API de servidor para servidor corretas para concluir o fluxo de autenticação com segurança. Isso pode resultar em experiências clunky que exigem a entrada de "números mágicos".

Com o OAuthCard do Serviço de Bot Azure, é mais fácil para seu bot Teams conectar seus usuários e acessar provedores de dados externos. Se você já implementou a autenticação e deseja alternar para algo mais simples ou se deseja adicionar autenticação ao serviço de bot pela primeira vez, o OAuthCard pode facilitar.

Outros tópicos na [](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) Autenticação descrevem a autenticação sem usar o OAuthCard, portanto, se você quiser entender a autenticação no Teams mais profundamente ou tiver uma situação em que não possa usar o OAuthCard, ainda poderá consultar esses tópicos.

## <a name="support-for-the-oauthcard"></a>Suporte para o OAuthCard

Atualmente, há algumas restrições para onde você pode usar o OAuthCard. Entre eles:

* O cartão não funcionará com acesso [de convidado](/MicrosoftTeams/guest-access).
* Não funcionará [com Microsoft Teams gratuito.](https://products.office.com/microsoft-teams/free)
* Ele só pode ser usado para autenticação de bot.
* Ele só funciona para bots registrados no [Azure Serviço de Bot](https://azure.microsoft.com/services/bot-service/).

## <a name="how-does-the-azure-bot-service-help-me-do-authentication"></a>Como o Azure Serviço de Bot me ajuda a fazer a autenticação?

A documentação completa usando o OAuthCard está disponível no tópico: Adicionar autenticação ao bot por meio do [Azure Serviço de Bot](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0&preserve-view=true). Observe que este tópico está no conjunto de documentação do Azure Bot Framework e não é específico para Teams.

As seções a seguir mostram como usar o OAuthCard no Teams.

## <a name="main-benefits-for-teams-developers"></a>Principais benefícios para Teams desenvolvedores

O OAuthCard ajuda com a autenticação das seguintes maneiras:

* Fornece um fluxo de autenticação baseado na Web inicial: você não precisa mais escrever e hospedar uma página da Web para direcionar para experiências de logon externas ou fornecer um redirecionamento.
* É contínuo para os usuários finais: conclua a experiência de entrada completa diretamente dentro Teams.
* Inclui o gerenciamento fácil de tokens: você não precisa mais implementar um sistema de armazenamento de tokens– em vez disso, o Serviço de Bot cuida do cache de token e fornece um mecanismo seguro para buscar esses tokens.
* Há suporte para SDKs completos: fácil de integrar e consumir do serviço de bot.
* Tem suporte pronto para uso para muitos provedores populares do OAuth, como Azure AD/MSA, Facebook e Google.

## <a name="when-should-i-implement-my-own-solution"></a>Quando devo implementar minha própria solução?

Como os tokens de acesso são informações confidenciais, talvez você não queira armazená-los em um serviço externo. Nesse caso, você pode optar por ainda implementar seu próprio sistema de gerenciamento de token e experiência de logon no Teams, conforme descrito no restante dos tópicos de autenticação Teams [](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) autenticação.

## <a name="getting-started-with-oauthcard-in-teams"></a>Introdução ao OAuthCard no Teams

> [!NOTE]
> Este guia está usando o SDK do Bot Framework v3. Você pode encontrar a implementação v4 [aqui](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true). Você ainda precisará criar um manifesto e incluir token.botframework.com na seção, porque caso contrário, o botão Entrar não abrirá a `validDomains` janela de autenticação. Use o [App Studio](~/concepts/build-and-test/app-studio-overview.md) para gerar seu manifesto.

Primeiro, você precisará configurar seu serviço de bot do Azure para configurar provedores de autenticação externos. Leia [Configurar provedores de identidade](~/concepts/authentication/configure-identity-provider.md) para obter etapas detalhadas.

Para habilitar a autenticação usando o Serviço de Bot do Azure, você precisa fazer essas adições ao código:

1. Inclua token.botframework.com na seção `validDomains` do manifesto do aplicativo porque Teams inserirá a página Serviço de Bot de logon do aplicativo.
2. Busque o token do Serviço de Bot sempre que o bot precisar acessar recursos autenticados. Se nenhum token estiver disponível, envie uma mensagem com um OAuthCard para o usuário solicitando que ele faça logon no serviço externo.
3. Manipule a atividade de conclusão de logon. Isso garante que a solicitação de autenticação e o token estejam associados ao usuário que está interagindo com o bot no momento.
4. Recupere o token sempre que o bot precisar executar ações autenticadas, como chamar APIs REST externas.

No código da caixa de diálogo, você precisará adicionar esse snippet (C#), que verifica se há um token de acesso existente:

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

Se um token de acesso não existir, seu código enviará uma mensagem com um OAuthCard para o usuário:

```CSharp
private async Task SendOAuthCardAsync(IDialogContext context, Activity activity)
{
    await context.PostAsync($"To do this, you'll first need to sign in.");

    var reply = await context.Activity.CreateOAuthReplyAsync(_connectionName, _signInMessage, _buttonLabel).ConfigureAwait(false);
    await context.PostAsync(reply);

    context.Wait(WaitForToken);
}
```

Para lidar com a atividade de logon completo, você precisará processar esta Invocação:

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

No código da caixa de diálogo, você pode recuperar o token do serviço de autenticação de Bot:

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

Você também pode usar o Azure Serviço de Bot para conectar provedores de terceiros à sua extensão de mensagens. O fluxo é o mesmo que com um bot, exceto que, em vez de retornar um OAuthCard, seu serviço retornará um prompt de logon.

O snippet de código a seguir (C#) ilustra como criar a resposta de logon:

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

Observe que, no exemplo acima, você precisa fazer a chamada diretamente `GetSignInLinkAsync` na `client.OAuthApi` propriedade.

Quando o usuário concluir com êxito a sequência de logon, o serviço receberá outra solicitação invoke contendo a consulta de usuário original, juntamente com uma cadeia de caracteres de parâmetro de estado que contém o "código mágico". Agora você pode buscar o token usando essa cadeia de caracteres, juntamente com a ID de usuário e o nome da conexão.

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
