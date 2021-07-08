---
title: Tipos de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Teams
localization_priority: Normal
keywords: referência de cartões bots
ms.topic: reference
ms.openlocfilehash: d3b84344eccee7c2595b0e978c72d7e331b198cb
ms.sourcegitcommit: b1f9162a0bbcd276064ae9e4f1e8bccc06cb7035
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2021
ms.locfileid: "53328069"
---
# <a name="types-of-cards"></a><span data-ttu-id="ff0e8-104">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="ff0e8-104">Types of cards</span></span>

<span data-ttu-id="ff0e8-105">Adaptável, herói, lista, conector Office 365, recibo, entrada e coleções de cartões de miniatura são suportados em bots para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-105">Adaptive, hero, list, Office 365 Connector, receipt, signin, and thumbnail cards and card collections are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="ff0e8-106">Eles são baseados em cartões definidos pela Estrutura de Bot, mas Teams não dá suporte a todos os cartões da Estrutura de Bot e adicionou alguns de seus próprios.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span>

<span data-ttu-id="ff0e8-107">Antes de identificar os diferentes tipos de cartão, entenda como criar um cartão de herói, um cartão de miniatura ou um Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-107">Before you identify the different card types, understand how to create a a hero card, thumbnail card, or Adaptive Card.</span></span>

## <a name="create-a-hero-card-thumbnail-card-or-adaptive-card"></a><span data-ttu-id="ff0e8-108">Criar um cartão de herói, um cartão em miniatura ou um Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="ff0e8-108">Create a hero card, thumbnail card, or Adaptive Card</span></span>

<span data-ttu-id="ff0e8-109">**Para criar um cartão de herói, um cartão em miniatura ou um Cartão Adaptável do App Studio**</span><span class="sxs-lookup"><span data-stu-id="ff0e8-109">**To create a hero card, thumbnail card, or Adaptive Card from App Studio**</span></span>

1. <span data-ttu-id="ff0e8-110">Vá para **o App Studio** Teams.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-110">Go to **App Studio** from Teams.</span></span>
1. <span data-ttu-id="ff0e8-111">Selecione **Editor de cartão**.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-111">Select **Card editor**.</span></span>
1. <span data-ttu-id="ff0e8-112">Selecione **Criar um novo cartão**.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-112">Select **Create a new card**.</span></span>
1. <span data-ttu-id="ff0e8-113">Selecione **Criar** para um dos cartões de **Cartão de Herói,** **Cartão de** Miniatura ou **Cartão Adaptável.**</span><span class="sxs-lookup"><span data-stu-id="ff0e8-113">Select **Create** for one of the cards from **Hero Card**, **Thumbnail Card**, or **Adaptive Card**.</span></span> <span data-ttu-id="ff0e8-114">Os exemplos de detalhes de metadados, botões e json, csharp e código de nó são mostrados para esse cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-114">The metadata details, buttons, and json, csharp, and node code examples are shown for that card.</span></span>

    ![Detalhes do cartão de herói](~/assets/images/Cards/Herocarddetails.png)

1. <span data-ttu-id="ff0e8-116">Selecione Enviar este cartão para **mim.**</span><span class="sxs-lookup"><span data-stu-id="ff0e8-116">Select **Send me this card**.</span></span> <span data-ttu-id="ff0e8-117">O cartão é enviado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-117">The card is sent to you as a chat message.</span></span>

## <a name="card-examples"></a><span data-ttu-id="ff0e8-118">Exemplos de cartão</span><span class="sxs-lookup"><span data-stu-id="ff0e8-118">Card examples</span></span>

<span data-ttu-id="ff0e8-119">Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do Construtor de Bots v3.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-119">You can find additional information on how to use cards in the documentation for the Bot Builder SDK v3.</span></span> <span data-ttu-id="ff0e8-120">Exemplos de código também estão disponíveis no **repositório Microsoft/BotBuilder-Samples** no GitHub.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-120">Code samples are also available in the **Microsoft/BotBuilder-Samples** repository on GitHub.</span></span> <span data-ttu-id="ff0e8-121">A seguir estão alguns exemplos de cartão:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-121">Following are a few card examples:</span></span>

* <span data-ttu-id="ff0e8-122">.NET</span><span class="sxs-lookup"><span data-stu-id="ff0e8-122">.NET</span></span>
  * <span data-ttu-id="ff0e8-123">[Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-123">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="ff0e8-124">[Código de exemplo de cartões Construtor de bots v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-124">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span></span>

* <span data-ttu-id="ff0e8-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="ff0e8-125">Node.js</span></span>
  * <span data-ttu-id="ff0e8-126">[Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-126">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="ff0e8-127">[Código de exemplo de cartões Construtor de bots v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-127">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span></span>

## <a name="card-types"></a><span data-ttu-id="ff0e8-128">Tipos de cartão</span><span class="sxs-lookup"><span data-stu-id="ff0e8-128">Card types</span></span>

<span data-ttu-id="ff0e8-129">Você pode identificar e usar diferentes tipos de cartões com base nos requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-129">You can identify and use different types of cards based on your application requirements.</span></span> <span data-ttu-id="ff0e8-130">A tabela a seguir mostra os tipos de cartões disponíveis para você:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-130">The following table shows the types of cards available to you:</span></span>

| <span data-ttu-id="ff0e8-131">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="ff0e8-131">Card type</span></span> | <span data-ttu-id="ff0e8-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff0e8-132">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="ff0e8-133">Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="ff0e8-133">Adaptive Card</span></span>](#adaptive-card) | <span data-ttu-id="ff0e8-134">Esse cartão é altamente personalizável e pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-134">This card is highly customizable and can contain any combination of text, speech, images, buttons, and input fields.</span></span> |
| [<span data-ttu-id="ff0e8-135">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="ff0e8-135">Hero card</span></span>](#hero-card) | <span data-ttu-id="ff0e8-136">Esse cartão normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-136">This card typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="ff0e8-137">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="ff0e8-137">List card</span></span>](#list-card) | <span data-ttu-id="ff0e8-138">Este cartão contém uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-138">This card contains a scrolling list of items.</span></span> |
| [<span data-ttu-id="ff0e8-139">Office 365 Cartão conector</span><span class="sxs-lookup"><span data-stu-id="ff0e8-139">Office 365 Connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="ff0e8-140">Esse cartão tem um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-140">This card has a flexible layout with multiple sections, fields, images, and actions.</span></span> |
| [<span data-ttu-id="ff0e8-141">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="ff0e8-141">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="ff0e8-142">Este cartão fornece um recibo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-142">This card provides a receipt to the user.</span></span> |
| [<span data-ttu-id="ff0e8-143">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="ff0e8-143">Signin card</span></span>](#signin-card) | <span data-ttu-id="ff0e8-144">Esse cartão permite que um bot solicite que um usuário entre.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-144">This card enables a bot to request that a user signs in.</span></span> |
| [<span data-ttu-id="ff0e8-145">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="ff0e8-145">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="ff0e8-146">Esse cartão normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-146">This card typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="ff0e8-147">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="ff0e8-147">Card collections</span></span>](#card-collections) | <span data-ttu-id="ff0e8-148">Essa coleção de cartões é usada para retornar vários itens em uma única resposta.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-148">This card collection is used to return multiple items in a single response.</span></span> |

## <a name="features-that-support-different-card-types"></a><span data-ttu-id="ff0e8-149">Recursos que suportam diferentes tipos de cartão</span><span class="sxs-lookup"><span data-stu-id="ff0e8-149">Features that support different card types</span></span>

| <span data-ttu-id="ff0e8-150">Tipo de cartão</span><span class="sxs-lookup"><span data-stu-id="ff0e8-150">Card type</span></span> | <span data-ttu-id="ff0e8-151">Bots</span><span class="sxs-lookup"><span data-stu-id="ff0e8-151">Bots</span></span> | <span data-ttu-id="ff0e8-152">Visualizações de extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="ff0e8-152">Message extension previews</span></span> | <span data-ttu-id="ff0e8-153">Resultados da extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="ff0e8-153">Message extension results</span></span> | <span data-ttu-id="ff0e8-154">Módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="ff0e8-154">Task modules</span></span> | <span data-ttu-id="ff0e8-155">Webhooks de saída</span><span class="sxs-lookup"><span data-stu-id="ff0e8-155">Outgoing Webhooks</span></span> | <span data-ttu-id="ff0e8-156">Webhooks de entrada</span><span class="sxs-lookup"><span data-stu-id="ff0e8-156">Incoming Webhooks</span></span> | <span data-ttu-id="ff0e8-157">Conectores O365</span><span class="sxs-lookup"><span data-stu-id="ff0e8-157">O365 Connectors</span></span> |
| --- | --- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="ff0e8-158">Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="ff0e8-158">Adaptive Card</span></span> | <span data-ttu-id="ff0e8-159">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-159">✔</span></span> | <span data-ttu-id="ff0e8-160">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-160">✖</span></span> | <span data-ttu-id="ff0e8-161">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-161">✔</span></span> | <span data-ttu-id="ff0e8-162">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-162">✔</span></span> | <span data-ttu-id="ff0e8-163">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-163">✔</span></span> | <span data-ttu-id="ff0e8-164">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-164">✔</span></span> | <span data-ttu-id="ff0e8-165">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-165">✖</span></span> |
| <span data-ttu-id="ff0e8-166">Cartão conector O365</span><span class="sxs-lookup"><span data-stu-id="ff0e8-166">O365 Connector card</span></span> | <span data-ttu-id="ff0e8-167">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-167">✔</span></span> | <span data-ttu-id="ff0e8-168">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-168">✖</span></span> | <span data-ttu-id="ff0e8-169">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-169">✔</span></span> | <span data-ttu-id="ff0e8-170">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-170">✖</span></span> | <span data-ttu-id="ff0e8-171">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-171">✔</span></span> | <span data-ttu-id="ff0e8-172">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-172">✔</span></span> | <span data-ttu-id="ff0e8-173">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-173">✔</span></span> |
| <span data-ttu-id="ff0e8-174">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="ff0e8-174">Hero card</span></span> | <span data-ttu-id="ff0e8-175">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-175">✔</span></span> | <span data-ttu-id="ff0e8-176">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-176">✔</span></span> | <span data-ttu-id="ff0e8-177">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-177">✔</span></span> | <span data-ttu-id="ff0e8-178">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-178">✖</span></span> | <span data-ttu-id="ff0e8-179">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-179">✔</span></span> | <span data-ttu-id="ff0e8-180">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-180">✔</span></span> | <span data-ttu-id="ff0e8-181">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-181">✖</span></span> |
| <span data-ttu-id="ff0e8-182">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="ff0e8-182">Thumbnail card</span></span> | <span data-ttu-id="ff0e8-183">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-183">✔</span></span> | <span data-ttu-id="ff0e8-184">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-184">✔</span></span> | <span data-ttu-id="ff0e8-185">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-185">✔</span></span> | <span data-ttu-id="ff0e8-186">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-186">✖</span></span> | <span data-ttu-id="ff0e8-187">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-187">✔</span></span> | <span data-ttu-id="ff0e8-188">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-188">✔</span></span> | <span data-ttu-id="ff0e8-189">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-189">✖</span></span> |
| <span data-ttu-id="ff0e8-190">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="ff0e8-190">List card</span></span> | <span data-ttu-id="ff0e8-191">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-191">✔</span></span> | <span data-ttu-id="ff0e8-192">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-192">✖</span></span> | <span data-ttu-id="ff0e8-193">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-193">✖</span></span> | <span data-ttu-id="ff0e8-194">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-194">✖</span></span> | <span data-ttu-id="ff0e8-195">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-195">✔</span></span> | <span data-ttu-id="ff0e8-196">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-196">✔</span></span> | <span data-ttu-id="ff0e8-197">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-197">✖</span></span> |
| <span data-ttu-id="ff0e8-198">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="ff0e8-198">Receipt card</span></span> | <span data-ttu-id="ff0e8-199">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-199">✔</span></span> | <span data-ttu-id="ff0e8-200">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-200">✖</span></span> | <span data-ttu-id="ff0e8-201">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-201">✖</span></span> | <span data-ttu-id="ff0e8-202">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-202">✖</span></span> | <span data-ttu-id="ff0e8-203">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-203">✖</span></span> | <span data-ttu-id="ff0e8-204">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-204">✔</span></span> | <span data-ttu-id="ff0e8-205">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-205">✖</span></span> |
| <span data-ttu-id="ff0e8-206">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="ff0e8-206">Signin card</span></span> | <span data-ttu-id="ff0e8-207">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-207">✔</span></span> | <span data-ttu-id="ff0e8-208">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-208">✖</span></span> | <span data-ttu-id="ff0e8-209">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-209">✖</span></span> | <span data-ttu-id="ff0e8-210">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-210">✖</span></span> | <span data-ttu-id="ff0e8-211">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-211">✖</span></span> | <span data-ttu-id="ff0e8-212">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-212">✖</span></span> | <span data-ttu-id="ff0e8-213">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-213">✖</span></span> |

> [!NOTE]
> <span data-ttu-id="ff0e8-214">Para Cartões Adaptáveis em Webhooks de Entrada, todos os elementos nativos de esquema de Cartão Adaptável, exceto `Action.Submit` , são totalmente suportados.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-214">For Adaptive Cards in Incoming Webhooks, all native Adaptive Card schema elements, except `Action.Submit`, are fully supported.</span></span> <span data-ttu-id="ff0e8-215">As ações suportadas são [**Action.OpenURL,**](https://adaptivecards.io/explorer/Action.OpenUrl.html) [**Action.ShowCard,**](https://adaptivecards.io/explorer/Action.ShowCard.html) [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html)e [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-215">The supported actions are [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html), and [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span></span>

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="ff0e8-216">Propriedades comuns para todos os cartões</span><span class="sxs-lookup"><span data-stu-id="ff0e8-216">Common properties for all cards</span></span>

<span data-ttu-id="ff0e8-217">Você pode passar por algumas propriedades comuns que são aplicáveis a todos os cartões.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-217">You can go through some common properties that are applicable to all cards.</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="ff0e8-218">Imagens de cartão em linha</span><span class="sxs-lookup"><span data-stu-id="ff0e8-218">Inline card images</span></span>

<span data-ttu-id="ff0e8-219">O cartão pode conter uma imagem em linha incluindo um link para a imagem disponível publicamente.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-219">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="ff0e8-220">Para fins de desempenho, é altamente recomendável hospedar a imagem em uma Rede de Distribuição de Conteúdo pública (CDN).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-220">For performance purposes, it is highly recommended you host the image on a public Content Delivery Network (CDN).</span></span>

<span data-ttu-id="ff0e8-221">As imagens são dimensionados para cima ou para baixo em tamanho para manter a taxa de proporção para cobrir a área da imagem.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-221">Images are scaled up or down in size to maintain the aspect ratio for covering the image area.</span></span> <span data-ttu-id="ff0e8-222">Em seguida, as imagens são cortadas do centro para atingir a proporção apropriada para o cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-222">Images are then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="ff0e8-223">As imagens devem ter no máximo 1024×1024 e no formato PNG, JPEG ou GIF.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-223">Images must be at most 1024×1024 and in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="ff0e8-224">Gif animado não é suportado.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-224">Animated GIF is not supported.</span></span>

<span data-ttu-id="ff0e8-225">A tabela a seguir fornece as propriedades das imagens de cartão em linha:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-225">The following table provides the properties of inline card images:</span></span>

| <span data-ttu-id="ff0e8-226">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ff0e8-226">Property</span></span> | <span data-ttu-id="ff0e8-227">Tipo</span><span class="sxs-lookup"><span data-stu-id="ff0e8-227">Type</span></span>  | <span data-ttu-id="ff0e8-228">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff0e8-228">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="ff0e8-229">url</span><span class="sxs-lookup"><span data-stu-id="ff0e8-229">url</span></span> | <span data-ttu-id="ff0e8-230">URL</span><span class="sxs-lookup"><span data-stu-id="ff0e8-230">URL</span></span> | <span data-ttu-id="ff0e8-231">URL HTTPS para a imagem.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-231">HTTPS URL to the image.</span></span> |
| <span data-ttu-id="ff0e8-232">alt</span><span class="sxs-lookup"><span data-stu-id="ff0e8-232">alt</span></span> | <span data-ttu-id="ff0e8-233">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ff0e8-233">String</span></span> | <span data-ttu-id="ff0e8-234">Descrição acessível da imagem.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-234">Accessible description of the image.</span></span> |

> [!NOTE]
> <span data-ttu-id="ff0e8-235">Se um cartão incluir uma URL de imagem redirecionada antes da imagem final, o redirecionamento na URL da imagem não será suportado.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-235">If a card includes an image URL that is redirected before the final image, the redirect in image URL is not supported.</span></span> <span data-ttu-id="ff0e8-236">Isso ocorre para imagens compartilhadas na nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-236">This occurs for images shared on the public cloud.</span></span>

### <a name="buttons"></a><span data-ttu-id="ff0e8-237">Botões</span><span class="sxs-lookup"><span data-stu-id="ff0e8-237">Buttons</span></span>

<span data-ttu-id="ff0e8-238">Os botões são mostrados empilhados na parte inferior do cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-238">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="ff0e8-239">O texto do botão está sempre em uma única linha e é truncado se o texto exceder a largura do botão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-239">Button text is always on a single line and is truncated if the text exceeds the button width.</span></span> <span data-ttu-id="ff0e8-240">Quaisquer botões adicionais além do número máximo suportado pelo cartão não são mostrados.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-240">Any additional buttons beyond the maximum number supported by the card are not shown.</span></span>

<span data-ttu-id="ff0e8-241">Para obter mais informações, consulte [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-241">For more information, see [card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

### <a name="card-formatting"></a><span data-ttu-id="ff0e8-242">Formatação de cartão</span><span class="sxs-lookup"><span data-stu-id="ff0e8-242">Card formatting</span></span>

<span data-ttu-id="ff0e8-243">Para obter mais informações sobre formatação de texto em cartões, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-243">For more information on text formatting in cards, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

<span data-ttu-id="ff0e8-244">Depois de identificar as propriedades comuns para todos os cartões, agora você pode trabalhar com Cartões Adaptáveis, que ajudam a aumentar o envolvimento e a eficiência adicionando seu conteúdo a ação diretamente aos aplicativos que você usa.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-244">After identifying the common properties for all cards, you can now work with Adaptive Cards, which help you increase engagement and efficiency by adding your actionable content directly into the apps you use.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="ff0e8-245">Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="ff0e8-245">Adaptive Card</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/J12lKt717Ws]

<span data-ttu-id="ff0e8-246">Um Cartão Adaptável é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-246">An Adaptive Card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="ff0e8-247">Para obter mais informações, [consulte Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-247">For more information, see [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="ff0e8-248">Suporte para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="ff0e8-248">Support for Adaptive Cards</span></span>

<span data-ttu-id="ff0e8-249">A tabela a seguir fornece os recursos que suportam Cartões Adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-249">The following table provides the features that support Adaptive Cards:</span></span>

| <span data-ttu-id="ff0e8-250">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-250">Bots in Teams</span></span> | <span data-ttu-id="ff0e8-251">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-251">Messaging extensions</span></span>  | <span data-ttu-id="ff0e8-252">Conectores</span><span class="sxs-lookup"><span data-stu-id="ff0e8-252">Connectors</span></span> | <span data-ttu-id="ff0e8-253">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ff0e8-253">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="ff0e8-254">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-254">✔</span></span> | <span data-ttu-id="ff0e8-255">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-255">✔</span></span> | <span data-ttu-id="ff0e8-256">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-256">✖</span></span> | <span data-ttu-id="ff0e8-257">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-257">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="ff0e8-258">Teams plataforma suporta v1.2 ou anterior de recursos de Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-258">Teams platform supports v1.2 or earlier of Adaptive Card features.</span></span>
> * <span data-ttu-id="ff0e8-259">O estilo de ação positivo ou destrutivo não é suportado em Cartões Adaptáveis na Teams plataforma.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-259">Positive or destructive action styling is not supported in Adaptive Cards on the Teams platform.</span></span>
> * <span data-ttu-id="ff0e8-260">No momento, os elementos de mídia não têm suporte no Cartão Adaptável na Teams plataforma.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-260">Media elements are currently not supported in Adaptive Card on the Teams platform.</span></span>

### <a name="example-of-adaptive-card"></a><span data-ttu-id="ff0e8-261">Exemplo de cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="ff0e8-261">Example of Adaptive Card</span></span>

![Exemplo de um cartão adaptável](~/assets/images/cards/adaptivecard.png)

<span data-ttu-id="ff0e8-263">O código a seguir mostra um exemplo de um Cartão Adaptável:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-263">The following code shows an example of an Adaptive Card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.card.adaptive",
  "content": {
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Publish Adaptive Card schema",
            "weight": "bolder",
            "size": "medium"
          },
          {
            "type": "ColumnSet",
            "columns": [
              {
                "type": "Column",
                "width": "auto",
                "items": [
                  {
                    "type": "Image",
                    "url": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
                    "size": "small",
                    "style": "person"
                  }
                ]
              },
              {
                "type": "Column",
                "width": "stretch",
                "items": [
                  {
                    "type": "TextBlock",
                    "text": "Matt Hidinger",
                    "weight": "bolder",
                    "wrap": true
                  },
                  {
                    "type": "TextBlock",
                    "spacing": "none",
                    "text": "Created {{DATE(2017-02-14T06:08:39Z, SHORT)}}",
                    "isSubtle": true,
                    "wrap": true
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Now that we have defined the main rules and features of the format, we need to produce a schema and publish it to GitHub. The schema will be the starting point of our reference documentation.",
            "wrap": true
          },
          {
            "type": "FactSet",
            "facts": [
              {
                "title": "Board:",
                "value": "Adaptive Card"
              },
              {
                "title": "List:",
                "value": "Backlog"
              },
              {
                "title": "Assigned to:",
                "value": "Matt Hidinger"
              },
              {
                "title": "Due date:",
                "value": "Not set"
              }
            ]
          }
        ]
      }
    ],
    "actions": [
      {
        "type": "Action.ShowCard",
        "title": "Set due date",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Date",
              "id": "dueDate"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      },
      {
        "type": "Action.ShowCard",
        "title": "Comment",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Text",
              "id": "comment",
              "isMultiline": true,
              "placeholder": "Enter your comment"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      }
    ]
  }  
}
```

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="ff0e8-264">Informações adicionais sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="ff0e8-264">Additional information on Adaptive Cards</span></span>

<span data-ttu-id="ff0e8-265">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-265">Bot Framework reference:</span></span>

* [<span data-ttu-id="ff0e8-266">Nó de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="ff0e8-266">Adaptive Cards Node</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="ff0e8-267">Cartão Adaptável C #</span><span class="sxs-lookup"><span data-stu-id="ff0e8-267">Adaptive Card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

<span data-ttu-id="ff0e8-268">Agora você pode trabalhar com um cartão de herói, que é um cartão multiuso usado para realçar visualmente uma seleção de usuário potencial.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-268">You can now work with a hero card, which is a multipurpose card used to visually highlight a potential user selection.</span></span>

## <a name="hero-card"></a><span data-ttu-id="ff0e8-269">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="ff0e8-269">Hero card</span></span>

<span data-ttu-id="ff0e8-270">Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-270">A card that typically contains a single large image, one or more buttons, and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="ff0e8-271">Suporte para cartões de herói</span><span class="sxs-lookup"><span data-stu-id="ff0e8-271">Support for hero cards</span></span>

<span data-ttu-id="ff0e8-272">A tabela a seguir fornece os recursos que suportam cartões de herói:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-272">The following table provides the features that support hero cards:</span></span>

| <span data-ttu-id="ff0e8-273">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-273">Bots in Teams</span></span> | <span data-ttu-id="ff0e8-274">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-274">Messaging extensions</span></span>  | <span data-ttu-id="ff0e8-275">Conectores</span><span class="sxs-lookup"><span data-stu-id="ff0e8-275">Connectors</span></span> | <span data-ttu-id="ff0e8-276">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ff0e8-276">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="ff0e8-277">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-277">✔</span></span> | <span data-ttu-id="ff0e8-278">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-278">✔</span></span> | <span data-ttu-id="ff0e8-279">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-279">✖</span></span> | <span data-ttu-id="ff0e8-280">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-280">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="ff0e8-281">Propriedades de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="ff0e8-281">Properties of a hero card</span></span>

<span data-ttu-id="ff0e8-282">A tabela a seguir fornece as propriedades de um cartão de herói:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-282">The following table provides the properties of a hero card:</span></span>

| <span data-ttu-id="ff0e8-283">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ff0e8-283">Property</span></span> | <span data-ttu-id="ff0e8-284">Tipo</span><span class="sxs-lookup"><span data-stu-id="ff0e8-284">Type</span></span>  | <span data-ttu-id="ff0e8-285">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff0e8-285">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="ff0e8-286">title</span><span class="sxs-lookup"><span data-stu-id="ff0e8-286">title</span></span> | <span data-ttu-id="ff0e8-287">Rich text </span><span class="sxs-lookup"><span data-stu-id="ff0e8-287">Rich text</span></span> | <span data-ttu-id="ff0e8-288">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-288">Title of the card.</span></span> <span data-ttu-id="ff0e8-289">Máximo de duas linhas.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-289">Maximum two lines.</span></span> |
| <span data-ttu-id="ff0e8-290">subtitle</span><span class="sxs-lookup"><span data-stu-id="ff0e8-290">subtitle</span></span> | <span data-ttu-id="ff0e8-291">Rich text </span><span class="sxs-lookup"><span data-stu-id="ff0e8-291">Rich text</span></span> | <span data-ttu-id="ff0e8-292">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-292">Subtitle of the card.</span></span> <span data-ttu-id="ff0e8-293">Máximo de duas linhas.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-293">Maximum two lines.</span></span>|
| <span data-ttu-id="ff0e8-294">texto</span><span class="sxs-lookup"><span data-stu-id="ff0e8-294">text</span></span> | <span data-ttu-id="ff0e8-295">Rich text </span><span class="sxs-lookup"><span data-stu-id="ff0e8-295">Rich text</span></span> | <span data-ttu-id="ff0e8-296">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-296">Text appears under the subtitle.</span></span> <span data-ttu-id="ff0e8-297">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-297">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="ff0e8-298">images</span><span class="sxs-lookup"><span data-stu-id="ff0e8-298">images</span></span> | <span data-ttu-id="ff0e8-299">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-299">Array of images</span></span> | <span data-ttu-id="ff0e8-300">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-300">Image displayed at the top of the card.</span></span> <span data-ttu-id="ff0e8-301">Taxa de proporção 16:9.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-301">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="ff0e8-302">botões</span><span class="sxs-lookup"><span data-stu-id="ff0e8-302">buttons</span></span> | <span data-ttu-id="ff0e8-303">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="ff0e8-303">Array of action objects</span></span> | <span data-ttu-id="ff0e8-304">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-304">Set of actions applicable to the current card.</span></span> <span data-ttu-id="ff0e8-305">Máximo de seis.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-305">Maximum six.</span></span> |
| <span data-ttu-id="ff0e8-306">tap</span><span class="sxs-lookup"><span data-stu-id="ff0e8-306">tap</span></span> | <span data-ttu-id="ff0e8-307">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="ff0e8-307">Action object</span></span> | <span data-ttu-id="ff0e8-308">Ativado quando o usuário toca no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-308">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="ff0e8-309">Exemplo de um cartão de herói</span><span class="sxs-lookup"><span data-stu-id="ff0e8-309">Example of a hero card</span></span>

![Exemplo de um cartão de herói](~/assets/images/cards/hero.png)

<span data-ttu-id="ff0e8-311">O código a seguir mostra um exemplo de um cartão de herói:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-311">The following code shows an example of a hero card:</span></span>

```json
{
   "contentType": "application/vnd.microsoft.card.hero",
   "content": {
     "title": "Seattle Center Monorail",
     "subtitle": "Seattle Center Monorail",
     "text": "The Seattle Center Monorail is an elevated train line between Seattle Center (near the Space Needle) and downtown Seattle. It was built for the 1962 World's Fair. Its original two trains, completed in 1961, are still in service.",
     "images": [
       {
         "url":"https://upload.wikimedia.org/wikipedia/commons/thumb/4/49/Seattle_monorail01_2008-02-25.jpg/1024px-Seattle_monorail01_2008-02-25.jpg"
       }
     ],
    "buttons": [
      {
         "type": "openUrl",
         "title": "Official website",
         "value": "https://www.seattlemonorail.com"
       },
      {
        "type": "openUrl",
        "title": "Wikipeda page",
        "value": "https://en.wikipedia.org/wiki/Seattle_Center_Monorail"
       }
     ]
   }
}

```

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="ff0e8-312">Informações adicionais sobre cartões de herói</span><span class="sxs-lookup"><span data-stu-id="ff0e8-312">Additional information on hero cards</span></span>

<span data-ttu-id="ff0e8-313">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-313">Bot Framework reference:</span></span>

* [<span data-ttu-id="ff0e8-314">Cartão de herói Node.js</span><span class="sxs-lookup"><span data-stu-id="ff0e8-314">Hero card Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="ff0e8-315">Cartão de herói C #</span><span class="sxs-lookup"><span data-stu-id="ff0e8-315">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="ff0e8-316">Cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="ff0e8-316">List card</span></span>

<span data-ttu-id="ff0e8-317">O cartão de lista foi adicionado por Teams para fornecer funções além do que a coleção de listas pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-317">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="ff0e8-318">O cartão de listagem fornece uma lista de rolagem de itens.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-318">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="ff0e8-319">Suporte para cartões de lista</span><span class="sxs-lookup"><span data-stu-id="ff0e8-319">Support for list cards</span></span>

<span data-ttu-id="ff0e8-320">A tabela a seguir fornece os recursos que suportam cartões de lista:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-320">The following table provides the features that support list cards:</span></span>

| <span data-ttu-id="ff0e8-321">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-321">Bots in Teams</span></span> | <span data-ttu-id="ff0e8-322">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-322">Messaging extensions</span></span>  | <span data-ttu-id="ff0e8-323">Conectores</span><span class="sxs-lookup"><span data-stu-id="ff0e8-323">Connectors</span></span> | <span data-ttu-id="ff0e8-324">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ff0e8-324">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="ff0e8-325">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-325">✔</span></span> | <span data-ttu-id="ff0e8-326">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-326">✖</span></span> | <span data-ttu-id="ff0e8-327">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-327">✖</span></span> |<span data-ttu-id="ff0e8-328">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-328">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="ff0e8-329">Propriedades de um cartão de listagem</span><span class="sxs-lookup"><span data-stu-id="ff0e8-329">Properties of a list card</span></span>

<span data-ttu-id="ff0e8-330">A tabela a seguir fornece as propriedades de um cartão de listagem:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-330">The following table provides the properties of a list card:</span></span>

| <span data-ttu-id="ff0e8-331">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ff0e8-331">Property</span></span> | <span data-ttu-id="ff0e8-332">Tipo</span><span class="sxs-lookup"><span data-stu-id="ff0e8-332">Type</span></span>  | <span data-ttu-id="ff0e8-333">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff0e8-333">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="ff0e8-334">title</span><span class="sxs-lookup"><span data-stu-id="ff0e8-334">title</span></span> | <span data-ttu-id="ff0e8-335">Rich text </span><span class="sxs-lookup"><span data-stu-id="ff0e8-335">Rich text</span></span> | <span data-ttu-id="ff0e8-336">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-336">Title of the card.</span></span> <span data-ttu-id="ff0e8-337">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-337">Maximum 2 lines.</span></span>|
| <span data-ttu-id="ff0e8-338">itens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-338">items</span></span> | <span data-ttu-id="ff0e8-339">Matriz de itens de lista</span><span class="sxs-lookup"><span data-stu-id="ff0e8-339">Array of list items</span></span> | <span data-ttu-id="ff0e8-340">Conjunto de itens aplicáveis ao cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-340">Set of items applicable to the card.</span></span>|
| <span data-ttu-id="ff0e8-341">botões</span><span class="sxs-lookup"><span data-stu-id="ff0e8-341">buttons</span></span> | <span data-ttu-id="ff0e8-342">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="ff0e8-342">Array of action objects</span></span> | <span data-ttu-id="ff0e8-343">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-343">Set of actions applicable to the current card.</span></span> <span data-ttu-id="ff0e8-344">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-344">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="ff0e8-345">Exemplo de um cartão de lista</span><span class="sxs-lookup"><span data-stu-id="ff0e8-345">Example of a list card</span></span>

<span data-ttu-id="ff0e8-346">O código a seguir mostra um exemplo de um cartão de lista:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-346">The following code shows an example of a list card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.teams.card.list",
  "content": {
    "title": "Card title",
    "items": [
      {
        "type": "file",
        "id": "https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx",
        "title": "Report",
        "subtitle": "teams > new > design",
        "tap": {
          "type": "imBack",
          "value": "editOnline https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx"
        }
      },
      {
        "type": "resultItem",
        "icon": "https://cdn2.iconfinder.com/data/icons/social-icons-33/128/Trello-128.png",
        "title": "Trello title",
        "subtitle": "A Trello subtitle",
        "tap": {
          "type": "openUrl",
          "value": "http://trello.com"
        }
      },
      {
        "type": "section",
        "title": "Manager"
      },
      {
        "type": "person",
        "id": "JohnDoe@contoso.com",
        "title": "John Doe",
        "subtitle": "Manager",
        "tap": {
          "type": "imBack",
          "value": "whois JohnDoe@contoso.com"
        }
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Select",
        "value": "whois"
      }
    ]
  }
}
```

## <a name="office-365-connector-card"></a><span data-ttu-id="ff0e8-347">Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="ff0e8-347">Office 365 connector card</span></span>

<span data-ttu-id="ff0e8-348">Você pode trabalhar com um cartão Office 365 Conector que fornece um layout flexível e é uma ótima maneira de obter informações úteis.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-348">You can work with an Office 365 Connector card that provides a flexible layout and is a great way to get useful information.</span></span> <span data-ttu-id="ff0e8-349">O Office 365 conector de usuário é compatível com Teams, não na Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-349">The Office 365 connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="ff0e8-350">Este cartão fornece um layout flexível com várias seções, campos, imagens e ações.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-350">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="ff0e8-351">Esse cartão contém um cartão conector para que possa ser usado por bots.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-351">This card contains a connector card so that it can be used by bots.</span></span> <span data-ttu-id="ff0e8-352">Para obter diferenças entre cartões de conector e o cartão Office 365 conector, consulte Informações adicionais [sobre o cartão Office 365 Connector.](#additional-information-on-the-office-365-connector-card)</span><span class="sxs-lookup"><span data-stu-id="ff0e8-352">For differences between connector cards and the Office 365 Connector card, see [Additional information on the Office 365 Connector card](#additional-information-on-the-office-365-connector-card).</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="ff0e8-353">Suporte para cartões Office 365 Conector</span><span class="sxs-lookup"><span data-stu-id="ff0e8-353">Support for Office 365 Connector cards</span></span>

<span data-ttu-id="ff0e8-354">A tabela a seguir fornece os recursos que suportam Office 365 conectores:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-354">The following table provides the features that support Office 365 Connector cards:</span></span>

| <span data-ttu-id="ff0e8-355">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-355">Bots in Teams</span></span> | <span data-ttu-id="ff0e8-356">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-356">Messaging extensions</span></span>  | <span data-ttu-id="ff0e8-357">Conectores</span><span class="sxs-lookup"><span data-stu-id="ff0e8-357">Connectors</span></span> | <span data-ttu-id="ff0e8-358">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ff0e8-358">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="ff0e8-359">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-359">✔</span></span> | <span data-ttu-id="ff0e8-360">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-360">✔</span></span> | <span data-ttu-id="ff0e8-361">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-361">✔</span></span> | <span data-ttu-id="ff0e8-362">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-362">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="ff0e8-363">Propriedades do cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="ff0e8-363">Properties of the Office 365 Connector card</span></span>

<span data-ttu-id="ff0e8-364">A tabela a seguir fornece as propriedades do cartão Office 365 conector:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-364">The following table provides the properties of the Office 365 connector card:</span></span>

| <span data-ttu-id="ff0e8-365">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ff0e8-365">Property</span></span> | <span data-ttu-id="ff0e8-366">Tipo</span><span class="sxs-lookup"><span data-stu-id="ff0e8-366">Type</span></span>  | <span data-ttu-id="ff0e8-367">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff0e8-367">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="ff0e8-368">title</span><span class="sxs-lookup"><span data-stu-id="ff0e8-368">title</span></span> | <span data-ttu-id="ff0e8-369">Rich text </span><span class="sxs-lookup"><span data-stu-id="ff0e8-369">Rich text</span></span> | <span data-ttu-id="ff0e8-370">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-370">Title of the card.</span></span> <span data-ttu-id="ff0e8-371">Máximo de duas linhas.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-371">Maximum two lines.</span></span> |
| <span data-ttu-id="ff0e8-372">summary</span><span class="sxs-lookup"><span data-stu-id="ff0e8-372">summary</span></span> | <span data-ttu-id="ff0e8-373">Rich text </span><span class="sxs-lookup"><span data-stu-id="ff0e8-373">Rich text</span></span> | <span data-ttu-id="ff0e8-374">Resumo do cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-374">Summary of the card.</span></span> <span data-ttu-id="ff0e8-375">Máximo de duas linhas.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-375">Maximum two lines.</span></span> |
| <span data-ttu-id="ff0e8-376">texto</span><span class="sxs-lookup"><span data-stu-id="ff0e8-376">text</span></span> | <span data-ttu-id="ff0e8-377">Rich text </span><span class="sxs-lookup"><span data-stu-id="ff0e8-377">Rich text</span></span> | <span data-ttu-id="ff0e8-378">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-378">Text appears under the subtitle.</span></span> <span data-ttu-id="ff0e8-379">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-379">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="ff0e8-380">themeColor</span><span class="sxs-lookup"><span data-stu-id="ff0e8-380">themeColor</span></span> | <span data-ttu-id="ff0e8-381">Cadeia de caracteres HEX</span><span class="sxs-lookup"><span data-stu-id="ff0e8-381">HEX string</span></span> | <span data-ttu-id="ff0e8-382">Cor que substitui o `accentColor` fornecido do manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-382">Color that overrides the `accentColor` provided from the application manifest.</span></span> |

### <a name="additional-information-on-the-office-365-connector-card"></a><span data-ttu-id="ff0e8-383">Informações adicionais sobre o cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="ff0e8-383">Additional information on the Office 365 Connector card</span></span>

<span data-ttu-id="ff0e8-384">Office 365 Os cartões conectores funcionam corretamente Microsoft Teams, incluindo [ `ActionCard` ações](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-384">Office 365 Connector cards function properly in Microsoft Teams, including [`ActionCard` actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="ff0e8-385">A diferença importante entre o uso de cartões de conector de um conector e o uso de cartões de conector no bot é o tratamento de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-385">The important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span> <span data-ttu-id="ff0e8-386">A tabela a seguir lista a diferença:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-386">The following table lists the difference:</span></span>

| <span data-ttu-id="ff0e8-387">Connector</span><span class="sxs-lookup"><span data-stu-id="ff0e8-387">Connector</span></span> | <span data-ttu-id="ff0e8-388">Bot</span><span class="sxs-lookup"><span data-stu-id="ff0e8-388">Bot</span></span> |
| --- | --- |
| <span data-ttu-id="ff0e8-389">O ponto de extremidade recebe a carga de cartão por meio de HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-389">The endpoint receives the card payload through HTTP POST.</span></span> | <span data-ttu-id="ff0e8-390">A ação dispara uma atividade que envia apenas a ID de ação `HttpPOST` e o corpo para o `invoke` bot.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-390">The `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>|

<span data-ttu-id="ff0e8-391">Cada cartão de conector pode exibir no máximo dez seções, e cada seção pode conter no máximo cinco imagens e cinco ações.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-391">Each connector card can display a maximum of ten sections, and each section can contain a maximum of five images and five actions.</span></span>

> [!NOTE]
> <span data-ttu-id="ff0e8-392">Quaisquer seções, imagens ou ações adicionais em uma mensagem não são exibidas.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-392">Any additional sections, images, or actions in a message do not appear.</span></span>

<span data-ttu-id="ff0e8-393">Todos os campos de texto suportam Markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-393">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="ff0e8-394">Você pode controlar quais seções usam Markdown ou HTML definindo `markdown` a propriedade em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-394">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="ff0e8-395">Por padrão, `markdown` é definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="ff0e8-395">By default, `markdown` is set to `true`.</span></span> <span data-ttu-id="ff0e8-396">Se você quiser usar HTML em vez disso, de definir `markdown` como `false` .</span><span class="sxs-lookup"><span data-stu-id="ff0e8-396">If you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="ff0e8-397">Se você especificar a `themeColor` propriedade, ela substituirá `accentColor` a propriedade no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-397">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="ff0e8-398">Para especificar o estilo de renderização `activityImage` para , você pode definir como mostrado na tabela a `activityImageType` seguir:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-398">To specify the rendering style for `activityImage`, you can set `activityImageType` as shown in the following table:</span></span>

| <span data-ttu-id="ff0e8-399">Valor</span><span class="sxs-lookup"><span data-stu-id="ff0e8-399">Value</span></span> | <span data-ttu-id="ff0e8-400">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff0e8-400">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="ff0e8-401">Padrão, `activityImage` é cortada como um círculo.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-401">Default, `activityImage` is cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="ff0e8-402">`activityImage` é exibido como um retângulo e mantém sua taxa de proporção.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-402">`activityImage` is displayed as a rectangle and retains its aspect ratio.</span></span> |

<span data-ttu-id="ff0e8-403">Para obter todos os outros detalhes sobre as propriedades do cartão do conector, consulte referência de cartão de mensagem a [ação.](/outlook/actionable-messages/card-reference)</span><span class="sxs-lookup"><span data-stu-id="ff0e8-403">For all other details about connector card properties, see [actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="ff0e8-404">As únicas propriedades de cartão de conector que Teams atualmente não suportam são as seguinte:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-404">The only connector card properties that Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="ff0e8-405">`startGroup`sempre tratado como `true` em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-405">`startGroup` always treated as `true` in Teams</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="ff0e8-406">Exemplo de um cartão Office 365 conector</span><span class="sxs-lookup"><span data-stu-id="ff0e8-406">Example of an Office 365 Connector card</span></span>

<span data-ttu-id="ff0e8-407">O código a seguir mostra um exemplo de um cartão Office 365 Connector:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-407">The following code shows an example of an Office 365 Connector card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "summary": "John Doe commented on Trello",
    "title": "Project Tango",
    "sections": [
        {
            "activityTitle": "John Doe commented",
            "activitySubtitle": "On Project Tango",
            "activityText": "\"Here are the designs\"",
            "activityImage": "http://connectorsdemo.azurewebsites.net/images/MSC12_Oscar_002.jpg"
        },
        {
            "title": "Details",
            "facts": [
                {
                    "name": "Labels",
                    "value": "Designs, redlines"
                },
                {
                    "name": "Due date",
                    "value": "Dec 7, 2016"
                },
                {
                    "name": "Attachments",
                    "value": "[final.jpg](http://connectorsdemo.azurewebsites.net/images/WIN14_Jan_04.jpg)"
                }
            ]
        },
        {
            "title": "Images",
            "images": [
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/MicrosoftSurface_024_Cafe_OH-06315_VS_R1c.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Scene_01.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Anthony_02.jpg"
                }
            ]
        }
    ],
    "potentialAction": [
        {
            "@context": "http://schema.org",
            "@type": "ViewAction",
            "name": "View in Trello",
            "target": [
                "https://trello.com/c/1101/"
            ]
        }
    ]
  }
}
```

## <a name="receipt-card"></a><span data-ttu-id="ff0e8-408">Cartão de recebimento</span><span class="sxs-lookup"><span data-stu-id="ff0e8-408">Receipt card</span></span>

<span data-ttu-id="ff0e8-409">Teams dá suporte ao cartão de recebimento.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-409">Teams supports receipt card.</span></span> <span data-ttu-id="ff0e8-410">É um cartão que permite que um bot forneça um recibo ao usuário.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-410">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="ff0e8-411">Normalmente, ele contém a lista de itens a ser incluídos no recibo, como informações fiscais e totais.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-411">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="ff0e8-412">Suporte para cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="ff0e8-412">Support for receipt cards</span></span>

<span data-ttu-id="ff0e8-413">A tabela a seguir fornece os recursos que suportam cartões de recebimento:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-413">The following table provides the features that support receipt cards:</span></span>

| <span data-ttu-id="ff0e8-414">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-414">Bots in Teams</span></span> | <span data-ttu-id="ff0e8-415">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-415">Messaging extensions</span></span>  | <span data-ttu-id="ff0e8-416">Conectores</span><span class="sxs-lookup"><span data-stu-id="ff0e8-416">Connectors</span></span> | <span data-ttu-id="ff0e8-417">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ff0e8-417">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="ff0e8-418">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-418">✔</span></span> | <span data-ttu-id="ff0e8-419">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-419">✔</span></span> | <span data-ttu-id="ff0e8-420">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-420">✖</span></span> | <span data-ttu-id="ff0e8-421">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-421">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="ff0e8-422">Exemplo de um cartão de confirmação</span><span class="sxs-lookup"><span data-stu-id="ff0e8-422">Example of a receipt card</span></span>

![Exemplo de um cartão de confirmação](~/assets/images/cards/receipt.png)

<span data-ttu-id="ff0e8-424">O código a seguir mostra um exemplo de um cartão de recebimento:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-424">The following code shows an example of a receipt card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.card.receipt",
  "content": {
    "title": "John Doe",
    "facts": [
      {
        "key": "Order Number",
        "value": "1234"
      },
      {
        "key": "Payment Method",
        "value": "VISA 5555-****"
      }
    ],
    "items": [
      {
        "title": "Data Transfer",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/traffic-manager.png"
        },
        "price": "$ 38.45",
        "quantity": "368"
      },
      {
        "title": "App Service",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/cloud-service.png"
        },
        "price": "$ 45.00",
        "quantity": "720"
      }
    ],
    "total": "$ 90.95",
    "tax": "$ 7.50",
    "buttons": [
      {
        "type": "openUrl",
        "title": "More information",
        "image": "https://account.windowsazure.com/content/6.10.1.38-.8225.160809-1618/aux-pre/images/offer-icon-freetrial.png",
        "value": "https://azure.microsoft.com/en-us/pricing/"
      }
    ]
  }
}
```

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="ff0e8-425">Informações adicionais sobre cartões de recebimento</span><span class="sxs-lookup"><span data-stu-id="ff0e8-425">Additional information on receipt cards</span></span>

<span data-ttu-id="ff0e8-426">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-426">Bot Framework reference:</span></span>

* [<span data-ttu-id="ff0e8-427">Cartão de Node.js</span><span class="sxs-lookup"><span data-stu-id="ff0e8-427">Receipt card Node.js</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="ff0e8-428">Cartão de recebimento C #</span><span class="sxs-lookup"><span data-stu-id="ff0e8-428">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="ff0e8-429">Cartão de signin</span><span class="sxs-lookup"><span data-stu-id="ff0e8-429">Signin card</span></span>

<span data-ttu-id="ff0e8-430">O cartão de Teams é semelhante ao cartão de assinatura na Estrutura de Bot, exceto que o cartão de signin no Teams suporta apenas duas ações `signin` e `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="ff0e8-430">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions `signin` and `openUrl`.</span></span>

<span data-ttu-id="ff0e8-431">A ação de signin pode ser usada de qualquer cartão Teams, não apenas o cartão de assinatura.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-431">The signin action can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="ff0e8-432">Para obter mais informações, [consulte Teams fluxo de autenticação para bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-432">For more information, see [Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="ff0e8-433">Suporte para cartões de assinatura</span><span class="sxs-lookup"><span data-stu-id="ff0e8-433">Support for signin cards</span></span>

<span data-ttu-id="ff0e8-434">A tabela a seguir fornece os recursos que suportam cartões de assinatura:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-434">The following table provides the features that support signin cards:</span></span>

| <span data-ttu-id="ff0e8-435">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-435">Bots in Teams</span></span> | <span data-ttu-id="ff0e8-436">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-436">Messaging extensions</span></span>  | <span data-ttu-id="ff0e8-437">Conectores</span><span class="sxs-lookup"><span data-stu-id="ff0e8-437">Connectors</span></span> | <span data-ttu-id="ff0e8-438">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ff0e8-438">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="ff0e8-439">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-439">✔</span></span> | <span data-ttu-id="ff0e8-440">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-440">✖</span></span> | <span data-ttu-id="ff0e8-441">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-441">✖</span></span> | <span data-ttu-id="ff0e8-442">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-442">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="ff0e8-443">Informações adicionais sobre cartões de assinatura</span><span class="sxs-lookup"><span data-stu-id="ff0e8-443">Additional information on signin cards</span></span>

<span data-ttu-id="ff0e8-444">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-444">Bot Framework reference:</span></span>

* [<span data-ttu-id="ff0e8-445">Cartão de Node.js</span><span class="sxs-lookup"><span data-stu-id="ff0e8-445">Signin card Node.js</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="ff0e8-446">Signin card C #</span><span class="sxs-lookup"><span data-stu-id="ff0e8-446">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="ff0e8-447">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="ff0e8-447">Thumbnail card</span></span>

<span data-ttu-id="ff0e8-448">Você pode trabalhar com um cartão de miniatura que é usado para enviar uma mensagem a ação simples.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-448">You can work with a thumbnail card that is used for sending a simple actionable message.</span></span> <span data-ttu-id="ff0e8-449">Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-449">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="ff0e8-450">Suporte para cartões de miniatura</span><span class="sxs-lookup"><span data-stu-id="ff0e8-450">Support for thumbnail cards</span></span>

<span data-ttu-id="ff0e8-451">A tabela a seguir fornece os recursos que suportam cartões de miniatura:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-451">The following table provides the features that support thumbnail cards:</span></span>

| <span data-ttu-id="ff0e8-452">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-452">Bots in Teams</span></span> | <span data-ttu-id="ff0e8-453">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-453">Messaging extensions</span></span>  | <span data-ttu-id="ff0e8-454">Conectores</span><span class="sxs-lookup"><span data-stu-id="ff0e8-454">Connectors</span></span> | <span data-ttu-id="ff0e8-455">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ff0e8-455">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="ff0e8-456">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-456">✔</span></span> | <span data-ttu-id="ff0e8-457">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-457">✔</span></span> | <span data-ttu-id="ff0e8-458">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-458">✖</span></span> | <span data-ttu-id="ff0e8-459">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-459">✔</span></span> |

![Exemplo de um cartão de miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="ff0e8-461">Propriedades de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="ff0e8-461">Properties of a thumbnail card</span></span>

<span data-ttu-id="ff0e8-462">A tabela a seguir fornece as propriedades de um cartão de miniatura:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-462">The following table provides the properties of a thumbnail card:</span></span>

| <span data-ttu-id="ff0e8-463">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ff0e8-463">Property</span></span> | <span data-ttu-id="ff0e8-464">Tipo</span><span class="sxs-lookup"><span data-stu-id="ff0e8-464">Type</span></span>  | <span data-ttu-id="ff0e8-465">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff0e8-465">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="ff0e8-466">title</span><span class="sxs-lookup"><span data-stu-id="ff0e8-466">title</span></span> | <span data-ttu-id="ff0e8-467">Rich text </span><span class="sxs-lookup"><span data-stu-id="ff0e8-467">Rich text</span></span> | <span data-ttu-id="ff0e8-468">Título do cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-468">Title of the card.</span></span> <span data-ttu-id="ff0e8-469">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-469">Maximum 2 lines.</span></span>|
| <span data-ttu-id="ff0e8-470">subtitle</span><span class="sxs-lookup"><span data-stu-id="ff0e8-470">subtitle</span></span> | <span data-ttu-id="ff0e8-471">Rich text </span><span class="sxs-lookup"><span data-stu-id="ff0e8-471">Rich text</span></span> | <span data-ttu-id="ff0e8-472">Legenda do cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-472">Subtitle of the card.</span></span> <span data-ttu-id="ff0e8-473">Máximo de 2 linhas.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-473">Maximum 2 lines.</span></span>|
| <span data-ttu-id="ff0e8-474">texto</span><span class="sxs-lookup"><span data-stu-id="ff0e8-474">text</span></span> | <span data-ttu-id="ff0e8-475">Rich text </span><span class="sxs-lookup"><span data-stu-id="ff0e8-475">Rich text</span></span> | <span data-ttu-id="ff0e8-476">O texto aparece sob o subtítulo.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-476">Text appears under the subtitle.</span></span> <span data-ttu-id="ff0e8-477">Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="ff0e8-477">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="ff0e8-478">images</span><span class="sxs-lookup"><span data-stu-id="ff0e8-478">images</span></span> | <span data-ttu-id="ff0e8-479">Matriz de imagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-479">Array of images</span></span> | <span data-ttu-id="ff0e8-480">Imagem exibida na parte superior do cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-480">Image displayed at the top of the card.</span></span> <span data-ttu-id="ff0e8-481">Taxa de proporção 1:1 quadrado.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-481">Aspect ratio 1:1 square.</span></span> |
| <span data-ttu-id="ff0e8-482">botões</span><span class="sxs-lookup"><span data-stu-id="ff0e8-482">buttons</span></span> | <span data-ttu-id="ff0e8-483">Matriz de objetos de ação</span><span class="sxs-lookup"><span data-stu-id="ff0e8-483">Array of action objects</span></span> | <span data-ttu-id="ff0e8-484">Conjunto de ações aplicáveis ao cartão atual.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-484">Set of actions applicable to the current card.</span></span> <span data-ttu-id="ff0e8-485">Máximo 6.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-485">Maximum 6.</span></span> |
| <span data-ttu-id="ff0e8-486">tap</span><span class="sxs-lookup"><span data-stu-id="ff0e8-486">tap</span></span> | <span data-ttu-id="ff0e8-487">Objeto Action</span><span class="sxs-lookup"><span data-stu-id="ff0e8-487">Action object</span></span> | <span data-ttu-id="ff0e8-488">Ativado quando o usuário toca no próprio cartão.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-488">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="ff0e8-489">Exemplo de um cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="ff0e8-489">Example of a thumbnail card</span></span>

<span data-ttu-id="ff0e8-490">O código a seguir mostra um exemplo de um cartão de miniatura:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-490">The following code shows an example of a thumbnail card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.card.thumbnail",
  "content": {
    "title": "Bender",
    "subtitle": "tale of a robot who dared to love",
    "text": "Bender Bending Rodríguez is a main character in the animated television series Futurama. He was created by series creators Matt Groening and David X. Cohen, and is voiced by John DiMaggio",
    "images": [
      {
        "url": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
        "alt": "Bender Rodríguez"
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Thumbs Up",
        "image": "http://moopz.com/assets_c/2012/06/emoji-thumbs-up-150-thumb-autox125-140616.jpg",
        "value": "I like it"
      },
      {
        "type": "imBack",
        "title": "Thumbs Down",
        "image": "http://yourfaceisstupid.com/wp-content/uploads/2014/08/thumbs-down.png",
        "value": "I don't like it"
      },
      {
        "type": "openUrl",
        "title": "I feel lucky",
        "image": "http://thumb9.shutterstock.com/photos/thumb_large/683806/148441982.jpg",
        "value": "https://www.bing.com/images/search?q=bender&qpvt=bender&qpvt=bender&qpvt=bender&FORM=IGRE"
      }
    ],
    "tap": {
      "type": "imBack",
      "value": "Tapped it!"
    }
  }
}
```

### <a name="additional-information"></a><span data-ttu-id="ff0e8-491">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="ff0e8-491">Additional information</span></span>

<span data-ttu-id="ff0e8-492">Referência da Estrutura de Bot:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-492">Bot Framework reference:</span></span>

* [<span data-ttu-id="ff0e8-493">Cartão de miniatura Node.js</span><span class="sxs-lookup"><span data-stu-id="ff0e8-493">Thumbnail card Node.js</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="ff0e8-494">Cartão de miniatura C #</span><span class="sxs-lookup"><span data-stu-id="ff0e8-494">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="ff0e8-495">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="ff0e8-495">Card collections</span></span>

<span data-ttu-id="ff0e8-496">Você pode trabalhar com coleções de cartões que incluem carrossel e coleções de lista.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-496">You can work with card collections that include carousel and list collections.</span></span> <span data-ttu-id="ff0e8-497">Teams dá suporte a coleções de cartões.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-497">Teams supports card collections.</span></span> <span data-ttu-id="ff0e8-498">As coleções de cartões `builder.AttachmentLayout.carousel` incluem `builder.AttachmentLayout.list` e .</span><span class="sxs-lookup"><span data-stu-id="ff0e8-498">Card collections include `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="ff0e8-499">Essas coleções contêm cartões adaptáveis, herois ou miniaturas.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-499">These collections contain Adaptive, hero, or thumbnail cards.</span></span>

### <a name="carousel-collection"></a><span data-ttu-id="ff0e8-500">Coleção Carousel</span><span class="sxs-lookup"><span data-stu-id="ff0e8-500">Carousel collection</span></span>

<span data-ttu-id="ff0e8-501">O [layout do carrossel](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-501">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

#### <a name="support-for-carousel-collections"></a><span data-ttu-id="ff0e8-502">Suporte para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="ff0e8-502">Support for carousel collections</span></span>

<span data-ttu-id="ff0e8-503">A tabela a seguir fornece os recursos que suportam coleções de carrossel:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-503">The following table provides the features that support carousel collections:</span></span>

| <span data-ttu-id="ff0e8-504">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-504">Bots in Teams</span></span> | <span data-ttu-id="ff0e8-505">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-505">Messaging extensions</span></span>  | <span data-ttu-id="ff0e8-506">Conectores</span><span class="sxs-lookup"><span data-stu-id="ff0e8-506">Connectors</span></span> | <span data-ttu-id="ff0e8-507">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ff0e8-507">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="ff0e8-508">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-508">✔</span></span> | <span data-ttu-id="ff0e8-509">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-509">✖</span></span> | <span data-ttu-id="ff0e8-510">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-510">✖</span></span> | <span data-ttu-id="ff0e8-511">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-511">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="ff0e8-512">Um carrossel pode exibir no máximo dez cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-512">A carousel can display a maximum of ten cards per message.</span></span>

#### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="ff0e8-513">Propriedades de um cartão de carrossel</span><span class="sxs-lookup"><span data-stu-id="ff0e8-513">Properties of a carousel card</span></span>

<span data-ttu-id="ff0e8-514">As propriedades de um cartão de carrossel são as mesmas que as de herói e miniatura.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-514">Properties of a carousel card are same as the hero and thumbnail cards.</span></span>

#### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="ff0e8-515">Exemplo de uma coleção de carrossel</span><span class="sxs-lookup"><span data-stu-id="ff0e8-515">Example of a carousel collection</span></span>

![Exemplo de um carrossel de cartões](~/assets/images/cards/carousel.png)

<span data-ttu-id="ff0e8-517">O código a seguir mostra um exemplo de uma coleção de carrossel:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-517">The following code shows an example of a carousel collection:</span></span>

```json
{
 "attachmentLayout": "carousel",
 "attachments":[
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "extraLarge",
                "weight": "bolder",
                "text": "Welcome to Employee Connect",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "size": "medium",
                "weight": "bolder",
                "text": "Add events to your calendar",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "The bot can send \r\rnotification to remind \r\ryou about the latest \r\revents and trainings.",
                "wrap": true,
                "height": "stretch"
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.2",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee connect"
              },
              {
                "type": "TextBlock",
                "text": "The bot can send notifications \r\rto remind you about the latest \r\r events and trainings",
                "wrap": true,
                "maxWidth": 2
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee Connect final"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Create and manage your tasks",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "text": "The app identifies all your pending tasks \r\r and helps you manage everything at \r\r one place.",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Try these commands \r\r- Pending Submissions \r\r- Pending Approvals- My Tools",
                "wrap": true,
                "height": "stretch"
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    }
  ]
}
```

#### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="ff0e8-518">Sintaxe para coleções de carrossel</span><span class="sxs-lookup"><span data-stu-id="ff0e8-518">Syntax for carousel collections</span></span>

<span data-ttu-id="ff0e8-519">`builder.AttachmentLayoutTypes.Carousel` é a sintaxe para coleções de carrossel.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-519">`builder.AttachmentLayoutTypes.Carousel` is the syntax for carousel collections.</span></span>

### <a name="list-collection"></a><span data-ttu-id="ff0e8-520">Coleção List</span><span class="sxs-lookup"><span data-stu-id="ff0e8-520">List collection</span></span>

<span data-ttu-id="ff0e8-521">O layout da lista mostra uma lista verticalmente empilhada de cartões, opcionalmente com botões de ação associados.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-521">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

#### <a name="support-for-list-collections"></a><span data-ttu-id="ff0e8-522">Suporte para coleções de lista</span><span class="sxs-lookup"><span data-stu-id="ff0e8-522">Support for list collections</span></span>

<span data-ttu-id="ff0e8-523">A tabela a seguir fornece os recursos que suportam coleções de lista:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-523">The following table provides the features that support list collections:</span></span>

| <span data-ttu-id="ff0e8-524">Bots em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-524">Bots in Teams</span></span> | <span data-ttu-id="ff0e8-525">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ff0e8-525">Messaging extensions</span></span>  | <span data-ttu-id="ff0e8-526">Conectores</span><span class="sxs-lookup"><span data-stu-id="ff0e8-526">Connectors</span></span> | <span data-ttu-id="ff0e8-527">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ff0e8-527">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="ff0e8-528">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-528">✔</span></span> | <span data-ttu-id="ff0e8-529">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-529">✔</span></span> | <span data-ttu-id="ff0e8-530">✖</span><span class="sxs-lookup"><span data-stu-id="ff0e8-530">✖</span></span> | <span data-ttu-id="ff0e8-531">✔</span><span class="sxs-lookup"><span data-stu-id="ff0e8-531">✔</span></span> |

#### <a name="example-of-a-list-collection"></a><span data-ttu-id="ff0e8-532">Exemplo de uma coleção de listas</span><span class="sxs-lookup"><span data-stu-id="ff0e8-532">Example of a list collection</span></span>

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

<span data-ttu-id="ff0e8-534">As propriedades das coleções de lista são as mesmas que os cartões de miniatura ou herói.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-534">Properties of list collections are same as the hero or thumbnail cards.</span></span>

<span data-ttu-id="ff0e8-535">Uma lista pode exibir no máximo dez cartões por mensagem.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-535">A list can display a maximum of ten cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="ff0e8-536">Algumas combinações de cartões de lista ainda não são suportadas no iOS e no Android.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-536">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

#### <a name="syntax-for-list-collections"></a><span data-ttu-id="ff0e8-537">Sintaxe para coleções de lista</span><span class="sxs-lookup"><span data-stu-id="ff0e8-537">Syntax for list collections</span></span>

<span data-ttu-id="ff0e8-538">`builder.AttachmentLayout.list` é a sintaxe para coleções de lista.</span><span class="sxs-lookup"><span data-stu-id="ff0e8-538">`builder.AttachmentLayout.list` is the syntax for list collections.</span></span>

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="ff0e8-539">Cartões não suportados em Teams</span><span class="sxs-lookup"><span data-stu-id="ff0e8-539">Cards not supported in Teams</span></span>

<span data-ttu-id="ff0e8-540">Os cartões a seguir são implementados pela Estrutura de Bot, mas não são suportados por Teams:</span><span class="sxs-lookup"><span data-stu-id="ff0e8-540">The following cards are implemented by the Bot Framework, but are not supported by Teams:</span></span>

* <span data-ttu-id="ff0e8-541">Cartões de animação</span><span class="sxs-lookup"><span data-stu-id="ff0e8-541">Animation cards</span></span>
* <span data-ttu-id="ff0e8-542">Cartões de áudio</span><span class="sxs-lookup"><span data-stu-id="ff0e8-542">Audio cards</span></span>
* <span data-ttu-id="ff0e8-543">Cartões de vídeo</span><span class="sxs-lookup"><span data-stu-id="ff0e8-543">Video cards</span></span>

## <a name="see-also"></a><span data-ttu-id="ff0e8-544">Confira também</span><span class="sxs-lookup"><span data-stu-id="ff0e8-544">See also</span></span>

* [<span data-ttu-id="ff0e8-545">Módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="ff0e8-545">Task modules</span></span>](~/task-modules-and-cards/what-are-task-modules.md)
* [<span data-ttu-id="ff0e8-546">Formatar cartões</span><span class="sxs-lookup"><span data-stu-id="ff0e8-546">Format cards</span></span>](~/task-modules-and-cards/cards/cards-format.md)
