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
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a><span data-ttu-id="809f6-104">Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="809f6-104">Import third-party platform messages to Teams using Microsoft Graph</span></span>

>[!IMPORTANT]
> <span data-ttu-id="809f6-105">As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários.</span><span class="sxs-lookup"><span data-stu-id="809f6-105">Microsoft Graph and Microsoft Teams public previews are available for early-access and feedback.</span></span> <span data-ttu-id="809f6-106">Embora esta versão tenha passado por testes extensos, ela não foi destinada ao uso na produção.</span><span class="sxs-lookup"><span data-stu-id="809f6-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

<span data-ttu-id="809f6-107">Com o Microsoft Graph, você pode migrar o histórico de mensagens e os dados existentes dos usuários de um sistema externo para um canal do Teams.</span><span class="sxs-lookup"><span data-stu-id="809f6-107">With Microsoft Graph, you can migrate users' existing message history and data from an external system into a Teams channel.</span></span> <span data-ttu-id="809f6-108">Ao habilitar a recriação de uma hierarquia de mensagens da plataforma de terceiros dentro do Teams, os usuários podem continuar suas comunicações de maneira perfeita e continuar sem interrupção.</span><span class="sxs-lookup"><span data-stu-id="809f6-108">By enabling the recreation of a third-party platform messaging hierarchy inside Teams, users can continue their communications in a seamless manner and proceed without interruption.</span></span>

## <a name="import-overview"></a><span data-ttu-id="809f6-109">Visão geral da importação</span><span class="sxs-lookup"><span data-stu-id="809f6-109">Import overview</span></span>

<span data-ttu-id="809f6-110">Em um nível alto, o processo de importação consiste do seguinte:</span><span class="sxs-lookup"><span data-stu-id="809f6-110">At a high level, the import process consists of the following:</span></span>

1. [<span data-ttu-id="809f6-111">Criar uma equipe com um back-in-timestamp</span><span class="sxs-lookup"><span data-stu-id="809f6-111">Create a team with a back-in-time timestamp</span></span>](#step-one-create-a-team)
1. [<span data-ttu-id="809f6-112">Criar um canal com um back-in-timestamp</span><span class="sxs-lookup"><span data-stu-id="809f6-112">Create a channel with a back-in-time timestamp</span></span>](#step-two-create-a-channel)  
1. [<span data-ttu-id="809f6-113">Importar mensagens internas e externas no tempo</span><span class="sxs-lookup"><span data-stu-id="809f6-113">Import external back-in-time dated messages</span></span>](#step-three-import-messages)
1. [<span data-ttu-id="809f6-114">Concluir o processo de migração de equipe e canal</span><span class="sxs-lookup"><span data-stu-id="809f6-114">Complete the team and channel migration process</span></span>](#step-four-complete-migration-mode)
1. [<span data-ttu-id="809f6-115">Adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="809f6-115">Add team members</span></span>](#step-five-add-team-members)

## <a name="necessary-requirements"></a><span data-ttu-id="809f6-116">Requisitos necessários</span><span class="sxs-lookup"><span data-stu-id="809f6-116">Necessary requirements</span></span>

### <a name="analyze-and-prepare-message-data"></a><span data-ttu-id="809f6-117">Analisar e preparar dados de mensagens</span><span class="sxs-lookup"><span data-stu-id="809f6-117">Analyze and prepare message data</span></span>

<span data-ttu-id="809f6-118">✔ revise os dados de terceiros para decidir o que será migrado.</span><span class="sxs-lookup"><span data-stu-id="809f6-118">✔ Review the third-party data to decide what will be migrated.</span></span>  
<span data-ttu-id="809f6-119">✔ Extraia os dados selecionados do sistema de chat de terceiros.</span><span class="sxs-lookup"><span data-stu-id="809f6-119">✔ Extract the selected data from the third-party chat system.</span></span>  
<span data-ttu-id="809f6-120">✔ mapear a estrutura de chat de terceiros para a estrutura do Teams.</span><span class="sxs-lookup"><span data-stu-id="809f6-120">✔ Map the third-party chat structure to the Teams structure.</span></span>  
<span data-ttu-id="809f6-121">✔ converter dados de importação no formato necessário para a migração.</span><span class="sxs-lookup"><span data-stu-id="809f6-121">✔ Convert import data into format needed for migration.</span></span>  

### <a name="set-up-your-office-365-tenant"></a><span data-ttu-id="809f6-122">Configurar seu locatário do Office 365</span><span class="sxs-lookup"><span data-stu-id="809f6-122">Set up your Office 365 tenant</span></span>

<span data-ttu-id="809f6-123">✔ verifique se existe um locatário do Office 365 para os dados de importação.</span><span class="sxs-lookup"><span data-stu-id="809f6-123">✔ Ensure that an Office 365 tenant exists for the import data.</span></span> <span data-ttu-id="809f6-124">Para obter mais informações sobre como configurar uma locação do Office 365 para o *Teams,* confira , Preparar seu [locatário do Office 365.](../../concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="809f6-124">For more information on setting up an Office 365 tenancy for Teams, *see*, [Prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>  
<span data-ttu-id="809f6-125">✔ se os membros da equipe estão no Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="809f6-125">✔ Make sure that team members are in Azure Active Directory (AAD).</span></span>  <span data-ttu-id="809f6-126">Para saber *mais, confira* [Adicionar um novo usuário](/azure/active-directory/fundamentals/add-users-azure-active-directory) ao Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="809f6-126">For more information *see* [Add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to Azure Active Directory.</span></span>

## <a name="step-one-create-a-team"></a><span data-ttu-id="809f6-127">Etapa um: criar uma equipe</span><span class="sxs-lookup"><span data-stu-id="809f6-127">Step One: Create a team</span></span>

<span data-ttu-id="809f6-128">Como os dados existentes estão sendo migrados, manter os dados de data/hora originais da mensagem e impedir a atividade de mensagens durante o processo de migração é fundamental para recriar o fluxo de mensagens existente do usuário no Teams.</span><span class="sxs-lookup"><span data-stu-id="809f6-128">Since existing data is being migrated, maintaining the original message timestamps and preventing messaging activity during the migration process are key to recreating the user's existing message flow in Teams.</span></span> <span data-ttu-id="809f6-129">Isso é feito da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="809f6-129">This is achieved as follows:</span></span>

> <span data-ttu-id="809f6-130">[Crie uma nova equipe](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um back-in-timestamp usando a propriedade de recurso da  `createdDateTime`  equipe.</span><span class="sxs-lookup"><span data-stu-id="809f6-130">[Create a new team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the team resource  `createdDateTime`  property.</span></span> <span data-ttu-id="809f6-131">Coloque a nova equipe em , um estado especial que barra os usuários da maioria das atividades dentro da equipe até `migration mode` que o processo de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="809f6-131">Place the new team in `migration mode`, a special state that bars users from most activities within the team until the migration process is complete.</span></span> <span data-ttu-id="809f6-132">Inclua o `teamCreationMode` atributo instance com o valor na `migration` solicitação POST para identificar explicitamente a nova equipe como sendo criada para migração.</span><span class="sxs-lookup"><span data-stu-id="809f6-132">Include the `teamCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  

> <span data-ttu-id="809f6-133">**OBSERVAÇÃO:** `createdDateTime` o campo só será preenchido para instâncias de uma equipe ou canal que foram migradas.</span><span class="sxs-lookup"><span data-stu-id="809f6-133">**NOTE**:  The `createdDateTime` field will only be populated for instances of a team or channel that have been migrated.</span></span>

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a><span data-ttu-id="809f6-134">Permissões</span><span class="sxs-lookup"><span data-stu-id="809f6-134">Permissions</span></span>

|<span data-ttu-id="809f6-135">ScopeName</span><span class="sxs-lookup"><span data-stu-id="809f6-135">ScopeName</span></span>|<span data-ttu-id="809f6-136">DisplayName</span><span class="sxs-lookup"><span data-stu-id="809f6-136">DisplayName</span></span>|<span data-ttu-id="809f6-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="809f6-137">Description</span></span>|<span data-ttu-id="809f6-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="809f6-138">Type</span></span>|<span data-ttu-id="809f6-139">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="809f6-139">Admin Consent?</span></span>|<span data-ttu-id="809f6-140">Entidades/APIs cobertas</span><span class="sxs-lookup"><span data-stu-id="809f6-140">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="809f6-141">Gerenciar a migração do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="809f6-141">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="809f6-142">Criando, gerenciando recursos para migração para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="809f6-142">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="809f6-143">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="809f6-143">**Application-only**</span></span>|<span data-ttu-id="809f6-144">**Sim**</span><span class="sxs-lookup"><span data-stu-id="809f6-144">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a><span data-ttu-id="809f6-145">Solicitar (criar uma equipe no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="809f6-145">Request (create a team in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="809f6-146">Resposta</span><span class="sxs-lookup"><span data-stu-id="809f6-146">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{teamId}/operations/{operationId}
Content-Location: /teams/{teamId}
```

#### <a name="error-messages"></a><span data-ttu-id="809f6-147">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="809f6-147">Error messages</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="809f6-148">`createdDateTime`  definido para o futuro.</span><span class="sxs-lookup"><span data-stu-id="809f6-148">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="809f6-149">`createdDateTime`  corretamente especificado, mas `teamCreationMode`  o atributo instance está ausente ou definido como valor inválido.</span><span class="sxs-lookup"><span data-stu-id="809f6-149">`createdDateTime`  correctly specified, but `teamCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-two-create-a-channel"></a><span data-ttu-id="809f6-150">Etapa dois: Criar um canal</span><span class="sxs-lookup"><span data-stu-id="809f6-150">Step Two: Create a channel</span></span>

<span data-ttu-id="809f6-151">Criar um canal para as mensagens importadas é semelhante ao cenário de criação de equipe:</span><span class="sxs-lookup"><span data-stu-id="809f6-151">Creating a channel for the imported messages is similar to the create team scenario:</span></span>

> <span data-ttu-id="809f6-152">[Crie um novo canal com](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) um back-in-timestamp usando a propriedade de recurso de `createdDateTime` canal.</span><span class="sxs-lookup"><span data-stu-id="809f6-152">[Create a new channel](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the channel resource `createdDateTime` property.</span></span> <span data-ttu-id="809f6-153">Coloque o novo canal em , um estado especial que barra os usuários da maioria das atividades de chat dentro do canal até `migration mode` que o processo de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="809f6-153">Place the new channel in `migration mode`, a special state that bars users from most chat activities within the channel until the migration process is complete.</span></span>  <span data-ttu-id="809f6-154">Inclua o `channelCreationMode` atributo instance com o valor na `migration` solicitação POST para identificar explicitamente a nova equipe como sendo criada para migração.</span><span class="sxs-lookup"><span data-stu-id="809f6-154">Include the `channelCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a><span data-ttu-id="809f6-155">Permissões</span><span class="sxs-lookup"><span data-stu-id="809f6-155">Permissions</span></span>

|<span data-ttu-id="809f6-156">ScopeName</span><span class="sxs-lookup"><span data-stu-id="809f6-156">ScopeName</span></span>|<span data-ttu-id="809f6-157">DisplayName</span><span class="sxs-lookup"><span data-stu-id="809f6-157">DisplayName</span></span>|<span data-ttu-id="809f6-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="809f6-158">Description</span></span>|<span data-ttu-id="809f6-159">Tipo</span><span class="sxs-lookup"><span data-stu-id="809f6-159">Type</span></span>|<span data-ttu-id="809f6-160">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="809f6-160">Admin Consent?</span></span>|<span data-ttu-id="809f6-161">Entidades/APIs cobertas</span><span class="sxs-lookup"><span data-stu-id="809f6-161">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="809f6-162">Gerenciar a migração do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="809f6-162">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="809f6-163">Criando, gerenciando recursos para migração para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="809f6-163">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="809f6-164">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="809f6-164">**Application-only**</span></span>|<span data-ttu-id="809f6-165">**Sim**</span><span class="sxs-lookup"><span data-stu-id="809f6-165">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a><span data-ttu-id="809f6-166">Solicitar (criar um canal no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="809f6-166">Request (create a channel in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="809f6-167">Resposta</span><span class="sxs-lookup"><span data-stu-id="809f6-167">Response</span></span>

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

#### <a name="error-message"></a><span data-ttu-id="809f6-168">Mensagem de erro</span><span class="sxs-lookup"><span data-stu-id="809f6-168">Error message</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="809f6-169">`createdDateTime`  definido para o futuro.</span><span class="sxs-lookup"><span data-stu-id="809f6-169">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="809f6-170">`createdDateTime`  especificado corretamente, mas `channelCreationMode`  o atributo instance está ausente ou definido como um valor inválido.</span><span class="sxs-lookup"><span data-stu-id="809f6-170">`createdDateTime`  correctly specified but `channelCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-three-import-messages"></a><span data-ttu-id="809f6-171">Etapa três: Importar mensagens</span><span class="sxs-lookup"><span data-stu-id="809f6-171">Step Three: Import messages</span></span>

<span data-ttu-id="809f6-172">Depois que a equipe e o canal foram criados, você pode começar a enviar mensagens de back-in-time usando as chaves no `createdDateTime` `from`  corpo da solicitação.</span><span class="sxs-lookup"><span data-stu-id="809f6-172">After the team and channel have been created, you can begin sending back-in-time messages using the `createdDateTime`  and `from`  keys in the request body.</span></span> <span data-ttu-id="809f6-173">**OBSERVAÇÃO:** não há suporte `createdDateTime` para mensagens importadas com o thread de `createdDateTime` mensagens anteriores ao thread.</span><span class="sxs-lookup"><span data-stu-id="809f6-173">**NOTE**: messages imported with `createdDateTime` earlier than the message thread `createdDateTime` is not supported.</span></span>

> [!NOTE]
> * <span data-ttu-id="809f6-174">`createdDateTime` deve ser exclusivo em todas as mensagens no mesmo thread.</span><span class="sxs-lookup"><span data-stu-id="809f6-174">`createdDateTime` must be unique across messages in the same thread.</span></span>
> * <span data-ttu-id="809f6-175">`createdDateTime` dá suporte a timestamps com precisão de milissegundos.</span><span class="sxs-lookup"><span data-stu-id="809f6-175">`createdDateTime` supports timestamps with milliseconds precision.</span></span> <span data-ttu-id="809f6-176">Por exemplo, se a mensagem de solicitação de entrada tiver o valor definido como `createdDateTime` *2020-09-16T05:50:31.0025302Z,* ela será convertida em *2020-09-16T05:50:31.002Z* quando a mensagem for ingerida.</span><span class="sxs-lookup"><span data-stu-id="809f6-176">For example, if the incoming request message has the value of `createdDateTime` set as *2020-09-16T05:50:31.0025302Z*, then it would be converted to *2020-09-16T05:50:31.002Z* when the message is ingested.</span></span>

#### <a name="request-post-message-that-is-text-only"></a><span data-ttu-id="809f6-177">Request (POST message that is text-only)</span><span class="sxs-lookup"><span data-stu-id="809f6-177">Request (POST message that is text-only)</span></span>

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

#### <a name="response"></a><span data-ttu-id="809f6-178">Resposta</span><span class="sxs-lookup"><span data-stu-id="809f6-178">Response</span></span>

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

#### <a name="error-messages"></a><span data-ttu-id="809f6-179">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="809f6-179">Error messages</span></span>

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a><span data-ttu-id="809f6-180">Solicitar (POSTAR uma mensagem com imagem em linha)</span><span class="sxs-lookup"><span data-stu-id="809f6-180">Request (POST a message with inline image)</span></span>

> <span data-ttu-id="809f6-181">**Observação:** não há escopos de permissão especiais neste cenário, pois a solicitação faz parte do chatMessage; os escopos de chatMessage também se aplicam aqui.</span><span class="sxs-lookup"><span data-stu-id="809f6-181">**Note**: There are no special permission scopes in this scenario since the request is part of chatMessage; scopes for chatMessage apply here as well.</span></span>

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

#### <a name="response"></a><span data-ttu-id="809f6-182">Resposta</span><span class="sxs-lookup"><span data-stu-id="809f6-182">Response</span></span>

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

## <a name="step-four-complete-migration-mode"></a><span data-ttu-id="809f6-183">Etapa quatro: Concluir o modo de migração</span><span class="sxs-lookup"><span data-stu-id="809f6-183">Step Four: Complete migration mode</span></span>

<span data-ttu-id="809f6-184">Depois que o processo de migração de mensagens é concluído, a equipe e o canal são retirados do modo de migração usando o  `completeMigration`  método.</span><span class="sxs-lookup"><span data-stu-id="809f6-184">Once the message migration process has completed, both the team and channel are taken out of migration mode using the  `completeMigration`  method.</span></span> <span data-ttu-id="809f6-185">Esta etapa abre os recursos de equipe e canal para uso geral pelos membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="809f6-185">This step opens the team and channel resources for general use by team members.</span></span> <span data-ttu-id="809f6-186">A ação é vinculada à `team` instância.</span><span class="sxs-lookup"><span data-stu-id="809f6-186">The action is bound to the `team` instance.</span></span>

#### <a name="request-end-team-migration-mode"></a><span data-ttu-id="809f6-187">Solicitação (modo de migração de equipe final)</span><span class="sxs-lookup"><span data-stu-id="809f6-187">Request (end team migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="809f6-188">Resposta</span><span class="sxs-lookup"><span data-stu-id="809f6-188">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-channel-migration-mode"></a><span data-ttu-id="809f6-189">Solicitação (modo de migração de canal final)</span><span class="sxs-lookup"><span data-stu-id="809f6-189">Request (end channel migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="809f6-190">Resposta</span><span class="sxs-lookup"><span data-stu-id="809f6-190">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="error-response"></a><span data-ttu-id="809f6-191">Resposta de erro</span><span class="sxs-lookup"><span data-stu-id="809f6-191">Error response</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="809f6-192">Ação chamada em um `team` ou que não está em `channel` `migrationMode` .</span><span class="sxs-lookup"><span data-stu-id="809f6-192">Action called on a `team` or `channel` that is not in `migrationMode`.</span></span>

## <a name="step-five-add-team-members"></a><span data-ttu-id="809f6-193">Etapa cinco: Adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="809f6-193">Step Five: Add team members</span></span>

<span data-ttu-id="809f6-194">Você pode adicionar um membro a uma equipe usando a interface do usuário do [Teams](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) ou a API adicionar [membro do](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) Microsoft Graph:</span><span class="sxs-lookup"><span data-stu-id="809f6-194">You can add a member to a team [using the Teams UI](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) or Microsoft Graph [Add member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:</span></span>

#### <a name="request-add-member"></a><span data-ttu-id="809f6-195">Solicitar (adicionar membro)</span><span class="sxs-lookup"><span data-stu-id="809f6-195">Request (add member)</span></span>

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

#### <a name="response"></a><span data-ttu-id="809f6-196">Resposta</span><span class="sxs-lookup"><span data-stu-id="809f6-196">Response</span></span>

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a><span data-ttu-id="809f6-197">Dicas e informações adicionais</span><span class="sxs-lookup"><span data-stu-id="809f6-197">Tips and additional information</span></span>

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* <span data-ttu-id="809f6-198">Você pode importar mensagens de usuários que não estão no Teams.</span><span class="sxs-lookup"><span data-stu-id="809f6-198">You can import messages from users who are not in Teams.</span></span> <span data-ttu-id="809f6-199">**OBSERVAÇÃO:** as mensagens importadas para usuários não presentes no locatário não serão pesquisáveis no cliente do Teams ou nos portais de conformidade durante a Visualização Pública.</span><span class="sxs-lookup"><span data-stu-id="809f6-199">**NOTE**: Messages imported for users not present in the tenant will not be searchable in the Teams client or compliance portals during Public Preview.</span></span>

* <span data-ttu-id="809f6-200">Depois que `completeMigration` a solicitação for feita, você não poderá importar mais mensagens para a equipe.</span><span class="sxs-lookup"><span data-stu-id="809f6-200">Once the `completeMigration` request is made, you cannot import further messages into the team.</span></span>

* <span data-ttu-id="809f6-201">Os membros da equipe só podem ser adicionados à nova equipe após a `completeMigration` solicitação ter retornado uma resposta bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="809f6-201">Team members can only be added to the new team after the `completeMigration` request has returned a successful response.</span></span>

* <span data-ttu-id="809f6-202">Throttling: As mensagens são importadas a 5 RPS por canal.</span><span class="sxs-lookup"><span data-stu-id="809f6-202">Throttling: Messages import at 5 RPS per channel.</span></span>

* <span data-ttu-id="809f6-203">Se você precisar fazer uma correção nos resultados da migração, será necessário excluir a equipe e repetir as etapas para criar a equipe e o canal e migrar as mensagens.</span><span class="sxs-lookup"><span data-stu-id="809f6-203">If you need to make a correction to the migration results, you need to delete the team and repeat the steps to create the team and channel and re-migrate the messages.</span></span>

> [!NOTE]
> <span data-ttu-id="809f6-204">Atualmente, as imagens em linha são o único tipo de mídia suportado pelo esquema de API de importação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="809f6-204">Currently, inline images are the only type of media supported by the import message API schema.</span></span>

##### <a name="import-content-scope"></a><span data-ttu-id="809f6-205">Importar escopo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="809f6-205">Import content scope</span></span>

|<span data-ttu-id="809f6-206">No escopo</span><span class="sxs-lookup"><span data-stu-id="809f6-206">In-scope</span></span> | <span data-ttu-id="809f6-207">Fora do escopo no momento</span><span class="sxs-lookup"><span data-stu-id="809f6-207">Currently out-of-scope</span></span>|
|----------|--------------------------|
|<span data-ttu-id="809f6-208">Mensagens de equipe e canal</span><span class="sxs-lookup"><span data-stu-id="809f6-208">Team and channel messages</span></span>|<span data-ttu-id="809f6-209">Mensagens de bate-papo de grupo e 1:1</span><span class="sxs-lookup"><span data-stu-id="809f6-209">1:1 and group chat messages</span></span>|
|<span data-ttu-id="809f6-210">Hora de criação da mensagem original</span><span class="sxs-lookup"><span data-stu-id="809f6-210">Created time of the original message</span></span>|<span data-ttu-id="809f6-211">Canais privados</span><span class="sxs-lookup"><span data-stu-id="809f6-211">Private channels</span></span>|
|<span data-ttu-id="809f6-212">Imagens em linha como parte da mensagem</span><span class="sxs-lookup"><span data-stu-id="809f6-212">Inline images as part of the message</span></span>|<span data-ttu-id="809f6-213">Em menções</span><span class="sxs-lookup"><span data-stu-id="809f6-213">At mentions</span></span>|
|<span data-ttu-id="809f6-214">Links para arquivos existentes no SPO/OneDrive</span><span class="sxs-lookup"><span data-stu-id="809f6-214">Links to existing files in SPO/OneDrive</span></span>|<span data-ttu-id="809f6-215">Reações</span><span class="sxs-lookup"><span data-stu-id="809f6-215">Reactions</span></span>|
|<span data-ttu-id="809f6-216">Mensagens com rich text</span><span class="sxs-lookup"><span data-stu-id="809f6-216">Messages with rich text</span></span>|<span data-ttu-id="809f6-217">Vídeos</span><span class="sxs-lookup"><span data-stu-id="809f6-217">Videos</span></span>|
|<span data-ttu-id="809f6-218">Cadeia de resposta de mensagens</span><span class="sxs-lookup"><span data-stu-id="809f6-218">Message reply chain</span></span>|<span data-ttu-id="809f6-219">Announcements</span><span class="sxs-lookup"><span data-stu-id="809f6-219">Announcements</span></span>|
|<span data-ttu-id="809f6-220">Processamento de alta taxa de transferência</span><span class="sxs-lookup"><span data-stu-id="809f6-220">High throughput processing</span></span>|<span data-ttu-id="809f6-221">Trechos de código</span><span class="sxs-lookup"><span data-stu-id="809f6-221">Code snippets</span></span>|
||<span data-ttu-id="809f6-222">Cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="809f6-222">Adaptive cards</span></span>|
||<span data-ttu-id="809f6-223">Figurinhas</span><span class="sxs-lookup"><span data-stu-id="809f6-223">Stickers</span></span>|
||<span data-ttu-id="809f6-224">Emojis</span><span class="sxs-lookup"><span data-stu-id="809f6-224">Emojis</span></span>|
||<span data-ttu-id="809f6-225">Aspas</span><span class="sxs-lookup"><span data-stu-id="809f6-225">Quotes</span></span>|
||<span data-ttu-id="809f6-226">Postagens cruzadas entre canais</span><span class="sxs-lookup"><span data-stu-id="809f6-226">Cross posts between channels</span></span>|

> [!div class="nextstepaction"]
>[<span data-ttu-id="809f6-227">Saiba mais sobre a integração do Microsoft Graph e do Teams</span><span class="sxs-lookup"><span data-stu-id="809f6-227">Learn more about Microsoft Graph and Teams integration</span></span>](/graph/teams-concept-overview)
