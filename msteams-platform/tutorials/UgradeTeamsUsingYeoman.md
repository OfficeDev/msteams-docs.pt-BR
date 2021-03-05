---
title: Tutorial - Atualizar o Teams usando o gerador Yeoman do Microsoft Teams
description: Saiba como usar o gerador Yeoman do Microsoft Teams para atualizar o Teams.
ms.topic: tutorial
ms.openlocfilehash: 0c52dd15703000a1c0f99ddd28401dd686e1b1bb
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449595"
---
# <a name="upgrade-teams-using-microsoft-teams-yeoman-generator"></a>Atualizar o Teams usando o gerador Yeoman do Microsoft Teams
Este tutorial ajuda você a atualizar sua versão atual do aplicativo do Microsoft Teams para a versão mais recente usando o gerador Yeoman do Microsoft Teams.

## <a name="get-current-version-of-teams"></a>Obter a versão atual do Teams
```PowerShell
 yo teams --version
```

## <a name="update-teams"></a>Atualizar o Teams
O comando yo lista várias opções que vão desde a criação do projeto até a atualização do gerador. Use o seguinte comando para selecionar o gerador de atualização:
```PowerShell
 yo
```

Use as teclas de seta para escolher **Atualizar Geradores**.
![imagem de YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

A lista exibe todos os geradores disponíveis. Para selecionar ou desmarcar a versão do Teams nas opções disponíveis, use a barra de espaços **e** escolha um gerador específico.
![imagem de UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)

Leva alguns segundos para a instalação do Teams ser concluída.

Depois que a instalação for concluída, use o seguinte comando para verificar a versão instalada:

```PowerShell
yo teams --version
```

![imagem de FindVersionAfterInstallation](~/assets/images/Update-Teams/FindVersionAfterInstallation.png)

Parabéns! Você atualizou o Microsoft Teams.

