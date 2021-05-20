---
title: Suporte SSO para suas extensões de mensagens
author: KirtiPereira
description: Como ativar o suporte ao SSO para suas extensões de mensagens
localization_priority: Normal
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 02d08506a07e955693531908f4f3cf16573a02c0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566198"
---
# <a name="single-sign-on-sso-support-for-messaging-extensions"></a>Suporte de login único (SSO) para extensões de mensagens
 
O suporte de login único já está disponível para extensões de mensagens e desvendação de links. Habilitar O SSO (Single Sign-on, on-on) para extensões de mensagens atualiza silenciosamente o token de autenticação, o que minimiza o número de vezes que você precisa para inserir seu sinal em credenciais para Microsoft Teams.

Este documento orienta você sobre como ativar o SSO e armazenar seu token de autenticação, se necessário.

## <a name="prerequisites"></a>Pré-requisitos

O pré-requisito para habilitar o SSO para extensões de mensagens e desvendação de links é o seguinte:
* Você deve ter uma [conta no Azure.](https://azure.microsoft.com/en-us/free/)
* Você deve configurar seu aplicativo através do portal AAD e atualizar seu manifesto de aplicativo Teams para o seu bot conforme definido no [cadastro do seu aplicativo através do portal AAD](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal).

> [!NOTE]
> Para obter mais informações sobre a criação de uma conta do Azure e a atualização do manifesto do aplicativo, consulte [o suporte ao Single Sign-on (SSO) para bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).

## <a name="enable-sso-for-messaging-extensions-and-link-unfurling"></a>Habilite o SSO para extensões de mensagens e desvendamento de links

Depois que os pré-requisitos forem concluídos, você pode habilitar o SSO para extensões de mensagens e desenrolar de links.

**Para habilitar o SSO**
1. Atualize seus bots [Detalhes da conexão OAuth](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) no portal Azure.
2. Baixe a [amostra de extensões de mensagens](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) e siga as instruções de configuração fornecidas pelo assistente.
   > [!NOTE]
   > Use a conexão OAuth dos bots ao configurar suas extensões de mensagens.
3. No arquivo [TeamsMessagingExtensionsSearchAuthConfigBot.cs,](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) atualize o valor do *auth* para *silentAuth* no `OnTeamsMessagingExtensionQueryAsync` e/ou `OnTeamsAppBasedLinkQueryAsync` .  

    > [!NOTE]
    > Não suportamos outros manipuladores SSO, exceto `OnTeamsMessagingExtensionQueryAsync` e `OnTeamsAppBasedLinkQueryAsync` do arquivo TeamsMessagingExtensionsSearchAuthConfigBot.cs arquivo.
   
4. Você recebe o token no `OnTeamsMessagingExtensionQueryAsync` manipulador na carga ou no , dependendo do cenário para o qual você está `turnContext.Activity.Value` `OnTeamsAppBasedLinkQueryAsync` habilitando o SSO:

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    Se você estiver usando a conexão OAuth, adicione o seguinte código às EquipesMessagingExtensionsSearchAuthConfigBot.cs arquivo para atualizar ou adicionar o token na loja:
    
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

* [Adicione autenticação às suas extensões de mensagens](add-authentication.md)
* [Use SSO para bots](../../bots/how-to/authentication/auth-aad-sso-bots.md)
* [Desenrolamento de link](link-unfurling.md)

