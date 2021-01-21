---
title: Adicionar autenticação à extensão de mensagens
author: clearab
description: Como adicionar autenticação a uma extensão de mensagens
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 4ebe65af06240d13ceb99fe3b7640ab402d716c5
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911867"
---
# <a name="add-authentication-to-your-messaging-extension"></a>Adicionar autenticação à extensão de mensagens

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a>Identificar o usuário

Todas as solicitações para seus serviços incluem a ID ofuscada do usuário que realizou a solicitação, bem como o nome de exibição do usuário e a ID de objeto do Azure Active Directory.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Os `id` valores e os valores são `aadObjectId` garantidos como sendo os do usuário autenticado do Teams. Eles podem ser usados como chaves para procurar credenciais ou qualquer estado armazenado em cache em seu serviço. Além disso, cada solicitação contém a ID de locatário do Azure Active Directory do usuário, que pode ser usada para identificar a organização do usuário. Se aplicável, a solicitação também contém as IDs de equipe e de canal da qual a solicitação se originou.

## <a name="authentication"></a>Autenticação

Se o serviço exigir autenticação do usuário, você precisará entrar no usuário antes que ele possa usar a extensão de mensagens. Se você tiver escrito um bot ou uma guia que entre no usuário, esta seção deve ser familiar.

A sequência é a seguinte:

1. O usuário emite uma consulta ou a consulta padrão é automaticamente enviada ao serviço.
2. Seu serviço verifica se o usuário foi autenticado primeiro inspecionando a ID de usuário do Teams.
3. Se o usuário não tiver sido autenticado, envie uma resposta `auth` com uma `openUrl` ação sugerida, incluindo a URL de autenticação.
4. O cliente Microsoft Teams inicia uma janela pop-up hospedando sua página da Web usando a URL de autenticação determinada.
5. Depois que o usuário entrar, você deverá fechar a janela e enviar um "código de autenticação" para o cliente do Teams.
6. Em seguida, o cliente do Teams em seguida emira a consulta para seu serviço, o que inclui o código de autenticação passado na etapa 5.

Seu serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5. Isso garante que um usuário mal-intencionado não tente fazer spoof ou comprometer o fluxo de login. Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.

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
> Para que a experiência de login seja hospedada em um pop-up do Teams, a parte de domínio da URL deve estar na lista de domínios válidos do seu aplicativo. (Consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.)

### <a name="start-the-sign-in-flow"></a>Iniciar o fluxo de login

Sua experiência de login deve ser responsiva e caber em uma janela pop-up. Ele deve se integrar ao [SDK](/javascript/api/overview/msteams-client)do cliente JavaScript do Microsoft Teams, que usa a passagem de mensagens.

Assim como outras experiências incorporadas em execução no Microsoft Teams, seu código dentro da janela precisa primeiro `microsoftTeams.initialize()` chamar. Se o código executar um fluxo OAuth, você poderá passar a ID de usuário do Teams para sua janela, que pode passá-la para a URL de entrada do OAuth.

### <a name="complete-the-sign-in-flow"></a>Concluir o fluxo de login

Quando a solicitação de login for concluída e redirecionada de volta para sua página, ela deverá executar as seguintes etapas:

1. Gere um código de segurança. (Pode ser um número aleatório.) Você precisa armazenar em cache esse código em seu serviço, juntamente com as credenciais obtidas por meio do fluxo de logon (como tokens OAuth 2.0).
2. Ligue `microsoftTeams.authentication.notifySuccess` e passe o código de segurança.

Neste ponto, a janela é fechada e o controle é passado para o cliente do Teams. O cliente agora pode reemarciar a consulta do usuário original, juntamente com o código de segurança na `state` propriedade. Seu código pode usar o código de segurança para procurar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e concluir a solicitação do usuário.

#### <a name="reissued-request-example"></a>Exemplo de solicitação em reemissão

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

## <a name="samples"></a>Exemplos
Para código de exemplo mostrando o processo de autenticação messaging-extensions, consulte:

[Exemplo de autenticação de extensões de mensagens do Microsoft Teams](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)

 
