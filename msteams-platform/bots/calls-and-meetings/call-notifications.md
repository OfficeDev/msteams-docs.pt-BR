---
title: Notificações de chamadas recebidas
description: Saiba mais sobre informações técnicas detalhadas sobre como lidar com notificações de chamadas de entrada, redirecionar e autenticar chamadas usando exemplos de código
ms.topic: conceptual
ms.localizationpriority: medium
keywords: afinidade de região de retorno de chamada de chamadas
ms.date: 04/02/2019
ms.openlocfilehash: d1d0371f714f64d2f64dbcb9512be77318cf1fb5
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60889157"
---
# <a name="incoming-call-notifications"></a>Notificações de chamadas recebidas

Ao [registrar um bot de chamadas e](./registering-calling-bot.md#create-new-bot-or-add-calling-capabilities)reuniões para Microsoft Teams , o Webhook para chamar URL é mencionado. Essa URL é o ponto de extremidade do webhook para todas as chamadas de entrada para seu bot.

## <a name="protocol-determination"></a>Determinação do protocolo

A notificação de entrada é fornecida em um formato herdado para compatibilidade com o protocolo [Skype anterior.](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0&preserve-view=true) Para converter a chamada para o protocolo microsoft Graph, seu bot deve determinar se a notificação está em um formato herdado e fornecer a seguinte resposta:

```http
HTTP/1.1 204 No Content
```

Seu bot recebe a notificação novamente, mas desta vez no protocolo microsoft Graph.

Em uma versão futura da Plataforma de Mídia em tempo real, você pode configurar o protocolo compatível com o aplicativo para evitar receber o retorno de chamada inicial no formato herddo.

A próxima seção fornece detalhes sobre notificações de chamadas de entrada redirecionadas para afinidade de região para sua implantação.

## <a name="redirects-for-region-affinity"></a>Redirecionamentos para afinidade de região

Você chama seu webhook do data-center que hospeda a chamada. A chamada começa em qualquer data center e não leva em conta as afinidades de região. A notificação é enviada para sua implantação, dependendo da resolução GeoDNS. Se o aplicativo determinar, inspecionando a carga de notificação inicial ou de outra forma, que ele precisa ser executado em uma implantação diferente, o aplicativo fornece a seguinte resposta:

```http
HTTP/1.1 302 Found
Location: your-new-location
```

Habilita o bot a responder a uma chamada de entrada usando a API [de resposta.](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) Você pode especificar o `callbackUri` para manipular essa chamada específica. Isso é útil para instâncias de estado em que sua chamada é manipulada por uma partição específica e você deseja inserir essas informações no roteamento para `callbackUri` a instância certa.

A próxima seção fornece detalhes sobre a autenticação do retorno de chamada inspecionando o token postado em seu webhook.

## <a name="authenticate-the-callback"></a>Autenticar o retorno de chamada

Seu bot deve inspecionar o token postado no webhook para validar a solicitação. Sempre que a API posta no webhook, a mensagem HTTP POST contém um token OAuth no cabeçalho Autorização como um token de portador, com a audiência como iD do aplicativo.

Seu aplicativo deve validar esse token antes de aceitar a solicitação de retorno de chamada.

O código de exemplo a seguir é usado para autenticar o retorno de chamada:

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
Authentication: Bearer <TOKEN>

"value": [
    "subscriptionId": "2887CEE8344B47C291F1AF628599A93C",
    "subscriptionExpirationDateTime": "2016-11-20T18:23:45.9356913Z",
    "changeType": "updated",
    "resource": "/app/calls/8A934F51F25B4EE19613D4049491857B",
    "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "state": "Established"
    }
]
```

O token OAuth tem os seguintes valores e é assinado por Skype:

```json
{
    "aud": "0efc74f7-41c3-47a4-8775-7259bfef4241",
    "iss": "https://api.botframework.com",
    "iat": 1466741440,
    "nbf": 1466741440,
    "exp": 1466745340,
    "tid": "1fdd12d0-4620-44ed-baec-459b611f84b2"
}
```

A configuração OpenID publicada <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> em pode ser usada para verificar o token. Cada valor de token OAuth é usado da seguinte forma:

* `aud` onde audiência é o URI de ID do aplicativo especificado para o aplicativo.
* `tid` é a ID do locatário para Contoso.com.
* `iss` é o emissor de token, `https://api.botframework.com` .

Para a manipulação de código, o webhook deve validar o token, garantir que ele não expirou e verificar se ele foi assinado pela configuração OpenID publicada. Você também deve verificar se a aud corresponde à ID do aplicativo antes de aceitar a solicitação de retorno de chamada.

Para obter mais informações, consulte [validate inbound requests](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Requisitos e considerações para bots de mídia hospedados pelo aplicativo](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
