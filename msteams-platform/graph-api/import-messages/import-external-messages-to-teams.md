---
title: Usar o Microsoft Graph para importar mensagens de plataforma externa para o Microsoft Teams
description: Descreve como usar o Microsoft Graph para importar mensagens de uma plataforma externa para o Microsoft Teams
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: gráfico de API de mensagens de importação de equipes Microsoft migrar migração post
ms.openlocfilehash: 934e00541773140c90c270a616d6bc50aacac6e1
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796292"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a><span data-ttu-id="9c835-104">Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="9c835-104">Import third-party platform messages to Teams using Microsoft Graph</span></span>

>[!IMPORTANT]
> <span data-ttu-id="9c835-105">As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários.</span><span class="sxs-lookup"><span data-stu-id="9c835-105">Microsoft Graph and Microsoft Teams public previews are available for early-access and feedback.</span></span> <span data-ttu-id="9c835-106">Embora este lançamento tenha transcorrido testes extensivos, ele não se destina ao uso em produção.</span><span class="sxs-lookup"><span data-stu-id="9c835-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

<span data-ttu-id="9c835-107">Com o Microsoft Graph, você pode migrar os dados e o histórico de mensagens existentes dos usuários de um sistema externo para um canal do teams.</span><span class="sxs-lookup"><span data-stu-id="9c835-107">With Microsoft Graph, you can migrate users' existing message history and data from an external system into a Teams channel.</span></span> <span data-ttu-id="9c835-108">Ao habilitar a recreação de uma hierarquia de mensagens de plataforma de terceiros dentro do Teams, os usuários podem continuar a comunicação de forma perfeita e prosseguir sem interrupção.</span><span class="sxs-lookup"><span data-stu-id="9c835-108">By enabling the recreation of a third-party platform messaging hierarchy inside Teams, users can continue their communications in a seamless manner and proceed without interruption.</span></span>

## <a name="import-overview"></a><span data-ttu-id="9c835-109">Visão geral da importação</span><span class="sxs-lookup"><span data-stu-id="9c835-109">Import overview</span></span>

<span data-ttu-id="9c835-110">Em um nível alto, o processo de importação consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="9c835-110">At a high level, the import process consists of the following:</span></span>

1. [<span data-ttu-id="9c835-111">Criar uma equipe com um carimbo de data/hora Back-in-time</span><span class="sxs-lookup"><span data-stu-id="9c835-111">Create a team with a back-in-time timestamp</span></span>](#step-one-create-a-team)
1. [<span data-ttu-id="9c835-112">Criar um canal com um carimbo de data/hora Back-in-time</span><span class="sxs-lookup"><span data-stu-id="9c835-112">Create a channel with a back-in-time timestamp</span></span>](#step-two-create-a-channel)  
1. [<span data-ttu-id="9c835-113">Importar mensagens de data e hora internas externas</span><span class="sxs-lookup"><span data-stu-id="9c835-113">Import external back-in-time dated messages</span></span>](#step-three-import-messages)
1. [<span data-ttu-id="9c835-114">Concluir o processo de migração de canal e equipe</span><span class="sxs-lookup"><span data-stu-id="9c835-114">Complete the team and channel migration process</span></span>](#step-four-complete-migration-mode)
1. [<span data-ttu-id="9c835-115">Adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="9c835-115">Add team members</span></span>](#step-five-add-team-members)

## <a name="necessary-requirements"></a><span data-ttu-id="9c835-116">Requisitos necessários</span><span class="sxs-lookup"><span data-stu-id="9c835-116">Necessary requirements</span></span>

### <a name="analyze-and-prepare-message-data"></a><span data-ttu-id="9c835-117">Analisar e preparar dados de mensagens</span><span class="sxs-lookup"><span data-stu-id="9c835-117">Analyze and prepare message data</span></span>

<span data-ttu-id="9c835-118">✔ Analise os dados de terceiros para decidir o que será migrado.</span><span class="sxs-lookup"><span data-stu-id="9c835-118">✔ Review the third-party data to decide what will be migrated.</span></span>  
<span data-ttu-id="9c835-119">✔ Extrair os dados selecionados do sistema de chat de terceiros.</span><span class="sxs-lookup"><span data-stu-id="9c835-119">✔ Extract the selected data from the third-party chat system.</span></span>  
<span data-ttu-id="9c835-120">✔ Mapeie a estrutura de chat de terceiros para a estrutura do teams.</span><span class="sxs-lookup"><span data-stu-id="9c835-120">✔ Map the third-party chat structure to the Teams structure.</span></span>  
<span data-ttu-id="9c835-121">✔ Converter dados de importação em formato necessário para a migração.</span><span class="sxs-lookup"><span data-stu-id="9c835-121">✔ Convert import data into format needed for migration.</span></span>  

### <a name="set-up-your-office-365-tenant"></a><span data-ttu-id="9c835-122">Configurar seu locatário do Office 365</span><span class="sxs-lookup"><span data-stu-id="9c835-122">Set up your Office 365 tenant</span></span>

<span data-ttu-id="9c835-123">✔ Garantir que um locatário do Office 365 existe para os dados de importação.</span><span class="sxs-lookup"><span data-stu-id="9c835-123">✔ Ensure that an Office 365 tenant exists for the import data.</span></span> <span data-ttu-id="9c835-124">Para obter mais informações sobre como configurar uma locação do Office 365 para o Teams, *consulte* , [Prepare Your Office 365 locatário](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="9c835-124">For more information on setting up an Office 365 tenancy for Teams, *see* , [Prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>  
<span data-ttu-id="9c835-125">✔ Certifique-se de que os membros da equipe estão no Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="9c835-125">✔ Make sure that team members are in Azure Active Directory (AAD).</span></span>  <span data-ttu-id="9c835-126">Para obter mais informações, *consulte* [Adicionar um novo usuário](/azure/active-directory/fundamentals/add-users-azure-active-directory) ao Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9c835-126">For more information *see* [Add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to Azure Active Directory.</span></span>

## <a name="step-one-create-a-team"></a><span data-ttu-id="9c835-127">Etapa 1: criar uma equipe</span><span class="sxs-lookup"><span data-stu-id="9c835-127">Step One: Create a team</span></span>

<span data-ttu-id="9c835-128">Como os dados existentes estão sendo migrados, a manutenção dos carimbos de data/hora da mensagem original e a prevenção da atividade de mensagens durante o processo de migração são fundamentais para recriar o fluxo de mensagens existente do usuário no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9c835-128">Since existing data is being migrated, maintaining the original message timestamps and preventing messaging activity during the migration process are key to recreating the user's existing message flow in Teams.</span></span> <span data-ttu-id="9c835-129">Isso é feito da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9c835-129">This is achieved as follows:</span></span>

> <span data-ttu-id="9c835-130">[Crie uma nova equipe](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um carimbo de data/hora Back-in-time usando a propriedade de recurso da equipe  `createdDateTime`  .</span><span class="sxs-lookup"><span data-stu-id="9c835-130">[Create a new team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the team resource  `createdDateTime`  property.</span></span> <span data-ttu-id="9c835-131">Coloque a nova equipe no `migration mode` , um estado especial que faz a barra de usuários da maioria das atividades dentro da equipe até que o processo de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="9c835-131">Place the new team in `migration mode`, a special state that bars users from most activities within the team until the migration process is complete.</span></span> <span data-ttu-id="9c835-132">Inclua o `teamCreationMode` atributo de instância com o `migration` valor na solicitação post para identificar explicitamente a nova equipe como sendo criada para migração.</span><span class="sxs-lookup"><span data-stu-id="9c835-132">Include the `teamCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  

> <span data-ttu-id="9c835-133">**Observação** : o `createdDateTime` campo só será preenchido para instâncias de uma equipe ou canal que foram migrados.</span><span class="sxs-lookup"><span data-stu-id="9c835-133">**NOTE** :  The `createdDateTime` field will only be populated for instances of a team or channel that have been migrated.</span></span>

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a><span data-ttu-id="9c835-134">Permissões</span><span class="sxs-lookup"><span data-stu-id="9c835-134">Permissions</span></span>

|<span data-ttu-id="9c835-135">ScopeName</span><span class="sxs-lookup"><span data-stu-id="9c835-135">ScopeName</span></span>|<span data-ttu-id="9c835-136">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9c835-136">DisplayName</span></span>|<span data-ttu-id="9c835-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c835-137">Description</span></span>|<span data-ttu-id="9c835-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="9c835-138">Type</span></span>|<span data-ttu-id="9c835-139">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="9c835-139">Admin Consent?</span></span>|<span data-ttu-id="9c835-140">Entidades/APIs abordadas</span><span class="sxs-lookup"><span data-stu-id="9c835-140">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="9c835-141">Gerenciar a migração do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9c835-141">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="9c835-142">Criando, Gerenciando recursos para migração para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9c835-142">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="9c835-143">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="9c835-143">**Application-only**</span></span>|<span data-ttu-id="9c835-144">Sim</span><span class="sxs-lookup"><span data-stu-id="9c835-144">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a><span data-ttu-id="9c835-145">Solicitação (criar uma equipe no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="9c835-145">Request (create a team in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="9c835-146">Resposta</span><span class="sxs-lookup"><span data-stu-id="9c835-146">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{teamId}/operations/{operationId}
Content-Location: /teams/{teamId}
```

#### <a name="error-messages"></a><span data-ttu-id="9c835-147">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="9c835-147">Error messages</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="9c835-148">`createdDateTime`  definido para futuro.</span><span class="sxs-lookup"><span data-stu-id="9c835-148">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="9c835-149">`createdDateTime`  especificado corretamente, mas o `teamCreationMode`  atributo de instância está ausente ou definido como um valor inválido.</span><span class="sxs-lookup"><span data-stu-id="9c835-149">`createdDateTime`  correctly specified, but `teamCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-two-create-a-channel"></a><span data-ttu-id="9c835-150">Etapa dois: criar um canal</span><span class="sxs-lookup"><span data-stu-id="9c835-150">Step Two: Create a channel</span></span>

<span data-ttu-id="9c835-151">A criação de um canal para as mensagens importadas é semelhante ao cenário criar equipe:</span><span class="sxs-lookup"><span data-stu-id="9c835-151">Creating a channel for the imported messages is similar to the create team scenario:</span></span>

> <span data-ttu-id="9c835-152">[Crie um novo canal](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um carimbo de data/hora de entrada usando a propriedade de recurso Channel `createdDateTime` .</span><span class="sxs-lookup"><span data-stu-id="9c835-152">[Create a new channel](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the channel resource `createdDateTime` property.</span></span> <span data-ttu-id="9c835-153">Coloque o novo canal `migration mode` , um estado especial que rebarra os usuários da maioria das atividades de chat no canal até que o processo de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="9c835-153">Place the new channel in `migration mode`, a special state that bars users from most chat activities within the channel until the migration process is complete.</span></span>  <span data-ttu-id="9c835-154">Inclua o `channelCreationMode` atributo de instância com o `migration` valor na solicitação post para identificar explicitamente a nova equipe como sendo criada para migração.</span><span class="sxs-lookup"><span data-stu-id="9c835-154">Include the `channelCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a><span data-ttu-id="9c835-155">Permissões</span><span class="sxs-lookup"><span data-stu-id="9c835-155">Permissions</span></span>

|<span data-ttu-id="9c835-156">ScopeName</span><span class="sxs-lookup"><span data-stu-id="9c835-156">ScopeName</span></span>|<span data-ttu-id="9c835-157">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9c835-157">DisplayName</span></span>|<span data-ttu-id="9c835-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c835-158">Description</span></span>|<span data-ttu-id="9c835-159">Tipo</span><span class="sxs-lookup"><span data-stu-id="9c835-159">Type</span></span>|<span data-ttu-id="9c835-160">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="9c835-160">Admin Consent?</span></span>|<span data-ttu-id="9c835-161">Entidades/APIs abordadas</span><span class="sxs-lookup"><span data-stu-id="9c835-161">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="9c835-162">Gerenciar a migração do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9c835-162">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="9c835-163">Criando, Gerenciando recursos para migração para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9c835-163">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="9c835-164">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="9c835-164">**Application-only**</span></span>|<span data-ttu-id="9c835-165">Sim</span><span class="sxs-lookup"><span data-stu-id="9c835-165">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a><span data-ttu-id="9c835-166">Solicitação (criar um canal no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="9c835-166">Request (create a channel in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="9c835-167">Resposta</span><span class="sxs-lookup"><span data-stu-id="9c835-167">Response</span></span>

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

#### <a name="error-message"></a><span data-ttu-id="9c835-168">Mensagem de erro</span><span class="sxs-lookup"><span data-stu-id="9c835-168">Error message</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="9c835-169">`createdDateTime`  definido para futuro.</span><span class="sxs-lookup"><span data-stu-id="9c835-169">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="9c835-170">`createdDateTime`  especificado corretamente, mas o `channelCreationMode`  atributo de instância está ausente ou definido como um valor inválido.</span><span class="sxs-lookup"><span data-stu-id="9c835-170">`createdDateTime`  correctly specified but `channelCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-three-import-messages"></a><span data-ttu-id="9c835-171">Etapa três: importar mensagens</span><span class="sxs-lookup"><span data-stu-id="9c835-171">Step Three: Import messages</span></span>

<span data-ttu-id="9c835-172">Depois que a equipe e o canal tiverem sido criados, você poderá começar a enviar mensagens de Back-in-time usando as `createdDateTime` `from`  teclas e no corpo da solicitação.</span><span class="sxs-lookup"><span data-stu-id="9c835-172">After the team and channel have been created, you can begin sending back-in-time messages using the `createdDateTime`  and `from`  keys in the request body.</span></span> <span data-ttu-id="9c835-173">**Observação** : não há suporte para mensagens importadas com `createdDateTime` versões anteriores ao segmento de mensagem `createdDateTime` .</span><span class="sxs-lookup"><span data-stu-id="9c835-173">**NOTE** : messages imported with `createdDateTime` earlier than the message thread `createdDateTime` is not supported.</span></span>

> [!NOTE]
> <span data-ttu-id="9c835-174">createdDateTime deve ser exclusivo nas mensagens no mesmo thread.</span><span class="sxs-lookup"><span data-stu-id="9c835-174">createdDateTime must be unique across messages in the same thread.</span></span>

#### <a name="request-post-message-that-is-text-only"></a><span data-ttu-id="9c835-175">Solicitação (mensagem POST que é somente texto)</span><span class="sxs-lookup"><span data-stu-id="9c835-175">Request (POST message that is text-only)</span></span>

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

#### <a name="response"></a><span data-ttu-id="9c835-176">Resposta</span><span class="sxs-lookup"><span data-stu-id="9c835-176">Response</span></span>

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

#### <a name="error-messages"></a><span data-ttu-id="9c835-177">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="9c835-177">Error messages</span></span>

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a><span data-ttu-id="9c835-178">Solicitação (postar uma mensagem com uma imagem embutida)</span><span class="sxs-lookup"><span data-stu-id="9c835-178">Request (POST a message with inline image)</span></span>

> <span data-ttu-id="9c835-179">**Observação** : não há escopos de permissão especiais neste cenário, pois a solicitação faz parte do chat; os escopos para chat também são aplicados aqui.</span><span class="sxs-lookup"><span data-stu-id="9c835-179">**Note** : There are no special permission scopes in this scenario since the request is part of chatMessage; scopes for chatMessage apply here as well.</span></span>

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

#### <a name="response"></a><span data-ttu-id="9c835-180">Resposta</span><span class="sxs-lookup"><span data-stu-id="9c835-180">Response</span></span>

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

## <a name="step-four-complete-migration-mode"></a><span data-ttu-id="9c835-181">Etapa quatro: concluir o modo de migração</span><span class="sxs-lookup"><span data-stu-id="9c835-181">Step Four: Complete migration mode</span></span>

<span data-ttu-id="9c835-182">Após a conclusão do processo de migração de mensagens, a equipe e o canal são retirados do modo de migração usando o  `completeMigration`  método.</span><span class="sxs-lookup"><span data-stu-id="9c835-182">Once the message migration process has completed, both the team and channel are taken out of migration mode using the  `completeMigration`  method.</span></span> <span data-ttu-id="9c835-183">Esta etapa abre a equipe e os recursos do canal para uso geral por membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="9c835-183">This step opens the team and channel resources for general use by team members.</span></span> <span data-ttu-id="9c835-184">A ação está associada à `team` instância.</span><span class="sxs-lookup"><span data-stu-id="9c835-184">The action is bound to the `team` instance.</span></span>

#### <a name="request-end-team-migration-mode"></a><span data-ttu-id="9c835-185">Solicitação (modo de migração de equipe final)</span><span class="sxs-lookup"><span data-stu-id="9c835-185">Request (end team migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="9c835-186">Resposta</span><span class="sxs-lookup"><span data-stu-id="9c835-186">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-channel-migration-mode"></a><span data-ttu-id="9c835-187">Solicitação (modo de migração de canal final)</span><span class="sxs-lookup"><span data-stu-id="9c835-187">Request (end channel migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="9c835-188">Resposta</span><span class="sxs-lookup"><span data-stu-id="9c835-188">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="error-response"></a><span data-ttu-id="9c835-189">Resposta de erro</span><span class="sxs-lookup"><span data-stu-id="9c835-189">Error response</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="9c835-190">Ação chamada em um `team` ou `channel` que não está no `migrationMode` .</span><span class="sxs-lookup"><span data-stu-id="9c835-190">Action called on a `team` or `channel` that is not in `migrationMode`.</span></span>

## <a name="step-five-add-team-members"></a><span data-ttu-id="9c835-191">Etapa cinco: adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="9c835-191">Step Five: Add team members</span></span>

<span data-ttu-id="9c835-192">Você pode adicionar um membro a uma equipe [usando a interface do usuário do teams ou o](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) Microsoft Graph [Add Member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:</span><span class="sxs-lookup"><span data-stu-id="9c835-192">You can add a member to a team [using the Teams UI](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) or Microsoft Graph [Add member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:</span></span>

#### <a name="request-add-member"></a><span data-ttu-id="9c835-193">Solicitação (Adicionar membro)</span><span class="sxs-lookup"><span data-stu-id="9c835-193">Request (add member)</span></span>

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

#### <a name="response"></a><span data-ttu-id="9c835-194">Resposta</span><span class="sxs-lookup"><span data-stu-id="9c835-194">Response</span></span>

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a><span data-ttu-id="9c835-195">Dicas e informações adicionais</span><span class="sxs-lookup"><span data-stu-id="9c835-195">Tips and additional information</span></span>

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* <span data-ttu-id="9c835-196">Você pode importar mensagens de usuários que não estão no Teams.</span><span class="sxs-lookup"><span data-stu-id="9c835-196">You can import messages from users who are not in Teams.</span></span> <span data-ttu-id="9c835-197">**Observação** : as mensagens importadas para usuários que não estão presentes no locatário não poderão ser pesquisadas no cliente ou portais de conformidade do Microsoft Teams durante a visualização pública.</span><span class="sxs-lookup"><span data-stu-id="9c835-197">**NOTE** : Messages imported for users not present in the tenant will not be searchable in the Teams client or compliance portals during Public Preview.</span></span>

* <span data-ttu-id="9c835-198">Depois que a `completeMigration` solicitação é feita, não é possível importar outras mensagens para a equipe.</span><span class="sxs-lookup"><span data-stu-id="9c835-198">Once the `completeMigration` request is made, you cannot import further messages into the team.</span></span>

* <span data-ttu-id="9c835-199">Os membros da equipe só poderão ser adicionados à nova equipe depois que a `completeMigration` solicitação tiver retornado uma resposta bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9c835-199">Team members can only be added to the new team after the `completeMigration` request has returned a successful response.</span></span>

* <span data-ttu-id="9c835-200">Limitação: importação de mensagens em 5 RPS por canal.</span><span class="sxs-lookup"><span data-stu-id="9c835-200">Throttling: Messages import at 5 RPS per channel.</span></span>

* <span data-ttu-id="9c835-201">Se for necessário fazer uma correção nos resultados da migração, você precisará excluir a equipe e repetir as etapas para criar a equipe e canal e migrar novamente as mensagens.</span><span class="sxs-lookup"><span data-stu-id="9c835-201">If you need to make a correction to the migration results, you need to delete the team and repeat the steps to create the team and channel and re-migrate the messages.</span></span>

> [!NOTE]
> <span data-ttu-id="9c835-202">Atualmente, as imagens embutidas são o único tipo de mídia suportado pelo esquema de API de mensagens de importação.</span><span class="sxs-lookup"><span data-stu-id="9c835-202">Currently, inline images are the only type of media supported by the import message API schema.</span></span>

##### <a name="import-content-scope"></a><span data-ttu-id="9c835-203">Importar escopo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="9c835-203">Import content scope</span></span>

|<span data-ttu-id="9c835-204">No escopo</span><span class="sxs-lookup"><span data-stu-id="9c835-204">In-scope</span></span> | <span data-ttu-id="9c835-205">Fora do escopo atualmente</span><span class="sxs-lookup"><span data-stu-id="9c835-205">Currently out-of-scope</span></span>|
|----------|--------------------------|
|<span data-ttu-id="9c835-206">Mensagens de canal e equipe</span><span class="sxs-lookup"><span data-stu-id="9c835-206">Team and channel messages</span></span>|<span data-ttu-id="9c835-207">1:1 e mensagens de chat de grupo</span><span class="sxs-lookup"><span data-stu-id="9c835-207">1:1 and group chat messages</span></span>|
|<span data-ttu-id="9c835-208">Hora de criação da mensagem original</span><span class="sxs-lookup"><span data-stu-id="9c835-208">Created time of the original message</span></span>|<span data-ttu-id="9c835-209">Canais privados</span><span class="sxs-lookup"><span data-stu-id="9c835-209">Private channels</span></span>|
|<span data-ttu-id="9c835-210">Imagens embutidas como parte da mensagem</span><span class="sxs-lookup"><span data-stu-id="9c835-210">Inline images as part of the message</span></span>|<span data-ttu-id="9c835-211">Em menção</span><span class="sxs-lookup"><span data-stu-id="9c835-211">At mentions</span></span>|
|<span data-ttu-id="9c835-212">Links para arquivos existentes no SPO/OneDrive</span><span class="sxs-lookup"><span data-stu-id="9c835-212">Links to existing files in SPO/OneDrive</span></span>|<span data-ttu-id="9c835-213">Reações</span><span class="sxs-lookup"><span data-stu-id="9c835-213">Reactions</span></span>|
|<span data-ttu-id="9c835-214">Mensagens com Rich Text</span><span class="sxs-lookup"><span data-stu-id="9c835-214">Messages with rich text</span></span>|<span data-ttu-id="9c835-215">Vídeos</span><span class="sxs-lookup"><span data-stu-id="9c835-215">Videos</span></span>|
|<span data-ttu-id="9c835-216">Cadeia de resposta de mensagem</span><span class="sxs-lookup"><span data-stu-id="9c835-216">Message reply chain</span></span>|<span data-ttu-id="9c835-217">Comunicados</span><span class="sxs-lookup"><span data-stu-id="9c835-217">Announcements</span></span>|
|<span data-ttu-id="9c835-218">Processamento de alta produtividade</span><span class="sxs-lookup"><span data-stu-id="9c835-218">High throughput processing</span></span>|<span data-ttu-id="9c835-219">Trechos de código</span><span class="sxs-lookup"><span data-stu-id="9c835-219">Code snippets</span></span>|
||<span data-ttu-id="9c835-220">Cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="9c835-220">Adaptive cards</span></span>|
||<span data-ttu-id="9c835-221">Etiquetas</span><span class="sxs-lookup"><span data-stu-id="9c835-221">Stickers</span></span>|
||<span data-ttu-id="9c835-222">Emojis</span><span class="sxs-lookup"><span data-stu-id="9c835-222">Emojis</span></span>|
||<span data-ttu-id="9c835-223">Eletrônica</span><span class="sxs-lookup"><span data-stu-id="9c835-223">Quotes</span></span>|
||<span data-ttu-id="9c835-224">Postagens entre canais</span><span class="sxs-lookup"><span data-stu-id="9c835-224">Cross posts between channels</span></span>|

> [!div class="nextstepaction"]
>[<span data-ttu-id="9c835-225">Saiba mais sobre a integração do Microsoft Graph e do teams</span><span class="sxs-lookup"><span data-stu-id="9c835-225">Learn more about Microsoft Graph and Teams integration</span></span>](/graph/teams-concept-overview)
