---
title: Detalhes técnicos sobre como lidar com notificações de chamada de entrada
description: Informações técnicas detalhadas sobre o tratamento de notificações de chamadas de entrada
keywords: chamar as notificações de chamadas afinidade de região de retorno de chamada
ms.date: 04/02/2019
ms.openlocfilehash: be8860ff70cd7dff4fd9599079ea7aab4f454174
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672872"
---
# <a name="incoming-call-notifications-technical-details"></a>Notificações de chamada de entrada: detalhes técnicos

Ao [registrar um bot de chamada e reunião para o Microsoft Teams](./registering-calling-bot.md#creating-a-new-bot-or-adding-calling-capabilities-to-an-existing-bot), mencionamos a URL de **webhook (para chamada)** , o ponto de extremidade de webhook para todas as chamadas de entrada para o bot. Este tópico discute os detalhes técnicos que você precisará para responder a essas notificações.

## <a name="protocol-determination"></a>Determinação de protocolo

A notificação de entrada é fornecida no formato Legacy para compatibilidade com o [protocolo Skype](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0)anterior. Para converter a chamada para o protocolo Microsoft Graph, seu bot deve determinar se a notificação está no formato herdado e responder com:

```http
HTTP/1.1 204 No Content
```

O bot receberá a notificação novamente, mas desta vez no protocolo Microsoft Graph.

Em uma versão futura da plataforma de mídia em tempo real, vamos permitir que você configure o protocolo que seu aplicativo suporta para evitar receber o retorno de chamada inicial no formato herdado.

## <a name="redirects-for-region-affinity"></a>Redireciona para afinidade de região

Você chamará o webhook do centro de dados que hospeda a chamada. A chamada pode começar em qualquer data center e não leva em conta as afinidades de região. A notificação será enviada para sua implantação, dependendo da resolução do GeoDNS. Se o aplicativo determinar, inspecionar a carga de notificação inicial ou, caso contrário, ele precisará ser executado em uma implantação diferente, o aplicativo pode responder com:

```http
HTTP/1.1 302 Found
Location: your-new-location
```

Habilite o bot para atender a uma chamada de entrada usando a API de [resposta](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) . Você pode especificar o `callbackUri` para lidar com essa chamada específica. Isso é útil para instâncias de _estado_ em que sua chamada é manipulada por uma determinada partição e você deseja inserir essas informações `callbackUri` no para roteamento para a instância correta.

## <a name="authenticating-the-callback"></a>Autenticar o retorno de chamada

O bot deve inspecionar o token Postado no seu webhook para validar a solicitação. Sempre que a API é postada para o webhook, a mensagem HTTP POST contém um token OAuth no cabeçalho Authorization como um token de portador, com o público como a ID de aplicativo do aplicativo.

O aplicativo deve validar esse token antes de aceitar a solicitação de retorno de chamada.

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

O token OAuth terá valores como os seguintes e será assinado pelo Skype. A configuração de OpenID publicada <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> em pode ser usada para verificar o token.

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

* o público-alvo **AUD** é o URI da ID do aplicativo especificado para o aplicativo.
* **tid** é a ID do locatário para contoso.com.
* o **ISS** é o emissor do token `https://api.botframework.com`,.

Seu código de manipulação do webhook deve validar o token, garantir que ele não tenha expirado e verificar se ele foi assinado pela nossa configuração de OpenID publicada. Você também deve verificar se o **AUD** corresponde à ID do aplicativo antes de aceitar a solicitação de retorno de chamada.

[Exemplo](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs) mostra como validar solicitações de entrada.
