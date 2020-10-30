---
title: Alterações de API de bot para membros de equipe/chat (atualização 2020)
author: ojasvichoudhary
description: Descreve as alterações futuras e em andamento das APIs de bot usadas para recuperar membros de equipes e chats
keywords: lista de membros da equipe de APIs da estrutura de bot
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: 243969796d9d1dc427ab7736cf5e0f0d320731c7
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796138"
---
# <a name="changes-to-teams-bot-apis-for-fetching-teamchat-members"></a>Alterações nas APIs de bot do teams para buscar membros da equipe/chat

Atualmente, os desenvolvedores de bot que desejam recuperar informações de um ou mais membros de um chat ou uma equipe usam as APIs do Microsoft Teams bot APIs `TeamsInfo.GetMembersAsync` (para C#) ou `TeamsInfo.getMembers` (para TypeScript/Node.js) [(documentadas aqui)](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetching-the-roster-or-user-profile). Essas APIs têm várias deficiências atuais:

* **Para equipes grandes, o desempenho é ruim e os tempos limites são mais prováveis.** O tamanho máximo da equipe cresceu consideravelmente desde que o Microsoft Teams foi lançado no início de 2017. Como `GetMembersAsync` / `getMembers` retorna toda a lista de membros, ela demora muito para que a chamada de API seja retornada para equipes grandes e não é incomum a chamada para o tempo limite e você precisa tentar novamente.
* **Obter detalhes de perfil para um único usuário é complicado.** Para obter as informações de perfil de um único usuário, você precisa recuperar toda a lista de membros e pesquisar o que desejar. True, há uma função auxiliar no SDK da estrutura de bot para torná-la mais simples, mas nas capas não é eficiente.

Separadamente, com a introdução de equipes de toda a organização, percebemos que era o tempo para alinhar melhor essas APIs com os controles de privacidade do Office 365: os bots usados em grandes equipes podem recuperar informações básicas do perfil, que é semelhante à `User.ReadBasic.All` permissão do Microsoft Graph. Os administradores de locatários têm uma grande quantidade de controle sobre quais aplicativos e bots podem ser usados em seus locatários, mas essas configurações são diferentes das que governam o Microsoft Graph.

Aqui está uma representação JSON de amostra do que é retornado por essas APIs hoje. Consultarei alguns dos campos abaixo.

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
Aqui estão as futuras alterações da API:

* Criamos uma nova API [`TeamsInfo.GetPagedMembersAsync`](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetching-the-roster-or-user-profile) para recuperar informações de perfil para os membros de um chat/equipe. Essa API está agora disponível com o SDK do bot Framework 4,8. Para desenvolvimento em todas as outras versões, use o [`GetConversationPagedMembers`](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable) método. **Observação** : em V3 ou v4, a melhor ação é atualizar para a versão mais recente do ponto (3.30.2 ou 4,8, respectivamente). 
* Criamos uma nova API [`TeamsInfo.GetMemberAsync`](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) para recuperar as informações de perfil de um único usuário. Ele usa a ID do Team/Chat e um [UPN](https://docs.microsoft.com/windows/win32/ad/naming-properties#userprincipalname) ( `userPrincipalName` , *Confira acima* ), a ID de objeto do Azure Active Directory (, confira `objectId` *acima* ) ou a ID de usuário do Microsoft Teams ( `id` , *Confira acima* ) como parâmetros e retorna as informações de perfil desse usuário. **Observação** : estamos mudando `objectId` para `aadObjectId` coincidir o que é chamado no `Activity` objeto de uma mensagem da estrutura de bot. A nova API está disponível com a versão 4,8 do SDK da estrutura do bot. Em breve, ele estará disponível na estrutura de bot de extensão do SDK do teams 3. x também; enquanto você pode usar o ponto de extremidade [REST](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details) .
* `TeamsInfo.GetMembersAsync` (C#) e `TeamsInfo.getMembers` (TypeScript/Node.js) é formalmente preterida e deixará de funcionar no tarde 2021. Anunciaremos um cronograma específico em maio de 2020, com base nos comentários dos desenvolvedores. Depois que a nova API paginável estiver disponível, os desenvolvedores devem atualizar seus bots para usá-la. (Isso também se aplica à [API REST subjacente que essas APIs usam](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json).)
* No final de 2021, os bots não poderão recuperar proativamente as `userPrincipalName` Propriedades ou os `email` membros de um chat/equipe e precisarão usar o Microsoft Graph para recuperá-los. Especificamente, `userPrincipalName` e `email` as propriedades não serão retornadas da nova `GetConversationPagedMembers` API a partir da última 2021. Os bots terão que usar o Microsoft Graph com um token de acesso para recuperar essas informações. Isso é obviamente uma alteração importante: devemos facilitar para os bots a obter um token de acesso, e devemos simplificar e simplificar o processo de consentimento do usuário final.

## <a name="feedback-and-more-information"></a>Comentários e mais informações
Usaremos essa página para fornecer informações atualizadas sobre essas alterações. Se você tiver dúvidas, use o "enviar comentários > nesta página" na seção **comentários** abaixo. 
