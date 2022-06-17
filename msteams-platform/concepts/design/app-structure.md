---
title: Projete seu aplicativo - Entenda a estrutura do aplicativo
description: Neste módulo, saiba o que você pode ou não personalizar no Microsoft Teams ao projetar a estrutura do aplicativo.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: surbhigupta
ms.openlocfilehash: cbcf44572b0105f9c0af4c7dc8cd0b00b6f5f9b9
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144394"
---
# <a name="understand-the-microsoft-teams-app-structure"></a>Compreender a estrutura do aplicativo Microsoft Teams

Ao criar seu aplicativo, é importante saber o que você pode e o que não pode personalizar no Microsoft Teams. Essas informações podem ajudar você a entender melhor quais partes da experiência do aplicativo você controla.

Os seguintes diagramas vetoriais mostram a você:

* As superfícies que você pode personalizar em cada recurso do aplicativo Teams (destacado em rosa).
* Os escopos que cada recurso suporta.

> [!TIP]
> **O que significa escopo?** Um escopo é uma área no Teams onde as pessoas podem usar seu aplicativo. Os aplicativos podem ter um ou vários escopos, incluindo pessoal, canais, chats e reuniões.

## <a name="personal-apps"></a>Aplicativos pessoais

Os aplicativos pessoais fornecem uma grande tela para hospedar o conteúdo do aplicativo para usuários individuais.

***Escopos compatíveis**: Pessoal*

### <a name="mobile"></a>Celular

A tela é um modo de exibição da Web para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-mobile.png" alt-text="Imagem conceitual mostrando as áreas de front-end no Teams que os desenvolvedores podem personalizar para aplicativos pessoais em dispositivos móveis." border="false":::

### <a name="desktop"></a>Área de trabalho

A tela é um iframe para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para aplicativos pessoais na área de trabalho." border="false":::

## <a name="tabs"></a>Guias

As guias fornecem uma tela grande para hospedar o conteúdo do seu aplicativo para um grupo de usuários. Você pode incluir guias em espaços compartilhados, como canais, chats e convites de reunião.

***Escopos com suporte**: Canais, Chats, Reuniões*

### <a name="mobile"></a>Celular

A tela é um modo de exibição da Web para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-mobile.png" alt-text="Imagem conceitual mostrando as áreas de front-end no Teams que os desenvolvedores podem personalizar para guias em dispositivos móveis." border="false":::

### <a name="desktop"></a>Área de trabalho

A tela é um iframe para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-desktop.png" alt-text="Imagem conceitual mostrando as áreas de front-end no Teams que os desenvolvedores podem personalizar para guias na área de trabalho." border="false":::

## <a name="bots"></a>Bots

Os bots são aplicativos de conversação que se integram aos recursos de mensagens nativos do Teams, para que o trabalho da interface do usuário seja tratado para você. Do ponto de vista do design, ainda há oportunidades para adicionar personalidade, funcionalidade personalizada e informações ricas e acionáveis ​​com nosso suporte de processamento de linguagem natural (NLP) e plataforma de cartões adaptáveis.

***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões*

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-mobile.png" alt-text="Imagem conceitual mostrando as áreas de front-end no Teams que os desenvolvedores podem personalizar para bots em dispositivos móveis." border="false":::

### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-desktop.png" alt-text="Imagem conceitual mostrando as áreas de front-end no Teams que os desenvolvedores podem personalizar para bots na área de trabalho." border="false":::

## <a name="message-extensions"></a>Extensões de mensagens

Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou reagir a uma mensagem sem sair da conversa. As extensões de mensagem baseadas em ação oferecem mais controle da experiência, enquanto o Teams lida com muito do que é renderizado para extensões de mensagem baseadas em pesquisa.

***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões*

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-mobile.png" alt-text="Imagem conceitual mostrando as áreas de front-end no Teams que os desenvolvedores podem personalizar para extensões de mensagem em dispositivos móveis." border="false":::

### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-desktop.png" alt-text="Imagem conceitual mostrando as áreas de front-end no Teams que os desenvolvedores podem personalizar para extensões de mensagem na área de trabalho." border="false":::

## <a name="meeting-extensions"></a>Extensões de reunião

As extensões de reunião são aplicativos para aprimorar as reuniões ao vivo. Você pode hospedar o conteúdo do seu aplicativo em vários cenários, incluindo antes, durante e depois das reuniões.

***Escopos com suporte**: Reuniões, Chats*

### <a name="mobile"></a>Celular

A superfície é uma visualização da web, permitindo que você personalize a experiência, mas lembre-se de que durante as reuniões esses aplicativos usam o tema escuro.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-mobile.png" alt-text="Imagem conceitual mostrando as áreas de front-end no Teams que os desenvolvedores podem personalizar para extensões de reunião em dispositivos móveis." border="false":::

### <a name="desktop"></a>Área de trabalho

A superfície é um iframe, permitindo que você personalize a experiência, mas lembre-se de que durante as reuniões esses aplicativos usam o tema escuro e são estreitos.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de reunião na área de trabalho." border="false":::
