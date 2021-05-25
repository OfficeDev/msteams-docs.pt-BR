---
title: Projetar seu aplicativo - Compreender a estrutura do aplicativo
description: Entenda o que você pode ou não personalizar no Microsoft Teams ao projetar seu aplicativo.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: bf84ad1d52cf46e9242bf4122dc5e900461ab806
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631231"
---
# <a name="understand-the-microsoft-teams-app-structure"></a><span data-ttu-id="79e4a-103">Compreender a estrutura Microsoft Teams de aplicativos</span><span class="sxs-lookup"><span data-stu-id="79e4a-103">Understand the Microsoft Teams app structure</span></span>

<span data-ttu-id="79e4a-104">Ao criar seu aplicativo, é importante saber o que você pode ou não personalizar no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="79e4a-104">When building your app, it's important to know what you can and can't customize in Microsoft Teams.</span></span> <span data-ttu-id="79e4a-105">Essas informações podem ajudá-lo a entender melhor quais partes da experiência do aplicativo você controla.</span><span class="sxs-lookup"><span data-stu-id="79e4a-105">This information can help you better understand which parts of the app experience you control.</span></span>

<span data-ttu-id="79e4a-106">Os seguintes wireframes mostram:</span><span class="sxs-lookup"><span data-stu-id="79e4a-106">The following wireframes show you:</span></span>

* <span data-ttu-id="79e4a-107">As superfícies que você pode personalizar em cada Teams de aplicativo (descrito em azul).</span><span class="sxs-lookup"><span data-stu-id="79e4a-107">The surfaces you can customize in each Teams app capability (outlined in blue).</span></span>
* <span data-ttu-id="79e4a-108">Os escopos com os suportes de cada recurso.</span><span class="sxs-lookup"><span data-stu-id="79e4a-108">The scopes each capability supports.</span></span>

> [!NOTE]
> <span data-ttu-id="79e4a-109">**O que significa escopo?**</span><span class="sxs-lookup"><span data-stu-id="79e4a-109">**What does scope mean?**</span></span> <span data-ttu-id="79e4a-110">Um escopo é uma área em Teams onde as pessoas podem usar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79e4a-110">A scope is an area in Teams where people can use your app.</span></span> <span data-ttu-id="79e4a-111">Os aplicativos podem ter um ou vários escopos, incluindo pessoal, canais, chats e reuniões.</span><span class="sxs-lookup"><span data-stu-id="79e4a-111">Apps can have one or many scopes, including personal, channels, chats, and meetings.</span></span>

## <a name="personal-apps"></a><span data-ttu-id="79e4a-112">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="79e4a-112">Personal apps</span></span>

<span data-ttu-id="79e4a-113">Os aplicativos pessoais fornecem uma tela grande para hospedar o conteúdo do aplicativo para usuários individuais.</span><span class="sxs-lookup"><span data-stu-id="79e4a-113">Personal apps provide a large canvas to host your app content for individual users.</span></span> <span data-ttu-id="79e4a-114">A tela é um iframe para que você possa personalizar completamente a experiência.</span><span class="sxs-lookup"><span data-stu-id="79e4a-114">The canvas is an iframe so you can completely customize the experience.</span></span>

<span data-ttu-id="79e4a-115">\***Escopos com suporte**: Pessoal\*</span><span class="sxs-lookup"><span data-stu-id="79e4a-115">\***Supported scopes**: Personal\*</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para aplicativos pessoais." border="false":::

## <a name="tabs"></a><span data-ttu-id="79e4a-117">Guias</span><span class="sxs-lookup"><span data-stu-id="79e4a-117">Tabs</span></span>

<span data-ttu-id="79e4a-118">As guias fornecem uma tela grande para hospedar o conteúdo do aplicativo para um grupo de usuários.</span><span class="sxs-lookup"><span data-stu-id="79e4a-118">Tabs provide a large canvas to host your app content for a group of users.</span></span> <span data-ttu-id="79e4a-119">Você pode incluir guias em espaços compartilhados, como canais, chats e convites de reunião.</span><span class="sxs-lookup"><span data-stu-id="79e4a-119">You can include tabs in shared spaces such as channels, chats, and meeting invites.</span></span> <span data-ttu-id="79e4a-120">A tela é um iframe para que você possa personalizar completamente a experiência.</span><span class="sxs-lookup"><span data-stu-id="79e4a-120">The canvas is an iframe so you can completely customize the experience.</span></span>

<span data-ttu-id="79e4a-121">\***Escopos com suporte**: Canais, Chats, Reuniões\*</span><span class="sxs-lookup"><span data-stu-id="79e4a-121">\***Supported scopes**: Channels, Chats, Meetings\*</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para guias." border="false":::

## <a name="bots"></a><span data-ttu-id="79e4a-123">Bots</span><span class="sxs-lookup"><span data-stu-id="79e4a-123">Bots</span></span>

<span data-ttu-id="79e4a-124">Bots são aplicativos de conversa que se integram Teams recursos nativos de mensagens, portanto, o trabalho da interface do usuário é manipulado para você.</span><span class="sxs-lookup"><span data-stu-id="79e4a-124">Bots are conversational apps that integrate with Teams native messaging features, so the UI work is handled for you.</span></span> <span data-ttu-id="79e4a-125">Do ponto de vista de design, ainda há oportunidades de adicionar personalidade, funcionalidade personalizada e informações avançadas e acionáveis com nosso suporte ao processamento de linguagem natural (NLP) e à plataforma Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="79e4a-125">From a design standpoint, there are still opportunities to add personality, custom functionality, and rich, actionable information with our natural language processing (NLP) support and Adaptive Cards platform.</span></span>

<span data-ttu-id="79e4a-126">\***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões\*</span><span class="sxs-lookup"><span data-stu-id="79e4a-126">\***Supported scopes**: Personal, Channels, Chats, Meetings\*</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para bots." border="false":::

## <a name="messaging-extensions"></a><span data-ttu-id="79e4a-128">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="79e4a-128">Messaging extensions</span></span>

<span data-ttu-id="79e4a-129">Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem sair da conversa.</span><span class="sxs-lookup"><span data-stu-id="79e4a-129">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span> <span data-ttu-id="79e4a-130">As extensões de mensagens baseadas em ação dão mais controle à experiência, enquanto Teams lida com grande parte do que renderiza para extensões de mensagens baseadas em pesquisa.</span><span class="sxs-lookup"><span data-stu-id="79e4a-130">Action-based messaging extensions give you more control of the experience, while Teams handles much of what renders for search-based messaging extensions.</span></span>

<span data-ttu-id="79e4a-131">\***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões\*</span><span class="sxs-lookup"><span data-stu-id="79e4a-131">\***Supported scopes**: Personal, Channels, Chats, Meetings\*</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de mensagens." border="false":::

## <a name="meeting-extensions"></a><span data-ttu-id="79e4a-133">Extensões de reunião</span><span class="sxs-lookup"><span data-stu-id="79e4a-133">Meeting extensions</span></span>

<span data-ttu-id="79e4a-134">Extensões de reunião são aplicativos para aprimorar reuniões ao vivo.</span><span class="sxs-lookup"><span data-stu-id="79e4a-134">Meeting extensions are apps to enhance live meetings.</span></span> <span data-ttu-id="79e4a-135">Você pode hospedar o conteúdo do aplicativo em vários cenários, incluindo antes, durante e após reuniões.</span><span class="sxs-lookup"><span data-stu-id="79e4a-135">You can host your app content in several scenarios, including before, during, and after meetings.</span></span> <span data-ttu-id="79e4a-136">A superfície é um iframe, permitindo que você personalize a experiência, mas tenha em mente que esses aplicativos são temas escuros e estreitos durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="79e4a-136">The surface is an iframe, allowing you to customize the experience, but keep in mind that these apps are dark themed and narrow during meetings.</span></span>

<span data-ttu-id="79e4a-137">\***Escopos com suporte**: Reuniões, Chats\*</span><span class="sxs-lookup"><span data-stu-id="79e4a-137">\***Supported scopes**: Meetings, Chats\*</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de reunião." border="false":::
