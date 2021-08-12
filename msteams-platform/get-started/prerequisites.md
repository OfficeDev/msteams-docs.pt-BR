---
title: Começar - Pré-requisitos
author: adrianhall
description: Saiba como começar com o desenvolvimento Microsoft Teams aplicativo e configurar seu ambiente.
ms.author: adhal
ms.date: 05/24/2021
ms.topic: quickstart
ms.openlocfilehash: 2945490d70023a620bad43b618789164aa915d8a
ms.sourcegitcommit: 6a41c529a423c81a184c7a79125dbaaed0179788
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2021
ms.locfileid: "53585995"
---
# <a name="prerequisites-get-started-with-microsoft-teams-app-development"></a>Pré-requisitos: começar a Microsoft Teams desenvolvimento de aplicativos

Antes de começar a criar seu primeiro Teams, você deve instalar algumas ferramentas e configurar seu ambiente de desenvolvimento.

## <a name="install-required-tools"></a>Instalar ferramentas obrigatórias

Algumas das ferramentas de que você precisa dependem de como você prefere criar seu Teams aplicativo:

- [Node.js](https://nodejs.org/en/download/) (use a versão mais recente do v14 LTS)
- Um navegador com ferramentas de desenvolvedor, como, [Microsoft Edge](https://www.microsoft.com/edge) (recomendado) ou [Google Chrome](https://www.google.com/chrome/)
- Se você estiver desenvolvendo com JavaScript, TypeScript ou o Estrutura do SharePoint (SPFx), instale Visual Studio Code [versão](https://code.visualstudio.com/download)1.55 ou posterior.  
- Se você estiver desenvolvendo com o .NET, [instale Visual Studio 2019](https://visualstudio.com/download). Certifique-se de instalar o **ASP.NET e desenvolvimento da Web** ou a carga de trabalho de desenvolvimento entre **plataformas do .NET Core.**

> [!WARNING]
> Há problemas conhecidos com `npm@7` , empacotado com o Nó v15 e posterior. Se você tiver problemas em `npm install` execução, verifique se está usando o Nó v14 (LTS)

## <a name="install-the-teams-toolkit"></a>Instalar o Teams Toolkit

O Teams Toolkit ajuda a simplificar o processo de desenvolvimento com ferramentas para provisionar e implantar recursos de nuvem para seu aplicativo, publicar no Teams store e muito mais. Você pode usar o kit de ferramentas com Visual Studio Code, Visual Studio ou como uma CLI (chamada `teamsfx` ). Para obter mais informações, [consulte Teams Toolkit for Visual Studio Code](../toolkit/visual-studio-code-overview.md), Teams Toolkit for [Visual Studio](../toolkit/visual-studio-overview.md) [e Teamsfx CLI Tool](https://github.com/OfficeDev/TeamsFx/tree/dev/packages/cli).

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abra o Visual Studio Code.
1. Selecione o **exibição Extensões** (**Ctrl+Shift+X**  /  **⌘⇧-X** ou **Exibir > Extensões).**
1. Na caixa de pesquisa, digite **Teams Toolkit**.
1. Selecione **Instalar** ao lado do Teams Toolkit.

Você também pode encontrar o Teams Toolkit no [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

As ferramentas a seguir podem ser instaladas pela extensão Visual Studio Code quando elas são necessárias. Se já estiver instalada, a versão instalada poderá ser usada em vez disso. Se estiver usando o Linux, incluindo o WSL, você deve instalar essas ferramentas antes de usar:

- [Ferramentas principais das funções do Azure](/azure/azure-functions/functions-run-local)

    As Ferramentas Principais de Funções do Azure são usadas para executar qualquer componente back-end localmente durante uma execução de depuração local, incluindo os auxiliares de autenticação necessários ao executar seus serviços no Azure. Ele é instalado no diretório do projeto (usando o npm `devDependencies` ).

- [.NET SDK](/dotnet/core/install/)

    O .NET SDK é usado para instalar vinculações personalizadas para implantações de aplicativos de depuração local e funções do Azure. Se você não tiver instalado o SDK .NET 3.1 (ou posterior) globalmente, a versão portátil poderá ser instalada.

- [ngrok](https://ngrok.com/download)

    Alguns Teams de aplicativo (bots de conversação, extensões de mensagens e webhooks de entrada) exigem conexões de entrada. Você precisa expor seu sistema de desenvolvimento para Teams através de um túnel. Um túnel não é necessário para aplicativos que incluem apenas guias. Este pacote é instalado no diretório do projeto (usando npm `devDependencies` ).

# <a name="visual-studio-2019"></a>[Visual Studio 2019](#tab/vs)

Você pode usar o Visual Studio 2019 para desenvolver Teams aplicativos com o Blazor Server no .NET. Se você não pretende desenvolver Teams aplicativos no .NET, instale Visual Studio Code versão do Teams Toolkit.

Para instalar a extensão Teams Toolkit:

1. Abra Visual Studio 2019.
1. Selecione **Extensões**  >  **Gerenciar Extensões**.
1. Na caixa de pesquisa, digite **Teams Toolkit**.
1. Selecione a Teams Toolkit e selecione **Baixar**. A extensão é baixada.
1. Feche Visual Studio 2019 para instalar a extensão.

# <a name="command-line"></a>[Linha de comando](#tab/cli)

Para instalar a CLI do TeamsFx, use o `npm` gerenciador de pacotes:

``` bash
npm install -g @microsoft/teamsfx-cli
```

Dependendo da configuração, talvez seja necessário usar `sudo` para instalar a CLI:

``` bash
sudo npm install -g --unsafe-perm @microsoft/teamsfx-cli
```

Isso é mais comum em sistemas Linux e macOS.

Certifique-se de adicionar o cache global npm ao seu PATH. Isso normalmente é feito como parte do Node.js instalador.  

Você pode usar a CLI com o `teamsfx` comando. Verifique se o comando está funcionando executando `teamsfx -h` .

> [!CAUTION]
> Antes de executar o TeamsFx em terminais do PowerShell, você deve habilitar a política de execução "assinada remotamente" para o PowerShell. Para obter mais informações, consulte a [documentação do PowerShell](/powershell/module/microsoft.powershell.core/about/about_signing).

---

## <a name="install-optional-tools"></a>Instalar ferramentas opcionais

Instalar ferramentas de navegador para desenvolvimento de aplicativos. Por exemplo, se seu aplicativo for escrito com React, você poderá usar React Ferramentas de Desenvolvedor:

- [React Ferramentas de desenvolvedor para Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)

Se você quiser acessar dados armazenados no Azure ou implantar um back-end baseado em nuvem para seu aplicativo Teams no Azure, instale estas ferramentas:

- [Ferramentas do Azure para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)
- [Azure CLI](/cli/azure/install-azure-cli)

Se você trabalhar com dados Graph microsoft, você deve aprender sobre e marcar o Microsoft Graph Explorer. Essa ferramenta baseada em navegador permite que você consulte o Microsoft Graph fora de um aplicativo.

- [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)

Com o Portal do Desenvolvedor para Teams, você pode configurar, gerenciar e distribuir seu aplicativo Teams, incluindo para sua organização ou o Teams store.

- [Portal do Desenvolvedor do Teams](https://dev.teams.microsoft.com/)

## <a name="enable-sideloading"></a>Habilitar o sideload

Durante o desenvolvimento, você deve carregar seu aplicativo dentro Teams sem distribuí-lo. Isso é conhecido como sideload.

Se você tiver uma Teams, verifique se pode fazer sideload de aplicativos Teams:

1. No cliente Teams, selecione **Aplicativos**.
1. Selecione **Upload um aplicativo personalizado.**

    :::image type="content" source="~/assets/images/teams-toolkit-v2/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde Teams você pode carregar um aplicativo personalizado.":::

> [!NOTE]
> Se você ainda não puder fazer sideload de aplicativos, fale com seu Teams administrador. Confira [habilitar Teams aplicativos personalizados](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) e ativar o carregamento personalizado de aplicativos para obter detalhes.

## <a name="get-a-free-teams-developer-tenant-optional"></a>Obter um locatário Teams desenvolvedor gratuito (opcional)

Se você não puder ver a opção de sideload ou não tiver uma conta Teams, você poderá obter uma conta de desenvolvedor gratuita Teams ingressar no programa de desenvolvedor do M365.  O processo de registro leva aproximadamente dois minutos.

1. Vá para o programa [Microsoft 365 desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)
1. Selecione **Ingressar agora** e siga as instruções na tela.
1. Na tela de boas-vindas, selecione **Configurar assinatura do E5**.
1. Configurar sua conta de administrador. Depois de concluir, você deverá ver uma tela como esta.

    :::image type="content" source="~/assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê depois de se inscrever no programa Microsoft 365 desenvolvedor.":::

1. Entre no Teams usando a conta de administrador que você acabou de configurar. Verifique se você tem a opção **Upload aplicativo** personalizado.

## <a name="get-a-free-azure-account"></a>Obter uma conta gratuita do Azure

Se você deseja hospedar seu aplicativo ou acessar recursos no Azure, deve ter uma assinatura do Azure.  Você pode [criar uma conta gratuita](https://azure.microsoft.com/free/) antes de começar.

## <a name="sign-in-to-your-microsoft-365-and-azure-accounts"></a>Entre em suas contas do Microsoft 365 e do Azure

Você deve ter acesso a duas contas:

- Suas Microsoft 365 de conta. Essa é a conta que você usa para entrar Teams. Se você estiver usando um locatário Microsoft 365 programa de desenvolvedor, essa é a conta de administrador que você configura quando se registrou no programa.
- Suas credenciais do Azure. Essa é a conta que você usa para acessar o Portal do Azure e para provisionar novos recursos de nuvem para dar suporte ao aplicativo.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abra Visual Studio Code
1. Selecione o Teams na barra lateral:

    :::image type="content" source="~/assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. Selecione **Entrar no M365**.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/account-commands.png" alt-text="Local da seção Contas usada para entrar.":::

    O processo de login começa usando seu navegador da Web normal. Conclua o processo de login da sua conta M365. Quando você é solicitado, você pode fechar o navegador e retornar ao Visual Studio Code.
1. Retorne ao Teams Toolkit dentro Visual Studio Code.
1. Selecione **Entrar no Azure**.

    > [!TIP]
    > Se você tiver a extensão da Conta do Azure instalada e estiver usando a mesma conta, ignore esta etapa. Use a mesma conta que você está usando em outras extensões.

1. O processo de login começa usando seu navegador da Web normal.  Conclua o processo de login da sua conta do Azure. Quando for solicitado, você poderá fechar o navegador e retornar ao Visual Studio Code.

    Quando concluída, a **seção ACCOUNTS** da barra lateral mostra as duas contas separadamente, juntamente com o número de assinaturas usáveis do Azure disponíveis para você. Certifique-se de ter pelo menos uma assinatura do Azure acessível disponível. Caso não, saia e use uma conta diferente.

# <a name="visual-studio-2019"></a>[Visual Studio 2019](#tab/vs)

Visual Studio 2019 solicita que você faça logoff em cada serviço conforme necessário. Você não precisa entrar em suas contas do M365 e do Azure com antecedência.

# <a name="command-line"></a>[Linha de comando](#tab/cli)

1. Entre no Microsoft 365 com a CLI teamsFx:

    ``` bash
    teamsfx account login m365
    ```

    O processo de login começa usando seu navegador da Web normal. Conclua o processo de login da sua conta M365. Você é solicitado quando pode fechar o navegador.

2. Entre no Azure com a CLI teamsFx:

    ``` bash
    teamsfx account login azure
    ```

    O processo de login começa usando seu navegador da Web normal. Conclua o processo de login da sua conta do Azure. Você é solicitado quando pode fechar o navegador.

    Os logons da conta são compartilhados entre Visual Studio Code e a CLI teamsFx.



    Agora que seu ambiente de desenvolvimento está configurado, você pode criar, criar e implantar seu primeiro Teams aplicativo.

## <a name="see-also"></a>Confira também

* [Visão geral dos tutoriais](code-samples.md) 
* [Criar um aplicativo usando React](first-app-react.md)
* [Criar um aplicativo usando o Blazor](first-app-blazor.md)
* [Criar um aplicativo usando SPFx](first-app-spfx.md)
* [Criar um aplicativo usando C# ou .NET](get-started-dotnet-app-studio.md)
* [Criar um aplicativo usando o Node.js](get-started-nodejs-app-studio.md)
* [Criar um aplicativo usando o gerador Yeoman](get-started-yeoman.md)
* [Criar um programa bot de conversação](first-app-bot.md)
* [Criar uma extensão de mensagem](first-message-extension.md)
* [Exemplos de código](https://github.com/OfficeDev/Microsoft-Teams-Samples)
