---
title: Referência de diretrizes de design
description: Descreve as diretrizes para a criação de um aplicativo pessoal
keywords: Diretrizes de design do Microsoft Teams aplicativos pessoais da estrutura de referência
ms.openlocfilehash: 0d886adf926697f8920c0893589201ea4e4c3a9c
ms.sourcegitcommit: 6c5c0574228310f844c81df0d57f11e2037e90c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "42228070"
---
# <a name="personal-apps"></a><span data-ttu-id="af852-104">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="af852-104">Personal apps</span></span>

> [!Important]
> <span data-ttu-id="af852-105">O suporte completo para guias em clientes móveis estará disponível em breve.</span><span class="sxs-lookup"><span data-stu-id="af852-105">Full support for tabs on mobile clients is coming soon.</span></span> <span data-ttu-id="af852-106">Para se preparar para essa alteração, você deve seguir as [orientações para guias em celular](~/tabs/design/tabs-mobile.md) ao criar suas guias.</span><span class="sxs-lookup"><span data-stu-id="af852-106">To prepare for this change you should follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span> <span data-ttu-id="af852-107">Os aplicativos pessoais (guias estáticas) estão disponíveis atualmente na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="af852-107">Personal apps (static tabs) are currently available in [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
>
> <span data-ttu-id="af852-108">Quando o suporte completo para guias é liberado:</span><span class="sxs-lookup"><span data-stu-id="af852-108">When full support for tabs is released:</span></span>
>
> * <span data-ttu-id="af852-109">Todas as guias sempre estarão disponíveis em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="af852-109">All tabs will always be available on mobile</span></span>
> * <span data-ttu-id="af852-110">O `contentUrl` **será carregado no cliente do Mobile Teams**.</span><span class="sxs-lookup"><span data-stu-id="af852-110">Your `contentUrl` **will be loaded in the mobile Teams client**.</span></span>
> * <span data-ttu-id="af852-111">Para guias de canal/grupo, os usuários ainda podem abrir sua guia em um navegador separado `websiteUrl`por meio de `contentUrl` seu, no entanto, seu primeiro será carregado.</span><span class="sxs-lookup"><span data-stu-id="af852-111">For channel/group tabs, users can still open your tab in a separate browser via your `websiteUrl`, however your `contentUrl` will be loaded first.</span></span>

<span data-ttu-id="af852-112">Um aplicativo pessoal é um aplicativo com escopo pessoal.</span><span class="sxs-lookup"><span data-stu-id="af852-112">A personal app is an app with a personal scope.</span></span> <span data-ttu-id="af852-113">Como desenvolvedor de aplicativos, você tem a opção de fornecer uma versão do seu aplicativo que é criada para o usuário individual.</span><span class="sxs-lookup"><span data-stu-id="af852-113">As an app developer, you have the option to provide a version of your app that is built for the individual user.</span></span> <span data-ttu-id="af852-114">Nesta versão, a coleção de guias (e o bot, se você incluiu uma), foram projetadas para a pessoa.</span><span class="sxs-lookup"><span data-stu-id="af852-114">In this version, the collection of tabs (and the bot, if you've included one), are designed for the person.</span></span> <span data-ttu-id="af852-115">Dessa forma, você pode criar uma interação um-em-um com seus usuários.</span><span class="sxs-lookup"><span data-stu-id="af852-115">This way, you're able to create a one-on-one interaction with your users.</span></span>

<span data-ttu-id="af852-116">Um aplicativo pessoal é onde alguém pode ver tudo o que é o seu e todos os itens que foram exibidos recentemente no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af852-116">A personal app is where someone can see everything that's theirs, and all the items they've recently viewed in the app.</span></span> <span data-ttu-id="af852-117">Ele coloca tudo em um só lugar.</span><span class="sxs-lookup"><span data-stu-id="af852-117">It puts everything in one place.</span></span> <span data-ttu-id="af852-118">Na captura de tela a seguir, a contoso é um aplicativo pessoal no submenu de aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="af852-118">In the following screenshot, Contoso is a personal app in the personal app flyout.</span></span>

![imagem do menu de estouro de aplicativos](~/assets/images/Personal-apps-App-flyout.png)

---

## <a name="guidelines"></a><span data-ttu-id="af852-120">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="af852-120">Guidelines</span></span>

<span data-ttu-id="af852-121">Um aplicativo pessoal normalmente contém as seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="af852-121">A personal app typically contains the following tabs:</span></span>

### <a name="your-tab"></a><span data-ttu-id="af852-122">Sua guia</span><span class="sxs-lookup"><span data-stu-id="af852-122">Your tab</span></span>

<span data-ttu-id="af852-123">Este é o local onde os usuários verão todas as suas coisas.</span><span class="sxs-lookup"><span data-stu-id="af852-123">This is where your users will see all their stuff.</span></span> <span data-ttu-id="af852-124">É seu espaço pessoal.</span><span class="sxs-lookup"><span data-stu-id="af852-124">It's their personal space.</span></span> <span data-ttu-id="af852-125">A guia pode ser organizada como uma lista, uma grade, colunas ou uma tela única... o que funcionar melhor para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af852-125">The tab can be arranged as a list, a grid, columns, or a single canvas...whatever works best for your application.</span></span> <span data-ttu-id="af852-126">Para obter informações adicionais sobre como criar guias eficazes, consulte: [design de guias](../../tabs/design/tabs.md).</span><span class="sxs-lookup"><span data-stu-id="af852-126">For additional information on designing effective tabs see: [Tabs design](../../tabs/design/tabs.md).</span></span>

<span data-ttu-id="af852-127">Como essa guia pode mostrar itens de vários canais, cada item deve exibir sua própria equipe, canal e guia para que o usuário possa ver facilmente onde ele se originou.</span><span class="sxs-lookup"><span data-stu-id="af852-127">Since this tab can show items from multiple channels, each item should display its own team, channel, and tab so the user can easily see where it originated.</span></span>

![Guia tarefas pessoais](~/assets/images/Personal-apps-MY-tab.png)

### <a name="recent"></a><span data-ttu-id="af852-129">Recentemente</span><span class="sxs-lookup"><span data-stu-id="af852-129">Recent</span></span>

<span data-ttu-id="af852-130">A guia **recente** permite que alguém Navegue por tudo o que exibiu recentemente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af852-130">The **Recent** tab lets someone browse everything they've recently viewed in your app.</span></span> <span data-ttu-id="af852-131">Ela é listada em ordem cronológica (do mais para menos recente).</span><span class="sxs-lookup"><span data-stu-id="af852-131">It's listed in chronological order (from most to least recent).</span></span> <span data-ttu-id="af852-132">Clicar em um item nesta lista navegará o usuário para o canal e a guia do item.</span><span class="sxs-lookup"><span data-stu-id="af852-132">Clicking on an item in this list will navigate the user to that item's channel and tab.</span></span>

![Guia recente](~/assets/images/Personal-apps-Recent-tab.png)

### <a name="all"></a><span data-ttu-id="af852-134">Todos</span><span class="sxs-lookup"><span data-stu-id="af852-134">All</span></span>

<span data-ttu-id="af852-135">Esta é uma lista de todas as suas guias na organização da pessoa (com as quais elas têm acesso, assim mesmo).</span><span class="sxs-lookup"><span data-stu-id="af852-135">This is a list of all your tabs in the person's organization (the ones they have access to, anyway).</span></span> <span data-ttu-id="af852-136">Em outras palavras, ele mostra a eles em qualquer lugar em que o aplicativo está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="af852-136">In other words, it shows them everywhere the app is being used.</span></span> <span data-ttu-id="af852-137">Como ocorre com a guia **recente** , selecionar algo na lista trará o usuário diretamente para o canal e a guia relevantes.</span><span class="sxs-lookup"><span data-stu-id="af852-137">As with the **Recent** tab, selecting something in the list will bring the user straight to the relevant channel and tab.</span></span>

### <a name="bot"></a><span data-ttu-id="af852-138">Bot</span><span class="sxs-lookup"><span data-stu-id="af852-138">Bot</span></span>

<span data-ttu-id="af852-139">Um bot não é necessário, mas é uma ótima maneira de se comunicar de forma direta e privada com seus usuários.</span><span class="sxs-lookup"><span data-stu-id="af852-139">A bot isn't required, but it's a great way to communicate directly and privately with your users.</span></span> <span data-ttu-id="af852-140">A notificação é uma das funções mais importantes de um aplicativo pessoal e qual é a melhor maneira de notificá-lo do que com comunicação direta?</span><span class="sxs-lookup"><span data-stu-id="af852-140">Notification is one of the most important functions of a personal app, and what better way to notify than with direct communication?</span></span>

<span data-ttu-id="af852-141">Os bots entregam mensagens na forma de cartões, que podem fornecer informações específicas (como um alerta que o novo conteúdo está disponível) ou atualizações amplas (como uma lista de tarefas diárias).</span><span class="sxs-lookup"><span data-stu-id="af852-141">Bots deliver messages in the form of cards, which can provide specific information (like an alert that new content is available) or broad updates (like a daily to-do list).</span></span> <span data-ttu-id="af852-142">Para obter informações adicionais sobre como projetar bots efetivos, consulte: [design de bot](../../bots/design/bots.md).</span><span class="sxs-lookup"><span data-stu-id="af852-142">For additional information on designing effective bots see: [Bot design](../../bots/design/bots.md).</span></span>

![Saudação de bot](~/assets/images/Personal-apps-Bot.png)

### <a name="help-and-settings"></a><span data-ttu-id="af852-144">Ajuda e configurações</span><span class="sxs-lookup"><span data-stu-id="af852-144">Help and Settings</span></span>

<span data-ttu-id="af852-145">O conteúdo da ajuda permite que os usuários descubram as nuances de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af852-145">Help content enables users to discover the nuances of your app.</span></span> <span data-ttu-id="af852-146">Adicione uma guia **configurações** para ter a possibilidade de personalizá-la.</span><span class="sxs-lookup"><span data-stu-id="af852-146">Add a **Settings** tab to give them the ability to further customize it.</span></span>

### <a name="about"></a><span data-ttu-id="af852-147">Sobre</span><span class="sxs-lookup"><span data-stu-id="af852-147">About</span></span>

<span data-ttu-id="af852-148">Inclua uma guia **sobre** para fornecer informações como números de versão, recursos, privacidade e links de permissões.</span><span class="sxs-lookup"><span data-stu-id="af852-148">Include an **About** tab to provide information like version number, capabilities, privacy, and permissions links.</span></span>

## <a name="best-practices"></a><span data-ttu-id="af852-149">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="af852-149">Best practices</span></span>

### <a name="communicate-directly-with-your-users"></a><span data-ttu-id="af852-150">Comunicar-se diretamente com seus usuários</span><span class="sxs-lookup"><span data-stu-id="af852-150">Communicate directly with your users</span></span>

<span data-ttu-id="af852-151">Use um bot para notificar os usuários sobre alterações e novos recursos.</span><span class="sxs-lookup"><span data-stu-id="af852-151">Use a bot to notify users of changes and new features.</span></span>

### <a name="customize-your-tabs"></a><span data-ttu-id="af852-152">Personalizar suas guias...</span><span class="sxs-lookup"><span data-stu-id="af852-152">Customize your tabs...</span></span>

<span data-ttu-id="af852-153">Sinta-se à vontade para adicionar outras guias que ajudarão os usuários a realizar tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="af852-153">Feel free to add other tabs that will help your users accomplish specific tasks.</span></span>

### <a name="and-make-them-relevant-to-every-user"></a><span data-ttu-id="af852-154">... e torná-los relevantes a todos os usuários</span><span class="sxs-lookup"><span data-stu-id="af852-154">...and make them relevant to every user</span></span>

<span data-ttu-id="af852-155">Cada guia que você declarar no manifesto do aplicativo ficará visível para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="af852-155">Every tab you declare in your app manifest will be visible to all users.</span></span> <span data-ttu-id="af852-156">Por exemplo, se seu aplicativo pessoal é uma ferramenta de relatório de despesas que é usada por gerentes e funcionários, uma guia de **aprovação** deve fornecer conteúdo que seja significativo para ambas as funções.</span><span class="sxs-lookup"><span data-stu-id="af852-156">For example, if your personal app is an expense reporting tool that is used by both managers and employees, an **Approval** tab should provide content that is meaningful to both roles.</span></span>
