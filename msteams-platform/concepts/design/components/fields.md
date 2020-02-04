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
# <a name="fields-and-flyouts"></a>Campos e submenus

---

## <a name="fields"></a>Campos

Os campos são áreas onde os usuários podem inserir texto.

### <a name="padding-and-size"></a>Enchimento e tamanho

Campos de texto de linha única são uma altura fixa de medianiz 32px para corresponder à altura de outros componentes. Alguns campos de texto, como campos de descrição, podem ser mais altos verticalmente para permitir mais texto.
[!include[Padding and size](~/includes/design/fields-image-padding.html)]

### <a name="states"></a>Determina

Estes são os Estados dos nossos campos de texto. Os campos de texto existem em diferentes Estados. Temos designs específicos dedicados a nove possíveis cenários, incluindo (de cima para baixo): colocar o campo de texto, o teclado em foco e o cursor dentro do campo, teclado em foco com o texto inserido, tratamento de erros bem-sucedido, falha no tratamento de erros, texto não criptografado campo (incluindo um ícone X), campo de pesquisa (incluindo um ícone de pesquisa), campo de carregamento e um campo desabilitado.
[!include[Field states](~/includes/design/fields-image-states.html)]

### <a name="formatting-help-text-and-labels"></a>Formatando texto de ajuda e rótulos

Os campos podem conter texto de espaço reservado para fornecer um exemplo do tipo de informação necessário. Eles também podem manter rótulos que dão ao usuário mais contexto. Dentro de um campo, seu texto deve sempre ser justificado à esquerda. Também utilizamos maiúsculas de minúsculas.

Usamos o Segoe UI regular em 12 pontos (legenda) e $app-cinza-02 para rótulos. Para o texto de ajuda, usamos o Segoe UI regular em 14 pt (base) e $app-Gray-02.
[!include[Fields typography](~/includes/design/fields-image-typography.html)]

---

## <a name="flyouts"></a>Submenus

Os submenus são mais simples do que as caixas de diálogo e podem ser ignorados rapidamente. Eles podem conter botões, campos e outros componentes.
[!include[Flyouts](~/includes/design/flyouts-image.html)]

### <a name="sizing-and-padding"></a>Dimensionamento e preenchimento

Recomendamos um preenchimento 16px à esquerda e à direita do conteúdo.
[!include[Flyouts size and padding](~/includes/design/flyouts-image-sizepadding.html)]

### <a name="placement"></a>Posicionamento

Os submenus são contextuais e devem ser colocados acima, abaixo ou ao lado do elemento que o disparou.

### <a name="scrolling"></a>Rolagem

O cabeçalho permanece no local para dar contexto ao conteúdo que está sendo rolado.
[!include[Flyouts scrolling](~/includes/design/flyouts-image-scrolling.html)]

## <a name="mobile"></a>Mobile

Os campos são caixas de entrada de texto que aceitam entrada de usuários. Menus de menu suspenso são janelas pop-up horizontais que aparecem no painel superior e podem ser usadas para mostrar mais detalhes sobre um item.

### <a name="field-controls"></a>Controles de campo

[!include[Mobile fields](~/includes/design/fields-mobile-image.html)]

### <a name="flyout-menu-list-controls"></a>Menu de menus de lista

[!include[Mobile flyout menu controls](~/includes/design/flyout-menu-mobile-image.html)]
