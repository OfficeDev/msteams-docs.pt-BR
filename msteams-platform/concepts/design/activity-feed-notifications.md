---
title: Projetando notificações de feed de atividade
author: heath-hamilton
description: 'Saiba como projetar notificações de feed de atividade para seu aplicativo Teams e obter o kit Teams interface do usuário. Desenvolver notificações do Teams no Visual Studio C #'
ms.localizationpriority: medium
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 06e6b0ed28208f9ce446a0fc037b7477a562c596
ms.sourcegitcommit: a85b4ae65b87006bb2e2e50ea902eb97291e83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64612619"
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
|2|**Tipo de atividade/ícone de aplicativo**: representa o tipo de atividade. Para notificações de aplicativo, o ícone de linha é substituído por um ícone de aplicativo.|
|3|**Título (primeira linha): Ator + motivo**: *Ator*: Nome do usuário ou aplicativo que iniciou a atividade. *Motivo*: descreve a atividade.|
|4|**Timestamp**: mostra quando a atividade aconteceu.|
|5|**Local (segunda linha)**: mostra onde a atividade ocorreu Teams.|
|6 |**Visualização de texto (terceira linha)**: mostra uma linha truncada desde o início da notificação.|

## <a name="types-of-activity-feed-notification-cards"></a>Tipos de cartões de notificação de feed de atividade

As variantes a seguir mostram os tipos de cartões de notificação de feed de atividade que você pode exibir. O logotipo do aplicativo substitui o avatar do usuário para notificações geradas pelo aplicativo.

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-types.png" alt-text="Variantes de Teams de feed de atividade." border="false":::

## <a name="manage-activity-feed-notifications"></a>Gerenciar notificações de feed de atividade

Os usuários podem gerenciar notificações enviadas de seu aplicativo na página Teams configurações.

## <a name="related-system-notifications"></a>Notificações relacionadas ao sistema

Cada atividade gera uma notificação do sistema. O que é exibido depende do que o usuário configura em suas configurações de notificação. Os usuários também podem escolher um estilo de notificação com base em seu sistema operacional.

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-related-system-notifications.png" alt-text="Variantes de Teams de feed de atividade no Android e iOS." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|Android|
|2|iOS|

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/related-system-notifications.png" alt-text="Variantes de Teams de atividade em diferentes sistemas operacionais." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|Teams personalizado|
|2|Windows|
|3|Mac|

---

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Implementar notificações de feed de atividade](/graph/teams-send-activityfeednotifications)
