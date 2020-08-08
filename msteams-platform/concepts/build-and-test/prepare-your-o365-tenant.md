---
title: Preparar seu locatário do Office 365
description: Como começar a usar o Microsoft Teams no Office 365
keywords: Configurar o carregamento do Office 365 locatário Teams
ms.openlocfilehash: 447968c9b56010e515fc1d1346eac4d8485c7f80
ms.sourcegitcommit: 7a2da3b65246a125d441a971e7e6a6418355adbe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "46587766"
---
# <a name="prepare-your-office-365-tenant"></a>Preparar seu locatário do Office 365

Se você é assinante do Office 365, pode desenvolver aplicativos para o Microsoft Teams com um dos seguintes [planos](https://products.office.com/business/compare-more-office-365-for-business-plans):

* Business Essentials
* Business Premium
* Enterprise E1, E3 e e5
* Developer
* Education, Education Plus e Education e5

O Microsoft Teams também estará disponível para clientes que se inscreveram no E4 antes da sua [aposentadoria](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).

## <a name="just-need-a-development-environment"></a>Precisa apenas de um ambiente de desenvolvimento?

Se você não tiver uma conta do Office 365, você poderá se inscrever em uma assinatura do [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) . É *grátis* por 90 dias e será renovado continuamente, desde que você o esteja usando para a atividade de desenvolvimento. Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional* , ambos os programas incluirão uma [assinatura](https://aka.ms/MyVisualStudioBenefits)gratuita de desenvolvedor do Microsoft 365, ativa pela vida da sua assinatura do Visual Studio. *Confira* [Configurar uma assinatura de desenvolvedor do Microsoft 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).

## <a name="enable-microsoft-teams-for-your-organization"></a>Habilitar o Microsoft Teams para sua organização

Se o Microsoft Teams não tiver sido habilitado para sua organização, você precisará fazer isso primeiro. Confira nossa orientação detalhada para [habilitar o Microsoft Teams para sua organização](https://docs.microsoft.com/microsoftteams/enable-features-office-365).

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Habilitar aplicativos personalizados do Teams e ativar o carregamento de aplicativos personalizados

Ative o aplicativo de Sideload personalizado para o seu locatário do desenvolvedor da seguinte maneira:

1. Faça logon no [centro de administração do Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com sua credencial de administrador. 

2. Selecione **Mostrar todas as**  -->  **equipes**. 

![imagem do menu de estouro de aplicativos](~/assets/images/prepare-test-tenant/admin-center.png)

3. Navegar para políticas de instalação de **aplicativos do teams**  -->  **Setup Policies**  -->  **global (padrão para toda a organização)**  

![imagem do menu de estouro de aplicativos](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Alternar **carregar aplicativos personalizados** para a posição **ativado** .

Isso é tudo. Agora, seu locatário de teste permitirá o Sideload de aplicativos personalizados.

> [!Note] 
> Pode levar até 24 horas antes de o Sideload ser habilitado. Durante o interim, você pode usar **upload \<your tenant> para** para testar seu aplicativo.

![imagem do menu de estouro de aplicativos](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Para obter informações completas sobre como essas configurações interagem, *consulte*, [gerenciar políticas e configurações personalizadas de aplicativos no Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) e [gerenciar políticas de instalação de aplicativos no Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).
