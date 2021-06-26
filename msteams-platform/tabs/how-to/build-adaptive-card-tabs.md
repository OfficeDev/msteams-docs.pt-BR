---
title: Criar guias de cartão adaptáveis
author: KirtiPereira
description: Criar guias usando Cartões Adaptáveis
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: c551ae748805ddc380fb3213b67f704c73060a2f
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140282"
---
# <a name="build-tabs-with-adaptive-cards"></a><span data-ttu-id="849cc-103">Criar guias com Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="849cc-103">Build tabs with Adaptive Cards</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="849cc-104">Esse recurso está na [Visualização do Desenvolvedor Público](~/resources/dev-preview/developer-preview-intro.md) e tem suporte na área de trabalho e em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="849cc-104">This feature is in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) and is supported in desktop and mobile.</span></span> <span data-ttu-id="849cc-105">O suporte no navegador da Web está chegando em breve.</span><span class="sxs-lookup"><span data-stu-id="849cc-105">Support in the web browser is coming soon.</span></span>
> * <span data-ttu-id="849cc-106">Atualmente, as guias com Cartões Adaptáveis têm suporte apenas como aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="849cc-106">Tabs with Adaptive Cards are currently only supported as personal apps.</span></span>

<span data-ttu-id="849cc-107">Ao desenvolver uma guia usando o método tradicional, você pode executar esses problemas, como considerações HTML e CSS, tempos de carga lentos, restrições de iFrame e manutenção e custos do servidor.</span><span class="sxs-lookup"><span data-stu-id="849cc-107">When developing a tab using the traditional method, you might run into these issues, such as HTML and CSS considerations, slow load times, iFrame constraints, and server maintenance and costs.</span></span> <span data-ttu-id="849cc-108">As guias Cartão Adaptável são uma nova maneira de criar guias no Teams.</span><span class="sxs-lookup"><span data-stu-id="849cc-108">Adaptive Card tabs is a new way to build tabs in Teams.</span></span> <span data-ttu-id="849cc-109">Em vez de incorporar conteúdo da Web em um IFrame, você pode renderizar Cartões Adaptáveis em uma guia. Enquanto o front-end é renderizado com Cartões Adaptáveis, o back-end é alimentado por um bot.</span><span class="sxs-lookup"><span data-stu-id="849cc-109">Instead of embedding web content in an IFrame, you can render Adaptive Cards to a tab. While the front-end is rendered with Adaptive Cards, the backend is powered by a bot.</span></span> <span data-ttu-id="849cc-110">O bot é responsável por aceitar solicitações e responder adequadamente com o Cartão Adaptável renderizado.</span><span class="sxs-lookup"><span data-stu-id="849cc-110">The bot is responsible for accepting requests and responding appropriately with the Adaptive Card that is rendered.</span></span>

<span data-ttu-id="849cc-111">Você pode criar suas guias com blocos de IU (interface do usuário) prontos que pareçam nativos na área de trabalho, na Web e no celular.</span><span class="sxs-lookup"><span data-stu-id="849cc-111">You can build your tabs with ready-made user interface (UI) Lego-blocks that look and feel native on desktop, web, and mobile.</span></span> <span data-ttu-id="849cc-112">Este artigo ajuda você a entender as alterações necessárias para serem feitas no manifesto do aplicativo, como as solicitações de atividade de invocação e envia informações na guia com Cartões Adaptáveis e o impacto no fluxo de trabalho do módulo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="849cc-112">This article helps you understand the changes required to be made to the app manifest, how the invoke activity requests and sends information in tab with Adaptive Cards, and the impact on the task module workflow.</span></span>

<span data-ttu-id="849cc-113">A imagem a seguir mostra guias de com build com Cartões Adaptáveis na área de trabalho e no celular:</span><span class="sxs-lookup"><span data-stu-id="849cc-113">The following image depicts build tabs with Adaptive Cards in desktop and mobile:</span></span>

:::image type="content" source="../../assets/images/tabs/adaptive-cards-rendered-in-tabs.jpg" alt-text="Exemplo de Cartão Adaptável renderizado em guias." border="false":::

## <a name="prerequisites"></a><span data-ttu-id="849cc-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="849cc-115">Prerequisites</span></span>

<span data-ttu-id="849cc-116">Antes de começar a usar Cartões Adaptáveis para criar guias, você deve:</span><span class="sxs-lookup"><span data-stu-id="849cc-116">Before you start using Adaptive Cards to build tabs, you must:</span></span>

* <span data-ttu-id="849cc-117">Familiarizar-se com o desenvolvimento [de bots,](../../bots/what-are-bots.md)cartões [adaptáveis](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)e [módulos](../../task-modules-and-cards/task-modules/task-modules-bots.md) de tarefa no Teams.</span><span class="sxs-lookup"><span data-stu-id="849cc-117">Be familiar with, [bot development](../../bots/what-are-bots.md), [Adaptive Cards](../../task-modules-and-cards/what-are-cards.md#adaptive-cards), and [task modules](../../task-modules-and-cards/task-modules/task-modules-bots.md) in Teams.</span></span>
* <span data-ttu-id="849cc-118">Tenha um bot em execução Teams seu desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="849cc-118">Have a bot running in Teams for your development.</span></span>
* <span data-ttu-id="849cc-119">Estar em [Visualização de Desenvolvedor Público](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="849cc-119">Be in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

## <a name="changes-to-app-manifest"></a><span data-ttu-id="849cc-120">Alterações no manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="849cc-120">Changes to app manifest</span></span>

<span data-ttu-id="849cc-121">Aplicativos pessoais que renderizar guias devem incluir uma `staticTabs` matriz no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="849cc-121">Personal apps that render tabs must include a `staticTabs` array in their app manifest.</span></span> <span data-ttu-id="849cc-122">As guias Cartão Adaptável são renderizadas quando `contentBotId` a propriedade é fornecida na `staticTab` definição.</span><span class="sxs-lookup"><span data-stu-id="849cc-122">Adaptive Card tabs are rendered when the `contentBotId` property is provided in the `staticTab` definition.</span></span> <span data-ttu-id="849cc-123">As definições de tabulação estáticas devem conter uma guia , especificando uma guia Cartão Adaptável ou uma , especificando uma experiência típica de guia de `contentBotId` `contentUrl` conteúdo da Web hospedada.</span><span class="sxs-lookup"><span data-stu-id="849cc-123">Static tab definitions must contain either a `contentBotId`, specifying an Adaptive Card tab or a `contentUrl`, specifying a typical hosted web content tab experience.</span></span>

> [!NOTE]
> <span data-ttu-id="849cc-124">A propriedade está disponível no manifesto `contentBotId` versão 1.9 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="849cc-124">The `contentBotId` property is currently available in manifest version 1.9 or later.</span></span>

<span data-ttu-id="849cc-125">Forneça a propriedade com a guia Cartão Adaptável com a que `contentBotId` `botId` deve se comunicar.</span><span class="sxs-lookup"><span data-stu-id="849cc-125">Provide the `contentBotId` property with the `botId` that the Adaptive Card tab must communicate with.</span></span> <span data-ttu-id="849cc-126">A guia Cartão Adaptável configurada é enviada no parâmetro de cada solicitação de invocação e pode ser usada para diferenciar guias de cartão adaptáveis que são alimentadas pelo `entityId` `tabContext` mesmo bot.</span><span class="sxs-lookup"><span data-stu-id="849cc-126">The `entityId` configured for the Adaptive Card tab is sent in the `tabContext` parameter of each invoke request, and can be used to differentiate Adaptive Card Tabs that are powered by the same bot.</span></span> <span data-ttu-id="849cc-127">Para obter mais informações sobre outros campos de definição de tabulação estática, consulte [esquema de manifesto](../../resources/schema/manifest-schema.md#statictabs).</span><span class="sxs-lookup"><span data-stu-id="849cc-127">For more information about other static tab definition fields, see [manifest schema](../../resources/schema/manifest-schema.md#statictabs).</span></span>

<span data-ttu-id="849cc-128">A seguir está um manifesto de guia cartão adaptável de exemplo:</span><span class="sxs-lookup"><span data-stu-id="849cc-128">Following is a sample Adaptive Card tab manifest:</span></span>

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

## <a name="invoke-activities"></a><span data-ttu-id="849cc-129">Invocar atividades</span><span class="sxs-lookup"><span data-stu-id="849cc-129">Invoke activities</span></span>

<span data-ttu-id="849cc-130">A comunicação entre sua guia Cartão Adaptável e seu bot é feita por meio de `invoke` atividades.</span><span class="sxs-lookup"><span data-stu-id="849cc-130">Communication between your Adaptive Card tab and your bot is done through `invoke` activities.</span></span> <span data-ttu-id="849cc-131">Cada `invoke` atividade tem um nome **correspondente**.</span><span class="sxs-lookup"><span data-stu-id="849cc-131">Each `invoke` activity has a corresponding **name**.</span></span> <span data-ttu-id="849cc-132">Use o nome de cada atividade para diferenciar cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="849cc-132">Use the name of each activity to differentiate each request.</span></span> <span data-ttu-id="849cc-133">`tab/fetch` e `tab/submit` são as atividades abordadas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="849cc-133">`tab/fetch` and `tab/submit` are the activities covered in this section.</span></span>

### <a name="fetch-adaptive-card-to-render-to-a-tab"></a><span data-ttu-id="849cc-134">Buscar Cartão Adaptável para renderizar em uma guia</span><span class="sxs-lookup"><span data-stu-id="849cc-134">Fetch Adaptive Card to render to a tab</span></span>

<span data-ttu-id="849cc-135">`tab/fetch`é a primeira solicitação de invocação que seu bot recebe quando um usuário abre uma guia Cartão Adaptável. Quando o bot recebe a solicitação,  ele envia uma resposta de continuação de tabulação ou uma **resposta de tabulação.**</span><span class="sxs-lookup"><span data-stu-id="849cc-135">`tab/fetch` is the first invoke request that your bot receives when a user opens an Adaptive Card tab. When your bot receives the request, it either sends a tab **continue** response or a tab **auth** response.</span></span>
<span data-ttu-id="849cc-136">A **resposta continue** inclui uma matriz para **cartões**, que é renderizada verticalmente para a guia na ordem da matriz.</span><span class="sxs-lookup"><span data-stu-id="849cc-136">The **continue** response includes an array for **cards**, which is rendered vertically to the tab in the order of the array.</span></span>

> [!NOTE]
> <span data-ttu-id="849cc-137">Para obter mais informações sobre **a resposta de autenticação,** consulte [authentication](#authentication).</span><span class="sxs-lookup"><span data-stu-id="849cc-137">For more information on **auth** response, see [authentication](#authentication).</span></span>

<span data-ttu-id="849cc-138">O código a seguir fornece exemplos de `tab/fetch` solicitação e resposta:</span><span class="sxs-lookup"><span data-stu-id="849cc-138">The following code provides examples of `tab/fetch` request and response:</span></span>

<span data-ttu-id="849cc-139">**`tab/fetch` request**</span><span class="sxs-lookup"><span data-stu-id="849cc-139">**`tab/fetch` request**</span></span>

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

<span data-ttu-id="849cc-140">**`tab/fetch` response**</span><span class="sxs-lookup"><span data-stu-id="849cc-140">**`tab/fetch` response**</span></span>

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

### <a name="handle-submits-from-adaptive-card"></a><span data-ttu-id="849cc-141">Manipular envios do Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="849cc-141">Handle submits from Adaptive Card</span></span>

<span data-ttu-id="849cc-142">Depois que um Cartão Adaptável é renderizado na guia, ele deve ser capaz de responder às interações do usuário.</span><span class="sxs-lookup"><span data-stu-id="849cc-142">After an Adaptive Card is rendered in the tab, it must be able to respond to user interactions.</span></span> <span data-ttu-id="849cc-143">Essa resposta é manipulada pela `tab/submit` solicitação de invocação.</span><span class="sxs-lookup"><span data-stu-id="849cc-143">This response is handled by the `tab/submit` invoke request.</span></span>

<span data-ttu-id="849cc-144">Quando um usuário seleciona um botão na guia Cartão Adaptável, a solicitação é disparada para o bot com os dados correspondentes por meio da função `tab/submit` `Action.Submit` de Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="849cc-144">When a user selects a button on the Adaptive Card tab, the `tab/submit` request is triggered to your bot with the corresponding data through the `Action.Submit` function of Adaptive Card.</span></span> <span data-ttu-id="849cc-145">Os dados do Cartão Adaptável estão disponíveis por meio da propriedade data da `tab/submit` solicitação.</span><span class="sxs-lookup"><span data-stu-id="849cc-145">The Adaptive Card data is available through the data property of the `tab/submit` request.</span></span> <span data-ttu-id="849cc-146">Você recebe uma das seguintes respostas à sua solicitação:</span><span class="sxs-lookup"><span data-stu-id="849cc-146">You receive either of the following responses to your request:</span></span>

* <span data-ttu-id="849cc-147">Uma resposta de código de status HTTP `200` sem corpo.</span><span class="sxs-lookup"><span data-stu-id="849cc-147">An HTTP status code `200` response with no body.</span></span> <span data-ttu-id="849cc-148">Uma resposta 200 vazia não resulta em nenhuma ação tomada pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="849cc-148">An empty 200 response results in no action taken by the client.</span></span>
* <span data-ttu-id="849cc-149">A guia `200` padrão **continua** a resposta, conforme explicado em [fetch Adaptive Card](#fetch-adaptive-card-to-render-to-a-tab).</span><span class="sxs-lookup"><span data-stu-id="849cc-149">The standard `200` tab **continue** response, as explained in [fetch Adaptive Card](#fetch-adaptive-card-to-render-to-a-tab).</span></span> <span data-ttu-id="849cc-150">Uma resposta **de continuação** de tabulação dispara o cliente para atualizar a guia Cartão Adaptável renderizado com os Cartões Adaptáveis fornecidos na matriz de cartões da **resposta continuar.**</span><span class="sxs-lookup"><span data-stu-id="849cc-150">A tab **continue** response triggers the client to update the rendered Adaptive Card tab with the Adaptive Cards provided in the cards array of the **continue** response.</span></span>

<span data-ttu-id="849cc-151">O código a seguir fornece exemplos de `tab/submit` solicitação e resposta:</span><span class="sxs-lookup"><span data-stu-id="849cc-151">The following code provides examples of `tab/submit` request and response:</span></span>

<span data-ttu-id="849cc-152">**`tab/submit` request**</span><span class="sxs-lookup"><span data-stu-id="849cc-152">**`tab/submit` request**</span></span>

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

<span data-ttu-id="849cc-153">**`tab/submit` response**</span><span class="sxs-lookup"><span data-stu-id="849cc-153">**`tab/submit` response**</span></span>

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

## <a name="understand-task-module-workflow"></a><span data-ttu-id="849cc-154">Entender o fluxo de trabalho do módulo de tarefas</span><span class="sxs-lookup"><span data-stu-id="849cc-154">Understand task module workflow</span></span>

<span data-ttu-id="849cc-155">O módulo de tarefa também usa Cartão Adaptável para invocar `task/fetch` e `task/submit` solicitações e respostas.</span><span class="sxs-lookup"><span data-stu-id="849cc-155">The task module also uses Adaptive Card to invoke `task/fetch` and `task/submit` requests and responses.</span></span> <span data-ttu-id="849cc-156">Para obter mais informações, [consulte using Task Modules in Microsoft Teams bots](../../task-modules-and-cards/task-modules/task-modules-bots.md).</span><span class="sxs-lookup"><span data-stu-id="849cc-156">For more information, see [using Task Modules in Microsoft Teams bots](../../task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="849cc-157">Com a introdução da guia Cartão Adaptável, há uma alteração na forma como o bot responde a uma `task/submit` solicitação.</span><span class="sxs-lookup"><span data-stu-id="849cc-157">With the introduction of Adaptive Card tab, there is a change in how the bot responds to a `task/submit` request.</span></span> <span data-ttu-id="849cc-158">Se você estiver usando uma guia Cartão Adaptável, o bot responderá à solicitação de invocação com a guia padrão continuará a resposta e `task/submit` fechará o módulo de tarefa. </span><span class="sxs-lookup"><span data-stu-id="849cc-158">If you are using an Adaptive Card tab, the bot responds to the `task/submit` invoke request with the standard tab **continue** response, and closes the task module.</span></span> <span data-ttu-id="849cc-159">A guia Cartão Adaptável é atualizada renderizando a nova lista de cartões fornecidos na guia continuar **o** corpo da resposta.</span><span class="sxs-lookup"><span data-stu-id="849cc-159">The Adaptive Card tab is updated by rendering the new list of cards provided in the tab **continue** response body.</span></span>

### <a name="invoke-taskfetch"></a><span data-ttu-id="849cc-160">Invocar `task/fetch`</span><span class="sxs-lookup"><span data-stu-id="849cc-160">Invoke `task/fetch`</span></span>

<span data-ttu-id="849cc-161">O código a seguir fornece exemplos de `task/fetch` solicitação e resposta:</span><span class="sxs-lookup"><span data-stu-id="849cc-161">The following code provides examples of `task/fetch` request and response:</span></span>

<span data-ttu-id="849cc-162">**`task/fetch` request**</span><span class="sxs-lookup"><span data-stu-id="849cc-162">**`task/fetch` request**</span></span>
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

<span data-ttu-id="849cc-163">**`task/fetch` response**</span><span class="sxs-lookup"><span data-stu-id="849cc-163">**`task/fetch` response**</span></span>

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

### <a name="invoke-tasksubmit"></a><span data-ttu-id="849cc-164">Invocar `task/submit`</span><span class="sxs-lookup"><span data-stu-id="849cc-164">Invoke `task/submit`</span></span>

<span data-ttu-id="849cc-165">O código a seguir fornece exemplos de `task/submit` solicitação e resposta:</span><span class="sxs-lookup"><span data-stu-id="849cc-165">The following code provides examples of `task/submit` request and response:</span></span>

<span data-ttu-id="849cc-166">**`task/submit` request**</span><span class="sxs-lookup"><span data-stu-id="849cc-166">**`task/submit` request**</span></span>

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

<span data-ttu-id="849cc-167">**`task/submit` tipo de resposta de tabulação**</span><span class="sxs-lookup"><span data-stu-id="849cc-167">**`task/submit` tab response type**</span></span>

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

## <a name="authentication"></a><span data-ttu-id="849cc-168">Autenticação</span><span class="sxs-lookup"><span data-stu-id="849cc-168">Authentication</span></span>

<span data-ttu-id="849cc-169">Nas seções anteriores deste artigo, você viu que a maioria dos paradigmas de desenvolvimento pode ser estendida das solicitações e respostas do módulo de tarefas em solicitações e respostas de tabulação.</span><span class="sxs-lookup"><span data-stu-id="849cc-169">In the previous sections of this article, you have seen that most of the development paradigms can be extended from the task module requests and responses into tab requests and responses.</span></span> <span data-ttu-id="849cc-170">Quando se trata de lidar com a autenticação, a guia fluxo de trabalho para Cartão Adaptável segue o padrão de autenticação para extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="849cc-170">When it comes to handling authentication, the workflow for Adaptive Card tab follows the authentication pattern for messaging extensions.</span></span> <span data-ttu-id="849cc-171">Para obter mais informações, consulte [add authentication](../../messaging-extensions/how-to/add-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="849cc-171">For more information, see [add authentication](../../messaging-extensions/how-to/add-authentication.md).</span></span>

<span data-ttu-id="849cc-172">`tab/fetch`solicitações podem ter uma **resposta continue** **ou auth.**</span><span class="sxs-lookup"><span data-stu-id="849cc-172">`tab/fetch` requests can have either a **continue** or an **auth** response.</span></span> <span data-ttu-id="849cc-173">Quando uma solicitação é acionada e recebe uma resposta `tab/fetch` **de tabulação,** a página de login é mostrada ao usuário.</span><span class="sxs-lookup"><span data-stu-id="849cc-173">When a `tab/fetch` request is triggered and receives a tab **auth** response, the sign-in page is shown to the user.</span></span>

<span data-ttu-id="849cc-174">**Para obter um código de autenticação por meio de `tab/fetch` invocação**</span><span class="sxs-lookup"><span data-stu-id="849cc-174">**To get an authentication code through `tab/fetch` invoke**</span></span>

1. <span data-ttu-id="849cc-175">Abra seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="849cc-175">Open your app.</span></span> <span data-ttu-id="849cc-176">A página de login é exibida.</span><span class="sxs-lookup"><span data-stu-id="849cc-176">The sign in page appears.</span></span>

    > [!NOTE]
    > <span data-ttu-id="849cc-177">O logotipo do aplicativo é fornecido por meio `icon` da propriedade definida no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="849cc-177">The app logo is provided through the `icon` property defined in the app manifest.</span></span> <span data-ttu-id="849cc-178">O título que aparece depois que o logotipo é definido na `title` propriedade retornada no corpo **da resposta de tabulação.**</span><span class="sxs-lookup"><span data-stu-id="849cc-178">The title appearing after the logo is defined in the `title` property returned in the tab **auth** response body.</span></span>

1. <span data-ttu-id="849cc-179">Selecione **Entrar**. </span><span class="sxs-lookup"><span data-stu-id="849cc-179">Select **Sign in**.</span></span> <span data-ttu-id="849cc-180">Você é redirecionado para a URL de autenticação fornecida na `value` propriedade do corpo **da** resposta de autenticação.</span><span class="sxs-lookup"><span data-stu-id="849cc-180">You are redirected to the authentication URL provided in the `value` property of the **auth** response body.</span></span>
1. <span data-ttu-id="849cc-181">Uma janela pop-up será exibida.</span><span class="sxs-lookup"><span data-stu-id="849cc-181">A pop-up window appears.</span></span> <span data-ttu-id="849cc-182">Essa janela pop-up hospeda sua página da Web usando a URL de autenticação.</span><span class="sxs-lookup"><span data-stu-id="849cc-182">This pop-up window hosts your web page using the authentication URL.</span></span>
1. <span data-ttu-id="849cc-183">Depois de entrar, feche a janela.</span><span class="sxs-lookup"><span data-stu-id="849cc-183">After you sign in, close the window.</span></span> <span data-ttu-id="849cc-184">Um **código de autenticação** é enviado para o Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="849cc-184">An **authentication code** is sent to the Teams client.</span></span>
1. <span data-ttu-id="849cc-185">O Teams cliente em seguida reeditará a solicitação para seu serviço, que inclui o código de autenticação fornecido `tab/fetch` pela página da Web hospedada.</span><span class="sxs-lookup"><span data-stu-id="849cc-185">The Teams client then reissues the `tab/fetch` request to your service, which includes the authentication code provided by your hosted web page.</span></span>

### <a name="tabfetch-authentication-data-flow"></a><span data-ttu-id="849cc-186">`tab/fetch` fluxo de dados de autenticação</span><span class="sxs-lookup"><span data-stu-id="849cc-186">`tab/fetch` authentication data flow</span></span>

<span data-ttu-id="849cc-187">A imagem a seguir fornece uma visão geral de como o fluxo de dados de autenticação funciona para uma `tab/fetch` invocação.</span><span class="sxs-lookup"><span data-stu-id="849cc-187">The following image provides an overview of how the authentication data flow works for a `tab/fetch` invoke.</span></span>

:::image type="content" source="../../assets/images/tabs/adaptive-cards-tab-auth-flow.png" alt-text="Exemplo de fluxo de tabulação de cartão adaptável." border="false":::

<span data-ttu-id="849cc-189">**`tab/fetch` resposta de auth**</span><span class="sxs-lookup"><span data-stu-id="849cc-189">**`tab/fetch` auth response**</span></span>

<span data-ttu-id="849cc-190">O código a seguir fornece um exemplo de `tab/fetch` resposta de auth:</span><span class="sxs-lookup"><span data-stu-id="849cc-190">The following code provides an example of `tab/fetch` auth response:</span></span>

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

### <a name="example"></a><span data-ttu-id="849cc-191">Exemplo</span><span class="sxs-lookup"><span data-stu-id="849cc-191">Example</span></span>

<span data-ttu-id="849cc-192">O código a seguir mostra um exemplo de solicitação reeditar:</span><span class="sxs-lookup"><span data-stu-id="849cc-192">The following code shows a reissued request example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="849cc-193">Também consulte</span><span class="sxs-lookup"><span data-stu-id="849cc-193">See also</span></span>

* [<span data-ttu-id="849cc-194">Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="849cc-194">Adaptive Card</span></span>](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)
* [<span data-ttu-id="849cc-195">Teams guias</span><span class="sxs-lookup"><span data-stu-id="849cc-195">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="849cc-196">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="849cc-196">Prerequisites</span></span>](~/tabs/how-to/tab-requirements.md)
* [<span data-ttu-id="849cc-197">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="849cc-197">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="849cc-198">Criar um canal ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="849cc-198">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="849cc-199">Criar uma página de conteúdo</span><span class="sxs-lookup"><span data-stu-id="849cc-199">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
* [<span data-ttu-id="849cc-200">Criar uma página de configuração</span><span class="sxs-lookup"><span data-stu-id="849cc-200">Create a configuration page</span></span>](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [<span data-ttu-id="849cc-201">Criar uma página de remoção para sua guia</span><span class="sxs-lookup"><span data-stu-id="849cc-201">Create a removal page for your tab</span></span>](~/tabs/how-to/create-tab-pages/removal-page.md)
* [<span data-ttu-id="849cc-202">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="849cc-202">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="849cc-203">Obtenha contexto para sua guia</span><span class="sxs-lookup"><span data-stu-id="849cc-203">Get context for your tab</span></span>](~/tabs/how-to/access-teams-context.md)
* [<span data-ttu-id="849cc-204">Criar abas para conversação</span><span class="sxs-lookup"><span data-stu-id="849cc-204">Create conversational tabs</span></span>](~/tabs/how-to/conversational-tabs.md)
* [<span data-ttu-id="849cc-205">Alterações na margem da guia</span><span class="sxs-lookup"><span data-stu-id="849cc-205">Tab margin changes</span></span>](~/resources/removing-tab-margins.md)

## <a name="next-step"></a><span data-ttu-id="849cc-206">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="849cc-206">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="849cc-207">Link de guias desdobradas e Exibição de Estágio</span><span class="sxs-lookup"><span data-stu-id="849cc-207">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)