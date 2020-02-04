---
title: Referência de diretrizes de design
description: Descreve as diretrizes para usar campos e submenus em seus aplicativos
keywords: Diretrizes de design de equipes referência de campos e submenus
ms.openlocfilehash: 0f62d38bf961ae79b05c599638cefb3c76f46ed4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672882"
---
# <a name="fields-and-flyouts"></a><span data-ttu-id="6b601-104">Campos e submenus</span><span class="sxs-lookup"><span data-stu-id="6b601-104">Fields and flyouts</span></span>

---

## <a name="fields"></a><span data-ttu-id="6b601-105">Campos</span><span class="sxs-lookup"><span data-stu-id="6b601-105">Fields</span></span>

<span data-ttu-id="6b601-106">Os campos são áreas onde os usuários podem inserir texto.</span><span class="sxs-lookup"><span data-stu-id="6b601-106">Fields are areas where users can input text.</span></span>

### <a name="padding-and-size"></a><span data-ttu-id="6b601-107">Enchimento e tamanho</span><span class="sxs-lookup"><span data-stu-id="6b601-107">Padding and size</span></span>

<span data-ttu-id="6b601-108">Campos de texto de linha única são uma altura fixa de medianiz 32px para corresponder à altura de outros componentes.</span><span class="sxs-lookup"><span data-stu-id="6b601-108">Single-line text fields are a fixed height of 32px to match the height of other components.</span></span> <span data-ttu-id="6b601-109">Alguns campos de texto, como campos de descrição, podem ser mais altos verticalmente para permitir mais texto.</span><span class="sxs-lookup"><span data-stu-id="6b601-109">Some text fields such as description fields may be taller vertically to allow more text.</span></span>
[!include[Padding and size](~/includes/design/fields-image-padding.html)]

### <a name="states"></a><span data-ttu-id="6b601-110">Determina</span><span class="sxs-lookup"><span data-stu-id="6b601-110">States</span></span>

<span data-ttu-id="6b601-111">Estes são os Estados dos nossos campos de texto.</span><span class="sxs-lookup"><span data-stu-id="6b601-111">These are the states of our text fields.</span></span> <span data-ttu-id="6b601-112">Os campos de texto existem em diferentes Estados.</span><span class="sxs-lookup"><span data-stu-id="6b601-112">Text fields exist in different states.</span></span> <span data-ttu-id="6b601-113">Temos designs específicos dedicados a nove possíveis cenários, incluindo (de cima para baixo): colocar o campo de texto, o teclado em foco e o cursor dentro do campo, teclado em foco com o texto inserido, tratamento de erros bem-sucedido, falha no tratamento de erros, texto não criptografado campo (incluindo um ícone X), campo de pesquisa (incluindo um ícone de pesquisa), campo de carregamento e um campo desabilitado.</span><span class="sxs-lookup"><span data-stu-id="6b601-113">We have specific designs dedicated to nine possible scenarios, including (top to bottom): Resting text field, Keyboard in focus and cursor inside the field, Keyboard in focus with text entered, Error handling has succeeded, Error handling has failed, Clear text field (including an X icon), Search field (including a Search icon), Loading field, and a Disabled field.</span></span>
[!include[Field states](~/includes/design/fields-image-states.html)]

### <a name="formatting-help-text-and-labels"></a><span data-ttu-id="6b601-114">Formatando texto de ajuda e rótulos</span><span class="sxs-lookup"><span data-stu-id="6b601-114">Formatting help text and labels</span></span>

<span data-ttu-id="6b601-115">Os campos podem conter texto de espaço reservado para fornecer um exemplo do tipo de informação necessário.</span><span class="sxs-lookup"><span data-stu-id="6b601-115">Fields can contain placeholder text to give an example of the kind of information that is required.</span></span> <span data-ttu-id="6b601-116">Eles também podem manter rótulos que dão ao usuário mais contexto.</span><span class="sxs-lookup"><span data-stu-id="6b601-116">They can also hold labels that give the user more context.</span></span> <span data-ttu-id="6b601-117">Dentro de um campo, seu texto deve sempre ser justificado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="6b601-117">Within a field, your text should always be justified left.</span></span> <span data-ttu-id="6b601-118">Também utilizamos maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="6b601-118">We use sentence casing throughout here, as well.</span></span>

<span data-ttu-id="6b601-119">Usamos o Segoe UI regular em 12 pontos (legenda) e $app-cinza-02 para rótulos.</span><span class="sxs-lookup"><span data-stu-id="6b601-119">We use Segoe UI Regular at 12 pt (caption) and $app-gray-02 for labels.</span></span> <span data-ttu-id="6b601-120">Para o texto de ajuda, usamos o Segoe UI regular em 14 pt (base) e $app-Gray-02.</span><span class="sxs-lookup"><span data-stu-id="6b601-120">For help text, we use Segoe UI Regular at 14 pt (base) and $app-gray-02.</span></span>
[!include[Fields typography](~/includes/design/fields-image-typography.html)]

---

## <a name="flyouts"></a><span data-ttu-id="6b601-121">Submenus</span><span class="sxs-lookup"><span data-stu-id="6b601-121">Flyouts</span></span>

<span data-ttu-id="6b601-122">Os submenus são mais simples do que as caixas de diálogo e podem ser ignorados rapidamente.</span><span class="sxs-lookup"><span data-stu-id="6b601-122">Flyouts are more lightweight than dialogs and can be dismissed quickly.</span></span> <span data-ttu-id="6b601-123">Eles podem conter botões, campos e outros componentes.</span><span class="sxs-lookup"><span data-stu-id="6b601-123">They can contain buttons, fields, and other components.</span></span>
[!include[Flyouts](~/includes/design/flyouts-image.html)]

### <a name="sizing-and-padding"></a><span data-ttu-id="6b601-124">Dimensionamento e preenchimento</span><span class="sxs-lookup"><span data-stu-id="6b601-124">Sizing and padding</span></span>

<span data-ttu-id="6b601-125">Recomendamos um preenchimento 16px à esquerda e à direita do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="6b601-125">We recommend a 16px padding to the left and right of the content.</span></span>
[!include[Flyouts size and padding](~/includes/design/flyouts-image-sizepadding.html)]

### <a name="placement"></a><span data-ttu-id="6b601-126">Posicionamento</span><span class="sxs-lookup"><span data-stu-id="6b601-126">Placement</span></span>

<span data-ttu-id="6b601-127">Os submenus são contextuais e devem ser colocados acima, abaixo ou ao lado do elemento que o disparou.</span><span class="sxs-lookup"><span data-stu-id="6b601-127">Flyouts are contextual and should be placed above, below, or beside the element that triggered it.</span></span>

### <a name="scrolling"></a><span data-ttu-id="6b601-128">Rolagem</span><span class="sxs-lookup"><span data-stu-id="6b601-128">Scrolling</span></span>

<span data-ttu-id="6b601-129">O cabeçalho permanece no local para dar contexto ao conteúdo que está sendo rolado.</span><span class="sxs-lookup"><span data-stu-id="6b601-129">The header remains in place to give context to the content being scrolled.</span></span>
[!include[Flyouts scrolling](~/includes/design/flyouts-image-scrolling.html)]

## <a name="mobile"></a><span data-ttu-id="6b601-130">Mobile</span><span class="sxs-lookup"><span data-stu-id="6b601-130">Mobile</span></span>

<span data-ttu-id="6b601-131">Os campos são caixas de entrada de texto que aceitam entrada de usuários.</span><span class="sxs-lookup"><span data-stu-id="6b601-131">Fields are text-entry boxes that accept input from users.</span></span> <span data-ttu-id="6b601-132">Menus de menu suspenso são janelas pop-up horizontais que aparecem no painel superior e podem ser usadas para mostrar mais detalhes sobre um item.</span><span class="sxs-lookup"><span data-stu-id="6b601-132">Flyout menus are horizontal pop-up windows that appear from the top pane and can be used to show more detail about an item.</span></span>

### <a name="field-controls"></a><span data-ttu-id="6b601-133">Controles de campo</span><span class="sxs-lookup"><span data-stu-id="6b601-133">Field Controls</span></span>

[!include[Mobile fields](~/includes/design/fields-mobile-image.html)]

### <a name="flyout-menu-list-controls"></a><span data-ttu-id="6b601-134">Menu de menus de lista</span><span class="sxs-lookup"><span data-stu-id="6b601-134">Flyout menu list controls</span></span>

[!include[Mobile flyout menu controls](~/includes/design/flyout-menu-mobile-image.html)]
