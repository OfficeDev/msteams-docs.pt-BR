---
title: Tutorial - Atualizar o Teams usando o gerador Yeoman do Microsoft Teams
description: Saiba como usar o gerador Yeoman do Microsoft Teams para atualizar o Teams.
ms.topic: tutorial
ms.openlocfilehash: 0c52dd15703000a1c0f99ddd28401dd686e1b1bb
ms.sourcegitcommit: afe4bc0336663e496d03c52e4b206217c02fae63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2021
ms.locfileid: "50528629"
---
# <a name="upgrade-teams-using-microsoft-teams-yeoman-generator"></a><span data-ttu-id="bdf08-103">Atualizar o Teams usando o gerador Yeoman do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bdf08-103">Upgrade Teams using Microsoft Teams Yeoman generator</span></span>
<span data-ttu-id="bdf08-104">Este tutorial ajuda você a atualizar sua versão atual do aplicativo do Microsoft Teams para a versão mais recente usando o gerador Yeoman do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="bdf08-104">This tutorial helps you to upgrade your current Microsoft Teams app version to the latest version using the Microsoft Teams Yeoman generator.</span></span>

## <a name="get-current-version-of-teams"></a><span data-ttu-id="bdf08-105">Obter a versão atual do Teams</span><span class="sxs-lookup"><span data-stu-id="bdf08-105">Get current version of Teams</span></span>
```PowerShell
 yo teams --version
```

## <a name="update-teams"></a><span data-ttu-id="bdf08-106">Atualizar o Teams</span><span class="sxs-lookup"><span data-stu-id="bdf08-106">Update Teams</span></span>
<span data-ttu-id="bdf08-107">O comando yo lista várias opções que vão desde a criação do projeto até a atualização do gerador.</span><span class="sxs-lookup"><span data-stu-id="bdf08-107">The yo command lists out various options ranging from creating project to updating generator.</span></span> <span data-ttu-id="bdf08-108">Use o seguinte comando para selecionar o gerador de atualização:</span><span class="sxs-lookup"><span data-stu-id="bdf08-108">Use the following command to select update generator:</span></span>
```PowerShell
 yo
```

<span data-ttu-id="bdf08-109">Use as teclas de seta para escolher **Atualizar Geradores**.</span><span class="sxs-lookup"><span data-stu-id="bdf08-109">Use the arrow keys to choose **Update Generators**.</span></span>
<span data-ttu-id="bdf08-110">![imagem de YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)</span><span class="sxs-lookup"><span data-stu-id="bdf08-110">![image of YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)</span></span>

<span data-ttu-id="bdf08-111">A lista exibe todos os geradores disponíveis.</span><span class="sxs-lookup"><span data-stu-id="bdf08-111">The list displays all the available generators.</span></span> <span data-ttu-id="bdf08-112">Para selecionar ou desmarcar a versão do Teams nas opções disponíveis, use a barra de espaços **e** escolha um gerador específico.</span><span class="sxs-lookup"><span data-stu-id="bdf08-112">To select or unselect Teams version from the available options, use the **space bar** and choose a specific generator.</span></span>
<span data-ttu-id="bdf08-113">![imagem de UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)</span><span class="sxs-lookup"><span data-stu-id="bdf08-113">![image of UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)</span></span>

<span data-ttu-id="bdf08-114">Leva alguns segundos para a instalação do Teams ser concluída.</span><span class="sxs-lookup"><span data-stu-id="bdf08-114">It takes few seconds to minutes for Teams installation to complete.</span></span>

<span data-ttu-id="bdf08-115">Depois que a instalação for concluída, use o seguinte comando para verificar a versão instalada:</span><span class="sxs-lookup"><span data-stu-id="bdf08-115">After the installation is complete, use the following command to check the installed version:</span></span>

```PowerShell
yo teams --version
```

![imagem de FindVersionAfterInstallation](~/assets/images/Update-Teams/FindVersionAfterInstallation.png)

<span data-ttu-id="bdf08-117">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="bdf08-117">Congrats!</span></span> <span data-ttu-id="bdf08-118">Você atualizou o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="bdf08-118">You have upgraded Microsoft Teams.</span></span>

