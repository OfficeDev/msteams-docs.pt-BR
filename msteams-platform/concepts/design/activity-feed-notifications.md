---
title: Projetando notificações de feed de atividade
author: heath-hamilton
description: Saiba como projetar notificações de feed de atividade para seu aplicativo Teams e obter o kit Microsoft Teams interface do usuário.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 7bc5527a4ac849ab6a46692da85b051f86606f92
ms.sourcegitcommit: 306b6e8cb3aac8bfda10ef3999467a797d64539d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2021
ms.locfileid: "58408549"
---
# <a name="designing-activity-feed-notifications-for-your-microsoft-teams-app"></a>Projetando notificações de feed de atividade para seu Microsoft Teams app

O feed de atividades é uma superfície para que os usuários acessem suas notificações Microsoft Teams. O feed mantém notificações das últimas quatro semanas.

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-overview.png" alt-text="Exemplo mostra uma notificação de aplicativo exibida no feed Teams atividade no celular." border="false":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/desktop-overview.png" alt-text="Exemplo mostra uma notificação de aplicativo exibida no feed Teams atividade." border="false":::

---

## <a name="anatomy"></a>Anatomia

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-anatomy.png" alt-text="Projete a anatomia da notificação Teams feed de atividade." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Avatar**: mostra quem iniciou a atividade.|
|2|**Tipo de atividade/ícone de aplicativo:** representa o tipo de atividade. Para notificações de aplicativo, o ícone de linha é substituído por um ícone de aplicativo.|
|3|**Título (primeira linha): Ator + motivo**: *Ator*: Nome do usuário ou aplicativo que iniciou a atividade. *Motivo*: Descreve a atividade.|
|4 |**Timestamp**: mostra quando a atividade aconteceu.|
|5 |**Local (segunda linha)**: mostra onde a atividade aconteceu Teams.|
|6 |**Informações terciárias (terceira linha)**: Opcional. Mostra texto de visualização ou informações adicionais.|

## <a name="types-of-activity-feed-notification-cards"></a>Tipos de cartões de notificação de feed de atividade

As variantes a seguir mostram os tipos de cartões de notificação de feed de atividade que você pode exibir. O logotipo do aplicativo substitui o avatar do usuário para notificações geradas pelo aplicativo.

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-types.png" alt-text="Variantes de Teams de feed de atividade." border="false":::

## <a name="manage-activity-feed-notifications"></a>Gerenciar notificações de feed de atividade

Os usuários podem gerenciar notificações enviadas do aplicativo na página Teams configurações.

## <a name="related-system-notifications"></a>Notificações relacionadas ao sistema

Cada atividade gera uma notificação do sistema. O que é exibido depende do que o usuário configura em suas configurações de notificação. Os usuários também podem escolher um estilo de notificação com base em seu sistema operacional.

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-related-system-notifications.png" alt-text="Variantes de Teams de feed de atividade no Android e iOS." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|Android|
|2|iOS|

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/related-system-notifications.png" alt-text="Variantes de Teams de atividade em sistemas operacionais diferentes." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|Teams personalizado|
|2|Windows|
|3|Mac|

---

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Implementar notificações de feed de atividade](/graph/teams-send-activityfeednotifications)
