---
title: Usar o Microsoft Graph para importar mensagens de plataforma externa para o Teams
description: Descreve como usar o Microsoft Graph para importar mensagens de uma plataforma externa para o Teams
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: teams import messages api graph microsoft migrar migration post
ms.openlocfilehash: 8cf4f964aba7ce9375b1b259ae88a7fbcb620631
ms.sourcegitcommit: f6e4a303828224a702138753a8e5e27c8a094c82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51176953"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a><span data-ttu-id="cc350-104">Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="cc350-104">Import third-party platform messages to Teams using Microsoft Graph</span></span>

>[!IMPORTANT]
> <span data-ttu-id="cc350-105">As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários.</span><span class="sxs-lookup"><span data-stu-id="cc350-105">Microsoft Graph and Microsoft Teams public previews are available for early-access and feedback.</span></span> <span data-ttu-id="cc350-106">Embora essa versão tenha passado por testes abrangentes, ela não se destina a ser usada na produção.</span><span class="sxs-lookup"><span data-stu-id="cc350-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

<span data-ttu-id="cc350-107">Com o Microsoft Graph, você pode migrar o histórico de mensagens e os dados existentes dos usuários de um sistema externo para um canal do Teams.</span><span class="sxs-lookup"><span data-stu-id="cc350-107">With Microsoft Graph, you can migrate users' existing message history and data from an external system into a Teams channel.</span></span> <span data-ttu-id="cc350-108">Ao habilitar a recriação de uma hierarquia de mensagens de plataforma de terceiros dentro do Teams, os usuários podem continuar suas comunicações de maneira perfeita e continuar sem interrupção.</span><span class="sxs-lookup"><span data-stu-id="cc350-108">By enabling the recreation of a third-party platform messaging hierarchy inside Teams, users can continue their communications in a seamless manner and proceed without interruption.</span></span>

> [!NOTE] 
> <span data-ttu-id="cc350-109">No futuro, a Microsoft pode exigir que você ou seus clientes paguem taxas adicionais com base na quantidade de dados importados.</span><span class="sxs-lookup"><span data-stu-id="cc350-109">In the future, Microsoft may require you or your customers to pay additional fees based on the amount of data imported.</span></span>

## <a name="import-overview"></a><span data-ttu-id="cc350-110">Visão geral de importação</span><span class="sxs-lookup"><span data-stu-id="cc350-110">Import overview</span></span>

<span data-ttu-id="cc350-111">Em um nível alto, o processo de importação consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="cc350-111">At a high level, the import process consists of the following:</span></span>

1. [<span data-ttu-id="cc350-112">Criar uma equipe com um back-in-timestamp</span><span class="sxs-lookup"><span data-stu-id="cc350-112">Create a team with a back-in-time timestamp</span></span>](#step-one-create-a-team)
1. [<span data-ttu-id="cc350-113">Criar um canal com um back-in-timestamp</span><span class="sxs-lookup"><span data-stu-id="cc350-113">Create a channel with a back-in-time timestamp</span></span>](#step-two-create-a-channel)  
1. [<span data-ttu-id="cc350-114">Importar mensagens datadas de back-in-time externas</span><span class="sxs-lookup"><span data-stu-id="cc350-114">Import external back-in-time dated messages</span></span>](#step-three-import-messages)
1. [<span data-ttu-id="cc350-115">Concluir o processo de migração de equipe e canal</span><span class="sxs-lookup"><span data-stu-id="cc350-115">Complete the team and channel migration process</span></span>](#step-four-complete-migration-mode)
1. [<span data-ttu-id="cc350-116">Adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="cc350-116">Add team members</span></span>](#step-five-add-team-members)

## <a name="necessary-requirements"></a><span data-ttu-id="cc350-117">Requisitos necessários</span><span class="sxs-lookup"><span data-stu-id="cc350-117">Necessary requirements</span></span>

### <a name="analyze-and-prepare-message-data"></a><span data-ttu-id="cc350-118">Analisar e preparar dados de mensagens</span><span class="sxs-lookup"><span data-stu-id="cc350-118">Analyze and prepare message data</span></span>

<span data-ttu-id="cc350-119">✔ revise os dados de terceiros para decidir o que será migrado.</span><span class="sxs-lookup"><span data-stu-id="cc350-119">✔ Review the third-party data to decide what will be migrated.</span></span>  
<span data-ttu-id="cc350-120">✔ Extrair os dados selecionados do sistema de chat de terceiros.</span><span class="sxs-lookup"><span data-stu-id="cc350-120">✔ Extract the selected data from the third-party chat system.</span></span>  
<span data-ttu-id="cc350-121">✔ mapear a estrutura de chat de terceiros para a estrutura do Teams.</span><span class="sxs-lookup"><span data-stu-id="cc350-121">✔ Map the third-party chat structure to the Teams structure.</span></span>  
<span data-ttu-id="cc350-122">✔ Converter dados de importação no formato necessário para a migração.</span><span class="sxs-lookup"><span data-stu-id="cc350-122">✔ Convert import data into format needed for migration.</span></span>  

### <a name="set-up-your-office-365-tenant"></a><span data-ttu-id="cc350-123">Configurar seu locatário do Office 365</span><span class="sxs-lookup"><span data-stu-id="cc350-123">Set up your Office 365 tenant</span></span>

<span data-ttu-id="cc350-124">✔ certifique-se de que exista um locatário do Office 365 para os dados de importação.</span><span class="sxs-lookup"><span data-stu-id="cc350-124">✔ Ensure that an Office 365 tenant exists for the import data.</span></span> <span data-ttu-id="cc350-125">Para obter mais informações sobre como configurar uma locação do Office 365 para o *Teams,* consulte , Prepare [your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="cc350-125">For more information on setting up an Office 365 tenancy for Teams, *see*, [Prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>  
<span data-ttu-id="cc350-126">✔ Certifique-se de que os membros da equipe estão no Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="cc350-126">✔ Make sure that team members are in Azure Active Directory (AAD).</span></span>  <span data-ttu-id="cc350-127">Para obter mais *informações,* [consulte Adicionar um novo usuário](/azure/active-directory/fundamentals/add-users-azure-active-directory) ao Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="cc350-127">For more information *see* [Add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to Azure Active Directory.</span></span>

## <a name="step-one-create-a-team"></a><span data-ttu-id="cc350-128">Etapa Um: Criar uma equipe</span><span class="sxs-lookup"><span data-stu-id="cc350-128">Step One: Create a team</span></span>

<span data-ttu-id="cc350-129">Como os dados existentes estão sendo migrados, manter os datas de data/hora originais e impedir a atividade de mensagens durante o processo de migração são fundamentais para recriar o fluxo de mensagens existente do usuário no Teams.</span><span class="sxs-lookup"><span data-stu-id="cc350-129">Since existing data is being migrated, maintaining the original message timestamps and preventing messaging activity during the migration process are key to recreating the user's existing message flow in Teams.</span></span> <span data-ttu-id="cc350-130">Isso é alcançado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="cc350-130">This is achieved as follows:</span></span>

> <span data-ttu-id="cc350-131">[Crie uma nova equipe](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um back-in-timestamp usando a propriedade de recurso de  `createdDateTime`  equipe.</span><span class="sxs-lookup"><span data-stu-id="cc350-131">[Create a new team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the team resource  `createdDateTime`  property.</span></span> <span data-ttu-id="cc350-132">Coloque a nova equipe em , um estado especial que barra os usuários da maioria das atividades dentro da equipe até que o processo `migration mode` de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="cc350-132">Place the new team in `migration mode`, a special state that bars users from most activities within the team until the migration process is complete.</span></span> <span data-ttu-id="cc350-133">Inclua o atributo instance com o valor na solicitação POST para identificar explicitamente a `teamCreationMode` nova equipe como sendo criada para `migration` migração.</span><span class="sxs-lookup"><span data-stu-id="cc350-133">Include the `teamCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  

> <span data-ttu-id="cc350-134">**OBSERVAÇÃO**: o campo só será preenchido para `createdDateTime` instâncias de uma equipe ou canal que tenham sido migrados.</span><span class="sxs-lookup"><span data-stu-id="cc350-134">**NOTE**:  The `createdDateTime` field will only be populated for instances of a team or channel that have been migrated.</span></span>

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a><span data-ttu-id="cc350-135">Permissões</span><span class="sxs-lookup"><span data-stu-id="cc350-135">Permissions</span></span>

|<span data-ttu-id="cc350-136">ScopeName</span><span class="sxs-lookup"><span data-stu-id="cc350-136">ScopeName</span></span>|<span data-ttu-id="cc350-137">DisplayName</span><span class="sxs-lookup"><span data-stu-id="cc350-137">DisplayName</span></span>|<span data-ttu-id="cc350-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc350-138">Description</span></span>|<span data-ttu-id="cc350-139">Tipo</span><span class="sxs-lookup"><span data-stu-id="cc350-139">Type</span></span>|<span data-ttu-id="cc350-140">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="cc350-140">Admin Consent?</span></span>|<span data-ttu-id="cc350-141">Entidades/APIs cobertas</span><span class="sxs-lookup"><span data-stu-id="cc350-141">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="cc350-142">Gerenciar a migração do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="cc350-142">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="cc350-143">Criando, gerenciando recursos para migração para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="cc350-143">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="cc350-144">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="cc350-144">**Application-only**</span></span>|<span data-ttu-id="cc350-145">**Sim**</span><span class="sxs-lookup"><span data-stu-id="cc350-145">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a><span data-ttu-id="cc350-146">Solicitação (criar uma equipe no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="cc350-146">Request (create a team in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="cc350-147">Resposta</span><span class="sxs-lookup"><span data-stu-id="cc350-147">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{teamId}/operations/{operationId}
Content-Location: /teams/{teamId}
```

#### <a name="error-messages"></a><span data-ttu-id="cc350-148">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="cc350-148">Error messages</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="cc350-149">`createdDateTime`  definido para o futuro.</span><span class="sxs-lookup"><span data-stu-id="cc350-149">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="cc350-150">`createdDateTime`  corretamente especificado, mas o atributo `teamCreationMode`  instance está ausente ou definido como valor inválido.</span><span class="sxs-lookup"><span data-stu-id="cc350-150">`createdDateTime`  correctly specified, but `teamCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-two-create-a-channel"></a><span data-ttu-id="cc350-151">Etapa Dois: Criar um canal</span><span class="sxs-lookup"><span data-stu-id="cc350-151">Step Two: Create a channel</span></span>

<span data-ttu-id="cc350-152">A criação de um canal para as mensagens importadas é semelhante ao cenário de criação de equipe:</span><span class="sxs-lookup"><span data-stu-id="cc350-152">Creating a channel for the imported messages is similar to the create team scenario:</span></span>

> <span data-ttu-id="cc350-153">[Crie um novo canal](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) com um back-in-timestamp usando a propriedade de recurso `createdDateTime` channel.</span><span class="sxs-lookup"><span data-stu-id="cc350-153">[Create a new channel](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) with a back-in-time timestamp using the channel resource `createdDateTime` property.</span></span> <span data-ttu-id="cc350-154">Coloque o novo canal em , um estado especial que barra os usuários da maioria das atividades de chat dentro do canal até que o processo `migration mode` de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="cc350-154">Place the new channel in `migration mode`, a special state that bars users from most chat activities within the channel until the migration process is complete.</span></span>  <span data-ttu-id="cc350-155">Inclua o atributo instance com o valor na solicitação POST para identificar explicitamente a `channelCreationMode` nova equipe como sendo criada para `migration` migração.</span><span class="sxs-lookup"><span data-stu-id="cc350-155">Include the `channelCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a><span data-ttu-id="cc350-156">Permissões</span><span class="sxs-lookup"><span data-stu-id="cc350-156">Permissions</span></span>

|<span data-ttu-id="cc350-157">ScopeName</span><span class="sxs-lookup"><span data-stu-id="cc350-157">ScopeName</span></span>|<span data-ttu-id="cc350-158">DisplayName</span><span class="sxs-lookup"><span data-stu-id="cc350-158">DisplayName</span></span>|<span data-ttu-id="cc350-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc350-159">Description</span></span>|<span data-ttu-id="cc350-160">Tipo</span><span class="sxs-lookup"><span data-stu-id="cc350-160">Type</span></span>|<span data-ttu-id="cc350-161">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="cc350-161">Admin Consent?</span></span>|<span data-ttu-id="cc350-162">Entidades/APIs cobertas</span><span class="sxs-lookup"><span data-stu-id="cc350-162">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="cc350-163">Gerenciar a migração do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="cc350-163">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="cc350-164">Criando, gerenciando recursos para migração para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="cc350-164">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="cc350-165">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="cc350-165">**Application-only**</span></span>|<span data-ttu-id="cc350-166">**Sim**</span><span class="sxs-lookup"><span data-stu-id="cc350-166">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a><span data-ttu-id="cc350-167">Solicitação (criar um canal no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="cc350-167">Request (create a channel in migration state)</span></span>

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

#### <a name="response"></a><span data-ttu-id="cc350-168">Resposta</span><span class="sxs-lookup"><span data-stu-id="cc350-168">Response</span></span>

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

#### <a name="error-message"></a><span data-ttu-id="cc350-169">Mensagem de erro</span><span class="sxs-lookup"><span data-stu-id="cc350-169">Error message</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="cc350-170">`createdDateTime`  definido para o futuro.</span><span class="sxs-lookup"><span data-stu-id="cc350-170">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="cc350-171">`createdDateTime`  corretamente especificado, mas `channelCreationMode`  o atributo instance está ausente ou definido como valor inválido.</span><span class="sxs-lookup"><span data-stu-id="cc350-171">`createdDateTime`  correctly specified but `channelCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-three-import-messages"></a><span data-ttu-id="cc350-172">Etapa Três: Importar mensagens</span><span class="sxs-lookup"><span data-stu-id="cc350-172">Step Three: Import messages</span></span>

<span data-ttu-id="cc350-173">Depois que a equipe e o canal foram criados, você pode começar a enviar mensagens de back-in-time usando as chaves e `createdDateTime` `from`  no corpo da solicitação.</span><span class="sxs-lookup"><span data-stu-id="cc350-173">After the team and channel have been created, you can begin sending back-in-time messages using the `createdDateTime`  and `from`  keys in the request body.</span></span> <span data-ttu-id="cc350-174">**OBSERVAÇÃO:** não há suporte para mensagens `createdDateTime` importadas com o thread de `createdDateTime` mensagem anterior ao thread da mensagem.</span><span class="sxs-lookup"><span data-stu-id="cc350-174">**NOTE**: messages imported with `createdDateTime` earlier than the message thread `createdDateTime` is not supported.</span></span>

> [!NOTE]
> * <span data-ttu-id="cc350-175">`createdDateTime` deve ser exclusivo entre mensagens no mesmo thread.</span><span class="sxs-lookup"><span data-stu-id="cc350-175">`createdDateTime` must be unique across messages in the same thread.</span></span>
> * <span data-ttu-id="cc350-176">`createdDateTime` oferece suporte a data/hora com precisão de milissegundos.</span><span class="sxs-lookup"><span data-stu-id="cc350-176">`createdDateTime` supports timestamps with milliseconds precision.</span></span> <span data-ttu-id="cc350-177">Por exemplo, se a mensagem de solicitação de entrada tiver o valor definido como `createdDateTime` *2020-09-16T05:50:31.0025302Z*, ela será convertida em *2020-09-16T05:50:31.002Z* quando a mensagem for ingerida.</span><span class="sxs-lookup"><span data-stu-id="cc350-177">For example, if the incoming request message has the value of `createdDateTime` set as *2020-09-16T05:50:31.0025302Z*, then it would be converted to *2020-09-16T05:50:31.002Z* when the message is ingested.</span></span>

#### <a name="request-post-message-that-is-text-only"></a><span data-ttu-id="cc350-178">Solicitação (mensagem POST que é somente texto)</span><span class="sxs-lookup"><span data-stu-id="cc350-178">Request (POST message that is text-only)</span></span>

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

#### <a name="response"></a><span data-ttu-id="cc350-179">Resposta</span><span class="sxs-lookup"><span data-stu-id="cc350-179">Response</span></span>

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

#### <a name="error-messages"></a><span data-ttu-id="cc350-180">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="cc350-180">Error messages</span></span>

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a><span data-ttu-id="cc350-181">Solicitar (POSTAR uma mensagem com imagem em linha)</span><span class="sxs-lookup"><span data-stu-id="cc350-181">Request (POST a message with inline image)</span></span>

> <span data-ttu-id="cc350-182">**Observação**: não há escopos de permissão especiais neste cenário, pois a solicitação faz parte do chatMessage; os escopos para chatMessage também se aplicam aqui.</span><span class="sxs-lookup"><span data-stu-id="cc350-182">**Note**: There are no special permission scopes in this scenario since the request is part of chatMessage; scopes for chatMessage apply here as well.</span></span>

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

#### <a name="response"></a><span data-ttu-id="cc350-183">Resposta</span><span class="sxs-lookup"><span data-stu-id="cc350-183">Response</span></span>

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

## <a name="step-four-complete-migration-mode"></a><span data-ttu-id="cc350-184">Etapa quatro: concluir o modo de migração</span><span class="sxs-lookup"><span data-stu-id="cc350-184">Step Four: Complete migration mode</span></span>

<span data-ttu-id="cc350-185">Depois que o processo de migração de mensagens é concluído, a equipe e o canal são retirados do modo de migração usando o  `completeMigration`  método.</span><span class="sxs-lookup"><span data-stu-id="cc350-185">Once the message migration process has completed, both the team and channel are taken out of migration mode using the  `completeMigration`  method.</span></span> <span data-ttu-id="cc350-186">Esta etapa abre os recursos de equipe e canal para uso geral pelos membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="cc350-186">This step opens the team and channel resources for general use by team members.</span></span> <span data-ttu-id="cc350-187">A ação está vinculada à `team` instância.</span><span class="sxs-lookup"><span data-stu-id="cc350-187">The action is bound to the `team` instance.</span></span>

#### <a name="request-end-team-migration-mode"></a><span data-ttu-id="cc350-188">Solicitação (modo de migração de equipe final)</span><span class="sxs-lookup"><span data-stu-id="cc350-188">Request (end team migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="cc350-189">Resposta</span><span class="sxs-lookup"><span data-stu-id="cc350-189">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-channel-migration-mode"></a><span data-ttu-id="cc350-190">Solicitação (modo de migração de canal final)</span><span class="sxs-lookup"><span data-stu-id="cc350-190">Request (end channel migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="cc350-191">Resposta</span><span class="sxs-lookup"><span data-stu-id="cc350-191">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="error-response"></a><span data-ttu-id="cc350-192">Resposta de erro</span><span class="sxs-lookup"><span data-stu-id="cc350-192">Error response</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="cc350-193">Ação chamada em um `team` ou que não está em `channel` `migrationMode` .</span><span class="sxs-lookup"><span data-stu-id="cc350-193">Action called on a `team` or `channel` that is not in `migrationMode`.</span></span>

## <a name="step-five-add-team-members"></a><span data-ttu-id="cc350-194">Etapa Cinco: Adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="cc350-194">Step Five: Add team members</span></span>

<span data-ttu-id="cc350-195">Você pode adicionar um membro a uma equipe usando a [interface do usuário](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) do Teams ou a API de membro do Microsoft Graph [Add:](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="cc350-195">You can add a member to a team [using the Teams UI](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) or Microsoft Graph [Add member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) API:</span></span>

#### <a name="request-add-member"></a><span data-ttu-id="cc350-196">Solicitação (adicionar membro)</span><span class="sxs-lookup"><span data-stu-id="cc350-196">Request (add member)</span></span>

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

#### <a name="response"></a><span data-ttu-id="cc350-197">Resposta</span><span class="sxs-lookup"><span data-stu-id="cc350-197">Response</span></span>

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a><span data-ttu-id="cc350-198">Dicas e informações adicionais</span><span class="sxs-lookup"><span data-stu-id="cc350-198">Tips and additional information</span></span>

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* <span data-ttu-id="cc350-199">Você pode importar mensagens de usuários que não estão no Teams.</span><span class="sxs-lookup"><span data-stu-id="cc350-199">You can import messages from users who are not in Teams.</span></span> <span data-ttu-id="cc350-200">**OBSERVAÇÃO**: As mensagens importadas para usuários que não estão presentes no locatário não serão pesquisáveis nos portais de conformidade ou cliente do Teams durante a Visualização Pública.</span><span class="sxs-lookup"><span data-stu-id="cc350-200">**NOTE**: Messages imported for users not present in the tenant will not be searchable in the Teams client or compliance portals during Public Preview.</span></span>

* <span data-ttu-id="cc350-201">Depois que `completeMigration` a solicitação for feita, você não poderá importar mais mensagens para a equipe.</span><span class="sxs-lookup"><span data-stu-id="cc350-201">Once the `completeMigration` request is made, you cannot import further messages into the team.</span></span>

* <span data-ttu-id="cc350-202">Os membros da equipe só podem ser adicionados à nova equipe após a solicitação `completeMigration` ter retornado uma resposta bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="cc350-202">Team members can only be added to the new team after the `completeMigration` request has returned a successful response.</span></span>

* <span data-ttu-id="cc350-203">Throttling: As mensagens são importadas em 5 RPS por canal.</span><span class="sxs-lookup"><span data-stu-id="cc350-203">Throttling: Messages import at 5 RPS per channel.</span></span>

* <span data-ttu-id="cc350-204">Se você precisar fazer uma correção nos resultados da migração, será necessário excluir a equipe e repetir as etapas para criar a equipe e o canal e migrar as mensagens.</span><span class="sxs-lookup"><span data-stu-id="cc350-204">If you need to make a correction to the migration results, you need to delete the team and repeat the steps to create the team and channel and re-migrate the messages.</span></span>

> [!NOTE]
> <span data-ttu-id="cc350-205">Atualmente, as imagens em linha são o único tipo de mídia com suporte pelo esquema de API de mensagem de importação.</span><span class="sxs-lookup"><span data-stu-id="cc350-205">Currently, inline images are the only type of media supported by the import message API schema.</span></span>

##### <a name="import-content-scope"></a><span data-ttu-id="cc350-206">Importar escopo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="cc350-206">Import content scope</span></span>

|<span data-ttu-id="cc350-207">No escopo</span><span class="sxs-lookup"><span data-stu-id="cc350-207">In-scope</span></span> | <span data-ttu-id="cc350-208">Atualmente fora do escopo</span><span class="sxs-lookup"><span data-stu-id="cc350-208">Currently out-of-scope</span></span>|
|----------|--------------------------|
|<span data-ttu-id="cc350-209">Mensagens de equipe e canal</span><span class="sxs-lookup"><span data-stu-id="cc350-209">Team and channel messages</span></span>|<span data-ttu-id="cc350-210">1:1 e mensagens de chat de grupo</span><span class="sxs-lookup"><span data-stu-id="cc350-210">1:1 and group chat messages</span></span>|
|<span data-ttu-id="cc350-211">Hora de criação da mensagem original</span><span class="sxs-lookup"><span data-stu-id="cc350-211">Created time of the original message</span></span>|<span data-ttu-id="cc350-212">Canais privados</span><span class="sxs-lookup"><span data-stu-id="cc350-212">Private channels</span></span>|
|<span data-ttu-id="cc350-213">Imagens em linha como parte da mensagem</span><span class="sxs-lookup"><span data-stu-id="cc350-213">Inline images as part of the message</span></span>|<span data-ttu-id="cc350-214">At mentions</span><span class="sxs-lookup"><span data-stu-id="cc350-214">At mentions</span></span>|
|<span data-ttu-id="cc350-215">Links para arquivos existentes no SPO/OneDrive</span><span class="sxs-lookup"><span data-stu-id="cc350-215">Links to existing files in SPO/OneDrive</span></span>|<span data-ttu-id="cc350-216">Reações</span><span class="sxs-lookup"><span data-stu-id="cc350-216">Reactions</span></span>|
|<span data-ttu-id="cc350-217">Mensagens com texto rico</span><span class="sxs-lookup"><span data-stu-id="cc350-217">Messages with rich text</span></span>|<span data-ttu-id="cc350-218">Vídeos</span><span class="sxs-lookup"><span data-stu-id="cc350-218">Videos</span></span>|
|<span data-ttu-id="cc350-219">Cadeia de resposta de mensagens</span><span class="sxs-lookup"><span data-stu-id="cc350-219">Message reply chain</span></span>|<span data-ttu-id="cc350-220">Announcements</span><span class="sxs-lookup"><span data-stu-id="cc350-220">Announcements</span></span>|
|<span data-ttu-id="cc350-221">Processamento de alta taxa de transferência</span><span class="sxs-lookup"><span data-stu-id="cc350-221">High throughput processing</span></span>|<span data-ttu-id="cc350-222">Trechos de código</span><span class="sxs-lookup"><span data-stu-id="cc350-222">Code snippets</span></span>|
||<span data-ttu-id="cc350-223">Cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="cc350-223">Adaptive cards</span></span>|
||<span data-ttu-id="cc350-224">Adesivos</span><span class="sxs-lookup"><span data-stu-id="cc350-224">Stickers</span></span>|
||<span data-ttu-id="cc350-225">Emojis</span><span class="sxs-lookup"><span data-stu-id="cc350-225">Emojis</span></span>|
||<span data-ttu-id="cc350-226">Aspas</span><span class="sxs-lookup"><span data-stu-id="cc350-226">Quotes</span></span>|
||<span data-ttu-id="cc350-227">Postagens entre canais</span><span class="sxs-lookup"><span data-stu-id="cc350-227">Cross posts between channels</span></span>|


## <a name="see-also"></a><span data-ttu-id="cc350-228">Confira também</span><span class="sxs-lookup"><span data-stu-id="cc350-228">See also</span></span>
> [!div class="nextstepaction"]
>[<span data-ttu-id="cc350-229">Saiba mais sobre a integração do Microsoft Graph e do Teams</span><span class="sxs-lookup"><span data-stu-id="cc350-229">Learn more about Microsoft Graph and Teams integration</span></span>](/graph/teams-concept-overview)
