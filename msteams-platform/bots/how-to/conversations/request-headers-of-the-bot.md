---
title: Enviar o ID do locatário e o ID da conversa para os cabeçalhos de solicitação do bot
description: Neste módulo, saiba como enviar a ID do locatário e a ID de conversa para os cabeçalhos de solicitação do bot Teams.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: dab795a65cf1c6d62bd899c9fa5a5948c44fcdfb
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144121"
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
