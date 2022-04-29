---
title: Enviar o ID do locatário e o ID da conversa para os cabeçalhos de solicitação do bot
description: Descreve como enviar o ID do locatário e o ID da conversa para os cabeçalhos de solicitação do bot.
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: 9b63dd81eeccbf78989a31a06baa5d678916acef
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111287"
---
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a>Enviar o ID do locatário e o ID da conversa para os cabeçalhos de solicitação do bot

As solicitações de saída atuais para o bot não contêm no cabeçalho ou URL nenhuma informação que ajude os bots a encaminhar o tráfego sem descompactar toda a carga útil. As atividades são enviadas para o bot através de uma URL semelhante a https://<sua_domínio>/api/mensagens. As solicitações são recebidas para mostrar o ID da conversa e o ID do locatário nos cabeçalhos.

## <a name="request-header-fields"></a>Campos de cabeçalho de solicitação

Dois campos de cabeçalho de solicitação não padrão são adicionados a todas as solicitações enviadas aos bots, tanto para fluxo assíncrono quanto para fluxo síncrono. A tabela a seguir fornece os campos de cabeçalho de solicitação e seus valores:

| Chave de campo | Valor |
|----------------|-----------------|
| x-ms-conversation-id | O ID da conversa correspondente à atividade de solicitação, se aplicável e confirmado ou verificado. |
| x-ms-tenant-id | O ID do locatário correspondente à conversa na atividade de solicitação. |

Se o ID do locatário ou da conversa não estiver presente na atividade ou não tiver sido validada no lado do serviço, o valor estará vazio.

![Campos de cabeçalho de solicitação](~/assets/images/bots/requestheaderfields.png)
