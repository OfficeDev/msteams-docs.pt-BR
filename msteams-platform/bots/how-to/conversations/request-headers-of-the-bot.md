---
title: Enviar ID de locatário e ID de conversa para os headers de solicitação do bot
description: descreve como enviar a ID do locatário e a ID da conversa para os headers de solicitação do bot.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: b3938b3011e09016f8594b2b17ba627d4922947b
ms.sourcegitcommit: 35bc2a31b92f3f7c6524373108f095a870d9ad09
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51922521"
---
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a>Enviar ID de locatário e ID de conversa para os headers de solicitação do bot

As solicitações de saída atuais para o bot não contêm no header ou url informações que ajudam os bots a rotear o tráfego sem desempacotar toda a carga. As atividades são enviadas para o bot por meio de uma URL semelhante a https://<your_domain>/api/messages. As solicitações são recebidas para mostrar a ID da conversa e a ID do locatário nos headers.

## <a name="request-header-fields"></a>Solicitar campos de header

Dois campos de header de solicitação não padrão são adicionados a todas as solicitações enviadas aos bots, para fluxo assíncrono e fluxo síncrono. A tabela a seguir fornece os campos de header de solicitação e seus valores.

| Chave de campo | Valor |
|----------------|-----------------|
| x-ms-conversation-id | A ID da conversa correspondente à atividade de solicitação, se aplicável e confirmado ou verificado. |
| x-ms-tenant-id | A ID do locatário correspondente à conversa na atividade de solicitação. |

Se o locatário ou a ID da conversa não estiver presente na atividade ou não tiver sido validado no lado do serviço, o valor estará vazio.

![Solicitar campos de header](~/assets/images/bots/requestheaderfields.png)
