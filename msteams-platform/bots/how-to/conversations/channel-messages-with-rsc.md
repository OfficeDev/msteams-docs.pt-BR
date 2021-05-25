---
title: Receber todas as mensagens de canal com RSC
author: surbhigupta12
description: Receber todas as mensagens de canal com permissões RSC
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 833bdbc015cf852fcd899ce4e75f742448b89978
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631239"
---
# <a name="receive-all-channel-messages-with-rsc"></a><span data-ttu-id="926e4-103">Receber todas as mensagens de canal com RSC</span><span class="sxs-lookup"><span data-stu-id="926e4-103">Receive all channel messages with RSC</span></span>

> [!NOTE]
> <span data-ttu-id="926e4-104">Esse recurso está disponível apenas na [visualização de desenvolvedor](../../../resources/dev-preview/developer-preview-intro.md) público.</span><span class="sxs-lookup"><span data-stu-id="926e4-104">This feature is currently available in [public developer preview](../../../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="926e4-105">O modelo de permissões de consentimento específico do recurso (RSC), originalmente desenvolvido para APIs Teams Graph, agora é estendido para cenários de bot.</span><span class="sxs-lookup"><span data-stu-id="926e4-105">The resource-specific consent (RSC) permissions model, originally developed for Teams Graph APIs, is now extended to bot scenarios.</span></span>

<span data-ttu-id="926e4-106">Atualmente, os bots só podem receber mensagens de canal do usuário quando estão @mentioned.</span><span class="sxs-lookup"><span data-stu-id="926e4-106">Currently, bots can only receive user channel messages when they are @mentioned.</span></span> <span data-ttu-id="926e4-107">Usando o RSC, agora você pode solicitar que os proprietários da equipe consentam para que um bot receba mensagens de usuário nos canais padrão em uma equipe sem @mentioned.</span><span class="sxs-lookup"><span data-stu-id="926e4-107">Using RSC, you can now request team owners to consent for a bot to receive user messages across standard channels in a team without being @mentioned.</span></span> <span data-ttu-id="926e4-108">Essa funcionalidade é habilitada especificando a permissão no manifesto de um `ChannelMessage.Read.Group` aplicativo Teams RSC habilitado.</span><span class="sxs-lookup"><span data-stu-id="926e4-108">This capability is enabled by specifying the `ChannelMessage.Read.Group` permission in the manifest of an RSC enabled Teams app.</span></span> <span data-ttu-id="926e4-109">Após a configuração, os proprietários da equipe podem conceder consentimento durante o processo de instalação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="926e4-109">After configuration, team owners can grant consent during the app installation process.</span></span>

<span data-ttu-id="926e4-110">Para obter mais informações sobre a habilitação do RSC para seu aplicativo, consulte [resource-specific consent in Teams](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="926e4-110">For more information about enabling RSC for your app, see [resource-specific consent in Teams](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest).</span></span>

## <a name="enable-bots-to-receive-all-channel-messages"></a><span data-ttu-id="926e4-111">Habilitar bots para receber todas as mensagens de canal</span><span class="sxs-lookup"><span data-stu-id="926e4-111">Enable bots to receive all channel messages</span></span>

<span data-ttu-id="926e4-112">A `ChannelMessage.Read.Group` permissão RSC é estendida para bots.</span><span class="sxs-lookup"><span data-stu-id="926e4-112">The `ChannelMessage.Read.Group` RSC permission is extended to bots.</span></span> <span data-ttu-id="926e4-113">Com o consentimento do usuário, essa permissão permite que os aplicativos gráficos recebam todas as mensagens em uma conversa e bots recebam todas as mensagens de canal sem serem @mentioned.</span><span class="sxs-lookup"><span data-stu-id="926e4-113">With user consent, this permission allows graph applications to get all messages in a conversation and bots to receive all channel messages without being @mentioned.</span></span>

## <a name="update-app-manifest"></a><span data-ttu-id="926e4-114">Atualizar manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="926e4-114">Update app manifest</span></span>

<span data-ttu-id="926e4-115">Para que o bot receba todas as mensagens de canal, o RSC deve ser configurado no manifesto do aplicativo Teams com a permissão `ChannelMessage.Read.Group` especificada na `webApplicationInfo` propriedade.</span><span class="sxs-lookup"><span data-stu-id="926e4-115">For your bot to receive all channel messages, RSC must be configured in the Teams app manifest with the `ChannelMessage.Read.Group` permission specified in the `webApplicationInfo` property.</span></span>

![Atualizar manifesto do aplicativo](~/bots/how-to/conversations/Media/appmanifest.png)

<span data-ttu-id="926e4-117">Veja a seguir um exemplo do `webApplicationInfo` objeto:</span><span class="sxs-lookup"><span data-stu-id="926e4-117">The following is an example of the `webApplicationInfo` object:</span></span>

* <span data-ttu-id="926e4-118">**id**: Sua Azure Active Directory (AAD) iD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="926e4-118">**id**: Your Azure Active Directory (AAD) app ID.</span></span> <span data-ttu-id="926e4-119">Isso pode ser o mesmo que sua ID de bot.</span><span class="sxs-lookup"><span data-stu-id="926e4-119">This can be the same as your bot ID.</span></span>
* <span data-ttu-id="926e4-120">**resource**: Qualquer cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="926e4-120">**resource**: Any string.</span></span> <span data-ttu-id="926e4-121">Este campo não tem nenhuma operação no RSC, mas deve ser adicionado e ter um valor para evitar a resposta de erro.</span><span class="sxs-lookup"><span data-stu-id="926e4-121">This field has no operation in RSC, but must be added and have a value to avoid error response.</span></span>
* <span data-ttu-id="926e4-122">**applicationPermissions**: as permissões RSC para seu aplicativo com `ChannelMessage.Read.Group` devem ser especificadas.</span><span class="sxs-lookup"><span data-stu-id="926e4-122">**applicationPermissions**: RSC permissions for your app with `ChannelMessage.Read.Group` must be specified.</span></span> <span data-ttu-id="926e4-123">Para obter mais informações, consulte [permissões específicas do recurso](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="926e4-123">For more information, see [resource-specific permissions](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).</span></span>

<span data-ttu-id="926e4-124">O código a seguir fornece um exemplo do manifesto do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="926e4-124">The following code provides an example of the app manifest:</span></span>

```json
"webApplicationInfo": {
"id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
"resource": "https://AnyString",
"applicationPermissions": [
"ChannelMessage.Read.Group"
    ]
  }
```

## <a name="sideload-in-a-team-to-test"></a><span data-ttu-id="926e4-125">Fazer sideload em uma equipe para testar</span><span class="sxs-lookup"><span data-stu-id="926e4-125">Sideload in a team to test</span></span>

<span data-ttu-id="926e4-126">Para fazer sideload em uma equipe para testar, se todas as mensagens de canal em uma equipe com RSC são recebidas sem @mentioned:</span><span class="sxs-lookup"><span data-stu-id="926e4-126">To sideload in a team to test, whether all channel messages in a team with RSC are received without being @mentioned:</span></span>

1. <span data-ttu-id="926e4-127">Selecione ou crie uma equipe.</span><span class="sxs-lookup"><span data-stu-id="926e4-127">Select or create a team.</span></span>
1. <span data-ttu-id="926e4-128">Selecione as releições &#x25CF;&#x25CF;&#x25CF; no painel esquerdo.</span><span class="sxs-lookup"><span data-stu-id="926e4-128">Select the ellipses &#x25CF;&#x25CF;&#x25CF; from the left pane.</span></span> <span data-ttu-id="926e4-129">O menu suspenso é exibido.</span><span class="sxs-lookup"><span data-stu-id="926e4-129">The drop-down menu appears.</span></span>
1. <span data-ttu-id="926e4-130">Selecione **Gerenciar equipe** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="926e4-130">Select **Manage team** from the drop-down menu.</span></span> <span data-ttu-id="926e4-131">Os detalhes aparecem.</span><span class="sxs-lookup"><span data-stu-id="926e4-131">The details appear.</span></span>

   ![Gerenciando aplicativos em equipe](~/bots/how-to/conversations/Media/managingteam.png)

1. <span data-ttu-id="926e4-133">Selecione **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="926e4-133">Select **Apps**.</span></span> <span data-ttu-id="926e4-134">Vários aplicativos aparecem.</span><span class="sxs-lookup"><span data-stu-id="926e4-134">Multiple apps appear.</span></span>
1. <span data-ttu-id="926e4-135">Selecione **Upload um aplicativo personalizado** no canto inferior direito.</span><span class="sxs-lookup"><span data-stu-id="926e4-135">Select **Upload a custom app** from the lower right corner.</span></span>

    ![Carregando aplicativo personalizado](~/bots/how-to/conversations/Media/uploadingcustomapp.png)

1. <span data-ttu-id="926e4-137">Selecione o pacote do aplicativo na **caixa de diálogo** Abrir.</span><span class="sxs-lookup"><span data-stu-id="926e4-137">Select the app package from the **Open** dialog box.</span></span>
1. <span data-ttu-id="926e4-138">Selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="926e4-138">Select **Open**.</span></span>

    ![Selecionar pacote de aplicativos](~/bots/how-to/conversations/Media/selectapppackage.png)

1. <span data-ttu-id="926e4-140">Selecione **Adicionar** no pop-up de detalhes do aplicativo, para adicionar o bot à sua equipe selecionada.</span><span class="sxs-lookup"><span data-stu-id="926e4-140">Select **Add** from the app details pop-up, to add the bot to your selected team.</span></span>

    ![Adicionando o bot](~/bots/how-to/conversations/Media/addingbot.png)

1. <span data-ttu-id="926e4-142">Selecione um canal e insira uma mensagem no canal do bot.</span><span class="sxs-lookup"><span data-stu-id="926e4-142">Select a channel and enter a message in the channel for your bot.</span></span>

    <span data-ttu-id="926e4-143">O bot recebe a mensagem sem ser @mentioned.</span><span class="sxs-lookup"><span data-stu-id="926e4-143">The bot receives the message without being @mentioned.</span></span>

    ![Bot recebe mensagem](~/bots/how-to/conversations/Media/botreceivingmessage.png)

## <a name="see-also"></a><span data-ttu-id="926e4-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="926e4-145">See also</span></span>

* [<span data-ttu-id="926e4-146">Conversas de bot</span><span class="sxs-lookup"><span data-stu-id="926e4-146">Bot conversations</span></span>](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [<span data-ttu-id="926e4-147">Consentimento específico do recurso</span><span class="sxs-lookup"><span data-stu-id="926e4-147">Resource-specific consent</span></span>](/microsoftteams/resource-specific-consent)
* [<span data-ttu-id="926e4-148">Testar o consentimento específico do recurso</span><span class="sxs-lookup"><span data-stu-id="926e4-148">Test resource-specific consent</span></span>](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [<span data-ttu-id="926e4-149">Upload aplicativo personalizado no Teams</span><span class="sxs-lookup"><span data-stu-id="926e4-149">Upload custom app in Teams</span></span>](~/concepts/deploy-and-publish/apps-upload.md)
