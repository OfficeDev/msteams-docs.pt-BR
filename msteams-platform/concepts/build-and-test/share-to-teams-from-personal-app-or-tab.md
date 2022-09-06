---
title: Compartilhar com o Teams a partir do aplicativo ou guia pessoal
description: Saiba como habilitar o botão Compartilhar com o Teams em seu aplicativo pessoal ou guia, limitações e experiência do usuário final.
ms.topic: reference
ms.localizationpriority: medium
ms.openlocfilehash: cd4de40fdb557300ad957df03f463a0879f44b0e
ms.sourcegitcommit: d92e14fad6567fe91fd52ee6c213836740316683
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2022
ms.locfileid: "67605058"
---
# <a name="share-to-teams-from-personal-app-or-tab"></a>Compartilhar com o Teams a partir do aplicativo ou guia pessoal

Compartilhar com o Teams permite que os usuários compartilhem o conteúdo do aplicativo pessoal ou da guia para outro usuário ou grupo ou canal no Teams. Os usuários podem selecionar Compartilhar com o Teams para iniciar a experiência Compartilhar com o Teams em uma janela pop-up. A janela pop-up permite que os usuários adicionem outro usuário, grupo ou canal para compartilhar o conteúdo.

A imagem a seguir mostra a janela pop-up Compartilhar com o Teams:

:::image type="content" source="../../assets/images/share-to-teams/share-to-teams.PNG" alt-text="share-to-teams-pop-up":::

## <a name="enable-share-to-teams-button"></a>Botão Habilitar Compartilhar no Teams

> [!NOTE]
> Verifique se você tem o [SDK do Cliente JavaScript do Microsoft Teams ou o SDK](../../tabs/how-to/using-teams-client-sdk.md) do Cliente [JavaScript do Microsoft Teams v2 Preview](../../tabs/how-to/using-teams-client-sdk.md) (`@microsoft/teams-js@1.11.0-beta.7` ou posterior) para habilitar o Compartilhamento com o Teams para seu aplicativo ou guia pessoal.

Para habilitar o Compartilhamento com o Teams:

1. Crie um aplicativo pessoal ou uma guia com o **SDK do Cliente Javascript do Teams**.

2. Botão **Criar um Compartilhamento com o Teams** .

3. No botão Compartilhar com o Teams, chame `microsoftTeams.sharing.shareWebContent` com uma carga de conteúdo.

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

A imagem a seguir mostra a opção Compartilhar com o Teams:

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

As limitações para adicionar o botão Compartilhar ao Teams:

* O botão Compartilhar com o Teams pode ser hospedado ou inserido em um aplicativo em execução no Teams.
* Você pode adicionar o botão Compartilhar ao Teams ao aplicativo criado usando o **SDK do Cliente Javascript do Teams**.

## <a name="end-user-share-to-teams-experience"></a>Experiência de compartilhamento do usuário final com o Teams

Depois de habilitar o botão Compartilhar com o Teams no aplicativo pessoal ou na guia, você pode compartilhar o conteúdo. Para acessar, siga as etapas:

1. Abra um aplicativo ou guia pessoal e selecione **Compartilhar com o Teams**.

    :::image type="content" source="../../assets/images/share-to-teams/share-button.PNG" alt-text="botão compartilhar para equipes":::

2. Adicione outro usuário, grupo ou canal para compartilhar o conteúdo.

    :::image type="content" source="../../assets/images/share-to-teams/add-recepient.PNG" alt-text="add-recipient":::

3. Selecione **Compartilhar**.

   :::image type="content" source="../../assets/images/share-to-teams/add-notes.PNG" alt-text="add-note":::

4. Selecione **Exibir** para acessar a conversa em que o link foi compartilhado.

   :::image type="content" source="../../assets/images/share-to-teams/link-shared.PNG" alt-text="share-to-teams-link-shared":::

## <a name="see-also"></a>Confira também

* [Compartilhar no Teams a partir de aplicativos Web](share-to-teams-from-web-apps.md)
* [Criar uma guia pessoal](../../tabs/how-to/create-personal-tab.md)
