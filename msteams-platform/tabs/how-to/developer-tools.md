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
# <a name="devtools-for-microsoft-teams-tabs"></a>Guias do DevTools para o Microsoft Teams

Quando o Teams está em execução em um navegador, é fácil acessar o DevTools do navegador: F12 (no Windows) ou Command-Option-I (no MacOS). O DevTools oferece acesso a:

1. Exibir logs do console.
1. Exibir/modificar solicitações de html, css e rede durante o tempo de execução.
1. Adicione pontos de interrupção ao código JavaScript e execute a depuração interativa.

O recurso só está disponível em clientes da área de trabalho e android depois que a Visualização do Desenvolvedor foi habilitada. Confira [Como habilitar a Visualização do Desenvolvedor](~/resources/dev-preview/developer-preview-intro.md) para obter mais informações.

## <a name="accessing-devtools-in-the-desktop"></a>Acessando o DevTools na Área de Trabalho

Embora a versão da Web do Teams e a versão da área de trabalho das equipes sejam quase exatamente as mesmas, há algumas diferenças, especialmente em relação à autenticação. Às vezes, a única maneira de descobrir o que está acontecendo é usar o DevTools. Veja como chegar a eles a partir do cliente de área de trabalho do Teams. Para usar o DevTools no cliente da área de trabalho:

1. Certifique-se de habilitar a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)
1. Abra uma guia para que você tenha algo a inspecionar com o DevTools.
1. Abra o DevTools de uma das seguintes maneiras:
    * **Windows**: selecione o ícone do Teams na bandeja da área de trabalho.
    * **macOS**: selecione o ícone do Teams no Dock.

A captura de tela a seguir mostra DevTools inspecionando um elemento em uma caixa de diálogo de configuração de tabulação:

![Tab e DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a>Acessando o DevTools de um cliente Android

Você também pode habilitar o DevTools do cliente Do Teams Android.

1. Certifique-se de habilitar a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md)
1. Conecte seu dispositivo ao computador da área de trabalho e configure seu dispositivo Android para [depuração remota](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)
1. No navegador Chrome, abra `chrome://inspect/#devices` .
1. Clique **em inspecionar** abaixo da guia que você deseja depurar, como na captura de tela abaixo.

![Android DevTools](~/assets/images/android-devtools.png)
