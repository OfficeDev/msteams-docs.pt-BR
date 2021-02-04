---
title: Usar o Microsoft Graph para importar mensagens de plataforma externa para o Teams
description: Descreve como usar o Microsoft Graph para importar mensagens de uma plataforma externa para o Teams
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: teams import messages api graph microsoft migrate migration post
ms.openlocfilehash: 97f24c34ebb825aad0fd104c9a814e46f9b5fa0d
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093257"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a>Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph

>[!IMPORTANT]
> As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários. Embora esta versão tenha passado por testes extensos, ela não foi destinada ao uso na produção.

Com o Microsoft Graph, você pode migrar o histórico de mensagens e os dados existentes dos usuários de um sistema externo para um canal do Teams. Ao habilitar a recriação de uma hierarquia de mensagens da plataforma de terceiros dentro do Teams, os usuários podem continuar suas comunicações de maneira perfeita e continuar sem interrupção.

## <a name="import-overview"></a>Visão geral da importação

Em um nível alto, o processo de importação consiste do seguinte:

1. [Criar uma equipe com um back-in-timestamp](#step-one-create-a-team)
1. [Criar um canal com um back-in-timestamp](#step-two-create-a-channel)  
1. [Importar mensagens internas e externas no tempo](#step-three-import-messages)
1. [Concluir o processo de migração de equipe e canal](#step-four-complete-migration-mode)
1. [Adicionar membros da equipe](#step-five-add-team-members)

## <a name="necessary-requirements"></a>Requisitos necessários

### <a name="analyze-and-prepare-message-data"></a>Analisar e preparar dados de mensagens

✔ revise os dados de terceiros para decidir o que será migrado.  
✔ Extraia os dados selecionados do sistema de chat de terceiros.  
✔ mapear a estrutura de chat de terceiros para a estrutura do Teams.  
✔ converter dados de importação no formato necessário para a migração.  

### <a name="set-up-your-office-365-tenant"></a>Configurar seu locatário do Office 365

✔ verifique se existe um locatário do Office 365 para os dados de importação. Para obter mais informações sobre como configurar uma locação do Office 365 para o *Teams,* confira , Preparar seu [locatário do Office 365.](../../concepts/build-and-test/prepare-your-o365-tenant.md)  
✔ se os membros da equipe estão no Azure Active Directory (AAD).  Para saber *mais, confira* [Adicionar um novo usuário](/azure/active-directory/fundamentals/add-users-azure-active-directory) ao Azure Active Directory.

## <a name="step-one-create-a-team"></a>Etapa um: criar uma equipe

Como os dados existentes estão sendo migrados, manter os dados de data/hora originais da mensagem e impedir a atividade de mensagens durante o processo de migração é fundamental para recriar o fluxo de mensagens existente do usuário no Teams. Isso é feito da seguinte forma:

> [Crie uma nova equipe](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um back-in-timestamp usando a propriedade de recurso da  `createdDateTime`  equipe. Coloque a nova equipe em , um estado especial que barra os usuários da maioria das atividades dentro da equipe até `migration mode` que o processo de migração seja concluído. Inclua o `teamCreationMode` atributo instance com o valor na `migration` solicitação POST para identificar explicitamente a nova equipe como sendo criada para migração.  

> **OBSERVAÇÃO:** `createdDateTime` o campo só será preenchido para instâncias de uma equipe ou canal que foram migradas.

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a>Permissões

|ScopeName|DisplayName|Descrição|Tipo|Consentimento do administrador?|Entidades/APIs cobertas|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Gerenciar a migração do Microsoft Teams|Criando, gerenciando recursos para migração para o Microsoft Teams|**Somente aplicativo**|**Sim**|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a>Solicitar (criar uma equipe no estado de migração)

```http
POST https://graph.microsoft.com/beta/teams

Content-Type: application/json
{
  "@microsoft.graph.teamCreationMode": "migration",
  "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('standard')",
  "displayName": "My Sample Team",
  "description": "My Sample Team’s Description",
  "createdDateTime": "2020-03-14T11:22:17.043Z"
}
```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 202 Accepted
Location: /teams/{teamId}/operations/{operationId}
Content-Location: /teams/{teamId}
```

#### <a name="error-messages"></a>Mensagens de erro

```http
400 Bad Request
```

* `createdDateTime`  definido para o futuro.
* `createdDateTime`  corretamente especificado, mas `teamCreationMode`  o atributo instance está ausente ou definido como valor inválido.

## <a name="step-two-create-a-channel"></a>Etapa dois: Criar um canal

Criar um canal para as mensagens importadas é semelhante ao cenário de criação de equipe:

> [Crie um novo canal com](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) um back-in-timestamp usando a propriedade de recurso de `createdDateTime` canal. Coloque o novo canal em , um estado especial que barra os usuários da maioria das atividades de chat dentro do canal até `migration mode` que o processo de migração seja concluído.  Inclua o `channelCreationMode` atributo instance com o valor na `migration` solicitação POST para identificar explicitamente a nova equipe como sendo criada para migração.  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a>Permissões

|ScopeName|DisplayName|Descrição|Tipo|Consentimento do administrador?|Entidades/APIs cobertas|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Gerenciar a migração do Microsoft Teams|Criando, gerenciando recursos para migração para o Microsoft Teams|**Somente aplicativo**|**Sim**|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a>Solicitar (criar um canal no estado de migração)

```http
POST https://graph.microsoft.com/beta/teams/{id}/channels

Content-Type: application/json
{
  "@microsoft.graph.channelCreationMode": "migration",
  "displayName": "Architecture Discussion",
  "description": "This channel is where we debate all future architecture plans",
  "membershipType": "standard",
  "createdDateTime": "2020-03-14T11:22:17.047Z"
}
```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 202 Accepted

{
   "@odata.context":"https://canary.graph.microsoft.com/testprodbetateamsgraphsvcncus/$metadata#teams('9cc6d6ab-07d8-4d14-bc2b-7db8995d6d23')/channels/$entity",
   "id":"19:e90f6814ce674072a4126206e7de485e@thread.tacv2",
   "createdDateTime":null,
   "displayName":"Architecture Discussion",
   "description":"This channel is where we debate all future architecture plans",
   "isFavoriteByDefault":null,
   "email":null,
   "webUrl":null,
   "membershipType":null,
   "moderationSettings":null
}
```

#### <a name="error-message"></a>Mensagem de erro

```http
400 Bad Request
```

* `createdDateTime`  definido para o futuro.
* `createdDateTime`  especificado corretamente, mas `channelCreationMode`  o atributo instance está ausente ou definido como um valor inválido.

## <a name="step-three-import-messages"></a>Etapa três: Importar mensagens

Depois que a equipe e o canal foram criados, você pode começar a enviar mensagens de back-in-time usando as chaves no `createdDateTime` `from`  corpo da solicitação. **OBSERVAÇÃO:** não há suporte `createdDateTime` para mensagens importadas com o thread de `createdDateTime` mensagens anteriores ao thread.

> [!NOTE]
> * `createdDateTime` deve ser exclusivo em todas as mensagens no mesmo thread.
> * `createdDateTime` dá suporte a timestamps com precisão de milissegundos. Por exemplo, se a mensagem de solicitação de entrada tiver o valor definido como `createdDateTime` *2020-09-16T05:50:31.0025302Z,* ela será convertida em *2020-09-16T05:50:31.002Z* quando a mensagem for ingerida.

#### <a name="request-post-message-that-is-text-only"></a>Request (POST message that is text-only)

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/messages

{
   "createdDateTime":"2019-02-04T19:58:15.511Z",
   "from":{
      "user":{
         "id":"id-value",
         "displayName":"Joh Doe",
         "userIdentityType":"aadUser"
      }
   },
   "body":{
      "contentType":"html",
      "content":"Hello World"
   }
}
```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 200 OK

{
   "@odata.context":"https://graph.microsoft.com/beta/$metadata#teams('teamId')/channels('channelId')/messages/$entity",
   "id":"id-value",
   "replyToId":null,
   "etag":"id-value",
   "messageType":"message",
   "createdDateTime":"2019-02-04T19:58:15.58Z",
   "lastModifiedDateTime":null,
   "deleted":false,
   "subject":null,
   "summary":null,
   "importance":"normal",
   "locale":"en-us",
   "policyViolation":null,
   "from":{
      "application":null,
      "device":null,
      "conversation":null,
      "user":{
         "id":"id-value",
         "displayName":"Joh Doe",
         "userIdentityType":"aadUser"
      }
   },
   "body":{
      "contentType":"html",
      "content":"Hello World"
   },
   "attachments":[
   ],
   "mentions":[
   ],
   "reactions":[
   ]
}
```

#### <a name="error-messages"></a>Mensagens de erro

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a>Solicitar (POSTAR uma mensagem com imagem em linha)

> **Observação:** não há escopos de permissão especiais neste cenário, pois a solicitação faz parte do chatMessage; os escopos de chatMessage também se aplicam aqui.

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/messages

{
  "body": {
        "contentType": "html",
        "content": "<div><div>\n<div><span><img height=\"250\" src=\"../hostedContents/1/$value\" width=\"176.2295081967213\" style=\"vertical-align:bottom; width:176px; height:250px\"></span>\n\n</div>\n\n\n</div>\n</div>"
    },
    "hostedContents":[
        {
            "@microsoft.graph.temporaryId": "1",
            "contentBytes": "iVBORw0KGgoAAAANSUhEUgAAANcAAAExCAYAAADvFzeeAAAXjklEQVR4Ae2d/XNU1RnH+9e0FFrA0RCIyaS8hRA0HV5KbS1gHRgVpjMClY4GHJ3yYm1HCmXaWttaaZUZtIIFKYi8lFAkvOQ9u5vN225IARVBbX9/Os9NbrLZbMjmhCfJPX5+2Lmb3T25y3O+n/M599x7w9f+++UXwoMakIF7n4GvUdR7X1RqSk01A8CFuZm5GGUAuIwKi72wF3ABF+YyygBwGRUWc2Eu4AIuzGWUAeAyKizmwlzABVyYyygDwGVUWMyFuYALuDCXUQaAy6iwmAtzARdwfWXMdeuzT+TGxz3Sfb1LunrapL07IW3pePDQ5/qavqef0c+OdYAELuAac4jGGkLL9rdvfyo9N9ODQAqBGmmrwGlb/R0u3xG4gMspOC5hG882CoRaaCSA8n1ff9doIQMu4PIOrus3u+8ZVNnw6e/Od5AALuDKOyz5hmqiPnfnzi1J9bSbgRWCpvvQfY307wQu4BoxJCOFaDK8rwsQmQsUIQhWW93XSIsewAVckYdLQ24F0Ui/926AARdwRRounZ6Np7GyYdN9DzdFBC7gijRc43GMlQ1U9s/6HXJNjYELuHI<<-----Removed----->>>>",
            "contentType": "image/png"
        }
    ]
}
```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 200 OK

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#teams('teamId')/channels('channelId')/messages/$entity",
    "id": "id-value",
    "replyToId": null,
    "etag": "id-value",
    "messageType": "message",
    "createdDateTime": "2019-02-04T19:58:15.511Z",
    "lastModifiedDateTime": null,
    "deleted": false,
    "subject": null,
    "summary": null,
    "importance": "normal",
    "locale": "en-us",
    "policyViolation": null,
    "from": {
        "application": null,
        "device": null,
        "conversation": null,
        "user": {
            "id": "id-value",
            "displayName": "Joh Doe",
            "userIdentityType": "aadUser"
        }
    },
      "body": {
        "contentType": "html",
        "content": "<div><div>\n<div><span><img height=\"250\" src=\"https://graph.microsoft.com/teams/teamId/channels/channelId/messages/id-value/hostedContents/hostedContentId/$value\" width=\"176.2295081967213\" style=\"vertical-align:bottom; width:176px; height:250px\"></span>\n\n</div>\n\n\n</div>\n</div>"
    },
    "attachments": [],
    "mentions": [],
    "reactions": []
}
```

## <a name="step-four-complete-migration-mode"></a>Etapa quatro: Concluir o modo de migração

Depois que o processo de migração de mensagens é concluído, a equipe e o canal são retirados do modo de migração usando o  `completeMigration`  método. Esta etapa abre os recursos de equipe e canal para uso geral pelos membros da equipe. A ação é vinculada à `team` instância.

#### <a name="request-end-team-migration-mode"></a>Solicitação (modo de migração de equipe final)

```http
POST https://graph.microsoft.com/beta/teams/teamId/completeMigration

```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-channel-migration-mode"></a>Solicitação (modo de migração de canal final)

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/completeMigration

```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 204 NoContent
```

#### <a name="error-response"></a>Resposta de erro

```http
400 Bad Request
```

* Ação chamada em um `team` ou que não está em `channel` `migrationMode` .

## <a name="step-five-add-team-members"></a>Etapa cinco: Adicionar membros da equipe

Você pode adicionar um membro a uma equipe usando a interface do usuário do [Teams](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) ou a API adicionar [membro do](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) Microsoft Graph:

#### <a name="request-add-member"></a>Solicitar (adicionar membro)

```http
POST https://graph.microsoft.com/beta/teams/{id}/members
Content-type: application/json
Content-length: 30
{
"@odata.type": "#microsoft.graph.aadUserConversationMember",
"roles": [],
"user@odata.bind": "https://graph.microsoft.com/beta/users/{user-id}"
}
```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a>Dicas e informações adicionais

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* Você pode importar mensagens de usuários que não estão no Teams. **OBSERVAÇÃO:** as mensagens importadas para usuários não presentes no locatário não serão pesquisáveis no cliente do Teams ou nos portais de conformidade durante a Visualização Pública.

* Depois que `completeMigration` a solicitação for feita, você não poderá importar mais mensagens para a equipe.

* Os membros da equipe só podem ser adicionados à nova equipe após a `completeMigration` solicitação ter retornado uma resposta bem-sucedida.

* Throttling: As mensagens são importadas a 5 RPS por canal.

* Se você precisar fazer uma correção nos resultados da migração, será necessário excluir a equipe e repetir as etapas para criar a equipe e o canal e migrar as mensagens.

> [!NOTE]
> Atualmente, as imagens em linha são o único tipo de mídia suportado pelo esquema de API de importação de mensagens.

##### <a name="import-content-scope"></a>Importar escopo de conteúdo

|No escopo | Fora do escopo no momento|
|----------|--------------------------|
|Mensagens de equipe e canal|Mensagens de bate-papo de grupo e 1:1|
|Hora de criação da mensagem original|Canais privados|
|Imagens em linha como parte da mensagem|Em menções|
|Links para arquivos existentes no SPO/OneDrive|Reações|
|Mensagens com rich text|Vídeos|
|Cadeia de resposta de mensagens|Announcements|
|Processamento de alta taxa de transferência|Trechos de código|
||Cartões adaptáveis|
||Figurinhas|
||Emojis|
||Aspas|
||Postagens cruzadas entre canais|

> [!div class="nextstepaction"]
>[Saiba mais sobre a integração do Microsoft Graph e do Teams](/graph/teams-concept-overview)
