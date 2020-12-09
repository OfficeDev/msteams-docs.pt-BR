---
title: Criar sua extensão de mensagens
description: Saiba como projetar uma extensão de mensagens de equipes e obter o kit de interface do usuário do Microsoft Teams.
keywords: Diretrizes de design de equipes referência de dicas de extensões de mensagens recomendadas
author: heath-hamilton
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: ad628bdaa46058aed4acdcea1a224c7ebfe40f89
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604791"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a>Projetando sua extensão de mensagens do Microsoft Teams

As extensões de mensagens são atalhos para inserir o conteúdo do aplicativo ou atuam em uma mensagem sem precisar sair da conversa.

Para guiar o design do aplicativo, as informações a seguir descrevem e ilustra como as pessoas podem adicionar, usar e gerenciar extensões de mensagens no Microsoft Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de interface do usuário do Microsoft Teams

Você pode encontrar diretrizes de design de extensão de mensagens abrangentes, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário do Microsoft Teams (figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a>Adicionar uma extensão de mensagens

Você pode adicionar uma extensão de mensagens nos seguintes contextos da equipe:

* No repositório do Teams (AppSource).
* Em um canal, chat ou reunião (antes, durante e depois) próximo da caixa de composição. Vale a pena observar se você adicionar uma extensão de mensagens em um desses lugares, somente você pode usá-lo nesse contexto.

O exemplo a seguir mostra como você adiciona uma extensão de mensagens em um canal.

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="O exemplo mostra como adicionar uma extensão de mensagens próxima à caixa de composição em um canal." border="false":::

## <a name="set-up-a-messaging-extension"></a>Configurar uma extensão de mensagens

A autenticação não é obrigatória, mas, se o aplicativo for algo parecido com uma ferramenta de controle de tíquetes, talvez você precise que as pessoas entrem para usar a extensão de mensagens.

Para consistência entre os aplicativos do Microsoft Teams, você não pode personalizar a tela de entrada. Se você usar a autenticação de logon único (SSO), os usuários serão conectados automaticamente.

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Exemplo mostra a tela de configuração de extensão de mensagens com um botão de entrada." border="false":::

## <a name="types-of-messaging-extensions"></a>Tipos de extensões de mensagens

As extensões de mensagens podem ter comandos de pesquisa, comandos de ação ou ambos. Seus comandos dependem dos recursos do seu aplicativo e de como eles se encaixam nos casos de uso do Microsoft Teams.

### <a name="search-commands"></a>Comandos de pesquisa

Com os comandos de pesquisa, as pessoas podem usar sua extensão de mensagens para localizar rapidamente conteúdo externo e inserir em uma mensagem. Os comandos de pesquisa normalmente são disponibilizados na caixa de composição. Por exemplo, você pode iniciar ou adicionar a uma discussão compartilhando uma parte do conteúdo, sem nunca deixar o Microsoft Teams.

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="O exemplo mostra uma extensão de mensagens baseada em pesquisa iniciada a partir da caixa de composição." border="false":::

#### <a name="compose-box-layout-options"></a>Opções de layout da caixa de composição

Você tem algumas opções para exibir resultados de pesquisa de extensão de mensagens, incluindo [modos de exibição de lista e de grade](../../messaging-Ask about extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Ilustrações mostrando opções de layout para resultados de pesquisa de extensão de mensagens." border="false":::

### <a name="action-commands"></a>Comandos de ação

Os comandos de ação permitem que as pessoas disparem ações e processem solicitações em serviços externos no Teams. Por exemplo, se o seu aplicativo rastreia pedidos, um usuário pode criar um novo pedido usando o conteúdo da mensagem de um colega da direita dentro do bate-papo.

As extensões de mensagens baseadas em ação freqüentemente exigem que os usuários concluam um formulário ou outro tipo de configuração em uma janela restrita. Você pode criar essas experiências com [módulos de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).

## <a name="open-a-messaging-extension"></a>Abrir uma extensão de mensagens

A caixa de redação e mensagens/postagens são os principais contextos em que as pessoas usam as extensões de mensagens.

### <a name="from-the-compose-box"></a>Na caixa de composição

Depois de adicionado, os usuários podem abrir sua extensão de mensagens selecionando o ícone do aplicativo abaixo da caixa de composição. Neste exemplo, a extensão tem comandos Search e Action.

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens na caixa de composição." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a>De uma mensagem de chat ou postagem de canal

Depois de adicionado, os usuários podem selecionar o ícone **mais** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: na mensagem de chat ou postagem de canal para localizar os comandos de ação da extensão. Sua extensão pode ser listada em **mais ações** com base no uso.

#### <a name="chat-message"></a>Mensagem de chat

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens de uma mensagem de chat." border="false":::

#### <a name="channel-post"></a>Postagem de canal

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens de uma postagem de canal." border="false":::

## <a name="use-a-messaging-extension"></a>Usar uma extensão de mensagens

Os cenários a seguir mostram as principais maneiras pelas quais as pessoas usam as extensões de mensagens.

### <a name="insert-content-into-a-message"></a>Inserir conteúdo em uma mensagem

**1. Selecione uma extensão de mensagens**. Os usuários podem pesquisar o conteúdo que deseja compartilhar da caixa de composição.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="O exemplo mostra um usuário procurando conteúdo a ser inserido na caixa de composição." border="false":::

**2. Insira o conteúdo**. Depois de publicado, as outras pessoas podem responder ou selecionar o conteúdo para ver mais informações em seu aplicativo.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="O exemplo mostra um usuário postando conteúdo em uma conversa de canal." border="false":::

### <a name="take-action-on-a-message"></a>Executar uma ação em uma mensagem

**1. Selecione uma extensão de mensagens**. Seu aplicativo pode incluir um ou mais comandos de ação.

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="O exemplo mostra um usuário selecionando um comando de ação de extensão de mensagem." border="false":::

**2. Conclua a ação**. Seu aplicativo pode receber e processar qualquer conteúdo ou dados enviados pela ação de mensagem. Isso permite que os usuários permaneçam em sua conversa e, no exemplo a seguir, não se preocupe em inserir informações diretamente em seu aplicativo.

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="O exemplo mostra um usuário procurando conteúdo a ser inserido na caixa de composição." border="false":::

### <a name="preview-links"></a>Visualizar links

As extensões de mensagens também permitem que você insira links ricos de uma URL reconhecida em uma mensagem (esse recurso é chamado de [link Unfurling](../../messaging-extensions/how-to/link-unfurling.md).)

**1. Cole um link reconhecido** na caixa de composição.

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="O exemplo mostra um usuário colando um link na caixa Compost." border="false":::

**2. Insira o conteúdo**. Se seu aplicativo reconhece a URL na caixa de composição, ele renderiza o link como um cartão que fornece uma visualização rica no conteúdo do conteúdo da Web. (Confira [diretrizes de design de cartões adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md) para obter mais informações.)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="O exemplo mostra como a URL, como é reconhecida pelo seu aplicativo, inclui um conteúdo avançado na caixa de composição." border="false":::

## <a name="manage-a-messaging-extension"></a>Gerenciar uma extensão de mensagens

Ao clicar com o botão direito do mouse no ícone, os usuários podem fixar, remover ou configurar sua extensão de mensagens.

## <a name="anatomy"></a>Anatomia

### <a name="messaging-extension-in-the-compose-box"></a>Extensão de mensagens na caixa de composição

O exemplo a seguir é uma extensão de mensagens aberta da caixa de composição.

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de composição." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Logotipo do aplicativo**: ícone de cor do logotipo do seu aplicativo.|
|2 |**Nome do aplicativo**: nome completo do seu aplicativo.|
|3 |**Ícone de menu de comandos de ação (opcional)**: abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar any).
|4 |**Caixa de pesquisa**: permite que os usuários encontrem o conteúdo de aplicativo que deseja inserir.|
|5 |**Menu guia (opcional)**: fornece várias categorias de conteúdo.|
|6 |**Menu de comandos de ação (opcional)**: exibe a lista de comandos de ação (se você especificar any).|
|7 |**Conteúdo do aplicativo**: primariamente para exibir resultados da pesquisa. O exemplo a seguir é usar o layout de lista (layout de grade é outra opção).|
|8 |**Logotipo do aplicativo**: ícone de estrutura de tópicos do logotipo do seu aplicativo.|

### <a name="messaging-extension-management-menu"></a>Menu de gerenciamento de extensões de mensagens

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de gerenciamento de extensão de mensagens." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Desafixar**: disponível se o usuário tiver afixado seu aplicativo.|
|2 |**Remover**: Remove a extensão de mensagens do canal, chat ou reunião.|

## <a name="best-practices"></a>Práticas recomendadas

### <a name="setup-and-general-usage"></a>Configuração e uso geral

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a>Fazer: integrar com logon único

O SSO torna o processo de entrada mais fácil, rápido e seguro. Além disso, se um usuário já tiver entrado no seu aplicativo pessoal, ele também não precisará entrar novamente para acessar a extensão de mensagens.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a>Não: retirar os usuários da conversa

As extensões de mensagens são atalhos que supostamente reduzem a alternância de contexto. Sua extensão não deve, por exemplo, direcionar os usuários para uma página da Web fora do teams.

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a>Fazer: realçar sua extensão de mensagens

As extensões de mensagens nem sempre são fáceis de encontrar. Inclua capturas de tela de como usá-lo na página de detalhes do aplicativo. Se seu aplicativo também incluir um bot, você poderá incluir a documentação de ajuda de extensão de mensagens em um tour de boas-vindas do bot.

### <a name="templating"></a>Refere

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a>Fazer: permitir que as equipes manipulem alguns dos trabalhos de design, se possível

Se fizer sentido para seus casos de uso, considere a criação de uma extensão de mensagens baseada em pesquisa. O Microsoft Teams processa esses tipos de extensões com temas e acessibilidade internos.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a>Não: Incorpore todo o aplicativo em um módulo de tarefa

Se sua extensão de mensagens requer comandos de ação, mantenha o módulo de tarefas simples e exiba apenas os componentes necessários para concluir a ação.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Fazer: aproveitar os tokens de cores do teams

Cada tema do teams tem seu próprio esquema de cores. Para lidar automaticamente com alterações de temas, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (IU fluente)</a> em seu design.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="dont-hard-code-color-values"></a>Não: valores de cor de código fixo

Se você não usar tokens de cores do Teams, seus designs serão menos escalonáveis e levará mais tempo para gerenciar.

   :::column-end:::
:::row-end:::

### <a name="actions"></a>Ações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a>Fazer: incluir comandos de ação que fazem sentido no contexto

As ações de mensagens devem estar relacionadas ao que um usuário está examinando. Por exemplo, forneça aos usuários um atalho para a criação de um problema ou item de trabalho usando o texto na postagem de alguém.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a>Não: incluir comandos de ações que não são contextuais

Uma ação de mensagem para **exibir seu painel** provavelmente parece ser desconectada da maioria das conversas.

   :::column-end:::
:::row-end:::

### <a name="searches"></a>Search

#### <a name="do-show-search-results-while-typing"></a>: Mostrar resultados da pesquisa ao digitar

Fornecer resultados de pesquisa sugeridos enquanto os usuários digitam. Eles podem encontrar o conteúdo que precisam mais rápido com uma quantidade mínima de caracteres.

#### <a name="dont-require-users-to-submit-a-query"></a>Não: exigir que os usuários enviem uma consulta

Você pode fazer com que os usuários pressionem uma tecla ou selecione um botão para enviar consultas ao seu aplicativo. Embora isso possa ser mais fácil no serviço de serviços de aplicativos, as pessoas podem ficar confusas de que não estão vendo os resultados de pesquisa em tempo real à medida que eles digitam.

#### <a name="do-consider-zero-term-queries"></a>Fazer: considerar consultas de zero prazos

Por exemplo, antes que um usuário escreva qualquer coisa na caixa de pesquisa, exiba o que foi exibido pela última vez em seu aplicativo. É possível que eles desejam inserir esse conteúdo em sua conversa.

## <a name="validate-your-design"></a>Validar o design

Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.

> [!div class="nextstepaction"]
> [Verificar diretrizes de validação de design](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
