---
title: Trabalhar com Ações Universais para Cartões Adaptáveis
description: Trabalhe com as Ações Universais para Cartões Adaptáveis.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 4361f1c7774837b728c6382df4e62e00ea912e35
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649696"
---
# <a name="work-with-universal-actions-for-adaptive-cards"></a><span data-ttu-id="820b0-103">Trabalhar com Ações Universais para Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="820b0-103">Work with Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="820b0-104">Ações universais para cartões adaptáveis fornece uma maneira de implementar cenários baseados em Cartão Adaptável para ambos, Teams e Outlook.</span><span class="sxs-lookup"><span data-stu-id="820b0-104">Universal Actions for Adaptive Cards provides a way to implement Adaptive Card based scenarios for both, Teams and Outlook.</span></span> <span data-ttu-id="820b0-105">Este documento aborda o seguinte:</span><span class="sxs-lookup"><span data-stu-id="820b0-105">This document covers the following:</span></span>

* [<span data-ttu-id="820b0-106">Esquema usado para ações universais para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="820b0-106">Schema used for Universal Actions for Adaptive Cards</span></span>](#schema-for-universal-actions-for-adaptive-cards)
* [<span data-ttu-id="820b0-107">Modelo de atualização</span><span class="sxs-lookup"><span data-stu-id="820b0-107">Refresh model</span></span>](#refresh-model)
* [<span data-ttu-id="820b0-108">`adaptiveCard/action` invocar atividade</span><span class="sxs-lookup"><span data-stu-id="820b0-108">`adaptiveCard/action` invoke activity</span></span>](#adaptivecardaction-invoke-activity)
* [<span data-ttu-id="820b0-109">Compatibilidade com versões anteriores</span><span class="sxs-lookup"><span data-stu-id="820b0-109">Backward compatibility</span></span>](#backward-compatibility)

## <a name="quick-start-guide-to-leverage-universal-actions-for-adaptive-cards-in-teams"></a><span data-ttu-id="820b0-110">Guia de início rápido para aproveitar ações universais para cartões adaptáveis no Teams</span><span class="sxs-lookup"><span data-stu-id="820b0-110">Quick start guide to leverage Universal Actions for Adaptive Cards in Teams</span></span>

1. <span data-ttu-id="820b0-111">Substitua todas as instâncias `Action.Submit` de para atualizar um cenário existente no `Action.Execute` Teams.</span><span class="sxs-lookup"><span data-stu-id="820b0-111">Replace all instances of `Action.Submit` with `Action.Execute` to update an existing scenario on Teams.</span></span>
2. <span data-ttu-id="820b0-112">Adicione uma cláusula ao seu Cartão Adaptável, se você quiser aproveitar o modelo de atualização automática ou se seu cenário `refresh` exigir Exibições Específicas do Usuário.</span><span class="sxs-lookup"><span data-stu-id="820b0-112">Add a `refresh` clause to your Adaptive Card, if you want to leverage the automatic refresh model or if your scenario requires User Specific Views.</span></span>

    >[!NOTE]
    > <span data-ttu-id="820b0-113">`userIds`Especifique a propriedade a ser identificada, quais usuários receberão atualizações automáticas.</span><span class="sxs-lookup"><span data-stu-id="820b0-113">Specify the `userIds` property to identify, which users get automatic updates.</span></span>

3. <span data-ttu-id="820b0-114">Manipular `adaptiveCard/action` solicitações de invocação em seu bot.</span><span class="sxs-lookup"><span data-stu-id="820b0-114">Handle `adaptiveCard/action` invoke requests in your bot.</span></span>
4. <span data-ttu-id="820b0-115">Use o contexto da solicitação de invocação para responder com cartões criados especificamente para um usuário.</span><span class="sxs-lookup"><span data-stu-id="820b0-115">Use the invoke request's context to respond back with cards that are specifically created for a user.</span></span>

    > [!NOTE]
    > <span data-ttu-id="820b0-116">Sempre que o bot retorna um novo cartão como resultado do processamento de um , a resposta `Action.Execute` deve estar em conformidade com o formato de resposta.</span><span class="sxs-lookup"><span data-stu-id="820b0-116">Whenever your bot returns a new card as a result of processing an `Action.Execute`, the response must conform to the response format.</span></span>

## <a name="schema-for-universal-actions-for-adaptive-cards"></a><span data-ttu-id="820b0-117">Esquema de ações universais para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="820b0-117">Schema for Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="820b0-118">Ações universais para cartões adaptáveis é introduzido no esquema cartões adaptáveis versão 1.4.</span><span class="sxs-lookup"><span data-stu-id="820b0-118">Universal Actions for Adaptive Cards is introduced in the Adaptive Cards schema version 1.4.</span></span> <span data-ttu-id="820b0-119">Para usar o Cartão Adaptável de forma eficaz, a propriedade do seu Cartão Adaptável deve `version` ser definida como 1,4.</span><span class="sxs-lookup"><span data-stu-id="820b0-119">To use Adaptive Card effectively, the `version` property of your Adaptive Card must be set to 1.4.</span></span>

> [!NOTE]
> <span data-ttu-id="820b0-120">Definir a propriedade como 1.4 torna seu Cartão Adaptável incompatível com clientes mais antigos das plataformas ou aplicativos, como Outlook e Teams, pois eles não suportam as Ações Universais para Cartões `version` Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="820b0-120">Setting the `version` property to 1.4 makes your Adaptive Card incompatible with older clients of the platforms or applications, such as Outlook and Teams, as they do not support the Universal Actions for Adaptive Cards.</span></span>

<span data-ttu-id="820b0-121">Se você definir a versão do cartão como menor que 1,4 e usar ambas as propriedades e `refresh` `Action.Execute` , o seguinte ocorrerá:</span><span class="sxs-lookup"><span data-stu-id="820b0-121">If you set the card version to less than 1.4 and use either or both, `refresh` property and `Action.Execute`, the following happens:</span></span>

| <span data-ttu-id="820b0-122">Cliente</span><span class="sxs-lookup"><span data-stu-id="820b0-122">Client</span></span> | <span data-ttu-id="820b0-123">Comportamento</span><span class="sxs-lookup"><span data-stu-id="820b0-123">Behavior</span></span> |
| :-- | :-- |
| <span data-ttu-id="820b0-124">Teams</span><span class="sxs-lookup"><span data-stu-id="820b0-124">Teams</span></span> | <span data-ttu-id="820b0-125">Seu cartão para de funcionar.</span><span class="sxs-lookup"><span data-stu-id="820b0-125">Your card stops working.</span></span> <span data-ttu-id="820b0-126">O cartão não é atualizado `Action.Execute` e não é renderizada dependendo da versão do Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="820b0-126">Card is not refreshed and `Action.Execute` does not render depending on the version of the Teams client.</span></span> <span data-ttu-id="820b0-127">Para garantir a máxima compatibilidade Teams, defina `Action.Execute` com um na propriedade `Action.Submit` fallback.</span><span class="sxs-lookup"><span data-stu-id="820b0-127">To ensure maximum compatibility in Teams, define `Action.Execute` with an `Action.Submit` in the fallback property.</span></span> |

<span data-ttu-id="820b0-128">Para obter mais informações sobre como dar suporte a clientes mais antigos, consulte [backward compatibility](#backward-compatibility).</span><span class="sxs-lookup"><span data-stu-id="820b0-128">For more information on how to support older clients, see [backward compatibility](#backward-compatibility).</span></span>

### <a name="actionexecute"></a><span data-ttu-id="820b0-129">Action.Exebonito</span><span class="sxs-lookup"><span data-stu-id="820b0-129">Action.Execute</span></span>

<span data-ttu-id="820b0-130">Ao ser autor de Cartões Adaptáveis, substitua `Action.Submit` e `Action.Http` por `Action.Execute` .</span><span class="sxs-lookup"><span data-stu-id="820b0-130">When authoring Adaptive Cards, replace `Action.Submit` and `Action.Http` with `Action.Execute`.</span></span> <span data-ttu-id="820b0-131">O esquema para `Action.Execute` é semelhante ao de `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="820b0-131">The schema for `Action.Execute` is similar to that of `Action.Submit`.</span></span>

<span data-ttu-id="820b0-132">Para obter mais informações, [consulteAction.Exeesquema e propriedades atraentes.](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)</span><span class="sxs-lookup"><span data-stu-id="820b0-132">For more information, see [Action.Execute schema and properties](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span></span>

<span data-ttu-id="820b0-133">Agora, você pode usar o modelo de atualização para permitir que cartões adaptáveis atualizem automaticamente.</span><span class="sxs-lookup"><span data-stu-id="820b0-133">Now, you can use the refresh model to allow Adaptive Cards to update automatically.</span></span>

## <a name="refresh-model"></a><span data-ttu-id="820b0-134">Modelo de atualização</span><span class="sxs-lookup"><span data-stu-id="820b0-134">Refresh model</span></span>

<span data-ttu-id="820b0-135">Para atualizar automaticamente seu Cartão Adaptável, defina sua propriedade, que incorpora uma `refresh` ação de tipo e uma `Action.Execute` `userIds` matriz.</span><span class="sxs-lookup"><span data-stu-id="820b0-135">To automatically refresh your Adaptive Card, define its `refresh` property, which embeds an action of type `Action.Execute` and an `userIds` array.</span></span>

<span data-ttu-id="820b0-136">Para obter mais informações, [consulte refresh schema and properties](/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).</span><span class="sxs-lookup"><span data-stu-id="820b0-136">For more information, see [refresh schema and properties](/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).</span></span>

## <a name="user-ids-in-refresh"></a><span data-ttu-id="820b0-137">IDs de usuário na atualização</span><span class="sxs-lookup"><span data-stu-id="820b0-137">User IDs in refresh</span></span>

<span data-ttu-id="820b0-138">Veja a seguir os recursos de UserIds na atualização:</span><span class="sxs-lookup"><span data-stu-id="820b0-138">The following are the features of UserIds in refresh:</span></span>

* <span data-ttu-id="820b0-139">UserIds é uma matriz de MRI do usuário que faz parte da `refresh` propriedade em Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="820b0-139">UserIds is an array of user MRI's which is part of the `refresh` property in Adaptive Cards.</span></span>

* <span data-ttu-id="820b0-140">Se a propriedade list for especificada como na seção de atualização do cartão, o `userIds` cartão não será atualizado `userIds: []` automaticamente.</span><span class="sxs-lookup"><span data-stu-id="820b0-140">If the `userIds` list property is specified as `userIds: []` in the refresh section of the card, the card is not automatically refreshed.</span></span> <span data-ttu-id="820b0-141">Em vez disso, uma opção Refresh **Card** é exibida para o usuário no menu de ponto triplo na Web ou área de trabalho e no menu de contexto de pressão longa no celular, ou seja, Android ou iOS para atualizar manualmente o cartão.</span><span class="sxs-lookup"><span data-stu-id="820b0-141">Instead, a **Refresh Card** option is displayed to the user in the triple dot menu in web or desktop and in the long press context menu in mobile, that is, Android or iOS to manually refresh the card.</span></span>

* <span data-ttu-id="820b0-142">A propriedade UserIds é adicionada porque os canais Teams podem incluir um grande número de membros.</span><span class="sxs-lookup"><span data-stu-id="820b0-142">UserIds property is added because channels in Teams can include a large number of members.</span></span> <span data-ttu-id="820b0-143">Se todos os membros estão exibindo o canal ao mesmo tempo, uma atualização automática incondicional resulta em muitas chamadas simultâneas para o bot.</span><span class="sxs-lookup"><span data-stu-id="820b0-143">If all members are viewing the channel at the same time, an unconditional automatic refresh results in many concurrent calls to the bot.</span></span> <span data-ttu-id="820b0-144">Para evitar isso, a propriedade sempre deve ser incluída para identificar quais usuários devem obter uma atualização automática com um máximo de `userIds` *60 (60) MRIs* de usuário.</span><span class="sxs-lookup"><span data-stu-id="820b0-144">To avoid this, the `userIds` property must always be included to identify which users must get an automatic refresh with a maximum of *60 (sixty) user MRIs*.</span></span>

* <span data-ttu-id="820b0-145">Para obter mais informações sobre como você pode buscar Teams MRIs de usuário do membro da conversa para adicionar na lista userIds na seção de atualização do Cartão Adaptável, consulte [fetch roster](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile)or user profile .</span><span class="sxs-lookup"><span data-stu-id="820b0-145">For more information on how you can fetch Teams conversation member's user MRIs to add in userIds list in refresh section of Adaptive Card, see [fetch roster or user profile](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).</span></span>

* <span data-ttu-id="820b0-146">Exemplo Teams MRI do usuário é`29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`</span><span class="sxs-lookup"><span data-stu-id="820b0-146">Sample Teams user MRI is `29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`</span></span>

> [!NOTE]
> <span data-ttu-id="820b0-147">A propriedade é ignorada no Outlook e a `userIds` propriedade é sempre ativada `refresh` automaticamente.</span><span class="sxs-lookup"><span data-stu-id="820b0-147">The `userIds` property is ignored in Outlook, and the `refresh` property is always automatically activated.</span></span> <span data-ttu-id="820b0-148">Não há nenhum problema de escala no Outlook porque os usuários visualizam o cartão em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="820b0-148">There is no scale issue in Outlook because users view the card at different times.</span></span>

<span data-ttu-id="820b0-149">A próxima etapa é usar a atividade `adaptiveCard/action` de invocação para entender qual solicitação deve ser feita após `Action.Execute` a execução.</span><span class="sxs-lookup"><span data-stu-id="820b0-149">Next step is to use the `adaptiveCard/action` invoke activity to understand what request must be made after `Action.Execute` is executed.</span></span>

## <a name="adaptivecardaction-invoke-activity"></a><span data-ttu-id="820b0-150">`adaptiveCard/action` invocar atividade</span><span class="sxs-lookup"><span data-stu-id="820b0-150">`adaptiveCard/action` invoke activity</span></span>

<span data-ttu-id="820b0-151">Quando `Action.Execute` é executado no cliente, um novo tipo de atividade Invoke é feito no `adaptiveCard/action` bot.</span><span class="sxs-lookup"><span data-stu-id="820b0-151">When `Action.Execute` is executed in the client, a new type of Invoke activity `adaptiveCard/action` is made to your bot.</span></span>

<span data-ttu-id="820b0-152">Para obter mais informações, consulte [request format and properties for a typical invoke `adaptiveCard/action` activity](/adaptive-cards/authoring-cards/universal-action-model#request-format).</span><span class="sxs-lookup"><span data-stu-id="820b0-152">For more information, see [request format and properties for a typical `adaptiveCard/action` invoke activity](/adaptive-cards/authoring-cards/universal-action-model#request-format).</span></span>

<span data-ttu-id="820b0-153">Para obter mais informações, consulte [formato de resposta e propriedades para uma atividade de `adaptiveCard/action` invocação típica com tipos de resposta com suporte.](/adaptive-cards/authoring-cards/universal-action-model#response-format)</span><span class="sxs-lookup"><span data-stu-id="820b0-153">For more information, see [response format and properties for a typical `adaptiveCard/action` invoke activity with supported response types](/adaptive-cards/authoring-cards/universal-action-model#response-format).</span></span>

<span data-ttu-id="820b0-154">Em seguida, você pode aplicar compatibilidade com versões anteriores a clientes mais antigos em diferentes plataformas e tornar seu Cartão Adaptável compatível.</span><span class="sxs-lookup"><span data-stu-id="820b0-154">Next, you can apply backward compatibility to older clients across different platforms and make your Adaptive Card compatible.</span></span>

## <a name="backward-compatibility"></a><span data-ttu-id="820b0-155">Compatibilidade com versões anteriores</span><span class="sxs-lookup"><span data-stu-id="820b0-155">Backward compatibility</span></span>

<span data-ttu-id="820b0-156">Ações universais para cartões adaptáveis permite definir propriedades que permitem compatibilidade com versões anteriores de Outlook e Teams.</span><span class="sxs-lookup"><span data-stu-id="820b0-156">Universal Actions for Adaptive Cards allows you to set properties that enable backward compatibility with older versions of Outlook and Teams.</span></span>

### <a name="teams"></a><span data-ttu-id="820b0-157">Teams</span><span class="sxs-lookup"><span data-stu-id="820b0-157">Teams</span></span>

<span data-ttu-id="820b0-158">Para garantir a compatibilidade com versões anteriores dos Cartões Adaptáveis com versões mais antigas Teams, você deve incluir a propriedade e definir seu `fallback` valor como `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="820b0-158">To ensure backward compatibility of your Adaptive Cards with older versions of Teams, you must include the `fallback` property and set its value to `Action.Submit`.</span></span> <span data-ttu-id="820b0-159">Além disso, seu código de bot deve processar `Action.Execute` tanto quanto `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="820b0-159">Also, your bot code must process both `Action.Execute` and `Action.Submit`.</span></span>

<span data-ttu-id="820b0-160">Para obter mais informações, consulte [backward compatibility on Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).</span><span class="sxs-lookup"><span data-stu-id="820b0-160">For more information, see [backward compatibility on Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).</span></span>

## <a name="code-sample"></a><span data-ttu-id="820b0-161">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="820b0-161">Code sample</span></span>

|<span data-ttu-id="820b0-162">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="820b0-162">Sample name</span></span> | <span data-ttu-id="820b0-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="820b0-163">Description</span></span> | <span data-ttu-id="820b0-164">. NETCore</span><span class="sxs-lookup"><span data-stu-id="820b0-164">.NETCore</span></span> |
|----------------|-----------------|--------------|
| <span data-ttu-id="820b0-165">Teams de bufê</span><span class="sxs-lookup"><span data-stu-id="820b0-165">Teams catering bot</span></span> | <span data-ttu-id="820b0-166">Crie um bot simples que aceite a ordem de alimentação usando Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="820b0-166">Create a simple bot that accepts food order using Adaptive Cards.</span></span> |[<span data-ttu-id="820b0-167">View</span><span class="sxs-lookup"><span data-stu-id="820b0-167">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)|

## <a name="see-also"></a><span data-ttu-id="820b0-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="820b0-168">See also</span></span>

* [<span data-ttu-id="820b0-169">Ações de Cartão Adaptável em Teams</span><span class="sxs-lookup"><span data-stu-id="820b0-169">Adaptive Card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [<span data-ttu-id="820b0-170">Como os bots funcionam</span><span class="sxs-lookup"><span data-stu-id="820b0-170">How bots work</span></span>](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
