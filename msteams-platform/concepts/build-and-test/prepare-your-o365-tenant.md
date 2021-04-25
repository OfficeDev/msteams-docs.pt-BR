---
title: Preparar o locatário do Microsoft 365
description: Como começar a usar o Teams no Microsoft 365
ms.topic: how-to
keywords: Configurar o carregamento do Microsoft 365 tenant Teams
ms.openlocfilehash: 4fbe1dcc7ba202aff0b46c7fc50d9aebc0278c38
ms.sourcegitcommit: 7b4f383b506d4bc68a1b5641d6e0f404edbfbc6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2021
ms.locfileid: "51946463"
---
# <a name="prepare-your-microsoft-365-tenant"></a>Preparar o locatário do Microsoft 365

Os assinantes do Microsoft 365 podem desenvolver aplicativos para o Microsoft Teams com um dos seguintes planos:

* Básica
* Padrão
* Enterprise E1, E3 e E5
* Developer
* Education, Education Plus e Education E5

> [!NOTE]
> * Para obter mais informações sobre assinaturas do Microsoft 365, consulte [planos](https://products.office.com/business/compare-more-office-365-for-business-plans).
> * O Teams também está disponível para clientes que assinaram o E4 antes de sua [aposentadoria.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)

## <a name="create-your-development-environment"></a>Criar seu ambiente de desenvolvimento

Se você não tiver uma conta do Microsoft 365, deverá se inscrever para uma assinatura do Programa de Desenvolvedor [do Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program) A assinatura é gratuita por 90 dias e continua a ser renovada desde que você a use para atividades de desenvolvimento. Se você tiver uma assinatura Visual Studio Enterprise ou Professional, ambos os programas incluirão uma assinatura gratuita de [desenvolvedor do](https://aka.ms/MyVisualStudioBenefits)Microsoft 365 . Ele está ativo enquanto sua assinatura Visual Studio está ativa. Para obter mais informações, consulte configurar uma assinatura de [desenvolvedor do Microsoft 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).

## <a name="enable-teams-for-your-organization"></a>Habilitar o Teams para sua organização

Habilitar o Teams para sua organização e para obter mais informações, consulte [enableing Teams for your organization](/microsoftteams/enable-features-office-365).

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Habilitar aplicativos personalizados do Teams e ativar o carregamento personalizado de aplicativos

**Para ativar o carregamento ou sideload de aplicativos personalizados para seu locatário de desenvolvedor**

1. Entre no Centro de administração do [Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com suas credenciais de administrador.

2. Selecione **Mostrar todas as**  >  **Equipes**.

    ![Menu centro de administração](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > Pode levar até 24 horas para que a **opção Teams** apareça. Você pode [carregar seu aplicativo personalizado em um](/microsoftteams/upload-custom-apps#validate) ambiente do Teams para testes e validação nesse momento.

3. Navegue até **Políticas de Configuração de Aplicativos** do Teams  >    >  **Global**.

   ![Ativar o exibição de sideload](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Alternar **Carregar aplicativos personalizados** para a **posição** On.

5. Selecione **Salvar**. Seu locatário de teste pode permitir o sideload de aplicativo personalizado.

    > [!Note]
    > Pode levar até 24 horas para que o sideload seja ativo. Nesse ínterim, você pode usar **o upload para \<your tenant>** testar seu aplicativo. Para carregar o arquivo do pacote .zip do aplicativo, consulte [upload custom apps](/microsoftteams/upload-custom-apps#upload).

    ![Carregar exibição de aplicativo](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Para obter informações completas sobre como essas configurações interagem, consulte [manage custom app policies and settings in Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and manage app setup policies in [Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"] 
> [Escolher uma configuração de teste](~/concepts/build-and-test/debug.md)

