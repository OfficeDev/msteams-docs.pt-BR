---
title: Testar a visão geral de seu aplicativo
description: Neste módulo, aprenda o processo para testar e depurar seu aplicativo personalizado Teams no Microsoft 365 e adicionar dados de teste ao seu locatário Microsoft 365
ms.topic: how-to
ms.localizationpriority: medium
ms.openlocfilehash: 3fa27881a081021fbb405208a5f7b4a259012aaf
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144380"
---
# <a name="test-your-app"></a>Testar seu aplicativo

Depois de integrar seu aplicativo como o Microsoft Teams, teste-o antes de publicá-lo. O objetivo final é obter o máximo de usuários para seu aplicativo, portanto, certifique-se de testar o aplicativo em múltiplos dispositivos que os usuários poderiam usar. Para testar seu aplicativo:

* Preparar seu locatário do Microsoft 365.
* Escolha um espaço de trabalho para testar e depurar seu aplicativo.
* Adicionar dados de teste ao seu locatário do Microsoft 365.

## <a name="prepare-your-microsoft-365-tenant"></a>Preparar o locatário do Microsoft 365

Antes de começar a testar seu aplicativo, prepare seu locatário de teste do Microsoft 365 e habilite o aplicativo personalizado do Teams para permitir que você carregue seu aplicativo. Você deve se inscrever no programa para desenvolvedores do Microsoft 365 e gerenciar as configurações do Teams para sua organização. Configure sua assinatura de desenvolvedor e configure-a em [preparar seu Locatário do Microsoft 365](~/concepts/build-and-test/prepare-your-o365-tenant.md).

## <a name="test-and-debug"></a>Testar e depurar

Para testar e depurar seu aplicativo, você deve criar pelo menos um espaço de trabalho. Você pode selecionar uma configuração de teste, como host local ou host baseado em nuvem, para testar e depurar o aplicativo. As diretrizes para depurar seu Teams aplicativo são fornecidas para carregar e executar sua experiência de aplicativo. Para obter mais informações, consulte [escolher uma configuração e executar seu aplicativo do Microsoft Teams](~/concepts/build-and-test/debug.md).

Testar seu bot localmente. Para obter mais informações, consulte [depurar seu bot localmente com um IDE](~/bots/how-to/debug/locally-with-an-ide.md). Você também pode depurar seu bot com [middleware de inspeção](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) e [ferramentas adaptáveis](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true).

Para exibir os logs do console, exibir ou modificar html, css e solicitações de rede durante o tempo de execução, adicione pontos de interrupção ao seu código JavaScript e realize depuração interativa para acessar o DevTools. Para obter mais informações, consulte [Acessar o DevTools para guias do Teams](~/tabs/how-to/developer-tools.md).

## <a name="add-test-data-to-your-microsoft-365-tenant"></a>Adicionar dados de teste ao seu locatário do Microsoft 365

Adicionar os dados de teste ao seu locatário de teste do Microsoft 365. Para obter mais informações, consulte [adicionar dados de teste ao seu locatário de teste do Office 365](~/concepts/build-and-test/test-data.md), e completar todos os pré-requisitos antes de iniciar o carregamento de seus dados de teste.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Preparar o locatário do Microsoft 365](~/concepts/build-and-test/prepare-your-o365-tenant.md)

## <a name="see-also"></a>Confira também

* [Depurar sua guia](~/tabs/how-to/developer-tools.md)
* [Depurar seus bots](~/bots/how-to/debug/locally-with-an-ide.md)
* [Testar permissões RSC](~/graph-api/rsc/test-resource-specific-consent.md)
