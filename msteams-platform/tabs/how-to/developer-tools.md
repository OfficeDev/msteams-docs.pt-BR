---
title: Guias do DevTools para o Microsoft Teams
description: Descreve como chegar ao DevTools ao usar o Microsoft Teams Desktop Client
localization_priority: Normal
ms.topic: how-to
keywords: devtools depurar ferramentas de desenvolvedor do cliente de área de trabalho do chrome móvel
ms.openlocfilehash: 70c9a2bab94ceb97e8dcd5cf5cdb98261d037f74
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101825"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="36932-104">Guias do DevTools para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="36932-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="36932-105">Quando Teams em execução em um navegador, é fácil acessar o DevTools: F12 do navegador no Windows ou Command-Option-I no MacOS.</span><span class="sxs-lookup"><span data-stu-id="36932-105">When Teams is running in a browser, it is easy to access the browser's DevTools: F12 on Windows or Command-Option-I on MacOS.</span></span> <span data-ttu-id="36932-106">O DevTools oferece acesso a:</span><span class="sxs-lookup"><span data-stu-id="36932-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="36932-107">Exibir logs do console.</span><span class="sxs-lookup"><span data-stu-id="36932-107">View console logs.</span></span>
1. <span data-ttu-id="36932-108">Exibir ou modificar solicitações html, CSS e rede durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="36932-108">View or modify HTML, CSS, and network requests during runtime.</span></span>
1. <span data-ttu-id="36932-109">Adicione pontos de interrupção ao código JavaScript e execute a depuração interativa.</span><span class="sxs-lookup"><span data-stu-id="36932-109">Add breakpoints to your JavaScript code and perform interactive debugging.</span></span>

> [!NOTE]
> <span data-ttu-id="36932-110">O recurso só estará disponível para clientes da área de trabalho e android depois que a **Visualização** do Desenvolvedor tiver sido habilitada.</span><span class="sxs-lookup"><span data-stu-id="36932-110">The feature is only available for desktop and Android clients after the **Developer Preview** has been enabled.</span></span> <span data-ttu-id="36932-111">Para obter mais informações, consulte [Como habilitar a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="36932-111">For more information, see [How do I enable developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

## <a name="access-devtools-on-the-desktop"></a><span data-ttu-id="36932-112">Access DevTools na área de trabalho</span><span class="sxs-lookup"><span data-stu-id="36932-112">Access DevTools on the desktop</span></span>

<span data-ttu-id="36932-113">Embora a versão da Web e a versão da área de trabalho do Teams sejam quase as mesmas, há algumas diferenças em relação à autenticação.</span><span class="sxs-lookup"><span data-stu-id="36932-113">While the web version and the desktop version of Teams are almost the same, there are some differences concerning authentication.</span></span> <span data-ttu-id="36932-114">Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools.</span><span class="sxs-lookup"><span data-stu-id="36932-114">Sometimes the only way to figure out what is going on is to use the DevTools.</span></span> <span data-ttu-id="36932-115">Para usar o DevTools no cliente da área de trabalho, você deve:</span><span class="sxs-lookup"><span data-stu-id="36932-115">To use DevTools in the desktop client, you must:</span></span>

1. <span data-ttu-id="36932-116">Verifique se você habilitar a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="36932-116">Ensure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="36932-117">Abra uma guia para que você tenha algo a inspecionar com o DevTools.</span><span class="sxs-lookup"><span data-stu-id="36932-117">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="36932-118">Abra o DevTools de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="36932-118">Open the DevTools one of the following ways:</span></span>
    * <span data-ttu-id="36932-119">No Windows, você abre o DevTools por meio do ícone Microsoft Teams na bandeja da área de trabalho:</span><span class="sxs-lookup"><span data-stu-id="36932-119">On Windows, you open DevTools via the Microsoft Teams icon in the desktop tray:</span></span><br>
  <span data-ttu-id="36932-120">![Clique com o botão direito do mouse para abrir o DevTools](~/assets/images/dev-preview/devtools-right-click.png)</span><span class="sxs-lookup"><span data-stu-id="36932-120">![Right-click to open DevTools](~/assets/images/dev-preview/devtools-right-click.png)</span></span>
    * <span data-ttu-id="36932-121">No MacOS, clique no ícone Microsoft Teams no Dock.</span><span class="sxs-lookup"><span data-stu-id="36932-121">On MacOS, click on the Microsoft Teams icon in the Dock.</span></span>

<span data-ttu-id="36932-122">O exemplo a seguir mostra DevTools abrir e inspecionar uma caixa de diálogo de configuração de tabulação:</span><span class="sxs-lookup"><span data-stu-id="36932-122">The following example shows DevTools open and inspecting a tab configuration dialog:</span></span>

   ![Tab e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="access-devtools-from-an-android-device"></a><span data-ttu-id="36932-124">Access DevTools de um dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="36932-124">Access DevTools from an Android device</span></span>

<span data-ttu-id="36932-125">Você também pode habilitar o DevTools do cliente Teams Android.</span><span class="sxs-lookup"><span data-stu-id="36932-125">You can also enable the DevTools from the Teams Android client.</span></span> <span data-ttu-id="36932-126">Para habilitar o DevTools, você deve:</span><span class="sxs-lookup"><span data-stu-id="36932-126">To enable DevTools, you must:</span></span>

1. <span data-ttu-id="36932-127">Habilitar [a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="36932-127">Enable the [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="36932-128">Conexão seu dispositivo para o computador da área de trabalho e configurar seu dispositivo Android para [depuração remota.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="36932-128">Connect your device to your desktop computer, and set up your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/).</span></span>
1. <span data-ttu-id="36932-129">No navegador Chrome, abra `chrome://inspect/#devices` .</span><span class="sxs-lookup"><span data-stu-id="36932-129">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="36932-130">Selecione **inspecionar** na guia que deseja depurar, como na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="36932-130">Select **inspect** under the tab you wish to debug, as in the following image:</span></span>

   ![Android DevTools](~/assets/images/android-devtools.png)
