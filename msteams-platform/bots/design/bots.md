---
title: Criar um bot
description: Saiba como criar um bot do Microsoft Teams e obter o Kit de Interface do Usuário do Microsoft Teams.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 2739bd4baaf68be90a62924601b0628c3d9b0f2c
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020130"
---
# <a name="designing-your-microsoft-teams-bot"></a><span data-ttu-id="0c770-103">Criar um bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0c770-103">Designing your Microsoft Teams bot</span></span>

<span data-ttu-id="0c770-104">Bots são aplicativos de conversa que executam um conjunto específico de tarefas.</span><span class="sxs-lookup"><span data-stu-id="0c770-104">Bots are conversational apps that perform a specific set of tasks.</span></span> <span data-ttu-id="0c770-105">Com base no <a href="https://dev.botframework.com/" target="_blank">Microsoft Bot Framework</a>, os bots se comunicam com os usuários, respondem às suas dúvidas e os notificam de forma proativa sobre alterações e outros eventos.</span><span class="sxs-lookup"><span data-stu-id="0c770-105">Based on the <a href="https://dev.botframework.com/" target="_blank">Microsoft Bot Framework</a>, bots communicate with users, respond to their questions, and proactively notify them about changes and other events.</span></span> <span data-ttu-id="0c770-106">Eles são uma ótima maneira de se comunicar.</span><span class="sxs-lookup"><span data-stu-id="0c770-106">They're a great way to reach out.</span></span>

<span data-ttu-id="0c770-107">Para orientar a criação do seu aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar bots no Mirosoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0c770-107">To guide your app design, the following information describes and illustrates how people can add, use, and manage bots in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="0c770-108">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0c770-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="0c770-109">No Kit de Interface do Usuário do Microsoft Teams, você encontra diretrizes de design de bot mais abrangentes, incluindo elementos que você pode modificar conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="0c770-109">You can find more comprehensive bot design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0c770-110">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="0c770-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-bot"></a><span data-ttu-id="0c770-111">Adicionar um bot</span><span class="sxs-lookup"><span data-stu-id="0c770-111">Add a bot</span></span>

<span data-ttu-id="0c770-112">Os bots estão disponíveis em chats, canais e aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="0c770-112">Bots are available in chats, channels, and personal apps.</span></span> <span data-ttu-id="0c770-113">É possível fazer isso por uma das formas a seguir:</span><span class="sxs-lookup"><span data-stu-id="0c770-113">You can add a bot one of the following ways:</span></span>

* <span data-ttu-id="0c770-114">A partir da loja do Microsoft Teams (AppSource).</span><span class="sxs-lookup"><span data-stu-id="0c770-114">From the Teams store (AppSource).</span></span>
* <span data-ttu-id="0c770-115">Use o submenu do aplicativo selecionando o ícone **Mais** no lado esquerdo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0c770-115">Using the app flyout by selecting the **More** icon on the left side of Teams.</span></span>
* <span data-ttu-id="0c770-116">Com uma @menção na nova caixa de chat ou de texto (o exemplo a seguir mostra como fazer isso em um chat em grupo).</span><span class="sxs-lookup"><span data-stu-id="0c770-116">With an @mention in the new chat or compose box (the following example shows how you can do this in a group chat).</span></span>

:::image type="content" source="../../assets/images/bots/add-bot-chat-at-mention.png" alt-text="Exemplo mostrando como adicionar um bot em um chat em grupo usando uma @menção." border="false":::

## <a name="introduce-a-bot"></a><span data-ttu-id="0c770-118">Apresentar um bot</span><span class="sxs-lookup"><span data-stu-id="0c770-118">Introduce a bot</span></span>

<span data-ttu-id="0c770-119">É fundamental que o bot se apresente e descreva o que ele pode fazer.</span><span class="sxs-lookup"><span data-stu-id="0c770-119">It’s critical that your bot introduces itself and describes what it can do.</span></span> <span data-ttu-id="0c770-120">Essa troca inicial ajuda as pessoas a entenderem o que fazer com o bot, a descobrirem suas limitações e, o mais importante, a se sentirem à vontade para interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="0c770-120">This initial exchange helps people understand what to do with the bot, find out its limitations and, most importantly, get comfortable interacting with it.</span></span>

### <a name="welcome-message-in-a-one-on-one-chat"></a><span data-ttu-id="0c770-121">Mensagem de boas-vindas em um chat entre duas pessoas</span><span class="sxs-lookup"><span data-stu-id="0c770-121">Welcome message in a one-on-one chat</span></span>

<span data-ttu-id="0c770-122">No contexto pessoal, as mensagens de boas-vindas definem o tom do bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-122">In personal contexts, welcome messages set your bot's tone.</span></span> <span data-ttu-id="0c770-123">A mensagem inclui uma saudação, o que o bot pode fazer e algumas sugestões sobre como interagir (por exemplo, "Tente perguntar sobre...").</span><span class="sxs-lookup"><span data-stu-id="0c770-123">The message includes a greeting, what the bot can do, and some suggestions for how to interact (for example, “Try asking me about …”).</span></span> <span data-ttu-id="0c770-124">Se possível, essas sugestões devem retornar respostas armazenadas sem que o usuário precise se conectar.</span><span class="sxs-lookup"><span data-stu-id="0c770-124">If possible, these suggestions should return stored responses without having to sign in.</span></span>

:::image type="content" source="../../assets/images/bots/bot-personal-welcome.png" alt-text="Exemplo mostrando a apresentação de um bot em um aplicativo pessoal." border="false":::

### <a name="introductions-in-group-chats-and-channels"></a><span data-ttu-id="0c770-126">Apresentações em chats e canais em grupo</span><span class="sxs-lookup"><span data-stu-id="0c770-126">Introductions in group chats and channels</span></span>

<span data-ttu-id="0c770-127">A apresentação do bot deve ser um pouco diferente em chats e canais em grupo em comparação com um contexto pessoal (como um aplicativo pessoal).</span><span class="sxs-lookup"><span data-stu-id="0c770-127">Your bot's introduction should be slightly different in group chats and channels compared to a personal context (like a personal app).</span></span> <span data-ttu-id="0c770-128">Na vida real, ao entrar em uma sala cheia de pessoas, você se apresenta, em vez de dar boas-vindas a todos que já estão lá.</span><span class="sxs-lookup"><span data-stu-id="0c770-128">In real life, if you entered a room full of people; you’d introduce yourself instead of welcoming everyone who’s already there.</span></span> <span data-ttu-id="0c770-129">Utilize esse raciocínio ao criar o bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-129">Carry that thinking into your bot design.</span></span>

:::image type="content" source="../../assets/images/bots/bot-group-welcome.png" alt-text="Exemplo mostrando a apresentação de um bot em um contexto colaborativo." border="false":::

### <a name="bot-authentication-with-single-sign-on"></a><span data-ttu-id="0c770-131">Autenticação de bot de logon único</span><span class="sxs-lookup"><span data-stu-id="0c770-131">Bot authentication with single sign-on</span></span>

<span data-ttu-id="0c770-132">Ao enviar uma mensagem a um bot, pode ser necessário se conectar para usar todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="0c770-132">When a person messages a bot, sign in may be required use all its features.</span></span> <span data-ttu-id="0c770-133">Você pode simplificar o processo de autenticação usando o SSO (logon único).</span><span class="sxs-lookup"><span data-stu-id="0c770-133">You can simplify the authentication process using single sign-on (SSO).</span></span>

<span data-ttu-id="0c770-134">Não se esqueça: no menu de comandos do bot (**O que posso fazer?**), você também deve fornecer um comando para sair.</span><span class="sxs-lookup"><span data-stu-id="0c770-134">Don’t forget: In the bot command menu (**What can I do?**), you must also provide a command to sign out.</span></span>

:::image type="content" source="../../assets/images/bots/bot-sso-example.png" alt-text="Exemplo mostrando um bot com um botão de logon." border="false":::

### <a name="tours"></a><span data-ttu-id="0c770-136">Tours</span><span class="sxs-lookup"><span data-stu-id="0c770-136">Tours</span></span>

<span data-ttu-id="0c770-137">Você pode incluir um tour com mensagens de boas-vindas e se o bot responder a algo como um comando de "ajuda".</span><span class="sxs-lookup"><span data-stu-id="0c770-137">You can include a tour with welcome messages and if the bot responds to something like a “help” command.</span></span> <span data-ttu-id="0c770-138">Um tour é a maneira mais eficaz de descrever o que o bot pode fazer.</span><span class="sxs-lookup"><span data-stu-id="0c770-138">A tour is the most effective way to describe what your bot can do.</span></span> <span data-ttu-id="0c770-139">Se for o caso, tours também são ótimos para descrever os outros recursos do aplicativo (por exemplo, incluir capturas de tela da sua extensão de mensagem).</span><span class="sxs-lookup"><span data-stu-id="0c770-139">If applicable, they’re also great for describing your app’s other features (for example, include screenshots of your messaging extension).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c770-140">Os tours devem estar acessíveis sem que o usuário precise se conectar.</span><span class="sxs-lookup"><span data-stu-id="0c770-140">Tours should be accessible without having to sign in.</span></span>

#### <a name="one-on-one-chats"></a><span data-ttu-id="0c770-141">Chats entre duas pessoas</span><span class="sxs-lookup"><span data-stu-id="0c770-141">One-on-one chats</span></span>

<span data-ttu-id="0c770-142">Em um aplicativo pessoal, um carrossel pode fornecer uma visão geral eficaz do bot e de todos os outros recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0c770-142">In a personal app, a carousel can provide an effective overview of your bot and any other features of your app.</span></span> <span data-ttu-id="0c770-143">Incluir botões para permitir que os usuários experimentem os comandos do bot é uma boa ideia (por exemplo, **Criar uma tarefa**).</span><span class="sxs-lookup"><span data-stu-id="0c770-143">Including buttons the let users try bot commands is encouraged (for example, **Create a task**).</span></span>

:::image type="content" source="../../assets/images/bots/bot-tour-personal.png" alt-text="Exemplo mostrando um tour de bot em um chat entre duas pessoas." border="false":::

#### <a name="channels-and-group-chats"></a><span data-ttu-id="0c770-145">Canais e chats em grupo</span><span class="sxs-lookup"><span data-stu-id="0c770-145">Channels and group chats</span></span>

<span data-ttu-id="0c770-146">Em canais e chats em grupo, o tour deve ser aberto em um modal (também conhecido como [módulo de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) para não interromper conversas em andamento.</span><span class="sxs-lookup"><span data-stu-id="0c770-146">In channels and group chats, a tour should open in a modal (also known as a [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) so it doesn’t interrupt ongoing conversations.</span></span> <span data-ttu-id="0c770-147">Isso também oferece a opção de implementar exibições baseadas em função para o tour.</span><span class="sxs-lookup"><span data-stu-id="0c770-147">This also gives you the option to implement role-based views for your tour.</span></span>

:::image type="content" source="../../assets/images/bots/bot-tour-channel.png" alt-text="Exemplo mostrando um tour de bot em um canal." border="false":::

## <a name="chat-with-a-bot"></a><span data-ttu-id="0c770-149">Conversar por chat com um bot</span><span class="sxs-lookup"><span data-stu-id="0c770-149">Chat with a bot</span></span>

<span data-ttu-id="0c770-150">Os bots integram-se diretamente na estrutura de mensagens do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0c770-150">Bots integrate directly into Team’s messaging framework.</span></span> <span data-ttu-id="0c770-151">Os usuários podem conversar com um bot para obter respostas às suas perguntas ou digitar comandos para que o bot execute um conjunto específico ou restrito de tarefas.</span><span class="sxs-lookup"><span data-stu-id="0c770-151">Users can chat with a bot to get their questions answered or type commands to have the bot perform a narrow or specific set of tasks.</span></span> <span data-ttu-id="0c770-152">Os bots podem notificar proativamente os usuários sobre alterações ou atualizações do aplicativo via chat.</span><span class="sxs-lookup"><span data-stu-id="0c770-152">Bots can proactively notify users about changes or updates to your app via chat.</span></span>

### <a name="chat-with-a-bot-in-different-contexts"></a><span data-ttu-id="0c770-153">Conversar por chat com um bot em outros contextos</span><span class="sxs-lookup"><span data-stu-id="0c770-153">Chat with a bot in different contexts</span></span>

<span data-ttu-id="0c770-154">Você pode usar bots nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="0c770-154">You can use bots in the following contexts:</span></span>

* <span data-ttu-id="0c770-155">**Aplicativos pessoais**: em aplicativos pessoais, os bots têm guias de chat dedicadas.</span><span class="sxs-lookup"><span data-stu-id="0c770-155">**Personal apps**: In a personal app, a bot has a dedicated chat tab.</span></span>
* <span data-ttu-id="0c770-156">**Chat entre duas pessoas**: um usuário pode iniciar uma conversa privada com um bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-156">**One-on-one chat**: A user can initiate a private conversation with a bot.</span></span> <span data-ttu-id="0c770-157">É a mesma experiência que usar um bot em um aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="0c770-157">It's the same experience as using a bot in a personal app.</span></span>
* <span data-ttu-id="0c770-158">**Chat em grupo**: as pessoas podem interagir com um bot em um chat em grupo @mencionando o bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-158">**Group chat**: People can interact with a bot in a group chat by @mentioning the bot.</span></span>
* <span data-ttu-id="0c770-159">**Canal**: As pessoas podem interagir com um bot em um canal.</span><span class="sxs-lookup"><span data-stu-id="0c770-159">**Channel**: People can interact with a bot in a channel.</span></span> <span data-ttu-id="0c770-160">@mencionando o nome do bot na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="0c770-160">by @mentioning the bot name in the compose box.</span></span> <span data-ttu-id="0c770-161">Lembre-se de que, nesse contexto, o bot está disponível para toda a equipe, não apenas para o canal.</span><span class="sxs-lookup"><span data-stu-id="0c770-161">Remember, in this context, the bot is available to the entire team, not just the channel.</span></span>

### <a name="anatomy"></a><span data-ttu-id="0c770-162">Anatomia</span><span class="sxs-lookup"><span data-stu-id="0c770-162">Anatomy</span></span>

:::image type="content" source="../../assets/images/bots/bot-anatomy.png" alt-text="Exemplo mostrando a anatomia estrutural de um bot." border="false":::

|<span data-ttu-id="0c770-164">Contador</span><span class="sxs-lookup"><span data-stu-id="0c770-164">Counter</span></span>|<span data-ttu-id="0c770-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c770-165">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="0c770-166">1</span><span class="sxs-lookup"><span data-stu-id="0c770-166">1</span></span>|<span data-ttu-id="0c770-167">**Ícone e nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="0c770-167">**App name and icon**</span></span>|
|<span data-ttu-id="0c770-168">2</span><span class="sxs-lookup"><span data-stu-id="0c770-168">2</span></span>|<span data-ttu-id="0c770-169">**Guia de chat**: abre o espaço para falar com o bot (somente em aplicativos pessoais).</span><span class="sxs-lookup"><span data-stu-id="0c770-169">**Chat tab**: Opens the space to talk with your bot (applicable only to personal apps).</span></span>|
|<span data-ttu-id="0c770-170">3</span><span class="sxs-lookup"><span data-stu-id="0c770-170">3</span></span>|<span data-ttu-id="0c770-171">**Guias personalizadas**: abre outros conteúdos relacionados ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0c770-171">**Custom tabs**: Opens other content related to your app.</span></span>|
|<span data-ttu-id="0c770-172">4 </span><span class="sxs-lookup"><span data-stu-id="0c770-172">4</span></span>|<span data-ttu-id="0c770-173">**Guia Sobre**: exibe informações básicas sobre o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0c770-173">**About tab**: Displays basic information about your app.</span></span>|
|<span data-ttu-id="0c770-174">5 </span><span class="sxs-lookup"><span data-stu-id="0c770-174">5</span></span>|<span data-ttu-id="0c770-175">**Balão de chat**: as conversas do bot usam a estrutura de mensagens do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0c770-175">**Chat bubble**: Bot conversations use the Teams messaging framework.</span></span>|
|<span data-ttu-id="0c770-176">6 </span><span class="sxs-lookup"><span data-stu-id="0c770-176">6</span></span>|<span data-ttu-id="0c770-177">**Cartão Adaptável**: se as respostas do bot incluírem Cartões Adaptáveis, o cartão ocupará toda a largura do balão de chat.</span><span class="sxs-lookup"><span data-stu-id="0c770-177">**Adaptive Card**: If your bot’s responses include Adaptive Cards, the card takes up the full width of the chat bubble.</span></span>|
|<span data-ttu-id="0c770-178">7 </span><span class="sxs-lookup"><span data-stu-id="0c770-178">7</span></span>|<span data-ttu-id="0c770-179">**Menu de comando**: exibe os comandos padrão do bot (definidos por você).</span><span class="sxs-lookup"><span data-stu-id="0c770-179">**Command menu**: Displays your bot's standard commands (defined by you).</span></span>

### <a name="command-menu"></a><span data-ttu-id="0c770-180">Menu de comando</span><span class="sxs-lookup"><span data-stu-id="0c770-180">Command menu</span></span>

<span data-ttu-id="0c770-181">O menu de comando fornece uma lista de palavras ou frases às quais você deseja que o bot sempre responda.</span><span class="sxs-lookup"><span data-stu-id="0c770-181">The command menu provides a list of words or phrases you want your bot to always respond to.</span></span> <span data-ttu-id="0c770-182">O menu de comando é exibido acima da caixa de texto quando alguém está conversando com um bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-182">The command menu displays above the compose box when someone is conversing with a bot.</span></span> <span data-ttu-id="0c770-183">Quando um comando é selecionado, ele é inserido em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="0c770-183">When a command is selected, it gets inserted into a message.</span></span>

<span data-ttu-id="0c770-184">A lista de comandos deve ser breve.</span><span class="sxs-lookup"><span data-stu-id="0c770-184">The list of commands should be brief.</span></span> <span data-ttu-id="0c770-185">O menu tem como objetivo destacar os principais recursos do bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-185">The menu is only meant to highlight your bot’s primary features.</span></span> <span data-ttu-id="0c770-186">Mantenha os comandos concisos também.</span><span class="sxs-lookup"><span data-stu-id="0c770-186">Keep commands concise, too.</span></span> <span data-ttu-id="0c770-187">Por exemplo, crie um comando chamado **Ajuda** em vez de usar **Você pode me ajudar**?</span><span class="sxs-lookup"><span data-stu-id="0c770-187">For example, create a command called **Help** instead of **Can you please help me**?</span></span>
<span data-ttu-id="0c770-188">O menu de comandos deve estar sempre disponível, independentemente do estado da conversa.</span><span class="sxs-lookup"><span data-stu-id="0c770-188">The command menu must always be available regardless of the state of the conversation.</span></span>

:::image type="content" source="../../assets/images/bots/bot-command-menu.png" alt-text="Exemplo mostrando o menu de comandos de um bot." border="false":::

## <a name="understand-what-people-are-saying"></a><span data-ttu-id="0c770-190">Entenda o que as pessoas estão dizendo</span><span class="sxs-lookup"><span data-stu-id="0c770-190">Understand what people are saying</span></span>

<span data-ttu-id="0c770-191">Use um dicionário de sinônimos e receba pessoas de todas as origens para ajudar você a gerar diferentes interpretações sobre as consultas padrão.</span><span class="sxs-lookup"><span data-stu-id="0c770-191">Use a thesaurus and get people from as many different backgrounds as possible to help you generate different interpretations of standard queries.</span></span>

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

### <a name="extract-intent-and-data-from-messages"></a><span data-ttu-id="0c770-195">Extrair intenção e dados de mensagens</span><span class="sxs-lookup"><span data-stu-id="0c770-195">Extract intent and data from messages</span></span>

<span data-ttu-id="0c770-196">Projete seu bot para reconhecer intenções, o que interpreta o que alguém deseja de um bot em resposta a uma mensagem ou consulta.</span><span class="sxs-lookup"><span data-stu-id="0c770-196">Design your bot to recognize intent, which captures what someone wants from a bot in response to a message or query.</span></span> <span data-ttu-id="0c770-197">A intenção classifica uma mensagem ou consulta como uma única ação com um ou mais objetos de dados que são afetados por essa ação.</span><span class="sxs-lookup"><span data-stu-id="0c770-197">Intent classifies a message or query as a single action with one or more data objects that are affected by the action.</span></span> 

<span data-ttu-id="0c770-198">Os exemplos a seguir descrevem as intenções e os dados do usuário em mensagens enviadas para bots.</span><span class="sxs-lookup"><span data-stu-id="0c770-198">The following examples outline the user intent and data in messages sent to bots.</span></span>

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

### <a name="analyze-and-improve"></a><span data-ttu-id="0c770-202">Analisar e melhorar</span><span class="sxs-lookup"><span data-stu-id="0c770-202">Analyze and improve</span></span>

<span data-ttu-id="0c770-203">Saiba o que os usuários dizem ao conversar com o bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-203">Learn what users say when chatting with your bot.</span></span> <span data-ttu-id="0c770-204">Este será um processo contínuo e iterativo, à medida que a sua base de usuários crescer em diferentes locais e organizações.</span><span class="sxs-lookup"><span data-stu-id="0c770-204">This will be an ongoing, iterative process as your user base grows in different locations and orgs.</span></span> <span data-ttu-id="0c770-205">Você pode ajustar o mapeamento de intenção e reconhecimento de linguagem do bot com o Microsoft Language Understanding (LUIS).</span><span class="sxs-lookup"><span data-stu-id="0c770-205">You can tune your bot's language recognition and intent mapping with Microsoft Language Understanding (LUIS).</span></span>

* <span data-ttu-id="0c770-206">[Funcionamento do LUIS](https://docs.microsoft.com/azure/cognitive-services/luis/artificial-intelligence): Descubra como o LUIS usa inteligência artificial para fornecer uma compreensão de linguagem natural (CLN) aos dados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0c770-206">[Understanding LUIS](https://docs.microsoft.com/azure/cognitive-services/luis/artificial-intelligence): Find out how LUIS uses AI to provide natural language understanding (NLU) to your app data.</span></span>
* <span data-ttu-id="0c770-207">[Integração com o LUIS](https://www.luis.ai/): adicione recursos de linguagem natural ao seu bot sem o processo complexo de criação de modelos de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="0c770-207">[Integrating with LUIS](https://www.luis.ai/): Add natural language capabilities to your bot without the complex process of creating machine learning models.</span></span>

## <a name="use-cases"></a><span data-ttu-id="0c770-208">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="0c770-208">Use cases</span></span>

### <a name="simple-queries"></a><span data-ttu-id="0c770-209">Consultas simples</span><span class="sxs-lookup"><span data-stu-id="0c770-209">Simple queries</span></span>

<span data-ttu-id="0c770-210">Os bots podem fornecer uma correspondência exata de uma consulta ou um grupo de correspondências relacionadas para ajudar com a desambiguação.</span><span class="sxs-lookup"><span data-stu-id="0c770-210">Bots can deliver an exact match to a query or a group of related matches to help with disambiguation.</span></span> <span data-ttu-id="0c770-211">Para ver as correspondências relacionadas, agrupe o conteúdo usando um cartão da lista.</span><span class="sxs-lookup"><span data-stu-id="0c770-211">For related matches, group the content using a list card.</span></span>

:::image type="content" source="../../assets/images/bots/bot-simple-query.png" alt-text="Exemplo mostrando uma interação de consulta simples com um bot." border="false":::

### <a name="multi-turn-interactions"></a><span data-ttu-id="0c770-213">Interações de várias etapas</span><span class="sxs-lookup"><span data-stu-id="0c770-213">Multi-turn interactions</span></span>

<span data-ttu-id="0c770-214">Embora o seu bot possa dar suporte a solicitações e perguntas completas, ele também deve ser capaz de lidar com interações de várias etapas.</span><span class="sxs-lookup"><span data-stu-id="0c770-214">While your bot can support complete requests and questions, it should also be able to handle multi-turn interactions.</span></span> <span data-ttu-id="0c770-215">Prever as próximas etapas possíveis torna muito mais fácil criar um fluxo de tarefas completo para as pessoas (em vez de esperar que elas criem uma única solicitação abrangente).</span><span class="sxs-lookup"><span data-stu-id="0c770-215">Anticipating possible next steps makes it much easier for people to a complete task flow (rather than expecting them to craft a comprehensive request).</span></span>

<span data-ttu-id="0c770-216">No exemplo a seguir, o bot responde a cada mensagem com opções para o que talvez você queira fazer em seguida.</span><span class="sxs-lookup"><span data-stu-id="0c770-216">In the following example, the bot responds to each message with options for what might want to do next.</span></span>

:::image type="content" source="../../assets/images/bots/bot-multi-turn.png" alt-text="Exemplo mostrando uma interação de várias etapas com um bot." border="false":::

### <a name="reach-out-to-users"></a><span data-ttu-id="0c770-218">Fale com os usuários</span><span class="sxs-lookup"><span data-stu-id="0c770-218">Reach out to users</span></span>

<span data-ttu-id="0c770-219">Com um sistema de mensagens proativo, seu bot pode atuar como um resumo que envia notificações relevantes para uma pessoa, chat em grupo ou canal com uma frequência específica.</span><span class="sxs-lookup"><span data-stu-id="0c770-219">With proactive messaging, your bot can act like a digest that sends notifications relevant to an individual, group chat, or channel at a specific frequency.</span></span> <span data-ttu-id="0c770-220">Um bot pode enviar uma mensagem quando houver alterações em um documento ou um item de trabalho for fechado.</span><span class="sxs-lookup"><span data-stu-id="0c770-220">A bot may send a message when something has changed in a document or a work item is closed.</span></span>

<span data-ttu-id="0c770-221">No exemplo a seguir, um usuário recebe uma notificação do sistema avisando que um bot enviou uma mensagem para ele em outro canal.</span><span class="sxs-lookup"><span data-stu-id="0c770-221">In the following example, a user gets a toast notification that a bot messaged them in another channel.</span></span>

:::image type="content" source="../../assets/images/bots/bot-proactive-message-toast.png" alt-text="Exemplo mostrando uma notificação do sistema de um bot enviando mensagens proativamente a um usuário de outro canal." border="false":::

<span data-ttu-id="0c770-223">Nesse canal, o usuário pode ler a mensagem por meio do bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-223">Now in that channel, the user can read their message from the bot.</span></span>

:::image type="content" source="../../assets/images/bots/bot-proactive-message.png" alt-text="Exemplo mostrando o usuário observando a mensagem proativa do bot." border="false":::

### <a name="use-tabs-with-bots"></a><span data-ttu-id="0c770-225">Usar guias com bots</span><span class="sxs-lookup"><span data-stu-id="0c770-225">Use tabs with bots</span></span>

<span data-ttu-id="0c770-226">As guias podem facilitar o uso do bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-226">A tab can make your bot easier to use.</span></span> <span data-ttu-id="0c770-227">Por exemplo, se o bot puder criar itens de trabalho, será bom mostrar todos esses itens em um local central dentro de uma guia. Saiba mais sobre [criação de guias](../../tabs/design/tabs.md).</span><span class="sxs-lookup"><span data-stu-id="0c770-227">For example, if your bot can create work items, it would be nice to show all those items in a central location inside a tab. See more about [designing tabs](../../tabs/design/tabs.md).</span></span>

:::image type="content" source="../../assets/images/bots/bot-with-tab.png" alt-text="Exemplo mostrando como uma guia pode ajudar a organizar o conteúdo do bot." border="false":::

## <a name="manage-a-bot"></a><span data-ttu-id="0c770-229">Gerenciar um bot</span><span class="sxs-lookup"><span data-stu-id="0c770-229">Manage a bot</span></span>

<span data-ttu-id="0c770-230">Os usuários devem ser capazes de alterar as configurações de um bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-230">Users should be able to change a bot's settings.</span></span> <span data-ttu-id="0c770-231">Você pode fornecer essa funcionalidade com comandos de bot, mas geralmente é mais eficiente incluir todas as configurações em um [módulo de tarefas](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) (como mostra o exemplo a seguir).</span><span class="sxs-lookup"><span data-stu-id="0c770-231">You can provide this functionality with bot commands, but it's usually more efficient to include all settings in a [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) (as shown in the following example).</span></span>

:::image type="content" source="../../assets/images/bots/manage-bot-task-module.png" alt-text="Exemplo mostrando um módulo de tarefas para definir as configurações de um bot." border="false":::

## <a name="best-practices"></a><span data-ttu-id="0c770-233">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="0c770-233">Best practices</span></span>

### <a name="content"></a><span data-ttu-id="0c770-234">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="0c770-234">Content</span></span>

:::image type="content" source="../../assets/images/bots/bot-content-persona-do.png" alt-text="Exemplo mostrando uma prática recomendada para bots." border="false":::

#### <a name="do-establish-a-clear-persona"></a><span data-ttu-id="0c770-236">Estabeleça uma personalidade bem definida</span><span class="sxs-lookup"><span data-stu-id="0c770-236">Do: Establish a clear persona</span></span>

<span data-ttu-id="0c770-237">O tom do bot é leve e amigável, focando "apenas em fatos", ou é mais peculiar?</span><span class="sxs-lookup"><span data-stu-id="0c770-237">Is your bot's tone friendly and light, “just the facts”, or super quirky?</span></span> <span data-ttu-id="0c770-238">Como ele deve responder em diferentes cenários?</span><span class="sxs-lookup"><span data-stu-id="0c770-238">How should it respond in different scenarios?</span></span> <span data-ttu-id="0c770-239">Planejar e documentar a personalidade do seu bot facilita escrever respostas que pareçam naturais e coesas.</span><span class="sxs-lookup"><span data-stu-id="0c770-239">Planning and documenting your bot's persona makes it easier to write responses that seem natural and cohesive.</span></span>

<span data-ttu-id="0c770-240">Saiba mais sobre como escrever para bots no <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Kit de Interface do Usuário do Microsoft Teams (Figma).</a></span><span class="sxs-lookup"><span data-stu-id="0c770-240">See more about writing for bots in the <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a></span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-do.png" alt-text="Exemplo mostrando práticas práticas de bots." border="false":::

#### <a name="do-clearly-convey-what-your-bot-can-do"></a><span data-ttu-id="0c770-242">Transmita claramente o que o bot pode fazer</span><span class="sxs-lookup"><span data-stu-id="0c770-242">Do: Clearly convey what your bot can do</span></span>

<span data-ttu-id="0c770-243">Mensagens de boas-vindas e tours ajudam as pessoas a entender o que elas podem fazer com o bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-243">Welcome messages and tours help people understand what they can do with your bot.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-dont.png" alt-text="Exemplo é mostrar uma prática prática de bot." border="false":::

#### <a name="dont-obscure-your-bots-features"></a><span data-ttu-id="0c770-245">Não oculte os recursos do bot</span><span class="sxs-lookup"><span data-stu-id="0c770-245">Don't: Obscure your bot's features</span></span>

<span data-ttu-id="0c770-246">A primeira impressão é importante.</span><span class="sxs-lookup"><span data-stu-id="0c770-246">First impressions matter.</span></span> <span data-ttu-id="0c770-247">As pessoas provavelmente ficarão confusas ou desconfiadas quando receberem uma mensagem de logon indefinida.</span><span class="sxs-lookup"><span data-stu-id="0c770-247">People will likely be confused or suspicious when presented with a nondescript sign-in message.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-do.png" alt-text="Exemplo de mostrar uma prática prática de bot." border="false":::

#### <a name="do-recognize-non-questions"></a><span data-ttu-id="0c770-249">Reconheça mensagens que não são perguntas</span><span class="sxs-lookup"><span data-stu-id="0c770-249">Do: Recognize non-questions</span></span>

<span data-ttu-id="0c770-250">Seu bot deve ser capaz de responder a mensagens como "Olá", "Ajuda" e "Obrigado", além de levar em conta erros comuns de ortografia e coloquialismos.</span><span class="sxs-lookup"><span data-stu-id="0c770-250">Your bot should be able to respond to messages like "Hi", "Help", and "Thanks" while also accounting for common misspellings and colloquialisms.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-dont.png" alt-text="Exemplo mostra uma prática prática de bot." border="false":::

#### <a name="dont-miss-out-on-opportunities-to-delight"></a><span data-ttu-id="0c770-252">Não perca oportunidades de agradar</span><span class="sxs-lookup"><span data-stu-id="0c770-252">Don't: Miss out on opportunities to delight</span></span>

<span data-ttu-id="0c770-253">Algumas pessoas esperam que as conversas fluam naturalmente, como com uma pessoa real.</span><span class="sxs-lookup"><span data-stu-id="0c770-253">Some people expect conversations to flow naturally like they would with a real person.</span></span> <span data-ttu-id="0c770-254">Tente evitar respostas insvasas a mensagens simples.</span><span class="sxs-lookup"><span data-stu-id="0c770-254">Try to avoid clumsy responses to simple messages.</span></span>

   :::column-end:::
:::row-end:::

### <a name="troubleshooting"></a><span data-ttu-id="0c770-255">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="0c770-255">Troubleshooting</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-do.png" alt-text="Exemplo de prática prática de bot." border="false":::

#### <a name="do-provide-help"></a><span data-ttu-id="0c770-257">Forneça ajuda</span><span class="sxs-lookup"><span data-stu-id="0c770-257">Do: Provide help</span></span>

<span data-ttu-id="0c770-258">Se o bot não puder atender a uma solicitação, forneça maneiras de o usuário se instruir sobre a interação com o bot.</span><span class="sxs-lookup"><span data-stu-id="0c770-258">If your bot can’t satisfy a request, provide ways for a user to educate themselves about interacting with your bot.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-dont.png" alt-text="O exemplo exibe uma prática prática de bot." border="false":::

#### <a name="dont-leave-users-stranded"></a><span data-ttu-id="0c770-260">Não deixe os usuários desamparados</span><span class="sxs-lookup"><span data-stu-id="0c770-260">Don't: Leave users stranded</span></span>

<span data-ttu-id="0c770-261">As pessoas abandonarão o bot rapidamente se não puderem solucionar problemas.</span><span class="sxs-lookup"><span data-stu-id="0c770-261">People will quickly abandon your bot if they can’t troubleshoot issues.</span></span>

   :::column-end:::
:::row-end:::

### <a name="complex-interactions"></a><span data-ttu-id="0c770-262">Interações complexas</span><span class="sxs-lookup"><span data-stu-id="0c770-262">Complex interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-do.png" alt-text="Exemplo exibindo uma prática prática de bot." border="false":::

#### <a name="do-use-task-modules-or-tabs"></a><span data-ttu-id="0c770-264">Use guias ou módulos de tarefa</span><span class="sxs-lookup"><span data-stu-id="0c770-264">Do: Use task modules or tabs</span></span>

<span data-ttu-id="0c770-265">Se o bot fornece uma resposta que exige algumas etapas adicionais, você pode incluir links para um módulo de tarefa ou uma guia para concluir a tarefa ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="0c770-265">If your bot provides an answer that requires a few more steps, you can link to a task module or tab to complete the task or flow.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-dont.png" alt-text="Consulte o exemplo de uma prática prática de bot." border="false":::

#### <a name="dont-make-multi-turn-interactions-tedious"></a><span data-ttu-id="0c770-267">Não torne as interações em várias etapas entediantes</span><span class="sxs-lookup"><span data-stu-id="0c770-267">Don't: Make multi-turn interactions tedious</span></span>

<span data-ttu-id="0c770-268">Ter uma longa conversa para concluir uma única tarefa é algo lento e complexo demais.</span><span class="sxs-lookup"><span data-stu-id="0c770-268">An extensive conversation to complete a single task is slow and overly complex.</span></span> <span data-ttu-id="0c770-269">Isso também exige que o desenvolvedor tenha em conta as alterações de status (por exemplo, a conversa expirar ou você enviar uma mensagem para "Cancelar").</span><span class="sxs-lookup"><span data-stu-id="0c770-269">It also requires the developer to account for state changes (such as the conversation timing out or you sending a “Cancel” message).</span></span>

   :::column-end:::
:::row-end:::

### <a name="privacy"></a><span data-ttu-id="0c770-270">Privacidade</span><span class="sxs-lookup"><span data-stu-id="0c770-270">Privacy</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-do.png" alt-text="Exemplo exibe uma prática prática de bot." border="false":::

#### <a name="do-only-show-sensitive-info-in-a-personal-context"></a><span data-ttu-id="0c770-272">Somente mostre informações confidenciais em um contexto pessoal</span><span class="sxs-lookup"><span data-stu-id="0c770-272">Do: Only show sensitive info in a personal context</span></span>

<span data-ttu-id="0c770-273">Se o bot estiver em um chat em grupo ou canal, recomendamos direcionar os usuários para um local privado (como um módulo de tarefas, uma guia ou um navegador) para exibir informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="0c770-273">If your bot is in a group chat or channel, we recommend directing users to a private location (such as a task module, tab, or browser) to view sensitive information.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-dont.png" alt-text="Ilustração mostrando uma prática prática de bot." border="false":::

#### <a name="dont-some-content-isnt-meant-to-be-seen-by-everyone"></a><span data-ttu-id="0c770-275">Alguns conteúdos não devem ser vistos por todos</span><span class="sxs-lookup"><span data-stu-id="0c770-275">Don't: Some content isn’t meant to be seen by everyone</span></span>

<span data-ttu-id="0c770-276">O bot não deve revelar informações confidenciais para um grupo de pessoas.</span><span class="sxs-lookup"><span data-stu-id="0c770-276">Your bot shouldn’t reveal sensitive information to a group of people.</span></span>

   :::column-end:::
:::row-end:::

## <a name="learn-more"></a><span data-ttu-id="0c770-277">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="0c770-277">Learn more</span></span>

<span data-ttu-id="0c770-278">Estas outras diretrizes podem ajudar com a criação do seu bot:</span><span class="sxs-lookup"><span data-stu-id="0c770-278">These other guidelines may help with your bot design:</span></span>

* [<span data-ttu-id="0c770-279">Criar seu aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="0c770-279">Designing your personal app</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="0c770-280">Criar Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="0c770-280">Designing Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)
* [<span data-ttu-id="0c770-281">Criar módulos de tarefa</span><span class="sxs-lookup"><span data-stu-id="0c770-281">Designing task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)

## <a name="validate-your-design"></a><span data-ttu-id="0c770-282">Valide o seu design</span><span class="sxs-lookup"><span data-stu-id="0c770-282">Validate your design</span></span>

<span data-ttu-id="0c770-283">Se você planeja publicar seu aplicativo no AppSource, deve compreender os problemas de design que normalmente causam falha dos aplicativos durante o envio.</span><span class="sxs-lookup"><span data-stu-id="0c770-283">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0c770-284">Verifique as diretrizes de validação de design</span><span class="sxs-lookup"><span data-stu-id="0c770-284">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
