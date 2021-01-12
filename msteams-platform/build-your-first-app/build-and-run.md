---
title: Começar - Criar e executar seu primeiro aplicativo
author: heath-hamilton
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe um "Hello, World!" usando o Kit de Ferramentas do Microsoft Teams.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: bc5d18dd887cbdbf56b8d6d013f53c21d1540370
ms.sourcegitcommit: 5687a901d48bcf2f5a3a086e0f703f854e8b9c21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2021
ms.locfileid: "49795465"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Criar e executar seu primeiro aplicativo Microsoft Teams

Você pode entrar no desenvolvimento do Microsoft Teams criando uma guia pessoal que exibe "Hello, World!"

## <a name="1-create-your-app-project"></a>1. Criar seu projeto de aplicativo

Use o Kit de Ferramentas do Microsoft Teams no Visual Studio Code para configurar seu primeiro projeto de aplicativo.

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

Sua ID de aplicativo do Teams é necessária para configurar seu aplicativo com o App Studio. Você pode encontrar a ID no `teamsAppId` objeto, que está localizado no arquivo do `package.json` projeto.

## <a name="3-build-and-run-your-app"></a>3. Crie e execute seu aplicativo

No interesse de tempo, você criará e executará seu aplicativo localmente.

(Essas informações também estão disponíveis no kit de `README` ferramentas.)

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e `npm install` execute.
1. Executar `npm start` .

Depois de concluído, há um **compilado com êxito!** no terminal. Seu aplicativo está em `https://localhost:3000` execução.

## <a name="4-sideload-your-app-in-teams"></a>4. Fazer sideload do aplicativo no Teams

Seu aplicativo está pronto para ser testado no Teams. Para fazer isso, você deve ter uma conta que permita o sideload do aplicativo. (Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma conta [de desenvolvimento do Teams.)](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account)

> [!TIP]
> Antes de fazer o sideload do aplicativo, verifique se há problemas usando o recurso de validação no [App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), que está incluído no kit de ferramentas. Os erros devem ser corrigidos para fazer o sideload do aplicativo com êxito.

1. No Visual Studio Code, pressione a **tecla F5** para iniciar um cliente Web do Teams.
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
