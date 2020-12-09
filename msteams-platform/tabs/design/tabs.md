---
title: Projetando sua guia para área de trabalho e Web
description: Saiba como criar uma guia do Teams (área de trabalho e Web) e obter o kit de interface do usuário do Microsoft Teams.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 692a21c78dc86cbca5bf248e55d0332bd71c6b92
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604640"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a>Projetando sua guia para a área de trabalho e a Web do Microsoft Teams

Uma guia é uma tela grande para o conteúdo que facilita a colaboração. Para guiar o design do aplicativo, as informações a seguir descrevem e ilustra como as pessoas podem adicionar, usar e gerenciar guias no Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de interface do usuário do Microsoft Teams

Você pode encontrar diretrizes de design de guia abrangentes, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams. O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e dimensionamento responsivo que não são abordados aqui.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário do Microsoft Teams (figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a>Adicionar uma guia

Você pode adicionar uma guia do repositório do Teams (AppSource) ou em um dos seguintes contextos:

* Chat
* Canal
* Reunião (antes, durante ou após a reunião)

O exemplo a seguir mostra como uma guia é adicionada em um canal.

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="O exemplo mostra uma guia que está sendo adicionada em um canal." border="false":::

## <a name="set-up-a-tab"></a>Configurar uma guia

Há um pequeno processo de configuração para adicionar um aplicativo como uma guia de canal, chat ou reunião. A experiência é larga para você. Por exemplo, você pode ter uma descrição de como usar o aplicativo e algumas configurações opcionais. Inclua uma etapa de logon aqui se você precisar autenticar usuários.

### <a name="tab-configuration-modal"></a>Configuração da guia modal

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="O exemplo mostra uma configuração de guia modal." border="false":::

### <a name="anatomy-tab-configuration-modal"></a>Anatomia: janela de configuração da guia

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma configuração de tabulação modal." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Logotipo do aplicativo**: logotipo completo do aplicativo de cor do seu aplicativo.|
|2 |**Nome do aplicativo**: nome completo do seu aplicativo.|
|3 |**iframe**: espaço responsivo para o conteúdo do aplicativo (por exemplo, configurações de guia ou autenticação).|
|4 |**Sobre link**: abre uma caixa de diálogo mostrando mais informações sobre o aplicativo, como uma descrição completa, permissões exigidas pelo aplicativo e links para sua política de privacidade e termos de serviço.
|5 |**Botão fechar**: fecha a janela restrita.|
|6 |**Opção notificar membros da equipe**: a janela restrita pergunta se você deseja criar uma postagem permitindo que outros saibam que você adicionou uma guia.|
|7 |**Botão voltar**: vai para a etapa anterior com base em onde a caixa de diálogo foi aberta.|
|8 |**Botão salvar**: conclui a configuração da guia.|

### <a name="tab-authentication-with-single-sign-on"></a>Autenticação de guia com logon único

Você pode adicionar uma etapa em que os usuários devem entrar primeiro com suas credenciais da Microsoft. Esse método de autenticação é chamado SSO (logon único).

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="O exemplo mostra uma tela de autenticação de guia." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a>Projetando uma configuração de guia com modelos de interface do usuário

Use um dos seguintes modelos de interface do usuário do Microsoft Teams para ajudar a criar sua experiência de configuração de guia:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato verificável e permitir que os usuários executem ações em uma lista inteira ou em itens individuais.
* [Form](../../concepts/design/design-teams-app-ui-templates.md#form): formulários são para coletar, validar e enviar entradas do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para vários cenários, incluindo o login, experiências de tela de apresentação, mensagens de erro e muito mais.

## <a name="view-a-tab"></a>Exibir uma guia

As guias fornecem uma experiência Web de tela inteira no Microsoft Teams, onde você pode exibir conteúdo colaborativo, como quadros de tarefas e painéis, e informações importantes.

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="O exemplo mostra uma guia com um quadro de tarefas." border="false":::

### <a name="anatomy-tab"></a>Anatomia: Tab

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface de usuário de uma guia." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome da guia**: rótulo de navegação para sua guia.|
|2 |**Estouro de tabulação**: abre ações de tabulação, como renomear e remover.|
|3 |**Chat de guia**: abre um thread de chat à direita, permitindo que os usuários tenham uma conversa ao lado do conteúdo.|
|4 |**iframe**: exibe o conteúdo da guia.

### <a name="designing-a-tab-with-ui-templates"></a>Projetando uma guia com modelos de interface do usuário

Use um dos seguintes modelos de interface do usuário do Microsoft Teams para ajudar a criar sua experiência de guia:

* [Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato verificável e permitir que os usuários executem ações em uma lista inteira ou em itens individuais.
* [Quadro de tarefas](../../concepts/design/design-teams-app-ui-templates.md#task-board): um quadro de tarefas, às vezes chamado de um quadro Kanban ou uma pista de baixo, é uma coleção de cartões usados para acompanhar o status de itens de trabalho ou tíquetes.
* [Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela contendo vários cartões que oferecem uma visão geral de dados ou conteúdo.
* [Form](../../concepts/design/design-teams-app-ui-templates.md#form): formulários são para coletar, validar e enviar entradas do usuário de forma estruturada.
* [Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para vários cenários, incluindo o login, experiências de tela de apresentação, mensagens de erro e muito mais.
* [NAV à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): o modelo de navegação à esquerda pode ajudar se sua guia requer alguma navegação. Em geral, você deve manter a navegação de guia no mínimo.

## <a name="use-a-tab-to-collaborate"></a>Usar uma guia para colaborar

As guias ajudam a facilitar as conversas sobre o conteúdo em um local central.

### <a name="thread-discussion"></a>Discussão de thread

Os usuários podem postar automaticamente para um canal ou chat após terem adicionado uma nova guia. Isso não apenas notifica os membros da equipe do novo conteúdo e fornece um link para Tab, permitindo que as pessoas comecem a falar sobre a guia.

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="O exemplo mostra uma guia sendo discutida em um thread de canal." border="false":::

### <a name="side-by-side-discussion"></a>Discussão lado a lado

Os usuários podem ter uma conversa ao lado de exibir o conteúdo da guia.

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="O exemplo mostra uma guia com um chat aberto no lado direito." border="false":::

### <a name="permissions-and-role-based-views"></a>Permissões e exibições baseadas em função

A experiência de guia pode ser diferente para os usuários, dependendo de suas permissões. Por exemplo, um usuário pode acessar a guia sem precisar fazer logon. Outro usuário, no entanto, deve assinar e receberá um conteúdo ligeiramente diferente.

## <a name="manage-a-tab"></a>Gerenciar uma guia

Você pode incluir opções para renomear, remover ou modificar uma guia.

### <a name="anatomy-tab-menu"></a>Anatomia: menu de guia

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu guia." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Configurações**: (opcional) permite que os usuários modifiquem as configurações de uma guia após serem adicionadas.|
|2 |**Rename**: permite que os usuários forneçam um nome mais significativo para a guia para a equipe.|
|3 |**Remover**: Remove a guia do canal, chat ou reunião.|

## <a name="tab-notifications-and-deep-linking"></a>Notificações de guia e vinculação profunda

Você pode enviar uma mensagem com um link profundo para sua guia. Por exemplo, um cartão mostra um resumo dos dados de erros que um usuário pode selecionar para ver todo o bug em uma guia. O envio de mensagens sobre a atividade de guia aumenta a conscientização sem notificar explicitamente todos (ou seja, atividades sem ruído). Você também pode @mention usuários específicos, se necessário.

Notifique os usuários da atividade de guia de uma das seguintes maneiras:

* **Bot**: esse método é preferível, especialmente se o thread de guia for direcionado. A conversa encadeada da guia é movida para o modo de exibição como ativo recentemente. Esse método também permite uma certa sofisticação na forma como a notificação é enviada.
* **Mensagem**: uma mensagem aparece no feed de atividades do usuário com um [link profundo para a guia](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).

## <a name="best-practices"></a>Práticas recomendadas

### <a name="collaboration"></a>Colaboração

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Ilustração mostrando o que fazer com o design de navegação de guia." border="false":::

#### <a name="do-facilitate-conversation"></a>Fazer: facilitar a conversa

Incluir conteúdo e componentes que as pessoas podem falar. Se ele não couber no contexto de um chat, canal ou reunião, ele não pertence à sua guia.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de navegação de guia." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a>Não: trate sua guia como qualquer outra página da Web

Uma guia não é uma página da Web que alguém pode exibir uma vez. Uma guia deve exibir o conteúdo mais importante e relevante que as pessoas precisam para realizar algo juntos.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navegação

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Ilustração mostrando o que fazer com o design de navegação de guia." border="false":::

#### <a name="do-limit-tasks-and-data"></a>Fazer: limitar tarefas e dados

As guias funcionam melhor quando atendem a necessidades específicas. Inclua um conjunto limitado de tarefas e dados relevantes para a equipe ou grupo.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de navegação de guia." border="false":::

#### <a name="dont-embed-your-entire-app"></a>Não: Incorpore todo o aplicativo

Usar uma guia para exibir um aplicativo inteiro com navegação de vários níveis e interações complexas leva à sobrecarga de informações.

   :::column-end:::
:::row-end:::

### <a name="setup"></a>Configurar

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Ilustração mostrando o que fazer com o design da configuração de guia." border="false":::

#### <a name="do-keep-it-simple"></a>Fazer: simplificar

Se seu aplicativo requer autenticação, tente integrar o Microsoft Single Sign-on (SSO) para obter uma experiência de entrada mais contínua. Além disso, inclua apenas as informações essenciais e as etapas para adicionar a guia.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Ilustração mostrando o que não fazer com o design da configuração de guia." border="false":::

#### <a name="dont-have-too-many-steps"></a>Não: ter muitas etapas

Remova as etapas desnecessárias para adicionar uma guia.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Ilustração mostrando o que fazer com os temas de tabulação." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Fazer: aproveitar os tokens de cores do teams

Cada tema do teams tem seu próprio esquema de cores. Para lidar automaticamente com alterações de temas, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (IU fluente)</a> em seu design.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Ilustração mostrando o que não fazer com os temas de tabulação." border="false":::

#### <a name="dont-hard-code-color-values"></a>Não: valores de cor de código fixo

Se você não usar tokens de cores do Teams, seus designs serão menos escalonáveis e levará mais tempo para gerenciar.

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a>Validar o design

Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.

> [!div class="nextstepaction"]
> [Verificar diretrizes de validação de design](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
