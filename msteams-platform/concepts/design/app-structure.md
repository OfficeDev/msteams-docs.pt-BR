---
title: Projetar seu aplicativo - Compreender a estrutura do aplicativo
description: Entenda o que você pode ou não personalizar no Microsoft Teams ao projetar seu aplicativo.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: surbhigupta
keywords: wireframe channel chat meeting messaging extensions mobile desktop
ms.openlocfilehash: 3d63cc705ac567b0b19db2e3caf4a84420dae9bd
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887571"
---
# <a name="understand-the-microsoft-teams-app-structure"></a>Compreender a estrutura Microsoft Teams de aplicativos

Ao criar seu aplicativo, é importante saber o que você pode ou não personalizar no Microsoft Teams. Essas informações podem ajudá-lo a entender melhor quais partes da experiência do aplicativo você controla.

Os seguintes wireframes mostram:

* As superfícies que você pode personalizar em cada Teams do aplicativo (descrito em rosa).
* Os escopos com os suportes de cada recurso.

> [!TIP]
> **O que significa escopo?** Um escopo é uma área em Teams onde as pessoas podem usar seu aplicativo. Os aplicativos podem ter um ou vários escopos, incluindo pessoal, canais, chats e reuniões.

## <a name="personal-apps"></a>Aplicativos pessoais

Os aplicativos pessoais fornecem uma tela grande para hospedar o conteúdo do aplicativo para usuários individuais.

***Escopos com suporte**: Pessoal*

### <a name="mobile"></a>Celular

A tela é uma webview para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-mobile.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para aplicativos pessoais em dispositivos móveis." border="false":::

### <a name="desktop"></a>Desktop

A tela é um iframe para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para aplicativos pessoais na área de trabalho." border="false":::

## <a name="tabs"></a>Guias

As guias fornecem uma tela grande para hospedar o conteúdo do aplicativo para um grupo de usuários. Você pode incluir guias em espaços compartilhados, como canais, chats e convites de reunião.

***Escopos com suporte**: Canais, Chats, Reuniões*

### <a name="mobile"></a>Celular

A tela é uma webview para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-mobile.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para guias no celular." border="false":::

### <a name="desktop"></a>Desktop

A tela é um iframe para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para guias na área de trabalho." border="false":::

## <a name="bots"></a>Bots

Bots são aplicativos de conversa que se integram Teams recursos nativos de mensagens, portanto, o trabalho da interface do usuário é manipulado para você. Do ponto de vista de design, ainda há oportunidades de adicionar personalidade, funcionalidade personalizada e informações avançadas e acionáveis com nosso suporte ao processamento de linguagem natural (NLP) e à plataforma Cartões Adaptáveis.

***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões*

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-mobile.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para bots em dispositivos móveis." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para bots na área de trabalho." border="false":::

## <a name="messaging-extensions"></a>Extensões de mensagens

Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem sair da conversa. As extensões de mensagens baseadas em ação dão mais controle à experiência, enquanto Teams lida com grande parte do que renderiza para extensões de mensagens baseadas em pesquisa.

***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões*

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-mobile.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de mensagens em dispositivos móveis." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de mensagens na área de trabalho." border="false":::

## <a name="meeting-extensions"></a>Extensões de reunião

Extensões de reunião são aplicativos para aprimorar reuniões ao vivo. Você pode hospedar o conteúdo do aplicativo em vários cenários, incluindo antes, durante e após reuniões.

***Escopos com suporte**: Reuniões, Chats*

### <a name="mobile"></a>Celular

A superfície é uma webview, permitindo que você personalize a experiência, mas tenha em mente que durante as reuniões esses aplicativos usam tema escuro.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-mobile.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de reunião em dispositivos móveis." border="false":::

### <a name="desktop"></a>Desktop

A superfície é um iframe, permitindo que você personalize a experiência, mas tenha em mente que durante as reuniões esses aplicativos usam tema escuro e são estreitos.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-desktop.png" alt-text="Imagem conceitual mostrando as áreas front-end no Teams que os desenvolvedores podem personalizar para extensões de reunião na área de trabalho." border="false":::
