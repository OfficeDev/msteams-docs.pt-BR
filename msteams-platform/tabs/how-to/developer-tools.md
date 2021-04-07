---
title: Guias do DevTools para o Microsoft Teams
description: Descreve como chegar ao DevTools ao usar o Microsoft Teams Desktop Client
ms.topic: how-to
keywords: devtools depurar ferramentas de desenvolvedor do cliente de área de trabalho do chrome móvel
ms.openlocfilehash: 1bf7d246136a24316309ae144ac9552c5fd4f57d
ms.sourcegitcommit: f5ee3fa5ef6126d9bf845948d27d9067b3bbb994
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596270"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="bca37-104">Guias do DevTools para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bca37-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="bca37-105">Quando o Teams está em execução em um navegador, é fácil acessar o DevTools do navegador: F12 (no Windows) ou Command-Option-I (no MacOS).</span><span class="sxs-lookup"><span data-stu-id="bca37-105">When Teams is running in a browser, it’s easy to access the browser's DevTools: F12 (on Windows) or Command-Option-I (on MacOS).</span></span> <span data-ttu-id="bca37-106">O DevTools oferece acesso a:</span><span class="sxs-lookup"><span data-stu-id="bca37-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="bca37-107">Exibir logs do console.</span><span class="sxs-lookup"><span data-stu-id="bca37-107">View console logs.</span></span>
1. <span data-ttu-id="bca37-108">Exibir/modificar solicitações de html, css e rede durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bca37-108">View/modify html, css, and network requests during runtime.</span></span>
1. <span data-ttu-id="bca37-109">Adicione pontos de interrupção ao código JavaScript e execute a depuração interativa.</span><span class="sxs-lookup"><span data-stu-id="bca37-109">Add breakpoints to your JavaScript code, and perform interactive debugging.</span></span>

<span data-ttu-id="bca37-110">O recurso só está disponível em clientes da área de trabalho e android depois que a Visualização do Desenvolvedor foi habilitada.</span><span class="sxs-lookup"><span data-stu-id="bca37-110">The feature is only available in desktop and Android clients after Developer Preview has been enabled.</span></span> <span data-ttu-id="bca37-111">Confira [Como habilitar a Visualização do Desenvolvedor](~/resources/dev-preview/developer-preview-intro.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="bca37-111">See [How do I enable Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for more information.</span></span>

## <a name="accessing-devtools-in-the-desktop"></a><span data-ttu-id="bca37-112">Acessando o DevTools na Área de Trabalho</span><span class="sxs-lookup"><span data-stu-id="bca37-112">Accessing DevTools in the Desktop</span></span>

<span data-ttu-id="bca37-113">Embora a versão da Web do Teams e a versão da área de trabalho das equipes sejam quase exatamente as mesmas, há algumas diferenças, especialmente em relação à autenticação.</span><span class="sxs-lookup"><span data-stu-id="bca37-113">While the web version of Teams and the desktop version of teams are almost exactly the same, there are some differences, particularly with respect to authentication.</span></span> <span data-ttu-id="bca37-114">Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools.</span><span class="sxs-lookup"><span data-stu-id="bca37-114">Sometimes the only way to figure out what’s going on is to use the DevTools.</span></span> <span data-ttu-id="bca37-115">Veja como chegar a eles a partir do cliente de área de trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="bca37-115">Here's how to get to them from the Teams desktop client.</span></span> <span data-ttu-id="bca37-116">Para usar o DevTools no cliente da área de trabalho:</span><span class="sxs-lookup"><span data-stu-id="bca37-116">To use DevTools in the desktop client:</span></span>

1. <span data-ttu-id="bca37-117">Certifique-se de habilitar a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="bca37-117">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="bca37-118">Abra uma guia para que você tenha algo a inspecionar com o DevTools.</span><span class="sxs-lookup"><span data-stu-id="bca37-118">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="bca37-119">Abra o DevTools de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="bca37-119">Open the DevTools one of the following ways:</span></span>
    * <span data-ttu-id="bca37-120">**Windows**: selecione o ícone do Teams na bandeja da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bca37-120">**Windows**: Select the Teams icon in the desktop tray.</span></span>
    * <span data-ttu-id="bca37-121">**macOS**: selecione o ícone do Teams no Dock.</span><span class="sxs-lookup"><span data-stu-id="bca37-121">**macOS**: Select the Teams icon in the Dock.</span></span>

<span data-ttu-id="bca37-122">A captura de tela a seguir mostra DevTools inspecionando um elemento em uma caixa de diálogo de configuração de tabulação:</span><span class="sxs-lookup"><span data-stu-id="bca37-122">The following screenshot shows DevTools inspecting an element in a tab configuration dialog:</span></span>

![Tab e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a><span data-ttu-id="bca37-124">Acessando o DevTools de um cliente Android</span><span class="sxs-lookup"><span data-stu-id="bca37-124">Accessing DevTools from an Android client</span></span>

<span data-ttu-id="bca37-125">Você também pode habilitar o DevTools do cliente Do Teams Android.</span><span class="sxs-lookup"><span data-stu-id="bca37-125">You can also enable the DevTools from the Teams Android client.</span></span>

1. <span data-ttu-id="bca37-126">Certifique-se de habilitar a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="bca37-126">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="bca37-127">Conecte seu dispositivo ao computador da área de trabalho e configure seu dispositivo Android para [depuração remota](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="bca37-127">Connect your device to your desktop computer, and setup your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span></span>
1. <span data-ttu-id="bca37-128">No navegador Chrome, abra `chrome://inspect/#devices` .</span><span class="sxs-lookup"><span data-stu-id="bca37-128">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="bca37-129">Clique **em inspecionar** abaixo da guia que você deseja depurar, como na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="bca37-129">Click **inspect** below the tab you wish to debug, as in the screenshot below.</span></span>

![Android DevTools](~/assets/images/android-devtools.png)
