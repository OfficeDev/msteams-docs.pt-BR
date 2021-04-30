---
title: Visão geral das ações universais para cartões adaptáveis
description: Uma visão geral rápida das Ações Universais para Cartões Adaptáveis.
ms.topic: overview
localization_priority: Normal
ms.openlocfilehash: f0adf3d1a01262ff9cbdf14128c9ffe088ae8072
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088830"
---
# <a name="universal-actions-for-adaptive-cards"></a><span data-ttu-id="3c907-103">Ações universais para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3c907-103">Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="3c907-104">As Ações Universais para Cartões Adaptáveis evoluíram dos comentários do desenvolvedor que, embora o layout e a renderização para Cartões Adaptáveis fosse universais, o tratamento de ações não era.</span><span class="sxs-lookup"><span data-stu-id="3c907-104">Universal Actions for Adaptive Cards evolved from developer feedback that even though layout and rendering for Adaptive Cards was universal, action handling was not.</span></span> <span data-ttu-id="3c907-105">Mesmo que um desenvolvedor quisesse enviar o mesmo cartão para locais diferentes, ele teria que lidar com ações de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="3c907-105">Even if a developer wanted to send the same card to different places, they have to handle actions differently.</span></span>

<span data-ttu-id="3c907-106">Ações universais para Cartões Adaptáveis traz o bot como o back-back comum para lidar com ações e introduz um novo tipo de ação, que funciona em aplicativos, como Teams e `Action.Execute` Outlook.</span><span class="sxs-lookup"><span data-stu-id="3c907-106">Universal Actions for Adaptive Cards brings the bot as the common backend for handling actions and introduces a new action type, `Action.Execute`, which works across apps, such as Teams and Outlook.</span></span>

<span data-ttu-id="3c907-107">Este documento ajuda você a entender como você pode usar o modelo de Ações Universais para aprimorar a experiência do usuário de interagir com Cartões Adaptáveis em plataformas e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3c907-107">This document helps you to understand how you can use Universal Actions model to enhance user experience of interacting with Adaptive Cards across platforms and applications.</span></span>

> [!NOTE]
> <span data-ttu-id="3c907-108">O suporte para Ações Universais para Cartões Adaptáveis só está disponível para cartões enviados por bot.</span><span class="sxs-lookup"><span data-stu-id="3c907-108">Support for Universal Actions for Adaptive Cards is only available for cards sent by bot.</span></span> <span data-ttu-id="3c907-109">O suporte para cartões enviados por meio da caixa de redação e dos cartões de desfraldamento de link está chegando em breve.</span><span class="sxs-lookup"><span data-stu-id="3c907-109">Support for cards sent through compose box and link unfurling cards is coming soon.</span></span>

## <a name="enhance-user-experiences-with-universal-actions-for-adaptive-cards"></a><span data-ttu-id="3c907-110">Aprimorar as experiências do usuário com ações universais para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3c907-110">Enhance user experiences with Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="3c907-111">Ações universais para cartões adaptáveis aprimora a experiência do usuário habilitando os seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="3c907-111">Universal Actions for Adaptive Cards enhances user experience by enabling the following scenarios:</span></span>

* [<span data-ttu-id="3c907-112">Ações universais</span><span class="sxs-lookup"><span data-stu-id="3c907-112">Universal Actions</span></span>](#universal-actions)
* [<span data-ttu-id="3c907-113">Exibições específicas do usuário</span><span class="sxs-lookup"><span data-stu-id="3c907-113">User Specific Views</span></span>](#user-specific-views)
* [<span data-ttu-id="3c907-114">Suporte ao Fluxo de Trabalho Sequencial</span><span class="sxs-lookup"><span data-stu-id="3c907-114">Sequential Workflow support</span></span>](#sequential-workflow-support)
* [<span data-ttu-id="3c907-115">Exibições atualizadas</span><span class="sxs-lookup"><span data-stu-id="3c907-115">Up to date views</span></span>](#up-to-date-views)

### <a name="universal-actions"></a><span data-ttu-id="3c907-116">Ações universais</span><span class="sxs-lookup"><span data-stu-id="3c907-116">Universal Actions</span></span>

<span data-ttu-id="3c907-117">Antes das Ações Universais para Cartões Adaptáveis, hosts diferentes forneceam modelos de ação diferentes da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3c907-117">Before the Universal Actions for Adaptive Cards, different hosts provided different action models as follows:</span></span>

* <span data-ttu-id="3c907-118">Teams ou bots usados , uma abordagem que adia o modelo de comunicação `Action.Submit` real para o canal subjacente.</span><span class="sxs-lookup"><span data-stu-id="3c907-118">Teams or bots used `Action.Submit`, an approach which defers the actual communication model to the underlying channel.</span></span>
* <span data-ttu-id="3c907-119">Outlook usado `Action.Http` para se comunicar com o serviço back-end explicitamente especificado na carga cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="3c907-119">Outlook used `Action.Http` to communicate with the backend service explicitly specified in the Adaptive Card payload.</span></span>

<span data-ttu-id="3c907-120">A imagem a seguir mostra o modelo de ação inconsistente atual:</span><span class="sxs-lookup"><span data-stu-id="3c907-120">The following image shows the current inconsistent action model:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/current-teams-outlook-action-model.png" alt-text="Modelo de ação inconsistente":::

<span data-ttu-id="3c907-122">Com as Ações Universais para Cartões Adaptáveis, você pode usar para o tratamento `Action.Execute` de ações em diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="3c907-122">With the Universal Actions for Adaptive Cards, you can use `Action.Execute` for action handling across different platforms.</span></span> <span data-ttu-id="3c907-123">`Action.Execute`funciona entre hubs, incluindo Teams e Outlook.</span><span class="sxs-lookup"><span data-stu-id="3c907-123">`Action.Execute` works across hubs including Teams and Outlook.</span></span> <span data-ttu-id="3c907-124">Além disso, um Cartão Adaptável pode ser retornado como resposta para uma `Action.Execute` solicitação de invocação disparada.</span><span class="sxs-lookup"><span data-stu-id="3c907-124">In addition, an Adaptive Card can be returned as response for an `Action.Execute` triggered invoke request.</span></span>

<span data-ttu-id="3c907-125">A imagem a seguir mostra o novo modelo de Ação Universal:</span><span class="sxs-lookup"><span data-stu-id="3c907-125">The following image shows the new Universal Action model:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-action-model.png" alt-text="Novas ações universais para cartões adaptáveis":::

<span data-ttu-id="3c907-127">Agora você pode enviar o mesmo cartão para ambos, Teams e Outlook e mantê-los em sincronia uns com os outros usando o bot subjacente.</span><span class="sxs-lookup"><span data-stu-id="3c907-127">You can now send the same card to both, Teams and Outlook, and keep them in sync with each other using the underlying bot.</span></span> <span data-ttu-id="3c907-128">Qualquer ação realizada em qualquer plataforma é refletida na outra com essa com build uma *vez, implante* em qualquer lugar (Ações Universais para Cartões Adaptáveis).</span><span class="sxs-lookup"><span data-stu-id="3c907-128">Any action taken on either platform is reflected to the other with this *build once, deploy anywhere* (Universal Actions for Adaptive Cards) model.</span></span>

<span data-ttu-id="3c907-129">A imagem a seguir mostra as Ações Universais para Cartões Adaptáveis para Teams e Outlook:</span><span class="sxs-lookup"><span data-stu-id="3c907-129">The following image depicts the Universal Actions for Adaptive Cards for both Teams and Outlook:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-teams-outlook.png" alt-text="Mesmo cartão para Teams e Outlook":::

### <a name="user-specific-views"></a><span data-ttu-id="3c907-131">Exibições específicas do usuário</span><span class="sxs-lookup"><span data-stu-id="3c907-131">User Specific Views</span></span>

<span data-ttu-id="3c907-132">Hoje, todos os usuários no Teams chat ou canal veem exatamente as mesmas ações de modo de exibição e botão no Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="3c907-132">Today every user in the Teams chat or channel sees the exact same view and button actions on the Adaptive Card.</span></span> <span data-ttu-id="3c907-133">No entanto, em determinados cenários, há um requisito para que determinados usuários atuem de forma diferente e tenham acesso a informações diferentes no mesmo chat ou canal.</span><span class="sxs-lookup"><span data-stu-id="3c907-133">However, in certain scenarios there is a requirement for certain users to act differently and have access to different information within the same chat or channel.</span></span>

<span data-ttu-id="3c907-134">Por exemplo, se você enviar um cartão de relatório de incidentes em um chat ou canal, somente o usuário atribuído ao incidente deverá ver um **botão Resolver.**</span><span class="sxs-lookup"><span data-stu-id="3c907-134">For example, if you send an incident reporting card in a chat or channel, only the user who is assigned the incident must see a **Resolve** button.</span></span> <span data-ttu-id="3c907-135">Por outro lado, o criador de incidentes deve ver um botão **Editar** e todos os outros usuários só poderão exibir detalhes do incidente.</span><span class="sxs-lookup"><span data-stu-id="3c907-135">On the other hand, the incident creator must see an **Edit** button and all other users must only be able to view details of the incident.</span></span> <span data-ttu-id="3c907-136">Isso é possível por exibições específicas do usuário que estão habilitadas pela `refresh` propriedade.</span><span class="sxs-lookup"><span data-stu-id="3c907-136">This is made possible by User Specific Views that is enabled by the `refresh` property.</span></span>

<span data-ttu-id="3c907-137">A imagem a seguir mostra um exemplo de uma extensão de mensagens de tíquete (ME) onde diferentes usuários no chat são mostrados diferentes ações com base no requisito:</span><span class="sxs-lookup"><span data-stu-id="3c907-137">The following image shows an example of a ticketing messaging extension (ME) where different users in the chat are shown different actions based on the requirement:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Exibições específicas do usuário":::

<span data-ttu-id="3c907-139">Para obter mais informações, consulte [sample for User Specific Views](User-Specific-Views.md).</span><span class="sxs-lookup"><span data-stu-id="3c907-139">For more information, see [sample for User Specific Views](User-Specific-Views.md).</span></span>

### <a name="sequential-workflow-support"></a><span data-ttu-id="3c907-140">Suporte ao Fluxo de Trabalho Sequencial</span><span class="sxs-lookup"><span data-stu-id="3c907-140">Sequential Workflow support</span></span>

<span data-ttu-id="3c907-141">Com o suporte ao Fluxo de Trabalho Sequencial, os usuários podem progredir através de uma série de fluxos de trabalho sem enviar cartões diferentes separadamente.</span><span class="sxs-lookup"><span data-stu-id="3c907-141">With Sequential Workflow support, users can progress through a series of workflows without sending different cards separately.</span></span> <span data-ttu-id="3c907-142">Isso é possível pela capacidade de `Action.Execute` retornar um Cartão Adaptável em resposta a uma ação.</span><span class="sxs-lookup"><span data-stu-id="3c907-142">This is made possible by the ability of `Action.Execute` to return an Adaptive Card in response to an action.</span></span> <span data-ttu-id="3c907-143">Além disso, qualquer usuário no chat ou canal pode progredir por meio de seu fluxo de trabalho sem modificar o cartão para outros usuários no chat.</span><span class="sxs-lookup"><span data-stu-id="3c907-143">Also, any user in the chat or channel can progress through their workflow without modifying the card for other users in the chat.</span></span>

<span data-ttu-id="3c907-144">A imagem a seguir ilustra um exemplo de bot de ordenação de alimentos:</span><span class="sxs-lookup"><span data-stu-id="3c907-144">The following image illustrates a food ordering bot example:</span></span> <br/>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

<span data-ttu-id="3c907-145">A imagem a seguir mostra os vários estados para diferentes usuários no chat ou no canal:</span><span class="sxs-lookup"><span data-stu-id="3c907-145">The following image shows the various states for different users in the chat or channel:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Estados de bot de bufê":::

<span data-ttu-id="3c907-147">Para obter mais informações, consulte [sample for Sequential Workflow](Sequential-Workflows.md).</span><span class="sxs-lookup"><span data-stu-id="3c907-147">For more information, see [sample for Sequential Workflow](Sequential-Workflows.md).</span></span>

### <a name="up-to-date-views"></a><span data-ttu-id="3c907-148">Exibições atualizadas</span><span class="sxs-lookup"><span data-stu-id="3c907-148">Up to date views</span></span>

<span data-ttu-id="3c907-149">Você pode criar Cartões Adaptáveis que são atualizados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3c907-149">You can create Adaptive Cards that update automatically.</span></span> <span data-ttu-id="3c907-150">Por exemplo, pode ser uma solicitação de aprovação enviada por um usuário.</span><span class="sxs-lookup"><span data-stu-id="3c907-150">For example, it can be an approval request sent by a user.</span></span> <span data-ttu-id="3c907-151">Após a aprovação, o cartão deve exibir automaticamente detalhes sobre o tempo de aprovação da solicitação e quem aprovou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="3c907-151">After approval, the card must automatically display details about the request approval time and who approved the request.</span></span> <span data-ttu-id="3c907-152">O modelo de atualização permite que você forneça tais exibições atualizadas.</span><span class="sxs-lookup"><span data-stu-id="3c907-152">The refresh model enables you to provide such up to date views.</span></span> <span data-ttu-id="3c907-153">A imagem a seguir mostra um fluxo de aprovação em várias etapas e como as exibições para diferentes usuários são mostradas.</span><span class="sxs-lookup"><span data-stu-id="3c907-153">The following image shows a multi-step approval flow and how the views for different users is shown.</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views.png" alt-text="Exibições específicas do usuário atualizadas":::

<span data-ttu-id="3c907-155">Para obter mais informações, consulte [exemplo de exibições atualizadas](Up-To-Date-Views.md).</span><span class="sxs-lookup"><span data-stu-id="3c907-155">For more information, see [sample for up to date views](Up-To-Date-Views.md).</span></span>

<span data-ttu-id="3c907-156">Agora, você pode entender como os Cartões Adaptáveis podem ser transformados com o novo modelo de Ações Universais para oferecer uma experiência de usuário exclusiva e aprimorada.</span><span class="sxs-lookup"><span data-stu-id="3c907-156">Now, you can understand how Adaptive Cards can be transformed with the new Universal Actions model to provide a unique and enhanced user experience.</span></span>

## <a name="adaptive-cards-and-the-new-universal-actions-model"></a><span data-ttu-id="3c907-157">Cartões adaptáveis e o novo modelo de Ações Universais</span><span class="sxs-lookup"><span data-stu-id="3c907-157">Adaptive Cards and the new Universal Actions model</span></span>

<span data-ttu-id="3c907-158">Cartões adaptáveis são uma combinação de conteúdo, como texto e elementos gráficos, e ações que podem ser executadas por um usuário.</span><span class="sxs-lookup"><span data-stu-id="3c907-158">Adaptive Cards are a combination of content, such as text and graphics, and actions that can be performed by a user.</span></span> <span data-ttu-id="3c907-159">Para obter mais informações, consulte [Adaptive Cards](http://adaptivecards.io/).</span><span class="sxs-lookup"><span data-stu-id="3c907-159">For more information, see [Adaptive Cards](http://adaptivecards.io/).</span></span> <span data-ttu-id="3c907-160">As novas Ações Universais para Cartões Adaptáveis permitem uma manipulação comum das ações do Cartão Adaptável em plataformas e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3c907-160">The new Universal Actions for Adaptive Cards enables a common handling of the Adaptive Card actions across platforms and applications.</span></span> <span data-ttu-id="3c907-161">Para obter mais informações, consulte [Modelo de Ação Universal](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model).</span><span class="sxs-lookup"><span data-stu-id="3c907-161">For more information, see [Universal Action Model](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model).</span></span>

<span data-ttu-id="3c907-162">[Trabalhar com ações universais para cartões adaptáveis](Work-with-universal-actions-for-adaptive-cards.md) o documento leva você pelas etapas para usar os recursos de Ações Universais para Cartões Adaptáveis para sua solução.</span><span class="sxs-lookup"><span data-stu-id="3c907-162">[Work with Universal Actions for Adaptive Cards](Work-with-universal-actions-for-adaptive-cards.md) document takes you through the steps to use the capabilities of Universal Actions for Adaptive Cards for your solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c907-163">Confira também</span><span class="sxs-lookup"><span data-stu-id="3c907-163">See also</span></span>

* [<span data-ttu-id="3c907-164">O que são bots</span><span class="sxs-lookup"><span data-stu-id="3c907-164">What are bots</span></span>](~/bots/what-are-bots.md)
* [<span data-ttu-id="3c907-165">Visão geral dos Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3c907-165">Adaptive Cards overview</span></span>](~/task-modules-and-cards/what-are-cards.md)
* [<span data-ttu-id="3c907-166">Cartões adaptáveis @ Microsoft Build 2020</span><span class="sxs-lookup"><span data-stu-id="3c907-166">Adaptive Cards @ Microsoft Build 2020</span></span>](https://youtu.be/hEBhwB72Qn4?t=1393)
* [<span data-ttu-id="3c907-167">Cartões adaptáveis @ Ignite 2020</span><span class="sxs-lookup"><span data-stu-id="3c907-167">Adaptive Cards @ Ignite 2020</span></span>](https://techcommunity.microsoft.com/t5/video-hub/elevate-user-experiences-with-teams-and-adaptive-cards/m-p/1689460)

## <a name="next-step"></a><span data-ttu-id="3c907-168">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="3c907-168">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3c907-169">Trabalhar com ações universais para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3c907-169">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
