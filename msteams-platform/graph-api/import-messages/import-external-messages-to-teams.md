---
title: Use o Microsoft Graph para importar mensagens de plataforma externa para Teams
description: Descreve como usar o Microsoft Graph para importar mensagens de uma plataforma externa para Teams
localization_priority: Normal
author: akjo
ms.author: lajanuar
ms.topic: Overview
keywords: teams import messages api graph microsoft migrar migration post
ms.openlocfilehash: 95cbf6bf2deac4ea71e60fe0fece06c1dd3ad24c
ms.sourcegitcommit: 656a1de9e23e0ad90dddcb93a2bbfcc63848a856
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53130091"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a><span data-ttu-id="043c0-104">Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="043c0-104">Import third-party platform messages to Teams using Microsoft Graph</span></span>

<span data-ttu-id="043c0-105">Com o Microsoft Graph, você pode migrar o histórico de mensagens e os dados existentes dos usuários de um sistema externo para um canal Teams.</span><span class="sxs-lookup"><span data-stu-id="043c0-105">With Microsoft Graph, you can migrate users' existing message history and data from an external system into a Teams channel.</span></span> <span data-ttu-id="043c0-106">Ao habilitar a recriação de uma hierarquia de mensagens de plataforma de terceiros dentro Teams, os usuários podem continuar suas comunicações de maneira perfeita e continuar sem interrupção.</span><span class="sxs-lookup"><span data-stu-id="043c0-106">By enabling the recreation of a third-party platform messaging hierarchy inside Teams, users can continue their communications in a seamless manner and proceed without interruption.</span></span>

> [!NOTE]
> <span data-ttu-id="043c0-107">No futuro, a Microsoft pode exigir que você ou seus clientes paguem taxas adicionais com base na quantidade de dados importados.</span><span class="sxs-lookup"><span data-stu-id="043c0-107">In the future, Microsoft may require you or your customers to pay additional fees based on the amount of data imported.</span></span>

## <a name="import-overview"></a><span data-ttu-id="043c0-108">Visão geral de importação</span><span class="sxs-lookup"><span data-stu-id="043c0-108">Import overview</span></span>

<span data-ttu-id="043c0-109">Em um nível alto, o processo de importação consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="043c0-109">At a high level, the import process consists of the following:</span></span>

1. <span data-ttu-id="043c0-110">[Crie uma equipe com um back-in-timestamp](#step-1-create-a-team).</span><span class="sxs-lookup"><span data-stu-id="043c0-110">[Create a team with a back-in-time timestamp](#step-1-create-a-team).</span></span>
1. <span data-ttu-id="043c0-111">[Crie um canal com um back-in-timestamp](#step-2-create-a-channel).</span><span class="sxs-lookup"><span data-stu-id="043c0-111">[Create a channel with a back-in-time timestamp](#step-2-create-a-channel).</span></span>
1. <span data-ttu-id="043c0-112">[Importar mensagens de back-in-time externas datadas](#step-3-import-messages).</span><span class="sxs-lookup"><span data-stu-id="043c0-112">[Import external back-in-time dated messages](#step-3-import-messages).</span></span>
1. <span data-ttu-id="043c0-113">[Conclua o processo de migração de equipe e canal.](#step-4-complete-migration-mode)</span><span class="sxs-lookup"><span data-stu-id="043c0-113">[Complete the team and channel migration process](#step-4-complete-migration-mode).</span></span>
1. <span data-ttu-id="043c0-114">[Adicionar membros da equipe](#step-five-add-team-members).</span><span class="sxs-lookup"><span data-stu-id="043c0-114">[Add team members](#step-five-add-team-members).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="043c0-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="043c0-115">Prerequisites</span></span>

### <a name="analyze-and-prepare-message-data"></a><span data-ttu-id="043c0-116">Analisar e preparar dados de mensagens</span><span class="sxs-lookup"><span data-stu-id="043c0-116">Analyze and prepare message data</span></span>

* <span data-ttu-id="043c0-117">Revise os dados de terceiros para decidir o que será migrado.</span><span class="sxs-lookup"><span data-stu-id="043c0-117">Review the third-party data to decide what will be migrated.</span></span>  
* <span data-ttu-id="043c0-118">Extraia os dados selecionados do sistema de chat de terceiros.</span><span class="sxs-lookup"><span data-stu-id="043c0-118">Extract the selected data from the third-party chat system.</span></span>  
* <span data-ttu-id="043c0-119">Mapeie a estrutura de chat de terceiros para a estrutura Teams de terceiros.</span><span class="sxs-lookup"><span data-stu-id="043c0-119">Map the third-party chat structure to the Teams structure.</span></span>  
* <span data-ttu-id="043c0-120">Converta os dados de importação no formato necessário para a migração.</span><span class="sxs-lookup"><span data-stu-id="043c0-120">Convert import data into format needed for migration.</span></span>  

### <a name="set-up-your-office-365-tenant"></a><span data-ttu-id="043c0-121">Configurar seu locatário do Office 365</span><span class="sxs-lookup"><span data-stu-id="043c0-121">Set up your Office 365 tenant</span></span>

* <span data-ttu-id="043c0-122">Verifique se existe Office 365 locatário para os dados de importação.</span><span class="sxs-lookup"><span data-stu-id="043c0-122">Ensure that an Office 365 tenant exists for the import data.</span></span> <span data-ttu-id="043c0-123">Para obter mais informações sobre como configurar Office 365 locatário para Teams, consulte [prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="043c0-123">For more information on setting up an Office 365 tenancy for Teams, see [prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>
* <span data-ttu-id="043c0-124">Certifique-se de que os membros da equipe estão Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="043c0-124">Make sure that team members are in Azure Active Directory (AAD).</span></span> <span data-ttu-id="043c0-125">Para obter mais informações, [consulte adicionar um novo usuário](/azure/active-directory/fundamentals/add-users-azure-active-directory) ao AAD.</span><span class="sxs-lookup"><span data-stu-id="043c0-125">For more information, see [add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to AAD.</span></span>

## <a name="step-1-create-a-team"></a><span data-ttu-id="043c0-126">Etapa 1: Criar uma equipe</span><span class="sxs-lookup"><span data-stu-id="043c0-126">Step 1: Create a team</span></span>

<span data-ttu-id="043c0-127">Como você está migrando dados existentes, manter os datas de data/hora originais da mensagem e impedir a atividade de mensagens durante o processo de migração são fundamentais para recriar o fluxo de mensagens existente do usuário no Teams.</span><span class="sxs-lookup"><span data-stu-id="043c0-127">Since you are migrating existing data, maintaining the original message timestamps and preventing messaging activity during the migration process are key to recreating the user's existing message flow in Teams.</span></span> <span data-ttu-id="043c0-128">Isso é alcançado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="043c0-128">This is achieved as follows:</span></span>

> <span data-ttu-id="043c0-129">[Crie uma nova equipe](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um back-in-timestamp usando a propriedade de recurso de `createdDateTime` equipe.</span><span class="sxs-lookup"><span data-stu-id="043c0-129">[Create a new team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the team resource `createdDateTime` property.</span></span> <span data-ttu-id="043c0-130">Coloque a nova equipe em , um estado especial que restringe os usuários da maioria das atividades dentro da equipe até que o processo `migration mode` de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="043c0-130">Place the new team in `migration mode`, a special state that restricts users from most activities within the team until the migration process is complete.</span></span> <span data-ttu-id="043c0-131">Inclua o atributo instance com o valor na solicitação POST para identificar explicitamente a `teamCreationMode` nova equipe como sendo criada para `migration` migração.</span><span class="sxs-lookup"><span data-stu-id="043c0-131">Include the `teamCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  

> [!NOTE]
> <span data-ttu-id="043c0-132">O `createdDateTime` campo só será preenchido para instâncias de uma equipe ou canal que foram migradas.</span><span class="sxs-lookup"><span data-stu-id="043c0-132">The `createdDateTime` field will only be populated for instances of a team or channel that have been migrated.</span></span>

<!-- markdownlint-disable MD001 -->

#### <a name="permission"></a><span data-ttu-id="043c0-133">Permissão</span><span class="sxs-lookup"><span data-stu-id="043c0-133">Permission</span></span>

|<span data-ttu-id="043c0-134">ScopeName</span><span class="sxs-lookup"><span data-stu-id="043c0-134">ScopeName</span></span>|<span data-ttu-id="043c0-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="043c0-135">DisplayName</span></span>|<span data-ttu-id="043c0-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="043c0-136">Description</span></span>|<span data-ttu-id="043c0-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="043c0-137">Type</span></span>|<span data-ttu-id="043c0-138">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="043c0-138">Admin Consent?</span></span>|<span data-ttu-id="043c0-139">Entidades/APIs cobertas</span><span class="sxs-lookup"><span data-stu-id="043c0-139">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="043c0-140">Gerenciar a migração do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="043c0-140">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="043c0-141">Criando e gerenciando recursos para migração para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="043c0-141">Creating and managing resources for migration to Microsoft Teams.</span></span>|<span data-ttu-id="043c0-142">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="043c0-142">**Application-only**</span></span>|<span data-ttu-id="043c0-143">**Sim**</span><span class="sxs-lookup"><span data-stu-id="043c0-143">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a><span data-ttu-id="043c0-144">Solicitação (criar uma equipe no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="043c0-144">Request (create a team in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="043c0-145">Resposta</span><span class="sxs-lookup"><span data-stu-id="043c0-145">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{team-id}/operations/{operation-id}
Content-Location: /teams/{team-id}
```

#### <a name="error-message"></a><span data-ttu-id="043c0-146">Mensagem de erro</span><span class="sxs-lookup"><span data-stu-id="043c0-146">Error message</span></span>

```http
400 Bad Request
```

<span data-ttu-id="043c0-147">Você pode receber a mensagem de erro nos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="043c0-147">You can receive the error message in the following scenarios:</span></span>

* <span data-ttu-id="043c0-148">Se `createdDateTime` estiver definido para o futuro.</span><span class="sxs-lookup"><span data-stu-id="043c0-148">If `createdDateTime` is set for future.</span></span>
* <span data-ttu-id="043c0-149">Se `createdDateTime` for especificado corretamente, mas o atributo instance estiver ausente ou definido como valor `teamCreationMode` inválido.</span><span class="sxs-lookup"><span data-stu-id="043c0-149">If `createdDateTime` is correctly specified, but `teamCreationMode` instance attribute is missing or set to invalid value.</span></span>

## <a name="step-2-create-a-channel"></a><span data-ttu-id="043c0-150">Etapa 2: Criar um canal</span><span class="sxs-lookup"><span data-stu-id="043c0-150">Step 2: Create a channel</span></span>

<span data-ttu-id="043c0-151">A criação de um canal para as mensagens importadas é semelhante ao cenário de criação de equipe:</span><span class="sxs-lookup"><span data-stu-id="043c0-151">Creating a channel for the imported messages is similar to the create team scenario:</span></span>

> <span data-ttu-id="043c0-152">[Crie um novo canal](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) com um back-in-timestamp usando a propriedade de recurso `createdDateTime` channel.</span><span class="sxs-lookup"><span data-stu-id="043c0-152">[Create a new channel](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) with a back-in-time timestamp using the channel resource `createdDateTime` property.</span></span> <span data-ttu-id="043c0-153">Coloque o novo canal em , um estado especial que restringe os usuários da maioria das atividades de chat dentro do canal até que o processo `migration mode` de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="043c0-153">Place the new channel in `migration mode`, a special state that restricts users from most chat activities within the channel until the migration process is complete.</span></span> <span data-ttu-id="043c0-154">Inclua o atributo instance com o valor na solicitação POST para identificar explicitamente a `channelCreationMode` nova equipe como sendo criada para `migration` migração.</span><span class="sxs-lookup"><span data-stu-id="043c0-154">Include the `channelCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  
<!-- markdownlint-disable MD024 -->
#### <a name="permission"></a><span data-ttu-id="043c0-155">Permissão</span><span class="sxs-lookup"><span data-stu-id="043c0-155">Permission</span></span>

|<span data-ttu-id="043c0-156">ScopeName</span><span class="sxs-lookup"><span data-stu-id="043c0-156">ScopeName</span></span>|<span data-ttu-id="043c0-157">DisplayName</span><span class="sxs-lookup"><span data-stu-id="043c0-157">DisplayName</span></span>|<span data-ttu-id="043c0-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="043c0-158">Description</span></span>|<span data-ttu-id="043c0-159">Tipo</span><span class="sxs-lookup"><span data-stu-id="043c0-159">Type</span></span>|<span data-ttu-id="043c0-160">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="043c0-160">Admin Consent?</span></span>|<span data-ttu-id="043c0-161">Entidades/APIs cobertas</span><span class="sxs-lookup"><span data-stu-id="043c0-161">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="043c0-162">Gerenciar a migração do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="043c0-162">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="043c0-163">Criando e gerenciando recursos para migração para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="043c0-163">Creating and managing resources for migration to Microsoft Teams.</span></span>|<span data-ttu-id="043c0-164">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="043c0-164">**Application-only**</span></span>|<span data-ttu-id="043c0-165">**Sim**</span><span class="sxs-lookup"><span data-stu-id="043c0-165">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a><span data-ttu-id="043c0-166">Solicitação (criar um canal no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="043c0-166">Request (create a channel in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="043c0-167">Resposta</span><span class="sxs-lookup"><span data-stu-id="043c0-167">Response</span></span>

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

#### <a name="error-message"></a><span data-ttu-id="043c0-168">Mensagem de erro</span><span class="sxs-lookup"><span data-stu-id="043c0-168">Error message</span></span>

```http
400 Bad Request
```
<span data-ttu-id="043c0-169">Você pode receber a mensagem de erro nos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="043c0-169">You can receive the error message in the following scenarios:</span></span>

* <span data-ttu-id="043c0-170">Se `createdDateTime` estiver definido para o futuro.</span><span class="sxs-lookup"><span data-stu-id="043c0-170">If `createdDateTime` is set for future.</span></span>
* <span data-ttu-id="043c0-171">Se `createdDateTime` for especificado corretamente, mas o `channelCreationMode` atributo instance estiver ausente ou definido como valor inválido.</span><span class="sxs-lookup"><span data-stu-id="043c0-171">If `createdDateTime` is correctly specified but `channelCreationMode` instance attribute is missing or set to invalid value.</span></span>

## <a name="step-3-import-messages"></a><span data-ttu-id="043c0-172">Etapa 3: Importar mensagens</span><span class="sxs-lookup"><span data-stu-id="043c0-172">Step 3: Import messages</span></span>

<span data-ttu-id="043c0-173">Depois que a equipe e o canal foram criados, você pode começar a enviar mensagens de back-in-time usando as chaves e `createdDateTime` `from` no corpo da solicitação.</span><span class="sxs-lookup"><span data-stu-id="043c0-173">After the team and channel have been created, you can begin sending back-in-time messages using the `createdDateTime`  and `from` keys in the request body.</span></span>

> [!NOTE]
> * <span data-ttu-id="043c0-174">Não há suporte para mensagens `createdDateTime` importadas com o thread da `createdDateTime` mensagem.</span><span class="sxs-lookup"><span data-stu-id="043c0-174">Messages imported with `createdDateTime` earlier than the message thread `createdDateTime` is not supported.</span></span>
> * <span data-ttu-id="043c0-175">`createdDateTime` deve ser exclusivo entre mensagens no mesmo thread.</span><span class="sxs-lookup"><span data-stu-id="043c0-175">`createdDateTime` must be unique across messages in the same thread.</span></span>
> * <span data-ttu-id="043c0-176">`createdDateTime` oferece suporte a data/hora com precisão de milissegundos.</span><span class="sxs-lookup"><span data-stu-id="043c0-176">`createdDateTime` supports timestamps with milliseconds precision.</span></span> <span data-ttu-id="043c0-177">Por exemplo, se a mensagem de solicitação de entrada tiver o valor definido como `createdDateTime` *2020-09-16T05:50:31.0025302Z*, ela será convertida em *2020-09-16T05:50:31.002Z* quando a mensagem for ingerida.</span><span class="sxs-lookup"><span data-stu-id="043c0-177">For example, if the incoming request message has the value of `createdDateTime` set as *2020-09-16T05:50:31.0025302Z*, then it would be converted to *2020-09-16T05:50:31.002Z* when the message is ingested.</span></span>

#### <a name="request-post-message-that-is-text-only"></a><span data-ttu-id="043c0-178">Solicitação (mensagem POST que é somente texto)</span><span class="sxs-lookup"><span data-stu-id="043c0-178">Request (POST message that is text-only)</span></span>

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

#### <a name="response"></a><span data-ttu-id="043c0-179">Resposta</span><span class="sxs-lookup"><span data-stu-id="043c0-179">Response</span></span>

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

#### <a name="error-message"></a><span data-ttu-id="043c0-180">Mensagem de erro</span><span class="sxs-lookup"><span data-stu-id="043c0-180">Error message</span></span>

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a><span data-ttu-id="043c0-181">Solicitar (POSTAR uma mensagem com imagem em linha)</span><span class="sxs-lookup"><span data-stu-id="043c0-181">Request (POST a message with inline image)</span></span>

> [!NOTE]
> * <span data-ttu-id="043c0-182">Não há escopos de permissão especiais nesse cenário, pois a solicitação faz parte de `chatMessage` .</span><span class="sxs-lookup"><span data-stu-id="043c0-182">There are no special permission scopes in this scenario since the request is part of `chatMessage`.</span></span>
> * <span data-ttu-id="043c0-183">Os escopos para `chatMessage` aplicar aqui.</span><span class="sxs-lookup"><span data-stu-id="043c0-183">The scopes for `chatMessage` apply here.</span></span>

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

#### <a name="response"></a><span data-ttu-id="043c0-184">Resposta</span><span class="sxs-lookup"><span data-stu-id="043c0-184">Response</span></span>

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

## <a name="step-4-complete-migration-mode"></a><span data-ttu-id="043c0-185">Etapa 4: Concluir o modo de migração</span><span class="sxs-lookup"><span data-stu-id="043c0-185">Step 4: Complete migration mode</span></span>

<span data-ttu-id="043c0-186">Após a conclusão do processo de migração de mensagens, a equipe e o canal são retirados do modo de migração usando o  `completeMigration` método.</span><span class="sxs-lookup"><span data-stu-id="043c0-186">After the message migration process has completed, both the team and channel are taken out of migration mode using the  `completeMigration` method.</span></span> <span data-ttu-id="043c0-187">Esta etapa abre os recursos de equipe e canal para uso geral pelos membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="043c0-187">This step opens the team and channel resources for general use by team members.</span></span> <span data-ttu-id="043c0-188">A ação está vinculada à `team` instância.</span><span class="sxs-lookup"><span data-stu-id="043c0-188">The action is bound to the `team` instance.</span></span> <span data-ttu-id="043c0-189">Antes da conclusão da equipe, todos os canais devem ser concluídos fora do modo de migração.</span><span class="sxs-lookup"><span data-stu-id="043c0-189">Before the team completes, all channels must be completed out of migration mode.</span></span>

#### <a name="request-end-channel-migration-mode"></a><span data-ttu-id="043c0-190">Solicitação (modo de migração de canal final)</span><span class="sxs-lookup"><span data-stu-id="043c0-190">Request (end channel migration mode)</span></span>

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/completeMigration

```

#### <a name="response"></a><span data-ttu-id="043c0-191">Resposta</span><span class="sxs-lookup"><span data-stu-id="043c0-191">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-team-migration-mode"></a><span data-ttu-id="043c0-192">Solicitação (modo de migração de equipe final)</span><span class="sxs-lookup"><span data-stu-id="043c0-192">Request (end team migration mode)</span></span>

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/completeMigration
```

#### <a name="response"></a><span data-ttu-id="043c0-193">Resposta</span><span class="sxs-lookup"><span data-stu-id="043c0-193">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

<span data-ttu-id="043c0-194">Ação chamada em um `team` ou que não está em `channel` `migrationMode` .</span><span class="sxs-lookup"><span data-stu-id="043c0-194">Action called on a `team` or `channel` that is not in `migrationMode`.</span></span>

## <a name="step-five-add-team-members"></a><span data-ttu-id="043c0-195">Etapa cinco: Adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="043c0-195">Step five: Add team members</span></span>

<span data-ttu-id="043c0-196">Você pode adicionar um membro a uma equipe usando a interface [do usuário Teams ou](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) o Microsoft Graph adicionar API de [membro:](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="043c0-196">You can add a member to a team [using the Teams UI](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) or Microsoft Graph [add member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:</span></span>

#### <a name="request-add-member"></a><span data-ttu-id="043c0-197">Solicitação (adicionar membro)</span><span class="sxs-lookup"><span data-stu-id="043c0-197">Request (add member)</span></span>

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

#### <a name="response"></a><span data-ttu-id="043c0-198">Resposta</span><span class="sxs-lookup"><span data-stu-id="043c0-198">Response</span></span>

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a><span data-ttu-id="043c0-199">Dicas informações adicionais</span><span class="sxs-lookup"><span data-stu-id="043c0-199">Tips and additional information</span></span>

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* <span data-ttu-id="043c0-200">Depois que `completeMigration` a solicitação for feita, você não poderá importar mais mensagens para a equipe.</span><span class="sxs-lookup"><span data-stu-id="043c0-200">After the `completeMigration` request is made, you cannot import further messages into the team.</span></span>

* <span data-ttu-id="043c0-201">Você só pode adicionar membros da equipe à nova equipe após a solicitação `completeMigration` ter retornado uma resposta bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="043c0-201">You can only add team members to the new team after the `completeMigration` request has returned a successful response.</span></span>

* <span data-ttu-id="043c0-202">Throttling: As mensagens são importadas em cinco RPS por canal.</span><span class="sxs-lookup"><span data-stu-id="043c0-202">Throttling: Messages import at five RPS per channel.</span></span>

* <span data-ttu-id="043c0-203">Se precisar fazer uma correção nos resultados da migração, exclua a equipe e repita as etapas para criar a equipe e o canal e migrar as mensagens.</span><span class="sxs-lookup"><span data-stu-id="043c0-203">If you need to make a correction to the migration results, you must delete the team and repeat the steps to create the team and channel and re-migrate the messages.</span></span>

> [!NOTE]
> <span data-ttu-id="043c0-204">Atualmente, as imagens em linha são o único tipo de mídia com suporte pelo esquema de API de mensagem de importação.</span><span class="sxs-lookup"><span data-stu-id="043c0-204">Currently, inline images are the only type of media supported by the import message API schema.</span></span>

##### <a name="import-content-scope"></a><span data-ttu-id="043c0-205">Importar escopo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="043c0-205">Import content scope</span></span>

<span data-ttu-id="043c0-206">A tabela a seguir fornece o escopo de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="043c0-206">The following table provides the content scope:</span></span>

|<span data-ttu-id="043c0-207">No escopo</span><span class="sxs-lookup"><span data-stu-id="043c0-207">In-scope</span></span> | <span data-ttu-id="043c0-208">Atualmente fora do escopo</span><span class="sxs-lookup"><span data-stu-id="043c0-208">Currently out-of-scope</span></span>|
|----------|--------------------------|
|<span data-ttu-id="043c0-209">Mensagens de equipe e canal</span><span class="sxs-lookup"><span data-stu-id="043c0-209">Team and channel messages</span></span>|<span data-ttu-id="043c0-210">1:1 e mensagens de chat de grupo</span><span class="sxs-lookup"><span data-stu-id="043c0-210">1:1 and group chat messages</span></span>|
|<span data-ttu-id="043c0-211">Hora de criação da mensagem original</span><span class="sxs-lookup"><span data-stu-id="043c0-211">Created time of the original message</span></span>|<span data-ttu-id="043c0-212">Canais privados</span><span class="sxs-lookup"><span data-stu-id="043c0-212">Private channels</span></span>|
|<span data-ttu-id="043c0-213">Imagens em linha como parte da mensagem</span><span class="sxs-lookup"><span data-stu-id="043c0-213">Inline images as part of the message</span></span>|<span data-ttu-id="043c0-214">At mentions</span><span class="sxs-lookup"><span data-stu-id="043c0-214">At mentions</span></span>|
|<span data-ttu-id="043c0-215">Links para arquivos existentes no SPO ou OneDrive</span><span class="sxs-lookup"><span data-stu-id="043c0-215">Links to existing files in SPO or OneDrive</span></span>|<span data-ttu-id="043c0-216">Reações</span><span class="sxs-lookup"><span data-stu-id="043c0-216">Reactions</span></span>|
|<span data-ttu-id="043c0-217">Mensagens com texto rico</span><span class="sxs-lookup"><span data-stu-id="043c0-217">Messages with rich text</span></span>|<span data-ttu-id="043c0-218">Vídeos</span><span class="sxs-lookup"><span data-stu-id="043c0-218">Videos</span></span>|
|<span data-ttu-id="043c0-219">Cadeia de resposta de mensagens</span><span class="sxs-lookup"><span data-stu-id="043c0-219">Message reply chain</span></span>|<span data-ttu-id="043c0-220">Announcements</span><span class="sxs-lookup"><span data-stu-id="043c0-220">Announcements</span></span>|
|<span data-ttu-id="043c0-221">Processamento de alta taxa de transferência</span><span class="sxs-lookup"><span data-stu-id="043c0-221">High throughput processing</span></span>|<span data-ttu-id="043c0-222">Trechos de código</span><span class="sxs-lookup"><span data-stu-id="043c0-222">Code snippets</span></span>|
||<span data-ttu-id="043c0-223">Adesivos</span><span class="sxs-lookup"><span data-stu-id="043c0-223">Stickers</span></span>|
||<span data-ttu-id="043c0-224">Emojis</span><span class="sxs-lookup"><span data-stu-id="043c0-224">Emojis</span></span>|
||<span data-ttu-id="043c0-225">Cotações</span><span class="sxs-lookup"><span data-stu-id="043c0-225">Quotes</span></span>|
||<span data-ttu-id="043c0-226">Postagens entre canais</span><span class="sxs-lookup"><span data-stu-id="043c0-226">Cross posts between channels</span></span>|


## <a name="see-also"></a><span data-ttu-id="043c0-227">Também consulte</span><span class="sxs-lookup"><span data-stu-id="043c0-227">See also</span></span>

[<span data-ttu-id="043c0-228">Integração Graph microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="043c0-228">Microsoft Graph and Teams integration</span></span>](/graph/teams-concept-overview)
