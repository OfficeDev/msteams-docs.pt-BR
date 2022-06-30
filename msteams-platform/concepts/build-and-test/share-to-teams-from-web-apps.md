---
title: Compartilhar no Teams a partir de aplicativos Web
description: Saiba como adicionar o botão Compartilhar no Teams incorporado em seu site, com uma visualização de site, usando Exemplos de código
ms.topic: reference
ms.localizationpriority: medium
ms.openlocfilehash: b555d0e111a16be2e5be45e07998aeb94e432901
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558475"
---
# <a name="share-to-teams-from-web-apps"></a>Compartilhar no Teams a partir de aplicativos Web

Sites de terceiros podem usar o script do inicializador para inserir botões Compartilhar no Teams em suas páginas da Web. Quando você seleciona o botão Compartilhar com o Teams, ele inicia a experiência Compartilhar com o Teams em uma janela pop-up. Isso permite que você compartilhe um link diretamente com qualquer pessoa ou canal do Microsoft Teams sem alternar o contexto.

A imagem a seguir exibe a janela pop-up da experiência de visualização Compartilhar com o Teams:

:::image type="content" source="~/assets/images/share-to-teams-popup.png" alt-text="Pop-up Compartilhar com o Teams":::

> [!NOTE]
>
> * Há suporte apenas para as versões para desktop do Microsoft&nbsp;Edge e Google Chrome.
> * Não há suporte para o uso de contas de convidado ou Freemium.

Você também pode adicionar links desfraldados para os links compartilhados por meio do botão Compartilhar com o Teams hospedado no aplicativo Web, aplicativo pessoal ou guia. Para obter mais informações, consulte [o link desfraldamento](~/messaging-extensions/how-to/link-unfurling.md).

A imagem a seguir exibe a experiência de desfralização de link por meio do botão Compartilhar com o Teams:

:::image type="content" source="~/assets/images/share-to-teams-link-unfurling.png" alt-text="Link compartilhar para o Teams desfraldando":::

> [!NOTE]
> No momento, o link desfralização em compartilhamento para o Teams só está disponível na versão prévia do desenvolvedor público.

Este artigo orienta você sobre como criar e inserir um botão Compartilhar no Teams para seu site, criar a visualização do site e estender o Compartilhamento para Teams para Educação.

Confira o vídeo a seguir para saber como inserir o botão Compartilhar no Teams:
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4vhWH]
<br>


## <a name="embed-a-share-to-teams-button"></a>Incorpore um botão Compartilhar no Teams

1. Adicione o script `launcher.js` em sua página da Web.

    ```html
    <script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
    ```

1. Adicione um elemento HTML em sua página da Web com o atributo de classe `teams-share-button` e o link para compartilhar no atributo `data-href`.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>">
    </div>
    ```

    Depois de concluir isso, o ícone do Teams é adicionado ao seu site. A imagem a seguir mostra o ícone Compartilhar no Teams:

    :::image type="content" source="~/assets/icons/share-to-teams-icon.png" alt-text="Ícone Compartilhar no Teams":::

1. Como alternativa, se você quiser um tamanho de ícone diferente para o botão Compartilhar com o Teams, use o `data-icon-px-size` atributo.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-icon-px-size="64">
    </div>
    ```

1. Se o link compartilhado exigir autenticação de usuário e a visualização da URL do link a ser compartilhada não renderizar bem no Teams, você poderá desabilitar a visualização da URL `data-preview` adicionando o atributo definido como `false`.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-preview="false">
    </div>
    ```

1. Para exibir uma mensagem de sua escolha na caixa de redação, você pode definir o texto no `data-msg-text` atributo.

     ```html
     <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-msg-text="<default-message-to-be-populated-in-compose-box>"
      data-preview="false">
      </div>
     ```

1. Se sua página renderizar dinamicamente o conteúdo, você poderá usar o método `shareToMicrosoftTeams.renderButtons()` para forçar a opção **Compartilhar** a renderizar no local apropriado do pipeline.

## <a name="craft-your-website-preview"></a>Crie a visualização do seu site

Quando seu site é compartilhado no Teams, o cartão inserido no canal selecionado contém uma visualização do seu site. Você pode controlar o comportamento dessa visualização garantindo que os metadados apropriados sejam adicionados ao site que está sendo compartilhado, como a URL `data-href`.  

Para mostrar a visualização:

* Você deve incluir uma **Imagem em miniatura** ou um **Título** e uma **Descrição**. Para ter melhores resultados, inclua todos os três.
* A URL compartilhada não requer autenticação. Se ela exigir autenticação, você poderá compartilhá-la, mas a visualização não será criada.

A tabela a seguir descreve as marcas necessárias:

|Valor|Marca Meta| Open Graph|
|----|----|----|
|Cargo|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Descrição|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Imagem em Miniatura| nenhuma. |`<meta property="og:image" content="http://example.com/image.jpg">`|

Você pode usar as versões padrão HTML ou a versão Open Graph.

## <a name="share-to-teams-for-education"></a>Compartilhar no Teams para Educação

Para professores que usam o botão Compartilhar com o Teams, `Create an Assignment` há uma opção adicional que permite que você crie rapidamente uma tarefa na Equipe escolhida, com base no link compartilhado. A imagem a seguir exibe a opção Compartilhar no Teams para Educação:

:::image type="content" source="../../assets/images/share-to-teams-popup-edu.png" alt-text="Pop-up Compartilhar no Teams para Edução":::

## <a name="full-launcherjs-definition"></a>Definição completa do launcher.js

| Propriedade | Atributo HTML | Tipo | Padrão | Descrição |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | string | n/d | A href do conteúdo a ser compartilhado. |
| visualização | `data-preview` | Booliano (como uma cadeia de caracteres) | `true` | Se deseja ou não mostrar uma visualização do conteúdo a ser compartilhado. |
| iconPxSize | `data-icon-px-size` | número (como uma cadeia de caracteres) | `32` | O tamanho em pixels do botão Compartilhar no Teams a ser renderizado. |
| msgText | `data-msg-text` | cadeia de caracteres | n/d | Texto padrão a ser inserido antes do link na caixa de composição da mensagem. O número máximo de caracteres é 200. |
| assignInstr | `data-assign-instr` | string | n/d | Texto padrão a ser inserido no campo "Instruções" das tarefas. O número máximo de caracteres é 200. |
| assignTitle | `data-assign-title` | string | n/d | Texto padrão a ser inserido no campo "Título" das tarefas. O número máximo de caracteres é 50. |

### <a name="methods"></a>Methods

**`shareToMicrosoftTeams.renderButtons(options)`**

`options` (opcional): `{ elements?: HTMLElement[] }`

Atualmente, todos os botões de compartilhamento são renderizados na página. Se um objeto opcional `options` for fornecido com uma lista de elementos, esses elementos serão renderizados em botões de compartilhamento.

### <a name="set-default-form-values"></a>Definir valores de formulário padrão

Você pode optar por definir valores padrão para os seguintes campos no formulário Compartilhar no Teams:

* Diga algo sobre isso: `msgText`
* Instruções da Tarefa: `assignInstr`
* Título da Tarefa: `assignTitle`

#### <a name="example"></a>Exemplo

 Os valores de formulário padrão são fornecidos no exemplo a seguir:

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```

## <a name="see-also"></a>Confira também

* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
* [Compartilhar com o Teams a partir do aplicativo ou guia pessoal](share-to-teams-from-personal-app-or-tab.md)
