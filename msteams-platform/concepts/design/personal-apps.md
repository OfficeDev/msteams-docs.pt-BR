---
title: Referência de diretrizes de design
description: Descreve as diretrizes para a criação de um aplicativo pessoal
keywords: Diretrizes de design do Microsoft Teams aplicativos pessoais da estrutura de referência
ms.openlocfilehash: f66691234149afa56a6753dd51379c9f2355318e
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2020
ms.locfileid: "44455496"
---
# <a name="personal-apps"></a><span data-ttu-id="f603e-104">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="f603e-104">Personal apps</span></span>

> [!NOTE]
> <span data-ttu-id="f603e-105">O suporte completo para guias em clientes móveis é suportado no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="f603e-105">Full support for tabs on mobile clients is supported in Teams.</span></span> <span data-ttu-id="f603e-106">Você deve seguir as [orientações para guias em dispositivos móveis](../../tabs/design/tabs-mobile.md) ao criar guias para plataformas móveis.</span><span class="sxs-lookup"><span data-stu-id="f603e-106">You should follow the [guidance for tabs on mobile](../../tabs/design/tabs-mobile.md) when creating tabs for mobile platforms.</span></span>

<span data-ttu-id="f603e-107">Um aplicativo pessoal é um aplicativo do teams com um escopo pessoal.</span><span class="sxs-lookup"><span data-stu-id="f603e-107">A personal app is a Teams application with a personal scope.</span></span>  <span data-ttu-id="f603e-108">Como desenvolvedor de aplicativos, você tem a opção de fornecer uma versão do seu aplicativo que se concentra em interações com um único usuário.</span><span class="sxs-lookup"><span data-stu-id="f603e-108">As an app developer, you have the option to provide a version of your app that focuses on interactions with a single user.</span></span> <span data-ttu-id="f603e-109">Pode ser um [bot de conversa](../../bots/what-are-bots.md) para participar de conversas de um-para-um com um usuário ou uma [guia pessoal](../../tabs/what-are-tabs.md) que forneça uma experiência Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="f603e-109">It can be a [conversational bot](../../bots/what-are-bots.md) to engage in one-to-one conversations with a user or a [personal tab](../../tabs/what-are-tabs.md) providing an embedded web experience.</span></span> <span data-ttu-id="f603e-110">Os aplicativos pessoais permitem que os usuários exibam o conteúdo selecionado em um só lugar.</span><span class="sxs-lookup"><span data-stu-id="f603e-110">Personal apps enable users to view their select content in one place.</span></span> <span data-ttu-id="f603e-111">Na captura de tela a seguir, a contoso é um aplicativo pessoal no submenu de aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="f603e-111">In the following screenshot, Contoso is a personal app in the personal app flyout.</span></span>

![imagem do menu de estouro de aplicativos](~/assets/images/Personal-apps-App-flyout.png)

---

## <a name="guidelines"></a><span data-ttu-id="f603e-113">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="f603e-113">Guidelines</span></span>

<span data-ttu-id="f603e-114">Um aplicativo pessoal normalmente contém as seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="f603e-114">A personal app typically contains the following tabs:</span></span>

### <a name="your-tab"></a><span data-ttu-id="f603e-115">Sua guia</span><span class="sxs-lookup"><span data-stu-id="f603e-115">Your tab</span></span>

<span data-ttu-id="f603e-116">Este é o local onde os usuários verão todas as suas coisas.</span><span class="sxs-lookup"><span data-stu-id="f603e-116">This is where your users will see all their stuff.</span></span> <span data-ttu-id="f603e-117">É seu espaço pessoal.</span><span class="sxs-lookup"><span data-stu-id="f603e-117">It's their personal space.</span></span> <span data-ttu-id="f603e-118">A guia pode ser organizada como uma lista, uma grade, colunas ou uma tela única... o que funcionar melhor para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f603e-118">The tab can be arranged as a list, a grid, columns, or a single canvas...whatever works best for your application.</span></span> <span data-ttu-id="f603e-119">Para obter informações adicionais sobre como criar guias eficazes, consulte: [design de guias](../../tabs/design/tabs.md).</span><span class="sxs-lookup"><span data-stu-id="f603e-119">For additional information on designing effective tabs see: [Tabs design](../../tabs/design/tabs.md).</span></span>

<span data-ttu-id="f603e-120">Como essa guia pode mostrar itens de vários canais, cada item deve exibir sua própria equipe, canal e guia para que o usuário possa ver facilmente onde ele se originou.</span><span class="sxs-lookup"><span data-stu-id="f603e-120">Since this tab can show items from multiple channels, each item should display its own team, channel, and tab so the user can easily see where it originated.</span></span>

![Guia tarefas pessoais](~/assets/images/Personal-apps-MY-tab.png)

### <a name="recent"></a><span data-ttu-id="f603e-122">Recentemente</span><span class="sxs-lookup"><span data-stu-id="f603e-122">Recent</span></span>

<span data-ttu-id="f603e-123">A guia **recente** permite que alguém Navegue por tudo o que exibiu recentemente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f603e-123">The **Recent** tab lets someone browse everything they've recently viewed in your app.</span></span> <span data-ttu-id="f603e-124">Ela é listada em ordem cronológica (do mais para menos recente).</span><span class="sxs-lookup"><span data-stu-id="f603e-124">It's listed in chronological order (from most to least recent).</span></span> <span data-ttu-id="f603e-125">Clicar em um item nesta lista navegará o usuário para o canal e a guia do item.</span><span class="sxs-lookup"><span data-stu-id="f603e-125">Clicking on an item in this list will navigate the user to that item's channel and tab.</span></span>

![Guia recente](~/assets/images/Personal-apps-Recent-tab.png)

### <a name="all"></a><span data-ttu-id="f603e-127">Todos</span><span class="sxs-lookup"><span data-stu-id="f603e-127">All</span></span>

<span data-ttu-id="f603e-128">Esta é uma lista de todas as suas guias na organização da pessoa (com as quais elas têm acesso, assim mesmo).</span><span class="sxs-lookup"><span data-stu-id="f603e-128">This is a list of all your tabs in the person's organization (the ones they have access to, anyway).</span></span> <span data-ttu-id="f603e-129">Em outras palavras, ele mostra a eles em qualquer lugar em que o aplicativo está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="f603e-129">In other words, it shows them everywhere the app is being used.</span></span> <span data-ttu-id="f603e-130">Como ocorre com a guia **recente** , selecionar algo na lista trará o usuário diretamente para o canal e a guia relevantes.</span><span class="sxs-lookup"><span data-stu-id="f603e-130">As with the **Recent** tab, selecting something in the list will bring the user straight to the relevant channel and tab.</span></span>

### <a name="bot"></a><span data-ttu-id="f603e-131">Bot</span><span class="sxs-lookup"><span data-stu-id="f603e-131">Bot</span></span>

<span data-ttu-id="f603e-132">Um bot não é necessário, mas é uma ótima maneira de se comunicar de forma direta e privada com seus usuários.</span><span class="sxs-lookup"><span data-stu-id="f603e-132">A bot isn't required, but it's a great way to communicate directly and privately with your users.</span></span> <span data-ttu-id="f603e-133">A notificação é uma das funções mais importantes de um aplicativo pessoal e qual é a melhor maneira de notificá-lo do que com comunicação direta?</span><span class="sxs-lookup"><span data-stu-id="f603e-133">Notification is one of the most important functions of a personal app, and what better way to notify than with direct communication?</span></span>

<span data-ttu-id="f603e-134">Os bots entregam mensagens na forma de cartões, que podem fornecer informações específicas (como um alerta que o novo conteúdo está disponível) ou atualizações amplas (como uma lista de tarefas diárias).</span><span class="sxs-lookup"><span data-stu-id="f603e-134">Bots deliver messages in the form of cards, which can provide specific information (like an alert that new content is available) or broad updates (like a daily to-do list).</span></span> <span data-ttu-id="f603e-135">Para obter informações adicionais sobre como projetar bots efetivos, consulte: [design de bot](../../bots/design/bots.md).</span><span class="sxs-lookup"><span data-stu-id="f603e-135">For additional information on designing effective bots see: [Bot design](../../bots/design/bots.md).</span></span>

![Saudação de bot](~/assets/images/Personal-apps-Bot.png)

### <a name="help-and-settings"></a><span data-ttu-id="f603e-137">Ajuda e configurações</span><span class="sxs-lookup"><span data-stu-id="f603e-137">Help and Settings</span></span>

<span data-ttu-id="f603e-138">O conteúdo da ajuda permite que os usuários descubram as nuances de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f603e-138">Help content enables users to discover the nuances of your app.</span></span> <span data-ttu-id="f603e-139">Adicione uma guia **configurações** para ter a possibilidade de personalizá-la.</span><span class="sxs-lookup"><span data-stu-id="f603e-139">Add a **Settings** tab to give them the ability to further customize it.</span></span>

### <a name="about"></a><span data-ttu-id="f603e-140">Sobre</span><span class="sxs-lookup"><span data-stu-id="f603e-140">About</span></span>

<span data-ttu-id="f603e-141">Inclua uma guia **sobre** para fornecer informações como números de versão, recursos, privacidade e links de permissões.</span><span class="sxs-lookup"><span data-stu-id="f603e-141">Include an **About** tab to provide information like version number, capabilities, privacy, and permissions links.</span></span>

## <a name="best-practices"></a><span data-ttu-id="f603e-142">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="f603e-142">Best practices</span></span>

### <a name="communicate-directly-with-your-users"></a><span data-ttu-id="f603e-143">Comunicar-se diretamente com seus usuários</span><span class="sxs-lookup"><span data-stu-id="f603e-143">Communicate directly with your users</span></span>

<span data-ttu-id="f603e-144">Use um bot para notificar os usuários sobre alterações e novos recursos.</span><span class="sxs-lookup"><span data-stu-id="f603e-144">Use a bot to notify users of changes and new features.</span></span>

### <a name="customize-your-tabs"></a><span data-ttu-id="f603e-145">Personalizar suas guias...</span><span class="sxs-lookup"><span data-stu-id="f603e-145">Customize your tabs...</span></span>

<span data-ttu-id="f603e-146">Sinta-se à vontade para adicionar outras guias que ajudarão os usuários a realizar tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="f603e-146">Feel free to add other tabs that will help your users accomplish specific tasks.</span></span>

### <a name="and-make-them-relevant-to-every-user"></a><span data-ttu-id="f603e-147">... e torná-los relevantes a todos os usuários</span><span class="sxs-lookup"><span data-stu-id="f603e-147">...and make them relevant to every user</span></span>

<span data-ttu-id="f603e-148">Cada guia que você declarar no manifesto do aplicativo ficará visível para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="f603e-148">Every tab you declare in your app manifest will be visible to all users.</span></span> <span data-ttu-id="f603e-149">Por exemplo, se seu aplicativo pessoal é uma ferramenta de relatório de despesas que é usada por gerentes e funcionários, uma guia de **aprovação** deve fornecer conteúdo que seja significativo para ambas as funções.</span><span class="sxs-lookup"><span data-stu-id="f603e-149">For example, if your personal app is an expense reporting tool that is used by both managers and employees, an **Approval** tab should provide content that is meaningful to both roles.</span></span>
