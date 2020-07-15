---
title: Diretrizes de design para bots
description: Descreve as diretrizes para a criação de bots
keywords: Diretrizes de design de equipes referência de bots
ms.openlocfilehash: 4f474278b37058f61886a620af634780d2e3cb19
ms.sourcegitcommit: d0ca6a4856ffd03d197d47338e633126723fa78a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2020
ms.locfileid: "45137672"
---
# <a name="start-talking-with-bots"></a><span data-ttu-id="5ea1e-104">Começar a falar com bots</span><span class="sxs-lookup"><span data-stu-id="5ea1e-104">Start talking with bots</span></span>

<span data-ttu-id="5ea1e-105">Bots são aplicativos de conversa que executam um conjunto estreito ou específico de tarefas.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-105">Bots are conversational apps that perform a narrow or specific set of tasks.</span></span> <span data-ttu-id="5ea1e-106">Eles fornecem uma oportunidade para se comunicar com os usuários, responder às suas perguntas e notificá-los proativamente sobre as alterações.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-106">They give you an opportunity to communicate with users, respond to their questions, and proactively notify them about changes.</span></span> <span data-ttu-id="5ea1e-107">Eles são uma ótima maneira de entrar.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-107">They’re a great way to reach out.</span></span>

---

## <a name="guidelines"></a><span data-ttu-id="5ea1e-108">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="5ea1e-108">Guidelines</span></span>

### <a name="avatars"></a><span data-ttu-id="5ea1e-109">Avatares</span><span class="sxs-lookup"><span data-stu-id="5ea1e-109">Avatars</span></span>

<span data-ttu-id="5ea1e-110">Os Avatar avatars no Teams estão moldados como hexágonos para que as pessoas possam afirmar rapidamente que estão conversando com um bot, em vez de uma pessoa.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-110">Bot avatars in Teams are shaped like hexagons so people can quickly tell that they’re talking to a bot instead of a person.</span></span> <span data-ttu-id="5ea1e-111">Você enviará o Avatar como um quadrado e o cortará para você.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-111">You’ll submit your avatar as a square and we’ll crop it for you.</span></span> <span data-ttu-id="5ea1e-112">Quando se trata de avatars, recomendamos que você se torne legível de 2 metros de distância e usando um contraste maior.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-112">When it comes to avatars, we recommend making yours legible from 2 feet away and using a higher contrast.</span></span>

[!include[Avatar image](~/includes/design/bot-avatar-image.html)]

### <a name="buttons"></a><span data-ttu-id="5ea1e-113">Botões</span><span class="sxs-lookup"><span data-stu-id="5ea1e-113">Buttons</span></span>

<span data-ttu-id="5ea1e-114">Oferecemos suporte para até seis botões por cartão.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-114">We support up to six buttons per card.</span></span> <span data-ttu-id="5ea1e-115">Seja conciso ao escrever o texto do botão e lembre-se de que a maioria dos botões só deve solucionar a tarefa em mãos.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-115">Be concise when writing button text, and keep in mind that most buttons should only address the task at hand.</span></span>

### <a name="graphics"></a><span data-ttu-id="5ea1e-116">Recurso</span><span class="sxs-lookup"><span data-stu-id="5ea1e-116">Graphics</span></span>

<span data-ttu-id="5ea1e-117">Os gráficos são uma boa maneira de informar uma história, mas nem todas as conversas de bot exigem elementos gráficos, portanto, use-as para o máximo impacto.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-117">Graphics are a good way to tell a story, but not all bot conversations require graphics, so use them for maximum impact.</span></span>

### <a name="onboarding-users"></a><span data-ttu-id="5ea1e-118">Usuários de integração</span><span class="sxs-lookup"><span data-stu-id="5ea1e-118">Onboarding users</span></span>

<span data-ttu-id="5ea1e-119">É fundamental que os bots se apresentem e transmitam o que eles podem fazer para os usuários.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-119">It is critical that bots introduce themselves and convey what they can do for users.</span></span> <span data-ttu-id="5ea1e-120">Esse *valor o Exchange* ajuda os usuários a entender o que fazer com o bot, onde as limitações podem estar, e o mais importante, ajuda os usuários a tolerar a interação com uma máquina que não será tão intuitiva como uma pessoa real.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-120">This *value exchange* helps users understand what to do with the bot, where the limitations may lie, and, most importantly, helps users tolerate the interaction with a machine that won’t be as intuitive as a real person .</span></span> <span data-ttu-id="5ea1e-121">Além disso, ele concede permissão aos dados do usuário no Exchange para o valor real que o serviço fornece.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-121">Additionally, it grants permission to user data in exchange for the real value the service provides.</span></span>

#### <a name="welcome-messages"></a><span data-ttu-id="5ea1e-122">Mensagens de boas-vindas</span><span class="sxs-lookup"><span data-stu-id="5ea1e-122">Welcome messages</span></span>

<span data-ttu-id="5ea1e-123">As mensagens de boas-vindas são a melhor maneira de definir o tom do bot e devem ser usadas em cenários pessoais e de equipe ou grupo.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-123">Welcome messages are the best way to set your bot's tone and should be used in personal and team or group scenarios.</span></span> <span data-ttu-id="5ea1e-124">A mensagem informa o que o bot faz e algumas maneiras comuns de interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-124">The message states what the bot does and some common ways to interact with it.</span></span> <span data-ttu-id="5ea1e-125">Use exemplos de recursos específicos, como "*Tente perguntar...*"</span><span class="sxs-lookup"><span data-stu-id="5ea1e-125">Use specific capability examples like,  “*Try asking ….*”</span></span> <span data-ttu-id="5ea1e-126">em uma lista com marcadores.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-126">in a bulleted list.</span></span> <span data-ttu-id="5ea1e-127">Sempre que possível, essas sugestões devem retornar respostas armazenadas.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-127">Whenever possible, these suggestions should return stored responses.</span></span> <span data-ttu-id="5ea1e-128">É fundamental que os exemplos de recursos funcionem sem exigir que os usuários entrem.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-128">It's critical that the capability examples work without requiring users to sign in.</span></span>

#### <a name="tours"></a><span data-ttu-id="5ea1e-129">Viagens</span><span class="sxs-lookup"><span data-stu-id="5ea1e-129">Tours</span></span>

<span data-ttu-id="5ea1e-130">Inclua um atributo *Take a Tour* com mensagens de boas-vindas e respostas para entrada de usuário equivalente a "*ajuda*".</span><span class="sxs-lookup"><span data-stu-id="5ea1e-130">Include a *Take a tour* attribute with welcome messages and responses to user input equivalent to “*help*”.</span></span> <span data-ttu-id="5ea1e-131">Essa é a maneira mais eficaz de permitir que os usuários saibam o que um bot pode fazer.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-131">This is the most effective way to let users learn what a bot can do.</span></span> <span data-ttu-id="5ea1e-132">Os carrossel em experiências de um-para-um são uma maneira excelente de informar essa história e incluir os botões de *experimentar que* os links para exemplos de respostas possíveis sejam incentivados.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-132">Carousels in one-to-one experiences are an excellent way to tell this story and including *Try it* buttons linking to  examples of possible responses is encouraged.</span></span> <span data-ttu-id="5ea1e-133">Os Tours também são bons lugares para falar sobre outros recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-133">Tours are also great places to talk about an app’s other features.</span></span> <span data-ttu-id="5ea1e-134">Por exemplo, você pode incluir capturas de tela das guias de extensões de mensagens e equipes.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-134">For example, you can include screenshots of messaging extensions and Teams tabs.</span></span>  <span data-ttu-id="5ea1e-135">Os usuários não devem ter que entrar no Access e usar um tour.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-135">Users shouldn't have to sign in to access and use a tour.</span></span>

<span data-ttu-id="5ea1e-136">Quando os Tours são usados em cenários de equipe ou grupo, eles devem ser abertos em um módulo de tarefa para não adicionar mais ruído de cartão às conversas em andamento entre usuários.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-136">When tours are used in team or group scenarios, they should open in a task module so as not to add more card noise to the ongoing conversations between users.</span></span>

### <a name="responding-to-users-and-failing-gracefully"></a><span data-ttu-id="5ea1e-137">Responder aos usuários e falhar normalmente</span><span class="sxs-lookup"><span data-stu-id="5ea1e-137">Responding to users and failing gracefully</span></span>

<span data-ttu-id="5ea1e-138">Seu bot também deve ser capaz de responder a coisas como "*Hi*", "*Help*" e "*thanks*" ao assumir erros comuns e coloquialismos em conta.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-138">Your bot should also be able to respond to things like "*Hi*", "*Help*", and "*Thanks*" while taking common misspellings and colloquialisms into account.</span></span> <span data-ttu-id="5ea1e-139">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5ea1e-139">For example:</span></span>

#### <a name="x2713-hello"></a><span data-ttu-id="5ea1e-140">&#x2713; Hello</span><span class="sxs-lookup"><span data-stu-id="5ea1e-140">&#x2713; Hello</span></span>

<span data-ttu-id="5ea1e-141">`"Hi"`  `"How are you"`  `"Howdy"`</span><span class="sxs-lookup"><span data-stu-id="5ea1e-141">`"Hi"`  `"How are you"`  `"Howdy"`</span></span>

#### <a name="x2713-help"></a><span data-ttu-id="5ea1e-142">&#x2713; ajuda</span><span class="sxs-lookup"><span data-stu-id="5ea1e-142">&#x2713; Help</span></span>

<span data-ttu-id="5ea1e-143">`"What do you do?"`  `"How does this work?"`  `"What the heck?"`</span><span class="sxs-lookup"><span data-stu-id="5ea1e-143">`"What do you do?"`  `"How does this work?"`  `"What the heck?"`</span></span>

#### <a name="x2713-thanks"></a><span data-ttu-id="5ea1e-144">&#x2713; agradecimentos</span><span class="sxs-lookup"><span data-stu-id="5ea1e-144">&#x2713; Thanks</span></span>

<span data-ttu-id="5ea1e-145">`"Thank you"`  `"Thankyou"`  `"Thx"`</span><span class="sxs-lookup"><span data-stu-id="5ea1e-145">`"Thank you"`  `"Thankyou"`  `"Thx"`</span></span>

<span data-ttu-id="5ea1e-146">O bot deve ser capaz de lidar com os seguintes tipos de consultas e entradas:</span><span class="sxs-lookup"><span data-stu-id="5ea1e-146">Your bot should be able to handle the following types of queries and inputs:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="5ea1e-147">**Perguntas reconhecidas**.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-147">**Recognized questions**.</span></span> <span data-ttu-id="5ea1e-148">Essas são as perguntas de "cenário de melhor caso" que você espera dos usuários.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-148">These are the “best case scenario” questions you would expect from users.</span></span>
> * <span data-ttu-id="5ea1e-149">**Não há perguntas reconhecidas**.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-149">**Recognized non-questions**.</span></span> <span data-ttu-id="5ea1e-150">Consultas sobre funcionalidades não suportadas e/ou entradas aleatórias, não relacionadas ou impróprias.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-150">Queries about unsupported functionality and/or random, unrelated , or profane entries.</span></span>
> * <span data-ttu-id="5ea1e-151">**Perguntas não reconhecidas**: entrada ou entradas que são ininteligível, sem significado ou sem sentido.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-151">**Unrecognized questions**: Input or entries that are unintelligible, meaningless, or nonsense.</span></span>

<span data-ttu-id="5ea1e-152">Exemplos de personalidade de bot e tipos de resposta:</span><span class="sxs-lookup"><span data-stu-id="5ea1e-152">Examples of bot personality and response types:</span></span>

[!include[Bot responses](~/includes/design/bot-responses-table.html)]

> [!TIP]
> <span data-ttu-id="5ea1e-153">Ao escrever seu script de bot, pergunte-se: "minha empresa será embarrassed se uma resposta for capturada e compartilhada?"</span><span class="sxs-lookup"><span data-stu-id="5ea1e-153">When writing your bot script, ask yourself: “Will my company be embarrassed if a response is screen captured and shared?”</span></span>

### <a name="understanding-what-users-are-trying-to-say"></a><span data-ttu-id="5ea1e-154">Noções básicas sobre o que os usuários estão tentando dizer</span><span class="sxs-lookup"><span data-stu-id="5ea1e-154">Understanding what users are trying to say</span></span>

#### <a name="use-a-thesaurus-for-synonyms"></a><span data-ttu-id="5ea1e-155">Usar um dicionário de sinônimos para sinônimos</span><span class="sxs-lookup"><span data-stu-id="5ea1e-155">Use a thesaurus for synonyms</span></span>

<span data-ttu-id="5ea1e-156">Ao fazer o debate de variações, use um dicionário de sinônimos e obtenha às pessoas o máximo de diferentes planos de fundo possíveis para ajudá-lo a gerar diferentes interpretações de cada consulta.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-156">When brainstorming variants, use a thesaurus and get people from as many different backgrounds as possible to help you generate different interpretations of each query.</span></span>

#### <a name="make-use-of-telemetry-and-interviews"></a><span data-ttu-id="5ea1e-157">Fazer uso de telemetria e entrevistas</span><span class="sxs-lookup"><span data-stu-id="5ea1e-157">Make use of telemetry and interviews</span></span>

<span data-ttu-id="5ea1e-158">Descubra o que os usuários estão dizendo e qual era a intenção de consultar seu bot.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-158">Find out what users are saying and what was their intent when querying your bot.</span></span> <span data-ttu-id="5ea1e-159">Este será um processo contínuo à medida que você obtém usuários em diferentes locais e tipos de empresas.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-159">This will be an ongoing process as you get users in different locations and types of companies.</span></span> <span data-ttu-id="5ea1e-160">Você pode ajustar o reconhecimento de idioma e o mapeamento de intenções com o idioma entendendo o serviço inteligente ([Luis](/azure/cognitive-services/luis/what-is-luis)).</span><span class="sxs-lookup"><span data-stu-id="5ea1e-160">You can fine-tune language recognition and intent mapping with Language Understanding Intelligent Service ([LUIS](/azure/cognitive-services/luis/what-is-luis)).</span></span>

### <a name="how-often-should-you-use-your-bot-to-reach-out-to-a-user"></a><span data-ttu-id="5ea1e-161">Com que frequência você deve usar o bot para entrar em um usuário?</span><span class="sxs-lookup"><span data-stu-id="5ea1e-161">How often should you use your bot to reach out to a user?</span></span>

#### <a name="x2713-when-a-state-has-changed"></a><span data-ttu-id="5ea1e-162">&#x2713; quando um estado tiver sido alterado</span><span class="sxs-lookup"><span data-stu-id="5ea1e-162">&#x2713; When a state has changed</span></span>

<span data-ttu-id="5ea1e-163">Por exemplo, se uma atribuição for marcada como concluída, quando um erro for alterado, quando uma nova mídia social estiver disponível ou quando uma pesquisa tiver sido concluída.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-163">For example, if an assignment is marked as complete, when a bug changes, when new social media is available, or when a poll has been completed.</span></span>

#### <a name="x2713-when-the-timing-is-right"></a><span data-ttu-id="5ea1e-164">&#x2713; quando o intervalo é para a direita</span><span class="sxs-lookup"><span data-stu-id="5ea1e-164">&#x2713; When the timing is right</span></span>

<span data-ttu-id="5ea1e-165">Seu bot pode agir como um resumo diário, enviando uma notificação para o usuário ou canal em uma frequência específica.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-165">Your bot can act like a daily digest, sending a notification to the user or channel at a specific frequency.</span></span>

<span data-ttu-id="5ea1e-166">Deixe o usuário no controle.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-166">Leave the user in control.</span></span> <span data-ttu-id="5ea1e-167">Fornecer configurações de notificação que incluem frequência e prioridade.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-167">Provide notification settings that include frequency and priority.</span></span>

[!include[Bot notification](~/includes/design/bot-notification-image.html)]

---

## <a name="using-tabs"></a><span data-ttu-id="5ea1e-168">Usando guias</span><span class="sxs-lookup"><span data-stu-id="5ea1e-168">Using tabs</span></span>

<span data-ttu-id="5ea1e-169">As guias tornam o bot muito mais funcional.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-169">Tabs make your bot much more functional.</span></span> <span data-ttu-id="5ea1e-170">Com guias, você pode criar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5ea1e-170">With tabs, you can create the following:</span></span>

### <a name="x2713-a-place-to-host-standing-queries"></a><span data-ttu-id="5ea1e-171">&#x2713; um local para hospedar consultas em pé</span><span class="sxs-lookup"><span data-stu-id="5ea1e-171">&#x2713; A place to host standing queries</span></span>

<span data-ttu-id="5ea1e-172">Em conversas pessoais entre um bot e uma única pessoa, as guias podem conter informações e listas específicas do usuário.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-172">In personal conversations between a bot and a single person, tabs can contain user-specific information and lists.</span></span> <span data-ttu-id="5ea1e-173">Eles também são um bom local para manter respostas de bot para perguntas frequentes (FAQs), de modo que os usuários não precisem continuar fazendo isso.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-173">They’re also a good place to maintain bot responses to frequently-asked questions (FAQs) — so users don’t need to keep asking.</span></span>

### <a name="x2713-a-place-to-finish-a-conversation"></a><span data-ttu-id="5ea1e-174">&#x2713; um local para concluir uma conversa</span><span class="sxs-lookup"><span data-stu-id="5ea1e-174">&#x2713; A place to finish a conversation</span></span>

<span data-ttu-id="5ea1e-175">Você pode vincular a uma guia de um cartão.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-175">You can link to a tab from a card.</span></span> <span data-ttu-id="5ea1e-176">Se o seu bot fornecer uma resposta que exija algumas etapas adicionais, ele pode vincular a uma guia para concluir a tarefa ou o fluxo.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-176">If your bot provides an answer that requires a few more steps, it can link to a tab to complete the task or flow.</span></span> <span data-ttu-id="5ea1e-177">Por exemplo, em resposta a, "como faço para formatar meu iPhone?", uma boa resposta pode ser um cartão que descreve as primeiras etapas e tem um botão para *Mostrar mais* que, em seguida, leva o usuário à guia de *ajuda* do bot e vincula detalhadamente as instruções específicas.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-177">For instance, in response to, "How do I format my iPhone?", a good response might be a card which outlines the first few steps and has a button for *Show more* that then takes the user to the bot's *Help* tab and deep links to the specific instructions.</span></span>

### <a name="x2713-a-place-to-host-a-settings-page"></a><span data-ttu-id="5ea1e-178">&#x2713; um local para hospedar uma página de configurações</span><span class="sxs-lookup"><span data-stu-id="5ea1e-178">&#x2713; A place to host a settings page</span></span>

<span data-ttu-id="5ea1e-179">Os bots devem ter um controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-179">Bots should have some user control.</span></span> <span data-ttu-id="5ea1e-180">Para muitos bots, ele é permitido por meio de uma interface de chat; no entanto, é difícil lembrar-se dessas configurações.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-180">For many bots it is allowed through a chat interface; however, it's hard to remember those settings.</span></span> <span data-ttu-id="5ea1e-181">Uma guia Configurações pode exibir configurações de usuários, permitir que os usuários alterem todos de uma vez e também podem ser um bom ponto de indisponibilidade para comportamentos personalizados de bot mais complexos.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-181">A settings tab can display users settings, allow users to change them all at once, and may also be a good hand-off point for more complex bot custom behaviors.</span></span>

### <a name="x2713-a-place-to-provide-some-help"></a><span data-ttu-id="5ea1e-182">&#x2713; um local para fornecer ajuda</span><span class="sxs-lookup"><span data-stu-id="5ea1e-182">&#x2713; A place to provide some help</span></span>

<span data-ttu-id="5ea1e-183">Adicione uma guia que instrua os usuários sobre como se comunicar com o bot.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-183">Add a tab that educates users about how to communicate with your bot.</span></span> <span data-ttu-id="5ea1e-184">Você pode fornecer um contexto para o que ele faz ou perguntas frequentes.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-184">You can provide some context for what it does or FAQs.</span></span>

![Fornecer ajuda](~/assets/images/framework/framework_bots_tbot-help.png)

> [!TIP]
> <span data-ttu-id="5ea1e-186">A incorporação de partes do seu site em uma guia ajudará os usuários a manter o contexto de uma conversa quando usarem o serviço.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-186">Embedding parts of your site in a tab will help users maintain the context of a conversation as they use your service.</span></span> <span data-ttu-id="5ea1e-187">Ele remove a necessidade de iniciar o serviço em um navegador e alternar entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-187">It removes the need to launch your service in a browser and switch back and forth between apps.</span></span>

---

## <a name="bots-in-channels"></a><span data-ttu-id="5ea1e-188">Bots em canais</span><span class="sxs-lookup"><span data-stu-id="5ea1e-188">Bots in channels</span></span>

<span data-ttu-id="5ea1e-189">Chamar um bot em um canal pode ser realizado por `@mention` .</span><span class="sxs-lookup"><span data-stu-id="5ea1e-189">Invoking a bot in a channel can be accomplished by `@mention`.</span></span> <span data-ttu-id="5ea1e-190">A caixa de diálogo de bot deve ser exclusiva em canais e grupos vs. cenários um-para-um e, geralmente, é uma boa ideia considerar abordagens distintas.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-190">Bot dialog should be unique in channels and groups vs. one-to-one scenarios and it's generally a good idea to consider separate approaches.</span></span> <span data-ttu-id="5ea1e-191">Isso se aplica especialmente nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="5ea1e-191">This is especially true in the following cases:</span></span>

### <a name="sensitive-data-sent-by-a-bot"></a><span data-ttu-id="5ea1e-192">Dados confidenciais enviados por um bot</span><span class="sxs-lookup"><span data-stu-id="5ea1e-192">Sensitive data sent by a bot</span></span>

<span data-ttu-id="5ea1e-193">Embora os usuários de uma equipe possam ser conhecidos do serviço, as funções de usuário reais não podem.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-193">While the users in a team can be known to the service, the actual user roles cannot.</span></span> <span data-ttu-id="5ea1e-194">Isso significa que, por exemplo, em um cenário de educação que envolve o anti-intimidação, as informações de contato do pai e do aluno não serão compartilhadas em uma configuração de equipe.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-194">This means that, for example, in an education scenario involving bullying, parent and student contact information wouldn't be shared in a team setting.</span></span> <span data-ttu-id="5ea1e-195">Em vez disso, a mensagem do bot pode ser: "dois incidentes anti-intimidação ocorridos hoje", junto com um botão para mostrar detalhes.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-195">Instead the bot's message might be,"Two bullying incidents occurred today" along with a button to show details.</span></span>

<span data-ttu-id="5ea1e-196">Os detalhes de inicialização em uma página da Web ou um módulo de tarefa podem solicitar credenciais de usuário ou consultas em um índice para funções de usuário emparelhadas com contas AAD.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-196">Launching details in a web page, or a task module can prompt for user credentials or query against an index for user roles paired with AAD accounts.</span></span> <span data-ttu-id="5ea1e-197">Em ambas as opções, os dados estão em um escopo de exibição particular e não haverá perda de dados.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-197">In both of these options the data is in a private view scope and there will be no data leakage.</span></span> <span data-ttu-id="5ea1e-198">Se os mesmos dados são enviados em um chat de um para um entre um usuário e o bot, os dados são visíveis apenas para o usuário naquele contexto e, portanto, é seguro para exibir totalmente na mensagem do bot.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-198">If the same data is sent in a one-to-one chat between a user and the bot, the data is only visible to the user in that context and is, therefore safe, to fully display in the bot message.</span></span> <span data-ttu-id="5ea1e-199">O uso de usuários de um canal para um chat de um-para-um deve ser evitado, no entanto, como a navegação forçada é altamente interrompida.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-199">Taking users from a channel to a one-to-one chat should be avoided however as that forced navigation is highly disruptive.</span></span>

### <a name="sending-cards-as-a-response-to-interactions"></a><span data-ttu-id="5ea1e-200">Enviando cartões como uma resposta a interações</span><span class="sxs-lookup"><span data-stu-id="5ea1e-200">Sending cards as a response to interactions</span></span>

<span data-ttu-id="5ea1e-201">Enquanto o envio de um cartão de carrossel em resposta para *fazer um tour* em um chat de um-para-um é perfeitamente aceitável, o mesmo padrão pode produzir dezenas ou centenas de *carrossel de Tour* em um canal ativo com muitos usuários.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-201">While sending a carousel card in response to *Take a tour* in a one-to-one chat is perfectly acceptable, the same pattern could yield tens or hundreds of *tour carousels* in an active channel with lots of users.</span></span> <span data-ttu-id="5ea1e-202">Para evitar isso, os cartões secundários devem ser hospedados em um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-202">To avoid this, secondary cards should be hosted in a task module.</span></span> <span data-ttu-id="5ea1e-203">Este padrão mantém os usuários no contexto com o canal, mantém o canal limpo de respostas excessivas de bot e, opcionalmente, pode considerar diferentes funções de usuário quando o *Tour* é mostrado.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-203">This pattern keeps users in context with the channel, keeps the channel clean of excessive bot responses, and can optionally consider different user roles when the *tour* is shown.</span></span>

## <a name="useful-tips"></a><span data-ttu-id="5ea1e-204">Dicas úteis</span><span class="sxs-lookup"><span data-stu-id="5ea1e-204">Useful tips</span></span>

### <a name="x2713-remember-bots-arent-assistants"></a><span data-ttu-id="5ea1e-205">&#x2713; lembrar, os bots não são assistentes</span><span class="sxs-lookup"><span data-stu-id="5ea1e-205">&#x2713; Remember, bots aren’t assistants</span></span>

<span data-ttu-id="5ea1e-206">Diferentemente de agentes, por exemplo, Cortana, bots atuam como especialistas.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-206">Unlike agents, e.g., Cortana, bots act as specialists.</span></span>

### <a name="x2713-discourage-chitchat"></a><span data-ttu-id="5ea1e-207">&#x2713; desencorajar Chitchat</span><span class="sxs-lookup"><span data-stu-id="5ea1e-207">&#x2713; Discourage chitchat</span></span>

<span data-ttu-id="5ea1e-208">A menos que seu bot seja criado para conversa, encontre maneiras de redirecionar Chitchat para a conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-208">Unless your bot is built for conversation, find ways to redirect chitchat toward task completion.</span></span>

### <a name="x2713-introduce-some-personality"></a><span data-ttu-id="5ea1e-209">&#x2713; apresentar algumas personalidades</span><span class="sxs-lookup"><span data-stu-id="5ea1e-209">&#x2713; Introduce some personality</span></span>

<span data-ttu-id="5ea1e-210">Mantenha sua personalidade de bot consistente com a voz do seu produto.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-210">Keep your bot personality consistent with the voice of your product.</span></span> <span data-ttu-id="5ea1e-211">Pense no bot como palestra à sua empresa.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-211">Think of your bot as speaking for your company.</span></span>

### <a name="x2713-maintain-tone"></a><span data-ttu-id="5ea1e-212">&#x2713; manter Tom</span><span class="sxs-lookup"><span data-stu-id="5ea1e-212">&#x2713; Maintain tone</span></span>

<span data-ttu-id="5ea1e-213">Determine se você deseja que o Tom seja amigável e claro, "apenas os fatos" ou a mais peculiaridades.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-213">Determine whether you want your tone to be friendly and light, “just the facts”, or super quirky.</span></span>

### <a name="x2713-encourage-easy-task-flow"></a><span data-ttu-id="5ea1e-214">&#x2713; incentivar o fluxo de tarefas fácil</span><span class="sxs-lookup"><span data-stu-id="5ea1e-214">&#x2713; Encourage easy task flow</span></span>

<span data-ttu-id="5ea1e-215">Dê suporte a interações de várias perfeitas e ainda permitindo perguntas totalmente formadas.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-215">Support multi-turn interactions while still allowing for fully formed questions.</span></span> <span data-ttu-id="5ea1e-216">Prever a próxima etapa ajudará os usuários a obter muito mais facilidade nos fluxos de tarefas.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-216">Anticipating the next step will help users get through task flows much easier.</span></span>

<span data-ttu-id="5ea1e-217">Se um usuário executar várias etapas para concluir uma tarefa, permita que o bot as assuma por meio de cada etapa, mas termine por ter sugerido um caminho mais rápido.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-217">If a user takes several steps to complete a task, allow your bot to take them through each step, but finish by having it suggest a quicker path.</span></span> <span data-ttu-id="5ea1e-218">Por exemplo, se um usuário levou várias pessoas para definir uma reunião (especificando primeiro uma reunião e, em seguida, identificando com quem e, em seguida, informando a hora e, em seguida, informando o dia), conclua a conversa com a seguinte sugestão: na próxima vez, tente perguntar se você pode agendar uma reunião com Bob em 1:00 amanhã.</span><span class="sxs-lookup"><span data-stu-id="5ea1e-218">For example, if a user has taken several conversational turns to set a meeting (by first specifying a meeting, then identifying with whom, then stating the time, then stating the day), finish the conversation with the following suggestion: Next time, try asking if you can ‘schedule a meeting with Bob at 1:00 tomorrow’.</span></span>
