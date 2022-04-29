---
title: Adicionar autenticação à sua extensão de mensagens
author: surbhigupta
description: Saiba como adicionar autenticação a uma extensão de mensagem usando amostra e exemplos de código
ms.localizationpriority: high
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 1aa64241c85617bec9a116ab3ff9357b93bd2c44
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111602"
---
# <a name="add-authentication-to-your-message-extension"></a>Adicionar autenticação à sua extensão de mensagens

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a>Identifique o usuário

Cada solicitação aos seus serviços inclui a ID de usuário, o nome de exibição do usuário e a ID do objeto do Azure Active Directory.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Os valores `id` e `aadObjectId` são garantidos para o usuário autenticado do Teams. Eles são usados como chaves para pesquisar as credenciais ou qualquer estado armazenado em cache em seu serviço. Além disso, cada solicitação contém a ID do locatário do Azure Active Directory, que é usada para identificar a organização do usuário. Se aplicável, a solicitação também conterá a ID da equipe e a ID do canal dos quais a solicitação é originada.

## <a name="authentication"></a>Autenticação

Se o serviço exigir autenticação de usuário, os usuários deverão entrar antes de usarem a extensão de mensagem. As etapas de autenticação são semelhantes às de um bot ou guia. A sequência é a seguinte:

1. O usuário emite uma consulta ou a consulta padrão é enviada automaticamente ao seu serviço.
1. O serviço verifica se o usuário é autenticado inspecionando a ID de usuário do Teams.
1. Se o usuário não estiver autenticado, envie uma resposta `auth` com uma ação sugerida `openUrl` incluindo a URL de autenticação.
1. O cliente do Microsoft Teams inicia uma caixa de diálogo que hospeda sua página da Web usando a URL de autenticação fornecida.
1. Depois que o usuário entrar, você deverá fechar a janela e enviar um **código de autenticação** para o cliente do Teams.
1. Em seguida, o cliente do Teams emiti novamente a consulta ao seu serviço, que inclui o código de autenticação passado na Etapa 5.

O serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5. Isso garante que um usuário mal-intencionado não tente falsificar ou comprometer o fluxo de entrada. Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.

### <a name="respond-with-a-sign-in-action"></a>Responda com uma ação de entrada

Para solicitar que um usuário não autenticado entre, responda com uma ação sugerida do tipo `openUrl` que inclui a URL de autenticação.

#### <a name="response-example-for-a-sign-in-action"></a>Exemplo de resposta para uma ação de entrada

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
>
> * Para que a experiência de entrada seja hospedada em uma janela pop-up do Teams, a parte do domínio da URL deve estar na lista de domínios válidos do seu aplicativo. Para obter mais informações, confira [validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.
> * O tamanho do pop-up de autenticação pode ser definido incluindo parâmetros da cadeia de caracteres de consulta de largura e altura, `Value = $"{_siteUrl}/searchSettings.html?settings={escapedSettings}",`.

### <a name="start-the-sign-in-flow"></a>Inicie o fluxo de entrada

Sua experiência de entrada deve ser responsiva e se encaixar em uma janela pop-up. Ela deve se integrar ao [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client), que usa a passagem de mensagens.

Assim como com outras experiências inseridas em execução no Microsoft Teams, o código dentro da janela precisa primeiro chamar `microsoftTeams.initialize()`. Se o código executar um fluxo OAuth, você poderá passar a ID de usuário do Teams para sua janela, que a passa para a URL de entrada do OAuth.

### <a name="complete-the-sign-in-flow"></a>Conclua o fluxo de entrada

Quando a solicitação de entrada for concluída e redirecionada de volta para sua página, ela deverá executar as seguintes etapas:

1. Gerar um código de segurança, um número aleatório. Você deve armazenar esse código em cache em seu serviço, juntamente com as credenciais obtidas por meio do fluxo de entrada, como tokens OAuth 2.0.
1. Chamar `microsoftTeams.authentication.notifySuccess` e passar o código de segurança.

Nesse ponto, a janela é fechada e o controle é passado para o cliente do Teams. O cliente agora emiti novamente a consulta do usuário original, juntamente com o código de segurança na propriedade `state`. Seu código pode usar o código de segurança para pesquisar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e, em seguida, concluir a solicitação do usuário.

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

## <a name="code-sample"></a>Exemplo de código

|**Nome de exemplo** | **Descrição** |**.NET** | **Node.js**|
|----------------|-----------------|--------------|----------------|
|Extensões de mensagem – autenticação e configuração | Uma Extensão de Mensagem que tem uma página de configuração aceita as solicitações de pesquisa e retorna resultados depois que o usuário se conectar. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)|[Exibir](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)|

## <a name="see-also"></a>Confira também

[Suporte de logon único (SSO) para extensões de mensagem](~/messaging-extensions/how-to/enable-sso-auth-me.md)
