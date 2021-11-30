---
title: Preparar contas para criar Teams aplicativos
author: zyxiaoyuer
description: Preparar contas para criar Teams aplicativos
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 6a215922ff4b89c4afdce187be9b03479e6a54e6
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2021
ms.locfileid: "61227893"
---
# <a name="prepare-accounts-to-build-teams-apps"></a>Preparar contas para criar Teams aplicativos

Para desenvolver um Teams, pelo menos uma conta Microsoft 365 com uma assinatura válida é necessária. Se você quiser hospedar seus recursos de back-end no Azure, uma conta do Azure também será necessária. A conta do Azure será opcional se o aplicativo existente estiver hospedado em outro provedor de nuvem e você quiser integrar o aplicativo existente à Teams plataforma.

## <a name="microsoft-365-account"></a>Microsoft 365 Conta

Se você não tiver uma conta de Microsoft 365 existente com uma assinatura válida, poderá criar uma ao ingressar no programa Microsoft 365 [desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program) O Programa para Desenvolvedores do Microsoft 365 inclui uma assinatura de desenvolvedor do Microsoft 365 E5 que você pode usar para criar sua própria área restrita e desenvolver soluções independentes de seu ambiente de produção.

## <a name="azure-account"></a>Conta do Azure

Se você deseja hospedar recursos relacionados ao aplicativo ou acessar recursos no **Azure,** você deve ter uma assinatura do Azure. Você pode [criar uma conta gratuita](https://azure.microsoft.com/free/) antes de começar.

## <a name="join-microsoft-365-developer-program"></a>Ingressar Microsoft 365 programa desenvolvedor 

Se você não tiver uma conta Microsoft 365, inscreva-se para uma assinatura de programa [Microsoft 365 desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program) A assinatura é gratuita por 90 dias e continua a ser renovada desde que você a use para atividades de desenvolvimento. Se você tiver uma assinatura Visual Studio Enterprise ou Professional, ambos os programas incluirão uma assinatura Microsoft 365 [desenvolvedor gratuita.](https://aka.ms/MyVisualStudioBenefits) Ele está ativo enquanto sua assinatura Visual Studio está ativa. Para obter mais informações, [consulte configurar uma assinatura Microsoft 365 desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)

1. Vá para o programa [Microsoft 365 desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)
2. Selecione **Ingressar agora** e siga as instruções na tela.
3. Na tela de boas-vindas, selecione **Configurar assinatura do E5**.
4. Configurar sua conta de administrador. Depois de concluir, você deverá ver a seguinte tela:

:::image type="content" source="./images/m365-developer-program.png" alt-text="Diagrama que mostra o programa microsoft m365":::

## <a name="accounts-for-microsoft-365-developer-program"></a>Contas para Microsoft 365 programa de desenvolvedor

Você pode se inscrever no programa para desenvolvedores usando um dos seguintes tipos de conta:

- **Conta da Microsoft** 

Você pode criar para uso pessoal - fornece acesso a todos os produtos e serviços de nuvem voltados para o consumidor da Microsoft, como Outlook, Messenger, OneDrive, MSN, Xbox Live ou Microsoft 365. Sua inscrição para uma caixa de correio do Outlook.com cria automaticamente um conta da Microsoft. Depois da criação de uma conta da Microsoft, ela pode ser usada para acessar serviços em nuvem direcionados ao consumidor, ou o Azure.

- **Conta de trabalho**

 O administrador pode emitir problemas para uso empresarial - fornece acesso a todos os serviços de nuvem da Microsoft de pequeno, médio e corporativo, como o Azure, Microsoft Intune ou Microsoft 365. Quando você acessa um desses serviços como uma organização, um diretório de nuvem é provisionado automaticamente no Azure Active Directory para representar a sua organização.

- **Visual Studio ID**

Você pode criar para suas assinaturas Visual Studio Professional ou Enterprise – recomendamos que você use essa opção para ingressar no programa de desenvolvedor de dentro da Galeria Visual Studio para obter os benefícios completos como assinante Visual Studio.

## <a name="teams-customer-app-uploading-sideloading-permission-check"></a>Teams de carregamento de aplicativos do cliente (permissão de sideload)

> [!IMPORTANT]
> Durante o desenvolvimento, você deve carregar seu aplicativo em seu Teams sem distribuí-lo. Isso é conhecido como **sideload.**

Uma das maneiras de verificar se você tem uma conta Teams, verifique se você pode fazer sideload de aplicativos Teams:

1. No cliente Teams, selecione **Aplicativos** na barra esquerda.
2. Selecione **Gerenciar seus aplicativos**.
3. Verifique se você pode ver a opção Upload **um aplicativo personalizado,** conforme mostrado na imagem:

:::image type="content" source="./images/sideload-check.png" alt-text="Diagrama que mostra para carregar um aplicativo personalizado":::

Se você não puder Upload uma opção **de aplicativo** personalizada, isso indica que você não tem permissão de sideload. Sem a permissão de sideload, você não poderá fazer nenhuma depuração local/remota. Portanto, é muito importante obter a permissão de sideload para sua conta antes de fazer qualquer depuração para seu Teams app. Se você for administrador do seu locatário, poderá abrir a configuração de sideload para seu locatário/organização, enquanto se você não for administrador, entre em contato com o administrador do locatário para ter a permissão.

## <a name="enable-custom-app-uploading-sideloading--for-your-organization"></a>Habilitar o carregamento personalizado de aplicativos (sideload) para sua organização

> [!IMPORTANT]
> Para ativar o carregamento ou sideload de aplicativos personalizados para seu locatário de desenvolvedor, você deve ser o administrador do locatário.

1. Entre [no](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) Centro de administração do Microsoft 365 com suas credenciais de administrador.

2. Selecione **Mostrar todos os**  >  **Teams**.

:::image type="content" source="./images/admin-center-teams.png" alt-text="Diagrama que mostra o Teams de administração":::

> [!NOTE]
> Pode levar **até 24** horas para que a opção **Teams** apareça. Você pode [carregar seu aplicativo personalizado em um ambiente Teams para](/microsoftteams/upload-custom-apps) teste e validação nesse momento.

3. Navegue **até Teams configuração**  >  **de**  >  **aplicativos Global**.

:::image type="content" source="./images/teams-setup-policy.png" alt-text="Diagrama que mostra a política de instalação para Teams":::

4. Alterne Upload aplicativos personalizados para a **posição** On.

:::image type="content" source="./images/turn-on-sideload.png" alt-text="Diagrama que mostra como ativar o sideload":::

5. Selecione **Salvar**. Seu locatário de teste pode permitir o sideload de aplicativo personalizado.

:::image type="content" source="./images/save-sideload.png" alt-text="Diagrama que mostra a opção salvar":::

> [!Note]
> Pode levar até 24 horas para que o sideload seja ativo. Enquanto isso, você pode usar **[carregar para seu locatário]** para testar seu aplicativo. Para carregar o arquivo .zip pacote do aplicativo, consulte [upload custom apps](/microsoftteams/teams-app-setup-policies).

Para obter mais informações, consulte [manage custom app policies and settings in Teams](/microsoftteams/teams-custom-app-policies-and-settings) and manage app setup policies in [Teams](/microsoftteams/teams-app-setup-policies).

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Criar novo Teams projeto](create-new-project.md)

> [!div class="nextstepaction"]
> [Provisione recursos de nuvem](provision.md)
