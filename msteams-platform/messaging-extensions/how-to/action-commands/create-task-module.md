---
title: Crie e envie o módulo de tarefas
author: clearab
description: Como manipular a ação de invocação inicial e responder com um módulo de tarefa de um comando de extensão de mensagens de ação
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: fbe90b3a3af8dbb053fdbaf6b4cd9b96344eaf00
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075588"
---
# <a name="create-and-send-the-task-module"></a><span data-ttu-id="68d96-103">Crie e envie o módulo de tarefas</span><span class="sxs-lookup"><span data-stu-id="68d96-103">Create and send the task module</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="68d96-104">Você pode criar o módulo de tarefa usando um Cartão Adaptável ou um exibição da Web incorporado.</span><span class="sxs-lookup"><span data-stu-id="68d96-104">You can create the task module using an Adaptive Card or an embedded web view.</span></span> <span data-ttu-id="68d96-105">Para criar um módulo de tarefa, você deve executar o processo chamado de solicitação de invocação inicial.</span><span class="sxs-lookup"><span data-stu-id="68d96-105">To create a task module, you must perform the process called the initial invoke request.</span></span> <span data-ttu-id="68d96-106">Este documento abrange a solicitação de invocação inicial, propriedades de atividade de carga quando um módulo de tarefa é invocado a partir de chat 1:1, chat de grupo, canal (nova postagem), canal (resposta ao thread) e caixa de comando.</span><span class="sxs-lookup"><span data-stu-id="68d96-106">This document covers the initial invoke request, payload activity properties when a task module is invoked from 1:1 chat, group chat, channel (new post), channel (reply to thread), and command box.</span></span> 
> [!NOTE]
> <span data-ttu-id="68d96-107">Se você não estiver preenchendo o módulo de tarefas com parâmetros definidos no manifesto do aplicativo, você deve criar o módulo de tarefa para usuários com um Cartão Adaptável ou uma exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="68d96-107">If you are not populating the task module with parameters defined in the app manifest, you must create the task module for users with either an Adaptive Card or an embedded web view.</span></span>

## <a name="the-initial-invoke-request"></a><span data-ttu-id="68d96-108">A solicitação de invocação inicial</span><span class="sxs-lookup"><span data-stu-id="68d96-108">The initial invoke request</span></span>

<span data-ttu-id="68d96-109">No processo da solicitação de invocação inicial, seu serviço recebe um objeto do tipo e você deve responder com um objeto contendo um Cartão Adaptável ou uma URL para o exibição `Activity` `composeExtension/fetchTask` da Web `task` incorporado.</span><span class="sxs-lookup"><span data-stu-id="68d96-109">In the process of the initial invoke request, your service receives an `Activity` object of type `composeExtension/fetchTask`, and you must respond with a `task` object containing either an Adaptive Card or a URL to the embedded web view.</span></span> <span data-ttu-id="68d96-110">Junto com as propriedades de atividade de bot padrão, a carga de invocação inicial contém os seguintes metadados de solicitação:</span><span class="sxs-lookup"><span data-stu-id="68d96-110">Along with the standard bot activity properties, the initial invoke payload contains the following request metadata:</span></span>

|<span data-ttu-id="68d96-111">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="68d96-111">Property name</span></span>|<span data-ttu-id="68d96-112">Objetivo</span><span class="sxs-lookup"><span data-stu-id="68d96-112">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="68d96-113">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-113">Type of request.</span></span> <span data-ttu-id="68d96-114">Deve ser `invoke` .</span><span class="sxs-lookup"><span data-stu-id="68d96-114">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="68d96-115">Tipo de comando emitido ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="68d96-115">Type of command that is issued to your service.</span></span> <span data-ttu-id="68d96-116">Deve ser `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="68d96-116">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="68d96-117">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-117">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="68d96-118">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-118">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="68d96-119">Azure Active Directory ID do objeto do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-119">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="68d96-120">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="68d96-120">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="68d96-121">ID do canal (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="68d96-121">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="68d96-122">ID da equipe (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="68d96-122">Team ID (if the request was made in a channel).</span></span> |
|`value.commandId` | <span data-ttu-id="68d96-123">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-123">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="68d96-124">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="68d96-124">The context that triggered the event.</span></span> <span data-ttu-id="68d96-125">Deve ser `compose` .</span><span class="sxs-lookup"><span data-stu-id="68d96-125">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="68d96-126">O tema cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="68d96-126">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="68d96-127">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="68d96-127">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="68d96-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-128">Example</span></span>

<span data-ttu-id="68d96-129">O código da solicitação de invocação inicial é dado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="68d96-129">The code for the initial invoke request is given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:bc319b1d-571a-194d-9ffb-11d7ab37c9ff",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  }
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "fe50f49e5c74440bb2ebf07f49e9553c",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-11-chat"></a><span data-ttu-id="68d96-130">Propriedades de atividade de carga quando um módulo de tarefa é invocado do chat 1:1</span><span class="sxs-lookup"><span data-stu-id="68d96-130">Payload activity properties when a task module is invoked from 1:1 chat</span></span> 

<span data-ttu-id="68d96-131">As propriedades de atividade de carga quando um módulo de tarefa é invocado do chat 1:1 são listadas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="68d96-131">The payload activity properties when a task module is invoked from 1:1 chat are listed as follows:</span></span>

|<span data-ttu-id="68d96-132">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="68d96-132">Property name</span></span>|<span data-ttu-id="68d96-133">Objetivo</span><span class="sxs-lookup"><span data-stu-id="68d96-133">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="68d96-134">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-134">Type of request.</span></span> <span data-ttu-id="68d96-135">Deve ser `invoke` .</span><span class="sxs-lookup"><span data-stu-id="68d96-135">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="68d96-136">Tipo de comando emitido ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="68d96-136">Type of command that is issued to your service.</span></span> <span data-ttu-id="68d96-137">Deve ser `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="68d96-137">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="68d96-138">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-138">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="68d96-139">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-139">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="68d96-140">Azure Active Directory ID do objeto do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-140">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="68d96-141">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="68d96-141">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="68d96-142">O nome de origem de onde o módulo de tarefa é invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-142">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="68d96-143">Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta.</span><span class="sxs-lookup"><span data-stu-id="68d96-143">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="68d96-144">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-144">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="68d96-145">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="68d96-145">The context that triggered the event.</span></span> <span data-ttu-id="68d96-146">Deve ser `compose` .</span><span class="sxs-lookup"><span data-stu-id="68d96-146">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="68d96-147">O tema cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="68d96-147">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="68d96-148">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="68d96-148">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="68d96-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-149">Example</span></span>

<span data-ttu-id="68d96-150">As propriedades de atividade de carga quando um módulo de tarefa é invocado do chat 1:1 são fornecidas no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="68d96-150">The payload activity properties when a task module is invoked from 1:1 chat are given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:bc319b1d-571a-194d-9ffb-11d7ab37c9ff",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  }
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "fe50f49e5c74440bb2ebf07f49e9553c",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```
## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-group-chat"></a><span data-ttu-id="68d96-151">Propriedades de atividade de carga quando um módulo de tarefa é invocado de um chat de grupo</span><span class="sxs-lookup"><span data-stu-id="68d96-151">Payload activity properties when a task module is invoked from a group chat</span></span> 

<span data-ttu-id="68d96-152">As propriedades de atividade de carga quando um módulo de tarefa é invocado de um chat de grupo são listadas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="68d96-152">The payload activity properties when a task module is invoked from a group chat are listed as follows:</span></span>

|<span data-ttu-id="68d96-153">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="68d96-153">Property name</span></span>|<span data-ttu-id="68d96-154">Objetivo</span><span class="sxs-lookup"><span data-stu-id="68d96-154">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="68d96-155">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-155">Type of request.</span></span> <span data-ttu-id="68d96-156">Deve ser `invoke` .</span><span class="sxs-lookup"><span data-stu-id="68d96-156">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="68d96-157">Tipo de comando emitido ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="68d96-157">Type of command that is issued to your service.</span></span> <span data-ttu-id="68d96-158">Deve ser `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="68d96-158">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="68d96-159">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-159">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="68d96-160">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-160">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="68d96-161">Azure Active Directory ID do objeto do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-161">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="68d96-162">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="68d96-162">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="68d96-163">O nome de origem de onde o módulo de tarefa é invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-163">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="68d96-164">Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta.</span><span class="sxs-lookup"><span data-stu-id="68d96-164">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="68d96-165">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-165">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="68d96-166">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="68d96-166">The context that triggered the event.</span></span> <span data-ttu-id="68d96-167">Deve ser `compose` .</span><span class="sxs-lookup"><span data-stu-id="68d96-167">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="68d96-168">O tema cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="68d96-168">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="68d96-169">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="68d96-169">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="68d96-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-170">Example</span></span>

<span data-ttu-id="68d96-171">As propriedades de atividade de carga quando um módulo de tarefa é invocado de um chat de grupo são fornecidas no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="68d96-171">The payload activity properties when a task module is invoked from a group chat are given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:bf72031f-a17e-f99c-48dc-5c0714950d87",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "groupChat",
    "id": "19:d77be72390a1416e9644261e9064fa00@thread.skype",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "213167a1e3b6428b93e186ea5407c759",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-channel-new-post"></a><span data-ttu-id="68d96-172">Propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (nova postagem)</span><span class="sxs-lookup"><span data-stu-id="68d96-172">Payload activity properties when a task module is invoked from a channel (new post)</span></span> 

<span data-ttu-id="68d96-173">As propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (nova postagem) são listadas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="68d96-173">The payload activity properties when a task module is invoked from a channel (new post) are listed as follows:</span></span>

|<span data-ttu-id="68d96-174">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="68d96-174">Property name</span></span>|<span data-ttu-id="68d96-175">Objetivo</span><span class="sxs-lookup"><span data-stu-id="68d96-175">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="68d96-176">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-176">Type of request.</span></span> <span data-ttu-id="68d96-177">Deve ser `invoke` .</span><span class="sxs-lookup"><span data-stu-id="68d96-177">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="68d96-178">Tipo de comando emitido ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="68d96-178">Type of command that is issued to your service.</span></span> <span data-ttu-id="68d96-179">Deve ser `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="68d96-179">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="68d96-180">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-180">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="68d96-181">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-181">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="68d96-182">Azure Active Directory ID do objeto do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-182">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="68d96-183">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="68d96-183">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="68d96-184">ID do canal (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="68d96-184">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="68d96-185">ID da equipe (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="68d96-185">Team ID (if the request was made in a channel).</span></span> |
|`channelData.source.name`| <span data-ttu-id="68d96-186">O nome de origem de onde o módulo de tarefa é invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-186">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="68d96-187">Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta.</span><span class="sxs-lookup"><span data-stu-id="68d96-187">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="68d96-188">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-188">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="68d96-189">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="68d96-189">The context that triggered the event.</span></span> <span data-ttu-id="68d96-190">Deve ser `compose` .</span><span class="sxs-lookup"><span data-stu-id="68d96-190">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="68d96-191">O tema cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="68d96-191">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="68d96-192">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="68d96-192">It must be `default`, `contrast`, or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="68d96-193">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-193">Example</span></span>

<span data-ttu-id="68d96-194">As propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (nova postagem) são fornecidas no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="68d96-194">The payload activity properties when a task module is invoked from a channel (new post) are given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:a5fbb109-c989-c449-ee83-71ac99919d4b",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "5336640edc7748b28ce2df43f5b45963",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-channel-reply-to-thread"></a><span data-ttu-id="68d96-195">Propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (responder ao thread)</span><span class="sxs-lookup"><span data-stu-id="68d96-195">Payload activity properties when a task module is invoked from a channel (reply to thread)</span></span> 

<span data-ttu-id="68d96-196">As propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (resposta ao thread) são listadas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="68d96-196">The payload activity properties when a task module is invoked from a channel (reply to thread) are listed as follows:</span></span>

|<span data-ttu-id="68d96-197">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="68d96-197">Property name</span></span>|<span data-ttu-id="68d96-198">Objetivo</span><span class="sxs-lookup"><span data-stu-id="68d96-198">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="68d96-199">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-199">Type of request.</span></span> <span data-ttu-id="68d96-200">Deve ser `invoke` .</span><span class="sxs-lookup"><span data-stu-id="68d96-200">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="68d96-201">Tipo de comando emitido ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="68d96-201">Type of command that is issued to your service.</span></span> <span data-ttu-id="68d96-202">Deve ser `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="68d96-202">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="68d96-203">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-203">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="68d96-204">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-204">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="68d96-205">Azure Active Directory ID do objeto do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-205">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="68d96-206">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="68d96-206">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="68d96-207">ID do canal (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="68d96-207">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="68d96-208">ID da equipe (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="68d96-208">Team ID (if the request was made in a channel).</span></span> |
|`channelData.source.name`| <span data-ttu-id="68d96-209">O nome de origem de onde o módulo de tarefa é invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-209">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="68d96-210">Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta.</span><span class="sxs-lookup"><span data-stu-id="68d96-210">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="68d96-211">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-211">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="68d96-212">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="68d96-212">The context that triggered the event.</span></span> <span data-ttu-id="68d96-213">Deve ser `compose` .</span><span class="sxs-lookup"><span data-stu-id="68d96-213">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="68d96-214">O tema cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="68d96-214">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="68d96-215">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="68d96-215">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="68d96-216">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-216">Example</span></span>

<span data-ttu-id="68d96-217">As propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (resposta ao thread) são fornecidas no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="68d96-217">The payload activity properties when a task module is invoked from a channel (reply to thread) are given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:19ccc884-c792-35ef-2f40-d0ff43dcca71",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype;messageid=1611060744833",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "TEst",
    "commandContext": "message",
    "requestId": "7f7d22efe5414818becebcec649a7912",
    "messagePayload": {
      "linkToMessage": "https://teams.microsoft.com/l/message/19:6decf54d86d945e4b3924b63a9161a78@thread.skype/1611060744833",
      "id": "1611060744833",
      "replyToId": null,
      "createdDateTime": "2021-01-19T12:52:24.833Z",
      "lastModifiedDateTime": null,
      "deleted": false,
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "body": {
        "contentType": "html",
        "content": "<div><div><at id=\"0\">Testing outgoing Webhook-Nikitha</at> - Hi</div>\n</div>"
      },
      "from": {
        "device": null,
        "conversation": null,
        "user": {
          "userIdentityType": "aadUser",
          "id": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc",
          "displayName": "Olo Brockhouse"
        },
        "application": null
      },
      "reactions": [],
      "mentions": [
        {
          "id": 0,
          "mentionText": "Testing outgoing Webhook-Nikitha",
          "mentioned": {
            "device": null,
            "conversation": null,
            "user": null,
            "application": {
              "applicationIdentityType": "webhook",
              "id": "b8c1c68c-e290-4bdd-81c3-266f310751dc",
              "displayName": "Testing outgoing Webhook-Nikitha"
            }
          }
        }
      ],
      "attachments": []
    },
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-command-box"></a><span data-ttu-id="68d96-218">Propriedades de atividade de carga quando um módulo de tarefa é invocado de uma caixa de comando</span><span class="sxs-lookup"><span data-stu-id="68d96-218">Payload activity properties when a task module is invoked from a command box</span></span> 

<span data-ttu-id="68d96-219">As propriedades de atividade de carga quando um módulo de tarefa é invocado de uma caixa de comando são listadas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="68d96-219">The payload activity properties when a task module is invoked from a command box are listed as follows:</span></span>

|<span data-ttu-id="68d96-220">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="68d96-220">Property name</span></span>|<span data-ttu-id="68d96-221">Objetivo</span><span class="sxs-lookup"><span data-stu-id="68d96-221">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="68d96-222">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-222">Type of request.</span></span> <span data-ttu-id="68d96-223">Deve ser `invoke` .</span><span class="sxs-lookup"><span data-stu-id="68d96-223">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="68d96-224">Tipo de comando emitido ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="68d96-224">Type of command that is issued to your service.</span></span> <span data-ttu-id="68d96-225">Deve ser `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="68d96-225">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="68d96-226">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-226">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="68d96-227">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-227">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="68d96-228">Azure Active Directory ID do objeto do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="68d96-228">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="68d96-229">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="68d96-229">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="68d96-230">O nome de origem de onde o módulo de tarefa é invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-230">The source name from where task module is invoked.</span></span> |
|`value.commandId` | <span data-ttu-id="68d96-231">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="68d96-231">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="68d96-232">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="68d96-232">The context that triggered the event.</span></span> <span data-ttu-id="68d96-233">Deve ser `compose` .</span><span class="sxs-lookup"><span data-stu-id="68d96-233">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="68d96-234">O tema cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="68d96-234">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="68d96-235">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="68d96-235">It must be `default`, `contrast`, or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="68d96-236">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-236">Example</span></span>

<span data-ttu-id="68d96-237">As propriedades de atividade de carga quando um módulo de tarefa é invocado de uma caixa de comando são fornecidas no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="68d96-237">The payload activity properties when a task module is invoked from a command box are given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:172560f1-95f9-3189-edb2-b7612cd1a3cd",
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "TEst",
    "commandContext": "compose",
    "requestId": "d2ce690cdc2b4920a538e75882610a30",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

### <a name="example"></a><span data-ttu-id="68d96-238">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-238">Example</span></span> 

<span data-ttu-id="68d96-239">A seção de código a seguir é um exemplo de `fetchTask` solicitação:</span><span class="sxs-lookup"><span data-stu-id="68d96-239">The following code section is an example of `fetchTask` request:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="68d96-240">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="68d96-240">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle fetch task
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="68d96-241">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="68d96-241">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreviewBot extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    //hand fetch task
  }
}
```

# <a name="json"></a>[<span data-ttu-id="68d96-242">JSON</span><span class="sxs-lookup"><span data-stu-id="68d96-242">JSON</span></span>](#tab/json)

```json
{
  "name": "composeExtension/fetchTask",
  "type": "invoke",
  "timestamp": "2019-07-01T22:57:22.175Z",
  "localTimestamp": "2019-07-01T15:57:22.175-07:00",
  "id": "f:0123456878990178955",
  "channelId": "msteams",
  "serviceURL": "https://smba.trafficmanager.net/amer/",
  "from": {
    "id": "29:1test2GgHIa0DXzDT_OGwL5vSMZdAxDlGR7hYxZ6_JBVqHz2Zq9Nm44FUNWqHCdGBwHg8WrlFRsYrd0cCAS7dig",
    "name": "John Smith",
    "aadObjectId": "1234567d-1234-462a-8952-35b75f16f1e1"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "tenantId": "1234abcd-1234-12ab-12ab-35b75f16f1e1",
    "id": "19:83ed1d507cb5427c93495cf914326310@thread.skype"
  },
  "recipient": {
    "id": "28:049566e0-4401-4bcf-86a1-ce22082ce03a",
    "name": "mess"
  },
  "entities": [
    {
      "locale": "en-US",
      "country": "US",
      "platform": "Windows",
      "type": "clientInfo"
    }
  ],
  "channelData": {
    "channel": {
      "id": "19:83ab1d507cb5427c93495cf912345678@thread.skype"
    },
    "team": {
      "id": "19:83ab1d507cb5427c93495cf912345678@thread.skype"
    },
    "tenant": {
      "id": "1234abcd-1234-12ab-12ab-35b75f16f1e1"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "hello",
    "commandContext": "compose",
    "context": {
      "theme": "dark"
    }
  },
  "locale": "en-US"
}
```

* * *

## <a name="initial-invoke-request-from-a-message"></a><span data-ttu-id="68d96-243">Solicitação de invocação inicial de uma mensagem</span><span class="sxs-lookup"><span data-stu-id="68d96-243">Initial invoke request from a message</span></span>

<span data-ttu-id="68d96-244">Quando o bot é invocado de uma mensagem, o objeto na solicitação de invocação inicial deve conter os detalhes da mensagem da sua extensão de `value` mensagens.</span><span class="sxs-lookup"><span data-stu-id="68d96-244">When your bot is invoked from a message,  the `value` object in the initial invoke request must contain the details of the message that your messaging extension is invoked from.</span></span> <span data-ttu-id="68d96-245">As matrizes e são opcionais e não estão presentes se não houver reações ou `reactions` `mentions` menções na mensagem original.</span><span class="sxs-lookup"><span data-stu-id="68d96-245">The `reactions` and `mentions` arrays are optional, and they are not present if there are no reactions or mentions in the original message.</span></span> <span data-ttu-id="68d96-246">A seção a seguir é um exemplo do `value` objeto:</span><span class="sxs-lookup"><span data-stu-id="68d96-246">The following section is an example of the `value` object:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="68d96-247">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="68d96-247">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var messageText = action.MessagePayload.Body.Content;
  var fromId = action.MessagePayload.From.User.Id;

  //finish handling the fetchTask
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="68d96-248">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="68d96-248">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    const messageText = action.messagePayload.body.content;

    //finish handling the fetchTask
  }
}
```

# <a name="json"></a>[<span data-ttu-id="68d96-249">JSON</span><span class="sxs-lookup"><span data-stu-id="68d96-249">JSON</span></span>](#tab/json)

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
...
  "value": {
    "commandId": "setReminder",
    "commandContext": "message",
    "messagePayload": {
      "id": "1111111111",
      "replyToId": null,
      "createdDateTime": "2019-02-25T21:29:36.065Z",
      "lastModifiedDateTime": null,
      "deleted": false,
      "subject": "Message subject",
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "body": {
        "contentType": "html",
        "content": "This is the message the messaging extension was invoked from."
    },
      "from": {
        "device": null,
        "conversation": null,
        "user": {
          "userIdentityType": "aadUser",
          "id": "wxyz12ab8-ab12-cd34-ef56-098abc123876",
          "displayName": "Jamie Smythe"
        },
        "application": null
      },
      "reactions": [
        {
          "reactionType": "like",
          "createdDateTime": "2019-02-25T22:40:40.806Z",
          "user": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "qrst12346-ab12-cd34-ef56-098abc123876",
              "displayName": "Jim Brown"
            },
            "application": null
          }
        }
      ],
      "mentions": [
        {
          "id": 0,
          "mentionText": "Sarah",
          "mentioned": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "ab12345678-ab12-cd34-ef56-098abc123876",
              "displayName": "Sarah"
            },
            "application": null
          }
        }
      ]
    }
  ...
```

* * *

## <a name="respond-to-the-fetchtask"></a><span data-ttu-id="68d96-250">Responder ao fetchTask</span><span class="sxs-lookup"><span data-stu-id="68d96-250">Respond to the fetchTask</span></span>

<span data-ttu-id="68d96-251">Responda à solicitação de invocação com um objeto que contém um objeto com o Cartão Adaptável ou a URL da `task` Web ou uma mensagem de cadeia de `taskInfo` caracteres simples.</span><span class="sxs-lookup"><span data-stu-id="68d96-251">Respond to the invoke request with a `task` object that contains either a `taskInfo` object with the Adaptive Card or web URL, or a simple string message.</span></span>

|<span data-ttu-id="68d96-252">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="68d96-252">Property name</span></span>|<span data-ttu-id="68d96-253">Objetivo</span><span class="sxs-lookup"><span data-stu-id="68d96-253">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="68d96-254">Pode ser para `continue` apresentar um formulário ou para um `message` pop-up simples.</span><span class="sxs-lookup"><span data-stu-id="68d96-254">Can be either `continue` to present a form, or `message` for a simple popup.</span></span> |
|`value`| <span data-ttu-id="68d96-255">Um `taskInfo` objeto para um formulário ou um `string` para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="68d96-255">Either a `taskInfo` object for a form, or a `string` for a message.</span></span> |

<span data-ttu-id="68d96-256">O esquema do objeto taskInfo é:</span><span class="sxs-lookup"><span data-stu-id="68d96-256">The schema for the taskInfo object is:</span></span>

|<span data-ttu-id="68d96-257">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="68d96-257">Property name</span></span>|<span data-ttu-id="68d96-258">Objetivo</span><span class="sxs-lookup"><span data-stu-id="68d96-258">Purpose</span></span>|
|---|---|
|`title`| <span data-ttu-id="68d96-259">O título do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="68d96-259">The title of the task module.</span></span>|
|`height`| <span data-ttu-id="68d96-260">Deve ser um inteiro (em pixels) ou `small` `medium` , `large` .</span><span class="sxs-lookup"><span data-stu-id="68d96-260">It must be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`width`| <span data-ttu-id="68d96-261">Deve ser um inteiro (em pixels) ou `small` `medium` , `large` .</span><span class="sxs-lookup"><span data-stu-id="68d96-261">It must be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`card`| <span data-ttu-id="68d96-262">O cartão adaptável que define o formulário (se estiver usando um).</span><span class="sxs-lookup"><span data-stu-id="68d96-262">The adaptive card defining the form (if using one).</span></span>
|`url`| <span data-ttu-id="68d96-263">A URL a ser aberta dentro do módulo de tarefas como uma exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="68d96-263">The URL to be opened inside of the task module as an embedded web view.</span></span>|
|`fallbackUrl`| <span data-ttu-id="68d96-264">Se um cliente não suportar o recurso de módulo de tarefa, essa URL será aberta em uma guia do navegador.</span><span class="sxs-lookup"><span data-stu-id="68d96-264">If a client does not support the task module feature, this URL is opened in a browser tab.</span></span> |

### <a name="respond-to-the-fetchtask-with-an-adaptive-card"></a><span data-ttu-id="68d96-265">Responder ao fetchTask com um Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="68d96-265">Respond to the fetchTask with an Adaptive Card</span></span>

<span data-ttu-id="68d96-266">Ao usar um cartão adaptável, você deve responder com um objeto com o `task` objeto que contém um Cartão `value` Adaptável.</span><span class="sxs-lookup"><span data-stu-id="68d96-266">When using an adaptive card, you must respond with a `task` object with the `value` object containing an Adaptive Card.</span></span>

#### <a name="example"></a><span data-ttu-id="68d96-267">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-267">Example</span></span>

<span data-ttu-id="68d96-268">A seção de código a seguir é um exemplo de `fetchTask` resposta com um cartão adaptável:</span><span class="sxs-lookup"><span data-stu-id="68d96-268">The following code section is an example to `fetchTask` response with an adaptive card:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="68d96-269">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="68d96-269">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="68d96-270">Este exemplo usa o [pacote AdaptiveCards NuGet](https://www.nuget.org/packages/AdaptiveCards) além do SDK da Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="68d96-270">This sample uses the [AdaptiveCards NuGet package](https://www.nuget.org/packages/AdaptiveCards) in addition to the Bot Framework SDK.</span></span>

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  string placeholder = "Not invoked from message";

  if (action.MessagePayload != null)
  {
      var messageText = action.MessagePayload.Body.Content;
      var fromId = action.MessagePayload.From.User.Id;
      placeholder = "Invoked from message";
  }

  var response = new MessagingExtensionActionResponse()
  {
    Task = new TaskModuleContinueResponse()
    {
      Value = new TaskModuleTaskInfo()
      {
        Height = "small",
        Width = "small",
        Title = "Example task module",
        Card = new Attachment()
        {
          ContentType = AdaptiveCard.ContentType,
          Content = new AdaptiveCard("1.0")
          {
            Body = new List<AdaptiveElement>()
            {
              new AdaptiveTextInput() { Id = "FormField1", Placeholder = placeholder},
              new AdaptiveTextInput() { Id = "FormField2", Placeholder = "FormField2"},
              new AdaptiveTextInput() { Id = "FormField3", Placeholder = "FormField3"},
            },
            Actions = new List<AdaptiveAction>()
            {
              new AdaptiveSubmitAction()
              {
                Type = AdaptiveSubmitAction.TypeName,
                Title = "Submit",
              },
            },
          },
        },
      },
    },
  };
  return response;
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="68d96-271">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="68d96-271">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
    handleTeamsMessagingExtensionFetchTask(context, action) {
      const adaptiveCard = CardFactory.adaptiveCard({
        actions: [{
          data: { submitLocation: 'messagingExtensionFetchTask'},
          title: 'Submit',
          type: 'Action.Submit'
        }],
        body: [
          { text: 'Task Module', type: 'TextBlock', weight: 'bolder'},
          { type: 'TextBlock', text: 'Enter text for Question:' },
          { id: 'Question', placeholder: 'Question text here', type: 'Input.Text', value: userText },
          { type: 'TextBlock', text: 'Options for Question:' },
          { type: 'TextBlock', text: 'Is Multi-Select:' },
          {
            choices: [{ title: 'True', value: 'true' }, { title: 'False', value: 'false' }],
            id: 'MultiSelect',
            isMultiSelect: false,
            style: 'expanded',
            type: 'Input.ChoiceSet',
            value: isMultiSelect ? 'true' : 'false'
          },
          { id: 'Option1', placeholder: 'Option 1 here', type: 'Input.Text', value: option1 },
          { id: 'Option2', placeholder: 'Option 2 here', type: 'Input.Text', value: option2 }
        ],
        type: 'AdaptiveCard',
        version: '1.0'
      });

      return {
        task: {
          type: 'continue',
          value: {
            card: adaptiveCard,
            height: 450,
            title: 'Task Module Fetch Example',
            url: null,
            width: 500
          }
        }
      };
    }
}
```

# <a name="json"></a>[<span data-ttu-id="68d96-272">JSON</span><span class="sxs-lookup"><span data-stu-id="68d96-272">JSON</span></span>](#tab/json)

```json
 {
  "task": {
    "type": "continue",
    "value": {
      "title": "Task module title",
      "height": 500,
      "width": "medium",
      "card": {
        "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Input.Text",
            "placeholder": "FormField1",
            "id": "FormField1"
          },
          {
            "type": "Input.Text",
            "placeholder": "FormField2",
            "id": "FormField2"
          },
          {
            "type": "Input.Text",
            "placeholder": "FormField3",
            "id": "FormField3"
          },
          {
            "type": "ActionSet",
            "actions": [
              {
                "type": "Action.Submit",
                "title": "Action.Submit",
                "id": "submitAction"
              }
            ]
          }
        ]
      }
    }
  }
}
```

* * *

### <a name="create-a-task-module-with-an-embedded-web-view"></a><span data-ttu-id="68d96-273">Criar um módulo de tarefa com um visualização da Web incorporado</span><span class="sxs-lookup"><span data-stu-id="68d96-273">Create a task module with an embedded web view</span></span>

<span data-ttu-id="68d96-274">Ao usar uma exibição da Web incorporada, você deve responder com um objeto com o objeto que contém a URL para o formulário `task` da Web que deseja `value` carregar.</span><span class="sxs-lookup"><span data-stu-id="68d96-274">When using an embedded web view, you must respond with a `task` object with the `value` object containing the URL to the web form that you want to load.</span></span> <span data-ttu-id="68d96-275">Os domínios de qualquer URL que você deseja carregar devem ser incluídos na `validDomains` matriz no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="68d96-275">The domains of any URL you want to load must be included in the `validDomains` array in your app's manifest.</span></span> <span data-ttu-id="68d96-276">Para obter mais informações sobre como criar sua exibição da Web incorporada, consulte a [documentação do módulo de tarefas](~/task-modules-and-cards/what-are-task-modules.md).</span><span class="sxs-lookup"><span data-stu-id="68d96-276">For more information on building your embedded web view, see the [task module documentation](~/task-modules-and-cards/what-are-task-modules.md).</span></span> 

# <a name="cnet"></a>[<span data-ttu-id="68d96-277">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="68d96-277">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  string placeholder = "Not invoked from message";

  if (action.MessagePayload != null)
  {
      var messageText = action.MessagePayload.Body.Content;
      var fromId = action.MessagePayload.From.User.Id;
      placeholder = "Invoked from message";
  }

  var response = new MessagingExtensionActionResponse()
  {
    Task = new TaskModuleContinueResponse()
    {
      Value = new TaskModuleTaskInfo()
      {
        Height = "small",
        Width = "small",
        Title = "Example task module",
        Url = "https://contoso.com/msteams/taskmodules/newcustomer",
        },
      },
    },
  };
  return response;
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="68d96-278">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="68d96-278">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    return {
      task: {
        type: 'continue',
        value: {
          width: 500,
          height: 450,
          title: 'Task Module Fetch Example',
          url: 'https://contoso.com/msteams/taskmodules/newcustomer',
          fallbackUrl: 'https://contoso.com/msteams/taskmodules/newcustomer'
        }
      }
    };
  }
}
```

# <a name="json"></a>[<span data-ttu-id="68d96-279">JSON</span><span class="sxs-lookup"><span data-stu-id="68d96-279">JSON</span></span>](#tab/json)

```json
{
  "task": {
    "type": "continue",
    "value": {
      "title": "Task module title",
      "height": 500,
      "width": "medium",
      "url": "https://contoso.com/msteams/taskmodules/newcustomer",
      "fallbackUrl": "https://contoso.com/msteams/taskmodules/newcustomer"
    }
  }
}
```

* * *

### <a name="request-to-install-your-conversational-bot"></a><span data-ttu-id="68d96-280">Solicitar a instalação do bot de conversa</span><span class="sxs-lookup"><span data-stu-id="68d96-280">Request to install your conversational bot</span></span>

<span data-ttu-id="68d96-281">Se o aplicativo contiver um bot de conversa, instale o bot na conversa e carregue o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="68d96-281">If the app contains a conversational bot, install the bot in the conversation and then load the task module.</span></span> <span data-ttu-id="68d96-282">O bot é útil para obter contexto adicional para o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="68d96-282">The bot is useful to get additional context for the task module.</span></span> <span data-ttu-id="68d96-283">Um exemplo para esse cenário é buscar a lista para preencher um controle de selador de pessoas ou a lista de canais em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="68d96-283">An example for this scenario is to fetch the roster to populate a people picker control or the list of channels in a team.</span></span>

<span data-ttu-id="68d96-284">Quando a extensão de mensagens receber a invocação, verifique se o bot está instalado no `composeExtension/fetchTask` contexto atual para facilitar o fluxo.</span><span class="sxs-lookup"><span data-stu-id="68d96-284">When the messaging extension receives the `composeExtension/fetchTask` invoke, check if the bot is installed in the current context to facilitate the flow.</span></span> <span data-ttu-id="68d96-285">Por exemplo, verifique o fluxo com uma chamada get roster.</span><span class="sxs-lookup"><span data-stu-id="68d96-285">For example, check the flow with a get roster call.</span></span> <span data-ttu-id="68d96-286">Se o bot não estiver instalado, retorne um Cartão Adaptável com uma ação que solicita que o usuário instale o bot.</span><span class="sxs-lookup"><span data-stu-id="68d96-286">If the bot is not installed, return an Adaptive Card with an action that requests the user to install the bot.</span></span> <span data-ttu-id="68d96-287">O usuário deve ter a permissão para instalar os aplicativos nesse local para verificação.</span><span class="sxs-lookup"><span data-stu-id="68d96-287">The user must have the permission to install the apps in that location for checking.</span></span> <span data-ttu-id="68d96-288">Se a instalação do aplicativo não tiver êxito, o usuário receberá uma mensagem para entrar em contato com o administrador.</span><span class="sxs-lookup"><span data-stu-id="68d96-288">If the app installation is unsuccessful, the user receives a message to contact the administrator.</span></span>

#### <a name="example"></a><span data-ttu-id="68d96-289">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-289">Example</span></span> 

<span data-ttu-id="68d96-290">A seção de código a seguir é um exemplo da resposta:</span><span class="sxs-lookup"><span data-stu-id="68d96-290">The following code section is an example of the response:</span></span>

```json
{
  "type": "AdaptiveCard",
  "body": [
    {
      "type": "TextBlock",
      "text": "Looks like you haven't used Disco in this team/chat"
    }
  ],
  "actions": [
    {
      "type": "Action.Submit",
      "title": "Continue",
      "data": {
        "msteams": {
          "justInTimeInstall": true
        }
      }
    }
  ],
  "version": "1.0"
}
```

<span data-ttu-id="68d96-291">Após a instalação do bot de conversa, ele recebe outra mensagem de invocação `name = composeExtension/submitAction` com e `value.data.msteams.justInTimeInstall = true` .</span><span class="sxs-lookup"><span data-stu-id="68d96-291">After the installation of conversational bot, it receives another invoke message with `name = composeExtension/submitAction`, and `value.data.msteams.justInTimeInstall = true`.</span></span>

#### <a name="example"></a><span data-ttu-id="68d96-292">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-292">Example</span></span> 

<span data-ttu-id="68d96-293">A seção de código a seguir é um exemplo da resposta da tarefa à invocação:</span><span class="sxs-lookup"><span data-stu-id="68d96-293">The following code section is an example of the task response to the invoke:</span></span>

```json
{
  "value": {
    "commandId": "giveKudos",
    "commandContext": "compose",
    "context": {
      "theme": "default"
    },
    "data": {
      "msteams": {
        "justInTimeInstall": true
      }
    }
  },
  "conversation": {
    "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
  },
  "name": "composeExtension/submitAction",
  "imdisplayname": "Bob Smith"
}
```

<span data-ttu-id="68d96-294">A resposta da tarefa à invocação deve ser semelhante à do bot instalado.</span><span class="sxs-lookup"><span data-stu-id="68d96-294">The task response to the invoke must be similar to that of the installed bot.</span></span>

#### <a name="example"></a><span data-ttu-id="68d96-295">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d96-295">Example</span></span> 

<span data-ttu-id="68d96-296">A seção de código a seguir é um exemplo de instalação just-in-time do aplicativo com cartão Adaptável:</span><span class="sxs-lookup"><span data-stu-id="68d96-296">The following code section is an example of just-in time installation of app with Adaptive card:</span></span> 

```csharp
private static Attachment GetAdaptiveCardAttachmentFromFile(string fileName)
  {
      //Read the card json and create attachment.
         string[] paths = { ".", "Resources", fileName };
         var adaptiveCardJson = File.ReadAllText(Path.Combine(paths));
         var adaptiveCardAttachment = new Attachment()
            {
                ContentType = "application/vnd.microsoft.card.adaptive",
                Content = JsonConvert.DeserializeObject(adaptiveCardJson),
            };
            return adaptiveCardAttachment;
        }
```

* * *

## <a name="code-sample"></a><span data-ttu-id="68d96-297">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="68d96-297">Code sample</span></span>

| <span data-ttu-id="68d96-298">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="68d96-298">Sample Name</span></span>           | <span data-ttu-id="68d96-299">Descrição</span><span class="sxs-lookup"><span data-stu-id="68d96-299">Description</span></span> | <span data-ttu-id="68d96-300">.NET</span><span class="sxs-lookup"><span data-stu-id="68d96-300">.NET</span></span>    | <span data-ttu-id="68d96-301">Node.js</span><span class="sxs-lookup"><span data-stu-id="68d96-301">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="68d96-302">Teams ação de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="68d96-302">Teams messaging extension action</span></span>| <span data-ttu-id="68d96-303">Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="68d96-303">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="68d96-304">View</span><span class="sxs-lookup"><span data-stu-id="68d96-304">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="68d96-305">View</span><span class="sxs-lookup"><span data-stu-id="68d96-305">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="68d96-306">Teams de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="68d96-306">Teams messaging extension search</span></span>   |  <span data-ttu-id="68d96-307">Descreve como definir comandos de pesquisa e responder a pesquisas.</span><span class="sxs-lookup"><span data-stu-id="68d96-307">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="68d96-308">View</span><span class="sxs-lookup"><span data-stu-id="68d96-308">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="68d96-309">View</span><span class="sxs-lookup"><span data-stu-id="68d96-309">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="see-also"></a><span data-ttu-id="68d96-310">Confira também</span><span class="sxs-lookup"><span data-stu-id="68d96-310">See also</span></span>

[<span data-ttu-id="68d96-311">Definir comandos de ação</span><span class="sxs-lookup"><span data-stu-id="68d96-311">Define action commands</span></span>](~/messaging-extensions/how-to/action-commands/define-action-command.md)


## <a name="next-step"></a><span data-ttu-id="68d96-312">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="68d96-312">Next step</span></span>

> [!div class="nextstepaction"] 
> [<span data-ttu-id="68d96-313">Responder ao comando de ação</span><span class="sxs-lookup"><span data-stu-id="68d96-313">Respond to action command</span></span>](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

