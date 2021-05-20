---
title: Projetando sua extensão de mensagens
description: Aprenda a projetar uma extensão de mensagens Teams e obtenha o kit de interface do usuário Microsoft Teams.
keywords: equipes projetam diretrizes de referência de extensões de mensagens dicas práticas recomendadas
author: heath-hamilton
localization_priority: Normal
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: ed1f0f2eb2ce8d429a8a780bd2c4c4eb421d6d54
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566212"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a>Projetando sua extensão de mensagens Microsoft Teams

As extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem navegar longe da conversa.
Para orientar o design do seu aplicativo, as seguintes informações descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar extensões de mensagens em Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

Você pode encontrar diretrizes abrangentes de design de extensão de mensagens, incluindo elementos que você pode pegar e modificar conforme necessário, no Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a>Adicione uma extensão de mensagens

Você pode adicionar uma extensão de mensagens nos seguintes contextos Teams:

* A partir da loja do Microsoft Teams (AppSource).
* Em um canal, converse ou encontro (antes, durante e depois) perto da caixa de composição. Vale a pena notar se você adicionar uma extensão de mensagens em um desses lugares, só você pode usá-la nesse contexto.

O exemplo a seguir mostra como você adiciona uma extensão de mensagens em um canal:

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Exemplo mostra como adicionar uma extensão de mensagens perto da caixa de composição em um canal." border="false":::

## <a name="set-up-a-messaging-extension"></a>Configure uma extensão de mensagens

A autenticação não é obrigatória, mas se o seu aplicativo é algo como uma ferramenta de rastreamento de bilhetes, você pode precisar que as pessoas entrem para usar a extensão de mensagens.

Para obter consistência em Teams aplicativos, você não pode personalizar a tela de login. Se você usar autenticação SSO (Single Sign-on), os usuários entrarão automaticamente.

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="O exemplo mostra a tela de configuração de extensão de mensagens com um botão de login." border="false":::

## <a name="types-of-messaging-extensions"></a>Tipos de extensões de mensagens

As extensões de mensagens podem ter comandos de pesquisa, comandos de ação ou ambos. Seus comandos dependem dos recursos do seu aplicativo e de como aqueles se encaixam dentro Teams casos de uso.

### <a name="search-commands"></a>Comandos de pesquisa

Com os comandos de pesquisa, as pessoas podem usar sua extensão de mensagens para encontrar rapidamente conteúdo externo e inserir em uma mensagem. Os comandos de pesquisa são comumente disponibilizados na caixa de composição. Por exemplo, você pode iniciar ou adicionar a uma discussão compartilhando um conteúdo — sem nunca deixar Teams.

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="O exemplo mostra uma extensão de mensagens baseada em pesquisa lançada a partir da caixa de composição." border="false":::

#### <a name="compose-box-layout-options"></a>Compor opções de layout de caixa

Você tem algumas opções para exibir resultados de pesquisa de extensão de mensagens, incluindo [exibição de listas e visualizações de grade](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Ilustrações que mostram opções de layout para resultados de pesquisa de extensão de mensagens." border="false":::

### <a name="action-commands"></a>Comandos de ação

Os comandos de ação permitem que as pessoas acionem ações e processem solicitações em serviços externos dentro de Teams. Por exemplo, se o seu aplicativo rastreia pedidos, um usuário pode criar uma nova ordem usando o conteúdo da mensagem de um colega de dentro de seu chat.

As extensões de mensagens baseadas em ação frequentemente exigem que os usuários preencham um formulário ou algum outro tipo de configuração dentro de um modal. Você pode criar essas experiências com [módulos de tarefas](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).

## <a name="open-a-messaging-extension"></a>Abra uma extensão de mensagens

A caixa de composição e mensagens ou postagens são os principais contextos em que as pessoas usam extensões de mensagens.

### <a name="from-the-compose-box"></a>Da caixa de composição

Uma vez adicionado, os usuários podem abrir sua extensão de mensagens selecionando seu ícone de aplicativo abaixo da caixa de composição. Neste exemplo, a extensão tem comandos de pesquisa e ação:

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens da caixa de composição." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a>A partir de uma mensagem de bate-papo ou post de canal

Uma vez adicionado, os usuários podem selecionar o ícone **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: na mensagem de bate-papo ou postagem do canal para encontrar os comandos de ação da sua extensão. Sua extensão pode ser listada em **Mais ações** com base no uso.

> [!NOTE]
> O suporte para mais ações a partir de uma mensagem de chat ou postagem de canal não está disponível em Microsoft Teams plataforma móvel. 

#### <a name="chat-message"></a>Mensagem de chat

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens a partir de uma mensagem de bate-papo." border="false":::

#### <a name="channel-post"></a>Post do canal

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens a partir de um post de canal." border="false":::

## <a name="use-a-messaging-extension"></a>Use uma extensão de mensagens

Os cenários a seguir mostram as principais maneiras pelas quais as pessoas usam extensões de mensagens.

### <a name="insert-content-into-a-message"></a>Insira conteúdo em uma mensagem

**1. Selecione uma extensão de mensagens**. Os usuários podem pesquisar o conteúdo que desejam compartilhar a partir da caixa de composição.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="O exemplo mostra um usuário procurando conteúdo para inserir na caixa de composição." border="false":::

**2. Insira conteúdo**. Uma vez postados, outros podem responder ou selecionar o conteúdo para ver mais informações em seu aplicativo.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="O exemplo mostra um usuário postando conteúdo em uma conversa de canal." border="false":::

### <a name="take-action-on-a-message"></a>Tome uma atitude em uma mensagem

**1. Selecione uma extensão de mensagens**. Seu aplicativo pode incluir um ou mais comandos de ação.

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="O exemplo mostra um usuário selecionando um comando de ação de extensão de mensagens." border="false":::

**2. Complete a ação**. Seu aplicativo pode receber e processar qualquer conteúdo ou dados enviados pela ação da mensagem. Isso permite que os usuários permaneçam em sua conversa e, no exemplo a seguir, não se preocupem em inserir informações diretamente em seu aplicativo.

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Exemplo de como agir em uma mensagem." border="false":::

### <a name="preview-links"></a>Links de visualização

As extensões de mensagens também permitem inserir links ricos de uma URL reconhecida em uma mensagem (esse recurso é chamado [de desvendação de link](../../messaging-extensions/how-to/link-unfurling.md).)

**1. Cole um link reconhecido** na caixa de composição.

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="O exemplo mostra um usuário colando um link na caixa de compostagem." border="false":::

**2. Insira conteúdo**. Se o seu aplicativo reconhecer a URL na caixa de composição, ele renderiza o link como um cartão que fornece uma visualização rica em conteúdo do conteúdo da Web. (Consulte [as diretrizes de design de cartões adaptativos](../../task-modules-and-cards/cards/design-effective-cards.md) para obter mais informações.)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Exemplo mostra como a URL, já que é reconhecida pelo seu aplicativo, inclui algum conteúdo rico na caixa de composição." border="false":::

## <a name="manage-a-messaging-extension"></a>Gerencie uma extensão de mensagens

Ao clicar com o botão direito do mouse no ícone, os usuários podem fixar, remover ou configurar sua extensão de mensagens.

## <a name="anatomy"></a>Anatomia

### <a name="messaging-extension-in-the-compose-box"></a>Extensão de mensagens na caixa de composição

O exemplo a seguir é uma extensão de mensagens aberta a partir da caixa de composição.

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de composição." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Logotipo do** aplicativo : Ícone de cor do logotipo do seu aplicativo.|
|2|**Nome do** aplicativo : Nome completo do seu aplicativo.|
|3|**O action comanda o ícone do menu (opcional)**: Abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar algum).
|4 |**Caixa de** pesquisa : Permite que os usuários encontrem conteúdo de aplicativo que desejam inserir.|
|5 |**Menu da guia (opcional)**: Fornece várias categorias de conteúdo.|
|6 |**Menu de comandos de ação (opcional)**: Exibe lista de comandos de ação (se você especificar algum).|
|7 |**Conteúdo do** aplicativo : Principalmente para exibir resultados de pesquisa. O exemplo aqui é usar o layout da lista (o layout da grade é outra opção).|
|8 |**Logotipo do** aplicativo : Ícone de contorno do logotipo do seu aplicativo.|

### <a name="messaging-extension-management-menu"></a>Menu de gerenciamento de extensão de mensagens

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de gerenciamento de extensão de mensagens." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Unpin**: Disponível se o usuário tiver fixado seu aplicativo.|
|2|**Remover**: Remove a extensão de mensagens do canal, bate-papo ou reunião.|

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="setup-and-general-usage"></a>Configuração e uso geral

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Exemplo sobre configuração e uso geral." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a>Faça: Integre-se com um único sinal

O SSO torna o processo de login mais fácil, rápido e seguro. Além disso, se um usuário já fez login no seu aplicativo pessoal, ele também não precisa fazer login novamente para acessar a extensão de mensagens.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Exemplo de integração com sinal único ligado." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a>Não: Tire os usuários da conversa

Extensões de mensagens são atalhos que supostamente reduzem a comutação de contexto. Sua extensão não deve, por exemplo, direcionar os usuários para uma página da web fora Teams.

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a>Faça: Destaque sua extensão de mensagens

Extensões de mensagens nem sempre são fáceis de encontrar. Inclua capturas de tela de como usá-lo na página de detalhes do seu aplicativo. Se o seu aplicativo também incluir um bot, você pode incluir a documentação de ajuda de extensão de mensagens em um tour de boas-vindas do bot.

### <a name="templating"></a>Templating

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Exemplo sobre templating." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a>Faça: Deixe Teams lidar com alguns dos trabalhos de design, se possível

Se fizer sentido para seus casos de uso, considere criar uma extensão de mensagens baseada em pesquisa. Teams torna esses tipos de extensões com tema embutido e acessibilidade.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Exemplo no manuseio do trabalho de design." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a>Não: incorpore todo o seu aplicativo em um módulo de tarefas

Se sua extensão de mensagem exigir comandos de ação, mantenha o módulo de tarefa simples e exiba apenas os componentes necessários para concluir a ação.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Exemplo de tema." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Faça: Aproveite Teams tokens de cores

Cada Teams tema tem seu próprio esquema de cores. Para lidar com as alterações do tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cores (Fluent UI)</a> em seu design.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Exemplo em tokens de cores." border="false":::

#### <a name="dont-hard-code-color-values"></a>Não: Valores de cores de código rígido

Se você não usar Teams tokens de cor, seus designs serão menos escaláveis e levarão mais tempo para gerenciar.

   :::column-end:::
:::row-end:::

### <a name="actions"></a>Ações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Exemplo de ações." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a>Faça: Inclua comandos de ação que façam sentido no contexto

As ações de mensagem devem estar relacionadas com o que um usuário está olhando. Por exemplo, forneça aos usuários um atalho para criar um problema ou item de trabalho usando o texto no post de alguém.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Exemplo em comandos de ação." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a>Não: Inclua comandos de ações que não sejam contextuais

Uma ação de mensagem para **exibir seu painel** provavelmente pareceria desconectada da maioria das conversas.

   :::column-end:::
:::row-end:::

### <a name="searches"></a>Pesquisas

#### <a name="do-show-search-results-while-typing"></a>Mostrar resultados de pesquisa ao digitar

Fornecer resultados de pesquisa sugeridos enquanto os usuários digitam. Eles podem encontrar o conteúdo de que precisam mais rápido com quantidade mínima de caracteres.

#### <a name="dont-require-users-to-submit-a-query"></a>Não: Exija que os usuários enviem uma consulta

Você pode fazer com que os usuários pressionem uma tecla ou selecione um botão para enviar consultas ao seu aplicativo. Embora isso possa ser mais fácil no seu serviço de serviços de aplicativos, as pessoas podem estar confusas por não estarem vendo resultados de pesquisa em tempo real à medida que digitam.

#### <a name="do-consider-zero-term-queries"></a>Faça: Considere consultas de prazo zero

Por exemplo, antes que um usuário escreva qualquer coisa na caixa de pesquisa, exiba o que viu pela última vez em seu aplicativo. É possível que eles queiram inserir esse conteúdo em sua conversa.
