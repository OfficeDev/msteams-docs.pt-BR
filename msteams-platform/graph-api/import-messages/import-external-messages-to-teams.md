---
title: Use o Microsoft Graph para importar mensagens de plataforma externa para Teams
description: Descreve como usar o Microsoft Graph para importar mensagens de uma plataforma externa para Teams
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: Overview
keywords: teams import messages api graph microsoft migrar migration post
ms.openlocfilehash: d20212bf5f5766e71b1be7a4476518510b8de80b
ms.sourcegitcommit: 7209e5af27e1ebe34f7e26ca1e6b17cb7290bc06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2022
ms.locfileid: "62212521"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a>Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph

Com o Microsoft Graph, você pode migrar o histórico de mensagens e os dados existentes dos usuários de um sistema externo para um canal Teams. Ao habilitar a recriação de uma hierarquia de mensagens de plataforma de terceiros dentro Teams, os usuários podem continuar suas comunicações de maneira perfeita e continuar sem interrupção.

> [!NOTE]
> No futuro, a Microsoft pode exigir que você ou seus clientes paguem taxas adicionais com base na quantidade de dados importados.

## <a name="import-overview"></a>Visão geral de importação

Em um nível alto, o processo de importação consiste no seguinte:

1. [Crie uma equipe com um back-in-timestamp](#step-1-create-a-team).
1. [Crie um canal com um back-in-timestamp](#step-2-create-a-channel).
1. [Importar mensagens de back-in-time externas datadas](#step-3-import-messages).
1. [Conclua o processo de migração de equipe e canal.](#step-4-complete-migration-mode)
1. [Adicionar membros da equipe](#step-five-add-team-members).

## <a name="prerequisites"></a>Pré-requisitos

### <a name="analyze-and-prepare-message-data"></a>Analisar e preparar dados de mensagens

* Revise os dados de terceiros para decidir o que será migrado.  
* Extraia os dados selecionados do sistema de chat de terceiros.  
* Mapeie a estrutura de chat de terceiros para a estrutura Teams de terceiros.  
* Converta os dados de importação no formato necessário para a migração.  

### <a name="set-up-your-office-365-tenant"></a>Configurar seu locatário do Office 365

* Verifique se existe Office 365 locatário para os dados de importação. Para obter mais informações sobre como configurar Office 365 locatário para Teams, consulte [prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).
* Certifique-se de que os membros da equipe estão Azure Active Directory. Para saber mais, [confira adicionar um novo usuário](/azure/active-directory/fundamentals/add-users-azure-active-directory) ao Azure AD.

## <a name="step-1-create-a-team"></a>Etapa 1: Criar uma equipe

Como você está migrando dados existentes, manter os datas de data/hora originais da mensagem e impedir a atividade de mensagens durante o processo de migração são fundamentais para recriar o fluxo de mensagens existente do usuário no Teams. Isso é alcançado da seguinte forma:

> [Crie uma nova equipe](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um back-in-timestamp usando a propriedade de recurso de `createdDateTime` equipe. Coloque a nova equipe em , um estado especial que restringe os usuários da maioria das atividades dentro da equipe até que o processo `migration mode` de migração seja concluído. Inclua o atributo instance com o valor na solicitação POST para identificar explicitamente a `teamCreationMode` nova equipe como sendo criada para `migration` migração.  

> [!NOTE]
> O `createdDateTime` campo só será preenchido para instâncias de uma equipe ou canal que foram migradas.

<!-- markdownlint-disable MD001 -->

#### <a name="permission"></a>Permissão

|ScopeName|DisplayName|Descrição|Tipo|Consentimento do administrador?|Entidades/APIs cobertas|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Gerenciar a migração do Microsoft Teams|Criando e gerenciando recursos para migração para Microsoft Teams.|**Somente aplicativo**|**Sim**|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a>Solicitação (criar uma equipe no estado de migração)

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

#### <a name="error-message"></a>Mensagem de erro

```http
400 Bad Request
```

Você pode receber a mensagem de erro nos seguintes cenários:

* Se `createdDateTime` estiver definido para o futuro.
* Se `createdDateTime` for especificado corretamente, mas o atributo instance estiver ausente ou definido como valor `teamCreationMode` inválido.

## <a name="step-2-create-a-channel"></a>Etapa 2: Criar um canal

A criação de um canal para as mensagens importadas é semelhante ao cenário de criação de equipe:

> [Crie um novo canal](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) com um back-in-timestamp usando a propriedade de recurso `createdDateTime` channel. Coloque o novo canal em , um estado especial que restringe os usuários da maioria das atividades de chat dentro do canal até que o processo `migration mode` de migração seja concluído. Inclua o atributo instance com o valor na solicitação POST para identificar explicitamente a `channelCreationMode` nova equipe como sendo criada para `migration` migração.  
<!-- markdownlint-disable MD024 -->
#### <a name="permission"></a>Permissão

|ScopeName|DisplayName|Descrição|Tipo|Consentimento do administrador?|Entidades/APIs cobertas|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Gerenciar a migração do Microsoft Teams|Criando e gerenciando recursos para migração para Microsoft Teams.|**Somente aplicativo**|**Sim**|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a>Solicitação (criar um canal no estado de migração)

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
Você pode receber a mensagem de erro nos seguintes cenários:

* Se `createdDateTime` estiver definido para o futuro.
* Se `createdDateTime` for especificado corretamente, mas o `channelCreationMode` atributo instance estiver ausente ou definido como valor inválido.

## <a name="step-3-import-messages"></a>Etapa 3: Importar mensagens

Depois que a equipe e o canal foram criados, você pode começar a enviar mensagens de back-in-time usando as chaves e `createdDateTime` `from` no corpo da solicitação.

> [!NOTE]
> * Não há suporte para mensagens `createdDateTime` importadas com o thread da `createdDateTime` mensagem.
> * `createdDateTime` deve ser exclusivo entre mensagens no mesmo thread.
> * `createdDateTime` oferece suporte a data/hora com precisão de milissegundos. Por exemplo, se a mensagem de solicitação de entrada tiver o valor definido como `createdDateTime` *2020-09-16T05:50:31.0025302Z*, ela será convertida em *2020-09-16T05:50:31.002Z* quando a mensagem for ingerida.

#### <a name="request-post-message-that-is-text-only"></a>Solicitação (mensagem POST que é somente texto)

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

#### <a name="error-message"></a>Mensagem de erro

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a>Solicitar (POSTAR uma mensagem com imagem em linha)

> [!NOTE]
> * Não há escopos de permissão especiais nesse cenário, pois a solicitação faz parte de `chatMessage` .
> * Os escopos para `chatMessage` aplicar aqui.

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

## <a name="step-4-complete-migration-mode"></a>Etapa 4: Concluir o modo de migração

Após a conclusão do processo de migração de mensagens, a equipe e o canal são retirados do modo de migração usando o  `completeMigration` método. Esta etapa abre os recursos de equipe e canal para uso geral pelos membros da equipe. A ação está vinculada à `team` instância. Antes da conclusão da equipe, todos os canais devem ser concluídos fora do modo de migração.

#### <a name="request-end-channel-migration-mode"></a>Solicitação (modo de migração de canal final)

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/completeMigration

```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-team-migration-mode"></a>Solicitação (modo de migração de equipe final)

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/completeMigration
```

#### <a name="response"></a>Resposta

```http
HTTP/1.1 204 NoContent
```

Ação chamada em um `team` ou que não está em `channel` `migrationMode` .

## <a name="step-five-add-team-members"></a>Etapa cinco: Adicionar membros da equipe

Você pode adicionar um membro a uma equipe usando a interface [do usuário Teams ou](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) o Microsoft Graph adicionar API de [membro:](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true)

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

## <a name="tips-and-additional-information"></a>Dicas informações adicionais

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* Depois que `completeMigration` a solicitação for feita, você não poderá importar mais mensagens para a equipe.

* Você só pode adicionar membros da equipe à nova equipe após a solicitação `completeMigration` ter retornado uma resposta bem-sucedida.

* Throttling: As mensagens são importadas em cinco RPS por canal.

* Se precisar fazer uma correção nos resultados da migração, exclua a equipe e repita as etapas para criar a equipe e o canal e migrar as mensagens.

> [!NOTE]
> Atualmente, as imagens em linha são o único tipo de mídia com suporte pelo esquema de API de mensagem de importação.

##### <a name="import-content-scope"></a>Importar escopo de conteúdo

A tabela a seguir fornece o escopo de conteúdo:

|No escopo | Atualmente fora do escopo|
|----------|--------------------------|
|Mensagens de equipe e canal|1:1 e mensagens de chat de grupo|
|Hora de criação da mensagem original|Canais privados|
|Imagens em linha como parte da mensagem|At mentions|
|Links para arquivos existentes no SPO ou OneDrive|Reações|
|Mensagens com texto rico|Vídeos|
|Cadeia de resposta de mensagens|Comunicados|
|Processamento de alta taxa de transferência|Trechos de código|
||Adesivos|
||Emojis|
||Cotações|
||Postagens entre canais|


## <a name="see-also"></a>Confira também

[Integração Graph microsoft Teams](/graph/teams-concept-overview)
