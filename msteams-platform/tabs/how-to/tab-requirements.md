---
title: Pré-requisitos
author: surbhigupta
description: Todas as guias Microsoft Teams devem seguir esses requisitos.
keywords: canal de grupo de guias do teams configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: b54fc7235132a9253f6eecc62417f786bf4aa45c
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140184"
---
# <a name="prerequisites"></a><span data-ttu-id="2d186-104">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2d186-104">Prerequisites</span></span>

<span data-ttu-id="2d186-105">Teams guias devem seguir os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="2d186-105">Teams tabs must adhere to the following prerequisites:</span></span>

* <span data-ttu-id="2d186-106">Você deve permitir que suas páginas de tabulação sejam mostradas em um iFrame, usando cabeçalhos de resposta HTTP X-Frame-Options e Content-Security-Policy.</span><span class="sxs-lookup"><span data-stu-id="2d186-106">You must allow your tab pages to be shown in an iFrame, using X-Frame-Options and Content-Security-Policy HTTP response headers.</span></span>
  * <span data-ttu-id="2d186-107">Definir o header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`</span><span class="sxs-lookup"><span data-stu-id="2d186-107">Set header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`</span></span>
  * <span data-ttu-id="2d186-108">Para compatibilidade com o Internet Explorer 11, de definir `X-Content-Security-Policy` .</span><span class="sxs-lookup"><span data-stu-id="2d186-108">For Internet Explorer 11 compatibility, set `X-Content-Security-Policy`.</span></span>
  * <span data-ttu-id="2d186-109">Como alternativa, de definir o header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` .</span><span class="sxs-lookup"><span data-stu-id="2d186-109">Alternately, set header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/`.</span></span> <span data-ttu-id="2d186-110">Esse header é preterido, mas ainda é aceito pela maioria dos navegadores.</span><span class="sxs-lookup"><span data-stu-id="2d186-110">This header is deprecated but still accepted by most browsers.</span></span>

* <span data-ttu-id="2d186-111">Normalmente, como uma proteção contra o clickjacking, as páginas de logon não são renderizações em iFrames.</span><span class="sxs-lookup"><span data-stu-id="2d186-111">Typically, as a safeguard against clickjacking, login pages do not render in iFrames.</span></span> <span data-ttu-id="2d186-112">Sua lógica de autenticação precisa usar um método diferente de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="2d186-112">Your authentication logic needs to use a method other than redirect.</span></span> <span data-ttu-id="2d186-113">Por exemplo, use autenticação baseada em token ou cookie.</span><span class="sxs-lookup"><span data-stu-id="2d186-113">For example, use token-based or cookie-based authentication.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2d186-114">O Chrome 80, agendado para lançamento no início de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão.</span><span class="sxs-lookup"><span data-stu-id="2d186-114">Chrome 80, scheduled for release in early 2020, introduces new cookie values and imposes cookie policies by default.</span></span> <span data-ttu-id="2d186-115">É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador.</span><span class="sxs-lookup"><span data-stu-id="2d186-115">It is recommended that you set the intended use for your cookies rather than rely on default browser behavior.</span></span> <span data-ttu-id="2d186-116">Para obter mais informações, consulte [atributo cookie SameSite](../../resources/samesite-cookie-update.md).</span><span class="sxs-lookup"><span data-stu-id="2d186-116">For more information, see [SameSite cookie attribute](../../resources/samesite-cookie-update.md).</span></span>

* <span data-ttu-id="2d186-117">Os navegadores aderem a uma restrição de política de mesma origem.</span><span class="sxs-lookup"><span data-stu-id="2d186-117">Browsers adhere to a same-origin policy restriction.</span></span> <span data-ttu-id="2d186-118">Ele impede que as páginas da Web fazem solicitações para domínios diferentes da página da Web atendida.</span><span class="sxs-lookup"><span data-stu-id="2d186-118">It prevents webpages from making requests to different domains than the served web page.</span></span> <span data-ttu-id="2d186-119">No entanto, você pode redirecionar a página de configuração ou conteúdo para outro domínio ou subdomínio.</span><span class="sxs-lookup"><span data-stu-id="2d186-119">However, you can redirect the configuration or content page to another domain or subdomain.</span></span> <span data-ttu-id="2d186-120">Sua lógica de navegação entre domínios deve permitir que o cliente Teams valide a origem em relação a uma lista estática no manifesto do aplicativo ao carregar ou se comunicar `validDomains` com a guia.</span><span class="sxs-lookup"><span data-stu-id="2d186-120">Your cross-domain navigation logic must allow the Teams client to validate the origin against a static `validDomains` list in the app manifest when loading or communicating with the tab.</span></span>

* <span data-ttu-id="2d186-121">Você deve estilar suas guias com base Teams tema, design e intenção do cliente.</span><span class="sxs-lookup"><span data-stu-id="2d186-121">You must style your tabs based on the Teams client's theme, design, and intent.</span></span> <span data-ttu-id="2d186-122">Normalmente, as guias funcionam melhor quando são criadas para atender a uma necessidade específica e se concentrar em um pequeno conjunto de tarefas ou em um subconjunto de dados relevante para o local do canal da guia.</span><span class="sxs-lookup"><span data-stu-id="2d186-122">Typically, tabs work best when they are built to address a specific need and focus on a small set of tasks or a subset of data that is relevant to the tab's channel location.</span></span>

* <span data-ttu-id="2d186-123">Em sua página de conteúdo, adicione uma referência ao [Microsoft Teams SDK](/javascript/api/overview/msteams-client) do cliente JavaScript usando marcas de script.</span><span class="sxs-lookup"><span data-stu-id="2d186-123">Within your content page, add a reference to [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) using script tags.</span></span> <span data-ttu-id="2d186-124">Depois que sua página for carregada, faça uma chamada `microsoftTeams.initialize()` para , caso contrário, sua página não será exibida.</span><span class="sxs-lookup"><span data-stu-id="2d186-124">After your page loads, make a call to `microsoftTeams.initialize()`, otherwise your page is not displayed.</span></span>

* <span data-ttu-id="2d186-125">Para que a autenticação funcione em clientes móveis, você deve atualizar Teams SDK JavaScript para pelo menos a versão 1.4.1.</span><span class="sxs-lookup"><span data-stu-id="2d186-125">For authentication to work on mobile clients, you must upgrade Teams JavaScript SDK to at least version 1.4.1.</span></span>

* <span data-ttu-id="2d186-126">Se você optar por fazer com que seu canal ou guia de grupo apareça Teams clientes móveis, a configuração deve ter um `setSettings()` valor para a `websiteUrl` propriedade.</span><span class="sxs-lookup"><span data-stu-id="2d186-126">If you choose to have your channel or group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property.</span></span>

* <span data-ttu-id="2d186-127">A guia Teams MS não dá suporte à capacidade de carregar sites da intranet que usam certificados auto-assinados.</span><span class="sxs-lookup"><span data-stu-id="2d186-127">MS Teams tab does not support the ability to load intranet websites that use self-signed certificates.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d186-128">Também consulte</span><span class="sxs-lookup"><span data-stu-id="2d186-128">See also</span></span>

* [<span data-ttu-id="2d186-129">Teams guias</span><span class="sxs-lookup"><span data-stu-id="2d186-129">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="2d186-130">Criar um canal ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="2d186-130">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="2d186-131">Criar uma página de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2d186-131">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
* [<span data-ttu-id="2d186-132">Criar uma página de configuração</span><span class="sxs-lookup"><span data-stu-id="2d186-132">Create a configuration page</span></span>](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [<span data-ttu-id="2d186-133">Criar uma página de remoção para sua guia</span><span class="sxs-lookup"><span data-stu-id="2d186-133">Create a removal page for your tab</span></span>](~/tabs/how-to/create-tab-pages/removal-page.md)
* [<span data-ttu-id="2d186-134">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="2d186-134">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="2d186-135">Obtenha contexto para sua guia</span><span class="sxs-lookup"><span data-stu-id="2d186-135">Get context for your tab</span></span>](~/tabs/how-to/access-teams-context.md)
* [<span data-ttu-id="2d186-136">Criar guias com Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="2d186-136">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)
* [<span data-ttu-id="2d186-137">Link de guias desdobradas e Exibição de Estágio</span><span class="sxs-lookup"><span data-stu-id="2d186-137">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)
* [<span data-ttu-id="2d186-138">Criar abas para conversação</span><span class="sxs-lookup"><span data-stu-id="2d186-138">Create conversational tabs</span></span>](~/tabs/how-to/conversational-tabs.md)
* [<span data-ttu-id="2d186-139">Alterações na margem da guia</span><span class="sxs-lookup"><span data-stu-id="2d186-139">Tab margin changes</span></span>](~/resources/removing-tab-margins.md)

## <a name="next-step"></a><span data-ttu-id="2d186-140">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="2d186-140">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2d186-141">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="2d186-141">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
