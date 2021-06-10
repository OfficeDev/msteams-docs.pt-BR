---
title: Configurar opções de instalação padrão para seu aplicativo
description: Descreve como especificar as opções de instalação padrão do aplicativo.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 561a4f2910e703db5ffce6176f6177dfd661d2ce
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230929"
---
# <a name="configure-default-install-options-for-your-microsoft-teams-app"></a><span data-ttu-id="0e2e7-103">Configurar opções de instalação padrão para seu Microsoft Teams app</span><span class="sxs-lookup"><span data-stu-id="0e2e7-103">Configure default install options for your Microsoft Teams app</span></span>

<span data-ttu-id="0e2e7-104">É comum um aplicativo dar suporte a vários cenários no Teams, mas você pode ter projetado com um escopo e funcionalidade específicos em mente.</span><span class="sxs-lookup"><span data-stu-id="0e2e7-104">It’s common for an app to support multiple scenarios in Teams, but you may have designed it with a specific scope and capability in mind.</span></span> <span data-ttu-id="0e2e7-105">Por exemplo, se seu aplicativo for principalmente para uso de equipe ou canal, você pode garantir que a primeira opção de instalação que os usuários vejam na loja seja **Adicionar a uma equipe.**</span><span class="sxs-lookup"><span data-stu-id="0e2e7-105">For example, if your app is primarily for team or channel use, you can make sure that the first install option users see in the store is **Add to a team**.</span></span>

:::row:::
   :::column span="2":::

![Adicionar um exemplo suspenso de aplicativo](../../assets/images/compose-extensions/addanapp.png)

   :::column-end:::
   :::column span="2":::
   :::column-end:::
:::row-end:::

<span data-ttu-id="0e2e7-107">Se o recurso principal do aplicativo for um bot, você também poderá tornar o bot o recurso padrão quando um usuário instala seu aplicativo em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="0e2e7-107">If your app's primary capability is a bot, you can also make the bot the default capability when a user installs your app to a team.</span></span>

## <a name="configure-your-apps-default-install-scope"></a><span data-ttu-id="0e2e7-108">Configurar o escopo de instalação padrão do aplicativo</span><span class="sxs-lookup"><span data-stu-id="0e2e7-108">Configure your app's default install scope</span></span>

<span data-ttu-id="0e2e7-109">Configure o escopo de instalação padrão para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0e2e7-109">Configure the default install scope for your app.</span></span> <span data-ttu-id="0e2e7-110">Você pode definir apenas um escopo por vez.</span><span class="sxs-lookup"><span data-stu-id="0e2e7-110">You can set only one scope at a time.</span></span>

<span data-ttu-id="0e2e7-111">**Para configurar o escopo de instalação padrão no manifesto do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="0e2e7-111">**To configure the default install scope in your app manifest**</span></span>

1. <span data-ttu-id="0e2e7-112">Abra o manifesto do aplicativo e adicione a `defaultInstallScope` propriedade.</span><span class="sxs-lookup"><span data-stu-id="0e2e7-112">Open your app manifest and add the `defaultInstallScope` property.</span></span>
2. <span data-ttu-id="0e2e7-113">Definir o valor de escopo de instalação padrão como `personal` , `team` , ou `groupchat` `meetings` .</span><span class="sxs-lookup"><span data-stu-id="0e2e7-113">Set default install scope value as, either `personal`, `team`, `groupchat`, or `meetings`.</span></span>

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> <span data-ttu-id="0e2e7-114">Para obter mais informações, consulte o esquema [de manifesto do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="0e2e7-114">For more information, see the [app manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="configure-the-default-capability-for-shared-scopes"></a><span data-ttu-id="0e2e7-115">Configurar o recurso padrão para escopos compartilhados</span><span class="sxs-lookup"><span data-stu-id="0e2e7-115">Configure the default capability for shared scopes</span></span>

<span data-ttu-id="0e2e7-116">Configure o recurso padrão quando seu aplicativo estiver instalado para uma equipe, reunião ou groupchat.</span><span class="sxs-lookup"><span data-stu-id="0e2e7-116">Configure the default capability when your app is installed for a team, meeting, or groupchat.</span></span>

> [!NOTE]
> <span data-ttu-id="0e2e7-117">`defaultGroupCapability` fornece o recurso padrão que será adicionado à equipe, groupchat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="0e2e7-117">`defaultGroupCapability` provides the default capability that will be added to the team, groupchat, or meeting.</span></span> <span data-ttu-id="0e2e7-118">Selecione uma guia, bot ou conector como o recurso padrão para seu aplicativo, mas você deve garantir que tenha fornecido o recurso selecionado na definição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0e2e7-118">Select a tab, bot, or connector as the default capability for your app, but you must ensure that you have provided the selected capability in your app definition.</span></span>

<span data-ttu-id="0e2e7-119">**Para configurar detalhes no manifesto do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="0e2e7-119">**To configure details in app manifest**</span></span>

1. <span data-ttu-id="0e2e7-120">Abra o manifesto do aplicativo e adicione `defaultGroupCapability` a propriedade a ele.</span><span class="sxs-lookup"><span data-stu-id="0e2e7-120">Open your app manifest and add the `defaultGroupCapability` property to it.</span></span>
2. <span data-ttu-id="0e2e7-121">Definir um valor `team` de `groupchat` , ou `meetings` .</span><span class="sxs-lookup"><span data-stu-id="0e2e7-121">Set a value of `team`, `groupchat`, or `meetings`.</span></span>
3. <span data-ttu-id="0e2e7-122">Para a funcionalidade de grupo selecionada, os recursos de grupo disponíveis `bot` são, `tab` , ou `connector` .</span><span class="sxs-lookup"><span data-stu-id="0e2e7-122">For the selected group capability, the available group capabilities are, `bot`, `tab`, or `connector`.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="0e2e7-123">Você pode selecionar apenas um recurso `bot` padrão, , `tab` ou para o recurso de grupo `connector` selecionado.</span><span class="sxs-lookup"><span data-stu-id="0e2e7-123">You can select only one default capability, `bot`, `tab`, or `connector` for the selected group capability.</span></span>

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```

> [!NOTE]
> <span data-ttu-id="0e2e7-124">Para obter mais informações, consulte o esquema [de manifesto do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="0e2e7-124">For more information, see the [app manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="next-step"></a><span data-ttu-id="0e2e7-125">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="0e2e7-125">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e2e7-126">Criar um pacote do aplicativo</span><span class="sxs-lookup"><span data-stu-id="0e2e7-126">Create your app package</span></span>](~/concepts/build-and-test/apps-package.md)
