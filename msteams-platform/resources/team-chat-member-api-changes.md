---
title: Alterações na API de bot para membros da equipe/chat
author: ojasvichoudhary
description: Descreve as alterações futuras e em andamento nas APIs de Bot usadas para recuperar membros de equipes e chats
keywords: lista de membros da equipe de APIS do bot Framework
ms.localizationpriority: medium
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: dfa85832fe8225b58e4566ba889c23d2696807e4
ms.sourcegitcommit: 61003a14e8a179e1268bbdbd9cf5e904c5259566
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64737206"
---
# <a name="teams-bot-api-changes-to-fetch-team-or-chat-members"></a>Teams api do bot para buscar membros da equipe ou chat

>[!NOTE]
> O processo de substituição para `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` APIs foi iniciado. Inicialmente, eles são fortemente limitados a cinco solicitações por minuto e retornam um máximo de 10 mil membros por equipe. Isso faz com que a lista completa não seja retornada à medida que o tamanho da equipe aumenta.
> Você deve atualizar para a versão 4.10 ou superior do SDK do Bot Framework e alternar para os pontos de extremidade da API paginada ou `TeamsInfo.GetMemberAsync` para a API de usuário único. Isso também se aplica ao bot mesmo que você não esteja usando diretamente essas APIs, pois os SDKs mais antigos chamam essas APIs durante [eventos membersAdded](../bots/how-to/conversations/subscribe-to-conversation-events.md#team-members-added) . Para exibir a lista de alterações futuras, consulte as [alterações de API](team-chat-member-api-changes.md#api-changes).

No momento, se você quiser recuperar informações para um ou mais membros de um chat ou equipe, poderá usar as APIs de bot do Microsoft Teams para C# `TeamsInfo.getMembers` ou [apIs](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) `TeamsInfo.GetMembersAsync` typeScript ou Node.js. Para obter mais informações, consulte [a lista de busca ou o perfil do usuário](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile).

Essas APIs têm as seguintes deficiências:

* Para equipes grandes, o desempenho é ruim e os tempos limite são mais prováveis: o tamanho máximo da equipe aumentou consideravelmente desde Teams foi lançado no início de 2017. Como `GetMembersAsync` ou `getMembers` retorna toda a lista de membros, leva muito tempo para que a chamada à API retorne para equipes grandes, e é comum que a chamada tenha tempo limite e você tenha que tentar novamente.
* É difícil obter detalhes de perfil para um único usuário: para obter as informações de perfil de um único usuário, você precisa recuperar toda a lista de membros e, em seguida, pesquisar o que deseja. Há uma função auxiliar no SDK do Bot Framework para simplificar, mas não é eficiente.

Com a introdução de equipes de toda a organização, há um requisito para alinhar melhor essas APIs com Office 365 de privacidade. Os bots usados em equipes grandes são capazes de recuperar informações básicas de perfil semelhantes à permissão `User.ReadBasic.All` do Microsoft Graph. Os administradores de locatários têm muito controle sobre quais aplicativos e bots podem ser usados em seu locatário, mas essas configurações são diferentes do Microsoft Graph.

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

## <a name="api-changes"></a>Alterações de API

A seguir estão as alterações futuras da API:

* Uma nova API é criada [`TeamsInfo.GetPagedMembersAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) para recuperar informações de perfil para membros de um chat ou equipe. Essa API agora está disponível com o SDK do Bot Framework versão 4.8 ou posterior. Para desenvolvimento em todas as outras versões, use o [`GetConversationPagedMembers`](/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true) método.

    > [!NOTE]
    > Na v3 ou v4, a melhor ação é atualizar para a versão de ponto mais recente, que é 3.30.2 ou 4.8 ou posterior, respectivamente.

* Uma nova API é criada [`TeamsInfo.GetMemberAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) para recuperar as informações de perfil de um único usuário. Ele usa a ID da equipe ou chat e um [UPN](/windows/win32/ad/naming-properties#userprincipalname)`userPrincipalName`, ou seja, a ID de objeto do Microsoft Azure Active Directory (Azure AD) ou a ID `objectId``id` de usuário do Teams como parâmetros e retorna as informações de perfil para esse usuário.

    > [!NOTE]
    > `objectId` é alterado para `aadObjectId` corresponder ao que é chamado no objeto `Activity` de uma mensagem do Bot Framework. A nova API está disponível com a versão 4.8 ou posterior do SDK do Bot Framework. Ele também está disponível na extensão Teams SDK do Bot Framework 3.x. Enquanto isso, você pode usar o ponto [de extremidade REST](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details) .

* `TeamsInfo.GetMembersAsync` em C# e `TeamsInfo.getMembers` em TypeScript ou Node.js foi formalmente preterido. Depois que a nova API estiver disponível, você deverá atualizar seus bots para usá-la. Isso também se aplica à [API REST subjacente que essas APIs usam](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json).
* Até o final de 2022, os bots `userPrincipalName` `email` não podem recuperar proativamente as propriedades ou os membros de um chat ou equipe. Os bots devem usar as APIs Graph para recuperar a imformação necessária. A nova `GetConversationPagedMembers` API não pode retornar as propriedades `userPrincipalName` do `email` final de 2022. Os bots devem usar API do Graph com um token de acesso para recuperar informações. 
