---
title: Criando notificações de feed de atividades
author: heath-hamilton
description: 'Saiba como criar notificações do feed de atividades para seu aplicativo do Teams e obter o Kit de Interface do Usuário do Teams. Desenvolver notificações do canal do Teams no Visual Studio C #'
ms.localizationpriority: medium
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 923519965b5ae6debaf256032f9bc4cdaada2f6e
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558006"
---
# <a name="designing-activity-feed-notifications-for-your-microsoft-teams-app"></a>Criando notificações do feed de atividades para seu aplicativo Microsoft Teams

O feed de atividades é uma superfície para que os usuários acessem suas notificações no Microsoft Teams. O feed retém notificações das últimas quatro semanas.

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-overview.png" alt-text="O exemplo mostra uma notificação de aplicativo exibida no feed de atividades do Teams no celular.":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/desktop-overview.png" alt-text="O exemplo mostra uma notificação de aplicativo exibida no feed de atividades do Teams.":::

---

## <a name="anatomy"></a>Anatomia

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-anatomy.png" alt-text="Crie a anatomia da notificação do feed de atividades do Teams.":::

|Contador|Descrição|
|----------|-----------|
|1|**Avatar**: mostra quem iniciou a atividade.|
|2|**Ícone do tipo de atividade/aplicativo**: representa o tipo de atividade. Para notificações de aplicativo, o ícone de linha é substituído por um ícone de aplicativo.|
|3|**Título (primeira linha): Ator + motivo**: *Ator*: Nome do usuário ou aplicativo que iniciou a atividade. *Motivo*: descreve a atividade.|
|4|**Carimbo de data/** hora: mostra quando a atividade ocorreu.|
|5|**Local (segunda linha)**: mostra onde a atividade ocorreu no Teams.|
|6 |**Visualização de texto (terceira linha)**: mostra uma linha truncada desde o início da notificação.|

## <a name="types-of-activity-feed-notification-cards"></a>Tipos de cartões de notificação do feed de atividades

As variantes a seguir mostram os tipos de cartões de notificação do feed de atividades que você pode exibir. O logotipo do aplicativo substitui o avatar do usuário para notificações geradas pelo aplicativo.

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-types.png" alt-text="Variantes de cartões de feed de atividades do Teams.":::

## <a name="manage-activity-feed-notifications"></a>Gerenciar notificações do feed de atividades

Os usuários podem gerenciar notificações enviadas de seu aplicativo na página de configurações do Teams.

## <a name="related-system-notifications"></a>Notificações do sistema relacionadas

Cada atividade gera uma notificação do sistema. O que é exibido depende do que o usuário define em suas configurações de notificação. Os usuários também podem escolher um estilo de notificação com base em seu sistema operacional.

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-related-system-notifications.png" alt-text="Variantes de cartões de feed de atividades do Teams no Android e iOS.":::

|Contador|Descrição|
|----------|-----------|
|1|Android|
|2|iOS|

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/related-system-notifications.png" alt-text="Variantes de cartões de atividades do Teams em sistemas operacionais diferentes.":::

|Contador|Descrição|
|----------|-----------|
|1|Personalizado do Teams|
|2|Windows|
|3|Mac|

---

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Implementar notificações do feed de atividades](/graph/teams-send-activityfeednotifications)
