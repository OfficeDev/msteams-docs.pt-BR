---
title: Criar um novo aplicativo de Teams
author: zyxiaoyuer
description: Neste módulo, saiba como criar um novo aplicativo do Teams usando o Teams Toolkit
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/14/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 234aa5ae8c118f323f8f0436f6b7226c490baa7c
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833048"
---
# <a name="create-a-new-teams-project"></a>Criar um novo projeto do Teams

Nesta seção, você pode aprender a criar um novo projeto do Teams usando Visual Studio Code e Visual Studio.

::: zone pivot="visual-studio-code"

## <a name="create-a-new-teams-project-for-visual-studio-code"></a>Criar um novo projeto do Teams para Visual Studio Code

Você pode criar um novo projeto do Teams selecionando **Criar um novo aplicativo do Teams** no Teams Toolkit. Você pode criar os seguintes tipos de aplicativo no Teams Toolkit:

| Tipo de aplicativo | Definição |
| --- | --- |
| Aplicativo Básico do Teams | Os aplicativos básicos do Teams são aplicativos de extensão de guia, bot ou mensagem que você pode criar e personalizar com base em suas necessidades. |
| Aplicativo Teams baseado em cenário | Os aplicativos do Teams baseados em cenário são bot de notificação, bot de comando, guia habilitada para SSO ou aplicativo de guia SPFx e é adequado para um cenário específico. Por exemplo, o bot de notificação é adequado apenas para enviar notificação e não é usado para chat. |

## <a name="create-a-new-teams-app"></a>Criar um novo aplicativo de Teams

As etapas para criar um novo aplicativo do Teams são semelhantes para todos os tipos de aplicativo, exceto SPFx, e bot de notificação. As seguintes etapas ajudam você a criar um novo aplicativo de guias:

**Para criar um aplicativo**

1. Abra o Visual Studio Code.

1. Selecione o ícone Kit de :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png"::: Ferramentas do Teams na barra de navegação à esquerda.

1. Selecione **Criar um novo aplicativo do Teams**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. Verifique se **Tab** está selecionado como seu recurso de aplicativo.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/select-capabilities-tabapp.png" alt-text="Selecionar Recurso de Aplicativo":::

1. Selecione **JavaScript** como linguagem de programação.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/select-language-tab.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. Selecione **Pasta padrão** para armazenar sua pasta raiz do projeto no local padrão.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/select-default-location.png" alt-text="Selecionar local padrão":::

   As etapas a seguir orientam você a alterar o local padrão:

      1. Selecione **Procurar**.

          :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/select-browse.png" alt-text="Selecione procurar armazenamento":::

      1. Selecione o local para o workspace do projeto.

      1. Selecione a **Pasta Selecionar**.

          :::image type="content" source="../assets/images/teams-toolkit-v2/select-folder.png" alt-text="select-folder para armazenamento":::

1. Insira `helloworld` como o nome do aplicativo. Verifique se você usa apenas caracteres alfanuméricos. Selecione **Enter**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/enter-name-tab1.png" alt-text="Captura de tela mostrando onde inserir o nome do aplicativo.":::

1. Por padrão, o projeto é aberto em uma nova janela dentro de 10 segundos. Se você quiser abrir na janela atual, selecione **Abrir na janela atual**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/new-window-notification.png" alt-text="Nova notificação de janela":::

   O aplicativo de guia Teams é criado em alguns segundos.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/tap-app-created1.png" alt-text="Captura de tela mostrando o aplicativo criado.":::

### <a name="directory-structure-for-different-app-types"></a>Estrutura de diretório para diferentes tipos de aplicativo

O Teams Toolkit fornece todos os componentes para a criação de um aplicativo. Depois de criar o projeto, você pode exibir as pastas e os arquivos do projeto no **Explorer**.

<br>
<details>
<summary><b>Estrutura de diretório para o aplicativo básico do Teams</b></summary>

Você tem três tipos diferentes de estrutura básica de aplicativo e diretório do Teams semelhantes para todos os tipos de aplicativos. O exemplo a seguir mostra uma estrutura básica de diretório de aplicativo da guia teams:

| Nome da pasta | Conteúdos |
| --- | --- |
| `.fx/configs` | Arquivos de configuração que o usuário pode personalizar para o aplicativo teams. |
| - `.fx/configs/config.<envName>.json` | Arquivo de configuração para cada ambiente. |
| - `.fx/configs/azure.parameters.<envName>.json` | Arquivo de parâmetros para provisionamento do Azure BICEP para cada ambiente. |
| - `.fx/configs/projectSettings.json` | Configurações de projeto globais que se aplicam a todos os ambientes. |
| `tabs` | Código para a funcionalidade Tab necessária no runtime, como o aviso de privacidade, os termos de uso e as guias de configuração. |
| - `tabs/src/index.jsx` | Ponto de entrada para o aplicativo front-end, em que o componente principal do Aplicativo é renderizado com `ReactDOM.render()` |
| - `tabs/src/components/App.jsx` | Código para lidar com o roteamento de URL no aplicativo. Ele chama o [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre seu aplicativo e o Teams. |
| - `tabs/src/components/Tab.jsx` | Código para implementar a interface do usuário do aplicativo. |
| - `tabs/src/components/TabConfig.jsx` | Código para implementar a interface do usuário que configura seu aplicativo. |
| `templates/appPackage` | Arquivos de modelo de manifesto de aplicativo e os ícones do aplicativo: color.png e outline.png. |
| - `templates/appPackage/manifest.template.json` | Manifesto do aplicativo para executar o aplicativo em ambiente local ou remoto.  |
| `templates/azure` | Arquivos de modelo BICEP |

> [!NOTE]
> Se você tiver um aplicativo de extensão de bot ou mensagem, as pastas relevantes serão adicionadas à estrutura do diretório.

Para saber mais sobre a estrutura de diretório de diferentes tipos de aplicativo básico do Teams, confira a seguinte tabela:

| Tipo de aplicativo | Links |
| --- | --- |
| Para aplicativo de guias | [Crie seu primeiro aplicativo de guia usando JavaScript](../sbs-gs-javascript.yml) |
| Para o aplicativo bot | [Crie seu primeiro aplicativo de bot usando JavaScript](../sbs-gs-bot.yml) |
| Para aplicativo de extensão de mensagem | [Criar seu primeiro aplicativo de extensão de mensagem usando JavaScript](../sbs-gs-msgext.yml) |

</details>
<br>
<details>
<summary><b>Estrutura de diretório para o aplicativo teams baseado em cenário</b></summary>

Você tem quatro tipos diferentes de estrutura de diretório e aplicativo do Teams baseados em cenários semelhantes para todos os tipos de aplicativos. O exemplo a seguir mostra uma estrutura de diretório de aplicativo do Teams de bot de notificação baseada em cenário:

A nova pasta de projeto contém o seguinte conteúdo:

| Nome da pasta | Conteúdos |
| --- | --- |
| `.fx` | Configurações, configuração e informações de ambiente do nível do projeto |
| `.vscode` | Arquivos de código VS para depuração local |
| `bot` | O código-fonte do bot |
| `templates` | Modelos de manifesto de aplicativo do Teams e recursos correspondentes do Azure |

A implementação de notificação principal na pasta **bot** e ela contém:

| Nome do arquivo | Conteúdos |
| --- | --- |
| `src/adaptiveCards/` | Modelos para Cartão Adaptável  |
| `src/internal/` | Código de inicialização gerado para funcionalidade de notificação |
| `src/index.*s` | O ponto de entrada para lidar com mensagens de bot e enviar notificações |
| `.gitignore` | Arquivo para excluir arquivos locais do projeto de bot |
| `package.json` | O arquivo de pacote npm para o projeto de bot |

> [!NOTE]
> Se você tiver um bot de comando, guia habilitada para SSO ou aplicativo de guia SPFx, pastas relevantes serão adicionadas à estrutura do diretório.

Para saber mais sobre a estrutura de diretório de diferentes tipos de aplicativo teams baseado em cenário, confira a tabela a seguir:

| Tipo de aplicativo | Links |
| --- | --- |
| Para aplicativo bot de notificação | [Enviar notificação para o Teams](../sbs-gs-notificationbot.yml) |
| Para aplicativo bot de comando | [Criar bot de comando](../sbs-gs-commandbot.yml) |
| Para aplicativo de guia SPFx | [Criar um aplicativo Teams com SPFx](../sbs-gs-spfx.yml) |

</details>
<br>
<details>
<summary><b>Estrutura de diretório para aplicativo de várias funcionalidades</b></summary>

Você pode adicionar mais recursos ao aplicativo do Teams existente usando a adição de recursos. Por exemplo, se você adicionar o aplicativo bot ao aplicativo de guia existente, o Teams Toolkit adicionará a pasta bot com arquivos e código relevantes.

A imagem a seguir mostra a estrutura de diretório do aplicativo tab:

   :::image type="content" source="../assets/images/teams-toolkit-v2/tabapp-directory.png" alt-text="Estrutura do diretório do aplicativo Tab":::

A imagem a seguir mostra a estrutura do diretório do aplicativo tab com o recurso bot:

   :::image type="content" source="../assets/images/teams-toolkit-v2/tab-app-with-bot-app.png" alt-text="Tab app with bot app directory structure":::

</details>

::: zone-end

::: zone pivot="visual-studio"

## <a name="create-new-teams-app-in-visual-studio"></a>Criar um aplicativo do Teams no Visual Studio

O Teams Toolkit fornece modelos de aplicativo do Microsoft Teams no Visual Studio para criar o aplicativo teams.  Você pode pesquisar e selecionar o modelo de aplicativo do Teams necessário ao criar um novo projeto. Você pode ter modelos de aplicativo do Teams para criar:

* Aplicativo Tab
* Bot de comando
* Bot de notificação
* Aplicativo Extensão de Mensagens

## <a name="prerequisites"></a>Pré-requisitos

| &nbsp; | Instalar | Para usar... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio versão 17.3 | Você pode instalar a edição corporativa do Visual Studio e instalar o "ASP.NET "carga de trabalho e Ferramentas de Desenvolvimento do Microsoft Teams. |
| &nbsp; | Kit de ferramentas do Teams | Uma extensão do Visual Studio que cria um scaffolding de projeto para seu aplicativo. Use a versão mais recente. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | O Microsoft Teams para colaborar com todos com quem você trabalha por meio de aplicativos para chats, reuniões, chamadas - tudo em um só lugar. |
 | &nbsp; | [Preparar o locatário do Microsoft 365](../concepts/build-and-test/prepare-your-o365-tenant.md) | Acesso à conta do Teams com as permissões apropriadas para instalar um aplicativo. |

## <a name="create-a-new-teams-app"></a>Criar um novo aplicativo de Teams

As etapas para criar um novo aplicativo do Teams são semelhantes para todos os tipos de aplicativo, exceto bot de notificação. As seguintes etapas ajudam você a criar um novo aplicativo de guias:

1. Abra o Visual Studio.
1. Crie um novo projeto usando uma das duas opções a seguir.

     :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-create-new-project1_1.png" alt-text="Criar um novo projeto com código a partir do início":::

    * Selecione **Criar um novo projeto** em **Introdução** ajuda você a escolher o modelo de projeto com scaffolding de código.
    * Selecione **Continuar sem Código** para criar projeto sem scaffolding de código e selecione **Arquivo** > **Novo** > **Projeto** no Visual Studio.

        :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-create-new-project2_1.png" alt-text="Criar um novo projeto no menu de arquivo":::

   A janela **Criar um novo projeto** é exibida.  

1. Insira equipes na caixa de pesquisa e na lista, selecione **Aplicativo do Microsoft Teams** e selecione **Avançar**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/visual-studio.png" alt-text="Pesquisar e escolher o aplicativo microsoft teams":::

   A janela **Configurar seu novo projeto** é exibida.

     :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-ms-teams-app-project-name_1.png" alt-text="Nomeie seu aplicativo":::

    1. Insira um nome adequado para seu projeto.

         > [!NOTE]
         > O nome do projeto que você está inserindo também é preenchido automaticamente no **nome da solução** . Se desejar, você pode alterar o nome da solução sem afetar o nome do projeto.

    1. Selecione o caminho da pasta em que você deseja criar o workspace do projeto.
    1. Insira um nome de solução diferente, se desejar.
    1. Verifique a opção para salvar o projeto e a solução na mesma pasta, se desejar. Para este tutorial, você não precisa dessa opção.
    1. Selecionar **Criar**.

   A janela **Criar um aplicativo do Teams** é exibida.

1. Neste tutorial, **Tab** é selecionado para criar um aplicativo teams e selecionar **Criar**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-ms-teams-app-type_3.png" alt-text="Selecione o tipo de aplicativo teams":::

   > [!NOTE]
   > Você pode selecionar o tipo necessário de aplicativo do Teams para seu projeto.

   O **Introdução** com a janela **Bem-vindo ao Teams Toolkit** é exibido.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-getting-started-page.png" alt-text="Selecione o kit de ferramentas Introdução teams":::

### <a name="directory-structure"></a>Estrutura de diretório

O Teams Toolkit fornece todos os componentes para a criação de um aplicativo. Depois de criar o projeto, você pode exibir as pastas e os arquivos do projeto no Explorer.

* **Estrutura de diretório para o aplicativo básico do Teams**

  :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-create-new-project-solution-explorer_1.png" alt-text="Selecione a guia Gerenciador de Soluções kit de ferramentas do teams":::

* **Estrutura de diretório para o aplicativo teams baseado em cenário**

  :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Create-new-app-VS/vs-create-new-project-solution-explorer.png" alt-text="Selecione o kit de ferramentas Gerenciador de Soluções teams":::

## <a name="teams-app-templates-in-teams-toolkit-for-visual-studio"></a>Modelos de aplicativo do Teams no Teams Toolkit para Visual Studio

Você pode ver modelos de aplicativo do Teams já preenchidos no Teams Toolkit para vários tipos de aplicativo do Teams. A tabela a seguir lista todos os modelos disponíveis:

|Modelo de aplicativo do Teams  |Descrição  |
|---------|---------|
|Bot de Notificação     |O aplicativo Bot de Notificação pode enviar notificação ao cliente do Teams, há várias maneiras de disparar a notificação. Por exemplo, acione a notificação por solicitação HTTP ou por tempo. Você também pode selecionar a notificação disparada com base no cenário de negócios.         |
|Bot de Comando     |Os usuários podem digitar um comando para interagir com o bot usando o aplicativo Bot de Comando.         |
|Tab     |O aplicativo Tab mostra uma página da Web dentro do Teams e habilita o logon único usando a conta do Teams.         |
|Extensão de Mensagem     |O aplicativo Message Extension implementa recursos simples como criar Cartão Adaptável, pesquisar pacotes nugget, desenrolar links para o domínio "dev.botframework.com".         |

> [!NOTE]
> Depois que o projeto é criado, o Teams Toolkit abre automaticamente **a janela Introdução** . Agora você pode ver as instruções na janela **Introdução** e verificar os diferentes recursos no Teams Toolkit.

::: zone-end

## <a name="see-also"></a>Confira também

* [Criar um aplicativo do Teams com o Blazor](../sbs-gs-blazorupdate.yml)
* [Criar um aplicativo Teams com C# ou .NET](../sbs-gs-csharp.yml)
* [Pré-requisitos para todos os tipos de ambiente e criar seu aplicativo teams](tools-prerequisites.md)
* [Preparar para criar aplicativos usando o Kit de Ferramentas do Microsoft Teams](build-environments.md)
* [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
* [Implantar o aplicativo teams na nuvem usando o Visual Studio](deploy.md#deploy-teams-app-to-the-cloud-using-visual-studio)
