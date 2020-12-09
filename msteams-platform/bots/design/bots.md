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
# <a name="designing-your-microsoft-teams-bot"></a><span data-ttu-id="dba65-103">Projetando seu bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="dba65-103">Designing your Microsoft Teams bot</span></span>

<span data-ttu-id="dba65-104">Bots são aplicativos de conversa que executam um conjunto específico de tarefas.</span><span class="sxs-lookup"><span data-stu-id="dba65-104">Bots are conversational apps that perform a specific set of tasks.</span></span> <span data-ttu-id="dba65-105">Com base na <a href="https://dev.botframework.com/" target="_blank">Microsoft bot Framework</a>, os bots se comunicam com os usuários, respondem às suas perguntas e os notificam proativamente sobre alterações e outros eventos.</span><span class="sxs-lookup"><span data-stu-id="dba65-105">Based on the <a href="https://dev.botframework.com/" target="_blank">Microsoft Bot Framework</a>, bots communicate with users, respond to their questions, and proactively notify them about changes and other events.</span></span> <span data-ttu-id="dba65-106">Eles são uma ótima maneira de entrar.</span><span class="sxs-lookup"><span data-stu-id="dba65-106">They're a great way to reach out.</span></span>

<span data-ttu-id="dba65-107">Para guiar o design do aplicativo, as informações a seguir descrevem e ilustra como as pessoas podem adicionar, usar e gerenciar bots no Teams.</span><span class="sxs-lookup"><span data-stu-id="dba65-107">To guide your app design, the following information describes and illustrates how people can add, use, and manage bots in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="dba65-108">Kit de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="dba65-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="dba65-109">Você pode encontrar diretrizes de design de bot mais abrangentes, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="dba65-109">You can find more comprehensive bot design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dba65-110">Obter o kit de interface do usuário do Microsoft Teams (figma)</span><span class="sxs-lookup"><span data-stu-id="dba65-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-bot"></a><span data-ttu-id="dba65-111">Adicionar um bot</span><span class="sxs-lookup"><span data-stu-id="dba65-111">Add a bot</span></span>

<span data-ttu-id="dba65-112">Os bots estão disponíveis em bate-papos, canais e aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="dba65-112">Bots are available in chats, channels, and personal apps.</span></span> <span data-ttu-id="dba65-113">Você pode adicionar um bot de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="dba65-113">You can add a bot one of the following ways:</span></span>

* <span data-ttu-id="dba65-114">No repositório do Teams (AppSource).</span><span class="sxs-lookup"><span data-stu-id="dba65-114">From the Teams store (AppSource).</span></span>
* <span data-ttu-id="dba65-115">Usando o submenu do aplicativo selecionando o ícone **mais** no lado esquerdo do teams.</span><span class="sxs-lookup"><span data-stu-id="dba65-115">Using the app flyout by selecting the **More** icon on the left side of Teams.</span></span>
* <span data-ttu-id="dba65-116">Com um @mention na nova caixa de chat ou redação (o exemplo a seguir mostra como você pode fazer isso em um chat de grupo).</span><span class="sxs-lookup"><span data-stu-id="dba65-116">With an @mention in the new chat or compose box (the following example shows how you can do this in a group chat).</span></span>

:::image type="content" source="../../assets/images/bots/add-bot-chat-at-mention.png" alt-text="O exemplo mostra como adicionar um bot em um chat de grupo usando um @mention." border="false":::

## <a name="introduce-a-bot"></a><span data-ttu-id="dba65-118">Introduzir um bot</span><span class="sxs-lookup"><span data-stu-id="dba65-118">Introduce a bot</span></span>

<span data-ttu-id="dba65-119">É fundamental que seu bot apresente a si próprio e descreve o que ele pode fazer.</span><span class="sxs-lookup"><span data-stu-id="dba65-119">It’s critical that your bot introduces itself and describes what it can do.</span></span> <span data-ttu-id="dba65-120">Este intercâmbio inicial ajuda as pessoas a entenderem o que fazer com o bot, descobrir suas limitações e, o que é mais importante, se sentir confortável para interagir com ela.</span><span class="sxs-lookup"><span data-stu-id="dba65-120">This initial exchange helps people understand what to do with the bot, find out its limitations and, most importantly, get comfortable interacting with it.</span></span>

### <a name="welcome-message-in-a-one-on-one-chat"></a><span data-ttu-id="dba65-121">Mensagem de boas-vindas em um chat de um em um</span><span class="sxs-lookup"><span data-stu-id="dba65-121">Welcome message in a one-on-one chat</span></span>

<span data-ttu-id="dba65-122">Em contextos pessoais, as mensagens de boas-vindas definem o tom do seu bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-122">In personal contexts, welcome messages set your bot's tone.</span></span> <span data-ttu-id="dba65-123">A mensagem inclui uma saudação, o que o bot pode fazer e algumas sugestões de como interagir (por exemplo, "tente me perguntar sobre...").</span><span class="sxs-lookup"><span data-stu-id="dba65-123">The message includes a greeting, what the bot can do, and some suggestions for how to interact (for example, “Try asking me about …”).</span></span> <span data-ttu-id="dba65-124">Se possível, essas sugestões devem retornar as respostas armazenadas sem ter que fazer logon.</span><span class="sxs-lookup"><span data-stu-id="dba65-124">If possible, these suggestions should return stored responses without having to sign in.</span></span>

:::image type="content" source="../../assets/images/bots/bot-personal-welcome.png" alt-text="O exemplo mostra uma introdução de bot em um aplicativo pessoal." border="false":::

### <a name="introductions-in-group-chats-and-channels"></a><span data-ttu-id="dba65-126">Introduções no grupo chats e canais</span><span class="sxs-lookup"><span data-stu-id="dba65-126">Introductions in group chats and channels</span></span>

<span data-ttu-id="dba65-127">A introdução do seu bot deve ser ligeiramente pouco diferente em conversas de grupo e canais em comparação a um contexto pessoal (como um aplicativo pessoal).</span><span class="sxs-lookup"><span data-stu-id="dba65-127">Your bot's introduction should be slightly little different in group chats and channels compared to a personal context (like a personal app).</span></span> <span data-ttu-id="dba65-128">Na vida real, se você inseriu uma sala cheia de pessoas; Você se apresentasse em vez de boas-vindas para todos os que já estão lá.</span><span class="sxs-lookup"><span data-stu-id="dba65-128">In real life, if you entered a room full of people; you’d introduce yourself instead of welcoming everyone who’s already there.</span></span> <span data-ttu-id="dba65-129">Leve isso em seu design de bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-129">Carry that thinking into your bot design.</span></span>

:::image type="content" source="../../assets/images/bots/bot-group-welcome.png" alt-text="O exemplo mostra uma introdução de bot em um contexto colaborativo." border="false":::

### <a name="bot-authentication-with-single-sign-on"></a><span data-ttu-id="dba65-131">Autenticação de bot com logon único</span><span class="sxs-lookup"><span data-stu-id="dba65-131">Bot authentication with single sign-on</span></span>

<span data-ttu-id="dba65-132">Quando uma pessoa mensagens um bot, a entrada pode ser necessária para usar todos os seus recursos.</span><span class="sxs-lookup"><span data-stu-id="dba65-132">When a person messages a bot, sign in may be required use all its features.</span></span> <span data-ttu-id="dba65-133">Você pode simplificar o processo de autenticação usando o logon único (SSO).</span><span class="sxs-lookup"><span data-stu-id="dba65-133">You can simplify the authentication process using single sign-on (SSO).</span></span>

<span data-ttu-id="dba65-134">Não se esqueça: no menu de comando do bot (**o que posso fazer?**), você também deve fornecer um comando para sair.</span><span class="sxs-lookup"><span data-stu-id="dba65-134">Don’t forget: In the bot command menu (**What can I do?**), you must also provide a command to sign out.</span></span>

:::image type="content" source="../../assets/images/bots/bot-sso-example.png" alt-text="O exemplo mostra um bot com um botão de entrada." border="false":::

### <a name="tours"></a><span data-ttu-id="dba65-136">Viagens</span><span class="sxs-lookup"><span data-stu-id="dba65-136">Tours</span></span>

<span data-ttu-id="dba65-137">Você pode incluir um tour com mensagens de boas-vindas e, se o bot responder algo como um comando "Help".</span><span class="sxs-lookup"><span data-stu-id="dba65-137">You can include a tour with welcome messages and if the bot responds to something like a “help” command.</span></span> <span data-ttu-id="dba65-138">Um Tour é a maneira mais eficaz de descrever o que o seu bot pode fazer.</span><span class="sxs-lookup"><span data-stu-id="dba65-138">A tour is the most effective way to describe what your bot can do.</span></span> <span data-ttu-id="dba65-139">Se aplicável, eles também são ótimos para descrever os outros recursos do aplicativo (por exemplo, inclua capturas de tela de sua extensão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="dba65-139">If applicable, they’re also great for describing your app’s other features (for example, include screenshots of your messaging extension).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dba65-140">Os Tours devem estar acessíveis sem que seja necessário fazer logon.</span><span class="sxs-lookup"><span data-stu-id="dba65-140">Tours should be accessible without having to sign in.</span></span>

#### <a name="one-on-one-chats"></a><span data-ttu-id="dba65-141">Chats de um em um</span><span class="sxs-lookup"><span data-stu-id="dba65-141">One-on-one chats</span></span>

<span data-ttu-id="dba65-142">Em um aplicativo pessoal, um carrossel pode fornecer uma visão geral eficaz do seu bot e de quaisquer outros recursos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dba65-142">In a personal app, a carousel can provide an effective overview of your bot and any other features of your app.</span></span> <span data-ttu-id="dba65-143">Incluindo botões os comandos permitir que os usuários tentem bot são incentivados (por exemplo, **criar uma tarefa**).</span><span class="sxs-lookup"><span data-stu-id="dba65-143">Including buttons the let users try bot commands is encouraged (for example, **Create a task**).</span></span>

:::image type="content" source="../../assets/images/bots/bot-tour-personal.png" alt-text="O exemplo mostra um tour de bot em um chat de um em um." border="false":::

#### <a name="channels-and-group-chats"></a><span data-ttu-id="dba65-145">Canais e bate-papos de grupo</span><span class="sxs-lookup"><span data-stu-id="dba65-145">Channels and group chats</span></span>

<span data-ttu-id="dba65-146">Em canais e bate-papos de grupo, um tour deve ser aberto em uma janela restrita (também conhecida como [módulo de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) , para que não interrompa as conversas em andamento.</span><span class="sxs-lookup"><span data-stu-id="dba65-146">In channels and group chats, a tour should open in a modal (also known as a [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) so it doesn’t interrupt ongoing conversations.</span></span> <span data-ttu-id="dba65-147">Isso também oferece a opção de implementar modos de exibição baseados em função para o seu tour.</span><span class="sxs-lookup"><span data-stu-id="dba65-147">This also gives you the option to implement role-based views for your tour.</span></span>

:::image type="content" source="../../assets/images/bots/bot-tour-channel.png" alt-text="O exemplo mostra um tour de bot em um canal." border="false":::

## <a name="chat-with-a-bot"></a><span data-ttu-id="dba65-149">Bater papo com um bot</span><span class="sxs-lookup"><span data-stu-id="dba65-149">Chat with a bot</span></span>

<span data-ttu-id="dba65-150">Os bots integram-se diretamente à estrutura de mensagens da equipe.</span><span class="sxs-lookup"><span data-stu-id="dba65-150">Bots integrate directly into Team’s messaging framework.</span></span> <span data-ttu-id="dba65-151">Os usuários podem bater papo com um bot para fazer suas perguntas responder ou digitar comandos para que o bot execute um conjunto estreito ou específico de tarefas.</span><span class="sxs-lookup"><span data-stu-id="dba65-151">Users can chat with a bot to get their questions answered or type commands to have the bot perform a narrow or specific set of tasks.</span></span> <span data-ttu-id="dba65-152">Os bots podem notificar os usuários sobre alterações ou atualizações no seu aplicativo proativamente por meio de chat.</span><span class="sxs-lookup"><span data-stu-id="dba65-152">Bots can proactively notify users about changes or updates to your app via chat.</span></span>

### <a name="chat-with-a-bot-in-different-contexts"></a><span data-ttu-id="dba65-153">Bater papo com um bot em contextos diferentes</span><span class="sxs-lookup"><span data-stu-id="dba65-153">Chat with a bot in different contexts</span></span>

<span data-ttu-id="dba65-154">Você pode usar bots nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="dba65-154">You can use bots in the following contexts:</span></span>

* <span data-ttu-id="dba65-155">**Aplicativos pessoais**: em um aplicativo pessoal, um bot tem uma guia de chat dedicada.</span><span class="sxs-lookup"><span data-stu-id="dba65-155">**Personal apps**: In a personal app, a bot has a dedicated chat tab.</span></span>
* <span data-ttu-id="dba65-156">**Chat de um em um**: um usuário pode iniciar uma conversa privada com um bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-156">**One-on-one chat**: A user can initiate a private conversation with a bot.</span></span> <span data-ttu-id="dba65-157">É a mesma experiência que o uso de um bot em um aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="dba65-157">It's the same experience as using a bot in a personal app.</span></span>
* <span data-ttu-id="dba65-158">**Chat de grupo**: as pessoas podem interagir com um bot em um chat de grupo @mentioning o bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-158">**Group chat**: People can interact with a bot in a group chat by @mentioning the bot.</span></span>
* <span data-ttu-id="dba65-159">**Canal**: as pessoas podem interagir com um bot em um canal.</span><span class="sxs-lookup"><span data-stu-id="dba65-159">**Channel**: People can interact with a bot in a channel.</span></span> <span data-ttu-id="dba65-160">@mentioning o nome do bot na caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="dba65-160">by @mentioning the bot name in the compose box.</span></span> <span data-ttu-id="dba65-161">Lembre-se, nesse contexto, o bot está disponível para toda a equipe, não apenas o canal.</span><span class="sxs-lookup"><span data-stu-id="dba65-161">Remember, in this context, the bot is available to the entire team, not just the channel.</span></span>

### <a name="anatomy"></a><span data-ttu-id="dba65-162">Anatomia</span><span class="sxs-lookup"><span data-stu-id="dba65-162">Anatomy</span></span>

:::image type="content" source="../../assets/images/bots/bot-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um bot." border="false":::

|<span data-ttu-id="dba65-164">Contador</span><span class="sxs-lookup"><span data-stu-id="dba65-164">Counter</span></span>|<span data-ttu-id="dba65-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="dba65-165">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="dba65-166">1</span><span class="sxs-lookup"><span data-stu-id="dba65-166">1</span></span>|<span data-ttu-id="dba65-167">**Nome do aplicativo e ícone**</span><span class="sxs-lookup"><span data-stu-id="dba65-167">**App name and icon**</span></span>|
|<span data-ttu-id="dba65-168">2 </span><span class="sxs-lookup"><span data-stu-id="dba65-168">2</span></span>|<span data-ttu-id="dba65-169">**Guia chat**: abre o espaço para falar com o bot (aplicável somente a aplicativos pessoais).</span><span class="sxs-lookup"><span data-stu-id="dba65-169">**Chat tab**: Opens the space to talk with your bot (applicable only to personal apps).</span></span>|
|<span data-ttu-id="dba65-170">3 </span><span class="sxs-lookup"><span data-stu-id="dba65-170">3</span></span>|<span data-ttu-id="dba65-171">**Guias personalizadas**: abre outro conteúdo relacionado ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dba65-171">**Custom tabs**: Opens other content related to your app.</span></span>|
|<span data-ttu-id="dba65-172">4 </span><span class="sxs-lookup"><span data-stu-id="dba65-172">4</span></span>|<span data-ttu-id="dba65-173">**Guia sobre**: exibe informações básicas sobre o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dba65-173">**About tab**: Displays basic information about your app.</span></span>|
|<span data-ttu-id="dba65-174">5 </span><span class="sxs-lookup"><span data-stu-id="dba65-174">5</span></span>|<span data-ttu-id="dba65-175">**Bolha de chat**: conversas de bot usam a estrutura de mensagens do teams.</span><span class="sxs-lookup"><span data-stu-id="dba65-175">**Chat bubble**: Bot conversations use the Teams messaging framework.</span></span>|
|<span data-ttu-id="dba65-176">6 </span><span class="sxs-lookup"><span data-stu-id="dba65-176">6</span></span>|<span data-ttu-id="dba65-177">**Cartão adaptável**: se as respostas de seu bot incluem cartões adaptáveis, o cartão ocupa a largura total da bolha de chat.</span><span class="sxs-lookup"><span data-stu-id="dba65-177">**Adaptive Card**: If your bot’s responses include Adaptive Cards, the card takes up the full width of the chat bubble.</span></span>|
|<span data-ttu-id="dba65-178">7 </span><span class="sxs-lookup"><span data-stu-id="dba65-178">7</span></span>|<span data-ttu-id="dba65-179">**Menu de comando**: exibe os comandos padrão do seu bot (definidos por você).</span><span class="sxs-lookup"><span data-stu-id="dba65-179">**Command menu**: Displays your bot's standard commands (defined by you).</span></span>

### <a name="command-menu"></a><span data-ttu-id="dba65-180">Menu de comando</span><span class="sxs-lookup"><span data-stu-id="dba65-180">Command menu</span></span>

<span data-ttu-id="dba65-181">O menu de comando fornece uma lista de palavras ou frases às quais você deseja que seu bot sempre responda.</span><span class="sxs-lookup"><span data-stu-id="dba65-181">The command menu provides a list of words or phrases you want your bot to always respond to.</span></span> <span data-ttu-id="dba65-182">O menu de comando é exibido acima da caixa de composição quando alguém está convertendo com um bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-182">The command menu displays above the compose box when someone is conversing with a bot.</span></span> <span data-ttu-id="dba65-183">Quando um comando é selecionado, ele é inserido em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="dba65-183">When a command is selected, it gets inserted into a message.</span></span>

<span data-ttu-id="dba65-184">A lista de comandos deve ser resumida.</span><span class="sxs-lookup"><span data-stu-id="dba65-184">The list of commands should be brief.</span></span> <span data-ttu-id="dba65-185">O menu só deve realçar os recursos principais do bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-185">The menu is only meant to highlight your bot’s primary features.</span></span> <span data-ttu-id="dba65-186">Mantenha os comandos conciso também.</span><span class="sxs-lookup"><span data-stu-id="dba65-186">Keep commands concise, too.</span></span> <span data-ttu-id="dba65-187">Por exemplo, crie um comando chamado **ajuda** em vez de **você pode me ajudar**?</span><span class="sxs-lookup"><span data-stu-id="dba65-187">For example, create a command called **Help** instead of **Can you please help me**?</span></span>
<span data-ttu-id="dba65-188">O menu de comando deve estar sempre disponível independentemente do estado da conversa.</span><span class="sxs-lookup"><span data-stu-id="dba65-188">The command menu must always be available regardless of the state of the conversation.</span></span>

:::image type="content" source="../../assets/images/bots/bot-command-menu.png" alt-text="O exemplo mostra o menu de comando de um bot." border="false":::

## <a name="understand-what-people-are-saying"></a><span data-ttu-id="dba65-190">Entender o que as pessoas estão dizendo</span><span class="sxs-lookup"><span data-stu-id="dba65-190">Understand what people are saying</span></span>

<span data-ttu-id="dba65-191">Use um dicionário de sinônimos e obtenha às pessoas o máximo de diferentes planos de fundo possíveis para ajudá-lo a gerar diferentes interpretações de consultas padrão.</span><span class="sxs-lookup"><span data-stu-id="dba65-191">Use a thesaurus and get people from as many different backgrounds as possible to help you generate different interpretations of standard queries.</span></span>

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

### <a name="extract-intent-and-data-from-messages"></a><span data-ttu-id="dba65-195">Extrair tentativas e dados de mensagens</span><span class="sxs-lookup"><span data-stu-id="dba65-195">Extract intent and data from messages</span></span>

<span data-ttu-id="dba65-196">Crie seu bot para reconhecer o objetivo, que captura o que alguém deseja de um bot em resposta a uma mensagem ou consulta.</span><span class="sxs-lookup"><span data-stu-id="dba65-196">Design your bot to recognize intent, which captures what someone wants from a bot in response to a message or query.</span></span> <span data-ttu-id="dba65-197">A intenção classifica uma mensagem ou consulta como uma ação única com um ou mais objetos de dados afetados pela ação.</span><span class="sxs-lookup"><span data-stu-id="dba65-197">Intent classifies a message or query as a single action with one or more data objects that are affected by the action.</span></span> 

<span data-ttu-id="dba65-198">Os exemplos a seguir descrevem a tentativa de usuário e os dados nas mensagens enviadas para bots.</span><span class="sxs-lookup"><span data-stu-id="dba65-198">The following examples outline the user intent and data in messages sent to bots.</span></span>

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

### <a name="analyze-and-improve"></a><span data-ttu-id="dba65-202">Analisar e aprimorar</span><span class="sxs-lookup"><span data-stu-id="dba65-202">Analyze and improve</span></span>

<span data-ttu-id="dba65-203">Saiba o que os usuários dizem ao bater papo com seu bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-203">Learn what users say when chatting with your bot.</span></span> <span data-ttu-id="dba65-204">Este será um processo contínuo e iterativo à medida que a sua base de usuários cresce em diferentes locais e organizações expandidas.</span><span class="sxs-lookup"><span data-stu-id="dba65-204">This will be an ongoing, iterative process as your user base grows in different locations and orgs.</span></span> <span data-ttu-id="dba65-205">Você pode ajustar o reconhecimento de idioma do bot e o mapeamento de intenções com o Microsoft Language Understanding (LUIS).</span><span class="sxs-lookup"><span data-stu-id="dba65-205">You can tune your bot's language recognition and intent mapping with Microsoft Language Understanding (LUIS).</span></span>

* <span data-ttu-id="dba65-206">[Understanding Luis](https://docs.microsoft.com/azure/cognitive-services/luis/artificial-intelligence): Descubra como o Luis usa o ai para fornecer a compreensão da linguagem natural (NLU) para seus dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dba65-206">[Understanding LUIS](https://docs.microsoft.com/azure/cognitive-services/luis/artificial-intelligence): Find out how LUIS uses AI to provide natural language understanding (NLU) to your app data.</span></span>
* <span data-ttu-id="dba65-207">[Integração com o Luis](https://www.luis.ai/): adicionar recursos de linguagem natural ao bot sem o processo complexo de criação de modelos de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="dba65-207">[Integrating with LUIS](https://www.luis.ai/): Add natural language capabilities to your bot without the complex process of creating machine learning models.</span></span>

## <a name="use-cases"></a><span data-ttu-id="dba65-208">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="dba65-208">Use cases</span></span>

### <a name="simple-queries"></a><span data-ttu-id="dba65-209">Consultas simples</span><span class="sxs-lookup"><span data-stu-id="dba65-209">Simple queries</span></span>

<span data-ttu-id="dba65-210">Os bots podem fornecer uma correspondência exata a uma consulta ou um grupo de correspondências relacionadas para ajudar com a desambigüidade.</span><span class="sxs-lookup"><span data-stu-id="dba65-210">Bots can deliver an exact match to a query or a group of related matches to help with disambiguation.</span></span> <span data-ttu-id="dba65-211">Para correspondências relacionadas, agrupe o conteúdo usando um cartão de lista.</span><span class="sxs-lookup"><span data-stu-id="dba65-211">For related matches, group the content using a list card.</span></span>

:::image type="content" source="../../assets/images/bots/bot-simple-query.png" alt-text="O exemplo mostra uma interação de consulta simples com um bot." border="false":::

### <a name="multi-turn-interactions"></a><span data-ttu-id="dba65-213">Interações de múltipla opção</span><span class="sxs-lookup"><span data-stu-id="dba65-213">Multi-turn interactions</span></span>

<span data-ttu-id="dba65-214">Embora o seu bot possa dar suporte a solicitações e perguntas completas, ele também deve ser capaz de lidar com interações de múltipla opção.</span><span class="sxs-lookup"><span data-stu-id="dba65-214">While your bot can support complete requests and questions, it should also be able to handle multi-turn interactions.</span></span> <span data-ttu-id="dba65-215">A previsão de possíveis etapas a seguir torna muito mais fácil para as pessoas um fluxo de tarefas completo (em vez de esperar que eles criem uma solicitação abrangente).</span><span class="sxs-lookup"><span data-stu-id="dba65-215">Anticipating possible next steps makes it much easier for people to a complete task flow (rather than expecting them to craft a comprehensive request).</span></span>

<span data-ttu-id="dba65-216">No exemplo a seguir, o bot responde a cada mensagem com opções para o que convém fazer em seguida.</span><span class="sxs-lookup"><span data-stu-id="dba65-216">In the following example, the bot responds to each message with options for what might want to do next.</span></span>

:::image type="content" source="../../assets/images/bots/bot-multi-turn.png" alt-text="O exemplo mostra uma interação de múltipla opção com um bot." border="false":::

### <a name="reach-out-to-users"></a><span data-ttu-id="dba65-218">Acessar os usuários</span><span class="sxs-lookup"><span data-stu-id="dba65-218">Reach out to users</span></span>

<span data-ttu-id="dba65-219">Com o sistema de mensagens proativo, seu bot pode atuar como um resumo que envia notificações relevantes a um indivíduo, chat de grupo ou canal em uma frequência específica.</span><span class="sxs-lookup"><span data-stu-id="dba65-219">With proactive messaging, your bot can act like a digest that sends notifications relevant to an individual, group chat, or channel at a specific frequency.</span></span> <span data-ttu-id="dba65-220">Um bot pode enviar uma mensagem quando algo foi alterado em um documento ou um item de trabalho é fechado.</span><span class="sxs-lookup"><span data-stu-id="dba65-220">A bot may send a message when something has changed in a document or a work item is closed.</span></span>

<span data-ttu-id="dba65-221">No exemplo a seguir, um usuário recebe uma notificação de notificação de que um bot o Messageou em outro canal.</span><span class="sxs-lookup"><span data-stu-id="dba65-221">In the following example, a user gets a toast notification that a bot messaged them in another channel.</span></span>

:::image type="content" source="../../assets/images/bots/bot-proactive-message-toast.png" alt-text="O exemplo mostra um sistema de mensagens de um bot proativamente enviar um usuário de outro canal." border="false":::

<span data-ttu-id="dba65-223">Agora, nesse canal, o usuário pode ler a mensagem no bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-223">Now in that channel, the user can read their message from the bot.</span></span>

:::image type="content" source="../../assets/images/bots/bot-proactive-message.png" alt-text="O exemplo mostra o usuário examinando a mensagem pró-ativa do bot." border="false":::

### <a name="use-tabs-with-bots"></a><span data-ttu-id="dba65-225">Usar guias com bots</span><span class="sxs-lookup"><span data-stu-id="dba65-225">Use tabs with bots</span></span>

<span data-ttu-id="dba65-226">Uma guia pode facilitar o uso do bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-226">A tab can make your bot easier to use.</span></span> <span data-ttu-id="dba65-227">Por exemplo, se o seu bot pode criar itens de trabalho, seria ótimo mostrar todos esses itens em um local central dentro de uma guia. Veja mais sobre a [criação de guias](../../tabs/design/tabs.md).</span><span class="sxs-lookup"><span data-stu-id="dba65-227">For example, if your bot can create work items, it would be nice to show all those items in a central location inside a tab. See more about [designing tabs](../../tabs/design/tabs.md).</span></span>

:::image type="content" source="../../assets/images/bots/bot-with-tab.png" alt-text="O exemplo mostra como uma guia pode ajudar a organizar o conteúdo do bot." border="false":::

## <a name="manage-a-bot"></a><span data-ttu-id="dba65-229">Gerenciar um bot</span><span class="sxs-lookup"><span data-stu-id="dba65-229">Manage a bot</span></span>

<span data-ttu-id="dba65-230">Os usuários devem ser capazes de alterar as configurações de um bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-230">Users should be able to change a bot's settings.</span></span> <span data-ttu-id="dba65-231">Você pode fornecer essa funcionalidade com comandos de bot, mas geralmente é mais eficiente incluir todas as configurações em um [módulo de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) (conforme mostrado no exemplo a seguir).</span><span class="sxs-lookup"><span data-stu-id="dba65-231">You can provide this functionality with bot commands, but it's usually more efficient to include all settings in a [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) (as shown in the following example).</span></span>

:::image type="content" source="../../assets/images/bots/manage-bot-task-module.png" alt-text="O exemplo mostra um módulo de tarefa para definir as configurações de um bot." border="false":::

## <a name="best-practices"></a><span data-ttu-id="dba65-233">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="dba65-233">Best practices</span></span>

### <a name="content"></a><span data-ttu-id="dba65-234">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="dba65-234">Content</span></span>

:::image type="content" source="../../assets/images/bots/bot-content-persona-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-establish-a-clear-persona"></a><span data-ttu-id="dba65-236">Fazer: estabelecer um persona claro</span><span class="sxs-lookup"><span data-stu-id="dba65-236">Do: Establish a clear persona</span></span>

<span data-ttu-id="dba65-237">O tom do seu bot é amigável e claro, "apenas os fatos" ou a mais peculiaridade?</span><span class="sxs-lookup"><span data-stu-id="dba65-237">Is your bot's tone friendly and light, “just the facts”, or super quirky?</span></span> <span data-ttu-id="dba65-238">Como ele responderá em diferentes cenários?</span><span class="sxs-lookup"><span data-stu-id="dba65-238">How should it respond in different scenarios?</span></span> <span data-ttu-id="dba65-239">Planejar e documentar o persona do seu bot facilita a gravação de respostas que pareçam naturais e coesas.</span><span class="sxs-lookup"><span data-stu-id="dba65-239">Planning and documenting your bot's persona makes it easier to write responses that seem natural and cohesive.</span></span>

<span data-ttu-id="dba65-240">Veja mais sobre gravação de bots no <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Kit de interface do usuário do Microsoft Teams (figma).</a></span><span class="sxs-lookup"><span data-stu-id="dba65-240">See more about writing for bots in the <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a></span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-clearly-convey-what-your-bot-can-do"></a><span data-ttu-id="dba65-242">Fazer: transmitir claramente o que o seu bot pode fazer</span><span class="sxs-lookup"><span data-stu-id="dba65-242">Do: Clearly convey what your bot can do</span></span>

<span data-ttu-id="dba65-243">As mensagens e os tours de boas-vindas ajudam as pessoas a entender o que podem fazer com seu bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-243">Welcome messages and tours help people understand what they can do with your bot.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-dont.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="dont-obscure-your-bots-features"></a><span data-ttu-id="dba65-245">Não: obscurecer os recursos de seu bot</span><span class="sxs-lookup"><span data-stu-id="dba65-245">Don't: Obscure your bot's features</span></span>

<span data-ttu-id="dba65-246">As primeiras impressões são importantes.</span><span class="sxs-lookup"><span data-stu-id="dba65-246">First impressions matter.</span></span> <span data-ttu-id="dba65-247">As pessoas provavelmente serão confundidas ou suspeitas quando forem apresentadas com uma mensagem de entrada do nondescript.</span><span class="sxs-lookup"><span data-stu-id="dba65-247">People will likely be confused or suspicious when presented with a nondescript sign-in message.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-recognize-non-questions"></a><span data-ttu-id="dba65-249">Fazer: reconhecer não perguntas</span><span class="sxs-lookup"><span data-stu-id="dba65-249">Do: Recognize non-questions</span></span>

<span data-ttu-id="dba65-250">Seu bot deve ser capaz de responder a mensagens como "Hi", "Help" e "Thanks" e, ao mesmo tempo, fazer o acompanhamento de erros comuns de ortografia e coloquialismos.</span><span class="sxs-lookup"><span data-stu-id="dba65-250">Your bot should be able to respond to messages like "Hi", "Help", and "Thanks" while also accounting for common misspellings and colloquialisms.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-dont.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="dont-miss-out-on-opportunities-to-delight"></a><span data-ttu-id="dba65-252">Não: perder oportunidades para encantarão</span><span class="sxs-lookup"><span data-stu-id="dba65-252">Don't: Miss out on opportunities to delight</span></span>

<span data-ttu-id="dba65-253">Algumas pessoas esperam que as conversas fluam naturalmente como fariam com uma pessoa real.</span><span class="sxs-lookup"><span data-stu-id="dba65-253">Some people expect conversations to flow naturally like they would with a real person.</span></span> <span data-ttu-id="dba65-254">Tente evitar respostas Clumsy a mensagens simples.</span><span class="sxs-lookup"><span data-stu-id="dba65-254">Try to avoid clumsy responses to simple messages.</span></span>

   :::column-end:::
:::row-end:::

### <a name="troubleshooting"></a><span data-ttu-id="dba65-255">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="dba65-255">Troubleshooting</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-provide-help"></a><span data-ttu-id="dba65-257">Fazer: fornecer ajuda</span><span class="sxs-lookup"><span data-stu-id="dba65-257">Do: Provide help</span></span>

<span data-ttu-id="dba65-258">Se o seu bot não puder atender a uma solicitação, forneça maneiras de um usuário se instruir a interagir com o bot.</span><span class="sxs-lookup"><span data-stu-id="dba65-258">If your bot can’t satisfy a request, provide ways for a user to educate themselves about interacting with your bot.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-dont.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="dont-leave-users-stranded"></a><span data-ttu-id="dba65-260">Não: deixar usuários perdidos</span><span class="sxs-lookup"><span data-stu-id="dba65-260">Don't: Leave users stranded</span></span>

<span data-ttu-id="dba65-261">As pessoas irão abandonar o bot rapidamente se não puderem solucionar problemas.</span><span class="sxs-lookup"><span data-stu-id="dba65-261">People will quickly abandon your bot if they can’t troubleshoot issues.</span></span>

   :::column-end:::
:::row-end:::

### <a name="complex-interactions"></a><span data-ttu-id="dba65-262">Interações complexas</span><span class="sxs-lookup"><span data-stu-id="dba65-262">Complex interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-use-task-modules-or-tabs"></a><span data-ttu-id="dba65-264">Fazer: usar guias ou módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="dba65-264">Do: Use task modules or tabs</span></span>

<span data-ttu-id="dba65-265">Se o seu bot fornecer uma resposta que exija algumas etapas adicionais, você poderá vincular a um módulo de tarefa ou guia para concluir a tarefa ou o fluxo.</span><span class="sxs-lookup"><span data-stu-id="dba65-265">If your bot provides an answer that requires a few more steps, you can link to a task module or tab to complete the task or flow.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-dont.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="dont-make-multi-turn-interactions-tedious"></a><span data-ttu-id="dba65-267">Não: tornar as interações de múltipla volta tediosas</span><span class="sxs-lookup"><span data-stu-id="dba65-267">Don't: Make multi-turn interactions tedious</span></span>

<span data-ttu-id="dba65-268">Uma conversa abrangente para concluir uma única tarefa é lenta e muito complexa.</span><span class="sxs-lookup"><span data-stu-id="dba65-268">An extensive conversation to complete a single task is slow and overly complex.</span></span> <span data-ttu-id="dba65-269">Também exige que o desenvolvedor Confira as alterações de estado (como o tempo de duração da conversa ou você envia uma mensagem "Cancelar").</span><span class="sxs-lookup"><span data-stu-id="dba65-269">It also requires the developer to account for state changes (such as the conversation timing out or you sending a “Cancel” message).</span></span>

   :::column-end:::
:::row-end:::

### <a name="privacy"></a><span data-ttu-id="dba65-270">Privacidade</span><span class="sxs-lookup"><span data-stu-id="dba65-270">Privacy</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-do.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="do-only-show-sensitive-info-in-a-personal-context"></a><span data-ttu-id="dba65-272">Fazer: mostrar apenas informações confidenciais em um contexto pessoal</span><span class="sxs-lookup"><span data-stu-id="dba65-272">Do: Only show sensitive info in a personal context</span></span>

<span data-ttu-id="dba65-273">Se o seu bot estiver em um canal ou chat de grupo, recomendamos direcionar os usuários para um local privado (como um módulo de tarefa, guia ou navegador) para exibir informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="dba65-273">If your bot is in a group chat or channel, we recommend directing users to a private location (such as a task module, tab, or browser) to view sensitive information.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-dont.png" alt-text="Exemplo mostrando uma prática recomendada de bot." border="false":::

#### <a name="dont-some-content-isnt-meant-to-be-seen-by-everyone"></a><span data-ttu-id="dba65-275">Não: alguns conteúdos não devem ser vistos por todos</span><span class="sxs-lookup"><span data-stu-id="dba65-275">Don't: Some content isn’t meant to be seen by everyone</span></span>

<span data-ttu-id="dba65-276">O bot deve revelar informações confidenciais para um grupo de pessoas.</span><span class="sxs-lookup"><span data-stu-id="dba65-276">Your bot shouldn’t reveal sensitive information to a group of people.</span></span>

   :::column-end:::
:::row-end:::

## <a name="learn-more"></a><span data-ttu-id="dba65-277">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="dba65-277">Learn more</span></span>

<span data-ttu-id="dba65-278">Essas outras diretrizes podem ajudá-lo com o design de bot:</span><span class="sxs-lookup"><span data-stu-id="dba65-278">These other guidelines may help with your bot design:</span></span>

* [<span data-ttu-id="dba65-279">Criando seu aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="dba65-279">Designing your personal app</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="dba65-280">Design de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="dba65-280">Designing Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)
* [<span data-ttu-id="dba65-281">Criando módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="dba65-281">Designing task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)

## <a name="validate-your-design"></a><span data-ttu-id="dba65-282">Validar o design</span><span class="sxs-lookup"><span data-stu-id="dba65-282">Validate your design</span></span>

<span data-ttu-id="dba65-283">Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.</span><span class="sxs-lookup"><span data-stu-id="dba65-283">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dba65-284">Verificar diretrizes de validação de design</span><span class="sxs-lookup"><span data-stu-id="dba65-284">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
