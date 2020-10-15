---
title: Usar o Microsoft Graph para importar mensagens de plataforma externa para o Microsoft Teams
description: Descreve como usar o Microsoft Graph para importar mensagens de uma plataforma externa para o Microsoft Teams
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: gráfico de API de mensagens de importação de equipes Microsoft migrar migração post
ms.openlocfilehash: 0f53e27ec849e18be49f233a754658587343f68b
ms.sourcegitcommit: 25afe104d10c9a6a2849decf5ec1d08969d827c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "48465905"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a>Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph

>[!IMPORTANT]
> As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários. Embora este lançamento tenha transcorrido testes extensivos, ele não se destina ao uso em produção.

Com o Microsoft Graph, você pode migrar os dados e o histórico de mensagens existentes dos usuários de um sistema externo para um canal do teams. Ao habilitar a recreação de uma hierarquia de mensagens de plataforma de terceiros dentro do Teams, os usuários podem continuar a comunicação de forma perfeita e prosseguir sem interrupção.

## <a name="import-overview"></a>Visão geral da importação

Em um nível alto, o processo de importação consiste no seguinte:

1. [Criar uma equipe com um carimbo de data/hora Back-in-time](#step-one-create-a-team)
1. [Criar um canal com um carimbo de data/hora Back-in-time](#step-two-create-a-channel)  
1. [Importar mensagens de data e hora internas externas](#step-three-import-messages)
1. [Concluir o processo de migração de canal e equipe](#step-four-complete-migration-mode)
1. [Adicionar membros da equipe](#step-five-add-team-members)

## <a name="necessary-requirements"></a>Requisitos necessários

### <a name="analyze-and-prepare-message-data"></a>Analisar e preparar dados de mensagens

✔ Analise os dados de terceiros para decidir o que será migrado.  
✔ Extrair os dados selecionados do sistema de chat de terceiros.  
✔ Mapeie a estrutura de chat de terceiros para a estrutura do teams.  
✔ Converter dados de importação em formato necessário para a migração.  

### <a name="set-up-your-office-365-tenant"></a>Configurar seu locatário do Office 365

✔ Garantir que um locatário do Office 365 existe para os dados de importação. Para obter mais informações sobre como configurar uma locação do Office 365 para o Teams, *consulte*, [Prepare Your Office 365 locatário](../../concepts/build-and-test/prepare-your-o365-tenant.md).  
✔ Certifique-se de que os membros da equipe estão no Azure Active Directory (AAD).  Para obter mais informações, *consulte* [Adicionar um novo usuário](/azure/active-directory/fundamentals/add-users-azure-active-directory) ao Azure Active Directory.

## <a name="step-one-create-a-team"></a>Etapa 1: criar uma equipe

Como os dados existentes estão sendo migrados, a manutenção dos carimbos de data/hora da mensagem original e a prevenção da atividade de mensagens durante o processo de migração são fundamentais para recriar o fluxo de mensagens existente do usuário no Microsoft Teams. Isso é feito da seguinte maneira:

> [Crie uma nova equipe](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um carimbo de data/hora Back-in-time usando a propriedade de recurso da equipe  `createdDateTime`  . Coloque a nova equipe no `migration mode` , um estado especial que faz a barra de usuários da maioria das atividades dentro da equipe até que o processo de migração seja concluído. Inclua o `teamCreationMode` atributo de instância com o `migration` valor na solicitação post para identificar explicitamente a nova equipe como sendo criada para migração.  

> **Observação**: o `createdDateTime` campo só será preenchido para instâncias de uma equipe ou canal que foram migrados.

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a>Permissions

|ScopeName|DisplayName|Descrição|Tipo|Consentimento do administrador?|Entidades/APIs abordadas|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Gerenciar a migração do Microsoft Teams|Criando, Gerenciando recursos para migração para o Microsoft Teams|**Somente aplicativo**|Sim|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a>Solicitação (criar uma equipe no estado de migração)

```http
POST https://graph.microsoft.com/beta/teams

Content-Type: application/json
{
  "@microsoft.graph.teamCreationMode": "migration",
  "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('standard')",
  "displayName": "My Sample Team",
  "description": "My Sample Team’s Description"
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

* `createdDateTime`  definido para futuro.
* `createdDateTime`  especificado corretamente, mas o `teamCreationMode`  atributo de instância está ausente ou definido como um valor inválido.

## <a name="step-two-create-a-channel"></a>Etapa dois: criar um canal

A criação de um canal para as mensagens importadas é semelhante ao cenário criar equipe:

> [Crie um novo canal](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um carimbo de data/hora de entrada usando a propriedade de recurso Channel `createdDateTime` . Coloque o novo canal `migration mode` , um estado especial que rebarra os usuários da maioria das atividades de chat no canal até que o processo de migração seja concluído.  Inclua o `channelCreationMode` atributo de instância com o `migration` valor na solicitação post para identificar explicitamente a nova equipe como sendo criada para migração.  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a>Permissions

|ScopeName|DisplayName|Descrição|Tipo|Consentimento do administrador?|Entidades/APIs abordadas|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Gerenciar a migração do Microsoft Teams|Criando, Gerenciando recursos para migração para o Microsoft Teams|**Somente aplicativo**|Sim|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a>Solicitação (criar um canal no estado de migração)

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

#### Error message

```http
400 Bad Request
```

* `createdDateTime`  definido para futuro.
* `createdDateTime`  especificado corretamente, mas o `channelCreationMode`  atributo de instância está ausente ou definido como um valor inválido.

## <a name="step-three-import-messages"></a>Etapa três: importar mensagens

Depois que a equipe e o canal tiverem sido criados, você poderá começar a enviar mensagens de Back-in-time usando as `createdDateTime` `from`  teclas e no corpo da solicitação. **Observação**: não há suporte para mensagens importadas com `createdDateTime` versões anteriores ao segmento de mensagem `createdDateTime` .

> [!NOTE]
> createdDateTime deve ser exclusivo nas mensagens no mesmo thread.

#### <a name="request-post-message-that-is-text-only"></a>Solicitação (mensagem POST que é somente texto)

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

#### <a name="request-post-a-message-with-inline-image"></a>Solicitação (postar uma mensagem com uma imagem embutida)

> **Observação**: não há escopos de permissão especiais neste cenário, pois a solicitação faz parte do chat; os escopos para chat também são aplicados aqui.

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

## <a name="step-four-complete-migration-mode"></a>Etapa quatro: concluir o modo de migração

Após a conclusão do processo de migração de mensagens, a equipe e o canal são retirados do modo de migração usando o  `completeMigration`  método. Esta etapa abre a equipe e os recursos do canal para uso geral por membros da equipe. A ação está associada à `team` instância.

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

* Ação chamada em um `team` ou `channel` que não está no `migrationMode` .

## <a name="step-five-add-team-members"></a>Etapa cinco: adicionar membros da equipe

Você pode adicionar um membro a uma equipe [usando a interface do usuário do teams ou o](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) Microsoft Graph [Add Member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:

#### <a name="request-add-member"></a>Solicitação (Adicionar membro)

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

* Você pode importar mensagens de usuários que não estão no Teams. **Observação**: as mensagens importadas para usuários que não estão presentes no locatário não poderão ser pesquisadas no cliente ou portais de conformidade do Microsoft Teams durante a visualização pública.

* Depois que a `completeMigration` solicitação é feita, não é possível importar outras mensagens para a equipe.

* Os membros da equipe só poderão ser adicionados à nova equipe depois que a `completeMigration` solicitação tiver retornado uma resposta bem-sucedida.

* Limitação: importação de mensagens em 5 RPS por canal.

* Se for necessário fazer uma correção nos resultados da migração, você precisará excluir a equipe e repetir as etapas para criar a equipe e canal e migrar novamente as mensagens.

> [!NOTE]
> Atualmente, as imagens embutidas são o único tipo de mídia suportado pelo esquema de API de mensagens de importação.

##### <a name="import-content-scope"></a>Importar escopo de conteúdo

|No escopo | Fora do escopo atualmente|
|----------|--------------------------|
|Mensagens de canal e equipe|1:1 e mensagens de chat de grupo|
|Hora de criação da mensagem original|Canais privados|
|Imagens embutidas como parte da mensagem|Em menção|
|Links para arquivos existentes no SPO/OneDrive|Reações|
|Mensagens com Rich Text|Vídeos|
|Cadeia de resposta de mensagem|Comunicados|
|Processamento de alta produtividade|Trechos de código|
||Cartões adaptáveis|
||Etiquetas|
||Emojis|
||Eletrônica|
||Postagens entre canais|

> [!div class="nextstepaction"]
>[Saiba mais sobre a integração do Microsoft Graph e do teams](/graph/teams-concept-overview)
