---
title: Preparar contas para criar Teams aplicativos
author: zyxiaoyuer
description: Preparar contas para criar Teams aplicativos
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 9dbfa97b892f2234b53eb42b5d5764b8f6fd6e93
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63452568"
---
# <a name="prepare-accounts-to-build-teams-apps"></a>Preparar contas para criar Teams aplicativos

Para desenvolver Teams aplicativo, você precisa de pelo menos uma Microsoft 365 com assinatura válida. Se você quiser hospedar seus recursos de back-end no Azure, precisará de uma conta do Azure. A conta do Azure será opcional se o aplicativo existente estiver hospedado em outro provedor de nuvem e você quiser integrar o aplicativo existente à Teams plataforma.

## <a name="microsoft-365-account"></a>Conta do Microsoft 365

Se você não tiver uma conta de Microsoft 365 existente com uma assinatura válida, poderá criar uma ao ingressar no programa Microsoft 365 [desenvolvedor](https://developer.microsoft.com/microsoft-365/dev-program). O Microsoft 365 de desenvolvedor inclui uma assinatura de desenvolvedor Microsoft 365 E5 que você pode usar para criar sua própria área de segurança e desenvolver soluções independentemente do seu ambiente de produção.

## <a name="azure-account"></a>Conta do Azure

Se quiser hospedar recursos relacionados ao aplicativo ou acessar recursos no Azure, você deve ter uma assinatura do Azure. Você pode [criar uma conta gratuita](https://azure.microsoft.com/free/) antes de começar.

## <a name="join-microsoft-365-developer-program"></a>Ingressar Microsoft 365 programa de desenvolvedor

Se você não tiver uma conta Microsoft 365, inscreva-se para uma assinatura de programa Microsoft 365 [desenvolvedor](https://developer.microsoft.com/microsoft-365/dev-program). A assinatura é gratuita por 90 dias e continua a ser renovada desde que você a use para atividades de desenvolvimento. Se você tiver uma assinatura Visual Studio Enterprise ou Professional, ambos os programas incluem uma assinatura Microsoft 365 [desenvolvedor gratuita](https://aka.ms/MyVisualStudioBenefits). Ele está ativo enquanto sua assinatura Visual Studio está ativa. Para obter mais informações, [consulte configurar uma assinatura Microsoft 365 desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)

1. Vá para o programa Microsoft 365 [desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)
2. Selecione **Ingressar agora**.
3. Selecione **Configurar assinatura do E5**.
4. Configurar sua conta de administrador. Depois de concluir, você deverá ver a seguinte tela:

:::image type="content" source="./images/m365-developer-program.png" alt-text="Diagrama que mostra Microsoft 365 programa":::

## <a name="accounts-for-microsoft-365-developer-program"></a>Contas para Microsoft 365 programa de desenvolvedor

Você pode se inscrever no programa para desenvolvedores usando um dos seguintes tipos de conta:

* **Conta da Microsoft para uso pessoal**

  Fornece acesso a todos os produtos e serviços de nuvem da Microsoft orientados para o consumidor, como Outlook, Messenger, OneDrive, MSN, Xbox Live ou Microsoft 365. Sua inscrição para uma caixa de correio do Outlook.com cria automaticamente um conta da Microsoft. Depois da criação de uma conta da Microsoft, ela pode ser usada para acessar serviços em nuvem direcionados ao consumidor, ou o Azure.

* **Conta de trabalho para empresas**

  Fornece acesso a todos os serviços de nuvem da Microsoft de pequeno, médio e corporativo, como o Azure, Microsoft Intune ou Microsoft 365. Ao se inscrever em um desses serviços como organização, um diretório baseado em nuvem é provisionado automaticamente no Microsoft Azure Active Directory (Azure AD) para representar sua organização.

* **Visual Studio ID**

  Você pode criar para suas assinaturas de Visual Studio Professional ou Enterprise – recomendamos que você use essa opção para ingressar no programa de desenvolvedor de dentro da Galeria Visual Studio para obter os benefícios completos como assinante Visual Studio.

## <a name="teams-customer-app-upload-or-sideload-permission"></a>Teams de carregamento ou sideload de aplicativos do cliente

> [!IMPORTANT]
> Durante o desenvolvimento, você deve carregar seu aplicativo em seu Teams sem distribuí-lo. Isso é conhecido como **sideload**.

A lista a seguir fornece etapas para verificar se a permissão do aplicativo de sideload está habilitada. As duas maneiras diferentes são as seguinte:

* **Para usar o código do Microsoft Visual studio**

    1. Abra **Visual Studio Code**.
    1. Selecione **Teams Toolkit** no painel esquerdo.
    1. Selecione **Contas** e faça logoff em sua Microsoft 365 de usuário.
    1. Verifique se você pode ver a opção **Sideloading habilitada** conforme mostrado na imagem:

       :::image type="content" source="../assets/images/teams-toolkit-v2/sideloading.png" alt-text="Habilitar o sideload":::

* **Para usar Teams conta**

    1. Abra **Microsoft Teams**.
    2. Selecione **Aplicativos** na barra esquerda.
    3. Selecione **Publicar um aplicativo**.

       :::image type="content" source="../assets/images/teams-toolkit-v2/publish.png" alt-text="Publicar um aplicativo":::

    4. Verifique se você pode ver a opção Upload **um aplicativo personalizado**, conforme mostrado na imagem:

       :::image type="content" source="../assets/images/teams-toolkit-v2/upload.png" alt-text="Upload um aplicativo personalizado":::

Se você não puder ver Upload uma opção **de** aplicativo personalizada, isso indica que você não tem permissão para sideload. Sem a permissão de sideload, você não poderá fazer nenhuma depuração local ou remota. Portanto, é muito importante obter a permissão de sideload para sua conta antes de fazer qualquer depuração para seu Teams app. Se você for administrador do seu locatário, poderá abrir a configuração de sideload para seu locatário ou organização. Se você não for um administrador, contate o administrador do locatário para a permissão.

## <a name="enable-custom-app-uploading-for-your-organization"></a>Habilitar o carregamento personalizado de aplicativos para sua organização

> [!IMPORTANT]
> Para ativar o carregamento ou sideload de aplicativos personalizados para seu locatário de desenvolvedor, você deve ser o administrador do locatário.

1. Entre [no Centro de administração do Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com suas credenciais de administrador.

2. Selecione **Mostrar Tudo** >  **Teams**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/5.png" alt-text="mostrar tudo":::

> [!NOTE]
> Pode levar **até 24** horas para que a opção **Teams** apareça. Você pode [carregar seu aplicativo personalizado em um ambiente Teams para](/microsoftteams/upload-custom-apps) teste e validação nesse momento.

3. Navegue **até Teams** **appsSetup** >  **PoliciesGlobal** > .

   :::image type="content" source="../assets/images/teams-toolkit-v2/3.png" alt-text="definir olicies":::

4. Alterne Upload aplicativos personalizados para a **posição** On.

   :::image type="content" source="../assets/images/teams-toolkit-v2/4.png" alt-text="alternância":::

5. Selecione **Salvar**.

> [!Note]
> Pode levar até 24 horas para que o sideload seja ativo. Enquanto isso, você pode usar **o carregamento para seu locatário** testar seu aplicativo. Para carregar o arquivo .zip pacote do aplicativo, consulte [carregar aplicativos personalizados](/microsoftteams/teams-app-setup-policies).

Para obter mais informações, consulte [manage custom app policies and settings in Teams](/microsoftteams/teams-custom-app-policies-and-settings) and [manage app setup policies in Teams](/microsoftteams/teams-app-setup-policies).

## <a name="see-also"></a>Confira também

* [Criar novo Teams projeto](create-new-project.md)
* [Provisionar recursos de nuvem](provision.md)
