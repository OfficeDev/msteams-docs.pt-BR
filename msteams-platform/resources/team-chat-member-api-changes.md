---
title: Alterações na API de bot para membros da equipe/chat
author: ojasvichoudhary
description: Descreve as alterações futuras e em andamento nas APIs bot usadas para recuperar membros de equipes e chats
keywords: lista de membros da equipe de apis de estrutura de bot
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: ee90c9c324f11e191cf596bcf8e27cd2bef41240
ms.sourcegitcommit: f5ee3fa5ef6126d9bf845948d27d9067b3bbb994
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596179"
---
# <a name="changes-to-teams-bot-apis-for-fetching-team-and-chat-members"></a>Alterações nas APIs de bot do Teams para buscar membros de equipe e chat

>[!NOTE]
> Começamos com o processo de deprecation para `TeamsInfo.getMembers` `TeamsInfo.GetMembersAsync` e APIs. Inicialmente, elas serão fortemente aceleradas para 5 solicitações por minuto e retornarão um máximo de 10 mil membros por equipe. Isso fará com que a lista completa não seja retornada à medida que o tamanho da equipe aumenta. 
> 
> Você deve atualizar para a versão **4.10** ou superior do SDK da Estrutura de Bot e alternar para os pontos de extremidade da API paginada ou para a API de usuário `TeamsInfo.GetMemberAsync` único. Isso também se aplica ao bot mesmo que você não esteja usando diretamente essas APIs, pois os SDKs mais antigos chamam essas APIs durante [eventos membersAdded.](../bots/how-to/conversations/subscribe-to-conversation-events.md#team-members-added) Para exibir a lista de alterações futuras, consulte [ALTERAÇÕES da API](team-chat-member-api-changes.md#api-changes). 

Atualmente, os desenvolvedores de bot que querem recuperar informações para um ou mais membros de um chat ou equipe usam as APIs de bot do Microsoft Teams `TeamsInfo.GetMembersAsync` (para C#) ou `TeamsInfo.getMembers` (para TYPEScript/Node.js) [APIs (documentadas aqui)](../bots/how-to/get-teams-context.md#fetching-the-roster-or-user-profile). Essas APIs têm várias deficiências hoje em dia:

* **Para equipes grandes, o desempenho é ruim e os tempos-de-tempo são mais prováveis.** O tamanho máximo da equipe cresceu consideravelmente desde que o Microsoft Teams foi lançado no início de 2017. Como retorna toda a lista de membros, leva muito tempo para que a chamada da API retorne para equipes grandes, e não é incomum que a chamada tenha tempo de espera e você precisa `GetMembersAsync` / `getMembers` tentar novamente.
* **Obter detalhes de perfil para um único usuário é complicado.** Para obter as informações de perfil de um único usuário, você precisa recuperar toda a lista de membros e pesquisar o que deseja. True, há uma função auxiliar no SDK da Estrutura de Bots para torná-lo mais simples, mas, sob as cobertas, não é eficiente.

Separadamente, com a introdução de equipes em toda a organização, percebemos que era hora de alinhar melhor essas APIs com controles de privacidade do Office 365: os bots usados em equipes grandes são capazes de recuperar informações básicas de perfil, que é semelhante à permissão do `User.ReadBasic.All` Microsoft Graph. Os administradores de locatários têm um grande controle sobre quais aplicativos e bots podem ser usados em seu locatário, mas essas configurações são diferentes das que regem o Microsoft Graph.

Aqui está uma representação JSON de exemplo do que é retornado por essas APIs hoje. Vou fazer referência a alguns dos campos abaixo.

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

Aqui estão as alterações futuras da API:

* Criamos uma nova API para recuperar informações de perfil para [`TeamsInfo.GetPagedMembersAsync`](~/bots/how-to/get-teams-context.md?tabs=dotnet#fetching-the-roster-or-user-profile) membros de um chat/equipe. Essa API agora está disponível com o SDK da Estrutura de Bot 4.10. Para desenvolvimento em todas as outras versões, use o [`GetConversationPagedMembers`](/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true) método.
  > [!NOTE]
  > Em v3 ou v4, a melhor ação é atualizar para a versão de ponto mais recente.
* Criamos uma nova API para recuperar as informações de perfil [`TeamsInfo.GetMemberAsync`](~/bots/how-to/get-teams-context.md?tabs=dotnet#get-single-member-details) de um único usuário. Ele pega a ID da equipe/chat e uma [UPN](https://docs.microsoft.com/windows/win32/ad/naming-properties#userprincipalname) ( , consulte acima `userPrincipalName` ), Azure Active Directory Object ID ( , consulte acima ) ou a ID do usuário do Teams ( , consulte acima ) como parâmetros e retorna as informações de perfil desse  `objectId`  `id` usuário. 
  > [!NOTE]
  > Estamos mudando para corresponder ao que é chamado no objeto `objectId` de uma mensagem da Estrutura de `aadObjectId` `Activity` Bot. A nova API está disponível com a versão 4.10 do SDK da Estrutura de Bots. Ele estará disponível em breve na extensão do Teams SDK Bot Framework 3.x também; Enquanto isso, você pode usar o ponto de extremidade [REST.](~/bots/how-to/get-teams-context.md?tabs=json#get-single-member-details)
* `TeamsInfo.GetMembersAsync` (C#) e (TypeScript/Node.js) é formalmente preterido e vai parar de funcionar no final `TeamsInfo.getMembers` de 2021. Atualize seus bots para usar as APIs paiadas. (Isso também se aplica à [API REST subjacente que essas APIs usam](~/bots/how-to/get-teams-context.md?tabs=json).)
* Até o final de 2021, os bots não poderão recuperar proativamente as propriedades ou para membros de um chat/equipe e precisarão usar o Microsoft Graph para `userPrincipalName` `email` recuperá-las. Especificamente, `userPrincipalName` e as propriedades não serão retornadas da nova API a partir do final de `email` `GetConversationPagedMembers` 2021. Os bots terão que usar o Microsoft Graph com um token de acesso para recuperar essas informações. Obviamente, essa é uma grande mudança: devemos facilitar a aplicação de um token de acesso aos bots e simplificar o processo de consentimento do usuário final.

## <a name="feedback-and-more-information"></a>Comentários e mais informações

Vamos usar esta página para fornecer informações atualizadas sobre essas alterações. Se você tiver dúvidas, use o "Enviar comentários > nesta página" na seção **Comentários** abaixo.
