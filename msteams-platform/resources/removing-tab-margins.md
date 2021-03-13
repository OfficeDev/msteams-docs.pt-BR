---
title: Removendo margens de tabulação no Microsoft Teams
author: laujan
description: Descreve como a remoção das margens de tabulação melhorará a experiência do desenvolvedor.
keywords: guia removendo preenchimento de margens
ms.topic: reference
ms.author: lomeybur
ms.openlocfilehash: 57e6b15999ffc41c0a3e09897ba565f9b3bf3705
ms.sourcegitcommit: 23ed7edf145df10dcfba15c43978eae9e0d451a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2021
ms.locfileid: "50753515"
---
# <a name="tab-margin-changes"></a>Mudanças na margem da guia

Este documento descreve como a remoção de margens em torno de todas as guias no Microsoft Teams melhorará a experiência do desenvolvedor ao criar aplicativos. Este é um aprimoramento introduzido no Microsoft Teams em 2021.
Remover as margens ao redor de todas as guias permitirá que os desenvolvedores criem aplicativos que pareçam mais nativos para o Teams. Isso também se alinhará com nossos designs [de kit de interface do usuário.](~/tabs/design/tabs.md) A maioria dos aplicativos já fica melhor sem as margens ao redor de suas experiências. No entanto, algumas guias são afetadas visualmente por essa alteração, e os desenvolvedores devem fazer as alterações necessárias.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Inteligência de tabulação e sem margens" border="false":::

## <a name="timelines"></a>Linhas do tempo

* 5 de março de 2021 - Margens removidas na [Visualização do Desenvolvedor Público.](~/resources/dev-preview/developer-preview-intro.md)
* 1º de maio de 2021 - As margens serão removidas em produção.

## <a name="guidelines"></a>Diretrizes

Os aplicativos do Microsoft Teams que usam guias serão afetados por essa alteração. Os desenvolvedores devem alternar para [Visualização](~/resources/dev-preview/developer-preview-intro.md) de Desenvolvedor Público para determinar como suas guias são afetadas e fazer as alterações necessárias.

Os desenvolvedores de guias não devem confiar no Teams para fornecer margens ao redor de suas guias. Os desenvolvedores são incentivados a adicionar margens ao redor de seus designs de tabulação onde é necessário. Designs de aplicativos em produção podem parecer que há preenchimento extra, ou seja, margens fornecidas pelo Teams e margens fornecidas pela guia. No entanto, o preenchimento extra é apenas temporário e desaparecerá em algumas semanas, deixando apenas o preenchimento fornecido pelo aplicativo.

## <a name="faq"></a>Perguntas frequentes

**Tudo bem para o aplicativo cromado, como barra de header ou barra de tarefas, tocar nas bordas de nossos designs?**

Sim, isso é bom e incentivado. Isso ajuda o aplicativo a se sentir nativo.

**Tudo bem para conteúdo do aplicativo, como texto, logotipos e imagens, tocar as bordas esquerda e direita de nossos designs?**

Não, você deve fornecer seu próprio preenchimento ou margens à esquerda e à direita de todo o conteúdo do aplicativo para garantir que ele não toque nas bordas da interface do usuário. Você também pode adicionar margens na parte superior da guia, se necessário.

**Qual é o tamanho das margens que o Teams aplicou anteriormente?**

* Esquerda e direita: 20px
* Top: 16px
* Inferior: 0px

> [!IMPORTANT]
> * Todas as guias têm suas margens removidas: guias pessoais, guias de chat (grupo), guias de reunião e guias de canal.
> * Não há como optar ou não por essa alteração. Ela se aplicará a todas as guias.
> * Essa alteração pode afetar guias que dependem do Microsoft Teams para fornecer margens em torno de sua interface do usuário.