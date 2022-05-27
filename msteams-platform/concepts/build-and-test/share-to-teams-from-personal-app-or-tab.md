---
title: Compartilhar com o Teams a partir do aplicativo ou guia pessoal
description: Saiba como adicionar o Compartilhamento no Teams inserido em seu aplicativo pessoal ou guia
ms.topic: reference
ms.localizationpriority: medium
keywords: Compartilhar a opção Compartilhar no Teams no Teams
ms.openlocfilehash: c40263504b77a8a848251431de1eb49b85253b77
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757259"
---
# <a name="share-to-teams-from-personal-app-or-tab"></a>Compartilhar com o Teams a partir do aplicativo ou guia pessoal

> [!NOTE]
> O compartilhamento Teams está disponível atualmente apenas na versão prévia [do desenvolvedor público](../../resources/dev-preview/developer-preview-intro.md).

Compartilhar com Teams permite que os usuários compartilhem o conteúdo de aplicativo pessoal ou guia para outro usuário ou grupo ou canal dentro Teams. Os usuários podem selecionar Compartilhar Teams para iniciar o Compartilhamento Teams experiência em uma janela pop-up. A janela pop-up permite que os usuários adicionem outro usuário, grupo ou canal para compartilhar o conteúdo.

A imagem a seguir mostra a janela pop-up Compartilhar Teams janela pop-up:

:::image type="content" source="../../assets/images/share-to-teams/share-to-teams.PNG" alt-text="share-to-teams-pop-up":::

## <a name="enable-share-to-teams-button"></a>Habilitar Compartilhamento Teams botão

> [!NOTE]
> Verifique se você tem um [SD Microsoft Teams K do Cliente JavaScript ou um SDK](../../tabs/how-to/using-teams-client-sdk.md) do Cliente [JavaScript v2 versão](../../tabs/how-to/using-teams-client-sdk.md)`@microsoft/teams-js@1.11.0-beta.7` prévia (ou posterior) para habilitar o Compartilhamento Teams para seu aplicativo ou guia pessoal. Microsoft Teams

Para habilitar o Compartilhamento Teams:

1. Crie um aplicativo ou guia pessoal com **Teams SDK do Cliente Javascript**.

2. Criar um **botão Compartilhar Teams** aplicativo.

3. No botão Compartilhar Teams, chame com `microsoftTeams.sharing.shareWebContent` uma carga de conteúdo.

O exemplo a seguir explica como criar uma carga de conteúdo:

```json
microsoftTeams.sharing.shareWebContent({
        content: [
          {
            type: 'URL',
            url: '<URL to be shared>',
            message: 'Default message to be loaded in the compose box',
            preview: true
          }
        ]
      });
```

A carga contém os seguintes parâmetros:

| Nome da propriedade | Objetivo |
|---|---|
| `type` | O tipo deve ser `URL` |
| `url` | `URL` a ser compartilhado |
|`message`| Mensagem padrão a ser carregada na caixa de composição |
| `preview` | Definido para habilitar `true` a visualização de URL |

A imagem a seguir mostra a opção Teams compartilhar:

:::image type="content" source="../../assets/images/share-to-teams/share-button.PNG" alt-text="botão compartilhar para equipes":::

## <a name="response-codes"></a>Códigos de resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **100** | A API não tem suporte na plataforma atual. |
| **404** | O arquivo especificado não foi encontrado no local especificado. |
| **500** | Erro interno encontrado ao executar a operação necessária. |
| **501** | A API não tem suporte no contexto atual. |
| **1.000** | Permissões negadas pelo usuário. |
| **2000** | Problema de rede. |
| **3000** | O hardware subjacente não dá suporte à funcionalidade. |
| **4000** | Um ou mais argumentos são inválidos. |
| **5000** | O usuário não está autorizado para esta operação. |
| **6000** | Não foi possível concluir a operação devido a recursos insuficientes. |
| **7000** | A plataforma limitou a solicitação porque a API foi invocada com muita frequência. |
| **8000** | O usuário anula a operação. |
| **9000** | O código da plataforma é antigo e não implementa essa API. |
| **10000** | O valor retornado é muito grande e excedeu nossos limites de tamanho. |

## <a name="limitations"></a>Limitações

As limitações para adicionar o Compartilhamento Teams botão:

* O botão Compartilhar Teams pode ser hospedado ou inserido em um aplicativo em execução dentro Teams.
* Você pode adicionar o botão Compartilhar Teams ao aplicativo criado usando Teams **SDK do Cliente Javascript**.

## <a name="end-user-share-to-teams-experience"></a>Compartilhamento de usuário final para Teams experiência

Depois de habilitar o botão Compartilhar com o Teams no aplicativo pessoal ou na guia, você pode compartilhar o conteúdo. Para acessar, siga as etapas:

1. Abra um aplicativo ou guia pessoal e selecione **Compartilhar para Teams**.

    :::image type="content" source="../../assets/images/share-to-teams/share-button.PNG" alt-text="botão compartilhar para equipes":::

2. Adicione outro usuário, grupo ou canal para compartilhar o conteúdo.

    :::image type="content" source="../../assets/images/share-to-teams/add-recepient.PNG" alt-text="add-recipient":::

    > [!NOTE]
    > Você pode adicionar uma anotação **em dizer algo sobre isso**.

3. Selecione **Compartilhar**.

   :::image type="content" source="../../assets/images/share-to-teams/add-notes.PNG" alt-text="add-note":::

4. Selecione **Exibir** para acessar a conversa em que o link foi compartilhado.

   :::image type="content" source="../../assets/images/share-to-teams/link-shared.PNG" alt-text="share-to-teams-link-shared":::

## <a name="see-also"></a>Confira também

* [Compartilhar no Teams a partir de aplicativos Web](share-to-teams-from-web-apps.md)
* [Criar uma guia pessoal](../../tabs/how-to/create-personal-tab.md)
