---
title: Solução do Teams para a criação de aplicativos
author: heath-hamilton
description: Aprenda a visão geral de soluções do Teams para criar aplicativos e forneça suporte desde o planejamento do aplicativo até a sua distribuição.
ms.topic: overview
ms.localizationpriority: high
ms.author: lajanuar
ms.date: 11/02/2021
ms.openlocfilehash: 1f2422f6e5c32e30bba80141e53a6ab60b08e08b
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123542"
---
# <a name="the-teams-solution"></a>A solução do Microsoft Teams

A Plataforma Microsoft Teams é uma plataforma poderosa e flexível para a criação de aplicativos do Microsoft Teams. Ela fornece um amplo conjunto de ambientes de desenvolvimento e ferramentas para dar suporte ao desenvolvimento de aplicativos.

## <a name="the-user-story"></a>A história do usuário

Você obteve uma exibição das ofertas do Teams. Agora você pode mapeá-las de acordo com as necessidades do usuário. Vamos revisitar o cenário.

O desenvolvedor da Agência de Viagens e Tours quer criar um aplicativo para seus usuários, os viajantes. O aplicativo deve:

- Verificar e enviar a previsão para os passageiros registrados na agência de viagens.
- Notificar os usuários um dia antes da data de partida para que eles possam se planejar.

Requisitos de agrupamento e mapeamento de recursos do Teams:

| Requisitos do aplicativo do usuário | Verificar previsão | Notificação antes da viagem | Usuário registrado |
| --- |:---:|:---:|:---:|
| **Recursos** | Bot | &nbsp; | &nbsp; |
| **Integração** | &nbsp; | &nbsp; | Microsoft Graph, API do Clima |
| **Escopo** | &nbsp; | Aplicativo pessoal | &nbsp; |
| **Ponto de integração** | &nbsp; | Chat | &nbsp; |

**Solução de aplicativo do Teams**: um aplicativo de *bot de chat pessoal* do Teams que verifica e *envia notificação de previsão* para *usuários registrados* antes da data da viagem.

:::image type="content" source="../msteams-platform/assets/images/overview/developer-scenario-solution.png" alt-text="Um desenvolvedor de uma agência de viagens cria um bot para o Microsoft Teams que envia a previsão do tempo aos clientes para eles se planejarem antes de suas viagens" border="false":::

O Teams oferece essas e muito mais funcionalidades para trazer aos usuários uma solução de aplicativos com recursos avançados. Para desenvolver este aplicativo:

1. Crie um aplicativo de bot de chat pessoal.
1. Integre com uma API externa de previsão do tempo para conectar e solicitar previsões para datas e localizações específicas.
1. Integre com o Microsoft Graph para usuários registrados.
1. Verifique e envie detalhes da previsão com base na data de viagem e no local de viagem do usuário.

## <a name="choose-what-suits-you"></a>Escolha o que combina com você

Você pode criar um aplicativo Teams de acordo com os requisitos do aplicativo. Com base em fatores, como necessidades de negócios, ambiente de desenvolvimento, conhecimento de domínio, selecione o ambiente e as ferramentas que deseja criar seu aplicativo.

Um aplicativo Teams oferece a flexibilidade de escolher seu ambiente de build. Inclui ferramentas, estrutura e idiomas para trabalhar no desenvolvimento do aplicativo.

:::image type="content" source="../msteams-platform/assets/images/overview/tools-of-your-choice.png" alt-text="A empresa precisa de um aplicativo" border="false":::

Crie seu aplicativo Teams no ambiente que funciona para seus requisitos específicos. Você pode até mesmo selecionar uma combinação.

Por exemplo, você pode usar o kit de ferramentas do Teams para criar um aplicativo com JavaScript e hospedá-lo em um site do SharePoint.

## <a name="teams-collaborative-platform"></a>Plataforma colaborativa do Teams

Um aplicativo Teams traz aos usuários as vantagens de um workspace colaborativo.

Como plataforma para criar aplicativos, o Teams oferece uma gama completa de aplicativos e kits de ferramentas. A plataforma Teams dá suporte a você em todos os estágios, desde planejar seu aplicativo até distribuí-lo.

:::image type="content" source="../msteams-platform/assets/images/overview/teams-dev-life-cycle.png" alt-text="Descrevendo um ciclo de vida do desenvolvimento do aplicativo Teams. Planejar, projetar, construir, estender, testar, implantar, distribuir. Detalhes mostrados em uma lista de marcadores abaixo." border="false":::

Desde o design até a criação e a distribuição de um aplicativo do Teams, você pode usar várias ferramentas e serviços. Um exemplo de fluxo de desenvolvimento pode ser:

1. Planejar seu projeto e descobrir o requisito.
1. Crie o aplicativo. Use o Kit de Interface do Usuário do Teams e a Biblioteca de Interface do Usuário para criar a interface do usuário das guias.
1. Criar o aplicativo com JavaScript usando o kit de ferramentas do Teams.
1. Estender a funcionalidade adicionando mais recursos do Teams e dados do M365 com o Microsoft Graph.
1. Testar o aplicativo em um locatário de desenvolvedor com dados de usuário de exemplo.
1. Implantar o aplicativo no Azure.
1. Gerenciar e publicar os aplicativos na Microsoft Store com o Portal do Desenvolvedor. Monetize seu aplicativo com opções, como ofertas de SaaS, compras no aplicativo e muito mais.

## <a name="next-step"></a>Próxima etapa

:::row:::
    :::column span="1":::
        **Começar criar**
    :::column-end:::
    :::column span="2":::
        Familiarize-se rapidamente com a criação do Teams configurando seu ambiente e criando um aplicativo simples.

        > [!div class="nextstepaction"]
        > [Desenvolver seu primeiro aplicativo](get-started/get-started-overview.md)
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Confira também

:::row:::
    :::column span="1":::
        **Planejar seu aplicativo**
    :::column-end:::
    :::column span="2":::
        Entenda e mapeie os casos de uso do aplicativo para os recursos do Teams.

        > [!div class="nextstepaction"]
        > [Planejar seu aplicativo](~/concepts/app-fundamentals-overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Criar seu aplicativo**
    :::column-end:::
    :::column span="2":::
        Projete a interface do usuário do aplicativo com o kit de interface do usuário do Microsoft Teams.

        > [!div class="nextstepaction"]
        > [Design seu aplicativo do Teams](~/concepts/design/design-teams-app-process.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Criar seu aplicativo**
    :::column-end:::
    :::column span="2":::
        Procurando inspiração para o desenvolvimento de aplicativos? Navegue pela nossa lista de cenários reais e soluções do setor com simulações de conceito de alta fidelidade para entender as várias maneiras pelas quais um aplicativo Teams pode ajudar seus usuários.

        > [!div class="nextstepaction"]
        > [Ver cenários de aplicativo](https://adoption.microsoft.com/extensibility-look-book/scenarios/)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Estender seu aplicativo entre Microsoft 365**
    :::column-end:::
    :::column span="2":::
        Você pode visualizar seus aplicativos do Teams em execução em outras experiências de Microsoft 365 com o SDK do cliente JavaScript do Microsoft Teams v2 Preview.

        > [!div class="nextstepaction"]
        > [Extender seu aplicativo](m365-apps/overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Testar seu aplicativo**
    :::column-end:::
    :::column span="2":::
        Depois de integrar seu aplicativo como o Microsoft Teams, teste-o antes de publicá-lo.

        > [!div class="nextstepaction"]
        > [Testar seu aplicativo](concepts/build-and-test/test-app-overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Distribuir seu aplicativo**
    :::column-end:::
    :::column span="2":::
        Você pode fornecer seu aplicativo Microsoft Teams para um indivíduo, equipe, organização ou qualquer pessoa que queira usá-lo.

        > [!div class="nextstepaction"]
        > [Distribuir seu aplicativo](~/concepts/deploy-and-publish/apps-publish-overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Monetize seu aplicativo**
    :::column-end:::
    :::column span="2":::
        A repositório do Teams oferece opções de monetização de aplicativos, como ofertas de SaaS e compras no aplicativo. Escolha a melhor opção de monetização adequada para seu aplicativo Teams.

        > [!div class="nextstepaction"]
        > [Monetize seu aplicativo](concepts/deploy-and-publish/appsource/prepare/monetize-overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Integrar com o Teams**
    :::column-end:::
    :::column span="2":::
        Combine os recursos que os usuários adoram em um aplicativo Web, serviço ou sistema existente com os recursos colaborativos do Teams.

        > [!div class="nextstepaction"]
        > [Integrar um aplicativo existente](samples/integrating-web-apps.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Um código pequeno é muito longo**
    :::column-end:::
    :::column span="2":::
        Você não precisa ser um programador especialista para criar um ótimo aplicativo Teams. Experimente uma das várias soluções de pouco código.

        > [!div class="nextstepaction"]
        > [Criar um app de código-baixo](samples/teams-low-code-solutions.md)
    :::column-end:::
:::row-end:::
