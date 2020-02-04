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
# <a name="devtools-for-microsoft-teams-tabs"></a>DevTools para guias do Microsoft Teams

Quando o Microsoft Teams é executado em um navegador, é fácil acessar o DevTools do navegador: F12 (no Windows) ou Command-Option-I (no MacOS). O DevTools fornece acesso a:

1. Exibir logs do console.
1. Exibir/modificar as solicitações HTML, CSS e de rede durante o tempo de execução.
1. Adicionar pontos de interrupção ao código JavaScript e realizar depuração interativa.

O recurso está disponível somente nos clientes de área de trabalho e Android após a visualização do desenvolvedor ter sido habilitada. Veja [como habilitar a visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md) para obter mais informações.

## <a name="accessing-devtools-in-the-desktop"></a>Acessando o DevTools na área de trabalho

Embora a versão da Web do Teams e da versão da área de trabalho do teams seja quase exatamente a mesma, existem algumas diferenças, particularmente em relação à autenticação. Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools. Confira aqui como acessá-los no cliente da área de trabalho do Microsoft Teams. Para usar o DevTools no cliente de desktop:

1. Verifique se você habilitou a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)
1. Abra uma guia para que você tenha algo a inspecionar com o DevTools.
1. Abra o DevTools
    * No Windows, abra o DevTools por meio do ícone do Microsoft Teams na bandeja da área de trabalho:

  ![Clique com o botão direito do mouse para abrir o DevTools](~/assets/images/dev-preview/devtools-right-click.png)

    * No MacOS, clique no ícone do Microsoft Teams no encaixe.

Veja a aparência de uma guia de exemplo com a DevTools aberta e um elemento selecionado:

![Guia e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a>Acessando o DevTools de um cliente Android

Você também pode habilitar o DevTools do cliente do Android do teams. Para fazer isso:

1. Verifique se você habilitou a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)
1. Conecte o dispositivo ao computador de mesa e configure seu dispositivo Android para [depuração remota](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)
1. No navegador Chrome, abra `chrome://inspect/#devices`.
1. Clique em **inspecionar** abaixo da guia que você deseja depurar, como na captura de tela abaixo.

![DevTools Android](~/assets/images/android-devtools.png)
