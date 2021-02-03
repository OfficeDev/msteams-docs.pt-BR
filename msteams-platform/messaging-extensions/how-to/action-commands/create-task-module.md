---
title: Criar e enviar o módulo de tarefas
author: clearab
description: Como manipular a ação de invocação inicial e responder com um módulo de tarefa de um comando de extensão de mensagem de ação
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 58fb7e1ff5690b33c2e23f68529f05869afa9016
ms.sourcegitcommit: ce74f821660b1258c72b3c3f71c1cf177e7e92ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2021
ms.locfileid: "50072872"
---
# <a name="create-and-send-the-task-module"></a><span data-ttu-id="6fe46-103">Criar e enviar o módulo de tarefas</span><span class="sxs-lookup"><span data-stu-id="6fe46-103">Create and send the task module</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="6fe46-104">Se você não estiver preenchendo o módulo de tarefa com parâmetros definidos no manifesto do aplicativo, você deve criar o módulo de tarefa para os usuários.</span><span class="sxs-lookup"><span data-stu-id="6fe46-104">If you are not populating the task module with parameters defined in the app manifest, you must create the task module for users.</span></span> <span data-ttu-id="6fe46-105">Use um Cartão Adaptável ou uma exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="6fe46-105">Use either an Adaptive Card or an embedded web view.</span></span>

## <a name="the-initial-invoke-request"></a><span data-ttu-id="6fe46-106">A solicitação de invocação inicial</span><span class="sxs-lookup"><span data-stu-id="6fe46-106">The initial invoke request</span></span>

<span data-ttu-id="6fe46-107">Usando esse método, seu serviço receberá um objeto do tipo e você deverá responder com um objeto contendo o cartão adaptável ou uma URL para o modo de exibição `Activity` `composeExtension/fetchTask` da Web `task` incorporado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-107">Using this method your service will receive an `Activity` object of type `composeExtension/fetchTask`, and you must respond with a `task` object containing either the adaptive card or a URL to the embedded web view.</span></span> <span data-ttu-id="6fe46-108">Juntamente com as propriedades de atividade de bot padrão, a carga de invocação inicial contém os seguintes metadados de solicitação:</span><span class="sxs-lookup"><span data-stu-id="6fe46-108">Along with the standard bot activity properties, the initial invoke payload contains the following request metadata:</span></span>

|<span data-ttu-id="6fe46-109">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="6fe46-109">Property name</span></span>|<span data-ttu-id="6fe46-110">Finalidade</span><span class="sxs-lookup"><span data-stu-id="6fe46-110">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="6fe46-111">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-111">Type of request.</span></span> <span data-ttu-id="6fe46-112">Deve `invoke` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-112">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="6fe46-113">Tipo de comando emitido para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6fe46-113">Type of command that is issued to your service.</span></span> <span data-ttu-id="6fe46-114">Deve `composeExtension/fetchTask` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-114">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="6fe46-115">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-115">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="6fe46-116">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-116">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="6fe46-117">Azure Active Directory object id of the user that sent the request.</span><span class="sxs-lookup"><span data-stu-id="6fe46-117">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="6fe46-118">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6fe46-118">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="6fe46-119">ID do canal (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="6fe46-119">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="6fe46-120">ID da equipe (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="6fe46-120">Team ID (if the request was made in a channel).</span></span> |
|`value.commandId` | <span data-ttu-id="6fe46-121">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-121">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="6fe46-122">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="6fe46-122">The context that triggered the event.</span></span> <span data-ttu-id="6fe46-123">Deve `compose` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-123">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="6fe46-124">O tema do cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="6fe46-124">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="6fe46-125">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="6fe46-125">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-11-chat-are-listed-in-the-following-section"></a><span data-ttu-id="6fe46-126">As propriedades de atividade de carga quando invocado um módulo de tarefa de chat 1:1 são listadas na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="6fe46-126">Payload activity properties when invoked a task module from 1:1 chat are listed in the following section:</span></span>

|<span data-ttu-id="6fe46-127">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="6fe46-127">Property name</span></span>|<span data-ttu-id="6fe46-128">Finalidade</span><span class="sxs-lookup"><span data-stu-id="6fe46-128">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="6fe46-129">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-129">Type of request.</span></span> <span data-ttu-id="6fe46-130">Deve `invoke` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-130">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="6fe46-131">Tipo de comando emitido para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6fe46-131">Type of command that is issued to your service.</span></span> <span data-ttu-id="6fe46-132">Deve `composeExtension/fetchTask` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-132">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="6fe46-133">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-133">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="6fe46-134">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-134">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="6fe46-135">Azure Active Directory object id of the user that sent the request.</span><span class="sxs-lookup"><span data-stu-id="6fe46-135">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="6fe46-136">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6fe46-136">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="6fe46-137">O nome de origem do qual o módulo de tarefa é invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-137">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="6fe46-138">Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta.</span><span class="sxs-lookup"><span data-stu-id="6fe46-138">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="6fe46-139">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-139">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="6fe46-140">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="6fe46-140">The context that triggered the event.</span></span> <span data-ttu-id="6fe46-141">Deve `compose` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-141">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="6fe46-142">O tema do cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="6fe46-142">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="6fe46-143">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="6fe46-143">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-group-chat-are-listed-in-the-following-section"></a><span data-ttu-id="6fe46-144">As propriedades de atividade de carga quando invocado um módulo de tarefa de um chat de grupo são listadas na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="6fe46-144">Payload activity properties when invoked a task module from a group chat are listed in the following section:</span></span>

|<span data-ttu-id="6fe46-145">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="6fe46-145">Property name</span></span>|<span data-ttu-id="6fe46-146">Finalidade</span><span class="sxs-lookup"><span data-stu-id="6fe46-146">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="6fe46-147">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-147">Type of request.</span></span> <span data-ttu-id="6fe46-148">Deve `invoke` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-148">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="6fe46-149">Tipo de comando emitido para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6fe46-149">Type of command that is issued to your service.</span></span> <span data-ttu-id="6fe46-150">Deve `composeExtension/fetchTask` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-150">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="6fe46-151">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-151">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="6fe46-152">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-152">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="6fe46-153">Azure Active Directory object id of the user that sent the request.</span><span class="sxs-lookup"><span data-stu-id="6fe46-153">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="6fe46-154">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6fe46-154">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="6fe46-155">O nome de origem do qual o módulo de tarefa é invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-155">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="6fe46-156">Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta.</span><span class="sxs-lookup"><span data-stu-id="6fe46-156">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="6fe46-157">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-157">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="6fe46-158">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="6fe46-158">The context that triggered the event.</span></span> <span data-ttu-id="6fe46-159">Deve `compose` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-159">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="6fe46-160">O tema do cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="6fe46-160">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="6fe46-161">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="6fe46-161">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-channel-new-post-are-listed-in-the-following-section"></a><span data-ttu-id="6fe46-162">As propriedades de atividade de carga quando invocado um módulo de tarefa de um canal (nova postagem) são listadas na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="6fe46-162">Payload activity properties when invoked a task module from a channel (new post) are listed in the following section:</span></span>

|<span data-ttu-id="6fe46-163">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="6fe46-163">Property name</span></span>|<span data-ttu-id="6fe46-164">Finalidade</span><span class="sxs-lookup"><span data-stu-id="6fe46-164">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="6fe46-165">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-165">Type of request.</span></span> <span data-ttu-id="6fe46-166">Deve `invoke` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-166">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="6fe46-167">Tipo de comando emitido para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6fe46-167">Type of command that is issued to your service.</span></span> <span data-ttu-id="6fe46-168">Deve `composeExtension/fetchTask` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-168">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="6fe46-169">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-169">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="6fe46-170">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-170">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="6fe46-171">Azure Active Directory object id of the user that sent the request.</span><span class="sxs-lookup"><span data-stu-id="6fe46-171">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="6fe46-172">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6fe46-172">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="6fe46-173">ID do canal (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="6fe46-173">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="6fe46-174">ID da equipe (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="6fe46-174">Team ID (if the request was made in a channel).</span></span> |
|`channelData.source.name`| <span data-ttu-id="6fe46-175">O nome de origem do qual o módulo de tarefa é invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-175">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="6fe46-176">Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta.</span><span class="sxs-lookup"><span data-stu-id="6fe46-176">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="6fe46-177">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-177">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="6fe46-178">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="6fe46-178">The context that triggered the event.</span></span> <span data-ttu-id="6fe46-179">Deve `compose` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-179">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="6fe46-180">O tema do cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="6fe46-180">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="6fe46-181">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="6fe46-181">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-channel-reply-to-thread-are-listed-in-the-following-section"></a><span data-ttu-id="6fe46-182">As propriedades de atividade de carga quando invocadas um módulo de tarefa de um canal (responder a thread) estão listadas na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="6fe46-182">Payload activity properties when invoked a task module from a channel (reply to thread) are listed in the following section:</span></span>

|<span data-ttu-id="6fe46-183">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="6fe46-183">Property name</span></span>|<span data-ttu-id="6fe46-184">Finalidade</span><span class="sxs-lookup"><span data-stu-id="6fe46-184">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="6fe46-185">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-185">Type of request.</span></span> <span data-ttu-id="6fe46-186">Deve `invoke` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-186">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="6fe46-187">Tipo de comando emitido para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6fe46-187">Type of command that is issued to your service.</span></span> <span data-ttu-id="6fe46-188">Deve `composeExtension/fetchTask` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-188">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="6fe46-189">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-189">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="6fe46-190">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-190">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="6fe46-191">Azure Active Directory object id of the user that sent the request.</span><span class="sxs-lookup"><span data-stu-id="6fe46-191">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="6fe46-192">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6fe46-192">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="6fe46-193">ID do canal (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="6fe46-193">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="6fe46-194">ID da equipe (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="6fe46-194">Team ID (if the request was made in a channel).</span></span> |
|`channelData.source.name`| <span data-ttu-id="6fe46-195">O nome de origem do qual o módulo de tarefa é invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-195">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="6fe46-196">Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta.</span><span class="sxs-lookup"><span data-stu-id="6fe46-196">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="6fe46-197">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-197">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="6fe46-198">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="6fe46-198">The context that triggered the event.</span></span> <span data-ttu-id="6fe46-199">Deve `compose` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-199">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="6fe46-200">O tema do cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="6fe46-200">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="6fe46-201">Deve ser `default` `contrast` `dark` ou.</span><span class="sxs-lookup"><span data-stu-id="6fe46-201">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-command-box-are-listed-in-the-following-section"></a><span data-ttu-id="6fe46-202">As propriedades de atividade de carga quando invocado um módulo de tarefa de uma caixa de comando são listadas na seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="6fe46-202">Payload activity properties when invoked a task module from a command box are listed in the following section:</span></span>

|<span data-ttu-id="6fe46-203">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="6fe46-203">Property name</span></span>|<span data-ttu-id="6fe46-204">Finalidade</span><span class="sxs-lookup"><span data-stu-id="6fe46-204">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="6fe46-205">Tipo de solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-205">Type of request.</span></span> <span data-ttu-id="6fe46-206">Deve `invoke` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-206">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="6fe46-207">Tipo de comando emitido para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6fe46-207">Type of command that is issued to your service.</span></span> <span data-ttu-id="6fe46-208">Deve `composeExtension/fetchTask` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-208">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="6fe46-209">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-209">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="6fe46-210">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-210">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="6fe46-211">Azure Active Directory object id of the user that sent the request.</span><span class="sxs-lookup"><span data-stu-id="6fe46-211">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="6fe46-212">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6fe46-212">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="6fe46-213">O nome de origem do qual o módulo de tarefa é invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-213">The source name from where task module is invoked.</span></span> |
|`value.commandId` | <span data-ttu-id="6fe46-214">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-214">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="6fe46-215">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="6fe46-215">The context that triggered the event.</span></span> <span data-ttu-id="6fe46-216">Deve `compose` ser.</span><span class="sxs-lookup"><span data-stu-id="6fe46-216">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="6fe46-217">O tema do cliente do usuário, útil para formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="6fe46-217">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="6fe46-218">Deve ser `default` , `contrast` ou `dark` .</span><span class="sxs-lookup"><span data-stu-id="6fe46-218">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="example-fetchtask-request"></a><span data-ttu-id="6fe46-219">Exemplo de solicitação fetchTask</span><span class="sxs-lookup"><span data-stu-id="6fe46-219">Example fetchTask request</span></span>

# <a name="cnet"></a>[<span data-ttu-id="6fe46-220">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="6fe46-220">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle fetch task
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="6fe46-221">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="6fe46-221">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreviewBot extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    //hand fetch task
  }
}
```

# <a name="json"></a>[<span data-ttu-id="6fe46-222">JSON</span><span class="sxs-lookup"><span data-stu-id="6fe46-222">JSON</span></span>](#tab/json)

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

## <a name="initial-invoke-request-from-a-message"></a><span data-ttu-id="6fe46-223">Solicitação de invocação inicial de uma mensagem</span><span class="sxs-lookup"><span data-stu-id="6fe46-223">Initial invoke request from a message</span></span>

<span data-ttu-id="6fe46-224">Quando seu bot é invocado a partir de uma mensagem em vez da área de composição ou da barra de comandos, o objeto na solicitação inicial deve conter os detalhes da mensagem da sua extensão de mensagens é `value` invocada.</span><span class="sxs-lookup"><span data-stu-id="6fe46-224">When your bot is invoked from a message rather than the compose area or the command bar, the `value` object in the initial request must contain the details of the message your messaging extension is invoked from.</span></span> <span data-ttu-id="6fe46-225">Consulte a seção a seguir para ver o exemplo deste objeto.</span><span class="sxs-lookup"><span data-stu-id="6fe46-225">See the following section  for the example of this object .</span></span> <span data-ttu-id="6fe46-226">The `reactions` and `mentions` arrays are optional, and they are not present if there are no reação or mentions in the original message.</span><span class="sxs-lookup"><span data-stu-id="6fe46-226">The `reactions` and `mentions` arrays are optional, and they are not present if there are no reactions or mentions in the original message.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="6fe46-227">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="6fe46-227">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var messageText = action.MessagePayload.Body.Content;
  var fromId = action.MessagePayload.From.User.Id;

  //finish handling the fetchTask
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="6fe46-228">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="6fe46-228">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    const messageText = action.messagePayload.body.content;

    //finish handling the fetchTask
  }
}
```

# <a name="json"></a>[<span data-ttu-id="6fe46-229">JSON</span><span class="sxs-lookup"><span data-stu-id="6fe46-229">JSON</span></span>](#tab/json)

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

## <a name="respond-to-the-fetchtask"></a><span data-ttu-id="6fe46-230">Responder à fetchTask</span><span class="sxs-lookup"><span data-stu-id="6fe46-230">Respond to the fetchTask</span></span>

<span data-ttu-id="6fe46-231">Responda à solicitação de invocação com um objeto que contém um objeto com o cartão adaptável ou a URL da Web ou uma mensagem de cadeia `task` `taskInfo` de caracteres simples.</span><span class="sxs-lookup"><span data-stu-id="6fe46-231">Respond to the invoke request with a `task` object that contains either a `taskInfo` object with the adaptive card or web URL, or a simple string message.</span></span>

|<span data-ttu-id="6fe46-232">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="6fe46-232">Property name</span></span>|<span data-ttu-id="6fe46-233">Finalidade</span><span class="sxs-lookup"><span data-stu-id="6fe46-233">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="6fe46-234">Pode ser `continue` para apresentar um formulário ou para um `message` pop-up simples.</span><span class="sxs-lookup"><span data-stu-id="6fe46-234">Can be either `continue` to present a form, or `message` for a simple popup.</span></span> |
|`value`| <span data-ttu-id="6fe46-235">Um `taskInfo` objeto para um formulário ou um `string` para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="6fe46-235">Either a `taskInfo` object for a form, or a `string` for a message.</span></span> |

<span data-ttu-id="6fe46-236">O esquema do objeto taskInfo é:</span><span class="sxs-lookup"><span data-stu-id="6fe46-236">The schema for the taskInfo object is:</span></span>

|<span data-ttu-id="6fe46-237">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="6fe46-237">Property name</span></span>|<span data-ttu-id="6fe46-238">Finalidade</span><span class="sxs-lookup"><span data-stu-id="6fe46-238">Purpose</span></span>|
|---|---|
|`title`| <span data-ttu-id="6fe46-239">O título do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6fe46-239">The title of the task module.</span></span>|
|`height`| <span data-ttu-id="6fe46-240">Ele deve ser um inteiro (em pixels) ou `small` , `medium` `large` .</span><span class="sxs-lookup"><span data-stu-id="6fe46-240">It must be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`width`| <span data-ttu-id="6fe46-241">Ele deve ser um inteiro (em pixels) ou `small` , `medium` `large` .</span><span class="sxs-lookup"><span data-stu-id="6fe46-241">It must be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`card`| <span data-ttu-id="6fe46-242">O cartão adaptável definindo o formulário (se estiver usando um).</span><span class="sxs-lookup"><span data-stu-id="6fe46-242">The adaptive card defining the form (if using one).</span></span>
|`url`| <span data-ttu-id="6fe46-243">A URL a ser aberta dentro do módulo de tarefa como uma exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="6fe46-243">The URL to be opened inside of the task module as an embedded web view.</span></span>|
|`fallbackUrl`| <span data-ttu-id="6fe46-244">Se um cliente não suportar o recurso de módulo de tarefa, essa URL será aberta em uma guia do navegador.</span><span class="sxs-lookup"><span data-stu-id="6fe46-244">If a client does not support the task module feature, this URL is opened in a browser tab.</span></span> |

### <a name="with-an-adaptive-card"></a><span data-ttu-id="6fe46-245">Com um cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="6fe46-245">With an adaptive card</span></span>

<span data-ttu-id="6fe46-246">Ao usar um cartão adaptável, você deve responder com um `task` objeto com o objeto que contém um cartão `value` adaptável.</span><span class="sxs-lookup"><span data-stu-id="6fe46-246">When using an adaptive card, you must respond with a `task` object with the `value` object containing an adaptive card.</span></span>

#### <a name="example-fetchtask-response-with-an-adaptive-card"></a><span data-ttu-id="6fe46-247">Exemplo de resposta fetchTask com um cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="6fe46-247">Example fetchTask response with an adaptive card</span></span>

# <a name="cnet"></a>[<span data-ttu-id="6fe46-248">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="6fe46-248">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="6fe46-249">Este exemplo usa o [pacote NuGet AdaptiveCards,](https://www.nuget.org/packages/AdaptiveCards) além do SDK do Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="6fe46-249">This sample uses the [AdaptiveCards NuGet package](https://www.nuget.org/packages/AdaptiveCards) in addition to the Bot Framework SDK.</span></span>

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="6fe46-250">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="6fe46-250">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="6fe46-251">JSON</span><span class="sxs-lookup"><span data-stu-id="6fe46-251">JSON</span></span>](#tab/json)

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

### <a name="with-an-embedded-web-view"></a><span data-ttu-id="6fe46-252">Com uma exibição da Web incorporada</span><span class="sxs-lookup"><span data-stu-id="6fe46-252">With an embedded web view</span></span>

<span data-ttu-id="6fe46-253">Ao usar uma exibição da Web incorporada, você deve responder com um objeto com o objeto que contém a URL para o formulário da Web que `task` `value` você gostaria de carregar.</span><span class="sxs-lookup"><span data-stu-id="6fe46-253">When using an embedded web view, you must respond with a `task` object with the `value` object containing the URL to the web form you'd like to load.</span></span> <span data-ttu-id="6fe46-254">Os domínios de qualquer URL que você deseja carregar devem ser incluídos na `validDomains` matriz no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6fe46-254">The domains of any URL you want to load must be included in the `validDomains` array in your app's manifest.</span></span> <span data-ttu-id="6fe46-255">Consulte a [documentação do módulo de tarefas](~/task-modules-and-cards/what-are-task-modules.md) para obter informações completas sobre como criar seu visualização da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="6fe46-255">See the [task module documentation](~/task-modules-and-cards/what-are-task-modules.md) for complete information on building your embedded web view.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="6fe46-256">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="6fe46-256">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="6fe46-257">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="6fe46-257">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="6fe46-258">JSON</span><span class="sxs-lookup"><span data-stu-id="6fe46-258">JSON</span></span>](#tab/json)

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

### <a name="request-to-install-your-conversational-bot"></a><span data-ttu-id="6fe46-259">Solicitar a instalação do bot de conversa</span><span class="sxs-lookup"><span data-stu-id="6fe46-259">Request to install your conversational bot</span></span>

<span data-ttu-id="6fe46-260">Se o aplicativo contiver um bot de conversa, instale o bot na conversa antes de carregar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6fe46-260">If the app contains a conversational bot, install the bot in the conversation before loading the task module.</span></span> <span data-ttu-id="6fe46-261">É útil obter contexto adicional para o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6fe46-261">It is useful to get additional context for the task module.</span></span> <span data-ttu-id="6fe46-262">O exemplo típico para esse cenário é buscar a lista de listas para popular um controle selador de pessoas ou a lista de canais em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="6fe46-262">Typical example for this scenario is to fetch the roster to populate a people picker control or the list of channels in a team.</span></span>

<span data-ttu-id="6fe46-263">Quando a extensão de mensagens receber a invocação, verifique se o bot está instalado no `composeExtension/fetchTask` contexto atual para facilitar o fluxo.</span><span class="sxs-lookup"><span data-stu-id="6fe46-263">When the messaging extension receives the `composeExtension/fetchTask` invoke, check if the bot is installed in the current context to facilitate the flow.</span></span> <span data-ttu-id="6fe46-264">Por exemplo, verifique o fluxo com uma chamada para obter lista de lista.</span><span class="sxs-lookup"><span data-stu-id="6fe46-264">For example, check the flow with a get roster call.</span></span> <span data-ttu-id="6fe46-265">Se o bot não estiver instalado, retorne um Cartão Adaptável com uma ação que solicita que o usuário instale o bot.</span><span class="sxs-lookup"><span data-stu-id="6fe46-265">If the bot is not installed, return an Adaptive Card with an action that requests the user to install the bot.</span></span> <span data-ttu-id="6fe46-266">Veja a ação no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6fe46-266">See the action in the following example.</span></span> <span data-ttu-id="6fe46-267">O usuário deve ter permissão para instalar os aplicativos nesse local para verificação.</span><span class="sxs-lookup"><span data-stu-id="6fe46-267">The user must have permission to install the apps in that location for checking.</span></span> <span data-ttu-id="6fe46-268">Se a instalação do aplicativo não for bem-sucedida, o usuário receberá uma mensagem para entrar em contato com o administrador.</span><span class="sxs-lookup"><span data-stu-id="6fe46-268">If the app installation is unsuccessful, the user receives a message to contact the administrator.</span></span>

#### <a name="example-of-the-response"></a><span data-ttu-id="6fe46-269">Exemplo da resposta:</span><span class="sxs-lookup"><span data-stu-id="6fe46-269">Example of the response:</span></span>

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

<span data-ttu-id="6fe46-270">Após a instalação, o bot recebe outra mensagem de invocação com `name = composeExtension/submitAction` e `value.data.msteams.justInTimeInstall = true` .</span><span class="sxs-lookup"><span data-stu-id="6fe46-270">After the installation, the bot receives another invoke message with `name = composeExtension/submitAction`, and `value.data.msteams.justInTimeInstall = true`.</span></span>

#### <a name="example-of-the-invoke"></a><span data-ttu-id="6fe46-271">Exemplo da invocação:</span><span class="sxs-lookup"><span data-stu-id="6fe46-271">Example of the invoke:</span></span>

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

<span data-ttu-id="6fe46-272">A resposta da tarefa à invocação deve ser semelhante à do bot instalado.</span><span class="sxs-lookup"><span data-stu-id="6fe46-272">The task response to the invoke must be similar to that of the installed bot.</span></span>

#### <a name="example-of-just-in-time-installation-of-app-with-adaptive-card"></a><span data-ttu-id="6fe46-273">Exemplo de instalação just-in time do aplicativo com cartão adaptável:</span><span class="sxs-lookup"><span data-stu-id="6fe46-273">Example of just-in time installation of app with Adaptive card:</span></span> 

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

## <a name="next-steps"></a><span data-ttu-id="6fe46-274">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6fe46-274">Next steps</span></span>

<span data-ttu-id="6fe46-275">Se você permitir que seus usuários enviem uma resposta de volta do módulo de tarefa, deverá manipular a ação de envio.</span><span class="sxs-lookup"><span data-stu-id="6fe46-275">If you allow your users to send a response back from the task module, you must handle the submit action.</span></span>

* [<span data-ttu-id="6fe46-276">Criar e responder com um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="6fe46-276">Create and respond with a task module</span></span>](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
