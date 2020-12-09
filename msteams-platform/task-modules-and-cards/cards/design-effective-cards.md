---
title: Criando cartões adaptáveis para seu aplicativo
description: Saiba como projetar cartões adaptáveis para equipes e obter o kit de interface do usuário do Microsoft Teams.
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: bd48846284620415cc8cadabc59f2ab7b61d5189
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604491"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a>Projetando cartões adaptáveis para seu aplicativo do Microsoft Teams

Um cartão adaptável contém um corpo de forma livre de elementos de cartão e conjunto opcional de ações. Cartões adaptáveis são trechos acionáveis do conteúdo que você pode adicionar a uma conversa por meio de um bot ou extensão de mensagens. Usando texto, elementos gráficos e botões, esses cartões fornecem comunicação avançada com o público.

A estrutura de cartão adaptável é usada em vários produtos da Microsoft, incluindo o Teams. Você pode enviar cartões dentro de mensagens para usuários via bots ou extensões de mensagens. Os usuários podem executar ações em cartões, quando presentes.

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Kit de interface do usuário do Microsoft Teams

Você pode encontrar diretrizes de design mais abrangentes para cartões adaptáveis no Teams, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams. O kit de interface do usuário também aborda tópicos essenciais, como temas, acessibilidade e dimensionamento responsivo.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário do Microsoft Teams (figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a>Designer de cartões adaptáveis

Você também pode começar a criar seus cartões adaptáveis diretamente no navegador.

> [!div class="nextstepaction"]
> [Experimente o designer de cartões adaptáveis](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a>Tipos de cartões adaptáveis

### <a name="hero"></a>Destaque

Nosso maior cartão. Use para compartilhar artigos ou cenários onde uma imagem diz maior parte da história.

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="thumbnail"></a>Thumbnail

Use para enviar uma mensagem acionável simples.

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="list"></a>Listar

Use em cenários em que você deseja que o usuário escolha um item de uma lista, mas os itens não precisam de muita explicação.

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="digest"></a>Digest

Use para resumos de notícias e postagens de arredondamento. Observação: Recomendamos o cartão de miniatura de uma atualização única ou de um item de notícias.

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="media"></a>Mídia

Use quando quiser combinar texto e mídia, como áudio ou vídeo.

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="people"></a>Pessoas

Melhor usado quando você transmite com eficiência as pessoas envolvidas em uma tarefa.

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="request-ticket"></a>Solicitar Tíquete

Use para obter entradas rápidas de um usuário para criar automaticamente uma tarefa ou um tíquete.

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="imageset"></a>ImageSet

Use para enviar várias miniaturas de imagem.

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="actionset"></a>ActionSet

Use quando você quiser que o usuário selecione um botão e, em seguida, coletar a entrada de usuário do mesmo cartão.

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="choiceset"></a>Choiceset

Use para coletar várias entradas do usuário.

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

## <a name="anatomy"></a>Anatomia

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Ilustração mostrando a anatomia de interface do usuário de um cartão adaptável." border="false":::

Cartões adaptáveis têm muita flexibilidade. Mas, no mínimo, é recomendável que você inclua os seguintes componentes em todos os cartões:

|Contador|Descrição|
|----------|-----------|
|A|**Cabeçalho**: torne os cabeçalhos claros e concisos, mas descritivos.|
|B|**Cópia de corpo**: Use para transmitir detalhes que seja muito longo ou não seja importante o suficiente para incluir no cabeçalho.|
|C|**Ações principais**: como prática recomendada, inclua ações primárias de 1-3. São permitidos no máximo seis.|

## <a name="best-practices"></a>Práticas recomendadas

### <a name="primary-and-secondary-actions"></a>Ações primárias e secundárias

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Exemplo mostrando uma prática recomendada de cartões adaptáveis." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a>Fazer: usar até seis ações principais

Embora os cartões adaptáveis possam suportar seis ações principais, a maioria dos cartões não precisa de. As ações devem ser claras, concisas e diretas. Menos é mais.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Exemplo mostrando uma prática recomendada de cartões adaptáveis." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a>Não: usar mais de seis ações principais

Os cartões adaptáveis devem apresentar conteúdo rápido e acionável. Muitas ações podem sobrecarregar um usuário.

   :::column-end:::
:::row-end:::

### <a name="frequency"></a>Frequência

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Exemplo mostrando uma prática recomendada de cartões adaptáveis." border="false":::

#### <a name="do-be-concise"></a>Fazer: seja conciso

É fácil enviar vários cartões para uma conversa, mas depois que os cartões saem do modo de exibição, eles se tornam menos úteis. Tente se limitar ao Essentials. Isso se aplica especialmente em um canal em que os usuários têm menos tolerância para o que eles percebem como "ruído".
