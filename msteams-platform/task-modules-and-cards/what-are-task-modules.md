---
title: Módulos de tarefas
author: surbhigupta
description: Adicionar experiências pop-up modais para coletar ou exibir informações aos usuários de seus Microsoft Teams aplicativos
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 3b0e639acc8901a3637189e435fcfc159e992ae3a674a437733474087103193c
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57707679"
---
# <a name="task-modules"></a>Módulos de tarefas

Os módulos de tarefas permitem que você crie experiências pop-up modais em seu Teams aplicativo. No pop-up, você pode:

* Execute seu próprio código HTML ou JavaScript personalizado.
* Mostrar um `<iframe>` widget baseado, como um vídeo do YouTube ou do Microsoft Stream.
* Exibir um [Cartão Adaptável](/adaptive-cards/).

Os módulos de tarefas são úteis para iniciar e concluir tarefas ou exibir informações ricas, como vídeos ou painéis do Power Business Intelligence (BI). Uma experiência pop-up geralmente é mais natural para usuários iniciando e concluindo tarefas em comparação com uma guia ou uma experiência de bot baseada em conversa.

Os módulos de tarefa são construídos com base Microsoft Teams guias. Eles são essencialmente uma guia dentro de uma janela pop-up. Eles usam o mesmo SDK, portanto, se você tiver criado uma guia, você já está familiarizado com a criação de um módulo de tarefa.

Módulos de tarefa podem ser invocados de três maneiras:

* Canal ou guias pessoais: usando o SDK de guias Microsoft Teams, você pode invocar módulos de tarefas de botões, links ou menus em sua guia. Para obter mais informações, [consulte using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md).
* Bots: usando botões em [cartões](~/task-modules-and-cards/cards/cards-reference.md) enviados do bot. Isso é útil quando você não exige que todos em um canal vejam o que você está fazendo com um bot. Por exemplo, ao fazer com que os usuários respondam a uma sondagem em um canal, não é útil ver um registro dessa sondagem sendo criada. Para obter mais informações, consulte [using task modules from Teams bots](~/task-modules-and-cards/task-modules/task-modules-bots.md).
* Fora do Teams de um link profundo: você também pode criar URLs para invocar um módulo de tarefa de qualquer lugar. Para obter mais informações, consulte [sintaxe de link profundo do módulo de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax).

## <a name="components-of-a-task-module"></a>Componentes de um módulo de tarefa

Veja a aparência de um módulo de tarefa quando invocado de um bot:

![Exemplo de módulo de tarefa](~/assets/images/task-module/task-module-example.png)

Um módulo de tarefa inclui o seguinte, conforme mostrado na imagem anterior:

1. O ícone do seu [ `color` aplicativo](~/resources/schema/manifest-schema.md#icons).
2. O nome do seu [ `short` aplicativo](~/resources/schema/manifest-schema.md#name).
3. O título do módulo de tarefa especificado na `title` propriedade do [objeto TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object).
4. O botão fechar ou cancelar do módulo de tarefas. Se o usuário selecionar esse botão, seu aplicativo receberá um `err` evento. Para obter mais informações, [consulte exemplo para enviar o resultado de um módulo de tarefa](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module).

    > [!NOTE]
    > No momento, não é possível detectar o evento quando um módulo de `err` tarefa é invocado de um bot.

5. O retângulo azul é onde sua página da Web será exibida se você estiver carregando sua própria página da Web usando a propriedade `url` [do objeto TaskInfo.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) Para obter mais informações, consulte [task module sizing](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-sizing).
6. Se você estiver exibindo um Cartão Adaptável usando a propriedade do `card` [objeto TaskInfo,](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) o preenchimento será adicionado para você. Para obter mais informações, consulte módulo de tarefa CSS para módulos de tarefa HTML ou [JavaScript.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-css-for-html-or-javascript-task-modules)
7. Botões de cartão adaptáveis são renderizar depois de selecionar **Inscrever-se**. Ao usar sua própria página, crie seus próprios botões.

## <a name="see-also"></a>Confira também

[Cartões](~/task-modules-and-cards/what-are-cards.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Invocar e ignorar módulos de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md)
