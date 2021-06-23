---
title: Criar abas para conversação
author: surbhigupta
description: Criar chat de sub entidade conversacional para suas guias de canal
keywords: canal de guias do teams configurável
ms.topic: conceptual
ms.author: lomeybur
ms.openlocfilehash: 343cbe26ded2792489640ae3d86ec94c7c6db72b
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069228"
---
# <a name="create-conversational-tabs"></a><span data-ttu-id="2c088-104">Criar abas para conversação</span><span class="sxs-lookup"><span data-stu-id="2c088-104">Create conversational tabs</span></span>

<span data-ttu-id="2c088-105">As sub-entidades de conversação proporcionam uma maneira de permitir que os usuários tenham conversas sobre sub-entidades em sua guia, como tarefas específicas, paciente e oportunidade de vendas, em vez de discutir a guia inteira, também conhecida como entidade.</span><span class="sxs-lookup"><span data-stu-id="2c088-105">Conversational sub-entities provides a way to allow users to have conversations about sub-entities in your tab, such as specific task, patient, and sales opportunity, instead of discussing the entire tab, also known as entity.</span></span> <span data-ttu-id="2c088-106">Um canal tradicional ou uma guia configurável permite que o usuário tenha uma conversa sobre uma guia, mas o usuário pode querer uma conversa mais focada.</span><span class="sxs-lookup"><span data-stu-id="2c088-106">A traditional channel or configurable tab allows the user to have a conversation about a tab, but the user may want a more focused conversation.</span></span> <span data-ttu-id="2c088-107">O requisito para uma conversa mais focada pode surgir, se houver muito conteúdo para ter uma discussão centralizada ou o conteúdo alterado com o tempo, tornando a conversa irrelevante para o conteúdo que está sendo mostrado.</span><span class="sxs-lookup"><span data-stu-id="2c088-107">The requirement for a more focused conversation can arise either, if there is too much content to have a centralized discussion or the content changed over time, making the conversation irrelevant to the content being shown.</span></span> <span data-ttu-id="2c088-108">As sub-entidades de conversa proporcionam uma experiência de conversa muito mais focada para guias dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="2c088-108">Conversational sub-entities provides a much more focused conversation experience for dynamic tabs.</span></span>

<span data-ttu-id="2c088-109">As sub-entidades de conversa só têm suporte em canais.</span><span class="sxs-lookup"><span data-stu-id="2c088-109">Conversational sub-entities are only supported in channels.</span></span> <span data-ttu-id="2c088-110">No entanto, eles podem ser usados de uma guia pessoal ou estática para criar ou continuar conversas em guias que já *estão* fixadas a um canal.</span><span class="sxs-lookup"><span data-stu-id="2c088-110">However, they can be used from a personal or static tab to create or continue conversations in tabs that are *already* pinned to a channel.</span></span> <span data-ttu-id="2c088-111">A guia estática é útil se você quiser fornecer um local para um usuário exibir e acessar conversas que ocorrem em vários canais.</span><span class="sxs-lookup"><span data-stu-id="2c088-111">The static tab is useful if you wish to provide one location for a user to view and access conversations happening across multiple channels.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2c088-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2c088-112">Prerequisites</span></span>

<span data-ttu-id="2c088-113">Para dar suporte a sub-entidades de conversação, seu aplicativo Web de tabulação deve ter a capacidade de armazenar um mapeamento entre sub-entidades ↔ conversas em um banco de dados back-end.</span><span class="sxs-lookup"><span data-stu-id="2c088-113">In order to support conversational sub-entities, your tab web application must have the ability to store a mapping between sub-entities ↔ conversations in a backend database.</span></span> <span data-ttu-id="2c088-114">Forneceremos o , mas será sua responsabilidade armazená-lo e devolvê-lo Teams para que os usuários `conversationId` `conversationId` continuem a conversa.</span><span class="sxs-lookup"><span data-stu-id="2c088-114">We will provide you with the `conversationId`, but it will be your responsibility to store that `conversationId` and return it to Teams in order for users to continue the conversation.</span></span>

## <a name="start-a-new-conversation"></a><span data-ttu-id="2c088-115">Iniciar uma nova conversa</span><span class="sxs-lookup"><span data-stu-id="2c088-115">Start a new conversation</span></span>

<span data-ttu-id="2c088-116">Para iniciar uma nova conversa, use a `openConversation()` função.</span><span class="sxs-lookup"><span data-stu-id="2c088-116">To start a new conversation, you use the `openConversation()` function.</span></span> <span data-ttu-id="2c088-117">No entanto, iniciar e continuar uma conversa é manipulado por esse método, as entradas para a função mudam dependendo da ação que você deseja tomar.</span><span class="sxs-lookup"><span data-stu-id="2c088-117">Starting and continuing a conversation are all handled by this method, however, the inputs to the function change depending on which action you want to take.</span></span> <span data-ttu-id="2c088-118">Da perspectiva dos usuários, isso abre o painel de conversa à direita da tela, para iniciar uma conversa ou continuar uma conversa.</span><span class="sxs-lookup"><span data-stu-id="2c088-118">From the users perspective, this opens the conversation panel to the right of the screen, either to initiate a conversation or continue a conversation.</span></span>

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

<span data-ttu-id="2c088-119">**OpenConversation** assume as seguintes entradas para iniciar uma conversa em um canal:</span><span class="sxs-lookup"><span data-stu-id="2c088-119">**openConversation** takes the following inputs to start a conversation in a channel:</span></span>

* <span data-ttu-id="2c088-120">**subEntityId**: essa é a ID da sua sub-entidade específica.</span><span class="sxs-lookup"><span data-stu-id="2c088-120">**subEntityId**: This is the ID of your specific sub-entity.</span></span> <span data-ttu-id="2c088-121">Por exemplo, tarefa-123.</span><span class="sxs-lookup"><span data-stu-id="2c088-121">For example, task-123.</span></span>
* <span data-ttu-id="2c088-122">**entityId**: essa é a ID da instância da guia quando ela foi criada.</span><span class="sxs-lookup"><span data-stu-id="2c088-122">**entityId**: This is the ID of the tab instance when it was created.</span></span> <span data-ttu-id="2c088-123">A ID é importante para se referir à mesma instância de tabulação.</span><span class="sxs-lookup"><span data-stu-id="2c088-123">The ID is important to refer back to the same tab instance.</span></span>
* <span data-ttu-id="2c088-124">**channelId**: este é o canal no qual a instância de tabulação reside.</span><span class="sxs-lookup"><span data-stu-id="2c088-124">**channelId**: This is the channel in which the tab instance resides.</span></span>
   > [!NOTE]
   > <span data-ttu-id="2c088-125">O **channelId** é opcional para guias de canal.</span><span class="sxs-lookup"><span data-stu-id="2c088-125">The **channelId** is optional for channel tabs.</span></span> <span data-ttu-id="2c088-126">No entanto, é recomendável que você queira manter sua implementação entre canais e guias estáticas da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="2c088-126">However, it is recommended if you wish to keep your implementation across channel and static tabs the same.</span></span>
* <span data-ttu-id="2c088-127">**title**: Este é o título que é mostrado ao usuário no painel de chat.</span><span class="sxs-lookup"><span data-stu-id="2c088-127">**title**: This is the title that is shown to the user in the chat panel.</span></span>

<span data-ttu-id="2c088-128">A maioria desses valores também pode ser recuperada da `getContext` API.</span><span class="sxs-lookup"><span data-stu-id="2c088-128">Most of these values can also be retrieved from the `getContext` API.</span></span>

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

<span data-ttu-id="2c088-129">Isso abrirá o painel de conversa.</span><span class="sxs-lookup"><span data-stu-id="2c088-129">This will open the conversation panel.</span></span>

![Sub Entidades de Conversação - Iniciar Conversa](~/assets/images/tabs/conversational-subentities/start-conversation.png)

<span data-ttu-id="2c088-131">Se o usuário iniciar uma conversa, é importante ouvir o retorno de chamada desse evento para recuperar e salvar a **conversationId**:</span><span class="sxs-lookup"><span data-stu-id="2c088-131">If the user starts a conversation, it’s important to listen for the callback of that event in order to retrieve and save the **conversationId**:</span></span>

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

<span data-ttu-id="2c088-132">O `conversationReponse` objeto contém informações relacionadas à conversa que acabou de ser iniciada.</span><span class="sxs-lookup"><span data-stu-id="2c088-132">The `conversationReponse` object contains information related to the conversation that was just started.</span></span> <span data-ttu-id="2c088-133">Recomendamos que você salve todas as propriedades deste objeto de resposta para reutilização posteriormente.</span><span class="sxs-lookup"><span data-stu-id="2c088-133">We recommend you save all the properties of this response object for reuse later.</span></span>

## <a name="continue-a-conversation"></a><span data-ttu-id="2c088-134">Continuar uma conversa</span><span class="sxs-lookup"><span data-stu-id="2c088-134">Continue a conversation</span></span>

<span data-ttu-id="2c088-135">Depois que uma conversa é iniciada, as chamadas subsequentes exigem que você também forneça as mesmas entradas como em Iniciar uma nova conversa de guia de canal , mas também incluir `openConversation()` [a](#Starting a new channel tab conversation) **conversationId**.</span><span class="sxs-lookup"><span data-stu-id="2c088-135">After a conversation starts, subsequent calls to `openConversation()` requires that you also provide the same inputs as in [Starting a new channel tab conversation](#Starting a new channel tab conversation), but also include the **conversationId**.</span></span> <span data-ttu-id="2c088-136">O painel de conversa é aberto para o usuário com a conversa apropriada em exibição.</span><span class="sxs-lookup"><span data-stu-id="2c088-136">The conversation panel opens for the user with the appropriate conversation in view.</span></span> <span data-ttu-id="2c088-137">Os usuários podem ver mensagens novas ou de entrada em tempo real.</span><span class="sxs-lookup"><span data-stu-id="2c088-137">Users are able to see new or incoming messages in real-time.</span></span>

![Sub Entidades de Conversação - Continuar Conversa](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## <a name="enhance-a-conversation"></a><span data-ttu-id="2c088-139">Aprimorar uma conversa</span><span class="sxs-lookup"><span data-stu-id="2c088-139">Enhance a conversation</span></span>

<span data-ttu-id="2c088-140">Por fim, é importante que sua guia consuma [deeplinks para sua sub-entidade](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="2c088-140">Finally, it’s important that your tab consumes [deeplinks to your sub-entity](~/concepts/build-and-test/deep-links.md).</span></span> <span data-ttu-id="2c088-141">Por exemplo, o usuário clicando no deeplink da guia da conversa do canal.</span><span class="sxs-lookup"><span data-stu-id="2c088-141">For example, user clicking the tab chiclet deeplink from the channel conversation.</span></span> <span data-ttu-id="2c088-142">O comportamento esperado é que você receba o deeplink, abra essa sub entidade e abra o painel de conversa para essa sub-entidade específica.</span><span class="sxs-lookup"><span data-stu-id="2c088-142">The expected behavior is for you to receive the deeplink, open that sub-entity, and then open the conversation panel for that specific sub-entity.</span></span>

<span data-ttu-id="2c088-143">Para dar suporte a sub-entidades de conversa a partir de sua guia pessoal ou estática, você não precisa alterar nada sobre sua implementação.</span><span class="sxs-lookup"><span data-stu-id="2c088-143">To support conversational sub-entities from your personal or static tab, you do not have to change anything about your implementation.</span></span> <span data-ttu-id="2c088-144">Só há suporte para conversas in-comodas ou contínuas de guias de canal que já estão fixadas.</span><span class="sxs-lookup"><span data-stu-id="2c088-144">We only support starting or continuing conversations from channel tabs that are already pinned.</span></span> <span data-ttu-id="2c088-145">As guias estáticas de suporte permitem que você forneça um único local para que seus usuários interajam com todas as suas sub-entidades.</span><span class="sxs-lookup"><span data-stu-id="2c088-145">Supporting static tabs allow you to provide a single location for your users to interact with all your sub-entities.</span></span> <span data-ttu-id="2c088-146">No entanto, é importante que você salve o , e quando sua guia for originalmente criada em um canal para que você tenha as propriedades certas ao abrir o modo de exibição de conversa em uma guia `subEntityId` `entityId` `channelId` estática.</span><span class="sxs-lookup"><span data-stu-id="2c088-146">It is, however, important that you save the `subEntityId`, `entityId`, and `channelId` when your tab is originally created in a channel in order for you to have the right properties when opening the conversation view in a static tab.</span></span>

## <a name="close-a-conversation"></a><span data-ttu-id="2c088-147">Fechar uma conversa</span><span class="sxs-lookup"><span data-stu-id="2c088-147">Close a conversation</span></span>

<span data-ttu-id="2c088-148">Você pode fechar manualmente o modo de exibição de conversa chamando a `closeConversation()` função.</span><span class="sxs-lookup"><span data-stu-id="2c088-148">You can manually close the conversation view by calling the `closeConversation()` function.</span></span>

```javascript
microsoftTeams.conversations.closeConversation();
```

<span data-ttu-id="2c088-149">Você também pode escutar um evento quando o exibição de conversa é fechado por um usuário.</span><span class="sxs-lookup"><span data-stu-id="2c088-149">You can also listen for an event when the conversation view is closed by a user.</span></span>

```javascript
microsoftTeams.conversations.onCloseConversation = (conversationResponse) => {
    // console.log(conversationResponse)
};
```
