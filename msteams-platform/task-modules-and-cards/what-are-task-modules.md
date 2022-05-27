---
title: Módulos de tarefas
author: surbhigupta
description: Adicionar experiências pop-up modais para coletar ou exibir informações aos usuários de seus aplicativos Microsoft Teams aplicativos
ms.localizationpriority: medium
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: a7d7778aa4d38dbc879255c449b93590d04f00e2
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756594"
---
# <a name="task-modules"></a>Módulos de tarefas

Os módulos de tarefas permitem que você crie experiências pop-up modais em seu aplicativo Teams. No pop-up, você pode:

* Execute seu próprio código HTML ou JavaScript personalizado.
* Mostrar um `<iframe>`widget baseado, como um vídeo do YouTube ou Microsoft Stream vídeo.
* Exibir um [Cartão Adaptável](/adaptive-cards/).

Os módulos de tarefa são úteis para iniciar e concluir tarefas ou exibir informações avançadas, como vídeos ou painéis do Power Business Intelligence (BI). Uma experiência pop-up geralmente é mais natural para usuários iniciando e concluindo tarefas em comparação com uma guia ou uma experiência de bot baseada em conversa.

Os módulos de tarefa se baseam na base Microsoft Teams guias. Eles são essencialmente uma guia dentro de uma janela pop-up. Eles usam o mesmo SDK, portanto, se você criou uma guia, já está familiarizado com a criação de um módulo de tarefa.

Módulos de tarefa podem ser invocados de três maneiras:

* Guias de canal ou pessoais: usando o SDK de guias Microsoft Teams, você pode invocar módulos de tarefa de botões, links ou menus na guia. Para obter mais informações, [consulte usando módulos de tarefa em guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md).
* Bots: usando botões em [cartões](~/task-modules-and-cards/cards/cards-reference.md) enviados do bot. Isso é útil quando você não precisa que todos em um canal vejam o que você está fazendo com um bot. Por exemplo, ao fazer com que os usuários respondam a uma votação em um canal, não é útil ver um registro dessa votação sendo criada. Para obter mais informações, [consulte usando módulos de tarefa Teams bots](~/task-modules-and-cards/task-modules/task-modules-bots.md).
* Fora do Teams de um link profundo: você também pode criar URLs para invocar um módulo de tarefa de qualquer lugar. Para obter mais informações, consulte [a sintaxe de vínculo profundo do módulo de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax).

## <a name="components-of-a-task-module"></a>Componentes de um módulo de tarefa

Veja como é a aparência de um módulo de tarefa quando invocado de um bot:

:::image type="content" source="../assets/images/task-module/task-module-example.png" alt-text="exemplo de módulo de tarefa":::

Um módulo de tarefa inclui o seguinte, conforme mostrado na imagem anterior:

1. Ícone [do aplicativo`color`.](~/resources/schema/manifest-schema.md#icons)
2. O nome do [aplicativo`short`](~/resources/schema/manifest-schema.md#name).
3. O título do módulo de tarefa especificado na propriedade `title` do [objeto TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object).
4. O botão fechar ou cancelar do módulo de tarefa. Se o usuário selecionar esse botão, seu aplicativo receberá um `err` evento. Para obter mais informações, [consulte o exemplo para enviar o resultado de um módulo de tarefa](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module).

    > [!NOTE]
    > No momento, não é possível detectar o evento `err` quando um módulo de tarefa é invocado de um bot.

5. O retângulo azul é onde sua página da Web é exibida se você estiver carregando sua própria página da Web `url` usando a propriedade do [objeto TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object). Para obter mais informações, consulte [dimensionamento do módulo de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-sizing).
6. Se você estiver exibindo um Cartão Adaptável `card` usando a propriedade do objeto [TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) , o preenchimento será adicionado para você. Para obter mais informações, consulte [o módulo de tarefa CSS para módulos de tarefa HTML ou JavaScript](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-css-for-html-or-javascript-task-modules).
7. Os botões cartão adaptável são renderizados depois que você **seleciona Inscrever-se**. Ao usar sua própria página, crie seus próprios botões.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Invocar e ignorar módulos de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md)

## <a name="see-also"></a>Confira também

[Cartões](~/task-modules-and-cards/what-are-cards.md)
