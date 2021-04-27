---
title: Começar - Criar e executar seu primeiro aplicativo
author: heath-hamilton
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe um "Hello, World!" usando a mensagem do Microsoft Teams Toolkit.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 1b34c3f3121e834abc8a8a92a8a0ac9a049c9e07
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020881"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Criar e executar seu primeiro aplicativo do Microsoft Teams

Inicie o desenvolvimento do Microsoft Teams criando uma guia pessoal que exibe "Hello, World!".
Crie e execute seu primeiro aplicativo do Teams usando as seguintes etapas:

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

Use o Microsoft Teams Toolkit código Visual Studio para configurar seu primeiro projeto de aplicativo. Crie seu projeto de aplicativo usando as seguintes etapas:

1. Em Visual Studio Código, selecione **Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos,** selecione **Tab** e **Next**.
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Captura de tela mostrando como configurar seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::
1. Insira um nome para seu aplicativo do Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.)
1. Marque apenas a **opção Guia Pessoal** e selecione **Concluir** na parte inferior da tela para configurar seu projeto.

## <a name="2-understand-important-app-project-components"></a>2. Entenda componentes importantes do projeto do aplicativo

Depois que o kit de ferramentas configurar seu projeto, você terá os componentes para criar uma guia pessoal básica para o Teams. Os diretórios e arquivos do projeto são exibidos na área Explorer do Visual Studio Code.

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para uma guia pessoal Visual Studio Code.":::

### <a name="app-scaffolding"></a>Scaffolding de aplicativos

O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a instalação.

Se você criar uma guia durante a instalação, por exemplo, o arquivo no diretório será importante porque ele lida com a inicialização e o `App.js` `src/components` roteamento do seu aplicativo. Ele chama o [SDK](../tabs/how-to/using-teams-client-sdk.md) do cliente JavaScript do Microsoft Teams para estabelecer comunicação entre seu aplicativo e o Teams.

### <a name="app-id"></a>ID do aplicativo

Configure seu aplicativo com o App Studio usando a ID do aplicativo do Teams. Encontre a ID no `teamsAppId` objeto, que está localizado no arquivo do seu `package.json` projeto.

## <a name="3-build-and-run-your-app"></a>3. Crie e execute seu aplicativo

Crie e execute seu aplicativo localmente para economizar tempo. Essas informações também estão disponíveis no kit de ferramentas `README` . Crie e execute seu aplicativo usando as seguintes etapas:

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Depois de concluído, há um **Compilado com êxito!** mensagem no terminal. Seu aplicativo está sendo executado em `https://localhost:3000` .

## <a name="4-sideload-your-app-in-teams"></a>4. Fazer sideload do aplicativo no Teams

Seu aplicativo está pronto para teste no Teams. Para fazer isso, você deve ter uma conta de desenvolvimento do Microsoft 365 que permita o sideload de aplicativos. Para obter mais informações sobre a abertura da conta, consulte [Conta de desenvolvimento do Teams.](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account) 

> [!TIP]
> Verifique se há problemas antes de fazer sideload do aplicativo, usando o recurso de validação no [App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), que está incluído no kit de ferramentas. Correção dos erros para fazer sideload com êxito do aplicativo.

Fazer sideload do aplicativo no Teams usando as seguintes etapas:

> [!NOTE]
> Para habilitar o sideload antes de fazer sideload do aplicativo no Teams, siga as etapas em [Ativar o sideload do aplicativo.](../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading)

1. Selecione a **chave F5** para iniciar um cliente Web do Teams Visual Studio Código.
1. Para exibir o conteúdo do aplicativo no Teams, especifique que onde seu aplicativo está sendo executado ( `localhost` ) é confiável:
   1. Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão) que foi aberta após pressionar **F5**.
   1. Vá para `https://localhost:3000/tab` e prossiga para a página.
1. Volte para o Teams. Na caixa de diálogo, selecione **Adicionar para que eu** instale seu aplicativo.
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Captura de tela mostrando um exemplo de aplicativo de guia pessoal &quot;Hello, World!&quot; em execução no Teams.":::

🎉 parabéns! Seu aplicativo está sendo executado no Teams.

## <a name="next-step"></a>Próxima etapa

Expanda na guia pessoal que você acabou de criar ou criar outro tipo de aplicativo do Teams.

> [!div class="nextstepaction"]
> [Adicionar à sua guia pessoal](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [Construir uma guia de canal](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)
