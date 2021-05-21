---
title: Use o Microsoft Graph para importar mensagens de plataforma externa para Teams
description: Descreve como usar o Microsoft Graph para importar mensagens de uma plataforma externa para Teams
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: teams import messages api graph microsoft migrar migration post
ms.openlocfilehash: 5ea06e8b490bae0595abb31086848d0b050bded0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566156"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a><span data-ttu-id="d2069-104">Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="d2069-104">Import third-party platform messages to Teams using Microsoft Graph</span></span>

<span data-ttu-id="d2069-105">Com o Microsoft Graph, você pode migrar o histórico de mensagens e os dados existentes dos usuários de um sistema externo para um canal Teams.</span><span class="sxs-lookup"><span data-stu-id="d2069-105">With Microsoft Graph, you can migrate users' existing message history and data from an external system into a Teams channel.</span></span> <span data-ttu-id="d2069-106">Ao habilitar a recriação de uma hierarquia de mensagens de plataforma de terceiros dentro Teams, os usuários podem continuar suas comunicações de maneira perfeita e continuar sem interrupção.</span><span class="sxs-lookup"><span data-stu-id="d2069-106">By enabling the recreation of a third-party platform messaging hierarchy inside Teams, users can continue their communications in a seamless manner and proceed without interruption.</span></span>

> [!NOTE] 
> <span data-ttu-id="d2069-107">No futuro, a Microsoft pode exigir que você ou seus clientes paguem taxas adicionais com base na quantidade de dados importados.</span><span class="sxs-lookup"><span data-stu-id="d2069-107">In the future, Microsoft may require you or your customers to pay additional fees based on the amount of data imported.</span></span>

## <a name="import-overview"></a><span data-ttu-id="d2069-108">Visão geral de importação</span><span class="sxs-lookup"><span data-stu-id="d2069-108">Import overview</span></span>

<span data-ttu-id="d2069-109">Em um nível alto, o processo de importação consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="d2069-109">At a high level, the import process consists of the following:</span></span>

1. [<span data-ttu-id="d2069-110">Criar uma equipe com um back-in-timestamp</span><span class="sxs-lookup"><span data-stu-id="d2069-110">Create a team with a back-in-time timestamp</span></span>](#step-one-create-a-team)
1. [<span data-ttu-id="d2069-111">Criar um canal com um back-in-timestamp</span><span class="sxs-lookup"><span data-stu-id="d2069-111">Create a channel with a back-in-time timestamp</span></span>](#step-two-create-a-channel) 
1. [<span data-ttu-id="d2069-112">Importar mensagens datadas de back-in-time externas</span><span class="sxs-lookup"><span data-stu-id="d2069-112">Import external back-in-time dated messages</span></span>](#step-three-import-messages)
1. [<span data-ttu-id="d2069-113">Concluir o processo de migração de equipe e canal</span><span class="sxs-lookup"><span data-stu-id="d2069-113">Complete the team and channel migration process</span></span>](#step-four-complete-migration-mode)
1. [<span data-ttu-id="d2069-114">Adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="d2069-114">Add team members</span></span>](#step-five-add-team-members)

## <a name="necessary-requirements"></a><span data-ttu-id="d2069-115">Requisitos necessários</span><span class="sxs-lookup"><span data-stu-id="d2069-115">Necessary requirements</span></span>

### <a name="analyze-and-prepare-message-data"></a><span data-ttu-id="d2069-116">Analisar e preparar dados de mensagens</span><span class="sxs-lookup"><span data-stu-id="d2069-116">Analyze and prepare message data</span></span>

<span data-ttu-id="d2069-117">✔ revise os dados de terceiros para decidir o que será migrado.</span><span class="sxs-lookup"><span data-stu-id="d2069-117">✔ Review the third-party data to decide what will be migrated.</span></span>  
<span data-ttu-id="d2069-118">✔ Extrair os dados selecionados do sistema de chat de terceiros.</span><span class="sxs-lookup"><span data-stu-id="d2069-118">✔ Extract the selected data from the third-party chat system.</span></span>  
<span data-ttu-id="d2069-119">✔ mapear a estrutura de chat de terceiros para a estrutura Teams de terceiros.</span><span class="sxs-lookup"><span data-stu-id="d2069-119">✔ Map the third-party chat structure to the Teams structure.</span></span>  
<span data-ttu-id="d2069-120">✔ Converter dados de importação no formato necessário para a migração.</span><span class="sxs-lookup"><span data-stu-id="d2069-120">✔ Convert import data into format needed for migration.</span></span>  

### <a name="set-up-your-office-365-tenant"></a><span data-ttu-id="d2069-121">Configurar seu locatário do Office 365</span><span class="sxs-lookup"><span data-stu-id="d2069-121">Set up your Office 365 tenant</span></span>

<span data-ttu-id="d2069-122">✔ certifique-se de que exista Office 365 locatário para os dados de importação.</span><span class="sxs-lookup"><span data-stu-id="d2069-122">✔ Ensure that an Office 365 tenant exists for the import data.</span></span> <span data-ttu-id="d2069-123">Para obter mais informações sobre como configurar um Office 365 locatário para Teams, consulte [Prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="d2069-123">For more information on setting up an Office 365 tenancy for Teams, see [Prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>  
<span data-ttu-id="d2069-124">✔ Certifique-se de que os membros da equipe estão Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="d2069-124">✔ Make sure that team members are in Azure Active Directory (AAD).</span></span>  <span data-ttu-id="d2069-125">Para obter mais informações, [consulte Add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d2069-125">For more information, see [Add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to Azure Active Directory.</span></span>

## <a name="step-one-create-a-team"></a><span data-ttu-id="d2069-126">Etapa Um: Criar uma equipe</span><span class="sxs-lookup"><span data-stu-id="d2069-126">Step One: Create a team</span></span>

<span data-ttu-id="d2069-127">Como os dados existentes estão sendo migrados, a manutenção dos datas de data/hora originais da mensagem e a prevenção da atividade de mensagens durante o processo de migração são fundamentais para recriar o fluxo de mensagens existente do usuário no Teams.</span><span class="sxs-lookup"><span data-stu-id="d2069-127">Since existing data is being migrated, maintaining the original message timestamps and preventing messaging activity during the migration process are key to recreating the user's existing message flow in Teams.</span></span> <span data-ttu-id="d2069-128">Isso é alcançado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d2069-128">This is achieved as follows:</span></span>

> <span data-ttu-id="d2069-129">[Crie uma nova equipe](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um back-in-timestamp usando a propriedade de recurso de  `createdDateTime`  equipe.</span><span class="sxs-lookup"><span data-stu-id="d2069-129">[Create a new team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the team resource  `createdDateTime`  property.</span></span> <span data-ttu-id="d2069-130">Coloque a nova equipe em , um estado especial que barra os usuários da maioria das atividades dentro da equipe até que o processo `migration mode` de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="d2069-130">Place the new team in `migration mode`, a special state that bars users from most activities within the team until the migration process is complete.</span></span> <span data-ttu-id="d2069-131">Inclua o atributo instance com o valor na solicitação POST para identificar explicitamente a `teamCreationMode` nova equipe como sendo criada para `migration` migração.</span><span class="sxs-lookup"><span data-stu-id="d2069-131">Include the `teamCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  

> [!Note]
> <span data-ttu-id="d2069-132">O `createdDateTime` campo só será preenchido para instâncias de uma equipe ou canal que foram migradas.</span><span class="sxs-lookup"><span data-stu-id="d2069-132">The `createdDateTime` field will only be populated for instances of a team or channel that have been migrated.</span></span>

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a><span data-ttu-id="d2069-133">Permissões</span><span class="sxs-lookup"><span data-stu-id="d2069-133">Permissions</span></span>

|<span data-ttu-id="d2069-134">ScopeName</span><span class="sxs-lookup"><span data-stu-id="d2069-134">ScopeName</span></span>|<span data-ttu-id="d2069-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d2069-135">DisplayName</span></span>|<span data-ttu-id="d2069-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2069-136">Description</span></span>|<span data-ttu-id="d2069-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="d2069-137">Type</span></span>|<span data-ttu-id="d2069-138">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="d2069-138">Admin Consent?</span></span>|<span data-ttu-id="d2069-139">Entidades/APIs cobertas</span><span class="sxs-lookup"><span data-stu-id="d2069-139">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="d2069-140">Gerenciar a migração do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d2069-140">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="d2069-141">Criando, gerenciando recursos para migração para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d2069-141">Creating, managing resources for migration to Microsoft Teams.</span></span>|<span data-ttu-id="d2069-142">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="d2069-142">**Application-only**</span></span>|<span data-ttu-id="d2069-143">**Sim**</span><span class="sxs-lookup"><span data-stu-id="d2069-143">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a><span data-ttu-id="d2069-144">Solicitação (criar uma equipe no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="d2069-144">Request (create a team in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="d2069-145">Resposta</span><span class="sxs-lookup"><span data-stu-id="d2069-145">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{team-id}/operations/{operation-id}
Content-Location: /teams/{team-id}
```

#### <a name="error-messages"></a><span data-ttu-id="d2069-146">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="d2069-146">Error messages</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="d2069-147">`createdDateTime`  definido para o futuro.</span><span class="sxs-lookup"><span data-stu-id="d2069-147">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="d2069-148">`createdDateTime`  corretamente especificado, mas o atributo `teamCreationMode`  instance está ausente ou definido como valor inválido.</span><span class="sxs-lookup"><span data-stu-id="d2069-148">`createdDateTime`  correctly specified, but `teamCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-two-create-a-channel"></a><span data-ttu-id="d2069-149">Etapa Dois: Criar um canal</span><span class="sxs-lookup"><span data-stu-id="d2069-149">Step Two: Create a channel</span></span>

<span data-ttu-id="d2069-150">A criação de um canal para as mensagens importadas é semelhante ao cenário de criação de equipe:</span><span class="sxs-lookup"><span data-stu-id="d2069-150">Creating a channel for the imported messages is similar to the create team scenario:</span></span>

> <span data-ttu-id="d2069-151">[Crie um novo canal](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) com um back-in-timestamp usando a propriedade de recurso `createdDateTime` channel.</span><span class="sxs-lookup"><span data-stu-id="d2069-151">[Create a new channel](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) with a back-in-time timestamp using the channel resource `createdDateTime` property.</span></span> <span data-ttu-id="d2069-152">Coloque o novo canal em , um estado especial que barra os usuários da maioria das atividades de chat dentro do canal até que o processo `migration mode` de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="d2069-152">Place the new channel in `migration mode`, a special state that bars users from most chat activities within the channel until the migration process is complete.</span></span>  <span data-ttu-id="d2069-153">Inclua o atributo instance com o valor na solicitação POST para identificar explicitamente a `channelCreationMode` nova equipe como sendo criada para `migration` migração.</span><span class="sxs-lookup"><span data-stu-id="d2069-153">Include the `channelCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a><span data-ttu-id="d2069-154">Permissões</span><span class="sxs-lookup"><span data-stu-id="d2069-154">Permissions</span></span>

|<span data-ttu-id="d2069-155">ScopeName</span><span class="sxs-lookup"><span data-stu-id="d2069-155">ScopeName</span></span>|<span data-ttu-id="d2069-156">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d2069-156">DisplayName</span></span>|<span data-ttu-id="d2069-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2069-157">Description</span></span>|<span data-ttu-id="d2069-158">Tipo</span><span class="sxs-lookup"><span data-stu-id="d2069-158">Type</span></span>|<span data-ttu-id="d2069-159">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="d2069-159">Admin Consent?</span></span>|<span data-ttu-id="d2069-160">Entidades/APIs cobertas</span><span class="sxs-lookup"><span data-stu-id="d2069-160">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="d2069-161">Gerenciar a migração do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d2069-161">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="d2069-162">Criando, gerenciando recursos para migração para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d2069-162">Creating, managing resources for migration to Microsoft Teams.</span></span>|<span data-ttu-id="d2069-163">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="d2069-163">**Application-only**</span></span>|<span data-ttu-id="d2069-164">**Sim**</span><span class="sxs-lookup"><span data-stu-id="d2069-164">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a><span data-ttu-id="d2069-165">Solicitação (criar um canal no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="d2069-165">Request (create a channel in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="d2069-166">Resposta</span><span class="sxs-lookup"><span data-stu-id="d2069-166">Response</span></span>

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

#### <a name="error-message"></a><span data-ttu-id="d2069-167">Mensagem de erro</span><span class="sxs-lookup"><span data-stu-id="d2069-167">Error message</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="d2069-168">`createdDateTime`  definido para o futuro.</span><span class="sxs-lookup"><span data-stu-id="d2069-168">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="d2069-169">`createdDateTime`  corretamente especificado, mas `channelCreationMode`  o atributo instance está ausente ou definido como valor inválido.</span><span class="sxs-lookup"><span data-stu-id="d2069-169">`createdDateTime`  correctly specified but `channelCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-three-import-messages"></a><span data-ttu-id="d2069-170">Etapa Três: Importar mensagens</span><span class="sxs-lookup"><span data-stu-id="d2069-170">Step Three: Import messages</span></span>

<span data-ttu-id="d2069-171">Depois que a equipe e o canal foram criados, você pode começar a enviar mensagens de back-in-time usando as chaves e `createdDateTime` `from`  no corpo da solicitação.</span><span class="sxs-lookup"><span data-stu-id="d2069-171">After the team and channel have been created, you can begin sending back-in-time messages using the `createdDateTime`  and `from`  keys in the request body.</span></span> <span data-ttu-id="d2069-172">**OBSERVAÇÃO:** não há suporte para mensagens `createdDateTime` importadas com o thread de `createdDateTime` mensagem anterior ao thread da mensagem.</span><span class="sxs-lookup"><span data-stu-id="d2069-172">**NOTE**: messages imported with `createdDateTime` earlier than the message thread `createdDateTime` is not supported.</span></span>

> [!NOTE]
> * <span data-ttu-id="d2069-173">`createdDateTime` deve ser exclusivo entre mensagens no mesmo thread.</span><span class="sxs-lookup"><span data-stu-id="d2069-173">`createdDateTime` must be unique across messages in the same thread.</span></span>
> * <span data-ttu-id="d2069-174">`createdDateTime` oferece suporte a data/hora com precisão de milissegundos.</span><span class="sxs-lookup"><span data-stu-id="d2069-174">`createdDateTime` supports timestamps with milliseconds precision.</span></span> <span data-ttu-id="d2069-175">Por exemplo, se a mensagem de solicitação de entrada tiver o valor definido como `createdDateTime` *2020-09-16T05:50:31.0025302Z*, ela será convertida em *2020-09-16T05:50:31.002Z* quando a mensagem for ingerida.</span><span class="sxs-lookup"><span data-stu-id="d2069-175">For example, if the incoming request message has the value of `createdDateTime` set as *2020-09-16T05:50:31.0025302Z*, then it would be converted to *2020-09-16T05:50:31.002Z* when the message is ingested.</span></span>

#### <a name="request-post-message-that-is-text-only"></a><span data-ttu-id="d2069-176">Solicitação (mensagem POST que é somente texto)</span><span class="sxs-lookup"><span data-stu-id="d2069-176">Request (POST message that is text-only)</span></span>

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

#### <a name="response"></a><span data-ttu-id="d2069-177">Resposta</span><span class="sxs-lookup"><span data-stu-id="d2069-177">Response</span></span>

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

#### <a name="error-messages"></a><span data-ttu-id="d2069-178">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="d2069-178">Error messages</span></span>

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a><span data-ttu-id="d2069-179">Solicitar (POSTAR uma mensagem com imagem em linha)</span><span class="sxs-lookup"><span data-stu-id="d2069-179">Request (POST a message with inline image)</span></span>

> [!Note]
> <span data-ttu-id="d2069-180">Não há escopos de permissão especiais nesse cenário, pois a solicitação faz parte do chatMessage; os escopos para chatMessage também se aplicam aqui.</span><span class="sxs-lookup"><span data-stu-id="d2069-180">There are no special permission scopes in this scenario since the request is part of chatMessage; scopes for chatMessage apply here as well.</span></span>

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

#### <a name="response"></a><span data-ttu-id="d2069-181">Resposta</span><span class="sxs-lookup"><span data-stu-id="d2069-181">Response</span></span>

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

## <a name="step-four-complete-migration-mode"></a><span data-ttu-id="d2069-182">Etapa quatro: concluir o modo de migração</span><span class="sxs-lookup"><span data-stu-id="d2069-182">Step Four: Complete migration mode</span></span>

<span data-ttu-id="d2069-183">Depois que o processo de migração de mensagens é concluído, a equipe e o canal são retirados do modo de migração usando o  `completeMigration`  método.</span><span class="sxs-lookup"><span data-stu-id="d2069-183">Once the message migration process has completed, both the team and channel are taken out of migration mode using the  `completeMigration`  method.</span></span> <span data-ttu-id="d2069-184">Esta etapa abre os recursos de equipe e canal para uso geral pelos membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="d2069-184">This step opens the team and channel resources for general use by team members.</span></span> <span data-ttu-id="d2069-185">A ação está vinculada à `team` instância.</span><span class="sxs-lookup"><span data-stu-id="d2069-185">The action is bound to the `team` instance.</span></span> <span data-ttu-id="d2069-186">Todos os canais devem ser concluídos fora do modo de migração antes que a equipe possa ser concluída.</span><span class="sxs-lookup"><span data-stu-id="d2069-186">All channels must be completed out of migration mode before the team can be completed.</span></span>

#### <a name="request-end-channel-migration-mode"></a><span data-ttu-id="d2069-187">Solicitação (modo de migração de canal final)</span><span class="sxs-lookup"><span data-stu-id="d2069-187">Request (end channel migration mode)</span></span>

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/completeMigration

```

#### <a name="response"></a><span data-ttu-id="d2069-188">Resposta</span><span class="sxs-lookup"><span data-stu-id="d2069-188">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-team-migration-mode"></a><span data-ttu-id="d2069-189">Solicitação (modo de migração de equipe final)</span><span class="sxs-lookup"><span data-stu-id="d2069-189">Request (end team migration mode)</span></span>

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/completeMigration
```

#### <a name="response"></a><span data-ttu-id="d2069-190">Resposta</span><span class="sxs-lookup"><span data-stu-id="d2069-190">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

* <span data-ttu-id="d2069-191">Ação chamada em um `team` ou que não está em `channel` `migrationMode` .</span><span class="sxs-lookup"><span data-stu-id="d2069-191">Action called on a `team` or `channel` that is not in `migrationMode`.</span></span>

## <a name="step-five-add-team-members"></a><span data-ttu-id="d2069-192">Etapa Cinco: Adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="d2069-192">Step Five: Add team members</span></span>

<span data-ttu-id="d2069-193">Você pode adicionar um membro a uma equipe usando a interface [do usuário Teams ou](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) a API de membro do Microsoft Graph [Adicionar:](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="d2069-193">You can add a member to a team [using the Teams UI](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) or Microsoft Graph [Add member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:</span></span>

#### <a name="request-add-member"></a><span data-ttu-id="d2069-194">Solicitação (adicionar membro)</span><span class="sxs-lookup"><span data-stu-id="d2069-194">Request (add member)</span></span>

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

#### <a name="response"></a><span data-ttu-id="d2069-195">Resposta</span><span class="sxs-lookup"><span data-stu-id="d2069-195">Response</span></span>

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a><span data-ttu-id="d2069-196">Dicas informações adicionais</span><span class="sxs-lookup"><span data-stu-id="d2069-196">Tips and additional information</span></span>

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* <span data-ttu-id="d2069-197">Depois que `completeMigration` a solicitação for feita, você não poderá importar mais mensagens para a equipe.</span><span class="sxs-lookup"><span data-stu-id="d2069-197">Once the `completeMigration` request is made, you cannot import further messages into the team.</span></span>

* <span data-ttu-id="d2069-198">Os membros da equipe só podem ser adicionados à nova equipe após a solicitação `completeMigration` ter retornado uma resposta bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d2069-198">Team members can only be added to the new team after the `completeMigration` request has returned a successful response.</span></span>

* <span data-ttu-id="d2069-199">Throttling: As mensagens são importadas em 5 RPS por canal.</span><span class="sxs-lookup"><span data-stu-id="d2069-199">Throttling: Messages import at 5 RPS per channel.</span></span>

* <span data-ttu-id="d2069-200">Se você precisar fazer uma correção nos resultados da migração, será necessário excluir a equipe e repetir as etapas para criar a equipe e o canal e migrar as mensagens.</span><span class="sxs-lookup"><span data-stu-id="d2069-200">If you need to make a correction to the migration results, you need to delete the team and repeat the steps to create the team and channel and re-migrate the messages.</span></span>

> [!NOTE]
> <span data-ttu-id="d2069-201">Atualmente, as imagens em linha são o único tipo de mídia com suporte pelo esquema de API de mensagem de importação.</span><span class="sxs-lookup"><span data-stu-id="d2069-201">Currently, inline images are the only type of media supported by the import message API schema.</span></span>

##### <a name="import-content-scope"></a><span data-ttu-id="d2069-202">Importar escopo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="d2069-202">Import content scope</span></span>

|<span data-ttu-id="d2069-203">No escopo</span><span class="sxs-lookup"><span data-stu-id="d2069-203">In-scope</span></span> | <span data-ttu-id="d2069-204">Atualmente fora do escopo</span><span class="sxs-lookup"><span data-stu-id="d2069-204">Currently out-of-scope</span></span>|
|----------|--------------------------|
|<span data-ttu-id="d2069-205">Mensagens de equipe e canal</span><span class="sxs-lookup"><span data-stu-id="d2069-205">Team and channel messages</span></span>|<span data-ttu-id="d2069-206">1:1 e mensagens de chat de grupo</span><span class="sxs-lookup"><span data-stu-id="d2069-206">1:1 and group chat messages</span></span>|
|<span data-ttu-id="d2069-207">Hora de criação da mensagem original</span><span class="sxs-lookup"><span data-stu-id="d2069-207">Created time of the original message</span></span>|<span data-ttu-id="d2069-208">Canais privados</span><span class="sxs-lookup"><span data-stu-id="d2069-208">Private channels</span></span>|
|<span data-ttu-id="d2069-209">Imagens em linha como parte da mensagem</span><span class="sxs-lookup"><span data-stu-id="d2069-209">Inline images as part of the message</span></span>|<span data-ttu-id="d2069-210">At mentions</span><span class="sxs-lookup"><span data-stu-id="d2069-210">At mentions</span></span>|
|<span data-ttu-id="d2069-211">Links para arquivos existentes no SPO/OneDrive</span><span class="sxs-lookup"><span data-stu-id="d2069-211">Links to existing files in SPO/OneDrive</span></span>|<span data-ttu-id="d2069-212">Reações</span><span class="sxs-lookup"><span data-stu-id="d2069-212">Reactions</span></span>|
|<span data-ttu-id="d2069-213">Mensagens com texto rico</span><span class="sxs-lookup"><span data-stu-id="d2069-213">Messages with rich text</span></span>|<span data-ttu-id="d2069-214">Vídeos</span><span class="sxs-lookup"><span data-stu-id="d2069-214">Videos</span></span>|
|<span data-ttu-id="d2069-215">Cadeia de resposta de mensagens</span><span class="sxs-lookup"><span data-stu-id="d2069-215">Message reply chain</span></span>|<span data-ttu-id="d2069-216">Announcements</span><span class="sxs-lookup"><span data-stu-id="d2069-216">Announcements</span></span>|
|<span data-ttu-id="d2069-217">Processamento de alta taxa de transferência</span><span class="sxs-lookup"><span data-stu-id="d2069-217">High throughput processing</span></span>|<span data-ttu-id="d2069-218">Trechos de código</span><span class="sxs-lookup"><span data-stu-id="d2069-218">Code snippets</span></span>|
||<span data-ttu-id="d2069-219">Adesivos</span><span class="sxs-lookup"><span data-stu-id="d2069-219">Stickers</span></span>|
||<span data-ttu-id="d2069-220">Emojis</span><span class="sxs-lookup"><span data-stu-id="d2069-220">Emojis</span></span>|
||<span data-ttu-id="d2069-221">Cotações</span><span class="sxs-lookup"><span data-stu-id="d2069-221">Quotes</span></span>|
||<span data-ttu-id="d2069-222">Postagens entre canais</span><span class="sxs-lookup"><span data-stu-id="d2069-222">Cross posts between channels</span></span>|


## <a name="see-also"></a><span data-ttu-id="d2069-223">Confira também</span><span class="sxs-lookup"><span data-stu-id="d2069-223">See also</span></span>

[<span data-ttu-id="d2069-224">Saiba mais sobre a integração Graph microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d2069-224">Learn more about Microsoft Graph and Teams integration</span></span>](/graph/teams-concept-overview)
