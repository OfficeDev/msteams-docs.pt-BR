---
title: Alterações na margem da guia
author: surbhigupta
description: Saiba como remover margens em torno de guias no Microsoft Teams com o kit de interface do usuário. Conheça o efeito de preenchimento extra, o tamanho da margem para esquerda, direita, superior e inferior.
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: 715c6b735323e442490de8634384054be565e7a8
ms.sourcegitcommit: 87bba925d005eb331d876a0b9b75154f8100e911
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2022
ms.locfileid: "67450440"
---
# <a name="tab-margin-changes"></a>Alterações na margem da guia

Este documento descreve como a remoção de margens em torno de todas as guias no Microsoft Teams aprimora sua experiência de criação de aplicativos. Esse é um aprimoramento introduzido no Teams em 2021.
Você pode criar aplicativos que parecem mais nativos do Teams removendo as margens em todas as guias. As guias com margens removidas se alinham com os [designs do kit de](~/tabs/design/tabs.md) interface do usuário do Microsoft Teams. A maioria dos aplicativos tem uma aparência aprimorada sem margens.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Inteligência de tabulação e sem margens":::

> [!NOTE]
> Esse recurso não é aplicável a clientes móveis, pois as guias exibidas nos clientes móveis não têm margens.

## <a name="guidelines"></a>Diretrizes

A remoção de margens de tabulação afeta os aplicativos do Teams que usam guias. Nesses casos, você pode adicionar margens ao redor de seus designs de guia onde for necessário. Designs de aplicativo em produção têm um efeito de preenchimento extra, ou seja, margens fornecidas pelo Teams e margens fornecidas pela guia. No entanto, o preenchimento extra é apenas temporário e desaparecerá em algumas semanas, deixando apenas o preenchimento fornecido pelo aplicativo.

## <a name="faq"></a>Perguntas frequentes

**É possível que o cromado do aplicativo, como a barra de cabeçalho ou a barra de tarefas, toque nas bordas de nossos designs?**

Sim, isso é bom e o Teams incentiva esse design. Ele ajuda o aplicativo a se sentir nativo.

**É possível que o conteúdo do aplicativo, como texto, logotipos e imagens, toque nas bordas esquerda e direita de nossos designs?**

Não, você deve fornecer seu próprio preenchimento ou margens à esquerda e à direita de todo o conteúdo do aplicativo para garantir que ele não toque nas bordas da interface do usuário. Você também pode adicionar margens na parte superior da guia, se necessário.

**Qual é o tamanho das margens de tabulação que o Teams aplicou anteriormente?**

* Esquerda e direita: 20 pixels
* Superior: 16 pixels
* Inferior: 0 pixels

> [!IMPORTANT]
>
> * Todas as guias têm suas margens removidas: guias pessoais, guias de chat (grupo), guias de reunião e guias de canal.
> * A alteração de remoção da margem de tabulação se aplica a todas as guias. Não há como aceitar ou recusar a alteração.
> * A alteração das margens de tabulação pode afetar as guias que dependem do Microsoft Teams para fornecer margens ao redor da interface do usuário.

## <a name="see-also"></a>Confira também

* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
