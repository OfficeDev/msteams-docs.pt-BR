---
title: Preparar seu locatário do Microsoft 365
description: Como começar a usar o Teams no Microsoft 365
ms.topic: how-to
keywords: Configurar o carregamento do Microsoft 365 tenant Teams
ms.openlocfilehash: aa7f994744f8b1c62aa32122a5006cfa0f22d391
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634745"
---
# <a name="prepare-your-microsoft-365-tenant"></a>Preparar seu locatário do Microsoft 365

Os assinantes do Microsoft 365 podem desenvolver aplicativos para o Microsoft Teams com um dos seguintes planos:

* Básica
* Padrão
* Enterprise E1, E3 e E5
* Developer
* Education, Education Plus e Education E5

> [!NOTE]
> Para obter mais informações sobre assinaturas do Microsoft 365, consulte [planos](https://products.office.com/business/compare-more-office-365-for-business-plans).
> 
> O Microsoft Teams também está disponível para clientes que assinaram o E4 antes de sua [aposentadoria.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)

## <a name="create-your-development-environment"></a>Criar seu ambiente de desenvolvimento

Se você não tiver uma conta do Microsoft 365, deverá se inscrever para uma assinatura do Programa de Desenvolvedor [do Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program) A assinatura é gratuita por 90 dias e continua a ser renovada desde que você a use para atividades de desenvolvimento. Se você tiver uma assinatura Visual Studio Enterprise ou Professional, ambos os programas incluirão uma assinatura gratuita de [desenvolvedor do](https://aka.ms/MyVisualStudioBenefits)Microsoft 365 . Ele está ativo enquanto sua assinatura Visual Studio está ativa. Para obter mais informações, consulte Configurar uma assinatura de desenvolvedor do [Microsoft 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).

## <a name="enable-microsoft-teams-for-your-organization"></a>Habilitar o Microsoft Teams para sua organização

Habilita o Microsoft Teams para sua organização e confira nossas diretrizes detalhadas para habilitar o [Teams para sua organização.](/microsoftteams/enable-features-office-365)

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Habilitar aplicativos personalizados do Teams e ativar o carregamento personalizado de aplicativos

**Para ativar o carregamento ou sideload de aplicativos personalizados para seu locatário de desenvolvedor**

1. Entre no Centro de administração do [Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com suas credenciais de administrador.

2. Selecione **Mostrar todas as**  >  **Equipes**.

    ![imagem do menu do centro de administração](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > Pode levar até 24 horas para que a **opção Teams** apareça. Você pode [carregar seu aplicativo personalizado em um](/microsoftteams/upload-custom-apps#validate) ambiente do Teams para testes e validação nesse momento.

3. Navegue até **Políticas de Configuração de Aplicativos** do Teams  >    >  **Global**.

   ![ativar o sideload view](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Alterne **o carregamento de aplicativos** personalizados para a **posição** on.

5. Selecione **Salvar**.
   Seu locatário de teste pode permitir o sideload de aplicativo personalizado.

    > [!Note]
    > Pode levar até 24 horas para que o sideload seja ativo. Durante o ínterim, você pode usar **o upload para \<your tenant>** testar seu aplicativo.

    ![exibição de aplicativo de updload](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Para obter informações completas sobre como essas configurações interagem, consulte [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and Manage app setup policies in Microsoft [Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"] 
> [Escolher uma instalação de teste](~/concepts/build-and-test/debug.md)
> 


