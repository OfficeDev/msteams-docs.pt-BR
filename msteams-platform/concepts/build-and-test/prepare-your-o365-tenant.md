---
title: Preparar o locatário do Microsoft 365
description: Neste módulo, saiba como começar a usar o Teams no Microsoft 365 e criar seu ambiente de desenvolvimento
ms.topic: how-to
ms.localizationpriority: medium
ms.openlocfilehash: 241040767c610692873e5a68bd215849a8cd26a0
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144387"
---
# <a name="prepare-your-microsoft-365-tenant"></a>Preparar o locatário do Microsoft 365

Assinantes do Microsoft 365 podem desenvolver aplicativos para Microsoft Teams com um dos seguintes planos:

* Básico
* Padrão
* Enterprise E1, E3 e E5
* Developer
* Education, Education Plus e Education E5

> [!NOTE]
>
> * Para obter mais informações sobre assinaturas do Microsoft 365, consulte [planos](https://products.office.com/business/compare-more-office-365-for-business-plans).
> * Teams também está disponível para clientes que assinaram o E4 antes de sua [desativação](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).

## <a name="create-your-development-environment"></a>Preparar seu ambiente de desenvolvimento

Se você não tiver uma conta do Microsoft 365, deverá assinar o [programa para desenvolvedores do Microsoft 365](https://developer.microsoft.com/microsoft-365/dev-program). A assinatura é gratuita por 90 dias e continua a ser renovada desde que você a esteja usando em atividades de desenvolvimento. Se você tiver uma assinatura do Visual Studio Enterprise ou Professional, ambos os programas incluem uma assinatura de [desenvolvedor gratuita](https://aka.ms/MyVisualStudioBenefits) do Microsoft 365. Ele estará ativo desde que sua assinatura do Visual Studio esteja ativa. Para mais informações, confira [Configurar uma assinatura de desenvolvedor do Microsoft 365](/office/developer-program/office-365-developer-program-get-started).

## <a name="enable-teams-for-your-organization"></a>Habilitar Teams para sua organização

Habilite Teams para sua organização e, para obter mais informações, confira [Como habilitar o Teams para sua organização](/microsoftteams/enable-features-office-365).

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Habilitar aplicativos personalizados do Teams e ativar o carregamento de aplicativo personalizado

Para ativar o carregamento ou sideload de aplicativo personalizado para seu locatário de desenvolvedor:

1. Acessar o [Centro de administração do Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com suas credenciais de administrador.

2. Selecione **Mostrar Tudo** > **Teams**.

    ![Menu do Centro de administração](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > Pode levar até 24 horas para a opção **Teams** ser exibida. Você pode [carregar seu aplicativo personalizado em um ambiente do Teams](/microsoftteams/upload-custom-apps#validate) para teste e validação naquele momento.

3. Navegue até **Aplicativos do Teams** > **Políticas de Configuração** > **Global**.

   ![Ativar o modo de exibição de sideload](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Alterne **Carregar aplicativos personalizados** para a posição **On**.

5. Selecione **Salvar**. Seu locatário de teste pode permitir o sideload de aplicativo personalizado.

    > [!Note]
    > Pode levar até 24 horas para que o sideload esteja ativo. Nesse ínterim, você pode usar o **upload para \<your tenant>** testar seu aplicativo. Para carregar o arquivo do pacote .zip do aplicativo, consulte [Carregar aplicativos personalizados](/microsoftteams/upload-custom-apps#upload).

    ![Carregar modo de exibição do aplicativo](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Para obter informações completas sobre como essas configurações interagem, consulte [gerenciar políticas e configurações de aplicativo personalizadas no Teams](/microsoftteams/teams-custom-app-policies-and-settings) e [gerenciar políticas de configuração de aplicativo no Teams](/microsoftteams/teams-app-setup-policies).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Escolher uma configuração de teste](~/concepts/build-and-test/debug.md)

## <a name="see-also"></a>Confira também

[Adicionar dados de teste ao seu locatário Microsoft 365 teste](~/concepts/build-and-test/test-data.md)
