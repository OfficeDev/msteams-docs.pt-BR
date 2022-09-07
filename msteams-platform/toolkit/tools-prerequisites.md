---
title: Pré-requisitos para criar seu aplicativo Teams usando o Visual Studio Code
author: zyxiaoyuer
description: Neste módulo, conheça os pré-requisitos necessários para Ferramentas e SDK
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/14/2022
ms.openlocfilehash: 412b7bfedb6ba39f1d38f42aac56cc793ea385b1
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617016"
---
# <a name="prerequisites-for-creating-your-teams-app"></a>Pré-requisitos para criar seu aplicativo teams

Verifique se os seguintes pré-requisitos foram atendidos antes de começar a criar seu aplicativo teams:

* [Requisitos básicos para criar seu aplicativo teams](#basic-requirements-to-build-your-teams-app)
* [Preparar contas para criar seu aplicativo do Teams](#accounts-to-build-your-teams-app)
* [Permissão de sideload](#sideloading-permission)

## <a name="basic-requirements-to-build-your-teams-app"></a>Requisitos básicos para criar seu aplicativo teams

Verifique se os seguintes requisitos foram atendidos antes de começar a criar seu aplicativo do Teams:

| &nbsp; | Requisitos básicos | Para usar| Para o tipo de ambiente|
   | --- | --- | --- |
   | **Required** | &nbsp; | &nbsp; | &nbsp; |
   | &nbsp; | Kit de ferramentas do Teams| Uma extensão Visual Studio Code Microsoft que cria um scaffolding de projeto para seu aplicativo. Use a versão mais recente. | JavaScript e SPFx|
   | &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | Colabore com todas as pessoas com quem você trabalha por meio de aplicativos para chat, reuniões, chamadas – tudo em um só lugar.| JavaScript e SPFx|
   | &nbsp; | [Node.js](https://nodejs.org/en/download/) | Ambiente de runtime do JavaScript de back-end. Use a versão mais recente do v16 LTS.| JavaScript e SPFx|
   | &nbsp; |[NPM (Gerenciador de Pacotes de Nó)](https://www.npmjs.com/package/@microsoft/teamsfx) | Instale e gerencie pacotes para uso em Node.js e ASP.NET Core aplicativos.| JavaScript e SPFx|
   | &nbsp; | [Microsoft&nbsp; Edge](https://www.microsoft.com/edge) (recomendado) ou [Google Chrome](https://www.google.com/chrome/) | Um navegador com ferramentas de desenvolvedor. | JavaScript e SPFx|
   | &nbsp; | [Visual Studio Code](https://code.visualstudio.com/download) | Ambientes de compilação JavaScript, TypeScript ou Estrutura do SharePoint (SPFx). Use a versão 1.55 ou posterior. | JavaScript e SPFx|
   | **Opcional** | &nbsp; | &nbsp; | &nbsp; |
   | &nbsp; | [Ferramentas do Azure para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) [CLI do Azure](/cli/azure/install-azure-cli) | Acesse dados armazenados ou implante um back-end baseado em nuvem para seu aplicativo Teams no Azure. | JavaScript|
   | &nbsp; | [React Developer Tools para Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi) OU [React Developer Tools para Microsoft&nbsp;Edge](https://microsoftedge.microsoft.com/addons/detail/react-developer-tools/gpphkfbcpidddadnkolkpfckpihlkkil) | Uma extensão de DevTools do navegador para a biblioteca javaScript React software livre. | JavaScript|
   | &nbsp; | [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) | Uma ferramenta baseada em navegador que permite executar uma consulta de dados do Microsoft Graph. | JavaScript e SPFx|
   | &nbsp; | [Portal do Desenvolvedor do Teams](https://dev.teams.microsoft.com/) | Portal baseado na Web para configurar, gerenciar e distribuir seu aplicativo do Teams, inclusive para sua organização ou para a loja do Teams.| JavaScript e SPFx|

   > [!NOTE]
   >
   > * O documento é testado com o Kit de Ferramentas do Teams versão 4.0.0 e o Nodejs versão 16.
   > * Marcar o Explorador do Microsoft Graph para saber mais sobre os serviços do Microsoft Graph. Essa ferramenta baseada em navegador permite que você consulte e acesse o Microsoft Graph fora de um aplicativo.

## <a name="accounts-to-build-your-teams-app"></a>Contas para criar seu aplicativo teams

Verifique se você tem as seguintes contas antes de começar a criar seu aplicativo teams:

| Contas | Para usar| Para o tipo de ambiente|
| --- | --- |
|[Conta do Microsoft 365 com uma assinatura válida](#microsoft-365-developer-program)|Conta de desenvolvedor do Teams ao desenvolver um aplicativo.| JavaScript e SPFx|
|[Conta do Azure](accounts.md#azure-account-to-host-backend-resources)|Recursos de back-end no Azure.| JavaScript e SPFx|
|[Conta de administrador do site do conjunto do SharePoint](#sharepoint-collection-site-administrator-account) |Implantação para hospedagem.| SPFx|

### <a name="microsoft-365-developer-program"></a>Programa para desenvolvedores do Microsoft 365

Para criar uma conta do Microsoft 365, inscreva-se para obter uma assinatura do programa para desenvolvedores do Microsoft 365. A assinatura é gratuita por 90 dias e continua a ser renovada desde que você a esteja usando em atividades de desenvolvimento.

Se você tiver uma assinatura do Visual Studio Enterprise ou Professional, ambos os programas incluirão uma [assinatura gratuita de desenvolvedor](https://aka.ms/MyVisualStudioBenefits) do Microsoft 365. Ele estará ativo desde que sua assinatura do Visual Studio esteja ativa. Para obter mais informações, consulte [Assinatura de desenvolvedor do Microsoft 365](https://developer.microsoft.com/microsoft-365/dev-program).

Você pode se inscrever no programa para desenvolvedores usando um dos seguintes tipos de conta:

* **Conta da Microsoft para uso pessoal**

  :::row:::

    :::column span="3":::

       A conta fornece acesso a produtos e serviços na nuvem da Microsoft, como Outlook, Messenger, OneDrive, MSN, Xbox Live ou Microsoft 365. 

       Você pode se inscrever em uma caixa de correio do Outlook.com para criar uma conta Microsoft, que pode ser usada para acessar serviços na nuvem da Microsoft ou do Azure relacionados ao consumidor.

    :::column-end:::
    :::column span="1":::
             :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/personal-account-icon.png" alt-text="conta pessoal.":::
   :::column-end:::

  :::row-end:::

* **Conta de trabalho da Microsoft para empresas**

  :::row:::

    :::column span="3":::

       A conta fornece acesso a todos os serviços de nuvem da Microsoft de pequeno, médio e médio porte. Os serviços incluem o Azure, Microsoft Intune ou Microsoft 365. 

       Quando você se inscreve em um desses serviços como uma organização, um diretório baseado em nuvem é provisionado automaticamente no Microsoft Azure AD para representar sua organização.

    :::column-end:::
    :::column span="1":::
             :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/work-account-icon.png" alt-text="conta corporativa.":::
    :::column-end:::

  :::row-end:::

#### <a name="create-a-free-microsoft-365-developer-account"></a>Criar uma conta de desenvolvedor gratuita do Microsoft 365

Para criar uma conta de desenvolvedor gratuita do Microsoft 365, ingresse no programa de desenvolvedor do Microsoft 365 e execute a seguinte conta:

1. Acesse o [Programa para desenvolvedores do Microsoft 365](https://developer.microsoft.com/microsoft-365/dev-program).
1. Selecione **Ingressar agora**.
1. Configurar a conta de administrador.

   Você pode ver a seguinte imagem após a conclusão da assinatura:

    :::image type="content" source="../assets/images/teams-toolkit-v2/m365-account.png" alt-text="Conta do M365":::

### <a name="azure-account"></a>Conta do Azure

Você precisa de uma conta do Azure para hospedar um aplicativo do Teams ou os recursos de back-end para seu aplicativo teams usando o Kit de Ferramentas do Teams Visual Studio Code. Você deve precisar da assinatura do Azure nos seguintes cenários:

* Se você já tiver um aplicativo existente em um provedor de nuvem diferente do Azure e quiser integrar o aplicativo na plataforma Teams, deverá ter uma assinatura do Azure.
* Você pode selecionar uma assinatura do Azure para hospedar seus recursos de back-end usando outro provedor de nuvem ou em seus próprios servidores, se eles estiverem disponíveis no domínio público.

> [!NOTE]
> Você precisa criar [uma conta gratuita antes](https://azure.microsoft.com/free/) de começar.

### <a name="sharepoint-collection-site-administrator-account"></a>Conta de administrador do site do conjunto do SharePoint

Ao criar o aplicativo Teams usando o ambiente SPFx, você precisará da conta de administrador do site do conjunto do SharePoint na implantação para hospedagem. Se você estiver usando um locatário do programa de desenvolvedor do Microsoft 365, poderá usar a conta de administrador criada no momento.

## <a name="sideloading-permission"></a>Permissão de sideload

Depois de criar o aplicativo, você deve carregar seu aplicativo no Teams sem distribuí-lo. Esse processo é conhecido como sideload. Entre em sua conta do Microsoft 365 para exibir essa opção.

Você pode verificar se a permissão de sideload está habilitada usando o Visual Studio Code ou cliente do Teams.

<br>
<details>
<summary><b>Verificar a permissão de sideload usando o Visual Studio Code</b></summary>

1. Abra o **Visual Studio Code**.
1. Selecione o ícone do Kit de Ferramentas do :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: Teams na barra de ferramentas do Kit de Ferramentas do Teams.

   > [!NOTE]
   > Se você não conseguir ver a opção, consulte Instalar o [Kit](install-Teams-Toolkit.md) de Ferramentas do Teams para instalar a extensão kit de ferramentas do Teams Visual Studio Code.
1. Selecione **Entrar no M365 em** **CONTAS** e entre em sua conta do Microsoft 365.

    :::image type="content" source="../assets/images/teams-toolkit-v2/accounts.png" alt-text="detalhes das contas":::

1. Verifique se você pode exibir a opção **Sideload habilitado** conforme mostrado na imagem a seguir:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sideloading.png" alt-text="Habilitar o sideload":::

</details>
<br>
<details>
<summary><b>Verificar a permissão de sideload usando o cliente Teams</b></summary>

1. No cliente do Teams, selecione **Aplicativos**.
1. Selecione **Gerenciar seu aplicativo**.
1. Selecione **Carregar um aplicativo**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/upload-app.png" alt-text="Publicar um aplicativo":::

4. Verifique se você pode ver a opção **Carregar um aplicativo personalizado**, conforme mostrado na imagem a seguir:

    :::image type="content" source="../assets/images/teams-toolkit-v2/upload-custom-app1.png" alt-text="Carregar um aplicativo personalizado":::.

</details>

### <a name="enable-sideloading-using-admin-center"></a>Habilitar o sideload usando o centro de administração

Se você não conseguir exibir a opção Carregar um aplicativo personalizado, isso indicará que você não tem **a** permissão necessária para sideload.

* Quanto a um administrador de locatários, habilite a configuração do sideload do seu locatário ou organização no Centro de administração do Teams.
* Se você não for um administrador de locatários, precisará entrar em contato com o administrador do locatário para habilitar o sideload.

Se você tiver direitos de administrador, execute as seguintes etapas para carregar o aplicativo personalizado usando o centro de administração:

  1. Entre no [Centro de administração do Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com suas credenciais de administrador.

  1. Selecione o ícone :::image type="icon" source="../assets/images/teams-toolkit-v2/showall icon.PNG"::: > **Teams**.

       :::image type="content" source="../assets/images/teams-toolkit-v2/m365-admin-center.png" alt-text="Administração Microsoft 365 central":::

     > [!Note]
     > Pode levar **até 24 horas** para a opção **Teams** ser exibida. Você pode [carregar seu aplicativo personalizado em um ambiente do Teams](/microsoftteams/upload-custom-apps) para teste e validação.

  1. Entre no Centro de administração do Microsoft Teams com suas credenciais de administrador.
  1. Selecione o ícone > :::image type="icon" source="../assets/images/teams-toolkit-v2/showall icon.PNG"::: **configuração de aplicativos** > **do** Teams.

     :::image type="content" source="../assets/images/teams-toolkit-v2/m365-admin-center1.png" alt-text="Administração Microsoft 365 center1":::

  1. Selecionar **Global (padrão em toda a organização)**

     :::image type="content" source="../assets/images/teams-toolkit-v2/select-manage-policies.png" alt-text="Selecionar Gerenciar Políticas":::

  1. Configurar alternar **Carregar aplicativos personalizados** para a posição **Ativado**.

     :::image type="content" source="../assets/images/teams-toolkit-v2/Upload-custom-apps.png" alt-text="Carregar aplicativos personalizados":::

  5. Selecione **Salvar**.

     > [!Note]
     > Pode levar até 24 horas para que os dados sejam preenchidos. Enquanto isso, você pode usar **carregamento do seu locatário** para testar seu aplicativo. Para carregar o arquivo do pacote .zip do aplicativo, consulte [Carregar aplicativos personalizados](/microsoftteams/teams-app-setup-policies).

     Verifique se, agora você tem a permissão de sideload usando as etapas mencionadas na verificação da permissão de [sideload usando o Visual Studio Code ou o cliente do Teams.](#sideloading-permission)

</details>

## <a name="see-also"></a>Confira também

* [Gerenciar políticas de aplicativo personalizado e as configurações no Teams](/microsoftteams/teams-custom-app-policies-and-settings)
* [Gerenciar políticas de configuração de aplicativo no Teams](/microsoftteams/teams-app-setup-policies)
* [Carregar aplicativos personalizados](/microsoftteams/teams-app-setup-policies)
* [Provisionar recursos de nuvem usando o Kit de Ferramentas do Teams](provision.md)
* [Implantar o aplicativo Teams na nuvem](deploy.md)
