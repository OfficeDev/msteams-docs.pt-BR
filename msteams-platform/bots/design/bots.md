---
title: Projetando o bot
description: Saiba como criar um bot do Teams e obter o kit de interface do usuário do Microsoft Teams.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: d1a7470f4986de22ecca7071823b620cb0234abb
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605360"
---
# <a name="designing-your-microsoft-teams-bot"></a>Projetando seu bot do Microsoft Teams

Bots são aplicativos de conversa que executam um conjunto específico de tarefas. Com base na <a href="https://dev.botframework.com/" target="_blank">Microsoft bot Framework</a>, os bots se comunicam com os usuários, respondem às suas perguntas e os notificam proativamente sobre alterações e outros eventos. Eles são uma ótima maneira de entrar.

Para guiar o design do aplicativo, as informações a seguir descrevem e ilustra como as pessoas podem adicionar, usar e gerenciar bots no Teams.

## <a name="microsoft-teams-ui-kit"></a>Kit de interface do usuário do Microsoft Teams

Você pode encontrar diretrizes de design de bot mais abrangentes, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams.

> [!div class="nextstepaction"]
> [Obter o kit de interface do usuário do Microsoft Teams (figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-bot"></a>Adicionar um bot

Os bots estão disponíveis em bate-papos, canais e aplicativos pessoais. Você pode adicionar um bot de uma das seguintes maneiras:

* No repositório do Teams (AppSource).
* Usando o submenu do aplicativo selecionando o ícone **mais** no lado esquerdo do teams.
* Com um @mention na nova caixa de chat ou redação (o exemplo a seguir mostra como você pode fazer isso em um chat de grupo).

:::image type="content" source="../../assets/images/bots/add-bot-chat-at-mention.png" alt-text="O exemplo mostra como adicionar um bot em um chat de grupo usando um @mention." border="false":::

## <a name="introduce-a-bot"></a>Introduzir um bot

É fundamental que seu bot apresente a si próprio e descreve o que ele pode fazer. Este intercâmbio inicial ajuda as pessoas a entenderem o que fazer com o bot, descobrir suas limitações e, o que é mais importante, se sentir confortável para interagir com ela.

### <a name="welcome-message-in-a-one-on-one-chat"></a>Mensagem de boas-vindas em um chat de um em um

Em contextos pessoais, as mensagens de boas-vindas definem o tom do seu bot. A mensagem inclui uma saudação, o que o bot pode fazer e algumas sugestões de como interagir (por exemplo, "tente me perguntar sobre..."). Se possível, essas sugestões devem retornar as respostas armazenadas sem ter que fazer logon.

:::image type="content" source="../../assets/images/bots/bot-personal-welcome.png" alt-text="O exemplo mostra uma introdução de bot em um aplicativo pessoal." border="false":::

### <a name="introductions-in-group-chats-and-channels"></a>Introduções no grupo chats e canais

A introdução do seu bot deve ser ligeiramente pouco diferente em conversas de grupo e canais em comparação a um contexto pessoal (como um aplicativo pessoal). Na vida real, se você inseriu uma sala cheia de pessoas; Você se apresentasse em vez de boas-vindas para todos os que já estão lá. Leve isso em seu design de bot.

:::image type="content" source="../../assets/images/bots/bot-group-welcome.png" alt-text="O exemplo mostra uma introdução de bot em um contexto colaborativo." border="false":::

### <a name="bot-authentication-with-single-sign-on"></a>Autenticação de bot com logon único

Quando uma pessoa mensagens um bot, a entrada pode ser necessária para usar todos os seus recursos. Você pode simplificar o processo de autenticação usando o logon único (SSO).

Não se esqueça: no menu de comando do bot (**o que posso fazer?**), você também deve fornecer um comando para sair.

:::image type="content" source="../../assets/images/bots/bot-sso-example.png" alt-text="O exemplo mostra um bot com um botão de entrada." border="false":::

### <a name="tours"></a>Viagens

Você pode incluir um tour com mensagens de boas-vindas e, se o bot responder algo como um comando "Help". Um Tour é a maneira mais eficaz de descrever o que o seu bot pode fazer. Se aplicável, eles também são ótimos para descrever os outros recursos do aplicativo (por exemplo, inclua capturas de tela de sua extensão de mensagens).

> [!IMPORTANT]
> Os Tours devem estar acessíveis sem que seja necessário fazer logon.

#### <a name="one-on-one-chats"></a>Chats de um em um

Em um aplicativo pessoal, um carrossel pode fornecer uma visão geral eficaz do seu bot e de quaisquer outros recursos do seu aplicativo. Incluindo botões os comandos permitir que os usuários tentem bot são incentivados (por exemplo, **criar uma tarefa**).

:::image type="content" source="../../assets/images/bots/bot-tour-personal.png" alt-text="O exemplo mostra um tour de bot em um chat de um em um." border="false":::

#### <a name="channels-and-group-chats"></a>Canais e bate-papos de grupo

Em canais e bate-papos de grupo, um tour deve ser aberto em uma janela restrita (também conhecida como [módulo de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) , para que não interrompa as conversas em andamento. Isso também oferece a opção de implementar modos de exibição baseados em função para o seu tour.

:::image type="content" source="../../assets/images/bots/bot-tour-channel.png" alt-text="O exemplo mostra um tour de bot em um canal." border="false":::

## <a name="chat-with-a-bot"></a>Bater papo com um bot

Os bots integram-se diretamente à estrutura de mensagens da equipe. Os usuários podem bater papo com um bot para fazer suas perguntas responder ou digitar comandos para que o bot execute um conjunto estreito ou específico de tarefas. Os bots podem notificar os usuários sobre alterações ou atualizações no seu aplicativo proativamente por meio de chat.

### <a name="chat-with-a-bot-in-different-contexts"></a>Bater papo com um bot em contextos diferentes

Você pode usar bots nos seguintes contextos:

* **Aplicativos pessoais**: em um aplicativo pessoal, um bot tem uma guia de chat dedicada.
* **Chat de um em um**: um usuário pode iniciar uma conversa privada com um bot. É a mesma experiência que o uso de um bot em um aplicativo pessoal.
* **Chat de grupo**: as pessoas podem interagir com um bot em um chat de grupo @mentioning o bot.
* **Canal**: as pessoas podem interagir com um bot em um canal. @mentioning o nome do bot na caixa de composição. Lembre-se, nesse contexto, o bot está disponível para toda a equipe, não apenas o canal.

### <a name="anatomy"></a>Anatomia

:::image type="content" source="../../assets/images/bots/bot-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um bot." border="false":::

|Contador|Descrição|
|----------|-----------|
|1|**Nome do aplicativo e ícone**|
|2 |**Guia chat**: abre o espaço para falar com o bot (aplicável somente a aplicativos pessoais).|
|3 |**Guias personalizadas**: abre outro conteúdo relacionado ao seu aplicativo.|
|4 |**Guia sobre**: exibe informações básicas sobre o aplicativo.|
|5 |**Bolha de chat**: conversas de bot usam a estrutura de mensagens do teams.|
|6 |**Cartão adaptável**: se as respostas de seu bot incluem cartões adaptáveis, o cartão ocupa a largura total da bolha de chat.|
|7 |**Menu de comando**: exibe os comandos padrão do seu bot (definidos por você).

### <a name="command-menu"></a>Menu de comando

O menu de comando fornece uma lista de palavras ou frases às quais você deseja que seu bot sempre responda. O menu de comando é exibido acima da caixa de composição quando alguém está convertendo com um bot. Quando um comando é selecionado, ele é inserido em uma mensagem.

A lista de comandos deve ser resumida. O menu só deve realçar os recursos principais do bot. Mantenha os comandos conciso também. Por exemplo, crie um comando chamado **ajuda** em vez de **você pode me ajudar**?
O menu de comando deve estar sempre disponível independentemente do estado da conversa.

:::image type="content" source="../../assets/images/bots/bot-command-menu.png" alt-text="O exemplo mostra o menu de comando de um bot." border="false":::

## <a name="understand-what-people-are-saying"></a>Entender o que as pessoas estão dizendo

Use um dicionário de sinônimos e obtenha às pessoas o máximo de diferentes planos de fundo possíveis para ajudá-lo a gerar diferentes interpretações de consultas padrão.

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-hello.png" alt-text="Ilustração que mostra como um bot pode interpretar ' Olá '." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-help.png" alt-text="Ilustração mostrando como um bot pode interpretar &quot;Help&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-thanks.png" alt-text="Ilustração mostrando como um bot pode interpretar ' thanks '." border="false":::
   :::column-end:::
:::row-end:::

### <a name="extract-intent-and-data-from-messages"></a>Extrair tentativas e dados de mensagens

Crie seu bot para reconhecer o objetivo, que captura o que alguém deseja de um bot em resposta a uma mensagem ou consulta. A intenção classifica uma mensagem ou consulta como uma ação única com um ou mais objetos de dados afetados pela ação. 

Os exemplos a seguir descrevem a tentativa de usuário e os dados nas mensagens enviadas para bots.

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-1.png" alt-text="O exemplo mostrado na sentença ' Book a voo para Seattle ', a intenção de usuário é ' agendar um vôo ' e os dados são ' Seattle '." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-2.png" alt-text="O exemplo mostrado na sentença ' When The Store Open ', User intuito é ' When ' e data é ' Open '." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-3.png" alt-text="Exemplo mostrado na frase &quot;agendar uma reunião no 1pm com Bob na distribuição&quot;, a intenção de usuário é &quot;agendar uma reunião&quot; e os dados são &quot;1pm&quot; e &quot;Bob in Distribution&quot;." border="false":::
   :::column-end:::
:::row-end:::

### <a name="analyze-and-improve"></a>Analisar e aprimorar

Saiba o que os usuários dizem ao bater papo com seu bot. Este será um processo contínuo e iterativo à medida que a sua base de usuários cresce em diferentes locais e organizações expandidas. Você pode ajustar o reconhecimento de idioma do bot e o mapeamento de intenções com o Microsoft Language Understanding (LUIS).

* [Understanding Luis](https://docs.microsoft.com/azure/cognitive-services/luis/artificial-intelligence): Descubra como o Luis usa o ai para fornecer a compreensão da linguagem natural (NLU) para seus dados de aplicativo.
* [Integração com o Luis](https://www.luis.ai/): adicionar recursos de linguagem natural ao bot sem o processo complexo de criação de modelos de aprendizado de máquina.

## <a name="use-cases"></a>Casos de uso

### <a name="simple-queries"></a>Consultas simples

Os bots podem fornecer uma correspondência exata a uma consulta ou um grupo de correspondências relacionadas para ajudar com a desambigüidade. Para correspondências relacionadas, agrupe o conteúdo usando um cartão de lista.

:::image type="content" source="../../assets/images/bots/bot-simple-query.png" alt-text="O exemplo mostra uma interação de consulta simples com um bot." border="false":::

### <a name="multi-turn-interactions"></a>Interações de múltipla opção

Embora o seu bot possa dar suporte a solicitações e perguntas completas, ele também deve ser capaz de lidar com interações de múltipla opção. A previsão de possíveis etapas a seguir torna muito mais fácil para as pessoas um fluxo de tarefas completo (em vez de esperar que eles criem uma solicitação abrangente).

No exemplo a seguir, o bot responde a cada mensagem com opções para o que convém fazer em seguida.

:::image type="content" source="../../assets/images/bots/bot-multi-turn.png" alt-text="O exemplo mostra uma interação de múltipla opção com um bot." border="false":::

### <a name="reach-out-to-users"></a>Acessar os usuários

Com o sistema de mensagens proativo, seu bot pode atuar como um resumo que envia notificações relevantes a um indivíduo, chat de grupo ou canal em uma frequência específica. Um bot pode enviar uma mensagem quando algo foi alterado em um documento ou um item de trabalho é fechado.

No exemplo a seguir, um usuário recebe uma notificação de notificação de que um bot o Messageou em outro canal.

:::image type="content" source="../../assets/images/bots/bot-proactive-message-toast.png" alt-text="O exemplo mostra um sistema de mensagens de um bot proativamente enviar um usuário de outro canal." border="false":::

Agora, nesse canal, o usuário pode ler a mensagem no bot.

:::image type="content" source="../../assets/images/bots/bot-proactive-message.png" alt-text="O exemplo mostra o usuário examinando a mensagem pró-ativa do bot." border="false":::

### <a name="use-tabs-with-bots"></a>Usar guias com bots

Uma guia pode facilitar o uso do bot. Por exemplo, se o seu bot pode criar itens de trabalho, seria ótimo mostrar todos esses itens em um local central dentro de uma guia. Veja mais sobre a [criação de guias](../../tabs/design/tabs.md).

:::image type="content" source="../../assets/images/bots/bot-with-tab.png" alt-text="O exemplo mostra como uma guia pode ajudar a organizar o conteúdo do bot." border="false":::

## <a name="manage-a-bot"></a>Gerenciar um bot

Os usuários devem ser capazes de alterar as configurações de um bot. Você pode fornecer essa funcionalidade com comandos de bot, mas geralmente é mais eficiente incluir todas as configurações em um [módulo de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) (conforme mostrado no exemplo a seguir).

:::image type="content" source="../../assets/images/bots/manage-bot-task-module.png" alt-text="O exemplo mostra um módulo de tarefa para definir as configurações de um bot." border="false":::

## <a name="best-practices"></a>Práticas recomendadas

### <a name="content"></a>Conteúdo

:::image type="content" source="../../assets/images/bots/bot-content-persona-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-establish-a-clear-persona"></a>Fazer: estabelecer um persona claro

O tom do seu bot é amigável e claro, "apenas os fatos" ou a mais peculiaridade? Como ele responderá em diferentes cenários? Planejar e documentar o persona do seu bot facilita a gravação de respostas que pareçam naturais e coesas.

Veja mais sobre gravação de bots no <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Kit de interface do usuário do Microsoft Teams (figma).</a>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-clearly-convey-what-your-bot-can-do"></a>Fazer: transmitir claramente o que o seu bot pode fazer

As mensagens e os tours de boas-vindas ajudam as pessoas a entender o que podem fazer com seu bot.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-dont.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="dont-obscure-your-bots-features"></a>Não: obscurecer os recursos de seu bot

As primeiras impressões são importantes. As pessoas provavelmente serão confundidas ou suspeitas quando forem apresentadas com uma mensagem de entrada do nondescript.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-recognize-non-questions"></a>Fazer: reconhecer não perguntas

Seu bot deve ser capaz de responder a mensagens como "Hi", "Help" e "Thanks" e, ao mesmo tempo, fazer o acompanhamento de erros comuns de ortografia e coloquialismos.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-dont.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="dont-miss-out-on-opportunities-to-delight"></a>Não: perder oportunidades para encantarão

Algumas pessoas esperam que as conversas fluam naturalmente como fariam com uma pessoa real. Tente evitar respostas Clumsy a mensagens simples.

   :::column-end:::
:::row-end:::

### <a name="troubleshooting"></a>Solução de problemas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-provide-help"></a>Fazer: fornecer ajuda

Se o seu bot não puder atender a uma solicitação, forneça maneiras de um usuário se instruir a interagir com o bot.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-dont.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="dont-leave-users-stranded"></a>Não: deixar usuários perdidos

As pessoas irão abandonar o bot rapidamente se não puderem solucionar problemas.

   :::column-end:::
:::row-end:::

### <a name="complex-interactions"></a>Interações complexas

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-use-task-modules-or-tabs"></a>Fazer: usar guias ou módulos de tarefas

Se o seu bot fornecer uma resposta que exija algumas etapas adicionais, você poderá vincular a um módulo de tarefa ou guia para concluir a tarefa ou o fluxo.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-dont.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="dont-make-multi-turn-interactions-tedious"></a>Não: tornar as interações de múltipla volta tediosas

Uma conversa abrangente para concluir uma única tarefa é lenta e muito complexa. Também exige que o desenvolvedor Confira as alterações de estado (como o tempo de duração da conversa ou você envia uma mensagem "Cancelar").

   :::column-end:::
:::row-end:::

### <a name="privacy"></a>Privacidade

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-only-show-sensitive-info-in-a-personal-context"></a>Fazer: mostrar apenas informações confidenciais em um contexto pessoal

Se o seu bot estiver em um canal ou chat de grupo, recomendamos direcionar os usuários para um local privado (como um módulo de tarefa, guia ou navegador) para exibir informações confidenciais.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-dont.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="dont-some-content-isnt-meant-to-be-seen-by-everyone"></a>Não: alguns conteúdos não devem ser vistos por todos

O bot deve revelar informações confidenciais para um grupo de pessoas.

   :::column-end:::
:::row-end:::

## <a name="learn-more"></a>Saiba mais

Essas outras diretrizes podem ajudá-lo com o design de bot:

* [Criando seu aplicativo pessoal](../../concepts/design/personal-apps.md)
* [Design de cartões adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md)
* [Criando módulos de tarefas](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)

## <a name="validate-your-design"></a>Validar o design

Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.

> [!div class="nextstepaction"]
> [Verificar diretrizes de validação de design](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
