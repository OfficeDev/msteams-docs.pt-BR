---
title: DevTools para guias do Microsoft Teams
description: Descreve como acessar o DevTools ao usar o cliente de desktop do Microsoft Teams
keywords: devtools depurar ferramentas de desenvolvedor do cliente Mobile Chrome desktop
ms.openlocfilehash: 6c8ac15caf64c979b23155be847e8791988486e6
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672701"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="efc25-104">DevTools para guias do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="efc25-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="efc25-105">Quando o Microsoft Teams é executado em um navegador, é fácil acessar o DevTools do navegador: F12 (no Windows) ou Command-Option-I (no MacOS).</span><span class="sxs-lookup"><span data-stu-id="efc25-105">When Teams is running in a browser, it’s easy to access the browser's DevTools: F12 (on Windows) or Command-Option-I (on MacOS).</span></span> <span data-ttu-id="efc25-106">O DevTools fornece acesso a:</span><span class="sxs-lookup"><span data-stu-id="efc25-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="efc25-107">Exibir logs do console.</span><span class="sxs-lookup"><span data-stu-id="efc25-107">View console logs.</span></span>
1. <span data-ttu-id="efc25-108">Exibir/modificar as solicitações HTML, CSS e de rede durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="efc25-108">View/modify html, css, and network requests during runtime.</span></span>
1. <span data-ttu-id="efc25-109">Adicionar pontos de interrupção ao código JavaScript e realizar depuração interativa.</span><span class="sxs-lookup"><span data-stu-id="efc25-109">Add breakpoints to your JavaScript code, and perform interactive debugging.</span></span>

<span data-ttu-id="efc25-110">O recurso está disponível somente nos clientes de área de trabalho e Android após a visualização do desenvolvedor ter sido habilitada.</span><span class="sxs-lookup"><span data-stu-id="efc25-110">The feature is only available in desktop and Android clients after Developer Preview has been enabled.</span></span> <span data-ttu-id="efc25-111">Veja [como habilitar a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="efc25-111">See [How do I enable Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for more information.</span></span>

## <a name="accessing-devtools-in-the-desktop"></a><span data-ttu-id="efc25-112">Acessando o DevTools na área de trabalho</span><span class="sxs-lookup"><span data-stu-id="efc25-112">Accessing DevTools in the Desktop</span></span>

<span data-ttu-id="efc25-113">Embora a versão da Web do Teams e da versão da área de trabalho do teams seja quase exatamente a mesma, existem algumas diferenças, particularmente em relação à autenticação.</span><span class="sxs-lookup"><span data-stu-id="efc25-113">While the web version of Teams and the desktop version of teams are almost exactly the same, there are some differences, particularly with respect to authentication.</span></span> <span data-ttu-id="efc25-114">Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools.</span><span class="sxs-lookup"><span data-stu-id="efc25-114">Sometimes the only way to figure out what’s going on is to use the DevTools.</span></span> <span data-ttu-id="efc25-115">Confira aqui como acessá-los no cliente da área de trabalho do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="efc25-115">Here's how to get to them from the Teams desktop client.</span></span> <span data-ttu-id="efc25-116">Para usar o DevTools no cliente de desktop:</span><span class="sxs-lookup"><span data-stu-id="efc25-116">To use DevTools in the desktop client:</span></span>

1. <span data-ttu-id="efc25-117">Verifique se você habilitou a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="efc25-117">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="efc25-118">Abra uma guia para que você tenha algo a inspecionar com o DevTools.</span><span class="sxs-lookup"><span data-stu-id="efc25-118">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="efc25-119">Abra o DevTools</span><span class="sxs-lookup"><span data-stu-id="efc25-119">Open the DevTools</span></span>
    * <span data-ttu-id="efc25-120">No Windows, abra o DevTools por meio do ícone do Microsoft Teams na bandeja da área de trabalho:</span><span class="sxs-lookup"><span data-stu-id="efc25-120">On Windows, you open DevTools via the Microsoft Teams icon in the desktop tray:</span></span>

  ![Clique com o botão direito do mouse para abrir o DevTools](~/assets/images/dev-preview/devtools-right-click.png)

    * <span data-ttu-id="efc25-122">No MacOS, clique no ícone do Microsoft Teams no encaixe.</span><span class="sxs-lookup"><span data-stu-id="efc25-122">On MacOS, click on the Microsoft Teams icon in the Dock.</span></span>

<span data-ttu-id="efc25-123">Veja a aparência de uma guia de exemplo com a DevTools aberta e um elemento selecionado:</span><span class="sxs-lookup"><span data-stu-id="efc25-123">Here’s what a sample tab looks like with the DevTools open and an element selected:</span></span>

![Guia e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a><span data-ttu-id="efc25-125">Acessando o DevTools de um cliente Android</span><span class="sxs-lookup"><span data-stu-id="efc25-125">Accessing DevTools from an Android client</span></span>

<span data-ttu-id="efc25-126">Você também pode habilitar o DevTools do cliente do Android do teams.</span><span class="sxs-lookup"><span data-stu-id="efc25-126">You can also enable the DevTools from the Teams Android client.</span></span> <span data-ttu-id="efc25-127">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="efc25-127">To do so:</span></span>

1. <span data-ttu-id="efc25-128">Verifique se você habilitou a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="efc25-128">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="efc25-129">Conecte o dispositivo ao computador de mesa e configure seu dispositivo Android para [depuração remota](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="efc25-129">Connect your device to your desktop computer, and setup your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span></span>
1. <span data-ttu-id="efc25-130">No navegador Chrome, abra `chrome://inspect/#devices`.</span><span class="sxs-lookup"><span data-stu-id="efc25-130">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="efc25-131">Clique em **inspecionar** abaixo da guia que você deseja depurar, como na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="efc25-131">Click **inspect** below the tab you wish to debug, as in the screenshot below.</span></span>

![DevTools Android](~/assets/images/android-devtools.png)
