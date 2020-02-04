---
title: Diretrizes de design para bots
description: Descreve as diretrizes para a criação de bots
keywords: Diretrizes de design de equipes referência de bots
ms.openlocfilehash: f59a1e9c280f27567692b4d10341db79d05c3464
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672868"
---
# <a name="start-talking-with-bots"></a><span data-ttu-id="48e85-104">Começar a falar com bots</span><span class="sxs-lookup"><span data-stu-id="48e85-104">Start talking with bots</span></span>

<span data-ttu-id="48e85-105">Bots são aplicativos de conversa que executam um conjunto estreito ou específico de tarefas.</span><span class="sxs-lookup"><span data-stu-id="48e85-105">Bots are conversational apps that perform a narrow or specific set of tasks.</span></span> <span data-ttu-id="48e85-106">Eles fornecem uma oportunidade para se comunicar com os usuários, responder às suas perguntas e notificá-los proativamente sobre as alterações.</span><span class="sxs-lookup"><span data-stu-id="48e85-106">They give you an opportunity to communicate with users, respond to their questions, and proactively notify them about changes.</span></span> <span data-ttu-id="48e85-107">Eles são uma ótima maneira de entrar.</span><span class="sxs-lookup"><span data-stu-id="48e85-107">They’re a great way to reach out.</span></span>

---

## <a name="guidelines"></a><span data-ttu-id="48e85-108">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="48e85-108">Guidelines</span></span>

### <a name="avatars"></a><span data-ttu-id="48e85-109">Avatares</span><span class="sxs-lookup"><span data-stu-id="48e85-109">Avatars</span></span>

<span data-ttu-id="48e85-110">Os Avatar avatars no Teams estão moldados como hexágonos para que as pessoas possam afirmar rapidamente que estão conversando com um bot, em vez de uma pessoa.</span><span class="sxs-lookup"><span data-stu-id="48e85-110">Bot avatars in Teams are shaped like hexagons so people can quickly tell that they’re talking to a bot instead of a person.</span></span> <span data-ttu-id="48e85-111">Você enviará o Avatar como um quadrado e o cortará para você.</span><span class="sxs-lookup"><span data-stu-id="48e85-111">You’ll submit your avatar as a square and we’ll crop it for you.</span></span> <span data-ttu-id="48e85-112">Quando se trata de avatars, recomendamos que você se torne legível de 2 metros de distância e usando um contraste maior.</span><span class="sxs-lookup"><span data-stu-id="48e85-112">When it comes to avatars, we recommend making yours legible from 2 feet away and using a higher contrast.</span></span>

[!include[Avatar image](~/includes/design/bot-avatar-image.html)]

### <a name="buttons"></a><span data-ttu-id="48e85-113">Botões</span><span class="sxs-lookup"><span data-stu-id="48e85-113">Buttons</span></span>

<span data-ttu-id="48e85-114">Oferecemos suporte para até seis botões por cartão.</span><span class="sxs-lookup"><span data-stu-id="48e85-114">We support up to six buttons per card.</span></span> <span data-ttu-id="48e85-115">Seja conciso ao escrever o texto do botão e lembre-se de que a maioria dos botões só deve solucionar a tarefa em mãos.</span><span class="sxs-lookup"><span data-stu-id="48e85-115">Be concise when writing button text, and keep in mind that most buttons should only address the task at hand.</span></span>

### <a name="graphics"></a><span data-ttu-id="48e85-116">Recurso</span><span class="sxs-lookup"><span data-stu-id="48e85-116">Graphics</span></span>

<span data-ttu-id="48e85-117">Os gráficos são uma boa maneira de informar uma história, mas nem todas as conversas de bot exigem elementos gráficos, portanto, use-as para o máximo impacto.</span><span class="sxs-lookup"><span data-stu-id="48e85-117">Graphics are a good way to tell a story, but not all bot conversations require graphics, so use them for maximum impact.</span></span>

### <a name="responding-to-users-and-failing-gracefully"></a><span data-ttu-id="48e85-118">Responder aos usuários e falhar normalmente</span><span class="sxs-lookup"><span data-stu-id="48e85-118">Responding to users and failing gracefully</span></span>

<span data-ttu-id="48e85-119">Seu bot também deve ser capaz de responder a coisas como "Hi", "Help" e "Thanks", enquanto adota erros comuns de ortografia e coloquialismos em conta.</span><span class="sxs-lookup"><span data-stu-id="48e85-119">Your bot should also be able to respond to things like 'Hi', 'Help', and 'Thanks' while taking common misspellings and colloquialisms into account.</span></span> <span data-ttu-id="48e85-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="48e85-120">For example:</span></span>

#### <a name="x2713-hello"></a><span data-ttu-id="48e85-121">&#x2713; Hello</span><span class="sxs-lookup"><span data-stu-id="48e85-121">&#x2713; Hello</span></span>

<span data-ttu-id="48e85-122">`Hi` `how are you` `howdy`</span><span class="sxs-lookup"><span data-stu-id="48e85-122">`Hi` `how are you` `howdy`</span></span>

#### <a name="x2713-help"></a><span data-ttu-id="48e85-123">&#x2713; ajuda</span><span class="sxs-lookup"><span data-stu-id="48e85-123">&#x2713; Help</span></span>

<span data-ttu-id="48e85-124">`What do you do?` `How does this work?` `What the heck?`</span><span class="sxs-lookup"><span data-stu-id="48e85-124">`What do you do?` `How does this work?` `What the heck?`</span></span>

#### <a name="x2713-thanks"></a><span data-ttu-id="48e85-125">&#x2713; agradecimentos</span><span class="sxs-lookup"><span data-stu-id="48e85-125">&#x2713; Thanks</span></span>

<span data-ttu-id="48e85-126">`Thank you` `thankyou` `thx`</span><span class="sxs-lookup"><span data-stu-id="48e85-126">`Thank you` `thankyou` `thx`</span></span>

<span data-ttu-id="48e85-127">O bot deve ser capaz de lidar com os seguintes tipos de consultas e entradas:</span><span class="sxs-lookup"><span data-stu-id="48e85-127">Your bot should be able to handle the following types of queries and inputs:</span></span>

* <span data-ttu-id="48e85-128">**Perguntas reconhecidas**: Estas são as perguntas de "melhor cenário" que você anteciparia dos usuários.</span><span class="sxs-lookup"><span data-stu-id="48e85-128">**Recognized questions**: These are the “best case scenario” questions you’d anticipate from users.</span></span>
* <span data-ttu-id="48e85-129">**Não há perguntas reconhecidas**: consultas sobre funcionalidades sem suporte, partes aleatórias de informações ou quando alguém deseja repetir o seu bot.</span><span class="sxs-lookup"><span data-stu-id="48e85-129">**Recognized non-questions**: Queries about unsupported functionality, random pieces of information, or when someone wants to curse at your bot.</span></span>
* <span data-ttu-id="48e85-130">**Perguntas não reconhecidas**: entradas não inteligível (por exemplo, ininteligível).</span><span class="sxs-lookup"><span data-stu-id="48e85-130">**Unrecognized questions**: Unintelligible inputs (i.e., gibberish).</span></span>

<span data-ttu-id="48e85-131">Exemplos de personalidade de bot e tipos de resposta:</span><span class="sxs-lookup"><span data-stu-id="48e85-131">Examples of bot personality and response types:</span></span>

[!include[Bot responses](~/includes/design/bot-responses-table.html)]

> [!TIP]
> <span data-ttu-id="48e85-132">Ao escrever seu script de bot, pergunte-se: "minha empresa será embarrassed se uma resposta for capturada e compartilhada?"</span><span class="sxs-lookup"><span data-stu-id="48e85-132">When writing your bot script, ask yourself: “Will my company be embarrassed if a response is screen captured and shared?”</span></span>

### <a name="understanding-what-users-are-trying-to-say"></a><span data-ttu-id="48e85-133">Noções básicas sobre o que os usuários estão tentando dizer</span><span class="sxs-lookup"><span data-stu-id="48e85-133">Understanding what users are trying to say</span></span>

#### <a name="use-a-thesaurus-for-synonyms"></a><span data-ttu-id="48e85-134">Usar um dicionário de sinônimos para sinônimos</span><span class="sxs-lookup"><span data-stu-id="48e85-134">Use a thesaurus for synonyms</span></span>

<span data-ttu-id="48e85-135">Ao fazer o debate de variações, use um dicionário de sinônimos e obtenha às pessoas o máximo de diferentes planos de fundo possíveis para ajudá-lo a gerar diferentes interpretações de cada consulta.</span><span class="sxs-lookup"><span data-stu-id="48e85-135">When brainstorming variants, use a thesaurus and get people from as many different backgrounds as possible to help you generate different interpretations of each query.</span></span>

#### <a name="make-use-of-telemetry-and-interviews"></a><span data-ttu-id="48e85-136">Fazer uso de telemetria e entrevistas</span><span class="sxs-lookup"><span data-stu-id="48e85-136">Make use of telemetry and interviews</span></span>

<span data-ttu-id="48e85-137">Descubra o que os usuários estão dizendo e qual era a intenção de consultar seu bot.</span><span class="sxs-lookup"><span data-stu-id="48e85-137">Find out what users are saying and what was their intent when querying your bot.</span></span> <span data-ttu-id="48e85-138">Este será um processo contínuo à medida que você obtém usuários em diferentes locais e tipos de empresas.</span><span class="sxs-lookup"><span data-stu-id="48e85-138">This will be an ongoing process as you get users in different locations and types of companies.</span></span> <span data-ttu-id="48e85-139">Você pode ajustar o reconhecimento de idioma e o mapeamento de intenções com o idioma entendendo o serviço inteligente ([Luis](/azure/cognitive-services/luis/what-is-luis)).</span><span class="sxs-lookup"><span data-stu-id="48e85-139">You can fine-tune language recognition and intent mapping with Language Understanding Intelligent Service ([LUIS](/azure/cognitive-services/luis/what-is-luis)).</span></span>

### <a name="how-often-should-you-use-your-bot-to-reach-out-to-a-user"></a><span data-ttu-id="48e85-140">Com que frequência você deve usar o bot para entrar em um usuário?</span><span class="sxs-lookup"><span data-stu-id="48e85-140">How often should you use your bot to reach out to a user?</span></span>

#### <a name="x2713-when-a-state-has-changed"></a><span data-ttu-id="48e85-141">&#x2713; quando um estado tiver sido alterado</span><span class="sxs-lookup"><span data-stu-id="48e85-141">&#x2713; When a state has changed</span></span>

<span data-ttu-id="48e85-142">Por exemplo, se uma atribuição for marcada como concluída, quando um erro for alterado, quando uma nova mídia social estiver disponível ou quando uma pesquisa tiver sido concluída.</span><span class="sxs-lookup"><span data-stu-id="48e85-142">For example, if an assignment is marked as complete, when a bug changes, when new social media is available, or when a poll has been completed.</span></span>

#### <a name="x2713-when-the-timing-is-right"></a><span data-ttu-id="48e85-143">&#x2713; quando o intervalo é para a direita</span><span class="sxs-lookup"><span data-stu-id="48e85-143">&#x2713; When the timing is right</span></span>

<span data-ttu-id="48e85-144">Seu bot pode agir como um resumo diário, enviando uma notificação para o usuário ou canal em uma frequência específica.</span><span class="sxs-lookup"><span data-stu-id="48e85-144">Your bot can act like a daily digest, sending a notification to the user or channel at a specific frequency.</span></span>

<span data-ttu-id="48e85-145">Deixe o usuário no controle.</span><span class="sxs-lookup"><span data-stu-id="48e85-145">Leave the user in control.</span></span> <span data-ttu-id="48e85-146">Fornecer configurações de notificação que incluem frequência e prioridade.</span><span class="sxs-lookup"><span data-stu-id="48e85-146">Provide notification settings that include frequency and priority.</span></span>

[!include[Bot notification](~/includes/design/bot-notification-image.html)]

---

## <a name="using-tabs"></a><span data-ttu-id="48e85-147">Usando guias</span><span class="sxs-lookup"><span data-stu-id="48e85-147">Using tabs</span></span>

<span data-ttu-id="48e85-148">As guias tornam o bot muito mais funcional.</span><span class="sxs-lookup"><span data-stu-id="48e85-148">Tabs make your bot much more functional.</span></span> <span data-ttu-id="48e85-149">Com guias, você pode criar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="48e85-149">With tabs, you can create the following:</span></span>

### <a name="x2713-a-place-to-host-standing-queries"></a><span data-ttu-id="48e85-150">&#x2713; um local para hospedar consultas em pé</span><span class="sxs-lookup"><span data-stu-id="48e85-150">&#x2713; A place to host standing queries</span></span>

<span data-ttu-id="48e85-151">Em conversas pessoais entre um bot e uma única pessoa, as guias podem alojar informações e listas específicas do usuário.</span><span class="sxs-lookup"><span data-stu-id="48e85-151">In personal conversations between a bot and a single person, tabs can house user-specific information and lists.</span></span> <span data-ttu-id="48e85-152">Eles também são um bom local para manter respostas de bot para perguntas frequentes (FAQs), de modo que os usuários não precisem continuar fazendo isso.</span><span class="sxs-lookup"><span data-stu-id="48e85-152">They’re also a good place to maintain bot responses to frequently-asked questions (FAQs) — so users don’t need to keep asking.</span></span>

### <a name="x2713-a-place-to-finish-a-conversation"></a><span data-ttu-id="48e85-153">&#x2713; um local para concluir uma conversa</span><span class="sxs-lookup"><span data-stu-id="48e85-153">&#x2713; A place to finish a conversation</span></span>

<span data-ttu-id="48e85-154">Você pode vincular a uma guia de um cartão.</span><span class="sxs-lookup"><span data-stu-id="48e85-154">You can link to a tab from a card.</span></span> <span data-ttu-id="48e85-155">Se o seu bot fornecer uma resposta que exija algumas etapas adicionais, ele pode vincular a uma guia para concluir a tarefa ou o fluxo.</span><span class="sxs-lookup"><span data-stu-id="48e85-155">If your bot provides an answer that requires a few more steps, it can link to a tab to complete the task or flow.</span></span>

### <a name="x2713-a-place-to-provide-some-help"></a><span data-ttu-id="48e85-156">&#x2713; um local para fornecer ajuda</span><span class="sxs-lookup"><span data-stu-id="48e85-156">&#x2713; A place to provide some help</span></span>

<span data-ttu-id="48e85-157">Adicione uma guia que instrua os usuários sobre como se comunicar com o bot.</span><span class="sxs-lookup"><span data-stu-id="48e85-157">Add a tab that educates users about how to communicate with your bot.</span></span> <span data-ttu-id="48e85-158">Você pode fornecer um contexto para o que ele faz ou perguntas frequentes.</span><span class="sxs-lookup"><span data-stu-id="48e85-158">You can provide some context for what it does or FAQs.</span></span>

![Fornecer ajuda](~/assets/images/framework/framework_bots_tbot-help.png)

> [!TIP]
> <span data-ttu-id="48e85-160">A incorporação de partes do seu site em uma guia ajudará alguém a manter o contexto de uma conversa enquanto usa o serviço.</span><span class="sxs-lookup"><span data-stu-id="48e85-160">Embedding parts of your site in a tab will help someone maintain the context of a conversation as they use your service.</span></span> <span data-ttu-id="48e85-161">Ele remove a necessidade de iniciar o serviço em um navegador e alternar entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="48e85-161">It removes the need to launch your service in a browser and switch back and forth between apps.</span></span>

---

## <a name="best-practices"></a><span data-ttu-id="48e85-162">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="48e85-162">Best practices</span></span>

### <a name="x2713-bots-arent-assistants"></a><span data-ttu-id="48e85-163">&#x2713; bots não são assistentes</span><span class="sxs-lookup"><span data-stu-id="48e85-163">&#x2713; Bots aren’t assistants</span></span>

<span data-ttu-id="48e85-164">Diferentemente de agentes, por exemplo, Cortana, bots atuam como especialistas.</span><span class="sxs-lookup"><span data-stu-id="48e85-164">Unlike agents, e.g., Cortana, bots act as specialists.</span></span>

### <a name="x2713-discourage-chitchat"></a><span data-ttu-id="48e85-165">&#x2713; desencorajar Chitchat</span><span class="sxs-lookup"><span data-stu-id="48e85-165">&#x2713; Discourage chitchat</span></span>

<span data-ttu-id="48e85-166">A menos que seu bot seja criado para conversa, encontre maneiras de redirecionar Chitchat para a conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="48e85-166">Unless your bot is built for conversation, find ways to redirect chitchat toward task completion.</span></span>

### <a name="x2713-introduce-some-personality"></a><span data-ttu-id="48e85-167">&#x2713; apresentar algumas personalidades</span><span class="sxs-lookup"><span data-stu-id="48e85-167">&#x2713; Introduce some personality</span></span>

<span data-ttu-id="48e85-168">Mantenha sua personalidade de bot consistente com a voz do seu produto.</span><span class="sxs-lookup"><span data-stu-id="48e85-168">Keep your bot personality consistent with the voice of your product.</span></span> <span data-ttu-id="48e85-169">Pense no bot como palestra à sua empresa.</span><span class="sxs-lookup"><span data-stu-id="48e85-169">Think of your bot as speaking for your company.</span></span>

### <a name="x2713-maintain-tone"></a><span data-ttu-id="48e85-170">&#x2713; manter Tom</span><span class="sxs-lookup"><span data-stu-id="48e85-170">&#x2713; Maintain tone</span></span>

<span data-ttu-id="48e85-171">Determine se você deseja que o Tom seja amigável e claro, "apenas os fatos" ou a mais peculiaridades.</span><span class="sxs-lookup"><span data-stu-id="48e85-171">Determine whether you want your tone to be friendly and light, “just the facts”, or super quirky.</span></span>

### <a name="x2713-encourage-easy-task-flow"></a><span data-ttu-id="48e85-172">&#x2713; incentivar o fluxo de tarefas fácil</span><span class="sxs-lookup"><span data-stu-id="48e85-172">&#x2713; Encourage easy task flow</span></span>

<span data-ttu-id="48e85-173">Dê suporte a interações de várias perfeitas e ainda permitindo perguntas totalmente formadas.</span><span class="sxs-lookup"><span data-stu-id="48e85-173">Support multi-turn interactions while still allowing for fully formed questions.</span></span> <span data-ttu-id="48e85-174">Prever a próxima etapa ajudará os usuários a obter muito mais facilidade nos fluxos de tarefas.</span><span class="sxs-lookup"><span data-stu-id="48e85-174">Anticipating the next step will help users get through task flows much easier.</span></span>

<span data-ttu-id="48e85-175">Se um usuário executar várias etapas para concluir uma tarefa, permita que o bot as assuma por meio de cada etapa, mas termine por ter sugerido um caminho mais rápido.</span><span class="sxs-lookup"><span data-stu-id="48e85-175">If a user takes several steps to complete a task, allow your bot to take them through each step, but finish by having it suggest a quicker path.</span></span> <span data-ttu-id="48e85-176">Por exemplo, se um usuário levou várias pessoas para definir uma reunião (especificando primeiro uma reunião e, em seguida, identificando com quem e, em seguida, informando a hora e, em seguida, informando o dia), conclua a conversa com a seguinte sugestão: na próxima vez, tente perguntar se você é possível agendar uma reunião com Bob em 1:00 amanhã.</span><span class="sxs-lookup"><span data-stu-id="48e85-176">For example, if a user has taken several conversational turns to set a meeting (by first specifying a meeting, then identifying with whom, then stating the time, then stating the day), finish the conversation with the following suggestion: Next time, try asking if you can ‘schedule a meeting with Bob at 1:00 tomorrow’.</span></span>