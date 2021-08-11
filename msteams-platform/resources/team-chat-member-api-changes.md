---
title: Alterações na API de bot para membros da equipe/chat
author: ojasvichoudhary
description: Descreve as alterações futuras e em andamento nas APIs bot usadas para recuperar membros de equipes e chats
keywords: lista de membros da equipe de apis de estrutura de bot
localization_priority: Normal
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: 25d3bdc5c25caec323ab1b45566b485e2c9df9fe78cb0b91f3546fcde7183e02
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57705119"
---
# <a name="teams-bot-api-changes-to-fetch-team-or-chat-members"></a>Teams da API de bot para buscar membros de equipe ou chat

>[!NOTE]
> O processo de deprecation para `TeamsInfo.getMembers` `TeamsInfo.GetMembersAsync` e APIs foi iniciado. Inicialmente, elas são fortemente aceleradas para cinco solicitações por minuto e retornam um máximo de 10 mil membros por equipe. Isso resulta na lista completa não sendo retornada à medida que o tamanho da equipe aumenta.
> Você deve atualizar para a versão 4.10 ou superior do SDK da Estrutura de Bot e alternar para os pontos de extremidade da API paginada ou para a API de usuário `TeamsInfo.GetMemberAsync` único. Isso também se aplica ao bot mesmo que você não use essas APIs diretamente, pois os SDKs mais antigos chamam essas APIs durante [eventos membersAdded.](../bots/how-to/conversations/subscribe-to-conversation-events.md#team-members-added) Para exibir a lista de alterações futuras, consulte [ALTERAÇÕES da API](team-chat-member-api-changes.md#api-changes).

Atualmente, se você deseja recuperar informações para um ou mais membros de um chat ou equipe, pode usar [as APIs](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) de bot Microsoft Teams para C# ou para `TeamsInfo.GetMembersAsync` `TeamsInfo.getMembers` APIs TypeScript ou Node.js. Para obter mais informações, consulte [fetch roster or user profile](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile).

Essas APIs têm as seguintes deficiências:

* Para equipes grandes, o desempenho é ruim e os tempos limite são mais prováveis: o tamanho máximo da equipe aumentou consideravelmente desde Teams foi lançado no início de 2017. Como ou retorna toda a lista de membros, leva muito tempo para a chamada da API retornar para equipes grandes, e é comum que a chamada tenha tempo de espera e você precisa `GetMembersAsync` `getMembers` tentar novamente.
* Obter detalhes de perfil para um único usuário é difícil: para obter as informações de perfil de um único usuário, você precisa recuperar toda a lista de membros e, em seguida, pesquisar o que você deseja. Há uma função auxiliar no SDK da Estrutura de Bots para torná-lo mais simples, mas não é eficiente.

Com a introdução de equipes de toda a organização, há um requisito para alinhar melhor essas APIs com Office 365 de privacidade. Bots usados em equipes grandes são capazes de recuperar informações básicas de perfil semelhantes à `User.ReadBasic.All` permissão microsoft Graph. Os administradores de locatários têm um grande controle sobre quais aplicativos e bots podem ser usados em seus locatários, mas essas configurações são diferentes do Microsoft Graph.

O código a seguir fornece uma representação JSON de exemplo do que é retornado pelas APIs Teams bot:

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

## <a name="api-changes"></a>Alterações na API

A seguir estão as próximas alterações na API:

* Uma nova API é criada [`TeamsInfo.GetPagedMembersAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) para recuperar informações de perfil para membros de um chat ou equipe. Essa API agora está disponível com o SDK da Estrutura de Bots versão 4.8 ou posterior. Para desenvolvimento em todas as outras versões, use o [`GetConversationPagedMembers`](/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true) método.

    > [!NOTE]
    > Em v3 ou v4, a melhor ação é atualizar para a versão de ponto mais recente que é 3.30.2 ou 4.8 ou posterior, respectivamente.

* Uma nova API é criada [`TeamsInfo.GetMemberAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) para recuperar as informações de perfil de um único usuário. Ele pega a ID da equipe ou chat e um [UPN](/windows/win32/ad/naming-properties#userprincipalname) que é , Azure Active Directory ID do objeto , ou a ID do usuário Teams como parâmetros e retorna as informações de perfil para esse `userPrincipalName` `objectId` `id` usuário.

    > [!NOTE]
    > `objectId` é alterado para `aadObjectId` corresponder ao que é chamado no objeto de uma mensagem da Estrutura de `Activity` Bot. A nova API está disponível com a versão 4.8 ou posterior do SDK da Estrutura de Bots. Ele também está disponível no Teams de extensão SDK Bot Framework 3.x. Enquanto isso, você pode usar o ponto de extremidade [REST.](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details)

* `TeamsInfo.GetMembersAsync` no C# e `TeamsInfo.getMembers` em TypeScript ou Node.js está formalmente preterido. Depois que a nova API está disponível, você deve atualizar seus bots para usá-la. Isso também se aplica à [API REST subjacente que essas APIs usam](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json).
* Até o final de 2022, os bots não podem recuperar proativamente as propriedades ou para membros de um `userPrincipalName` `email` chat ou equipe. Os bots devem usar Graph para recuperá-los. As `userPrincipalName` propriedades e não são `email` retornadas da nova API a partir do `GetConversationPagedMembers` final de 2022. Os bots têm que usar Graph com um token de acesso para recuperar informações. Deve ser mais fácil para os bots obterem um token de acesso e simplificarem e simplificarem o processo de consentimento do usuário final.
