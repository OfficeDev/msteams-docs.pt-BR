---
title: Usar o Microsoft Graph para importar mensagens de plataforma externa para o Microsoft Teams
description: Descreve como usar o Microsoft Graph para importar mensagens de uma plataforma externa para o Microsoft Teams
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: margens de atraso de equipes importar mensagens gráfico de API Microsoft migrar postagem migração
ms.openlocfilehash: 8e8b21c9a38570d7ede745e27b9316b7aba29956
ms.sourcegitcommit: 9fd61042e8be513c2b2bd8a33ab5e9e6498d65c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46820362"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a><span data-ttu-id="d7e22-104">Importar mensagens de plataforma de terceiros para o Microsoft Teams usando o Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="d7e22-104">Import third-party platform messages to Teams using Microsoft Graph</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d7e22-105">As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários.</span><span class="sxs-lookup"><span data-stu-id="d7e22-105">Microsoft Graph and Microsoft Teams public previews are available for early-access and feedback.</span></span> <span data-ttu-id="d7e22-106">Embora este lançamento tenha transcorrido testes extensivos, ele não se destina ao uso em produção.</span><span class="sxs-lookup"><span data-stu-id="d7e22-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

<span data-ttu-id="d7e22-107">Com o Microsoft Graph, você pode migrar os dados e o histórico de mensagens existentes dos usuários de um sistema externo para um canal do teams.</span><span class="sxs-lookup"><span data-stu-id="d7e22-107">With Microsoft Graph, you can migrate users' existing message history and data from an external system into a Teams channel.</span></span> <span data-ttu-id="d7e22-108">Ao habilitar a recreação de uma hierarquia de mensagens de plataforma de terceiros dentro do Teams, os usuários podem continuar a comunicação de forma perfeita e prosseguir sem interrupção.</span><span class="sxs-lookup"><span data-stu-id="d7e22-108">By enabling the recreation of a third-party platform messaging hierarchy inside Teams, users can continue their communications in a seamless manner and proceed without interruption.</span></span>

## <a name="import-overview"></a><span data-ttu-id="d7e22-109">Visão geral da importação</span><span class="sxs-lookup"><span data-stu-id="d7e22-109">Import overview</span></span>

<span data-ttu-id="d7e22-110">Em um nível alto, o processo de importação consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="d7e22-110">At a high level, the import process consists of the following:</span></span>

1. [<span data-ttu-id="d7e22-111">Criar uma equipe com um carimbo de data/hora Back-in-time</span><span class="sxs-lookup"><span data-stu-id="d7e22-111">Create a team with a back-in-time timestamp</span></span>](#step-one-create-a-team)
1. [<span data-ttu-id="d7e22-112">Criar um canal com um carimbo de data/hora Back-in-time</span><span class="sxs-lookup"><span data-stu-id="d7e22-112">Create a channel with a back-in-time timestamp</span></span>](#step-two-create-a-channel)  
1. [<span data-ttu-id="d7e22-113">Importar mensagens de data e hora internas externas</span><span class="sxs-lookup"><span data-stu-id="d7e22-113">Import external back-in-time dated messages</span></span>](#step-three-import-messages)
1. [<span data-ttu-id="d7e22-114">Concluir o processo de migração de canal e equipe</span><span class="sxs-lookup"><span data-stu-id="d7e22-114">Complete the team and channel migration process</span></span>](#step-four-complete-migration-mode)
1. [<span data-ttu-id="d7e22-115">Adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="d7e22-115">Add team members</span></span>](#step-five-add-team-members)

## <a name="necessary-requirements"></a><span data-ttu-id="d7e22-116">Requisitos necessários</span><span class="sxs-lookup"><span data-stu-id="d7e22-116">Necessary requirements</span></span>

### <a name="analyze-and-prepare-message-data"></a><span data-ttu-id="d7e22-117">Analisar e preparar dados de mensagens</span><span class="sxs-lookup"><span data-stu-id="d7e22-117">Analyze and prepare message data</span></span>

<span data-ttu-id="d7e22-118">✔ Analise os dados de terceiros para decidir o que será migrado.</span><span class="sxs-lookup"><span data-stu-id="d7e22-118">✔ Review the third-party data to decide what will be migrated.</span></span>  
<span data-ttu-id="d7e22-119">✔ Extrair os dados selecionados do sistema de chat de terceiros.</span><span class="sxs-lookup"><span data-stu-id="d7e22-119">✔ Extract the selected data from the third-party chat system.</span></span>  
<span data-ttu-id="d7e22-120">✔ Converter dados de importação em formato necessário para a migração.</span><span class="sxs-lookup"><span data-stu-id="d7e22-120">✔ Convert import data into format needed for migration.</span></span>  
<span data-ttu-id="d7e22-121">✔ Mapeie a estrutura de chat de terceiros para a estrutura do teams.</span><span class="sxs-lookup"><span data-stu-id="d7e22-121">✔ Map the third-party chat structure to the Teams structure.</span></span>

### <a name="set-up-your-office-365-tenant"></a><span data-ttu-id="d7e22-122">Configurar seu locatário do Office 365</span><span class="sxs-lookup"><span data-stu-id="d7e22-122">Set up your Office 365 tenant</span></span>

<span data-ttu-id="d7e22-123">✔ Garantir que um locatário do Office 365 existe para os dados de importação.</span><span class="sxs-lookup"><span data-stu-id="d7e22-123">✔ Ensure that an Office 365 tenant exists for the import data.</span></span> <span data-ttu-id="d7e22-124">Para obter mais informações sobre como configurar uma locação do Office 365 para o Teams, *consulte*, [Prepare Your Office 365 locatário](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="d7e22-124">For more information on setting up an Office 365 tenancy for Teams, *see*, [Prepare your Office 365 tenant](../../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>  
<span data-ttu-id="d7e22-125">✔ Certifique-se de que os membros da equipe estão no Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="d7e22-125">✔ Make sure that team members are in Azure Active Directory (AAD).</span></span>  <span data-ttu-id="d7e22-126">Para obter mais informações, *consulte* [Adicionar um novo usuário](/azure/active-directory/fundamentals/add-users-azure-active-directory) ao Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d7e22-126">For more information *see* [Add a new user](/azure/active-directory/fundamentals/add-users-azure-active-directory) to Azure Active Directory.</span></span>

## <a name="step-one-create-a-team"></a><span data-ttu-id="d7e22-127">Etapa 1: criar uma equipe</span><span class="sxs-lookup"><span data-stu-id="d7e22-127">Step One: Create a team</span></span>

<span data-ttu-id="d7e22-128">Como os dados existentes estão sendo migrados, a manutenção dos carimbos de data/hora da mensagem original e a prevenção da atividade de mensagens durante o processo de migração são fundamentais para recriar o fluxo de mensagens existente do usuário no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d7e22-128">Since existing data is being migrated, maintaining the original message timestamps and preventing messaging activity during the migration process are key to recreating the user's existing message flow in Teams.</span></span> <span data-ttu-id="d7e22-129">Isso é feito da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d7e22-129">This is achieved as follows:</span></span>

1. <span data-ttu-id="d7e22-130">[Crie uma nova equipe](/graph/api/team-post?view=graph-rest-beta&tabs=http) com um carimbo de data/hora Back-in-time usando a propriedade de recurso da equipe  `createdDateTime`  .</span><span class="sxs-lookup"><span data-stu-id="d7e22-130">[Create a new team](/graph/api/team-post?view=graph-rest-beta&tabs=http) with a back-in-time timestamp using the team resource  `createdDateTime`  property.</span></span>  

1. <span data-ttu-id="d7e22-131">Coloque a nova equipe no `migration mode` , um estado especial que faz a barra de usuários da maioria das atividades dentro da equipe até que o processo de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="d7e22-131">Place the new team in `migration mode`, a special state that bars users from most activities within the team until the migration process is complete.</span></span> <span data-ttu-id="d7e22-132">Inclua o `teamCreationMode` atributo de instância com o `migration` valor na solicitação post para identificar explicitamente a nova equipe como sendo criada para migração.</span><span class="sxs-lookup"><span data-stu-id="d7e22-132">Include the `teamCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a><span data-ttu-id="d7e22-133">Permissões</span><span class="sxs-lookup"><span data-stu-id="d7e22-133">Permissions</span></span>

|<span data-ttu-id="d7e22-134">ScopeName</span><span class="sxs-lookup"><span data-stu-id="d7e22-134">ScopeName</span></span>|<span data-ttu-id="d7e22-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d7e22-135">DisplayName</span></span>|<span data-ttu-id="d7e22-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7e22-136">Description</span></span>|<span data-ttu-id="d7e22-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="d7e22-137">Type</span></span>|<span data-ttu-id="d7e22-138">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="d7e22-138">Admin Consent?</span></span>|<span data-ttu-id="d7e22-139">Entidades/APIs abordadas</span><span class="sxs-lookup"><span data-stu-id="d7e22-139">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="d7e22-140">Gerenciar a migração para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d7e22-140">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="d7e22-141">Criando, Gerenciando recursos para migração para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d7e22-141">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="d7e22-142">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="d7e22-142">**Application-only**</span></span>|<span data-ttu-id="d7e22-143">Sim</span><span class="sxs-lookup"><span data-stu-id="d7e22-143">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a><span data-ttu-id="d7e22-144">Solicitação (criar uma equipe no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="d7e22-144">Request (create a team in migration state)</span></span>

```http
POST https://graph.microsoft.com/beta/teams

Content-Type: application/json
{
  "@microsoft.graph.teamCreationMode": "migration",
  "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('standard')",
  "displayName": "My Sample Team",
  "description": "My Sample Team’s Description"
  "createdDateTime": "2020-03-14T11:22:17.067Z"
}
```

#### <a name="response"></a><span data-ttu-id="d7e22-145">Resposta</span><span class="sxs-lookup"><span data-stu-id="d7e22-145">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{teamId}/operations/{operationId}
Content-Location: /teams/{teamId}
```

#### <a name="error-messages"></a><span data-ttu-id="d7e22-146">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="d7e22-146">Error messages</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="d7e22-147">`createdDateTime`  definido para futuro.</span><span class="sxs-lookup"><span data-stu-id="d7e22-147">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="d7e22-148">`createdDateTime`  especificado corretamente, mas o `teamCreationMode`  atributo de instância está ausente ou definido como um valor inválido.</span><span class="sxs-lookup"><span data-stu-id="d7e22-148">`createdDateTime`  correctly specified, but `teamCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-two-create-a-channel"></a><span data-ttu-id="d7e22-149">Etapa dois: criar um canal</span><span class="sxs-lookup"><span data-stu-id="d7e22-149">Step Two: Create a channel</span></span>

<span data-ttu-id="d7e22-150">A criação de um canal para as mensagens importadas é semelhante ao cenário criar equipe:</span><span class="sxs-lookup"><span data-stu-id="d7e22-150">Creating a channel for the imported messages is similar to the create team scenario:</span></span> 

1. <span data-ttu-id="d7e22-151">[Crie um novo canal](/graph/api/channel-post?view=graph-rest-beta&tabs=http) com um carimbo de data/hora de entrada usando a propriedade de recurso Channel `createdDateTime` .</span><span class="sxs-lookup"><span data-stu-id="d7e22-151">[Create a new channel](/graph/api/channel-post?view=graph-rest-beta&tabs=http) with a back-in-time timestamp using the channel resource `createdDateTime` property.</span></span>

1. <span data-ttu-id="d7e22-152">Coloque o novo canal `migration mode` , um estado especial que rebarra os usuários da maioria das atividades de chat no canal até que o processo de migração seja concluído.</span><span class="sxs-lookup"><span data-stu-id="d7e22-152">Place the new channel in `migration mode`, a special state that bars users from most chat activities within the channel until the migration process is complete.</span></span>  <span data-ttu-id="d7e22-153">Inclua o `channelCreationMode` atributo de instância com o `migration` valor na solicitação post para identificar explicitamente a nova equipe como sendo criada para migração.</span><span class="sxs-lookup"><span data-stu-id="d7e22-153">Include the `channelCreationMode` instance attribute with the `migration` value in the POST request to explicitly identify the new team as being created for migration.</span></span>  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a><span data-ttu-id="d7e22-154">Permissões</span><span class="sxs-lookup"><span data-stu-id="d7e22-154">Permissions</span></span>

|<span data-ttu-id="d7e22-155">ScopeName</span><span class="sxs-lookup"><span data-stu-id="d7e22-155">ScopeName</span></span>|<span data-ttu-id="d7e22-156">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d7e22-156">DisplayName</span></span>|<span data-ttu-id="d7e22-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7e22-157">Description</span></span>|<span data-ttu-id="d7e22-158">Tipo</span><span class="sxs-lookup"><span data-stu-id="d7e22-158">Type</span></span>|<span data-ttu-id="d7e22-159">Consentimento do administrador?</span><span class="sxs-lookup"><span data-stu-id="d7e22-159">Admin Consent?</span></span>|<span data-ttu-id="d7e22-160">Entidades/APIs abordadas</span><span class="sxs-lookup"><span data-stu-id="d7e22-160">Entities/APIs covered</span></span>|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|<span data-ttu-id="d7e22-161">Gerenciar a migração para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d7e22-161">Manage migration to Microsoft Teams</span></span>|<span data-ttu-id="d7e22-162">Criando, Gerenciando recursos para migração para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d7e22-162">Creating, managing resources for migration to Microsoft Teams</span></span>|<span data-ttu-id="d7e22-163">**Somente aplicativo**</span><span class="sxs-lookup"><span data-stu-id="d7e22-163">**Application-only**</span></span>|<span data-ttu-id="d7e22-164">Sim</span><span class="sxs-lookup"><span data-stu-id="d7e22-164">**Yes**</span></span>|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a><span data-ttu-id="d7e22-165">Solicitação (criar um canal no estado de migração)</span><span class="sxs-lookup"><span data-stu-id="d7e22-165">Request (create a channel in migration state)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/{id}/channels

Content-Type: application/json
{
  "@microsoft.graph.channelCreationMode": "migration",
  "displayName": "Architecture Discussion",
  "description": "This channel is where we debate all future architecture plans",
  "membershipType": "standard",
  "createdDateTime": "2020-03-14T11:22:17.067Z"
}
```

#### <a name="response"></a><span data-ttu-id="d7e22-166">Resposta</span><span class="sxs-lookup"><span data-stu-id="d7e22-166">Response</span></span>

```http
HTTP/1.1 202 Accepted
Location: /teams/{teamId}/channels/{channelId}/operations/{operationId}
Content-Location: /teams/{teamId}/channels/{channelId}
```

#### <a name="error-message"></a><span data-ttu-id="d7e22-167">Mensagem de erro</span><span class="sxs-lookup"><span data-stu-id="d7e22-167">Error message</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="d7e22-168">`createdDateTime`  definido para futuro.</span><span class="sxs-lookup"><span data-stu-id="d7e22-168">`createdDateTime`  set for future.</span></span>
* <span data-ttu-id="d7e22-169">`createdDateTime`  especificado corretamente, mas o `channelCreationMode`  atributo de instância está ausente ou definido como um valor inválido.</span><span class="sxs-lookup"><span data-stu-id="d7e22-169">`createdDateTime`  correctly specified but `channelCreationMode`  instance attribute  is missing or set to invalid value.</span></span>

## <a name="step-three-import-messages"></a><span data-ttu-id="d7e22-170">Etapa três: importar mensagens</span><span class="sxs-lookup"><span data-stu-id="d7e22-170">Step Three: Import messages</span></span>

<span data-ttu-id="d7e22-171">Depois que a equipe e o canal tiverem sido criados, você poderá começar a enviar mensagens de Back-in-time usando as `createdDateTime` `from`  teclas e no corpo da solicitação.</span><span class="sxs-lookup"><span data-stu-id="d7e22-171">After the team and channel have been created, you can begin sending back-in-time messages using the `createdDateTime`  and `from`  keys in the request body.</span></span>

#### <a name="request-post-message-that-is-text-only"></a><span data-ttu-id="d7e22-172">Solicitação (mensagem POST que é somente texto)</span><span class="sxs-lookup"><span data-stu-id="d7e22-172">Request (POST message that is text-only)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/messages

{
    "replyToId": null,
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
        "content": "Hello World"
    },
    "attachments": [],
    "mentions": [],
    "reactions": []
}
```

#### <a name="response"></a><span data-ttu-id="d7e22-173">Resposta</span><span class="sxs-lookup"><span data-stu-id="d7e22-173">Response</span></span>

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
        "content": "Hello World"
    },
    "attachments": [],
    "mentions": [],
    "reactions": []
}
```

#### <a name="request-post-a-message-with-inline-image"></a><span data-ttu-id="d7e22-174">Solicitação (postar uma mensagem com uma imagem ' inline ')</span><span class="sxs-lookup"><span data-stu-id="d7e22-174">Request (POST a message with inline \`image)</span></span>

> <span data-ttu-id="d7e22-175">**Observação**: não há escopos de permissão especiais neste cenário, pois a solicitação faz parte do chat; os escopos para chat também são aplicados aqui.</span><span class="sxs-lookup"><span data-stu-id="d7e22-175">**Note**: There are no special permission scopes in this scenario since the request is part of chatMessage; scopes for chatMessage apply here as well.</span></span>

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

#### <a name="response"></a><span data-ttu-id="d7e22-176">Resposta</span><span class="sxs-lookup"><span data-stu-id="d7e22-176">Response</span></span>

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
    {
      "body": {
        "contentType": "html",
        "content": "<div><div>\n<div><span><img height=\"250\" src=\"https://graph.microsoft.com/teams/teamId/channels/channelId/messages/id-value/hostedContents/hostedContentId/$value\" width=\"176.2295081967213\" style=\"vertical-align:bottom; width:176px; height:250px\"></span>\n\n</div>\n\n\n</div>\n</div>"
    },
    "attachments": [],
    "mentions": [],
    "reactions": []
}
```

## <a name="step-four-complete-migration-mode"></a><span data-ttu-id="d7e22-177">Etapa quatro: concluir o modo de migração</span><span class="sxs-lookup"><span data-stu-id="d7e22-177">Step Four: Complete migration mode</span></span>

<span data-ttu-id="d7e22-178">Após a conclusão do processo de migração de mensagens, a equipe e o canal são retirados do modo de migração usando o  `completeMigration`  método.</span><span class="sxs-lookup"><span data-stu-id="d7e22-178">Once the message migration process has completed, both the team and channel are taken out of migration mode using the  `completeMigration`  method.</span></span> <span data-ttu-id="d7e22-179">Esta etapa abre a equipe e os recursos do canal para uso geral por membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="d7e22-179">This step opens the team and channel resources for general use by team members.</span></span> <span data-ttu-id="d7e22-180">A ação está associada à `team` instância.</span><span class="sxs-lookup"><span data-stu-id="d7e22-180">The action is bound to the `team` instance.</span></span>

#### <a name="request-end-team-migration-mode"></a><span data-ttu-id="d7e22-181">Solicitação (modo de migração de equipe final)</span><span class="sxs-lookup"><span data-stu-id="d7e22-181">Request (end team migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="d7e22-182">Resposta</span><span class="sxs-lookup"><span data-stu-id="d7e22-182">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-channel-migration-mode"></a><span data-ttu-id="d7e22-183">Solicitação (modo de migração de canal final)</span><span class="sxs-lookup"><span data-stu-id="d7e22-183">Request (end channel migration mode)</span></span>

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/completeMigration

```

#### <a name="response"></a><span data-ttu-id="d7e22-184">Resposta</span><span class="sxs-lookup"><span data-stu-id="d7e22-184">Response</span></span>

```http
HTTP/1.1 204 NoContent
```

#### <a name="error-response"></a><span data-ttu-id="d7e22-185">Resposta de erro</span><span class="sxs-lookup"><span data-stu-id="d7e22-185">Error response</span></span>

```http
400 Bad Request
```

* <span data-ttu-id="d7e22-186">Ação chamada em um `team` ou `channel` que não está no `migrationMode` .</span><span class="sxs-lookup"><span data-stu-id="d7e22-186">Action called on a `team` or `channel` that is not in `migrationMode`.</span></span>

## <a name="step-five-add-team-members"></a><span data-ttu-id="d7e22-187">Etapa cinco: adicionar membros da equipe</span><span class="sxs-lookup"><span data-stu-id="d7e22-187">Step Five: Add team members</span></span>

<span data-ttu-id="d7e22-188">Você pode adicionar um membro a uma equipe [usando a interface do usuário do teams ou o](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) Microsoft Graph [Add Member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http) API:</span><span class="sxs-lookup"><span data-stu-id="d7e22-188">You can add a member to a team [using the Teams UI](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) or Microsoft Graph [Add member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http) API:</span></span>

#### <a name="request-add-member"></a><span data-ttu-id="d7e22-189">Solicitação (Adicionar membro)</span><span class="sxs-lookup"><span data-stu-id="d7e22-189">Request (add member)</span></span>

```http
POST https://graph.microsoft.com/beta/groups/{id}/members/$ref
Content-type: application/json
Content-length: 30

{
  "@odata.id": "https://graph.microsoft.com/beta/directoryObjects/{id}"
}
```

#### <a name="response"></a><span data-ttu-id="d7e22-190">Resposta</span><span class="sxs-lookup"><span data-stu-id="d7e22-190">Response</span></span>

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a><span data-ttu-id="d7e22-191">Dicas e informações adicionais</span><span class="sxs-lookup"><span data-stu-id="d7e22-191">Tips and additional information</span></span>

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* <span data-ttu-id="d7e22-192">Você pode importar mensagens de usuários que não estão no Teams.</span><span class="sxs-lookup"><span data-stu-id="d7e22-192">You can import messages from users who are not in Teams.</span></span>

* <span data-ttu-id="d7e22-193">Depois que a `completeMigration` solicitação é feita, não é possível importar outras mensagens para a equipe.</span><span class="sxs-lookup"><span data-stu-id="d7e22-193">Once the `completeMigration` request is made, you cannot import further messages into the team.</span></span>

* <span data-ttu-id="d7e22-194">Os membros da equipe só poderão ser adicionados à nova equipe depois que a `completeMigration` solicitação tiver retornado uma resposta bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d7e22-194">Team members can only be added to the new team after the `completeMigration` request has returned a successful response.</span></span>

* <span data-ttu-id="d7e22-195">Limitação: importação de mensagens em 5 RPS por canal.</span><span class="sxs-lookup"><span data-stu-id="d7e22-195">Throttling: Messages import at 5 RPS per channel.</span></span>

* <span data-ttu-id="d7e22-196">Se for necessário fazer uma correção nos resultados da migração, você precisará excluir a equipe e repetir as etapas para criar a equipe e canal e migrar novamente as mensagens.</span><span class="sxs-lookup"><span data-stu-id="d7e22-196">If you need to make a correction to the migration results, you need to delete the team and repeat the steps to create the team and channel and re-migrate the messages.</span></span>

> [!NOTE]
> <span data-ttu-id="d7e22-197">Atualmente, as imagens embutidas são o único tipo de mídia suportado pelo esquema de API de mensagens de importação.</span><span class="sxs-lookup"><span data-stu-id="d7e22-197">Currently, Inline images is the only type of media supported by the import message API schema.</span></span>

##### <a name="import-content-scope"></a><span data-ttu-id="d7e22-198">Importar escopo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="d7e22-198">Import content scope</span></span>

|<span data-ttu-id="d7e22-199">No escopo</span><span class="sxs-lookup"><span data-stu-id="d7e22-199">In-scope</span></span> | <span data-ttu-id="d7e22-200">Fora do escopo atualmente</span><span class="sxs-lookup"><span data-stu-id="d7e22-200">Currently out-of-scope</span></span>|
|----------|--------------------------|
|<span data-ttu-id="d7e22-201">Mensagens de canal e equipe</span><span class="sxs-lookup"><span data-stu-id="d7e22-201">Team and channel messages</span></span>|<span data-ttu-id="d7e22-202">1:1 e mensagens de chat de grupo</span><span class="sxs-lookup"><span data-stu-id="d7e22-202">1:1 and group chat messages</span></span>|
|<span data-ttu-id="d7e22-203">Hora de criação da mensagem original</span><span class="sxs-lookup"><span data-stu-id="d7e22-203">Created time of the original message</span></span>|<span data-ttu-id="d7e22-204">Canais privados</span><span class="sxs-lookup"><span data-stu-id="d7e22-204">Private channels</span></span>|
|<span data-ttu-id="d7e22-205">Imagens embutidas como parte da mensagem</span><span class="sxs-lookup"><span data-stu-id="d7e22-205">Inline images as part of the message</span></span>|<span data-ttu-id="d7e22-206">Em menção</span><span class="sxs-lookup"><span data-stu-id="d7e22-206">At mentions</span></span>|
|<span data-ttu-id="d7e22-207">Links para arquivos existentes no SPO/OneDrive</span><span class="sxs-lookup"><span data-stu-id="d7e22-207">Links to existing files in SPO/OneDrive</span></span>|<span data-ttu-id="d7e22-208">Reações</span><span class="sxs-lookup"><span data-stu-id="d7e22-208">Reactions</span></span>|
|<span data-ttu-id="d7e22-209">Mensagens com Rich Text</span><span class="sxs-lookup"><span data-stu-id="d7e22-209">Messages with rich text</span></span>|<span data-ttu-id="d7e22-210">Vídeos</span><span class="sxs-lookup"><span data-stu-id="d7e22-210">Videos</span></span>|
|<span data-ttu-id="d7e22-211">Cadeia de resposta de mensagem</span><span class="sxs-lookup"><span data-stu-id="d7e22-211">Message reply chain</span></span>|<span data-ttu-id="d7e22-212">Announcements</span><span class="sxs-lookup"><span data-stu-id="d7e22-212">Announcements</span></span>|
|<span data-ttu-id="d7e22-213">Processamento de alta produtividade</span><span class="sxs-lookup"><span data-stu-id="d7e22-213">High throughput processing</span></span>|<span data-ttu-id="d7e22-214">Trechos de código</span><span class="sxs-lookup"><span data-stu-id="d7e22-214">Code snippets</span></span>|
||<span data-ttu-id="d7e22-215">Cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="d7e22-215">Adaptive cards</span></span>|
||<span data-ttu-id="d7e22-216">Etiquetas</span><span class="sxs-lookup"><span data-stu-id="d7e22-216">Stickers</span></span>|
||<span data-ttu-id="d7e22-217">Emojis</span><span class="sxs-lookup"><span data-stu-id="d7e22-217">Emojis</span></span>|
||<span data-ttu-id="d7e22-218">Eletrônica</span><span class="sxs-lookup"><span data-stu-id="d7e22-218">Quotes</span></span>|
||<span data-ttu-id="d7e22-219">Postagens entre canais</span><span class="sxs-lookup"><span data-stu-id="d7e22-219">Cross posts between channels</span></span>|

> [!div class="nextstepaction"]
>[<span data-ttu-id="d7e22-220">Saiba mais sobre a integração do Microsoft Graph e do teams</span><span class="sxs-lookup"><span data-stu-id="d7e22-220">Learn more about Microsoft Graph and Teams integration</span></span>](/graph/teams-concept-overview)
