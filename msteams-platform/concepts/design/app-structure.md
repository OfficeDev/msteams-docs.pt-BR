---
title: Projetar seu aplicativo - Compreender a estrutura do aplicativo
description: Entenda o que você pode ou não personalizar no Microsoft Teams ao projetar seu aplicativo.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: a574ebeb5416e614152bb24d52cc798f0032943c
ms.sourcegitcommit: 0fe60b3fd406a5768b18977df53d1f4c665e5300
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53133371"
---
# <a name="understand-the-microsoft-teams-app-structure"></a><span data-ttu-id="ab081-103">Compreender a estrutura Microsoft Teams de aplicativos</span><span class="sxs-lookup"><span data-stu-id="ab081-103">Understand the Microsoft Teams app structure</span></span>

<span data-ttu-id="ab081-104">Ao criar seu aplicativo, é importante saber o que você pode ou não personalizar no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ab081-104">When building your app, it's important to know what you can and can't customize in Microsoft Teams.</span></span> <span data-ttu-id="ab081-105">Essas informações podem ajudá-lo a entender melhor quais partes da experiência do aplicativo você controla.</span><span class="sxs-lookup"><span data-stu-id="ab081-105">This information can help you better understand which parts of the app experience you control.</span></span>

<span data-ttu-id="ab081-106">Os seguintes wireframes mostram:</span><span class="sxs-lookup"><span data-stu-id="ab081-106">The following wireframes show you:</span></span>

* <span data-ttu-id="ab081-107">As superfícies que você pode personalizar em cada Teams do aplicativo (descrito em rosa).</span><span class="sxs-lookup"><span data-stu-id="ab081-107">The surfaces you can customize in each Teams app capability (outlined in pink).</span></span>
* <span data-ttu-id="ab081-108">Os escopos com os suportes de cada recurso.</span><span class="sxs-lookup"><span data-stu-id="ab081-108">The scopes each capability supports.</span></span>

> [!TIP]
> <span data-ttu-id="ab081-109">**O que significa escopo?**</span><span class="sxs-lookup"><span data-stu-id="ab081-109">**What does scope mean?**</span></span> <span data-ttu-id="ab081-110">Um escopo é uma área em Teams onde as pessoas podem usar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab081-110">A scope is an area in Teams where people can use your app.</span></span> <span data-ttu-id="ab081-111">Os aplicativos podem ter um ou vários escopos, incluindo pessoal, canais, chats e reuniões.</span><span class="sxs-lookup"><span data-stu-id="ab081-111">Apps can have one or many scopes, including personal, channels, chats, and meetings.</span></span>

## <a name="personal-apps"></a><span data-ttu-id="ab081-112">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="ab081-112">Personal apps</span></span>

<span data-ttu-id="ab081-113">Os aplicativos pessoais fornecem uma tela grande para hospedar o conteúdo do aplicativo para usuários individuais.</span><span class="sxs-lookup"><span data-stu-id="ab081-113">Personal apps provide a large canvas to host your app content for individual users.</span></span>

<span data-ttu-id="ab081-114">\***Escopos com suporte**: Pessoal\*</span><span class="sxs-lookup"><span data-stu-id="ab081-114">\***Supported scopes**: Personal\*</span></span>

# <a name="desktop"></a>[<span data-ttu-id="ab081-115">Desktop</span><span class="sxs-lookup"><span data-stu-id="ab081-115">Desktop</span></span>](#tab/desktop)

<span data-ttu-id="ab081-116">A tela é um iframe para que você possa personalizar completamente a experiência.</span><span class="sxs-lookup"><span data-stu-id="ab081-116">The canvas is an iframe so you can completely customize the experience.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para aplicativos pessoais na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="ab081-118">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="ab081-118">Mobile</span></span>](#tab/mobile)

<span data-ttu-id="ab081-119">A tela é uma webview para que você possa personalizar completamente a experiência.</span><span class="sxs-lookup"><span data-stu-id="ab081-119">The canvas is a webview so you can completely customize the experience.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-mobile.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para aplicativos pessoais em dispositivos móveis." border="false":::

---

## <a name="tabs"></a><span data-ttu-id="ab081-121">Guias</span><span class="sxs-lookup"><span data-stu-id="ab081-121">Tabs</span></span>

<span data-ttu-id="ab081-122">As guias fornecem uma tela grande para hospedar o conteúdo do aplicativo para um grupo de usuários.</span><span class="sxs-lookup"><span data-stu-id="ab081-122">Tabs provide a large canvas to host your app content for a group of users.</span></span> <span data-ttu-id="ab081-123">Você pode incluir guias em espaços compartilhados, como canais, chats e convites de reunião.</span><span class="sxs-lookup"><span data-stu-id="ab081-123">You can include tabs in shared spaces such as channels, chats, and meeting invites.</span></span>

<span data-ttu-id="ab081-124">\***Escopos com suporte**: Canais, Chats, Reuniões\*</span><span class="sxs-lookup"><span data-stu-id="ab081-124">\***Supported scopes**: Channels, Chats, Meetings\*</span></span>

# <a name="desktop"></a>[<span data-ttu-id="ab081-125">Desktop</span><span class="sxs-lookup"><span data-stu-id="ab081-125">Desktop</span></span>](#tab/desktop)

<span data-ttu-id="ab081-126">A tela é um iframe para que você possa personalizar completamente a experiência.</span><span class="sxs-lookup"><span data-stu-id="ab081-126">The canvas is an iframe so you can completely customize the experience.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para guias na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="ab081-128">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="ab081-128">Mobile</span></span>](#tab/mobile)

<span data-ttu-id="ab081-129">A tela é uma webview para que você possa personalizar completamente a experiência.</span><span class="sxs-lookup"><span data-stu-id="ab081-129">The canvas is a webview so you can completely customize the experience.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-mobile.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para guias no celular." border="false":::

---

## <a name="bots"></a><span data-ttu-id="ab081-131">Bots</span><span class="sxs-lookup"><span data-stu-id="ab081-131">Bots</span></span>

<span data-ttu-id="ab081-132">Bots são aplicativos de conversa que se integram Teams recursos nativos de mensagens, portanto, o trabalho da interface do usuário é manipulado para você.</span><span class="sxs-lookup"><span data-stu-id="ab081-132">Bots are conversational apps that integrate with Teams native messaging features, so the UI work is handled for you.</span></span> <span data-ttu-id="ab081-133">Do ponto de vista de design, ainda há oportunidades de adicionar personalidade, funcionalidade personalizada e informações avançadas e acionáveis com nosso suporte ao processamento de linguagem natural (NLP) e à plataforma Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="ab081-133">From a design standpoint, there are still opportunities to add personality, custom functionality, and rich, actionable information with our natural language processing (NLP) support and Adaptive Cards platform.</span></span>

<span data-ttu-id="ab081-134">\***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões\*</span><span class="sxs-lookup"><span data-stu-id="ab081-134">\***Supported scopes**: Personal, Channels, Chats, Meetings\*</span></span>

# <a name="desktop"></a>[<span data-ttu-id="ab081-135">Desktop</span><span class="sxs-lookup"><span data-stu-id="ab081-135">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para bots na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="ab081-137">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="ab081-137">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-mobile.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para bots em dispositivos móveis." border="false":::

---

## <a name="messaging-extensions"></a><span data-ttu-id="ab081-139">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ab081-139">Messaging extensions</span></span>

<span data-ttu-id="ab081-140">Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem sair da conversa.</span><span class="sxs-lookup"><span data-stu-id="ab081-140">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span> <span data-ttu-id="ab081-141">As extensões de mensagens baseadas em ação dão mais controle à experiência, enquanto Teams lida com grande parte do que renderiza para extensões de mensagens baseadas em pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ab081-141">Action-based messaging extensions give you more control of the experience, while Teams handles much of what renders for search-based messaging extensions.</span></span>

<span data-ttu-id="ab081-142">\***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões\*</span><span class="sxs-lookup"><span data-stu-id="ab081-142">\***Supported scopes**: Personal, Channels, Chats, Meetings\*</span></span>

# <a name="desktop"></a>[<span data-ttu-id="ab081-143">Desktop</span><span class="sxs-lookup"><span data-stu-id="ab081-143">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de mensagens na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="ab081-145">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="ab081-145">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-mobile.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de mensagens em dispositivos móveis." border="false":::

---

## <a name="meeting-extensions"></a><span data-ttu-id="ab081-147">Extensões de reunião</span><span class="sxs-lookup"><span data-stu-id="ab081-147">Meeting extensions</span></span>

<span data-ttu-id="ab081-148">Extensões de reunião são aplicativos para aprimorar reuniões ao vivo.</span><span class="sxs-lookup"><span data-stu-id="ab081-148">Meeting extensions are apps to enhance live meetings.</span></span> <span data-ttu-id="ab081-149">Você pode hospedar o conteúdo do aplicativo em vários cenários, incluindo antes, durante e após reuniões.</span><span class="sxs-lookup"><span data-stu-id="ab081-149">You can host your app content in several scenarios, including before, during, and after meetings.</span></span>

<span data-ttu-id="ab081-150">\***Escopos com suporte**: Reuniões, Chats\*</span><span class="sxs-lookup"><span data-stu-id="ab081-150">\***Supported scopes**: Meetings, Chats\*</span></span>

# <a name="desktop"></a>[<span data-ttu-id="ab081-151">Desktop</span><span class="sxs-lookup"><span data-stu-id="ab081-151">Desktop</span></span>](#tab/desktop)

<span data-ttu-id="ab081-152">A superfície é um iframe, permitindo que você personalize a experiência, mas tenha em mente que durante as reuniões esses aplicativos usam tema escuro e são estreitos.</span><span class="sxs-lookup"><span data-stu-id="ab081-152">The surface is an iframe, allowing you to customize the experience, but keep in mind that during meetings these apps use dark theme and are narrow.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de reunião na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="ab081-154">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="ab081-154">Mobile</span></span>](#tab/mobile)

<span data-ttu-id="ab081-155">A superfície é uma webview, permitindo que você personalize a experiência, mas tenha em mente que durante as reuniões esses aplicativos usam tema escuro.</span><span class="sxs-lookup"><span data-stu-id="ab081-155">The surface is a webview, allowing you to customize the experience, but keep in mind that during meetings these apps use dark theme.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-mobile.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de reunião em dispositivos móveis." border="false":::

---
