---
title: Projetando sua extensão de mensagens
description: Saiba como projetar uma extensão Teams de mensagens e obter o kit Microsoft Teams interface do usuário.
keywords: Práticas práticas práticas de referência de extensões de mensagens de referência de diretrizes de design do teams
author: heath-hamilton
localization_priority: Normal
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: 8b918c59910cbdc560fe415354d2c62c0fdd443c
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101573"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a>Projetando sua extensão Microsoft Teams de mensagens

Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem sair da conversa.
Para orientar o design do aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar extensões de mensagens em Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Você pode encontrar diretrizes abrangentes de design de extensão de mensagens, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit de interface do usuário Microsoft Teams usuário.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a>Adicionar uma extensão de mensagens

Você pode adicionar uma extensão de mensagens nos seguintes Teams contextos:

* A partir da loja do Microsoft Teams (AppSource).
* Em um canal, chat ou reunião (antes, durante e depois) perto da caixa de composição. Vale a pena notar se você adicionar uma extensão de mensagens em um desses locais, somente você poderá usá-la nesse contexto.

O exemplo a seguir mostra como você adiciona uma extensão de mensagens em um canal.

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Exemplo mostra como adicionar uma extensão de mensagens perto da caixa de redação em um canal." border="false":::

## <a name="set-up-a-messaging-extension"></a>Configurar uma extensão de mensagens

A autenticação não é obrigatória, mas se seu aplicativo for algo como uma ferramenta de controle de tíquetes, talvez seja necessário que as pessoas entre para usar a extensão de mensagens.

Para ter consistência Teams aplicativos, você não pode personalizar a tela de login. Se você usar a autenticação de logom único (SSO), os usuários serão automaticamente assinados.

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Exemplo mostra a tela de instalação de extensão de mensagens com um botão de login." border="false":::

## <a name="types-of-messaging-extensions"></a>Tipos de extensões de mensagens

As extensões de mensagens podem ter comandos de pesquisa, comandos de ação ou ambos. Seus comandos dependem dos recursos do aplicativo e de como eles se ajustam Teams casos de uso.

### <a name="search-commands"></a>Comandos de pesquisa

Com comandos de pesquisa, as pessoas podem usar sua extensão de mensagens para encontrar rapidamente conteúdo externo e inserir em uma mensagem. Comandos de pesquisa são comumente disponibilizados na caixa de redação. Por exemplo, você pode iniciar ou adicionar a uma discussão compartilhando um conteúdo sem sair Teams.

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Exemplo mostra uma extensão de mensagens baseada em pesquisa lançada na caixa de redação." border="false":::

#### <a name="compose-box-layout-options"></a>Opções de layout de caixa de redação

Você tem algumas opções para exibir resultados de pesquisa de extensão de mensagens, incluindo [exibições de lista e grade.](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests)

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Ilustrações mostrando opções de layout para resultados de pesquisa de extensão de mensagens." border="false":::

### <a name="action-commands"></a>Comandos de ação

Comandos de ação permitem que as pessoas acionem ações e solicitações de processo em serviços externos Teams. Por exemplo, se seu aplicativo rastreia pedidos, um usuário pode criar uma nova ordem usando o conteúdo da mensagem de um colega de dentro do chat.

Extensões de mensagens baseadas em ação frequentemente exigem que os usuários concluam um formulário ou algum outro tipo de configuração dentro de um modal. Você pode criar essas experiências com [módulos de tarefa.](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)

## <a name="open-a-messaging-extension"></a>Abrir uma extensão de mensagens

A caixa de redação e as mensagens/postagens são os principais contextos em que as pessoas usam extensões de mensagens.

### <a name="from-the-compose-box"></a>Na caixa de redação

Depois de adicionado, os usuários podem abrir sua extensão de mensagens selecionando o ícone do aplicativo abaixo da caixa de redação. Neste exemplo, a extensão tem comandos de pesquisa e ação.

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens da caixa de redação." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a>De uma mensagem de chat ou postagem de canal

Depois de adicionado, os usuários podem selecionar o ícone **Mais** na mensagem de chat ou na postagem do :::image type="icon" source="../../assets/icons/teams-client-more.png"::: canal para encontrar os comandos de ação da extensão. Sua extensão pode estar listada em **Mais ações** com base no uso.

> [!NOTE]
> O suporte para mais ações de uma mensagem de chat ou postagem de canal não está disponível Microsoft Teams plataforma móvel. 

#### <a name="chat-message"></a>Mensagem de chat

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens de uma mensagem de chat." border="false":::

#### <a name="channel-post"></a>Postagem de canal

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens de uma postagem de canal." border="false":::

## <a name="use-a-messaging-extension"></a>Usar uma extensão de mensagens

Os cenários a seguir mostram as principais maneiras pelas quais as pessoas usam extensões de mensagens.

### <a name="insert-content-into-a-message"></a>Inserir conteúdo em uma mensagem

**1. Selecione uma extensão de mensagens**. Os usuários podem pesquisar o conteúdo que eles querem compartilhar na caixa de redação.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Exemplo mostra um usuário procurando conteúdo para inserir na caixa de redação." border="false":::

**2. Insira conteúdo**. Depois de postado, outras pessoas podem responder ou selecionar o conteúdo para ver mais informações em seu aplicativo.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Exemplo mostra um usuário postando conteúdo em uma conversa de canal." border="false":::

### <a name="take-action-on-a-message"></a>Tomar medidas em uma mensagem

**1. Selecione uma extensão de mensagens**. Seu aplicativo pode incluir um ou mais comandos de ação.

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Exemplo mostra um usuário selecionando um comando de ação de extensão de mensagens." border="false":::

**2. Conclua a ação**. Seu aplicativo pode receber e processar qualquer conteúdo ou dados enviados pela ação da mensagem. Isso permite que os usuários permaneçam em suas conversas e, no exemplo a seguir, não se preocupe em inserir informações diretamente em seu aplicativo.

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Exemplo sobre como agir em uma mensagem." border="false":::

### <a name="preview-links"></a>Links de visualização

As extensões de mensagens também permitem inserir links ricos de uma URL reconhecida em uma mensagem (esse recurso é chamado [de desatada](../../messaging-extensions/how-to/link-unfurling.md)de link .)

**1. Colar um link reconhecido** na caixa de redação.

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Exemplo mostra um usuário colar um link na caixa de compostagem." border="false":::

**2. Insira conteúdo**. Se seu aplicativo reconhecer a URL na caixa de redação, ele renderizará o link como um cartão que fornece uma visualização rica em conteúdo do conteúdo da Web. (Consulte [Diretrizes de design de Cartões Adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md) para obter mais informações.)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Exemplo mostra como a URL, já que é reconhecida pelo seu aplicativo, inclui algum conteúdo rico na caixa de redação." border="false":::

## <a name="manage-a-messaging-extension"></a>Gerenciar uma extensão de mensagens

Clicando com o botão direito do mouse no ícone, os usuários podem fixar, remover ou configurar sua extensão de mensagens.

## <a name="anatomy"></a>Anatomia

### <a name="messaging-extension-in-the-compose-box"></a>Extensão de mensagens na caixa de redação

O exemplo a seguir é uma extensão de mensagens aberta na caixa de redação.

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de redação." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Logotipo do aplicativo**: Ícone de cor do logotipo do aplicativo.|
|2|**Nome do** aplicativo : Nome completo do seu aplicativo.|
|3|**Ícone de menu comandos de ação (opcional)**: abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar algum).
|4 |**Caixa de** pesquisa : Permite que os usuários encontrem o conteúdo do aplicativo que eles querem inserir.|
|5 |**Menu Guia (opcional)**: Fornece várias categorias de conteúdo.|
|6 |**Menu comandos de ação (opcional)**: exibe a lista de comandos de ação (se você especificar algum).|
|7 |**Conteúdo do** aplicativo : principalmente para exibir os resultados da pesquisa. O exemplo aqui está usando o layout da lista (layout de grade é outra opção).|
|8 |**Logotipo do aplicativo**: Ícone de contorno do logotipo do aplicativo.|

### <a name="messaging-extension-management-menu"></a>Menu de gerenciamento de extensão de mensagens

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de gerenciamento de extensão de mensagens." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Desempin**: Disponível se o usuário fixou seu aplicativo.|
|2|**Remover**: remove a extensão de mensagens do canal, chat ou reunião.|

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="setup-and-general-usage"></a>Instalação e uso geral

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Exemplo de configuração e uso geral." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a>Fazer: Integrar com o single-sign on

O SSO torna o processo de login mais fácil, rápido e seguro. Além disso, se um usuário já tiver feito login no seu aplicativo pessoal, ele não precisa também entrar novamente para acessar a extensão de mensagens.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Exemplo de integração com o single-sign on." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a>Não: tire os usuários da conversa

Extensões de mensagens são atalhos que devem reduzir a alternção de contexto. Sua extensão não deve, por exemplo, direcionar usuários para uma página da Web fora Teams.

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a>Do: Realça sua extensão de mensagens

Extensões de mensagens nem sempre são fáceis de encontrar. Inclua capturas de tela de como usá-lo na página de detalhes do aplicativo. Se seu aplicativo também incluir um bot, você poderá incluir a documentação da ajuda de extensão de mensagens em um tour de boas-vindas de bot.

### <a name="templating"></a>Templating

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Exemplo de templating." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a>Fazer: deixe Teams lidar com alguns dos trabalhos de design, se possível

Se fizer sentido para seus casos de uso, considere a criação de uma extensão de mensagens baseada em pesquisa. Teams renderiza esses tipos de extensões com temas e acessibilidade integrados.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Exemplo sobre como manipular o trabalho de design." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a>Não: incorporar seu aplicativo inteiro em um módulo de tarefa

Se a extensão de mensagens exigir comandos de ação, mantenha o módulo de tarefas simples e exibe apenas os componentes necessários para concluir a ação.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Exemplo sobre temas." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Do: tire proveito de Teams de cores

Cada Teams tem seu próprio esquema de cores. Para lidar com alterações de tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (interface do usuário fluente)</a> em seu design.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Exemplo em tokens de cores." border="false":::

#### <a name="dont-hard-code-color-values"></a>Não: Valores de cor de código rígidos

Se você não usar tokens Teams cores, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.

   :::column-end:::
:::row-end:::

### <a name="actions"></a>Ações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Exemplo de ações." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a>Do: Incluir comandos de ação que fazem sentido no contexto

As ações de mensagem devem estar relacionadas ao que um usuário está olhando. Por exemplo, forneça aos usuários um atalho para criar um problema ou item de trabalho usando o texto na postagem de alguém.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Exemplo em comandos de ação." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a>Não: inclua comandos de ações que não sejam contextuais

Uma ação de mensagem para **Exibir seu painel** provavelmente pareceria desconectada da maioria das conversas.

   :::column-end:::
:::row-end:::

### <a name="searches"></a>Pesquisas

#### <a name="do-show-search-results-while-typing"></a>Do: Mostrar resultados da pesquisa durante a digitação

Forneça resultados de pesquisa sugeridos enquanto os usuários digitam. Eles podem encontrar o conteúdo de que precisam mais rapidamente com a quantidade mínima de caracteres.

#### <a name="dont-require-users-to-submit-a-query"></a>Não: Exigir que os usuários enviem uma consulta

Você pode fazer com que os usuários pressionem uma tecla ou selecionem um botão para enviar consultas ao seu aplicativo. Embora isso possa ser mais fácil no seu serviço de serviços de aplicativo, as pessoas podem estar confusas de que não estão vendo resultados de pesquisa em tempo real à medida que digitam.

#### <a name="do-consider-zero-term-queries"></a>Do: considere consultas de termo zero

Por exemplo, antes de um usuário escrever qualquer coisa na caixa de pesquisa, exempli-lo pela última vez em seu aplicativo. É possível que eles queiram inserir esse conteúdo em suas conversas.
