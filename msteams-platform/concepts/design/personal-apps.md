---
title: Criar seu aplicativo pessoal
description: Saiba como implementar as diretrizes de design, incluindo elementos de interface do usuário para criar um aplicativo pessoal usando o kit de interface do usuário do Microsoft Teams.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: 4646d47c5aa325291f060ea192dcc1705b414ac7
ms.sourcegitcommit: bd96080c78f25eb0a67ce176df5e255be348f7b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2022
ms.locfileid: "68575781"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a>Projetando seu aplicativo pessoal para o Microsoft Teams

Um aplicativo pessoal pode ser um bot, um espaço de trabalho privado ou ambos. Às vezes, ele funciona como um local para criar ou exibir conteúdo. Outras vezes, ele oferece ao usuário uma visão geral de tudo o que é deles quando o aplicativo é configurado como uma guia em vários canais.

Para orientar o design do seu aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar aplicativos pessoais no Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de IU do Microsoft Teams

Você pode localizar diretrizes abrangentes de design de aplicativo pessoal, incluindo elementos que podem ser usados e modificados conforme necessário, no Kit de Interface do Usuário do Microsoft Teams. O kit de Interface do Usuário também possui tópicos essenciais, como acessibilidade e dimensionamento dinâmico, que não são abordados aqui.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a>Adicionar um aplicativo pessoal

Os usuários podem adicionar um aplicativo pessoal da loja do Teams ou do submenu do aplicativo selecionando o ícone **Mais** no lado esquerdo do Teams (mostrado no exemplo a seguir).

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="O exemplo mostra como adicionar um aplicativo pessoal a partir do submenu do aplicativo.":::

## <a name="use-a-personal-app-private-workspace"></a>Usar um aplicativo pessoal (espaço de trabalho privado)

Com um espaço de trabalho privado, os usuários podem exibir o conteúdo do aplicativo que é significativo para eles em um local central sem sair do Teams.

(Observação de implementação: o espaço de trabalho privado é baseado no recurso [*guia pessoal*](../../tabs/how-to/create-personal-tab.md).)

### <a name="anatomy-personal-app-private-workspace"></a>Anatomia: aplicativo pessoal (espaço de trabalho privado)

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-component-anatomy.png" alt-text="O exemplo mostra a anatomia do componente da guia pessoal.":::

|Contador|Descrição|
|----------|-----------|
|A|**Atribuição do aplicativo**: o nome do seu aplicativo.|
|B|**Guias**: fornece navegação para seu aplicativo pessoal.|
|C|**Menu Mais**: inclui outras opções e informações do aplicativo.|
|D|**Navegação principal**: fornece navegação para outros recursos principais do Teams em seu aplicativo.|

#### <a name="configure-and-add-multiple-actions-in-navbar"></a>**Configurar e adicionar várias ações no NavBar**

Você pode adicionar várias ações ao NavBar superior direito e criar um menu de estouro para ações extras em um aplicativo.

>[!NOTE]
> Um máximo de cinco ações pode ser adicionado no NavBar, incluindo o menu de estouro.

:::image type="content" source="../../assets/images/overflow-menu-and-multiple-actionsoptions.png" alt-text="A captura de tela é um exemplo que descreve o menu NavBar e Estouro.":::

Para **configurar e adicionar várias ações no NavBar**, chame [a API setNavBarMenu](/javascript/api/@microsoft/teams-js/microsoftteams.menus?view=msteams-client-js-1.12.1&preserve-view=true) . e adicione a `displayMode enum` propriedade a `MenuItem`. Define `displayMode enum` como um menu é exibido no NavBar. O valor padrão de `displayMode enum` é definido como `ifRoom`.

Com base nos requisitos e no espaço disponível no NavBar, defina `displayMode enum` considerando um dos seguintes itens.

* Se houver espaço, defina para `ifRoom = 0` colocar um item no NavBar.
* Se não houver espaço, `overflowOnly = 1`defina, para que esse item sempre seja colocado no menu de estouro do NavBar, mas não no NavBar.

A seguir está um exemplo de configuração do NavBar com um menu de estouro para várias ações:

```typescript
const menuItems = [item1, item2, item3, item4, item5]
microsoftTeams.menus.setNavBarMenu(menuItems, (id: string) => {
  output(`Clicked ${id}`)
  return true;
})
```

> [!NOTE]
> A `setNavBarMenu` API não controla o **botão Atualizar** . Ele é exibido por padrão.

:::image type="content" source="../../assets/images/overflow-menu-and-multple-actions.png" alt-text="A captura de tela é um exemplo que mostra a barra de navegação e várias ações em um menu de estouro.":::

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-structural-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural da guia pessoal.":::

|Contador|Descrição|
|----------|-----------|
|A|**Guias**: fornece navegação para seu aplicativo pessoal.|
|1|**Modo de exibição da Web**: exibe o conteúdo do aplicativo.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Este exemplo mostra a anatomia do componente da guia pessoal.":::

|Contador|Descrição|
|----------|-----------|
|A|**Atribuição do aplicativo**: o logotipo e o nome do seu aplicativo.|
|B|**Guias**: fornece navegação para seu aplicativo pessoal.|
|C|**Exibição de pop-up**: envia o conteúdo do seu aplicativo de uma janela principal para uma janela secundária independente.|
|D|**Menu Mais**: inclui outras opções e informações do aplicativo. (Você também pode transformar **Configurações** em uma guia.)|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Este exemplo mostra a anatomia estrutural da guia pessoal.":::

|Contador|Descrição|
|----------|-----------|
|A|**Guias**: fornece navegação para seu aplicativo pessoal.|
|1|**iframe**: exibe o conteúdo do aplicativo.|

### <a name="design-with-ui-templates-and-advanced-components"></a>Design com modelos de interface do usuário e componentes avançados

Use um dos seguintes modelos e componentes do Teams para ajudar a criar sua guia pessoal:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato que facilita a visualização e permite que os usuários executem ações em uma lista inteira ou itens individuais.
* [Painel de tarefas](../../concepts/design/design-teams-app-ui-templates.md#task-board): um painel de tarefas, às vezes chamado de quadro Kanban ou raias, é uma coleção de cartões frequentemente usados para acompanhar o status de itens de trabalho ou tíquetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou do conteúdo.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): os formulários são para coletar, validar e enviar a entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira execução, mensagens de erro, e muito mais.
* [Navegação esquerda](~/concepts/design/design-teams-app-advanced-ui-components.md#left-nav): o componente de navegação esquerda pode ajudar se seu aplicativo pessoal exigir alguma navegação. Em geral, você deve manter a navegação no mínimo.

## <a name="use-a-personal-app-bot"></a>Usar um aplicativo pessoal (bot)

Personal apps can include a bot for one-on-one conversations and private notifications (for instance, when a colleague posts a comment on artboard). Users interact with the bot in a tab you specify.

### <a name="anatomy-personal-app-bot"></a>Anatomia: aplicativo pessoal (bot)

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-bot-anatomy.png" alt-text="O exemplo mostra a anatomia do componente de bot pessoal.":::

|Contador|Descrição|
|----------|-----------|
|A|**Ponto de entrada de bot**: ponto de entrada para os usuários acessarem o recurso de bot em seu aplicativo pessoal.|
|B|**Botão Voltar**: leva os usuários de volta ao espaço de trabalho privado.|
|C|**Mensagem de bot**: os bots geralmente enviam mensagens e notificações na forma de um cartão (como um Cartão Adaptável).|
|D|**Caixa de composição**: campo de entrada para enviar mensagens ao bot.|

#### <a name="configure-back-button"></a>Botão Configurar Voltar

Ao selecionar o botão Voltar em um aplicativo do Teams, você retornará à plataforma teams sem navegar dentro do aplicativo.

Para navegar dentro do aplicativo, configure o botão Voltar para que, ao selecionar o botão Voltar, você possa voltar para as etapas anteriores e navegar dentro do aplicativo.

Para **configurar o botão Voltar**, chame a API [registerBackButtonHandler](/javascript/api/@microsoft/teams-js/pages.backstack?view=msteams-client-js-latest&preserve-view=true&branch=pr-en-us-6801&preserve-view=true) , que manipula a funcionalidade do botão Voltar, dependendo de uma das seguintes condições:

* Quando `registerBackButtonHandler` definido como , o `false`SDK `navigateBack` do JavaScript chama a API e a plataforma teams manipula o botão Voltar.
* Quando `registerBackButtonHandler` definido como `true`, o aplicativo lida com a funcionalidade do botão Voltar (você pode voltar para as etapas anteriores e navegar dentro do aplicativo), e a plataforma teams não executa nenhuma ação adicional.

A seguir está um exemplo de configuração do botão Voltar:

```typescript
microsoftTeams.registerBackButtonHandler(() => {
  const selectOption = registerBackReturn.options[registerBackReturn.selectedIndex].value
  var isHandled = false
  if (selectOption == 'true') 
    isHandled = true;
  output(`onBack isHandled ${isHandled}`)
  return isHandled;
})
```

#### <a name="desktop"></a>Área de trabalho

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="O exemplo mostra a anatomia do componente bot pessoal.":::

|Contador|Descrição|
|----------|-----------|
|A|**Guia Bot**: por exemplo, inclua uma guia **Chat** para acessar conversas e notificações de bot.|
|B|**Mensagem de bot**: os bots geralmente enviam mensagens e notificações na forma de um cartão (como um Cartão Adaptável).|
|C|**Caixa de composição**: campo de entrada para enviar mensagens ao bot.|

## <a name="manage-a-personal-tab"></a>Gerenciar uma guia pessoal

No lado esquerdo do Teams, os usuários podem clicar com o botão direito do mouse no aplicativo pessoal para fixar, remover e configurar outras opções do aplicativo.

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="O exemplo mostra opções para gerenciar um aplicativo pessoal.":::

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="tab-priority"></a>Prioridade de tabulação

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a>Fazer: mostrar o conteúdo mais relevante na primeira guia

Com o dimensionamento responsivo, as guias à direita podem ficar truncadas ou fora de exibição.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Exemplo mostra um aplicativo pessoal exibindo o conteúdo mais relevante na primeira guia.":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a>Não: lidere com conteúdo secundário ou metadados

Como um aplicativo Web padrão, a navegação por tabulação deve avançar em uma ordem que ajude a compreender os recursos principais dos aplicativos.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="Exemplo mostra um aplicativo pessoal à esquerda com conteúdo ou metadados secundários.":::

### <a name="tab-hierarchy"></a>Hierarquia de guias

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a>Fazer: as guias devem ser de hierarquia igual e representar páginas de aplicativos principais

Suas guias devem categorizar os principais recursos e conteúdo dos aplicativos. Com o dimensionamento responsivo, o conteúdo à direita pode ficar truncado ou fora de exibição.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="Exemplo mostra um aplicativo pessoal com guias de hierarquia igual.":::

#### <a name="dont-include-different-levels-of-hierarchy"></a>Não: incluir diferentes níveis de hierarquia

Seu conteúdo deve avançar em uma ordem lógica que ajude os usuários a fazer sentido dele. Se você tiver duas guias que estão intimamente relacionadas, considere combiná-las em uma guia.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="Exemplo mostra um aplicativo pessoal com diferentes níveis de hierarquia.":::

### <a name="first-run-experience"></a>Tela de apresentação

#### <a name="do-include-a-first-run-experience"></a>Incluir uma experiência de primeira execução

Deve haver pelo menos uma tela de boas-vindas na primeira vez que você usar um aplicativo pessoal. Para bots, descreva o que seu bot pode fazer e forneça ações rápidas, como um botão de entrada.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="Exemplo mostra o que fazer durante uma experiência de primeira execução de aplicativo pessoal.":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="Outro exemplo mostra o que fazer durante uma experiência de primeira execução de aplicativo pessoal.":::

#### <a name="dont-start-with-a-blank-screen"></a>Não: comece com uma tela em branco

Os usuários poderão ficar confusos se nada for exibido na primeira vez que executarem seu aplicativo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="Exemplo mostra o que não fazer durante uma experiência de primeira execução de aplicativo pessoal.":::

### <a name="personalized-content"></a>Conteúdo personalizado

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a>Fazer: agregar conteúdo do aplicativo relevante para um usuário

Seja uma guia pessoal ou um bot, exiba conteúdo relacionado apenas à atividade de um usuário em seu aplicativo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="Exemplo mostra o que fazer com um aplicativo pessoal e conteúdo personalizado.":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="Outro exemplo mostra o que fazer com um aplicativo pessoal e conteúdo personalizado.":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a>Não: mostrar conteúdo não relacionado ou muito amplo

Em contextos pessoais, não exiba conteúdo para equipes das quais um usuário não faz parte. O conteúdo do bot pessoal deve se concentrar no indivíduo—, não em um grupo.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="Exemplo mostra o que não fazer com um aplicativo pessoal e conteúdo personalizado.":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="Outro exemplo mostra o que não fazer com um aplicativo pessoal e conteúdo personalizado.":::

### <a name="complex-app-features"></a>Recursos complexos do aplicativo

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a>Fazer: permitir que os usuários acessem recursos complexos em um navegador

Seu aplicativo deve se concentrar nas principais tarefas no Teams, mas você ainda pode exibir o aplicativo autônomo completo em um navegador.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="Exemplo mostra como lidar com recursos complexos de aplicativo com um aplicativo pessoal.":::

#### <a name="dont-include-your-entire-app"></a>Não: inclua todo o seu aplicativo

A menos que tenha criado seu aplicativo especificamente para o Teams, você provavelmente tem recursos que não fazem sentido em uma ferramenta de colaboração.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="Exemplo mostra como não lidar com recursos complexos de aplicativo com um aplicativo pessoal.":::

## <a name="see-also"></a>Confira também

Essas outras diretrizes de design podem ajudar dependendo do escopo do seu aplicativo pessoal:

* [Criando sua guia](../../tabs/design/tabs.md)
* [Criar um bot](../../bots/design/bots.md)
* [registerBackButtonHandler](/javascript/api/@microsoft/teams-js/pages.backstack?view=msteams-client-js-latest&preserve-view=true&branch=pr-en-us-6801&preserve-view=true)
* [Enumeração DisplayMode](/javascript/api/@microsoft/teams-js/menus.displaymode?view=msteams-client-js-latest&preserve-view=true)
