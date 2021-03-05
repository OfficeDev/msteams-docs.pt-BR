---
title: Definir comandos de pesquisa de extensão de mensagens
author: clearab
description: Definir comandos de pesquisa de extensão de mensagens para aplicativos do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 18bac3049fec8fead168c12f2832bfbbb72cf609
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449266"
---
# <a name="define-messaging-extension-search-commands"></a><span data-ttu-id="3f131-103">Definir comandos de pesquisa de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="3f131-103">Define messaging extension search commands</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="3f131-104">Comandos de pesquisa de extensão de mensagens permitem que os usuários pesquisem sistemas externos e insiram os resultados dessa pesquisa em uma mensagem na forma de um cartão.</span><span class="sxs-lookup"><span data-stu-id="3f131-104">Messaging extension search commands allow your users to search external systems and insert the results of that search into a message in the form of a card.</span></span>

> [!NOTE]
> <span data-ttu-id="3f131-105">O limite de tamanho do cartão de resultado é de 28 KB.</span><span class="sxs-lookup"><span data-stu-id="3f131-105">The result card size limit is 28 KB.</span></span> <span data-ttu-id="3f131-106">O cartão não será enviado se seu tamanho exceder 28 KB.</span><span class="sxs-lookup"><span data-stu-id="3f131-106">The card is not sent if its size exceeds 28 KB.</span></span> 

## <a name="choose-messaging-extension-invoke-locations"></a><span data-ttu-id="3f131-107">Escolher locais de invocação de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="3f131-107">Choose messaging extension invoke locations</span></span>

<span data-ttu-id="3f131-108">A primeira coisa que você precisa decidir é de onde o comando de pesquisa pode ser acionado (ou especificamente, *invocado*).</span><span class="sxs-lookup"><span data-stu-id="3f131-108">The first thing you need to decide is where your search command can be triggered (or specifically, *invoked*) from.</span></span> <span data-ttu-id="3f131-109">Seu comando de pesquisa pode ser invocado de um ou ambos os seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="3f131-109">Your search command can be invoked from one or both of the following locations:</span></span>

* <span data-ttu-id="3f131-110">Os botões na parte inferior da área de mensagem de redação</span><span class="sxs-lookup"><span data-stu-id="3f131-110">The buttons at the bottom of the compose message area</span></span>
* <span data-ttu-id="3f131-111">Por @mentioning na caixa de comando</span><span class="sxs-lookup"><span data-stu-id="3f131-111">By @mentioning in the command box</span></span>

<span data-ttu-id="3f131-112">Quando invocado da área de mensagem de redação, o usuário terá a opção de enviar os resultados para a conversa.</span><span class="sxs-lookup"><span data-stu-id="3f131-112">When invoked from the compose message area, your user will have the option of sending the results to the conversation.</span></span> <span data-ttu-id="3f131-113">Quando invocado da caixa de comando, o usuário pode interagir com o cartão resultante ou copiá-lo para uso em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="3f131-113">When invoked from the command box, the user can interact with the resulting card, or copy it for use elsewhere.</span></span>

## <a name="add-the-command-to-your-app-manifest"></a><span data-ttu-id="3f131-114">Adicionar o comando ao manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3f131-114">Add the command to your app manifest</span></span>

<span data-ttu-id="3f131-115">Agora que você decidiu como os usuários interagirão com seu comando de pesquisa, é hora de adicioná-lo ao manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f131-115">Now that you've decided how users will interact with your search command, it is time to add it to your app manifest.</span></span> <span data-ttu-id="3f131-116">Para fazer isso, você adicionará um novo objeto ao nível superior do JSON do `composeExtension` manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f131-116">To do this you'll add a new `composeExtension` object to the top level of your app manifest JSON.</span></span> <span data-ttu-id="3f131-117">Você pode fazer isso com a ajuda do App Studio ou manualmente.</span><span class="sxs-lookup"><span data-stu-id="3f131-117">You can either do so with the help of App Studio, or manually.</span></span>

### <a name="create-a-command-using-app-studio"></a><span data-ttu-id="3f131-118">Criar um comando usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="3f131-118">Create a command using App Studio</span></span>

<span data-ttu-id="3f131-119">O pré-requisito para criar um comando de pesquisa é que você já deve criar uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3f131-119">The prerequisite to create a search command is that you must already create a messaging extension.</span></span> <span data-ttu-id="3f131-120">Para obter informações sobre como criar uma extensão de mensagens, consulte [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="3f131-120">For information on how to create a messaging extension, see [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span></span>

<span data-ttu-id="3f131-121">**Para criar um comando de pesquisa**</span><span class="sxs-lookup"><span data-stu-id="3f131-121">**To create a search command**</span></span>

1. <span data-ttu-id="3f131-122">No cliente do Microsoft Teams, abra **o App Studio** e selecione a guia Editor **de** manifesto.</span><span class="sxs-lookup"><span data-stu-id="3f131-122">From the Microsoft Teams client, open **App Studio**, and select the **Manifest editor** tab.</span></span>
1. <span data-ttu-id="3f131-123">Se você já criou um pacote de aplicativos no **App Studio**, escolha-o na lista.</span><span class="sxs-lookup"><span data-stu-id="3f131-123">If you already created an app package in the **App Studio**, choose it from the list.</span></span> <span data-ttu-id="3f131-124">Se você não tiver criado um pacote de aplicativos, importe um existente.</span><span class="sxs-lookup"><span data-stu-id="3f131-124">If you have not created an app package, import an existing one.</span></span>
1. <span data-ttu-id="3f131-125">Depois de importar um pacote de aplicativos, selecione **Extensões de mensagens** em **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="3f131-125">After importing an app package, select **Messaging extensions** under **Capabilities**.</span></span>
1. <span data-ttu-id="3f131-126">Selecione **Adicionar** na seção **Comando** na página extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3f131-126">Select **Add** in the **Command** section in the messaging extensions page.</span></span>
1. <span data-ttu-id="3f131-127">Escolha **Permitir que os usuários consultem seu serviço para obter informações e insira-os em uma mensagem**.</span><span class="sxs-lookup"><span data-stu-id="3f131-127">Choose **Allow users to query your service for information and insert that into a message**.</span></span>
1. <span data-ttu-id="3f131-128">Adicione uma **ID de Comando** e um **Título.**</span><span class="sxs-lookup"><span data-stu-id="3f131-128">Add a **Command Id** and a **Title**.</span></span>
1. <span data-ttu-id="3f131-129">Selecione o local de onde o comando de pesquisa deve ser acionado.</span><span class="sxs-lookup"><span data-stu-id="3f131-129">Select the location from where your search command must be triggered.</span></span> <span data-ttu-id="3f131-130">Selecionar **mensagem** no momento não altera o comportamento do comando de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="3f131-130">Selecting **message** does not currently alter the behavior of your search command.</span></span>
1. <span data-ttu-id="3f131-131">Adicione o parâmetro de pesquisa e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="3f131-131">Add your search parameter and select **Save**.</span></span>
 
### <a name="manually-create-a-command"></a><span data-ttu-id="3f131-132">Criar manualmente um comando</span><span class="sxs-lookup"><span data-stu-id="3f131-132">Manually create a command</span></span>

<span data-ttu-id="3f131-133">Para adicionar manualmente o comando de pesquisa de extensão de mensagens ao manifesto do aplicativo, você precisará adicionar os seguintes parâmetros à `composeExtension.commands` sua matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="3f131-133">To manually add your messaging extension search command to your app manifest, you'll need to add the following parameters to your `composeExtension.commands` array of objects.</span></span>

| <span data-ttu-id="3f131-134">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="3f131-134">Property name</span></span> | <span data-ttu-id="3f131-135">Finalidade</span><span class="sxs-lookup"><span data-stu-id="3f131-135">Purpose</span></span> | <span data-ttu-id="3f131-136">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="3f131-136">Required?</span></span> | <span data-ttu-id="3f131-137">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="3f131-137">Minimum manifest version</span></span> |
|---|---|---|---|
| `id` | <span data-ttu-id="3f131-138">ID exclusiva que você atribui a esse comando.</span><span class="sxs-lookup"><span data-stu-id="3f131-138">Unique ID that you assign to this command.</span></span> <span data-ttu-id="3f131-139">A solicitação do usuário incluirá essa ID.</span><span class="sxs-lookup"><span data-stu-id="3f131-139">The user request will include this ID.</span></span> | <span data-ttu-id="3f131-140">Sim</span><span class="sxs-lookup"><span data-stu-id="3f131-140">Yes</span></span> | <span data-ttu-id="3f131-141">1.0</span><span class="sxs-lookup"><span data-stu-id="3f131-141">1.0</span></span> |
| `title` | <span data-ttu-id="3f131-142">Nome do comando.</span><span class="sxs-lookup"><span data-stu-id="3f131-142">Command name.</span></span> <span data-ttu-id="3f131-143">Esse valor aparece na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="3f131-143">This value appears in the UI.</span></span> | <span data-ttu-id="3f131-144">Sim</span><span class="sxs-lookup"><span data-stu-id="3f131-144">Yes</span></span> | <span data-ttu-id="3f131-145">1.0</span><span class="sxs-lookup"><span data-stu-id="3f131-145">1.0</span></span> |
| `description` | <span data-ttu-id="3f131-146">Texto de ajuda que indica o que esse comando faz.</span><span class="sxs-lookup"><span data-stu-id="3f131-146">Help text indicating what this command does.</span></span> <span data-ttu-id="3f131-147">Esse valor aparece na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="3f131-147">This value appears in the UI.</span></span> | <span data-ttu-id="3f131-148">Sim</span><span class="sxs-lookup"><span data-stu-id="3f131-148">Yes</span></span> | <span data-ttu-id="3f131-149">1.0</span><span class="sxs-lookup"><span data-stu-id="3f131-149">1.0</span></span> |
| `type` | <span data-ttu-id="3f131-150">Deve ser `query`</span><span class="sxs-lookup"><span data-stu-id="3f131-150">Must be `query`</span></span> | <span data-ttu-id="3f131-151">Não</span><span class="sxs-lookup"><span data-stu-id="3f131-151">No</span></span> | <span data-ttu-id="3f131-152">1.4</span><span class="sxs-lookup"><span data-stu-id="3f131-152">1.4</span></span> |
|`initialRun` | <span data-ttu-id="3f131-153">Se definido como **true**, indica que esse comando deve ser executado assim que o usuário escolher esse comando na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="3f131-153">If set to **true**, indicates this command should be executed as soon as the user chooses this command in the UI.</span></span> | <span data-ttu-id="3f131-154">Não</span><span class="sxs-lookup"><span data-stu-id="3f131-154">No</span></span> | <span data-ttu-id="3f131-155">1.0</span><span class="sxs-lookup"><span data-stu-id="3f131-155">1.0</span></span> |
| `context` | <span data-ttu-id="3f131-156">Matriz opcional de valores que define o contexto em que a ação de pesquisa está disponível.</span><span class="sxs-lookup"><span data-stu-id="3f131-156">Optional array of values that defines the context the search action is available in.</span></span> <span data-ttu-id="3f131-157">Os valores possíveis `message` são `compose` , ou `commandBox` .</span><span class="sxs-lookup"><span data-stu-id="3f131-157">Possible values are `message`, `compose`, or `commandBox`.</span></span> <span data-ttu-id="3f131-158">O padrão é `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="3f131-158">Default is `["compose", "commandBox"]`.</span></span> | <span data-ttu-id="3f131-159">Não</span><span class="sxs-lookup"><span data-stu-id="3f131-159">No</span></span> | <span data-ttu-id="3f131-160">1,5</span><span class="sxs-lookup"><span data-stu-id="3f131-160">1.5</span></span> |

<span data-ttu-id="3f131-161">Você também precisará adicionar os detalhes do parâmetro de pesquisa, que definirá o texto visível para seu usuário no cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="3f131-161">You'll also need to add the details of the search parameter, which will define the text visible to your user in the Teams client.</span></span>

| <span data-ttu-id="3f131-162">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="3f131-162">Property name</span></span> | <span data-ttu-id="3f131-163">Finalidade</span><span class="sxs-lookup"><span data-stu-id="3f131-163">Purpose</span></span> | <span data-ttu-id="3f131-164">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="3f131-164">Required?</span></span> | <span data-ttu-id="3f131-165">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="3f131-165">Minimum manifest version</span></span> |
|---|---|---|---|
| `parameters` | <span data-ttu-id="3f131-166">Lista estática de parâmetros para o comando.</span><span class="sxs-lookup"><span data-stu-id="3f131-166">Static list of parameters for the command.</span></span> | <span data-ttu-id="3f131-167">Não</span><span class="sxs-lookup"><span data-stu-id="3f131-167">No</span></span> | <span data-ttu-id="3f131-168">1.0</span><span class="sxs-lookup"><span data-stu-id="3f131-168">1.0</span></span> |
| `parameter.name` | <span data-ttu-id="3f131-169">O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3f131-169">The name of the parameter.</span></span> <span data-ttu-id="3f131-170">Isso é enviado ao seu serviço na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="3f131-170">This is sent to your service in the user request.</span></span> | <span data-ttu-id="3f131-171">Sim</span><span class="sxs-lookup"><span data-stu-id="3f131-171">Yes</span></span> | <span data-ttu-id="3f131-172">1.0</span><span class="sxs-lookup"><span data-stu-id="3f131-172">1.0</span></span> |
| `parameter.description` | <span data-ttu-id="3f131-173">Descreve as finalidades desse parâmetro ou o exemplo do valor que deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="3f131-173">Describes this parameter’s purposes or example of the value that should be provided.</span></span> <span data-ttu-id="3f131-174">Esse valor aparece na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="3f131-174">This value appears in the UI.</span></span> | <span data-ttu-id="3f131-175">Sim</span><span class="sxs-lookup"><span data-stu-id="3f131-175">Yes</span></span> | <span data-ttu-id="3f131-176">1.0</span><span class="sxs-lookup"><span data-stu-id="3f131-176">1.0</span></span> |
| `parameter.title` | <span data-ttu-id="3f131-177">Título ou rótulo de parâmetro fácil de usar curto.</span><span class="sxs-lookup"><span data-stu-id="3f131-177">Short user-friendly parameter title or label.</span></span> | <span data-ttu-id="3f131-178">Sim</span><span class="sxs-lookup"><span data-stu-id="3f131-178">Yes</span></span> | <span data-ttu-id="3f131-179">1.0</span><span class="sxs-lookup"><span data-stu-id="3f131-179">1.0</span></span> |
| `parameter.inputType` | <span data-ttu-id="3f131-180">De acordo com o tipo de entrada necessário.</span><span class="sxs-lookup"><span data-stu-id="3f131-180">Set to the type of input required.</span></span> <span data-ttu-id="3f131-181">Os valores possíveis `text` `textarea` incluem , `number` , , , , `date` `time` `toggle` .</span><span class="sxs-lookup"><span data-stu-id="3f131-181">Possible values include `text`, `textarea`, `number`, `date`, `time`, `toggle`.</span></span> <span data-ttu-id="3f131-182">Padrão é definido como `text`</span><span class="sxs-lookup"><span data-stu-id="3f131-182">Default is set to `text`</span></span> | <span data-ttu-id="3f131-183">Não</span><span class="sxs-lookup"><span data-stu-id="3f131-183">No</span></span> | <span data-ttu-id="3f131-184">1.4</span><span class="sxs-lookup"><span data-stu-id="3f131-184">1.4</span></span> |

#### <a name="app-manifest-example"></a><span data-ttu-id="3f131-185">Exemplo de manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3f131-185">App manifest example</span></span>

<span data-ttu-id="3f131-186">Veja a seguir um exemplo de `composeExtensions` um objeto que define um comando de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="3f131-186">Below is an example of a `composeExtensions` object defining a search command.</span></span> <span data-ttu-id="3f131-187">Não é um exemplo do manifesto completo, para o esquema de manifesto completo do aplicativo, consulte: [Esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="3f131-187">It is not an example of the complete manifest, for the full app manifest schema see: [App manifest schema](~/resources/schema/manifest-schema.md).</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="3f131-188">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3f131-188">Next steps</span></span>

<span data-ttu-id="3f131-189">Agora que você adicionou o comando de pesquisa, precisará lidar [com a solicitação de pesquisa](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span><span class="sxs-lookup"><span data-stu-id="3f131-189">Now that you've added your search command, you'll need to [handle the search request](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
