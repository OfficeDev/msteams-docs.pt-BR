---
title: Projetar seu aplicativo – Entender a estrutura do aplicativo
description: Entenda o que você pode ou não personalizar no Microsoft Teams ao projetar seu aplicativo.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: surbhigupta
keywords: wireframe channel chat meeting message extensions mobile desktop
ms.openlocfilehash: 8353fa74dce12642e5ca96c85c34dc06fc0da203
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103282"
---
# <a name="understand-the-microsoft-teams-app-structure"></a>Compreender a estrutura do aplicativo Microsoft Teams

Ao criar seu aplicativo, é importante saber o que você pode ou não personalizar no Microsoft Teams. Essas informações podem ajudá-lo a entender melhor quais partes da experiência do aplicativo você controla.

Os seguintes wireframes mostram:

* As superfícies que você pode personalizar em cada Teams de aplicativo (descritas em rosa).
* Os escopos compatíveis com cada funcionalidade.

> [!TIP]
> **O que significa escopo?** Um escopo é uma área em Teams onde as pessoas podem usar seu aplicativo. Os aplicativos podem ter um ou vários escopos, incluindo pessoal, canais, chats e reuniões.

## <a name="personal-apps"></a>Aplicativos pessoais

Os aplicativos pessoais fornecem uma tela grande para hospedar o conteúdo do aplicativo para usuários individuais.

***Escopos com suporte**: Pessoal*

### <a name="mobile"></a>Celular

A tela é um modo de exibição da Web para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-mobile.png" alt-text="Imagem conceitual mostrando as áreas de front-end Teams que os desenvolvedores podem personalizar para aplicativos pessoais em dispositivos móveis." border="false":::

### <a name="desktop"></a>Desktop

A tela é um iframe para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-desktop.png" alt-text="Imagem conceitual mostrando as áreas de front-end Teams que os desenvolvedores podem personalizar para aplicativos pessoais na área de trabalho." border="false":::

## <a name="tabs"></a>Guias

As guias fornecem uma tela grande para hospedar o conteúdo do aplicativo para um grupo de usuários. Você pode incluir guias em espaços compartilhados, como canais, chats e convites de reunião.

***Escopos com suporte**: Canais, Chats, Reuniões*

### <a name="mobile"></a>Celular

A tela é um modo de exibição da Web para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-mobile.png" alt-text="Imagem conceitual mostrando as áreas de front-end Teams que os desenvolvedores podem personalizar para guias no celular." border="false":::

### <a name="desktop"></a>Desktop

A tela é um iframe para que você possa personalizar completamente a experiência.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-desktop.png" alt-text="Imagem conceitual mostrando as áreas de front-end Teams que os desenvolvedores podem personalizar para guias na área de trabalho." border="false":::

## <a name="bots"></a>Bots

Os bots são aplicativos de conversa que se integram Teams de mensagens nativas, portanto, o trabalho da interface do usuário é tratado para você. Do ponto de vista do design, ainda há oportunidades de adicionar personalidade, funcionalidade personalizada e informações avançadas e acionáveis com nosso suporte ao NLP (processamento de linguagem natural) e à plataforma de Cartões Adaptáveis.

***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões*

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-mobile.png" alt-text="Imagem conceitual mostrando as áreas de front-end Teams que os desenvolvedores podem personalizar para bots em dispositivos móveis." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-desktop.png" alt-text="Imagem conceitual mostrando as áreas de front-end Teams que os desenvolvedores podem personalizar para bots na área de trabalho." border="false":::

## <a name="message-extensions"></a>Extensões de mensagem

Extensões de mensagem são atalhos para inserir o conteúdo do aplicativo ou agir em uma mensagem sem navegar para longe da conversa. As extensões de mensagem baseadas em ação oferecem mais controle da experiência, enquanto Teams lida com grande parte do que é renderizado para extensões de mensagem baseadas em pesquisa.

***Escopos com suporte**: Pessoal, Canais, Chats, Reuniões*

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-mobile.png" alt-text="Imagem conceitual mostrando as áreas de front-end Teams que os desenvolvedores podem personalizar para extensões de mensagem em dispositivos móveis." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-desktop.png" alt-text="Imagem conceitual mostrando as áreas de front-end Teams que os desenvolvedores podem personalizar para extensões de mensagem na área de trabalho." border="false":::

## <a name="meeting-extensions"></a>Extensões de reunião

As extensões de reunião são aplicativos para aprimorar reuniões ao vivo. Você pode hospedar o conteúdo do aplicativo em vários cenários, incluindo antes, durante e após reuniões.

***Escopos com suporte**: Reuniões, Chats*

### <a name="mobile"></a>Celular

A superfície é um modo de exibição da Web, permitindo que você personalize a experiência, mas tenha em mente que, durante as reuniões, esses aplicativos usam tema escuro.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-mobile.png" alt-text="Imagem conceitual mostrando as áreas de front-end Teams que os desenvolvedores podem personalizar para extensões de reunião em dispositivos móveis." border="false":::

### <a name="desktop"></a>Desktop

A superfície é um iframe, permitindo que você personalize a experiência, mas tenha em mente que, durante as reuniões, esses aplicativos usam tema escuro e são estreitos.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-desktop.png" alt-text="Imagem conceitual mostrando as áreas de front-end Teams que os desenvolvedores podem personalizar para extensões de reunião na área de trabalho." border="false":::
