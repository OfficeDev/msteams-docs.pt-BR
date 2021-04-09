---
title: Guias do DevTools para o Microsoft Teams
description: Descreve como chegar ao DevTools ao usar o Microsoft Teams Desktop Client
ms.topic: how-to
keywords: devtools depurar ferramentas de desenvolvedor do cliente de área de trabalho do chrome móvel
ms.openlocfilehash: 1c540c94adc080d9495097f8e3b427eeb14c56d8
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634738"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="c76a7-104">Guias do DevTools para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c76a7-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="c76a7-105">Quando o Teams está em execução em um navegador, é fácil acessar o DevTools: F12 do navegador no Windows ou Command-Option-I no MacOS.</span><span class="sxs-lookup"><span data-stu-id="c76a7-105">When Teams is running in a browser, it is easy to access the browser's DevTools: F12 on Windows or Command-Option-I on MacOS.</span></span> <span data-ttu-id="c76a7-106">O DevTools oferece acesso a:</span><span class="sxs-lookup"><span data-stu-id="c76a7-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="c76a7-107">Exibir logs do console.</span><span class="sxs-lookup"><span data-stu-id="c76a7-107">View console logs.</span></span>
1. <span data-ttu-id="c76a7-108">Exibir ou modificar solicitações html, CSS e rede durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c76a7-108">View or modify HTML, CSS, and network requests during runtime.</span></span>
1. <span data-ttu-id="c76a7-109">Adicione pontos de interrupção ao código JavaScript e execute a depuração interativa.</span><span class="sxs-lookup"><span data-stu-id="c76a7-109">Add breakpoints to your JavaScript code and perform interactive debugging.</span></span>

> [!NOTE]
> <span data-ttu-id="c76a7-110">O recurso só está disponível em clientes da área de trabalho e android depois que **a Visualização** do Desenvolvedor foi habilitada.</span><span class="sxs-lookup"><span data-stu-id="c76a7-110">The feature is only available in desktop and Android clients after **Developer Preview** has been enabled.</span></span> <span data-ttu-id="c76a7-111">Para obter mais informações, consulte [Como habilitar a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="c76a7-111">For more information, see [How do I enable developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

## <a name="access-devtools-in-the-desktop"></a><span data-ttu-id="c76a7-112">Access DevTools na Área de Trabalho</span><span class="sxs-lookup"><span data-stu-id="c76a7-112">Access DevTools in the Desktop</span></span>

<span data-ttu-id="c76a7-113">Embora a versão da Web e a versão da área de trabalho do Teams sejam quase exatamente as mesmas, há algumas diferenças em relação à autenticação.</span><span class="sxs-lookup"><span data-stu-id="c76a7-113">While the web version and the desktop version of Teams are almost exactly the same, there are some differences with respect to authentication.</span></span> <span data-ttu-id="c76a7-114">Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools.</span><span class="sxs-lookup"><span data-stu-id="c76a7-114">Sometimes the only way to figure out what is going on is to use the DevTools.</span></span> <span data-ttu-id="c76a7-115">Para usar o DevTools no cliente da área de trabalho, você deve:</span><span class="sxs-lookup"><span data-stu-id="c76a7-115">To use DevTools in the desktop client, you must:</span></span>

1. <span data-ttu-id="c76a7-116">Verifique se você habilitar a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="c76a7-116">Ensure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="c76a7-117">Abra uma guia para que você tenha algo a inspecionar com o DevTools.</span><span class="sxs-lookup"><span data-stu-id="c76a7-117">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="c76a7-118">Abra o DevTools de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c76a7-118">Open the DevTools in one of the following ways:</span></span>
    * <span data-ttu-id="c76a7-119">**Windows**: selecione o ícone do Teams na bandeja da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c76a7-119">**Windows**: Select the Teams icon in the desktop tray.</span></span>
    * <span data-ttu-id="c76a7-120">**MacOS**: selecione o ícone do Teams no Dock.</span><span class="sxs-lookup"><span data-stu-id="c76a7-120">**MacOS**: Select the Teams icon in the Dock.</span></span>
 
   <span data-ttu-id="c76a7-121">A imagem a seguir mostra DevTools inspecionando um elemento em uma caixa de diálogo de configuração de tabulação:</span><span class="sxs-lookup"><span data-stu-id="c76a7-121">The following image shows DevTools inspecting an element in a tab configuration dialog:</span></span>

   ![Tab e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="access-devtools-from-an-android-client"></a><span data-ttu-id="c76a7-123">Access DevTools de um cliente Android</span><span class="sxs-lookup"><span data-stu-id="c76a7-123">Access DevTools from an Android client</span></span>

<span data-ttu-id="c76a7-124">Você também pode habilitar o DevTools do cliente Do Teams Android.</span><span class="sxs-lookup"><span data-stu-id="c76a7-124">You can also enable the DevTools from the Teams Android client.</span></span> <span data-ttu-id="c76a7-125">Para habilitar o DevTools, você deve:</span><span class="sxs-lookup"><span data-stu-id="c76a7-125">To enable DevTools, you must:</span></span>

1. <span data-ttu-id="c76a7-126">Habilitar [a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="c76a7-126">Enable the [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="c76a7-127">Conecte seu dispositivo ao computador da área de trabalho e configure seu dispositivo Android para [depuração remota.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="c76a7-127">Connect your device to your desktop computer, and setup your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/).</span></span>
1. <span data-ttu-id="c76a7-128">No navegador Chrome, abra `chrome://inspect/#devices` .</span><span class="sxs-lookup"><span data-stu-id="c76a7-128">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="c76a7-129">Selecione **inspecionar** na guia que deseja depurar, como na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="c76a7-129">Select **inspect** under the tab you wish to debug, as in the following image:</span></span>

   ![Android DevTools](~/assets/images/android-devtools.png)
