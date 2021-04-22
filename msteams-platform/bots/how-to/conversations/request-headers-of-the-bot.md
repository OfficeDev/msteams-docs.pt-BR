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
# <a name="send-tenant-id-and-conversation-id-to-the-request-headers-of-the-bot"></a><span data-ttu-id="af60b-103">Enviar ID de locatário e ID de conversa para os headers de solicitação do bot</span><span class="sxs-lookup"><span data-stu-id="af60b-103">Send tenant ID and conversation ID to the request headers of the bot</span></span>

<span data-ttu-id="af60b-104">As solicitações de saída atuais para o bot não contêm no header ou url informações que ajudam os bots a rotear o tráfego sem desempacotar toda a carga.</span><span class="sxs-lookup"><span data-stu-id="af60b-104">The current outgoing requests to the bot do not contain in the header or URL any information that helps bots route the traffic without unpacking the entire payload.</span></span> <span data-ttu-id="af60b-105">As atividades são enviadas para o bot por meio de uma URL semelhante a https://<your_domain>/api/messages.</span><span class="sxs-lookup"><span data-stu-id="af60b-105">The activities are sent to the bot through a URL similar to https://<your_domain>/api/messages.</span></span> <span data-ttu-id="af60b-106">As solicitações são recebidas para mostrar a ID da conversa e a ID do locatário nos headers.</span><span class="sxs-lookup"><span data-stu-id="af60b-106">Requests are received to show the conversation ID and tenant ID in the headers.</span></span>

## <a name="request-header-fields"></a><span data-ttu-id="af60b-107">Solicitar campos de header</span><span class="sxs-lookup"><span data-stu-id="af60b-107">Request header fields</span></span>

<span data-ttu-id="af60b-108">Dois campos de header de solicitação não padrão são adicionados a todas as solicitações enviadas aos bots, para fluxo assíncrono e fluxo síncrono.</span><span class="sxs-lookup"><span data-stu-id="af60b-108">Two non-standard request header fields are added to all the requests sent to bots, for both asynchronous flow and synchronous flow.</span></span> <span data-ttu-id="af60b-109">A tabela a seguir fornece os campos de header de solicitação e seus valores.</span><span class="sxs-lookup"><span data-stu-id="af60b-109">The following table provides the request header fields and their values.</span></span>

| <span data-ttu-id="af60b-110">Chave de campo</span><span class="sxs-lookup"><span data-stu-id="af60b-110">Field key</span></span> | <span data-ttu-id="af60b-111">Valor</span><span class="sxs-lookup"><span data-stu-id="af60b-111">Value</span></span> |
|----------------|-----------------|
| <span data-ttu-id="af60b-112">x-ms-conversation-id</span><span class="sxs-lookup"><span data-stu-id="af60b-112">x-ms-conversation-id</span></span> | <span data-ttu-id="af60b-113">A ID da conversa correspondente à atividade de solicitação, se aplicável e confirmado ou verificado.</span><span class="sxs-lookup"><span data-stu-id="af60b-113">The conversation ID corresponding to the request activity if applicable and confirmed or verified.</span></span> |
| <span data-ttu-id="af60b-114">x-ms-tenant-id</span><span class="sxs-lookup"><span data-stu-id="af60b-114">x-ms-tenant-id</span></span> | <span data-ttu-id="af60b-115">A ID do locatário correspondente à conversa na atividade de solicitação.</span><span class="sxs-lookup"><span data-stu-id="af60b-115">The tenant ID corresponding to the conversation in the request activity.</span></span> |

<span data-ttu-id="af60b-116">Se o locatário ou a ID da conversa não estiver presente na atividade ou não tiver sido validado no lado do serviço, o valor estará vazio.</span><span class="sxs-lookup"><span data-stu-id="af60b-116">If the tenant or conversation ID is not present in the activity or was not validated on the service side, the value is empty.</span></span>

![Solicitar campos de header](~/assets/images/bots/requestheaderfields.png)
