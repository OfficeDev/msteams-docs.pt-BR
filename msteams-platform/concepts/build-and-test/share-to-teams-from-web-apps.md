---
title: Compartilhar com Teams de aplicativos Web
description: Saiba como adicionar o botão Compartilhar ao Teams inserido em seu site, com uma visualização de site, usando exemplos de código
ms.topic: reference
ms.localizationpriority: medium
keywords: Compartilhar Teams compartilhar com Teams
ms.openlocfilehash: ac08d3c697bc5f02eb8527d2239afe022cb421af
ms.sourcegitcommit: f892125106adb6731a20127f15d6e92f279127c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64685654"
---
# <a name="share-to-teams-from-web-apps"></a>Compartilhar com Teams de aplicativos Web

Sites de terceiros podem usar o script do inicializador para inserir o Compartilhamento Teams botões em suas páginas da Web. Quando você seleciona, ele inicia o Compartilhamento para Teams experiência em uma janela pop-up. Isso permite que você compartilhe um link diretamente com qualquer pessoa ou Microsoft Teams canal sem alternar o contexto. Este documento orienta você sobre como criar e inserir um botão Compartilhar para Teams para seu site, criar sua visualização de site e estender o Compartilhamento para Teams para Educação.

> [!NOTE]
>
> * Há suporte apenas para as versões de área de trabalho do MicrosoftEdge&nbsp; e do Google Chrome.
> * Não há suporte para o uso de contas de convidado ou Freemium.  

A imagem a seguir exibe a experiência pop-up Compartilhar para Teams pop-up:

:::image type="content" source="../../assets/images/share-to-teams-popup.png" alt-text="Compartilhar com Teams pop-up":::

## <a name="embed-a-share-to-teams-button"></a>Inserir um botão Compartilhar Teams

1. Adicione o `launcher.js` script à sua página da Web.

    ```html
    <script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
    ```

1. Adicione um elemento HTML em sua página da Web com o atributo `teams-share-button` de classe e o link para compartilhar no `data-href` atributo.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>">
    </div>
    ```

    Depois de concluir isso, o Microsoft Teams ícone é adicionado ao seu site. A imagem a seguir mostra o ícone Compartilhar para Teams:

    ![Compartilhar com o Teams ícone](~/assets/icons/share-to-teams-icon.png)

1. Como alternativa, se você quiser um tamanho de ícone diferente para o botão Compartilhar Teams, use o `data-icon-px-size` atributo.

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

1. Se sua página renderizar dinamicamente o conteúdo, você poderá usar `shareToMicrosoftTeams.renderButtons()` o método  para forçar o Compartilhamento a renderizar no local apropriado no pipeline.

## <a name="craft-your-website-preview"></a>Criar a visualização do seu site

Quando seu site é compartilhado com Teams, o cartão inserido no canal selecionado contém uma visualização do seu site. Você pode controlar o comportamento dessa visualização garantindo que os metadados apropriados sejam adicionados ao site que está sendo compartilhado, como a `data-href` URL.  

Para exibir a visualização:

* Você deve incluir uma imagem **em miniatura ou** um **título** e uma **descrição**. Para obter melhores resultados, inclua todos os três.
* A URL compartilhada não requer autenticação. Se ela exigir autenticação, você poderá compartilhá-la, mas a visualização não será criada.

A tabela a seguir descreve as marcas necessárias:

|Valor|Marca Meta| Abrir Graph|
|----|----|----|
|Cargo|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Descrição|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Imagem em miniatura| Nenhum. |`<meta property="og:image" content="http://example.com/image.jpg">`|

Você pode usar as versões padrão html ou a versão Graph open.

## <a name="share-to-teams-for-education"></a>Compartilhar com Teams para Educação

Para professores que usam o botão Compartilhar Teams, há uma opção adicional para `Create an Assignment`. Isso permite que você crie rapidamente uma atribuição na Equipe escolhida, com base no link compartilhado. A imagem a seguir exibe Compartilhar com Teams para educação:

:::image type="content" source="../../assets/images/share-to-teams-popup-edu.png" alt-text="Compartilhar com Teams educação pop-up":::

## <a name="full-launcherjs-definition"></a>Definição launcher.js completa

| Propriedade | Atributo HTML | Tipo | Padrão | Descrição |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | string | n/d | O href do conteúdo a ser compartilhado. |
| visualização | `data-preview` | Booliano (como uma cadeia de caracteres) | `true` | Se deseja ou não mostrar uma visualização do conteúdo a ser compartilhado. |
| iconPxSize | `data-icon-px-size` | número (como uma cadeia de caracteres) | `32` | O tamanho em pixels do botão Compartilhar Teams ser renderizado. |
| msgText | `data-msg-text` | string | n/d | Texto padrão a ser inserido antes do link na caixa de redação da mensagem. O número máximo de caracteres é 200. |
| assignInstr | `data-assign-instr` | string | n/d | Texto padrão a ser inserido no campo "Instruções" de atribuições. O número máximo de caracteres é 200. |
| assignTitle | `data-assign-title` | string | n/d | Texto padrão a ser inserido no campo "Título" das atribuições. O número máximo de caracteres é 50. |

### <a name="methods"></a>Métodos

**`shareToMicrosoftTeams.renderButtons(options)`**

`options` (opcional): `{ elements?: HTMLElement[] }`

Atualmente, todos os botões de compartilhamento são renderizados na página. Se um objeto `options` opcional for fornecido com uma lista de elementos, esses elementos serão renderizados em botões de compartilhamento.

### <a name="set-default-form-values"></a>Definir valores de formulário padrão

Você pode selecionar para definir valores padrão para os seguintes campos no formulário Compartilhar Teams:

* Diga algo sobre isso: `msgText`
* Instruções de atribuição: `assignInstr`
* Título da Atribuição: `assignTitle`

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
* [Compartilhar com Teams de aplicativo pessoal ou guia](share-to-teams-from-personal-app-or-tab.md)
