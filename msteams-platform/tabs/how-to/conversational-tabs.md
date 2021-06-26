---
title: Criar abas para conversação
author: surbhigupta
description: Criar chat de sub entidade conversacional para suas guias de canal
keywords: canal de guias do teams configurável
ms.topic: conceptual
ms.author: lomeybur
ms.openlocfilehash: fbc5e90842c892cfb7e14f845563d7d2ffb397bb
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140261"
---
# <a name="create-conversational-tabs"></a><span data-ttu-id="74c6d-104">Criar abas para conversação</span><span class="sxs-lookup"><span data-stu-id="74c6d-104">Create conversational tabs</span></span>

<span data-ttu-id="74c6d-105">As sub-entidades de conversação proporcionam uma maneira de permitir que os usuários tenham conversas sobre sub-entidades em sua guia, como tarefas específicas, paciente e oportunidade de vendas, em vez de discutir a guia inteira, também conhecida como entidade.</span><span class="sxs-lookup"><span data-stu-id="74c6d-105">Conversational sub-entities provides a way to allow users to have conversations about sub-entities in your tab, such as specific task, patient, and sales opportunity, instead of discussing the entire tab, also known as entity.</span></span> <span data-ttu-id="74c6d-106">Um canal tradicional ou uma guia configurável permite que o usuário tenha uma conversa sobre uma guia, mas o usuário exige uma conversa mais focada.</span><span class="sxs-lookup"><span data-stu-id="74c6d-106">A traditional channel or configurable tab allows the user to have a conversation about a tab, but the user requires a more focused conversation.</span></span> <span data-ttu-id="74c6d-107">O requisito para uma conversa mais focada pode surgir, se houver muito conteúdo para ter uma discussão centralizada ou porque o conteúdo mudou com o tempo, tornando a conversa irrelevante para o conteúdo que está sendo mostrado.</span><span class="sxs-lookup"><span data-stu-id="74c6d-107">The requirement for a more focused conversation can arise either, if there is too much content to have a centralized discussion or because the content changed over time, making the conversation irrelevant to the content being shown.</span></span> <span data-ttu-id="74c6d-108">As sub-entidades de conversa proporcionam uma experiência de conversa muito mais focada para guias dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="74c6d-108">Conversational sub-entities provides a much more focused conversation experience for dynamic tabs.</span></span>

<span data-ttu-id="74c6d-109">As sub-entidades de conversa só têm suporte em canais.</span><span class="sxs-lookup"><span data-stu-id="74c6d-109">Conversational sub-entities are only supported in channels.</span></span> <span data-ttu-id="74c6d-110">Elas podem ser usadas de uma guia pessoal ou estática para criar ou continuar conversas em guias que já estão fixadas a um canal.</span><span class="sxs-lookup"><span data-stu-id="74c6d-110">They can be used from a personal or static tab to create or continue conversations in tabs that are already pinned to a channel.</span></span> <span data-ttu-id="74c6d-111">A guia estática é útil se você quiser fornecer um local para um usuário exibir e acessar conversas que ocorrem em vários canais.</span><span class="sxs-lookup"><span data-stu-id="74c6d-111">The static tab is useful if you want to provide one location for a user to view and access conversations happening across multiple channels.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74c6d-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="74c6d-112">Prerequisites</span></span>

<span data-ttu-id="74c6d-113">Para dar suporte a sub-entidades de conversação, seu aplicativo Web de tabulação deve ter a capacidade de armazenar um mapeamento entre sub-entidades ↔ conversas em um banco de dados back-end.</span><span class="sxs-lookup"><span data-stu-id="74c6d-113">In order to support conversational sub-entities, your tab web application must have the ability to store a mapping between sub-entities ↔ conversations in a backend database.</span></span> <span data-ttu-id="74c6d-114">O `conversationId` é fornecido, mas você deve armazená-lo e devolvê-lo Teams para que os `conversationId` usuários continuem a conversa.</span><span class="sxs-lookup"><span data-stu-id="74c6d-114">The `conversationId` is provided, but you must store that `conversationId` and return it to Teams in order for users to continue the conversation.</span></span>

## <a name="start-a-new-conversation"></a><span data-ttu-id="74c6d-115">Iniciar uma nova conversa</span><span class="sxs-lookup"><span data-stu-id="74c6d-115">Start a new conversation</span></span>

<span data-ttu-id="74c6d-116">Para iniciar uma nova conversa, use a `openConversation()` função.</span><span class="sxs-lookup"><span data-stu-id="74c6d-116">To start a new conversation, use the `openConversation()` function.</span></span> <span data-ttu-id="74c6d-117">Iniciar e continuar uma conversa são manipulados por esse método.</span><span class="sxs-lookup"><span data-stu-id="74c6d-117">Starting and continuing a conversation are all handled by this method.</span></span> <span data-ttu-id="74c6d-118">As entradas para a função mudam dependendo da ação que você deseja tomar.</span><span class="sxs-lookup"><span data-stu-id="74c6d-118">The inputs to the function change depending on which action you want to take.</span></span> <span data-ttu-id="74c6d-119">Da perspectiva dos usuários, isso abre o painel de conversa à direita da tela, para iniciar uma conversa ou continuar uma conversa.</span><span class="sxs-lookup"><span data-stu-id="74c6d-119">From the users perspective, this opens the conversation panel to the right of the screen, either to initiate a conversation or continue a conversation.</span></span>

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

<span data-ttu-id="74c6d-120">**OpenConversation** assume as seguintes entradas para iniciar uma conversa em um canal:</span><span class="sxs-lookup"><span data-stu-id="74c6d-120">**openConversation** takes the following inputs to start a conversation in a channel:</span></span>

* <span data-ttu-id="74c6d-121">**subEntityId**: essa é a ID da sua sub-entidade específica.</span><span class="sxs-lookup"><span data-stu-id="74c6d-121">**subEntityId**: This is the ID of your specific sub-entity.</span></span> <span data-ttu-id="74c6d-122">Por exemplo, tarefa-123.</span><span class="sxs-lookup"><span data-stu-id="74c6d-122">For example, task-123.</span></span>
* <span data-ttu-id="74c6d-123">**entityId**: essa é a ID da instância da guia quando ela foi criada.</span><span class="sxs-lookup"><span data-stu-id="74c6d-123">**entityId**: This is the ID of the tab instance when it was created.</span></span> <span data-ttu-id="74c6d-124">A ID é importante para se referir à mesma instância de tabulação.</span><span class="sxs-lookup"><span data-stu-id="74c6d-124">The ID is important to refer back to the same tab instance.</span></span>
* <span data-ttu-id="74c6d-125">**channelId**: este é o canal no qual a instância de tabulação reside.</span><span class="sxs-lookup"><span data-stu-id="74c6d-125">**channelId**: This is the channel in which the tab instance resides.</span></span>
   > [!NOTE]
   > <span data-ttu-id="74c6d-126">O **channelId** é opcional para guias de canal.</span><span class="sxs-lookup"><span data-stu-id="74c6d-126">The **channelId** is optional for channel tabs.</span></span> <span data-ttu-id="74c6d-127">No entanto, é recomendável se você quiser manter sua implementação entre canais e guias estáticas da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="74c6d-127">However, it is recommended if you want to keep your implementation across channel and static tabs the same.</span></span>
* <span data-ttu-id="74c6d-128">**title**: Este é o título que é mostrado ao usuário no painel de chat.</span><span class="sxs-lookup"><span data-stu-id="74c6d-128">**title**: This is the title that is shown to the user in the chat panel.</span></span>

<span data-ttu-id="74c6d-129">A maioria desses valores também pode ser recuperada da `getContext` API.</span><span class="sxs-lookup"><span data-stu-id="74c6d-129">Most of these values can also be retrieved from the `getContext` API.</span></span>

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

<span data-ttu-id="74c6d-130">A imagem a seguir mostra o painel de conversa:</span><span class="sxs-lookup"><span data-stu-id="74c6d-130">The following image shows the conversation panel:</span></span>

![Sub-entidades de conversação - iniciar conversa](~/assets/images/tabs/conversational-subentities/start-conversation.png)

<span data-ttu-id="74c6d-132">Se o usuário iniciar uma conversa, é importante ouvir o retorno de chamada desse evento para recuperar e salvar a **conversationId**:</span><span class="sxs-lookup"><span data-stu-id="74c6d-132">If the user starts a conversation, it is important to listen for the callback of that event in order to retrieve and save the **conversationId**:</span></span>

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

<span data-ttu-id="74c6d-133">O `conversationResponse` objeto contém informações relacionadas à conversa que foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="74c6d-133">The `conversationResponse` object contains information related to the conversation that was started.</span></span> <span data-ttu-id="74c6d-134">É recomendável que você salve todas as propriedades deste objeto de resposta para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="74c6d-134">It is recommended that you save all the properties of this response object for later use.</span></span>

## <a name="continue-a-conversation"></a><span data-ttu-id="74c6d-135">Continuar uma conversa</span><span class="sxs-lookup"><span data-stu-id="74c6d-135">Continue a conversation</span></span>

<span data-ttu-id="74c6d-136">Depois que uma conversa é iniciada, as chamadas subsequentes exigem que você também forneça as mesmas entradas que no início de uma nova conversa , mas também inclua `openConversation()` **a conversationId**. [](#start-a-new-conversation)</span><span class="sxs-lookup"><span data-stu-id="74c6d-136">After a conversation starts, subsequent calls to `openConversation()` requires that you also provide the same inputs as in [start a new conversation](#start-a-new-conversation), but also include the **conversationId**.</span></span> <span data-ttu-id="74c6d-137">O painel de conversa é aberto para o usuário com a conversa apropriada em exibição.</span><span class="sxs-lookup"><span data-stu-id="74c6d-137">The conversation panel opens for the user with the appropriate conversation in view.</span></span> <span data-ttu-id="74c6d-138">Os usuários podem ver mensagens novas ou de entrada em tempo real.</span><span class="sxs-lookup"><span data-stu-id="74c6d-138">Users are able to see new or incoming messages in real-time.</span></span>

<span data-ttu-id="74c6d-139">A imagem a seguir mostra o painel de conversa com a conversa apropriada:</span><span class="sxs-lookup"><span data-stu-id="74c6d-139">The following image shows the conversation panel with the appropriate conversation:</span></span>

![Sub-entidades de conversação - continuar a conversa](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## <a name="enhance-a-conversation"></a><span data-ttu-id="74c6d-141">Aprimorar uma conversa</span><span class="sxs-lookup"><span data-stu-id="74c6d-141">Enhance a conversation</span></span>

<span data-ttu-id="74c6d-142">É importante que sua guia inclua [links profundos para sua sub-entidade](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="74c6d-142">It is important that your tab includes [deeplinks to your sub-entity](~/concepts/build-and-test/deep-links.md).</span></span> <span data-ttu-id="74c6d-143">Por exemplo, o usuário selecionando o deeplink de guia da conversa do canal.</span><span class="sxs-lookup"><span data-stu-id="74c6d-143">For example, user selecting the tab chiclet deeplink from the channel conversation.</span></span> <span data-ttu-id="74c6d-144">O comportamento esperado é receber o deeplink, abrir essa sub-entidade e, em seguida, abrir o painel de conversa para essa sub-entidade.</span><span class="sxs-lookup"><span data-stu-id="74c6d-144">The expected behavior is to receive the deeplink, open that sub-entity, and then open the conversation panel for that sub-entity.</span></span>

<span data-ttu-id="74c6d-145">Para dar suporte a sub-entidades de conversa a partir de sua guia pessoal ou estática, você não precisa alterar nada em sua implementação.</span><span class="sxs-lookup"><span data-stu-id="74c6d-145">To support conversational sub-entities from your personal or static tab, you do not have to change anything in your implementation.</span></span> <span data-ttu-id="74c6d-146">Só há suporte para conversas in-comodas ou contínuas de guias de canal que já estão fixadas.</span><span class="sxs-lookup"><span data-stu-id="74c6d-146">We only support starting or continuing conversations from channel tabs that are already pinned.</span></span> <span data-ttu-id="74c6d-147">As guias estáticas de suporte permitem que você forneça um único local para que seus usuários interajam com todas as sub-entidades.</span><span class="sxs-lookup"><span data-stu-id="74c6d-147">Supporting static tabs allows you to provide a single location for your users to interact with all your sub-entities.</span></span> <span data-ttu-id="74c6d-148">É importante que você salve o , e quando sua guia for originalmente criada em um canal para ter as propriedades certas ao abrir o exibição de conversa em `subEntityId` `entityId` uma guia `channelId` estática.</span><span class="sxs-lookup"><span data-stu-id="74c6d-148">It is important that you save the `subEntityId`, `entityId`, and `channelId` when your tab is originally created in a channel to have the right properties when opening the conversation view in a static tab.</span></span>

## <a name="close-a-conversation"></a><span data-ttu-id="74c6d-149">Fechar uma conversa</span><span class="sxs-lookup"><span data-stu-id="74c6d-149">Close a conversation</span></span>

<span data-ttu-id="74c6d-150">Você pode fechar manualmente o modo de exibição de conversa chamando a `closeConversation()` função.</span><span class="sxs-lookup"><span data-stu-id="74c6d-150">You can manually close the conversation view by calling the `closeConversation()` function.</span></span>

```javascript
microsoftTeams.conversations.closeConversation();
```

<span data-ttu-id="74c6d-151">Você também pode escutar um evento quando o exibição de conversa é fechado por um usuário.</span><span class="sxs-lookup"><span data-stu-id="74c6d-151">You can also listen for an event when the conversation view is closed by a user.</span></span>

```javascript
microsoftTeams.conversations.onCloseConversation = (conversationResponse) => {
    // console.log(conversationResponse)
};
```

## <a name="see-also"></a><span data-ttu-id="74c6d-152">Também consulte</span><span class="sxs-lookup"><span data-stu-id="74c6d-152">See also</span></span>

* [<span data-ttu-id="74c6d-153">Teams guias</span><span class="sxs-lookup"><span data-stu-id="74c6d-153">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="74c6d-154">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="74c6d-154">Prerequisites</span></span>](~/tabs/how-to/tab-requirements.md)
* [<span data-ttu-id="74c6d-155">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="74c6d-155">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="74c6d-156">Criar um canal ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="74c6d-156">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="74c6d-157">Criar uma página de conteúdo</span><span class="sxs-lookup"><span data-stu-id="74c6d-157">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
* [<span data-ttu-id="74c6d-158">Criar uma página de configuração</span><span class="sxs-lookup"><span data-stu-id="74c6d-158">Create a configuration page</span></span>](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [<span data-ttu-id="74c6d-159">Criar uma página de remoção para sua guia</span><span class="sxs-lookup"><span data-stu-id="74c6d-159">Create a removal page for your tab</span></span>](~/tabs/how-to/create-tab-pages/removal-page.md)
* [<span data-ttu-id="74c6d-160">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="74c6d-160">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="74c6d-161">Obtenha contexto para sua guia</span><span class="sxs-lookup"><span data-stu-id="74c6d-161">Get context for your tab</span></span>](~/tabs/how-to/access-teams-context.md)
* [<span data-ttu-id="74c6d-162">Criar guias com Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="74c6d-162">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)
* [<span data-ttu-id="74c6d-163">Link de guias desdobradas e Exibição de Estágio</span><span class="sxs-lookup"><span data-stu-id="74c6d-163">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)

## <a name="next-step"></a><span data-ttu-id="74c6d-164">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="74c6d-164">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="74c6d-165">Alterações na margem da guia</span><span class="sxs-lookup"><span data-stu-id="74c6d-165">Tab margin changes</span></span>](~/resources/removing-tab-margins.md)