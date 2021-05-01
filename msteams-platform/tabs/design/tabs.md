---
title: Projetando sua guia para área de trabalho e Web
description: Saiba como projetar uma guia Teams (área de trabalho e Web) e obter o Microsoft Teams de interface do usuário.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 9dc5489f4a6a4c6f0e1188250a9e2a9bc5793690
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101846"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a>Projetando sua guia para Microsoft Teams desktop e web

Uma guia é uma tela grande para seu conteúdo. Para orientar o design do aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar guias no Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Você pode encontrar diretrizes abrangentes de design de guia, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit Microsoft Teams interface do usuário. O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e tamanho responsivo que não são abordados aqui.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a>Adicionar uma guia

Você pode adicionar uma guia do Teams (AppSource) ou em um dos seguintes contextos:

* Chat
* Canal
* Reunião (antes, durante ou após a reunião)

O exemplo a seguir mostra como uma guia é adicionada a um canal.

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Exemplo mostra uma guia sendo adicionada a um canal." border="false":::

## <a name="set-up-a-tab"></a>Configurar uma guia

Há um curto processo de instalação para adicionar um aplicativo como canal, chat ou guia de reunião. A experiência é em grande parte com você. Por exemplo, você pode ter uma descrição de como usar o aplicativo e algumas configurações opcionais. Inclua uma etapa de login aqui se você precisar autenticar usuários.

### <a name="tab-configuration-modal"></a>Modal de configuração de tabulação

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Exemplo mostra um modal de configuração de tabulação." border="false":::

### <a name="anatomy-tab-configuration-modal"></a>Anatomia: modal de configuração de tabulação

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um modal de configuração de tabulação." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Logotipo do aplicativo**: logotipo completo do aplicativo de cores do seu aplicativo.|
|2|**Nome do** aplicativo : Nome completo do seu aplicativo.|
|3|**iframe**: espaço responsivo para o conteúdo do aplicativo (por exemplo, configurações de tabulação ou autenticação).|
|4 |**Sobre o link**: abre uma caixa de diálogo mostrando mais informações sobre o aplicativo, como uma descrição completa, permissões exigidas pelo aplicativo e links para sua política de privacidade e termos de serviço.
|5 |**Botão Fechar**: fecha o modal.|
|6 |**Opção Notificar membros da** equipe : O modal pergunta se você deseja criar uma postagem informando que você adicionou uma guia.|
|7 |**Botão Voltar**: vai para a etapa anterior com base em onde a caixa de diálogo foi aberta.|
|8 |**Botão Salvar**: Conclui a configuração da guia.|

### <a name="tab-authentication-with-single-sign-on"></a>Autenticação de tabulação com login único

Você pode adicionar uma etapa na qual os usuários devem entrar primeiro com suas credenciais da Microsoft. Esse método de autenticação é chamado de SSO (single sign-on).

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Exemplo mostra uma tela de autenticação de tabulação." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a>Projetando uma configuração de tabulação com modelos de interface do usuário

Use um dos seguintes modelos Teams de interface do usuário para ajudar a projetar sua experiência de configuração de tabulação:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.

## <a name="view-a-tab"></a>Exibir uma guia

As guias fornecem uma experiência da Web de tela inteira em Teams onde você pode exibir conteúdo colaborativo, como painéis e painéis de tarefas, e informações importantes.

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Exemplo mostra uma guia com um quadro de tarefas." border="false":::

### <a name="anatomy-tab"></a>Anatomia: Guia

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma guia." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome da guia**: Rótulo de navegação para sua guia.|
|2|**Estouro da** guia : abre ações de guia, como renomear e remover.|
|3|**Chat de tabulação**: abre um thread de chat à direita, permitindo que os usuários tenham uma conversa ao lado do conteúdo.|
|4 |**iframe**: exibe o conteúdo da guia.

### <a name="designing-a-tab-with-ui-templates"></a>Criar uma guia com modelos de interface do usuário

Use um dos seguintes modelos Teams de interface do usuário para ajudar a projetar sua experiência de guia:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.
* [Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : um quadro de tarefas, às vezes chamado de quadro kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou conteúdo.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.
* [Navegação à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): O modelo de navegação à esquerda pode ajudar se sua guia exigir alguma navegação. Em geral, você deve manter a navegação de tabulação no mínimo.

## <a name="use-a-tab-to-collaborate"></a>Usar uma guia para colaborar

Guias ajudam a facilitar conversas sobre conteúdo em um local central.

### <a name="thread-discussion"></a>Discussão de thread

Os usuários podem postar automaticamente em um canal ou chat depois de adicionarem uma nova guia. Isso não apenas notifica os membros da equipe do novo conteúdo e fornece um link para guia, ele permite que as pessoas comecem a falar sobre a guia.

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Exemplo mostra uma guia sendo discutida em um thread de canal." border="false":::

### <a name="side-by-side-discussion"></a>Discussão lado a lado

Os usuários podem ter uma conversa em seguida durante a exibição do conteúdo da guia.

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Exemplo mostra uma guia com um chat aberto no lado direito." border="false":::

### <a name="permissions-and-role-based-views"></a>Permissões e exibições baseadas em função

A experiência de tabulação pode ser diferente para os usuários, dependendo de suas permissões. Por exemplo, um usuário pode acessar a guia sem precisar entrar. Outro usuário, no entanto, deve assinar e ver conteúdo ligeiramente diferente.

## <a name="manage-a-tab"></a>Gerenciar uma guia

Você pode incluir opções para renomear, remover ou modificar uma guia.

### <a name="anatomy-tab-menu"></a>Anatomia: menu Tab

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de tabulação." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Configurações**: (Opcional) Permite que os usuários modifiquem as configurações de uma guia depois que ela foi adicionada.|
|2|**Renomear**: Permite que os usuários dêem à guia um nome mais significativo para a equipe.|
|3|**Remover**: remove a guia do canal, chat ou reunião.|

## <a name="tab-notifications-and-deep-linking"></a>Notificações de tabulação e vinculação profunda

Você pode enviar uma mensagem com um link profundo para sua guia. Por exemplo, um cartão mostra um resumo dos dados de bugs que um usuário pode selecionar para ver o bug inteiro em uma guia. O envio de mensagens sobre a atividade de tabulação aumenta a conscientização sem notificar explicitamente todos (ou seja, atividades sem ruído). Você também pode @mention usuários específicos, se necessário.

Notificar os usuários da atividade de tabulação uma das seguintes maneiras:

* **Bot**: Este método é preferencial especialmente se o thread de tabulação for direcionado. A conversa encadeada da guia é movida para a exibição como ativa recentemente. Esse método também permite alguma sofisticação na forma como a notificação é enviada.
* **Mensagem**: uma mensagem aparece no feed de atividade do usuário com um [link profundo para a guia](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="collaboration"></a>Colaboração

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="A ilustração mostra o que fazer com o design de navegação de tabulação." border="false":::

#### <a name="do-facilitate-conversation"></a>Do: Facilitar a conversa

Inclua conteúdo e componentes que as pessoas possam falar. Se ele não se encaixar no contexto de um chat, canal ou reunião, ele não pertence à sua guia.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Exemplo mostra o que não fazer com o design de navegação de tabulação." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a>Não: trate sua guia como qualquer outra página da Web

Uma guia não é uma página da Web que alguém pode exibir uma vez. Uma guia deve exibir o conteúdo mais importante e relevante que as pessoas precisam para realizar algo juntos.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Exemplo mostrando o que fazer com o design de navegação de tabulação." border="false":::

#### <a name="do-limit-tasks-and-data"></a>Fazer: Limitar tarefas e dados

As guias funcionam melhor quando elas abordam necessidades específicas. Inclua um conjunto limitado de tarefas e dados relevantes para a equipe ou grupo.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de navegação de tabulação." border="false":::

#### <a name="dont-embed-your-entire-app"></a>Não: incorporar seu aplicativo inteiro

Usar uma guia para exibir um aplicativo inteiro com navegação de vários níveis e interações complexas leva à sobrecarga de informações.

   :::column-end:::
:::row-end:::

### <a name="setup"></a>Configurar

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Ilustração mostrando o que fazer com o design de configuração de tabulação." border="false":::

#### <a name="do-keep-it-simple"></a>Fazer: mantenha-o simples

Se seu aplicativo exigir autenticação, tente integrar o SSO (login único) da Microsoft para uma experiência de login mais perfeita. Além disso, inclua apenas informações essenciais e etapas para adicionar a guia.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de configuração de tabulação." border="false":::

#### <a name="dont-have-too-many-steps"></a>Não: ter muitas etapas

Remova todas as etapas desnecessárias para adicionar uma guia.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Ilustração mostrando o que fazer com temas de tabulação." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Do: tire proveito de Teams de cores

Cada Teams tem seu próprio esquema de cores. Para lidar com alterações de tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (interface do usuário fluente)</a> em seu design.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Ilustração mostrando o que não fazer com temas de tabulação." border="false":::

#### <a name="dont-hard-code-color-values"></a>Não: Valores de cor de código rígidos

Se você não usar tokens Teams cores, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.

   :::column-end:::
:::row-end:::
