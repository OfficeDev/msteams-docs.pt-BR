---
title: Usando o Serviço bot do Azure para autenticação Teams
description: Descreve o OAuthCard do Serviço de Bot do Azure e como ele é usado para autenticação
ms.topic: conceptual
localization_priority: Normal
keywords: autenticação do teams OAuthCard OAuth card Azure Bot Service
ms.openlocfilehash: 3d0df4f04625c5be3468d12319b54096ae06de90
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020678"
---
# <a name="using-azure-bot-service-for-authentication-in-teams"></a>Usando o Serviço bot do Azure para autenticação Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sem o OAuthCard do Serviço de Bot do Azure, é complicado implementar a autenticação em um bot. É um desafio de pilha completa que envolve a criação de uma experiência da Web, a integração com provedores OAuth externos, o gerenciamento de tokens e o tratamento das chamadas de API de servidor para servidor corretas para concluir o fluxo de autenticação com segurança. Isso pode resultar em experiências descaradas que exigem a entrada de "números mágicos".

Com o OAuthCard do Serviço de Bot do Azure, é mais fácil para seu bot Teams entrar em seus usuários e acessar provedores de dados externos. Se você já implementou a autenticação e deseja alternar para algo mais simples ou se deseja adicionar autenticação ao serviço de bot pela primeira vez, o OAuthCard pode facilitar.

Outros tópicos [](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) em Autenticação descrevem a autenticação sem usar o OAuthCard, portanto, se você quiser entender a autenticação no Teams mais profundamente ou se tiver uma situação em que não possa usar o OAuthCard, ainda poderá se referir a esses tópicos.

## <a name="support-for-the-oauthcard"></a>Suporte para o OAuthCard

Atualmente, há algumas restrições para onde você pode usar o OAuthCard. Entre eles:

* O cartão não funcionará com o [acesso de convidados](/MicrosoftTeams/guest-access)
* Ele não funcionará com [Microsoft Teams gratuito](https://products.office.com/microsoft-teams/free)
* Ele só pode ser usado para autenticação de bot
* Ele só funciona para bots registrados no [Serviço bot do Azure](https://azure.microsoft.com/services/bot-service/)

## <a name="how-does-the-azure-bot-service-help-me-do-authentication"></a>Como o Serviço bot do Azure me ajuda a fazer autenticação?

A documentação completa usando o OAuthCard está disponível no tópico: Adicionar autenticação ao bot por meio do [Serviço de Bot do Azure.](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0&preserve-view=true) Observe que este tópico está no conjunto de documentação da Estrutura de Bots do Azure e não é específico para Teams.

As seções a seguir dizem como usar o OAuthCard no Teams.

## <a name="main-benefits-for-teams-developers"></a>Principais benefícios para Teams desenvolvedores

O OAuthCard ajuda na autenticação das seguintes maneiras:

* Fornece um fluxo de autenticação baseado na Web de forma in-loco: você não precisa mais gravar e hospedar uma página da Web para direcionar para experiências de logon externos ou fornecer um redirecionamento.
* É perfeita para os usuários finais: conclua a experiência de logon completa dentro Teams.
* Inclui o gerenciamento fácil de tokens: você não precisa mais implementar um sistema de armazenamento de tokens – em vez disso, o Serviço bot cuida do cache de token e fornece um mecanismo seguro para buscar esses tokens.
* É suportado por SDKs completos: fácil de integrar e consumir do seu serviço de bot.
* Tem suporte pronto para muitos provedores OAuth populares, como o Azure AD/MSA, o Facebook e o Google.

## <a name="when-should-i-implement-my-own-solution"></a>Quando devo implementar minha própria solução?

Como os tokens de acesso são informações confidenciais, talvez você não queira que eles sejam armazenados em um serviço externo. Nesse caso, você pode optar por ainda implementar seu próprio sistema de gerenciamento de tokens e experiência de logon no Teams, conforme descrito no restante dos tópicos Teams [Autenticação.](~/resources/bot-v3/bot-authentication/auth-flow-bot.md)

## <a name="getting-started-with-oauthcard-in-teams"></a>Iniciando com o OAuthCard no Teams

> [!NOTE]
> Este guia está usando o SDK da Estrutura de Bot v3. Você pode encontrar a implementação v4 [aqui](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true). Você ainda precisará criar um manifesto e incluir token.botframework.com na seção, pois caso contrário, o botão Entrar não abrirá a `validDomains` janela de autenticação. Use o [App Studio](~/concepts/build-and-test/app-studio-overview.md) para gerar seu manifesto.

Primeiro, você precisará configurar seu serviço de bot do Azure para configurar provedores de autenticação externos. Leia [Configurando provedores de identidade](~/concepts/authentication/configure-identity-provider.md) para etapas detalhadas.

Para habilitar a autenticação usando o Serviço bot do Azure, você precisa fazer essas adições ao seu código:

1. Inclua token.botframework.com na seção do manifesto do aplicativo porque Teams inserirá a página de logon do Serviço `validDomains` bot.
2. Busque o token do Serviço bot sempre que o bot precisar acessar recursos autenticados. Se nenhum token estiver disponível, envie uma mensagem com um OAuthCard para o usuário solicitando que ele faça logon no serviço externo.
3. Manipular a atividade de conclusão de logon. Isso garante que a solicitação de autenticação e o token estão associados ao usuário que está interagindo com seu bot no momento.
4. Recupere o token sempre que o bot precisar executar ações autenticadas, como chamar APIs REST externas.

No código de caixa de diálogo, você precisará adicionar esse trecho (C#), que verifica se há um token de acesso existente:

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

Para manipular a atividade completa de logon, você precisará processar este Invoke:

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

No código de caixa de diálogo, você pode recuperar o token do serviço de autenticação bot:

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

Você também pode usar o Serviço bot do Azure para conectar provedores de terceiros à extensão de mensagens. O fluxo é igual ao de um bot, exceto que, em vez de retornar um OAuthCard, seu serviço retornará um prompt de logon.

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

Observe que, no exemplo acima, você precisa fazer a chamada `GetSignInLinkAsync` diretamente contra a `client.OAuthApi` propriedade.

Quando o usuário concluir com êxito a sequência de logon, seu serviço receberá outra solicitação Invoke contendo a consulta do usuário original, juntamente com uma cadeia de caracteres de parâmetro de estado que contém o "código mágico". Agora você pode buscar o token usando essa cadeia de caracteres, juntamente com a ID do usuário e o nome da conexão.

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
