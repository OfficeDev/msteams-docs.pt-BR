---
title: Designar cartões eficazes
description: Descreve as diretrizes de design para criar cartões
keywords: Diretrizes de design de equipes referência de cartões de estrutura de referência leve
ms.openlocfilehash: 4ec410820e0288d99dacb6944a8096f4f61b9d34
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48209834"
---
# <a name="design-effective-cards"></a><span data-ttu-id="8abe4-104">Designar cartões eficazes</span><span class="sxs-lookup"><span data-stu-id="8abe4-104">Design effective cards</span></span>

<span data-ttu-id="8abe4-105">Os cartões são trechos acionáveis do conteúdo que você pode adicionar a uma conversa através de um bot, um conector ou um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8abe4-105">Cards are actionable snippets of content that you can add to a conversation through a bot, a connector, or app.</span></span> <span data-ttu-id="8abe4-106">Usando texto, elementos gráficos e botões, os cartões permitem que você se comunique com uma audiência.</span><span class="sxs-lookup"><span data-stu-id="8abe4-106">Using text, graphics, and buttons, cards allow you to communicate with an audience.</span></span>

<span data-ttu-id="8abe4-107">Nossa estrutura de cartão elimina o ônus de projetar um UX totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="8abe4-107">Our card framework eliminates the burden of designing a fully functional UX.</span></span> <span data-ttu-id="8abe4-108">Desenvolvemos vários tipos de cartões padrão e cada um cabe em nossas plataformas suportadas.</span><span class="sxs-lookup"><span data-stu-id="8abe4-108">We developed several standard card types and each one fits within our supported platforms.</span></span> <span data-ttu-id="8abe4-109">Isso significa que o layout está totalmente encaredo e você não precisará desenvolver iterações de cartão diferentes entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="8abe4-109">This means layout is completely taken care of, and you won’t need to develop different card iterations across platforms.</span></span> <span data-ttu-id="8abe4-110">Em vez disso, você pode se concentrar na discagem em seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8abe4-110">Instead, you can focus on dialing in your content.</span></span>

---

## <a name="guidelines"></a><span data-ttu-id="8abe4-111">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="8abe4-111">Guidelines</span></span>

<span data-ttu-id="8abe4-112">Considere um cartão como uma resposta a uma pergunta de usuário ou uma configuração.</span><span class="sxs-lookup"><span data-stu-id="8abe4-112">Think of a card as a response to a user question or a setting.</span></span> <span data-ttu-id="8abe4-113">Um cartão pode responder a uma pergunta direta (como "quantos erros abertos eu tenho?") ou a uma condição (como "Enviar uma lista de meus bugs abertos às 9 AM todos os dias").</span><span class="sxs-lookup"><span data-stu-id="8abe4-113">A card can respond to a direct question (like, “How many open bugs do I have?”) or to a condition (like, “Send a list of my open bugs at 9 am every day”).</span></span>

> [!TIP]
> <span data-ttu-id="8abe4-114">O uso de um dos nossos tipos de cartão padrão significa que você já saberá que todas as suas respostas serão bem processadas em todas as plataformas suportadas.</span><span class="sxs-lookup"><span data-stu-id="8abe4-114">Using one of our standard card types means you’ll already know that all your responses will render nicely across each supported platform.</span></span>

<span data-ttu-id="8abe4-115">Um cartão pode incluir qualquer um dos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="8abe4-115">A card could include any of the following elements:</span></span><br />

[!include[Card anatomy](~/includes/design/card-image-anatomy.html)]

1. <span data-ttu-id="8abe4-116">**Texto do envelope**: melhor usado para mensagens de chat.</span><span class="sxs-lookup"><span data-stu-id="8abe4-116">**Envelope text**: Best used for chat messages.</span></span> <span data-ttu-id="8abe4-117">Por exemplo, se você deseja que um bot diga: "aqui está o que eu encontrei!"</span><span class="sxs-lookup"><span data-stu-id="8abe4-117">For example, if you want a bot to say: “Here’s what I found!”</span></span> <span data-ttu-id="8abe4-118">ou "hora do seu resumo de notícias do 1:00", essa mensagem é melhor exibida no texto do envelope.</span><span class="sxs-lookup"><span data-stu-id="8abe4-118">or “Time for your 1:00 news digest”, that message is best displayed in envelope text.</span></span>

   <span data-ttu-id="8abe4-119">O texto do envelope é uma ótima maneira de injetar uma pequena personalidade no seu serviço, apenas se lembre de mantê-lo relativamente curto.</span><span class="sxs-lookup"><span data-stu-id="8abe4-119">Envelope text is a great way to inject a little personality into your service—just remember to keep it relatively short.</span></span>

2. <span data-ttu-id="8abe4-120">**Título**: seu título sempre será o maior texto no seu cartão.</span><span class="sxs-lookup"><span data-stu-id="8abe4-120">**Title**: Your title will always be the largest text in your card.</span></span> <span data-ttu-id="8abe4-121">Ele também serve como seu "gancho", portanto, tente manter o título curto, fácil de lembrar e fácil de digitalizar.</span><span class="sxs-lookup"><span data-stu-id="8abe4-121">It also serves as your “hook”, so try to keep the title short, memorable, and easy to scan.</span></span>

3. <span data-ttu-id="8abe4-122">**Subtítulo**: melhor usado para atribuição, mote ou como uma diretiva secundária.</span><span class="sxs-lookup"><span data-stu-id="8abe4-122">**Subtitle**: Best used for attribution, taglines, or as a secondary directive.</span></span> <span data-ttu-id="8abe4-123">Este componente aparece logo abaixo do título.</span><span class="sxs-lookup"><span data-stu-id="8abe4-123">This component appears just below your title.</span></span>

4. <span data-ttu-id="8abe4-124">**Image**: as imagens são dimensionadas de acordo com o contêiner.</span><span class="sxs-lookup"><span data-stu-id="8abe4-124">**Image**: Images scale to fit their container.</span></span> <span data-ttu-id="8abe4-125">Os cartões herói têm uma largura máxima de 420px, as miniaturas têm uma largura máxima de 100px e os modos de exibição de lista só permitem o medianiz 32px no modo de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8abe4-125">Hero cards have a max width of 420px, thumbnails have a max width of 100px, and list views only allow for 32px in desktop mode.</span></span>

5. <span data-ttu-id="8abe4-126">**Texto**: melhor usado para texto sem formatação no corpo do cartão.</span><span class="sxs-lookup"><span data-stu-id="8abe4-126">**Text**: Best used for plain text in the body of your card.</span></span> <span data-ttu-id="8abe4-127">O tamanho máximo depende do tipo de cartão que você selecionou.</span><span class="sxs-lookup"><span data-stu-id="8abe4-127">Your max length depends on the card type you’ve selected.</span></span>

6. <span data-ttu-id="8abe4-128">**Botões**: melhor usado para abrir páginas da Web, guias ou conteúdo de chat adicional.</span><span class="sxs-lookup"><span data-stu-id="8abe4-128">**Buttons**: Best used to open web pages, tabs, or additional chat content.</span></span> <span data-ttu-id="8abe4-129">Certifique-se de manter o texto do botão curto e para o ponto.</span><span class="sxs-lookup"><span data-stu-id="8abe4-129">Make sure to keep your button text short and to the point.</span></span>

   <span data-ttu-id="8abe4-130">Você pode incluir até 6 botões por cartão, mas seria recomendável seguir uma filosofia ' menos mais ' aqui.</span><span class="sxs-lookup"><span data-stu-id="8abe4-130">You can include up to 6 buttons per card, but we’d recommend following a ‘less is more’ philosophy here.</span></span>

7. <span data-ttu-id="8abe4-131">**Região de toque**: esta é a região de clique do cartão.</span><span class="sxs-lookup"><span data-stu-id="8abe4-131">**Tap region**: This is the clickable region of your card.</span></span> <span data-ttu-id="8abe4-132">A maioria dos usuários desejará clicar em imagens automaticamente, portanto, experimente e crie seu texto para que eles saibam onde devem tocar ou clicar.</span><span class="sxs-lookup"><span data-stu-id="8abe4-132">Most users will want to click on images automatically, so try and craft your text so they know where they should tap or click.</span></span>

> [!TIP]
> <span data-ttu-id="8abe4-133">Não é necessário incluir todos os elementos em cada cartão que você criar.</span><span class="sxs-lookup"><span data-stu-id="8abe4-133">There’s no need to include every element in each card you create.</span></span> <span data-ttu-id="8abe4-134">Permitir que o conteúdo dite seus elementos.</span><span class="sxs-lookup"><span data-stu-id="8abe4-134">Let your content dictate your elements.</span></span>

---

## <a name="types-of-cards"></a><span data-ttu-id="8abe4-135">Tipos de cartões</span><span class="sxs-lookup"><span data-stu-id="8abe4-135">Types of cards</span></span>

### <a name="hero"></a><span data-ttu-id="8abe4-136">Destaque</span><span class="sxs-lookup"><span data-stu-id="8abe4-136">Hero</span></span>

<span data-ttu-id="8abe4-137">Nosso maior cartão.</span><span class="sxs-lookup"><span data-stu-id="8abe4-137">Our largest card.</span></span> <span data-ttu-id="8abe4-138">Melhor usado para artigos, descrições longas ou cenários em que a imagem está informando a maior parte da história.</span><span class="sxs-lookup"><span data-stu-id="8abe4-138">Best used for articles, long descriptions, or scenarios where your image is telling most of the story.</span></span>

[!include[Card anatomy](~/includes/design/card-image-hero.html)]

### <a name="thumbnail"></a><span data-ttu-id="8abe4-139">Thumbnail</span><span class="sxs-lookup"><span data-stu-id="8abe4-139">Thumbnail</span></span>

<span data-ttu-id="8abe4-140">Curta e doce.</span><span class="sxs-lookup"><span data-stu-id="8abe4-140">Short and sweet.</span></span> <span data-ttu-id="8abe4-141">Esses cartões são ideais para respostas curtas ou se você deseja retornar vários cartões de uma só vez, para que o usuário possa escolher entre várias opções.</span><span class="sxs-lookup"><span data-stu-id="8abe4-141">These cards are ideal for short answers, or if you want to return several cards at once so the user can choose from a bunch of options.</span></span> <span data-ttu-id="8abe4-142">Acreditamos que essas são uma ótima maneira de vincular detalhadamente a outra guia ou serviço Web.</span><span class="sxs-lookup"><span data-stu-id="8abe4-142">We think these are a great way to deep link to another tab or a web service.</span></span>

[!include[Card anatomy](~/includes/design/card-image-thumbnail.html)]

### <a name="sign-in"></a><span data-ttu-id="8abe4-143">Entrar</span><span class="sxs-lookup"><span data-stu-id="8abe4-143">Sign in</span></span>

<span data-ttu-id="8abe4-144">Alguns serviços exigem que os usuários entrem de forma independente da nossa autenticação.</span><span class="sxs-lookup"><span data-stu-id="8abe4-144">Some services require users to sign in independently of our authentication.</span></span> <span data-ttu-id="8abe4-145">Nesse caso, você apresentaria um cartão de conexão antes que o usuário possa se conectar ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="8abe4-145">In that event, you would present a sign-in card before the user can connect to your service.</span></span>

[!include[Card anatomy](~/includes/design/card-image-signin.html)]

> [!TIP]
> <span data-ttu-id="8abe4-146">Limitar as ocorrências de um cartão de entrada adicional, uma vez que elas representam uma considerável bomba de velocidade para novos usuários.</span><span class="sxs-lookup"><span data-stu-id="8abe4-146">Limit the occurrences of an additional sign-in card since they pose a significant speed bump for new users.</span></span>

---

## <a name="card-collections"></a><span data-ttu-id="8abe4-147">Coleções de cartões</span><span class="sxs-lookup"><span data-stu-id="8abe4-147">Card collections</span></span>

<span data-ttu-id="8abe4-148">Também temos tipos de cartões padrão que são mais usados quando você deseja apresentar vários pedaços de conteúdo de uma só vez ou em uma sucessão rápida.</span><span class="sxs-lookup"><span data-stu-id="8abe4-148">We also have standard card types that are best used when you want to present several pieces of content at once or in quick succession.</span></span> <span data-ttu-id="8abe4-149">Para essa finalidade, temos um carrossel, um resumo, uma lista e o que chamamos de uma ' mesclagem em bolha '.</span><span class="sxs-lookup"><span data-stu-id="8abe4-149">For that purpose, we have a carousel, a digest, a list, and what we call a ‘bubble merge’.</span></span>

### <a name="carousel"></a><span data-ttu-id="8abe4-150">Carrossel</span><span class="sxs-lookup"><span data-stu-id="8abe4-150">Carousel</span></span>

<span data-ttu-id="8abe4-151">Melhor usado para artigos, compras e navegação através de cartões.</span><span class="sxs-lookup"><span data-stu-id="8abe4-151">Best used for articles, shopping, and browsing through cards.</span></span>

[!include[Card anatomy](~/includes/design/card-image-carousel.html)]

> [!TIP]
> <span data-ttu-id="8abe4-152">O carrossel será a altura máxima do seu maior cartão.</span><span class="sxs-lookup"><span data-stu-id="8abe4-152">The carousel will be the max height of your largest card.</span></span> <span data-ttu-id="8abe4-153">Recomendamos o uso do mesmo tipo de cartão e campos de conteúdo no todo.</span><span class="sxs-lookup"><span data-stu-id="8abe4-153">We recommend using the same card type and content fields throughout.</span></span>

### <a name="digest"></a><span data-ttu-id="8abe4-154">Digest</span><span class="sxs-lookup"><span data-stu-id="8abe4-154">Digest</span></span>

<span data-ttu-id="8abe4-155">Melhor usado para notícias, resumos e sempre que você deseja que o usuário exiba vários cartões de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="8abe4-155">Best used for news, digests, and whenever you want the user to view multiple cards at once.</span></span> <span data-ttu-id="8abe4-156">Recomendamos o uso de cartões de miniatura para resumos.</span><span class="sxs-lookup"><span data-stu-id="8abe4-156">We recommend using thumbnail cards for digests.</span></span>

[!include[Card anatomy](~/includes/design/card-image-digest.html)]

### <a name="lists"></a><span data-ttu-id="8abe4-157">Listas</span><span class="sxs-lookup"><span data-stu-id="8abe4-157">Lists</span></span>

<span data-ttu-id="8abe4-158">As listas são uma ótima maneira de apresentar um conjunto de objetos que podem ser varridos em um cenário "escolha um destes".</span><span class="sxs-lookup"><span data-stu-id="8abe4-158">Lists are a great way to present a scannable set of objects in a “pick one of these” scenario.</span></span> <span data-ttu-id="8abe4-159">As listas são melhores usadas para itens que não precisam de muita explicação.</span><span class="sxs-lookup"><span data-stu-id="8abe4-159">Lists are best used for items that don’t need a lot of explanation.</span></span>

[!include[Card anatomy](~/includes/design/card-image-list.html)]

### <a name="bubble-merge"></a><span data-ttu-id="8abe4-160">Mesclagem em bolha</span><span class="sxs-lookup"><span data-stu-id="8abe4-160">Bubble merge</span></span>

<span data-ttu-id="8abe4-161">Alguns efeitos interessantes podem ser obtidos enviando um herói e várias miniaturas em uma sucessão rápida.</span><span class="sxs-lookup"><span data-stu-id="8abe4-161">Some interesting effects can be achieved by sending one hero and several thumbnails in quick succession.</span></span> <span data-ttu-id="8abe4-162">Recomendamos essa abordagem quando você quiser atender um resultado principal, mas incluir alguns itens relacionados.</span><span class="sxs-lookup"><span data-stu-id="8abe4-162">We recommend this approach when you want to serve a main result but include a few more related items.</span></span>

[!include[Card anatomy](~/includes/design/card-image-bubble-merge.html)]

---

## <a name="best-practices"></a><span data-ttu-id="8abe4-163">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="8abe4-163">Best practices</span></span>

### <a name="keep-the-noise-down"></a><span data-ttu-id="8abe4-164">Mantenha o ruído pressionado</span><span class="sxs-lookup"><span data-stu-id="8abe4-164">Keep the noise down</span></span>

<span data-ttu-id="8abe4-165">É fácil enviar vários cartões para uma conversa, mas depois que os cartões saem do modo de exibição, eles se tornam menos úteis.</span><span class="sxs-lookup"><span data-stu-id="8abe4-165">It’s easy to send multiple cards into a conversation, but once cards scroll out of view, they become less useful.</span></span> <span data-ttu-id="8abe4-166">Tente se limitar ao Essentials.</span><span class="sxs-lookup"><span data-stu-id="8abe4-166">Try to limit yourself to the essentials.</span></span> <span data-ttu-id="8abe4-167">Isso se aplica especialmente em um canal em que os usuários têm menos tolerância para o que eles percebem como "ruído".</span><span class="sxs-lookup"><span data-stu-id="8abe4-167">This is especially true in a channel where users have less tolerance for what they perceive as “noise”.</span></span>

### <a name="test-on-mobile"></a><span data-ttu-id="8abe4-168">Testar em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="8abe4-168">Test on mobile</span></span>

<span data-ttu-id="8abe4-169">Os ambientes móveis são restritos por espaço e largura de banda, portanto, tenha cuidado ao incluir imagens de tamanho excessivo e conjuntos de dados grandes em listas e carrossel.</span><span class="sxs-lookup"><span data-stu-id="8abe4-169">Mobile environments are space- and bandwidth-constrained, so be cautious about including oversized images and large data sets in lists and carousels.</span></span> <span data-ttu-id="8abe4-170">Além disso, as larguras de título e os comprimentos de texto ficarão truncados em dispositivos móveis, portanto, outra coisa para ficar atento.</span><span class="sxs-lookup"><span data-stu-id="8abe4-170">Also, title widths and text lengths will truncate on mobile, so that’s another thing to keep an eye on.</span></span>

### <a name="check-your-graphics"></a><span data-ttu-id="8abe4-171">Verifique seus elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="8abe4-171">Check your graphics</span></span>

<span data-ttu-id="8abe4-172">Os elementos gráficos serão dimensionados e, portanto, não se esqueça de visualizá-los em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="8abe4-172">Graphics are going to scale, so be sure to preview them on all platforms.</span></span>

### <a name="avoid-including-text-in-a-graphic"></a><span data-ttu-id="8abe4-173">Evitar incluir texto em um gráfico</span><span class="sxs-lookup"><span data-stu-id="8abe4-173">Avoid including text in a graphic</span></span>

<span data-ttu-id="8abe4-174">Tudo o que precisa ser lido por um usuário deve ser incluído em um campo de texto.</span><span class="sxs-lookup"><span data-stu-id="8abe4-174">Anything that needs to be read by a user should be included in a text field.</span></span> <span data-ttu-id="8abe4-175">Após a escala dinâmica de uma imagem, qualquer texto que você adicionar a um gráfico poderá se tornar ininteligível.</span><span class="sxs-lookup"><span data-stu-id="8abe4-175">Once an image is dynamically scaled, any text you add to a graphic may become unintelligible.</span></span>

### <a name="use-mentions-if-you-want-the-attention-of-specific-users"></a><span data-ttu-id="8abe4-176">Use menção se quiser a atenção de usuários específicos</span><span class="sxs-lookup"><span data-stu-id="8abe4-176">Use mentions if you want the attention of specific users</span></span>

> [!NOTE]
> <span data-ttu-id="8abe4-177">Mencione o suporte nos cartões atualmente é suportado apenas na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md) .</span><span class="sxs-lookup"><span data-stu-id="8abe4-177">Mention support in cards is currently supported in [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="8abe4-178">As mencionas são uma ótima maneira de notificar usuários específicos em uma equipe ou em um chat de grupo.</span><span class="sxs-lookup"><span data-stu-id="8abe4-178">Mentions are a great way to notify specific users in a Team or group chat.</span></span> <span data-ttu-id="8abe4-179">Você pode incluir um cartão em cenários, como uma tarefa atribuída a um usuário ou fornecer Parabéns a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="8abe4-179">You can include a mention in card in scenarios like, a task thats assigned to a user or giving Kudos to a teammate.</span></span> <span data-ttu-id="8abe4-180">Saiba como incluir mençãos em cartões na página de [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="8abe4-180">Learn how to include mentions in cards in the [card formatting page](~/task-modules-and-cards/cards/cards-format.md).</span></span> 
