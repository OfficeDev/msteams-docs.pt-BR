---
title: Criar abas para conversação
author: surbhigupta
description: Criar chat de sub entidade conversacional para suas guias de canal
keywords: canal de guias do teams configurável
ms.topic: conceptual
ms.author: lomeybur
ms.openlocfilehash: b563510b9ce232a98572430c76f1b8e59ddb4886
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179689"
---
# <a name="create-conversational-tabs"></a><span data-ttu-id="42740-104">Criar abas para conversação</span><span class="sxs-lookup"><span data-stu-id="42740-104">Create conversational tabs</span></span>

<span data-ttu-id="42740-105">As sub-entidades de conversação proporcionam uma maneira de permitir que os usuários tenham conversas sobre sub-entidades em sua guia, como tarefas específicas, paciente e oportunidade de vendas, em vez de discutir a guia inteira, também conhecida como entidade.</span><span class="sxs-lookup"><span data-stu-id="42740-105">Conversational sub-entities provides a way to allow users to have conversations about sub-entities in your tab, such as specific task, patient, and sales opportunity, instead of discussing the entire tab, also known as entity.</span></span> <span data-ttu-id="42740-106">Um canal tradicional ou uma guia configurável permite que o usuário tenha uma conversa sobre uma guia, mas o usuário exige uma conversa mais focada.</span><span class="sxs-lookup"><span data-stu-id="42740-106">A traditional channel or configurable tab allows the user to have a conversation about a tab, but the user requires a more focused conversation.</span></span> <span data-ttu-id="42740-107">O requisito para uma conversa mais focada pode surgir, se houver muito conteúdo para ter uma discussão centralizada ou porque o conteúdo mudou com o tempo, tornando a conversa irrelevante para o conteúdo que está sendo mostrado.</span><span class="sxs-lookup"><span data-stu-id="42740-107">The requirement for a more focused conversation can arise either, if there is too much content to have a centralized discussion or because the content changed over time, making the conversation irrelevant to the content being shown.</span></span> <span data-ttu-id="42740-108">As sub-entidades de conversa proporcionam uma experiência de conversa muito mais focada para guias dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="42740-108">Conversational sub-entities provides a much more focused conversation experience for dynamic tabs.</span></span>

<span data-ttu-id="42740-109">As sub-entidades de conversa só têm suporte em canais.</span><span class="sxs-lookup"><span data-stu-id="42740-109">Conversational sub-entities are only supported in channels.</span></span> <span data-ttu-id="42740-110">Elas podem ser usadas de uma guia pessoal ou estática para criar ou continuar conversas em guias que já estão fixadas a um canal.</span><span class="sxs-lookup"><span data-stu-id="42740-110">They can be used from a personal or static tab to create or continue conversations in tabs that are already pinned to a channel.</span></span> <span data-ttu-id="42740-111">A guia estática é útil se você quiser fornecer um local para um usuário exibir e acessar conversas que ocorrem em vários canais.</span><span class="sxs-lookup"><span data-stu-id="42740-111">The static tab is useful if you want to provide one location for a user to view and access conversations happening across multiple channels.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="42740-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="42740-112">Prerequisites</span></span>

<span data-ttu-id="42740-113">Para dar suporte a sub-entidades de conversação, seu aplicativo Web de tabulação deve ter a capacidade de armazenar um mapeamento entre sub-entidades ↔ conversas em um banco de dados back-end.</span><span class="sxs-lookup"><span data-stu-id="42740-113">In order to support conversational sub-entities, your tab web application must have the ability to store a mapping between sub-entities ↔ conversations in a backend database.</span></span> <span data-ttu-id="42740-114">O `conversationId` é fornecido, mas você deve armazená-lo e devolvê-lo Teams para que os `conversationId` usuários continuem a conversa.</span><span class="sxs-lookup"><span data-stu-id="42740-114">The `conversationId` is provided, but you must store that `conversationId` and return it to Teams in order for users to continue the conversation.</span></span>

## <a name="start-a-new-conversation"></a><span data-ttu-id="42740-115">Iniciar uma nova conversa</span><span class="sxs-lookup"><span data-stu-id="42740-115">Start a new conversation</span></span>

<span data-ttu-id="42740-116">Para iniciar uma nova conversa, use a `openConversation()` função.</span><span class="sxs-lookup"><span data-stu-id="42740-116">To start a new conversation, use the `openConversation()` function.</span></span> <span data-ttu-id="42740-117">Iniciar e continuar uma conversa são manipulados por esse método.</span><span class="sxs-lookup"><span data-stu-id="42740-117">Starting and continuing a conversation are all handled by this method.</span></span> <span data-ttu-id="42740-118">As entradas para a função mudam dependendo da ação que você deseja tomar.</span><span class="sxs-lookup"><span data-stu-id="42740-118">The inputs to the function change depending on which action you want to take.</span></span> <span data-ttu-id="42740-119">Da perspectiva dos usuários, isso abre o painel de conversa à direita da tela, para iniciar uma conversa ou continuar uma conversa.</span><span class="sxs-lookup"><span data-stu-id="42740-119">From the users perspective, this opens the conversation panel to the right of the screen, either to initiate a conversation or continue a conversation.</span></span>

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

<span data-ttu-id="42740-120">**OpenConversation** assume as seguintes entradas para iniciar uma conversa em um canal:</span><span class="sxs-lookup"><span data-stu-id="42740-120">**openConversation** takes the following inputs to start a conversation in a channel:</span></span>

* <span data-ttu-id="42740-121">**subEntityId**: essa é a ID da sua sub-entidade específica.</span><span class="sxs-lookup"><span data-stu-id="42740-121">**subEntityId**: This is the ID of your specific sub-entity.</span></span> <span data-ttu-id="42740-122">Por exemplo, tarefa-123.</span><span class="sxs-lookup"><span data-stu-id="42740-122">For example, task-123.</span></span>
* <span data-ttu-id="42740-123">**entityId**: essa é a ID da instância da guia quando ela foi criada.</span><span class="sxs-lookup"><span data-stu-id="42740-123">**entityId**: This is the ID of the tab instance when it was created.</span></span> <span data-ttu-id="42740-124">A ID é importante para se referir à mesma instância de tabulação.</span><span class="sxs-lookup"><span data-stu-id="42740-124">The ID is important to refer back to the same tab instance.</span></span>
* <span data-ttu-id="42740-125">**channelId**: este é o canal no qual a instância de tabulação reside.</span><span class="sxs-lookup"><span data-stu-id="42740-125">**channelId**: This is the channel in which the tab instance resides.</span></span>
   > [!NOTE]
   > <span data-ttu-id="42740-126">O **channelId** é opcional para guias de canal.</span><span class="sxs-lookup"><span data-stu-id="42740-126">The **channelId** is optional for channel tabs.</span></span> <span data-ttu-id="42740-127">No entanto, é recomendável se você quiser manter sua implementação entre canais e guias estáticas da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="42740-127">However, it is recommended if you want to keep your implementation across channel and static tabs the same.</span></span>
* <span data-ttu-id="42740-128">**title**: Este é o título que é mostrado ao usuário no painel de chat.</span><span class="sxs-lookup"><span data-stu-id="42740-128">**title**: This is the title that is shown to the user in the chat panel.</span></span>

<span data-ttu-id="42740-129">A maioria desses valores também pode ser recuperada da `getContext` API.</span><span class="sxs-lookup"><span data-stu-id="42740-129">Most of these values can also be retrieved from the `getContext` API.</span></span>

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

<span data-ttu-id="42740-130">A imagem a seguir mostra o painel de conversa:</span><span class="sxs-lookup"><span data-stu-id="42740-130">The following image shows the conversation panel:</span></span>

![Sub-entidades de conversação - iniciar conversa](~/assets/images/tabs/conversational-subentities/start-conversation.png)

<span data-ttu-id="42740-132">Se o usuário iniciar uma conversa, é importante ouvir o retorno de chamada desse evento para recuperar e salvar a **conversationId**:</span><span class="sxs-lookup"><span data-stu-id="42740-132">If the user starts a conversation, it is important to listen for the callback of that event in order to retrieve and save the **conversationId**:</span></span>

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

<span data-ttu-id="42740-133">O `conversationResponse` objeto contém informações relacionadas à conversa que foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="42740-133">The `conversationResponse` object contains information related to the conversation that was started.</span></span> <span data-ttu-id="42740-134">É recomendável que você salve todas as propriedades deste objeto de resposta para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="42740-134">It is recommended that you save all the properties of this response object for later use.</span></span>

## <a name="continue-a-conversation"></a><span data-ttu-id="42740-135">Continuar uma conversa</span><span class="sxs-lookup"><span data-stu-id="42740-135">Continue a conversation</span></span>

<span data-ttu-id="42740-136">Depois que uma conversa é iniciada, as chamadas subsequentes exigem que você também forneça as mesmas entradas que no início de uma nova conversa , mas também inclua `openConversation()` **a conversationId**. [](#start-a-new-conversation)</span><span class="sxs-lookup"><span data-stu-id="42740-136">After a conversation starts, subsequent calls to `openConversation()` requires that you also provide the same inputs as in [start a new conversation](#start-a-new-conversation), but also include the **conversationId**.</span></span> <span data-ttu-id="42740-137">O painel de conversa é aberto para o usuário com a conversa apropriada em exibição.</span><span class="sxs-lookup"><span data-stu-id="42740-137">The conversation panel opens for the user with the appropriate conversation in view.</span></span> <span data-ttu-id="42740-138">Os usuários podem ver mensagens novas ou de entrada em tempo real.</span><span class="sxs-lookup"><span data-stu-id="42740-138">Users are able to see new or incoming messages in real-time.</span></span>

<span data-ttu-id="42740-139">A imagem a seguir mostra o painel de conversa com a conversa apropriada:</span><span class="sxs-lookup"><span data-stu-id="42740-139">The following image shows the conversation panel with the appropriate conversation:</span></span>

![Sub-entidades de conversação - continuar a conversa](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## <a name="enhance-a-conversation"></a><span data-ttu-id="42740-141">Aprimorar uma conversa</span><span class="sxs-lookup"><span data-stu-id="42740-141">Enhance a conversation</span></span>

<span data-ttu-id="42740-142">É importante que sua guia inclua [links profundos para sua sub-entidade](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="42740-142">It is important that your tab includes [deeplinks to your sub-entity](~/concepts/build-and-test/deep-links.md).</span></span> <span data-ttu-id="42740-143">Por exemplo, o usuário selecionando o deeplink de guia da conversa do canal.</span><span class="sxs-lookup"><span data-stu-id="42740-143">For example, user selecting the tab chiclet deeplink from the channel conversation.</span></span> <span data-ttu-id="42740-144">O comportamento esperado é receber o deeplink, abrir essa sub-entidade e, em seguida, abrir o painel de conversa para essa sub-entidade.</span><span class="sxs-lookup"><span data-stu-id="42740-144">The expected behavior is to receive the deeplink, open that sub-entity, and then open the conversation panel for that sub-entity.</span></span>

<span data-ttu-id="42740-145">Para dar suporte a sub-entidades de conversa a partir de sua guia pessoal ou estática, você não precisa alterar nada em sua implementação.</span><span class="sxs-lookup"><span data-stu-id="42740-145">To support conversational sub-entities from your personal or static tab, you do not have to change anything in your implementation.</span></span> <span data-ttu-id="42740-146">Só há suporte para conversas in-comodas ou contínuas de guias de canal que já estão fixadas.</span><span class="sxs-lookup"><span data-stu-id="42740-146">We only support starting or continuing conversations from channel tabs that are already pinned.</span></span> <span data-ttu-id="42740-147">As guias estáticas de suporte permitem que você forneça um único local para que seus usuários interajam com todas as sub-entidades.</span><span class="sxs-lookup"><span data-stu-id="42740-147">Supporting static tabs allows you to provide a single location for your users to interact with all your sub-entities.</span></span> <span data-ttu-id="42740-148">É importante que você salve o , e quando sua guia for originalmente criada em um canal para ter as propriedades certas ao abrir o exibição de conversa em `subEntityId` `entityId` uma guia `channelId` estática.</span><span class="sxs-lookup"><span data-stu-id="42740-148">It is important that you save the `subEntityId`, `entityId`, and `channelId` when your tab is originally created in a channel to have the right properties when opening the conversation view in a static tab.</span></span>

## <a name="close-a-conversation"></a><span data-ttu-id="42740-149">Fechar uma conversa</span><span class="sxs-lookup"><span data-stu-id="42740-149">Close a conversation</span></span>

<span data-ttu-id="42740-150">Você pode fechar manualmente o modo de exibição de conversa chamando a `closeConversation()` função.</span><span class="sxs-lookup"><span data-stu-id="42740-150">You can manually close the conversation view by calling the `closeConversation()` function.</span></span>

```javascript
microsoftTeams.conversations.closeConversation();
```

<span data-ttu-id="42740-151">Você também pode escutar um evento quando o exibição de conversa é fechado por um usuário.</span><span class="sxs-lookup"><span data-stu-id="42740-151">You can also listen for an event when the conversation view is closed by a user.</span></span>

```javascript
microsoftTeams.conversations.onCloseConversation = (conversationResponse) => {
    // console.log(conversationResponse)
};
```

## <a name="see-also"></a><span data-ttu-id="42740-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="42740-152">See also</span></span>

* [<span data-ttu-id="42740-153">Teams guias</span><span class="sxs-lookup"><span data-stu-id="42740-153">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="42740-154">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="42740-154">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="42740-155">Criar um canal ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="42740-155">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="42740-156">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="42740-156">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="42740-157">Criar guias com Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="42740-157">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="next-step"></a><span data-ttu-id="42740-158">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="42740-158">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="42740-159">Alterações na margem da guia</span><span class="sxs-lookup"><span data-stu-id="42740-159">Tab margin changes</span></span>](~/resources/removing-tab-margins.md)