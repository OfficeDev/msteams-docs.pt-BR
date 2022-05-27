---
title: Enviar o ID do locatário e o ID da conversa para os cabeçalhos de solicitação do bot
description: Descreve como enviar o ID do locatário e o ID da conversa para os cabeçalhos de solicitação do bot.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 8aca2c11dbdfc84abe8c4d0ec40e2748d04f6301
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757287"
---
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a>Enviar o ID do locatário e o ID da conversa para os cabeçalhos de solicitação do bot

As solicitações de saída atuais para o bot não contêm no cabeçalho ou url nenhuma informação que ajude os bots a rotear o tráfego sem desempacotar todo o conteúdo. As atividades são enviadas para o bot através de uma URL semelhante a https://<sua_domínio>/api/mensagens. As solicitações são recebidas para mostrar o ID da conversa e o ID do locatário nos cabeçalhos.

## <a name="request-header-fields"></a>Campos de cabeçalho de solicitação

Dois campos de cabeçalho de solicitação não padrão são adicionados a todas as solicitações enviadas aos bots, tanto para fluxo assíncrono quanto para fluxo síncrono. A tabela a seguir fornece os campos de cabeçalho de solicitação e seus valores:

| Chave de campo | Valor |
|----------------|-----------------|
| x-ms-conversation-id | O ID da conversa correspondente à atividade de solicitação, se aplicável e confirmado ou verificado. |
| x-ms-tenant-id | O ID do locatário correspondente à conversa na atividade de solicitação. |

Se a ID do locatário ou da conversa não estiver presente na atividade ou não tiver sido validada no lado do serviço, o valor estará vazio.

![Campos de cabeçalho de solicitação](~/assets/images/bots/requestheaderfields.png)
