---
title: Explorar o Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Neste módulo, saiba mais sobre como explorar o Kit de Ferramentas do Teams
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 07/29/2022
ms.openlocfilehash: 0ef95064a1715a64d8f719c54aced7cdc74ecb23
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617062"
---
# <a name="explore-teams-toolkit"></a>Explorar o Kit de Ferramentas do Teams

Neste documento, você pode entender diferentes elementos de interface do usuário, juntamente com a descrição e o uso básico no Kit de Ferramentas do Teams.

## <a name="teams-toolkit-basic-ui-elements"></a>Elementos básicos da interface do usuário do Kit de Ferramentas do Teams

Após a instalação do Kit de Ferramentas do Teams, você verá a interface do usuário do Kit de Ferramentas do Teams, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/overview1.png" alt-text="Visão geral do Kit de Ferramentas do Teams":::

| Número de série | Elementos da interface do usuário | Definição |
| --- | --- |
| 1 | **Introdução** | Explore o Kit de Ferramentas do Teams. |
| &nbsp; | **Tutoriais** | Acesse diferentes tutoriais. |
| &nbsp; | **Documentação** | Acesse a Documentação do Desenvolvedor do Microsoft Teams. |
| 2 | **Criar um novo aplicativo do Teams** | Crie um novo aplicativo teams com base em suas necessidades. |
| 3 | **Exibir exemplos** | Crie diferentes tipos de aplicativo com base em exemplos existentes. |
| 4 | **Abrir Pasta** | Abra o aplicativo Teams existente. |
| 5 | **Novo Arquivo** | Crie um novo arquivo. |
| &nbsp; | **Abrir Arquivo** | Abra o arquivo existente. |
| &nbsp; | **Abrir Pasta** | Abra a pasta existente. |
| 6 | **Recente** | Exiba os arquivos recentes. |

### <a name="exploring-the-teams-toolkit-task-pane"></a>Explorando o painel de tarefas do Kit de Ferramentas do Teams

Você pode explorar mais elementos da interface do usuário no painel de tarefas no Kit de Ferramentas do Teams. O painel de tarefas fica visível somente depois de criar um aplicativo usando o Kit de Ferramentas do Teams. O vídeo a seguir ajuda você a saber mais sobre o processo de criação de um novo aplicativo do Teams e, após esse processo, você pode exibir o painel de tarefas no Kit de Ferramentas do Teams.

   ![Criar um aplicativo do Teams](~/assets/videos/javascript-tab-app1.gif)

Depois de criar um novo aplicativo teams, você pode ver a estrutura de diretório do aplicativo no painel esquerdo e o arquivo leiame no painel direito.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/first-page.png" alt-text="Primeira página do Kit de Ferramentas do Teams":::

Vamos fazer um tour pela interface do usuário do Kit de Ferramentas do Teams.

 Na Visual Studio Code de ferramentas, os seguintes ícones são relevantes para o Kit de Ferramentas do Teams:

| Ícone | Descrição |
| --- | --- |
| **Explorador** :::image type="icon" source="../assets/images/teams-toolkit-v2/file-explorer-icon.PNG":::  | Para exibir a estrutura de diretório do aplicativo. |
| **Executar e depurar** :::image type="icon" source="../assets/images/teams-toolkit-v2/run-debug-icon.PNG":::  | Para iniciar o processo de depuração local ou remoto. |
| **Kit de ferramentas do Teams** :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: | Para exibir o painel de tarefas no Kit de Ferramentas do Teams. |

No painel de tarefas, você pode ver as seguintes seções:

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/accounts1.png" alt-text="seção contas":::
   :::column-end:::
   :::column span="":::

        Para desenvolver um aplicativo do Teams, você precisa das seguintes contas:
        
        * **Entre no M365**: use sua conta do Microsoft 365 com uma assinatura válida do E5 para criar seu aplicativo.

        * **Entre no Azure**: use sua conta do Azure para implantar o aplicativo no Azure. Você pode [criar uma conta gratuita do Azure](https://azure.microsoft.com/free/) antes de começar.
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/environment1.png" alt-text="Seção de ambiente":::
   :::column-end:::
   :::column span="":::

        Para implantar o aplicativo Teams, você precisa dos seguintes ambientes:
        
       * **local**: implante seu aplicativo no ambiente local padrão com configurações de ambiente de computador local.

        * **desenvolvimento**: implante seu aplicativo no ambiente de desenvolvimento padrão com configurações de ambiente remoto ou de nuvem. Você pode criar mais ambientes, conforme necessário.
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/development.png" alt-text="Seção de desenvolvimento":::
   :::column-end:::
   :::column span="":::

        Para criar e personalizar seu aplicativo teams, você precisa dos seguintes recursos:
        
       * **Criar um novo aplicativo do Teams**: use o assistente do kit de ferramentas para preparar o scaffolding de projeto para o desenvolvimento de aplicativos.

        * **Exibir exemplos**: selecione qualquer um dos aplicativos de exemplo do Kit de Ferramentas do Teams. O kit de ferramentas baixa o código do aplicativo do GitHub e você pode criar o aplicativo de exemplo.
        
        * **Adicionar recursos**: adicione outros recursos necessários do Teams ao aplicativo Teams durante o processo de desenvolvimento e adicione recursos opcionais de nuvem adequados para seu aplicativo.
       
        * **Editar arquivo de manifesto**: edite a integração do aplicativo Teams ao cliente do Teams.
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deployment1.png" alt-text="Seção implantação":::
   :::column-end:::
   :::column span="":::

        Para provisionar, implantar e publicar seu aplicativo do Teams, você precisa dos seguintes recursos:
        
        * **Provisionar na nuvem**: aloque recursos do Azure para seu aplicativo. O Kit de ferramentas do Teams está integrado ao Gerenciador de Recursos do Teams.

        * **Pacote de metadados do Zip Teams**: crie o pacote do aplicativo que pode ser carregado no Teams ou no Portal do Desenvolvedor. Ele contém o manifesto do aplicativo e os ícones do aplicativo.
        
        * **Implantar na nuvem**: implante o código-fonte no Azure.
       
        * **Publicar no Teams**: publique seu aplicativo desenvolvido e distribua-o para escopos, como pessoal, equipe, canal ou organização.
        
        * **Portal do Desenvolvedor para Teams**: use o Portal do Desenvolvedor para configurar e gerenciar seu aplicativo do Teams. 
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/help-and-feedback1.png" alt-text="Seção Ajuda e comentários":::
   :::column-end:::
   :::column span="":::

        Para acessar mais informações sobre o Kit de Ferramentas do Teams. você precisa da documentação e dos recursos a seguir.
        
        * **Introdução**: Veja a ajuda de Introdução ao Kit de Ferramentas do Teams Visual Studio Code.

        * **Tutoriais**: selecione para acessar tutoriais diferentes.
        
        * **Documentação**: Selecione para acessar a Documentação do Desenvolvedor do Microsoft Teams.
       
        * **Relatar problemas no GitHub**: selecione para acessar a página do GitHub e gerar problemas.
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Confira também

* [Instalar o Kit de Ferramentas do Teams](install-Teams-Toolkit.md)
* [Criar um novo aplicativo Teams usando o Kit de Ferramentas do Teams](create-new-project.md)
* [Preparar-se para criar aplicativos usando o Kit de Ferramentas do Microsoft Teams](build-environments.md)
* [Provisionar recursos de nuvem usando o Kit de Ferramentas do Teams](provision.md)

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
