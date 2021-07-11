---
title: Trabalhar com Ações Universais para Cartões Adaptáveis
description: Trabalhar com Ações Universais para Cartões Adaptáveis.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 4361f1c7774837b728c6382df4e62e00ea912e35
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649696"
---
# <a name="work-with-universal-actions-for-adaptive-cards"></a><span data-ttu-id="8f2cf-103">Trabalhar com Ações Universais para Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="8f2cf-103">Work with Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="8f2cf-104">As Ações Universais para Cartões Adaptáveis fornecem uma maneira de implementar cenários baseados no Cartão Adaptável para o Teams e o Outlook.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-104">Universal Actions for Adaptive Cards provides a way to implement Adaptive Card based scenarios for both, Teams and Outlook.</span></span> <span data-ttu-id="8f2cf-105">Este documento aborda o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8f2cf-105">This document covers the following:</span></span>

* [<span data-ttu-id="8f2cf-106">Esquema usado em Ações Universais para Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="8f2cf-106">Schema used for Universal Actions for Adaptive Cards</span></span>](#schema-for-universal-actions-for-adaptive-cards)
* [<span data-ttu-id="8f2cf-107">Modelo de atualização</span><span class="sxs-lookup"><span data-stu-id="8f2cf-107">Refresh model</span></span>](#refresh-model)
* [<span data-ttu-id="8f2cf-108">`adaptiveCard/action` atividade de invocação</span><span class="sxs-lookup"><span data-stu-id="8f2cf-108">`adaptiveCard/action` invoke activity</span></span>](#adaptivecardaction-invoke-activity)
* [<span data-ttu-id="8f2cf-109">Compatibilidade com versões anteriores</span><span class="sxs-lookup"><span data-stu-id="8f2cf-109">Backward compatibility</span></span>](#backward-compatibility)

## <a name="quick-start-guide-to-leverage-universal-actions-for-adaptive-cards-in-teams"></a><span data-ttu-id="8f2cf-110">Guia de início rápido para aproveitar as Ações Universais para Cartões Adaptáveis no Teams</span><span class="sxs-lookup"><span data-stu-id="8f2cf-110">Quick start guide to leverage Universal Actions for Adaptive Cards in Teams</span></span>

1. <span data-ttu-id="8f2cf-111">Substitua todas as instâncias de `Action.Submit` por `Action.Execute` para atualizar um cenário existente no Teams.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-111">Replace all instances of `Action.Submit` with `Action.Execute` to update an existing scenario on Teams.</span></span>
2. <span data-ttu-id="8f2cf-112">Adicione uma cláusula `refresh` ao seu Cartão Adaptável, se você quiser aproveitar o modelo de atualização automática ou se seu cenário exigir Exibições Específicas do Usuário.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-112">Add a `refresh` clause to your Adaptive Card, if you want to leverage the automatic refresh model or if your scenario requires User Specific Views.</span></span>

    >[!NOTE]
    > <span data-ttu-id="8f2cf-113">Especifique a propriedade `userIds` para identificar quais usuários obtêm atualizações automáticas.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-113">Specify the `userIds` property to identify, which users get automatic updates.</span></span>

3. <span data-ttu-id="8f2cf-114">Manipule solicitações de invocação `adaptiveCard/action` em seu bot.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-114">Handle `adaptiveCard/action` invoke requests in your bot.</span></span>
4. <span data-ttu-id="8f2cf-115">Use o contexto da solicitação de invocação para responder com cartões criados especificamente para um usuário.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-115">Use the invoke request's context to respond back with cards that are specifically created for a user.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8f2cf-116">Sempre que um bot retorna um novo cartão como resultado do processamento de um `Action.Execute`, a resposta deve estar de acordo com o formato de resposta.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-116">Whenever your bot returns a new card as a result of processing an `Action.Execute`, the response must conform to the response format.</span></span>

## <a name="schema-for-universal-actions-for-adaptive-cards"></a><span data-ttu-id="8f2cf-117">Esquema de Ações Universais para Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="8f2cf-117">Schema for Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="8f2cf-118">As Ações Universais para Cartões Adaptáveis são introduzidas na versão 1.4 do esquema de Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-118">Universal Actions for Adaptive Cards is introduced in the Adaptive Cards schema version 1.4.</span></span> <span data-ttu-id="8f2cf-119">Para usar o Cartão Adaptável com eficiência, a propriedade `version` do seu Cartão Adaptável deve ser definida como 1.4.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-119">To use Adaptive Card effectively, the `version` property of your Adaptive Card must be set to 1.4.</span></span>

> [!NOTE]
> <span data-ttu-id="8f2cf-120">Definir a propriedade `version` como 1.4 torna seu Cartão Adaptável incompatível com clientes mais antigos das plataformas ou aplicativos, como o Outlook e o Teams, pois eles não dão suporte às Ações Universais para Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-120">Setting the `version` property to 1.4 makes your Adaptive Card incompatible with older clients of the platforms or applications, such as Outlook and Teams, as they do not support the Universal Actions for Adaptive Cards.</span></span>

<span data-ttu-id="8f2cf-121">Se você definir a versão do cartão como menor que 1.4 e usar uma ou ambas, propriedade `refresh` e `Action.Execute`, ocorrerá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8f2cf-121">If you set the card version to less than 1.4 and use either or both, `refresh` property and `Action.Execute`, the following happens:</span></span>

| <span data-ttu-id="8f2cf-122">Cliente</span><span class="sxs-lookup"><span data-stu-id="8f2cf-122">Client</span></span> | <span data-ttu-id="8f2cf-123">Comportamento</span><span class="sxs-lookup"><span data-stu-id="8f2cf-123">Behavior</span></span> |
| :-- | :-- |
| <span data-ttu-id="8f2cf-124">Teams</span><span class="sxs-lookup"><span data-stu-id="8f2cf-124">Teams</span></span> | <span data-ttu-id="8f2cf-125">Seu cartão para de funcionar.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-125">Your card stops working.</span></span> <span data-ttu-id="8f2cf-126">O cartão não é atualizado e `Action.Execute` não é renderizado dependendo da versão do cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-126">Card is not refreshed and `Action.Execute` does not render depending on the version of the Teams client.</span></span> <span data-ttu-id="8f2cf-127">Para garantir a compatibilidade máxima no Teams, defina `Action.Execute` com um `Action.Submit` na propriedade de fallback.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-127">To ensure maximum compatibility in Teams, define `Action.Execute` with an `Action.Submit` in the fallback property.</span></span> |

<span data-ttu-id="8f2cf-128">Para obter mais informações sobre como dar suporte a clientes mais antigos, consulte [compatibilidade com versões anteriores](#backward-compatibility).</span><span class="sxs-lookup"><span data-stu-id="8f2cf-128">For more information on how to support older clients, see [backward compatibility](#backward-compatibility).</span></span>

### <a name="actionexecute"></a><span data-ttu-id="8f2cf-129">Action.Execute</span><span class="sxs-lookup"><span data-stu-id="8f2cf-129">Action.Execute</span></span>

<span data-ttu-id="8f2cf-130">Ao criar Cartões Adaptáveis, substitua `Action.Submit` e `Action.Http` por `Action.Execute`.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-130">When authoring Adaptive Cards, replace `Action.Submit` and `Action.Http` with `Action.Execute`.</span></span> <span data-ttu-id="8f2cf-131">O esquema para `Action.Execute` é semelhante ao de `Action.Submit`.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-131">The schema for `Action.Execute` is similar to that of `Action.Submit`.</span></span>

<span data-ttu-id="8f2cf-132">Para obter mais informações, consulte o [esquema e as propriedades Action.Execute](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span><span class="sxs-lookup"><span data-stu-id="8f2cf-132">For more information, see [Action.Execute schema and properties](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span></span>

<span data-ttu-id="8f2cf-133">Agora, você pode usar o modelo de atualização para permitir que Cartões Adaptáveis sejam atualizados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-133">Now, you can use the refresh model to allow Adaptive Cards to update automatically.</span></span>

## <a name="refresh-model"></a><span data-ttu-id="8f2cf-134">Modelo de atualização</span><span class="sxs-lookup"><span data-stu-id="8f2cf-134">Refresh model</span></span>

<span data-ttu-id="8f2cf-135">Para atualizar automaticamente seu Cartão Adaptável, defina sua propriedade `refresh`, que insere uma ação do tipo `Action.Execute` e uma matriz `userIds`.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-135">To automatically refresh your Adaptive Card, define its `refresh` property, which embeds an action of type `Action.Execute` and an `userIds` array.</span></span>

<span data-ttu-id="8f2cf-136">Para obter mais informações, consulte [atualizar esquema e propriedades](/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).</span><span class="sxs-lookup"><span data-stu-id="8f2cf-136">For more information, see [refresh schema and properties](/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).</span></span>

## <a name="user-ids-in-refresh"></a><span data-ttu-id="8f2cf-137">IDs de usuário na atualização</span><span class="sxs-lookup"><span data-stu-id="8f2cf-137">User IDs in refresh</span></span>

<span data-ttu-id="8f2cf-138">Estes são os recursos de UserIds na atualização:</span><span class="sxs-lookup"><span data-stu-id="8f2cf-138">The following are the features of UserIds in refresh:</span></span>

* <span data-ttu-id="8f2cf-139">UserIds é uma matriz de MRIs de usuário que faz parte da propriedade `refresh` nos Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-139">UserIds is an array of user MRI's which is part of the `refresh` property in Adaptive Cards.</span></span>

* <span data-ttu-id="8f2cf-140">Se a propriedade de lista `userIds` for especificada como `userIds: []` na seção de atualização do cartão, o cartão não será atualizado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-140">If the `userIds` list property is specified as `userIds: []` in the refresh section of the card, the card is not automatically refreshed.</span></span> <span data-ttu-id="8f2cf-141">Em vez disso, uma opção **Atualizar Cartão** é exibida para o usuário no menu de três pontos na Web ou área de trabalho e no menu de contexto de pressionamento longo no celular, ou seja, Android ou iOS para atualizar manualmente o cartão.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-141">Instead, a **Refresh Card** option is displayed to the user in the triple dot menu in web or desktop and in the long press context menu in mobile, that is, Android or iOS to manually refresh the card.</span></span>

* <span data-ttu-id="8f2cf-142">A propriedade userIds é adicionada porque os canais no Teams podem incluir um número grande de membros.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-142">UserIds property is added because channels in Teams can include a large number of members.</span></span> <span data-ttu-id="8f2cf-143">Se todos os membros estão exibindo o canal ao mesmo tempo, uma atualização automática incondicional resultará em muitas chamadas simultâneas para o bot.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-143">If all members are viewing the channel at the same time, an unconditional automatic refresh results in many concurrent calls to the bot.</span></span> <span data-ttu-id="8f2cf-144">Para evitar isso, a propriedade `userIds` deve sempre ser incluída para identificar quais usuários devem obter uma atualização automática com um máximo de *60 (sessenta) MRIs de usuário*.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-144">To avoid this, the `userIds` property must always be included to identify which users must get an automatic refresh with a maximum of *60 (sixty) user MRIs*.</span></span>

* <span data-ttu-id="8f2cf-145">Para obter mais informações sobre como você pode buscar as MRIs de usuário do membro da conversa do Teams para adicionar na lista userIds na seção de atualização do Cartão Adaptável, consulte [buscar lista de participantes ou perfil de usuário](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).</span><span class="sxs-lookup"><span data-stu-id="8f2cf-145">For more information on how you can fetch Teams conversation member's user MRIs to add in userIds list in refresh section of Adaptive Card, see [fetch roster or user profile](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).</span></span>

* <span data-ttu-id="8f2cf-146">Exemplo de MRI de usuário do Teams é `29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`</span><span class="sxs-lookup"><span data-stu-id="8f2cf-146">Sample Teams user MRI is `29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`</span></span>

> [!NOTE]
> <span data-ttu-id="8f2cf-147">A propriedade `userIds` é ignorada no Outlook e a propriedade `refresh` é sempre ativada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-147">The `userIds` property is ignored in Outlook, and the `refresh` property is always automatically activated.</span></span> <span data-ttu-id="8f2cf-148">Não há nenhum problema de escala no Outlook porque os usuários exibem o cartão em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-148">There is no scale issue in Outlook because users view the card at different times.</span></span>

<span data-ttu-id="8f2cf-149">A próxima etapa é usar a atividade de inovação `adaptiveCard/action` para entender qual solicitação deve ser feita depois que `Action.Execute` é executado.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-149">Next step is to use the `adaptiveCard/action` invoke activity to understand what request must be made after `Action.Execute` is executed.</span></span>

## <a name="adaptivecardaction-invoke-activity"></a><span data-ttu-id="8f2cf-150">`adaptiveCard/action` atividade de invocação</span><span class="sxs-lookup"><span data-stu-id="8f2cf-150">`adaptiveCard/action` invoke activity</span></span>

<span data-ttu-id="8f2cf-151">Quando `Action.Execute` é executado no cliente, um novo tipo de Atividade de invocação `adaptiveCard/action` é realizada no bot.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-151">When `Action.Execute` is executed in the client, a new type of Invoke activity `adaptiveCard/action` is made to your bot.</span></span>

<span data-ttu-id="8f2cf-152">Para obter mais informações, consulte [formato da solicitação e propriedades de uma atividade de invocação`adaptiveCard/action` típica ](/adaptive-cards/authoring-cards/universal-action-model#request-format).</span><span class="sxs-lookup"><span data-stu-id="8f2cf-152">For more information, see [request format and properties for a typical `adaptiveCard/action` invoke activity](/adaptive-cards/authoring-cards/universal-action-model#request-format).</span></span>

<span data-ttu-id="8f2cf-153">Para obter mais informações, consulte [formato de resposta e propriedade de uma atividade de invocação típica `adaptiveCard/action` com tipos de resposta com suporte](/adaptive-cards/authoring-cards/universal-action-model#response-format).</span><span class="sxs-lookup"><span data-stu-id="8f2cf-153">For more information, see [response format and properties for a typical `adaptiveCard/action` invoke activity with supported response types](/adaptive-cards/authoring-cards/universal-action-model#response-format).</span></span>

<span data-ttu-id="8f2cf-154">Em seguida, você pode aplicar a compatibilidade com versões anteriores a clientes mais antigos em diferentes plataformas e tornar seu Cartão Adaptável compatível.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-154">Next, you can apply backward compatibility to older clients across different platforms and make your Adaptive Card compatible.</span></span>

## <a name="backward-compatibility"></a><span data-ttu-id="8f2cf-155">Compatibilidade com versões anteriores</span><span class="sxs-lookup"><span data-stu-id="8f2cf-155">Backward compatibility</span></span>

<span data-ttu-id="8f2cf-156">As Ações Universais para Cartões Adaptáveis permitem definir propriedades que permitem a compatibilidade com versões anteriores do Outlook e do Teams.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-156">Universal Actions for Adaptive Cards allows you to set properties that enable backward compatibility with older versions of Outlook and Teams.</span></span>

### <a name="teams"></a><span data-ttu-id="8f2cf-157">Teams</span><span class="sxs-lookup"><span data-stu-id="8f2cf-157">Teams</span></span>

<span data-ttu-id="8f2cf-158">Para garantir a compatibilidade com versões anteriores do Teams nos Cartões Adaptáveis, você deve incluir a propriedade `fallback` e definir seu valor como `Action.Submit`.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-158">To ensure backward compatibility of your Adaptive Cards with older versions of Teams, you must include the `fallback` property and set its value to `Action.Submit`.</span></span> <span data-ttu-id="8f2cf-159">Além disso, o código do bot deve processar `Action.Execute` e `Action.Submit`.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-159">Also, your bot code must process both `Action.Execute` and `Action.Submit`.</span></span>

<span data-ttu-id="8f2cf-160">Para obter mais informações, consulte [compatibilidade com versões anteriores no Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).</span><span class="sxs-lookup"><span data-stu-id="8f2cf-160">For more information, see [backward compatibility on Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).</span></span>

## <a name="code-sample"></a><span data-ttu-id="8f2cf-161">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="8f2cf-161">Code sample</span></span>

|<span data-ttu-id="8f2cf-162">Nome do exemplo</span><span class="sxs-lookup"><span data-stu-id="8f2cf-162">Sample name</span></span> | <span data-ttu-id="8f2cf-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f2cf-163">Description</span></span> | <span data-ttu-id="8f2cf-164">.NETCore</span><span class="sxs-lookup"><span data-stu-id="8f2cf-164">.NETCore</span></span> |
|----------------|-----------------|--------------|
| <span data-ttu-id="8f2cf-165">Bot de refeições do Teams</span><span class="sxs-lookup"><span data-stu-id="8f2cf-165">Teams catering bot</span></span> | <span data-ttu-id="8f2cf-166">Crie um bot simples que aceita encomendas de comida usando Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="8f2cf-166">Create a simple bot that accepts food order using Adaptive Cards.</span></span> |[<span data-ttu-id="8f2cf-167">Exibir</span><span class="sxs-lookup"><span data-stu-id="8f2cf-167">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)|

## <a name="see-also"></a><span data-ttu-id="8f2cf-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="8f2cf-168">See also</span></span>

* [<span data-ttu-id="8f2cf-169">Ações de Cartão Adaptável no Teams</span><span class="sxs-lookup"><span data-stu-id="8f2cf-169">Adaptive Card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [<span data-ttu-id="8f2cf-170">Como os bots funcionam</span><span class="sxs-lookup"><span data-stu-id="8f2cf-170">How bots work</span></span>](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
