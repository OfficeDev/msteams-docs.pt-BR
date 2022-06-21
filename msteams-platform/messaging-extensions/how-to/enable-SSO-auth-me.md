---
title: Suporte de SSO para extensões de mensagem
author: KirtiPereira
description: Neste artigo, você aprenderá a habilitar o suporte ao SSO (logon único) para suas extensões de mensagens com exemplos de Código.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: e891e147d4cc3216b6c2acb686505dd03353b385
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189859"
---
# <a name="single-sign-on-support-for-message-extensions"></a>Suporte de logon único para extensões de mensagem

O suporte ao SSO (logon único) agora está disponível para extensões de mensagem e desassociação do link. Habilitar o logon único para extensões de mensagem por padrão atualiza o token de autenticação, o que minimiza o número de vezes que você precisa inserir as credenciais de entrada para Microsoft Teams.

Este documento orienta você sobre como habilitar o SSO e armazenar seu token de autenticação, se necessário.

## <a name="prerequisites"></a>Pré-requisitos

O pré-requisito para habilitar o SSO para extensões de mensagem e desassociar o link é o seguinte:

* Você deve ter uma [conta do Azure](https://azure.microsoft.com/free/).
* Você deve configurar seu aplicativo por meio do portal Azure AD e atualizar o manifesto do aplicativo do Teams, conforme definido em [registro do aplicativo por meio do portal Azure AD aplicativo](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-azure-ad-portal).

> [!NOTE]
> Para obter mais informações sobre como criar uma conta do Azure e atualizar o manifesto do aplicativo, consulte o suporte de SSO (logon único [) para bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).

## <a name="enable-sso-for-message-extensions-and-link-unfurling"></a>Habilitar o SSO para extensões de mensagem e desassociação do link

Depois que os pré-requisitos forem concluídos, você poderá habilitar o SSO para extensões de mensagem e vincular o desassociar.

Para habilitar o SSO:

1. Atualize os detalhes [de conexão OAuth](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) dos bots no portal Microsoft Azure aplicativo.
2. Baixe o [exemplo de extensões de mensagem](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) e siga as instruções de configuração fornecidas pelo assistente.
   > [!NOTE]
   > Use a conexão OAuth dos bots ao configurar as extensões de mensagem.
3. No arquivo [TeamsMessagingExtensionsSearchAuthConfigBot.cs](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs), atualize o valor de *autenticação* para *silentAuth* no `OnTeamsMessagingExtensionQueryAsync` e/ou `OnTeamsAppBasedLinkQueryAsync`.  

    > [!NOTE]
    > Não há suporte para outros manipuladores SSO, exceto `OnTeamsMessagingExtensionQueryAsync` e `OnTeamsAppBasedLinkQueryAsync` do arquivo TeamsMessagingExtensionsSearchAuthConfigBot.cs.

4. Você recebe o token no `OnTeamsMessagingExtensionQueryAsync` `turnContext.Activity.Value` manipulador no conteúdo `OnTeamsAppBasedLinkQueryAsync`ou no , dependendo de qual cenário você está habilitando o SSO para:

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    Se você estiver usando a conexão OAuth, adicione o seguinte código ao arquivo TeamsMessagingExtensionsSearchAuthConfigBot.cs para atualizar ou adicionar o token no repositório:

   ```C#
   protected override async Task<InvokeResponse> OnInvokeActivityAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
        {
            JObject valueObject = JObject.FromObject(turnContext.Activity.Value);
            if (valueObject["authentication"] != null)
            {
                JObject authenticationObject = JObject.FromObject(valueObject["authentication"]);
                if (authenticationObject["token"] != null)
                {
                    //If the token is NOT exchangeable, then return 412 to require user consent
                    if (await TokenIsExchangeable(turnContext, cancellationToken))
                    {
                        return await base.OnInvokeActivityAsync(turnContext, cancellationToken).ConfigureAwait(false);
                    }
                    else
                    {
                        var response = new InvokeResponse();
                        response.Status = 412;
                        return response;
                    }
                }
            }
            return await base.OnInvokeActivityAsync(turnContext, cancellationToken).ConfigureAwait(false);
        }
        private async Task<bool> TokenIsExchangeable(ITurnContext turnContext, CancellationToken cancellationToken)
        {
            TokenResponse tokenExchangeResponse = null;
            try
            {
                JObject valueObject = JObject.FromObject(turnContext.Activity.Value);
                var tokenExchangeRequest =
                ((JObject)valueObject["authentication"])?.ToObject<TokenExchangeInvokeRequest>();
                var userTokenClient = turnContext.TurnState.Get<UserTokenClient>();
                tokenExchangeResponse = await userTokenClient.ExchangeTokenAsync(
                                turnContext.Activity.From.Id,
                                 _connectionName,
                                 turnContext.Activity.ChannelId,
                                 new TokenExchangeRequest
                 {
                     Token = tokenExchangeRequest.Token,
                 },
                  cancellationToken).ConfigureAwait(false);
            }
    #pragma warning disable CA1031 //Do not catch general exception types (ignoring, see comment below)
            catch
    #pragma warning restore CA1031 //Do not catch general exception types
            {
                //ignore exceptions
                //if token exchange failed for any reason, tokenExchangeResponse above remains null, and a failure invoke response is sent to the caller.
                //This ensures the caller knows that the invoke has failed.
            }
            if (tokenExchangeResponse == null || string.IsNullOrEmpty(tokenExchangeResponse.Token))
            {
                return false;
            }
            return true;
        }
    
    ```

## <a name="code-sample"></a>Exemplo de código

Esta seção fornece um exemplo de SDK de autenticação de bot v3.

| **Nome de exemplo** | **Descrição** | **.NET** | **Node.js** | **Python** |
|---------------|------------|------------|-------------|---------------|
| Autenticação de bot | Este exemplo mostra como começar a usar a autenticação em um bot para Teams. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth) | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/46.teams-auth) |
| SSO de guia, bot e extensão de mensagem (ME) | Este exemplo mostra o SSO para Tab, Bot e ME – pesquisar, ação, vincular desfral. |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-sso/nodejs) | Não disponível |

## <a name="see-also"></a>Confira também

* [Adicionar autenticação à sua extensão de mensagens](add-authentication.md)
* [Usar o SSO para bots](../../bots/how-to/authentication/auth-aad-sso-bots.md)
* [Desenrolamento de link](link-unfurling.md)
