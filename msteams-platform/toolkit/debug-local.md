---
title: Depurar seu aplicativo Teams localmente
author: surbhigupta
description: 'Neste módulo, você aprenderá a depurar seu aplicativo Teams localmente no Kit de Ferramentas do Teams e conhecerá os principais recursos desse kit '
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 65eb9599bb60b35448aaf1b6239fc155b7d397d5
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791570"
---
# <a name="debug-your-teams-app-locally"></a>Depurar seu aplicativo Teams localmente

O Teams Toolkit ajuda você a depurar e visualizar seu aplicativo do Microsoft Teams localmente. Durante o processo de depuração, o Teams Toolkit inicia automaticamente serviços de aplicativo, inicia depuradores e carrega lateralmente o aplicativo Teams. Você pode visualizar seu aplicativo do Teams no cliente Web do Teams localmente após a depuração.

::: zone pivot="visual-studio-code"

## <a name="debug-your-microsoft-teams-app-locally-for-visual-studio-code"></a>Depurar seu aplicativo do Microsoft Teams localmente para Visual Studio Code

O Teams Toolkit em Visual Studio Code fornece os recursos para automatizar a depuração do aplicativo teams localmente. O Visual Studio permite que você depure a guia, o bot e a extensão da mensagem. Você precisa configurar o Teams Toolkit antes de depurar seu aplicativo.

> [!NOTE]
>
> Você pode atualizar seu projeto antigo do Teams Toolkit para usar novas tarefas, para obter mais informações, consulte [doc configurações de depuração](https://aka.ms/teamsfx-debug-upgrade-new-tasks)

## <a name="set-up-your-teams-toolkit-for-debugging"></a>Configurar seu Kit de Ferramentas do Teams para depuração

As etapas a seguir ajudam você a configurar seu Kit de Ferramentas do Teams antes de iniciar o processo de depuração:

# <a name="windows"></a>[Windows](#tab/Windows)

1. Selecione **Depurar (Edge)** ou **Depurar (Chrome)** na barra de atividades da **RUN AND DEBUG ▷** drop down.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Opção de navegador":::

1. Selecione **Executar** > **Iniciar Depuração (F5)**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Iniciar depuração":::

3. Selecione **Entrar** para sua conta Microsoft 365.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Entrar":::

   > [!TIP]
   > Você pode selecionar **Ler mais** para saber mais sobre o Programa para Desenvolvedores do Microsoft 365. Seu navegador da Web padrão é aberto para permitir que você entre em sua conta do Microsoft 365 com suas credenciais.

4. Selecione **Instalar** para instalar o certificado de desenvolvimento para localhost.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="certificado":::

   > [!TIP]
   > Você pode selecionar **Saiba mais** para saber mais sobre o certificado de desenvolvimento.

5. Selecione **Sim** na caixa de diálogo **Aviso de Segurança** é exibida:

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/development-certificate.png" alt-text="autoridade de certificação":::

O Kit de Ferramentas inicia uma nova instância do navegador Edge ou Chrome com base na sua seleção e abre uma página da Web para carregar o cliente do Teams.  

# <a name="macos"></a>[macOS](#tab/macOS)

1. Selecione **Depurar Borda** ou **Depurar Chrome** no **RUN AND DEBUG ▷** suspenso.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Listas de navegadores":::

1. Selecione **Iniciar Depuração (F5)** ou **Executar** para executar seu aplicativo Teams no modo de depuração.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Depurar seu aplicativo":::

3. Selecione **Entrar** para sua conta Microsoft 365.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Entrar na conta M365":::

   > [!TIP]
   > Você pode selecionar **Ler mais** para saber mais sobre o Programa para Desenvolvedores do Microsoft 365. Seu navegador da Web padrão está aberto para permitir que você entre na sua conta do Microsoft 365 usando suas credenciais.

4. Selecione **Instalar** para instalar o certificado de desenvolvimento para localhost.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="certificado":::

   > [!TIP]
   > Você pode selecionar **Saiba mais** para saber mais sobre o certificado de desenvolvimento.

5. Insira seu **Nome de Usuário** e **Senha** e selecione **Atualizar Configurações**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/mac-settings.png" alt-text="logon do mac":::

O Teams Toolkit inicia sua instância do navegador e abre uma página da Web para carregar o cliente do Teams.

---

## <a name="debug-your-app"></a>Depurar seu aplicativo

Após o processo de configuração inicial, o Teams Toolkit inicia os seguintes processos:

* [Inicia serviços de aplicativo](#starts-app-services)
* [Inicia configurações de depuração](#launches-debug-configurations)
* [Faz o sideload do aplicativo Teams](#sideloads-the-teams-app)

### <a name="starts-app-services"></a>Inicia serviços de aplicativo

Executa tarefas conforme definido em `.vscode/tasks.json`.

|  Componente |  Nome da tarefa  | Folder |
| --- | --- | --- |
|  Tab |  **Iniciar Front-end** |  guias |
|  Bot ou extensões de mensagens |  **Iniciar Bot** |  bot |
|  Azure Functions |  **Iniciar Back-end** |  API |

A imagem a seguir exibe nomes de tarefa nas guias **OUTPUT** e **TERMINAL** do Visual Studio Code durante a execução da guia, bot ou extensão de mensagem e Azure Functions.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/Terminal1.png" alt-text="Iniciar serviços de aplicativo" lightbox="../assets/images/teams-toolkit-v2/debug/Terminal1.png":::

### <a name="launches-debug-configurations"></a>Inicia configurações de depuração

Inicia as configurações de depuração conforme definido em `.vscode/launch.json`.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/launch-debuggers.png" alt-text="Iniciar depurador":::

A tabela a seguir lista os nomes e tipos de configuração de depuração para projeto com guia, bot ou aplicativo de extensão de mensagem e Azure Functions:

|  Componente |  Nome da configuração de depuração  | Tipo de configuração de depuração |
| --- | --- | --- |
|  Tab |  **Anexar ao Front-end (Edge)** ou  **Anexar ao Front-end (Chrome)**  |  pwa-msedge ou pwa-chrome  |
|  Bot ou extensões de mensagens |   **Anexar ao Bot** |  pwa-node |
| Azure Functions |   **Anexar ao Back-end** |  pwa-node |

A tabela a seguir lista os nomes e tipos de configuração de depuração para o projeto com o aplicativo bot, Azure Functions e sem aplicativo de guias:

|  Componente |  Nome da configuração de depuração  | Tipo de configuração de depuração  |
| --- | --- | --- |
|  Bot ou extensão de mensagem  | **Iniciar Bot (Edge)** ou  **Iniciar Bot (Chrome)**  |   pwa-msedge ou pwa-chrome  |
|  Bot ou extensão de mensagem  |   **Anexar ao Bot** |  pwa-node  |
|  Azure Functions |  **Anexar ao Back-end** |  pwa-node |

### <a name="sideloads-the-teams-app"></a>Faz o sideload do aplicativo Teams

A configuração **Anexar ao Frontend** ou **Iniciar Bot** inicia uma instância do navegador Edge ou Chrome para carregar o cliente do Teams na página da Web. Depois que o cliente do Teams é carregado, o Teams carrega o aplicativo Teams controlado pela URL de sideload definida nas configurações de inicialização do [Microsoft Teams](https://teams.microsoft.com/l/app/>${localTeamsAppId}?installAppPackage=true&webjoin=true&${account-hint}). Quando o cliente do Teams for carregado no navegador da Web, selecione **Adicionar** ou selecione uma opção na lista suspensa de acordo com seus requisitos.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hello-local-debug.png" alt-text="Adicionar depuração local" lightbox="../assets/images/teams-toolkit-v2/debug/hello-local-debug.png":::

   Seu aplicativo foi adicionado ao Teams!

## <a name="next"></a>Avançar

> [!div class="nextstepaction"]
> [Depurar processos em segundo plano](debug-background-process.md)

::: zone-end

::: zone pivot="visual-studio"

## <a name="debug-your-teams-app-locally-using-visual-studio"></a>Depurar seu aplicativo teams localmente usando o Visual Studio

O Teams Toolkit ajuda você a depurar e visualizar seu aplicativo do Microsoft Teams localmente. O Visual Studio permite que você depure a guia, o bot e a extensão da mensagem. Você pode depurar seu aplicativo localmente no Visual Studio usando o Teams Toolkit executando:

### <a name="set-up-ngrok-only-for-bot-and-message-extension-app"></a>Configurar o ngrok (somente para bot e aplicativo de extensão de mensagem)

Use um prompt de comando para executar este comando:

```
ngrok http 5130
```

### <a name="set-up-your-teams-toolkit"></a>Configure seu Kit de Ferramentas do Teams

Execute as seguintes etapas usando o Kit de Ferramentas do Teams para depurar seu aplicativo depois de criar um projeto:

1. Clique com o botão direito do mouse em seu **projeto**.
1. Selecione **Teams Toolkit** > **Prepare Teams App Dependencies**.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-teamsappdependencies.png" alt-text="Dependências de aplicativo do Teams para depuração local" lightbox="../assets/images/debug-teams-app/vs-localdebug-teamsappdependencies.png":::

   > [!NOTE]
   > Nesse cenário, o nome do projeto é MyTeamsApp1

   Sua conta do Microsoft 365 precisa ter a permissão de carregamento lateral antes de entrar.  Verifique se o aplicativo teams pode ser carregado no locatário, caso contrário, seu aplicativo teams pode falhar ao ser executado no Cliente do Teams.

1. Entre na conta do **Microsoft 365** e selecione **Continuar**

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-signin-m365.png" alt-text="Entrar na conta do Microsoft 365":::

   > [!Note]
   > Saiba mais sobre a permissão de sideload visitando <https://aka.ms/teamsfx-sideloading-option>.

1. Selecione **Depurar** > **Iniciar Depuração** ou selecione **F5** diretamente.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-Startdebug.png" alt-text="Iniciar a depuração":::

   O Visual Studio inicia o aplicativo Teams dentro do cliente do Microsoft Teams em seu navegador.

   > [!Note]
   > Saiba mais visitando <https://aka.ms/teamsfx-vs-debug>.

1. Depois que o Microsoft Teams for carregado, selecione **Adicionar** para instalar seu aplicativo no Teams.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-add-loadapp.png" alt-text="Selecione adicionar ao aplicativo de carga":::

   > [!TIP]
   > Você também pode usar a função de recarga quente do Visual Studio durante a depuração. Saiba mais visitando <https://aka.ms/teamsfx-vs-hotreload>.

   > [!NOTE]
   > Certifique-se de postar a solicitação HTTP para `http://localhost:5130/api/notification` disparar a notificação quando você estiver depurando o aplicativo Bot de Notificação. Se você tiver selecionado o gatilho HTTP ao criar o projeto, poderá usar todas as ferramentas de API, como curl (Prompt de Comando do Windows), Postman e assim por diante.

   > [!TIP]
   > Se você fizer alterações no arquivo de manifesto do aplicativo teams (/templates/appPackage/manifest.template.json), verifique se você executa o comando Preparar Dependências de Aplicativo do Teams. Antes de tentar executar o aplicativo teams novamente localmente.

::: zone-end

## <a name="see-also"></a>Confira também

* [Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem](provision.md)
* [Adicionar recursos aos aplicativos do Teams](add-capability.md)
* [Implantar na nuvem](deploy.md)
* [Gerenciar vários ambientes no Kit de Ferramentas do Teams](TeamsFx-multi-env.md)
