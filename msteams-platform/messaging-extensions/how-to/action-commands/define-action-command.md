---
title: Definir comandos de ação de extensão de mensagens
author: clearab
description: Uma visão geral dos comandos de ação de extensão de mensagens
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f49e821ecb98659b4cfd68f93b37f1a8f611a9fb
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020713"
---
# <a name="define-messaging-extension-action-commands"></a><span data-ttu-id="ba886-103">Definir comandos de ação de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="ba886-103">Define messaging extension action commands</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="ba886-104">Os comandos de ação permitem que você apresente aos usuários um pop-up modal chamado módulo de tarefa Teams.</span><span class="sxs-lookup"><span data-stu-id="ba886-104">Action commands allow you to present your users with a modal popup called a task module in Teams.</span></span> <span data-ttu-id="ba886-105">O módulo de tarefa coleta ou exibe informações, processa a interação e envia as informações de volta para Teams.</span><span class="sxs-lookup"><span data-stu-id="ba886-105">The task module collects or displays information, processes the interaction and sends the information back to Teams.</span></span> <span data-ttu-id="ba886-106">Este documento orienta você sobre como selecionar locais de invocação de comando de ação, criar seu módulo de tarefa, enviar mensagem final ou cartão, criar comando de ação usando o app studio ou crie-o manualmente.</span><span class="sxs-lookup"><span data-stu-id="ba886-106">This document guides you on how to select action command invoke locations, create your task module, send final message, or card, create action command using app studio, or create it manually.</span></span> 

<span data-ttu-id="ba886-107">Antes de criar o comando de ação, você deve decidir os seguintes fatores:</span><span class="sxs-lookup"><span data-stu-id="ba886-107">Before creating the action command you must decide the following factors:</span></span>

1. [<span data-ttu-id="ba886-108">De onde o comando de ação pode ser disparado?</span><span class="sxs-lookup"><span data-stu-id="ba886-108">Where can the action command be triggered from?</span></span>](#select-action-command-invoke-locations)
1. [<span data-ttu-id="ba886-109">Como o módulo de tarefa será criado?</span><span class="sxs-lookup"><span data-stu-id="ba886-109">How will the task module be created?</span></span>](#select-how-to-create-your-task-module)
1. [<span data-ttu-id="ba886-110">A mensagem final ou o cartão será enviado para o canal de um bot ou a mensagem ou o cartão será inserido na área de mensagem de redação para o usuário enviar?</span><span class="sxs-lookup"><span data-stu-id="ba886-110">Will the final message or card be sent to the channel from a bot, or will the message or card be inserted into the compose message area for the user to submit?</span></span>](#select-how-the-final-message-is-sent)

## <a name="select-action-command-invoke-locations"></a><span data-ttu-id="ba886-111">Selecionar locais de invocação de comando de ação</span><span class="sxs-lookup"><span data-stu-id="ba886-111">Select action command invoke locations</span></span>

<span data-ttu-id="ba886-112">Primeiro, você deve decidir o local de onde seu comando de ação deve ser invocado.</span><span class="sxs-lookup"><span data-stu-id="ba886-112">First, you must decide the location from where your action command must be invoked.</span></span> <span data-ttu-id="ba886-113">Especificando o `context` no manifesto do aplicativo, seu comando pode ser invocado de um ou mais dos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="ba886-113">By specifying the `context` in your app manifest, your command can be invoked from one or more of the following locations:</span></span>

* <span data-ttu-id="ba886-114">Área de mensagem de redação: os botões na parte inferior da área de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="ba886-114">Compose message area: The buttons at the bottom of the compose message area.</span></span>
* <span data-ttu-id="ba886-115">Caixa de comando: @mentioning seu aplicativo na caixa de comando.</span><span class="sxs-lookup"><span data-stu-id="ba886-115">Command box: By @mentioning your app in the command box.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="ba886-116">Se a extensão de mensagens for invocada da caixa de comando, você não poderá responder com uma mensagem bot inserida diretamente na conversa.</span><span class="sxs-lookup"><span data-stu-id="ba886-116">If messaging extension is invoked from the command box, you cannot respond with a bot message inserted directly into the conversation.</span></span>

* <span data-ttu-id="ba886-117">Mensagem: diretamente de uma mensagem existente por meio do `...` menu de estouro em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="ba886-117">Message: Directly from an existing message through the `...` overflow menu on a message.</span></span> 
    > [!NOTE] 
    > <span data-ttu-id="ba886-118">A invocação inicial ao bot inclui um objeto JSON que contém a mensagem da qual foi invocada.</span><span class="sxs-lookup"><span data-stu-id="ba886-118">The initial invoke to your bot includes a JSON object containing the message from which it was invoked.</span></span> <span data-ttu-id="ba886-119">Você pode processar a mensagem antes de apresentá-la com um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="ba886-119">You can process the message before presenting them with a task module.</span></span>

<span data-ttu-id="ba886-120">A imagem a seguir exibe os locais de onde o comando de ação é invocado:</span><span class="sxs-lookup"><span data-stu-id="ba886-120">The following image displays the locations from where action command is invoked:</span></span>

![locais de invocação de comando de ação](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="select-how-to-create-your-task-module"></a><span data-ttu-id="ba886-122">Selecione como criar seu módulo de tarefas</span><span class="sxs-lookup"><span data-stu-id="ba886-122">Select how to create your task module</span></span>

<span data-ttu-id="ba886-123">Além de selecionar de onde o comando pode ser invocado, você também deve selecionar como preencher o formulário no módulo de tarefas para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="ba886-123">In addition to selecting where your command can be invoked from, you must also select how to populate the form in the task module for your users.</span></span> <span data-ttu-id="ba886-124">Você tem as três opções a seguir para criar o formulário renderizado dentro do módulo de tarefa:</span><span class="sxs-lookup"><span data-stu-id="ba886-124">You have the following three options for creating the form that is rendered inside the task module:</span></span>   

* <span data-ttu-id="ba886-125">**Lista estática de parâmetros**: este é o método mais simples.</span><span class="sxs-lookup"><span data-stu-id="ba886-125">**Static list of parameters**: This is the simplest method.</span></span> <span data-ttu-id="ba886-126">Você pode definir uma lista de parâmetros no manifesto do aplicativo que o cliente Teams renderiza, mas não pode controlar a formatação nesse caso.</span><span class="sxs-lookup"><span data-stu-id="ba886-126">You can define a list of parameters in your app manifest the Teams client renders, but cannot control the formatting in this case.</span></span>
* <span data-ttu-id="ba886-127">**Cartão Adaptável**: você pode selecionar para usar um Cartão Adaptável, que fornece maior controle sobre a interface do usuário, mas ainda o limita nos controles disponíveis e opções de formatação.</span><span class="sxs-lookup"><span data-stu-id="ba886-127">**Adaptive Card**:  You can select to use an Adaptive Card, which provides greater control over the UI, but still limits you on the available controls and formatting options.</span></span>
* <span data-ttu-id="ba886-128">**Exibição da Web** incorporada : Você pode selecionar para inserir um exibição da Web personalizado no módulo de tarefas para ter um controle completo sobre a interface do usuário e os controles.</span><span class="sxs-lookup"><span data-stu-id="ba886-128">**Embedded web view**: You can select to embed a custom web view in the task module to have a complete control over the UI and controls.</span></span> 

<span data-ttu-id="ba886-129">Se você selecionar para criar o módulo de tarefa com uma lista estática de parâmetros e quando o usuário enviar o módulo de tarefa, a extensão de mensagens será chamada.</span><span class="sxs-lookup"><span data-stu-id="ba886-129">If you select to create the task module with a static list of parameters and when the user submits the task module, the messaging extension is called.</span></span> <span data-ttu-id="ba886-130">Ao usar uma exibição da Web incorporada ou um Cartão Adaptável, sua extensão de mensagens deve manipular um evento de invocação inicial do usuário, criar o módulo de tarefa e devolvê-lo ao cliente.</span><span class="sxs-lookup"><span data-stu-id="ba886-130">When using an embedded web view or an Adaptive Card, your messaging extension must handle an initial invoke event from the user, create the task module, and return it back to the client.</span></span>

## <a name="select-how-the-final-message-is-sent"></a><span data-ttu-id="ba886-131">Selecione como a mensagem final é enviada</span><span class="sxs-lookup"><span data-stu-id="ba886-131">Select how the final message is sent</span></span>

<span data-ttu-id="ba886-132">Na maioria dos casos, o comando de ação resulta em um cartão inserido na caixa de mensagem de redação.</span><span class="sxs-lookup"><span data-stu-id="ba886-132">In most cases, the action command results in a card inserted into the compose message box.</span></span> <span data-ttu-id="ba886-133">O usuário pode enviá-lo para o canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="ba886-133">The user can send it into the channel or chat.</span></span> <span data-ttu-id="ba886-134">Nesse caso, a mensagem vem do usuário, e o bot não pode editar ou atualizar o cartão ainda mais.</span><span class="sxs-lookup"><span data-stu-id="ba886-134">In this case, the message comes from the user, and the bot cannot edit or update the card further.</span></span>

<span data-ttu-id="ba886-135">Se a extensão de mensagens for invocada da caixa de redação ou diretamente de uma mensagem, seu serviço Web poderá inserir a resposta final diretamente no canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="ba886-135">If the messaging extension is invoked from the compose box or directly from a message, your web service can insert the final response directly into the channel or chat.</span></span> <span data-ttu-id="ba886-136">Nesse caso, o Cartão Adaptável vem do bot, o bot o atualiza e responde ao thread de conversa, se necessário.</span><span class="sxs-lookup"><span data-stu-id="ba886-136">In this case, the Adaptive Card comes from the bot, the bot updates it, and replies to the conversation thread if needed.</span></span> <span data-ttu-id="ba886-137">Você deve adicionar o `bot` objeto ao manifesto do aplicativo usando a mesma ID e definindo os escopos apropriados.</span><span class="sxs-lookup"><span data-stu-id="ba886-137">You must add the `bot` object to the app manifest using  the same ID and defining the appropriate scopes.</span></span>

## <a name="add-the-action-command-to-your-app-manifest"></a><span data-ttu-id="ba886-138">Adicionar o comando de ação ao manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ba886-138">Add the action command to your app manifest</span></span>

<span data-ttu-id="ba886-139">Para adicionar o comando de ação ao manifesto do aplicativo, você deve adicionar um novo objeto ao nível superior do manifesto `composeExtension` do aplicativo JSON.</span><span class="sxs-lookup"><span data-stu-id="ba886-139">To add the action command to the app manifest, you must add a new `composeExtension` object to the top level of the app manifest JSON.</span></span> <span data-ttu-id="ba886-140">Você pode usar uma das seguintes maneiras de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="ba886-140">You can use one of the following ways to do so:</span></span>

* [<span data-ttu-id="ba886-141">Criar um comando de ação usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="ba886-141">Create an action command using App Studio</span></span>](#create-an-action-command-using-app-studio)
* [<span data-ttu-id="ba886-142">Criar um comando de ação manualmente</span><span class="sxs-lookup"><span data-stu-id="ba886-142">Create an action command manually</span></span>](#create-an-action-command-manually)

### <a name="create-an-action-command-using-app-studio"></a><span data-ttu-id="ba886-143">Criar um comando de ação usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="ba886-143">Create an action command using App Studio</span></span>

> [!NOTE]
> <span data-ttu-id="ba886-144">O pré-requisito para criar um comando de ação é que você já criou uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ba886-144">The prerequisite to create an action command is that you have already created a messaging extension.</span></span> <span data-ttu-id="ba886-145">Para obter informações sobre como criar uma extensão de mensagens, consulte [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="ba886-145">For information on how to create a messaging extension, see [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span></span>

<span data-ttu-id="ba886-146">**Para criar um comando de ação**</span><span class="sxs-lookup"><span data-stu-id="ba886-146">**To create an action command**</span></span>

1. <span data-ttu-id="ba886-147">Abra **o App Studio** no cliente Microsoft Teams e selecione a guia Editor **de** manifesto.</span><span class="sxs-lookup"><span data-stu-id="ba886-147">Open **App Studio** from the Microsoft Teams client and select the **Manifest editor** tab.</span></span>
1. <span data-ttu-id="ba886-148">Se você já criou seu pacote de aplicativos **no App Studio,** selecione-o na lista.</span><span class="sxs-lookup"><span data-stu-id="ba886-148">If you already created your app package in **App Studio**, select it from the list.</span></span> <span data-ttu-id="ba886-149">Se você não tiver criado um pacote de aplicativos, importe um existente.</span><span class="sxs-lookup"><span data-stu-id="ba886-149">If you have not created an app package, import an existing one.</span></span>
1. <span data-ttu-id="ba886-150">Depois de importar um pacote de aplicativos, selecione **Extensões de mensagens** em **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="ba886-150">After importing an app package, select **Messaging extensions** under **Capabilities**.</span></span> <span data-ttu-id="ba886-151">Você tem uma janela pop-up para configurar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ba886-151">You get a pop-up window to set up the messaging extension.</span></span>
1. <span data-ttu-id="ba886-152">Selecione **Configurar na** janela para incluir a extensão de mensagens na experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ba886-152">Select **Set up** in the window to include the messaging extension in your app experience.</span></span> <span data-ttu-id="ba886-153">A imagem a seguir exibe a janela de configuração da extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="ba886-153">The following image displays the messaging extension set up window:</span></span>

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>
    
1. <span data-ttu-id="ba886-154">Para criar uma extensão de mensagens, você precisa de um bot registrado da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ba886-154">To create a messaging extension, you need a Microsoft registered bot.</span></span> <span data-ttu-id="ba886-155">Você pode usar um bot existente ou criar um novo bot.</span><span class="sxs-lookup"><span data-stu-id="ba886-155">You can either use an existing bot or create a new bot.</span></span> <span data-ttu-id="ba886-156">Selecione **Criar nova opção bot,** dê um nome para o novo bot e selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="ba886-156">Select **Create new bot** option, give a name for the new bot, and select **Create**.</span></span> <span data-ttu-id="ba886-157">A imagem a seguir exibe a criação de bots para extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="ba886-157">The following image displays bot creation for messaging extension:</span></span>

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. <span data-ttu-id="ba886-158">Selecione **Adicionar** na seção **Comando da** página extensões de mensagens para incluir os comandos que decidem o comportamento da extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ba886-158">Select **Add** in the **Command section** of the messaging extensions page to include the commands which decides the behaviour of messaging extension.</span></span>   
<span data-ttu-id="ba886-159">A imagem a seguir exibe a adição de comando para extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="ba886-159">The following image displays command addition for messaging extension:</span></span>

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>

1. <span data-ttu-id="ba886-160">Selecione **Permitir que os usuários acionem ações em serviços externos enquanto estão Teams**.</span><span class="sxs-lookup"><span data-stu-id="ba886-160">Select **Allow users to trigger actions in external services while inside of Teams**.</span></span> <span data-ttu-id="ba886-161">A imagem a seguir exibe a seleção de comando de ação:</span><span class="sxs-lookup"><span data-stu-id="ba886-161">The following image displays the action command selection:</span></span>

    <img src="~/assets/images/messaging-extension/action-command-selection.png" alt="action command selection" width="500"/>
    
1. <span data-ttu-id="ba886-162">Para usar um conjunto estático de parâmetros para criar seu módulo de tarefa, selecione Definir um conjunto de **parâmetros estáticos para o comando**.</span><span class="sxs-lookup"><span data-stu-id="ba886-162">To use a static set of parameters to create your task module, select **Define a set of static parameters for the command**.</span></span> 

    <span data-ttu-id="ba886-163">A imagem a seguir exibe a seleção de parâmetro estático do comando de ação:</span><span class="sxs-lookup"><span data-stu-id="ba886-163">The following image displays the action command static parameter selection:</span></span>

   <img src="~/assets/images/messaging-extension/action-command-static-parameter-selection.png" alt="action command static parameter selection" width="500"/> 
   
    <span data-ttu-id="ba886-164">A imagem a seguir exibe um exemplo de configuração de parâmetro estático:</span><span class="sxs-lookup"><span data-stu-id="ba886-164">The following image displays an example static parameter set-up:</span></span> 

   <img src="~/assets/images/messaging-extension/setting-up-of-static-parameter.png" alt="action command static parameter set-up" width="500"/>

    <span data-ttu-id="ba886-165">A imagem a seguir exibe um exemplo de teste de parâmetro estático:</span><span class="sxs-lookup"><span data-stu-id="ba886-165">The following image displays an example static parameter testing:</span></span>

   <img src="~/assets/images/messaging-extension/static-parameter-testing.png" alt="action command static parameter testing" width="500"/>

1. <span data-ttu-id="ba886-166">Para usar parâmetros dinâmicos, selecione **Para Buscar um conjunto dinâmico de parâmetros do bot**.</span><span class="sxs-lookup"><span data-stu-id="ba886-166">To use dynamic parameters, select to **Fetch a dynamic set of parameters from your bot**.</span></span> <span data-ttu-id="ba886-167">A imagem a seguir exibe a seleção do parâmetro de comando de ação:</span><span class="sxs-lookup"><span data-stu-id="ba886-167">The following image displays the action command parameter selection:</span></span>

    <img src="~/assets/images/messaging-extension/action-command-dynamic-parameter-selection.png" alt="action command dynamic parameter selection" width="500"/>
    
1. <span data-ttu-id="ba886-168">Adicione uma **ID de Comando** e um **Título.**</span><span class="sxs-lookup"><span data-stu-id="ba886-168">Add a **Command Id** and a **Title**.</span></span>
1. <span data-ttu-id="ba886-169">Selecione o local de onde você deseja invocar o comando de ação.</span><span class="sxs-lookup"><span data-stu-id="ba886-169">Select the location from where you want to invoke the action command.</span></span> <span data-ttu-id="ba886-170">A imagem a seguir exibe o local de invocação do comando de ação:</span><span class="sxs-lookup"><span data-stu-id="ba886-170">The following image displays the action command invoke location:</span></span>

    <img src="~/assets/images/messaging-extension/action-command-invoke-location.png" alt="action command invoke location" width="500"/>

1. <span data-ttu-id="ba886-171">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="ba886-171">Select **Save**.</span></span>
1. <span data-ttu-id="ba886-172">Para adicionar mais parâmetros, selecione o **botão Adicionar** na **seção Parâmetros.**</span><span class="sxs-lookup"><span data-stu-id="ba886-172">To add more parameters, select the **Add** button in the **Parameters** section.</span></span>

### <a name="create-an-action-command-manually"></a><span data-ttu-id="ba886-173">Criar um comando de ação manualmente</span><span class="sxs-lookup"><span data-stu-id="ba886-173">Create an action command manually</span></span>

<span data-ttu-id="ba886-174">Para adicionar manualmente o comando de extensão de mensagens baseada em ação ao manifesto do aplicativo, adicione os seguintes parâmetros à `composeExtension.commands` matriz de objetos:</span><span class="sxs-lookup"><span data-stu-id="ba886-174">To manually add your action-based messaging extension command to your app manifest, you must add the following parameters to the `composeExtension.commands` array of objects:</span></span>

| <span data-ttu-id="ba886-175">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="ba886-175">Property name</span></span> | <span data-ttu-id="ba886-176">Finalidade</span><span class="sxs-lookup"><span data-stu-id="ba886-176">Purpose</span></span> | <span data-ttu-id="ba886-177">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="ba886-177">Required?</span></span> | <span data-ttu-id="ba886-178">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="ba886-178">Minimum manifest version</span></span> |
|---|---|---|---|
| `id` | <span data-ttu-id="ba886-179">Essa propriedade é uma ID exclusiva que você atribui a este comando.</span><span class="sxs-lookup"><span data-stu-id="ba886-179">This property is an unique ID that you assign to this command.</span></span> <span data-ttu-id="ba886-180">A solicitação do usuário inclui essa ID.</span><span class="sxs-lookup"><span data-stu-id="ba886-180">The user request includes this ID.</span></span> | <span data-ttu-id="ba886-181">Sim</span><span class="sxs-lookup"><span data-stu-id="ba886-181">Yes</span></span> | <span data-ttu-id="ba886-182">1.0</span><span class="sxs-lookup"><span data-stu-id="ba886-182">1.0</span></span> |
| `title` | <span data-ttu-id="ba886-183">Essa propriedade é um nome de comando.</span><span class="sxs-lookup"><span data-stu-id="ba886-183">This property is a command name.</span></span> <span data-ttu-id="ba886-184">Esse valor aparece na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="ba886-184">This value appears in the UI.</span></span> | <span data-ttu-id="ba886-185">Sim</span><span class="sxs-lookup"><span data-stu-id="ba886-185">Yes</span></span> | <span data-ttu-id="ba886-186">1.0</span><span class="sxs-lookup"><span data-stu-id="ba886-186">1.0</span></span> |
| `type` | <span data-ttu-id="ba886-187">Essa propriedade deve ser `action` um .</span><span class="sxs-lookup"><span data-stu-id="ba886-187">This property must be an `action`.</span></span> | <span data-ttu-id="ba886-188">Não</span><span class="sxs-lookup"><span data-stu-id="ba886-188">No</span></span> | <span data-ttu-id="ba886-189">1.4</span><span class="sxs-lookup"><span data-stu-id="ba886-189">1.4</span></span> |
| `fetchTask` | <span data-ttu-id="ba886-190">Essa propriedade é definida como para um cartão adaptável ou exibição da Web incorporada para o módulo de tarefas e para uma lista estática de parâmetros ou ao carregar o visualização `true` da Web por um `false` `taskInfo` .</span><span class="sxs-lookup"><span data-stu-id="ba886-190">This property is set to `true` for an adaptive card or embedded web view for your task module, and`false` for a static list of parameters or when loading the web view by a `taskInfo`.</span></span> | <span data-ttu-id="ba886-191">Não</span><span class="sxs-lookup"><span data-stu-id="ba886-191">No</span></span> | <span data-ttu-id="ba886-192">1.4</span><span class="sxs-lookup"><span data-stu-id="ba886-192">1.4</span></span> |
| `context` | <span data-ttu-id="ba886-193">Essa propriedade é uma matriz opcional de valores que define de onde a extensão de mensagens é invocada.</span><span class="sxs-lookup"><span data-stu-id="ba886-193">This property is an optional array of values that defines where the messaging extension is invoked from.</span></span> <span data-ttu-id="ba886-194">Os valores possíveis são `message`, `compose` ou `commandBox`.</span><span class="sxs-lookup"><span data-stu-id="ba886-194">The possible values are `message`, `compose`, or `commandBox`.</span></span> <span data-ttu-id="ba886-195">O valor padrão é `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="ba886-195">The default value is `["compose", "commandBox"]`.</span></span> | <span data-ttu-id="ba886-196">Não</span><span class="sxs-lookup"><span data-stu-id="ba886-196">No</span></span> | <span data-ttu-id="ba886-197">1,5</span><span class="sxs-lookup"><span data-stu-id="ba886-197">1.5</span></span> |

<span data-ttu-id="ba886-198">Se você estiver usando uma lista estática de parâmetros, também deverá adicionar os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="ba886-198">If you are using a static list of parameters, you must also add the following parameters:</span></span>

| <span data-ttu-id="ba886-199">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="ba886-199">Property name</span></span> | <span data-ttu-id="ba886-200">Finalidade</span><span class="sxs-lookup"><span data-stu-id="ba886-200">Purpose</span></span> | <span data-ttu-id="ba886-201">É necessário?</span><span class="sxs-lookup"><span data-stu-id="ba886-201">Is required?</span></span> | <span data-ttu-id="ba886-202">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="ba886-202">Minimum manifest version</span></span> |
|---|---|---|---|
| `parameters` | <span data-ttu-id="ba886-203">Essa propriedade descreve a lista estática de parâmetros do comando.</span><span class="sxs-lookup"><span data-stu-id="ba886-203">This property describes the static list of parameters for the command.</span></span> <span data-ttu-id="ba886-204">Use somente quando `fetchTask` for `false` .</span><span class="sxs-lookup"><span data-stu-id="ba886-204">Only use when `fetchTask` is `false`.</span></span> | <span data-ttu-id="ba886-205">Não</span><span class="sxs-lookup"><span data-stu-id="ba886-205">No</span></span> | <span data-ttu-id="ba886-206">1.0</span><span class="sxs-lookup"><span data-stu-id="ba886-206">1.0</span></span> |
| `parameter.name` | <span data-ttu-id="ba886-207">Essa propriedade descreve o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ba886-207">This property describes the name of the parameter.</span></span> <span data-ttu-id="ba886-208">Isso é enviado ao seu serviço na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="ba886-208">This is sent to your service in the user request.</span></span> | <span data-ttu-id="ba886-209">Sim</span><span class="sxs-lookup"><span data-stu-id="ba886-209">Yes</span></span> | <span data-ttu-id="ba886-210">1.0</span><span class="sxs-lookup"><span data-stu-id="ba886-210">1.0</span></span> |
| `parameter.description` | <span data-ttu-id="ba886-211">Esta propriedade descreve as finalidades do parâmetro ou o exemplo do valor que deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="ba886-211">This property describes the parameter’s purposes or example of the value that should be provided.</span></span> <span data-ttu-id="ba886-212">Esse valor aparece na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="ba886-212">This value appears in the UI.</span></span> | <span data-ttu-id="ba886-213">Sim</span><span class="sxs-lookup"><span data-stu-id="ba886-213">Yes</span></span> | <span data-ttu-id="ba886-214">1.0</span><span class="sxs-lookup"><span data-stu-id="ba886-214">1.0</span></span> |
| `parameter.title` | <span data-ttu-id="ba886-215">Essa propriedade é um título ou rótulo de parâmetro fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="ba886-215">This property is a short user-friendly parameter title or label.</span></span> | <span data-ttu-id="ba886-216">Sim</span><span class="sxs-lookup"><span data-stu-id="ba886-216">Yes</span></span> | <span data-ttu-id="ba886-217">1.0</span><span class="sxs-lookup"><span data-stu-id="ba886-217">1.0</span></span> |
| `parameter.inputType` | <span data-ttu-id="ba886-218">Essa propriedade é definida como o tipo de entrada necessária.</span><span class="sxs-lookup"><span data-stu-id="ba886-218">This property is set to the type of input required.</span></span> <span data-ttu-id="ba886-219">Os valores possíveis `text` `textarea` incluem , `number` , , , , `date` `time` `toggle` .</span><span class="sxs-lookup"><span data-stu-id="ba886-219">The possible values include `text`, `textarea`, `number`, `date`, `time`, `toggle`.</span></span> <span data-ttu-id="ba886-220">O valor padrão é definido como `text` .</span><span class="sxs-lookup"><span data-stu-id="ba886-220">The default value is set to `text`.</span></span> | <span data-ttu-id="ba886-221">Não</span><span class="sxs-lookup"><span data-stu-id="ba886-221">No</span></span> | <span data-ttu-id="ba886-222">1.4</span><span class="sxs-lookup"><span data-stu-id="ba886-222">1.4</span></span> |

<span data-ttu-id="ba886-223">Se você estiver usando uma exibição da Web incorporada, você pode, opcionalmente, adicionar o objeto para buscar sua `taskInfo` exibição da Web sem chamar seu bot diretamente.</span><span class="sxs-lookup"><span data-stu-id="ba886-223">If you are using an embedded web view, you can optionally add the `taskInfo` object to fetch your web view without calling your bot directly.</span></span> <span data-ttu-id="ba886-224">Se você selecionar essa opção, o comportamento será semelhante ao de usar uma lista estática de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ba886-224">If you select this option, the behavior is similar to that of using a static list of parameters.</span></span> <span data-ttu-id="ba886-225">Na medida em que a primeira interação com seu bot está [respondendo à ação](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)de envio do módulo de tarefas .</span><span class="sxs-lookup"><span data-stu-id="ba886-225">In that the first interaction with your bot is [responding to the task module submit action](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md).</span></span> <span data-ttu-id="ba886-226">Se você estiver usando um `taskInfo` objeto, deverá definir o `fetchTask` parâmetro como `false` .</span><span class="sxs-lookup"><span data-stu-id="ba886-226">If you are using a `taskInfo` object, you must set the `fetchTask` parameter to `false`.</span></span>

| <span data-ttu-id="ba886-227">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="ba886-227">Property name</span></span> | <span data-ttu-id="ba886-228">Finalidade</span><span class="sxs-lookup"><span data-stu-id="ba886-228">Purpose</span></span> | <span data-ttu-id="ba886-229">É necessário?</span><span class="sxs-lookup"><span data-stu-id="ba886-229">Is required?</span></span> | <span data-ttu-id="ba886-230">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="ba886-230">Minimum manifest version</span></span> |
|---|---|---|---|
|`taskInfo`|<span data-ttu-id="ba886-231">Especifique o módulo de tarefa a ser pré-carregado ao usar um comando de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ba886-231">Specify the task module to preload when using a messaging extension command.</span></span> | <span data-ttu-id="ba886-232">Não</span><span class="sxs-lookup"><span data-stu-id="ba886-232">No</span></span> | <span data-ttu-id="ba886-233">1.4</span><span class="sxs-lookup"><span data-stu-id="ba886-233">1.4</span></span> |
|`taskInfo.title`|<span data-ttu-id="ba886-234">Título inicial do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="ba886-234">Initial task module title.</span></span> |<span data-ttu-id="ba886-235">Não</span><span class="sxs-lookup"><span data-stu-id="ba886-235">No</span></span> | <span data-ttu-id="ba886-236">1.4</span><span class="sxs-lookup"><span data-stu-id="ba886-236">1.4</span></span> |
|`taskInfo.width`|<span data-ttu-id="ba886-237">Largura do módulo de tarefa, um número em pixels ou layout `large` padrão, como , `medium` ou `small` .</span><span class="sxs-lookup"><span data-stu-id="ba886-237">Task module width, either a number in pixels or default layout such as `large`, `medium`, or `small`.</span></span> |<span data-ttu-id="ba886-238">Não</span><span class="sxs-lookup"><span data-stu-id="ba886-238">No</span></span> | <span data-ttu-id="ba886-239">1.4</span><span class="sxs-lookup"><span data-stu-id="ba886-239">1.4</span></span> |
|`taskInfo.height`|<span data-ttu-id="ba886-240">Altura do módulo de tarefa, um número em pixels ou layout `large` padrão, como , `medium` ou `small` .</span><span class="sxs-lookup"><span data-stu-id="ba886-240">Task module height, either a number in pixels or default layout such as `large`, `medium`, or `small`.</span></span>|<span data-ttu-id="ba886-241">Não</span><span class="sxs-lookup"><span data-stu-id="ba886-241">No</span></span> | <span data-ttu-id="ba886-242">1.4</span><span class="sxs-lookup"><span data-stu-id="ba886-242">1.4</span></span> |
|`taskInfo.url`|<span data-ttu-id="ba886-243">URL de exibição da Web inicial.</span><span class="sxs-lookup"><span data-stu-id="ba886-243">Initial web view URL.</span></span>|<span data-ttu-id="ba886-244">Não</span><span class="sxs-lookup"><span data-stu-id="ba886-244">No</span></span> | <span data-ttu-id="ba886-245">1.4</span><span class="sxs-lookup"><span data-stu-id="ba886-245">1.4</span></span> | 

#### <a name="app-manifest-example"></a><span data-ttu-id="ba886-246">Exemplo de manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ba886-246">App manifest example</span></span>

<span data-ttu-id="ba886-247">A seção a seguir é um exemplo de um `composeExtensions` objeto que define dois comandos de ação.</span><span class="sxs-lookup"><span data-stu-id="ba886-247">The following section is an example of a `composeExtensions` object defining two action commands.</span></span> <span data-ttu-id="ba886-248">Não é um exemplo do manifesto completo.</span><span class="sxs-lookup"><span data-stu-id="ba886-248">It is not an example of the complete manifest.</span></span> <span data-ttu-id="ba886-249">Para o esquema de manifesto completo do aplicativo, consulte [esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md):</span><span class="sxs-lookup"><span data-stu-id="ba886-249">For the complete app manifest schema, see [app manifest schema](~/resources/schema/manifest-schema.md):</span></span>

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
        "fetchTask": true,
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

## <a name="code-sample"></a><span data-ttu-id="ba886-250">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="ba886-250">Code sample</span></span>

| <span data-ttu-id="ba886-251">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="ba886-251">Sample Name</span></span>           | <span data-ttu-id="ba886-252">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba886-252">Description</span></span> | <span data-ttu-id="ba886-253">.NET</span><span class="sxs-lookup"><span data-stu-id="ba886-253">.NET</span></span>    | <span data-ttu-id="ba886-254">Node.js</span><span class="sxs-lookup"><span data-stu-id="ba886-254">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="ba886-255">Teams ação de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="ba886-255">Teams messaging extension action</span></span>| <span data-ttu-id="ba886-256">Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="ba886-256">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="ba886-257">View</span><span class="sxs-lookup"><span data-stu-id="ba886-257">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="ba886-258">View</span><span class="sxs-lookup"><span data-stu-id="ba886-258">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="ba886-259">Teams de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="ba886-259">Teams messaging extension search</span></span>   |  <span data-ttu-id="ba886-260">Descreve como definir comandos de pesquisa e responder a pesquisas.</span><span class="sxs-lookup"><span data-stu-id="ba886-260">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="ba886-261">View</span><span class="sxs-lookup"><span data-stu-id="ba886-261">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="ba886-262">View</span><span class="sxs-lookup"><span data-stu-id="ba886-262">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a><span data-ttu-id="ba886-263">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ba886-263">Next step</span></span>

<span data-ttu-id="ba886-264">Se você estiver usando um Cartão Adaptável ou uma exibição da Web incorporada sem um objeto, a `taskInfo` próxima etapa será:</span><span class="sxs-lookup"><span data-stu-id="ba886-264">If you are using either an Adaptive Card or an embedded web view without a `taskInfo` object, the next step is to:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ba886-265">Criar e responder com um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="ba886-265">Create and respond with a task module</span></span>](~/messaging-extensions/how-to/action-commands/create-task-module.md)

<span data-ttu-id="ba886-266">Se você estiver usando os parâmetros ou uma exibição da Web incorporada com um objeto, a `taskInfo` próxima etapa será:</span><span class="sxs-lookup"><span data-stu-id="ba886-266">If you are using the parameters or an embedded web view with a `taskInfo` object, the next step is to:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ba886-267">Responder ao envio do módulo de tarefas</span><span class="sxs-lookup"><span data-stu-id="ba886-267">Respond to task module submit</span></span>](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

