---
title: Guias do DevTools para o Microsoft Teams
description: Descreve como chegar ao DevTools ao usar o Microsoft Teams Desktop Client
localization_priority: Normal
ms.topic: how-to
keywords: devtools depurar ferramentas de desenvolvedor do cliente de área de trabalho do chrome móvel
ms.openlocfilehash: 663368c96f4c75953dde2ce1160314eca0917e2a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020370"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="71de1-104">Guias do DevTools para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="71de1-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="71de1-105">Quando o Teams está em execução em um navegador, é fácil acessar o DevTools: F12 do navegador no Windows ou Command-Option-I no MacOS.</span><span class="sxs-lookup"><span data-stu-id="71de1-105">When Teams is running in a browser, it is easy to access the browser's DevTools: F12 on Windows or Command-Option-I on MacOS.</span></span> <span data-ttu-id="71de1-106">O DevTools oferece acesso a:</span><span class="sxs-lookup"><span data-stu-id="71de1-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="71de1-107">Exibir logs do console.</span><span class="sxs-lookup"><span data-stu-id="71de1-107">View console logs.</span></span>
1. <span data-ttu-id="71de1-108">Exibir ou modificar solicitações html, CSS e rede durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="71de1-108">View or modify HTML, CSS, and network requests during runtime.</span></span>
1. <span data-ttu-id="71de1-109">Adicione pontos de interrupção ao código JavaScript e execute a depuração interativa.</span><span class="sxs-lookup"><span data-stu-id="71de1-109">Add breakpoints to your JavaScript code and perform interactive debugging.</span></span>

> [!NOTE]
> <span data-ttu-id="71de1-110">O recurso só estará disponível para clientes da área de trabalho e android depois que a **Visualização** do Desenvolvedor tiver sido habilitada.</span><span class="sxs-lookup"><span data-stu-id="71de1-110">The feature is only available for desktop and Android clients after the **Developer Preview** has been enabled.</span></span> <span data-ttu-id="71de1-111">Para obter mais informações, consulte [Como habilitar a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="71de1-111">For more information, see [How do I enable developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

## <a name="access-devtools-in-the-desktop"></a><span data-ttu-id="71de1-112">Access DevTools na Área de Trabalho</span><span class="sxs-lookup"><span data-stu-id="71de1-112">Access DevTools in the Desktop</span></span>

<span data-ttu-id="71de1-113">Embora a versão da Web e a versão da área de trabalho do Teams sejam quase as mesmas, há algumas diferenças em relação à autenticação.</span><span class="sxs-lookup"><span data-stu-id="71de1-113">While the web version and the desktop version of Teams are almost the same, there are some differences concerning authentication.</span></span> <span data-ttu-id="71de1-114">Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools.</span><span class="sxs-lookup"><span data-stu-id="71de1-114">Sometimes the only way to figure out what is going on is to use the DevTools.</span></span> <span data-ttu-id="71de1-115">Para usar o DevTools no cliente da área de trabalho, você deve:</span><span class="sxs-lookup"><span data-stu-id="71de1-115">To use DevTools in the desktop client, you must:</span></span>

1. <span data-ttu-id="71de1-116">Verifique se você habilitar a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="71de1-116">Ensure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="71de1-117">Abra uma guia para que você tenha algo a inspecionar com o DevTools.</span><span class="sxs-lookup"><span data-stu-id="71de1-117">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="71de1-118">Abra o DevTools de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="71de1-118">Open the DevTools in one of the following ways:</span></span>
    * <span data-ttu-id="71de1-119">**Windows**: selecione o ícone do Teams na bandeja da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="71de1-119">**Windows**: Select the Teams icon in the desktop tray.</span></span>
    * <span data-ttu-id="71de1-120">**macOS**: selecione o ícone do Teams no Dock.</span><span class="sxs-lookup"><span data-stu-id="71de1-120">**macOS**: Select the Teams icon in the Dock.</span></span>
 
   <span data-ttu-id="71de1-121">A imagem a seguir mostra DevTools inspecionando um elemento em uma caixa de diálogo de configuração de tabulação:</span><span class="sxs-lookup"><span data-stu-id="71de1-121">The following image shows DevTools inspecting an element in a tab configuration dialog:</span></span>

   ![Tab e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="access-devtools-from-an-android-client"></a><span data-ttu-id="71de1-123">Access DevTools de um cliente Android</span><span class="sxs-lookup"><span data-stu-id="71de1-123">Access DevTools from an Android client</span></span>

<span data-ttu-id="71de1-124">Você também pode habilitar o DevTools do cliente Do Teams Android.</span><span class="sxs-lookup"><span data-stu-id="71de1-124">You can also enable the DevTools from the Teams Android client.</span></span> <span data-ttu-id="71de1-125">Para habilitar o DevTools, você deve:</span><span class="sxs-lookup"><span data-stu-id="71de1-125">To enable DevTools, you must:</span></span>

1. <span data-ttu-id="71de1-126">Habilitar [a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="71de1-126">Enable the [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="71de1-127">Conecte seu dispositivo ao computador da área de trabalho e configurar seu dispositivo Android para [depuração remota.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="71de1-127">Connect your device to your desktop computer, and set up your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/).</span></span>
1. <span data-ttu-id="71de1-128">No navegador Chrome, abra `chrome://inspect/#devices` .</span><span class="sxs-lookup"><span data-stu-id="71de1-128">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="71de1-129">Selecione **inspecionar** na guia que deseja depurar, como na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="71de1-129">Select **inspect** under the tab you wish to debug, as in the following image:</span></span>

   ![Android DevTools](~/assets/images/android-devtools.png)
