---
title: Alterações na API de bot para membros da equipe/chat
author: ojasvichoudhary
description: Neste módulo, aprenda as alterações futuras e em andamento nas APIs de Bot usadas para recuperar membros de equipes e chats
ms.localizationpriority: medium
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: b2e9258975de236116e5b9e33aef4aaf914ec797
ms.sourcegitcommit: 3aaccc48906fc6f6fbf79916af5664bf55537250
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68295953"
---
# <a name="teams-bot-api-changes-to-fetch-team-or-chat-members"></a>Alterações na API do bot do Teams para buscar membros da equipe ou chat

>[!NOTE]
> O processo de descontinuação das APIs `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` foi iniciado. Inicialmente, eles são fortemente limitados a cinco solicitações por minuto e retornam no máximo 10 mil membros por equipe. Isto faz com que a lista completa não seja retornada à medida que o tamanho da equipe aumenta.
> Você deve atualizar para a versão 4.10 ou superior do SDK do Bot Framework e alternar para os pontos de extremidade da API paginada, ou para a API de usuário único `TeamsInfo.GetMemberAsync`. Isso também se aplica ao seu bot, mesmo que você não esteja usando diretamente essas APIs, pois os SDKs mais antigos chamam essas APIs durante os eventos de [membersAdded](../bots/how-to/conversations/subscribe-to-conversation-events.md#members-added). Para ver a lista de alterações futuras, consulte [Alterações da API](team-chat-member-api-changes.md#api-changes).

Atualmente, se você quiser recuperar informações de um ou mais membros de um chat ou equipe, você pode usar as [APIs de bot do Microsoft Teams](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) `TeamsInfo.GetMembersAsync` para C# ou `TeamsInfo.getMembers` para APIs do TypeScript ou Node.js. Para obter mais informações, consulte [buscar a lista ou perfil do usuário](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile).

Estas APIs têm as seguintes deficiências:

* Para grandes equipes, o desempenho é ruim e os tempos limite são mais prováveis: o tamanho máximo da equipe cresceu consideravelmente desde que o Teams foi lançado no início de 2017. Como `GetMembersAsync` ou `getMembers` retorna toda a lista de membros, leva muito tempo para que a chamada à API retorne para equipes grandes, e é comum que a chamada tenha o tempo limite e você tenha que tentar novamente.
* Obter detalhes de perfil para um único usuário é difícil: Para obter as informações de perfil de um único usuário, você precisa recuperar toda a lista de membros e, em seguida, pesquisar por aquela que você deseja. Há uma função auxiliar no SDK do Bot Framework para simplificar, mas não é eficiente.

Com a introdução de equipes de toda a organização, há um requisito para alinhar melhor essas APIs com Office 365 de privacidade. Os bots usados em grandes equipes podem recuperar informações básicas do perfil semelhantes à permissão do `User.ReadBasic.All` Microsoft Graph. Os administradores de locatários têm um grande controle sobre quais aplicativos e bots podem ser usados nos seus locatários, mas essas configurações são diferentes do Microsoft Graph.

O código a seguir fornece um exemplo de representação JSON do que é retornado pelas APIs de bot do Teams:

```json
[{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "name": "Anon1 (Guest)",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47",
 "userRole": "anonymous"
}, {
    "id": "29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk",
    "objectId": "76b0b09f-d410-48fd-993e-84da521a597b",
    "givenName": "John",
    "surname": "Patterson",
    "email": "johnp@fabrikam.com",
    "userPrincipalName": "johnp@fabrikam.com",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47",
 "userRole": "user"
}, {
    "id": "29:1URzNQM1x1PNMr1D7L5_lFe6qF6gEfAbkdG8_BUxOW2mTKryQqEZtBTqDt10-MghkzjYDuUj4KG6nvg5lFAyjOLiGJ4jzhb99WrnI7XKriCs",
    "objectId": "6b7b3b2a-2c4b-4175-8582-41c9e685c1b5",
    "givenName": "Rick",
    "surname": "Stevens",
    "email": "Rick.Stevens@fabrikam.com",
    "userPrincipalName": "rstevens@fabrikam.com",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47",
 "userRole": "user"
}]
```

## <a name="api-changes"></a>Mudanças da API

A seguir estão as próximas alterações na API:

* Uma nova API foi criada [`TeamsInfo.GetPagedMembersAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) para recuperar as informações de perfil de membros de um chat ou equipe. Esta API agora está disponível com o SDK do Bot Framework versão 4.8 ou posterior. Para o desenvolvimento em todas as outras versões, utilize o método [`GetConversationPagedMembers`](/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true).

    > [!NOTE]
    > Na v3 ou na v4, a melhor ação é atualizar para a versão de ponto mais recente que é 3.30.2 ou 4.8 ou posterior, respectivamente.

* Uma nova API foi criada [`TeamsInfo.GetMemberAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) para recuperar as informações de perfil de um único usuário. Ele usa a ID da equipe ou do chat e uma [UPN](/windows/win32/ad/naming-properties#userprincipalname) que é `userPrincipalName`, a ID de objeto do Microsoft Azure Active Directory (Microsoft Azure AD) `objectId` ou a ID do usuário do Teams `id` como parâmetros e retorna as informações de perfil desse usuário.

    > [!NOTE]
    > `objectId` é alterado para `aadObjectId` para corresponder ao que é chamado no objeto `Activity` de uma mensagem do Bot Framework. A nova API está disponível com a versão 4.8 ou posterior do SDK do Bot Framework. Ele também está disponível na extensão do SDK do Teams do Bot Framework 3.x. Enquanto isso, você pode utilizar o ponto de extremidade [REST](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details).

* `TeamsInfo.GetMembersAsync` no C# e `TeamsInfo.getMembers` no TypeScript ou Node.js estão formalmente preteridos. Uma vez que a nova API esteja disponível, você deve atualizar seus bots para utilizá-la. Isso também se aplica à [API REST subjacente que essas APIs usam](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json).
* Até o final de 2022, os bots não poderão recuperar proativamente as propriedades `userPrincipalName` ou `email` para os membros de um chat ou equipe. Os bots devem usar as APIs do Graph para recuperar as informações necessárias. A nova API `GetConversationPagedMembers` não pode retornar as propriedades `userPrincipalName` e `email` do final de 2022. Os bots devem usar a API do Graph com um token de acesso para recuperar informações.

> [!NOTE]
>
> Recomendamos que você use o [API do Graph](/microsoftteams/platform/resources/team-chat-member-api-changes#api-changes) com um token de acesso para recuperar informações.
