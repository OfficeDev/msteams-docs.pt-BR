---
title: Configurar opções de instalação padrão para seu aplicativo
description: Descreve como especificar as opções de instalação padrão do aplicativo.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 0afcce50a4779421016c23c4ec4e3d25cc3401d1
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058611"
---
# <a name="add-a-default-install-scope-and-group-capability"></a><span data-ttu-id="f6ca3-103">Adicionar um escopo de instalação padrão e funcionalidade de grupo</span><span class="sxs-lookup"><span data-stu-id="f6ca3-103">Add a default install scope and group capability</span></span>

<span data-ttu-id="f6ca3-104">É comum um aplicativo dar suporte a vários cenários no Teams, mas você pode ter projetado com um escopo e funcionalidade específicos em mente.</span><span class="sxs-lookup"><span data-stu-id="f6ca3-104">It’s common for an app to support multiple scenarios in Teams, but you may have designed it with a specific scope and capability in mind.</span></span> <span data-ttu-id="f6ca3-105">Por exemplo, se seu aplicativo for principalmente para uso de equipe ou canal, você pode garantir que a primeira opção de instalação que os usuários vejam na loja seja **Adicionar a uma equipe.**</span><span class="sxs-lookup"><span data-stu-id="f6ca3-105">For example, if your app is primarily for team or channel use, you can make sure that the first install option users see in the store is **Add to a team**.</span></span>

![Adicionar um aplicativo](../../assets/images/compose-extensions/addanapp.png)

<span data-ttu-id="f6ca3-107">Se o recurso principal do aplicativo for um bot, você também poderá tornar o bot o recurso padrão quando um usuário instala seu aplicativo em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="f6ca3-107">If your app's primary capability is a bot, you can also make the bot the default capability when a user installs your app to a team.</span></span>

## <a name="configure-your-apps-default-install-scope"></a><span data-ttu-id="f6ca3-108">Configurar o escopo de instalação padrão do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f6ca3-108">Configure your app's default install scope</span></span>

<span data-ttu-id="f6ca3-109">Configure o escopo de instalação padrão para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6ca3-109">Configure the default install scope for your app.</span></span> <span data-ttu-id="f6ca3-110">Você pode definir apenas um escopo por vez.</span><span class="sxs-lookup"><span data-stu-id="f6ca3-110">You can set only one scope at a time.</span></span>

<span data-ttu-id="f6ca3-111">**Para configurar o escopo de instalação padrão no manifesto do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="f6ca3-111">**To configure the default install scope in your app manifest**</span></span>

1. <span data-ttu-id="f6ca3-112">Abra o manifesto do aplicativo e adicione a `defaultInstallScope` propriedade.</span><span class="sxs-lookup"><span data-stu-id="f6ca3-112">Open your app manifest and add the `defaultInstallScope` property.</span></span>
2. <span data-ttu-id="f6ca3-113">Definir o valor de escopo de instalação padrão como `personal` , `team` , ou `groupchat` `meetings` .</span><span class="sxs-lookup"><span data-stu-id="f6ca3-113">Set default install scope value as, either `personal`, `team`, `groupchat`, or `meetings`.</span></span>

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> <span data-ttu-id="f6ca3-114">Para obter mais informações, consulte o esquema [de manifesto do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="f6ca3-114">For more information, see the [app manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="configure-the-default-capability-for-shared-scopes"></a><span data-ttu-id="f6ca3-115">Configurar o recurso padrão para escopos compartilhados</span><span class="sxs-lookup"><span data-stu-id="f6ca3-115">Configure the default capability for shared scopes</span></span>

<span data-ttu-id="f6ca3-116">Configure o recurso padrão quando seu aplicativo estiver instalado para uma equipe, reunião ou groupchat.</span><span class="sxs-lookup"><span data-stu-id="f6ca3-116">Configure the default capability when your app is installed for a team, meeting, or groupchat.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ca3-117">`defaultGroupCapability` fornece o recurso padrão que será adicionado à equipe, groupchat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="f6ca3-117">`defaultGroupCapability` provides the default capability that will be added to the team, groupchat, or meeting.</span></span> <span data-ttu-id="f6ca3-118">Selecione uma guia, bot ou conector como o recurso padrão para seu aplicativo, mas você deve garantir que tenha fornecido o recurso selecionado na definição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6ca3-118">Select a tab, bot, or connector as the default capability for your app, but you must ensure that you have provided the selected capability in your app definition.</span></span>

<span data-ttu-id="f6ca3-119">**Para configurar detalhes no manifesto do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="f6ca3-119">**To configure details in app manifest**</span></span>

1. <span data-ttu-id="f6ca3-120">Abra o manifesto do aplicativo e adicione `defaultGroupCapability` a propriedade a ele.</span><span class="sxs-lookup"><span data-stu-id="f6ca3-120">Open your app manifest and add the `defaultGroupCapability` property to it.</span></span>
2. <span data-ttu-id="f6ca3-121">Definir um valor `team` de `groupchat` , ou `meetings` .</span><span class="sxs-lookup"><span data-stu-id="f6ca3-121">Set a value of `team`, `groupchat`, or `meetings`.</span></span>
3. <span data-ttu-id="f6ca3-122">Para a funcionalidade de grupo selecionada, os recursos de grupo disponíveis `bot` são, `tab` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="f6ca3-122">For the selected group capability, the available group capabilities are, `bot`, `tab`, or `connector`.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="f6ca3-123">Você pode selecionar apenas um recurso `bot` padrão, , `tab` ou para o recurso de grupo `connector` selecionado.</span><span class="sxs-lookup"><span data-stu-id="f6ca3-123">You can select only one default capability, `bot`, `tab`, or `connector` for the selected group capability.</span></span>

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```

> [!NOTE]
> <span data-ttu-id="f6ca3-124">Para obter mais informações, consulte o esquema [de manifesto do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="f6ca3-124">For more information, see the [app manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="next-step"></a><span data-ttu-id="f6ca3-125">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="f6ca3-125">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f6ca3-126">Escolha como distribuir o aplicativo</span><span class="sxs-lookup"><span data-stu-id="f6ca3-126">Choose how to distribute your app</span></span>](overview.md)
