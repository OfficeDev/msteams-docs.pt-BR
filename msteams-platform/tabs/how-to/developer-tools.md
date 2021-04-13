---
title: Guias do DevTools para o Microsoft Teams
description: Descreve como chegar ao DevTools ao usar o Microsoft Teams Desktop Client
ms.topic: how-to
keywords: devtools depurar ferramentas de desenvolvedor do cliente de área de trabalho do chrome móvel
ms.openlocfilehash: 7bd9403a74fd33619a2f8ac1b4b3a4c74a21175d
ms.sourcegitcommit: 9404c2e3a30887b9e17e0c89b12dd26fd9b8033e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2021
ms.locfileid: "51654381"
---
# <a name="devtools-for-microsoft-teams-tabs"></a>Guias do DevTools para o Microsoft Teams

Quando o Teams está em execução em um navegador, é fácil acessar o DevTools: F12 do navegador no Windows ou Command-Option-I no MacOS. O DevTools oferece acesso a:

1. Exibir logs do console.
1. Exibir ou modificar solicitações html, CSS e rede durante o tempo de execução.
1. Adicione pontos de interrupção ao código JavaScript e execute a depuração interativa.

> [!NOTE]
> O recurso só estará disponível para clientes da área de trabalho e android depois que a **Visualização** do Desenvolvedor tiver sido habilitada. Para obter mais informações, consulte [Como habilitar a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).

## <a name="access-devtools-in-the-desktop"></a>Access DevTools na Área de Trabalho

Embora a versão da Web e a versão da área de trabalho do Teams sejam quase as mesmas, há algumas diferenças em relação à autenticação. Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools. Para usar o DevTools no cliente da área de trabalho, você deve:

1. Verifique se você habilitar a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).
1. Abra uma guia para que você tenha algo a inspecionar com o DevTools.
1. Abra o DevTools de uma das seguintes maneiras:
    * **Windows**: selecione o ícone do Teams na bandeja da área de trabalho.
    * **macOS**: selecione o ícone do Teams no Dock.
 
   A imagem a seguir mostra DevTools inspecionando um elemento em uma caixa de diálogo de configuração de tabulação:

   ![Tab e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="access-devtools-from-an-android-client"></a>Access DevTools de um cliente Android

Você também pode habilitar o DevTools do cliente Do Teams Android. Para habilitar o DevTools, você deve:

1. Habilitar [a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).
1. Conecte seu dispositivo ao computador da área de trabalho e configurar seu dispositivo Android para [depuração remota.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)
1. No navegador Chrome, abra `chrome://inspect/#devices` .
1. Selecione **inspecionar** na guia que deseja depurar, como na imagem a seguir:

   ![Android DevTools](~/assets/images/android-devtools.png)
