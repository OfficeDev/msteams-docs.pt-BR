---
title: Depurar seu aplicativo Teams
author: surbhigupta
description: Neste módulo, saiba como depurar seu aplicativo teams no Teams Toolkit e os principais recursos do Teams Toolkit
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 111f45a8ed0b5246a75d1a1adbda9b124c1e9578
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833146"
---
# <a name="debug-your-teams-app"></a>Depurar seu aplicativo Teams

O Teams Toolkit ajuda você a depurar e visualizar seu aplicativo do Microsoft Teams. Depuração é o processo de verificação, detecção e correção de problemas ou bugs para garantir que o programa seja executado com êxito no Teams.

::: zone pivot="visual-studio-code"

## <a name="debug-your-teams-app-for-visual-studio-code"></a>Depurar seu aplicativo teams para Visual Studio Code

O Teams Toolkit na Microsoft Visual Studio Code automatiza o processo de depuração. Você pode detectar erros e corrigi-los, bem como visualizar o aplicativo teams. Você também pode personalizar as configurações de depuração para criar sua guia ou bot.

## <a name="debug-your-microsoft-teams-app-for-visual-studio-code"></a>Depurar seu aplicativo do Microsoft Teams para Visual Studio Code

O Teams Toolkit no Visual Studio Code automatiza o processo de depuração. Você pode detectar erros e corrigi-los, bem como visualizar o aplicativo teams. Você também pode personalizar as configurações de depuração para criar sua guia ou bot.

Durante o processo de depuração:

* O Teams Toolkit inicia automaticamente os serviços de aplicativo, inicia depuradores e carrega o aplicativo Teams automaticamente.
* O Teams Toolkit verifica os pré-requisitos durante o processo de depuração em segundo plano.
* Seu aplicativo teams está disponível para visualização no cliente Web do Teams localmente após a depuração.
* Você também pode personalizar as configurações de depuração para usar seus pontos de extremidade de bot, certificado de desenvolvimento ou componente parcial de depuração para carregar seu aplicativo configurado.
* O Microsoft Visual Studio Code permite que você depure guia, bot, extensão de mensagem e Azure Functions.

## <a name="key-debug-features-of-teams-toolkit"></a>Principais recursos de depuração do Teams Toolkit

O Kit de Ferramentas do Teams dá suporte aos seguintes recursos de depuração:

* [Iniciar depuração](#start-debugging)
* [Depuração de vários destinos](#multi-target-debugging)
* [Alternar pontos de interrupção](#toggle-breakpoints)
* [Recarga dinâmica](#hot-reload)
* [Parar a depuração](#stop-debugging)

O Teams Toolkit executa funções em segundo plano durante o processo de depuração, que incluem a verificação dos pré-requisitos necessários para depuração. Você pode ver o progresso do processo de verificação no canal de saída do Teams Toolkit. No processo de instalação, você pode registrar e configurar seu aplicativo do Teams.

### <a name="start-debugging"></a>Iniciar a depuração

Você pode pressionar **F5** como uma única operação para iniciar a depuração. O Kit de Ferramentas do Teams começa a verificar os pré-requisitos, registra o aplicativo do Azure AD, o aplicativo do Teams e registra o bot, inicia os serviços e inicia o navegador.

### <a name="multi-target-debugging"></a>Depuração de vários destinos

O Kit de Ferramentas do Teams utiliza o recurso de depuração de vários destinos para depurar a guia, o bot, a extensão de mensagem e o Azure Functions ao mesmo tempo.

### <a name="toggle-breakpoints"></a>Alternar pontos de interrupção

Você pode alternar pontos de interrupção nos códigos-fonte das guias, bots, extensões de mensagens e do Azure Functions. Os pontos de interrupção são executados quando você interage com o aplicativo Teams em um navegador da Web. A imagem a seguir mostra o ponto de interrupção de alternância:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/toggle-points.png" alt-text="alternar pontos de interrupção" lightbox="../assets/images/teams-toolkit-v2/debug/toggle-points.png":::

### <a name="hot-reload"></a>Recarga dinâmica

Você pode atualizar e salvar os códigos-fonte de guia, bot, extensão de mensagem e Azure Functions ao mesmo tempo ao depurar o aplicativo teams. O aplicativo recarrega e o depurador é reanexado às linguagens de programação.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hot-reload.png" alt-text="recarga dinâmica para códigos-fonte" lightbox="../assets/images/teams-toolkit-v2/debug/hot-reload.png":::

### <a name="stop-debugging"></a>Parar a depuração

Ao concluir a depuração local, você pode selecionar **Parar (Shift+F5)** ou **[Alt] Desconectar (Shift+F5)** na barra de ferramentas de depuração flutuante para interromper todas as sessões de depuração e encerrar tarefas. A imagem a seguir mostra a ação parar a depuração:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/stop-debug.png" alt-text="parar a depuração":::

## <a name="prepare-for-debug"></a>Preparar para depuração

As seguintes etapas ajudam você a se preparar para a depuração:

### <a name="sign-in-to-microsoft-365"></a>Entrar no Microsoft 365

Se você já se inscreveu no Microsoft 365, entre no Microsoft 365. Para obter mais informações, confira [Programa de desenvolvedor do Microsoft 365](tools-prerequisites.md#microsoft-365-developer-program)

### <a name="toggle-breakpoints"></a>Alternar pontos de interrupção

Verifique se você pode alternar pontos de interrupção nos códigos-fonte de guias, bots, extensões de mensagem e Azure Functions para obter mais informações, consulte [Alterne pontos de interrupção](#toggle-breakpoints)

## <a name="customize-debug-settings"></a>Personalizar configurações de depuração

O Teams Toolkit permite personalizar as configurações de depuração para criar sua guia ou bot. Para obter mais informações sobre a lista completa de opções personalizáveis, consulte [doc configurações de depuração](https://aka.ms/teamsfx-debug-tasks).

### <a name="customize-scenarios"></a>Personalizar cenários

<br>

<details>

<summary><b>Ignorar verificações de pré-requisito</b></summary>

 > `"prerequisites"``"Validate & install prerequisites"``"args"` > Em `.fx/configs/tasks.json` , atualize as verificações de pré-requisito que você deseja ignorar.

  :::image type="content" source="../assets/images/teams-toolkit-v2/debug/skip-prerequisite-checks.png" alt-text="ignorar as verificações de pré-requisito":::

</details>

<details>
<summary><b>Usar seu certificado de desenvolvimento</b></summary>

1. Em `.fx/configs/tasks.json`, desmarque em >  > `"prerequisites"``"devCert"` `"Validate & install prerequisites"``"args"`.
1. Defina "SSL_CRT_FILE" e "SSL_KEY_FILE" no caminho do arquivo de certificado e no `.env.teamsfx.local` caminho do arquivo de chave.

</details>

<details>
<summary><b>Personalizar args de instalação do npm</b></summary>

Em `.fx/configs/tasks.json`, defina npmInstallArgs em `"Install npm packages"`.
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/customize-npm-install.png" alt-text="Instalar pacote npm":::

</details>

<details>
<summary><b>Modificar portas</b></summary>

* Bot
  1. `"3978"` Pesquise em todo o projeto e procure por aparições em `tasks.json`, `ngrok.yml` e `index.js`.
  1. Substitua-o pela porta.
     :::image type="content" source="../assets/images/teams-toolkit-v2/debug/modify-ports-bot.png" alt-text="Substituir sua porta por bot":::
* Tab
  1. Em `.fx/configs/tasks.json`, pesquise por `"53000"`.
  1. Substitua-o pela porta.
     :::image type="content" source="../assets/images/teams-toolkit-v2/debug/modify-ports-tab.png" alt-text="Substituir sua porta por guia":::

</details>

<details>
<summary><b>Usar seu próprio pacote de aplicativos</b></summary>

No `.fx/configs/tasks.json`, definido `"appPackagePath"` como `"Build & upload Teams manifest"` o caminho do pacote de aplicativo.

  :::image type="content" source="../assets/images/teams-toolkit-v2/debug/app-package-path.png" alt-text="usar seu próprio caminho de pacote de aplicativo":::

</details>

<details>
<summary><b>Use seu próprio túnel</b></summary>

1. `"Start Teams App Locally"`Em `.fx/configs/tasks.json` , você pode atualizar `"Start Local tunnel"`.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-local-tunnel.png" alt-text="Use seu próprio túnel":::
1. Inicie seu próprio serviço de túnel e atualize `"botMessagingEndpoint"` para seu próprio ponto de extremidade de mensagem em `.fx/configs/tasks.json` `"Set up bot"`.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/set-up-bot.png" alt-text="atualizar ponto de extremidade de mensagens":::

</details>

<details>

<summary><b>Adicionar variáveis de ambiente</b></summary>

Você pode adicionar variáveis de ambiente ao arquivo `.env.teamsfx.local` para guias, bots, extensão de mensagem e para o Azure Functions. O Kit de Ferramentas do Teams carrega as variáveis de ambiente adicionadas para iniciar serviços durante a depuração local.

 > [!NOTE]
 > Certifique-se de iniciar uma nova depuração local depois de adicionar novas variáveis de ambiente, pois as variáveis de ambiente não dão suporte ao recarga quente.

</details>

<details>
<summary><b>Depurar componente parcial</b></summary>

O Kit de Ferramentas do Teams utiliza a depuração de vários destinos do Visual Studio Code para depurar a guia, o bot, a extensão de mensagem e o Azure Functions ao mesmo tempo. Você pode atualizar `.vscode/launch.json` e `.vscode/tasks.json` para depurar componente parcial. Se você quiser depurar a guia somente em uma guia mais bot com o projeto do Azure Functions, use as seguintes etapas:

1. Atualizar `"Attach to Bot"` e `"Attach to Backend"` depurar composto em `.vscode/launch.json`.

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

2. Atualize `"Start Backend"` e `"Start Bot"` na tarefa Iniciar Tudo em .vscode/tasks.json.

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

## <a name="next"></a>Avançar

> [!div class="nextstepaction"]
> [Depurar seu aplicativo localmente](debug-local.md)

::: zone-end

::: zone pivot="visual-studio"

## <a name="debug-your-teams-app-using-visual-studio"></a>Depurar seu aplicativo teams usando o Visual Studio

O Teams Toolkit automatiza os serviços de inicialização de aplicativos, inicia a depuração e o aplicativo teams de carga lateral. Após a depuração, você pode visualizar o aplicativo Teams no cliente Web do Teams. Você também pode personalizar as configurações de depuração para usar seus pontos de extremidade de bot ou variáveis de ambiente para carregar seu aplicativo configurado. O Visual Studio permite que você depure a guia, o bot e a extensão da mensagem. Durante o processo de depuração, o Teams Toolkit dá suporte aos seguintes recursos de depuração:

* Preparar dependências de aplicativo do Teams
* Iniciar a depuração
* Alternar pontos de interrupção
* Recarga dinâmica
* Parar a depuração

## <a name="prerequisites"></a>Pré-requisitos

| &nbsp; | Instalar | Para usar... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio 2022 versão 17.3 | Você pode instalar a edição corporativa do Visual Studio e instalar o "ASP.NET "carga de trabalho e Ferramentas de Desenvolvimento do Microsoft Teams. |
| &nbsp; | Kit de ferramentas do Teams | Uma extensão do Visual Studio que cria um scaffolding de projeto para seu aplicativo. Use a versão mais recente. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | O Microsoft Teams para colaborar com todos com quem você trabalha por meio de aplicativos para chats, reuniões, chamadas - tudo em um só lugar. |
| &nbsp; | [Preparar o locatário do Microsoft 365](../concepts/build-and-test/prepare-your-o365-tenant.md) | Acesso à conta do Teams com as permissões apropriadas para instalar um aplicativo. |
| &nbsp; | [Conta de desenvolvedor do Microsoft 365](../concepts/build-and-test/prepare-your-o365-tenant.md) | Acesso à conta do Teams com as permissões apropriadas para instalar um aplicativo. |
| &nbsp; | Ferramentas do Azure e [CLI do Microsoft Azure](/cli/azure/install-azure-cli) | Ferramentas do Azure para acessar dados armazenados ou implantar um back-end baseado em nuvem para seu aplicativo teams no Azure. |
|&nbsp;  | **Opcional** | &nbsp; |
|&nbsp; |[Ngrok](https://ngrok.com/) | O Ngrok é usado para encaminhar mensagens externas do Azure Bot Framework para seu computador local.|

## <a name="key-features-of-teams-toolkit"></a>Principais recursos do Kit de Ferramentas do Teams

Você pode ver os seguintes principais recursos do Teams Toolkit, que automatizam o processo de depuração local do aplicativo teams:

### <a name="prepare-teams-app-dependencies"></a>Preparar dependências de aplicativo do Teams

O Teams Toolkit prepara dependências locais de depuração e registra seu aplicativo teams no locatário em sua conta. Para aplicativos bot e extensão de mensagem, o Teams Toolkit registrará e configurará o bot.

### <a name="start-debugging"></a>Iniciar a depuração

Você pode executar a depuração com uma única operação, pressione **F5** para iniciar a depuração. O Teams Toolkit cria código, inicia serviços e o aplicativo inicializa no navegador.

### <a name="toggle-breakpoints"></a>Alternar pontos de interrupção

Você pode alternar pontos de interrupção nos códigos-fonte de guias, bots, extensões de mensagem e funções do Azure. Os pontos de interrupção são executados quando você interage com o aplicativo Teams no navegador da Web.
A imagem a seguir mostra os pontos de interrupção de alternância:

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-toggle-breakpoint.png" alt-text="Pontos de interrupção de alternância de depuração local" lightbox="../assets/images/debug-teams-app/vs-localdebug-toggle-breakpoint.png":::

### <a name="hot-reload"></a>Recarga dinâmica

Selecione **Recarga Dinâmica** para aplicar suas alterações no aplicativo teams quando quiser atualizar e salvar os códigos-fonte simultaneamente durante a depuração.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-hot-reload.png" alt-text="Selecione ícone de recarga quente":::

Selecione a opção **Recarga Dinâmica no Arquivo Salvar** na lista suspensa para habilitar o recarga automática.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-hot-reload-filesave.png" alt-text="Selecionar recarga quente na salvação de arquivos":::
  
   > [!Tip]
   > Para saber mais sobre Recarga Dinâmica função do Visual Studio durante a depuração, você pode visitar <https://aka.ms/teamsfx-vs-hotreload>.

### <a name="stop-debugging"></a>Parar a depuração

Selecione **Parar Depuração** quando a depuração local estiver concluída.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-Stopdebug.png" alt-text="Selecione ícone parar de depuração":::

## <a name="customize-debug-settings"></a>Personalizar configurações de depuração

Você pode personalizar a configuração de depuração para seu aplicativo teams para usar seus pontos de extremidade de bot e adicionar variáveis de ambiente:

### <a name="use-your-bot-endpoint"></a>Usar o ponto de extremidade do bot

Você pode definir a configuração do siteEndpoint em **.fx/configs/config.local.json** como seu ponto de extremidade.

```
"bot": {
    "siteEndpoint": "https://baidu.com"
}
```

### <a name="add-environment-variables"></a>Adicionar variáveis de ambiente

Você pode adicionar **environmentVariables** ao arquivo **launchSettings.json** .

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-environment-variables.png" alt-text="Adicionar variáveis de ambiente personalizadas":::

### <a name="launch-teams-app-as-a-web-app"></a>Iniciar o aplicativo Teams como um aplicativo Web

Você pode iniciar o aplicativo Teams como um aplicativo Web em vez de executar no cliente do Teams.

1. Selecione **Propriedades** > **launchSettings.json** no painel Gerenciador de Soluções em seu projeto.
1. Remova o **'launchUrl'** do arquivo.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-launch-teamsapp-webapp.png" alt-text="Iniciar equipes como um aplicativo Web removendo o launchurl" lightbox="../assets/images/debug-teams-app/vs-localdebug-launch-teamsapp-webapp.png":::

1. Clique com o botão direito do mouse em **Solução** e selecione **Propriedades**.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-solution-properties.png" alt-text="Clique com o botão direito do mouse na solução e selecione propriedades" lightbox="../assets/images/debug-teams-app/vs-localdebug-solution-properties.png":::

1. Selecione **Configuração de Propriedades** >  de **Configuração** na caixa de diálogo.
1. Desmarque a caixa de seleção **Implantar** .
1. Selecione **OK**.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-disable-deploy.png" alt-text="Desmarcar a implantação em propriedades de configuração" lightbox="../assets/images/debug-teams-app/vs-localdebug-disable-deploy.png":::

::: zone-end

## <a name="see-also"></a>Confira também

* [Depurar processo em segundo plano](debug-background-process.md)
* [Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem](provision.md)
* [Implantar na nuvem](deploy.md)
* [Visualizar e personalizar o manifesto do aplicativo Teams](TeamsFx-preview-and-customize-app-manifest.md)
