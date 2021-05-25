---
title: Projetando notificações de feed de atividade
author: heath-hamilton
description: Saiba como projetar notificações de feed de atividade para seu aplicativo Teams e obter o kit Microsoft Teams interface do usuário.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 61a2a6da2a5ed0cb3126b9798094b06c575c9b6c
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631221"
---
# <a name="designing-activity-feed-notifications-for-your-microsoft-teams-app"></a><span data-ttu-id="1c0d8-103">Projetando notificações de feed de atividade para seu Microsoft Teams app</span><span class="sxs-lookup"><span data-stu-id="1c0d8-103">Designing activity feed notifications for your Microsoft Teams app</span></span>

<span data-ttu-id="1c0d8-104">O feed de atividades é uma superfície para que os usuários acessem suas notificações Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-104">The activity feed is a surface for users to access their notifications in Microsoft Teams.</span></span> <span data-ttu-id="1c0d8-105">O feed mantém notificações das últimas quatro semanas.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-105">The feed retains notifications from the past four weeks.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="1c0d8-106">Desktop</span><span class="sxs-lookup"><span data-stu-id="1c0d8-106">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/desktop-overview.png" alt-text="Exemplo mostra uma notificação de aplicativo exibida no feed Teams atividade." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="1c0d8-108">Mobile</span><span class="sxs-lookup"><span data-stu-id="1c0d8-108">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-overview.png" alt-text="Exemplo mostra uma notificação de aplicativo exibida no feed Teams atividade no celular." border="false":::

---

## <a name="anatomy"></a><span data-ttu-id="1c0d8-110">Anatomia</span><span class="sxs-lookup"><span data-stu-id="1c0d8-110">Anatomy</span></span>

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-anatomy.png" alt-text="Projete a anatomia da notificação Teams feed de atividade." border="false":::

|<span data-ttu-id="1c0d8-112">Contador</span><span class="sxs-lookup"><span data-stu-id="1c0d8-112">Counter</span></span>|<span data-ttu-id="1c0d8-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c0d8-113">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="1c0d8-114">1</span><span class="sxs-lookup"><span data-stu-id="1c0d8-114">1</span></span>|<span data-ttu-id="1c0d8-115">**Avatar**: mostra quem iniciou a atividade.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-115">**Avatar**: Shows who initiated the activity.</span></span>|
|<span data-ttu-id="1c0d8-116">2</span><span class="sxs-lookup"><span data-stu-id="1c0d8-116">2</span></span>|<span data-ttu-id="1c0d8-117">**Tipo de atividade/ícone de aplicativo:** representa o tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-117">**Activity type/app icon**: Depicts the type of activity.</span></span> <span data-ttu-id="1c0d8-118">Para notificações de aplicativo, o ícone de linha é substituído por um ícone de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-118">For app notifications, the line icon is replaced with an app icon.</span></span>|
|<span data-ttu-id="1c0d8-119">3</span><span class="sxs-lookup"><span data-stu-id="1c0d8-119">3</span></span>|<span data-ttu-id="1c0d8-120">**Título (primeira linha): Ator + motivo**: *Ator*: Nome do usuário ou aplicativo que iniciou a atividade.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-120">**Title (first line): Actor + reason**: *Actor*: Name of the user or app that initiated the activity.</span></span> <span data-ttu-id="1c0d8-121">*Motivo*: Descreve a atividade.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-121">*Reason*: Describes the activity.</span></span>|
|<span data-ttu-id="1c0d8-122">4 </span><span class="sxs-lookup"><span data-stu-id="1c0d8-122">4</span></span>|<span data-ttu-id="1c0d8-123">**Timestamp**: mostra quando a atividade aconteceu.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-123">**Timestamp**: Shows when the activity happened.</span></span>|
|<span data-ttu-id="1c0d8-124">5 </span><span class="sxs-lookup"><span data-stu-id="1c0d8-124">5</span></span>|<span data-ttu-id="1c0d8-125">**Local (segunda linha)**: mostra onde a atividade aconteceu Teams.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-125">**Location (second line)**: Shows where the activity happened in Teams.</span></span>|
|<span data-ttu-id="1c0d8-126">6 </span><span class="sxs-lookup"><span data-stu-id="1c0d8-126">6</span></span>|<span data-ttu-id="1c0d8-127">**Informações terciárias (terceira linha)**: Opcional.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-127">**Tertiary information (third line)**: Optional.</span></span> <span data-ttu-id="1c0d8-128">Mostra texto de visualização ou informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-128">Shows preview text or additional information.</span></span>|

## <a name="types-of-activity-feed-notification-cards"></a><span data-ttu-id="1c0d8-129">Tipos de cartões de notificação de feed de atividade</span><span class="sxs-lookup"><span data-stu-id="1c0d8-129">Types of activity feed notification cards</span></span>

<span data-ttu-id="1c0d8-130">As variantes a seguir mostram os tipos de cartões de notificação de feed de atividade que você pode exibir.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-130">The following variants show the kinds of activity feed notification cards you can display.</span></span> <span data-ttu-id="1c0d8-131">O logotipo do aplicativo substitui o avatar do usuário para notificações geradas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-131">The app logo replaces the user avatar for app-generated notifications.</span></span>

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-types.png" alt-text="Variantes de Teams de feed de atividade." border="false":::

## <a name="manage-activity-feed-notifications"></a><span data-ttu-id="1c0d8-133">Gerenciar notificações de feed de atividade</span><span class="sxs-lookup"><span data-stu-id="1c0d8-133">Manage activity feed notifications</span></span>

<span data-ttu-id="1c0d8-134">Os usuários podem gerenciar notificações enviadas do aplicativo na página Teams configurações.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-134">Users can manage notifications sent from your app in the Teams settings page.</span></span>

## <a name="related-system-notifications"></a><span data-ttu-id="1c0d8-135">Notificações relacionadas ao sistema</span><span class="sxs-lookup"><span data-stu-id="1c0d8-135">Related system notifications</span></span>

<span data-ttu-id="1c0d8-136">Cada atividade gera uma notificação do sistema.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-136">Each activity generates a system notification.</span></span> <span data-ttu-id="1c0d8-137">O que é exibido depende do que o usuário configura em suas configurações de notificação.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-137">What displays depends on what the user configures in their notification settings.</span></span> <span data-ttu-id="1c0d8-138">Os usuários também podem escolher um estilo de notificação com base em seu sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="1c0d8-138">Users can also choose a notification style based on their operating system.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="1c0d8-139">Desktop</span><span class="sxs-lookup"><span data-stu-id="1c0d8-139">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/related-system-notifications.png" alt-text="Variantes de Teams de atividade em sistemas operacionais diferentes." border="false":::

|<span data-ttu-id="1c0d8-141">Contador</span><span class="sxs-lookup"><span data-stu-id="1c0d8-141">Counter</span></span>|<span data-ttu-id="1c0d8-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c0d8-142">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="1c0d8-143">1</span><span class="sxs-lookup"><span data-stu-id="1c0d8-143">1</span></span>|<span data-ttu-id="1c0d8-144">Teams personalizado</span><span class="sxs-lookup"><span data-stu-id="1c0d8-144">Teams custom</span></span>|
|<span data-ttu-id="1c0d8-145">2</span><span class="sxs-lookup"><span data-stu-id="1c0d8-145">2</span></span>|<span data-ttu-id="1c0d8-146">Windows</span><span class="sxs-lookup"><span data-stu-id="1c0d8-146">Windows</span></span>|
|<span data-ttu-id="1c0d8-147">3</span><span class="sxs-lookup"><span data-stu-id="1c0d8-147">3</span></span>|<span data-ttu-id="1c0d8-148">Mac</span><span class="sxs-lookup"><span data-stu-id="1c0d8-148">Mac</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="1c0d8-149">Mobile</span><span class="sxs-lookup"><span data-stu-id="1c0d8-149">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-related-system-notifications.png" alt-text="Variantes de Teams de feed de atividade no Android e iOS." border="false":::

|<span data-ttu-id="1c0d8-151">Contador</span><span class="sxs-lookup"><span data-stu-id="1c0d8-151">Counter</span></span>|<span data-ttu-id="1c0d8-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c0d8-152">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="1c0d8-153">1</span><span class="sxs-lookup"><span data-stu-id="1c0d8-153">1</span></span>|<span data-ttu-id="1c0d8-154">Android</span><span class="sxs-lookup"><span data-stu-id="1c0d8-154">Android</span></span>|
|<span data-ttu-id="1c0d8-155">2</span><span class="sxs-lookup"><span data-stu-id="1c0d8-155">2</span></span>|<span data-ttu-id="1c0d8-156">iOS</span><span class="sxs-lookup"><span data-stu-id="1c0d8-156">iOS</span></span>|

---

## <a name="next-step"></a><span data-ttu-id="1c0d8-157">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="1c0d8-157">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c0d8-158">Implementar notificações de feed de atividade</span><span class="sxs-lookup"><span data-stu-id="1c0d8-158">Implement activity feed notifications</span></span>](/graph/teams-send-activityfeednotifications)
