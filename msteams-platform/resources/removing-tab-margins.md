---
title: Alterações na margem da guia
author: surbhigupta
description: Descreve como a remoção de margens de tabulação aprimora a experiência de criação de aplicativos.
keywords: guia removendo preenchimento de margens
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: 4ca8356bddc0e578bc58b38112fb1268302a5ad0e84631bf81864c70cffbcb64
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57704379"
---
# <a name="tab-margin-changes"></a>Alterações na margem da guia

Este documento descreve como a remoção de margens ao redor de todas as guias no Microsoft Teams melhora sua experiência de criação de aplicativos. Este é um aprimoramento introduzido no Microsoft Teams em 2021.
Você pode criar aplicativos mais nativos para Teams removendo as margens ao redor de todas as guias. As guias com margens removidas se alinham Microsoft Teams designs de kit de [interface do usuário.](~/tabs/design/tabs.md) A maioria dos aplicativos tem uma aparência aprimorada sem margens.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Inteligência de tabulação e sem margens" border="false":::

> [!NOTE]
> Esse recurso não é aplicável a clientes móveis, pois as guias exibidas nos clientes móveis não têm margens. 

## <a name="guidelines"></a>Diretrizes

A remoção de margens de tabulação afeta Teams aplicativos que usam guias. Nesses casos, você pode adicionar margens ao redor de seus designs de tabulação onde é necessário. Designs de aplicativos em produção têm um efeito de preenchimento extra, ou seja, margens fornecidas por Teams e margens fornecidas pela guia. No entanto, o preenchimento extra é apenas temporário e vai embora em algumas semanas, deixando apenas o preenchimento fornecido pelo aplicativo.

## <a name="faq"></a>Perguntas frequentes

**Tudo bem para o aplicativo cromado, como barra de header ou barra de tarefas, tocar nas bordas de nossos designs?**

Sim, isso é bom e Teams incentiva esse design. Ele ajuda o aplicativo a se sentir nativo.

**Tudo bem para conteúdo do aplicativo, como texto, logotipos e imagens, tocar as bordas esquerda e direita de nossos designs?**

Não, você deve fornecer seu próprio preenchimento ou margens à esquerda e à direita de todo o conteúdo do aplicativo para garantir que ele não toque nas bordas da interface do usuário. Você também pode adicionar margens na parte superior da guia, se necessário.

**Qual é o tamanho das margens de tabulação que Teams aplicadas anteriormente?**

* Esquerda e direita: 20px
* Top: 16px
* Inferior: 0px

> [!IMPORTANT]
> * Todas as guias têm suas margens removidas: guias pessoais, guias de chat (grupo), guias de reunião e guias de canal.
> * A alteração da margem de tabulação se aplica a todas as guias. Não há como optar ou não pela alteração. 
> * A alteração das margens de tabulação pode afetar as guias que dependem Microsoft Teams fornecer margens ao redor da interface do usuário.

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
