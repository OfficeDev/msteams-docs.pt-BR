---
title: Adicionar autenticação à sua extensão de mensagens
author: clearab
description: Como adicionar autenticação a uma extensão de mensagens
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f7ebbcd99b1ec35900de7ec2f54f93263918e945
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672516"
---
# <a name="add-authentication-to-your-messaging-extension"></a>Adicionar autenticação à sua extensão de mensagens

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

Os `id` valores `aadObjectId` e são garantidos do usuário do Microsoft Teams. Eles podem ser usados como chaves para procurar credenciais ou qualquer estado em cache em seu serviço. Além disso, cada solicitação contém a ID de locatário do Azure Active Directory do usuário, que pode ser usada para identificar a organização do usuário. Se aplicável, a solicitação também contém as IDs de canal e equipe das quais a solicitação foi originada.

## <a name="authentication"></a>Autenticação

Se o serviço exigir autenticação do usuário, você precisará entrar no usuário antes de poder usar a extensão de mensagens. Se você escreveu um bot ou uma guia que entra no usuário, esta seção deve ser familiar.

A sequência é a seguinte:

1. O usuário emite uma consulta ou a consulta padrão é enviada automaticamente ao seu serviço.
2. Seu serviço verifica se o usuário foi autenticado pela primeira vez inspecionando a ID de usuário do teams.
3. Se o usuário não tiver sido autenticado, envie uma `auth` resposta com uma `openUrl` ação sugerida, incluindo a URL de autenticação.
4. O cliente do Microsoft Teams inicia uma janela pop-up hospedando sua página da Web usando a URL de autenticação determinada.
5. Após o usuário entrar, você deve fechar sua janela e enviar um "código de autenticação" para o cliente do teams.
6. Em seguida, o cliente do teams emite novamente a consulta para o serviço, o que inclui o código de autenticação passado na etapa 5.

Seu serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5. Isso garante que um usuário mal-intencionado não tente falsificar ou comprometer o fluxo de entrada. Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.

### <a name="respond-with-a-sign-in-action"></a>Responder com uma ação de entrada

Para solicitar que um usuário não autenticado entre, responda com uma ação sugerida do tipo `openUrl` que inclui a URL de autenticação.

#### <a name="response-example-for-a-sign-in-action"></a>Exemplo de resposta para uma ação de logon

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
> Para que a experiência de entrada seja hospedada em um pop-up de equipes, a parte de domínio da URL deve estar na lista de domínios válidos de seu aplicativo. (Consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.)

### <a name="start-the-sign-in-flow"></a>Iniciar o fluxo de entrada

Sua experiência de entrada deve ser responsiva e ajustada em uma janela pop-up. Ele deve se integrar ao [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client), que usa a transmissão de mensagens.

Assim como ocorre com outras experiências incorporadas no Microsoft Teams, seu código dentro da janela precisa `microsoftTeams.initialize()`primeiro chamar. Se o código executar um fluxo OAuth, você poderá passar a ID de usuário do teams para sua janela, o que pode passá-la para a URL de entrada OAuth.

### <a name="complete-the-sign-in-flow"></a>Concluir o fluxo de entrada

Quando a solicitação de entrada é concluída e redireciona de volta para sua página, ela deve executar as seguintes etapas:

1. Gere um código de segurança. (Pode ser um número aleatório.) Você precisa armazenar em cache esse código em seu serviço, junto com as credenciais obtidas por meio do fluxo de entrada (como tokens OAuth 2,0).
2. Chame `microsoftTeams.authentication.notifySuccess` e passe o código de segurança.

Neste ponto, a janela é fechada e o controle é passado para o cliente Teams. Agora, o cliente pode reemitir a consulta de usuário original, juntamente com o código `state` de segurança na propriedade. Seu código pode usar o código de segurança para pesquisar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e concluir a solicitação do usuário.

#### <a name="reissued-request-example"></a>Exemplo de solicitação reemitida

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

