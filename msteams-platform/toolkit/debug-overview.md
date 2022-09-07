---
title: Depurar seu aplicativo Teams
author: surbhigupta
description: Neste módulo, saiba como depurar seu aplicativo Teams no Kit de Ferramentas do Teams e os principais recursos do Kit de Ferramentas do Teams
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
ms.openlocfilehash: 8545d4bbd97a6a4c5065c279368505f18dd5a14a
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617011"
---
# <a name="debug-your-microsoft-teams-app"></a>Depurar seu aplicativo Microsoft Teams

O Kit de Ferramentas do Microsoft Teams ajuda você a depurar e visualizar seu aplicativo do Teams. Depurar é o processo de verificação, detecção e correção de problemas ou bugs para garantir que o programa seja executado com êxito no Teams.

Durante o processo de depuração:

* O Kit de Ferramentas do Teams inicia automaticamente os serviços de aplicativos, inicia depuradores e sideloads do aplicativo Teams.
* O Kit de Ferramentas do Teams verifica os pré-requisitos durante o processo em segundo plano de depuração.
* Seu aplicativo Teams está disponível para visualização no cliente Web do Teams localmente após a depuração.
* Você também pode personalizar as configurações de depuração para usar seus pontos de extremidade de bot, certificado de desenvolvimento ou componente parcial de depuração para carregar seu aplicativo configurado.
* O Microsoft Visual Studio Code permite depurar guias, bots, extensão de mensagem e Azure Functions.

## <a name="key-debug-features-of-teams-toolkit"></a>Principais recursos de depuração do Kit de Ferramentas do Teams

O Kit de Ferramentas do Teams dá suporte aos seguintes recursos de depuração:

* [Iniciar depuração](#start-debugging)
* [Depuração de vários destinos](#multi-target-debugging)
* [Alternar pontos de interrupção](#toggle-breakpoints)
* [Recarga dinâmica](#hot-reload)
* [Parar a depuração](#stop-debugging)

O Kit de Ferramentas do Teams executa funções em segundo plano durante o processo de depuração, que incluem verificar os pré-requisitos necessários para a depuração. Você pode ver o progresso do processo de verificação no canal de saída do Kit de Ferramentas do Teams. No processo de instalação, você pode registrar e configurar seu aplicativo teams.

### <a name="start-debugging"></a>Iniciar a depuração

Você pode pressionar **F5** como uma única operação para iniciar a depuração. O Kit de Ferramentas do Teams começa a verificar os pré-requisitos, registra o aplicativo do Azure AD, o aplicativo do Teams e registra o bot, inicia os serviços e inicia o navegador.

### <a name="multi-target-debugging"></a>Depuração de vários destinos

O Kit de Ferramentas do Teams utiliza o recurso de depuração de vários destinos para depurar a guia, o bot, a extensão de mensagem e o Azure Functions ao mesmo tempo.

### <a name="toggle-breakpoints"></a>Alternar pontos de interrupção

Você pode alternar pontos de interrupção nos códigos-fonte das guias, bots, extensões de mensagens e do Azure Functions. Os pontos de interrupção são executados quando você interage com o aplicativo Teams em um navegador da Web. A imagem a seguir mostra o ponto de interrupção de alternância:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/toggle-points.png" alt-text="alternar pontos de interrupção" lightbox="../assets/images/teams-toolkit-v2/debug/toggle-points.png":::

### <a name="hot-reload"></a>Recarga dinâmica

Você pode atualizar e salvar os códigos-fonte de tab, bot, extensão de mensagem e Azure Functions ao mesmo tempo ao depurar o aplicativo Teams. O aplicativo recarrega e o depurador é reanexado às linguagens de programação.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hot-reload.png" alt-text="recarga dinâmica para códigos-fonte" lightbox="../assets/images/teams-toolkit-v2/debug/hot-reload.png":::

### <a name="stop-debugging"></a>Parar a depuração

Ao concluir a depuração local, você pode selecionar Parar **(Shift+F5)** ou **[Alt] Desconectar (Shift+F5)** na barra de ferramentas de depuração flutuante para interromper todas as sessões de depuração e encerrar tarefas. A imagem a seguir mostra a ação parar a depuração:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/stop-debug.png" alt-text="parar a depuração":::

## <a name="prepare-for-debug"></a>Preparar para depuração

As etapas a seguir ajudam você a se preparar para a depuração:

### <a name="sign-in-to-microsoft-365"></a>Entrar no Microsoft 365

Se você já se inscreveu no Microsoft 365, entre no Microsoft 365. Para obter mais informações, consulte [o programa para desenvolvedores do Microsoft 365](tools-prerequisites.md#microsoft-365-developer-program)

### <a name="toggle-breakpoints"></a>Alternar pontos de interrupção

Verifique se você pode alternar pontos de interrupção nos códigos-fonte de guias, bots, extensões de mensagem e Azure Functions para obter mais informações, consulte [Alternar pontos de interrupção](#toggle-breakpoints)

## <a name="customize-debug-settings"></a>Personalizar configurações de depuração

O Kit de Ferramentas do Teams desmarca alguns pré-requisitos e permite personalizar as configurações de depuração para criar sua guia ou bot:

<br>

<details>
<summary><b>Usar o ponto de extremidade do bot</b></summary>

1. Em Visual Studio Code configurações, você precisa desmarcar Se o **Ngrok está instalado e iniciado (ngrok)**.

1. Você pode definir a `siteEndpoint` configuração `.fx/configs/config.local.json` em seu ponto de extremidade.

```json
{
    "bot": {
        "siteEndpoint": "https://your-bot-tunneling-url"
    }
}

```

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/bot-endpoint.png" alt-text="Personalizar o ponto de extremidade do bot":::

</details>

<details>
<summary><b>Usar seu certificado de desenvolvimento</b></summary>

1. Em Visual Studio Code configurações, você precisa desmarcar Verificar se o certificado de **desenvolvimento é confiável (devCert)**.

1. Você pode definir e `sslCertFile` configurar `sslKeyFile` o caminho `.fx/configs/config.local.json` do arquivo de certificado e o caminho do arquivo de chave.

```json
{
    "frontend": {
        "sslCertFile": "",
        "sslKeyFile": ""
    }
}
```

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/development-certificate-customize.png" alt-text="Personalizar certificado":::

</details>

<details>
<summary><b>Use seus scripts de início para iniciar os serviços de aplicativo</b></summary>

1. Para a guia, você precisa atualizar `dev:teamsfx` o script em `tabs/package.json`.

1. Para o bot ou a extensão de mensagem, você precisa atualizar o `dev:teamsfx` script em `bot/package.json`.

1. Por Azure Functions, você precisa atualizar `dev:teamsfx` o script em `api/package.json` e para o script de atualização do `watch:teamsfx` TypeScript.

   > [!NOTE]
   > Atualmente, a guia, o bot, os aplicativos de extensão de mensagem e as portas do Azure Functions não suportam a personalização.

</details>

<details>
<summary><b>Adicionar variáveis de ambiente</b></summary>

Você pode adicionar variáveis de ambiente ao arquivo `.env.teamsfx.local` para guias, bots, extensão de mensagem e para o Azure Functions. O Kit de Ferramentas do Teams carrega as variáveis de ambiente adicionadas para iniciar serviços durante a depuração local.

 > [!NOTE]
 > Certifique-se de iniciar uma nova depuração local depois de adicionar novas variáveis de ambiente, pois as variáveis de ambiente não suportam a recarga dinâmica.

</details>

<details>
<summary><b>Depurar componente parcial</b></summary>

O Kit de Ferramentas do Teams utiliza a depuração de vários destinos do Visual Studio Code para depurar a guia, o bot, a extensão de mensagem e o Azure Functions ao mesmo tempo. Você pode atualizar `.vscode/launch.json` e `.vscode/tasks.json` para depurar componente parcial. Se você quiser depurar a guia somente em uma guia mais bot com o projeto do Azure Functions, use as seguintes etapas:

1. Comentário **`Attach to Bot`** e de **`Attach to Backend`** depuração composta em `.vscode/launch.json`.

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

2. Comente **`Start Backend`** e inicie o bot da tarefa Iniciar Tudo em .vscode/tasks.json.

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

## <a name="see-also"></a>Confira também

* [Depurar processo em segundo plano](debug-background-process.md)
* [Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem](provision.md)
* [Implantar na nuvem](deploy.md)
* [Visualizar e personalizar o manifesto do aplicativo Teams](TeamsFx-preview-and-customize-app-manifest.md)
