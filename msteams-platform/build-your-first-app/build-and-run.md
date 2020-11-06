---
title: Introdução-compilar e executar seu primeiro aplicativo
author: heath-hamilton
description: Criar rapidamente um aplicativo do Microsoft Teams que exibe um "Olá, mundo!" mensagem usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 62c4bd950183ceb64fb30b528661cf84e9210d89
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931770"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Criar e executar seu primeiro aplicativo do Microsoft Teams

Você pode ir direto para o desenvolvimento do Microsoft Teams criando uma guia pessoal que exibe "Olá, mundo!"

## <a name="1-create-your-app-project"></a>1. criar seu projeto de aplicativo

Use o Microsoft Teams Toolkit no Visual Studio Code para configurar seu primeiro projeto de aplicativo.

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.
1. Na tela **Adicionar recursos** , selecione **Tab** e **Avançar**.
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Captura de tela mostrando como configurar seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::
1. Insira um nome para seu aplicativo do Microsoft Teams. (Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)
1. Marque somente a opção **guia pessoal** e selecione **concluir** na parte inferior da tela para configurar seu projeto.

## <a name="2-understand-important-app-project-components"></a>2. compreender os principais componentes do projeto de aplicativos

Quando o kit de ferramentas configura seu projeto, você tem os componentes para criar uma guia pessoal básica para o Microsoft Teams. Os diretórios e arquivos do projeto são exibidos na área do Explorer do Visual Studio Code.

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para uma guia pessoal no Visual Studio Code.":::

### <a name="app-scaffolding"></a>Aplicativo scaffolding

O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a configuração.

Se você criar uma guia durante a configuração, por exemplo, o `App.js` arquivo no `src/components` diretório é importante porque trata da inicialização e do roteamento do seu aplicativo. Ele chama o [SDK do Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre o seu aplicativo e o Teams.

### <a name="app-id"></a>ID do aplicativo

Sua ID de aplicativo do Microsoft Teams é necessária para configurar seu aplicativo com o app Studio. Você pode encontrar a ID no `teamsAppId` objeto, localizada no arquivo do seu projeto `package.json` .

## <a name="3-build-and-run-your-app"></a>3. Compilar e executar o aplicativo

Nos juros de tempo, você criará e executará seu aplicativo localmente.

(Essas informações também estão disponíveis no kit de ferramentas `README` .)

1. Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .
1. Executar `npm start` .

Após a conclusão, há uma **compilação bem-sucedida!** mensagem no terminal. O aplicativo está sendo executado `https://localhost:3000` .

## <a name="4-sideload-your-app-in-teams"></a>4. Sideload seu aplicativo no Microsoft Teams

Seu aplicativo está pronto para teste no Teams. Para fazer isso, você deve ter uma conta que permita o aplicativo Sideload. (Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma [conta de desenvolvimento do teams](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)

> [!TIP]
> Antes de fazer o Sideload do aplicativo, verifique se há problemas usando o [recurso de validação no app Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), que está incluído no kit de ferramentas. Os erros devem ser corrigidos para Sideload com êxito o aplicativo.

1. No Visual Studio Code, pressione a tecla **F5** para iniciar um cliente Web do teams.
1. Para exibir o conteúdo do aplicativo no Teams, especifique o local em que o aplicativo está em execução ( `localhost` ) é confiável:
   1. Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão), aberta após pressionar **F5**.
   1. Vá até `https://localhost:3000/tab` a página e vá até ela.
1. Volte para o Microsoft Teams. Na caixa de diálogo, selecione **Adicionar para mim** para instalar o aplicativo.
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Captura de tela mostrando um exemplo de aplicativo de guia pessoal &quot;Olá, mundo!&quot; executado no Teams.":::

🎉 Parabéns! Seu aplicativo está em execução no Microsoft Teams.

## <a name="next-step"></a>Próxima etapa

Expanda na guia pessoal que você acabou de criar ou criar outro tipo de aplicativo do teams.

> [!div class="nextstepaction"]
> [Adicionar à sua guia pessoal](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [Construir uma guia de canal](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [Construir um bot](../build-your-first-app/build-bot.md)
