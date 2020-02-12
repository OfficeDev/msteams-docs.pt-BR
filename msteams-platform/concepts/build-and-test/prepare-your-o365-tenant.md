---
title: Preparar o locatário do Office 365
description: Como começar a usar o Microsoft Teams no Office 365
keywords: Configurar o carregamento do Office 365 locatário Teams
ms.openlocfilehash: 634392ea3f0228aef69ff920d3b369eb49dd3965
ms.sourcegitcommit: 060b486c38b72a3e6b63b4d617b759174082a508
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2020
ms.locfileid: "41953492"
---
# <a name="prepare-your-office-365-tenant"></a>Preparar o locatário do Office 365

Se você é assinante do Office 365, pode desenvolver aplicativos para o Microsoft Teams com um dos seguintes [planos](https://products.office.com/business/compare-more-office-365-for-business-plans):

* Business Essentials
* Business Premium
* Enterprise E1, E3 e e5
* Developer
* Education, Education Plus e Education e5

O Microsoft Teams também estará disponível para clientes que se inscreveram no E4 antes da sua [aposentadoria](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).

## <a name="just-need-a-development-environment"></a>Precisa apenas de um ambiente de desenvolvimento?

Se você não tiver uma conta do Office 365, você poderá se inscrever em uma assinatura do [programa de desenvolvedor do office 365](https://dev.office.com/devprogram) . É *grátis* por 90 dias e será renovado continuamente, desde que você o esteja usando para a atividade de desenvolvimento. Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional* , ambos os programas incluirão uma [assinatura](https://aka.ms/MyVisualStudioBenefits)gratuita de desenvolvedor do Office 365, ativa pela vida da sua assinatura do Visual Studio. *Confira* [Configurar uma assinatura de desenvolvedor do Microsoft 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).

## <a name="enable-microsoft-teams-for-your-organization"></a>Habilitar o Microsoft Teams para sua organização

Se o Microsoft Teams não tiver sido habilitado para sua organização, você precisará fazer isso primeiro. Confira nossa orientação detalhada para [habilitar o Microsoft Teams para sua organização](https://docs.microsoft.com/microsoftteams/enable-features-office-365).

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Habilitar aplicativos personalizados do Teams e ativar o carregamento de aplicativos personalizados

> [!Note] 
> Se você estiver usando a plataforma de desenvolvedor do Office 365 para criar seu aplicativo, essas configurações já devem estar configuradas para permitir que você crie, carregue e teste seu aplicativo.

Há três configurações relevantes para habilitar aplicativos personalizados e carregamento de aplicativos personalizados:

* **Configuração** => de aplicativo personalizado para toda a organização**permita a interação com aplicativos** => personalizados **— essa** configuração habilita ou desabilita aplicativos personalizados para sua organização. Ele precisa estar ativado. 
* **Configuração** =>  => **do** aplicativo personalizado de equipe**permitir que os membros carreguem aplicativos personalizados**— essa configuração se aplica a cada equipe individual no Microsoft Teams. Se você quiser instalar o aplicativo para uma equipe específica, será necessário que ele esteja ativado para essa equipe.
* **Política** => de aplicativo personalizada => **de** usuário o**usuário pode carregar aplicativos personalizados**— essa configuração controla as permissões para um usuário individual. Você precisará habilitar isso para pessoas com permissão para carregar aplicativos personalizados.

Para obter informações completas sobre como essas configurações interagem, *consulte* [gerenciar políticas e configurações de aplicativos personalizados no Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) e [gerenciar políticas de configuração de aplicativos no Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).
