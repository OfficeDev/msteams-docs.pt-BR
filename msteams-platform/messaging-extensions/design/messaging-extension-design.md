---
title: Projetando sua extensão de mensagens
description: Saiba como criar uma extensão de mensagens do Teams e obter o Kit de Interface do Usuário do Microsoft Teams.
keywords: práticas recomendadas de dicas de extensões de mensagens de referência de diretrizes de design do teams
author: heath-hamilton
localization_priority: Priority
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: f4d1ba1e6e0b71b37e2b7b2d2a32fb729822ba1c
ms.sourcegitcommit: 99b1f151e4e36a86c6a5d2ccbde01bf45b61f526
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2021
ms.locfileid: "53037667"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a>Criando sua extensão de mensagens do Microsoft Teams

Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem sair da conversa.
Para orientar a criação do seu aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar extensões de mensagens no Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de IU do Microsoft Teams

No Kit de Interface do Usuário do Microsoft Teams, você encontra diretrizes de design de extensão de mensagem mais abrangentes, incluindo elementos que você pode modificar conforme necessário.

> [!div class="nextstepaction"]
> [Obtenha o Kit de IU do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a>Adicionar uma extensão de mensagem

Você pode adicionar uma extensão de mensagens nos seguintes contextos do Teams:

* Vá para a Teams Store.
* Em um canal, chat ou reunião (antes, durante e depois) próximo à caixa de redação. Vale a pena observar que se você adicionar uma extensão de mensagens em um desses locais, somente você poderá usá-la nesse contexto.

O exemplo a seguir mostra como adicionar uma extensão de mensagens em um canal:

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="O exemplo mostra como adicionar uma extensão de mensagens perto da caixa de redação em um canal." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-add-in-channel.png" alt-text="O exemplo mostra como adicionar uma extensão de mensagens perto da caixa de redação em um canal no celular." border="false":::

---

## <a name="set-up-a-messaging-extension"></a>Criar uma extensão de mensagem

A autenticação não é obrigatória, mas se seu aplicativo for algo como uma ferramenta de acompanhamento de tíquetes, talvez seja necessário que as pessoas se conectem para usar a extensão de mensagens.

Para consistência entre os aplicativos do Teams, você não pode personalizar a tela de entrada. Se você usar a autenticação de SSO (logon único), os usuários serão conectados automaticamente.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="O exemplo mostra a tela de configuração da extensão de mensagens com um botão de entrada." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-set-up.png" alt-text="O exemplo mostra a tela de configuração da extensão de mensagens com um botão de entrada no celular." border="false":::

---

## <a name="types-of-messaging-extensions"></a>Tipos de extensões de mensagens

As extensões de mensagens podem ter comandos de pesquisa, comandos de ação ou ambos. Seus comandos dependem dos recursos do seu aplicativo e de como eles se encaixam nos casos de uso do Teams.

### <a name="search-commands"></a>Comandos de pesquisa

Com comandos de pesquisa, as pessoas podem usar sua extensão de mensagens para localizar rapidamente conteúdo externo e inserir em uma mensagem. Comandos de pesquisa normalmente são disponibilizados na caixa de redação. Por exemplo, você pode iniciar ou adicionar a uma discussão compartilhando um conteúdo sem sair do Teams.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="O exemplo mostra uma extensão de mensagens baseada em pesquisa iniciada na caixa de redação." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-search-command-type.png" alt-text="O exemplo mostra uma extensão de mensagens baseada em pesquisa iniciada na caixa de texto no celular." border="false":::

---

#### <a name="compose-box-layout-options"></a>Opções de layout de caixa de texto

Você tem algumas opções para exibir os resultados da pesquisa de extensão de mensagens, incluindo [modos de exibição em lista e grade](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Ilustrações mostrando opções de layout para resultados de pesquisa de extensão de mensagens." border="false":::

### <a name="action-commands"></a>Comandos de ação

Os comandos de ação permitem que as pessoas disparem ações e processem solicitações em serviços externos no Teams. Por exemplo, se seu aplicativo rastreia pedidos, um usuário pode criar um novo pedido usando o conteúdo da mensagem de um colega diretamente dentro do chat.

Extensões de mensagens baseadas em ação frequentemente exigem que os usuários preencham um formulário ou algum outro tipo de configuração dentro de um modal. Você pode criar essas experiências com [módulos de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).

## <a name="open-a-messaging-extension"></a>Abrir uma extensão de mensagem

A caixa de redação e as mensagens ou postagens são os principais contextos nos quais as pessoas usam extensões de mensagens.

### <a name="from-the-compose-box"></a>Na caixa de redação

Depois de adicionados, os usuários podem abrir sua extensão de mensagens selecionando o ícone do aplicativo abaixo da caixa de redação. Nesses exemplos, a extensão tem comandos de pesquisa e ação.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens na caixa de redação." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-compose-box.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens na caixa redigir no celular." border="false":::

---

### <a name="from-a-chat-message-or-channel-post"></a>De uma mensagem de chat ou postagem de canal

Depois de adicionados, os usuários podem selecionar o ícone **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: na mensagem de chat ou na postagem do canal para localizar os comandos de ação da extensão. Sua extensão pode estar listada em **mais ações** com base no uso.

> [!NOTE]
> O suporte para mais ações de uma mensagem de chat ou postagem de canal não está disponível na plataforma móvel do Microsoft Teams. 

#### <a name="chat-message"></a>Mensagem de chat

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens de uma mensagem de chat." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-chat-post.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens de uma postagem de chat no celular." border="false":::

---

#### Channel post

# [Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Example shows how to open a messaging extension from a channel post on mobile." border="false":::

# [Mobile](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-channel-post.png" alt-text="Example shows how to open a messaging extension from a channel post on mobile." border="false":::

---

## <a name="use-a-messaging-extension"></a>Adicionar uma extensão de mensagem

Os cenários a seguir mostram as principais formas como as pessoas usam extensões de mensagens.

### <a name="insert-content-into-a-message"></a>Inserir conteúdo em uma mensagem

**1. Selecione uma extensão de mensagem**. Os usuários podem pesquisar o conteúdo que desejam compartilhar na caixa de redação.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="O exemplo mostra um usuário pesquisando o conteúdo a ser inserido na caixa de redação." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-search.png" alt-text="O exemplo mostra um usuário pesquisando o conteúdo a ser inserido na caixa de texto no celular." border="false":::

---

**2. Insira conteúdo**. Depois de postados, outras pessoas podem responder ou selecionar o conteúdo para ver mais informações em seu aplicativo.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="O exemplo mostra um usuário postando conteúdo em uma conversa de canal." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-posted.png" alt-text="O exemplo mostra um usuário postando conteúdo em uma conversa de canal no celular." border="false":::

---

### <a name="take-action-on-a-message"></a>Executar ações em uma mensagem

**1. Selecione uma extensão de mensagem**. Seu aplicativo pode incluir um ou mais comandos de ação.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="O exemplo mostra um usuário selecionando um comando de ação de extensão de mensagens." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-select-action-command.png" alt-text="O exemplo mostra um usuário selecionando um comando de ação de extensão de mensagens no celular." border="false":::

---

**2. Conclua a ação**. Seu aplicativo pode receber e processar qualquer conteúdo ou dados enviados pela ação da mensagem. Isso permite que os usuários permaneçam em suas conversas e, no exemplo a seguir, não se preocupem em inserir informações diretamente em seu aplicativo.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Exemplo de como executar uma ação em uma mensagem." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-complete-action-command.png" alt-text="Exemplo de como executar uma ação em uma mensagem no celular." border="false":::

---

### <a name="preview-links"></a>Links de visualização

As extensões de mensagens também permitem que você insira links avançados de uma URL reconhecida em uma mensagem (essa funcionalidade é chamada de [desdobramento de link](../../messaging-extensions/how-to/link-unfurling.md).)

**1. Cole um link reconhecido** na caixa de texto.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="O exemplo mostra um usuário colando um link na caixa de redação." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-paste-preview-link.png" alt-text="O exemplo mostra um usuário colando um link na caixa de redação no celular." border="false":::

---

**2. Insira conteúdo**. Se seu aplicativo reconhecer a URL na caixa de redação, ele renderizará o link como um cartão que fornece uma visualização com conteúdo avançado do conteúdo da Web. (Consulte as [Diretrizes de design de Cartões Adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md) para obter mais informações.)

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="O exemplo mostra como a URL, já que é reconhecida pelo seu aplicativo, inclui algum conteúdo avançado na caixa de redação." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-preview-link.png" alt-text="O exemplo mostra como a URL, já que é reconhecida pelo seu aplicativo, inclui algum conteúdo avançado na caixa de redação no celular." border="false":::

---

## <a name="manage-a-messaging-extension"></a>Gerenciar uma extensão de mensagem

Ao clicar com o botão direito do mouse no ícone, os usuários podem fixar, remover ou configurar sua extensão de mensagens.

## <a name="anatomy"></a>Anatomia

### <a name="messaging-extension-in-the-compose-box"></a>Extensão de mensagens na caixa de redação

O exemplo a seguir é uma extensão de mensagens aberta na caixa de redação.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de redação." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Logotipo do aplicativo**: ícone de cor do logotipo do aplicativo.|
|2|**Nome do aplicativo**: nome completo do seu aplicativo.|
|3|**Ícone de menu de comandos de ação (opcional)**: abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar algum).
|4|**Caixa de pesquisa**: permite que os usuários localizem o conteúdo do aplicativo que desejam inserir.|
|5|**Menu guia (opcional)**: fornece várias categorias de conteúdo.|
|6|**Menu de comandos de ação (opcional)**: exibe a lista de comandos de ação (se você especificar algum).|
|7|**Conteúdo do aplicativo**: principalmente para exibir os resultados da pesquisa. O exemplo aqui está usando o layout da lista (o layout da grade é outra opção).|
|8|**Logotipo do aplicativo**: ícone de contorno do logotipo do aplicativo.|

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de redação no celular." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome do aplicativo**: nome completo do seu aplicativo.|
|2|**Ícone de menu de comandos de ação (opcional)**: abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar algum).
|3|**Caixa de pesquisa**: permite que os usuários localizem o conteúdo do aplicativo que desejam inserir.|
|4|**Menu guia (opcional)**: fornece várias categorias de conteúdo.|
|5|**Menu de comandos de ação (opcional)**: exibe a lista de comandos de ação (se você especificar algum).|
|6|**Conteúdo do aplicativo**: principalmente para exibir os resultados da pesquisa.|

---

### <a name="messaging-extension-management-menu"></a>Menu de gerenciamento de extensão de mensagens

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de gerenciamento de extensão de mensagens." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Desafixar**: disponível se o usuário fixou seu aplicativo.|
|2|**Remover**: remove a extensão de mensagens do canal, chat ou reunião.|

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="setup-and-general-usage"></a>Configuração e uso geral

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Exemplo de configuração e uso geral." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a>Recomendamos: integrar com logon único

O SSO torna o processo de entrada mais fácil, rápido e seguro. Além disso, se um usuário já tiver entrado em seu aplicativo pessoal, ele não precisará entrar novamente para acessar a extensão de mensagens.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Exemplo de integração com logon único." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a>Não recomendamos: remover os usuários da conversa

Extensões de mensagens são atalhos que devem reduzir a alternância de contexto. Sua extensão não deve, por exemplo, direcionar usuários para uma página da Web fora do Teams.

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a>Recomendamos: realçar sua extensão de mensagens

As extensões de mensagens nem sempre são fáceis de localizar. Inclua capturas de tela de como usá-las na página de detalhes do aplicativo. Se seu aplicativo também incluir um bot, você poderá incluir a documentação da ajuda da extensão de mensagens em um tour de boas-vindas do bot.

### <a name="templating"></a>Modelagem

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Exemplo de modelagem." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a>Recomendamos: permitir que o Teams cuide de parte do trabalho de design, se possível

Se fizer sentido para seus casos de uso, considere criar uma extensão de mensagens baseada em pesquisa. O Teams renderiza esses tipos de extensões com temas e acessibilidade internos.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Exemplo de como o trabalho de design é cuidado." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a>Não recomendamos: inserir todo o aplicativo em um módulo de tarefa

Se a extensão de mensagens exigir comandos de ação, mantenha o módulo de tarefa simples e exiba apenas os componentes necessários para concluir a ação.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Temas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Exemplo de temas." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Recomendamos: aproveitar os tokens de cor do Teams

Cada tema do Teams tem seu próprio esquema de cores. Para manipular as alterações de tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cores (IU do Fluent)</a> em seu design.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Exemplos de tokens de cor." border="false":::

#### <a name="dont-hard-code-color-values"></a>Não recomendamos: valores de cor de código rígido

Se você não usar tokens de cor do Teams, seus designs serão menos escalonáveis e levarão mais tempo para serem gerenciados.

   :::column-end:::
:::row-end:::

### <a name="actions"></a>Ações

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Exemplo de ações." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a>Recomendamos: incluir comandos de ação que fazem sentido no contexto

As ações de mensagem devem estar relacionadas ao que um usuário está olhando. Por exemplo, forneça aos usuários um atalho para criar um problema ou item de trabalho usando o texto na postagem de alguém.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Exemplos de comandos de ação." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a>Não recomendamos: incluir comandos de ações que não são contextuais

Uma ação de mensagem para **exibir seu painel** provavelmente pareceria desconectada da maioria das conversas.

   :::column-end:::
:::row-end:::

### <a name="searches"></a>Pesquisas

#### <a name="do-show-search-results-while-typing"></a>Recomendamos: mostrar resultados da pesquisa ao digitar

Forneça resultados de pesquisa sugeridos enquanto os usuários digitam. Eles podem encontrar o conteúdo de que precisam mais rapidamente com a quantidade mínima de caracteres.

#### <a name="dont-require-users-to-submit-a-query"></a>Não recomendamos: exigir que os usuários enviem uma consulta

Você pode fazer com que os usuários pressionem uma tecla ou selecionem um botão para enviar consultas ao seu aplicativo. Embora isso possa ser mais fácil para o serviço de serviços de aplicativo, as pessoas podem ficar confusas por não estarem vendo os resultados da pesquisa em tempo real enquanto digitam.

#### <a name="do-consider-zero-term-queries"></a>Recomendamos: considerar consultas de zero termo

Por exemplo, antes de um usuário gravar qualquer coisa na caixa de pesquisa, exiba o que ele visualizou pela última vez em seu aplicativo. É possível que eles desejem inserir esse conteúdo em suas conversas.
