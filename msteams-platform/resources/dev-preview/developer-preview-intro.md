---
title: Developer Preview
description: Descreve os recursos na Pré-visualização pública do Desenvolvedor do Microsoft Teams
ms.topic: conceptual
ms.localizationpriority: high
keywords: recursos da pré-visualização do desenvolvedor do teams
ms.openlocfilehash: b84a13936e023c743829876f9d1c039d6744b063
ms.sourcegitcommit: 3d0cfa779dec6bfc0daa57880ea37ab94f3d426f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2022
ms.locfileid: "63492950"
---
# <a name="public-developer-preview-for-microsoft-teams"></a>Pré-visualização pública do desenvolvedor para o Microsoft Teams

>[!NOTE]
>Os recursos incluídos na pré-visualização podem não estar completos e podem sofrer alterações antes de se tornarem disponíveis no lançamento público. Eles são fornecidos apenas para fins de teste e exploração. Eles não devem ser usados em aplicativos de produção.

A pré-visualização pública é um programa para desenvolvedores que fornece acesso antecipado a recursos não lançados no Microsoft Teams. Isso permite que você explore e teste os recursos futuros para uma possível inclusão em seu aplicativo Microsoft Teams. Também agradecemos o [feedback](~/feedback.md) sobre qualquer recurso em pré-visualizações do desenvolvedor. A pré-visualização do desenvolvedor está habilitada por cliente do Microsoft Teams, portanto, você não precisa se preocupar em afetar toda sua organização.

## <a name="developer-preview-app-manifest"></a>Manifesto do aplicativo de pré-visualização do desenvolvedor

Muitos recursos habilitados na pré-visualização do desenvolvedor exigirão alterações no arquivo JSON do manifesto do aplicativo. Para fazer isso, você precisará usar o [esquema de manifesto da visualização do desenvolvedor](~/resources/schema/manifest-schema-dev-preview.md). Se usar esse esquema, não poderá usar o [App Studio](~/concepts/build-and-test/app-studio-overview.md) para fazer essas alterações nem poderá usá-lo para carregar seu aplicativo para teste. Para carregar seu aplicativo, você precisará clicar no ícone `More apps` na barra de aplicativos e, em seguida, selecionar o `Upload a custom app link`. Usando esse método, você só pode carregar uma versão compactada do pacote do aplicativo.

Você pode achar útil usar o App Studio para criar as partes de pré-visualização de não desenvolvedor do pacote de aplicativos e, em seguida, exportar esse pacote e editar manualmente o arquivo `manifest.json` para adicionar os recursos de pré-visualização do desenvolvedor que você deseja usar. Depois de adicionar recursos da visualização do desenvolvedor ao arquivo `manifest.json`, você não poderá importar novamente o pacote para o App Studio.

## <a name="enable-developer-preview"></a>Habilitar a visualização do desenvolvedor

A pré-visualização do desenvolvedor é habilitada por cliente, mas a opção de ativar a pré-visualização do desenvolvedor é controlada no nível da organização. Para habilitar a opção de ativar a pré-visualização do desenvolvedor para um indivíduo, você deve garantir que ele possa carregar aplicativos personalizados. Consulte [configuração do locatário](~/concepts/build-and-test/prepare-your-o365-tenant.md) para obter informações adicionais.

O uso de um aplicativo que contém recursos de visualização do desenvolvedor pode fazer com que os clientes que não habilitaram a pré-visualização do desenvolvedor se comportem de forma inesperada. Se você não encontrar uma entrada para a pré-visualização do desenvolvedor, o motivo mais provável é que sua organização não está configurada para carregamento de aplicativos.

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

Use o mesmo item de menu em Sobre → Pré-visualização do desenvolvedor e clique nela para desativá-la.

## <a name="see-also"></a>Confira também

[Testar e depurar seu aplicativo Microsoft Teams](~/concepts/build-and-test/debug.md)
