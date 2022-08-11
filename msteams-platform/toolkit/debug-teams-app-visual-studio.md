---
author: surbhigupta
title: Depurar seu aplicativo Teams para Visual Studio
description: Neste módulo, saiba como depurar seu aplicativo teams localmente no Visual Studio usando o Kit de Ferramentas do Teams
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
ms.openlocfilehash: cff0b3e18f63bc7943a7fc16875294f41257a37c
ms.sourcegitcommit: 52a11f7614c43172bc2d57401a60d569db5310a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2022
ms.locfileid: "67291664"
---
# <a name="debug-your-teams-app-locally-using-visual-studio"></a>Depurar seu aplicativo teams localmente usando o Visual Studio

O Kit de Ferramentas do Teams ajuda você a depurar e visualizar seu aplicativo Microsoft Teams localmente. A depuração é um processo de criação, verificação, detecção e correção de problemas ou bugs em seu aplicativo. A depuração garante que o programa seja executado com êxito. O Visual Studio permite depurar a guia, o bot e a extensão de mensagem. O Kit de Ferramentas do Teams dá suporte aos seguintes recursos de depuração:

* Preparar dependências de aplicativos do Teams
* Iniciar a depuração
* Alternar pontos de interrupção
* Recarga dinâmica
* Parar a depuração

Durante o processo de depuração, o Kit de Ferramentas do Teams inicia automaticamente os serviços de aplicativos, inicia a depuração e carrega o aplicativo do Teams. Após a depuração, você pode visualizar o aplicativo Teams no cliente Web do Teams. Você também pode personalizar as configurações de depuração para usar os pontos de extremidade do bot ou variáveis de ambiente para carregar o aplicativo configurado.

## <a name="prerequisites"></a>Pré-requisitos

| &nbsp; | Instalar | Para usar... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio 2022 versão 17.3 | Você pode instalar a edição enterprise do Visual Studio e instalar a carga de trabalho "ASP.NET" e as Ferramentas de Desenvolvimento do Microsoft Teams. |
| &nbsp; | Kit de ferramentas do Teams | Uma extensão do Visual Studio que cria um scaffolding de projeto para seu aplicativo. Use a versão mais recente. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | O Microsoft Teams para colaborar com todos com quem você trabalha por meio de aplicativos para chats, reuniões, chamadas - tudo em um só lugar. |
| &nbsp; | [Preparar o locatário do Microsoft 365](../concepts/build-and-test/prepare-your-o365-tenant.md) | Acesso à conta do Teams com as permissões apropriadas para instalar um aplicativo. |
| &nbsp; | [Conta de desenvolvedor do Microsoft 365](/../concepts/build-and-test/prepare-your-o365-tenant) | Acesso à conta do Teams com as permissões apropriadas para instalar um aplicativo. |
| &nbsp; | Ferramentas do Azure e [CLI do Microsoft Azure](/cli/azure/install-azure-cli) | Ferramentas do Azure para acessar dados armazenados ou implantar um back-end baseado em nuvem para seu aplicativo Teams no Azure. |
|&nbsp;  | **Opcional** | &nbsp; |
|&nbsp; |[Ngrok](https://ngrok.com/) | O Ngrok é usado para encaminhar mensagens externas do Azure Bot Framework para seu computador local.|

## <a name="debug-your-app-locally"></a>Depurar seu aplicativo localmente

Você pode depurar seu aplicativo localmente no Visual Studio usando o Kit de Ferramentas do Teams executando:

### <a name="set-up-ngrok-only-for-bot-and-message-extension-app"></a>Configurar o ngrok (somente para o aplicativo bot e extensão de mensagem)

Use um prompt de comando para executar este comando:

```
ngrok http 5130
```

### <a name="set-up-your-teams-toolkit"></a>Configure seu Kit de Ferramentas do Teams

Execute as seguintes etapas usando o Kit de Ferramentas do Teams para depurar seu aplicativo depois de criar um projeto:

1. Clique com o botão direito do mouse em seu **projeto**.
1. Selecione **o Kit de Ferramentas do Teams**.
1. Selecione **Preparar Dependências de Aplicativos do Teams**.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-teamsappdependencies.png" alt-text="Dependências de aplicativo do Teams para depuração local":::

   > [!NOTE]
   > Nesse cenário, o nome do projeto é MyTeamsApp1

   Sua conta do Microsoft 365 precisa ter a permissão de carregamento lateral antes de entrar.  Verifique se o aplicativo Teams pode ser carregado para o locatário, caso contrário, o aplicativo Teams pode não ser executado no Cliente do Teams.

1. Entre em sua conta **do Microsoft 365**.
1. Selecione **Continuar**
   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-signin-m365.png" alt-text="Entrar na conta do Microsoft 365":::

   > [!Note]
   > Saiba mais sobre o sideload de permissão visitando <https://aka.ms/teamsfx-sideloading-option>.

1. Selecione **Depurar**.
1. Selecione **Iniciar Depuração** ou selecione **F5 diretamente**.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-Startdebug.png" alt-text="Iniciar Depuração":::

   O Visual Studio inicia o aplicativo Teams dentro do cliente do Microsoft Teams em seu navegador.

   > [!Note]
   > Saiba mais visitando <https://aka.ms/teamsfx-vs-debug>.

1. Depois que o Microsoft Teams for carregado, **selecione Adicionar** para instalar seu aplicativo no Teams.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-add-loadapp.png" alt-text="Selecione Adicionar para carregar aplicativo":::

   > [!TIP]
   > Você também pode usar a função de recarga dinâmica do Visual Studio durante a depuração. Saiba mais visitando <https://aka.ms/teamsfx-vs-hotreload>.

   > [!NOTE]
   > Certifique-se de postar a solicitação HTTP em '<http://localhost:5130/api/notification>' para disparar a notificação, quando você estiver depurando o aplicativo de Bot de Notificação. Se você tiver selecionado o gatilho HTTP ao criar o projeto, poderá usar qualquer ferramenta de API, como curl (Prompt de Comando do Windows), Postman e assim por diante.

   > [!TIP]
   > Se você fizer alterações no arquivo de manifesto do aplicativo Teams (/templates/appPackage/manifest.template.json), certifique-se de executar o comando Preparar Dependências de Aplicativo do Teams. Antes de tentar executar o aplicativo Teams novamente localmente.

## <a name="key-features-of-teams-toolkit"></a>Principais recursos do Kit de Ferramentas do Teams

Você pode ver os seguintes recursos principais do Kit de Ferramentas do Teams, que automatizam o processo de depuração local do aplicativo Teams:

### <a name="prepare-teams-app-dependencies"></a>Preparar dependências de aplicativos do Teams

O Kit de Ferramentas do Teams prepara as dependências de depuração locais e registra seu aplicativo do Teams no locatário em sua conta. Para aplicativos de Bot e Extensão de Mensagem, o Kit de Ferramentas do Teams registrará e configurará o bot.

### <a name="start-debugging"></a>Iniciar a depuração

Você pode executar a depuração com uma única operação, pressione **F5** para iniciar a depuração. O Kit de Ferramentas do Teams cria código, inicia serviços e o aplicativo é iniciado em seu navegador.

### <a name="toggle-breakpoints"></a>Alternar pontos de interrupção

Você pode alternar pontos de interrupção nos códigos-fonte de guias, bots, extensões de mensagem e funções do Azure. Os pontos de interrupção são executados quando você interage com o aplicativo Teams em seu navegador da Web.
A imagem a seguir mostra os pontos de interrupção de alternância:

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-toggle-breakpoint.png" alt-text="Pontos de interrupção de alternância de depuração local":::

### <a name="hot-reload"></a>Recarga dinâmica

Selecione **Recarga Dinâmica** para aplicar suas alterações no aplicativo Teams quando quiser atualizar e salvar os códigos-fonte simultaneamente durante a depuração.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-hot-reload.png" alt-text="Selecionar o ícone de recarga dinâmica":::

Selecione a opção **Recarga Dinâmica salvar arquivo** na lista suspensa para habilitar o recarregamento dinâmico automático.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-hot-reload-filesave.png" alt-text="Selecionar recarga ativa no salvamento de arquivo":::
  
   > [!Tip]
   > Para saber mais sobre Recarga Dinâmica função do Visual Studio durante a depuração, visite<https://aka.ms/teamsfx-vs-hotreload>.

### <a name="stop-debugging"></a>Parar a depuração

Selecione **Parar Depuração** quando a depuração local for concluída.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-Stopdebug.png" alt-text="Selecione o ícone parar depuração":::

## <a name="customize-debug-settings"></a>Personalizar configurações de depuração

Você pode personalizar a configuração de depuração do aplicativo Teams para usar os pontos de extremidade do bot e adicionar variáveis de ambiente:

### <a name="use-your-bot-endpoint"></a>Usar o ponto de extremidade do bot

Você pode definir a configuração do siteEndpoint **em .fx/configs/config.local.json** para o ponto de extremidade.

```
"bot": {
    "siteEndpoint": "https://baidu.com"
}
```

### <a name="add-environment-variables"></a>Adicionar variáveis de ambiente

Você pode adicionar **environmentVariables** ao **arquivo launchSettings.json** .

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-environment-variables.png" alt-text="Adicionar variáveis de ambiente personalizadas":::

### <a name="launch-teams-app-as-a-web-app"></a>Iniciar o aplicativo Teams como um aplicativo Web

Você pode iniciar o aplicativo Teams como um aplicativo Web em vez de ser executado no cliente do Teams.

1. Selecione **Propriedades** > **launchSettings.json** no Gerenciador de Soluções em seu projeto.
1. Remova **o 'launchUrl'** do arquivo.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-launch-teamsapp-webapp.png" alt-text="Iniciar equipes como um aplicativo Web removendo launchurl":::

1. Clique com o botão direito do mouse em **Solução**.
1. Selecione **Propriedades**.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-solution-properties.png" alt-text="Clique com o botão direito do mouse na solução e selecione as propriedades":::

1. Selecione **Configuração de Propriedades** > **de Configuração** na caixa de diálogo.
1. Selecione desmarcar **a caixa Implantar** processo.
1. Selecione **OK**.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-disable-deploy.png" alt-text="Desmarque a implantação nas propriedades de configuração ":::

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
* [Implantar o aplicativo Teams na nuvem usando o Visual Studio](deploy-teams-app.md)
* [Editar manifesto do aplicativo Teams usando o Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
