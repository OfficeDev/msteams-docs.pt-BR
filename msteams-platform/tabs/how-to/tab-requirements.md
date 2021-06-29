---
title: Pré-requisitos
author: surbhigupta
description: Todas as guias Microsoft Teams devem seguir esses requisitos.
keywords: canal de grupo de guias do teams configurável
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 8566bb0457db76e4639593dcd67a0442749c0a31
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179934"
---
# <a name="prerequisites"></a><span data-ttu-id="9a49f-104">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9a49f-104">Prerequisites</span></span>

<span data-ttu-id="9a49f-105">Teams guias devem seguir os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="9a49f-105">Teams tabs must adhere to the following prerequisites:</span></span>

* <span data-ttu-id="9a49f-106">Você deve permitir que suas páginas de tabulação sejam mostradas em um iFrame, usando cabeçalhos de resposta HTTP X-Frame-Options e Content-Security-Policy.</span><span class="sxs-lookup"><span data-stu-id="9a49f-106">You must allow your tab pages to be shown in an iFrame, using X-Frame-Options and Content-Security-Policy HTTP response headers.</span></span>
  * <span data-ttu-id="9a49f-107">Definir o header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`</span><span class="sxs-lookup"><span data-stu-id="9a49f-107">Set header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`</span></span>
  * <span data-ttu-id="9a49f-108">Para compatibilidade com o Internet Explorer 11, de definir `X-Content-Security-Policy` .</span><span class="sxs-lookup"><span data-stu-id="9a49f-108">For Internet Explorer 11 compatibility, set `X-Content-Security-Policy`.</span></span>
  * <span data-ttu-id="9a49f-109">Como alternativa, de definir o header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` .</span><span class="sxs-lookup"><span data-stu-id="9a49f-109">Alternately, set header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/`.</span></span> <span data-ttu-id="9a49f-110">Esse header é preterido, mas ainda é aceito pela maioria dos navegadores.</span><span class="sxs-lookup"><span data-stu-id="9a49f-110">This header is deprecated but still accepted by most browsers.</span></span>

* <span data-ttu-id="9a49f-111">Normalmente, como uma proteção contra o clickjacking, as páginas de logon não são renderizações em iFrames.</span><span class="sxs-lookup"><span data-stu-id="9a49f-111">Typically, as a safeguard against clickjacking, login pages do not render in iFrames.</span></span> <span data-ttu-id="9a49f-112">Sua lógica de autenticação precisa usar um método diferente de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="9a49f-112">Your authentication logic needs to use a method other than redirect.</span></span> <span data-ttu-id="9a49f-113">Por exemplo, use autenticação baseada em token ou cookie.</span><span class="sxs-lookup"><span data-stu-id="9a49f-113">For example, use token-based or cookie-based authentication.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9a49f-114">O Chrome 80, agendado para lançamento no início de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão.</span><span class="sxs-lookup"><span data-stu-id="9a49f-114">Chrome 80, scheduled for release in early 2020, introduces new cookie values and imposes cookie policies by default.</span></span> <span data-ttu-id="9a49f-115">É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador.</span><span class="sxs-lookup"><span data-stu-id="9a49f-115">It is recommended that you set the intended use for your cookies rather than rely on default browser behavior.</span></span> <span data-ttu-id="9a49f-116">Para obter mais informações, consulte [atributo cookie SameSite](../../resources/samesite-cookie-update.md).</span><span class="sxs-lookup"><span data-stu-id="9a49f-116">For more information, see [SameSite cookie attribute](../../resources/samesite-cookie-update.md).</span></span>

* <span data-ttu-id="9a49f-117">Os navegadores aderem a uma restrição de política de mesma origem.</span><span class="sxs-lookup"><span data-stu-id="9a49f-117">Browsers adhere to a same-origin policy restriction.</span></span> <span data-ttu-id="9a49f-118">Ele impede que as páginas da Web fazem solicitações para domínios diferentes da página da Web atendida.</span><span class="sxs-lookup"><span data-stu-id="9a49f-118">It prevents webpages from making requests to different domains than the served web page.</span></span> <span data-ttu-id="9a49f-119">No entanto, você pode redirecionar a página de configuração ou conteúdo para outro domínio ou subdomínio.</span><span class="sxs-lookup"><span data-stu-id="9a49f-119">However, you can redirect the configuration or content page to another domain or subdomain.</span></span> <span data-ttu-id="9a49f-120">Sua lógica de navegação entre domínios deve permitir que o cliente Teams valide a origem em relação a uma lista estática no manifesto do aplicativo ao carregar ou se comunicar `validDomains` com a guia.</span><span class="sxs-lookup"><span data-stu-id="9a49f-120">Your cross-domain navigation logic must allow the Teams client to validate the origin against a static `validDomains` list in the app manifest when loading or communicating with the tab.</span></span>

* <span data-ttu-id="9a49f-121">Você deve estilar suas guias com base Teams tema, design e intenção do cliente.</span><span class="sxs-lookup"><span data-stu-id="9a49f-121">You must style your tabs based on the Teams client's theme, design, and intent.</span></span> <span data-ttu-id="9a49f-122">Normalmente, as guias funcionam melhor quando são criadas para atender a uma necessidade específica e se concentrar em um pequeno conjunto de tarefas ou em um subconjunto de dados relevante para o local do canal da guia.</span><span class="sxs-lookup"><span data-stu-id="9a49f-122">Typically, tabs work best when they are built to address a specific need and focus on a small set of tasks or a subset of data that is relevant to the tab's channel location.</span></span>

* <span data-ttu-id="9a49f-123">Em sua página de conteúdo, adicione uma referência ao [Microsoft Teams SDK](/javascript/api/overview/msteams-client) do cliente JavaScript usando marcas de script.</span><span class="sxs-lookup"><span data-stu-id="9a49f-123">Within your content page, add a reference to [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) using script tags.</span></span> <span data-ttu-id="9a49f-124">Depois que sua página for carregada, faça uma chamada `microsoftTeams.initialize()` para , caso contrário, sua página não será exibida.</span><span class="sxs-lookup"><span data-stu-id="9a49f-124">After your page loads, make a call to `microsoftTeams.initialize()`, otherwise your page is not displayed.</span></span>

* <span data-ttu-id="9a49f-125">Para que a autenticação funcione em clientes móveis, você deve atualizar Teams SDK JavaScript para pelo menos a versão 1.4.1.</span><span class="sxs-lookup"><span data-stu-id="9a49f-125">For authentication to work on mobile clients, you must upgrade Teams JavaScript SDK to at least version 1.4.1.</span></span>

* <span data-ttu-id="9a49f-126">Se você optar por fazer com que seu canal ou guia de grupo apareça Teams clientes móveis, a configuração deve ter um `setSettings()` valor para a `websiteUrl` propriedade.</span><span class="sxs-lookup"><span data-stu-id="9a49f-126">If you choose to have your channel or group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property.</span></span>

* <span data-ttu-id="9a49f-127">A guia Teams MS não dá suporte à capacidade de carregar sites da intranet que usam certificados auto-assinados.</span><span class="sxs-lookup"><span data-stu-id="9a49f-127">MS Teams tab does not support the ability to load intranet websites that use self-signed certificates.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a49f-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a49f-128">See also</span></span>

* [<span data-ttu-id="9a49f-129">Teams guias</span><span class="sxs-lookup"><span data-stu-id="9a49f-129">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="9a49f-130">Criar um canal ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="9a49f-130">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="9a49f-131">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="9a49f-131">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)

## <a name="next-step"></a><span data-ttu-id="9a49f-132">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="9a49f-132">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9a49f-133">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="9a49f-133">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
