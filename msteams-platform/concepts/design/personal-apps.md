---
title: Criando seu aplicativo pessoal
description: Saiba como criar um aplicativo pessoal do Teams e obter o kit de interface do usuário do Microsoft Teams.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 971071be9f345815f5461646d7970efdf05fd5c4
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604959"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a>Projetando seu aplicativo pessoal para o Microsoft Teams

Um aplicativo pessoal pode ser um bot, um espaço de trabalho privado ou ambos. Às vezes, ele funciona como um local para criar ou exibir o conteúdo, outras vezes, ele oferece ao usuário uma visão geral de todos os itens que são seus, quando o aplicativo é configurado como uma guia em vários canais.

Para guiar o design do aplicativo, as informações a seguir descrevem e ilustra como as pessoas podem adicionar, usar e gerenciar aplicativos pessoais no Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de interface do usuário do Microsoft Teams

Você pode encontrar diretrizes abrangentes de design de aplicativo pessoal, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams. O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e dimensionamento responsivo que não são abordados aqui.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário do Microsoft Teams (figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a>Adicionar um aplicativo pessoal

Você pode adicionar um aplicativo pessoal do repositório do Teams (AppSource) ou o submenu do aplicativo selecionando o ícone **mais** no lado esquerdo do Teams (mostrado no exemplo a seguir).

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="O exemplo mostra como adicionar um aplicativo pessoal do submenu de aplicativo." border="false":::

## <a name="use-a-personal-app-private-workspace"></a>Usar um aplicativo pessoal (espaço de trabalho privado)

Com um espaço de trabalho privado, você pode visualizar o conteúdo do aplicativo que é significativo para você em um local central sem sair do Microsoft Teams.

(Observação de implementação: o espaço de trabalho privado baseia-se no recurso de [*Tabulação pessoal*](../../build-your-first-app/build-personal-tab.md) .)

### <a name="anatomy-personal-app-private-workspace"></a>Anatomia: aplicativo pessoal (espaço de trabalho privado)

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="O exemplo mostra a anatomia do componente da guia pessoal." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Atribuição de aplicativos**: o logotipo e o nome do aplicativo.|
|B|**Guias**: fornece navegação para seu aplicativo pessoal. Por exemplo, inclua uma guia **sobre** ou **ajuda** .|
|C|**Pop-up View**: envia o conteúdo do aplicativo de uma janela pai para uma janela filho autônoma.|
|D|**Mais menu**: inclui informações e opções adicionais do aplicativo. (Você poderia, opcionalmente, fazer **configurações** uma guia.)|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural da guia pessoal." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Guias**: fornece navegação para seu aplicativo pessoal.|
|1 |**iframe**: exibe o conteúdo do aplicativo.|

### <a name="designing-with-ui-templates"></a>Projetando com modelos de interface do usuário

Use um dos seguintes modelos de interface do usuário do Microsoft Teams para ajudar a criar sua guia pessoal:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato verificável e permitir que os usuários executem ações em uma lista inteira ou em itens individuais.
* [Quadro de tarefas](../../concepts/design/design-teams-app-ui-templates.md#task-board): um quadro de tarefas, às vezes chamado de um quadro Kanban ou uma pista de baixo, é uma coleção de cartões usados para acompanhar o status de itens de trabalho ou tíquetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela contendo vários cartões que oferecem uma visão geral de dados ou conteúdo.
* [Form](../../concepts/design/design-teams-app-ui-templates.md#form): formulários são para coletar, validar e enviar entradas do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para vários cenários, incluindo o login, experiências de tela de apresentação, mensagens de erro e muito mais.
* [NAV à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): o modelo de navegação à esquerda pode ajudar se sua guia requer alguma navegação. Em geral, você deve manter a navegação de guia no mínimo.

## <a name="use-a-personal-app-bot"></a>Usar um aplicativo pessoal (bot)

Os aplicativos pessoais podem incluir um bot para conversas de uma em um e notificações privadas (por exemplo, quando um colega posta um comentário na sua prancheta). O bot está disponível em uma guia que você especificar.

### <a name="anatomy-personal-app-bot"></a>Anatomia: aplicativo pessoal (bot)

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="O exemplo mostra a anatomia do componente de bot pessoal." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Guia bot**: por exemplo, inclua uma guia **chat** para acessar conversas e notificações de bot.|
|B|**Mensagem de bot**: os bots geralmente enviam mensagens e notificações na forma de um cartão (como um cartão adaptável).|
|C|**Caixa de composição**: campo de entrada para envio de mensagens ao bot.|

## <a name="best-practices"></a>Práticas recomendadas

### <a name="tab-priority"></a>Prioridade de tabulação

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a>Fazer: mostrar o conteúdo mais relevante na primeira guia

Com o dimensionamento responsivo, as guias à direita podem ficar truncadas ou fora de visão.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a>Não: liderança com conteúdo secundário ou metadados

Como um aplicativo Web padrão, a navegação de guia deve progredir em uma ordem que ajuda a fazer sentido dos principais recursos do aplicativo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

### <a name="tab-hierarchy"></a>Hierarquia de guias

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a>Fazer: as guias devem ser de hierarquia igual e representar páginas de aplicativo de chave

Suas guias devem categorizar os principais recursos e conteúdo do aplicativo. Com o dimensionamento responsivo, o conteúdo à direita pode ficar truncado ou fora do modo de exibição.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a>Não: incluir níveis diferentes de hierarquia

O conteúdo deve progredir em uma ordem lógica que ajude os usuários a fazer sentido. Se você tiver duas guias que estão intimamente relacionadas, considere combiná-las em uma guia.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

### <a name="first-run-experience"></a>Tela de apresentação

#### <a name="do-include-a-first-run-experience"></a>Fazer: incluir uma experiência de primeira execução

Deve haver pelo menos uma tela de boas-vindas na primeira vez que você usa um aplicativo pessoal. Para bots, descreva o que seu bot pode fazer e forneça ações rápidas, como um botão de entrada.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a>Não: começar com uma tela em branco

Os usuários podem ser confundidos se nada é exibido na primeira vez que executam o aplicativo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

### <a name="personalized-content"></a>Conteúdo personalizado

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a>Fazer: agregar o conteúdo do aplicativo relevante a um usuário

Seja uma guia ou um bot pessoal, exiba o conteúdo relacionado à atividade de um usuário em seu aplicativo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a>Não: Mostrar conteúdo abrangente ou muito amplo

Em contextos pessoais, não exibe conteúdo para equipes que um usuário não faz parte do. O conteúdo do bot pessoal deve se concentrar na pessoa, não em um grupo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

### <a name="complex-app-features"></a>Recursos de aplicativos complexos

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a>Fazer: permitir que os usuários acessem recursos complexos em um navegador

Seu aplicativo deve se concentrar nas tarefas principais no Teams, mas você ainda pode exibir o aplicativo completo autônomo em um navegador.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

#### <a name="dont-include-your-entire-app"></a>Não: inclua todo o aplicativo

A menos que você tenha criado o aplicativo especificamente para o Teams, provavelmente tem recursos que não fazem sentido em uma ferramenta de colaboração.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

## <a name="manage-a-personal-tab"></a>Gerenciar uma guia pessoal

No lado esquerdo do Teams, os usuários podem clicar com o botão direito do mouse no aplicativo pessoal para fixar, remover e configurar outras opções de aplicativos.

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="O exemplo mostra opções para gerenciar um aplicativo pessoal." border="false":::

## <a name="learn-more"></a>Saiba mais

Essas outras diretrizes de design podem ajudar dependendo do escopo do seu aplicativo pessoal:

* [Criar sua guia](../../tabs/design/tabs.md)
* [Projetando o bot](../../bots/design/bots.md)

## <a name="validate-your-design"></a>Validar o design

Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.

> [!div class="nextstepaction"]
> [Verificar diretrizes de validação de design](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
