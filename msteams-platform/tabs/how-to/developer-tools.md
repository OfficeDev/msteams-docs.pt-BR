---
title: Guias do DevTools para o Microsoft Teams
description: Descreve como chegar ao DevTools ao usar o Microsoft Teams desktop e a depuração
ms.localizationpriority: medium
ms.topic: how-to
keywords: Guia ferramentas de desenvolvedor do cliente de área de trabalho do chrome móvel de depuração
ms.openlocfilehash: bec7b94b1db2492de9eaaa38ff62c0783c972f6e
ms.sourcegitcommit: d9daad3d5818d5774911b96fdc7bde45b04c9908
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64511211"
---
# <a name="devtools-for-microsoft-teams-tabs"></a>Guias do DevTools para o Microsoft Teams

Quando Teams em execução em um navegador, é fácil acessar o DevTools: F12 do navegador no Windows ou Command-Option-I no MacOS. O DevTools oferece acesso a:

1. Exibir logs do console.
1. Exibir ou modificar solicitações html, CSS e rede durante o tempo de execução.
1. Adicione pontos de interrupção ao código JavaScript e execute a depuração interativa.

> [!NOTE]
> O recurso só estará disponível para clientes da área de trabalho e android depois que a **Visualização** do Desenvolvedor tiver sido habilitada. Para obter mais informações, [consulte Como fazer habilitar a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).

## <a name="access-devtools-on-the-desktop"></a>Access DevTools na área de trabalho

Embora a versão da Web e a versão da área de trabalho Teams sejam quase as mesmas, há algumas diferenças em relação à autenticação. Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools. Para usar o DevTools no cliente da área de trabalho, você deve:

1. Verifique se você habilitar a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).
1. Abra uma guia para que você tenha algo a inspecionar com o DevTools.
1. Abra o DevTools de uma das seguintes maneiras:
    * No Windows, você abre o DevTools por meio do ícone Microsoft Teams na bandeja da área de trabalho.

      :::image type="content" source="../../assets/images/dev-preview/devtools-right-click.png" alt-text="developer-tool-windows":::

    * No MacOS, selecione o ícone Microsoft Teams no Dock.

      :::image type="content" source="../../assets/images/dev-preview/mac-os-developer-tools.PNG" alt-text="mac-os-dev-tools":::

O exemplo a seguir mostra DevTools abrir e inspecionar uma caixa de diálogo de configuração de tabulação:

   [![Tab e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)](~/assets/images/dev-preview/tab-and-devtools.png#lightbox)

## <a name="access-devtools-from-an-android-device"></a>Access DevTools de um dispositivo Android

Você também pode habilitar o DevTools do cliente Teams Android. Para habilitar o DevTools, você deve:

1. Habilitar [a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).
1. Conexão seu dispositivo para o computador da área de trabalho e configurar seu dispositivo Android para [depuração remota](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/).
1. No navegador Chrome, abra `chrome://inspect/#devices`.
1. Selecione **inspecionar** na guia que deseja depurar, como na imagem a seguir:

   ![Android DevTools](~/assets/images/android-devtools.png)
