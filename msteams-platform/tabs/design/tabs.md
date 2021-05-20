---
title: Projetando sua guia para desktop e web
description: Aprenda a projetar uma guia Teams (desktop e web) e obtenha o kit de interface do usuário Microsoft Teams.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: baa17cd97ff4e2cad91615dced5c4e4cf5e533c8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566877"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a>Projetando sua guia para Microsoft Teams desktop e web

Uma guia é uma tela grande para o seu conteúdo. Para orientar o design do aplicativo, as seguintes informações descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar guias em Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Você pode encontrar diretrizes abrangentes de design de guias, incluindo elementos que você pode pegar e modificar conforme necessário, no Microsoft Teams UI Kit. O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e dimensionamento responsivo que não são abordados aqui.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a>Adicionar uma guia

Você pode adicionar uma guia na loja Teams (AppSource) ou em um dos seguintes contextos:

* Chat
* Canal
* Reunião (antes, durante ou depois da reunião)

O exemplo a seguir mostra como uma guia é adicionada em um canal:

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="O exemplo mostra uma guia sendo adicionada em um canal." border="false":::

## <a name="set-up-a-tab"></a>Configure uma guia

Há um pequeno processo de configuração para adicionar um aplicativo como canal, chat ou guia de reunião. A experiência depende de você. Por exemplo, você pode ter uma descrição de como usar o aplicativo e algumas configurações opcionais. Inclua um passo de login aqui se você precisar autenticar os usuários.

### <a name="tab-configuration-modal"></a>Modal de configuração da guia

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="O exemplo mostra um modal de configuração de guia." border="false":::

### <a name="anatomy-tab-configuration-modal"></a>Anatomia: Modal de configuração da guia

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um modal de configuração de guia." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Logotipo do** aplicativo : Logotipo completo do aplicativo colorido do seu aplicativo.|
|2|**Nome do** aplicativo : Nome completo do seu aplicativo.|
|3|**iframe**: Espaço responsivo para o conteúdo do seu aplicativo. Por exemplo, configurações de guia ou autenticação.|
|4 |**Sobre o link**: Abre uma caixa de diálogo mostrando mais informações sobre o aplicativo, como uma descrição completa, permissões exigidas pelo aplicativo e links para sua política de privacidade e termos de serviço.
|5 |**Botão de fechamento**: Fecha o modal.|
|6 |**Opção notificar membros da equipe**: O modal pergunta se você deseja criar um post informando que você adicionou uma guia.|
|7 |**Botão de** trás : Vai para a etapa anterior com base em onde o diálogo foi aberto.|
|8 |**Botão salvar:** completa a configuração da guia.|

### <a name="tab-authentication-with-single-sign-on"></a>Autenticação de guia com login único

Você pode adicionar uma etapa na qual os usuários devem primeiro fazer login com suas credenciais microsoft. Este método de autenticação é chamado de single sign-on (SSO).

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="O exemplo mostra uma tela de autenticação de guias." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a>Projetando uma configuração de guia com modelos de interface do usuário

Use um dos seguintes modelos de interface do usuário Teams para ajudar a projetar sua experiência de configuração de guia:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): As listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar a entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): O modelo de estado vazio pode ser usado para muitos cenários, incluindo login, experiências de primeira execução, mensagens de erro e muito mais.

## <a name="view-a-tab"></a>Exibir uma guia

As guias fornecem uma experiência web em tela cheia em Teams onde você pode exibir conteúdo colaborativo — tais painéis de tarefas e dashboards — e informações importantes.

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="O exemplo mostra uma guia com uma placa de tarefas." border="false":::

### <a name="anatomy-tab"></a>Anatomia: Guia

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma guia." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome da guia**: Etiqueta de navegação para sua guia.|
|2|**Estouro da** guia : Abre ações de guia, como renomear e remover.|
|3|**Tab chat**: Abre um thread de bate-papo à direita, permitindo que os usuários tenham uma conversa ao lado do conteúdo.|
|4 |**iframe**: Exibe o conteúdo da guia.

### <a name="designing-a-tab-with-ui-templates"></a>Projetando uma guia com modelos de interface do usuário

Use um dos seguintes modelos de interface do usuário Teams para ajudar a projetar sua experiência de guia:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): As listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.
* [Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : Um quadro de tarefas, às vezes chamado de placa kanban ou pistas de natação, é uma coleção de cartões frequentemente usados para rastrear o status de itens de trabalho ou bilhetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Um painel de instrumentos é uma tela que contém vários cartões que fornecem uma visão geral de dados ou conteúdo.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar a entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): O modelo de estado vazio pode ser usado para muitos cenários, incluindo login, experiências de primeira execução, mensagens de erro e muito mais.
* [Navegação à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): O modelo de navegação à esquerda pode ajudar se sua guia precisar de alguma navegação. Em geral, você deve manter a navegação de controle ao mínimo.

## <a name="use-a-tab-to-collaborate"></a>Use uma guia para colaborar

As guias ajudam a facilitar conversas sobre conteúdo em um local central.

### <a name="thread-discussion"></a>Discussão de tópicos

Os usuários podem postar automaticamente em um canal ou chat depois de adicionar uma nova guia. Isso não só notifica os membros da equipe do novo conteúdo e fornece um link para a guia, ele permite que as pessoas comecem a falar sobre a guia.

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="O exemplo mostra uma guia sendo discutida em um segmento de canal." border="false":::

### <a name="side-by-side-discussion"></a>Discussão lado a lado

Os usuários podem ter uma conversa em seguida enquanto visualizam o conteúdo da guia.

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="O exemplo mostra uma guia com um chat aberto no lado direito." border="false":::

### <a name="permissions-and-role-based-views"></a>Permissões e visualizações baseadas em papéis

A experiência da guia pode ser diferente para os usuários, dependendo de suas permissões. Por exemplo, um usuário pode acessar a guia sem ter que fazer login. Outro usuário, no entanto, deve assinar e verá conteúdo ligeiramente diferente.

## <a name="manage-a-tab"></a>Gerenciar uma guia

Você pode incluir opções para renomear, remover ou modificar uma guia.

### <a name="anatomy-tab-menu"></a>Anatomia: Menu de guia

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de guia." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Configurações**: (Opcional) Permite que os usuários modifiquem as configurações de uma guia após sua adicionada.|
|2|**Renomear**: Permite que os usuários dêem à guia um nome mais significativo para a equipe.|
|3|**Remova**: Remove a guia do canal, bate-papo ou reunião.|

## <a name="tab-notifications-and-deep-linking"></a>Notificações de guias e vinculação profunda

Você pode enviar uma mensagem com um link profundo para sua guia. Por exemplo, um cartão mostra um resumo dos dados de bugs que o usuário pode selecionar para ver todo o bug em uma guia. Enviar mensagens sobre atividade de guia aumenta a conscientização sem notificar explicitamente todos (ou seja, atividade sem ruído). Você também pode @mention usuários específicos, se necessário.

Notifique os usuários da atividade da guia uma das seguintes maneiras:

* **Bot**: Este método é preferido especialmente se o segmento de guia for direcionado. A conversa roscada da guia é colocada em exibição como recentemente ativa. Este método também permite alguma sofisticação na forma como a notificação é enviada.
* **Mensagem**: Uma mensagem aparece no feed de atividades do usuário com um [link profundo para a guia](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade:

### <a name="collaboration"></a>Colaboração

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="A ilustração mostra o que fazer com o design de navegação de guias." border="false":::

#### <a name="do-facilitate-conversation"></a>Faça: Facilite a conversa

Inclua conteúdo e componentes que as pessoas possam falar. Se ele não se encaixa no contexto de um chat, canal ou reunião, ele não pertence à sua guia.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Exemplo mostra o que não fazer com o design de navegação de guias." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a>Não: Trate sua guia como qualquer outra página da Web

Uma guia não é uma página web que alguém pode visualizar uma vez. Uma guia deve exibir seu conteúdo mais importante e relevante que as pessoas precisam para realizar algo juntos.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Exemplo mostrando o que fazer com o design de navegação de guias." border="false":::

#### <a name="do-limit-tasks-and-data"></a>Faça: Limite tarefas e dados

As guias funcionam melhor quando abordam necessidades específicas. Inclua um conjunto limitado de tarefas e dados relevantes para a equipe ou grupo.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de navegação de guias." border="false":::

#### <a name="dont-embed-your-entire-app"></a>Não: incorpore todo o seu aplicativo

Usar uma guia para exibir um aplicativo inteiro com navegação em vários níveis e interações complexas leva à sobrecarga de informações.

   :::column-end:::
:::row-end:::

### <a name="setup"></a>Configurar

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Ilustração mostrando o que fazer com o design de configuração da guia." border="false":::

#### <a name="do-keep-it-simple"></a>Faça: Mantenha simples

Se o seu aplicativo precisar de autenticação, tente integrar o SSO (Single Login) (Microsoft Single Sign-on) para uma experiência de login mais perfeita. Além disso, inclua apenas informações e etapas essenciais para adicionar a guia.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de configuração da guia." border="false":::

#### <a name="dont-have-too-many-steps"></a>Não: Tenha muitos passos

Remova quaisquer etapas desnecessárias para adicionar uma guia.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Ilustração mostrando o que fazer com o tema da guia." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Faça: Aproveite Teams tokens de cores

Cada Teams tema tem seu próprio esquema de cores. Para lidar com as alterações do tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cores (Fluent UI)</a> em seu design.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Ilustração mostrando o que não fazer com o tema da guia." border="false":::

#### <a name="dont-hard-code-color-values"></a>Não: Valores de cores de código rígido

Se você não usar Teams tokens de cor, seus designs serão menos escaláveis e levarão mais tempo para gerenciar.

   :::column-end:::
:::row-end:::
