---
title: Enviar o ID do locatário e o ID da conversa para os cabeçalhos de solicitação do bot
description: Saiba como rotear o tráfego do bot sem desempacotar toda a carga usando a ID do locatário e a ID de conversa presentes nos cabeçalhos de solicitação do bot no Teams.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 3132d91d4b3d0b290ee8e1fb35ebeea076217fe8
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100144"
---
# <a name="request-headers-of-the-bot"></a>Solicite cabeçalhos do bot

As solicitações de saída atuais para o bot não contêm no cabeçalho ou url nenhuma informação que ajude os bots a rotear o tráfego sem desempacotar todo o conteúdo. As atividades são enviadas para o bot através de uma URL semelhante a https://<sua_domínio>/api/mensagens. As solicitações são recebidas para mostrar o ID da conversa e o ID do locatário nos cabeçalhos.

## <a name="request-header-fields"></a>Campos de cabeçalho de solicitação

Dois campos de cabeçalho de solicitação não padrão são adicionados a todas as solicitações enviadas aos bots, tanto para fluxo assíncrono quanto para fluxo síncrono. A tabela a seguir fornece os campos de cabeçalho de solicitação e seus valores:

| Chave de campo | Valor |
|----------------|-----------------|
| x-ms-conversation-id | O ID da conversa correspondente à atividade de solicitação, se aplicável e confirmado ou verificado. |
| x-ms-tenant-id | O ID do locatário correspondente à conversa na atividade de solicitação. |

Se a ID do locatário ou da conversa não estiver presente na atividade ou não tiver sido validada no lado do serviço, o valor estará vazio.

![Campos de cabeçalho de solicitação](~/assets/images/bots/requestheaderfields.png)
