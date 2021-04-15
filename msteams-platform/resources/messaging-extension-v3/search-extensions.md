---
title: Pesquisar com extensões de mensagens
description: Descreve como desenvolver extensões de mensagens baseadas em pesquisa
keywords: Pesquisa de extensões de mensagens de mensagens do teams
ms.topic: how-to
ms.date: 07/20/2019
ms.openlocfilehash: 7a4074fe4f3a15621729f4c549d31dc90d98e714
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696099"
---
# <a name="search-with-messaging-extensions"></a><span data-ttu-id="911cd-104">Pesquisar com extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="911cd-104">Search with messaging extensions</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

<span data-ttu-id="911cd-105">Extensões de mensagens baseadas em pesquisa permitem que você consulte seu serviço e poste essas informações na forma de um cartão, direto em sua mensagem</span><span class="sxs-lookup"><span data-stu-id="911cd-105">Search based messaging extensions allow you to query your service and post that information in the form of a card, right into your message</span></span>

![Exemplo de cartão de extensão de mensagens](~/assets/images/compose-extensions/ceexample.png)

<span data-ttu-id="911cd-107">As seções a seguir descrevem como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="911cd-107">The following sections describe how to do this.</span></span>

[!include[common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="search-type-message-extensions"></a><span data-ttu-id="911cd-108">Extensões de mensagem de tipo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="911cd-108">Search type message extensions</span></span>

<span data-ttu-id="911cd-109">Para a extensão de mensagens baseada em pesquisa, de `type` definir o parâmetro como `query` .</span><span class="sxs-lookup"><span data-stu-id="911cd-109">For search based messaging extension set the `type` parameter to `query`.</span></span> <span data-ttu-id="911cd-110">Veja a seguir um exemplo de um manifesto com um único comando de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="911cd-110">Below is an example of a manifest with a single search command.</span></span> <span data-ttu-id="911cd-111">Uma única extensão de mensagens pode ter até 10 comandos diferentes associados a ela.</span><span class="sxs-lookup"><span data-stu-id="911cd-111">A single messaging extension can have up to 10 different commands associated with it.</span></span> <span data-ttu-id="911cd-112">Isso pode incluir vários comandos baseados em ação e pesquisa.</span><span class="sxs-lookup"><span data-stu-id="911cd-112">This can include both multiple search and multiple Action-based commands.</span></span>

#### <a name="complete-app-manifest-example"></a><span data-ttu-id="911cd-113">Exemplo de manifesto completo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="911cd-113">Complete app manifest example</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0",
  "id": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
  "packageName": "com.microsoft.teams.samples.bing",
  "developer": {
    "name": "John Developer",
    "websiteUrl": "http://bingbotservice.azurewebsites.net/",
    "privacyUrl": "http://bingbotservice.azurewebsites.net/privacy",
    "termsOfUseUrl": "http://bingbotservice.azurewebsites.net/termsofuse"
  },
  "name": {
    "short": "Bing",
    "full": "Bing"
  },
  "description": {
    "short": "Find Bing search results",
    "full": "Find Bing search results and share them with your team members."
  },
  "icons": {
    "outline": "bing-outline.jpg",
    "color": "bing-color.jpg"
  },
  "accentColor": "#ff6a00",
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
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "bingbotservice.azurewebsites.net",
    "*.bingbotservice.azurewebsites.net"
  ]
}
```

### <a name="test-via-uploading"></a><span data-ttu-id="911cd-114">Testar por meio do carregamento</span><span class="sxs-lookup"><span data-stu-id="911cd-114">Test via uploading</span></span>

<span data-ttu-id="911cd-115">Você pode testar sua extensão de mensagens carregando seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="911cd-115">You can test your messaging extension by uploading your app.</span></span>

<span data-ttu-id="911cd-116">Para abrir sua extensão de mensagens, navegue até qualquer um dos seus chats ou canais.</span><span class="sxs-lookup"><span data-stu-id="911cd-116">To open your messaging extension, navigate to any of your chats or channels.</span></span> <span data-ttu-id="911cd-117">Escolha o **botão Mais opções** (**&#8943;**) na caixa de redação e escolha sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="911cd-117">Choose the **More options** (**&#8943;**) button in the compose box, and choose your messaging extension.</span></span>

## <a name="add-event-handlers"></a><span data-ttu-id="911cd-118">Adicionar manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="911cd-118">Add event handlers</span></span>

<span data-ttu-id="911cd-119">A maior parte do seu trabalho envolve o evento, que lida com todas as interações na janela de extensão `onQuery` de mensagens.</span><span class="sxs-lookup"><span data-stu-id="911cd-119">Most of your work involves the `onQuery` event, which handles all interactions in the messaging extension window.</span></span>

<span data-ttu-id="911cd-120">Se você definir `canUpdateConfiguration` como `true` no manifesto, habilita o item de menu **Configurações** para sua extensão de mensagens e também deve manipular `onQuerySettingsUrl` e `onSettingsUpdate` .</span><span class="sxs-lookup"><span data-stu-id="911cd-120">If you set `canUpdateConfiguration` to `true` in the manifest, you enable the **Settings** menu item for your messaging extension and must also handle `onQuerySettingsUrl` and `onSettingsUpdate`.</span></span>

### <a name="handle-onquery-events"></a><span data-ttu-id="911cd-121">Manipular eventos onQuery</span><span class="sxs-lookup"><span data-stu-id="911cd-121">Handle onQuery events</span></span>

<span data-ttu-id="911cd-122">Uma extensão de mensagens recebe um evento quando algo acontece na janela de extensão de mensagens ou `onQuery` é enviado para a janela.</span><span class="sxs-lookup"><span data-stu-id="911cd-122">A messaging extension receives an `onQuery` event when anything happens in the messaging extension window or is sent to the window.</span></span>

<span data-ttu-id="911cd-123">Se sua extensão de mensagens usa uma página de configuração, seu manipulador deve primeiro verificar se há informações de configuração armazenadas; se a extensão de mensagens não estiver configurada, retorne uma resposta com um link para sua página de `onQuery` `config` configuração.</span><span class="sxs-lookup"><span data-stu-id="911cd-123">If your messaging extension uses a configuration page, your handler for `onQuery` should first check for any stored configuration information; if the messaging extension isn't configured, return a `config` response with a link to your configuration page.</span></span> <span data-ttu-id="911cd-124">Esteja ciente de que a resposta da página de configuração também é manipulada por `onQuery` .</span><span class="sxs-lookup"><span data-stu-id="911cd-124">Be aware that the response from the configuration page is also handled by `onQuery`.</span></span> <span data-ttu-id="911cd-125">(A única exceção é quando a página de configuração é chamada pelo manipulador para `onQuerySettingsUrl` ; consulte a seção a seguir.)</span><span class="sxs-lookup"><span data-stu-id="911cd-125">(The sole exception is when the configuration page is called by the handler for `onQuerySettingsUrl`; see the following section.)</span></span>

<span data-ttu-id="911cd-126">Se sua extensão de mensagens exigir autenticação, verifique as informações de estado do usuário; se o usuário não estiver assinado, siga as instruções na seção [Autenticação](#authentication) posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="911cd-126">If your messaging extension requires authentication, check the user state information; if the user isn't signed in, follow the instructions in the [Authentication](#authentication) section later in this topic.</span></span>

<span data-ttu-id="911cd-127">Em seguida, verifique se está definido; em caso afirmativa, tome as medidas apropriadas, como fornecer instruções `initialRun` ou uma lista de respostas.</span><span class="sxs-lookup"><span data-stu-id="911cd-127">Next, check whether `initialRun` is set; if so, take appropriate action, such as providing instructions or a list of responses.</span></span>

<span data-ttu-id="911cd-128">O restante do manipulador solicita informações ao usuário, exibe uma lista de cartões de visualização e retorna `onQuery` o cartão selecionado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="911cd-128">The remainder of your handler for `onQuery` prompts the user for information, displays a list of preview cards, and returns the card selected by the user.</span></span>

### <a name="handle-onquerysettingsurl-and-onsettingsupdate-events"></a><span data-ttu-id="911cd-129">Manipular eventos onQuerySettingsUrl e onSettingsUpdate</span><span class="sxs-lookup"><span data-stu-id="911cd-129">Handle onQuerySettingsUrl and onSettingsUpdate events</span></span>

<span data-ttu-id="911cd-130">Os `onQuerySettingsUrl` eventos e funcionam juntos para `onSettingsUpdate` habilitar o item de menu **Configurações.**</span><span class="sxs-lookup"><span data-stu-id="911cd-130">The `onQuerySettingsUrl` and `onSettingsUpdate` events work together to enable the **Settings** menu item.</span></span>

![Capturas de tela de locais do item de menu Configurações](~/assets/images/compose-extensions/compose-extension-settings-menu-item.png)

<span data-ttu-id="911cd-132">Seu manipulador para retorna a URL da página de configuração; depois que a página de configuração é fechado, o manipulador aceita e `onQuerySettingsUrl` `onSettingsUpdate` salva o estado retornado.</span><span class="sxs-lookup"><span data-stu-id="911cd-132">Your handler for `onQuerySettingsUrl` returns the URL for the configuration page; after the configuration page closes, your handler for `onSettingsUpdate` accepts and saves the returned state.</span></span> <span data-ttu-id="911cd-133">(Este é o único caso no qual `onQuery` *não recebe* a resposta da página de configuração.)</span><span class="sxs-lookup"><span data-stu-id="911cd-133">(This is the one case in which `onQuery` *doesn't* receive the response from the configuration page.)</span></span>

## <a name="receive-and-respond-to-queries"></a><span data-ttu-id="911cd-134">Receber e responder a consultas</span><span class="sxs-lookup"><span data-stu-id="911cd-134">Receive and respond to queries</span></span>

<span data-ttu-id="911cd-135">Todas as solicitações para sua extensão de mensagens são feitas por meio de um `Activity` objeto postado em sua URL de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="911cd-135">Every request to your messaging extension is done via an `Activity` object that is posted to your callback URL.</span></span> <span data-ttu-id="911cd-136">A solicitação contém informações sobre o comando do usuário, como ID e valores de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="911cd-136">The request contains information about the user command, such as ID and parameter values.</span></span> <span data-ttu-id="911cd-137">A solicitação também fornece metadados sobre o contexto no qual sua extensão foi invocada, incluindo iD de usuário e locatário, juntamente com ID de chat ou canal e IDs de equipe.</span><span class="sxs-lookup"><span data-stu-id="911cd-137">The request also supplies metadata about the context in which your extension was invoked, including user and tenant ID, along with chat ID or channel and team IDs.</span></span>

### <a name="receive-user-requests"></a><span data-ttu-id="911cd-138">Receber solicitações de usuário</span><span class="sxs-lookup"><span data-stu-id="911cd-138">Receive user requests</span></span>

<span data-ttu-id="911cd-139">Quando um usuário executa uma consulta, o Microsoft Teams envia ao seu serviço um objeto Da Estrutura de `Activity` Bot padrão.</span><span class="sxs-lookup"><span data-stu-id="911cd-139">When a user performs a query, Microsoft Teams sends your service a standard Bot Framework `Activity` object.</span></span> <span data-ttu-id="911cd-140">Seu serviço deve executar sua lógica para um que tenha definido como e definido como um tipo com suporte, conforme `Activity` mostrado na tabela a `type` `invoke` `name` `composeExtension` seguir.</span><span class="sxs-lookup"><span data-stu-id="911cd-140">Your service should perform its logic for an `Activity` that has `type` set to `invoke` and `name` set to a supported `composeExtension` type, as shown in the following table.</span></span>

<span data-ttu-id="911cd-141">Além das propriedades de atividade de bot padrão, a carga contém os seguintes metadados de solicitação:</span><span class="sxs-lookup"><span data-stu-id="911cd-141">In addition to the standard bot activity properties, the payload contains the following request metadata:</span></span>

|<span data-ttu-id="911cd-142">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="911cd-142">Property name</span></span>|<span data-ttu-id="911cd-143">Objetivo</span><span class="sxs-lookup"><span data-stu-id="911cd-143">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="911cd-144">Tipo de solicitação; deve ser `invoke` .</span><span class="sxs-lookup"><span data-stu-id="911cd-144">Type of request; must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="911cd-145">Tipo de comando emitido ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="911cd-145">Type of command that is issued to your service.</span></span> <span data-ttu-id="911cd-146">Atualmente, os seguintes tipos são suportados:</span><span class="sxs-lookup"><span data-stu-id="911cd-146">Currently the following types are supported:</span></span> <br>`composeExtension/query` <br>`composeExtension/querySettingUrl` <br>`composeExtension/setting` <br>`composeExtension/selectItem` <br>`composeExtension/queryLink` |
|`from.id`| <span data-ttu-id="911cd-147">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="911cd-147">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="911cd-148">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="911cd-148">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="911cd-149">ID do objeto do Azure Active Directory do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="911cd-149">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="911cd-150">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="911cd-150">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="911cd-151">ID do canal (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="911cd-151">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="911cd-152">ID da equipe (se a solicitação foi feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="911cd-152">Team ID (if the request was made in a channel).</span></span> |
|`clientInfo`|<span data-ttu-id="911cd-153">Metadados opcionais sobre o software cliente usado para enviar a mensagem de um usuário.</span><span class="sxs-lookup"><span data-stu-id="911cd-153">Optional metadata about the client software used to send a user's message.</span></span> <span data-ttu-id="911cd-154">A entidade pode conter duas propriedades:</span><span class="sxs-lookup"><span data-stu-id="911cd-154">The entity can contain two properties:</span></span><br><span data-ttu-id="911cd-155">O `country` campo contém o local detectado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="911cd-155">The `country` field contains the user's detected location.</span></span><br><span data-ttu-id="911cd-156">O `platform` campo descreve a plataforma de cliente de mensagens.</span><span class="sxs-lookup"><span data-stu-id="911cd-156">The `platform` field describes the messaging client platform.</span></span> <br><span data-ttu-id="911cd-157">Para obter informações adicionais, *consulte* Tipos de entidade [não IRI — clientInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).</span><span class="sxs-lookup"><span data-stu-id="911cd-157">For additional information, please *see* [Non-IRI entity types — clientInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).</span></span>|

<span data-ttu-id="911cd-158">Os parâmetros de solicitação em si são encontrados no objeto value, que inclui as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="911cd-158">The request parameters itself are found in the value object, which includes the following properties:</span></span>

| <span data-ttu-id="911cd-159">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="911cd-159">Property name</span></span> | <span data-ttu-id="911cd-160">Objetivo</span><span class="sxs-lookup"><span data-stu-id="911cd-160">Purpose</span></span> |
|---|---|
| `commandId` | <span data-ttu-id="911cd-161">O nome do comando invocado pelo usuário, correspondendo a um dos comandos declarados no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="911cd-161">The name of the command invoked by the user, matching one of the commands declared in the app manifest.</span></span> |
| `parameters` | <span data-ttu-id="911cd-162">Matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="911cd-162">Array of parameters.</span></span> <span data-ttu-id="911cd-163">Cada objeto de parâmetro contém o nome do parâmetro, juntamente com o valor do parâmetro fornecido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="911cd-163">Each parameter object contains the parameter name, along with the parameter value provided by the user.</span></span> |
| `queryOptions` | <span data-ttu-id="911cd-164">Parâmetros paginação:</span><span class="sxs-lookup"><span data-stu-id="911cd-164">Pagination parameters:</span></span> <br><span data-ttu-id="911cd-165">`skip`: ignorar a contagem dessa consulta</span><span class="sxs-lookup"><span data-stu-id="911cd-165">`skip`: skip count for this query</span></span> <br><span data-ttu-id="911cd-166">`count`: número de elementos a retornar</span><span class="sxs-lookup"><span data-stu-id="911cd-166">`count`: number of elements to return</span></span> |

#### <a name="request-example"></a><span data-ttu-id="911cd-167">Exemplo de solicitação</span><span class="sxs-lookup"><span data-stu-id="911cd-167">Request example</span></span>

```json
{
  "name": "composeExtension/query",
  "value": {
    "commandId": "searchCmd",
    "parameters": [
      {
        "name": "searchKeywords",
        "value": "Toronto"
      }
    ],
    "queryOptions": {
      "skip": 0,
      "count": 25
    }
  },
  "type": "invoke",
  "timestamp": "2017-05-01T15:45:51.876Z",
  "localTimestamp": "2017-05-01T08:45:51.876-07:00",
  "id": "f:622749630322482883",
  "channelId": "msteams",
  "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
  "from": {
    "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
    "name": "Larry Jin",
    "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
  },
  "conversation": {
    "id": "19:skypespaces_8198cfe0dd2647ae91930f0974768a40@thread.skype"
  },
  "recipient": {
    "id": "28:b4922ea1-5315-4fd0-9b21-d941ab06e39f",
    "name": "TheComposeExtensionDev"
  },
  "entities": [
    {
    "type": "clientInfo",
      "country": "US",
      "platform": "Windows"
    }
  ]
}
```

### <a name="receive-requests-from-links-inserted-into-the-compose-message-box"></a><span data-ttu-id="911cd-168">Receber solicitações de links inseridos na caixa de mensagem de redação</span><span class="sxs-lookup"><span data-stu-id="911cd-168">Receive requests from links inserted into the compose message box</span></span>

<span data-ttu-id="911cd-169">Como alternativa (ou além disso) à pesquisa do seu serviço externo, você pode usar uma URL inserida na caixa de mensagem de redação para consultar seu serviço e retornar um cartão.</span><span class="sxs-lookup"><span data-stu-id="911cd-169">As an alternative (or in addition) to searching your external service, you can use a URL inserted into the compose message box to query your service and return a card.</span></span> <span data-ttu-id="911cd-170">Na captura de tela abaixo, um usuário firmou uma URL para um item de trabalho no Azure DevOps que a extensão de mensagens resolveu em um cartão.</span><span class="sxs-lookup"><span data-stu-id="911cd-170">In the screenshot below a user has pasted in a URL for a work item in Azure DevOps which the messaging extension has resolved into a card.</span></span>

![Exemplo de desfraldamento de link](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

<span data-ttu-id="911cd-172">Para permitir que sua extensão de mensagens interaja com links dessa forma, primeiro você precisará adicionar a matriz ao manifesto do aplicativo, como `messageHandlers` no exemplo abaixo:</span><span class="sxs-lookup"><span data-stu-id="911cd-172">To enable your messaging extension to interact with links this way you'll first need to add the `messageHandlers` array to your app manifest as in the example below:</span></span>

```json
"composeExtensions": [
  {
    "botId": "abc123456-ab12-ab12-ab12-abcdef123456",
    "messageHandlers": [
      {
        "type": "link",
        "value": {
          "domains": [
            "*.trackeddomain.com"
          ]
        }
      }
    ]
  }
]
```

<span data-ttu-id="911cd-173">Depois de adicionar o domínio para ouvir o manifesto do aplicativo, você [](#respond-to-user-requests) precisará alterar seu código bot para responder à solicitação de invocação abaixo.</span><span class="sxs-lookup"><span data-stu-id="911cd-173">Once you've added the domain to listen on to the app manifest, you'll need to change your bot code to [respond](#respond-to-user-requests) to the below invoke request.</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

<span data-ttu-id="911cd-174">Se seu aplicativo retornar vários itens, apenas o primeiro será usado.</span><span class="sxs-lookup"><span data-stu-id="911cd-174">If your app returns multiple items only the first will be used.</span></span>

### <a name="respond-to-user-requests"></a><span data-ttu-id="911cd-175">Responder a solicitações de usuário</span><span class="sxs-lookup"><span data-stu-id="911cd-175">Respond to user requests</span></span>

<span data-ttu-id="911cd-176">Quando o usuário executa uma consulta, o Microsoft Teams emite uma solicitação HTTP síncrona ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="911cd-176">When the user performs a query, Microsoft Teams issues a synchronous HTTP request to your service.</span></span> <span data-ttu-id="911cd-177">Nesse ponto, seu código tem 5 segundos para fornecer uma resposta HTTP à solicitação.</span><span class="sxs-lookup"><span data-stu-id="911cd-177">At that point, your code has 5 seconds to provide an HTTP response to the request.</span></span> <span data-ttu-id="911cd-178">Durante esse tempo, seu serviço pode realizar uma consulta adicional ou qualquer outra lógica de negócios necessária para atender à solicitação.</span><span class="sxs-lookup"><span data-stu-id="911cd-178">During this time, your service can perform additional lookup, or any other business logic needed to serve the request.</span></span>

<span data-ttu-id="911cd-179">Seu serviço deve responder com os resultados correspondentes à consulta do usuário.</span><span class="sxs-lookup"><span data-stu-id="911cd-179">Your service should respond with the results matching the user query.</span></span> <span data-ttu-id="911cd-180">A resposta deve indicar um código de status HTTP e um `200 OK` objeto application/json válido com o seguinte corpo:</span><span class="sxs-lookup"><span data-stu-id="911cd-180">The response must indicate an HTTP status code of `200 OK` and a valid application/json object with the following body:</span></span>

|<span data-ttu-id="911cd-181">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="911cd-181">Property name</span></span>|<span data-ttu-id="911cd-182">Objetivo</span><span class="sxs-lookup"><span data-stu-id="911cd-182">Purpose</span></span>|
|---|---|
|`composeExtension`|<span data-ttu-id="911cd-183">Envelope de resposta de nível superior.</span><span class="sxs-lookup"><span data-stu-id="911cd-183">Top-level response envelope.</span></span>|
|`composeExtension.type`|<span data-ttu-id="911cd-184">Tipo de resposta.</span><span class="sxs-lookup"><span data-stu-id="911cd-184">Type of response.</span></span> <span data-ttu-id="911cd-185">Os seguintes tipos são suportados:</span><span class="sxs-lookup"><span data-stu-id="911cd-185">The following types are supported:</span></span> <br><span data-ttu-id="911cd-186">`result`: exibe uma lista de resultados da pesquisa</span><span class="sxs-lookup"><span data-stu-id="911cd-186">`result`: displays a list of search results</span></span> <br><span data-ttu-id="911cd-187">`auth`: pede ao usuário para autenticar</span><span class="sxs-lookup"><span data-stu-id="911cd-187">`auth`: asks the user to authenticate</span></span> <br><span data-ttu-id="911cd-188">`config`: pede ao usuário para configurar a extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="911cd-188">`config`: asks the user to set up the messaging extension</span></span> <br><span data-ttu-id="911cd-189">`message`: exibe uma mensagem de texto simples</span><span class="sxs-lookup"><span data-stu-id="911cd-189">`message`: displays a plain text message</span></span> |
|`composeExtension.attachmentLayout`|<span data-ttu-id="911cd-190">Especifica o layout dos anexos.</span><span class="sxs-lookup"><span data-stu-id="911cd-190">Specifies the layout of the attachments.</span></span> <span data-ttu-id="911cd-191">Usado para respostas do tipo `result` .</span><span class="sxs-lookup"><span data-stu-id="911cd-191">Used for responses of type `result`.</span></span> <br><span data-ttu-id="911cd-192">Atualmente, os seguintes tipos são suportados:</span><span class="sxs-lookup"><span data-stu-id="911cd-192">Currently the following types are supported:</span></span> <br><span data-ttu-id="911cd-193">`list`: uma lista de objetos de cartão que contêm campos de miniatura, título e texto</span><span class="sxs-lookup"><span data-stu-id="911cd-193">`list`: a list of card objects containing thumbnail, title, and text fields</span></span> <br><span data-ttu-id="911cd-194">`grid`: uma grade de imagens em miniatura</span><span class="sxs-lookup"><span data-stu-id="911cd-194">`grid`: a grid of thumbnail images</span></span> |
|`composeExtension.attachments`|<span data-ttu-id="911cd-195">Matriz de objetos de anexo válidos.</span><span class="sxs-lookup"><span data-stu-id="911cd-195">Array of valid attachment objects.</span></span> <span data-ttu-id="911cd-196">Usado para respostas do tipo `result` .</span><span class="sxs-lookup"><span data-stu-id="911cd-196">Used for responses of type `result`.</span></span> <br><span data-ttu-id="911cd-197">Atualmente, os seguintes tipos são suportados:</span><span class="sxs-lookup"><span data-stu-id="911cd-197">Currently the following types are supported:</span></span> <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|<span data-ttu-id="911cd-198">Ações sugeridas.</span><span class="sxs-lookup"><span data-stu-id="911cd-198">Suggested actions.</span></span> <span data-ttu-id="911cd-199">Usado para respostas de tipo `auth` ou `config` .</span><span class="sxs-lookup"><span data-stu-id="911cd-199">Used for responses of type `auth` or `config`.</span></span> |
|`composeExtension.text`|<span data-ttu-id="911cd-200">Mensagem a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="911cd-200">Message to display.</span></span> <span data-ttu-id="911cd-201">Usado para respostas do tipo `message` .</span><span class="sxs-lookup"><span data-stu-id="911cd-201">Used for responses of type `message`.</span></span> |

#### <a name="response-card-types-and-previews"></a><span data-ttu-id="911cd-202">Tipos de cartão de resposta e visualizações</span><span class="sxs-lookup"><span data-stu-id="911cd-202">Response card types and previews</span></span>

<span data-ttu-id="911cd-203">Suportamos os seguintes tipos de anexo:</span><span class="sxs-lookup"><span data-stu-id="911cd-203">We support the following attachment types:</span></span>

* [<span data-ttu-id="911cd-204">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="911cd-204">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="911cd-205">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="911cd-205">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="911cd-206">Cartão do Conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="911cd-206">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="911cd-207">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="911cd-207">Adaptive card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="911cd-208">Consulte [Cartões para](~/task-modules-and-cards/what-are-cards.md) uma visão geral.</span><span class="sxs-lookup"><span data-stu-id="911cd-208">See [Cards](~/task-modules-and-cards/what-are-cards.md) for an overview.</span></span>

<span data-ttu-id="911cd-209">Para saber como usar os tipos de miniatura e cartão de herói, consulte [Adicionar cartões e ações de cartão.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="911cd-209">To learn how to use the thumbnail and hero card types, see [Add cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

<span data-ttu-id="911cd-210">Para obter documentação adicional sobre o cartão conector do Office 365, consulte [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="911cd-210">For additional documentation regarding the Office 365 Connector card, see [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="911cd-211">A lista de resultados é exibida na interface do usuário do Microsoft Teams com uma visualização de cada item.</span><span class="sxs-lookup"><span data-stu-id="911cd-211">The result list is displayed in the Microsoft Teams UI with a preview of each item.</span></span> <span data-ttu-id="911cd-212">A visualização é gerada de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="911cd-212">The preview is generated in one of two ways:</span></span>

* <span data-ttu-id="911cd-213">Usando a `preview` propriedade dentro do `attachment` objeto.</span><span class="sxs-lookup"><span data-stu-id="911cd-213">Using the `preview` property within the `attachment` object.</span></span> <span data-ttu-id="911cd-214">O `preview` anexo só pode ser um cartão Hero ou Thumbnail.</span><span class="sxs-lookup"><span data-stu-id="911cd-214">The `preview` attachment can only be a Hero or Thumbnail card.</span></span>
* <span data-ttu-id="911cd-215">Extraído das propriedades `title` básicas `text` , e do `image` anexo.</span><span class="sxs-lookup"><span data-stu-id="911cd-215">Extracted from the basic `title`, `text`, and `image` properties of the attachment.</span></span> <span data-ttu-id="911cd-216">Eles são usados somente se `preview` a propriedade não estiver definida e essas propriedades estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="911cd-216">These are used only if the `preview` property is not set and these properties are available.</span></span>

<span data-ttu-id="911cd-217">Você pode exibir uma visualização de um cartão Adaptável ou conector do Office 365 na lista de resultados simplesmente definindo sua propriedade de visualização; isso não será necessário se os resultados já são cartões de miniatura ou herói.</span><span class="sxs-lookup"><span data-stu-id="911cd-217">You can display a preview of an Adaptive or Office 365 Connector card in the result list simply by setting its preview property; this is not necessary if the results are already hero or thumbnail cards.</span></span> <span data-ttu-id="911cd-218">Se você usar o anexo de visualização, ele deve ser um cartão Hero ou Thumbnail.</span><span class="sxs-lookup"><span data-stu-id="911cd-218">If you use the preview attachment, it must be either a Hero or Thumbnail card.</span></span> <span data-ttu-id="911cd-219">Se nenhuma propriedade de visualização for especificada, a visualização do cartão falhará e nada será exibido.</span><span class="sxs-lookup"><span data-stu-id="911cd-219">If no preview property is specified, the preview of the card will fail and nothing will be displayed.</span></span>

#### <a name="response-example"></a><span data-ttu-id="911cd-220">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="911cd-220">Response example</span></span>

<span data-ttu-id="911cd-221">Este exemplo mostra uma resposta com dois resultados, misturando diferentes formatos de cartão: Office 365 Connector e Adaptável.</span><span class="sxs-lookup"><span data-stu-id="911cd-221">This example shows a response with two results, mixing different card formats: Office 365 Connector and Adaptive.</span></span> <span data-ttu-id="911cd-222">Embora você provavelmente queira manter um formato de cartão em sua resposta, ele mostra como a propriedade de cada elemento na coleção deve definir explicitamente uma visualização no formato hero ou miniatura, conforme descrito `preview` `attachments` acima.</span><span class="sxs-lookup"><span data-stu-id="911cd-222">While you'll likely want to stick with one card format in your response, it shows how the `preview` property of each element in the `attachments` collection must explicitly define a preview in hero or thumbnail format as described above.</span></span>

```json
{
  "composeExtension": {
    "type": "result",
    "attachmentLayout": "list",
    "attachments": [
      {
        "contentType": "application/vnd.microsoft.teams.card.o365connector",
        "content": {
          "sections": [
            {
              "activityTitle": "[85069]: Create a cool app",
              "activityImage&quot;: &quot;https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value&quot;: &quot;[Larry Brown](mailto:larryb@example.com)"
                },
                {
                  "name": "State:",
                  "value": "Active"
                }
              ]
            }
          ]
        },
        "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "85069: Create a cool app",
            "images": [
              {
                "url": "https://placekitten.com/200/200"
              }
            ]
          }
        }
      },
      {
        "contentType": "application/vnd.microsoft.card.adaptive",
        "content": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Container",
              "items": [
                {
                  "type": "TextBlock",
                  "text": "Microsoft Corp (NASDAQ: MSFT)",
                  "size": "medium",
                  "isSubtle": true
                },
                {
                  "type": "TextBlock",
                  "text": "September 19, 4:00 PM EST",
                  "isSubtle": true
                }
              ]
            },
            {
              "type": "Container",
              "spacing": "none",
              "items": [
                {
                  "type": "ColumnSet",
                  "columns": [
                    {
                      "type": "Column",
                      "width": "stretch",
                      "items": [
                        {
                          "type": "TextBlock",
                          "text": "75.30",
                          "size": "extraLarge"
                        },
                        {
                          "type": "TextBlock",
                          "text": "▼ 0.20 (0.32%)",
                          "size": "small",
                          "color": "attention",
                          "spacing": "none"
                        }
                      ]
                    },
                    {
                      "type": "Column",
                      "width": "auto",
                      "items": [
                        {
                          "type": "FactSet",
                          "facts": [
                            {
                              "title": "Open",
                              "value": "62.24"
                            },
                            {
                              "title": "High",
                              "value": "62.98"
                            },
                            {
                              "title": "Low",
                              "value": "62.20"
                            }
                          ]
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          ],
          "version": "1.0"
        },
        "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "Microsoft Corp (NASDAQ: MSFT)",
            "text": "75.30 ▼ 0.20 (0.32%)"
          }
        }
      }
    ]
  }
}
```

### <a name="default-query"></a><span data-ttu-id="911cd-223">Consulta padrão</span><span class="sxs-lookup"><span data-stu-id="911cd-223">Default query</span></span>

<span data-ttu-id="911cd-224">Se você definir como no manifesto, o Microsoft Teams emite uma consulta "padrão" quando o usuário abre pela primeira vez a extensão `initialRun` `true` de mensagens.</span><span class="sxs-lookup"><span data-stu-id="911cd-224">If you set `initialRun` to `true` in the manifest, Microsoft Teams issues a "default" query when the user first opens the messaging extension.</span></span> <span data-ttu-id="911cd-225">Seu serviço pode responder a essa consulta com um conjunto de resultados pré-populados.</span><span class="sxs-lookup"><span data-stu-id="911cd-225">Your service can respond to this query with a set of prepopulated results.</span></span> <span data-ttu-id="911cd-226">Isso pode ser útil para exibir, por exemplo, itens exibidos recentemente, favoritos ou qualquer outra informação que não dependa da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="911cd-226">This can be useful for displaying, for instance, recently viewed items, favorites, or any other information that is not dependent on user input.</span></span>

<span data-ttu-id="911cd-227">A consulta padrão tem a mesma estrutura que qualquer consulta de usuário regular, exceto com um parâmetro cujo valor `initialRun` de cadeia de caracteres é `true` .</span><span class="sxs-lookup"><span data-stu-id="911cd-227">The default query has the same structure as any regular user query, except with a parameter `initialRun` whose string value is `true`.</span></span>

#### <a name="request-example-for-a-default-query"></a><span data-ttu-id="911cd-228">Exemplo de solicitação para uma consulta padrão</span><span class="sxs-lookup"><span data-stu-id="911cd-228">Request example for a default query</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/query",
  "value": {
    "commandId": "searchCmd",
    "parameters": [
      {
        "name": "initialRun",
        "value": "true"
      }
    ],
    "queryOptions": {
      "skip": 0,
      "count": 25
    }
  },
  ⋮
}
```

## <a name="identify-the-user"></a><span data-ttu-id="911cd-229">Identificar o usuário</span><span class="sxs-lookup"><span data-stu-id="911cd-229">Identify the user</span></span>

<span data-ttu-id="911cd-230">Todas as solicitações aos seus serviços incluem a ID ofuscada do usuário que realizou a solicitação, bem como o nome de exibição do usuário e a ID do objeto do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="911cd-230">Every request to your services includes the obfuscated ID of the user that performed the request, as well as the user's display name and Azure Active Directory object ID.</span></span>

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

<span data-ttu-id="911cd-231">Os `id` valores e são `aadObjectId` garantidos como os do usuário do Teams autenticado.</span><span class="sxs-lookup"><span data-stu-id="911cd-231">The `id` and `aadObjectId` values are guaranteed to be that of the authenticated Teams user.</span></span> <span data-ttu-id="911cd-232">Elas podem ser usadas como chaves para procurar credenciais ou qualquer estado armazenado em cache em seu serviço.</span><span class="sxs-lookup"><span data-stu-id="911cd-232">They can be used as keys to look up credentials or any cached state in your service.</span></span> <span data-ttu-id="911cd-233">Além disso, cada solicitação contém a ID de locatário do Azure Active Directory do usuário, que pode ser usada para identificar a organização do usuário.</span><span class="sxs-lookup"><span data-stu-id="911cd-233">In addition, each request contains the Azure Active Directory tenant ID of the user, which can be used to identify the user’s organization.</span></span> <span data-ttu-id="911cd-234">Se aplicável, a solicitação também contém as IDs de equipe e canal das quais a solicitação se originou.</span><span class="sxs-lookup"><span data-stu-id="911cd-234">If applicable, the request also contains the team and channel IDs from which the request originated.</span></span>

## <a name="authentication"></a><span data-ttu-id="911cd-235">Autenticação</span><span class="sxs-lookup"><span data-stu-id="911cd-235">Authentication</span></span>

<span data-ttu-id="911cd-236">Se o serviço exigir autenticação do usuário, você precisará entrar no usuário antes que ele possa usar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="911cd-236">If your service requires user authentication, you need to sign in the user before he or she can use the messaging extension.</span></span> <span data-ttu-id="911cd-237">Se você tiver escrito um bot ou uma guia que assina no usuário, esta seção deve ser familiar.</span><span class="sxs-lookup"><span data-stu-id="911cd-237">If you have written a bot or a tab that signs in the user, this section should be familiar.</span></span>

<span data-ttu-id="911cd-238">A sequência é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="911cd-238">The sequence is as follows:</span></span>

1. <span data-ttu-id="911cd-239">O usuário emite uma consulta ou a consulta padrão é enviada automaticamente ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="911cd-239">User issues a query, or the default query is automatically sent to your service.</span></span>
2. <span data-ttu-id="911cd-240">Seu serviço verifica se o usuário foi autenticado pela primeira vez inspecionando a ID do usuário do Teams.</span><span class="sxs-lookup"><span data-stu-id="911cd-240">Your service checks whether the user has first authenticated by inspecting the Teams user ID.</span></span>
3. <span data-ttu-id="911cd-241">Se o usuário não tiver sido autenticado, envie uma `auth` resposta com uma ação `openUrl` sugerida, incluindo a URL de autenticação.</span><span class="sxs-lookup"><span data-stu-id="911cd-241">If the user has not authenticated, send back an `auth` response with an `openUrl` suggested action including the authentication URL.</span></span>
4. <span data-ttu-id="911cd-242">O cliente do Microsoft Teams inicia uma janela pop-up hospedando sua página da Web usando a URL de autenticação determinada.</span><span class="sxs-lookup"><span data-stu-id="911cd-242">The Microsoft Teams client launches a pop-up window hosting your webpage using the given authentication URL.</span></span>
5. <span data-ttu-id="911cd-243">Depois que o usuário entrar, feche a janela e envie um "código de autenticação" para o cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="911cd-243">After the user signs in, you should close your window and send an "authentication code" to the Teams client.</span></span>
6. <span data-ttu-id="911cd-244">Em seguida, o cliente do Teams reenvia a consulta ao seu serviço, que inclui o código de autenticação passado na etapa 5.</span><span class="sxs-lookup"><span data-stu-id="911cd-244">The Teams client then reissues the query to your service, which includes the authentication code passed in step 5.</span></span>

<span data-ttu-id="911cd-245">Seu serviço deve verificar se o código de autenticação recebido na etapa 6 corresponde ao da etapa 5.</span><span class="sxs-lookup"><span data-stu-id="911cd-245">Your service should verify that the authentication code received in step 6 matches the one from step 5.</span></span> <span data-ttu-id="911cd-246">Isso garante que um usuário mal-intencionado não tente fazer a spoof ou comprometer o fluxo de login.</span><span class="sxs-lookup"><span data-stu-id="911cd-246">This ensures that a malicious user does not try to spoof or compromise the sign-in flow.</span></span> <span data-ttu-id="911cd-247">Isso efetivamente "fecha o loop" para concluir a sequência de autenticação segura.</span><span class="sxs-lookup"><span data-stu-id="911cd-247">This effectively "closes the loop" to finish the secure authentication sequence.</span></span>

### <a name="respond-with-a-sign-in-action"></a><span data-ttu-id="911cd-248">Responder com uma ação de login</span><span class="sxs-lookup"><span data-stu-id="911cd-248">Respond with a sign-in action</span></span>

<span data-ttu-id="911cd-249">Para solicitar que um usuário não autenticado entre, responda com uma ação sugerida do tipo que inclui a `openUrl` URL de autenticação.</span><span class="sxs-lookup"><span data-stu-id="911cd-249">To prompt an unauthenticated user to sign in, respond with a suggested action of type `openUrl` that includes the authentication URL.</span></span>

#### <a name="response-example-for-a-sign-in-action"></a><span data-ttu-id="911cd-250">Exemplo de resposta para uma ação de login</span><span class="sxs-lookup"><span data-stu-id="911cd-250">Response example for a sign-in action</span></span>

```json
{
  "composeExtension":{
    "type":"auth",
    "suggestedActions":{
      "actions":[
        {
          "type": "openUrl",
          "value": "https://example.com/auth",
          "title": "Sign in to this app"
        }
      ]
    }
  }
}
```

> [!NOTE]
> <span data-ttu-id="911cd-251">Para que a experiência de login seja hospedada em um pop-up do Teams, a parte de domínio da URL deve estar na lista de domínios válidos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="911cd-251">For the sign-in experience to be hosted in a Teams pop-up, the domain portion of the URL must be in your app’s list of valid domains.</span></span> <span data-ttu-id="911cd-252">(Consulte [validDomains](~/resources/schema/manifest-schema.md#validdomains) no esquema de manifesto.)</span><span class="sxs-lookup"><span data-stu-id="911cd-252">(See [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema.)</span></span>

### <a name="start-the-sign-in-flow"></a><span data-ttu-id="911cd-253">Iniciar o fluxo de login</span><span class="sxs-lookup"><span data-stu-id="911cd-253">Start the sign-in flow</span></span>

<span data-ttu-id="911cd-254">Sua experiência de login deve ser responsiva e adequada dentro de uma janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="911cd-254">Your sign-in experience should be responsive and fit within a popup window.</span></span> <span data-ttu-id="911cd-255">Ele deve se integrar ao [SDK do cliente JavaScript do Microsoft Teams,](/javascript/api/overview/msteams-client)que usa a passagem de mensagens.</span><span class="sxs-lookup"><span data-stu-id="911cd-255">It should integrate with the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client), which uses message passing.</span></span>

<span data-ttu-id="911cd-256">Assim como com outras experiências incorporadas em execução no Microsoft Teams, seu código dentro da janela precisa chamar primeiro `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="911cd-256">As with other embedded experiences running inside Microsoft Teams, your code inside the window needs to first call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="911cd-257">Se seu código executar um fluxo OAuth, você poderá passar a ID do usuário do Teams para sua janela, que poderá passá-lo para a URL de entrada do OAuth.</span><span class="sxs-lookup"><span data-stu-id="911cd-257">If your code performs an OAuth flow, you can pass the Teams user ID into your window, which then can pass it to the OAuth sign-in URL.</span></span>

### <a name="complete-the-sign-in-flow"></a><span data-ttu-id="911cd-258">Concluir o fluxo de login</span><span class="sxs-lookup"><span data-stu-id="911cd-258">Complete the sign-in flow</span></span>

<span data-ttu-id="911cd-259">Quando a solicitação de login for concluída e redirecionar para sua página, ela deverá executar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="911cd-259">When the sign-in request completes and redirects back to your page, it should perform the following steps:</span></span>

1. <span data-ttu-id="911cd-260">Gere um código de segurança.</span><span class="sxs-lookup"><span data-stu-id="911cd-260">Generate a security code.</span></span> <span data-ttu-id="911cd-261">(Pode ser um número aleatório.) Você precisa armazenar em cache esse código em seu serviço, juntamente com as credenciais obtidas por meio do fluxo de logon (como tokens OAuth 2.0).</span><span class="sxs-lookup"><span data-stu-id="911cd-261">(This can be a random number.) You need to cache this code on your service, along with the credentials obtained through the sign-in flow (such as OAuth 2.0 tokens).</span></span>
2. <span data-ttu-id="911cd-262">Chame `microsoftTeams.authentication.notifySuccess` e passe o código de segurança.</span><span class="sxs-lookup"><span data-stu-id="911cd-262">Call `microsoftTeams.authentication.notifySuccess` and pass the security code.</span></span>

<span data-ttu-id="911cd-263">Neste ponto, a janela fecha e o controle é passado para o cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="911cd-263">At this point, the window closes and control is passed to the Teams client.</span></span> <span data-ttu-id="911cd-264">O cliente agora pode reeditar a consulta de usuário original, juntamente com o código de segurança na `state` propriedade.</span><span class="sxs-lookup"><span data-stu-id="911cd-264">The client now can reissue the original user query, along with the security code in the `state` property.</span></span> <span data-ttu-id="911cd-265">Seu código pode usar o código de segurança para procurar as credenciais armazenadas anteriormente para concluir a sequência de autenticação e concluir a solicitação do usuário.</span><span class="sxs-lookup"><span data-stu-id="911cd-265">Your code can use the security code to look up the credentials stored earlier to complete the authentication sequence and then complete the user request.</span></span>

#### <a name="reissued-request-example"></a><span data-ttu-id="911cd-266">Exemplo de solicitação reemissão</span><span class="sxs-lookup"><span data-stu-id="911cd-266">Reissued request example</span></span>

```json
{
    "name": "composeExtension/query",
    "value": {
        "commandId": "insertWiki",
        "parameters": [{
            "name": "searchKeyword",
            "value": "lakers"
        }],
        "state": "12345",
        "queryOptions": {
            "skip": 0,
            "count": 25
        }
    },
    "type": "invoke",
    "timestamp": "2017-04-26T05:18:25.629Z",
    "localTimestamp": "2017-04-25T22:18:25.629-07:00",
    "entities": [{
        "type": "clientInfo",
        "country": "US",
        "platform": "Web",
        
    }],
    "text": "",
    "attachments": [],
    "address": {
        "id": "f:7638210432489287768",
        "channelId": "msteams",
        "user": {
            "id": "29:1A5TJWHkbOwSyu_L9Ktk9QFI1d_kBOEPeNEeO1INscpKHzHTvWfiau5AX_6y3SuiOby-r73dzHJ17HipUWqGPgw",
            "aadObjectId": "fc8ca1c0-d043-4af6-b09f-141536207403"
        },
        "conversation": {
            "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
        },
        "bot": {
            "id": "28:c073afa8-7e77-4f92-b3e7-aa589e952a3e",
            "name": "maotestbot2"
        },
        "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
        "useAuth": true
    },
    "source": "msteams"
}
```

## <a name="sdk-support"></a><span data-ttu-id="911cd-267">Suporte ao SDK</span><span class="sxs-lookup"><span data-stu-id="911cd-267">SDK support</span></span>

### <a name="net"></a><span data-ttu-id="911cd-268">.NET</span><span class="sxs-lookup"><span data-stu-id="911cd-268">.NET</span></span>

<span data-ttu-id="911cd-269">Para receber e manipular consultas com o SDK do Construtor de Bots para .NET, você pode verificar o tipo de ação na atividade de entrada e usar o método auxiliar no pacote `invoke` NuGet [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) para determinar se é uma atividade de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="911cd-269">To receive and handle queries with the Bot Builder SDK for .NET, you can check for the `invoke` action type on the incoming activity and then use the helper method in the NuGet package [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) to determine whether it’s a messaging extension activity.</span></span>

#### <a name="example-code-in-net"></a><span data-ttu-id="911cd-270">Exemplo de código no .NET</span><span class="sxs-lookup"><span data-stu-id="911cd-270">Example code in .NET</span></span>

```csharp
public async Task<HttpResponseMessage> Post([FromBody]Activity activity)
{
    if (activity.Type == ActivityTypes.Invoke) // Received an invoke
    {
        if (activity.IsComposeExtensionQuery())
        {
            // This is the response object that will get sent back to the messaging extension request.
            ComposeExtensionResponse invokeResponse = null;

            // This helper method gets the query as an object.
            var query = activity.GetComposeExtensionQueryData();

            if (query.CommandId != null && query.Parameters != null && query.Parameters.Count > 0)
            {
                // query.Parameters has the parameters sent by client
                var results = new ComposeExtensionResult()
                {
                    AttachmentLayout = "list",
                    Type = "result",
                    Attachments = new List<ComposeExtensionAttachment>(),
                };
                invokeResponse.ComposeExtension = results;
            }

            // Return the response
            return Request.CreateResponse<ComposeExtensionResponse>(HttpStatusCode.OK, invokeResponse);
        } else
        {
            // Handle other types of Invoke activities here.
        }
    } else {
      // Failure case catch-all.
      var response = Request.CreateResponse(HttpStatusCode.BadRequest);
      response.Content = new StringContent("Invalid request! This API supports only messaging extension requests. Check your query and try again");
      return response;
    }
}
```

### <a name="nodejs"></a><span data-ttu-id="911cd-271">Node.js</span><span class="sxs-lookup"><span data-stu-id="911cd-271">Node.js</span></span>

#### <a name="example-code-in-nodejs"></a><span data-ttu-id="911cd-272">Exemplo de código no Node.js</span><span class="sxs-lookup"><span data-stu-id="911cd-272">Example code in Node.js</span></span>

```javascript
require('dotenv').config();

import * as restify from 'restify';
import * as builder from 'botbuilder';
import * as teamBuilder from 'botbuilder-teams';

class App {
    run() {
        const server = restify.createServer();
        let teamChatConnector = new teamBuilder.TeamsChatConnector({
            appId: process.env.MICROSOFT_APP_ID,
            appPassword: process.env.MICROSOFT_APP_PASSWORD
        });

        // Command ID must match what's defined in manifest
        teamChatConnector.onQuery('<%= commandId %>',
            (event: builder.IEvent,
            query: teamBuilder.ComposeExtensionQuery,
            callback: (err: Error, result: teamBuilder.IComposeExtensionResponse, statusCode: number) => void) => {
                // Check for initialRun; i.e., when you should return default results
                // if (query.parameters[0].name === 'initialRun') {}

                // Check query.queryOptions.count and query.queryOptions.skip for paging

                // Return auth response
                // let response = teamBuilder.ComposeExtensionResponse.auth().actions([
                //     builder.CardAction.openUrl(null, 'https://authUrl', 'Please sign in')
                // ]).toResponse();

                // Return config response
                // let response = teamBuilder.ComposeExtensionResponse.config().actions([
                //     builder.CardAction.openUrl(null, 'https://configUrl', 'Please sign in')
                // ]).toResponse();

                // Return result response
                let response = teamBuilder.ComposeExtensionResponse.result('list').attachments([
                    new builder.ThumbnailCard()
                        .title('Test thumbnail card')
                        .text('This is a test thumbnail card')
                        .images([new builder.CardImage().url('https://bot-framework.azureedge.net/bot-icons-v1/bot-framework-default-9.png')])
                        .toAttachment()
                ]).toResponse();
                callback(null, response, 200);
            });
        server.post('/api/composeExtension', teamChatConnector.listen());
        server.listen(process.env.PORT, () => console.log(`listening to port:` + process.env.PORT));
    }
}

const app = new App();
app.run();
```
<span data-ttu-id="911cd-273">*Consulte também Exemplos* [da Estrutura de Bot.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)</span><span class="sxs-lookup"><span data-stu-id="911cd-273">*See also* [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>
