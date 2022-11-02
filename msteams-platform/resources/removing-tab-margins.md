---
title: Alterações na margem da guia
author: surbhigupta
description: Saiba como remover margens em torno de guias no Microsoft Teams com kit de interface do usuário. Saiba efeito de preenchimento extra, tamanho da margem para esquerda, direita, superior e inferior.
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: ba203cd89904acde77e1d9971175afc19c47d24d
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820070"
---
# <a name="tab-margin-changes"></a>Alterações na margem da guia

Este documento descreve como a remoção de margens em todas as guias no Microsoft Teams aprimora sua experiência de criação de aplicativos. Este é um aprimoramento introduzido no Teams em 2021.
Você pode criar aplicativos que parecem mais nativos do Teams removendo as margens em todas as guias. As guias com margens removidas se alinham com os [designs do kit de interface do usuário](~/tabs/design/tabs.md) do Microsoft Teams. A maioria dos aplicativos tem uma aparência aprimorada sem margens.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tab wit e sem margens":::

> [!NOTE]
> Esse recurso não é aplicável a clientes móveis, pois as guias exibidas nos clientes móveis não têm margens.

## <a name="guidelines"></a>Diretrizes

A remoção de margens de guia afeta seus aplicativos do Teams que usam guias. Nesses casos, você pode adicionar margens ao redor de seus designs de guia onde ela é necessária. Os designs de aplicativos em produção têm um efeito de preenchimento extra, ou seja, margens fornecidas pelo Teams e margens fornecidas pela guia. No entanto, o preenchimento extra é apenas temporário e desaparece em algumas semanas, deixando apenas o preenchimento fornecido pelo aplicativo.

## <a name="faq"></a>Perguntas frequentes

**Está tudo bem para o chrome do aplicativo, como barra de cabeçalho ou barra de tarefas, tocar nas bordas de nossos designs?**

Sim, isso é bom e o Teams incentiva esse design. Ele ajuda o aplicativo a se sentir nativo.

**Está tudo bem para o conteúdo do aplicativo, como texto, logotipos e imagens, tocar nas bordas esquerda e direita de nossos designs?**

Não, você deve fornecer seu próprio preenchimento ou margens à esquerda e à direita de todo o conteúdo do aplicativo para garantir que ele não toque nas bordas da interface do usuário. Você também pode adicionar margens na parte superior da guia, se necessário.

**Qual é o tamanho das margens de guia que o Teams aplicou anteriormente?**

* Esquerda e direita: 20 pixels
* Top: 16 pixels
* Inferior: 0 pixels

> [!IMPORTANT]
>
> * Todas as guias têm suas margens removidas: guias pessoais, guias de chat (grupo), guias de reunião e guias de canal.
> * A alteração da remoção da margem de guia se aplica a todas as guias. Não há como aceitar ou cancelar a alteração.
> * A alteração das margens de guia pode afetar guias que dependem do Microsoft Teams para fornecer margens em torno de sua interface do usuário.

## <a name="see-also"></a>Confira também

* [Compilar guias para o Teams](../tabs/what-are-tabs.md)
* [Criar uma guia pessoal](../tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou guia de grupo](../tabs/how-to/create-channel-group-tab.md)
