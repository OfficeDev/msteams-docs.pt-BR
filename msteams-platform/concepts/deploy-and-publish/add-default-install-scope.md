---
title: Configurar opções de instalação padrão para seu aplicativo
description: Descreve como especificar as opções de instalação padrão do aplicativo.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: a4b70df70c7b9442e29953dae8a8c4e892cb72c1
ms.sourcegitcommit: 7b4f383b506d4bc68a1b5641d6e0f404edbfbc6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2021
ms.locfileid: "51946484"
---
# <a name="add-a-default-install-scope-and-group-capability"></a><span data-ttu-id="40a6a-103">Adicionar um escopo de instalação padrão e funcionalidade de grupo</span><span class="sxs-lookup"><span data-stu-id="40a6a-103">Add a default install scope and group capability</span></span>

<span data-ttu-id="40a6a-104">É comum um aplicativo dar suporte a vários cenários no Teams, mas você pode ter projetado com um escopo e funcionalidade específicos em mente.</span><span class="sxs-lookup"><span data-stu-id="40a6a-104">It’s common for an app to support multiple scenarios in Teams, but you may have designed it with a specific scope and capability in mind.</span></span> <span data-ttu-id="40a6a-105">Por exemplo, se seu aplicativo for principalmente para uso de equipe ou canal, você pode garantir que a primeira opção de instalação que os usuários vejam na loja seja **Adicionar a uma equipe.**</span><span class="sxs-lookup"><span data-stu-id="40a6a-105">For example, if your app is primarily for team or channel use, you can make sure that the first install option users see in the store is **Add to a team**.</span></span>

![Adicionar um aplicativo](../../assets/images/compose-extensions/addanapp.png)

<span data-ttu-id="40a6a-107">Se o recurso principal do aplicativo for um bot, você também poderá tornar o bot o recurso padrão quando um usuário instala seu aplicativo em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="40a6a-107">If your app's primary capability is a bot, you can also make the bot the default capability when a user installs your app to a team.</span></span> 

## <a name="configure-your-apps-default-install-scope"></a><span data-ttu-id="40a6a-108">Configurar o escopo de instalação padrão do aplicativo</span><span class="sxs-lookup"><span data-stu-id="40a6a-108">Configure your app's default install scope</span></span>

<span data-ttu-id="40a6a-109">Configure o escopo de instalação padrão para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40a6a-109">Configure the default install scope for your app.</span></span> <span data-ttu-id="40a6a-110">Você pode definir apenas um escopo por vez.</span><span class="sxs-lookup"><span data-stu-id="40a6a-110">You can set only one scope at a time.</span></span>

<span data-ttu-id="40a6a-111">**Para configurar o escopo de instalação padrão no manifesto do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="40a6a-111">**To configure the default install scope in your app manifest**</span></span>

1. <span data-ttu-id="40a6a-112">Abra o manifesto do aplicativo e adicione a `defaultInstallScope` propriedade.</span><span class="sxs-lookup"><span data-stu-id="40a6a-112">Open your app manifest and add the `defaultInstallScope` property.</span></span>
2. <span data-ttu-id="40a6a-113">De definir um valor `personal` de , , ou `team` `groupchat` `meetings` (consulte um exemplo abaixo).</span><span class="sxs-lookup"><span data-stu-id="40a6a-113">Set a value of `personal`, `team`, `groupchat`, or `meetings` (see an example below).</span></span>

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> <span data-ttu-id="40a6a-114">Para obter mais informações, consulte o esquema [de manifesto do aplicativo](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="40a6a-114">For more information, see the [app manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="configure-the-default-capability-for-shared-scopes"></a><span data-ttu-id="40a6a-115">Configurar o recurso padrão para escopos compartilhados</span><span class="sxs-lookup"><span data-stu-id="40a6a-115">Configure the default capability for shared scopes</span></span>

<span data-ttu-id="40a6a-116">Configure o recurso padrão quando seu aplicativo estiver instalado para uma equipe, reunião ou chat.</span><span class="sxs-lookup"><span data-stu-id="40a6a-116">Configure the default capability when your app is installed for a team, meeting, or chat.</span></span>

<span data-ttu-id="40a6a-117">**Para configurar detalhes no manifesto do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="40a6a-117">**To configure details in app manifest**</span></span>

1. <span data-ttu-id="40a6a-118">Abra o manifesto do aplicativo e adicione `defaultGroupCapability` a propriedade a ele.</span><span class="sxs-lookup"><span data-stu-id="40a6a-118">Open your app manifest and add the `defaultGroupCapability` property to it.</span></span>
2. <span data-ttu-id="40a6a-119">Salve as atualizações.</span><span class="sxs-lookup"><span data-stu-id="40a6a-119">Save the updates.</span></span>

    <span data-ttu-id="40a6a-120">A seguir está um exemplo JSON:</span><span class="sxs-lookup"><span data-stu-id="40a6a-120">Following is a JSON example:</span></span>

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```
> [!NOTE]
> <span data-ttu-id="40a6a-121">Para obter informações sobre o esquema completo, consulte [esquema de manifesto](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="40a6a-121">For information on full schema, see [manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="next-step"></a><span data-ttu-id="40a6a-122">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="40a6a-122">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="40a6a-123">Escolha como distribuir o aplicativo</span><span class="sxs-lookup"><span data-stu-id="40a6a-123">Choose how to distribute your app</span></span>](overview.md)
