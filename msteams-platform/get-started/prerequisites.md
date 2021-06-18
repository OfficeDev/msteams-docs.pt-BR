---
title: Começar - Pré-requisitos
author: adrianhall
description: Saiba como começar com o desenvolvimento de aplicativos do Microsoft Teams e configurar seu ambiente.
ms.author: adhal
ms.date: 05/24/2021
ms.topic: quickstart
ms.openlocfilehash: 6496d238b3858c1df974732fa57c28eed7c54eb2
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994186"
---
# <a name="prerequisites-get-started-with-microsoft-teams-app-development"></a>Pré-requisitos: começar com o desenvolvimento de aplicativos do Microsoft Teams

Antes de criar seu primeiro aplicativo do Teams, você deve instalar algumas ferramentas e configurar seu ambiente de desenvolvimento.

## <a name="install-required-tools"></a>Instalar ferramentas necessárias

Algumas das ferramentas de que você precisa dependem de como você prefere criar seu aplicativo do Teams:

- [Node.js](https://nodejs.org/en/download/) (use a versão mais recente do v14 LTS)
- Um navegador com ferramentas de desenvolvedor - como [o Microsoft Edge](https://www.microsoft.com/edge) (recomendado) ou o Google [Chrome](https://www.google.com/chrome/)
- Se você estiver desenvolvendo com JavaScript, TypeScript ou a Estrutura do SharePoint (SPFx), instale Visual Studio [Code](https://code.visualstudio.com/download), versão 1.55 ou posterior.  
- Se você estiver desenvolvendo com o .NET, instale [Visual Studio 2019](https://visualstudio.com/download). Certifique-se de instalar o **ASP.NET e desenvolvimento da Web** ou a carga de trabalho de desenvolvimento entre **plataformas do .NET Core.**

> [!WARNING]
> Há problemas conhecidos com `npm@7` , empacotado com o Nó v15 e posterior. Se você tiver problemas em `npm install` execução, verifique se está usando o Nó v14 (LTS)

## <a name="install-the-teams-toolkit"></a>Instalar o teams Toolkit

O teams Toolkit ajuda a simplificar o processo de desenvolvimento com ferramentas para provisionar e implantar recursos de nuvem para seu aplicativo, publicar na loja do Teams e muito mais. Você pode usar o kit de ferramentas com Visual Studio Código, Visual Studio ou como uma CLI (chamada `teamsfx` ).

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abra o Visual Studio Code.
1. Selecione o exibição Extensões (**Ctrl+Shift+X**  /  **⌘⇧-X** ou **Exibir > Extensões).**
1. Na caixa de pesquisa, digite **Teams Toolkit**.
1. Selecione o botão de instalação verde ao lado do teams Toolkit.

Você também pode encontrar o teams Toolkit no [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

As ferramentas a seguir podem ser instaladas pela extensão Visual Studio Code quando elas são necessárias. Se já estiver instalada, a versão instalada poderá ser usada em vez disso. Se estiver usando o Linux, incluindo o WSL, você deve instalar essas ferramentas antes de usar:

- [Ferramentas principais das funções do Azure](/azure/azure-functions/functions-run-local)

    As Ferramentas Principais de Funções do Azure são usadas para executar qualquer componente back-end localmente durante uma execução de depuração local, incluindo os auxiliares de autenticação necessários ao executar seus serviços no Azure. Ele é instalado no diretório do projeto (usando o npm `devDependencies` ).

- [.NET SDK](/dotnet/core/install/)

    O .NET SDK é usado para instalar vinculações personalizadas para implantações de aplicativos de depuração local e funções do Azure. Se você não tiver instalado o SDK .NET 3.1 (ou posterior) globalmente, a versão portátil poderá ser instalada.

- [ngrok](https://ngrok.com/download)

    Alguns recursos de aplicativo do Teams (bots de conversa, extensões de mensagens e webhooks de entrada) exigem conexões de entrada. Você precisa expor seu sistema de desenvolvimento ao Teams por meio de um túnel. Um túnel não é necessário para aplicativos que incluem apenas guias. Este pacote é instalado no diretório do projeto (usando npm `devDependencies` ).

# <a name="visual-studio-2019"></a>[Visual Studio 2019](#tab/vs)

Você pode usar o Visual Studio 2019 para desenvolver aplicativos do Teams com o Servidor Blazor no .NET. Se você não pretende desenvolver aplicativos do Teams no .NET, instale Visual Studio versão de código do Teams Toolkit.

Para instalar a extensão Toolkit teams:

1. Abra Visual Studio 2019.
1. Selecione **Extensões**  >  **Gerenciar Extensões**.
1. Na caixa de pesquisa, digite **Teams Toolkit**.
1. Selecione a extensão teams Toolkit e selecione **Baixar**.

A extensão pode ser baixada. Feche Visual Studio 2019 para instalar a extensão.

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

Instalar ferramentas de navegador para desenvolvimento de aplicativos. Por exemplo, se seu aplicativo for gravado com o React, você poderá usar As Ferramentas de Desenvolvedor do React:

- [Ferramentas de desenvolvedor do React para Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)

Se você quiser acessar dados armazenados no Azure ou implantar um back-end baseado em nuvem para seu aplicativo do Teams no Azure, instale estas ferramentas:

- [Ferramentas do Azure para Visual Studio Código](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)
- [Azure CLI](/cli/azure/install-azure-cli)

Se você trabalhar com dados do Microsoft Graph, você deve aprender sobre e marcar o Microsoft Graph Explorer. Essa ferramenta baseada em navegador permite consultar o Microsoft Graph fora de um aplicativo.

- [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)

Com o Portal do Desenvolvedor para o Teams, você pode configurar, gerenciar e distribuir seu aplicativo do Teams, incluindo para sua organização ou o armazenamento do Teams.

- [Portal do Desenvolvedor do Teams](https://dev.teams.microsoft.com/)

## <a name="enable-sideloading"></a>Habilitar o sideload

Durante o desenvolvimento, você deve carregar seu aplicativo no Teams sem distribuí-lo. Isso é conhecido como "sideloading".

1. Se você tiver uma conta do Teams, verifique se pode fazer sideload de aplicativos no Teams:

    1. No cliente do Teams, selecione **Aplicativos**.
    1. Procure uma opção para **Carregar um aplicativo personalizado.**

    :::image type="content" source="~/assets/images/teams-toolkit-v2/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde no Teams você pode carregar um aplicativo personalizado.":::

> [!NOTE]
> Se você ainda não puder fazer sideload de aplicativos, fale com o administrador do Teams. Confira [habilitar aplicativos personalizados do Teams e ativar](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) o carregamento personalizado de aplicativos para obter detalhes.

## <a name="get-a-free-teams-developer-tenant-optional"></a>Obter um locatário de desenvolvedor gratuito do Teams (opcional)

Se você não puder ver a opção de sideload ou se não tiver uma conta do Teams, poderá obter uma conta de desenvolvedor gratuita do Teams in joining the M365 developer program.  O processo de registro leva aproximadamente dois minutos.

1. Vá para o programa de desenvolvedor do [Microsoft 365](https://developer.microsoft.com/microsoft-365/dev-program).
1. Selecione **Ingressar agora** e siga as instruções na tela.
1. Quando você chegar à tela de boas-vindas, selecione **Configurar assinatura do E5**.
1. Configurar sua conta de administrador. Depois de concluir, você deverá ver uma tela como esta.

    :::image type="content" source="~/assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê depois de se inscrever no programa de desenvolvedor do Microsoft 365.":::

1. Entre no Teams usando a conta de administrador que você acabou de configurar.
1. Verifique se agora você tem **a opção Carregar um aplicativo** personalizado.

## <a name="get-a-free-azure-account"></a>Obter uma conta gratuita do Azure

Se você deseja hospedar seu aplicativo ou acessar recursos no Azure, deve ter uma assinatura do Azure.  Você pode [criar uma conta gratuita](https://azure.microsoft.com/free/) antes de começar.

## <a name="sign-in-to-your-microsoft-365-and-azure-accounts"></a>Entre em suas contas do Microsoft 365 e do Azure

Você deve ter acesso a duas contas:

- Suas credenciais de conta do Microsoft 365. Essa é a conta que você usa para entrar no Teams. Se você estiver usando um locatário de programa de desenvolvedor do Microsoft 365, essa é a conta de administrador que você configura quando se registrou no programa.
- - Suas credenciais do Azure. Essa é a conta que você usa para acessar o Portal do Azure e para provisionar novos recursos de nuvem para dar suporte ao aplicativo.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Abrir Visual Studio código
1. Selecione o Teams na barra lateral:

    :::image type="content" source="~/assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. Selecione **Entrar no M365**.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/account-commands.png" alt-text="Local da seção Contas usada para entrar.":::

1. O processo de login começa usando seu navegador da Web normal. Conclua o processo de login da sua conta M365. Você é solicitado quando pode fechar o navegador e retornar ao Visual Studio Code.
1. Retorne ao Teams Toolkit dentro Visual Studio Code.
1. Selecione **Entrar no Azure**.

    > [!TIP]
    > Se você tiver a extensão da Conta do Azure instalada e estiver usando a mesma conta, ignore esta etapa. Use a mesma conta que você está usando em outras extensões.

1. O processo de login começa usando seu navegador da Web normal.  Conclua o processo de login da sua conta do Azure. Você é solicitado quando pode fechar o navegador e retornar ao Visual Studio Code.

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

---

Agora que seu ambiente de desenvolvimento está configurado, você pode criar, criar e implantar seu primeiro Teams aplicativo.

## <a name="see-also"></a>Confira também

- [Criar seu primeiro Teams com o Blazor](first-app-blazor.md)
- [Crie seu primeiro Teams usando Estrutura do SharePoint (SPFx)](first-app-spfx.md)
- [Criar um programa bot de conversação](first-app-bot.md)
- [Criar uma extensão de mensagem](first-message-extension.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Crie seu primeiro Teams usando React](first-app-react.md)
