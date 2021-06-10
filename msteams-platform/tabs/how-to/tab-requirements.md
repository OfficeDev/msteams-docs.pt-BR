---
title: Requisitos de guia
author: laujan
description: Todas as guias Microsoft Teams devem seguir esses requisitos.
keywords: canal de grupo de guias do teams configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 50d529697a80ca9ba78921009405f18fa021e802
ms.sourcegitcommit: 45c66faef8145abb903ef7118b9fa914c12aba2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2021
ms.locfileid: "52736758"
---
# <a name="tab-requirements"></a><span data-ttu-id="6b3e7-104">Requisitos de guia</span><span class="sxs-lookup"><span data-stu-id="6b3e7-104">Tab requirements</span></span>

<span data-ttu-id="6b3e7-105">Teams guias devem seguir os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="6b3e7-105">Teams tabs must adhere to the following requirements:</span></span>

* <span data-ttu-id="6b3e7-106">Você deve permitir que suas páginas de tabulação sejam atendidas em um iFrame, usando cabeçalhos de resposta HTTP X-Frame-Options e Content-Security-Policy.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-106">You must allow your tab pages to be served in an iFrame, using X-Frame-Options and Content-Security-Policy HTTP response headers.</span></span>
  * <span data-ttu-id="6b3e7-107">Definir o header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`</span><span class="sxs-lookup"><span data-stu-id="6b3e7-107">Set header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`</span></span>
  * <span data-ttu-id="6b3e7-108">Para compatibilidade com o Internet Explorer 11, de definir `X-Content-Security-Policy` .</span><span class="sxs-lookup"><span data-stu-id="6b3e7-108">For Internet Explorer 11 compatibility, set `X-Content-Security-Policy`.</span></span>
  * <span data-ttu-id="6b3e7-109">Como alternativa, de definir o header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` .</span><span class="sxs-lookup"><span data-stu-id="6b3e7-109">Alternately, set header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/`.</span></span> <span data-ttu-id="6b3e7-110">Esse header é preterido, mas ainda é aceito pela maioria dos navegadores.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-110">This header is deprecated but still accepted by most browsers.</span></span>
* <span data-ttu-id="6b3e7-111">Normalmente, como uma proteção contra o uso de cliques, as páginas de logon não são renderizações em iFrames.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-111">Typically, as a safeguard against click-jacking, login pages do not render in iFrames.</span></span> <span data-ttu-id="6b3e7-112">Sua lógica de autenticação precisa usar um método diferente de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-112">Your authentication logic needs to use a method other than redirect.</span></span> <span data-ttu-id="6b3e7-113">Por exemplo, use autenticação baseada em token ou cookie.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-113">For example, use token-based or cookie-based authentication.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6b3e7-114">O Chrome 80, agendado para lançamento no início de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-114">Chrome 80, scheduled for release in early 2020, introduces new cookie values and imposes cookie policies by default.</span></span> <span data-ttu-id="6b3e7-115">É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-115">It is recommended that you set the intended use for your cookies rather than rely on default browser behavior.</span></span> <span data-ttu-id="6b3e7-116">Para obter mais informações, consulte [SameSite cookie attribute 2020 update](../../resources/samesite-cookie-update.md).</span><span class="sxs-lookup"><span data-stu-id="6b3e7-116">For more information, see [SameSite cookie attribute 2020 update](../../resources/samesite-cookie-update.md).</span></span>

* <span data-ttu-id="6b3e7-117">Os navegadores aderem a uma restrição de política de mesma origem que impede uma página da Web de fazer solicitações para um domínio diferente do que aquele que atendeu a uma página da Web.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-117">Browsers adhere to a same-origin policy restriction that prevents a webpage from making requests to a different domain than the one that served a web page.</span></span> <span data-ttu-id="6b3e7-118">No entanto, você pode redirecionar a página de configuração ou conteúdo para outro domínio ou subdomínio.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-118">However, you can redirect the configuration or content page to another domain or subdomain.</span></span> <span data-ttu-id="6b3e7-119">Sua lógica de navegação entre domínios deve permitir que o cliente Teams valide a origem em relação a uma lista validDomains estática no manifesto do aplicativo ao carregar ou se comunicar com a guia.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-119">Your cross-domain navigation logic must allow the Teams client to validate the origin against a static validDomains list in the app manifest when loading or communicating with the tab.</span></span>

* <span data-ttu-id="6b3e7-120">Para criar uma experiência perfeita, você deve projetar suas guias com base Teams tema, design e intenção do cliente.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-120">To create a seamless experience, you must style your tabs based on the Teams client's theme, design, and intent.</span></span> <span data-ttu-id="6b3e7-121">Normalmente, as guias funcionam melhor quando são criadas para atender a uma necessidade específica e se concentrar em um pequeno conjunto de tarefas ou em um subconjunto de dados relevante para o local do canal da guia.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-121">Typically, tabs work best when they are built to address a specific need and focus on a small set of tasks or a subset of data that is relevant to the tab's channel location.</span></span>

* <span data-ttu-id="6b3e7-122">Em sua página de conteúdo, adicione uma referência ao [Microsoft Teams SDK](/javascript/api/overview/msteams-client) do cliente JavaScript usando marcas de script.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-122">Within your content page, add a reference to [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) using script tags.</span></span> <span data-ttu-id="6b3e7-123">Depois que sua página for carregada, faça uma chamada `microsoftTeams.initialize()` para , caso contrário, sua página não será exibida.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-123">After your page loads, make a call to `microsoftTeams.initialize()`, otherwise your page is not displayed.</span></span>

* <span data-ttu-id="6b3e7-124">Para que a autenticação funcione em clientes móveis, você deve atualizar Teams SDK JavaScript para pelo menos a versão 1.4.1.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-124">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

* <span data-ttu-id="6b3e7-125">Se você optar por fazer com que seu canal ou guia de grupo apareça Teams clientes móveis, a configuração deve ter um `setSettings()` valor para a `websiteUrl` propriedade.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-125">If you choose to have your channel or group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property.</span></span>

* <span data-ttu-id="6b3e7-126">A guia Teams MS não dá suporte à capacidade de carregar sites da intranet que usam certificados auto-assinados.</span><span class="sxs-lookup"><span data-stu-id="6b3e7-126">MS Teams tab does not support the ability to load intranet websites that use self-signed certificates.</span></span>

## <a name="next-step"></a><span data-ttu-id="6b3e7-127">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="6b3e7-127">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6b3e7-128">Crie uma guia pessoal personalizada usando Node.js e o Gerador Yeoman para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6b3e7-128">Create a custom personal tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>](~/tabs/quickstarts/create-personal-tab-node-yeoman.md)
