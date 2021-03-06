---
title: Criar um botão Compartilhar para o Teams
description: Como adicionar o botão Compartilhar ao Teams incorporado em seu site
ms.topic: reference
localization_priority: Normal
keywords: Compartilhar Teams share-to-Teams
ms.openlocfilehash: d3e23c50cbaa38a53fa02c19cec69061478d9a57
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075644"
---
# <a name="create-share-to-teams-button"></a>Criar um botão Compartilhar para o Teams

Sites de terceiros podem usar o script do launcher para inserir botões de Compartilhamento para Teams em suas páginas da Web. Quando você seleciona, ele inicia a experiência Share-to-Teams em uma janela pop-up. Isso permite compartilhar um link diretamente com qualquer pessoa ou canal Microsoft Teams sem alternar o contexto. Este documento orienta você sobre como criar e inserir um botão Compartilhar para Teams para seu site, criar a visualização do site e estender o Share-to-Teams para Educação.

> [!NOTE]
> * Somente as versões da área de trabalho do Edge e do Chrome têm suporte.
> * Não há suporte para o uso de contas de convidado ou de Freemium.  

A imagem a seguir exibe a experiência pop-up Share-to-Teams:

![Share-to-Teams pop-up](~/assets/images/share-to-teams-popup.png)

## <a name="embed-a-share-to-teams-button"></a>Inserir um botão Compartilhar Teams

1. Adicione o `launcher.js` script em sua página da Web.

    ```html
    <script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
    ```

1. Adicione um elemento HTML em sua página da Web com o atributo de classe e `teams-share-button` o link para compartilhar no `data-href` atributo.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>">
    </div>
    ```

    Depois de concluir isso, o Microsoft Teams ícone é adicionado ao seu site. A imagem a seguir mostra o ícone Compartilhar para Teams:

    ![Compartilhar para Teams ícone](~/assets/icons/share-to-teams-icon.png)

1. Como alternativa, se você quiser um tamanho de ícone diferente para o botão Compartilhar Teams, use o `data-icon-px-size` atributo.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-icon-px-size="64">
    </div>
    ```
1. Se o link compartilhado exigir autenticação do usuário e a visualização de URL do link a ser compartilhado não renderizar bem no Teams, você poderá desabilitar a visualização da URL adicionando o atributo `data-preview` definido como `false` .

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-preview="false">
    </div>
    ```

1. Se sua página renderizar dinamicamente o conteúdo, você poderá usar o método para forçar o botão Compartilhar a renderizar no `shareToMicrosoftTeams.renderButtons()` local apropriado no pipeline. 

## <a name="craft-your-website-preview"></a>Criar a visualização do site

Quando seu site é compartilhado Teams, o cartão inserido no canal selecionado contém uma visualização do seu site. Você pode controlar o comportamento dessa visualização garantindo que os metadados apropriados são adicionados ao site que está sendo compartilhado, como a `data-href` URL.  

**Para exibir a visualização**

* Você deve incluir uma imagem **thumbnail** ou um **título** e uma **descrição.** Para melhores resultados, inclua todos os três.
* A URL compartilhada não exige autenticação. Se ela exigir autenticação, você poderá compartilhá-la, mas a visualização não será criada.

A tabela a seguir descreve as marcas necessárias:

|Valor|Marca Meta| Abra Graph|
|----|----|----|
|Título|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Descrição|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Imagem de miniatura| none. |`<meta property="og:image" content="http://example.com/image.jpg">`|

Você pode usar as versões padrão html ou a versão Graph Open.

## <a name="share-to-teams-for-education"></a>Compartilhar com Teams educação

Para professores que usam o botão Compartilhar Teams, há uma opção adicional para `Create an Assignment` . Isso permite que você crie rapidamente uma atribuição na Equipe escolhida, com base no link compartilhado. A imagem a seguir exibe Share-to-Teams para educação: 

![Compartilhar para Teams educação pop-up](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a>Definição launcher.js completa

| Propriedade | Atributo HTML | Tipo | Padrão | Descrição |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | cadeia de caracteres | n/d | O href do conteúdo a ser compartilhá-lo. |
| visualização | `data-preview` | booleano (como uma cadeia de caracteres) | `true` | Se deve ou não mostrar uma visualização do conteúdo a ser compartilhá-lo. |
| iconPxSize | `data-icon-px-size` | number (como uma cadeia de caracteres) | `32` | O tamanho em pixels do botão Compartilhar para Teams renderizar. |
| msgText | `data-msg-text` | cadeia de caracteres | n/d | Texto padrão a ser inserido antes do link na caixa de redação da mensagem. O número máximo de caracteres é 200. |
| assignInstr | `data-assign-instr` | cadeia de caracteres | n/d | Texto padrão a ser inserido no campo "Instruções" de atribuições. O número máximo de caracteres é 200. |
| assignTitle | `data-assign-title` | cadeia de caracteres | n/d | Texto padrão a ser inserido no campo "Título" de atribuições. O número máximo de caracteres é 50. |

### <a name="methods"></a>Métodos

**`shareToMicrosoftTeams.renderButtons(options)`**

`options` (opcional): `{ elements?: HTMLElement[] }`

Atualmente, todos os botões de compartilhamento são renderizados na página. Se um objeto `options` opcional for fornecido com uma lista de elementos, esses elementos serão renderizados em botões de compartilhamento.

### <a name="set-default-form-values"></a>Definir valores de formulário padrão

Você pode selecionar para definir valores padrão para os seguintes campos no formulário Compartilhar Teams:

* Diga algo sobre isso: `msgText`
* Instruções de atribuição: `assignInstr`
* Título da atribuição: `assignTitle`

#### <a name="example"></a>Exemplo

 Os valores de formulário padrão são dados no exemplo a seguir:

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

[Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
