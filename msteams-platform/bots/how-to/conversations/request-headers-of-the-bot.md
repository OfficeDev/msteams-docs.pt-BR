---
title: Enviar o ID do locatário e o ID da conversa para os cabeçalhos de solicitação do bot
description: Neste módulo, saiba como enviar a ID do locatário e a ID de conversa para os cabeçalhos de solicitação do bot no Teams.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: b292db11ced764bbe235bee0f6f8f4829ba7b6c9
ms.sourcegitcommit: ffc57e128f0ae21ad2144ced93db7c78a5ae25c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66503771"
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
