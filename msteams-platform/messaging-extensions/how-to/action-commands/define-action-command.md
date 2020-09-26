---
title: Definir comandos de ação de extensão de mensagens
author: clearab
description: Uma visão geral das extensões de mensagens na plataforma do Microsoft Teams
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 89cf92260418701ef4809f5a13750b991b9f7acb
ms.sourcegitcommit: b51a4982842948336cfabedb63bdf8f72703585e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "48279678"
---
# <a name="define-messaging-extension-action-commands"></a><span data-ttu-id="8d4dc-103">Definir comandos de ação de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="8d4dc-103">Define messaging extension action commands</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="8d4dc-104">Os comandos de ação permitem que você apresente aos seus usuários um pop-up modal (chamado de módulo de tarefa no Microsoft Teams) para coletar ou exibir informações e, em seguida, processar sua interação e enviar informações de volta para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-104">Action commands allow you present your users with a modal popup (called a task module in Teams) to collect or display information, then process their interaction and send information back to Teams.</span></span> <span data-ttu-id="8d4dc-105">Antes de criar seu comando, você precisará decidir:</span><span class="sxs-lookup"><span data-stu-id="8d4dc-105">Before creating your command you'll need to decide:</span></span>

1. <span data-ttu-id="8d4dc-106">De onde pode ser disparado o comando Action?</span><span class="sxs-lookup"><span data-stu-id="8d4dc-106">Where can the action command be triggered from?</span></span>
1. <span data-ttu-id="8d4dc-107">Como o módulo de tarefa será criado?</span><span class="sxs-lookup"><span data-stu-id="8d4dc-107">How will the task module be created?</span></span>
1. <span data-ttu-id="8d4dc-108">A mensagem ou o cartão final será enviado para o canal de um bot ou a mensagem ou o cartão será inserido na área de mensagem de redação para o usuário enviar?</span><span class="sxs-lookup"><span data-stu-id="8d4dc-108">Will the final message or card be sent to the channel from a bot, or will the message or card be inserted into the compose message area for the user to submit?</span></span>

## <a name="choose-action-command-invoke-locations"></a><span data-ttu-id="8d4dc-109">Selecionar locais de invocação de comando de ação</span><span class="sxs-lookup"><span data-stu-id="8d4dc-109">Choose action command invoke locations</span></span>

<span data-ttu-id="8d4dc-110">A primeira coisa que você precisa decidir é onde o comando de ação pode ser acionado (ou mais especificamente, *invocado*) a partir do.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-110">The first thing you need to decide is where your action command can be triggered (or more specifically, *invoked*) from.</span></span> <span data-ttu-id="8d4dc-111">Ao especificar o `context` em seu manifesto de aplicativo, seu comando pode ser chamado a partir de um ou mais dos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="8d4dc-111">By specifying the `context` in your app manifest, your command can be invoked from one or more of the following locations:</span></span>

* <span data-ttu-id="8d4dc-112">Os botões na parte inferior da área de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-112">The buttons at the bottom of the compose message area.</span></span>
* <span data-ttu-id="8d4dc-113">Por @mentioning seu aplicativo na caixa de comando.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-113">By @mentioning your app in the command box.</span></span> <span data-ttu-id="8d4dc-114">Observação: você não pode responder com uma mensagem de bot inserida diretamente na conversa se sua extensão de mensagens for invocada na caixa de comando.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-114">Note: You cannot respond with a bot message inserted directly into the conversation if your messaging extension is invoked from the command box.</span></span>
* <span data-ttu-id="8d4dc-115">Diretamente de uma mensagem existente por meio de... menu de estouro em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-115">Directly from an existing message via the ... overflow menu on a message.</span></span> <span data-ttu-id="8d4dc-116">Observação: a chamada inicial para o bot incluirá um objeto JSON que contém a mensagem da qual foi invocado, o que você pode processar antes de apresentá-los com um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-116">Note: The initial invoke to your bot will include a JSON object containing the message from which it was invoked, which you can process before presenting them with a task module.</span></span>

## <a name="choose-how-to-build-your-task-module"></a><span data-ttu-id="8d4dc-117">Escolha como criar seu módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="8d4dc-117">Choose how to build your task module</span></span>

<span data-ttu-id="8d4dc-118">Além de escolher onde o comando pode ser chamado, você também deve escolher como preencher o formulário no módulo de tarefa para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-118">In addition to choosing where your command can be invoked from, you must also chose how to populate the form in the task module for your users.</span></span> <span data-ttu-id="8d4dc-119">Você tem três opções para criar o formulário que é renderizado no módulo de tarefa:</span><span class="sxs-lookup"><span data-stu-id="8d4dc-119">You have three options for creating the form that is rendered inside the task module:</span></span>

* <span data-ttu-id="8d4dc-120">**Lista estática de parâmetros** -esta é a opção mais simples.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-120">**Static list of parameters** - This is the simplest option.</span></span> <span data-ttu-id="8d4dc-121">Você pode definir uma lista de parâmetros (campos de entrada) em seu manifesto de aplicativo que o cliente do teams processará.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-121">You can define a list of parameters (input fields) in your app manifest the Teams client will render.</span></span> <span data-ttu-id="8d4dc-122">Você não pode controlar a formatação com essa opção.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-122">You cannot control the formatting with this option.</span></span>
* <span data-ttu-id="8d4dc-123">**Cartão adaptável** : você pode optar por usar um cartão adaptável, que oferece maior controle sobre a interface do usuário, mas ainda limita você sobre os controles disponíveis e as opções de formatação.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-123">**Adaptive card** - You can choose to use an adaptive card, which provides greater control over the UI, but still limits you on the available controls and formatting options.</span></span>
* <span data-ttu-id="8d4dc-124">**Modo de exibição da Web incorporado** -se você precisar de controle completo sobre a interface do usuário e os controles, você pode optar por inserir um modo de exibição da Web personalizado no módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-124">**Embedded web view** - If you need complete control over the UI and controls, you can choose to embed a custom web view in the task module.</span></span>

<span data-ttu-id="8d4dc-125">Se você optar por criar seu módulo de tarefa com uma lista estática de parâmetros, a primeira chamada para sua extensão de mensagens será quando um usuário enviar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-125">If you choose to create your task module with a static list of parameters, the first call to your messaging extension will be when a user submits the task module.</span></span> <span data-ttu-id="8d4dc-126">Ao usar um modo de exibição da Web incorporado ou um cartão adaptável, sua extensão de mensagens precisará lidar com um evento de chamada inicial do usuário, criar o módulo de tarefa e retorná-lo ao cliente.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-126">When using an embedded web view or an adaptive card, your messaging extension will need to handle an initial invoke event from the user, create the task module, and return it back to the client.</span></span>

## <a name="choose-how-the-final-message-will-be-sent"></a><span data-ttu-id="8d4dc-127">Escolha como a mensagem final será enviada</span><span class="sxs-lookup"><span data-stu-id="8d4dc-127">Choose how the final message will be sent</span></span>

<span data-ttu-id="8d4dc-128">Na maioria dos casos, o comando de ação resultará em um cartão inserido na caixa de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-128">In most cases, your action command will result in a card inserted into the compose message box.</span></span> <span data-ttu-id="8d4dc-129">Em seguida, o usuário pode optar por enviá-lo para o canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-129">Your user can then decide to send it into the channel or chat.</span></span> <span data-ttu-id="8d4dc-130">A mensagem nesse caso vem do usuário e seu bot não poderá editar ou atualizar o cartão mais tarde.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-130">The message in this case comes from the user, and your bot will not be able to edit or update the card further.</span></span>

<span data-ttu-id="8d4dc-131">Se sua extensão de mensagens é disparada a partir da caixa de redação ou diretamente de uma mensagem, seu serviço Web pode inserir a resposta final diretamente no canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-131">If your messaging extension is triggered from the compose box or directly from a message, your web service can insert the final response directly into the channel or chat.</span></span> <span data-ttu-id="8d4dc-132">Nesse caso, o cartão adaptável é proveniente do bot, o bot será capaz de atualizá-lo, e o bot também poderá responder ao thread de conversa, se necessário.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-132">In this case, the adaptive card comes from the bot, the bot will be able to update it, and the bot can also reply to the conversation thread if needed.</span></span> <span data-ttu-id="8d4dc-133">Você precisará adicionar o `bot` objeto ao manifesto do seu aplicativo usando a mesma ID e definindo os escopos apropriados.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-133">You will need to add the `bot` object to your app manifest using the same Id and defining the appropriate scopes.</span></span>

## <a name="add-the-command-to-your-app-manifest"></a><span data-ttu-id="8d4dc-134">Adicione o comando ao manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="8d4dc-134">Add the command to your app manifest</span></span>

<span data-ttu-id="8d4dc-135">Agora que você decidiu como os usuários irão interagir com seu comando Action, é hora de adicioná-lo ao manifesto do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-135">Now that you've decided how users will interact with your action command, it is time to add it to your app manifest.</span></span> <span data-ttu-id="8d4dc-136">Para fazer isso, você adicionará um novo `composeExtension` objeto ao nível superior de seu aplicativo JSON de manifesto.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-136">To do this you'll add a new `composeExtension` object to the top level of your app manifest JSON.</span></span> <span data-ttu-id="8d4dc-137">Você pode fazer isso com a ajuda do App Studio ou manualmente.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-137">You can either do so with the help of App Studio, or manually.</span></span>

### <a name="create-a-command-using-app-studio"></a><span data-ttu-id="8d4dc-138">Criar um comando usando o app Studio</span><span class="sxs-lookup"><span data-stu-id="8d4dc-138">Create a command using App Studio</span></span>

<span data-ttu-id="8d4dc-139">As etapas a seguir supõem que você já tenha [criado uma extensão de mensagens](~/messaging-extensions/how-to/create-messaging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="8d4dc-139">The following steps assume you've already [created a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span></span>

1. <span data-ttu-id="8d4dc-140">No cliente Microsoft Teams, abra o **app Studio** e selecione a guia **Editor de manifesto** .</span><span class="sxs-lookup"><span data-stu-id="8d4dc-140">From the Microsoft Teams client, open **App Studio** and select the **Manifest Editor** tab.</span></span>
2. <span data-ttu-id="8d4dc-141">Se você já criou seu pacote de aplicativos no app Studio, escolha-o na lista.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-141">If you've already created your app package in App Studio, chose it from the list.</span></span> <span data-ttu-id="8d4dc-142">Caso contrário, você pode importar um pacote de aplicativos existente.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-142">If not, you can import an existing app package.</span></span>
3. <span data-ttu-id="8d4dc-143">Clique no botão **Adicionar** na seção comando.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-143">Click the **Add** button in the Command section.</span></span>
4. <span data-ttu-id="8d4dc-144">Escolha **permitir que os usuários disparem ações em serviços externos enquanto estão dentro do teams**.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-144">Choose **Allow users to trigger actions in external services while inside of Teams**.</span></span>
5. <span data-ttu-id="8d4dc-145">Se você deseja usar um conjunto estático de parâmetros para criar seu módulo de tarefa, selecione essa opção.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-145">If you want to use a static set of parameters to create your task module, select that option.</span></span> <span data-ttu-id="8d4dc-146">Caso contrário, opte por **buscar um conjunto dinâmico de parâmetros do bot**.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-146">Otherwise, choose to **Fetch a dynamic set of parameters from your bot**.</span></span>
6. <span data-ttu-id="8d4dc-147">Adicione uma **ID de comando** e um **título**.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-147">Add a **Command Id** and a **Title**.</span></span>
7. <span data-ttu-id="8d4dc-148">Selecione onde você deseja que seu comando de ação seja disparado.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-148">Select where you want your action command to be triggered from.</span></span>
8. <span data-ttu-id="8d4dc-149">Se você estiver usando parâmetros para o módulo de tarefas, adicione o primeiro.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-149">If you're using parameters for your task module, add the first one.</span></span>
9. <span data-ttu-id="8d4dc-150">Click Save</span><span class="sxs-lookup"><span data-stu-id="8d4dc-150">Click Save</span></span>
10. <span data-ttu-id="8d4dc-151">Se você precisar adicionar mais parâmetros, clique no botão **Adicionar** na seção **parâmetros** para adicioná-los.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-151">If you need to add more parameters, click the **Add** button in the **Parameters** section to add them.</span></span>

### <a name="manually-create-a-command"></a><span data-ttu-id="8d4dc-152">Criar um comando manualmente</span><span class="sxs-lookup"><span data-stu-id="8d4dc-152">Manually create a command</span></span>

<span data-ttu-id="8d4dc-153">Para adicionar manualmente o comando de extensão de mensagens baseado em ação ao manifesto do seu aplicativo, você precisará adicionar os parâmetros de acompanhamento à sua `composeExtension.commands` matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-153">To manually add your action-based messaging extension command to your app manifest, you'll need to add the follow parameters to your `composeExtension.commands` array of objects.</span></span>

| <span data-ttu-id="8d4dc-154">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="8d4dc-154">Property name</span></span> | <span data-ttu-id="8d4dc-155">Finalidade</span><span class="sxs-lookup"><span data-stu-id="8d4dc-155">Purpose</span></span> | <span data-ttu-id="8d4dc-156">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="8d4dc-156">Required?</span></span> | <span data-ttu-id="8d4dc-157">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="8d4dc-157">Minimum manifest version</span></span> |
|---|---|---|---|
| `id` | <span data-ttu-id="8d4dc-158">ID exclusiva que você atribui a este comando.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-158">Unique ID that you assign to this command.</span></span> <span data-ttu-id="8d4dc-159">A solicitação do usuário incluirá essa ID.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-159">The user request will include this ID.</span></span> | <span data-ttu-id="8d4dc-160">Sim</span><span class="sxs-lookup"><span data-stu-id="8d4dc-160">Yes</span></span> | <span data-ttu-id="8d4dc-161">1.0</span><span class="sxs-lookup"><span data-stu-id="8d4dc-161">1.0</span></span> |
| `title` | <span data-ttu-id="8d4dc-162">Nome do comando.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-162">Command name.</span></span> <span data-ttu-id="8d4dc-163">Esse valor é exibido na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-163">This value appears in the UI.</span></span> | <span data-ttu-id="8d4dc-164">Sim</span><span class="sxs-lookup"><span data-stu-id="8d4dc-164">Yes</span></span> | <span data-ttu-id="8d4dc-165">1.0</span><span class="sxs-lookup"><span data-stu-id="8d4dc-165">1.0</span></span> |
| `type` | <span data-ttu-id="8d4dc-166">Deve ser `action`</span><span class="sxs-lookup"><span data-stu-id="8d4dc-166">Must be `action`</span></span> | <span data-ttu-id="8d4dc-167">Não</span><span class="sxs-lookup"><span data-stu-id="8d4dc-167">No</span></span> | <span data-ttu-id="8d4dc-168">1.4</span><span class="sxs-lookup"><span data-stu-id="8d4dc-168">1.4</span></span> |
| `fetchTask` | <span data-ttu-id="8d4dc-169">`true` para um cartão adaptável ou modo de exibição da Web incorporado para seu módulo de tarefa, `false` para uma lista estática de parâmetros ou ao carregar o modo de exibição da Web por um `taskInfo`</span><span class="sxs-lookup"><span data-stu-id="8d4dc-169">`true` for an adaptive card or embedded web view for your task module, `false` for a static list of parameters or when loading the web view by a `taskInfo`</span></span> | <span data-ttu-id="8d4dc-170">Não</span><span class="sxs-lookup"><span data-stu-id="8d4dc-170">No</span></span> | <span data-ttu-id="8d4dc-171">1.4</span><span class="sxs-lookup"><span data-stu-id="8d4dc-171">1.4</span></span> |
| `context` | <span data-ttu-id="8d4dc-172">Matriz opcional de valores que define onde a extensão de mensagens pode ser chamada.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-172">Optional array of values that defines where the messaging extension can be invoked from.</span></span> <span data-ttu-id="8d4dc-173">Os valores possíveis são `message` , `compose` , ou `commandBox` .</span><span class="sxs-lookup"><span data-stu-id="8d4dc-173">Possible values are `message`, `compose`, or `commandBox`.</span></span> <span data-ttu-id="8d4dc-174">O padrão é `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-174">Default is `["compose", "commandBox"]`.</span></span> | <span data-ttu-id="8d4dc-175">Não</span><span class="sxs-lookup"><span data-stu-id="8d4dc-175">No</span></span> | <span data-ttu-id="8d4dc-176">1,5</span><span class="sxs-lookup"><span data-stu-id="8d4dc-176">1.5</span></span> |

<span data-ttu-id="8d4dc-177">Se você estiver usando uma lista estática de parâmetros, você também as adicionará.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-177">If you are using a static list of parameters, you'll add them as well.</span></span>

| <span data-ttu-id="8d4dc-178">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="8d4dc-178">Property name</span></span> | <span data-ttu-id="8d4dc-179">Finalidade</span><span class="sxs-lookup"><span data-stu-id="8d4dc-179">Purpose</span></span> | <span data-ttu-id="8d4dc-180">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="8d4dc-180">Required?</span></span> | <span data-ttu-id="8d4dc-181">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="8d4dc-181">Minimum manifest version</span></span> |
|---|---|---|---|
| `parameters` | <span data-ttu-id="8d4dc-182">Lista estática de parâmetros para o comando.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-182">Static list of parameters for the command.</span></span> <span data-ttu-id="8d4dc-183">Usar somente quando `fetchTask` for `false`</span><span class="sxs-lookup"><span data-stu-id="8d4dc-183">Only use when `fetchTask` is `false`</span></span> | <span data-ttu-id="8d4dc-184">Não</span><span class="sxs-lookup"><span data-stu-id="8d4dc-184">No</span></span> | <span data-ttu-id="8d4dc-185">1.0</span><span class="sxs-lookup"><span data-stu-id="8d4dc-185">1.0</span></span> |
| `parameter.name` | <span data-ttu-id="8d4dc-186">O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-186">The name of the parameter.</span></span> <span data-ttu-id="8d4dc-187">Isso é enviado para o serviço na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-187">This is sent to your service in the user request.</span></span> | <span data-ttu-id="8d4dc-188">Sim</span><span class="sxs-lookup"><span data-stu-id="8d4dc-188">Yes</span></span> | <span data-ttu-id="8d4dc-189">1.0</span><span class="sxs-lookup"><span data-stu-id="8d4dc-189">1.0</span></span> |
| `parameter.description` | <span data-ttu-id="8d4dc-190">Descreve os fins deste parâmetro ou o exemplo do valor que deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-190">Describes this parameter’s purposes or example of the value that should be provided.</span></span> <span data-ttu-id="8d4dc-191">Esse valor é exibido na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-191">This value appears in the UI.</span></span> | <span data-ttu-id="8d4dc-192">Sim</span><span class="sxs-lookup"><span data-stu-id="8d4dc-192">Yes</span></span> | <span data-ttu-id="8d4dc-193">1.0</span><span class="sxs-lookup"><span data-stu-id="8d4dc-193">1.0</span></span> |
| `parameter.title` | <span data-ttu-id="8d4dc-194">Título ou rótulo curto de parâmetro amigável.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-194">Short user-friendly parameter title or label.</span></span> | <span data-ttu-id="8d4dc-195">Sim</span><span class="sxs-lookup"><span data-stu-id="8d4dc-195">Yes</span></span> | <span data-ttu-id="8d4dc-196">1.0</span><span class="sxs-lookup"><span data-stu-id="8d4dc-196">1.0</span></span> |
| `parameter.inputType` | <span data-ttu-id="8d4dc-197">Defina como o tipo de entrada obrigatória.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-197">Set to the type of input required.</span></span> <span data-ttu-id="8d4dc-198">Os valores possíveis incluem,,,, `text` `textarea` `number` `date` `time` `toggle` .</span><span class="sxs-lookup"><span data-stu-id="8d4dc-198">Possible values include `text`, `textarea`, `number`, `date`, `time`, `toggle`.</span></span> <span data-ttu-id="8d4dc-199">O padrão é definido como `text`</span><span class="sxs-lookup"><span data-stu-id="8d4dc-199">Default is set to `text`</span></span> | <span data-ttu-id="8d4dc-200">Não</span><span class="sxs-lookup"><span data-stu-id="8d4dc-200">No</span></span> | <span data-ttu-id="8d4dc-201">1.4</span><span class="sxs-lookup"><span data-stu-id="8d4dc-201">1.4</span></span> |

<span data-ttu-id="8d4dc-202">Se você estiver usando um modo de exibição da Web incorporado, você pode opcionalmente adicionar o `taskInfo` objeto para buscar o modo de exibição da Web sem chamar o bot diretamente.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-202">If you are using an embedded web view, you can optionally add the `taskInfo` object to fetch your web view without calling your bot directly.</span></span> <span data-ttu-id="8d4dc-203">Se você optar por usar essa opção, o comportamento será semelhante ao uso de uma lista estática de parâmetros em que a primeira interação com o bot será [responder à ação de envio do módulo de tarefa](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md).</span><span class="sxs-lookup"><span data-stu-id="8d4dc-203">If you choose to use this option, the behavior is similar to using a static list of parameters in that the first interaction with your bot will be [responding to the task module submit action](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md).</span></span> <span data-ttu-id="8d4dc-204">Se você estiver usando um `taskInfo` objeto, certifique-se de também definir o `fetchTask` parâmetro como `false` .</span><span class="sxs-lookup"><span data-stu-id="8d4dc-204">If you are using a `taskInfo` object, be sure to also set the `fetchTask` parameter to `false`.</span></span>

| <span data-ttu-id="8d4dc-205">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="8d4dc-205">Property name</span></span> | <span data-ttu-id="8d4dc-206">Finalidade</span><span class="sxs-lookup"><span data-stu-id="8d4dc-206">Purpose</span></span> | <span data-ttu-id="8d4dc-207">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="8d4dc-207">Required?</span></span> | <span data-ttu-id="8d4dc-208">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="8d4dc-208">Minimum manifest version</span></span> |
|---|---|---|---|
|`taskInfo`|<span data-ttu-id="8d4dc-209">Especificar o módulo de tarefa a ser pré-carregar ao usar um comando de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="8d4dc-209">Specify the task module to preload when using a messaging extension command</span></span>| <span data-ttu-id="8d4dc-210">Não</span><span class="sxs-lookup"><span data-stu-id="8d4dc-210">No</span></span> | <span data-ttu-id="8d4dc-211">1.4</span><span class="sxs-lookup"><span data-stu-id="8d4dc-211">1.4</span></span> |
|`taskInfo.title`|<span data-ttu-id="8d4dc-212">Título do módulo de tarefa inicial</span><span class="sxs-lookup"><span data-stu-id="8d4dc-212">Initial task module title</span></span>|<span data-ttu-id="8d4dc-213">Não</span><span class="sxs-lookup"><span data-stu-id="8d4dc-213">No</span></span> | <span data-ttu-id="8d4dc-214">1.4</span><span class="sxs-lookup"><span data-stu-id="8d4dc-214">1.4</span></span> |
|`taskInfo.width`|<span data-ttu-id="8d4dc-215">Largura do módulo de tarefa: um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '</span><span class="sxs-lookup"><span data-stu-id="8d4dc-215">Task module width - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|<span data-ttu-id="8d4dc-216">Não</span><span class="sxs-lookup"><span data-stu-id="8d4dc-216">No</span></span> | <span data-ttu-id="8d4dc-217">1.4</span><span class="sxs-lookup"><span data-stu-id="8d4dc-217">1.4</span></span> |
|`taskInfo.height`|<span data-ttu-id="8d4dc-218">Altura do módulo de tarefa-um número em pixels ou layout padrão, como ' grande ', ' médio ' ou ' pequeno '</span><span class="sxs-lookup"><span data-stu-id="8d4dc-218">Task module height - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|<span data-ttu-id="8d4dc-219">Não</span><span class="sxs-lookup"><span data-stu-id="8d4dc-219">No</span></span> | <span data-ttu-id="8d4dc-220">1.4</span><span class="sxs-lookup"><span data-stu-id="8d4dc-220">1.4</span></span> |
|`taskInfo.url`|<span data-ttu-id="8d4dc-221">URL de exibição inicial da Web</span><span class="sxs-lookup"><span data-stu-id="8d4dc-221">Initial web view URL</span></span>|<span data-ttu-id="8d4dc-222">Não</span><span class="sxs-lookup"><span data-stu-id="8d4dc-222">No</span></span> | <span data-ttu-id="8d4dc-223">1.4</span><span class="sxs-lookup"><span data-stu-id="8d4dc-223">1.4</span></span> |

#### <a name="app-manifest-example"></a><span data-ttu-id="8d4dc-224">Exemplo de manifesto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="8d4dc-224">App manifest example</span></span>

<span data-ttu-id="8d4dc-225">Veja a seguir um exemplo de um `composeExtensions` objeto que define dois comandos de ação.</span><span class="sxs-lookup"><span data-stu-id="8d4dc-225">The below is an example of a `composeExtensions` object defining two action commands.</span></span> <span data-ttu-id="8d4dc-226">Não é um exemplo de manifesto completo, para o esquema de manifesto de aplicativo completo, consulte: [esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="8d4dc-226">It is not an example of the complete manifest, for the full app manifest schema see: [App manifest schema](~/resources/schema/manifest-schema.md).</span></span>

```json
...
"composeExtensions": [
  {
    "botId": "12a3c29f-1fc5-4d97-a142-12bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "addTodo",
        "description": "Create a To Do item",
        "title": "Create To Do",
        "type": "action",
        "context": ["commandBox", "message", "compose"],
        "fetchTask": false,
        "parameters": [
          {
            "name": "Name",
            "description": "To Do Title",
            "title": "Title",
            "inputType": "text"
          },
          {
            "name": "Description",
            "description": "Description of the task",
            "title": "Description",
            "inputType": "textarea"
          },
          {
            "name": "Date",
            "description": "Due date for the task",
            "title": "Date",
            "inputType": "date"
          }
        ]
      },
      {
        "id": "reassignTodo",
        "description": "Reassign a todo item",
        "title": "Reassign a todo item",
        "type": "action",
        "fetchTask": true,
      }
    ]
  }
]
...
```

## <a name="next-steps"></a><span data-ttu-id="8d4dc-227">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8d4dc-227">Next steps</span></span>

<span data-ttu-id="8d4dc-228">Se você estiver usando um cartão adaptável ou um modo de exibição da Web incorporado sem um `taskInfo` objeto, convém:</span><span class="sxs-lookup"><span data-stu-id="8d4dc-228">If you are using either an adaptive card or an embedded web view without a `taskInfo` object, you'll want to:</span></span>

* [<span data-ttu-id="8d4dc-229">Criar e responder com um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="8d4dc-229">Create and respond with a task module</span></span>](~/messaging-extensions/how-to/action-commands/create-task-module.md)

<span data-ttu-id="8d4dc-230">Se você estiver usando parâmetros ou um modo de exibição da Web incorporado com um `taskInfo` objeto, a próxima etapa para você é:</span><span class="sxs-lookup"><span data-stu-id="8d4dc-230">If you are using parameters or an embedded web view with a `taskInfo` object, the next step for you is to:</span></span>

* [<span data-ttu-id="8d4dc-231">Responder ao envio do módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="8d4dc-231">Respond to task module submit</span></span>](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
