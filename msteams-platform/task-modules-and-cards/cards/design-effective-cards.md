---
title: Projetando Cartões Adaptáveis para seu aplicativo
description: Aprenda a projetar Cartões Adaptáveis para o Teams e obtenha o Kit de IU do Microsoft Teams.
localization_priority: Priority
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: ca7c38f112808f98ae1555e91f794f032e880c862a697e1218953d40cbb410aa
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57708465"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a>Projetando Cartões Adaptáveis para seu aplicativo Microsoft Teams

Um Cartão Adaptável contém um corpo de elementos de cartão de forma livre e um conjunto opcional de ações. Cartões Adaptáveis são fragmentos de conteúdo acionáveis que você pode adicionar a uma conversa por meio de um bot ou extensão de mensagem. Usando texto, gráficos e botões, esses cartões fornecem uma comunicação rica para seu público-alvo.

A estrutura de Cartão Adaptável é usada em muitos produtos da Microsoft, incluindo o Teams. Você pode enviar cartões dentro de mensagens para usuários por meio de bots ou extensões de mensagens. Os usuários também podem realizar ações em cartões quando presentes.

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Exemplo de visão geral de um Cartão Adaptável." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Kit de IU do Microsoft Teams

Você pode encontrar diretrizes de design mais abrangentes para Cartões Adaptáveis no Teams, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit de IU do Microsoft Teams. O kit de IU também cobre tópicos essenciais, como temas, acessibilidade e dimensionamento dinâmico.

> [!div class="nextstepaction"]
> [Obtenha o Kit de IU do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a>Designer de cartões adaptáveis

Você também pode começar a projetar seus Cartões Adaptáveis diretamente no navegador.

> [!div class="nextstepaction"]
> [Experimente o designer de cartões adaptáveis ](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a>Tipos de Cartões Adaptáveis

### <a name="hero"></a>Destaque

Nosso maior cartão. Uso para compartilhar artigos ou cenários onde uma imagem conta a maior parte da história.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="O exemplo mostra um cartão de destaque do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-hero-card.png" alt-text="O exemplo mostra um cartão de destaque do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="thumbnail"></a>Miniatura

Use para enviar uma mensagem acionável simples.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="O exemplo mostra um cartão em miniatura do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-thumbnail-card.png" alt-text="O exemplo mostra um cartão em miniatura do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="list"></a>List

Use em cenários em que você deseja que o usuário escolha um item de uma lista, mas os itens não precisam de muitas explicações.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="O exemplo mostra um cartão de lista do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-list-card.png" alt-text="O exemplo mostra um cartão de lista do Cartão Adaptável no dispositivo móvel." border="false":::

---
Use for news digests and round-up posts. Note: We recommend the thumbnail card for a single update or news item.
':::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Example shows an Adaptive Card digest card." border="false"::': null
':::image type="content" source="../../assets/images/adaptive-cards/mobile-digest-card.png" alt-text="Example shows an Adaptive Card digest card on mobile." border="false"::': null
---

### <a name="media"></a>Mídia

Use quando quiser combinar texto e mídia, como áudio ou vídeo.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="O exemplo mostra um cartão de mídia do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-media-card.png" alt-text="O exemplo mostra um cartão de mídia do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="people"></a>Pessoas

Melhor usado para transmitir com eficiência quem está envolvido em uma tarefa.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="O exemplo mostra um cartão de pessoas do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-people-card.png" alt-text="O exemplo mostra um cartão de pessoas do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="request-ticket"></a>Solicitar ingresso

Use para obter entradas rápidas de um usuário para criar automaticamente uma tarefa ou tíquete.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="O exemplo mostra um cartão de tíquete de solicitação do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-request-ticket-card.png" alt-text="O exemplo mostra um cartão de tíquete de solicitação do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="image-set"></a>Conjunto de imagens

Use para enviar várias miniaturas de imagens.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de imagens do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-image-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de imagens do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="action-set"></a>Conjunto de ações

Use quando quiser que o usuário selecione um botão e, em seguida, reúna a entrada adicional do usuário do mesmo cartão.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de ações do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-action-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de ações do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="choice-set"></a>Conjunto de opções

Use para reunir várias entradas do usuário.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de opções do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-choice-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de opções do Cartão Adaptável no dispositivo móvel." border="false":::

---

## <a name="anatomy"></a>Anatomia

Os Cartões Adaptáveis têm muita flexibilidade. Mas, no mínimo, sugerimos fortemente incluir os seguintes componentes em cada cartão.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="O exemplo mostra a anatomia do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-anatomy.png" alt-text="O exemplo mostra a anatomia do Cartão Adaptável no dispositivo móvel." border="false":::

---

|Contador|Descrição|
|----------|-----------|
|A|**Cabeçalho**: Deixe seus cabeçalhos claros e concisos.|
|B|**Cópia do corpo**: Transmita detalhes que sejam muito longos ou não são importantes o suficiente para incluir no cabeçalho.|
|C|**Ações primárias**: Como prática recomendada, inclua 13 ações principais. Você pode ter até seis.|

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="primary-and-secondary-actions"></a>Ações primárias e secundárias

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Prática recomendada sobre como você deve incluir apenas um pequeno conjunto de ações em um Cartão Adaptável." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a>Faça: Usar até seis ações principais

Embora os Cartões Adaptáveis possam suportar seis ações primárias, a maioria dos cartões não precisa disso. As ações devem ser claras, concisas e diretas. Menos é mais.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Prática recomendada sobre como não sobrecarregar os usuários com demasiadas ações em um Cartão Adaptável." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a>Não faça: Usar mais de seis ações principais

Os Cartões Adaptáveis devem apresentar conteúdo rápido e prático. Muitas ações podem sobrecarregar um usuário.

   :::column-end:::
:::row-end:::

### <a name="frequency"></a>Frequência

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Práticas recomendadas sobre a frequência do Cartão Adaptável." border="false":::

#### <a name="do-be-concise"></a>Faça: Seja conciso

É fácil enviar vários cartões em uma conversa, mas quando os cartões saem da exibição, eles se tornam menos úteis. Experimente se limitar ao essencial. Isso é especialmente verdadeiro em um canal onde os usuários têm menos tolerância com o que percebem como "ruído".
