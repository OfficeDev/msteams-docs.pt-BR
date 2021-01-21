---
title: Projetando seu aplicativo com modelos de interface do usuário
author: heath-hamilton
description: Projete seu aplicativo mais rapidamente com componentes, layouts e padrões padronizados da interface do usuário geralmente vistos no Microsoft Teams.
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: b4d244bbf78ac85042d5caf8ec84afe42e79b3c7
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911923"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a>Projetando seu aplicativo Microsoft Teams com modelos de interface do usuário

Projete seu aplicativo Microsoft Teams mais rapidamente com modelos de interface do usuário. Os modelos são um conjunto de componentes baseados na interface do usuário fluente que funcionam em casos de uso comuns do Teams, dando mais tempo para você descobrir a melhor experiência para seus usuários.

## <a name="getting-started-with-tools-and-samples"></a>Getting started with tools and samples

Os recursos a seguir podem ajudá-lo a projetar e desenvolver seu aplicativo usando modelos de interface do usuário.

### <a name="microsoft-teams-ui-kit"></a>Kit de interface do usuário do Microsoft Teams

Pegue modelos de interface do usuário para seu design de aplicativo do Kit de Interface do Usuário do Microsoft Teams, que também inclui informações abrangentes sobre uso, anatomia, acessibilidade e práticas recomendadas.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário (Ltdma)](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a>Biblioteca de interface do usuário do Microsoft Teams

Exibir e testar modelos de interface do usuário individuais do Teams e componentes relacionados em seu navegador.

> [!div class="nextstepaction"]
> [Experimente a biblioteca de interface do usuário (playground)](https://dev-int.teams.microsoft.com/storybook/main/index.html)

Importe esses modelos e componentes relacionados diretamente para seu projeto de aplicativo do Teams.

> [!div class="nextstepaction"]
> [Obter a biblioteca de interface do usuário (GitHub)](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a>Aplicativo de exemplo

Instale um aplicativo de exemplo para ver a aparência e o comportamento dos modelos de interface do usuário nos contextos do Teams.

> [!div class="nextstepaction"]
> [Obter o aplicativo de exemplo (GitHub)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="list"></a>Listar

Você pode usar uma lista para exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="O exemplo mostra um modelo de interface do usuário de lista." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Exibir dados
* Ações contextuais no conteúdo do aplicativo

## <a name="dashboard"></a>Painel

Um painel exibe diferentes tipos de conteúdo em um local central (aplicativo pessoal ou guia do Teams). Os usuários devem ser capazes de personalizar pelo menos parte do que veem em um painel.

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="O exemplo mostra um modelo de interface do usuário do painel." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Analisar dados
* Métricas de relatório
* Organizar informações diferentes em um só lugar

## <a name="form"></a>Formulário

Os formulários são usados para coletar, validar e enviar entradas do usuário de maneira estruturada. Limpar a rotulagem e os agrupamentos lógicos dos campos de entrada são fundamentais para uma boa experiência do usuário.

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="O exemplo mostra um modelo de interface do usuário do formulário." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Entrar
* Perfis de usuário
* Configurações
* Coleção de entrada do usuário

## <a name="sign-in"></a>Entrar

Você pode projetar fluxos de entrada do aplicativo para diferentes contextos e provedores de identidade do Teams. O exemplo a seguir inclui o SSO (logo único), que recomendamos para a experiência de autenticação mais simples.

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="O exemplo mostra um modelo de interface do usuário de login." border="false":::

### <a name="top-use-case"></a>Principais casos de uso

* Autenticar usuários

## <a name="task-board"></a>Quadro de tarefas

Um quadro de tarefas, às vezes chamado de tabuleiro kanban ou trilhos de mesa, é uma coleção de cartões frequentemente usada para acompanhar o status de itens de trabalho ou tíquetes. Ele também pode ser usado para classificar qualquer tipo de conteúdo em categorias. Você pode editar e mover os cartões entre colunas.

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="O exemplo mostra um modelo de interface do usuário do quadro de tarefas." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Gerenciamento de projetos. Atribuindo tarefas e status de controle
* Brainstorming. Adicionando ideias em categorias diferentes
* Classificar exercícios. Organizando qualquer tipo de informação em buckets

## <a name="data-visualization"></a>Visualização de dados

Você pode usar tamanhos de cartão diferentes (único, duplo e completo) para empilhar e organizar visualizações de dados na mesma página. Os cartões são dimensionados para caber no layout de coluna e preencher espaços em branco.

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="Exemplo mostra um modelo de interface do usuário de visualização de dados." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Exibir informações complexas
* Criar um painel

## <a name="wizard"></a>Assistente

Um assistente orienta um usuário em várias telas para concluir uma tarefa (como um processo de configuração).

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="O exemplo mostra um modelo de interface do usuário do assistente." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Configurar
* Integração
* Experiências de primeira vez

## <a name="empty-state"></a>Estado vazio

O modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais. É altamente flexível : adapte-o para usar um, alguns ou todos os componentes no design a seguir.

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="O exemplo mostra um modelo de interface do usuário de estado vazio." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Entrar
* Mensagens de boas-vindas e experiências de primeira vez
* Mensagens de sucesso
* Mensagens de erro

## <a name="notification-bar"></a>Notification bar

Uma barra de notificação é uma área dedicada para exibir mensagens breves e importantes que não exigem que o usuário tome medidas imediatas. Cores de plano de fundo e ícones específicos estão associados a tipos específicos de mensagens (veja abaixo).

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="Exemplo mostra modelos de barra de notificação." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Mensagens críticas, erros e avisos
* Mensagens de sucesso
* Mensagens informativas ou promocionais

## <a name="left-nav"></a>Nav à esquerda

Use a navegação à esquerda para navegar em várias páginas na guia do Teams. No exemplo a seguir, a navegação à esquerda fica entre a lista de canais e o conteúdo da guia.

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="O exemplo mostra um modelo de nav à esquerda." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Procurar várias páginas em uma guia do Teams
* Separar aplicativos complexos em várias páginas

## <a name="breadcrumb"></a>Navegação estrutural

As navegação são um auxílio de navegação que transmite a hierarquia do seu aplicativo. Eles ajudam os usuários a entender como a página que estão exibindo se encaixa na experiência geral e têm acesso de um clique para níveis mais altos nessa hierarquia.

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="O exemplo mostra um modelo de breadcrumb." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Comunicar hierarquia
* Navegação

## <a name="toolbar"></a>Barra de ferramentas

Uma barra de ferramentas é um contêiner para agrupar um conjunto de controles.

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="O exemplo mostra um modelo de barra de ferramentas." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Ações contextuais no conteúdo do aplicativo
* Filtro contextual e encontrar
* Navegação e navegação

## <a name="stage"></a>Etapa

O estágio oferece uma maneira para os usuários abrirem uma entidade, como uma imagem, arquivo ou site, no Teams, em vez de abri-la em outro aplicativo ou navegador. O principal caso de uso do estágio é exibição; a superfície não deve ser usada para interações complexas.

(Observação de implementação: crie seu estágio usando um módulo [de tarefa grande.)](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="O exemplo mostra um modelo de estágio." border="false":::

### <a name="top-use-cases"></a>Principais casos de uso

* Abrir uma entidade no Teams em vez de outro aplicativo ou navegador
* Mídia de destaque ou outro conteúdo
