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
# <a name="devtools-for-microsoft-teams-tabs"></a>Guias do DevTools para o Microsoft Teams

Quando o Teams está sendo executado em um navegador, é fácil acessar o DevTools do navegador: F12 (no Windows) ou Command-Option-I (no MacOS). O DevTools oferece acesso a:

1. Exibir logs do console.
1. Exibir/modificar solicitações html, css e rede durante o tempo de execução.
1. Adicione pontos de interrupção ao seu código JavaScript e execute a depuração interativa.

O recurso só estará disponível em clientes da área de trabalho e android depois que a Visualização do Desenvolvedor tiver sido habilitada. Veja [como habilitar a Visualização do Desenvolvedor](~/resources/dev-preview/developer-preview-intro.md) para obter mais informações.

## <a name="accessing-devtools-in-the-desktop"></a>Acessando o DevTools na área de trabalho

Embora a versão web do Teams e a versão de área de trabalho das equipes sejam quase exatamente as mesmas, existem algumas diferenças, particularmente em relação à autenticação. Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools. Veja aqui como fazer isso a partir do cliente da área de trabalho do Teams. Para usar o DevTools no cliente da área de trabalho:

1. Certifique-se de ter habilitado a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)
1. Abra uma guia para que você tenha algo para inspecionar com o DevTools.
1. Abra o DevTools
    * No Windows, você abre o DevTools por meio do ícone do Microsoft Teams na bandeja da área de trabalho:

  ![Clique com o botão direito do mouse para abrir o DevTools](~/assets/images/dev-preview/devtools-right-click.png)

    * No MacOS, clique no ícone do Microsoft Teams no Dock.

Veja a aparência de uma guia de exemplo com o DevTools aberto e um elemento selecionado:

![Tab e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a>Acessando o DevTools de um cliente Android

Você também pode habilitar o DevTools do cliente Android do Teams. Para fazer isso:

1. Certifique-se de ter habilitado a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)
1. Conecte seu dispositivo ao computador desktop e configure seu dispositivo Android para [depuração remota](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)
1. No navegador Chrome, `chrome://inspect/#devices` abra.
1. Clique **na** inspeção abaixo da guia que você deseja depurar, como na captura de tela abaixo.

![Android DevTools](~/assets/images/android-devtools.png)
