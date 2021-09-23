---
title: Projete guias para desktop, Web e dispositivos móveis
description: Saiba como criar uma guia para desktop, Web e dispositivos móveis do Teams e obter o Kit de Interface do Usuário do Microsoft Teams.
author: heath-hamilton
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 99588b35e5de0a4d6c06e5d1353af312429081cc
ms.sourcegitcommit: 8feddafb51b2a1a85d04e37568b2861287f982d3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2021
ms.locfileid: "59475626"
---
# <a name="design-your-tab-for-microsoft-teams"></a>Projete sua guia para o Microsoft Teams

Uma guia é uma grande tela para o conteúdo do seu aplicativo. Para orientar a criação do seu aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar guias no Microsoft Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

No Kit de Interface do Usuário do Microsoft Teams, você encontra diretrizes abrangentes de design de guia, incluindo elementos que você pode modificar conforme necessário. O kit de Interface do Usuário também possui tópicos essenciais, como acessibilidade e dimensionamento dinâmico, que não são abordados aqui.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a>Adicionar uma guia

Você pode adicionar uma guia da loja do Teams (AppSource) ou em um dos seguintes contextos:

* Chat
* Canal
* Reunião (antes, durante ou depois da reunião)

### <a name="mobile"></a>Celular

Os usuários podem acessar as guias selecionando o botão **Mais** no canal (exemplo abaixo) ou no chat ao qual foram adicionados.

:::image type="content" source="../../assets/images/tabs/mobile-design-access-tab.png" alt-text="Exemplo mostra uma guia de celular sendo adicionada a um canal." border="false":::

### <a name="desktop"></a>Desktop

O exemplo a seguir mostra como os usuários podem adicionar uma guia em um canal.

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Exemplo mostra uma guia sendo adicionada a um canal." border="false":::

## <a name="set-up-a-tab"></a>Configurar uma guia

Há um breve processo de configuração para adicionar um aplicativo como um canal, um chat ou uma guia de reunião. A experiência depende muito de você. Por exemplo, você pode criar uma descrição de como usar o aplicativo e algumas configurações opcionais. Inclua uma etapa de logon aqui se você precisar autenticar usuários.

### <a name="tab-configuration-dialog"></a>Diálogo de configuração da guia

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Exemplo mostra um modal de configuração de guia." border="false":::

#### <a name="anatomy-tab-configuration-dialog"></a>Anatomia: diálogo de configuração da guia

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um modal de configuração de guia." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Logotipo do aplicativo**: logotipo colorido do seu aplicativo.|
|2|**Nome do aplicativo**: nome completo do seu aplicativo.|
|3|**iframe**: espaço responsivo para o conteúdo do seu aplicativo (por exemplo, configurações de guia ou autenticação).|
|4|**Link Sobre**: abre uma caixa de diálogo mostrando mais informações sobre o aplicativo, como uma descrição completa, permissões exigidas pelo aplicativo e links para sua política de privacidade e termos de serviço.|
|5|**Botão Fechar**: fecha a caixa de diálogo.|
|6|**opção Notificar membros da equipe**: a caixa de diálogo pergunta aos usuários se eles desejam criar uma postagem, permitindo que outras pessoas saibam que adicionaram uma guia.|
|7|**Botão Voltar**: vai para a etapa anterior com base no local onde a caixa de diálogo foi aberta.|
|8|**Botão Salvar**: conclui a configuração da guia.|

### <a name="tab-authentication-with-single-sign-on"></a>Autenticação de guia de logon único

Você pode adicionar uma etapa na qual os usuários devem primeiro entrar com suas credenciais da Microsoft. Esse método de autenticação é chamado de logon único (SSO).

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Exemplo mostra uma tela de autenticação de guia." border="false":::

### <a name="design-a-tab-setup-with-ui-templates"></a>Crie uma configuração de guia com modelos de interface do usuário

Use um dos seguintes modelos de interface do usuário do Teams para ajudar a projetar sua experiência de configuração de guia:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato que facilita a visualização e permite que os usuários executem ações em uma lista inteira ou itens individuais.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): os formulários são para coletar, validar e enviar a entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo logon, experiências de primeira execução, mensagens de erro e muito mais.

## <a name="view-a-tab"></a>Exibir uma guia

As guias fornecem uma experiência na Web em tela inteira no Teams, em que você pode exibir conteúdo colaborativo — como painéis e dashboards — e informações importantes.

### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/tabs/mobile-design-view-tab.png" alt-text="Exemplo mostra uma guia de celular com um painel de tarefas." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Exemplo mostra uma guia com um painel de tarefas." border="false":::

### <a name="anatomy-tab"></a>Anatomia: guia

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/tabs/mobile-design-view-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma guia." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome da guia**: rótulo de navegação para sua guia.|
|2|**Chat da guia**: abre um chat que permite que os usuários tenham uma conversa ao lado do conteúdo.|
|3|**Modo de exibição da Web**: exibe o conteúdo do aplicativo.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Esta ilustração mostra a anatomia da interface do usuário de uma guia." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome da guia**: rótulo de navegação para sua guia.|
|2|**Excedente da guia**: abre as ações de guia, como renomear e remover.|
|3|**Chat da guia**: abre um chat à direita, permitindo que os usuários tenham uma conversa ao lado do conteúdo.|
|4|**iframe**: exibe o conteúdo do aplicativo.|

### <a name="design-a-tab-with-ui-templates-and-advanced-components"></a>Projete uma guia com modelos de interface do usuário e componentes avançados

Use um dos seguintes modelos do Teams e componentes para ajudar a projetar sua experiência de guia:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato que facilita a visualização e permite que os usuários executem ações em uma lista inteira ou itens individuais.
* [Painel de tarefas](../../concepts/design/design-teams-app-ui-templates.md#task-board): um painel de tarefas, às vezes chamado de quadro Kanban ou raias, é uma coleção de cartões frequentemente usados para acompanhar o status de itens de trabalho ou tíquetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou do conteúdo.
* [Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): os formulários são para coletar, validar e enviar a entrada do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo logon, experiências de primeira execução, mensagens de erro e muito mais.
* [Navegação esquerda](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): o componente de navegação à esquerda pode ajudar se a guia requer alguma navegação. Em geral, você deve diminuir a navegação por guias.

## <a name="use-a-tab-to-collaborate"></a>Usar uma guia para colaborar

As guias facilitam as conversas sobre o conteúdo em um local central.

### <a name="thread-discussion"></a>Discussão da thread

Os usuários podem postar automaticamente em um canal ou chat depois de adicionarem uma nova guia. Isso não apenas notifica os membros da equipe sobre o novo conteúdo e fornece um link para a guia, mas permite que as pessoas comecem a falar sobre a guia.

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/tabs/mobile-design-use-tab-channel.png" alt-text="Exemplo mostra uma guia de celular sendo discutida em uma thread do canal." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Exemplo mostra uma guia sendo discutida em uma thread do canal." border="false":::

### <a name="tab-chat"></a>Chat da guia

Os usuários podem conversar ao lado do conteúdo da guia que estão exibindo. No desktop, o chat é aberto ao lado do conteúdo do aplicativo.

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/tabs/mobile-design-use-tab-side-chat.png" alt-text="Exemplo mostra uma guia de celular com uma área de chat no contexto." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Exemplo mostra uma guia com um chat aberto no lado direito." border="false":::

### <a name="permissions-and-role-based-views"></a>Permissões e exibições baseadas na função

A experiência da guia pode ser diferente para os usuários, dependendo de suas permissões. Por exemplo, um usuário pode acessar a guia sem precisar entrar. Outro usuário, no entanto, deve entrar e verá o conteúdo ligeiramente diferente.

## <a name="manage-a-tab"></a>Gerenciar uma guia

Você pode incluir opções para renomear, remover ou modificar uma guia.

### <a name="anatomy-tab-menu"></a>Anatomia: menu Guia

#### <a name="mobile"></a>Celular

:::image type="content" source="../../assets/images/tabs/mobile-design-manage-tab-menu-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de guia de celular." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Abrir no navegador**: abre o aplicativo no navegador padrão do dispositivo.|
|2|**Copiar link**: os usuários podem copiar e compartilhar um link na guia.|
|3|**Configurações**: (opcional) modifique as configurações de uma guia depois que ela for adicionada.|
|4|**Renomear**: os usuários podem dar um nome à guia que seja significativo para o canal, chat ou reunião.|
|5|**Excluir**: remove a guia do canal, chat ou reunião.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de guia." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Configurações**: (opcional) Permite que os usuários modifiquem as configurações de uma guia depois que ela for adicionada.|
|2|**Renomear**: os usuários podem dar um nome à guia que seja significativo para o canal, chat ou reunião.|
|3|**Remover**: remove a guia do canal, chat ou reunião.|

## <a name="tab-notifications-and-deep-linking"></a>Notificações de guia e vinculação profunda

Você pode enviar uma mensagem com um link profundo para sua guia. Por exemplo, um cartão mostra um resumo dos dados do bug que um usuário pode selecionar para ver o bug inteiro em uma guia. O envio de mensagens sobre a atividade da guia aumenta a visibilidade sem notificar explicitamente todos (ou seja, atividads sem ruído). Você também pode @mencionar usuários específicos, se necessário.

Notifique os usuários sobre a atividade da guia de uma das seguintes maneiras:

* **Bot**: esse método é preferencial, especialmente se a thread da guia for direcionada. A conversa encadeada da guia é exibida como ativa recentemente. Esse método também permite algum refinamento em como a notificação é enviada.
* **Mensagem**: uma mensagem aparece no feed de atividades do usuário com um [link profundo para a guia](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade:

### <a name="collaboration"></a>Colaboração

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Ilustração mostra o que fazer com o design da navegação por guia." border="false":::

#### <a name="do-facilitate-conversation"></a>Recomendamos: facilitar a conversa

Inclua conteúdo e componentes sobre os quais as pessoas possam falar. Se ele não se ajustar no contexto de um chat, canal ou reunião, não pertence à sua guia.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Exemplo mostra o que não fazer com o design da navegação por guia." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a>Não recomendamos: tratar sua guia como qualquer outra página da Web

Uma guia não é uma página da Web que alguém pode exibir uma vez. Uma guia deve exibir o conteúdo mais importante e relevante de que as pessoas precisam para realizar algo juntos.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Exemplo mostrando o que fazer com o design da navegação por guia." border="false":::

#### <a name="do-limit-tasks-and-data"></a>Recomendamos: limitar tarefas e dados

As guias funcionam melhor quando atendem a necessidades específicas. Inclua um conjunto limitado de tarefas e dados relevantes para a equipe ou grupo.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Ilustração mostrando o que não fazer com o design da navegação por guia." border="false":::

#### <a name="dont-embed-your-entire-app"></a>Não recomendamos: inserir todo o aplicativo

Usar uma guia para exibir um aplicativo inteiro com navegação em vários níveis e interações complexas leva à sobrecarga de informações.

   :::column-end:::
:::row-end:::

### <a name="setup"></a>Configuração

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Ilustração mostrando o que fazer com o design de configuração da guia." border="false":::

#### <a name="do-keep-it-simple"></a>Recomendamos: manter a simplicidade

Se o seu aplicativo exigir autenticação, tente integrar o logon único (SSO) da Microsoft para uma experiência de logon mais contínua. Além disso, inclua apenas informações essenciais e etapas para adicionar a guia.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de configuração da guia." border="false":::

#### <a name="dont-have-too-many-steps"></a>Não recomendamos: ter muitas etapas

Remova as etapas desnecessárias para adicionar uma guia.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Ilustração mostrando o que fazer com o tema da guia." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Recomendamos: aproveitar os tokens de cor do Teams

Cada tema do Teams tem seu próprio esquema de cores. Para manipular as alterações de tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cores (IU do Fluent)</a> em seu design.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Ilustração mostrando o que não fazer com o tema da guia." border="false":::

#### <a name="dont-hard-code-color-values"></a>Não recomendamos: valores de cor de código rígido

Se você não usar tokens de cor do Teams, seus designs serão menos escalonáveis e levarão mais tempo para serem gerenciados.

   :::column-end:::
:::row-end:::
