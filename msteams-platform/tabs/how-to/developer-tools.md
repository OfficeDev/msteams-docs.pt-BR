---
title: Guias do DevTools para o Microsoft Teams
description: Descreve como obter o DevTools ao usar o Cliente de Área de Trabalho do Microsoft Teams
ms.topic: how-to
keywords: ferramentas de desenvolvedor do cliente de área de trabalho chrome móvel de depuração
ms.openlocfilehash: 8f23a5d56faa00d40451d2bbeadde32f6a5d0f7f
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014576"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="7dab1-104">Guias do DevTools para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7dab1-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="7dab1-105">Quando o Teams está sendo executado em um navegador, é fácil acessar o DevTools do navegador: F12 (no Windows) ou Command-Option-I (no MacOS).</span><span class="sxs-lookup"><span data-stu-id="7dab1-105">When Teams is running in a browser, it’s easy to access the browser's DevTools: F12 (on Windows) or Command-Option-I (on MacOS).</span></span> <span data-ttu-id="7dab1-106">O DevTools oferece acesso a:</span><span class="sxs-lookup"><span data-stu-id="7dab1-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="7dab1-107">Exibir logs do console.</span><span class="sxs-lookup"><span data-stu-id="7dab1-107">View console logs.</span></span>
1. <span data-ttu-id="7dab1-108">Exibir/modificar solicitações html, css e rede durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7dab1-108">View/modify html, css, and network requests during runtime.</span></span>
1. <span data-ttu-id="7dab1-109">Adicione pontos de interrupção ao seu código JavaScript e execute a depuração interativa.</span><span class="sxs-lookup"><span data-stu-id="7dab1-109">Add breakpoints to your JavaScript code, and perform interactive debugging.</span></span>

<span data-ttu-id="7dab1-110">O recurso só estará disponível em clientes da área de trabalho e android depois que a Visualização do Desenvolvedor tiver sido habilitada.</span><span class="sxs-lookup"><span data-stu-id="7dab1-110">The feature is only available in desktop and Android clients after Developer Preview has been enabled.</span></span> <span data-ttu-id="7dab1-111">Veja [como habilitar a Visualização do Desenvolvedor](~/resources/dev-preview/developer-preview-intro.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="7dab1-111">See [How do I enable Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for more information.</span></span>

## <a name="accessing-devtools-in-the-desktop"></a><span data-ttu-id="7dab1-112">Acessando o DevTools na área de trabalho</span><span class="sxs-lookup"><span data-stu-id="7dab1-112">Accessing DevTools in the Desktop</span></span>

<span data-ttu-id="7dab1-113">Embora a versão web do Teams e a versão de área de trabalho das equipes sejam quase exatamente as mesmas, existem algumas diferenças, particularmente em relação à autenticação.</span><span class="sxs-lookup"><span data-stu-id="7dab1-113">While the web version of Teams and the desktop version of teams are almost exactly the same, there are some differences, particularly with respect to authentication.</span></span> <span data-ttu-id="7dab1-114">Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools.</span><span class="sxs-lookup"><span data-stu-id="7dab1-114">Sometimes the only way to figure out what’s going on is to use the DevTools.</span></span> <span data-ttu-id="7dab1-115">Veja aqui como fazer isso a partir do cliente da área de trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="7dab1-115">Here's how to get to them from the Teams desktop client.</span></span> <span data-ttu-id="7dab1-116">Para usar o DevTools no cliente da área de trabalho:</span><span class="sxs-lookup"><span data-stu-id="7dab1-116">To use DevTools in the desktop client:</span></span>

1. <span data-ttu-id="7dab1-117">Certifique-se de ter habilitado a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="7dab1-117">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="7dab1-118">Abra uma guia para que você tenha algo para inspecionar com o DevTools.</span><span class="sxs-lookup"><span data-stu-id="7dab1-118">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="7dab1-119">Abra o DevTools</span><span class="sxs-lookup"><span data-stu-id="7dab1-119">Open the DevTools</span></span>
    * <span data-ttu-id="7dab1-120">No Windows, você abre o DevTools por meio do ícone do Microsoft Teams na bandeja da área de trabalho:</span><span class="sxs-lookup"><span data-stu-id="7dab1-120">On Windows, you open DevTools via the Microsoft Teams icon in the desktop tray:</span></span>

  ![Clique com o botão direito do mouse para abrir o DevTools](~/assets/images/dev-preview/devtools-right-click.png)

    * <span data-ttu-id="7dab1-122">No MacOS, clique no ícone do Microsoft Teams no Dock.</span><span class="sxs-lookup"><span data-stu-id="7dab1-122">On MacOS, click on the Microsoft Teams icon in the Dock.</span></span>

<span data-ttu-id="7dab1-123">Veja a aparência de uma guia de exemplo com o DevTools aberto e um elemento selecionado:</span><span class="sxs-lookup"><span data-stu-id="7dab1-123">Here’s what a sample tab looks like with the DevTools open and an element selected:</span></span>

![Tab e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a><span data-ttu-id="7dab1-125">Acessando o DevTools de um cliente Android</span><span class="sxs-lookup"><span data-stu-id="7dab1-125">Accessing DevTools from an Android client</span></span>

<span data-ttu-id="7dab1-126">Você também pode habilitar o DevTools do cliente Android do Teams.</span><span class="sxs-lookup"><span data-stu-id="7dab1-126">You can also enable the DevTools from the Teams Android client.</span></span> <span data-ttu-id="7dab1-127">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="7dab1-127">To do so:</span></span>

1. <span data-ttu-id="7dab1-128">Certifique-se de ter habilitado a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="7dab1-128">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="7dab1-129">Conecte seu dispositivo ao computador desktop e configure seu dispositivo Android para [depuração remota](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="7dab1-129">Connect your device to your desktop computer, and setup your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span></span>
1. <span data-ttu-id="7dab1-130">No navegador Chrome, `chrome://inspect/#devices` abra.</span><span class="sxs-lookup"><span data-stu-id="7dab1-130">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="7dab1-131">Clique **na** inspeção abaixo da guia que você deseja depurar, como na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="7dab1-131">Click **inspect** below the tab you wish to debug, as in the screenshot below.</span></span>

![Android DevTools](~/assets/images/android-devtools.png)
