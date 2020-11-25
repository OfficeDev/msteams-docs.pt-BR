---
title: Referência de diretrizes de design
description: Descreve as diretrizes para usar cores nos aplicativos
keywords: Diretrizes de design de equipes referência de componentes de referência
ms.openlocfilehash: dab223891e88615b52386d3692d4a98607d6d449
ms.sourcegitcommit: aca9990e1f84b07b9e77c08bfeca4440eb4e64f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "49409061"
---
# <a name="color"></a><span data-ttu-id="b2eab-104">Cor</span><span class="sxs-lookup"><span data-stu-id="b2eab-104">Color</span></span>

<span data-ttu-id="b2eab-105">Usar nossa paleta neutra aprovada para planos de fundo, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="b2eab-105">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="b2eab-106">Como o Microsoft Teams tem dois temas de cor (claros e escuros), é uma boa ideia garantir que seu aplicativo fique ótimo nos dois temas.</span><span class="sxs-lookup"><span data-stu-id="b2eab-106">Since Teams has two color themes (light and dark), it’s a good idea to make sure your app looks great in both themes.</span></span>

### <a name="app-black-252423"></a><span data-ttu-id="b2eab-107">$app-preto (#252423)</span><span class="sxs-lookup"><span data-stu-id="b2eab-107">$app-black (#252423)</span></span>

<span data-ttu-id="b2eab-108">Nossa cor de texto usada com mais frequência.</span><span class="sxs-lookup"><span data-stu-id="b2eab-108">Our most commonly-used text color.</span></span> <span data-ttu-id="b2eab-109">Podemos usá-lo em cinco níveis de opacidade para o texto.</span><span class="sxs-lookup"><span data-stu-id="b2eab-109">We use it at five levels of opacity for text.</span></span> <span data-ttu-id="b2eab-110">O texto deve ser usado principalmente em 100%, 74%, 64% de opacidade, pois é acessível.</span><span class="sxs-lookup"><span data-stu-id="b2eab-110">Text should mainly be used at 100%, 74%, 64% opacity since it is accessible.</span></span> <span data-ttu-id="b2eab-111">O texto em 52% e 36% deve ser usado com moderação, já que não está acessível.</span><span class="sxs-lookup"><span data-stu-id="b2eab-111">Text at 52% and 36% should be used sparingly since it is not accessible.</span></span>

[!include[Appblack color and text](~/includes/design/color-image-appblack-text.html)]

1. <span data-ttu-id="b2eab-112">100%-cabeçalhos e texto base</span><span class="sxs-lookup"><span data-stu-id="b2eab-112">100% - Headers and base text</span></span>
2. <span data-ttu-id="b2eab-113">74%-rótulos, subtítulos, atribuições e botões de ícone</span><span class="sxs-lookup"><span data-stu-id="b2eab-113">74% - Labels, subheads, attributions, and icon buttons</span></span>
3. <span data-ttu-id="b2eab-114">64%-visualizações de mensagem, texto de ajuda (não mostrado)</span><span class="sxs-lookup"><span data-stu-id="b2eab-114">64% - Message previews, help text (not shown)</span></span>
4. <span data-ttu-id="b2eab-115">52%-carimbos de data/hora</span><span class="sxs-lookup"><span data-stu-id="b2eab-115">52% - Timestamps</span></span>
5. <span data-ttu-id="b2eab-116">36%-texto desabilitado</span><span class="sxs-lookup"><span data-stu-id="b2eab-116">36% - Disabled text</span></span>

<span data-ttu-id="b2eab-117">Também usamos `$app-black` em outros opacities para alguns elementos da interface do usuário:</span><span class="sxs-lookup"><span data-stu-id="b2eab-117">We also use `$app-black` at other opacities for some UI elements:</span></span>

[!include[Appblack color and text](~/includes/design/color-image-appblack-ui.html)]

1. <span data-ttu-id="b2eab-118">planos de fundo de 14%</span><span class="sxs-lookup"><span data-stu-id="b2eab-118">14% - Banner backgrounds</span></span>
2. <span data-ttu-id="b2eab-119">5%-botões desabilitados e bordas de cartão</span><span class="sxs-lookup"><span data-stu-id="b2eab-119">5% - Disabled button and card borders</span></span>

### <a name="default-theme-color-ramp"></a><span data-ttu-id="b2eab-120">Rampa de cores de tema padrão</span><span class="sxs-lookup"><span data-stu-id="b2eab-120">Default theme color ramp</span></span>

<span data-ttu-id="b2eab-121">Consulte a caneta [Microsoft Teams design Guidelines – rampa de cores de tema padrão](https://codepen.io/msteams/pen/KyPmqL/) no CodePen.</span><span class="sxs-lookup"><span data-stu-id="b2eab-121">See the Pen [Microsoft Teams design guidelines - default theme color ramp](https://codepen.io/msteams/pen/KyPmqL/) on CodePen.</span></span>

<iframe height='620' scrolling='no' title='<span data-ttu-id="b2eab-122">Diretrizes de design do Microsoft Teams-rampa de cores de tema padrão</span><span class="sxs-lookup"><span data-stu-id="b2eab-122">Microsoft Teams design guidelines - default theme color ramp</span></span>' src='//codepen.io/msteams/embed/KyPmqL/?height=682&theme-id=31655&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="b2eab-123">Consulte a caneta <a href='https://codepen.io/msteams/pen/KyPmqL/'>Microsoft Teams design Guidelines-default Theme Color ramping</a> by Microsoft Teams (<a href='https://codepen.io/msteams'>@msteams</a>) no <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="b2eab-123">See the Pen <a href='https://codepen.io/msteams/pen/KyPmqL/'>Microsoft Teams design guidelines - default theme color ramp</a> by Microsoft Teams (<a href='https://codepen.io/msteams'>@msteams</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

### <a name="other-default-theme-colors"></a><span data-ttu-id="b2eab-124">Outras cores de tema padrão</span><span class="sxs-lookup"><span data-stu-id="b2eab-124">Other default theme colors</span></span>

<span data-ttu-id="b2eab-125">Consulte a caneta [Microsoft Teams design Guidelines-outras cores de tema padrão](https://codepen.io/msteams/pen/zPOdYJ/) no CodePen.</span><span class="sxs-lookup"><span data-stu-id="b2eab-125">See the Pen [Microsoft Teams design guidelines - other default theme colors](https://codepen.io/msteams/pen/zPOdYJ/) on CodePen.</span></span>

<iframe height='392' scrolling='no' title='<span data-ttu-id="b2eab-126">Diretrizes de design do Microsoft Teams-outras cores de temas padrão</span><span class="sxs-lookup"><span data-stu-id="b2eab-126">Microsoft Teams design guidelines - other default theme colors</span></span>' src='//codepen.io/msteams/embed/zPOdYJ/?height=442&theme-id=31655&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="b2eab-127">Consulte a caneta <a href='https://codepen.io/msteams/pen/zPOdYJ/'>Microsoft Teams design Guidelines-outras cores de temas padrão</a> pelo Microsoft Teams (<a href='https://codepen.io/msteams'>@msteams</a>) no <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="b2eab-127">See the Pen <a href='https://codepen.io/msteams/pen/zPOdYJ/'>Microsoft Teams design guidelines - other default theme colors</a> by Microsoft Teams (<a href='https://codepen.io/msteams'>@msteams</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

### <a name="dark-theme-color-ramp"></a><span data-ttu-id="b2eab-128">Rampa de cores do tema escuro</span><span class="sxs-lookup"><span data-stu-id="b2eab-128">Dark theme color ramp</span></span>

<span data-ttu-id="b2eab-129">Consulte a caneta [Microsoft Teams design Guidelines-rampa de cores de tema escuro](https://codepen.io/msteams/pen/BmBwjx/) no CodePen.</span><span class="sxs-lookup"><span data-stu-id="b2eab-129">See the Pen [Microsoft Teams design guidelines - dark theme color ramp](https://codepen.io/msteams/pen/BmBwjx/) on CodePen.</span></span>

<iframe height='798' scrolling='no' title='<span data-ttu-id="b2eab-130">Diretrizes de design do Microsoft Teams-rampa de cores de tema escuro</span><span class="sxs-lookup"><span data-stu-id="b2eab-130">Microsoft Teams design guidelines - dark theme color ramp</span></span>' src='//codepen.io/msteams/embed/BmBwjx/?height=846&theme-id=31655&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="b2eab-131">Consulte a caneta <a href='https://codepen.io/msteams/pen/BmBwjx/'>Microsoft Teams design Guidelines-rampa de cores de tema escuro</a> pelo Microsoft Teams (<a href='https://codepen.io/msteams'>@msteams</a>) no <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="b2eab-131">See the Pen <a href='https://codepen.io/msteams/pen/BmBwjx/'>Microsoft Teams design guidelines - dark theme color ramp</a> by Microsoft Teams (<a href='https://codepen.io/msteams'>@msteams</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>

> <span data-ttu-id="b2eab-132">**Observação:** A biblioteca msteams-UI-Styles-Core tem os valores reais codificados como variáveis.</span><span class="sxs-lookup"><span data-stu-id="b2eab-132">**Note:** The msteams-ui-styles-core library has the actual values coded as variables.</span></span> <span data-ttu-id="b2eab-133">Essas variáveis serão úteis se as cores forem atualizadas.</span><span class="sxs-lookup"><span data-stu-id="b2eab-133">These variables will be helpful if the colors are ever updated.</span></span>


### <a name="other-dark-theme-colors"></a><span data-ttu-id="b2eab-134">Outras cores de temas escuros</span><span class="sxs-lookup"><span data-stu-id="b2eab-134">Other dark theme colors</span></span>

<span data-ttu-id="b2eab-135">Consulte a caneta [Microsoft Teams design Guidelines-outras cores de tema escuro](https://codepen.io/msteams/pen/zPOEXN/) no CodePen.</span><span class="sxs-lookup"><span data-stu-id="b2eab-135">See the Pen [Microsoft Teams design guidelines - other dark theme colors](https://codepen.io/msteams/pen/zPOEXN/) on CodePen.</span></span>

<iframe height='390' scrolling='no' title='<span data-ttu-id="b2eab-136">Diretrizes de design do Microsoft Teams-outras cores de temas escuros</span><span class="sxs-lookup"><span data-stu-id="b2eab-136">Microsoft Teams design guidelines - other dark theme colors</span></span>' src='//codepen.io/msteams/embed/zPOEXN/?height=442&theme-id=31655&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'><span data-ttu-id="b2eab-137">Consulte a caneta <a href='https://codepen.io/msteams/pen/zPOEXN/'>Microsoft Teams design Guidelines-outras cores de temas escuros</a> pelo Microsoft Teams (<a href='https://codepen.io/msteams'>@msteams</a>) no <a href='https://codepen.io'>CodePen</a>.</span><span class="sxs-lookup"><span data-stu-id="b2eab-137">See the Pen <a href='https://codepen.io/msteams/pen/zPOEXN/'>Microsoft Teams design guidelines - other dark theme colors</a> by Microsoft Teams (<a href='https://codepen.io/msteams'>@msteams</a>) on <a href='https://codepen.io'>CodePen</a>.</span></span>
</iframe>
