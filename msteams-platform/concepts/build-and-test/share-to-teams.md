---
title: Criar um botão compartilhar para o Teams
description: Como adicionar o botão Compartilhar ao Teams inserido em seu site
ms.topic: reference
keywords: Compartilhar o compartilhamento do Teams com o Teams
ms.openlocfilehash: 46091c957137cc871095ca6a57c0d61fa79d9458
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014331"
---
# <a name="create-a-share-to-teams-button-for-your-website"></a>Criar um botão Compartilhar no Teams para o seu site

>[!NOTE]
> * Há suporte apenas para as versões de área de trabalho do Edge e do Chrome.
> * Não há suporte para o uso de contas de convidado ou Freemium.

Sites de terceiros podem usar o script do launcher para inserir botões de compartilhamento no Teams em suas páginas da Web, que iniciarão a experiência Compartilhar com o Teams em uma janela pop-up quando clicado. Isso permitirá que você compartilhe um link diretamente com qualquer pessoa ou canal do Microsoft Teams sem alternar contexto.

![Compartilhar com o pop-up do Teams](~/assets/images/share-to-teams-popup.png)

## <a name="how-to-embed-a-share-to-teams-button"></a>Como inserir um botão Compartilhar no Teams

Primeiro, você precisará adicionar o `launcher.js` script à sua página da Web.

```html
<script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
```

Em seguida, adicione um elemento HTML à sua página da Web com o atributo de classe e `teams-share-button` o link para compartilhar no `data-href` atributo.

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>">
</div>
```

Isso adicionará o ícone do Microsoft Teams ao seu site.

![Ícone Compartilhar com o Teams](~/assets/icons/share-to-teams-icon.png)

Opcionalmente, se você quiser um tamanho de ícone diferente para o botão Compartilhar com o Teams, use o `data-icon-px-size` atributo.

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-icon-px-size="64">
</div>
```

Se você sabe que a visualização da URL do seu link a ser compartilhada não renderizará bem no Teams (por exemplo, o link exigiria autenticação do usuário), você pode desabilitar a visualização da URL adicionando o atributo `data-preview` definido como `false` .

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-preview="false">
</div>
```

Se sua página renderizar dinamicamente o conteúdo, você poderá usar o método para forçar o botão Compartilhar a renderizar no `shareToMicrosoftTeams.renderButtons()` local apropriado no pipeline. 

## <a name="crafting-your-website-preview"></a>Criar a visualização do seu site

Quando seu site for compartilhado com o Teams, o cartão inserido no canal selecionado conterá uma visualização do seu site. Você pode controlar o comportamento dessa visualização garantindo que os metadados apropriados são adicionados ao site que está sendo compartilhado (a `data-href` URL). A tabela abaixo descreve as marcas necessárias. Você pode usar as versões padrão html ou a versão do Open Graph.

Para que a visualização seja exibida, você deve:

* Inclua uma imagem em miniatura ou um título e uma descrição (para melhores resultados, inclua todos os três).
* A URL que está sendo compartilhada não pode exigir autenticação. Se isso acontecer, você ainda poderá compartilhá-lo, mas a visualização não será criada.

|Valor|Marca Meta| Abrir o Graph|
|----|----|----|
|Título|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Descrição|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Imagem em miniatura| nenhum |`<meta property="og:image" content="http://example.com/image.jpg">`|

## <a name="share-to-teams-for-education"></a>Compartilhar com o Teams para Educação

Para professores que usam o botão Compartilhar com o Teams, você terá uma opção adicional `Create an Assignment` para. Isso permite que você crie rapidamente uma atribuição na Equipe escolhida com base no link compartilhado.

![Compartilhar com o pop-up do Teams](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a>Definição launcher.js completa

| Propriedade | Atributo HTML | Tipo | Padrão | Descrição |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | string | n/d | O href do conteúdo a ser compartilhá-lo. |
| visualização | `data-preview` | booliana (como uma cadeia de caracteres) | `true` | Se deve ou não mostrar uma visualização do conteúdo a ser compartilhá-lo. |
| iconPxSize | `data-icon-px-size` | número (como uma cadeia de caracteres) | `32` | O tamanho em pixels do botão Compartilhar para Teams a ser renderização. |
| msgText | `data-msg-text` | string | n/d | Texto padrão a ser inserido antes do link na caixa de redação de mensagem (limite de 200 caracteres) |
| assignInstr | `data-assign-instr` | string | n/d | Texto padrão a ser inserido no campo de atribuições "Instruções" (limite de 200 caracteres) |
| assignTitle | `data-assign-title` | string | n/d | Texto padrão a ser inserido no campo de atribuições "Título" (limite de 50 caracteres) |

### <a name="methods"></a>Métodos

**`shareToMicrosoftTeams.renderButtons(options)`**

`options` (opcional): `{ elements?: HTMLElement[] }`

Renderiza todos os botões de compartilhamento atualmente na página. Se um objeto opcional for fornecido com uma lista de elementos, esses elementos `options` serão renderizados em botões de compartilhamento.

### <a name="setting-default-form-values"></a>Definindo valores de formulário padrão

Opcionalmente, você pode optar por definir valores padrão para os seguintes campos no formulário Compartilhar com o Teams:

* Diga algo sobre isso ( `msgText` )
* Instruções de atribuição ( `assignInstr` )
* Título da Atribuição ( `assignTitle` )

#### <a name="example-default-form-values"></a>Exemplo: valores de formulário padrão

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```
