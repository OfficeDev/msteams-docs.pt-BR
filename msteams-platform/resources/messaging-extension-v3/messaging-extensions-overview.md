---
title: Desenvolver extensões de mensagens
description: Descreve como começar a usar as extensões de mensagens no Microsoft Teams
keywords: extensões de mensagens de extensões de mensagens do Microsoft Teams
ms.openlocfilehash: 6ba8f73d40f795a83f28707ef89c207c5d51d67c
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672479"
---
# <a name="develop-messaging-extensions-for-microsoft-teams"></a><span data-ttu-id="73559-104">Desenvolver extensões de mensagens para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="73559-104">Develop messaging extensions for Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

<span data-ttu-id="73559-105">As extensões de mensagens são uma maneira poderosa para os usuários entrarem com seu aplicativo no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="73559-105">Messaging extensions are a powerful way for users to engage with your app from Microsoft Teams.</span></span> <span data-ttu-id="73559-106">Com esse recurso, os usuários podem consultar ou postar informações de e para o seu serviço e postar essas informações, na forma de cartões, diretamente em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="73559-106">With this capability, users can query or post information to and from your service and post that information, in the form of cards, right into a message.</span></span>

![Exemplo de cartão de extensão de mensagens](~/assets/images/compose-extensions/ceexample.png)

<span data-ttu-id="73559-108">As extensões de mensagens aparecem ao longo da parte inferior da caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="73559-108">Messaging extensions appear along the bottom of the compose box.</span></span> <span data-ttu-id="73559-109">Alguns são internos, como Emoji, Giphy e adesivo.</span><span class="sxs-lookup"><span data-stu-id="73559-109">A few are built in, such as Emoji, Giphy, and Sticker.</span></span> <span data-ttu-id="73559-110">Escolha o botão **mais opções** (**&#8943;**) para ver outras extensões de mensagens, incluindo aquelas que você adicionar da Galeria de aplicativos ou se carregar sozinho.</span><span class="sxs-lookup"><span data-stu-id="73559-110">Choose the **More Options** (**&#8943;**) button to see other messaging extensions, including those you add from the app gallery or upload yourself.</span></span>

<span data-ttu-id="73559-111">Como você usaria as extensões de mensagens?</span><span class="sxs-lookup"><span data-stu-id="73559-111">How would you use messaging extensions?</span></span> <span data-ttu-id="73559-112">Veja algumas possibilidades:</span><span class="sxs-lookup"><span data-stu-id="73559-112">Here are a few possibilities:</span></span>

* <span data-ttu-id="73559-113">Itens de trabalho e bugs</span><span class="sxs-lookup"><span data-stu-id="73559-113">Work items and bugs</span></span>
* <span data-ttu-id="73559-114">Tíquetes de atendimento ao cliente</span><span class="sxs-lookup"><span data-stu-id="73559-114">Customer support tickets</span></span>
* <span data-ttu-id="73559-115">Relatórios e gráficos de uso</span><span class="sxs-lookup"><span data-stu-id="73559-115">Usage charts and reports</span></span>
* <span data-ttu-id="73559-116">Imagens e conteúdo de mídia</span><span class="sxs-lookup"><span data-stu-id="73559-116">Images and media content</span></span>
* <span data-ttu-id="73559-117">Oportunidades de vendas e clientes potenciais</span><span class="sxs-lookup"><span data-stu-id="73559-117">Sales opportunities and leads</span></span>

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="73559-118">Tipos de extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="73559-118">Types of messaging extensions</span></span>

<span data-ttu-id="73559-119">Há principalmente dois tipos de extensões de mensagens que você pode criar para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="73559-119">There's primarily two kinds of messaging extensions you can create for Teams today.</span></span> <span data-ttu-id="73559-120">Os tópicos a seguir orientarão você durante o processo de criação:</span><span class="sxs-lookup"><span data-stu-id="73559-120">The following topics will guide you through the process of creating them:</span></span>

* <span data-ttu-id="73559-121">[Pesquisar extensões de mensagens baseadas](~/resources/messaging-extension-v3/search-extensions.md): consulte o serviço para obter informações e insira-o em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="73559-121">[Search based messaging extensions](~/resources/messaging-extension-v3/search-extensions.md): Query your service for information and insert that into a message.</span></span> <span data-ttu-id="73559-122">Exemplo: Pesquisar um item de trabalho</span><span class="sxs-lookup"><span data-stu-id="73559-122">Example: Lookup a work item</span></span>
* <span data-ttu-id="73559-123">[Extensões de mensagens baseadas em ação](~/resources/messaging-extension-v3/create-extensions.md): coletar informações do usuário e postar em um serviço de terceiros.</span><span class="sxs-lookup"><span data-stu-id="73559-123">[Action-based messaging extensions](~/resources/messaging-extension-v3/create-extensions.md): Collect information from the user and post to a 3rd party service.</span></span> <span data-ttu-id="73559-124">Exemplo: criar um item de trabalho</span><span class="sxs-lookup"><span data-stu-id="73559-124">Example: Create a work item</span></span>
