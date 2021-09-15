---
title: Criar seu aplicativo pessoal
description: Saiba como projetar um aplicativo Teams pessoal e obter o kit Microsoft Teams interface do usuário.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: 2f55661c7941422eb4067023eed46b05d1b757ea
ms.sourcegitcommit: 72de146d11e81fd9777374dd3915ad290fd07d82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59360715"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a>Projetar seu aplicativo pessoal para Microsoft Teams

Um aplicativo pessoal pode ser um bot, um espaço de trabalho privado ou ambos. Às vezes, funciona como um local para criar ou exibir conteúdo, outras vezes oferece ao usuário uma visão visual de tudo o que é deles quando o aplicativo foi configurado como uma guia em vários canais.

Para orientar o design do aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar aplicativos pessoais Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de IU do Microsoft Teams

Você pode encontrar diretrizes abrangentes de design de aplicativo pessoal, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit de interface do usuário Microsoft Teams usuário. O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e tamanho responsivo que não são abordados aqui.

> [!div class="nextstepaction"]
> [Obtenha o Kit de IU do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a>Adicionar um aplicativo pessoal

Os usuários podem adicionar um aplicativo pessoal do Teams ou do flyout do aplicativo selecionando o ícone **Mais** no lado esquerdo do Teams (mostrado no exemplo a seguir).

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="Exemplo mostra como adicionar um aplicativo pessoal do flyout do aplicativo." border="false":::

## <a name="use-a-personal-app-private-workspace"></a>Usar um aplicativo pessoal (espaço de trabalho privado)

Com um espaço de trabalho privado, os usuários podem exibir conteúdo de aplicativo que seja significativo para eles em um local central sem sair Teams.

(Observação de implementação: o espaço de trabalho privado é baseado no [*recurso de guia*](../../build-your-first-app/build-personal-tab.md) pessoal.)

### <a name="anatomy-personal-app-private-workspace"></a>Anatomia: aplicativo pessoal (espaço de trabalho privado)

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-component-anatomy.png" alt-text="Exemplo mostra a anatomia do componente da guia pessoal." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Atribuição de aplicativo**: Seu nome do aplicativo.|
|B|**Guias**: fornece navegação para seu aplicativo pessoal.|
|C|**Mais menu**: inclui opções e informações adicionais do aplicativo.|
|D|**Navegação primária**: fornece navegação para seu aplicativo outros recursos Teams principais.|

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-structural-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural da guia pessoal." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Guias**: fornece navegação para seu aplicativo pessoal.|
|1|**webview**: exibe o conteúdo do aplicativo.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Este exemplo mostra a anatomia do componente da guia pessoal." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Atribuição do aplicativo**: o logotipo e o nome do aplicativo.|
|B|**Guias**: fornece navegação para seu aplicativo pessoal.|
|C|**Exibição pop-out**: empurra o conteúdo do aplicativo de uma janela pai para uma janela filha autônoma.|
|D|**Mais menu**: inclui opções e informações adicionais do aplicativo. (Você poderia, alternativamente, **Configurações** uma guia.)|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Este exemplo mostra a anatomia estrutural da guia pessoal." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Guias**: fornece navegação para seu aplicativo pessoal.|
|1|**iframe**: exibe o conteúdo do aplicativo.|

### <a name="design-with-ui-templates-and-advanced-components"></a>Projetar com modelos de interface do usuário e componentes avançados

Use um dos seguintes Teams e componentes para ajudar a projetar sua guia pessoal:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.
* [Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : um quadro de tarefas, às vezes chamado de quadro kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou conteúdo.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.
* [Navegação à esquerda](~/concepts/design/design-teams-app-advanced-ui-components.md#left-nav): O componente de navegação esquerdo pode ajudar se seu aplicativo pessoal exigir alguma navegação. Em geral, você deve manter a navegação no mínimo.

## <a name="use-a-personal-app-bot"></a>Usar um aplicativo pessoal (bot)

Os aplicativos pessoais podem incluir um bot para conversas um-a-um e notificações privadas (por exemplo, quando um colega posta um comentário na área de trabalho). Os usuários interagem com o bot em uma guia especificada.

### <a name="anatomy-personal-app-bot"></a>Anatomia: aplicativo pessoal (bot)

#### <a name="mobile"></a>Dispositivo móvel

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-bot-anatomy.png" alt-text="Exemplo mostra a anatomia do componente de bot pessoal." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Ponto de entrada do bot**: Ponto de entrada para os usuários acessarem o recurso bot em seu aplicativo pessoal.|
|B|**Botão Voltar**: leva os usuários de volta para o espaço de trabalho privado.|
|C|**Mensagem bot**: os bots geralmente enviam mensagens e notificações na forma de um cartão (como um Cartão Adaptável).|
|D|**Caixa de redação**: Campo de entrada para envio de mensagens para o bot.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="Exemplo mostra a anatomia do componente de bot pessoal." border="false":::

|Contador|Descrição|
|----------|-----------|
|A|**Guia Bot**: Por exemplo, inclua uma guia **Chat** para acessar as conversas de bot e notificações.|
|B|**Mensagem bot**: os bots geralmente enviam mensagens e notificações na forma de um cartão (como um Cartão Adaptável).|
|C|**Caixa de redação**: Campo de entrada para envio de mensagens para o bot.|

## <a name="manage-a-personal-tab"></a>Gerenciar uma guia pessoal

No lado esquerdo do Teams, os usuários podem clicar com o botão direito do mouse no aplicativo pessoal para fixar, remover e configurar outras opções de aplicativo.

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="Exemplo mostra opções para gerenciar um aplicativo pessoal." border="false":::

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="tab-priority"></a>Prioridade de tabulação

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a>Do: Mostrar o conteúdo mais relevante na primeira guia

Com o ressamento responsivo, as guias à direita podem ficar truncadas ou fora de exibição.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Exemplo mostra um aplicativo pessoal exibindo o conteúdo mais relevante na primeira guia." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a>Não: Levar com conteúdo ou metadados secundários

Como um aplicativo Web padrão, a navegação por tabulação deve progredir em uma ordem que ajude a entender os principais recursos do aplicativo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="Exemplo mostra um aplicativo pessoal à frente com conteúdo ou metadados secundários." border="false":::

### <a name="tab-hierarchy"></a>Hierarquia de guias

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a>Do: As guias devem ser de hierarquia igual e representar páginas principais do aplicativo

Suas guias devem categorizar os principais recursos e conteúdo do aplicativo. Com o ressamento responsivo, o conteúdo à direita pode ficar truncado ou fora de exibição.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="Exemplo mostra um aplicativo pessoal com guias de hierarquia igual." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a>Não: inclua diferentes níveis de hierarquia

Seu conteúdo deve progredir em uma ordem lógica que ajude os usuários a entender isso. Se você tiver duas guias intimamente relacionadas, considere combiná-las em uma guia.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="Exemplo mostra um aplicativo pessoal com diferentes níveis de hierarquia." border="false":::

### <a name="first-run-experience"></a>Tela de apresentação

#### <a name="do-include-a-first-run-experience"></a>Do: Incluir uma experiência de primeira executar

Deve haver pelo menos uma tela de boas-vindas na primeira vez que você usar um aplicativo pessoal. Para bots, descreva o que seu bot pode fazer e forneça ações rápidas, como um botão de login.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="Exemplo mostra o que fazer durante uma experiência de primeira executar um aplicativo pessoal." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="Outro exemplo mostra o que fazer durante uma experiência de primeira executar um aplicativo pessoal." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a>Não: Comece com uma tela em branco

Os usuários podem ficar confusos se nada for exibido na primeira vez em que executarem seu aplicativo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="Exemplo mostra o que não fazer durante uma experiência de primeira executar um aplicativo pessoal." border="false":::

### <a name="personalized-content"></a>Conteúdo personalizado

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a>Do: Agregar conteúdo de aplicativo relevante para um usuário

Seja uma guia pessoal ou bot, exibe conteúdo relacionado apenas à atividade de um usuário em seu aplicativo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="Exemplo mostra o que fazer com um aplicativo pessoal e conteúdo personalizado." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="Outro exemplo mostra o que fazer com um aplicativo pessoal e conteúdo personalizado." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a>Não: mostrar conteúdo não relacionado ou muito amplo

Em contextos pessoais, não exibir conteúdo para equipes da qual um usuário não faz parte. O conteúdo do bot pessoal deve se concentrar no indivíduo, não em um grupo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="Exemplo mostra o que não fazer com um aplicativo pessoal e conteúdo personalizado." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="Outro exemplo mostra o que não fazer com um aplicativo pessoal e conteúdo personalizado." border="false":::

### <a name="complex-app-features"></a>Recursos complexos do aplicativo

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a>Fazer: permitir que os usuários acessem recursos complexos em um navegador

Seu aplicativo deve se concentrar nas tarefas principais no Teams, mas você ainda pode exibir o aplicativo completo e autônomo em um navegador.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="Exemplo mostra como lidar com recursos complexos de aplicativo com um aplicativo pessoal." border="false":::

#### <a name="dont-include-your-entire-app"></a>Não: inclua seu aplicativo inteiro

A menos que você tenha criado seu aplicativo especificamente para Teams, você provavelmente terá recursos que não fazem sentido em uma ferramenta de colaboração.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="Exemplo mostra como não manipular recursos complexos do aplicativo com um aplicativo pessoal." border="false":::

## <a name="see-also"></a>Confira também

Essas outras diretrizes de design podem ajudar, dependendo do escopo do seu aplicativo pessoal:

* [Projetando sua guia](../../tabs/design/tabs.md)
* [Projetando um bot](../../bots/design/bots.md)
