---
title: Criar aplicativos para usuário anônimo
author: v-sdhakshina
description: Saiba como criar aplicativos para usuários anônimos e testar a experiência entregue aos usuários anônimos em aplicativos de reunião com todas as configurações de administrador.
ms.topic: conceptual
ms.author: v-sdhakshina
ms.localizationpriority: medium
ms.openlocfilehash: ff897c5135740557e12898e7e5d231557b2e2823
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615389"
---
# <a name="build-apps-for-anonymous-users"></a>Criar aplicativos para usuários anônimos

Você pode criar bots, extensões de mensagens, cartões e módulos de tarefa em seu aplicativo para interagir com participantes anônimos da reunião.

Para testar a experiência do aplicativo para usuários anônimos, selecione a URL no convite da reunião e ingresse na reunião em uma janela privada do navegador.

## <a name="admin-setting-for-anonymous-user-app-interaction"></a>Administração configuração para interação de aplicativo de usuário anônimo

Os administradores do Teams podem usar o portal de administração para habilitar ou desabilitar a interação do aplicativo de usuário anônimo para todo o locatário. Essa configuração é habilitada por padrão. Para obter mais informações, consulte [permitir que usuários anônimos interajam com aplicativos em reuniões](/microsoftteams/meeting-settings-in-teams).

## <a name="in-meeting-getcontext-from-teams-client-sdk"></a>In-Meeting getContext do SDK do cliente teams

Os aplicativos recebem as informações a seguir para um usuário anônimo quando chamam `getContext` a API do estágio de aplicativo compartilhado. Você pode reconhecer usuários anônimos verificando um valor `userLicenseType` **desconhecido.**

```csharp
"userObjectId": "8:anon:<GUID1>",
"userLicenseType": "Unknown",
"loginHint": "8:teamsvisitor:<ID>",
"userPrincipalName": "8:teamsvisitor:<ID>",
"tid": "<meeting organizer tenant ID>"
```

| **Nome da propriedade** | **Descrição** |
| --- | --- |
| `userObjectId` | Valor gerado exclusivo para o usuário anônimo. Esse valor não pode ser usado em chamadas para APIs do Graph. |
| `userLicenseType` | `Unknown`, representa o usuário anônimo. |
| `loginHint` | Valor gerado exclusivo. Esse valor não pode ser usado como uma dica em fluxos de logon. |
| `userPrincipalName` | Valor gerado exclusivo. Esse valor não pode ser usado em chamadas para APIs do Graph. |
| `tid` | ID do locatário do organizador da reunião. |

> [!NOTE]
> Quando um usuário anônimo ingressa em uma reunião, uma nova ID de usuário é gerada. Sempre que o usuário anônimo ingressar novamente em uma reunião, uma ID de usuário diferente será gerada.

## <a name="bot-activities-and-apis"></a>Atividades e APIs do bot

Com algumas diferenças, as atividades enviadas ao bot e as respostas que ele recebe das APIs de bot são consistentes entre os participantes anônimos e não anônimos da reunião. Em geral:

* A ID de usuário é um valor gerado que é diferente sempre que o usuário anônimo ingressa na reunião.
* A `aadObjectId` propriedade é omitida.
* A `userRole` propriedade é definida como **anônima**.
* A ID de locatário fornecida é definida como a ID de locatário do organizador da reunião.

### <a name="get-members-and-get-single-member-apis"></a>Obter membros e obter APIs de membro único

Os [membros get e](/microsoftteams/platform/bots/how-to/get-teams-context#fetch-the-roster-or-user-profile) obter APIs [de membro](/microsoftteams/platform/bots/how-to/get-teams-context#get-single-member-details) único retornam informações limitadas para usuários anônimos:

```json
{ 
  "id": "<GUID1>", 
  "name": "<AnonTest (Guest)>",  
  "tenantId": "<GUID2>", 
  "userRole": "anonymous" 
} 
```

| **Nome da propriedade** | **Descrição** |
| --- | --- |
| `id` | Valor gerado exclusivo para o usuário anônimo. |
| `name` | Nome fornecido pelo usuário anônimo ao ingressar na reunião. |
| `tenantId` | ID do locatário do organizador da reunião. |
| `userRole` | `anonymous`, representa o usuário anônimo. |

> [!NOTE]
> A ID recebida das APIs de bot e a API do SDK do cliente do Teams não são as mesmas.

### <a name="conversationupdate-activity-membersadded-and-membersremoved"></a>Atividade ConversationUpdate MembersAdded e MembersRemoved

```csharp
{ 
  "membersAdded": [ 
    { 
      "id": "<GUID1>" 
    } 
  ], 
  "type": "conversationUpdate", 
  "timestamp": "<timestamp>", 
  "id": "<event unique identifier>", 
  "channelId": "msteams", 
  "serviceUrl": "<serviceURL>", 
  "from": { 
    "id": "<GUID2>" 
  }, 
  "conversation": { 
    "isGroup": true, 
    "tenantId": "<tenant id>", 
    "id": "<conversation id>" 
  }, 
  "recipient": { 
    "id": "<bot id>", 
    "name": "<bot name>" 
  }, 
  "channelData": { 
    "tenant": { 
      "id": "<tenant id>" 
    }, 
    "source": null, 
    "meeting": { 
      "id": "<meeting id>" 
    } 
  } 
} 
```

| **Nome da propriedade** | **Descrição** |
| --- | --- |
| `membersAdded.id` | ID de usuário anônimo. |
| `from.id` | ID do organizador da reunião. |
| `conversation.tenantId` | ID do locatário do organizador da reunião. |
| `conversation.id` | ID da conversa do chat da reunião. |
| `tenant.id` | ID do locatário do organizador da reunião. |

Alterações semelhantes se aplicam ao `membersRemoved` conteúdo da atividade.

> [!NOTE]
>
> Quando um usuário anônimo ingressa ou sai de uma reunião, `from` o objeto no conteúdo sempre tem a ID do organizador da reunião, mesmo que a ação tenha sido executada por outra pessoa.

### <a name="create-conversation-api"></a>Criar API de Conversa

Os bots não têm permissão para iniciar uma conversa um-para-um com um usuário anônimo. Se um bot chamar a API Criar Conversa com a ID de usuário de um usuário anônimo, ele receberá um código de status de Solicitação Incorreta e a `400` seguinte resposta de erro:

```csharp
{ 
  "error": {
    "code": "BadArgument",
    "message": "Bot cannot create a conversation with an anonymous user"
  }
} 
```

### <a name="adaptive-cards"></a>Cartões adaptáveis

Os usuários anônimos podem exibir e interagir com Cartões Adaptáveis no chat da reunião. As ações de cartão adaptável se comportam da mesma maneira para usuários anônimos e não anônimos. Para obter mais informações, consulte [Ações de cartão](/microsoftteams/platform/task-modules-and-cards/cards/cards-actions?tabs=json).

## <a name="known-issues-and-limitations"></a>Limitações e problemas conhecidos

* As guias do painel lateral e as bolhas de conteúdo não estão disponíveis para usuários anônimos. Os usuários anônimos ainda podem ver o conteúdo do aplicativo compartilhado para o estágio da reunião.

* Para um usuário anônimo, a ID de usuário e `getContext` a ID de usuário recebidas pelo bot são diferentes. Não é possível correlacionar os dois diretamente. Se você precisar acompanhar a identidade do usuário entre a guia e o bot, deverá solicitar que o usuário se autentique com um provedor de identidade externo.

* Os usuários anônimos verão um ícone de aplicativo genérico em cartões e mensagens de bot, em vez do ícone real do aplicativo. Por exemplo:

    :::image type="content" source="../assets/images/apps-in-meetings/app-icon.png" alt-text="Esta captura de tela mostra como o ícone do aplicativo é exibido para o usuário anônimo.":::

## <a name="see-also"></a>Confira também

* [Criar aplicativos para o estágio de reunião do Teams](build-apps-for-teams-meeting-stage.md)
* [APIs de aplicativos de reunião](meeting-apps-apis.md)
* [Como os bots do Microsoft Teams funcionam](/azure/bot-service/bot-builder-basics-teams)
