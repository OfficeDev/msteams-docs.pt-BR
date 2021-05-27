---
title: Criar guias de cartão adaptáveis
author: KirtiPereira
description: Criar guias usando Cartões Adaptáveis
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: d65fc537b5282c050d891a6a73ff114c630e2c1c
ms.sourcegitcommit: c59d90ae03eae32996db49f162855965b55c52fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2021
ms.locfileid: "52668845"
---
# <a name="build-tabs-with-adaptive-cards"></a><span data-ttu-id="aaf1d-103">Criar guias com Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="aaf1d-103">Build tabs with Adaptive Cards</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="aaf1d-104">Esse recurso está na [Visualização do Desenvolvedor Público](~/resources/dev-preview/developer-preview-intro.md) e tem suporte na área de trabalho e em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-104">This feature is in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) and is supported in desktop and mobile.</span></span> <span data-ttu-id="aaf1d-105">O suporte no navegador da Web está chegando em breve.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-105">Support in the web browser is coming soon.</span></span>
> * <span data-ttu-id="aaf1d-106">Atualmente, as guias com Cartões Adaptáveis têm suporte apenas como aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-106">Tabs with Adaptive Cards are currently only supported as personal apps.</span></span>

<span data-ttu-id="aaf1d-107">Use Cartões Adaptáveis para criar guias com facilidade.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-107">Use Adaptive Cards to build tabs with ease.</span></span> <span data-ttu-id="aaf1d-108">Você pode criar suas guias com blocos de IU da Interface do Usuário prontos que pareçam nativos na área de trabalho, na Web e no celular.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-108">You can build your tabs with ready-made UI Lego-blocks that look and feel native on desktop, web, and mobile.</span></span> <span data-ttu-id="aaf1d-109">A criação de guias com Cartões Adaptáveis centraliza todos os recursos do aplicativo Teams em torno de um back-end de bot e front-end cartão adaptável, eliminando a necessidade de um back-back diferente para seu bot e guias.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-109">Building tabs with Adaptive Cards centralizes all Teams app capabilities around a bot backend and Adaptive Card frontend, thus, eliminating the need for a different backend for your bot and tabs.</span></span> <span data-ttu-id="aaf1d-110">Isso reduz consideravelmente os custos de servidor e manutenção do seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-110">This greatly reduces server and maintenance costs of your Teams app.</span></span> <span data-ttu-id="aaf1d-111">Este artigo ajuda você a entender as alterações necessárias para serem feitas no manifesto do aplicativo, como as solicitações de atividade de invocação e envia informações na guia com Cartões Adaptáveis e o impacto no fluxo de trabalho do módulo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-111">This article helps you understand the changes required to be made to the app manifest, how the invoke activity requests and sends information in tab with Adaptive Cards, and the impact on the task module workflow.</span></span> 

A imagem a seguir mostra guias de com build com Cartões Adaptáveis na área de trabalho e no celular: :::image type="content" source="../../assets/images/tabs/adaptive-cards-rendered-in-tabs.jpg" alt-text="Exemplo de Cartão Adaptável renderizado em guias." border="false":::

## <a name="prerequisites"></a><span data-ttu-id="aaf1d-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="aaf1d-113">Prerequisites</span></span>

<span data-ttu-id="aaf1d-114">Antes de começar a usar Cartões Adaptáveis para criar guias, você deve:</span><span class="sxs-lookup"><span data-stu-id="aaf1d-114">Before you start using Adaptive Cards to build tabs, you must:</span></span>

* <span data-ttu-id="aaf1d-115">Familiarizar-se com o desenvolvimento [de bots,](../../bots/what-are-bots.md)cartões [adaptáveis](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)e [módulos de tarefa](../../task-modules-and-cards/task-modules/task-modules-bots.md) no Teams.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-115">Be familiar with, [bot development](../../bots/what-are-bots.md), [Adaptive Cards](../../task-modules-and-cards/what-are-cards.md#adaptive-cards), and [Task Modules](../../task-modules-and-cards/task-modules/task-modules-bots.md) in Teams.</span></span>
* <span data-ttu-id="aaf1d-116">Tenha um bot em execução Teams seu desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-116">Have a bot running in Teams for your development.</span></span>
* <span data-ttu-id="aaf1d-117">Estar em [Visualização de Desenvolvedor Público](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="aaf1d-117">Be in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

## <a name="changes-to-app-manifest"></a><span data-ttu-id="aaf1d-118">Alterações no manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="aaf1d-118">Changes to app manifest</span></span>

<span data-ttu-id="aaf1d-119">Aplicativos pessoais que renderizar guias devem incluir uma `staticTabs` matriz no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-119">Personal apps that render tabs must include a `staticTabs` array in their app manifest.</span></span> <span data-ttu-id="aaf1d-120">A Guia cartão adaptável é renderizada quando `contentBotId` a propriedade é fornecida na `staticTab` definição.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-120">Adaptive Card Tab are rendered when the `contentBotId` property is provided in the `staticTab` definition.</span></span> <span data-ttu-id="aaf1d-121">As definições de tabulação estáticas devem conter uma , especificando uma Guia de Cartão Adaptável ou uma , especificando uma experiência típica de guia de `contentBotId` `contentUrl` conteúdo da Web hospedado.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-121">Static tab definitions must contain either a `contentBotId`, specifying an Adaptive Card Tab or a `contentUrl`, specifying a typical hosted web content tab experience.</span></span>

> [!NOTE]
> <span data-ttu-id="aaf1d-122">A `contentBotId` propriedade está disponível no momento versão 1.9 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-122">The `contentBotId` property is currently available manifest version 1.9 or later.</span></span> 

<span data-ttu-id="aaf1d-123">Forneça a propriedade com a guia cartão adaptável com a que `contentBotId` `botId` deve se comunicar.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-123">Provide the `contentBotId` property with the `botId` that the Adaptive Card Tab must communicate with.</span></span> <span data-ttu-id="aaf1d-124">A configuração para a Guia Cartão Adaptável é enviada no parâmetro de cada solicitação de invocação e pode ser usada para diferenciar diferentes Guias de Cartão Adaptável que são alimentadas pelo `entityId` `tabContext` mesmo bot.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-124">The `entityId` configured for the Adaptive Card Tab is sent in the `tabContext` parameter of each invoke request, and can be used to differentiate different Adaptive Card Tabs that are powered by the same bot.</span></span> <span data-ttu-id="aaf1d-125">Para obter mais informações sobre outros campos de definição de tabulação estática, consulte [esquema de manifesto](../../resources/schema/manifest-schema.md#statictabs).</span><span class="sxs-lookup"><span data-stu-id="aaf1d-125">For more information about other static tab definition fields, see [manifest schema](../../resources/schema/manifest-schema.md#statictabs).</span></span>

<span data-ttu-id="aaf1d-126">A seguir está um manifesto de guia de cartão adaptável de exemplo:</span><span class="sxs-lookup"><span data-stu-id="aaf1d-126">Following is a sample Adaptive Card Tab manifest:</span></span>

```json
{
  "$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
  "manifestVersion": "1.9",
  "id": "00000000-0000-0000-0000-000000000000",
  "version": "0.0.1",
  "packageName": "acprototype",
  "developer": {
    "name": "Contoso",
    "websiteUrl": "https://contoso.yourwebsite.com",
    "privacyUrl": "https://contoso.yourwebsite.com/privacy.html",
    "termsOfUseUrl": "https://contoso.yourwebsite.com/terms.html"
  },
  "name": {
    "short": "Contoso",
    "full": "Contoso Home"
  },
  "description": {
    "short": "Add short description here",
    "full": "Add full description here"
  },
  "icons": {
    "outline": "icon-outline.png",
    "color": "icon-color.png"
  },
  "accentColor": "#D85028",
  "configurableTabs": [],
  "staticTabs": [
    {
      "entityId": "homeTab",
      "name": "Home",
      "contentBotId": "00000000-0000-0000-0000-000000000000",
      "scopes": ["personal"]
    },
    {
      "entityId": "moreTab",
      "name": "More",
      "contentBotId": "00000000-0000-0000-0000-000000000000",
      "scopes": ["personal"]
    }
  ],
  "connectors": [],
  "composeExtensions": [],
  "permissions": ["identity", "messageTeamMembers"],
  "validDomains": [
    "contoso.yourwebsite.com",
    "token.botframework.com"
  ]
}
```

## <a name="invoke-activities"></a><span data-ttu-id="aaf1d-127">Invocar atividades</span><span class="sxs-lookup"><span data-stu-id="aaf1d-127">Invoke activities</span></span>

<span data-ttu-id="aaf1d-128">A comunicação entre a guia Cartão Adaptável e o bot é feita por meio de `invoke` atividades.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-128">Communication between your Adaptive Card Tab and your bot is done through `invoke` activities.</span></span> <span data-ttu-id="aaf1d-129">Cada `invoke` atividade tem um nome *correspondente*.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-129">Each `invoke` activity has a corresponding *name*.</span></span> <span data-ttu-id="aaf1d-130">Use o nome de cada atividade para diferenciar cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-130">Use the name of each activity to differentiate each request.</span></span> <span data-ttu-id="aaf1d-131">`tab/fetch` e `tab/submit` são as atividades abordadas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-131">`tab/fetch` and `tab/submit` are the activities covered in this section.</span></span>

### <a name="fetch-adaptive-card-to-render-to-a-tab"></a><span data-ttu-id="aaf1d-132">Buscar Cartão Adaptável para renderizar em uma guia</span><span class="sxs-lookup"><span data-stu-id="aaf1d-132">Fetch Adaptive Card to render to a tab</span></span>

<span data-ttu-id="aaf1d-133">`tab/fetch` é a primeira solicitação de invocação que seu bot recebe quando um usuário abre uma Guia de Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-133">`tab/fetch` is the first invoke request that your bot receives when a user opens an Adaptive Card Tabs.</span></span> <span data-ttu-id="aaf1d-134">Quando o bot receber a solicitação,  ele enviará uma resposta de continuação de tabulação ou uma **resposta de tabulação.**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-134">When your bot receives the request, it will either send a tab **continue** response or a tab **auth** response.</span></span>
<span data-ttu-id="aaf1d-135">A **resposta continue** inclui uma matriz para **cartões**, que é renderizada verticalmente para a guia na ordem da matriz.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-135">The **continue** response includes an array for **cards**, which is rendered vertically to the tab in the order of the array.</span></span>

> [!NOTE]
> <span data-ttu-id="aaf1d-136">A **resposta de autenticação** é explicada em detalhes na [seção autenticação.](#authentication)</span><span class="sxs-lookup"><span data-stu-id="aaf1d-136">The **auth** response is explained in detail in the [authentication](#authentication) section.</span></span>

<span data-ttu-id="aaf1d-137">Os seguintes trechos de código são exemplos de `tab/fetch` solicitação e resposta:</span><span class="sxs-lookup"><span data-stu-id="aaf1d-137">The following code snippets are examples of `tab/fetch` request and response:</span></span>

<span data-ttu-id="aaf1d-138">**`tab/fetch` request**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-138">**`tab/fetch` request**</span></span>

```json
// tab/fetch POST request: agents/{botId}/invoke
{
    "name": "tab/fetch",
    "value: {
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
        },
        "context": {
            "theme": "default"
            }
    },
    "conversation": {
        "id": "{generated_conversation_id}"
    },
    "imdisplayname": "{user_display_name}"
}
```

<span data-ttu-id="aaf1d-139">**`tab/fetch` response**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-139">**`tab/fetch` response**</span></span>

```json
// tab/fetch **continue** POST response:
{
    "tab": {
        "type": "continue",
        "value": {
            "cards": [
                {
                    "card": adaptiveCard1,
                },
                {
                    "card": adaptiveCard2,
                }
                {
                    "card": adaptiveCard3
                }  
            ]
        },
    },
    "responseType": "tab"
}
```

### <a name="handle-submits-from-adaptive-card"></a><span data-ttu-id="aaf1d-140">Manipular envios do Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="aaf1d-140">Handle submits from Adaptive Card</span></span>

<span data-ttu-id="aaf1d-141">Depois que um Cartão Adaptável é renderizado na guia, ele deve ser capaz de responder às interações do usuário.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-141">After an Adaptive Card is rendered in the tab, it must be able to respond to user interactions.</span></span> <span data-ttu-id="aaf1d-142">Essa resposta é manipulada pela `tab/submit` solicitação de invocação.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-142">This response is handled by the `tab/submit` invoke request.</span></span>

<span data-ttu-id="aaf1d-143">Quando um usuário seleciona um botão na guia Cartão Adaptável, a solicitação é disparada para o bot com os dados correspondentes por meio da `tab/submit` *função Action.Submit* do Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-143">When a user selects a button on the Adaptive Card Tab, the `tab/submit` request is triggered to your bot with the corresponding data through the *Action.Submit* function of Adaptive Card.</span></span> <span data-ttu-id="aaf1d-144">Os dados do Cartão Adaptável estão disponíveis por meio da propriedade data da `tab/submit` solicitação.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-144">The Adaptive Card data is available through the data property of the `tab/submit` request.</span></span> <span data-ttu-id="aaf1d-145">Você receberá uma das seguintes respostas à sua solicitação:</span><span class="sxs-lookup"><span data-stu-id="aaf1d-145">You will receive either of the following responses to your request:</span></span>

* <span data-ttu-id="aaf1d-146">Uma resposta de código de status http `200` sem corpo.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-146">A http status code `200` response with no body.</span></span> <span data-ttu-id="aaf1d-147">Uma resposta 200 vazia não resultará em nenhuma ação tomada pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-147">An empty 200 response will result in no action taken by the client.</span></span>
* <span data-ttu-id="aaf1d-148">A guia `200` padrão **continua** a resposta, conforme explicado na seção Buscar [Cartão Adaptável.](#fetch-adaptive-card-to-render-to-a-tab)</span><span class="sxs-lookup"><span data-stu-id="aaf1d-148">The standard `200` tab **continue** response, as explained in [Fetch Adaptive Card](#fetch-adaptive-card-to-render-to-a-tab) section.</span></span> <span data-ttu-id="aaf1d-149">Uma resposta **de continuação** de tabulação dispara o cliente para atualizar a Guia cartão adaptável renderizado com os Cartões Adaptáveis fornecidos na matriz de cartões da **resposta continuar.**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-149">A tab **continue** response triggers the client to update the rendered Adaptive Card Tab with the Adaptive Cards provided in the cards array of the **continue** response.</span></span>

<span data-ttu-id="aaf1d-150">Os seguintes trechos de código são exemplos de `tab/submit` solicitação e resposta:</span><span class="sxs-lookup"><span data-stu-id="aaf1d-150">The following code snippets are examples of `tab/submit` request and response:</span></span>

<span data-ttu-id="aaf1d-151">**`tab/submit` request**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-151">**`tab/submit` request**</span></span>

```json
// tab/submit POST request: agents/{botId}/invoke:
{
    "name": "tab/submit",
    "value": {
        "data": {
            "type": "tab/submit",
            //...<data properties>
            },
        "context": {
            "theme": "default"
            },
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
            },
        },
    "conversation": {
           "id": "{generated_conversation_id}" 
        },
    "imdisplayname": "{user_display_name}"
}
```

<span data-ttu-id="aaf1d-152">**`tab/submit` response**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-152">**`tab/submit` response**</span></span>

```json
//tab/fetch **continue** POST response:
{
    "tab": {
        "type": "continue",
        "value": {
            "cards": [
              {
                "card": adaptiveCard1,
                },
              {
                "card": adaptiveCard2,
                } 
            ]
        },
    },
    "responseType": "tab"
}
```

## <a name="understand-task-module-workflow"></a><span data-ttu-id="aaf1d-153">Entender o fluxo de trabalho do módulo de tarefas</span><span class="sxs-lookup"><span data-stu-id="aaf1d-153">Understand task module workflow</span></span>

<span data-ttu-id="aaf1d-154">O módulo de tarefa também usa Cartão Adaptável para invocar `task/fetch` e `task/submit` solicitações e respostas.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-154">The task module also uses Adaptive Card to invoke `task/fetch` and `task/submit` requests and responses.</span></span> <span data-ttu-id="aaf1d-155">Para obter mais informações, consulte [Using Task Modules in Microsoft Teams bots](../../task-modules-and-cards/task-modules/task-modules-bots.md).</span><span class="sxs-lookup"><span data-stu-id="aaf1d-155">For more information, see [Using Task Modules in Microsoft Teams bots](../../task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="aaf1d-156">No entanto, com a introdução da Guia Cartão Adaptável, há uma alteração na forma como o bot responde a uma `task/submit` solicitação.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-156">However, with the introduction of Adaptive Card Tab there is a change in how the bot responds to a `task/submit` request.</span></span> <span data-ttu-id="aaf1d-157">Se você estiver usando uma guia Cartão Adaptável, o bot responderá à solicitação de invocação com a guia padrão continuar a resposta e `task/submit` fechará o módulo de tarefa. </span><span class="sxs-lookup"><span data-stu-id="aaf1d-157">If you are using an Adaptive Card Tab, the bot responds to the `task/submit` invoke request with the standard tab **continue** response, and closes the task module.</span></span> <span data-ttu-id="aaf1d-158">A Guia Cartão Adaptável é atualizada renderizando a nova lista de cartões fornecidos na guia continuar **o** corpo da resposta.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-158">The Adaptive Card Tab is updated by rendering the new list of cards provided in the tab **continue** response body.</span></span>

### <a name="invoke-taskfetch"></a><span data-ttu-id="aaf1d-159">Invocar `task/fetch`</span><span class="sxs-lookup"><span data-stu-id="aaf1d-159">Invoke `task/fetch`</span></span>

<span data-ttu-id="aaf1d-160">Os seguintes trechos de código são exemplos de `task/fetch` solicitação e resposta:</span><span class="sxs-lookup"><span data-stu-id="aaf1d-160">The following code snippets are examples of `task/fetch` request and response:</span></span>

<span data-ttu-id="aaf1d-161">**`task/fetch` request**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-161">**`task/fetch` request**</span></span>
```json
// task/fetch POST request: agents/{botId}/invoke
{
    "name": "task/fetch",
    "value": {
        "data": {
            "type": "task/fetch"
        },
        "context": {
            "theme": "default",
        },
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
        }
    },
    "imdisplayname": "{user_display_name}",
    "conversation": {
        "id": "{generated_conversation_id}"
    } 
}
```

<span data-ttu-id="aaf1d-162">**`task/fetch` response**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-162">**`task/fetch` response**</span></span>

```json
// task/fetch POST response: agents/{botId}/invoke
{
    "task": {
        "value": {
            "title": "Ninja Cat",
            "height": "small",
            "width": "small",
            "card": {
                "contentType": "application/vnd.microsoft.card.adaptive",
                "content": adaptiveCard,
            }
        },
    "type": "continue"
    },
    "responseType": "task"
}
```

### <a name="invoke-tasksubmit"></a><span data-ttu-id="aaf1d-163">Invocar `task/submit`</span><span class="sxs-lookup"><span data-stu-id="aaf1d-163">Invoke `task/submit`</span></span>

<span data-ttu-id="aaf1d-164">Os seguintes trechos de código são exemplos de `task/submit` solicitação e resposta:</span><span class="sxs-lookup"><span data-stu-id="aaf1d-164">The following code snippets are examples of `task/submit` request and response:</span></span>

<span data-ttu-id="aaf1d-165">**`task/submit` request**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-165">**`task/submit` request**</span></span>

```json
// task/submit POST request: agent/{botId}/invoke:
{
    "name": "task/submit",
    "value": {
        "data": {serialized_data_object},
        "context": {
            "theme": "default"
        },
    "tabContext": {
        "tabEntityId": "{tab_entity_id}"
        },
    },
    "conversation": {
        "id": "{generated_conversation_id}"
    },
    "imdisplayname": "{user_display_name}",
}
```

<span data-ttu-id="aaf1d-166">**`task/submit` tipo de resposta de tabulação**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-166">**`task/submit` tab response type**</span></span>

```json
// tab/fetch **continue** POST response: 
{
    "task":{
        "value": {
            "tab": {
                "type": "continue",
                "value": {
                    "cards": [
                        {
                            "card": adaptiveCard1
                        },
                        {
                            "card": adaptiveCard2
                        }
                    ]
                }
            }
        },
        "type": "continue"
    },
    "responseType": "task"
}
```

## <a name="authentication"></a><span data-ttu-id="aaf1d-167">Autenticação</span><span class="sxs-lookup"><span data-stu-id="aaf1d-167">Authentication</span></span>

<span data-ttu-id="aaf1d-168">Nas seções anteriores deste artigo, você viu que a maioria dos paradigmas de desenvolvimento poderia ser extrapolada das solicitações e respostas do módulo de tarefas em solicitações e respostas de tabulação.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-168">In the previous sections of this article, you have seen that most of the development paradigms could be extrapolated from the task module requests and responses into tab requests and responses.</span></span> <span data-ttu-id="aaf1d-169">No entanto, quando se trata de lidar com a autenticação, o fluxo de trabalho para a Guia Cartão Adaptável segue o padrão de autenticação para extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-169">However, when it comes to handling authentication, the workflow for Adaptive Card Tab follows the authentication pattern for messaging extensions.</span></span> <span data-ttu-id="aaf1d-170">Para obter mais informações, consulte [add authentication](../../messaging-extensions/how-to/add-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="aaf1d-170">For more information, see [add authentication](../../messaging-extensions/how-to/add-authentication.md).</span></span> 

<span data-ttu-id="aaf1d-171">Na seção [invocar atividades,](#invoke-activities) você foi informado de que as solicitações podem ter uma `tab/fetch` resposta **continue** ou **auth.**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-171">In the [invoke activities](#invoke-activities) section, you were informed that `tab/fetch` requests can have either a **continue** or an **auth** response.</span></span> <span data-ttu-id="aaf1d-172">Quando uma solicitação é acionada e recebe uma resposta `tab/fetch` **de tabulação,** a página de login é mostrada ao usuário.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-172">When a `tab/fetch` request is triggered and receives a tab **auth** response, the sign-in page is shown to the user.</span></span> 

<span data-ttu-id="aaf1d-173">**Para obter um código de autenticação por meio de `tab/fetch` invocação**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-173">**To get an authentication code through `tab/fetch` invoke**</span></span>

1. <span data-ttu-id="aaf1d-174">Abra seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-174">Open your app.</span></span> <span data-ttu-id="aaf1d-175">A página de login é exibida.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-175">The sign in page appears.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aaf1d-176">O logotipo do aplicativo é fornecido por meio da propriedade definida no manifesto do aplicativo e o título que aparece depois que o logotipo é definido na propriedade retornada no corpo da resposta de `icon` `title` **tabulação.**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-176">The app logo is provided through the `icon` property defined in the app manifest, and the title appearing after the logo is defined in the `title` property returned in the tab **auth** response body.</span></span>

1. <span data-ttu-id="aaf1d-177">Selecione **Entrar**. </span><span class="sxs-lookup"><span data-stu-id="aaf1d-177">Select **Sign in**.</span></span> <span data-ttu-id="aaf1d-178">Você é redirecionado para a URL de autenticação fornecida na `value` propriedade do corpo **da** resposta de autenticação.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-178">You are redirected to the authentication URL provided in the `value` property of the **auth** response body.</span></span> 
1. <span data-ttu-id="aaf1d-179">Uma janela pop-up será exibida.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-179">A pop-up window appears.</span></span> <span data-ttu-id="aaf1d-180">Essa janela pop-up hospeda sua página da Web usando a URL de autenticação.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-180">This pop-up window hosts your web page using the authentication URL.</span></span>
1. <span data-ttu-id="aaf1d-181">Depois de entrar, feche a janela.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-181">After you sign in, close the window.</span></span> <span data-ttu-id="aaf1d-182">Um *código de autenticação* é enviado para o Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-182">An *authentication code* is sent to the Teams client.</span></span>
1. <span data-ttu-id="aaf1d-183">O Teams cliente em seguida reeditará a solicitação para seu serviço, que inclui o código de autenticação fornecido `tab/fetch` pela página da Web hospedada.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-183">The Teams client then reissues the `tab/fetch` request to your service, which includes the authentication code provided by your hosted web page.</span></span> 

### <a name="tabfetch-authentication-data-flow"></a><span data-ttu-id="aaf1d-184">`tab/fetch` fluxo de dados de autenticação</span><span class="sxs-lookup"><span data-stu-id="aaf1d-184">`tab/fetch` authentication data flow</span></span>

<span data-ttu-id="aaf1d-185">A imagem a seguir fornece uma visão geral de como o fluxo de dados de autenticação funciona para uma `tab/fetch` invocação.</span><span class="sxs-lookup"><span data-stu-id="aaf1d-185">The following image provides an overview of how the authentication data flow works for a `tab/fetch` invoke.</span></span>

:::image type="content" source="../../assets/images/tabs/adaptive-cards-tab-auth-flow.png" alt-text="Exemplo de fluxo de tabulação de cartão adaptável." border="false":::

<span data-ttu-id="aaf1d-187">**`tab/fetch` resposta de auth**</span><span class="sxs-lookup"><span data-stu-id="aaf1d-187">**`tab/fetch` auth response**</span></span>

<span data-ttu-id="aaf1d-188">O trecho de código a seguir é um exemplo de `tab/fetch` resposta de auth:</span><span class="sxs-lookup"><span data-stu-id="aaf1d-188">The following code snippet is an example of `tab/fetch` auth response:</span></span>

```json
// tab/auth POST response (openURL)
{
    "tab": {
        "type": "auth",
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

### <a name="example"></a><span data-ttu-id="aaf1d-189">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aaf1d-189">Example</span></span>

<span data-ttu-id="aaf1d-190">Veja a seguir um exemplo de solicitação reeditar:</span><span class="sxs-lookup"><span data-stu-id="aaf1d-190">The following shows a reissued request example:</span></span>

```json
{
    "name": "tab/fetch",
    "type": "invoke",
    "timestamp": "2021-01-15T00:10:12.253Z",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "from": {
        "id": "{id}",
        "name": "John Smith",
        "aadObjectId": "00000000-0000-0000-0000-000000000000"
    },
    "conversation": {
        "tenantId": "{tenantId}",
        "id": "tab:{guid}"
    },
    "recipients": {
        "id": "28:00000000-0000-0000-0000-000000000000",
        "name": "ContosoApp"
    },
    "entities": [
        {
            "locale": "en-us",
            "country": "US",
            "platform": "Windows",
            "timezone": "America/Los_Angeles",
            "type": "clientInfo"
        }
    ],
    "channelData": {
        "tenant": { "id": "00000000-0000-0000-0000-000000000000" },
        "source": { "name": "message" }
    },
    "value": {
        "tabContext": { "tabEntityId": "homeTab" },
        "state": "0.43195668034524815"
    },
    "locale": "en-US",
    "localTimeZone": "America/Los_Angeles"
}
```

## <a name="see-also"></a><span data-ttu-id="aaf1d-191">Confira também</span><span class="sxs-lookup"><span data-stu-id="aaf1d-191">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aaf1d-192">Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="aaf1d-192">Adaptive Card</span></span>](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)

