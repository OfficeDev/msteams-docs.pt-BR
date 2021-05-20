---
title: Alterações na API de bot para membros da equipe/chat
author: ojasvichoudhary
description: Descreve as próximas e em andamento as APIs bot usadas para recuperar membros de equipes e chats
keywords: lista de membros da equipe de apis da estrutura bot
localization_priority: Normal
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: 333a29664f0d60e89039f906fce77e71054d486f
ms.sourcegitcommit: 9ef3b415cbba484c2201abe9c6927e08d974388e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52555434"
---
# <a name="teams-bot-api-changes-to-fetch-team-or-chat-members"></a>Teams a API de bot muda para buscar membros da equipe ou do chat

>[!NOTE]
> O processo de depreciação `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` APIs já começaram. Inicialmente, eles são fortemente estrangulados a cinco pedidos por minuto e retornam um máximo de 10K membros por equipe. Isso resulta na escalação completa não sendo devolvida à medida que o tamanho da equipe aumenta.
> Você deve atualizar para a versão 4.10 ou superior do Bot Framework SDK e mudar para os pontos finais de API paginados ou para a `TeamsInfo.GetMemberAsync` API do usuário único. Isso também se aplica ao seu bot, mesmo que você não esteja usando diretamente essas APIs, já que os SDKs mais antigos chamam essas APIs durante os eventos [adicionados.](../bots/how-to/conversations/subscribe-to-conversation-events.md#team-members-added) Para visualizar a lista de alterações futuras, consulte [alterações de API](team-chat-member-api-changes.md#api-changes). 

Atualmente, desenvolvedores de bots que desejam recuperar informações para um ou mais membros de um chat ou equipe usam as APIs de bot Microsoft Teams `TeamsInfo.GetMembersAsync` para C# ou `TeamsInfo.getMembers` para APIs TypeScript ou Node.js. Para obter mais informações, consulte [lista de busca ou perfil de usuário](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile). Essas APIs têm várias deficiências.

Atualmente, se você quiser recuperar informações para um ou mais membros de um chat ou equipe, você pode usar as [APIs de bot Microsoft Teams](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) `TeamsInfo.GetMembersAsync` para C# ou para `TeamsInfo.getMembers` APIs TypeScript ou Node.js. Essas APIs têm as seguintes deficiências:

* Para equipes grandes, o desempenho é ruim e os tempos limite são mais prováveis: o tamanho máximo da equipe cresceu consideravelmente desde que Teams foi lançado no início de 2017. Como `GetMembersAsync` ou retorna toda a lista de `getMembers` membros, leva muito tempo para a chamada da API retornar para grandes equipes, e é comum que a chamada para o tempo fora e você tem que tentar novamente.
* Obter detalhes do perfil para um único usuário é difícil: Para obter as informações do perfil para um único usuário, você tem que recuperar toda a lista de membros e, em seguida, procurar o que você deseja. Há uma função de ajudante no Bot Framework SDK para torná-lo mais simples, mas não é eficiente.

Com a introdução de equipes de organização ampla, há um requisito para alinhar melhor essas APIs com Office 365 controles de privacidade. Bots usados em grandes equipes são capazes de recuperar informações básicas de perfil semelhantes à `User.ReadBasic.All` permissão de Graph da Microsoft. Os administradores de inquilinos têm um grande controle sobre quais aplicativos e bots podem ser usados em seu inquilino, mas essas configurações são diferentes da Microsoft Graph.

O código a seguir fornece uma representação JSON amostra do que é devolvido por Teams apis bot:

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

## <a name="api-changes"></a>Alterações da API

A seguir, as próximas alterações da API:

* Uma nova API é criada [`TeamsInfo.GetPagedMembersAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) para recuperar informações de perfil para membros de um chat ou equipe. Esta API já está disponível com o Bot Framework versão 4.8 ou posterior SDK. Para desenvolvimento em todas as outras versões, use o [`GetConversationPagedMembers`](/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true) método.

    > [!NOTE]
    > Em v3 ou v4, a melhor ação é atualizar para a versão de ponto mais recente que é 3.30.2 ou 4.8 ou posterior, respectivamente.

* Uma nova API é criada [`TeamsInfo.GetMemberAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) para recuperar as informações do perfil de um único usuário. Ele pega o ID da equipe ou chat e uma [UPN](/windows/win32/ad/naming-properties#userprincipalname) que é `userPrincipalName` , Azure Active Directory Object ID , ou o `objectId` Teams ID do usuário como `id` parâmetros e retorna as informações do perfil para esse usuário.

    > [!NOTE]
    > `objectId` é alterado `aadObjectId` para corresponder ao que é chamado no `Activity` objeto de uma mensagem Bot Framework. A nova API está disponível com a versão 4.8 ou posterior do Bot Framework SDK. Também está disponível no Teams extensão SDK Bot Framework 3.x. Enquanto isso, você pode usar o ponto final [REST.](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details)

* `TeamsInfo.GetMembersAsync` em C# e `TeamsInfo.getMembers` no TypeScript ou Node.js é formalmente preterido. Uma vez que a nova API esteja disponível, você deve atualizar seus bots para usá-la. Isso também se aplica à [API REST subjacente que essas APIs usam.](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json)
* Até o final de 2021, os bots não podem recuperar proativamente as `userPrincipalName` propriedades ou para membros de um chat ou `email` equipe. Os bots devem usar Graph para recuperá-los. As `userPrincipalName` propriedades `email` não retornam da nova API a partir do `GetConversationPagedMembers` final de 2021. Os bots têm que usar Graph com um token de acesso para recuperar informações. Deve ser mais fácil para os bots obter um token de acesso e simplificar e simplificar o processo de consentimento do usuário final.
