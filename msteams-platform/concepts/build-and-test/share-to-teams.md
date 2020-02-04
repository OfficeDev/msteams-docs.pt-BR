---
title: Botão compartilhar com o Teams
description: Como adicionar o botão compartilhar ao Teams incorporado no seu site
keywords: Compartilhar o Microsoft Teams para o Teams
ms.openlocfilehash: 219724e6ef3448db8a5b1fc70a519803255ffee6
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672800"
---
# <a name="creating-a-share-to-teams-embedded-button"></a>Criando um botão compartilhar com o Teams

>[!NOTE]
> * Só há suporte para as versões de área de trabalho do Edge e do Chrome.
> * Não há suporte para o uso de contas de convidado ou freemium.

Sites de terceiros podem usar o script iniciador para inserir o compartilhamento para os botões do teams em suas páginas da Web, que iniciarão o compartilhamento com a experiência do teams em uma janela pop-up quando clicado. Isso permitirá que você compartilhe um link diretamente para qualquer pessoa ou canal do Microsoft Teams sem alterar o contexto.

![Pop-up compartilhar com o Teams](~/assets/images/share-to-teams-popup.png)

## <a name="how-to-embed-a-share-to-teams-button"></a>Como inserir um compartilhamento no botão Teams

Primeiro, você precisará adicionar o `launcher.js` script na sua página da Web.

```html
<script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
```

Em seguida, adicione um elemento HTML na sua página da Web `teams-share-button` com o atributo Class e o link para compartilhar `data-href` no atributo.

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>">
</div>
```

Isso adicionará o ícone do Microsoft Teams ao seu site.

![Ícone compartilhar com o Teams](~/assets/icons/share-to-teams-icon.png)

Opcionalmente, se você quiser um tamanho de ícone diferente para o botão compartilhar com Teams, `data-icon-px-size` use o atributo.

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-icon-px-size="64">
</div>
```

Se você souber que a URL de visualização do link a ser compartilhado não renderizará bem no Teams (por exemplo, o link exigirá autenticação do usuário), você poderá desabilitar a `data-preview` visualização da URL `false`adicionando o atributo definido para.

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-preview="false">
</div>
```

Se sua página renderiza dinamicamente o conteúdo, você pode usar o `shareToMicrosoftTeams.renderButtons()` método para forçar o botão **compartilhar** para renderizar no local apropriado no pipeline.

## <a name="crafting-your-website-preview"></a>Como criar sua versão prévia do site

Quando o seu site é compartilhado para o Microsoft Teams, o cartão que é inserido no canal selecionado conterá uma visualização do seu site. Você pode controlar o comportamento dessa visualização garantindo que os metadados apropriados sejam adicionados ao site que está sendo compartilhado (a `data-href` URL). A tabela abaixo descreve as marcas necessárias. Você pode usar as versões padrão HTML ou a versão aberta do Graph.

Para que a visualização seja exibida, você deve:

* Inclua uma imagem em miniatura ou um título e uma descrição (para obter os melhores resultados, inclua todos os três).
* A URL que está sendo compartilhada não pode exigir autenticação. Se você ainda pode compartilhá-lo, mas a visualização não será criada.

|Valor|Marca Meta| Abrir gráfico|
|----|----|----|
|Cargo|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Descrição|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Imagem em miniatura| nenhuma |`<meta property="og:image" content="http://example.com/image.jpg">`|

## <a name="share-to-teams-for-education"></a>Compartilhar com o Microsoft Teams para educação

Para professores usando o botão compartilhar para equipes, você receberá uma opção adicional para `Create an Assignment`. Isso permite que você crie rapidamente uma atribuição na equipe escolhida com base no link compartilhado.

![Pop-up compartilhar com o Teams](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a>Definição do iniciador. js completo

| Propriedade | Atributo HTML | Tipo | Padrão | Descrição |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | string | n/d | O href do conteúdo a ser compartilhado. |
| visualização | `data-preview` | booliano (como uma cadeia de caracteres) | `true` | Se mostrar ou não uma visualização do conteúdo a ser compartilhado. |
| iconPxSize | `data-icon-px-size` | número (como uma cadeia de caracteres) | `32` | O tamanho em pixels do botão Share-to-Teams a ser renderizado. |
| msgText | `data-msg-text` | string | n/d | Texto padrão a ser inserido antes do link na caixa de composição de mensagem (limite de caracteres de 200) |
| assignInstr | `data-assign-instr` | string | n/d | Texto padrão a ser inserido no campo atribuições "instruções" (limite de caracteres 200) |
| assignTitle | `data-assign-title` | string | n/d | Texto padrão a ser inserido no campo "título" das atribuições (limite de caracteres de 50) |

### <a name="methods"></a>Métodos

**`shareToMicrosoftTeams.renderButtons(options)`**

`options`(opcional):`{ elements?: HTMLElement[] }`

Processa todos os botões de compartilhamento atualmente na página. Se um objeto `options` opcional for fornecido com uma lista de elementos, esses elementos serão renderizados em botões de compartilhamento.

### <a name="setting-default-form-values"></a>Definindo valores de formulário padrão

Opcionalmente, você pode optar por definir valores padrão para os seguintes campos no formulário compartilhar com o Teams:

* Diga algo sobre isso (`msgText`)
* Instruções de atribuição`assignInstr`()
* Título da atribuição`assignTitle`()

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
