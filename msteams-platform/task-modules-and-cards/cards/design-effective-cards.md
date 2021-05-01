---
title: Projetando cartões adaptáveis para seu aplicativo
description: Saiba como projetar Cartões Adaptáveis para Teams e obter o kit Microsoft Teams interface do usuário.
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 14ffff1264e716e04a1ffb5549b71a8b7ec5fc14
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101734"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a>Projetando cartões adaptáveis para seu Microsoft Teams app

Um Cartão Adaptável contém um corpo de forma livre de elementos de cartão e um conjunto opcional de ações. Cartões adaptáveis são trechos acionáveis de conteúdo que você pode adicionar a uma conversa por meio de um bot ou extensão de mensagens. Usando texto, gráficos e botões, essas placas fornecem uma comunicação rica para o público-alvo.

A estrutura cartão adaptável é usada em muitos produtos Microsoft, incluindo Teams. Você pode enviar cartões dentro de mensagens para os usuários por meio de bots ou extensões de mensagens. Os usuários podem tomar ações em cartões quando presentes.

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Exemplo de visão geral de um Cartão Adaptável." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Você pode encontrar diretrizes de design mais abrangentes para Cartões Adaptáveis no Teams, incluindo elementos que você pode obter e modificar conforme necessário, no kit de interface do usuário Microsoft Teams UI. O kit de interface do usuário também aborda tópicos essenciais, como temas, acessibilidade e tamanho responsivo.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a>Designer de Cartões Adaptáveis

Você também pode começar a projetar seus Cartões Adaptáveis diretamente no navegador.

> [!div class="nextstepaction"]
> [Experimente o designer de Cartões Adaptáveis](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a>Tipos de cartões adaptáveis

### <a name="hero"></a>Destaque

Nosso maior cartão. Use para compartilhar artigos ou cenários em que uma imagem conta a maior parte da história.

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Exemplo mostra um cartão de herói do Cartão Adaptável." border="false":::

### <a name="thumbnail"></a>Miniatura

Use para enviar uma mensagem simples a actionable.

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Exemplo mostra um cartão de miniatura do Cartão Adaptável." border="false":::

### <a name="list"></a>List

Use em cenários em que você deseja que o usuário escolha um item de uma lista, mas os itens não precisam de muita explicação.

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Exemplo mostra um cartão de lista cartão adaptável." border="false":::

### <a name="digest"></a>Digest

Use para resumos de notícias e postagens arredonddas. Observação: recomendamos o cartão de miniatura para uma única atualização ou item de notícias.

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Exemplo mostra um cartão digest do Cartão Adaptável." border="false":::

### <a name="media"></a>Mídia

Use quando quiser combinar texto e mídia, como áudio ou vídeo.

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Exemplo mostra um cartão de mídia cartão adaptável." border="false":::

### <a name="people"></a>Pessoas

Melhor usado quando você transmite com eficiência quem está envolvido com uma tarefa.

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Exemplo mostra um cartão de pessoas do Cartão Adaptável." border="false":::

### <a name="request-ticket"></a>Tíquete de solicitação

Use para obter entradas rápidas de um usuário para criar automaticamente uma tarefa ou tíquete.

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Exemplo mostra um cartão de tíquete de solicitação de Cartão Adaptável." border="false":::

### <a name="imageset"></a>ImageSet

Use para enviar várias miniaturas de imagem.

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Exemplo mostra um cartão de conjunto de imagens do Cartão Adaptável." border="false":::

### <a name="actionset"></a>ActionSet

Use quando quiser que o usuário selecione um botão e, em seguida, reúna a entrada do usuário de adição do mesmo cartão.

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Exemplo mostra um cartão de conjunto de ações cartão adaptável." border="false":::

### <a name="choiceset"></a>ChoiceSet

Use para coletar várias entradas do usuário.

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Exemplo mostra um cartão de conjunto de opções do Cartão Adaptável." border="false":::

## <a name="anatomy"></a>Anatomia

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Exemplo mostra um cartão de anatomia do Cartão Adaptável." border="false":::

Cartões adaptáveis têm muita flexibilidade. No mínimo, sugerimos incluir os seguintes componentes em cada cartão:

|Contador|Descrição|
|----------|-----------|
|A|**Header**: Tornar os headers claros e concisos, mas descritivos.|
|B|**Cópia do** corpo : use para transmitir detalhes que são muito longos ou não importantes o suficiente para incluir no header.|
|C|**Ações primárias**: Como prática prática, inclua ações primárias de 1 a 3. No máximo seis são permitidos.|

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="primary-and-secondary-actions"></a>Ações primárias e secundárias

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Práticas práticas sobre como você deve incluir apenas um pequeno conjunto de ações em um Cartão Adaptável." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a>Fazer: usar até seis ações primárias

Embora os Cartões Adaptáveis possam dar suporte a seis ações principais, a maioria dos cartões não precisa disso. As ações devem ser claras, concisas e diretas. Menos é mais.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Práticas práticas sobre como não sobrecarregar os usuários com muitas ações em um Cartão Adaptável." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a>Não: use mais de seis ações primárias

Cartões adaptáveis devem apresentar conteúdo rápido e ativos. Muitas ações podem sobrecarregar um usuário.

   :::column-end:::
:::row-end:::

### <a name="frequency"></a>Frequência

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Prática prática sobre a frequência do Cartão Adaptável." border="false":::

#### <a name="do-be-concise"></a>Do: Ser conciso

É fácil enviar vários cartões para uma conversa, mas quando os cartões ficam fora de exibição, eles se tornam menos úteis. Tente limitar-se ao essencial. Isso é especialmente verdadeiro em um canal onde os usuários têm menos tolerância para o que eles percebem como "ruído".
