---
title: Criar aplicativos com o Teams Toolkit e Visual Studio
description: Começar a criar grandes aplicativos personalizados diretamente Visual Studio com o Microsoft Teams Toolkit. Aprenda a configurar seu aplicativo Visual Studio, validar seu aplicativo e publicá-lo no Visual Studio e no Portal do Desenvolvedor.
keywords: kit de ferramentas do visual studio do teams
ms.localizationpriority: medium
ms.topic: overview
ms.date: 1/13/2022
ms.author: johmil
ms.openlocfilehash: c34f1113cd4da5f1b416dba6bc950b3588accecf
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453417"
---
# <a name="teams-toolkit-for-visual-studio"></a>Kit de ferramentas do Teams para Visual Studio

Crie, teste e desenvolva para Teams dentro do seu IDE.

A extensão do Teams Toolkit para o Visual Studio facilita a criação de novos projetos para o Teams, configurar automaticamente aplicativos no Portal do Desenvolvedor do Teams, executar e depurar no Teams, configurar a hospedagem na nuvem e usar o [TeamsFx](https://github.com/OfficeDev/teamsfx) a partir do seu IDE.

## <a name="install-teams-toolkit-for-visual-studio"></a>Instalar Teams Toolkit para Visual Studio

>[!NOTE]
> Como pré-requisito, certifique-se de usar o Visual Studio 2022 17.1 Preview 2 ou mais novo para seguir as instruções a seguir.

1. Se você já tiver Visual Studio versão 2022 17.1 Preview 2 instalada, pule para a próxima etapa. Caso contrário, [instale o Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/).
2. Abra o Instalador do Visual Studio.
3. Selecione **Modificar** para a instalação existente do VS 2022 Preview.
4. Selecione o ASP.NET **e a carga de trabalho de desenvolvimento da Web**.
5. À direita, expanda a seção ASP.NET e desenvolvimento da **Web** e selecione Microsoft Teams ferramentas de **desenvolvimento na lista** opcional de componentes.
6. Selecione **Instalar** ou **Modificar** no Instalador do Visual Studio para concluir o processo de instalação.

![Selecionando as Microsoft Teams de desenvolvimento no Visual Studio instalador.) instalado.](images/teams-development-tools-vs-installer.png)

## <a name="get-started-quickly-with-a-new-project"></a>Começar rapidamente com um novo projeto

Teams Toolkit modelos de projeto fornecem todos os códigos, arquivos e configurações que você precisa para começar com um projeto Teams aplicativo.

O Microsoft Teams de projeto do App permite que você especifique uma conta Microsoft 365 que é necessária para registrar e configurar automaticamente seu novo Teams app.

> [!NOTE]
> Se você não tiver uma conta Microsoft 365, poderá inscrever-se para uma assinatura Microsoft 365 [programa de desenvolvedor](https://developer.microsoft.com/microsoft-365/dev-program). Ele é gratuito por 90 dias e é renovado desde que você o use para atividades de desenvolvimento. Se você tiver uma assinatura de Visual Studio Enterprise ou Professional, ambos os programas incluirão uma assinatura de desenvolvedor Microsoft 365 [gratuita, ativa](https://aka.ms/MyVisualStudioBenefits) para o tempo de vida da sua assinatura Visual Studio. Para obter mais informações, [consulte configurar uma assinatura Microsoft 365 desenvolvedor.](/office/developer-program/office-365-developer-program-get-started)

1. Iniciar Visual Studio 2022.
1. Na janela inicial, escolha **Criar um novo projeto**.
1. Na caixa **Pesquisar modelos**, digite Microsoft Teams App.
1. Selecione o **Microsoft Teams de aplicativo** e selecione **Next**.
1. Na janela **Configurar seu novo projeto**, digite ou insira _HelloTeams_ na caixa **Project nome**. Em seguida, selecione **Criar**.
1. Na janela **Criar um novo** aplicativo Teams, escolha ou entre em uma conta Microsoft 365 usando o seletor **Escolher uma** conta. Em seguida, selecione **Criar**.

![Criando um novo projeto Microsoft Teams App no Visual Studio.](images/teams-toolkit-vs-new-project.png)

Visual Studio abrirá seu novo projeto e Teams Toolkit o novo projeto no Teams Portal do Desenvolvedor. O projeto será adicionado para a organização Teams vinculada à conta Microsoft 365 que você escolheu nas etapas acima e criará um novo Azure Active Directory registro. Isso é necessário para que o aplicativo seja executado Teams.

## <a name="run-and-debug-your-app-in-teams"></a>Executar e depurar seu aplicativo em Teams

Você pode iniciar seu projeto de aplicativo em execução localmente Visual Studio.

1. Abra ou [crie um projeto Teams aplicativo.](#get-started-quickly-with-a-new-project)
2. Pressione **F5** ou selecione **Depurar > Iniciar a Depuração** no Visual Studio.

Visual Studio iniciará seu projeto Teams aplicativo em um navegador e iniciará a depuração.

## <a name="host-your-teams-app-in-the-cloud-and-preview-it"></a>Hospedar seu Teams aplicativo na nuvem e visualiza-lo

Você pode criar e configurar automaticamente recursos de nuvem para hospedar seu aplicativo no Azure usando Teams Toolkit.

1. Selecione o **Project > Teams Toolkit > provisionamento no** menu Nuvem.
2. Na janela Selecionar sua assinatura, escolha a assinatura do Azure com a qual você deseja usar para criar recursos.

Teams Toolkit criará recursos do Azure nesta assinatura, mas nenhum código será implantado durante esta etapa. Para implantar seu projeto nesses novos recursos:

1. Selecione o **Project > Teams Toolkit > Implantar no** menu Nuvem.

## <a name="preview-your-app-running-from-cloud-resources"></a>Visualizar seu aplicativo em execução a partir de recursos de nuvem

Você pode executar seu aplicativo em um navegador usando os recursos remotos para verificar se tudo funciona. Ainda não é possível depurar durante esse cenário.

1. Selecione o **menu Project > Teams Toolkit > Visualização Teams aplicativo**.

Seu aplicativo abrirá em um navegador e usará os recursos criados pelas etapas Provisionar e Implantar.

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

No [Portal](https://dev.teams.microsoft.com/home) do Desenvolvedor do Teams, você pode carregar seu aplicativo em uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da sua empresa para usuários em sua organização ou enviar seu aplicativo para a Fonte de Aplicativos para todos os Teams usuários.

- Seu administrador de TI revisará esses envios.
- Você pode retornar à página **Publicar** para verificar o status do envio e saber se seu aplicativo foi aprovado ou rejeitado pelo administrador de TI. Isso também é onde você pode enviar atualizações para seu aplicativo ou cancelar quaisquer envios ativos no momento.
