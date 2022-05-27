---
title: Guias do DevTools para o Microsoft Teams
description: Descreve como acessar o DevTools ao usar o cliente Microsoft Teams Desktop e a depuração
ms.localizationpriority: medium
ms.topic: how-to
keywords: guia ferramentas de desenvolvedor do cliente de devtools debug mobile chrome desktop
ms.openlocfilehash: c4601711948df798bda6b7d4940b5436c66f8c97
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757476"
---
# <a name="devtools-for-microsoft-teams-tabs"></a>Guias do DevTools para o Microsoft Teams

Quando Teams em execução em um navegador, é fácil acessar o DevTools do navegador: F12 no Windows ou Command-Option-I no MacOS. O DevTools fornece acesso a:

1. Exibir logs do console.
1. Exiba ou modifique solicitações de HTML, CSS e rede durante o runtime.
1. Adicione pontos de interrupção ao código JavaScript e execute a depuração interativa.

> [!NOTE]
> O recurso só estará disponível para clientes da área de trabalho e do Android depois que o **Developer Preview** tiver sido habilitado. Para obter mais informações, consulte [Como fazer versão prévia do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).

## <a name="access-devtools-on-the-desktop"></a>Acessar o DevTools na área de trabalho

Embora a versão da Web e a versão da área para desktop do Teams sejam quase as mesmas, há algumas diferenças em relação à autenticação. Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools. Para usar o DevTools no cliente para desktop, você deve:

1. Verifique se você habilitou a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).
1. Abra uma guia para que você tenha algo para inspecionar com o DevTools.
1. Abra o DevTools de uma das seguintes maneiras:
    * No Windows, você abre o DevTools por meio do Microsoft Teams na bandeja do desktop.

      :::image type="content" source="../../assets/images/dev-preview/devtools-right-click.png" alt-text="developer-tool-windows":::

    * No MacOS, selecione o Microsoft Teams no Dock.

      :::image type="content" source="../../assets/images/dev-preview/mac-os-developer-tools.PNG" alt-text="mac-os-dev-tools":::

O exemplo a seguir mostra o DevTools aberto e inspecionando uma caixa de diálogo de configuração de guia:

   [![Tab e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)](~/assets/images/dev-preview/tab-and-devtools.png#lightbox)

## <a name="access-devtools-from-an-android-device"></a>Acessar o DevTools de um dispositivo Android

Você também pode habilitar o DevTools do cliente Teams Android. Para habilitar o DevTools, você deve:

1. Habilitar a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).
1. Conexão seu dispositivo no computador desktop e configure seu dispositivo Android para [depuração remota](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/).
1. No navegador Chrome, abra `chrome://inspect/#devices`.
1. Selecione **inspecionar** na guia que você deseja depurar, como na imagem a seguir:

   ![Android DevTools](~/assets/images/android-devtools.png)
