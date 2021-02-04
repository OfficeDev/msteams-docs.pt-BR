---
title: Começar - Criar e executar seu primeiro aplicativo
author: heath-hamilton
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe um "Hello, World!" usando o Kit de Ferramentas do Microsoft Teams.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 46a92f54cdbf68e28510c0bd4cc0b7018cfaae3c
ms.sourcegitcommit: 55a4246e62d69d631a63bdd33de34f1b62cc0132
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093947"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Criar e executar seu primeiro aplicativo Microsoft Teams

Inicie o desenvolvimento do Microsoft Teams criando uma guia pessoal que exibe "Olá, Mundo!".
Crie e execute seu primeiro aplicativo teams usando as seguintes etapas:

## <a name="1-create-your-app-project"></a>1. Crie seu projeto de aplicativo

Use o Kit de Ferramentas do Microsoft Teams no Visual Studio Code para configurar seu primeiro projeto de aplicativo. Crie seu projeto de aplicativo usando as seguintes etapas:

1. No Visual Studio Code, selecione **o Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos,** selecione **Tab** e **Next.**
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Screenshot showing how to configure your app project with the Visual Studio Code Teams Toolkit.":::
1. Insira um nome para seu aplicativo do Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em seu computador local.)
1. Marque somente a **opção de guia** Pessoal e selecione **Concluir** na parte inferior da tela para configurar seu projeto.

## <a name="2-understand-important-app-project-components"></a>2. Compreender componentes importantes do projeto do aplicativo

Depois que o kit de ferramentas configurar seu projeto, você terá os componentes para criar uma guia pessoal básica para o Teams. Os diretórios e arquivos do projeto são exibidos na área Explorer do Visual Studio Code.

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Captura de tela mostrando arquivos de projeto do aplicativo para uma guia pessoal no Visual Studio Code.":::

### <a name="app-scaffolding"></a>Scaffolding de aplicativos

O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a instalação.

Se você criar uma guia durante a instalação, por exemplo, o arquivo no diretório é importante porque ele lida com a inicialização e o roteamento `App.js` `src/components` do seu aplicativo. Ele chama o [SDK](../tabs/how-to/using-teams-client-sdk.md) do cliente JavaScript do Microsoft Teams para estabelecer a comunicação entre seu aplicativo e o Teams.

### <a name="app-id"></a>ID do aplicativo

Configure seu aplicativo com o App Studio usando a ID de aplicativo do Teams. Encontre a ID no `teamsAppId` objeto, que está localizado no arquivo do `package.json` projeto.

## <a name="3-build-and-run-your-app"></a>3. Crie e execute seu aplicativo

Crie e execute seu aplicativo localmente para economizar tempo. Essas informações também estão disponíveis no kit de `README` ferramentas. Crie e execute seu aplicativo usando as seguintes etapas:

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e `npm install` execute.
1. Executar `npm start` .

Depois de concluído, há um **compilado com êxito!** no terminal. Seu aplicativo está em `https://localhost:3000` execução.

## <a name="4-sideload-your-app-in-teams"></a>4. Fazer sideload do aplicativo no Teams

Seu aplicativo está pronto para ser testado no Teams. Para fazer isso, você deve ter uma conta de desenvolvimento do Microsoft 365 que permita o sideload do aplicativo. Para saber mais sobre como abrir conta, confira a conta [de desenvolvimento do Teams.](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account) 

> [!TIP]
> Verifique se há problemas antes de fazer o sideload do aplicativo, usando o recurso de validação no [App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), que está incluído no kit de ferramentas. Corrige os erros para fazer o sideload do aplicativo com êxito.

Fazer o sideload do aplicativo no Teams usando as seguintes etapas:

> [!NOTE]
> Para habilitar o sideload antes de fazer o sideload do aplicativo no Teams, siga as etapas em [Ativar sideload do aplicativo.](../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading)

1. Selecione a **tecla F5** para iniciar um cliente Web do Teams no Visual Studio Code.
1. Para exibir o conteúdo do aplicativo no Teams, especifique que onde o aplicativo está sendo executado ( `localhost` ) é confiável:
   1. Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão) que foi aberta após pressionar **F5**.
   1. Vá para `https://localhost:3000/tab` a página e prossiga para a página.
1. Volte para o Teams. Na caixa de diálogo, selecione **Adicionar para instalar** seu aplicativo.
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Screenshot showing an example 'Hello, World!' personal tab app running in Teams.":::

🎉 parabéns! Seu aplicativo está sendo executado no Teams.

## <a name="next-step"></a>Próxima etapa

Expanda a guia pessoal que você acabou de criar ou criar outro tipo de aplicativo do Teams.

> [!div class="nextstepaction"]
> [Adicionar à sua guia pessoal](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [Construir uma guia de canal](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)
