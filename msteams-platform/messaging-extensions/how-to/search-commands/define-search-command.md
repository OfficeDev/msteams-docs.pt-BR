---
title: Definir comandos de pesquisa de extensão de mensagens
author: surbhigupta
description: Defina comandos de pesquisa de extensão de mensagens para Microsoft Teams aplicativos.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 6333840e6817761911b2b5acd4b53849448b5b68
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068913"
---
# <a name="define-messaging-extension-search-commands"></a><span data-ttu-id="b254b-103">Definir comandos de pesquisa de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="b254b-103">Define messaging extension search commands</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="b254b-104">Comandos de pesquisa de extensão de mensagens permitem que os usuários pesquisem sistemas externos e insiram os resultados dessa pesquisa em uma mensagem na forma de um cartão.</span><span class="sxs-lookup"><span data-stu-id="b254b-104">Messaging extension search commands allow users to search external systems and insert the results of that search into a message in the form of a card.</span></span> <span data-ttu-id="b254b-105">Este documento orienta você sobre como selecionar locais de invocação de comando de pesquisa e adicionar o comando de pesquisa ao manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b254b-105">This document guides you on how to select  search command invoke locations, and add the search command to your app manifest.</span></span>

> [!NOTE]
> <span data-ttu-id="b254b-106">O limite de tamanho do cartão de resultado é de 28 KB.</span><span class="sxs-lookup"><span data-stu-id="b254b-106">The result card size limit is 28 KB.</span></span> <span data-ttu-id="b254b-107">O cartão não será enviado se seu tamanho exceder 28 KB.</span><span class="sxs-lookup"><span data-stu-id="b254b-107">The card is not sent if its size exceeds 28 KB.</span></span>

## <a name="select-search-command-invoke-locations"></a><span data-ttu-id="b254b-108">Selecionar locais de invocação de comando de pesquisa</span><span class="sxs-lookup"><span data-stu-id="b254b-108">Select search command invoke locations</span></span>

<span data-ttu-id="b254b-109">O comando de pesquisa é invocado de qualquer um ou ambos os seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="b254b-109">The search command is invoked from any one or both of the following locations:</span></span>

* <span data-ttu-id="b254b-110">Área de mensagem de redação: os botões na parte inferior da área de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="b254b-110">Compose message area: The buttons at the bottom of the compose message area.</span></span>
* <span data-ttu-id="b254b-111">Caixa de comando: @mentioning na caixa de comando.</span><span class="sxs-lookup"><span data-stu-id="b254b-111">Command box: By @mentioning in the command box.</span></span>

<span data-ttu-id="b254b-112">Quando o comando de pesquisa é invocado da área de mensagem de composição, o usuário envia os resultados para a conversa.</span><span class="sxs-lookup"><span data-stu-id="b254b-112">When search command is invoked from the compose message area, the user sends the results to the conversation.</span></span> <span data-ttu-id="b254b-113">Quando ele é invocado da caixa de comando, o usuário interage com o cartão resultante ou o copia para uso em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="b254b-113">When it is invoked from the command box, the user interacts with the resulting card, or copies it for use elsewhere.</span></span>

<span data-ttu-id="b254b-114">A imagem a seguir exibe os locais de invocação do comando de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="b254b-114">The following image displays the invoke locations of the search command:</span></span>

![locais de invocação de comando de pesquisa](~/assets/images/messaging-extension/search-command-invoke-locations.png)

## <a name="add-the-search-command-to-your-app-manifest"></a><span data-ttu-id="b254b-116">Adicionar o comando de pesquisa ao manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="b254b-116">Add the search command to your app manifest</span></span>

<span data-ttu-id="b254b-117">Para adicionar o comando de pesquisa ao manifesto do aplicativo, você deve adicionar um novo objeto ao nível superior `composeExtension` do manifesto JSON do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b254b-117">To add the search command to your app manifest, you must add a new `composeExtension` object to the top level of your app manifest JSON.</span></span> <span data-ttu-id="b254b-118">Você pode adicionar o comando de pesquisa com a ajuda do App Studio ou manualmente.</span><span class="sxs-lookup"><span data-stu-id="b254b-118">You can add the search command either with the help of App Studio, or manually.</span></span>

### <a name="create-a-search-command-using-app-studio"></a><span data-ttu-id="b254b-119">Criar um comando de pesquisa usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="b254b-119">Create a search command using App Studio</span></span>

<span data-ttu-id="b254b-120">O pré-requisito para criar um comando de pesquisa é que você já deve ter criado uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b254b-120">The prerequisite to create a search command is that you must already have created a messaging extension.</span></span> <span data-ttu-id="b254b-121">Para obter informações sobre como criar uma extensão de mensagens, consulte [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="b254b-121">For information on how to create a messaging extension, see [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span></span>

<span data-ttu-id="b254b-122">**Para criar um comando de pesquisa**</span><span class="sxs-lookup"><span data-stu-id="b254b-122">**To create a search command**</span></span>

1. <span data-ttu-id="b254b-123">Abra **o App Studio** no cliente Microsoft Teams e selecione a guia Editor **de** Manifesto.</span><span class="sxs-lookup"><span data-stu-id="b254b-123">Open **App Studio** from the Microsoft Teams client, and select the **Manifest Editor** tab.</span></span>
1.  <span data-ttu-id="b254b-124">Se você já criou seu pacote de aplicativos **no App Studio**, selecione na lista.</span><span class="sxs-lookup"><span data-stu-id="b254b-124">If you already created your app package in **App Studio**, select from the list.</span></span> <span data-ttu-id="b254b-125">Se você não tiver criado um pacote de aplicativos, importe um existente.</span><span class="sxs-lookup"><span data-stu-id="b254b-125">If you have not created an app package, import an existing one.</span></span>
1. <span data-ttu-id="b254b-126">Depois de importar o pacote de aplicativos, selecione **Extensões de mensagens** em **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="b254b-126">After importing app package, select **Messaging extensions** under **Capabilities**.</span></span> <span data-ttu-id="b254b-127">Você tem uma janela pop-up para configurar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b254b-127">You get a pop-up window to set up the messaging extension.</span></span>
1. <span data-ttu-id="b254b-128">Selecione **Configurar na** janela para incluir a extensão de mensagens na experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b254b-128">Select **Set up** in the window to include the messaging extension in your app experience.</span></span> <span data-ttu-id="b254b-129">A imagem a seguir exibe a página de configuração de extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="b254b-129">The following image displays the messaging extension set up page:</span></span> 

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>

1. <span data-ttu-id="b254b-130">Para criar a extensão de mensagens, você precisa de um bot registrado da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b254b-130">To create the messaging extension, you need a Microsoft registered bot.</span></span> <span data-ttu-id="b254b-131">Você pode usar um bot existente ou criar um novo bot.</span><span class="sxs-lookup"><span data-stu-id="b254b-131">You can either use an existing bot or create a new bot.</span></span> <span data-ttu-id="b254b-132">Selecione **Criar nova opção bot,** dê um nome para o novo bot e selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="b254b-132">Select **Create new bot** option, give a name for the new bot, and select **Create**.</span></span> <span data-ttu-id="b254b-133">A imagem a seguir exibe a criação de bots para extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="b254b-133">The following image displays bot creation for messaging extension:</span></span>

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. <span data-ttu-id="b254b-134">Selecione **Adicionar** na seção **Comando da** página extensões de mensagens para incluir os comandos que decidem o comportamento da extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b254b-134">Select **Add** in the **Command section** of the messaging extensions page to include the commands which decides the behaviour of messaging extension.</span></span>   
<span data-ttu-id="b254b-135">A imagem a seguir exibe a adição de comando para extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="b254b-135">The following image displays command addition for messaging extension:</span></span>

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>
1. <span data-ttu-id="b254b-136">Selecione **Permitir que os usuários consultem seu serviço para obter informações e insira-os em uma mensagem**.</span><span class="sxs-lookup"><span data-stu-id="b254b-136">Select **Allow users to query your service for information and insert that into a message**.</span></span> <span data-ttu-id="b254b-137">A imagem a seguir exibe a seleção do parâmetro de comando de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="b254b-137">The following image displays the search command parameter selection:</span></span>

    <img src="~/assets/images/messaging-extension/search-command-parameter-selection.png" alt="search command parameter selection" width="500"/>

1. <span data-ttu-id="b254b-138">Adicione uma **ID de Comando** e um **Título.**</span><span class="sxs-lookup"><span data-stu-id="b254b-138">Add a **Command Id** and a **Title**.</span></span>
1. <span data-ttu-id="b254b-139">Selecione o local de onde o comando de pesquisa deve ser invocado.</span><span class="sxs-lookup"><span data-stu-id="b254b-139">Select the location from where your search command must be invoked.</span></span> <span data-ttu-id="b254b-140">Selecionar **mensagem** no momento não altera o comportamento do comando de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b254b-140">Selecting **message** does not currently alter the behavior of your search command.</span></span> <span data-ttu-id="b254b-141">A imagem a seguir exibe o local de invocação do comando de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="b254b-141">The following image displays the search command invoke location:</span></span>

    <img src="~/assets/images/messaging-extension/search-command-invoke-location-selection.png" alt="search command invoke location selection]" width="500"/>

1. <span data-ttu-id="b254b-142">Adicione o parâmetro de pesquisa e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="b254b-142">Add your search parameter and select **Save**.</span></span>

### <a name="create-a-search-command-manually"></a><span data-ttu-id="b254b-143">Criar um comando de pesquisa manualmente</span><span class="sxs-lookup"><span data-stu-id="b254b-143">Create a search command manually</span></span> 

<span data-ttu-id="b254b-144">Para adicionar manualmente o comando de pesquisa de extensão de mensagens ao manifesto do aplicativo, adicione os seguintes parâmetros à `composeExtension.commands` sua matriz de objetos:</span><span class="sxs-lookup"><span data-stu-id="b254b-144">To manually add your messaging extension search command to your app manifest, you must add the following parameters to your `composeExtension.commands` array of objects:</span></span>

| <span data-ttu-id="b254b-145">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="b254b-145">Property name</span></span> | <span data-ttu-id="b254b-146">Objetivo</span><span class="sxs-lookup"><span data-stu-id="b254b-146">Purpose</span></span> | <span data-ttu-id="b254b-147">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="b254b-147">Required?</span></span> | <span data-ttu-id="b254b-148">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="b254b-148">Minimum manifest version</span></span> |
|---|---|---|---|
| `id` | <span data-ttu-id="b254b-149">Essa propriedade é uma ID exclusiva que você atribui ao comando de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b254b-149">This property is an unique ID that you assign to search command.</span></span> <span data-ttu-id="b254b-150">A solicitação do usuário inclui essa ID.</span><span class="sxs-lookup"><span data-stu-id="b254b-150">The user request includes this ID.</span></span> | <span data-ttu-id="b254b-151">Sim</span><span class="sxs-lookup"><span data-stu-id="b254b-151">Yes</span></span> | <span data-ttu-id="b254b-152">1.0</span><span class="sxs-lookup"><span data-stu-id="b254b-152">1.0</span></span> |
| `title` | <span data-ttu-id="b254b-153">Essa propriedade é um nome de comando.</span><span class="sxs-lookup"><span data-stu-id="b254b-153">This property is a command name.</span></span> <span data-ttu-id="b254b-154">Esse valor aparece na interface do usuário (interface do usuário).</span><span class="sxs-lookup"><span data-stu-id="b254b-154">This value appears in the user interface (UI).</span></span> | <span data-ttu-id="b254b-155">Sim</span><span class="sxs-lookup"><span data-stu-id="b254b-155">Yes</span></span> | <span data-ttu-id="b254b-156">1.0</span><span class="sxs-lookup"><span data-stu-id="b254b-156">1.0</span></span> |
| `description` | <span data-ttu-id="b254b-157">Essa propriedade é um texto de ajuda que indica o que esse comando faz.</span><span class="sxs-lookup"><span data-stu-id="b254b-157">This property is a help text indicating what this command does.</span></span> <span data-ttu-id="b254b-158">Esse valor aparece na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="b254b-158">This value appears in the UI.</span></span> | <span data-ttu-id="b254b-159">Sim</span><span class="sxs-lookup"><span data-stu-id="b254b-159">Yes</span></span> | <span data-ttu-id="b254b-160">1.0</span><span class="sxs-lookup"><span data-stu-id="b254b-160">1.0</span></span> |
| `type` | <span data-ttu-id="b254b-161">Essa propriedade deve ser `query` um .</span><span class="sxs-lookup"><span data-stu-id="b254b-161">This property must be a `query`.</span></span> | <span data-ttu-id="b254b-162">Não</span><span class="sxs-lookup"><span data-stu-id="b254b-162">No</span></span> | <span data-ttu-id="b254b-163">1.4</span><span class="sxs-lookup"><span data-stu-id="b254b-163">1.4</span></span> |
|`initialRun` | <span data-ttu-id="b254b-164">Se essa propriedade for definida como **true**, ele indicará que esse comando deve ser executado assim que o usuário selecionar esse comando na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="b254b-164">If this property is set to **true**, it indicates this command should be executed as soon as the user selects this command in the UI.</span></span> | <span data-ttu-id="b254b-165">Não</span><span class="sxs-lookup"><span data-stu-id="b254b-165">No</span></span> | <span data-ttu-id="b254b-166">1.0</span><span class="sxs-lookup"><span data-stu-id="b254b-166">1.0</span></span> |
| `context` | <span data-ttu-id="b254b-167">Essa propriedade é uma matriz opcional de valores que define o contexto em que a ação de pesquisa está disponível.</span><span class="sxs-lookup"><span data-stu-id="b254b-167">This property is an optional array of values that defines the context the search action is available in.</span></span> <span data-ttu-id="b254b-168">Os valores possíveis são `message`, `compose` ou `commandBox`.</span><span class="sxs-lookup"><span data-stu-id="b254b-168">The possible values are `message`, `compose`, or `commandBox`.</span></span> <span data-ttu-id="b254b-169">O padrão é `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="b254b-169">The default is `["compose", "commandBox"]`.</span></span> | <span data-ttu-id="b254b-170">Não</span><span class="sxs-lookup"><span data-stu-id="b254b-170">No</span></span> | <span data-ttu-id="b254b-171">1,5</span><span class="sxs-lookup"><span data-stu-id="b254b-171">1.5</span></span> |

<span data-ttu-id="b254b-172">Você deve adicionar os detalhes do parâmetro de pesquisa, que define o texto visível para o usuário no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="b254b-172">You must add the details of the search parameter, that defines the text visible to your user in the Teams client.</span></span>

| <span data-ttu-id="b254b-173">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="b254b-173">Property name</span></span> | <span data-ttu-id="b254b-174">Objetivo</span><span class="sxs-lookup"><span data-stu-id="b254b-174">Purpose</span></span> | <span data-ttu-id="b254b-175">É necessário?</span><span class="sxs-lookup"><span data-stu-id="b254b-175">Is required?</span></span> | <span data-ttu-id="b254b-176">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="b254b-176">Minimum manifest version</span></span> |
|---|---|---|---|
| `parameters` | <span data-ttu-id="b254b-177">Essa propriedade define uma lista estática de parâmetros para o comando.</span><span class="sxs-lookup"><span data-stu-id="b254b-177">This property defines a static list of parameters for the command.</span></span> | <span data-ttu-id="b254b-178">Não</span><span class="sxs-lookup"><span data-stu-id="b254b-178">No</span></span> | <span data-ttu-id="b254b-179">1.0</span><span class="sxs-lookup"><span data-stu-id="b254b-179">1.0</span></span> |
| `parameter.name` | <span data-ttu-id="b254b-180">Essa propriedade descreve o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b254b-180">This property describes the name of the parameter.</span></span> <span data-ttu-id="b254b-181">Isso é enviado ao seu serviço na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="b254b-181">This is sent to your service in the user request.</span></span> | <span data-ttu-id="b254b-182">Sim</span><span class="sxs-lookup"><span data-stu-id="b254b-182">Yes</span></span> | <span data-ttu-id="b254b-183">1.0</span><span class="sxs-lookup"><span data-stu-id="b254b-183">1.0</span></span> |
| `parameter.description` | <span data-ttu-id="b254b-184">Esta propriedade descreve as finalidades do parâmetro ou o exemplo do valor que deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="b254b-184">This property describes the parameter’s purposes or example of the value that must be provided.</span></span> <span data-ttu-id="b254b-185">Esse valor aparece na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="b254b-185">This value appears in the UI.</span></span> | <span data-ttu-id="b254b-186">Sim</span><span class="sxs-lookup"><span data-stu-id="b254b-186">Yes</span></span> | <span data-ttu-id="b254b-187">1.0</span><span class="sxs-lookup"><span data-stu-id="b254b-187">1.0</span></span> |
| `parameter.title` | <span data-ttu-id="b254b-188">Essa propriedade é um título ou rótulo de parâmetro fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="b254b-188">This property is a short user-friendly parameter title or label.</span></span> | <span data-ttu-id="b254b-189">Sim</span><span class="sxs-lookup"><span data-stu-id="b254b-189">Yes</span></span> | <span data-ttu-id="b254b-190">1.0</span><span class="sxs-lookup"><span data-stu-id="b254b-190">1.0</span></span> |
| `parameter.inputType` | <span data-ttu-id="b254b-191">Essa propriedade é definida como o tipo de entrada necessária.</span><span class="sxs-lookup"><span data-stu-id="b254b-191">This property is set to the type of the input required.</span></span> <span data-ttu-id="b254b-192">Os valores possíveis `text` `textarea` incluem , `number` , , , , `date` `time` `toggle` .</span><span class="sxs-lookup"><span data-stu-id="b254b-192">Possible values include `text`, `textarea`, `number`, `date`, `time`, `toggle`.</span></span> <span data-ttu-id="b254b-193">O padrão é definido como `text` .</span><span class="sxs-lookup"><span data-stu-id="b254b-193">Default is set to `text`.</span></span> | <span data-ttu-id="b254b-194">Não</span><span class="sxs-lookup"><span data-stu-id="b254b-194">No</span></span> | <span data-ttu-id="b254b-195">1.4</span><span class="sxs-lookup"><span data-stu-id="b254b-195">1.4</span></span> |

#### <a name="example"></a><span data-ttu-id="b254b-196">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b254b-196">Example</span></span>

<span data-ttu-id="b254b-197">A seção a seguir é um exemplo do manifesto de aplicativo simples do `composeExtensions` objeto que define um comando de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="b254b-197">Following section is an example of the simple app manifest of the `composeExtensions` object defining a search command:</span></span> 

```json
{
...
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [{
          "id": "searchCmd",
          "description": "Search Bing for information on the web",
          "title": "Search",
          "initialRun": true,
          "parameters": [{
            "name": "searchKeyword",
            "description": "Enter your search keywords",
            "title": "Keywords"
          }]
        }
      ]
    }
  ],
...
}
```
<span data-ttu-id="b254b-198">Para o manifesto completo do aplicativo, consulte [Esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="b254b-198">For the complete app manifest, see [App manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="b254b-199">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="b254b-199">Code sample</span></span>

| <span data-ttu-id="b254b-200">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="b254b-200">Sample Name</span></span>           | <span data-ttu-id="b254b-201">Descrição</span><span class="sxs-lookup"><span data-stu-id="b254b-201">Description</span></span> | <span data-ttu-id="b254b-202">.NET</span><span class="sxs-lookup"><span data-stu-id="b254b-202">.NET</span></span>    | <span data-ttu-id="b254b-203">Node.js</span><span class="sxs-lookup"><span data-stu-id="b254b-203">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="b254b-204">Teams ação de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="b254b-204">Teams messaging extension action</span></span>| <span data-ttu-id="b254b-205">Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="b254b-205">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="b254b-206">View</span><span class="sxs-lookup"><span data-stu-id="b254b-206">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="b254b-207">View</span><span class="sxs-lookup"><span data-stu-id="b254b-207">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="b254b-208">Teams de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="b254b-208">Teams messaging extension search</span></span>   |  <span data-ttu-id="b254b-209">Descreve como definir comandos de pesquisa e responder a pesquisas.</span><span class="sxs-lookup"><span data-stu-id="b254b-209">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="b254b-210">View</span><span class="sxs-lookup"><span data-stu-id="b254b-210">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="b254b-211">View</span><span class="sxs-lookup"><span data-stu-id="b254b-211">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a><span data-ttu-id="b254b-212">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="b254b-212">Next step</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="b254b-213">[Responder aos comandos de pesquisa](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span><span class="sxs-lookup"><span data-stu-id="b254b-213">[Respond to the search commands](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

