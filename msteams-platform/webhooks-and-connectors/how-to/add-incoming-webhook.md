---
title: Criar um Webhook de entrada
author: laujan
description: descreve como adicionar o Webhook de entrada ao Teams aplicativo e postar solicitações externas para Teams com webhooks de entrada
keywords: teams tabs outgoing webhook
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 53fe9725148579325386fa4677bebb61fdb72c56
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140095"
---
# <a name="create-incoming-webhook"></a><span data-ttu-id="1e91c-104">Criar Webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="1e91c-104">Create Incoming Webhook</span></span>

<span data-ttu-id="1e91c-105">O Webhook de entrada permite que todos os aplicativos externos compartilhem conteúdo em Teams canais.</span><span class="sxs-lookup"><span data-stu-id="1e91c-105">Incoming Webhook allows any external apps to share content in Teams channels.</span></span> <span data-ttu-id="1e91c-106">Esses webhooks são usados como ferramentas de rastreamento e notificação.</span><span class="sxs-lookup"><span data-stu-id="1e91c-106">These webhooks are used as tracking and notifying tools.</span></span> <span data-ttu-id="1e91c-107">Eles fornecem uma URL exclusiva, para a qual você envia uma carga JSON com uma mensagem no formato de cartão.</span><span class="sxs-lookup"><span data-stu-id="1e91c-107">They provide a unique URL, to which you send a JSON payload with a message in card format.</span></span> <span data-ttu-id="1e91c-108">Os cartões são contêineres de interface do usuário que incluem conteúdo e ações relacionadas a um único tópico.</span><span class="sxs-lookup"><span data-stu-id="1e91c-108">Cards are user interface containers that include content and actions related to a single topic.</span></span> <span data-ttu-id="1e91c-109">Teams cartões nos seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="1e91c-109">Teams use cards within the following capabilities:</span></span>

* <span data-ttu-id="1e91c-110">Bots</span><span class="sxs-lookup"><span data-stu-id="1e91c-110">Bots</span></span>
* <span data-ttu-id="1e91c-111">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1e91c-111">Messaging extensions</span></span>
* <span data-ttu-id="1e91c-112">Conectores</span><span class="sxs-lookup"><span data-stu-id="1e91c-112">Connectors</span></span>

## <a name="key-features-of-incoming-webhook"></a><span data-ttu-id="1e91c-113">Principais recursos do Webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="1e91c-113">Key features of Incoming Webhook</span></span>

<span data-ttu-id="1e91c-114">A tabela a seguir fornece os recursos e a descrição do Webhook de entrada:</span><span class="sxs-lookup"><span data-stu-id="1e91c-114">The following table provides the features and description of Incoming Webhook:</span></span>

| <span data-ttu-id="1e91c-115">Recursos</span><span class="sxs-lookup"><span data-stu-id="1e91c-115">Features</span></span> | <span data-ttu-id="1e91c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e91c-116">Description</span></span> |
| ------- | ----------- |
|<span data-ttu-id="1e91c-117">Cartões adaptáveis usando um Webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="1e91c-117">Adaptive Cards using an Incoming Webhook</span></span>|<span data-ttu-id="1e91c-118">Cartões adaptáveis podem ser enviados por meio de Webhooks de entrada.</span><span class="sxs-lookup"><span data-stu-id="1e91c-118">Adaptive Cards can be sent through Incoming Webhooks.</span></span> <span data-ttu-id="1e91c-119">Para obter mais informações, [consulte Send Adaptive Cards using Incoming Webhooks](../../webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook).</span><span class="sxs-lookup"><span data-stu-id="1e91c-119">For more information, see [Send Adaptive Cards using Incoming Webhooks](../../webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook).</span></span>|
|<span data-ttu-id="1e91c-120">Suporte a mensagens a ações</span><span class="sxs-lookup"><span data-stu-id="1e91c-120">Actionable messaging support</span></span>|<span data-ttu-id="1e91c-121">Os cartões de mensagem a ação são suportados em todos os grupos Office 365, incluindo Teams.</span><span class="sxs-lookup"><span data-stu-id="1e91c-121">Actionable message cards are supported in all Office 365 groups including Teams.</span></span> <span data-ttu-id="1e91c-122">Se você enviar mensagens por meio de cartões, deverá usar o formato de cartão de mensagem a ação.</span><span class="sxs-lookup"><span data-stu-id="1e91c-122">If you send messages through cards, you must use the actionable message card format.</span></span> <span data-ttu-id="1e91c-123">Para obter mais informações, consulte [referência de cartão de mensagem a actionable herdado](/outlook/actionable-messages/message-card-reference) e playground de cartão de [mensagem](https://messagecardplayground.azurewebsites.net).</span><span class="sxs-lookup"><span data-stu-id="1e91c-123">For more information, see [legacy actionable message card reference](/outlook/actionable-messages/message-card-reference) and [message card playground](https://messagecardplayground.azurewebsites.net).</span></span>|
|<span data-ttu-id="1e91c-124">Suporte independente de mensagens HTTPS</span><span class="sxs-lookup"><span data-stu-id="1e91c-124">Independent HTTPS messaging support</span></span>|<span data-ttu-id="1e91c-125">Os cartões fornecem informações de forma clara e consistente.</span><span class="sxs-lookup"><span data-stu-id="1e91c-125">Cards provide information clearly and consistently.</span></span> <span data-ttu-id="1e91c-126">Qualquer ferramenta ou estrutura que possa enviar solicitações HTTPS POST, pode enviar mensagens para Teams por meio de um Webhook de entrada.</span><span class="sxs-lookup"><span data-stu-id="1e91c-126">Any tool or framework that can send HTTPS POST requests, can send messages to Teams through an Incoming Webhook.</span></span>|
|<span data-ttu-id="1e91c-127">Suporte a markdown</span><span class="sxs-lookup"><span data-stu-id="1e91c-127">Markdown support</span></span>|<span data-ttu-id="1e91c-128">Todos os campos de texto em cartões de mensagens a ação suportam Markdown básico.</span><span class="sxs-lookup"><span data-stu-id="1e91c-128">All text fields in actionable messaging cards support basic Markdown.</span></span> <span data-ttu-id="1e91c-129">Não use marcação HTML em seus cartões.</span><span class="sxs-lookup"><span data-stu-id="1e91c-129">Do not use HTML markup in your cards.</span></span> <span data-ttu-id="1e91c-130">O HTML será ignorado e tratado como texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="1e91c-130">HTML is ignored and treated as plain text.</span></span>|
|<span data-ttu-id="1e91c-131">Configuração com escopo</span><span class="sxs-lookup"><span data-stu-id="1e91c-131">Scoped configuration</span></span>|<span data-ttu-id="1e91c-132">O Webhook de entrada tem escopo e configuração no nível do canal.</span><span class="sxs-lookup"><span data-stu-id="1e91c-132">Incoming Webhook is scoped and configured at the channel level.</span></span>|
|<span data-ttu-id="1e91c-133">Definições de recursos seguros</span><span class="sxs-lookup"><span data-stu-id="1e91c-133">Secure resource definitions</span></span>|<span data-ttu-id="1e91c-134">As mensagens são formatadas como cargas JSON.</span><span class="sxs-lookup"><span data-stu-id="1e91c-134">Messages are formatted as JSON payloads.</span></span> <span data-ttu-id="1e91c-135">Essa estrutura declarativa de mensagens impede a inserção de código mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="1e91c-135">This declarative messaging structure prevents the insertion of malicious code.</span></span>|

> [!NOTE]
> * <span data-ttu-id="1e91c-136">Teams bots, extensões de mensagens, Webhook de entrada e a Estrutura de Bot suportam Cartões Adaptáveis, uma estrutura de plataforma de cartão cruzado aberta.</span><span class="sxs-lookup"><span data-stu-id="1e91c-136">Teams bots, messaging extensions, Incoming Webhook, and the Bot Framework support Adaptive Cards, an open cross card platform framework.</span></span> <span data-ttu-id="1e91c-137">Atualmente, Teams [conectores não](../../webhooks-and-connectors/how-to/connectors-creating.md) suportam Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="1e91c-137">Currently, [Teams connectors](../../webhooks-and-connectors/how-to/connectors-creating.md) do not support Adaptive Cards.</span></span> <span data-ttu-id="1e91c-138">No entanto, é possível criar um [fluxo que](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) poste Cartões Adaptáveis em um canal Teams.</span><span class="sxs-lookup"><span data-stu-id="1e91c-138">However, it is possible to create a [flow](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) that posts Adaptive Cards to a Teams channel.</span></span>
> * <span data-ttu-id="1e91c-139">Para obter mais informações sobre cartões e webhooks, consulte [Cartões adaptáveis e Webhooks de entrada.](~/task-modules-and-cards/what-are-cards.md#adaptive-cards-and-incoming-webhooks)</span><span class="sxs-lookup"><span data-stu-id="1e91c-139">For more information on cards and webhooks, see [Adaptive cards and Incoming Webhooks](~/task-modules-and-cards/what-are-cards.md#adaptive-cards-and-incoming-webhooks).</span></span>

## <a name="create-incoming-webhook"></a><span data-ttu-id="1e91c-140">Criar Webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="1e91c-140">Create Incoming Webhook</span></span>

<span data-ttu-id="1e91c-141">**Para adicionar um Webhook de entrada a um Teams canal**</span><span class="sxs-lookup"><span data-stu-id="1e91c-141">**To add an Incoming Webhook to a Teams channel**</span></span>

1. <span data-ttu-id="1e91c-142">Vá para o canal onde você deseja adicionar o webhook e selecione &#8226;&#8226;&#8226; **mais opções** na barra de navegação superior.</span><span class="sxs-lookup"><span data-stu-id="1e91c-142">Go to the channel where you want to add the webhook and select &#8226;&#8226;&#8226; **More options** from the top navigation bar.</span></span>
1. <span data-ttu-id="1e91c-143">Selecione **Conectores** no menu suspenso:</span><span class="sxs-lookup"><span data-stu-id="1e91c-143">Select **Connectors** from the dropdown menu:</span></span>

    ![Selecionar Conector](~/assets/images/connectors.png)

1. <span data-ttu-id="1e91c-145">Pesquise **o Webhook de entrada** e selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="1e91c-145">Search for **Incoming Webhook** and select **Add**.</span></span>
1. <span data-ttu-id="1e91c-146">Selecione **Configurar**, forneça um nome e carregue uma imagem para seu webhook, se necessário:</span><span class="sxs-lookup"><span data-stu-id="1e91c-146">Select **Configure**, provide a name, and upload an image for your webhook if required:</span></span>

    ![Botão Configurar](~/assets/images/configure.png)

1. <span data-ttu-id="1e91c-148">A janela de diálogo apresenta uma URL exclusiva que mapeia para o canal.</span><span class="sxs-lookup"><span data-stu-id="1e91c-148">The dialog window presents a unique URL that maps to the channel.</span></span> <span data-ttu-id="1e91c-149">Copie e salve a URL do webhook, para enviar informações para Microsoft Teams e selecione **Feito**:</span><span class="sxs-lookup"><span data-stu-id="1e91c-149">Copy and save the webhook URL, to send information to Microsoft Teams and select **Done**:</span></span>

    ![URL exclusiva](~/assets/images/url.png)

<span data-ttu-id="1e91c-151">O webhook está disponível no canal Teams.</span><span class="sxs-lookup"><span data-stu-id="1e91c-151">The webhook is available in the Teams channel.</span></span>

> [!NOTE]
> <span data-ttu-id="1e91c-152">Em Teams, selecione **Configurações** Permissões de membro Permitir que os membros criem, atualizem e  >    >  **removam** conectores, para que qualquer membro da equipe possa adicionar, modificar ou excluir um conector.</span><span class="sxs-lookup"><span data-stu-id="1e91c-152">In Teams, select **Settings** > **Member permissions** > **Allow members to create, update, and remove connectors**, so that any team member can add, modify, or delete a connector.</span></span>

## <a name="remove-incoming-webhook"></a><span data-ttu-id="1e91c-153">Remover Webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="1e91c-153">Remove Incoming Webhook</span></span>

<span data-ttu-id="1e91c-154">**Para remover um Webhook de entrada de um Teams canal**</span><span class="sxs-lookup"><span data-stu-id="1e91c-154">**To remove an Incoming Webhook from a Teams channel**</span></span>

1. <span data-ttu-id="1e91c-155">Vá para o canal.</span><span class="sxs-lookup"><span data-stu-id="1e91c-155">Go to the channel.</span></span>
1. <span data-ttu-id="1e91c-156">Selecione &#8226;&#8226;&#8226; **Mais opções** na barra de navegação superior.</span><span class="sxs-lookup"><span data-stu-id="1e91c-156">Select &#8226;&#8226;&#8226; **More options** from the top navigation bar.</span></span>
1. <span data-ttu-id="1e91c-157">Selecione **Conectores** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="1e91c-157">Select **Connectors** from the dropdown menu.</span></span>
1. <span data-ttu-id="1e91c-158">À esquerda, em **Gerenciar**, selecione **Configurado**.</span><span class="sxs-lookup"><span data-stu-id="1e91c-158">On the left, under **Manage**, select **Configured**.</span></span>
1. <span data-ttu-id="1e91c-159">Selecione **< *o 1>* Configurado para** ver uma lista dos conectores atuais:</span><span class="sxs-lookup"><span data-stu-id="1e91c-159">Select the **<*1*> Configured** to see a list of your current connectors:</span></span>

    ![Webhook configurado](~/assets/images/configured.png)

1. <span data-ttu-id="1e91c-161">Selecione **Gerenciar** ao lado do conector que você deseja remover:</span><span class="sxs-lookup"><span data-stu-id="1e91c-161">Select **Manage** next to the connector that you want to remove:</span></span>

    ![Gerenciar webhook](~/assets/images/manage.png)

1. <span data-ttu-id="1e91c-163">Selecione **Remover**:</span><span class="sxs-lookup"><span data-stu-id="1e91c-163">Select **Remove**:</span></span>

    ![Remover webhook](~/assets/images/remove.png)

    <span data-ttu-id="1e91c-165">A **caixa de diálogo Remover Configuração** é exibida:</span><span class="sxs-lookup"><span data-stu-id="1e91c-165">The **Remove Configuration** dialog box appears:</span></span>

    ![Remover Configuração](~/assets/images/removeconfiguration.png)

1. <span data-ttu-id="1e91c-167">Conclua os campos e caixas de seleção da caixa de diálogo e selecione **Remover**:</span><span class="sxs-lookup"><span data-stu-id="1e91c-167">Complete the dialog box fields and checkboxes and select **Remove**:</span></span>

    ![Remover Final](~/assets/images/finalremove.png)

    <span data-ttu-id="1e91c-169">O webhook é removido do Teams canal.</span><span class="sxs-lookup"><span data-stu-id="1e91c-169">The webhook is removed from the Teams channel.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e91c-170">Também consulte</span><span class="sxs-lookup"><span data-stu-id="1e91c-170">See also</span></span>

* [<span data-ttu-id="1e91c-171">Criar um Webhook de Saída</span><span class="sxs-lookup"><span data-stu-id="1e91c-171">Create an Outgoing Webhook</span></span>](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [<span data-ttu-id="1e91c-172">Criar um conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="1e91c-172">Create an Office 365 Connector</span></span>](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [<span data-ttu-id="1e91c-173">Criar e enviar mensagens</span><span class="sxs-lookup"><span data-stu-id="1e91c-173">Create and send messages</span></span>](~/webhooks-and-connectors/how-to/connectors-using.md)
