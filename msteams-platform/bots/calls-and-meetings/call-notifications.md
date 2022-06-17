---
title: Notificações de chamadas recebidas
description: Neste módulo, saiba mais sobre informações técnicas detalhadas sobre como lidar com notificações de chamadas de entrada, redirecionar e autenticar chamadas usando exemplos de código
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 04/02/2019
ms.openlocfilehash: fd68b85a3c6f5f4682a728461d792093bcd8cac0
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143827"
---
# <a name="incoming-call-notifications"></a>Notificações de chamadas recebidas

Ao [registrar um bot de chamadas e reuniões para o Microsoft Teams](./registering-calling-bot.md#create-new-bot-or-add-calling-capabilities), o Webhook para a URL de chamada é mencionado. Essa URL é o ponto de extremidade do webhook para todas as chamadas de entrada para o seu bot.

## <a name="protocol-determination"></a>Determinação de protocolo

A notificação de entrada é fornecida em um formato herdado para compatibilidade com o [protocolo Skype](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0&preserve-view=true)anterior. Para converter a chamada para o protocolo microsoft Graph, o bot deve determinar se a notificação está em um formato herdado e fornece a seguinte resposta:

```http
HTTP/1.1 204 No Content
```

Seu bot recebe a notificação novamente, mas desta vez no Microsoft Graph protocolo.

Em uma versão futura da Plataforma de Mídia em Tempo Real, você pode configurar o protocolo compatível com seu aplicativo para evitar o recebimento do retorno de chamada inicial no formato herdado.

A próxima seção fornece detalhes sobre as notificações de chamada de entrada redirecionadas para afinidade de região para sua implantação.

## <a name="redirects-for-region-affinity"></a>Redirecionamentos para afinidade de região

Você chama o webhook do data center que hospeda a chamada. A chamada é iniciada em qualquer data center e não leva em conta as afinidades de região. A notificação é enviada para sua implantação, dependendo da resolução do GeoDNS. Se o aplicativo determinar, inspecionando a carga de notificação inicial ou de outra forma, que ele precisa ser executado em uma implantação diferente, o aplicativo fornecerá a seguinte resposta:

```http
HTTP/1.1 302 Found
Location: your-new-location
```

Habilite o bot para responder a uma chamada de entrada usando a API [de resposta](/graph/api/call-answer?view=graph-rest-1.0&tabs=http&preserve-view=true). Você pode especificar o `callbackUri` para manipular essa chamada específica. Isso é útil para instâncias com estado em que sua chamada é tratada por uma partição específica e você deseja inserir essas informações no `callbackUri` para roteamento para a instância certa.

A próxima seção fornece detalhes sobre como autenticar o retorno de chamada inspecionando o token postado no webhook.

## <a name="authenticate-the-callback"></a>Autenticar o retorno de chamada

Seu bot deve inspecionar o token postado no webhook para validar a solicitação. Sempre que a API posta no webhook, a mensagem HTTP POST contém um token OAuth no cabeçalho de Autorização como um token de portador, com a audiência como a ID do aplicativo.

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

O token OAuth tem os seguintes valores e é assinado pelo Skype:

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

A configuração openID publicada em <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> pode ser usada para verificar o token. Cada valor de token OAuth é usado da seguinte maneira:

* `aud` em que audiência é o URI da ID do Aplicativo especificado para o aplicativo.
* `tid` é a ID do locatário Contoso.com.
* `iss` é o emissor do token, `https://api.botframework.com`.

Para o tratamento de código, o webhook deve validar o token, verificar se ele não expirou e verificar se ele foi assinado pela configuração do OpenID publicada. Você também deve verificar se a aud corresponde à ID do aplicativo antes de aceitar a solicitação de retorno de chamada.

Para obter mais informações, consulte [validar solicitações de entrada](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Requisitos e considerações para bots de mídia hospedados pelo aplicativo](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)

## <a name="see-also"></a>Confira também

* [Configurar um atendedor automático](/microsoftteams/create-a-phone-system-auto-attendant)
* [Configurar a resposta automática para Salas do Microsoft Teams em Android e em dispositivos de telefone com vídeo Teams](/microsoftteams/set-up-auto-answer-on-teams-android)