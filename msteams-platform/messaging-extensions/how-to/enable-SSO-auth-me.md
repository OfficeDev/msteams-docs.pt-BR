---
title: Suporte a SSO para extensões de mensagens
author: KirtiPereira
description: Como habilitar o suporte ao SSO para suas extensões de mensagens
localization_priority: Normal
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 656c17612c74ee55b870fd2e7e13dea60e6ed2f8
ms.sourcegitcommit: 2c4c77dc8344f2fab8ed7a3f7155f15f0dd6a5ce
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58345238"
---
# <a name="single-sign-on-sso-support-for-messaging-extensions"></a>Suporte a SSO (login único) para extensões de mensagens
 
O suporte a um único sign-on agora está disponível para extensões de mensagens e desaparalização de link. A habilitação do SSO (SSO) para extensões de mensagens atualiza silenciosamente o token de autenticação, o que minimiza o número de vezes que você precisa inserir suas credenciais de entrada para Microsoft Teams.

Este documento orienta você sobre como habilitar o SSO e armazenar seu token de autenticação, se necessário.

## <a name="prerequisites"></a>Pré-requisitos

O pré-requisito para habilitar o SSO para extensões de mensagens e a desassobilização de link são:
* Você deve ter uma [conta do Azure.](https://azure.microsoft.com/free/)
* Você deve configurar seu aplicativo por meio do portal do AAD e atualizar o manifesto do aplicativo Teams para seu bot, conforme definido no registro de seu aplicativo por meio [do portal do AAD.](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal)

> [!NOTE]
> Para obter mais informações sobre como criar uma conta do Azure e atualizar o manifesto do aplicativo, consulte Suporte a [SSO (login único) para bots.](../../bots/how-to/authentication/auth-aad-sso-bots.md)

## <a name="enable-sso-for-messaging-extensions-and-link-unfurling"></a>Habilitar o SSO para extensões de mensagens e vincular desfraldamento

Depois que os pré-requisitos são concluídos, você pode habilitar o SSO para extensões de mensagens e a desarquivamento de link.

**Para habilitar o SSO**
1. Atualize os detalhes da [conexão OAuth de](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) bots no portal do Azure.
2. Baixe o [exemplo de extensões de mensagens](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) e siga as instruções de instalação fornecidas pelo assistente.
   > [!NOTE]
   > Use sua conexão OAuth de bots ao configurar suas extensões de mensagens.
3. No [arquivo TeamsMessagingExtensionsSearchAuthConfigBot.cs,](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) atualize o valor de *auth* para *silentAuth* `OnTeamsMessagingExtensionQueryAsync` no e/ou `OnTeamsAppBasedLinkQueryAsync` .  

    > [!NOTE]
    > Não há suporte para outros manipuladores SSO, exceto no arquivo `OnTeamsMessagingExtensionQueryAsync` `OnTeamsAppBasedLinkQueryAsync` TeamsMessagingExtensionsSearchAuthConfigBot.cs.
   
4. Você recebe o token no manipulador na carga ou no , dependendo de qual cenário você está habilitando `OnTeamsMessagingExtensionQueryAsync` `turnContext.Activity.Value` o `OnTeamsAppBasedLinkQueryAsync` SSO para:

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    Se você estiver usando a conexão OAuth, adicione o seguinte código ao arquivo TeamsMessagingExtensionsSearchAuthConfigBot.cs para atualizar ou adicionar o token na loja:
    
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
                tokenExchangeResponse = await (turnContext.Adapter as IExtendedUserTokenProvider).ExchangeTokenAsync(
                 turnContext,
                 _connectionName,
                 turnContext.Activity.From.Id,
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

## <a name="see-also"></a>Confira também

* [Adicionar autenticação às extensões de mensagens](add-authentication.md)
* [Usar SSO para bots](../../bots/how-to/authentication/auth-aad-sso-bots.md)
* [Desenrolamento de link](link-unfurling.md)

