---
title: Projetando seu aplicativo com modelos de interface do usuário
author: heath-hamilton
description: Projete seu aplicativo mais rapidamente com componentes de Interface do Usuário padronizados, layouts e padrões comumente vistos em Microsoft Teams.
ms.author: lajanuar
localization_priority: Normal
ms.topic: reference
ms.openlocfilehash: 0cd5c6c4525e340f9aa53a78749211783880225a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566016"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a>Projetando seu aplicativo de Microsoft Teams com modelos de interface do usuário

Projete seu aplicativo Microsoft Teams mais rápido com modelos de interface do usuário. Os modelos são uma coleção de componentes baseados em Interface do Usuário Fluentes que funcionam em casos comuns de uso Teams, dando-lhe mais tempo para descobrir a melhor experiência para seus usuários.

## <a name="getting-started-with-tools-and-samples"></a>Começando com ferramentas e amostras

Os seguintes recursos podem ajudá-lo a projetar e desenvolver seu aplicativo usando modelos de interface do usuário.

### <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Pegue modelos de interface do usuário para o design do seu aplicativo a partir do Microsoft Teams UI Kit, que também inclui informações extensas sobre uso, anatomia, acessibilidade e práticas recomendadas.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário (Figma)](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a>Microsoft Teams Biblioteca de Interface do Usuário

Exibir e testar modelos de interface do usuário individuais Teams e componentes relacionados no seu navegador.

> [!div class="nextstepaction"]
> [Experimente a biblioteca de interface do usuário (playground)](https://dev-int.teams.microsoft.com/storybook/main/index.html)

Importe esses modelos e componentes relacionados diretamente no seu projeto de aplicativo Teams.

> [!div class="nextstepaction"]
> [Obtenha a biblioteca de interface do usuário (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a>Aplicativo de amostra

Instale um aplicativo de exemplo para ver como os modelos de interface do usuário parecem e se comportam dentro de Teams contextos.

> [!div class="nextstepaction"]
> [Obtenha o aplicativo de amostra (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="list"></a>List

Você pode usar uma lista para exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="O exemplo mostra um modelo de interface do usuário da lista." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Exibir dados
* Ações contextuais sobre conteúdo de aplicativos

## <a name="dashboard"></a>Painel

Um painel exibe diferentes tipos de conteúdo em um local central (Teams aplicativo ou guia pessoal). Os usuários devem ser capazes de personalizar pelo menos um pouco do que vêem em um painel.

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="O exemplo mostra um modelo de interface do usuário do painel." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Analisar dados
* Métricas de relatório
* Organize diferentes informações em um só lugar

## <a name="form"></a>Formulário

Os formulários são usados para coletar, validar e enviar a entrada do usuário de forma estruturada. Rotulagem clara e agrupamentos lógicos de campos de entrada são fundamentais para uma boa experiência do usuário.

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="O exemplo mostra um modelo de interface do usuário de formulário." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Entrar
* Perfis de usuário
* Configurações
* Coleta de entrada do usuário

## <a name="sign-in"></a>Entrar

Você pode projetar fluxos de login de aplicativos para diferentes Teams contextos e provedores de identidade. O exemplo a seguir inclui o single sign-on (SSO), que recomendamos para a experiência de autenticação mais simples.

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="O exemplo mostra um sinal no modelo de interface do usuário." border="false":::

### <a name="top-use-case"></a>Caso de uso superior

* Autenticar usuários

## <a name="task-board"></a>Quadro de tarefas

Um quadro de tarefas, às vezes chamado de placa kanban ou pistas de natação, é uma coleção de cartões frequentemente usados para rastrear o status de itens de trabalho ou bilhetes. Ele também pode ser usado para classificar qualquer tipo de conteúdo em categorias. Você pode editar e mover as cartas entre as colunas.

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="O exemplo mostra um modelo de interface do usuário da placa de tarefas." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* gerenciamento de Project: Atribuindo tarefas e status de rastreamento.
* Brainstorming: Adicionando ideias em diferentes categorias.
* Exercícios de triagem: Organizando qualquer tipo de informação em baldes.

## <a name="data-visualization"></a>Visualização de dados

Você pode usar diferentes tamanhos de cartão (simples, duplo e completo) para empilhar e organizar visualizações de dados na mesma página. A escala de cartões para se encaixar no layout da coluna e preencher espaços em branco.

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="O exemplo mostra um modelo de interface do usuário de visualização de dados." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Exibir informações complexas
* Crie um painel de instrumentos

## <a name="wizard"></a>Assistente

Um assistente guia um usuário através de várias telas para completar uma tarefa (como um processo de configuração).

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="O exemplo mostra um modelo de interface do usuário do assistente." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Configurar
* Integração
* Experiências de primeira viagem

## <a name="empty-state"></a>Estado vazio

O modelo de estado vazio pode ser usado para muitos cenários, incluindo login, experiências de primeira execução, mensagens de erro e muito mais. É altamente flexível — adaptá-lo para usar um, alguns ou todos os componentes no design a seguir.

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="O exemplo mostra um modelo de interface do usuário de estado vazio." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Entrar
* Mensagens de boas-vindas e experiências de primeira viagem
* Mensagens de sucesso
* Mensagens de erro

## <a name="notification-bar"></a>Notification bar

Uma barra de notificação é uma área dedicada para exibir uma mensagem breve e importante que não exige que o usuário tome medidas imediatas. Cores e ícones de fundo específicos estão associados a tipos específicos de mensagens (veja abaixo).

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="O exemplo mostra modelos de barras de notificação." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Mensagens críticas, erros e avisos
* Mensagens de sucesso
* Mensagens informacionais ou promocionais

## <a name="left-nav"></a>Navegação esquerda

Use a navegação à esquerda para navegar em várias páginas na guia Teams. No exemplo a seguir, a navegação à esquerda está entre a lista de canais e o conteúdo da guia.

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="O exemplo mostra um modelo de navegação à esquerda." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Navegue por várias páginas em uma guia Teams.
* Desbre aplicativos complexos em várias páginas.

## <a name="breadcrumb"></a>Trilha

Migalhas de pão são um auxílio de navegação que transmite a hierarquia do seu aplicativo. Eles ajudam os usuários a entender como a página que estão visualizando se encaixa na experiência geral e oferecem acesso de um clique a níveis mais altos nessa hierarquia.

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="O exemplo mostra um modelo de migalhas de pão." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Comunicar hierarquia
* Navegação

## <a name="toolbar"></a>Barra de ferramentas

Uma barra de ferramentas é um recipiente para agrupar um conjunto de controles.

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="O exemplo mostra um modelo de barra de ferramentas." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Ações contextuais sobre conteúdo de aplicativos
* Filtro contextual e encontrar
* Navegação e migalhas de pão

## <a name="stage"></a>Estágio

O Stage oferece uma maneira de os usuários abrirem uma entidade — como uma imagem, arquivo ou site — em Teams em vez de abri-la em outro aplicativo ou navegador. O principal caso de uso do estágio é a visualização; a superfície não deve ser usada para interações complexas.

(Nota de implementação: Construa seu estágio usando um grande [módulo de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).)

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="O exemplo mostra um modelo de palco." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Abra uma entidade em Teams em vez de outro aplicativo ou navegador.
* Mídia de holofotes ou outros conteúdos.
