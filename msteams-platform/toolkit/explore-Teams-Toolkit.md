---
title: Explorar o Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Neste módulo, saiba mais sobre como explorar o Teams Toolkit
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 07/29/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 0fa31c52b206738cfb174519fc6d3c445b604a8e
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833125"
---
# <a name="explore-teams-toolkit"></a>Explorar o Kit de Ferramentas do Teams

Neste documento, você pode entender diferentes elementos da interface do usuário, juntamente com a descrição e o uso básico no Teams Toolkit para Visual Studio Code e Visual Studio.

::: zone pivot="visual-studio-code"

## <a name="teams-toolkit-for-visual-studio-code-basic-ui-elements"></a>Kit de Ferramentas do Teams para Visual Studio Code elementos básicos da interface do usuário

Após a instalação do Teams Toolkit, você verá a interface do usuário do Teams Toolkit, conforme mostrado na seguinte imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/overview1.png" alt-text="Visão geral do Kit de Ferramentas do Teams":::

| Serial No | Elementos da interface do usuário | Definição |
| --- | --- |
| 1 | **Introdução** | Explore o Kit de Ferramentas do Teams. |
| &nbsp; | **Tutoriais** | Acesse tutoriais diferentes. |
| &nbsp; | **Documentação** | Acesse a Documentação do Desenvolvedor do Microsoft Teams. |
| 2 | **Criar um novo aplicativo do Teams** | Crie um novo aplicativo do Teams com base em seus requisitos. |
| 3 | **Exibir exemplos** | Crie diferentes tipos de aplicativo com base em exemplos existentes. |
| 4 | **Abrir pasta** | Abra o aplicativo teams existente. |
| 5 | **Novo arquivo** | Crie um novo arquivo. |
| &nbsp; | **Abrir arquivo** | Abra o arquivo existente. |
| &nbsp; | **Abrir pasta** | Abra a pasta existente. |
| 6 | **Recente** | Exibir os arquivos recentes. |

### <a name="exploring-the-teams-toolkit-task-pane"></a>Explorando o painel de tarefas do Teams Toolkit

Você pode explorar mais elementos da interface do usuário no painel de tarefas no Teams Toolkit. O painel de tarefas só fica visível depois de criar um aplicativo usando o Teams Toolkit. O vídeo a seguir ajuda você a saber sobre o processo de criação de um novo aplicativo do Teams e, após esse processo, você pode exibir o painel de tarefas no Teams Toolkit.

   ![Criar um aplicativo do Teams](~/assets/videos/javascript-tab-app1.gif)

Depois de criar um novo aplicativo do Teams, você pode ver a estrutura de diretório do aplicativo no painel esquerdo e o arquivo readme no painel direito.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/first-page.png" alt-text="Primeira página do Teams Toolkit":::

Vamos fazer um tour pela interface do usuário do Teams Toolkit.

 Na barra de ferramentas Visual Studio Code, os seguintes ícones são relevantes para o Kit de Ferramentas do Teams:

| Ícone | Descrição |
| --- | --- |
| **Explorador** :::image type="icon" source="../assets/images/teams-toolkit-v2/file-explorer-icon.PNG":::  | Para exibir a estrutura de diretório do aplicativo. |
| **Executar e Depurar** :::image type="icon" source="../assets/images/teams-toolkit-v2/run-debug-icon.PNG":::  | Para iniciar o processo de depuração local ou remota. |
| **Kit de ferramentas do Teams** :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: | Para exibir o painel de tarefas no Teams Toolkit. |

No painel de tarefas, você pode ver as seguintes seções:

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/accounts1.png" alt-text="seção contas":::
   :::column-end:::
   :::column span="":::

        Para desenvolver um aplicativo do Teams, você precisa das seguintes contas:
        
        * **Entre no M365**: use sua conta do Microsoft 365 com uma assinatura E5 válida para criar seu aplicativo.

        * **Entrar no Azure**: use sua conta do Azure para implantar o aplicativo no Azure. Você pode [criar uma conta gratuita do Azure](https://azure.microsoft.com/free/) antes de começar.
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/environment1.png" alt-text="Seção Ambiente":::
   :::column-end:::
   :::column span="":::

        Para implantar seu aplicativo teams, você precisa dos seguintes ambientes:
        
       * **local**: implantar seu aplicativo no ambiente local padrão com configurações de ambiente de máquina local.

        * **dev**: implantar seu aplicativo no ambiente de desenvolvimento padrão com configurações remotas ou de ambiente de nuvem. Você pode criar mais ambientes, conforme necessário.
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/development.png" alt-text="Seção Desenvolvimento":::
   :::column-end:::
   :::column span="":::

        Para criar e personalizar seu aplicativo do Teams, você precisa dos seguintes recursos:
        
       * **Criar um novo aplicativo do Teams**: use o assistente do kit de ferramentas para preparar o scaffolding do projeto para o desenvolvimento de aplicativos.

        * **Exibir exemplos**: selecione qualquer um dos aplicativos de exemplo do Teams Toolkit. O kit de ferramentas baixa o código do aplicativo do GitHub e você pode criar o aplicativo de exemplo.
        
        * **Adicionar recursos**: adicione outros recursos necessários do Teams ao aplicativo Teams durante o processo de desenvolvimento e adicione recursos de nuvem opcionais adequados para seu aplicativo.
       
        * **Editar arquivo de manifesto**: edite a integração do aplicativo do Teams com o cliente do Teams.
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deployment1.png" alt-text="Seção Implantação":::
   :::column-end:::
   :::column span="":::

        Para provisionar, implantar e publicar seu aplicativo teams, você precisa dos seguintes recursos:
        
        * **Provisionamento na nuvem**: alocar recursos do Azure para seu aplicativo. O Kit de ferramentas do Teams está integrado ao Gerenciador de Recursos do Teams.

        * **Pacote de metadados do Zip Teams**: crie o pacote de aplicativos que pode ser carregado no Teams ou no Portal do Desenvolvedor. Ele contém o manifesto do aplicativo e os ícones do aplicativo.
        
        * **Implantar na nuvem**: implante o código-fonte no Azure.
       
        * **Publicar no Teams**: Publique seu aplicativo desenvolvido e distribua-o para escopos, como pessoal, equipe, canal ou organização.
        
        * **Portal do Desenvolvedor para Equipes**: use o Portal do Desenvolvedor para configurar e gerenciar seu aplicativo do Teams. 
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/help-and-feedback1.png" alt-text="Seção Ajuda e comentários":::
   :::column-end:::
   :::column span="":::

        Para acessar mais informações sobre o Teams Toolkit. você precisa da documentação e dos recursos a seguir.
        
        * **Introdução**: exiba a ajuda do Teams Toolkit Introdução em Visual Studio Code.

        * **Tutoriais**: selecione para acessar tutoriais diferentes.
        
        * **Documentação**: selecione para acessar a Documentação do Desenvolvedor do Microsoft Teams.
       
        * **Problemas de relatório no GitHub**: selecione para acessar a página do GitHub e levantar quaisquer problemas.
   :::column-end:::
:::row-end:::

::: zone-end

::: zone pivot="visual-studio"

## <a name="explore-teams-toolkit-for-visual-studio"></a>Explorar o Kit de Ferramentas do Teams para Visual Studio

Depois de instalar o Teams Toolkit, você pode exibir as opções do Teams Toolkit em dois métodos diferentes:

# <a name="project"></a>[Projeto](#tab/prj)

Você pode acessar o Kit de Ferramentas do Teams em **Project**.

1. Selecione Kit **de Ferramentas do** **Project** >  Teams.
1. Agora você pode acessar diferentes opções do Teams Toolkit.

   :::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-operations-menu_1.png" alt-text="Menu de operações do kit de ferramentas do Teams":::

# <a name="solution-explorer"></a>[Gerenciador de Soluções](#tab/solutionexplorer)

   Você pode acessar o Teams Toolkit **em Gerenciador de Soluções**.

1. Selecione **Exibição** >  **Gerenciador de Soluções** para exibir Gerenciador de Soluções painel.
1. Clique com o botão direito do mouse em seu **Projeto**.
1. Selecione **Kit de Ferramentas do Teams** para acessar diferentes opções do Teams Toolkit.

   :::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-operations-menu1_1.png" alt-text="Operações de kit de ferramentas do Teams do Project":::

   > [!NOTE]
   > Nesse cenário, o nome do projeto é **MyTeamsApp1**.

---

Depois de criar o Projeto do Teams, você pode executar as seguintes funções no Teams Toolkit para Visual Studio:

:::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-menu-options.png"alt-text="Operações de kit de ferramentas do Teams no menu Project":::

|Função  |Descrição  |
|---------|---------|
|Preparar dependências de aplicativo do Teams     |Antes de fazer uma depuração local, execute esta etapa, ela ajuda você a configurar as dependências de depuração locais e registrar o aplicativo Teams na plataforma do Teams. Você precisa de uma conta do Microsoft 365. Para obter mais informações, confira [Depurar seu aplicativo teams localmente usando o Visual Studio](debug-local.md)         |
|Abrir arquivo de manifesto     |Para abrir o arquivo de manifesto do Teams, você pode passar o mouse sobre os parâmetros para visualizar os valores. Para obter mais informações, confira [Editar manifesto de aplicativo do Teams usando o Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)         |
|Atualizar Manifesto no Portal do Desenvolvedor do Teams     |Quando você atualiza o arquivo de manifesto, só então você pode reimplantar o arquivo de manifesto no Azure sem implantar todo o projeto novamente. Use este comando para atualizar suas alterações no controle remoto. Para obter mais informações, confira [Editar manifesto de aplicativo do Teams usando o Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)       |
|Provisionar na nuvem     |Essa opção ajuda você a criar recursos do Azure que hospedam seu aplicativo do Teams. Para obter mais informações, consulte [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)        |
|Implantar na nuvem     |Essa opção ajuda você a copiar seu código para os recursos do Azure criados quando você fez "Provisionar na Nuvem". Para obter mais informações, confira [Implantar o aplicativo Teams na nuvem usando o Visual Studio](deploy.md#deploy-teams-app-to-the-cloud-using-visual-studio)        |
|Visualização no Teams     |Essa opção inicia o cliente Web do Teams e permite visualizar o aplicativo teams no navegador deles.         |
|Pacote Zip App     |Essa opção gera um pacote de aplicativos do Teams na `Build` pasta no projeto. Você pode carregar o pacote no cliente do Teams e executar o aplicativo Teams.         |

::: zone-end

## <a name="see-also"></a>Confira também

* [Instalar o Kit de Ferramentas do Teams](install-Teams-Toolkit.md)
* [Criar um novo aplicativo Teams usando o Kit de Ferramentas do Teams](create-new-project.md)
* [Preparar para criar aplicativos usando o Kit de Ferramentas do Microsoft Teams](build-environments.md)
* [Provisionar recursos de nuvem usando o Teams Toolkit](provision.md)
* [Criar um aplicativo do Teams no Visual Studio](create-new-project.md#create-new-teams-app-in-visual-studio)
* [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
* [Implantar o aplicativo teams na nuvem usando o Visual Studio](deploy.md#deploy-teams-app-to-the-cloud-using-visual-studio)

<!--  
:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/ui-elements.png" alt-text="UI Elements":::

|Section|Features|Details
|---------|---------|--------|
| **1. ACCOUNTS** | &nbsp; | &nbsp; |
| &nbsp; |Microsoft 365 account|  Use your Microsoft 365 account with a valid E5 subscription for building your app.|
| &nbsp; | Azure Account |  Use your Azure account for deploying app on Azure. You can [create a free Azure account](https://azure.microsoft.com/free/) before you start.|
|**2.ENVIRONMENT** |  &nbsp; | &nbsp;|
| &nbsp; |Local |Deploy your app in the default local environment with local machine environment configurations.|
| &nbsp; | Dev |Deploy your app in the default dev environment with remote or cloud environment configurations. You can create more environments, as you need.|
| **3.DEVELOPMENT** | &nbsp; | &nbsp; |
| &nbsp; | Create a new Teams app | Teams Toolkit helps you to create and customize your Teams app project that makes the Teams app development work simpler. Create a new Teams app helps you to start with Teams app development by creating new Teams project using Teams Toolkit either by using **Create new project**|
| &nbsp; | View Samples | Select any of Teams Toolkit's sample apps. The toolkit downloads the app code from GitHub, and you can build the sample app.|
| &nbsp; | Add Features | It helps you to add additional Teams capabilities such as **Tab** or **Bot** or **Message extension** or **Command bot** or **Notification bot**, or **SSO enabled tab** optionally add Azure resources such as **Azure SQL Database** or **Azure Key Vault**, or **Azure function** or **Azure API Management** which fits your development needs to your current Teams app. You can also add **API connection** or **Single Sign-on** or **CI/CD workflows** for your Teams app.
| &nbsp; | Edit Manifest file | It helps you customize manifest file based on the app requirements |
| **4.DEPLOYMENT** | &nbsp; | &nbsp; |
| &nbsp;| Provision in the cloud | Allocate Azure resources for your application. Teams Toolkit is integrated with Azure Resource Manager.|
| &nbsp; | Zip Teams metadata package| Create the app package that can be uploaded to Teams or Developer Portal. It contains the app manifest and app icons. |
| &nbsp; | Deploy to the cloud| Deploy the source code to Azure.|
| &nbsp; | Publish to Teams| Publish your developed app and distribute it to scopes, such as personal, team, channel, or organization.|
| &nbsp; | Developer Portal for Teams| It is the primary tool for configuring, distributing, and managing your Microsoft Teams apps. You can collaborate with colleagues on your app, set up runtime environments, and much more. |
| **5.HELP AND FEEDBACK** | &nbsp; | &nbsp; |
| &nbsp; | Get Started |  View the Teams Toolkit Get started help within Visual Studio Code.|
| &nbsp; | Tutorials| Select to access different tutorials.|
| &nbsp; | Documentation| Select to access the Microsoft Teams Developer Documentation.|
| &nbsp; | Report issues on GitHub| It helps to get **Quick support** from product expert. Browse the existing issues before you create a new one, or visit [StackOverflow tag `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) to submit feedback.|
| **6.Explorer** | &nbsp; | &nbsp; |
 &nbsp; | &nbsp; | It helps to view the directory structure of your app.|
| **7.Run and Debug** | &nbsp; | &nbsp; |
 &nbsp; | &nbsp; | To start the local or remote debug process.|
-->
