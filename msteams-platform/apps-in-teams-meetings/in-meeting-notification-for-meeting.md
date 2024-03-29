---
title: Criar notificação em reunião para a reunião do Teams
author: v-sdhakshina
description: Neste artigo, saiba como criar uma notificação em reunião para a reunião do Microsoft Teams e seu exemplo de código.
ms.topic: conceptual
ms.author: v-sdhakshina
ms.localizationpriority: medium
ms.openlocfilehash: e62958535fa1bcbcdeb104b5fd5fdd2882250aa3
ms.sourcegitcommit: 372aade09e62ac7e5936215173a6632fbb042c9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2022
ms.locfileid: "68699126"
---
# <a name="build-in-meeting-notification-for-teams-meeting"></a>Criar notificação em reunião para a reunião do Teams

A notificação em reunião é usada para envolver os participantes e coletar informações ou comentários durante a reunião. Use uma [carga de notificação na reunião](meeting-apps-apis.md#send-an-in-meeting-notification) para disparar uma notificação na reunião. Como parte da solicitação de carga de notificação, inclua a URL em que o conteúdo a ser mostrado está hospedado.

Uma URL de recurso externo é usada para exibir a notificação na reunião. Você pode usar o `submitTask` método para enviar dados em um chat de reunião.

:::image type="content" source="../assets/images/apps-in-meetings/in-meeting-dialogbox.png" alt-text="A captura de tela é um exemplo que mostra como você pode usar uma caixa de diálogo na reunião.":::

Você também pode adicionar a imagem de exibição do Teams e o cartão de visita do usuário à notificação de reunião com base no `onBehalfOf` token com a MRI do usuário e o nome de exibição passado em conteúdo. A seguir um exemplo de conteúdo:

```json
    {
       "type": "message",
       "text": "John Phillips assigned you a weekly todo",
       "summary": "Don't forget to meet with Marketing next week",
       "channelData": {
           onBehalfOf: [
             { 
               itemId: 0, 
               mentionType: 'person', 
               mri: context.activity.from.id, 
               displayname: context.activity.from.name 
             }
            ],
           "notification": {
           "alertInMeeting": true,
           "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
            }
        },
       "replyToId": "1493070356924"
    }
```

:::image type="content" source="../assets/images/apps-in-meetings/in-meeting-people-card.png" alt-text="Esta captura de tela mostra como a imagem do Teams e o cartão de pessoas são usados com a caixa de diálogo na reunião." border="true":::

## <a name="code-sample"></a>Exemplo de código

Nome do exemplo | Descrição | C# | Node.js |
|----------------|-----------------|--------------|----------------|
| Notificação na reunião | Demonstra como implementar a notificação em reunião usando o bot. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs) |

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo](../sbs-meeting-content-bubble.yml) para gerar uma notificação em reunião na reunião do Teams.

## <a name="see-also"></a>Confira também

* [Criar guias para reunião](~/apps-in-teams-meetings/build-tabs-for-meeting.md)
* [Criar aplicativos para o estágio de reunião do Teams](build-apps-for-teams-meeting-stage.md)
* [Criar conversa extensível para chat de reunião](build-extensible-conversation-for-meeting-chat.md)
* [Criar aplicativos para usuários anônimos](build-apps-for-anonymous-user.md)
* [APIs de reunião avançadas](meeting-apps-apis.md)
