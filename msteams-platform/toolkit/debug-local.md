---
title: Depurar seu aplicativo Teams
description: Depurar seu aplicativo Teams localmente no Kit de Ferramentas do Teams
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
ms.openlocfilehash: 25a851f0dcc956139551a46b713dc2e7df3f626d
ms.sourcegitcommit: 5e5d2d3fb621bcbd9d792a5b450f95167ec8548b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63731541"
---
# <a name="debug-your-teams-app-locally"></a>Depurar seu aplicativo Teams localmente

O Kit de Ferramentas do Teams ajuda você a depurar e visualizar seu aplicativo Teams localmente. Depurar é o processo de verificação, detecção e correção de problemas ou bugs para garantir que o programa seja executado com êxito. O Visual Studio Code permite depurar a guia, o bot, a extensão de mensagens e o Azure Functions. O Kit de Ferramentas do Teams dá suporte aos seguintes recursos de depuração:

* [Iniciar depuração](#start-debugging)
* [Depuração de vários destinos](#multi-target-debugging)
* [Alternar pontos de interrupção](#toggle-breakpoints)
* [Recarga dinâmica](#hot-reload)
* [Parar a depuração](#stop-debugging)  


Durante o processo de depuração, o Kit de Ferramentas do Teams inicia automaticamente os serviços de aplicativo, inicia os depuradores e faz o sideload do aplicativo Teams. O aplicativo Teams está disponível para visualização no cliente Web do Teams localmente após a depuração. Você também pode personalizar as configurações de depuração para usar seus pontos de extremidade de bot, certificado de desenvolvimento ou componente parcial de depuração para carregar seu aplicativo configurado.

## <a name="prerequisite"></a>Pré-requisito

Instalar a [versão mais recente do Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

## <a name="key-features-of-teams-toolkit"></a>Principais recursos do Kit de Ferramentas do Teams

#### <a name="start-debugging"></a>Iniciar a depuração

Você pode executar uma única operação, selecione **F5** para iniciar a depuração. O Kit de Ferramentas do Teams começa verificando pré-requisitos, registrando o aplicativo Azure Active Directory, registrando o aplicativo Teams, registrando o bot, iniciando os serviços e iniciando o navegador.

#### <a name="multi-target-debugging"></a>Depuração de vários destinos

O Kit de Ferramentas do Teams utiliza o recurso de depuração de vários destinos para depurar a guia, o bot, a extensão de mensagens e o Azure Functions ao mesmo tempo.

#### <a name="toggle-breakpoints"></a>Alternar pontos de interrupção

Você pode alternar pontos de interrupção nos códigos-fonte de guias, bots, extensões de mensagens e funções do Azure. Os pontos de interrupção são executados quando você interage com o aplicativo Teams em um navegador da Web. A imagem a seguir mostra os pontos de interrupção de alternância:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/toggle-points.png" alt-text="alternar pontos de interrupção":::

#### <a name="hot-reload"></a>Recarga dinâmica

Você pode atualizar e salvar os códigos-fonte da guia, do bot, da extensão de mensagens e do Azure Functions ao mesmo tempo quando estiver depurando o aplicativo Teams. O aplicativo recarrega e o depurador é reanexado às linguagens de programação.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hot-reload.png" alt-text="recarga dinâmica para códigos-fonte":::

#### <a name="stop-debugging"></a>Parar a depuração

Ao concluir a depuração local, você pode selecionar **Parar** ou **Desconectar** na barra de ferramentas de depuração flutuante para interromper todas as sessões de depuração e encerrar tarefas. A imagem a seguir mostra a ação parar a depuração:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/stop-debug.png" alt-text="parar a depuração":::

## <a name="debug-your-teams-app-locally"></a>Depurar seu aplicativo Teams localmente

#### <a name="1-set-up-your-teams-toolkit"></a>1. Configurar o Kit de Ferramentas do Teams

Conclua as etapas a seguir para depurar seu aplicativo após a criação de um novo aplicativo usando o Kit de Ferramentas do Teams:

<br>

<details>
<summary><b>Windows</b></summary>

1. Selecione **Depurar o Edge** ou **Depurar o Chrome** em **Executar e Depurar** na barra de atividades.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Opção de navegador" border="false":::

1. Selecione **Iniciar Depuração (F5)** ou **Executar** para executar seu aplicativo Teams no modo de depuração.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Iniciar depuração" border="false":::

3. Selecione **Entrar** para sua conta Microsoft 365.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Entrar" border="true":::


   > [!TIP]
   > Você pode selecionar **Ler mais** para saber mais sobre o Programa para Desenvolvedores do Microsoft 365. O navegador da Web padrão é aberto para permitir que você entre na sua conta Microsoft 365 usando suas credenciais.

4. Selecione **Instalar** para a instalação do certificado de desenvolvimento para localhost.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="certificado" border="true":::

   > [!TIP]
   > Você pode selecionar **Saiba mais** para saber mais sobre o certificado de desenvolvimento.

5. Selecione **Sim** se a caixa de diálogo a seguir for exibida:

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/development-certificate.png" alt-text="autoridade de certificação" border="true":::

O Kit de Ferramentas inicia uma nova instância do navegador Edge ou Chrome, dependendo da seleção e abre uma página da Web para carregar o cliente do Teams.  

</details>

<details>
<summary><b>macOS</b></summary>

1. Selecione **Depurar o Edge** ou **Depurar o Chrome** em **Executar e Depurar** na barra de atividades.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Listas de navegadores" border="false":::

1. Selecione **Iniciar Depuração (F5)** ou **Executar** para executar seu aplicativo Teams no modo de depuração.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Depurar seu aplicativo" border="false":::

3. Selecione **Entrar** para sua conta Microsoft 365.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Entrar na conta M365" border="true":::

   > [!TIP]
   > Você pode selecionar **Ler mais** para saber mais sobre o Programa para Desenvolvedores do Microsoft 365. O navegador da Web padrão é aberto para permitir que você entre na sua conta Microsoft 365 usando suas credenciais.

4. Selecione **Instalar** para instalar o certificado de desenvolvimento para localhost.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="certificado" border="true":::

   > [!TIP]
   > Você pode selecionar **Saiba mais** para saber mais sobre o certificado de desenvolvimento.

5. Insira seu **Nome de Usuário** e **Senha** e selecione **Atualizar Configurações** na caixa de diálogo a seguir:

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/mac-settings.png" alt-text="logon do mac" border="true":::

O Kit de Ferramentas inicia uma nova instância do navegador Edge ou Chrome, dependendo da seleção e abre uma página da Web para carregar o cliente do Teams. 

</details>


#### <a name="2-debug-your-app"></a>2. Depurar seu aplicativo 

Após o processo de configuração inicial, o Kit de Ferramentas do Teams inicia os seguintes processos:

  a. [Inicia serviços de aplicativo](#starts-app-services) </br>
  b. [Inicia depuradores](#launches-debuggers)   </br>
  c. [Faz o sideload do aplicativo Teams](#sideloads-the-teams-app)
        
#### <a name="starts-app-services"></a>Inicia serviços de aplicativo

Executa as tarefas definidas em `.vscode/tasks.json` da seguinte forma:

|  Componente |  Nome da tarefa  | Folder |
| --- | --- | --- |
|  Tab |  **Iniciar Front-end** |  guias |
|  Extensões de bot ou de mensagens |  **Iniciar Bot** |  bot |
|  Azure Functions |  **Iniciar Back-end** |  api |

A imagem a seguir exibe nomes de tarefas na guia **Terminal** de **Saída** do Visual Studio Code durante a execução da guia, do bot ou da extensão de mensagens e o Azure Functions.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/Terminal.png" alt-text="Iniciar serviços de aplicativo":::

#### <a name="launches-debuggers"></a>Inicia depuradores

Inicia as configurações de depuração definidas em `.vscode/launch.json` da seguinte forma:

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/launch-debuggers.png" alt-text="Iniciar depurador":::

A tabela a seguir lista os nomes e tipos de configuração de depuração do projeto com aplicativo de guia e aplicativo de bot:

|  Componente |  Nome da configuração de depuração  | Tipo de configuração de depuração |
| --- | --- | --- |
|  Tab |  **Anexar ao Front-end (Edge)** ou  **Anexar ao Front-end (Chrome)**  |  pwa-msedge ou pwa-chrome  |
|  Extensões de bot ou de mensagens |   **Anexar ao Bot** |  pwa-node |
| Azure Functions |   **Anexar ao Back-end** |  pwa-node |

A tabela a seguir lista os nomes e tipos de configuração de depuração do projeto com aplicativo bot e sem aplicativo de guia:

|  Componente |  Nome da configuração de depuração  | Tipo de configuração de depuração  |
| --- | --- | --- |
|  Bot ou extensão de mensagens  | **Iniciar Bot (Edge)** ou  **Iniciar Bot (Chrome)**  |   pwa-msedge ou pwa-chrome  |
|  Bot ou extensão de mensagens  |   **Anexar ao Bot** |  pwa-node  |
|  Azure Functions |  **Anexar ao Back-end** |  pwa-node |

#### <a name="sideloads-the-teams-app"></a>Faz o sideload do aplicativo Teams

A configuração **Anexar ao Front-end** ou **Iniciar Bot** inicia uma nova instância do navegador Edge ou Chrome e abre uma página da Web para carregar o cliente do Teams. Depois que o cliente do Teams é carregado, o Teams faz o sideload do aplicativo Teams controlado pela url de sideload definida nas configurações de inicialização do [Microsoft Teams](https://teams.microsoft.com/l/app/>${localTeamsAppId}?installAppPackage=true&webjoin=true&${account-hint}).  Quando o cliente do Teams for carregado no navegador da Web, selecione **Adicionar** ou selecione um na lista suspensa de acordo com seu requisito.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hello-local-debug.png" alt-text="depuração local" border="true":::

   Seu aplicativo foi adicionado ao Teams!

## <a name="customize-debug-settings"></a>Personalizar configurações de depuração

O Kit de Ferramentas do Teams permite personalizar as configurações de depuração para criar sua guia ou bot desmarcando alguns pré-requisitos:

<br>

<details>
<summary><b>Usar o ponto de extremidade do bot</b></summary>

1. Nas configurações do Visual Studio Code, desmarque **Verificar se Ngrok está instalado e foi iniciado (ngrok)**.

1. Defina a configuração botDomain e botEndpoint em `.fx/configs/localSettings.json` para seu domínio e ponto de extremidade.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/bot-endpoint.png" alt-text="Personalizar o ponto de extremidade do bot":::

</details>

<details>
<summary><b>Usar seu certificado de desenvolvimento</b></summary>

1. Nas configurações do Visual Studio Code, desmarque **Verificar se o certificado de desenvolvimento é confiável (devCert)**.

1. Defina a configuração sslCertFile e sslKeyFile em `.fx/configs/localSettings.json` no caminho do arquivo de certificado e no caminho do arquivo de chave.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/development-certificate-customize.png" alt-text="Personalizar certificado":::

</details>

<details>
<summary><b>Use seus scripts de início para iniciar os serviços de aplicativo</b></summary>

1. Para guia, atualize o script `dev:teamsfx` em `tabs/package.json`.

1. Para extensão de bot ou de mensagens, atualize o script `dev:teamsfx` em `bot/package.json`.

1. Para o Azure Functions, atualize o script `dev:teamsfx` em `api/package.json` e para o TypeScript, atualize o script `watch:teamsfx`.

   > [!NOTE]
   > Atualmente, a guia, o bot, os aplicativos de extensão de mensagens e portas do Azure Functions não dão suporte à personalização.

</details>

<details>
<summary><b>Adicionar variáveis de ambiente</b></summary>

Você pode adicionar variáveis de ambiente ao arquivo `.env.teamsfx.local` para guia, bot, extensão de mensagens e Azure Functions. O Kit de Ferramentas do Teams carrega as variáveis de ambiente adicionadas para iniciar serviços durante a depuração local.

 > [!NOTE]
 > Certifique-se de iniciar uma nova depuração local depois de adicionar novas variáveis de ambiente, pois elas não dão suporte à recarga dinâmica.

</details>

<details>
<summary><b>Depurar componente parcial</b></summary>


O Kit de Ferramentas do Teams utiliza a depuração de vários destinos do Visual Studio Code para depurar a guia, o bot, a extensão de mensagens e o Azure Functions ao mesmo tempo. Você pode atualizar `.vscode/launch.json` e `.vscode/tasks.json` para depurar componente parcial. Se você quiser depurar a guia somente em uma guia mais bot com o projeto do Azure Functions, use as seguintes etapas:

1. Comentário **Anexar ao Bot** e **Anexar ao Back-end** do composto de depuração em `.vscode/launch.json`

   ```json
   {
       "name": "Debug (Edge)",
        "configurations": [
           "Attach to Frontend (Edge)",
           // "Attach to Bot",
           // "Attach to Backend""
           ],
           "preLaunchTask": "Pre Debug Check & Start All",
           "presentation": {
               "group": "all",
               "order": 1
           },
           "stopAll": true

   }
   ```

2. Comentário **Iniciar Back-end** e Iniciar Bot a partir da tarefa Iniciar Tudo em .vscode/tasks.json

   ```json
   {
                                           
       "label": "Start All",
       "dependsOn": [
           "Start Frontend",
             // "Start Backend",
             // "Start Bot"

         ]
              
   }
   ```

</details>


## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Depurar processo em segundo plano](debug-background-process.md).

## <a name="see-also"></a>Confira também

* [Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem](provision.md)
* [Adicionar recursos aos aplicativos do Teams](add-capability.md)
* [Implantar na nuvem](deploy.md)
* [Gerenciar vários ambientes no Kit de Ferramentas do Teams](TeamsFx-multi-env.md)
