---
title: Pré-visualização pública do desenvolvedor para o Microsoft Teams
description: Uma Versão Prévia do Desenvolvedor (Beta) é um programa público para explorar e testar os recursos futuros para inclusão potencial em seu aplicativo Microsoft Teams.
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: dd0583f453e93a0127bf4cbcc29a6a56dec6655a
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100284"
---
# <a name="public-developer-preview-for-teams"></a>Visualização do desenvolvedor público do Teams

>[!NOTE]
>Os recursos incluídos na pré-visualização podem não estar completos e podem sofrer alterações antes de se tornarem disponíveis no lançamento público. Eles são fornecidos apenas para fins de teste e exploração. Eles não devem ser usados em aplicativos de produção.

O Developer Preview é um programa público para desenvolvedores, que fornece acesso antecipado a recursos não lançados no Microsoft Teams. Isso permite que você explore e teste os próximos recursos para uma possível inclusão em seu aplicativo Teams. Também agradecemos o [feedback](~/feedback.md) sobre qualquer recurso em pré-visualizações do desenvolvedor. A pré-visualização do desenvolvedor está habilitada por cliente do Microsoft Teams, portanto, você não precisa se preocupar em afetar toda sua organização.

## <a name="developer-preview-app-manifest"></a>Manifesto do aplicativo de pré-visualização do desenvolvedor

Muitos recursos habilitados na pré-visualização do desenvolvedor exigirão alterações no arquivo JSON do manifesto do aplicativo. Para fazer isso, você precisará usar o [esquema de manifesto da visualização do desenvolvedor](~/resources/schema/manifest-schema-dev-preview.md). Se você usar esse esquema, não poderá usar [Portal do Desenvolvedor do Teams](~/concepts/build-and-test/teams-developer-portal.md) para fazer essas alterações, nem poderá usá-lo para carregar seu aplicativo para teste. Para fazer upload de seu aplicativo, você precisará selecionar o ícone `More apps` na barra de aplicativos e, em seguida, selecionar o `Upload a custom app link`. Usando esse método, você só pode carregar uma versão compactada do pacote do aplicativo.

Você pode achar útil usar o Portal do Desenvolvedor do Teams para criar as partes de visualização que não são de desenvolvedor do pacote de aplicativos e, em seguida, exportar esse pacote e editar manualmente o arquivo `manifest.json` para adicionar os recursos de visualização do desenvolvedor que você deseja usar. Depois de adicionar recursos de visualização do desenvolvedor ao arquivo `manifest.json`, você não poderá importar novamente o pacote para o Portal do Desenvolvedor do Teams.

## <a name="enable-developer-preview"></a>Habilitar a visualização do desenvolvedor

A pré-visualização do desenvolvedor é habilitada por cliente, mas a opção de ativar a pré-visualização do desenvolvedor é controlada no nível da organização. Para habilitar a opção de ativar a pré-visualização do desenvolvedor para um indivíduo, você deve garantir que ele possa carregar aplicativos personalizados. Consulte [configuração do locatário](~/concepts/build-and-test/prepare-your-o365-tenant.md) para obter informações adicionais.

O uso de um aplicativo que contém recursos de visualização do desenvolvedor pode fazer com que os clientes que não habilitaram a pré-visualização do desenvolvedor se comportem de forma inesperada. Se você não vir uma entrada para a visualização do desenvolvedor, o motivo mais provável é que sua organização não está configurada para upload de aplicativos.

### <a name="on-a-desktop-or-web-client"></a>Em uma área de trabalho ou cliente Web

Para habilitar a visualização pública do desenvolvedor em uma área de trabalho ou cliente Web:

1. Habilite o carregamento ou sideload de aplicativo personalizado para seu locatário do desenvolvedor. Para obter mais informações, confira [Habilitar aplicativos personalizados do Teams](../../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading).
1. Selecione o menu de reticências (...) ao lado do seu perfil de usuário para exibir o menu do Teams.
1. Selecione **Sobre** > **Visualização do desenvolvedor**.
1. Selecione **Alternar para pré-visualização do Desenvolvedor**.

### <a name="on-a-mobile-client"></a>Em um cliente móvel

Para habilitar a visualização pública do desenvolvedor em um cliente móvel:

1. Habilite o carregamento ou sideload de aplicativo para seu locatário do desenvolvedor. Para obter mais informações, confira [Habilitar aplicativos personalizados do Teams](../../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading).
1. Abra o menu de hambúrguer no canto superior esquerdo e selecione **Configurações**.
1. Selecione **Sobre**.
1. Habilitar a alternância de **Visualização do desenvolvedor**.

## <a name="disable-developer-preview"></a>Desabilite a pré-visualização do desenvolvedor

Use o mesmo item de menu em Sobre → Visualização do desenvolvedor e selecione-o para desativá-lo.

## <a name="see-also"></a>Confira também

[Testar e depurar seu aplicativo Microsoft Teams](~/concepts/build-and-test/debug.md)
