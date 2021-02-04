---
title: Preparar seu locatário do Microsoft 365
description: Como começar a usar o Teams no Microsoft 365
ms.topic: how-to
keywords: Configurar o carregamento do Microsoft 365 tenant Teams
ms.openlocfilehash: 50765271b93edd380d1c23672289b618baf1d346
ms.sourcegitcommit: 55a4246e62d69d631a63bdd33de34f1b62cc0132
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093940"
---
# <a name="prepare-your-microsoft-365-tenant"></a>Preparar seu locatário do Microsoft 365

Se você for assinante do Microsoft 365, poderá desenvolver aplicativos para o Microsoft Teams com um dos seguintes [planos:](https://products.office.com/business/compare-more-office-365-for-business-plans)

* Básica
* Padrão
* Enterprise E1, E3 e E5
* Developer
* Education, Education Plus e Education E5

O Microsoft Teams também estará disponível para os clientes que assinaram o E4 antes da sua [baixa.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)

## <a name="just-need-a-development-environment"></a>Só precisa de um ambiente de desenvolvimento?

Se você não tiver uma conta do Microsoft 365 no momento, inscreva-se para uma assinatura do Programa para Desenvolvedores do [Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program) Ele é gratuito *por* 90 dias e será renovado continuamente, desde que você o esteja usando para atividades de desenvolvimento. Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional,* ambos os programas incluirão uma assinatura gratuita de desenvolvedor do Microsoft 365, ativa durante a vida de sua assinatura do Visual Studio. [](https://aka.ms/MyVisualStudioBenefits) *Confira* [Configurar uma assinatura de desenvolvedor do Microsoft 365.](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started)

## <a name="enable-microsoft-teams-for-your-organization"></a>Habilitar o Microsoft Teams para sua organização 

Se o Microsoft Teams não tiver sido habilitado para sua organização, você precisará fazer isso primeiro. Dê uma olhada em nossas orientações detalhadas para [habilenciar o Teams para sua organização.](/microsoftteams/enable-features-office-365)

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Habilitar aplicativos personalizados do Teams e ativar o carregamento de aplicativos personalizados

Adquira o sideload de aplicativo personalizado para seu locatário de desenvolvedor da seguinte forma:

1. Entre no [Centro de administração do Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com sua credencial de administrador. 

2. Selecione **Mostrar Todas as**  -->  **Equipes.** 

![imagem do menu do centro de administração](~/assets/images/prepare-test-tenant/admin-center.png)

> [!Note] 
> Pode levar até 24 horas para que a opção "Teams" apareça. Durante o ínterim, você [pode carregar seu aplicativo personalizado em um ambiente do Teams](/microsoftteams/upload-custom-apps#validate) para teste e validação.

3. Navegue até Políticas de Instalação de **Aplicativos** do Teams  -->    -->  **Global (padrão em toda a organização)**  

![ativar o sideload view](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Alterne **o carregamento de aplicativos** **personalizados para a posição** on.

5. Selecione **Salvar** para salvar as alterações.

Isso é tudo. Seu locatário de teste agora permitirá o sideload de aplicativo personalizado.

> [!Note] 
> Pode levar até 24 horas para que o sideload seja habilitado. Durante o ínterim, você pode **usar o carregamento para \<your tenant>** testar seu aplicativo.

![exibição do aplicativo de updload](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Para obter informações completas sobre como essas configurações interagem, confira , Gerenciar políticas e configurações de [aplicativos personalizados](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) no Microsoft Teams e gerenciar políticas de configuração de aplicativos [no Microsoft Teams.](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies)
