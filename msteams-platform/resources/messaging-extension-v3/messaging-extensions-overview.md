---
title: Desenvolver extensões de mensagens
description: Descreve como começar a usar extensões de mensagens no Microsoft Teams
ms.topic: overview
localization_priority: Normal
keywords: extensões de mensagens do teams messaging extensions
ms.openlocfilehash: 2301a9af7574c193c7327bb45e38f91bedc73793
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020601"
---
# <a name="develop-messaging-extensions-for-microsoft-teams"></a><span data-ttu-id="9c9ea-104">Desenvolver extensões de mensagens para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9c9ea-104">Develop messaging extensions for Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

<span data-ttu-id="9c9ea-105">Extensões de mensagens são uma maneira poderosa de os usuários se envolverem com seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9c9ea-105">Messaging extensions are a powerful way for users to engage with your app from Microsoft Teams.</span></span> <span data-ttu-id="9c9ea-106">Com essa funcionalidade, os usuários podem consultar ou postar informações de e para o serviço e postar essas informações, na forma de cartões, em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="9c9ea-106">With this capability, users can query or post information to and from your service and post that information, in the form of cards, right into a message.</span></span>

![Exemplo de cartão de extensão de mensagens](~/assets/images/compose-extensions/ceexample.png)

<span data-ttu-id="9c9ea-108">As extensões de mensagens aparecem ao longo da parte inferior da caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="9c9ea-108">Messaging extensions appear along the bottom of the compose box.</span></span> <span data-ttu-id="9c9ea-109">Alguns são integrados, como Emoji, Giphy e Sticker.</span><span class="sxs-lookup"><span data-stu-id="9c9ea-109">A few are built in, such as Emoji, Giphy, and Sticker.</span></span> <span data-ttu-id="9c9ea-110">Escolha o **botão Mais Opções** (**&#8943;**) para ver outras extensões de mensagens, incluindo aquelas que você adiciona na galeria de aplicativos ou carrega você mesmo.</span><span class="sxs-lookup"><span data-stu-id="9c9ea-110">Choose the **More Options** (**&#8943;**) button to see other messaging extensions, including those you add from the app gallery or upload yourself.</span></span>

<span data-ttu-id="9c9ea-111">Como você usaria extensões de mensagens?</span><span class="sxs-lookup"><span data-stu-id="9c9ea-111">How would you use messaging extensions?</span></span> <span data-ttu-id="9c9ea-112">Aqui estão algumas possibilidades:</span><span class="sxs-lookup"><span data-stu-id="9c9ea-112">Here are a few possibilities:</span></span>

* <span data-ttu-id="9c9ea-113">Itens de trabalho e bugs</span><span class="sxs-lookup"><span data-stu-id="9c9ea-113">Work items and bugs</span></span>
* <span data-ttu-id="9c9ea-114">Tíquetes de suporte ao cliente</span><span class="sxs-lookup"><span data-stu-id="9c9ea-114">Customer support tickets</span></span>
* <span data-ttu-id="9c9ea-115">Gráficos de uso e relatórios</span><span class="sxs-lookup"><span data-stu-id="9c9ea-115">Usage charts and reports</span></span>
* <span data-ttu-id="9c9ea-116">Imagens e conteúdo de mídia</span><span class="sxs-lookup"><span data-stu-id="9c9ea-116">Images and media content</span></span>
* <span data-ttu-id="9c9ea-117">Oportunidades de vendas e leads</span><span class="sxs-lookup"><span data-stu-id="9c9ea-117">Sales opportunities and leads</span></span>

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="9c9ea-118">Tipos de extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="9c9ea-118">Types of messaging extensions</span></span>

<span data-ttu-id="9c9ea-119">Há basicamente dois tipos de extensões de mensagens que você pode criar para o Teams hoje.</span><span class="sxs-lookup"><span data-stu-id="9c9ea-119">There's primarily two kinds of messaging extensions you can create for Teams today.</span></span> <span data-ttu-id="9c9ea-120">Os tópicos a seguir orientarão você durante o processo de criação deles:</span><span class="sxs-lookup"><span data-stu-id="9c9ea-120">The following topics will guide you through the process of creating them:</span></span>

* <span data-ttu-id="9c9ea-121">[Extensões de mensagens baseadas em pesquisa:](~/resources/messaging-extension-v3/search-extensions.md)consulte seu serviço para obter informações e insira-as em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="9c9ea-121">[Search based messaging extensions](~/resources/messaging-extension-v3/search-extensions.md): Query your service for information and insert that into a message.</span></span> <span data-ttu-id="9c9ea-122">Exemplo: Procure um item de trabalho</span><span class="sxs-lookup"><span data-stu-id="9c9ea-122">Example: Lookup a work item</span></span>
* <span data-ttu-id="9c9ea-123">[Extensões de mensagens baseadas em](~/resources/messaging-extension-v3/create-extensions.md)ação : Coletar informações do usuário e postar em um serviço de terceiros.</span><span class="sxs-lookup"><span data-stu-id="9c9ea-123">[Action-based messaging extensions](~/resources/messaging-extension-v3/create-extensions.md): Collect information from the user and post to a 3rd party service.</span></span> <span data-ttu-id="9c9ea-124">Exemplo: Criar um item de trabalho</span><span class="sxs-lookup"><span data-stu-id="9c9ea-124">Example: Create a work item</span></span>
