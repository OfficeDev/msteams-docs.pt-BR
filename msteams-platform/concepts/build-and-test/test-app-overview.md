---
title: Testar a visão geral do aplicativo
description: Descreve o processo para testar seu aplicativo Teams personalizado no Microsoft 365
ms.topic: how-to
localization_priority: Normal
keywords: Configurar Microsoft 365 de Teams de teste de carregamento
ms.openlocfilehash: 37f917727aba1a0f9828434b1519b4bb787df7aa
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631003"
---
# <a name="test-your-app"></a>Testar seu aplicativo

Depois de integrar seu aplicativo com Microsoft Teams, você deve testar seu aplicativo antes de publicá-lo. O objetivo final é obter o máximo de usuários para seu aplicativo, portanto, garantir que o aplicativo seja testado em vários dispositivos que os usuários poderiam usar. Para testar seu aplicativo:

* Prepare seu Microsoft 365 locatário.
* Escolha um espaço de trabalho para testar e depurar seu aplicativo.
* Adicione dados de teste ao seu Microsoft 365 locatário.

## <a name="prepare-your-microsoft-365-tenant"></a>Preparar o locatário do Microsoft 365

Antes de começar a testar seu aplicativo, prepare seu Microsoft 365 de teste e habilita o aplicativo Teams personalizado para que você carregue seu aplicativo. Você deve se inscrever no programa Microsoft 365 desenvolvedor e gerenciar as configurações Teams de sua organização. Configure sua assinatura de desenvolvedor e configure-a por [meio da preparação do seu Microsoft 365 Tenant.](~/concepts/build-and-test/prepare-your-o365-tenant.md)

## <a name="test-and-debug"></a>Testar e depurar

Para testar e depurar seu aplicativo, você deve criar pelo menos um espaço de trabalho. Você pode selecionar uma configuração de teste, como host local ou host baseado em nuvem para testar e depurar o aplicativo. As diretrizes para depurar seu Teams aplicativo são fornecidas para carregar e executar a experiência do aplicativo. Para obter mais informações, [consulte choose a set up and run your Microsoft Teams app](~/concepts/build-and-test/debug.md).

Teste seu bot localmente. Para obter mais informações, consulte [depurar seu bot localmente com um IDE](~/bots/how-to/debug/locally-with-an-ide.md). Você também pode depurar seu bot com [middleware de inspeção](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) e [ferramentas adaptáveis.](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true) 

Para exibir os logs do console, exibir ou modificar solicitações de html, css e rede durante o tempo de execução, adicione pontos de interrupção ao código JavaScript e execute a depuração interativa acesse o DevTools. Para obter mais informações, [consulte Access the DevTools for Teams tabs](~/tabs/how-to/developer-tools.md). 

## <a name="add-test-data-to-your-microsoft-365-tenant"></a>Adicionar dados de teste ao seu Microsoft 365 locatário

Adicione os dados de teste Microsoft 365 locatário de teste. Para obter mais informações, consulte [add test data to your Office 365 test tenant](~/concepts/build-and-test/test-data.md), and complete all the prerequisites before you start uploading your test data.

## <a name="see-also"></a>Confira também

* [Depurar sua guia](~/tabs/how-to/developer-tools.md)
* [Depurar seus bots](~/bots/how-to/debug/locally-with-an-ide.md)
* [Testar permissões RSC](~/graph-api/rsc/test-resource-specific-consent.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Preparar o locatário do Microsoft 365](~/concepts/build-and-test/prepare-your-o365-tenant.md)
