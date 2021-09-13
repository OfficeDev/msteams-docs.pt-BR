---
title: Preparar o locatário do Microsoft 365
description: Como começar a usar Teams no Microsoft 365
ms.topic: how-to
ms.localizationpriority: medium
keywords: Configurar Microsoft 365 locatário Teams carregamento
ms.openlocfilehash: 83d45d567c11ff26b5c788371cd4a676f9c3ca2c
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155047"
---
# <a name="prepare-your-microsoft-365-tenant"></a>Preparar o locatário do Microsoft 365

Microsoft 365 assinantes podem desenvolver aplicativos para Microsoft Teams com um dos seguintes planos:

* Básico
* Padrão
* Enterprise E1, E3 e E5
* Developer
* Education, Education Plus e Education E5

> [!NOTE]
> * Para obter mais informações sobre Microsoft 365 assinaturas, consulte [planos](https://products.office.com/business/compare-more-office-365-for-business-plans).
> * Teams também está disponível para clientes que assinaram o E4 antes de sua [aposentadoria.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)

## <a name="create-your-development-environment"></a>Criar seu ambiente de desenvolvimento

Se você não tiver uma conta Microsoft 365, você deve se inscrever para uma assinatura Microsoft 365 programa de [desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program) A assinatura é gratuita por 90 dias e continua a ser renovada desde que você a use para atividades de desenvolvimento. Se você tiver uma assinatura Visual Studio Enterprise ou Professional, ambos os programas incluirão uma assinatura Microsoft 365 [desenvolvedor gratuita.](https://aka.ms/MyVisualStudioBenefits) Ele está ativo enquanto sua assinatura Visual Studio está ativa. Para obter mais informações, [consulte configurar uma assinatura Microsoft 365 desenvolvedor.](/office/developer-program/office-365-developer-program-get-started)

## <a name="enable-teams-for-your-organization"></a>Habilitar Teams para sua organização

Enable Teams for your organization and for more information, see [enableing Teams for your organization](/microsoftteams/enable-features-office-365).

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Habilitar Teams aplicativos personalizados e ativar o carregamento personalizado de aplicativos

**Para ativar o carregamento ou sideload de aplicativos personalizados para seu locatário de desenvolvedor**

1. Entre [no](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) Centro de administração do Microsoft 365 com suas credenciais de administrador.

2. Selecione **Mostrar todos os**  >  **Teams**.

    ![Menu centro de administração](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > Pode levar até 24 horas para que a opção **Teams** apareça. Você pode [carregar seu aplicativo personalizado em um ambiente Teams para](/microsoftteams/upload-custom-apps#validate) teste e validação nesse momento.

3. Navegue **até Teams configuração**  >  **de**  >  **aplicativos Global**.

   ![Ativar o exibição de sideload](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Alterne **Upload aplicativos personalizados** para a **posição** On.

5. Selecione **Salvar**. Seu locatário de teste pode permitir o sideload de aplicativo personalizado.

    > [!Note]
    > Pode levar até 24 horas para que o sideload seja ativo. Nesse ínterim, você pode usar **o upload para \<your tenant>** testar seu aplicativo. Para carregar o arquivo .zip pacote do aplicativo, consulte [upload custom apps](/microsoftteams/upload-custom-apps#upload).

    ![Upload de aplicativo](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Para obter informações completas sobre como essas configurações interagem, consulte [manage custom app policies and settings in Teams](/microsoftteams/teams-custom-app-policies-and-settings) and manage app setup policies in [Teams](/microsoftteams/teams-app-setup-policies).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"] 
> [Escolher uma configuração de teste](~/concepts/build-and-test/debug.md)

