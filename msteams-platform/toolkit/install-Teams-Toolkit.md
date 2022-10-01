---
title: Instalar o Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Neste módulo, aprenda a instalação do Kit de Ferramentas do Teams
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 07/29/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 03d101df114d3f7564c78c433d01191172e180c9
ms.sourcegitcommit: 3aaccc48906fc6f6fbf79916af5664bf55537250
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68295981"
---
# <a name="install-teams-toolkit"></a>Instalar o Kit de Ferramentas do Teams

Este artigo descreve como instalar a extensão do Kit de Ferramentas do Teams.

## <a name="prerequisites"></a>Pré-requisitos

::: zone pivot="visual-studio-code"

Antes de instalar o Kit de Ferramentas do Teams para Visual Studio Code, você precisará [baixar e instalar](https://code.visualstudio.com/Download) Visual Studio Code.

::: zone-end

::: zone pivot="visual-studio"

Antes de instalar o Kit de Ferramentas do Teams para Visual Studio, você precisará baixar e instalar o [Visual Studio 2022](https://aka.ms/VSDownload) usando o Instalador do Visual Studio.

::: zone-end

::: zone pivot="visual-studio-code"

## <a name="install-teams-toolkit-for-visual-studio-code"></a>Instale o Kit de ferramentas do Teams para o Visual Studio Code

Você pode instalar o Kit de Ferramentas do Teams usando a janela Extensões no Visual Studio Code ou instalá-lo no Visual Studio Marketplace.

# <a name="visual-studio-code"></a>[Código do Visual Studio](#tab/vscode)

1. Inicie **Visual Studio Code**.
1. Abra a janela Extensões (**Ctrl+Shift+X** / **⌘⇧-X** ou **Exibir > Extensões**).

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-1.png" alt-text="Captura de tela que mostra como instalar.":::

1. Insira **o Kit de Ferramentas do Teams** na caixa de pesquisa.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-toolkit2.png" alt-text="Captura de tela que mostra o Kit de Ferramentas.":::

1. Selecione **Instalar**.
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-install-ttk.png" alt-text="A captura de tela mostra o kit de ferramentas de instalação 4.0.0.":::

   Após a instalação bem-sucedida do Kit de Ferramentas do Teams no Visual Studio Code, um ícone do Kit de Ferramentas do Teams é exibido na barra Visual Studio Code ferramentas.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/after-install.png" alt-text="A captura de tela mostra após a exibição de instalação.":::

# <a name="marketplace"></a>[Mercado](#tab/marketplace)

1. Acesse o [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) em um navegador da Web.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-ttk-marketplace.png" alt-text="Captura de tela que mostra a instalação do TTK Marketplace.":::

1. Selecione **Instalar**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/Install-ttk.png" alt-text="Captura de tela que mostra como instalar o TTK.":::

1. Na janela pop-up, selecione **Abrir** para iniciar Visual Studio Code.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-open.png" alt-text="A captura de tela mostra a opção abrir.":::

   A página de extensão do Kit de Ferramentas do Teams é mostrada Visual Studio Code:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/ttk-in-vsc.png" alt-text="A captura de tela mostra como selecionar o TTK na VSC.":::

1. Selecione **Instalar**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-install-ttk.png" alt-text="A captura de tela mostra como selecionar Instalar o TTK na VSC.":::

   Após a instalação bem-sucedida do Kit de Ferramentas do Teams no Visual Studio Code, um ícone do Kit de Ferramentas do Teams é exibido na barra Visual Studio Code ferramentas.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/after-install.png" alt-text="Captura de tela que mostra o modo de exibição após a instalação.":::

---

## <a name="installing-a-different-release-version"></a>Instalando uma versão de versão diferente

Por padrão, Visual Studio Code mantém automaticamente o Kit de Ferramentas do Teams atualizado. Se você quiser instalar uma versão diferente, siga as etapas:

* Selecione o ícone Extensões (:::image type="icon" source="../assets/images/teams-toolkit-v2/extension icon.PNG":::) na barra Visual Studio Code ferramentas.
* Insira **o Kit de Ferramentas do Teams**  na caixa de pesquisa.
* Na página kit de ferramentas do Teams, selecione a seta suspensa ao lado do botão **Desinstalar** .
* Selecione **Instalar Outra Versão...** no menu e escolha qual versão instalar.

## <a name="installing-a-pre-release-version"></a>Instalando uma versão de pré-lançamento

O Kit de Ferramentas do Teams Visual Studio Code extensão também está disponível no GitHub. Para baixar pré-lançamentos, acesse a página Versões no [GitHub](https://github.com/OfficeDev/TeamsFx/releases) e procure downloads de extensão marcados como Pré-lançamento.

::: zone-end

::: zone pivot="visual-studio"

## <a name="install-teams-toolkit-for-visual-studio"></a>Instalar o Kit de ferramentas do Teams para Visual Studio

   > [!IMPORTANT]
   > É recomendável usar o Visual Studio 2022 versão 17.3.3 ou mais recente para o Kit de Ferramentas do Teams, que é a versão mais recente para corrigir vários problemas conhecidos em versões anteriores do Visual Studio.

1. [Baixe o instalador do Visual Studio](https://aka.ms/VSDownload) ou abra-o se já estiver instalado.
2. Selecione **Instalar** ou **Modificar se** o Visual Studio já estiver instalado.
3. Selecione a **guia Cargas de** Trabalho e, em seguida, selecione a ASP.NET **e a carga de trabalho de desenvolvimento na** Web.
4. À direita, selecione as **ferramentas de desenvolvimento do Microsoft Teams** na **seção** Opcional do **painel Detalhes da** instalação.
5. Selecione **Modificar** **ou Instalar** para concluir a instalação.

   :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-install_1.png" alt-text="Captura de tela que mostra como instalar o Visual Studio.":::

6. Após a conclusão da instalação, selecione **Iniciar** para abrir o Visual Studio..

    :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-launch_1.png" alt-text="Captura de tela que mostra como iniciar o Visual Studio.":::

::: zone-end

## <a name="next-steps"></a>Próximas etapas

Agora que o Kit de Ferramentas do Teams está instalado, visite [Criar um novo projeto do Teams](create-new-project.md) para começar.

## <a name="see-also"></a>Confira também

* [Explorar o Kit de Ferramentas do Teams](explore-Teams-Toolkit.md)
* [Criar um novo aplicativo Teams usando o Kit de Ferramentas do Teams](create-new-project.md)
* [Preparar-se para criar aplicativos usando o Kit de Ferramentas do Microsoft Teams](build-environments.md)
* [Provisionar recursos de nuvem usando o Kit de Ferramentas do Teams](provision.md)
* [Implantar o aplicativo Teams na nuvem](deploy.md)
* [Criar um novo aplicativo teams no Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
* [Implantar o aplicativo Teams na nuvem usando o Visual Studio](deploy-teams-app.md)
