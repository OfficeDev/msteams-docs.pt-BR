---
title: Preparar contas para criar o aplicativo Teams
author: zyxiaoyuer
description: Preparar contas para criar o aplicativo Teams
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/14/2022
ms.openlocfilehash: 21de5611daacbc00630cd7fa4b2aa3704788ed5e
ms.sourcegitcommit: ca902f505a125641c379a917ee745ab418bd1ce6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2022
ms.locfileid: "63464290"
---
# <a name="prepare-accounts-to-build-teams-apps"></a>Preparar contas para criar o aplicativo Teams

Para criar e carregar um Teams, você precisa preparar as seguintes contas:

* [Conta com assinatura válida do Microsoft 365.](accounts.md#microsoft-365-account)
* [Conta do Azure para hospedar os recursos de back-end no Azure](accounts.md#azure-account-to-host-backend-resources).

## <a name="microsoft-365-account"></a>Conta do Microsoft 365

Para criar uma conta Microsoft 365, inscreva-se em uma assinatura do Programa para Desenvolvedores do Microsoft 365. A assinatura é gratuita por 90 dias e continua a ser renovada desde que você a esteja usando em atividades de desenvolvimento.

Se você tiver uma assinatura do Visual Studio Enterprise ou Professional, ambos os programas incluem uma assinatura de [desenvolvedor gratuita](https://aka.ms/MyVisualStudioBenefits) do Microsoft 365. Ele estará ativo desde que sua assinatura do Visual Studio esteja ativa. Para obter mais informações, consulte [Assinatura de desenvolvedor do Microsoft 365](https://developer.microsoft.com/microsoft-365/dev-program).

### <a name="microsoft-365-developer-program"></a>Programa para desenvolvedores do Microsoft 365

Para obter uma conta de desenvolvedor gratuita do Teams, ingresse no desenvolvedor do Microsoft 365 e execute as seguintes etapas:

1. Acesse o [Programa para desenvolvedores do Microsoft 365](https://developer.microsoft.com/microsoft-365/dev-program).
2. Selecione **Ingressar agora**.
3. Selecione **Configurar a assinatura do E5**.
4. Configurar a conta de administrador.

   A imagem a seguir é exibida depois que você concluir a assinatura:

    :::image type="content" source="./images/m365-developer-program.png" alt-text="Diagrama que mostra o programa do Microsoft 365":::

### <a name="microsoft-365-developer-account-types"></a>Tipos de conta de desenvolvedor do Microsoft 365

Você pode se inscrever no programa para desenvolvedores usando um dos seguintes tipos de conta:

- **Conta da Microsoft para uso pessoal**

    A conta Microsoft fornece-lhe acesso a produtos e serviços na nuvem da Microsoft, como Outlook, Messenger, OneDrive, MSN, Xbox Live ou Microsoft 365. Você pode se inscrever em uma caixa de correio Outlook.com para criar uma conta Microsoft, que pode ser usada para acessar os serviços na nuvem da Microsoft ou do Azure relacionados ao consumidor.

- **Conta de trabalho da Microsoft para empresas**

     Essa conta fornece acesso a todos os serviços na nuvem da Microsoft de nível empresarial de pequeno, médio e grande porte, como Azure, Microsoft Intune ou Microsoft 365. Quando você acessa um desses serviços, como uma organização, um diretório na nuvem é provisionado automaticamente no Azure Active Directory (Azure AD) para representar sua organização.

- **ID de usuário do Visual Studio**

    A ID de usuário criada para usar a assinatura do Visual Studio Professional ou Enterprise pode ser usada para ingressar no programa de desenvolvedor na Galeria do Visual Studio para aproveitar todos os benefícios como assinante do Visual Studio.

## <a name="azure-account-to-host-backend-resources"></a>Conta do Azure para hospedar recursos de back-end

A conta do Azure será opcional se seu aplicativo existente estiver hospedado em outro provedor na nuvem e você quiser integrar o aplicativo existente na plataforma Teams.

**ID do Visual Studio**

Se você quiser hospedar recursos relacionados ao aplicativo ou acessar recursos no Azure, você pode [criar uma conta gratuita](https://azure.microsoft.com/free/) antes de começar. Como alternativa, você pode selecionar para hospedar seus recursos back-end usando outro provedor na nuvem ou em seus próprios servidores se eles estiverem disponíveis no domínio público.

## <a name="teams-custom-app-upload-or-sideload-permission"></a>Permissão de carregamento de aplicativos personalizados ou sideload do Teams

> [!IMPORTANT]
> Depois de criar o aplicativo, você deve carregar seu aplicativo no Teams sem distribuí-lo. Esse processo é conhecido como **sideload**.

   Você pode verificar se a permissão de sideload está habilitada usando o Visual Studio Code ou cliente do Teams.

* **Verificar a permissão de sideload usando o Visual Studio Code**

    1. Abra o **Visual Studio Code**.
    1. Selecione **Kit de ferramentas do Teams** no painel esquerdo. Se você não conseguir ver a opção, verifique se instalou a extensão do Kit de Ferramentas do Teams.
    1. Selecione **Contas** e faça logon da sua conta Microsoft 365.
    1. Verifique se você pode exibir a opção **Sideload habilitado** conforme mostrado na imagem a seguir:

       :::image type="content" source="../assets/images/teams-toolkit-v2/sideloading.png" alt-text="Habilitar o sideload" border="true":::

* **Verificar a permissão de sideload usando o cliente Teams**

    1. Abra o **Microsoft Teams**.
    2. Selecione **Aplicativos** no painel esquerdo.
    3. Selecione **Publicar um aplicativo**.

       :::image type="content" source="../assets/images/teams-toolkit-v2/publish.png" alt-text="Publicar um aplicativo" border="true":::

    4. Verifique se você pode ver a opção **Carregar um aplicativo personalizado**, conforme mostrado na imagem a seguir:

       :::image type="content" source="../assets/images/teams-toolkit-v2/upload.png" alt-text="Carregar um aplicativo personalizado" border="true":::.

        Se você não conseguir exibir a opção **Carregar um aplicativo personalizado**, isso indicará que você não tem a permissão necessária para sideload.
        * Quanto a um administrador de locatários, habilite a configuração do sideload do seu locatário ou organização no Centro de administração do Teams.
        * Se você não for um administrador de locatários, precisará entrar em contato com o administrador do locatário para habilitar o sideload.

### <a name="upload-your-custom-app"></a>Carregar seu aplicativo personalizado

> [!IMPORTANT]
> Para ativar o carregamento ou o sideload de aplicativos personalizados do seu locatário de desenvolvedor, você deve ser o administrador do seu locatário.

**Para carregar o aplicativo personalizado**

1. Acessar o [Centro de administração do Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com suas credenciais de administrador.

2. Selecione **Mostrar Tudo** > **Teams**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/5.png" alt-text="mostrar tudo" border="true":::

   > [!Note]
   > Pode levar **até 24 horas** para a opção **Teams** ser exibida. Você pode [carregar seu aplicativo personalizado em um ambiente do Teams](/microsoftteams/upload-custom-apps) para teste e validação.

3. Navegue até **Aplicativos do Teams** > **Políticas de Configuração**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/3.png" alt-text="definir políticas":::

4. Configurar alternar **Carregar aplicativos personalizados** para a posição **Ativado**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/4.png" alt-text="alternância":::

5. Selecione **Salvar**.

   > [!Note]
   > Pode levar até 24 horas para que os dados sejam preenchidos. Enquanto isso, você pode usar **carregamento do seu locatário** para testar seu aplicativo. Para carregar o arquivo do pacote .zip do aplicativo, consulte [Carregar aplicativos personalizados](/microsoftteams/teams-app-setup-policies).

Para obter mais informações, consulte [Gerenciar configurações e políticas de aplicativo personalizadas no Teams](/microsoftteams/teams-custom-app-policies-and-settings) e [Gerenciar políticas de configuração de aplicativo no Teams](/microsoftteams/teams-app-setup-policies).

## <a name="see-also"></a>Confira também

* [Criar um novo aplicativo Teams usando o Kit de Ferramentas do Teams](create-new-project.md)
* [Provisionar recursos de nuvem](provision.md)
* [Implantar o aplicativo Teams na nuvem](deploy.md)
* [Publique seu aplicativo Teams](TeamsFx-collaboration.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)