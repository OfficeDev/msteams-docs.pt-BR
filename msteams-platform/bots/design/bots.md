---
title: Criar um bot
description: Saiba como criar um bot do Microsoft Teams e obter o Kit de Interface do Usuário do Microsoft Teams.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: b6b6712a6372a37886ef227fd941cb70f24a57ce2d65a8e3492bea8c080c74ef
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57709633"
---
# <a name="designing-your-microsoft-teams-bot"></a>Criar um bot do Microsoft Teams

Bots são aplicativos de conversa que executam um conjunto específico de tarefas. Com base no <a href="https://dev.botframework.com/" target="_blank">Microsoft Bot Framework</a>, os bots se comunicam com os usuários, respondem às suas dúvidas e os notificam de forma proativa sobre alterações e outros eventos. Eles são uma ótima maneira de se comunicar.

> [!IMPORTANT]
> Atualmente, os bots estão disponíveis no Nuvem da Comunidade Governamental (GCC) mas não estão disponíveis no GCC-High e Departamento de Defesa (DOD).

Para orientar a criação do seu aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar bots no Mirosoft Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de Interface do Usuário do Microsoft Teams

No Kit de Interface do Usuário do Microsoft Teams, você encontra diretrizes de design de bot mais abrangentes, incluindo elementos que você pode modificar conforme necessário.

> [!div class="nextstepaction"]
> [Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-bot"></a>Adicionar um bot

Os bots estão disponíveis em chats, canais e aplicativos pessoais.

# <a name="desktop"></a>[Desktop](#tab/desktop)

Os usuários podem adicionar um bot de uma das seguintes maneiras:

* Vá para a Teams Store.
* Use o submenu do aplicativo selecionando o ícone **Mais** no lado esquerdo do Microsoft Teams.
* Com uma @menção na nova caixa de chat ou de texto (o exemplo a seguir mostra como fazer isso em um chat em grupo).

    :::image type="content" source="../../assets/images/bots/add-bot-chat-at-mention.png" alt-text="Exemplo mostrando como adicionar um bot em um chat em grupo usando uma @menção." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

Os usuários podem acessar bots que foram adicionados à área de trabalho com um @mention.

:::image type="content" source="../../assets/images/bots/mobile-access-bot-chat-at-mention.png" alt-text="Exemplo mostra como acessar um bot móvel em um chat de grupo usando um @mention." border="false":::

---

## <a name="introduce-a-bot"></a>Apresentar um bot

É fundamental que o bot se apresente e descreva o que ele pode fazer. Essa troca inicial ajuda as pessoas a entenderem o que fazer com o bot, a descobrirem suas limitações e, o mais importante, a se sentirem à vontade para interagir com ele.

### <a name="welcome-message-in-a-one-on-one-chat"></a>Mensagem de boas-vindas em um chat entre duas pessoas

No contexto pessoal, as mensagens de boas-vindas definem o tom do bot. A mensagem inclui uma saudação, o que o bot pode fazer e algumas sugestões de como interagir. Por exemplo, "Tente me perguntar sobre ...". Se possível, essas sugestões devem retornar respostas armazenadas sem que o usuário precise se conectar.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-personal-welcome.png" alt-text="Exemplo mostrando a apresentação de um bot em um aplicativo pessoal." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-personal-welcome.png" alt-text="Exemplo mostra uma introdução de bot em um aplicativo pessoal no celular." border="false":::

---

### <a name="welcome-message-in-channels-and-group-chats"></a>Mensagem de boas-vindas em canais e chats de grupo

A introdução do bot deve ser um pouco diferente em canais e chats de grupo em comparação com um espaço pessoal (como um aplicativo pessoal). Na vida real, ao entrar em uma sala cheia de pessoas, você se apresenta, em vez de dar boas-vindas a todos que já estão lá. Utilize esse raciocínio ao criar o bot.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-group-welcome.png" alt-text="Exemplo mostrando a apresentação de um bot em um contexto colaborativo." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-group-welcome.png" alt-text="Exemplo mostra uma introdução de bot em um contexto colaborativo no celular." border="false":::

---

### <a name="bot-authentication-with-single-sign-on"></a>Autenticação de bot de logon único

Ao enviar uma mensagem a um bot, pode ser necessário se conectar para usar todos os recursos. Você pode simplificar o processo de autenticação usando o SSO (logon único).

Não se esqueça: no menu de comandos do bot (**O que posso fazer?**), você também deve fornecer um comando para sair.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-sso-example.png" alt-text="Exemplo mostrando um bot com um botão de logon." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-sso-example.png" alt-text="Exemplo mostra um bot com um botão de login no celular." border="false":::

---

### <a name="tours"></a>Tours

Você pode incluir um tour com mensagens de boas-vindas e se o bot responder a algo como um comando de "ajuda". Um tour é a maneira mais eficaz de descrever o que o bot pode fazer. Se aplicável, eles também são ótimos para descrever os outros recursos do seu aplicativo. Por exemplo, inclua capturas de tela de sua extensão de mensagens.

> [!IMPORTANT]
> Os tours devem estar acessíveis sem que o usuário precise se conectar.

#### <a name="one-on-one-chats"></a>Chats entre duas pessoas

Em um aplicativo pessoal, um carrossel pode fornecer uma visão geral eficaz do bot e de todos os outros recursos do aplicativo. Incluindo botões, os comandos de bot permitem que os usuários experimentem são incentivados. Por exemplo, **Criar uma tarefa**.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-tour-personal.png" alt-text="Exemplo mostrando um tour de bot em um chat entre duas pessoas." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-tour-personal.png" alt-text="Exemplo mostra um tour de bot em um chat um-a-um no celular." border="false":::

---

#### <a name="channels-and-group-chats"></a>Canais e chats em grupo

Em canais e chats em grupo, o tour deve ser aberto em um modal (também conhecido como [módulo de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) para não interromper conversas em andamento. Isso também oferece a opção de implementar exibições baseadas em função para o tour.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-tour-channel.png" alt-text="Exemplo mostrando um tour de bot em um canal." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-tour-channel.png" alt-text="Exemplo mostra um tour de bot em um canal móvel." border="false":::

---

## <a name="chat-with-a-bot"></a>Conversar por chat com um bot

Os bots integram-se diretamente na estrutura de mensagens do Microsoft Teams. Os usuários podem conversar com um bot para obter respostas às suas perguntas ou digitar comandos para que o bot execute um conjunto específico ou restrito de tarefas. Os bots podem notificar proativamente os usuários sobre alterações ou atualizações do aplicativo via chat.

### <a name="chat-with-a-bot-in-different-contexts"></a>Conversar por chat com um bot em outros contextos

Você pode usar bots nos seguintes contextos:

* **Aplicativos pessoais**: em aplicativos pessoais, os bots têm guias de chat dedicadas.
* **Chat entre duas pessoas**: um usuário pode iniciar uma conversa privada com um bot. É a mesma experiência que usar um bot em um aplicativo pessoal.
* **Chat em grupo**: as pessoas podem interagir com um bot em um chat em grupo @mencionando o bot.
* **Canal**: As pessoas podem interagir com um bot em um canal. @mencionando o nome do bot na caixa de texto. Lembre-se de que, nesse contexto, o bot está disponível para toda a equipe, não apenas para o canal.

### <a name="anatomy"></a>Anatomia

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-anatomy.png" alt-text="Exemplo mostrando a anatomia estrutural de um bot." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Ícone e nome do aplicativo**|
|2|**Guia de chat**: abre o espaço para falar com o bot (somente em aplicativos pessoais).|
|3|**Guias personalizadas**: abre outros conteúdos relacionados ao aplicativo.|
|4 |**Guia Sobre**: exibe informações básicas sobre o aplicativo.|
|5 |**Balão de chat**: as conversas do bot usam a estrutura de mensagens do Microsoft Teams.|
|6 |**Cartão Adaptável**: Se as respostas do bot incluirem Cartões Adaptáveis, o cartão ocupa a largura total da bolha de chat.|
|7 |**Menu de comando**: exibe os comandos padrão do bot (definidos por você).|

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de um bot móvel." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Ícone e nome do aplicativo**|
|2|**Guia de chat**: abre o espaço para falar com o bot (somente em aplicativos pessoais).|
|3|**Guias personalizadas**: abre outros conteúdos relacionados ao aplicativo.|
|4 |**Balão de chat**: as conversas do bot usam a estrutura de mensagens do Microsoft Teams.|
|5 |**Cartão Adaptável**: Se as respostas do bot incluirem Cartões Adaptáveis, o cartão ocupa a largura total da bolha de chat.|

---

### <a name="command-menu"></a>Menu de comando

O menu de comando fornece uma lista de palavras ou frases às quais você deseja que o bot sempre responda. O menu de comando é exibido acima da caixa de texto quando alguém está conversando com um bot. Quando um comando é selecionado, ele é inserido em uma mensagem.

A lista de comandos deve ser breve. O menu tem como objetivo destacar os principais recursos do bot. Mantenha os comandos concisos também. Por exemplo, crie um comando chamado **Ajuda** em vez de usar **Você pode me ajudar**?
O menu de comandos deve estar sempre disponível, independentemente do estado da conversa.

:::image type="content" source="../../assets/images/bots/bot-command-menu.png" alt-text="Exemplo mostrando o menu de comandos de um bot." border="false":::

## <a name="understand-what-people-are-saying"></a>Entenda o que as pessoas estão dizendo

Use um dicionário de sinônimos e receba pessoas de todas as origens para ajudar você a gerar diferentes interpretações sobre as consultas padrão.

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-hello.png" alt-text="Ilustração mostrando como um bot pode interpretar &quot;Olá&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-help.png" alt-text="Ilustração mostrando como um bot pode interpretar &quot;Ajuda&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-thanks.png" alt-text="Ilustração mostrando como um bot pode interpretar &quot;Obrigado&quot;." border="false":::
   :::column-end:::
:::row-end:::

### <a name="extract-intent-and-data-from-messages"></a>Extrair intenção e dados de mensagens

Projete seu bot para reconhecer intenções, o que interpreta o que alguém deseja de um bot em resposta a uma mensagem ou consulta. A intenção classifica uma mensagem ou consulta como uma única ação com um ou mais objetos de dados que são afetados por essa ação. 

Os exemplos a seguir definem a intenção e os dados do usuário em mensagens enviadas para bots:

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-1.png" alt-text="Exemplo mostrando a frase &quot;Reservar um voo para São Paulo&quot;, cuja intenção do usuário é &quot;agendar um voo&quot; e os dados são &quot;São Paulo&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-2.png" alt-text="Exemplo mostrando a frase &quot;Quando a loja vai abrir&quot;, cuja intenção do usuário é &quot;quando&quot; e os dados são &quot;abrir&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-3.png" alt-text="Exemplo mostrando a frase &quot;Agendar uma reunião às 13h com Paulo na Distribuição&quot;, cuja intenção do usuário é &quot;agendar uma reunião&quot; e os dados são &quot;13h&quot; e 'Paulo na Distribuição'." border="false":::
   :::column-end:::
:::row-end:::

### <a name="analyze-and-improve"></a>Analisar e melhorar

Saiba o que os usuários dizem ao conversar com o bot. Este será um processo contínuo e iterativo, à medida que a sua base de usuários crescer em diferentes locais e organizações. Você pode ajustar o mapeamento de intenção e reconhecimento de linguagem do bot com o Microsoft Language Understanding (LUIS).

* [Funcionamento do LUIS](/azure/cognitive-services/luis/artificial-intelligence): Descubra como o LUIS usa inteligência artificial para fornecer uma compreensão de linguagem natural (CLN) aos dados do aplicativo.
* [Integração com o LUIS](https://www.luis.ai/): adicione recursos de linguagem natural ao seu bot sem o processo complexo de criação de modelos de aprendizado de máquina.

## <a name="use-cases"></a>Casos de uso

### <a name="simple-queries"></a>Consultas simples

Os bots podem fornecer uma correspondência exata de uma consulta ou um grupo de correspondências relacionadas para ajudar com a desambiguação. Para ver as correspondências relacionadas, agrupe o conteúdo usando um cartão da lista.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-simple-query.png" alt-text="Exemplo mostrando uma interação de consulta simples com um bot." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-simple-query.png" alt-text="Exemplo mostra uma interação de consulta simples com um bot no celular." border="false":::

---

### <a name="multi-turn-interactions"></a>Interações de várias etapas

Embora o seu bot possa dar suporte a solicitações e perguntas completas, ele também deve ser capaz de lidar com interações de várias etapas. Prever as próximas etapas possíveis torna muito mais fácil criar um fluxo de tarefas completo para as pessoas (em vez de esperar que elas criem uma única solicitação abrangente).

Nos exemplos a seguir, o bot responde a cada mensagem com opções para o que pode querer fazer em seguida.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-multi-turn.png" alt-text="Exemplo mostrando uma interação de várias etapas com um bot." border="false":::


# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-multi-turn.png" alt-text="Exemplo mostra uma interação de várias voltas com um bot no celular." border="false":::


---

### <a name="reach-out-to-users"></a>Fale com os usuários

Com um sistema de mensagens proativo, seu bot pode atuar como um resumo que envia notificações relevantes para uma pessoa, chat em grupo ou canal com uma frequência específica. Um bot pode enviar uma mensagem quando houver alterações em um documento ou um item de trabalho for fechado.

# <a name="desktop"></a>[Desktop](#tab/desktop)

No exemplo a seguir, o usuário recebe uma notificação de

:::image type="content" source="../../assets/images/bots/bot-proactive-message-toast.png" alt-text="Exemplo mostrando uma notificação do sistema de um bot enviando mensagens proativamente a um usuário de outro canal." border="false":::

Nesse canal, o usuário pode ler a mensagem por meio do bot.

:::image type="content" source="../../assets/images/bots/bot-proactive-message.png" alt-text="Exemplo mostrando o usuário observando a mensagem proativa do bot." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

No exemplo a seguir, o usuário recebe uma notificação de que um bot os recebeu em outro canal.

:::image type="content" source="../../assets/images/bots/mobile-bot-proactive-message-toast.png" alt-text="Exemplo mostra um sistema de mensagens de um bot de forma proativa de um usuário de outro canal no celular." border="false":::

Nesse canal, o usuário pode ler a mensagem por meio do bot.

:::image type="content" source="../../assets/images/bots/mobile-bot-proactive-message.png" alt-text="Exemplo mostra o usuário olhando para a mensagem proativa do bot no celular." border="false":::

---

### <a name="use-tabs-with-bots"></a>Usar guias com bots

Em aplicativos pessoais, uma guia pode complementar o que seu bot pode fazer. Por exemplo, se o bot puder criar itens de trabalho, será bom mostrar todos esses itens em um local central dentro de uma guia. Saiba mais sobre [criação de guias](../../tabs/design/tabs.md).

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-with-tab.png" alt-text="Exemplo mostrando como uma guia pode ajudar a organizar o conteúdo do bot." border="false":::

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-with-tab.png" alt-text="Exemplo mostra como uma guia pode ajudar a organizar o conteúdo do bot no celular." border="false":::

---

## <a name="manage-a-bot"></a>Gerenciar um bot

Os usuários devem ser capazes de alterar as configurações de um bot. Você pode fornecer essa funcionalidade com comandos de bot, mas geralmente é mais eficiente incluir todas as configurações em um [módulo de tarefas](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) (como mostra o exemplo a seguir).

:::image type="content" source="../../assets/images/bots/manage-bot-task-module.png" alt-text="Exemplo mostrando um módulo de tarefas para definir as configurações de um bot." border="false":::

## <a name="best-practices"></a>Práticas recomendadas

Use essas recomendações para criar uma experiência de aplicativo de qualidade.

### <a name="content"></a>Conteúdo

:::image type="content" source="../../assets/images/bots/bot-content-persona-do.png" alt-text="Exemplo mostrando uma prática prática de bot para estabelecer uma persona clara." border="false":::

#### <a name="do-establish-a-clear-persona"></a>Estabeleça uma personalidade bem definida

O tom do bot é leve e amigável, focando "apenas em fatos", ou é mais peculiar? Como ele deve responder em diferentes cenários? Planejar e documentar a personalidade do seu bot facilita escrever respostas que pareçam naturais e coesas.

Saiba mais sobre como escrever para bots no <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Kit de Interface do Usuário do Microsoft Teams (Figma).</a>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-do.png" alt-text="Exemplo mostrando para transmitir claramente o que seu bot pode fazer." border="false":::

#### <a name="do-clearly-convey-what-your-bot-can-do"></a>Transmita claramente o que o bot pode fazer

Mensagens de boas-vindas e tours ajudam as pessoas a entender o que elas podem fazer com o bot.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-dont.png" alt-text="Exemplo mostrando para não obscurecer os recursos do bot." border="false":::

#### <a name="dont-obscure-your-bots-features"></a>Não oculte os recursos do bot

A primeira impressão é importante. As pessoas provavelmente ficarão confusas ou desconfiadas quando receberem uma mensagem de logon indefinida.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-do.png" alt-text="Exemplo mostrando que seu bot deve reconhecer não perguntas." border="false":::

#### <a name="do-recognize-non-questions"></a>Reconheça mensagens que não são perguntas

Seu bot deve ser capaz de responder a mensagens como "Olá", "Ajuda" e "Obrigado", além de levar em conta erros comuns de ortografia e coloquialismos.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-dont.png" alt-text="Exemplo mostrando que você deve evitar respostas desastradas a mensagens de bot simples." border="false":::

#### <a name="dont-miss-out-on-opportunities-to-delight"></a>Não perca oportunidades de agradar

Algumas pessoas esperam que as conversas fluam naturalmente, como com uma pessoa real. Tente evitar respostas insvasas a mensagens simples.

   :::column-end:::
:::row-end:::

### <a name="troubleshooting"></a>Solução de problemas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-do.png" alt-text="Exemplo mostrando bots deve ajudar os usuários a entender como usar bots." border="false":::

#### <a name="do-provide-help"></a>Forneça ajuda

Se o bot não puder atender a uma solicitação, forneça maneiras de o usuário se instruir sobre a interação com o bot.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-dont.png" alt-text="Exemplo mostrando que seu bot não deve deixar os usuários encalhados." border="false":::

#### <a name="dont-leave-users-stranded"></a>Não deixe os usuários desamparados

As pessoas abandonarão o bot rapidamente se não puderem solucionar problemas.

   :::column-end:::
:::row-end:::

### <a name="complex-interactions"></a>Interações complexas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-do.png" alt-text="Exemplo mostrando que você pode usar módulos de tarefa ou guias com seu bot para interações complexas." border="false":::

#### <a name="do-use-task-modules-or-tabs"></a>Use guias ou módulos de tarefa

Se o bot fornece uma resposta que exige algumas etapas adicionais, você pode incluir links para um módulo de tarefa ou uma guia para concluir a tarefa ou fluxo.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-dont.png" alt-text="Exemplo mostrando como seu bot deve evitar interações de várias voltas." border="false":::

#### <a name="dont-make-multi-turn-interactions-tedious"></a>Não torne as interações em várias etapas entediantes

Ter uma longa conversa para concluir uma única tarefa é algo lento e complexo demais. Isso também exige que o desenvolvedor tenha em conta as alterações de status (por exemplo, a conversa expirar ou você enviar uma mensagem para "Cancelar").

   :::column-end:::
:::row-end:::

### <a name="privacy"></a>Privacidade

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-do.png" alt-text="Exemplo mostrando como os bots só devem mostrar informações privadas em um contexto pessoal." border="false":::

#### <a name="do-only-show-sensitive-info-in-a-personal-context"></a>Somente mostre informações confidenciais em um contexto pessoal

Se o bot estiver em um chat em grupo ou canal, recomendamos direcionar os usuários para um local privado (como um módulo de tarefas, uma guia ou um navegador) para exibir informações confidenciais.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-dont.png" alt-text="Exemplo mostrando como os bots não devem revelar informações confidenciais para um grupo ou pessoas." border="false":::

#### <a name="dont-some-content-isnt-meant-to-be-seen-by-everyone"></a>Alguns conteúdos não devem ser vistos por todos

O bot não deve revelar informações confidenciais para um grupo de pessoas.

   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Confira também

Estas outras diretrizes podem ajudar com a criação do seu bot:

* [Criar seu aplicativo pessoal](../../concepts/design/personal-apps.md)
* [Criar Cartões Adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md)
* [Criar módulos de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
