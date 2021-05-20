---
title: Teste a visão geral do seu aplicativo
description: Descreve o processo para testar seu aplicativo personalizado Teams em Microsoft 365
ms.topic: how-to
localization_priority: Normal
keywords: Configure Microsoft 365 aplicativo de teste de Teams de upload de inquilinos
ms.openlocfilehash: 2c9f23a5c6ae286ff4b7d911f370bd45b854a647
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565181"
---
# <a name="test-your-app"></a>Testar seu aplicativo

Depois de integrar seu aplicativo com Microsoft Teams, você deve testar seu aplicativo antes de publicá-lo. O objetivo final é obter o maior número de usuários para o seu aplicativo, portanto, garantir testar o aplicativo em vários dispositivos que os usuários poderiam usar. Para testar seu aplicativo:

* Prepare seu inquilino Microsoft 365.
* Escolha um espaço de trabalho para testar e depurar seu aplicativo.
* Adicione dados de teste ao seu inquilino Microsoft 365.

## <a name="prepare-your-microsoft-365-tenant"></a>Preparar o locatário do Microsoft 365

Antes de começar a testar seu aplicativo, prepare seu inquilino de teste Microsoft 365 e habilite Teams aplicativo personalizado permita que você carregue seu aplicativo. Você deve se inscrever para Microsoft 365 programa de desenvolvedor e gerenciar as configurações de Teams para sua organização. Configure sua assinatura de desenvolvedor e configure-a através [da preparação de seu Microsoft 365 Tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).

## <a name="test-and-debug"></a>Testar e depurar

Para testar e depurar seu aplicativo, você deve criar pelo menos um espaço de trabalho. Você pode selecionar uma configuração de teste, como host local ou host baseado em nuvem para testar e depurar o aplicativo. Orientações para depurar seu aplicativo Teams são fornecidas para carregar e executar sua experiência no aplicativo. Para obter mais informações, consulte [escolher uma configuração e executar seu aplicativo de Microsoft Teams](~/concepts/build-and-test/debug.md).

Teste seu bot localmente. Para obter mais informações, consulte [depurar seu bot localmente com um IDE](~/bots/how-to/debug/locally-with-an-ide.md). Você também pode depurar seu bot com [middleware de inspeção](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) e [ferramentas adaptativas.](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true) 

Para visualizar os logs do console, visualizar ou modificar as solicitações html, css e rede durante o tempo de execução, adicione pontos de interrupção ao seu código JavaScript e execute a depuração interativa acessar os DevTools. Para obter mais informações, consulte [Acessar as guias de Teams de Teams](~/tabs/how-to/developer-tools.md). 

## <a name="add-test-data-to-your-microsoft-365-tenant"></a>Adicione dados de teste ao seu inquilino Microsoft 365

Adicione os dados do teste ao Microsoft 365 inquilino do teste. Para obter mais informações, consulte [adicionar dados de teste ao seu inquilino de teste Office 365](~/concepts/build-and-test/test-data.md)e completar todos os pré-requisitos antes de começar a carregar seus dados de teste.

## <a name="see-also"></a>Confira também

- [Depurar sua guia](~/tabs/how-to/developer-tools.md)
 
- [Depurar seus bots](~/bots/how-to/debug/locally-with-an-ide.md)

- [Testar as permissões RSC](~/graph-api/rsc/test-resource-specific-consent.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Preparar o locatário do Microsoft 365](~/concepts/build-and-test/prepare-your-o365-tenant.md)
