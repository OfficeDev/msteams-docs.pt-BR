---
title: Use o Microsoft Graph para importar mensagens de plataforma externas para Teams
description: Descreve como usar o Microsoft Graph para importar mensagens de uma plataforma externa para Teams
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: equipes de importação mensagens api gráfico microsoft migrar post de migração
ms.openlocfilehash: 5ea06e8b490bae0595abb31086848d0b050bded0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566156"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a>Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph

Com a Microsoft Graph, você pode migrar o histórico de mensagens e dados existentes dos usuários de um sistema externo para um canal Teams. Ao permitir a recriação de uma hierarquia de mensagens de plataforma de terceiros dentro Teams, os usuários podem continuar suas comunicações de forma perfeita e prosseguir sem interrupção.

> [!NOTE] 
> No futuro, a Microsoft pode exigir que você ou seus clientes paguem taxas adicionais com base na quantidade de dados importados.

## <a name="import-overview"></a>Visão geral da importação

Em alto nível, o processo de importação consiste no seguinte:

1. [Crie uma equipe com um relógio back-in-time](#step-one-create-a-team)
1. [Crie um canal com um relógio back-in-time](#step-two-create-a-channel) 
1. [Importar mensagens datadas externas de back-in-time](#step-three-import-messages)
1. [Completar o processo de migração de equipe e canal](#step-four-complete-migration-mode)
1. [Adicionar membros da equipe](#step-five-add-team-members)

## <a name="necessary-requirements"></a>Requisitos necessários

### <a name="analyze-and-prepare-message-data"></a>Analisar e preparar dados de mensagens

✔ Revise os dados de terceiros para decidir o que será migrado.  
✔ Extrair os dados selecionados do sistema de bate-papo de terceiros.  
✔ Mapeia a estrutura de bate-papo de terceiros para a estrutura Teams.  
✔ Converter dados de importação em formato necessário para migração.  

### <a name="set-up-your-office-365-tenant"></a>Configurar seu locatário do Office 365

✔ Assegurado que exista um inquilino Office 365 para os dados de importação. Para obter mais informações sobre como configurar um Office 365 para Teams, consulte [Prepare seu inquilino Office 365](../../concepts/build-and-test/prepare-your-o365-tenant.md).  
✔ Certifique-se de que os membros da equipe estão em Azure Active Directory (AAD).  Para obter mais informações, consulte [Adicionar um novo usuário](/azure/active-directory/fundamentals/add-users-azure-active-directory) ao Azure Active Directory.

## <a name="step-one-create-a-team"></a>Passo Um: Crie uma equipe

Uma vez que os dados existentes estão sendo migrados, manter os horários de mensagem originais e impedir a atividade de mensagens durante o processo de migração são fundamentais para recriar o fluxo de mensagens existente do usuário em Teams. Isso é alcançado da seguinte forma:

> [Crie uma nova equipe](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um relógio back-in-time usando a propriedade de recursos da  `createdDateTime`  equipe. Coloque a nova equipe em `migration mode` um estado especial que barra os usuários da maioria das atividades dentro da equipe até que o processo de migração seja concluído. Inclua o `teamCreationMode` atributo de instância com o valor na solicitação POST para identificar explicitamente a nova equipe como sendo criada `migration` para migração.  

> [!Note]
> O `createdDateTime` campo só será povoado por exemplos de uma equipe ou canal que tenha sido migrado.

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a>Permissões

|Nome do escopo|DisplayName|Descrição|Tipo|Consentimento administrativo?|Entidades/APIs cobertas|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Gerenciar a migração do Microsoft Teams|Criando, gerenciando recursos para migração para Microsoft Teams.|**Somente aplicativos**|**Sim**|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a>Solicitação (criar uma equipe em estado de migração)

```http
POST https://graph.microsoft.com/v1.0/teams

Content-Type: application/json
{
  "@microsoft.graph.teamCreationMode": "migration",
  "template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
  "displayName": "My Sample Team",
  "description": "My Sample Team’s Description",
  "createdDateTime": "2020-03-14T11:22:17.043Z"
}
```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 202 Accepted
Location: /teams/{team-id}/operations/{operation-id}
Content-Location: /teams/{team-id}
```

#### <a name="error-messages"></a>Mensagens de erro

```http
400 Bad Request
```

* `createdDateTime`  definido para o futuro.
* `createdDateTime`  especificada corretamente, mas `teamCreationMode`  o atributo de instância está faltando ou definido como valor inválido.

## <a name="step-two-create-a-channel"></a>Passo Dois: Crie um canal

Criar um canal para as mensagens importadas é semelhante ao cenário da equipe de criação:

> [Crie um novo canal](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) com um relógio back-in-time usando a propriedade de recursos do `createdDateTime` canal. Coloque o novo canal em `migration mode` , um estado especial que barra os usuários da maioria das atividades de bate-papo dentro do canal até que o processo de migração seja concluído.  Inclua o `channelCreationMode` atributo de instância com o valor na solicitação POST para identificar explicitamente a nova equipe como sendo criada `migration` para migração.  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a>Permissões

|Nome do escopo|DisplayName|Descrição|Tipo|Consentimento administrativo?|Entidades/APIs cobertas|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Gerenciar a migração do Microsoft Teams|Criando, gerenciando recursos para migração para Microsoft Teams.|**Somente aplicativos**|**Sim**|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a>Solicitação (criar um canal em estado de migração)

```http
POST https://graph.microsoft.com/v1.0/teams/{team-id}/channels

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
   "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#teams('team-id')/channels/$entity",
   "id":"id-value",
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
* `createdDateTime`  especificado corretamente, mas `channelCreationMode`  o atributo de instância está faltando ou definido como valor inválido.

## <a name="step-three-import-messages"></a>Passo Três: Mensagens de importação

Depois que a equipe e o canal tiverem sido criados, você pode começar a enviar mensagens de volta no tempo usando as `createdDateTime`  chaves no corpo de `from`  solicitação. **NOTA**: as mensagens importadas com `createdDateTime` anteriores ao segmento de mensagem `createdDateTime` não são suportadas.

> [!NOTE]
> * `createdDateTime` deve ser único através de mensagens no mesmo segmento.
> * `createdDateTime` suporta timestamps com precisão de milissegundos. Por exemplo, se a mensagem de solicitação recebida tiver o valor definido `createdDateTime` como *2020-09-16T05:50:31.0025302Z*, então ela seria convertida para *2020-09-16T05:50:31.002Z* quando a mensagem é ingerida.

#### <a name="request-post-message-that-is-text-only"></a>Solicitação (mensagem POST que é somente por texto)

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/messages

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
   "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#teams('team-id')/channels('channel-id')/messages/$entity",
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

#### <a name="request-post-a-message-with-inline-image"></a>Solicitação (POSTAR uma mensagem com imagem inline)

> [!Note]
> Não há escopos de permissão especiais neste cenário, uma vez que a solicitação faz parte do chatMessage; escopos para chatMessage aplicar aqui também.

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/messages

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
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('team-id')/channels('channel-id')/messages/$entity",
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

## <a name="step-four-complete-migration-mode"></a>Passo Quatro: Modo de migração completo

Uma vez concluído o processo de migração de mensagens, tanto a equipe quanto o canal são retirados do modo de migração usando o  `completeMigration`  método. Esta etapa abre os recursos da equipe e do canal para uso geral por membros da equipe. A ação está vinculada à `team` instância. Todos os canais devem ser preenchidos fora do modo de migração antes que a equipe possa ser concluída.

#### <a name="request-end-channel-migration-mode"></a>Solicitação (modo de migração do canal final)

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/completeMigration

```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-team-migration-mode"></a>Solicitação (modo de migração da equipe final)

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/completeMigration
```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 204 NoContent
```

* Ação chamada em um `team` ou que não está em `channel` `migrationMode` .

## <a name="step-five-add-team-members"></a>Passo Cinco: Adicionar membros da equipe

Você pode adicionar um membro a uma equipe [usando a interface do usuário Teams](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) ou a API de adicionar [membros](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) da Microsoft Graph:

#### <a name="request-add-member"></a>Solicitação (adicionar membro)

```http
POST https://graph.microsoft.com/beta/teams/{team-id}/members
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

* Uma vez feita a `completeMigration` solicitação, você não pode importar mais mensagens para a equipe.

* Os membros da equipe só podem ser adicionados à nova equipe depois que a `completeMigration` solicitação tiver retornado uma resposta bem sucedida.

* Estrangulamento: As mensagens importam a 5 RPS por canal.

* Se você precisar fazer uma correção para os resultados de migração, você precisa excluir a equipe e repetir as etapas para criar a equipe e canalizar e re migrar as mensagens.

> [!NOTE]
> Atualmente, as imagens inline são o único tipo de mídia suportada pelo esquema de API da mensagem de importação.

##### <a name="import-content-scope"></a>Escopo de conteúdo de importação

|No escopo | Atualmente fora de escopo|
|----------|--------------------------|
|Mensagens de equipe e canal|1:1 e mensagens de bate-papo em grupo|
|Tempo criado da mensagem original|Canais privados|
|Imagens inline como parte da mensagem|Nas menções|
|Links para arquivos existentes em SPO/OneDrive|Reações|
|Mensagens com texto rico|Vídeos|
|Cadeia de resposta de mensagens|Announcements|
|Processamento de alto rendimento|Trechos de código|
||Adesivos|
||Emojis|
||Cotações|
||Cross posts entre canais|


## <a name="see-also"></a>Confira também

[Saiba mais sobre a integração de Graph e Teams da Microsoft](/graph/teams-concept-overview)
