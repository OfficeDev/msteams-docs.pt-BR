---
title: Definir comandos de pesquisa de extensão de mensagens
author: clearab
description: Definir comandos de pesquisa de extensão de mensagens para os aplicativos do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: b6837fb8a131d8ce3e2bbd0c51c2861dbffda2bc
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672762"
---
# <a name="define-messaging-extension-search-commands"></a><span data-ttu-id="85c4b-103">Definir comandos de pesquisa de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="85c4b-103">Define messaging extension search commands</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="85c4b-104">Os comandos de pesquisa de extensão de mensagens permitem que os usuários pesquisem sistemas externos e insiram os resultados da pesquisa em uma mensagem na forma de um cartão.</span><span class="sxs-lookup"><span data-stu-id="85c4b-104">Messaging extension search commands allow your users to search external systems and insert the results of that search into a message in the form of a card.</span></span>

## <a name="choose-messaging-extension-invoke-locations"></a><span data-ttu-id="85c4b-105">Escolher locais de invocação de mensagens</span><span class="sxs-lookup"><span data-stu-id="85c4b-105">Choose messaging extension invoke locations</span></span>

<span data-ttu-id="85c4b-106">A primeira coisa que você precisa decidir é onde o comando de pesquisa pode ser acionado (ou mais especificamente, *invocado*) a partir do.</span><span class="sxs-lookup"><span data-stu-id="85c4b-106">The first thing you need to decide is where your search command can be triggered (or more specifically, *invoked*) from.</span></span> <span data-ttu-id="85c4b-107">O comando de pesquisa pode ser chamado a partir de um ou dos dois locais a seguir:</span><span class="sxs-lookup"><span data-stu-id="85c4b-107">Your search command can be invoked from one or both of the following locations:</span></span>

* <span data-ttu-id="85c4b-108">Os botões na parte inferior da área de redação da mensagem</span><span class="sxs-lookup"><span data-stu-id="85c4b-108">The buttons at the bottom of the compose message area</span></span>
* <span data-ttu-id="85c4b-109">Por @mentioning na caixa comando</span><span class="sxs-lookup"><span data-stu-id="85c4b-109">By @mentioning in the command box</span></span>

<span data-ttu-id="85c4b-110">Quando invocado da área de mensagem de composição, o usuário terá a opção de enviar os resultados para a conversa.</span><span class="sxs-lookup"><span data-stu-id="85c4b-110">When invoked from the compose message area, your user will have the option of sending the results to the conversation.</span></span> <span data-ttu-id="85c4b-111">Quando invocado na caixa comando, o usuário pode interagir com o cartão resultante ou copiá-lo para uso em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="85c4b-111">When invoked from the command box, the user can interact with the resulting card, or copy it for use elsewhere.</span></span>

## <a name="add-the-command-to-your-app-manifest"></a><span data-ttu-id="85c4b-112">Adicione o comando ao manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="85c4b-112">Add the command to your app manifest</span></span>

<span data-ttu-id="85c4b-113">Agora que você decidiu como os usuários irão interagir com seu comando de pesquisa, é hora de adicioná-lo ao manifesto do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85c4b-113">Now that you've decided how users will interact with your search command, it is time to add it to your app manifest.</span></span> <span data-ttu-id="85c4b-114">Para fazer isso, você adicionará um `composeExtension` novo objeto ao nível superior de seu aplicativo JSON de manifesto.</span><span class="sxs-lookup"><span data-stu-id="85c4b-114">To do this you'll add a new `composeExtension` object to the top level of your app manifest JSON.</span></span> <span data-ttu-id="85c4b-115">Você pode fazer isso com a ajuda do App Studio ou manualmente.</span><span class="sxs-lookup"><span data-stu-id="85c4b-115">You can either do so with the help of App Studio, or manually.</span></span>

### <a name="create-a-command-using-app-studio"></a><span data-ttu-id="85c4b-116">Criar um comando usando o app Studio</span><span class="sxs-lookup"><span data-stu-id="85c4b-116">Create a command using App Studio</span></span>

<span data-ttu-id="85c4b-117">As etapas a seguir supõem que você já tenha [criado uma extensão de mensagens](~/messaging-extensions/how-to/create-messaging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="85c4b-117">The following steps assume you've already [created a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span></span>

1. <span data-ttu-id="85c4b-118">No cliente Microsoft Teams, abra o **app Studio** e selecione a guia **Editor de manifesto** .</span><span class="sxs-lookup"><span data-stu-id="85c4b-118">From the Microsoft Teams client, open **App Studio** and select the **Manifest Editor** tab.</span></span>
2. <span data-ttu-id="85c4b-119">Se você já criou seu pacote de aplicativos no app Studio, escolha-o na lista.</span><span class="sxs-lookup"><span data-stu-id="85c4b-119">If you've already created your app package in App Studio, chose it from the list.</span></span> <span data-ttu-id="85c4b-120">Caso contrário, você pode importar um pacote de aplicativos existente.</span><span class="sxs-lookup"><span data-stu-id="85c4b-120">If not, you can import an existing app package.</span></span>
3. <span data-ttu-id="85c4b-121">Clique no botão **Adicionar** na seção comando.</span><span class="sxs-lookup"><span data-stu-id="85c4b-121">Click the **Add** button in the Command section.</span></span>
4. <span data-ttu-id="85c4b-122">Escolha **permitir que os usuários consultem o serviço para obter informações e insiram isso em uma mensagem**.</span><span class="sxs-lookup"><span data-stu-id="85c4b-122">Choose **Allow users to query your service for information and insert that into a message**.</span></span>
5. <span data-ttu-id="85c4b-123">Adicione uma **ID de comando** e um **título**.</span><span class="sxs-lookup"><span data-stu-id="85c4b-123">Add a **Command Id** and a **Title**.</span></span>
6. <span data-ttu-id="85c4b-124">Selecione onde você deseja que seu comando de pesquisa seja disparado.</span><span class="sxs-lookup"><span data-stu-id="85c4b-124">Select where you want your search command to be triggered from.</span></span> <span data-ttu-id="85c4b-125">Selecionar a **mensagem** não altera atualmente o comportamento do seu comando de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="85c4b-125">Selecting **message** does not currently alter the behavior of your search command.</span></span>
7. <span data-ttu-id="85c4b-126">Adicione o parâmetro de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="85c4b-126">Add your search parameter.</span></span>
8. <span data-ttu-id="85c4b-127">Clique em Salvar.</span><span class="sxs-lookup"><span data-stu-id="85c4b-127">Click Save.</span></span>

### <a name="manually-create-a-command"></a><span data-ttu-id="85c4b-128">Criar um comando manualmente</span><span class="sxs-lookup"><span data-stu-id="85c4b-128">Manually create a command</span></span>

<span data-ttu-id="85c4b-129">Para adicionar manualmente seu comando de pesquisa de extensão de mensagens ao manifesto do seu aplicativo, você precisará adicionar os parâmetros `composeExtension.commands` de acompanhamento à sua matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="85c4b-129">To manually add your messaging extension search command to your app manifest, you'll need to add the follow parameters to your `composeExtension.commands` array of objects.</span></span>

| <span data-ttu-id="85c4b-130">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="85c4b-130">Property name</span></span> | <span data-ttu-id="85c4b-131">Finalidade</span><span class="sxs-lookup"><span data-stu-id="85c4b-131">Purpose</span></span> | <span data-ttu-id="85c4b-132">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="85c4b-132">Required?</span></span> | <span data-ttu-id="85c4b-133">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="85c4b-133">Minimum manifest version</span></span> |
|---|---|---|---|
| `id` | <span data-ttu-id="85c4b-134">ID exclusiva que você atribui a este comando.</span><span class="sxs-lookup"><span data-stu-id="85c4b-134">Unique ID that you assign to this command.</span></span> <span data-ttu-id="85c4b-135">A solicitação do usuário incluirá essa ID.</span><span class="sxs-lookup"><span data-stu-id="85c4b-135">The user request will include this ID.</span></span> | <span data-ttu-id="85c4b-136">Sim</span><span class="sxs-lookup"><span data-stu-id="85c4b-136">Yes</span></span> | <span data-ttu-id="85c4b-137">1.0</span><span class="sxs-lookup"><span data-stu-id="85c4b-137">1.0</span></span> |
| `title` | <span data-ttu-id="85c4b-138">Nome do comando.</span><span class="sxs-lookup"><span data-stu-id="85c4b-138">Command name.</span></span> <span data-ttu-id="85c4b-139">Esse valor é exibido na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="85c4b-139">This value appears in the UI.</span></span> | <span data-ttu-id="85c4b-140">Sim</span><span class="sxs-lookup"><span data-stu-id="85c4b-140">Yes</span></span> | <span data-ttu-id="85c4b-141">1.0</span><span class="sxs-lookup"><span data-stu-id="85c4b-141">1.0</span></span> |
| `description` | <span data-ttu-id="85c4b-142">Texto de ajuda que indica o que esse comando faz.</span><span class="sxs-lookup"><span data-stu-id="85c4b-142">Help text indicating what this command does.</span></span> <span data-ttu-id="85c4b-143">Esse valor é exibido na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="85c4b-143">This value appears in the UI.</span></span> | <span data-ttu-id="85c4b-144">Sim</span><span class="sxs-lookup"><span data-stu-id="85c4b-144">Yes</span></span> | <span data-ttu-id="85c4b-145">1.0</span><span class="sxs-lookup"><span data-stu-id="85c4b-145">1.0</span></span> |
| `type` | <span data-ttu-id="85c4b-146">Deve ser `query`</span><span class="sxs-lookup"><span data-stu-id="85c4b-146">Must be `query`</span></span> | <span data-ttu-id="85c4b-147">Não</span><span class="sxs-lookup"><span data-stu-id="85c4b-147">No</span></span> | <span data-ttu-id="85c4b-148">1.4</span><span class="sxs-lookup"><span data-stu-id="85c4b-148">1.4</span></span> |
|`initialRun` | <span data-ttu-id="85c4b-149">Se definido como **true**, indica que este comando deve ser executado assim que o usuário escolhe este comando na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="85c4b-149">If set to **true**, indicates this command should be executed as soon as the user chooses this command in the UI.</span></span> | <span data-ttu-id="85c4b-150">Não</span><span class="sxs-lookup"><span data-stu-id="85c4b-150">No</span></span> | <span data-ttu-id="85c4b-151">1.0</span><span class="sxs-lookup"><span data-stu-id="85c4b-151">1.0</span></span> |
| `context` | <span data-ttu-id="85c4b-152">Matriz opcional de valores que define o contexto no qual a ação de pesquisa está disponível.</span><span class="sxs-lookup"><span data-stu-id="85c4b-152">Optional array of values that defines the context the search action is available in.</span></span> <span data-ttu-id="85c4b-153">Os valores possíveis `message`são `compose`,, `commandBox`ou.</span><span class="sxs-lookup"><span data-stu-id="85c4b-153">Possible values are `message`, `compose`, or `commandBox`.</span></span> <span data-ttu-id="85c4b-154">O padrão é `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="85c4b-154">Default is `["compose", "commandBox"]`.</span></span> | <span data-ttu-id="85c4b-155">Não</span><span class="sxs-lookup"><span data-stu-id="85c4b-155">No</span></span> | <span data-ttu-id="85c4b-156">1,5</span><span class="sxs-lookup"><span data-stu-id="85c4b-156">1.5</span></span> |

<span data-ttu-id="85c4b-157">Você também precisará adicionar os detalhes do parâmetro Search, que definirá o texto visível para o usuário no cliente Teams.</span><span class="sxs-lookup"><span data-stu-id="85c4b-157">You'll also need to add the details of the search parameter, which will define the text visible to your user in the Teams client.</span></span>

| <span data-ttu-id="85c4b-158">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="85c4b-158">Property name</span></span> | <span data-ttu-id="85c4b-159">Finalidade</span><span class="sxs-lookup"><span data-stu-id="85c4b-159">Purpose</span></span> | <span data-ttu-id="85c4b-160">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="85c4b-160">Required?</span></span> | <span data-ttu-id="85c4b-161">Versão mínima do manifesto</span><span class="sxs-lookup"><span data-stu-id="85c4b-161">Minimum manifest version</span></span> |
|---|---|---|---|
| `parameters` | <span data-ttu-id="85c4b-162">Lista estática de parâmetros para o comando.</span><span class="sxs-lookup"><span data-stu-id="85c4b-162">Static list of parameters for the command.</span></span> | <span data-ttu-id="85c4b-163">Não</span><span class="sxs-lookup"><span data-stu-id="85c4b-163">No</span></span> | <span data-ttu-id="85c4b-164">1.0</span><span class="sxs-lookup"><span data-stu-id="85c4b-164">1.0</span></span> |
| `parameter.name` | <span data-ttu-id="85c4b-165">O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="85c4b-165">The name of the parameter.</span></span> <span data-ttu-id="85c4b-166">Isso é enviado para o serviço na solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="85c4b-166">This is sent to your service in the user request.</span></span> | <span data-ttu-id="85c4b-167">Sim</span><span class="sxs-lookup"><span data-stu-id="85c4b-167">Yes</span></span> | <span data-ttu-id="85c4b-168">1.0</span><span class="sxs-lookup"><span data-stu-id="85c4b-168">1.0</span></span> |
| `parameter.description` | <span data-ttu-id="85c4b-169">Descreve os fins deste parâmetro ou o exemplo do valor que deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="85c4b-169">Describes this parameter’s purposes or example of the value that should be provided.</span></span> <span data-ttu-id="85c4b-170">Esse valor é exibido na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="85c4b-170">This value appears in the UI.</span></span> | <span data-ttu-id="85c4b-171">Sim</span><span class="sxs-lookup"><span data-stu-id="85c4b-171">Yes</span></span> | <span data-ttu-id="85c4b-172">1.0</span><span class="sxs-lookup"><span data-stu-id="85c4b-172">1.0</span></span> |
| `parameter.title` | <span data-ttu-id="85c4b-173">Título ou rótulo curto de parâmetro amigável.</span><span class="sxs-lookup"><span data-stu-id="85c4b-173">Short user-friendly parameter title or label.</span></span> | <span data-ttu-id="85c4b-174">Sim</span><span class="sxs-lookup"><span data-stu-id="85c4b-174">Yes</span></span> | <span data-ttu-id="85c4b-175">1.0</span><span class="sxs-lookup"><span data-stu-id="85c4b-175">1.0</span></span> |
| `parameter.inputType` | <span data-ttu-id="85c4b-176">Defina como o tipo de entrada obrigatória.</span><span class="sxs-lookup"><span data-stu-id="85c4b-176">Set to the type of input required.</span></span> <span data-ttu-id="85c4b-177">Os valores possíveis `text`incluem `textarea`, `number` `date` `time`,,, `toggle`.</span><span class="sxs-lookup"><span data-stu-id="85c4b-177">Possible values include `text`, `textarea`, `number`, `date`, `time`, `toggle`.</span></span> <span data-ttu-id="85c4b-178">O padrão é definido como`text`</span><span class="sxs-lookup"><span data-stu-id="85c4b-178">Default is set to `text`</span></span> | <span data-ttu-id="85c4b-179">Não</span><span class="sxs-lookup"><span data-stu-id="85c4b-179">No</span></span> | <span data-ttu-id="85c4b-180">1.4</span><span class="sxs-lookup"><span data-stu-id="85c4b-180">1.4</span></span> |

#### <a name="app-manifest-example"></a><span data-ttu-id="85c4b-181">Exemplo de manifesto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="85c4b-181">App manifest example</span></span>

<span data-ttu-id="85c4b-182">Veja a seguir um exemplo de um `composeExtensions` objeto que define um comando de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="85c4b-182">The below is an example of a `composeExtensions` object defining a search command.</span></span> <span data-ttu-id="85c4b-183">Não é um exemplo de manifesto completo, para o esquema de manifesto de aplicativo completo, consulte: [esquema de manifesto do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="85c4b-183">It is not an example of the complete manifest, for the full app manifest schema see: [App manifest schema](~/resources/schema/manifest-schema.md).</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="85c4b-184">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="85c4b-184">Next steps</span></span>

<span data-ttu-id="85c4b-185">Agora que você adicionou o comando de pesquisa, precisará [lidar com a solicitação de pesquisa](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span><span class="sxs-lookup"><span data-stu-id="85c4b-185">Now that you've added your search command, you'll need to [handle the search request](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]