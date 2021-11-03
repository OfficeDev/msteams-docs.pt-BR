---
title: Adicionar autenticação à sua extensão de mensagens
author: surbhigupta
description: Como adicionar autenticação a uma extensão de mensagens
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 85353608e062d30529d67184716f65c3e2de1863
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60719858"
---
# <a name="add-authentication-to-your-messaging-extension"></a>Adicionar autenticação à sua extensão de mensagens

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a>Identificar o usuário

Todas as solicitações aos seus serviços incluem a ID do usuário, o nome de exibição do usuário e Azure Active Directory ID do objeto.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Os `id` valores e são `aadObjectId` garantidos para o usuário Teams autenticado. Eles são usados como chaves para procurar as credenciais ou qualquer estado armazenado em cache em seu serviço. Além disso, cada solicitação contém Azure Active Directory ID do locatário, que é usada para identificar a organização do usuário. Se aplicável, a solicitação também contém a ID da equipe e a ID do canal da qual a solicitação é originada.

## <a name="authentication"></a>Autenticação

Se o serviço exigir autenticação do usuário, os usuários devem entrar antes de usar a extensão de mensagens. As etapas de autenticação são semelhantes às de um bot ou guia. A sequência é a seguinte:

1. O usuário emite uma consulta ou a consulta padrão é enviada automaticamente ao seu serviço.
1. Seu serviço verifica se o usuário é autenticado inspecionando Teams ID do usuário.
1. Se o usuário não for autenticado, envie uma resposta com uma ação `auth` `openUrl` sugerida, incluindo a URL de autenticação.
1. O Microsoft Teams cliente inicia uma caixa de diálogo hospedando sua página da Web usando a URL de autenticação determinada.
1. Depois que o usuário entrar, você deve fechar a janela e enviar um código de autenticação **para** o Teams cliente.
1. O Teams cliente, em seguida, reeditará a consulta para o seu serviço, que inclui o código de autenticação passado na Etapa 5.

Seu serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5. Isso garante que um usuário mal-intencionado não tente fazer a spoof ou comprometer o fluxo de acesso. Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.

### <a name="respond-with-a-sign-in-action"></a>Responder com uma ação de login

Para solicitar que um usuário não autenticado entre, responda com uma ação sugerida do tipo que inclui a `openUrl` URL de autenticação.

#### <a name="response-example-for-a-sign-in-action"></a>Exemplo de resposta para uma ação de login

```json
{
  "composeExtension":{
    "type":"auth",
    "suggestedActions":{
      "actions":[
        {
          "type": "openUrl",
          "value": "https://example.com/auth",
          "title": "Sign in to this app"
        }
      ]
    }
  }
}
```

> [!NOTE]
> Para que a experiência de login seja hospedada em uma janela pop-up Teams, a parte de domínio da URL deve estar na lista de domínios válidos do aplicativo. Para obter mais informações, [consulte validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.

### <a name="start-the-sign-in-flow"></a>Iniciar o fluxo de login

Sua experiência de login deve ser responsiva e adequada dentro de uma janela pop-up. Ele deve se integrar ao [Microsoft Teams SDK do cliente JavaScript](/javascript/api/overview/msteams-client), que usa a passagem de mensagens.

Assim como outras experiências incorporadas em execução dentro Microsoft Teams, seu código dentro da janela precisa chamar primeiro `microsoftTeams.initialize()` . Se seu código executar um fluxo OAuth, você poderá passar a ID do usuário Teams para sua janela, que o passa para a URL de entrada do OAuth.

### <a name="complete-the-sign-in-flow"></a>Concluir o fluxo de login

Quando a solicitação de entrar é concluída e redireciona de volta para sua página, ela deve executar as seguintes etapas:

1. Gere um código de segurança, um número aleatório. Você deve armazenar em cache esse código em seu serviço, juntamente com as credenciais obtidas por meio do fluxo de logon, como tokens OAuth 2.0.
1. Chame `microsoftTeams.authentication.notifySuccess` e passe o código de segurança.

Neste ponto, a janela fecha e o controle é passado para o cliente Teams cliente. O cliente agora reeditará a consulta de usuário original, juntamente com o código de segurança na `state` propriedade. Seu código pode usar o código de segurança para procurar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e concluir a solicitação do usuário.

#### <a name="reissued-request-example"></a>Exemplo de solicitação reemissão

```json
{
    "name": "composeExtension/query",
    "value": {
        "commandId": "insertWiki",
        "parameters": [{
            "name": "searchKeyword",
            "value": "lakers"
        }],
        "state": "12345",
        "queryOptions": {
            "skip": 0,
            "count": 25
        }
    },
    "type": "invoke",
    "timestamp": "2017-04-26T05:18:25.629Z",
    "localTimestamp": "2017-04-25T22:18:25.629-07:00",
    "entities": [{
        "locale": "en-US",
        "country": "US",
        "platform": "Web",
        "type": "clientInfo"
    }],
    "text": "",
    "attachments": [],
    "address": {
        "id": "f:7638210432489287768",
        "channelId": "msteams",
        "user": {
            "id": "29:1A5TJWHkbOwSyu_L9Ktk9QFI1d_kBOEPeNEeO1INscpKHzHTvWfiau5AX_6y3SuiOby-r73dzHJ17HipUWqGPgw",
            "aadObjectId": "fc8ca1c0-d043-4af6-b09f-141536207403"
        },
        "conversation": {
            "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
        },
        "bot": {
            "id": "28:c073afa8-7e77-4f92-b3e7-aa589e952a3e",
            "name": "maotestbot2"
        },
        "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
        "useAuth": true
    },
    "source": "msteams"
}
```

## <a name="code-sample"></a>Exemplo de código
|**Nome do exemplo** | **Descrição** |**.NET** | **Node.js**|
|----------------|-----------------|--------------|----------------|
|Extensões de mensagens - auth e config | Uma Extensão de Mensagens que tem uma página de configuração, aceita solicitações de pesquisa e retorna resultados depois que o usuário se inscreveu. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)|[View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)| 

 
