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
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a><span data-ttu-id="fea94-103">Envie iD de inquilino e ID de conversação para os cabeçalhos de solicitação do bot</span><span class="sxs-lookup"><span data-stu-id="fea94-103">Send tenant ID and conversation ID to the request headers of the bot</span></span>

<span data-ttu-id="fea94-104">As solicitações de saída atuais para o bot não contêm no cabeçalho ou URL qualquer informação que ajude os bots a rotear o tráfego sem desempacotar toda a carga útil.</span><span class="sxs-lookup"><span data-stu-id="fea94-104">The current outgoing requests to the bot do not contain in the header or URL any information that helps bots route the traffic without unpacking the entire payload.</span></span> <span data-ttu-id="fea94-105">As atividades são enviadas ao bot através de uma URL semelhante a https://<your_domain>/api/messages.</span><span class="sxs-lookup"><span data-stu-id="fea94-105">The activities are sent to the bot through a URL similar to https://<your_domain>/api/messages.</span></span> <span data-ttu-id="fea94-106">Solicitações são recebidas para mostrar o ID de conversação e o ID do inquilino nos cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="fea94-106">Requests are received to show the conversation ID and tenant ID in the headers.</span></span>

## <a name="request-header-fields"></a><span data-ttu-id="fea94-107">Solicitar campos de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="fea94-107">Request header fields</span></span>

<span data-ttu-id="fea94-108">Dois campos de cabeçalho de solicitação não padrão são adicionados a todas as solicitações enviadas aos bots, tanto para fluxo assíncrono quanto para fluxo síncrocro.</span><span class="sxs-lookup"><span data-stu-id="fea94-108">Two non-standard request header fields are added to all the requests sent to bots, for both asynchronous flow and synchronous flow.</span></span> <span data-ttu-id="fea94-109">A tabela a seguir fornece os campos de cabeçalho de solicitação e seus valores:</span><span class="sxs-lookup"><span data-stu-id="fea94-109">The following table provides the request header fields and their values:</span></span>

| <span data-ttu-id="fea94-110">Chave de campo</span><span class="sxs-lookup"><span data-stu-id="fea94-110">Field key</span></span> | <span data-ttu-id="fea94-111">Valor</span><span class="sxs-lookup"><span data-stu-id="fea94-111">Value</span></span> |
|----------------|-----------------|
| <span data-ttu-id="fea94-112">x-ms-conversation-id</span><span class="sxs-lookup"><span data-stu-id="fea94-112">x-ms-conversation-id</span></span> | <span data-ttu-id="fea94-113">O ID de conversação correspondente à atividade de solicitação, se aplicável e confirmado ou verificado.</span><span class="sxs-lookup"><span data-stu-id="fea94-113">The conversation ID corresponding to the request activity if applicable and confirmed or verified.</span></span> |
| <span data-ttu-id="fea94-114">x-ms-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="fea94-114">x-ms-tenant-id</span></span> | <span data-ttu-id="fea94-115">O ID do inquilino correspondente à conversa na atividade de solicitação.</span><span class="sxs-lookup"><span data-stu-id="fea94-115">The tenant ID corresponding to the conversation in the request activity.</span></span> |

<span data-ttu-id="fea94-116">Se o inquilino ou id de conversação não estiver presente na atividade ou não tiver sido validado no lado do serviço, o valor está vazio.</span><span class="sxs-lookup"><span data-stu-id="fea94-116">If the tenant or conversation ID is not present in the activity or was not validated on the service side, the value is empty.</span></span>

![Solicitar campos de cabeçalho](~/assets/images/bots/requestheaderfields.png)
