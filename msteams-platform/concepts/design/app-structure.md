---
title: Projetar seu aplicativo - Compreender a estrutura do aplicativo
description: Entenda o que você pode ou não personalizar no Microsoft Teams ao projetar seu aplicativo.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: bf84ad1d52cf46e9242bf4122dc5e900461ab806
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631231"
---
# <a name="understand-the-microsoft-teams-app-structure"></a>Compreender a estrutura Microsoft Teams de aplicativos

Ao criar seu aplicativo, é importante saber o que você pode ou não personalizar no Microsoft Teams. Essas informações podem ajudá-lo a entender melhor quais partes da experiência do aplicativo você controla.

Os seguintes wireframes mostram:

* As superfícies que você pode personalizar em cada Teams de aplicativo (descrito em azul).
* Os escopos com os suportes de cada recurso.

> [!NOTE]
> **O que significa escopo?** Um escopo é uma área em Teams onde as pessoas podem usar seu aplicativo. Os aplicativos podem ter um ou vários escopos, incluindo pessoal, canais, chats e reuniões.

## <a name="personal-apps"></a>Aplicativos pessoais

Os aplicativos pessoais fornecem uma tela grande para hospedar o conteúdo do aplicativo para usuários individuais. A tela é um iframe para que você possa personalizar completamente a experiência.

***Escopos com suporte**: Pessoal*

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para aplicativos pessoais." border="false":::

## <a name="tabs"></a>Guias

As guias fornecem uma tela grande para hospedar o conteúdo do aplicativo para um grupo de usuários. Você pode incluir guias em espaços compartilhados, como canais, chats e convites de reunião. A tela é um iframe para que você possa personalizar completamente a experiência.

***Escopos com suporte**: Canais, Chats, Reuniões*

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para guias." border="false":::

## <a name="bots"></a>Bots

Bots são aplicativos de conversa que se integram Teams recursos nativos de mensagens, portanto, o trabalho da interface do usuário é manipulado para você. Do ponto de vista de design, ainda há oportunidades de adicionar personalidade, funcionalidade personalizada e informações avançadas e acionáveis com nosso suporte ao processamento de linguagem natural (NLP) e à plataforma Cartões Adaptáveis.

***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões*

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para bots." border="false":::

## <a name="messaging-extensions"></a>Extensões de mensagens

Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem sair da conversa. As extensões de mensagens baseadas em ação dão mais controle à experiência, enquanto Teams lida com grande parte do que renderiza para extensões de mensagens baseadas em pesquisa.

***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões*

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de mensagens." border="false":::

## <a name="meeting-extensions"></a>Extensões de reunião

Extensões de reunião são aplicativos para aprimorar reuniões ao vivo. Você pode hospedar o conteúdo do aplicativo em vários cenários, incluindo antes, durante e após reuniões. A superfície é um iframe, permitindo que você personalize a experiência, mas tenha em mente que esses aplicativos são temas escuros e estreitos durante as reuniões.

***Escopos com suporte**: Reuniões, Chats*

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de reunião." border="false":::
