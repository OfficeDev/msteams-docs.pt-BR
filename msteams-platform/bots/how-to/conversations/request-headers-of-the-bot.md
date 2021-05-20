---
title: Envie iD de inquilino e ID de conversação para os cabeçalhos de solicitação do bot
description: descreve como enviar id de inquilino e ID de conversação para os cabeçalhos de solicitação do bot.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 76f667453114ab202d43217b9a4c01a6d14cc1a8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565890"
---
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a>Envie iD de inquilino e ID de conversação para os cabeçalhos de solicitação do bot

As solicitações de saída atuais para o bot não contêm no cabeçalho ou URL qualquer informação que ajude os bots a rotear o tráfego sem desempacotar toda a carga útil. As atividades são enviadas ao bot através de uma URL semelhante a https://<your_domain>/api/messages. Solicitações são recebidas para mostrar o ID de conversação e o ID do inquilino nos cabeçalhos.

## <a name="request-header-fields"></a>Solicitar campos de cabeçalho

Dois campos de cabeçalho de solicitação não padrão são adicionados a todas as solicitações enviadas aos bots, tanto para fluxo assíncrono quanto para fluxo síncrocro. A tabela a seguir fornece os campos de cabeçalho de solicitação e seus valores:

| Chave de campo | Valor |
|----------------|-----------------|
| x-ms-conversation-id | O ID de conversação correspondente à atividade de solicitação, se aplicável e confirmado ou verificado. |
| x-ms-inquilino-id | O ID do inquilino correspondente à conversa na atividade de solicitação. |

Se o inquilino ou id de conversação não estiver presente na atividade ou não tiver sido validado no lado do serviço, o valor está vazio.

![Solicitar campos de cabeçalho](~/assets/images/bots/requestheaderfields.png)
